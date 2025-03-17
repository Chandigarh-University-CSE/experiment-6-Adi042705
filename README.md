Perfect Squares:
public class Solution {
    public int numSquares(int n) {
       int[] dp = new int[n + 1];
       Arrays.fill(dp, Integer.MAX_VALUE);
       dp[0] = 0;
       for(int i = 0; i <= n; i++){
           for(int j = 1; i + j * j <= n; j++){
               dp[i  + j * j] = Math.min(dp[i + j * j], dp[i] + 1);
            }
       }
       return dp[n];
    }
}
House Robber
class Solution {
    public int rob(int[] nums) {
        int n = nums.length;
        if (n == 1) return nums[0];

        int prev1 = 0, prev2 = 0;
        for (int num : nums) {
            int temp = prev1;
            prev1 = Math.max(prev2 + num, prev1);
            prev2 = temp;
        }
        return prev1;
    }
}
Longest Increasing Subsequence
class Solution {
    public int lengthOfLIS(int[] nums) {
        List<Integer> res = new ArrayList<>();

        for (int n : nums) {
            if (res.isEmpty() || res.get(res.size() - 1) < n) {
                res.add(n);
            } else {
                int idx = binarySearch(res, n);
                res.set(idx, n);
            }
        }

        return res.size();        
    }

    private int binarySearch(List<Integer> arr, int target) {
        int left = 0;
        int right = arr.size() - 1;

        while (left <= right) {
            int mid = (left + right) / 2;
            if (arr.get(mid) == target) {
                return mid;
            } else if (arr.get(mid) > target) {
                right = mid - 1;
            } else {
                left = mid + 1;
            }
        }

        return left;
    }    
}
