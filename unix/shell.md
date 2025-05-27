# Shell and Process in UNIX - Study Notes

## Shell

### Interpretive Cycle of Shell

The shell follows a continuous cycle:

1. **Read** - Read command from user
2. **Parse** - Break command into tokens and analyze syntax
3. **Execute** - Run the command or built-in function
4. **Wait** - Wait for command to complete
5. **Display** - Show results and display prompt again

```
User Input → Parse → Execute → Output → Prompt
    ↑                                      ↓
    ←←←←←←←←←← Repeat Cycle ←←←←←←←←←←←←←←←
```

---

## Types of Shell

### 1. Bourne Shell (sh)
- **Original** UNIX shell
- **Prompt** - $ (for regular users)
- **Features** - Basic scripting, simple

### 2. C Shell (csh)
- **Syntax** - Similar to C programming language
- **Features** - Command history, job control
- **Prompt** - %

### 3. Korn Shell (ksh)
- **Combines** - Features of Bourne and C shells
- **Features** - Advanced scripting, command editing

### 4. Bash (Bourne Again Shell)
- **Most common** on Linux systems
- **Features** - Command completion, history, advanced scripting
- **Prompt** - $ (regular users), # (root)

### 5. Zsh (Z Shell)
- **Advanced** features and customization
- **Popular** among developers

---

## Pattern Matching (Wildcards)

### Asterisk (*)
- **Matches** - Any number of characters (including zero)
```bash
ls *.txt        # All files ending with .txt
ls file*        # All files starting with "file"
ls *            # All files in current directory
```

### Question Mark (?)
- **Matches** - Exactly one character
```bash
ls file?.txt    # file1.txt, file2.txt, but not file10.txt
ls ???.doc      # Any 3-character filename with .doc extension
```

### Square Brackets []
- **Matches** - Any one character from the set
```bash
ls file[123].txt    # file1.txt, file2.txt, file3.txt
ls [a-z]*.txt       # Files starting with any lowercase letter
ls [A-Z]*           # Files starting with uppercase letter
```

### Examples
```bash
ls [!a]*        # Files NOT starting with 'a'
ls file[0-9].txt # file0.txt through file9.txt
```

---

## Escaping

### Purpose
- **Remove special meaning** of characters
- Make shell treat special characters literally

### Backslash (\)
- **Escapes** next character
```bash
echo \$HOME     # Prints: $HOME (not the value)
echo file\ name.txt  # Handle filename with space
ls \*.txt       # Look for file literally named "*.txt"
```

### Examples
```bash
echo "Price: \$10"      # Prints: Price: $10
touch file\ with\ spaces.txt  # Create file with spaces in name
```

---

## Quoting

### Single Quotes ('')
- **Preserves** everything literally
- **No variable expansion** or command substitution
```bash
echo 'Today is $USER day'   # Prints: Today is $USER day
echo 'Current directory: $(pwd)'  # Prints literally
```

### Double Quotes ("")
- **Allows** variable expansion and command substitution
- **Preserves** spaces and most special characters
```bash
echo "Today is $USER day"   # Prints: Today is john day
echo "Current directory: $(pwd)"  # Shows actual directory
```

### Backticks (`` or $())
- **Command substitution** - executes command and uses output
```bash
echo "Today is `date`"      # Shows current date
echo "Files: $(ls | wc -l)" # Shows count of files
```

---

## Redirection

### Output Redirection (>)
- **Redirects** output to file (overwrites)
```bash
ls > filelist.txt       # Save directory listing to file
echo "Hello" > greeting.txt
```

### Append Redirection (>>)
- **Appends** output to file
```bash
echo "New line" >> file.txt
date >> log.txt
```

### Input Redirection (<)
- **Takes** input from file instead of keyboard
```bash
mail user@domain < message.txt
sort < unsorted.txt > sorted.txt
```

---

## Standard Input, Output, and Error

### Standard Input (stdin) - File Descriptor 0
- **Default** - Keyboard
- **Purpose** - Where program reads input from

### Standard Output (stdout) - File Descriptor 1
- **Default** - Terminal screen
- **Purpose** - Where normal program output goes

### Standard Error (stderr) - File Descriptor 2
- **Default** - Terminal screen
- **Purpose** - Where error messages go

### Redirecting Error Messages
```bash
command 2> error.log        # Redirect errors to file
command > output.txt 2>&1   # Redirect both output and errors
command 2>/dev/null         # Discard error messages
```

---

## /dev/null and /dev/tty

### /dev/null
- **"Black hole"** - discards all data sent to it
- **Usage** - Suppress unwanted output
```bash
command > /dev/null         # Discard output
command 2>/dev/null         # Discard errors
command >/dev/null 2>&1     # Discard everything
```

### /dev/tty
- **Represents** current terminal
- **Usage** - Force output to terminal even when redirected
```bash
echo "This goes to terminal" > /dev/tty
read answer < /dev/tty      # Read from terminal
```

---

## Pipe (|)

### Purpose
- **Connects** output of one command to input of another
- **Creates** pipeline of commands

