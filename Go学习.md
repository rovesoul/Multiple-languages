[toc]

## Go命令行工具：

```shell
build     编译打包依赖
clean     清理链接和缓存文件
doc       展示包的文档
env       打印Go环境变量信息
bug       启动Go语言调试
fix       更新文档语法
fmt       格式化文档结构
generate  通过扫描Go源码中的特殊注释来识别要运行的常规命令
get       下载安装包和依赖项
install   编译安装包和依赖项
list      查询包
run       编译运行Go程序
test      测试包
tool      运行Go的其他工具
version   打印版本号
vet       静态错误检查工具
```



## string包用法

这道题：

```go
s = []string{"bitcoin", "take", "over", "the", "world", "maybe", "who", "knows", "perhaps"}
    Expect(TwoSort(s)).To(Equal("b***i***t***c***o***i***n"))
```

解法

```go
package kata
import (
  "sort"
  "strings"
)

func TwoSort(arr []string) string {
  sort.Strings(arr)
  return strings.Join(strings.Split(arr[0],""), "***")
}
```



## 判断类型

如果我们需要判断变量的类型，可以使用Go语言标准库中的reflect

```go
fmt.Println(reflect.TypeOf(a))

fmt.Println("变量b值为:",b,",变量类型为:",reflect.TypeOf(b)) 
fmt.Println("转换变量b类型为string:",string(b))
```

## 变量声明

一般情况下，我们将指针变量的类型声明为*int。 使用操作符“&”取变量地址

```go
func main() {
num :=1
var p *int
p = &num 
fmt.Println("num变量的地址为:",p) 
fmt.Println("指针变量p的地址为:",&p)
}
```

Go语言中有丰富的数据类型，基本的数据类型，如整型、浮点型、字符串、字 符和布尔型。除了以上类型，Go语言还有切片、通道、map(映射)和函数等类型。

## Buffer 和 runtime

```go
// 缓存拼接 Buffer
func main(){
a := "012345"
b := "6789"
var c bytes.Buffer
c.WriteString(a)
c.WriteString(b)
fmt.Println(c.String())
fmt.Println(reflect.TypeOf(c))
import (
     "runtime"
     "fmt" )

    
// 以下程序引入了`runtime`包，使用`NumCPU()`函数获取了程序使用的CPU核数并传递给num变量。
func main() {
         if num := runtime.NumCPU();num >=1 {
          fmt.Println("程序使用的CPU核数为:",num) 11 
             }
        }
```



## if语句

题目：Examples
1705 --> 18
1900 --> 19
1601 --> 17
2000 --> 20

```go
// 我的：
package kata
func century(year int) int {
 // Finish this :)
  yushu := year % 100;
  shang := year / 100;
  if yushu != 0{
    shang ++ 
  }
 return shang
}

//不错答案1
func century(year int) int {
 // Finish this :)
 if year % 100 != 0  { year += 100 }
 return year / 100
}

//不错答案2
package kata
func century(year int) int {
  if year%100 == 0{
    return year / 100
  }
  return year/100 + 1
}

// 不错答案3
package kata
func century(year int) int {
  return (year + 99)/100 
}
```

题目：把正负数 ，都返回负数形式，0则返回0

```go 
package kata
func MakeNegative(x int) int {
  if x > 0 {
    return -x
  }
  return x
}
```

## for循环

```go
package main

import "fmt"
func main() {
     for i := 1;i <=5;i++ {
            fmt.Println(i)
         }
     }
```

```go
//加倍问题，我的答案
package kata
import(
"fmt"
)

func Maps(x []int) []int {
    var getlist [] int
      for i := range x{
        fmt.Println(i)
      getlist = append(getlist,x[i]*2)
    }
    return getlist
}

//加倍问题，第一名答案 ，位置、数额可以同时获取，我给忘了。。
package kata

func Maps(x []int) []int {
  result := make([]int, len(x))
  for i, v := range x {
    result[i] = v + v
  }
  return result
}
```



## Case语法练习

```go
// 注意的是：switch语句后边的‘;’，没有就报错
func GetGrade(a,b,c int) rune {
    switch mean := (a+b+c)/3; {
    case mean < 60: 
    	return 'F'
    case mean < 70: 
    	return 'D'
    case mean < 80: 
    	return 'C'
    case mean < 90: 
    	return 'B'
    default: 
    	return 'A'
    }
    
}
```

另一种写法

```go
package kata

func GetGrade(a,b,c int) rune {
  
  mean := ((a + b + c) / 3)

  switch{
    case mean>=90&&mean<=100:
      return rune(65)
    case mean>=80&&mean<90:
      return rune(66)
    case mean>=70 && mean<80:
      return rune(67)
    case mean>=60 && mean<70:
      return rune(68)
    //no need to check for values greater than 100
    default:
      return rune(70)
  }
}
//------------------------------------------------------------------------------------
package kata

func GetGrade(a, b, c int) rune {
    switch ((a + b + c) / 30) {
        case 10: return 'A'
        case 9: return 'A'
        case 8: return 'B'
        case 7: return 'C'
        case 6: return 'D'
        default: return 'F'
    }
}
```



