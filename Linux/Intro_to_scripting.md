# Introduction to Bash Scripting

A Bash script is simply a text file containing Linux commands that are executed automatically, one after another.

Instead of typing the same commands repeatedly, you can place them in a script and run them whenever needed.

Some use cases for scripts:

- Creating users automatically
- Backing up files
- Checking disk usage
- Installing software
- Generating reports
- Performing routine system administration tasks

## Creating Your First Script

Create a file:

```sh
nano hello.sh
```

Add the following:

```sh
#!/bin/bash

echo "Hello World!"
```

- `#!/bin/bash`: This is called the shebang. It tells Linux to run the script using Bash.
- `echo "Hello World!"`: Displays text on the screen.

### Make the Script Executable

Before running a script, give it execute permissions:

```sh
chmod +x hello.sh
```

Run the Script with: `./hello.sh`

Expected output:

```sh
Hello World!
```

## Variables

Variables store data.

Create a file called variables.sh:

```sh
#!/bin/bash

NAME="Frankie"

echo "Hello $NAME"
```

- `NAME="Frankie"`: Declare a variable called `NAME` and assign the text string `Frankie` to it
- `$NAME`: Use the `$` followed by the variable's name to recall it's value

Give the script execute permission & run it

Expected output:

```sh
Hello Frankie
```

## User Input

Scripts can ask users for information.

Create a file called user_input.sh:

```sh
#!/bin/bash

read -p "Enter your name: " NAME

echo "Welcome $NAME"
```

- `read -p`: The `read` command is used to receive input from STDIN; The `-p` option displays a prompt (the message to the user).

Expected output:

```sh
Enter your name: Scout
Welcome Scout
```

## Working with Commands

Store command output in a variable:

```sh
#!/bin/bash

HOSTNAME=$(hostname)

echo "This computer is called $HOSTNAME"
```

>The next few example are implementing programming logic. If you're unfamiliar with if statements and loops don't worry, we will explore them in depth during our programming module, after which you can return to your Linux scripts to include additional functionality.

## If/Else statements

Using if statements to make decisions.

```sh
#!/bin/bash

read -p "Enter your age: " AGE

if [ "$AGE" -ge 18 ]
then
    echo "Adult"
else
    echo "Child"
fi
```

## Loops

Loops are used to perform tasks repeatedly.

### For Loop

```sh
#!/bin/bash

for NUMBER in 1 2 3 4 5
do
    echo "Number: $NUMBER"
done
```

### While Loop

```sh
#!/bin/bash

COUNT=1

while [ $COUNT -le 5 ]
do
    echo $COUNT
    ((COUNT++))
done
```

## Using Arguments

Rather than capturing user input, you may want to pass values through when you execute the script. Create the following file to accept values from the command line.

```sh
#!/bin/bash

echo "Hello $1"
```

Call the script with: `./greet.sh Frankie`

You can use and pass multiple variables into your script:

- `$1` = first argument
- `$2` = second argument
- `$3` = third argument

### Additional Special Variables

|Variable|Meaning|
|---|---|
|`$0`|Script name|
|`$#`|Number of arguments|
|`$USER`|Current user|
|`$HOME`|Home directory|

Example:

```sh
#!/bin/bash

echo "Running script: $0"
echo "Argument count: $#"
```

## Challenge 1

Create a script which reports current login information including hostname, username, and current date.

<details><summary>Answer:</summary>

```sh
#!/bin/bash

echo "System Information"
echo "=================="

echo "Hostname: $(hostname)"
echo "User: $USER"
echo "Date: $(date)"
```

</details>

## Challenge 2

For your portfolio, create a script that carries out a common system administration or business task.

If you do not yet feel confident enough to complete the task, begin by identifying the task or scenario you wish to create a script for, and try writing psuedo code (non-functional code, which lays out the logic to be completed), and you can return to it and update it as your knowledge grows.
