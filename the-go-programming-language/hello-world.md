# Hello, World

```go
package main

import "fmt"

func main() {
    fmt.Println("Hello, 世界")
}
```

Go 是一门编译型语言，Go 语言的工具链将源代码及其依赖转换成计算机的机器指令（静态编译）。Go 语言提供的工具都通过一个单独的命令 `go` 调用， `go` 命令有一系列子命令。最简单的一个子命令就是 `run`。这个命令编译一个或多个以 `.go` 结尾的源文件，链接库文件，并运行最终生成的可执行文件。

{% hint style="info" %}
实际执行 `go run`，发现并不会生成实际的对应可执行文件。猜测是生成在 RAM 中，并运行。
{% endhint %}



Go 语言原生支持 Unicode，所以它可以处理全世界任何语言的文本。

编译出实际的可执行文件：

```go
go build helloworld.go
```

这个命令生成一个名为 `helloworld` 的可执行的二进制文件。Windows系统下生成的可执行文件是 `helloworld.exe`，增加了`.exe`后缀名），之后你可以随时运行它。在 Windows 系统下在命令行直接输入 `helloworld.exe` 命令运行，不需任何处理。双击可执行文件是无效的。因为静态编译，所以不用担心在系统库更新的时候冲突，幸福感满满。

## 程序本身

Go 语言的代码通过 包（Package）组织，包类似于其他语言的库（libraries）或者模块（modules）。  
一个包由位于单个目录下的一个或多个 `.go` 源代码文件组成，目录定义包的作用。  
每个源文件都以一条 package 声明语句开始，`package main`，表示该文件树于哪个包（这里就是 main 包）。紧跟着一系列 import（导入）的包，之后是存储在这个文件里的程序语句。

* **`import` 声明必须跟在文件的 package 声明之后。** 随后才是组成程序的函数，变量，常量，类型的声明语句（分别由关键字 func、var、const、type 定义）。



