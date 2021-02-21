# 语法

**1.八种基本数据类型是什么？他们的包装类型是什么？各占多少个字节？**
- byte Byte 1个字节、short Short 2个字节、int Integer 4个字节、long Long 8个字节、float Float 4个字节、double Double 8个字节、char Character 2个字节、boolean Boolean 1位

**2.==与equals的区别，equals与hashCode的区别**
- ==比较的是地址，equals比较的是内容
- hashCode是用来在比较对象的时候，减少equals的调用次数，因为hashCode不相等，那么equals肯定就不相等，不用去调用equals了（map的时候是对hashcode取模，直接映射到具体的桶的位置。不用去遍历整个集合）。

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

**11.说说Object类的常用方法**
- 1、clone() 创建并返回此对象的副本。2、equals(Object obj) 指示一些其他对象是否等于此。3、getClass() 返回此 Object的运行时类。4、hashCode() 返回对象的哈希码值。5、notify() 唤醒正在等待对象监视器的单个线程。6、notifyAll() 唤醒正在等待对象监视器的所有线程。7、toString() 返回对象的字符串表示形式。 8、wait() 导致当前线程等待，直到另一个线程调用该对象的 notify()方法或 notifyAll()方法。 

**12.JDK、JRE、JVM三者之间的联系与区别**
- JDK(Java SE Development Kit)，Java标准开发包，它提供了编译、运行Java程序所需的各种工具和资源，包括Java编译器、Java运行时环境，以及常用的Java类库等。
- JRE( Java Runtime Environment) ，Java运行环境，用于解释执行Java的字节码文件。
- JVM(Java Virtual Machine)，Java虚拟机，是JRE的一部分。它是整个java实现跨平台的最核心的部分，负责解释执行字节码文件，是可运行java字节码文件的虚拟计算机。所有平台的上的JVM向编译器提供相同的接口，而编译器只需要面向虚拟机，生成虚拟机能识别的代码，然后由虚拟机来解释执行。
- JDk 包含 JRE 包含 JVM

**13.接口和抽象类的区别**
- 接口中的方法必须是抽象的，抽象类中的方法可以有非抽象的。
- 实现接口的关键字为implements，继承抽象类的关键字为extends。一个类可以实现多个接口，但一个类只能继承一个抽象类。
- 实现一个接口，必须重写它的所有方法。继承一个抽象类，可以不重写他的所有抽象方法，前提是该类是抽象类，否则必须重写其全部抽象方法。
- 接口成员变量默认为public static final，成员方法是public abstract。抽象类中成员变量默认default，抽象方法必须被abstract修饰

**14.对于static关键字的理解**
- 被static修饰的变量或方法，只属于这个类，而不属于该类所创建的对象，可以通过类名点变量或方法名调用。
- 静态代码块只执行一次，而且是在类被加载的时候执行的，静态代码块在非静态代码块之前执行在构造方法之前执行（执行顺序：静态代码块->非静态代码块->构造方法）

**15.this和supper的区别**
- this是自身的一个对象，代表对象本身。super是父类的一个对象。

**16.++i和i++的区别**
- ++i是先加再用（例如i=2，那么++i的值就是3），i++是先用再加（例如i=2，那么i++的值也是2）。

# 异常

**1.Error和Exception的区别**
- Error 是程序并没有执行而产生的，表示系统级的错误，是 java 运行环境内部错误或者硬件问题，不能指望程序来处理这样的问题，它是 java 虚拟机抛出的。
- Exception 是程序运行过程中产生的，表示程序需要捕捉、需要处理的异常，是由于程序设计的不完善而出现的问题，程序可以处理的问题。

**2.throw和throws的区别**
- throws用在方法上，后面跟的是异常类，可以跟多个；而throw用在方法内，后面跟的是异常对象。

**3.finally 块一定会执行吗**
- 不一定，当在 try 块或者 catch 块中有 System.exit(0)，这样的语句存在时 finally 块就不会被执行到了，因为程序被结束了。
- 当在 try 块或者 catch 块里 return 时 finally 会被执行；执行顺序是，当碰到try或者catch中的return时，会去执行finally中的语句，如果finally中有return，那么就直接return，如果没有，那就执行try或者catch中的return。

**4.try、catch、finally中哪个部分可以省略**
- 如果try了，也就是捕获了异常，那么必须进行catch或者finally来处理异常，所以catch或finally可以省略，但不能同时省略。

# 反射
**1.什么是反射**
- 反射是在运行状态中，对于任意一个类，都能够知道这个类的所有属性和方法；对于任意一个对象，都能够调用它的任意一个方法和属性；这种动态获取的信息以及动态调用对象方法的功能称为 Java 语言的反射机制。

**2.Java中反射的作用**
- 通过反射可以获取Class模板（该模板可以获取对象，构造方法，成员方法，属性等）：1、Class.forName("全限类名");2、类名.class;3、对象.getClass();
- 通过Class模板.newInstance();可以获取对象。


# 注解

# IO流

