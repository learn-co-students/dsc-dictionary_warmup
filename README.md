
For today's warmup, you will be working with National Basketball Association data.  This data was acquired using the [nba_api package](https://github.com/swar/nba_api).  You will not have to use the API, rather, you will work accessing data stored in dictionaries created from the data returned from the API calls.

The team_dicts object is a list, each element of which is a dictionary associated with a different NBA team's stats from the 2019-2020 season.  

The first team listed, i.e. the team dictionary associated with index 0 of team_dicts, is the LA Lakers.

Dictionaries are made of key:value pairs. You can see the keys of a dictionary using the .keys() method.


```python
lakers.keys()
```




    dict_keys(['LeagueID', 'SeasonID', 'TeamID', 'TeamCity', 'TeamName', 'Conference', 'ConferenceRecord', 'PlayoffRank', 'ClinchIndicator', 'Division', 'DivisionRecord', 'DivisionRank', 'WINS', 'LOSSES', 'WinPCT', 'LeagueRank', 'Record', 'HOME', 'ROAD', 'L10', 'Last10Home', 'Last10Road', 'OT', 'ThreePTSOrLess', 'TenPTSOrMore', 'LongHomeStreak', 'strLongHomeStreak', 'LongRoadStreak', 'strLongRoadStreak', 'LongWinStreak', 'LongLossStreak', 'CurrentHomeStreak', 'strCurrentHomeStreak', 'CurrentRoadStreak', 'strCurrentRoadStreak', 'CurrentStreak', 'strCurrentStreak', 'ConferenceGamesBack', 'DivisionGamesBack', 'ClinchedConferenceTitle', 'ClinchedDivisionTitle', 'ClinchedPlayoffBirth', 'EliminatedConference', 'EliminatedDivision', 'AheadAtHalf', 'BehindAtHalf', 'TiedAtHalf', 'AheadAtThird', 'BehindAtThird', 'TiedAtThird', 'Score100PTS', 'OppScore100PTS', 'OppOver500', 'LeadInFGPCT', 'LeadInReb', 'FewerTurnovers', 'PointsPG', 'OppPointsPG', 'DiffPointsPG', 'vsEast', 'vsAtlantic', 'vsCentral', 'vsSoutheast', 'vsWest', 'vsNorthwest', 'vsPacific', 'vsSouthwest', 'Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec', 'PreAS', 'PostAS'])



You can see the values of a dictionary using the .values() method.


```python
lakers.values()
```




    dict_values(['00', '22019', 1610612747, 'Los Angeles', 'Lakers', 'West', '36-10', 1, ' - w', 'Pacific', '10-3 ', 1, 52, 19, 0.732, 0, '52-19', '25-10', '27-9 ', '4-6  ', '7-3  ', '6-4  ', '2-0  ', '7-3  ', '25-11', 6, 'W 6', 14, 'W 14', 10, 4, -1, 'L 1', -2, 'L 2', -1, 'L 1', 0.0, 0.0, 1, 1, 1, 0, 0, '39-8 ', '11-10', '2-1  ', '43-0 ', '7-16 ', '2-3  ', '48-14', '36-19', '22-14', '42-4 ', '38-7 ', '33-5 ', 113.4, 107.6, 5.8, '16-9', '5-5', '4-3', '7-1', '36-10', '12-3', '10-3', '14-4', '10-4', '9-2', '4-1', None, None, None, '1-0', '2-5', None, '3-1', '14-1', '9-5', '41-12', '11-7'])



# Task 1


```python
# Assign the Laker's Division Rank to the variable division rank

division_rank = lakers['DivisionRank']
division_rank
```




    1



# Task 2

Now using the `team_dict` list, loop through each team dictionary and print out the team name and the division rank for the 2019-20.
The output of the first round of the loop should look like:  

Lakers 1


