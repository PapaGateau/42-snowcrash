# snow-crash
In a provided Linux ISO, perform a series of flag hunts by exploiting various security vulnerabilities.
This project is an introduction to cyber security.

## Useful commands
- ```find / -user xx -group xx``` search for files owned by a user of group
- ```ls -la``` list all files in directory with detailed information
- ```getfacl``` shows the detailed permissions of a file
- ```ltrace``` shows all dynamic library calls and signals received by a process
- ```gdb``` is a great tool to analyse or manipulate execution flow
- ```ssh``` allows us to have several sessions of a machine's terminal running
- ```scp``` can be used to copy files from and to a virtual machine for inspection
- ```nc``` listen to TCP and UPD connections

## Useful programs
- **VirtualBOX** virtualization tool
- **Wireshark** network protocol analyzer
- [online dissassembler](https://onlinedisassembler.com/odaweb/) executable dissassembly and analysis tool

## Vulnerabilities exploited (see **levelXX/Ressources/** for method)
### level00
Mother of all security vulnerabilities, **the user**!  
His password can be found in a text file that he owns.
### level01
An **unprotected system file** contains the password.  
[etc/passwd format](https://www.cyberciti.biz/faq/understanding-etcpasswd-file-format/)    
[**John the Ripper** decryption tool](https://www.openwall.com/john/
)
### level02
A network packet snapshot that contains the password can be read with **Wireshark**.
### level03
Fake **binary redirection** using environment variables.  
[exploiting setuid binaries](https://www.riccardoancarani.it/exploting-setuid-setgid-binaries/)
### level04
A **CGI perl subroutine with elevated permissions** is running and can receive parameters.   
[perl and CGI](https://www.tutorialspoint.com/perl/perl_cgi.htm)
### level05
Abuse of **wildcard in a cron script** with elevated permissions.  
[cron jobs](https://www.ostechnix.com/a-beginners-guide-to-cron-jobs/)
### level06
Another **wildcard script exploit**, this time with **'e'** regex modifier in a php script.  
[pattern modifiers in php](https://www.php.net/manual/en/reference.pcre.pattern.modifiers.php)
### level07
Weak security based on an **unprotected environment variable**.
### level08
**Hardcoded file name check**, easily circumvented with a dynamic link.
### level09
Encryption method was too basic and easily reverse engineered.
### level10
**access() security hole**
Swapping files between security check and file open to use script elevated permissions
### level11
Running lua task is not protected against **code injection**
### level12
**Wildcard in a perl script** with elevated permissions, albeit more formatting is required
### level13
Executable with elevated permissions is unprotected against **library injections**
### level14
After **dissassembling** an executable we find **unobfuscated strings and functions** that lead us to crucial code. With ```gdb``` we can perform an **jump** and run it.  
[gdb jumping](https://sourceware.org/gdb/onlinedocs/gdb/Jumping.html)
