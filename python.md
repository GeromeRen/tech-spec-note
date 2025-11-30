# Basic
```python
a = int("3")
print(type(a))
b = str(1)
print(type(b))
c = float("1.123")
print(type(c))
print("hello", "world", sep="-")
a = 30
if (a == 30):
    print("a is 30")
else:
    print("a is not 30")
a = 'sb'
# match a:
#     case 'sb':
#         print("a is sb")
#     case 'bb':
#         print("a is bb")
#     case _:
#         print("a is neither sb nor bb")

for i in range(6):
    print(i) #1 2 3 4 5 

while i < 30:
    if i == 20:
        pass
    i += 1
```

Multi-line string
```python
name = '''gerome
is 
good
'''
```

```python
print("------------")
name = 'gerome is good'
print(name[-1])
print(name[-2])
print("------------")
name="gerome ren"
print(name[2:4]) # goes from 2 to 4-1
print(name[2:-1]) # important: size of name is 10, then this is equals to name[2:9]
print(name[2:9])
```

# StÍring methods
```python
a = "hello gerome"
print(a.upper())
print(a.lower())
print(a.capitalize())
print(a.title())

a = " hello world "
print(a)
print(a.strip())
print(a.lstrip())
print(a.rstrip())

a = "hello world, welcome to the world of python"
print(a.find("world"))
print(a.replace("world,", "hey!" ))

#split will convert to list
a = "a, b, c, d"
print(a.split(",")[0])
```

# convert list to string
```python
print("~".join(["1", "2", "3"])) # "1~2~3"

text="hello123"
print(text.isalpha())
print(text.isalnum())
print(text.isdigit())
```

# f-string (formatted string literal)
```python
a = "gerome"
b = "ren"
print(f"hello {a} {b}, how are you!")
```

# function
```python
def average(a, b, c):
    return (a + b + c)/3
print(average(1, 2, 3))

'''default value of input param'''
def average(a, b, c=3):
    return (a + b + c)/3

print(average(1, 2)) #2

'''explictly specify param order'''
def average(a, b, c=10):
    return (a + b + c)/3
print(average(b=10, a=10)) #10
```

# lambda function
```python
'''lambda funtions are anonymous inline functions'''
sum = lambda x, y: x + y
print(sum(1,2)) #3
```

# recursion 
```python
'''A function calling itself to resolve problem'''
'''FIBONACCI SERIES 0 1 2 3 5 8 13 ...'''
def fib(n):
    if (n==0 or n==1):
        return n

    return fib(n-2) + fib(n-1)
print(fib(5)) #5
```

# Python module
```python
'''
Why use modules? we dont want to reinvent the wheel, so we use modules
types of modules in python:
- built-in modules: come with python installation: https://docs.python.org/3/py-modindex.html
- external modules: need to be installed via pip
- custom modules: created by you
'''
import math
import os
print(math.sqrt(16)) #4.0
print(os.getcwd()) #/Users/gerome/python_course

'''how to create custom module? see mymodule.py file'''
import mymodule
mymodule.hello()

'''external modules

external moduels can always being installed via pip

pip install requests

after install, requests.py will be saved by phthon installer

doc about requests module: https://pypi.org/project/requests/
another good doc on requests module: https://requests.readthedocs.io/en/latest/
'''
import requests
r = requests.get("https://www.baidu.com")
print(r.status_code) #200
```

# variable scope 
```python
'''
Function only keeps variables until it returns. After that, all variables inside function are deleted from memory.
'''

global abc # declare a as global variable
abc = 10

def test():
    global abc
    abc += 5
    print(f"global variable abc is {abc}") #15
test()
```


