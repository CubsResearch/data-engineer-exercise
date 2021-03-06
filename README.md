# API Exercise
In this exercise, you will be creating an ETL process to load MLB data from public APIs. Please use Python, Java, or another similar language. The exercise should generally not take more than 2 or 3 hours. If you do not finish within a few hours, that's okay; submit what you have at that point.

### Fetching Data
Your primary goal is to create a process that fetches all of the current day's **completed MLB** games. You can assume the process would be scheduled to run at regular intervals and by default your process should load all games that have not previously been loaded.

Your implemention should also have a way to accept a specific game ID (`gamePk`) to reload.

### Storing data
You will be given credentials to a SQL database to store the output of your process. Your code must store the following information, in a schema you create that best fits the data (Please include a `.sql` file with the DDL of any tables you create)

- Game metadata (Date, time, venue ID/name)
- Team info (IDs, names)
- Score
- Number of pitches in the game
- Name/ID of batter with highest exit-velocity hit of the game

You will notice while exploring the API that this is a very small subset of the available data. While you can explore and feel free to store anything else you find interesting, we are looking spefically for the above items.

### Resources
You can view relevant API documentation [here](https://chcubs-docs.s3.us-east-1.amazonaws.com/docs.html) (or use the `docs.html` file included in this repo).

For example, to fetch a list of all Triple-A (sport ID 11) games on 6/3/2021, you would use http://statsapi.mlb.com/api/v1/schedule?sportIds=11&date=2021-06-03.

### Some helpful notes:
- MLB Sport ID is 1.
- Within a game, there is a hierarchy of plays and events, where each play contains multiple events. Plays can be thought of at-bats or plate appearances, whereas events can be thought of as pitches or other actions that happen during an at-bat, such as stolen bases. You can assume the batter and pitcher are constant for all events within a play.
- In the MLB API, exit-velocity is referred to as `launchSpeed` and can be found within the `hitData` object of a pitch (only some pitches).
- You know a game is completed when it has a `abstractGameCode` or `statusCode` of `F`.
- Feel free to use any modules available via pip (or your language's similar package management system). Include a requirements.txt file that lists the dependencies.
- Your code can assume the tables it uses have already been created. That is, it doesn't need to automatically create the tables.
