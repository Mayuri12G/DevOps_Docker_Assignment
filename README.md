1. Firstly, I create test.sql file which contains create table query and some insert opertions that we can do after executing bash with mysql monitor.

2. Write a dockerfile 
  'FROM' keyword tells which base image you want to use. 
  In our example, we are creating an image from the mysql image.
  The ENV command is used to set environment variable. We set MYSQL ROOT_PASSWORD to root.
  Add a database pucsdStudents and creating user pucsd with password pucsd.
  
  The command copy the database backup file to /docker-entrypoint-initdb.d directory in the Docker container. 
  The docker-entrypoint.sh file will run any files in this directory.
  In our example, we have only one sql script file test.sql.
  The EXPOSE command exposes port 3306 of the image.

3. After writing this two files we have to work through terminal
   Commands that I use,
   
   docker build . -t mytestsql:0.1
   docker run -itd mytestsql:0.1
   docker ps
   docker exec -it d8507b5b73c7 bash
   mysql -upucsd -p
   use pucsdStudents
   show databases;
   show tables;
   select * from studentData;


   docker build . -t mytestsql:0.1
   Here, mysqltest is the name we are giving to the Image and 0.1 is the tag number. 
   The last dot . indicates the current location. 
   Check whether the image is created. Try with 'docker images'.
   
   docker run -itd mytestsql:0.1
   This command is used to run docker container based on a given docker image.
   As argument to docker run you pass the name or image ID of the Docker image you want to run a container.
   It shows like returning some id.
    
   check with 'docker ps' that your container is running now.
   
   docker exec -it d8507b5b73c7 bash
   executing this command you can see it enter into root of id d8507b5b73c7 of your conatiner.
   Now you are ready to use mysql.
   
   mysql -upucsd -p
   After that you have to enter in user which we already created in dockerfile and enter the password.
   Now you are ready with your mysql connection connect to database which is already created you can do create insert operations manually even.
   
   
   
