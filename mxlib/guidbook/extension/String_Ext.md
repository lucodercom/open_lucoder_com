# 字符串扩展类

字符串扩展类扩展了字符串的操作，比如切割、替换等方法。

# 头文件

```cpp
class String_Ext
{
  public:
	vector<string> split(string src, string splitor);
	//替换方法，将srcString中的replaceSrc替换为replaceDst
	void replace(string &srcString, const string &replaceSrc, const string &replaceDst);
};
```

# 使用

扩展字符串主要扩展了几个字符串操作的相关方法。

## split

切分方法，封装了字符串`split`方法支持将一个字符串使用字符分割切割。

```cpp
String_Ext ext;

vector<string> result = ext.split("2018/10/01","/");
result = ext.split("20:15:13",":");

for(int i = 0; i < result.size(); i++)
    cout<<result[i]<<endl;

cout<<"------------------------------"<<endl;

for(int i = 0; i < result.size(); i++)
    cout<<result[i]<<endl;

```

输出：
```shell
2018
10
01
------------------------------
20
15
13
```

方法一共有两个参数，第一个参数是源字符串，第二个是切割符号，返回切割结果是一个`vector<string>`类型。

## replace

替换方法，封装了字符串`split`方法支持将一个字符串使用字符分割切割。

```cpp
String_Ext ext;
String_Ext ext;
string src = "Hello ,this is a simple test";
ext.replace(src, "simple","split");
cout<<src<<endl;
```
输出：
```
Hello , this is a split test
```

方法一共有两个参数，第一个参数是源字符串，第二个是切割符号，返回切割结果是一个`vector<string>`类型。