# List
```python
'''List is ordered (this order is present and also maintained throughout the program) and mutable (changable) collection of items'''
print("#### append ####")
mylist = [1, 2, 3, 4, 5]
print(mylist[2:4]) # 3 4. We can slice list just like string
mylist.append(6) # add 6 to the end of list
print(mylist) # [1, 2, 3, 4, 5, 6]

print("#### pop ####")
mylist.pop()
print(mylist) # [1, 2, 3, 4, 5] # remove last item

mylist.insert(2, 10) # insert 10 before index 2
print(mylist) # [1, 2, 10, 3, 4 5]

print("#### list ####")
list1 = [1, 2, 3]
list2 = [4, 5, 6]
list1.extend(list2) # take another list as input and it will append all the elements to the end of the list
print(list1) # [1, 2, 3, 4, 5, 6]
print(list2) # [4, 5, 6]

print("#### sort ####")
list1 = [4, 2, 1, 6, 9]
list1.sort()
print(list1) # [1, 2, 4, 6, 9]

print("#### reverse ####")
list1 = [4, 2, 1, 6, 9]
list1.reverse()
print(list1) # [9, 6, 1, 2, 4]

print("#### remove ####")
list1 = [4, 2, 1, 6, 9]
list1.remove(2) # remove the 2 element
print(list1) # [4, 1, 6, 9]

print("#### insert ####")
list1 = [4, 2, 1, 6, 9]
list1.insert(2, "gerome") # remove element at index
print(list1) # [4, 2, 'gerome', 1, 6, 9]

print("#### list comprehention ####")
table = []
for i in range (1, 11):
    table.append(i*2)
print(table) # [2, 4, 6, 8, 10, 12, 14, 16, 18, 20]

'''shortcut using list comprehention in below'''
table = [i*2 for i in range(1, 11)]
print(table) # [2, 4, 6, 8, 10, 12, 14, 16, 18, 20]
```

# Tuples
```python
''' Tuples are ordered but immutable (unchangable after creation) collection of items
    Why need Tuples? 
    1. Faster than lists (since they are immutable)
    2. Used as dictionary keys (since they are hashable)
    3. Safe from unintended modifications
'''
t1 = (1, 2, 3, 4, 5)
#t1[0] = 10 # will raise error

# to create a tuple with a single element, we need to add a comma after the element
# because parentheses is sth tha you can always use to group certain numbers, or to make certain operations
t2 = (1,)

# unpacking of tuples: where we assign certain variables with the content of the tuple
t3 = (1, 2, 5)
a, b, c = t3
print(a) #1
print(b) #2
print(c) #5

print("#### count(x) ####")
# count(x): returns the number of times x appears in the tuple
t1 = (1,3,1,3,1,4,5)
print(t1.count(3)) #2   

print("#### index(x) ####")
# index(x): returns the index of the first occurrence of x in the tuple
t1 = (1,3,1,3,1,4,5)
print(t1.index(3)) #1
```

# Sets
```python
'''
    sets are unordered, unique collections (no duplicates)
    no order, just like a bucket, you are simply storing elements
    since it's unorded, we cannot access elements via indexing s[0], s[1] etc.
    main use case of sets: membership testing, removing duplicates from a collection
'''
fruits = {"apple", "banana", "cherry"}
# print(fruits[1]) # TypeError: 'set' object is not subscriptable
fruits.add("orange")
print(fruits) # {'banana', 'orange', 'cherry', 'apple'}

fruits.remove("apple")
print(fruits) # {'banana', 'orange', 'cherry'}

### discard() - Remove if present, No errors if element not found###
fruits = {"apple", "banana", "cherry"}
fruits.discard("cherry")
fruits.discard("gerome")
#fruits.remove("hello") # this will give error as element not found
print(fruits) # {'banana', 'orange'}
fruits.pop() # remove random element

### remove duplicates from a list ###
a = {3, 23, 1}
b = {23, 4, 2, 55, 1}
c = a.union(b)
print(c) # {1, 2, 3, 4, 55, 23}

### intersection() - elements present in both sets ###
a = {3, 23, 1}
b = {23, 4, 2, 55, 1}
c = a.intersection(b)
print(c) # {1, 23}
```

# Dictionary
```python
'''
    key should be hashable (immutable types like string, number, tuple), means Python should be able
    to hash that particilar data type internally.
'''
student = {"name": "gerome", "age": 25, "courses": ["math", "compSci"]}
student["age"] = 26 # modify existing entry

### Dictionary Methods - print all keys, values or items###
print(student.keys()) # dict_keys(['name', 'age', 'courses']
print(student.values()) # dict_values(['gerome', 26, ['math', 'compSci']])
print(student.items()) # dict_items([('name', 'gerome'), ('age', 26), ('courses', ['math', 'compSci'])])

### Remove "age" key
student.pop("age")

### Empties dictionary ###
student.clear()

### dictionary comprehention ###
s = {i: i+1 for i in range(5)}
print(s)
```

