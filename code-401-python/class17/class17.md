# Read 17 : Automation

## Python Regular Expressions Tutorial [source](https://www.datacamp.com/tutorial/python-regular-expression-tutorial)

**Regular Expressions, often shortened as regex, are a sequence of characters used to check whether a pattern exists in a given text (string) or not. If you've ever used search engines, search and replace tools of word processors and text editors.**


### How to use the Regular Expressions

1. first need to `import re` library 
2. ` pattern = r"Ordinary Characters" `
3. function use in regular exprestion :

      1. **re.match( pattern , text)** ---> boolean
      2. **re.search(pattern,text)** --> boolean
      3. **re.findall(pattern,text)** --> list of all substring that match pattern
      4. **re.finditer (pattern,text)** --->returns an iterator
      5. **re.sub(pattern,repl,text,count=0)**  
   
          This method replaces all occurrences of the pattern in string with repl, substituting all occurrences, unless count provided
      1.  **re.search(pattern,text).group**    
   
           which returns the string matched, start and end which return the start and ending positions of the first match, and span which returns the start and end positions of the first match as a tuple.

### Metacharacters:
1. `^` : match start of string
2. `$` :match end of string
3. `.` dote : any characters except new line
4. `\`  Backslash.:
   
    1. `\s` - Lowercase 's'. Matches a single whitespace character
    2. `\S` - Uppercase 'S'. Matches any character not part of \s 
    3. `\w `- Lowercase 'w'. Matches any single letter, digit, or underscore.
    4. `\W `- Uppercase 'W'. Matches any character not part of \w (lowercase w).
    5. `\d` - Lowercase d. Matches decimal digit 0-9.
    6. `\D `- Uppercase d. Matches any character that is not a decimal digit.
    7. `\t `- Lowercase t. Matches tab.
    8. `\n` - Lowercase n. Matches newline.
    9. `\r` - Lowercase r. Matches return.
    10. `\A` - Uppercase a. Matches only at the start of the string. Works across multiple lines as well.
    11. `\Z` - Uppercase z. Matches only at the end of the string.
    12. `\b` - Lowercase b. Matches only the beginning or end of the word.

5. **Repetitions**:
   
     1. `*` :character appears zero or more times starting from that position.
     2. `+` : character appears one or more times starting from that position.
     3. ` ?` : character appears zero or one times starting from that position.
     4. `{x}` - Repeat exactly x number of times.
     5. `{x,}` - Repeat at least x times or more.
     6. `{x, y}` - Repeat at least x times but no more than y times.
6. `( )`	Creates a group when performing matches.
7. `< >`	Creates a named group when performing matches.

## shutil — High-level File Operations [source](https://pymotw.com/3/shutil/)
 **The shutil module includes high-level file operations such as copying and archiving.** 

 ### Copying Files:
 * copyfile() copies the contents of the source to the destination and raises IOError if it does not have permission to write to the destination file.
  
 * The implementation of copyfile() uses the lower-level function copyfileobj(). While the arguments to copyfile() are filenames, the arguments to copyfileobj() are open file handles. The optional third argument is a buffer length to use for reading in blocks.

 * The copy() function interprets the output name like the Unix command line tool cp. If the named destination refers to a directory instead of a file, a new file is created in the directory using the base name of the source.

 * copy2() works like copy(), but includes the access and modification times in the metadata copied to the new file.

 ### Copying File Metadata

 * By default when a new file is created under Unix, it receives permissions based on the umask of the current user. To copy the permissions from one file to another, use copymode().


### Working With Directory Trees

* copytree() accepts two callable arguments to control its behavior. The ignore argument is called with the name of each directory or subdirectory being copied along with a list of the contents of the directory. It should return a list of items that should be copied. The copy_function argument is called to actually copy the file.
  
  
### Finding Files

* The which() function scans a search path looking for a named file. The typical use case is to find an executable program on the shell’s search path defined in the environment variable PATH.
  

### Archives

* Python’s standard library includes many modules for managing archive files such as tarfile and zipfile. There are also several higher-level functions for creating and extracting archives in shutil. get_archive_formats() returns a sequence of names and descriptions for formats supported on the current system.

