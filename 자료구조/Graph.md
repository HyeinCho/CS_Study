## Graph

### 정점과 간선의 집합, Graph

_cf) 트리 또한 그래프이며, 그 중 사이클이 허용되지 않는 그래프를 말한다._

### 그래프 관련 용어 정리

#### Undirected Graph 와 Directed Graph (Digraph)

말 그대로 정점과 간선의 연결관계에 있어서 방향성이 없는 그래프를 Undirected Graph 라 하고,
간선에 방향성이 포함되어 있는 그래프를 Directed Graph 라고 한다.

<img width="533" alt="a" src="https://user-images.githubusercontent.com/42761910/105529197-64bbbe80-5d29-11eb-9c7f-388f0b82c9af.png">


* Directed Graph (Digraph)

```
V = {1, 2, 3, 4, 5, 6}
E = {(1, 4), (2,1), (3, 4), (3, 4), (5, 6)}
(u, v) = vertex u에서 vertex v로 가는 edge
```

* Undirected Graph

```
V = {1, 2, 3, 4, 5, 6}
E = {(1, 4), (2,1), (3, 4), (3, 4), (5, 6)}
(u, v) = vertex u와 vertex v를 연결하는 edge
```

#### Degree

Undirected Graph 에서 각 정점(Vertex)에 연결된 Edge 의 개수를 Degree 라 한다.
Directed Graph 에서는 간선에 방향성이 존재하기 때문에 Degree 가 두 개로 나뉘게 된다.
각 정점으로부터 나가는 간선의 개수를 Outdegree 라 하고, 들어오는 간선의 개수를 Indegree 라 한다.

#### 가중치 그래프(Weight Graph)와 부분 그래프(Sub Graph)

가중치 그래프란 간선에 가중치 정보를 두어서 구성한 그래프를 말한다. 반대의 개념인 비가중치 그래프 즉, 모든 간선의 가중치가 동일한 그래프도 물론 존재한다. 부분 집합과 유사한 개념으로 부분 그래프라는 것이 있다. 부분 그래프는 본래의 그래프의 일부 정점 및 간선으로 이루어진 그래프를 말한다.

</br>

### 그래프를 구현하는 두 방법

#### 인접 행렬 (adjacent matrix) : 정방 행렬을 사용하는 방법

해당하는 위치의 value 값을 통해서 vertex 간의 연결 관계를 O(1) 으로 파악할 수 있다. Edge 개수와는 무관하게 V^2 의 Space Complexity 를 갖는다. Dense graph 를 표현할 때 적절할 방법이다.

##### ex)
     1  2  3  4  5  6
   ---------------------
1 |  0  1  0  0  0  0 \
2 |  0  0  1  0  0  0 \
3 |  0  0  0  0  0  0  \
4 |  0  0  0  0  1  1 \
5 |  0  0  0  0  0  0 \
6 |  0  0  1  0  0  0   방향성이 없는 그래프 구현하고 싶다? 그러면 대각선 대칭 해주면됨


#### 인접 리스트 (adjacent list) : 연결 리스트를 사용하는 방법

vertex 의 adjacent list 를 확인해봐야 하므로 vertex 간 연결되어있는지 확인하는데 오래 걸린다. Space Complexity 는 O(E + V)이다. Sparse graph 를 표현하는데 적당한 방법이다.

##### ex) 위 정방행렬을 인접리스트로 표현해보기
(1,2)
(2,3)
(4,5)
(4,6)
(6,3)

</br>

### 그래프 탐색

그래프는 정점의 구성 뿐만 아니라 간선의 연결에도 규칙이 존재하지 않기 때문에 탐색이 복잡하다. 따라서 그래프의 모든 정점을 탐색하기 위한 방법은 다음의 두 가지 알고리즘을 기반으로 한다.

#### 깊이 우선 탐색 (Depth First Search: DFS)

그래프 상에 존재하는 임의의 한 정점으로부터 연결되어 있는 한 정점으로만 나아간다라는 방법을 우선으로 탐색한다. 일단 연결된 정점으로 탐색하는 것이다. 연결할 수 있는 정점이 있을 때까지 계속 연결하다가 더이상 연결되지 않은 정점이 없으면 바로 그 전 단계의 정점으로 돌아가서 연결할 수 있는 정점이 있는지 살펴봐야 할 것이다. 갔던 길을 되돌아 오는 상황이 존재하는 미로찾기처럼 구성하면 되는 것이다. 어떤 자료구조를 사용해야할까? 바로 Stack 이다.
**Time Complexity : O(V+E) … vertex 개수 + edge 개수**
<img src="https://user-images.githubusercontent.com/42761910/105529189-638a9180-5d29-11eb-9653-3bd7e4e76489.png" width=200 height=200>
<img src="https://user-images.githubusercontent.com/42761910/105529200-65545500-5d29-11eb-8682-3040f292539c.png" width=200 height=200>

#### 너비 우선 탐색 (Breadth First Search: BFS)

