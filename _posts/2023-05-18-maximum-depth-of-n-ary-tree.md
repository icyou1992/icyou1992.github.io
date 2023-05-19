---
title: Maximum Depth of N-ary Tree

author: icyou
date: 2023-05-18 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Maximum Depth of N-ary Tree
N-ary Tree의 최대 깊이를 구하는 문제입니다.  

```
class Solution:
    def maxDepth(self, root: 'Node') -> int:
        return 0 if not root else 1 if not root.children else 1 + max([self.maxDepth(x) for x in root.children])

```  
tree에서 node가 없을 경우 0, node의 children이 없을 경우 1,  
아닌 경우 재귀를 호출하면서 1을 더해갈 경우 최대 깊이를 구할 수 있습니다.  
좀 더 풀어 쓰면 아래와 같습니다.  

```
class Solution:
    def maxDepth(self, root: 'Node') -> int:
        if not root:
            return 0
        elif not root.children:
            return 1
        return 1 + max([self.maxDepth(x) for x in root.children])
```

<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/maximum-depth-of-n-ary-tree/submissions/952481739/](https://leetcode.com/problems/maximum-depth-of-n-ary-tree/submissions/952481739/)