# Number Guessing Game

## Overview

The **Number Guessing Game** is a command-line application built using **Bash scripting** and **PostgreSQL**. The game generates a random number between **1 and 1000**, and players attempt to guess the correct number while receiving hints after each attempt.

User statistics are stored in a PostgreSQL database, allowing the game to track the number of games played and each player's best performance.

---

## Features

* Random number generation between 1 and 1000
* User account tracking
* Persistent storage using PostgreSQL
* Records total games played
* Records best game (fewest guesses)
* Input validation for integers only
* Personalized welcome messages for returning players

---

## Technologies Used

* Bash Shell Scripting
* PostgreSQL
* SQL
* Linux Command Line

---

## How the Game Works

1. The user enters a username.
2. The system checks if the user already exists in the database.
3. New users are welcomed and added to the database.
4. Returning users are shown:

   * Total games played
   * Best game record
5. A random secret number is generated.
6. The user continues guessing until the correct number is found.
7. The system provides hints:

   * "It's higher than that"
   * "It's lower than that"
8. User statistics are updated after the game ends.

---

## Database Structure

### Database

```sql
CREATE DATABASE number_guess;
```

### Table

```sql
CREATE TABLE games (
    username VARCHAR(50) UNIQUE NOT NULL,
    games INTEGER DEFAULT 0 NOT NULL,
    best INTEGER DEFAULT 0 NOT NULL
);
```

### Sample Data

```sql
INSERT INTO games VALUES ('qwerty', 3, 1);
```

---

## Project Structure

```text
number-guess-game/
│
├── number_guess.sh
├── number_guess.sql
└── README.md
```

---

## Running the Project

### 1. Import the Database

```bash
psql -U freecodecamp < number_guess.sql
```

### 2. Make the Script Executable

```bash
chmod +x number_guess.sh
```

### 3. Run the Game

```bash
./number_guess.sh
```

---

## Example Gameplay

```text
Enter your username:
hero

Welcome back, hero! You have played 5 games, and your best game took 4 guesses.

Guess the secret number between 1 and 1000:
500
It's lower than that, guess again:
250
It's higher than that, guess again:
375
It's lower than that, guess again:
320

You guessed it in 4 tries. The secret number was 320. Nice job!
```

---

## Input Validation

The game validates user input to ensure only integers are accepted.

Example:

```text
abc
That is not an integer, guess again:
```

---

## Learning Objectives

This project demonstrates:

* Bash scripting fundamentals
* Conditional statements
* Loops and iteration
* PostgreSQL database integration
* SQL queries (SELECT, INSERT, UPDATE)
* User input validation
* Persistent data storage

---

## Future Improvements

* Store every game in a separate table
* Add a leaderboard system
* Track average guesses per player
* Add difficulty levels
* Implement multiplayer support
* Add colored terminal output

---

## Author

Created as part of the FreeCodeCamp Relational Database Certification Project.

**Developer:** Hero Park

---

## License

This project is for educational and learning purposes.
