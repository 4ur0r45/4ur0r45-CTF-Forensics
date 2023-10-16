# [PicoCTF Forensics] information
## Intro
![](https://hackmd.io/_uploads/HJOvZzq-6.jpg)

[Link to chall](https://play.picoctf.org/practice/challenge/186?category=4&originalEvent=34&page=1)

This challenge give you a image and want you to find Flag ignored in the image.


## Overview 
First, I used `file` command:
![](https://hackmd.io/_uploads/ryBzVf9ba.png)
It is a jpeg file.

I used `strings` command but also didn't find any special string.

I clicked on the file to view it.
But i can't find anything it just a normal cat.

After, I researched it by HxD:
![](https://hackmd.io/_uploads/HJnkrf9WT.png)
`JFIF` means `jpeg`

I think this is a normal jpeg file.

## Metadata
I researched on Google and it is known that it is related to `metadata`
[Metadata](https://www.creativeforce.io/blog/image-meta-tags-explained-beginner-to-expert-guide)

## Solution
I used `exiftool cat.jpg`:
```
ExifTool Version Number         : 12.40
File Name                       : cat.jpg
Directory                       : .
File Size                       : 858 KiB
File Modification Date/Time     : 2023:10:13 20:18:05+07:00
File Access Date/Time           : 2023:10:16 08:41:38+07:00
File Inode Change Date/Time     : 2023:10:13 20:18:05+07:00
File Permissions                : -rwxrwxrwx
File Type                       : JPEG
File Type Extension             : jpg
MIME Type                       : image/jpeg
JFIF Version                    : 1.02
Resolution Unit                 : None
X Resolution                    : 1
Y Resolution                    : 1
Current IPTC Digest             : 7a78f3d9cfb1ce42ab5a3aa30573d617
Copyright Notice                : PicoCTF
Application Record Version      : 4
XMP Toolkit                     : Image::ExifTool 10.80
License                         : cGljb0NURnt0aGVfbTN0YWRhdGFfMXNfbW9kaWZpZWR9
Rights                          : PicoCTF
Image Width                     : 2560
Image Height                    : 1598
Encoding Process                : Baseline DCT, Huffman coding
Bits Per Sample                 : 8
Color Components                : 3
Y Cb Cr Sub Sampling            : YCbCr4:2:0 (2 2)
Image Size                      : 2560x1598
Megapixels                      : 4.1    
```
`License                         : cGljb0NURnt0aGVfbTN0YWRhdGFfMXNfbW9kaWZpZWR9`
I decode by [CyberChef](https://cyberchef.org/) decode from base64 `cGljb0NURnt0aGVfbTN0YWRhdGFfMXNfbW9kaWZpZWR9`

Yeah, I found!

## Flag
`picoCTF{the_m3tadata_1s_modified}`