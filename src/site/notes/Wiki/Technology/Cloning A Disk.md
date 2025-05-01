---
dg-publish: true
dg-created: Jun 17, 2024, 7:46 PM
---

# Software

For dad's migration we visited the [Data Transfer](https://www.crucial.com/support/ssd-support#dataTransfer) section of the Crucial web page to download [Acronis True Image](https://www.acronis.com/en-sg/promotion/crucialhd-download/?cm_re=ssd-support-_-structured-_-acronis-link). However, this requires [at least 1 Crucial SSD](https://i.imgur.com/RW3grcY.png) to be installed in your system, so we will use [Macrium Reflect](https://www.macrium.com/blog/cloning-a-disk-with-macrium-reflect-v8), downloaded on their website, from [Major Geeks](https://www.majorgeeks.com/files/details/macrium_reflect_free_edition.html), or via chocolatey with the below command:

```
choco install -y reflect-free
```

# Cables

Then simply plug your SSD into the Motherboard with a [SATA cable](https://www.amazon.com/Benfei-Straight-Locking-Compatible-Driver/dp/B07JFQ2H9R/ref=zg_bs_g_3015394011_d_sccl_1/145-8432420-4810266?th=1) or externally with a [SATA-to-USB Adapter](https://www.amazon.com/StarTech-com-SATA-USB-Cable-USB3S2SAT3CB/dp/B00HJZJI84/ref=zg_bs_g_3015394011_d_sccl_2/145-8432420-4810266?th=1). You may want to pick up a [Mounting Bracket](https://www.amazon.com/Corsair-Dual-Mounting-Bracket-CSSD-BRKT2/dp/B016498CK0/) to secure the SSD in the Desktop Case.

# Formatting

Since the SSD is not new and has been used before, you can skip straight to the cloning process. However, to ensure a clean and error-free cloning, it’s a good idea to delete any existing partitions on the SSD to start fresh. Here’s how to do that, followed by the steps for cloning your HDD to the SSD:

1. Open `Disk Management`.

![](https://i.imgur.com/EotSXPC.png)

![](https://i.imgur.com/9IUpqNv.png)


You can crosscheck the disk letter.

![](https://i.imgur.com/Dwk61G9.png)

# Cloning
## Using Macrium Reflect (Example)

1. **Download and Install**: Download Macrium Reflect Free from the official website and install it.
2. **Open Macrium Reflect**: Launch the application.
3. **Select the Source Disk**: Click on your HDD (the source disk) in the main window.
4. **Clone this Disk**: Select "Clone this disk..." under the disk options.
5. **Select Destination Disk**: Choose your SSD as the destination disk.
6. **Configure Cloning Options**: You can resize partitions on the destination disk if needed. Ensure all partitions from the source disk are selected.
7. **Start Cloning**: Click "Next" and then "Finish" to start the cloning process. Confirm any prompts that appear.

![](https://i.imgur.com/erh79GU.png)
