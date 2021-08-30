### MsgBox Function
***
```
Syntax 
      MsgBox(prompt [, buttons][, title]
         [, helpfile, context])

Key
   prompt    The dialogue box text.
   buttons   The sum of the constants for button, icon, default button and modality
   title     Title bar text
   helpfile  A helpfile to link to the help button
   context   Helpfile context number

Constants
  Buttons: vbOKOnly (0), vbOKCancel(1), vbAbortRetryIgnore (2), vbYesNoCancel(3)
           vbYesNo (4), vbRetryCancel (5)
  Icon: vbCritical (16),vbQuestion (32),vbExclamation (48), vbInformation (64) 
  Default button: vbDefaultButton1 (0),vbDefaultButton2 (256),vbDefaultButton3 (512),vbDefaultButton4(768)
  Modality: vbApplicationModal, vbSystemModal
The MsgBox function will return one of the following:

1 = OK was clicked (vbOK)
2 = Cancel was clicked (vbCancel )
3 = Abort was clicked (vbAbort)
4 = Retry was clicked (vbRetry)
5 = Ignore was clicked (vbIgnore)
6 = Yes was clicked (vbYes)
7 = No was clicked (vbNo)
```

```vb
'Msgbox : Display a dialogue box message
xx = MsgBox("pop up message",4,"123 title")
```
![msgbox](../../images/develop/vbscript/msgbox.png)  

### Date Function
***

```vb
'Date : The current system date
xx = MsgBox(Date(),4,"Date Function")
```
![date](../../images/develop/vbscript/date.png)   

```vb
'Now : Return the current Date and Time  
xx = MsgBox(Now,4,"Now Function")
```
![now](../../images/develop/vbscript/now.png)  
```vb
'Time : The current system time
xx = MsgBox(Time,4,"Time Function")
```
![time](../../images/develop/vbscript/time.png) 

### String Function
***
```vb
'Instr : Find one string within another
a = "123 456 abc"
xx = MsgBox(InStr(a,"a") ,4,"Instr Function")
```
![instr](../../images/develop/vbscript/instr.png)  
```vb
'Mid : Return a mid-section from a string
a = "123 456 abc"
xx = MsgBox(Mid(a,5,3) ,4,"Mid Function")
```
![mid](../../images/develop/vbscript/mid.png) 
```vb
'Left : Return the leftmost len characters of string
a = "123 456 abc"
xx = MsgBox(Left(a,3) ,4,"Left Function")
```
![left](../../images/develop/vbscript/left.png)
```vb
'Right : Return the rightmost len characters of string
a = "123 456 abc"
xx = MsgBox(Right(a,3) ,4,"Right Function")
```
![right](../../images/develop/vbscript/right.png)
```vb
'Replace : Find and replace text
a = "123 456 abc"
xx = MsgBox(Replace(a, "abc","edf") ,4,"Replace Function")
```
![replace](../../images/develop/vbscript/replace.png)


### Conditional Function
***
```vb
'If...ElseIf...Else...End If : Conditionally execute a block of statements.
a = 12
strtext = "a：" & a & " "
If a<0 Then  
  strtext = strtext & "< 0" 
ElseIf  a=0 Then
  strtext = strtext  & "= 0" 
Else 
  strtext = strtext &  ">0" 
End if
x=MsgBox(strtext)
``` 
![if_else](../../images/develop/vbscript/if_else.png)

```vb
'Select...Case... : Conditionally execute a block of statements
a = 1
strtext = "" 
d=weekday(date)
Select Case d
Case 1
strtext = strtext & ("Sunday")
Case 2
strtext = strtext &("Monday")
Case 3
strtext = strtext &("Tuesday")
Case 4
strtext = strtext &("Wednesday")
Case 5
strtext = strtext &("Thursday")
Case 6
strtext = strtext &("Friday")
Case else
strtext = strtext &("Saturday")
End Select
x=MsgBox("Today is？"&chr(10)& strtext )
```
![switch_case](../../images/develop/vbscript/switch_case.png)

