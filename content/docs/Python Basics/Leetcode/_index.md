---
weight: 3
bookCollapseSection: true
title: "Leetcode Notes"
---

# **Leetcode Interview Preparation Notes**

## **Basic Data Structures**

### **Arrays**
In Python, arrays are typically represented using lists. While Python doesn't have a native array type as seen in other languages like Java or C++, lists are versatile and can be used similarly to arrays. 

【`Last Update: 2024-08-14`】

```python
arr = []          # O(1)
arr = [1, 2, 3]   # O(n), where n is the number of elements
first_element = arr[0]  # O(1)
arr[1] = 10  # O(1)
arr.append(6)  # O(1) on average for appending
arr.insert(2, 15)  # O(n), where n is the number of elements after the insertion index
arr.remove(15)  # O(n), where n is the number of elements in the list [remove the first 15 in the array]
del arr[2]  # O(n), where n is the number of elements after the deleted index
last_element = arr.pop()  # O(1)
arr.sort()  # 原地排序
sorted_arr = sorted(arr)  # 返回排序后的数组
arr[::-1] # arr 倒序
```

```python
## Counter() 的常用语法和使用情况
from collections import Counter
arr = [1, 2, 2, 3, 3, 3]
counts = Counter(arr)  # 结果：Counter({3: 3, 2: 2, 1: 1})

## 找到出现次数最多的元素
most_common_element = counts.most_common(1)[0]  # 结果：(3, 3)

## 判断出现的元素是否相同
arr1 = [1, 2, 3]
arr2 = [3, 2, 1]
is_anagram = Counter(arr1) == Counter(arr2)  # 结果：True
```
```python
## set() 的常用语法和使用情况
arr = [1, 2, 2, 3, 4, 4]

## 快速查找
seen = set(arr)
if 3 in seen:
    print("3 is in array")

## 去重
unique_elements = list(set(arr))  # 结果：[1, 2, 3, 4]

## 两个数组的交集
arr1 = [1, 2, 2, 3]
arr2 = [2, 3, 4]
intersection = list(set(arr1) & set(arr2))  # 结果：[2, 3]
```
### **Strings**
Strings in Python are immutable sequences of characters. You can perform various operations on strings using built-in methods and operators.

【`Last Update: 2024-08-14`】
```python
s = "Hello, World!"  # O(n), where n is the length of the string
first_char = s[0]  # O(1)
substring = s[7:12]  # O(k), where k is the length of the substring
combined = s + " Python"  # O(n + m), where n and m are the lengths of the two strings
repeated = s * 2  # O(n * k), where k is the number of repetitions

upper_s = s.upper()  # O(n), where n is the length of the string
lower_s = s.lower()  # O(n), where n is the length of the string
starts_with_hello = s.startswith("Hello")  # O(n), where n is the length of the prefix
contains_world = "World" in s  # O(n * m), where n is the length of the string and m is the length of the substring
replaced_s = s.replace("World", "Python")  # O(n * m), where n is the length of the string and m is the length of the substring

words = s.split(", ")  # O(n), where n is the length of the string
joined = " - ".join(words)  # O(n), where n is the total length of the resulting string
```

### **Linked Lists**
A Linked List is a linear data structure consisting of nodes, where each node contains:

  * A data part that stores the actual data.
  * A next part (or pointer) that points to the next node in the list.

【`Last Update: 2024-11-14`】

```python
## A node in a linked list can be represented as a class

class ListNode:
    def __init__(self, data=0, next=None):
        self.data = data  # Data of the node
        self.next = next  # Pointer to the next node
```
```python
##  Inserting Nodes

def insert_at_beginning(head, data):
    new_node = ListNode(data)  # Create a new node
    new_node.next = head       # Link the new node to the current head
    return new_node            # New node becomes the head
```
```python
## Deleting Nodes

def delete_from_beginning(head):
    if not head:
        return None
    return head.next  # The second node becomes the new head
```
```python
## Searching for a Node

def search(head, key):
    current = head
    while current:
        if current.data == key:
            return True  # Found the data
        current = current.next
    return False  # Data not found
```

