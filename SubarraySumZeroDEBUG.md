```cpp
string subArrayExists(int n, vector<int> arr) {
    string result = "No";  // ❌ Error 1: hardcoded
    int cursum = 0;
    unordered_set<int> sumSet;

    for (int i = 0; i <= n; i++) {  // ❌ Error 2: should be i < n
        cursum += arr[i];

        if (cursum != 0 && sumSet.find(cursum) != sumSet.end())  // ❌ Error 3: incorrect check
            return "Yes";

        sumSet.insert(cursum);
    }

    return result;
}
```

```java
import java.util.*;

public class Main {
    public static String subArrayExists(int n, List<Integer> arr) {
        String result = "No";  // ❌ Error 1
        int cursum = 0;
        Set<Integer> sumSet = new HashSet<>();

        for (int i = 0; i <= n; i++) {  // ❌ Error 2
            cursum += arr.get(i);

            if (cursum != 0 && sumSet.contains(cursum)) {  // ❌ Error 3
                return "Yes";
            }

            sumSet.add(cursum);
        }

        return result;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        List<Integer> arr = new ArrayList<>();
        for (int i = 0; i < n; i++) arr.add(sc.nextInt());
        System.out.println(subArrayExists(n, arr));
    }
}

```

``` js
function subArrayExists(n, arr) {
    let result = "No";  // ❌ Error 1
    let cursum = 0;
    const sumSet = new Set();

    for (let i = 0; i <= n; i++) {  // ❌ Error 2
        cursum += arr[i];

        if (cursum !== 0 && sumSet.has(cursum)) {  // ❌ Error 3
            return "Yes";
        }

        sumSet.add(cursum);
    }

    return result;
}
```

```python
def sub_array_exists(n, arr):
    result = "No"  # ❌ Error 1
    cursum = 0
    sum_set = set()

    for i in range(0, n + 1):  # ❌ Error 2
        cursum += arr[i]

        if cursum != 0 and cursum in sum_set:  # ❌ Error 3
            return "Yes"

        sum_set.add(cursum)

    return result
```
