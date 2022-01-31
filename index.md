## Reverse Engineering Embedded Device Firmware - koi0x


This write-up will focus on the process of reverse engineering an embedded device's binary firmware file that uses OpenWrt. A few notes to begin, as always, I am going to keep this write-up short and to the point. I will also not discuss which device or manufacturer this device comes from or any related info out of privacy respect. This write-up is purely for educational purposes only. Let's get started.

### Basic Reconnaissance 

Firstly, we need to gather basic information before anything else, so we have a base to work with. We have our bin (Renamed from the original name) in our working directory. Let's go ahead and run the strings command against the file to see if we can get any interesting strings returned. You can see that there was a mention of OpenWrt Linux-3.10.14 just by running the strings command against it. That is vital information for us. I blurred out the other string references as they mentioned the product. 

![image](https://user-images.githubusercontent.com/95584654/151872853-398a9151-61d5-4e09-a936-26e907b3d129.png)

This next step is optional, but you can also run the file command against it to see if you can pull down any information. In the case of this firmware, we do not get anything. The following steps will be using the tool binwalk to gather more information regarding the file. When working with firmware, it's always good practice to check the file's entropy as well. You can do this by using binwalk with the tac -E option. 

Let's move on to the primary process now. Let's go ahead and walk the file using binwalk by running the command "binwalk firmware.bin". You can also see by doing this; we are also returned with OpenWrt information. So given the information that we have, we can extract the file system by also using binwalk. Note: Doing will not always be this easy; however, this write-up focuses on the fundamentals.

![image](https://user-images.githubusercontent.com/95584654/151874435-b8436ba8-631f-4a6c-b2f1-71a2d11402fc.png)


```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [Basic writing and formatting syntax](https://docs.github.com/en/github/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/Koi0x/Reverse-Engineering-Embedded-Device-Firmware/settings/pages). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://docs.github.com/categories/github-pages-basics/) or [contact support](https://support.github.com/contact) and we’ll help you sort it out.
