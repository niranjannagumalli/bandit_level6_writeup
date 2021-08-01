# bandit_level6_writeup



Hello everyone ,I am Niranjan and this is my writeup on the wargame bandit's 6th level.
## Login & password details

To enter this level,you will have to ssh to bandit level 6 

`ssh bandit6@bandit.labs.overthewire.org -p 2220`

and the password is 

`DXjZPULLxYr17uwoI01bNLQbtFemEgo7`


## Problem statement

![Info about problem](https://user-images.githubusercontent.com/87712842/127764432-608af0a9-3bcc-42b0-a271-92ee33e1c1cd.png)

## Disserting the problem

On reading the statement  we know we have to find a file which  is 
     * located somewhere on the server
     * owned by user bandit7
     * owned by group bandit6
     * 33 bytes in size
     
On seeing the recommended commands we find the ***find*** command which I think will help in my search for the required file.

 So without wasting time lets check the [man](https://en.wikipedia.org/wiki/Man_page) page of ***find*** 
 
`man find`

From reading the initial lines we can understand that this is the right command to find that file.

Now we have to find the right flags (i.e the way to convey our requirements associated with the command) 


  1. /
-----
  Since our file is located somewhere on the server we must add the flag which allows the ***find*** command to check all the files on the server. So we will add  **/** after ` find ` which will  check all the file from the root directory.
 
-----

  2. -user
  -----
  Our required  file is owned by user named bandit7.Upon referring the man page of ***find*** we will find that the required flag or this action will be 
  
  
   ![-user in man page of find](https://user-images.githubusercontent.com/87712842/127764238-c3f63338-ffc1-4b8f-880d-c2f7e9e3033a.png)
   
     so our command becomes 

     `find / -user bandit7`
-----


  3. -group


-----
  On searching in the similar way for group:
  
  
   ![](https://user-images.githubusercontent.com/87712842/127764246-5ad9aea4-5336-4caa-896a-85228c2dbf42.png)
 
   
   
   
   so our command will become
 
    `find / user bandit7 -group bandit6`   

-----


4. -size

-----
   On searching in the similar way for size :
   ![size from man find](https://user-images.githubusercontent.com/87712842/127764252-b383dc65-9372-42bf-9b9b-378bd2bf5140.png)
  
   Therefore our command becomes 
   `find / -user bandit7 -group bandit6 -size 33c`
  
-----


## Result

when executed this was the output displayed.

![output](https://user-images.githubusercontent.com/87712842/127764253-ea1eef95-47ee-4c11-b51d-778849c3c8cb.png)

Here,the  location of the 4th file end  is accessible by us as well as satisfies all the required conditions.

Lets check the contents of the file

![password](https://user-images.githubusercontent.com/87712842/127764254-12034ff5-032f-4665-96a2-22eca7264e7d.png)  
The password for the next level is ***HKBPTKQnIay4Fw76bEy8PVxKEDQRKTzs*** 
-----
***THE END***
