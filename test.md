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
