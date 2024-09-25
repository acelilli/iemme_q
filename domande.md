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

## Se scrivo IEsempio<T>?
IEsempio è un'interfaccia. <T> rappresenta un tipo di dato generico.
L'elemento interfaccia è un costrutto che contiene esclusivamente dei metodi senza corpo. È in realtà un elenco di metodi senza corpo quindi tecnicamente non è una classe, ma ci dice esclusivamente cosa si è costretti ad implementare a livello di metodi Al suo interno quindi NON ci sono attributi.
Un'interfaccia viene IMPLEMENTATA.

## Che cos'è un metodo statico?
È un metodo che non ha bisogno dell'istanza di una classe per essere richiamato I metodi static vengono allocati immediatamente all'inizio del programma. Un esempio di metodo static è il MAIN che rappresenta l'unizio del mio programma.

## Concetto di information hiding e incapsulamento
Con il concetto di incapsulamento intendiamo dire che tutto ciò che appartiene ad una classe viene descritto al suo interno. È buona norma non far acceder direttamente gli utenti agli attributi di una classe, quindi utiliziamo i modificatori di accesso (public, private) consentendo il loro accesso solo tramite i metodi get e set, che permettono di filtrare il dato in entrata e il dato in uscita. Con private posso quindi nascondere i dettagli costruttivi (attributi, metodi, filtri) della mia classe (e quindi delle sue istanze), questo è il concetto di information hiding.

## Che cos'è ToString()?
È un metodo predefinito appartenente alla classe Object che restituisce una stringa che ci dice il tipo dell'oggetto per il quale lo invochiamo.

## Che cosa vuol dire override?

## CHe cos'è una stored procedure?
Una stored proedure è un innesto di linguaggo di programmazione che ci permette di fare DDL (es. con le tablle temporanee), DML e QL.

## stringa di comando per fare push
git remote add origin https://github.com/acelilli/iemme_q.git

git branch -M main

git push -u origin main
