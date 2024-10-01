## Che cos'è una classe astratta?
In generale, una classe si può definire come una aggregazione di metodi e attributi. 

Una classe astratta è una classe che non può essere istanziata. È un'astrazione, una sorta di stampo che contiene attributi e metodi che verranno poi ereditati dalle sue sottoclassi. Una classe astratta viene ESTESA da una sottoclasse.

Un metodo astratto è un metodo SENZA CORPO che deve essere necessariamente essere ereditato da una sottoclasse tramite la parola chiave OVERRIDE che ci permette di riscrivere il metodo nella sottoclasse.

## Che cos'è la classe Object?
Object è la **superclasse** dalla quale derivano tutte le entità.

## Che cos'è la firma?
È il modo con cui un metodo può essere richiamato. Due metodi non possono avere la stessa firma sebbene possano chiamarsi allo stesso modo. Le firme devono essere necessariamente diverse (cioè avere parametri diversi). Quando esistono dei metodi che hanno lo stesso nome ma firme diverse si dice che si sta facendo un OVERLOAD di parametri.

## Che cos'è una lista?
Una lista risolve il problema degli array statici: è una raccolta di dati che possono anche non essere dello stesso tipo, la lunghezza della lista è variabile, ogni elemento al suo intero potrà quindi occupare spazi non sequenziali in memoria. 

## Che cos'è un array?
Un array è una raccolta di dati omogenea e statica. Cioè un array ha lunghezza fissa (quindi occupa un certo spazio in memoria) e al suo interno i dati sono tutti dello stesso tipo.

## Se scrivo IEsempio"<"T">"?
In `IEsempio<T>` IEsempio rappresenta un'interfaccia, mentre `<T>` rappresenta un tipo di dato generico, cioè che potrà in seguito essere sostituito con qualsiasi altro tipo (es. una classe) a mia scelta.
L'elemento interfaccia è un costrutto che contiene esclusivamente dei metodi senza corpo. È in realtà un elenco di metodi senza corpo quindi tecnicamente non è una classe, ci dice esclusivamente cosa si è **costretti** ad implementare a livello di metodi. Al suo interno quindi **non** ci sono attributi.
Un'interfaccia viene **implementata**.

## Che cos'è il tipo generico e a cosa serve?

## Che cos'è static?
Può essere attributo o metodo di classe che, quando associato alla parola chiave **static**, indica una proprietà o attributo allocato immediatamente all'inizio del programma: non avrà quindi bisogno dell'istanza di una classe per essere richiamato. Un esempio di metodo static è il *main* che rappresenta l'inizio del proramma.

## Concetto di information hiding e incapsulamento
Con il concetto di incapsulamento intendiamo dire che tutto ciò che appartiene ad una classe viene descritto al suo interno. 

È buona norma non far acceder direttamente gli utenti agli attributi di una classe, quindi utiliziamo i modificatori di accesso (public, private) consentendo il loro accesso solo tramite i metodi get e set, filtrando il dato in entrata e il dato in uscita. 

Con *private* posso quindi nascondere i dettagli costruttivi (attributi, metodi, filtri) della mia classe (e quindi delle sue istanze), questo è il concetto di information hiding.

## Che cos'è ToString()?
È un metodo predefinito appartenente alla classe Object che restituisce una stringa che ci dice il tipo dell'oggetto per il quale lo invochiamo.

## Che cosa vuol dire override?

## Che cos'è una stored procedure?
Una stored proedure è un innesto di linguaggo di programmazione che ci permette di fare DDL (es. con le tablle temporanee), DML e QL.

## Principi SOLID
Sono regole che devono sempre eseguite quando si sviluppa un nuovo software.Sono principi di web coding


**S** : *Single Responsibility Principle*: il principio di singola responsabilità afferma che ogni classe dovrebbe avere una ed una sola responsabilità, interamente incapsulata al suo interno.


**O**: *Open/closed principle*: un'entità software dovrebbe essere aperta alle estensioni, ma chiusa alle modifiche. Ovvero principio di estendibilità, quindi, in un certo senso, contiene anche l'ereditarietà.


**L**: *Liskov substitution principle*: secondo il principio di sostituzione di Liskov gli oggetti devono poter essere sostituiti con dei sottotipi senza alterare il comportamento che li caratterizza. 
(polimorfismo)


**I**: *Interface integration principle*: cioè è preferibile l’implementazione di  più interfacce specifiche che non di una più grande e generica. 


**D**: *Dependency inversion principle*:  una classe dovrebbe dipendere dall’astrazioni e non da classi concrete. 


