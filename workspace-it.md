---
language: it
layout: default
title: "Spazio di lavoro per il corso"
permalink: /it/workspace
---


{%include pageglobal.html %}


## Suggerimenti per la creazione di uno *spazio di lavoro* per il corso

*Versione {{ ryear }}*


Nel nostro corso utilizzeremo tre software principali:
- MySQL community edition (<https://www.mysql.com/it/products/community/>), il DBMS,
- MySQL workbench (<https://www.mysql.com/it/products/workbench/>), l’interfaccia grafica per MySQL

Le versioni del software utilizzate **per l'anno accademico {{ryear}}/{{ryear | plus: 1}}** sono indicate nella sezione 
[Software](/it/risorse#software).

**Nota** : se preferite un
prodotto del tutto *open source*, potete scaricare **MariaDB**
(versione 10 o superiore) (<https://mariadb.org/>),
che è in buona parte compatibile con MySQL 8 e con il MySQL Workbench.
Allo stesso modo, come tool di interazione col DBMS al posto del Workbench
potete ad esempio utilizzare DBeaver Community (<https://dbeaver.io/>), che è open source,
anche se la sua interfaccia è molto diversa da quella del Workbench che utilizzeremo a lezione.

Inoltre, per disegnare i **diagrammi ER** , potrete usare qualsiasi software di grafica vettoriale a vostra
disposizione. Un suggerimento è provare **diagrams.net** (prima nota come *draw.io*),
che potete usare online all'indirizzo <https://app.diagrams.net/>
oppure scaricare come applicazione desktop per tutte le piattaforme
all'indirizzo <https://github.com/jgraph/drawio-desktop/releases>.

## Scaricamento e Installazione di MySQL Server e MySQL Workbench

### Installazione per Windows

- Scaricate l'installer (pacchetto msi) da <https://dev.mysql.com/downloads/installer/> ed eseguitelo.

- Selezionate "***Custom***" come tipo di setup (per minimizzare il software da installare in base alle nostre esigenze).

- Selezionate solo i seguenti componenti: **MySQL Servers -\> MySQLServer 8** , **Applications -\> MySQL Workbench -\> MySQL Workbench 8** e **MySQL Notifier** (se disponibile).

- Se viene evidenziato qualche **requisito** nella pagina successiva, cliccate su *execute* (non next) e lasciate che l'installer scarichi i runtime necessari a MySQL, eventualmente accettandone l'installazione sui relativi installer che verranno avviati.

- Quando tutti i requisiti avranno la spunta verde, cliccate su *next*.

- Nella schermata di riepilogo delle componenti da installare cliccate su *execute.*

- Attendete che tutte le tre componenti selezionate siano state installate (spunte verdi) quindi cliccate su *next*.

- Vi verrà notificato che è necessario ora configurare il server. Cliccate su *next*.

- Accertatevi che sia selezionata la configurazione "***standalone mysql server*** " (default) e procedete cliccando su *next*.

- Accertatevi che come tipo di installazione sia selezionata "***development computer*** " (default) e che la porta del server sia quella standard (3306), quindi cliccate su *next*.

- Accertatevi che il tipo di autenticazione selezionata sia quella "***strong***" (default), quindi cliccate su *next*.

- Scegliete una password per l'utente *root* . Useremo questo utente per gli esperimenti con MySQL, in quanto ha tutti i privilegi e può operare liberamente sul server. Ovviamente vedremo a lezione come creare altri utenti con privilegi meno elevati. Cliccate su *next*.

- Se state operando su Windows, vi verrà chiesto se installare MySQL come **servizio**. Accettate questa opzione ma **deselezionate** "*start at system startup*". In questo modo potrete avviare il server solo quando necessario, risparmiando risorse preziose della vostra macchina (e rendendola anche più sicura). Cliccate su *next*.

- Infine, cliccate su *execute* per applicare la configurazione al server. Se tutto va bene, dopo poco tempo potrete cliccare su *finish* e completare il processo di configurazione. In caso contrario, guardate il log per cercare di capire cos'è andato storto.

- Procedete quindi con *next*, e l'installer vi chiederà se avviare il workbench. Potete farlo adesso o più avanti, in ogni caso al primo accesso al workbench dovrete configurarne la connessione a MySQL come spiegato più avanti.

- Terminate il processo di installazione.

> Nota: su sistemi Windows, se avete installato il "**MySQL notifier** " (che sta comunque venendo dismesso, quindi potrebbe non essere più disponibile), potrete usarlo per avviare e fermare il relativo servizio (cioè il server MySQL). In alternativa, aprite il *Task manager* (Gestione attività), selezionate la pagina dei *Servizi*, individuate MySQL, cliccateci col tasto destro e selezionate l'operazione da eseguire.

### Installazione per sistemi Unix

Su sistemi Unix, **accertatevi prima di tutto di non avere MySQL 8 già installato**. Se è presente una versione precedente, dovrete rimuoverla prima di procedere. Se la versione 8 è già presente, dovrete installare solo il workbench.

E' possibile installare il server e il workbench separatamente scaricando i pacchetti rispettivamente da <https://dev.mysql.com/downloads/mysql/>
e <https://dev.mysql.com/downloads/workbench/>, oppure usare il **repository APT** (per distribuzioni Linux Debian e Ubuntu) come spiegato in questo tutorial: <https://dev.mysql.com/doc/mysql-apt-repo-quick-guide/en>.

In ogni caso, date un'occhiata alle istruzioni di installazione per Windows, in modo da sapere quali componenti installare (se disponibili per la vostra piattaforma) e quali impostazioni applicare (nel caso siano impostabili sulla vostra piattaforma).

### Installazione per MacOS

E' possibile installare il server e il workbench separatamente scaricando i pacchetti rispettivamente da <https://dev.mysql.com/downloads/mysql/>
e <https://dev.mysql.com/downloads/workbench/>.

In ogni caso, date un'occhiata alle istruzioni di installazione per Windows, in modo da sapere quali componenti installare (se disponibili per la vostra piattaforma) e quali impostazioni applicare (nel caso siano impostabili sulla vostra piattaforma).

> Nota: le versioni del workbench a partire dalla *8.0.23* contengono **un  bug che ne impedisce il funzionamento su MacOS**. 
> Tale bug continua ad essere presente 
> nell'ultima versione (8.0.32) disponibile al momento della scrittura di questa 
> guida. E' quindi necessario accedere alla sezione archivio download 
(<https://downloads.mysql.com/archives/workbench/>) e scaricare la versione *8.0.22*.

## Avvio e configurazione di MySQL Workbench

Prima di avviare il workbench, assicuratevi sempre che il server MySQL sia in esecuzione (avviando il relativo servizio, se non lo è già).

Il workbench, se installato insieme al server, dovrebbe avere una connessione preconfigurata chiamata "***Local instance MySQL***" (o similari), che vi verrà mostrata nel *welcome screen* dell'applicazione. Se non la trovate, cliccate sul segno "+" a fianco al titolo "**MySQL Connections**", date un nome a piacere alla connessione, inserite **127.0.0.1** come hostname, **3306** come porta e **root** come username (dovrebbero esserci di default), quindi cliccate su "***Test Connection***". Se tutto va bene, potrete poi cliccare su ok per salvare la configurazione.

Cliccate sulla connessione da attivare, inserite la password (se vi state connettendo come *root* , è quella scelta in fase di installazione) e magari cliccate su *save* per non doverla reinserire ogni volta (tanto si tratta di un server di sviluppo locale alla vostra macchina). Se tutto va bene, vedrete aprirsi l'editor SQL connesso al server in esecuzione.