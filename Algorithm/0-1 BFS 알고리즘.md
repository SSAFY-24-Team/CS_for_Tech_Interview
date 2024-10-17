![img.png](/img/0-1%20BFS%20알고리즘/img.png)
# 0-1 BFS (0-1 Breadth First Search) 알고리즘
> 💡 0-1 BFS는 특정 상황의 그래프에서 최단 경로를 찾을 때 사용된다.
- 가중치가 0과 1로 이루어진 그래프에서 최단 경로를 찾을 때 사용한다.
- 최단 경로를 구할 때 많이 사용하는 우선순위 큐 다익스트라(Dikjstra) 알고리즘은 시간 복잡도가 O(E log V)인 반면에, 0-1 BFS는 일반적인 BFS 시간 복잡도와 같이 O(V + E)의 선형 시간 복잡도를 갖는다.
- 일반 BFS 에서 큐를 사용하는 것과 달리 덱(Deque)을 사용한다.


## 🚀 0-1 BFS의 동작 과정
1. 덱의 front에서 현재 방문한 노드를 꺼낸다.
2. 연결된 인접 노드를 살펴본다.
3. (현재 비용+ 다음 노드 가중치) < (다음 노드에 기록된 비용)이라면, 다음 노드에 기록된 비용을 갱신해 준다.
4. 노드가 갱신될 때, 가중치가 0이라면 덱의 front, 가중치가 1이라면 덱의 back에 삽입한다.
5. 덱에 노드가 남지 않을 때까지 위 과정을 반복한다.

![img_1.png](/img/0-1%20BFS%20알고리즘/img_1.png)

## 🚀 시간 복잡도 O(V + E) 이유
> 노드의 수 : V / 간선의 수 : E
- 모든 정점을 최단 거리로 방문해 1번씩만 방문하므로 덱의 최대 크기는 최대 V이다 : O(V)
- 비용이 적은 경로부터 차례대로 탐색하게 되기 때문에, 모든 간선을 1번씩만 지나가게 된다 : O(E)
- 덱을 사용하며 앞 뒤 정점을 추가하거나 제거할 때 상수 시간이 소요된다 : O(V)
- 상수시간은 시간 복잡도에 영향을 주지 않으므로 0-1 BFS의 시간 복잡도는 O(V + E)이다.

## 🚀 0-1 BFS의 핵심코드
백준 1261번 문제의 0-1 BFS 풀이 코드이다.  
0-1 BFS는 기본 BFS와 코드가 같지만, 적절히 활용하는게 더 중요하다.

```java
import java.io.*;
import java.util.ArrayDeque;
import java.util.Deque;
import java.util.StringTokenizer;

public class Main {
    public static void main(String[] args) throws IOException {
        // Input
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));
        StringTokenizer st = new StringTokenizer(br.readLine());

        int M = Integer.parseInt(st.nextToken());
        int N = Integer.parseInt(st.nextToken());

        int[][] map = new int[N][M]; // 맵 정보

        for (int i = 0; i < N; i++) {

            char[] chars = br.readLine().toCharArray();

            for (int j = 0; j < M; j++) {
                map[i][j] = Character.getNumericValue(chars[j]);
            }
        }

        // 0-1 BFS
        int[] dx = {-1, 0, 1, 0};
        int[] dy = {0, 1, 0, -1};

        Deque<AOJ> dq = new ArrayDeque<>();
        dq.addFirst(new AOJ(0, 0, 0));

        while (!dq.isEmpty()) {
            AOJ aoj = dq.pollFirst();

            if (aoj.row == N - 1 && aoj.col == M - 1) { // Output
                bw.write(Integer.toString(aoj.broken));
                bw.flush();
                break;
            } else {
                for (int i = 0; i < 4; i++) {
                    int r = aoj.row + dx[i];
                    int c = aoj.col + dy[i];
                    if (0 <= r && r < N && 0 <= c && c < M) {
                        if (map[r][c] == 0) {
                            dq.addFirst(new AOJ(r, c, aoj.broken));
                        } else if (map[r][c] == 1) {
                            dq.addLast(new AOJ(r, c, aoj.broken + 1));
                        }
                        map[r][c] = -1; // 방문체크
                    }
                }
            }
        }
    }

    public static class AOJ {
        int row, col, broken;

        public AOJ(int row, int col, int broken) {
            this.row = row;
            this.col = col;
            this.broken = broken;
        }
    }
}
```

## 예제 질문
### 0-1 BFS (0-1 Breadth First Search) 알고리즘에 대해 설명하시오.

<details>
   <summary> 예비 답안 보기 (👈 Click)</summary>
<br />

0-1 BFS는 가중치가 0과 1로만 이루어진 그래프에서 최단 경로를 찾을 때 사용하는 알고리즘이다. 일반적인 다익스트라 알고리즘보다 시간 복잡도가 더 낮은 O(V + E)를 가지며, 덱(Deque)을 사용해 가중치에 따라 덱의 앞(front) 또는 뒤(back)에 노드를 삽입하는 방식으로 동작한다. 덱의 front에서 가중치가 0인 경우는 앞에, 1인 경우는 뒤에 노드를 추가함으로써 최단 경로를 찾아간다.

</details>

### 0-1 BFS와 다익스트라 알고리즘의 차이점을 설명해보세요.

<details>
   <summary> 예비 답안 보기 (👈 Click)</summary>
<br />

1. **가중치의 특성**:
    - 0-1 BFS는 가중치가 0과 1로만 이루어진 그래프에서 사용되며, 덱(Deque)을 통해 가중치가 0인 노드를 덱의 앞에, 가중치가 1인 노드를 뒤에 삽입한다.
    - 다익스트라는 가중치가 다양한 그래프에서도 적용 가능하며, 우선순위 큐를 사용해 최소 거리를 가지는 노드를 먼저 탐색한다.

2. **시간 복잡도**:
    - 0-1 BFS는 BFS와 유사하게 O(V + E)의 시간 복잡도를 가지며, 덱을 사용하여 선형 시간 내에 최단 거리를 탐색한다.
    - 다익스트라는 우선순위 큐를 사용해 O(E log V)의 시간 복잡도를 가지며, 작은 가중치로 경로를 탐색하는 데 유리하다.

3. **사용하는 자료구조**:
    - 0-1 BFS는 덱(Deque)을 사용하여 가중치에 따라 노드를 추가하며, 경로의 가중치가 작을수록 덱의 앞쪽에서 처리한다.
    - 다익스트라는 우선순위 큐(Priority Queue)를 사용해 가장 최단 거리에 있는 노드를 우선적으로 처리한다.

</details>


## 레퍼런스
- 수민 포스팅 : https://soooom.tistory.com/480