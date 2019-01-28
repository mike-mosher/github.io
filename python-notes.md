# Random Python Snippets

## Naming Things

Three ways to name a multi-word variable:

- Camel Case: `distanceToNearestTown`
- Pascal Case: `DistanceToNearestTown`
- Snake Case: `distance_to_nearest_town`

Which way is the best?

- PEP8 recommends Snake Case
- https://www.python.org/dev/peps/pep-0008/

## Strings

Strings can be broken up over multiple lines without backspaces or anything

```python
>>>my_string = ('This is a super long string const '
                'spread out over multiple lines. '
                'And look, no backslash characters '
                'needed!')
>>> my_string
'This is a super long string const spread out over multiple lines. And look, no backslash characters needed!'
```

Triple Quotes:

```python
>>>my_string = """
  did you know that you can use triple quotes for multi-line strings as well?
  However, there is a difference in how they are represented.
  See output.
"""
>>> my_string
'\n  did you know that you can use triple quotes for multi-line strings as well?\n  However, there is a difference in how they are represented.\n  See output.\n'
```

Joining and Splitting Strings:

```python
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

```python
"Hello World"[:5]       # 'Hello'
```

String Methods:

strip():

```python
# Use this to remove leading and trailing whitespace
s = ' Hello World '
s.strip()
#'Hello World'
```

replace():

```python
# use this to remove all spaces
s = ' Hello World'
s.replace()
# 'HelloWorld'
```

split():

```python
# use this to split the string up into a list of items
s = 'Hello World'
s.split()
# ['Hello', 'World']


# can also do this to remove duplicates ;)
s = ' Hello   World'
" ".join(s.split())
# 'Hello World'
```

s.title():

```python
# converts string to 'Title' case
>>> 'the sun also rises'.title()
'The Sun Also Rises'
```

Right / Left / Center Justify:

- rjust, ljust, center
- example:

```python
>>> a = 'this is a long text that I will use as the longest'
>>> b = 'slightly shorter string.  medium'
>>> c = 'very short'
>>> width = len(max([a,b,c], key=len)) + 20
>>>
>>> for i in [a,b,c]:
...     print('\'' + i.rjust(width) + '\'')
...
'                    this is a long text that I will use as the longest'
'                                      slightly shorter string.  medium'
'                                                            very short'
```

String Formatting:

Old Style:

```python
>>> 'This is a %s and this is a number/integer: %i' % ('string', 17)
'This is a string and this is a number/integer: 17'
```

New Style:

- https://docs.python.org/3/library/string.html#string-formatting
- Introduced in Python 3, and is prefered over the old style (even though the old style is still allowed)

```python
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

```python
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

## Diff between String Concatenation and String Interpolation

String Concatenation:

```python
>>> name = 'Mike'
>>> age = 37
>>>
>>> greeting = 'My name is ' + name + ' and I am ' + age + ' years old'
```

String Interpolation:

```python
>>> name = 'Mike'
>>> age = 37
>>>
>>> greeting = 'My name is {} and I am {} years old'.format(name, age)
```

## Printing

One cool trick with printing

- How to print out a string with no new line

```python
# use the named argument "end" to explicitly specify the end of line string
print("Hello World!", end = '')
print("My name is Karim")
# output:
# Hello World!My name is Karim
```

## Multi-Line Comments

- two ways:
  - block out each line with `#`

```python
# This is a "block comment" in Python, made
# out of several single-line comments.
# Pretty great, eh?
answer = 42
```

- Use a multi-line string with `"""`

```python
"""
This is a "block comment" in Python, made
out of a mult-line string constant.
This actually works quite well!
"""
answer = 42
```

- Note: This actually isn't technically a comment, but actually makes a multi-line string.  However, it's never accessed, so when Python is compiled, this string isn't referenced

## Printing Stuff

```python
>>> print('test')
test
# Custom return carriage
>>> print('specify', 'a', 'custom', 'return', 'carriage', end='\n\n\n')
specify a custom return carriage


>>> 
>>> print('specify', 'an', 'empty', 'return', 'carriage', end='')
specify an empty return carriage>>>
>>>
# Custom separator
>>> print('multiple', 'words', 'separated', 'by', 'space', 'by', 'default')
multiple words separated by space by default
>>> print('multiple', 'words', 'separated', 'by', 'custom', 'separator', sep='-')
multiple-words-separated-by-custom-separator
>>> 
# Printing to file
>>> with open('file.txt', 'w') as f:
...     print('print to file', file=f)
...     
>>>
```

## Pretty Printing Stuff

you can use json.dumps():

```python
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

```python
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

