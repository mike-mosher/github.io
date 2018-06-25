# Random Python Snippets:


Strings:
----

Strings can be broken up over multiple lines without backspaces or anything

```Python
>>>my_string = ('This is a super long string const '
                'spread out over multiple lines. '
                'And look, no backslash characters '
                'needed!')
>>> my_string
'This is a super long string const spread out over multiple lines. And look, no backslash characters needed!'
```

Triple Quotes:

```Python
>>>my_string = """
  did you know that you can use triple quotes for multi-line strings as well?
  However, there is a difference in how they are represented.
  See output.
"""
>>> my_string
'\n  did you know that you can use triple quotes for multi-line strings as well?\n  However, there is a difference in how they are represented.\n  See output.\n'
```

Joining and Splitting Strings:

```Python
>>> l = ['server=mpilgrim', 'uid=sa', 'database=master', 'pwd=secret']
>>> l
['server=mpilgrim', 'uid=sa', 'database=master', 'pwd=secret']
>>> s = ";".join(l)     # 'server=mpilgrim;uid=sa;database=master;pwd=secret'
>>> s
'server=mpilgrim;uid=sa;database=master;pwd=secret'
>>> s.split(";")        # ['server=mpilgrim', 'uid=sa', 'database=master', 'pwd=secret']
['server=mpilgrim', 'uid=sa', 'database=master', 'pwd=secret']
>>>
>>>
>>>l = ['This', 'is', 'how', 'you', 'join']
>>>' '.join(l)
'This is how you join'
```

Get Subset of a String:
```Python
"Hello World"[:5]       # 'Hello'
```


String Methods:

strip():
```Python
# Use this to remove leading and trailing whitespace
s = ' Hello World '
s.strip()
#'Hello World'
```

replace():
```Python
# use this to remove all spaces
s = ' Hello World'
s.replace()
# 'HelloWorld'
```

split():
```Python
# use this to split the string up into a list of items
s = 'Hello World'
s.split()
# ['Hello', 'World']


# can also do this to remove duplicates ;)
s = ' Hello   World'
" ".join(s.split())
# 'Hello World'
```



String Formatting:

Old Style:

```Python
>>> 'This is a %s and this is a number/integer: %i' % ('string', 17)
'This is a string and this is a number/integer: 17'
```

New Style:
  - https://docs.python.org/3/library/string.html#string-formatting
  - Introduced in Python 3, and is prefered over the old style (even though the old style is still allowed)

```Python
>>>'This is a {} and this is a number/integer: {}'.format('string', 17)
'This is a string and this is a number/integer: 17'
>>>
>>>'This is a {0} and this is a number/integer: {1}'.format('string', 17)
'This is a string and this is a number/integer: 17'
>>>
>>>'This is a {1} and this is a number/integer: {0}'.format(17, 'string')
'This is a string and this is a number/integer: 17'
>>>
>>>'This is a {string} and this is a number/integer: {number}'.format(string='string', nu
mber=17)
'This is a string and this is a number/integer: 17'
```

New New Style (Python 3.6+):
  - Literal String Interpolation or Formatted String Literals

```Python
>>> string = 'string'
>>> number = 17
>>> f'This is a {string} and this is a number/integer: {number}'
'This is a string and this is a number/integer: 17'
>>>
>>> a = 5
>>> b = 10
>>> f'five plus 10 is {a + b} and not {2 * (a + b)}'
'five plus 10 is 15 and not 30'
```

Diff between String Concatenation and String Interpolation:
----

String Concatenation:

```Python
>>> name = 'Mike'
>>> age = 37
>>>
>>> greeting = 'My name is ' + name + ' and I am ' + age + ' years old'
```

String Interpolation:

```Python
>>> name = 'Mike'
>>> age = 37
>>>
>>> greeting = 'My name is {} and I am {} years old'.format(name, age)
```


Pretty Printing Stuff:
----

you can use json.dumps():

