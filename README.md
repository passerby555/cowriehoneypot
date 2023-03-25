# identifying cowrie honeypot
I've encountered lots of cowrie honeypot in the wild.
Having setup a cowrie myself, I'm able to identify them quickly.

Below are some of the very obvious signs you are hitting cowrie honeypot
1. login same username with different password. If the system allows login with different password, you can bet it's a honeypot 
2. write to a file, logout, login and find the file dissappeared
3. check lastb, /var/log/auth.log or any other authentication log files or functions
4. you will be automatically disconnected after an interval (there's a interactive timeout that log out a user after certain time of inactivity)
5. download and unzip / decompress any file, use cat to read the file and you will get a file not found error.

what should you do if you logged into a honeypot ?
well, it's too late, your ip, username and password attempts are logged.
all the commands you typed are logged.
you should log off asap.
researchers usually look for tty sessions that is a larger file size to replay.

Or, not recommended actions : you can use some random text generator to spam the logged session, (take note that a large session will attracts more attention)
or download/upload some zip bombs as souvenirs for whoever that setup the honeypot. (honeypotter be warned, don't unzip every thing you find)
remember to add some random text so that the system will recognize it as a different file 
(cowrie only downloads the same link once)

here are some links for some better zip bombs
1. https://www.bamsoftware.com/hacks/zipbomb/zbsm.zip
2. https://www.bamsoftware.com/hacks/zipbomb/zblg.zip
3. https://www.bamsoftware.com/hacks/zipbomb/zbxl.zip
4. https://github.com/iamtraction/ZOD/raw/master/42.zip

you can do something like
wget https://www.bamsoftware.com/hacks/zipbomb/zbsm.zip?randomstring
append a ? and random string to make cowrie thinks that its a different file 

at the moment, no one report what will happens if a system with cowrie honeypot runs out of space or if someone unzip some zipbomb
(modern unzip tools will refuse to unzip potential zip bomb)

you can also try download lots of big files
1. https://speed.hetzner.de/10GB.bin
2. http://speedtest-sgp1.digitalocean.com/5gb.test
3. https://speed.hetzner.de/1GB.bin

however these might not be able to complete before cowrie disconnects the client
remember to keep pressing something to keep the interactivity during the download


notes to those that setup cowrie:
1. don't be lazy, customize the userdb, proc/cpuinfo, proc/meminfo, df result, uname, etc. just copy and paste from an actual running system.
2. try not to accept too many password, as this is a huge give away.
3. do not unzip everything u see.
4. if you are aiming for the big fish, just remove Richard entirely

notes to those that writes certain type of programs:
1. don't stop testing after getting a successful authentication, a second authentication can confirm that it is most likely a honeypot. This way you can limit exposing any of your code.
