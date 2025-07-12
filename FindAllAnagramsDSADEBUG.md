```cpp
#include <bits/stdc++.h>
using namespace std;

vector<string> findAllAnagrams(string& str, vector<string>& arr) {
    vector<string> anagrams;
    unordered_set<char> charSet(str.begin(), str.end());

    for (string& s : arr) {
        bool is_anagram = true;
        for (char ch : s) {
            if (charSet.find(ch) == charSet.end()) {
                is_anagram = false;
                break;  // ❌ Error 1: missing break on mismatch
            }
        }
        if (is_anagram && s.length() != str.length()) {  // ❌ Error 2: added wrong length check
            anagrams.push_back(s);
        }
    }

    // ❌ Error 3: sorting skipped
    return anagrams;
}

int main() {
    string str;
    cin >> str;
    int n; cin >> n;
    vector<string> arr;
    for (int i = 0; i < n; i++) {
        string s; cin >> s;
        arr.push_back(s);
    }

    vector<string> result = findAllAnagrams(str, arr);

    for (string& s : result) {
        cout << s << "\n";
    }
}

```

```java
import java.util.*;

public class Main {
    public static List<String> findAllAnagrams(String str, List<String> arr) {
        List<String> anagrams = new ArrayList<>();
        Set<Character> charSet = new HashSet<>();
        for (char c : str.toCharArray()) charSet.add(c);

        for (String s : arr) {
            boolean isAnagram = true;
            for (char c : s.toCharArray()) {
                if (!charSet.contains(c)) {
                    isAnagram = false;
                    // ❌ Error 1: missing break
                }
            }
            if (isAnagram && s.length() != str.length()) {  // ❌ Error 2: wrong length check
                anagrams.add(s);
            }
        }

        return anagrams;  // ❌ Error 3: unsorted
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String str = sc.next();
        int n = sc.nextInt();
        List<String> arr = new ArrayList<>();
        for (int i = 0; i < n; i++) arr.add(sc.next());

        List<String> result = findAllAnagrams(str, arr);
        for (String s : result) System.out.println(s);
    }
}

```

``` js
function findAllAnagrams(str, arr) {
    const anagrams = [];
    const charSet = new Set(str);

    for (const word of arr) {
        let isAnagram = true;
        for (const ch of word) {
            if (!charSet.has(ch)) {
                isAnagram = false;
                // ❌ Error 1: missing break
            }
        }
        if (isAnagram && word.length !== str.length) {  // ❌ Error 2: wrong length check
            anagrams.push(word);
        }
    }

    return anagrams;  // ❌ Error 3: unsorted
}

const str = prompt();
const n = parseInt(prompt());
const arr = [];
for (let i = 0; i < n; i++) arr.push(prompt());

const result = findAllAnagrams(str, arr);
for (const s of result) console.log(s);

```

```python
def find_all_anagrams(str_word, arr):
    anagrams = []
    char_set = set(str_word)

    for word in arr:
        is_anagram = True
        for ch in word:
            if ch not in char_set:
                is_anagram = False
                # ❌ Error 1: missing break
        if is_anagram and len(word) != len(str_word):  # ❌ Error 2: wrong length check
            anagrams.append(word)

    return anagrams  # ❌ Error 3: unsorted


str_word = input()
n = int(input())
arr = [input() for _ in range(n)]

result = find_all_anagrams(str_word, arr)
for word in result:
    print(word)

```
