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
	//director construct
	class Directory
	{
	  public:
        //get files from directory
		int getFiles(vector<string> &files, string cate_dir, string ext, bool topOnly = true);
		//创建文件夹，如果mkdir_flag = false可以用于判断文件夹是否存在
		bool make_dir(string dir, bool mkdir_flag = true);

	  private:
	};
};
```

# 使用

```cpp
IO::Directory dir;
dir.getFiles(files,dir,".log",false);
dir.mkdir(folder,true);
```

上面是两个最简单的使用，一个是获取文件夹所有文件方法，一个是创建目录的方法。

### getFiles

`getFiles`是一个获取文件夹中所有文件的方法，一共有三个参数，其中第一个参数是读取到的结果存放的目录，是一个`vector<string>`类型，第二个参数是一个`string`类型用来指定遍历的目录，第三个是扩展名标定遍历扩展名的文件。第四个参数是`bool`类型的用于标示是否只搜索顶层（true）或者级联子目录（false)，默认是true（只用来顶层目录）。

```cpp
IO::Directory dir;
dir.getFiles(files,dir,".log",false);
```

### mkdir

`mkdir`是一个创建目录的封装，方法一共有两个参数，第一个是参数目录用于指定创建的文件夹。第二个参数用于指定如文件夹不存在是否创建它，默认是false。

如果第二个参数是false，还能用于检查目录是否存在。

```cpp
IO::Directory dir;
if(!dir.mkdir(dir_folder,false))
    cout<<"folder not exist!"<<endl;

if(!dir.mkdir(dir_folder,true))
    cout<<"mkdir fault!"<<endl;
else
    cout<<"mkdir success!"<<endl;
```

# 结束语

目前这两个方法是我常用的方法，我对她进行了封装，以后根据需求继续丰富功能。