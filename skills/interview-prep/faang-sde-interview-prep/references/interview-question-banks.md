# Interview Question Banks

Realistic FAANG questions organized by difficulty and pattern. Not random dumps—curated for learning.

---

## Easy DSA Problems (Warm-up, 15-20 min)

These are interview warm-ups. Should solve in 10-15 min to build confidence.

### Sliding Window / Arrays
1. **Two Sum** - Find two numbers that add to target
   - Pattern: Hash map or two pointers
   - Variants: Two sum sorted, two sum unique, k-sum

2. **Majority Element** - Find element appearing >n/2 times
   - Pattern: Hash map or Boyer-Moore voting
   - Follow-up: What if >n/3? >n/k?

3. **Merge Sorted Array** - Merge two sorted arrays
   - Pattern: Two pointers from end
   - Follow-up: In-place merge?

### Linked List
4. **Reverse Linked List** - Reverse entire linked list
   - Pattern: In-place reversal
   - Follow-up: Reverse between positions?

5. **Palindrome Linked List** - Check if linked list is palindrome
   - Pattern: Fast & slow pointers + reversal
   - Follow-up: Without modifying list?

### Trees
6. **Binary Tree Level Order** - Level-order traversal
   - Pattern: Queue + BFS
   - Follow-up: Zigzag order?

7. **Invert Binary Tree** - Mirror the tree
   - Pattern: Recursion or BFS
   - Follow-up: In-place? Iterative?

### Strings
8. **Valid Parentheses** - Check if parentheses are balanced
   - Pattern: Stack
   - Follow-up: Nested? Multiple types?

9. **Longest Common Prefix** - Find common prefix
   - Pattern: Strings, character comparison
   - Follow-up: Optimize?

### Other
10. **FizzBuzz** - Classic warm-up (not always asked, but good warm-up)
11. **Remove Duplicates** - Remove duplicates from sorted array
12. **Rotate Array** - Rotate array by k positions
13. **Best Time to Buy Stock** - Find max profit with one transaction

---

## Medium DSA Problems (Core, 35-45 min)

These are the typical interview problems. Expect 1-2 follow-ups.

### Sliding Window
1. **Longest Substring Without Repeating Characters**
   - Pattern: Sliding window + hash map
   - Follow-up: Find the substring, not just length?

2. **Minimum Window Substring**
   - Pattern: Sliding window + two pointers
   - Difficulty: Hard-medium
   - Follow-up: Multiple matches?

3. **Permutation in String**
   - Pattern: Sliding window + character count
   - Follow-up: Count all permutations?

### Two Pointers
4. **3Sum** - Find all unique triplets that sum to 0
   - Pattern: Sorting + two pointers
   - Follow-up: 4Sum? K-Sum?

5. **Container With Most Water**
   - Pattern: Two pointers, greedy
   - Follow-up: Explanation of why greedy works?

6. **Trapping Rain Water** (Hard-medium)
   - Pattern: Two pointers or dynamic programming
   - Follow-up: Can you do it in O(n) without DP?

### Trees
7. **Path Sum** - Check if tree has root-to-leaf path summing to target
   - Pattern: DFS recursion
   - Follow-up: Find the path? All paths?

8. **Lowest Common Ancestor**
   - Pattern: Tree traversal, recursion
   - Follow-up: In BST? Without parent pointers?

9. **Validate Binary Search Tree**
   - Pattern: DFS with min/max bounds
   - Follow-up: Iterative? In-order traversal?

10. **Binary Tree Right Side View**
    - Pattern: BFS or DFS
    - Follow-up: Variants (left side, top, bottom)?

### Graphs
11. **Number of Islands** - Count connected components
    - Pattern: DFS/BFS
    - Follow-up: With obstacles? Largest island size?

12. **Word Ladder** - Shortest transformation sequence
    - Pattern: BFS
    - Follow-up: Find all paths? Track path?

