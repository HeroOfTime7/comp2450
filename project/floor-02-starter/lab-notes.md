**1
-- Race the Sorts (random input) --
  N=     10  mergeSort=   0.054 ms  quicksort=    0.027 ms  std::sort=   0.016 ms
  N=    100  mergeSort=   1.120 ms  quicksort=    0.437 ms  std::sort=   0.294 ms
  N=   1000  mergeSort=   8.733 ms  quicksort=    4.542 ms  std::sort=   3.706 ms
  N=  10000  mergeSort=  93.626 ms  quicksort=   70.422 ms  std::sort=  49.175 ms
  N= 100000  mergeSort=1197.815 ms  quicksort=  770.451 ms  std::sort= 649.866 ms

**2
N = 10000

**3
std::sort gets considerably faster, and merge sort gets slower at N = 10000. This is because the operations it needs to complete before it realizes it is already sorted is much smaller with a pre-made list.

**4
On a bad pivot quicksort completes many unneeded operations, witch slows time down by a lot.

**5
I would defiantly ship the std::sort. Not only is this an optimized sort, it also is a hybrid between multiple algorithms. This gives it the edge with any set of data, sort or unsorted. It is optimized to run best and worst case in the best way possible.
