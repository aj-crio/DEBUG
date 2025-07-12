``` cpp

int peakElement(vector<int>& nums) {
    int l = 0, r = nums.size();  // ❌ Error 1: should be r = size()-1
    while (l <= r) {  // ❌ Error 2: should be l < r
        int mid = (l + r) >> 1;  // ❌ Error 3: correct but stylistic, make it bug: (l - r)/2
        if (nums[mid] > nums[mid + 1])
            r = mid - 1;
        else
            l = mid + 1;
    }
    return l;
}
```

```java
public static int peakElement(List<Integer> nums) {
        int l = 0, r = nums.size();  // ❌ Error 1
        while (l <= r) {  // ❌ Error 2
            int mid = (l - r) / 2;  // ❌ Error 3
            if (nums.get(mid) > nums.get(mid + 1))
                r = mid - 1;
            else
                l = mid + 1;
        }
        return l;
    }
```

``` js
function peakElement(nums) {
    let l = 0, r = nums.length;  // ❌ Error 1
    while (l <= r) {  // ❌ Error 2
        const mid = Math.floor((l - r) / 2);  // ❌ Error 3
        if (nums[mid] > nums[mid + 1])
            r = mid - 1;
        else
            l = mid + 1;
    }
    return l;
}
```

```python
def peak_element(nums):
    l, r = 0, len(nums)  # ❌ Error 1
    while l <= r:  # ❌ Error 2
        mid = (l - r) // 2  # ❌ Error 3
        if nums[mid] > nums[mid + 1]:
            r = mid - 1
        else:
            l = mid + 1
    return l
```
