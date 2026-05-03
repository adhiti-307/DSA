# Two Sum Variations (LeetCode Practice)

---

## 1. Two Sum

### Problem Statement
Given an array of integers `nums` and an integer `target`, return indices of the two numbers such that they add up to the target.

### Input
nums = [2,7,11,15], target = 9

### Output
[0,1]

### Explanation
nums[0] + nums[1] = 2 + 7 = 9

### Java Code
```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        HashMap<Integer, Integer> map = new HashMap<>();
        
        for(int i = 0; i < nums.length; i++){
            int complement = target - nums[i];
            
            if(map.containsKey(complement)){
                return new int[]{map.get(complement), i};
            }
            
            map.put(nums[i], i);
        }
        
        return new int[]{};
    }
}
````

---

## 2. Two Sum II - Input Array Is Sorted

### Problem Statement

Given a sorted array of integers, find two numbers such that they add up to a specific target number.

### Input

numbers = [2,7,11,15], target = 9

### Output

[1,2]

### Explanation

Using two pointers, 2 + 7 = 9.

### Java Code

```java
class Solution {
    public int[] twoSum(int[] numbers, int target) {
        int low = 0;
        int high = numbers.length - 1;

        while (low < high) {
            int sum = numbers[low] + numbers[high];

            if (sum == target) {
                return new int[]{low + 1, high + 1};
            } else if (sum > target) {
                high--;
            } else {
                low++;
            }
        }

        return new int[]{}; // fallback (problem guarantees one solution)
    }
}

```

---

## 3. Two Sum Less Than K

### Problem Statement

Find the maximum sum of two numbers less than K.

### Input

nums = [10,20,30], k = 15

### Output

-1

### Explanation

No pair has sum less than 15.

### Java Code

```java
class Solution {
    public int twoSumLessThanK(int[] nums, int k) {
        Arrays.sort(nums);

        int low = 0;
        int high = nums.length - 1;
        int maxSum = -1;

        while (low < high) {
            int sum = nums[low] + nums[high];

            if (sum < k) {
                maxSum = Math.max(maxSum, sum);
                low++;
            } else {
                high--;
            }
        }

        return maxSum;
    }
}
```

---

## 4. Max Number of K-Sum Pairs

### Problem Statement

Return the maximum number of operations where you pick two numbers that sum to k.

### Input

nums = [1,2,3,4], k = 5

### Output

2

### Explanation

Pairs: (1,4), (2,3)

### Java Code

```java
class Solution {
    public int maxOperations(int[] nums, int k) {
        HashMap<Integer, Integer> map = new HashMap<>();
        int count = 0;

        for (int num : nums) {
            int complement = k - num;

            if (map.getOrDefault(complement, 0) > 0) {
                count++;
                map.put(complement, map.get(complement) - 1);
            } else {
                map.put(num, map.getOrDefault(num, 0) + 1);
            }
        }

        return count;
    }
}
```

---

## 5. 3Sum

### Problem Statement

Find all unique triplets in the array which gives the sum of zero.

### Input

nums = [-1,0,1,2,-1,-4]

### Output

[[-1,-1,2], [-1,0,1]]

### Explanation

Triplets sum to zero.

### Java Code

```java
class Solution {
    public List<List<Integer>> threeSum(int[] nums) {
        List<List<Integer>> ans = new ArrayList<>();
        Arrays.sort(nums);

        for (int i = 0; i < nums.length - 2; i++) {

            // Skip duplicate elements for i
            if (i > 0 && nums[i] == nums[i - 1]) continue;

            int left = i + 1;
            int right = nums.length - 1;

            while (left < right) {
                int sum = nums[i] + nums[left] + nums[right];

                if (sum == 0) {
                    ans.add(Arrays.asList(nums[i], nums[left], nums[right]));

                    left++;
                    right--;

                    // Skip duplicates for left
                    while (left < right && nums[left] == nums[left - 1]) left++;

                    // Skip duplicates for right
                    while (left < right && nums[right] == nums[right + 1]) right--;

                } else if (sum < 0) {
                    left++;
                } else {
                    right--;
                }
            }
        }

        return ans;
    }
}
```

---

## 6. 3Sum Closest

### Problem Statement

Find three integers such that the sum is closest to a given target.

### Input

nums = [-1,2,1,-4], target = 1

### Output

2

### Explanation

Closest sum is 2.

### Java Code

```java
class Solution {
    public int threeSumClosest(int[] nums, int target) {
        Arrays.sort(nums);
        int closestSum = nums[0] + nums[1] + nums[2];

        for (int i = 0; i < nums.length - 2; i++) {

            int left = i + 1;
            int right = nums.length - 1;

            while (left < right) {
                int sum = nums[i] + nums[left] + nums[right];

                // Update closest sum
                if (Math.abs(sum - target) < Math.abs(closestSum - target)) {
                    closestSum = sum;
                }

                if (sum < target) {
                    left++;
                } else if (sum > target) {
                    right--;
                } else {
                    return sum; // exact match
                }
            }
        }

        return closestSum;
    }
}
```

---

## 7. 4Sum

### Problem Statement

Find all unique quadruplets that sum to a target.

### Input

nums = [1,0,-1,0,-2,2], target = 0

### Output

[[-2,-1,1,2], [-2,0,0,2], [-1,0,0,1]]

### Explanation

All quadruplets sum to target.

### Java Code

```java
List<List<Integer>> ans = new ArrayList<>();
        Arrays.sort(nums);
        int n = nums.length;

        for (int i = 0; i < n - 3; i++) {

            // Skip duplicate i
            if (i > 0 && nums[i] == nums[i - 1]) continue;

            for (int j = i + 1; j < n - 2; j++) {

                // Skip duplicate j
                if (j > i + 1 && nums[j] == nums[j - 1]) continue;

                int left = j + 1;
                int right = n - 1;

                while (left < right) {
                    long sum = (long) nums[i] + nums[j] + nums[left] + nums[right];

                    if (sum == target) {
                        ans.add(Arrays.asList(nums[i], nums[j], nums[left], nums[right]));

                        left++;
                        right--;

                        // Skip duplicates for left
                        while (left < right && nums[left] == nums[left - 1]) left++;

                        // Skip duplicates for right
                        while (left < right && nums[right] == nums[right + 1]) right--;

                    } else if (sum < target) {
                        left++;
                    } else {
                        right--;
                    }
                }
            }
        }

        return ans;
