---
layout: post
title: Kth Smallest Element in a BST
categories: [leetcode]
tags: [leetcode]
fullview: true
comments: true
---


문제 요약: bst구조에서 k번째 작은 원소를 찾아내는 문제이다.<br>

해결방법: bst조건에 맞추어 In order 조회하여 오름차순으로 배열에 저장한후 k번째 값을 반환하였다.<br>


<a class="btn btn-default" href="https://leetcode.com/problems/kth-smallest-element-in-a-bst/?envType=study-plan-v2&envId=top-interview-150"> 문제 링크

```java
    ArrayList<Integer> arr= new ArrayList<>();

    public int kthSmallest(TreeNode root, int k) {
        inOrder(root,k);

        return arr.get(k-1);
    }
    public void inOrder(TreeNode root, int k){
        TreeNode tmp;

        if (root.left != null) {
            tmp = root.left;
            inOrder(tmp, k);
        }
        arr.add(root.val);
        if (root.right != null) {
            tmp = root.right;
            inOrder(tmp, k);
        }
    }

```