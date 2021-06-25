---
title: "Introduction to the command line"
subtitle: "Practical session"
author: "Patricia Carvajal-López"
date: "28/06/2021"
note: "This is a suppoting document for the practical segment of the lecture -Introduction to the command line-, from the 2021 summer school in bioinformatics.  https://www.ebi.ac.uk/training/events/summer-school-bioinformatics-2021/

---

___
# Introduction to the command line
___
This is a suppoting document for the practical segment of the lecture -Introduction to the command line-, from the 2021 summer school in bioinformatics.  https://www.ebi.ac.uk/training/events/summer-school-bioinformatics-2021/
<p>&nbsp;</p>

__Some notes before we start.__ 
* If you type the command `clear` on your terminal LINUX will clean the screen.
* The Tab key can help you to autofill commands or file/directory names
* The up and down arrows will bring back previous commands
* You have several options to get help from LINUX about the commands, for instance:
* `command -h` displays a help page about the command
* `command -help` also displays a help page about the command
* `man command` enters the manual of the commands (type `q` when you need to exit the manual)

## 1. Environmental variables  

The command `echo` is used to display lines of text or strings that are passed as an argument. For instance if you type on your Terminal
```
echo The door is closed
```
You will literally get a message on that says "The door is closed"

Now let's use the command `echo` to observe the value of a couple of environmental variables. 

Let's start with the variable _PATH_

```
echo $PATH
```

Now we let's see the value of the variable _HOME_
```
echo $HOME
```
<p>&nbsp;</p>


## 2. Directories and their content
When you opened your CLI by default LINUX locates you at your home directory. To find out the location of your current directory type `pwd` and verify this
```
pwd
```

There is a directory in your home called _practical-cli_. Let's move to that directory with the help of the command `cd`
```
cd practical-cli
```
Note that there is a spece between the command and the name of the directory.

What is the content of this directory? (Hint, find out with the help of the command `ls`)
```
ls
```
Can you identify which are files, directories, programs or links?. Even better, can you tell us more about the contents of the directory? Find out by using the `-l` option
```
ls -l
```
Are you sure that what you are seeing is everything contained within the directory. Find hidden files (well actually files that start with a dot '.') by adding the option `-a` to the `ls` command
```
ls -la
```
Now let's move arround directories (make sure that at this momment you are at the _practical-cli_ directory)

Go to _dir1_ 
```
cd dir1
```

Display the content of this directory
```
ls
```

Go back to the previous directory 
```
cd ..
```
Note that we used double dots to denote “previous directory”


Now go to _dir2_ 
```
cd dir2
```

How do I display the content of the previous directory?
```
ls ../
```

Now go to the directory _basket_ 
```
cd basket
```

From your current location, how do I display the content of the home directory? 
```
ls ~/
```
Or you could also type
```
ls $HOME
```

Go back to _dir2_ (which is the previous directory) 
```
cd ..
```
<p>&nbsp;</p>

## 3. Removal of files and directories
Now we get to remove some stuff. Remember at this momment you are supposed to be located at the _dir2_ directory.

Let's start by erasing the file _eraseme.txt_
```
rm eraseme.txt
```
Now remove the directory _i-am-here_
```
rm i-am-here
```
What happened? You noticed that Linux did not remove the directory, we need to tell the OS that what we are removing is a directory, not a file, we'll do this by adding the _-rf_ option to the _rm_ command
```
rm -rf i-am-here
```
<p>&nbsp;</p>

## 4. Changing names on files and directories
You can always modify the name of a file or directory with the help of the `mv` command. Now we'll change the name of a file and a directory

Go to the renaming directory (which is located inside 	practical-cli), then display its content
```
cd ~/practical-cli/renaming
ls
```
Rename the file car.txt to automobile.txt (verify the name 	change)
```
mv car.txt automobile.txt
ls
```
Rename the directory moto to motorcycle (verify the name 	change)
```
mv moto motorcycle
ls
```
Go back to the home directory
```
cd ~/
```

<p>&nbsp;</p>

## 5. Compression and decompression
There are several options compress and decompress files/directories, in the interest of time we’ll just use the tar command to perform compression and decompression. 

