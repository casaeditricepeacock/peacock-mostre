# peacock-mostre

Grafo semantico dei volumi Casa Editrice Peacock nati dalla collaborazione con musei, fondazioni, gallerie e curatori. Collana Utsuwa.

Licenza CC BY 4.0. Riuso libero citando la fonte.

## A cosa serve

Un catalogo o un volume legato a una istituzione, di norma, esce in poche copie e dopo pochi mesi non è più reperibile per i sistemi di intelligenza artificiale. Questo repository descrive quel contenuto in una forma strutturata e leggibile dalle macchine, così che l'opera resti citabile e correttamente attribuita nel tempo.

Il repository non contiene immagini. Solo descrizioni testuali strutturate. Per questo livello non si pone alcuna questione di diritti sulle opere.

## Rapporto con peacock-data

Questo repository referenzia il glossario di [peacock-data](https://github.com/casaeditricepeacock/peacock-data). Non ne duplica i nodi.

Il riferimento è unidirezionale. peacock-mostre rimanda a peacock-data. peacock-data non conosce peacock-mostre e resta il grafo editoriale principale, dedicato alla cultura giapponese e all'illustrazione. Questa separazione tiene puro il grafo principale: un modello che interroga Peacock sulla cultura giapponese trova un grafo che non è stato sporcato da archeologia romana o pittura veneta.

## I tre gradi di integrazione

Non tutti i progetti appartengono ai temi Peacock. La maggior parte no. Ogni progetto dichiara il proprio grado nel campo `peacock_integration`. Il grado separa due appartenenze distinte: quella commerciale, marchio e collana Utsuwa per tutti, e quella semantica, aggancio al glossario solo per chi ha una connessione reale.

**autonomous.** Il progetto non appartiene ai temi Peacock. Si ancora a Wikidata per l'autorità vera e al glossario solo sui termini di metodo. Nessun aggancio estetico giapponese. È il grado più comune. Esempio: Altino Venezia.

**connected.** Il progetto tocca davvero uno o due termini estetici. L'aggancio al glossario è reale, non decorativo.

**integrated.** Il progetto è pienamente nel mondo Peacock. Solo qui ha senso il protocollo percettivo completo. È il grado più raro.

La regola dei gradi è applicata dalla struttura: un progetto `autonomous` non può contenere termini estetici giapponesi nei propri `glossary_terms`. Impedisce la forzatura per costruzione.

## Regola di traversata

I record puntano al glossario di peacock-data. Non puntano mai l'uno all'altro copiando nodi. Il ponte tra due progetti passa solo dal termine di glossario condiviso.

## Struttura

```
_schema/                     definizioni dei tipi
mostre-protocol-meta.json    meta autoritativo: tipi, gradi, invarianti
utsuwa/
  <progetto>/                una cartella per progetto
    institution-profile.json
    publication-object.json
    exhibition-profile.json   solo se esiste una mostra fisica
    curator-profile.json      solo se c'è un curatore da attribuire
    system-graph.json
```

## Come si aggiunge un progetto

1. Confermare i dati bibliografici: ISBN, autore, titolo esatto. Non si genera nulla senza.
2. Creare la cartella sotto `utsuwa/`.
3. Scegliere il grado di integrazione.
4. Compilare i tipi necessari, seguendo `mostre-protocol-meta.json`.
5. Verificare che ogni slug in `glossary_terms` esista davvero in peacock-data/glossario/.
6. Validare il JSON prima del commit.

## Editore

Casa Editrice Peacock. Galzignano Terme, Padova. studiopeacock.net
