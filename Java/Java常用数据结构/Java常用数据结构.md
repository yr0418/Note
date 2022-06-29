# 字符串

---



## 3.1 字符串的拼接 —— concat方法

```java
String str1 = "我的世界，你的爱情";
str1=str1.concat("love in the sky");
System.out.println(str1)；
```

---



## 3.2 数字转换为字符串:

### 1. 显示转换

```java
String str1 = String.valueOf(12.123); //适用于全部类型的数据转换为字符串
```



### 2. 隐式转换：

语法：**字符串 = 字符串 + 数字**

```java
String str1 = "" + 123; 
String str1 = "345" + 123;
```

隐式转换要注意的三种情况：

```java
String a = "1" + 2 + 3 + 4    // 输出结果为 "1234"，碰到字符串后直接输出后面的内容
String b = 1 + 2 + 3 + "4"    // 输出结果为 "64"，碰到字符串前先做运算再拼接
String c = "1" + (2 + 3 + 4)  // 输出结果为 "19"，碰到字符串后，先运算括号里的值，再拼接
```

---



## 3.3 获取字符串长度

语法：**str.length()**

```java
String str1 = "1234567890987";
int a = str1.length(); // length 后有()存在，而获取数组长度时，length后无括号。

// length() 方法返回的字符串长度包括字符串里的空格
// null字符串（即空字符串）不能使用length() 方法
```

---



## 3.4 获取指定的字符

语法：**str.charAt(int index);**

1. Index：自定字符的索引（字符串中的每一个字符均存在一个索引，索引亦从 0 开始）
2. Str：字符串对象

```java
String name = "Peter";
char ch = name.charAt(0);    // 输出：P
```

---



## 3.5 获取子字符串索引位置

#### 1.indexOf(String str)

查找指定字符第一次出现的索引位置。

语法：**a.indexOf(str);**

1. a：任意字符串对象。
2. Str：要搜索的字符串

> lastindexOf (String str)：返回指定字符最后出现位置的索引。

```java
String a = "we are the world";
int size = a.indexOf("e");    // size的值为 1。 
```



#### 2.indexOf(String str，int fromIndex)

从指定索引 **fromIndex** 开始到字符串最后，返回指定子字符串在此字符串中第一次出现的位置。如果没有检索到指定字符串，则返回 **-1**

> lastindexOf（String str，int fromIndex），从指定的索引向前搜索，返回指定子字符串在此字符串中最后出现的索引。

```java
String c = "we are the world";
int index = c.indexOf("r", 3);
```

---

 

## 3.6 判断字符串首尾内容

startsWith( ) 和 endsWith( ) 分别用于字符串是否以指定内容开始或结尾，这两个方法的返回值都是Boolean类型

#### 1.endsWith(String suffix)

该方法用于判断字符串是否以指定字符结尾

```java
String str = "HelloJava.java";
boolean b1 = str.endsWith("java");
System.out.println(b1);    //Boolean值为 true
```

 

#### 2.startsWith(String prefix)

该方法用于判断字符串是否以指定字符开始

```java
String str = "HelloJava.java";
boolean b1 = str.startsWith("H");
System.out.println(b1);    // true
```

 

#### 3.startsWith(String prefix, int offset)

该方法用于判断从指定索引开始的子字符串是否以指定字符开始

```java
String str = "HelloJava.java";
boolean b1 = str.startsWith("l",2);    // 索引2开始
System.out.println(b1);                // 输出 true
```

---



## 3.7 获取字符数组：toCharArray( )方法

```java
String str = "我是一个字符串";
char[] ch = str.toCharArray();    //将字符串变成一个字符数组
```

---



## 3.8 判断子字符串是否存在

1. **contains**( )
2. **indexOf**( )

```java
// indexOf("b"), 表示 b 所在的索引值

String str = "88888B88888";
Boolean bool1 = str.contains("B");    // 返回 true
Boolean bool2 = str.contains("F");    // 返回 false

String str = "88888B88888";
if (str.indexOf("B")>-1) {
  System.out.println("B存在");
  System.out.println("B的索引为" + str.indexOf("B"));
}  

```

---



