# 编译命令

//编译命令：go build hello.go

//编译命令自定义命名：go build -o myhello hello.go

# go语言的语法要求和注意事项

//go语言的文件后缀是“.go”

//go应用程序的执行入口是main()函数

//go语言严格区分大小写

//go方法是有一条条语句构成的，每个语句后不需要分号（go语言会在每行后自动加分号），这也体现出golang的简洁性

//go编译器是一行行进行编译的，因此我们一行就写一条语句，不能把多条语句写在同一行，否则报错

//go语言定义的变量或者import的包如果没有使用到，代码不能编译通过

//大括号是成对出现的，缺一不可

# go的转义字符（escape char）

\t	：一个制表位，实现对齐的功能；

\n	：换行符

\\\	 :一个\

\\"	:一个"

\r	:一个回车 fmt.Println("天龙八部雪山飞狐\r张飞")

# go开发常见错误和解决方法

文件名或者路径错误；

语法错误：尝试去看懂编译器报告的语法错误。

# go语言中的注释（comment）

// 行注释

/*  */ 块注释（多行注释）

# 规范的代码风格要求

正确的注释和注释风格

正确的缩进和空白（选中tab整体向右，shift+tab整体向左；使用fofmt -w命令格式化代码）

运算符两边习惯加空格

go语言设计者思想：一个问题尽量只有一个解决方法

go语言的代码风格（允许）

```go
package main
import "fmt"
func main() {
	fmt.Println("tom\tjack")    // \t 等于一个tab
	fmt.Println("hello\nworld") // \n 等于换行
	fmt.Println("/Users/roc/Desktop/goproject/src/go_code/chapter02/escaptechar/main.go")
	fmt.Println("tom说\"i love you\"") // \"等于一个“
	fmt.Println("天龙八部雪山飞狐\r张飞厉害")     // \r 回车，从当前行的最前面开始输出，覆盖掉以前内容
	fmt.Println("姓名\t年龄\t籍贯\t住址\njohn\t12\t河北\t北京")
}
```

go语言的代码风格（不允许【go语言不允许这样写，是错误的！】）

```go
package main
import "fmt"
func main() 
{
	fmt.Println("tom\tjack")    // \t 等于一个tab
	fmt.Println("hello\nworld") // \n 等于换行
	fmt.Println("/Users/roc/Desktop/goproject/src/go_code/chapter02/escaptechar/main.go")
	fmt.Println("tom说\"i love you\"") // \"等于一个“
	fmt.Println("天龙八部雪山飞狐\r张飞厉害")     // \r 回车，从当前行的最前面开始输出，覆盖掉以前内容
	fmt.Println("姓名\t年龄\t籍贯\t住址\njohn\t12\t河北\t北京")
}
```

行长约定：一行最长不超过80个字符，超过的请使用换行展示，尽量保持格式优雅性！

# go官方编程指南

官方网站：golang.org【需要科学上网访问】

解释术语：API：application program interface：应用程序编程接口； 就是我们go的各个包里面的各个函数

# Golang标准库api文档

Golang中文网，在线标准库文档：https://studygolang.com/pkgdoc

Golang的包和源文件和函数的关系简图

调用一个函数的方式：import包

使用包的函数：报名.函数名

# Dos常用命令

Dos基本介绍：Disk Operation System硬盘操作系统

# 第三章_变量

## 为什么需要变量

一个程序就是一个世界

变量是程序的基本组成单位；不论使用哪种高级程序语言编写程序，变量都是其程序的基本组成单位

## 变量介绍和快速入门

变量相当于内存中一个数据存储空间的表示，你可以把变量看作是一个房间的门牌号，通过门牌号我们可以找到房间，同样的道理，通过变量名可以访问到变量（值）

变量的使用步骤：1、声明变量（定义变量）；2、给变量赋值；3、使用变量；

变量快速入门案例：

```go
package main
import "fmt"
func main() {
	//定义变量/声明变量i
	var i int
	//给i赋值
	i = 10
	//使用变量
	fmt.Println("i=", i)
}
```

## 变量使用的注意事项

1、变量表示内存中的一个存储区域

2、 该区域有自己的名称（变量名）和类型（数据类型）

3、Golang变量使用的三种方式

​	指定变量类型，声明后若不赋值，使用默认值

```go
package main
import "fmt"
func main() {
	//golang的使用方式1
	//int的默认值是0
	var i int
	fmt.Println("i=", i)
}
```

​	根据值自行判定变量类型（类型推导）

```go
package main
import "fmt"
func main() {
	//第一种
	//int的默认值是0
	var i int
	fmt.Println("i=", i)

	//第二种
	var num = 10.11
	fmt.Println("num=", num)
}
```

​	省略var，注意  :=左侧的变量不应该是已经声明过的，否则会导致编译错误；

```go
package main
import "fmt"
func main() {
	//第一种
	//int的默认值是0
	var i int
	fmt.Println("i=", i)

	//第二种
	var num = 10.11
	fmt.Println("num=", num)

	//第三种，下面的方式等价于 var name string name = "tom"
	// :=中的 : 不能省略，否则错误
	num2 := "tom"
	fmt.Println("name=", num2)
}
```

4、多变量声明

​	在编程中，有时我们需要一次性声明多个变量，Golang也提供这样的语法

​	一次性声明变量的三种方式：

```go
package main
import "fmt"
func main() {
	//该案例演示golang如何一次性声明多个变量
	// var n1, n2, n3 int
	// fmt.Println("n1=", n1, "n2=", n2, "n3=", n3)

	//一次性声明多个变量的方式2（不同类型）
	// var n1, name, n3 = 100, "tom", 888
	// fmt.Println("n1=", n1, "name=", name, "n3=", n3)

	//一次性声明多个变量的方式3（同样可以使用类型推导）
	n1, name, n3 := 100, "tom", 888
	fmt.Println("n1=", n1, "name=", name, "n3=", n3)
}
```

​	如何一次性声明多个全局变量【在go中函数外部定义的变量就是全局变量】：

5、该区域的数据值可以在同一类型范围内不断变化（重点）

```go
package main
import "fmt"

//变量使用的注意事项
func main() {
	//该区域的数据值可以在同一类型范围内不断变化
	var i int = 10
	i = 30
	i = 50
	fmt.Println("i=", i)
	//i = 1.2 //会报错，原因是不能改变数据类型
}
```



6、变量在同一个作用域(在一个函数或者代码块)内不能重名

```go
package main
import "fmt"

//变量使用的注意事项
func main() {
	//该区域的数据值可以在同一类型范围内不断变化
	var i int = 10
	i = 30
	i = 50
	fmt.Println("i=", i)
	//i = 1.2 //会报错，原因是不能改变数据类型

	//变量在同一个作用域内不能重名
	//var i int = 50
	//i := 99
}
```



7、变量 = 变量名 + 值 + 数据类型，这一点需要注意，变量的三要素

8、Golang的变量如果没有赋初始值，编译器会使用默认值

比如int默认值为0，string默认值为空串，小数默认为0

## 明确变量的几个概念

### 声明变量基本语法

var 变量名 数据类型

var a int 这就是声明了一个变量，变量名是a

var num1 float32 这也是声明了一个变量，表示一个单精度类型的小数，变量名是num1

### 初始化变量

在声明变量的时候，就给值

var a int = 45 这就是初始化变量a

使用细节：如果声明时就直接赋值，可省略数据类型

var b = 400

### 给变量赋值

比如你声明了变量：var num int //默认0

然后，再给值 num = 780 这就是给变量赋值

### 程序中+号的使用

当左右两边都是数值型时，则做加法运算

当左右两边都是字符串，则做字符串拼接

```go
package main
import "fmt"
//演示golang中+的使用
func main() {
	var i = 1
	var j = 2
	var r = i + j //做加法运算符号
	fmt.Println("r=", r)

	var str1 = "hello"
	var str2 = "world"
	var res = str1 + str2 //做拼接操作
	fmt.Println(res)
}
```



## 数据类型介绍

### 基本数据类型

数值型：

​	整数类型（int,int8,int16,in32,in64,uint,uint8,uint32,uint64,byte）

​	浮点类型（float32,float64）

字符型：

​	没有专门的字符型，使用byte来保存单个字母字符

布尔型：

​	bool：true;flase

字符串（strin）

​	官方将string归属到基本数据类型

### 派生/复杂数据类型

指针（Pointer）

数组

结构体（struct）：相当于java中的class类

管道（Channel）

函数（也是一种类型）

切片（slice）：类似于动态数组

接口（interface）

map：相当于java中的hashmap集合

## 整数类型基本使用

基本介绍：简单地说，就是用于存放整数值的，比如0，-1，2345等

```go
package main
import "fmt"

//演示golang中整数类型使用
func main() {
	var i int = 1
	fmt.Println("i=", i)

	//测试一下int8的范围 -128 ~ 127
	//其他的int16,int32,int64类推
	var j int8 = -128
	fmt.Print("j=", j)
}
```

## 指针及其内存布局

指针基本介绍

1、基本数据类型，变量存的就是值，也叫值类型

2、获取变量的地址，用&，比如：var num int,获取num的地址：&num

3、指针类型，变量存的是一个地址，这个地址指向的空间存的才是值，比如：var ptr *int = &num

4、获取指针类型所指向的值，使用：*，比如：var ptr *int，使用 *ptr获取ptr指向的值

5、举例说明

ptr是指针，指针获取的是i的地址，ptr本身也有一个地址

```go
package main
import "fmt"
//演示golang中指针类型
func main() {
	//基本数据类型在内存布局
	var i int = 10
	//i的地址是什么，&1
	fmt.Println("i的地址=", &i)

	//下面的var ptr *int = &i
	//1.ptr 是一个指针变量
	//2.ptr 的类型 *int
	//3.ptr 本身的值&1

	var ptr *int = &i
	fmt.Printf("ptr=%v\n", ptr)
	fmt.Printf("ptr的地址=%v\n", &ptr)
	fmt.Printf("ptr指向的值=%v\n", *ptr)
}

```

## 指针案例和使用陷阱

1、写一个程序，获取一个int变量num的地址，并显示到终端

2、将num的地址赋给指针ptr，并通过ptr去修改num的值

```go
package main

import (
	"fmt"
)

func main() {
	var num int = 9
	fmt.Println("num的地址是：", &num)

	var ptr *int
	ptr = &num
	*ptr = 10
	fmt.Println("num修改后的值是：", num)
}
```

```go
func main(){
	var a int = 300 //
  var b int = 400 //
  var ptr *int = &a //ok
  *ptr = 100 //a = 100
  ptr = &b //ok
  *ptr = 200 //b = 200
  fmt.Printf("a=%d,b=%d,*ptr=%d,a,b,*ptr")
}

//输出结果：
a=100;b=200,*ptr=200
```

指针细节说明：

1、值类型，都有**对应的指针类型**，形式为*数据类型，比如int的对应的指针就是*int，float32对应的指针类型就是*float32，以此类推

2、值类型包括：基本数据类型int系列，float系列，bool，string、数组和结构体struct

## 值类型和引用类型

常见的值类型和引用类型

1、值类型：基本数据类型int系列，float系列，bool，string、数组和结构体struct

2、引用类型：指针、slice切片、map、管道chan、interface等都是引用类型

值类型和引用类型使用特点：

1、值类型：变量直接存储值，内存通常在栈中分配

2、引用类型：变量存储的是一个地址，这个地址对应的空间才真正存储数据（值），内存通常在堆上分配，当没有任何变量引用这个地址时，该地址对应的数据空间就成为一个垃圾，由GC来回收

## 标识符的基本使用

标识符的概念

1、golang对各种变量、方法、函数等命名时使用的字符序列称为标识符

2、凡是自己可以起名字的地方都叫标识符

标识符的命名规则

1、由26个英文字母大小写，0-9，_组成

2、不可以以数字开头

3、golang中严格区分大小写

4、标识符不能包含空格

5、下划线"_"本身在go中是一个特殊的标识符，称为空标识符。可以代表任何其他的标识符，但是它对应的值会被忽略（比如：忽略某个返回值）。所以仅能被作为占位符使用，不能作为标识符使用

6、不能以系统保留关键字作为标识符，比如break，if等

系统保留关键字：在go中，为了简化代码编译过程中对代码的解析，其定义的保留关键字只有25个

break default func interface select case defer go map struct chan else goto package switch const

fallthrough if range type continue for import return var

## go标识符命名特点和规范

标识符的命名规范：

1、包名：保持package的名字和目录保持一致，尽量采取有意义的包名，简短、有意义、不要和标准库冲突

2、变量名、函数名、常量名：采用驼峰法

​	举例：var stuName string = "toom"

​	var goodPrice float32 = 1234.5 

3、如果变量名、函数名、常量名首字母大写，则可以被其他的包访问；如果首字母是小些则只能在本报中使用（注：可以简单的理解为，首字母大写是公有的，首字母小些是私有的）,在golang中没有public、private等关键字

## 基本数据类型的转换

介绍

golang和java/C不同，go在不同类型的变量之间赋值时需要显式转换（强制转换）。也就是说golang中数据类型不能自动转换。

基本语法

表达式T(v)将值转换为类型T

T：就是数据类型，比如int32，int64，float32等等

v：就是需要转换的变量

案例演示：

```go
package main

import "fmt"

func main() {
	var i int32 = 100
	//希望将i => float
	var n1 float32 = float32(i)
	var n2 int8 = int8(i)
	var n3 int64 = int64(i)

	fmt.Printf("i=%v n1=%v n2=%v n3=%v", i, n1, n2, n3)
	//被转换的是变量存储的数据（即值），变量本身的数据类型并没有变化
	fmt.Printf("i type is %T", i) //int32

	//在转换中，比如将int64转成int8，编译时不会报错，只是转换的结果是按溢出处理，和我们希望的结果不一样
	var num1 int64 = 999999
	var num2 int8 = int8(num1)
	fmt.Println("num2=", num2) //63,二进制的溢出处理
}
```

细节说明

1、Go中，数据类型的转换可以是从表示范围小-->表示范围大，也可以 范围大-->范围小

2、被转换的是变量存储的数据（即值），变量本身的数据类型并没有变化

3、在转换中，比如将int64转成int8，编译时不会报错，只是转换的结果是按溢出处理，和我们希望的结果不一样

课堂练习：

```go
package main
func main() {
	//课堂练习
	var n1 int32 = 12
	var n2 int64
	var n3 int8

	//n2 = n1 + 20 //int32 --> int64 错误
	//n3 = n1 + 20 // int32 --> int8 错误
}
```

如何修改上面的代码，就可以正确？

```go
package main
import "fmt"
func main() {
	//课堂练习
	var n1 int32 = 12
	var n2 int64
	var n3 int8

	n2 = int64(n1) + 20 //int32 --> int64 错误
	n3 = int8(n1) + 20  // int32 --> int8 错误

	fmt.Println("n2 is", n2)
	fmt.Println("n3 is", n3)
}
```

如果我们没有使用到一个包，但是又想去掉，前面加一个 _  表示忽略

## 基本数据类型和string的转换

基本介绍：

在程序开发中，我们经常将基本数据类型转成string，或者将string转成基本数据类型

基本类型转string类型

方式一:

fmt.Sprintf("%参数",表达式) 【推荐这个，灵活】

函数的介绍：Sprintf根据format参数生成格式化的字符串并返回该字符串

参数需要和表达式的数据类型相匹配

fmt.Springtf()..会返回转换后的字符串

案例演示：

```go
package main

import "fmt"

func main() {
	var num1 int = 99
	var num2 float32 = 23.456789
	var b bool = true
	var myChar byte = 'h'
	var str string //空的str

	//使用第一种方式来转换 fmt.Sprintf方法
	str = fmt.Sprintf("%d", num1)
	fmt.Printf("str type %T str=%q\n", str, str)

	str = fmt.Sprintf("%f", num2)
	fmt.Printf("str type %T str=%q\n", str, str)

	str = fmt.Sprintf("%t", b)
	fmt.Printf("str type %T str=%q\n", str, str)

	str = fmt.Sprintf("%c", myChar)
	fmt.Printf("str type %T str=%q\n", str, str)

}
```

方式二:

使用strconv包的函数（Format___）

```go
package main
import (
	"fmt"
	"strconv"
)
func main() {
	var num1 int = 99
	var num2 float64 = 23.456
	var b bool = true
	var myChar byte = 'h'
	var str string //空的str

	//使用第一种方式来转换 fmt.Sprintf方法
	str = fmt.Sprintf("%d", num1)
	fmt.Printf("str type %T str=%q\n", str, str)

	str = fmt.Sprintf("%f", num2)
	fmt.Printf("str type %T str=%q\n", str, str)

	str = fmt.Sprintf("%t", b)
	fmt.Printf("str type %T str=%q\n", str, str)

	str = fmt.Sprintf("%c", myChar)
	fmt.Printf("str type %T str=%q\n", str, str)

	//使用第二种方式 strconv 函数
	var num3 int = 99
	var num4 float64 = 23.456
	var b2 bool = true

	str = strconv.FormatInt(int64(num3), 10)
	fmt.Printf("str type %T str=%q\n", str, str)

	//说明：'f'格式 10:表示小数位保留10位 64:表示这个小数是float64
	str = strconv.FormatFloat(num4, 'f', 10, 64)
	fmt.Printf("str type%T str=%q\n", str, str)

	str = strconv.FormatBool(b2)
	fmt.Printf("str type%T str=%q\n", str, str)
}

```

方式三:

int转string:使用strconv包中有一个函数Itoa

```go
package main

import (
	"fmt"
	"strconv"
)

func main() {
	var num1 int = 99
	var num2 float64 = 23.456
	var b bool = true
	var myChar byte = 'h'
	var str string //空的str

	//使用第一种方式来转换 fmt.Sprintf方法
	str = fmt.Sprintf("%d", num1)
	fmt.Printf("str type %T str=%q\n", str, str)

	str = fmt.Sprintf("%f", num2)
	fmt.Printf("str type %T str=%q\n", str, str)

	str = fmt.Sprintf("%t", b)
	fmt.Printf("str type %T str=%q\n", str, str)

	str = fmt.Sprintf("%c", myChar)
	fmt.Printf("str type %T str=%q\n", str, str)

	//使用第二种方式 strconv 函数
	var num3 int = 99
	var num4 float64 = 23.456
	var b2 bool = true

	str = strconv.FormatInt(int64(num3), 10)
	fmt.Printf("str type %T str=%q\n", str, str)

	//说明：'f'格式 10:表示小数位保留10位 64:表示这个小数是float64
	str = strconv.FormatFloat(num4, 'f', 10, 64)
	fmt.Printf("str type%T str=%q\n", str, str)

	str = strconv.FormatBool(b2)
	fmt.Printf("str type%T str=%q\n", str, str)

	//使用第三种方式 strconv 包中有一个函数Itoa
	var num5 int = 4567
	str = strconv.Itoa(num5)
	fmt.Printf("str type%T str=%q\n", str, str)
}
```



## string转基本数据类型

使用的是strconv包中的函数

func ParseBool(str string) (value bool, err error)

func ParseInt(s string, base int, bitSize int) (i int64, err error)

func ParseUint(s string, base int, bitSize int) (n uint64, err error)

func ParseFloat(s string, bitSize int) (f float64, err error)

案例演示:

note:因为返回的值时int64或者float64,如希望要得到int32,float32等如下处理:

var num5 int32

num5 = int32(num)

```go
package main

import (
	"fmt"
	"strconv"
)

//演示golang中string转成基本数据类型
func main() {
	//一、转bool的
	var str string = "true"
	var b bool
	b, _ = strconv.ParseBool(str)
	//说明:
	//strconv.ParseBool(str)函数会返回两个值(value bool, err error)
	//因为我只想获取到value bool,不想获取err,所以我是用 _ 忽略error
	fmt.Printf("b type %T\nb=%v\n", b, b)

	//二、转int
	var str2 string = "1234590"
	var n1 int64
	var n2 int
	n1, _ = strconv.ParseInt(str2, 10, 0)
	n2 = int(n1)
	fmt.Printf("n1 type %T\nn1=%v\n", n1, n1)
	fmt.Printf("n2 type %T\nn2=%v\n", n2, n2)

	//三、转float
	var str3 string = "123.456"
	var f1 float64
	f1, _ = strconv.ParseFloat(str3, 64)
	fmt.Printf("f1 type %T\nf1=%v\n", f1, f1)
}
```

## string转基本类型细节

注意事项:

再将string类型转成基本数据类型时,要确保string类型能够转成有效的数据,

比如我们可以把“123”转成一个整数,但是不能把“hello”转成一个整数,如果这样做,Golang会直接将其转成0

```go
	//注意事项
	var str4 string = "hello"
	var n3 int64 = 11
	n3, _ = strconv.ParseInt(str4, 10, 64) //如果没有转成功,n3 = 0(默认值),,bool = false(默认值)
	fmt.Printf("n3 type %T\nn3=%v", n3, n3)
```

# 第四章_运算符

## 运算符基本介绍

运算符是一种特殊的符号,用以表示数据的运算、赋值和比较等

1、算术运算符

2、赋值运算符

3、比较运算符/关系运算符

4、逻辑运算符

5、位运算符

6、其他运算符

7、三元运算符(golang中没有,要使用if--else)

## 算数运算符基本使用

算数运算符是对数值类型的变量进行运算的,比如:加减乘除.在Go程序中使用的非常多

+3 正号

-4 负号

5+5 加

6-4 减

3*4 乘

5/5 除

7%5 取模(取余)

a=2 a++ 自增

a=2 a-- 自减

"He"+"llo" 字符串相加/拼接

演示 / 使用的特点:

```go
package main

import "fmt"

func main() {
	//重点讲解 / %
	//说明:如果参与运算的数都是整数,那么除后,去掉小数部分,保留整数部分(不会四舍五入)
	fmt.Println(10 / 4)
	var n1 float32 = 10 / 4
	fmt.Println(n1)

	//如果我们希望保留小数部分,则需要有浮点数参与运算
	var n2 float32 = 10.0 / 4
	fmt.Println(n2)
}
```

演示%取模的使用

```go
package main

import "fmt"

func main() {
	//重点讲解 / %
	//说明:如果参与运算的数都是整数,那么除后,去掉小数部分,保留整数部分(不会四舍五入)
	fmt.Println(10 / 4)
	var n1 float32 = 10 / 4
	fmt.Println(n1)

	//如果我们希望保留小数部分,则需要有浮点数参与运算
	var n2 float32 = 10.0 / 4
	fmt.Println(n2)

	// 演示 % 的使用
	// 看一个公式 a % b = a - a / b * b
	fmt.Println("10%3=", 10%3)     // =1
	fmt.Println("-10%3=", -10%3)   // = -10 - (-10) / 3 * 3 = -10 - (-9) = -1
	fmt.Println("10%-3=", 10%-3)   // =1
	fmt.Println("-10%-3=", -10%-3) // =-1
}
```

演示 ++ 和 -- 的使用

```go
package main

import "fmt"

func main() {
	//重点讲解 / %
	//说明:如果参与运算的数都是整数,那么除后,去掉小数部分,保留整数部分(不会四舍五入)
	fmt.Println(10 / 4)
	var n1 float32 = 10 / 4
	fmt.Println(n1)

	//如果我们希望保留小数部分,则需要有浮点数参与运算
	var n2 float32 = 10.0 / 4
	fmt.Println(n2)

	// 演示 % 的使用
	// 看一个公式 a % b = a - a / b * b
	fmt.Println("10%3=", 10%3)     // =1
	fmt.Println("-10%3=", -10%3)   // = -10 - (-10) / 3 * 3 = -10 - (-9) = -1
	fmt.Println("10%-3=", 10%-3)   // =1
	fmt.Println("-10%-3=", -10%-3) // =-1

	// ++ 和 -- 的使用
	var i int = 10
	i++                  // 等价于i = i + 1
	fmt.Println("i=", i) // 11
	var j int = 50
	j--                  // 等价于j = j - 1
	fmt.Println("j=", j) //49
} 
```

+、-、*是一个道理,完全可以类推

## 算数运算符的细节

1、对于 / ,他的整数除和小数除是有区别的:整数之间做除法时,只保留整数部分而舍弃小数部分

2、当对一个树取模时,可以等价a%b=a-a/b*b,这样我们可以看到取模的一个本质运算

3、golang的自增自减只能当作一个独立语言使用时,不能这样使用 b := a++ 或者 b := a--

4、golang的++和--只能写在变量的后面,不能写在变量的前面,即只有 a++ a-- 没有 ++a --a

5、golang的设计者去掉c/java中的自增自减的容易混淆的写法,让golang更加简洁,统一

```go
package main
	//3、
func main() {
	//在golang中,++和--只能独立使用
	// var i int = 8
	// var a int
	// a = i++ //错误,i++只能独立使用
	// a = i-- //错误,i--只能独立使用

	// if i++ > 0 {
	// 	fmt.Println("ok")
	// }
}
```

```go
package main

import "fmt"
	//4、
func main() {
	//在golang中,++和--只能独立使用
	// var i int = 8
	// var a int
	// a = i++ //错误,i++只能独立使用
	// a = i-- //错误,i--只能独立使用

	// if i++ > 0 {
	// 	fmt.Println("ok")
	// }

	var i int = 1
	i++
	//++i // 错误,golang没有 前++
	i--
	//--i // 错误,golang没有 前--
	fmt.Println("i=", i)
}
```

## 关系运算符