## The Low-Down on Datatypes

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

  | Data Type | Mutable?   | Ordered? | Index-based?   |
  |-----------|------------|----------|----------------|
  | List:     | yes        | yes      | yes            |
  | Tuple:    | no         | yes      | yes            |
  | Dict:     | (values)   | no       | no (key/value) |
  | Set:      | yes        | no       | yes            |

## Lists

Create:

```python
l = []
l = list()

A = []; B = []  # independent lists

A = B = []      # both names will point to the same list

A = []
B = A           # both names will point to the same list
```

Adding items to lists:

```python
l.append(x)                     # add to end of list
l.insert(2, x)                  # add item to index 2 of list (3rd item)
l.extend(["new", "elements"])   # concat this list to the end of l

# -- difference between append and extend:
l = ["a", "b", "c"]
l.append(["d", "e", "f"])       # ["a", "b", "c" ["d", "e", "f"] ]
l.extend(["d", "e", "f"])       # ["a", "b", "c", "d", "e", "f"]
```

Adding multiple list values:

- `a[m:n] = <iterable>`

```python
>>> a = ['foo', 'bar', 'baz', 'qux', 'quux', 'corge']

>>> a[1:4]
['bar', 'baz', 'qux']
>>> a[1:4] = [1.1, 2.2, 3.3, 4.4, 5.5]
>>> a
['foo', 1.1, 2.2, 3.3, 4.4, 5.5, 'quux', 'corge']
>>> a[1:6]
[1.1, 2.2, 3.3, 4.4, 5.5]
>>> a[1:6] = ['Bark!']
>>> a
['foo', 'Bark!', 'quux', 'corge']
```

- The number of elements inserted need not be equal to the number replaced. Python just grows or shrinks the list as needed.
- You can insert multiple elements in place of a single element—just use a slice that denotes only one element:

```python
>>> a = [1, 2, 3]
>>> a[1:2] = [2.1, 2.2, 2.3]
>>> a
[1, 2.1, 2.2, 2.3, 3]
```

- You can also insert elements into a list without removing anything. Simply specify a slice of the form [n:n] (a zero-length slice) at the desired index:

```python
>>> a = [1, 2, 7, 8]
>>> a[2:2] = [3, 4, 5, 6]
>>> a
[1, 2, 3, 4, 5, 6, 7, 8]
```

- You can delete multiple elements out of the middle of a list by assigning the appropriate slice to an empty list. You can also use the del statement with the same slice:

```python
>>> a = ['foo', 'bar', 'baz', 'qux', 'quux', 'corge']
>>> a[1:5] = []
>>> a
['foo', 'corge']

>>> a = ['foo', 'bar', 'baz', 'qux', 'quux', 'corge']
>>> del a[1:5]
>>> a
['foo', 'corge']
```

Prepending or Appending Items to a List:

- Additional items can be added to the start or end of a list using the + concatenation operator or the += augmented assignment operator:

```python
>>> a = ['foo', 'bar', 'baz', 'qux', 'quux', 'corge']

>>> a += ['grault', 'garply']
>>> a
['foo', 'bar', 'baz', 'qux', 'quux', 'corge', 'grault', 'garply']

>>> a = ['foo', 'bar', 'baz', 'qux', 'quux', 'corge']

>>> a = [10, 20] + a
>>> a
[10, 20, 'foo', 'bar', 'baz', 'qux', 'quux', 'corge']
```

- Notes this difference:

```python
>>> a = ['foo', 'bar', 'baz', 'qux', 'quux']
>>> a += 'corge'
>>> a
['foo', 'bar', 'baz', 'qux', 'quux', 'c', 'o', 'r', 'g', 'e']
```

```python
>>> a = ['foo', 'bar', 'baz', 'qux', 'quux']
>>> a += ['corge']
>>> a
['foo', 'bar', 'baz', 'qux', 'quux', 'corge']
```

Access list items:

```python
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

- Note about slices:
  - lists don't error out if you are trying to acces a slice of the list that is past the start or end boundry.

```python 
a = [1,2,3,4,5]
>>> a = [1,2,3,4,5]
>>> 
>>> first_twenty_items = a[:20]  # Python doesn't care if you are trying to access items out of bounds
>>> first_twenty_items
[1, 2, 3, 4, 5]
>>> last_twenty_items = a[-20:]  # Python doesn't care if you are trying to access items out of bounds
>>> last_twenty_items
[1, 2, 3, 4, 5]
>>> 
```

- In contrast, you will get an eerror if you try to access a specific item out of bounds

```python 
>>> a[20]
IndexError: list index out of range
```


Searching items in list:

```python
if value in L:
  print "list contains", value