# When to use Each Data Structure
| Data Structure | Features                             | Best For                              |
|----------------|--------------------------------------|---------------------------------------|
| List           | Ordered, Mutable                     | Storing sequences, dynamic data       |
| Tuple          | Ordered, Immutable                   | Fixed collections, dictionary keys    |
| Set            | Unordered, Unique                    | Removing duplicates, set operations   |
| Dictionary     | Ordered, Key-Value Pairs, Mutable    | Fast lookups, structured data         |

# Class
```python
'''
- self -> represents the instance of the class
'''
class Employee:
    company_name = "Accenture" # class attribute
    def __init__(self, salary, name, bond):
        self.salary = salary
        self.name = name
        self.bond = bond
        self.company_name = self.__class__.company_name
    def get_salary(self):
        return self.salary
    def get_info(self):
        print(f"Employee Name: {self.name}, Salary: {self.salary}, Bond: {self.bond} years, Company: {self.company_name}")

e1 = Employee(34000, "gerome", 4)
print(e1.get_salary()) #34000
print(e1.get_info()) #34000


'''
super() -> get an instance of parent class, and access parent class methods and attributes
'''

class Animal:
    def speak(self):
        print("Animal speaks")

class Cat(Animal): # This is how inheritance is done in Python
    def speak(self):
        super().speak()
        print("Meow Meow")

cat = Cat()
cat.speak() #Meow Meow

'''
    overload operator by writing __xx__ function 
    __sub__ (-)
    __mul__ (*)
    __truediv__ (/)
    __eq__ (==)
    __ne__ (!=)
    __lt__ (<)
    __gt__ (>)
    __len__ (len())
    __getitem__ (indexing [])
    __setitem__ (indexing [])
    __delitem__ (deleting item [])
    for list/dictionary-like behavior - allowing you to use [] with your objects
'''

class Point:
    def __init__(self, x, y):
        self.x = x
        self.y = y
    def sum(self, point):
        return Point(self.x + point.x, self.y + point.y)
    
    def __add__(self, point):
        return Point(self.x + point.x, self.y + point.y)
    def __eq__(self, point):
        return self.x == point.x and self.y == point.y
    
p1 = Point(1, 1)
p2 = Point(2, 2)
p3 = p1.sum(p2)
print(f"Point p3: ({p3.x}, {p3.y})") #(3, 3)

p1 = Point(1, 1)
p2 = Point(2, 2)
p3 = p1 + p2
print(f"Point p3: ({p3.x}, {p3.y})") #(3, 3)

p1 = Point(3, 3)
p2 = Point(3, 3)
print(f"is p1 equal to p2? {p1 == p2})") #True
```

# Decorators
```python
'''
Decorators are a way to modify or enhance functions or methods without changing their actual code.

It's a key feature in python that enable code reusability and cleaner function modifications. They are commonly used for:
- Logging: Recording when a function is called and it's argument
- Timing: Measuring how long a function takes to execute
- Authentication and Authorization: Checking i fa user has permission to access a function
- Caching: Storing the results of a function call so that subsequent calls with the same argumetns can be returned quickly
- Rate Limiting: Controlling how often a function can be called.
- Input Validation: Checking if the arguments to a function meet certain criteria
- Instrumentation: Adding monitoring and profiling to funtions.

Frameworks like Flash and Django use decorators extensively for routing, authentication, and defining middleware.
'''
def decorator1(func):
    def wrapper():
        print("I am about to execute a function...")
        func()
        print("I have executed the function.")
    return wrapper
@decorator1
def say_hello():
    print("Hello!")
say_hello()
#I am about to execute a function...
#Hello!
#I have executed the function.

print("#### Pass param to decorator ####")

def say_hello_decorator(n):
    def decorator1(func):
        def wrapper():
            print(f"I am about to execute {n} times...")
            for i in range(n):
                func()
            print(f"I have executed the function {n} times.")
        return wrapper
    return decorator1
@say_hello_decorator(5)
def say_hello():
    print("Hello!")

say_hello()
#I am about to execute 5 times...
#Hello!
#Hello!
#Hello!
#Hello!
#Hello!
#I have executed the function 5 times.
```