1、关系运算符的结果都是bool型,也就是要是true,要么false

2、关系运算符组成的表达式,我们称为关系表达式:a>B

3、比较运算符"=="不能误写成"="

## 逻辑运算符基本使用

用于连接多个条件(一般来讲就是关系表达式),最终的结果也是一个bool值

&& 逻辑 与 运算符,如果两边的操作数都是True,则为True,否则为false

|| 逻辑 或 运算符,如果两边的操作数有一个True,则为True,否则为false

! 逻辑 非 运算符,如果条件为True,则逻辑为false,否则为True

演示使用:

```go
package main

import "fmt"

func main() {
	//演示逻辑运算符的使用 &&
	var age int = 40
	if age > 30 && age < 50 {
		fmt.Println("ok1")
	}

	if age > 30 && age < 40 {
		fmt.Println("ok2")
	}

	//演示逻辑运算符的使用 ||
	if age > 30 || age < 50 {
		fmt.Println("ok3")
	}

	if age > 30 || age < 40 {
		fmt.Println("ok4")
	}

	//演示逻辑运算符的使用 !
	if age > 30 {
		fmt.Println("ok5")
	}
	if !(age > 30) {
		fmt.Println("ok6")
	}
}
```

## 短路与和短路或

1、&&也叫短路与:如果第一个条件为flase,则第二个条件不会判断,最终结果为false

2、||也叫短路或:如果第一个条件为true,则第二个条件不会判断,最终结果为true

案例演示:

```go
package main

import "fmt"

// 声明一个函数(测试)
func test() bool {
	fmt.Println("test.....")
	return true
}

func main() {

	var i int = 10
	// 短路与
	// 说明: 因为i<9 为false,因此后面的test()就不执行
	if i < 9 && test() {
		fmt.Println("ok.....")
	}

	// 短路或
  // 说明:因为i>9 为false,因此后面的test()就不执行
	if i > 9 || test() {
		fmt.Println("hello")
	}

}
```

## 赋值运算符基本使用

赋值运算符就是将某个运算后的值,赋给指定的变量

= 简单的赋值运算符,将一个表达式的值赋给一个左值 C=A+B 将 A+B表达式结果赋值给C

+= 相加后再赋值 C += A 等于C = C + A

-= 相减后再赋值 C -= A 等于 C = C - A

*= 相乘后再赋值 C *= A 等于 C = C * A

/= 相除后再赋值 C /= A 等于 C = C / A

%= 求余后再赋值 C %= A 等于 C = C % A

案例演示赋值运算符的基本使用:

1、赋值基本案例

2、有两个变量 a 和 b,要求将其进行交换,最终打印结果

3、+=的使用案例

```go
package main

import "fmt"

func main() {
	//赋值运算符的演示
	// var i int
	// i = 10 //基本赋值

	//有两个变量,a和b,要求将其进行交换,最终打印结果
	//a = 9 , b = 2 ==> a = 2, b = 9
	a := 9
	b := 2
	fmt.Printf("交换前的情况是a=%v,b=%v\n", a, b)
	//定义一个临时变量
	t := a
	a = b
	b = t
	fmt.Printf("交换后的情况是a=%v,b=%v\n", a, b)

	//符合赋值的操作
	a += 17 // 等价于 a = a + 7
	fmt.Println("a=", a)
}
```

赋值运算符特点

1、运算顺序从右往左

2、赋值运算符的左边 只能是变量,右边 可以是变量、表达式、常量值

3、复合赋值运算符等价于下面的效果:

​	比如: a += 3 等价于 a = a + 3

```go
package main

import "fmt"

func test() int {
	return 90
}
func main() {
	//赋值运算符的演示
	// var i int
	// i = 10 //基本赋值

	//有两个变量,a和b,要求将其进行交换,最终打印结果
	//a = 9 , b = 2 ==> a = 2, b = 9
	a := 9
	b := 2
	fmt.Printf("交换前的情况是a=%v,b=%v\n", a, b)
	//定义一个临时变量
	t := a
	a = b
	b = t
	fmt.Printf("交换后的情况是a=%v,b=%v\n", a, b)

	//符合赋值的操作
	a += 17 // 等价于 a = a + 7
	fmt.Println("a=", a)

	var c int
	c = a + 3 // 赋值运算的执行顺序是从右向左
	fmt.Println(c)

	// 赋值运算符的左边 只能是变量 右边可以是变量、表达式、常量值
	// 表达式:任何有值的都可以看作表达式
	var d int
	d = a           //
	d = 8 + 2*7     // =的右边是一个表达式
	d = test() + 90 // =的右边是一个表达式
	// d = 890         //常量
	fmt.Println(d)
}

```



## 赋值运算经典面试题

有两个变量 a 和 b ,要求将其进行交换,但是不允许使用中间变量,最终打印结果

```go
package main

import "fmt"

func main() {
	//有两个变量 a 和 b ,要求将其进行交换,但是不允许使用中间变量,最终打印结果
	var a int = 10
	var b int = 20

	fmt.Printf("交换前a=%v b=%v\n", a, b)

	a = a + b
	b = a - b // b = a + b - b ==> b = a
	a = a - b // a = a + b - a ==> a = b

	fmt.Printf("a=%v b=%v", a, b)
}
```

## 其他运算符

& 返回变量存储地址

&a; 将给出变量的实际地址

*指针变量

*a; 是一个指针变量

```go
package main

import "fmt"

func main() {
	// 演示一把 & 和 * 的使用
	a := 100
	fmt.Println("a的地址是:", &a)

	var ptr *int = &a
	fmt.Println("ptr指向的值是:", *ptr)
}
```

特别说明: go语言明确不支持三元运算符,如果要用的话使用 if --- else的形式

举例说明,如果在golang中实现三元运算的效果:

```go
package main

import "fmt"

func main() {

	var n int
	var i int = 10
	var j int = 12
	// 传统的三元运算符
	// n = i > j ? i : J
	if i > j {
		n = i
	} else {
		n = j
	}
	fmt.Println("n=", n)
}
```

## 练习

1、求出两个数的最大值

2、求出三个数的最大值

```go
package main

import "fmt"

func main() {
	// 求出两个数的最大值
	var n1 int = 10
	var n2 int = 20
	var max int
	if n1 > n2 {
		max = n1
	} else {
		max = n2
	}
	fmt.Println("前两个数的最大值为:", max)

	// 求出三个数的最大值
	// 思路:先求出两个数的最大值,然后让这个最大值和第三个数比较,再求出最大值
	var n3 int = 45
	if n3 > max {
		max = n3
	}
	fmt.Println("三个数的最大值为:", max)
}
```

## 获取用户终端输入

步骤

​	1、导入fmt包

​	2、调用fmt包的fmt.Scanln()或者fmt.Scanf()

案例演示：

​	要求：可以从控制台接收用户信息，【姓名，年龄，薪水，是否及格】

​	1.使用fmt.Scanln()获取

​	2.使用fmt.Scanf()获取

```go
//方式一
package main

import (
	"fmt"
)

func main() {
	//方式1:fmt.Scanln
	//1先声明变量
	var name string
	var age byte
	var sal float32
	var isPass bool

	fmt.Println("请输入姓名")
	//当程序执行到这的时候，程序会停在这里，等待用户输入，并回车
	fmt.Scanln(&name)
	fmt.Println("请输入年龄")
	fmt.Scanln(&age)
	fmt.Println("请输入薪水")
	fmt.Scanln(&sal)
	fmt.Println("请输入是否合格")
	fmt.Scanln(&isPass)
	fmt.Printf("名字是%v \n 年龄是%v \n 薪水是%v \n 是否及格%v \n", name, age, sal, isPass)
}
```

## 计算机进制的介绍

对于整数来说,有四种表示方式:

1、二进制: 0,1  满2进1

​	在golang中,不能直接使用二进制来表示一个整数,它沿用了c的特点

2、十进制: 0-9  满10进1

3、八进制: 0-7  满8进1,以数字0开头表示

4、十六进制: 0-9、A-F 满16进1 以0x或0X开头表示, 此处A-F不区分大小写

​	如: 0x21AF + 1 = 0X21B0

```go
package main

import "fmt"

func main() {
	var i int = 5
	// 二进制输出
	fmt.Printf("%b\n", i) // %b 按二进制输出

	// 八进制
	var j int = 011 // 011 => 9
	fmt.Println("j=", j)

	// 十六进制
	var k int = 0x11 // 0x11 => 16 + 1 = 17
	fmt.Println("k=v", k)
}

```

## 其他进制转十进制

### 二进制转十进制

从最低位开始(右边的),将每个位上的数提取出来,乘以2的(位数-1)次方,然后求和

案例:请将二进制1011转成十进制的数

1011 = 1 * 2的0次方 + 1 * 2 + 0 * 2 * 2 + 1 * 2 * 2 * 2 = 1 + 2 + 0 + 8 = 11

### 八进制转十进制

从最低位开始(右边的),将每个位上的数提取出来,乘以8的(位数-1)次方,然后求和

案例:请将0123转成十进制的数

0123 = 3 * 1 + 2 * 8 + 1 * 8 * 8 = 3 + 16 + 64 = 83

### 16进制转换成十进制

从最低位开始(右边的),将每个位上的数提取出来,乘以16的(位数-1)次方,然后求和

案例:请将0x34A转成十进制的数

0x34A = 10 * 1 + 4 * 16 + 3 *16 *16 = 10 + 64 + 768 = 842

## 十进制转其它进制

### 十进制转换成二进制

将该数不断除以2,知道商为0为止,然后将每步得到的余数倒过来,就是对应的二进制

案例:请将56转成二进制

56 = 111000

### 十进制转换成八进制

将该数不断除以8,直到商为0为止,然后将每步得到的余数倒过来,就是对应的八进制

案例:请将156转成八进制

156 = 0234

### 十进制转换成十六进制

将该数不断除以16,直到商为0为止,然后将每步得到的余数倒过来,就是对应的八进制

案例:请将356转成十六进制

356 = 0x164

## 二进制转其它进制

### 二进制转八进制

将二进制数每三位一组(从低位开始组合),转成对应的八进制数即可

案例:请将二进制11010101转成八进制

11010101 = 0325

### 二进制转十六进制

将二进制数每四位一组(从低位开始组合),转成对应的八进制数即可

案例:请将二进制11010101转成十六进制

11010101 = 0xD5

## 其他进制转二进制

### 八进制转换二进制

将八进制数每一位,转成对应的一个3位的二进制数即可

案例:请将0237转成二进制

0237 = 10011111

### 十六进制转换二进制

将十六进制数每一位,转成对应的一个3位的二进制数即可

案例:请将0x237转成二进制

0x237 = 1000110111

## 位运算

在计算机内部,运行各种运算时,都是以二进制的方式来运行

### 原码、反码、补码

对于有符号的而言:

1、二进制的最高位是符号位: 0表示正数 1表示负数

2、正数的原码、反码、补码都一样

3、负数的反码 = 它的原码符号位不变,其他位取反(0 -> 1, 1->0)

4、负数的补码 = 它的反码 + 1

5、0的反码、补码都是0

6、在计算机运算的时候,都是以补码的方式来运算的

# 第五章_程序流程控制

在程序中,程序运行的流程控制决定程序是如何执行的,是我们必须掌握的,主要有三大流程控制语句

1、顺序控制

2、分支控制

3、循环控制

## 顺序控制

程序从上到下逐行地执行,中间没有任何判断和跳转

## 分支控制

让程序有选择的执行,分支控制有三种

1、单分支

2、双分支

3、多分支

### 单分支基本使用

基本语法

if 条件表达式{

​	执行代码块

}

说明: 当条件表达式为true时,就会执行{ }的代码

```go
package main

import "fmt"

func main() {
	// 编写一个程序,可以输入人的年龄,如果该同志的年龄大于18岁,则输出“你成年了”

	// 分析
	// 1.年龄 ==> var age int
	// 2.从控制台接收一个输入 fmt.Scanln(&age)
	// 3.if判断
	var age int
	fmt.Println("请输入年龄")
	fmt.Scanln(&age)
	if age > 18 {
		fmt.Println("你成年了")
	} 
}

```

### 双分支基本使用

说明:当条件表达式成立,即执行代码块1,否则执行代码块2

```go
package main

import "fmt"

func main() {
	// 编写一个程序,可以输入人的年龄,如果该同志的年龄大于18岁,则输出“你成年了”

	// 分析
	// 1.年龄 ==> var age int
	// 2.从控制台接收一个输入 fmt.Scanln(&age)
	// 3.if判断
	var age int
	fmt.Println("请输入年龄")
	fmt.Scanln(&age)
	if age > 18 {
		fmt.Println("你成年了")
	} else {
		fmt.Println("你输的撒?")
	}
}

```

### 多分支基本使用

说明:多分支的判断流程如下

1、先判断条件表达式1是否成立,如果为真,就执行代码块1

2、如果条件表达式1如果为假,就去判断条件表达式2是否成立,如果条件表达式2为真,就执行代码块2

3、依此类推

4、如果所有的条件表达式不成立,则执行else的语句块

注意:

else不是必须的

多分支只能有一个执行入口

```go
package main

import "fmt"

func main() {
	var cj int
	fmt.Println("请输入考试成绩:")
	fmt.Scanln(&cj)
	if cj == 100 {
		fmt.Println("奖励一辆BMW")
	} else if cj > 80 && cj <= 99 {
		fmt.Println("奖励一台ip7Plus")
	} else if cj >= 60 && cj <= 80 {
		fmt.Println("奖励一个ipad")
	} else {
		fmt.Println("撒也木有!!!")
	}
}
```

## 嵌套分支

在一个分支结构中又完整的嵌套了另一个完整的分支结构,里面的分支的结构称为内层分支外面的分支结构称为外层分支

说明: 嵌套分支不宜过多,最多我们建议控制在3层

## switch基本使用

1、switch语句用于基于不同条件执行不同动作,每一个case分支都是唯一的,从上到下逐一测试,直到匹配为止

2、匹配项后面也不需要再加break

语法:

switch 表达式 {

​	case 表达式1,表达式2:

​	case 表达式3,表达式4:

​	//这里可以有多个case语句

​	default:

​		语句块

}

说明:

1、golang的case后的表达式可以有多个,使用 逗号 间隔

2、golang中的case语句块不需要写break,因为默认会有,即当程序执行完case语句块后,就直接退出该switch控制结构

```go
package main

import "fmt"

func main() {
	var week byte
	fmt.Println("请输入暗号:")
	fmt.Scanf("%c", &week)
	switch week {
	case 'a':
		fmt.Println("对应星期一")
	case 'b':
		fmt.Println("星期二")
	default:
		fmt.Println("输入无效")
	}
}

```

## switch使用细节

1、case是一个表达式(即:常量值、变量、一个有返回值的函数等都可以)

2、case后的各个表达式的值的数据类型,必须和switch的表达式数据类型一致

3、case后面可以带多个表达式,使用逗号间隔

4、case后面的表达式如果是常量值(字面量),则要求不能重复

5、csse后面不需要带break,程序匹配到一个case后就会执行对应的代码块,然后退出switch,如果一个都匹配不到,则执行default

6、default语句不是必须的

7、switch的数据类型要与case的数据类型保持一致,否则报错

8、switch后也可以不带表达式,蕾丝if---else分支来使用

9、switch后也可以直接声明/定义一个变量,分号结束(不推荐)

10、switch穿透-fallthrough,如果在case语句块后增加fallthrough,则会继续执行下一个case,也叫switch穿透(默认只能穿透一层)

```go
var num int = 10
	switch num {
	case 10:
		fmt.Println("ok1")
		fallthrough // 默认只能穿透一层
	case 20:
		fmt.Println("ok2")
		fallthrough
	case 30:
		fmt.Println("ok3")
	default:
		fmt.Println("NoSerach")
	}
```

## Type switch

type switch: switch语句还可以被用于type-switch来判断某个interface变量中实际指向的变量类型

```go
package main

import "fmt"

func main() {
	var x interface{}
	var y = 10.0
	x = y
	switch i := x.(type) {
	case nil:
		fmt.Printf("x的类型~:%T", i)
	case int:
		fmt.Printf("x是int型")
	case float64:
		fmt.Printf("x是float64型")
	case func(int) float64:
		fmt.Printf("x是func(int)型")
	case bool, string:
		fmt.Printf("x是bool或者string型")
	default:
		fmt.Printf("未知类型")
	}

}

```

## for循环控制

听其名而知其意,就是让你的代码可以循环的执行

```go
package main

import (
	"fmt"
)

func main() {
	// 输出10句'gonb'

	// golang中,有循环控制语句来处理循环的执行某段代码的方法 -> for循环
	// for循环快速入门
	for i := 1; i <= 10; i++ {
		fmt.Println("gonb", i)
	}

	// for循环的第二种写法
	j := 1 //循环变量初始化
	for j <= 10 {
		fmt.Println("golangnb", j)
		j++
	}

	// for循环的第三种写法,这种写法通常会配合break使用
	k := 1
	for {
		if k <= 10 {
			fmt.Println("ok~", k)
		} else {
			break
		}
		k++
	}

  // 字符串遍历方式1 传统方式(中文会乱码)
	var str string = "hello,world!"
	for i := 0; i < len(str); i++ {
		fmt.Printf("%c\n", str[i]) // 使用到下标
	}

  // 字符串遍历方式2 for-range(中文不乱码)
	str = "abc-ok上海"
	for index, val := range str {
		fmt.Printf("index=%d,val=%c \n", index, val)
	}
}

```

注意:如果我们的字符串含有中文,那么传统的遍历字符串方式,就是错误,会出现乱码,原因是传统的对字符串的遍历是按照字节来遍历,而一个汉字在utr8编码是对应3个字节

如何解决: 需要将 str 转成 []rune 切片   => 体验一把

```go
	// []rune(str)切片遍历方式
	var str string = "hello,world!北京"
	str2 := []rune(str) // 就是把str转成 []rune
	for i := 0; i < len(str2); i++ {
		fmt.Printf("%c\n", str2[i]) // 使用到下标
	}
```

对于for-range遍历方式而言,是按照字符的方式遍历,因此如果字符串有中文,也是ok

## for循环练习题

1、打印1~100之间所有是9的倍数的整数的个数及总和

```go
package main

import "fmt"

// 打印1~100之间所有是9的倍数的整数的个数及总和
func main() {
	var max = 100
	var count int = 0
	var sum int = 0
	for i := 1; i <= max; i++ {
		if i%9 == 0 {
			count++
			sum += i
			fmt.Println("当前找到的数字是:", i)
			fmt.Println("当前累计的和是:", sum)
		}
	}
	fmt.Println("0-100中9的倍数的个数:", count)
	fmt.Println("0-100中9的倍数的数字之和是:", sum)
}
```

2、完成下面的表达式输出,6是可变的

0 + 6 = 6

1 + 5 = 6

2 + 4 = 6

3 + 3 = 6

4 + 2 = 6

5 + 1 = 6

6 + 0 = 6

```go
// 完成下面的表达式输出,6是可变的
	var n int = 6
	for i := 0; i <= n; i++ {
		fmt.Printf("%v + %v = %v \n", i, n-i, n)
	}
```

## while和dowhile控制

go语言没有while和do...while语法,这一点需要注意

如果我们需要使用类似其他语言(java/c的while和do...while),可以通过for循环来实现其使用效果

while 和 do...while的实现:

```go
package main

import "fmt"
package main

import "fmt"

func main() {
	// 使用while方式输出10句“hello,world”
	// 循环变量初始化
	var i int = 1
	for {
		if i > 10 {
			break // 跳出for循环,结束for循环
		}
		fmt.Println("hello,world!", i)
		i++ // 循环变量的迭代
	}

	// 使用do...while方式输出10句“hello,world”
	var j int = 1
	for {
		fmt.Println("hello,ok", j)
		j++
		if j > 10 {
			break
		}
	}
}

```

## 多重循环控制(重点,难点)

1、将一个循环放在另一个循环体内,就形成了嵌套循环,在外边的for称为外层循环在里面的for循环称为内层循环(建议一般使用两层,最多不要超过3层)

2、实质上,嵌套循环就是把内层循环当成外层循环的循环体,当只有内层循环的循环条件为false时,才会完全跳出内层循环,才可结束外层的当次循环,开始下一次的循环

3、外层循环次数为m次,内层为n次,则内层循环体实际上需要执行m*n=mn次

编程两大绝招

1、先易后难:即将一个复杂的问题分解成简单的问题

2、先死后活:即先把代码写死,再用变量做活

```go
package main

import "fmt"

func main() {
	// 1、统计3个班成绩情况,每个班有5名学生
	// 求出各个班的平均分和所有班级的平均分[学生的成绩从控制台输入]

	// 分析实现思路_1
	// 1、统计1个班成绩情况,每个班有5名学生,求出该班的平均分[学生成绩从控制台输入] ==》先易后难
	// 2、学生数就是5个 ==》先死后活
	// 3、声明一个sum变量统计总分计算平均分

	// 分析实现思路_2
	// 1、统计3个班成绩情况,每个班有5名学生,求出各个班的平均分和所有班级的平均分[学生的成绩从控制台输入]
	// 2、j表示第几个班级
	// 3、定义一个变量存放总成绩

	// 分析实现思路_3
	// 1、我们可以把代码做活
	// 2、定义两个变量,表示班级的个数和班级的人数

	// 统计三个班及格人数,每个班有5名同学
	// 分析思路
	// 1、声明一个变量passCount用于保存及格人数

	var classNum int = 2
	var stuNum int = 3
	var totalsum float64 = 0.0
	var passCount int = 0
	for j := 1; j <= classNum; j++ {
		sum := 0.0
		for i := 1; i <= stuNum; i++ {
			var scoure float64
			fmt.Printf("请输入第%d个班 第%d个学生的成绩\n", j, i)
			fmt.Scanln(&scoure)
			// 累计总分
			sum += scoure
			// 判断分数是否及格
			if scoure >= 60 {
				passCount++
			}
		}
		fmt.Printf("第%v个班级总分为:%v\n", j, sum)
		totalsum += sum
		fmt.Printf("第%v个班级平均分:%v\n", j, sum/float64(stuNum))
	}
	fmt.Printf("各个班的总成绩是:%v", totalsum)
	fmt.Printf("各个班的平均成绩是:%v", totalsum/(float64(stuNum)*float64(classNum)))
	fmt.Printf("三个班的及格人数是:%v", passCount)
}
```

## 经典案例打印空心金字塔

```go
package main

import "fmt"

func main() {
	// 使用for循环编写一个程序,可以接受一个整数,表示层数,打印出金字塔

	// 编程思路
	// 1、打印一个矩形
	// 2、打印半个金字塔
	// 3、打印整个金字塔
	// 4、做活:将层数做成一个变量
	// 5、打印空心金字塔
	// 分析:在我们给每行打印*号时,需要考虑是打印*还是打印空格
	// 我们分析的结果是每层的第一个和最后一个是打印*,其他就应该是空的,即输出空格
	// 我们还分析到一个例外情况,最后层(底层)是全部打印*

	var totalLevel int = 20
	// i表示层数
	for i := 1; i <= 3; i++ {
		// j表示每层打印多少个*
		for j := 1; j <= 3; j++ {
			fmt.Print("*")
		}
		fmt.Println()

	}
	for i := 1; i <= 3; i++ {
		// j表示每层打印多少个*
		for j := 1; j <= i; j++ {
			fmt.Print("*")
		}
		fmt.Println()

	}
	for i := 1; i <= totalLevel; i++ {
		// 在打印*前先打印空格
		for k := 1; k <= totalLevel-i; k++ {
			fmt.Print(" ")
		}
		// j表示每层打印多少个*
		for j := 1; j <= 2*i-1; j++ {
			fmt.Print("*")
		}
		fmt.Println()

	}
	for i := 1; i <= totalLevel; i++ {
		// 在打印*前先打印空格
		for k := 1; k <= totalLevel-i; k++ {
			fmt.Print(" ")
		}
		// j表示每层打印多少个*
		for j := 1; j <= 2*i-1; j++ {
			if j == 1 || j == 2*i-1 || i == totalLevel {
				fmt.Print("*")
			} else {
				fmt.Print(" ")
			}
		}
		fmt.Println()

	}

}

```

## 经典案例九九乘法表

```go
package main

import "fmt"

// 打印九九乘法表
func main() {
	// 变量控制层
	var numLevel int = 9
	for i := 1; i <= numLevel; i++ {
		for j := 1; j <= i; j++ {
			fmt.Printf("%v * %v = %v\t", j, i, i*j)
			if i == j {
				fmt.Println()
			}
		}
	}
}

```

## break引入和快速入门

需求: 随机生成1-100的一个数,直到生成了99这个数,看看你一共用了几次?

分析: 编写一个无限循环的控制,然后不停的随机生成数,当生成了99时,就退出这个无限循环 ==》 break  

这里我们给大家说一下,如何随机生成1-100整数

