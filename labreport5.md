# Lab Report 5:

## Bash code for grader:

```
rm -rf student-submission
git clone $1 student-submission
echo 'Finished cloning'

if ! test -f ./student-submission/ListExamples.java ; then
    echo "ListExamples.java not found"
    echo "Grade: 0/3"
    exit 1
fi
echo "Found ListExamples.java"

cp TestListExamples.java ./student-submission/TestListExamples.java
echo "Moved tester file"

javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar -d ./ ./student-submission/*.java
if ! test -f ./ListExamples.class ; then
  echo "Compile failed."
  echo "Grade: 0/3"
  exit 2
fi
echo "Compile successful"

java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore TestListExamples > results.txt
rm -rf *.class
grep -i "Tests run: [0-9],  Failures: [0-9]" results.txt > grep-results.txt
if ! test -s grep-results.txt ; then
  echo "Grade: 3/3"
  rm -rf *.txt
  exit 0
fi

failed=$(cut -b 26 grep-results.txt)
echo -n "Grade: "
echo -n $((3-$failed))
echo "/3"
rm -rf *.txt
```

## Basic Explanation:
1. If an existing folder named "student-submission" exists, remove it
2. Clones the given repository
3. Checks if "ListExamples.java" exists inside repository
4. If the file does not exist, give a grade of 0 and exit
5. Copies tester into student-submission folder
6. Compiles all files in student-submission folder
7. If compile fails, give a grade of 0 and exit
8. Runs tester and puts result into "results.txt"
9. Looks for the regex case "Tests run: \[0-9],  Failures: \[0-9]" and puts the results in grep-results.txt
10. If no such file exists, the text was never found and thus the test ran successfully. In this case, the grade gives full score and exits
11. Finds number of failed tests from "grep-results.txt"
12. Calculates and prints score
13. Deletes all temporary ".txt" files

## Test 1: Unedited Code from lab 3
![](https://raw.githubusercontent.com/alanycwang/cse15l-lab-reports/main/Screen%20Shot%202023-03-12%20at%2010.57.18%20PM.png)

## Test 2: Correct Code
![](https://raw.githubusercontent.com/alanycwang/cse15l-lab-reports/main/Screen%20Shot%202023-03-12%20at%2010.59.17%20PM.png)

## Test 3: Missing Semicolon
![](https://raw.githubusercontent.com/alanycwang/cse15l-lab-reports/main/Screen%20Shot%202023-03-12%20at%2010.59.25%20PM.png)

## Test 4: Switched Filter Arguments
![](https://raw.githubusercontent.com/alanycwang/cse15l-lab-reports/main/Screen%20Shot%202023-03-12%20at%2010.59.36%20PM.png)

## Test 5: Incorrect Filename
![](https://raw.githubusercontent.com/alanycwang/cse15l-lab-reports/main/Screen%20Shot%202023-03-12%20at%2010.59.51%20PM.png)

## Test 6: Nested Directory
![](https://raw.githubusercontent.com/alanycwang/cse15l-lab-reports/main/Screen%20Shot%202023-03-12%20at%2010.59.59%20PM.png)
