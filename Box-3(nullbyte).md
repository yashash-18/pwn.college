## BOX-NullyByte
### After successfully connecting to the 2nd vm , we need to check for the ip address and then scan it to find all the open ports and we need to explore all the ports under the given services and check for any end points which helps us to know more about the website and find the vulnerabilities and exploit it and find the username ond pass to log in to the 2nd vm and get the root access.
## list all the network interfaces and ip address
<img width="902" height="242" alt="image" src="https://github.com/user-attachments/assets/f3fee22e-2e3d-41e7-833d-43ff447d3f70" /></br>
### ->the target ip address will be in the range of as of our ip address
<img width="801" height="673" alt="image" src="https://github.com/user-attachments/assets/b42f0671-3839-4711-bd24-b4681b03ee4d" /></br>
### -> From the above scan we found the target ip address and the two open ports and their services.
### -> Search the ip address and then it displays a webpage of that.
<img width="1916" height="841" alt="image" src="https://github.com/user-attachments/assets/6e864328-9190-4a41-9dc9-6779b6e966ae" /></br>
### -> Check for robots.txt to get some information or to get the endpoints.
### -> We found that there is no such file exists and only a web page with an image is displayed.
### -> Now lets extract or get the data from the image file.
### -> We need to download some specific tools inorder to extract the data of an image file.
### -> We installed exiftool and extracted the data of the image file .
<img width="557" height="383" alt="image" src="https://github.com/user-attachments/assets/0e49e5b3-4081-4e8b-9484-c067f7c1b9b8" /></br>
### -> We got all the data of the image file and there we got some text in the comment section.
### -> Initially i thought it was password since there is a character p infront of it, but then generally we will search for endpoints after entering the web page(robots.txt), but here there is no such file so lets just assume that the text we got as a path and lets try implementing it in the url.
<img width="974" height="235" alt="image" src="https://github.com/user-attachments/assets/5ed60aef-d7e2-45a3-8bed-7076fe1e43d5" /></br>
### -> Yes what we got in the comment section was actually the path itself.
### -> Now just enter some text inside the key , and we observed that the type of input is 'password'.
### -> Now we need to find the password basically.since there are is no other information related to key, lets brute force it to get the password.
### -> We can use the tool 'hydra' for brute force.
### -> In order to run the hydra we need username, and password which we are going to brute-force it.
### -> There are some usernames and passwords in some files like they are commonly used credentials.
<img width="762" height="123" alt="image" src="https://github.com/user-attachments/assets/784b20db-d7f9-47f7-a88e-c12ac7653598" /></br>
### -> In order to locate the passwords file(rockyou.txt) ,we need to unzip it since it is compressed intially,since it occupies much space.
<img width="1717" height="220" alt="image" src="https://github.com/user-attachments/assets/385311ab-feba-4b7b-a424-c0635a9b2232" /></br>
### -> In the above command -L refers to list of usernames and -P refers to the password and their respective paths and mention the target ip address and its             endpoint ,like where the login form is present and then we need to mention the form variable and an error mesaage to tell hydra whether the password that was sent is correct or incorrect. 
### -> eg: if the input we are giving in a parameter named key,then we need to give it as "/path:key=^PASS^:F=invalid key" here ^PASS^ is a standard place holder         for the password ,so that hydra sents all the passwords into this to test and F refers to fail and invalid key is the message that u receive on the web            page when we type or enter the password and if it is incorrect then the message that is displayed has to be mentioned here and also it is case-sensitive.
### -> After entering the password , a web page with the login form saying to enter username is displayed.
<img width="515" height="177" alt="Screenshot 2026-03-13 180930" src="https://github.com/user-attachments/assets/a0e356f2-c7c4-4761-a5b3-3a3d6cb44f75" /></br>
### -> We found that , if we enter any characters it is taking in and displaying "Fetched data successfully".
### -> Since there is nothing we can do with that so then try searching like are there any tools in order to exploit this situation.
### -> We found a tool named sqlmap which is used to detect and exploit the sqli vulnerabilities and  it can automatically take over database servers once a flaw         is identified.
<img width="1540" height="742" alt="image" src="https://github.com/user-attachments/assets/56a5b264-0694-4df8-9786-9c43bb2089ca" /></br>
### -> We had run the command and mention the target server(url) that was intiated with the message(feteched data successfully) and asked to list all the databases on the target server.
### -> From the above databases  information_schema,performance_schema,phpmyadmin and mysql are the default databases, so the database that is present is seth.
<img width="1206" height="732" alt="image" src="https://github.com/user-attachments/assets/238a2937-e863-4c74-8926-e0d47596362e" /></br>
### -> We had tried to check for any tables in the database(seth), where -D refers to database name and --tables will ask to list all the tables present.
### -> Now we can check for the columns present in the table.
### -> Use this command to list the columns of the table.
<img width="1170" height="82" alt="image" src="https://github.com/user-attachments/assets/471832fa-39fe-4862-86d8-99789459e548" /></br>
<img width="721" height="258" alt="image" src="https://github.com/user-attachments/assets/839ac89e-5911-40f2-8552-16d173780394" /></br>
### -> Now we can ask to dump the data by the command,
<img width="1258" height="63" alt="image" src="https://github.com/user-attachments/assets/9a1c1091-748f-45ce-afb0-f6de0fe21802" /></br>
### -> We got the username and password(encoded). then try decoding the password into plain text .(we get pw=omega,user=ramses)
<img width="1021" height="217" alt="image" src="https://github.com/user-attachments/assets/1aee82dd-6320-4125-9cd6-248226848418" /></br>
### -> Now since we got the credentials , we can try log in to ssh on port 777.
<img width="746" height="325" alt="image" src="https://github.com/user-attachments/assets/95ac3d35-34d5-4597-b362-e5e93097d421" /></br>
### -> search for the sudo privileges by running sudo -l
### -> It says that ramses is not in the sudoers file which means ramses doesn't have any privilejes as of root.
<img width="778" height="151" alt="image" src="https://github.com/user-attachments/assets/4751cb35-70c3-4d94-b001-59d920e44fea" /></br>
### -> On a Linux system, files set to run with root permissions,even when executed by a standard user they have the permissions as of root and they are called           SUID (Set User ID) executables.
### -> Now lets list all the SUID files on the system .
<img width="600" height="47" alt="image" src="https://github.com/user-attachments/assets/711fbc2d-07da-414a-b8e9-6645ac7e51e3" /></br>
### -> -perm 4000 mean it looks for files with the SUID bit set.(where 4000 refers to SUID bit is on(4) and no permissions assigned to owner,group and others(000))
### -> -type f looks for files only and 2>/dev/null refers to hide "Permission Denied" errors so the list stays clean.(since we cant access the root files '/root')
### -> Now look for non-standard binaries (ignore the normal system files like /usr/bin/passwd and search for /tmp,/var/www ..)
<img width="698" height="401" alt="image" src="https://github.com/user-attachments/assets/5d861517-afd8-43c6-bf1a-58028d8a7795" /></br>
### -> We found a file /var/www/backup/procwatch and then list the files.check for the type of file by running the command(file filename).
### -> 
### -> We observe that it is a executable file which mean we need to run the file as ./filename 
### -> Read the file ./procwatch.
### -> Then a table is displayed with PID,TTY,TIME and CMD.generally if u just run the commands in the terminal,then we observe that ps command also displays the         same output with those columns. which means ps command is running process alongside procwatch.
### -> 
### -> generally procwatch calls the ps but it doesn't know where the ps files are located.then it goes to $PATH where some paths are present and it checks in that path and if it found one in any of the path then it wil be included as the ps file and take the path of it.
### -> so now lets create a fake ps file in any directory and then copy the system shell content to that file and export the path since we have created a file with the system shell content in it.
### -> to copy the system shell content run cp /bin/sh /file directory
### -> run export PATH=/filedirectory:$PATH 
### -> if we check for the permissions for the file we created , there is no such permission of execute.so give the permission of execute to that file.
### -> run chmod 777 filename. (it adds the execute permission to it)
### -> 
### -> now go to the procwatch directory and execute it , u will see a root prompt with # in the terminal.
### -> 
### -> now search ls / to list all the directories
### -> now go to the root directory and list the files and read the files.
### -> 
### -> found a .txt file and check the file content.
### ->

























       




 