```go
package main

import (
	"fmt"
	"math/rand"
	"time"
)

func main() {
	// // 我们为了生成一个随机数,还需要给rand设置一个种子
	// // time.Now().Unix()  :  返回一个从1970年1月1日 0时0分0秒到现在的秒数
	fmt.Println(time.Now().Unix())
	rand.Seed(time.Now().Unix())
	// // 如何随机生成1-100的整数
	n := rand.Intn(100) + 1 // [100)
	fmt.Println(n)

	// 随机生成0-100的一个数,直到生成了99这个数,看看你一共用了几次
	// 分析思路
	// 编写一个无限循环的控制,然后不停的随机生成数,当生成了99时,就退出这个无限循环 ==》 break
	var cishu int = 0
	for {
		rand.Seed(time.Now().UnixNano())
		// 如何随机生成1-100的整数
		m := rand.Intn(100) + 1
		if m == 99 {
			fmt.Printf("生成到了99用了%v次", cishu)
			break
		} else {
			fmt.Println("当前生成的随机数是:", m)
			cishu++
		}
	}
}
```

## break语法和流程图

break语句用于终止某个语句块的执行,用于中断当前for循环或跳出switch语句

## break注意事项和细节说明

break语句出现在多层嵌套的语句块中时,可以通过标签指明要终止的是哪一层语句块

```go
// 演示一下指定标签的形式来使用break
lable2:
	for i := 0; i < 4; i++ {
		// lable1: // 设置一个标签
		for j := 0; j < 10; j++ {
			if j == 2 {
				// break // brea默认会跳出最近的for循环
				// break lable1
				break lable2
			}
			fmt.Println("j=", j)
		}
	}
```

对上面案例的说明:

1、break默认会跳出最近的for循环

2、break后面可以指定标签,跳出标签对应的for循环

## break练习题

1、100以内的数求和,求出 当和 第一次大于20的当前数

2、实现登陆验证,有三次机会,如果用户为“张三”,密码为“888”提示登陆成功,否则提示还有几次机会

```go
package main

import "fmt"

func main() {
	// 1、100以内的数求和,求出 当和 第一次大于20的当前数
	var sum int = 0
	for i := 1; i <= 100; i++ {
		sum += i // 求和
		if sum > 20 {
			fmt.Printf("100以内的数求和,当和第一次大于20的当前数为:%v\n", i)
			break
		}

	}

	// 2、实现登陆验证,有三次机会,如果用户为“张三”,密码为“888”提示登陆成功,否则提示还有几次机会
	var id string
	var pwd string
	var jihui int = 3
	for i := 1; i <= jihui; i++ {
		fmt.Println("请输入你的账号:")
		fmt.Scanln(&id)
		fmt.Println("请输入你的密码:")
		fmt.Scanln(&pwd)
		if id == "张三" && pwd == "888" {
			fmt.Println("登陆成功")
			break
		} else if jihui-i == 0 {
			fmt.Println("对不起,三次机会已用尽,账号已被锁定!")
		} else {
			fmt.Printf("对不起,输入错误,你还有%v次机会\n", jihui-i)
		}
	}
}

```

## continue介绍

1、continue语句用于结束本次循环,继续执行下一次循环

2、continue语句出现在多层嵌套的循环语句体中时,可以通过标签指明要跳过的是哪一层循环,这个和前面的标签的使用的规则一样

## continue执行流程分析

```go
package main

import "fmt"

func main() {
	// continue案例
	// lable2:
	for i := 0; i < 4; i++ {
		for j := 0; j < 10; j++ {
			if j == 2 {
				continue
			}
			fmt.Println("j=", j)
		}
	}
}

```

## goto和return

1、go语言的goto语句可以无条件地转移到程序中指定的行

2、goto语句通常与条件语句配合使用,可用来实现条件转移,跳出循环体等功能

3、在go程序设计中一般不主张使用goto语句,以免造成程序流程的混乱,使理解和调试程序都产生困难

```go
package main

import "fmt"

func main() {
	// 演示 goto 的使用
	var n int = 30
	fmt.Println("ok1")
	if n > 20 {
		goto label1
	}
	fmt.Println("ok2")
	fmt.Println("ok3")
	fmt.Println("ok4")
label1:
	fmt.Println("ok5")
}

```

return使用在方法或者函数中,表示跳出所在的方法或函数

1、如果return是在普通的函数,则表示跳出该函数,即不再执行函数中return后面代码,也可以理解成终止函数

2、如果return是在main函数,表示终止main函数,也就是说终止程序

```go
// 演示 return 的使用
	var n int = 30
	fmt.Println("ok1")
	if n > 20 {
		return
	}
	fmt.Println("ok2")
	fmt.Println("ok3")
	fmt.Println("ok4")
	fmt.Println("ok5")
```

# 第六章_函数、包、错误处理

## 为什么需要函数

输入两个数,再输入一个运算符(+-*/),得到结果

```go
package main

import (
	"fmt"
)

func main() {
	// 输入两个数,再输入一个运算符(+-*/),得到结果

	var n1 float64
	var n2 float64
	var operator byte
	var res float64
	fmt.Println("请输入第一个数")
	fmt.Scanln(&n1)
	fmt.Println("请输入第二个数")
	fmt.Scanln(&n2)
	fmt.Println("请输入运算符+-*/")
	fmt.Scanln(&operator)
	switch operator {
	case '+':
		res = n1 + n2
	case '-':
		res = n1 - n2
	case '*':
		res = n1 * n2
	case '/':
		res = n1 / n2
	default:
		fmt.Println("输入有误.....")
	}
	fmt.Println("本次计算结果为:", res)
}

```

分析上面的代码

1、上面的写法是可以完成功能,但是代码冗余

2、同时不利于代码维护

3、函数可以解决这个问题

## 函数介绍和应用案例

为完成某一功能的程序指令(语句)的集合,称为函数

在go中,函数分为:自定义函数、系统函数(查看go编程手册)

函数语法:

1、形参列表:表示函数的输入

2、函数中的语句:表示为了实现某一功能代码块

3、函数可以有返回值,也可以没有

函数的快速入门案例:使用函数解决前面的计算问题:

```go
package main

import (
	"fmt"
)

// 将计算的功能,放到一个函数中,然后在需要使用时调用即可
func cal(n1 float64, n2 float64, operator byte) float64 {
	var res float64
	switch operator {
	case '+':
		res = n1 + n2
	case '-':
		res = n1 - n2
	case '*':
		res = n1 * n2
	case '/':
		res = n1 / n2
	default:
		fmt.Println("输入有误.....")
	}
	return res
}

func main() {
	// 输入两个数,再输入一个运算符(+-*/),得到结果

	var n1 float64 = 1.2
	var n2 float64 = 2.3
	var operator byte = '+'
	result := cal(n1, n2, operator)
	fmt.Println("本次计算结果为:", result)
}
```

## 包的引出和使用原理

1、在实际开发中,我们往往需要在不同的文件中,去调用其他文件定义的函数,比如main.go中,去使用utils,go文件中的函数,如何实现?

2、现在有两个程序员共同开发一个Go项目,程序员xiaoming希望定义函数Cal,程序员xiaoqiang也想定义函数也叫Cal,两个程序员为此还吵了起来,怎么办?

包的原理:

包的本质实际上就是创建不同的文件夹,来存放程序文件

## 包的快速入门

说明:go的每一个文件都是属于一个包的,也就是说go是以包的形式来管理文件和项目目录结构的

包的三大作用：

1、区分相同名字的函数、变量等标识符

2、当程序文件很多时，可以很好的管理项目

3、控制函数、变量等访问范围，即作用域

包的相关说明：

打包基本语法： package util（包名）

引入包的基本语法：import "包的路径"

```go
package main

import (
	"fmt"
	util "goproject/src/go_code/chapter06/fundemo01/utils" //给包起别名
)

func main() {
	// 输入两个数,再输入一个运算符(+-*/),得到结果

	var n1 float64 = 1.2
	var n2 float64 = 2.3
	var operator byte = '*'
	result := utils.Cal(n1, n2, operator)
	fmt.Printf("本次计算结果为:%.2f", result)
}

```

```go
package utils

import "fmt"

// 将计算的功能,放到一个函数中,然后在需要使用时调用即可
// 为了让其它包的文件使用Cal函数，需要将首字母大写，类似其它语言的public（公有）
func Cal(n1 float64, n2 float64, operator byte) float64 {
	var res float64
	switch operator {
	case '+':
		res = n1 + n2
	case '-':
		res = n1 - n2
	case '*':
		res = n1 * n2
	case '/':
		res = n1 / n2
	default:
		fmt.Println("输入有误.....")
	}
	return res
}

```



## 包使用注意事项和细节

1、在给一个文件打包时，该包对应一个文件夹，比如这里的utils文件夹对应的包名就是utils，文件的包名通常和文件所在的文件夹名一致，一般为小写字母

2、当一个文件要使用其他包函数或变量时，需要先引入对应的包

3、为了让其它包的文件，可以访问到本包的函数，则该函数名的首字母需要大写，类似其它语言的public，这样才能跨包访问

4、在访问其他包函数时，其语法是 包名.函数名

5、如果包名较长，Go支持给包取别名，注意细节，取别名后，原来的包名就不能使用了（引入路径前直接写一个变量）

```go
import (
	"fmt"
	util "goproject/src/go_code/chapter06/fundemo01/utils" //给包起别名
)
```

6、在同一个包下（同一个文件夹），不能有相同的函数名（也不能有相同的全局变量名），否则报重复定义

7、如果你要编译成一个可执行程序文件，就需要将这个包声明为main，即package main，这个就是一个语法规范，如果你是写一个库，包名可以自定义

## 函数_递归调用

一个函数在函数体内又调用了本身，我们称之为递归调用

```go
package main

import "fmt"

func test(n int) {
	if n > 2 {
		n--
		test(n)
	}
	fmt.Println("n=", n)
}

func test2(n int) {
	if n > 2 {
		n--
		test2(n)
	} else {
		fmt.Println("n=", n)
	}
}

func main() {
	// 看一段代码
	test(4)
	test2(4)
}

```

函数递归需要遵守的重要原则：

1、执行一个函数时，就创建一个新的受保护的独立空间（新函数栈）

2、函数的局部变量是独立的，不会相互影响

3、递归必须向退出递归的条件逼近，否则就是无限递归，死龟了

4、当一个函数执行完毕，或者遇到return，就会返回，遵守谁调用，就将结果返回给谁，同时当函数执行完毕或者返回时，该函数本身也会被系统销毁

## 函数_递归调用练习题

1、斐波那契数

请使用递归的方式，求出斐波那契数1，1，2，3，5，8，13...

给你一个整数n，求出它的斐波那契数是多少？

```go
package main

import "fmt"

// 写一个函数
// 1、斐波那契数
// 请使用递归的方式，求出斐波那契数1，1，2，3，5，8，13...
// 给你一个整数n，求出它的斐波那契数是多少？
func fbn(n int) int {
	if n == 1 || n == 2 {
		return 1
	} else {
		return fbn(n-1) + fbn(n-2)
	}
}

func main() {
	// 测试
	res := fbn(3)
	fmt.Println("res=", res)
	fmt.Println("res=", fbn(4))
	fmt.Println("res=", fbn(5))
	fmt.Println("res=", fbn(6))
}
```

2、求函数值

已知f(1) = 3; f(n) = 2*f(n-1)+1

请使用递归的思想编程，求出f(n)的值？

```go
package main

import "fmt"

// 2、求函数值
// 已知f(1) = 3; f(n) = 2*f(n-1)+1
// 请使用递归的思想编程，求出f(n)的值？

func f(n int) int {
	if n == 1 {
		return 3
	} else {
		return 2*f(n-1) + 1
	}
}

func main() {
	// 测试一下
	fmt.Println("f(1)=", f(1))
	fmt.Println("f(5)=", f(5))
}

```

3、猴子吃桃子问题

有一堆桃子，猴子第一天吃了其中的一半，并再多一了一个！以后每天猴子都吃其中的一半，然后再多吃一个。当到第十天时，想再吃时（还没吃），发现只有一个桃子了。问题：最初共有多少个桃子？

思路分析：

1、第10天只有一个桃子

2、第9天有几个桃子 ==》 （第10天的桃子数量 + 1） * 2

3、规律：第n天的桃子数量 = （（第n天的桃子数量+1）+1） * 2

```go
package main

import "fmt"

// 3、猴子吃桃子问题
// 有一堆桃子，猴子第一天吃了其中的一半，并再多一了一个！以后每天猴子都吃其中的一半，然后再多吃一个。
// 当到第十天时，想再吃时（还没吃），发现只有一个桃子了。问题：最初共有多少个桃子？
// 思路分析：
// 1、第10天只有一个桃子
// 2、第9天有几个桃子 ==》 （第10天的桃子数量 + 1） * 2
// 3、规律：第n天的桃子数量 = （第n天的桃子数量+1）+1 * 2

func peach(n int) int {
	if n > 10 || n < 1 {
		fmt.Println("天数不对")
		return 0 // 返回0表示没有得到正确的数量
	}
	if n == 10 {
		return 1
	} else {
		return (peach(n+1) + 1) * 2
	}
}

var sum int = 0

func main() {
	for i := 1; i <= 10; i++ {
		fmt.Printf("第%v天桃子的数量是%v\n", i, peach(i))
		sum += peach(i)
	}
	fmt.Println("最初桃子的数量是：", peach(1))
}
```

## 函数注意事项和细节

1、函数的形参列表可以是多个，返回值列表也可以是多个

2、形参列表和返回值列表的数据类型可以是值类型和引用类型

3、函数的命名遵循标识符命名规范，首字母不能是数字，首字母大写该函数可以被本包文件和其它包文件使用，类似public，首字母小写，只能被本包文件使用，其他包文件不能使用，类似private

4、函数中的变量是局部的，函数外不生效

```go
package main
import "fmt"
//函数中的变量是局部的，函数外不生效
func test() {
	// n1是test函数的局部变量，只能在test()函数中使用
	var n1 int = 10
}
func main() {
	// 这里不能使用n1，因为n1是test()函数的局部变量
	fmt.Println(n1)
}
```

5、基本数据类型和数组默认都是值传递的，即进行值拷贝。在函数内修改，不会影响到原来的值

```go
package main

import "fmt"

//函数中的变量是局部的，函数外不生效

//func test() {
//n1是test函数的局部变量，只能在test()函数中使用
// var n1 int = 10
//}
func test02(n1 int) {
	n1 = n1 + 10
	fmt.Println("test02() n1 = ", n1)
}

func main() {
	num := 20
	test02(num)
	fmt.Println("main() num=", num)
}
```

6、如果希望函数内的变量能修改函数外的变量（指的是默认以值传递的方式的数据类型），可以传入变量的地址&，函数内以指针的方式操作变量，从效果上看类似引用

```go
package main

import "fmt"


// n1 就是 *int 类型
func test03(n1 *int) {
	*n1 = *n1 + 10
	fmt.Println("test03() n1=", *n1)
}

func main() {
	num := 20
	fmt.Println("num的地址：", &num)
	test02(num)
	fmt.Println("main() num=", num)

	test03(&num)

}
```

7、Go函数不支持函数重载（下方代码报错：重复定义）

```go
func test02(n1 int) {
	n1 = n1 + 10
	fmt.Println("test02() n1 = ", n1)
}

func test02(n1 int, n2 int) {

}
```

8、在go中，函数也是一种数据类型，可以赋值给一个变量，则该变量就是一个函数类型的变量了。 通过该变量可以对函数调用

```go
package main

import "fmt"

//在go中，函数也是一种数据类型，可以赋值给一个变量，则该变量就是一个函数类型的变量了。 通过该变量可以对函数调用

func getsum(n1 int, n2 int) int {
	return n1 + n2
}
func main() {
	a := getsum
	fmt.Printf("a的类型是：%T，getsum函数的类型是%T\n", a, getsum)

	res := a(10, 40) // 等价 res := getsum(10,40)
	fmt.Println("res=", res)
}
```

9、函数既然是一种数据类型，因此在go中，函数可以作为形参，并且调用

```go
package main

import "fmt"

// 在go中，函数也是一种数据类型，可以赋值给一个变量，则该变量就是一个函数类型的变量了。 通过该变量可以对函数调用

func getsum(n1 int, n2 int) int {
	return n1 + n2
}

// 函数既然是一种数据类型，因此在go中，函数可以作为形参，并且调用
// func(int,int) int是funvar的函数数据类型 表达方式
// 把一个函数func(int,int) int 交给一个形参funvar
// 通过形参调用：funvar(num1,num2)
func myFun(funvar func(int, int) int, num1 int, num2 int) int {
	return funvar(num1, num2)
}

func main() {
	a := getsum
	fmt.Printf("a的类型是：%T，getsum函数的类型是%T\n", a, getsum)

	res := a(10, 40) // 等价 res := getsum(10,40)
	fmt.Println("res=", res)

	// 看案例
	res2 := myFun(getsum, 50, 60)
	fmt.Println("res2=", res2)

}
```

10、为了简化数据类型定义，go支持自定义数据类型（相当于起一个别名）

```go
	// 给int取了别名，在go中 myInt 和 int 虽然都是int类型，但是go认为myInt和int还是两个类型
	type myInt int
	var num1 myInt = 0
	var num2 int
	num1 = 40
	num2 = int(num1) // 注意：这里依然需要显式转换
	fmt.Println("num1=", num1)
	fmt.Println("num2=", num2)
```

```go
package main

import (
	"fmt"
)

// 在go中，函数也是一种数据类型，可以赋值给一个变量，则该变量就是一个函数类型的变量了。 通过该变量可以对函数调用

func getsum(n1 int, n2 int) int {
	return n1 + n2
}

// 再加一个案例
// 这时 myFun 就是func(int,int) int类型
type myFunType func(int, int) int

// 函数既然是一种数据类型，因此在go中，函数可以作为形参，并且调用
// func(int,int) int是funvar的函数数据类型 表达方式
// 把一个函数func(int,int) int 交给一个形参funvar
// 通过形参调用：funvar(num1,num2)
func myFun2(funvar myFunType, num1 int, num2 int) int {
	return funvar(num1, num2)
}

func main() {
	a := getsum
	fmt.Printf("a的类型是：%T，getsum函数的类型是%T\n", a, getsum)

	res := a(10, 40) // 等价 res := getsum(10,40)
	fmt.Println("res=", res)

	// 看案例
	res2 := myFun2(getsum, 50, 60)
	fmt.Println("res2=", res2)

	// 给int取了别名，在go中 myInt 和 int 虽然都是int类型，但是go认为myInt和int还是两个类型
	type myInt int
	var num1 myInt = 0
	var num2 int
	num1 = 40
	num2 = int(num1) // 注意：这里依然需要显式转换
	fmt.Println("num1=", num1)
	fmt.Println("num2=", num2)

	// 看案例
	res3 := myFun2(getsum, 500, 600)
	fmt.Println("res3=", res3)
}
```

11、支持对函数返回值命名

```go
package main

import (
	"fmt"
)

// 在go中，函数也是一种数据类型，可以赋值给一个变量，则该变量就是一个函数类型的变量了。 通过该变量可以对函数调用

func getsum(n1 int, n2 int) int {
	return n1 + n2
}

// 再加一个案例
// 这时 myFun 就是func(int,int) int类型
type myFunType func(int, int) int

// 函数既然是一种数据类型，因此在go中，函数可以作为形参，并且调用
// func(int,int) int是funvar的函数数据类型 表达方式
// 把一个函数func(int,int) int 交给一个形参funvar
// 通过形参调用：funvar(num1,num2)
func myFun2(funvar myFunType, num1 int, num2 int) int {
	return funvar(num1, num2)
}

// 支持对函数返回值命名
func getSumAndSub(n1 int, n2 int) (sum int, sub int) {
	sum = n1 + n2
	sub = n1 - n2
	return
}
func main() {
	a := getsum
	fmt.Printf("a的类型是：%T，getsum函数的类型是%T\n", a, getsum)

	res := a(10, 40) // 等价 res := getsum(10,40)
	fmt.Println("res=", res)

	// 看案例
	res2 := myFun2(getsum, 50, 60)
	fmt.Println("res2=", res2)

	// 给int取了别名，在go中 myInt 和 int 虽然都是int类型，但是go认为myInt和int还是两个类型
	type myInt int
	var num1 myInt = 0
	var num2 int
	num1 = 40
	num2 = int(num1) // 注意：这里依然需要显式转换
	fmt.Println("num1=", num1)
	fmt.Println("num2=", num2)

	// 看案例
	res3 := myFun2(getsum, 500, 600)
	fmt.Println("res3=", res3)

	// 看案例
	a1, b1 := getSumAndSub(1, 2)
	fmt.Printf("a=%v,b=%v\n", a1, b1)
}
```

12、使用 _ 标识符，忽略返回值

13、go支持可变参数

​	args是slice切片，通过args[index]可以访问到各个值

​	args是起的名字（通常情况下都用args），可以随便取

​	如果一个函数的形参列表中有可变参数，则可变参数要放在形参列表里面的最后一个

```go
package main

import (
	"fmt"
)

// 在go中，函数也是一种数据类型，可以赋值给一个变量，则该变量就是一个函数类型的变量了。 通过该变量可以对函数调用

func getsum(n1 int, n2 int) int {
	return n1 + n2
}

// 再加一个案例
// 这时 myFun 就是func(int,int) int类型
type myFunType func(int, int) int

// 函数既然是一种数据类型，因此在go中，函数可以作为形参，并且调用
// func(int,int) int是funvar的函数数据类型 表达方式
// 把一个函数func(int,int) int 交给一个形参funvar
// 通过形参调用：funvar(num1,num2)
func myFun2(funvar myFunType, num1 int, num2 int) int {
	return funvar(num1, num2)
}

// 支持对函数返回值命名
func getSumAndSub(n1 int, n2 int) (sum int, sub int) {
	sum = n1 + n2
	sub = n1 - n2
	return
}

// 案例演示：编写一个函数sum，可以求出 1到多个int的和
// 演示可变参数的使用
// args是起的名字（通常情况下都用args），可以随便取
// 可变参数要放在形参列表里面的最后一个
func sum(n1 int, args ...int) int {
	sum := n1
	// 遍历args
	for i := 0; i < len(args); i++ {
		sum += args[i] // args[0] 表示取出args切片的第一个元素值，其它依此类推
	}
	return sum
}
func main() {
	a := getsum
	fmt.Printf("a的类型是：%T，getsum函数的类型是%T\n", a, getsum)

	res := a(10, 40) // 等价 res := getsum(10,40)
	fmt.Println("res=", res)

	// 看案例
	res2 := myFun2(getsum, 50, 60)
	fmt.Println("res2=", res2)

	// 给int取了别名，在go中 myInt 和 int 虽然都是int类型，但是go认为myInt和int还是两个类型
	type myInt int
	var num1 myInt = 0
	var num2 int
	num1 = 40
	num2 = int(num1) // 注意：这里依然需要显式转换
	fmt.Println("num1=", num1)
	fmt.Println("num2=", num2)

	// 看案例
	res3 := myFun2(getsum, 500, 600)
	fmt.Println("res3=", res3)

	// 看案例
	a1, b1 := getSumAndSub(1, 2)
	fmt.Printf("a=%v,b=%v\n", a1, b1)

	// 案例演示：编写一个函数sum，可以求出 1到多个int的和
	// 测试一下可变参数的使用
	res4 := sum(10, 0, 90, -1, 10, 100)
	fmt.Println("res4=", res4)
}
```



## 函数练习题

请编写一个函数swap(n1 *int,n2 *int)可以变换n1和n2的值

```go
package main
import "fmt"
// 请编写一个函数swap(n1 *int,n2 *int)可以变换n1和n2的值
func swap(n1 *int, n2 *int) {
	// 定义一个临时变量
	t := *n1
	*n1 = *n2
	*n2 = t
}
func main() {
	a := 10
	b := 20
	fmt.Printf("默认的值是：a=%v,b=%v\n", a, b)
	swap(&a, &b) // 传入的是地址
	fmt.Printf("a=%v b=%v\n", a, b)
}

```

## init函数

每一个源文件都可以包含一个init函数，该函数会在main函数执行前，被go运行框架调用，也就是说init会在main函数前被调用

```go
package main
import "fmt"
// init函数，通常可以在init函数中完成初始化工作
func init() {
	fmt.Println("init()...")
}
func main() {
	fmt.Println("main()...")
}

```

## init函数的注意事项和细节

1、如果一个文件同时包含全局变量定义，init函数和main函数，则执行的流程是 变量定义->init函数->main函数

```go
package main

import "fmt"

var age = test()

// 为了看到全局变量是先被初始化的，我们这里先写一个函数
func test() int {
	fmt.Println("test()") // 1
	return 90
}

// init函数，通常可以在init函数中完成初始化工作
func init() {
	fmt.Println("init()...") // 2
}
func main() {
	fmt.Println("main()...", age) // 3
}
```

2、init函数最主要的作用，就是完成一些初始化的工作

```go
package utils

import "fmt"

var Age int
var Name string

// Age 和 Name 全局变量，我们需要在main.go使用
// 但是我们需要初始化 Age 和 Name

// init 函数完成初始化工作
func init() {
	fmt.Println("utils包里的 init()...")
	Age = 100
	Name = "tom"
}

```

```go
package main

import (
	"fmt"
	"goproject/src/go_code/chapter06/funcinit/utils"
)

var age = test()

// 为了看到全局变量是先被初始化的，我们这里先写一个函数
func test() int {
	fmt.Println("test()") // 1
	return 90
}

// init函数，通常可以在init函数中完成初始化工作
func init() {
	fmt.Println("init()...") // 2
}
func main() {
	fmt.Println("main()...", age) // 3
	fmt.Printf("Age=%v name = %v", utils.Age, utils.Name)
}

```

## init函数面试题

如果main.go 和 utils.go 都含有变量定义，init函数时，执行的流程是怎样的？

