## 1
> selftest registry
  index: size==5, distinct weaknesses==3, count[holy]==3: OK
  knows: Lich present, Drake absent: OK
  recall: Wraith->hp==14, Drake==nullptr: OK
  hasWeakness: holy present, water absent: OK
  countWeakness: holy==3, water==0: OK
  forget: drop a shared weakness (count--), drop a last weakness (erased), absent==false: OK
  all phases OK
> knows Lich
  McCown knows 'Lich'.
> knows Drake
  McCown does not know 'Drake'.
> weaknesses
  blunt  (2 monsters)
  fire  (6 monsters)
  holy  (3 monsters)
  light  (2 monsters)
  slashing  (1 monsters)
  water  (1 monsters)
  (6 distinct weaknesses)
> lookup Lich
Lich   HP 35   ATK 6   weakness: holy
  (looked up in the Registry)
> weakness fire
  6 monsters fear fire.
> names
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
  (15 names, alphabetical ΓÇö std::map keeps them ordered)
> strike Goblin
  Struck 'Goblin' from the Hall of Names. (14 remain.)
> recall Goblin
Goblin   HP 8   ATK 2   weakness: fire
  (recalled from the tree)
> benchmark names

-- The Hall of Names: linear scan vs BST vs std::map (1000 iterations per cell) --
  N=    100  query=last    linear=     3.022 us  BST=   0.398 us  std::map=   1.224 us  (tree height 13)
  N=    100  query=absent  linear=     1.677 us  BST=   0.292 us  std::map=   0.911 us  (tree height 13)
  N=   1000  query=last    linear=    23.591 us  BST=   0.632 us  std::map=   1.265 us  (tree height 22)
  N=   1000  query=absent  linear=    13.043 us  BST=   0.583 us  std::map=   1.067 us  (tree height 22)
  N=  10000  query=last    linear=   204.162 us  BST=   0.795 us  std::map=   1.518 us  (tree height 30)
  N=  10000  query=absent  linear=   162.292 us  BST=   0.701 us  std::map=   1.831 us  (tree height 30)
  N= 100000  query=last    linear=  2106.280 us  BST=   0.553 us  std::map=   2.005 us  (tree height 40)
  N= 100000  query=absent  linear=  1317.972 us  BST=   0.564 us  std::map=   1.810 us  (tree height 40)

std::map::find tracks the BST ΓÇö both grow with log N, both crush
the linear scan. The difference is the code: the BST was a class you
wrote across a whole floor; std::map was one declaration. And unlike
your plain BST, std::map is balanced (a red-black tree), so it NEVER
degenerates into a stick ΓÇö the library gives you the balanced tree of
Floor 9┬╜ and a key->value index on top of it, for free.

> quit
McCown notes your departure. "You leave in order."

## 2
a. byName_.count(name) > 0;
b. byName_.find(name).attack;
c. weaknesses_.count(w) > 0;
d. auto it = weaknessCounts_.find(w);
When you want to find only unique items.

## 3
The reason they are sorted is because std::map is a self-balancing tree. We built an BST which was similar. Zombie would be hidden because it would be on the wrong side of the tree.

## 4
One thing I gained is that writing std::map was much easier, however one thing I lost would be that BST is much faster.

## 5
error C2678: binary '[': no operator found which takes a left-hand operand of type 'const std::map<std::string,int,std::less<std::string>,std::allocator<std::pair<const std::string,int>>>' (or there is no acceptable conversion)
a. it would return null right?
b. this is a type conversion you cannot do.

## 6
All we did was remove the name, not the node from the tree.
This is not a bug because we still want to access some data.

## 7
The command I first think of is find() which uses the self-balancing tree just as it was intended. The thing is, when using the command count() you don't need a self-balancing tree. I think having the self-balancing tree is nice, because it makes it simple on our end, so I would keep it.
