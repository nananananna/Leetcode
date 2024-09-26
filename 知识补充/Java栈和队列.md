在 Java 中，栈（Stack）和队列（Queue）的实现原理涉及到基础的数据结构及其操作。让我们深入了解它们各自的实现原理。

## 栈和队列的实现原理
### 栈（Stack）的实现原理

#### 1. 使用 `java.util.Stack` 类

`Stack` 类继承自 `Vector`，因此它的实现基于动态数组。`Vector` 是一个可以动态调整大小的数组，这使得栈操作非常高效。以下是 `Stack` 的一些核心操作：

- **push(E item)**: 将元素压入栈顶。这实质上是将元素添加到 `Vector` 的末尾。
- **pop()**: 移除并返回栈顶的元素。这相当于删除 `Vector` 中最后一个元素，并返回它。
- **peek()**: 返回栈顶的元素但不移除它。这只是访问 `Vector` 的最后一个元素。
- **empty()**: 检查栈是否为空。这通过检查 `Vector` 的大小是否为零来实现。
- **search(Object o)**: 返回对象在栈中的位置。通过从栈顶开始搜索对象，并返回其位置。

由于 `Stack` 基于 `Vector`，其底层实现是一个动态数组，具有快速的随机访问和修改能力。

```java
import java.util.Stack;

public class StackExample {
    public static void main(String[] args) {
        Stack<String> stack = new Stack<>();
        
        stack.push("A");
        stack.push("B");
        stack.push("C");

        System.out.println("Peek: " + stack.peek()); // C
        System.out.println("Pop: " + stack.pop());   // C
        System.out.println("Peek after pop: " + stack.peek()); // B
        System.out.println("Is stack empty? " + stack.empty()); // false
    }
}
```

#### 2. 使用 `Deque` 接口及其实现类

`Deque`（双端队列）接口支持在两端插入和删除元素，因此它可以用来实现栈。常用的实现类有 `ArrayDeque` 和 `LinkedList`。

- **ArrayDeque**: 基于动态数组实现，具有快速的随机访问和修改能力。
- **LinkedList**: 基于双向链表实现，具有快速的插入和删除能力。

```java
import java.util.ArrayDeque;
import java.util.Deque;

public class DequeAsStack {
    public static void main(String[] args) {
        Deque<String> stack = new ArrayDeque<>();

        stack.push("A");
        stack.push("B");
        stack.push("C");

        System.out.println("Peek: " + stack.peek()); // C
        System.out.println("Pop: " + stack.pop());   // C
        System.out.println("Peek after pop: " + stack.peek()); // B
        System.out.println("Is stack empty? " + stack.isEmpty()); // false
    }
}
```

### 队列（Queue）的实现原理

#### 1. 使用 `java.util.LinkedList` 类

`LinkedList` 类实现了 `Queue` 接口，是一个基于双向链表的实现。它允许在队列的头部和尾部快速插入和删除元素。

- **offer(E e)**: 将元素插入队列的尾部。实质上是将元素添加到链表的末尾。
- **poll()**: 移除并返回队列头部的元素。这相当于删除链表的第一个元素，并返回它。
- **peek()**: 返回队列头部的元素但不移除它。这只是访问链表的第一个元素。

```java
import java.util.LinkedList;
import java.util.Queue;

public class QueueExample {
    public static void main(String[] args) {
        Queue<String> queue = new LinkedList<>();

        queue.offer("A");
        queue.offer("B");
        queue.offer("C");

        System.out.println("Peek: " + queue.peek()); // A
        System.out.println("Poll: " + queue.poll()); // A
        System.out.println("Peek after poll: " + queue.peek()); // B
        System.out.println("Is queue empty? " + queue.isEmpty()); // false
    }
}
```

#### 2. 使用 `java.util.ArrayDeque` 类

`ArrayDeque` 类实现了 `Deque` 接口，是一个基于动态数组的双端队列实现。它可以在队列的两端高效地插入和删除元素。

