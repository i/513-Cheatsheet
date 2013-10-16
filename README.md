Master Theorem
  * takes on the form of T(n) = a T(n/b) + f(n)
  * n is the original input size (size of the problem)
  * a is the number of recursive calls (number of subproblems in the recursion)
  * n/b is the size of each subproblem (assumed to be the same size)
  * f(n) is the cost of the work done for the current problem (outside recrusive calls)
  * there are three cases to account for:
    * Case 1:  f(n) = theta(n<sup>c</sup>). where c < log<sub>b</sub>(a)
        T(n) = theta(n<sup>log_b(a)</sup>)
    * Case 2:  f(n) = theta(n<sup>c</sup> log<sup>k</sup>(n))
        T(n) = theta(n<sup>c</sup> log<sup>k+1</sup>(n))
    * Case 3:  f(n) = theta(n<sup>c</sup>) where c > log<sub>b</sub>(a)
        T(n) = theta(f(n))

Amortized Analysis:
  * given a sequence of operations (x<sub>1</sub>, ..., x<sub>n</sub>), the amortized cost of the
    operations is the average
    the amortized cost of an algorithm is the maximum worst case

Weight-balanced search tree:
  * weight of a child is defined as all the nodes in the child-rooted subtree
  * balanced when this rule is satisfied:
      weight of heavier child is no more than twice the weight of lighter child
  * when not balanced:
      - rebuild tree from scratch. worst case O(n)
      - amortized cost of an insertion is O(log n) - it takes at least (n/2) + 1
        insertions for a balanced tree to become unbalanced

Treap (tree + heap):
  * Probalistic data structure
  * Average: Space O(n), Search O(log n), ins, del same
  * Worst: Space O(n), Search amortized O(log n), ins, del, same
  * Every node has < k, h > pair k=tree order for k, random heap value for h
  * Maintains tree order and heap order.
  * Insert(< k, h >) into treap
  * If there are no repeated values, the treap is unique
  * Expected depth of n-node treap is D(n) <= c * log n.

Comparison Sorts:
  * Examples : Mergesort, bubblesort, qsort, library sort, insertion sort, etc.
  * Not examples : Radix sort, bucket sort, vEB sort, counting sort

Decision tree (in general):
  * binary, not-necessarily balanced,  worst-case of algorithm >= depth of deepest node (depth only counts comparisons)
  * avg-case of algorithm >= average depth of leaves (if all leaves equally likely)
  * each leaf is a distinct output of the algorithm
    - assuming no two keys are equal,  then number of leaves is n! , output tells you the order of the input
  * number of nodes is >= 2n!-1
  * worst-case for algorithm A >= depth of DT for A >= depth of shallowest tree with n! leaves
  * has n + 1 leaves -> lower bound is Omega(log n). same for avg case

Rank problem:
  Rank(array A, int x) -> return k, if there are k elements less than x in A
  Decision tree has n + 1 leaves, so lower bound is Omega(log n)

Range min query:
 * RMQ in an array is the LCA in its cartesian tree
 * cartesian tree (array) => binary tree where in order traversal = array
   - build tree from left to right


Stable sorting - A sorting algorithm is stable if two entries of the same value do not change order

Bin sort:
  * sort n integers in range [m]
  * O(n + m)


Radix sort:
  * Works if sorting n k-digit numbers in base b
  * Running time: O(k(n + b))

Euler tour:<br>
  * Go to every node 
  <img src="http://upload.wikimedia.org/wikipedia/commons/thumb/1/14/Stirling_permutation_Euler_tour.svg/240px-Stirling_permutation_Euler_tour.svg.png">

LCA(u, v) "Least Common Ancestor":
  * Return the least common ancestor of nodes u and v in tree T.
  * Do Euler tour
  * TODO


  
Van Emde Boas tree:
  <img src="http://upload.wikimedia.org/wikipedia/commons/6/6b/VebDiagram.svg" width="50%">
  Uses associate array with m-bit integer keys
  * Space  O(n)
  * Search O(log log n)
  * Insert O(log log n)
  * Delete O(log log n)
Deletion van emde boas:
```
function Delete(T, x)
    if T.min == T.max == x then
        T.min = M
        T.max = -1
        return
    if x == T.min then
        if T.aux is empty then
            T.min = T.max
            return
        else
            x = T.children[T.aux.min].min
            T.min = x
    if x == T.max then
        if T.aux is empty then
            T.max = T.min
            return
        else
            T.max = T.children[T.aux.max].max
    if T.aux is empty then
        return
    i = floor(x / )
    Delete(T.children[i], x % )
    if T.children[i] is empty then
        Delete(T.aux, i)
end
```
Level ancestor problem - LA(node n, level l) -> returns n's ancestor at level l:
  * pointers: point to ancestor with depths that are powers of 2 less than your depth [O(nlogn), O(nlogn)]
  * Home path - 
  * Path decomposition (long path) - double long path - twice the size with ancestors above.
  
Useful?:
  * a = bc  <->  logb(a) = c ;; a = blogb(a) ;; logc(ab) = logc(a) + logc(b) ;; logb(a) = logc(a)/logc(b)
  * logb(1/a) = -logb(a) ;; logb(a) = 1/loga(b) ;; alogb(c) = clogb(a) ;;
  * sum(i=1 to k) { i(i+1) } = 1/3 (k+1)(k+2) ;; sum(i=1 to k) { i } = 1/2 k(k+1)) ;;
  * sum(i=0 to k) { i * 2<sup>i</sup> = (k - 1) * 2<sup>k + 1</sup> + 2
