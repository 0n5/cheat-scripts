Python builtin functions, methods, types
========================================

#### isinstance

returns true if object is an instance, false if not

``` python

if isinstance([OBJECT], unicode):
    print 'object is unicode'
else:
    print 'object is NOT unicode'
```

#### split

splits a string into seperate words and returns list

``` python 

break = 'one, two, three'

broken = break.split(',', 1)
# uses maxsplit parameter, will stop after first comma

broken = break.split(',')
# no maxsplit parameter, will split all words at all commas

broken[0]
# returns first word in list

broken[1]
# returns second word in list

```