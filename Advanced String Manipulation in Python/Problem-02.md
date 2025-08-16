# Problem Statement
You are given an array of `n` strings. Your task is to find the longest common suffix shared among all strings in the array. A suffix is a sequence of letters at the end of a word. For instance, in the word "flying," "ing" is a suffix.

If the given array is empty or there is no common suffix among the strings, your function should return an empty string.

For example, given an array of strings: `["barking", "parking", "starking"]`, the longest common suffix is `"arking"`.

# Solution
```python
def solution(strs):
    if not strs:
        return ""
    
    reversed_string_list = [s[::-1] for s in strs]
    
    min_s = min(len(s) for s in reversed_string_list)
    
    suffix = []
    for i in range(min_s):
        current_ch = reversed_string_list[0][i]
        if all(s[i] == current_ch for s in reversed_string_list):
            suffix.append(current_ch)
        else:
            break
    return "".join(suffix[::-1])
    pass
```

# Tests
```python
import unittest
from solution import solution


class SolutionTests(unittest.TestCase):
    def test1(self):
        self.assertEqual(solution(["barking", "parking", "starking"]), "arking")

    def test2(self):
        self.assertEqual(solution(["flower", "tower", "power"]), "ower")

    def test3(self):
        self.assertEqual(solution(["alpha", "beta", "gamma"]), "a")

    def test4(self):
        self.assertEqual(solution(["racer", "placer", "effacer"]), "acer")

    def test5(self):
        self.assertEqual(solution(["hello", "jello"]), "ello")

    def test6(self):
        self.assertEqual(solution(["word"]), "word")

    def test7(self):
        self.assertEqual(solution(["apple", "grapple", "pineapple"]), "apple")

    def test8(self):
        self.assertEqual(solution(["a", "aa", "aaa"]), "a")

    def test9(self):
        self.assertEqual(solution(["ab", "abc", "abcd"]), "")

    def test10(self):
        self.assertEqual(solution([]), "")

    def test11(self):
        self.assertEqual(solution(["introduction", "reduction", "production", "seduction"]), "duction")

    def test12(self):
        self.assertEqual(solution(["communication", "station", "vacation", "nation"]), "ation")

    def test13(self):
        self.assertEqual(solution(["spoon", "moon", "balloon", "cartoon", "raccoon"]), "oon")

    def test14(self):
        self.assertEqual(solution(["abracadabra", "dabra", "califragilisticexpialidociousdabra"]), "dabra")

    def test15(self):
        self.assertEqual(solution(["transformation", "information", "formation", "automation"]), "mation")

    def test16(self):
        self.assertEqual(solution(["repeater", "defeater", "heater", "seater", "eater"]), "eater")

    def test17(self):
        self.assertEqual(solution(["intelligibility", "responsibility", "agility", "ability"]), "ility")

    def test18(self):
        self.assertEqual(solution(["synchronization", "organization", "localization", "realization"]), "ization")

    def test19(self):
        self.assertEqual(solution(["complication", "application", "implication", "replication", "duplication"]), "plication")

    def test20(self):
        self.assertEqual(solution(["understanding", "withstanding", "demanding", "commanding", "handing"]), "anding")


if __name__ == '__main__':
    unittest.main()
```