### Loop Function
***
```vb
'For...Next... : Repeat a block of statements a given number of times
'Step : to skip number every loop
'Exit For : to end loop
strtext = "" 
For i = 1 To 5 Step 2
if i = 4 Then Exit For
strtext = strtext &chr(10)& i
Next
x=MsgBox("count one to five："&strtext ,0,"For Next Function")
```
![for_next](../../images/develop/vbscript/for_next.png)

```vb
'For...Each... : Loop through the items in a collection or array
strtext = "" 
Dim country(2)
country(0)="china"
country(1)="japan"
country(2)="south korea"
For Each c In country
  strtext = strtext & c & ","
Next
x=MsgBox("list all countries："&strtext ,0,"For Each Function")
```
![for_each](../../images/develop/vbscript/for_each.png)

```vb
'Do While...Loop..., Do...Loop Until... : Repeat a block of statements
a = 5
strtext = "" 
Do While a>0
a = a -1
strtext = strtext & a &","
Loop
x=MsgBox("a minus 1 every loop："&strtext ,0,"Do Loop Function")

'codes equal

a = 5
strtext = "" 
Do 
a = a -1
strtext = strtext & a &","
Loop Until a<1
x=MsgBox("a minus 1 every loop："&strtext ,0,"Do Loop Function")

```
![do_loop](../../images/develop/vbscript/do_loop.png)

### Object Function
***
```vb
'GetObject : a wscript method, Get an Automation object
Set fileObject = GetObject("D:\1.xlsx")
Set cell = fileObject.Sheets(1).Cells(1,1)
x=MsgBox(cell,4,"Read Excel Cell")
```
![getobject](../../images/develop/vbscript/getobject.png)

```vb
'CreateObject : an automation object / run an external command
'write text file D:\1.txt with content "123abc" 
Set objFileToWrite = CreateObject("Scripting.FileSystemObject").OpenTextFile("D:\1.txt",2,true)
objFileToWrite.WriteLine("123abc")
objFileToWrite.Close
Set objFileToWrite = Nothing
```

```vb
'UBound : Return the largest subscript for an array dimension
a = Array("abele","iefjofe","jlkkl")
x = MsgBox("a largest dimension:"& UBound(a),4,"Ubound Function")
```
![ubound](../../images/develop/vbscript/ubound.png)

### File Object
***
```
FileSystemObject Methods:

.BuildPath(strPath, strFileName)
.CopyFile(Source, Dest [,Overwrite (True/False)]
.CopyFolder(Source, Dest [,Overwrite (True/False)]
.CreateFolder(Path)
.CreateTextFile(FileName [,Overwrite (True/False) [, Unicode (True/False)]])
.DeleteFile(FileSpec, Force (True/False))
.DeleteFolder(FileSpec, Force (True/False))
.DriveExists(strDrive) (True/False)
.FileExists(strFile) (True/False)
.FolderExists(strFolder) (True/False)
.GetAbsolutePathName(strPath) - Returns a string with the full drive, path, and file names: Drive:\Path\To\File.Ext
.GetBaseName(strPath) - Returns a string with the file name, without the extension: File
.GetDrive(strDrive) - Returns an object referring to a drive
.GetDriveName(strDrive) - Returns a string referring to a drive. Drive:
.GetExtensionName(strPath) - Returns a string referring to the extension of the file. Ext
.GetFile(strPath) - Returns an object referring to a file.
.GetFileName(strPath) - Returns a string referring to a file. File.Ext
.GetFolder(strPath) - Returns an object referring to the path.
.GetParentFolderName(strPath) - Returns a string referring to the path. \Path\To\
.GetSpecialFolderName(FolderType) FolderType=SystemFolder/TemporaryFolder/WindowsFolder
.GetStandardStream(Type [,Unicode (True/False)])
.GetTempName()
.MoveFile(Source, Dest)
.MoveFolder(Source, Dest)
.OpenTextFile(strFile [,IOMode (8=append, 1=Read, 2=Write) [,Create (True/False) [,Format (0=Ascii, -1=Unicode, -2=default)]]])

Drive Properties:
AvailableSpace, DriveLetter, DriveType, FileSystem, FreeSpace,IsReady, 
Path, RootFolder, SerialNumber, ShareName, TotalSize, VolumeName
DrivesCollection properties: Count, Item

File Properties:
Attributes, DateCreated, DateLastAccessed, DateLastModified,Drive,
Name, ParentFolder, Path, ShortName, ShortPath, Size, Type
File Methods: .copy, .Delete, .Move, .OpenAsTextStream

Folder Properties:
Attributes, DateCreated, DateLastAccessed, DateLastModified,Drive,
Files, IsRootFolder, Name, ParentFolder, Path,
ShortName, ShortPath, Size, SubFolders, Type
Folder Methods: .copy, .CreateTextFile, .Delete, .Move

FoldersCollection properties: Count, Item
FoldersCollection Methods: Add
```
  
