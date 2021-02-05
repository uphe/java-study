#### 基础

**1.八种基本数据类型是什么？他们的包装类型是什么？各占多少个字节？**
- byte Byte 1个字节、short Short 2个字节、int Integer 4个字节、long Long 8个字节、float Float 4个字节、double Double 8个字节、char Character 2个字节、boolean Boolean 1位

**2.==与equals的区别**
- ==比较的是地址，equals比较的是内容

**3.重载和重写的区别**
- 重载：发生在同一个类中，方法名必须相同，参数类型不同、个数不同、顺序不同，方法返回值和访问修饰符可以不同，发生在编译时。
- 重写：发生在父子类中，方法名、参数列表必须相同，返回值范围小于等于父类，抛出的异常范围小于等于父类，访问修饰符范围大于等于父类；如果父类方法访问修饰符为private则子类就不能重写该方法。

**4.StringStringBuffer和StringBuilder的区别是什么**
- StringBuffer和StringBuilder的实现原理一样，其父类都是AbstractStringBuilder。StringBuffer是线程安全的，StringBuilder是JDK 1.5新增的，其功能和StringBuffer类似，性能有一些提升，但是线程不安全。

**5.String为什么不可变**
- String类中使用字符数组保存字符串，private final char value[]，被final修饰了。

**6.&和&&的区别**
- &运算符：1、按位与；2、逻辑与。
- &&运算符是短路运算符，当有一个为false的时候，结果就为false。

**7.final的作用**
- final可以修饰类、变量、方法，修饰类表示该类不能被继承、修饰方法表示该方法不能被重写、修饰变量表示该变量是一个常量不能被重新赋值。

**8.final finally finalize区别**
- final可以修饰类、变量、方法，修饰类表示该类不能被继承、修饰方法表示该方法不能被重写、修饰变量表示该变量是一个常量不能被重新赋值。
- finally一般作用在try-catch代码块中，在处理异常的时候，通常我们将一定要执行的代码方法finally代码块中，表示不管是否出现异常，该代码块都会执行，一般用来存放一些关闭资源的代码。
- finalize是一个方法，属于Object类的一个方法，而Object类是所有类的父类，该方法一般由垃圾回收器来调用，当我们调用System.gc() 方法的时候，由垃圾回收器调用finalize()，回收垃圾，一个对象是否可回收的最后判断。

**9.private default protect public的作用范围**
- private：Java语言中对访问权限限制的最窄的修饰符，一般称之为”私有的”。被其修饰的类、属性以及方法只能被该类的对象访问，其子类不能访问，更不能允许跨包访问。
- default：即不加任何访问修饰符，通常称为“默认访问模式“。该模式下，只允许在同一个包中进行访问。
- protect：一般称之为“受保护的”。被其修饰的类、属性以及方法只能被类本身的方法及子类访问，即使子类在不同的包中也可以访问。
- public：Java语言中访问限制最宽的修饰符，一般称之为“公共的”。被其修饰的类、属性以及方法不仅可以跨类访问，而且允许跨包（package）访问。

**10.BIO,NIO,AIO的区别**
- BIO：Block IO 同步阻塞式 IO，就是我们平常使用的传统 IO，它的特点是模式简单使用方便，并发处理能力低。
- NIO：Non IO 同步非阻塞 IO，是传统 IO 的升级，客户端和服务器端通过 Channel（通道）通讯，实现了多路复用。
- AIO：Asynchronous IO 是 NIO 的升级，也叫 NIO2，实现了异步非堵塞 IO ，异步 IO 的操作基于事件和回调机制。

**11.throw和throws的区别**
- throws用在方法上，后面跟的是异常类，可以跟多个；而throw用在方法内，后面跟的是异常对象。


#### 集合

**1.说说你了解的集合**
- 集合从大的方向分有两个，一是Collection集合，二是Map集合。
- Collection集合下有List、Set、Queue。Map集合下有HashMap、LinkedHashMap、TreeMap、HashTable、ConcurrentHashMap。
- List集合下有ArrayList、LinkedList、Vector、CopyOnWriteArrayList。Set集合下有HashSet、LinkedHashSet、TreeSet、CopyOnWriteArraySet

