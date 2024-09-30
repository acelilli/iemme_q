## Che cos'è una classe astratta?
Una classe si può definire come una aggregazione di metodi e attributi. Una classe astratta è una classe che non può essere istanziata. È un'astrazione, una sorta di stampo che contiene attributi e metodi che verranno poi ereditati dalle sue sottoclassi. Una classe astratta viene ESTESA da una sottoclasse.
Un metodo astratto è un metodo SENZA CORPO che deve essere necessariamente essere ereditato da una sottoclasse tramite la parola chiave OVERRIDE che ci permette di riscrivere il metodo nella sottoclasse.

## Che cos'è la classe Object?
Object è la superclasse dalla quale derivano tutte le entità.

## Che cos'è la firma?
È il modo con cui un metodo può essere richiamat. Due metodi non possono avere la stessa firma sebbene possano chiamarsi allo stesso modo. Le firme devono essere necessariamente diverse (cioè avere parametri diversi). Quando esistono dei metodi che hanno lo stesso nome ma firme diverse si dice che si sta facendo un OVERLOAD di parametri.

## Che cos'è una lista?
Una lista risolve il problema degli array statici: è una raccolta di dati ch possono anche non essere delo stesso tipo e la lunghezza della lista è variabile.

## Che cos'è un array?
Un array è una raccolta di dati omogenea e statica. Cioè un array ha una lunghezza fissa e al suo interno i dati sono tutti dello stesso tipo.

## Se scrivo IEsempio"<"T">"?
IEsempio è un'interfaccia. "<"T">" rappresenta un tipo di dato generico.
L'elemento interfaccia è un costrutto che contiene esclusivamente dei metodi senza corpo. È in realtà un elenco di metodi senza corpo quindi tecnicamente non è una classe, ma ci dice esclusivamente cosa si è costretti ad implementare a livello di metodi Al suo interno quindi NON ci sono attributi.
Un'interfaccia viene IMPLEMENTATA.

## Che cos'è static?
Può essere attributo o metodo di classe.

## Che cos'è un metodo statico?
È un metodo che non ha bisogno dell'istanza di una classe per essere richiamato I metodi static vengono allocati immediatamente all'inizio del programma. Un esempio di metodo static è il MAIN che rappresenta l'unizio del mio programma.

## Concetto di information hiding e incapsulamento
Con il concetto di incapsulamento intendiamo dire che tutto ciò che appartiene ad una classe viene descritto al suo interno. È buona norma non far acceder direttamente gli utenti agli attributi di una classe, quindi utiliziamo i modificatori di accesso (public, private) consentendo il loro accesso solo tramite i metodi get e set, che permettono di filtrare il dato in entrata e il dato in uscita. Con private posso quindi nascondere i dettagli costruttivi (attributi, metodi, filtri) della mia classe (e quindi delle sue istanze), questo è il concetto di information hiding.

## Che cos'è ToString()?
È un metodo predefinito appartenente alla classe Object che restituisce una stringa che ci dice il tipo dell'oggetto per il quale lo invochiamo.

## Che cosa vuol dire override?

## Che cos'è una stored procedure?
Una stored proedure è un innesto di linguaggo di programmazione che ci permette di fare DDL (es. con le tablle temporanee), DML e QL.

## Principi SOLID
Sono regole che devono sempre eseguite quando si sviluppa un nuovo software.Sono principi di web coding


S : single responsability principle principio di singola responsabilità .


O: Open close ovvero principio di estendibilità cioè l’ereditarietà 


L Liskov  ovvero gli oggetti devono poter essere sostituiti con dei sottotipi senza alterare il comportamento che li caratterizza. 
(polimorfismo)


I Interface integration principle cioè è preferibile l’implementazione di  più interfacce specifiche che non di un generica 


D Dependency Invertion  una classe dovrebbe dipendere dall’astrazioni e non da classi concrete. 


## Definizione di polimorfismo:
In una situazione di ereditarietà, per polimorfismo si intende la capacità di un oggetto di trasformarsi, cioè di modificare il tip della sua istanza, in questo caso si SPECIALIZZA. Questo procedimento si chiama BINDING DINAMICO. Per esempio quando istanziamo una superclasse Persona e specializziamo il suo oggetto nella sottoclasse Studente:

Persona per = new Studente();

In pratica stiamo sfruttando la capacità della superclasse di trasformarsi un una delle sue specifiche sottoclassi. Potremmo sfruttare il polimorfismo per, per esempio, per creare una lista di oggetti eterogenei.

Si può utilizzare il polimorfismo in tutti i casi di ereditarietà, ad esempio abbiamo due tipi di polimorfismo: polimorfismo di classe e polimorfismo di interfaccia.

## Che cos'è il binding dinamico?
Quando l’istanza di una classe madre si specializza nel tipo della classe figlia. Il binding dinamico avviene solo all'avvio del programma.

## Cos’è LINQ?
Language Integrate Query è una funzionalità di .NET che consente di eseguire query su diverse fonti in modo uniforme. Integra la sintassi delle query direttamente il linguaggio di programmazione.  (posso interrogare e trasformare??? i dati ). 


## Cos’è il dbset ?
È un contenitore di tuple, la tupla è un riga (un record). 

## Cos’è il singleton?
E’ un parttern che garantisce che abbia la creazione di una singola istanza e fornisca un accesso globale a essa.


## Cos’è una Stored Procedure?
Una stored procedure è un innesto di linguaggio di programmazione che ci permette di fare DML , QL.

## Cos'è lo using ?
Lo using alloca variabili all'interno del suo contesto dette disposable, cioè alla sua conclusione grazie al garabage collector vengono eliminate dalla memoria. 


## Cos’è il BCL?
Il BCL (Base Class Library) è una parte fondamentale del framework .NET che offre un'ampia gamma di classi e metodi per supportare lo sviluppo di applicazioni, consentendo agli sviluppatori di risparmiare tempo e sforzo grazie alla disponibilità di funzionalità già pronte e testate.


## Cosa sono le proprerties? 
Sono un costrutto utile per gestire l’accesso e la modifica degli attributi di un oggetto in modo controllato, facilitando l’incapsulamento. Questi forniscono i metodi get e set per accedere e modificare i valori dei campi privati.

## Qual è la differenza tra un classe e un oggetto?
la classe è come un progetto o un modello che stabilisce come dovrebbe essere un oggetto, mentre l'oggetto è l'effettiva realizzazione di quel modello, con caratteristiche e dati specifici.


## Com’è fatta una classe ?
Si può definire come una aggregazione di metodi e attributi. 


## Cos’è un attributo?
È la proprietà di un oggetto



## Cos’è un metodo ? 
È un sottoprogramma o una funzione che esegue delle operazioni.



## stringa di comando per fare push
git remote add origin https://github.com/acelilli/iemme_q.git

git branch -M main

git push -u origin main