```

---

## 8. Subarray Sum Equals K

### Problem Statement

Find the total number of continuous subarrays whose sum equals k.

### Input

nums = [1,1,1], k = 2

### Output

2

### Explanation

Subarrays: [1,1] at indices (0,1) and (1,2)

### Java Code

```java
class Solution {
    public int subarraySum(int[] nums, int k) {
        HashMap<Integer, Integer> map = new HashMap<>();

        int sum = 0;
        int count = 0;
        map.put(0,1);

        for(int num : nums){
            sum +=num;

            if(map.containsKey(sum - k)){
                count += map.get(sum - k);
            }
            map.put(sum,map.getOrDefault(sum,0)+1 );
        }
        return count;
    }
}
```

---

## 9. Continuous Subarray Sum

### Problem Statement

Check if the array has a continuous subarray of size at least 2 whose sum is a multiple of k.

### Input

nums = [23,2,4,6,7], k = 6

### Output

true

### Explanation

Subarray [2,4] sums to 6.

### Java Code

```java
class Solution {
    public boolean checkSubarraySum(int[] nums, int k) {
         HashMap<Integer, Integer> map = new HashMap<>();

        map.put(0, -1); 
        int sum = 0;

        for (int i = 0; i < nums.length; i++) {
            sum += nums[i];

            int rem = (k != 0) ? sum % k : sum; 

            if (map.containsKey(rem)) {
                if (i - map.get(rem) >= 2) {
                    return true;
                }
            } else {
                map.put(rem, i);
            }
        }

        return false;
    }
}
```

---

## 10. Count Number of Nice Subarrays

### Problem Statement

Return number of subarrays with exactly k odd numbers.

### Input

nums = [1,1,2,1,1], k = 3

### Output

2

### Explanation

Valid subarrays contain exactly 3 odd numbers.

### Java Code

```java
class Solution {
    public int numberOfSubarrays(int[] nums, int k) {
        HashMap<Integer, Integer> map = new HashMap<>();
        
        map.put(0, 1);
        int count = 0;
        int sum = 0;

        for (int num : nums) {
            // convert odd → 1, even → 0
            if (num % 2 != 0) {
                sum += 1;
            }

            if (map.containsKey(sum - k)) {
                count += map.get(sum - k);
            }

            map.put(sum, map.getOrDefault(sum, 0) + 1);
        }

        return count;
    }
}
```

---
