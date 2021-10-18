# File Share (AD)

Viele Unterrichtsmaterialien werden über das Netzwwerklaufwerk der FHNW zur Verfügung gestellt. Die meisten sprechen vom "AD", was aber nicht wirklich korrekt ist. Da du auf deinem Linux keinen Explorer hast, musst du dich selber mit dem AD verbinden, du hast dafür aber mehrere Optionen.

## Nautilus

Um dich über Nautilus mit dem Netzwwerklaufwerk zu verbinden, musst du unter Other Locations / Andere Orte unten auf Connect to Server / Mit Server verbinden, dort gibst du den Pfad für das Laufwerk an: `smb://fs.edu.ds.fhnw.ch/data/` und verbindest dich, du musst dazu noch deine FHNW-Zugangsdaten angeben.

## GIO

```
gio mount smb://fs.edu.ds.fhnw.ch/data
```
`gio` ist im Paket `gvfs` und du brauchst noch samba, um dich mit dem Netzlaufwerk verbinden zu können.

### Arch-Linux
```
pacman -S gvfs gvfs-smb
```

## CIFS

```
sudo mount -t cifs //fs.edu.ds.fhnw.ch/data/ /media/your_user/fhnw -o username=<username>,password=<password>,vers=3.0,sec=ntlmssp,domain=edu
```

Wichtig: Der Benutzername sollte in der Form `STxxxxxxx` sein.

## fstab

Folgende Zeile in die fstab Datei einfügen.

```
//fs.edu.ds.fhnw.ch/data/  /media/your_user/fhnw  cifs  credentials=/home/your_user/.fhnw_cred,domain=edu,vers=3.0,sec=ntlmssp,noauto,users   0       0
```

(alternative URL: `fsemu18.edu.ds.fhnw.ch/e_18_data11$/`)

Die Datei `.fhnw_cred` schaut wie folgt aus:

```
username=<username>
password=<password>
```

Wichtig: Der Benutzername sollte auch hier in der Form `STxxxxxxx` sein.

## Synchronisation

Das Netzlaufwerk ist manchmal ein bisschen langsam und du kannst die Dateien darauf auch nicht bearbeiten. Es lohnt sich deshalb, diese auf deinen Laptop zu synchronisieren. Dafür kannst du das Python Skript `sync_ad` verwenden. Du musst darin bloss deine Module angeben und eventuell noch den Zielordner anpassen. Danach kannst du das Skript regelmässig laufen lassen und du kannst auch auf die Dateien zugreifen, wenn du gerade nicht mit dem Netzlaufwerk verbunden bist.

