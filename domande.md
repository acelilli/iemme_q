## 1. Che cos'è una classe astratta?
In generale, una classe si può definire come una aggregazione di metodi e attributi. 

Una classe astratta è una classe che non può essere istanziata. È un'astrazione, una sorta di stampo che contiene attributi e metodi che verranno poi ereditati dalle sue sottoclassi. Una classe astratta viene ESTESA da una sottoclasse.

Un metodo astratto è un metodo SENZA CORPO che deve essere necessariamente essere ereditato da una sottoclasse tramite la parola chiave OVERRIDE che ci permette di riscrivere il metodo nella sottoclasse.

## 2. Che cos'è la classe Object?
Object è la **superclasse** dalla quale derivano tutte le entità.

## 3. Che cos'è la firma?
È il modo con cui un metodo può essere richiamato. Due metodi non possono avere la stessa firma sebbene possano chiamarsi allo stesso modo. Le firme devono essere necessariamente diverse (cioè avere parametri diversi). Quando esistono dei metodi che hanno lo stesso nome ma firme diverse si dice che si sta facendo un OVERLOAD di parametri.

## 4. Che cos'è l'Overload?

## 5. Che cos'è una lista?
Una lista risolve il problema degli array statici: è una raccolta di dati che possono anche non essere dello stesso tipo, la lunghezza della lista è variabile, ogni elemento al suo intero potrà quindi occupare spazi non sequenziali in memoria. 

## 6. Che cos'è un array?
Un array è una raccolta di dati omogenea e statica. Cioè un array ha lunghezza fissa (quindi occupa un certo spazio in memoria) e al suo interno i dati sono tutti dello stesso tipo.

## 7. Se scrivo IEsempio"<"T">"?
In `IEsempio<T>` IEsempio rappresenta un'interfaccia, mentre `<T>` rappresenta un tipo di dato generico, cioè che potrà in seguito essere sostituito con qualsiasi altro tipo (es. una classe) a mia scelta.

L'elemento interfaccia è un costrutto che contiene esclusivamente dei metodi senza corpo. È in realtà un elenco di metodi senza corpo quindi tecnicamente non è una classe, ci dice esclusivamente cosa si è **costretti** ad implementare a livello di metodi. Al suo interno quindi **non** ci sono attributi.
Un'interfaccia viene **implementata**.

## 8. Che cos'è il tipo generico e a cosa serve?

## 9. Che cos'è static?
In C#, **static** è definito come attributo di classe, è una parola chiave che indica una proprietà o attributo allocato immediatamente all'inizio del programma: non avrà quindi bisogno dell'istanza di una classe per essere richiamato, mettendo a disposizione l'attributo o il metodo in qualsiasi punto del punto del programma. Un esempio di metodo static è il *main* che rappresenta l'inizio del programma.

