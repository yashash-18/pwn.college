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
<img width="1251" height="486" alt="image" src="https://github.com/user-attachments/assets/f20aac15-7353-4983-b2a5-5863a216f936" /></br>
### -> Yes what we got in the comment section was actually the path itself.