utiols.go ：变量定义【执行1】	init函数【执行2】

main.go  ：变量定义【执行3】	init函数【执行4】	main函数【执行5】

## 匿名函数

go支持匿名函数(没有命名的函数)，如果我们某个函数只是希望使用一次，可以考虑使用匿名函数，匿名函数也可以实现多次调用

匿名函数使用方式一：在定义匿名函数时就直接调用

```go
package main

import "fmt"

func main() {
	// 匿名函数使用方式一：在定义匿名函数时就直接调用
	// 案例演示，求两个数的和，使用匿名函数的方式完成
	res1 := func(n1 int, n2 int) int {
		return n1 + n2
	}(10, 20)
	fmt.Println("res1=", res1)
}

```

匿名函数使用方式二：将匿名函数赋给一个变量（函数变量），再通过该变量·来条用匿名函数

```go
package main

import "fmt"

func main() {
	// 匿名函数使用方式一：在定义匿名函数时就直接调用
	// 案例演示，求两个数的和，使用匿名函数的方式完成
	res1 := func(n1 int, n2 int) int {
		return n1 + n2
	}(10, 20)
	fmt.Println("res1=", res1)

	// 将匿名函数func(n1 int, n2 int) int赋给a变量
	// 则a的数据类型就是函数类型，此时，我们可以通过a完成调用
	// main()函数中再定义函数的妙用
	a := func(n1 int, n2 int) int {
		return n1 - n2
	}
	res2 := a(10, 30)
	fmt.Println("res2=", res2)
	res3 := a(90, 30)
	fmt.Println("res3=", res3)
}
```

全局匿名函数：如果将匿名函数赋给一个全局变量，那么这个匿名函数，就成为一个全局匿名函数，可以在程序有效

```go
package main

import (
	"fmt"
)

// 全局匿名函数：如果将匿名函数赋给一个全局变量，那么这个匿名函数，就成为一个全局匿名函数，可以在程序有效
var (
	Fun1 = func(n1 int, n2 int) int {
		return n1 * n2
	}
)

func main() {
	// 匿名函数使用方式一：在定义匿名函数时就直接调用
	// 案例演示，求两个数的和，使用匿名函数的方式完成
	res1 := func(n1 int, n2 int) int {
		return n1 + n2
	}(10, 20)
	fmt.Println("res1=", res1)

	// 将匿名函数func(n1 int, n2 int) int赋给a变量
	// 则a的数据类型就是函数类型，此时，我们可以通过a完成调用
	// main()函数中再定义函数的妙用
	a := func(n1 int, n2 int) int {
		return n1 - n2
	}
	res2 := a(10, 30)
	fmt.Println("res2=", res2)
	res3 := a(90, 30)
	fmt.Println("res3=", res3)

	// 全局匿名函数的使用
	res4 := Fun1(4, 9)
	fmt.Println("res4=", res4)
}

```



## 闭包的基本介绍

闭包就是一个函数和与其相关的引用环境组合的一个整体（实体）

```go
package main

import "fmt"

func AddUpper() func(int) int {
	var n int = 10
	return func(x int) int {
		n = n + x
		return n
	}
}
func main() {
	// 累加器
	f := AddUpper()
	fmt.Println(f(1)) // 11
	fmt.Println(f(2)) // 13
	fmt.Println(f(3)) // 16
}
```

对上面代码的说明和总结：

1、AddUpper是一个函数，返回的数据类型是fun(int)int

2、闭包的说明：返回的是一个匿名函数，但是这个匿名函数引用到函数外的n，因此这个匿名函数就和n形成一个整体，构成闭包

3、大家可以这样理解：闭包是一个类，函数是操作，n是字段。函数和它使用到n构成闭包

4、当我们反复调用f函数时，因为n是初始化一次，因此每调用一次就进行累计

5、我们要搞清楚闭包的关键，就是要分析出返回的函数它使用（引用）到哪些变量，因为函数和它引用到的变量共同构成闭包

```go
package main

import "fmt"

func AddUpper() func(int) int {
	var n int = 10
	var str = "hello"
	return func(x int) int {
		n = n + x
		str += string("a") // -->$
		fmt.Println("str=", str)
		return n
	}
}
func main() {
	// 累加器
	f := AddUpper()
	fmt.Println(f(1)) // 11
	fmt.Println(f(2)) // 13
	fmt.Println(f(3)) // 16
}

```



## 闭包最佳实践和分析

1、编写一个函数makeSuffix(suffix string)可以接收一个文件后缀名（比如.jpg），并返回一个闭包

2、调用闭包，可以传入一个文件名，如果该文件名没有指定的后缀（比如.jpg），则返回文件名.jpg，如果已经有.jpg后缀，则返回原文件名

3、要求使用闭包的方式完成

4、strings.HasSuffix，该函数可以判断某个字符串是否有指定的后缀

```go
package main

import (
	"fmt"
	"strings"
)

func AddUpper() func(int) int {
	var n int = 10
	var str = "hello"
	return func(x int) int {
		n = n + x
		str += string("a") // -->$
		fmt.Println("str=", str)
		return n
	}
}

// 1、编写一个函数makeSuffix(suffix string)可以接收一个文件后缀名（比如.jpg），并返回一个闭包
// 2、调用闭包，可以传入一个文件名，如果该文件名没有指定的后缀（比如.jpg），则返回文件名.jpg，如果已经有.jpg后缀，则返回原文件名
// 3、要求使用闭包的方式完成
// 4、strings.HasSuffix，该函数可以判断某个字符串是否有指定的后缀
func makeSuffix(suffix string) func(string) string {
	return func(name string) string {
		// 如果 name 没有指定的后缀，则加上，否则就返回原来的名字
		if !strings.HasSuffix(name, suffix) {
			return name + suffix
		}
		return name
	}
}

func main() {
	// 累加器
	f := AddUpper()
	fmt.Println(f(1)) // 11
	fmt.Println(f(2)) // 13
	fmt.Println(f(3)) // 16

	// 测试makeSuffix的使用
	// 返回一个闭包
	f2 := makeSuffix(".jpg")
	fmt.Println("文件名处理后：", f2("winter"))   //winter.jpg
	fmt.Println("文件名处理后：", f2("bird.jpg")) //bird.jpg
	fmt.Println("文件名处理后：", f2("bird.avi")) //bird.avi.jpg
}

```

上面代码的总结和说明：

1、返回的匿名函数和makeSuffix(suffix string)的 suffix变量 组合成一个闭包，因为返回的函数引用到suffix这个变量

2、我们体会一下闭包的好处，如果使用传统的方法，也可以轻松实现这个功能，但是传统方法需要每次都引入后缀名，比如.jpg，而闭包以你为可以保留上次引用的某个值，所以我们传入一次就可以反复使用



## defer的基本使用

在函数中，程序员经常需要创建资源（比如：数据库连接、文件句柄、锁等），为了在函数执行完毕后，及时的释放资源，go的设计者提供defer（延时机制）

1、当go执行到一个defer时，不会立即执行defer后的语句，而是将defer后的语句压入到一个栈中（defer栈），然后继续执行函数下一个语句

2、当函数执行完毕后，再从defer栈中，一次从栈顶取出语句执行（注：遵守栈 先入后出的机制）

```go
package main

import "fmt"

func sum(n1 int, n2 int) int {
	// 当执行到defer时，暂时不执行，会将defer后面的语句压入到独立的栈（defer栈）
	// 当函数执行完毕后，再从defer栈，按照先入后出的方式出栈，执行
	defer fmt.Println("ok n1 =", n1) // 3、ok1 n1 = 10
	defer fmt.Println("ok n2 =", n2) // 2、ok2 n2 = 20
	res := n1 + n2
	fmt.Println("ok3 res=", res) // 1、ok3 res = 30
	return res
}

func main() {
	res := sum(10, 20)
	fmt.Println("res =", res) // 4、res =30
}

```

3、在defer将语句放入到栈时，也会将相关的值拷贝同时入栈。

```go
package main

import "fmt"

func sum(n1 int, n2 int) int {
	// 当执行到defer时，暂时不执行，会将defer后面的语句压入到独立的栈（defer栈）
	// 当函数执行完毕后，再从defer栈，按照先入后出的方式出栈，执行
	defer fmt.Println("ok n1 =", n1) // 3、ok1 n1 = 10
	defer fmt.Println("ok n2 =", n2) // 2、ok2 n2 = 20

	// 第三点：增加一句话
	n1++                         // n1 = 11，不影响上面n1的值
	n2++                         // n2 = 21，不影响上面n2的值
	res := n1 + n2               // res = 32
	fmt.Println("ok3 res=", res) // 1、ok3 res = 30  // 第三点：ok3 res=32
	return res
}

func main() {
	res := sum(10, 20)
	fmt.Println("res =", res) // 4、res =30		// 第三点：res = 32
}

```

## defer的最佳实践

defer最主要的价值是在，当函数执行完毕后，可以及时的释放函数创建的资源，看下模拟代码：

```go
func test(){
  // 关闭文件资源
  file = openfile(文件名)
  defer file.close() // 整个函数执行完才执行defer
  // 其他代码
}

func tese(){
  // 释放数据库资源
  connect = openDatabase()
  defer connect.close() // 整个函数执行完才执行defer
  // 其他代码
}
```

说明：

1、在golang编程中的通常做法是，创建资源后，比如（打开了文件，获取了数据库的链接，或者是锁资源），可以执行defer file.Close() defer.connect.Close()

2、在defer后，可以继续使用创建资源

3、当函数执行完毕后，系统会依次从defer栈中，取出语句，关闭资源

4、这种机制，非常简洁，程序员不用再为甚么时机关闭资源而烦心

## 函数参数传递方式

我们在讲解函数注意事项和使用细节时，已经讲过值类型和引用类型了，这里我们再系统总结一下，因为这是重点，值类型参数默认就是值传递，而引用类型参数默认就是引用传递。

两种传递方式：

1、值传递

2、引用传递

其实，不管是值传递还是引用传递，传递给函数的都是变量的副本，不同的是，值传递的是值的拷贝，引用传递的是地址的拷贝，一般来说，地址拷贝效率高，因为数据量小，而值拷贝决定拷贝的数据大小，数据越大，效率越低

值类型和引用类型

1、值类型：基本数据类型int系列，float系列，bool，string、数组和结构体struct

2、引用类型：指针、slice切片、map、管道chan、interface等都是引用类型

值传递和引用传递使用特点

1、值类型默认是值传递：变量直接存储值，内存通常在栈中分配

2、引用类型默认是引用传递：变量存储的是一个地址，这个地址对应的空间才真正存储数据（值），内存通常在堆上分配，当没有任何变量引用这个地址时，该地址对应的数据空间就成为一个垃圾，由GC回收

3、如果希望函数内的变量能修改函数外的变量，可以传入变量的地址&，函数内以指针的方式操作变量

## 变量作用域

1、函数内部声明/定义的变量叫局部变量（不管首字母是否大写），作用域仅限于函数内部

2、函数外部声明/定义的变量叫全局变量，作用域在整个包都有效，如果其首字母为大写，则作用域在整个程序有效

3、如果变量是在一个代码块，比如 for / if 中，那么这个变量的作用域就在该代码块

## 函数练习题（综合）

1、函数可以没有返回值案例，编写一个函数，从终端输入一个整数打印出对应的金字塔

```go
package main

import "fmt"

// 将打印金字塔的代码封装到函数中

func printPyramid(totalLevel int) {
	for i := 1; i <= totalLevel; i++ {
		// 在打印*前先打印空格
		for k := 1; k <= totalLevel-i; k++ {
			fmt.Print(" ")
		}
		// j表示每层打印多少个*
		for j := 1; j <= 2*i-1; j++ {
			if j == 1 || j == 2*i-1 || i == totalLevel {
				fmt.Print("*")
			} else {
				fmt.Print(" ")
			}
		}
		fmt.Println()

	}
}

func main() {
	// 调用pringPyramid()函数就可以打印金字塔了
	var n int = 0
	fmt.Println("请输入金字塔的层数：")
	fmt.Scanln(&n)
	printPyramid(n)
}

```



2、编写一个函数，从终端输入一个整数（1-9），打印出对应的乘法表

```go
package main

import "fmt"

// 编写一个函数调用九九乘法表
func printMulti(numLevel int) {
	// 变量控制层
	for i := 1; i <= numLevel; i++ {
		for j := 1; j <= i; j++ {
			fmt.Printf("%v * %v = %v\t", j, i, i*j)
			if i == j {
				fmt.Println()
			}
		}
	}
}
func main() {
	// 从终端输入一个整数，表示要打印的乘法表对应的层数
	var num int
	fmt.Println("请输入九九乘法表的层数：")
	fmt.Scanln(&num)
	if num >= 1 && num <= 9 {
		printMulti(num)
	} else {
		fmt.Println("输入有误")
	}

}

```



3、编写函数，对给定的一个二维数组（3x3）转置



## Go字符串中常用的系统函数

1、统计字符串的长度，按字节 len(str)

2、字符串遍历，同时处理有中文的问题 r := []rune(str)

3、字符串转整数：n, err := strconv.Atoi("12")

4、整数转字符串 str = strconv.Itoa(12345)

5、字符串转 []byte：var bytes = []byte("hello go")

6、[]byte转字符串：str = string([]byte{97,98,99})

7、10进制转2,8,16进制：str = strconv.FormatInt(132,2) // 2->8，16

8、查找子串是否在指定的字符串中：strings.Contains("seafood","foo") // true

9、统计一个字符串有几个指定的子串：strings.Count("ceheese","e") //4

10、不区分大小写的字符串比较（==是区分字母大小写的）：fmt.Println(strings.EqualFold("abc","Abc")) // true

11、返回子串在字符串第一次出现的index值，如果没有返回-1：strings.Index("NLT_abc","abc") // 4

12、返回子串在字符串最后一次出现的index，如没有返回-1

13、将指定的子串替换成 另外一个子串：strings.Replace("go go hello","go","go语言",n)

14、按照指定的某个字符，为分割表示，将一个字符串拆分成字符串数组

15、将字符串的字母进行大小写的转换

16、将字符串左右两边的空格去掉

17、将字符串左右两边指定的字符去掉

18、将字符串左边指定的字符去掉

19、将字符串右边指定的字符去掉

20、判断字符串是否以指定的字符串开头

21、判断字符串是否以指定的字符串结束

```go
package main

import (
	"fmt"
	"strconv"
	"strings"
)

func main() {
	// 	1、统计字符串的长度，按字节 len(str)
	str := "hello北"
	// golang的编码统一为utf-8(ascii的字符(字母和数字)占一个字节，汉字占用3个字节)
	fmt.Println("str lens:", len(str)) // 8

	// 2、字符串遍历，同时处理有中文的问题 r := []rune(str)
	str2 := "hello北京"
	r := []rune(str2)
	for i := 0; i < len(r); i++ {
		fmt.Printf("字符=%c\n", r[i])
	}

	// 3、字符串转整数：n, err := strconv.Atoi("12")
	n, err := strconv.Atoi("123")
	if err != nil { // nil 相当于其他语言中的 null（空）
		fmt.Println("转换错误：", err)
	} else {
		fmt.Println("转换结果是：", n)
	}

	// 4、整数转字符串 str = strconv.Itoa(12345)
	str = strconv.Itoa(12345)
	fmt.Printf("str =%v strtype =%T\n", str, str)

	// 5、字符串转 []byte：var bytes = []byte("hello go")
	var bytes = []byte("hello go")
	fmt.Printf("byte=%v\n", bytes)

	// 6、[]byte转字符串：str = string([]byte{97,98,99})
	str = string([]byte{97, 98, 99}) // a对应的ascii值是97
	fmt.Printf("str=%v\n", str)      // abc

	// 7、10进制转2,8,16进制：str = strconv.FormatInt(132,2) // 2->8，16
	str = strconv.FormatInt(123, 2) // 2->8，16
	fmt.Printf("123对应的二进制是：%v\n", str)
	str = strconv.FormatInt(123, 16) // 2->8，16
	fmt.Printf("123对应的十六进制是：%v\n", str)

	// 8、查找子串是否在指定的字符串中：strings.Contains("seafood","foo") // true
	b := strings.Contains("seafood", "food")
	fmt.Printf("b=%v\n", b) // true

	// 9、统计一个字符串有几个指定的子串：strings.Count("ceheese","e") //4
	num := strings.Count("ceheese", "e")
	fmt.Printf("c=%v\n", num) // 4

	// 10、不区分大小写的字符串比较（==是区分字母大小写的）：fmt.Println(strings.EqualFold("abc","Abc")) // true
	fmt.Println(strings.EqualFold("abc", "Abc"))
	fmt.Println("结果", "abc" == "Abc") // ==区分大小写

	// 11、返回子串在字符串第一次出现的index值，如果没有返回-1：strings.Index("NLT_abc","abc") // 4
	index := strings.Index("NLT_abc", "abc")
	fmt.Printf("index=%v\n", index) // 4

	// 12、返回子串在字符串最后一次出现的index，如没有返回-1
	index = strings.LastIndex("go golang", "go")
	fmt.Printf("index=%v\n", index) // 3

	// 13、将指定的子串替换成 另外一个子串：strings.Replace("go go hello","go","go语言",n)
	// n可以指定你希望替换几个，如果n=-1表示全部替换
	str2 = "go go hello"
	str = strings.Replace(str2, "go", "go语言", -1)
	fmt.Printf("str=%v\n", str) // go语言 go语言 hello

	// 14、按照指定的某个字符，为分割表示，将一个字符串拆分成字符串数组
	strArr := strings.Split("hello,world,ok", ",") // 分割后是一个数组strArr
	for i := 0; i < len(strArr); i++ {             // 遍历数组strArr[]
		fmt.Printf("str[%v]=%v\n", i, strArr[i])
	}
	fmt.Printf("strArr =%v\n", strArr)

	// 15、将字符串的字母进行大小写的转换
	str = "goLang Hello"
	str = strings.ToLower(str)  // 全部转换成小写
	fmt.Printf("str=%v\n", str) // golang hello
	str = strings.ToUpper(str)  // 全部转换成大写
	fmt.Printf("str=%v\n", str) // golang hello

	// 16、将字符串左右两边的空格去掉
	str = strings.TrimSpace("   tn a lone gopher ntrn    ")
	fmt.Printf("str=%v\n", str) // tn a lone gopher ntrn

	// 17、将字符串左右两边指定的字符去掉
	str = strings.Trim("!  he!llo!  ", " !")
	fmt.Printf("str=%q\n", str) // he!llo

	// 18、将字符串左边指定的字符去掉
	str = strings.TrimLeft("!hello!", "!")
	fmt.Printf("str=%v\n", str) // hello!

	// 19、将字符串右边指定的字符去掉
	str = strings.TrimRight("!hello!", "!")
	fmt.Printf("str=%v\n", str) //!hello

	// 20、判断字符串是否以指定的字符串开头
	b = strings.HasPrefix("ftp://192.168.0.1", "ftp")
	fmt.Println("b=", b) // true

	// 21、判断字符串是否以指定的字符串结束
	b = strings.HasSuffix("NLT_abc.jpg", "abc")
	fmt.Println("b = ", b) // false
}
```

## 时间和日期函数详解

在编程中，会经常使用到日期相关的函数，比如：统计某段代码执行花费的时间

1、时间和日期相关函数，需要导入time包

 2、time.Time类型：用于表示时间

3、获取到当前时间的方法：

now := time.Now() // now的类型就是time.Time

```go
package main

import (
	"fmt"
	"time"
)

func main() {
	// 看看日期和时间相关函数和方法使用
	// 1、获取当前时间
	now := time.Now()
	fmt.Printf("now=%v\nnowtype=%T", now, now)
}

// now=2022-05-02 16:27:47.527566 +0800 CST m=+0.000161242
// nowtype=time.Time

```

4、如何获取到其它日期信息

```go
package main

import (
	"fmt"
	"time"
)

func main() {
	// 看看日期和时间相关函数和方法使用
	// 1、获取当前时间
	now := time.Now()
	fmt.Printf("now=%v\nnowtype=%T\n", now, now)

	// 2、通过now可以获取到年月日，时分秒
	fmt.Printf("年=%v\n", now.Year())
	fmt.Printf("月=%v\n", now.Month())
	fmt.Printf("月=%v\n", int(now.Month()))
	fmt.Printf("日=%v\n", now.Day())
	fmt.Printf("时=%v\n", now.Hour())
	fmt.Printf("分=%v\n", now.Minute())
	fmt.Printf("秒=%v\n", now.Second())
}

```

5、格式化日期时间

​	方式1：就是使用 Printf 或者 SPrintf

​	方式2：使用time.Format()方法完成

说明："2006/01/02 15:04:05" 这个字符串的各个数字是固定的，必须是这样写

```go
package main

import (
	"fmt"
	"time"
)

func main() {
	// 看看日期和时间相关函数和方法使用
	// 1、获取当前时间
	now := time.Now()
	fmt.Printf("now=%v\nnowtype=%T\n", now, now)

	// 2、通过now可以获取到年月日，时分秒
	fmt.Printf("年=%v\n", now.Year())
	fmt.Printf("月=%v\n", now.Month())
	fmt.Printf("月=%v\n", int(now.Month()))
	fmt.Printf("日=%v\n", now.Day())
	fmt.Printf("时=%v\n", now.Hour())
	fmt.Printf("分=%v\n", now.Minute())
	fmt.Printf("秒=%v\n", now.Second())

	// 格式化日期时间_方式一
	fmt.Printf("当前年月日时分秒 %02d-%02d-%02d %02d:%02d:%02d \n",
		now.Year(), now.Month(), now.Day(), now.Hour(), now.Minute(), now.Second())
	dateStr := fmt.Sprintf("当前年月日时分秒 %02d-%02d-%02d %02d:%02d:%02d \n",
		now.Year(), now.Month(), now.Day(), now.Hour(), now.Minute(), now.Second())
	fmt.Println("dataStr = ", dateStr)

	// 格式化日期时间_方式二
	fmt.Println(now.Format("2006-01-02 15:04:05"))
	fmt.Println(now.Format("2006-01-02"))
	fmt.Println(now.Format("15:04:05"))
}

```



6、结合Sleep使用一下时间常量

常量的作用：在程序中可用于获取指定时间单位的时间，比如想得到100毫秒

```go
const(

Nanosecond Duration = 1 // 纳秒

Microsecond = 1000 * Nanosecond // 微秒

Millisecond = 1000 * Microsecond // 毫秒

Second = 1000 * Millisecond // 秒

Minute = 60 * Second // 分钟

Hour = 60 * Minute // 小时

)
```

```go
package main

import (
	"fmt"
	"time"
)

func main() {
	// 看看日期和时间相关函数和方法使用
	// 1、获取当前时间
	now := time.Now()
	fmt.Printf("now=%v\nnowtype=%T\n", now, now)

	// 2、通过now可以获取到年月日，时分秒
	fmt.Printf("年=%v\n", now.Year())
	fmt.Printf("月=%v\n", now.Month())
	fmt.Printf("月=%v\n", int(now.Month()))
	fmt.Printf("日=%v\n", now.Day())
	fmt.Printf("时=%v\n", now.Hour())
	fmt.Printf("分=%v\n", now.Minute())
	fmt.Printf("秒=%v\n", now.Second())

	// 格式化日期时间_方式一
	fmt.Printf("当前年月日时分秒 %02d-%02d-%02d %02d:%02d:%02d \n",
		now.Year(), now.Month(), now.Day(), now.Hour(), now.Minute(), now.Second())
	dateStr := fmt.Sprintf("当前年月日时分秒 %02d-%02d-%02d %02d:%02d:%02d \n",
		now.Year(), now.Month(), now.Day(), now.Hour(), now.Minute(), now.Second())
	fmt.Println("dataStr = ", dateStr)

	// 格式化日期时间_方式二
	fmt.Println(now.Format("2006-01-02 15:04:05"))
	fmt.Println(now.Format("2006-01-02"))
	fmt.Println(now.Format("15:04:05"))

	// 需求：每隔1秒打印一个数字，打印到100时就退出
	// 需求2：每隔0.1秒打印一个数字，打印到100时就退出
	i := 0
	for {
		i++
		fmt.Println(i)
		// 休眠1秒
		// time.Sleep(time.Second)
		time.Sleep(time.Millisecond * 100)
		// 休眠0.1秒
		if i == 100 {
			break
		}
	}
}

```

7、获取当前 unix 时间戳 和 unixnano 时间戳（作用是可以获取随机数字uuid ）

```go
	// Unix 和 UnixNano 的使用
	fmt.Printf("unix时间戳=%v\nunixnano时间戳=%v", now.Unix(), now.UnixNano())

// unix时间戳=1651482818
// unixnano时间戳=1651482818345129000
```

## 时间函数练习

编写一段代码来统计 函数test03()运行的时间

```go
package main

import (
	"fmt"
	"strconv"
	"time"
)

func test03() {
	str := ""
	for i := 0; i < 100000; i++ {
		str += "hello" + strconv.Itoa(i)
	}
}
func main() {
	// 在执行test03()前，先获取到当前的unix时间戳
	start := time.Now().Unix()
	test03()
	end := time.Now().Unix()
	fmt.Println("执行test03()一共用了", end-start, "秒")
}

```

## go内置函数

 golang设计者为了编程方便，提供了一些函数，这些函数可以直接使用，我们称为go的内置函数

