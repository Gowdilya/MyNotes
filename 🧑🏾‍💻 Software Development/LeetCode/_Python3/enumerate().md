---
Link: https://docs.python.org/3/library/functions.html#enumerate
---
enumerate(_iterable_, _start=0_)[¶](https://docs.python.org/3/library/functions.html#enumerate "Permalink to this definition")

Return an enumerate object. _iterable_ must be a sequence, an [iterator](https://docs.python.org/3/glossary.html#term-iterator), or some other object which supports iteration. The [`__next__()`](https://docs.python.org/3/library/stdtypes.html#iterator.__next__ "iterator.__next__") method of the iterator returned by [`enumerate()`](https://docs.python.org/3/library/functions.html#enumerate "enumerate") returns a tuple containing a count (from _start_ which defaults to 0) and the values obtained from iterating over _iterable_.

```python
seasons = ['Spring', 'Summer', 'Fall', 'Winter']
>>> list(enumerate(seasons))
[(0, 'Spring'), (1, 'Summer'), (2, 'Fall'), (3, 'Winter')]
>>> list(enumerate(seasons, start=1))
[(1, 'Spring'), (2, 'Summer'), (3, 'Fall'), (4, 'Winter')]
```