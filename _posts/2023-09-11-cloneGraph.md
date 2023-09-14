---
layout: post
title: WordSearch2
categories: [leetcode]
tags: [leetcode]
fullview: true
comments: true
---


문제 요약: 주어진 노드의 구조를 탐색하여 그 클론 리스트노드를 반환하는 문제이다.<br>

해결방법:입력받은 노드를 dfs 탐색하여 그값들을 저장하여 노드를 반환하였다.<br>


<a class="btn btn-default" href="https://leetcode.com/problems/clone-graph/?envType=study-plan-v2&envId=top-interview-150"> 문제 링크

```java
    class Solution {
        Node visited[] = new Node[101];

        public Node cloneGraph(Node node) {

            if (node == null) {
                return null;
            } else {
                Node newNode = new Node(node.val);

                dfs(node, newNode, visited);

                return newNode;
            }
        }

        public void dfs(Node node, Node newNode, Node visited[]) {
            visited[newNode.val] = newNode;
            for (Node n : node.neighbors) {
                if (visited[n.val] != null) {
                    newNode.neighbors.add(visited[n.val]);   //이미 방문한 곳이면 이웃에만 추가

                } else {//방문 안했으면 재귀
                    Node tmpNode = new Node(n.val);
                    newNode.neighbors.add(tmpNode);
                    dfs(n, tmpNode, visited);
                }
            }
        }
    }
```