13. **Clone Graph**
    - Pattern: BFS/DFS with hash map
    - Follow-up: Disconnected graph?

14. **Evaluate Division**
    - Pattern: Graph building + DFS
    - Follow-up: Optimize for multiple queries?

### Dynamic Programming
15. **Longest Increasing Subsequence**
    - Pattern: DP or binary search
    - Follow-up: Actual subsequence? O(n log n) solution?

16. **Coin Change**
    - Pattern: DP bottom-up
    - Follow-up: Coin Change II (count ways)?

17. **House Robber**
    - Pattern: DP
    - Follow-up: House Robber II (circular)?

18. **Word Break**
    - Pattern: DP
    - Follow-up: Word Break II (find all)?

### Backtracking
19. **Permutations** - Generate all permutations
    - Pattern: Backtracking
    - Follow-up: Permutations II (with duplicates)?

20. **Combinations**
    - Pattern: Backtracking
    - Follow-up: Combinations Sum variants?

### Other
21. **LRU Cache** - Implement LRU cache
    - Pattern: Hash map + doubly linked list
    - Difficulty: Medium-hard
    - Follow-up: LFU cache?

22. **Merge K Sorted Lists**
    - Pattern: Heap or merge sort
    - Follow-up: Divide and conquer approach?

23. **Group Anagrams**
    - Pattern: Hash map, string sorting
    - Follow-up: Optimize space/time?

24. **Decode Ways**
    - Pattern: Dynamic programming
    - Follow-up: Count? Actual decodings?

---

## Hard DSA Problems (Differentiation, 50-60 min)

For senior roles or to stand out. 1-2 are asked in harder interview rounds.

1. **Median of Two Sorted Arrays**
   - Pattern: Binary search
   - Difficulty: Very hard
   - Follow-up: What if not sorted?

2. **Binary Tree Maximum Path Sum**
   - Pattern: DFS recursion, tricky edge cases
   - Follow-up: Between any two nodes (not just root)?

3. **LFU Cache**
   - Pattern: Hash map + priority queue + linked list
   - Difficulty: Hard
   - Follow-up: How to optimize?

4. **Regular Expression Matching**
   - Pattern: DP or recursion with memoization
   - Difficulty: Very hard

5. **Longest Valid Parentheses**
   - Pattern: DP or stack
   - Follow-up: Find the indices?

6. **Alien Dictionary**
   - Pattern: Topological sort + graph
   - Follow-up: Verify if valid? Count solutions?

7. **Edit Distance**
   - Pattern: DP 2D
   - Follow-up: Find the edits? Optimize space?

8. **Word Search II**
   - Pattern: Backtracking + Trie (optimization)
   - Difficulty: Hard

9. **Burst Balloons**
   - Pattern: DP (unusual approach needed)
   - Difficulty: Very hard

10. **Maximum Sliding Window** (Hard-medium)
    - Pattern: Deque or segment tree
    - Follow-up: All windows with max?

---

## System Design Problems (50-60 min each)

### Low-Level Design (OOP)
1. **Parking Lot** - Design a parking lot system
   - Classes: ParkingLot, ParkingSpace, Vehicle, Ticket
   - Operations: Park, unpark, search
   - Constraints: Multiple levels, handicap spaces

2. **Library Management System**
   - Classes: Book, Member, Library, Librarian
   - Operations: Borrow, return, search, reserve
   - Constraints: Multiple copies, overdue fines

3. **ATM Machine**
   - Classes: ATM, Account, Transaction, Card
   - Operations: Withdraw, deposit, balance, pin verification
   - Constraints: Cash limit, PIN security

4. **Vending Machine**
   - Classes: VendingMachine, Slot, Product, Coin
   - Operations: Select, pay, dispense
   - Constraints: Change calculation, stock

