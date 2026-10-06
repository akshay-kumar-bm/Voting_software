# Voting Software

**A small desktop voting app (Tkinter + pandas) that checks voter IDs against a registry, allows one vote per ID, and shows tallies.**

## What it does

`run_election.py` opens a 300x300 "Online Voting System" window. A voter enters their Voter ID and picks Candidate A or B. The ID is validated against `voter_ids.csv` (500 registered IDs); a duplicate vote or unknown ID triggers an error dialog. Each accepted vote is written to `voting_data.csv`, and "View Results" shows per-candidate counts.

## Features

- Voter ID validation against a CSV registry
- One-vote-per-ID check
- Votes persisted to CSV after every submission
- Results popup with per-candidate counts
- `start_new_election.py` helper to reset `voting_data.csv` (note: it writes an empty row rather than the `Voter_ID,Vote` header)

## Tech stack

Python 3, Tkinter/ttk, pandas.

## Structure

```
run_election.py          # GUI app
start_new_election.py    # resets voting_data.csv
voter_ids.csv            # registered voter IDs
voting_data.csv          # recorded votes
requirements.txt         # lists pandas and tkinter
```

## Run

```bash
pip install pandas          # tkinter ships with Python (on Linux: apt install python3-tk)
python run_election.py
```

## Limitations

- No authentication beyond ID knowledge, no vote secrecy (voter ID stored next to the vote), no tamper protection.
- The "already voted" check uses in-memory data only, so restarting the app lets IDs vote again (the CSV is not reloaded; it is overwritten on the next vote).
- Only two hard-coded candidates; `requirements.txt` lists `tkinter`, which is not pip-installable.
- Educational project, not suitable for real elections.
