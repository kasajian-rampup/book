# Python

## Examples

{% tabs %}
{% tab title="Notes" %}
```python
=== numbers, variables, assignments, expressions ===
>>> x=5
>>> x
5

// x = 5; y = 6;
>>> x, y = 5, 6
>>> x
5
>>> y
6

//x=y=z=77
>>> x=y=z=77

// complex: 5 + 2i
>>> complex(5,2)
(5+2j)

// complex: 5 + 2i
>>> 5+2j
(5+2j)

// Real part of complex
>>> (5+2j).real
5.0

// Imaginary part of complex
>>> (5+2j).imag
2.0

// (float)5
>>> float(5)
5.0

// (long)5.9
>>> long(5)
5L

// (int)70000.9
>>> int(70000.9)
70000




=== strings ===
// print "test", 3
>>> print "test", 3
test 3

// "Don't"
>>> 'don\'t'
"don't"

// "\"Yes,\" he said.\n"
>>> "\"Yes,\" he said.\n"
'"Yes," he said.\n'

// raw string
>>> r"abc\n"
'abc\\n'

// long string
>>> "abc\
... def"
'abcdef'

// block of text
>>> print """a
... b
... c"""
a
b
c

// concatination
>>> 'a' + 'b'
'ab'
>>> 'a' 'b'
'ab'

// string multiplication
>>> 'a'*5
'aaaaa'

// string trim
>>> '  a  '.strip()
'a'

// string subscripting
>>> 'abc'[1]
'b'
>>> '0123456'[3:5]
'34'
>>> '0123456'[:3]
'012'
>>> '0123456'[3:]
'3456'
>>> '0123456'[-2]
'5'

// string invariant
>>> s[:i] + s[i:] == s
True

// length
>>> len('0123456')
7




=== I/O ===
//print 5.5 * 10
>>> 5.5 * 10
55.0


// input
>>> raw_input('prompt')




=== Lists ===

// list
>>> a = [ 1, 2, 3, 'four']
>>> a
[1, 2, 3, 'four']
>>> a[0]
1
>>> a[3]
'four'
>>> a[1]
2
>>> a[0:-1]
[1, 2, 3]
>>> a[:2] + ['bacon',2*2]
[1, 2, 'bacon', 4]
>>> a[:3]
[1, 2, 3]
>>> a[:3] * 3
[1, 2, 3, 1, 2, 3, 1, 2, 3]
>>> a[:3] * 3 + ['Boo!']
[1, 2, 3, 1, 2, 3, 1, 2, 3, 'Boo!']
>>> a[2] = a[2] + 1
[1, 2, 4, 'four']
>>> a[0:2] = ['one', 'two']
>>> a
['one', 'two', 4, 'four']
>>> a[0:2] = []
>>> a
[4, 'four']
>>> a[1:1] = ['y', 'z']
>>> a
[4, 'y', 'z', 'four']
>>> a[0:0] = a
[4, 'y', 'z', 'four', 4, 'y', 'z', 'four']

>>> a = []
>>> a
[]
>>> len(a)
0

>>> a = [1,2,3,4]
>>> len(a)

>>> q = [1,2]
>>> p = [3,q,4]
>>> len(p)
3
>>> p
[3, [1, 2], 4]
>>> p[1]
[1, 2]
>>> p[1][0]
1
>>> p[1].append('XXX')
>>> p
[3, [1, 2, 'xxx'], 4]




=== other ===
//comment
>>> #comment

// In interactive mode, the last printed expression is stored in _
>>> _
70000

// fib
>>> a, b = 0, 1
>>> while b < 10:
...    print b
...    a, b = b, a+b
1
1
2
3
5
8










=== Conditionals ===

// if
>>> if 5 < 6:
...     print '<'
... elif 5 > 6:
...     print '>'
... else:
...     print '=='
<


=== Loops === 

// for
>>> a = [1,2,3]
>>> for x in a:
...     print x
...
1
2
3
>>> for x in a: print x
1
2
3

>>> for x in a[:]: #make a slice copy of the entire list
...     if x == 2 : a.insert(0,x)
...
a
[2,1,2,3]

>>> for x in range(5) : print x
...
0
1
2
3
4

>>> for x in range(2,5) : print x
...
2
3
4

>>> a = ['Mary', 'had', 'a', 'little', 'lamb']
>>> for i in range(len(a)):
...     print i, a[i]
...
0 Mary
1 had
2 a
3 little
4 lamb

// for / else
>>> for n in range(1,5):
...     print n
... else:
...     print "loop didn't break"
...
1
2
3
4
loop didn't break

// pass does nothing
>>> while True
...     pass
...

>>> class X
...    pass

// function
>>> def x(): print "hello world"
...
>>> x()
hello world
>>> x() == None
hello world
True

>>> def x():
...     "doc for function x"
...     print "hello world"
...
>>> x()
hello world
>>> y = x
>>> y()
hello world

>>> def x():
...     return 5
...
>>> x()
5

// in keyword
>>> 1 in (1,2,3)
True

// exception
>>> raise IOError, "x"
IOError: x

// default value can be a non-literal, in which case it's evaluated once, when the function is defined.
>>> def f(a, l=[]):
...     l.append(a)
...     return l
>>> print f(1)
[1]
>>> print f(2)
[1, 2]
>>> print f(3)
[1, 2, 3]

// if the above is not desired, write like so:
>>> def f(a, l=[]):
...     if l is None:
...         l = []
...     l.append(a)
...     return l
>>> print f(1)
[1]
>>> print f(2)
[2]
>>> print f(3)
[3]

// named arguments
>>> def x( a = 1, b = 2, c = 3):
...     print a
...     print b
...     print c
...
>>> x(c = 33)
1
2
33

// variable number of arguments:
>>> def x(*arguments, **keywords):
...     for arg in arguments: print arg
...     print "-" * 40
...     keys = keywords.keys()
...     key.sort()
...     for kw in keys: print kw, ":", keywords[kw]
...
>>> x(1,2,3,x=4,y=5,z=6)
1
2
3
----------------------------------------
x : 4
y : 5
z : 6

// Unpacking arguments
>>> range(3,6)
[3, 4, 5]
>>> args = [3,6]
>>> range(*args)
[3, 4, 5]

>>> d = {"x":1, "y":2, "z":3}
>>> def a(x,y,z):
...     print x
...     print y
...     print z
...
>>> a(**d)
1
2
3

// Lambda
>>> def make_incrementor(n):
...     return lambda x: x + n
...
>>> f = make_incrementor(42)
>>> f(0)
42
>>> f(1)
43

// List
>>> a = []
>>> a.append(5)
>>> a
[5]
>>> b = [1,2,3]
>>> a.extend(b)
>>> a
[5, 1, 2, 3]
>>> a.insert(2, "fred")
>>> a
[5, 1, 'fred', 2, 3]
>>> a.remove('fred')
>>> a
[5, 1, 2, 3]
>>> a.pop()
3
>>> a
[5, 1, 2]
>>> a.pop(0)
5
>>> a
[1, 2]
>>> a = [ 'a', 'b', 'c' ]
>>> a.index('b')
1

// number of times 'b' appears
>>> a.count('b')
1
>>> a.reverse()
>>> a
['c', 'b', 'a']
>>> a.sort()
>>> a
['a', 'b', 'c']

// use as a stack
>>> a = [1, 2, 3]
>>> a.append(4)
>>> a.pop()

// use as a queue
>>> a = [1, 2, 3]
>>> a.append(4)
>>> a.pop(0)

// functional programming
>>> def f(x): return x % 2 != 0 and x % 3 != 0
...
>>> filter(f, range(2, 25))
[5, 7, 11, 13, 17, 19, 23]

>>> def cube(x): return x*x*x
...
>>> map(cube, range(1,11))
[1, 8, 27, 64, 125, 216, 343, 512, 729, 1000]

>>> seq = range(8)
>>> def add(x,y): return x+y
...
>>> reduce( add, range(1,11))
55
>>> reduce( add, range(2,11), 1)
55

// delete from a list
>>> a = [1, 2, 3, 4]
>>> del a[0]
>>> a
[2, 3, 4]

>>> a = [1, 2, 3, 4]
>>> del a[2:4]
>>> a
[1, 2]
>>> del a[:]
>>> a
[]

// delete a variable
>>> del a

// tuples -- non mutable lists.
>>> t = 1, 2, 3
>>> t[0]
1
>>> t
(1, 2, 3)
>>> (1, 2, ('a', 'b'), 3 )
(1, 2, ('a', 'b'), 3)
>>> ()
()
>>> (1,)
(1,)
>>> s = 1,
>>> s
(1,)
>>> x,y,z = t
>>> x
1
>>> y
2
>>> z
3

>>> x,y,z = (1,2,3)
>>> x,y,z = [1,2,3]

// sets
>>> a = set(['x', 'y', 'z'])
>>> a

// fast lookup
>>> 'x' in a
True

set(['y', 'x', 'z'])
>>> a = set('xyz')
>>> a
set(['y', 'x', 'z'])
>>> a = set('yxyyzyzzxzxx')
>>> a
set(['y', 'x', 'z'])
>>> b = set('wxz')

>>> a - b
set(['y'])
>>> a | b
set(['w', 'y', 'x', 'z'])
>>> a & b
set(['x', 'z'])
>>> a ^ b
set(['w', 'y'])

// dictionary
>>> a = {'x':1, 'y':2}
>>> a['x']
1
>>> a
{'x':1, 'y':2}
>>> del a['x']
>>> a
{'y': 2"
>>> a['z'] = 33
>>> a
{'z': 33, 'y': 2}

>>> a = {'x':1, 'y':2, 'z':3}
>>> for k, v in a.iteritems():
...     print k, v
...
x 1
z 3
y 2

>>> for i, v in enumerate([99,88,77]):
...     print i, v
...
0 99
1 88
2 77

>>> for i, v in enumerate((99,88,77)):
...     print i, v
...
0 99
1 88
2 77

>>> a = [1,2,3]
>>> b = [11,22,33]
>>> for x,y in zip(a,b):
...     print x, y
...
1 11
2 22
3 33

>>> for i in reversed(range(1,5)):
...     print i
...
4
3
2
1

>>> for i in sorted(set([3, 9, 1, 4, 2])):
        print i
1
2
3
4
9

// modules:
>>> __name__
'__console__'
>>> import fibo
>>> fibo.fib(10)
1 1 2 3 5 8
>>> z = fibo.fib(10)
>>> z(10)
1 1 2 3 5 8
>>> from fibo import fib2
>>> fib2(10)
 [1, 1, 2, 3, 5, 8]

>>> from fibo import *

// running a .py file from the command line.
>>> if __name__ == "__main__":
        import sys
        fib(int(sys.argv[1]))

// package is a folder that contains the __init__.py file.

// if __init__.py code defines a list named __all__, it is taken to be the list of modules that should be imported with: from package import *


// output
>>> str(5)
'5'
>>> repr(5)
'5'

>>> 'x'.rjust(5)
'    x'

// file io
>>> f = open( 'file', 'w')
>>> print f

>>> for line in f:
...     print line,


>>> pickle is to serialize
>>> import pickle
>>> x = { 'name': 'Fred', 'age': 32}
>>> f = open( 'something.pickle', 'wb')
>>> pickle.dump(x,f)
>>> f.close()

>>> f = open(..., 'rb')
>>> x = pickle.load(f)
>>> x
{ 'name': 'Fred', 'age': 32}


>>> try:
...     x = int("abc")
... except ValueError:
...     print "value error"
...
value error

>>> try:
...     x = int("abc")
... except (ValueError, RuntimeError, TypeError, NameError)
...     print "error"
...

>>> try:
...     x = int("abc")
... except (ValueError, RuntimeError, TypeError, NameError)
...     print "error"
... except IOError, e:
...     print "i/o error (%s)" % str(e)
... except
...     print "unexpected"
...     raise
...

>>> try:
...     x = int("abc")
... except ValueError:
...     print "value error"
... else:
...     print "didn't throw exception"
...

>>> try:
...     raise Exception( 'aa', 'bb')
... except Exception, inst:
...     x, y = inst
...     print x
...     print y
...

>>> try:
...     raise KeyboardInterrupt
... finally:
...     print 'Goodbye, world!'
...

>>> class X:
...     i = 5
...
>>> a = X()
>>> print a.i
5

>>> class X:
...     def __init__(self):
...         self.i = 5
...
>>> a = X()
>>> print a.i
5
>>> a.g = 55
>>> print a.g
55


```
{% endtab %}

