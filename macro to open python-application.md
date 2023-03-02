```
Sub prog_ex()
' Call Shell("python C:\Users\sugivsun\Desktop\st.py")
 Call Shell("C:\Program Files (x86)\Google\Chrome\Application\chrome.exe" & _ 
          " -url" & " " & "www.stackoverflow.com", vbMaximizedFocus)
' open some application 
' Call Shell("C:\Temp\TestApplication.exe",vbNormalFocus)
End Sub
```
