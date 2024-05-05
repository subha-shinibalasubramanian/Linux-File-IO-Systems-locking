**Ex:07**  
# Linux-File-IO-Systems-locking
**DATE:**
# AIM:
To Write a C program that illustrates files copying and locking

# DESIGN STEPS:

### Step 1:

Navigate to any Linux environment installed on the system or installed inside a virtual environment like virtual box/vmware or online linux JSLinux (https://bellard.org/jslinux/vm.html?url=alpine-x86.cfg&mem=192) or docker.

### Step 2:

Write the C Program using Linux IO Systems locking

### Step 3:

Execute the C Program for the desired output. 

# PROGRAM:
**NAME:SUBHASHINI.B**   
**REGISTER NUMBER:212223040211**  

## 1.To Write a C program that illustrates files copying 
```c
#include <sys/stat.h>
#include <fcntl.h>
#include <stdlib.h>
int main()
{
char block[1024];
int in, out;
int nread;
in = open("filecopy.c", O_RDONLY);
out = open("file.out", O_WRONLY|O_CREAT, S_IRUSR|S_IWUSR);
while((nread = read(in,block,sizeof(block))) > 0)
write(out,block,nread);
exit(0);}
```





## 2.To Write a C program that illustrates files locking
```c
#include <fcntl.h>
#include <stdio.h>
#include <string.h>
#include <unistd.h>
#include <sys/file.h>
int main (int argc, char* argv[])
{ char* file = argv[1];
 int fd;
 struct flock lock;
 printf ("opening %s\n", file);
 /* Open a file descriptor to the file. */
 fd = open (file, O_WRONLY);
// acquire shared lock
if (flock(fd, LOCK_SH) == -1) {
    printf("error");
}else
{printf("Acquiring shared lock using flock");
}
getchar();
// non-atomically upgrade to exclusive lock
// do it in non-blocking mode, i.e. fail if can't upgrade immediately
if (flock(fd, LOCK_EX | LOCK_NB) == -1) {
    printf("error");
}else
{printf("Acquiring exclusive lock using flock");}
getchar();
// release lock
// lock is also released automatically when close() is called or process exits
if (flock(fd, LOCK_UN) == -1) {
    printf("error");
}else{
printf("unlocking");
}
getchar();
close (fd);
return 0;
}

```



# OUTPUT
## C program that illustrates files copying
![Screenshot from 2024-04-30 10-39-56](https://github.com/shivsujan/Linux-File-IO-Systems-locking/assets/145633245/bebfc9f4-d20f-46e1-bf0b-7d5a439b2eea)



## C program that illustrates files locking

![Screenshot from 2024-04-30 10-43-51](https://github.com/shivsujan/Linux-File-IO-Systems-locking/assets/145633245/46738263-a92d-48e1-84ed-2fd056f31c5c)



# RESULT:
The programs are executed successfully.
