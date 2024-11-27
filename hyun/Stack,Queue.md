# Stack, Queue

# 스택 (Stack)

## 정의

→ 스택은 데이터를 하나씩 쌓아올린 형태의 자료구조로 가장 마지막에 들어온 데이터가 가장 먼저 나가는 `후입선출(Last In First Out)` 구조이다.

## 주요 연산

- `push(x)` : 스택에 데이터 x를 추가
- `pop()` : 스택의 맨 위의 데이터를 제거하고 데이터를 반환
- `peek()` : 스택의 맨 위 데이터를 조회
- `size()` : 스택에 저장된 데이터 개수를 반환
- `isEmpty()` : 현재 스택이 비어 있는지 확인

## 시간 복잡도

- **삽입(Push)** : O(1)
- **삭제(Pop)** : O(1)
- **탐색(Search)** : O(n)

## 특징

- 단방향 접근 구조
    - 삽입과 삭제 연산이 항상 끝쪽에서만 수행 된다.
    - 중간데이터에 직접 접근이 불가능하고 반드시 순서대로 접근해야한다.
- 스택 오버플로우와 언더플로우
    - 오버플로우 : 스택의 크기를 초과해 데이터를 삽입할때 발생한다.
    - 언더플로우 : 스택이 비어있는 상태에서 데이터를 제거하려 할때 발생한다.

## 활용 예시

- 함수의 콜 스택, 웹 브라우저 뒤로가기, 실행 취소

## 자바에서 스택

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
        System.out.println("스택: " + stack); // [10, 20, 30]

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

# 큐(Queue)

## 정의

→ 큐는 먼저 들어온 데이터가 먼저 나가는 특성인 `선입선출(First In First Out)`의 특징을 가진 선형 자료구조이다.

## 주요 연산

- `enqueue(x)` : 큐의 뒤쪽에 데이터 x를 추가
- `dequeue()`  : 큐의 앞쪽에 데이터를 제거 후 반환
- `peek()` : 큐의 앞쪽 데이터를 제거하지않고 확인
- `isEmpty()` : 큐가 비어있는지 확인
- `size()` : 큐의 데이터 개수를 반환

## 시간 복잡도

- **삽입(Enqueue)** : O(1)
- **제거(Dequeue)** : O(1)
- **탐색(Search)** : O(n)

## 특징

- 단방향 접근 구조
    - 삽입 : 뒤쪽에서만 수행
    - 제거 : 앞쪽에서만 수행
- 구현 방식
    - 배열 기반 큐
        - 데이터를 연속된 메모리에 저장하고 큐가 가득차면 스택 오버플로우 발생한다.
    - 원형 큐
        - 배열 기반의 큐의 비효율성을 개선한 방식으로 빈 공간 재사용 가능하다.
    - 연결리스트 기반 큐
        - 동적으로 크기 조절이 가능하다.

## 활용 예시

- 대기열 관리, 프로세스 관리, BFS알고리즘

## 자바에서 큐

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

## 선형 큐(Linear Queue)

→ 가장 기본적인 큐의 형태로 큐의 앞에서 데이터를 제거하고 뒤에서 데이터를 삽입하는 방식이다. 일반적으로 배열을 사용하여 구현한다.

큐의 크기가 고정되어 있으므로 큐가 가득차면 더이상 데이터를 삽입할수 없다.

```java
// 선형 큐 구현 (배열 사용)
int[] queue = new int[5]; // 크기 5인 큐
int front = -1, rear = -1;

// Enqueue: 데이터 삽입
rear++;
queue[rear] = 10;  // 10 삽입

// Dequeue: 데이터 삭제
front++;
int removedValue = queue[front];  // 큐에서 앞의 데이터 제거
```

## 단점

- 큐에서 데이터를 삭제해도 배열의 앞부분에 빈공간이 남기때문에 메모리 낭비가 발생한다.

## 원형 큐(Circular Queue)

→ 원형 큐는 선형 큐에서 발생하는 메모리 낭비 문제를 해결하기 위해 배열의 끝과 처음이 연결된 형태의 큐이다. 배열이 원형이되며 앞과 뒤가 연결되어있다.

## 특징

- 배열이 원형으로 연결되어있기 때문에 빈 공간을 재사용 할수 있어 메모리 낭비를 최소화한다.
- 큐의 크기가 고정되어있지만 배열의 앞부분도 재사용 할 수 있다.

```java
// 원형 큐 구현 (배열 사용)
int[] queue = new int[5]; // 크기 5인 큐
int front = -1, rear = -1;

// Enqueue: 데이터 삽입
rear = (rear + 1) % 5;
queue[rear] = 10;  // 10 삽입

// Dequeue: 데이터 삭제
front = (front + 1) % 5;
int removedValue = queue[front];  // 큐에서 앞의 데이터 제거
```

### 단점

- 큐의 크기가 고정되어 있어 크기를 넘어서는 데이터 삽입이 불가능하다.
- 배열 크기를 미리 결정해야 하므로 크기가 정해지지 않은 상황에서는 유연성이 부족할 수 있다.

## 우선순위 큐(Priority Queue)

→ 큐에서 우선순위를 고려하여 데이터를 처리하는 자료구조이다. 각 데이터에는 우선순위가 설정되고 데이터를 제거할때 우선순위가 가장 높은 요소부터 처리된다.

```java
import java.util.PriorityQueue;
import java.util.Collections;

public class PriorityQueueExample {
    public static void main(String[] args) {
        // 내림차순 우선순위 큐
        PriorityQueue<Integer> pq = new PriorityQueue<>(Collections.reverseOrder());

        pq.offer(10);
        pq.offer(30);
        pq.offer(20);

        // Dequeue: 우선순위가 높은 요소부터 제거
        System.out.println(pq.poll());  // 30
        System.out.println(pq.poll());  // 20
        System.out.println(pq.poll());  // 10
    }
}
```

### 장점

- 우선순위에 따라 데이터 처리가 가능하여 다양한 알고리즘과 스케줄링 문제에 유용하게 사용된다.
- 우선순위 큐는 힙(Heap) 자료구조를 사용하므로 삽입과 삭제가 O(log N)의 시간 복잡도를 가진다.

### 단점

- 우선순위를 설정할 수 있는 데이터가 필요한 문제에만 적합하다. 우선순위가 중요한 데이터가 아니라면 과도하게 복잡할 수 있다.
- 힙(Heap) 자료구조를 사용하므로 배열이나 링크드 리스트에 비해 메모리 사용이 비효율적일 수 있다.
