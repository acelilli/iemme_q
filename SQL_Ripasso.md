## Database SQL e il suo linguaggio.
Un **database** è un archivio di dati che ci permette di gestire la PERMANENZA dei dati. Senza il db tutti i dati vengono normalmente salvati sulla ram come memoria VOLATILE, cioè una volta chiusa la nostra applicazione spariscono. In altre parole, un database è un gigantesco file dove vengono salvati dei dati. Il DATABASE FILE, deve essere *frazionato*, cioè tutti i dati di un certo tipo devono essere ravvicinati. La sua organizzazione è direttamente connessa all’azienda che lo va a sviluppare.


Invece il dbms, cioè il **database management system** è il processo che riesce a gestire il db file. Per esempio SSMS, MySql, Apache…L’ unico modo che abbiamo per interagire con un database è tramite un DBMS. Più o meno tutti i dbms utilizzano circa lo stesso linguaggio, tuttavia hanno dei ‘dialetti’ che li differenziano tra loro, e ogni parte del linguaggio è divisa per *competenze*. Ad esempio abbiamo:
- **DDL** : *Data Definition Language* ⇒ Quando dobbiamo effettuare delle operazioni di salvataggio di dati, creiamo prima di tutto una struttura, a questo serve il DDL. Serve a gestire LO SCHEMA. Lo schema è la parte invariante del database (o meglio, cambia con una cadenza molto lenta) quindi è l’istanza del database.
*Es.:*
  ```sql
  -- Crea il database 'ilMioDb'
   CREATE DATABASE ilMioDb; 

  -- Usa il database 'ilMioDb' (ogni operazione da ora verrà datta sul db)
  USE ilMioDb;

  -- Crea la tabella MiaTabella
  CREATE TABLE MiaTabella(
  dato VARCHAR(250) NOT NULL
  );

  -- Cancella la tabella
  DROP TABLE MiaTabella;

  -- Cancella il database
  DROP DATABASE ilMioDb;

- **DML** : *Data Manipulation Language* ⇒ inserisce, modifica, elimina, insomma manipola i dati già creati nelle strutture.
*Es.:*
  ```sql
  -- Inserisci dei valori all'interno della tabella pazienti
  INSERT INTO patients(first_name, last_name, allergies, weight)
  VALUES('Mario', 'Rossi' , null, 110);

  -- Aggiorna i valori della colonna arrergie dove il valore è null con 'NKA'
  UPDATE patients
  SET allergies = 'NKA'
  WHERE allergies IS NULL;

  -- Cancella dalla tabella il record che ha come nome 'Mario', come cognome 'Rossi' e come CF 'RSSMRO12345'
  DELETE FROM MyTable WHERE first_name = 'Mario' AND last_name = 'Rossi' AND cf = 'RSSMRO12345'
  ```
- **QL** : *Querying language* ⇒ tutto ciò che serve per leggere i dati ed estrarre nuove informazioni.
*Es.:*
  ```sql
  --Seleziona tutti i pazienti
  SELECT * FROM patients;

  -- Seleziona nome, cognome e genere dei pazienti in cui il genere è M
  SELECT first_name, last_name, gender
  FROM patients
  WHERE gender = 'M';

  -- Seleziona nome e cognome dei pazienti dove il valore delle allergie è nullo
  SELECT first_name, last_name
  FROM patients
  WHERE allergies IS null;

  -- Seleziona il nome dei pazienti dove la prima lettera del nome è 'C'
  SELECT first_name
  FROM patients
  WHERE first_name
  LIKE 'C%';

  -- Seleziona nome e cognome dei pazienti dove il peso è tra 100 e 120
  SELECT first_name, last_name
  FROM patients
  WHERE weight BETWEEN 100 AND 120;

  -- Seleziona nome e cognome dei pazienti in un'unica colonna chiamata full_name
  SELECT CONCAT(first_name,' ', last_name) AS full_name
  FROM patients;
  ```
  
***N.B.:** Nel caso delle select, possiamo parlare di **PROIEZIONE**. Cioè una sorta di *filtro* che crea una tabella ‘virtuale’ dove vengono depositati i dati della ricerca che sta venendo effettuata. In pratica si riferisce al processo di selezionare determinate colonne da una tabella, escludendone altre. Parliamo di proiezione verticale quando selezioniamo le colonne di una tabella (es.: ` SELECT first_name, last_name, gender FROM patients`) mentre parliamo di proiezione orizzontale quando ci riferiamo ad alcuni dati specifici dei record (es.:` SELECT first_name, last_name, gender FROM patients WHERE gender = 'M'`)

---

### Vincoli interni ed esterni
**Vincoli interni** anche detti *vincoli intrinsechi* si intendono i *tipi di dato* che specifichiamo per le nostre colonne. Anche la nullability, la UNIQUE, il valore default e il check fanno parte di questa categoria. Ad esempio, quando dichiariamo una tabella:

```sql
CREATE TABLE MiaTabella(
  idUtente INT PRIMARY KEY IDENTITY(1,1),
  nome VARCHAR(250) NOT NULL,
  eta INT NOT NULL CHECK(eta >= 18),
  CF CHAR(16) NOT NULL UNIQUE,
  utenza_attiva BIT DEFAULT 0
  );
