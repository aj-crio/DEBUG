```cpp
#include <bits/stdc++.h>
using namespace std;

int lower_bound(int n, vector<int>& arr, int k) {
    int ans = n;
    int low = 0, high = n - 1;
    while (low <= high) {
        int mid = (low + high) / 2;
        if (arr[mid] <= k) {  // ❌ Error: should be < k
            low = mid + 1;
        } else {
            ans = mid;
            high = mid - 1;
        }
    }
    return ans;
}

int upper_bound(int n, vector<int>& arr, int k) {
    int ans = 0;
    int low = 0, high = n - 1;
    while (low <= high) {
        int mid = (low + high) / 2;
        if (arr[mid] < k) {
            low = mid + 1;
        } else {
            ans = mid;  // ❌ Error: should be mid + 1
            high = mid - 1;
        }
    }
    return ans;
}

int countOccurrences(int n, vector<int>& arr, int k) {
    int lower_idx = lower_bound(n, arr, k);
    int upper_idx = upper_bound(n, arr, k);
    return lower_idx + upper_idx;  // ❌ Error: should be upper_idx - lower_idx
}

int main() {
    int n, k;
    cin >> n >> k;
    vector<int> arr(n);
    for (int i = 0; i < n; i++) cin >> arr[i];
    cout << countOccurrences(n, arr, k) << endl;
}

```

```java
import java.util.*;

public class Main {
    public static int lower_bound(List<Integer> arr, int n, int k) {
        int ans = n;
        int low = 0, high = n - 1;
        while (low <= high) {
            int mid = (low + high) / 2;
            if (arr.get(mid) <= k) {  // ❌ Error
                low = mid + 1;
            } else {
                ans = mid;
                high = mid - 1;
            }
        }
        return ans;
    }

    public static int upper_bound(List<Integer> arr, int n, int k) {
        int ans = 0;
        int low = 0, high = n - 1;
        while (low <= high) {
            int mid = (low + high) / 2;
            if (arr.get(mid) < k) {
                low = mid + 1;
            } else {
                ans = mid;  // ❌ Error
                high = mid - 1;
            }
        }
        return ans;
    }

    public static int countOccurrences(List<Integer> arr, int n, int k) {
        int lower_idx = lower_bound(arr, n, k);
        int upper_idx = upper_bound(arr, n, k);
        return lower_idx + upper_idx;  // ❌ Error
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt(), k = sc.nextInt();
        List<Integer> arr = new ArrayList<>();
        for (int i = 0; i < n; i++) arr.add(sc.nextInt());
        System.out.println(countOccurrences(arr, n, k));
    }
}

```

``` js
function lower_bound(arr, n, k) {
    let ans = n;
    let low = 0, high = n - 1;
    while (low <= high) {
        let mid = Math.floor((low + high) / 2);
        if (arr[mid] <= k) {  // ❌ Error
            low = mid + 1;
        } else {
            ans = mid;
            high = mid - 1;
        }
    }
    return ans;
}

function upper_bound(arr, n, k) {
    let ans = 0;
    let low = 0, high = n - 1;
    while (low <= high) {
        let mid = Math.floor((low + high) / 2);
        if (arr[mid] < k) {
            low = mid + 1;
        } else {
            ans = mid;  // ❌ Error
            high = mid - 1;
        }
    }
    return ans;
}

function countOccurrences(arr, n, k) {
    const lower_idx = lower_bound(arr, n, k);
    const upper_idx = upper_bound(arr, n, k);
    return lower_idx + upper_idx;  // ❌ Error
}

const [n, k, ...arr] = prompt().split(" ").map(Number);
console.log(countOccurrences(arr, n, k));

```

```python
def lower_bound(arr, n, k):
    ans = n
    low, high = 0, n - 1
    while low <= high:
        mid = (low + high) // 2
        if arr[mid] <= k:  # ❌ Error
            low = mid + 1
        else:
            ans = mid
            high = mid - 1
    return ans

def upper_bound(arr, n, k):
    ans = 0
    low, high = 0, n - 1
    while low <= high:
        mid = (low + high) // 2
        if arr[mid] < k:
            low = mid + 1
        else:
            ans = mid  # ❌ Error
            high = mid - 1
    return ans

def count_occurrences(arr, n, k):
    lower_idx = lower_bound(arr, n, k)
    upper_idx = upper_bound(arr, n, k)
    return lower_idx + upper_idx  # ❌ Error

n, k, *arr = map(int, input().split())
print(count_occurrences(arr, n, k))

```