```java
import java.util.ArrayDeque;
import java.util.Queue;

public class ArrayDequeAsQueue {
    public static void main(String[] args) {
        Queue<String> queue = new ArrayDeque<>();

        queue.offer("A");
        queue.offer("B");
        queue.offer("C");

        System.out.println("Peek: " + queue.peek()); // A
        System.out.println("Poll: " + queue.poll()); // A
        System.out.println("Peek after poll: " + queue.peek()); // B
        System.out.println("Is queue empty? " + queue.isEmpty()); // false
    }
}
```

#### 3. 使用 `java.util.PriorityQueue` 类

`PriorityQueue` 类实现了一个基于堆（heap）的优先级队列，元素按自然顺序或提供的比较器排序。

- **offer(E e)**: 将元素插入优先级队列，按优先级排列。
- **poll()**: 移除并返回队列中具有最高优先级的元素。
- **peek()**: 返回队列中具有最高优先级的元素但不移除它。

```java
import java.util.PriorityQueue;
import java.util.Queue;

public class PriorityQueueExample {
    public static void main(String[] args) {
        Queue<String> queue = new PriorityQueue<>();

        queue.offer("C");
        queue.offer("A");
        queue.offer("B");

        System.out.println("Peek: " + queue.peek()); // A
        System.out.println("Poll: " + queue.poll()); // A
        System.out.println("Peek after poll: " + queue.peek()); // B
        System.out.println("Is queue empty? " + queue.isEmpty()); // false
    }
}
```

### 总结

- **栈（Stack）**：
  - `java.util.Stack` 基于 `Vector` 实现。
  - `Deque` 接口的实现类如 `ArrayDeque` 和 `LinkedList` 也可用作栈。
  - 主要操作是 `push`（压入）、`pop`（弹出）和 `peek`（查看）。

- **队列（Queue）**：
  - `java.util.LinkedList` 基于双向链表实现。
  - `ArrayDeque` 基于动态数组实现。
  - `PriorityQueue` 基于堆实现。
  - 主要操作是 `offer`（插入）、`poll`（移除并返回）和 `peek`（查看）。

这些实现利用了基础的数据结构（数组、链表、堆）及其相应的操作特性，使得栈和队列的操作高效且符合预期的行为模式。

## 关于`Stack`的四个问题

### 1. Java 中 `Stack` 是容器么？

是的，Java 中的 `Stack` 是一种容器。它是 `java.util` 包中的一个类，用于实现栈（LIFO，后进先出）数据结构。

### 2. Java 使用的 `Stack` 是属于哪个版本的 STL？

Java 没有 C++ 那样的 STL（Standard Template Library）。Java 提供了自己的集合框架（Java Collections Framework），包括了各种数据结构和算法。Java 的 `Stack` 类属于这个集合框架的一部分。

### 3. Java 使用的集合框架中 `Stack` 是如何实现的？

Java 的 `Stack` 类继承自 `Vector` 类。`Vector` 是一个动态数组，能够自动调整大小，因此 `Stack` 类可以利用 `Vector` 的方法来实现栈的功能。以下是 `Stack` 的一些关键方法及其实现：

- **push(E item)**：将元素压入栈顶。
- **pop()**：移除并返回栈顶的元素。
- **peek()**：返回栈顶的元素但不移除它。
- **empty()**：检查栈是否为空。
- **search(Object o)**：返回对象在栈中的位置（从栈顶开始计算）。

### 4. `Stack` 提供迭代器来遍历 `Stack` 空间么？

是的，`Stack` 类继承自 `Vector`，而 `Vector` 实现了 `Iterable` 接口，因此 `Stack` 也具有迭代器。可以使用迭代器来遍历 `Stack` 中的元素。例如：

```java
Stack<String> stack = new Stack<>();
stack.push("A");
stack.push("B");
stack.push("C");

Iterator<String> iterator = stack.iterator();
while (iterator.hasNext()) {
    String element = iterator.next();
    System.out.println(element);
}
```