```Python
import json

>>> d
{'id': 1, 'name': 'Leanne Graham', 'username': 'Bret', 'email': 'Sincere@april.biz', 'address': {'street': 'Kulas Light', 'suite': 'Apt. 556', 'city': 'Gwenborough', 'zipcode': '92998-3874', 'geo': {'lat': '-37.3159', 'lng': '81.1496'}}, 'phone': '1-770-736-8031 x56442', 'website': 'hildegard.org', 'company': {'name': 'Romaguera-Crona', 'catchPhrase': 'Multi-layered client-server neural-net', 'bs': 'harness real-time e-markets'}}
>>>
>>> print(json.dumps(d, indent=4))
{
    "id": 1,
    "name": "Leanne Graham",
    "username": "Bret",
    "email": "Sincere@april.biz",
    "address": {
        "street": "Kulas Light",
        "suite": "Apt. 556",
        "city": "Gwenborough",
        "zipcode": "92998-3874",
        "geo": {
            "lat": "-37.3159",
            "lng": "81.1496"
        }
    },
    "phone": "1-770-736-8031 x56442",
    "website": "hildegard.org",
    "company": {
        "name": "Romaguera-Crona",
        "catchPhrase": "Multi-layered client-server neural-net",
        "bs": "harness real-time e-markets"
    }
}
>>>
```

Or better yet, use pprint!:

```Python
>>> from pprint import pprint
>>>
>>> d
{'id': 1, 'name': 'Leanne Graham', 'username': 'Bret', 'email': 'Sincere@april.biz', 'address': {'street': 'Kulas Light', 'suite': 'Apt. 556', 'city': 'Gwenborough', 'zipcode': '92998-3874', 'geo': {'lat': '-37.3159', 'lng': '81.1496'}}, 'phone': '1-770-736-8031 x56442', 'website': 'hildegard.org', 'company': {'name': 'Romaguera-Crona', 'catchPhrase': 'Multi-layered client-server neural-net', 'bs': 'harness real-time e-markets'}}
>>>
>>> pprint(d)
{'address': {'city': 'Gwenborough',
             'geo': {'lat': '-37.3159', 'lng': '81.1496'},
             'street': 'Kulas Light',
             'suite': 'Apt. 556',
             'zipcode': '92998-3874'},
 'company': {'bs': 'harness real-time e-markets',
             'catchPhrase': 'Multi-layered client-server neural-net',
             'name': 'Romaguera-Crona'},
 'email': 'Sincere@april.biz',
 'id': 1,
 'name': 'Leanne Graham',
 'phone': '1-770-736-8031 x56442',
 'username': 'Bret',
 'website': 'hildegard.org'}
>>>
```

Note: It's important to remember to use 'from pprint import pprint'. If you just use 'import pprint', then you have to run: `pprint.pprint(d)`



The Low-Down on Datatypes:
----

List:
  - mutable
  - ordered

Dict:
  - mutable (values)
    - Keys are unique and immutable
  - unordered
    - if an ordered dict is needed, then "from collections import OrderedDict"

Set:
  - mutable
  - unordered

Tuple:
  - immutable
  - ordered
  - examples: days of the week, months of the year, any other list you want to hold and not change


Cheatsheet:

  | Data Type | Mutable? | Ordered? | Index-based?   |
  |---------|------------|----------|----------------|
  | List:   | yes        | yes      | yes            |
  | Tuple:  | no         | yes      | yes            |
  | Dict:   | (values)   | no       | no (key/value) |
  | Set:    | yes        | no       | yes            |


Lists:
----

Create:

```Python
l = []
l = list()

A = []; B = []  # independent lists

A = B = []      # both names will point to the same list

A = []
B = A           # both names will point to the same list
```

Adding items to lists:

```Python
l.append(x)                     # add to end of list
l.insert(2, x)                  # add item to index 2 of list (3rd item)
l.extend(["new", "elements"])   # concat this list to the end of l

# -- difference between append and extend:
l = ["a", "b", "c"]
l.append(["d", "e", "f"])       # ["a", "b", "c" ["d", "e", "f"] ]
l.extend(["d", "e", "f"])       # ["a", "b", "c", "d", "e", "f"]
```

Access list items:

```Python
l = ['a', 'b', 'new', 'mpilgrim', 'z', 'example', 'new', 'two', 'elements']
l[5]                  # 'elements'
l.index("elements")   # 5

l[index]              # access item at index
l[i:j]                # returns a new list, containing the objects between i and j.
l[-1]                 # access last item in list
l[:]                  # shorthand to return the full list

l[start:stop:step]
l[::2] # get every other item, starting with the first
```

Searching items in list:

```Python
if value in L:
  print "list contains", value
```          

Deleting items in a list:

