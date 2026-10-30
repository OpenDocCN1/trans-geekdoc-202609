operating system. These are important pieces of information. There is also a link to the actual vulnerability that is being exploited.

The real work happens in the def exploit section. Notice the first new statement make_nops. This function is part of Metasploit and generates a nop sled of a supplied length and returns it to the caller. That begs the question, what is a nop sled? Sometimes called a nop slide, this is a sequence of no-operation sequences sent to the CPU to basically slide the CPU’s execution flow to the destination in memory that the attacker wants. This is a common technique in malware and other exploits.

So basically, junk data is combined with the nop sled and sent to the socket. If all goes well, and the target is vulnerable, this will cause a buffer overflow. This is a brief exploit, but one that is easy to follow. You should study this exploit carefully before moving forward.

# Extending Existing Exploits

The exploit that follows is rather basic. It tries to send a buffer to a remote IMAP. While it is simple, there is much to understand in this exploit. First, read through the code, then we will cover the key items.

```
```ruby
require 'msf/core'

class Exploit1 < Msf::Auxiliary
  include Msf::Exploit::Remote::Imap
  include Msf::Auxiliary::Dos

  #basic metasploit description
  def initialize
    super(
      'Name' => 'Basic test for IMAP',
      'Description' =>'A basic IMAP test.'
      'Author'     => [ 'open' ],
    )
    end

  #generate a random text which will be sent
  def rannum
    return Rex::Text.rand_text_alphanumeric(rand(1024))
  end

  def run
  srand(0)

  #get connected. If not connected, tell the user and exit
  #if connected send a random buffer
```
```