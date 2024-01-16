# Pyhton-IP-Management
<h3>Intro</h3>
<p>The following is a breakdown of my Python automation capstone project following Google's "Automate Cybersecurity Tasks with Python" course.</p>

<p>The project is somewhat guided but the code is my own and resembles what students learn during the course.</p>

<p>You can find a word doc of the report by clicking "PythonProjectReport.docx" and clicking "raw" to download the file and, the raw code for the project can be found above.</p>

<h3>Project Description</h3>
<p> Playing the role of a security professional working at a health care company, my job task is to update a file that identifies the employees who can access restricted content. The file “allow_list.txt” contains information on who is able to work with personal patient records. Access to a separate network subnet that contains the restricted patient data is controlled via IP address. The allow list that permits access to the restricted subnetwork contains IP addresses for the users and is stored in the “allow_list.txt” file. There is also a remove list that identifies which employees must be removed from the allow list.
<p> My task, now, is to create an algorithm that uses Python code to check whether the allow list contains any IP addresses identified on the remove list. If any IP addresses in the restricted list are present in the allowed list, the file contents need to be updated by removing restricted user IPs from the allow list. </p>
<h3>Open File Containing Allow List</h3>
<p> To begin the project, I opened the “allow_list.txt” file by assigning the filename as a string to the “importFile” variable. I also manually defined the IP addresses to be removed as a list stored in the “removeList” variable. Note: The program assumes that the allow list is present in the same directory as the running Python program. Otherwise, the directory of the file must be included.</p>

<p align="center"> <img src="https://i.imgur.com/nbWSSow.png"> </p>

I then used a with statement to open the file.

<p align="center"> <img src="https://i.imgur.com/SzgkCxO.png"> </p>

My algorithm uses with and the .open( ) function in read mode to open the allow list file for the purpose of reading it. The purpose of opening the file is to allow me to access the IP addresses stored in the allow list file. Using with allows efficient resource management by closing the file after exiting the statement. The code within the with open(importFile, “r”) as file statement has two parameters, “importFile”, which indicates the file being imported, and “r” which indicates I want to read the file. I also use an as statement to store the output into a file variable.

<h3>Read File Contents</h3>
<p>To read the file contents I used the .read( ) method, converting the contents into a string.</p>
<p align="center"> <img src="https://i.imgur.com/hDSfu1d.png"> </p>
<p>The .read( ) function converts the file contents into a string, which is stored in the allowList variable. The resulting issue is I would like to automatically process the IP address in a for loop. While regex can accomplish finding IP addresses in the string, converting the contents of allowList into a list is more practical.</p>

<h3>Convert String to List</h3>
<p>To accomplish this, I use the .split( ) method.</p>
<p align="center"> <img src="https://i.imgur.com/7RcV8oB.png"> </p>
<p> The .split( ) method is used by appending  it to the end of a string and automatically converts a string to a list, making it easier to remove IP addresses from the allow list. The .split( ) method will automatically divide the IP addresses that are separated by spaces and, in this algorithm, will store them in the allowList variable.</p>

<h3>Iterate Through Remove List</h3>
<p>To iterate through the remove list, I implemented a for loop.</p>
<p align="center"> <img src="https://i.imgur.com/Z08nlFZ.png"> </p>
<p>The for loop takes IP addresses contained in the removeList and defines them in the ip variable. The loop will run until it has checked every IP address in the removeList. I now need to automate decision making by implemented the use of an if statement.</p>
<h3>Removing the IP Addresses</h3>
<p>The integration of the if statement automatically processes data and performs decision making. </p>
<p align="center"> <img src="https://i.imgur.com/dwBIClx.png"> </p>

<p>In this case, the algorithm compares every IP in removeList and, if it is present, the program will remove the  IP from the list stored in the allowList variable.</p>

<h3>Update Original Allowed IPs</h3>
<p>The last step is to update the original allowList file.</p>

<p align="center"> <img src="https://i.imgur.com/cLRH3HM.png"> </p>

<p>The “\n”.join(allowList) code ensures all the IPs are converted back into a string, separating each IP on a new line. The final step is to write the file however, since the with and open( ) methods close files after they are used, I need to reuse the methods with a few changes.</p>

<p align="center"> <img src="https://i.imgur.com/Gf04n4r.png"> </p>

<p>I again run a with statement and open( ) function. Instead of using “r” as a parameter and the .read( ) method like before, I use “w” and .write( ) to write to the file.</p>

<h3>Results</h3>
<p>The following images illustrate the text file before and after running the code.</p>
<p align="center"> <img src="https://i.imgur.com/wKOnxDN.png"><br><i>Figure 1: Before</i> </p>

<p align="center"> <img src="https://i.imgur.com/7aNuk7K.png"><br><i>Figure 2: After</i> </p>

<h3>Summary</h3>
The algorithm I created removes IP addresses found in a remove_list variable from the “allow_list.txt” file. The algorithm functions by opening the file, turning the IP addresses into a list, and subsequently utilizes a for loop and if statement to iterate the list, checking to see if there are IPs present in the remove list in the allow list. If any remove list IPs are discovered to be in the allow list, they will be removed before the file is updated using the .join( ) method to convert the data back into a string. To finalize the update, I used the .write( ) method.</p>

<p>Some alternatives to the code would be to implement the use of input( ) functions. By doing this automated manual input of IP addresses can be achieved. Alternatively, my code includes commented lines of importing another text file of addresses to be removed. If used, the manually input list must be commented out.</p>

<p align="center"> <img src="https://i.imgur.com/au3cG2i.png"> </p>
