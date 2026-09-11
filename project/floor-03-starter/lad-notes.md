**1
> search Goblin
Goblin   HP 8   ATK 2   weakness: fire
> search Iron key
 Iron key(wt 0.1, val 0)
> inventory
   1.  Rusty sword       (wt 4.0, val 5)
   2.  Healing potion    (wt 0.5, val 12)
   3.  Iron key          (wt 0.1, val 0)
   4.  Loaf of bread     (wt 0.1, val 1)
   5.  Cloak of shadows  (wt 1.5, val 80)
> inspect 3
  Iron key  (wt 0.1, val 0)
> inspect 99
No such item. (index 98 out of bounds for size 5)
> sort inventory by weight
   1.  Iron key          (wt 0.1, val 0)
   2.  Loaf of bread     (wt 0.1, val 1)
   3.  Healing potion    (wt 0.5, val 12)
   4.  Cloak of shadows  (wt 1.5, val 80)
   5.  Rusty sword       (wt 4.0, val 5)
> benchmark sort 10000
  N=  10000  mergeSort= 100.577 ms  quicksort=   69.978 ms  std::sort=  46.459 ms

**2
[build] C:\Users\emcco\Documents\comp2450\project\floor-03-starter\bestiary\Search.h(73,15): error C2228: left of '.name' must have class/struct/union [C:\Users\emcco\Documents\comp2450\project\floor-03-starter\build\the_descent.vcxproj]
It's telling me what the tem[plete was not made to find strings in int bags. This error looks ridiculous.

**3
The exception allows you to trace the error back in simple terms instead of having to try and read a long traceback

**4
The traceback is so long it's impossible to track the error

**5
std::exception simplifies the error for you, that way you do not need to simplify it yourself.
