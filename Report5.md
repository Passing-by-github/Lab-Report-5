This is an actual bug that I had to debug while doing this report, and my thought proccess through it: 

Part 1 – Debugging Scenario
---
**Edstem post:**    
Hello, I get a compiler error message when using the student submission that has the correct methods: 

![image](https://github.com/Passing-by-github/Lab-Report-5/assets/130006613/8b1d6740-c5ff-4790-839f-a7ce09d471b8)

Here's my code when compiling and my if statment: 

![image](https://github.com/Passing-by-github/Lab-Report-5/assets/130006613/2d6e261a-3350-40f7-8894-b8b6a8026105)

I don't know why this is happening, but I think it might have to do with my if statment. (this was my actual guess). 

**Response:**

Hi! if you want to know if the error is from the if statement, you should check that the statment is getting the correct exit status by printing it out. Also, could you show the compile error message? (I forgot to check it lol).   

**Student Response:**    
Oh, sure! I get my exit status as one so that means my code didn't compile correctly:   
![image](https://github.com/Passing-by-github/Lab-Report-5/assets/130006613/4edd6d37-8ebe-41ba-acb5-8ad359f1105e)    
I get that it says compile successful and I now that because it's checking a different line now. 

My compiler error is this:   
![image](https://github.com/Passing-by-github/Lab-Report-5/assets/130006613/0b4858f7-23ea-49fc-b89e-5c06399c4651)
![image](https://github.com/Passing-by-github/Lab-Report-5/assets/130006613/83463c03-1acf-4ae3-b3df-32372f13fb1b)


So it's saying that my `Server.java` and `GradeServer.java` have duplicate classes when there are none within the `grading-area` directory:
![image](https://github.com/Passing-by-github/Lab-Report-5/assets/130006613/5e5e96a4-c2a4-4b7f-b95b-30ab58c272c7)   

I would assume it has to do with the files `Server.java` and `GradeServer.java` that are outside of the directory but that makes no sense. 

**Response:**
Well, you are correct with how the `Server.java` and `GradeServer.java` are outside of `grading-area` and shouldn't affect each-other, but if you compile both of them at the same time it would cause problems. Your `javac` command should look like this: 

`javac -cp $CPATH grading-area/*.java 2> grading-area/compile-error.txt`   

Essiensially without compiling the files outside `grading-area`.  

Also you get the error that `package org.junit does not exist`, so double check if you're using the correct `CPATH` string that is compatible with your system.    
Mac: `.:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar`   
Windows: ` ".;lib/hamcrest-core-1.3.jar;lib/junit-4.13.2.jar"`  
Hope this helps! 

**At the end, all the information needed about the setup including:**
*The contents of each file before fixing the bug:*
I showed what I would've had on an edstem post for for accuracy's sake, but here's the full `grade.sh` file:       
![image](https://github.com/Passing-by-github/Lab-Report-5/assets/130006613/9e78093e-1449-49fc-b1c6-20e2ba9c2d6c)    
The new and improved `grade.sh:  
![image](https://github.com/Passing-by-github/Lab-Report-5/assets/130006613/08d1dde8-5d22-4a87-bd04-4c37e0e56972)  

 
And for completion's sake, here's `Server.java`:   
![image](https://github.com/Passing-by-github/Lab-Report-5/assets/130006613/86413607-55ee-4bb3-b9f9-850a3f7773f2)                  

And `GradeServer.java`:    
![image](https://github.com/Passing-by-github/Lab-Report-5/assets/130006613/99c6982f-0b1b-4b20-ae86-09936a1050fa)
![image](https://github.com/Passing-by-github/Lab-Report-5/assets/130006613/38b0b7ff-eb72-42d8-9dd4-ffb9f4048d13)       

Part 2 – Reflection
---


I've always seen the terminal as an interesting place that's between us and our Java files. Through these past few labs, we learned how to interact at more deeper level with the terminal. Blurring this obvious line as we learn how to make bash scripts that run commands on the terminal itself then using the process class in Java files as well. Then the separation completely disappears when vim comes along and make us able to edit Java files on the terminal. I've learned that the terminal isn't just some subspace to run files, but is an important tool that I could use for my benefit as a programmer and I believe that fact alone is of the most important things that I've learned from this class. 
