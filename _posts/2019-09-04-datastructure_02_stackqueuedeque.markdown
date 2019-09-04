---
title:  "[자료구조] 스택(Stack) / 큐(Queue) / 데크(Deque)"
excerpt: "선형 자료구조"
last_modified_at:   2019-09-04 15:18:24 +0900
categories: DataStructure
tags:
- 자료구조
- 스택
- 큐
- 데크
---

>## 스택(Stack)  
  
후입선출 (LIFO, Last In First Out)  
리스트 내 데이터 삽입, 삭제가 한쪽 끝에서 이루어지는 데이터구조  
  
```java 
import java.util.*;
public class StackTest {
    public static void main(String[] args) {
        Stack stk = new Stack();
        
        stk.push("A");
        stk.push("B");
        stk.push("C");
                
        while(!stk.empty()) {
            System.out.println(stk.pop());
        }
    }
}

```
  
>## 큐(Queue)  
  
선입 선출 (FIFO, First In First Out)  
추상적 자료형, 시작과 끝에 두개의 포인터를 갖는 자료구조   
   
```java  
import java.util.*;
public class QueueTest {
    public static void main(String[] args) {
        Queue que = new LinkedList();
        
        que.add("A");
        que.add("B");
        que.add("C");
        
        while(!que.isEmpty()) {
            System.out.println(que.poll());
        }
    }
}
```
    
>## 데크(Deque)  
  
스택과 큐과 결합한 자료구조  
양쪽 끝에서 삽입, 삭제 가능  
- 입력제한데크(Scroll) : 한쪽의 입력을 제한  
- 출력제한데크(Shelf) : 한쪽의 출력을 제한  
  
  
```java 
import java.util.*;
class DequeTest {
    public static void main(String[] args) {
      Deque<Integer> deque = new ArrayDeque<>(8);
      deque.push(5); // [5] 
      deque.push(4); // [5,4] 
      System.out.println(deque.pop()); // 4 출력 
      System.out.println(deque); // [5] => Stack(LIFO)
      
      deque.offerFirst(3); // [3,5] => Deque
      deque.offerLast(6); // [3,5,6] => Queue
      System.out.println(deque.pollFirst()); // 3 출력
      System.out.println(deque); // [5,6] => Queue(FIFO)
      }
   }
```
