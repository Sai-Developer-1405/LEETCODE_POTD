class Solution(object):
    def maxOperations(self, s):
        """
        :type s: str
        :rtype: int
        """
        s += '1'
        s = s.split('0')
        ret = 0
        cnt = 0
        for i in range(len(s) - 1):
            if s[i]:
                cnt += len(s[i])
                ret += cnt
        return ret