### High-Level Design
1. **Design Instagram**
   - Components: API, User service, Post service, Feed service, Notification
   - Database: Users, Posts, Follows, Likes, Comments
   - Scale: 500M DAU, 10M posts/day
   - Key challenges: Feed generation, scaling storage, notifications

2. **Design Twitter**
   - Components: Tweet service, Timeline service, Search service
   - Scale: 1B users, 500M tweets/day
   - Key challenges: Real-time feed, searching billions of tweets

3. **Design Uber**
   - Components: User service, Driver service, Trip service, Location service
   - Challenges: Real-time location, matching, surge pricing
   - Scale: Millions of daily trips

4. **Design YouTube / Netflix**
   - Components: Upload service, Encoding service, CDN, Recommendation engine
   - Challenges: Video streaming, buffering, recommendation
   - Scale: Petabytes of data, billions of views

5. **Design Amazon Store**
   - Components: Product service, Cart, Order, Inventory, Payment, Shipping
   - Scale: Millions of products, billions of transactions
   - Challenges: Inventory management, concurrency

6. **Design a Rate Limiter**
   - Algorithms: Token bucket, sliding window, leaky bucket
   - Distributed: How to rate limit across servers?
   - Use cases: API limits, DDoS protection

7. **Design a Cache System**
   - Data structures: Hash map + linked list (LRU), segment tree (write-through)
   - Eviction: LRU, LFU, TTL
   - Distributed: Consistent hashing, replication

8. **Design a Distributed Task Queue**
   - Producer-consumer with persistence
   - Retry logic, dead letter queue
   - Scale: Millions of jobs/day

9. **Design Search Autocomplete**
   - Trie structure, frequency counting
   - Distributed: How to sync across regions?
   - Personalization: User history

10. **Design a Notification System**
    - Push notifications, email, SMS
    - Real-time, reliably delivered
    - Scaling: Millions of recipients

---

## Behavioral Questions (By Category)

### Leadership & Ownership
1. "Tell me about a time you took ownership of a project"
2. "Describe a situation where you had to step up"
3. "Tell me about a time you drove change in your team"

### Technical Problem-Solving
4. "Tell me about the hardest technical problem you've solved"
5. "Describe a system you architected"
6. "Tell me about a complex bug you debugged"

### Conflict & Disagreement
7. "Tell me about a time you disagreed with your manager"
8. "Describe a time you had a conflict with a teammate"
9. "Tell me about a time you had to compromise"

### Failure & Learning
10. "Tell me about a time you failed"
11. "Describe a mistake you made and what you learned"
12. "Tell me about a time you shipped something that didn't work"

### Scaling & Growth
13. "Tell me about a system you optimized"
14. "Describe a time you made things faster/cheaper"
15. "Tell me about handling growth challenges"

### Communication & Clarity
16. "Tell me about a time you had to explain something complex"
17. "Describe a time you had to communicate bad news"
18. "Tell me about a time you gave feedback to someone"

### Ambiguity & Creativity
19. "Tell me about a time you worked with unclear requirements"
20. "Describe a time you had to be creative"
21. "Tell me about a time you had to learn something new quickly"

---

## Practice Tips

### For Easy Problems:
- Solve in 10-15 min without looking at hints
- Then code cleanly in 5 min
- Practice 1-2 per day

### For Medium Problems:
- First: Solve without hints (40 min)
- Then: Check solutions, understand approach
- Variations: How would you solve if...?
- Practice 1-2 per week

### For Hard Problems:
- Solve only after you've mastered medium
- First: Try for 60 min without hints
- Then: Look at one hint, try again
- Then: Study full solution
- Practice 1 per week

### System Design Tips:
- Use diagrams (draw ASCII art)
- Talk through every decision
- Identify bottlenecks early
- Discuss tradeoffs explicitly

### Mock Interview Tips:
- Record yourself (you'll hear your mistakes)
- Time yourself strictly
- Don't look at hints mid-interview
- Score yourself: 0-100
- Review and iterate

