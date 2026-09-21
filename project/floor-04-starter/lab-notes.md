##1
> search Goblin
Goblin   HP 8   ATK 2   weakness: fire
> inventory
   1.  Rusty sword       (wt 4.0, val 5)
   2.  Healing potion    (wt 0.5, val 12)
   3.  Iron key          (wt 0.1, val 0)
   4.  Loaf of bread     (wt 0.1, val 1)
   5.  Cloak of shadows  (wt 1.5, val 80)
> sort inventory by value desc
   1.  Cloak of shadows  (wt 1.5, val 80)
   2.  Healing potion    (wt 0.5, val 12)
   3.  Rusty sword       (wt 4.0, val 5)
   4.  Loaf of bread     (wt 0.1, val 1)
   5.  Iron key          (wt 0.1, val 0)
> inspect 99
No such item. (index 98 out of bounds for size 5)
> log 8
  1. error: index 98 out of bounds for size 5
  2. sort inventory by value desc
  3. inventory ΓÇö listed 5 items
  4. search Goblin ΓÇö found in bestiary
  5. began session as "Ethan"
 (newest first; chain length 5)
> benchmark log 100000
  N= 100000   Chain::push_front =   195.27 ms   Bag::insert(begin) = 23755530.42 ms
> selftest chain
  Chain<int> allocations:  1000   deallocations:  1000   leaked:     0   OK
> quit
The forge cools. The chain dissolves link by link.

##2
> selftest chain
  Chain<int> allocations:  1000   deallocations:     0   leaked:  1000   LEAK ΓÇö implement ~Chain() / clear()

##3
error C2280: 'dungeon::Chain<int>::Chain(const dungeon::Chain<int> &)': attempting to reference a deleted function 
This error is occurring because instead of having a copying constructor we just made it delete the object.

##4
> benchmark log 100000
  N= 100000   Chain::push_front =   195.27 ms   Bag::insert(begin) = 23755530.42 ms
The reason Bag::insert(begin) is so much slower is that the vector must push back ever single element, slowing down the process. push_back simply changes two pointers, making the process much faster.

##5
This is a good decision because when storing monsters there isn't an order that is necessarily better than another. The goal is to just throw a bunch of monsters into a system where you can access each individually, and Bag works great. A Chain for the event log is a good choice because you would want to add events to the very begining of the field, marking them chronologically. Chain is easy to add to the start off, so this is a good choice. If this was swapped then the events would add to the Bag, but it would take AGES. The monsters would also loose the speed of a Bag when it comes to indexing. You have to go through every link of the chain instead of being able to just use the index.
