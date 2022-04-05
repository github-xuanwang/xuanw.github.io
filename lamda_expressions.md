Lamda表达式
 ## Part 1：Lamda表达式是什么
 Lambda是一个匿名函数，可以理解为一段可以传递的代码，将代码像数据一样进行传递，可以写出更加简介、更加灵活的代码。Lambda表达式的名字来源于数理逻辑领域的λ演算。它体现了函数式编程的思想。
 
它的格式是  parameter -> expression
 
下面是一个简单的lambda表达式的例子。
 接受2个参数(数字),并返回他们的差值    (x, y) -> x – y  
  
## Part 2：为什么要有Lamda表达式
在学习中我们了解到，既然lambda表达式与函数都能实现相同的效果，为什么要用lambda表达式，为什么C++与Java的版本中会增加lambda表达式的功能呢？
 
1.其实这和近年来函数式编程范式的兴起有关。
函数式编程是一种编程范式。编程范式共有三种：基于图灵机的过程/命令编程范式；基于λ运算（λ-calculus）的函数编程范式；基于一阶逻辑（First-order logic，一般递归函数）的逻辑编程范式。
 
函数式编程将电脑运算视为函数运算，并且避免使用程序状态以及易变对象。其中，λ演算为该语言最重要的基础。而且，λ演算的函数可以接受函数作为输入参数和输出返回值。比起指令式编程，函数式编程更加强调程序执行的结果而非执行的过程，倡导利用若干简单的执行单元让计算结果不断渐进，逐层推导复杂的运算，而不是设计一个复杂的执行过程。在函数式编程中，函数是头等对象，意思是说一个函数，既可以作为其它函数的输入参数值，也可以从函数中返回值，被修改或者被分配给一个变量。
 
函数式编程已经有近60年的历史，之前一直在学术界流行而在工业界没有大规模应用。原因是之前函数式编程常被认为严重耗费CPU和存储器资源。但现在已经有很大改善。因其更适合做并行计算，近年来函数式编程开始受到大数据开发者的广泛关注。Python、JavaScript等当红语言对函数式编程支持都不错，Scala更是以函数式编程的优势在大数据领域攻城略地，即使是老牌的Java为了适应函数式编程，也加大对函数式编程的支持。（这也体现了近年来的一个现象，各种语言之间相互融合。）
 
2.具体到Java语言，Java为何需要Lambda
1996年1月，Java 1.0发布了，此后计算机编程领域发生了翻天覆地的变化。商业发展需要更复杂的应用，大多数程序都跑在更强大的装备多核CPU的机器上。带有高效运行期编译器的Java虚拟机（JVM）的出现，使得程序员将精力更多放在编写干净、易于维护的代码上，而不是思考如何将每一个CPU时钟、每一字节内存物尽其用。
多核CPU的出现成了“房间里的大象”，无法忽视却没人愿意正视。算法中引入锁不但容易出错，而且消耗时间。人们开发了java.util.concurrent包和很多第三方类库，试图将并发抽象化，用以帮助程序员写出在多核CPU上运行良好的程序。不幸的是，到目前为止，我们走得还不够远。
那些类库的开发者使用Java时，发现抽象的级别还不够。处理大数据就是个很好的例子，面对大数据，Java还欠缺高效的并行操作。Java 8允许开发者编写复杂的集合处理算法，只需要简单修改一个方法，就能让代码在多核CPU上高效运行。为了编写并行处理这些大数据的类库，需要在语言层面上修改现有的Java：增加lambda表达式。
 
简而言之，Java中加入Lambda表达式，可以使Java利用函数式编程的长处，并且提高Java的并行处理能力。
 
## Part 3：Lamda表达式的优缺点
那么，加入一些函数式编程的特性（lambda表达式）对Java有何好处呢？
1.可以让代码风格更加简洁
2.可以利用多核的优势并行处理。
 
 
同样，使用lambda表达式也有缺点：
1.对于不了解lambda的人来说，代码不容易理解。
2.如果不使用并行计算，很多时候计算速度不比传统的for循环快。（并行计算有时候需要预热才能显示出效率优势）
3.不易调试。
 
 
## Part 4：应用场景
 
可以暂时简单地理解为在需要对一个集合内的多个对象进行重复操作的时候，如：
 
1.列表迭代
对一个列表的每一个元素进行操作。
如对某一个列表进行排序；
对某一列表进行计算，如求1到100的阶乘；
 
 
不使用 Lambda 表达式时如下：
 
