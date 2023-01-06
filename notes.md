---
marp: true
theme: gaia
class: invert

---
# [TITLE]
---

## Module 3
[DESCRIPTION]
#
### 3.1
#### Performing operations (part 1)
#
#### Notes:
[TEXT]
##### Lesson Task 1:
Create a script called CalculateVolume.py. An engineer wants to calculate the volume of a rectangular tank using the formula length width height. The program needs to request these three values as input from the user and store them in three different variables. Using these three variables, calculate the volume of the tank and store it in a fourth variable. The engineer has learned from experience that measurements and calculations are always a bit short of the volume the tank can store because the plastic tank expands when filled. Therefore, he requires that the script increase the calculated volume of the tank by 1% before displaying the resulting volume to the user.

```py

```
#
##### Lesson Task 2:
Create a script called TimeCalculation.py. A manager has requested that you write a script that allows him to enter a value representing the number of minutes one of his employees has worked in a month. He wants the script to use the number of minutes to calculate the number of days worked in the month, the number of hours left over (not adding up to a full working day) and the number of minutes left over (not adding up to a full hour). For the sake of this calculation, a working day consists of eight hours. Once calculated, display the resulting calculation in the following format: working days:hours:minutes.
#
##### Lesson Task 3
Create a script called PizzaShop.py. A pizza shop owner has asked you to write a script that allows a customer to calculate the cost of a pizza. He has asked you to make the following options available to the customer:
* **Pizza base (Customer must choose 1): Thick (Kr 10) or Thin (Kr 5).**
```py

```

* **Pizza size (Customer must choose 1): Small (Kr 30), Medium (Kr 40), or Large (Kr 50).**
```py

```

* **Basic sauce (Customer must choose 1): Tomato (Kr 5) or Barbecue (Kr 10).**
```py

```
* **Toppings (Customer may choose any or none): Cheese (Kr 5), Mushrooms (Kr 3), Avocado (Kr 7), Pineapple (Kr 5), Bacon (Kr 7), Chicken (Kr 7) or Fish (Kr 6).**
```py

```
---

### 3.2
#### Performing operations (part 2)
#
#### Notes:
[TEXT]
#### Lesson Task:

---

### 3.3
#### Loops
#
#### Notes:
[TEXT]
#### Lesson Task:

---

### 3.4
#### Functions (part 1)
#
#### Notes:
[TEXT]
#### Lesson Task:


---
## Module 4
[DESCRIPTION]
#
### 4.1
#### Functions (part 2)
#
##### Notes:
[TEXT]
##### Lesson Task:

---

### 4.2
#### Importing modules
#
##### Notes:
[TEXT]
##### Lesson Task:

---
### 4.3
#### Managing files
#
##### Notes:
[TEXT]
##### Lesson Task:

---
### 4.4
#### Programing objects:
#
##### Notes:
[TEXT]
##### Lesson Task:
---



## Module 5
[DESCRIPTION]
#
### 5.1
#### Integrating with operating systems
#
##### Notes:
[TEXT]
##### Lesson Task 1: 

Create a script called monthlyzip.py. Before writing the script, please create a new directory and copy a few text, image or sound files. In the script, do the following:
* **Ask the user for the name of a new directory.**
```py
new_dir = input('Name of new directory: ')
```
*  **Create the directory in the same path as the script.**

```py
pre_path = 'C:\\Users\\johannes.falnes\\PycharmProjects\\NoroffVC\\Module 5\\M5L1\\folder'
new_path = f'C:\\Users\\johannes.falnes\\PycharmProjects\\NoroffVC\\Module 5\\M5L1\\{new_dir}'

```
* **Copy all of the files from your pre-created directory to the new directory.**
```py

```
* **Rename each newly created file by appending the original file's creation date to the file name (before the file extension). This may require dusting off your string manipulation skills.**
```py

```
* **Display the list of newly created files to the user by reading the contents of the new directory.**
```py

```
* **Create a new zip file named according to today's date and add the contents of the entire (new) directory to the zip file.**
```py

```

