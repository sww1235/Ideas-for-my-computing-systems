## Build processes

Have Gold, Build and Compile server(s). Gold acts as director, build manages
build processes and built images, and compile does the actual compilation of
binaries and kernels.

-   Create a basic disk image for \[linux|bsd\] with a basic root
hirarchy (/root /bin /dev /proc /usr /home) as empty directories for
mountpoints.
-   Copy master blank disk image for each individual machine. (snapshots? when?)
-   Compile kernel using specific kernel flags for each machine / use case and
copy to proper location on /boot of disk image.
-   Compile/copy 
