
Colorado State University 	
Basic FTP Commands

What is FTP?

The FTP (File Transfer Protocol) utility program is commonly used for copying files to and from other computers. These computers may be at the same site or at different sites thousands of miles apart. FTP is a general protocol that works on UNIX systems as well as a variety of other (non-UNIX) systems. 

For the purposes of this Web page, the local machine refers to the machine you are initially logged into, the one on which you type the ftp command. The remote machine is the other one, the one that is the argument of the ftp command. 

A user interface for the standard File Transfer Protocol for ARPANET, FTP acts as an interpreter on the remote machine. The user may type a number of UNIX-like commands under this interpreter to perform desired actions on the remote machine. 

Most operating systems and communication programs now include some form of an FTP utility program, but the commands differ slightly between them. The following explanations and alphabetical list of commands refers to the common FTP utility program as provided on a UNIX machine. Check the documentation for your own machine to determine the comparable commands.

Most computers today include a windows-based type FTP program that is more PC-oriented and does not require full knowledge of these commands.
You can also perform FTP through a browser. For example, bring up Internet Explorer and type in
            ftp://yourLoginName@IPaddress

instead of a normal web page URL. 

The FTP site of the Computer Science department at CSU requires the user to use sftp, the secure version of FTP. Just type sftp instead of ftp, when you are using FTP in a terminal window. 

Getting Started

To connect your local machine to the remote machine, type
            ftp machinename

where machinename is the full machine name of the remote machine, e.g., purcell.cs.colostate.edu. If the name of the machine is unknown, you may type

            ftp machinennumber

where machinennumber is the net address of the remote machine, e.g., 129.82.45.181. In either case, this command is similar to logging onto the remote machine. If the remote machine has been reached successfully, FTP responds by asking for a loginname and password.

When you enter your own loginname and password for the remote machine, it returns the prompt
            ftp>

and permits you access to your own home directory on the remote machine. You should be able to move around in your own directory and to copy files to and from your local machine using the FTP interface commands given on the following page.

Anonymous FTP

At times you may wish to copy files from a remote machine on which you do not have a loginname. This can be done using anonymous FTP.
When the remote machine asks for your loginname, you should type in the word anonymous. Instead of a password, you should enter your own electronic mail address. This allows the remote site to keep records of the anonymous FTP requests.
Once you have been logged in, you are in the anonymous directory for the remote machine. This usually contains a number of public files and directories. Again you should be able to move around in these directories. However, you are only able to copy the files from the remote machine to your own local machine; you are not able to write on the remote machine or to delete any files there.
Common FTP Commands

?	to request help or information about the FTP commands
ascii	to set the mode of file transfer to ASCII 
(this is the default and transmits seven bits per character)
binary	to set the mode of file transfer to binary 
(the binary mode transmits all eight bits per byte and thus provides less chance of a transmission error and must be used to transmit files other than ASCII files)
bye	to exit the FTP environment (same as quit)
cd	to change directory on the remote machine
close	to terminate a connection with another computer
 	close brubeck	 closes the current FTP connection with brubeck, 
  but still leaves you within the FTP environment.
delete	to delete (remove) a file in the current remote directory (same as rm in UNIX)
get	to copy one file from the remote machine to the local machine
 	get ABC DEF	 copies file ABC in the current remote directory to (or on top of) a file named DEF in your current local directory.
 	get ABC	 copies file ABC in the current remote directory to (or on top of) a file with the same name, ABC, in your current local directory.
help	to request a list of all available FTP commands
lcd	to change directory on your local machine (same as UNIX cd)
ls	to list the names of the files in the current remote directory
mkdir	to make a new directory within the current remote directory
mget	to copy multiple files from the remote machine to the local machine; 
  you are prompted for a y/n answer before transferring each file
 	mget *	 copies all the files in the current remote directory to your current local directory, using the same filenames. Notice the use of the wild card character, *.
mput	to copy multiple files from the local machine to the remote machine; 
  you are prompted for a y/n answer before transferring each file