```

**NB.:** Il check può essere definito non direttamente sulla stessa riga nella quale definiamo la colonna, ad esempio per una gestione migliore.

```sql
CREATE TABLE MiaTabella(
  idUtente INT PRIMARY KEY IDENTITY(1,1),
  nome VARCHAR(250) NOT NULL,
  eta INT NOT NULL,
  CF CHAR(16) NOT NULL UNIQUE,
  utenza_attiva BIT DEFAULT 0
  CONSTRAINT CHK_eta CHECK(eta >=18)
  );
```

**Vincoli esterni** anche detti *vincoli relazionali* regolano i collegamenti tra tabelle diverse e servono a mantenere l'integrità referenziale. Sono quindi vincoli esterni la foreign key, l'ON DELETE/ON UPDATE CASCADE/SET NULL/RESTRICT/NO ACTION.

```sql
CREATE TABLE MiaTabellaDocumenti(
  idDoc INT PRIMARY KEY IDENTITY(1,1),
  contenuto_doc VARCHAR(MAX) NOT NULL,
  idUtente_FK INT NOT NULL,
  FOREIGN KEY (idUtente_FK) REFERENCES MiaTabella(idUtente) ON DELETE CASCADE
  UNIQUE(idDoc, idUtente)
);
```
**N.B.:** Nello specifico:
- La foreign key, o il **VINCOLO DI INTEGRITÀ RELAZIONALE** è una chiave di riferimento ad una tabella esterna, sottoforma numerica. Serve a garantire l'integrità e la coerena dei dati  tra le due tabelle. Una foreign key quindi **non può** essere null e **non può** fare riferimento ad una chiave primaria che non esiste. Possiamo definirla come una **CONSTRAINT** cioè *impone un vincolo di controllo* su una colonna di associazione.
- Tramite `ON DELETE CASCADE` specifichiamo che quando un record nella tabella referenziata (MiaTabella) viene eliminato, allora anche i record associati nella tabella MiaTabellaDocumenti verranno eliminati automaticamente.
- Con `UNIQUE(idDoc, idUtente)` assicuriamo che non ci siano duplicati nella combinazione di un certo idDoc con un idUtente.

---

### Relazioni tra tabelle
Le relazioni tra tabelle possono essere di tra tipi e ciascuna relazione che intercorre tra due elementi deve avere un nome.

- Uno ad uno ⇒ Un record in una tabella è associato ad uno ed un solo record in un'altra tabella, e viceversa. Es.: Una persona possiede un codice fiscale.
  ```sql
  CREATE TABLE Persone (
    idPersona INT PRIMARY KEY,
    nome VARCHAR(100) NOT NULL
  );

  CREATE TABLE CodiciFiscali (
    idCodiceFiscale INT PRIMARY KEY,
    codice_fiscale CHAR(16) NOT NULL UNIQUE,
    idPersona_FK INT UNIQUE, 
    FOREIGN KEY (idPersona_FK) REFERENCES Persone(idPersona) ON DELETE CASCADE
  );
  ```
- Uno a molti ⇒ Un record in una tabella può essere associato ad uno o più record in un'altra tabella, ma un record nella seconda tabella può essere associato solamente ad un record nella prima tabella. Es.: Una persona può possedere una o più carte fedeltà. Ma una carta fedeltà può essere posseduta solo da una persona.
  ```sql
  CREATE TABLE Persone (
    idPersona INT PRIMARY KEY,
    nome VARCHAR(100) NOT NULL
  );

  CREATE TABLE CarteFedelta (
    idCarta INT PRIMARY KEY,
    numero_carta VARCHAR(50) NOT NULL UNIQUE,
    idPersona_FK INT NOT NULL,
    FOREIGN KEY (idPersona_FK) REFERENCES Persone(idPersona) ON DELETE CASCADE
  );
  ```
- Molti a molti ⇒ Un record in una tabella può essere associato a uno o più record in un'altra tabella e viceversa. Questo tipo di relazione necessita di una *tabella di associazione* (per rispettare il principio della normalizzazione del dato). Es.: Uno studente può essere iscritto a uno o più corsi. Un corso può avere uno o più studenti iscritti (la *tabella di associazione* potrà essere 'Iscrizioni').
   ```sql
  CREATE TABLE Studenti (
    idStudente INT PRIMARY KEY,
    nome VARCHAR(100) NOT NULL
  );

  CREATE TABLE Corsi (
    idCorso INT PRIMARY KEY,
    nome_corso VARCHAR(100) NOT NULL
  );

  CREATE TABLE Iscrizioni (
    idStudente_FK INT NOT NULL,
    idCorso_FK INT NOT NULL,
    UNIQUE (idStudente_FK, idCorso_FK), -- Chiave ELETTA*
    FOREIGN KEY (idStudente_FK) REFERENCES Studenti(idStudente) ON DELETE CASCADE,
    FOREIGN KEY (idCorso_FK) REFERENCES Corsi(idCorso) ON DELETE CASCADE
  );
  ```

**NB.:** In un database relazionale vige la regola della *normalizzazione del dato*. Ciò vuol dire che la molteplicità di dati all'interno di una cella **non è tollerata**. Ogni cella contiene un solo valore.

* **Chiave Eletta** ⇒ o anche detta *chiave candidata*, in assenza di una primary key definita la chiave eletta si occupa di identificare univocamente i record. Può venire utilizzata quando la nostra tabella *non* necessita di un identificatore principale (primary key).
  
---

### Indice, JOIN, GROUP BY

### 1. Indice
Avere un indice riduce il tempo necessario per la ricerca di un record specifico nelle nostre tabelle e nel loro ordinamento, sono quindi molto utili anche nel processo delle Join tra tabelle.
Nell'ambito SQL abbiamo diversi tipi di indici:
- Indice primario: quando definiamo una **Primary Key** nella nostra tabella. Questo indice è unico per ciascun record, quindi lo identifica univocamente.
- Indice unico: non necessariamente legato alla primary Key, ad esempio una chiave eletta con UNIQUE può essere un indice unico.
- Indice non univoco: richiedono che i valori di una data colonna siano unici, vengono utilizzati per migliorare le prestazioni delle query che non richiedono unicità.
  ```sql
  CREATE INDEX idx_nome
  ON Persone (nome);

  --Gli indici possono anche venire cancellati
  DROP INDEX idx_nome ON Persone;
  ```
- Indice composto: è un indice che include più colonne. Utile quando le query utilizzano più colonne in una WHERE o in un ORDER BY. L'ordine delle colonne nell'indice è importante.
   ```sql
   CREATE INDEX idx_nome_eta
   ON Persone (nome, eta); 
  ```
Negli ultimi due casi in particolare, l'indice rappresenta una tabella indipendente che viene generata  separatamente dalle altre, tuttavia resta una tabella puramente virtuale: possiamo visualizzarla ma non modificarla.

Possiamo quindi fare un'ulteriore distinzione tra:
- **Clustered Index**: l'organizzazione della tabella è basata sull'indice. L'indice viene creato automaticamente quando viene definita una Primary Key.
- **Non-Clustered Index**: l'indice non modifica l'ordine fisico della tabella, mantiene una struttura separata (es.: l'indice `idx_nome` e quello `idx_nome_eta`)

#### 2. JOIN
Ci sono diversi tipi di Join. Tra cui:
- Inner join ⇒ Il risultato mostrerà solo ciò che é in comune tra le due tabelle. I record che non sono corrispondenti verranno esclusi dal risultato. Es.:
  ```sql
  SELECT Persone.nome, CarteFedelta.numero_carta
  FROM Persone
  INNER JOIN CarteFedelta
  ON Persone.idPersona = CarteFedelta.idPersona_FK;

  -- Il risultato mostrerà il nome della persona e il numero della carta solo delle persone che possiedono una carta fedeltà.
  ```
  
- Left join ⇒ Il risultato mostrerà ciò che é in comune più tutto ciò che si trova nella tabella di partenza. Cioè tutti i record della tabella prima del FROM e i record corrispondenti della tabella di destra. Se non ci sono corrispondenze, i valori della tabella di destra verranno visualizzati come NULL. Es.:
  ```sql
    SELECT Persone.nome, CarteFedelta.numero_carta
    FROM Persone
    LEFT JOIN CarteFedelta
    ON Persone.idPersona = CarteFedelta.idPersona_FK;
  
    -- Il risultato mostrerà tutti i nomi della tabella persone e tutte le carte fedeltà, se non esiste una carta per un record, il valore della cartà sarà NULL.
    ```
- Right join ⇒ Il risultato mostrerà ciò che è in comune più ciò che si trova nella tabella non di partenza (quella dopo il JOIN), se non ci sono corrispondenze vengono restituiti i record della tabella di sinistra impostati su null. Es.:
  ```sql
  SELECT Persone.nome, CarteFedelta.numero_carta
  FROM Persone
  RIGHT JOIN CarteFedelta
  ON Persone.idPersona = CarteFedelta.idPersona_FK;

  -- Il risultato mostrerà la lista dei i nomi della tabella persone in cui appariranno dei valori null per tutte le carte fedeltà che non hanno un proprietario, e tutte le carte fedeltà.
  ```
- Full Outer join ⇒ Il risultato mostrerà tutti i dati tra le due tabelle, combinando i risultati di left e right join. In altre parole verranno mostrati sia i record corrispondenti che i record non corrispondenti da entrambe le tabelle.
  ```sql
  SELECT Persone.nome, CarteFedelta.numero_carta
  FROM Persone
  FULL OUTER JOIN CarteFedelta
  ON Persone.idPersona = CarteFedelta.idPersona_FK;

  -- Il risultato mostrerà tutti i dati tra le due tabelle, ove non ci sono corrispondenze i valori verranno impostati come null.
  ```

#### 3. GROUP BY, DISTINCT e HAVING.
Divide il risultato di una query (quindi una `SELECT`) in base ai valori di una o più colonne, eseguendo quindi delle aggregazioni di gruppi.
Può essere accostata anche ad altre operazioni (es. operazioni matematiche) per mostrare un certo risultato.
  ```sql
    SELECT città,
    FROM Persone
    GROUP BY città;
  
  -- Una query così descritta non è errata, però vedrei un elenco di città per quante volte ciascuna persona è registrata in una certa città. Potrei scrivere semplicemente:
  
  SELECT DISTINCT città
  FROM Persone;
  ```
**N.B.:**  `DISTINCT` restituisce valori unici da una colonna senza bisogno di fare un raggruppamento esplicito. In pratica, se ho bisogno solo di un elenco di valori unici, utilizziamo `DISTINCT`, altrimenti, se ho bisogno di fare dei calcoli devo utilizzare `GROUP BY`.

Per utilizzare correttamente `GROUP BY` possiamo associarlo a `COUNT()`.
```sql
SELECT città, COUNT(*) AS num_persone
FROM Persone
GROUP BY città
ORDER BY COUNT(*) DESC;

