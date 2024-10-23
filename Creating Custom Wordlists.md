# Creating Custom Wordlists

## Crunch

Crunch is a popular open-source tool used for creating custom wordlists or dictionaries for password cracking, network security testing, or other security-related purposes. With Crunch, users can generate wordlists based on specified criteria such as character sets, length, patterns, and combinations. 

### Basic Syntax

The basic syntax for using crunch is as follows:

```markdown
crunch <min_length> <max_length> [options]
```

- `<min_length>`: The minimum length of the generated words.
- `<max_length>`: The maximum length of the generated words.
- `[options]`: Additional options to customize the wordlist generation process.

### Character Sets

Crunch allows you to define custom character sets to include or exclude specific characters in the generated wordlists. 

Here are some commonly used character set options:

- `t <character_set>`: Specifies a custom character set to be used. For example, `t abc123` will generate words using the characters 'a', 'b', 'c', '1', '2', and '3'.
- `f <file>`: Specifies a file containing a list of characters to be used as a character set.

### Wordlist Output

Crunch provides options to control the output of the generated wordlist:

- `o <output_file>`: Specifies the output file where the generated wordlist will be saved.
- `s <start_offset>`: Sets the starting point for generating words. For example, `s 100` will start generating words from the 100th position.
- `b <byte_offset>`: Sets the maximum file size for the generated wordlist. For example, `b 1MB` restricts the output file size to 1 megabyte.

### Custom Patterns

Crunch allows you to define custom patterns or masks to generate words that follow specific formats. Some pattern options include:

- `%`: Specifies a lowercase character.
- `^`: Specifies an uppercase character.
- `@`: Specifies any character (lowercase, uppercase, or numeric).
- ``: Specifies any character (lowercase, uppercase, numeric, or special).

Example - Generate words consisting of an uppercase letter followed by two lowercase letters:

```markdown
crunch 3 3 -t ^@@ -o output.txt
```

### Advanced Options

Crunch offers additional options to further customize the wordlist generation process. Some notable options include:

- `d <separator>`: Specifies a separator character to be used when combining multiple character sets.
- `l`: Enables generation of words in a sequential manner instead of random.
- `p <prefix>`: Adds a prefix to each generated word.
- `s <suffix>`: Adds a suffix to each generated word.

### Examples:

1. Wordlist with lowercase alphabets (a-z) of length 4 to 6 characters:
    
    ```markdown
    crunch 4 6 abcdefghijklmnopqrstuvwxyz -o wordlist.txt
    ```
    
    This command will generate a wordlist (`wordlist.txt`) containing all possible combinations of lowercase alphabets with lengths ranging from 4 to 6 characters.
    
2. Wordlist with alphanumeric characters (a-z, 0–9) of length 3 to 4 characters:
    
    ```markdown
    crunch 3 4 abcdefghijklmnopqrstuvwxyz0123456789 -o wordlist.txt
    ```
    
    This command will generate a wordlist (wordlist.txt) containing all possible combinations of lowercase alphabets and digits with lengths ranging from 3 to 4 characters.
    
3. Wordlist with a custom character set and fixed length:
    
    ```markdown
    crunch 5 5 -t @%#^ -o wordlist.txt
    ```
    
    This command will generate a wordlist (`wordlist.txt`) with words of length 5 characters, where the characters can be lowercase, uppercase, numeric, or special characters specified by `@%#^`.