```vb
'FileSystemObject : Work with Drives, Folders and Files
'create a folder and a file
Set fs = CreateObject("Scripting.FileSystemObject")
fs.CreateFolder("D:\test folder")
fs.CreateTextFile("D:\test folder\1.txt")

'copy folder and file
fs.CopyFolder "D:\test folder", "D:\test folder copy"
fs.CopyFile "D:\test folder\1.txt", "D:\test folder copy\2.txt"

'move folder and file
fs.MoveFolder "D:\test folder", "D:\test folder move"
fs.MoveFile "D:\test folder\1.txt", "D:\test folder move\1.txt"

'delete folder and file
fs.DeleteFolder "D:\test folder"
fs.DeleteFIle "D:\text folder\1.txt"

'get file name
fs.GetFileName("D:\text folder\1.txt")
fs.GetFile("D:\text folder\1.txt").Name

'show file create time
fs.GetFile("D:\text folder\1.txt").DateCreated

'show drive spaces
fs.Drives("C").AvailableSpace/1024/1024/1024

'whether file, folder, drive exist
fs.FileExists("D:\text folder\1.txt")
fs.FolderExists("D:\text folder\")
fs.DriveExists("D:\")

'loop read files in folder
Function ListFiles(filespec)
   Dim fso, msg
   Set fso = CreateObject("Scripting.FileSystemObject")
   Set fd = fso.GetFolder(filespec)
   For Each ofd in fd.SubFolders:
         ListFiles(ofd.Path)
   Next
   For Each ofs in fd.Files:
          Set f = fso.OpenTextFile(ofs.Path, 1, True)
          MsgBox(ofs.Path & " content: " & (f.ReadAll))
   Next
End Function
ListFiles("D:\text folder")


'OpenTextFile : 1-read,2-overwrite,8-appendwrite
Set fs = CreateObject("Scripting.FileSystemObject")
'append text in file
Set f = fs.OpenTextFile("D:\test folder\1.txt", 8 , False)
f.Write("HELLO WORLD")
'read all text content
MsgBox(f.ReadAll)
'read one line text
MsgBox(f.ReadLine)
f.Close
Set fs = Nothing
```

### Regular Expression Function
***
```vb
'RegExp : Regular expression search object.
'test mail url valid or invalid
Sub ReFunc(text)
Set re  = New RegExp
re.Pattern = "^[\w-\.]{1,}\@([\da-zA-Z-]{1,}\.){1,}[\da-zA-Z-]{2,3}$"
re.IgnoreCase = False
re.Global = False
If re.Test(text) Then
   MsgBox(text & " valid mail")
Else
   MsgBox(text & " invalid mail")
End If
Set re = Nothing
End Sub

text = "@123.com"
ReFunc text
text = "12@123.com"
ReFunc text
```

### Class Definition
***
```vb
Class User
    'create user properties
	private user_name
	private user_age
	
	Private Sub Class_Initialize  
		'MsgBox("user class initialize")
	End Sub
	Private Sub Class_Terminate  
		'MsgBox("user class terminate")
	End Sub
	
    'create get and set property functions
	Public Property Get UserName
		UserName = user_name
	End Property
	Public Property Get UserAge
	    UserAge = user_age
	End Property
	Public Property Let UserName(new_name)
		user_name = new_name
	End Property 
	Public Property Let UserAge(new_age)
		user_age = new_age
	End Property

    'create custom function
	Public Sub ToString()
		MsgBox "name："+UserName+" , age："+UserAge
	End Sub
	
End Class

'call user
Dim myuser
set myuser = New User
myuser.UserName = "Neo"
myuser.UserAge ="23"
myuser.ToString
```

