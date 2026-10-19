## 1
> selftest queue
  empty Queue<int>: size==0 && empty(): OK
  enqueue(7): size==1 && front()==7: OK
  enqueue 1,2,3: size==3 && front()==1 (FIFO): OK
  after dequeue(): size==2 && front()==2: OK
  drain to empty: size==0 && empty(): OK
  all phases OK
> potato A B C D E 3
  Survivor: D
> potato Gric Skrit Quill Vael Resh 2
  Survivor: Quill
> potato OnlyOne 7
  Survivor: OnlyOne
> provoke Goblin
  Goblin takes a number and joins the line.
> provoke Skeleton
  Skeleton takes a number and joins the line.
> provoke Imp
  Imp takes a number and joins the line.
> simulate
  Turn 1: Goblin stirs in the dark.
  Turn 2: Skeleton stirs in the dark.
  Turn 3: Imp stirs in the dark.
All enemies have acted; the line is empty.
> simulate
No enemies are in line. Use `provoke <name>` first.
> quit
Quill stamps your ticket. The line shuffles forward by one.

## 2
### Stack<T>
add an item (push / enqueue)
> chain.push_front()
remove an item (pop / dequeue)
> chain.pop_front()
read the next item out (top / front)
> chain.head()->data
### Queue<T>
add an item (push / enqueue)
> chain.push_back()
remove an item (pop / dequeue)
> chain.pop_front()
read the next item out (top / front)
> chain.head()->data

## 3
> potato A B C D E 3
  Survivor: A
> selftest queue
  empty Queue<int>: size==0 && empty(): OK
  enqueue(7): size==1 && front()==7: OK
  enqueue 1,2,3: size==3 && front()==1 (FIFO): FAIL ΓÇö front() did not return the FIRST enqueued value ΓÇö enqueue/front are on the same end (that's a stack, not a queue)
  after dequeue(): size==2 && front()==2: OK
  drain to empty: size==0 && empty(): OK
  (see FAILs above)

What I actually built was a Stack.

## 4
start:               A B C D
rotate:              B C D A
eliminate:           C D A
rotate:              D A C
eliminate:           A C
rotate:              C A
eliminate:           A
survivor:            A
I got the same result from running it.

## 5
The concept was easier to grip once I understood that we created the same thing twice. The only difference was that we were swapping the background methods. All of this connects to Chain in a different way, so it's easy once you write Chain.
