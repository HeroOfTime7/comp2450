## 1
> search Goblin
  Goblin   HP 8   ATK 2   weakness: fire
  (found in bestiary)
> search Iron key
  Iron key  (wt 0.1, val 0)
  (found in inventory)
> search began
  began session as "Ethan"
  (found in event log)
> log
   1.  search began — found in event log
   2.  search Iron key — found in inventory
   3.  search Goblin — found in bestiary
   4.  began session as "Ethan"
  (newest first; chain length 4)
> log --oldest 3
   1.  began session as "Ethan"
   2.  search Goblin — found in bestiary
   3.  search Iron key — found in inventory
  (oldest first; chain length 4)
> selftest iterator
  range-for over Chain<int>: OK
  std::find(Chain<int>, 42): OK
  std::distance(begin, end): OK
  range-for over const Chain<int>&: OK
  std::reverse(Chain<int>) — first now == 9: OK
  all phases OK
> quit
  The lens dims. The lens does not remember what it saw — only how it moved.

## 2
> log --oldest 3
   1.  search Goblin — found in bestiary
   (newest first; chain length 5)

## 3
> log
  (the chain is empty ΓÇö nothing to remember yet)
> selftest iterator
  range-for over Chain<int>: FAIL ΓÇö begin == end (stub returns true) ΓÇö implement operator++ and operator==
  std::find(Chain<int>, 42): FAIL ΓÇö std::find returned end() ΓÇö likely operator++ stub or operator== stub
  std::distance(begin, end): FAIL ΓÇö expected 100 ΓÇö got 0 means begin == end immediately (operator== stub)
  range-for over const Chain<int>&: OK
  std::reverse(Chain<int>) ΓÇö first now == 9: FAIL ΓÇö operator-- not yet wired (Friday) ΓÇö std::reverse can't walk back
  (see FAILs above)
This happens because the end is pointing at the beginning, and end must point at the node right after the last, which would be nullptr.

## 4
> 'std::_Sort_unchecked': no matching overloaded function found [C:\Users\emcco\Documents\comp2450\project\floor-05-starter\build\the_descent.vcxproj]
  [build]   (compiling source file '../main.cpp')
  [build]       C:\Program Files (x86)\Microsoft Visual Studio\18\BuildTools\VC\Tools\MSVC\14.51.36231\include\algorithm(9051,19):
  [build]       could be 'void std::_Sort_unchecked(<mark>_RanIt,_RanIt</mark>,iterator_traits<_Iter>::difference_type,_Pr)'
  [build]           C:\Program Files (x86)\Microsoft Visual Studio\18\BuildTools\VC\Tools\MSVC\14.51.36231\include\algorithm(9085,10):
  [build]           'void std::_Sort_unchecked(<mark>_RanIt,_RanIt</mark>,iterator_traits<_Iter>::difference_type,_Pr)': expects 4 arguments - 3 provided
Looks like it needs an policy to see how to sort.

## 5
> for (const auto& s : hero.eventLog) std::cout << s << "\n";
> for (Chain<std::string>::const_iterator it = hero.eventLog.cbegin(); it != hero.eventLog.cend(); ++it) {
    std::cout << *it << "\n";
  }
If would much rather write the first loop. It is much much shorter. I also don't have to change the container when using auto because it detects the change on its own.

## 6
The iterator allows for us to simplify how we navigate the chain, making it easier to access memory. The sword becomes double edged since the iterator only cares about the next item, not traversing the vector.
