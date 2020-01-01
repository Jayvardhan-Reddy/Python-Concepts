# Python-Concepts
Python learning material

## Basics

1. Mutable & Immutable

2. List & Tuple

3. Array & List

4. Lambda
    - Map
    - Filter
    - Reduce
  
5. Functions
    - Recursive
  
6. Global vs Globals (Local & Global Variable)

7. Decorators
    - To change behaviour of existing function during compile time.
      eg:

```        
   Checks if numerator is less than denominator and performs swap of variables
   
   def div(a,b):
     print(a/b)
     
   def smart_func(func):
     def inner(a,b):
       if a < b:
         a,b = b,a
       return func(a,b)
   return inner
   
   div = smart_func(div)
   div(2,4)
```

8. Module

9. __ _name_ __ (Special Variables)
    - main
  
10. OOPS/Functional/Procedural

11. __ _init_ __ (Special Methods)
    - Similar to Constructor in Java
   
12. Namespace 
    - Is an area where you create and store Object/Variable   
      - Class Namespace
      - Object/Instance Namespace

13. Types of Variables
    - Instance
    - Class/Stactic variable
  
14. Types of Methods
    - Instance
    - Class
    - Static
  
15. Overriding vs Overloading

16. Inheritance
    - Multiple
    - Multi-level
  
17. Iterator
    - iter()
    - next()
  
18. Generator
    - Yield()
  
19. Polymorphism
    - Duck Typing
      - Execute()
    - Operator Overloading
    - Method Overloading
  
20. Exception Handling

21. Multithreading

22. File Handling

----------------------------

## Advance Topics (In-Depth)

1. Type Checking

Type checking is mainly classified into 2 types

i) Static

ii) Dynamic

   - We dont need to specify the type of variable and objects
   - Variable is known at run-time
   - Dynamically typed OOP

2. Data type classification

  It is mainly classified into two categories
      
   - Mutable
   
   - Immutable
    
   - In python, everything is considered as Objects. They are categorized as shown below

   - Mutable data types: list, dictionary, set and user-defined classes.
```
   eg:
    list_values = [1, 2, 3]
    list_values[0] = 100
    print(list_values)
```
   
   - Immutable data types: int, float, decimal, bool, string, tuple, and range.
```	  
	  eg1:
	     set_values = (10, 20, 30)
	     set_values[0] = 100	// Will throw an error: 'tuple' object does not support item assignment

	  eg2:
	     number = 42
	     print(id(number))

	     number += 1
	     print(id(number))
```

  Here id is identity which is the object’s address in memory. A new id would be created the second time, therefore making it immutable.
  Similar to String concept of Java

3. Object instantiation & Storage details

  The default implementation of Python is CPython.
	
  Therefore allocation/deallocation of memory might be done using malloc and dealloc functions of C language.

   - There is a struct called a 'PyObject', which every other object in CPython uses and it consists of 2 things.
     --> ob_refcnt: reference count
     --> ob_type: pointer to another type

   - Stored in OS-specific Virtual Memory Manager and in CPython object allocator is responsible for it.
   eg:
       a = 10;

   - Garbage collector cleans based on the reference count of Object. When it reaches '0' the object is removed.

4. Bytecode Compilation and Execution

   - Python is an interpreted programming language. Your Python code actually gets compiled down to more computer-readable instructions called bytecode.
```   eg:
	import py_compile
	py_compile.compile(<filename>.py)
```
   - dis module provides a "disassembler" for Python bytecode
```
       def hello()
    	  print("Hello, World!")
```
   To get the bytecode listing for the hello() function above typed in python cmd
```
       import dis
       dis.dis(hello)
```
   -  The CPython VM only knows about CPython bytecode, CPython interpreter is used to run it.

5. Tuple: Insertion and Deletion of elements in Python

   - It is immutable in nature.

   - Deletion, insertion, and update is not possible.

Lets look at one of the workarounds to overcome it.
```
    - Insertion
      eg:
	z = (10,302,03,90)
	z += (52,)
	print(z)

    - Deletion
      eg:
	tup = (10, 20, 30, 40, 50)
	conv_list = list(tup)
	conv_list.pop(1)
	tup = tuple(conv_list)
```
Here it does not attempt to modify the reference in place, it reassigns.

6. Sorting a Tuple

   - use sorted()

	eg:
	 a = (6,7,4,2,1,5,3)
	 sorted(a)

	O/P:
	 [1, 2, 3, 4, 5, 6, 7]

   The sorted method returns a list as output.

  - Descending order

   You can pass another boolean parameter reverse as an argument to the sorted function as below:
  ``` eg:
       sorted(a, reverse=True)
   ```

7. List VS Tuple

➡️ List

   - Mutable by nature
   - Variable length
   - Slow while iterating values
   - Due to mutability not an idle candidate for dictionary keys
   - Copied
   
   ```
    eg:
      list_names = ['Jay', 'Reddy', 'Vardhan']
      copyNames = list(list_names)
      print(list_names is copyNames)
    O/P:
      False
```

➡️ Tuple

   - Immutable by nature (write protected)
   - Fixed length
   - Faster while iterating
   - Suitable candidate for Dictionary keys
   - Reused i.e, returns itself
   ```
    eg:
      tup_names = ('Jay', 'Reddy', 'Vardhan')
      copyNames = tuple(tup_names)
      print(tup_names is copyNames)
    O/P:
      True
```

8. Creating Empty Dictionary

  ➡️ my_dict = dict() // slow

  ➡️ my_dict = {} // Fast

9. Array Deep & Shallow Copy

➡️ Shallow Copy (or) View

   - Creates a new Array at different location	
   - Changes are affected for both even if one of the array is modified.
	
```
aar2 = arr.view()
arr[1] = 10
print(arr)
print(id(arr))
print(aar2)
print(id(aar2))
```

➡️ Deep Copy

   - Creates a new Array at different location
   - Changes to one Array does not affect the values of other Array
	
```
aar3 = arr.copy()
arr[1] = 15
print(arr)
print(id(arr))
print(aar3)
print(id(aar3))
```
