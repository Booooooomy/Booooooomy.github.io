---
title: "inheritance"
date: 2018-07-10
header:
  image: "/images/C++ wallpaper.jpg"
exerpt: C++
---



## What is inheritance?

New classes can be derived from existing classes using a mechanism called "inheritance". Classes derived **FROM** are called **Base classes** and **Derived classes** are also known as **sub-classes**.


## How does it look like?

The form of inheritance is shown in the example below.

```c++
class Vehicle
{ 
    private:
               string Make;
       string Color;
       ...
}; 

class Car: Vehicle
{ 
     // member list includes Make and Color
     // other Car specific members would go here.
};
```

Vehicle is the base class and Car is the derived class. Car automatically inherits the Make and Color properties and is also free to implement its own properties and methods specific for a Car.


## Types of Inheritance in C++

**C++ supports 3 different forms of inheritance: public, private, protected.**

Public inheritance describes how a derived class inherits all the member variables of a base class but is only able to directly access the public members of the base class.
All members of the base class will retain their accessibility in the derived class.  

Example of public inheritance:

```c++
**Person.h**
#pragma once
#include <string>

class Person
{
private:
   std::string firstName;
public:
   Person();
   ~Person();
}

**Student.h**
#pragma once
#include "Person.h"

class Student: public Person
{
public:
   Student();
   ~Student();
};

**Student.cpp**
#include "Student.h"
#include "stdafx.h"

Student::Student()
{
}

Student::~Student()
{
}

firstName = "Tom";
// this line will cause a compiler error

```

This code above will cause a compiler error because Student is a derived class of Person using public inheritance and we tried to access to firsName and give it a string of "Tom".
When inherited using public inheritance, derived class can't access to the base class's private variable or function.
We can get rid of this error simply and there are 2 ways of doing so- 1. get and set function 2. Initializing parameters of an object of base class.  

Here is an example for case 2.

```c++
Student::Student():Person("Tom")
{}
```

In Objective-C, it is required to have the base class initialized before the derived classes.


## The Protected keyword

Sometimes we may like to keep certain members of the base class private to the outside world but public to derived classes of the base class.
Here, we use keyword - protected. **If a variable or function is in protected keyword, then it can be accessed by derived classes but not by outside world**.


## The combinations of the component declaration and inheritance

![table](https://i.stack.imgur.com/W6CJ3.jpg)

1. how a variable / function is declared at base class:  

First, if declared as public at base class then it is accessible from both derived class's declaration and object.  
Second, if declared as private at base class then it is not accessible from both ".  
Third, if declared as protected at base class then it is accessible from derived class's declaration, but not from its object.  

2. what type of inheritance we use:  

First, if inherited as public, all the type remains same as it is in base class - but access to private is N/A.  
Second, if inherited as private, all the type change into private type - but access to private is N/A.  
Third, if inherited as protected, public type changes into protected, and everything same, but access to private is N/A.  
