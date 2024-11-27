
# Stack

## 정의
→ 스택은 데이터를 하나씩 쌓아올린 형태의 자료구조로 가장 마지막에 들어온 데이터가 가장 먼저 나가는 `후입선출(Last In First Out)` 구조이다.

## 특징
- **스택 오버플로우와 언더플로우**
    - 오버플로우 : 스택의 크기를 초과해 데이터를 삽입할때 발생한다.
    - 언더플로우 : 스택이 비어있는 상태에서 데이터를 제거하려 할때 발생한다.   
- **후입선출 구조 (LIFO)**
    - 나중에 삽입된 데이터가 가장 먼저 삭제된다.
    - 데이터 삽입과 삭제는 스택의 **탑(Top)**에서만 이루어진다.
- **한쪽 방향 접근**
    - 스택은 한쪽 끝(Top)에서만 데이터를 추가하거나 제거할 수 있다.
    - 중간데이터에 직접 접근이 불가능하고 반드시 순서대로 접근해야 한다.
- **순서 유지**
    - 삽입된 데이터의 순서를 유지하며, 순서대로 처리 가능하다.

## 연산
- `push(x)` : 스택에 데이터 x를 추가한다.
- `pop()` : 스택의 맨 위의 데이터를 제거하고 데이터를 반환한다.
- `peek()` : 스택의 맨 위 데이터를 조회한다.
- `size()` : 스택에 저장된 데이터 개수를 반환한다.
- `isEmpty()` : 현재 스택이 비어 있는지 확인한다. 
- `isFull()` : 스택이 가득 찼는지 확인한다.



## 구현
```java

import java.util.Stack;

public class StackExample {
    public static void main(String[] args) {
        // 스택 생성
        Stack<Integer> stack = new Stack<>();

        // push: 스택에 값 추가
        stack.push(10);
        stack.push(20);
        stack.push(30);
        System.out.println("스택: " + stack); 
        // [10, 20, 30]

        // pop: 스택의 맨 위 값 제거 및 반환
        int poppedValue = stack.pop();
        System.out.println("pop(): " + poppedValue); // 30
        System.out.println("스택: " + stack); // [10, 20]

        // peek: 맨 위 값 확인 (제거 X)
        int topValue = stack.peek();
        System.out.println("peek(): " + topValue); // 20

        // isEmpty: 스택이 비어있는지 확인
        boolean isEmpty = stack.isEmpty();
        System.out.println("isEmpty(): " + isEmpty); // false

        // size: 스택의 요소 개수 확인
        int size = stack.size();
        System.out.println("size(): " + size); // 2
    }
}
```

## 활용예시
- 괄호 유효성 검사 : 열고 닫는 괄호가 올바르게 배치 되었는지 확인한다.
- 중위 표현식을 후위 표현식으로 변환 : 연산자의 우선순위를 고려해 변환한다. 
- 후위 표현식 계산 : 후위 표기법으로 표현된 수식 평가이다.
- 최소값 스택 설계 : 현재 스택의 최소값을 `O(1)` 시간복잡도로 반환한다.
- 웹 브라우저 방문 기록 혹은 뒤로가기 기능하다.

## 시간복잡도
| 연산 | 시간 복잡도 | 설명 |
| --- | --- | --- |
| **삽입 (Push)** | O(1) | 데이터를 스택의 Top에 추가한다. Top 위치만 변경되므로 시간 복잡도는 O(1)이다. |
| **삭제 (Pop)** | O(1) | 스택의 Top에서 데이터를 제거한다. Top 위치만 이동하므로 시간 복잡도는 O(1)이다. |
| **탐색 (Search)** | O(n) | 스택 전체를 순차적으로 탐색해야 하므로 시간 복잡도는 O(n)이다. |
| **읽기 (Peek)** | O(1) | 스택의 Top에 있는 데이터를 읽는 연산으로, 데이터 이동 없이 Top을 참조만 하므로 O(1)이다. |

---

# Queue

## 정의
→ 큐는 먼저 들어온 데이터가 먼저 나가는 특성인 `선입선출(First In First Out)`의 특징을 가진 선형 자료구조이다.


