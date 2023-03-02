# 연결리스트(Linked Lists)
- 연속적인 메모리 위치에 저장되지 않는 선형 자료구조

### 장점
- 크기를 동적으로 설정할 수 있다.
- 데이터의 삽입, 삭제가 용이하다

### 단점
- 반드시 첫번째 노드부터 순차적으로 요소에 접근해야 한다. (이진 탐색 불가능)
- 각 요소마다 포인터를 위한 공간이 필요하다.
#

* * *

# 트리(Tree), 트라이(Trie), 그래프

## 트리(Tree)
- 값을 가진 노드와 이 노드들을 연결해주는 간선(Edge) 으로 이루어진 자료구조
- 그래프와 트리의 차이는 사이클(시작 지점과 마지막 지점이 같은 경로)의 유무로 설명된다.

### 순회 방식
#### 전위 순회
- 각 루트를 순차적으로 방문하는 방식
- Root -> 왼쪽 자식 -> 오른쪽 자식

#### 중위 순회
- 왼쪽 하위 트리를 방문 후 루트를 방문하는 방식
- 왼쪽 자식 -> Root -> 오른쪽 자식

#### 후위 순회
- 왼쪽 하위 트리부터 하위를 모두 방문 후 루트를 방문하는 방식
- 왼쪽 자식 -> 오른쪽 자식 -> Root

#### 레벨 순회
- 루트부터 계층 별로 방문하는 방식
- 각 계층별 왼쪽 노드 -> 오른쪽 노드


## 트라이(Trie)
- 문자열에서 검색을 빠르게 도와주는 자료구조

### 장점
* 문자열을 빠르게 찾을 수 있다.
* 추가 또한 빠르게 처리할 수 있다.

### 단점
* 필요한 메모리의 크기가 너무 크다.

### 자바 구현코드

```java
static class Trie {
    boolean end;
    boolean pass;
    Trie[] child;

    Trie() {
        end = false;
        pass = false;
        child = new Trie[10];
    }

    public boolean insert(String str, int idx) {

        //끝나는 단어 있으면 false 종료
        if(end) return false;

        //idx가 str만큼 왔을때
        if(idx == str.length()) {
            end = true;
            if(pass) return false; // 더 지나가는 단어 있으면 false 종료
            else return true;
        }
        //아직 안왔을 때
        else {
            int next = str.charAt(idx) - '0';
            if(child[next] == null) {
                child[next] = new Trie();
                pass = true;
            }
            return child[next].insert(str, idx+1);
        }

    }
}
```

## 그래프
- 트리와 유사하지만 사이클이 존재한다.
#

- - -

# 스택 & 큐

## 스택
- 가장 나중에 들어온 것이 가장 먼저 나오는 자료구조 (LIFO)

### 언제 사용?
- 함수의 콜스택
- 문자열 역순 출력
- 연산자 후위표기법

## 큐
- 가장 먼저 들어온 것이 가장 먼저 나오는 자료구조 (FIFO)

### 언제 사용?
- 버퍼
- BFS
#

- - -

# 힙
- 완전 이진 트리의 일종

