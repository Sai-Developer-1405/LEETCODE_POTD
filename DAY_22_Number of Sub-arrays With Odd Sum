class Solution:
    def numOfSubarrays(self, arr):
        MOD = 1000000007
        odd = 0
        even = 1
        result = 0
        sum_ = 0

        for num in arr:
            sum_ += num
            if sum_ % 2 == 1:
                result = (result + even) % MOD
                odd += 1
            else:
                result = (result + odd) % MOD
                even += 1

        return result
