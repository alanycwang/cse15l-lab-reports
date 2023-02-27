# Lab Report 4:

## Lab Competition Procedure: 

1. ```<up>```
2. ```<enter>```
3. Paste:
```
git clone git@github.com:alanycwang/lab7.git
cd lab7
javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java
java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore TestListExamples
sed -i  '43 s/1/2/1' ListExamples.java
javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java
 java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore TestListExamples
git add .
git commit -m test
git push
```
## Explanation:

 - Pressing the up button brings up the last command used, which, given the right setup, should be ```ssh cs15lwi23axi@ieng6.ucsd.edu```
 - After logging in automatically (due to our ssh key), we paste in the code above, which executes each line sequentially, almost like a bash file.
 - ```git clone git@github.com:alanycwang/lab7.git``` clones the repository to the home directory
 - ```cd lab7``` moves us to the newly cloned repository
 - ```javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java``` compiles the code
 - ```java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore TestListExamples``` runs the JUnit tests
 - ```sed -i  '43 s/1/2/1' ListExamples.java``` replaces the first ```1``` character on line 43 of ListExamples.java to ```2```, fixing the bug
 - We then recompile and run our code
 - ```git add .``` adds all changes to the next commit
 - ```git commit -m test``` commits our changes
 - ```git push``` pushes our changes to github