### WshScript Shell
***
```vb
'WScript Object run notepad.exe and type keyboard with text "1abd"
Set objWshShell = CreateObject("WScript.Shell")
objWshShell.Run "Notepad"
WScript.Sleep 5000
objWshShell.sendKeys "1abd"

'.Run : Run an external Command
objWshShell.Run "iexplore.exe"

'.Sendkeys : end one or more keystrokes to the active window as if they were typed at the keyboard
objWshShell.sendKeys "%d"

'.RegWrite : Write a value to the Registry
objWshShell.RegWrite "HKLM\SOFTWARE\ivan\", 1, "REG_BINARY"
objWshShell.RegWrite "HKLM\SOFTWARE\ivan\test", "Goocher!", "REG_SZ")

'.RegRead : Read a value from the Registry
WScript.Echo objWshShell.RegRead("HKLM\SOFTWARE\ivan\")
WScript.Echo objWshShell.RegRead("HKLM\SOFTWARE\ivan\test")

'.RegDelete : Delete a value from the Registry
objWshShell.RegDelete("HKLM\SOFTWARE\ivan\")
objWshShell.RegDelete("HKLM\SOFTWARE\ivan\test")


'.Popup : Display text in a pop-up message box
objWshShell.Popup "2 second to close", 2, "popup title"

Set objWshShell = Nothing

'run cmd command example
Sub runBatch(command)
	Const WshFinished = 1
	Const WshFailed = 2
	strCommand = "cmd /C " & command
	'MsgBox strCommand
	Set WshShell = CreateObject("WScript.Shell")
	Set WshShellExec = WshShell.Exec(strCommand)
	dim strOutput
	strOutput = ""
	WScript.Sleep 500
	Select Case WshShellExec.Status
		Case WshFinished
			strOutput = strOutput & WshShellExec.StdOut.ReadAll
		Case WshFailed
			strOutput = strOutput & WshShellExec.StdErr.ReadAll
	End Select
	'WScript.StdOut.Write strOutput 'write results to the command line
	'WScript.Echo strOutput 'write results to default output
	MsgBox strOutput 'write results in a message box	
End Sub
runBatch "dir"

```
registry abbr. see [windows](../system/windows.md)


### WshScript Network
***
```vb
'.Network : Provides access to the shared resources on the network to which your computer is connected
Set WshNetwork = WScript.CreateObject("WScript.Network")
WScript.Echo "Domain = " & WshNetwork.UserDomain
WScript.Echo "Computer Name = " & WshNetwork.ComputerName
WScript.Echo "User Name = " & WshNetwork.UserName


'.EnumPrinterConnections : Enumerate printer connections
Set oPrinters = WshNetwork.EnumPrinterConnections
For i = 0 to oPrinters.Count - 1 Step 2
    WScript.Echo "Port " & oPrinters.Item(i) & " = " & oPrinters.Item(i + 1)
Next
```

### Windows Processes
***
```vb
'find ie process id and kill it
strComputer = "."
notepadPid = "0"
Set wbemServices = Getobject("winmgmts://" & strComputer)
Set wbemObjectSet = wbemServices.InstancesOf("Win32_Process")
For Each wbemObject In wbemObjectSet
'WScript.Echo "Name:   " & wbemObject.Name & vbCrLf & _
'	" Handle:  " & wbemObject.Handle & vbCrLf & _
'	" Process ID: " & wbemObject.ProcessID
                If wbemObject.Name = "iexplore.exe" Then
	'MsgBox("ie pid:" & wbemObject.ProcessID)
	wbemObject.Terminate()
                End If
Next
Set wbemServices = Nothing
Set wbemObjectSet = Nothing
```

### Visual Basic Dictionary
***
```vb
'add keys and values, loop the dictionary
Dim a, d, i, s
Set d = CreateObject("Scripting.Dictionary")
d.Add "a", "Athens"
d.Add "b", "Belgrade"
d.Add "c", "Cairo"
a = d.Items
For i = 0 To d.Count - 1
  s = s & a(i) & " "
Next
MsgBox s
```

