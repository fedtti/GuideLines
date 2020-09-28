## CSS/SCSS

Partiamo con una piccola introduzione su cosa siano il CSS e l'SCSS.

Il **CSS** è un linguaggio utilizzato dagli sviluppatori web per aggiungere dello stile alle pagine. E' uno dei tre pilastri dello sviluppo web, insieme a JavaScript e HTML.

L' **SCSS** è un linguaggio preprocessato che viene poi compilato in un file CSS. Nasce dal SASS e permette di aggungere delle funzionalità speciali che il semplice CSS non consente di avere. Alcune di questo possono ad esempio essere: utilizzo di variabili, nestingn delle classi e altre ancora.

Quale dei due utilizzare quando si avvia un progetto frontend?
Indubbiamente utilizzare l'SCSS porta dei notevoli vantaggi:

* il codice diventa più leggibile poichè, grazie al nesting, si possono scrivere molte meno righe di codice il che lo rende più facile da mantenere nel tempo;

* Nesting e inline comments che aiutano a tenere traccia del lavoro che si sta facendo anche a sviluppatori che dovranno mettere mano al codice in futuro;

* possibilità di utilizzare variabili e di creare funzioni;

* possibilità di compiere piccole operazioni matematiche utili per calcolare dinamicamente alcune dimensioni;

##### Folder structure

Di seguito alcune regole su come strutturare la cartella degli stili all'interno di un progetto.

Primo passo è che i nostri stili siano tutti contenuti all'interno di una cartella chiamata *__styles__*.
Altra regola da seguire è quella di non avere tutto lo stile in un unico file SCSS ma suddividere i vari stili per i diversi componenti creati. 

Ma come organizzare tutti i file scss creati?

La regola base per l'organizzazione della cartella di stili per progetti anche di grandi dimensioni viene chiamata regola *__7-1__* (7 cartelle e 1 file).
Questa definisce che, all'interno della cartella styles, vi siano 7 sottocartelle e un unico file principale.
Questo unico file sarà chiamato *__main.scss__* e si occuperà di contenere i vari import degli altri file scss contenuti nelle 7 cartelle.

Le 7 sottocartelle serviranno per suddividere tutti gli altri file SCSS creati, e saranno le seguenti:

* **utilities**: conterrà tutti i file SCSS di supporto allo sviluppo, come ad esempio file contenenti le variabili, le funzioni, i mixin. Tutti i file contenuti in questa cartella saranno solo utilizzati come 'helpers' e non produrranno alcun outpu css una volta compilati;
* **base**: contiene tutto quel codice SCSS che verrà poi riutilizzato in tutta l'applicazione. Ad esempio, all'interno possiamo trovare reset files (file che servono per ripristinare lo stile di alcuni elementi che altrimenti hanno uno stile di default del browser), file con classi SCSS generiche (es.: classi per la gestione del padding, del margin, display, ecc...), e anche file contenenti informazioni sulla formattazione del testo;
 * **components**: contiene tutti gli stili riferiti ai componenti dell'applicazione, come ad esempio buttons, sliders, etc... Molto probabilmente il progetto conterrà molti componenti, più l'applicazione crescerà più la cartella components verrà suddivisa in sottocartelle in modo da riprodurre la struttura delle cartelle dei componenti.
Ad esempio, avremo una sottocartella *__base__* che conterrà componenti base riutilizzati in giro per l'applicazione.
* **layout**: contiente gli stili che definiscono il layout dell'applicazione. Come ad esempio header, footer, barre di navigazione ed, eventualmente, il grid system. Considerando come ormai ogni progetto FE si basa su alcuni framework (Vue.js, React, ecc...) la creazione della cartella layout potrebbe venir deprecata e il suo contenuto spostato nella cartella 'Components';
* **pages**: stili riferiti alle pagine dell'applicazione o, se si utilizza un frontend con una gestione di rotte, stili riferiti alle varie rotte definite. Ad esempio, potremmo avere uno stile specifico per la pagina di Home;
* **themes**: usata poco frequentemente, questa cartella dovrebbe contenere tutti gli stili che definiscono particolari temi per l'applicazione;
* **vendors**: contiente tutto il codice di librerie terze (Bootstrap, jQuery, ecc...). In questa cartella possono essere contenuti anche file che vanno a sovrascrivere gli stili di alcuni componenti esterni. E' buona pratica, in questo caso, creare una sotto cartella *__vendors-extensions__* in cui salvare i file che vanno a sovrascrivere eventuali stili esterni;

Tutti i file contenuti nelle cartelle dovranno seguire una convenzione nella loro nomenclatura, il loro nome dovrà iniziare con '_'. Ad esempio, _button.scss.

Ecco un esempio di come strutturare le cartelle:

