---
keyword: [attach a disk, attach, create a disk, ECS, Alibaba Cloud]
---

# Attach a data disk

You can create a separate pay-as-you-go disk and then attach the disk to an ECS instance as a data disk.

-   The disk is in the same zone as the instance to which the disk is attached.
-   The instance is in the **Running** \(Running\) or **Stopped** \(Stopped\) state, not in the **Locked** \(Locked\) state.
-   The disk is in the **Unattached** \(Available\) state.
-   You have no overdue payments in your account.

Before you attach a disk, take note of the following items:

-   Disks that are created along with instances and subscription data disks that are created for subscription instances are automatically attached to the corresponding instances. You do not need to manually attach the disks.
-   You can attach a maximum of 16 data disks to an ECS instance.
-   A disk can be attached only to a single instance.

**Note:** The attach operation refers to attaching disks to ECS instances in the console, instead of mounting file systems to the operating systems of ECS instances by running the `mount` command. For more information, see [Format a data disk for a Linux instance](/intl.en-US/Block Storage/Cloud disks/Format a data disk/Format a data disk for a Linux instance.md) and [Format a data disk for a Windows ECS instance](/intl.en-US/Block Storage/Cloud disks/Format a data disk/Format a data disk for a Windows ECS instance.md).

You can also attach disks on the Instances or Disks page.

-   If you want to attach multiple disks to an ECS instance, we recommend that you perform the operation on the Instances page. For more information, see [Attach disks on the Instances page](#section_x9k_hqr_iul).
-   If you want to attach multiple disks to different ECS instances, we recommend that you perform the operation on the Disks page. For more information, see [Attach disks on the Disks page](#section_2qq_dlf_fes).

## Attach disks on the Instances page

1.  Log on to the [ECS console](https://ecs.console.aliyun.com).

2.  In the left-side navigation pane, choose **Instances & Images** \> **Instances**.

3.  In the top navigation bar, select a region.

4.  Find the instance to which you want to attach disks and click the ID of the instance.

    ![Attach a data disk](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1772909951/p73891.png)

5.  Click the **Cloud Disk** tab. In the upper-right corner of the **Cloud Disk** tab, click **Attach Disk**.

    ![Attach Disk](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2635585061/p4420.png)

6.  In the Attach Disk dialog box, configure the related parameters to attach the disk.

    ![Attach](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1772909951/p4421.png)

    1.  Select the disk that you want to attach and specify the release settings for the disk.

        |Parameter|Description|
        |---------|-----------|
        |Target Disk|Select the disk that you want to attach.|
        |Release Disk with Instance|If you select this option, the disk will be automatically released when the instance is released. If you do not select this option, the disk will be retained when the instance is released.**Note:** If the disk that you want to attach is a system disk that you detached from another instance, the instance specified by **Release Disk with Instance** refers to the instance from which you detached the disk, not the current instance. |
        |Delete Automatic Snapshots While Releasing Disk|If you select this option, automatic snapshots of the disk will be released when the disk is released. We recommend that you do not select this option to retain backup data.|

    2.  Click **OK**.

    3.  Click **Attach**.

    If the status of the disk becomes **In Use**, the disk is attached.

7.  Create partitions and file systems after the disk is attached to the instance. The following table describes the operations to be performed based on different scenarios.

    |Disk status|Operating system|What to do next|
    |:----------|:---------------|:--------------|
    |New empty disks|Linux|    -   For information about operations on disks that are smaller than 2 TiB, see [Format a data disk for a Linux instance](/intl.en-US/Block Storage/Cloud disks/Format a data disk/Format a data disk for a Linux instance.md).
    -   For information about operations on disks that are larger than 2 TiB, see [Partition and format a data disk larger than 2 TiB in size](/intl.en-US/Block Storage/Cloud disks/Format a data disk/Partition and format a data disk larger than 2 TiB in size.md). |
    |Windows Server|    -   For information about operations on disks that are smaller than 2 TiB, see [Format a data disk for a Windows ECS instance](/intl.en-US/Block Storage/Cloud disks/Format a data disk/Format a data disk for a Windows ECS instance.md).
    -   For information about operations on disks that are larger than 2 TiB, see [Partition and format a data disk larger than 2 TiB in size](/intl.en-US/Block Storage/Cloud disks/Format a data disk/Partition and format a data disk larger than 2 TiB in size.md). |
    |Disks created from snapshots|Linux|Connect to the instance and run the following command to mount the disk partitions that have available file systems:     ```
mount <Data disk partition> <Mount point>
    ``` |
    |Windows Server|N/A|


## Attach disks on the Disks page

1.  Log on to the [ECS console](https://ecs.console.aliyun.com).

2.  In the left-side navigation pane, choose **Storage & Snapshots** \> **Disks**.

3.  In the top navigation bar, select a region.

4.  Find the disk in the **Unattached** state and choose **More** \> **Attach** in the **Actions** column.

    ![Attach a disk on the Disks page](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1772909951/p4422.png)

5.  In the dialog box that appears, configure the following parameters.

    ![Attach](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1772909951/p4423.png)

    1.  Select the disk that you want to attach and specify the release settings for the disk.

        |Parameter setting|Description|
        |-----------------|-----------|
        |Target Instance|Select an ECS instance to which you want to attach disks.|
        |Release Disk with Instance|If you select this option, the disk will be automatically released when the instance is released. If you do not select this option, the disk will be retained when the instance is released.**Note:** If the disk that you want to attach is a system disk that you detached from another instance, the instance specified by **Release Disk with Instance** refers to the instance from which you detached the disk, not the current instance. |
        |Delete Automatic Snapshots While Releasing Disk|If you select this option, automatic snapshots of the disk will be released when the disk is released. We recommend that you do not select this option to retain backup data.|

    2.  Click **Attach**.

    If the status of the disk becomes **In Use**, the disk is attached.

6.  Create partitions and file systems after the disk is attached to the instance. The following table describes the operations to be performed based on different scenarios.

    |Disk status|Operating system|What to do next|
    |:----------|:---------------|:--------------|
    |New empty disks|Linux|    -   For information about operations on disks that are smaller than 2 TiB, see [Format a data disk for a Linux instance](/intl.en-US/Block Storage/Cloud disks/Format a data disk/Format a data disk for a Linux instance.md).
    -   For information about operations on disks that are larger than 2 TiB, see [Partition and format a data disk larger than 2 TiB in size](/intl.en-US/Block Storage/Cloud disks/Format a data disk/Partition and format a data disk larger than 2 TiB in size.md). |
    |Windows Server|    -   For information about operations on disks that are smaller than 2 TiB, see [Format a data disk for a Windows ECS instance](/intl.en-US/Block Storage/Cloud disks/Format a data disk/Format a data disk for a Windows ECS instance.md).
    -   For information about operations on disks that are larger than 2 TiB, see [Partition and format a data disk larger than 2 TiB in size](/intl.en-US/Block Storage/Cloud disks/Format a data disk/Partition and format a data disk larger than 2 TiB in size.md). |
    |Disks created from snapshots|Linux|Connect to the instance and run the following command to mount the disk partitions that have available file systems:     ```
mount <Data disk partition> <Mount point>
    ``` |
    |Windows Server|N/A|


**References**  


[AttachDisk](/intl.en-US/API Reference/Disk/AttachDisk.md)

