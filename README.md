# Docker-Project
For this project I followed a guide from Medhat Elmasry building a PHP and MySQL Web App. I added my own twist by cloning an HTML page and adding it to the web page.
1. To start, you need a linux machine running with Docker installed, navigate to (https://docs.docker.com/get-docker/) to get started.
2. From your home directory, create and change to a new directory for this project, I named mine _php-mysql-app_: ```mkdir php-mysql-app``` followed by ```cd php-mysql-app```. Your command line should now look like this:<br/>![image](https://user-images.githubusercontent.com/71033480/155025361-f91cb2a8-f1c6-4fd1-85ae-26094774ef1e.png)
3. From within _php-mysql-app_ create a directory called _src_, this will be used to store the source code: ```mkdir src```.
4. Inside of _src_ create a text file called _index.php_: ```vi index.php```. Using _vi_ will create and open the file to edit. [This](https://github.com/coledavisbrand/Docker-Project/blob/main/src/index.php) code is what you need to connect to the MySQL database. The HTML is used to list the current databeses that exist on the MySQL server. Feel free to edit the HTML to make it your own. Copy the code from the link above into your _index.php_ file to continue.
5. By running ```cd ..``` return to the parent directory (php-mysql-app).
6. Create a file called _Dockerfile_: ```vi Dockerfile```. This file will be used to create a Docker image that contains the web app with Apache and PHP. Fill _Dockerfile_ with [this](https://github.com/coledavisbrand/Docker-Project/blob/main/Dockerfile) code.
7. The last step in the configuration is to create a _docker-compose.yml_ file. Do this in the parent directory (php-mysql-app): ```vi docker-compose.yml```. Fill _docker-compose.yml_ with [this](https://github.com/coledavisbrand/Docker-Project/blob/main/docker-compose.yml) code. This file is used to create the two containers that is needed for this project.
8. To check and make sure that all your files exist, and exist in the proper directory. Run ```tree``` from the parent directory (php-mysql-app). In my case I added an HTML file (info.html) to the _src_ directory (not needed for functionality). The results should look like this:<br/>![image](https://user-images.githubusercontent.com/71033480/155027957-ef8ed0af-dfd4-4766-93fc-186ee7b7e5a6.png)<br/>To install tree on your linux machine reference [this](https://www.javatpoint.com/linux-tree-command) site.
9. Now you are ready to test functionality. Run this command ```docker-compose up```. Give the machine a minute to configure the containers and complete any needed instalations.<br/>![image](https://user-images.githubusercontent.com/71033480/155028767-73120a6e-5dc6-45a9-b8df-d0e8fcf7bac4.png)<br/>Once you see this line, your configuration is complete and your server up.
10. To check this, navigate to the IP of the machine that is running Docker, at port 8080, from your browser. Example: ```192.168.1.2:8080```
