## 스택 (Stack)
> 스택이란 나중에 들어온 데이터가 먼저 나가는 LIFO 자료구조

<br>

### 스택의 특징 
- 삽입, 삭제 연산이 Top에서만 이뤄짐
- 스택의 크기를 초과해서 데이터를 추가할 경우 스택 오버플로우 발생 

<br>

### 스택 연산 
- push() : 데이터를 스택에 추가
- pop() : 스택에서 데이터를 제거 및 반환 
- peek() : 스택의 가장 마지막에 들어온 Top 반환 
- isEmpty() : 스택이 비어있는지 확인
- isFull() : 스택이 가득 찼는지 확인 

```java

class Stack {
    private int[] stack;
    private int top;
    private int capacity;

    public Stack(int size) {
        stack = new int[size];
        capacity = size;
        top = -1;
    }

    public void push(int x) {
        if (isFull()) {
            System.out.println("Stack overflow");
            return;
        }
        stack[++top] = x;
    }

    public int pop() {
        if (isEmpty()) {
            System.out.println("Stack underflow");
            return -1;
        }
        return stack[top--];
    }

    public int peek() {
        if (isEmpty()) {
            System.out.println("Stack is empty");
            return -1;
        }
        return stack[top];
    }

    public boolean isEmpty() {
        return top == -1;
    }

    public boolean isFull() {
        return top == capacity - 1;
    }
}

public class Main {
    public static void main(String[] args) {
        Stack stack = new Stack(5);

        stack.push(10);
        stack.push(20);
        stack.push(30);

        System.out.println(stack.peek()); 
        stack.pop(); 
        System.out.println(stack.peek()); 
        System.out.println(stack.isEmpty());
        // 반환 : 30 20 false 
    }
}


```

<br>

### 스택 구현 
1. 배열을 사용한 구현
- 크기가 고정된 배열로 스택 구현
- 접근 속도가 빠름 
```java

class ArrayStack {
    private int[] stack;
    private int top;
    private int capacity;

    public ArrayStack(int size) {
        stack = new int[size];
        capacity = size;
        top = -1;
    }

    public void push(int x) {
        if (top == capacity - 1) {
            System.out.println("Stack overflow");
            return;
        }
        stack[++top] = x;
    }

    public int pop() {
        if (isEmpty()) {
            System.out.println("Stack underflow");
            return -1;
        }
        return stack[top--];
    }

    public boolean isEmpty() {
        return top == -1;
    }
}

```

<br>

2. Linked List를 통한 구현
- 동적 메모리 할당을 통해 크기 제한이 없음 
- 포인터 저장으로 인한 추가적인 메모리가 사용됨 
```java

class Node {
    int data;
    Node next;

    public Node(int data) {
        this.data = data;
        this.next = null;
    }
}

class LinkedListStack {
    private Node top;

    public LinkedListStack() {
        top = null;
    }

    public void push(int x) {
        Node newNode = new Node(x);
        newNode.next = top;
        top = newNode;
    }

    public int pop() {
        if (isEmpty()) {
            System.out.println("Stack underflow");
            return -1;
        }
        int data = top.data;
        top = top.next;
        return data;
    }

    public boolean isEmpty() {
        return top == null;
    }
}

```

<br>

3. 내장 클래스를 통한 구현 
- java.util.Stack 클래스 
```java

import java.util.Stack;

public class Main {
    public static void main(String[] args) {
        Stack<Integer> stack = new Stack<>();

        stack.push(10);
        stack.push(20);
        System.out.println(stack.pop()); 
        System.out.println(stack.peek());
        System.out.println(stack.isEmpty());
        // 반환 : 20 10 false
    }
}

```

<br>

### 스택 활용 
- 괄호 유효성 검사 : 열고 닫는 괄호가 올바르게 배치 되었는지 확인 
- 중위 표현식을 후위 표현식으로 변환 : 연산자의 우선순위를 고려해 변환함
- 후위 표현식 계산 : 후위 표기법으로 표현된 수식 평가 
- 최소값 스택 설계 : 현재 스택의 최소값을 `O(1)` 시간복잡도로 반환 