그래프 상에 존재하는 임의의 한 정점으로부터 연결되어 있는 모든 정점으로 나아간다. Tree 에서의 Level Order Traversal 형식으로 진행되는 것이다. BFS 에서는 자료구조로 Queue 를 사용한다. 연락을 취할 정점의 순서를 기록하기 위한 것이다.
우선, 탐색을 시작하는 정점을 Queue 에 넣는다.(enqueue) 그리고 dequeue 를 하면서 dequeue 하는 정점과 간선으로 연결되어 있는 정점들을 enqueue 한다.
즉 vertex 들을 방문한 순서대로 queue 에 저장하는 방법을 사용하는 것이다.
**Time Complexity : O(V+E) … vertex 개수 + edge 개수**
_**! BFS 로 구한 경로는 최단 경로이다.**_

<img src="https://user-images.githubusercontent.com/42761910/105529192-64232800-5d29-11eb-94d1-cfaa937bf046.png" width=200 height=200>
<img src="https://user-images.githubusercontent.com/42761910/105529625-00e5c580-5d2a-11eb-91bb-d0e1a2c8221c.png" width=200 height=200>
</br>

### Minimum Spanning Tree

그래프 G 의 spanning tree 중 edge weight 의 합이 최소인 `spanning tree`를 말한다. 여기서 말하는 `spanning tree`란 그래프 G 의 모든 vertex 가 cycle 이 없이 연결된 형태를 말한다.
잘 설명된 블로그 : https://gmlwjd9405.github.io/2018/08/28/algorithm-mst.html

##### cf) 어떻게 cycle 생성 여부를 판단하는가?

Graph 의 각 vertex 에 `set-id`라는 것을 추가적으로 부여한다. 그리고 초기화 과정에서 모두 1~n 까지의 값으로 각각의 vertex 들을 초기화 한다. 여기서 0 은 어떠한 edge 와도 연결되지 않았음을 의미하게 된다. 그리고 연결할 때마다 `set-id`를 하나로 통일시키는데, 값이 동일한 `set-id` 개수가 많은 `set-id` 값으로 통일시킨다.

dfs 로 back-edge 탐색으로 그래프싸이클 판단하는 것을 잘 설명한 블로그 : https://kim6394.tistory.com/228

### MST 구현 방법
#### 1. Kruskal Algorithm

초기화 작업으로 **edge 없이** vertex 들만으로 그래프를 구성한다. 그리고 weight 가 제일 작은 edge 부터 검토한다. 그러기 위해선 Edge Set 을 non-decreasing 으로 sorting 해야 한다. 그리고 가장 작은 weight 에 해당하는 edge 를 추가하는데 추가할 때 그래프에 cycle 이 생기지 않는 경우에만 추가한다. spanning tree 가 완성되면 모든 vertex 들이 연결된 상태로 종료가 되고 완성될 수 없는 그래프에 대해서는 모든 edge 에 대해 판단이 이루어지면 종료된다.
[Kruskal Algorithm의 세부 동작과정](https://gmlwjd9405.github.io/2018/08/29/algorithm-kruskal-mst.html)
[Kruskal Algorithm 관련 Code](https://github.com/morecreativa/Algorithm_Practice/blob/master/Kruskal%20Algorithm.cpp)

다시 말하자면? 
    전체간선값을 최솟값부터 나열해서 싸이클살피면서 간선 늘려가다가 n-1개 되면 멈추는 방법

##### Time Complexity

1.  Edge 의 weight 를 기준으로 sorting - O(E log E)
2.  cycle 생성 여부를 검사하고 set-id 를 통일 - O(E + V log V)
    => 전체 시간 복잡도 : O(E log E)

#### 2. Prim Algorithm

초기화 과정에서 한 개의 vertex 로 이루어진 초기 그래프 A 를 구성한다. 그리고나서 그래프 A 내부에 있는 vertex 로부터 외부에 있는 vertex 사이의 edge 를 연결하는데 그 중 가장 작은 weight 의 edge 를 통해 연결되는 vertex 를 추가한다. 어떤 vertex 건 간에 상관없이 edge 의 weight 를 기준으로 연결하는 것이다. 이렇게 연결된 vertex 는 그래프 A 에 포함된다. 위 과정을 반복하고 모든 vertex 들이 연결되면 종료한다.

다시 말하자면?
    정점하나잡아서 그 인접 정점까지의 간선들 중의 최솟값간선을 사이클확인하면서 간선추가하다가 n-1개 간선일 때 정점 n개 충족되면 멈추기

##### Time Complexity

=> 전체 시간 복잡도 : O(E log V)

</br>


--------------------------------------------------------
## 면접 예상 질문

### 최소 신장 트리(Minimum Spanning Tree)에 대해서 설명해주세요.(or 크루스칼,프림 알고리즘 설명해주세요 + 더 나아가서는 A*까지)

그래프 G의 스패닝 트리 중 edge weight 값이 최소인 스패닝 트리를 말한다. 스패닝 트리란 그래프 G의 모든 vertex가 cycle 없이 연결된 형태를 말한다. n개의 vertex를 가지는 그래프에서 반드시 (n-1)개의 edge만을 사용해야 하며 사이클이 포함되어서는 안 된다. Kruskal과 Prim을 통해서 MST를 구현할 수 있다. Kruskal의 경우 그래프의 간선들을 오름차순으로 정렬하여 가장 낮은 가중치의 간선부터 차례로 MST에 집합체 추가하는 그리디 알고리즘 방식을 사용한다. Prim의 경우는 시작 정점부터 단계적으로 트리를 확장하는 방법이다.

####이 이상의 깊은 질문은 안하는 듯 함.(아마도)
