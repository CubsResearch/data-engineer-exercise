# API Exercise
In this exercise, you will be creating an ETL process to load MLB data from public APIs. Please use Python, Java, or another similar language. The exercise should generally not take more than 2 or 3 hours, although you're free to take as much time as you'd like to work on it. If you do not finish within a few hours, that's okay; submit what you have at that point.

### Fetching Data
Your primary goal is to create a process that fetches all of the current day's completed MLB games. You can assume the process would be scheduled to run at regular intervals and by default your process should load all games that have not previously been loaded. Your implemention should also have a way to accept a specific game ID (`gamePk`) to reload.

### Storing data
You will be given credentials to a SQL database to store the output of your process. Your code must store the following information, in a schema you create that best fits the data (Please include a `.sql` file with the DDL of any tables you create)

- Game metadata (Date, time, venue ID/name)
- Team info (IDs, names)
- Score
- Number of pitches/plays in the game
- Name/ID of batter with highest exit-velocity hit of the game

You will notice while exploring the API that this is a very small subset of the available data. While you can explore and feel free to store anything else you find interesting, we are looking spefically for the above items.

### Resources
Included in the `docs` folder is information on API endpoints you may find useful. For example, to fetch a list of all Triple-A (sport ID 11) games on 6/3/2021, you would use http://statsapi.mlb.com/api/v1/schedule?sportIds=11&date=2021-06-03.

### Some helpful notes:
- MLB Sport ID is 1.
- You know a game is completed when it has a `abstractGameCode` or `statusCode` of `F`.
- Feel free to use any modules available via pip (or your language's similar package management system). Include a requirements.txt file that lists the dependencies.
- Your code can assume the tables it uses have already been created. That is, it doesn't need to automatically create the tables.