##### Full code:
```py

import os
import shutil
from datetime import datetime
import zipfile

new_dir = input('Name of new directory: ')

pre_path = 'C:\\Users\\johannes.falnes\\PycharmProjects\\NoroffVC\\Module 5\\M5L1\\folder'
new_path = f'C:\\Users\\johannes.falnes\\PycharmProjects\\NoroffVC\\Module 5\\M5L1\\{new_dir}'

os.mkdir(new_path)

def copy_files(PRE_PATH, PATH):

    time_now = datetime.now()
    time_now = str(time_now)

    for current, subdirectories, files in os.walk(PRE_PATH):
        print("Current directory:",current)
        for current_subdir in subdirectories:
            print("Subdirectory:", current_subdir)
            
        for current_file in files:
            print("File:", current_file)

            split_file = current_file.split('.')
            new_name = f'{split_file[0]}{time_now[:10]}.{split_file[1]}'
            os_path = os.path.join(PRE_PATH, current_file)

            shutil.copy(os_path, f'{PATH}\{new_name}')


def list_dir(PATH):
    for current, subdirectories, files in os.walk(PATH):
        print("Current directory:",current)
    for current_subdir in subdirectories:
        print("Subdirectory:", current_subdir)

    for current_file in files:
        print("File:", current_file)
        
    print()

def zip_dir(PATH):

    with zipfile.ZipFile('noroff.zip', 'w') as zip:
        for current, subdirectories, files in os.walk(PATH):
            print("Current directory:",current)
        for current_subdir in subdirectories:
            print("Subdirectory:", current_subdir)

        for current_file in files:
            print("File:", current_file)
            zip.write(f'{PATH}\{current_file}')

copy_files(pre_path, new_path)
list_dir(new_path)
zip_dir(new_path)
```
#
#

##### Lesson Task 2:
Create a script called timedexecution.py. Before starting the script, create a text file containing a welcome message, such as "Welcome to the system". The script should do the following:
* Schedule a task that will execute every Monday to Friday at 08:00 in the morning. This task should read the contents of the text file and display the text to the command line.**

```py

```
* Schedule a task that will open a web browser every hour and point it to the address https://www.noroff.no**
```py

```

### 5.2
#### Consuming services
#
##### Notes:
[TEXT]
##### Lessong task:


---

### 5.3
#### Hashing with Python
#
##### Notes:
[TEXT]
##### Lesson task 1:
#### Write a Python script that accepts the following command line arguments:
* ###### folder to be scanned and a file name.
First we need to import the necessary libraries for the script. The *'argparse'* library is used to parse command-line arguments, the *'os'* library is used for interacting with the operating system, the 'Image' module from the *'PIL'* library is used for opening and manipulating image files, and the 'imagehash' library is used for generating hashes for images.
```py
import argparse
import os
from PIL import Image
import imagehash

```

We then have to create an *'ArgumentParser'* object which will be used to parse the command-line arguments passed to the script. The *'prog'* parameter specifies the name of the program, which will be used in the help message. The *'description'* parameter provides a brief description of the program's purposem which will also be uncluded in the help message. The *'epilog'* parameter specifies text that will be displayed at the bottom of the help message. 
```py
parser = argparse.ArgumentParser(
                    prog = 'ImageHasher',
                    description = 'Checks images for equal hashes',
                    epilog = 'Text at the bottom of help')
```

Now we need to add the required arguments to the *'ArgumentParser'* object: *'folder'* and *'output'*. The *'folder'* argument specifies the input folder containing the images, and the *'output'* argument specifies the output file to which the matching image hashes will be written.
```py
parser.add_argument('folder')
parser.add_argument('output')
```

 The line below parses the command-line arguments passed to the script and stores them in the *'args'* variable.
```py
args = parser.parse_args()
```

We need to check if the input folder specified in *args.folder* exists and is a directory using *'os.path.isdir()'* the result is stored in the *'isdir'* variable.
```py
isdir = os.path.isdir(args.folder)
```

