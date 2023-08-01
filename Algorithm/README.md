# 알고리즘

- [슬라이딩 윈도우](#슬라이딩-윈도우)
- 투 포인터
- BFS / DFS
- 백트래킹
- 트리
- DP
- 재귀
- 순열
- 조합

## 슬라이딩 윈도우

* 문제 예시 : https://www.acmicpc.net/problem/21921
고정 사이즈의 윈도우가 이동하면서 윈도우 내에 있는 데이터를 이용해 문제를 풀이하는 알고리즘을 말한다. 배열이나 리스트의 요소의 일정 범위의 값을 비교할 때 사용하면 매우 유용하다. 원래 네트워크에서 사용되던 알고리즘을 문제풀이에 응용한 경우이다. 배열이나 리스트의 요소를 슬라이딩 윈도우를 사용하지 않고 단순히 값을 비교하면 배열이나 리스트의 크기, 비교해야 하는 일정 범위가 커지면 커질 수록 시간복잡도가 굉장히 커지게 된다. 이러한 경우에 시간복잡도를 줄이기 위해 사용할 수 있다. 한 칸씩 이동하기 때문에 공통된 부분은 유지하고 처음과 끝 원소만 갱신하며 비교할 수 있다.

https://soeasyalgo.tistory.com/49

## 순열
- 순열
  
  1, 2, 3, 4, 5 중에서 순서를 생각하여 3개를 뽑는다. 1, 2, 3과 1, 3, 2를 다르게 생각한다.
  ```
  private static void makePermutation(int r, int[] temp, int current, boolean[] visited) {
		if (r == current) {
			System.out.println(Arrays.toString(temp));
		} else {
			for (int i = 0; i < arr.length; i++) {
				if (!visited[i]) {
					visited[i] = true;
					temp[current] = arr[i];
					makePermutation(r, temp, current +1, visited);
					visited[i] = false;
				}
			}
		}
	}
  ```
  - r : 뽑고자 하는 개수
  - temp : r개를 뽑는 결과를 저장하는 배열
  - current : 현재 개수를 저장해놓은 값
  - visited : 방문 여부 확인 배열
- 중복순열

  순서를 고려해서 중복을 포함한 3개를 뽑는 것이다. 1, 2, 1과 2, 1, 1을 다르게 생각한다
  ```
  private static void makeOverlabPermutation(int r, int[] temp, int current) {
		if (r == current) {
			System.out.println(Arrays.toString(temp));
		} else {
			for (int i = 0; i < arr.length; i++) {
				temp[current] = arr[i];
				makeOverlabPermutation(r, temp, current + 1);
			}
		}
	}
  ```
    - r : 뽑고자 하는 개수
  - temp : r개를 뽑는 결과를 저장하는 배열
  - current : 현재 개수를 저장해놓은 값
  - visited : 방문 여부 확인 배열

## BFS
너비 우선 탐색은 맹목적 탐색 방법의 하나로 시작 정점을 방문한 후 시작 정점에 인접한 모든 정점들을 우선 방문하는 방법이다. 더 이상 방문하지 않은 정점이 없을 때까지 방문하지 않은 모든 정점들에 대해서도 너비 우선 검색을 적용한다. 

* 루트 노드(혹은 다른 임의의 노드)에서 시작해서 인접한 노드를 먼저 탐색하는 방법
* 사용하는 경우: 두 노드 사이의 최단 경로 혹은 임의의 경로를 찾고 싶을 때 이 방법을 선택한다.

- BFS는 시작 정점으로부터 거리가 가까운 정점의 순서로 탐색한다. (거리 1부터 2, 3 순서대로)
- 그래프 탐색의 경우 어떤 노드를 방문했었는지 여부를 반드시 검사해야 한다. (이를 검사하지 않을 경우 무한루프에 빠질 위험이 있다.)
- BFS는 재귀적으로 동작하지 않는다.
- BFS는 방문한 노드들을 차례로 저장한 후 꺼낼 수 있는 자료 구조인 큐(Queue)를 사용한다.
- 즉, 선입선출(FIFO) 원칙으로 탐색
- 일반적으로 큐를 이용해서 반복적 형태로 구현하는 것이 가장 잘 동작한다.
