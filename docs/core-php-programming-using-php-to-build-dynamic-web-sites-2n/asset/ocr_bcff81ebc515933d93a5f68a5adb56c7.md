# integer sem_get(integer key, integer maximum, integer permission)

Use sem_get to receive an identifier for a semaphore. If the semaphore does not exist, it will be created. The optional maximum and permission arguments are used only during creation. The maximum argument controls how many times a semaphore may be acquired. It defaults to 1. The permission argument controls read and write privileges to the semaphore in the same way file permissions do. It defaults to 0x666, which is read and write access for all users. The key argument used to identify the semaphore among processes in the system. The identifier returned by sem_get may be unique each time it is called, even when the same key is specified.

# boolean sem_release(integer identifier)

Use sem_release to reverse the process of the sem_acquire function.

# Shared Memory

PHP offers an extension for using System V shared memory. It follows the same restrictions on the System V semaphore functions, above. That is, your operating system must support this functionality. Solaris, Linux, and AIX are known to work with shared memory.

Shared memory is virtual memory by separate processes. It helps solve the problem of communication between processes running on the same machine. An obvious method might be to write information to a file, but access to permanent storage is relatively slow. Shared memory allows the creation of system memory that may be accessed by multiple processes, which is much faster. Since exclusive use of this memory is essential, you must use some sort of locking. This is usually done with semaphores. If you use the shared memory functions, make sure you support for System V semaphores as well.

A full discussion of the use of shared-memory functions is beyond the scope of this text. I found a short description of shared memory at whatis.com (http://www.whatis.com/). You may parse college courses about operating systems, or Unix Networking by W. Richard Stevens to learn more about shared memory.

The shared memory extension was added to PHP by Christian Cactus.

# integer shm_attach(integer key, integer size, integer permissions)

The shm_attach function returns an identifier to shared memory. The key argument is an integer that specifies the shared memory. The shared memory will be created if