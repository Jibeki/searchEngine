# SearchEngine
I’m building a Python command-line tool that searches a folder of local .txt files. It will rank matching files and show a line from each result so you can see why it matched.

Status · Planning
Planned demo
Create these three files in sample_docs/.
File	Contents
roasting.txt	Coffee roasting at home.
coffee.txt	Iced coffee with milk.
tea.txt	Green tea brews quickly.


Once the command-line interface is ready, run this from the project folder.
python3 search.py ./sample_docs "coffee roasting"
The expected results are shown in search order.
roasting.txt  Coffee roasting at home.
coffee.txt    Iced coffee with milk.
How search works
Documents and queries go through the same tokenizer. For example, Coffee, ROASTING! becomes ["coffee", "roasting"]. An inverted index maps each word to the files where it appears and counts its occurrences in each file.

A file ranks higher when it matches more distinct query words. If two files match the same number of words, the total number of occurrences of those words breaks the tie. In the demo, roasting.txt comes first because it contains both coffee and roasting.
Roadmap
- [ ] 1. Load documents. Write load_documents(folder) using pathlib. Read the three sample files and return each filename with its text.
- [ ] 2. Tokenize text. Turn documents and queries into lowercase words and handle punctuation.
- [ ] 3. Build the inverted index. Store the filenames and word counts for each term in a Python dictionary.
- [ ] 4. Search and rank. Look up query words and order matching files by relevance. Handle queries with no matches.
- [ ] 5. Build the command-line interface. Accept a folder and a query, then print ranked results with matching lines.
- [ ] 6. Save the index and finish the demo. Use SQLite to reuse the index across runs and add a command to rebuild it when files change. Add tests for tokenization and ranking, and update the run instructions.
Planned repository layout
Path	Purpose
README.md	Project overview, demo, and roadmap
search.py	Command-line entry point
sample_docs/	Sample text files for the demo
tests/	Search behavior tests
