## What you need to start
* A PSU account
  * If you are not local, you will need to create a Slim account. Please talk to Paul first before requesting a slim account.
    * https://ics.psu.edu/advanced-cyberinfrastructure/accounts/slim-access-accounts/
  * You must have 2fa setup on your account, which you can do at https://2fa.psu.edu/
* A CSE account
  * [Eric, how do they create a CSE account if they are not CSE students? What if they are temporary visitors that need access to the server?]
* An ACI account (only needed to access archive storage)
* The AnyConnect VPN client, installed on the machine you plan to connect to the server with.
  * You can get the VPN client by going to https://vpn.cse.psu.edu. They will need to put in your CSE user id and password and for "second password" enter either  "phone" or a duo number provided by your phone.

## Connecting to the server

* The name of the server is CSE-P112MEDG01. 
* To access it you must first be on the CSE VPN. Then, you can just type `ssh CSE-P112MEDG01`
* Documentation on the VPN available while on the CSE network here https://www.cse.psu.edu/it/documentation/vpn.  Unfortunately without being on the CSE network it cannot be accessed.
  

## Archival storage: 
* Not mounted on server, but data can be moved there using methods below.
* The host name for accessing the storage is: datamgr.aci.ics.psu.edu
* The directory of our data is /archive/pzm11/default
* You (and any of your collaborators) can sign up for accounts at: https://accounts.aci.ics.psu.edu/acipriv
* If you have issues or questions just submit a ticket to our i-ASK center: https://iask.aci.ics.psu.edu
* To access the data, you have various options:
  * lftp sftp://user@datamgr.aci.ics.psu.edu:22 <applewebdata://A275D139-EFAC-4822-A3E0-FBC240CD66BF> -e 'mirror --verbose --use-pget-n=8 -c /remote/path /local/path'
    * sftp:// = uses SFTP protocol
    * mirror = mirror mode
    * verbose = shows the files being downloaded
    * use-pget-n = number of segments, realy useful to speed up big files
    * parallel = downloads multiplier files at the same time
    * if you want to download files in parallel switch out use-pget-n=8 with --parallel=8


  * Parallel rsync: http://www.linuxproblem.org/art_9.html <http://www.linuxproblem.org/art_9.html>
    * prsync /home/source /home/target target.machine.psu.edu <http://stratus.met.psu.edu/> 8
    * (8 is number of threads)

  * Python based Parallel Rsync: https://code.google.com/archive/p/parallel-ssh/ or more directly https://storage.googleapis.com/google-code-archive-downloads/v2/code.google.com/parallel-ssh/pssh-2.3.1.tar.gz which is the tarball with the appropriate code source. The man page is here: https://www.mankier.com/1/prsync

* Keep in mind the the first connection to that machine via ssh (sftp, lftp, etc) will prompt you for a DUO token 
connection.


## Windows manager

OSX or linux users can open a shell with X forwarding using  `ssh -X CSE-P112MEDG01`

If using windows, they will need the Xserver. I have found xming to be a decent one that works well with winssh. Both xming and fonts are needed.
* http://sourceforge.net/projects/xming/files/Xming/6.9.0.31/Xming-6-9-0-31-setup.exe/download
( http://sourceforge.net/projects/xming/files/Xming-fonts/7.7.0.10/Xming-fonts-7-7-0-10-setup.exe/download

After having all of those..

     Windows.

         Open WinSSH and go to settings and find the "Forward X 
connections" and check the box. Save settings.

         Connect vpn to vpn.cse.psu.edu   using your CSE User id and 
password.

         ssh  to the hostname      CSE-P112MEDG01

         It will prompt for duo 2 factor id.

         Once received it will prompt for PSU Access Account Password 
(not cse)