```

Deleting items in a list:

```python
del L[i]
del L[i:j]
item = L.pop() # last item
item = L.pop(0) # first item
item = L.pop(index)
L.remove(item)
```

Copy items from a list:

```python
a = [1, 2, 3, 4, 5]

# shallow copy
b = a[:]

# copy by type casting
b = list(a)

#Python 3 only
b = list.copy()

# Deepcopy, just like with a dict
from copy import deepcopy

l = [[1, 2], [3, 4]]

l2 = deepcopy(l)
```

Methods:

```python
list.index(x)       # get index of first matching item
list.count(x)       # number of x items
list.sort()
list.reverse()
list.insert(<index>, <obj>)       # Insert obj at index
list.remove(<obj>)       # removes obj
list.pop(<index>)   # removes and returns.  You can specify the index, not the obj
```

Notes:

- If you have multiple variables pointing to a list, then updating it updates both variables
- to avoid this:

```python
  L = []
  M = L[:] # create a copy

  # modify L only
  L.append(obj)
```

Reversing a list:

- If you want to iterate over the reversed list, use `reversed`:

```python
original_list = [1, 2, 3, 4, 5]
for element in reversed(original_list):
    print(element)
````

- If you want need the whole list, and don't need to iterate over the reversed list, use `sorted`:

```python
reversed_list = sorted(original_list, reverse=True)
````


Sorting Lists:

- Sorting numbers is easy with .sort()

```python
>>> L = [15, 22.4, 8, 10, 3.14]
>>> L.sort()
>>> L
[3.14, 8, 10, 15, 22.4]
# Notice that the list L was sorted in place. No new objects were created.

# Create a new sorted list, and leave the original unmodified
>>> L = [15, 22.4, 8, 10, 3.14]
>>> sorted_list = sorted(L)
>>> L
[15, 22.4, 8, 10, 3.14]
>>> sorted_list
[3.14, 8, 10, 15, 22.4]

