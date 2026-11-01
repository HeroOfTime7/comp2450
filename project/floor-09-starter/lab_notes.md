## 1
> selftest bst
  empty BST<int>: empty() && size==0 && height==0: OK
  insert: root==5 and size==7 over the sample: OK
  contains: 7 and 2 present, 6 and 404 absent: OK
  inOrder == {2,3,4,5,7,8,9} (ascending): OK
  degenerate: sorted inserts give height==5, not balanced: OK
  deep copy: mutating the original leaves the copy unchanged: OK
  remove: leaf(2), one-child(3), two-children(5) all correct: OK
  all phases OK
> catalogue
Bone Spider   HP 6   ATK 2   weakness: fire
Cave Troll   HP 28   ATK 7   weakness: fire
Cinder Bat   HP 4   ATK 1   weakness: water
Frostmaw   HP 22   ATK 6   weakness: fire
Goblin   HP 8   ATK 2   weakness: fire
Ironclaw Bear   HP 24   ATK 5   weakness: slashing
Lich   HP 35   ATK 6   weakness: holy
Marsh Lurker   HP 18   ATK 3   weakness: fire
Necrothrall   HP 16   ATK 4   weakness: light
Ratking   HP 9   ATK 2   weakness: fire
Shadow Hound   HP 12   ATK 4   weakness: light
Skeleton   HP 10   ATK 3   weakness: blunt
Stone Sentinel   HP 30   ATK 5   weakness: blunt
Wisp   HP 3   ATK 1   weakness: holy
Wraith   HP 14   ATK 4   weakness: holy
  (15 creatures, alphabetical; tree height 6)
> recall Lich
Lich   HP 35   ATK 6   weakness: holy
  (recalled from the tree)
> recall Skeleton
Skeleton   HP 10   ATK 3   weakness: blunt
  (recalled from the tree)
> recall Wisp
Wisp   HP 3   ATK 1   weakness: holy
  (recalled from the tree)
> forget Goblin
  McCown strikes 'Goblin' from the tree. (14 remain.)
> benchmark bst

-- Bestiary: linear scan vs BST lookup (1000 iterations per cell) --
  N=    100  query=last    linear=     3.267 us  BST=     0.402 us  (tree height 13)
  N=    100  query=absent  linear=     2.380 us  BST=     0.501 us  (tree height 13)
  N=   1000  query=last    linear=    22.840 us  BST=     0.806 us  (tree height 22)
  N=   1000  query=absent  linear=    13.350 us  BST=     0.648 us  (tree height 22)
  N=  10000  query=last    linear=   214.053 us  BST=     0.854 us  (tree height 30)
  N=  10000  query=absent  linear=   148.690 us  BST=     0.925 us  (tree height 30)
  N= 100000  query=last    linear=  2214.774 us  BST=     0.630 us  (tree height 40)
  N= 100000  query=absent  linear=  1354.665 us  BST=     0.576 us  (tree height 40)

Linear scan grows with N; BST lookup grows with log N ΓÇö the same
win binary search gave you on Floor 1, but now the structure STAYS
searchable as you insert and remove, with no re-sort step.
One catch: this tree was built from SHUFFLED data. Insert the
monsters already sorted and the BST degenerates into a stick
(height ~N), and lookup drops right back to linear ΓÇö the problem
the next floor's self-balancing tree exists to solve.

> quit
McCown notes your departure. "You leave in order."

## 2
The most nodes you look through will be the height of the tree.

## 3
If you do it in this order than you will always sort by ascending. Left is always the smallest, and right is always the largest.

## 4
14 would move to be the root because 10 is removed. This keeps the tree in order because the left is still smaller than the root node.

## 5
  N=    100  query=last    linear=     2.493 us  BST=     0.416 us  (tree height 13)
  N=    100  query=absent  linear=     1.303 us  BST=     0.284 us  (tree height 13)
  N=   1000  query=last    linear=    28.884 us  BST=     0.829 us  (tree height 22)
  N=   1000  query=absent  linear=    14.859 us  BST=     0.669 us  (tree height 22)
  N=  10000  query=last    linear=   272.985 us  BST=     0.845 us  (tree height 30)
  N=  10000  query=absent  linear=   176.498 us  BST=     0.884 us  (tree height 30)
  N= 100000  query=last    linear=  2626.504 us  BST=     0.662 us  (tree height 40)
  N= 100000  query=absent  linear=  1762.562 us  BST=     0.817 us  (tree height 40)

The height of the tree would have been the same as the number of monsters inputted. This means the tree would basiclly be a linked list.

## 6
It made it very easy to search. There is a very simple algorithm that allows me to search the entire BST quickly, witch is much better than the Tree we made. However, removing items is harder because you need to premote the correct node to allow the BST to work.