Go to the _compress-and-decompress_ directory (it's located inside the _practical-cli_ directory), then uncompress the _compress.tar.gz_ file. Verify the content of the current directory?
```
cd ~/practical-cli/compress-and-decompress
tar –xvzf compress.tar.gz
ls
```
Compress all the text files into one single file called _new.tar.gz_, verify that you created this new file
```
tar –cvzf new.tar.gz *.txt
ls
```

<p>&nbsp;</p>

## 6. Processes
Open Firefox and then go back to your terminal.
Visualize all the processes that your computer is working on by using the command
```
top
```
Identify which is the Process ID (PID) assigned to Firefox, then quit the _top_ visualization by typing
```
q
```
Suposing that Firefox's PID is 18033, terminate that process with the help of the command _kill_
```
kill -9 18033
```
Note that you have to replace the number with the PID assigned by your computer. 

Open Firefox again and go back to the terminal. Now we'll use an easyer way to get the application's PID with the help of the command _pgrep_ 
```
pgrep firefox
```
Now let's terminate Firefox's process by using any of the following options -->
```
kill  -9 PID
killall firefox
pkill firefox
```
<p>&nbsp;</p>

## 7. Create and display content
Go to the _visualizing_ directory (located inside of _practical-cli_)
```
cd ~/practical-cli/visualizing/
```
Using the command touch create two files, one called star.txt 	and another called telescope.txt. Verify that the files were created
```
touch star.txt
touch telescope.txt
ls
```
With the help of the text editor _nano_ add the lyrics of Baby Shark to the file _star.txt_. (Get the text from Google. You can copy-paste it to the text editor).
```
nano star.txt
```
Once you finish type _ctrl+o_ to save the file and _ctrl+x_ to exit

<p>&nbsp;</p>

Now let’s visualize the content of _telescope.txt_ and _cat.txt_ with 	the help of the command _cat_
```
cat telescope.txt
cat star.txt
```
You are totally right, the file _telescope.txt_ doesn't contain anything, that's why nothing showed up in the screen. 
On the other end, the file star.txt may be too long to visualize all at once. Let's see just the beginning and the end of this file with the help of the command _head_ and _tail_
```
head star.txt
tail star.txt
```

<p>&nbsp;</p>

## 8. Text analysis
Clean your screans and display the contents of your current directory (which should be _visualizing_).
```
clear
ls
```
We'll use some of these files to perform text analysis. 

First we are going to see if the file _cinco.txt_ contains the word "@message". We'll use the command _grep_ to find out
```
grep @message cinco.txt
```
What is the line number where the word "@message" is located within the _cinco.txt_ file?
```
grep -n @message cinco.txt
```
<p>&nbsp;</p>

We are going to count how many time does a word appear within a file. How many times does the _file diez.txt_ contain the word "penguin"?
```
grep -c penguin diez.txt
```
<p>&nbsp;</p>

Let's find out how many lines are there in the file _transportation.txt_. Now we'll use the command _wc_ to get this information.
```
wc -l transportation.txt
```

Visualize the content of the file _transportation.txt_. Notice that the words in the sentences  are separated by tabs (instead of spaces).
```
cat transportation.txt
```
How do I visualize only the contents of the second column of the file transportation.txt?
We'll do this using two methods. One using the command _cut_ and the other using _awk_
```
cut -f2 transportation.txt
awk '{print $2}' transportation.txt
```
_awk_ is byitself a programming language. It is used quite often on text analysis along with Perl 'one-liners'. 

<p>&nbsp;</p>

Let's get some things in order. Visualize the content of the file _weather.txt_
```
cat weather.txt
```
You'll notice it's a list of words, but they are not in order. We'll use the command _sort_ to see them in order
```
sort weather.txt
```

<p>&nbsp;</p>


## 9. Pipelines
We can combine commands and perform one process after another with the help of the _|_ (pipe) charecter.

Clean your screan and display the contents of your current directory (which should be _visualizing_).

Now put all the words contained in the second column of the file _transportation.txt_ and display them in one line.
```
cut -f2 transportation.txt|awk '{print}' ORS=' '
```

<p>&nbsp;</p>

Often we want to save the output of the processes we are running. We can do this by redirecting such output to a file with the help of the _>_ charecter.

In a new file called _analyzed.txt_, seve the text from the second column of _transportation.txt_.

```
cut -f2 transportation.txt > analyzed.txt
```
<p>&nbsp;</p>

For last, extract the third column of the _final.txt_ file, sort it, and save it in a file called _end.txt_ 
```
cut -f3 final.txt | sort > end.txt
```

<p>&nbsp;</p>
