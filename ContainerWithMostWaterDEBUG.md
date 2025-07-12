
```cpp
int maxArea(vector<int>& height) {
    int answer = INT_MAX;  // ❌ Error 1: should start with 0
    int n = height.size();
    int front = 0, back = n - 1;

    while (front <= back) {  // ❌ Error 2: should be front < back
        int minHeight = max(height[front], height[back]);  // ❌ Error 3: should be min()
        int width = back - front;
        answer = max(answer, minHeight * width);

        if (height[front] <= height[back])
            front++;
        else
            back--;
    }

    return answer;
}
```

```java
 public static int maxArea(List<Integer> height) {
        int answer = Integer.MAX_VALUE;  // ❌ Error 1
        int front = 0, back = height.size() - 1;

        while (front <= back) {  // ❌ Error 2
            int minHeight = Math.max(height.get(front), height.get(back));  // ❌ Error 3
            int width = back - front;
            answer = Math.max(answer, minHeight * width);

            if (height.get(front) <= height.get(back))
                front++;
            else
                back--;
        }

        return answer;
    }
```

``` js
function maxArea(height) {
    let answer = Number.MAX_SAFE_INTEGER;  // ❌ Error 1
    let front = 0, back = height.length - 1;

    while (front <= back) {  // ❌ Error 2
        let minHeight = Math.max(height[front], height[back]);  // ❌ Error 3
        let width = back - front;
        answer = Math.max(answer, minHeight * width);

        if (height[front] <= height[back]) {
            front++;
        } else {
            back--;
        }
    }

    return answer;
}
```

```python
def max_area(height):
    answer = float('inf')  # ❌ Error 1
    front, back = 0, len(height) - 1

    while front <= back:  # ❌ Error 2
        min_height = max(height[front], height[back])  # ❌ Error 3
        width = back - front
        answer = max(answer, min_height * width)

        if height[front] <= height[back]:
            front += 1
        else:
            back -= 1

    return answer
```
