# Jenkins-Backup

Under the Jenkins Backup heading I am explaining two backups 
1. ThinBackup
2. Periodic Backup

### 1. ThinBackup

I have installed the jenkins plugin for ThinBackup as shown in the screenshot attached below.

![image](https://github.com/user-attachments/assets/27d6c7ef-f4bb-4efa-b630-8b320695e901)

Created backup direcitory and changed the owner and group for the directory as shown in the screenshot attached below.

![image](https://github.com/user-attachments/assets/784be28f-e1ed-4847-9beb-e176c774c131)
![image](https://github.com/user-attachments/assets/0773dbdd-7029-4045-aa5b-d615995327d0)
![image](https://github.com/user-attachments/assets/a203a77a-cc4b-427a-b54c-923be4deefdf)

Go to **Manage Jenkins** > **System**. Then go to ThinBackup Configuration as shown in the screenshot attached below.

![image](https://github.com/user-attachments/assets/c80e55e5-04e8-4544-9518-92f99717f6e9)
![image](https://github.com/user-attachments/assets/b46eee63-90e9-4d67-9b4c-44ea0009f881)

In backup schedule for Full and differential backup cron job I used 9:10 AM UTC daily for backup. For the first time if no Full backup present then it will create it and from the next time onwards it will create the differential backup. In configuration I checked the option for **cleanup differential backups** and **Move old backups to zip files.** Which denotes the differential backup is removed and it will be removed before zipping happens when hence zip files contain no differential backup.

For **Max number of backup sets** I used the value 30 which means for one month I keep the backup and whenever a new backup will be generated the oldest one will be discarded.

The screenshot for backup directory before and after running the cronjob for ThinBackup is as shown in the screenshot attached below.

![image](https://github.com/user-attachments/assets/832c292b-cfe5-41fa-9ea6-ec10f2e10692)
![image](https://github.com/user-attachments/assets/78d694d4-6f65-4dac-9375-3b5df45aaede)

At present I have one Jenkins Job with the name of test-1 I will delete this Jenkins Job and restore from ThinBackup. **After restoring from ThinBackup restart the Jenkins.** Then you will find the deleted Jenkins Job.

![image](https://github.com/user-attachments/assets/3cc7efc7-e572-4517-9eea-7c1198f6500b)

Now I delete the test-1 Jenkins Job as shown in the screenshot attached below.

![image](https://github.com/user-attachments/assets/1f1b6bca-b7a1-43e6-aa08-75ea1ee8943b)

Go to **Manage Jenkins** > **ThinBackup** then click on Restore option as shown in the screenshot attached below. Restore from the available Backup option as shown in the screenshot attached below.

![image](https://github.com/user-attachments/assets/26be47b0-e2ce-4066-904a-93d724241cf4)

After the Restore I am unable to see the deleted Jenkins Job for that I restarted the Jenkins as shown in the screenshot attached below.

![image](https://github.com/user-attachments/assets/1326ef02-3753-4de0-a680-6462eca26e2e)

Restart the Jenkins

![image](https://github.com/user-attachments/assets/91d8985e-44f9-4173-9a0c-0cfab093d15f)

![image](https://github.com/user-attachments/assets/0e71613a-1e1d-453e-9e26-2fb0c8aaba57)

Same number of Builds are also present as it was earlier.

![image](https://github.com/user-attachments/assets/22270bdd-c21d-4957-9eb3-f1c7ede6e3cf)

### 2. Periodic Backup

For periodic backup, installation of Jenkins plugin Periodic Backup has been done as shown in the screenshot attached below.

![image](https://github.com/user-attachments/assets/13815d6c-b57b-47f9-a8e0-d28bf4c986cd)

### 2. Periodic Backup

For periodic backup, installation of Jenkins plugin Periodic Backup has been done as shown in the screenshot attached below.

![image](https://github.com/user-attachments/assets/39c49c0c-6676-419b-a1fb-cb1fe28b34d6)

**Backup Location**
(a) Amazon S3

(b) LocalDirectory

**(a) Amazon S3**

create a temporary directory and change its ownership as shown in the screenshot attached below.

![image](https://github.com/user-attachments/assets/57f1b20b-f044-4987-b753-0a61a7876261)

Create an Amazon S3 Bucket as shown in the screenshot attached below.

![image](https://github.com/user-attachments/assets/076130cb-ae95-4ff8-a398-cc1ba52cd851)

Create a An IAM User with Access Key and Secret Key and which has sufficient privileges to access S3 bucket.

Do the configuration for Periodic backup with backup location as Amazon S3 as shown in the screenshot attached below.

![image](https://github.com/user-attachments/assets/85047883-b09d-42b5-908f-f93cbf6994a6)
![image](https://github.com/user-attachments/assets/a6bd557a-47da-4b12-a94f-9dbb018d39cb)
![image](https://github.com/user-attachments/assets/e5b86b49-862e-469b-9f9f-4bbdeb2c0acf)
![image](https://github.com/user-attachments/assets/659dddb8-7faf-434b-bd03-94ac09ecaeec)

Backup is scheduled at 11:00 AM UTC daily as shown in the screenshot attached below. Daily one backup and total 30 backups will be stored, backup older than 30 days will be discarded.

After the cron job run as per the scheduled time as shown in the screenshot attached above the backup will be availabe in the S3 bucket as shown in the screenshot attached below.

![image](https://github.com/user-attachments/assets/ad10a22a-2a39-460d-8955-47b8d656a83b)
![image](https://github.com/user-attachments/assets/2ff07004-b2a3-4ba5-926b-7af4242b7d98)

Before taking the backup there was a jenkins job with the name of test-1 was present but after backup I deleted the test-1 jenkins job as shown in the below screenshots.

![image](https://github.com/user-attachments/assets/b6eb0b3a-504c-4ea2-a0a0-5abf84caa831)
![image](https://github.com/user-attachments/assets/42a8558f-c051-4717-acc4-e19ab55fad34)

Now for Restoration of backup follow the steps as written below.

![image](https://github.com/user-attachments/assets/93f63bd7-42f9-4fab-b601-e9d4a48b51c9)
![image](https://github.com/user-attachments/assets/5966dc61-cdd5-4b1a-90d3-6f5c9934ec58)
![image](https://github.com/user-attachments/assets/903c5038-1c1a-464c-b7f2-c63fec8fce4d)
![image](https://github.com/user-attachments/assets/6168d238-6191-45f1-8173-068fccea1f6f)
![image](https://github.com/user-attachments/assets/98f66f8b-7ead-4295-96ef-2668e0fa7e7f)

Finally you will find the same jenkins job test-1 as shown in the screenshot attached below.

![image](https://github.com/user-attachments/assets/11cfbb08-c387-4209-aaf3-65b2f655ef33)
