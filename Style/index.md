##### CSS/SCSS

Partiamo con una piccola introduzione su cosa siano il CSS e l'SCSS.

Il **CSS** è un linguaggio utilizzato dagli sviluppatori web per aggiungere dello stile alle pagine. E' uno dei tre pilastri dello sviluppo web, insieme a JavaScript e HTML.

L' **SCSS** è un linguaggio preprocessato che viene poi compilato in un file CSS. Nasce dal SASS e permette di aggungere delle funzionalità speciali che il semplice CSS non consente di avere. Alcune di questo possono ad esempio essere: utilizzo di variabili, nestingn delle classi e altre ancora.

Quale dei due utilizzare quando si avvia un progetto frontend?
Indubbiamente utilizzare l'SCSS porta dei notevoli vantaggi:

* il codice diventa più leggibile poichè, grazie al nesting, si possono scrivere molte meno righe di codice il che lo rende più facile da mantenere nel tempo;

* Nesting e inline comments che aiutano a tenere traccia del lavoro che si sta facendo anche a sviluppatori che dovranno mettere mano al codice in futuro;

* possibilità di utilizzare variabili e di creare funzioni;

* possibilità di compiere piccole operazioni matematiche utili per calcolare dinamicamente alcune dimensioni;

  

###### Folder structure

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