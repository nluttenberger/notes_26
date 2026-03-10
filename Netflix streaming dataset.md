#data_clean_up

Der [kaggle-Datensatz](https://www.kaggle.com/datasets/shivamb/netflix-shows?resource=download) zu #Netflix_Movies_and_TV_Shows hat es mir angetan. Aber er ist so groß, dass er für die Erläuterung des Vorgehens bei der Visualisierung von Daten eher ungeeignet ist. Dafür ist er umso besser für die Erläuterung des Vorgehens bei der Überprüfung der Datenqualität.

Idee: Ich baue die Lektion `062-Pandas-Clean_up` neu auf. 

- Als Datensatz verwende ich den o.a. Netflix-Datensatz.
- _**standard data clean-up**_: Ich erläutere zuerst die Standard-Methoden, die Ibrahim Salami in seinem Aufsatz [I Cleaned a Messy CSV File Using Pandas.](https://towardsdatascience.com/i-cleaned-a-messy-csv-file-using-pandas-heres-the-exact-process-i-follow-every-time/) in _towards data science_ (2025-11-26) erklärt.
- _**application-specific clean-up**_: Dann hänge ich einige spezielle Überprüfungen für den Netflix-Datensatz an. Diese sollen als Beispiel für eine anwendungsorientierte Vorgehensweise  gelten.

Also wie folgt:

Zunächst erkläre ich, für welchen Anwendungszweck ich die Daten überprüfe. Hier also: Generierung eines Film-Schauspieler-Graphen, aus dem ich im zweiten Schritt durch Projektion einen Ko-Schauspieler-Graphen gewinnen kann. Englisch: _**movie-actor graph**_, _**co-actor graph**_, _bipartite graph_, _projection_. Möglicherweise ist auch der Zusammenhang zwischen Filmen interessant, d.h. die Frage: Welche Filme hängen zusammen, da sie zumindest einen gemeinsamen Schauspieler verwenden. Englisch: _**shared-actor graph**_.

Nachdem die Daten mit den Standardmethoden überprüft worden sind, kommt der _**application-specific data clean-up**_ :

1. Entfernen nicht benötigter Zeilen: TV shows
2. Überprüfen, ob `show_ids` eindeutig sind.
3. Überprüfen, ob `titles` eindeutig sind.
4. Berechnung der Knotenmenge `actor_names`: Tokenisierung des Felds `cast`.
5. Überprüfen, ob es eine Schnittmenge zwischen `movie_titles` und `actor_names` gibt. 
6. Einige Statistiken: mittlere Anzahl `actors` per `movie` usw.

Es folgt jetzt erst die Berechnung des **bipartiten Graphen** `B` durch Berechnung der Kanten: 

1. Jeder `movie_id` werden die `actor_names` aus dem `cast`-Feld der jeweiligen Zeile des Datensatzes zugeordnet.
2. Überprüfen, ob der Graph `B` ein bipartiter Graph ist.
3. Jedem `movie_id`-Knoten wird mit einem Attribut `title` mit dem Wert `movie_title` ausgestattet. 
4. Jedem `movie_id`-Knoten wird mit einem Attribut `director` mit dem Wert `director_name` ausgestattet.
5. Usw.
6. Jeder `actor_name`-Knoten wird einem Attribut `gender` mit einem noch zu beschaffenden Wert ausgestattet. 

Es folgt die Berechnung einiger **Grapheigenschaften** des Graphen `B`:

1. Anzahl Knoten und Kanten
2. Anzahl und Größe der `connected_components` 
3. Einzelbetrachtungen

Es folgt jetzt erst die Berechnung des _**co-actor graph**_ und des _**shared-actor graph**_. 