1、len：用来求长度，比如string、array、slice、map、channel

2、new：用来分配内存，主要用来分配值类型，比如int、float32、struct...返回的是指针

```go
package main

import "fmt"

func main() {
	num1 := 100
	fmt.Printf("num1的类型是：%T，num1的值是：%v，num1的地址是：%v\n", num1, num1, &num1)
	num2 := new(int) // *int类型   相当于 ==> var num2 *int
	// num2的类型 ==》 *int
	// num2的值（值就是一个地址） ==》0xc0000c4010(这个地址是系统分配)
	// num2的地址 ==》地址:0xc0000be020(这个地址是系统分配)
	// num2指向的值 = 0
	*num2 = 100
	fmt.Printf("num2的类型是：%T，num2的值是：%v，num2的地址是：%v,\nnum2这个指针它指向的值是：%v\n", num2, num2, &num2, *num2)
}

```

3、make：用来分配内存，主要用来分配引用类型，比如channel、map、slice

## 错误处理机制

```go
package main

import "fmt"

func test() {
	num1 := 10
	num2 := 0
	res := num1 / num2
	fmt.Println("res=", res)
}
func main() {
	test()
	fmt.Println("main()下面的代码")
}

```

对上面代码的总结：

1、在默认情况下，当代码发生错误后（panic），程序就会退出（崩溃）

2、如果我们希望，当发生错误后，可以捕获到错误，并进行处理，保证程序可以继续执行，还可以在捕获到错误后，给管理员一个提示（邮件、短信...）

3、引出golang错误处理机制



基本说明：

1、go语言追求简洁优雅，所以go语言不支持传统的try...catch...finally这种处理

2、go中引入的处理方式为：defer，panic，recover

3、这几个异常的使用场景可以这么简单描述：go中可以抛出一个panic的异常，然后在defer中通过recover捕获这个异常，然后正常处理



使用defer+recover来处理错误

```go
package main

import (
	"fmt"
	"time"
)

func test() {
	// 使用defer + recover 来捕获和处理异常高
	defer func() {
		err := recover() // recover()内置函数，可以捕获到异常
		if err != nil {  // 说明捕获到错误
			fmt.Println("err=", err)
		}
	}()
	num1 := 10
	num2 := 0
	res := num1 / num2
	fmt.Println("res=", res)
}
func main() {
	test()
	for {
		fmt.Println("main()下面的代码")
		time.Sleep(time.Second)
	}
}

```

错误处理的好处

进行错误处理后，程序不会轻易挂掉，如果加入预警代码，就可以让程序更加的健壮

```go
package main

import (
	"fmt"
	"time"
)

func test() {
	// 使用defer + recover 来捕获和处理异常高
	defer func() {
		err := recover() // recover()内置函数，可以捕获到异常
		if err != nil {  // 说明捕获到错误
			fmt.Println("err=", err)
			// 这里就可以将错误信息发送给管理员...
			fmt.Println("发送邮件给admin@roc.cc")
		}
	}()
	num1 := 10
	num2 := 0
	res := num1 / num2
	fmt.Println("res=", res)
}
func main() {
	test()
	for {
		fmt.Println("main()下面的代码")
		time.Sleep(time.Second)
	}
}
```



## 错误处理机制_自定义错误

go程序中，也支持自定义错误，使用 errors.New 和 panic内置函数

1、errors.New("错误说明")，会返回一个error类型的值，表示一个错误

2、panic内置函数，接收一个interface{}类型的值（也就是任何值了）作为参数，可以接受error类型的变量，输出错误信息，并退出程序

```go
package main

import (
	"errors"
	"fmt"
)

func test() {
	// 使用defer + recover 来捕获和处理异常高
	defer func() {
		err := recover() // recover()内置函数，可以捕获到异常
		if err != nil {  // 说明捕获到错误
			fmt.Println("err=", err)
			// 这里就可以将错误信息发送给管理员...
			fmt.Println("发送邮件给admin@163.com")
		}
	}()
	num1 := 10
	num2 := 0
	res := num1 / num2
	fmt.Println("res=", res)
}

// 函数去读取一个配置文件init.conf的信息
// 如果文件名传入不正确，我们就返回一个自定义的错误
func readConf(name string) (err error) {
	if name == "config.ini" {
		// 读取
		return nil
	} else {
		// 返回自定义错误
		return errors.New("读取文件错误")
	}
}
func test02() {
	err := readConf("config2.ini")
	if err != nil {
		// 如果读取文件发生错误，就输出这个错误，并终止程序
		panic(err)
	}
	fmt.Println("test02()继续执行...")
}

func main() {
	test()
	// for {
	// 	fmt.Println("main()下面的代码")
	// 	time.Sleep(time.Second)
	// }

	// 测试自定义错误使用
	test02()
	fmt.Println("main()下面的代码")

}

```



## 函数练习

1、循环打印输入的年月，并判断该月有多少天

```go
package main

import (
	"fmt"
	"strconv"
)

func main() {
	var year int
	var month int
	for {
		fmt.Print("请输入年份：")
		fmt.Scanln(&year)
		fmt.Print("请输入月份：")
		fmt.Scanln(&month)
		stryear := fmt.Sprint(year)
		strmonth := fmt.Sprint(month)
		if len(stryear) == 4 && len(strmonth) == 2 {
			day := monthday(stryear, strmonth)
			fmt.Printf("%v年%v月一共有%v天\n", stryear, strmonth, day)
		} else {
			fmt.Println("您输入的格式不正确，请重新输入")
			continue
		}

	}
}
func monthday(year string, month string) (day int) {
	switch month {
	case "1":
		return 31
	case "2":
		stryear, _ := strconv.ParseInt(year, 10, 0)
		if stryear%4 == 0 {
			return 29
		} else {
			return 28
		}
	case "3":
		return 31
	case "4":
		return 30
	case "5":
		return 31
	case "6":
		return 30
	case "7":
		return 31
	case "8":
		return 31
	case "9":
		return 30
	case "10":
		return 31
	case "11":
		return 30
	case "12":
		return 31
	default:
		fmt.Println("您输入的月份不存在")
	}
	return
}

```

2、编写一个函数，随机猜数游戏，随机生成一个1-10的整数，有十次机会，

如果第一次就猜中，提示“你真是个天才”

如果第2-3次猜中，提示“你很聪明，赶上我了”

如果4-9次猜中，提示“一般般”

如果最后一次猜中，提示“可算猜对啦”

一次都没猜对，提示“说你点啥好呢”

```go
package main

import (
	"fmt"
	"math/rand"
	"time"
)

var guessnum int = 0

func main() {
	var count int = 10
	rand.Seed(time.Now().Unix())
	randomnum := rand.Intn(10) + 1
	fmt.Printf("------------游戏开始------------\n-----------已生成一个1-10的随机数-------------\n请输入：")
	for i := 1; i <= count; i++ {
		fmt.Scanln(&guessnum)
		if guessnum == randomnum {
			switch i {
			case 1:
				fmt.Println("你真是个天才")
			case 2, 3:
				fmt.Println("你很聪明，赶上我了")
			case 4, 5, 6, 7, 8, 9:
				fmt.Println("一般般")
			case 10:
				fmt.Println("可算猜对啦")
			}
			break
		} else if i == count {
			fmt.Println("一次都没对，说你点啥好呢")
		} else {
			fmt.Print("vvvvv猜的不对哦，重新猜一下vvvvv,请输入：")
			continue
		}

	}
}

```

3、编写一个函数，输出100以内的所有素数（只能被1和自己整除的数），每行显示5个，并求和

```go
package main

import "fmt"

var count = 1
var flag = true

func main() {
	for count < 100 {
		count++
		flag = true
		for i := 2; i < count; i++ {
			if count%i == 0 {
				flag = false
			}
		}
		if flag {
			fmt.Printf("%v\t", count)
		}
	}

}

```

4、编写一个函数，判断是打鱼还是晒网

中国有句俗语叫“三天打鱼两天晒网”，如果从1990年1月1日起开始执行“三天打鱼两天晒网”，如何判断在以后的某一天中是“打鱼”还是“晒网”？

```go
package main

import (
	"fmt"
	"time"
)

func daySum(year, month, day int) int {
	inputTime := time.Date(year, time.Month(month), day, 0, 0, 0, 0, time.Local)
	initTime := time.Date(1990, 1, 1, 0, 0, 0, 0, time.Local)
	daysSum := int(inputTime.Sub(initTime).Hours() / 24)
	return daysSum + 1
}

func fishOrNet(days int) {
	res := days % 5
	switch res {
	case 1, 2, 3:
		fmt.Println("这一天在打鱼！")
	case 4, 5:
		fmt.Println("这一天在晒网！")
	}
}
func inputFun() (num1, num2, num3 int) {
	var year int
	var month int
	var day int
	for {
		fmt.Print("请输入年：")
		fmt.Scanln(&year)
		if year >= 1990 {
			break
		} else {
			fmt.Println("输入的年份有误！")
		}
	}

	for {
		fmt.Print("请输入月：")
		fmt.Scanln(&month)
		if month > 0 && month <= 12 {
			break
		} else {
			fmt.Println("输入的月份有误！")
		}
	}
	for {
		fmt.Print("请输入日：")
		fmt.Scanln(&day)
		if year%4 == 0 && year%100 != 0 || year%400 == 0 {
			if day > 0 && day <= 29 {
				break
			}
			fmt.Println("输入的月份有误！")
		} else {
			if day > 0 && day <= 28 {
				break
			}
			fmt.Println("输入的月份有误！")
		}
	}
	return year, month, day
}
func main() {
	dayCount := daySum(inputFun())
	fishOrNet(dayCount)

}

```

# 第七章_数组和切片

## 数组的快速入门

数组可以存放多个同一类型数据，数组也是一种数据类型，在go中，数组是值类型

```go
package main

import "fmt"

// 养鸡场6只鸡，
func main() {
	// 1、定义一个数组
	var hens [6]float64
	// 2、给数组的每个元素赋值，元素的下标是从0开始的 0-5
	hens[0] = 3.0
	hens[1] = 5.0
	hens[2] = 1.0
	hens[3] = 3.4
	hens[4] = 2.0
	hens[5] = 50.0
	// 3、遍历数组求出总体重
	totalWeight2 := 0.00
	for i := 0; i < len(hens); i++ {
		totalWeight2 += hens[i]
	}
	// 求出平均体重
	avgWeight2 := fmt.Sprintf("%.2f", totalWeight2/float64(len(hens)))
	fmt.Printf("totalWeight2=%v\navgWeight2=%v", totalWeight2, avgWeight2)
}

```

对上面代码的总结：

1、使用数组来解决问题，程序的可维护性增加

2、而且方法代码更加清晰，也更容易扩展

## 数组定义和内存布局

```go
package main

import "fmt"

func main() {
	var intArr [3]int
	// 当我们定义完数组后，其实数组的各个元素有默认值0
	fmt.Println(intArr)
	intArr[0] = 10
	intArr[1] = 20
	intArr[2] = 30
	// 1、数组的地址可以通过数组名来获取 &intArr
	// 2、数组的第一个元素的地址，就是数组的首地址
	fmt.Printf("intArr的地址=%p intArr[0]的地址=%p intArr[1]的地址=%p", &intArr, &intArr[0], &intArr[1])
}

```

对上面代码的总结：

1、数组的地址可以通过数组名来获取 &intArr

2、数组的第一个元素的地址，就是数组的首地址

3、数组的各个元素的地址间隔是依据数组的类型决定的，比如int64 -> 8   int32 -> 4

## 数组的使用

访问数组元素：

数组名[下标] 比如： 你要使用a数组的第二个元素  a[2]

快速入门案例：

循环输入5个成绩，保存到float64数组，并输出

```go
package main

import "fmt"

func main() {
	var intArr [3]int
	// 当我们定义完数组后，其实数组的各个元素有默认值0
	fmt.Println(intArr)
	intArr[0] = 10
	intArr[1] = 20
	intArr[2] = 30
	// 1、数组的地址可以通过数组名来获取 &intArr
	// 2、数组的第一个元素的地址，就是数组的首地址
	fmt.Printf("intArr的地址=%p intArr[0]的地址=%p intArr[1]的地址=%p\n", &intArr, &intArr[0], &intArr[1])

	// 循环输入5个成绩，保存到float64数组，并输出
	var scoreArr [5]float64
	for i := 0; i < len(scoreArr); i++ {
		fmt.Printf("请输入第%v位同学的成绩\n", i+1)
		fmt.Scanln(&scoreArr[i])
	}
	for i := 0; i < len(scoreArr); i++ {
		fmt.Printf("第%v位同学的成绩是：%v\n", i+1, scoreArr[i])
	}
}
```

四种初始化数组的方式

```go
package main

import "fmt"

func main() {
	var intArr [3]int
	// 当我们定义完数组后，其实数组的各个元素有默认值0
	fmt.Println(intArr)
	intArr[0] = 10
	intArr[1] = 20
	intArr[2] = 30
	// 1、数组的地址可以通过数组名来获取 &intArr
	// 2、数组的第一个元素的地址，就是数组的首地址
	fmt.Printf("intArr的地址=%p intArr[0]的地址=%p intArr[1]的地址=%p\n", &intArr, &intArr[0], &intArr[1])

	// 循环输入5个成绩，保存到float64数组，并输出
	var scoreArr [5]float64
	for i := 0; i < len(scoreArr); i++ {
		fmt.Printf("请输入第%v位同学的成绩\n", i+1)
		fmt.Scanln(&scoreArr[i])
	}
	for i := 0; i < len(scoreArr); i++ {
		fmt.Printf("第%v位同学的成绩是：%v\n", i+1, scoreArr[i])
	}

	// 四种初始化数组的方式
	var numArr01 [3]int = [3]int{1, 2, 3}
	fmt.Println("numArr01", numArr01)

	var numArr02 = [3]int{5, 6, 7}
	fmt.Println("numArr02", numArr02)

	// 这里的[...]是固定写法
	var numArr03 [3]int = [...]int{8, 9, 10}
	fmt.Println("numArr03", numArr03)

	var numArr04 [3]int = [...]int{1: 800, 2: 900, 0: 100}
	fmt.Println("numArr04", numArr04)
  
  // 类型推导
	strArr05 := [...]string{1: "tom", 2: "jack", 0: "marry"}
	fmt.Println("strArr05", strArr05)
}

```



## 数组for-range遍历

方式一：常规遍历

方式二：for-range结构遍历

这是go语言一种独有的结构，可以用来遍历访问数组的元素

for index,value := range array01{

}

说明：

1、第一个返回值index是数组的下标

2、第二个value是在该下标位置的值

3、他们都是仅在for循环内部可见的局部变量

4、遍历数组元素的时候，如果不想使用下标index，可以直接把下标index标为下划线_

5、index和value的名称不是固定的，即程序员可以自行指定，一般命名为index和value

```go
package main

import "fmt"

func main() {
	// 演示for-range遍历数组
	heroes := [3]string{"宋江", "吴用", "卢俊义"}
	fmt.Println(heroes)
	// for-range
	for index, value := range heroes {
		fmt.Printf("index=%v value=%v\n", index, value)
		fmt.Printf("heroes[%d]=%v\n", index, heroes[index]) // 不建议两个都使用
	}
	// for-range, 使用 _ 忽略下标
	for _, value := range heroes {
		fmt.Printf("元素的值=%v\n", value)
	}
}

```

## 数组使用注意事项和细节

1、数组是多个相同类型数据的组合，一个数组一旦声明/定义了，其长度是固定的，不能动态变化

2、var arr []int 这时 arr 就是一个slice切片，切片后面专门讲解

3、数组中的元素可以是任何数据类型，包括值类型和引用类型，但是不能混用

4、数组创建后，如果没有赋值，有默认值（零值 ）：

​	数值类型数组：默认值为0

​	字符串数组：默认值为""

​	bool数组：默认值为false

5、使用数组的步骤：1、声明数组并开辟空间 2、给数组各个元素赋值（默认零值） 3、使用数组

6、数组的下标是从0开始的

7、数组下标必须在指定范围内使用，否则报panic：数组越界，比如

​	var arr [5]int 则有效下标为0-4

8、go的数组属值类型，在默认情况下是值传递，因此会进行值拷贝。数组间不会相互影响

9、如想在其他函数中，去修改原来的数组，可以使用引用传递（指针方式）

10、长度是数据类型的一部分，在传递函数参数时，需要考虑数组的长度

## 数组应用案例

1、创建一个byte类型的26个元素的数组，分别放置'A-Z'，使用for循环访问所有元素并打印出来，提示：字符数据运算'A'+1 -> 'B'

2、请求出一个数组的最大值，并得到对应的下标

```go
package main

import "fmt"

func main() {
	// 创建一个byte类型的26个元素的数组，分别放置'A-Z'，使用for循环访问所有元素并打印出来，提示：字符数据运算'A'+1 -> 'B'

	// 思路
	// 1、声明一个数组
	// 2、使用for循环，利用 字符可以进行运算的特点来赋值 'A' + 1 -> 'B'
	// 3、使用for循环打印即可

	var myChars [26]byte
	for i := 0; i < 26; i++ {
		myChars[i] = 'A' + byte(i)
	}

	for i := 0; i < 26; i++ {
		fmt.Printf("%c ", myChars[i])
	}

	// 请求出一个数组的最大值，并得到对应的下标
	// 思路
	// 1、声明一个数组
	// 2、假定第一个元素就是最大值，下标0
	// 3、然后从第二个元素循环比较，如果发现有更大的，则交换

	fmt.Println("")
	var intArr [5]int = [5]int{1, -1, 9, 90, 11}
	maxVal := intArr[0]
	maxValIndex := 0
	for i := 0; i < len(intArr); i++ {
		if maxVal < intArr[i] {
			maxVal = intArr[i]
			maxValIndex = i
		}
	}
	fmt.Printf("maxVal=%v maxValIndex=%v", maxVal, maxValIndex)
}

```

3、请求出一个数组的和、平均值。for-range

```go
package main

import "fmt"

func main() {
	// 创建一个byte类型的26个元素的数组，分别放置'A-Z'，使用for循环访问所有元素并打印出来，提示：字符数据运算'A'+1 -> 'B'

	// 思路
	// 1、声明一个数组
	// 2、使用for循环，利用 字符可以进行运算的特点来赋值 'A' + 1 -> 'B'
	// 3、使用for循环打印即可

	var myChars [26]byte
	for i := 0; i < 26; i++ {
		myChars[i] = 'A' + byte(i)
	}

	for i := 0; i < 26; i++ {
		fmt.Printf("%c ", myChars[i])
	}

	// 请求出一个数组的最大值，并得到对应的下标
	// 思路
	// 1、声明一个数组
	// 2、假定第一个元素就是最大值，下标0
	// 3、然后从第二个元素循环比较，如果发现有更大的，则交换

	fmt.Println("")
	var intArr [5]int = [5]int{1, -1, 9, 90, 11}
	maxVal := intArr[0]
	maxValIndex := 0
	for i := 0; i < len(intArr); i++ {
		if maxVal < intArr[i] {
			maxVal = intArr[i]
			maxValIndex = i
		}
	}
	fmt.Printf("maxVal=%v maxValIndex=%v\n\n", maxVal, maxValIndex)

	// 请求出一个数组的和、平均值。for-range
	// 思路
	// 1、声明一个数组
	// 2、求出和
	// 3、求出平均值

	var intArr2 [5]int = [5]int{1, -1, 9, 90, 12}
	sum := 0
	for _, value := range intArr2 {
		//累计求和
		sum += value
	}
	// 如何让平均值保留到小数，对计算结果进行类型转换
	fmt.Printf("sum = %v  平均值 = %v", sum, float64(sum)/float64(len(intArr2)))
}

```



## 数组的复杂应用_反转

要求：随机生成五个数，并将其反转打印

```go
package main

import (
	"fmt"
	"math/rand"
	"time"
)

func main() {
	// 创建一个byte类型的26个元素的数组，分别放置'A-Z'，使用for循环访问所有元素并打印出来，提示：字符数据运算'A'+1 -> 'B'

	// 思路
	// 1、声明一个数组
	// 2、使用for循环，利用 字符可以进行运算的特点来赋值 'A' + 1 -> 'B'
	// 3、使用for循环打印即可

	var myChars [26]byte
	for i := 0; i < 26; i++ {
		myChars[i] = 'A' + byte(i)
	}

	for i := 0; i < 26; i++ {
		fmt.Printf("%c ", myChars[i])
	}

	// 请求出一个数组的最大值，并得到对应的下标
	// 思路
	// 1、声明一个数组
	// 2、假定第一个元素就是最大值，下标0
	// 3、然后从第二个元素循环比较，如果发现有更大的，则交换

	fmt.Println("")
	var intArr [5]int = [5]int{1, -1, 9, 90, 11}
	maxVal := intArr[0]
	maxValIndex := 0
	for i := 0; i < len(intArr); i++ {
		if maxVal < intArr[i] {
			maxVal = intArr[i]
			maxValIndex = i
		}
	}
	fmt.Printf("maxVal=%v maxValIndex=%v\n\n", maxVal, maxValIndex)

	// 请求出一个数组的和、平均值。for-range
	// 思路
	// 1、声明一个数组
	// 2、求出和
	// 3、求出平均值

	var intArr2 [5]int = [5]int{1, -1, 9, 90, 12}
	sum := 0
	for _, value := range intArr2 {
		//累计求和
		sum += value
	}
	// 如何让平均值保留到小数，对计算结果进行类型转换
	fmt.Printf("sum = %v  平均值 = %v\n\n", sum, float64(sum)/float64(len(intArr2)))

	// 要求：随机生成五个数，并将其反转打印
	// 思路
	// 1、随机生成5个数，rand.Intn()函数
	// 2、当得到随机数后，就放到一个数组 int数组
	// 3、反转打印：交换的次数时 len / 2，倒数第一个和第一个元素交换，倒数第2个和第2个交换

	var intArr3 [5]int
	intArr3len := len(intArr3)
	// 为了每次生成的随机数不一样，我们需要给一个seed值
	rand.Seed(time.Now().UnixNano())
	for i := 0; i < intArr3len; i++ {
		intArr3[i] = rand.Intn(100) // 0 <= n < 100
	}
	fmt.Println("交换前：", intArr3)
	temp := 0 // 做一个临时变量，用作临时交换
	for i := 0; i < intArr3len/2; i++ {
		temp = intArr3[intArr3len-1-i]
		intArr3[intArr3len-1-i] = intArr3[i]
		intArr3[i] = temp
	}
	fmt.Println("交换后", intArr3)
}

```

## slice切片基本介绍和入门

需求：我们需要一个数组用于保存学生的成绩，但是学生的个数是不确定的。这时需要使用切片（动态数组）

1、切片的英文是slice

2、切片是数组的一个引用，因此切片是引用类型，在进行传递时，遵守引用传递的机制

3、切片的使用和数组类似，遍历切片、访问切片的元素和求切片长度len(slice)都一样

4、切片的长度是可以变化的，因此切片是一个可以动态变化的数组

5、切片定义的基本语法：

​	var 变量(切片)名 []类型     ==》	var a []int

```go
package main

import "fmt"

func main() {
	// 演示切片slice的基本使用
	var intArr [5]int = [...]int{1, 22, 33, 66, 99}
	// 声明/定义一个切片
	// slice := intArr[1:3]
	// 1、slice 就是切片名
	// 2、intArr[1:3] 表示 slice引用到intArr这个数组
	// 3、引用intArr数组的起始下标为1，终止下标为3（不包含3）
	slice := intArr[1:3]
	fmt.Println("intArr = ", intArr)
	fmt.Println("slice 的元素是：", slice)
	fmt.Println("slice 的元素个数是：", len(slice))
	fmt.Println("slice 的容量是：", cap(slice)) // 切片的容量可以动态变化
}
// intArr =  [1 22 33 66 99]
// slice 的元素是： [22 33]
// slice 的元素个数是： 2
// slice 的容量是： 4
```

## 切片使用的三种方式

方式一：定义一个切片，然后让切片去引用一个已经创建好的数组

方式二：通过make来创建切片

​	基本语法：var 切片名 []type = make([]type,len,[cap])

​	参数说明：type:就是数据类型，len:大小，cap:指定切片容量（可选），如果分配了cap，则要求cap >= len

方式三：定义一个切片，直接就指定具体数组，使用原理类似make的方式

```go
package main

import "fmt"

func main() {
	// 方式二：演示切片的使用make
	var slice []float64 = make([]float64, 5, 10)
	slice[1] = 10
	slice[3] = 20
	// 对于切片，必须make使用
	fmt.Println(slice)
	fmt.Println("slice的size = ", len(slice))
	fmt.Println("slice的cap = ", cap(slice))

	// 方式三
	var strSlice []string = []string{"tom", "jack", "marry"}
	fmt.Println(strSlice)
	fmt.Println("slice的size = ", len(strSlice))
	fmt.Println("slice的cap = ", cap(strSlice))
}

```

对上面代码的小结：

1、通过make方式创建切片可以指定切片的大小和容量

2、如果没有给切片的各个元素赋值，那么就会使用默认值[int,float... =>0   string ->""  bool => false]

3、通过make方式创建的切片对应的数组是由make底层维护，对外不可见，即只能通过slice访问各个元素

## 切片的遍历

切片的遍历和数组一样，也有两种方式

方式一：for循环常规方式遍历

方式二：for-range结构遍历切片

