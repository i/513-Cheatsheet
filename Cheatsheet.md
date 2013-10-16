Master Theorem
  * takes on the form of T(n) = a T(n/b) + f(n)
  * n is the original input size (size of the problem)
  * a is the number of recursive calls (number of subproblems in the recursion)
  * n/b is the size of each subproblem (assumed to be the same size)
  * f(n) is the cost of the work done for the current problem (outside recrusive calls)
  * there are three cases to account for:
    * Case 1:  f(n) = theta(n^c). where c < log_b(a)
        T(n) = theta(n^(log_b(a)))
    * Case 2:  f(n) = theta(n^c log^(k)(n))
        T(n) = theta(n^c log^(k+1)(n))
    * Case 3:  f(n) = theta(n^c) where c > log_b(a)
        T(n) = theta(f(n))

Amortized Analysis:
  * given a sequence of operations (x_1, ..., x_n), the amortized cost of the
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
  * Every node has <k,h> pair k=tree order for k, random heap value for h
  * Maintains tree order and heap order.
  * Insert(<k,h>) into treap
  * If there are no repeated values, the treap is unique
  * Expected depth of n-node treap is D(n) <= c*log n

Comparison Sorts:
  * Examples
    - Mergesort, bubblesort, qsort, library sort, insertion sort, etc.
  * Not examples
    - Radix sort, bucket sort, vEB sort, counting sort

Decision tree (in general):
  * binary
  * not-necessarily balanced
  * worst-case of algorithm >= depth of deepest node (depth only counts comparisons)
  * avg-case of algorithm >= average depth of leaves (if all leaves equally likely)
  * each leaf is a distinct output of the algorithm
    - assuming no two keys are equal
      + then number of leaves is n!
      + output tells you the order of the input
  * number of nodes is >= 2n!-1
  * worst-case for algorithm A >= depth of DT for A >= depth of shallowest tree with n! leaves

Rank problem:
  Rank(array A, int x):
    return k, if there are k elements less than x in A
  Decision tree has n + 1 leaves, so lower bound is Omega(log n)

Van Emde Boas tree:
  Uses associate array with m-bit integer keys
  * Space  O(n)
  * Search O(log log n)
  * Insert O(log log n)
  * Delete O(log log n)
