---
title: "vectors and vector functions"
date: 2018-07-25
header:
  image: "/images/C++ wallpaper.jpg"
exerpt: C++
---



## what is vector?

...not the same concept from math's vectors...  
STL vectors are **same as dynamic arrays with ability to resize itself automatically when an element is inserted or deleted**.
Any type can be assigned into vector, but only one type for a vector can be assigned.


## format of vector:

```c++
#include<vector>
using namespace::std;
vector<typename> vectorname; // vector<int> intvector;
```


## what is a difference between arrays and vectors?

Array is just a sequential memory container and it cannot grow its size during the program runs. 
However, as we covered beforehand, we can use dynamic memory allocation and resize an array.
STL Vector is a template class that uses this method. So STL vector is almost same as dynamic array, but few things differ.  

**std::vector is standardized STL while dynamic array is created by me, which means others can more easily understand STL vector over dynamic array.


## STL vector API


(1) push_back()

putting a new data at the back of the vector. For example, if a[0] and a[1], a.push_back(1) makes a[2] == 1.


(2) pop_back()

getting rid of the last data of the vector. The size of the vector automatically reduces one.


(3) back()

returning the last data.


(4) size()

size shows how many elements of the vector are occupied by data.


(5) resize()

resizing the number of elements of vector.
