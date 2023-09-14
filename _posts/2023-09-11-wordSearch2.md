---
layout: post
title: WordSearch2
categories: [leetcode]
tags: [leetcode]
fullview: true
comments: true
---


문제 요약: 주어진 단어들중 m*n문자보드에 주어진 철자들의 인접조합(가로,세로)로 만들수있는 단어를 찾아내는 문제이다.<br>

해결방법: tire구조에 dfs로 탐색을 하여 철자들을 집어넣어두고 search하여 문제를 해결하였다.<br>

시간이 부족하여 예제를 통과하진 못하였다.<br>


<a class="btn btn-default" href="https://leetcode.com/problems/word-search-ii/?envType=study-plan-v2&envId=top-interview-150"> 문제 링크

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

    public class Trie{


        public Trie(){
            root=new Node();
        }

//        public void addWord(Character c){
//            Node current =this.root;
//
//            for(int i=0;i<word.length();i++){
//                if(i==word.length()-1){
//                    current.isEndOfWord=true;
//                }
//                if(!current.children.containsKey(word.charAt(i))){
//                    current.children.put(word.charAt(i),new Node());
//                }
//                current=current.children.get(word.charAt(i));
//            }
//        }

    }
    public boolean search(String word) {
        Node current=this.root;
        boolean ans=true;

        if (word.length() == 0) {
            return ans;
        }

        for(int i=0;i<word.length();i++){
            if(current.children.containsKey(word.charAt(i))){
                current=current.children.get(word.charAt(i));
            }
            else {
                return false;
            }
        }
        return ans;
    }


    public List<String> findWords(char[][] board, String[] words) {

        List<String> ans=new ArrayList<>();
        for(int i=0;i< board.length;i++){               //노드에 문자들 추가
            for(int j=0;j< board[board.length-1].length;j++){
                int [][] visited=new int[12][12];
                Node current =this.root;
                dfs(i,j,visited,board,current);
            }
        }
        //찾기
        for(int i=0;i<words.length;i++){
          boolean isTrue= search(words[i]);
          if(isTrue){
              ans.add(words[i]);
          }
        }

        return ans;

    }
    public void dfs(int x ,int y,int [][] visited,char[][] board,Node node){
        int[] xx={0,0,1,-1};
        int[] yy={1,-1,0,0};

        for(int i=0;i<4;i++){
            x+=xx[i];
            y+=yy[i];

            if(0<=x &&x<board.length && 0<=y &&y<board[board.length-1].length&&visited[x][y]==0){
                visited[x][y]=1;
                node.children.put(board[x][y],new Node());
            }
            else {return;}
            dfs(x,y,visited,board,node.children.get(board[x][y]));
        }
    }

```