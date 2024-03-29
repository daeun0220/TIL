# Dijkstra

다익스트라 알고리즘은 가중치 그래프에서 시작점과 도착점이 주어졌을 때, 최단 경로를 반환하는 알고리즘이다


1. 우선순위큐에 시작점 노드 추가 ex) (가중치, 위치) (0,1)
2. 우선순위가 가장 높은 노드 추출
3. 방문여부 확인
   * 이미 방문했다면 최소 비용이 아님으로 다음 노드 추출한다
4. 비용 업데이트
5. 현재 노드와 연결된 노드 우선순위큐에 추가  
6. 우선순위큐가 빈 후, 도착점에 기록된 비용 반환


<p align="center"><img src="../Images/Algorithm/DijkstraCode.png" width=60% height=20%></p>

### 코드

```python
def dijkstra(graph, start, final) :
   costs = {}
   pq = []
   heapq.heappush(pq, (0, start))

   while pq :
      cur_cost, cur_v = heapq.heappop(pq)
      if cur_v not in costs :
         costs[cur_v] = cur_cost
         for cost, next_v in graph[cur_v] :
            next_cost = cur_cost + cost
            heapq.heappush(pq,(next_cost, next_v))

   return costs[final]   
```