### **Stack**
A Stack is a linear data structure that stores items in a **Last-In/First-Out (LIFO)** or **First-In/Last-Out (FILO)** manner. In stack, a new element is added at one end and an element is removed from that end only.

  * `push(a)` – Inserts the element ‘a’ at the top of the stack – Time Complexity: O(1)
  * `pop()` – Deletes the topmost element of the stack – Time Complexity: O(1)
  * `Peek` - View the top element without removing it.
  * `Empty` - Check if the stack is empty.

【`Last Update: 2024-11-19`】

```python
stack = []

# Push elements onto the stack
stack.append(1)
stack.append(2)

# Pop element from the stack
top = stack.pop()  # Removes and returns 2

# Peek the top element
top = stack[-1] if stack else None  # Returns 1

# Check if the stack is empty
is_empty = len(stack) == 0
```

### **Queue**
Queue is a linear data structure that stores items in **First In First Out (FIFO)** manner. With a queue the least recently added item is removed first. 

  * `Enqueue`: Adds an item to the queue. If the queue is full, then it is said to be an Overflow condition – Time Complexity : O(1)
  * `Dequeue`: Removes an item from the queue. The items are popped in the same order in which they are pushed. If the queue is empty, then it is said to be an Underflow condition – Time Complexity : O(1)
  * `Peek`: View the front element without removing it.
  * `Empty`: Check if the queue is empty.

【`Last Update: 2024-11-19`】

```python
from collections import deque

# Initialize a queue
queue = deque()

# Enqueue elements
queue.append(1)
queue.append(2)

# Dequeue element
front = queue.popleft()  # Removes and returns 1

# Peek at the front element
front = queue[0] if queue else None

# Check if the queue is empty
is_empty = len(queue) == 0
```

### **Deque**
A deque is a generalized queue that allows insertion and deletion from both ends with O(1) complexity. Internally, it is implemented as a doubly linked list or a circular buffer.

【`Last Update: 2024-11-25`】

```python
from collections import deque

# Initialize a deque
dq = deque()

# Add elements
dq.append(1)       # Add to the right
dq.appendleft(2)   # Add to the left

# Remove elements
dq.pop()           # Remove from the right
dq.popleft()       # Remove from the left

# Access and manipulation
dq.extend([3, 4])          # Add multiple elements to the right
dq.extendleft([0, -1])     # Add multiple elements to the left (reversed order)
dq.rotate(1)               # Rotate elements right
dq.rotate(-1)              # Rotate elements left
dq.clear()                 # Clear all elements
```

## **Advanced Data Structures**
### **Overview**
- **Trees**: Explore the concepts of binary trees, binary search trees, AVL trees, and tree traversals (in-order, pre-order, post-order, level-order).
- **Graphs**: Learn about different graph representations (adjacency list, adjacency matrix), and traversal algorithms (Depth-First Search, Breadth-First Search) to solve problems like finding connected components or checking cycles.
- **Hash Tables**: Study how hash tables work, including hashing functions, handling collisions, and applications in tasks like item counting or implementing dictionaries.

### **Heap**
A heap is a complete binary tree stored as an array. It maintains the heap property: in a min-heap, **the parent is less than or equal to its children**. Insertions and deletions are **O(log n)** due to the need to maintain the heap property.

  * Two main types:
    * Min-Heap: The root node is the smallest, and every parent node is smaller than or equal to its children.
    * Max-Heap: The root node is the largest, and every parent node is larger than or equal to its children.
  * Root Node Access: 
    * Min-Heap: Root is the smallest element
    * Max-Heap: Root is the largest element.
  * Efficient Operations:
    * Insert and delete both take O(log n).
    * Maintains heap properties using adjustments (upward or downward shifts).


【`Last Update: 2024-11-25`】

```python
import heapq

# Initialize a heap
heap = []

# Add elements
heapq.heappush(heap, 3)  # Push element into the heap
heapq.heappush(heap, 1)
heapq.heappush(heap, 4)

# Access the smallest element
smallest = heap[0]

# Remove elements
min_element = heapq.heappop(heap)  # Pop the smallest element

# Heapify an existing list
nums = [4, 1, 7, 3]
heapq.heapify(nums)

# Get n largest or smallest elements
largest = heapq.nlargest(2, nums)
smallest = heapq.nsmallest(2, nums)
```