-- il risultato sarà una vista in cui ci una colonna sono le città, e l'altra colonna, chiamata num_persone, conta quanti record ci sono per ciascuna città (contando di fatto le persone) in ordine decrescente (più record a meno record).
```

**N.B.:** Non possono venire selezionate colonne che non verranno incluse nel `GROUP BY`.

Possiamo inoltre inserire la clausola `HAVING` per filtrare ulteriormente i gruppi. Da npotare che, mentre `WHERE` applica un filtro PRIMA che le operazioni vengano effettivamente compiute, la clausola `HAVING` viene applicata **dopo** le altre funzioni.
```sql
  SELECT colonna1, operazione(colonna2) AS nome_operazione
  FROM nome_tabella
  GROUP BY colonna1
  HAVING operazione(colonna2)

-- Esempio pratico:
  SELECT idVenditore, COUNT(venditaID) AS numero_vendite
  FROM Vendite
  GROUP BY idVenditore
  HAVING COUNT(venditaID) > 2;

-- Il risultato sarà una colonna che mostra l'idVenditore e una colonna in cui viene indicato il numero totale delle sue vendite registrate.
```

`HAVING` può essere anche utilizzato assieme al  `WHERE` nel caso di operazioni particolari.
```sql
  SELECT idVenditore, COUNT(venditaID) AS numero_vendite, SUM(importo) AS totale_vendite
  FROM Vendite
  WHERE importo > 50  
  GROUP BY idVenditore
  HAVING COUNT(venditaID) > 2 AND SUM(importo) > 500; 