open	to open a connection with another computer
 	open brubeck	 opens a new FTP connection with brubeck; 
  you must enter a username and password for a brubeck account 
      (unless it is to be an anonymous connection).
put	to copy one file from the local machine to the remote machine
pwd	to find out the pathname of the current directory on the remote machine
quit	to exit the FTP environment (same as bye)
rmdir	to to remove (delete) a directory in the current remote directory
Further Information

Many other interface commands are available. Also FTP can be run with different options. Please refer to your manual or the UNIX man page on ftp for more information.
Example Sessions

Examples of two FTP sessions are given on the next two pages. These show the type of interaction you may expect when using the ftp utility.

Example of Anonymous FTP Session

%   ftp cs.colorado.edu  
Connected to cs.colorado.edu.  
220 bruno FTP server (SunOS 4.1) ready.  
Name (cs.colorado.edu:yourlogin): anonymous  
331 Guest login ok, send ident as password.  
Password:  
230-This server is courtesy of Sun Microsystems, Inc.  
230-  
230-The data on this FTP server can be searched and accessed via WAIS, using  
230-our Essence semantic indexing system.  Users can pick up a copy of the  
230-WAIS ".src" file for accessing this service by anonymous FTP from  
230-ftp.cs.colorado.edu, in pub/cs/distribs/essence/aftp-cs-colorado-edu.src  
230-This file also describes where to get the prototype source code and a  
230-paper about this system.  
230-  
230-  
230 Guest login ok, access restrictions apply.  
ftp> cd /pub/HPSC  
250 CWD command successful.  
ftp> ls  
200 PORT command successful.  
150 ASCII data connection for /bin/ls (128.138.242.10,3133) (0 bytes).  
ElementsofAVS.ps.Z  
   . . .
execsumm_tr.ps.Z  
viShortRef.ps.Z  
226 ASCII Transfer complete.  
418 bytes received in 0.043 seconds (9.5 Kbytes/s)  
ftp> get README  
200 PORT command successful.  
150 ASCII data connection for README (128.138.242.10,3134) (2881 bytes).  
226 ASCII Transfer complete.  
local: README remote: README  
2939 bytes received in 0.066 seconds (43 Kbytes/s)  
ftp> bye  
221 Goodbye.  
%   ls  
   . . .
README    
   . . .
An FTP session to obtain the HPSC README file from the cs.colorado.edu anonymous ftp directory using a loginname of anonymous and a password of one's own electronic mail address.

Example of Regular FTP Session

%   ftp nordsieck.cs.colorado.edu  
Connected to nordsieck.cs.colorado.edu.  
220 nordsieck FTP server (Version 5.53 Tue Aug 25 10:46:12 MDT 1992) ready.  
Name (nordsieck.cs.colorado.edu:yourlogin): yourlogin  
331 Password required for yourlogin.  
Password:  
230 User yourlogin logged in.  
ftp> cd HPSC/exercises  
250 CWD command successful.  
ftp> ls  
200 PORT command successful.  
550 No files found.  
ftp> put tmul.out  
200 PORT command successful.  
150 Opening ASCII mode data connection for tmul.out.  
226 Transfer complete.  
local: tmul.out remote: tmul.out  
1882 bytes sent in 0.0095 seconds (1.9e+02 Kbytes/s)  
ftp> ls  
200 PORT command successful.  
150 Opening ASCII mode data connection for file list.  
tmul.out  
226 Transfer complete.  
9 bytes received in 0.0021 seconds (4.3 Kbytes/s)  
ftp> mput *  
mput Makefile? y  
200 PORT command successful.  
150 Opening ASCII mode data connection for Makefile.  
226 Transfer complete.  
local: Makefile remote: Makefile  
1020 bytes sent in 0.0062 seconds (1.6e+02 Kbytes/s)  
mput tmul.out? n  
ftp> quit  
221 Goodbye.  
%   ls  
   . . .
Makefile    
tmul.out    
   . . .
An FTP session to copy files from a remote machine back to nordsieck.cs.colorado.edu using one's own login and password.

Comments: 

