# Producer-Consumer-Problem
Implemented the Semaphore Solution to the classic Producer-Consumer Problem inside the linux kernel.

## 📝 Testing the Modifications
    
<br>

Apply the patch file to the stock kernel<br>
Run the makefile <br>
run the command <br>

    ./p and ./c in different terminals

Kill the both the processes (using control + C) and then run the below command to check the kernel logs

    sudo dmesg -c

```p``` is the producer which enqueues in the queue and ```c``` is the consumer which dequeues from the queue.

<br>

## ⚙️ Modifying the Kernel 

### syscall_64.tbl
    
    Added the name of syscalls writer and reader and their syscall numbers

### sys.c

    Added semaphore headerfiles
    
    Added the definition of the syscalls writer and reader.
    
    Added Global Variables head, tail, semaphores, circQueue pointer, size of queue.
<br>

## ✍🏻 writer

    This is used by the producer to enqueue elements into the queue. 

## 📖 reader

    This is used by the consumer to dequeue elements from the queue

## 🔒 Use of Semaphores
    Semaphore sem1 = N : Counting Semaphore, Number of empty slots in buffer, this will be the size of the queue
    
    Semaphore sem2 = 0 : Counting Semaphore, Number of slots filled
    
    Semaphore s3 : Mutex, used to provide mutual exclusion to the reader and writer calls

## 🔢 Random Values in Producer

    refer to getRand() function defined in Producer.
    
    Read an 8 byte number into a character buffer from /dev/urandom

    Convert that character buffer to an unsigned long long using bitwise manipulation

## 💻 For more details:
  [Write Up](https://github.com/abhik-s-basu/Producer-Consumer-Problem/blob/main/writeup_ass4.pdf)
