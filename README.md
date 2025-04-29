# leetcode----2962
Count Subarrays Where Max Element Appears at Least k Times
//code in java
class Solution {
    public long countSubarrays(int[] nums, int k) {
        int max = Integer.MIN_VALUE;
        int n = nums.length;
        
        // Find the maximum element
        for (int num : nums) {
            max = Math.max(max, num);
        }
        
        long ans = 0;
        int count = 0;
        int left = 0;
        
        for (int right = 0; right < n; right++) {
            if (nums[right] == max) {
                count++;
            }
            
            // Shrink the window until we have count >= k
            while (count >= k) {
                if (nums[left] == max) {
                    count--;
                }
                left++;
            }
            
            ans += left;
        }
        
        return ans;
    }
}
