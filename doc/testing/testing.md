### manuscript doc

```shell script
# vbscript read excel
Dim currentWorkSheet

columnIndex = "A"
excelPath = "C:\Users\ivanovsky\Desktop\abc.xlsx"

Set objExcel = CreateObject("Excel.Application")
Set objExcelBook = objExcel.WorkBooks.Open(excelPath)

objExcel.DisplayAlerts = 0

Set excelDict = CreateObject("Scripting.Dictionary")
excelDict.Add "zzz",0

dim columnCount
For i = 1 to objExcel.Worksheets.Count
   Set sheet = objExcelBook.Worksheets(i)
	columnCount =  sheet.cells(sheet.Rows.Count, columnIndex).End(-4162).Row
	For j = 1 to columnCount	
		dim ak , av
		ak = "" & sheet.cells(j, columnIndex) & ""

		If Not excelDict.exists(ak) Then
			excelDict.Add ak, 1
		Else
			av =  excelDict.Item(ak) + 1
			excelDict.Remove(ak)
			excelDict.Add ak, av
		End If
		
	Next

Next

Dim allResult
For k=0 To excelDict.Count - 1
	allResult = allResult &"key:"& excelDict.Keys()(k) &",value:" & excelDict.Items()(k) & vbCrlf
Next
msgbox allResult

objExcelBook.Close
objExcel.Quit
set objExcelBook = Nothing
Set objExcel = Nothing

```