# Both methods above accept 'reverse=True' to sort descending
>>> L = [15, 22.4, 8, 10, 3.14]
>>> L.sort(reverse = True)
>>> L
[22.4, 15, 10, 8, 3.14]
```

- You can do the same with strings (sorting them alphabetically)

```python
>>> L = [15, 22.4, 8, 10, 3.14]
>>> L.sort(reverse = True)
>>> L
[22.4, 15, 10, 8, 3.14]
```

- What about if there are titles (with uppercase letters)
  - clue: python considers uppercase letters to be lower than lowercase

```python
>>> L = ["oranges", "apples", "Bananas"]
>>> L.sort()
>>> L
['Bananas', 'apples', 'oranges']
```

- How to make sort work case-insensitive?
  - `sort` and `sorted` have a `key` parameter
  - This `key` parameter specifies a function that will be called on each list item before making comparisons.
  - Below is how we sort independent of case:

```python
>>> L = ["oranges", "apples", "Bananas"]
>>> L.sort(key=str.lower)
>>> L
['apples', 'Bananas', 'oranges']
```

- this will instruct the sort function to perform comparisons between the all-lowercase versions of the strings

## Dictionaries

Create a dictionary:

```python
d = {}
d = {"name": "Mike", "Age": 7}
```

Access items:

```python
d['name']
d.get('name')
d.get('name', 'default value if name doesnt exist')
```

Difference between the two snippets above:

- if the key 'name' doesn't exist in d:
  - `d['name']` will raise a KeyError
  - `d.get('name)` will return nothing
    - ** Actually, it returns a NoneType, which evaluates to boolean False

Get an item from a dic, but provide a default value if the provided key doesn't match:

```python
d = { 'key1' : 'val1', 'key2' : 'val2', 'key3' : 'val3' }

print(d.get('key4', 'default'))

# Output: default
```

You could use this in an IF statement to run code if a key exists

```python
if d.get('test', 0):
  # We only run this code if d['test'] exists

# for clarity, this works just as well
if d.get('test'):
  # only runs if this key exists.  If not, it returns NoneType, which evaluates to boolean False
```

Crude way of updating a dictionary (d1) with any key/value pairs from d2 that don't exist in d1

```python
>>> d1 = {'test1': 'value1', 'test2': 'value2', 'test3': 'value3'}
>>> d2 = {'test1': 'val1', 'test2': 'val2'}
>>>
>>> d1
{'test1': 'value1', 'test2': 'value2', 'test3': 'value3'}
>>> d2
{'test1': 'val1', 'test2': 'val2'}
>>>
>>> for i, n in d1.items():
...     d2[i] = d2.get(i, n)
...
>>> d2
{'test1': 'val1', 'test2': 'val2', 'test3': 'value3'}
>>>
>>>
>>> #Now let's do it with a dictionary comprehension
>>> test= { d2[i] : d2.get(i, n) for i, n in d1.items() }
>>> test
{'val1': 'val1', 'val2': 'val2', 'value3': 'value3'}
```

- intersectionality / commonality of two dicts:

```python
>>> a = {
...    'x' : 1,
...    'y' : 2,
...    'z' : 3
... }
>>> 
>>> b = {
...    'w' : 10,
...    'x' : 11,
...    'y' : 2
... }
>>> 
>>> a.items() & b.items()
{('y', 2)}
```

Adding / Updating items:

```python
d["city"] = "Bayfield"
```

Removing items:

- `d.pop(<key>[, <default>])`
- You can use pop to remove an item from the dict and return it

```python
>>> d = {'a': 10, 'b': 20, 'c': 30}
>>>
>>> d.pop('b')
20
>>> d
{'a': 10, 'c': 30}
```

- You can set a default value, incase that key doesn't exist

```python
>>> d = {'a': 10, 'b': 20, 'c': 30}
>>> d.pop('z', -1)
-1
>>> d
{'a': 10, 'b': 20, 'c': 30}
```

- d.popitem()
- removes a random, arbitrary key-value pair from d and returns it as a tuple

```python
>>> d = {'a': 10, 'b': 20, 'c': 30}

>>> d.popitem()
('c', 30)
>>> d
{'a': 10, 'b': 20}

>>> d.popitem()
('b', 20)
>>> d
{'a': 10}
```

- If d is empty, d.popitem() raises a KeyError exception:

```python
>>> d = {}
>>> d.popitem()
Traceback (most recent call last):
  File "<pyshell#11>", line 1, in <module>
    d.popitem()
KeyError: 'popitem(): dictionary is empty'
```

Updating items:

- `d.update(<obj>)`
- Merges a dictionary with another dictionary, updating the original (d) with the values in `<obj>` if they overlap

```python
>>> d1 = {'a': 10, 'b': 20, 'c': 30}
>>> d2 = {'b': 200, 'd': 400}

>>> d1.update(d2)
>>> d1
{'a': 10, 'b': 200, 'c': 30, 'd': 400}
```

Merging Dicts:

```python
>>> d1 = { 'a': 1 }
>>> d2 = { 'b': 2 }

# Normal way of merging
d1.update(d2)

# can also do any of the following
d1.update(**d2)
{**d1, **d2}
dict(d1.items() | d2.items())

# and result in this
{'a': 1, 'b': 2}
```

Deleting items:

```python
del d["city"]
dict.clear();         # remove all entries in dict
```

Loop over dicts:

```python
for k in d:               # get keys in dict
  print k

for k,v in d.items():     # get key, value of dict
  print k,v

for v in d.values():      # get values in dict
  print v
```

How to sort a shallow dict:

```python
>>> d = {'test': 'seven', 'apple': 'six', 'zinger': 'five' }
>>>
>>> d2 = { i : d[i] for i in sorted(d) }    # Dict comprehension
>>>
>>> d2
{'apple': 'six', 'test': 'seven', 'zinger': 'five'}

```

Methods:

```python
d.has_key(key)      # returns true if key exists
d.items()           # returns key, value tuples as a list
d.keys()            # returns list of keys
d.values()          # returns list of values
```

## Sets

Create a Set:

```python
s = set()                       # creates empty set
s = {}                          # This does not work.  This creates an empty dictionary
s = {1,2,3,4,5}
l = [1,2,3,4,5]; s = set(l)     # create a set from a list
```

Add to a Set:

- add a single element

```python
s.add("test")
```

Update a Set:

- add multiple elements

```python
s.update([1,2,3,4,5])
```

Remove from a Set:

- removes item from a set, but raises an error if the item doesn't exist

```python
s.remove("test")
```

Discard from a Set:

- removes item from a set, but doesn't raise any errors if the item doesn't exist

```python
s.discard("test")
```

Use case for Sets:

- to remove duplicate values
- when combining two lists and need unique items

Example:

- using a for loop to remove duplicate items in a list:

```python
>>> my_list = [1, 2, 3, 2, 3, 4]
>>> no_duplicate_list = []
>>>
>>> for item in my_list:
...     if item not in no_duplicate_list:
...             no_duplicate_list.append(item)
...
>>> no_duplicate_list
[1, 2, 3, 4]
```

- Using sets to do the same thing:

```python
>>> my_list = [1, 2, 3, 2, 3, 4]
>>>
>>> no_duplicate_list = list(set(my_list))
>>>
>>> no_duplicate_list
[1, 2, 3, 4]
>>>
```

## Tuples

- Tuples are identical to lists in all respects, except for the following properties:
  - Tuples are defined by enclosing the elements in parentheses (()) instead of square brackets ([]).
  - Tuples are immutable.
- Everything you’ve learned about lists—they are ordered, they can contain arbitrary objects, they can be indexed and sliced, they can be nested—is true of tuples as well. But they can’t be modified

Create a Tuple:

```python
t = ()          # empty tuple
t = 'test',     # tuple with one item (note the comma)
t = ('test',)
t = ('test1', 'test2', 3)
```

```python
>>> t = ('foo', 'bar', 'baz', 'qux', 'quux', 'corge')
>>> t
('foo', 'bar', 'baz', 'qux', 'quux', 'corge')

>>> t[0]
'foo'
>>> t[-1]
'corge'
>>> t[1::2]
('bar', 'qux', 'corge')
```

- you can reverse, like a list

```python
>>> t[::-1]
('corge', 'quux', 'qux', 'baz', 'bar', 'foo')
```

Methods:

- Tuples have no methods (because they are immutable)

## Alternate Data Types

- Defaultdict:
  - behaves like a normal Python dictionary, except when a key isn't present it'll substitute in a default value rather than raising a KeyError.

```python
# use defaultdict to count words in a list
from collections import defaultdict
import json
words = ['test', 'test', 'test', 'two', 'two', 'new']
d = defaultdict(int)

for word in words:
  d[word] += 1

print(json.dumps(d, indent=4))
# {
#     "test": 3,
#     "two": 2,
#     "new": 1
# }
```

- Create nested / multi-array dictionaries:
  - use a one-liner function and defaultdicts:
  - From here: https://gist.github.com/hrldcpr/2012250

```python
from collections import defaultdict
import json

# define a makeshift 'tree'
def tree(): return defaultdict(tree)

"""
# Can also do the same with the following one-liner:
tree = lambda: defaultdict(tree)
"""

users = tree()
users['harold']['username'] = 'hrldcpr'
users['handler']['username'] = 'matthandlersux'

print(json.dumps(users, indent=4))
# {
#     "harold": {
#         "username": "hrldcpr"
#     },
#     "handler": {
#         "username": "matthandlersux"
#     }
# }
```

## Advanced Variables

Underscores and Double Underscores (Dunders):

```python
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

## IF Statements

```python
if condition_1:
    statement_block_1
elif condition_2:
    statement_block_2
else:
    statement_block_3
```

Abbreviated if:

```python
x if condition else y;
```

Ternary if:

```python
# The first is a fairly standard teranary style;
# <value if true> if <conditional> else <value if false>

print ('passed') if x else print('did not pass')

```

## BREAK Statement

- used to break out of a `for` or `while` loop
- Note: if you break out of a for or while loop, any corresponding loop else block is not executed.

## CONTINUE Statement

- The `continue` statement is used to tell Python to skip the rest of the statements in the current loop block and to continue to the next iteration of the loop.

## PASS Statement

- `pass` is a null operation -- when it is executed, nothing happens. It is useful as a placeholder when a statement is required syntactically, but no code needs to be executed

## Loops

```python
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
        for index in fruits:
            print('Current fruit: ', i)



    while loops:
        1)
        while expression:
            statement

        2)
        while expression: statment

        1)      # else statement is run after the while loop finishes
        while expression:
            statement
        else:
            statement

