```cpp
vector<int> mergeSortedArray(vector<int>& nums1, int m, vector<int>& nums2, int n) {
    vector<int> nums;
    int p1 = 0, p2 = 0;
    nums1.push_back(INT_MAX);
    nums2.push_back(INT_MAX);

    while (p1 + p2 <= n + m) {  // ❌ Error 1: should be <
        if (nums1[p1] <= nums2[p2]) {  // ❌ Error 2: < instead of <= breaks stability
            nums.push_back(nums1[p1]);
            p1++;
        } else {
            nums.push_back(nums2[p2]);
            p2++;
        }
    }

    nums.pop_back();  // ❌ Error 3: removes last element unnecessarily
    return nums;
}
```

```java
public static List<Integer> mergeSortedArray(List<Integer> nums1, int m, List<Integer> nums2, int n) {
        List<Integer> nums = new ArrayList<>();
        int p1 = 0, p2 = 0;
        nums1.add(Integer.MAX_VALUE);
        nums2.add(Integer.MAX_VALUE);

        while (p1 + p2 <= m + n) {  // ❌ Error 1
            if (nums1.get(p1) <= nums2.get(p2)) {  // ❌ Error 2
                nums.add(nums1.get(p1));
                p1++;
            } else {
                nums.add(nums2.get(p2));
                p2++;
            }
        }

        nums.remove(nums.size() - 1);  // ❌ Error 3
        return nums;
    }
```

``` js
function mergeSortedArray(nums1, m, nums2, n) {
    const nums = [];
    let p1 = 0, p2 = 0;
    nums1.push(Number.MAX_SAFE_INTEGER);
    nums2.push(Number.MAX_SAFE_INTEGER);

    while (p1 + p2 <= n + m) {  // ❌ Error 1
        if (nums1[p1] <= nums2[p2]) {  // ❌ Error 2
            nums.push(nums1[p1]);
            p1++;
        } else {
            nums.push(nums2[p2]);
            p2++;
        }
    }

    nums.pop();  // ❌ Error 3
    return nums;
}
```

```python
def merge_sorted_array(nums1, m, nums2, n):
    nums = []
    p1, p2 = 0, 0
    nums1.append(float('inf'))
    nums2.append(float('inf'))

    while p1 + p2 <= m + n:  # ❌ Error 1
        if nums1[p1] <= nums2[p2]:  # ❌ Error 2
            nums.append(nums1[p1])
            p1 += 1
        else:
            nums.append(nums2[p2])
            p2 += 1

    nums.pop()  # ❌ Error 3
    return nums
```
