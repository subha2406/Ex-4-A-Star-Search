<h1>ExpNo 4 : Implement A* search algorithm for a Graph</h1> 
<h3>Name:Subha shree U    </h3>
<h3>Register Number: 2305002025        </h3>
<H3>Aim:</H3>
<p>To ImplementA * Search algorithm for a Graph using Python 3.</p>
<H3>Algorithm:</H3>


// A* Search Algorithm
1. Initialize:

* open_set = {start}, g[start] = 0, parents[start] = None.

2. While open_set not empty:
   
*  Pick node n with lowest f(n) = g[n] + H[n].
* If n is goal → reconstruct and return path
* Compute cost g[n] + weight.
* If better, update g[m], parents[m], add m to open_set.

4. If loop ends without reaching goal → path doesn’t exist.

## PROGRAM
```python
graph, H = {}, {}
def AStar(start, goal):
    open_set, g, parents = [start], {start:0}, {start:None}
    while open_set:
        n = min(open_set, key=lambda x: g[x]+H[x])
        if n==goal:
            path=[]
            while n: path.append(n); n=parents[n]
            print("Path found:", path[::-1]); return
        open_set.remove(n)
        for m,w in graph.get(n,[]):
            cost=g[n]+w
            if m not in g or cost<g[m]:
                g[m]=cost; parents[m]=n
                if m not in open_set: open_set.append(m)
    print("Path does not exist!")
n,e=map(int,input().split())
for _ in range(e):
    u,v,w=input().split(); w=int(w)
    graph.setdefault(u,[]).append((v,w))
    graph.setdefault(v,[]).append((u,w))
for _ in range(n):
    node,h=input().split(); H[node]=int(h)
AStar(input(),input())

```

## GRAPH 

<img width="1036" height="625" alt="image" src="https://github.com/user-attachments/assets/89da85ca-32ed-484e-8d12-b7515a2b8273" />


## INPUT

10 14<Br>
A B 6<Br>
A F 3<Br>
B D 2<Br>
B C 3<Br>
C D 1<Br>
C E 5<Br>
D E 8<Br>
E I 5<Br>
E J 5<Br>
F G 1<Br>
G I 3<Br>
I J 3<Br>
F H 7<Br>
I H 2<Br>
A 10<Br>
B 8<Br>
C 5<Br>
D 7<Br>
E 3<Br>
F 6<Br>
G 5<Br>
H 3<Br>
I 1<Br>
J 0<Br>
A<Br>
J<Br>

## OUTPUT
<hr>
<img width="617" height="764" alt="image" src="https://github.com/user-attachments/assets/795ca38c-8f17-4266-bdc7-1001d9f11527" />

<hr>

## RESULT:
The program successfully implements the A* Search Algorithm and finds the shortest path from the given start node to the goal node