### Usage
```bash
command1 | command2         # Output of command1 becomes input of command2
ls | grep txt              # List files, then filter for .txt files
ps aux | grep user         # Show processes, filter by user
cat file.txt | sort | uniq # Display, sort, and remove duplicates
```

### Examples
```bash
ls -l | wc -l              # Count number of files
history | tail -10         # Show last 10 commands
who | sort                 # Show logged users, sorted
```

---

## tee Command

### Purpose
- **Splits** output - sends to both file and next command
- **Like** a T-junction in plumbing

### Usage
```bash
command | tee filename     # Save output to file AND display
command | tee -a filename  # Append to file AND display
```

### Examples
```bash
ls | tee filelist.txt      # Save listing to file and show on screen
ps aux | tee processes.txt | grep user  # Save all processes, filter for user
date | tee -a log.txt      # Append date to log and display
```

---

## Command Substitution

### Purpose
- **Execute** command and use its output as part of another command

### Methods
1. **Backticks** - `command`
2. **Dollar parentheses** - $(command) [preferred]

### Examples
```bash
echo "Today is `date`"                  # Using backticks
echo "Today is $(date)"                 # Using $() - preferred
files=$(ls | wc -l)                     # Store result in variable
echo "Current directory: $(pwd)"        # Embed command output
touch file_$(date +%Y%m%d).txt         # Create file with date in name
```

---

## Shell Variables

### Environment Variables
- **Available** to all programs
- **Examples** - HOME, PATH, USER
```bash
echo $HOME          # Display home directory
echo $PATH          # Display command search path
echo $USER          # Display username
```

### Local Variables
- **Available** only in current shell
```bash
name="John"         # Create variable
echo $name          # Display variable
echo "Hello $name"  # Use in string
```

### Setting Variables
```bash
export VAR=value    # Make variable available to child processes
unset VAR          # Remove variable
readonly VAR=value # Make variable read-only
```

---

# Process

## Basic Idea about UNIX Process

### Definition
- **Process** - A running program in memory
- **Instance** of a program being executed
- **Has** unique Process ID (PID)

### Process Characteristics
- **PID** - Unique process identifier
- **PPID** - Parent process ID
- **Owner** - User who started the process
- **Memory** - Allocated memory space
- **State** - Current status (running, sleeping, etc.)

---

## Display Process Attributes (ps)

### Basic ps Command
```bash
ps              # Show processes in current terminal
ps -f           # Full format listing
ps -l           # Long format
ps aux          # All processes, all users (BSD style)
ps -ef          # All processes (System V style)
```

### Output Explanation
```
PID  PPID  USER   %CPU %MEM   VSZ  RSS TTY STAT START TIME COMMAND
1234 1000  john   2.1  1.5   4532 2048 pts/0 S  10:30 0:05 bash
```

- **PID** - Process ID
- **PPID** - Parent Process ID  
- **USER** - Process owner
- **%CPU** - CPU usage percentage
- **%MEM** - Memory usage percentage
- **COMMAND** - Command name

---

## Display System Processes

### Viewing All Processes
```bash
ps aux          # All processes (BSD style)
ps -ef          # All processes (System V style)
ps -eLf         # Include threads
top             # Real-time process display
htop            # Enhanced version of top (if available)
```

### Filtering Processes
```bash
ps aux | grep username      # Processes by specific user
ps aux | grep command_name  # Processes by command name
pgrep command_name          # Find PID by command name
```

---

## Process Creation Cycle

### Fork and Exec
1. **Fork** - Parent process creates copy of itself
2. **Exec** - Child process replaces itself with new program
3. **Wait** - Parent waits for child to complete (optional)

### Process Hierarchy
- All processes descend from **init** (PID 1)
- When parent dies, children become orphans
- **init** adopts orphaned processes

---

## Shell Creation Steps

### Boot Process Chain
1. **init** (PID 1) - First process started by kernel
2. **getty** - Manages terminal connections
3. **login** - Handles user authentication
4. **shell** - User's command interpreter

### Detailed Steps
```
Kernel starts → init → getty → login → shell
                 ↓       ↓       ↓
            Monitor    Get      Start user
            terminals  username environment
```

---

## Process State

### Common Process States
- **R (Running)** - Currently executing or ready to run
- **S (Sleeping)** - Waiting for event (interruptible)
- **D (Disk Sleep)** - Waiting for I/O (uninterruptible)
- **T (Stopped)** - Process stopped by signal
- **Z (Zombie)** - Terminated but not yet cleaned up

### Viewing Process States
```bash
ps aux          # STAT column shows state
ps -l           # S column shows state
```

---

## Zombie State

### Definition
- **Zombie** - Process that has finished but not been cleaned up
- **Parent** hasn't read exit status yet
- **Shows** as \<defunct> in process list

### Characteristics
- **No resources** used except process table entry
- **Cannot** be killed with kill command
- **Cleaned up** when parent reads exit status

