# Path 类

`Path类`是一个模仿`C#`开发的一个类，内部封装了与路径相关的方法。

# 使用

MXLIB的IO组建是一个封装的`PATH`类，内部封装各种和路径相关的方法，`Path`类属于`IO`中的一个类。

# 头文件

```cpp
//io construct
class IO
{
  public:
	class Path
	{
	  public:
		//获取文件的目录名称
		string getDirectory(string file);
		//获取文件的扩展名称
		string getFileExtension(string file);
		//获取文件的名称不包含扩展名
		string getFilenameWithoutExtension(string file);
		//获取文件的名称
		string getFilename(string file);
	};
};
```

# 使用

```cpp
IO::Directory dir;

string file = "/home/cast/a.txt";
cout<<dir.getDirectory(file)<<endl;
cout<<dir.getFileExtension(file)<<endl;
cout<<dir.getFilenameWithoutExtension(file)<<endl;
cout<<dir.getFilename(file)<<endl;
```

输出：

```shell
/home/cast
.txt
a
a.txt
```

上面是两个最简单的使用，一个是获取文件夹所有文件方法，一个是创建目录的方法。

### getDirectory

`getDirectory`是一个获取文件夹名称的方法，该方法可以得到文件夹名称。

```cpp
IO::Directory dir;
dir.getDirectory(file);
```

### getFileExtension

`getFileExtension`将获取到文件的扩展名（注意前面有.）。

```
IO::Directory dir;
dir.getFileExtension(file);
```

### getFilenameWithoutExtension

`getFileExtension`将获取到文件的名称，没有扩展名。

```
IO::Directory dir;
dir.getFilenameWithoutExtension(file);
```

### getFilename

`getFilename`将获取到文件的名称带有扩展名。

```
IO::Directory dir;
dir.getFilename(file);
```

# 结束语

虽然现在的`Path类`还是非常鸡肋，但是需要不断的注入新能量。