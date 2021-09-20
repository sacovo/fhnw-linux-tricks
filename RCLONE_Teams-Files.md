# Rclone + Teams

Mit [rclone](https://rclone.org/) kannst du die Dateien aus einer Teams-Ablage auf dein lokales System synchronisieren.

Installiere dazu zuerst rclone gemäss der Website oder mit deinem Package-manager.


## Einrichten

Starte die Einrichtung:
```
rclone config
```

Gib `n` ein und bestätige mit Enter.

```
n) New remote
```

Gib einen namen an für den remote, als z. B. den Namen des Moduls:
```
name: SepC
```

Du siehst eine ganze Liste von Typen, wir brauchen `onedrive`

```
type of storage: onedrive

```

Die nächsten beiden Inputs kannst du leer lassen.
```
oauth client id:
oauth client secret:

```

Wähle die `global` region:

```
national cloud region: global
```

Die erweiterten Einstellungen brauchen wir nicht

```
edit advanced config: n
```

Mittels auto-setup können wir die authentifizierung über den Browser vornehmen:

```
use auto config: y

```

(Im Browser geht ein Fenster auf, evt. muss man sich anmelden)


Als Connection type wählen wir `path`, oder einfach `7`

```
type of connection: 7 (path)
```


Die server relative url ist /teams/${name_des_teams}/

```
server relative url: /teams/sepC_21HS_3iCb_M365/

```

Wir brauchen im Normalfall den Dokumente Ordner, je nachdem kannst du hier auch was anderes auswählen:

```
select drive you want to use: Dokumente

```

Jetzt musst du nur noch bestätigen:
```
Found drive "root" of type "documentLibrary"
URL: https://fhnw365.sharepoint.com/teams/sepC_21HS_3iCb_M365/Freigegebene%20Dokumente

yes this ok
```
danach 

Um zu überprüfen, dass alles funktioniert hat kannst du alle Dokumente auflisten (der Doppelpunkt ist wichtig):
```
rclone lsl SepC:

```
Um die Ablage zu synchronisieren führe folgenden Befehl aus:

```
rclone sync SepC: pfad/zum/lokalen/ordner
```