## 列表

```go
package main

import "fmt"

func main() {
		 	var num = [...]int{1, 2, 3, 4}
 			for k, v := range num {
 			 	fmt.Println("变量k：", k," ","变量v：", v)
 			 }
 		}

// another
func main() {
    var student = [...]string{"Tom","Ben","Peter"}
    for k,v := range student{
        fmt.Println("数组下标：",k,"，对应元素",v)
        }
}
```

## 切片

◇ **地址**：切片的地址一般指切片中第一个元素所指向的内存地址，用十六进制表示。

◇ **长度**：切片中实际存在元素的个数。

◇ **容量**：从切片的起始元素开始到其底层数组中的最后一个元素的个数

```go
//切片的声明格式如下：
var 切片变量名 []元素类型
package main

import "fmt"

func main() {
    var student []int                               //第一种，空的
    var student =[]string{"Tom","Ben","Peter"}      //第二种，赋值了
    fmt.Println("student切片：",student)
    fmt.Println("student切片长度：",len(student))
    fmt.Println("student切片容量：",cap(student))
    fmt.Println("判定student切片是否为空：",student==nil)
    }

//student切片：[]
//student切片长度：0
//student切片容量：0
//判定student切片是否为空：true

//student切片：[Tom Ben Peter]
//student切片长度：3
//student切片容量：3
//判定student切片是否为空：false


```

给切片增加元素：

```go
student := make([]int,1,1)
student = append(student,i)
```

## map

类似python的dict

```go
// var map [键类型]值类型
country := map[string]string{
 "中国":"China",
 "美国":"America",
 "日本":"Japan",
}
func main() {
        var studentScoreMap map[string]int
        fmt.Println(studentScoreMap)
    }

//==================================================================
//map[]

func main() {
    var studentScoreMap = map[string]int{
            "Tom":80,
            "Ben":85,
            "Peter":90,
        }
    fmt.Println(studentScoreMap)
    }
//map[Tom:80 Ben:85 Peter:90]
//==================================================================
// 声明一个map，然后要make一下，
package main

import "fmt"

func main() {
	var studentScoreMap map[string]int
	studentScoreMap = make(map[string]int)   //这行是必要的
	studentScoreMap["Tom"]=80
	studentScoreMap["Ben"]=85
	studentScoreMap["Bob"]=90
    //for循环，打印key 和 value
	for k,v := range studentScoreMap{
		fmt.Println(k,v)
	}
	// 只打印key 或 value
	for k := range studentScoreMap{
		fmt.Println(k)  //key
		fmt.Println(studentScoreMap[k])   //value
	   }

	//删除
	delete(studentScoreMap,"Tom")
	fmt.Println(studentScoreMap)
}


```

## Go内置函数

![image-20220126100254716](C:\Users\39770\AppData\Roaming\Typora\typora-user-images\image-20220126100254716.png)

## 工作区结构

它应包含三个子目录：src目录、pkg目录和bin目录

- **src目录**：用于以代码包的形式组织并保存Go源码文件（如.go、.c、.h、.s等），同时也是

Go编译时查找代码的地方。

- **pkg目录**：用于存放经由go get/install命令构建安装后的代码包的“.a”归档文件，也是编译

生成的lib文件存储的地方。

- **bin目录**：与pkg目录类似，在通过go get/install命令完成安装后，保存由Go命令源码文件生

成的可执行文件。

```
GO工作区:
 ├─--bin
 │        ...
 ├─--pkg
 │   └─--windows_amd64
 │       ├─--github.com
 │       ...
 └─--src
     ├─----github.com
     ...
```

## 结构体

```go
// type 结构体名 struct {
//  成员变量1 类型1
//  成员变量2 类型2
//  成员变量3 类型3
//  ...
// }
type Book struct {
 title string
 author string
 num int
 id int
}

//对于同变量类型的结构体成员，可以将它们写在同一行
type Book struct {
 title,author string
 num,id int
}
```

## 文件操作

文件有三种权限，分别为读取、写入和执行，对应字母为r、w、x。

```go
//读
func OpenFile(name string, flag int, perm FileMode) (file *File, err error)
//写
func (f *File) Write(b []byte) (n int, err error)
```

## 并发

```go
go 函数名（函数参数）
```

## 打包

```go
go build

//upx压缩
终端文件夹中：upx -9 main.exe
```

UPX程序下载网址：https://github.com/upx/upx/releases。  
