malloc-free
===========
mem.h/mem.c contain the main functions that allocates and frees memory space. 
Mem_Alloc() is similar to the library function malloc(). Mem_Alloc takes as a parameter the size in bytes of the object to be allocated, 
and returns a pointer to the start of that object.  If there is not enough contiguous free space within sizeOfRegion allocated by 
Mem_Init to fulfill the request NULL is returned.  Mem_Alloc() returns 4-byte aligned chunks of memory.  Mem_Malloc() starts at
the begining of the memory and allocates the first free block which can accommodate the requested size.
Mem_Free() takes in a pointer and frees the memory object that it points to. If  the pointer was not allocated by Mem_Alloc(), or 
the pointer is NULL Mem_Free() will return -1.  If it successfully frees the memory 0 is returned.  Mem_Free() coalesces if one or 
both of the immediate neighbours are free.

The top level Makefile will produce libmem.so from mem.h/mem.c.  In order to run any tests a current version of libmem.so needs 
to be in the tests directory.

The tests directory contains different scenarios or Mem_Alloc() and Mem_Free().  To see current statistics of the memory place
Mem_Dump(); into the test file.  En example is coalesce6.c.
To compile the tests directory, use Makefile in that directory.
testlist.txt explains all tests in the tests directory.

All files are compiled using: gcc -Wall -m32 -O