# Stack, Queue
|  | **Stack** | **Queue** |
| --- | --- | --- |
| | ![](https://velog.velcdn.com/images/sisofiy626/post/903c827f-6595-49d0-a311-837b0311b30b/image.png) | ![](https://velog.velcdn.com/images/sisofiy626/post/ec98d0ca-51c7-4485-8e72-638a7402eee3/image.png )|
| **구조** | **LIFO** (Last In First Out) | **FIFO** (First In First Out) |
| **삽입 위치** | top (맨 위) | rear (맨 뒤) |
| **삭제 위치** | top (맨 위) | front (맨 앞) |
| **시간복잡도** | 삽입/삭제 : O(1)<br>탐색 : O(n) | 삽입/삭제 : O(1)<br>탐색 : O(n) |
| **사용 예시** | 브라우저 뒤로가기, 실행취소(Undo), 재귀 함수 | 프린터 대기열, BFS(너비 우선 탐색) |


<br>

## 큐의 종류

### 우선순위 큐  Priority Queue

우선순위에 따라 요소를 정렬하여 처리하는 자료구조. 힙을 기반으로 구현된다. 

각 요소는 값과 우선순위 총 2가지 데이터를 가지고 있다. 우선순위가 높은 요소일수록 먼저 삭제된다. 우선순위가 같은 경우, 삽입 순서(FIFO)를 따른다. 

![image.png](https://velog.velcdn.com/images/sisofiy626/post/bda424e6-981a-4801-9ac8-f7e9dccf495f/image.png)

<br>

### 원형 큐  **Circular Queue**

선형 큐의 단점을 보완하기 위해 나온 개념으로, 열의 끝과 시작을 연결하여 공간 효율성을 높인 자료구조

![image.png](https://velog.velcdn.com/images/sisofiy626/post/e563df64-c66c-4ca3-87e1-346a77bea7e3/image.png)

배열 기반 큐에서 앞부분이 비어 공간을 재사용하지 못하는 문제를 해결한다. 선형 큐는 빈 공간을 활용하기 위해 현재 요소들을 앞으로 재배치하는 별도의 작업이 필요했지만 원형큐는 front와 rear가 순환하기 때문에 별도의 작업이 필요 없다. 

![image.png](https://velog.velcdn.com/images/sisofiy626/post/383bcb66-5487-4626-b547-563b7371a976/image.png)

<br>

### 양뱡향 큐  Deque (**Double-ended Queue)**

양쪽 모두 데이터의 삽입/삭제가 가능한 자료구조

![image.png](https://velog.velcdn.com/images/sisofiy626/post/376f2309-5a11-4d12-b9f6-4b04853ba660/image.png)

<br>

## **언어별 메서드 정리**
|  | 기능 | JavaScript (배열) | Java (`Stack`/`Queue`) | Python (`list`/`deque`) |
| --- | --- | --- | --- | --- |
| **Stack** | **삽입** | `push(item)` | `push(item)`  | `append(item)` |
|  | **삭제** | `pop()` | `pop()` | `pop()` |
|  | **조회(최상단)** | `stack[stack.length-1]` | `peek()` | `stack[-1]` |
| **Queue** | **삽입** | `push(item)` | `offer(item)` , `add(item)` | `append(item)` |
|  | **삭제** | `shift()` | `poll()`, `remove()`, `remove(item)` | `popleft()` |
|  | **조회(맨 앞)** | `queue[0]` | `peek()` | `queue[0]` |

<br>

>📎<br>- offer() : 큐가 가득 차서 요소를 추가 할수 없는 경우 **false**를 반환<br>- add() : 큐가 가득 차서 요소를 추가 할수 없는 경우 **IllegalStateException 예외**를 발생<br><br>- poll() : 삭제된 값 리턴, 공백 큐이면 **null** 리턴<br>- remove() : 삭제된 값 리턴, 공백 큐이면 **Exception("NoSuchElementException")** 발생<br>- remove(item) : 큐에 해당 item이 존재하면 해당 값 삭제 후 true 리턴, 존재하지 않으면 **false** 리턴

<br>

---
**🔗 참고)**
[블로그 링크](https://velog.io/@sisofiy626/%EC%9E%90%EB%A3%8C%EA%B5%AC%EC%A1%B0-2.-%EC%8A%A4%ED%83%9DStack%EA%B3%BC-%ED%81%90Queue-%EB%8D%B1Deque#%EC%8A%A4%ED%83%9D%EA%B3%BC-%ED%81%90-%EB%8D%B1)
