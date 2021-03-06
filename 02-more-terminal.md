# More Terminal #

Below, I have listed examples of the many common commands and practices of the
shell. If you want to know more about specific commands, you can use man to
find out more information.

```bash
man find  # will return the man page about find. Press 'q' to get out of this page
```

Or just do what I did for this entire lesson and search The Google.

### Output to Terminal ###

#### echo - write arguments to standard output ####

```bash
# Instructions
# echo <text_to_output>

# print user inputted text to standard output
echo 'hello world!'

# OUTPUT:
# hello world!

# enable escaped characters such as new line ('\n')
echo -e 'hello\n world!'

# OUTPUT:
# hello
# world!
```

#### cat - print files to standard output ####

```bash
# Instructions
cat <file_to_output>

# output contents of file to standard output
cat myfile.txt
```

### Searching ###

#### find - Find a file recursively in a given directory ####

The find command will search a folder and ALL of its subdirectories. For
example, if Judy searches her home folder for a file, find will look in her
home folder, her Desktop folder, her documents folder, her Projects folder … until it has checked every directory and every file for the
pattern.

```bash
# Instructions
# find <starting directory> <matching criteria and actions>
```

```bash
# allowed
find ~/ -name myfile

# allowed if your current working directory is at or within your home directory
find . -name myfile

# allowed if myfolder is at or within your home directory
find myfolder/ -name myfile

# not allowed because it starts the search at the / directory
# DO NOT EVER RUN THIS!!
find / -name myfile
# DO NOT EVER RUN THIS!!
```

Actual Examples

```bash
# find a file within my Desktop folder or below named readme.txt
find ~/Desktop -name "readme.txt"

# find all .class files in my documents/ directory or below and delete them
find ~/documents -name "*.class" -exec rm {} \;

# previous command explained
# find <directory to search> -name <name including wildcard> -exec <command to execute> {} \;

# The {}'s are a placeholder for each file that the find command locates
# The \; is the end of the command specified by -exec'
```

#### grep - file pattern searcher ####
`grep` will search through the CONTENTS of files in order to find a pattern.

Note that this is different from `find` which will search through file names to match a pattern.

```bash
# Instructions
# grep "<search term>" <files_to_search>

# Arguments
# -n : show line number of occurrence
# -i : case-insensitive search
# -w : match whole word  
# -r : search recursively in sub-folders

# search within files of the projects folder for occurrences of the text "main"
grep -n "main" ~/documents/projects/*

# search all files in ~/documents and its subfolders for the whole word "shapes"
grep -nrw "shapes" ~/documents/
```

### Input/Output Redirection ###
#### Standard Input ####

The standard input is the default input to the system. When you type on the
keyboard in a terminal window, you are feeding the standard input stream. When
Scanner is used in Java, it takes input from standard input.

```bash
# Redirect standard input from user input to a file

# Instructions
# program < file

# Feed the java program with the contents of geo_input.txt
java PlaneGeometry < geo_input.txt

# Send the contents of my_story to the input of grep and search for the term "The End"
grep -n "The End" < my_story
```

#### Standard Output ####

The standard output is the default output of the system, which is usually the
terminal window. When characters are sent to the standard output, they show up
in a terminal window.

```bash
# Redirect standard output from the terminal window to a file

# Instructions
# program > file

# Send the output of the java program to output.txt
java PlaneGeometry > output.txt

# Send the output of the program 'ls' to dir_info
ls > dir_info

# Combine both standard input and standard output redirection
# geo_input.txt will send all text to the scanner
# output will capture all "System.out.print" calls.
java PlaneGeometry < geo_input.txt > output.txt
```

#### Pipes ####

A pipe connects the output of one command to the input of another.

```bash
# Instructions
# program1 | program2

# Feed the java program with the contents of input.txt
cat input.txt | java program

# NOTE: the above command is equivalent to
java program < input.txt

# search for the term "SCALAR" in the output of program
cat input.txt | java program | grep "SCALAR"
```

### Downloading From the Internet ###

```bash
# Instructions
# wget <website>

# Recursively download from a website (download the entire thing)
wget -r <website>
#Be careful. Only use this if you need to download from the entire website.
```

### Text Statistics ###
#### wc - word, line, character, byte count ####

```bash
# Print the number of lines, words, and characters of file
wc book.txt

# Print the number of lines, words, and characters from standard input
cat book.txt | wc
```

### History ###
#### history - command line history ####

```bash
# print recent previous commands
history

# re-enter command number 72
!72  <ENTER>

# print out command number 72 to Standard Output
echo "!72"
```