```go
package main

import "fmt"

func main() {
	// 使用常规的for循环遍历切片
	var arr [5]int = [...]int{10, 20, 30, 40, 50}
	slice := arr[1:4]
	for i := 0; i < len(slice); i++ {
		fmt.Printf("slice[%v]=%v\n\n", i, slice[i])
	}

	// 使用for-range方式遍历切片
	for i, v := range slice {
		fmt.Printf("slice[%v]=%v", i, v)
	}
}

```

## 切片注意事项和细节

1、切片初始化时，var slice = arr[startIndex:endIndex]，从arr数组下标为strtIndex，取到endIndex的元素（不含endIndex）

2、切片初始化时，仍然不能越界。范围在[0-len(arr)]之间，但是可以动态增长

​	var slice = arr[0:end] 可以简写 var slice = arr[:end]

​	var slice = arr[start:len(arr)] 可以简写 var slice = arr[start:]

​	var slice = arr[0:len(arr)] 可以简写 var slice = arr[:]

3、cap是一个内置函数，用于统计切片的容量，即最大可以存放多少个元素

4、切片定义完后，还不能使用，因为本身是一个空的，需要让其引用到一个数组，或者make一个空间供切片来使用

5、切片可以继续切片

6、用append内置函数，可以对切片进行动态追加

```go
package main

import "fmt"

func main() {
	// 使用常规的for循环遍历切片
	var arr [5]int = [...]int{10, 20, 30, 40, 50}
	slice := arr[1:4]
	for i := 0; i < len(slice); i++ {
		fmt.Printf("slice[%v]=%v\n\n", i, slice[i])
	}

	// 使用for-range方式遍历切片
	for i, v := range slice {
		fmt.Printf("slice[%v]=%v\n", i, v)
	}

	slice2 := slice[1:2]
	slice2[0] = 100 // 因为arr、slice、slice2 指向的数据空间是同一个，因此slice2[0]改变了，slice、arr都会变化
	fmt.Println("slice2=", slice2)
	fmt.Println("slice=", slice)
	fmt.Println("arr=", arr)

	// 用append内置函数，可以对切片进行动态追加
	var slice3 []int = []int{100, 200, 300}
	// 通过append直接给slice3追加具体的元素
	slice3 = append(slice3, 400, 500, 600)
	fmt.Println("slice3=", slice3)
	// 通过append函数将切片slice3追加给slice3， ...是固定写法
	slice3 = append(slice3, slice3...)
	fmt.Println("slice3=", slice3)

}

```

对上面代码的小结（切片append操作的底层原理分析）：

​	切片append操作的本质就是对数组扩容

​	go底层会创建一个新的数组newArr（安装扩容后大小）

​	将slice原来包含的元素拷贝到新的数组newArr

​	slice重新引用到newArr

​	注意newArr是在底层来维护的，程序员不可见

7、切片的拷贝操作：切片使用copy内置函数完成拷贝

```go
// 切片的拷贝操作
// 切片使用copy内置函数完成拷贝
	var slice4 []int = []int{1, 2, 3, 4, 5}
	var slice5 = make([]int, 10)
	copy(slice5, slice4)
	fmt.Println("slice4=", slice4)
	fmt.Println("slice5=", slice5)
```

对上面代码的说明：

​	copy(para1,para2) 参数的数据类型是切片

​	按照上面的代码来看，slice4和slice5的数据空间是独立的，相互不影响，也就是说slice4[0] = 999，slice5[0] 仍然是1

8、切片是引用类型，所以在传递时，遵守引用传递机制

## string和slice

1、string底层是一个byte数组，因此string也可以进行切片处理

```go
package main

import "fmt"

func main() {
	str := "hello@golang"
	// 使用切片获取到 golang
	slice := str[6:]
	fmt.Println("slice=", slice)
}
```

2、string和切片在内存的形式 

3、string是不可变的，也就说不能通过str[0] = 'z'方式来修改字符串

4、如果需要修改字符串，可以先将string -> []byte / 或者 []rune -> 修改 -> 重写转成string

```go
package main

import "fmt"

func main() {
	str := "hello@golang"
	// 使用切片获取到 golang
	slice := str[6:]
	fmt.Println("slice=", slice)

	// str[0] = 'z' // 编译不通过，报错，原因是string是不可变的
	// "hello@golang" ==> 改成"zello@golang"
	arr1 := []byte(str)
	arr1[0] = 'z'
	str = string(arr1)
	fmt.Println("str=", str)

	// 细节，我们转成[]byte后，可以处理英文和数字，但是不能处理中文
	// 原因是 []byte 按字节来处理，而一个汉字是3个字节，因此就会出现乱码
	// 解决方法是将 string 转成 []rune 即可，因为 []rune 是按字符处理，兼容汉字
	arr2 := []rune(str)
	arr2[0] = '北'
	str = string(arr2)
	fmt.Println("str", str)
}
```

## 切片练习题

说明：编写一个函数fbn（n int），要求完成

1、可以接收一个n int

2、能够将斐波那契的数列放到切片中

```go
package main

import "fmt"

func fbn(n int) []uint64 {
	// 声明一个切片，切片大小 n
	fbnslice := make([]uint64, n)
	// 第一个数和第二个数的斐波那契数 为1
	fbnslice[0] = 1
	fbnslice[1] = 1
	for i := 2; i < n; i++ {
		fbnslice[i] = fbnslice[i-1] + fbnslice[i-2]
	}
	return fbnslice

}
func main() {
	// 说明：编写一个函数fbn（n int），要求完成
	// 1、可以接收一个n int
	// 2、能够将斐波那契的数列放到切片中

	// 思路
	// 1、声明一个函数fbn(n int) ([]uint64)
	// 2、编写fbn(n int) 进行for循环来存放斐波那契数列 0=》1  1=》1

	// 测试一把，是否好用
	fbnslice := fbn(20)
	fmt.Println("fbnslice=", fbnslice)
}

```



# 第八章_排序和查找

## 数组排序

排序是将一组数据，依指定的顺序进行排列的过程

排序的分类：

1、内部排序：指将需要处理的所有数据都加载到内部存储器中进行排序，包括（交换式排序法、选择式排序法、插入式排序法）

2、外部排序：数据量过大，无法全部加载到内存中，需要借助外部存储进行排序，包括（合并排序法、直接合并排序法）



交换式排序法：

交换式排序属于内部排序法，是运用数据值比较后，依判断规则对数据位置进行交换，以达到排序的目的

交换式排序法又可以分为两种：1、冒泡排序法（Bubble sort）2、快速排序法（Quick sort）



交换式排序法_冒泡排序法

冒泡排序（Bubble sort）的基本思想是：通过对待排序序列从后向前（从下标较大的元素开始），依次比较相邻元素的排序码，若发现逆序则交换，使排序码较小的元素逐渐从后部移向前部（从下标较大的单元移向下标较小的单元），就像水底下的旗袍一样逐渐向上冒

因为排序的过程中，各元素不断接近自己的位置，如果一趟比较下来没有进行过交换，就说明序列有序，因此要在排序过程中设置一个标志flag判断元素是否进行过交换，从而减少不必要的比较（优化）



## 冒泡排序思路分析

冒泡排序法案例：

我们将五个无序：24，69，80，57，13 使用冒泡排序法将其排成一个从小到大的有序数列

规则：

1、一共会经过arr.length-1次的轮数比较，每一轮将会确定一个数的位置

2、每一轮的比较次数在逐渐的减少

3、当发现前面的一个数比后面的一个数大的时候，就进行了交换

## 冒泡排序的实现

```go
package main

import "fmt"

func BubbleSort(arr *[5]int) {
	fmt.Println("排序前arr=", (*arr))
	temp := 0 // 临时变量（用于做交换）
	// 冒泡排序...
	for i := 0; i < len(*arr)-1; i++ {

		for j := 0; j < len(*arr)-1-i; j++ {
			if (*arr)[j] > (*arr)[j+1] { // >从小到大，<从大到小
				// 交换
				temp = (*arr)[j]
				(*arr)[j] = (*arr)[j+1]
				(*arr)[j+1] = temp

			}
		}
	}
	fmt.Println("排序后arr=", (*arr))
}

// 冒泡排序
func main() {
	// 声明/定义数组
	arr := [5]int{24, 69, 80, 57, 13}
	// 将数组传递给一个函数，完成排序

	BubbleSort(&arr)
	fmt.Println("maini() arr=", arr) // 是有序的
}

```

## 顺序查找

在golang中，我们常用的查找有两种：

1、顺序查找

2、二分查找（该数组是有序）

有一个数列：白眉鹰王、金毛狮王、紫衫龙王、青翼蝠王

猜数游戏：从键盘人意输入一个名称，判断数列中是否包含此名称【顺序查找】

```go
package main

import "fmt"

func main() {
	// 有一个数列：白眉鹰王、金毛狮王、紫衫龙王、青翼蝠王
	// 猜数游戏：从键盘人意输入一个名称，判断数列中是否包含此名称【顺序查找】

	// 1、定义一个数组，字符串数组
	// 2、从控制台接受用户输入名称，依次比较，如果发现有，就提示

	names := [4]string{"白眉鹰王", "金毛狮王", "紫衫龙王", "青翼蝠王"}
	var heronName = ""
	fmt.Print("请输入查找的人名：")
	fmt.Scanln(&heronName)

	// 顺序查找：第一种方式
	for i := 0; i < len(names); i++ {
		if heronName == names[i] {
			fmt.Println("找到了：", heronName)
			break
		} else if i == len(names)-1 {
			fmt.Println("没有找到")
		}
	}

	// 顺序查找：第二种方式【推荐】
	index := -1
	for i := 0; i < len(names); i++ {
		if heronName == names[i] {
			index = i // 将找到的值对应的下标赋给index
			break
		}
	}
	if index != -1 {
		fmt.Println("找到了：", heronName)
	} else {
		fmt.Println("没有找到！")
	}
}

```



## 二分查找的思路分析

请对一个有序数组进行二分查找{1,8,10,89,1000,1234}，请输入一个数看看该数组是否存在此数，并且求出下标，如果没有就提示“没有这个数”【会使用到 递归】

arr = {1,8,10,89,1000,1234}

二分超着的思路：比如我们要查找的数是findVal

1、arr是一个有序数组，并且是从小到大排序

2、先找到中间的下标middle = (leftIndex + rightIndex) / 2，然后让中间下标的值和findVal进行比较

​	2.1、如果arr[middle] > findVal，就应该向 leftIndex ~ (middle - 1)

​	2.2、如果arr[middle] < findVal，就应该向 (middle + 1) ~ rightIndex

​	2.3、如果arr[middle] == findVal，就找到

3、退出递归的条件：

```go
if leftIndex > rightIndex{
	// 找不到
	return...
}
```

## 二分查找的代码实现

```go
package main

import "fmt"

// 二分查找的函数
func BinaryFind(arr *[6]int, leftIndex int, rightIndex int, findVal int) {
	// 判断leftIndex 是否大于 rithtIndex
	if leftIndex > rightIndex {
		fmt.Println("找不到")
		return
	}
	// 先找到中间的下标
	middle := (leftIndex + rightIndex) / 2
	if (*arr)[middle] > findVal {
		// 说明我们要查找的数，应该在leftIndex ～ middle -1之间
		BinaryFind(arr, leftIndex, middle-1, findVal)
	} else if (*arr)[middle] < findVal {
		// 说明我们要查找的数，应该在 middle+1 ~ rightIndex之间
		BinaryFind(arr, middle+1, rightIndex, findVal)
	} else {
		// 找到了
		fmt.Printf("找到了，下标为%v\n", middle)
	}
}
func main() {
	arr := [6]int{1, 8, 10, 89, 1000, 1234}
	var num int
	// 测试一哈
	fmt.Print("请输入你要查找的数字：")
	fmt.Scanln(&num)
	BinaryFind(&arr, 0, len(arr)-1, num)
}

```



## 二维数组的应用场景

比如我们开发一个五子棋游戏，棋盘就是需要二维数组来表示

入门案例：请用二维数组输出如下图形

0 0 0 0 0 0

0 0 1 0 0 0 

0 2 0 3 0 0 

0 0 0 0 0 0

```go
package main

import "fmt"

func main() {
	// 声明/定义二维数组
	var arr [4][6]int
	// 赋初值
	arr[1][2] = 1
	arr[2][1] = 2
	arr[2][3] = 3

	// 遍历二维数组，按照要求输出图形
	for i := 0; i < 4; i++ {
		for j := 0; j < 6; j++ {
			fmt.Print(arr[i][j], " ")
		}
		fmt.Println()
	}
}

```

## 二维数组的遍历方式

方式1：双层for循环完成遍历

方式2：for-range方式完成遍历

```go
package main

import "fmt"

func main() {
	// 演示二维数组的遍历
	var arr3 [2][3]int = [2][3]int{{1, 2, 3}, {4, 5, 6}}

	// for循环遍历
	for i := 0; i < len(arr3); i++ {
		for j := 0; j < len(arr3[i]); j++ {
			fmt.Printf("%v\t", arr3[i][j])
		}
		fmt.Println()
	}

	// for-range方式遍历二维数组
	for i, v := range arr3 {
		for j, v2 := range v {
			fmt.Printf("arr3[%v][%v]=%v \t", i, j, v2)

		}
		fmt.Println()
	}
}

```



## 二维数组的应用案例

定义二维数组，用于保存三个班，每个班五名同学成绩，并求每个班级平均分、以及所有班级平均分

```go
package main

import "fmt"

func main() {
	// 定义二维数组，用于保存三个班，每个班五名同学成绩，并求每个班级平均分、以及所有班级平均分

	// 1、定义一个二维数组
	var scores [3][5]float64
	// 2、循环输入成绩
	for i := 0; i < len(scores); i++ {
		for j := 0; j < len(scores[i]); j++ {
			fmt.Printf("请输入第%d班的第%d个学生的成绩\n", i+1, j+1)
			fmt.Scanln(&scores[i][j])
		}
	}
	// fmt.Println(scores)
	// 3、遍历输入成绩后的二维数组，统计平均分
	totalSum := 0.0 //定义一个变量，用于累计所有班级的总分
	for i := 0; i < len(scores); i++ {
		sum := 0.0
		for j := 0; j < len(scores[i]); j++ {
			sum += scores[i][j]
		}
		totalSum += sum
		fmt.Printf("第%d班级的总分为%v，平均分%v\n", i+1, sum, sum/float64(len(scores[i])))
	}
	fmt.Printf("所有班级的总分：%v，平均分：%v\n", totalSum, totalSum/15)
}

```



# 第九章_map

map是 key-value 数据结构，又称为字段或者关联数组，类似其它编程语言的集合，在编程中是经常使用到

基本语法：var map变量名 map[keytype]valuetype

key可以是什么类型：golang中的map，key可以是很多种类型，比如bool、数字、string、指针、channel，还可以是只包括前面几个类型的接口、结构体、数组，通常为int、string【注意：slice、map、function不可以，因为这几个没法用 == 来判断】

valuetype可以是什么类型：value的类型和key基本一样，通常为数字（整数、浮点数）、string、马map、struct

map声明的距离：

```go
var a map[string]string
var a map[string]int
var a map[int]string
var a map[string]map[string]string
// 【注意：声明不会分配内存的，初始化需要make，分配内存后才能赋值和使用】
```

```go
package main

import "fmt"

func main() {
	// map的声明和注意事项
	var a = make(map[string]string, 10)
	// 在使用map前，需要先make，make的作用就是给map分配数据空间
	a["no1"] = "宋江"
	a["no2"] = "吴用"
	a["no1"] = "武松" // key唯一，重复会覆盖
	a["no3"] = "吴用"
	fmt.Println(a)
}

```

对上面代码的说明：

1、map在使用时一定要make

2、map的key是不能重复，如果重复了，则以最后这个key-value为准（覆盖）

3、map的value是可以相同的

4、map的key-value是无序的*

## map的三种使用方式和应用实例

```go
package main

import "fmt"

func main() {
	// 第一种使用方式
	// map的声明和注意事项
	var a = make(map[string]string, 10)
	// 在使用map前，需要先make，make的作用就是给map分配数据空间
	a["no1"] = "宋江"
	a["no2"] = "吴用"
	a["no1"] = "武松" // key唯一，重复会覆盖
	a["no3"] = "吴用"
	fmt.Println(a)

	// 第二种方式
	cities := make(map[string]string)
	cities["no1"] = "北京"
	cities["no2"] = "天津"
	cities["no3"] = "上海"
	fmt.Println(cities)

	// 第三种方式
	heroes := map[string]string{
		"here1": "宋江",
		"here2": "卢俊义",
	}
	fmt.Println("heros =", heroes)
}

```

我们要存放3个学生信息，每个学生有name和sex信息

思路：map[string]map[string]string

```go
package main

import (
	"fmt"
)

func main() {
	// 我们要存放3个学生信息，每个学生有name和sex信息
	// 思路：map[string]map[string]string
	studentMap := make(map[string]map[string]string)
	studentMap["stu01"] = make(map[string]string) // 这句话不能少，少了会报错
	studentMap["stu01"]["name"] = "tom"
	studentMap["stu01"]["sex"] = "男"
	studentMap["stu01"]["address"] = "北京长安街"

	studentMap["stu02"] = make(map[string]string) // 这句话不能少，少了会报错
	studentMap["stu02"]["name"] = "marry"
	studentMap["stu02"]["sex"] = "女"
	studentMap["stu02"]["address"] = "上海陆家嘴"

	fmt.Println(studentMap)
	fmt.Println(studentMap["stu02"])
	fmt.Println(studentMap["stu02"]["address"])
}

```



## map的crud操作

新增&删除

```go
package main

import "fmt"

func main() {
	// map的crud
	cities := make(map[string]string)
	cities["no1"] = "北京"
	cities["no2"] = "天津"
	cities["no3"] = "上海"

	// 因为no3这个key已经存在，因此下面这句话就是 修改
	cities["no3"] = "上海呀"
	fmt.Println(cities)

	// 演示删除
	delete(cities, "no1")
	fmt.Println(cities)
	// 当delete指定的key不存在时，删除不会操作，也不会报错
	delete(cities, "no1")
	fmt.Println(cities)
}
```

map删除细节说明：

1、如果我们要删除map的所有key，没有一个专门的方法一次删除，可以遍历一下key，逐个删除

2、或者 map = make(...)，make一个新的，让原来的成为垃圾，被GC回收

```go
// 1、如果我们要删除map的所有key，没有一个专门的方法一次删除，可以遍历一下key，逐个删除
// 2、或者 map = make(...)，make一个新的，让原来的成为垃圾，被GC回收
	cities = make(map[string]string)
	fmt.Println(cities)
```

map查找：

```go
	// 演示map的查找
	val, ok := cities["no1"]
	if ok {
		fmt.Printf("有no1 ok 值为%v\n", val)
	} else {
		fmt.Printf("没有no1 key\n")
	}
```

对上面代码的说明：如果heroes这个map中存在"no1"，那么ok就会返回true，否则返回false

## map的遍历

说明：map的遍历使用for-range的结构遍历

```go
package main

import "fmt"

func main() {
	// 使用for-range遍历map
	cities := make(map[string]string)
	cities["no1"] = "北京"
	cities["no2"] = "天津"
	cities["no3"] = "上海"

	for k, v := range cities {
		fmt.Printf("k=%v v=%v \n", k, v)
	}
	// 获取map的长度：len(mapName)
	fmt.Println("cities 有", len(cities), "对key-value")

	// 使用for-range遍历一个结构比较复杂的map
	studentMap := make(map[string]map[string]string)
	studentMap["stu01"] = make(map[string]string) // 这句话不能少，少了会报错
	studentMap["stu01"]["name"] = "tom"
	studentMap["stu01"]["sex"] = "男"
	studentMap["stu01"]["address"] = "北京长安街"

	studentMap["stu02"] = make(map[string]string) // 这句话不能少，少了会报错
	studentMap["stu02"]["name"] = "marry"
	studentMap["stu02"]["sex"] = "女"
	studentMap["stu02"]["address"] = "上海陆家嘴"

	fmt.Println(studentMap)
	fmt.Println(studentMap["stu02"])
	fmt.Println(studentMap["stu02"]["address"])

	// 双层for-range遍历双层map
	for k1, v1 := range studentMap {
		fmt.Println("k1=", k1)
		for k2, v2 := range v1 {
			fmt.Printf("\t k2=%v v2=%v\n", k2, v2)
		}
		fmt.Println()
	}
}
```

## map的长度

```go
// 获取map的长度：len(mapName)
	fmt.Println("cities 有", len(cities), "对key-value")
```

## map切片

切片的数据类型如果是map，则我们称为slice of map，map切片，这样使用则map个数就可以动态变化了

 要求：使用一个map来记录妖怪monster的信息name和age，也就是说一个monster对应一个map，并且妖怪的个数可以动态的增加=>map切片

```go
package main

import "fmt"

func main() {
	// 演示map切片的使用

	// 要求：使用一个map来记录妖怪monster的信息name和age，也就是说一个monster对应一个map，
	// 并且妖怪的个数可以动态的增加=>map切片

	// 1、声明一个map切片
	monsters := make([]map[string]string, 2) // 准备放入两个妖怪
	// 2、增加第一个妖怪的信息
	if monsters[0] == nil {
		monsters[0] = make(map[string]string)
		monsters[0]["name"] = "牛魔王"
		monsters[0]["age"] = "500"
	}
	// 下面这个写法越界了
	// if monsters[1] == nil {
	// 	monsters[1] = make(map[string]string)
	// 	monsters[1]["name"] = "玉兔精"
	// 	monsters[1]["age"] = "400"
	// }

	// 这里需要用到切片的append函数，可以动态的增加monster
	// 1、先定义一个monster信息
	newMonster := map[string]string{
		"name": "新的妖怪~火云邪神",
		"age":  "200",
	}
	monsters = append(monsters, newMonster)
	fmt.Println(monsters)
}

```



## map排序

1、golang中没有一个专门的方法针对map的key进行排序

2、golang中的map默认是无序的，注意也不是按照添加的顺序存放的，你每次遍历，得到的输出可能不一样

3、golang中map的排序，是先将key进行排序，然后根据key值遍历输出即可

```go
package main

import (
	"fmt"
	"sort"
)

func main() {
	// map的排序
	map1 := make(map[int]int)
	map1[10] = 100
	map1[1] = 13
	map1[4] = 56
	map1[8] = 90
	fmt.Println(map1)

	// 如果按照map的key的顺序进行排序输出
	// 1、先将map的key放入到 切片中
	// 2、对切片排序
	// 3、遍历切片，然后按照key输出map的值

	var keys []int
	for k := range map1 {
		keys = append(keys, k)
	}

	// 排序
	sort.Ints(keys)
	fmt.Println(keys)

	for _, k := range keys {
		fmt.Printf("map1[%v]=%v\n", k, map1[k])
	}

}

```



## map使用细节

1、map是引用类型，遵守引用类型传递的机制，在一个函数接受map，修改后，会直接修改原来的map



```go
package main

import "fmt"

func modify(map1 map[int]int) {
	map1[10] = 900
}

func main() {
	// map是引用类型，遵守引用类型传递的机制，在一个函数接受map，修改后，会直接修改原来的map
	map1 := make(map[int]int)
	map1[1] = 90
	map1[2] = 88
	map1[10] = 1
	map1[20] = 2
	modify(map1)
	// 看看结果，map1[10] = 900，说明map是引用类型
	fmt.Println(map1)
}

```

2、map的容量达到后，再向map增加元素，会自动扩容，并不会发生panic，也就是说map能 动态的增长键值对(key-value)

3、map的value也经常使用struct类型，更适合管理复杂的数据

```go
package main

import "fmt"

func modify(map1 map[int]int) {
	map1[10] = 900
}

// 定义一个学生结构体
type Stu struct {
	Name    string
	Age     int
	Address string
}

func main() {
	// map是引用类型，遵守引用类型传递的机制，在一个函数接受map，修改后，会直接修改原来的map
	map1 := make(map[int]int)
	map1[1] = 90
	map1[2] = 88
	map1[10] = 1
	map1[20] = 2
	modify(map1)
	// 看看结果，map1[10] = 900，说明map是引用类型
	fmt.Println(map1)

	// map的value也经常使用struct类型，更适合管理复杂的数据
	// 1、map的key为学生的学号，是唯一的
	// 2、map的value为结构体，包含学生的名字、年龄、地址

	students := make(map[string]Stu)
	stu1 := Stu{Name: "tom", Age: 18, Address: "北京"}
	stu2 := Stu{Name: "marry", Age: 28, Address: "上海"}
	students["no1"] = stu1
	students["no2"] = stu2
	fmt.Println(students)

	// 遍历各个学生信息

	for k, v := range students {
		fmt.Printf("学生的编号是：%v\n", k)
		fmt.Printf("学生的名字是：%v\n", v.Name)
		fmt.Printf("学生的年龄是：%v\n", v.Age)
		fmt.Printf("学生的地址是：%v\n", v.Address)
	}

}
```



## map综合应用实例

1、使用map[string]map[string]string 的map类型

2、key：表示用户名，是唯一的，不可以重复

3、如果某个用户名存在，就将其密码修改为"888888"，如果不存在就增加这个用户信息，（包括昵称nickname和 密码pwd）

4、编写一个函数modifyUser(users mapp[string]map[string]string,name string)完成上述功能

