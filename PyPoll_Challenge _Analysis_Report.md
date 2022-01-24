<!-- Strong-->

# PyPoll Challenge - Election Analysis
<!-- Horizontal Rule-->

## Overview and Background of Project
The Client (the Colorado Board of Election) has requested that an election audit of a recently completed local congressional election be done. The Client's representative, Tom, has been given the responsibility to coordinate and oversee the project on behalf of the Client. The deliverables for this project was discussed with Tom, and the understanding is that Python scripting is to be used for the exercise to deliver the following results when the script is run:

*  Total number of votes cast;
*  A complete list of candidates who received votes;
*  Total number of votes each candidate received;
*  Percentage of votes each candidate won;
*  The winner of the election based on popular vote
    

## Purpose
The purpose of this Data Analytic exercise is to use the power of Python to assist Tom, and by extension, the Colorado Board of Elections, with a detailed analysis of a large csv dataset comprising over 369,00 votes cast in favour of three candidates and to determine, ultimately, the winner of the Election.

## Analysis and Challenges
The challenge of this exercise is to determine the number of voter turnout for the Jefferson, Denver and Arapaho counties. And to establish the percentage contribution of votes from these three counties, including the county with the highest voter turnout.

### Initial Review of Dataset:
<!--UL-->
* First, a high-level inspection and review were done to get a sense of the data regarding the dataset's number of columns and rows. This was done to understand the data types and to determine whether the data was readable or would need to be converted before progressing further with the analysis. Upon inspection of the dataset, it was determined that the file was in csv format, which contained information stored in what appeared to be columns, separated by a comma, with headings for ballot ID, the name for county and candidates., included in 369,712 rows of data.  

<!--Links-->
<!--UL-->
* Because the election result dataset was so large, an investigation was done to precisely establish the number of columns and rows. This was done by opening the file in excel and utilizing various keyboard shortcuts, combining keyboard keys such as CTRL/right or down arrow keys to get a quick idea of the dataset's number of rows and columns. It was established that election result data is stored in 369, 712 rows and in three columns. 
  
* Next, it was necessary to determine whether Python was installed correctly on the machine to permit Python scripting to progress. This was achieved by scripting a simple program to print "Hello World" to the terminal. This was proven to be favourable. The data was then imported into Python for further inspection and stored in a folder called Resources as the first step towards performing the election analysis.  
  
<!--UL-->
### Initial analysis to test data before deep dive:

* This was achieved by utilizing the pseudocode method, which helps to facilitate the code scripting process by creating models or flowcharts for a high-level understanding and roadmap for the project. Hence a list of actions was written down. For example; to open the data file; to write down the names of all candidates, to add a vote count for each candidate, to get the total votes for each candidate and finally to get the total votes cast in the election, thus:

#### Pseudocode:
   * The data we need to retrieve
   * The total number of votes cast 
   * A complete list of candidates who received votes
   * The total number of votes each candidate won
   * The winner of the election based on popular vote.

1. Import the datetime class from the datetime module.
   import datetime as dt
   
2. Use the now() attribute on the datetime class to get the present time:

   * now = dt.datetime.now()
   * Print the present time:
   * print("The time right now is", now)
   * import csv
   * import os

3. Assign a variable for the file to load and the path:
  * file_to_load = 'Resources\election_results.csv'
  * file_to_load = os.path.join("Resources", "election_results.csv")

4. Assign a variable to save the file to a path.
* file_to_save = os.path.join("analysis", "election_analysis.txt")

5. Open the election results and read the file.
* with open(file_to_load) as election_data:

### Perform analysis.
* print(election_data)

Close the file.
* election_data.close()

6. Create a filename variable to a direct or indirect path to the file
* file_to_save = os.path.join("analysis", "election_analysis.txt")

7. Using the open() function with the "w" mode we will write data to the file.
* open(file_to_save, "w")

8. Create a filename variable to a direct or indirect path to the file. 
* file_to_save = os.path.join("analysis","election_analysis.txt")

9. Use the open statement to open the file as a text file.
* with open(file_to_save,"w") as txt_file:

10. Write some data to the file.
* txt_file.write("Hello World, ")

11. Write three counties to the file.
    * txt_file.write("Arapahoe, ")
    * txt_file.write("Denver, ")
    * txt_file.write("Jefferson")

12. Write three counties to the file.
    * txt_file.write("Arapahoe, Denver, Jefferson")
    * txt_file.write("Counties in the Election\n------------------------\n")
    * txt_file.write("Arapahoe\nDenver\nJefferson")

 <!--UL--> 
## Analysis of Election & Results 

* A new python file was created and named "PyPoll_Challenge.py". This was used to generate the output for the analysis of the election results thus: 

* Add our dependencies.
import csv
import os
* Assign a variable to load a file from a path.
file_to_load = os.path.join("Resources", "election_results.csv")
* Assign a variable to save the file to a path.
file_to_save = os.path.join("analysis", "election_analysis.txt")
* Initialize a total vote counter.
total_votes = 0
* Candidate options and candidate votes.
candidate_options = []
candidate_votes = {}
* Create a county list and county votes dictionary.
county_list = []
county_dict = {}

* Track the winning candidate, vote count, and percentage.
winning_candidate = ""
winning_count = 0
winning_percentage = 0

* Track the largest county and county voter turnout.
largest_county = ""
county_voter_turnout = 0
winning_count_percentage = 0

