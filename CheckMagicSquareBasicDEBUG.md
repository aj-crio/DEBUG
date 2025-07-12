
```cpp
#include <bits/stdc++.h>
using namespace std;

bool checkMagicSquare(vector<vector<int>> mat, int n) {
    int sumReq = n * (n * n + 1) / 2;
    int diagOne = 0, diagTwo = 0;
    for (int i = 0; i <= n; i++) {  // ❌ Error 1: should be i < n
        int sum = 0;
        for (int j = 0; j < n; j++) {
            if (i == j) {
                diagOne += mat[i][j];
            }
            if (i + j == n - 1) {
                diagTwo += mat[i][j];
            }
            sum += mat[i][j];
        }
        if (sum == sumReq) {  // ❌ Error 2: should be != for failure
            return false;
        }
        sum = 0;
        for (int j = 0; j < n; j++) {
            sum += mat[j][i];
        }
        if (sum == sumReq) {  // ❌ Error 3: should be !=
            return false;
        }
    }
    if (diagOne != sumReq || diagTwo != sumReq) {
        return false;
    }
    return true;
}

int main() {
    int n;
    cin >> n;
    vector<vector<int>> mat(n, vector<int>(n));
    for (int i = 0; i < n; i++) {
        for (int j = 0; j < n; j++) {
            cin >> mat[i][j];
        }
    }
    bool result = checkMagicSquare(mat, n);
    if (result) {
        cout << "Yes";
    } else {
        cout << "No";
    }
}

```

```java
import java.util.*;

public class Main {
    public static boolean checkMagicSquare(int[][] mat, int n) {
        int sumReq = n * (n * n + 1) / 2;
        int diagOne = 0, diagTwo = 0;
        for (int i = 0; i <= n; i++) {  // ❌ Error 1: should be <
            int rowSum = 0;
            for (int j = 0; j < n; j++) {
                if (i == j) diagOne += mat[i][j];
                if (i + j == n - 1) diagTwo += mat[i][j];
                rowSum += mat[i][j];
            }
            if (rowSum == sumReq) {  // ❌ Error 2
                return false;
            }
            int colSum = 0;
            for (int j = 0; j < n; j++) {
                colSum += mat[j][i];
            }
            if (colSum == sumReq) {  // ❌ Error 3
                return false;
            }
        }
        if (diagOne != sumReq || diagTwo != sumReq) return false;
        return true;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int[][] mat = new int[n][n];
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                mat[i][j] = sc.nextInt();
            }
        }
        System.out.println(checkMagicSquare(mat, n) ? "Yes" : "No");
    }
}

```

``` js
function checkMagicSquare(mat, n) {
    const sumReq = (n * (n * n + 1)) / 2;
    let diagOne = 0, diagTwo = 0;
    for (let i = 0; i <= n; i++) {  // ❌ Error 1: should be <
        let rowSum = 0;
        for (let j = 0; j < n; j++) {
            if (i === j) diagOne += mat[i][j];
            if (i + j === n - 1) diagTwo += mat[i][j];
            rowSum += mat[i][j];
        }
        if (rowSum === sumReq) {  // ❌ Error 2
            return false;
        }
        let colSum = 0;
        for (let j = 0; j < n; j++) {
            colSum += mat[j][i];
        }
        if (colSum === sumReq) {  // ❌ Error 3
            return false;
        }
    }
    if (diagOne !== sumReq || diagTwo !== sumReq) return false;
    return true;
}

const n = parseInt(prompt());
const mat = [];
for (let i = 0; i < n; i++) {
    mat.push(prompt().split(' ').map(Number));
}
console.log(checkMagicSquare(mat, n) ? "Yes" : "No");

```

```python
def check_magic_square(mat, n):
    sum_req = n * (n * n + 1) // 2
    diag_one = diag_two = 0
    for i in range(0, n + 1):  # ❌ Error 1: should stop at n
        row_sum = 0
        for j in range(n):
            if i == j:
                diag_one += mat[i][j]
            if i + j == n - 1:
                diag_two += mat[i][j]
            row_sum += mat[i][j]
        if row_sum == sum_req:  # ❌ Error 2
            return False
        col_sum = sum(mat[j][i] for j in range(n))
        if col_sum == sum_req:  # ❌ Error 3
            return False
    if diag_one != sum_req or diag_two != sum_req:
        return False
    return True


n = int(input())
mat = [list(map(int, input().split())) for _ in range(n)]
print("Yes" if check_magic_square(mat, n) else "No")

```
