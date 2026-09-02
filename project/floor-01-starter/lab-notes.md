**1:
-- Race the Bestiary (1000 iterations per cell) --
  N=     10  query=last    linear=     0.388 us  binary=   0.225 us  recursive=   0.202 us
  N=     10  query=absent  linear=     0.246 us  binary=   0.177 us  recursive=   0.189 us
  N=    100  query=last    linear=     3.390 us  binary=   0.535 us  recursive=   0.423 us
  N=    100  query=absent  linear=     2.576 us  binary=   0.725 us  recursive=   0.571 us
  N=   1000  query=last    linear=    25.239 us  binary=   0.554 us  recursive=   0.755 us
  N=   1000  query=absent  linear=    15.800 us  binary=   0.367 us  recursive=   0.409 us
  N=  10000  query=last    linear=   226.591 us  binary=   0.735 us  recursive=   0.749 us
  N=  10000  query=absent  linear=   137.746 us  binary=   0.557 us  recursive=   0.730 us
  N= 100000  query=last    linear=  2315.507 us  binary=   1.089 us  recursive=   1.339 us
  N= 100000  query=absent  linear=  1427.470 us  binary=   0.661 us  recursive=   0.750 us

Notice the curve: linear grows with N, binary grows with log N.
For tiny N the constants matter and the gap is small.
For large N the gap is enormous.

**2:
N = 100

**3:
Recursive, and this is surprising because it's more function calls.

**4:
Since the list is unsorted the target could get completely skipped due to it's index not matching the value.

**5:
Recursive is usually slightly slower. This is probably because of how many times the computer needs to call the same function. The difference is only around 200 milliseconds.
