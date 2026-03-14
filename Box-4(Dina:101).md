## BOX-Dina:1.0.1
### -> 
### -> scan the target ip address and get the open ports and their services.
### -> 
### -> search the ip address and view the web page.
### -> check the robots.txt file and get the endpoints if present
### -> 
### -> when we explore page source of nothing ,then we got few secret passwords in that page.
### -> 
### -> now lets scan the target ip address to get more information by using a tool named nikto.
### -> 
### -> found a directory name 'secure' in the scan.
### -> 
### -> when we follow the path ,we found a zip file and after downloading, it asks us for password and we have a list of passwords already so trry checking all the passwords and unzip it.
### -> now find the type of file.we observe that it is a text file. so read the content of that file.
### ->
### -> we found a new path, follow the path and then it displays a login form containing username and password.
### -> 
### -> the username is already given in the text file(user-touhid) and now try check the passwords that we got initially and get the access into it.(pw=diana)
### -> 
### -> 

