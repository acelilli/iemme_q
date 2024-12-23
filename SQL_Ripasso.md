## Database SQL e il suo linguaggio.
Un **database** è un archivio di dati che ci permette di gestire la PERMANENZA dei dati. Senza il db tutti i dati vengono normalmente salvati sulla ram come memoria VOLATILE, cioè una volta chiusa la nostra applicazione spariscono. In altre parole, un database è un gigantesco file dove vengono salvati dei dati. Il DATABASE FILE, deve essere *frazionato*, cioè tutti i dati di un certo tipo devono essere ravvicinati. La sua organizzazione è direttamente connessa all’azienda che lo va a sviluppare.


Invece il dbms, cioè il **database management system** è il processo che riesce a gestire il db file. Per esempio SSMS, MySql, Apache…L’ unico modo che abbiamo per interagire con un database è tramite un DBMS. Più o meno tutti i dbms utilizzano circa lo stesso linguaggio, tuttavia hanno dei ‘dialetti’ che li differenziano tra loro, e ogni parte del linguaggio è divisa per *competenze*. Ad esempio abbiamo:
- **DDL** : *Data Definition Language* ⇒ Quando dobbiamo effettuare delle operazioni di salvataggio di dati, creiamo prima di tutto una struttura, a questo serve il DDL. Serve a gestire LO SCHEMA. Lo schema è la parte invariante del database (o meglio, cambia con una cadenza molto lenta) quindi è l’istanza del database.
*Es.:*
  ```sql
   CREATE DATABASE ilMioDb; 
  
  USE ilMioDb;

  CREATE TABLE MiaTabella(
  dato VARCHAR(250) NOT NULL
  );
  
  DROP TABLE MiaTabella;
  DROP DATABASE ilMioDb;

- **DML** : *Data Manipulation Language* ⇒ inserisce, modifica, elimina, insomma manipola i dati già creati nelle strutture.
*Es.:*
```sql
  INSERT INTO patients(first_name, last_name, allergies. weight)
  VALUES('Mario', 'Rossi' , null, 110);

  UPDATE patients
  SET allergies = 'NKA'
  WHERE allergies IS NULL;

  DELETE FROM MyTable WHERE first_name = 'Mario' AND last_name = 'Rossi' AND cf = 'RSSMRO12345'
```
- **QL** : *Querying language* ⇒ tutto ciò che serve per leggere i dati ed estrarre nuove informazioni.
*Es.:*
```sql
  SELECT first_name, last_name, gender
  FROM patients
  WHERE gender = 'M';

  SELECT first_name, last_name
  FROM patients
  WHERE allergies IS null;

  SELECT first_name
  FROM patients
  WHERE first_name
  LIKE 'C%';

  SELECT first_name, last_name
  FROM patients
  WHERE weight BETWEEN 100 AND 120;
```
