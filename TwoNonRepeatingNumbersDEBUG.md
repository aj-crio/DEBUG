
```cpp

vector<int> twoNonRepeatingNumbers(int arr[], int n) {
    int Xor = 0;  // ❌ Error 1: should initialize with arr[0]
    int set_bit_no;
    int x = 1, y = 1;  // ❌ Error 2: should start from 0

    for (int i = 0; i <= n; i++) {  // ❌ Error 3: should be i < n
        Xor ^= arr[i];
    }

    set_bit_no = Xor & (Xor - 1);  // ❌ Error 4: wrong formula

    for (int i = 0; i < n; i++) {
        if (arr[i] & set_bit_no) {
            x ^= arr[i];
        } else {
            y ^= arr[i];
        }
    }

    vector<int> d = {x, y};
    sort(d.begin(), d.end());
    return d;
}
```

```java
    public static List<Integer> twoNonRepeatingNumbers(int[] arr) {
        int Xor = 0;  // ❌ Error 1
        int x = 1, y = 1;  // ❌ Error 2
        int n = arr.length;

        for (int i = 0; i <= n; i++) {  // ❌ Error 3
            Xor ^= arr[i];
        }

        int set_bit_no = Xor & (Xor - 1);  // ❌ Error 4

        for (int i = 0; i < n; i++) {
            if ((arr[i] & set_bit_no) != 0) {
                x ^= arr[i];
            } else {
                y ^= arr[i];
            }
        }

        List<Integer> res = Arrays.asList(x, y);
        Collections.sort(res);
        return res;
    }
```

``` js
function twoNonRepeatingNumbers(arr) {
    let Xor = 0;  // ❌ Error 1
    let x = 1, y = 1;  // ❌ Error 2
    const n = arr.length;

    for (let i = 0; i <= n; i++) {  // ❌ Error 3
        Xor ^= arr[i];
    }

    const set_bit_no = Xor & (Xor - 1);  // ❌ Error 4

    for (let i = 0; i < n; i++) {
        if (arr[i] & set_bit_no) {
            x ^= arr[i];
        } else {
            y ^= arr[i];
        }
    }

    return [x, y].sort((a, b) => a - b);
}
```

```python
def two_non_repeating_numbers(arr):
    Xor = 0  # ❌ Error 1
    x, y = 1, 1  # ❌ Error 2
    n = len(arr)

    for i in range(n + 1):  # ❌ Error 3
        Xor ^= arr[i]

    set_bit_no = Xor & (Xor - 1)  # ❌ Error 4

    for i in range(n):
        if arr[i] & set_bit_no:
            x ^= arr[i]
        else:
            y ^= arr[i]

    return sorted([x, y])
```
