## 1. Che cos'è una classe astratta?
In generale, una classe si può definire come una aggregazione di metodi e attributi. 

Una classe astratta è una classe che non può essere istanziata. È un'astrazione, una sorta di stampo che contiene attributi e metodi che verranno poi ereditati dalle sue sottoclassi. Una classe astratta viene ESTESA da una sottoclasse.

Un metodo astratto è un metodo SENZA CORPO che deve essere necessariamente essere ereditato da una sottoclasse tramite la parola chiave OVERRIDE che ci permette di riscrivere il metodo nella sottoclasse, quando nella superclasse è specificata la parola chiave VIRTUAL.

## 2. Che cos'è la classe Object?
Object è la **superclasse** dalla quale derivano tutte le entità.

## 3. Che cos'è la firma?
È il modo con cui un metodo può essere richiamato. Due metodi non possono avere la stessa firma sebbene possano chiamarsi allo stesso modo. Le firme devono essere necessariamente diverse (cioè avere parametri diversi). Quando esistono dei metodi che hanno lo stesso nome ma firme diverse si dice che si sta facendo un OVERLOAD di parametri.

## 4. Che cos'è l'Overload?
Si fa l'overload quando scriviamo due metodi con nome uguale ma firme, cioè parametri, diversi. (polimorfismo statico)

## 5. Che cos'è una lista?
Una lista risolve il problema degli array statici: è una raccolta di dati che possono anche non essere dello stesso tipo, la lunghezza della lista è variabile, ogni elemento al suo intero potrà quindi occupare spazi non sequenziali in memoria. 

## 6. Che cos'è un array?
Un array è una raccolta di dati omogenea e statica. Cioè un array ha lunghezza fissa (quindi occupa un certo spazio in memoria) e al suo interno i dati sono tutti dello stesso tipo.

## 7. Se scrivo IEsempio"<"T">"?
In `IEsempio<T>` IEsempio rappresenta un'interfaccia, mentre `<T>` rappresenta un tipo di dato generico, cioè che potrà in seguito essere sostituito con qualsiasi altro tipo (es. una classe) a mia scelta.

L'elemento interfaccia è un costrutto che contiene esclusivamente dei metodi senza corpo. È in realtà un elenco di metodi senza corpo quindi tecnicamente non è una classe, ci dice esclusivamente cosa si è **costretti** ad implementare a livello di metodi. Al suo interno quindi **non** ci sono attributi.
Un'interfaccia viene **implementata**.

## 8. Che cos'è il tipo generico e a cosa serve?
`<T>` rappresenta il dato generico di una classe. Ad esempio, quando dobbiamo implementare un'interfaccia associandole `<T>`, (es.: `IInterfaccia<T>`) diciamo che nel diamond potrà andare qualsiasi tipo di dato, e quando implementata sarà: `public class Persona : IInterfaccia<Persona>`

## 9. Che cos'è static?
In C#, **static** è definito come attributo di classe, è una parola chiave che indica una proprietà o attributo allocato immediatamente all'inizio del programma: non avrà quindi bisogno dell'istanza di una classe per essere richiamato, mettendo a disposizione l'attributo o il metodo in qualsiasi punto del punto del programma. Un esempio di metodo static è il *main* che rappresenta l'inizio del programma.

