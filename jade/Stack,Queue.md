### **Stack의 특징**

- **후입선출 구조 (LIFO)**
    - 나중에 삽입된 데이터가 가장 먼저 삭제됨.
    - 데이터 삽입과 삭제는 스택의 **탑(Top)**에서만 이루어짐.
- **한쪽 방향 접근**
    - 스택은 한쪽 끝(Top)에서만 데이터를 추가하거나 제거할 수 있음.
- **순서 유지**
    - 삽입된 데이터의 순서를 유지하며, 순서대로 처리 가능.

---

### **Stack의 시간복잡도**

| 연산 | 시간 복잡도 | 설명 |
| --- | --- | --- |
| **삽입 (Push)** | O(1) | 데이터를 스택의 Top에 추가. Top 위치만 변경되므로 시간 복잡도는 O(1). |
| **삭제 (Pop)** | O(1) | 스택의 Top에서 데이터를 제거. Top 위치만 이동하므로 시간 복잡도는 O(1). |
| **탐색 (Search)** | O(n) | 스택 전체를 순차적으로 탐색해야 하므로 시간 복잡도는 O(n). |
| **읽기 (Peek)** | O(1) | 스택의 Top에 있는 데이터를 읽는 연산으로, 데이터 이동 없이 Top을 참조만 하므로 O(1). |

---

### **Stack의 예시**

**삽입 (Push)과 삭제 (Pop) - O(1)**

```java
import java.util.Stack;

public class Example {
    public static void main(String[] args) {
        Stack<Integer> stack = new Stack<>();

        // 삽입 (Push)
        stack.push(1);  // O(1)
        stack.push(2);  // O(1)
        
        // 삭제 (Pop)
        stack.pop();    // O(1)
        
        System.out.println(stack.peek()); // O(1)
    }
}

```

탐색 - O(n)

```java
import java.util.Stack;

public class Example {
    public static void main(String[] args) {
        Stack<Integer> stack = new Stack<>();
        stack.push(1);
        stack.push(2);
        stack.push(3);

        for (int num : stack) {
            System.out.println(num); // -> O(n)
        }
    }
}

```

---

### **Queue의 특징**

- **선입선출 구조 (FIFO)**
    - 먼저 삽입된 데이터가 가장 먼저 삭제됨.
- **양쪽 방향 접근**
    - 데이터 삽입은 큐의 **뒤쪽(Rear)**에서, 삭제는 **앞쪽(Front)**에서 이루어짐.
- **순서 유지**
    - 삽입된 데이터의 순서를 유지하며, 순서대로 처리 가능.

---

### **Queue의 시간복잡도**

| 연산 | 시간 복잡도 | 설명 |
| --- | --- | --- |
| **삽입 (Enqueue)** | O(1) | 데이터를 큐의 Rear에 추가. Rear 위치만 이동하므로 시간 복잡도는 O(1). |
| **삭제 (Dequeue)** | O(1) | 큐의 Front에서 데이터를 제거. Front 위치만 이동하므로 시간 복잡도는 O(1). |
| **탐색 (Search)** | O(n) | 큐 전체를 순차적으로 탐색해야 하므로 시간 복잡도는 O(n). |
| **읽기 (Peek)** | O(1) | 큐의 Front 데이터를 읽는 연산으로, 데이터 이동 없이 Front를 참조만 하므로 O(1). |

---

### **Queue의 코드 예시**

**삽입 (Enqueue)과 삭제 (Dequeue) - O(1)**

```java
import java.util.LinkedList;
import java.util.Queue;

public class Example {
    public static void main(String[] args) {
        Queue<Integer> queue = new LinkedList<>();

        // 삽입 (Enqueue)
        queue.add(1);  // O(1)
        queue.add(2);  // O(1)
        
        // 삭제 (Dequeue)
        queue.poll();  // O(1)
        
        System.out.println(queue.peek()); // O(1)
    }
}

```

탐색 - O(n)

```java
import java.util.LinkedList;
import java.util.Queue;

public class Example {
    public static void main(String[] args) {
        Queue<Integer> queue = new LinkedList<>();
        queue.add(1);
        queue.add(2);
        queue.add(3);

        for (int num : queue) {
            System.out.println(num); // -> O(n)
        }
    }
}

```

---

### **Stack과 Queue의 비교**

| 특성 | **Stack** | **Queue** |
| --- | --- | --- |
| **구조** | LIFO (후입선출) | FIFO (선입선출) |
| **삽입 위치** | Top | Rear (뒤) |
| **삭제 위치** | Top | Front (앞) |
| **삽입/삭제 속도** | O(1) | O(1) |
| **탐색 속도** | O(n) | O(n) |
| **사용 예시** | 재귀 호출, 괄호 검사, 되돌리기 기능 | 작업 대기열, BFS, 캐시 시스템 |
|  |  |  |

---

### **정리**

- **Stack**은 **후입선출** 작업이 필요한 경우(예: 재귀, 실행 흐름 관리)에 적합.
- **Queue**는 **선입선출** 작업이 필요한 경우(예: 작업 큐, 데이터 흐름 제어)에 적합.
