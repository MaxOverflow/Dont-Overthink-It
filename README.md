# Learning resources
A repo for useful tools and resources in my journey to learning ICT

Absolute and Relative Paths
“.” Current directory
“..” Parent directory
Accessing Directories
Print working directory
pwd
Change to home directory
cd ~ or cd
Change to parent directory
cd ..
Change to previous directory
cd -
Change to root
cd /
Base64 Encoding (is not encryption!)
base64 -d -e
-d(ecode)
-e(ncode)

echo ‘text’ | base64 -d/e
Command Line Customisation

# See current Bash prompt
$ echo “PS1”


# Default CLI prompt
PS1="\u@\h \$ "
\u(ser)
\h(ome)
\$($)
\s(hell name)
\v(ersion)
\d(ate)
\t(ime - 24 Hr)
\T(ime - 12 Hr)
\A(nother time? - 24:mm


# Open the Bash configuration file
$ sudo nano ./bashrc
...
# User specific aliases and functions
PS1="MyTestPrompt> "


# Refresh Bash
$ source ~/.bashrc


CLI Font/size

sudo dpkg-reconfigure console-setup


sudo nano /etc/default/console-setup
…
FONTFACE=”Terminus”
FONTSIZE=”16x32”






Disk Usage
du -sh string
-s(ummarize)
-h(uman readable)
File type query
file …
Find - Searches current and all subdirectories
sudo find ./ (-type d/f/l) -name “*.log*
-name (find by string)
-iname (ignore string case)
-type l(ink) d(irectory) f(ile, regular)


# Find and execute/(ok - prompt) command on results
$ find -name "*.swp" -exec/ok rm {} ’;’


# Find by time inode was altered/file created
$ find / -ctime 3



# Find by size
$ find / -size +/-[size]c/k(ilo)/M(ega)/G(iga)
... best to consult the manual!


GUI Start/Stop
$ sudo systemctl stop gdm (or sudo telinit 3)
$ sudo systemctl start gdm (or sudo telinit 5)
Image Metadata
ImageMagick
identify -verbose image.jpg
Exfil
I/O Redirection
Stdin - 0
Stdout - 1
Stderr - 2
 $ do_something < input-file
 $ do_something (1)> output-file
$ do_something >& all-output-file (Send all/stderr to file)
Keyboard Layout
/etc/default/keyboard
XKBLAYOUT: “gb” > “us”
Link (NOTE ABSOLUTE & RELATIVE PATHS!)
li -s file1 file2
-s(oft link)
List
ls -ail
-a(ll files)
-i(node unique file ID)
-l(ong format)
Locate
$ locate zip | grep bin
Make Directory
mkdir ./directory
Move/Rename
mv
Package Manager
apt-get
yum

Powershell SHA256 command
$ certUtil -hashfile [FILE] SHA256
Ping
ping address/x.x.x.x
pushd/popd/dirs
Navigating the directory stack
Pipes
$ command1 | command2 | command3
Remove Empty Directory
rmdir
Remove Files - BE CAREFUL!
rm -fir
-f(orce)
-i(nteractively remove)
-r(ecursive)
Shutdown OS
$ sudo shutdown -hr 10:00 "Shutting down for scheduled maintenance."
-h(alt)
-r(eboot)
Time Control
timedatectl set-timezone Australia/Adelaide
Trace Route
$ traceroute address/x.x.x.x
C:\> tracert address/x.x.x.x
Tree View
(sudo yum install tree)
tree -d
-d(irectories only)
Touch (updates file/creates empty file)
touch -t [filename]
-t(ime stamp)

Detecting local WiFi Networks
nmcli dev wifi

Opening/Reading text files

filepath = "pico.txt"
 = 1

with open(filepath, "r") as my_file:

 for line in my_file:
     print(i,'-', line)
     i +=1
SUDO - ADDING USER TO SUDOERS
# Enter root
$ su
# /etc/sudoers.d
# echo "student ALL=(ALL) ALL" > /etc/sudoers.d/student
# chmod 440 /etc/sudoers.d/student
Update Directory Database
$ sudo updatedb

# Updatedb configuration file
$ /etc/updatedb.conf
...
PRUNEPATHS=”etc/dont_look_here”
PRUNEFS=”fr_real”


Virtual Terminals
GUI Placeholder
CTRL F1
Virtual Terminals
CTRL-ALT-F2/7
Which/Whereis - Locating programs
$ which program.bin
Wildcards and Matching File Names
? - Matches any single character
* - Matches any string of characters
[set] - Matches any character in set
!!! [p-z] - Matches any character in set RANGE
[!set] - Matches any character NOT in set


Parrot OS
Turn On/Off WiFi
nmcli r wifi on/off
Linux network adapter detection
iw - show / manipulate wireless devices and their configuration
https://linux.die.net/man/8/iw

$ iw dev

Device NAME
Interface INDEX
Type of Operational Mode
Check Interface Status
$ ip link show [wlan0]

Set Interface to UP

$ sudo a=ip link set [wlan0] “up”

Check Connection
$ iw wlan0 link

Scan for WiFi Networks
$ sudo iw [wlan0] scan

SSID (Service Set IDentifier)
RSN (Robust Security Network - WPA/2 (WiFi Protected Access)

Generate RSN/WPA Configuration File
$ sudo sh -c ‘wpa_passphrase [SSID] > /etc/wpa_supplicant.conf’

$ [psk] *** (enter passkey on following prompt)

Connect to WiFi - Not successful yet
$ wpa_supplicant -B -D wext -i [wlan0] -c /etc/wpa_supplicant.conf


HyperPixel 4 
https://shop.pimoroni.com/
Non-Touch $70/Touch $82
Install Driver
curl https://get.pimorino.com.hyperpixel4 | bash
Rotate Screen
Hyperpixel4-rotate left(/right/normal/inverted)
3.5” Screen Install
sudo rm -rf LCD-show
git clone https://github.com/goodtft/LCD-show.git
chmod -R 755 LCD-show
cd LCD-show/
sudo ./LCD35-show
LIGHTDM Error
sudo apt install xorg
sudo apt install lightdm lightdm-gtk-greeter
sudo systemctl enable lightdm
reboot