```

## Operators

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

## Testing Flags and Vars

Check if var exists:

```python
try:
    x
except NameError:
    x_exists = False
else:
    x_exists = True
```

Check if var is true:

- See previous section called 'Knowing when something is True or False'

```python
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

```python
if not var:
  print('var is false')
```

When a var is false:

- See previous section 'Knowing when something is True or False'

How not to check if a var is empty:

```python
# Good
if not x:     # Works for strings, lists, dicts, sets, and tuples. Strings evaluate to False if they are empty.


# Bad
if foo == "":

# "" is a magical value. You should never check against magical values (more commonly known as magical numbers)
```

Ternary if to check if something is true:

```python
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

```python
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

```python
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

```python
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

Compound 'OR' expressions:

- code example: `(expr1) or (expr 2) or (expr 3) or (expr 4) or ... (expr n)`
- python evaluates the expressions from left to right.  
- The first true evaluation found, it stops evaluating all other expressions and returns the last evaluated expression

Compound 'AND' expressions:

- code example: `(expr1) and (expr 2) and (expr 3) and (expr 4) and ... (expr n)`
- python stops evaluating as soon as any operand is found to be false, because at that point the entire expression is known to be false
- the value of the last expression, which was found to be false, is returned

Any() and All() Functions:

- Any() function:
  - takes a iterable as input 
  - Will return True if any of the items are truthy.  False if all are Falsy (or input is empty)
  - You can think of it like a series of `OR` comparisons between the items 
