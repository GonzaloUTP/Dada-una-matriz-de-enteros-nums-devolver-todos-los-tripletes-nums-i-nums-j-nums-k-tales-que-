JOSE GONZALO DZUL UC  TICS GRUPO 4A
# Dada-una-matriz-de-enteros-nums-devolver-todos-los-tripletes-nums-i-nums-j-nums-k-tales-que-
/**
 * @param {number[]} nums
 * @return {number[][]}
 */
var threeSum = function(nums) {
    const n = nums.length;
    let res = [];
    nums.sort((a, b) => a - b);
    for (let i = 0; i < n - 2; i++) {
        // skip: if nums[i] > 0,
        // then nums[i] + nums[l] + nums[r] never = 0
        if (nums[i] > 0) break; 
        // skip same number
        if (i > 0 && nums[i] === nums[i - 1]) continue;
        let l = i + 1;
        let r = n - 1;
        while (l < r) {
            if (nums[i] + nums[l] + nums[r] === 0) {
                res.push([nums[i], nums[l++], nums[r--]]);
                // skip same number
                while (l < r && nums[l] === nums[l - 1]) l++;
                while (l < r && nums[r] === nums[r + 1]) r--;
            } else if (nums[i] + nums[l] + nums[r] > 0) {
                r--;
            } else {          
                l++;
            }  
        }
    }
    return res;
};
