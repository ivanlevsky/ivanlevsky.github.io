### MsgBox Function
***
Display a dialogue box message
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

```
xx=MsgBox("pop up message",4,"123 title")
```
![msgbox](../../images/develop/vbscript/msgbox.png)  

### Date Function
***
The current system date
```
xx=MsgBox(Date(),4,"Date Function")
```
![msgbox](../../images/develop/vbscript/date.png) 

Reference:  
https://www.informit.com/articles/article.aspx?p=1187429&seqNum=5
'https://docs.microsoft.com/en-us/previous-versions//d1wf56tt(v=vs.85)
'https://ss64.com/vb/network.html
'https://docs.microsoft.com/en-us/previous-versions/ms807642%28v%3dmsdn.10%29