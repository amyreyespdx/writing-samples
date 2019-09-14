# Sample: Getting Started Guide

This sample is adapted from a Getting Started Guide that I created for an employer. The original guide was created in XMetaL and published in HTML on the company's website. I have removed or modified certain content to preserve confidentiality.


## SDK Getting Started Guide

This guide will show you how to install and begin working with the SDK. Your development environment will consist of a host computer and a target device. You will use the SDK to develop and build your application on the host computer and then you will run the application on the target. The target device needs a custom Yocto* image to support the application. The SDK download package contains an installer script that builds the image for you. The installer also builds the recommended Yocto toolchain. 

### Prerequisites

You will need a host computer and target device that meet the following specifications.

| Device            | Specifications 
| ----------------- |----------------------------------------------------------------------------------------| 
| Host computer     | In order for the provided installer to build the custom Yocto image and toolchain, you need a Linux* machine that meets the following requirements: | 
| Target device     | centered      |
| 



A Linux* distribution that supports Yocto Project.
Internet access.
A minimum of 70GB of free disk space.
Recommended: Processor with a minimum of four cores.
Recommended: A minimum of 16GB of RAM.
A USB drive that you can use as a bootable drive. You will use the drive to install the Yocto image on the target device. Note: When you create the bootable USB drive, the existing contents of the drive will be overwritten.

A minimum of 8GB.
High-quality USB3 drives are highly recommended for fast flashing.
Connection to the local network to copy code samples from the host computer to the target device.