- All() function:
  - returns True when all items are Truthy 
  - You can think of it like a seres of `AND` comparisons between the items
  

```python
>>> any([False, True, False])
>>> True  # At least one item is Truthy
>>> 
>>> all([False, True, False])
>>> False # At least one item was not Truthy
```

Identity Operands:

- Difference between Identity (`x is y`) and equality (`x == y`):
  - identity (`is`) checks if two items refer to the same underlying object
  - equality (`==`) checks if two objects contain the same data (but can be two distinct objects)

```python
# Example
>>> x = 1001
>>> y = 1000 + 1
>>> print(x, y)
1001 1001

>>> x == y
True
>>> x is y
False
```

## Comprehensions

list comprehension:

```python
# Template

values = [expression
          for item in collection
          if condition]

# or without conditions

values = [ expression
          for item in collection ]
```

Set Comprehensions:

```python
# Template

dict = { expression for item in collection }

# Example

>>> s = { x for x in range(10) }
>>>
>>> s
{0, 1, 2, 3, 4, 5, 6, 7, 8, 9}
>>>
>>> type(s)
<class 'set'>
>>>
```

Dict Comprehensions:

```python
# Template

dict = { key:value for item in collection }

# Example

>>> d = {x:x + 1 for x in range(10)}
>>>
>>> d
{0: 1, 1: 2, 2: 3, 3: 4, 4: 5, 5: 6, 6: 7, 7: 8, 8: 9, 9: 10}
>>>
>>> type(d)
<class 'dict'>
>>>
```

## Checking if dict key exists

How not to do it:

```python
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

```python
d = {'key1' : 'val1', 'key2' : 'val2', 'key3' : 'val3'}

if 'key4' not in d:
  print('key4 not in d')
```

Newer, cooler way of doing it with setdefault():

```python
d = {'key1' : 'val1', 'key2' : 'val2', 'key3' : 'val3'}

# If the key does not exist, then setdefault() creates it and sets it to the value specified in the second argument.

d.setdefault('key3', 'wrongVal3')   # Since 'key3' exists, it will not set the value passed
d.setdefault('key4', 'val4')        # Since 'key4' doesn't exist, it will create and set value passed in second argument
print(d)
# {'key1': 'val1', 'key2': 'val2', 'key3': 'val3', 'key4': 'val4'}

```

## Remove Dups from List

```python
items = [2, 2, 3, 3, 1]

newitems2 = list(set(items))
```

## Set Global Variables programatically

```python
d = {'a': 1, 'b': 'var2', 'c': [1, 2, 3]}
globals().update(d)
```

## Pytonic way of value swapping

```python
"""pythonic way of value swapping"""
a, b = 5, 10

a, b = b, a
```

## Reading Files

Code to read files

```python

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

## Reading CSV Files

- csv file:

```python
name,department,birthday month
John Smith,Accounting,November
Erica Meyers,IT,March
```

```python
import csv

with open('employee_birthday.txt', mode='r') as csv_file:
    csv_reader = csv.DictReader(csv_file)
    line_count = 0
    for row in csv_reader:
        if line_count == 0:
            print(f'Column names are {", ".join(row)}')
            line_count += 1
        print(f'\t{row["name"]} works in the {row["department"]} department, and was born in {row["birthday month"]}.')
        line_count += 1
    print(f'Processed {line_count} lines.')
```

Output:

```python
Column names are name, department, birthday month
    John Smith works in the Accounting department, and was born in November.
    Erica Meyers works in the IT department, and was born in March.
Processed 3 lines.
```

- Reading CSVs with pandas

CSV file:

```python
Name,Hire Date,Salary,Sick Days remaining
Graham Chapman,03/15/14,50000.00,10
John Cleese,06/01/15,65000.00,8
Eric Idle,05/12/14,45000.00,10
Terry Jones,11/01/13,70000.00,3
Terry Gilliam,08/12/14,48000.00,7
Michael Palin,05/23/13,66000.00,8
```

```python
import pandas
df = pandas.read_csv('hrdata.csv')
print(df)
```

Output:

```pyton
             Name Hire Date   Salary  Sick Days remaining
0  Graham Chapman  03/15/14  50000.0                   10
1     John Cleese  06/01/15  65000.0                    8
2       Eric Idle  05/12/14  45000.0                   10
3     Terry Jones  11/01/13  70000.0                    3
4   Terry Gilliam  08/12/14  48000.0                    7
5   Michael Palin  05/23/13  66000.0                    8
```

## HTTP Requests / Working with Requests module

Basic example:

