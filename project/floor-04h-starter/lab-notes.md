##1
> search Goblin
Goblin   HP 8   ATK 2   weakness: fire
> inventory
   1.  Rusty sword       (wt 4.0, val 5)
   2.  Healing potion    (wt 0.5, val 12)
   3.  Iron key          (wt 0.1, val 0)
   4.  Loaf of bread     (wt 0.1, val 1)
   5.  Cloak of shadows  (wt 1.5, val 80)
> inspect 99
No such item. (index 98 out of bounds for size 5)
> log --oldest 5
  1. began session as "Ethan"
  2. search Goblin ΓÇö found in bestiary
  3. inventory ΓÇö listed 5 items
  4. error: index 98 out of bounds for size 5
oldest first; chain length 4.
> clone hero 
  -- original log (newest first) --
   1.  error: index 98 out of bounds for size 5
   2.  inventory ΓÇö listed 5 items
   3.  search Goblin ΓÇö found in bestiary
   4.  began session as "Ethan"
  (newest first; chain length 4)
  -- cloned log (newest first) --
   1.  error: index 98 out of bounds for size 5
   2.  inventory ΓÇö listed 5 items
   3.  search Goblin ΓÇö found in bestiary
   4.  began session as "Ethan"
  (newest first; chain length 4)
  (clone is being destroyed now)
  (clone destroyed; original event log still has 4 entries ΓÇö try `log 3`)
> log 3
   1.  clone hero ΓÇö copy lived and died
   2.  error: index 98 out of bounds for size 5
   3.  inventory ΓÇö listed 5 items
  (newest first; chain length 5)
> selftest chain
  Phase 1 (single chain)
    allocations:  1000   deallocations:  1000   leaked:     0   OK
  Phase 2 (deep copy)
    original after copy died ΓÇö forward walk:  1000   backward walk:  1000
    copy before death        ΓÇö forward walk:  1000   backward walk:  1000
    allocations:  2000   deallocations:  2000   leaked:     0   OK
> quit
The forge cools. Two chains dissolve, each by its own hand.

##2
There is no code like this listed.

##3
I did not get an error message, but my code immediately exited.

##4
Chain& operator=(const Chain& other) {
  Chain tmp(other);
  swap(tmp);
  return *this;
}

Chain& operator=(const Chain& other) {
  if (this == &other) return *this;
  clear();
  for (const Node* p = other.head_; p; p = p->next) {
    push_back(p->data);
  }
  return *this;
}

I would rather use the first function. Its so much shorter!

##5
You would have to iterate over the entire list to then assign the last element a tail to nullptr. This means you iterate over the list twice.

##6
The rule of three is when you implement a destructor, a copy constructor, and a copy assignment operator. Rule of zero is when you define none of these special operators. Chain would not qualify because we define all three of the memory functions.