```Python
del L[i]
del L[i:j]
item = L.pop() # last item
item = L.pop(0) # first item
item = L.pop(index)
L.remove(item)
```

Copy items from a list:

```Python
a = [1, 2, 3, 4, 5]

# shallow copy
b = a[:]

# copy by type casting
b = list(a)

#Python 3 only
b = list.copy()
```


Methods:

```Python
list.index(x)       # get index of first matching item
list.count(x)       # number of x items
list.sort()
list.reverse()
```


Notes:
  - If you have multiple variables pointing to a list, then updating it updates both variables
  - to avoid this:

```Python
  L = []
  M = L[:] # create a copy

  # modify L only
  L.append(obj)
```


Dictionaries:
----

Create a dictionary:
```Python
d = {}
d = {"name": "Mike", "Age": 7}
```


Access items:
```Python
d["name"]
d.get("name")
```

***
this is freaking awesome:
***

Get an item from a dic, but provide a default value if the provided key doesn't match:

```Python
d = { 'key1' : 'val1', 'key2' : 'val2', 'key3' : 'val3' }

print(d.get('key4', 'default'))

# Output: default
```


Adding / Updating items:
```Python
d["city"] = "Bayfield"
```

Deleting items:
```Python
del d["city"]
dict.clear();         # remove all entries in dict
```

Loop over dicts:
```Python
for k in d:               # get keys in dict
  print k

for k,v in d.items():     # get key, value of dict
  print k,v

for v in d.values():      # get values in dict
  print v
```

Methods:

```Python
d.has_key(key)      # returns true if key exists
d.items()           # returns key, value tuples as a list
d.keys()            # returns list of keys
d.values()          # returns list of values
```


Sets:
----

Create a Set:
```Python
s = set()                       # creates empty set
s = {}                          # This does not work.  This creates an empty dictionary
s = {1,2,3,4,5}
l = [1,2,3,4,5]; s = set(l)     # create a set from a list
```

Add to a Set:
```Python
s.add("test")
```

Remove from a Set:
```Python
s.discard("test")
```



Tuples:
----

Create a Tuple:
```Python
t = ()          # empty tuple
t = 'test',     # tuple with one item (note the comma)
t = ('test',)
t = ('test1', 'test2', 3)
```

Methods:
  - Tuples have no methods (because they are immutable)



Advanced Variables:
----

Underscores and Double Underscores (Dunders):

```Python
Single Leading Underscore: _var
Double Trailing Underscore: var_
Double Leading Underscore: __var
Double Leading and Trailing Underscore: __var__
Single Understore: _

_var = ('Single underscores are a Python naming convention that '
        'indicates a name is meant for internal use.  It is generally '
        'not enforced by the interpreter and is only meant as a hint '
        'to the programmer')

var_ = ('used to assign a variable that is already reserved in Python, '
        'and this method can be used to break the naming conflict. '
        'Example: def and class are reserved in the language. '
        'def_ and class_ can be used instead')

__var = ('A double underscore prefix causes the Python interpreter to '
        'rewrite the attribute name in order to naming conflicts '
        'in the subclass')

__var__ = ('reserved for special use in the language, like __init__')

_ = ('Used as a convention to signal that the variable is temporary '
     'or insignificant.  See example below.  This var name is valid, but it's'
     'used as a throwaway most times.')

# _ example
for _ in range(5):
  print("Hello World!")

_ = ('This is also used in most REPLs (interpreters) as the result of the last '
     'calculation.  See example below')

# _ in a REPL
>>> 20 + 3
23
>>> _
23
>>> print(_)
23

```


IF Statements:
----

```Python
if condition_1:
    statement_block_1
elif condition_2:
    statement_block_2
else:
    statement_block_3
```

Abbreviated if:

```Python
x if condition else y;
```

Ternary if:
```Python
# The first is a fairly standard teranary style;
# <value if true> if <conditional> else <value if false>

print ('passed') if x else print('did not pass')

```




Loops:
----

```Python
    for loops:
        1)
        for iterating_var in sequence:
            statements

        2)
        for iterating_var in sequence: statements

        3)
        # else statement is run after iterating the entire sequense
        for iterating_var in sequence:
            statements
        else:
            statements

        4)
        # An alternative way of iterating through each item is by index offset into the sequence itself
        fruits = ['banana', 'apple',  'mango']
        for index in range(len(fruits)):
            print 'Current fruit :', fruits[index]



    while loops:
        1)
        while expression:
            statement

        2)
        while expression: statment

        3)      # else statement is run after the while loop finishes
        while expression:
            statement
        else:
            statement

```


