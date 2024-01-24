What are namespaces?

https://www.youtube.com/shorts/ftMEPQcVp4c

Container for a set of related class and other types.
```C#
namespace MyNameSpace
{
	class MyClass
	{
		// class impemenet
	}
}
```

Now when we need MyClass...

```C#
using MyNameSpace;

MyClass myInsance = new MyClass();

```