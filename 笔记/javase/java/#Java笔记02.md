# Java笔记 02   今日目标 186集

## 第四章 数组
### 数组概述
#### Java数组存储元素的特点？
1. 数组长度一旦确定不可变。
2. 数组中元素数据类型一致，每个元素占用空间大小相同。
3. 数组中每个元素在空间存储上，内存地址是连续的。
4. 每个元素有索引，首元素索引0，以1递增。
5. 以首元素的内存地址作为数组对象在堆内存中的地址。
6. 所有数组对象都有length属性用来获取数组元素个数。末尾元素下标：length-1
#### 数组优点？
**根据下标查询某个元素的效率极高**。数组中有100个元素和有100万个元素，查询效率相同。时间复杂度O(1)。也就是说在数组中根据下标查询某个元素时，不管数组的长短，耗费时间是固定不变的。
**原因**：知道首元素内存地址，元素在空间存储上内存地址又是连续的，每个元素占用空间大小相同，只要知道下标，就可以通过数学表达式计算出来要查找元素的内存地址。直接通过内存地址定位元素。
#### 数组缺点？
**随机增删元素的效率较低**。因为随机增删元素时，为了保证数组中元素的内存地址连续，就需要涉及到后续元素的位移问题。时间复杂度O(n)。O(n)表示的是线性阶，随着问题规模n的不断增大，时间复杂度不断增大，算法的执行效率越低。（不过需要注意的是：对数组末尾元素的增删效率是不受影响的。）
**无法存储大量数据**，因为很难在内存上找到非常大的一块连续的内存。

### 一维数组
#### 如何静态初始化一维数组？
第一种：int[] arr = {55,67,22}; 或者 int arr[] = {55,67,22};
第二种：int[] arr = new int[]{55,67,22};
#### 如何动态初始化一维数组？
int[] arr = new int[4];
Object[] objs = new Object[5];
数组动态初始化的时候，确定长度，并且数组中每个元素采用默认值。
#### 关于main方法的形参args？
接收命令行参数
在DOS命令窗口中怎么传？在IDEA中怎么传？
#### 关于方法的可变长度参数？
可变长参数只能出现在形参列表中的最后一个位置。
可变长参数可以当做数组来处理。
#### 一维数组的扩容
数组长度一旦确定不可变。
那数组应该如何扩容？
只能创建一个更大的数组将原数组中的数据全部拷贝到新数组中
可以使用System.arraycopy()方法完成数组的拷贝。
数组扩容会影响程序的执行效率，因此尽可能预测数据量，创建一个接近数量的数组，减少扩容次数。

### 二维数组
二维数组是一个特殊的一维数组，特殊在：这个一维数组中每个元素是一个一维数组。
#### 二维数组的静态初始化
int[][] arr = new int[][]{{},{},{}};
int[][] arr = {{},{},{}};
#### 二维数组的动态初始化(等长)
int[][] arr = new int[3][4];
#### 二维数组的动态初始化（不等长）
int[][] arr = new int[3][];

### Junit单元测试
#### 什么是单元测试，为什么要进行单元测试？
一个项目是巨大的，只有保证你写的每一块都是正确的，最后整个项目才能正常运行。这里所谓的每一块就是一个单元。
做单元测试需要引入JUnit框架，JUnit框架在JDK中没有，需要额外引入，也就是引入JUnit框架的class文件（jar包）
#### 单元测试类（测试用例）怎么写？
单元测试类名：XxxTest
单元测试方法怎么写？
单元测试方法需要使用@Test注解标注。
单元测试方法返回值类型必须是void
单元测试方法形参个数为0
建议单元测试方法名：testXxx
#### 什么是期望值，什么是实际值？
期望值就是在程序执行之前，你觉得正确的输出结果应该是多少
实际值就是程序在实际运行之后得到的结果
#### 常见注解：
@BeforeAll @AfterAll 主要用于在测试开始之前/之后执行必要的代码。被标注的方法需要是静态的。
@BeforeEach @AfterEach 主要用于在每个测试方法执行前/后执行必要的代码。
#### 单元测试中使用Scanner失效怎么办？
选中导航栏的“Help”，然后选中“Edit Custom VM Options...”，接着在“IDEA64.exe.vmoptions”文件中添加内容“-Deditable.java.test.console=true”，最后在重启IDEA即可解决

