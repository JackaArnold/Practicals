# Practical 03 - Decision Structures 

**All students (internal and external), please submit your prac work via LearnJCU each week by the due date for your situation.**  

Write your answers for the early non-coding questions in a simple text file called `questions.txt`.  
By now you should be able to use PyCharm easily enough to edit text files. Get started straight away.

## Collaboration 
External students can do the group activities individually.   
Internal students, **form a group of 2 or 3** to do the next two sections (until we get to the programming parts when you can work individually but help each other out if needed).  
Try and remember your new friends' names and use them when you can to help reinforce them in your memory.  
What do they like that starts with the first letter of their name?   

## Quick Questions
For some of the questions below, use the following set values to calculate the result of the expression:  
```python
a = 2
b = 3
c = 4
```

1. What is the "not equal to" operator in Python?
2. What is the "less than or equal to" operator in Python?	
3. b + c * a > a ** b  
4. True or (c ** b - a % b > c ** c)  
5. not True and False or True  
6. (a * b + c) % 2 == 0  

## Patterns
We have learned 5 common **decision patterns** and when to use them (the "best tool for the job"):

1. if, no else
2. if-else
3. if-elif-else
4. if-elif no else
5. if, if, if...
  
**Which pattern** would be the most appropriate choice for each of the following situations: 

1. Deciding what coffee to make based on a customer's order (flat white, cappuccino, piccolo, long black, espresso...)
2. Deciding whether to toast a customer's sandwich  
3. Recording what foods a customer is allergic to (ask for each allergen)
4. Calculating tax based on income - could be one of several tax brackets 
5. Handling the "play again?" question at the end of a computer game level
6. Determining if a frog is poisonous based on its colour
7. Determining if a frog is poisonous based on its colour, tongue length and number of eyes


## Logic Exercise

...

## Note

Before we get on to writing code, we need to highlight a very common error.

