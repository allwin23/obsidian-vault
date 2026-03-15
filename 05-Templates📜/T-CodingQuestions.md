---
tags:
  - coding-questions
  - dsa
status:
---
## 📋 Info

| Field               | Value                                                               |
| ------------------- | ------------------------------------------------------------------- |
| **Question Number** |                                                                     |
| **Platform**        | LeetCode / HackerRank / CodeForces / GFG/ Chat                      |
| **Difficulty**      | 🟢 Easy / 🟡 Medium / 🔴 Hard                                       |
| **Topic**           | [[Arrays]]                                                          |
| **Problem Link**    | [Link](https://claude.ai/chat/4e32e0a0-7c06-4e1b-b3ca-67a04d87afd9) |
| **Date Solved**     | {{date}}                                                            |
| Intuition Log       |                                                                     |


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