-- Nel risultato vedremo:
  -- Tutti gli idVenditore che soddisfano i criteri
  -- Tutte le vendite in cui l'importo è maggiore di 50, raggruppate per idVenditore;
  -- Il numero delle vendite, cioè il numero delle vendite di ciascun venditore contando solo le vendite in cui l'importo è maggiore di 50;
  -- La somma dell'importo per ciascun venditore (sempre considerando solo i maggiori di 50);
```

---

### VIEW
Il comando `VIEW` genera una tabella virtuale della quale i contenuti vengono definiti dalla query (non possiamo effettuare modifiche, cancellare o inserire dati in o tramite una view). Una vista quindi **non esiste** sul nostro database, esegue unicamente delle operazioni di filtro sulle tabelle alle quali fa riferimento. 
```sql
  CREATE VIEW nome_view AS
  SELECT colonna1, colonna2, ...
  FROM miaTabella
  WHERE condizione;

  -- Esempio:
  CREATE VIEW Maggiorenni AS
  SELECT idPersona, nome, città
  FROM Persone
  WHERE eta >= 18;

  -- In seguito posso fare delle operazioni di visualizzazione su questa tabella virtuale:
SELECT * FROM Maggiorenni;

-- Posso inoltre cancellare una view:
DROP VIEW Maggiorenni;
```

Si possono creare delle viste ad esempio utilizzando delle JOIN:
```sql
CREATE VIEW VistaPersoneCarta AS
SELECT Persone.idPersona, Persone.nome, Persone.città, CarteFedelta.numero_carta
FROM Persone
JOIN CarteFedelta ON Persone.idPersona = CarteFedelta.idPersona_FK;

