# Highest Frequency Remainder Count

## Problem Statement

Given an array of integers, find the remainder when each integer is divided by `n`, and return the highest frequency of any remainder.

## Example

For an array `[5, 9, 7, 10, 4]` and `n = 3`:
- Remainders when divided by 3 are `[2, 0, 1, 1, 1]`.
- Frequency of remainders: `{2: 1, 0: 1, 1: 3}`.
- The highest frequency is 3, which corresponds to remainder 1. Hence, 3 is the output.

## Implementation Details

### C++

```cpp
#include <iostream>
#include <vector>
#include <unordered_map>
#include <algorithm>

int highestFrequencyRemainder(const std::vector<int>& arr, int n) {
    std::unordered_map<int, int> remainderFreq;

    for (int num : arr) {
        int remainder = num % n;
        remainderFreq[remainder]++;
    }

    int maxFrequency = 0;
    for (auto& pair : remainderFreq) {
        maxFrequency = std::max(maxFrequency, pair.second);
    }

    return maxFrequency;
}

int main() {
    std::vector<int> arr1 = {5, 9, 7, 10, 4};
    int n1 = 3;
    std::cout << "Test Case 1 - Highest frequency of remainder: " << highestFrequencyRemainder(arr1, n1) << std::endl;

    std::vector<int> arr2 = {};
    int n2 = 5;
    std::cout << "Test Case 2 - Highest frequency of remainder: " << highestFrequencyRemainder(arr2, n2) << std::endl;

    std::vector<int> arr3 = {10, 20, 30};
    int n3 = 5;
    std::cout << "Test Case 3 - Highest frequency of remainder: " << highestFrequencyRemainder(arr3, n3) << std::endl;

    std::vector<int> arr4 = {1000, 2000, 3000, 4000};
    int n4 = 7;
    std::cout << "Test Case 4 - Highest frequency of remainder: " << highestFrequencyRemainder(arr4, n4) << std::endl;

    return 0;
}
```
### Java

```java
import java.util.*;

public class HighestFrequencyRemainder {

    public static int highestFrequencyRemainder(int[] arr, int n) {
        Map<Integer, Integer> remainderFreq = new HashMap<>();

        for (int num : arr) {
            int remainder = num % n;
            remainderFreq.put(remainder, remainderFreq.getOrDefault(remainder, 0) + 1);
        }

        int maxFrequency = 0;
        for (int count : remainderFreq.values()) {
            maxFrequency=Math.max(maxFrequency, count);
        }

        return maxFrequency;
    }

    public static void main(String[] args) {
        int[] arr1 = {5, 9, 7, 10, 4};
        int n1 = 3;
        System.out.println("Test Case 1 - Highest frequency of remainder: " + highestFrequencyRemainder(arr1, n1));

        int[] arr2 = {};
        int n2 = 5;
        System.out.println("Test Case 2 - Highest frequency of remainder: " + highestFrequencyRemainder(arr2, n2));

        int[] arr3 = {10, 20, 30};
        int n3 = 5;
        System.out.println("Test Case 3 - Highest frequency of remainder: " + highestFrequencyRemainder(arr3, n3));

        int[] arr4 = {1000, 2000, 3000, 4000};
        int n4 = 7;
        System.out.println("Test Case 4 - Highest frequency of remainder: " + highestFrequencyRemainder(arr4, n4));
    }
}
```

### Test Cases
1. Input: `[5, 9, 7, 10, 4]`, `n = 3`
   - Expected Output: `3`

2. Input: `[]`, `n = 5`
   - Expected Output: `0`

3. Input: `[10, 20, 30]`, `n = 5`
   - Expected Output: `3`

4. Input: `[1000, 2000, 3000, 4000]`, `n = 7`
   - Expected Output: `1`

5. Input: `[10, 20, 30, 40]`, `n = 10`
   - Expected Output: `4`

6. Input: `[5]`, `n = 3`
   - Expected Output: `1`

7. Input: `[2, 4, 6, 8]`, `n = 3`
   - Expected Output: `2`

8. Input: `[-5, -9, 7, 10, 4]`, `n = 3`
   - Expected Output: `3`

9. Input: `[1, 2, 3, 4, 5, 1, 2, 3, 4, 5, 1, 2, 3, 4, 5]`, `n = 3`
   - Expected Output: `6`

10. Input: `[100, 200, 300, 400]`, `n = 100`
    - Expected Output: `4`

