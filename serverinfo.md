Archival storage: 
* Not mounted on server, but data can be moved there using methods below.
* The host name for accessing the storage is: datamgr.aci.ics.psu.edu
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

 
 
