# Esercitazione Wheretech

## Descrizione:

API Rest in Django per colloquio tecnico con Wheretech con utilizzo della libreria Rest-Framework.

diagramma:
## Requisiti:
- Python: Versione 3.11.9 e oltre.
- Pip: 25.0 e oltre.

## Installazione del Virtual Enviroment:

È consigliato l'utilizzo di un Virtual Enviroment per evitare conflitti con i pacchetti e librerie installati globalmente.

Eseguire i seguenti comandi da terminale dopo essersi posizionati nella caretella root della repository:

Generazione virtual enviroment nella cartella root sotto la cartella **venv**:

    python3 -m venv .venv

Attivare il Virtual Enviroment:

- per **Linux** e **MacOs**:

        source .venv/bin/activate

- per **Windows**:
    - in **Cmd**:

           venv\Scripts\activate.bat
    - in **PowerShell**:

               venv\Scripts\Activate.ps1

**N.B.** Per disattivare il Virtual Enviroment al termine delle operazioni, usare il comando:

    deactivate

## Installazione delle librerie nel Virtual Enviroment:
per installare le dipendenze richieste dalla WebApi rimanere nella cartella root ed eseguire i seguenti comandi:

- Aggiornare Pip:

        pip install -U pip

- Installare le dipendenze presenti nel file **requirements.txt**:

        pip install -r ./requirements.txt

## Avviare la WebApi:
Una volta aver attivato il Virtual Enviroment, recarsi da terminale nella cartella **demo** ed eseguire i seguenti comandi:

generazione del **DB** SQLite e prima migration:

    python3 manage.py migrate

avvio dell' applicazione:

    python3 manage.py runserver
    
## Riempire il db con dati fittizzi per farlo basta eseguire

    python3 manage.py populate_db
    
Esempio di chiamate possibili:

Cercare per titolo: Se vuoi cercare tutti i libri con il titolo che contiene la parola "Python", la query sarà:
- http://localhost:8000/api/libri/?titolo=Python

Cercare per nazionalità dell'autore: Se vuoi cercare i libri degli autori provenienti dalla "Italia", la query sarà:
- http://localhost:8000/api/libri/?autore__indirizzo__nazionalita=Italia

Cercare per titolo e nazionalità dell'autore: Se vuoi combinare entrambe le condizioni (ad esempio, libri con "Python" nel titolo e autori italiani), la query sarà:
- http://localhost:8000/api/libri/?titolo=Python&autore__indirizzo__nazionalita=Italia

si può utilizzare la documentazione fornita automaticamente da django in debug mode per effettuare query sui libri a gli indirizzi:
- http://localhost:8000/api/libri/
- http://localhost:8000/api/libri/ordinati

## Perché ho usato SQLite

Per una realizzazione veloce di questa un webapi ho ritenuto opportuno l'utilizzo del db fornito e supportato dal framework, altre implementazioni potrebbero favorire di un associazione a database non relazionale come MongoDB per la gestione di una mole ampia di libri, essendo i db non relazionali più efficienti in lettura che scrittura, mantenendo comunque un infrastruttura relazionale per la gestione di utenti e autori rendendo uno un as-is dell'altro e differenziandoli da un flag, si potrebbe inoltre usare un DBMS che possa gestire funzionalità aggiuntive (SQLServer,PostgreSQL...).

## Migliorie varie

Oltre la citata miglioria riguardante il db, potrebbe giovare aggiungere un sistema di carrello-cassa e pagamento al sistema per la ricezione di transazioni attraverso un altro servizio per la gestione delle suddette, un sistema di autenticazione utente, anche con Oauth attraverso servizzi esterni.
