=== Problem ====
A ciphertext alphabet is obtained from the plaintext alphabet by means of rearranging some characters. For example "bacdef...xyz" will be a simple ciphertext alphabet where a and b are rearranged.

A substitution cipher is a method of encoding where each letter of the plaintext alphabet is replaced with the corresponding (i.e. having the same index) letter of some ciphertext alphabet.

Given two strings, check whether it is possible to obtain them from each other using some (possibly, different) substitution ciphers.

Example

For string1 = "aacb" and string2 = "aabc", the output should be
solution(string1, string2) = true.

Any ciphertext alphabet that starts with acb... would make this transformation possible.

For string1 = "aa" and string2 = "bc", the output should be
solution(string1, string2) = false.

Input/Output

[execution time limit] 4 seconds (js)

[input] string string1

A string consisting of lowercase English characters.

Guaranteed constraints:
1 ≤ string1.length ≤ 10.

[input] string string2

A string consisting of lowercase English characters of the same length as string1.

Guaranteed constraints:
string2.length = string1.length.

[output] boolean

====== Solution=====
function solution(string1, string2) {
 var a;
  var b;
  var ret = string1.length === string2.length;
  var t = 2;
  var aux;
  var pos;
  while (t--) {
    for (var i = 0; i < string1.length; i++) {
      a = string1[i];
      b = string2[i];
      pos = string1.indexOf(a, i + 1);
      while (pos >= 0) {
        if (string2[pos] != b) {
          ret = false;
        }
        pos = string1.indexOf(a, pos + 1);
      }
    }

    aux = string1;
    string1 = string2;
    string2 = aux;
  }

  return ret;
}
