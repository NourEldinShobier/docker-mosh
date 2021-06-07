# The ultimate docker course

A `Dockerfile` is a text document that contains all the commands a user could call on the command line to assemble an image.

A `Docker image` is a read-only template that contains a set of instructions for creating a **container** for example:

![hh](./assets/1c6ea4aacd1609507284547e8cdbba6aaa228fd2.png)

Once we have an image, we tell docker to start a container using that image.

---

### Dockerize a Node app

1) Create `Dockerfile`

```dockerfile
FROM node:alpine # base image
# (.) copy all files from current directory
# (/app) into /app directory inside the image
COPY . /app
# command to launch our app
CMD node /app/app.js

# OR

WORKDIR /app
CMD node app.js
```

2. Build the image (Put image into container): `docker build -t tag_name .`
   
   1. `.` : means that `Dockerfile` exist in current directory.

3. Display all docker images: `docker images ls`

4. Run the image: `docker run tag_name`

> To download an image: `docker pull image_name`

---

### Linux commands

- `docker run ubuntu` : This command will pull the image if not found locally and run it

- `docker ps` : displays list of running containers
  
  - `docker ps -a` : displays list of running + stopped containers

- `docker run -it ubuntu` : run ubuntu in interactive mode
  
  - run ubuntu shell

- `docker start -i 2f7` : run docker container in interactive mode and provide first parts of the container id

#### <u>Commands</u>

- `whoami` : shows the current user

- `echo $0` : shows the shell directory

> notice that ubuntu uses forward slash `/`

##### Package managers (apt)

- `apt list` : shows list of installed packages

- before running `apt install package_name` always run `apt update`

- `apt remove nano`_

##### File system

- `pwd` : print working directory

- `ls` : print directory files
  
  - blue text represent directories
  - `ls -a` : show all files including hidden ones

- `cd` :
  
  - relative path: starts from the current directory
  
  - absolute path: start form the root directory `/`
  
  - `cd ..`
  
  - `cd ~` : to move to home directory

- `mkdir hello` create directory

- `mv hello docker` rename directory
  
  - `mv hello /etc` : this will move the hello directory to etc directory **in the root folder**

- `touch hello.txt blabla.txt` to create files

- `rm file.txt file2.txt` : to remove files
  
  - `rm file*` : the pattern will remove files that start with `file`
  
  - `rm -r directory_name` :  the `-r` means recursively and used with directory

- `cat file.txt` to read file
  
  - `more file.txt` to read long files by pagination
  
  - `less file.txt` is better than more, it enables you to move up/down in the file
  
  - `head -n 5 file.txt` to read first 5 lines
  
  - `tail -n 5 file.txt` to read last 5 lines

- `cat file1.txt file0.txt > file2.txt` to copy file1 content to the end of file2
  
  - `>` : redirect operator

- <u>search text in files: lesson 20</u>

- `find` : to find files and directories (in the current directory)
  
  - `find -type d` : find directories, to find files replace `d` with `f`
  
  - `find -type f -name "f*"` : find all files that start with f
  
  - `find -type f -iname "f*"` : `iname` is case insensitive
  
  - `find / .......` : find files and directories starting from root directory

- `...;...;...` : chain commands
  
  - `... && ...` : chain commands and if one fails, execution stops
  
  - `... || ...` : executes either the first or the second 
  
  - ` .... | ....` : (pipes) takes output of the first command as input to second

- `printenv` : print env variables
  
  - `printenv PATH` is equal to `echo $PATH` to print env variable
  
  - `export DB_USER=mosh` to set variables  -> available for only current session

##### Processes

- `ps` to print running process

- `sleep 3 &` : the `&` create process in the background

- `kill 38` kill process with `pid` 

##### Manage users (25, 26)

##### Files permission

- `ls -l` to print all files with their permissions

- `chmod` : is used to change user/group/other permission

---

# Docker
