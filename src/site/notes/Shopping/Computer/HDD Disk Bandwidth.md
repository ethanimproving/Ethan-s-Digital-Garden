---
dg-publish: true
dg-created: Jun 16, 2024, 11:35 PM
---

Dad just upgraded his desktop for Father's Day, and as a result offered his old components to upgrade Faith's desktop in the hallway. The last time she used it was November 2021. Her Google Chrome History was of a book she made for Aunt Edith titled, "The Bible Way To Heaven." She illustrated pictured for her book using Gimp, but her computer kept beeping while it was on, indicating a component failure.

Fast forward to 2024, and now she has a new computer thanks to dad's upgrades. However, things are still a little groggy due to the old Disk Drive.

![](https://i.imgur.com/nZEysMg.png)

==Disk utilization refers to how much of the disk's bandwidth or read/write capacity is being used, not the amount of free space available==. Even with plenty of free space, your disk can be fully utilized if the read/write operations are consuming all the available bandwidth.

# Monitoring Tools

- **Resource Monitor:**
    
    - Provides a more detailed view of what’s using the disk. Open it by typing `resmon` in the Run dialog (`Win + R`).
- **Performance Monitor:**
    
    - Open it by typing `perfmon` in the Run dialog (`Win + R`). This tool provides more granular details on system performance.

It looks like her system is being bogged down by system tasks. However, it's only 8MB per second. That's not a lot.

![](https://i.imgur.com/PGaqpSh.png)

# Causes of Slowing Down Over Time

## 1. Fragmentation (HDDs):
    
- For HDDs, fragmentation can cause slower read/write speeds. Use the built-in Disk Defragmenter to defragment the disk.

HDD fragmentation refers to the scattering of parts of a file all over the hard drive rather than storing them in contiguous sectors. This phenomenon occurs over time as files are created, modified, deleted, and resized. Here’s a more detailed explanation:

### How Fragmentation Happens

1. **File Creation and Deletion:**
    
    - When you create a file, the operating system saves it in the next available free space on the hard drive.
    - Deleting files creates gaps of free space.
2. **File Modification:**
    
    - When a file is modified and grows in size, the additional data may not fit into the originally allocated space.
    - The operating system then places the extra data in the next available free space, causing the file to become fragmented.

### Impact of Fragmentation

1. **Slower Read/Write Speeds:**
    
    - The read/write head of the HDD must move to different locations to read a fragmented file, which increases seek time and slows down access speeds.
2. **Reduced System Performance:**
    
    - Programs and files take longer to open, and overall system responsiveness can decrease because the HDD spends more time seeking fragmented pieces of data.
3. **Increased Wear and Tear:**
    
    - Excessive movement of the read/write head can lead to faster mechanical wear of the HDD components, potentially shortening its lifespan.

## 2. Wear and Tear (SSDs):
    
- SSDs have a finite number of write cycles. Over time, their performance can degrade as cells wear out.
- Use tools like CrystalDiskInfo to check the health of your SSD.

# Recourse

The best course of action is probably to [[Wiki/Technology/Cloning A Disk\|clone the drive]] to Dad's old 500GB SSD or [[Shopping/Computer/Buying Hard Drives\|buy a new Disk]]. That should be a lot faster. Alternatively, you can defragment the current HDD.

## Fixing Fragmentation

1. **Using Disk Defragmenter:**
    
    - After analyzing the drive, click "Optimize" to start the defragmentation process.
    - This process consolidates fragmented files and rearranges them to occupy contiguous spaces on the disk.

![](https://i.imgur.com/b2tq12j.png)

1. **Scheduled Maintenance:**
    
    - Windows can automatically defragment your hard drive on a regular schedule. Ensure that this feature is enabled:
        - In the Disk Defragmenter tool, click "Turn on" under Scheduled Optimization and set a frequency (e.g., weekly).



