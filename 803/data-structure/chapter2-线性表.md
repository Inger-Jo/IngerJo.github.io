# Chapter2 - 线性表

## 顺序表

随机存取，插入删除需要移动大量元素。

***插入移动元素***

- 在表头插，需后移 n 个元素
- 在表尾插，后移 0 个元素
- **故平均情况 = n(n+1)/2 / (n+1) = n/2** ，n+1 表示有 n+1 个位置可以插入，n+……+1为分别在每个位置插入需要后移的次数之和。

***删除移动元素***

- 删除表头元素，前移 n-1 个元素
- 删除表尾元素，前移 0 个元素
- 故平均情况 = **n(n-1) /2 / n = (n-1)/2***

[408统考题](../assets/线性表/顺序表算法.md)

## 链表

### 错题

1. 单链表中，增加一个头结点的目的是为了：**方便运算**，插入时不需判断是否在第一个元素之前，删除时也无需判断是否为第一个元素。
2. 在一个长度为 n 的带头结点的单链表 h 上，设有尾指针 r，则执行（删除单链表最后一个元素）操作与链表长度有关。`虽然有尾指针 r，但删除最后一个元素时，依然需要从头到尾遍历到倒数第二个结点设置其 next 域的值为 NULL。`
3. 某线性表最常见的操作是在最后一个元素之后插入一个元素p和删除第一个元素，则采用（**仅有尾指针的单循环链表**）最合适。`插入操作：p->next = rare->next; rare->next = p; rare = p; rare指针的next域指向第一个元素,故删除操作只需：p = rare->next; rare->next = rare->next->next; free(p)`
4. 带头结点的**双循环链表** L 为空的条件是：`L->prior = L && L->next = L`
5. 一个链表最常用的操作是**在末尾插入节点和删除**节点，则选用 **带头结点的双循环链表** 最省时间。`插入: p->next = head->prior->next; p->prior = head->prior; head->prior->next = p; p->next = head; 删除：p = head->prior; head->prior = p->prior; p->prior->next = p->next; free(p); `