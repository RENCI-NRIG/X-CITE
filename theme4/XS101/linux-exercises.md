# Linux Exercises for CHESS Users
Wherever you see `<your CLASSE username>` below, substitute your own CLASSE username.

## Exercise 1: Logging in
Open a terminal on `lnx201` using one of the following options:
1. `ssh` from your computer's terminal (for Mac and Linux users)
   - Type `ssh <your CLASSE username>@lnx201.classe.cornell.edu`
3. PuTTY (for Windows users)
   - See https://wiki.classe.cornell.edu/Computing/WinTunnelVncSSH
5. Use CLASSE's NoMachine service
   - Browse to https://nomachine.classe.cornell.edu
   - Respond to Duo prompt
   - Click on `lnx201`
   - Create a new desktop or custom session → Create a new virtual desktop
   - Click on Terminal icon in bottom menu bar
   - To log out: Applications → Log Out
1. Use CLASSE's JupyterHub service
   - Browse to https://jupyterhub.classe.cornell.edu
   - Respond to Duo prompt
   - Server Options: Select a job profile: Local Process on JupyterHub Server, click Start
   - Launcher tab: Terminal
      - OR File → New → Terminal
   - To log out: File → Log Out

## Exercise 2: Basic commands
After logging in, you will be in your home directory. Start navigating in the same terminal window as before. Run the following commands:
1. `pwd`
   - pwd = print working directory. This commend tells you what the current working directory is
2. `ls`
   - This command lists the contents of your current working directory
3. `ls -la`
   - This command lists the contents of the current working directory with the additional options
     - `-l` tells `ls` to show details about each file’s type, permissions, size, etc. (lowercase “l” = “long”)
     - `-a` tells `ls` to list hidden files, too (“a” = “all”)
   - Individual options to ls like `-l` and `-a` can be shortened to `-la`
   - How to read the output of `ls -l`: https://docs.nersc.gov/filesystems/unix-file-permissions/
  
## Exercise 3: CHESS user directory
Do not make a habit of working in your home directory `/home/<your CLASSE username>`!

Instead, use your CHESS user directory: `/nfs/chess/user/<your CLASSE username>`.

1. Type `cd /nfs/chess/user/<your CLASSE username>`
   - cd = change directory
   - If your CHESS user directory does not exist, first type `mkdir /nfs/chess/user/<your CLASSE username>`
1. OR, use the premade symbolic link in your home directory:
   - Type `cd /home/<your CLASSE username>/CLASSE_shortcuts/chess_<your CLASSE username>`
1. Repeat Exercise 2 and observe how your CHESS user directory differs from your home directory
2. Return to your home directory
   - Type `cd /home/<your CLASSE username>`
   - OR type `cd ~`
     - The tilde symbol `~` is shorthand for your home directory

## Exercise 4: Tab completion
Tab completion is an extremely useful feature of the Linux command line that helps you type commands much faster. It works with commands and file paths. Simply start typing one or two characters of a command or file path, then hit the `tab` key. The command line will automatically fill in additional characters if it can. If it cannot fill in your command or file path all the way, hit the `tab` key twice to see the available options. (Unfortunately tab completion is not available in the JupyterHub terminal.)

For example:
1. Type `cd ~/CL`, then hit the `tab` key
   - The command line should automatically complete what you typed to `cd ~/CLASSE_shortcuts/` (unless you have another file or directory that begins with "CL")
   - Hit `return`. Now you are in the CLASSE_shortcuts directory within your home directory
   - Type `ls` to see the directory contents
2. Type `cd ch`, then hit the `tab` key
   - This time, the command line can only partially complete what you've typed. Hit the `tab` key **twice** to show the available options, one of which should be `chess_<your CLASSE username>`.
   - Now, type the first letter or two of your CLASSE username and hit `tab` again.
   - If the command line was able to complete your username, then hit `return` to go to your CHESS user directory
     - If not, keep typing letters followed by `tab` until your username is complete, then hit `return`

## Exercise 5: Use pipe to combine commands
In Linux (UNIX), a **pipe (`|`)** is used to **connect the output of one command to the input of another**. This allows for **powerful chaining** of small utilities to perform complex tasks, following the UNIX philosophy:  
> *"Do one thing well."*

For example:  
```bash
command1 | command2
```
means “take the output of `command1` and pass it as input to `command2`”.

For the following set of exercises please review [Linux commands](https://xcitecourse.org/theme2/SF100/) like `echo`, `cat`, `env`, `grep`, `more` and `less`.


### Linux pipes activity 1: Combine `echo` and `grep`
```bash
# print string; the flag -e will properly handle backslash escapes `\n` 
echo -e "apple\nbanana\ncherry"

# now combine commands via pipe
echo -e "apple\nbanana\ncherry" | grep 'an'
```
*What will be printed?*

**Expected:**  
```
banana
```

### Linux pipes activity 2: Print your shell
```bash
env | grep SHELL
```
*List all environment variables, then print only the one that specifies your current shell.*

### Linux pipes activity 3: Create files
Combine Linux tools introduced above and redirect the output to produce a new file.
```bash
# find who you are
env | grep USER

# make new area on /tmp (default temporary area on ANY Linux node)
mkdir /tmp/$USER

# create new file in /tmp/$USER area
echo "my data" > /tmp/$USER/file.dat
```
- *What would be content of /tmp/$USER/file.dat?*
- *Can you print content of the /tmp/$USER/file.dat?*

Hint: `cat` tool can be used both for viewing and creating files

```
# create new file
cat > /tmp/$USER/file.txt << EOF
one
two
three
EOF

# view the file
cat /tmp/$USER/file.txt

# chain together multiple commands with pipe
cat /tmp/$USER/file.txt | grep t | wc -l
```

### Linux pipes activity 4: Use pagination tools
Linux offer two pagination tools `less` and `more`, which can be combine with the pipe concept:
```bash
# use paginators, less and more
ls /etc | less
```
Use either tool to view and navigate large files or lengthy output from a command.
