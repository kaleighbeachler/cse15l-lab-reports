# Week 9 Lab Report

## Grading Script from Lab 7

```
# Create your grading script here

CPATH=".:../lib/hamcrest-core-1.3.jar:../lib/junit-4.13.2.jar"

echo "Getting Submission"
rm -rf student-submission
git clone $1 student-submission 2> /dev/null
cp TestListExamples.java student-submission/
cd student-submission/

if !  [ -f "ListExamples.java" ]; then
        echo "ListExamples.java not found"
        exit
fi

javac -cp $CPATH *.java 2> compiler_output.txt

if !  [ $? -eq "0" ]; then
        echo "Compile Errors"
        cat compiler_output.txt
        exit
fi

echo "Starting Tests"
java -cp $CPATH org.junit.runner.JUnitCore TestListExamples > test_output.txt
echo "Finished Tests"

FAILED=$(head -n 2 test_output.txt | tail -n 1 | grep -o "E" | wc -l)
TOTAL=$(head -n 2 test_output.txt | tail -n 1 | grep -o "\." | wc -l)
PASSED=$(($TOTAL - $FAILED))
echo "You've passed $PASSED out of $TOTAL tests. Score: $PASSED/$TOTAL"
```

## Screenshots of Student Submissions

[Submission #1](https://github.com/ucsd-cse15l-f22/list-methods-lab3)

Output:
![Alt text](W9%20SS/S1Output.png)


[Submission #2](https://github.com/ucsd-cse15l-f22/list-methods-corrected.git)

Output:
![Alt text](W9%20SS/CorrectOutput.png)

[Submission #3](https://github.com/ucsd-cse15l-f22/list-methods-compile-error.git)

Output:
![Alt text](W9%20SS/CompileError.png)

## Trace of grade.sh

Trace of Submission #2 (Corrected ListExamples file)

```
1: Doesn't run: comment
2: Doesn't run: space
3: Assigns variable
4: Doesn't run: space
5: Prints std output "Getting Submission". Return code is 0. No stderror.
6: Removes current student-submission. No stdout nor stderr. Return code is 0.
7: Clones student submission. No stdout nor  stderr. Return code is 0.
8: Copies TestListExamples into student submissions folder. No stdout nor stderr. Returns code is 0.
9: Opens student submission folder. No stdout nor stderr. Return code is 0.
10: Doesn't run: space
11: If statement evalutes to false because the file is found. Return code is 0. No stdout nor stderr.
12: Doesn't run: in if-statement
13: Doesn't run: in if-statement
14: Doesn't run: closes if-statement
15: Doesn't run: space
16: Compiles files and stores compile error in a text file. Return code is 0. No stdout nor stderr.
17: Doesn't run: space
18: If statement evaluates to false because return code is 0. Return code here is also 0. No stdout nor stderr.
19: Doesn't run: in if-statement
20: Doesn't run: in if-statement
21: Doesn't run: in if-statement
22: Doesn't run: closes if-statement
23: Doesn't run: space
24: Prints stdoutput "Starting Tests". Return code is 0. No stderr. 
25: Runs files and stores output in a file. Return code is 0. No stdout nor stderr.
26: Prints stdoutput "Finished Tests" Return code is 0. No stderr.
27: Doesn't run: space
28: Stores number of failed tests in variable FAILED. Return code here is also 0. No stdout nor stderr.
29: Stores number of tests in variable TOTAL. Return code here is also 0. No stdout nor stderr.
30: Stores number of passed tests in variale PASSED. Return code here is also 0. No stdout nor stderr.
31: Prints the number of passed tests and gives a score (stdout). Return code here is also 0. No stderr.
```