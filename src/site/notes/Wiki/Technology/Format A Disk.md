---
dg-publish: true
dg-created: Jul 02, 2024, 10:41 AM
---

# How To Format A Disk

## Partitioning Scheme

Given that my 12TB Iron Wolf Hard Drive is intended for media storage on a Plex server and I have a separate SSD as the boot drive, I will use the **GPT (GUID Partition Table)** partitioning scheme. GPT is necessary for drives larger than 2TB and offers better reliability and more flexibility than MBR (Master Boot Record). GPT stores multiple copies of the partition table, providing redundancy, which makes it more reliable.

## Disk management

Open Disk Management and right-click on the unallocated space to select "New Simple Volume."

![](https://i.imgur.com/EPbwQzn.png)

For simplicity and to maximize available space, create a single partition for the entire drive.

## File System

I was tempted to choose exFAT because it is natively supported by both Windows and Linux (with additional packages installed on Linux), and I may transfer this drive to the Linux system later on. The drawback is that it may be less reliable than NTFS for critical data due to fewer built-in error recovery mechanisms. **NTFS includes advanced error-checking and recovery capabilities**, making it more reliable for critical data, so I believe this to be the most appropriate file system for this drive.

![](https://i.imgur.com/BpdT8fs.png)

- **For Windows**: Use NTFS.
- **For macOS**: Use HFS+ (Mac OS Extended) or APFS.
- **For Linux**: Use ext4.

## Full Format

A full format can take a lot of time. For my 12TB HDD, it only progressed 1% in the first 10 minutes. A quick format is almost instantaneous by comparison, but there are a few reasons I opted for a full format with this drive. 

![](https://i.imgur.com/LTiXCXI.png)

### Security

I purchased the drive [[Shopping/Computer/Buying Hard Drives#Amazon Deals\|for a deal]] from Amazon Renewed, I don't like the idea of previous data still existing on the drive. In reality this doesn't matter at all to me, it would only matter to the previous owner for security reasons. I can recover his data if I wanted to. But the concept of previous viruses being on the drive make me feel like it could be tainted. A full format overwrite existing data with zeroes, which is what takes so long.

### Disk Health Check

The other advantage of a full format is that it scan the disk for bad sectors. Given that my disk is a renewed disk from Amazon, it's prudent to take some precautions to ensure its reliability and security before putting it to use. There are some diagnostic tools I could use for that besides a full format, so it's not really necessary. But you can be sure that if there are underlying issues with the disk, they will be detected.

A good rule of thumb is the following:

- **Health Check**: Perform a thorough health check using disk diagnostic tools to ensure the drive is in good condition.
- **Full Format (if Concerns)**: If the health check reveals any issues or if you have concerns about data security, opt for a full format. This will help ensure all sectors are checked and any potential issues are addressed.
- **Quick Format (if Confident)**: If the health check indicates no issues and you're confident in the drive's condition, a quick format should suffice to prepare it for use.

### Wear On The Drive

In full transparency, since I have a pretty high risk tolerance, **I wouldn't do the full format next time.** If I had any good reason to doubt the drive's integrity, I would opt for a full format to ensure all sectors are checked and any potential issues are addressed. But this does contribute to slightly more wear on the drive due to the extensive read-write operations involved.

## Allocation unit size (Block Size)

Larger allocation unit sizes (e.g., 128K, 256K, 512K, 1M, 2M) reduce overhead and improve performance for large files because fewer clusters are needed to store each file. This can reduce fragmentation and optimize disk space usage. It can, however, lead to more wasted space for small files because each file consumes at least one full cluster, so it's important to strike a decent balance based on your use case.

It's like choosing box sizes if you were planning to move, but imagine you're only allowed to put one item in each box, and for large items you can just tape the little boxes together to make a big box. If you had a ton of tiny items, you would want a ton of tiny boxes, because a giant box with one tiny item in it is wasting space. If you only had large items, you would want larger boxes so you don't have to order as many of them and go through the work of taping them together.

**You can choose to optimize for space or optimize for performance**. Since I have large media files and 12TB drives are relatively cheap these, days, I'm going to optimize for performance. This reduce overhead, fragmentation, and improves disk access speed. Realistically with a Plex server the bottleneck is probably the network speed anyway, not the disk speed, so it's somewhat of a moot point. However, I still want the disk read speed to be as fast as possible for the best streaming I can get. Less fragmentation will also allow the disks to last longer potentially, and reduce slowing over time.

If you choose 512K, you ask, "Am I willing to lose up to half a megabyte on each file in order to avoid fragmenting the disk with tons of cluster allocations per file?" In a year, I will add 150 sermons from one church. That's 75 megabytes of max potential wasted space, and probably closer to 30 megabytes realistically. That is 0.00025% of my 12TB capacity. I am willing to sacrifice that amount of space for a potential 5% to 15% improvement in sequential read speeds.

Going beyond 256K or 512K may not provide significant additional benefits (diminishing returns) and could potentially lead to increased wasted space for small files, so for my 12TB Iron Wolf Hard Drive, which is primarily used to store large media files such as videos and high-resolution media (which are typically several hundred megabytes to several gigabytes in size), choosing an allocation unit size of 128K or 256K would be appropriate.