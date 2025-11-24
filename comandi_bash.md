---
layout: default
title: Guida Rapida Comandi Bash
---
#Appunti #Esami #OS 

***Nota bene***: i riferimenti riguardano il numero in basso a destra nelle slide del file **4_InterfacciaUtenteACaratteri_BashScripting.pdf**; riferimenti differenti sono specificati direttamente nelle tabelle

---

# Guida Rapida Comandi Bash, Crittografia e Gestione Pacchetti

## I. Comandi Base e Utilità della Shell (Bash)

Questa sezione contiene i comandi fondamentali per la navigazione nel filesystem, la gestione di file, directory e l'ottenimento di informazioni sul sistema.

| Categoria              | Comando                            | Descrizione                                                                                                                                         | Riferimenti |
| :--------------------- | :--------------------------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------- | :---------- |
| **Navigazione e File** | `pwd`                              | Visualizza il **percorso completo** della directory di lavoro corrente (directory corrente).                                                        | 33          |
| **Navigazione e File** | `cd <percorso>`                    | **Cambia la directory** di lavoro corrente. Può usare percorsi assoluti (`/home/user`) o relativi (`../`).                                          | 34          |
| **Navigazione e File** | `ls -alh <percorso>`               | **Elenca informazioni sui file** nella directory specificata (opzioni: `-a` tutti i file, `-l` formato lungo, `-h` dimensione leggibile dall'uomo). | 48          |
| **Navigazione e File** | `mkdir <percorso_dir>`             | **Crea una nuova directory** nel percorso specificato.                                                                                              | 82          |
| **Navigazione e File** | `rmdir <percorso_dir>`             | **Elimina la directory** specificata, solo se è vuota.                                                                                              | 82          |
| **Navigazione e File** | `rm <percorso_file>`               | **Elimina il file** specificato.                                                                                                                    | 82          |
| **Navigazione e File** | `mv <src> <dest>`                  | **Sposta o rinomina** il file specificato.                                                                                                          | 82          |
| **Navigazione e File** | `touch <percorso_file>`            | **Crea il file** specificato se non esiste, o ne aggiorna la data.                                                                                  | 82          |
| **Contenuto File**     | `cat <percorso_file>`              | Visualizza in output il **contenuto completo** del file specificato.                                                                                | 82          |
| **Contenuto File**     | `more <file>` / `less <file>`      | Mostra il file specificato **un poco alla volta** (paginazione).                                                                                    | 82          |
| **Contenuto File**     | `head <file>`                      | Mostra le **prime 10 linee** del file specificato.                                                                                                  | 82          |
| **Contenuto File**     | `tail <file>`                      | Mostra le **ultime 10 linee** del file specificato.                                                                                                 | 82          |
| **Info/Utility**       | `man <comando>`                    | **Manuale**: fornisce informazioni sul comando specificato.                                                                                         | 82          |
| **Info/Utility**       | `which <eseguibile>`               | Visualizza il **percorso** dell'eseguibile (solo se si trova nella variabile `PATH`).                                                               | 82          |
| **Info/Utility**       | `strace <comando>`                 | Esegue un comando e visualizza le **system call** che sono chiamate dal processo.                                                                   | 10          |
| **Info/Utility**       | `echo <caratteri>`                 | Visualizza in output la sequenza di caratteri specificata.                                                                                          | 38          |
| **Info/Utility**       | `grep <pattern> <file>`            | **Cerca** tra le righe di un file (o da stdin) quelle che contengono il pattern.                                                                    | 82          |
| **Info/Utility**       | `find <dir> <opzioni>`             | Cerca dei file in una directory e nelle sue sottodirectory.                                                                                         | 82          |
| **Info/Utility**       | `wc`                               | **Conta** il numero di parole, caratteri o linee di un file.                                                                                        | 82          |
| **Permessi**           | `chown <nuovoproprietario> <file>` | Cambia il **proprietario** di un file.                                                                                                              | 45,46       |
| **Permessi**           | `chgrp <nuovogruppo> <file>`       | Cambia il **gruppo** di un file.                                                                                                                    | 45          |
| **Permessi**           | `chmod <modo> <file>`              | Cambia i **permessi** di un file.                                                                                                                   | 43          |

---

## II. Comandi per Gestione Processi (Jobs e Segnali)

Questa sezione include i comandi per la visualizzazione, la gestione e la manipolazione dei processi e dei lavori (jobs) della shell.

| Categoria         | Comando                     | Descrizione                                                                                                                                       | Riferimenti |
| :---------------- | :-------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------ | :---------- |
| **Processi/Jobs** | `ps aux`                    | Stampa informazioni sui **processi in esecuzione**.                                                                                               | 82          |
| **Processi/Jobs** | `<comando> &`               | Lancia un comando direttamente in **background**. Il PID viene salvato in `$!`.                                                                   | 194         |
| **Processi/Jobs** | `jobs`                      | Produce una lista numerata dei processi in background o sospesi nella shell corrente.                                                             | 194         |
| **Processi/Jobs** | `bg`                        | Riprende un job fermato e lo mette in **sottofondo** (background).                                                                                | 194         |
| **Processi/Jobs** | `fg %n`                     | Porta il job con indice `%n` in **primo piano** (foreground).                                                                                     | 194         |
| **Processi/Jobs** | `kill -9 <pid/jobid>`       | Invia il segnale **SIGKILL** (terminazione forzata, non ignorabile) al processo specificato.                                                      | 82, 201     |
| **Processi/Jobs** | `killall <nome_processo>`   | **Elimina tutti i processi** con quel nome.                                                                                                       | 82, 209     |
| **Processi/Jobs** | `disown <jobid/pid>`        | **Sgancia il job** dalla shell interattiva che lo ha lanciato, impedendo il segnale SIGHUP alla chiusura della shell.                             | 194, 198    |
| **Processi/Jobs** | `nohup <cmd> &`             | Lancia un comando che è reso **immune al segnale SIGHUP** (utile per processi in background che devono sopravvivere alla chiusura del terminale). | 200         |
| **Processi/Jobs** | `wait <pid/jobid>`          | **Attende la terminazione** del processo o job specificato.                                                                                       | 205, 206    |
| **Segnali**       | `trap "<action>" <signals>` | Definisce l'azione da eseguire al ricevimento di un elenco di segnali.                                                                            | 203         |

---

## III. Bash Scripting: Variabili, Controllo di Flusso e Espansioni

| Categoria                | Sintassi                         | Descrizione                                                                                                                              | Riferimenti |
| :----------------------- | :------------------------------- | :--------------------------------------------------------------------------------------------------------------------------------------- | :---------- |
| **Variabili**            | `VARIABILE=contenuto`            | **Assegnamento** di valore a una variabile locale (NOTA: non sono ammessi spazi prima o dopo `=`).                                       | 41          |
| **Variabili**            | `echo ${VAR}` / `echo $VAR`      | **Espansione** di variabile (sostituzione del nome con il suo valore).                                                                   | 36          |
| **Variabili**            | `export <variabile>`             | **Trasforma una variabile locale in variabile d'ambiente**, ereditata dalle subshell.                                                    | 54          |
| **Variabili**            | `unset <variabile>`              | **Elimina** una variabile esistente.                                                                                                     | 62          |
| **Variabili**            | `VAR="stringa" <comando>`        | Definisce una **variabile d'ambiente temporanea** solo per l'esecuzione di quel comando (la variabile non rimane nella shell chiamante). | 60          |
| **Variabili Speciali**   | `$#`                             | Contiene il **numero di argomenti** passati allo script.                                                                                 | 84          |
| **Variabili Speciali**   | `$0`                             | Contiene il **nome del processo** (lo script) in esecuzione.                                                                             | 84          |
| **Variabili Speciali**   | `$1, $2, ...`                    | Contengono il primo, secondo, ecc., **argomento** passato allo script.                                                                   | 84          |
| **Variabili Speciali**   | `$*`                             | Tutti gli argomenti concatenati e separati da spazi.                                                                                     | 84          |
| **Variabili Speciali**   | `"$@"`                           | Tutti gli argomenti, quotati singolarmente, permettendo di non spezzare gli argomenti che contengono spazi.                              | 86          |
| **Variabili Speciali**   | `$?`                             | Contiene l'**Exit Status** (valore restituito, 0 per successo) dell'ultimo comando eseguito.                                             | 97          |
| **Variabili Speciali**   | `$!`                             | PID dell'ultimo processo lanciato in **background**.                                                                                     | 195         |
| **Variabili d'ambiente** | `env`                            | Mostra **tutte** le variabili d'ambiente **e il loro valore**                                                                            | 54          |
| **Espansioni**           | `~` / `~/dir`                    | **Tilde Expansion**: sostituita dal percorso assoluto della Home Directory dell'utente.                                                  | 37, 77      |
| **Espansioni**           | `*`                              | **Wildcard**: sostituita da una qualunque sequenza di caratteri (anche vuota) per ottenere nomi di file.                                 | 78          |
| **Espansioni**           | `?`                              | **Wildcard**: sostituita da esattamente un singolo carattere.                                                                            | 78          |
| **Espansioni**           | `[elenco]`                       | **Wildcard**: sostituita da un solo carattere tra quelli specificati (es. ``, `[[:digit:]]`).                                            | 78          |
| **Matematica**           | `(( NUM=3+2 ))`                  | **Valutazione aritmetica** (utilizzata per assegnamenti e come condizione logica: 0=True, 1=False).                                      | 88          |
| **Matematica**           | `NUM=$((3+2))`                   | **Espansione aritmetica** (il risultato numerico sostituisce l'espressione).                                                             | 88          |
| **Condizionali**         | `[[ <condizione> ]]`             | **Espressione condizionale** (ritorna Exit Status 0 o >0). Disabilita le interpretazioni di _Word splitting_ e _pathname expansion_.     | 117-124     |
| **Controllo Flusso**     | `if <list>; then <list>; ... fi` | Struttura di controllo `if/then/else` che valuta l'Exit Status della `<list>` (lista di comandi o espressione condizionale).             | 102         |
| **Controllo Flusso**     | `for <var> in ... ; do ... done` | Loop che itera sugli elementi di un elenco di parole.                                                                                    | 102         |
| **Controllo Flusso**     | `while <list>; do <list>; done`  | Loop che continua finché la `<list>` restituisce Exit Status 0 (successo).                                                               | 102         |

---

## IV. Reindirizzamenti e Gruppi di Comandi
 
Questa sezione copre gli operatori di I/O (Input/Output) e i metodi per raggruppare i comandi. I descrittori di file standard sono: `0` (stdin), `1` (stdout), `2` (stderr).

| Sintassi | Tipo | Descrizione | Riferimenti |
| :--- | :--- | :--- | :--- |
| `<cmd> > <file>` | Output | **Reindirizza lo standard output** (`fd 1`) su un file, **sovrascrivendolo**. | 150, 151 |
| `<cmd> >> <file>` | Output | Reindirizza lo standard output (`fd 1`) su un file, **aggiungendolo in coda**. | 150, 151 |
| `<cmd> < <file>` | Input | **Reindirizza lo standard input** (`fd 0`) prendendolo dal file. | 150 |
| `<cmd> 2> <file>` | Error | Reindirizza lo standard error (`fd 2`) sul file. | 153 |
| `<cmd> &> <file>` | All Output | Reindirizza **stdout e stderr** sullo stesso file. | 154 |
| `<cmd> N>&M` | FD Mapping | Reindirizza il **file descriptor N** per puntare allo stesso target del file descriptor M. (Esempio: `ls 2>&1 > file.txt` reindirizza stderr (`2`) verso stdout (`1`), che a sua volta è reindirizzato verso `file.txt`). | 158 |
| `\|` | Pipe | Collega lo standard output di `cmd1` allo standard input di `cmd2` (i processi eseguono in contemporanea in subshell). | 156 |
| `\|&` | Pipe All | Collega **stdout e stderr** di `cmd1` allo standard input di `cmd2` (scorciatoia per `2>&1 \|`). | 166 |
| `exec {FD}< <file>` | Apertura FD | **Apre un file** e assegna il **file descriptor** libero ad una variabile (`FD`). | 145 |
| `exec {FD}>&-` | Chiusura FD | **Chiude** lo stream associato al file descriptor nella variabile `FD`. | 148 |
| `OUT=\`<cmd>\`` | Command Sub | Sostituisce il comando con l'output prodotto su stdout (sintassi **backticks**). | 112 |
| `OUT=$(<cmd>)` | Command Sub | Sostituisce il comando con l'output prodotto su stdout (sintassi **tonde**). | 112 |
| `( <lista> )` | Raggruppamento | Esegue la lista di comandi in una **subshell** (copia dell'ambiente). | 101 |
| `{ <lista> ; }` | Raggruppamento | Esegue la lista di comandi nella **shell corrente** (richiede `;` prima di `}`). | 101 |
| `<cmd> << FINE ... FINE` | Here Doc | **Here Document**: ridirige l'input multi-linea specificato tra due delimitatori (`FINE`) allo standard input del comando. | 172, 173 |

---

## V. Gestione Variabili Avanzata (Parameter Expansion)

Operatori utilizzati all'interno della sintassi `${VAR...}` per manipolare il contenuto di una variabile (spesso usati per estrazione o sostituzione di sottostringhe).

| Operatore              | Esempio (VAR="alfabetagamma")            | Descrizione                                                                                            | Riferimenti |
| :--------------------- | :--------------------------------------- | :----------------------------------------------------------------------------------------------------- | :---------- |
| `${#VAR}`              | `echo ${#VAR}` (Output: 13)              | **Lunghezza** della variabile in byte.                                                                 | 139         |
| `${VAR/pat/str}`       | `${VAR/beta/XXX}` (Output: alfaXXXgamma) | Sostituisce la **prima** occorrenza di `pat` con `str`.                                                | 224         |
| `${VAR//pat/str}`      | `${VAR//a/X}` (Output: XlfxbetXgXmmX)    | Sostituisce **tutte** le occorrenze di `pat` con `str`.                                                | 226         |
| `${VAR:offset:length}` | `${VAR:4:4}` (Output: beta)              | Estrae una **sottostringa** di `length` a partire da `offset` (il primo carattere è offset 0).         | 224         |
| `${VAR#pat}`           | `${VAR#al*be}` (Output: tagamma)         | Rimuove il **prefisso più corto** che corrisponde al pattern (wildcard supportate).                    | 223         |
| `${VAR##pat}`          | `${VAR##al*m}` (Output: ma)              | Rimuove il **prefisso più lungo** che corrisponde al pattern.                                          | 223         |
| `${VAR%pat}`           | `${VAR%gamma}` (Output: alfabetagamma)   | Rimuove il **suffisso più corto** che corrisponde al pattern.                                          | 223         |
| `${VAR%%pat}`          | `${VAR%%amma}` (Output: alfabetag)       | Rimuove il **suffisso più lungo** che corrisponde al pattern.                                          | 223         |
| `${!Prefisso*}`        | `${!BASH_AR*}`                           | **Riferimento indiretto**: restituisce un elenco dei nomi delle variabili che iniziano con `Prefisso`. | 227         |

---

## VI. Gestione Pacchetti APT/DPKG

Comandi per l'installazione, la rimozione e l'aggiornamento di software su sistemi basati su Debian/Ubuntu, e per la gestione delle chiavi GPG dei repository.

***Nota bene:*** questi comandi e il relativo scopo si trovano nel file **APT_e_APT_Keyring.pdf**

| Comando                            | Scopo                                                                                                     | Note                                                                                                                                                                           |
| :--------------------------------- | :-------------------------------------------------------------------------------------------------------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `sudo apt-get update`              | **Aggiorna l'indice** locale dei pacchetti disponibili dai repository.                                    | Comando fondamentale da eseguire per primo per sincronizzare il database locale con i repository.                                                                              |
| `sudo apt update`                  | Equivalente moderno di `apt-get update`.                                                                  | `apt-get` è preferito negli script poiché il suo output è considerato stabile.                                                                                                 |
| `apt-get install -y gnupg`         | **Installa il pacchetto `gnupg`** (GNU Privacy Guard).                                                    | Questo pacchetto contiene i comandi necessari per generare chiavi GPG e firmare i file. L'opzione `-y` (se specificata) installa anche i pacchetti raccomandati (come `gpgv`). |
| `sudo apt-get upgrade`             | Installa le nuove versioni di **tutti i pacchetti installati**.                                           |                                                                                                                                                                                |
| `sudo apt-get install <pacchetto>` | Installa un nuovo pacchetto e tutte le sue dipendenze.                                                    | apt-get usa `dpkg` per l'installazione vera e propria.                                                                                                                         |
| `sudo apt-get remove <pacchetto>`  | Rimuove un pacchetto, ma **lascia i file di configurazione**.                                             |                                                                                                                                                                                |
| `sudo apt-get purge <pacchetto>`   | Rimuove un pacchetto **inclusi i file di configurazione**.                                                |                                                                                                                                                                                |
| `sudo apt-get autoremove`          | Rimuove i pacchetti che erano **dipendenze** ma che non sono più necessari.                               |                                                                                                                                                                                |
| `sudo apt-get dist-upgrade`        | Esegue un **aggiornamento completo** della distribuzione (gestisce anche i cambiamenti nelle dipendenze). | Più potente di `upgrade`.                                                                                                                                                      |
| `sudo apt-get clean`               | Cancella i file `.deb` scaricati dalla cache locale.                                                      |                                                                                                                                                                                |

## VII. Crittografia, GPG e Gestione Chiavi APT

| Operazione              | Comando                                                                             | Descrizione                                                                                                                                                                                                                           |
| :---------------------- | :---------------------------------------------------------------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Download Chiave GPG** | `wget -qO- <URI_chiave> \|sudo gpg --dearmor -o /etc/apt/keyrings/nome.gpg`         | Scarica la chiave pubblica GPG (`wget`) in formato ASCII e la converte (`gpg --dearmor`) nel formato binario Keyring che APT preferisce, salvandola nella directory sicura `/etc/apt/keyrings/`.                                      |
| **Aggiunta Repository** | `echo "deb [signed-by=.../nome.gpg] " \|sudo tee /etc/apt/sources.list.d/repo.list` | Aggiunge il repository al sistema, specificando esplicitamente con `signed-by` il percorso della chiave pubblica da usare per verificare l'autenticità dei pacchetti.                                                                 |
|                         | **`shasum256 nomefile`**                                                            | **Calcola il _digest_ (hash) SHA-255** di un file, producendo una riga di output contenente il checksum e il nome del file.                                                                                                           |
|                         | **`sha256sum -c nomefile.sha256`**                                                  | **Verifica l'integrità** di un file confrontando il _digest_ ricalcolato con quello memorizzato nel file `nomefile.sha256`. Scrive `OK` se i digest combaciano o `FAILED` in caso contrario. Esiste anche il comando **`sha512sum`**. |
|                         | **`openssl dgst -sha256 nomefile`**                                                 | Comando alternativo, fornito dal package `openssl`, per **calcolare il _digest_** del file specificato (in questo caso usando SHA-256).                                                                                               |
|                         | **`gpg --list-secret-keys`**                                                        | **Visualizza l'elenco delle chiavi private** (segrete) GPG già presenti nella home directory dell'utente (`/home/${USER}/.gnupg`).                                                                                                    |
|                         | **`gpg --gen-key`**                                                                 | **Genera la coppia di chiavi GPG** (pubblica e privata) RSA. Crea i file necessari, come `pubring.gpg`, `secring.gpg` e `gpg.conf`, nella directory di configurazione (`/home/${USER}/.gnupg`).                                       |
|                         | **`gpg --armor --detach-sign nomefile`**                                            | **Crea una firma GPG _detached_** (separata) in formato **ASCII leggibile**. L'output è un file di testo chiamato `nomefile.asc`.                                                                                                     |
|                         | **`gpg --detach-sign nomefile`**                                                    | **Crea una firma GPG _detached_** (separata) in formato **binario**. L'output è un file binario chiamato `nomefile.sig`.                                                                                                              |
|                         | **`gpg --clearsign nomefile`**                                                      | **Crea una firma GPG _inline_**, generando un file di testo (`nomefile.asc`) che contiene sia il file originale che la firma, entrambi in formato ASCII leggibile.                                                                    |
|                         | **`gpg --sign nomefile`**                                                           | **Crea una firma GPG _in-place_ (incorporata)**, generando un file binario (`nomefile.gpg`) che contiene sia il contenuto originale che la firma.                                                                                     |
|                         | **`gpg --verify nomefile.asc nomefile`**                                            | **Verifica una firma GPG _detached_** (separata), confrontando il file di firma (`nomefile.asc`) con il file originale (`nomefile`).                                                                                                  |
|                         | **`gpg --verify nomefile.gpg`**                                                     | **Verifica una firma GPG _inline_ o _incorporata_**.                                                                                                                                                                                  |
|                         | **`gpg --list-secret-keys --keyid-format long`**                                    | **Trova l'ID completo (long format) della chiave privata** da utilizzare, specialmente quando sono presenti più chiavi installate.                                                                                                    |
|                         | **`gpg --local-user ID_CHIAVE --detach-sign nomefile`**                             | **Firma un file specificando l'ID della chiave privata** (`ID_CHIAVE`) da utilizzare per la firma.                                                                                                                                    |

---

## VIII. Accesso Remoto SSH (Secure Shell)

Comandi per la connessione remota sicura e la gestione delle coppie di chiavi SSH/RSA.

***Nota bene:*** i comandi e il relativo scopo si trovano nel file **Accesso da remoto con SSH**

| Comando                                                                          | Scopo                                                                                                                                                                            | Note                                                                                                   |
| :------------------------------------------------------------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----------------------------------------------------------------------------------------------------- |
| `ssh-keygen -t rsa`                                                              | **Crea una coppia di chiavi** (pubblica e privata) RSA sul client.                                                                                                               | La chiave privata viene salvata in `~/.ssh/id_rsa`, la pubblica in `~/.ssh/id_rsa.pub`.                |
| `ssh <account>@<host>`                                                           | Stabilisce una **connessione cifrata SSH** con la macchina remota, autenticandosi tramite password o chiavi.                                                                     | L'output dei comandi eseguiti sul server viene visualizzato sul terminale del client.                  |
| `ssh <account>@<host> -o PubkeyAuthentication=no`                                | Si connette a SSH **forzando l'uso della password** invece dell'autenticazione a chiave pubblica/privata.                                                                        |                                                                                                        |
| `ssh-copy-id <account>@<host>`                                                   | **Copia la chiave pubblica** del client sul server nella directory `~/.ssh/authorized_keys`.                                                                                     | Questo è il metodo consigliato rispetto alla copia manuale.                                            |
| `scp ~/.ssh/id_rsa.pub account_server@nome_host_server:.ssh/authorized_keys`     | **Copia la chiave pubblica** dal client al server, nel file `authorized_keys` dell'utente di destinazione. Questo è un metodo limitato perché _sovrascrive_ le chiavi esistenti. |                                                                                                        |
| `cat ~/.ssh/id_rsa.pub \|ssh "mkdir -p ~/.ssh && cat >> ~/.ssh/authorized_keys"` | **Copia la chiave pubblica** in modo sicuro usando la pipeline bash, garantendo che le chiavi esistenti non vengano sovrascritte.                                                |                                                                                                        |
| `ssh -T <host> /bin/bash <<FINESCRIPT ... FINESCRIPT`                            | Esegue una **sequenza di comandi** o uno script localmente definito sul server remoto.                                                                                           | La stringa `FINESCRIPT` (o qualsiasi altra stringa scelta) delimita l'inizio e la fine della sequenza. |
| `ssh-copy-id account_server@nome_host`                                           | **Utility preferita** per copiare la chiave pubblica sul server in modo sicuro, gestendo la creazione della directory e l'aggiunta al file `authorized_keys`.                    |                                                                                                        |
| `ssh ... -o PubkeyAuthentication=no`                                             | Parametro da usare con il comando `ssh` per **forzare l'uso dell'autenticazione tramite password**, disabilitando l'autenticazione basata su chiave pubblica/privata.            |                                                                                                        |

---

## IX. Script Base e Modelli (Boilerplate)

Questa sezione contiene schemi di script riutilizzabili per affrontare compiti comuni o complessi, specialmente quelli relativi alla gestione di I/O, cicli, e interazione con processi remoti.

## A. Scripting Base e Flusso di Controllo

### 1. Modello per l'elaborazione di input da file (Ciclo `while read`)

Questo script legge un file riga per riga. L'uso di `while read RIGA` è lo standard per evitare problemi con gli spazi bianchi e permette di processare grandi file senza caricarli completamente in memoria.

```
#!/bin/bash
# Uso: ./processa_file.sh <file_da_leggere>

FILE_INPUT="$1" #primo parametro passato in input

# Verifica se il file esiste
if [[ ! -f "$FILE_INPUT" ]]; then
    echo "Errore: File non trovato: ${FILE_INPUT}" >&2
    exit 1
fi

echo "Inizio elaborazione del file: ${FILE_INPUT}"

# L'output di 'cat' è convogliato in pipe come input per 'while read'.
# Nota: L'uso di read in una pipe lo esegue in una subshell.
cat "${FILE_INPUT}" | while read RIGA ; do

    # Ignora le righe vuote o che iniziano con # (commenti)
    if [[ -z "${RIGA}" || "${RIGA}" =~ ^# ]]; then
        continue
    fi

    # Esempio di elaborazione: estrai la lunghezza della riga
    LUNGHEZZA=${#RIGA}
    echo "Riga processata (Lunghezza: ${LUNGHEZZA}): ${RIGA}"

done

# NOTA: Le modifiche a variabili locali (es. contatori) FATTE ALL'INTERNO
# del ciclo while NON sono visibili fuori, se il ciclo è in una pipe.

echo "Elaborazione completata."
exit 0
```

### 2. Modello per l'uso di argomenti e opzioni (`case/getopts`)

Questo modello illustra come accedere agli argomenti passati allo script (`$1, $2, ...`) e come iterare su di essi, mantenendo i valori quotati per gestire argomenti contenenti spazi (`"$@"` vs `"$*"`).

```
#!/bin/bash

# Accesso al nome dello script: $0
echo "Esecuzione dello script: $0"

# Accesso al numero di argomenti: $#
if (( $# == 0 )); then
    echo "Nessun argomento fornito."
fi

# Iterazione sicura su tutti gli argomenti
echo "Lista degli argomenti ($# totali):"
for ARG in "$@" ; do
    echo "  - Argomento: ${ARG}"
done

# Esempio di verifica condizionale (Exit Status)
FILE_DA_VERIFICARE="$1"
if [[ -f "$FILE_DA_VERIFICARE" ]]; then
    echo "Il file '$FILE_DA_VERIFICARE' esiste ed è regolare. (Status 0: Successo)"
    # Esegue solo se il test precedente ha successo (&&)
    ls -l "$FILE_DA_VERIFICARE" && echo "Lista completata."
else
    echo "Il file non esiste. (Status >0: Fallimento)"
fi

exit 0 # Exit Status 0 (Successo)
```

## B. Gestione File Descriptor e Reindirizzamenti I/O

Questi script dimostrano come manipolare gli stream di I/O (Input/Output) oltre ai classici `stdin` (0), `stdout` (1) e `stderr` (2).

### 1. Apertura e Chiusura di un File Descriptor per la Scrittura

Questo script apre un file e scrive su di esso usando un file descriptor (FD) scelto automaticamente dal sistema.

```
#!/bin/bash
OUTPUT_FILE="/tmp/log_esame_$$" # Nome temporaneo sicuro (con PID)

# Chiede al sistema operativo di assegnare un FD libero e salvarlo in FD_SCRITTURA
exec {FD_SCRITTURA}> "$OUTPUT_FILE"

if (( $? != 0 )); then
    echo "Errore nell'apertura del file." >&2
    exit 1
fi

echo "File aperto con FD: ${FD_SCRITTURA}"

# Scrittura sul file descriptor, reindirizzando lo stdout (1) verso FD_SCRITTURA
echo "Messaggio di prova 1" 1>&"${FD_SCRITTURA}"
echo "Questo messaggio è scritto sul file." 1>&"${FD_SCRITTURA}"

# Tentativo di scrivere su stderr (che va ancora al terminale)
echo "Questo va a stderr (terminale)." >&2

# Chiusura del file descriptor
exec {FD_SCRITTURA}>&-

echo "File descriptor ${FD_SCRITTURA} chiuso."

echo "Contenuto del file $OUTPUT_FILE:"
cat "$OUTPUT_FILE"
rm "$OUTPUT_FILE"
```

### 2. Catturare sia STDOUT che STDERR in una Pipeline (`|&`)

Questo modello usa l'operatore `|&` per convogliare sia l'output standard (`stdout`, fd 1) che l'output di errore (`stderr`, fd 2) del primo comando verso l'input standard (`stdin`, fd 0) del comando successivo (come scorciatoia per `2>&1 |`).

```
#!/bin/bash
echo "--- Prova di reindirizzamento STDERR e STDOUT (comando 'ls') ---"

# Tenta di elencare un file esistente (successo) e uno non esistente (errore)
# Tutto l'output (stdout e stderr) viene inviato a 'grep'
ls /dev/null file_che_non_esiste_MAI |& grep "null"
# Output previsto: viene visualizzata la riga contenente "/dev/null"
# (sia che fosse su stdout che su stderr, viene intercettata)

echo ""

echo "--- Prova di mancato reindirizzamento solo con '|' ---"
# Qui viene inviato solo lo STDOUT a grep, quindi l'errore non viene intercettato.
ls /dev/null file_che_non_esiste_MAI | grep "such"
# Output previsto: L'errore del comando 'ls' va al terminale (stderr), non a grep.
# Viene visualizzato: "ls: cannot access file_che_non_esiste_MAI: No such file or directory" >&2
```

## C. Scripting e Accesso Remoto (SSH)

Questi schemi sono essenziali per le operazioni che coinvolgono l'autenticazione a chiave pubblica/privata e l'esecuzione di comandi su server remoti.

### 1. Generazione di Chiavi RSA (Richiesto per SSH e Crittografia Asimmetrica)

La generazione di chiavi RSA è il primo passo per l'autenticazione SSH a chiave pubblica (asimmetrica).

```
#!/bin/bash
echo "Generazione di una nuova coppia di chiavi RSA..."

# -t rsa specifica il tipo di chiave (RSA)
# -b 4096 specifica la dimensione (almeno 2048 bit sono consigliati per RSA)
ssh-keygen -t rsa -b 4096 -f ~/.ssh/id_rsa_esame

echo ""
echo "Chiavi generate in ~/.ssh/id_rsa_esame (privata, SEGRETA) e ~/.ssh/id_rsa_esame.pub (pubblica)."
echo "La sicurezza dipende dalla segretezza della chiave privata."

# Pulizia: non fare in uno script reale, solo per esempio.
# rm ~/.ssh/id_rsa_esame*
```

### 2. Esecuzione di uno Script Completo su Server Remoto (Here Document con SSH)

Questo è un modello avanzato per eseguire una sequenza multi-linea di comandi (un "Here Document" `<<FINESCRIPT`) sul server remoto. Utile per automatizzare operazioni complesse.

```
#!/bin/bash
# Sostituire con l'host e l'utente di destinazione
HOST_SERVER="account_server@nome_host_server"

echo "Esecuzione di comandi sul server remoto: ${HOST_SERVER}"

# SSH lancia /bin/bash sul server, che a sua volta legge i comandi fino a FINESCRIPT
# -T disabilita l'allocazione di pseudo-terminale (utile per script non interattivi)
ssh -T "${HOST_SERVER}" /bin/bash <<FINESCRIPT

# --- Inizio Comandi Eseguiti sul Server Remoto ---

echo "Ciao da $HOST_SERVER!"

# Esegui un comando locale sul server
pwd

# Esempio di gestione file: crea un file e verifica i permessi
touch /tmp/remote_test_file.txt
ls -l /tmp/remote_test_file.txt

# Verifica il Process ID della subshell SSH (BASHPID è il PID della bash remota)
echo "PID della shell remota: \$BASHPID"

# Esempio di gestione pacchetti (se hai i permessi di sudo sul remoto)
# sudo apt update && echo "Aggiornamento indici completato."

# --- Fine Comandi Eseguiti sul Server Remoto ---
FINESCRIPT

echo "Esecuzione remota terminata."
# L'Exit Status di questo script sarà l'Exit Status dell'ultimo comando *REMOTO* eseguito
```

## D. Gestione e Firma dei Pacchetti APT/GPG

Questi schemi replicano i passaggi critici per l'aggiunta di repository di terze parti, che richiedono l'uso combinato di `wget`, `gpg`, `tee` e APT per garantire l'integrità tramite firma digitale GPG.

### 1. Aggiunta Sicura di un Repository Esterno (I tre passi GPG/APT)

Questo script integra i tre passaggi fondamentali: download della chiave GPG, salvataggio nel keyring sicuro e aggiunta della sorgente con verifica esplicita della chiave (`signed-by`).

```
#!/bin/bash
REPO_URI="https://packages.example.com/repos/myapp"
REPO_DIST="stable"
REPO_COMPONENTS="main"
KEY_URL="https://packages.example.com/keys/myapp.asc"
KEYRING_FILE="/etc/apt/keyrings/myapp-archive-keyring.gpg"
REPO_LIST="/etc/apt/sources.list.d/myapp.list"

# 1. Creare la directory per i Keyrings (se non esiste)
sudo mkdir -p /etc/apt/keyrings || { echo "Errore nella creazione della directory keyring." >&2; exit 1; }

# 2. Scaricare e Convertire la chiave GPG in Keyring binario
echo "Scarico e converto la chiave GPG..."
# wget -qO- scarica in silenzio (-q) sullo stdout (-O-)
# | sudo gpg --dearmor -o ... converte lo stdout nel formato binario Keyring (.gpg) e lo salva
wget -qO- "${KEY_URL}" | sudo gpg --dearmor -o "${KEYRING_FILE}"

if (( $? != 0 )); then
    echo "Errore durante il download/conversione della chiave." >&2
    exit 1
fi
echo "Chiave salvata in ${KEYRING_FILE}"

# 3. Aggiungere il repository con la clausola signed-by
REPO_LINE="deb [signed-by=${KEYRING_FILE}] ${REPO_URI} ${REPO_DIST} ${REPO_COMPONENTS}"
echo "Aggiungo la riga del repository a ${REPO_LIST}..."
# echo | sudo tee sovrascrive il file con i privilegi di root
echo "${REPO_LINE}" | sudo tee "${REPO_LIST}" > /dev/null

# 4. Aggiornare l'indice dei pacchetti
echo "Aggiorno l'indice dei pacchetti (apt update)..."
sudo apt update

echo "Repository aggiunto e verifica GPG configurata."
# Ora è possibile installare il pacchetto: sudo apt install myapp
```

