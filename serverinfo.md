## What you need to start
* A PSU Access Account 
  * If you are not local, you will need to create a Slim account. Please talk to Paul first before requesting a slim account.
    * https://ics.psu.edu/advanced-cyberinfrastructure/accounts/slim-access-accounts/
  * You must have two factor authorization setup on your account, which you can do at https://2fa.psu.edu/
* An account on the server. Please email csehelpdesk@engr.psu.edu and CC Paul to create one.
* An ACI account 
  * Only needed to access archive storage. If you are not sure if you need this, then just skip it.
  * Sign up for an account at https://accounts.aci.ics.psu.edu/acipriv. You must already have a PSU Access Account.
* The GlobalProtect VPN client, installed on the machine you plan to connect to the server with.
  * You can get the VPN client by going to https://pennstate.service-now.com/sp?id=kb_article_view&sysparm_article=KB0013431&sys_kb_id=16d424b6db11f8107fb5266e139619c3&spa=1


## Connecting to the server

* Connect to PSU VPN using GlobalProtect VPN client
  * The portal address is Secure-connect.psu.edu.
  * You will need to do 2fa at this stage
* ssh into the host `cse-cbmedg01.psu.edu`
  * You will need to do 2fa at this stage
  * Your username/password are your PSU access account.

## Using the server
* Your home directory has a 2 Gb quota. Use it to to store anything that you want backed up daily. For example,
  * Your code
  * Small data files
* Use `/resesarch/<username>/` for other storage. It is NOT backed up.
* Use archival storage as a way to backup data more than 2 Gb (NOTE: As of 8/2/2021, archival storage is no longer available):
  * We have storage that is located outside the server. This is called archival storage. It is not mounted on our  server. To access the storage, see below.
  * Use archival storage to copy over data that is more permanent in nature. Archival storage is not only an alternate location for your data, it itself is backed up regularly by ACI. For example, any datasets from old papers that you want to preserve can be copied to archival storage when the project is stable. 
* Please use the slack channel "server" to communicate regarding day-to-day use.
* It is recommended that you use version control for your code, e.g. GitHub. If you are a member of the [medvedevgroup](https://github.com/medvedevgroup/) GitHub org, you can have unlimited private repos
* If you have data that more than 2 Gb that you would like to backup, your best option is to use archival storage to store it (see below).


## Accessing archival storage: 
<!-- Archival storage resides on `datamgr.aci.ics.psu.edu`, and the directory of our data is /archive/pzm11/default. To access the data, here are some options suggested by IT staff: 
* `lftp sftp://user@datamgr.aci.ics.psu.edu:22 <applewebdata://A275D139-EFAC-4822-A3E0-FBC240CD66BF> -e 'mirror --verbose --use-pget-n=8 -c /remote/path /local/path'`
* [Parallel rsync](https://www.mankier.com/1/prsync)
  * https://code.google.com/archive/p/parallel-ssh/  -->

Archival storage resides on `Globus` and inside `Penn State ICDS Archive` collection, and the directory of our data is  `/storage/archive/pzm11/default`. To access the data, here are some options:

* Use the Globus web interface to transfer files
  * https://www.globus.org/
  * You will need to sign into Globus account using your PSU email address
  * You will need to connect to the Penn State ICDS Archive collection

* Download and install Globus Connect Personal ([see here](https://docs.globus.org/globus-connect-personal/install/linux/)) from your profile  on our server
* While running the program in the terminal, you can access our server from `Globus`. Our server endpoint is `e5-cse-cbmedg01` and  the archival storage endpoint is `Penn State ICDS Archive`.
* After you have connected to the endpoints, you can archive files in `/storage/archive/pzm11/default/`.

## Help
* Use the server channel on slack as a first point for questions that you think other lab members might have encounetered.
* To get help regarding the archival storage or the ACI accounts, submit a ticket to the i-ASK center: https://iask.aci.ics.psu.edu
* For other help, contact csehelpdesk@engr.psu.edu
