# Simplified versions of the solutions for all 10 topics in Python & Java

**Two Sum:**

**Python:**
```python
def two_sum(nums, target):
    seen = {}
    for i, num in enumerate(nums):
        if target - num in seen:
            return [seen[target - num], i]
        seen[num] = i
    return []
```

**Java:**
```java
import java.util.HashMap;
import java.util.Map;

public class TwoSum {
    public int[] twoSum(int[] nums, int target) {
        Map<Integer, Integer> seen = new HashMap<>();
        for (int i = 0; i < nums.length; i++) {
            if (seen.containsKey(target - nums[i])) {
                return new int[] { seen.get(target - nums[i]), i };
            }
            seen.put(nums[i], i);
        }
        return new int[0];
    }
}
```

**Reverse String:**

**Python:**
```python
def reverse_string(s):
    return s[::-1]
```

**Java:**
```java
public class ReverseString {
    public String reverseString(String s) {
        return new StringBuilder(s).reverse().toString();
    }
}
```

**Palindrome:**

**Python:**
```python
def is_palindrome(s):
    s = ''.join(c for c in s if c.isalnum()).lower()
    return s == s[::-1]
```

**Java:**
```java
public class Palindrome {
    public boolean isPalindrome(String s) {
        s = s.replaceAll("[^a-zA-Z0-9]", "").toLowerCase();
        return s.equals(new StringBuilder(s).reverse().toString());
    }
}
```

**Fibonacci Series:**

**Python:**
```python
def fibonacci(n):
    fib = [0, 1]
    while len(fib) < n:
        fib.append(fib[-1] + fib[-2])
    return fib
```

**Java:**
```java
import java.util.ArrayList;
import java.util.List;

public class Fibonacci {
    public List<Integer> fibonacci(int n) {
        List<Integer> fib = new ArrayList<>();
        fib.add(0);
        if (n > 1) {
            fib.add(1);
            for (int i = 2; i < n; i++) {
                fib.add(fib.get(i - 1) + fib.get(i - 2));
            }
        }
        return fib;
    }
}
```

**Merge Sorted Arrays:**

**Python:**
```python
def merge_sorted_arrays(nums1, nums2):
    return sorted(nums1 + nums2)
```

**Java:**
```java
import java.util.Arrays;

public class MergeSortedArrays {
    public int[] mergeSortedArrays(int[] nums1, int[] nums2) {
        int[] merged = new int[nums1.length + nums2.length];
        System.arraycopy(nums1, 0, merged, 0, nums1.length);
        System.arraycopy(nums2, 0, merged, nums1.length, nums2.length);
        Arrays.sort(merged);
        return merged;
    }
}
```

**Linked List Operations:**

**Python:**
```python
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

def insert_linked_list(head, val):
    new_node = ListNode(val)
    new_node.next = head
    return new_node

def delete_linked_list(head, val):
    if head is None:
        return None
    if head.val == val:
        return head.next
    current = head
    while current.next is not None:
        if current.next.val == val:
            current.next = current.next.next
            return head
        current = current.next
    return head
```

**Java:**
```java
class ListNode {
    int val;
    ListNode next;
    ListNode(int val) {
        this.val = val;
    }
}

public class LinkedListOperations {
    public ListNode insertLinkedList(ListNode head, int val) {
        ListNode newNode = new ListNode(val);
        newNode.next = head;
        return newNode;
    }

    public ListNode deleteLinkedList(ListNode head, int val) {
        if (head == null) {
            return null;
        }
        if (head.val == val) {
            return head.next;
        }
        ListNode current = head;
        while (current.next != null) {
            if (current.next.val == val) {
                current.next = current.next.next;
                return head;
            }
            current = current.next;
        }
        return head;
    }
}
```

**Binary Search:**

**Python:**
```python
def binary_search(nums, target):
    left, right = 0, len(nums) - 1
    while left <= right:
        mid = left + (right - left) // 2
        if nums[mid] == target:
            return mid
        elif nums[mid] < target:
            left = mid + 1
        else:
            right = mid - 1
    return -1
```

**Java:**
```java
public class BinarySearch {
    public int binarySearch(int[] nums, int target) {
        int left = 0;
        int right = nums.length - 1;
        while (left <= right) {
            int mid = left + (right - left) / 2;
            if (nums[mid] == target) {
                return mid;
            } else if (nums[mid] < target) {
                left = mid + 1;
            } else {
                right = mid - 1;
            }
        }
        return -1;
    }
}
```

**Maximum Subarray:**

**Python:**
```python
def max_subarray(nums):
    max_sum = current_sum = nums[0]
    for num in nums[1:]:
        current_sum = max(num, current_sum + num)
        max_sum = max(max_sum, current_sum)
    return max_sum
```

**Java:**
```java
public class MaximumSubarray {
    public int maxSubarray(int[] nums) {
        int maxSum = nums[0];
        int currentSum = nums[0];
        for (int i = 1; i < nums.length; i++) {
            currentSum = Math.max(nums[i], currentSum + nums[i]);
            maxSum = Math.max(maxSum, currentSum);
        }
        return maxSum;
    }
}
```

**Valid Parentheses:**

**Python:**
```python
def is_valid_parentheses(s):
    stack = []
    mapping = {')': '(', '}': '{', ']': '['}
    for char in s:
        if char in mapping:
            top_element = stack.pop() if stack else '#'
            if mapping[char] != top_element:
                return False
        else:
            stack.append(char)
    return not stack
```

**Java:**
```java
import java.util.Stack;

public class ValidParentheses {
    public boolean isValidParentheses(String s) {
        Stack<Character> stack = new Stack<>();
        for (char c : s.toCharArray()) {
            if (c == '(' || c == '{' || c == '[') {
                stack.push(c);
            } else if (c == ')' && !stack.isEmpty

() && stack.peek() == '(') {
                stack.pop();
            } else if (c == '}' && !stack.isEmpty() && stack.peek() == '{') {
                stack.pop();
            } else if (c == ']' && !stack.isEmpty() && stack.peek() == '[') {
                stack.pop();
            } else {
                return false;
            }
        }
        return stack.isEmpty();
    }
}
```

**String Manipulation:**

**Python:**
```python
def reverse_sentence(sentence):
    words = sentence.split()
    return ' '.join(words[::-1])

def to_uppercase(s):
    return s.upper()

def to_lowercase(s):
    return s.lower()
```

**Java:**
```java
public class StringManipulation {
    public String reverseSentence(String sentence) {
        String[] words = sentence.split(" ");
        StringBuilder reversed = new StringBuilder();
        for (int i = words.length - 1; i >= 0; i--) {
            reversed.append(words[i]);
            if (i > 0) {
                reversed.append(" ");
            }
        }
        return reversed.toString();
    }

    public String toUppercase(String s) {
        return s.toUpperCase();
    }

    public String toLowercase(String s) {
        return s.toLowerCase();
    }
}
```

Feel free to use these simplified versions of the solutions to practice and understand the concepts better.