### Visual Basic ADO
***
```vb
'connect to mysql and query myclass table
Set objConnection = CreateObject("ADODB.CONNECTION")
Set objCMD = CreateObject("ADODB.COMMAND")
sql = "select * from myclass"
constr = "Driver={MySQL ODBC 5.1 Driver};Server=localhost;" & _
 "Database=mytest;User=root;" & "Password=root;"
objConnection.open constr
If(objConnection.State=1) Then
   MsgBox("database connected")
End If
objCMD.ActiveConnection = objConnection
objCMD.CommandText = sql
set rs = objCMD.Execute
While rs.EOF <> True AND rs.BOF <> True
    wscript.echo rs(0) & " " & rs(1) & " " & rs(2)
    rs.movenext
WEnd
objConnection.close
```


### WshScript shell sendkeys
***
  
Key/Character | SendKey | Description
---|---|---
~	| {~} |	Send a tilde (~)
!	| {!} |	Send an exclamation point (!)
^	| {^} |	Send a caret (^)
+	| {+} |	Send a plus sign (+)
Backspace	| {BACKSPACE} or {BKSP} or {BS}	| Send a Backspace keystroke
Break	| {BREAK}	| Send a Break keystroke
Caps Lock	| {CAPSLOCK}	| Press the Caps Lock Key (toggle on or off)
Clear	| {CLEAR}	| Clear the field
Delete	| {DELETE} or {DEL}	| Send a Delete keystroke
Insert	| {INSERT} or {INS}	| Send an Insert keystroke
Cursor control arrows	| {LEFT} / {RIGHT} / {UP} / {DOWN}	|Send a Left/Right/Up/Down Arrow
End	| {END}	| Send an End keystroke
Enter	| {ENTER} or ~  | Send an Enter keystroke
Escape	| {ESCAPE} | Send an Esc keystroke
F1 through F16	| {F1} through {F16}	|Send a Function keystroke
Help	| {HELP} | Send a Help keystroke
Home	| {HOME} | Send a Home keystroke
Numlock	| {NUMLOCK} | Send a Num Lock keystroke
Page Down Page Up | {PGDN} {PGUP} | Send a Page Down or Page Up keystroke
Print Screen | {PRTSC} | Send a Print Screen keystroke
Scroll lock	| {SCROLLLOCK} | Press the Scroll lock Key (toggle on or off)
TAB	| {TAB} | Send a TAB keystroke
  
To specify keys combined with any combination of SHIFT,
CTRL, and ALT keys, precede the key code with one or more 
of the following:  
For SHIFT prefix with +  
For CTRL  prefix with ^  
For ALT   prefix with %  


### Visual Basic miscellaneous constants
***
  
Constant | Equivalent | Description
---|---|---
vbCrLf | Chr(13) + Chr(10) | Carriage return-linefeed combination
vbCr | Chr(13) | Carriage return character
vbLf | Chr(10) | Linefeed character
vbNewLine | Chr(13) + Chr(10) or, on the Macintosh, Chr(13) | Platform-specific new line character; whichever is appropriate for current platform
vbNullChar | Chr(0) | Character having value 0
vbNullString | String having value 0 | Not the same as a zero-length string (""); used for calling external procedures
vbObjectError | -2147221504 | User-defined error numbers should be greater than this value. For example: Err.Raise Number = vbObjectError + 1000
vbTab | Chr(9) | Tab character
vbBack | Chr(8) | Backspace character
vbFormFeed | Chr(12) | Not useful in Microsoft Windows or on the Macintosh
vbVerticalTab | Chr(11) | Not useful in Microsoft Windows or on the Macintosh


Reference:  
[WshShell Object](https://www.informit.com/articles/article.aspx?p=1187429&seqNum=5)  
[Windows VBScript Commands](https://ss64.com/vb/network.html)    
[Microsoft VBScript Language Reference](https://docs.microsoft.com/en-us/previous-versions//d1wf56tt(v=vs.85))    
[Microsoft VBScript ADO Guide](https://docs.microsoft.com/en-us/previous-versions/ms807642%28v%3dmsdn.10%29)
