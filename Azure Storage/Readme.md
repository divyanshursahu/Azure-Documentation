## Azure Storage:

How many types of Storage services we have in Azure ?

Azure Storage has **five** services. They are:
  
  1. Azure Blobs
  2. Azure Files
  3. Azure Queues
  4. Azure Tables
  5. Azure Disks

  ![Azure Storage Architecture](https://github.com/divyanshursahu/Azure-Documentation/assets/96013623/36d452e3-7799-4609-9897-4e6f8b6a12e0)

  ![image](https://github.com/divyanshursahu/Azure-Documentation/assets/96013623/9b17fed5-348d-4b24-8321-2faf36213c75)

  ![Front End Layer in Azure Architecture](https://github.com/divyanshursahu/Azure-Documentation/assets/96013623/7f33a016-bcb5-44bb-8f75-cfece78867b0)

  ![image](https://github.com/divyanshursahu/Azure-Documentation/assets/96013623/9b17fed5-348d-4b24-8321-2faf36213c75)

  ![Different storgaes and their features in the Front End layer](https://github.com/divyanshursahu/Azure-Documentation/assets/96013623/e695ed82-7014-46ac-963e-f80bd5f43816)

  ![image](https://github.com/divyanshursahu/Azure-Documentation/assets/96013623/9b17fed5-348d-4b24-8321-2faf36213c75)

  ![Types of Blobs](https://github.com/divyanshursahu/Azure-Documentation/assets/96013623/daadfcf6-47ae-48d6-ae47-f9e3f7fd6e92)

*** 
![Azure Hierarchy with Azure Maximums](https://github.com/divyanshursahu/Azure-Documentation/assets/96013623/6c8f3fb5-1496-443b-9f95-c9870ce75519)

# Reference
https://medium.com/geekculture/what-is-a-blob-83e65f590694

What is Container in Azure Storage ?

- Container is a set of Blobs. Its like directory in file system.

How many containers we can create in a storage.

- We can create unlimited number of Container in a Storage account

How many Blobs we can create in a Storage account or in a Container ?
- we can create  unlimited number of Blobs in a Storage account or in a Container

  ![image](https://github.com/divyanshursahu/Azure-Documentation/assets/96013623/3ca12e21-0c9e-49e8-856a-f482647b47f4)

What is Azure Blobs ?
- Azure Blobs storage is object storage solution. This is used for storing massive amount of unstructured data like text or binary data. Like Images, videos or audios, etc. Suppose if we want our application to stream audio or video, or we want to access our application data from anywhere, then we should consider Azure Blobs storage. Also its used for Backup and Restore, Disaster Recovery or archiving.

![image](https://github.com/divyanshursahu/Azure-Documentation/assets/96013623/683b3b17-7f93-4a86-a008-bdfe0862a744)

What is Block Blobs, Page Blobs and Append Blobs ?

**Block Blob**
- when we create Blob that time we specify Blob type. After we create Blob type we can't change the type. Block Blobs are for uploading large amount of data. This Blobs composed of **Blocks**
  - What is Block?
    - Block is the unit.
    - we can split a Blob into Blocks
    - Minimum size of Block is 64KB and Maximum size is 100MB.
   
**Page Blob**
- Azure Disks are in Hyper-V VHD format and they are nothing but Page Blobs in Azure Storage.

**Append Blob**

This is also composed of Blocks.
Append Blobs is optimised for fast append operations, this is ideal for scenarios where the data must be added to an existing blob without modifying the existing contents of that blob (Ex: Logging data from a VM, Auditing).
![image](https://github.com/divyanshursahu/Azure-Documentation/assets/96013623/9b2ae3a0-3589-4f93-8b53-55f8f95a3724)

How many types of Storage accounts we have in Azure?

Currently Azure has four storage accounts. They are:
1. **Standard general-purposr v2** (Example: Standard storage account type for Blobs, Queues, Tables and File Shares, Recommended for most of the storgae scenarios)
2. **Premium block blobs**(Example: especially good for handling smaller blob sizes)
3. **Premium page blobs** (Example: Premium page Blobs are high- performance solid-state drive (SSD)-based storage, designed to support I/O-intensive workloads with significantly high throughput and low latency)
4. **Premium file shares** (Example: stores file shares on solid state drives (SSD), with single-digit millisecond latency)

How do you access Azure Files ?
- We can mount the file share on our local machine by using the SMB 3.0 protocol, or else we can use tool like Storage Explorer to access files in our file share. From our application, we can use storage client libraries, REST APIs, PowerShell, or Azure CLI to access our files in the Azure file share.

What is Azure Storage Explorer 

Its an application that helps us to easily access Azure Storage account through any device like Windows or Linux. We can manipulate tables, blobs, queues and files. We can copy, delete download, manage snapshots.

What is AzCopy ? 

AzCopy is used for copy files or blobs to and from a storage account. AzCopy is just an executable file, so there's nothing to install. We can provide authorization credentials by Azure AD or SAS Token.

Troubleshooting Azure Files:

When you try to mount a file share you are getting "System error 5 occured. Access is denied"
May be
1. Client OS does not support SMB encryption, or
2. Connection is not made from the same datacenter where the Azure File Share resides, or
3. "Secure Transfer Required" is enabled in the storage account, or
4. You can check the VNET and Storage Firewall rules are configured properly, or
5. Share level permission is not correct if we are using Azure AD DS or normal AD.

When you try to mount or unmount a file share you are getting "Error 53\67\87"

May be:
1. Firewall or ISP is blocking Port 445
2. NTLM v1 is enabled.

For this issues we can run AzFileDiagnostics script to check the port is blocked or not.

When you try to access or delete a file share you are getting "No access error"

May be:
1. Firewall or VNET is blocking because of rules configured.
2. User account is not having the access

Slow file copy to and from Azure Files

May be:
1. Check the I/O size and recommended is 1 MiB ad the I/O size
2. Use AzCopy for file transfer between two Azure Files
3. User can use Robocopy for transfering files between Azure Files to On-premises.

Performance issues with Azure Files

May be:

1. Check the I/O bandwith limit
2. Enable large File Shares in your storage account
3. Increase the file IOPS limit
4. May be because of single threaded application, we should increase the number of threads from application side or should use AzCopy
5. We should check the response type of API and need to modify from application side.
   

Reference:

https://www.msp360.com/resources/blog/microsoft-azure-storage-types-explained/

https://www.linkedin.com/pulse/microsoft-azure-storage-services-pawan-verma/
