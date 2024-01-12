# Substring-with-Concatenation-of-All-Words
You are given a string s and an array of strings words. All the strings of words are of the same length.  A concatenated substring in s is a substring that contains all the strings of any permutation of words concatenated.

from collections import Counter

class Solution:
    def findSubstring(self, s, words):
        if not s or not words:
            return []

        word_len = len(words[0])
        word_count = len(words)
        total_len = word_len * word_count
        word_freq = Counter(words)

        result = []

        for i in range(len(s) - total_len + 1):
            substring = s[i:i+total_len]
            substring_freq = Counter([substring[j:j+word_len] for j in range(0, total_len, word_len)])

            if substring_freq == word_freq:
                result.append(i)

        return result


sol = Solution()

s1 = "barfoothefoobarman"
words1 = ["foo", "bar"]
print(sol.findSubstring(s1, words1))  

s2 = "wordgoodgoodgoodbestword"
words2 = ["word", "good", "best", "word"]
print(sol.findSubstring(s2, words2))  

s3 = "barfoofoobarthefoobarman"
words3 = ["bar", "foo", "the"]
print(sol.findSubstring(s3, words3))  

