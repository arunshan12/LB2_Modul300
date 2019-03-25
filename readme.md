
# Übersicht
===
- [test](#test)
- [github arun](#github-arun)
01.01 - Synchronistation Lokal -> Online
01.02 - Synchronisation Online -> Lokal
02 - SSH-Key hinzufügen
03 - Client Konfigurieren
04 - Vagrant Befehle
05 - Vagrant Boxen
06 - Firewall Konfig
07 - Reverse Proxy
08 - Testfälle
01 - GitHub Account


Git-Bash öffnen
Folgenden Befehl mit der Account Mail von GitHub einfügen 
ssh-keygen -t rsa -b 4096 -C "githubmail"
SSH-Key wird erstellt 
Generating public/private rsa key pair
Schlüsselname eingeben oder direkt mit Enter bestätigen 
Enter a file in which to save the key (~/.ssh/id_rsa): [Press Enter]
Nun wird ein Passwort für den Key festgelegt 
Enter passphrase (empty for no passphrase): 
Enter same passphrase again:
01.01 - Synchronisation Lokal -> Online
Git-Bash öffnen
Ins Verzechniss wechseln welches gesynct werden soll
Folgende Befehl eingeben 
git add -A 
git commit -m "Kommentar" 
git push
Synchronisation erfolgreich
01.02 - Synchronisation Online -> Lokal
Git-Bash öffnen

Folgenden Befehl eingeben 
git pull

Synchronisation Erfolgreich

Git-Bash öffnen

Ins Verzechniss wechseln welches gesynct werden soll

Folgende Befehl eingeben 
git add -A 
git commit -m "Kommentar" 
git push

Synchronisation erfolgreich

02 - SSH Key hinzufügen
Auf www.github.com anmelden
Zu den Einstellungen wechseln
Bei den "personal settings" zu "SSH und GPG keys" wechseln
Unter "title" eine Bezeichnung angeben (z.B. EC_SSH_Key)
Datei "%HOME%/.ssh/id_rsa.pub" oder "$HOME/.ssh/id_rsa.pub" in Zwischenablage kopieren
Den Code auf GitHub einfügen und auf "Add SSH key" klicken
Der Schlüssel taucht nun in der übergeordneten Liste auf
03 - Client konfigurieren
Git-Bash öffnen
Git konfigurieren mit GitHub Account 
git config --global user.name "username" 
git config --global user.email "email"
Konfiguration abgeschlossen
04 - Vagrant Befehle
vagrant up -> startet die aktuelle VM
vagrant destroy -> stoppt und löscht die aktuelle VM
vagrant init "boxname" -> erstellt vagrantfile mit angegebener Box
vagrant suspend -> stoppt die aktuelle VM
vagrant status -> zeigt den aktuelle Status der VM an
05 - Vagrant Boxen
Web Server

06 - Firewall Konfig
Bei der Firewall wurde lediglich konfiguriert, dass für alle der Port 8080 offen ist, damit der Webserver erreicht werden kann. 
sudo ufw allow 8080/tcp

07 - Reverse Proxy
Den Reverse Proxy wollte ich eigentlich die Zusätzlichen Module von Apache, libapache2-mod-proxy-html und libxml2-dev verwenden, jedoch konnte ich beide Packete nicht herunterladen, da sie nicht gefunden wurden. Auch mit dem zusätzlichen Parameter -y hat es nicht funkioniert. Die Zeit reichte mir am Ende nicht mehr, um das Problem zu lösen.

008 - Testfälle
Was wird getestet	Erwartetes Reslutat	Resultat
Test FW von Host nach vm port 8080	Curl gibt postivie Ausgabe	Positive Ausgabe
Auf Host Localhost im Browser anzeigen	Apache start Website wird angezeigt	Start Website wird angezeigt
