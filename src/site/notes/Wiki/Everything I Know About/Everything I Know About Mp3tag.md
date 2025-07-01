---
dg-publish: true
dg-created: Jan 19, 2022, 11:46 PM
---

# Pastor Anderson Sermons

## Use Regular Expressions

Select all the files you wish to modify, right-click, and choose `Actions (Quick) > Replace with Regular Expression`.

![](https://i.imgur.com/qPOlHzY.png)

![](https://i.imgur.com/xyfhA35.png)


Example:

```
Pattern: (\d\d)(\d\d)(\d\d)(.)
Replace: $1-$2-20$3 \U$4M -
```

`010514a - Love One Another` becomes `01-05-2014 AM - Love One Another`.

![](https://i.imgur.com/l4wOJ3I.png)

## Add sequential numbers to the filename

Tag - Filename: `$num(%_counter%,3) - %_filename%`

![](https://i.imgur.com/JbTBqNL.png)


## Add Metadata

Plex will pickup metadata that is written to the properties of MP4 files, such as Title, Date, Comment, etc.

HOWEVER. The process of tagging MP4s can be [very slow if they exist on a NAS](https://community.mp3tag.de/t/an-observation-regarding-tag-values-and-performance-speeds/61562) or external drive. I moved them from the NAS to local drive and voilà, it's as fast as mp3 tagging. So the difference is the NAS vs. local drive.

| Operation      | Field         | Pattern                                                                                                              |
| -------------- | ------------- | -------------------------------------------------------------------------------------------------------------------- |
| Filename - Tag |               | `%track% - %month%-%day%-%year% %time% - %title%`                                                                    |
| Tag - Tag      | Comment       | `Preached by Pastor Steven Anderson at Faithful Word Baptist Church on %month%/%day%/%year% for the %time% service.` |
| Tag - Tag      | Media created | `%month%/%day%/%year%` See [[Wiki/Everything I Know About/Everything I Know About exiftool#Add "Media created" Tag\|exiftool]].                   |

![](https://i.imgur.com/HM7474R.png)
![](https://i.imgur.com/KUzuxpf.png)

Directors: Steven Anderson
Media Created:
Author URL: http://www.faithfulwordbaptist.org/page5.html

## [Filename - Filename](https://help.mp3tag.de/main_converter.html#ftf)
%1 - %2 (%3) %4
```
Old filename: 001 - 01-05-2014 AM - Love One Another.mp4
Old filename pattern: %1 - %2 %3 - %4
 
New filename pattern: %1 - %4 (%2)
New filename: 001 - Love One Another (01-05-2014).mp4

```

## Add Spirit Sheets

Being able to mouseover the timeline is awesome. To do that, generate spirit sheets using [[Wiki/Everything I Know About/Everything I Know About FFmpeg#Generate Sprite Sheet (Filmstrip/Montage) From Multiple MP4s\|FFmpeg]].



# Add track numbers

Tag - Tag: `$num(%_counter%,)`