If the input folder is a directory, this *'if'* statement will execute. The first line initializes an empty list *'hash_list'* which will be used to store the generated image hashes. The secound line gets a list of the files in the directory using *'os.listdir()'* and stores it in the *'dir_list'* variable. The third line prints the list of files and the empty *'hash_list'* to the console. 
```py
if isdir == True:
    hash_list = []
    dir_list = os.listdir(args.folder)
    print(dir_list, hash_list)
```
This *'for'* loop iterates through the list of files in the input directory, specified by *'dir_list'*. For each file, the script generates a hash using *'imagehash.average_hash()'* and opens the file using the *'Image.open()'* function. The generated hash is then covnverted to a string using *'str()'* and appeneded to the *'hash_list'* list.
```py
# list_2 = hash_list
# for x in hash_list:
#     hash_list.remove(x)
```

These lines initialises a new list *'list_2'* and assigns it the value *'hash_list'*. Then, it starts a 'for' loop that iterates through the elements in 'hash_list'. For each element, the element is removed from *'hash_list'* using the *'list.remove()'* method.

This has the effect of emptying the *'hash_list'* list. Unsure what the point of the line above is, as it does not need to do this, but it was included during the lecture. 

Moving on to the next "real" part of the code:
These *'if'* statements check wheher the current element, *'x'*, is in the *'hash_list'* list. If it is not, the element is appended to the list using the *'list.append()'* method and a message is printed to the console indicating that there is a matching hash. If the element is already in the list, a message is printed to the console indicating that there is a matching hash.

It is important to nothe that these *'if'* statements will never be executed, because the *'hash_list'* list is empty 


```py
if x not in hash_list:
    hash_list.append(x)

    print(f'Matching hashes: {x}')
if x in hash_list:
    print(f'Matching hashes:)
```


* ###### The folder to be scanned needs to be an image folder that the user wants to scan. The file name will be the filename and path where the end user wants to save the results.
```py

```
* ###### The image folder will need to be scanned, and the images hashed and compared. If a matching hash is found, it must be saved to the text file. The format to save the results in would be the filename, hash.
```py

```

#
##### Lesson task 2:
#
```py



```

##### Lesson task 3:
#
---

### 5.4
#### Network scanning
#
##### Notes:
[TEXT]
##### Lesson task 1:

Create a script with command line arguments that will scan the provided network. For the command line arguments, you would need a net parameter. 

In your script, you must use this net parameter you received from the command line and scan that network. You need to print your results to the screen for the end user.
###### Answer:
First we need to *'import nmap3'* since this task uses nmap, and we use nmap3 in python3, then we *'import json'*.
We then need to set the *'nmap'* variable to an instance of the *'Nmap'* class from the *'nmap3'* module. before we make a variable named *'net'* that should take the input from user as an IP, then we print the result while also adding a rule for indentation for readability.

```py
import nmap3
import json

nmap = nmap3.NmapScanTechniques()
net = input('IP: ') # 192.268.0.0/24
results = nmap.nmap_ping_scan(net)

print(json.dumps(results, indent = 4))
```
#

##### Lesson task 2:

Create a script that will present the end user with a menu system. The user can select to scan a network or a device for open ports. You are required to use the NMAP Python module.
#
The menu options would be:
1. Scan a network.
2. Scan a device for open ports.
3. Save results to a CSV (Comma separate value) file.
4. Exit.

When the user selects option 1, they need to enter a network subnet to scan, for example, 192.168.0.0/24. If the user doesn’t enter the correct value, they need to be prompted with an error to correct their input. The results need to be displayed on the screen.

When the user selects option 2, they need to specify a host IP address, for example, 192.168.0.1, and provide the ports to scan. This will be gathered with a separate input prompt. If any value entered is incorrect, the user needs to be prompted with an error to correct their input. The result needs to be displayed on the screen.

When the user selects option 3, the last results from option 1 or 2 need to be saved to a CSV file with the relevant information. When the user selects this option, they will need to provide a path to a file where the results need to be saved. Any error in the user input would need to be handled with an exception, and the end user will need to correct the mistake or error.
###### Answer:
Firs we import what we need, we will ofc use *'nmap3'*, we then need to display the data gathered in an easy to read format by importing this badboy: *'import json'*.
we then need to *'import subprocess'* im not sure what this does, but the description looks like this:
**"This module allows you to spawn processes, connect to their input/output/error pipes, and obtain their return codes."**
so it's safe to assume that the program does exactly that.
and then we then need to set the *'nmap'* variable to an instance of the *'Nmap'* class from the *'nmap3'* module.