## 10. Come funziona l'avvio del pogramma (static)?
(sempre nell'ambito dello static)
Il programma inizia dal metodo **static Main** che è l'entry point del programma. Gli altri metodo definiti come **static** saranno disponibili in qualsiasi punto del programma perchè già allocati al suo avvio. 

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
Sono regole del coding che devono sempre eseguite quando si sviluppa un nuovo software. 


**S** : *Single Responsibility Principle*: il principio di singola responsabilità afferma che ogni classe dovrebbe avere una ed una sola responsabilità, interamente **incapsulata** al suo interno.


**O**: *Open/closed principle*: un'entità software dovrebbe essere aperta alle estensioni, ma chiusa alle modifiche. Ovvero principio di estendibilità, quindi, in un certo senso, contiene anche l'**ereditarietà**.


**L**: *Liskov substitution principle*: secondo il principio di sostituzione di Liskov gli oggetti devono poter essere sostituiti con dei sottotipi senza alterare il comportamento che li caratterizza. Cioè facciamo riferimento al **polimorfismo**.


**I**: *Interface integration principle*: cioè è preferibile l’implementazione di  più interfacce specifiche che non di una più grande e generica. 


**D**: *Dependency inversion principle*:  una classe dovrebbe dipendere dall’astrazioni e non da classi concrete. 


## 16. Definizione di polimorfismo:
In una situazione di ereditarietà, per polimorfismo si intende la capacità di un oggetto di trasformarsi, cioè di modificare il tipo della sua istanza, in questo caso si SPECIALIZZA. Questo procedimento si chiama BINDING DINAMICO. Per esempio quando istanziamo una superclasse Persona e specializziamo il suo oggetto nella sottoclasse Studente:

`Persona per = new Studente();`

In pratica stiamo sfruttando la capacità della superclasse di trasformarsi un una delle sue specifiche sottoclassi. Potremmo sfruttare il polimorfismo per, per esempio, per creare una lista di oggetti eterogenei.

Si può utilizzare il polimorfismo in tutti i casi di ereditarietà, ad esempio abbiamo diversi tipi di polimorfismo: 
- Polimorfismo di classe e Polimorfismo di interfaccia. Per **polimorfismo di classe** si ha quando una sottoclasse sostituisce(override) o estende(overload) i metodi di una classe madre. Il **polimorfismo di interfaccia** si ha quand si implementano una o più interfacce in una classe e se ne ridefiniscono i metodi.
- Polimorfismo dinamico e Polimorfismo statico: il **polimorfismo dinamico** (overriding) si ha quando c'è una riscrittura di un metodo ereditato (es. ToString() che ereditiamo dalla classe Object e del quale facciamo overriding ridefinendolo), mentre il **polimorfismo statico** (overloading) si ha quando abbiamo più metodi con lo stesso nome ma firme (parametri) diverse.

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

`public static PersonaDao GetInstance()`
`{
 if(instance == null)
   instance = new PersonaDao()
  return instance;
}`

`private PersonaDao() {}`

## 20. Cos’è una Stored Procedure?
Una stored procedure è un innesto di linguaggio di programmazione che ci permette di fare DML, QL. In pratica creiamo un sottoprogramma all'interno del nostro DBMS che ci permette di fare delle operazioni, anche parametriche, richiamandolo col il suo nome.

`CREATE PROCEDURE NomeProcedure
 @parametro VARCHAR(250)
 --altri eventuali parametri
AS
 BEGIN INSERT INTO miaTabella(nomeColonna) VALUES (@parmetro);
  PRINT 'Inserimento effettuato con successo'
 END;`

 Per richiamare la procedura:
 
 `EXEC NomeProcedura = 'valore'`

## 21. Cos'è lo using ?
Lo using alloca variabili all'interno del suo contesto dette disposable, cioè alla sua conclusione grazie al garabage collector vengono eliminate dalla memoria. 

## 22. Cos’è il BCL?
Il **BCL** (Base Class Library) è una parte fondamentale del framework .NET che offre un'ampia gamma di classi e metodi per supportare lo sviluppo di applicazioni, consentendo agli sviluppatori di risparmiare tempo e sforzo grazie alla disponibilità di funzionalità già pronte e testate.

## 23. Cosa sono le proprerties? 
Sono un costrutto utile per gestire l’accesso e la modifica degli attributi di un oggetto in modo controllato, facilitando l’incapsulamento. Questi forniscono i metodi get e set per accedere e modificare i valori dei campi dei relativi attributi.

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
**ORM** = Object Relational Mapping, garantito o effettuato dall'entity framework. Cea un collegamento diretto tra il programma e le tabelle che si trovano nel database. In altre parole: se una classe genera degli oggetti, gli oggetti sono a loro volta collegati alle *righe* delle tabelle. Quindi, creando un nuovo oggetto, creerò un nuovo record!

In altre parole, permette di mappare gli oggetti di un linguaggio OOP alle strutture di un DB relazionale (come tabelle, righe, colonne).

Questo avviene quando installo Entity Framework nel mio programma: si può fare manualmente con il DAL (e i relativi DAO) oppure con lo scaffolding, che importerà tutto in automatico.

## 31. Perché, all'interno di una classein C# che contiene delle foreign key, l'attributo public virtual MiaClasseRifNavigation? è nullable?
`public virtual MiaClasseRifNavigation? {get; set}` 

## 32. Che cos'è typeOf()? E come l'abbiamo utilizzato? 
**typeOf()** è un metodo che abbiamo utilizzato per comparare se il tipo di un oggetto è uguale ad una classe. Cioè:

`if(stu.GetType() == typeOf(Persona))` =>  in questo esempio controlliamo se il tipo di stu è uguale al tipo della classe Persona.

## 33. Funzione di HASH e MD5:
Un **hash** è un valore numerico generato da una funzione di Hashing. Gli hash sono utilizzati per confrontare per confrontare oggetti e per ottimizzare la ricerca in strutture di dati. In pratica è una stringa rappresentativa di un valore.

MD5 è un algoritmo di cifratura non invertente al quale posso dare un testo e mi restituirà un codice (HASH) di 32 caratteri. Non è invertente nel senso che restituisce solo un certo numero di caratteri. Gli algortmi di hashting sono pubblici e vengono detti **riepologativi**. Vengono anche detti **generatori di impronta**.

L'**impronta** è una funzione che mi ritorna un valore, viene detta di **digest**: se gli diamo dei valori diversi mi restituirà dei valori diversi, se gli do dei valore uguali mi restituirà gli stessi valori.

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
**Contact Delivery Network** compututer o server super ottimizzato, dedicato solo al delivery di un certo file, quindi che lo forniscono in maniera più ottimizzata.

## 37. Che cos'è una Constraint? Un esempio?
Nel contesto dei database una costraint è un **vincolo** che si applica ad una colonna o ad un gruppo di colonne di una tabella per grantire l'integrità e la correttezza dei dati. Ne esistono di vari tipi, tra cui: primary key, foreign key, unique e check. Possiamo scrivere una constraint così:

`ADD CONSTRAINT Chk_eta CHECK (eta > 18)` 

## 38. Che cos'è un indice nel contesto della una primary key?
Quando viene creata la struttura dei record in memoria, insieme ad essa viene creato un indice associato ai singoli record. Grazie alla primary key possiamo scorrere molto più rapidamente la memoria e trovare i record associati, che è quindi un campo identificativo univoco che ci permette di operare in maniera **atomica**, cioè su una singola riga.

L'indice è una struttura che ci permette una rapida scansione dei record di una tabella. Può essere necessario su una tabella con numerosissimi record, per interrogazioni frequenti.

## 39. Che cos'è una Unique ed una chiave eletta?
Garantisce che i valori in una data colonna siano unici ovvero che non siano duplicati all'interno di quella colonna. Una unique diventa una chiave elentta quando non viene definita la primary key. La chiave primaria eletta deve soddisfare i criteri di unicità e non nullità, se li soddisfa potrà essere appropriata per identificare univocamente ogni record della tabella.

## 40. Che vuol dire DOM e che cos'è?
Il *Document Object Model* è la rappresentazione sottoforma di albero della struttura del documento HTML. È formato dai tag che rappresentano i nodi dell'albero e possiamo accedere ai nodi tramite JavaScript utilizzando, ad esempio, `document.getElementByID()` per esempio.

## 41. Che significa che l'HTML è stateless? 
Vuol dire che è senza stato. Se modifichiamo o inseriamo dei dati nell'HTML, i dati non vengono conservati: questo perché non vengono conservati nello *stato*.

## 42. Che cos'è il CSS?
Nell'ambito dei linguaggi di makup, il *Cascading Style Sheet* rappresenta lo stile del nostro documento che può essere associato al nostro documento HTML. È un insieme di regole che vengono applicate a tutti gli elementi del DOM, vanno quindi a modificare la grafica della nostra applicazione.

## 43. Qual è la differenza tra classe astratta e interfaccia? 
Un'interfaccia è composta unicamente da metodi vuoti. Una classe astratta invce contiene attributi e metodi. Quando implementiamo un'interfaccia se ne si implementiamo obbligatoriamente tutti i metodi, che se vogliamo utilizzare dovremo necessariamente farne l'override. Quando estendiamo una classe astratta e ne ereditiamo i metodi possiamo decidere di farne l'override oppure utilizzarli come sono nella classe madre.

## 44. Che cos'è una tupla?
È una sequenza ordinata di dati eterogenei. Nel contesto del database, una tupla può corrispodere a dun record di una tabella.

Tecnicamente è un array statico di Object (cioè l'array può essere considerato come una tabella di Object), dei quali gli oggetti nell'array corrisponderanno ai record della tabella.

## 45. Che cos'è un'arrow function?
Funzione che non ha bsogno della keyword function, può venire associata ad una variabile (preferibilmente una const), che permette di scrivere una funzione in maniera molto più sintetica.

`const miaFunzione = (param) => param * 2` 

In presenza di un solo parametro, le parentesi tonde possono anche non venire scritte.

## 46. Perchè utilizziamo var e perchè usiamo let? Che cos'è const?
- `var` definisce una variabile di qualsiasi tipo, sovrascrivibile e richiamabile in qualsiasi punto (quindi pericolosa).
- `let` accessibile solo in un dato ambito o scope, non può essere ridichiarata ma uò essere aggiornata. Preferita a var.
- `const` una volta dichiarato il suo valore non può cambiare. 

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
Il C# il **Dao** (Data Access Object) è un pattern di programmazione che rappresenta il legame tra il codice sorgente ed il database. Diversi DAO sono contenuti in una cartella DAL (Data Acces Layer). Il DAO rappresenta quindi un'interfaccia (detta **IDao**) che implementiamo dei DAO nei nostri componenti per definirne i metodi.

## 52. Esempi di relazioni one to one, one to many e many to many?
- One to One: una persona ha solo una carta di identità (o codice fiscale...)
- One to Many: una persona ha tante carte fedeltà.
- Many to Many: tanti pacchetti viaggi contengono tante destinazioni.

## 53. Possiamo definire C# come fortemente o debolmente tipizzato?
Possiamo definire C# come un linguaggio fortemente tipizzato.

## 54. Che cosa significa override?
È l'operazione che ci permette di ridefinire un attriuto o un metodo di una classe genitore. Nella classe genitore deve avere la parola chiave **abstract** che indica che quel metodo deve essere necessariamente implementato nelle sottoclassi.

## 55. Che cos'è la composizione e come viene utilizzata?
Rappresenta una relazione di possesso stretto e dipendenza: ad esempio un mazzo di fiori, che senza i fiori non esiste. Ad esempio un contenitore (lista, ienumerable ecc.) non esiste se non ha del contenuto (oggetti o valori) al suo interno.
`public List<Fiori> {get; set;};`

## 56. Che cos'è l'aggregazione e come viene utilizzata?
Rappresenta una relazione di collaborazione dove gli oggetti e il loro contenitore possono esistere indipendentement gli uni dagli altri.  Ad esempio un archivio continua ad esistere senza gli elementi al suo interno.
`public List<Archivio> {get; set;} = new List<Archivio>()`

## 57. Che cos'è l'UML?
**Unified Modeling Language** rappresenta la struttura progettuale di un programma, nell'ambito della OOP. Attraverso l'UML possiamo creare diagrammi di classi, oggetti e componenti.  Attraverso i diagrammi che scriviamo con l'UML possiamo tracciare metodi, attributi e relazioni tra le classi.

Invece per tracciare le tabelle di un Database si utilizza il ERD (Diagramma entità relazionale).

## 58. Che succederebbe se, in una situazione ereditaria, scrivessi un costritture parametrico nella superclasse?
In una situazione ereditaria, scrivendo un costruttore parametrico sovrascrivo il costruttore di default! Quindi è bsempre bene dichiarare il costruttore senza parametri, quello di default, nella superclasse per non sovrascriverlo!

## 59. Che cos'è GIT?
È un sistema di controllo di versionamento (VCS - Version Control System): cioè permette di tracciare le modifiche ai file di un progetto e coordinare il lavoro tra più sviluppatori.  **GitHub** è una repository remota.

## 60. Che cos'è la staging area?
La staging area, ossia l'area di sviluppo, nel contesto di GIT rappresenta un'area intermedia nella quale vengono preparati i file prima di essere committati.

## 61. Che cos'è la commit?
Prende ciò che c'è nella staging area, gli da un codice identificativo, e salva una copia degli elementi al suo interno.

## 62. Che cos'è la modalità Fast Forward?
Modalità che permette di fare il commit da un branch al main quando non ci sono conflitti e altri commit precedenti.

## 63. Cosa sono i conflitti?
Nel contesto di Git, possiamo avere dei conflitti quando vengono apportate delle modifiche ad una parte del codice che git non è in grado di unire automaticamente: può accadere se per esempio due sviluppatori stanno lavorando alla stessa parte di codice, può succedere durante l'uso di branch (ramificazioni) o durante le operazioni di push e merge.

## 64. Che cos'è un CDN?
*Contact Delivery Network* è un computer o un serve super ottimizzato, dedicato **solo** alla delivery di un certo file, quindi fornendolo nella maniera più ottimizzata.

## 65. Qual è la differenza tra null e undefined in JavaScript?
Rappresentano tipologie di valori vuoto, in cui:
- **Undefined** non ha assegnato alcun valore, cioè è stata dichiarata ma non inizializzata.
- **Null** esplicitamente asegnato, rappresenta un valore nullo o vuoto, cioè non ha niente al suo interno.
- **0** non rappresenta assenza di valore, è un numero valido.
Rappresentano tutti e tre dei valori **falsy* cioè possono rappresentare tutti il valore **false**

`null == undefined` => true, ma se scriviamo `null === undefined` => false perchè non c'è corrispondenza di tipo

`0 == false` => true perchè 0 è falsy ma `0 === false` => false perché non c'è corrispondenza di tipo

## 66. Paradigma client-server:
Architettura di rete nella quale i client (computer, browser...) si connette ad un server (computer contenenti file fisici che costituiscon es. siti web) per usufruire di un servizio. Da un client connesso ad internet è possibile inviare una richiesta ad un server (**Http Request**) e dal server è possibile ricevere la risposta alla richiesta (**Http Response**)

- *Client*: qualsiasi strumento in grado di fare delle richieste http.
- Una architettura http deve stare a delle regole, cioè i **protocolli**. Il client utilizza il protocollo http per fare una richiesta. Una richiesta http è una richiesta di dati o servzi. Es. una API: cioè una tipologia di elemento che ci restituisce qualcosa alla richiesta.
- *Server*: è il computer al quale chiediamo i servizi e ci fornisce quindi una Http Response.

Richiesta HTTP: Hyper Text Transfer Protocol. Una richiesta HTTP è stateless: non conserva i dati della precedente richiesta. Per funzionare, al paradigma HTTP deve essere associata una *response*.

HTTP request e HTTP Response:
- **Http request** può essere effettuata in due modi: get e post. Al suo in terno sono specificati il mittente, il destinatario e un payload (il contenuto). Con il mio browser posso fare esclusivamente richieste *get*, per creare delle richieste di post ho bisogno di un simulatore.
- **Http response** contiene il mittente, il destinatario, uno status code e un payload opzionale.

## 67. Status code:
- 100 informativo
- 200 OK
- 300 rindirizzamento
- 400 client errors (es. quando si entra in una pagina che non esiste, es. quando di digita male)
- 500 server errors (es. il server non è stato in grado di gestire una richiesta, ome un imprevisto interno gg)

## 68. Che cos'è MVC?
*Guarda 96 per la versione estesa*
È un pattern di programmazione che suddivide i file per i compiti, Model View Controller.
- La *View* è l'unica parte in cui l'utente viene a contatto con il programma, es. è la parte in cui ci sarà HTML, CSS, JS.
- Il *Controller* genera gli oggetti a partire dalle classi all'interno di Models e li salva nel database.
- *Models* contiene le classi, serve soltanto al controller per, effettivamente, creare gli oggetti che poi (il controller) creerà anche nel database.

## 69. Che cos'è il TLD?
È il Top Level Domain, cioè è la prima parte di un **endpoint**, che, combinato a dei segment, porterà ad una pagina. Es: facebook.com/home : il TDL è facebook.com, mentre il segment è /home, cioè tutto ciò che in genere si trova tra /.

## 70. Principi ACID:
Nel contesto dei database applichiamo i principi ACID quando implementiamo le transaction. Questi principi si applicano sia alle operazioni stesse che, più in generale, al DB stesso, e sono:
- A => Atomicità: Ogni transazione deve essere totale o nulla, non amette esecuzioni parziali. Si assicura che le operazioni all'interno della **transazione** avvengano come una unità indivisibile.
- C => Coerenza: Se c'è un vincolo di integrità, questo non può essere contraddetto, cioè mantiene la coerenza dei dati all'interno del **database**.
- I => Isolamento: Ogni **transazione** deve essere eseguita in maniera isolata e indipendente, a blocco e sequenziale, cioè non interferisce con le altre!
- D = Durabilità: Se la modifiche vanno a buon fine, non si può tornare indietro, aggiornando in ogni caso lo stato del **database**! 

## 71. Vincoli interni e vincoli esterni:
Vincoli esterni, nel contesto del database, sono ad esempio quando dichiariamo il tipo di dato (VARCHAR, INT ecc.) o anche UNIQUE, NOT NULL...mentre i vincoli esterni per esempio sono le Foreign Key.

## 72. Cosa sono i tipi primitivi e quali sono?
Sono tipi che non posso essere nè mmodificati nè scomposti,

## 73. In C# cos'è una var? Posso fare una lista di var?
In C# una variabile dichiarata come `var` è una variabile del quae il tipo viene determinato al momento della compilazione ma che **non può cambiare**. Cioè anche se cambiamo il valore di quella variabile, se viene istanziata come string allora dovrà essere una string anche la sua modifica.

## 74. Come funziona l'ereditarietà?
C'è una situazione di ereditarietà quando, a patire da una superclasse, abbiamo delle sottoclassi che ne ereditano metodi e attributi. Dei metodi ereditati da una superclasse possiamo fare *override* nella sottoclasse quando, nella superclasse, sono definiti come *virtual*.

## 75. Che cos'è un'istanza?
È la realizzazione di una classe, cioè un **oggetto** concreto che possiamo utilizzare nel programma.

## 76. Che cos'è un attributo di classe?
Una caratteristica della mia classe che valorizzamo attraverso le properties.

## 77. Come si fa un ciclo infinito?
Il ciclo continuerà a eseguire il blocco di codice al suo interno fino a quando non si interrompe manualmente l'esecuzione
` while (true)
        {
            Console.WriteLine("Questo è un ciclo infinito.");
            Thread.Sleep(1000); // Pausa di 1 secondo
        }`

## 78. Come funzione la SQL Injection?
Tecnica che viene utilizzata per bypassare dei controlli con l'obiettovo di accedere a dei dati ai quali non si dovrebbe accedere.

## 79. Che cos'è una Property?
// sopra

## 80. Che cos'è una transaction? E come è fatta?
Nel contesto del database, la transaction è una funzionalità che ci permette di aggrupare diversi comandi di esecuzione in un blocco solo. Se tutto va bene questo blocco verrà eseguito nella sua totalità altrimenti il sistema si bloccera e non verrà eseguito il comando. Esempio:
`BEGIN TRANSACTION;
INSERT INTO Utente (nome, cognome) 
VALUES ('Mario', 'Rossi');
INSERT INTO Libro (titolo, autore) 
VALUES ('Il Grande Libro', 'Giovanni Verdi');
COMMIT;
`
Per gestire gli errore utilizziamo la ROLLBACK all'interno di un try catch. (così il nostro programma non va in blocco e si ritorna allo stato precedente).

## 81. Com'è fatto un foglio HTML?
E' composto da due sezioni principali: Head, che è la parte che non viene visualizzata dall'utente e contiene delle informazioni tecniche relative all'utente. Descrivono al browser come codeficare i caratteri, o descrivere la scala del sito. L'unico tagg all'interno di head visualizzato dall'utnte è il title, nella barra del browser. Nel body è racchiuso il contenuto vero e proprio della pagina, visibile dagli utenti. Possiamo suddividere a sua volta il body in header, main e footer.

## 82. Un metodo per collegarsi al DB senza entity framework? Quale libreria si usa?
// DAO

## 83. Che cosa sono i Services e cosa fanno?
Rappresentano la logica del progetto in cui si effettua lo scambio dato tra quelli che devono essere accessibile dagli utenti (DTO) e quelli che vengono effettivamente mandati al DB (attraverso i model) i services possono comunicare solo con gli altri services, i DTO e le Repositories.

## 84. Che cos'è il costruttore? E come è fatto in Javascript e in typescript?
Il cotruttore è il primo metodo che viene richiamato quando istanziamo una classe.  I costruttori sono implicitamente pubblici, per inibirli possiamo renderlo privato, ma se stiamo scrivendo una superclasse, basterà definire la classe come astratta. 
Possiamo fare overload del costruttore dandogli dei parametri. Tuttavia facendolo in una superclasse inibiremmo anche il costruttore delle classi figlie, quindi è una pratica sconsigliata.
- In C# richiamiamo il constructor semplicemente utilizzando il `new`
- In **JavaScript** e in **Typescript** viene richiamato il constructor con il metodo speciale `constructor()`, inoltre in **TS** possiamo tipizzarne i parametri.

## 85. Che cos'è MVC? E perchè dovrei usarlo?
Pattern di programmazione, "Model View Controller" // da integrare //. Si utilizza poichè è facilmente scalabile e mantenibile.

## 86. Che cos'è MVVM?
Model View ViewModel, è la struttura utilizzata da Angular: potenzia all'estremo l'MVC. // da integrare //

## 87. Che cos'è il navigator/rif navigation(?)? Qual è l'obiettivo?


## 88. Come si chiamano le modalità con cui si portano dietro gli oggetti entity framework?
Sono modalità di recupero di informazioni dal database.
- Lazy Loading -> Porta direttamente l'oggetto
- Eager Loading -> Porta dietro un oggetto e anche i riferimenti.

## 89. Che cos'è una migrazione?
Nell'approccio code first possiamo creare e modificare delle tabelle (quindi faremo del DDL), che quindi non abbiamo nella fase iniziale, tramite il codice in C#. Creiamo le classi nel nostro codice, quindi creiamo la migrazione. Inoltre possiamo apportare delle modifiche al database per modificare le tabelle. Lo stato attuale della migrazione del database è lo storico di tutte le sue migrazioni.

## 90. Che cos'è l'Ereditarietà?
Principio della programmazione ad oggetti // da implementare //

## 91. Cosa intendiamo per Astrazione?
L'astrazione consente di modellare entità del mondo reale o concetti complessi attraverso interfacce o classi astratte , consiste nel ridurre la complessità mostrando solo gli aspetti esesnsiali di un oggetto nascondendo i dettagli implementatitvi. 

## 92. Che cos'è un metodo astratto?
E' un metodo che viene dichiarato ma non ha corpo (non ha un'implementazione nella classe astratta), deve essere implementato da tutti le casi derivare concrete, può essere dichiarato soltanto da una calse astratta. 
## 93. Che cos'è l'interfaccia in typescript?
Un'interfaccia in TypeScript serve a definire un contratto per gli oggetti o le classi, specificando quali proprietà e metodi devono essere presenti.

## 94. Il Javascript è un linguaggio di programmazione orientato ad oggetti?
Si ma non del tutto, essa implementa il concett di OOP in modo diverso, usa principalmente l'uso di prototipi per l'eridarietà, sinstassi delle classi, incapsulamento con le (closure) visto che non abbiamo i metodi get e set, polimorfismo attraverso l'ereditarietà e la possibilità di sovrascrivere metodi in classi derivare.

## 95. Cos'è il ToString() e cosa sono .Equals e GetHashCode(?) che fanno arte della la casse Object?
- ToString() restituisce sottoforma di string il tipo dell'oggetto.
- Equals() verifica che qualsiasi tipo di oggetto e i suoi valori siano uguali a quelli dell'oggetto passato nella funzione, restituice un bool. `base.Equals(obj)` quindi compara il **contenuto**
- GetHasCode() restitusce un valore numerico che identifica un certo oggetto. Non verifica il contenuto della variabile, serve proprio per identificare due oggetti siano effettivamente due oggetti diversi.

## 96. Come funziona il pattern MVC?
*Guarda 68 per la versione breve*
Il pattern di programmazione MODEL VIEW CONTROLLER: nel model definiamo le classi che valoriazziamo attraverso la logica scritta nel controller. Accediamo alla logica attraverso le View, che rappresentano l'unico punto di comunicazione tra l'utente e la logica del programma.

Es.: attraverso un form compiato dall'utente nella view (la parte visualizzata composta da HTML ecc.), inviamo la richiesta al controller che si occupa della gestione dei dati inviati, e li confronta con il model. Poi, a seconda della struttura del progetto può essere il controller ad inviare i dati al database, oppure può essere il model ad occuparsi di questa operazione (attraverso le strutture intermediare di Repo, Services e DTO).7

View ↔ Controller ↔ Model

View ↔ Controller ↔ Service(DTOs) ↔ Models(Repositories) ↔ DBMS

## 97. Invece con Angular? (MVVM)
Il pattern MVVM (MODEL VIEW VIEWMODEL) rappresenta un potenziamento dell'MVC, ma all'interno del framework Angular.

Utilizza cioè una struttura come quella dell'MVC: il **model** contiene le classi e rappresenta il collegamento tra la business logic e i dati. La **view**, come in MVC è la parte HTML con cui comunica l'utente che visualizza i dati. Il ViewModel è un intermediario tra i model e le view: raccoglie i dati e gestisce gli eventi. Interagisce con la view utilizzando il **data binding** , cioè accedendo ai dati `prod.Nom`.

## 98. Cos'è il two way binding?


## 99. Due variabili possono puntare alla stssa locazione di memoria?
Sì. Se per esempio creiamo una variabile alla quale assegnamo come valore un'altra variabile, entrambe punteranno alla stessa locazione in memoria. Es:

`int x = 5;`

`int y = x`

Visto che entrambi puntano alla stessa cella di memoria, modificando uno verrà modificata anche l'altra. C# le variabili quindi puntano ad un indirizzo in memoria, mentre, ad esempio se scrivessimo la stessa cosa su **JavaScript**, la variabile x e la variabile y sarebbero totalmente separate tra di loro creando una nuova cella di memoria per ciascuna.

## 100. Cosa sono AddTransient(), AddSingleton() e AddScoped()?
Nell'ambito di una applicazione API WEB nel nostro progran.cs implementiamo questi metodi per registrare i servizi. Essi definiscono il ciclo di vita dei servizzi all'interno dell'applicazione especificando quando le istanze di un servizio vengono create e gestite. 
AddTransient()--> ASP.NET crea una nuova istanza del servizio ogni qual volta viene richiesto.
AddScope()--> ASP.NET crea una nuova istanza del servizio per ogni richiesta HTTP. 
AddSingleton() ASP.NeT crea una solo istanza del servizion che viene condivisa in tutta l'applicazione. 

## 101. Che cos'è una architettura Client/Server? Come funzionano l'Http Request e l'Http response? 
Una complient architecture basata su due attori: Client e Server. La comunicazione avviene tramite protocolli HTTP, in cui il CLIENT tramite la HTTP REQUEST manda una richiesta, detta HEADER (che contiene mittente, destinatario e payload).
Quando il server ha effettuato qualsiasi tipo di operazione richiesta, manterà la sua HTTP RESPONSE in cui mette nell'HEADER mittende, destinatario e lo stato della richiesta mentre nel payload il risultato dell'operazione.

## 102. Che cos'è POSTMAN?
Programma che utilizziamo per comunicare con il database attraverso le API. Attraverso PostMan possiamo fare tutte le operazioni CRUD (CREATE, READ, UPDATE e DELETE) tramite le operazioni di GET, POST, PUT e DELETE.

## 103. Che cos'è una REST API? 
In una architettura CLIENT SERVER, una REST API è una metodologia di comunicazione che comunica in HTTP, che invia il body in formato JSON.

## 104. Che cos'è Angular?
Framework di sviluppo di web app single page che gira sul client. Tra le sue peculiarità:
- La sua **struttura in componenti**, indipendenti tra loro e riutilizzabili;
- La sua sincronizzazione tra modello di dati e l'interfaccia utente **data binding bidirezionale**;
- Un sistema di **dipendency injection** cioè quel design pattern architetturale che permette di iniettare dei riferimenti ad altre dipendenze in modo tale da facilitare la comunicazione tra queste (es. per utilizzarne metodi o attributi). Cioè non creiamo una nuova istanza di una classe ma una sua "iniezione".
- **Routing** cioè gestisce la navigazione tra diverse viste dell'app: cioè non viene cambiata la pagina nè viene ricaricata la app, semplicemente avviene un cambiamento di componenti all'interno della mia app.
- Linguaggio **Typescript** cioè superset di Javascript, tipizzato implementato dalla seconda versione di Angular.

## 105. Che cos'è il DOM Dinamico?
Cioè, l'HTML di base è stateless, quinsi, per renderlo dinamico sisogna renderlo stateful e questo avviene non aggiornando mai la pagina: se la pagina non si aggiorna non perde il suo stato e conserverà i dati, passando da stateless a stateful. Con Angular, essendo una single page application i nodi verranno generati in maniera dinamica.

## 106. Cos'è un try-catch? Come funziona? Che succede se innesto un try catch dentro un altro?
E' una struttura di controllo per gestire le eccezzioni, questi possono verificarsi durante l'esecuzione di un programma e mi permette che non si blocchi il flusso dell'esecuzione dell'applicazione. Il try catch anidato (try catch su try catch) se si verifica un'ecceszione nel blocco interno, viene rilasciata al blocco ester no catch che lo catturerà per poi gestirla ulteriormente. 

## 107. Che cos'è l'Http Context?
Contesto che permette di accedere all'Http Response e l'Http Request.

## 108. Che significa SerializeObject e DeserializeObject ?
Sono metodi forniti dalla libreria di Newtonsoft_Json(Json.NET), il primo ovvero Serialize permette di salvare l'oggetto in un formato dati Json che può essere facilemte memorizzato e trasmesso, mentre il secondo lo utilizziamo per ricostruire un oggeto appartier da una stringa Json.

## 109. Che cos'è await async?
Parole chiave utilizzate per gestire la programmazione asincrona in modo più semplice e leggibile. Consentono di scrivre codice asincrono che appare e si comporta in modo sincrono (migliorando la gestione delle promesse). 

Cioè, dichiarando una funzione come asincrona, la rendiamo automaticamente una **promessa** della quale aspettiamo la risoluzione. Ogni promise è univoca, quindi fa le propre "domande" e da solamente le proprie risposte. Inoltre, una promessa non è bloccante: il programma non aspetta la sua risoluzione per continuare le proprie funzionalità, e il ciclo di vita della promise dipende *unicamente* dalla sua resolve o reject.


`async function getSomething() {
  try {
    const data = await url('MIOURL');
    return data;
  } catch (error) {
    console.error(error);
  }
}`

In altre parole, con **async** creiamo una sorta di "thread" parallelo al nostro programma, in cui tutto ciò che NON è async, fa parte de thread principale. 

Utilizzando `await` invece faccio sì che la funzione asincrona torni ad essere sincrona, quindi il programma ne **aspetterà** la risposta.

## 110. Rest API?
Stile architetturale per sistemi distribuiti. Rappresenta un sistema di trasmissione di dati su http, i sistemi Rest non prevedono il concetto di sessione, ovvero sono stateless. 

## 111. Cos'è la fetch?
Fetch è un'API JavaScript moderna utilizzata per effettuare richieste di rete (HTTP) e recuperare risorse, come dati da un server. Effettua richieste asimcrone. Le fetch restituiscono un promise che risolve la risposta della richiesta, supporta i vari metodi del HTTP (GET, POST,PUT,DELETE), gestisce ancje diversi formati di dati. 

## 112. ViewBag cos'è?
ViewBag è un oggetto dinamico fornito dal framework ASP.NET MVC (e ASP.NET Core) che consente di passare dati dalla controller alla view senza dover definire un modello fortemente tipizzato. È utile per inviare dati temporanei o informazioni che non giustificano la creazione di un modello completo.

## 113. Cosa sono i cookies e le session?
Per cookie  intendiamo una riserva nella memoia, un piccolo storage composto da elementi chiave-valore. Viene emesso dal client, tuttavia è il server che dice al client come è fatto il cookie (gli fornisce la "ricetta"). La sessione invece è la sessione di comunicazione al server.

## 114. Che cos'è RAZOR?
Razor è un **template engine**, cioè è un sistema che prende delle strutture comuni e le restituisce all'utente, cioè ci aiuta a creare delle pagine dinamiche HTML. 

## 115. Che cos'è un Form?
Elemento HTML che permette il trasferimento di stato, definibile come un tag HTML per il trasferimento di dati. Può fare solamente **get** e **post**, in maniera **sincrona**. 
`<form method="POST" asp-controller:"cliente" asp-action="salva">`

`<div class="mt-3">`

`<label class="form-label"> Nome: </label>`

`<input type="text" class="form-control" asp-for="Nome"/>`

`</div>`

`</form>`

## 116. Cosa sono i tipi union in typescript?

## 117. Che cos'è un component in Angular? E come si genera un component?
`ng generate new component component/component` (in cui il comando prima della slash è il nome della cartella e quello dopo il nome della cartella è il nome del file.

Tripla di file composta da un file typescript (che corrisponde al controller MVC), la parte di visualizzazione e il suo CSS.

## 118. Che cos'è una callback?
Evento che viene attivato quando qualcuno ci risponde. Cioè, secondo l'architettura client-server, per ogni richiesta del client riceve una risposta del server, la callback è ciò che viene attivato quando arriva una risposta.




---

## stringa di comando per fare push
git remote add origin https://github.com/acelilli/iemme_q.git

git branch -M main

git push -u origin main