**2.说说对ArrayList的理解**
- ArrayList是List集合的一个实现类，其底层实现是数组`transient Object[] elementData;`，数组的查询是直接通过索引，查询速度比较快，时间复杂度是O(1)，增删的话，根据增删的位置，时间复杂度有所不同，如果是中间第i个位置，时间复杂度就是O(n-i)，简单理解其时间复杂度是O(n)
- 扩容机制：当构造方法中没有指定数组的大小时，其默认初始容量是10。当超过这个默认值的时候，一定有一个扩容机制，其扩容机制是，当集合中元素的个数大于集合容量的时候，也就是add的时候集合放不下了，就会触发扩容机制，扩容后的新集合容量是旧集合容量的1.5倍，源码：`int newCapacity = oldCapacity + (oldCapacity >> 1);`。
- 线程问题：ArrayList是线程不安全的，在add()方法的时候，首先会检查一下数组的容量是否够用，如果够用，那么就会执行elementData[size++] = e;方法，该语句执行了两大步，第一大步是，将e放到elementData缓冲区，第二大步是，将size的大小进行加1操作，也就是说，这个操作并非原子性操作。当在并发的情况时，就会出现问题。

**3.说说对LinkedList的理解**
- LinkedList也是List的一个实现类，其底层是双向链表，其内部有一个next指针指向下一个节点，一个prev指针，指向上一个节点，由于是链表的数据结构，所以在查询的时候相对就比较慢了，时间复杂度是O(n)，因为当我们需要查询某个元素的时候，需要从第一个节点开始遍历，直到查询结束。而他的增删就比较快了，如果增加一个N节点，直接将后一个节点的prev指向N节点，N节点的next指向后一个节点，前一个节点的next指向N节点，N节点的prev指针指向前一个节点即可，时间复杂度为O(1)，空间复杂度一般比ArrayList大，因为每个节点都要存储两个指针。
- 线程问题：LinkedList也是线程不安全的，其添加元素的操作，通过linkLast方法在尾部进行添加的，添加完之后，并把size的大小加1。其他的不说，单单一个size++就不是原子性了。简单的a加1操作会执行三步：1：把a的值加载到内存、2：将内存中的值，存储到变量中、3：然后进行加1操作。

**4.说说对Vector的理解**
- Vector也是List的一个实现类，其底层也是一个数组`protected Object[] elementData;`，底层ArrayList差不多，也就是加了synchronized的ArrayList，线程是安全的，效率没有ArrayList高，一般不建议使用。

**5.如果不使用Vector来解决ArrayList的线程安全问题，还有其他的解决方案吗？**
- 既然不建议使用Vector，还有一个包java.util.concurrent(JUC)包，它下面有一个类CopyOnWriteArrayList也是线程安全的。CopyOnWriteArrayList也是List的一个实现类。
- add方法用Lock锁来解决并发问题，其中在进行添加数据的时候，用了copyOf方法，也就是复制了一份，然后再set进去。
- CopyOnWriteArrayList底层也是用的数组，但是它的数组是用volatile修饰了，主要是保证了数据的可见性。get操作时，并没有加锁，因为volatile保证了数据的可见性，当数据被修改的时候，读操作能立刻知道。

**6.说说List和Set的区别**
- List的存储顺序是按照存入的顺序来的，而Set是根据哈希值来的
- List可以存储相同的元素，Set不可以存储相同的元素

**7.说说对HashSet的理解**
- HashSet是Set集合的一个实现类，其底层实现是HashMap的key，初始化容量是16，负载因子是0.75，扩容机制，是变为原来的2倍。
- HashSet存储元素的顺序并不是按照存入时的顺序（和List不同）而是按照哈希值来存的所以取数据也是按照哈希值取得。元素的哈希值是通过元素的hashcode方法来获取的, HashSet首先判断两个元素的哈希值，如果哈希值一样，接着会比较equals方法 如果 equals结果为true ，HashSet就视为同一个元素。如果equals 为false就不是同一个元素。 哈希值相同equals为false的元素是怎么存储呢,就是在同样的哈希值下顺延（可以认为哈希值相同的元素放在一个哈希桶中）。也就是哈希一样的存一列。

**8.说说对LinkedHashSet的理解**
- LinkedHashSet是对在HashSet的基础上维护了一个双向链表，使得LinkedHashSet存取有序。