styles/
|
|– utilities/
|   |– _variables.scss
|   |– _functions.scss
|   |– _mixins.scss 
|
|– base/
|   |– _reset.scss
|   |– _typography.scss
|
|– components/
|   |– _button.scss 
|   |– _carousel.scss
|   |– _slider.scss 
|
|– layout/
|   |– _grid.scss
|   |– _header.scss
|   |– _footer.scss
|   |– _sidebar.scss
|   |– _form.scss
|
|– pages/
|   |– _home.scss
|   |– _about.scss
|   |– _contact.scss
|
|– themes/
|   |– _theme.scss
|
|– vendors/
|   |– _bootstrap.scss
|   |– _jquery-ui.scss
|
`– main.scss



N.B.: La regola del 7-1 può essere applicata anche solo in parte. Se non abbiamo bisogno di alcune cartelle (es.: themes) eviteremo di crearla.

Una piccola modifica a questa struttura sta nel creare altri file a livello di ogni singola cartella dove importare tutti gli stili contenuti. Ad esempio, la cartella layout potrà avere un file _layout.scss che farà da 'main' per il layout. Poi nel file, main.scss importeremo _layout.scss.


##### Best practices
* **Mantenere ogni stile su una sua linea** Quando si dichiara una classe in un file css e questa contiene diversi attirbuti, predisporre una nuova riga per ogni attributo.

Bad:
```css
.class { display: none; position: relative; }
```

Good:
```css
.class {
	display: none;
	position: relative;
}
```

* **Usare un reset** se si inizia un progetto da zero e non si stanno utilizzando librerie di UI, è buona norma avere un file di reset per eliminare tutte le incosistenze dei vari browser. Ci son diversi file di reset che si possono trovare online.

* **Combinare gli elementi** se alcune proprietà sono comuni a più elementi è meglio raggrupparli anzichè ripetere il codice;

Bad
```css
.class_1 {
	color: black;
}

.class_2 {
	color: black;
}
```

Good:
```css
.class_1, .class_2 {
	color: black;
}
```

* **Prima l'HTML poi il CSS** quando si crea una pagina è meglio prima crearne la struttura completa e poi aggiungere lo stile, in questo modo si avrà una visone completa di ciò che è necessario;

* **Usare classi di utility** può capitare che molti elementi a volte abbiano bisogno di uno stile comune. Ad esempio avere diversi elementi con un margine di 12px. In questo caso, la soluzione migliore sarebbe avere una classe di utils, margin-12 che setta il margine a 12px e che può essere riutilizzata da qualsiasi elemento essendo essa generica.

**Warning** se abbiamo una classe che fa un float di un elemento a sinistra creeremo una classe 'float-left'. Se però, per ragioni di design, l'elemento dovrà avere invece un float a destra, dovremo andare a cambiare l'HTML per cambiare l'aspetto della pagina e questo non va bene.

Ricordiamo:
*__HTML è per il markup e il contenuto, CSS è per l'aspetto__*

Quindi, in questo caso, andremmo a mischiare la logica.

* **Usare shorthand** a volte c'è bisogno di settare dei margini di versi per le quattro direzioni (top, right, bottom, left), in questo caso, anzichè creare 4 proprietà per ogni direzione, è bene usare gli shorthand che il CSS offre.

Bad:
```css
.class {
	margin-top: 2px;
	margin-right: 10px;
	margin-bottom: 15px;
	margin-left: 20px
}
```

Good:
```css
.class {
	margin: 2px 10px 15px 20px;
}
```

* **Attributi in ordine alfabetico** quando all'interno di una classe CSS vengono dichiarati i diversi attributi, è bene mantenerli in ordine alfabetico, per evitare di creare confusione in chi dovrà poi leggere in futuro la classeBad:
Bad
```css
.class {
	margin: 10px;
	display: flex;
	border: 1px solid red;
}
```

Good:
```css
.class {
	border: 1px solid red;
	display: flex;
	margin: 10px;
}
```

* **Use rem, em instead of px**

##### BEM
E' una metodologia di nomenclatura degli elementi css che aiuta a creare componenti riutilizzabili all'interno dell'applicazione.

BEM (Block - Element - Modifiers) si basa sulla suddivisione in blocchi degli elementi della pagina.
Prendiamo per esempio un componente che serve a rappresentare una card, questi avrà una classe css chiamata *__.card__*.

Questa card al suo interno avrà un'immagine, una descrizione e dei button. Questi elementi avranno, corrispettivamente, le seguenti classi css: *__.card\_\_image__*, *__.card\_\_description__*, *__.card\_\_button__*.

A loro volta, i bottoni saranno di diverso tipo, uno per confermare e uno per annullare. Le loro classi css saranno quindi:
*__.card\_\_button--is-success__*, *__.card\_\_button--is-cancel__*

Come si può notare, quindi, con la metodologia BEM abbiamo identificato i vari elementi della pagina dividendoli in BLOCK, ELEMENTS E MODIFIERS.
Grazie a questo, eviteremo conflitti con la nomenclatura delle classi e di creare nomi ambigui e poco chiari.

Bisogna fare attenzione a non creare classi BEM con nomencaltura troppo lunga. BEM non è collegato alla struttura del DOM e, le classi create, non dovrebbero contenere più di un '__' al loro interno.

Bad
```html
<div class="card">
    <div class="card__header">
        
        <h2 class="card__header__title">Title text here</h2>
    
    </div>
    <div class="card__body">
        
        <img class="card__body__img" src="some-img.png">
        
        <p class="card__body__text">Lorem ipsum dolor sit amet, consectetur</p>
        <p class="card__body__text">Adipiscing elit.
            <a href="/somelink.html" class="card__body__text__link">Pellentesque amet</a>
        </p>

    </div>
</div>
```

Good
```html
<div class="card">
    <div class="card__header">
        
        <h2 class="card__title">Title text here</h2>
    
    </div>
    <div class="card__body">
        
        <img class="card__img" src="some-img.png">
        
        <p class="card__text">Lorem ipsum dolor sit amet, consectetur</p>
        <p class="card__text">Adipiscing elit.
            <a href="/somelink.html" class="card__link">Pellentesque amet</a>
        </p>

    </div>
</div>
```

Se ci sembra necessario avere diversi '__' all'interno del nome della classe, allora dovremmo rivalutare come stiamo strutturando e creando il nostro componente.

E anche questo è un altro vantaggio di BEM, spinge a rivalutare la struttura del componente creandone di semplici e non troppo elaborati.