```py
import nmap3
import json
import subprocess

nmap = nmap3.NmapScanTechniques()
```

Bravo, we have gotten this far! Now let's add the different defenitions, I will not explain every function in detail, but I will explain what the purpose of the functions, the first two is mainly for error handeling:

This function makes sure the IP adress follows the rules that makes up an IP address, (needs to be between 0 - 255 ect.)

```py
def validate_ip(s):
    a = s.split('.')
    if len(a) != 4:
        return False
    for x in a:
        if not x.isdigit():
            return False
        i = int(x)
        if i < 0 or i > 255:
            return False
    return True
```
This makes sure the cird used is correct, example: */24*
```py
def validate_cidr(s):
        if s in range(30):
            return True
        else: 
            return False
```
now what we have done that we can start making up the different features, in this instance we only have two, network scanner and port scanner. Network scanner looks like this:
```py
def net_scan():
    
    net = input('IP: ') # 172.24.1.54
    
    cidr = input('CIDR: ') # /24
    
    if validate_ip(net):
        try:
            if validate_cidr(int(cidr)):

                net = f'{net}/{cidr}'
                results = nmap.nmap_ping_scan(net)

                a = json.dumps(results, indent=4)
                print(a)
                with open('result.json', 'w') as f:
                    f.write(a)
            else:
                print('Invalid CIDR try again!')
        except ValueError as e:
            print(e)
            net_scan()
    else:
        print('Invalid IP address try again!')
```
And the port scanner looks like this: 
```py
def port_scan():
    net = input('IP: ') # 172.24.1.54
    port = input('Port: ')
    
    cmd = f'nmap {net} -p{int(port)}'
    with open('result_port.txt', 'w') as f:
        return_code = subprocess.call(cmd, stdout=f)
        print(return_code)

```
We also need to tie this all together with a menu system, all we basicly have to do is to assign the input 1 & 2 the correct function to call upon when we input the number 1 or 2:
```py
def menu():
    with open(r'Module5\M5L4\menu.txt', 'r') as f:
        for x in f.readlines():
            print(x.strip())

    user_inp = input('>> ')
    if user_inp == '1':
        net_scan()
    elif user_inp == '2':
        port_scan()
    else:
        exit()

menu()
```
#
**Full code**
```py
import nmap3
import json
import subprocess

nmap = nmap3.NmapScanTechniques()

def validate_ip(s):
    a = s.split('.')
    if len(a) != 4:
        return False
    for x in a:
        if not x.isdigit():
            return False
        i = int(x)
        if i < 0 or i > 255:
            return False
    return True


def validate_cidr(s):
        if s in range(30):
            return True
        else: 
            return False


def net_scan():
    
    net = input('IP: ') # 172.24.1.54
    
    cidr = input('CIDR: ') # /24
    
    if validate_ip(net):
        try:
            if validate_cidr(int(cidr)):

                net = f'{net}/{cidr}'
                results = nmap.nmap_ping_scan(net)

                a = json.dumps(results, indent=4)
                print(a)
                with open('result.json', 'w') as f:
                    f.write(a)
            else:
                print('Invalid CIDR try again!')
        except ValueError as e:
            print(e)
            net_scan()
    else:
        print('Invalid IP address try again!')



def port_scan():
    net = input('IP: ') # 172.24.1.54
    port = input('Port: ')
    
    cmd = f'nmap {net} -p{int(port)}'
    with open('result_port.txt', 'w') as f:
        return_code = subprocess.call(cmd, stdout=f)
        print(return_code)


def menu():
    with open(r'Module5\M5L4\menu.txt', 'r') as f:
        for x in f.readlines():
            print(x.strip())

    user_inp = input('>> ')
    if user_inp == '1':
        net_scan()
    elif user_inp == '2':
        port_scan()
    else:
        exit()

menu()
```

