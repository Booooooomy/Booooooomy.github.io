---
title: ""
date: 2018-06-30
header:
  image: "/images/C++ wallpaper.jpg"
excerpt: "C/C++"
---

# Pointer

First, let’s review the basic C++ pointers beforehand.

## Memory location of data:

If we declare 
```c++
int num = 3; 
```

then the compiler automatically stores the variable num at certain address. Once the memory location is done by declaring it, the memory address is fixed during an execution of the application code(while num is in scope).

## Definition of Pointer:
A pointer is a variable that holds the memory address of an object. We can think of a pointer as another variable that contains address in it.
If we want to make a variable pNum, which is a pointer pointing to the address of num, it can be defined like this.
```c++
Int* pNum = &num;
```

it has a same structure as int num = 3;.
A pointer cannot be compiled without initialization just like other types like int.

<Importance of pointers>
1. As the amount of data gets bigger, passing a pointer is much efficient than passing the entire data structure. 
2. The pointer gives you a direct access to the data.
3. Pointers allow to dynamically allocate memory in application (DMA: do not need to know the size of memory that will be needed for an object at compile time, but the size is allocated during runtime).


#The dereference operator#

The asterisk(*) is used as a dereference operator as well. From the pNum example above, if there is a notation looks like *pNum then it is a dereferenced value of pNum, which is 3.

How to distinguish which one is which???

	**If * is at the left side of the assignment =, then it’s used as a pointer.**
	**If * is at the right side of the =, then it’s used as a dereference operator.**
