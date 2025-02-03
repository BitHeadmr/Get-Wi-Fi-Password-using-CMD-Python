1.Using CMD
Here’s how to find the WiFi password using the command prompt:

Open the command prompt by opening Run (Windows + R) and typing CMD. Hit Enter.

Note: Alternatively, you can use Search and type CMD. Right-click on Command Prompt and select Run As Administrator.

Type the following command line and hit Enter:


NETSH WLAN SHOW PROFILE


You will see a list of WLAN profiles stored on the PC. Take note of the network name you’d like to explore.

Type the following command and replace “WIFI” with the network name.


NETSH WLAN SHOW PROFILE WIFI KEY=CLEAR


Completing these steps successfully will bring up the WLAN profile of the network you want to connect to. Scroll down and you’ll find the password under the Key Content field. 

3. Using Python
First import subprocess, this is the module we will use to interact with the cmd. 

Next, get the output for the command "netsh wlan show profiles" using subprocess.check_output(). Then decode the output with utf-8 and split the string by a newline character to get each line in a separate string 

Now that we have a list of strings, we can get lines that only contain "All User Profile". With these lines we then need to split it by a ':', get the right hand side and remove the first and last character 

Now that the variable a contains the WiFi profile names, we can get the output for the command "netsh wlan show profile {Profile Name} key=clear" using subprocess.check_output() again for a particular profile while looping through all profiles. 

Still in the loop, find lines that contain "Key Content", split by ':' and remove the first and last character just like before 

Now we should have a list containing one string which is the particular profiles key. Here you could just use a simple print statement but I have just formatted it a bit. 

Now put an input call at the end of the script outside the loop so that when the script is run it will not immediately stop when results are displayed. 

Save this file with a .py extension and you can now run the script. You can run it by double-clicking on the script, running it in IDLE or even cmd using python {filename} 