## 특징 

- **오버플로우** : 크기가 제한된 경우 오버 플로우가 발생할 수 있다. 
- **단방향 접근 구조**
    - 삽입 : rear(뒤쪽)에서만 수행한다.
    - 제거 : front(앞쪽)에서만 수행한다.    
- **선입선출 구조 (FIFO)** : 먼저 삽입된 데이터가 가장 먼저 삭제된다.
- **순서 유지** : 삽입된 데이터의 순서를 유지하며 순서대로 처리가 가능하다. 


## 연산
- `enqueue()` - 큐에 끝(rear)에 항목을 추가한다.
- `dequeue()` - 큐에 맨 앞(front)에 항목을 제거한다.
- `peek()` - 큐에 맨 앞(front)에 있는 항목을 반환한다.
- `isfull()` - 큐가 가득 찼는지 확인한다.
- `isempty()` - 큐가 비어 있는지 확인한다. 


## 구현
```java

import java.util.LinkedList;
import java.util.Queue;

public class QueueExample {
    public static void main(String[] args) {
        // LinkedList를 Queue로 사용
        Queue<Integer> queue = new LinkedList<>();

        // Enqueue: 큐에 데이터 삽입
        queue.offer(10);
        queue.offer(20);
        queue.offer(30);

        System.out.println("큐: " + queue);

        // Dequeue: 큐에서 데이터 제거
        int dequeuedValue = queue.poll();
        System.out.println("poll(): " + dequeuedValue); // 10
        System.out.println("큐: " + queue);

        // Peek: 큐의 맨 앞 데이터 확인
        int frontValue = queue.peek();
        System.out.println("peek(): " + frontValue); // 20

        // 큐의 크기 확인
        System.out.println("큐의 크기: " + queue.size()); // 2
    }
}

```


## 활용예시
- BFS : 너비 우선 탐색에서 방문 노드를 순서대로 처리한다.
- 캐시 구현 : 최근 사용 데이터를 관리한다.
- 운영체제 프로세스 스케줄링 : 작업을 순서대로 처리한다.
- 데이터 흐름 관리 : 네트워크 트래픽을 처리한다.


## 시간복잡도 
| 연산 | 시간 복잡도 | 설명 |
| --- | --- | --- |
| **삽입 (Push)** | O(1) | 데이터를 스택의 Top에 추가한다. Top 위치만 변경되므로 시간 복잡도는 O(1)이다. |
| **삭제 (Pop)** | O(1) | 스택의 Top에서 데이터를 제거한다. Top 위치만 이동하므로 시간 복잡도는 O(1)이다. |
| **탐색 (Search)** | O(n) | 스택 전체를 순차적으로 탐색해야 하므로 시간 복잡도는 O(n)이다. |
| **읽기 (Peek)** | O(1) | 스택의 Top에 있는 데이터를 읽는 연산으로, 데이터 이동 없이 Top을 참조만 하므로 O(1)이다. |


## 종류 

### 원형 큐
→ 배열의 처음(Front)과 끝(Rear)이 연결된 형태의 큐이다. 

**특징**
- rear와 front가 순환 구조를 가지고 배열을 재사용 할 수 있어 메모리 효율성이 좋다. 
- FIFO(First In, First Out) 구조를 유지한다.
- 공간 낭비를 줄이고 배열 크기를 효율적으로 사용한다.

<br>

### 우선순위 큐
→ 큐에서 우선순위를 고려하여 데이터를 처리하는 자료구조이다. 

**특징**
- 높은 우선순위를 가진 데이터가 먼저 제거(Dequeue)된다.
- FIFO가 아닌 우선순위를 기준으로 처리한다.
- 힙(Heap) 자료구조를 기반으로 구현되는 경우가 많다.

<br>

### 양방향 큐 
→ 양쪽 모두 데이터의 삽입/삭제가 가능한 자료구조이다. 

**특징**
- ArrayDeque 클래스를 사용하여 구현이 가능하다.
- 양방향 큐의 대표적인 클래스로는 LinkedList클래스가 있다.
- 양쪽 끝에서 요소를 추가하거나 제거할 수 있으므로 유연성이 높다. 