**9.说说对TreeSet的理解**
- TreeSet()是使用二叉树的原理对新add()的对象按照指定的顺序排序（升序、降序），每增加一个对象都会进行排序，将对象插入的二叉树指定的位置。

**10.如果想要对HashSet进行线程安全处理，应该怎么办？**
- 可以通过CopyOnWriteArraySet来实现。

**11.queue是什么呢**
- queue是一个队列，先进先出（FIFO）的数据结构

**12.聊聊对HashMap的理解（重要）**
- 底层是JDK1.7是通过数组+链表JDK1.8是通过数组+链表+红黑树组成。所有的数据都是通过一个Node节点进行封装，其中Node节点中封装了hash值，key，value，和next指针。hash是通过key计算出的hashCode值进行对数组容量减一求余得到的（官方的求余方式是通过&运算进行的）。不同的key计算出来的hash值可能相同，解决冲突是通过拉链法（链表和红黑树）进行处理。正是因为这种存储形势，所以HashMap的存取顺序是无序的。
- 懒加载机制，在put值的时候会判断数组是否为空，如果是就初始化数组，而不是new的时候就初始化。
- HashMap是Map的一个实现类，其默认初始化容量大小是16。扩容机制是根据扩容因子来扩容的，当容量的使用量达到总容量的0.75时，就会触发扩容，举例说就是，当总容量是16时，使用量达到12，就会触发扩容机制。
- 当我们put一个值的时候，通过key来计算出hash值，计算出来的hash值做为数组的索引，Node节点中封装了hash值，key，value和next。当链表的长度小于8的时候，处理冲突的方式是链表。大于等于8的时候，就会触发红黑树方式存储。
- 当元素个数小于等于6的时候，会触发红黑树转化为链表的形式，为什么不是小于等于7，是因为给一个过度，也就是防止添加一个刚好为8，删除一个刚好为7，这样来回转化。

**13.说说对LinkedHashMap的理解**
- LinkedHashMap解决了HashMap不能保证存取顺序的问题。内部增加了一个链表用于维护元素存取顺序。

**14.说说对TreeMap的理解**
- TreeMap实现SortedMap接口，能够把它保存的记录根据键排序，默认是按键值的升序排序。

**15.如果想要保证HashMap的线程安全，应该怎么办？**
- 可以通过HashTable，该类的出现主要是解决了HashMap的线程安全问题，直接用了synchronized锁，所以效率上不高，不建议使用（发现JDK1.0的线程问题，解决都很暴力）。
- ConcurrentHashMap是java.util.concurrent包下的，并发包下的。他就是对HashMap进行了一个扩展，也就是解决了他的线程安全问题。ConcurrentHashMap用了大量的CAS来进行优化。

**16.什么是CAS呢？**
- CAS（Compare and swap）比较和替换是设计并发算法时用到的一种技术。简单来说，比较和替换是使用一个期望值和一个变量的当前值进行比较，如果当前变量的值与我们期望的值相等，就使用一个新值替换当前变量的值。

**17.Collection 和 Collections 有什么区别？**
- Collection 是一个集合接口（集合类的一个顶级接口）。它提供了对集合对象进行基本操作的通用接口方法。Collection接口在Java 类库中有很多具体的实现。Collection接口的意义是为各种具体的集合提供了最大化的统一操作方式，其直接继承接口有List与Set。
- Collections则是集合类的一个工具类，其中提供了一系列静态方法，用于对集合中元素进行排序、搜索以及线程安全等各种操作。

**18.ArrayList和LinkedList 的区别是什么？**
- ArrayList底层的数据结构是数组，支持随机访问，而 LinkedList 的底层数据结构是双向循环链表，不支持随机访问。使用下标访问一个元素，ArrayList 的时间复杂度是 O(1)，而 LinkedList 是 O(n)。

**19.ArrayList和Vector 的区别是什么？**
- Vector使用了synchronized来实现线程同步，是线程安全的，而ArrayList是非线程安全的。
- Vector扩容每次会增加1倍，而ArrayList只会增加0.5倍。

**20.HashMap和HashTable的区别？**
- HashMap允许空键值，HashTable不允许。
- HashMap线程不安全（效率高），HashTable线程安全。

#### 多线程

#### JVM

**更新中...**