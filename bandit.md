## Overthewire: Bandit wargame

ssh -p 2220 banditx@bandit.labs.overthewire.org to access Bandit level x 

**Level 0**: 
- [X] ls then cat readme
- [X] password: ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If

**Level 1 -> level 2**: 
- [X] cat ./-
- [X] password: 263JGJPfgU6LtdEvgfWU1XP5yac29mFx
* ./ specify to shell that - is a file

**Level 2 -> level 3**: 
- [X] cat "spaces in this filename"
- [X] password: MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx
- [X] enclose filename in quotes for shell to treat the entire name as one argument

**Level 3 -> level 4**: 
- [X] cd inhere then ls -a then cat "...Hiding-From-You"
- [X] password: 2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ
* -a shows all directory contents (including hidden ones)

**Level 4 -> level 5**: 
- [X] cd inhere then file ./* then cat -- file07 (file type ASCII text which is human readable)
- [X] password: 4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw
* file shows the file type and -- used to indicate end of command option so the file name is properly handled by shell

**Level 5 -> level 6**: 
- [X] find inhere -type f -size 1033c ! -executable -exec file {} \; | grep "text"
then cat inhere/maybehere07/.file2 (provided target file)
- [X] password: HWasnPhtq9AVKe0dmk45nxy20cvUa6EG
* makes good use of find command: looks for files that is human-readable, 1033 bytes in size and not executable

**Level 6 -> level 7**: 
- [X] find / -type f -size 33c -user bandit7 -group bandit6 2>/dev/null
then cat /var/lib/dpkg/info/bandit7.password (identified file)
- [X] password: morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj
* 2>/dev/null to suppress permission denied errors 

**Level 7 -> level 8**: 
- [X] grep "millionth" data.txt
- [X] password: dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc
* grep command used to locate lines containing the word "millionth"

**Level 8 -> level 9**: 
- [X] sort data.txt | uniq -u
- [X] password: 4CKMh1JI91bUIZZPXDqGanal4xvAg0JM
* uniq -u finds lines that only occur exactly once

**Level 9 -> level 10**: 
- [X] strings data.txt | grep '='
- [X] password: FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
* strings command extracts readable text from data.txt

**Level 10 -> level 11**: 
- [X] base64 -d data.txt
- [X] password: dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr
* base64 command used to decode the data 

**Level 11 -> level 12**: 
- [X] tr 'A-Za-z' 'N-ZA-Mn-za-m' < data.txt
- [X] password: 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4
* tr command translates characters based on two sets of characters provided. For ROT13:
Source Set: A-Za-z
Target Set: N-ZA-Mn-za-m 
(it is 13 positions from A to M)

**Main objective: get familiar with using different unix command lines


