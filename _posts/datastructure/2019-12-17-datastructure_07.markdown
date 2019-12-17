---
title:  "[자료구조] 그래프"
excerpt: 그래프, 그래프 탐색 등 간략정리
date: 2019-12-17 16:07:24 +0900
categories: DataStructure
tags: 자료구조 그래프
last_modified_at: 2019-12-17 16:07:24 +0900
---

>## 그래프  

- 그래프는 단순히 노드와 그 노드를 연결하는 간선(edge)을 하나로 모아 놓은 것.  
- 트리는 그래프의 한 종류.
- 방향성이 있을 수도 없을 수도 있다.
- 사이클이 존재할 수도 존재하지 않을 수도 있다.  

>## 그래프 탐색  

>### 깊이 우선 탐색 (DFS, depth-first search)  

그래프에서 모든 노드를 방문하고자 할 때 더 선호되는 편이다. 둘 중 아무거나 사용해도 상관없지만, 깊이 우선 탐색이 좀 더 간단하긴 하다.  
전위 순회를 포함한 다른 형태의 트리 순회는 모두 DFS의 한 종류이다.  
그래프 탐색의 경우 어떤 노드를 방문했었는지 여부를 반드시 검사해야 한다는 것이 큰 차이점이다. 검사하지 않을 경우 무한 루프에 빠질 위험이 있다.

```java
//DFS 의사코드

void searchDFS(Node root){
  if(root == null) return;
  visit(root);
  root.visited = true;
  for each(Node n in root.adjacent){
    if(n.visited == false){
      searchDFS(n);
    }
  }
}

```


>### 너비 우선 탐색 (BFS, breadth-first search)  

두 노드 사이의 최단 경로 혹은 임의의 경로를 찾고 싶을 때는 너비 우선 탐색이 더 낫다.  
BFS는 직관적이지 않은 면이 있다.   
실패하는 가장 흔한 이유는 BFS가 재귀적으로 동작할 거라고 잘못 가정하는 것이다.  
BFS는 `큐(Queue)`를 이용해서 반복적 형태로 구현하는 것이 가장 잘 동작한다.

```java
//BFS 의사코드

void searchBFS(Node root){
  Queue queue = new Queue();
  root.marked = true;
  queue.enqueue(root);

  while(!queue.isEmpty()){
    Node r = queue.dequeue();
    visit(r);
    for each (Node n in r.adjacent){
      if(n.marked == false){
        n.marked = true;
        queue.enqueue(n);
      }
    }
  }
}

```

>### 양방향 탐색  

양방향 탐색은 출발지와 도착지 사이에 최단 경로를 찾을 때 사용되곤 한다. 기본적으로 출발지와 도착지 두 노드에서 동시에 너비 우선 탐색을 수행한 뒤, 두 탐색 지점이 충돌하는 경우에 경로를 찾는 방식이다.  