## 3.9 比较字符串是否相同

对字符串对象的比较不能简单的使用比较运算符 **==** 来进行判断，因为比较运算符比较的是两个字符串的内存位置是不是相同。即使两个字符串的文本值相同，两个对象的内存地址也是不同的，所以使用比较运算符会返回false

#### 1.equals(String str)

将此字符与指定字符比较，当且仅当该参数不为 null ，并且是与此对象表示相同字符序列的String 对象是，结果才为 true。

```java
String str = new String("abc");
String str1 = new String("abc");
System.out.println(str.equals(str1));    // true
```

 

#### 2.equalsIgnoreCase(str1) —— 不区分大小的比较方法

```java
String str = new String("abc");
String str1 = new String("ABC");
System.out.println(str.equalsIgnoreCase(str1));    // true
```

 

### 3. 特殊情况

当字符串的创建没有使用 new 创建新对象，而是直接引入字符变量，则可以使用 **==** 直接比较。但是在实际应用中，不可使用 **==** 进行字符串的比较。这是为了防止出现异常。

```java
String str = "abc";
String str1 = "abc";
System.out.println(str==str1);    // 输出true

String s1 = new String("abc");
String s2 = new String("abc");
System.out.println(s1==s2);       // 输出false

String s1 = "hello" + "java";
String s2 = "hellojava";
System.out.println(s1==s2);       // 输出true 
```

---



## 3.10 截取字符串

#### 1.substring(int beginindex)

该方法从指定字符的索引位置开始截取，一直到字符串的结尾位置

```java
String str = "asdfghjk";
String s1=str.substring(6);
System.out.println(s1);   //输出jk
```

 

#### 2.substring(int beginIndex，int endIndex)

该方法从指定索引位置 **beginIndex** 开始截取，一直到 **endIndex-1** 处结束

```java
String str = "asdfghjk";
String s1=str.substring(1,3);
System.out.println(s1);    //输出sd
```

---



## 3.11 字符串的替换

#### 1.replace(CharSequence target, CharSequence replacement)

该方法可以将指定的字符序列替换成指定的新的字符序列

```java
String str = "馒头一文一个";
String s1 = str.replace("一", "壹");
System.out.println(s1);    //输出馒头壹文壹个
```

 

#### 2.replaceAll(String regex, String replacement)

该方法可以将指定的字符序列替换成指定的新的字符序列，支持正则表达式（正则表达式是含有一些具有特殊意义的字符的字符串，这些特殊字符称为正则表达式的元字符，例如：**\\\d** 表示数字 **0~9** 中的任意一个。

```java
String str = "123456abcd";
String s1 = str.replaceAll("\\d", "?");
System.out.println(s1);    // 输出：??????abcd
```

 

#### 3.replaceFirst(String regex, String replacement)

该方法可以将第一个指定的字符序列替换成指定的新的字符序列，支持正则表达式

```java
String str = "123456aacd";
String s1 = str.replaceFirst("a", "?");
System.out.println(s1);    //输出：123456?acd
```

---



## 3.12 字符串分割 —— split

#### 1.split(String regex)

该方法可根据指定的分隔符对字符串进行分割，支持正则表达式，最后返回一个字符串数组

```java
String str = "abc,def,ghi";
String s1[] = str.split(",");    // 以","作为分割符
for (int i=0; i<s1.length; i++)
   System.out.println(s1[i]);    // 分割符不输出
```

  

#### 2.split(String regex, int limit)

该方法可根据指定的分隔符对字符串进行分割，并限定分割次数，支持正则表达式

```java
String str = "abc,def,gh,i";
String s1[] = str.split(",", 2);    // 将原字符串分隔为两块
for (int i=0; i<s1.length; i++)
   System.out.println(s1[i]);       // 输出："abc"、"def,gh,i"
```



### 3. 多个分隔符 

想定义多个分隔符，可以使用符号 **|** 分隔多个分隔符。如果用 **|** 做分隔符，需要使用转义字符 **\\\ |**

```java
String str = "a,b.c d|efg/hi";
String s1[] = str.split(",| |\\.|\\||/");
   for (int i=0; i<s1.length; i++)
     System.out.println(s1[i]);    // 输出a b c d efg hi。字符"."需要使用转义字符。
```

