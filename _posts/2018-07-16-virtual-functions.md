---
title: "virtual functions"
date: 2018-07-16
header:
  image: "/images/C++ wallpaper.jpg"
exerpt: C++
---




## Introducing virtual fucntions

One of the main reasons that we use inheritance is to reuse common code across a hierarchy of related classes.
In these cases, we often find that the derived classes need to implement specialized versions of some member functions from the base class.
For example, Person class might define its display() member function to display only a person't name and age while Student class might want to display the student's course as well.
This is known as **"Overriding"**.

To define overridable member functions in C++, we use **"virtual"** keyword in the base class definition.

```c++
    class Person
    {
    private:
        std::string name;
        int age;

    public:
        virtual void display() const;        // Overrideable function.
        ...
    };
```

Note that you don't use the virtual keyword when you implement the function in the source file:
```c++
    void Person::display() const
    {
        std::cout << name << ", " << age << std::endl;
    }
```


## Overriding virtual functions

When we define a derived class, we can optionally choose to override some of all of the virtual functions defined in the base class.
At the same time, if we don't want to override, then we don't have to.

When overriding a virtual function in a derived class, we should use the virtual keyword again.
From the example above, continuing...

```C++
    class Student : public Person
    {
    private:
        std::string course;

    public:
         virtual void display() const;     // Override function from base class.
        ...
    };
```

In the source file for the derived class, implement the new version of the function for your derived class. If you want to leverage the existing functionality of the base-class version of the function, you can call the function using the syntax BaseClassName::FunctionName(). For example:

```c++
    void Student::display() const
    {
        // Call base-class version of display(), to display person-related info.
        Person::display();

        // Now display the student-related info.
        std::cout << course << std::endl;
    }
```

- if a base class defines one or more virtual functions, then it should also define a virtual destructor.

```C++
    class Person
    {
        ...
    public:
        virtual ~Person();
        ...
    };
```


## pointers and references in inheritance

C++ allows you to creat base-class variables and initialize them to point to the object made itself or its derived-class objects.

```c++
    // A base-class pointer can point to that type of object, or to any derived type of object.
    Person * p1 = new Person;
    Person * p2 = new Student;

    // A base-class reference can refer to that type of object, or to any derived type of object.
    Person & r1 = somePersonObject;
    Person & r2 = someStudentObject;
```


## pure virtual functions and classes

Pure virtual functions are abstract functions and pure virtual class is an interface in those languages.  
Pure virtual functions: just put = 0; at the end of a virtual function.  

If a pure virtual function is not defined in a derived class, then there would be an error occur in compiler.

### then what is an abstract function?

Being an abstract means that the function is not declared at that base class.  
Thus, the function needs to be overridden and redeclared at derived class.


