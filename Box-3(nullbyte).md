## BOX-NullyByte
### After successfully connecting to the 2nd vm , we need to check for the ip address and then scan it to find all the open ports and we need to explore all the ports under the given services and check for any end points which helps us to know more about the website and find the vulnerabilities and exploit it and find the username ond pass to log in to the 2nd vm and get the root access.
## list all the network interfaces and ip address
<img width="902" height="242" alt="image" src="https://github.com/user-attachments/assets/f3fee22e-2e3d-41e7-833d-43ff447d3f70" /></br>
### ->the target ip address will be in the range of as of our ip address
<img width="842" height="531" alt="image" src="https://github.com/user-attachments/assets/8e92f643-2cac-4b28-86dc-236c810ce568" /></br>
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
### -> In the above command -L refers to list of usernames and -P refers to the password and their respective paths and mention the target ip address and its endpoint ,like where the login form is present and then we need to mention the form variable and an error mesaage to tell hydra whether the password that was sent is correct or incorrect. 
### -> eg: if the input we are giving in a parameter named key,then we need to give it as "/path:key=^PASS^:F=invalid key" here ^PASS^ is a standard place holder for the password ,so that hydra sents all the passwords into this to test and F refers to fail and invalid key is the message that u receive on the web page when we type or enter the password and if it is incorrect then the message that is displayed has to be mentioned here and also it is case-sensitive.
### -> After entering the password , a web page with the login form saying to enter username is displayed.