```python
import requests

response = requests.get('http://www.amazon.com')

print(response.status_code)
print(response.headers)
```

Simple check if a response is good or not:

- If you use a Response instance in a conditional expression, it will evaluate to True if the status code was between 200 and 400, and False otherwise.

```python 
response = requests.get('http://www.amazon.com')

if response:
    print('Success!')
```

Passing Query String Parameters to a request:
```python 
url = 'http://example.com'
params = {
    'user': 'mike',
    'age': 100,
    'sex': 'M'
}
response = requests.get(url, params=params)
response.url
# 'http://example.com/?name=mike&age=100&sex=M'
``` 

Passing Headers to a request:
```python
url = 'http://example.com'
headers = {
    'Content-Type': 'application/json'
}
response = request.get(url, headers=headers)
```

Disable SSL Certificate Verification:

```python
requests.get(url, verify=False)
```

Setting the data / body in a request:

- Mostly used for `PUT`, `POST`, and `PATCH` methods
- You can send data in the body of a request as a dictionary, a list of tuples, bytes, or a file-like object
- You will use the `data` parameter, and most times use a dictionary object (for example, if the content type is: application/x-www-form-urlencoded)
- You can also set the request data / body as json data using the `json` parameter 
- When you pass JSON data via json, requests will serialize your data and add the correct Content-Type header for you.
  - You will mostly use the json parameter when posting data to APIs

```python 
url = 'http://httpbin.org/post'
data = {
    'username': 'your mom', 
    'password': 'your moms password'
}
response = requests.post(url, data=data)
response = requests.post(url, json=data)
```

Viewing / Validating request properties:

- you can access all of the properties of the prepared request using the `.request` object:
- valid properties of the `.request` object are:
  - body 
  - headers
  - method 
  - path_url (just the path, not the domain)
  - url

```python 
response = request.post(url, headers=headers, params=params, json=data)
print(response.request.url)
print(response.request.headers)
print(response.request.body)

``` 

Viewing / Validating Response properties:

- valid properties of the response object:
  - response.content = raw content in bytes
  - response.text = raw content returned as a string 
  - response.json = content returned as a json string (if the response is valid json)
  - response.headers = all the headers, as a json object (so you can do things like `response.headers['Content-Type']`)

## Kerberos

How to do Kerberos auth to internal websites:

````python
import requests
from requests_kerberos import HTTPKerberosAuth, OPTIONAL

url = 'https://w.amazon.com'

kerberos_auth = HTTPKerberosAuth(mutual_authentication=OPTIONAL, sanitize_mutual_error_response=False)
r = requests.get(url, auth=kerberos_auth, verify=False)


print(r.status_code)   # 200 OK

````

A more complex example of requests, using query string parameters, headers, and ssl verification turned off:

```python
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

## Regex

```python
import re

text = 'something here'

#basic search
match = re.search(r'something', text)

match.group(0)  # 'something'
```

```python
# more complex example
text = 'var stuff = "other stuff in the text";var WPQ2ListData = something I actually want to grep;var WPQ2SchemaData = "other stuff"'

match = re.search(r'(var WPQ2ListData = )(.*)(;var WPQ2SchemaData)', text, re.DOTALL)

match.group(0)    # 'var WPQ2ListData = something I actually want to grep;var WPQ2SchemaData'
match.group(1)    # 'var WPQ2ListData = '
match.group(2)    # 'something I actually want to grep'
match.group(3)    # ';var WPQ2SchemaData'

```

## JSON

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

 ```python
import json

s = '{"test": "value"}'

d = json.loads(s)

print(type(d))    # dict
print(d)          # {'test': 'value'}

 ```

Get JSON data from URL with requests:

```python
import json

r = requests.get('https://jsonplaceholder.typicode.com/todos')

# Two ways of doing this.

# The long way
a = json.loads(r.text)

# The short way
b = r.json()
```

## Zip() Function

- takes any number of iterables as arguments and returns an iterator over tuples of their corresponding elements

```python
list_a = [1, 2, 3, 4, 5]
list_b = ['a', 'b', 'c', 'd', 'e']

zipped_list = zip(list_a, list_b)

print zipped_list # [(1, 'a'), (2, 'b'), (3, 'c'), (4, 'd'), (5, 'e')]
```

- If the length of the iterables are not equal, zip creates the list of tuples of length equal to the smallest iterable.

```python
list_a = [1, 2, 3]
list_b = ['a', 'b', 'c', 'd', 'e']

zipped_list = list(zip(list_a, list_b))

print(zipped_list)
# [(1, 'a'), (2, 'b'), (3, 'c')]
```

- You can also unzip a list of tuples

```python
zipper_list = [(1, 'a'), (2, 'b'), (3, 'c')]