## Definizione di polimorfismo:
In una situazione di ereditarietà, per polimorfismo si intende la capacità di un oggetto di trasformarsi, cioè di modificare il tip della sua istanza, in questo caso si SPECIALIZZA. Questo procedimento si chiama BINDING DINAMICO. Per esempio quando istanziamo una superclasse Persona e specializziamo il suo oggetto nella sottoclasse Studente:

`Persona per = new Studente();`

In pratica stiamo sfruttando la capacità della superclasse di trasformarsi un una delle sue specifiche sottoclassi. Potremmo sfruttare il polimorfismo per, per esempio, per creare una lista di oggetti eterogenei.

Si può utilizzare il polimorfismo in tutti i casi di ereditarietà, ad esempio abbiamo due tipi di polimorfismo: polimorfismo di classe e polimorfismo di interfaccia.

## Che cos'è il binding dinamico?
Quando l’istanza di una classe madre si specializza nel tipo della classe figlia. Il binding dinamico avviene solo all'avvio del programma.

## Cos’è LINQ?
Language Integrate Query serve per inerrogare le strutture di dati attraverso .Net con una sintassi simile a quella di SQL.

Cioè è una funzionalità di .NET che consente di eseguire query su diverse fonti in modo uniforme integrando la sintassi delle query direttamente nel linguaggio di programmazione. Grazie a LINQ possiamo interrogare i dati del database. 

## Cos’è il dbset ?
È un contenitore di tuple, la tupla è un riga (un record). 

## Cos’è il singleton?
E’ un parttern di programmazione che garantisce la creazione di una singola istanza fornisce un accesso globale a essa.

## Cos’è una Stored Procedure?
Una stored procedure è un innesto di linguaggio di programmazione che ci permette di fare DML , QL.

## Cos'è lo using ?
Lo using alloca variabili all'interno del suo contesto dette disposable, cioè alla sua conclusione grazie al garabage collector vengono eliminate dalla memoria. 

## Cos’è il BCL?
Il BCL (Base Class Library) è una parte fondamentale del framework .NET che offre un'ampia gamma di classi e metodi per supportare lo sviluppo di applicazioni, consentendo agli sviluppatori di risparmiare tempo e sforzo grazie alla disponibilità di funzionalità già pronte e testate.

## Cosa sono le proprerties? 
Sono un costrutto utile per gestire l’accesso e la modifica degli attributi di un oggetto in modo controllato, facilitando l’incapsulamento. Questi forniscono i metodi get e set per accedere e modificare i valori dei campi privati.

## Qual è la differenza tra un classe e un oggetto?
la classe è come un progetto o un modello che stabilisce come dovrebbe essere un oggetto, mentre l'oggetto è l'effettiva realizzazione di quel modello, con caratteristiche e dati specifici. Un oggetto può essere una variabile che basa la sua esistenza su una classe.

## Com’è fatta una classe ?
Si può definire come una aggregazione di metodi e attributi. A livello di progettazione abbiamo:

- Strutture che immagazzinano i dati (attributi)
- Funzionalità (metodi)

## Cos’è un attributo?
È la proprietà di un oggetto adibita all'immagazinamento dei dati.

## Cos’è un metodo ? 
È un sottoprogramma o una funzione che esegue delle operazioni.

## Definizione di Foreign Key e a cosa serve?
La foreign key, o il **VINCOLO DI INTEGRITÀ RELAZIONALE** è una chiave di riferimento ad una tabella esterna, sottoforma numerica. Serve a garantire l'integrità e la coerena dei dati  tra le due tabelle.
- Una foreing key **non può** essere null;
- Una foreign key **non può** fare riferimento ad una chiave primaria che non esiste.
  
Una foreign key è un **CONSTRAINT** cioè *impone un vincolo di controllo* su una colonna di associazione.

Per assicurare la coerenza dei dati, all'eliminazione di un record dalla tabella alla quale fa riferimento la foreign key, possiamo utilizzare la dicitura `ON DELETE CASCADE`.

## Che cos'è lo scaffolding?
È la traduzione della tabella in una classe. 

## Che cos'è l'ORM?
**ORM** = Object Relational Mapping, garantito o effettuato dall'entity framework. Cea un collegamento diretto tra le tabelle che si trovano nel database e i loro record. In altre parole: se una classe genera degli oggetti, gli oggetti sono a loro volta collegati alle *righe* delle tabelle. Quindi, creando un nuovo oggetto, creerò un nuovo record!

## Perché, all'interno di una classein C# che contiene delle foreign key, l'attributo public virtual MiaClasseRifNavigation? è nullable?
`public virtual MiaClasseRifNavigation? {get; set}` 


---

## stringa di comando per fare push
git remote add origin https://github.com/acelilli/iemme_q.git

git branch -M main

git push -u origin main
