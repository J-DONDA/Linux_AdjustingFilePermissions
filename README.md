<h1>Linux - Adjusting File Permissions</h1>

<h2>Description</h2>
In this lab, I am assuming the role of a security professional at a large organization. I mainly work with their research team. Part of my job is to ensure users on this team are authorized with the appropriate permissions. This helps keep the system secure. 
<br />
<br />
My tasks are to examine existing permissions on the file system within the projects directory. I’ll need to determine if the permissions match the authorization that should be given. If they do not match, I’ll need to modify the permissions to authorize the appropriate users and remove any unauthorized access.
<br />


<h2>Languages and Utilities Used</h2>

- <b>File Permissions</b>

<h2>Environments Used </h2>

- <b>Linux</b> 

<h2>Program walk-through:</h2>


<b>Task 1.) Check file and directory details:</b>

First, I’ll use command  ls -la to assess  the current permissions assigned to the projects directory and any contained files (incluing any hidden files): <br />

![image](https://github.com/J-DONDA/Linux_AdjustingFilePermissions/assets/116527248/2843ab42-01d6-44d6-a2f7-0f15ff55c3b3)


<br />
<br />
<br />
<br />

<b>Task 2.) Describe the permissions string:</b>  <br />

The permissions string is a 10 character string that shows what permissions are currently enabled/disabled for a file or directory. For example, using the project_k.txt file as shown above, the permission string is: <br />

![image](https://github.com/J-DONDA/Linux_AdjustingFilePermissions/assets/116527248/1aca8f21-10fa-46af-a932-3eee939db42e)

<br />
This 10 character string is divided into 4 sections:

The first character indicates wheter this is a file – or a directory d, in this example this is a file -

The next 3 characters rw- show the user permissions. This user  has read and write access  enabled, but does not have  execute .

Characters  5-7 show the group permissions, set as rw- .This group has read and write access  enabled, but does not have  execute .

Characters  8-10 show the other permissions, set as rw- .This other category has read and write access  enabled, but does not have  execute ..

<br />
<br />
<br />
<br />
<br />

<b>Task 3.) Change file permissions:</b> <br/>

The organization does not allow other to have write access to any files. Based on the current permissions, I will need to identify which file(s) needs to have permissions modified: <br />

![image](https://github.com/J-DONDA/Linux_AdjustingFilePermissions/assets/116527248/64a7667a-e18a-447c-9fa5-8c6182bf4ba3)

<br />
As shown in the screenshot above, there is one file project_k.txt that does not adhere to the guidelines. This file incorrectly allows other to have write access. I will need to adjust the permissions to remove the write access.
<br />
<br />
<br />
Using the chmod command I remove the write access  from the file and relist the current permissions to make sure the adjustment was successful: <br />
<br />

![image](https://github.com/J-DONDA/Linux_AdjustingFilePermissions/assets/116527248/f130be7b-e9a9-40a7-bded-098f676fd5fd)
<br />
<br />
The other permissions for the project_k.txt file are  now correct, in only having the read access  enabled.

<br />
<br />
<br />
<br />
<br />

<b>Task 4.) Change file permissions on a hidden file:</b>  <br />

The research team has archived .project_x.txt, which is why it’s a hidden file. This file should not have write permissions for anyone, but the user and group should be able to read the file. 
Again, usng the ls -la command, the permissions are displayed including any potential hidden files (files with a filename starting with a .): <br />

![image](https://github.com/J-DONDA/Linux_AdjustingFilePermissions/assets/116527248/d2020ccf-08c6-4f33-a1fb-2363af6d20e1)

<br />
As shown in the screenshot above, there is a hidden file .project_x.txt . This file incorrectly has write permissions enabled for the user and group, and the group also needs to have read access  enabled.
<br />
<br />
<br />
Using the chmod command I adjust the user and group permissions. Then I use ls -la again to view the permissions to make sure the change was successful: <br />
<br />

![image](https://github.com/J-DONDA/Linux_AdjustingFilePermissions/assets/116527248/f3be2505-1049-470d-86cc-dfc200f35e5d)
<br />
<br />
<br />
The hidden .project_x.txt file now has the correct permissions, allowing user and group to have read only access: <br />
<br />

![image](https://github.com/J-DONDA/Linux_AdjustingFilePermissions/assets/116527248/e5567862-255e-4de5-9840-7232ad9923b0)

<br />
<br />
<br />
<br />
<br />

<b> Task 5.) Change directory permissions:</b>  <br/>

The files and directories in the projects directory belong to the researcher2 user. Only researcher2 should be allowed to access the drafts directory and its contents. 

I used ls -la to view the current permissions:  <br />

![image](https://github.com/J-DONDA/Linux_AdjustingFilePermissions/assets/116527248/fb702f6b-19a7-4dc2-a8ae-b376bf8bb02c)


<br />
As shown above, the drafts directory incorrectly has permissions set up enabling the group with --x execute access.
<br />
<br />
<br />
I use the chmod command to remove this access from the group and re-list the permissions with ls -la to make sure the change was successful: <br />
<br />

![image](https://github.com/J-DONDA/Linux_AdjustingFilePermissions/assets/116527248/82fd1439-968b-49f8-97a2-cf9ab11e1c40)

<br />
<br />
Now the drafts directory has the permissions set correctly, only allowing access to the user: <br />
<br />

![image](https://github.com/J-DONDA/Linux_AdjustingFilePermissions/assets/116527248/0724d609-c16e-487e-8858-d89fc86d9489)

<br />
<br />
<br />
<br />
<br />


<b> Summary:</b>  <br/>

My task was to examine the existing permissions on the file system within the projects directory. I needed to determine if the existing permissions matched the authorization that should be given. I found several issues that I needed to modify the permissions to authorize the appropriate users and remove any unauthorized access.

First, I adjusted the other permissions for the project_k.txt file, removing write access and only leaving the read access  enabled. Then, I adjusted the user and group permissions for the hidden .project_x.txt file, removing write access from the group and adding read access  as well. Lastly, I adjusted the group permissions for the drafts directory,removing the execute access. Now, all files and directories within the projects directory adhere to the guidelines.
</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