**1.java中有几种类型的流**
- 字节流和字符流，字节流继承InputStream和OutputStream，字符流继承自Reader和Writer

**2.字节流和字符流的区别**
- 底层设备只接受字节数据，有时候要写字符串到底层设备，需要将字符串转成字节再进行写入。字符流是字节流的包装，字符流则是接受字符串，它内部将串转成字节，再写入底层设备。

**3.什么是序列化和反序列化**
- 1、序列化：把Java对象转换为字节序列的过程。2、反序列化：把字节序列恢复为Java对象的过程。

**4.序列化的作用**
- 1、把对象的字节序列永久地保存到硬盘上（持久化对象）。 2、在网络上传送对象的字节序列（网络传输对象）。

**5.开发过程中，用字节流好，还是字符流好**
- 大多数情况下使用字节流会更好，因为大多数时候 IO 操作都是直接操作磁盘文件，所以这些流在传输时都是以字节的方式进行的（图片、音频等都是按字节存储的）
- 如果对于操作需要通过 IO 在内存中频繁处理字符串的情况使用字符流会好些，因为字符流具备缓冲区，提高了性能。

**6.说说BIO、NIO和AIO的区别**
- Java BIO： 同步并阻塞，服务器实现模式为一个连接一个线程，即客户端有连接请求时服务器端就需要启动一个线程进行处理，如果这个连接不做任何事情会造成不必要的线程开销，当然可以通过线程池机制改善。
- Java NIO： 同步非阻塞，服务器实现模式为一个请求一个线程，即当一个连接创建后，不需要对应一个线程，这个连接会被注册到多路复用器上面，所以所有的连接只需要一个线程就可以搞定，当这个线程中的多路复用器进行轮询的时候，发现连接上有请求的话，才开启一个线程进行处理，也就是一个请求一个线程模式。BIO与NIO一个比较重要的不同，是我们使用BIO的时候往往会引入多线程，每个连接一个单独的线程；而NIO则是使用单线程或者只使用少量的多线程，每个连接共用一个线程。
- Java AIO(NIO.2)： 异步非阻塞，服务器实现模式为一个有效请求一个线程，客户端的I/O请求都是由OS先完成了再通知服务器应用去启动线程进行处理。（来自网络）


# 集合

**1.说说你了解的集合**
- 集合从大的方向分有两个，一是Collection集合，二是Map集合。
- Collection集合下有List、Set、Queue。Map集合下有HashMap、LinkedHashMap、TreeMap、HashTable、ConcurrentHashMap。
- List集合下有ArrayList、LinkedList、Vector、CopyOnWriteArrayList。Set集合下有HashSet、LinkedHashSet、TreeSet、CopyOnWriteArraySet

**2.说说对ArrayList的理解**
- ArrayList是List集合的一个实现类，其底层实现是数组`transient Object[] elementData;`，数组的查询是直接通过索引，查询速度比较快，时间复杂度是O(1)，增删的话，根据增删的位置，时间复杂度有所不同，如果是中间第i个位置，时间复杂度就是O(n-i)，简单理解其时间复杂度是O(n)
- 扩容机制：当构造方法中没有指定数组的大小时，其默认容量是0，当向集合中添加第一个元素的时候，初始化容量为10。当超过这个默认值的时候，一定有一个扩容机制，其扩容机制是，当集合中元素的个数大于集合容量的时候，也就是add的时候集合放不下了，就会触发扩容机制，扩容后的新集合容量是旧集合容量的1.5倍，源码：`int newCapacity = oldCapacity + (oldCapacity >> 1);`。
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

# 多线程

**1.说说你知道的创建线程的方式**
- 1、继承Thread类，重写run方法。2、实现Runnable接口，重写run方法。3、实现Callable接口，重写call方法。4、通过线程池创建线程。

**2.说说Runnable和Callable的区别**
- Callable可以返回一个类型V，而Runnable不可以。Callable能够抛出checked exception,而Runnable不可以。
- Future和FutureTask留给你们！我放GitHub上了（uphe）

**3.说说通过线方程池创建线程的式**
- `Executors.newCachedThreadPool();`创建一个可缓存线程池，如果线程池长度超过处理需要，可灵活回收空闲线程，若无可回收，则新建线程。
- `Executors.newFixedThreadPool(10);`创建一个定长线程池，可控制线程最大并发数，超出的线程会在队列中等待。
- `Executors.newScheduledThreadPool(10);`创建一个定长线程池，支持定时及周期性任务执行。
- `Executors.newSingleThreadExecutor();`创建一个单线程化的线程池，它只会用唯一的工作线程来执行任务，保证所有任务按照指定顺序(FIFO, LIFO, 优先级)执行。
- 阿里巴巴开发手册上不推荐上面的创建方式，创建线程池推荐用ThreadPoolExecutor，其中ThreadPoolExecutor有七大参数，四大拒绝策略。
- 1、int corePoolSize 核心线程池大小。2、int maximumPoolSize 最大核心线程池大小。3、long keepAliveTime 超时存活时间。4、TimeUnit unit 超时单位。5、BlockingQueue<Runnable> workQueue 阻塞队列。6、ThreadFactory threadFactory 线程工厂，用于创建线程。7、RejectedExecutionHandler handler 拒绝策略。
- 四大拒绝策略，这里通过银行办理业务的例子进行说明。 1、AbortPolicy()); 银行满了还有人进来，不处理，抛出异常（默认）。2、CallerRunsPolicy(); 银行满了，不处理，哪里来的去哪里，一般抛给main线程。3、DiscardPolicy(); 银行满了，把该线程丢掉，不抛异常。4、DiscardOldestPolicy(); 银行满了，会和先来的线程竞争，不抛异常。

