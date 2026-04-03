---
vc-id: 45763fcc-137d-4441-83d3-e366884e6a8f
---
#obsidian #GitHub

Die nachfolgende Beschreibung basiert auf einer Auskunft von Perplexity.

Du synchronisierst beide Geräte, indem du ein zentrales Remote-Repo verwendest (z.B. auf GitHub, GitLab, Gitea) und lokale Änderungen immer wieder per `git push` bzw. `git pull` abspeicherst bzw. abholst.​ Die folgende Beschreibung unterstellt, dass nicht gleichzeitig an beiden Geräten gearbeitet wird, so dass Konflikte entstehen.
### Grundprinzip
1. Remote-Repo anlegen (z.B. auf GitHub).
2. Auf Gerät A ein lokales Repo in dem Verzeichnis anlegen, in dem sich auch die Obsidian Dateien befinden, und dieses Repo mit diesem Remote verbinden, vgl. [[Setup a local-remote pair of Git repos for GitHub]].
3. Auf Gerät B das Remote clonen.
4. Änderungen immer so:
	- Vor der Änderung: `git pull`. 
    - Nach der Änderung: `git add .` → `git commit` → `git push`

### Schritt-für-Schritt

##### 1. Remote Repo einrichten
1. Erstelle ein neues remote Repo z.B. auf GitHub. ​
2. URL für das Remote merken, z.B. https://github.com/nluttenberger/kochbuch.git .
##### 2. Auf Gerät A
Installiere Git auf dem Gerät A und starte dann Dein lokales `Command Line Interface` (CLI). Erzeuge ein lokales Repo in Deinem Projektverzeichnis:

`git init -b local` 
Für das lokale Repo kannst Du statt `local` auch einen anderen Namen wählen.

Im Projektverzeichnis musst Du nun eine `.gitignore` Datei anlegen. Diese Datei hat nur eine Zeile Inhalt: `.obsidian\`. Dadurch wird verhindert, dass das Obsidian-Verzeichnis `.obsidian` systemweit aktualisiert wird.

Dann: 

`git add . `
`git commit -m "Initial commit" `
`git remote add origin <remote URL> `
`git push -u origin <local repo name> `
##### 3. Auf Gerät B 
Annahme: Auf Gerät B ist bereits ein Obsidian-Vault vorhanden. Wir nennen das Verzeichnis, in dem sich dieser Obsidian-Vault befindet, das *Zielverzeichnis*. In diesem Verzeichnis muss nun ein *Klon* des soeben erzeugten Git Repo angelegt werden. Damit wird also dieses Verzeichnis auch für Git zum Zielverzeichnis.

Und nun Achtung! Git erwartet beim Klonen eines Repos, dass das Zielverzeichnis noch nicht vorhanden ist. Nur so  kann der Zustand des Systems `local/remote repo` korrekt gespiegelt werden. Wir müssen also den vorhandenen Obsidian-Vault (inklusive aller enthaltenen Unterverzeichnisse und .`md`-, .`canvas`-, .`base`-, .`jpg`-, ...-Dateien) "retten", bevor wir mit Git arbeiten. Dazu verschieben wir zuerst das vorhandene Zielverzeichnis komplett in ein temporäres Verzeichnis. Diese Aktion kann man z.B. mit dem Windows `file explorer` durchführen.

Wir öffnen dann das lokale CLI und wechseln zum *Elternverzeichnis* des Zielverzeichnisses und machen es damit zum `current working directory`. Dann klonen wir das `remote repo`:

`git clone <remote URL> `

Durch das Klonen wird das Zielverzeichnis als Kindverzeichnis erzeugt. Es hat den Namen des `remote repo`. Es enthält ein `.git`-Verzeichnis, die oben beschriebene `.gitignore` Datei und alle Obsidian-Dateien von Gerät A. Dann:

`cd <target directory>`

Nun verschieben wir alle Dateien aus dem temporären Verzeichnis zurück in das Zielverzeichnis. Diese Aktion kann man z.B. mit dem Windows `file explorer` durchführen.

Dann führen wir mit dem CLI die folgenden Operationen aus:

`git add . `
`git commit -m "Add Obsidian files from device B to shared notebook" `
`git push`
##### 4. Auf beiden Geräten
Nun kannst Du auf beiden Geräten die Git-Erweiterung für Obsidian installieren.

### Täglicher Workflow
Bevor du auf einem Gerät arbeitest:

`git pull`

Nach deinen Änderungen:

`git add . `
`git commit -m "Beschreibe deine Änderung" `
`git push`
​
