class Solution:
    def hasSameDigits(self, s: str) -> bool:
        iteration = 0  # Tracks how many layers of reduction have been done
        arr = list(s)  # mutable list of characters

        # Continue reducing until only two digits remain
        while len(arr) - iteration != 2:
            # Replace each character with the sum of adjacent digits (mod 10)
            for i in range(len(arr) - 1 - iteration):
                arr[i] = chr(((ord(arr[i]) - ord('0') + ord(arr[i+1]) - ord('0')) % 10) + ord('0'))
            iteration += 1

        # Return true if the final two digits are equal
        return arr[0] == arr[1]