## 10. Come funziona l'avvio del pogramma (static)?
(sempre nell'ambito dello static)

## 11. Concetto di information hiding e incapsulamento
Nell'ambito della programmazione ad oggetti, con il concetto di incapsulamento intendiamo dire che tutto ciò che appartiene ad una classe viene descritto al suo interno. 

È buona norma non far acceder direttamente gli utenti agli attributi e ai metodi di una classe, per farlo utiliziamo i modificatori di accesso (public, private) nascondendo i dettagli di implemenazione e le informazioni interne (logica applicaiva della classe), consentendo solo l'accesso alle informazioni necessarie. 

Con *private* posso quindi nascondere i dettagli costruttivi (attributi, metodi, filtri) della mia classe (e quindi delle sue istanze), questo è il concetto di information hiding.

## 12. Che cos'è ToString()?
È un metodo predefinito appartenente alla classe Object che restituisce una stringa che ci dice il tipo dell'oggetto per il quale lo invochiamo.

## 13. Che cos'è una stored procedure?
Nel contesto del database una stored proedure è un innesto di linguaggo di programmazione che ci permette di fare DDL (es. con le tablle temporanee), DML e QL. Cioè ci permette di compiere un'azione complessa richiamandola in maniera semplice.

Es. di Stored Procedure in cui inseriamo un valore in una tabella:
`CREATE PROCEDURE inserimento_nominativo`
`@nominativo VARCHAR(150)`
`AS`
`BEGIN`
`  INSERT INTO Mia_Tabella(nome)`
`  VALUES('Nome Cognome')`
`END;`

## 14. Che cos'è una left join?
Esempio di Join (che di default è INNER Join) quindi ci mostrerà tutti i record in persona che hanno una carta:
`SELECT * FROM Carta`
`JOIN Persona ON Carta.personaRif = Persona.personaID`
Facendo una Left Join in questo caso otteremmo tutte le carte.


## 15. Principi SOLID
Sono regole che devono sempre eseguite quando si sviluppa un nuovo software.Sono principi di web coding


**S** : *Single Responsibility Principle*: il principio di singola responsabilità afferma che ogni classe dovrebbe avere una ed una sola responsabilità, interamente incapsulata al suo interno.


**O**: *Open/closed principle*: un'entità software dovrebbe essere aperta alle estensioni, ma chiusa alle modifiche. Ovvero principio di estendibilità, quindi, in un certo senso, contiene anche l'ereditarietà.


**L**: *Liskov substitution principle*: secondo il principio di sostituzione di Liskov gli oggetti devono poter essere sostituiti con dei sottotipi senza alterare il comportamento che li caratterizza. 
(polimorfismo)


**I**: *Interface integration principle*: cioè è preferibile l’implementazione di  più interfacce specifiche che non di una più grande e generica. 


**D**: *Dependency inversion principle*:  una classe dovrebbe dipendere dall’astrazioni e non da classi concrete. 


## 16. Definizione di polimorfismo:
In una situazione di ereditarietà, per polimorfismo si intende la capacità di un oggetto di trasformarsi, cioè di modificare il tip della sua istanza, in questo caso si SPECIALIZZA. Questo procedimento si chiama BINDING DINAMICO. Per esempio quando istanziamo una superclasse Persona e specializziamo il suo oggetto nella sottoclasse Studente:

`Persona per = new Studente();`

In pratica stiamo sfruttando la capacità della superclasse di trasformarsi un una delle sue specifiche sottoclassi. Potremmo sfruttare il polimorfismo per, per esempio, per creare una lista di oggetti eterogenei.

Si può utilizzare il polimorfismo in tutti i casi di ereditarietà, ad esempio abbiamo due tipi di polimorfismo: polimorfismo di classe e polimorfismo di interfaccia.

## 17. Che cos'è il binding dinamico?
Quando l’istanza di una classe madre si specializza nel tipo della classe figlia. Il binding dinamico avviene solo all'avvio del programma.

## 18. Cos’è LINQ?
Language Integrate Query serve per inerrogare le strutture di dati attraverso .Net con una sintassi simile a quella di SQL.

Cioè è una funzionalità di .NET che consente di eseguire query su diverse fonti in modo uniforme integrando la sintassi delle query direttamente nel linguaggio di programmazione. Grazie a LINQ possiamo interrogare i dati del database. 

## 19. Cos’è il dbset ?
È un contenitore di tuple, la tupla è un riga (un record) che ne permettono l'interrogazione o la creazione. 

## 20. Cos’è il singleton?
È un design pattern di programmazione che garantisce la creazione di una singola istanza, fornendo un accesso globale a essa.

All'interno del DAO (Data Access Project)  che fa parte del DAL
`private static PersonaDao instance;`
...

## 20. Cos’è una Stored Procedure?
Una stored procedure è un innesto di linguaggio di programmazione che ci permette di fare DML , QL.

## 21. Cos'è lo using ?
Lo using alloca variabili all'interno del suo contesto dette disposable, cioè alla sua conclusione grazie al garabage collector vengono eliminate dalla memoria. 

## 22. Cos’è il BCL?
Il BCL (Base Class Library) è una parte fondamentale del framework .NET che offre un'ampia gamma di classi e metodi per supportare lo sviluppo di applicazioni, consentendo agli sviluppatori di risparmiare tempo e sforzo grazie alla disponibilità di funzionalità già pronte e testate.

## 23. Cosa sono le proprerties? 
Sono un costrutto utile per gestire l’accesso e la modifica degli attributi di un oggetto in modo controllato, facilitando l’incapsulamento. Questi forniscono i metodi get e set per accedere e modificare i valori dei campi privati.

## 24. Qual è la differenza tra un classe e un oggetto?
la classe è come un progetto o un modello che stabilisce come dovrebbe essere un oggetto, mentre l'oggetto è l'effettiva realizzazione di quel modello, con caratteristiche e dati specifici. Un oggetto può essere una variabile che basa la sua esistenza su una classe.

## 25. Com’è fatta una classe ?
Si può definire come una aggregazione di metodi e attributi. A livello di progettazione abbiamo:

- Strutture che immagazzinano i dati (attributi)
- Funzionalità (metodi)

## 26. Cos’è un attributo?
È la proprietà di un oggetto adibita all'immagazinamento dei dati.

## 27. Cos’è un metodo ? 
È un sottoprogramma o una funzione che esegue delle operazioni.

## 28. Definizione di Foreign Key e a cosa serve?
La foreign key, o il **VINCOLO DI INTEGRITÀ RELAZIONALE** è una chiave di riferimento ad una tabella esterna, sottoforma numerica. Serve a garantire l'integrità e la coerena dei dati  tra le due tabelle.
- Una foreing key **non può** essere null;
- Una foreign key **non può** fare riferimento ad una chiave primaria che non esiste.
  
Una foreign key è un **CONSTRAINT** cioè *impone un vincolo di controllo* su una colonna di associazione.

Per assicurare la coerenza dei dati, all'eliminazione di un record dalla tabella alla quale fa riferimento la foreign key, possiamo utilizzare la dicitura `ON DELETE CASCADE`.

## 29. Che cos'è lo scaffolding?
È la traduzione della tabella in una classe. 

## 30. Che cos'è l'ORM?
**ORM** = Object Relational Mapping, garantito o effettuato dall'entity framework. Cea un collegamento diretto tra le tabelle che si trovano nel database e i loro record. In altre parole: se una classe genera degli oggetti, gli oggetti sono a loro volta collegati alle *righe* delle tabelle. Quindi, creando un nuovo oggetto, creerò un nuovo record!

## 31. Perché, all'interno di una classein C# che contiene delle foreign key, l'attributo public virtual MiaClasseRifNavigation? è nullable?
`public virtual MiaClasseRifNavigation? {get; set}` 

## 32. Che cos'è .typeOf()? E come l'abbiamo utilizzato? 

## 33. Funzione di HASH e MD5:
Un hash è un valore numerico generato da una funzione di Hashing. Gli hash sono utilizzati per confrontare per confrontare oggetti e per ottimizzare la ricerca in strutture di dati. In pratica è una stringa rappresentativa di un valore.

MD5 è un algoritmo di cifratura non invertente al quale posso dare un testo e mi restituirà un codice (HASH) di 32 caratteri. Non è invertente nel senso che restituisce solo un certo numero di caratteri. Gli algortmi di hashting sono pubblici e vengono detti **riepologativi**. Vengono anche detti **generatori di impronta**.

L'**impronta** è una funzione che mi ritorna un valore, viene detta di **digest**: se gli diamo dei valori diversi mi restituirà dei valori diversi, se gli do dei valoro uguali mi restituirà gli stessi valori.

## 34. Che cos'è una Hash Table? E che cos'è il Dictionary?
`Hashtable` è una collezione di elementi combinati in coppie chiave-valore, la cui chiave deve necessariamente essere di un tipo primitivo mentre i valori possono avere qualsiasi tipo. Questo fa si che sia un contenitore **non omogeneo** e si può accedere ai valori **solo** tramite la chiave, che è sempre il primo valore. L'hastable è un contenitore **sequenziale** quindi l'ordinamento non è possibile e non essendo omogeneo, o comunque visto che i suoi elementi non possono esere accumunati tra loro, non si può utilizzare LINQ in questo contesto Si usa una hashtable quando non ha importanza l'rdinamento degli elementi. Tuttavia è importante notare che troppa libertà sulla tipologia dei dati creerà difficoltà nella standardizzazione e quindi nella gestione dei dati.

`Hashtable ht = new HashTable()`

`ht.Add(0, "Mario");`

`ht.Add("pippo", 0.5f)`

`ht.Add("obj", new {Nome = "Valeria", Cognome = "Verdi"})`

`Dictionary` associa ad una chiave un contenuto, cioè è una collezione di elementi combinati in coppie chiave-valore. È un elemento con tipizzazione forte, in cui possiamo specificare il tipo della nostra chiave e del nostro valore. Anche in questo caso l'ordinamento sarà **fittizio** poichè l'elenco preerva l'ordine dell'inserimento, ossia l'ordine sequenziale.

`Dictionary<int, string> elenco = new Dictionary<int, string>();`

`elenco.Add(0, "Studente uno);`

`elenco.Add(1, "Studente due);`

## 35. Cosa sono IEnumerable, ICollection e IList?
`IEnumerable` è una interfaccia che contiene dei metodi basici. È utile quando si vuole semplicemente leggere gli elementi di una collezione senza bisogno di aggiungere, rimuovere o contarli.

`ICollection` eredita da `IEnumerable` e vi aggiunge nuovi metodi, come `.Add()`. È utile quando, oltre a voler iterare su una collezione, si ha bisogno di modificarla, aggiungere o rimuovere elementi o conoscere la dimensione della collezione.
`IList` eredita a sua volta da `ICollection`, con la specifica `.Add(T)`

Perchè utilizzare `ICollection`? Per il principio **D** del **SOLID**: le classi dovrebbero dipendere da astrazioni e non da classi concrete Cioè, si dovrebbe sempre poter accedere ai metoi implementati da `ICollection`.

## 36. Cos'è il CDN?

## 37. Che cos'è una Constraint? Un esempio?

## 38. Che cos'è un indice nel contesto della una primary key?
Quando viene creata la struttura dei record in memoria, insieme ad essa viene creato un indice associato ai singoli record. Grazie alla primary key possiamo scorrere molto più rapidamente la memoria e trovare i record associati, che è quindi un campo identificativo univoco che ci permette di operare in maniera **atomica**, cioè su una singola riga.

L'indice è una struttura che ci permette una rapida scansione dei record di una tabella. Può essere necessario su una tabella con numerosissimi record, per interrogazioni frequenti.

## 39. Che cos'è una Unique ed una chiave eletta?

## 40. Che vuol dire DOM e che cos'è?
Il *Document Object Model* è la rappresentazione sottoforma di albero della struttura del documento HTML. È formato dai tag che rappresentano i nodi dell'albero e possiamo accedere ai nodi tramite JavaScript utilizzando, ad esempio, `document.getElementByID()` per esempio.

## 41. Che signiica che l'HTML è stateless? 
Se modifichiamo o inseriamo dei dati nell'HTML, i dati non vengono conservati: questo perché non vengono conservati nello *stato*.

## 42. Che cos'è il CSS?
Nell'ambito dei linguaggi di makup, il *Cascading Style Sheet* rappresenta lo stile del nostro documento che può essere associato al nostro documento HTML. È un insieme di regole che vengono applicate a tutti gli elementi del DOM, vanno quindi a modificare la grafica della nostra applicazione.

## 43. Qual è la differenza tra classe astratta e interfaccia? 

## 44. Che cos'è una tupla?
È una sequenza di dati eterogenei. Tecnicamente è un array statico di object, che può corrispondere ad un record.

## 45. Che cos'è un'arrow function?

## 46. Perchè utilizziamo var e perchè usiamo let? Che cos'è const?

## 47. Che cos'è una View? E si possono fare delle proiezioni al suo interno?
Nel contesto dei database, la View è una struttura, dichiarata in DDL, che può contenere Query language,  potrà quindi solamente leggere i dati. Possiamo dire che è temporanea poichè viene creata solamente per leggere. 

Un'operazione di proiezione consente di determinare, ad esempio, delle singole colonne da una tabella per visualizzarne i dati. 

`Esempio di codice qui`

## 48. Come funziona il protected?
Data una situazione ereditaria, settando una property come protected, potranno accedervi **solo** una superclasse e i suoi discendenti. Invece con il private, potrà accedervi solo la classe stessa.

## 49. Internal invece?
All'interno di un progetto fa sì che altre soluzioni non possono accedere alle informazioni delle altre, quindi racchiudendo tutte le informazioni all'interno di ciascuna singola soluzione.

## 50. Che cos'è readonly?
è una parola chiave che utilizziamo per far sì che si possa avere accesso ad un dato in sola lettura. Cioè, questo dato non sarà in alcun modo modificabile.

## 51. Che cos'è il DAO?
Il C# il **Dao** (Data Access Object) è un pattern di programmazione che rappresenta il legame tra il codice sorgente ed il database. // da integrare

## 52. Esempi di relazioni one to one, one to many e many to many?

## 53. Possiamo definire C# come fortemente o debolmente tipizzato?

## 54. Che cosa signifia override?
È l'operazione che ci permette di ridefinire un attriuto o un metodo di una classe genitore. Nella classe genitore deve avere la parola chiave **abstract** che indica che quel metodo deve essere necessariamente implementato nelle sottoclassi.

## 55. Che cos'è la composizione e come viene utilizzata?

## 56. Che cos'è l'aggregazione e come viene utilizzata?

## 57. Che cos'è l'UML?
**Unified Modeling Language**.

## 58. Che succederebbe se, in una situazione ereditaria, scrivessi un costritture parametrico nella superclasse?
In una situazione ereditaria, scrivendo un costruttore parametrico sovrascrivo il costruttore di default! Quindi è bsempre bene dichiarare il costruttore senza parametri, quello di default, nella superclasse per non sovrascriverlo!

## 59. Che cos'è GIT?

## 60. Che cos'è la staging area?

## 61. Che cos'è la commit?
Prende ciò che c'è nella stagin area, gli da un codice identificativo, e salva una copia degli elementi al suo interno.

## 62. Che cos'è la modalità Fast Forward?

## 63. Cosa sono i conflitti?

## 64. Che cos'è un CDN?
*Contact Delivery Network* è un computer o un serve super ottimizzato, dedicato **solo** alla delivery di un certo file, quindi fornendolo nella maniera più ottimizzata.

## 65. Qual è la differenza tra null e undefined in JavaScript?

## 66. Paradigma client-server:
Design pattern architetturale.
*Client*: qualsiasi strumento in grado di fare delle richieste http. Una architettura http deve stare a delle regole: il client utilizza il protocollo http per fare una richiesta. Una richiesta http è una richiesta di dati o servzi. Es. una API: cioè una tipologia di elemento che ci restituisce qualcosa alla richiesta.

*Server*: è qualcosa a cui chiediamo i servizi.

Richiesta HTTP: Hyper Text Transfer Protocol. Una richiesta HTTP è stateless: non conserva i dati della precedente richiesta. Per funzionare, al paradigma HTTP deve essere associata una *response*.

HTTP request e HTTP Response:
- **Http request** può essere effettuata in due modi: get e post. hanno specificato il mittente, il destinatario e un payload (il contenuto). Con il mio browser posso fare esclusivamente richieste *get*, per creare delle richieste di post ho bisogno di un simulatore.
- **Http response** contiene il mittente, il destinatario, uno status code e un payload opzionale.

## 67. Status code:
- 100 informativo
- 200 OK
- 300 rindirizzamento
- 400 client errors (es. quando si entra in una pagina che non esiste, es. quando di digita male)
- 500 server errors (es. il server non è stato in grado di gestire una richiesta, ome un imprevisto interno gg)

## 68. Che cos'è MVC?
È un pattern di programmazione che suddivide i file per i compiti, Model View Controller.
- La *View* è l'unica parte in cui l'utente viene a contatto con il programma, es. è la parte in cui ci sarà HTML, CSS, JS.
- Il *Controller* genera gli oggetti a partire dalle classi all'interno di Models e li salva nel database.
- *Models* contiene le classi, serve soltanto al controller per, effettivamente, creare gli oggetti che poi (il controller) creerà anche nel database.

## 69. Che cos'è il TLD?
È il Top Level Domain, cioè è la prima parte di un **endpoint**, che, combinato a dei segment, porterà ad una pagina. Es: facebook.com/home : il TDL è facebook.com, mentre il segment è /home, cioè tutto ciò che in genere si trova tra /.

## 70. Principi ACID:
- A => Atomicità: Ogni transazione deve essere totale o nulla, non amette esecuzioni parziali.
- C => Coerenza: Se c'è un vincolo di integrità, questo non può essere contraddetto. 
- I => Isolamento: Ogni transazione deve essere eseguita in maniera isolata e indipendente, a blocco e sequenziale, non interferisce con le altre!
- D = Durabilità: Se c'è un nuovo stato, se la commit va a buon fine, non si può tornare indietro! Diventa quello il suo stato attuale.

## 71. Vincoli interni e vincoli esterni:
Vincoli esterni, nel contesto del database, sono ad esempio quando dichiariamo il tipo di dato (VARCHAR, INT ecc.) o anche UNIQUE, NOT NULL...mentre i vincoli esterni per esempio sono le Foreign Key.

## 72. Cosa sono i tipo primitivi e quali sono?

## 73. In C# cos'è una var? Posso fare una lista di var?

## 74. Come funziona l'ereditarietà?
C'è una situazione di ereditarietà quando, a patire da una superclasse, abbiamo delle sottoclassi che ne ereditano metodi e attributi. Dei metodi ereditati da una superclasse possiamo fare *override* nella sottoclasse quando, nella superclasse, sono definiti come *virtual*.

## 75. Che cos'è un'istanza?

## 76. Che cos'è un attributo di classe?

## 77. Come si fa un ciclo infinito?

## 78. Come funzione la SQL Injection?
Tecnica che viene utilizzata per bypassare dei controlli con l'obiettovo di accedere a dei dati ai quali non si dovrebbe accedere.

## 79. Che cos'è una Property?

## 80. Che cos'è una transaction? E come è fatta?

## 81. Com'è fatto un foglio HTML?

## 82. Un metodo per collegarsi al DB senza entity framework? Quale libreria si usa?

## 83. Che cosa sono i Services e cosa fanno?

## 84. Che cos'è il costruttore?
// da integrare // I costruttori sono implicitamnte pubblici, per inibirli possiamo renderlo privato, ma se stiamo scrivendo una superclasse, basterà definire la classe come astratta. 

## 85. Che cos'è MVC? E perchè dovrei usarlo?
Pattern di programmazione, "Model View Controller" // da integrare //. Si utilizza poichè è facilmente scalabile e mantenibile.

## 86. Che cos'è MVVM?
Model View ViewModel, è la struttura utilizzata da Angular: potenzia all'estremo l'MVC. // da integrare //


---

## stringa di comando per fare push
git remote add origin https://github.com/acelilli/iemme_q.git

git branch -M main

git push -u origin main
