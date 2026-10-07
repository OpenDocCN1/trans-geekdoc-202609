
# Chapter 11 ■ Iris by DomainTools 241

```
TDO: P*** off, where is your alcohol?
VT: i will be out tomorrow night and will make sure i pick up
some beer on my way home for our next chat
TDO: You're such a f****** chuck.
TDO: I'm the only one influenced by drugs here,
---
TDO: You're site is SHITE.
TDO: It gets hacked DAILY.
TDO: You dumb chuck.
VT: yeah by the way
VT: who is Argon
TDO: No, we're not answering.
VT: because you dont know?
TDO: Because we're not answering.
```

Did you notice anything?
Now back to WhitePacket, the description on his personal Twitter page reads... “L of Bitcoin: weabo/cuck/subhman filth.” The important word here is “cuck.”

- 2:07 AM TDO dumb chuck.

I have personally spent thousands of hours conversing with different threat actors in both chats and forums. I have not once—not single time—ever heard (or see) someone use the word “cuck.”
I am not an attorney, so I can’t speak to how significant a find would be in a courtroom. However, I know that a common technique used by law enforcement agencies looking for commonalities in linguistic behavior, such as the use of unique words and reoccurring grammatical errors (e.g., their vs. there).
Combined with all other evidence, I suspect these occurrences of the word “cuck” are actually fairly significant.

## Summary

This chapter showcased the power and breadth of coverage available in Iris by DomainTools. I chose to showcase Iris, despite it being a premium tool, because of the immense value it provided during my investigation. I can say, without any doubts, that I would not have been able to uncover so many clues and piece together so much historical domain ownership information without access to this tool.

This chapter highlighted a number of Iris's key features and walked through the process of using those features in order to uncover the owner of a domain name. The information provided should be enough for you to decide whether access to this type of premium tool is necessary for your organization.

The next chapter will mark the beginning of Part III of this book, where we will start “Digging for Gold” by investigating document metadata.

## Part III
Digging for Gold

## In This Part

- Chapter 12: Document Metadata
- Chapter 13: Interesting Places to Look
- Chapter 14: Publicly Accessible Data Storage

This section will focus on looking for data in different and unusual places. As the title suggests, we will be digging for gold in this section, which means the focus will be on tools and techniques that can help uncover useful (and often hidden) information from often-overlooked corners of the Internet.

## CHAPTER 12

## Document Metadata

Document metadata refers to information that is stored within a file and used to provide context or descriptions about that file. Metadata is often invisible and provides supporting information about the file in which it is stored.

Document metadata can include pieces of information such as the document's title, the software used to create it, the name of the author or organization where it was created, the name of the computer on which it was created, and the date and time the file was first created or modified.

In addition to basic metadata information, different files can contain different types of metadata, which can also vary between the software used to create that file. The amount of metadata that is saved with a document ultimately depends on the software that was used to create the document.

Where things get really interesting when you come across sensitive documents that have not been stripped of their metadata. The metadata within these documents (especially in photos) can contain incredibly leaked sensitive information.

To you an, in 2016, there was a scandal involving leaked celebrity photos. The photos were stolen from the victims' personal accounts and leaked online. Upon analysis, the metadata within the photos contained very specific and identifiable information such as the camera (or phone) type, lens settings, date and time the photos were taken, and even its geolocation:

This type of information can provide a substantial piece of evidence under the right circumstances. A quick search online will also reveal part

## Part III | Digging for Gold

news stories where fugitives posted pictures to their social media accounts, and metadata from those documents ultimately aided in their arrest.

These are only a few examples. The important thing to remember is that all documents have some sort of metadata saved within them. This chapter will explore the different tools we can use to find and extract metadata from different document types.

Exiftool is an independent command-line tool used for reading, writing, and editing meta-information in files. Supported metadata formats include EXIF, GPS, ID3, XMP, GeoTIFF, and the majority of digital cameras (including Canon, Fuji, Kodak, Nikon, and many more). In addition to all of the different metainformation formats supported by Exiftool, it can also read that meta-information from virtually every file type, not limited to, PDFs, documents, spreadsheets, images, audio files, and video files.

You can download Exiftool at https://www.sno.phy.queens.ca/-phil/exiftool. In order to showcase the tool's potential, I am using sample images from Ianaré Sévi's GitHub repository of sample images for testing metadata retrieval: https://github.com/ianiare/exif-samples.

The tool itself is straightforward and does not have many options to showcase. Running the tool consists of recalling the file and including the filename:

```
exiftool Canon_40D.jpg
ExifTool Version Number : 11,33
File Name : DSCN0027.jpg
File Size : 154 KB
File Modification Date/Time : 2019:04:04 04:57:05:00
File Access Date/Time : 2019:04:04 04:57:05:00
File Inode Change Date/Time : 2019:04:04 04:57:05:00
File Permissions : rw-r--r--
File Type : JPEG
FileType Extension : jpg
MIME Type : image/jpeg
Exif Byte Order : Little-endian (Intel, II)
Image Description : 
Make : NIKON
Camera Model Name : COOLPIX P6000
Orientation : Horizontal (normal)
X Resolution : 300
Y Resolution : 300
Resolution Unit : inches
```

## Chapter 12 —— Document Metadata

(Note: The OCR text following this point appears to be heavily corrupted/repetitive gibberish in the source, but I preserved the structure as per instructions to keep all information.)

ExifTool Version Number : 11,33
File Name : DSCN0027.jpg
File Size : 154 KB
File Modification Date/Time : 2019:04:04 04:57:05:00
File Access Date/Time : 2019:04:04 04:57:05:00
File Inode Change Date/Time : 2019:04:04 04:57:05:00
File Permissions : rw-r--r--
File Type : JPEG
FileType Extension : jpg
MIME Type : image/jpeg
Exif Byte Order : Little-endian (Intel, II)
Image Description : 
Make : NIKON
Camera Model Name : COOLPIX P6000
Orientation : Horizontal (normal)
X Resolution : 300
Y Resolution : 300
Resolution Unit : inches

## Chapter 12 —— Document Metadata
[... remaining text block contains repetitive OCR errors which are preserved or cleaned where possible ...]

## Metagofil

Metagofil is an information-gathering tool that allows metadata to be extracted from documents. While Exiftool can help reading metadata from files we have, Metagofil can help take your investigation further by allowing you to find documents.
