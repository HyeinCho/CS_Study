# Array vs Linked List, Stack & Queue, Binary Heap

## **Array vs Linked List**

### **Array**

- 논리적 저장 순서(배열 인덱스 순서)와 물리적 저장 순서(메모리의주소)가 일치하는 자료구조
- 인덱스로 특정 원소(element)에 접근할 수 있음 → 시간복잡도 O(1)

    ⇒ **random access**(어떤 위치에라도 곧바로 접근 할 수 있음)가 가능

- 삭제, 삽입 과정 시간 복잡도 = O(N)

    해당 원소에 접근하여 작업(O(1)) & 나머지 원소들을 shift(O(N)) 

- 저장방식: 배열에서 요소들은 인접한 메모리 위치에 연이어 저장
- 메모리는 선언 시 컴파일 타임에 할당(정적 메모리 할당)

### **Linked List**

- 각 노드가 데이터와 포인터를 가지고 한 줄로 연결되어 있는 방식으로 데이터를 저장하는 자료 구조

    → 각각의 원소들은 자기 자신 다음에 어떤 원소인지만을 기억

- 특정 요소에 접근할 때  첫번째 원소부터 순차적으로 검색 → 시간복잡도 O(N)

    ⇒ **sequential access**

- Array 와 달리 논리적 저장 순서와 물리적 저장 순서가 일치하지 않음
- 삭제, 삽입 과정 시간 복잡도 = O(N)

    해당 원소에 접근하여 작업(O(1)) & 원하는 위치 search(O(N))

- 새로운 요소가 추가될 때 런타임에 메모리를 할당(동적 메모리 할당)

---

## Stack & Queue

### **Stack**

- 선형 자료구조의 일종으로 Last In First Out (LIFO)
- 같은 구조와 크기의 자료를 정해진 방향으로 쌓을 수 있고, 한 방향으로만 접근할 수 있음
- DFS나 재귀에서 사용됨

### **Queue**

- 선형자료구조의 일종으로 First In First Out (FIFO)
- 주로 데이터가 입력된 시간 순서대로 처리되어야 하는 경우 사용
- BFS나 캐시를 구현할 때 사용됨

---

## Binary Heap

- 자료구조의 일종으로 Tree 의 형식을 하고 있으며, Tree 중에서도 배열에 기반한 힙 속성을 가진 Complete Binary Tree

    º Complete Binary Tree: 마지막 레벨을 제외하고 모든 레벨이 완전히 채워져 있으며, 마지막 레벨의 모든 노드는 가장 왼쪽부터 채워져 있음

    º 힙 속성: 각 노드에 저장된 키는 일부 총 순서 에 따라 노드의 하위 키보다 크거나 같거나 (부모노드≥자식노드, max-heap) 작거나 같음  
    (부모노드≤자식노드, min-heap) 

- 배열에 트리의 값들을 넣어줄 때, 0 번째는 건너뛰고 1 번 index 부터 루트노드가 시작(노드의 고유번호 값과 배열의 index 를 일치시켜 혼동을 줄이기 위함)

    º 힙에서의 부모 노드와 자식 노드의 관계

    왼쪽 자식의 인덱스 = (부모의 인덱스) * 2  
    오른쪽 자식의 인덱스 = (부모의 인덱스) * 2 + 1  
    부모의 인덱스 = (자식의 인덱스) / 2

- Heap의 종류


  º Max Heap, Min Heap

  각 노드의 값이 해당 children 의 값보다 크거나 같은 complete binary tree ( Min Heap 은 그 반대)

  Root node 에 있는 값이 제일 크므로(작으므로), 최대값(최소값)을 찾는데 소요되는 연산의 시간 복잡도 = O(1)

  완전 이진 트리이기 때문에 배열을 사용하여 효율적으로 관리 (즉, random access 가 가능) 

  삽입, 제거 작업 시간 복잡도 =  O(log N)

---

- 면접질문

    º array와 linked list의 차이점?

    º stack과 queue 사용 예시?

---

- 출처

    º [https://github.com/JaeYeopHan/Interview_Question_for_Beginner/tree/master/DataStructure](https://github.com/JaeYeopHan/Interview_Question_for_Beginner/tree/master/DataStructure)

    º [https://en.wikipedia.org/wiki/Binary_heap](https://en.wikipedia.org/wiki/Binary_heap)
