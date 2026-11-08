## 1
> selftest balance
  balanceFactor: empty==0, bushy==0, left-leaning==1: OK
  isBalanced: bushy {5,3,8,2,4,7,9} balanced (true): OK
  degenerate: sorted stick {1..6} is NOT balanced (height 5): OK
  rotate: rotateRootLeft on {1,2,3} -> root 2, height 1, order kept: OK
  balanceRoot: right- and left-heavy sticks both rebalance (order kept): OK
  all phases OK
> balance
  McCown's catalogue: 15 names, height 6, root balance factor -3 ΓÇö NOT balanced (lopsided).
> benchmark balance

-- Same sorted input: your plain BST vs std::set (1000 iterations per cell) --
  N=     10  plain BST: height=     9  find=    1.683 us    std::set: find=   1.335 us
  N=    100  plain BST: height=    99  find=    9.364 us    std::set: find=   2.314 us
  N=   1000  plain BST: height=   999  find=   65.221 us    std::set: find=   1.244 us

Same data, same order. Inserted in sorted order, your plain BST
degenerated into a stick of height N-1 ΓÇö lookup is back to O(n).
std::set saw the identical input and stayed shallow: it is a
balanced tree (a red-black tree) that rotates on every insert to
hold its height near log2 N. You do not hand-write that balancing ΓÇö
you reach for std::set / std::map. That is the next floor, the
Hall of Names.

> quit
McCown notes your departure. "You leave in order."

## 2
A balanced tree in this example means we only have to check half the nodes.

## 3
It is still valid because 3 is less than 5 and 8 is greater than 5.

## 4
It is still unbalanced because 3 is the root but has 1 and 2 as left branches. A real AVL tree would rotate 3 and than 1.

## 5
> benchmark balance

-- Same sorted input: your plain BST vs std::set (1000 iterations per cell) --
  N=     10  plain BST: height=     9  find=    1.683 us    std::set: find=   1.335 us
  N=    100  plain BST: height=    99  find=    9.364 us    std::set: find=   2.314 us
  N=   1000  plain BST: height=   999  find=   65.221 us    std::set: find=   1.244 us

The only way std::set was able to stay short is that it would rotate to stay short. The plain BST just got really long.

## 6
The way std::set and std::map are made they a superior when it comes to efficacy. They wrote code in ways that are simpler and faster than what I wrote, so I should use their code. Always rely on your peers!
