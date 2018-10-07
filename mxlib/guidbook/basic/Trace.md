# MXLIB 日志组建

日志记录是一个非常常用的一个功能，是项目开发必备的一个模块，日志组建可以给帮助开发者优化系统和BUG的重构。

# 使用

MXLIB的日志组建是一个封装的`Trace`类，内部封装各种日志记录相关的方法。

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

using namespace std;
namespace mxcoder
{

//Trace construct
class Trace
{
  public:
	//constructor of trace
	Trace();
	Trace(bool debug, bool log, string folder);
	Trace(bool debug, bool log, string folder, int size);
	void setLogFolder(string logfolder);
	//set capacity of log factory
	void setLogFactoryCount(int size);
	//bind and initial create of Trace
	void bind(bool debug, bool log, string folder);
	//write info into log factory
	void writeLine(const char *info, ...);
	//write exception into log factory
	void writeException(const char *info, ...);
	void writeException(exception ex);
	//write logfactory info into file
	void writeToFileAsync();
	string getLogFile();

  private:
	bool isdebug;
	bool islog;
	string logFolder;
	int logFactoryCount;
	vector<string> logFactory;
};

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

上面的头文件是`Trace`必须的，其中日期部分在`Trace`中有过引用，所以也需要使用`Date`的头文件。


# 开放方法

本小节开始就着重介绍`Trace`的封装。

## 创建

创建`Trace`拥有两种封装，你可以使用下面任意一种对`Trace`初始化。
```cpp
Trace trace;
trace.bind(debug,log,log_folder);

Trace trace2(debug,log,log_folder);

Trace trace3(debug,log,log_folder,factory_size)
```

|属性|类型|默认|说明|
|---|---|---|---|
|debug|bool|true|用于指定是否是debug模式，true表示debug模式，将会打印所有的输出信息。否则是release模式，除了错误信息几乎不打印任何数据。|
|islog|bool|false|用于指定是否输出日志，true表示输出日志，将会把日志写入到日志中。否则将不会输出到文件中，注意的是在程序结束之后务必调用一次writeToFileAsync()，将日志工厂的日志数据生产到日志文件中。|
|log_folder|string|"./"|log_folder是用来存放日志的文件夹。默认是当前文件夹|
|factory_size|int | 100|日志工厂容量，表示积累多少条日志之后写入文件|

## 方法

本小结介绍内部封装的方法

### writeLine

`writeLine`方法是一个写入信息的方法，方法调用之前必须调用`创建小节`中的内容，必须在`bind`初始化之后，或者在`Trace`构造函数绑定。

```cpp
trace.writeLine("hello world！");
trace.writeLine("I am %s , and %d year old！","张三",15);
trace.writeLine("PI is %lf buf exp is ",3.14159,2.71828);
```

### writeException

`writeException`方法是一个写入异常信息的方法，方法调用之前必须调用`创建小节`中的内容，必须在`bind`初始化之后，或者在`Trace`构造函数绑定。

```cpp
trace.writeException(ex);
trace.writeLine("error happend when you write content to file");
trace.writeLine("error happend and error code is %d",error_code);
```

### writeToFileAsync

`writeToFileAsync`方法是一个输出到文件的方法，方法调用之前必须调用`创建小节`中的内容，必须在`bind`初始化之后，或者在`Trace`构造函数绑定。

```cpp
trace.writeToFileAsync();
```
`writeToFileAsync`方法是终态方法，如果你设置写入到文件，那么在程序执行之后必须执行该方法，才能将日志工厂中的所有的数据写入到文件中-->关闭工厂-->结束日志引擎。

### 其他方法

内部包含其他方法，都是非常用的一些方法。

#### Trace()

默认构造函数，使用这种构造函数必须自己设置绑定。

```cpp
bind(debug,log,log_folder);
```
另外还有两种构造函数。

```cpp
Trace(bool debug, bool log, string folder);
Trace(bool debug, bool log, string folder, int size);
```

#### setLogFolder(string logfolder)

设置日志目录。
	
#### setLogFactoryCount(int size)

设置日志工厂容量方法。

#### bind(bool debug, bool log, string folder)

默认绑定方法，一般用于默认的构造函数之后。

#### string getLogFile()

获取当前日志文件名称（包括路径）。

# 结束语

MXLIB的日志引擎到此告一段落，该日志引擎基本可以满足我们的日常开发需求，并且使用起来非常简单方便。但是要注意，MXLIB日志引擎中，`writeLine`的最大允许长度不超过1000字符，如果有特殊需要可以从`Github`下载代码重新编译。