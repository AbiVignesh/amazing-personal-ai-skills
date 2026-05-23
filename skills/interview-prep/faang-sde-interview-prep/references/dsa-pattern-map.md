# DSA Pattern Map

Master patterns, not random problems. Each pattern is a template for solving 20+ similar problems.

---

## Pattern Learning Philosophy

When you master a pattern, you can recognize and solve any variant. Instead of memorizing solutions, understand:
1. **When to use it** — What problem characteristics trigger this pattern?
2. **Why it works** — What's the intuition?
3. **Implementation** — Code template
4. **Variants** — How does it change for different problems?

---

## Core Patterns

### 1. Sliding Window

**Intuition:** Maintain a window of elements that satisfy a condition. Expand right, contract left.

**When to use:**
- Contiguous subarray/substring problems
- "Maximum/minimum in all subarrays of size k"
- "Longest substring without repeating characters"
- "Find all anagrams in string"

**Template:**
```python
def sliding_window(arr, k):
    window = {}
    left = 0
    result = 0
    
    for right in range(len(arr)):
        # Add arr[right] to window
        window[arr[right]] = window.get(arr[right], 0) + 1
        
        # Shrink from left if needed
        while condition_not_met(window):
            window[arr[left]] -= 1
            if window[arr[left]] == 0:
                del window[arr[left]]
            left += 1
        
        # Update result
        result = max(result, right - left + 1)
    
    return result
```

**Problems:**
- Easy: Max consecutive ones (with one flip allowed)
- Medium: LRU cache, Longest substring without repeating
- Hard: Minimum window substring

**Complexity:** O(n) time, O(k) space

---

### 2. Two Pointers

**Intuition:** Use two pointers to solve problems in one pass. Pointers move in opposite or same directions.

**When to use:**
- Sorted array problems
- "Remove duplicates", "Two sum", "Container with most water"
- Partition problems

**Template:**
```python
def two_pointers(arr):
    left, right = 0, len(arr) - 1
    
    while left < right:
        if condition(arr[left], arr[right]):
            # Process or move
            left += 1
        else:
            right -= 1
    
    return result
```

**Problems:**
- Easy: Two sum (sorted), Valid palindrome
- Medium: Container with most water, 3Sum
- Hard: Trapping rain water

**Complexity:** O(n) time, O(1) space

---

### 3. Fast & Slow Pointers

**Intuition:** Move at different speeds to detect cycles or find midpoints.

**When to use:**
- Cycle detection in linked lists
- Finding middle of linked list
- Palindrome checking
- Happy number detection

**Template:**
```python
def fast_slow(head):
    slow = fast = head
    
    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next
        
        if slow == fast:  # Cycle detected
            return True
    
    return False
```

**Problems:**
- Easy: Linked list cycle, Middle of linked list
- Medium: Palindrome linked list
- Hard: Intersection point in linked lists

**Complexity:** O(n) time, O(1) space

---

### 4. Merge Intervals

**Intuition:** Sort by start point, then merge overlapping intervals by comparing end points.

**When to use:**
- Overlapping interval problems
- "Merge intervals", "Insert interval"
- "Employee free time", "Calendar events"

**Template:**
```python
def merge_intervals(intervals):
    if not intervals:
        return []
    
    intervals.sort()
    result = [intervals[0]]
    
    for current in intervals[1:]:
        last = result[-1]
        if current[0] <= last[1]:
            result[-1] = (last[0], max(last[1], current[1]))
        else:
            result.append(current)
    
    return result
```

**Problems:**
- Easy: Merge intervals, Insert interval
- Medium: Meeting rooms, Employee free time
- Hard: Interval list intersections

**Complexity:** O(n log n) time, O(n) space

---

### 5. Cyclic Sort

**Intuition:** For problems with numbers in range [1, n], place each number at its correct index.

**When to use:**
- Numbers in range [1, n]
- "Find missing number", "Find duplicate", "First missing positive"

**Template:**
```python
def cyclic_sort(nums):
    i = 0
    while i < len(nums):
        correct_idx = nums[i] - 1
        if nums[i] > 0 and nums[i] <= len(nums) and nums[i] != nums[correct_idx]:
            nums[i], nums[correct_idx] = nums[correct_idx], nums[i]
        else:
            i += 1
    
    return nums
```

**Problems:**
- Easy: Find missing number, Find duplicate
- Medium: First missing positive
- Hard: Array of duplicate numbers

**Complexity:** O(n) time, O(1) space

---

### 6. In-place Reversal