list_a, list_b = list(zip(*zipper_list))
 print(list_a)
 # (1, 2, 3)
 print(list_b)
 # ('a', 'b', 'c')
```

- in Python 3, zip() returns a zip object (unlike python2, where it returns a list of tuples)
  - This is why we have to call list(zip())
  - zip objects are generators

```python
list_a = [1, 2, 3]
list_b = [4, 5, 6]

zipped = zip(a, b) # Output: Zip Object. <zip at 0x4c10a30>

len(zipped) # TypeError: object of type 'zip' has no len()

zipped[0] # TypeError: 'zip' object is not subscriptable

list_c = list(zipped) #Output: [(1, 4), (2, 5), (3, 6)]

list_d = list(zipped) # Output []... Output is empty list becuase by the above statement zip got exhausted.
```

## Logging

Below is code that lets you log to a specified log file (change 'logfile.log') and to the console

```python
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

## Most common elements in an iterable

```python
# collections.Counter lets you find the most common
# elements in an iterable:

>>> import collections
>>> c = collections.Counter('helloworld')

>>> c
Counter({'l': 3, 'o': 2, 'e': 1, 'd': 1, 'h': 1, 'r': 1, 'w': 1})

>>> c.most_common(3)
[('l', 3), ('o', 2), ('e', 1)]
```

## Permutations

```python
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

## Variable Unpacking

- A way to assign valuees to multiple variables at one time, say from a list

Enumerate:

- enumerate unpacks two items (index and item), and the following example is how to unpack in a for loop

```python
for index, item in enumerate(some_list):
    # do something with index and item
```

    - enumerate also allows you to give the starting number for the index.  Default is 0, but this is useful when you need the index to start at 1

```python
>>> l = ['a', 'b', 'c']
>>> for i, v in enumerate(l):
...     print(i,v)
0 a
1 b
2 c
>>>
>>>
>>> for i, v in enumerate(l, 1):
...     print(i,v)
1 a
2 b
3 c
>>> # You could also specify the start param like so
>>> for i, v in enumerate(l, start=1):
...     print(i,v)
```

Using enumerate to unpack tuples (in a cool way):

```python
>>> L = [('Matt', 20), ('Karim', 30), ('Maya', 40)]
>>>
>>> for idx, (name, age) in enumerate(L):
...     print(f"Index is {idx}, name is {name}, and age is {age}")
Index is 0, name is Matt, and age is 20
Index is 1, name is Karim, and age is 30
Index is 2, name is Maya, and age is 40
```

Variable swap can be an example of unpacking:

```python
a, b = b, a
```

Nested unpacking works as well:

```python
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

```python
a, *rest = [1, 2, 3]
# a = 1, rest = [2, 3]

a, *middle, c = [1, 2, 3, 4]
# a = 1, middle = [2, 3], c = 4
```

Use a throwaway variable when unpacking:

```python
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

Different ways to do variable unpacking:

- list

```python
human = ['James', 180, 32, 'm']

name, weight, age, sex = human
# This is better than:
# name = human[0]
```

- Dict:

```python
human = {'name': 'James', 'weight': 182, 'age': 18, 'sex: 'm'}

name, weight, age, sex = human.values()
```

- Named Tuple
- Note: This isn't variable unpacking, but is still cool

```python
humans = namedtuple('human', ['name', 'height', 'age', 'sex'])

human = humans('James', 180, 32, 'm')

human
human(name='James', height=180, age=32, sex='m')

human.name
'James'
```

## Interesting way to handle exceptions

```python
import contextlib

with contextlib.suppress(FileNotFoundError):
    os.remove('somefile.tmp')

# This is equivalent to:

try:
    os.remove('somefile.tmp')
except FileNotFoundError:
    pass
```


## General Guidance

- Use list comprehensions instead of maps and filters
- Use `enumerate` over `range`
- Avoid `else` blocks after `for` and `while` loops 
- Functions:
  - Prefer to return exceptions instead of `None`


# Random 

## Print emojis on the command line:

```python
# pip install emoji
from emoji import emojize
print(emojize(":thumbs_up:"))
 👍
```

## `sh` module

- replacement for OS module
- lets you call any program as ordinary function

```python
from sh import ifconfig
print(ifconfig("wlan0"))


from sh import *
sh.pwd()
sh.mkdir('new_folder')
sh.touch('new_file.txt')
sh.whoami()
sh.echo('This is great!')

# ls command
sh.ls("-l", "/tmp", color="never")

# piping ls -l to wc -l
sh.wc(sh.ls("-1"), "-l")

# git
sh.git.show("HEAD")
```