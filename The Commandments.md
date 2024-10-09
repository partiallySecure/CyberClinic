# The Commandments

(linux style)

**Literal GODMODE**

If the command fails try with sudo at the beginning. Enables root privileges

```markdown
sudo
```

**Listing Files**

Lists all files and directories in the present working directory

```markdown
ls
```

Lists files in sub-directories as well

```markdown
ls -R
```

Lists hidden files as well

```markdown
ls -a
```

Lists files and directories with detailed information like permissions,size, owner, etc.

```markdown
ls -al
```

**Changing Directory**

To change to a particular directory

```markdown
cd 
```

Moves to HOME directory

```markdown
cd ~
```

Moves to the previous directory. Can be chained with / e.g. ../../../../

```markdown
cd ..
```

moves to root directory

```markdown
cd /
```

**Reading/Writing Files**

Outputs the content of the file

```markdown
cat file.txt
```

creates new file (called file.txt)

```markdown
cat > file.txt
```

Moves the file to a different directory 

```markdown
mv file.txt /home/test/
```

renames file (file.txt to file2.txt)

```markdown
mv file.txt file2.txt
```

Deletes a file

```markdown
rm file.txt
```

opens panel to edit file

```markdown
nano file.txt
```

**File Permissions**

gives file read permission

```markdown
chmod + r
```

gives file write permission

```markdown
chmod + w
```

gives file execute permission

```markdown
chmod + x
```

gives file no permission

```markdown
chmod -=
```

**Directories**

Creates a directory

```markdown
mkdir
```

Deletes a directory

```markdown
rmdir
```

Deletes a directory containing other directories

```markdown
rmdir -R
```

**Miscellaneous**

Gives help for the command before it

```markdown
man
```

Downloads a program

```markdown
apt-get
```

Clones a git source code from a URL

```markdown
git clone
```