When using compound Boolean expressions (sounds fancy doesn't it?) with **and** and/or **or**, you need to make each side of the expression complete.  
Example:
```
if age < 0 or > 100
```
is NOT OK, because the right side (after the or) is just `> 100`
which is incomplete and cannot be determined.  
In English, we often shortcut this when we speak (e.g. the above could be said "if age is less than zero or greater than one hundred") – makes sense to us, but in pseudocode and code, you can't take that shortcut.  
You need to restate the variable to make the expression complete so that the code can run (and so pseudocode makes sense).  
Example:
```
if age < 0 or age > 100	
```

## Python Coding - Decision Structures

As you do individual work on your computer, if you need help, start by talking to your peers.  
External students are encouraged to use Slack to ask questions of others in the class.

### Example
Let's walk through a complete example, from problem description, through problem solving to code and testing.  
Just read along and understand. Do not "do" any of this, just read it and make sure you understand.  
Use this example (and the lecture teaching) as a reference when you do your own work.
 
#### Problem Description:
The Automated Steakhouse needs a program to tell customers how long they can expect to wait for their steak.  
The customer has three options: "rare", "medium" and "well-done" - 
if they enter anything else, they receive an error message.  
Rare steaks take 2 minutes to cook, medium steaks take 4 minutes to cook, and well-done steaks require 6 minutes.

When we decompose the problem, looking for nouns, verbs and "decision" words, we can see things like "options" and "if", so we're going to be using decisions.  
We can see multiple cases/paths and their conditions.  
Also, we can tell that there is a default case - the error message. 

What pattern will we use?  
This looks like a menu-style problem and has multiple cases with a default, so...  
It's clearly the **if-elif-else** pattern.

### Algorithm

Notice that in pseudocode we use "else if", not "elif", since "elif" is code specific to Python, and it means "else if".  

```
get choice
if choice == "rare"
    display "2 minutes"
else if choice == "medium"
    display "4 minutes"
else if choice == "well-done"
    display "6 minutes"
else
   display error message
```


### Code

```python
choice = input("Steak choice (rare, medium or well-done): ")
if choice == "rare":
    print("2 minutes")
elif choice == "medium":
    print("4 minutes")
elif choice == "well-done":
    print("6 minutes")
else:
    print("Ain't no steak like that here")
```

### Testing
Remember that when testing decision structures, you should use test data to produce each path/output.  
There are 4 possible paths here, so we need to test each one.

| Input | Expected Output | Actual Output |
|---|---|---|
| rare | 2 minutes | ? |
| medium | 4 minutes | ? |
| well-done | 6 minutes | ? |
| anything | Ain't no steak like that here | ? |


### Things to do

Create a new Python file, `example.py` (File > New > Python File)    
**Now, you type this code in (don't copy it)**, and **test it** with the planned test values.  
As you type into PyCharm, watch how it helps you complete the task. E.g. when you press Enter after a colon, it automatically indents.  
You should also try typing your `elif` or `else` statements completely before you indent/outdent and watch to see that PyCharm automatically puts them in the right position!

Now, make these changes to help you understand the code:

- Add another case: "burnt" should take 8 minutes
- Try testing with "Rare" instead of "rare". What happens?  Apparently `"Rare" != "rare"`, but you knew that.

We could handle this using something like:
```python
if choice == "rare" or choice == "Rare":
```
**but** what about `"RARE"`, isn't that also the same thing?  

We are going to jump ahead to some string processing and learn to use the `lower()` method...  

We can essentially ignore the case by converting our choice string to lower case. We can either do this for each and every case, or (better), just when we get the input.  
Try this in your code now:  

```python
choice = input("Steak choice (rare, medium or well-done): ").lower()
```

So, we get the string and convert it to lower case, which means "Rare" or "RARE" or "RaRe" become "rare".  
Nice.

Test this and see if it works.

# Exercises
 
Write all of your answers to the following questions in a single Python file called `programs.py`  
At the top of each program, put a **comment** (starts with a `#`) with the exercise number/name (copy-and-paste it from here) so you/we know what the program is for later.  
Example:

```python
# 2. Miles to Kilometres
number_of_miles = int(input("Miles: "))
...
``` 

## 1. Tax
The following problem is partly done for you. Complete your parts:

The Python Party wins government at the next election and introduce a simpler tax system that works like this:

- If you earn under $100, you pay no tax
- If you earn between $100 and $1000, you pay 5% tax on the total amount
- If you earn over $1000, you pay 10% tax on the total amount

First, think of what decision pattern applies.
Write the pseudocode for this (in comments), then code up the solution, some of which is started for you below.  
Note the good use of constants.   
Get used to using the IDE to finish off these long names, so you don't have to type them. 
Make sure to only put your calculation for `take_home_pay` in one spot - it doesn't need to go in each path of the if-elif-else statement.

```python
TAX_RATE_LOW = 0.05  # 5%
TAX_RATE_HIGH = 0.1  # 10%
TAX_THRESHOLD_LOW = 100
TAX_THRESHOLD_HIGH = 1000

print("Python Party Tax Program - Where Tax is a Party")
income = float(input("Income: $"))
# TODO: complete this part of the program here
total_tax = 0
take_home_pay = 0

print("Total tax is: $", total_tax, sep="")
print("Take home pay is: $", take_home_pay, sep="")
```

Here is some sample output for two runs of the program, so you know what to test it with ("known-good" data).

```
Python Party Tax Program - Where Tax is a Party
Income: $10000
Total tax is: $1000.00
Take home pay is: $9000.00

Python Party Tax Program - Where Tax is a Party
Income: $595
Total tax is: $29.75
Take home pay is: $565.25
```

Again, don't worry about the 2 decimal place currency formatting. We will get to that later.

### Comment Out
Remember that you can **comment out** code so it doesn't run by selecting the lines of code (doesn't need to be exact characters, just any part of the right lines) and press `Ctrl+/` (Windows) or `Cmd+/` (Mac).  
Remember also to do this shortcut again when you're finished so that it looks like normal code again - all programs will run - before you submit your work.

## 2. Car Insurance

Car rental company Painz determines whether a renter requires special insurance based on their age.  
Applicants under 18 are refused hire altogether. 
Applicants under 25 are required to purchase special insurance. 
Applicants 25 years and over are not required to purchase insurance.
Painz needs you to write a program that gets the applicant's age, and outputs "Insurance required", "Insurance not required", or "Hire refused" as appropriate.

## 3. Simple Password Checker

Write a program that has a secret password stored as a constant, and checks a user's password against it.  
Use string comparison to print either "Access granted" or "Access denied" depending on if the user's password matches the secret.


## 4. Dog Years
Write a Python program to calculate a dog's age in dog years.  

To do this – Each year of the first two human years is equal to 10.5 dog years.
After that, each human year equals 4 dog years.

Expected Output:
```
Age in human years: 15
Age in dog years is 73
```

### Don't Repeat Yourself
**Note:** "Don't Repeat Yourself" (DRY) is an important programming principle.  
In this program, and many of your others, you will have a single output that depends on the True/False value of one or more conditions.  
But whatever the result, you print `Age in dog years is ...` so the only difference is the value.  
Calculate the value in the True path and False path (two calculation lines), but do the printing only once _outside_ the paths - no matter what the result of the condition/s.

## 5. Rock Of Ages

Ask the user for their age, then tell them what you think of them.

- Use a **compound Boolean expression** to test if the age is valid (between 0 and 120 inclusive); print "Invalid age" if not.
- Then print your own personal response for how old they are. You decide how many different responses you want.

## 6. Speeding Fines

[Current penalties for individuals caught speeding in Queensland](https://www.tmr.qld.gov.au/Safety/Driver-guide/Speeding/Speeding-fines-and-demerit-points.aspx) are: 

| Infringement                                                   | Penalty amount | Demerit points |
|----------------------------------------------------------------|----------------|----------------|
| Less than 13km/h over the speed limit                          | $177           | 1              |
| At least 13km/h but not more than 20km/h over the speed limit  | $266           | 3              |
| More than 20km/h but not more than 30km/h over the speed limit | $444           | 4              |
| More than 30km/h but not more than 40km/h over the speed limit | $622           | 6              |
| More than 40km/h over the speed limit                          | $1,245         | 8              |

Avoid a 6 month suspension by writing a program to ask for the user's speed, the speed limit and then tell them their penalties.


# Practice and Extension

These final sections in practicals are _not required_ to be completed for marks, but you will definitely find benefit in completing them for extra practice and to extend yourself.  
The more practice you do, the more you develop and "lock in" your new skills.  

Create a new file, `practice.py` to complete these tasks in:

## Coffee Pour and Grind

As all good baristas know (right, Raven?), the length of time a shot of coffee pours indicates if the grind level is right:  

- 25-35 seconds = OK, leave it
- under 25 seconds = grind finer (so it pours slower)
- over 35 seconds = grind courser (so it pours faster)

Write an algorithm, then a program, to help create a robot that replaces the barista.  
Give it a cool beard, maybe some tattoos and engaging conversation so the customer still feels the love.   

## Good morning, good evening and good night.

Write 4 different versions of a time-based greeting program.  
(You will use different decision patterns for some of these, as appropriate.)  

In each case, ask the user for the hour of day (0-23).

1. If it is morning, print "Good morning" (otherwise do nothing) 
2. If it is morning, print "Good morning"; if night time, print "Good night"
3. Print either: Good morning / good afternoon / good night
4. Print either: Good morning / good afternoon / good evening / good night

## Pool pH

Given pool pH level:

- 7.4 - 7.6 is ideal, no change
- Below 7.4, is too acidic, add soda
- Above 7.6 is too alkaline, add acid

## JCU Grades
[Grades at JCU work like this](https://www.jcu.edu.au/students/exams-and-results/subject-results-explained) depending on your final percentage for a subject.  

I think you know what to do...  
Write a program to tell a student what their grade is based on their input subject percentage. 

| Grade | Percentage |
|-------|------------|
| HD    | 85%-100%   |
| D     | 75%-84%    |
| C     | 65%-74%    |
| P     | 50%-64%    |
| N     | < 50%      |

## Extension

### Divisibility
Write a program that takes two numbers, and prints "Divisible" if the first is divisible by the second, and "Not divisible" otherwise. 

## Steak ++
Automated Steak House wants version 2 of their program.

- add a default minimum order time as a constant 
- handle the outputs as the extra cooking time plus this minimum, so if the minimum is 3 minutes, a rare steak will take 5.

You should notice that to handle this properly, you will need to replace your fixed outputs with a calculation (e.g. not "2 minutes", but 3 + 2).  