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

![image](https://github.com/Connextstrategy/python-challenge/assets/18508699/0b18f223-caef-4df7-a527-cef12fb1a3ff)


## pypoll

PyBank Instructions

In this Challenge, I was tasked with helping a small, rural town modernize its vote-counting process.

I was given a set of poll data called election_data.csv. The dataset is composed of three columns: "Voter ID", "County", and "Candidate". The task is to create a Python script that analyzes the votes and calculates each of the following values:

* The total number of votes cast

* A complete list of candidates who received votes

* The percentage of votes each candidate won

* The total number of votes each candidate won

* The winner of the election based on popular vote

Your analysis should align with the following results:

![image](https://github.com/Connextstrategy/python-challenge/assets/18508699/6fabf385-b74e-4fc1-be13-537addabf39f)


### Dependencies

* Must have GitBash used as an application for Microsoft Windows environments which provides an emulation layer for a Git command line experience noting commands for analysis

* Must have Visual Studio Code 

### Installing

* Download the VBA raw data and copy and paste it while in VBA Developer mode in Excel. 
* No modifications needed to be made to files/folders

### Python Code - pybank

First we'll import the os module
import os

# Module for reading CSV files
import csv
from statistics import mean

# Module for reading CSV files
pybankcsv = os.path.join("Resources","budget_data.csv")

# Lists to store data
profit = []
revenue = []
averagemonthlychanges = []

# Set variables to zero
 
totalmonths = 0
totalrevenue = 0
totalprofitchanges = 0
initialprofit = 0

# Open the CSV using the set path PyBankcsv

with open(pybankcsv, newline="") as csvfile:
    csvreader = csv.reader(csvfile, delimiter=",")
    csv_header = next(csvreader)

# Going through csv
    for row in csvreader:    
      
# Use count to total months
      totalmonths = totalmonths + 1 

 # Appending to add revenue for profit calculation
      revenue.append(row[0])

# Append the profit information & calculate the total profit
      profit.append(row[1])
      totalrevenue = totalrevenue + int(row[1])

#Calculate the average change in profits from month to month. Then calulate the average change in profits
      totalprofit = int(row[1])
      monthlyprofits = totalprofit - initialprofit

#Store these monthly changes in a list
      averagemonthlychanges.append(monthlyprofits)

      totalprofitchanges = totalprofitchanges + monthlyprofits
      initialprofit = totalprofit

#Calculate the average change in profits
      averagechangeprofits = (totalprofitchanges/totalmonths)

#Max and min change in profits and dates for printing out 
      bestprofits = max(averagemonthlychanges)
      worstprofits = min(averagemonthlychanges)

      bestdate = revenue[averagemonthlychanges.index(bestprofits)]
      worstdate = revenue[averagemonthlychanges.index(worstprofits)]


# Print Financial Analysis
# Print " " for space between print out
print("Financial Analysis")
print(" ")

# Print Divider
print("---------------------")
print(" ")

# Print Months Addition
print("Total Months: " + str(totalmonths))
print(" ")

# Print Total Revenue
print("Total Revenue: "+ "$" + str(totalrevenue))
print(" ")

# Print Average Charge
print("Average Change: "+ "$" + str(averagechangeprofits))
print(" ")

# Print Greatest Increase In Profits
print("Greatest Increase In Profits: "+ str(bestdate) + " ($" + str(bestprofits) + ")")
print(" ")

# Print Greatest Decrease In Profits
print("Greatest Decrease In Profits: "+ str(worstdate) + " ($" + str(worstprofits) + ")")
print(" ")

# Print a text file with 

with open('financial_analysis.txt', 'w') as text:
    text.write("Financial Analysis")
    text.write("\n")
    text.write("---------------------")
    text.write("\n")
    text.write("Total Months: " + str(totalmonths))
    text.write("\n")
    text.write("Total Revenue: "+ "$" + str(totalrevenue))
    text.write("\n")
    text.write("Average Change: "+ "$ " + str(averagechangeprofits))
    text.write("\n")
    text.write("Greatest Increase In Profits: "+ str(bestdate) + " ($" + str(bestprofits) + ")")
    text.write("\n")
    text.write("Greatest Decrease In Profits: "+ str(worstdate) + " ($" + str(worstprofits) + ")")

## Help

No issues as it runs well on Microsoft Excel. Do recommend erasing the updated data to check the code every time. 

## Authors

Christopher Manfredi 

## Version History

    * Initial Release

## Acknowledgments

* This is specifically for an exercise for Rutgers Boot Camp 
