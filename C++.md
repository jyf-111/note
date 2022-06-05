1. 二进制输入输出文件记得记得ios::binary

2. 函数指针 向pthread_thread传递函数指针

3. 快速初始化

4. lambda捕获ostream 

5. vector别开太大

关键是，你还没有定义成员，而你这个vector声明是属于类的对象的，你这样等于在没有成员的情况下给这个容器分配了起源，你可以在构造函数里这样初始化它：base():a(10){...}, 使用了初始化列表。如果你想让这个容器属于类，你可以在类里把它声明为静态的，但是定义一定要在类外：vector<int> base::a(10); 当然，也对，vector是动态数组，所以你不用担心关于制定大小这些问题。
```C++
__FILE__  
__LINE__  
__DATE__  
__TIME__  
__FUNC__
__FUNCTION__
```
mysql cmake c 需要 
* libcrypto-1_1-x64.dll
* libmysql.dll 
* libmysql.lib 
* libssl-1_1-x64.dll