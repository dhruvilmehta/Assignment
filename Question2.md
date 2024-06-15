# Mode of an Array

## Problem Statement

Given an array of integers, find the mode (the value that appears most frequently).

If input is empty, return 0.

## C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <unordered_map>
#include <algorithm>

int findMode(const std::vector<int>& arr) {
    if (arr.empty()) {
        return 0;
    }
    std::unordered_map<int, int> freq;

    for (int num : arr) {
        freq[num]++;
    }

    int mode = arr[0];
    int maxFreq = freq[arr[0]];

    for (auto& pair : freq) {
        if (pair.second > maxFreq) {
            mode = pair.first;
            maxFreq = pair.second;
        }
    }

    return mode;
}

int main() {
    std::vector<int> arr1 = {5, 9, 7, 10, 4, 7, 7};
    std::cout << "Test Case 1 - Mode of the array: " << findMode(arr1) << std::endl;

    std::vector<int> arr2 = {3, 3, 1, 2, 2, 3};
    std::cout << "Test Case 2 - Mode of the array: " << findMode(arr2) << std::endl;

    std::vector<int> arr3 = {10, 10, 20, 20, 30, 30, 30};
    std::cout << "Test Case 3 - Mode of the array: " << findMode(arr3) << std::endl;

    return 0;
}
```
### Java
```Java
import java.util.*;

public class ModeOfArray {

    public static int findMode(int[] arr) {
        if (arr.length == 0) {
            return 0;
        }
        Map<Integer, Integer> freq = new HashMap<>();

        for (int num : arr) {
            freq.put(num, freq.getOrDefault(num, 0) + 1);
        }

        int mode = arr[0];
        int maxFreq = freq.get(arr[0]);

        for (Map.Entry<Integer, Integer> entry : freq.entrySet()) {
            if (entry.getValue() > maxFreq) {
                mode = entry.getKey();
                maxFreq = entry.getValue();
            }
        }

        return mode;
    }

    public static void main(String[] args) {
        int[] arr1 = {5, 9, 7, 10, 4, 7, 7};
        System.out.println("Test Case 1 - Mode of the array: " + findMode(arr1));

        int[] arr2 = {3, 3, 1, 2, 2, 3};
        System.out.println("Test Case 2 - Mode of the array: " + findMode(arr2));

        int[] arr3 = {10, 10, 20, 20, 30, 30, 30};
        System.out.println("Test Case 3 - Mode of the array: " + findMode(arr3));
    }
}
```
## Test Cases

1. **Input:** `[5, 9, 7, 10, 4, 7, 7]`
   - **Expected Output:** `7`

2. **Input:** `[3, 3, 1, 2, 2, 3]`
   - **Expected Output:** `3`

3. **Input:** `[10, 10, 20, 20, 30, 30, 30]`
   - **Expected Output:** `10`

4. **Input:** `[1, 1, 1, 2, 2, 2, 3, 3, 3]`
   - **Expected Output:** `1`

5. **Input:** `[]` (empty array)
   - **Expected Output:** `0`

6. **Input:** `[10]` (single element)
   - **Expected Output:** `10`

7. **Input:** `[1, 2, 3, 4, 5, 6, 7, 8, 9, 10]`
   - **Expected Output:** `1`

8. **Input:** `[-5, -5, -5, 0, 0, 0, 5, 5, 5]`
   - **Expected Output:** `-5`

9. **Input:** `[1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 10, 10, 10, 10]`
   - **Expected Output:** `10`

10. **Input:** `[100, 100, 200, 200, 300, 300, 400, 400, 500, 500]`
    - **Expected Output:** `100`