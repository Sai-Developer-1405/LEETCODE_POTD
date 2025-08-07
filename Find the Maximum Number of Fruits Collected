class Solution:
    def maxCollectedFruits(self, fruits: List[List[int]]) -> int:
        size = len(fruits)
        total = 0
        for i in range(size):
            total += fruits[i][i]

        right_path = [fruits[0][size - 1], 0, 0]
        bottom_path = [fruits[size - 1][0], 0, 0]
        window = 2

        for step in range(1, size - 1):
            new_right = [0] * (window + 2)
            new_bottom = [0] * (window + 2)
            for dist in range(window):
                new_bottom[dist] = (
                    max(bottom_path[dist - 1], bottom_path[dist], bottom_path[dist + 1])
                    + fruits[size - 1 - dist][step]
                )

                new_right[dist] = (
                    max(right_path[dist - 1], right_path[dist], right_path[dist + 1])
                    + fruits[step][size - 1 - dist]
                )

            bottom_path = new_bottom
            right_path = new_right

            if window - size + 4 + step <= 1:
                window += 1
            elif window - size + 3 + step > 1:
                window -= 1

        return total + right_path[0] + bottom_path[0]
