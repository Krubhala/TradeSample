Problem:
=========

Set of sample data is given to solve the following requirements
               Create a report that shows
                        Amount in USD settled incoming everyday
                        Amount in USD settled outgoing everyday
                        Ranking of entities based on incoming and outgoing amount. 
Eg: If entity foo instructs the highest amount for a buy instruction, then foo is rank 1 for outgoing

Conditions to be satisfied:
============================

A work week starts Monday and ends Friday, unless the currency of the trade is AED or SAR, where the work week starts Sunday and ends Thursday. 
No other holidays to be taken into account.
A trade can only be settled on a working day.
If an instructed settlement date falls on a weekend, then the settlement date should be changed to the next working day.
USD amount of a trade = Price per unit * Units * Agreed Fx

Program Logic:
==============
Input has been stored in a text file (C:\\Project\\trade.txt). Input content has been provided below.
Logic has two files - main class and a sub class.

Tradeexample.java
- Reads the input text file and stores in an array list based on buy/sell category.
- getTotalUSD function used to convert the amount in to USD for each entity. It also holiday check based on currency using the function isBankHoliday.
- Hash map function used to map the generated USD values to the given entity
- printData function prints the data for Incoming and Outgoing USD total.
- dispalyRanks function orders the rank of entities. 

Input:
=======

foo|B|0.30|SGP|01 Jan 2018|02 Jan 2018|300|100.25
man|B|0.60|AED|01 Jan 2018|05 Jan 2018|150|200.25
boy|B|0.50|SAR|01 Jan 2018|20 Jan 2018|250|160.25
zoo|B|0.30|SGP|01 Jan 2018|04 Jan 2018|500|200.25
poo|B|0.60|SGP|01 Jan 2018|05 Jan 2018|150|200.25
moo|B|0.50|SGP|01 Jan 2018|06 Jan 2018|350|160.25
woman|S|0.50|SGP|02 Jan 2018|09 Jan 2018|200|100.25
bar|S|0.22|AED|05 Jan 2018|30 Mar 2018|450|150.5
ras|S|0.32|SAR|05 Jan 2018|29 Mar 2018|450|150.5

Output
=======

********Amount in USD settled incoming everyday*********

----------------------------
Settlement Date | Toal USD  
----------------------------
29-Mar-2018     | 21672.0
09-Jan-2018     | 10025.0
01-Apr-2018     | 14899.5

******** Incoming Ranking*********
---------------------------------
Ranking  |   Entity   |  Amount  
---------------------------------
1        | ras       | 21672.0
2        | bar       | 14899.5
3        | woman       | 10025.0


********Amount in USD settled outgoing everyday*********

----------------------------
Settlement Date | Toal USD  
----------------------------
08-Jan-2018     | 28043.75
21-Jan-2018     | 20031.25
04-Jan-2018     | 30037.5
02-Jan-2018     | 9022.5
07-Jan-2018     | 18022.5
05-Jan-2018     | 18022.5

******** Outgoing Ranking*********
---------------------------------
Ranking  |   Entity   |  Amount  
---------------------------------
1        | zoo       | 30037.5
2        | moo       | 28043.75
3        | boy       | 20031.25
4        | poo       | 18022.5
4        | man       | 18022.5
5        | foo       | 9022.5