**Intuition:** Reverse linked lists or arrays in place without extra space.

**When to use:**
- Linked list reversal
- "Reverse between indices", "Reverse k groups"
- Palindrome problems

**Template:**
```python
def reverse_linked_list(head):
    prev, curr = None, head
    
    while curr:
        # Store next node
        next_temp = curr.next
        # Reverse the link
        curr.next = prev
        # Move forward
        prev = curr
        curr = next_temp
    
    return prev
```

**Problems:**
- Easy: Reverse linked list
- Medium: Reverse linked list between positions
- Hard: Reverse nodes in k-groups

**Complexity:** O(n) time, O(1) space

---

### 7. Tree BFS (Level Order)

**Intuition:** Process tree level by level using a queue.

**When to use:**
- Level order traversal
- "Binary tree level order", "Minimum depth"
- "Vertical order", "Connect nodes at same level"

**Template:**
```python
def bfs_tree(root):
    if not root:
        return []
    
    result = []
    queue = deque([root])
    
    while queue:
        level_size = len(queue)
        level = []
        
        for _ in range(level_size):
            node = queue.popleft()
            level.append(node.val)
            
            if node.left:
                queue.append(node.left)
            if node.right:
                queue.append(node.right)
        
        result.append(level)
    
    return result
```

**Problems:**
- Easy: Binary tree level order, Minimum depth
- Medium: Vertical order, Right view of tree
- Hard: Binary tree maximum path sum

**Complexity:** O(n) time, O(w) space (w = max width)

---

### 8. Tree DFS (In/Pre/Post Order)

**Intuition:** Traverse tree using recursion. Order matters: inorder (left-root-right), preorder (root-left-right), postorder (left-right-root).

**When to use:**
- Any tree traversal
- "Validate BST", "Path sum", "Serialize tree"
- Building trees, recovering paths

**Template:**
```python
def dfs_tree(root):
    if not root:
        return
    
    # Preorder: process root first
    process(root)
    
    # Inorder: process root in middle
    dfs_tree(root.left)
    process(root)
    dfs_tree(root.right)
    
    # Postorder: process root last
    dfs_tree(root.left)
    dfs_tree(root.right)
    process(root)
```

**Problems:**
- Easy: Inorder traversal, Path sum
- Medium: Validate BST, Path sum II
- Hard: Serialize/deserialize tree

**Complexity:** O(n) time, O(h) space (h = height)

---

### 9. Graph BFS

**Intuition:** Explore graph level by level. Find shortest path in unweighted graphs.

**When to use:**
- Shortest path in unweighted graph
- "Number of islands", "Rotten oranges"
- Connected components, bipartite check

**Template:**
```python
def bfs_graph(graph, start):
    visited = set([start])
    queue = deque([start])
    
    while queue:
        node = queue.popleft()
        
        for neighbor in graph[node]:
            if neighbor not in visited:
                visited.add(neighbor)
                queue.append(neighbor)
    
    return visited
```

**Problems:**
- Easy: Number of islands, Rotten oranges
- Medium: Word ladder, Clone graph
- Hard: All paths in DAG

**Complexity:** O(V + E) time, O(V) space

---

### 10. Graph DFS

**Intuition:** Explore graph deeply. Useful for cycles, connectivity, topological sort.

**When to use:**
- Cycle detection, Topological sort
- All paths, Connected components
- Strongly connected components

**Template:**
```python
def dfs_graph(graph, node, visited):
    visited.add(node)
    
    for neighbor in graph[node]:
        if neighbor not in visited:
            dfs_graph(graph, neighbor, visited)
```

**Problems:**
- Easy: Number of connected components
- Medium: Evaluate division, Detect cycle
- Hard: Alien dictionary, Critical connections

**Complexity:** O(V + E) time, O(V) space

---

### 11. Dynamic Programming

**Intuition:** Break problem into overlapping subproblems. Use memoization or tabulation to avoid recomputation.

**When to use:**
- Optimization problems (max/min)
- Counting problems
- "Coin change", "Longest increasing subsequence", "Knapsack"

**Template:**
```python
# Memoization (Top-down)
def dp_memo(n, memo={}):
    if n in memo:
        return memo[n]
    
    if n <= 1:
        return n
    
    memo[n] = dp_memo(n-1, memo) + dp_memo(n-2, memo)
    return memo[n]

# Tabulation (Bottom-up)
def dp_tab(n):
    dp = [0] * (n + 1)
    dp[1] = 1
    
    for i in range(2, n + 1):
        dp[i] = dp[i-1] + dp[i-2]
    
    return dp[n]
```