不过需要注意的是，迭代器遍历的顺序是从栈底到栈顶，这与栈的典型使用模式（LIFO）不同。如果需要按栈的顺序（LIFO）进行遍历，可以使用 `for-each` 循环或手动弹出元素：

```java
// 使用for-each循环（从栈底到栈顶）
for (String element : stack) {
    System.out.println(element);
}

// 按LIFO顺序遍历
while (!stack.isEmpty()) {
    System.out.println(stack.pop());
}
```

### 总结

- Java 中的 `Stack` 是一个容器，属于 Java 集合框架的一部分。
- 它继承自 `Vector`，利用动态数组实现。
- `Stack` 提供了迭代器，可以从栈底到栈顶遍历元素。
- 如果需要按 LIFO 顺序遍历，可以使用 `pop()` 方法。

## `Deque`双端队列
`Deque`（双端队列，Double Ended Queue）接口在 Java 的集合框架中是一个非常灵活的数据结构，它允许在两端插入和移除元素。`Deque` 接口有多种实现方式，如 `ArrayDeque` 和 `LinkedList`。以下是 `Deque` 接口的一些常用方法：

### 插入操作

- **`addFirst(E e)`**：在队列的开头插入元素，如果队列已满则抛出异常。
- **`addLast(E e)`**：在队列的末尾插入元素，如果队列已满则抛出异常。
- **`offerFirst(E e)`**：在队列的开头插入元素，如果队列已满则返回 `false`。
- **`offerLast(E e)`**：在队列的末尾插入元素，如果队列已满则返回 `false`。

### 移除操作

- **`removeFirst()`**：移除并返回队列的第一个元素，如果队列为空则抛出异常。
- **`removeLast()`**：移除并返回队列的最后一个元素，如果队列为空则抛出异常。
- **`pollFirst()`**：移除并返回队列的第一个元素，如果队列为空则返回 `null`。
- **`pollLast()`**：移除并返回队列的最后一个元素，如果队列为空则返回 `null`。

### 检查操作

- **`getFirst()`**：返回队列的第一个元素，但不移除，如果队列为空则抛出异常。
- **`getLast()`**：返回队列的最后一个元素，但不移除，如果队列为空则抛出异常。
- **`peekFirst()`**：返回队列的第一个元素，但不移除，如果队列为空则返回 `null`。
- **`peekLast()`**：返回队列的最后一个元素，但不移除，如果队列为空则返回 `null`。

### 栈操作

`Deque` 也可以用作栈（LIFO，后进先出）数据结构：

- **`push(E e)`**：将元素推入栈顶，相当于 `addFirst(E e)`。
- **`pop()`**：移除并返回栈顶元素，相当于 `removeFirst()`。
- **`peek()`**：返回栈顶元素，但不移除，相当于 `peekFirst()`。

### 其他常用操作

- **`size()`**：返回队列中的元素数量。
- **`isEmpty()`**：检查队列是否为空。
- **`contains(Object o)`**：检查队列是否包含指定的元素。
- **`iterator()`**：返回按从队列头部到尾部顺序的迭代器。
- **`descendingIterator()`**：返回按从队列尾部到头部顺序的迭代器。

### 示例代码

以下是一些使用 `ArrayDeque` 实现 `Deque` 接口的方法示例：

