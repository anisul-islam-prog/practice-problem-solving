# Problem Statement
You are given two strings, `string1` and `string2`. Your goal is to determine a new string, `string3`, that is formed by characters that occur in both `string1` and `string2` in the same order as they occur in `string1`.

Characters in `string3` should maintain their original sequence order from `string1`. If a character is repeated in `string1` and `string2`, include that character in `string3` as many times as it occurs in both strings, but not more than that.

For example, given `string1 = "apple"` and `string2 = "peach"`, the resulting `string3` would be `"ape"`.

Your algorithm should not exceed a time complexity of **_`O(string1.length+string2.length)`_**.

# Solution
```python
def solution(string1, string2):
    freq = {}
    for ch in string2:
        freq[ch] = freq.get(ch, 0) + 1
    result = []
    for ch in string1:
        if ch in freq and freq[ch] > 0:
            result.append(ch)
            freq[ch] -= 1
    return ''.join(result)
    pass
```

# Tests
```python
import unittest
from solution import solution

class SolutionTests(unittest.TestCase):

    def test1(self):
        self.assertEqual(solution("abcd", "dcba"), "abcd")

    def test2(self):
        self.assertEqual(solution("apple", "peach"), "ape")

    def test3(self):
        self.assertEqual(solution("aabbcc", "abc"), "abc")

    def test4(self):
        self.assertEqual(solution("aaaa", "aaaa"), "aaaa")

    def test5(self):
        self.assertEqual(solution("abcdef", "fedcba"), "abcdef")

    def test6(self):
        self.assertEqual(solution("aabbccdd", "bcda"), "abcd")
    
    def test7(self):
        self.assertEqual(solution("python", "thonpy"), "python")
    
    def test8(self):
        self.assertEqual(solution("interview", "review"), "iervew")

    def test9(self):
        self.assertEqual(solution("aaaaa", "b"), "")
    
    def test10(self):
        self.assertEqual(solution("abc", "def"), "")


if __name__ == '__main__':
    unittest.main()
```