SELECT * FROM VistaPersoneCarte;
```

---

### Transactions
La TRANSACTION é un blocco di codice sicuro che raccoglie una o più operazioni. Le operazioni contenute all'interno del blocco della transaction avviengono prima a livello di ram (memoria non permanente) e, se tutto va a buon fine  vengono *committate* nel database, assicurando l’operazione nella memoria permanente. Se invece non vanno a buon fine viene eseguito il *ROLLBACK*, che farà tornare il database allo stato precedente, come se la transaction non fosse mai avvenuta.

In altre parole garantisce che tutte le operazioni al suo interno vengano eseguite come un'unità **atomica**: o tutte vengono completate correttamente oppure nessuna ha effetto. Per questo si dice che sia una **OPERAZIONE PRIORITARIA**: niente può intromettersi nell'esecuzione della transaction. 

Una transaction viene utilizata quando si devono eseguire dei blocchi di più operazioni che spesso dipendono l'una dall'altra o che coinvolgono una o più tabelle: in questo modo se la transizione si blocca o fallisce tutte le modifiche vengono annullate automaticamente, evitando che il database rimanga in uno stato incoerente. Senza le transazioni, ciascuna operazione è indipendente l'una dall'altra, quindi non vengono utilizzate per una singola operazione.

Una volta che una transazione è stata completata (committata) le modifiche sono permanenti, anche in caso di crash.(NB.: **Principi ACID** - Atomicità, Constenza, Isolamento, Durabilità).

Alla transaction possiamo abbinare il blocco `try-catch` per garantire più robustezza alle nostre operazioni.

```sql
-- Scheletro di una transaction:
BEGIN TRY
  BEGIN TRANSACTION
  -- Operazioni
  COMMIT;