{% tab title="Sample" %}
```python
## Sample Python code
import sys

## Sample_Conditional
def Sample_Conditional() :
    print 'This should print: 5 < 6:'
    if 5 < 6:
        print '5 < 6'
    elif 5 > 6:
        print 100
    else:
        print 101

    print 'This should print: 1 is in (1,2,3):'
    if 1 in (1,2,3):
        print '1 is in (1,2,3)'


## Sample_FunctionPointerAssignment
def print_helloworld(): print 'hello world'

def Sample_FunctionPointerAssignment() :
    print '# invoking the original function should print: hello world'
    print_helloworld()
    print '# assign the function to another variable and then'
    x = print_helloworld
    print '# invoke the same function through the new variable:'
    x()


## Sample_FunctionWithDefaults
def Sample_FunctionWithDefaults_sub( a = 1, b = 2, c = 3):
    print a, b, c

def Sample_FunctionWithDefaults():
    print 'this should print: 1 2 3'
    Sample_FunctionWithDefaults_sub()
    print 'this should print: 33 2 3'
    Sample_FunctionWithDefaults_sub(33)


# Sample_FunctionWithVarArgs
def Sample_FunctionWithVarArgs_sub(*arguments):
    for arg in arguments: print arg

def Sample_FunctionWithVarArgs_sub_with_keywords(**keywords):
    keys = keywords.keys()
    for k in keys: print k, ':', keywords[k]

def Sample_FunctionWithVarArgs():
    print 'This should print 21, 22 and 23 each on a separate line:'
    Sample_FunctionWithVarArgs_sub( 21, 22, 23)
    print 'This should print y : 35, x : 34, z : 36 on a separate line:'
    Sample_FunctionWithVarArgs_sub_with_keywords( x=34, y=35, z=36)
    print 'This should do the same as above, but using a dictioanry ( { } lists )'
    stuff = {'x':34, 'y':35, 'z':36}
    Sample_FunctionWithVarArgs_sub_with_keywords( **stuff )


## Sample_FunctionMaker

# This function returns a newly created function for a specific type of gas price
# That function can then be called with number of gallons to get the total price of gas
def gas_calc_function_maker(price_per_gallon) :
    return lambda gas_calculator: gas_calculator * price_per_gallon

def Sample_FunctionMaker():
    # make a function called regular_gas()
    regular_gas = gas_calc_function_maker( 3.00 )

    # make a function called unleaded_gas()
    unleaded_gas = gas_calc_function_maker( 4.00 )

    # make a function called super_unleaded_gas()
    super_unleaded_gas = gas_calc_function_maker( 5.00 )

    # Pass in number of gallons and print out $ to buy that type of gas
    print '10 gallons at $3 a gallon:'
    print regular_gas( 10 )

    print '10 gallons at $4 a gallon:'
    print unleaded_gas( 10 )


#Sample_Strings
def Sample_Strings():
    s = 'Jeff\
 Spicoli'
    print 'Should print Jeff Spicoli:'
    print s

    print 'Should print Jeff | Spicoli, each word on a separate line:'
    print """
Jeff
Spicoli
"""
    print 'Should print unicode Jeff Spicoli:'
    print u'Jeff\u0020Spicoli'

    print 'Should print Jeff Spicoli:'
    print 'Jeff ' + "Spicoli"

    print 'Should print Jeff Spicoli:'
    print 'Jeff ' "Spicoli"

    print 'Should print JeffJeffJeffJeffJeff:'
    print 'Jeff' * 5

    print 'Should print Jeff:'
    print '   Jeff '.strip() #trims

    a = 'Jeff Spicoli'
    print 'Should print Spicoli:'
    print a[5:12]  #from pos 5 to pos 12

    print 'Should print Jeff:'
    print a[:4] #1st 4 chars

    print 'Should print Spicoli:'
    print a[5:] #everything except 1st 5 chars

    print 'Should print Spicoli:'
    print a[-7:] #last 7 chars

    print 'Should print Jeff:'
    print a[:-8] #Everything except the last 9 characters

    print 'Should print 1st 3 and last 3 characters: J e f | i l o'
    print a[0], a[1], a[2] # first 3 characters
    print a[-1], a[-2], a[-3] # last 3 characters in reverse order

    # i can be any valid index, this always return sture
    i = 5
    print 'Should return true for any valid index i of string a: a[:i] + a[i:] == a'
    print a[:i] + a[i:] == a

    print 'Should print 10 9:'
    print '{1} {0}'.format( 9, 10)

    print 'Should print 10 9:'
    print '%s %s' % (10, 9)

    import string
    from string import Template
    s = Template('$who likes $what')
    s = Template('$who likes $what')
    print 'Should print tim likes kung pao:'
    print s.substitute(who='tim', what='kung pao')

    print "Should print: ['abc', 'def', 'ghi']"
    print 'abc def ghi'.split(' ')

    print "Should print: abc def ghi"
    print ' '.join(['abc', 'def', 'ghi'])

    print "Should print abc"
    print ''.join(['a','b','c'])


#Sample_MapReduce
def mp_cube(x):
    return x * x * x

def mp_add(x,y):
    return x + y

def Sample_MapReduce():
    print 'prints a list that\'s the cubes of 1 through 10:'
    print map(mp_cube, range(1,11))

    print 'prints the sum of the numbers 1 through 10:'
    print reduce( mp_add, range(1,11))



## Sample_ReturnValue
def return_hello_world():
    "This is the doc for the function -- it's not executed"
    return 'hello world returned'

def Sample_ReturnValue():
    print 'this should print: hello world returned'
    print return_hello_world()


## Sample_Values
def Sample_Values():
    a, b = 0, 1
    print 'Should print 0 1'
    print a, b

    print 'Should print 11'
    x = 5
    y = 6
    z = x + y
    print z

    print 'Should print 15'
    x,y = 7,8
    z = x + y
    print z

    print 'Should print concat strings'
    s = "concat" + " strings"
    print s

    # x is no longer a valid variable
    del x

    print 'Should print c concat st'
    print s[0], s[0:9]

    print 'Should print 14'
    print len(s)

    print 'Should print: -----'
    print '-' * 5

    print 'Should print 97'
    print ord('a')

    print 'Should print imaginary number i, by printing 1j twice:'
    print complex(0,1), 1j

    print 'Should print true, to indicate that the square of i**2 is -1:'
    print 1j * 1j == -1

    a=1.5+0.5j

    print 'Should print 1.5:'
    print a.real
    print 'Should print 0.5:'
    print a.imag

    print 'Should print 3.0 5 34:'
    print float(3), abs(-5), int( "34" )


## Sample_ClassSimple

# SimpleClass1 and SimpleClass2 are basically identical
class SimpleClass1:
    i = 5

class SimpleClass2:
    def __init__(self):
        self.i = 5

class SimpleClass3:
    i = 5
    def get_i(self):
        return self.i

# SimpleClass3 and SimpleClass4 are basically identical
def get_i(self):
    return self.i

class SimpleClass4:
    i = 5
    get_i = get_i

# Simple struct: Rect
class Rect:
    pass

# The for loops right now, during class definition
class WeirdClass:
	i = []
	for j in range(5):
		i.append(j)

class Animal:
    age = 0
    def __init__(self):
        self.age = 34

class Dog(Animal):
    def __init__(self):
        Animal.__init__(self)

def Sample_ClassSimple():
        #SimpleClass
        a = SimpleClass1()
        a.i = 99
        b = SimpleClass1()
        b.z = 102
        print 'Should print 99, 5, 102:'
        print a.i, b.i, b.z

        #SimpleClass2
        a = SimpleClass2()
        a.i = 99
        b = SimpleClass2()
        b.z = 102
        print 'Should print 99, 5, 102:'
        print a.i, b.i, b.z

        #SimpleClass3
        a = SimpleClass3()
        print 'Should print 5 and 5:'
        print a.i
        print a.get_i()

        #SimpleClass4
        a = SimpleClass4()
        print 'Should print 5 and 5:'
        print a.i
        print a.get_i()

        #Rect
        r = Rect()
        r.top = 1
        r.left = 1
        r.bottom = 100
        r.right = 200
        print 'Should print 1 1 100 200:'
        print r.top, r.left, r.bottom, r.right

        #Dog
        d = Dog()
        print 'Should print 34'
        print d.age

        print 'Should print [0, 1, 2, 3, 4]'
        weird = WeirdClass()
        print weird.i


## Sample_Lists

# list x with members 1, 2 and 3.
x = [1,2,3]
# add 4 to the list
x.append(4)

# This function is not intuitive.  The second parameter lives
# beyond the call to the function (kind of like static)
def func_owns_static_list_and_returns_it(a, l=[]):
    l.append(a)
    return l

def Sample_Lists():
    print 'Print the entire list: ', x
    print 'Print one item at a time: ', x[0], x[1], x[2], x[3]

    # The following three lines will display:
    # [11]
    # [11, 22]
    # [11, 22, 33]
    print func_owns_static_list_and_returns_it(11)
    print func_owns_static_list_and_returns_it(22)
    print func_owns_static_list_and_returns_it(33)


## Sample_ListOperations

def Sample_ListOperations():
    a = range(1,11)

    print 'Should print: 1-10:'
    print a
    print 'Should print 2 4:'
    print a[1], a[3]
    print 'Should print 2-10:'
    print a[1:]
    print 'Should print 1-9:'
    print a[0:-1]

    print 'Should print 1-5:'
    print [1,2,3] + [4,5]

    a = range(1,11)

    print 'Should print 1,2:'
    print a[0:2]

    a[0:2] = [11,22]
    print 'Should print: [11, 22, 3, 4, 5, 6, 7, 8, 9, 10]'
    print a

    print 'Should print: [6, 7]'
    print a[5:7]

    a[5:7] = []
    print 'Should print: [11, 22, 3, 4, 5, 8, 9, 10]'

    a = range(1,11)
    print 'Should print 10:'
    print len(a)

    args = [1,11]
    a = range(*args)
    print 'Should print: 1-10:'
    print a

    a = []
    a.append(5)
    print 'Should print [5]:'
    print a

    b = [98,99]
    a.extend(b)
    print 'Should print [55, 98, 99]:'
    print a

    a = [5, 6, 7]
    a.insert(2, 'fred')
    print 'Should print [5, 6, \'fred\', 7'
    print a

    print 'Should print 7:'
    print a.pop()
    print 'Should print [5, 6, \'fred\''
    print a

    a = [5, 6, 7]
    a.remove(6)
    print 'Should print [5, 7]'
    print a

    a = [1, 2, 3, 4]
    del a[0]
    print 'Should print: [2, 3, 4]:'
    print a

    a = [1, 2, 3, 4]
    a[0:1] = []
    print 'Should print: [2, 3, 4]:'
    print a

    a = range(1,11)
    del a[:]
    print 'Should print: []:'
    print a

    a = range(1,5)
    del a[2:3]
    print 'Should print: [1,2,4]'
    print a

    print 'Should print: 0 a | 1 b | 2 c, each on a separate line'
    a = ['a', 'b', 'c']
    for i, v in enumerate(a):
        print i, v

    print 'Should print: 0 a | 1 b | 2 c, each on a separate line'
    a = [0, 1, 2]
    b = ['a', 'b', 'c']
    for i, v in zip(a, b):
        print i, v

    print 'Should print: 4, 3, 2, 1, each on a separate line'
    a = range(1, 5)
    for i in reversed(a):
        print i

    print 'Should print: [1, 2, 3, 4]'
    a = [1, 2, 3, 4]
    print [x for x in a]

    print 'Should print: [3, 6, 9, 12]'
    print [3*x for x in a]

    print 'Should print: [9, 12]'
    print [3*x for x in a if x > 2]

    print 'Should print: [[1, 1], [2, 4], [3, 9], [4, 16]]'
    print [[x,x**2] for x in a]

    print 'Should print: [8, 6, -18, 16, 12, -36, 24, 18, -54]'
    print 'and [6, 5, -7, 8, 7, -5, 10, 9, -3]'
    a1 = [2, 4, 6]
    a2 = [4, 3, -9]
    print [x*y for x in a1 for y in a2]
    print [x+y for x in a1 for y in a2]

    print 'Should print: [8, 12, -54]'
    print [a1[i]*a2[i] for i in range(len(a1))]

    print "Should print: ['3.1', '3.14', '3.142', '3.1416', '3.14159']"
    print [str(round(355/113.0, i)) for i in range(1,6)]

    mat = [
           [1, 2, 3],
           [4, 5, 6],
           [7, 8, 9],
          ]

    print 'Should print: [(1, 4, 7), (2, 5, 8), (3, 6, 9)]'
    print zip(*mat)


## Sample_DictionaryOperations

def Sample_DictionaryOperations():
    a = {'x':1, 'y':2}

    print "Should print: {'y': 2, 'x': 1}"
    print a

    print 'Should print 1'
    print a['x']

    a = {'x':1, 'y':2, 'z':3}

    print 'Should print True True False False'
    print a.has_key('x'),
    print 'x' in a,
    del a['x']
    print a.has_key('x'),
    print 'x' in a

    print 'Should print y 2 | z 3, on a separate line, in no particular order'
    for k, v in a.iteritems():
        print k, v

    print "Should print: ['y', 'z']:"
    print a.keys()
    print "Should print: [('y', 2), ('z', 3)]"
    print a.items()

## Sample_SetOperations
def Sample_SetOperations():
    print "Should print 3 times in a row: set(['y', 'x', 'z'])"
    s = set(['x', 'y', 'z'])
    print s
    s = set('xyz')
    print s
    s = set('yxyyzyzzxzxx')
    print s

    print 'Should print True False'
    print 'x' in s, 'w' in s

    print "Should print 'set(['x', 'z', 'w'])'"
    t = set('wxz')
    print t

    print "Should print: set(['y'])"
    print s - t

    print s | t
    print "Should print: set(['w', 'y', 'x', 'z'])"

    print s & t
    print "Should print: set(['x', 'z'])"

    print s ^ t
    print "Should print: set(['y', 'w'])"


## Sample_Tuples
def Sample_Tuples():
    print 'Should print (1, 2, 3)'
    t = 1, 2, 3
    print t

    print 'Should print (1, 2, 3)'
    t = (1, 2, 3)
    print t

    print 'Should print 1'
    print t[0]

    print 'Should print 1 2 3'
    x,y,z = t
    print x, y, z

    print 'Should print 1 2 3'
    x,y,z = (1,2,3)
    print x, y, z

    print 'Should print 1 2 3'
    x,y,z = [1,2,3]
    print x, y, z

    print 'Should print (1,)'
    t = (1, )
    print t

    print 'Should print (1,)'
    t = 1,
    print t


## Sample_Loops
def Sample_Loops():
    a, b = 0, 1

    print 'Should print on a separate line each: 1 1 2 3 5 8'
    while b < 10:
        print b
        a, b = b, a + b

    print 'Should print 1 2 3'
    a = [1,2,3]
    for x in a:
        print x

    print 'Should print [1, 2, 42, 3, 4]'
    a = range(1,5)
    #slice copy because list will be modified
    for x in a[:]:
        if x == 2 : a.insert(x,42)
    print a

    print 'Should print each on a separate line: 0 1 2'
    for x in range(3) : print x

    print 'Should print each on a separate line: 2 3 4'
    for x in range(2,5) : print x

    a = ['Mary', 'had', 'a', 'little', 'lamb']
    print 'Should print each on a separate line: 0 Mary | 1 had | 2 a | 3 little | 4 lamb'
    for i in range(len(a)):
        print i, a[i]

    print "Should print on a Separate line: -1 | 0 | didn't break"
    for n in range(-1,1): print n
    else: print "didn't break"


#Sample_Exception
class MyError(Exception):
    def __init__(self, value):
        self.value = value

    def __str__(self):
        return repr(self.value)

def this_fails():
    x = 1 / 0

def Sample_Exception():
    try:
        x = int( "a" )
    except ValueError:
        print "Could not convert data to an integer."
    except IOError as (errno, strerror):
        print "I/O error({0}): {1}".format(errno, strerror)
    except:
        print "Unexpected error:", sys.exc_info()[0]
    else:
        print "this won't execut"

    try:
        x = int('9')
    except:
        print "Unexpected error:", sys.exc_info()[0]
    else:
        print "there was no exception'"

    print "Try program raised exception"
    try:
        raise Exception( 'spam', 'eggs' )
    except Exception as inst:

        print 'Should print exception type'
        print 'type: ', type(inst)

        print "Should print tuple ('spam', 'eggs')"
        print 'args: ', inst.args

        print "Should print string: ('spam', 'eggs')"
        print 'as string: ', inst
        x, y = inst

        print "Should print spam eggs"
        print 'unpacked: x, y: ', x, y

    print "Should indicate divice by zero error"
    try:
        this_fails()
    except ZeroDivisionError as detail:
        print 'Handling run-time error:', detail

    print "Custom exceptions"
    try:
        raise MyError(2*2)
    except MyError as e:
        print "My exception occurred, value:", e.value

    print "re-raise"
    try:
        try:
            raise MyError( 97 )
        except MyError as e:
            print "My exception occurred, value:", e.value
            raise
    except:
        print "Unexpected error:", sys.exc_info()[0]

    print 'try/finally'
    try:
        x = int('9')
    except:
        print "Unexpected error:", sys.exc_info()[0]
    else:
        print "there was no exception'"
    finally:
        print 'Finally clause'

## Sample_OS
class DirTreeWalker_count:
    i = 0

def dirTreeWalker( arg, dirname, fnames):
#    DirTreeWalker_count
    print dirname
    print fnames


def Sample_OS():
    print 'Should print current working directory:'
    import os
    print os.getcwd()

    print 'Should print current working directory:'
    from os import getcwd
    print getcwd()

    print 'Should print the PATH environment variable:'
    print os.environ.get('PATH')

    print 'Should print files (1st 10) in current directory (using glob):'
    import glob
    i = 0
    for x in glob.iglob('*'):
        print x,
        i = i + 1
        if i > 10: break

    print 'Should print files (1st 10) in current directory (using dircache):'
    import dircache
    i = 0
    for x in dircache.listdir('.'):
        print x,
        i = i + 1
        if i > 10: break

    print 'Should print (1st 10) files in the root directory:'
    d = '/'
    filenames = os.listdir(d)
    i = 0
    for filename in filenames:
        path = os.path.join(d, filename)
        print path, os.path.abspath(path)
        i = i + 1
        if i > 10: break

    print 'About to create then remove folder delete_me'
    tempdir = os.path.join(os.getcwd(), "delete_me")

    if os.path.exists( tempdir ):
        raise Exception( tempdir + ' already exists' )
    os.mkdir( tempdir )
    if not os.path.exists( tempdir ):
        raise Exception( tempdir + ' does not exist')
    os.rmdir( tempdir )
    if os.path.exists( tempdir ):
        raise Exception( tempdir + ' could not be removed' )

    import shutil
    #shutil.copy

    import commands
    cmd = 'ls -l'
    print 'about to do ls -l'
    (status, output) = commands.getstatusoutput(cmd)
    if status:
        sys.stderrr.write( "there was an error:" + output)
        # sys.exit(1)
    else:
        print output

## Sample_FileIO
def Sample_FileIO():

    #this will create a file called something.pickle

    import pickle
    x = { 'name': 'Fred', 'age': 32}
    f = open( 'something.pickle', 'wb')
    pickle.dump(x,f)
    f.close()

    print 'Should print: pickle.dump(x,f)'
    import linecache
    print linecache.getline('fileio.py', 4)

    print "Should print something like: {'age': 32, 'name': 'Fred'}"
    f = open('something.pickle', 'rb')
    x = pickle.load(f)
    print x
    f.close()

    f = open( 'some.txt', 'wb')
    f.write('one\n')
    f.write('two\n')
    f.close()

    print 'Should print two lines, with embedded \\n: one | two'
    f = open( 'some.txt', 'rb' )
    for line in f:
        print line
    f.close()

    print "Should print: ['one\\n', 'two\\n']"
    f = open('some.txt', 'rb')
    x = f.readlines()
    print x

    print 'Should print two lines, with embedded \\n: one | two'
    print x[0]
    print x[1]
    f.close()

    print 'Should print two lines, with embedded \\n: one | two'
    f = open( 'some.txt', 'rb' )
    print f.readline()[:-1] # the [:-1] prints all but last char of the line
    print f.readline()[:-1]
    f.close()

    f = open('test.out', 'wb')
    f.write('Kenny')
    f.close()

    print "Should print something like:..."
    f = open('test.out', 'rb')
    f.seek(2)

    print 'Should print nn:'
    print f.read(2)

    print 'Should print 4:'
    print f.tell()

    print 'Should print y:'
    print f.read()
    f.close()

    print 'Should print Kenny:'
    with open('test.out', 'rb') as f:
        print f.read(5)


##Sample_Internet
def Sample_Internet():
    import urllib2
    import urllib

    for line in urllib2.urlopen('http://tycho.usno.navy.mil/cgi-bin/timer.pl'):
        if 'EST' in line or 'EDT' in line:  # look for Eastern Time
            print line

    print 'Filename of google logo file downloaded'
    a, b = urllib.urlretrieve('http://www.google.com/logos/classicplus.png', 'blah.png')
    print a
    

##Sample_SQL
def Sample_SQL():
    import sqlite3
    con = sqlite3.connect(":memory:")
    con.execute("create table person (id integer primary key, firstname varchar unique)")
    con.execute("insert into person values (5, 'Kenny')")
    con.execute("insert into person values (7, 'Curt')")

    print 'Should print 5 Kenny | 7 Curt'
    for i in con.execute("select * from person"):
            print i[0], i[1]


##Sample_RE
def Find(pat, text):
    import re

    match = re.search(pat, text)
    if match: print match.group()
    else: print 'not found'

def Sample_RE():
    import re

    match = re.search( 'Xyz', 'abc xyz fred', re.IGNORECASE)
    print( "Should print False:" )
    print match == None

    match = re.search( 'xyZz', 'abc xyz fred')
    print( "Should print True:" )
    print match == None

    print( "Should print ig:" )
    Find( 'ig', 'called piiig' )

    match = re.search(r'([\w.]+)@([\w.]+)', 'blah nick.p@gmail.com yatta @')

    print ("Should print True four times" )
    print match.group() == 'nick.p@gmail.com',
    print match.group(1) == 'nick.p',
    print match.group(2) == 'gmail.com',
    print match.group(0) == 'nick.p@gmail.com'

    print "Should print: [('Jones', 'Fred'), ('Sage', 'Ken'), ('Smith', 'Jill')]"
    print re.findall(r'(\w*),(\w*)', 'Jones,Fred Sage,Ken Smith,Jill')





## main
def main() :
    print
    print '----'
    print 'sys.argv:', sys.argv

    print 'Menu:'
    print '1. Conditional'
    print '2. FunctionPointerAssignment'
    print '3. FunctionWithDefaults'
    print '4. FunctionWithVarArgs'
    print '5. FunctionMaker'
    print '6. Strings'
    print '7. MapReduce'
    print '8. ReturnValue'
    print '9. Values'
    print '10. ClassSimple'
    print '20. Lists'
    print '21. ListOperations'
    print '30. DictionaryOperations'
    print '31. SetOperations'
    print '32. Tuples'
    print '40. Loops'
    print '45. Exceptions'
    print '50. OS'
    print '60. FileIO'
    print '65. Internet'
    print '70. SQL'
    print '80. Regular Expressions'
    print
    print 'q. quit'
    print 's. shell'

    entered = raw_input( 'Select: ' )
    print
    print '>>>>'
    if entered == 'q':
        quit()
    if entered == 's':
        print 'dropping through to shell'
    elif entered == '1':
        Sample_Conditional()
        main()
    elif entered == '2':
        Sample_FunctionPointerAssignment()
        main()
    elif entered == '3':
        Sample_FunctionWithDefaults()
        main()
    elif entered == '4':
        Sample_FunctionWithVarArgs()
        main()
    elif entered == '5':
        Sample_FunctionMaker()
        main()
    elif entered == '6':
        Sample_Strings()
        main()
    elif entered == '7':
        Sample_MapReduce()
        main()
    elif entered == '8':
        Sample_ReturnValue()
        main()
    elif entered == '9':
        Sample_Values()
        main()
    elif entered == '10':
        Sample_ClassSimple()
        main()
    elif entered == '20':
        Sample_Lists()
        main()
    elif entered == '21':
        Sample_ListOperations()
        main()
    elif entered == '30':
        Sample_DictionaryOperations()
        main()
    elif entered == '31':
        Sample_SetOperations()
        main()
    elif entered == '32':
        Sample_Tuples()
        main()
    elif entered == '40':
        Sample_Loops()
    elif entered == '45':
        Sample_Exception()
        main()
    elif entered == '50':
        Sample_OS()
        main()
    elif entered == '60':
        Sample_FileIO()
        main()
    elif entered == '65':
        Sample_Internet()
        main()
    elif entered == '70':
        Sample_SQL()
        main()
    elif entered == '80':
        Sample_RE()
        main()
    else:
        pass


## Invoke the Main function
if __name__ == '__main__':
    main()

```
{% endtab %}
{% endtabs %}

