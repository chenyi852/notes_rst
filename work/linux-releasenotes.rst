linux release notes
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

6.3
===========

内存
-----------

#. folios changes

   内核引入page folio的目的是为了明确内存操作。当前内核多个页称为复合页，compoud
   page。每个base page是由page struct来表示的。如果是复合页，通过在第一个page的
   page struct打上特殊的标记，从而明确这是复合页，所以其他pages('tail pages')
   也被标记出来了。
   tail page可以很容易根据page struct找到复合页的page struct，那么问题来了，如
   果函数传来一个指向tail page的参数，那么是要此函数在这个tail page上执行，还是
   要在整个复合页上执行。
   定义folio是就是明确指向的是整个复合页。而不需要通过**compound_head**来获取
   指向head page的指针。这个函数执行时间相对较少，但是由于此函数是个inline函数
   且被多次调用，因此会占用内核的镜像体积。