* Open the election results and read the file.
with open(file_to_load) as election_data:
    file_reader = csv.reader(election_data)
    
    Read the header row.
    headers = next(file_reader)
    
    Print each row in the CSV file.
    for row in file_reader:
        
        Add to the total vote count.
        total_votes += 1
        
        Get the candidate name from each row.
        candidate_name = row[2]
        
        3: Extract the county name from each row.
        county_name = row[1]

        If the candidate does not match any existing candidate, add the
        the candidate list.
        if candidate_name not in candidate_options:
            
            Add the candidate name to the candidate list.
            candidate_options.append(candidate_name)
            
            And begin tracking that candidate's voter count.
            candidate_votes[candidate_name] = 0
        Add a vote to that candidate's count.
        candidate_votes[candidate_name] += 1

        4a: Write an if statement that checks that the
        if county_name not in county_list:
        county does not match any existing county in the county list.
             4b: Add the existing county to the list of counties.
            county_list.append(county_name)
             4c: Begin tracking the county's vote count.
            county_dict[county_name] = 0
        5: Add a vote to that county's vote count.
        county_dict[county_name] += 1

        Save the results to our text file.
with open(file_to_save, "w") as txt_file:
    After opening the file print the final vote count to the terminal.
    election_results = (
        f"\nElection Results\n"
        f"-------------------------\n"
        f"Total Votes: {total_votes:,}\n"
        f"-------------------------\n")
    print(election_results, end="")
    After printing the final vote count to the terminal save the final vote count to the text file.
    txt_file.write(election_results)

<!--Links-->
3. Next,  [Stockoverflow](https://stackoverflow.com/search?q=python+dictionary
"Iterating over dictionaries using 'for' loops") was consulted for assistance with a code string when iterating over dictionaries using 'for' loop and how to add new keys to a dictionary in Python.  
   
 ## 6a: Write a for loop to get the county from the county dictionary.
   
    for county_name in county_dict:
        
        # 6b: Retrieve the county vote count.
        county_votes = county_dict[county_name]
        # 6c: Calculate the percentage of votes for the county.
        county_votes_percentage = float(county_votes)/float(total_votes) * 100
            # 6d: Print the county results to the terminal.
        county_results = (
            f"\nCounty Votes:\n"
            f"{county_name}: {county_votes_percentage:.1f}% ({county_votes:,})\n")
            # Print each County Votes and percentage to the terminal
                    
        print(county_results)
            # 6e: Save the county votes to a text file.
        txt_file.write(county_results)
            # 6f: Write an if statement to determine the winning county and get its vote count.
        if (county_votes > county_voter_turnout) and (county_votes_percentage > winning_count_percentage):
            county_voter_turnout = county_votes
            largest_county = county_name
            winning_count_percentage = county_votes_percentage

### 7: Print the county with the largest turnout to the terminal.
    largest_county_summary = (
        f"\n-------------------------\n"
        f"Largest County Turnout: {largest_county}\n"
        f"-------------------------\n")
    print(largest_county_summary)

### 8: Save the county with the largest turnout to a text file.
    txt_file.write(largest_county_summary)

    for candidate_name in candidate_votes:
        # Retrieve vote count and percentage.
        votes = candidate_votes[candidate_name]
        vote_percentage = float(votes) / float(total_votes) * 100
        candidate_results = (
            f"{candidate_name}: {vote_percentage:.1f}% ({votes:,})\n")

        # Print each candidate's voter count and percentage to the terminal.
        print(candidate_results)
        #  Save the candidate results to our text file.
        txt_file.write(candidate_results)
        # Determine winning vote count, winning percentage, and winning candidate.
        if (votes > winning_count) and (vote_percentage > winning_percentage):
            winning_count = votes
            winning_candidate = candidate_name
            winning_percentage = vote_percentage
    # Print the winning candidate's results to the terminal.
    winning_candidate_summary = (
        f"-------------------------\n"
        f"Winner: {winning_candidate}\n"
        f"Winning Vote Count: {winning_count:,}\n"
        f"Winning Percentage: {winning_percentage:.1f}%\n"
        f"-------------------------\n")
    print(winning_candidate_summary)
    # Save the winning candidate's results to the text file.
    txt_file.write(winning_candidate_summary)
 
### Analysis of Outcomes Based Refactored Codes versus Original Codes
<!--UL-->
 <!--Strong--> 
 <!--Images-->
### Results from Election Analysis:

![Election Results](https://github.com/Brentnol/Election-Analysis/blob/main/Resources/Election%20Results.png)

   
 <!--OL--> 
### Challenges and Solutions Encountered

1.  Learning and executing the for loop, and writing to the text file were challenging. However, over time, I grasped key concepts of these commands to produce the desired results.

2.  Stockoverflow continues to be a fantastic resource with a considerable repertoire of codes and other valuable resources. StackOverflow was consulted extensively during this exercise. 

## Conclusions:
<!--OL-->
### Outcomes based on Python Analysis of the Election Results:
1.  Python scripting has proven itself to be a powerful data analytic tool in performing the election audit analysis for the Colorado Election Commission. As can be seen from the results, we were able to accurately determined, by way of python scripting, the total number of votes cast in the recent Colorado congressional election. And further established that the ballots were cast in favour of three candidates, Charles Casper Stockham, Diana Degette and Raymon Anthony Doane; with 23%, 73.8% and 3.1% of the votes, respectively, representing a total of 369,711 total votes cast. Furthermore, we determined that Diana Degette won the election, securing a total of 272,892 votes or 73.8%.

