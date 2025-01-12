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

### Indice, Join, Transaction e Group by
