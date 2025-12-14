# Python Scripting Exercise

## Overview

**Python scripting** streamlines tasks on different platforms, enabling efficient file and directory manipulation, text processing, and system administration.

- Python scripts empowers users with automation tools for enhanced productivity, workflow optimization, and scalable solutions across domains like development, data science, and system management.
- Python's versatility and extensive library ecosystem make it a valuable tool for creating automation solutions.

## In this challange lab i have to write a Python script based on the following requirements:

- Display all the prime numbers between 1 to 250.
- Store the results in a results.txt file.
- Test the script. Verify that it produced the expected results in the results.txt file.
- Save the script and make a note of its location (absolute path) for future reference.

---

## Task 1

**I used SSH to Connect to the Linux Host**


### **Step 1: the initial Preparations to start up linux**

- In the AWS Management Console, i had to select the EC2 instance and make note of the **Public IPv4 address**
- i downloaded the private key file (`labsuser.pem`).

### **Step 2: Here i established SSH Connection**

- I connected to the instance using the `ssh` command, the key, and the instance's Public IPv4 address.

<img width="944" height="469" alt="Screenshot 2025-11-11 023923" src="https://github.com/user-attachments/assets/9e605acd-81ce-4b9c-936c-5b81be3d2c7e" />


## Task 2

**Python Scripting Solution**
- In this solution i will be writing the Python script (`challenge-lab.py`) to execute the prime number calculation and file output.

### Step 1: I imported the os module.

- I enterd the code "**import os**"
-This code will intstall the os module
- This OS module provides a way to interact with the operating system.
- It is wahat i  will use to perform arious system-related operations such as file manipulation, directory operations, and executing system commands.


### Step 2: I created the results.txt file using the touch command 

- I enterd the code "**os.system("touch results.txt")**".
- I used the os.system() function to run a system command from within a Python script.
- The command "touch results.txt" is a Unix/Linux command that creates a new empty file named results.txt in the current directory.
- I used this command because is commonly used to create files or update the timestamp of existing ones.

### Step 3: In this step i display the prime numbers;

- for number in range(1,251): it iterated through numbers from 1 to 250.

- prime = True Assume the number is prime initially.

- for the divider in range(2,number): it itarated through dividers from 2 to number-1.

- if number % divider == 0: it will check if number is divisible by any divider.

- prime = False If divisible, the number is not prime.

- if prime == True: Check if the number remains prime.

- os.system("echo " + str(number) + " | tee -a results.txt") Print and append the prime number to results.txt..
  
<img width="1145" height="352" alt="Screenshot 2025-12-14 214657" src="https://github.com/user-attachments/assets/9d8add9f-192f-430c-9c9e-28459ab67043" />

### Step 3: Typing the script.

- Here I typed the script using the Vim text editor.
- I included comments using # to enhance the readability of the code.
- After saving the changes and i ended the lab by closing the editor.

<img width="1046" height="422" alt="image" src="https://github.com/user-attachments/assets/f3ae847c-30f0-4db1-9942-58a2c9d7c826" />


## Task 3

**here i tested the script and ensured that it is properlt stored**

## Step 1: Testing the script.

- I used the command "**python3 challange-lab.py**
- To test the script i executed it using by using python 3
- It displayed all the prime numbers between 1 to 250 got displayed.
<img width="757" height="540" alt="image" src="https://github.com/user-attachments/assets/b231298c-959e-45b6-a0de-05cb58da9f2e" />

## Step 2: for the final step I verified the storage.

- I enterd the command, "**cat results.txt**" to view the contents of the "results.txt" file.

## Conclusion
- The import statement lets you use extra tools (modules) in your Python code.
- Functions like os.system() allow your script to run system commands, while loops and range() help repeat actions over a set of numbers.
- The if statement lets your code make decisions by checking conditions and choosing what to do next.

