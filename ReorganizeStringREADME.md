# leet-day40

# Reorganize String

## Problem Description

Given a string `s`, you need to rearrange its characters such that no two adjacent characters are the same. Return any possible rearrangement of `s` or an empty string if not possible.

## Example

### Input
```
s = "aab"
```
### Output
```
"aba"
```

## Constraints

- 1 <= s.length <= 500
- s consists of lowercase English letters.

## Approach

The given problem can be approached using a greedy strategy. The idea is to arrange the characters in decreasing order of their frequencies while making sure that no two adjacent characters are the same.

1. Count the frequency of each character in the string.
2. Use a max heap to prioritize characters with higher frequencies.
3. Iterate through the max heap to construct the rearranged string.
4. If at any point, two characters with the same frequency are adjacent in the rearranged string, switch to the second most frequent character.
5. Reinsert characters into the max heap if needed to ensure no two adjacent characters are the same.

## Implementation

1. Define a `std::unordered_map` to count the frequency of each character in the string.
2. Use a `std::priority_queue` (max heap) to prioritize characters based on their frequencies.
3. Initialize an empty string `result` to store the rearranged string.
4. Iterate while the max heap is not empty:
   - Pop the character with the highest frequency from the max heap.
   - If the result is empty or the last character of the result is not the same as the popped character, add the popped character to the result.
   - If the popped character has frequency greater than 1, push it back to the max heap with frequency decreased by 1.
   - If the last character of the result is the same as the popped character, pop the second character from the max heap and add it to the result.
   - Push the original character back to the max heap with frequency decreased by 1.
5. After the loop, return the `result`.

## Usage

1. Provide the input string `s`.
2. Create an instance of the `Solution` class.
3. Call the `reorganizeString` function with the input string to get the rearranged result.

```cpp
std::string result = solution.reorganizeString(s);
```

## Complexity Analysis

- Time Complexity: O(n log k), where n is the length of the input string and k is the number of unique characters. The code involves counting the frequency of each character and performing operations on a max heap.
- Space Complexity: O(k), where k is the number of unique characters. The code uses space for the character frequency hash map and the max heap.