<br>

### 스택의 한계
- 배열 기반 스택 : 고정된 크기를 초과하면 스택 오버플로우가 발생함 
- 스택 오버플로우 : 너무 많은 데이터를 push() 하면 발생 
- 동적 메모리 할당 필요 : 동적 메모리 할당을 통해 스택 크기 제한을 피할 수 있지만 메모리 사용량 증가 및 오버헤드가 발생할 수 있음 

<br>

### 재귀와 스택 
- 재귀 호출은 내부적으로 스택 프레임을 사용해 함수 호출 정보를 저장하며 각 함수 호출은 스택에 쌓이고 함수가 반환될 때 스태택에서 제거됨 무한 재귀는 스택 오버플로우를 일으킴


<br>


### DFS에서의 활용 
- 스택을 사용하면 DFS 탐색 순서를 명확히 제어 가능 
```java

import java.util.Stack;

public class DFSExample {
    public static void main(String[] args) {
        int[][] graph = {
            {0, 1, 0, 0, 1},
            {1, 0, 1, 1, 0},
            {0, 1, 0, 1, 0},
            {0, 1, 1, 0, 1},
            {1, 0, 0, 1, 0},
        };
        boolean[] visited = new boolean[graph.length];
        Stack<Integer> stack = new Stack<>();

        stack.push(0); 
        while (!stack.isEmpty()) {
            int node = stack.pop();
            if (!visited[node]) {
                visited[node] = true;
                System.out.print(node + " ");
                for (int i = 0; i < graph[node].length; i++) {
                    if (graph[node][i] == 1 && !visited[i]) {
                        stack.push(i);
                    }
                }
            }
        }
    }
}

```

<br>


### 스택을 통한 백트래킹 
- 스택은 백트래킹에서 상태를 저장하고 탐색 경로를 기억하는 데 사용됨 스택에 현재 상태를 저장하고 유효하지 않은 경로에서 되돌아 올 때 스택을 통해 이전 상태를 복원할 수 있음 


<br>

### 스택의 시간복잡도
| 연산      | 배열 기반 스택 | 연결 리스트 기반 스택 | 설명                        |
|:-------:|:--------:|:------------:|:-------------------------:|
| push    | O(1)     | O(1)         | 데이터를 스택 맨 위에 추가          |
| pop     | O(1)     | O(1)         | 스택의 맨 위 데이터 제거 및 반환       |
| peek    | O(1)     | O(1)         | 스택의 맨 위 데이터 확인            |
| isEmpty | O(1)     | O(1)         | 스택이 비어 있는지 확인             |
| isFull  | O(1)     | N/A          | 배열 기반 스택에서만 사용 (고정 크기 때문) |


<br>

---

<br>

## 큐 (Queue)
> 큐란 먼저 들어온 데이터가 먼저 나가는 FIFO 구조의 자료구조 

<br>

### 큐의 특징 
- 삽입은 rear(뒤쪽), 삭제는 front(앞쪽)에서 이뤄짐
- 크기가 제한된 경우 오버 플로우가 발생할 수 있음 

<br>


### 큐 연산 
- enqueue(): 데이터를 큐에 추가
- dequeue(): 큐에서 데이터를 제거하고 반환
- peek(): 큐의 front 데이터 반환 
- isEmpty(): 큐가 비어 있는지 확인
- isFull(): 큐가 가득 찼는지 확인
```java

class Queue {
    private int[] queue;
    private int front, rear, capacity;

    public Queue(int size) {
        capacity = size;
        queue = new int[size];
        front = 0;
        rear = -1;
    }

    public void enqueue(int x) {
        if (isFull()) {
            System.out.println("Queue overflow");
            return;
        }
        queue[++rear] = x;
        System.out.println(x + " enqueued");
    }

    public int dequeue() {
        if (isEmpty()) {
            System.out.println("Queue underflow");
            return -1;
        }
        int data = queue[front++];
        System.out.println(data + " dequeued");
        return data;
    }

    public int peek() {
        if (isEmpty()) {
            System.out.println("Queue is empty");
            return -1;
        }
        return queue[front];
    }

    public boolean isEmpty() {
        return front > rear;
    }

    public boolean isFull() {
        return rear == capacity - 1;
    }
}



```