**Problems:**
- Easy: Climbing stairs, House robber
- Medium: Coin change, Longest increasing subsequence
- Hard: Burst balloons, Edit distance

**Complexity:** Varies, usually O(n*m) time

---

### 12. Backtracking

**Intuition:** Explore all possible solutions by building incrementally and pruning invalid paths.

**When to use:**
- Permutations, combinations
- "N-Queens", "Sudoku solver", "Word search"
- Path finding with constraints

**Template:**
```python
def backtrack(path, candidates):
    if is_solution(path):
        result.append(path[:])
        return
    
    for i, candidate in enumerate(candidates):
        # Choose
        path.append(candidate)
        # Explore
        backtrack(path, candidates[i+1:])
        # Unchoose
        path.pop()
```

**Problems:**
- Easy: Permutations, Combinations
- Medium: N-Queens, Sudoku solver
- Hard: Word search II

**Complexity:** O(branching^depth), varies

---

### 13. Greedy

**Intuition:** Make locally optimal choices hoping to find global optimum. Requires proof that greedy choice is safe.

**When to use:**
- Activity selection, Huffman coding
- "Jump game", "Gas station", "Interval scheduling"

**Template:**
```python
def greedy(arr):
    # Sort or order by greedy criterion
    arr.sort(key=greedy_criterion)
    
    result = 0
    for item in arr:
        # Check if we can include this item
        if can_include(item):
            result += item
    
    return result
```

**Problems:**
- Easy: Jump game, Best time to buy/sell stock
- Medium: Gas station, Jump game II
- Hard: Rearrange string k distance apart

**Complexity:** Usually O(n log n) or O(n)

---

### 14. Bit Manipulation

**Intuition:** Solve problems using bit operations. Powers of 2, XOR properties, bit shifting.

**When to use:**
- "Single number", "Power of two"
- Hamming distance, Number of 1 bits
- Subset generation

**Template:**
```python
# Check if bit is set
if num & (1 << i):  # i-th bit is set

# Set i-th bit
num |= (1 << i)

# Clear i-th bit
num &= ~(1 << i)

# Toggle i-th bit
num ^= (1 << i)

# Check if power of 2
if num & (num - 1) == 0:
```

**Problems:**
- Easy: Single number, Hamming distance
- Medium: Number of 1 bits, Maximum product
- Hard: Reverse integer

**Complexity:** O(log n) or O(1)

---

### 15. Math & Geometry

**Intuition:** Recognize mathematical properties and geometric relationships.

**When to use:**
- GCD, LCM, primes
- Coordinate geometry, overlapping rectangles
- Modular arithmetic

**Key Algorithms:**
- Euclidean algorithm for GCD
- Sieve of Eratosthenes for primes
- Coordinate geometry formulas

**Problems:**
- Easy: Pow(x, n), Palindrome number
- Medium: Fraction to repeating decimal, Rectangle overlap
- Hard: Trapping rain water, Skyline problem

---

## Learning Progression

**Week 1-2 (Foundations):**
1. Sliding window
2. Two pointers
3. Fast & slow pointers

**Week 3 (Data Structures):**
4. Merge intervals
5. Cyclic sort
6. In-place reversal

**Week 4-5 (Trees & Graphs):**
7. Tree BFS
8. Tree DFS
9. Graph BFS
10. Graph DFS

**Week 6-8 (Advanced):**
11. Dynamic programming
12. Backtracking
13. Greedy
14. Bit manipulation
15. Math & geometry

---

## Problem Solving Approach

For any problem:

1. **Identify the pattern** — What data structure? What operation?
2. **Find the template** — Which pattern matches?
3. **Adapt the template** — What needs to change?
4. **Code it** — Follow the adapted template
5. **Optimize** — Can you reduce time/space?
6. **Verify** — Test edge cases

---

## Common Pitfalls by Pattern

| Pattern | Pitfall | Fix |
|---------|---------|-----|
| Sliding window | Pointer goes out of bounds | Check bounds in while condition |
| Two pointers | Wrong initial state | Verify pointer positions before loop |
| BFS | Forgetting to mark visited | Add to visited when enqueueing |
| DFS | Stack overflow | Use iterative DFS for large graphs |
| DP | Overlapping states not memoized | Always check memo before computing |
| Backtracking | Not undoing choices | Always undo in same order as choices |
| Greedy | Not proving greedy is safe | Trace through counterexamples |

