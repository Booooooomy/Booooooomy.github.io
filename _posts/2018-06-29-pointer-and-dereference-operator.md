---
title: "about * : Pointer and dereference operator"
date: 2018-06-29
header:
  image: "/images/C++ wallpaper.jpg"
exerpt: C++
---



## 3 different usages of * in C++.
1. multiplication    ex) 4 * 5
2. pointer    ex) int* num;
3. dereference    ex) * num;



## Pointer

before we get in, review this:

**Memory location of data:**
If we declare 
```c++
int num = 3; 
```
then the compiler automatically stores the variable num at certain address. Once the memory location is done by declaring it, the memory address is fixed during an execution of the application code(while num is in scope).


### Definition of Pointer:
A pointer is **a variable that holds the memory address of an object**. *We can simply think of a pointer as another variable that contains address in it.* A pointer never points to the object or data itself... it only points to the memory address of an object.  
If we want to make a variable pNum, which is a pointer pointing to the address of num, it can be defined like this.
```c++
int* pNum = &num; // int* is a bottle that contains an address value of some integer value, and pNum is a pointer itself, and it contains the address of num.
```
it has the same structure as int num = 3;.  
A pointer cannot be compiled without initialization just like other types like int.


If the concept of a pointer is confusing, then we can just simply think of it in this way.

A bottle that **contains** a cuisine called **an address** of integer.


### Why are pointers so important?

1. As the amount of data gets bigger, passing a pointer is much more efficient than passing the entire data structure. 
2. The pointer gives you a direct access to the data.
3. Pointers allow to dynamically allocate memory during run time(Dynamic Memory Allocation: do not need to know the size or number of memory that will be needed for an object at compile time, rather the size is allocated during runtime).


### The allocation of a pointer

let's say there are two pointers called numPtr and numPtr2. Since both of them are pointers, if we do **numPtr = numPtr2;**, numPtr points to the same address where numPtr2 is also pointing to.  
Just to double check, if we do (numPtr == numPtr2) here, we get true boolean value, since now both pointers are same.



## the . and -> operator

We use . and -> operators many time in programming. Each usage is different.  
Each is, **object.member; pointer->member;.**  
So if a thing that a member is in is an obejct, use . operator and it is in a pointer, use -> operator.  
For example, **(* nPtr).member** is the same thing as **nPtr->member**.



## The dereference operator

The asterisk( * ) is used as a dereference operator as well.  
From the pNum example above, if there is a notation looks like (* pNum) then it is a dereferenced value of pNum, which is num, which is 3.



## How to distinguish which one is pointer and whicn one is dereference operator???

 * If * is at the left side of the assignment =, then it’s used as a pointer.
 * If * is at the right side of the =, then it’s used as a dereference operator.
