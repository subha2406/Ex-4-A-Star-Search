<h1>ExpNo 4 : Implement A* search algorithm for a Graph</h1> 
<h3>Name: Subha Shree U      </h3>
<h3>Register Number: 2305002025          </h3>
<H3>Aim:</H3>
<p>To Implement A * Search algorithm for a Graph using Python 3.</p>
<H3>Algorithm:</H3>


 1. Initialize

       - Open list ← priority queue (min-heap)

       - Closed list ← empty set

       - Insert the start node into the open list with:

           - g = 0

           - h = heuristic(start)

           - f = g + h

2. While Open list is not empty:
   
      - Remove the node q with the lowest f from the open list.
   
      - If q is the goal node, return the path (reconstruct from parents).
   
      - If q is already in the Closed list, skip it.
   
      - Add q to the Closed list.

3. For each neighbor n of q:

      - Compute:

           - g(n) = g(q) + cost(q, n)

           - h(n) = heuristic(n)

           - f(n) = g(n) + h(n)

     - If n is not in Closed list:

       - Insert (f(n), g(n), n, path_so_far) into Open list.

4. If goal is never reached and Open list becomes empty:

    - Return "No path found".

## PROGRAM
```python

import heapq

def astar(g,s,t,h):
    q=[(h[s],0,s,[])]
    v=set()
    while q:
        f,gc,u,p=heapq.heappop(q)
        if u==t: return p+[u]
        if u in v: continue
        v.add(u)
        for x,c in g.get(u,[]): 
            if x not in v: heapq.heappush(q,(gc+c+h.get(x,0),gc+c,x,p+[u]))
    return None

g={}
print("Input edges as: node1 node2 cost (type 'done' when finished):")
while (e:=input())!="done":
    u,v,c=e.split();g.setdefault(u,[]).append((v,int(c)))

h={u:int(input(f"Heuristic for {u}: ")) for u in g}
s=input("Start node: ");t=input("Goal node: ")
print("Path:",astar(g,s,t,h) or "No path found")

```

## GRAPH 
<img width="369" height="402" alt="image" src="https://github.com/user-attachments/assets/183400db-1769-448c-9feb-cb1ff61c3b97" />




## INPUT
A B 3

A D 5

B C 4

C E 6

D F 1

E F 2

## OUTPUT

<img width="991" height="673" alt="image" src="https://github.com/user-attachments/assets/6184e746-2656-47f3-8942-5ff112523b79" />



## RESULT

Thus, the program successfully finds the shortest path from the start node to the goal node using the A* algorithm.
