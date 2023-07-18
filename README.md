<h1>Resolve issues reported by SCA tools</h1>


<h2>Description</h2>
In this lab, participants will learn how to effectively resolve issues reported by Software Composition Analysis (SCA) tools.
<br />


<h2>Languages and Utilities Used</h2>

- <b>Safety</b>
- <b>JSON</b>

<h2>Environments Used </h2>

- <b>Windows 11</b>
- <b>Linux</b> 

<h2>Program walk-through:</h2>

First, we need to download the source code of the project from our git repository: <br/>
- git clone https://gitlab.practical-devsecops.training/pdso/django.nv webapp<br/>
 
<p align="center">
<img src="https://i.imgur.com/bNs1t00.png" height="80%" width="80%" alt="Disk Sanitization Step"/>
</p>

<br />
<br />

Lets cd into the application code, so we can scan the app: <br/>
- cd webapp<br/>
 
<p align="center">
<img src="https://i.imgur.com/31y2TU2.png" height="80%" width="80%" alt="Disk Sanitization Step"/>
</p>

<br />
<br />

Let’s install the safety tool on the system to scan the python dependencies: <br/>
- pip3 install safety==2.3.5<br/>
 
<p align="center">
<img src="https://i.imgur.com/0zZCyYs.png" height="80%" width="80%" alt="Disk Sanitization Step"/>
</p>

<br />
<br />

Lets explore what options safety provides us: <br/>
- safety check --help<br/>
 
<p align="center">
<img src="https://i.imgur.com/XRxRU3S.png" height="80%" width="80%" alt="Disk Sanitization Step"/>
</p>

<br />
<br />

We are using the tee command to show the output and store it in a file simultaneously: <br/>
- safety check -r requirements.txt --json | tee safety-output.json<br/>
 
<p align="center">
<img src="https://i.imgur.com/p67RuJr.png" height="80%" width="80%" alt="Disk Sanitization Step"/>
</p>

<br />
<br />

To fix these issues, we would need to see what components are installed in the system by having a look at requirements.txt file: <br/>
```
- cat requirements.txt<br/>
``` 
<p align="center">
<img src="https://i.imgur.com/mErtNMv.png" height="80%" width="80%" alt="Disk Sanitization Step"/>
</p>

<br />
<br />

Edit the requirements.txt file to use version 3.2: <br/>
```
- cat >requirements.txt<<EOF
  Django==3.2
  EOF
```  
  <br/>
 
<p align="center">
<img src="https://i.imgur.com/nUXrPCV.png" height="80%" width="80%" alt="Disk Sanitization Step"/>
</p>

<br />
<br />

Let’s run the scanner once again: <br/>
```
- safety check -r requirements.txt --json | tee safety-output.json
```
<br/>
<p align="center">
<img src="https://i.imgur.com/qGW5EZK.png" height="80%" width="80%" alt="Disk Sanitization Step"/>
</p>

<br />
<br />

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
