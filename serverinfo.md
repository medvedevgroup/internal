## What you need to start
* A PSU Access Account 
  * If you are not local, you will need to create a Slim account. Please talk to Paul first before requesting a slim account.
    * https://ics.psu.edu/advanced-cyberinfrastructure/accounts/slim-access-accounts/
  * You must have two factor authorization setup on your account, which you can do at https://2fa.psu.edu/
* A CSE account
  * If you're a CSE grad student, you automatically have a CSE account. You can check with helpdesk@cse.psu.edu, if you are not sure. To create an account, please work with Paul to complete the form https://github.com/medvedevgroup/internal/blob/master/CSEAccount%20Form.v2.pdf and submit it to helpdesk@cse.psu.edu. A "Dept. or School Officer Signature" is not needed for a student or person affiliated with Penn State (i.e. Visiting Scholar, Post Doc, etc.) 
* An account on the server. Please email helpdesk@cse.psu.edu and CC Paul to create one.
* An ACI account (only needed to access archive storage)
  * Sign up for an account at https://accounts.aci.ics.psu.edu/acipriv. You must already have a PSU Access Account.
* The AnyConnect VPN client, installed on the machine you plan to connect to the server with.
  * You can get the VPN client by going to https://vpn.cse.psu.edu. They will need to put in your CSE user id and password and for "second password" enter either  "phone" or a duo number provided by your phone.
  * More information on the VPN is available at https://www.cse.psu.edu/it/documentation/vpn. Unfortunately, you need to be on the VPN to access this information.

## Connecting to the server

* The name of the server is CSE-P112MEDG01. 
* To access it you must first be on the CSE VPN. You will need your CSE credentials for this.
* After you are on the VPN, you can ssh into the host `CSE-P112MEDG01`
* Your username/password are your PSU access account.
  

## Archival storage: 
* Not mounted on server, but data can be moved there using methods below.
* The host name for accessing the storage is: datamgr.aci.ics.psu.edu
* The directory of our data is /archive/pzm11/default

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

## Help
* To get help regarding CSE accounts, email helpdesk@cse.psu.edu from your CSE account.
* To get help regarding the archival storage or the ACI accounts, submit a ticket to the i-ASK center: https://iask.aci.ics.psu.edu


## Windows manager
In order to run X windows programs (i.e. non-terminal) programs, you need an X client installed. OSX or Linux users already have an X client and you can open a shell with X forwarding using  `ssh -X CSE-P112MEDG01`. This will allow you to run X windows programs from the server. 

If using Windows, you will need the Xserver. I have found xming to be a decent one that works well with winssh. Both xming and fonts are needed.
* http://sourceforge.net/projects/xming/files/Xming/6.9.0.31/Xming-6-9-0-31-setup.exe/download
* http://sourceforge.net/projects/xming/files/Xming-fonts/7.7.0.10/Xming-fonts-7-7-0-10-setup.exe/download

After having all of those, then 
* Open WinSSH and go to settings and find the "Forward X connections" and check the box. Save settings.
* Connect vpn to vpn.cse.psu.edu.
* ssh to the host CSE-P112MEDG01