# Getters and Setters using Decorators
```python
print("#### Getters and Setters using Decorators ####")
class Employee:
    def __init__(self, age):
        self._age = age

e1 = Employee(40)
e1.salary = 20000
print(e1.salary)

e2 = Employee(30)
#print(e2.salary) # will raise error as salary attribute not found

# To prevent this, we can use getters and setters using decorators

class Employee:
    def __init__(self, age):
        self._age = age
    
    @property # to define getter for Employee
    def salary(self):
        return self._salary
    @salary.setter
    def salary(self, value):
        
        r = requests.get("https://www.baidu.com")
        if value == None:
            self._salary = r.status_code
        else:
            self._salary = value

e3 = Employee(50)
e3.salary = "$1000"
print(e3.salary) #$1000

e4 = Employee(35)
e4.salary = None
print(e4.salary) #200
```

# Static && Class Methods using staticmethod decarator
```python
'''
    !!!! Use case: 
    - there will be no self pass to staticmethod
    - Sometimes we want to write some utility methods and we want them as part of our classes, like below staticmethod sum

'''
class Employee:
    company_name = "Accenture" # This is class attribute
    def __init__(self, salary, name, bond):
        self.salary = salary # this is instance attribute
        self.name = name
        self.bond = bond

# So you cannot call Employee.salary directly, because salary is instance attribute

# By default a method in a class is an instance method, which means it requires an instance of the class to be called.
# So e1.sum(1, 2) doesn't work because sum is not an instance method.
class Employee:
    company_name = "Accenture" # This is class attribute
    def __init__(self, salary, name, bond):
        self.salary = salary # this is instance attribute
        self.name = name
        self.bond = bond
    def sum(a, b):
        return a + b
e1 = Employee(34000, "gerome", 4)
e2 = Employee(40000, "ren", 3)
#e1.sum(1, 2) # will raise error - TypeError: sum() takes 2 positional arguments but 3 were give
# So to fix this, we can use staticmethod decorator. 

class Employee:
    company_name = "Accenture" # This is class attribute
    def __init__(self, salary, name, bond):
        self.salary = salary # this is instance attribute
        self.name = name
        self.bond = bond
    @staticmethod
    def sum(a, b):
        return a + b
e1 = Employee(34000, "gerome", 4)
print(e1.sum(1, 2)) #3

print("#### Change class attribute and instance attribute ####")
class Employee:
    company_name = "Accenture" # This is class attribute
    def __init__(self, salary, name, bond):
        self.salary = salary # this is instance attribute
        self.name = name
        self.bond = bond
    @staticmethod
    def change_company_name(e, new_name):
        e.company_name = new_name # or Employee.company_name = new_name
    @staticmethod
    def change_salary(e, new_salary):
        e.salary = new_salary
e1 = Employee(34000, "gerome", 4)
print(e1.company_name) # Accenture
print(e1.salary) # 34000
e1.change_company_name(e1, "Google")
e1.change_salary(e1, 50000)
print("change.....")
print(e1.company_name) # Google
print(e1.salary) # 
```

# Dunder Methods (double underscore methods)
```python
'''
    Magic methods, also called dunder (double underscore) methods, are special methods in Python
    that have double underscores at the beginning and end of their names (e.g. __init__, __str__,
    __add___). These methods allow you to define how your objects interact with built-in Python
    operator overloading and customize the behavior of your classes in a Pythonic way. 

    basically provide a way to implement operator overloading towork with constructors that is
    constructing new objects from existing classes. And they can also customize the behavior of
    some of the default Python constructs. 

    overload operator by writing __xx__ function 
    __sub__ (-)
    __mul__ (*)
    __truediv__ (/)
    __eq__ (==)
    __ne__ (!=)
    __lt__ (<)
    __gt__ (>)
    __len__ (len())
    __getitem__ (indexing [])
    __setitem__ (indexing [])
    __delitem__ (deleting item [])
    for list/dictionary-like behavior - allowing you to use [] with your objects
'''

class Employee:
    def __init__(self, salary, name, bond):
        self.salary = salary
        self.name = name
        self.bond = bond
    def __str__(self):
        return f"Employee Name: {self.name}, Salary: {self.salary}, Bond: {self.bond} years"

e1 = Employee(34000, "gerome", 4)
print(str(e1)) #Employee Name: gerome, Salary: 34000, Bond: 4 years
```

