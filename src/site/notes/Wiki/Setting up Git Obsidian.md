---
tags: wiki tutorial matadata
dg-home: true
dg-publish: true
---

# Introduction to Obsidian

Obsidian was built from the ground up to be a second-brain or <mark class="hltr-yellow">personal knowledge management system</mark>, so it included second-brain functionality from the start. It’s more than just a place to jot down and keep your notes; it’s an intuitive productivity app, more than a digital note-taking platform for capturing ideas. It’s a second brain.[^1]

## Bi-Directional Linking

Your mind is a network of connections between different pieces of information, so any software that wants to mimic the mind needs to make the same connections. Enter bi-directional links.

The idea of linking is simple. Imagine a student who needs to take notes about Caesar for a history class. He wants to link to a previous note about Rome within the text. Wikipedia uses these types of links within its articles.

But Obsidian takes this idea one step further. When taking notes, you can link out but also see the links coming in, too. These are backlinks. Backlinks don’t link out to other notes. Instead, they are the record of the notes linking to you. So, for example, if we went to our Rome note and checked the backlinks, we’d see that our Caesar note was linking to us.[^1]

## Digital Gardening

[Digital gardening](https://www.youtube.com/watch?v=Hn6_4ZzcpiY), also known as **personal knowledge management** or PKM, is a relatively new concept that has emerged in recent years as a response to the growing amount of information that people encounter and need to manage in their daily lives.

The term "digital gardening" was first coined by American software developer and blogger Joel Hooks in 2019. However, the idea of using digital tools to organize and cultivate personal knowledge has been around for much longer, and can be traced back to early note-taking and personal information management systems like Evernote and OneNote.

In recent years, there has been a growing interest in digital gardening and PKM as more people have come to recognize ==the value of curating their own personal knowledge bases and making them accessible== and useful for themselves and others. Today, there are a variety of digital tools and platforms available that cater specifically to the needs of digital gardeners, including Obsidian, Roam Research, and Notion, among others.

## Competitors

- [Why I chose Obsidian over Roam (as a Roam investor)](https://www.youtube.com/watch?v=AWUk8-6yG2g).
- [Why I left Notion for Obsidian](https://www.youtube.com/watch?v=4DXHVawhh4c).
- [Notion vs Obsidian // Databases vs Dataview](https://www.youtube.com/watch?v=AhhFLXfldJQ).

---
[^1]:  Gaynor, Gregory J. “[How to Migrate Your Notes: Evernote to Obsidian](https://facedragons.com/foss/migrate-evernote-to-obsidian/).” _Face Dragons_, 15 Jan. 2023.


[Readme guide](https://github.com/gitobsidiantutorial/obsidian-git-tut-windows/blob/main/README.md)
> [!Bible] 
> In the beginning was the Word, and the Word was with God, and the Word was God.
>The same was in the beginning with God. All things were made by him; and without him was not any thing made that was made.
> 
> 
  [John 1:1-3 - KJV](https://bible-api.com/John+1:1-3?translation=kjv)


## [Installation and clone a repo](https://github.com/Vinzent03/obsidian-git-mobile#installation-)
1. Create new vault
2. Change config directory in Settings -> About
3. Install Community Plugin Obsidian Git
4. Set password/personal access token and username in Settings -> Obsidian Git
5. Execute clone repo command with `https://github.com/ethanimproving/Family-Ideas.git`
6. Reload plugin

# Frequent Shortcuts

| Action                | Shortcut         |
| --------------------- | ---------------- |
| Commit Changes        | Ctrl + K         |
| Push Changes          | Ctrl + Shift + K |
| View history for file | Alt + H          |
| Format                | Shift + Alt + F  |
| Reveal current file in navigation | Alt + 1 |


## Multi-caret selection / line manipulation

| Action                                    | Shortcut           |
| ----------------------------------------- | ------------------ |
| Add cursor below                          | Ctrl + Ctrl + Down |
| Add additional carrot                     | Alt + click        |
| Add the next matching text as a selection | Ctrl + D           |
| Add all matching text as selections       | Ctrl + Shift + L   |
| Copy Line Down                            | Ctrl + Alt + Down  |
| Move Line Down                            | Alt + Down         |
| [Add cursor below](https://github.com/ethanmiller1/PowerShell/blob/master/Program%20Data/Visual%20Studio%20Community/Shortcuts.md)                        |                    |
| [Column selection mode](https://forum.obsidian.md/t/column-selection-and-editing-mode/32191)                   |                    |

# Buffer size issue

[This repository currently has approximately 320 loose objects](https://stackoverflow.com/questions/21457407/git-gui-perpetually-getting-this-repository-currently-has-approximately-320-lo).

Prune
```bash
# Prune loose objects older than 2 weeks
$ git gc --prune
# Prune loose objects regardless of their age
$ git gc --prune=now
# Aggressively optimize the repository at the expense of taking much more time. The effects of this optimization are mostly persistent.
$ git gc --aggressive
```

[Git GC Docs](https://git-scm.com/docs/git-gc#_options)

Runs a number of housekeeping tasks within the current repository, such as compressing file revisions (to reduce disk space and increase performance) and removing unreachable objects which may have been created from prior invocations of git add.


> Even when you removed the files, they are still present in previous revisions. That's the whole point of git, is that even if you delete something, you can still get it back by accessing the history. ([Stackoverflow 2012](https://stackoverflow.com/questions/11050265/remove-large-pack-file-created-by-git))

To rewrite history, it is recommended in [official Github docs](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/removing-sensitive-data-from-a-repository) to use [BFS Repo-Cleaner](https://rtyley.github.io/bfg-repo-cleaner/). Download the JAR file into an empty folder and step through the following commands:

```bash
git clone --mirror https://github.com/ethanimproving/Family-Ideas.git
java -jar .idea/bfg-1.14.0.jar --delete-files *.png .git
java -jar .idea/bfg-1.14.0.jar --delete-files *.jpg Family-Ideas.git
java -jar .idea/bfg-1.14.0.jar --delete-files *.jpeg Family-Ideas.git
java -jar .idea/bfg-1.14.0.jar --delete-files *.gif Family-Ideas.git
java -jar .idea/bfg-1.14.0.jar --delete-folders .obsidian\plugins\obsidian-multi-cursor Family-Ideas.git
git reflog expire --expire=now --all && git gc --prune=now --aggressive
git push
```

Feb 18
```
 Filename                                   Git id
        --------------------------------------------------------------
        337cde8e-af73-43f6-b05e-6a0ccafb22c9.png | a3bc6e67 (60.0 KB)
        353a747d-1fa0-4438-8916-52ff26468344.png | cae3b8df (158.3 KB)
        52001e00-1dfe-497c-b888-67ea10da29c7.png | 1fd33562 (13.3 KB)
        5357c81d-70f9-43cd-8caa-be9491068044.png | a580a4be (43.7 KB)
        5a4d9b5f-3b0b-4801-bb3b-fc8a9aba1e9d.png | e49497e0 (82.2 KB)
        5dcb62e2-d805-4330-b280-92331f41ae98.png | aec5dcae (35.4 KB)
        Balanced Binary Tree.png                 | 5015186a (51.6 KB)
        Maximum Depth of Binary Tree.png         | 74709269 (297.3 KB)
        Pasted image 20221005221241.png          | 3d6447ea (793.3 KB)
        Pasted image 20221010212804.png          | ea79d9a0 (3.2 MB)
        Pasted image 20221023174756.png          | e69ff684 (204.5 KB)
        Pasted image 20221024161400.png          | be234a91 (10.1 KB)
        Pasted image 20221024161512.png          | f1ede3fa (6.5 KB)
        Pasted image 20221024161817.png          | 21760046 (291.1 KB)
        Pasted image 20221024161849.png          | 7fd5a87c (37.6 KB)
        ...

```

It will output something like this:
![](https://i.imgur.com/OJvkh2H.png)

# Plugin

* Advanced Tables
* Better Code Block
* Better Word Count
* Calendar
* Checklist
* Zotero
* Citations
* Dataview*
* Dynamic Table of Contents
* Excel to Markdown Table
* Markdown Table Editor
* Kanban
* Vantage - Advanced Search Builder
* [Using color to think better](https://www.youtube.com/watch?v=vZC7FAOSjkU)
* [Heatmap Calendar](obsidian://show-plugin?id=heatmap-calendar)
* [Search For Selected Text](https://github.com/scambier/obsidian-omnisearch/issues/212)
* [Option to open in a new tab](https://github.com/scambier/obsidian-omnisearch/issues/213)

# Version Control with Git LFS
[Introducing and Setting up Git LFS (Large File Storage)](https://www.youtube.com/@CloudwithChris)
https://git-lfs.github.com/

```bash
git init
git lfs track "*.png"
git lfs track "*.jpg"
git lfs track "*.gif"
git lfs track "*.web"
git add .gitattributes
git remote add origin https://github.com/ethanimproving/PDF-Library.git
git push -u origin master
```

```bash
$ git push -u origin master
Uploading LFS objects:   0% (0/95), 0 B | 0 B/s, done.
batch response: This repository is over its data quota. Account responsible for LFS bandwidth should purchase more data packs to restore access.
error: failed to push some refs to 'https://github.com/ethanimproving/PDF-Library.git'
```

[Include Git LFS objects in archives](https://stackoverflow.com/questions/62905325/this-repository-is-over-its-data-quota-account-responsible-for-lfs-bandwidth-sh)

# Plug-in Ideas

- Share file as Git link.
- Timeline
- Hymns app Integration (maybe with Dataview)
- Better quote blocks (‘’’qoute-orange)
- Custom fonts