List<Integer>numbers =Arrays.asList(1,2,3,4,5);for(intelement :numbers){System.out.prinln(element);}
 
使用 Lambda 表达式：
 
List<Integer>numbers =Arrays.asList(1,2,3,4,5);numbers.forEach(x ->System.out.println(x));
 
如果只需要调用单个函数对列表元素进行处理，那么可以使用更加简洁的 方法引用 代替 Lambda 表达式：
 
List<Integer>numbers =Arrays.asList(1,2,3,4,5);numbers.forEach(System.out::println);
 
 
2.事件监听
不使用 Lambda 表达式：
 
button.addActionListener(newActionListener(){@OverridepublicvoidactionPerformed(ActionEvente){//handle the event}});
 
使用 Lambda 表达式，需要编写多条语句时用花括号包围起来：
 
button.addActionListener(e ->{//handle the event});
 
3.Predicate 接口
java.util.function 包中的 Predicate 接口可以很方便地用于过滤。如果你需要对多个对象进行过滤并执行相同的处理逻辑，那么可以将这些相同的操作封装到 filter 方法中，由调用者提供过滤条件，以便重复使用。
 
不使用 Predicate 接口，对于每一个对象，都需要编写过滤条件和处理逻辑：
 
List<Integer>numbers =Arrays.asList(1,2,3,4,5);List<String>words =Arrays.asList("a","ab","abc");numbers.forEach(x ->{if(x %2==0){//process logic}})words.forEach(x ->{if(x.length()>1){//process logic}})
 
使用 Predicate 接口，将相同的处理逻辑封装到 filter 方法中，重复调用：
 
publicstaticvoidmain(String[]args){List<Integer>numbers =Arrays.asList(1,2,3,4,5);List<String>words =Arrays.asList("a","ab","abc");filter(numbers,x ->(int)x %2==0);filter(words,x ->((String)x).length()>1);}publicstaticvoidfilter(List list,Predicate condition){list.forEach(x ->{if(condition.test(x)){//process logic}})}
 
filter 方法也可写成：
 
publicstaticvoidfilter(List list,Predicate condition){list.stream().filter(x ->condition.test(x)).forEach(x ->{//process logic})}
 
4.Map 映射
 
使用 Stream 对象的 map 方法将原来的列表经由 Lambda 表达式映射为另一个列表，并通过 collect 方法转换回 List 类型：
 
List<Integer>numbers =Arrays.asList(1,2,3,4,5);List<Integer>mapped =numbers.stream().map(x ->x *
2).collect(Collectors.toList());mapped.forEach(System.out::println);
 
5.Reduce 聚合
 
reduce 操作，就是通过二元运算对所有元素进行聚合，最终得到一个结果。例如使用加法对列表进行聚合，就是将列表中所有元素累加，得到总和。
因此，我们可以为 reduce 提供一个接收两个参数的 Lambda 表达式，该表达式就相当于一个二元运算：
 
List<Integer>numbers =Arrays.asList(1,2,3,4,5);intsum =numbers.stream().reduce((x,y)->x +y).get();System.out.println(sum);
 
6.代替 Runnable
 
以创建线程为例，使用 Runnable 类的代码如下：
 
Runnabler =newRunnable(){@Overridepublicvoidrun(){//to do something}};Threadt =newThread(r);t.start();
 
使用 Lambda 表达式：
Runnable r =()->{//to do something};Thread t =newThread(r);t.start();
 
或者使用更加紧凑的形式：
 
Thread t =newThread(()->{//to do something});t.sta
 
 
Part5 参考资料：
https://juejin.cn/post/6857124454653394957
https://www.zhihu.com/question/20125256
https://zh.wikipedia.org/wiki/%CE%9B%E6%BC%94%E7%AE%97
函数式编程
https://zh.wikipedia.org/wiki/%E5%87%BD%E6%95%B0%E5%BC%8F%E7%BC%96%E7%A8%8B
可计算性与计算复杂性：
https://zh.wikipedia.org/wiki/%E6%B1%BA%E5%AE%9A%E6%80%A7%E5%95%8F%E9%A1%8C
停机问题
https://zh.wikipedia.org/wiki/%E5%81%9C%E6%9C%BA%E9%97%AE%E9%A2%98
From <https://www.cnblogs.com/wangxin37/p/6737522.html> 
https://www.jianshu.com/p/0ffa278deb44
https://juejin.cn/post/6844903564993626120> 