# Exception Handling and Custom Errors
```python
'''
ZeroDivisionError

FileNotFoundError - When you try to open or access a file that doesn't exist.

PermissionError - When you try to perform an operation without the necessary access rights

ValueError - When a function receives an argument of the right type but an inappropriate value.

TypeError - When an operation or function is applied to an object of an inappropriate type.

FileNotFoundError

PermissionError
"2" + 2
len(5) len does not support integer

IndexError
my_list = [1, 2, 3]
print(my_list[5]) # The list only has indices 0, 1, and 2.

Exception
'''

try:
    # Code that might raise an exception
    #number = int(input("Enter a number: "))
    number = 0
    result = 10 / number
    print(f"Result is {result}")

    raise ValueError("invalid value")
except ValueError:
    # Handles the specific case where input is not an integer
    print("That's not a valid number!")

except ZeroDivisionError:
    # Handles the specific case of division by zero
    print("You can't divide by zero!")

except Exception as e:
    # A catch-all for any other exceptions.
    # It's good practice to be more specific with your exceptions.
    print(f"An unexpected error occurred: {e}")

else:
    # This runs only if NO exception was raised in the try block.
    print("Division performed successfully!")

finally:
    # This code ALWAYS runs, whether there was an exception or not.
    # Perfect for cleanup actions (like closing files).
    print("This is the final cleanup step.")
```
    
# Map filter and reduce 
```python
'''
map, filter, and reduce are higher-order functions in Python (and many other programming languages) that 
operate on iterables (list, tuples, etc). They provide a concise and functional way to perform common 
operations on sequences of data without using explicit loops. 

map always return map object
filter always return filter object
'''

print("############# map an list functions ####################")
my_list = [1,2,3,4,5]
map_obj = map(lambda x: x+1, my_list) # always return map object
list_obj = list(map_obj)
print(list_obj) #[2, 3, 4, 5, 6]

print("############# filter function ####################")
def filter_result(input):
    if input > 9:
        return True
    else:
        return False

source = [1,51, 4,1,5,766,1,22,4,3,1,2,66,5,1,12]
filter_object = filter(filter_result, source)
print(filter_object) # always return filter object
list_object = list(filter_object)
print(list_object) #[51, 766, 22, 66, 12]

print("############# reduce function ####################")
'''
reduce is an application of a given function one by one to all the values of a given list
finally we get a reduced value, and this reduced value is found after there is only a single
value in our initial table, in below this case is 21:
'''
from functools import reduce # reduce is an internal module
my_list = [1, 2, 3, 4, 5, 6]
def sum (x, y):
    return x + y

print(reduce(sum, my_list))
# [1, 2, 3, 4, 5, 6]
# [3, 3, 4, 5, 6]
# [6, 4, 5, 6]
# [10, 5, 6]
# [15, 6]
# [21]
```

# Walrus opreator 
```python
'''
The walrus operator allows you to assign a value to a variable as part of an expression, instead of in a separate line.
In other words, it lets you “assign and return” a value simultaneously.

introduced in Python 3.8.
'''

print("############# case 1 ###################")
# before
import re

text = "Order ID: 12345"
matched = re.search(r"\d+", text)
if matched:
    print("Found order ID:", matched.group())

# after
text = "Order ID: 12345"
if matched := re.search(r"\d+", text):
    print("Found order ID:", matched.group())

print("############# case 2 ###################")
# before
results = []
for n in range(10):
    squared = n * n
    if squared > 20:
        results.append(squared)
        
# How is possible to have one-liner in Python for list?
'''
Python’s list comprehension allows you to combine loops, conditions, and assignments into a single, readable 
expression — especially handy with the walrus operator to avoid recomputing values.


Python’s official grammar for a list comprehension is:
[ expression for target in iterable [if condition] ]

'''
```
# Comprehension in Python (推导)
```
Comprehensions are a concise way to create new sequences (lists, sets, dictionaries, generators) from existing iterables using a single line of code.
They replace longer for-loops and make your code cleaner and more readable.

1. list comprehension
structure:
[new_item for item in iterable if condition]

sample:
abc = ["result is " + str(x) for x in range(1,6) if x % 2 == 0]
print(abc)

result:
['result is 2', 'result is 4']

2. Dictionary comprehension
structure:
{key_expression: value_expression for item in iterable if condition}

sample:
abc = {x: x+1 for x in range(1,6) if x%2==0}
print(abc)

result:
{2: 3, 4: 5}

3. Set comprehension
structure:
{expression for item in iterable if condition}

sample:
abc = ["aa", "ab", "bb", "cc"]
def = {x for x in abc}
print def
```