Operators:
----

Relational Operators:
  - Relational operators compares the values. It either returns True or False according to the condition.

  | Operator  | Example     | Meaning  | Result         |
  |-----------|-------------|----------|----------------|
  | ==	      | a ==        | Equal to	                  | True if the value of a is equal to the value of b; False otherwise |
  | !=        | a != b	    | Not Equal to	              | True if a is not equal to b; False otherwise |
  | <	        | a < b	      | Less than	                  | True if a is less than b; False otherwise |
  | <=        | a <= b	    | Less than or equal to       | True if a is less than or equal to b; False otherwise |
  | >	        | a > b	      | Greater than                | True if a is greater than b; False otherwise |
  | >=        | a >= b	    | Greater than or equal to    | True if a is greater than or equal to b; False otherwise |


Logical Operators:
  - used to combine expressions and test 'truthy'ness


  | Operator  | Example     | Result         |
  |-----------|-------------|----------------|
  | not       | not x       | True if x is False; False if x is True; (Logically reverses the sense of x) |
  | or        | x or y      | True if either x or y is True; False otherwise |
  | and       | x and y     | True if both x and y are True; False otherwise |

Bitwise Operators:
  - Bitwise operators acts on bits and performs bit by bit operation.
  - They operate on numbers (normally), but instead of treating that number as if it were a single value, they treat it as if it were a string of bits, written in binary.


  | Operator    | Syntax            | Desc        |
  |-------------|-------------------|-------------|
  | &           | x & y             | Bitwise AND |
  | *backslash* | x *backslash* y   | Bitwise OR  |
  | ~           | ~x                | Bitwise NOT |
  | ^           | x ^ y             | Bitwise XOR |


Assignment Operators:
  - Assignment operators are used to assign values to the variables


  | Operator    | Syntax            |
  |-------------|-------------------|
  | =           | x + y = z         |
  | +=          | a += b; a = a + b |
  | -=          | a -= b; a = a - b |
  | *star*=     | a *star*= b       |
  | /=          | a /= b; a = a / b |


Difference between 'and' and '&':
  - 'and' is a logical operator (used to combine expressions and test truthyness)
  - '&' is a bitwise operator (used to do binary comparisons)



Knowing when something is True or False:

  - Items considered False:
    - Boolean value 'False'
    - Any value that is numerically zero (0, 0.0, 0.0j)
    - An empty string
    - An empty object ([], {}, etc)
    - 'None' object

  - Items considered true:
    - Virtually any other object built into Python is regarded as True.




Testing Flags and Vars:
----

Check if var exists:

```Python
try:
    x
except NameError:
    x_exists = False
else:
    x_exists = True
```


Check if var is true:
  - See previous section called 'Knowing when something is True or False'

```Python
>>> a = 0
>>> b = 1
>>> c = 'exists'
>>>
>>> if a:
...     print(a)
>>> if b:
...     print(b)
1
>>> if c:
...     print(c)
exists
>>>
```

Check if a var is false:

```Python
if not var:
  print('var is false')
```

When a var is false:
  - See previous section 'Knowing when something is True or False'


How not to check if a var is empty:

```Python
# Good
if not x:     # Works for strings, lists, dicts, sets, and tuples. Strings evaluate to False if they are empty.


# Bad
if foo == "":

# "" is a magical value. You should never check against magical values (more commonly known as magical numbers)
```


Ternary if to check if something is true:

```Python
# The first is a fairly standard ternary style;
# <value if true> if <conditional> else <value if false>

print ('passed') if x else print('did not pass')

```


Using the 'OR' logical operator:
  - if the first value is 'truthy', then it returns the first value and moves on / doesn't analyze the second
  - if the first value is 'falsy', then it returns the second value, no matter what it is, and moves on / doesn't analyze the second value
  - This is called the lazy OR
  - When to use this:
    - if statements: `if x or y:`
    - return statements in functions:
      `def greater_than_ten(num): return (num > 10) or False`

