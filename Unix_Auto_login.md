Procedure :
1. Save your username in putty  configuration   under  "connection" --> "data" --> "Auto-login Username "
2. Please save the below script as .vbs and run it. Change the putty.exe file location & passwords according to your environment . 


one way authentication
-----------------------------
```
box = InputBox("HI")
strIPHost = box
If strIPHost ="" Then
  Wscript.Quit
Else
  Set WShell = CreateObject("WScript.Shell")
  command ="C:\Users\Public\putty.exe  "& strIPHost &" -l username -pw P@SSW0RD"
  WShell.exec command
End If
```

two way authentication
-----------------------------
```
Dim UserName
Dim Passwrd


ServerName = InputBox("Please Enter Your Servername:")
Passwrd  = InputBox("Please Enter Your Password:")



Set shell = WScript.CreateObject("WScript.Shell")
'pcmd = "C:\Users\Public\putty.exe -ssh"&" "&UserName & "@ABCDSERVER12345 -pw" &" "&Passwrd
'pcmd = "C:\Users\Public\putty.exe "&Servername & " -pw" &" "&Passwrd
pcmd = "C:\Users\Public\putty.exe ABCDSERVER12345 -pw P@SSW0RD"&Passwrd


Set exec = shell.Exec(pcmd)
Set pout = exec.StdOut
```

Double Password Authentication
=========================
```
Dim UserName
Dim Passwrd
ServerName = InputBox("Please Enter Your Servername:")
Passwrd  = InputBox("Please Enter Your RSA TOKEN:")
If ServerName ="" Then
  Wscript.Quit
Else
 Set shell = WScript.CreateObject("WScript.Shell")
 pcmd = "C:\Program Files (x86)\Putty\putty.exe "&Servername & " -pw firstpwd"&Passwrd
Set exec = shell.Exec(pcmd)
Set pout = exec.StdOut
End If
```

Multiple Server Login at one shot
=========================
  Save the Below script as  .bat file  & create another file called host.txt and add all your servernames that you want to login 

Example :   multi-server-login.bat
```
(for /f %%i in (host.txt) do (
start "" "C:\Program Files\Putty\putty.exe" %%i -l username -pw pwd
))
```
