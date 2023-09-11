---
layout: post
title:  Design Add and Search Words Data Structure
categories: [leetcode]
tags: [leetcode]
fullview: true
comments: true
---


문제 요약: 단어장 저장 클래스를 만드는 문제이다. 저장, 검색 기능이 있는데, 이때 '.'은 아무 문자와도 매칭되도록한다.<br>

해결방법: '.'예외처리에 주의하며 따로 함수를 만들어 처리하였으며 나머지는 기본적인 trie구조와 유사하게 구현하였다.<br>

채점 통과를 못하였는데 input이 너무 길어서 틀린곳을 못찾아서 고치지 못했다.<br>


<a class="btn btn-default" href="https://leetcode.com/problems/design-add-and-search-words-data-structure/?envType=study-plan-v2&envId=top-interview-150"> 문제 링크

```java
   public class Node {
        public Map<Character,Node> children;
        public boolean isEndOfWord;

        public Node() {
            this.children = new HashMap<>();
            this.isEndOfWord = false;
        }
    }
    Node root;
    public WordDictionary() {
        root=new Node();

    }

    public void addWord(String word) {
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
            System.out.println(word.charAt(i));
            System.out.println(current.isEndOfWord);
            if(i==word.length()-1&&word.charAt(i)!='.'){
                if(!current.isEndOfWord){
                    return false;
                }
            }
            if(word.charAt((i))=='.'){          //'.'일 경우 처리 함수로 이동
                boolean dotCheck=true;
                if(current.children.isEmpty()){
                    return false;               //'.'인데 root의 자식이 없을경우 false;
                }
                for(Node childNodes:current.children.values()){
                    dotCheck=dotSearch(childNodes,word,i);
                }
                if(dotCheck){
                    return true;
                }
                else return false;
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

    public boolean dotSearch(Node node,String word,int index){
        index++;
        boolean ans=true;
        if(index==word.length()){
            if (node.isEndOfWord){
                return true;
            }
            else if(node.children.isEmpty()){
                return false;
            }
        }

        for(int i=index;i<word.length();i++){
            if(i==word.length()-1&&word.charAt(i)!='.'){
                if(!node.isEndOfWord){
                    return false;
                }
            }
            if(word.charAt(i)=='.'){
                for (Node childNodes:node.children.values()){
                    ans=dotSearch(childNodes,word,i);           //'.'일경우 재귀
                }
                return ans;
            }
            if(node.children.containsKey(word.charAt(i))){
                node=node.children.get(word.charAt(i));
            }
            else{
                return false;
            }
        }
        return ans;
    }
```