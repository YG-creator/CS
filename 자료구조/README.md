# 1. List

## Array

index로 바로 조회가능

삭제 및 추가시 shift 과정이 필요

## Linked

index 없음, 자신 다음에 어떤 원소인지만 기록

삽입, 삭제 시 shift 과정이 필요없으나, index가 없어서 차례대로 찾아야 됨

# 2. Stack

* LIFO

# 3. Queue

* FIFO

# 4. Tree

## 정의

* 비선형 계층적 자료구조

## 용어

- Node  : 트리를 구성하고 있는 각각의 요소
- Edge (간선) : 노드와 노드를 연결하는 선
- Root Node  : 최상위에 있는 노드
- Terminal Node ( = leaf Node, 단말 노드) : 자식 노드 없는 최하위 노드
- Internal Node (내부노드, 비단말 노드) : 단말 노드를 제외한 모든 노드(루트 노드 포함)

## Binary Tree

* 자식 노드가 최대 2개인 트리

* 층별로 숫자(Level or height)를 매김 (루트노드는 0)

* 종류

  * Perfect Binary Tree (포화 이진 트리)

    모든 레벨이 꽉찬 이진 트리

  * Complete Binary Tree (완전 이진 트리)

    위->아래, 왼 -> 오 차고차곡 채워진 이진 트리

  * Full Binary Tree (정 이진 트리)

    모든 노드가 0개 혹은 2개의 자식 노드만을 갖는 이진 트리



## BST(Binary Search Tree)

* 효율적인 탐색을 위한 저장방법
* 이진 탐색 트리
* 노드에 저장된 키는 유일하다.
* 왼쪽 자식 노드 < 부모 노드 < 오른쪽 자식 노드 
* 편향 트리가 되면 비효율적 -> Rebalancing 작업이 필요(Red-Black Tree)



# 3. Binary Heap

## 특징

* Complete Binary Tree
* 최댓값 or 최솟값 찾을 때 사용 O(1)
* 새로운 값 추가시 heapify 과정 필요 O(log n)



## 종류

* Max Heap

  각 노드의 값이 자식 노드보다 크거나 같은 Complete Binary Tree(왼->오, 위->아래 차고차곡)

  최댓값 찾을 때 사용 O(1)

* Min Heap

  각 노드의 값이 자식 노드보다 작거나 같은 Complete Binary Tree(왼->오, 위->아래 차고차곡)

  최댓값 찾을 때 사용 O(1)



# 4. Red Black Tree

## 정의

1. 각 노드는 Red or Black 

2. 루트 노드는 Black

3. 단말 노드는 Black

4. Red인 노드의 자식 노드는 Black

5. *Black-Height:*

   노드 x  ~ 노드 x 를 포함하지 않은 leaf node 까지의 simple path 상에 있는 black nodes 들의 개수

## 특징

1. BST 
2. balanced 상태(최소 경로 : 최대 경로 = 1 : 2)
3. 노드의 자식이 비어있을 때는 NIL값을 저장



## 사용 이유

BST 삽입, 삭제시 문제접 해결

balanced 상태(최소 경로 : 최대 경로 = 1 : 2)가 됨

Tree Map, Hash Map(Seperate Chaining)에 사용

## 삽입

삽입된 노드는 RED -> RBT 특징 위배 시 색깔 조정  /  Black-Height 위배 시 rotation

## 삭제

지워진 노드가  Black -> Black-Height이 1 감소한 경로에 Blac node가 1개 추가 되도록 rotation -> 색깔 조정

지워진 노드가 Red -> 그대로

# 5. Hash

## 특징

* 배열을 사용

* index = Hash function() 값

## Hash function

* 문제점

  * 1:1 대응 관계를 만들면 비효율적
  * Collision(index가 겹침) 피해야 됨

* 해결법

  * Open Address 방식 (개방주소법)

    * Collision 발생 시 다른 해시 버킷에 해당 자료를 삽입하는 방식
    * 버킷 밀도가 높을수록 비효율적
    * Seperate Chaining 보다 느림
    * 연속된 공간에 데이터를 저장해서 캐시 효율이 높다.

  *  Separate Chaining 방식 (분리 연결법)

    * 보조 해시 함수로 Collision 발생 방지

    * 방식

      * LinkedList : 데이터 갯수가 적을 때 사용(기준 key-value 쌍 6개 8개)

      * RBT : 데이터 갯수가 많을 때 사용

    * 테이블 확장을 늦출 수 있다.

## 해시 버킷 수 확장

* 현재 데이터 개수가 해시 버킷의 개수의 75%가 될 때 버킷의 갯수 2 배로 늘린다.



# 6. Graph

## 정의

* 정점과 간선의 집합



## 용어

* 단방향 vs 양방향
* Degree : 노드에 연결된 간선의 갯수 
  * Outdegree : 나감
  * Indegree : 들어옴

## 구현

* Array : 밀도가 높을수록 좋음
* List : 밀도가 낮을수록 좋음



## 탐색

* BFS
* DFS



## Minimum Spanning Tree

### 정의

* edge weight 의 합이 최소인 `spanning tree`

### 알고리즘

* Krustal

  edge weight 오름차순 정렬 -> 사이클이 안생길 때(if(find(a) != find(b))) ->  그래프에 추가 union(a,b)

* Prim