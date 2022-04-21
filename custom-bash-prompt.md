# Customizing Bash prompts

We all use the command line, so the prompt is a pretty regular sight nowerdays.Some promps may look basic, some might look cool. **Here is how you can customize your prompt however you want!**

## Before you start

To edit your promt you will need to make cghanges to an important file: `~/.bashrc`. It would be wise to make a backup of this file with the following command:
```bash
cp ~/.bashrc ~/.bashrc.bak
```
To restore the default confings (if you mess something up) run:
```bash
sudo cp ~/.bashrc.bak ~/.bashrc
```

## How to edit a Bash prompt

Your current promt settings are stored in an environment variable called `PS1`. Take a look at it with the following command:
```bash
echo $PS1
```

The default Bash prompt looks something like this:
```bash
username@hostname:~$
# or
[username@hostname ~]$
```
These will return the folowing settings:
```bash
\u@\H:\w$ 
# or
[\u@\H \w]$ 
```

To access th `PS1` variable, you need to look into the `~/.bashrc` file. You can edit this file:
```bash
nano ~/.bashrc
```
It should look something like this:
```
#
# ~/.bashrc
#

# If not running interactively, don't do anything
[[ $- != *i* ]] && return

alias ls='ls --color=auto'
PS1='[\u@\H \w]$ '
```
**You can see that PS1 variable down at the bottom.**
Now to change the appearence of your prompt, you simply have to change the variable. Try setting it to `PS1='My Custom prompt > '`, save the file and exit. Now run `source ~/.bashrc` to reinitialize bash and see your new promt:
```bash
My Custom prompt > 
```

## Customization

It is possible to temporarily modify the apearence of your prompt with the `export` command. For changes to be permanent thy need to be saved in the `~/.bashrc` file.

### Username and hostname

There are many options for customizing the prompt. If you want it to display your username, try including the `\u` option:
```bash
export PS1="\u > "
# will look like
username > 
```
Or the `\H` option, which will display your devices name (Hostname):
```bash
export PS1="\u@\H> "
# will look like
username@hostname > 
```

### Time and date

- `\d` will display the current date in `weekday month day` format:

    ```bash
    export PS1="\d > "
    # will look like
    mon. january 1 > 
    ```

- `\t` will display the current time in 24h format (`hh:mm:ss`):

    ```bash
    export PS1="\t > "
    # will look like
    16:42:24 > 
    ```

### Colors

You can change the color of  your promt thanks to the `\e` option.
The syntax for this option is 
- `\e[<typeface>;<color>m` to enter color change mode

- `\e[0m` to exit color change mode

The typeface specifies the style of the text:

- `0` - Normal

- `1` - Bold

- `2` - Dim

- `4` - Underlined

The color is the color you want:

- `30` - Black

- `31` - Red

- `32` - Green

- `33` - Brown

- `34` - Blue

- `35` - Purple

- `36` - Cyan

- `37` - Light gray

**Example:**
```bash
export PS1="\e[1;31m\u@\H>\e[0m "
# will be a bold and red version of
username@hostname > 
```

### More options

**These may not work in all linux versions**

- `\a` - Bell character
- `\d` - Date
- `\D{format}` - Custom format date
- `\e` - Escape character
- `\h` - Hostname
- `\H` - Full hostname
- `\j` - Number of jobs that are being managed by the shell
- `\l` - Basename of shells terminal device
- `\n` - New line
- `\r` - Carriage return
- `\s` - Name of shell
- `\t` - Time
- `\T` - Time (12h)
- `\@` - Time (AM/PM)
- `\A` - Time (without seconds)
- `\u` - Username
- `\v` - Bash version
- `\V` - Bash version info
- `\w` - Working directory
- `\W` - Working directory basname
- `\!` - Number of command in the shell history
- `\#` - Number of command in shell session
- `\$` - User is root (`#`) or not (`$`)
- `\\` - Backslash
- `\[` - Non displayed character sequence start
- `\]` - Non displayed character sequence finish