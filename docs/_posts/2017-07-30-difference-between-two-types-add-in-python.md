## a += b
	>>> a1 = [0, 1, 2]
	>>> a2 = a1
	>>> a2 += [3]
	>>> a1
	[0, 1, 2, 3]
	>>> a2
	[0, 1, 2, 3]
## a = a + b
	>>> a1 = [0, 1, 2]
	>>> a2 = a1
	>>> a2 = a2 + [3]
	>>> a1
	[0, 1, 2]
	>>> a2
	[0, 1, 2, 3]
 
Obviously there is difference between 'a += b' and 'a = a + b', it is because in Python, '+=' operator call '\_\_iadd\_\_' method, which is different from '\_\_add\_\_' method called by '+' operator.

However, the difference only occurs in **mutable objects**.

'\_\_iadd\_\_' method directly **updates** the original object after the operation, which means the previous pointer to that object is unchanged. The return value of '\_\_iadd\_\_' method is None.

'\_\_add\_\_' method would return **a new object** and change the previous pointer to this new object.

It must be noted that for immutable objects like 'int' and 'string', the functions of these two methods are same since immutable objects are directly used by interpreter, not referenced like 'list' object.