END TRY
BEGIN CATCH
ROLLBACK;
  PRINT 'Errore durante la transazione. Tutte le modifiche sono state annullate'
END CATCH;

-- Esempio di una transaction
BEGIN TRY
  BEGIN TRANSACTION;  
  INSERT INTO Persone (nome, cognome, città)
  VALUES ('Mario', 'Rossi', 'Roma');
  INSERT INTO CarteFedelta (numero_carta, idPersona_FK)
  VALUES ('1234567890', 10);
  
  COMMIT;  -- Applica le modifiche in modo permanente se le operazioni vanno a buon fine
END TRY
BEGIN CATCH
  ROLLBACK;
  PRINT 'Errore durante la transazione. Tutte le modifiche sono state annullate'
END CATCH;
```

Dichiarare delle variabili può essere utile nel contesto di una transazione, ad esempio se vogliamo manipolare o calcolare dei valori durante una transazione senza doverli memorizzare nelle tabelle. Es.:
```sql
-- Semplice dichiarazione di una variabile in SQLServer:
DECLARE @miaVar VARCHAR(250) = 'Ciao' 
SELECT @miaVar;

-- Esempio di dichiarazione di una variabile e utilizzo all'interno di una transaction.
-- Trasferiamo un saldo da un conto (con id = 1) ad un altro (con id =2):
DECLARE @importoTransferito DECIMAL(10,2);
SET @importoTransferito = 100;

BEGIN TRY
  BEGIN TRANSACTION
    UPDATE ContiBancari
    SET saldo = saldo - @importoTransferito
    WHERE idConto = 1;

    UPDATE ContiBancari
    SET saldo = saldo + @importoTransferito
    WHERE idConto = 2;
  COMMIT;
END TRY
BEGIN CATCH
ROLLBACK;
  PRINT 'Errore durante la transazione. Tutte le modifiche sono state annullate'
END CATCH;
```
Possiamo inoltre rendere la struttura più solida con dei controlli if/else:
```sql
-- Utilizzanbdo la stessa struttura, controlliamo che nel conto con id = 1 ci sia abbastanza denaro. Quindi:
DECLARE @importoTransferito DECIMAL(10,2);
SET @importoTransferito = 100;

BEGIN TRY
  BEGIN TRANSACTION
    UPDATE ContiBancari
    SET saldo = saldo - @importoTransferito
    WHERE idConto = 1;