```go
package main

import "fmt"

func modifyUser(users map[string]map[string]string, name string) {
	// 判断users中是否有name
	// v, ok := users[name]
	if users[name] != nil {
		// 有这个用户
		users[name]["pwd"] = "888888"

	} else {
		// 没有这个用户
		users[name] = make(map[string]string, 2)
		users[name]["pwd"] = "888888"
		users[name]["nickname"] = "昵称～" + name
	}
}
func main() {
	users := make(map[string]map[string]string, 10)
	users["smith"] = make(map[string]string, 2)
	users["smith"]["pwd"] = "999999"
	users["smith"]["nickname"] = "小花猫"

	modifyUser(users, "tom")
	modifyUser(users, "marry")
	modifyUser(users, "smith")
	fmt.Println(users)
}

```



# 第十章_面向对象编程(上)



## go独树一帜的面向对象特点

一个程序就是一个世界，有很多对象（变量）

1、golang也支持面向对象编程（OOP），但是和传统的面向对象编程有区别，并不是纯粹的面向对象语言，所以我们说golang支持面向对象编程特性是比较准确的

2、golang没有类（class），go语言的结构体（struct）和其它编程语言的类（class）有同等的地位，你可以理解golang是基于struct来实现OPP特性的

3、golang面向对象编程非常简洁，去掉了传统OPP语言的继承、发放重载、构造函数和析构函数、隐藏的this指针等等

4、golang仍然有面向对象编程的继承，封装和多态的特性，知识实现的方式和其它OOP语言不一样，比如继承：golang没有extends关键字，继承是通过匿名字段来实现

5、golang面向对象（OOP）很优雅，OOP本身就是语言类型系统（type system）的一部分，通过接口（interface）关联，耦合性低，也非常灵活，也就是说在golang中面向接口编程是非常重要的特性

## go面向对象编程快速入门

```go
package main

import "fmt"

func main() {
	// 定义一个Cat结构体，将cat的各个字段/属性信息，放入到Cat结构体进行管理
	type Cat struct {
		Name  string
		Age   int
		Color string
		Hobby string
	}

	// 创建一个 Cat 的变量
	var cat1 Cat // var a int
	cat1.Name = "小白"
	cat1.Age = 3
	cat1.Color = "白色"
	cat1.Hobby = "吃鱼"
	fmt.Println("cat1=", cat1)
	fmt.Println("猫猫的信息如下：")
	fmt.Println("name=", cat1.Name)
	fmt.Println("age=", cat1.Age)
	fmt.Println("color=", cat1.Color)
	fmt.Println("hobby=", cat1.Hobby)

}

```



## 结构体声明和使用陷阱

字段/属性注意事项：

1、字段声明语法同变量，实例：字段名 字段类型

2、字段的类型可以为：基本类型、数组或引用类型

3、在创建一个结构体变量后，如果没有给字段赋值，都对应一个零值（默认值）

4、不同结构体变量的字段是独立的，互不影响，一个结构体变量字段的更改，不影响另外一个，结构体是值类型！

```go
package main

import (
	"fmt"
)

//如果结构体的字段类型是: 指针，slice，和map的零值都是 nil ，即还没有分配空间
//如果需要使用这样的字段，需要先make，才能使用.

type Person struct {
	Name   string
	Age    int
	Scores [5]float64
	ptr    *int              //指针
	slice  []int             //切片
	map1   map[string]string //map
}

type Monster struct {
	Name string
	Age  int
}

func main() {

	//定义结构体变量
	var p1 Person
	fmt.Println(p1)

	if p1.ptr == nil {
		fmt.Println("ok1")
	}

	if p1.slice == nil {
		fmt.Println("ok2")
	}

	if p1.map1 == nil {
		fmt.Println("ok3")
	}

	//使用slice, 再次说明，一定要make
	p1.slice = make([]int, 10)
	p1.slice[0] = 100 //ok

	//使用map, 一定要先make
	p1.map1 = make(map[string]string)
	p1.map1["key1"] = "tom~"
	fmt.Println(p1)

	//不同结构体变量的字段是独立，互不影响，一个结构体变量字段的更改，
	//不影响另外一个, 结构体是值类型
	var monster1 Monster
	monster1.Name = "牛魔王"
	monster1.Age = 500

	monster2 := monster1 //结构体是值类型，默认为值拷贝
	monster2.Name = "青牛精"

	fmt.Println("monster1=", monster1) //monster1= {牛魔王 500}
	fmt.Println("monster2=", monster2) //monster2= {青牛精 500}

}

```



## 创建结构体实例的四种方式

```go
package main

import "fmt"

type Person struct {
	Name string
	Age  int
}

func main() {
	// 方式一

	// 方式二：
	p2 := Person{"mary", 18}
	p2.Name = "tom"
	p2.Age = 18
	fmt.Println(p2)

	// 方式三
	var p3 *Person = new(Person)
	// 因为p3是一个指针，因此标准的给字段赋值方式
	(*p3).Name = "smith"
	(*p3).Age = 30
	// 上面的写法 (*p3).Name = "smith" 也可以这样写：p3.Name = "smith"
	// 原因：go的设计者 为了程序员使用方便，底层会对 p3.Name = "smith" 进行处理
	// 会给 p3 加上取值运算 (*p3).Name = "smith"
	p3.Name = "john"
	p3.Age = 100
	fmt.Println(*p3)

	// 方式四
	// 下面语句，也可以直接给字段赋值
	// var person *Person = &Person{"mary", 60}
	var person *Person = &Person{}
	// 因为person是一个指针，因此标准的访问字段的方法
	// (*person).Name = "scott"
	// go的设计者为了程序员使用方便，也可以person.Name = "scott"
	// 原因和上面一样，底层会对 person.Name = "scott" 进行处理，会加上 (*person)
	(*person).Name = "scott"
	person.Name = "scott~"
	(*person).Age = 88
	person.Age = 10
	fmt.Println(*person)

}

```

说明：

1、第3种 和 第4种方式返回的是结构体指针

2、结构体指针访问字段的标准方式应该是：(结构体指针).字段名，比如（person).Name = "tom"

3、但go做了一个简化，也支持 结构体指针.字段名，比如person.Name = "tom"，更加符合程序员使用习惯，go编译器底层对person.Name做了转化（*person).Name

## 结构体使用细节

1、结构体的所有字段在内存中是连续的

2、结构体是用户单独定义的类型，和其它类型进行转换时需要有完全相同的字段（名字、个数、类型）

```go
package main

import "fmt"

// 结构体
type A struct {
	Num int
}

// 结构体
type B struct {
	Num int
}

func main() {
	var a A
	var b B
	a = A(b) // 可以转换，但是有要求：结构体的字段要完全一样（包括：名字、个数、类型）
	fmt.Println(a, b)
}

```

3、结构体进行type重新定义（相当于取别名），golang认为是新的数据类型，但是相互间可以强转

4、struct的每个字段上，可以写上一个tag，该tag可以通过反射机制获取，常见的使用场景就是序列化和反序列化

```go
package main

import (
	"encoding/json"
	"fmt"
)

type A struct {
	Num int
}
type B struct {
	Num int
}

type Monster struct {
	Name  string `json:"name"` // `json:"name"` 就是 struct tag
	Age   int    `json:"age"`
	Skill string `json:"skill"`
}

func main() {
	var a A
	var b B
	a = A(b) // ? 可以转换，但是有要求，就是结构体的的字段要完全一样(包括:名字、个数和类型！)
	fmt.Println(a, b)

	//1. 创建一个Monster变量
	monster := Monster{"牛魔王", 500, "芭蕉扇~"}

	//2. 将monster变量序列化为 json格式字串
	//   json.Marshal 函数中使用反射，这个讲解反射时，我会详细介绍
	jsonStr, err := json.Marshal(monster)
	if err != nil {
		fmt.Println("json 处理错误 ", err)
	}
	fmt.Println("jsonStr", string(jsonStr))

}

```



## 方法介绍和使用

golang中的方法是作用在指定的数据类型上的（即：和指定的数据类型绑定），因此自定义类型，都可以有方法，而不仅仅是struct

```go
type A struct{
	Num int
}

func(aA) test(){
  fmt.Println(a.Num)
}

```

对上面语法的说明：

1、func(aA) test() {} 表示A结构体有一方法，方法名为test

2、（aA）体现test方法是和A类型绑定的

```go
package main

import "fmt"

type Person struct {
	Name string
}

// 给Person类型绑定一个方法
func (p Person) test() {
	fmt.Println("test() Name =", p.Name)
}
func main() {
	var p Person
	p.Name = "tom"
	p.test() // 调用方法
}

```

对上面的代码总结：

1、test方法和Person类型绑定

2、test方法只能通过Person类型的变量来调用，不能直接调用，也不能使用其他类型变量调用

```go
	// 下面的使用方式都是错误的
	var dog Dog
	dog.test()
	test()
```

3、func (p Person) test() {}	p表示哪个Person变量调用，这个p就是它的副本，这点和函数传参非常相似

4、p这个名字，可以随意指定，不是固定的，比如修改成person也是可以的

```go
package main

import "fmt"

type Person struct {
	Name string
}

type Dog struct {
}

// 给Person类型绑定一个方法
func (p Person) test() {
	p.Name = "jack"
	fmt.Println("test() Name =", p.Name) // 输出jack
}
func main() {
	var p Person
	p.Name = "tom"
	p.test()                              // 调用方法
	fmt.Println("main() p.Name=", p.Name) // 输出tom

	// 下面的使用方式都是错误的
	// var dog Dog
	// dog.test()
	// test()
}

```



## 方法的快速入门

1、给Person结构体添加 speak 方法，输出 xxx是一个好人

```go
func (p Person) speak() {
	fmt.Println(p.Name, "是一个好人")
}
func main() {
	var p Person
	p.Name = "tom"
	p.speak()
}

```

2、给Person结构体添加jisuan方法，可以计算从 1+...+1000 的结果（说明方法体内可以和函数一样，进行各种运算）

```go
// 2、给Person结构体添加jisuan方法，可以计算从 1+...+1000 的结果
//（说明方法体内可以和函数一样，进行各种运算）
func (p Person) jisuan() {
	res := 0
	for i := 1; i <= 1000; i++ {
		res += i
	}
	fmt.Println(p.Name, "计算结果是：", res)
}
```

3、给Peson结构体jisuan2方法，该方法可以接收一个数n，计算从1+...+n的结果

```go
// 3、给Person结构体jisuan2方法，该方法可以接收一个参数n，计算从1+...+n的结果
func (p Person) jisuan2(n int) {
	res := 0
	for i := 1; i <= n; i++ {
		res += i
	}
	fmt.Println(p.Name, "计算结果是：", res)
}
```

4、给Person结构体添加getSum方法，可以计算两个数的和，并返回结果

```go
// 4、给Person结构体添加getSum方法，可以计算两个数的和，并返回结果
func (p Person) getSum(n1 int, n2 int) int {
	return n1 + n2
}
```

5、方法的调用

```go
package main

import "fmt"

type Person struct {
	Name string
}

// 1、给Person结构体添加 speak 方法，输出 xxx是一个好人
func (p Person) speak() {
	fmt.Println(p.Name, "是一个好人")
}

// 2、给Person结构体添加jisuan方法，可以计算从 1+...+1000 的结果
//（说明方法体内可以和函数一样，进行各种运算）
func (p Person) jisuan() {
	res := 0
	for i := 1; i <= 1000; i++ {
		res += i
	}
	fmt.Println(p.Name, "计算结果是：", res)
}

// 3、给Person结构体jisuan2方法，该方法可以接收一个参数n，计算从1+...+n的结果
func (p Person) jisuan2(n int) {
	res := 0
	for i := 1; i <= n; i++ {
		res += i
	}
	fmt.Println(p.Name, "计算结果是：", res)
}

// 4、给Person结构体添加getSum方法，可以计算两个数的和，并返回结果
func (p Person) getSum(n1 int, n2 int) int {
	return n1 + n2
}

// 给Person类型绑定一个方法
func (p Person) test() {
	p.Name = "jack"
	fmt.Println("test() Name =", p.Name) // 输出jack
}
func main() {
	var p Person
	p.Name = "tom"
	p.test()                              // 调用方法
	fmt.Println("main() p.Name=", p.Name) // 输出tom

	// 下面的使用方式都是错误的
	// var dog Dog
	// dog.test()
	// test()

	// 1、调用
	p.speak()
	// 2、调用
	p.jisuan()
	// 3、调用
	p.jisuan2(10)
	// 4、调用
	res := p.getSum(10, 20)
	fmt.Println("res= ", res)
}

```



## 方法的调用和传参机制

说明：方法的调用和传参机制和函数基本一样，不一样的地方是方法调用时，会将调用方法的变量，当做实参也传递给方法

1、在通过一个变量去调用方法时，其调用机制和函数一样

2、不一样的地方是，变量调用方法时，该变量本身也会作为一个参数传递到方法（如果变量是值类型，则进行值拷贝；如果变量时引用类型，则进行地址拷贝）

请编写一个程序，要求如下：

1、声明一个结构体Circle，字段为 radius，声明一个方法area和Circle绑定，可以返回面积

```go
package main

import "fmt"

type Circle struct {
	radius float64
}

func (c *Circle) area() float64 {
	return c.radius * c.radius * 3.14
}

func main() {
	// 声明一个结构体Circle，字段为 radius，声明一个方法area和Circle绑定，可以返回面积
	// 创建一个结构体变量
	var circle Circle
	circle.radius = 4.0
	mianji := circle.area()
	fmt.Println("面积是：", mianji)
}

```

## 方法声明（定义）

```go
func (recevier type) methodName (参数列表) (返回值列表) {
  	方法体
    return 返回值
}
```

1、参数列表：表示方法输入

2、recevier type：表示这个方法和type这个类型进行绑定，或者说该方法作用于type类型

3、recevier type：type可以是结构体，也可以是其他的自定义类型

4、recevier：就是type类型的一个变量（实例），比如：Person结构体的一个变量（实例）

5、返回值列表：表示返回的值，可以是多个

6、方法主体：表示为了实现某一功能代码块

7、return语句不是必须的（有了“返回值列表”就必须return）

## 方法注意事项和细节

1、结构体类型是值类型，在方法调用中，遵守值类型的传递机制，是值拷贝传递方式

2、如希望在方法中，修改结构体变量的值，可以通过结构体指针的方式来处理【效率高】

```go
// 2、如希望在方法中，修改结构体变量的值，可以通过结构体指针的方式来处理【效率高】
package main

import "fmt"

type Circle struct {
	radius float64
}

func (c Circle) area() float64 {
	return c.radius * c.radius * 3.14
}

// 为了提高效率，通常我们方法和结构体的指针类型绑定
func (c *Circle) area2() float64 {
	// 因为c是指针，因此我们标准的访问其字段的方式是(*c).radius
	// return (*c).radius * (*c).radius * 3.14
	// (*c).radius 等价于 c.radius
	return c.radius * c.radius * 3.14
}

func main() {
	// 声明一个结构体Circle，字段为 radius，声明一个方法area和Circle绑定，可以返回面积
	// 创建一个结构体变量
	var circle Circle
	circle.radius = 7.0
	mianji := circle.area()
	// 指针标准调用方法
	// mianji2 := (&circle).area2()
	// 编译器底层做了优化 (&circle).area2() 等价于 circle.area2()
	// 因为编译器会自动给加上 &
	mianji2 := circle.area2()
	fmt.Println("面积是：", mianji)
	fmt.Println("面积是：", mianji2)
}

```

3、golang中的方法作用在指定的数据类型上的（即：和指定的数据类型绑定），因此自定义类型，都可以有方法，而不仅仅是struct，比如int、float32等都可以有方法

```go
package main

import "fmt"

// 3、golang中的方法作用在指定的数据类型上的（即：和指定的数据类型绑定），
// 因此自定义类型，都可以有方法，而不仅仅是struct，比如int、float32等都可以有方法
type integer int

func (i integer) print() {
	fmt.Println("i=", i)
}

// 请编写一个方法，可以改变i的值
func (i *integer) change() {
	*i = *i + 1
}
func main() {
	var i integer = 10
	i.print()
	i.change()
	fmt.Println("i=", i)
}

```

4、方法的访问范围控制的规则，和函数一样。方法名首字母小写，只能在本包访问，方法首字母大写，可以在本包和其它包访问

5、如果一个类型实现了String()这个方法，那么fmt.Println默认会调用这个变量的Sting()进行输出

```go
package main

import "fmt"

// 3、golang中的方法作用在指定的数据类型上的（即：和指定的数据类型绑定），
// 因此自定义类型，都可以有方法，而不仅仅是struct，比如int、float32等都可以有方法
type integer int

func (i integer) print() {
	fmt.Println("i=", i)
}

// 请编写一个方法，可以改变i的值
func (i *integer) change() {
	*i = *i + 1
}

type Student struct {
	Name string
	Age  int
}

// 给student实现方法String()
func (stu *Student) String() string {
	str := fmt.Sprintf("Name=[%v] Age=[%v]", stu.Name, stu.Age)
	return str
}

func main() {
	var i integer = 10
	i.print()
	i.change()
	fmt.Println("i=", i)

	// 定义一个Student变量
	stu := Student{
		Name: "tom",
		Age:  20,
	}
	fmt.Println(stu)
	// 如果已实现了 *student 类型的 String方法，就会自动调用
	fmt.Println(&stu)
}

```

## 方法练习题

1、编写结构体(MethodUtils)，编程一个方法，方法不需要参数，在方法中打印 10 * 8 的矩形，在main方法中调用该方法

2、编写一个方法，提供 m 和 n 两个参数，方法中打印一个 m*n 的矩形

3、编写一个方法算该矩形的面积（可以接收长len，和宽width），将其作为方法返回值，在main方法中调用该方法，接收返回的面积值并打印

```go
package main

import "fmt"

type MothodUtils struct {
}

// 给MothodUtils编写方法
func (mu MothodUtils) Print() {
	for i := 1; i <= 10; i++ {
		for j := 1; j <= 8; j++ {
			fmt.Print("*")
		}
		fmt.Println()
	}
}

// 2、编写一个方法，提供 m 和 n 两个参数，方法中打印一个 m*n 的矩形
func (mu MothodUtils) Print2(m int, n int) {
	for i := 1; i <= m; i++ {
		for j := 1; j <= n; j++ {
			fmt.Print("*")
		}
		fmt.Println()
	}
}

// 3、编写一个方法算该矩形的面积（可以接收长len，和宽width），将其作为方法返回值，在main方法中调用该方法，接收返回的面积值并打印
func (mu MothodUtils) area(len float64, width float64) float64 {
	return len * width
}

func main() {
	// 1、编写结构体(MethodUtils)，编程一个方法，方法不需要参数，在方法中打印 10 * 8 的矩形，在main方法中调用该方法
	var mu MothodUtils
	mu.Print()
	fmt.Println()
	mu.Print2(5, 20)
	fmt.Println()
	areaRes := mu.area(2, 3)
	fmt.Println("面积是：", areaRes)

}

```

 4、编写一个方法：判断一个数是奇数还是偶数

5、根据行、列、字符打印 对应行数和列数的字符，比如：  行：3，列：2，字符*，则打印相应的效果

6、定义小小计算器结构体(Calcuator)，实现加减乘除四个功能

​	实现形式1：分四个方法完成

​	实现形式2：用一个方法搞定

```go
package main

import "fmt"

type MothodUtils struct {
}

// 给MothodUtils编写方法
func (mu MothodUtils) Print() {
	for i := 1; i <= 10; i++ {
		for j := 1; j <= 8; j++ {
			fmt.Print("*")
		}
		fmt.Println()
	}
}

// 2、编写一个方法，提供 m 和 n 两个参数，方法中打印一个 m*n 的矩形
func (mu MothodUtils) Print2(m int, n int) {
	for i := 1; i <= m; i++ {
		for j := 1; j <= n; j++ {
			fmt.Print("*")
		}
		fmt.Println()
	}
}

// 3、编写一个方法算该矩形的面积（可以接收长len，和宽width），将其作为方法返回值，在main方法中调用该方法，接收返回的面积值并打印
func (mu MothodUtils) area(len float64, width float64) float64 {
	return len * width
}

// 4、编写一个方法：判断一个数是奇数还是偶数
func (mu *MothodUtils) JudgeNum(num int) {
	if num%2 == 0 {
		fmt.Println(num, "是偶数...")
	} else {
		fmt.Println(num, "是奇数...")
	}
}

// 5、根据行、列、字符打印 对应行数和列数的字符，比如：  行：3，列：2，字符*，则打印相应的效果
func (mu *MothodUtils) Print3(n int, m int, key string) {
	for i := 1; i <= n; i++ {
		for j := 1; j <= m; j++ {
			fmt.Print(key)
		}
		fmt.Println()
	}
}

// 6、定义小小计算器结构体(Calcuator)，实现加减乘除四个功能
// 实现形式1：分四个方法完成，分别计算 + - * /
// 实现形式2：用一个方法搞定，需要接受两个数，还有一个运算符
// 实现形式1演示：
type Calcuator struct {
	Num1 float64
	Num2 float64
}

func (calcuator *Calcuator) getSum() float64 {
	return calcuator.Num1 + calcuator.Num2
}
func (calcuator *Calcuator) getSub() float64 {
	return calcuator.Num1 - calcuator.Num2
}

// 实现形式2演示：
func (calcuator *Calcuator) gerRes(operator byte) float64 {
	res := 0.0
	switch operator {
	case '+':
		res = calcuator.Num1 + calcuator.Num2
	case '-':
		res = calcuator.Num1 - calcuator.Num2
	case '*':
		res = calcuator.Num1 * calcuator.Num2
	case '/':
		res = calcuator.Num1 / calcuator.Num2
	default:
		fmt.Println("您输入的运算符暂不支持")
	}
	return res
}
func main() {
	// 1、编写结构体(MethodUtils)，编程一个方法，方法不需要参数，在方法中打印 10 * 8 的矩形，在main方法中调用该方法
	var mu MothodUtils
	mu.Print()
	fmt.Println()

	mu.Print2(5, 20)
	fmt.Println()

	areaRes := mu.area(2, 3)
	fmt.Println("面积是：", areaRes)

	mu.JudgeNum(0)

	mu.Print3(20, 7, "#")

	// 测试一下：
	// 创建calcuator结构体变量
	var calcuator Calcuator
	calcuator.Num1 = 1.2
	calcuator.Num2 = 2.2
	fmt.Println("sum=", fmt.Sprintf("%.2f", calcuator.getSum()))
	fmt.Println("sub=", fmt.Sprintf("%.2f", calcuator.getSub()))

	res := calcuator.gerRes('*')
	fmt.Println("res = ", fmt.Sprintf("%.2f", res))
}

```



## 方法和函数的区别

1、调用方式不一样

​	函数的调用方式：函数名（实参列表）

​	方法的调用方式：变量.方法名（实参列表）

2、对于普通函数，接收者为值类型时，不能将指针类型的数据直接传递，反之亦然

3、对于方法（如struct的方法），接收者为值类型时，可以直接用指针类型的变量调用方法，反过来同样也可以

```go
package main

import "fmt"

type Person struct {
	Name string
}

// 函数
// 2、对于普通函数，接收者为值类型时，不能将指针类型的数据直接传递，反之亦然
func test01(p Person) {
	fmt.Println(p.Name)
}

func test02(p *Person) {
	fmt.Println(p.Name)
}

// 3、对于方法（如struct的方法）
// 接收者为值类型时，可以直接用指针类型的变量调用方法，反过来同样也可以
func (p Person) test03() {
	p.Name = "jack"
	fmt.Println("test03()=", p.Name) // jack
}
func (p *Person) test04() {
	p.Name = "mary"
	fmt.Println("test04()=", p.Name) // mary
}

func main() {
	p := Person{"tom"}
	test01(p)
	test02(&p)

	p.test03()
	fmt.Println("main() p.Name=", p.Name) // tom
	(&p).test03()                         // 从形式上是传入地址，但是本质仍然是值拷贝
	fmt.Println("main() p.Name=", p.Name) // tom

	(&p).test04()
	p.test04()                            // 等价于上面的写法，从形式上是传入值类型，但是本质仍然是地址拷贝，关键看func(p *Person)绑定的是什么
	fmt.Println("main() p.Name=", p.Name) // mary
}

```

总结：

1、不管调用形式如何，其真正决定是值拷贝还是地址拷贝，主要是看这个方法是和哪个类型绑定的

2、如果是和值类型，比如（p Person）：则是值拷贝；如果和指针类型，比如（p *person）：则是地址拷贝



## 面向对象编程应用实例

步骤：

1、声明（定义）结构体，确定结构体名

2、编写结构体的字段

3、编写结构体的方法

### 学生案例

1、 编写一个Student结构体，包含name、gender、age、id、score字段，分别为string、string、int、int、float64类型 

2、结构体中声明一个say方法，返回string类型，方法返回信息中包括所有字段值

3、在main方法中，创建Student结构体实例（变量），并访问say方法，并将调用结果打印输出

