# 下载

你可以选择下载源码自己编译，也可以使用发行版本。

## 发行版

我们提供了三种平台编译完成的库组件<a href='https://open.lucoder.com/mxlib'>https://open.lucoder.com/mxlib</a>，可以直接下载使用。

## 下载源码

```
git clone https://github.com/lucodercom/mxlib.git
cd mxlib
make
```

# 链接使用

由于作者是用于ARM平台（Ubuntu Linux），所以这里就介绍Linux下面的使用方法。
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

    Trace trace;

    return 0;
}
```