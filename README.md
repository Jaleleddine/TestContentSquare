# TestContentSquare
? What would you change if the list of keywords was much larger (several millions) ?
for much larger list of keywords, i store the keyweords in a parquet file since it encodes data in binary format which is required for
for efficient data processing by the CPU.
We create a view from its Data Frame and execute SQL query to get the best data as follows:
sparkSess.sql("select Mot from ParquetTable where Mot like 'proj%' LIMIT 4")
For the whole code see ReadParquet class

? What would you change if the requirements were to match any portion of the
keywords (for example, given the string �pro�, the program could suggest the
keyword �repro?be�) ?
I change startWith by contains as follows:
words.filter(w=>w.contains(word)).slice(0, maxResult)
