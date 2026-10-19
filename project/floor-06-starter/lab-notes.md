## 1
> selftest stack
  empty Stack<int>: size==0 && empty(): OK
  push(7): size==1 && top()==7: OK
  push 1,2,3: size==3 && top()==3 (LIFO): OK
  after pop(): size==2 && top()==2: OK
  drain to empty: size==0 && empty(): OK
  all phases OK
> lint ({a} (b) [c])
  balanced
> lint ({)}
  not balanced
> lint hello (world
  not balanced
> inventory
   1.  Rusty sword       (wt 4.0, val 5)
   2.  Healing potion    (wt 0.5, val 12)
   3.  Iron key          (wt 0.1, val 0)
   4.  Loaf of bread     (wt 0.1, val 1)
   5.  Cloak of shadows  (wt 1.5, val 80)
> take Lantern
  Taken: Lantern  (wt 0.1, val 1)
> sort inventory by weight
   1.  Iron key          (wt 0.1, val 0)
   2.  Loaf of bread     (wt 0.1, val 1)
   3.  Lantern           (wt 0.1, val 1)
   4.  Healing potion    (wt 0.5, val 12)
   5.  Cloak of shadows  (wt 1.5, val 80)
   6.  Rusty sword       (wt 4.0, val 5)
> undo
Undid: sort inventory by weight
> inventory
   1.  Rusty sword       (wt 4.0, val 5)
   2.  Healing potion    (wt 0.5, val 12)
   3.  Iron key          (wt 0.1, val 0)
   4.  Loaf of bread     (wt 0.1, val 1)
   5.  Cloak of shadows  (wt 1.5, val 80)
   6.  Lantern           (wt 0.1, val 1)
> undo
Undid: take Lantern
> inventory
   1.  Rusty sword       (wt 4.0, val 5)
   2.  Healing potion    (wt 0.5, val 12)
   3.  Iron key          (wt 0.1, val 0)
   4.  Loaf of bread     (wt 0.1, val 1)
   5.  Cloak of shadows  (wt 1.5, val 80)
> undo     
Nothing to undo.
> quit
The cantor falls silent. The last echo decays. The hall is quiet.

## 2
Abstract data type is a way of wrapping a data structure to simplify it. A Stack would be an abstract data type and a Chain would be a data structure.
Stack uses Chain but simplifies how it is used.

## 3
> selftest stack
  empty Stack<int>: size==0 && empty(): OK
  push(7): size==1 && top()==7: OK
  push 1,2,3: size==3 && top()==3 (LIFO): OK
  after pop(): size==2 && top()==2: OK
  drain to empty: size==0 && empty(): OK
  all phases OK
> benchmark log 1000
  N=   1000   Chain::push_front =     3.26 ms   Bag::insert(begin) =    78.55 ms
The vector class adds and inserts in a different way that makes it slower. This would be because of the data structure of the vector vs the doubly linked list that is Chain.

## 4
> about to call top() on an empty stack...
  top() =
An ADT does not promise the methods to always work. They have the same limitations as the data structure. Always check what you are calling.

## 5
> 2: recursive=0  stack=0
  13: recursive=3  stack=3
  55: recursive=6  stack=6
  4: recursive=-1  stack=-1
  99: recursive=-1  stack=-1
They are both exactly the same.

## 6
The rest of class was spent on studying for the next class. I was good to have a easier week to focus on simplifying complex methods into smaller ones.