```go
package main

import "fmt"

// 1、 编写一个Student结构体，包含name、gender、age、id、score字段，分别为string、string、int、int、float64类型
// 2、结构体中声明一个say方法，返回string类型，方法返回信息中包括所有字段值
// 3、在main方法中，创建Student结构体实例（变量），并访问say方法，并将调用结果打印输出

type Student struct {
	name   string
	gender string
	age    int
	id     int
	score  float64
}

func (student *Student) say() string {
	infoStr := fmt.Sprintf("student的信息 name=[%v]  gender=[%v]  age=[%v]  id=[%v]  score=[%v]", student.name, student.gender, student.age, student.id, student.score)
	return infoStr
}
func main() {
	// 测试
	// 创建一个Student实例变量
	var stu = Student{
		name:   "tom",
		gender: "male",
		age:    18,
		score:  22.28,
	}
	fmt.Println(stu.say())
}

```



### 盒子案例

1、编程创建一个Box结构体，在其中声明三个字段表示一个立方体的长、宽、高，长宽高要从终端获取

2、声明一个方法获取立方体的体积

3、创建一个Box结构体变量，打印给定尺寸的立方体的体积

```go
package main

import "fmt"

// 1、编程创建一个Box结构体，在其中声明三个字段表示一个立方体的长、宽、高，长宽高要从终端获取
// 2、声明一个方法获取立方体的体积
// 3、创建一个Box结构体变量，打印给定尺寸的立方体的体积
type Box struct {
	len    float64
	width  float64
	height float64
}

func (box *Box) getVolumn() float64 {
	return box.len * box.width * box.height
}

func main() {
	// 测试
	// 创建一个Student实例变量
	var stu = Student{
		name:   "tom",
		gender: "male",
		age:    18,
		score:  22.28,
	}
	fmt.Println(stu.say())

	// 测试代码
	var box Box
	box.len = 1.1
	box.width = 2.2
	box.height = 3.3
	volumn := box.getVolumn()
	fmt.Println("体积=", fmt.Sprintf("%.2f", volumn))
}
```



### 景区门票案例

1、一个景区根据游人的年龄收取不同价格的门票，比如年龄大于18，收费20元，其它情况门票免费

2、请编写Visitor结构体，根据年龄段决定能够购买的门票价格并输出

```go
package main

import "fmt"

// 1、一个景区根据游人的年龄收取不同价格的门票，比如年龄大于18，收费20元，其它情况门票免费
// 2、请编写Visitor结构体，根据年龄段决定能够购买的门票价格并输出
type Visitor struct {
	Name string
	Age  int
}

func (visitor *Visitor) showPrice() {
	if visitor.Age >= 90 || visitor.Age <= 8 {
		fmt.Println("考虑到安全，即iu不要玩了")
		return
	}
	if visitor.Age > 18 {
		fmt.Printf("游客的名字为:%v 年龄为:%v 收费20元\n", visitor.Name, visitor.Age)
	} else {
		fmt.Printf("游客的名字为:%v 年龄为:%v 免费！\n", visitor.Name, visitor.Age)
	}
}

func main() {
	// 测试
	var v Visitor
	for {
		fmt.Println("请输入你的名字：")
		fmt.Scanln(&v.Name)
		fmt.Println("请输入你的年龄：")
		fmt.Scanln(&v.Age)
		v.showPrice()

	}
}
```



## 创建struct实例指定字段值

golang在创建结构体实例（变量）时，可以直接指定字段的值

1、方式一：

```go
var stu1 Student = Student{"tom",18}

stu2 := Student{"tom~",19}

var stu3 Student = Student{
  Name: "mary",
  Age: 30,
}

stu4 := Student{
  Name: "mary~"
  Age: 20,
}
```

2、方式二：

```go
var stu5 *Student = &Student{"smith", 30}
var stu6 *Student = &Student{
  Name: "scott",
  Age: 80,
}
```

完整代码：

```go
package main

import "fmt"

type Stu struct {
	Name string
	Age  int
}

func main() {
	// 在创建结构体变量时，就直接指定字段的值,顺序必须与结构体内定义的字段顺序一致
	var stu1 = Stu{"小明", 19}
	stu2 := Stu{"小明～", 20}

	// 在创建结构体变量时，把字段名和字段值写在一起，这种写法就不依赖字段的定义顺序【稳健】
	var stu3 = Stu{
		Name: "jack",
		Age:  20,
	}
	stu4 := Stu{
		Age:  30,
		Name: "mary",
	}
	fmt.Println(stu1, stu2, stu3, stu4)

	// 方式二：返回结构体的指针类型【重要】
	var stu5 = &Stu{"小王", 29} // stu2 --> 地址 --> 结构体数据[xxxx,xxx]
	stu6 := &Stu{"小王～", 39}

	//在创建结构体指针变量时，把字段名和字段值写在一起，这种写法就不依赖字段的定义顺序
	var stu7 = &Stu{
		Name: "小李",
		Age:  49,
	}
	stu8 := &Stu{
		Age:  59,
		Name: "小李～",
	}
	fmt.Println(*stu5, *stu6, *stu7, *stu8)

}

```



## 工厂模式详解

说明：golang的结构体没有构造函数，通常可以使用工厂模式来解决这个问题

看一个需求：一个结构体的声明是这样的：

```go
package model

type Student struct {
  Name string...
}
```

因为这里的Student的首字母 s 是大写的，如果我们想在其它包创建Student的实例（比如main包），引入model包后，就可以直接创建Student结构体的变量（实例）。但是问题来了，如果首字母是小写的，比如 是type sudent struct{...} 就不行了，需要--->工厂模式解决

使用工厂模式实现跨包创建结构体实例（变量）的案例：

如果model包的结构体变量首字母大写，引入后，直接使用，没有问题

```go
package model

//定义一个结构体
type Student struct {
	Name  string
	Score float64
}
```

```go
package main
import (
	"fmt"
	"goproject/src/go_code/chapter10/factory/model"
)

func main() {
	// 创建一个Student实例
	var stu = model.Student{
		Name:  "tom",
		Score: 78.9,
	}
	fmt.Println(stu)
}
```

如果model包的 结构体变量首字母小写，引入后，不能直接使用，可以工厂模式解决（公有方法调用私有字段）

```go
// student.go
package model

//定义一个结构体
type student struct {
	Name  string
	Score float64
}

// 因为student结构体首字母是小写，因此只能在model包使用
// 通过工厂模式来解决

func NewStudent(n string, s float64) *student {
	return &student{
		Name:  n,
		Score: s,
	}
}

```

```go
// main.go
package main

import (
	"fmt"
	"goproject/src/go_code/chapter10/factory/model"
)

func main() {
	// 创建一个Student实例
	// var stu = model.Student{
	// 	Name:  "tom",
	// 	Score: 78.9,
	// }

	// 如果student结构体是首字母小写，我们可以通过工厂模式来解决
	var stu = model.NewStudent("tom~", 88.8)

	fmt.Println(stu)                                       // &{tom~ 88.8}
	fmt.Println(*stu)                                      // {tom~ 88.8}
	fmt.Println("name=", (*stu).Name, "score=", stu.Score) // {tom~ 88.8}
}

```



思考一下，如果model包的student的结构体的字段Score改成score，我们还能正常访问吗

```go
// student.go
package model

//定义一个结构体
type student struct {
	Name  string
	score float64
}

// 因为student结构体首字母是小写，因此只能在model包使用
// 通过工厂模式来解决

func NewStudent(n string, s float64) *student {
	return &student{
		Name:  n,
		score: s,
	}
}

// 如果score字段首字母小写，则在其它包不可以直接访问，我们可以提供一个方法
func (s *student) GetScore() float64 {
	return s.score
}

```

```go
// main.go
package main

import (
	"fmt"
	"goproject/src/go_code/chapter10/factory/model"
)

func main() {
	// 创建一个Student实例
	// var stu = model.Student{
	// 	Name:  "tom",
	// 	Score: 78.9,
	// }

	// 如果student结构体是首字母小写，我们可以通过工厂模式来解决
	var stu = model.NewStudent("tom~", 88.8)

	fmt.Println(stu)                                            // &{tom~ 88.8}
	fmt.Println(*stu)                                           // {tom~ 88.8}
	fmt.Println("name=", (*stu).Name, "score=", stu.GetScore()) // {tom~ 88.8}
}

```



# 第十一章_面向对象编程(下)

## 面向对象编程思想-抽象

抽象的介绍

我们在前面去定义一个结构体的时候，实际上就是把一类事物的共有的属性（字段）和行为（方法）提取出来，形成一个物理模型（结构体），这种研究问题的方法称为抽象

```go
package main

import "fmt"

// 定义一个结构体Account
type Account struct {
	AccountNo string
	Pwd       string
	Balance   float64
}

// 方法
// 1、存款
func (account *Account) Deposite(money float64, pwd string) {
	// 校验输入的密码是否正确
	if pwd != account.Pwd {
		fmt.Println("您输入的密码不正确")
		return
	}

	// 校验存款金额是否正确
	if money < 0 {
		fmt.Println("您存入的金额不正确")
		return
	}
	account.Balance += money
	fmt.Println("存款成功～")
}

// 2、取款
func (account *Account) WithDraw(money float64, pwd string) {
	// 校验输入的密码是否正确
	if pwd != account.Pwd {
		fmt.Println("您输入的密码不正确")
		return
	}

	// 校验取款金额是否正确
	if money < 0 || money > account.Balance {
		fmt.Println("您存入的金额不正确")
		return
	}
	account.Balance -= money
	fmt.Println("存款成功～")
}

// 3、查询余额
func (account *Account) Query(pwd string) {
	// 校验输入的密码是否正确
	if pwd != account.Pwd {
		fmt.Println("您输入的密码不正确")
		return
	}
	fmt.Printf("你的账号为：%v\n你的银行账户当前余额为：%v\n", account.AccountNo, account.Balance)
}

func main() {
	// 测试一把
	account := &Account{
		AccountNo: "gs1111111",
		Pwd:       "666666",
		Balance:   100.0,
	}
	// 这里可以做的更加灵活，就是让用户通过控制台输入命令
	// 菜单...
	// 用户输入
	account.Query("666666")
	account.Deposite(200.0, "666666")
	account.Query("666666")
	account.WithDraw(50.0, "666666")
	account.Query("666666")

}

```



## 面向对象编程三大特性-封装

golang仍然有面向对象编程的继承、封装、多态的特性，只是实现的方式和其它OOP语言不一样，下面看golang的三大特性的实现

封装介绍：

封装（encapsulation）就是把抽象出的字段和对字段的操作封装在一起，数据被保护在内部，程序的其它包只有通过被授权的操作（方法），才能对字段进行操作

封装的理解和好处：

1、隐藏实现细节

2、它可以对数据进行验证，保证安全合理（Age）

如何体现封装：

1、对结构体中的属性进行封装

2、通过方法、包 实现封装

封装的实现步骤：

1、将结构体、字段（属性）的首字母小写（不能导出了，其它包不能使用，类似privata）

2、给结构体所在包提供一个工厂模式的函数，首字母大写。类似一个构造函数

3、提供一个首字母大写的Set方法（类似其它语言的public），用于与属性判断并赋值

```go
func (var 结构体类型名) SetXxx(参数列表)(返回值列表){
  // 加入“数据验证”的业务逻辑
  var.字段 = 参数
}
```

4、提供一个首字母大写的Get方法（类似其它语言的public），用于获取属性的值

```go
func (var 结构体类型名) GetXxx(){
  return var.字段
}
```

特别说明：在golang开发中并没有特别强调封装，这点并不像Java，所以提醒学过Java的朋友，不用总是用java的语法特性来看待golang，golang本身对面向对象的特性做了简化的

## 封装快速入门案例

写一个程序（person.go），不能随便查看人的年龄、工资等隐私，并对输入的年龄进行合理的验证

设计：model包（person.go）main包（main.go调用Person结构体）

```go
// model/person.go
package model

import "fmt"

type person struct {
	Name string
	age  int //不可导出，其它包不能直接访问
	sal  float64
}

// 写一个工厂模式的函数，相当于构造函数
func NewPerson(name string) *person {
	return &person{
		Name: name,
	}
}

// 为了访问 age 和 sal 我们编写一对SetXxx的方法和GetXxx的方法
func (p *person) SetAge(age int) {
	if age > 0 && age < 150 {
		p.age = age
	} else {
		fmt.Println("年龄范围不正确..")
		// 给程序员一个默认值
	}
}

func (p *person) GetAge() int {
	return p.age
}

func (p *person) SetSal(sal float64) {
	if sal >= 3000 && sal <= 30000 {
		p.sal = sal
	} else {
		fmt.Println("薪水范围不正确..")
		// 给程序员一个默认值
	}
}

func (p *person) GetSal() float64 {
	return p.sal
}

```

```go
// main/main.go
package main

import (
	"fmt"
	"goproject/src/go_code/chapter11/encapsulate/model"
)

func main() {
	p := model.NewPerson("smith")
	p.SetAge(18)
	p.SetSal(5000.00)
	fmt.Println(*p)
	fmt.Println(p.Name, "age=", p.GetAge(), "sal=", p.GetSal())
}

```



## 封装练习题

创建程序，在model包中定义Account结构体：在main函数中体会golang的封装性

1、Account结构体要求具有字段：账号（长度6-10之间）、余额（必须>20）、密码（必须是六位）

2、通过SetXxx的方法给Account的字段赋值，通过GetXxx的方法获取字段的值

3、在main（）函数中测试

```go
// model/account.go
package model

import "fmt"

type account struct {
	accountNo string
	pwd       string
	balance   float64
}

// 工厂模式的函数-构造函数
func NewAccount(accountNo string, pwd string, balance float64) *account {
	if len(accountNo) < 6 || len(accountNo) > 10 {
		fmt.Println("账号长度不对...")
		return nil
	}
	if len(pwd) != 6 {
		fmt.Println("密码的长度不对...")
		return nil
	}
	if balance < 20 {
		fmt.Println("余额数目不对...")
		return nil
	}
	return &account{
		accountNo: accountNo,
		pwd:       pwd,
		balance:   balance,
	}
}

// 方法
// 1、存款
func (account *account) Deposite(money float64, pwd string) {
	// 校验输入的密码是否正确
	if pwd != account.pwd {
		fmt.Println("您输入的密码不正确")
		return
	}

	// 校验存款金额是否正确
	if money < 0 {
		fmt.Println("您存入的金额不正确")
		return
	}
	account.balance += money
	fmt.Println("存款成功～")
}

// 2、取款
func (account *account) WithDraw(money float64, pwd string) {
	// 校验输入的密码是否正确
	if pwd != account.pwd {
		fmt.Println("您输入的密码不正确")
		return
	}

	// 校验取款金额是否正确
	if money < 0 || money > account.balance {
		fmt.Println("您存入的金额不正确")
		return
	}
	account.balance -= money
	fmt.Println("存款成功～")
}

// 3、查询余额
func (account *account) Query(pwd string) {
	// 校验输入的密码是否正确
	if pwd != account.pwd {
		fmt.Println("您输入的密码不正确")
		return
	}
	fmt.Printf("你的账号为：%v\n你的银行账户当前余额为：%v\n", account.accountNo, account.balance)
}

```

```go
// main/main.go
package main

import (
	"fmt"
	"goproject/src/go_code/chapter11/encapexerise/model"
)

func main() {
	account := model.NewAccount("jzh1", "999999", 40)
	if account != nil {
		fmt.Println("创建成功 = ", account)
	} else {
		fmt.Println("创建失败")
	}
}

```



## 面向对象编程三大特性-继承

 看个学生考试系统的程序，提出代码复用的问题

```go
package main

import "fmt"

// 编写一个学生考试系统
type Pupil struct {
	Name  string
	Age   int
	Score int
}

// 显示他的成绩
func (p *Pupil) showInfo() {
	fmt.Printf("学生名=%v 年龄=%v 成绩=%v\n", p.Name, p.Age, p.Score)
}

func (p *Pupil) SetScore(score int) {
	// 业务判断
	p.Score = score
}

func (p *Pupil) tesing() {
	fmt.Println("小学生正在考试中.....")
}

// 大学生，研究生考试，怎么处理？
type Graduate struct {
	Name  string
	Age   int
	Score int
}

// 显示他的成绩
func (p *Graduate) showInfo() {
	fmt.Printf("学生名=%v 年龄=%v 成绩=%v\n", p.Name, p.Age, p.Score)
}

func (p *Graduate) SetScore(score int) {
	// 业务判断
	p.Score = score
}

func (p *Graduate) tesing() {
	fmt.Println("大学生正在考试中.....")
}
func main() {
	// 测试
	var puil = &Pupil{
		Name: "tom",
		Age:  10,
	}
	puil.tesing()
	puil.SetScore(90)
	puil.showInfo()

	// 测试大学生
	var graduate = &Graduate{
		Name: "tom",
		Age:  10,
	}
	graduate.tesing()
	graduate.SetScore(90)
	graduate.showInfo()

}

```

对上面代码的小结：

1、Pupil 和 Graduate 两个结构体的字段和方法几乎一样，但是我们却写了相同的代码

2、出现代码冗余，而且代码不利于维护，同时也不利于功能的扩展

3、解决方法：通过继承的方式来解决



## 继承基本语法

继承可以解决代码复用，让我们的编程更加靠近人类思维

当多个结构体存在相同属性（字段）和方法时，可以从这些结构体中抽象出结构体（比如刚才Student），在该结构体中定义这些相同的属性和方法

其它的结构体不需要重新定义这些属性和方法，只需要嵌套一个Student匿名结构体即可

也就是说：在golang中，如果一个struct嵌套了另一个匿名结构体，那么这个结构体可以直接访问匿名结构体的字段和方法，从而实现了继承特性

嵌套匿名结构体的基本语法：

```go
type Goods struct{
	Name string
  Price int
}

type Book struct{
  Goods 						// 这里就是嵌套匿名结构体Goods
  Write string
}
```



## 继承快速入门案例

我们对学生考试系统改进，使用嵌套匿名结构体的方式来实现继承特性

```go
package main

import "fmt"

// 编写一个学生考试系统
type Student struct {
	Name  string
	Age   int
	Score int
}

// 将 Pupil 和 Graduate 共有的方法也绑定到 *Student
func (stu *Student) ShowInfo() {
	fmt.Printf("学生名：%v 年龄：%v 成绩：%v\n", stu.Name, stu.Age, stu.Score)
}

func (stu *Student) SetScore(score int) {
	// 业务判断
	stu.Score = score
}

// 给 *Student 增加一个方法，那么Pupil和Graduate都可以使用该方法
func (stu *Student) GetSum(n1 int, n2 int) int {
	return n1 + n2

}

// 小学生
type Pupil struct {
	Student // 嵌入了Student匿名结构体
}

// 显示他的成绩

// 这是Pupil结构体特有的方法，保留
func (p *Pupil) tesing() {
	fmt.Println("小学生正在考试中.....")
}

// 大学生，研究生考试，怎么处理？
type Graduate struct {
	Student // 嵌入了Student匿名结构体
}

// 显示他的成绩
// 这是Graduate结构体特有的方法，保留
func (p *Graduate) tesing() {
	fmt.Println("大学生正在考试中.....")
}
func main() {
	// 当我们对结构体嵌入了匿名结构体后，使用方法会发生变化
	pupil := &Pupil{}
	pupil.Student.Name = "tom"
	pupil.Student.Age = 8
	pupil.tesing()
	pupil.Student.SetScore(70)
	pupil.Student.ShowInfo()
	fmt.Println("res=", pupil.Student.GetSum(1, 2))

	// 大学生
	graduate := &Graduate{}
	graduate.Student.Name = "mary"
	graduate.Student.Age = 28
	graduate.tesing()
	graduate.Student.SetScore(90)
	graduate.Student.ShowInfo()
	fmt.Println("res=", graduate.Student.GetSum(2, 3))

}

```



## 继承的深入讨论

1、结构体可以使用嵌套匿名结构体所有的字段和方法，即：首字母大写或者小写的字段、方法，都可以使用

2、匿名结构体字段访问可以简化

3、当结构体和匿名结构体有相同的字段或者方法时，编译器采用就近访问原则访问，如希望访问匿名结构体的字段和方法，可以通过匿名结构体名来区分

```go
package main

import "fmt"

type A struct {
	Name string
	Age  int
}

func (a *A) SayOk() {
	fmt.Println("A Sayok", a.Name)
}

func (a *A) hello() {
	fmt.Println("A hello", a.Name)
}

type B struct {
	A
	Name string
}

func (b *B) SayOk() {
	fmt.Println("B SayOk", b.Name)
}

func main() {
	var b B
	// b.A.Name = "tom"
	// b.A.Age = 123
	// b.A.SayOk()
	// b.A.hello()

	// // (2)上面的写法可以简化
	// b.Name = "smith"
	// b.Age = 20
	// b.SayOk()
	// b.hello()

	b.Name = "jack"    // ok
	b.A.Name = "scott" // ?赋值
	b.Age = 100        // ok
	b.SayOk()          // B SayOk jack
	b.A.SayOk()        // A SayOK scott
	b.hello()          // A hello ? "jack" ? ""   ==>"scott"
}

```

对上面的代码小结：

​	（1）、当我们直接通过 b 访问字段或方法时，其执行流程如下比如 b.Name

​	（2）、编译器会先看 b 对应的类型有没有 Name，如果有，则直接调用 B 类型的 Name 字段

​	（3）、如果没有就去看 B 中嵌入的匿名结构体 A 有没有声明 Name 字段，如果有就调用，如果没有继续查找，如果没有，就报错



4、结构体嵌入两个（或多个）匿名结构体，如两个匿名结构体有相同的字段和方法（同时结构体本身没有同名的字段和方法），在访问时，就必须明确指定匿名结构体名字，否则编译报错【开发过程中都指定就好了】

```go
package main

import "fmt"

type A struct {
	Name string
	Age  int
}
type B struct {
	Name  string
	Score float64
}
type C struct {
	A
	B
	// Name string
}

func main() {
	var c C
	// 如果c 没有Name字段，而 A 和 B 有Name，这时就必须通过指定匿名结构体名字来区分
	// 所以 c.Name 就会报编译错误，这个规则对方法也是一样的！
	c.A.Name = "tom" //error
	fmt.Println("c")
}

```



5、如果一个struct嵌套了一个有名结构体，这种模式就是组合，如果是组合关系，那么在访问组合的结构体的字段或方法时，必须带上结构体的名字

```go
//有名结构体
type D struct {
	a A
}

func main() {
	var c C
	// 如果c 没有Name字段，而 A 和 B 有Name，这时就必须通过指定匿名结构体名字来区分
	// 所以 c.Name 就会报编译错误，这个规则对方法也是一样的！
	c.A.Name = "tom" //error
	fmt.Println("c")

	// 如果 D 中是一个有名结构体，则访问有名结构体的字段时，就必须带上有名结构体的名字
	// 比如：d.a.Name
	var d D
	d.a.Name = "jack"
}

```



6、嵌套匿名结构体后，也可以在创建结构体变量（实例）时，直接指定各个匿名结构体字段的值

```go
package main

import "fmt"

type A struct {
	Name string
	Age  int
}
type B struct {
	Name  string
	Score float64
}
type C struct {
	A
	B
	// Name string
}

//有名结构体
type D struct {
	a A
}

type Goods struct {
	Name  string
	Price float64
}

type Brand struct {
	Name    string
	Address string
}

type TV struct {
	*Goods // Goods
	*Brand // Brand
}

func main() {
	var c C
	// 如果c 没有Name字段，而 A 和 B 有Name，这时就必须通过指定匿名结构体名字来区分
	// 所以 c.Name 就会报编译错误，这个规则对方法也是一样的！
	c.A.Name = "tom" //error
	fmt.Println("c")

	// 如果 D 中是一个有名结构体，则访问有名结构体的字段时，就必须带上有名结构体的名字
	// 比如：d.a.Name
	var d D
	d.a.Name = "jack"

	// 嵌套匿名结构体后，也可以在创建结构体变量（实例）时，直接指定各个匿名结构体字段的值
	tv := TV{&Goods{"电视机001", 5000.1}, &Brand{"海尔", "山东"}}
	tv2 := TV{
		&Goods{
			Name:  "电视机001",
			Price: 5000.1,
		},
		&Brand{
			Name:    "海尔",
			Address: "山东",
		},
	}
	fmt.Println(*tv.Goods, *tv.Brand)
	fmt.Println(*tv2.Goods, *tv2.Brand)
}

```



7、结构体的匿名字段是基本数据类型，如何访问

```go
type Monster struct {
	Name string
	Age  int
}

type E struct {
	Monster
	int		// 匿名字段是基本数据类型
  n int // 给int字段指定名字
}

func main() {
	// 演示一下匿名字段是基本数据类型的使用
	var e E
	e.Monster.Name = "狐狸精"
	e.Monster.Age = 300
	e.int = 20
  e.n = 40
	fmt.Println("e = ", e)
}
```

说明：

1、如果一个结构体中有 int 类型的匿名字段，就不能有第二个

2、如果需要有多个int的字段，则必须给 int 字段指定名字



## 多重继承介绍

如果一个 struct 嵌套了多个匿名结构体，那么该结构体可以直接访问嵌套的匿名结构体的字段和方法，从而实现了多重继承

1、如嵌入的匿名结构体有相同的字段名或者方法名，则在访问时，需要通过匿名结构体类型名来区分

2、为了保证代码的简洁性，建议尽量不使用多重继承

```go
type Goods struct {
	Name  string
	Price float64
}

type Brand struct {
	Name    string
	Address string
}

type TV struct {
	*Goods // Goods
	*Brand // Brand
}

func main() {
  // 访问Goods的Name
	fmt.Println(tv.Goods.Name)
	fmt.Println(tv.Price)
}
```













