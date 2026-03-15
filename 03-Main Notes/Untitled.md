---
tags:
  - coding-questions
  - dsa
status:
---
## 📋 Info

| Field               | Value                                                     |
| ------------------- | --------------------------------------------------------- |
| **Question Number** |                                                           |
| **Platform**        | LeetCode                                                  |
| **Difficulty**      | 🟢 Easy                                                   |
| **Topic**           | [[Arrays]] [[DSA]]                                        |
| **Problem Link**    | [Link](https://leetcode.com/problems/powx-n/description/) |
| **Date Solved**     | {{date}}                                                  |
| Intuition Log       |                                                           |


---

## ❓ Question:

> Paste the problem statement here



## **Constraints:**

---

## 💻 Solution :


```cpp
class Solution {
public:
    vector<vector<int>> generate(int n) {
        vector<vector<int>> result;
        result.push_back({1});
        
        if(n == 1) return result;
        
        for(int i = 0; i < n - 1; i++) {
            vector<int> buff;
            buff.push_back(1);
            
            for(int j = 1; j < result[i].size(); j++) {
                buff.push_back(result[i][j] + result[i][j-1]);
            }
            
            buff.push_back(1);
            result.push_back(buff);
        }
        
        return result;
    }
};
```



---


## ⏱️ Complexity :

|Type|Complexity|
|---|---|
|**Time**|O()|
|**Space**|O()|

---

## 💡 Key Insight :

---

## 🔗 Related Questions

|Question|Topic|Difficulty|
|---|---|---|
|[[]]|||
|[[]]|||
