---
layout: post
title: Implement Trie (Prefix Tree)
categories: [leetcode]
tags: [leetcode]
fullview: true
comments: true
---


문제 요약: trie 구조를 직접 구현해보는 문제이다.<br>

해결방법: trie 설명을 보면서 구현해보았다.<br>


<a class="btn btn-default" href="https://leetcode.com/problems/implement-trie-prefix-tree/?envType=study-plan-v2&envId=top-interview-150"> 문제 링크

```java
  public class Node {
        public Map<Character, Node> children;
        public boolean isEndOfWord;

        public Node() {
            this.children = new HashMap<>();
            this.isEndOfWord = false;
        }
    }
    Node root;
    public Trie() {
        root=new Node();
    }

    public void insert(String word) {
        Node current =this.root;

        for(int i=0;i<word.length();i++){
            if(i==word.length()-1){
                current.isEndOfWord=true;
            }
            if(!current.children.containsKey(word.charAt(i))){
                current.children.put(word.charAt(i),new Node());
            }
            current=current.children.get(word.charAt(i));
        }
    }

    public boolean search(String word) {

        Node current=this.root;
        boolean ans=true;

        if (word.length() == 0) {
            return ans;
        }

        for(int i=0;i<word.length();i++){
            System.out.println(current.isEndOfWord);
            if(i==word.length()-1){
                if(!current.isEndOfWord){
                    return false;
                }
            }

            if(current.children.containsKey(word.charAt(i))){
                current=current.children.get(word.charAt(i));
            }
            else {
                return false;
            }
        }
        return ans;
    }

    public boolean startsWith(String prefix) {
        Node current =this.root;
        boolean ans=true;

        for(char c:prefix.toCharArray()){
           if(current.children.containsKey(c)){
               current=current.children.get(c);
           }
           else return false;
        }

        return ans;
    }

```