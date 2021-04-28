#Terminal Cheatsheet

####Interface
- Command Line Interface = Z Shell
- % = Default Shell Prompt

####Scripting
- Shell Scripts can be written with .sh file extensions.
- Z shell are declared by starting the file with #!/bin/zsh followed by the contents.

####Environment Functions
- Environment = Settings and preferences of the user.
- You can set greetings, aliases, variables, etc.
- These are saved at ~/.zshrc.
- Open the shell profile to establish settings and preferences.
- Use *source* command to effect profile settings or restart terminal.

|Key|Description|
|:-:|:-:|
|env|Lists environment variables|
|$|Prefix for environment variables e.g. \$PATH, \$USER|
|alias [string]="[command]"|Sets alias for a command|
|export [variable]="[string]"|Set string for environment variable e.g. USER|
|ln -s [path][newpath]|Link Function - This helps set a shorter file path for the path specified.|

####Shortcuts
|Key/Command|Description|
|:-:|:-:|
| Tab | Auto-complete files and folder names |
| Ctrl + A | Go to the beginning of the line you are currently typing on |
| Ctrl + E | Go to the end of the line you are currently typing on |
| Ctrl + U | Clear the line before the cursor |
| Ctrl + K | Clear the line after the cursor |
| Ctrl + W | Delete the word before the cursor |
| Ctrl + T | Swap the last two characters before the cursor |
| Esc + T | Swap the last two words before the cursor |
| Ctrl + R | Lets you search through previously used commands |
| Ctrl + L | Clears the Screen |
| Ctrl + C | Kill whatever you are running |
| Ctrl + D | Exit the current shell |
|Up/Down Arrow|Scroll through previous commands|

####Commands

#####Handy Notes
- Standard Command Format = Command -[Options] [Arguments]
- Options can be consolidated (i.e. ls -alt refers to -a & -l & -t).
- Options are case-sensitive.

|Command|Options|Description|
|:-:|:-:|:-:|
|pwd|none|Print current working directory|
|ls [dir]|none<br>-a<br>-l<br>-t<br>-R|List files in current working directory<br>List including hidden files<br>List in long format (permissions, dates, authors, etc.)<br>List sorted on last modified<br>List entire contents of folder recursively (subfolders etc.)|
|chmod [file]|none<br>-R<br>|Change permissions of file<br>Change permissions of subfolders and files|
|cd [dir]|none<br>~<br>/<br>..<br>|Navigate to home directory<br>Navigate to home directory<br>Navigate to root of drive<br>Navigate to parent directory|
|mkdir [dir]|none<br>-p|Create a new directory<br>Create nested directories (e.g. dir/dir|
|rmdir [dir]|none|Remove directory (only works on empty directories)|
|touch [file]|none|Create new file|
|cp [file][newfile]<br>cp [file][dir]<br>cp -R [dir][newdir]|none|Copy file to new file<br>Copy file to directory<br>Copy directory to new directory|
|mv [file][newfile]|none<br>-v|Move/Rename file<br>Move/Rename file and show new file|
|rm [file]|none<br>-i<br>-r<br>-f<br>|Remove file<br>Remove file with confirmation prompt<br>Remove directory and all hierarchy below<br>Force removal without confirmation|
|open [file/dir]|none|Opens file or directory|
|nano/pico/vim [file]|none|Open file in text editor|
|curl [file] [url]|none<br>-o<br>-L|Print source code of URL<br>Print result of curl function to designated file<br>Follow redirects of url 
|echo [string]|none|Print string to terminal - This can be redirected into a file|
|cat [file]|none|Print contents of file|
|grep [string] [file/dir]|none<br>-R<br>-i|Search for string with file<br>Search for string in subfolders and files<br>Case insensitive search|
|wc [file/stdin]|none<br>-c<br>-l<br>-m<br>-w<br>|Word Count of file or standard input<br>Display number of bytes<br>Display number of lines<br>Display number of characters<br>Display number of words|
|sed 's/[string]/[string]/g'|none|Stream Editor<br>s = substitute - Replaces string with string<br>g = global - Replaces strings across entire input rather than first instance in each line|
|clear|none|Clear screen|
|history|none|Shows command history|
|man [command]|none|Open manual for a command -  Press d to scroll down, w to scroll up, q to exit|
|top|none|Display active processes|
|sudo [command]|none|Run command with the security privileges of the superuser (Super User DO)|
|exit|none|Quit|

####Syntax
|Item|Description|
|:-:|:-:|
|~|Home Directory|
|.|Current Directory|
|..|Parent Directory|
|>|Push output to file (this will overwrite existing data)|
|>>|Redirect output to file and append|
|<|Tell command to read input from a file|
|\||Pipe Standard Output into following command|
|*|Wildcard character to represent anything|
|\\|'Escape' following character and print as it is|
|""|Encapsulate characters as string - useful for strings with spaces etc.|

####Useful Brew Functions
These are handy functions installed via Homebrew, a helpful package manager (brew.sh).
|Command|Options|Description|
|:-:|:-:|:-:|
|tree [dir]|none<br>-L #|Draw tree of all subfolders and files<br>Set level to which tree executes|
|code [file]|none<br>|Opens file in Visual Studio Code|

####Scripting

##### zmv function
`autoload zmv`

**zmv batch renaming of files**
`zmv -n -W '**/<>.*' '**/<>.*'`
-n is a dry-run which shows what it would rename
-W lets you use wildcards without parentheses.