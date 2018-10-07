# MXLib日期组建

日期组建是用来封装C++中的日期操作，C++中原生日期操作操作相对复杂，封装日期类方便开发者调用。

# 使用

MXLIB的日期组建是一个封装的`Date`类，内部封装对时间操作的一些方法。

## 头文件

C++的一个非常好的特性就是你可以自定义头文件，只选择自己需要的部分作为头文件，或者说是只将自己需要的部分添加头文件即可，但是头文件的文件名称必须是`mxlib.h`。

```cpp
#include <iostream>
#include <fstream>
#include <vector>
#include <cstdarg>
#include <time.h>
#include <stdlib.h>
#include <stdio.h>
#include <string.h>

//Date time construct
class Date
{
  public:
	//if the year input is leap year. if you set nothing input ,it will return the result of current year.
	bool LeapYear(int year = 0);
	//get date of current date, and you can input a char to split it
	static string getDate(char splitor = '#');
	//get time of current time, and you can input a char to split it
	static string getTime(char splitor = '#');

  private:
	int getYear();
};
```

## 链接使用

我们提供了三种平台编译完成的库组件<a href='https://open.lucoder.com/mxlib'>https://open.lucoder.com/mxlib</a>，可以直接下载使用。由于作者是用于ARM平台（Ubuntu Linux），所以这里就介绍Linux下面的使用方法。
```
g++ ./test.cpp -o ./test.exe -I include -Llib -lmxlib
```
其中`include`是头文件存放的目录，`lib`是存放库文件的目录（`mxlib`），完成之后你将会看到一个文件`test.exe`。
```
./test.exe
```

# 使用

`mxlib`使用任何封装都必须包含头文件的引用：`#include "mxlib.h"`，只要使用`mxlib`需要引用命名空间`mxcoder`,当然允许你是用`mxcoder::`。

```cpp
#include "mxlib.h"

using namespace mxcoder;

int main(){

    cout<<Date::getDate("")<<endl;
    cout<<Date::getTime("")<<endl;
    cout<<Date::getDate("/")<<endl;
    cout<<Date::getTime("/")<<endl;

    return 0;
}
```

输出结果：

```shell
20181001
1730
2018/10/01
17:30:10
```
# 开放方法

本小结介绍`Date`的封装。

## getDate

获取当前日期，带有构造函数的封装，构造参数可以是非`#`的任意符号用于分割。

## getTime

获取当前时间，带有构造函数的封装，构造参数可以是非`#`的任意符号用于分割。

## LeapYear

用于查看是否是闰年，如果输入的是一个整数，算法将会判断该整数是否是闰年，否则将会返回本年是否是闰年。

# 结束语

MXLIB的日期引擎到此告一段落，该日期引擎基本可以满足我们的日常开发需求，并且使用起来非常简单方便。