<br>

### 큐 구현 
1. 배열을 사용한 구현 
- 크기가 고정됨 
```java

class ArrayQueue {
    private int[] queue;
    private int front, rear, capacity;

    public ArrayQueue(int size) {
        queue = new int[size];
        capacity = size;
        front = 0;
        rear = -1;
    }

    public void enqueue(int x) {
        if (rear == capacity - 1) {
            System.out.println("Queue overflow");
            return;
        }
        queue[++rear] = x;
    }

    public int dequeue() {
        if (isEmpty()) {
            System.out.println("Queue underflow");
            return -1;
        }
        return queue[front++];
    }

    public boolean isEmpty() {
        return front > rear;
    }
}

```

<br>


2. Linked List를 사용한 구현
```java

class Node {
    int data;
    Node next;

    public Node(int data) {
        this.data = data;
        this.next = null;
    }
}

class LinkedListQueue {
    private Node front, rear;

    public LinkedListQueue() {
        front = rear = null;
    }

    public void enqueue(int x) {
        Node newNode = new Node(x);
        if (rear != null) {
            rear.next = newNode;
        }
        rear = newNode;
        if (front == null) {
            front = newNode;
        }
    }

    public int dequeue() {
        if (isEmpty()) {
            System.out.println("Queue underflow");
            return -1;
        }
        int data = front.data;
        front = front.next;
        if (front == null) {
            rear = null;
        }
        return data;
    }

    public boolean isEmpty() {
        return front == null;
    }
}

```

<br>

3. 내장 클래스를 통한 구현 
- `java.util.Queue` 인터페이스의 `LinkedList` 또는 `ArrayDeque`를 통해 구현됨
- `LinkedList` : 메모리 동적 할당 가능한 양방향 연결 리스트로 구현됨
- `ArrayDeque` : 메모리 연속 할당 가능
```java

import java.util.LinkedList;
import java.util.Queue;

public class Main {
    public static void main(String[] args) {
        Queue<Integer> queue = new LinkedList<>();

        queue.add(10); 
        queue.add(20);
        System.out.println(queue.poll()); 
        System.out.println(queue.peek()); 
        System.out.println(queue.isEmpty()); 
        // 반환 : 10 20 false 
    }
}

```

<br>

### 선형 큐 (Linear Queue)
- 배열 기반 큐로 rear가 끝까지 차면 오버플로우 발생함 데이터가 제거된 뒤에도 공간 재활용이 어렵다는 단점이 있음

<br>

### 원형 큐 (Circular Queue)
- rear와 front가 순환 구조를 가지고 배열을 재사용 할 수 있어 메모리 효율성이 좋음 
```java

// 배열 기반 원형 큐 
class CircularQueue {
    private int[] queue;
    private int front, rear, capacity, size;

    public CircularQueue(int capacity) {
        this.capacity = capacity;
        queue = new int[capacity];
        front = 0;
        rear = -1;
        size = 0;
    }

    public void enqueue(int x) {
        if (isFull()) {
            System.out.println("Queue overflow");
            return;
        }
        // 순환 구조
        rear = (rear + 1) % capacity; 
        queue[rear] = x;
        size++;
    }

    public int dequeue() {
        if (isEmpty()) {
            System.out.println("Queue underflow");
            return -1;
        }
        int data = queue[front];
        // 순환 구조 
        front = (front + 1) % capacity; 
        size--;
        return data;
    }

    public boolean isEmpty() {
        return size == 0;
    }

    public boolean isFull() {
        return size == capacity;
    }
}

```


