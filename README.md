# Python Rutgers Bootcamp Challenge 

These two sets of projects helped me understand Python coding, giving me a chance to turn my initial coding into something tangible using GitBash as my dashboard and Visual Studio Code as my coding space.

## Description

In this assignment, I used the concepts I learned to complete two Python challenges, PyBank and PyPoll. Both tasks present a real-world situation where my newly developed Python scripting skills came in handy.

## pybank

PyBank Instructions

In this Challenge, I was tasked with creating a Python script to analyze the financial records of your company. You will be given a financial dataset called budget_data.csv. The dataset is composed of two columns: "Date" and "Profit/Losses".

The task is to create a Python script that analyzes the records to calculate each of the following values:

* The total number of months included in the dataset

* The net total amount of "Profit/Losses" over the entire period

* The changes in "Profit/Losses" over the entire period, and then the average of those changes

* The greatest increase in profits (date and amount) over the entire period

* The greatest decrease in profits (date and amount) over the entire period

The analysis should align with the following results:

### Dependencies

* Must have GitBash used as an application for Microsoft Windows environments which provides an emulation layer for a Git command line experience noting commands for analysis

* Must have Visual Studio Code 

### Installing

* Download the VBA raw data and copy and paste it while in VBA Developer mode in Excel. 
* No modifications needed to be made to files/folders

### VBA Code

Sub stockanalysis()


' Set CurrentWs as a worksheet object variable. CurrentWs was added to each "Cells" or "Ranges" after I got it to run on one sheet
        
        Dim CurrentWs As Worksheet
        
        Dim Need_Summary_Table_Header As Boolean
        
        Dim COMMAND_SPREADSHEET As Boolean
        
'Set Header flag

        Need_Summary_Table_Header = False

'Set Multipage Command which will command from any of the years (2018,2019,2020)

        COMMAND_SPREADSHEET = True              
        
' Loop through all of the worksheets in the active workbook.
        
        For Each CurrentWs In Worksheets

' Set an initial variables for tickername as text. Tickername functionality was taken from Credit Card example in my class. 

    Dim tickername As String
    tickername = " "
  
' Set an initial variable for tickervolume, yearlychange, percentchange. Set them as zero. Tickervolume functionality came from Credit Card example
    
    Dim yearlychange As Double
    yearlychange = 0
    
    Dim percentchange As Double
    percentchange = 0
    
    Dim tickervolume As Double
    tickervolume = 0
    
' Set an initial variable for open and close price of stock. Set open and close stocks as zero
    
    Dim Open_Price As Double
    Open_Price = 0
    Dim Close_Price As Double
    Close_Price = 0
    
' Set an initial variable for Best, Worst Yearly Change and Total Volume. Set Percent (Max & Min) and Max Volume as zero. 
    
    Dim MAX_TICKERNAME As String
    MAX_TICKERNAME = " "
    
    Dim MIN_TICKERNAME As String
    MIN_TICKERNAME = " "

    Dim MAX_PERCENT As Double
    MAX_PERCENT = 0
    
    Dim MIN_PERCENT As Double
    MIN_PERCENT = 0
       
    Dim MAX_VOLUME As Double
    MAX_VOLUME = 0
    
    Dim MAX_VOLUMETICKER As String
    MAX_VOLUMETICKER = " "
    
  
' Set an summary table for data
  
    Dim Summary_Table_Row As Integer
    Summary_Table_Row = 2
    
' Counts the number of rows and helps cycle up and down row (Used previous code for this from Rutgers class)

    Lastrow = CurrentWs.Cells(Rows.Count, 1).End(xlUp).Row
 

' Set initial value of Open Price

    Open_Price = CurrentWs.Cells(2, 3).Value
  
' Loop through each row

    For i = 2 To Lastrow
  
' Check if we are still within the same ticker, if it is not...

    If CurrentWs.Cells(i + 1, 1).Value <> CurrentWs.Cells(i, 1).Value Then
           
' Close Price Loop

    Close_Price = CurrentWs.Cells(i, 6).Value
    yearlychange = Close_Price - Open_Price
    
    If Open_Price <> 0 Then
        percentchange = (yearlychange / Open_Price) * 100
        
                    Els
  
                    End If

' Set the tickername

      tickername = CurrentWs.Cells(i, 1).Value


' Add to the tickervolume

      tickervolume = tickervolume + CurrentWs.Cells(i, 7).Value

' Print the tickername in the Summary Table

      CurrentWs.Range("J" & Summary_Table_Row).Value = tickername
      
' Print the yearlychange in the Summary Table with functionality

      CurrentWs.Range("K" & Summary_Table_Row).Value = yearlychange
      If (yearlychange > 0) Then
        CurrentWs.Range("K" & Summary_Table_Row).Interior.ColorIndex = 4
            ElseIf (yearlychange <= 0) Then
                CurrentWs.Range("K" & Summary_Table_Row).Interior.ColorIndex = 3
                    End If
      
' Print the percentagechange in the Summary Table

      CurrentWs.Range("L" & Summary_Table_Row).Value = (CStr(percentchange) & "%")
      
' Print the tickervolume in the Summary Table

      CurrentWs.Range("M" & Summary_Table_Row).Value = tickervolume
      
' Add one to the summary table row

      Summary_Table_Row = Summary_Table_Row + 1
      
' Reset the percentchange, Close_Price, Open_Price
    
      percentchange = 0
      Close_Price = 0
      Open_Price = CurrentWs.Cells(i + 1, 3).Value
      
' If then for Best Percent Change, Worst Percent Change (Got help from previous answer I found on GitHub because I could not figure out the right code for If...Then...Else
    
        If (yearlychange > MAX_PERCENT) Then
                        MAX_PERCENT = yearlychange
                        MAX_TICKERNAME = tickername
                        
                    ElseIf (yearlychange < MIN_PERCENT) Then
                        MIN_PERCENT = yearlychange
                        MIN_TICKERNAME = tickername
                        
                    End If
                           
                    If (tickervolume > MAX_VOLUME) Then
                        MAX_VOLUME = tickervolume
                        MAX_VOLUMETICKER = tickername
                        
                    End If
                    
' Hard part adjustments to resetting counters
                        
                    yearlychange = 0
                    tickervolume = 0
      
' If the cell immediately following a row is the ticker...

                    Else

' Add to the tickervolume
      
        tickervolume = tickervolume + CurrentWs.Cells(i, 7).Value

    End If

  Next i
  
' Analysis of Max Percent Change, Min Percent Change, Max Tickername, Min Tickername, Max Volume, Min Volume
 
        CurrentWs.Range("Q2").Value = (CStr(MAX_PERCENT) & "%")
        CurrentWs.Range("Q3").Value = (CStr(MIN_PERCENT) & "%")
        CurrentWs.Range("P2").Value = MAX_TICKERNAME
        CurrentWs.Range("P3").Value = MIN_TICKERNAME
        CurrentWs.Range("Q4").Value = MAX_VOLUME
        CurrentWs.Range("P4").Value = MAX_VOLUMETICKER
            
         Next CurrentWs
        
End Sub

## Help

No issues as it runs well on Microsoft Excel. Do recommend erasing the updated data to check the code every time. 

## Authors

Christopher Manfredi 

## Version History

    * Initial Release

## Acknowledgments

* This is specifically for an exercise for Rutgers Boot Camp 