```Python
# Examples:

>>> x = 3
>>> y = 4
>>> x or y
3
>>> y or x
4
>>>
>>> bool(x or y)
True
>>> bool(y or x)
True
>>>
>>>
>>> x = 0.0
>>> y = 4.4
>>> x or y
4.4
>>> y or x
4.4
>>>
>>> bool(y or x)
True
>>> bool(x or y)
True
>>>
>>>
>>>
>>> x = True
>>> y = False
>>>
>>> if x or y:
...     print('True')
... else:
...     print('False')
True
>>> if y or x:
...     print('True')
... else:
...     print('False')
True
>>>
>>>
>>>
>>> def greater_than_ten(num):
...     return (num > 10) or False
>>>
>>>
>>> greater_than_ten(11)
True
>>> greater_than_ten(9)
False
>>>

# Note: the function above could also be written like the following (but used the above as an example)
>>> def greater_than_ten(num):
...     return num > 10
>>>
```


Setting a default value for a variable using the 'OR' logical operand:

```Python
# One thing we can do from this is set a default value in a variable

>>> x = 0
>>> y = 2
>>>
>>> a = x or 'default'
>>> b = y or 'default'
>>> a
'default'
>>> b
2
>>>
>>>
>>> l = []
>>> l.append(x or 'default')
>>> l.append(y or 'default')
>>> l
['default', 2]
>>>
```



Using the 'AND' logical operator:
  - if the first value is 'truthy', then it returns the second value and moves on / doesn't analyze the second
  - if the first value is 'falsy', then it returns the first value and moves on / doesn't analyze the second value
  - This is the exact opposite of the 'OR' logical operator
  - One way to think about this:
    - both need to be true for the overall `x and y` statement to be true
    - if the first if falsy, there is no way that the overall statement can be true, so it returns the first value and doesn't move forward
    - if the first if true, then the second value can only evaluate to truthy or falsy, so it doesn't need to explicity analyze it, just return the second value

```Python
# Example:

>>> x = 3
>>> y = 4
>>> x and y
4

>>> x = 0.0
>>> y = 4.4
>>> x and y
0.0
>>>
>>>
>>>
>>> x = 0
>>> y = 2
>>>
>>> x and y
0
>>> y and x
0
>>> bool(x and y)
False
>>> bool(y and x)
False
>>>
>>>
>>> x = 1
>>> y = 2
>>>
>>> x and y
2
>>> y and x
1
>>>
>>> bool(x and y)
True
>>> bool(y and x)
True
>>>
```










Comprehensions:
----

list comprehension:

```Python
l = [mapping-expression for element in source-list]
```
list comprehension that filters on condition:

```Python
l = [mapping-expression for element in source-list if filter-expression]
```




checking if dict key exists:
----

How not to do it:

```Python
d = {'key1' : 'val1', 'key2' : 'val2', 'key3' : 'val3'}

if not d['key4']:
  print('not in d')

# This is will result in the following KeyError:
Traceback (most recent call last):
  File "<input>", line 1, in <module>
    if not d['key4']:
KeyError: 'key4'
```


How to do it:

```Python
d = {'key1' : 'val1', 'key2' : 'val2', 'key3' : 'val3'}

if 'key4' not d:
  print('not in d')
```

Newer, cooler way of doing it with setdefault():

```Python
d = {'key1' : 'val1', 'key2' : 'val2', 'key3' : 'val3'}

# If the key does not exist, then setdefault() creates it and sets it to the value specified in the second argument.

d.setdefault('key3', 'wrongVal3')   # Since 'key3' exists, it will not set the value passed
d.setdefault('key4', 'val4')        # Since 'key4' doesn't exist, it will create and set value passed in second argument
print(d)
# {'key1': 'val1', 'key2': 'val2', 'key3': 'val3', 'key4': 'val4'}

```


Remove Dups from List:
----

```Python
items = [2, 2, 3, 3, 1]

newitems2 = list(set(items))
```


Set Global Variables programatically:

```Python
d = {'a': 1, 'b': 'var2', 'c': [1, 2, 3]}
globals().update(d)
```

Pytonic way of value swapping:

```Python
"""pythonic way of value swapping"""
a, b = 5, 10

a, b = b, a
```



Reading Files:
----
Code to read files