**4.最大线程数是如何确定的呢**
- 一般有两种策略CPU密集型和IO密集型，所谓CPU密集型，也就是，几核的CPU就定义为几，我的是八核，所以定义为8，`Runtime.getRuntime().availableProcessors();` 获取CPU的核数，IO密集型，就是判断程序中有多少个非常耗IO线程的程序，最大线程池的大小要大于这个值即可。

**5.说说synchronized和Lock的区别**
- 1、synchronized是关键字，Lock是类。2、synchronized无法获取锁的状态，Lock可以。3、synchronized会自动释放锁，Lock需要手动。4、synchronized没有Lock锁灵活（Lock锁可以自己定制）。

**6.说说ReentrantLock的应用场景**
- 1、ReentrantLock默认是非公平锁，但它可以设置公平锁，也就是谁先来的谁先获得锁new ReentrantLock(true)。2、ReentrantLock可以响应中断，也就是当两个线程发生死锁的时候，你把A线程中断了，B线程可以正常运行。3、ReentrantLock可以通过tryLock()实现限时等待，这样可以解决死锁问题。

**7.synchronized锁的优化了解吗**
- synchronized在JDK1.6进行了锁的优化，也就是当一个线程多次访问一个同步代码块的时候，此时会记录该线程的threadId也就是，当你再来访问的时候，我就只需判断threadId就行了，效率高，这属于偏向锁。
- 当有多个线程来的时候，那么这个锁就会升级为轻量级锁，也就是通过CAS，来进行尝试获取锁，是一种自旋锁的状态。如果在短时间内可以获得锁，不会堵塞，而且节约了CUP上下文切换的时间。
- 如果长时间没有获取到锁，会消耗CUP的资源，因为在那一直死循环，经过一个时间段后会升级为重量级锁，会发生阻塞。其中锁升级是不可逆的。

**8.说说对volatile关键字的理解**
- 三大特性保证可见性，不保证原子性，禁止指令重排。
- 在说volatile之前，需要讲解一个东西，Java内存模型（Java Memory Model，JMM），当线程读取内存中的一个变量时，会先把这个变量拷贝到CPU的高速缓存区，然后对其进行操作，操作完成后，会把该变量写入到内存中。在单线程中是不会出现任何问题的，但是在多线程中就会有问题，当线程1读取了该变量a=1到缓存区进行了加1操作，还没写到内存中，线程2读取了内存中的变量a=1也进行加1操作，然后线程1写入内存a=2，线程2也写入a=2到内存，那么最后，该变量的值是2，而不是3（出现了线程安全问题）。
- 我们想要当线程1进行了加1操作之后，让线程2知道，这就是volatile的作用了，可以保证可见性，也就是，当线程1对a变量进行了加1操作，会直接写入到内存中（立即马上），并且通知线程2，变量被修改了，要求线程2缓冲区的值去内存中重新读取。但是，加1操作不是原子性的（三步，首先读取a变量的值，然后对其进行加1操作，然后赋值给a），也就是说，当线程1读取a变量到缓冲区后，还没有修改a的值，此时线程2进来了，读取了a的值，并且对其进行了加1操作，由于可见性，会把线程1缓冲区的值进行修改，但是，线程1中的CPU已经读取了缓冲区的值，而且是更新前的值，所以出现了线程安全问题，也是volatile不保证原子性的问题。于是就需要加1操作是原子性操作，于是就有了一个automic包，通过该包下的方法，可以实现加1的原子性操作（还有其他原子性操作）。
- 所谓指令重排，也就是在不影响单线程程序程序结果的情况下进行最优执行排序

**9.那你说说CAS吧**
- CAS（Compare And Swap，比较并交换），如果我们想要修改某个值num，那么我们可以通过一个方法compareAndSet(5,6)意思是，我们期望num的值是5，如果是，就修改为6。但是这就会有一个问题，我们期望的num是5，如果有其他线程把5修改为了8，然后又修改为了5，最终是5，但是已经被修改过一次了，这就是ABA问题。我们可以通过AtomicStampedReference，也就是原子引用，在创建的时候，有一个印记，相当于版本号，每被修改一次，版本号都被更新，所以，当出现ABA问题的时候，我们就可以清楚的知道，被修改了多少次。

**10.AQS了解吗**
- 不了解，回家等通知吧，了解的私聊我，我们一起探讨一下【贺贺学编程】


# JVM

**更新中...**