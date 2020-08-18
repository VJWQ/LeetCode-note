- Sliding Window + Hashmap
  - HashMap + Two Pointers
- Sliding Window + Ordered Dictionary

### Python
```python
class Solution:
    def lengthOfLongestSubstringKDistinct(self, s: str, k: int) -> int:
        '''Sliding Window + Hashmap-1'''
        # n = len(s)
        # counter = {}
        # left = 0
        # max_len = 0
        # for right in range(n):
        #     counter[s[right]] = counter.get(s[right], 0) + 1
        #     while left <= right and len(counter) > k:
        #         counter[s[left]] -= 1
        #         if counter[s[left]] == 0:
        #             del counter[s[left]]
        #         left += 1

        #     max_len = max(max_len, right - left + 1)
        # return max_len
        
        
        '''Sliding Window + Hashmap-2'''
        # from collections import defaultdict
        # n = len(s) 
        # if k == 0 or n == 0:
        #     return 0
        # # sliding window left and right pointers
        # left, right = 0, 0
        # # hashmap character -> its rightmost position 
        # # in the sliding window
        # hashmap = defaultdict()

        # max_len = 1
        
        # while right < n:
        #     # add new character and move right pointer
        #     hashmap[s[right]] = right
        #     right += 1

        #     # slidewindow contains 3 characters
        #     if len(hashmap) == k + 1:
        #         # delete the leftmost character
        #         del_idx = min(hashmap.values())
        #         del hashmap[s[del_idx]]
        #         # move left pointer of the slidewindow
        #         left = del_idx + 1

        #     max_len = max(max_len, right - left)

        # return max_len
        
        
        '''Sliding Window + Ordered Dictionary'''
        n = len(s) 
        if k == 0 or n == 0:
            return 0
        
        # sliding window left and right pointers
        left, right = 0, 0
        # hashmap character -> its rightmost position 
        # in the sliding window
        hashmap = OrderedDict()

        max_len = 1
        
        while right < n:
            character = s[right]
            # if character is already in the hashmap -
            # delete it, so that after insert it becomes
            # the rightmost element in the hashmap
            if character in hashmap:
                del hashmap[character]
            hashmap[character] = right
            right += 1

            # slidewindow contains k + 1 characters
            if len(hashmap) == k + 1:
                # delete the leftmost character
                _, del_idx = hashmap.popitem(last = False)
                # move left pointer of the slidewindow
                left = del_idx + 1

            max_len = max(max_len, right - left)

        return max_len
```