<br>

### 데큐 (Deque)
- 양쪽에서 삽입, 삭제 연산이 가능한 큐로 Java에서 `ArrayDeque` 클래스를 사용하여 구현 가능 
```java

import java.util.ArrayDeque;

public class Main {
    public static void main(String[] args) {
        ArrayDeque<Integer> deque = new ArrayDeque<>();

        deque.addFirst(10); // 앞에서 삽입
        deque.addLast(20);  // 뒤에서 삽입
        System.out.println(deque.pollFirst()); // 앞에서 제거
        System.out.println(deque.pollLast());  // 뒤에서 제거
    }
}

```

<br>

### 우선순위 큐 (Priority Queue) 
- element가 우선순위에 따라 정렬되어 처리되는 큐로 Java에서 `PriorityQueue` 클래스를 사용하여 구현
```java

import java.util.PriorityQueue;

public class Main {
    public static void main(String[] args) {
        PriorityQueue<Integer> pq = new PriorityQueue<>();

        pq.add(30);
        pq.add(10);
        pq.add(20);

        System.out.println(pq.poll()); // 가장 낮은 값 10 출력
        System.out.println(pq.poll()); // 20
        System.out.println(pq.poll()); // 30
    }
}

```

<br>


### 큐 활용 
- BFS : 너비 우선 탐색에서 방문 노드를 순서대로 처리
- 캐시 구현 : 최근 사용 데이터를 관리
- 운영체제 프로세스 스케줄링 : 작업을 순서대로 처리
- 데이터 흐름 관리 : 네트워크 트래픽 처리

<br>


### 큐의 한계 
- 배열 기반 큐 : 크기 제한으로 인한 오버플로우 발생 가능 
- 선형 큐 : 큐의 front에서 데이터가 제거된 뒤에도 배열 공간을 재활용 하지 못해 메모리 낭비 발생 
- 원형 큐 : 배열 크기가 고정 돼 있어 데이터가 계속 삽입되면 크기를 재조정 해야 함 
- 연결 리스트 : 노드마다 추가 메모리가 필요하기 때문에 메모리 사용량이 배열 기반 큐에 비해 많음 


<br>


### 큐의 시간복잡도
| 연산      | 배열 기반 큐 | 연결 리스트 기반 큐 | 설명                       |
|:-------:|:-------:|:-----------:|:------------------------:|
| enqueue | O(1)    | O(1)        | 데이터를 큐의 rear에 추가         |
| dequeue | O(1)    | O(1)        | 데이터를 큐의 front에서 제거 및 반환  |
| peek    | O(1)    | O(1)        | 큐의 front 데이터를 반환         |
| isEmpty | O(1)    | O(1)        | 큐가 비어 있는지 확인             |
| isFull  | O(1)    | N/A         | 배열 기반 큐에서만 사용 (고정 크기 때문) |


<br>

---

<br>

### 스택 vs 큐 정리 
| 구분          | 스택 (Stack)                     | 큐 (Queue)                       |
|:-------------:|:--------------------------------:|:--------------------------------:|
| 데이터 처리 방식 | **LIFO** (Last In, First Out)   | **FIFO** (First In, First Out)   |
| 삽입 위치       | Top                             | Rear                             |
| 삭제 위치       | Top                             | Front                            |
| 주요 연산       | push, pop, peek                 | enqueue, dequeue, peek           |
| 활용 예시       | 재귀 호출, DFS, 백트래킹        | BFS, 캐시, 프로세스 스케줄링     |
| 자료구조 특징   | 한쪽 끝에서 삽입과 삭제         | 양쪽 끝 사용 (입력/출력 분리)    |
| 구현 방식       | 배열, Linked List, java.util.Stack | 배열, Linked List, java.util.Queue |


<br>