---



## 3.13 大小写转换

1. toLowerCase( )：全部转化为小写。
2. toUpperCase( )：全部转化为大写

```java
String str = "abc EFG";
String s1 = str.toLowerCase();    // 全部转换为小写
String s2 = str.toUpperCase();    // 全部转换为大写
System.out.println(s1);    // 输出：abc efg
System.out.println(s2);    // 输出：ABC EFG
```

---



## 3.14 去除字符串首尾的空白：trim()

trim( ) 方法可以返回字符串的副本，忽略首尾的空白

```java
String str = "  abcEFG  ";
String s1=str.trim();
System.out.println("["+s1+"]");    // 输出：[abcEFG]

// **注：**：该方法对字符串中间的空白部分无效
// 引申：去除字符串中的所有空格
String str = "  a bc  EF G  ";
String s1 = str.replaceAll("\\s", "");
System.out.println("["+s1+"]");    // 输出：[abcEFG]
```

---

# ArrayList

ArrayList 类是一个可以动态修改的数组，与普通数组的区别就是它是没有固定大小的限制，我们可以添加或删除元素。



## 1. 初始化

```java
ArrayList<E> objectName =new ArrayList<>();　 // 初始化
```

- **E:** 泛型数据类型，用于设置 objectName 的数据类型，**只能为引用数据类型**。
- **objectName:** 对象名。

ArrayList 中的元素实际上是对象，如果我们要存储其他类型，而 **<E\>** 只能为引用数据类型，这时我们就需要使用到基本类型的包装类。

基本类型对应的包装类表如下：

| 基本类型 | 引用类型  |
| :------- | :-------- |
| boolean  | Boolean   |
| byte     | Byte      |
| short    | Short     |
| int      | Integer   |
| long     | Long      |
| float    | Float     |
| double   | Double    |
| char     | Character |

此外，BigInteger、BigDecimal 用于高精度的运算，BigInteger 支持任意精度的整数，也是引用类型，但它们没有相对应的基本类型。



## 2. 常用方法

