---
title: "about &: reference-type and address-of operator"
date: 2018-07-02
header:
  image: "/images/C++ wallpaper.jpg"
exerpt: C++
---




## 3 different possible usage of &(ampersand)

1. address of a     ex) int a, scanf(%d; &a)
2. bit and operator     ex) 0 & 1
3. **reference variable**     ex) int a = 20; int& b = a;

Among those 3 different usage of & in c++, I will go over 1 and 3.


## Reference variable(only possible on C++, doesn't work on C)

A reference is a simple reference datatype that is relatively less powerful but safer than the pointer type.
If int& a = b;, a is an alias of b. a is just another name of b. So a is b. Not just it's value that's the same, **but they are just "same"**.

Here is a good example. This will show the difference between call by reference and call by value.
Swap is a function that swaps the value of x and y.

First, let's try with call by value

```c++
int main()
{
   int a = 100; b = 200;
   swap(a, b);
   printf("a = %d, b = %d\n", a, b);
}

void swap(int x, int y)
{
   int tmp = x;
   x = y;
   y = tmp;
}
```

What would the result be? **The values are not swapped.**  
Why? the value of x and y would be swapped but they will expire as soon as the scope of the program exits the swap function.  
Let's use call be reference then.

```c++
int main()
{
   int a = 100; b = 200;
   swap(a, b);
   printf("a = %d, b = %d\n", a, b);
}

void swap(int& x, int& y)
{
   int tmp = x;
   x = y;
   y = tmp;
}
```
Now it works. The only thing I did was to change parameters of swap function from int to int&.  
By doing so, we could call not a copy of a and b, but called the exact a and b themselves.  
this is called **call by reference**.


### Difference between refernce and pointers

1. reference cannot be uninitialized. Think of it as a shadow. There can be no shadow if there is no object.  
If there's no object to reference, for sure it would cause a syntax error.
2. reference cannot be null while pointers can.
3. Once a refernce is created, it can't be later made to reference another object while it happens to pointers many times.


## & as an address-of operator

& is the unary address operator. When applied to a variable or object it returns its address, a value that can be stored in a pointer.


## How to distinguish & of reference type from & of address-of operator?

If used with int& declaration, it's reference. If not, it's an address-of operator.


## Examples

If we write a code like below,

```c++
    int num = 3;
    int &refNum = num;

    cout << "num contains " << num << endl;
    cout << "refNum contains " << refNum << endl;

    refNum++;    // increment refNum by 1

    cout << "num contains " << num << endl;
    cout << "refNum contains " << refNum << endl;
    cout << "refNum is located at " << &refNum << " and num is located at " << &num << endl;
```

we get this result:

```c++
    num contains 3
    refNum contains 3
    num contains 4
    refNum contains 4
    refNum is located at 0018FE14 and num is located at 0018FE14
    Press any key to continue . . .
```

So num and refNum are essentially same.  
Reference is very, very useful when you want to make another name of a variable.