# Walrus operator
'''
Available in Python 3.8 and later, the walrus operator (:=) allows you to assign values to variables as part of an expression.
'''
def func_a():
    return 10

if (a :=func_a() > 5):
    print(f"a is greater than 5: {a}")

# args
'''
args will be a tuple of all the values passed to the sum function

why need * before args? “This function can accept any number of positional arguments, and I want them packaged together inside a tuple called args.”
'''
def sum(*args):
    print(type(args)) # <class 'tuple'>
    total = 0
    for num in args:
        total += num
    return total
print(sum(1, 2, 3, 4, 5))

# kwargs
'''
kwargs is a dictionary with all the key value pairs which were passed to marks
'''

def marks(**kwargs):
    print(type(kwargs)) # <class 'dict'>
    for key, value in kwargs.items():
        print(f"key is {key} and value is {value}")
    for item in kwargs:
        print(f"key is {item} and value is {kwargs[item]}")  
    for item in kwargs.items():
        print(item)
marks(gerome=1, summer=2, joey=3)

# args + kwargs
def render(*args, **kwargs):
    print(args)
    print(kwargs)

render(1,2,3, gerome=1, summer=2, joey=3)

# Exercises - Decarator
```python3
def logger(func):
    def wrapper():
        print("Function is being called!")
        func()
    return wrapper

@logger
def say_hello():
    print("Hello!")

say_hello()

def timmer(func):
    import time
    def wrapper(*args, **kwargs):
        start_time = time.time()
        result = func(*args, **kwargs)
        end_time = time.time()
        print(f"Function {func.__name__} took {end_time - start_time} seconds to execute.")
        return result
    return wrapper
@timmer
def _sums(n):
    total = 0
    for i in range(1, n + 1):
        total += i
    return total

print(_sums(100000000))
```
# Exercises - Getter and Setter
```python3
class Employee:
    @property
    def salary(self):
        return self.salary
    @salary.setter
    def salary(self, value):
        if value < 0:
            raise ValueError("Salary cannot be nagative value")
        self.salary = value

e1 = Employee()
e1.salary = -1
print(e1.salary)
e2 = Employee()
e2.salary = 5000
print(e2.salary)
```
# Exercises - Class methods and static methods
- A staticmethod is just a normal function placed inside a class for organization, but it cannot access or modify the class or instance.
- A classmethod knows which class called it and can modify class state or create new instances.
```python3
class MathUtils:
    @staticmethod
    def add(a,b):
        return a + b
    @classmethod
    def description(cls): #In a @classmethod, Python automatically passes the class object as the first argument.
        print("This is a utility class for math operations.")

print(MathUtils.add(3, 5))  # Returns 8
MathUtils.description()  # Prints the description
```

# Exercises - Dunder methods
```python3
class Book:
    def __init__(self):
        pass
    @property
    def title(self):
        return self._title
    @title.setter
    def title(self, value):
        self._title = value
    def __str__(self):
        return self._title
    def __len__(self):
        return len(self._title)
b1 = Book()
b1.title = "The Great Gatsby"
print(len(b1))
b2 = Book()
b2.title = "The Great HHHH"
print(len(b2))
```

# Exercisees - map and filter
```python3
list1 = [1,2,3,4,5]
ln1 = lambda x: x*2
print(list(map(ln1, list1))) #[2, 4, 6, 8, 10]

list2 = [10, 11, 12, 13, 14]
ln2 = lambda x: x%2 == 0
print(list(filter(ln2, list2))) #[10, 12, 14]

list3 = [1,2,3]
ln3 = lambda x, y: x*y
from functools import reduce
print(reduce(ln3, list3)) #6
```

# OS Module and shutil Module
# They are builtin modules to build and manage files and directories
import os