```java
import java.util.ArrayDeque;
import java.util.Deque;

public class DequeExample {
    public static void main(String[] args) {
        Deque<String> deque = new ArrayDeque<>();

        // 插入操作
        deque.addFirst("A");
        deque.addLast("B");
        deque.offerFirst("C");
        deque.offerLast("D");

        // 检查操作
        System.out.println("First element: " + deque.getFirst()); // 输出 C
        System.out.println("Last element: " + deque.getLast());   // 输出 D

        // 移除操作
        System.out.println("Removed first: " + deque.removeFirst()); // 输出 C
        System.out.println("Removed last: " + deque.removeLast());   // 输出 D

        // 栈操作
        deque.push("E");
        System.out.println("Pushed and peek: " + deque.peek()); // 输出 E
        System.out.println("Popped: " + deque.pop());           // 输出 E

        // 其他操作
        System.out.println("Size: " + deque.size()); // 输出 2 (A 和 B)
        System.out.println("Is empty: " + deque.isEmpty()); // 输出 false
        System.out.println("Contains A: " + deque.contains("A")); // 输出 true

        // 迭代
        System.out.println("Elements: ");
        for (String element : deque) {
            System.out.println(element); // 输出 A 和 B
        }
    }
}
```

### 总结

`Deque` 接口提供了丰富的方法来操作双端队列，使其既可以用作队列（FIFO）也可以用作栈（LIFO）。通过 `ArrayDeque` 或 `LinkedList` 等实现类，你可以灵活地进行各种插入、移除和检查操作。

## 关于`Queue`的四个问题
### 1. **Java中的`Queue`是容器吗？**

是的，Java 中的 `Queue` 是一种**容器**。`Queue` 是 Java Collections Framework（集合框架）中的一部分，用于存储一组元素，并且是一种**特殊的线性数据结构**。它遵循**先进先出（FIFO）**的原则，即先加入的元素先被处理或删除。

`Queue` 是一个接口，继承自 `Collection` 接口，因此它是容器类型的数据结构。它的主要实现类有：
- `LinkedList`（也实现了 `Deque`）
- `PriorityQueue`
- `ArrayDeque`

### 2. **我们使用的`Queue`是哪个版本的STL？**

Java 中的 `Queue` 并不是直接来自 C++ 的 STL（Standard Template Library），而是 Java 自己的集合框架中的一个接口。Java 的 `Queue` 接口出现在 **Java 2 Platform, Standard Edition (J2SE) 5.0** 版本中（也就是 Java 5）引入的 Java Collections Framework（集合框架）的一部分。

Java 集合框架中的 `Queue` 接口类似于 C++ STL 中的 `queue`，但两者是不同语言中的独立实现。Java 结合了自己的泛型系统来构建类似于 C++ 的容器功能。

### 3. **Java中的`Queue`是如何实现的？**

`Queue` 是一个接口，它有多个具体的实现类。最常用的几种实现包括：

- **`LinkedList`**：
  - `LinkedList` 实现了 `Queue` 接口（也实现了 `Deque`），它是基于双向链表的数据结构，能够高效地进行元素的插入和删除操作。`LinkedList` 是一个双端队列，支持 `Queue` 的所有方法，并且可以用作队列、栈或双端队列。
  
- **`PriorityQueue`**：
  - `PriorityQueue` 是基于**堆（heap）**的数据结构，默认是**小顶堆**。它根据元素的优先级进行排序，而不是按照插入顺序处理。你可以通过自定义比较器来指定元素的优先级。

- **`ArrayDeque`**：
  - `ArrayDeque` 是基于**数组**实现的双端队列，能够快速在队列的两端进行元素的插入和删除操作。它不允许 `null` 元素，并且比 `LinkedList` 更高效。

这些实现类都遵循 `Queue` 接口定义的方法，如 `add()`, `offer()`, `poll()`, `remove()` 和 `peek()` 等。

### 4. **`Queue`提供迭代器遍历空间吗？**

是的，`Queue` 提供了迭代器来遍历元素。因为 `Queue` 继承自 `Collection` 接口，而 `Collection` 接口继承自 `Iterable` 接口，所以所有 `Queue` 实现都提供了 `iterator()` 方法，允许你通过 `Iterator` 对队列进行遍历。

例如，遍历一个队列可以使用如下代码：

```java
Queue<Integer> queue = new LinkedList<>();
queue.add(1);
queue.add(2);
queue.add(3);

Iterator<Integer> iterator = queue.iterator();
while (iterator.hasNext()) {
    System.out.println(iterator.next());
}
```

