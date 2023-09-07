---
layout: post
title: Minimum Absolute Difference in BST
categories: [leetcode]
tags: [leetcode]
fullview: true
comments: true
---


문제 요약: 주어진 bst에서 어느 노드든 최소의 절대값 차이를 구하는 문제이다.<br>

해결방법: 순회를하며 각 노드값을 배열에 담아준후 배열을 정렬하고 배열을 돌며 최소값을 찾았다.<br>


<a class="btn btn-default" href="https://leetcode.com/problems/minimum-absolute-difference-in-bst/description/?envType=study-plan-v2&envId=top-interview-150"> 문제 링크

```java
 int ans=100000;
    ArrayList<Integer> arr=new ArrayList<>();
    public int getMinimumDifference(TreeNode root) {
        search(root);
        Collections.sort(arr);

        for(int i=0;i<arr.size()-1;i++){
            ans=Math.min(ans,Math.abs(arr.get(i)-arr.get(i+1)));
        }
        return ans;
    }

    public void search(TreeNode root){
        TreeNode tmp;
        arr.add(root.val);
        if(root.left!=null){
            tmp=root.left;
            search(tmp);
        }
        if(root.right!=null){
            tmp=root.right;
            search(tmp);
        }
    }

```