### **Tree**
A tree is a hierarchical data structure with nodes connected by edges. The topmost node is the root, and nodes with no children are called leaves.

  * **Binary Tree**: Each node has at most two children.
  * **Binary Search Tree (BST)**: A binary tree where the left child contains values less than the parent, and the right child contains values greater.
  * **Balanced Tree**: A tree where the height difference between left and right subtrees of any node is minimal (e.g., AVL tree, Red-Black tree).
  * **Tree Traversals**:
    * Preorder Traversal (Root, Left, Right)
    * Inorder Traversal (Left, Root, Right)
    * Postorder Traversal (Left, Right, Root)

```python
## Trees are often represented using classes. 

class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right
```

  <p align="center">
  <img src="images/tree.jpg" width="500">
  </p>

```python
## Preorder Traversal (Root, Left, Right)
def preorder_traversal(root):
    if root:
        print(root.val)
        preorder_traversal(root.left)
        preorder_traversal(root.right)

## Inorder Traversal (Left, Root, Right)
def inorder_traversal(root):
    if root:
        inorder_traversal(root.left)
        print(root.val)
        inorder_traversal(root.right)

## Postorder Traversal (Left, Right, Root)
def postorder_traversal(root):
    if root:
        postorder_traversal(root.left)
        postorder_traversal(root.right)
        print(root.val)
```

```python
## Binary Search Tree (BST) Operations

## 1. Insert a Node
def insert_into_bst(root, val):
    if not root:
        return TreeNode(val)
    if val < root.val:
        root.left = insert_into_bst(root.left, val)
    else:
        root.right = insert_into_bst(root.right, val)
    return root

## 	2. Search for a Value
def search_bst(root, val):
    if not root or root.val == val:
        return root
    if val < root.val:
        return search_bst(root.left, val)
    return search_bst(root.right, val)

## 	3. Delete a Node
def delete_node(root, key):
    if not root:
        return None
    if key < root.val:
        root.left = delete_node(root.left, key)
    elif key > root.val:
        root.right = delete_node(root.right, key)
    else:
        if not root.left:
            return root.right
        if not root.right:
            return root.left
        min_larger_node = root.right
        while min_larger_node.left:
            min_larger_node = min_larger_node.left
        root.val = min_larger_node.val
        root.right = delete_node(root.right, root.val)
    return root
```

### **Hash Tables**
In Python, the built-in dict type (short for dictionary) functions as a hash table. Hash tables are a key data structure used for efficient data retrieval and storage, providing average time complexities of O(1) for insertion, deletion, and lookup operations due to their underlying hashing mechanism.

【`Last Update: 2024-11-06`】

```python
my_dict = {}  # Creating an empty dictionary
my_dict = {'key1': 'value1', 'key2': 'value2'}  # Creating a dictionary with initial values
value = my_dict['key1']   # Accessing a value by key
my_dict['key3'] = 'value3'  # Adding a new key-value pair
my_dict['key2'] = 'new_value2'  # Updating an existing key-value pair
del my_dict['key1']   # Removing an entry by key
value = my_dict.pop('key2')  # Popping an entry (removes and returns the value)
exists = 'key3' in my_dict  # # Checking if a key is in the dictionary [True]

for key in my_dict:
    print(key, my_dict[key]) # Iterating through keys
for key, value in my_dict.items(): # Iterating through key-value pairs
    print(key, value)
for value in my_dict.values(): # Iterating through values
    print(value)
```

