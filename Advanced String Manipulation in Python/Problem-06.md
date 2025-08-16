# Problem Statement
You are given a string of characters. Your task is to write a function that will find and return the most common substring of a given length in the input string. If two or more substrings have the same maximum frequency, you should return the lexicographically smallest one.

For example, given the input string `"bananabananaba"` and a substring length of `5`, your function should return `"anaba"`, since it appears twice and is lexicographically smaller than other substrings that also appear twice (e.g., "banan").

The expected time complexity for this task is **_`O(str.length⋅length)`_**.

# Solution
```python
def find_most_common_substring(s: str, length: int) -> str:
    
    freq = {}
    n = len(s)
    max_freq = 0
    best_substring = ''
    for i in range(n - length + 1):
        substring = s[i:i + length]
        freq[substring] = freq.get(substring, 0) + 1
        
        if freq[substring] > max_freq:
            max_freq = freq[substring]
            best_substring = substring
        elif freq[substring] == max_freq:
            best_substring = min(best_substring, substring)
    
    return best_substring
    pass
```

# Tests
```python
import unittest
from solution import find_most_common_substring

class SolutionTests(unittest.TestCase):
    def test1(self):
        self.assertEqual(find_most_common_substring('bananabananaba', 5), 'anaba')

    def test2(self):
        self.assertEqual(find_most_common_substring('a.b.aa.ab.', 3), '.aa')

    def test3(self):
        self.assertEqual(find_most_common_substring('abcabcabc', 2), 'ab')

    def test4(self):
        self.assertEqual(find_most_common_substring('zyxwvutsr', 1), 'r')

    def test5(self):
        self.assertEqual(find_most_common_substring('epidemiology', 6), 'demiol')
   
    def test6(self):
        self.assertEqual(find_most_common_substring('abcdabcdabcdabcdabcd', 4), 'abcd')
    
    def test7(self):
        self.assertEqual(find_most_common_substring('lololololo', 3), 'lol')

    def test8(self):
        self.assertEqual(find_most_common_substring('a', 1), 'a')

    def test9(self):
        self.assertEqual(find_most_common_substring('aa', 1), 'a')

    def test10(self):
        self.assertEqual(find_most_common_substring('abcdefgh', 1), 'a')

    def test11(self):
        self.assertEqual(find_most_common_substring('abcdefgh', 8), 'abcdefgh')
        
    def test12(self):
        self.assertEqual(find_most_common_substring('xyzzyx', 2), 'xy')

    def test13(self):
        self.assertEqual(find_most_common_substring('abcd', 4), 'abcd')

    def test14(self):
        self.assertEqual(find_most_common_substring('aaa', 1), 'a')

    def test15(self):
        self.assertEqual(find_most_common_substring('racecar', 3), 'ace')

    def test16(self):
        self.assertEqual(find_most_common_substring('aaabbb', 3), 'aaa')


if __name__ == '__main__':
    unittest.main()
```