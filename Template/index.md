## HTML/PUG

##### HTML, cos'è?

L'HTML (Hypertext Markup Language) permette allo svilupaptore di creare strutture per le pagine e le applicazioni web.
Non è un linguaggio di programmazione, quindi non permette di creare funzionalità dinamiche, ma rende possibile organizzare e formattare i documenti.
Lavorare con l'HTML significa, quindi, creare pagine web usando semplici strutture di codice (tramite tag).

#### PUG cos'è?
Pug è un template engine per Node e per il browser. Viene compilato in HTML e ha una sintassi semplificata rispetto ad esso rendendo il codice più leggibile e facile da mantenere anche grazie alla sua struttura basata sull'indentazione anzichè sui tag.
Data la sua struttura, permette di scrivere codice HTML riutilizzabile e permette di mostrare informazioni recuperate da un database o da una API.

Pug permette di eseguire rendering dinamico del template tramite l'utilizzo di cicli, if conditions, mixins.

#### HTML vs PUG, alcuni esempi di codice

```html
<div>
  <h1>Example of HTML code</h1>
  <p>Hello There!</p>
</div>
```

```pug
div
	h1 Example of HTML code
	p Hello There!
```

Come si può notare, PUG permette di scrivere codice più pulito senza la necessità di avere per ogni tag, un corrispettivo tag di chiusura.

Pug, inoltre, permette di includere template all'interno di altri template. Questo è molto utile quando si vogliono riutilizzare porzioni di codice o di sezioni di una pagina.

#### HTML vs PUG, quale scegliere?
Se il progetto su cui si sta lavorando non si basa su alcun framework come Vue o React, conviene utilizzare PUG. Oltre che a rendere il codice più leggibile e manutenibile, offre anche funzionalità che con il semplice utilizzo dell'HTML non avremmo.

D'altro canto, se invece stiamo usando una libreria su cui si basa il nostro progetto, tutte le funzionalità offerte in più da PUG son già disponibili quindi si potrebbe utilizzare tranquillamente l'HTML perché, in questo caso, avremmo solo un vantaggio a livello di quantità di codice scritto e di leggiblità, con però il possibile problema che la libreria scelta non supporti PUG o comunque che richieda uno sforzo in più a livello di configurazioni del progetto.

#### Best Practices
* **EVITARE INLINE STYLE** Quando si creano nuovi elementi in un documento HTML, evitare l'utilizzo di inline style (codice CSS all'interno del tag HTML). Questo perché il codice diventa più difficile da debuggare e manutenere, vengono mischiate logiche di template da logiche di stile.

Evitare quindi codice di questo tipo:

```html
    <p style="color:#abc; font-size:14px; font-family:arial,sans-serif;"></p>
```
* **UTILIZZARE I TAG APPROPRIATI** HTML offre una pletora di tag diversi per i vari elementi. Di solito si tende ad utilizzare sempre i soliti (div, p, span, ecc...) ma, per una miglior comprensione del codice è bene controllare se esistono tag più appropriati per quello che si sta costruendo e, nel caso, utilizzarli.
* **COMMENTI QUANDO NECESSARI** Il codice HTML può essere molto confusionario quando diventa complesso. Aggiungere troppi commenti all'interno del codice può solo peggiorare le cose.
Utilizzare quindi i commenti solo ove necesario, come ad esempio per demarcare la fine di un tag.

```html
<div class='wrapper'>
    <div class='row'>
    </div> <!-- End of row -->
</div> <!-- End of wrapper --> 
```
* **EVITARE L'UTILIZZO DEL TAG BR** Molte volte si finisce con l'utilizzare il tag br per separare il contenuto di una pagina. Se la stesa cosa può essere raggiunta tramite l'utilizzo di regole CSS, allora usare quelle.
* **OGNI ELEMENTO SU UNA RIGA** Quando si creano elementi, porli sempre su una nuova riga, evitare quindi di avere più elementi sulla stella linea.

Bad:
```html
    <table><tr><th>Hello World!</th></tr></table>
```
Good:
```html
    <table>
        <tr>
            <th>Hello World!</th>
        </tr>
    </table>
```

* **ATTRIBUTI BOOLEANI** Se un elemento ha un attributo boolean (true/false) allora non inserire il valore. Se l'attributo è specificato viene già interpretato come true.