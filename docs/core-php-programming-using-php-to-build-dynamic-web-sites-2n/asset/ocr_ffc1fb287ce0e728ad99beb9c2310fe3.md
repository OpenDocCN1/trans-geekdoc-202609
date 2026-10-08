Core PHP Programming

```
shm_remove($mem);

//release semaphore
sem_release($sem);
}
else {

//we failed to acquire the semaphore
print("Failed to acquire semaphore! <BR\n");
}
?>
```

# boolean shm_remove_var(integer identifier, integer key)

The shm_remove_var function frees the memory associated with a variable within a shared memory segment.

# SNMP

SNMP, the Simple Network Management Protocol, is a protocol for Internet management. It was first described in RFC 1089. One place to start learning about SNMP is SNMP Research at < http://www.snmp.com/>. To use functions under UNIX, you must use the UCD SNMP libraries. You can find them at <http://ucd-snmp.ucdavis.edu/>. Documentation at this site is more specific to the library PHP uses. I have attempted to follow their examples by translating them into equivalent PHP code.

Mike Jackson, Rasmus Lerdorf, and Steven Lawrence have contributed to the SNMP extension.

# boolean snmp_get_quick_print()

The snmp_get_quick_print function returns the status of the UCD SNMP library's quick_print status. Consequently, this function is unavailable to Windows users. The quick_print setting controls how verbose object values are. By default, quick_print is FALSE, and values include types and other information. The UCD SNMP manual provides more information.

IT-SC book

504