# list files and directories in a specified path
```python3
listdir = os.listdir("/Users/gerome/python_course")
print(listdir)
```
# get current path
```python3
print(os.getcwd())
```
# check if a file or directory exists
```python3
print(os.path.exists("/Users/gerome/python_course/main.py"))
```
# os.remove()  # to remove a file; only works for deleting files, not directories
```python3
file_descriptor = os.open("/Users/gerome/python_course/abc.txt", os.O_CREAT | os.O_WRONLY)
os.write(file_descriptor, "Hello".encode())  # create a file
os.close(file_descriptor)
os.remove("/Users/gerome/python_course/abc.txt")
```
# os.rmdir()   # to remove an empty directory
# os.mkdir()   # to create a directory
```python3
os.mkdir("/Users/gerome/python_course/test_dir")
os.rmdir("/Users/gerome/python_course/test_dir")
```
# shutil module is more powerful for file and directory management
```import shutil```
# shutil.rmtree() # to remove a directory and all its contents
```python3
os.mkdir("/Users/gerome/python_course/test_dir")
os.makedirs("/Users/gerome/python_course/test_dir/sub_dir1/sub_dir2")  # to create nested directories
shutil.rmtree("/Users/gerome/python_course/test_dir")  # to remove a directory and all its contents
```
# shutil.copy() # to copy a file
```
os.mkdir("/Users/gerome/python_course/test_dir")
shutil.copy("gerome.txt", "/Users/gerome/python_course/test_dir/gerome_copy.txt")  # to copy a file
print(os.listdir("/Users/gerome/python_course/test_dir"))
```

# shutil.move() # to move a file or directory
```python3
shutil.move("a.txt", "dir1/") # to move a file to a directory
```

# Write and Read file
```python3
with open("notes.txt", "w") as f:
    f.write("Learning Python is fun")

with open("notes.txt", "r") as f:
    content = f.read()
    print(content)
```
# Read line by line
```python3
with open("notes.txt", "r") as f:
    for line in f:
        print(line.strip())
```
# Use os module
```python3
import os
print(os.getcwd())
print(os.listdir())
os.mkdir("new_folder")
```
# Use shutil module to copy file from one folder to another
```python3
import shutil
shutil.copyfile("notes.txt", "notes_copy.txt")
```


# virtual Env and Pip
```pip install virtualenv```

## create venv1
```python3
# -m tells Python to look for a module inside the current environment’s module search path and run it as if it were a script.
python3 -m venv venv1
```

## activate venv1
```source env1/bin/activate```

## pip is Phython's package installer. It's used to install, upgrade and manage external libraries
## Inside venv1, i want to install:
```python3
install requests
install numpy==1.19.5
```

## list all package installed in venv1
```pip list```

## upgrade package
```pip install requests --upgrade```

## uninstall package
```pip uninstall requests```

## deactivate an virtual env
```deactivate```

# requirements.txt
A requirements.txt file lists all the packages your project depends on. This makes it easy to recreate the environment on another machine

## show all packages and versions
```python3
pip freeze
```

## Create the requirements.txt file
```pip freeze > requirements.txt```

## Switch to another virtual env and install all packages listed in requirements.txt
```python3
python3 -m venv venv2
source venv2/bin/activate
pip install -r returnments.txt
```

# API Call
Good doc: https://requests.readthedocs.io/en/latest/user/quickstart/#make-a-request
```pytyon
import requests
r = requests.get('https://api.github.com')
r = requests.post('https://httpbin.org/post', data = {'key':'value'})
r = requests.put('https://httpbin.org/put', data = {'key':'value'})
r = requests.delete('https://httpbin.org/delete')
r = requests.head('https://httpbin.org/get')
r = requests.options('https://httpbin.org/get')
r = requests.patch('https://httpbin.org/patch', data = {'key':'value'})
r = requests.request('GET', 'https://api.github.com')
r = requests.get('https://api.github.com', params = {'key':'value'})    
r = requests.get('https://api.github.com', headers = {'Authorization':'Bearer YOUR_TOKEN'})
r = requests.get('https://api.github.com', timeout = 5)                                 
r = requests.get('https://api.github.com')
print(r.status_code)
print(r.headers['content-type'])
print(r.text)
print(r.json()) 
```

