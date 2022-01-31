## Reverse Engineering Embedded Device Firmware - koi0x


This write-up will focus on the process of reverse engineering an embedded device's binary firmware file that uses OpenWrt. A few notes to begin, as always, I am going to keep this write-up short and to the point. I will also not discuss which device or manufacturer this device comes from or any related info out of privacy respect. This write-up is purely for educational purposes only. Let's get started.

### Basic Reconnaissance 

Firstly, we need to gather basic information before anything else, so we have a base to work with. We have our bin (Renamed from the original name) in our working directory. Let's go ahead and run the strings command against the file to see if we can get any interesting strings returned. You can see that there was a mention of OpenWrt Linux-3.10.14 just by running the strings command against it. That is vital information for us. I blurred out the other string references as they mentioned the product. 

![image](https://user-images.githubusercontent.com/95584654/151872853-398a9151-61d5-4e09-a936-26e907b3d129.png)

This next step is optional, but you can also run the file command against it to see if you can pull down any information. In the case of this firmware, we do not get anything. The following steps will be using the tool binwalk to gather more information regarding the file. When working with firmware, it's always good practice to check the file's entropy as well. You can do this by using binwalk with the tac -E option. 

Let's move on to the primary process now. Let's go ahead and walk the file using binwalk by running the command "binwalk firmware.bin". You can also see by doing this; we are also returned with OpenWrt information. So given the information that we have, we can extract the file system by also using binwalk. Note: Doing this will not always be this easy; however, this write-up focuses on the fundamentals.

![image](https://user-images.githubusercontent.com/95584654/151874435-b8436ba8-631f-4a6c-b2f1-71a2d11402fc.png)

### Extracting Filesystem

We are now moving on to extracting the filesystem from the bin file. Once again, we can use binwalk with the tac option -Me to extract it. This option will recursively scan for extracted files and then extract them to a separate directory. Give it a bit of time, and you should start to see all of the files being extracted from the cpio archive in this case and or whatever you are working with. 

![image](https://user-images.githubusercontent.com/95584654/151876328-ebd9c1d1-d18d-4822-a355-d7bd6974c1f0.png)

You can now see that we have fully extracted the underlying file system of the embedded device. You can now view source code, binary files, and scripts that make the device work. This marks the end of the write-up.

![image](https://user-images.githubusercontent.com/95584654/151876724-c3930214-7e22-4655-9ca3-226f1f043736.png)

### Closing Notes

Again, this is a very basic fundamental write-up on the topic of reverse engineering firmware. There is a lot more to it, and I plan to create more write-up's as time goes on and I learn more. It can be enjoyable to reverse these kinds of things to get a better understanding of how they work, but it also opens up the ability to be able to conduct ethical vulnerability research on these devices. I hope you were able to learn something. Thanks for reading. 




