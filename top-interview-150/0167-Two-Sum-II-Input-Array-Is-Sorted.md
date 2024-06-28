# Problem 167. Two Sum II - Input Array Is Sorted

> [!NOTE]
> [167. Two Sum II - Input Array Is Sorted](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/description/?envType=study-plan-v2&envId=top-interview-150)

Given a `1-indexed` array of integers `numbers` that is already sorted in **non-decreasing** order, find two numbers such that they add up to a specific `target` number. Let these two numbers be `numbers[index1]` and `numbers[index2]` where `1 <= index1 < index2 <= numbers.length`.

Return the indices of the two numbers, `index1` and `index2`, added by one as an integer array `[index1, index2]` of length `2`.

The tests are generated such that there is exactly one solution. You may not use the same element twice.

Your solution must use only constant extra space.

### Examples

#### Example 1:

> **Input**: `numbers = [2,7,11,15], target = 9`
>
> **Output**: `[1,2]`
>
> **Explanation**: `The sum of 2 and 7 is 9. Therefore, index1 = 1, index2 = 2. We return [1, 2].`

#### Example 2:

> **Input**: `numbers = [2,3,4], target = 6`
> **Output**: `[1,3]`
> **Explanation**: `The sum of 2 and 4 is 6. Therefore index1 = 1, index2 = 3. We return [1, 3].`

#### Example 3:

> **Input**: `numbers = [-1,0], target = -1`
> **Output**: `[1,2]`
> **Explanation**: `The sum of -1 and 0 is -1. Therefore index1 = 1, index2 = 2. We return [1, 2].`

#### Constraints:

- `2 <= numbers.length <= 3 * 104`
- `-1000 <= numbers[i] <= 1000`
- `numbers is sorted in non-decreasing order.`
- `-1000 <= target <= 1000`
- `The tests are generated such that there is exactly one solution.`

## Solutions

### Solution 1

```java
public int[] twoSum(int[] numbers, int target) {
    int len = numbers.length;
    int l = 0;
    int r = len - 1;
    while (l < r) {
        int sum = numbers[l] + numbers[r];
        if (sum == target) {
            break;
        } else if ((sum > target || numbers[r] > target) && sum >= 0) {
            r--;
        } else {
            l++;
        }
    }
    return new int[]{l + 1, r + 1};
}
```

#### Complexities

- `Time Complexity`: O(n)
    - where `n` is the number of elements in the input array
    - iterate through the array once using two pointers, and the pointers move towards each other until they find the target sum.
- `Space Complexity`: O(1)
    - use a constant amount of extra space regardless of the size of the input array.

### Solution 2

```java
public int[] twoSum(int[] numbers, int target) {
    int l = 0;
    int r = numbers.length - 1;
    int sum = numbers[l] + numbers[r];
    // Since we have a guaranteed sum = target. 
    while (sum != target) {
        if (sum > target) {
            r--;
        } else {
            l++;
        }
        sum = numbers[l] + numbers[r];
    }
    return new int[]{l + 1, r + 1};
}
```

#### Complexities

- `Time Complexity`: O(n)
    - where `n` is the number of elements in the input array
    - iterate through the array once using two pointers, and the pointers move towards each other until they find the target sum.
- `Space Complexity`: O(1)
    - use a constant amount of extra space regardless of the size of the input array.

> [!TIP]
> `Solution 2` is a little faster an simplified, however both solutions have the same complexities.
