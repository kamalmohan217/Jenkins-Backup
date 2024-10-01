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
