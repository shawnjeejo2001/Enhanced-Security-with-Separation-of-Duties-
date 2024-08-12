The Enhanced Security with Separation of Duties

Objective

In this project we are going to be modifying permissions in linux based on an organizations need. We are going to be using the chmod to do this. In this project we’ll also see what the permission string is. Correct assignment of permissions is necessary to keep the organization and its data safe. To minimize unauthorized access we’ ll follow principle of least privilege where a user only gets access to a limited access to data which the user needs.

Skills Learned

- Mastery of Linux file permissions and access control.
- Proficiency in using Bash commands to modify and manage file and directory permissions.
- Understanding of the principles and importance of separation of duties in cybersecurity.
- Ability to design and implement access control policies in a Linux environment.
- Enhanced problem-solving skills related to access management and system security.

Tools Used

- Linux Bash shell for modifying permissions and managing access control.
- File and directory permission management commands (e.g., chmod, chown, chgrp).
- Security best practices documentation for implementing separation of duties.

Steps

Assessing Current Permissions
  To check for file and directory details we first go to the directory we need to check. Once we are there we use ls -l this lists all the files and the permissions assigned to them.Next to check for hidden files we could use the command ls -a Alternatively we can use the command ls -la which displays all the files and permissions including the hidden files.In this example we are going to be checking and changing the permissions associated with the projects directory in the researcher2 directory(/home/researcher2/projects).

  
<img width="692" alt="Screenshot 2024-08-12 at 7 02 40 PM" src="https://github.com/user-attachments/assets/33eb3a99-4e6a-46ff-8f7f-85d4d622f770">
    
Describe the permissions string
  The permission string is a 10 character string represented as drwxrwxrwx. The first character representswhether it is a directory or a file(drwxrwxrwx). If it’s a file the d is replaced with a ‘-’. Then next 3 characters indicate the permissions allowed for the User(drwxrwxrwx). Here in this example rwx indicated that the User has read, write and execute privileges. The fifth through the 7th characters represent permissions allowed for the Group(drwxrwxrwx). Here the group is allowed to read, write and execute in that directory. The 8th to the 10th character indicated permission allowed for other(drwxrwxrwx). Other indicates all other users on the system. Here the other group has been allowed to read,write and execute files in that directory.

Modifying Permissions
  To change the permissions we can use the chmod command. In this example we can see one of the files who has granted permission to other to write to the file project_k.txt. This can be a security issue since only the User and Group should be allowed to make any changes to the file. This could result in a vulnerability where threat actors could take advantage of this to change contents of a file to knowingly harm the organization. Also the organization needs to follow the principle of least privilege so that no one in the organization gets access/authorization to files they won’t need to look into to complete their tasks.In this example we are going to remove the other’s access to write to this file using the command chmod o-w project_k.txt . This changes the permission string of that file to -rw-rw-r-- . This indicates that only the User and the Group have permissions to read and write on that file.

  
<img width="688" alt="Screenshot 2024-08-12 at 7 06 24 PM" src="https://github.com/user-attachments/assets/a250299b-918f-40cc-8051-60fe3fa44d4e">



Change file permissions on a hidden file  
  The organization doesn’t want anyone to have write permission to the hidden file .project_x.txt . Hidden files are files that start with ‘.’. In this example we are going to removing write access for both the User and Group. To do this we use the command chmod u=r,g=r .project_x.txt. This changes the permission for the hidden file so that both the user and group only have read permissions.
  
    
<img width="692" alt="Screenshot 2024-08-12 at 7 09 40 PM" src="https://github.com/user-attachments/assets/cec533b0-e468-4e8d-bb4d-e7bd353398e2">

Change directory permissions
The organization doesn’t want anyone other that the User to have execute permission. So in this example we are going to remove the execute permission from the group. We can do this by using the command  chmod g-x drafts


<img width="692" alt="Screenshot 2024-08-12 at 7 16 02 PM" src="https://github.com/user-attachments/assets/6a0e898b-a564-4694-901d-9a98953462a0">


Summary


  In this project, we focused on modifying file and directory permissions in a Linux environment to align with organizational security needs. Permissions are represented by a 10-character string (drwxrwxrwx), distinguishing between directories (d) and files (-), and specifying read (r), write (w), and execute (x) access for users, groups, and others. We used commands like ls -l to inspect permissions and chmod to adjust them. For instance,chmod o-w project_k.txt removed write access for others, ensuring only users and groups could modify the file (-rw-rw-r--). Hidden files, denoted by names starting with ., were managed with commands like chmod u=r,g=r .project_x.txt to restrict write permissions. Additionally, directories had permissions adjusted to restrict execute access for groups using chmod g-x drafts. This approach followed the principle of least privilege, granting minimal permissions necessary for tasks, thereby enhancing security by reducing the risk of unauthorized access and ensuring organizational data integrity.


