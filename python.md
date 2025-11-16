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