```Python

###
### Read from csv file
###

# Sample from csv file
caseId,version,mentee,mentorApproval,mentor,dateCreated,dateModified
4918232321,5,royga,Approved,devired,8-Mar,8-Mar
4869165861,3,royga,Approved,fajulugb,9-Feb,9-Feb

# Code
with open(file) as f:
    reader = csv.DictReader(f)
    for row in reader:
      print(row['caseId'], row['mentee'], row['mentor'])



###
### Read from text file
###

# Sample from csv file
This is a test
Line 2

# Code
with open('test.txt') as f:
    print(f.read())         # Reads whole file at once

# Output
This is a test
Line 2


###
# Read each line of a file
###

SOME_LARGE_FILE = 'caps.txt'

with open(SOME_LARGE_FILE) as f:
    for i in f:             # Reads each line individually
        print(i)

```


HTTP Requests:
----

Basic example:

```Python
import requests

response = requests.get('http://www.amazon.com')

print(response.status_code)
print(response.headers)
```

Disable SSL Certificate Verification:

```Python
requests.get(url, verify=False)
```



Kerberos:
----

How to do Kerberos auth to internal websites:
````Python
import requests
from requests_kerberos import HTTPKerberosAuth, OPTIONAL

url = 'https://w.amazon.com'

kerberos_auth = HTTPKerberosAuth(mutual_authentication=OPTIONAL, sanitize_mutual_error_response=False)
r = requests.get(url, auth=kerberos_auth, verify=False)


print(r.status_code)   # 200 OK

````

A more complex example of requests, using query string parameters, headers, and ssl verification turned off:
```Python
# Wiki API
url = 'https://share.amazon.com/sites/ps/Networking/NHO/Lists/Mentee%20Case%20Review/PersonalViews.aspx'

# Setup kerberos request to wiki
kerberos_auth = HTTPKerberosAuth(mutual_authentication=OPTIONAL, sanitize_mutual_error_response=False)

# Set query parameters
params = {}
params['PageView'] = "Personal"
params['ShowWebPart'] = "{406E2538-EB04-4223-B2E8-C995B8319A2A}"
params['AjaxDelta'] = "1"

# Set headers to send to wiki
headers = {}
# headers['Accept'] = "*/*"
# headers['Accept-Encoding'] = "gzip, deflate, br"
# headers['Accept-Language'] = "en-US,en;q=0.9"
# headers['Cache-Control'] = "no-cache"
# headers['Connection'] = "keep-alive"
# headers['Content-Type'] = "applicatoin/x-www-form-urlencoded; charset=utf-8"
# headers['Referer'] = 'https://share.amazon.com/sites/ps/Networking/NHO/_layouts/15/start.aspx'
# headers['DNT'] = "1"
# headers['Pragma'] = "SharePointAjaxDelta=|SITES|PS|NETWORKING|NHO:|SITES|PS|NETWORKING|NHO|_CATALOGS|MASTERPAGE|SEATTLE.MASTER:3.16.0.0.0.16.0.4522.1000.0.FALSE...BUNDLE=TRUE.FLAGS=01.TAG=0:en-US:en-US:RW"
# headers['X-SharePoint'] = "SharePointAjaxDelta=|SITES|PS|NETWORKING|NHO:|SITES|PS|NETWORKING|NHO|_CATALOGS|MASTERPAGE|SEATTLE.MASTER:3.16.0.0.0.16.0.4522.1000.0.FALSE...BUNDLE=TRUE.FLAGS=01.TAG=0:en-US:en-US:RW"
# headers['X-Requested-With'] = "XMLHttpRequest"
headers['User-Agent'] = "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_12_6) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36"     # This seems to be the only header that SharePoint cares about.  Doesn't like to see a User-Agent of 'python-requests/2.18.4'


# Let's call the API and get the response
r = requests.get(url, auth=kerberos_auth, headers=headers, params=params, verify=False)
```


Regex:
----


```Python
import re

text = 'something here'

#basic search
match = re.search(r'something', text)

match.group(0)  # 'something'
```

```Python
# more complex example
text = 'var stuff = "other stuff in the text";var WPQ2ListData = something I actually want to grep;var WPQ2SchemaData = "other stuff"'

match = re.search(r'(var WPQ2ListData = )(.*)(;var WPQ2SchemaData)', text, re.DOTALL)

match.group(0)    # 'var WPQ2ListData = something I actually want to grep;var WPQ2SchemaData'
match.group(1)    # 'var WPQ2ListData = '
match.group(2)    # 'something I actually want to grep'
match.group(3)    # ';var WPQ2SchemaData'

```


