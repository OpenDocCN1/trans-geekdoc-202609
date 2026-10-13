
I highly recommend enabling write block whenever examining artifacts. This prevents you from making changes during your investigation. Remember that even the slightest change will change the hash value of the artifact you are investigating!

Now that you have an idea of what static analysis is, next let’s look at how to recover data from a powered-off system.

### Recovering Data

The most basic goal of a digital forensic investigation is to recover data. A common misconception among computer users is that when they delete data, it is erased from the computer and can’t be retrieved; in fact, they are just telling the computer that the space occupied by the deleted data is now available, and the data is not removed until something is written over it. Many hard drives use a first-in, last-out approach, meaning deleted data won’t be overwritten until all other space runs out. Consequently, old data can linger as long as a few years before new data is written over it. I have run recovery software on old USB drives of mine and recovered hundreds of files that I deleted years earlier.

I spoke at DEFCON about my research on this topic a few years ago. I had matched the publicly posted social media handles of HR employees in various organizations with the handles of sellers on eBay. My hypothesis was that HR employees were selling used computers holding extremely sensitive data on eBay but were not following proper data deletion protocols, allowing buyers to acquire the systems and recover sensitive data. Any time I saw one of these eBay sellers list a hard drive or a printer with a hard drive, I purchased it with the intent to investigate whether I could recover extremely sensitive information from it. Sure enough, I collected driver’s license information, passport details, documents labeled classified, and much more from printer hard drives, scanner hard drives, and external media, all sold on eBay. Think about devices such as scanners used for scanning sensitive data, IoT devices that collect data about users, cameras used for conference calls or security, USB drives that are shared with employees, and all of the other drives that have collected data that can reveal all sorts of details about their environment and associated users.

One simple way to recover data is to use a free open-source tool called Foremost. One great feature about Foremost is that it will automatically identify all files within a target location and organize them by file type. You can run Foremost by using the command `foremost -t all -t -I <location to scan> -o <where to send what is found>` against any hard drive that is connected to your forensic laptop. [Figure 8-33](#ch08.xhtml#ch08fig33) is an example of running Foremost on a USB drive found at `/dev/sdb1` and outputting the results to a folder located at `/root/Desktop/recover/`.

![FIGURE 8-33 Example Running Foremost](Images/08fig33.jpg)

**FIGURE 8-33** Example Running Foremost

[Figure 8-34](#ch08.xhtml#ch08fig34) shows the output from the previous run command. Notice all the nice folders; any matching file formats will be placed in their corresponding folder. Many commercial programs do the same thing but include fancy GUIs and are marketed as the solution for when you delete something by accident and need to recover it. My advice is to just use a free option such as Foremost that does a fantastic job of locating any lost data and collecting it in a nice file library.

![FIGURE 8-34 Example Foremost Output](Images/08fig34.jpg)

**FIGURE 8-34** Example Foremost Output

> **Note**
>
> To properly delete or destroy the data on a hard drive, either physically destroy the hard drive (recommended approach) or use a write program that writes over the entire hard drive with 0s and 1s.

### Forensic Dynamic Analysis

*Dynamic analysis* in digital forensics refers to analyzing a target system that is running (powered on). Do not shut off a target system that is powered on; not only because it changes the state of the system but also because you will lose any volatile data. *Volatile data* is data that is not saved but is used while the system is running. Common places to find volatile data include registries, cache, and RAM. Why care about volatile data? Remember that even encrypted data must at some point be unencrypted in order to be processed by the system. Also think about how your system remembers your user history to make life “easier” for you. This is the type of data that sits in a volatile state and can be collected with the right tools and techniques.

Some examples of volatile data you can find on running systems (and will lose if you turn off the systems) include the following:

*   Running processes
*   Unencrypted data
*   Passwords in clear text
*   Who is logged in
*   Instant messages
*   Attached devices
*   Executed console commands
*   System information
*   IP addresses
*   Registry information
*   Trojan horses
*   Open ports and listening applications

#### Volatility

One tool you can use to view volatile data in RAM is Volatility. You will need to first dump RAM from a running system—a program such as DumpIT allows you to dump a copy of a running Windows RAM. If you don’t know the type of RAM you are working with, you can use the command `volatility-2.5.standalone.exe –f <mem dump file.raw> imageinfo` to get a fingerprint of the type data you are working with. You will need to figure out the offset of the memory, which you can find by running the command `volatility-2.5.standalone.exe –f <mem dump file.raw> --profile= <suggested profile> kdbgscan`. With the offset, you can identify what processes are running on the system by using the command `volatility-2.5.standalone.exe –f <mem dump file.raw> --profile= <suggested profile> --kdbg= <off set> pslist`, as shown in [Figure 8-35](#ch08.xhtml#ch08fig35).

![FIGURE 8-35 Finding Processes in RAM Using Volatility](Images/08fig35.jpg)

**FIGURE 8-35** Finding Processes in RAM Using Volatility

You can also recover hash dumps with Volatility to see password hashes, as shown in [Figure 8-36](#ch08.xhtml#ch08fig36). This is useful for running against password rainbow tables to recover passwords.

![FIGURE 8-36 Dumping Hashes Using Volatility](Images/08fig36.jpg)

**FIGURE 8-36** Dumping Hashes Using Volatility

If you can get access to the RAM of a terminal server, running the `cmdscan` option allows you to see all commands that have been run. Imagine all of the sensitive information you can recover with that history file, including admin passwords, critical IP addresses, and so much more! [Figure 8-37](#ch08.xhtml#ch08fig37) shows an example of running Volatility to access this info.

![FIGURE 8-37 Dumping Command-Line History Using Volatility](Images/08fig37.jpg)

**FIGURE 8-37** Dumping Command-Line History Using Volatility

One last Volatility example is pulling the history of what websites were accessed regardless of the browser being used. The command ends with `iehistory`, but it will dump the history of all browser usage, not just Internet Explorer. [Figure 8-38](#ch08.xhtml#ch08fig38) shows how that command looks in Volatility.

![FIGURE 8-38 Dumping Browser History Using Volatility](Images/08fig38.jpg)

**FIGURE 8-38** Dumping Browser History Using Volatility

### Digital Forensics Summary

The examples presented in the previous sections provide just a glimpse into what can be pulled from a running system; active systems are a gold mine if you can keep them powered on while investigating them. You do not want to investigate the live system; however, you can pull dumps of the live data, mark the time of dump, and investigate the dump without impacting the original system.
