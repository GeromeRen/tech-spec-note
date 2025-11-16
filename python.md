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

name = '''gerome
is 
good
'''
print(name)

print(name[0])
print(name[-3])
print("------------")
name = 'gerome is good'
print(name[-1])
print(name[-2])
print("------------")
name="gerome ren"
print(name[2:4]) # goes from 2 to 4-1
print(name[2:-1]) # important: size of name is 10, then this is equals to name[2:9]
print(name[2:9])

##################### string methods #####################
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
# convert list to string
print("~".join(["1", "2", "3"])) # "1~2~3"

text="hello123"
print(text.isalpha())
print(text.isalnum())
print(text.isdigit())

##################### fstriging #####################
a = "gerome"
b = "ren"
print(f"hello {a} {b}, how are you!")


##################### function #####################
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

##################### lambda function #####################
'''lambda funtions are anonymous inline functions'''
sum = lambda x, y: x + y
print(sum(1,2)) #3


##################### recursion #####################
'''A function calling itself to resolve problem'''
'''FIBONACCI SERIES 0 1 2 3 5 8 13 ...'''
def fib(n):
    if (n==0 or n==1):
        return n

    return fib(n-2) + fib(n-1)
print(fib(5)) #5

##################### python module #####################
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

##################### variable scope #####################
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



##################### List and List Methods #####################
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

##################### Tuples #####################
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

##################### Sets #####################
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


##################### Dictionary #####################
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


##################### When to use Each Data Structure #####################
'''
Data Structure      Features                            Best For
List                Ordered, Mutable                    Storing sequences, dynamic data
Tuple               Ordered, Immutable                  Fixed collections, dictionary keys
Set                 Unordered, Unique                   Removing duplicates, set operations
Dictionary          Ordered, Key-Value Pairs, Mutable   Fast lookups, structured data
'''

##################### Class #####################
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


##################### Decorators #####################
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

##################### Getters and Setters using Decorators #####################
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
    
    @property
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


##################### Static && Class Methods using staticmethod decarator #####################
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

######################## Dunder Methods (double underscore methods) #####################
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


#################### Exception Handling and Custom Errors #####################
'''
ZeroDivisionError

FileNotFoundError - When you try to open or access a file that doesn't exist.

PermissionError - When you try to perform an operation without the necessary access rights

ValueError - When a function receives an argument of the right type but an inappropriate value.

TypeError - When an operation or function is applied to an object of an inappropriate type.
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
    
    
########################## Map filter and reduce ###################################
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

########################## Walrus opreator ###################################
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


explain comprehension and summary it in python TODO
