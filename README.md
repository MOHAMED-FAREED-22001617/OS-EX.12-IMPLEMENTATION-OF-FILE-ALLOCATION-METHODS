# OS-EX.12-IMPLEMENTATION-OF-FILE-ALLOCATION-METHODS

## AIM:
To implement file management using sequential list.

## ALGORITHM:
Step 1: Start the program.

Step 2: Get the number of memory partition and their sizes.

Step 3: Get the number of processes and values of block size for each process.

Step 4: First fit algorithm searches all the entire memory block until a hole which is big enough is encountered. It allocates that memory block for the requesting process.

Step 5: Best-fit algorithm searches the memory blocks for the smallest hole which can be allocated to requesting process and allocates it.

Step 6: Worst fit algorithm searches the memory blocks for the largest hole and allocates it to the process.

Step 7: Analyses all the three memory management techniques and display the best algorithm which utilizes the memory resources effectively and efficiently.

Step 8: Stop the program.

## PROGRAM:
```
#include < stdio.h>
#include<conio.h>
void main()
{
int f[50], i, st, len, j, c, k, count = 0;
clrscr();
for(i=0;i<50;i++)
f[i]=0;
printf("Files Allocated are : \n");
x: count=0;
printf(“Enter starting block and length of files: ”);
scanf("%d%d", &st,&len);
for(k=st;k<(st+len);k++)
if(f[k]==0)
count++;
if(len==count)
{
for(j=st;j<(st+len);j++)
if(f[j]==0)
{
f[j]=1;
printf("%d\t%d\n",j,f[j]);
}
if(j!=(st+len-1))
printf(” The file is allocated to disk\n");
}
else
printf(” The file is not allocated \n");
printf("Do you want to enter more file(Yes - 1/No - 0)");
scanf("%d", &c);
if(c==1)
goto x;
else
exit();
getch();
}
```

## OUTPUT:
![image](https://github.com/Thirukaalathessvarar-S/OS-EX.12-IMPLEMENTATION-OF-FILE-ALLOCATION-METHODS/assets/121166390/8df6dd8d-948b-401c-be09-642096cea935)

## RESULT:
Thus, file management using sequential list is implemented successfully.


# LINKED ALLOCATION

## AIM
To implement file management using indexed list.

## DESCRIPTION:
1.Linked allocation solves all problems of contiguous allocation. With linked allocation, each file is a linked list of disk blocks; the disk blocks may be scattered anywhere on the disk. The directory contains a pointer to the first and last blocks of the file.

2.Each block contains a pointer to the next block. These pointers are not made available to the user. Thus, if each block is 512 bytes, and a disk address (the pointer) requires 4 bytes, then the user sees blocks of 508bytes.

3.To create a new file, we simply create a new entry in the directory. With linked allocation, each directory entry has a pointer to the first disk block of thefile.

4.This pointer is initialized to nil (the end-of-list pointer value) to signify an empty file. The size field is also set to 0. A write to the file causes a free block to be found via the free-space-management system, and this new block is then written to, and is linked to the end of thefile.

5.To read a file, we simply read blocks by following the pointers from block to block. There is no external fragmentation with linked allocation, and any free blockon the free-space list can be used to satisfy arequest.

6.The size of a file does not need to be declared when that file is created. A file can continue to grow as long as free blocks areavailable.

7.Consequently, it is never necessary to compact diskspace.

## PROGRAM
```
#include<stdio.h>
int main()
{
int n,m[20],i,j,ib[20],b[20][20];
printf("Enter no. of files:");
scanf("%d",&n);
for(i=0;i<n;i++)
{ 
printf("Enter index block :",i+1); 
scanf("%d",&ib[i]);
printf("Enter blocks occupied by file%d:",i+1); 
scanf("%d",&m[i]);
printf("enter blocks of file%d:",i+1); 
for(j=0;j<m[i];j++) 
scanf("%d",&b[i][j]);
} printf("\nFile\t index\tlength\n"); 
for(i=0;i<n;i++) 
printf("%d\t%d\t%d\n",i+1,ib[i],m[i]); 
printf("blocks occupiedare:"); 
for(i=0;i<n;i++)
{ printf("fileno%d",i+1);
for(j=0;j<m[i];j++)
printf("\t%d--->%d\n",ib[i],b[i][j]);
printf("\n");
}
}
```

## OUTPUT
![image](https://github.com/Thirukaalathessvarar-S/OS-EX.12-IMPLEMENTATION-OF-FILE-ALLOCATION-METHODS/assets/121166390/e501e45a-0dfd-43ca-8c0d-180ca1bf03a0)

## RESULT
Thus, file management using linked list is implemented successfully.
