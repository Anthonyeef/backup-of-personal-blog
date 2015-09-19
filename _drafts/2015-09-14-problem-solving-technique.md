---
layout: post
title: "Programming and Problem solving with C++"
<!--date: 2015-09-14 16:38:46 +0800-->
comments: true
categories: 
- Life
- 2015
- Develope
- Taiwan

---

这是我在台湾阅读的第一本书。下面是一些简单的笔记和摘抄：

> Never reinvent the wheel. If a solution exists, use it. If you've solved the same or a similar problem before, just repoeat your solution.

---

> Beware when declaring two or more pointers on the same line. The * operator binds with the variable name, not the type name.

{% highlight C++ linenos%}
int* x,y,z;  //same as: int* x, int y; int z;
{% endhighlight %}

---

> This decision is consistent with C++'s general philosophy of not introducing any feature that would slow the execution of a program.

---

> int A[15][30] declares A to be an array of 30 objects, each of which is an array of 15 intergers.（二维数组）

> The name of an array is equivalent to a pointer to the array's initial element and vice versa.

> Given two arays c and d, the comparison(c == d) does not test whether the contents of the two arrays are equal. Rather it compares the address of their initial elements.

> Unlike some programming languages such as Java, C++ does not provide automatic garbage collection.（ C++ 不提供垃圾回收机制）  

---

> new 命令使用之后需要 delete 命令进行内存的回收：
{% highlight C++ linenos%}
char* buffer = new char[500];
buffer[3] = 'a';
delete [] buffer;
{% endhighlight %} 

> Static casting is used when a conversion is made between two related types, for example numbers to numbers or pointers to pointers.
{% highlight C++ linenos%}
static_cast<desired_type>
{% endhighlight %}

> Since the rules are complex, it is a good idea to add parentheses to complex expressions to make your intent clear to someone reading your program.

这里我想到的是谭浩强那本书里，讲到优先级的时候在课后练习里无所不用其极的古怪运算符组合。当时我只是把那当纯粹的练习题目而已，然而现在回想起来，那不就是典型的「烂代码」吗？可读性极差，实际工作中绝对很少见到。

> Exact type agreement is not always necessary, however, for the compiler may perform implicit type conversions in some cases, such as casting a short actual argument to match an int formal argument.

编译器有时会执行隐性的类型转换，在actual argument 中的 short 类型会转换橙 formal argument 中的 int 类型。

> By default, arguments in C++ programs are passed by value. 声明是用值传递的。
{% highlight C++ linenos%}
void f(int value, int& ref) { 
	value++;  //no effect on the actual argument
	ref++     //modify the actual argument
	cout << value << endl;     
	cout << ref   << endl;
}
{% endhighlight %}

> Most C++ style manuals recommend that public members be presented first, since these are the elements of the class that are relevant to a programmer who wishes to use the class.

> Class member functions can be placed in two major categories: accessor functions, which only read class data; and update functions, which may alter class data. The keyword "const" indicates that the member function ifFrequentFlyer is an accessor.
{% highlight C++ linenos %}
bool isFrequentFlyer() const;
{% endhighlight %} 

const 字样同时也提醒编译器，如果有出现尝试修改 const 变量的操作，会报错。

> When the function is used, the compiler considers the types of the actual argument and invokes the appropriate function, that is, the one with signature closest to the actual argument.
 
编译器会自己选择与实际声明最接近的 argument 并进行应用。

> A copy constructor for a class T is typically declared to take a single argument, which is a constant reference to an object of the same class, that is, `T(const T&t)`.

这么写 copy constructor 是为了避免 memory leak，后面的函数体部分进一步完成了 copy，从而避免了 `shallow copy` 造成的 `memory leak。

{% highlight C++ linenos%}
Vect::Vect(const Vect& a){
size = a.size;
data = new int[size];
for( int i = 0; i<size; i++){
	data[i] = a.data[i];
	}
}
{% endhighlight %}
>  We perform this check using keyword **this**. For any instance of a class object, "**this**" is defined to be the address of this instance.

**this** 是当前类的实例的地址。
{% highlight C++ linenos %}
Vect& Vect::operator=(const Vect& a) {
	if(this != &a) {
		delete [] data; //delete old array
		size = a.size;
		data = new ine[size];
		for( int i = 0; i < size; i++) {
			data[i] = a.data[i];
		}
	}
	return *this;
}
{% endhighlight %}

> For example. consider a class SomeClass. Suppose that we want to define an overloaded output operator for this class, and this output operator needs access to private member data. 此时适合使用 friend 方法。

{% highlight C++ linenos %}
class SomeClass {
	private:
		int secret;
	public:
		friend ostream& operator<<(ostream& out, const SomeClass& x);
	};
	
	ostream& operator<<(ostream& out, const SomeClass& x)
		{ cout<<x.secret;}
{% endhighlight %}

> In order to indicate that a pattern string p is not found, the find function returns the special value string::npos.
{% highlight C++ linenos %}
if (s.find("doug") == string::npos){}
{% endhighlight %}


> s.erase(i,m) //remove the substring of length m starting at index i;
> s.replace(i, m, p) // replace the substring of length m