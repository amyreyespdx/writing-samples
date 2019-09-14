# Technical Writing Sample: Getting Started Guide

*This writing sample is adapted from a Getting Started Guide that I created for an employer. I have removed or modified certain content for brevity and to preserve confidentiality.*

*The original guide was created in XMetaL/SDL Trisoft and published in HTML on the company's website.*

## Getting Started Guide

This guide will show you how to build the required Yocto Project-based image and toolchain.

- [Prerequisites](#Prerequisites)
- [Step 1: Install the Build Host Packages](#step-1-install-the-build-host-packages)
- [Step 2: Build the Image and Toolchain](#step-2-build-the-image-and-toolchain)
- [Step 3: Install the Toolchain](#step-3-install-the-toolchain)

### Prerequisites

You will need a host system that meets the following specifications.

- A [Linux distribution](https://www.yoctoproject.org/docs/2.5.1/ref-manual/ref-manual.html#detailed-supported-distros) that supports Yocto Project.
- Internet access. 
- A minimum of 70GB of free disk space. 
- Recommended: Processor with a minimum of four cores. 
- Recommended: A minimum of 16GB of RAM. 

### Step 1: Install the Build Host Packages

In this step, you will install the build host packages for Yocto Project on your host system. This is a one-time step.

**NOTE** The following command is for Ubuntu and Debian. For updates and commands for other supported Linux distributions, see [Yocto Project Reference Manual](https://www.yoctoproject.org/docs/current/ref-manual/ref-manual.html#required-packages-for-the-build-host).

To install the build host packages, run the following command:

*Ubuntu and Debian*

```
$ sudo apt-get install gawk wget git-core diffstat unzip texinfo gcc-multilib build-essential chrpath socat cpio python python3 python3-pip python3-pexpect xz-utils debianutils iputils-ping libsdl1.2-dev xterm xsltproc docbook-utils dblatex xmlto xutils-dev nfs-common
```
### Step 2: Build the Image and Toolchain

In this step, you will run the provided script on your host system to build a custom Yocto Project-based image and toolchain. 

**NOTE** To build this image, your computer will take anywhere from one half-hour (assuming your computer is a large server) to several hours (assuming your computer is a typical laptop).

1. If you haven't already downloaded the SDK package, go to \<link omitted>.

2. In a terminal window, extract the package. Replace `<version>` as appropriate.
   ```
   tar -xvf package_<version>.tar.gz
   ```

3. Go to the directory containing the extracted files:
   ```
   cd package_<version>
   ```

4. Make the script executable by running the following command. Replace `<version>` as appropriate.
   ```
   chmod +x ./sdk_install_<version>.sh
   ```

5. Run the following command to run the script. For the target argument, specify the desired installation directory — the script will create the directory if it doesn't already exist. Example: `/home/<user>/Desktop/my-files`. The script will do its work in the specified directory.
   ```
   ./sdk_install_<version>.sh --keep --target <installation directory>
   ```

6. Read and accept the license. If the "More" prompt appears in the license, press the Enter key to scroll down until you are prompted to accept. The installer begins.

7. After the installer is finished, confirm that the following items appear in the installation directory:
   - Image: `<installation directory>/build/tmp/deploy/images/image.iso`.
   - Toolchain installation script: `<installation directory>/build/tmp/deploy/sdk/toolchain-script.sh`.

### Step 3: Install the Toolchain

In this step, you will install the toolchain on the host system. You can use the toolchain to build your applications.

1. On the host system, go to the toolchain installation script location. Replace `<installation directory>` with the directory specified in [Step 2: Build the Image and Toolchain](#step-2-build-the-image-and-toolchain).
   ```
   cd <installation directory>/yocto_build/build/tmp/deploy/sdk
   ```
2. Run the following command to install the toolchain. Replace `<toolchain installation directory>` with the desired destination — the script will create the directory if it doesn't already exist. Example: `/home/<user>/Desktop/my-files/toolchain`.
   ```
   ./toolchain-script.sh -d <toolchain installation directory>
   ```

3. To build an application, source the toolchain cross-compile environment. Replace `<toolchain installation directory>` with the directory from the previous step.
   ```
   source <toolchain installation directory>/environment-setup-linux
   ```
    After completing this step, the standard toolchain variables (for example, CC, AR, and LD) now point to the toolchain.

4. As an example, build one of the provided sample applications, `provided_sample`, as follows:
   - Go to the following directory:
      ```
      cd $SDKTARGETSYSROOT/usr/share/samples/provided_sample
      ```
   - Build the sample:
      ```
      make
      ```
