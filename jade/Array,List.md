### Array의 특징

- 고정된 크기 → 배열 선언할 때 크기를 지정하며, 한 번 선언된 크기는 변경할 수 없음
- 배열 내 데이터 타입 동일 → 배열에 저장하는 데이터의 타입은 동일함
- 빠른 인덱스 접근 → 배열의 인덱스를 사용하여 빠르게 접근 가능

### Array의 시간복잡도

- 빠른 인덱스 접근으로 인하여, 배열의 특정 요소에 접근하는 시간 → O(1)

```java
public class Example {
    public static void main(String[] args) {
        int[] arr = {1, 2, 3, 4, 5};
        System.out.println(arr[0]);
        // -> O(1)
    }
}
```

- 크기가 n인 배열의 모든 요소를 순차적으로 탐색하는 시간 → O(n)

```java
public class Example {
    public static void main(String[] args) {
        int[] arr = {1, 2, 3, 4, 5};
        for (int i = 0; i < arr.length; i++) {
            System.out.println(arr[i]);
            // -> 5번 반복. O(n)
        }
    }
}
```

- 요소의 추가(배열의 공간이 남아있는 경우, 그냥 바로 넣으면 됨) → O(1)
- 요소의 추가(배열의 공간이 남아있지 않아 확장이 필요한 경우, 배열을 큰놈으로 선언하고 어쨋든 다시 요소를 복사해야하므로 이때 드는시간이 n임) → O(n)
- 요소의 삭제(끝에서 삭제, 그냥 지우면 됨) → O(1)
- 요소의 삭제(중간에서 삭제, 최악의 경우 0번 인덱스를 지울때 드는시간 n) → O(n)

---

### ArrayList의 특징(Java의 ArrayList)

- 동적 크기 → 리스트는 동적으로 크기가 변할 수 있음. 데이터의 추가, 삭제가 용이함
- 리스트 내 데이터 타입 동일 → 리스트에 저장되는 데이터의 타입은 동일해야함
- 순서 보장 → 리스트는 데이터가 삽입된대로 저장됨. 즉, 인덱스를 사용하여 빠른 접근 가능

### ArrayList의 시간복잡도

- 빠른 인덱스 접근으로 인하여, 리스트의 특정 요소에 접근하는 시간 → O(1)

```java
public class Example {
    public static void main(String[] args) {
        List<Integer> list = new ArrayList<>(List.of(1, 2, 3, 4, 5));
        System.out.println(list.get(0));
        // -> O(1)
    }
}
```

- 크기가 n인 리스트의 모든 요소를 순차적으로 탐색하는 시간 → O(n)

```java
public class Example {
    public static void main(String[] args) {
        List<Integer> list = new ArrayList<>(List.of(1, 2, 3, 4, 5));
        for (int i = 0; i < list.size(); i++) {
            System.out.println(list.get(i));
            // -> 5번 반복. O(n)
        }
    }
}
```

- 요소 추가(공간이 남아있는 경우, 배열 끝에 바로 추가) → O(1)
- 요소 추가(공간이 부족한 경우, 내부 배열 확장 후 기존 요소 복사) → O(n)
- 요소 삭제(끝에서 삭제) → O(1)
- 요소 삭제(중간에서 삭제) → O(n)

---

### LinkedList의 특징

- 노드 기반 구조 → 각 요소는 노드로 저장되며 다음 노드의 주소를 저장함
- 동적 크기 → 메모리를 동적으로 할당하므로 크기가 고정되지 않음
- 삽입/삭제 속도 → 특정 위치에서 삽입/삭제가 빠름(주소 변경으로 처리)
- 인덱스 접근 속도 → 인덱스 접근이 느림(순차적 탐색 필요)

### LinkedList의 시간복잡도

- 요소 접근(처음 노드부터 순차적으로 탐색해야 함) → O(n)

```java
public class Example {
    public static void main(String[] args) {
        LinkedList<Integer> list = new LinkedList<>();
        list.add(1);
        list.add(2);
        list.add(3);

        System.out.println(list.get(2)); // -> O(n)
    }
}
```

- 순차 탐색 → O(n)

```java
public class Example {
    public static void main(String[] args) {
        LinkedList<Integer> list = new LinkedList<>();
        list.add(1);
        list.add(2);
        list.add(3);

        for (int num : list) {
            System.out.println(num); // -> O(n)
        }
    }
}
```

- 요소 추가(끝에 추가) → O(1)
- 요소 추가(중간에 추가, 삽입 위치를 찾기 위해 순차 탐색이 필요함) → O(n)
- 요소 삭제(끝에서 삭제) → O(1)
- 요소 삭제(중간에서 삭제) → O(n)

---

### Array와 List(Linked List)의 비교

| 특성 | **Array** | **List (Linked List)** |
| --- | --- | --- |
| **메모리 구조** | 연속적인 메모리 공간 | 불연속적 노드 연결 |
| **크기 조정** | 고정 크기 | 동적 크기 |
| **삽입/삭제 속도** | 끝: O(1), 중간: O(n) | 처음/끝: O(1), 중간: O(n) |
| **접근 속도** | O(1) | O(n) |
| **메모리 사용** | 효율적 | 포인터 저장으로 오버헤드 발생 |
| **사용 예시** | 정적 데이터 | 동적 데이터 처리 |

### **정리**

- **Array**는 **빠른 데이터 접근**이 필요한 경우 적합.→ 고정 크기의 데이터, 순차적 접근을 자주 사용하는 경우.
- **List**는 **삽입/삭제가 빈번한 데이터 처리**에 적합.→ 데이터 크기가 동적으로 변하거나, 중간 삽입/삭제가 많을 때 효율적.