### 排序算法
### 查找算法
### arrays工具类
- Arrays.toString()方法：将数组转换成字符串
- Arrays.deepToString()方法：可以将二维数组转换成字符串
- Arrays.equals(int[] arr1, int[] arr2)方法：判断两个数组是否相等
- Arrays.equals(Object[] arr1, Object[] arr2)方法
- Arrays.deepEquals(Object[] arr1, Object[] arr2)方法：判断两个二维数组是否相等
- Arrays.sort(int[] arr)方法：基于快速排序算法，适合小型数据量排序。
- Arrays.sort(String[] arr)方法
- Arrays.parallelSort(int[] arr)方法：基于分治的归并排序算法，支持多核CPU排序，适合大数据量排序。
- int binarySearch(int[] arr, int elt)方法：二分法查找
- Arrays.fill(int[] arr, int data)方法：填充数组
- Arrays.fill(int[] a, int fromIndex, int toIndex, int val)方法
- int[] Arrays.copyOf(int[] original, int newLength)方法：数组拷贝
- int[] Arrays.copyOfRange(int[] original, int from, int to)
- Arrays.asList(T... data)方法：将一组数据转换成List集合。
## 第五章 异常
### 异常概述
#### 什么是异常？有什么用？

**Java中的异常是指程序运行时出现了错误或异常情况，导致程序无法继续正常执行的现象**。例如，数组下标越界、空指针异常、类型转换异常等都属于异常情况。
**Java提供了异常处理机制，即在程序中对可能出现的异常情况进行捕捉和处理**。异常机制可以帮助程序员更好地管理程序的错误和异常情况，避免程序崩溃或出现不可预测的行为。
**没有异常机制的话，程序中就可能会出现一些难以调试和预测的异常行为，可能导致程序崩溃，甚至可能造成数据损失或损害用户利益**。因此，异常机制是一项非常重要的功能，是编写可靠程序的基础。
#### 异常在Java中以类和对象的形式存在。
现实生活中也有异常，比如地震，火灾就是异常。也可以提取出类和对象，例如：
地震是类：512大地震、唐山大地震就是对象。
空指针异常是类：发生在第52行的空指针异常、发生在第100行的空指针异常就是对象。
也就是说：在第52行和第100行发生空指针异常的时候，底层一定分别new了一个NullPointerException对象。在程序中异常是如何发生的？

### 异常继承结构
### 所有的异常和错误都是可抛出的。都继承了Throwable类。
Error是无法处理的，出现后只有一个结果：JVM终止。
Exception是可以处理的。
###Exception的分类：
所有的RuntimeException的子类：运行时异常/未检查异常(UncheckedException)/非受控异常
Exception的子类（除RuntimeException之外）：编译时异常/检查异常(CheckedException)/受控异常
### 编译时异常和运行时异常区别：
编译时异常特点：在编译阶段必须提前处理，如果不处理编译器报错。
运行时异常特点：在编译阶段可以选择处理，也可以不处理，没有硬性要求。
编译时异常一般是由外部环境或外在条件引起的，如网络故障、磁盘空间不足、文件找不到等
运行时异常一般是由程序员的错误引起的，并且不需要强制进行异常处理

注意：编译时异常并不是在编译阶段发生的异常，所有的异常发生都是在运行阶段的，因为每个异常发生都是会new异常对象的，new异常对象只能在运行阶段完成。那为什么叫做编译时异常呢？这是因为这种异常必须在编译阶段提前预处理，如果不处理编译器报错，因此而得名编译时异常。

### 自定义异常
第一步：编写异常类继承Exception/RuntimeException
第二步：提供一个无参数构造方法，再提供一个带String msg参数的构造方法，在构造方法中调用父类的构造方法。

### 异常处理
#### 声明异常：类似于推卸责任的处理方式
在方法定义时使用throws关键字声明异常，告知调用者，调用这个方法可能会出现异常。这种处理方式的态度是：如果出现了异常则会抛给调用者来处理。
#### 捕捉异常：真正的处理捕捉异常
在可能出现异常的代码上使用try..catch进行捕捉处理。这种处理方式的态度是：把异常抓住。其它方法如果调用这个方法，对于调用者来说是不知道这个异常发生的。因为这个异常被抓住并处理掉了。
#### 异常在处理的整个过程中应该是：
声明和捕捉联合使用。
#### 什么时候捕捉？什么时候声明？
如果异常发生后需要调用者来处理的，需要调用者知道的，则采用声明方式。否则采用捕捉。

### 异常常用方法
#### 获取异常的简单描述信息：
exception.getMessage();
获取的message是通过构造方法创建异常对象时传递过去的message。
#### 打印异常堆栈信息：
exception.printStackTrace();
要会看异常的堆栈信息：
异常信息的打印是符合栈数据结构的。
看异常信息主要看最开始的描述信息。看栈顶信息。

### finally语句块
**finally语句块中的代码是一定会执行的**。

**finally语句块不能单独使用，至少需要配合try语句块一起使用**：
try...finally
try...catch...finally
#### 通常在finally语句块中完成资源的释放
资源释放的工作比较重要，如果资源没有释放会一直占用内存。
为了保证资源的关闭，也就是说：不管程序是否出现异常，关闭资源的代码一定要保证执行。
因此在finally语句块中通常进行资源的释放。



## 常用类
### String类
### StringBuffer与StringBuilder
### 包装类
### 大数字
### 日期处理
### java8的新日期API
### Math
### 枚举
### Random
### System
### UUID