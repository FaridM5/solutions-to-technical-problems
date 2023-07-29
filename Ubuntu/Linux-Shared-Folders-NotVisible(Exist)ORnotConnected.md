# Linux Shared Folders are NotVisible (Exist) or not Connected 
<i></i>
<b></b>
## Detailed Issue Description:
The shared folder is created on the host machine. In virtual machine, the directory is not visible to the user. Even if created manually, it is not connected directly to the host.

## Prerequisite:
You should have activated your "Shared Folder" in your VM.
<br> For VMware Workstation Player:
  - Open the VM
  - Among Virtual Machine list, select your VM and go to <i>Settings</i>
  - In Options section, there is <i>Shared Folders</i>
  - Turn <i>Folder sharing</i> mode to <i>Always enabled</i>
  - In the <i>Folders</i> section on bottom, select the directory where you will put your files in your host machine to be accessible by your VM
  - OK

## Solution:
(Open terminal)

  - <b>sudo nano /etc/fstab</b>
<br> -Opens the editor to have our own entry in the <i>/etc/fstab</i> file
<br>

  - <b>vmhgfs-fuse /mnt/hgfs fuse defaults,allow_other 0 0</b>
<br> - Write down this entry to the file editor to define how a specific filesystem should be mounted in Linux.
<br> - After writing, just press <i>Ctrl+O</i> - to write out & <i>Ctrl+X</i> - to exit from the editor.
<br>

  - <b>sudo mkdir /mnt/hgfs</b>
<br> - Creates related directory where we will get the files from our host machine
<br>

  - <b>sudo mount -a</b>
<br> - It will mount the shared folders to the specified mount point.

## Result:
The shared folders will be accessible in the Linux guest operating system under the <i>/mnt/hgfs</i> directory.