然而，值得注意的是，尽管你可以通过迭代器遍历队列，但这种遍历并不会改变队列的顺序或遵循队列的 FIFO（先进先出）原则。也就是说，迭代器遍历是基于队列的当前存储结构，而不一定是按照队列元素的出队顺序进行的。

总结：
- **`Queue` 是容器**，用于存储和管理元素。
- Java 中的 `Queue` 是 Java Collections Framework 中的一部分，不属于 C++ 的 STL。
- `Queue` 的实现类包括 `LinkedList`、`PriorityQueue` 和 `ArrayDeque`，它们分别基于链表、堆和数组实现。
- `Queue` 提供迭代器，可以通过 `iterator()` 方法进行遍历。

## 栈里面的元素在内存中是连续分布的么？（面试题）
栈（`Stack`）中的元素在内存中**不一定是连续分布的**，这取决于具体的栈实现方式。在 Java 或其他高级编程语言中，栈的实现通常基于不同的数据结构（如数组或链表），而这些数据结构的存储方式决定了元素在内存中的分布是否连续。

### 1. **数组实现的栈（连续分布）**：
   如果栈是基于**数组**实现的，比如 Java 中的 `ArrayDeque` 或自己手动实现的基于数组的栈，那么栈中的元素在内存中是**连续分布**的，因为数组本身是连续的内存块。

   - **优点**：数组实现的栈可以通过索引快速访问元素，速度较快。
   - **缺点**：数组的大小是固定的，当需要动态扩展时，需要进行数组复制操作，可能会影响性能。

   例如，自己实现的基于数组的栈：

   ```java
   public class ArrayStack {
       private int[] stack;
       private int top;

       public ArrayStack(int capacity) {
           stack = new int[capacity];  // 数组，内存中是连续的
           top = -1;
       }

       public void push(int value) {
           stack[++top] = value;       // 元素存储在连续的数组中
       }

       public int pop() {
           return stack[top--];
       }
   }
   ```

   在这种实现中，`stack` 数组中的元素是连续分布的，因为数组在内存中是连续的存储单元。

### 2. **链表实现的栈（不连续分布）**：
   如果栈是基于**链表**实现的，比如 Java 中的 `LinkedList` 实现的栈，那么栈中的元素在内存中可能是**不连续分布**的。链表的每个节点存储了数据和一个指向下一个节点的指针，而这些节点在内存中的位置可以是不连续的。

   - **优点**：链表实现的栈能够动态扩展，不需要预定义大小，适合大小不确定的场景。
   - **缺点**：链表节点在内存中不连续，操作时需要通过指针遍历节点，相较于数组访问慢一些。

   例如，基于链表实现的栈：

   ```java
   public class LinkedListStack {
       private Node top;

       private static class Node {
           int data;
           Node next;
           Node(int data) {
               this.data = data;
           }
       }

       public void push(int value) {
           Node newNode = new Node(value);
           newNode.next = top;
           top = newNode;
       }

       public int pop() {
           int value = top.data;
           top = top.next;
           return value;
       }
   }
   ```

   在这个链表实现的栈中，栈中的每个元素是通过链表节点存储的，节点在内存中的分布是由内存分配器动态管理的，可能是不连续的。

### 3. **Java `Stack` 类的实现**：
   Java 中的 `Stack` 类实际上是继承自 `Vector` 类的，而 `Vector` 是基于动态数组实现的。因此，Java 中 `Stack` 类中的元素存储在一个动态数组中，在内存中是**连续分布**的。不过，随着栈的增长，数组可能会重新分配内存，导致栈的内容被复制到一个新的、较大的连续内存区域。

### 总结：
- **数组实现的栈**：栈中的元素在内存中是**连续分布**的。
- **链表实现的栈**：栈中的元素在内存中是**不连续分布**的。
- **Java `Stack` 类**：基于动态数组实现，因此栈中的元素在内存中通常是**连续分布**的，除非数组需要扩容。