# Regular Expressions in Python - re module
## Find one
```python3
import re
text = "The quick brown fox jumps over the lazy dog."
```
## search for a pattern, if multi matched, return the first one
```python3
match = re.search(r"fox", text)
print(match.start())
print(match.end())
```

## how to use r?
The 'r' before the string indicates a raw string, which tells Python to treat backslashes as literal characters.
- Without raw string (regular string)
```python3
pattern1 = "\section"    # Python interprets \s as a space character
print(pattern1)          # Output: " ection"
```
- With raw string
```
pattern2 = r"\section"   # Python treats \s as literal characters \ and s
print(pattern2)          # Output: "\section"
```

## Find all
```
import re
text = "The quick brown fox jumps over the lazy dog. The fox is clever."
matches = re.findall(r"fox", text, re.IGNORECASE)  # returns ['fox', 'fox']
print(matches)
```
## Replace
```
new_text = re.sub(r"fox", "cat", text)  
print(new_text) # returns "The quick brown cat jumps over the lazy dog. The cat is clever."
```
# Multithreading
```
'''
This allow your pragrams to perform multiple tasks concurrently, improving performance
Multithreading is particularly useful for I/O-bound tasks, such as web scraping, file handling, and network operations.
Multithreading can help keep your application responsive by offloading time-consuming tasks to separate threads.
Multithreading using threading module

CPU Bound tasks are better handled with multiprocessing module
CPU Bound tasks are tasks that require significant CPU resources and processing power, such as complex calculations, data analysis, and image processing.
CPU Bound tasks can benefit from multiprocessing because it allows the program to utilize multiple CPU cores, thereby improving performance and reducing execution time.
CPU Bound tasks are limited by the speed of the CPU, meaning that the performance of these tasks is primarily determined by the processing power of the CPU rather than other factors such as I/O operations or memory access.
CPU Bound tasks can lead to performance bottlenecks if the CPU is overloaded with too many tasks, resulting in slower execution times and reduced responsiveness.
CPU Bound tasks can be optimized by using efficient algorithms, parallel processing, and optimizing code to reduce CPU usage.
COu Bound Prcesses: CPU-bound tasks require heavy computation and keep the processor busy. Examples include mathematical calculations, data processing, and video encoding.

thread.join() - It blocks the current (main) thread until the target thread completes.
'''


import threading
import time
def worker(i):
    """Thread worker function"""
    print("thread {i} is running")
    time.sleep(2)
    print("thread {i} thread is done")

threads = []
for i in range(3):
    thread = threading.Thread(target=worker, args=(i,))
    threads.append(thread)
    thread.start()

for thread in threads:
    thread.join() # It blocks the current (main) thread until the target thread completes. Wait until this exact thread finishes.

print("All threads are done")
```

# Multiprocessing
```
import time
from multiprocessing import Process

def scan(path):
    # run blackduck CLI command for this path
    print(f"blackduck scan {path} start")
    time.sleep(3)
    print(f"blackduck scan {path} end")

if __name__ == "__main__":
    parts = ["src_part1", "src_part2", "src_part3"]
    procs = []

    for p in parts:
        proc = Process(target=scan, args=(p,))
        procs.append(proc)
        proc.start()

    for proc in procs:
        proc.join()
    print("All scans completed.")
```

# Flash

Bootstrap: https://getbootstrap.com/docs/4.0/examples/

```
from flask import Flask, request, render_template, jsonify

app = Flask(__name__, static_folder="assets", static_url_path="/static")

@app.route("/services")
def home():
    return render_template("home.html")

@app.route("/contact")
def contact():
    return render_template("contacts.html")

@app.route("/about")
def about():
    return render_template("about.html")

@app.route("/create", methods=["GET", "POST"])
def create():
    print(request.method)
    return render_template("home.html")

@app.raoute("/query", method=["GET"])
def query():
    name = request.args['name']
    token = request.args['token']
    return render_template("query.html", name, token)

@app.route("/jsonify", method=["GET"])
def test_jsonify():
    """test jsonify"""
    marks = {
        "Gerome": 1,
        "Summer": 2
    }
    return jsonify(marks)
app.run(debug=True, port=9999)
```
More to explore: https://elevenlabs.io/pricing 
