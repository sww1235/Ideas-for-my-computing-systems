
## Ideal requirements
-   Local source code repository
-   Local compilation (w/ cluster)
-   have both push and pull installation capabilities
-   provide normal package manager funtionality (ideally completely transparent
    to end user, but allowing for package restriction)
-   show what software is installed on an individual or group of machines
-   show where an individual piece of software is installed
-   provide dependancy management
-   allow for kernel upgrading and compiling (even on a machine specific basis)
-   potentially provide for multiple kernel types (bsd/linux) in one system
-   have integration with versioning and upgrade mechanisms for prebuilt distros
    -   have cache for most common distributions
    -   can detect if prebuilt distributions need updates (pfsense, freeNAS) and
        apply them
