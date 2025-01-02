### Code: Binary Search, Lower Bound, and Upper Bound in C++
```cpp
#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

// Binary Search Function
bool binarySearch(const vector<int>& arr, int target) {
    int left = 0, right = arr.size() - 1;
    while (left <= right) {
        int mid = left + (right - left) / 2;
        if (arr[mid] == target)
            return true;
        else if (arr[mid] < target)
            left = mid + 1;
        else
            right = mid - 1;
    }
    return false;
}

// Lower Bound Function
int lowerBound(const vector<int>& arr, int target) {
    int left = 0, right = arr.size();
    while (left < right) {
        int mid = left + (right - left) / 2;
        if (arr[mid] < target)
            left = mid + 1;
        else
            right = mid;
    }
    return left;
}

// Upper Bound Function
int upperBound(const vector<int>& arr, int target) {
    int left = 0, right = arr.size();
    while (left < right) {
        int mid = left + (right - left) / 2;
        if (arr[mid] <= target)
            left = mid + 1;
        else
            right = mid;
    }
    return left;
}

int main() {
    vector<int> arr = {1, 3, 3, 5, 7, 9, 11}; // Sorted array
    int target = 3;

    // Binary Search
    cout << "Binary Search: " << (binarySearch(arr, target) ? "Found" : "Not Found") << endl;

    // Lower Bound
    int lb = lowerBound(arr, target);
    cout << "Lower Bound: Index " << lb << ", Value " << (lb < arr.size() ? arr[lb] : -1) << endl;

    // Upper Bound
    int ub = upperBound(arr, target);
    cout << "Upper Bound: Index " << ub << ", Value " << (ub < arr.size() ? arr[ub] : -1) << endl;

    return 0;
}
```

---

### Explanation

1. **Binary Search:**
   - Used to check if a `target` element exists in a **sorted array**.
   - Returns `true` if found, otherwise `false`.
   - The time complexity is \(O(\log N)\).

2. **Lower Bound:**
   - Finds the first position where an element is **not less than the `target`**.
   - Returns the **index of the first occurrence** of the `target` or the first element greater than it.
   - Time complexity: \(O(\log N)\).

3. **Upper Bound:**
   - Finds the first position where an element is **greater than the `target`**.
   - Returns the **index of the first greater element**.
   - Time complexity: \(O(\log N)\).

---

### Output Example

For the array `{1, 3, 3, 5, 7, 9, 11}` and `target = 3`:
```
Binary Search: Found
Lower Bound: Index 1, Value 3
Upper Bound: Index 3, Value 5
```

---

Let me know if you need further explanation or examples!