### Viewing Zombies
```bash
ps aux | grep defunct       # Find zombie processes
ps aux | grep Z            # Find by state
```

---

## Background Jobs

### & Operator
- **Runs** command in background
- **Returns** control to shell immediately
```bash
command &                   # Run in background
long_running_script.sh &    # Background execution
sleep 60 &                  # Sleep in background
```

### nohup Command
- **Prevents** termination when shell exits
- **Redirects** output to nohup.out
```bash
nohup command &             # Run in background, ignore hangup signal
nohup ./script.sh &         # Script continues after logout
nohup command > output.log 2>&1 &  # Custom output redirection
```

---

## Reduce Priority (nice)

### Purpose
- **Lower** process priority to be "nice" to other processes
- **Higher** nice value = lower priority

### Usage
```bash
nice command                # Run with default nice value (+10)
nice -n 15 command         # Run with nice value of 15
nice --adjustment=5 command # Alternative syntax
```

### Changing Running Process Priority
```bash
renice priority PID         # Change priority of running process
renice +5 1234             # Increase nice value (lower priority)
```

### Nice Values
- **Range** - -20 (highest priority) to +19 (lowest priority)
- **Default** - 0
- **Only root** can set negative values

---

## Using Signals to Kill Process

### kill Command
```bash
kill PID                    # Send TERM signal (polite termination)
kill -9 PID                # Send KILL signal (force termination)
kill -STOP PID             # Stop (pause) process
kill -CONT PID             # Continue stopped process
```

### Common Signals
- **TERM (15)** - Terminate (default, allows cleanup)
- **KILL (9)** - Kill immediately (cannot be caught)
- **STOP (19)** - Stop process
- **CONT (18)** - Continue process
- **HUP (1)** - Hangup

### killall Command
```bash
killall program_name        # Kill all processes with name
killall -9 firefox         # Force kill all firefox processes
```

---

## Background and Foreground Jobs

### Sending Job to Background (bg)
```bash
bg %job_number              # Send job to background
bg %1                       # Send job 1 to background
bg                          # Send current job to background
```

### Bringing Job to Foreground (fg)
```bash
fg %job_number              # Bring job to foreground
fg %1                       # Bring job 1 to foreground
fg                          # Bring current job to foreground
```

### Job Control Flow
```bash
command                     # Start in foreground
Ctrl+Z                      # Suspend job
bg                          # Resume in background
fg                          # Bring back to foreground
```

---

## Listing Jobs (jobs)

### Purpose
- **Show** jobs running in current shell session

### Usage
```bash
jobs                        # List all jobs
jobs -l                     # Include PID information
jobs -p                     # Show only PIDs
jobs -r                     # Show only running jobs
jobs -s                     # Show only stopped jobs
```

### Job Output Format
```
[1]  + running    sleep 100 &
[2]  - stopped    vi document.txt
```
- **[1], [2]** - Job numbers
- **+** - Current job
- **-** - Previous job

---

## Suspend Job

### Methods
1. **Ctrl+Z** - Suspend foreground job
2. **kill -STOP PID** - Suspend by PID

### After Suspension
```bash
jobs                        # Check suspended jobs
bg %1                       # Resume in background
fg %1                       # Resume in foreground
```

---

## Kill a Job

### By Job Number
```bash
kill %1                     # Kill job 1
kill %job_name             # Kill by command name
kill %%                    # Kill current job
```

### By PID
```bash
kill 1234                   # Kill process 1234
kill -9 1234               # Force kill process 1234
```

---

## Execute at Specified Time

### at Command
- **Schedule** one-time job execution
```bash
at 2:30pm                   # Schedule for 2:30 PM today
at 10:00am tomorrow         # Schedule for tomorrow
at now + 1 hour            # Schedule for 1 hour from now
at 9:00am 12/25/2024       # Schedule for specific date
```

### Using at Command
```bash
$ at 2:30pm
at> ls -l > listing.txt
at> <Ctrl+D>               # End input
job 1 at Mon May 26 14:30:00 2025
```

### at Command Management
```bash
atq                         # List scheduled jobs
atrm job_number            # Remove scheduled job
```

### batch Command
- **Execute** when system load is low
- **No specific time** - runs when resources available
```bash
batch                       # Schedule for low system load
batch< script.sh           # Run script when load is low
```

## Key Points for Exams

### Shell Concepts
- **Wildcards**: * (any), ? (one), [] (set)
- **Redirection**: > (output), >> (append), < (input)
- **Pipes**: | (connect commands)
- **Variables**: $VAR (use), VAR=value (set)

### Process Management
- **ps aux** - show all processes
- **kill PID** - terminate process
- **jobs** - list current jobs
- **bg/fg** - background/foreground control
- **&** - run in background
- **Ctrl+Z** - suspend job

### Job Scheduling
- **at** - schedule one-time jobs
- **batch** - run when system load is low
- **nohup** - ignore hangup signals

### Important Signals
- **15 (TERM)** - polite termination
- **9 (KILL)** - force kill
- **19 (STOP)** - pause process
- **18 (CONT)** - resume process
