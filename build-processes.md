## Build processes

Have Gold, Build/deploy and Compile server(s). Gold acts as director,
build/deploy manages build processes and built images and also acts as tftp
server for pxelinux/other solution and host for complete disk images, and
compile does the actual compilation of binaries and kernels.

### New machine or significant upgrade

#### Before imaging machine - can be completed at any time
-   Create a basic disk image for \[linux|bsd\] with a basic root
hirarchy (/root /bin /dev /proc /usr /home) as empty directories for
mountpoints. (filesystem?)
-   Copy master blank disk image for each individual machine. (snapshots? when?)
-   Compile kernel using specific kernel flags for each machine / use case and
copy to proper location on /boot of disk image.
-   Compile/copy necessary binaries to proper locations on disk image.
-   Create grub and /etc/fstab files based on knowledge of specific machine.
Somehow have the ability to autocreate /etc/fstab for machine-local disks.
-   Further host specific setup, /etc/hostname, networking settings, etc.

#### After imaging host
-   Use deployment solution to copy disk image to local disk of target machine.
-   Script setup of specific services, users, ssh keys, RBAC etc.
-   Test services (done by build server) and connection to other servers on
network.

### Existing machine - minor update

#### Kernel upgrade

-   Compile new kernel version
-   Send request to server to reboot. Wait for ack
-   On ack, change grub settings of remote machine to boot to tftp environment
and force reboot remote machine.
-   Verify that remote machine has come back up and is connected to tftp server.
If not request manual intervention.
-   Copy new kernel files to appropriate locations on remote machine
-   Change grub config to use new kernel and to boot back to local machine.
-   Add script that contacts build server if system comes back up and makes it
through boot. If not request manual intervention or somehow remote connect to
server to grab log files / change grub back?
-   Torture remote system to verify stability
-   Take snapshot of local disk image of remote machine and perform same changes
on local image.

#### Other software update

-   Compile/Copy new binary using machine specific versions/flags when necessary
-   If software replacement requires reboot then
    -   Send request to server to reboot. Wait for ack
    -   On ack, change grub settings of remote machine to boot to tftp
    environment and force reboot remote machine.
    -   Verify that remote machine has come back up and is connected to tftp
    server. If not request manual intervention.
-   Else then stop all services using binary and prevent new services from
starting.
-   Copy binaries to appropriate locations, replacing old binaries but making
sure a backup of old binary exists on build server. (hashing and timestamp etc.)
-   Test new binary (from build server)
-   Take snapshot of local disk image of remote machine and perform same changes
on local image.

### Restoring existing image

-   Send request to server to reboot. Wait for ack
-   On ack, change grub settings of remote machine to boot to tftp environment
and force reboot remote machine.
-   Verify that remote machine has come back up and is connected to tftp server.
If not request manual intervention.
-   Image machine with appropriate image
-   Verify machine comes back up
-   Torture remote system to verify stability
