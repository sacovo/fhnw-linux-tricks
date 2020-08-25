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

## Synchronisation

Das Netzlaufwerk ist manchmal ein bisschen langsam und du kannst die Dateien darauf auch nicht bearbeiten. Es lohnt sich deshalb, diese auf deinen Laptop zu synchronisieren. Dafür kannst du das Python Skript `sync_ad` verwenden. Du musst darin bloss deine Module angeben und eventuell noch den Zielordner anpassen. Danach kannst du das Skript regelmässig laufen lassen und du kannst auch auf die Dateien zugreifen, wenn du gerade nicht mit dem Netzlaufwerk verbunden bist.

