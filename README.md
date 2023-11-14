#Loading the required libraries
import pandas  as pd
import numpy as np
from matplotlib import pyplot as plt
import seaborn as sns


#Loading the ipl match dataset
ipl=pd.read_csv(r'C:\Users\ANCHAL\Downloads\match_info_data.csv')
ipl

#Having a glance at the first five record of the dataset
ipl.head()

 #Looking at the number of row and column in the dataset
ipl.shape 

#Getting the frequency of most man of the match awards
ipl['player_of_match'].value_counts()

#Getting the top 10 players with most man of the match awards
ipl['player_of_match'].value_counts()[0:10] 

#Getting the top 5 players with most of the match awards
ipl['player_of_match'].value_counts()[0:5]

list(ipl['player_of_match'].value_counts()[0:5].keys())

#Making  a bar-plot for the top5 players with most of the match awards
plt.figure(figsize=(8,5))
plt.bar(list(ipl['player_of_match'].value_counts()[0:5].keys()),list(ipl['player_of_match'].value_counts()[0:5]),color="y")
plt.show()

#Getting the frequency of result column
ipl['result'].value_counts()

#Finding out the number of toss wins w.r.t each team
ipl['toss_winner'].value_counts()

#Extracting the records where a term won batting firts
batting_first=ipl[ipl['win_by_runs']!=0]

#Looking at the head
batting_first.head()

#making  a histogram
plt.figure(figsize=(7,7))
plt.hist(batting_first['win_by_runs'])
plt.show()

#Finding our the number of win w.r.t each  term after batting first
batting_first['winner'].value_counts()

#Making a bar-plot for top 3 teams with most wins after batting first
plt.figure(figsize=(7,7))
plt.bar(list(batting_first['winner'].value_counts()[0:3].keys()),list(batting_first['winner'].value_counts()[0:3]),color=["blue","yellow","orange"])
plt.show()

#Making a pie chart
plt.figure(figsize=(7,7))
plt.pie(list(batting_first['winner'].value_counts()),labels=list(batting_first['winner'].value_counts().keys()),autopct='%0.1f%%')
plt.show()

#Extracting those record where a term has won after battting secod
batting_second=ipl[ipl['win_by_wickets']!=0] #!=0(is not equalto 0) 



#looking at the head
batting_second.head()

#making a histogram for frequency of wins w.r.t number of wickets
plt.figure(figsize=(7,7))
plt.hist(batting_second['win_by_wickets'],bins=30)
plt.show()

#Finding out the frequency of number of wind w.r.t.each time after batting second
batting_second['winner'].value_counts()

plt.figure(figsize=(7,7))
plt.bar(list(batting_second['winner'].value_counts()[0:3].keys()),list(batting_second['winner'].value_counts()[0:3]),color=["purple","blue","yellow"])
#plt.bar(list(batting_second['winner'].value_counts()[0:3].keys()),list(batting_second['winner'].value_counts()[0:3]),color=["blue","yellow","orange"])
plt.show()



#Making a pie chart for distribution of most wins after batting second
plt.figure(figsize=(12,12))
plt.pie(list(batting_second['winner'].value_counts()),labels=list(batting_second['winner'].value_counts().keys()),autopct='%0.1f%%')
plt.show()

#Looking at the number of matches playes each season
ipl.head()
ipl['season'].value_counts()

#Looking at the number of match played in each city
ipl['city'].value_counts()



#Find out how many times a team has the match after winning the toss
import numpy as np
np.sum(ipl['toss_winner']==ipl['winner'])







