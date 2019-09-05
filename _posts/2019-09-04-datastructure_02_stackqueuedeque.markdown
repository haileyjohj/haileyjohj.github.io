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
  
  
![스택/큐/데크 비교](https://nakjunizm.github.io/2017/02/24/Queue_And_Deque/queue1.png)  
출처 : https://nakjunizm.github.io
  
  
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
  
| 메소드               	| 설명                                                                                                                                                 	|
|----------------------	|------------------------------------------------------------------------------------------------------------------------------------------------------	|
| boolean empty()      	| 해당 스택이 비어 있으면 true를, 비어 있지 않으면 false를 반환                                                                                        	|
| E peek()             	| 해당 스택의 제일 상단에 있는(제일 마지막으로 저장된) 요소를 반환                                                                                     	|
| E pop()              	| 해당 스택의 제일 상단에 있는(제일 마지막으로 저장된) 요소를 반환하고,  <br> 해당 요소를 스택에서 제거                                                      	|
| E push(E item)       	| 해당 스택의 제일 상단에 전달된 요소를 삽입                                                                                                           	|
| int search(Object o) 	| 해당 스택에서 전달된 객체가 존재하는 위치의 인덱스를 반환 <br> 이때 인덱스는 제일 상단에 있는(제일 마지막으로 저장된) 요소의 위치부터 0이 아닌 1부터 시작 	|
  
  
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
  
| 메소드             	| 설명                                                                                                                                           	|
|--------------------	|------------------------------------------------------------------------------------------------------------------------------------------------	|
| boolean add(E e)   	| 해당 큐의 맨 뒤에 전달된 요소를 삽입 만약 삽입에 성공하면 true를 반환하고,<br>  큐에 여유 공간이 없어 삽입에 실패하면 IllegalStateException을 발생 	|
| E element()        	| 해당 큐의 맨 앞에 있는(제일 먼저 저장된) 요소를 반환                                                                                           	|
| boolean offer(E e) 	| 해당 큐의 맨 뒤에 전달된 요소를 삽입                                                                                                           	|
| E peek()           	| 해당 큐의 맨 앞에 있는(제일 먼저 저장된) 요소를 반환<br>  만약 큐가 비어있으면 null을 반환                                                          	|
| E poll()           	| 해당 큐의 맨 앞에 있는(제일 먼저 저장된) 요소를 반환하고 해당 요소를 큐에서 제거  <br>  만약 큐가 비어있으면 null을 반환                            	|
| E remove()         	| 해당 큐의 맨 앞에 있는(제일 먼저 저장된) 요소를 제거                                                                                           	|
  
    
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
  
  
| Queue Method 	| Equivalent Deque Method 	| 설명                                                                                                                                                                                                                  	|
|--------------	|-------------------------	|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------	|
| add(e)       	| addLast(e)              	| 용량 제한을 위반하지 않고 즉시 수행 할 수있는 경우이 deque 끝에 지정된 요소를 삽입.<br> 용량 제한 deque를 사용할 때는 offerLast (E) 메소드를 사용하는 것이 일반적으로 바람직.<br> 이 메소드는 add (E)와 같습니다.<br> 	|
| offer(e)     	| offerLast(e)            	| 용량 제한을 위반하지 않는 한 지정된 요소를이 deque 앞에 삽입. <br> 용량 제한 deque를 사용하는 경우, 일반적으로 addFirst (E) 메소드보다 선호.                                                                          	|
| remove()     	| removeFirst()           	| 첫 번째 요소를 검색하고 제거. <br> deque가 비어있는 경우 예외를 발생 시킨다는 점에서만 pollFirst와 다름.                                                                                                              	|
| poll()       	| pollFirst()             	| 첫 번째 요소를 검색하여 제거하거나, <br> deque가 비어 있으면 null을 반환.                                                                                                                                             	|
| element()    	| getFirst()              	| 첫 번째 요소를 검색하지만 제거하지는 않음.<br> deque가 비어있는 경우 예외를 발생 시킨다는 점에서만 peekFirst와 다름.                                                                                                  	|
| peek()       	| peekFirst()             	| 첫 번째 요소를 검색하지만 제거하지는 않음.<br> deque가 비어 있으면 null을 반환.                                                                                                                                       	|
  
  
| Stack Method 	| Equivalent Deque Method 	| 설명                                                                                                                                                                       	|
|--------------	|-------------------------	|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------	|
| push(e)      	| addFirst(e)             	| 용량 제한을 위반하지 않고 즉시 수행 할 수있는 경우 지정된 요소를 deque 앞에 삽입.<br> 용량 제한 deque를 사용할 때는 offerFirst (E) 방법을 사용하는 것이 일반적으로 바람직. 	|
| pop()        	| removeFirst()           	| deque의 첫 번째 요소를 검색하고 제거. <br> 비어있는 경우 예외를 발생 시킨다는 점에서만 pollFirst와 다름.                                                                   	|
| peek()       	| peekFirst()             	| deque의 첫 번째 요소를 검색하지만 제거하지는 않음.<br> deque가 비어 있으면 null을 반환.                                                                                    	|
