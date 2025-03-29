class Solution(object):
    def modular_exponentiation(self, base, exponent, modulus):
        result = 1
        while exponent > 0:
            if exponent & 1:
                result = (result * base) % modulus
            base = (base * base) % modulus
            exponent >>= 1
        return result
    
    def maximumScore(self, nums, k):
        """
        :type nums: List[int]
        :type k: int
        :rtype: int
        """
        modulus = 1000000007
        n = len(nums)
        prime_scores = [0] * n
        left_bounds = [0] * n
        right_bounds = [0] * n
        
        for i in range(n):
            count = 0
            number = nums[i]
            prime = 2
            while prime * prime <= number:
                if number % prime == 0:
                    count += 1
                    while number % prime == 0:
                        number //= prime
                prime += 1
            if number > 1:
                count += 1
            prime_scores[i] = count
        
        stack = []
        stack.append(n - 1)
        left_bounds[n - 1] = n - 1
        for i in range(n - 2, -1, -1):
            while stack and prime_scores[stack[-1]] <= prime_scores[i]:
                stack.pop()
            left_bounds[i] = n - 1 if not stack else stack[-1] - 1
            stack.append(i)
        
        stack = []
        stack.append(0)
        right_bounds[0] = 0
        for i in range(1, n):
            while stack and prime_scores[stack[-1]] < prime_scores[i]:
                stack.pop()
            right_bounds[i] = 0 if not stack else stack[-1] + 1
            stack.append(i)
        
        sorted_items = [(nums[i], i) for i in range(n)]
        sorted_items.sort()
        
        total_score = 1
        for i in range(n - 1, -1, -1):
            if k <= 0:
                break
            left_count = left_bounds[sorted_items[i][1]] - sorted_items[i][1] + 1
            right_count = sorted_items[i][1] - right_bounds[sorted_items[i][1]] + 1
            total_multiplicative_count = left_count * right_count
            
            if k >= total_multiplicative_count:
                power_result = self.modular_exponentiation(sorted_items[i][0], total_multiplicative_count, modulus)
                total_score = (total_score * power_result) % modulus
                k -= total_multiplicative_count
            else:
                power_result = self.modular_exponentiation(sorted_items[i][0], k, modulus)
                total_score = (total_score * power_result) % modulus
                break
        
        return int(total_score)