| 方法                                                         | 描述                                          |
| :----------------------------------------------------------- | :-------------------------------------------- |
| [add()](https://www.runoob.com/java/java-arraylist-add.html) | 将元素插入到指定位置的 arraylist 中           |
| [addAll()](https://www.runoob.com/java/java-arraylist-addall.html) | 添加集合中的所有元素到 arraylist 中           |
| [clear()](https://www.runoob.com/java/java-arraylist-clear.html) | 删除 arraylist 中的所有元素                   |
| [clone()](https://www.runoob.com/java/java-arraylist-clone.html) | 复制一份 arraylist                            |
| [contains()](https://www.runoob.com/java/java-arraylist-contains.html) | 判断元素是否在 arraylist                      |
| [get()](https://www.runoob.com/java/java-arraylist-get.html) | 通过索引值获取 arraylist 中的元素             |
| [indexOf()](https://www.runoob.com/java/java-arraylist-indexof.html) | 返回 arraylist 中元素的索引值                 |
| [removeAll()](https://www.runoob.com/java/java-arraylist-removeall.html) | 删除存在于指定集合中的 arraylist 里的所有元素 |
| [remove()](https://www.runoob.com/java/java-arraylist-remove.html) | 删除 arraylist 里的单个元素                   |
| [size()](https://www.runoob.com/java/java-arraylist-size.html) | 返回 arraylist 里元素数量                     |
| [isEmpty()](https://www.runoob.com/java/java-arraylist-isempty.html) | 判断 arraylist 是否为空                       |
| [subList()](https://www.runoob.com/java/java-arraylist-sublist.html) | 截取部分 arraylist 的元素                     |
| [set()](https://www.runoob.com/java/java-arraylist-set.html) | 替换 arraylist 中指定索引的元素               |
| [sort()](https://www.runoob.com/java/java-arraylist-sort.html) | 对 arraylist 元素进行排序                     |
| [toArray()](https://www.runoob.com/java/java-arraylist-toarray.html) | 将 arraylist 转换为数组                       |
| [toString()](https://www.runoob.com/java/java-arraylist-tostring.html) | 将 arraylist 转换为字符串                     |
| [ensureCapacity](https://www.runoob.com/java/java-arraylist-surecapacity.html)() | 设置指定容量大小的 arraylist                  |
| [lastIndexOf()](https://www.runoob.com/java/java-arraylist-lastindexof.html) | 返回指定元素在 arraylist 中最后一次出现的位置 |
| [retainAll()](https://www.runoob.com/java/java-arraylist-retainall.html) | 保留 arraylist 中在指定集合中也存在的那些元素 |
| [containsAll()](https://www.runoob.com/java/java-arraylist-containsall.html) | 查看 arraylist 是否包含指定集合中的所有元素   |
| [trimToSize()](https://www.runoob.com/java/java-arraylist-trimtosize.html) | 将 arraylist 中的容量调整为数组中的元素个数   |
| [removeRange()](https://www.runoob.com/java/java-arraylist-removerange.html) | 删除 arraylist 中指定索引之间存在的元素       |
| [replaceAll()](https://www.runoob.com/java/java-arraylist-replaceall.html) | 将给定的操作内容替换掉数组中每一个元素        |
| [removeIf()](https://www.runoob.com/java/java-arraylist-removeif.html) | 删除所有满足特定条件的 arraylist 元素         |
| [forEach()](https://www.runoob.com/java/java-arraylist-foreach.html) | 遍历 arraylist 中每一个元素并执行特定操作     |

---

# Java LinkedList

链表（Linked list）是一种常见的基础数据结构，是一种线性表，但是并不会按线性的顺序存储数据，而是在每一个节点里存到下一个节点的地址。

链表可分为单向链表和双向链表。

一个单向链表包含两个值: 当前节点的值和一个指向下一个节点的链接。

![img](Java常用数据结构.assets/408px-Singly-linked-list.svg_.png)

一个双向链表有三个整数值: 数值、向后的节点链接、向前的节点链接。

![img](Java常用数据结构.assets/610px-Doubly-linked-list.svg_.png)

Java LinkedList（链表） 类似于 ArrayList，是一种常用的数据容器。

与 ArrayList 相比，LinkedList 的增加和删除的操作效率更高，而查找和修改的操作效率较低。

**以下情况使用 ArrayList :**

- 频繁访问列表中的某一个元素。
- 只需要在列表末尾进行添加和删除元素操作。

**以下情况使用 LinkedList :**

- 你需要通过循环迭代来访问列表中的某些元素。
- 需要频繁的在列表开头、中间、末尾等位置进行添加和删除元素操作。



## 1. 初始化

```java
LinkedList<E> list = new LinkedList<E>();   // 普通创建方法

// 使用集合创建链表
LinkedList<E> list = new LinkedList(Collection<? extends E> c); 

```

- **E:** 泛型数据类型，用于设置 objectName 的数据类型，**只能为引用数据类型**。
- **objectName:** 对象名。



## 2. 常用方法

| 方法                                           | 描述                                                         |
| :--------------------------------------------- | :----------------------------------------------------------- |
| public boolean add(E e)                        | 链表末尾添加元素，返回是否成功，成功为 true，失败为 false。  |
| public void add(int index, E element)          | 向指定位置插入元素。                                         |
| public boolean addAll(Collection c)            | 将一个集合的所有元素添加到链表后面，返回是否成功，成功为 true，失败为 false。 |
| public boolean addAll(int index, Collection c) | 将一个集合的所有元素添加到链表的指定位置后面，返回是否成功，成功为 true，失败为 false。 |
| public void addFirst(E e)                      | 元素添加到头部。                                             |
| public void addLast(E e)                       | 元素添加到尾部。                                             |
| public boolean offer(E e)                      | 向链表末尾添加元素，返回是否成功，成功为 true，失败为 false。 |
| public boolean offerFirst(E e)                 | 头部插入元素，返回是否成功，成功为 true，失败为 false。      |
| public boolean offerLast(E e)                  | 尾部插入元素，返回是否成功，成功为 true，失败为 false。      |
| public void clear()                            | 清空链表。                                                   |
| public E removeFirst()                         | 删除并返回第一个元素。                                       |
| public E removeLast()                          | 删除并返回最后一个元素。                                     |
| public boolean remove(Object o)                | 删除某一元素，返回是否成功，成功为 true，失败为 false。      |
| public E remove(int index)                     | 删除指定位置的元素。                                         |
| public E poll()                                | 删除并返回第一个元素。                                       |
| public E remove()                              | 删除并返回第一个元素。                                       |
| public boolean contains(Object o)              | 判断是否含有某一元素。                                       |
| public E get(int index)                        | 返回指定位置的元素。                                         |
| public E getFirst()                            | 返回第一个元素。                                             |
| public E getLast()                             | 返回最后一个元素。                                           |
| public int indexOf(Object o)                   | 查找指定元素从前往后第一次出现的索引。                       |
| public int lastIndexOf(Object o)               | 查找指定元素最后一次出现的索引。                             |
| public E peek()                                | 返回第一个元素。                                             |
| public E element()                             | 返回第一个元素。                                             |
| public E peekFirst()                           | 返回头部元素。                                               |
| public E peekLast()                            | 返回尾部元素。                                               |
| public E set(int index, E element)             | 设置指定位置的元素。                                         |
| public Object clone()                          | 克隆该列表。                                                 |
| public Iterator descendingIterator()           | 返回倒序迭代器。                                             |
| public int size()                              | 返回链表元素个数。                                           |
| public ListIterator listIterator(int index)    | 返回从指定位置开始到末尾的迭代器。                           |
| public Object[] toArray()                      | 返回一个由链表元素组成的数组。                               |
| public T[] toArray(T[] a)                      | 返回一个由链表元素转换类型而成的数组。                       |

---

# Java HashSet

1. HashSet 基于 HashMap 来实现的，是一个**不允许有重复元素的集合**。
2. HashSet 允许有 null 值。
3. HashSet 是无序的，即不会记录插入的顺序。
4. HashSet 不是线程安全的， 如果多个线程尝试同时修改 HashSet，则最终结果是不确定的。 在多线程访问时必须显式同步对 HashSet 的并发访问。



## 1. 初始化

```java
HashSet<E> sites = new HashSet<E>();
```

**E:** 泛型数据类型，用于设置 objectName 的数据类型，**只能为引用数据类型**。

| 基本类型 | 引用类型  |
| :------- | :-------- |
| boolean  | Boolean   |
| byte     | Byte      |
| short    | Short     |
| int      | Integer   |
| long     | Long      |
| float    | Float     |
| double   | Double    |
| char     | Character |



## 2. 常用方法

| 方法               | 描述                                                      |
| :----------------- | :-------------------------------------------------------- |
| `add(E e)`         | 如果指定的元素尚不存在，则将其添加到此集合中。            |
| `clear()`          | 从该集中删除所有元素。                                    |
| `clone()`          | 返回此 `HashSet`实例的浅表副本：未克隆元素本身。          |
| contains(Object o) | 如果此set包含指定的元素，则返回 true。                    |
| `isEmpty()`        | 如果此集合不包含任何元素，则返回 true。                   |
| `iterator()`       | 返回此set中元素的迭代器。                                 |
| `remove(Object o)` | 如果存在，则从该集合中移除指定的元素。                    |
| `size()`           | 返回此集合中的元素数（基数）。                            |
| `spliterator()`    | 在此集合中的元素上创建late-binding和失败快速Spliterator。 |

---

# Java HashMap

1. HashMap 是一个散列表，它存储的内容是键值对(key-value)映射。
2. HashMap 实现了 Map 接口，根据键的 HashCode 值存储数据，具有很快的访问速度，最多允许一条记录的键为 null，不支持线程同步。
3. HashMap 是无序的，即不会记录插入的顺序。



## 1. 初始化

```java
HashMap<Integer, String> Sites = new HashMap<Integer, String>();
```

HashMap 中的元素实际上是对象，一些常见的基本类型需要使用它的**包装类**。



## 2. 常用方法

| 方法                                                         | 描述                                                         |
| :----------------------------------------------------------- | :----------------------------------------------------------- |
| [clear()](https://www.runoob.com/java/java-hashmap-clear.html) | 删除 hashMap 中的所有键/值对                                 |
| [clone()](https://www.runoob.com/java/java-hashmap-clone.html) | 复制一份 hashMap                                             |
| [isEmpty()](https://www.runoob.com/java/java-hashmap-isempty.html) | 判断 hashMap 是否为空                                        |
| [size()](https://www.runoob.com/java/java-hashmap-size.html) | 计算 hashMap 中键/值对的数量                                 |
| [put()](https://www.runoob.com/java/java-hashmap-put.html)   | 将键/值对添加到 hashMap 中                                   |
| [putAll()](https://www.runoob.com/java/java-hashmap-putall.html) | 将所有键/值对添加到 hashMap 中                               |
| [putIfAbsent()](https://www.runoob.com/java/java-hashmap-putifabsent.html) | 如果 hashMap 中不存在指定的键，则将指定的键/值对插入到 hashMap 中。 |
| [remove()](https://www.runoob.com/java/java-hashmap-remove.html) | 删除 hashMap 中指定键 key 的映射关系                         |
| [containsKey()](https://www.runoob.com/java/java-hashmap-containskey.html) | 检查 hashMap 中是否存在指定的 key 对应的映射关系。           |
| [containsValue()](https://www.runoob.com/java/java-hashmap-containsvalue.html) | 检查 hashMap 中是否存在指定的 value 对应的映射关系。         |
| [replace()](https://www.runoob.com/java/java-hashmap-replace.html) | 替换 hashMap 中是指定的 key 对应的 value。                   |
| [replaceAll()](https://www.runoob.com/java/java-hashmap-replaceall.html) | 将 hashMap 中的所有映射关系替换成给定的函数所执行的结果。    |
| [get()](https://www.runoob.com/java/java-hashmap-get.html)   | 获取指定 key 对应对 value                                    |
| [getOrDefault()](https://www.runoob.com/java/java-hashmap-getordefault.html) | 获取指定 key 对应对 value，如果找不到 key ，则返回设置的默认值 |
| [forEach()](https://www.runoob.com/java/java-hashmap-foreach.html) | 对 hashMap 中的每个映射执行指定的操作。                      |
| [entrySet()](https://www.runoob.com/java/java-hashmap-entryset.html) | 返回 hashMap 中所有映射项的集合集合视图。                    |
| [keySet](https://www.runoob.com/java/java-hashmap-keyset.html)() | 返回 hashMap 中所有 key 组成的集合视图。                     |
| [values()](https://www.runoob.com/java/java-hashmap-values.html) | 返回 hashMap 中存在的所有 value 值。                         |
| [merge()](https://www.runoob.com/java/java-hashmap-merge.html) | 添加键值对到 hashMap 中                                      |
| [compute()](https://www.runoob.com/java/java-hashmap-compute.html) | 对 hashMap 中指定 key 的值进行重新计算                       |
| [computeIfAbsent()](https://www.runoob.com/java/java-hashmap-computeifabsent.html) | 对 hashMap 中指定 key 的值进行重新计算，如果不存在这个 key，则添加到 hasMap 中 |
| [computeIfPresent()](https://www.runoob.com/java/java-hashmap-computeifpresent.html) | 对 hashMap 中指定 key 的值进行重新计算，前提是该 key 存在于 hashMap 中。 |

---

# PriorityQueue

PriorityQueue类提供堆数据结构的功能。它实现了[Queue接口](https://www.cainiaojc.com/java/java-queue.html)。

与普通队列不同，优先队列元素是按排序顺序检索的。

假设我们想以升序检索元素。在这种情况下，优先队列的头是最小的元素。检索到该元素后，下一个最小的元素将成为队列的头。

需要注意的是，优先队列的元素可能没有排序。但是，元素总是按排序顺序检索的。

学习链接：[Java PriorityQueue - Java教程 - 菜鸟教程 (cainiaojc.com)](https://www.cainiaojc.com/java/java-priorityqueue.html)

