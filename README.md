# 🎨 Pretty Bashrc

A powerful, feature-rich Bash configuration that transforms your terminal experience with enhanced aliases, functions, and a beautiful customizable prompt.  This repository provides a comprehensive toolkit for developers, system administrators, and power users who want to supercharge their command-line productivity.

![Shell](https://img.shields.io/badge/Shell-Bash-green.svg)
![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Maintenance](https://img.shields.io/badge/Maintained%3F-yes-green.svg)

## 📋 Table of Contents

- [Features](#-features)
- [Installation](#-installation)
- [Quick Start](#-quick-start)
- [Functions Reference](#-functions-reference)
  - [Search & Find](#-search--find)
  - [Documentation & Manuals](#-documentation--manuals)
  - [Video Processing](#-video-processing)
  - [Security & System Monitoring](#-security--system-monitoring)
  - [File & Permission Management](#-file--permission-management)
  - [Network & System Info](#-network--system-info)
  - [Python Development](#-python-development)
  - [Utilities](#-utilities)
  - [Prompt Customization](#-prompt-customization)
- [Aliases Reference](#-aliases-reference)
- [Configuration](#-configuration)
- [Tips & Tricks](#-tips--tricks)
- [Dependencies](#-dependencies)
- [Troubleshooting](#-troubleshooting)
- [Contributing](#-contributing)
- [License](#-license)

## ✨ Features

### 🎯 Core Features
- **130+ Productivity Aliases** - Common commands made shorter and safer
- **40+ Powerful Functions** - Complex tasks simplified into single commands
- **4 Beautiful Prompts** - Customizable, informative prompt styles with Git integration
- **Color-Coded Output** - Enhanced readability with intelligent color schemes
- **Smart History** - Expanded history with better management (1M lines!)
- **Security Toolkit** - Built-in security auditing and monitoring functions
- **Video Processing** - FFmpeg-based video rotation and metadata tools
- **Advanced Search** - Powerful file and content search capabilities

### 🚀 Why This Bashrc?

- **Saves Time** - Reduces common multi-command workflows to single function calls
- **Prevents Mistakes** - Safer defaults (e.g., `mkdir -p`, confirmation prompts)
- **Beautiful Terminal** - Professional, informative prompts with Git status
- **Learning Tool** - Well-documented functions teach best practices
- **Security-First** - Built-in security monitoring and hardening tools
- **Highly Customizable** - Easy to extend and modify for your workflow

## 📦 Installation

### Method 1: Quick Install (Recommended)

```bash
# Backup your existing bashrc
cp ~/.bashrc ~/. bashrc.backup

# Clone the repository
git clone https://github.com/ernos/pretty-bashrc.git ~/pretty-bashrc

# Copy files to your home directory
cp ~/pretty-bashrc/.bashrc ~/. bashrc
cp ~/pretty-bashrc/.bashrcfunctions ~/.bashrcfunctions

# Reload your bash configuration
source ~/.bashrc
```

### Method 2: Selective Integration

If you already have a customized `.bashrc`, you can source these files:

```bash
# Add to your existing ~/. bashrc
if [ -f ~/pretty-bashrc/.bashrcfunctions ]; then
    source ~/pretty-bashrc/.bashrcfunctions
fi

# Source specific aliases/functions you want
```

### Post-Installation

After installation, you'll see a helpful splash screen every time you open a new terminal.  Run `bashrchelp` anytime to see available functions. 

## 🎬 Quick Start

### First Commands to Try

```bash
# See all available functions
bashrchelp

# Search for files
searchf "*. log"

# Search inside files
searchinf "error" "*.log"

# Check system security
kernelTainted
listListeners

# Fix permissions recursively
fixpermissions /path/to/folder 644 755

# Create Python virtual environment
venv myproject

# Get help for any function
fixpermissions -h
searchf -h
```

## 📚 Functions Reference

### 🔍 Search & Find

#### `searchf <pattern>`
Find files by name pattern with enhanced output.

**Usage:**
```bash
searchf config           # Find files with 'config' in name
searchf '*.php'          # Find all PHP files
searchf 'index.*'        # Find all index files
searchf '*log*'          # Find files with 'log' in name
```

**Features:**
- Recursive search from current directory
- Shows file size and permissions
- Color-coded output
- Pattern matching with wildcards
- Displays result count

**Example Output:**
```
Searching for files matching:  '*.log'
----------------------------------------
📄 ./app/logs/error.log [2. 3M] (-rw-r--r--)
📄 ./system/debug.log [156K] (-rw-r--r--)
----------------------------------------
Found 2 file(s) matching '*.log'
```

---

#### `searchinf <search_string> [file_pattern] [-i]`
Search for text content inside files with context.

**Usage:**
```bash
searchinf 'function'              # Search for 'function' in all files
searchinf 'PDO' '*.php'           # Search for 'PDO' in PHP files
searchinf 'console. log' '*.js'    # Search in JavaScript files
searchinf 'ERROR' '*.log'         # Search for errors in log files
searchinf 'config' -i             # Case-insensitive search
```

**Features:**
- Shows line numbers and surrounding context
- Color-coded matches
- Supports file pattern filtering
- Case-insensitive option
- Limits output to prevent overwhelming results
- Displays match statistics

**Example Output:**
```
🔍 Searching for 'ERROR' in files matching '*.log'... 
========================================================

📁 ./app/logs/error. log
----------------------------------------
45-[2025-12-10 10:23:15] INFO: Application started
46:[2025-12-10 10:23:16] ERROR: Database connection failed
47-[2025-12-10 10:23:17] INFO:  Retrying connection... 

========================================================
🎯 Search completed for:  'ERROR'
📊 Found in 1 out of 3 files
📈 Total matches: 1
```

---

### 📖 Documentation & Manuals

#### `manfind <command> <search_string>`
Jump directly to a specific section in a manual page.

**Aliases:** `manstr`, `manjump`, `findinman`

**Usage:**
```bash
manfind bash HISTSIZE          # Jump to HISTSIZE in bash manual
manfind git commit             # Jump to commit section in git manual
manfind tar extract            # Jump to extract info in tar manual
```

**Why it's convenient:**
- No more scrolling through long man pages
- Instantly find relevant documentation
- Saves time when you know what you're looking for

---

#### `xman <command>`
Open graphical manual pages in Yelp viewer.

**Usage:**
```bash
xman bash                      # Open bash manual in GUI
xman git                       # Open git manual in GUI
```

**Why it's convenient:**
- Better readability with GUI
- Easy navigation with hyperlinks
- Search functionality
- Bookmark important sections

---

### 🎥 Video Processing

These functions require `ffmpeg` and `exiftool` to be installed.

#### `video_rotate_exif <file> [degrees]`
View or modify video rotation metadata without re-encoding.

**Usage:**
```bash
video_rotate_exif video.mp4              # View current rotation
video_rotate_exif video.mp4 90           # Set rotation to 90°
video_rotate_exif video.mp4 180          # Set rotation to 180°
video_rotate_exif video.mp4 270          # Set rotation to 270°
```

**Why it's convenient:**
- Instant rotation (no re-encoding)
- No quality loss
- Works with most modern video players
- Useful for quickly fixing phone videos

---

#### `video_rotate_90 <input> <output> [fake]`
Rotate video 90 degrees clockwise.

**Usage:**
```bash
video_rotate_90 input.mp4 output.mp4              # Re-encode and rotate
video_rotate_90 input.mp4 output.mp4 fake         # Metadata only (fast)
```

**Related Functions:**
- `video_rotate_180 <input> <output>` - Rotate 180°
- `video_rotate_270 <input> <output>` - Rotate 270° (counter-clockwise)

**Examples:**
```bash
# Properly rotate a sideways video
video_rotate_90 sideways.mp4 fixed.mp4

# Quick metadata fix (no re-encoding)
video_rotate_90 phone_video.mp4 rotated.mp4 fake

# Flip video upside down
video_rotate_180 upside_down.mp4 corrected.mp4
```

**Why it's convenient:**
- Fix improperly rotated videos from phones/cameras
- Batch processing support
- Choose between quality (re-encode) or speed (metadata)
- Built-in help with `-h` flag

---

### 🛡️ Security & System Monitoring

**⚠️ Note:** These functions require elevated privileges (`sudo`).

#### `kernelTainted`
Check if the Linux kernel has been "tainted" and verify Secure Boot status.

**Usage:**
```bash
kernelTainted
```

**What it checks:**
- Kernel taint flags (proprietary modules, forced module loading, etc.)
- Recent taint messages in kernel log
- Secure Boot enabled/disabled status

**Why it's important:**
- Detects potentially unsafe kernel modules
- Helps diagnose system stability issues
- Security compliance verification
- Required for some support scenarios

---

#### `findSuidSgidfiles`
Find all SUID and SGID files on the system.

**Usage:**
```bash
findSuidSgidfiles
```

**Why it's important:**
- SUID/SGID files can be privilege escalation vectors
- Regular auditing detects unauthorized changes
- Helps maintain security posture
- Essential for compliance and hardening

**What to look for:**
- Unexpected SUID binaries in user directories
- Recently modified SUID files
- SUID files in /tmp or unusual locations

---

#### `listListeners`
Show all active network listeners (open ports).

**Usage:**
```bash
listListeners
```

**Output includes:**
- Protocol (TCP/UDP)
- Local address and port
- Process ID and name
- User running the process

**Why it's important:**
- Detect unexpected open ports
- Identify potentially malicious listeners
- Network security auditing
- Firewall rule verification

---

#### `listSuspiciousProcesses`
Scan for processes commonly associated with malware or unauthorized access.

**Usage:**
```bash
listSuspiciousProcesses
```

**Scans for:**
- Remote desktop software (TeamViewer, AnyDesk, VNC)
- Packet capture tools (tcpdump, Wireshark)
- Network tunneling tools (netcat, socat)
- Known rootkit processes

**Why it's important:**
- Early detection of compromised systems
- Identify unauthorized remote access
- Detect packet sniffing/MITM attacks
- Security incident response

---

#### `dpgkVerify`
Verify integrity of installed packages.

**Usage:**
```bash
dpgkVerify
```

**What it does:**
- Runs `dpkg -V` to check for modified package files
- Runs `debsums` to verify checksums
- Reports any discrepancies

**Why it's important:**
- Detect rootkits and system tampering
- Verify system integrity after suspected breach
- Compliance auditing
- Troubleshoot package corruption

---

#### `cloudinitStatus`
Check cloud-init status and configuration.

**Usage:**
```bash
cloudinitStatus
```

**Why it's useful:**
- Verify cloud initialization completed successfully
- Troubleshoot cloud instance provisioning
- Check if cloud-init is enabled/disabled
- Useful for cloud deployments (AWS, Azure, GCP)

---

#### `scanRKHunter`
Run comprehensive rootkit detection scan with rkhunter.

**Usage:**
```bash
scanRKHunter
```

**Features:**
- Updates rkhunter database before scanning
- Comprehensive system scan
- Verbose logging
- Saves timestamped log file in `~/logs/`

**What it scans for:**
- Known rootkits
- Hidden files and processes
- Suspicious strings in kernel modules
- Modified system binaries
- Network listeners
- Application backdoors

**Configuration:**
```bash
# Edit the function in . bashrcfunctions to set your package manager: 
--pkgmgr DPKG    # For Debian/Ubuntu (default)
--pkgmgr RPM     # For RedHat/CentOS/Fedora
```

**Why it's important:**
- Regular security auditing
- Rootkit detection
- Post-incident forensics
- Compliance requirements

---

#### `updateFirmware`
Check for kernel and firmware updates.

**Usage:**
```bash
updateFirmware
```

**What it shows:**
- Installed kernel packages
- Available firmware updates via fwupd
- Firmware device information

**Why it's important:**
- Security updates for hardware
- Fix hardware bugs
- Performance improvements
- Maintain system stability

---

### 📁 File & Permission Management

#### `fixpermissions <path> [file_perms] [folder_perms]`
Recursively fix file and folder permissions with safety checks.

**Usage:**
```bash
fixpermissions /var/www                  # Defaults:  644 for files, 755 for folders
fixpermissions /home/user 664            # Files: 664, Folders: 755 (default)
fixpermissions /tmp 666 777              # Files: 666, Folders: 777
fixpermissions -h                        # Show detailed help
```

**Features:**
- Sets ownership to current user
- Separate permissions for files vs directories
- Safety checks prevent running on dangerous paths (/, ~, . .)
- Color-coded status output
- Comprehensive error handling

**Why it's convenient:**
- Common task after extracting archives
- Fix web server permission issues
- Restore correct ownership after sudo operations
- One command instead of multiple find/chmod/chown

**Example:**
```bash
# Fix WordPress installation permissions
fixpermissions /var/www/wordpress 644 755

# Make all scripts executable
fixpermissions ~/scripts 755 755
```

---

#### `shredfolder <path>`
Securely delete a folder and all its contents.

**Usage:**
```bash
shredfolder /path/to/sensitive/data
```

**What it does:**
1. Recursively finds all files in the folder
2. Shreds each file with 3 overwrite passes
3. Zeroes out file contents
4. Removes the folder structure

**Why it's important:**
- Secure deletion prevents data recovery
- Essential for sensitive information (passwords, keys, PII)
- More secure than standard `rm -rf`
- Compliance with data protection regulations

**⚠️ Warning:** This operation is irreversible! 

---

#### `extract <archive>`
Automatically extract various archive formats.

**Usage:**
```bash
extract file.tar.gz
extract archive.zip
extract package.tar.bz2
extract data.7z
```

**Supported formats:**
- `.tar.gz`, `.tgz` - Gzipped tarballs
- `.tar.bz2`, `.tbz2` - Bzipped tarballs
- `.tar` - Plain tarballs
- `.zip` - ZIP archives
- `.rar` - RAR archives
- `.gz` - Gzip files
- `.bz2` - Bzip2 files
- `.7z` - 7-Zip archives
- `.Z` - Compress files

**Why it's convenient:**
- No need to remember extraction commands for different formats
- Automatic format detection
- Single command for all archive types
- Verbose output shows extraction progress

---

### 🌐 Network & System Info

#### `whatsmyip` / `whatismyip`
Display internal and external IP addresses.

**Usage:**
```bash
whatsmyip
```

**Example Output:**
```
Internal IP: 192.168.1.100
External IP: 203.0.113.45
```

**Why it's convenient:**
- Quick network troubleshooting
- Verify VPN connections
- Check NAT configuration
- Useful for remote access setup

---

#### `get_pid_from_port <port|--all>`
Find which process is using a specific port. 

**Usage:**
```bash
get_pid_from_port 8080                   # Check specific port
get_pid_from_port --all                  # List all listening ports
get_pid_from_port -a                     # Short form for --all
```

**Example Output (JSON):**
```json
{
  "port": "8080",
  "pids": ["12345"],
  "processes": ["node"],
  "message": "Found processes listening on port 8080"
}
```

**Why it's convenient:**
- Troubleshoot "port already in use" errors
- Identify unexpected network services
- Kill specific process using a port
- Security auditing
- JSON output for scripting/automation

**Combined example:**
```bash
# Find what's on port 8080 and kill it
PORT=8080
PID=$(get_pid_from_port $PORT | jq -r '.pids[0]')
kill $PID
```

---

### 🐍 Python Development

#### `venv [directory]`
Create and activate a Python virtual environment.

**Usage:**
```bash
venv                    # Creates .venv in current directory
venv myproject          # Creates myproject virtual environment
venv --help             # Show detailed help
```

**What it does:**
1. Creates Python virtual environment using `python3 -m venv`
2. Automatically activates the environment
3. If environment exists, just activates it

**Why it's convenient:**
- One command instead of two (create + activate)
- Prevents polluting global Python environment
- Ensures reproducible development environments
- Best practice for Python projects

**Example workflow:**
```bash
mkdir my-python-project
cd my-python-project
venv
pip install requests flask
pip freeze > requirements.txt
```

---

### 🔧 Utilities

#### `json-generator key1 val1 key2 val2 ...`
Generate properly formatted JSON from key-value pairs.

**Aliases:** `json`

**Usage:**
```bash
json name "John Doe" age 30
# Output: {"name":  "John Doe", "age":  30}

json user "Alice" active true score 95. 5 email null
# Output: {"user": "Alice", "active": true, "score": 95.5, "email": null}

json id "001" phone "555-1234" version "2.0.1"
# Output: {"id":  "001", "phone": "555-1234", "version": "2.0.1"}
```

**Features:**
- **Automatic type detection:**
  - Integers:  `42`, `-15`, `0`
  - Floats: `3.14`, `-0.5`, `19.99`
  - Booleans: `true`/`false` (case-insensitive)
  - Null: literal string `null`
  - Strings: everything else
- Preserves leading zeros (`"001"` stays as string)
- Proper JSON escaping for special characters
- Clean, formatted output via jq

**Why it's convenient:**
- Quick API testing
- Generate config files
- Create mock data
- Scripting and automation
- No need to manually escape quotes

---

#### `string_remove_dupes <string>`
Remove duplicate words from a space-separated string.

**Usage:**
```bash
string_remove_dupes "apple banana apple cherry banana"
# Output: apple banana cherry

string_remove_dupes "one two two three three three"
# Output: one two three
```

**Why it's useful:**
- Clean up duplicate entries
- Process command output
- Data sanitization
- Used internally by other functions

---

### 🎨 Prompt Customization

Pretty Bashrc includes 4 different prompt styles.  Try them all and pick your favorite!

#### `setPrompt1`
**Fancy colored prompt with time, user, and path.**

**Features:**
- Color-coded segments with backgrounds
- Shows weekday
- Current time (HH:MM: SS)
- Username with green highlight
- Current directory
- Arrow prompt symbol

**Example:**
```
 Wed | 14:23:45  ernos @/home/ernos/projects❯
```

---

#### `setPrompt2`
**Simple colored prompt - clean and minimal.**

**Features:**
- User@hostname in green
- Current directory in cyan
- Time in yellow
- Standard `$` prompt

**Example:**
```
ernos@laptop ~/projects 14:23 $
```

---

#### `setPrompt3`
**Multi-line prompt with Git integration and status indicators.**

**Features:**
- Shows last command exit status (✓ or ✗)
- Current time in brackets
- Git branch and dirty/clean indicator
- Two-line format for better readability

**Example:**
```
[14:23:45] ✓ ernos@laptop: ~/projects (main*)
└─▶ $
```

---

#### `setPrompt4`
**Polished dynamic prompt with comprehensive Git status.**

**Features:**
- Shows exit code when non-zero
- Shortened path (last two segments)
- Git branch with dirty (✗) or clean (✓) marker
- Current time
- Updates automatically via PROMPT_COMMAND

**Example:**
```
ernos@laptop projects/pretty-bashrc (main✓) 14:23:45
❯ $
```

**How to use:**
```bash
# Try each prompt
setPrompt1
setPrompt2
setPrompt3
setPrompt4

# Add your favorite to ~/.bashrc to make it permanent
# Already included:  setPrompt3 is the default
```

---

## 🔖 Aliases Reference

### Directory Listing Aliases

| Alias | Command | Description |
|-------|---------|-------------|
| `ls` | `ls -aFh --color=always` | List with colors, file types, and human-readable sizes |
| `la` | `ls -Alh --color=always` | Show hidden files |
| `ll` | `ls -Fls --color=always` | Long listing format |
| `lx` | `ls -lXBh --color=always` | Sort by extension |
| `lk` | `ls -lSrh --color=always` | Sort by size (largest last) |
| `lc` | `ls -lcrh --color=always` | Sort by change time |
| `lu` | `ls -lurh --color=always` | Sort by access time |
| `lr` | `ls -lRh --color=always` | Recursive listing |
| `lt` | `ls -ltrh --color=always` | Sort by date (newest last) |
| `lm` | `ls -alh --color=always\|more` | Pipe through 'more' |
| `lw` | `ls -xAh --color=always` | Wide listing format |
| `labc` | `ls -lap --color=always` | Alphabetical sort |
| `lf` | `ls -l --color=always \| egrep -v '^d'` | Files only (no directories) |
| `ldir` | `ls -l --color=always \| egrep '^d'` | Directories only |

### Grep Aliases

| Alias | Command | Description |
|-------|---------|-------------|
| `grep` | `grep --text --color=auto` | Grep with color |
| `egrep` | `egrep -E --text --color=auto` | Extended grep with color |
| `fgrep` | `fgrep -F --text --color=auto` | Fixed string grep with color |
| `rgrep` | `rgrep -R --text --color=auto` | Recursive grep with color |

### System Aliases

| Alias | Command | Description |
|-------|---------|-------------|
| `bashrc` | `source ~/.bashrc` | Reload bash configuration |
| `psofport` | `lsof -i :` | Find process using port (usage: `psofport 8080`) |
| `psx` | `ps auxf` | Show all processes in tree format |
| `ping` | `ping -c 10` | Limit ping to 10 packets |
| `cls` | `clear` | Clear the screen |
| `mkdir` | `mkdir -p` | Create parent directories as needed |

### Permission Aliases

| Alias | Command | Description |
|-------|---------|-------------|
| `000` | `chmod -R 000` | No permissions |
| `644` | `chmod -R 644` | Standard file permissions |
| `666` | `chmod -R 666` | Read/write for all |
| `755` | `chmod -R 755` | Standard directory permissions |
| `777` | `chmod -R 777` | Full permissions for all |

### Process & Performance Aliases

| Alias | Command | Description |
|-------|---------|-------------|
| `topcpu` | `/bin/ps -eo pcpu,pid,user,args \| sort -k 1 -r \| head -10` | Top 10 CPU-consuming processes |
| `f` | `find . \| grep` | Quick file search |
| `countfiles` | Complex find command | Count files, links, and directories |
| `checkcommand` | `type -t` | Check if command is alias, file, or built-in |

### Network Aliases

| Alias | Command | Description |
|-------|---------|-------------|
| `openports` | `sudo netstat -nape --inet` | Show all open ports |

### System Management Aliases

| Alias | Command | Description |
|-------|---------|-------------|
| `rebootsafe` | `sudo shutdown -r now` | Safe reboot |
| `rebootforce` | `sudo shutdown -r -n now` | Force reboot (skip sync) |

### Disk Usage Aliases

| Alias | Command | Description |
|-------|---------|-------------|
| `diskspace` | `du -S \| sort -n -r \| more` | Show disk usage sorted |
| `folders` | `du -h --max-depth=1` | Show folder sizes |
| `folderssort` | `find . -maxdepth 1 -type d -print0 \| xargs -0 du -sk \| sort -rn` | Sorted folder sizes |
| `tree` | `tree -CAhF --dirsfirst` | Colorful tree view, directories first |
| `treed` | `tree -CAFd` | Tree view, directories only |
| `mountedinfo` | `df -hT` | Show mounted filesystems |

### Archive Aliases

| Alias | Command | Description |
|-------|---------|-------------|
| `mktar` | `tar -cvf` | Create tar archive |
| `mkbz2` | `tar -cvjf` | Create bzip2 archive |
| `mkgz` | `tar -cvzf` | Create gzip archive |
| `untar` | `tar -xvf` | Extract tar archive |
| `unbz2` | `tar -xvjf` | Extract bzip2 archive |
| `ungz` | `tar -xvzf` | Extract gzip archive |

### Log Viewing Aliases

| Alias | Command | Description |
|-------|---------|-------------|
| `logs` | Complex tail command | Follow all text logs in /var/log |

### Security Aliases

| Alias | Command | Description |
|-------|---------|-------------|
| `sha1` | `openssl sha1` | Calculate SHA1 hash |

---

## ⚙️ Configuration

### Customizing Your Setup

#### 1. Choose Your Prompt

Edit `~/.bashrc` and change the prompt function at the end:

```bash
# Change this line:
setPrompt3

# To any of these:
setPrompt1    # Fancy colored with backgrounds
setPrompt2    # Simple colored
setPrompt3    # Multi-line with Git (default)
setPrompt4    # Polished dynamic with Git
```

#### 2. Disable Splash Screen

If you don't want the help screen on every new terminal:

```bash
# Comment out or remove this line from . bashrc: 
bashrchelp
```

#### 3. Set Your Package Manager for RKHunter

Edit `.bashrcfunctions` and find the `scanRKHunter` function:

```bash
function scanRKHunter() {
    # Change --pkgmgr based on your distribution: 
    sudo rkhunter --check --sk --pkgmgr DPKG    # Debian/Ubuntu
    # sudo rkhunter --check --sk --pkgmgr RPM   # RedHat/CentOS/Fedora
}
```

#### 4. Customize Colors

Colors are defined at the top of `.bashrcfunctions`:

```bash
RESET="\[\e[0m\]"
BOLD="\[\e[1m\]"
RED="\[\e[31m\]"
GREEN="\[\e[32m\]"
YELLOW="\[\e[33m\]"
BLUE="\[\e[34m\]"
MAGENTA="\[\e[35m\]"
CYAN="\[\e[36m\]"
WHITE="\[\e[37m\]"
```

#### 5. Adjust History Size

Edit these lines in `.bashrc`:

```bash
export HISTFILESIZE=1000000    # Lines saved to disk
export HISTSIZE=50000          # Lines in memory
```

---

## 💡 Tips & Tricks

### 1. Getting Help

Almost all functions support the `-h` or `--help` flag:

```bash
fixpermissions -h
video_rotate_90 -h
venv --help
json-generator -h
```

### 2. Combining Functions

Chain functions together for powerful workflows:

```bash
# Find large log files and archive them
searchf "*. log" | xargs mkgz logs_backup.tar.gz

# Search for errors and save to file
searchinf "ERROR" "*.log" > error_report.txt

# Get process on port and kill it
PID=$(get_pid_from_port 8080 | jq -r '.pids[0]')
kill $PID
```

### 3. Quick Security Audit

Run these commands for a quick security check:

```bash
kernelTainted
listListeners
listSuspiciousProcesses
findSuidSgidfiles > suid_files.txt
```

### 4. Batch Video Processing

Process multiple videos at once: 

```bash
for video in *.mp4; do
    video_rotate_90 "$video" "rotated_$video"
done
```

### 5. SSH Workflow

Add to your remote servers:

```bash
# On remote server
git clone https://github.com/ernos/pretty-bashrc.git ~/.bashrc-remote
echo "source ~/.bashrc-remote/. bashrcfunctions" >> ~/.bashrc
```

### 6. Create Your Own Functions

Add custom functions to `~/.bashrcfunctions`:

```bash
function myfunction() {
    if [[ "$1" == "-h" ]]; then
        echo "My custom function help"
        return 0
    fi
    # Your code here
}
```

### 7. Alias Your Favorites

Create shorter aliases for frequently used functions:

```bash
alias sf='searchf'
alias sif='searchinf'
alias fp='fixpermissions'
alias getpid='get_pid_from_port'
```

---

## 📦 Dependencies

### Required (Core Functionality)
- **Bash 4.0+** - The shell itself
- **GNU Coreutils** - Standard Unix utilities (ls, grep, find, etc.)

### Optional (Enhanced Features)

| Tool | Purpose | Install Command |
|------|---------|----------------|
| `jq` | JSON processing for `json-generator` and `get_pid_from_port` | `sudo apt install jq` |
| `ffmpeg` | Video rotation functions | `sudo apt install ffmpeg` |
| `exiftool` | Video metadata functions | `sudo apt install libimage-exiftool-perl` |
| `rkhunter` | Rootkit scanning | `sudo apt install rkhunter` |
| `debsums` | Package verification (Debian/Ubuntu) | `sudo apt install debsums` |
| `fwupd` | Firmware updates | `sudo apt install fwupd` |
| `tree` | Directory tree visualization | `sudo apt install tree` |
| `netstat` | Network statistics (or use `ss` alternative) | `sudo apt install net-tools` |
| `lsof` | List open files and ports | `sudo apt install lsof` |

### Install All Optional Dependencies (Debian/Ubuntu)

```bash
sudo apt update
sudo apt install -y jq ffmpeg libimage-exiftool-perl rkhunter \
                     debsums fwupd tree net-tools lsof
```

### For Other Distributions

**RedHat/CentOS/Fedora:**
```bash
sudo dnf install jq ffmpeg perl-Image-ExifTool rkhunter \
                 fwupd tree net-tools lsof
```

**Arch Linux:**
```bash
sudo pacman -S jq ffmpeg perl-image-exiftool rkhunter \
               fwupd tree net-tools lsof
```

---

## 🐛 Troubleshooting

### Common Issues

#### 1. "Command not found" errors

**Problem:** Functions aren't available after installation.

**Solution:**
```bash
# Make sure functions file is sourced
source ~/.bashrcfunctions

# Or reload entire bashrc
source ~/.bashrc

# Check if file exists
ls -l ~/.bashrcfunctions
```

#### 2. Colors not showing

**Problem:** Terminal doesn't support colors or TERM is not set correctly.

**Solution:**
```bash
# Check TERM variable
echo $TERM

# Try setting it
export TERM=xterm-256color

# Add to ~/. bashrc to make permanent
echo 'export TERM=xterm-256color' >> ~/.bashrc
```

#### 3. Git branch not showing in prompt

**Problem:** Git information missing from setPrompt3 or setPrompt4.

**Solution:**
```bash
# Make sure you're in a git repository
git status

# Check if git is installed
which git

# Install git if missing
sudo apt install git
```

#### 4. Permission denied errors

**Problem:** Security functions fail with permission errors.

**Solution:**
```bash
# Most security functions require sudo
sudo kernelTainted
sudo listListeners
sudo scanRKHunter

# Or run with sudo -i to get a root shell
sudo -i
kernelTainted
```

#### 5. Video functions not working

**Problem:** "ffmpeg:  command not found" or "exiftool: command not found"

**Solution:**
```bash
# Install required dependencies
sudo apt install ffmpeg libimage-exiftool-perl

# Verify installation
ffmpeg -version
exiftool -ver
```

#### 6. JSON functions not working

**Problem:** `json-generator` or `get_pid_from_port` fails.

**Solution:**
```bash
# Install jq
sudo apt install jq

# Verify installation
jq --version
```

#### 7. History not saving properly

**Problem:** Command history gets lost between sessions.

**Solution:**
```bash
# Check history file permissions
ls -l ~/.bash_history

# Fix if needed
chmod 600 ~/.bash_history

# Check HISTFILE variable
echo $HISTFILE

# Make sure PROMPT_COMMAND is set (should be in .bashrc)
echo $PROMPT_COMMAND
```

---

## 🤝 Contributing

Contributions are welcome! Here's how you can help:

### Reporting Bugs

1. Check if the issue already exists
2. Include your OS/distribution and version
3. Provide steps to reproduce
4. Include error messages and output

### Suggesting Features

1. Open an issue describing the feature
2. Explain the use case and benefits
3. Provide examples if possible

### Submitting Pull Requests

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Follow existing code style and conventions
4. Add documentation for new functions
5. Include `-h` help text for new functions
6. Test thoroughly
7. Commit your changes (`git commit -m 'Add amazing feature'`)
8. Push to the branch (`git push origin feature/amazing-feature`)
9. Open a Pull Request

### Code Style Guidelines

- Use descriptive function names
- Add comments for complex logic
- Include help text with `-h` flag
- Use consistent indentation (4 spaces)
- Add color coding for user-facing output
- Include error handling
- Validate user input

---

## 📄 License

This project is licensed under the MIT License - see below for details: 

```
MIT License

Copyright (c) 2025 ernos

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE. 
```

---

## 🌟 Acknowledgments

- Inspired by various bashrc configurations from the Linux community
- Color schemes adapted from popular terminal themes
- Git prompt functions inspired by git-prompt. sh

---

## 📞 Support

- **Issues:** [GitHub Issues](https://github.com/ernos/pretty-bashrc/issues)
- **Discussions:** [GitHub Discussions](https://github.com/ernos/pretty-bashrc/discussions)

---

## 🗺️ Roadmap

Future enhancements planned:

- [ ] Docker container management functions
- [ ] Kubernetes helper aliases
- [ ] Cloud provider CLI shortcuts (AWS, GCP, Azure)
- [ ] Enhanced Git workflow functions
- [ ] System backup and restore functions
- [ ] Performance monitoring dashboard
- [ ] Plugin system for easy extensions
- [ ] Auto-update mechanism

---

<div align="center">

**[⬆ Back to Top](#-pretty-bashrc)**

Made with ❤️ by the community

If this project helps you, please consider giving it a ⭐! 

</div>
