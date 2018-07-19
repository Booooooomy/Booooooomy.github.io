---
title: "Allocating and deallocating memory"
date: 2018-07-04
header:
  image: "/images/C++ wallpaper.jpg"
exerpt: C++
---




## Allocating memory in C++

Allocating memory during runtime of a program is a common requirement.  
For example, you may not know how many objects that your application will be needed before you run the application.  
In this case, you'd want to make a program that creates objects whenever needed during a runtime automatically.
It is possible in both C and C++. It's called **Dynamic memory allocation**.

```c++
int* pInt = new int;  // creating a pointer that can possibly point to int types, but not pointing at anything for now
double* pDouble = new double;  //same, but points to double types instead of int
```

By doing dynamic memory allocation, we are making an empty(unassigned) pointer that could possibly point to a certain data type.  
When I first learned this, I questioned, "Why didn't the C++ makers make something like int* pInt;? What's the point of having 'new' keyword?"  
It's because sometimes it is possible to have A type pointer to point to B type variable. For example, it is possible that long pointers point at int variable.  
Thus, our OS cannot know what variable the pointer is going to point at and thus cannot assign a proper size for the variable.  


## Deallocating memory(deallocation)

Deallocation is the last required step after using 'new' keyword. All you have to do is to delete the memory that you dynamically allocated created using a keyword 'delete'  
Continuing from the example code above,

```c++
int* pInt = new int;  // creating a pointer that can possibly point to int types, but not pointing at anything for now
double* pDouble = new double;  //same, but points to double types instead of int

delete pInt;
delete pDouble;
```

Simple, right? just type delete keyword and a pointer that you used for DMA. By doing so, you are deallocating a memory.  
This step is essential, theoretically, because if you don't, the memory would not be deallocated until the program ends and will casue memory leak.  
But in real application, it's ok if you don't do so because most of the OS, including windows and macOS, automatically delete them for you if you forget to do so.  
By the way, in C, keywords malloc() and free is used instead of keywords new and delete.