-- Verifichiamo che il saldo sia sufficente.
-- Se il saldo è minore di 0 allora facciamo rollback.
    IF(SELECT saldo FROM ContiBancari WHERE idConto = 1) < 0
      BEGIN
        ROLLBACK;
        PRINT 'Errore: saldo insufficiente';
      END
-- Se il saldo non è minore di 0 allora completiamo l'operazione sul conto 2:
    ELSE
      BEGIN
      UPDATE ContiBancari
      SET saldo = saldo + @importoTransferito
      WHERE idConto = 2;
    COMMIT;
END TRY
BEGIN CATCH
ROLLBACK;
  PRINT 'Errore durante la transazione. Tutte le modifiche sono state annullate'
  PRINT 'Dettagli errore:';
  PRINT ERROR_MESSAGE(); 
END CATCH;
```
---

### Stored Procedures
Creazione ed esecuzione di una Stored procedure semplice:
```sql
CREATE PROCEDURE NomeProcedura
AS
BEGIN
  -- Operazioni da eseguire
  SELECT * FROM NomeTabella;
END;

EXEC NomeProcedura;
```

Creazione ed esecuzione di una SP parametrica:
```sql
CREATE PROCEDURE NomeProceduraConParametri
  @Parametro1 INT,
  @Parametro2 VARCHAR(50)
AS
BEGIN
  -- Operazioni che usano i parametri
  SELECT * FROM NomeTabella WHERE Colonna = @Parametro1;
END;

-- Esecuzione della Stored Procedure con parametri
EXEC NomeProceduraConParametri 10, 'Test';
```

---
### Altre operazioni
  #### 1. COUNT, ORDER BY, operazioni matematiche e PRINT
  ```sql
  -- Utilizzo di COUNT e ORDER BY
  SELECT Colonna, COUNT(*)
  FROM NomeTabella
  GROUP BY Colonna
  ORDER BY COUNT(*) DESC;
  
  -- Operazioni matematiche
  SELECT Colonna1, Colonna2, (Colonna1 + Colonna2) AS Somma
  FROM NomeTabella;
  
  -- Uso di PRINT per messaggi
  PRINT 'Operazione completata';
  ```
  #### 2. NEWID()
  ```sql
  ```
  #### 3. CURSORE, FETCH e OFFSET
  //bozza dagli appunti disordinati
  Il CURSORE è un elemento che seleziona. Seleziona ogni singola riga, in altre parole, è un ciclo!
  Con OFFSET diciamo al cursore da dove partire. OFFSET 1 ROWS parte dalla seconda riga, OFFSET 2 ROWS partirà dalla terza ecc.
  ```sql
  -- Creazione di un cursore
  DECLARE NomeCursore CURSOR FOR
  SELECT Colonna
  FROM NomeTabella;
  
  -- Dichiarazione di una variabile per memorizzare il risultato del cursore
  DECLARE @Valore INT;
  
  -- Apertura del cursore
  OPEN NomeCursore;
  
  -- Iterazione sul cursore
  FETCH NEXT FROM NomeCursore INTO @Valore;
  WHILE @@FETCH_STATUS = 0
  BEGIN
    -- Operazioni da eseguire su ogni riga selezionata
    PRINT @Valore;
  
    -- Avanzamento alla riga successiva
    FETCH NEXT FROM NomeCursore INTO @Valore;
  END;
  
  -- Chiusura e deallocazione del cursore
  CLOSE NomeCursore;
  DEALLOCATE NomeCursore;
  ```

Possiamo utilizare offset per saltare delle righe:
```sql
SELECT *
FROM NomeTabella
ORDER BY Colonna
OFFSET 1 ROWS; -- Parte dalla seconda riga

-- Con FETCH per limitare il numero di righe
SELECT *
FROM NomeTabella
ORDER BY Colonna
OFFSET 2 ROWS
FETCH NEXT 5 ROWS ONLY; -- Recupera 5 righe dopo la terza
```