JSON:
----

dump:
 - Used to write data to a file (deserialization)
dumps:
 - Used to deserialize data to a string

load:
 - Used to convert (serialize) data from a file into a json object (or dict in Python)
loads:
 - Used to convert (serialize) a string into a json object (or dict in Python)



json.loads():

converts a string to a dict:

 ```Python
import json

s = '{"test": "value"}'

d = json.loads(s)

print(type(d))    # dict
print(d)          # {'test': 'value'}

 ```

Get JSON data from URL with requests:

```Python
import json

r = requests.get('https://jsonplaceholder.typicode.com/todos')

# Two ways of doing this.

# The long way
a = json.loads(r.text)

# The short way
b = r.json()
```




Logging:
----

Below is code that lets you log to a specified log file (change 'logfile.log') and to the console

```Python
import logging

# set up logging to file
logging.basicConfig(level=logging.DEBUG,
                    format='%(asctime)s %(name)-12s %(levelname)-8s %(message)s',
                    datefmt='%m-%d %H:%M',
                    filename='logfile.log',
                    filemode='w')

# define a Handler which writes INFO messages or higher to the sys.stderr
console = logging.StreamHandler()
console.setLevel(logging.INFO)

# set a format which is simpler for console use
formatter = logging.Formatter('%(name)-12s: %(levelname)-8s %(message)s')

# tell the handler to use this format
console.setFormatter(formatter)

# add the handler to the root logger
logging.getLogger('').addHandler(console)

# This is how we log to console and to log file
logging.info('This is a log message')

```



Most common elements in an iterable:
------------------------------------

```Python
# collections.Counter lets you find the most common
# elements in an iterable:

>>> import collections
>>> c = collections.Counter('helloworld')

>>> c
Counter({'l': 3, 'o': 2, 'e': 1, 'd': 1, 'h': 1, 'r': 1, 'w': 1})

>>> c.most_common(3)
[('l', 3), ('o', 2), ('e', 1)]
```


Permutations:
------------

```Python
# itertools.permutations() generates permutations
# for an iterable. Time to brute-force those passwords ;-)

>>> import itertools
>>> for p in itertools.permutations('ABCD'):
...     print(p)

('A', 'B', 'C', 'D')
('A', 'B', 'D', 'C')
('A', 'C', 'B', 'D')
('A', 'C', 'D', 'B')
('A', 'D', 'B', 'C')
('A', 'D', 'C', 'B')
('B', 'A', 'C', 'D')
('B', 'A', 'D', 'C')
('B', 'C', 'A', 'D')
('B', 'C', 'D', 'A')
('B', 'D', 'A', 'C')
('B', 'D', 'C', 'A')
('C', 'A', 'B', 'D')
('C', 'A', 'D', 'B')
('C', 'B', 'A', 'D')
('C', 'B', 'D', 'A')
('C', 'D', 'A', 'B')
('C', 'D', 'B', 'A')
('D', 'A', 'B', 'C')
('D', 'A', 'C', 'B')
('D', 'B', 'A', 'C')
('D', 'B', 'C', 'A')
('D', 'C', 'A', 'B')
('D', 'C', 'B', 'A')
```


Variable Unpacking:
-------------------
- A way to assign valuees to multiple variables at one time, say from a list

enumerate unpacks two items (index and item), and the following example is how to unpack in a for loop:

```Python
for index, item in enumerate(some_list):
    # do something with index and item
```

Variable swap can be an example of unpacking:

```Python
a, b = b, a
```


Nested unpacking works as well:

```Python
>>> v = 1
>>> l = [2,3]
>>>
>>> a, (b, c) = v, l
>>> a
1
>>> b
2
>>> c
3
>>>
```

Python 3 has an new form of extended unpacking:

```Python
a, *rest = [1, 2, 3]
# a = 1, rest = [2, 3]

a, *middle, c = [1, 2, 3, 4]
# a = 1, middle = [2, 3], c = 4
```

Use a throwaway variable when unpacking:

```Python
>>> filename = 'foobar.txt'
>>> basename, __, ext = filename.rpartition('.')
>>> basename
'foobar'
>>> __
'.'
>>> ext
'txt'
>>>
```
