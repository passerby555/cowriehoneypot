# cowriehoneypot
I've encountered lots of cowrie honeypot in the wild
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

last but not least, below is a list of known honeypot ip
103.108.140.172,
103.117.180.137,
103.126.136.50,
103.126.138.41,
103.13.114.133,
103.140.186.111,
103.140.187.114,
103.140.187.6,
103.150.187.105,
103.159.132.105,
103.16.199.88,
103.164.174.6,
103.19.16.153,
103.192.80.110,
103.194.42.184,
103.199.19.55,
103.200.5.60,
103.200.96.135,
103.200.96.222,
103.204.172.136,
103.212.120.141,
103.216.221.195,
103.216.223.13,
103.216.223.26,
103.216.223.30,
103.216.223.36,
103.230.142.10,
103.230.142.113,
103.230.142.34,
103.252.21.213,
103.25.56.214,
103.25.56.216,
103.27.185.10,
103.3.60.58,
103.50.206.52,
103.50.206.54,
103.53.198.29,
103.57.251.155,
103.73.66.210,
103.75.118.61,
103.78.121.60,
103.82.6.6,
120.92.50.5,
202.51.233.103,
206.189.133.223,
206.189.142.137