```python
# defaultdict 使用方法，没见过的元素不会报错。适用于计数、分组和嵌套字典等应用。

from collections import defaultdict

# 使用 int 类型的 defaultdict
dd = defaultdict(int)
print(dd['missing_key'])  # 输出：0，因为 int() 的默认值是 0
print(dd)  # 输出：defaultdict(<class 'int'>, {'missing_key': 0})

# 统计元素出现次数
data = "abracadabra"
counter = defaultdict(int)
for char in data:
    counter[char] += 1
print(counter)  # 输出：defaultdict(<class 'int'>, {'a': 5, 'b': 2, 'r': 2, 'c': 1, 'd': 1})

# defaultdict(list)常用于将多个值归类到同一个键下。
data = [("apple", 1), ("banana", 2), ("apple", 3), ("banana", 4)]
grouped_data = defaultdict(list)
for fruit, count in data:
    grouped_data[fruit].append(count)
print(grouped_data)  # 输出：defaultdict(<class 'list'>, {'apple': [1, 3], 'banana': [2, 4]})

# 可以使用dict()将defaultdict转换为普通字典。
dd = defaultdict(int)
dd['a'] += 1
print(dict(dd))  # 输出：{'a': 1}

```

## **Core Algorithms**
### **Overview**
- **Two Pointer**: The two-pointer technique is used primarily in solving array and linked list problems. It involves using two pointers to traverse the data structure, allowing for efficient searching and processing of elements. 
- **Sorting Algorithms**: Review the mechanisms and use cases for quicksort, mergesort, and heapsort. Understand the trade-offs in terms of time and space complexity.
- **Search Algorithms**: Study binary search on sorted arrays, and learn about its variations for finding the first or last position of an element.
- **Recursion and Backtracking**: Understand how to apply recursion for solving problems involving permutations, combinations, and other backtrack-required scenarios. Study the call stack mechanism and how to optimize recursion through memoization.
- **Prefix Sum and Suffix Sum**: Prefix Sum and Suffix Sum are techniques used to compute the sum of elements in a subarray quickly by precomputing cumulative sums.

### **Two Pointer**
  * Finding Pairs with a Given Sum: When looking for two numbers in a sorted array that add up to a specific target.
  * Reversing a String or Array: Using two pointers to swap elements from the start and end until they meet in the middle.
  * Merging Two Sorted Arrays: Traversing both arrays simultaneously to create a new sorted array.
  * Removing Duplicates from a Sorted Array: Using two pointers to track unique elements.
  * 设置 two pointers 的时候，left 一般会在最前面，但是 right 不一定在最后，可以设置在 left 后面。

【`Last Update: 2024-11-07`】

### **Prefix Sum and Suffix Sum**

1.	Prefix Sum: For an array nums, the prefix sum at each index i is the sum of all elements from the start of the array up to i. This allows you to find the sum of any subarray [i, j] in constant time by calculating prefix[j+1] - prefix[i].
2.	Suffix Sum: For the same array nums, the suffix sum at index i is the sum of all elements from i to the end of the array. It enables efficient queries for sums of subarrays that start from any index i to a given end by using suffix[i] - suffix[j+1].

```python
## Input [1, 2, 3, 4] -> Output [2x3x4, 1x3x4, 1x2x4, 1x2x3] = [24, 12, 8, 6]
## Predix -> [0, 1, 1x2, 1x2x3] = [0, 1, 2, 6]
## Suffix -> [2x3x4, 3x4, 4, 0] = [24, 12, 4, 0]

def productExceptSelf(self, nums: List[int]) -> List[int]:
  res = [1] * len(nums)
  prefix, suffix = 1, 1

  for i in range(len(nums)):
    res[i] = prefix
    prefix *= nums[i]

  for j in range(len(nums)-1,-1,-1):
    res[j] *= suffix
    suffix *= nums[j]
        
  return res
```
【`Last Update: 2024-11-11`】

## **Advanced Algorithms**
### **Overview**
- **Dynamic Programming**: Explore the methodology of solving problems by breaking them down into smaller subproblems, storing results, and combining them to solve larger problems. Focus on understanding the concepts of overlapping subproblems and optimal substructure.
- **Greedy Algorithms**: Learn how greedy choices can lead to globally optimized solutions and their applications in problems like scheduling, graph based problems (like minimum spanning trees), and currency denomination.
- **Graph Algorithms**: Study shortest path algorithms (Dijkstra’s, Bellman-Ford) and minimum spanning tree algorithms (Prim’s, Kruskal’s). Understand their use cases and limitations.