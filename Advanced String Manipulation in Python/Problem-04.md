# Problem Statement
You have been given an array of strings, `words`. Your task is to implement a function that will find the largest common prefix among the strings in the array. If there is no common prefix, it should return an empty string.

Your task should aim for a solution of complexity `O(words.length * length^2)`, where `words.length` is the number of strings in the array and length is the length of the smallest string.

For example, `largest_common_prefix(["tractor", "traffic", "transmit"]))` should output `"tra"`, as it is the largest common prefix for these three strings.

# Solution
```python
def largest_common_prefix(words):
    if not words:
        return ''
    
    prefix = []
    min_w = min(len(w) for w in words)
    
    for i in range(min_w):
        ch_to_compare = words[0][i]
        if all(ch_to_compare == w[i] for w in words):
            prefix.append(ch_to_compare)
        else:
            break
    return "".join(prefix)
        
    pass
```

# Tests
```python
import unittest
from solution import largest_common_prefix

class SolutionTests(unittest.TestCase):
    def test1(self):
        self.assertEqual(largest_common_prefix(["tractor", "traffic", "transmit"]), "tra")

    def test2(self):
        self.assertEqual(largest_common_prefix(["interview", "internal", "integrity"]), "inte")
        
    def test3(self):
        self.assertEqual(largest_common_prefix(["flower", "flow", "flight"]), "fl")
        
    def test4(self):
        self.assertEqual(largest_common_prefix(["dog", "racecar", "car"]), "")
        
    def test5(self):
        self.assertEqual(largest_common_prefix(["class", "classic", "classification"]), "class")
        
    def test6(self):
        self.assertEqual(largest_common_prefix(["sun", "sunny", "sunday"]), "sun")
        
    def test7(self):
        self.assertEqual(largest_common_prefix(["python", "pythonic", "py"]), "py")
        
    def test8(self):
        self.assertEqual(largest_common_prefix(["beam", "bean", "beard"]), "bea")
        
    def test9(self):
        self.assertEqual(largest_common_prefix(["run", "rune", "array"]), "")
        
    def test10(self):
        self.assertEqual(largest_common_prefix(["boxing", "box", "boxes"]), "box")
        
    def test11(self):
        self.assertEqual(largest_common_prefix(["base", "ball", "bat"]), "ba")
        
    def test12(self):
        self.assertEqual(largest_common_prefix(["jump", "jumper", "jumpy"]), "jump")
        
    def test13(self):
        self.assertEqual(largest_common_prefix(["lovely", "loveless", "love"]), "love")
        
    def test14(self):
        self.assertEqual(largest_common_prefix(["dark", "darkness", "dart"]), "dar")
        
    def test15(self):
        self.assertEqual(largest_common_prefix(["fire", "firefly", "firefox"]), "fire")
        
    def test16(self):
        self.assertEqual(largest_common_prefix(["prefix", "preview", "prelude"]), "pre")
        
    def test17(self):
        self.assertEqual(largest_common_prefix(["postscript", "postman", "post"]), "post")
        
    def test18(self):
        self.assertEqual(largest_common_prefix(["gaming", "gamer", "game"]), "gam")
        
    def test19(self):
        self.assertEqual(largest_common_prefix(["jelly", "jellyfish", "jellybean"]), "jelly")
        
    def test20(self):
        self.assertEqual(largest_common_prefix(["queen", "query", "quadratic"]), "qu")

    def test21(self):
        self.assertEqual(largest_common_prefix(["class", "class", "class"]), "class")


if __name__ == '__main__':
    unittest.main()
```