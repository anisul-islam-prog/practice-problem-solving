# Problem Statement
You are given a string `s`. Your task is to create a function that checks whether the string `s` consists of one repeated substring.

If it does, the function should return the substring. If there are multiple possible answers, return the longest one. If it does not consist of a repeated substring, return an empty string.

To clarify, a "repeated substring" refers to a pattern of characters that reoccurs throughout the full string, with no characters left over. For example, the string "abababab" consists of repeated substrings "ab" and "abab". On the other hand, the string "abcabcab" does not consist of a repeated substring, as the final characters "ab" do not complete the repeating pattern of "abc".

# Solution
```python
def repeat_substring(s):
    n = len(s)
    
    for longest in range(n // 2, 0, -1):
        if n % longest == 0:
            candidate = s[:longest]
            if candidate * (n // longest) == s:
                return candidate
    return ""
    pass
```

# Tests
```python
import unittest
from solution import repeat_substring

class RepeatSubstringTest(unittest.TestCase):
    def test_1(self):
        self.assertEqual(repeat_substring("ababab"), "ab")

    def test_2(self):
        self.assertEqual(repeat_substring("abcab"), "")

    def test_3(self):
        self.assertEqual(repeat_substring("abcdefg"), "")

    def test_4(self):
        self.assertEqual(repeat_substring("zzzz"), "zz")

    def test_5(self):
        self.assertEqual(repeat_substring("#$#$$$#$#"), "")

    def test_6(self):
        self.assertEqual(repeat_substring("PythonPythonPython"), "Python")

    def test_7(self):
        self.assertEqual(repeat_substring("0"), "")

    def test_8(self):
        self.assertEqual(repeat_substring("10011001100110011"), "")

    def test_9(self):
        self.assertEqual(repeat_substring("qwertyqwertyqwerty"), "qwerty")

    def test_10(self):
        self.assertEqual(repeat_substring("aaaaaaaaaa"), "aaaaa")

    def test_11(self):
        self.assertEqual(repeat_substring("abababcbcbcbc"), "")

    def test_12(self):
        self.assertEqual(repeat_substring("abababab"), "abab")

    def test_13(self):
        self.assertEqual(repeat_substring("1111111111"), "11111")

    def test_14(self):
        self.assertEqual(repeat_substring("xyzxyzxyzxyzxyzxyz"), "xyzxyzxyz")

    def test_15(self):
        self.assertEqual(repeat_substring("a" * 10000), "a" * 5000)

    def test_16(self):
        self.assertEqual(repeat_substring("bmbmbmbmbmbmbmbmbmbmbbmbmbmbmbmbmbmbmbmbmb"), "bmbmbmbmbmbmbmbmbmbmb")

    def test_17(self):
        self.assertEqual(repeat_substring("lololololololololo"), "lololo")

    def test_18(self):
        self.assertEqual(repeat_substring("abcdefghijabcdefghijabcdefghij"), "abcdefghij")

    def test_19(self):
        self.assertEqual(repeat_substring("y" * 999 + "z"), "")

    def test_20(self):
        self.assertEqual(repeat_substring("tuttuttuttuttut"), "tut")


if __name__ == '__main__':
    unittest.main()
```