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
'Display a dialogue box message
xx = MsgBox("pop up message",4,"123 title")
```
![msgbox](../../images/develop/vbscript/msgbox.png)  

### Date Function
***

```vb
'The current system date
xx = MsgBox(Date(),4,"Date Function")
```
![date](../../images/develop/vbscript/date.png)   

```vb
'Return the current Date and Time  
xx = MsgBox(Now,4,"Now Function")
```
![now](../../images/develop/vbscript/now.png)  
```vb
'The current system time
xx = MsgBox(Time,4,"Time Function")
```
![time](../../images/develop/vbscript/time.png) 

### String Function
***
```vb
'Find one string within another
a = "123 456 abc"
xx = MsgBox(InStr(a,"a") ,4,"Instr Function")
```
![instr](../../images/develop/vbscript/instr.png)  
```vb
'Return a mid-section from a string
a = "123 456 abc"
xx = MsgBox(Mid(a,5,3) ,4,"Mid Function")
```
![mid](../../images/develop/vbscript/mid.png) 
```vb
'Return the leftmost len characters of string
a = "123 456 abc"
xx = MsgBox(Left(a,3) ,4,"Left Function")
```
![left](../../images/develop/vbscript/left.png)
```vb
'Return the rightmost len characters of string
a = "123 456 abc"
xx = MsgBox(Right(a,3) ,4,"Right Function")
```
![right](../../images/develop/vbscript/right.png)
```vb
'Find and replace text
a = "123 456 abc"
xx = MsgBox(Replace(a, "abc","edf") ,4,"Replace Function")
```
![replace](../../images/develop/vbscript/replace.png)



Reference:  
https://www.informit.com/articles/article.aspx?p=1187429&seqNum=5
'https://docs.microsoft.com/en-us/previous-versions//d1wf56tt(v=vs.85)
'https://ss64.com/vb/network.html
'https://docs.microsoft.com/en-us/previous-versions/ms807642%28v%3dmsdn.10%29