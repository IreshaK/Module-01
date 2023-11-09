# Command Line Interface #

Working from the command line is like learning to ride a bicycle, or drive a car, it can be awkward at first and you will often compare it unfavourably to alternatives; but, with time and practice, you will begin to appreciate and value the unique attributes of this particular medium.

## Required Preparation ##

  * Access to a unix-like command line
  * A working Node.js installation

## Resources ##

  * [Basic linux navigation](https://www.digitalocean.com/community/tutorials/basic-linux-navigation-and-file-management)

## Practice Exercises ##

  * Create a directory
  * Touch a new file in a directory
  * Enter text into the file using nano
  * Make a copy of the file
  * Delete the file and the copy
  
## Knowledge and Skills Checklist ##

  * Access, navigate, and understand terminal program help pages
  * Navigate and interact with the filesystem from the terminal
  * Run JS programs from the terminal
  * Edit text files using terminal programs

## Getting Help ##

Before getting started on using programs with a command line interface (CLI), you should become familiar with manual pages, and help pages. One of the very first programs you're going to look at is ls which is used to list directory contents; before using the ls command to list directory contents, get some guidance on the capabilities of ls by typing: 
`ls --help`
This will print the manual for ls to your terminal; the other way you can easily find this information is with the man (manual) program by typing:
`man ls`
Doing so will open the manual for ls in another program called 'less'; to learn to navigate less you can press 'h' whilst inside a less program, which will open less's manual.

## Exploring and creating directories ##

One of the most fundamental activities you can do on a computer is to explore and interact with the filesystem, so to begin with, you will learn some of the necessary tools to navigate your directories and their files. 

### ls - List contents ###

Use ls to list the contents of a directory and begin experimenting with some commonly used arguments. Try the following commands, use the manual for ls to better understand the differences between what is being shown to you. You can't break anything by looking at it with ls, so experiment with the arguments to develop a sense of this program.
```
ls
ls -a
ls -1
ls -1S
```

### cd - Change directory ###

Use cd to change directory, there's a handy trick where you can use '.' to represent 'the current directory' and '..' to represent 'the parent directory'
Imagine I have a directory structure like below, and I am currently in the 'my_dir' directory.

my_dir/
└── docs
	├── file1
	└── file2
	
I could navigate to the docs directory by use of 
```
cd docs
```
I could then navigate back to my_dir by use of
```
cd ..
```

You can't break anything just by trying to change directories, you may not have permissions to visit every directory on your system; so try navigating around your filesystem to build your intuition with this program.

### mkdir - Make directory ###

mkdir is a program used to make directories. You pass it a new directory name and it will create it in the current directory; or you pass it a path with a new directory name and it will make that directory at that path.
Consider the same example from before:

my_dir/
└── docs
    ├── file1
    └── file2
	
If I am currently located inside my 'my_dir/docs' and run the following commands:
```
mkdir sub_docs
mkdir ../secret_docs
```

The state of my_dir will now look like this:
my_dir/
├── docs
│   ├── file1
│   ├── file2
│   └── sub_docs
└── secret_docs

If I try to make a directory that already exists, I will receive an error informing me mkdir cannot create the directory because it already exists.

You can't break anything by making a lot of directories (although you could make your directory structure quite messy!) so have a shot using the tool, don't worry too much if you make a few unnecessary directories, you'll be learning how to remove files and directories shortly.

## Creating, copying, moving, and deleting files ##

It wouldn't be much good only being able to make directories and print out the contents, you also need to be able to interact with files; now, you will learn how to modify your files and their location within the filesystem. 

### touch - Making files ###

touch is a program used to update the access and modification time of each file to the current time, but with an important addition: if the file does not exist, touch will create an empty file. Here's an example creating file3 inside the 'docs' directory, assuming I'm currently in my_dir.

```
touch ./docs/file3
```

Touching files outside of very specific circumstances won't create any problems, so try making a few new files to solidify your knowledge of touch. 

### mv - Move ###

mv is a program used to move files, here's an example moving file1 from docs to secret_docs if we are in the my_dir directory:

```
mv ./docs/file1 ./secret_docs/file1
```

You can see the basic structure of mv <source_path> <destination_path>, the destination path could be in the same directory, and with a different file name, which is an easy way to rename things.

Move is the first of the commands you've seen that does have the potential to create problems if you move the wrong files; you should still experiment with it and develop comfort, but be sure you're not moving files that are important to the operation of your system. Consider making a temporary directory (mkdir) creating a few files (touch) and then move them around.

### cp - Copy ###

cp is like mv, except the source file remains where it is, and a copy is created at the destination file path.
Here's an example copying file2 to secret_docs, and renaming it to 'secret_file2', assuming I'm in my_dir.

```
cp ./docs/file2 ./secret_docs/secret_file2
```

What about if I wanted to copy a whole directory, let's try copying docs to docs_backup; we'll make use of the -r argument to achieve this. Use cp --help to read about what the -r argument does. 

```
cp -r ./docs/ ./docs_backup/
```


Copy like touch has a few specific circumstances where you could break something, but as long as you stick to copying files inside of a directory you've created (not a system directory) you won't run into problems. 

### rm - Remove ###

rm is used to completely remove files from the filesystem, it does not send them to a recycling bin; once you rm something, it is gone forever. Be cautious with your application of rm. 

If I wanted to delete secret_file2 that is currently in secret_docs, I could do it like so:
```
rm ./secret_docs/secret_file2
```

If you want to delete a directory, the -r argument is used here (just like in mv or cp), let's get rid of docs_backup entirely now.
```
rm -r ./docs_backup/
```

Be careful with rm, especially if you're using -r; it is very easy to accidentally remove something you don't want to with rm, and it's not a delete you can simply reverse. When using rm it's best to measure twice and cut once, it's a useful tool, but with great power comes great responsibility.


## Reading text ##

### Nano ###

nano is a very lightweight text editor that comes included with even very minimal command line operating systems. Upon opening nano, you'll see the hotkeys down the bottom of the screen, the carat symbol and a letter means the control or cloverleaf key (depending on your system) and the key at the same time. Use nano to write your first javascript program, stick with the classics and write a program to log "Hello, world!" when run. To do this, run nano and enter the following code:

``` javascript
console.log("Hello, world!");
```

To save the program, exit (^x) and it will prompt you if you want to save the file (y) and then ask you for a file name, use 'hello_world.js' and hit enter to save your code to that filename and exit nano. Use ls to verify the directory now contains a 'hello_world.js' file. 

Experiment with nano a bit, despite being a very lightweight text editor, you may find it quite helpful for quickly altering small files with ease.

### Cat ###

cat is used to concatenate (where it's name is from) the contents of a file to the terminal; this is an archaic way of saying it prints the contents of files to your terminal. This can be very useful when you're navigating your filesystem in the terminal and want to check the contents of a file. Use cat to print the contents of 'hello_world.js'

```
cat hello_world.js
```

You can investigate the limited but useful capabilities of cat in the manual for it, although it's a simple program, you will find it can be incredibly helpful in a range of situations. 

### Head ###

head is a program used to quickly visit the first lines of a file, by default it will show you the top 10 lines of a file. 

```
head hello_world.js
```

The output of this will look the same as cat because our file is so small, but in some situations, a file is too large to cat the whole thing, and you only want the first few lines. 

Experiment with head on a longer file, and the way you can configure the n(umber) of lines it prints using an argument when you run the head program.

### Tail ###

tail is the opposite of head, tail is used to read the last (10 by default) lines of a file. 

```
tail hello_world.js
```

The output of this will look the same as cat and head due to the file length, but in a longer file, you may only want to look at the final few lines, for example, when reviewing log files, the last files in the log are normally the most recent and most pertinant. 

Experiment with tail, especially the ability to f(ollow) changes to the file, which can be very useful for displaying logging in real time. 

## Running JS programs ##

You will need to follow the instructions for your particular operating system to download and install Node.js, once you have acquired it, you can run your hello world program by using the node program and giving it the javascript source code file you want run.

```
node hello_world.js
```

Congratulations! You just ran your own javascript program in the terminal. 