```python
for team in team_dicts:
    print(team['TeamName'], team['DivisionRank'])
```

    Lakers 1
    Bucks 1
    Clippers 2
    Raptors 1
    Celtics 2
    Nuggets 1
    Rockets 1
    Pacers 2
    Heat 1
    Thunder 2
    76ers 3
    Jazz 3
    Mavericks 2
    Nets 4
    Trail Blazers 4
    Magic 2
    Grizzlies 3
    Wizards 3
    Suns 3
    Hornets 4
    Spurs 4
    Bulls 3
    Kings 4
    Knicks 5
    Pistons 4
    Pelicans 5
    Timberwolves 5
    Hawks 5
    Cavaliers 5
    Warriors 5


# Task 3

Next, let's create a set of dictionaries nested within a dictionary.  

Each dictionary will represent a division, and each value will be another dictionary.  

The second level dictionaries will have team names as keys, and division rank as values.

So, one key:value pair of the outer dictionary would look like so:

`'Pacific': {'Lakers': 1, 'Clippers': 2, 'Suns': 3, 'Kings': 4, 'Warriors': 5}`



Once you get the hang of them, list comprehensions are amazing.  They are visually concise and faster than explicit for loops.

Now your turn.  Populate a dictionary called division_dictionary that has the division ranks of each team in each of the 6 divisions.

Hint: you may need two for loops, one nested within the other.  A dictionary for each division should be created between the two for loops.


```python

division_dictionary = {}

for division in division_names:
    division_dictionary[division] = {}
    for team in team_dicts:
        if division == team['Division']:
            division_dictionary[division][team['TeamName']] =  team['DivisionRank']
division_dictionary
```




    {'Central': {'Bucks': 1,
      'Pacers': 2,
      'Bulls': 3,
      'Pistons': 4,
      'Cavaliers': 5},
     'Southwest': {'Rockets': 1,
      'Mavericks': 2,
      'Grizzlies': 3,
      'Spurs': 4,
      'Pelicans': 5},
     'Southeast': {'Heat': 1, 'Magic': 2, 'Wizards': 3, 'Hornets': 4, 'Hawks': 5},
     'Atlantic': {'Raptors': 1, 'Celtics': 2, '76ers': 3, 'Nets': 4, 'Knicks': 5},
     'Northwest': {'Nuggets': 1,
      'Thunder': 2,
      'Jazz': 3,
      'Trail Blazers': 4,
      'Timberwolves': 5},
     'Pacific': {'Lakers': 1, 'Clippers': 2, 'Suns': 3, 'Kings': 4, 'Warriors': 5}}



# Bonus

The original API call is sort of messy.  With the .get_dict() method associated with the nba_api package, we are left with a nested series of lists and dictionary. To get the data, we need to parse it with a series of keys and list indices. 

The bonus task asks you to recreate the exercise from task 3 above, starting with the new_response object below.  I.E., create a division dictionary for the 2018-19 season.

If you are feeling adventurous, code a function that takes the response as an argument, and returns the dicitonary.

The first key: value pair should be:

`'Central': {'Bucks': 1,
  'Pacers': 2,
  'Pistons': 3,
  'Bulls': 4,
  'Cavaliers': 5},`


```python
def get_division_ranks(response):
    
    '''Given a response to the nba_api LeagueStandings request, return a dictionary of division rankings.
    
    parameters: 
        response: a list of dictionaries containing league standing data
    return:
        division_dictionary: a dictionary containing the league standings of teams in each division.
    '''
    
    # Isolate headers
    new_headers = response['resultSets'][0]['headers']
    
    # Isolate data
    team_list = response['resultSets'][0]['rowSet']

    # Create a new dictionary with headers attached to the data of each team
    team_dicts = [dict(zip(new_headers, team)) for team in team_list]
    
    division_names = [team['Division'] for team in team_dicts]

    division_dictionary = {}

    for division in division_names:
        division_dictionary[division] = {}
        for team in team_dicts:
            if division == team['Division']:
                division_dictionary[division][team['TeamName']] =  team['DivisionRank']
                
    return division_dictionary

get_division_ranks(new_response)
```
