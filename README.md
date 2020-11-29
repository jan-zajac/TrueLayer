# TrueLayer
Data Engineer Challenge v1.02

## Running
### Prerequisites
- Clone this repository to your local machine
- Download both datasets from the links and extract the data so the raw files are available in the root directory of this project.
- You only need movies_metadata.csv and enwiki-latest-abstract.xml files, so you can discard the rest.

### Setting up Postgres database
- Run the command docker-compose up from the terminal in the root directory of this project to spin up the database.
- Make sure port 5432 is free on your local machine. Otherwise change to somethin else in the docker-compose.yml file

### Processing the datasets
- The datasets and processed and uploaded to the database using the jupyter notebook true-layer-data-engineer-challeng.ipynb
- To run it, set up your pipenv environment by running *pipenv sync* in the root dir, followed by *pipenv run jupyter notebook* in your terminal.
- Follow the code and comments in the notebook to understand how the datasets are processed and uploaded to the database.

### Viewing results
- Connect to the database using any tool of your choice. I used the Postgres tool available in VS code.
- The credentials are available in the docker-compose.yml file.
- The table name is "TrueLayerDataEngineerChallenge"

### Why Docker for setting up Postgres?
- Doesn't require any installing of Postgres on your local machine
- Containerized databases are simple to deploy
- Allows for setting up multilple databases instances if needed.

### Why Pandas used for processing the data
- It's the go to library for processing data in Python. It is flexible in reading different types of data. 
- Has many functions which make processing data very quick and simple.
- Pandas is designed for vectorized calculations. Using entire columns rather than rows - making it easy to calculate things such as ratio (budget/revenue) in one go.

### Algorithmic choices
- I processed the movies metadata dataset first as it provided the 1000 entries I needed for the challenge.
- I iterated through the wiki xml dump line by line only extracting the tags and attributes that were required, instead of loading hte entire file into memory
- Once parsed I merged the extracted data into the first constrcuted dataframe.

### Testing for correctness
- If possible match against another source. Some of the data was wrong in both the wiki dump and the movies metadata dataset so those entries had to be dropped.
- Validate table schema. Table was automatically created in Postgres by pandas, so double check that all data types look correct.
- Count that there are actually 1000 entries in the table.


