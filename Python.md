# Notes
* REPL (Read, Evaluate, Print, Loop) - Each line is read and evaluated. The return value is then printed to the screen, and then the process repeats.
* MVC = Model: where the business logic exists; View: how information is shown to the end user; Cntroller: glue between Model and View
* POST HTTP - It's for creating a resource in the server, and is occasionally used for updating resources.
* GET HTTP - Requesting a resource from the server
* Starting Python3.7 REPL - By running `python3.7` from the terminal
* Tools to install python packages - Pip and Pipenv
* Creating a doctest method within a class - Add a triple-quoted string a test to the top of the method context.
* Virtualenvs - Sandbox environments that are setup to keep different Python projects' dependencies contained
* How to fetch an environment variables value in Python - os.getenv('SECRET')
* Running a python file from terminal - python3.7 <filename>
* File needed to create an installable Python package - setup.py
* How are dependencies specified in setup.py - By adding the package name to the 'requires' key
* Keywords used to wrap code - tryexcept/else/finally
* method - A function that is defined within the context of an object.
* list - ordered sequence of items that are mutable
* string immutability - When a string is created, it is immutable because it can't be changed once it's assigned
* Steps to install python
  - sudo -i
- yum groupinstall -y "development tools"
- yum install -y \
libffi-devel \
zlib-devel \
bzip2-devel \
openssl-devel \
ncurses-devel \
sqlite-devel \
readline-devel \
tk-devel \
gdbm-devel \
db4-devel \
libpcap-devel \
xz-devel \
expat-devel

- cd /usr/src
- wget http://python.org/ftp/python/3.7.2/Python-3.7.2.tar.xz
- tar xf Python-3.7.2.tar.xz
- cd Python-3.7.2
- ./configure --enable-optimizations
- make altinstall

# Programming tips
* __init__ method - This method overrides the initializer of the class. The initializer is what is used when we create a new version of a class.
* 'with' example
with open('xmen.txt', 'w+') as my_file:
    my_file.write('Beast\n')
    my_file.write('Phoenix\n')
    my_file.writelines([
        'Cyclops\n',
        'Bishop\n',
        'Nightcrawler\n',
         ])

my_file = open('xmen.txt', 'r')
with my_file:
    print(my_file.read())
    print("I'm reading again")
    print(my_file.read())
    
* function format
- The def keyword
- The function name - lowercase starting with a letter or underscore (_)
- Left parenthesis (()
- 0 or more argument names
- Right parenthesis ())
- A colon :
- An indented function body

* map()
Takes in a function and a list of values and returns list with the result of applying the function to each value in the original list.

* Comparison Operators
< - strictly less than
<= - less than or equal
> - strictly greater than
>= - greater than or equal
== - equal
!= - not equal
is - object identity
is not - negated object identity

* Slicing
- Getting values based on position in a list
my_list[0:2] - Gets the first through third values
my_list[1:4] - Gets the 2nd through 5th values.

* Creating dictionaries
 - workers = { ' Benji':'44','Jerry':'55','Johnny':'66'}

- weights = dict(kevin=160, bob=240, kayla=135)

- colors = dict([('kevin', 'blue'), ('bob', 'green'), ('kayla', 'red')])
>>> colors
{'kevin': 'blue', 'bob': 'green', 'kayla': 'red'}

* String methods
.find() - Finds a character in a string
.lower() - Puts string in lowercase
.upper() - Puts string in uppercase

* for example
>>> kids = ['serenity', 'trinity']
>>> for kid in kids:
...     print(kid)
... 
serenity
trinity

* Example function
>>> def contact_card(name, age, car_model):
...     return f"{name} is {age} and drives a {car_model}"
...
>>> contact_card("Keith", 29, "Honda Civic")
'Keith is 29 and drives a Honda Civic'

* If structure
if True:
print("This is true")
elif False:
print("This is not real.")
else:
print("I don't know what's real.")

* open() modes
The file argument is pretty simple, but the mode argument has a variety of options that all work a little differently:

'r' - Opens the file for reading, which is the default mode
'w' - Opens the file for writing, while removing the existing content (truncating the file)
'x' - Opens the file to create it, failing if the file already exists
'a' - Opens the file for writing without truncating, appending any new writes to the end of the file
'b' - Opens the file in binary mode, in which the file expects to write and return bytes objects
't' - Opens the file in text mode, the default mode, where the object expects to write and return strings
'+' - Opens the file for reading and writing

* Comments in python
' # - One line of comment
""" [block of comment] ""

* Stepping
Values based on position in. a list
my_list[::2] - prints every 2nd value from the list
my_list[2] - prints the 2nd value from the list
my_list[::-1] - prints the list in reverse.

* List functions
.len() - Gets the length of a list
.append() - Adds to a list
.remove() - Removes from a list

* Unpacking a tuple
>>> point_3d = (2.0,3.0,4.0)
>>> x, y, z = point_3d
>>> x
2.0
>>> y
3.0
>>> z
4.0
