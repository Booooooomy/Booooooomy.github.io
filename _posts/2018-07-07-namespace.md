---
title: "namespace"
date: 2018-07-07
header:
  image: "/images/C++ wallpaper.jpg"
exerpt: C++
---



## what is namespace:

If 2 or more functions have same name but differenct parameter in a class, then 'function overloading' system of visual studio automatically chooses the right one that matches the parameter. However, if both functions have same name and same parameter, or we make a function with same name and parameter with one of STL functions, 'function overloading' cannot happen.  
C++ uses namespaces to help resolve those conflicting issues. Namespace is a scope container that contains classes, variables, and other identifiers and prevent name collisions and ambiguity.


## how to use namespace:

Let's take a look at the example.

This is out namespace ContosoData.

```C++
namespace ContosoData  
{      
    class ObjectManager   
    {  
    public:  
        void DoSomething() {}  
    };  
    void Func(ObjectManager) {}  
}
```

We can use
1.	A scope operator

```C++
ContosoData::ObjectManager mgr;  
mgr.DoSomething();  
ContosoData::Func(mgr);
```

So every time we use class or function from namespace ContosoData, we have to put ContosoData:: in front of each of them.
On the other hand, we can use using declaration. In many cases, using using declaration is much convenient and efficient.

2.	‘using’ declaration

```C++
using ContosoData::ObjectManager; 

ObjectManager mgr;  
mgr.DoSomething();
ContosoData::Func(mgr);
```

By using 'using' declaration, we don’t have to put ContosoData:: when we use ObjectManager. However, we didn’t declared Func(mgr) yet so ContosoData:: for that one is still needed.

If we’re sure that there is no keyword in std that would be confused with other class's keywords with same name and parameter, then we can simply declare by using using namespace ContosoData; at the very top.

```c++
using namespace ContosoData;

ObjectManager mgr;  
mgr.DoSomething();  
Func(mgr);
```

*By doing this, all of the keywords used in the program, if they are included in namespace Contosodata, will be automatically called whenever they are used. So if there is any kind of uncertainty that some of the keyword might be included in other files than namespace Contosodata, we should not use this method.*

* * Do not use 'using' in .h file because most likely it would make a collision with other declaration in header file.*


## +) Exceptional case:

There is an exception of 'using' declaration. If our c++ implementation file is separated from our header file, where our namespace is declared, we cannot skip but should put ContosoDataServer:: thing every time in the file.

```c++
//contosoData.h   
#pragma once  
namespace ContosoDataServer  
{  
    void Foo();  
    int Bar();  
}


#include "contosodata.h"  
using namespace ContosoDataServer;   

void ContosoDataServer::Foo() // use fully-qualified name here  
{  
   // no qualification needed for Bar()  
   Bar();   
}  

int ContosoDataServer::Bar(){return 0;}
```
