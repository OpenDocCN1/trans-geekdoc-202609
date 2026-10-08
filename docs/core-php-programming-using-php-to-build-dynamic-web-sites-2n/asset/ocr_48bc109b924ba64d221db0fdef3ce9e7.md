# Core PHP Programming

The shm_put_var function sets the value for a variable in a shared memory segment. If the variable does not exist, it will be created. The variable will last inside the shared memory until removed with shm_remove_var, or when the shared memory itself is destroyed by shm_remove. The value will be serialized with the same argument used for the serialize function. That means you may use any PHP value or variable—with one exception: at the time of this writing, objects lose their methods when serialized.

boolean shm_remove(integer identifier)

Use shm_remove to free a shared memory segment. All variables in the segment will be destroyed, so it is not strictly necessary to remove them. If you do not remove shared memory segments with this function, they may exist perpetually.

```
<?php
/*
** Shared Memory example 2
**
** This example removes shared memory created
** by the previous shared memory example.
*/

// Define integer for semaphore key
define("SEM_COREPHP", 1970);

// Define integer for shared memory key
define("SHM_COREPHP", 1970);

// Define integer for variable key
define("SHMVAR_MESSAGE", 1970);

//Get or create the semaphore
//This semaphore can be acquired only once
$sem = sem_acquire($SEM_COREPHP, 1);

// acquire semaphore
if(sem_acquire($sem)) {
    // attach to shared memory
    // make the memory 1K in size
    $mem = shm_attach(SHM_COREPHP, 1024);

    // remove variable
    shm_remove_var($mem, SHMVAR_MESSAGE);

    // remove shared memory

```