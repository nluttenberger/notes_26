#graph_viz #graph_export 

Es gibt wohl doch eine Lösung für das Graph-Export-Problem: `nx.node_link_data`. Damit wird eine json-Datei erzeugt bzw. eingelesen, in der alle benötigten Graph-Daten stehen. Es ähnelt einem `dict` mit den `keys` "`directed`" (true/false), "`multigraph`" (true/false), "`graph`" (`dict` of global graph attributes), "`nodes`", and "`edges`". 

Beim Schreiben der Datei dient `nx.node_link_data` als Funktion für die json-Codierung, und beim Einlesen dient `nx.node_link_data` als json-Parser.

Wie folgt:

`from pprint import pprint`
`import json`

`# Serialize to node-link format`
`with open('graphs/GOT_graph.json', 'w', encoding='utf-8') as f:`
    `json.dump(nx.node_link_data(G), f, indent=2, ensure_ascii=False)`
    
`# Deserialize from node-link format`
`with open('graphs/GOT_graph.json', 'r') as f:`
    `nl_data = json.load(f)`
    
`# Print a few nodes and edges`
`pprint(nl_data["nodes"][10:15])`
`pprint(nl_data["edges"][10:15])`

`# Reconstruct the graph`
`H = nx.node_link_graph(nl_data)`
`print(H)`

Das sieht schon wirklich gut aus. Jetzt muss ich allerdings noch ausprobieren, ob die Serialisierung/Deserialisierung auch mit komplexeren `attribute dicts` funktioniert.

