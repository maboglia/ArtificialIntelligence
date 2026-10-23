# Linus Torvalds e l'AI: traduzione e analisi tecnica

Il messaggio di Linus Torvalds è particolarmente interessante per chi insegna informatica e per chi sviluppa software: affronta una questione centrale nell'era dell'intelligenza artificiale, ovvero se utilizzare uno strumento che automatizza parte del lavoro significhi necessariamente comprenderlo meno.

Il messaggio attribuito a Linus Torvalds non è una semplice difesa dell'AI. È una riflessione più ampia sul rapporto tra strumenti, competenza professionale e responsabilità individuale. Per comprenderlo correttamente, conviene distinguere la traduzione letterale del messaggio dalla sua interpretazione tecnica e didattica.

## 1. Traduzione integrale in italiano

Mittente: Linus Torvalds — Data: martedì 13 ottobre 2026, ore 13:45:09 (-0700) — Oggetto: R: [PATCH] docs: rimuovere i riferimenti ad Assisted-by

Il messaggio risponde a Laurent Pinchart, che aveva scritto:

> Quello di cui si tratta è stabilire le nostre aspettative, dire che cosa vogliamo e che cosa non vogliamo.

Linus Torvalds risponde:

No. Quello di cui stai parlando è qualcosa di completamente diverso. Non ha nulla a che fare con le «aspettative» e ha tutto a che fare con i tuoi pregiudizi.

Non capisco questo concetto completamente idiota del tipo «non usare l'AI per X».

Ecco una nuova regola, solo per te: non usare compilatori per nessuno dei tuoi contributi al kernel.

Perché, se non sei in grado di dimostrare di capire davvero che cosa sta facendo la macchina scrivendo il tuo codice in assembly, allora non voglio vedere i tuoi contributi al codice. Chiaramente non sei competente se non sai scriverlo in quel modo.

E, a proposito, faresti meglio a non usare nemmeno un editor per scrivere il messaggio di commit.

Perché voglio che tu mi dimostri di saper scrivere un buon messaggio di commit senza usare strumenti che rendono facile cancellare e nascondere gli errori commessi mentre digiti.

Va bene?

Perché, altrimenti, quei tuoi commit assistiti dagli strumenti dimostrano chiaramente che non sai quello che stai facendo.

Non ti rendi conto di quanto siano ASSOLUTAMENTE STUPIDE regole di questo genere?

Quindi no. Non introdurremo regole stupide del tipo «non puoi usare strumenti per X».

Il tipo di aspettative che io ho è che le persone facciano del loro meglio e mi aspetto che capiscano quello che stanno facendo.

Ma questa comprensione ha ben poco a che fare con gli strumenti che utilizzano.

E, a dire il vero, nella mia esperienza, le persone che rispetto e considero intelligenti non sono quelle che evitano di usare strumenti nuovi e interessanti.

Linus

## 2. Il contesto: perché Torvalds ne parla?

Il messaggio nasce da una discussione nella mailing list del kernel Linux relativa alla rimozione della dicitura `Assisted-by`, utilizzata per segnalare che un contributo al kernel era stato sviluppato con l'aiuto di un modello linguistico.&#x20;

[image](https://www.google.com/s2/favicons?domain=https://mid.mail-archive.com\&sz=32)

mid.mail-archive.com

+1

La questione è più concreta di quanto possa sembrare: come si valuta un contributo software quando il suo autore ha utilizzato un assistente AI?

La discussione mette in evidenza due esigenze legittime:

- Qualità e affidabilità: chi mantiene il kernel deve poter contare su codice corretto, sicuro, verificabile e adeguatamente documentato.
- Responsabilità dell'autore: chi propone una modifica deve comprenderla, saperla giustificare e rispondere alle osservazioni dei revisori.

Il problema è stabilire se la semplice presenza di un'etichetta che segnala l'uso dell'AI sia davvero utile a soddisfare queste esigenze.

Nella proposta di rimozione si osservava che la dicitura `Assisted-by` era presente solo in una parte dei contributi, mentre l'utilizzo effettivo dei modelli linguistici era più diffuso. Di conseguenza, l'assenza dell'etichetta non permetteva di concludere che l'AI non fosse stata utilizzata.&#x20;

[image](https://www.google.com/s2/favicons?domain=https://lkml.rescloud.iu.edu\&sz=32)

lkml.rescloud.iu.edu

+1

Torvalds si oppone soprattutto all'idea di trasformare il mezzo utilizzato in un criterio generale per giudicare la competenza di chi sviluppa.

## 3. Analisi tecnica: i cinque concetti fondamentali

### 3.1. Gli strumenti non sono una misura della competenza

L'analogia con il compilatore è il cuore dell'argomentazione.

Torvalds provoca il suo interlocutore: se per dimostrare di essere un programmatore competente fosse necessario scrivere direttamente in assembly, allora bisognerebbe rinunciare anche ai compilatori.

Il ragionamento è volutamente provocatorio, ma tecnicamente significativo.

Consideriamo questo codice Java:

```
public class Calculator {

    public static int sum(int a, int b) {
        return a + b;
    }

    public static void main(String[] args) {
        System.out.println(sum(10, 20));
    }
}
```

Un compilatore trasforma il codice sorgente in bytecode JVM. La JVM, a sua volta, interpreta o compila il bytecode in istruzioni eseguibili, a seconda dell'implementazione e delle condizioni di esecuzione.

Un programmatore competente non deve necessariamente scrivere a mano il bytecode o il codice macchina per poter sviluppare software professionale.

Deve però conoscere, nella misura richiesta dal problema, i concetti che stanno dietro al proprio programma: tipi, semantica, comportamento a runtime, errori, prestazioni e limiti dell'ambiente di esecuzione.

Lo stesso principio può essere applicato agli assistenti AI.

| Strumento            | Che cosa delega                                      | Che cosa resta responsabilità dello sviluppatore       |
| -------------------- | ---------------------------------------------------- | ------------------------------------------------------ |
| Compilatore          | Traduzione del codice                                | Correttezza del programma e diagnosi degli errori      |
| IDE                  | Editing, refactoring, navigazione                    | Comprensione delle modifiche e controllo del risultato |
| Libreria o framework | Funzionalità già implementate                        | Uso corretto delle API e comprensione delle dipendenze |
| Assistente AI        | Generazione, trasformazione o spiegazione del codice | Verifica, integrazione, test e responsabilità tecnica  |

La differenza fondamentale è che l'AI può intervenire anche sul ragionamento e sulla progettazione, non soltanto sulla trasformazione meccanica del codice. Per questo richiede controlli specifici, ma non per questo deve essere automaticamente esclusa.

### 3.2. Comprendere il codice non significa averlo scritto personalmente

Questo è il principio più importante per uno sviluppatore senior.

Immaginiamo che un assistente AI generi un metodo Java che gestisce una transazione bancaria. Il metodo compila, i test di base passano e il codice sembra leggibile.

È sufficiente? No.

Il responsabile dello sviluppo deve chiedersi:

- La transazione è atomica?
- Che cosa succede se una delle operazioni fallisce?
- Sono gestiti correttamente concorrenza e isolamento?
- Esiste una possibilità di doppio addebito?
- Le eccezioni vengono gestite senza nascondere errori?
- I test coprono i casi limite?
- Il comportamento è coerente con i requisiti?

L'AI può produrre una soluzione plausibile senza garantire che sia corretta in ogni condizione.

La competenza, pertanto, non si misura contando quante righe sono state digitate personalmente. Si misura anche dalla capacità di valutare il risultato, individuare i difetti e assumersi la responsabilità della soluzione.

Questo non significa che la scrittura manuale sia inutile: è fondamentale per imparare, comprendere la sintassi e sviluppare capacità di debugging. Significa che, in un contesto professionale, non è l'unico indicatore della competenza.

### 3.3. La qualità del risultato conta più della provenienza, ma non basta da sola

Qui occorre introdurre una distinzione importante.

Un programma può funzionare in un test e contenere comunque un difetto di sicurezza, una condizione di gara o un errore che emerge soltanto in produzione.

Per questo, quando Torvalds insiste sulla comprensione, non dobbiamo interpretare il suo messaggio come «se il codice sembra funzionare, va bene».

Un processo professionale di revisione dovrebbe valutare almeno:

Correttezza funzionale

Il codice soddisfa i requisiti, compresi i casi limite?

Sicurezza e robustezza

Sono stati valutati input non validi, autorizzazioni, concorrenza ed errori?

Test e riproducibilità

I test sono adeguati? I risultati sono riproducibili nell'ambiente previsto?

Comprensione e manutenibilità

L'autore sa spiegare la soluzione, modificarla e correggerla?

La provenienza del codice può essere rilevante per la revisione, ma non sostituisce nessuna di queste verifiche. Allo stesso tempo, la qualità apparente del risultato non rende superflua la trasparenza quando questa è richiesta da una policy, da un contratto o da esigenze di tracciabilità.

### 3.4. Il messaggio non equivale a un'approvazione incondizionata dell'AI

Sarebbe un errore interpretare la posizione di Torvalds come un invito ad accettare qualsiasi codice generato da un modello.

Il suo bersaglio è soprattutto il divieto generalizzato del tipo «non usare l'AI per questa attività», quando viene giustificato esclusivamente dalla natura dello strumento.

La posizione è più vicina a questo principio:

> Puoi usare gli strumenti che ritieni opportuni, ma devi capire ciò che proponi e rispondere della qualità del tuo lavoro.

Restano pienamente legittime le regole specifiche necessarie per proteggere informazioni riservate, rispettare licenze e obblighi contrattuali, prevenire rischi di sicurezza o garantire una valutazione didattica attendibile.

La distinzione è tra una regola motivata dal rischio concreto e una proibizione basata soltanto sul fatto che uno strumento è stato utilizzato.

### 3.5. La responsabilità non può essere delegata al modello

Questo punto è particolarmente importante per chi lavora su sistemi complessi.

Un assistente AI non è il soggetto che approva una pull request, mantiene un servizio in produzione o risponde di un incidente informatico. Queste responsabilità restano in capo alle persone e alle organizzazioni coinvolte.

Un senior developer che accetta codice generato dall'AI senza leggerlo, verificarlo e testarlo non può giustificarsi dicendo: «Lo ha scritto il modello».

Dal punto di vista professionale, delegare la produzione di una soluzione non equivale a delegare la responsabilità della sua accettazione.

## 4. Il punto di vista di un docente di informatica

Per chi insegna programmazione, il testo apre una questione ancora più interessante: come distinguere uno studente che usa l'AI per imparare da uno che la usa per evitare di imparare?

È un problema che riguarda direttamente i corsi di Java, Python, SQL e sviluppo backend.

### Il paradosso didattico

Consideriamo due studenti che consegnano la stessa esercitazione: una REST API in Spring Boot.

Studente A — codice scritto interamente a mano

Conosce la sintassi utilizzata, ma non sa spiegare perché il controller restituisce un determinato status HTTP, come vengono gestite le eccezioni o come testare il servizio.

Competenza non dimostrata

Studente B — codice sviluppato con l'AI

Sa spiegare l'architettura, giustifica le scelte, individua un errore introdotto dal modello, modifica il codice e scrive test per verificare il comportamento.

Competenza dimostrata

Lo studente B potrebbe aver dimostrato una competenza professionale superiore, nonostante abbia scritto personalmente meno codice.

Naturalmente, questa conclusione dipende anche dagli obiettivi della prova. Se l'esercitazione serve a verificare la capacità di scrivere autonomamente istruzioni, usare correttamente la sintassi o risolvere un problema senza assistenza, l'uso dell'AI può compromettere la validità della valutazione.

La conseguenza didattica è importante: non dobbiamo valutare sempre e soltanto il prodotto finale, ma neppure ignorare le abilità individuali che un determinato esercizio intende misurare.

### Come valuterei un esercizio di programmazione assistita dall'AI

Proporrei una consegna in tre fasi.

1. Fase 1 — Produzione

   Lo studente realizza la soluzione, con o senza AI secondo le regole dell'esercizio. Se utilizza l'assistente, conserva le decisioni rilevanti e verifica il codice prodotto.
2. Fase 2 — Verifica

   Lo studente esegue i test, analizza i casi limite e corregge almeno un difetto reale o introdotto intenzionalmente dal docente.
3. Fase 3 — Difesa tecnica

   Il docente pone domande sul codice, chiede di prevederne il comportamento e richiede una piccola modifica non preparata in precedenza.

La terza fase è particolarmente efficace perché verifica se lo studente possiede un modello mentale del programma, anziché limitarsi a riconoscere una soluzione apparentemente corretta.

Per esempio, in Java:

- Perché questo metodo è `static`?
- Che cosa succede se il parametro è `null`?
- Perché è stata scelta una `List` invece di un array?
- Quale test manca?
- Come modificheresti il metodo senza rompere il comportamento esistente?

Sono domande che funzionano sia con codice scritto a mano sia con codice generato.

## 5. Come applicare questo principio al lavoro di uno sviluppatore senior

Nel lavoro quotidiano, adotterei una regola operativa: l'AI può contribuire alla produzione, ma ogni modifica deve superare controlli proporzionati al rischio.

| Attività                         | Uso ragionevole dell'AI                         | Verifica richiesta                                     |
| -------------------------------- | ----------------------------------------------- | ------------------------------------------------------ |
| Generazione di codice ripetitivo | Automatizzare strutture e boilerplate           | Revisione e test                                       |
| Refactoring                      | Proporre alternative e semplificazioni          | Equivalenza del comportamento e test di regressione    |
| SQL                              | Generare query e suggerire indici               | Risultati, piani di esecuzione, prestazioni e permessi |
| Debugging                        | Formulare ipotesi e individuare possibili cause | Riproduzione del problema e conferma della causa       |
| Sicurezza                        | Segnalare rischi e suggerire contromisure       | Analisi indipendente e test specifici                  |
| Revisione del codice             | Evidenziare difetti e casi limite               | Valutazione critica di ogni osservazione               |

Nel caso di un'applicazione PHP o Spring Boot già in produzione, per esempio, non accetterei una modifica suggerita dall'AI senza verificare gli effetti sulle API esistenti, sull'autenticazione, sul database e sui log.

Per una funzione semplice, la verifica potrebbe essere rapida. Per una modifica al sistema di autorizzazione o alla gestione delle transazioni, servirebbe invece un controllo molto più approfondito.

La produttività aggiuntiva dell'AI è reale quando riduce il tempo necessario a ottenere una soluzione affidabile. Non lo è necessariamente quando produce più codice da controllare di quanto ne faccia risparmiare.

## 6. La mia valutazione critica del messaggio

Sono sostanzialmente d'accordo con il principio espresso da Torvalds, ma aggiungerei tre precisazioni.

Primo: comprendere non significa necessariamente conoscere ogni dettaglio implementativo. Uno sviluppatore backend può essere competente senza conoscere a memoria il bytecode JVM o il funzionamento interno di ogni libreria. Deve però sapere quali garanzie offre un componente, quali assunzioni fa e quando è necessario approfondire.

Secondo: la comprensione dichiarata deve essere verificabile. Non basta affermare di aver letto il codice generato. Occorre dimostrarlo attraverso test, debugging, revisione, spiegazioni tecniche e capacità di intervenire sulla soluzione.

Terzo: la responsabilità professionale include anche la provenienza e il contesto d'uso. In alcuni progetti è necessario dichiarare l'impiego dell'AI, proteggere dati e codice riservati o rispettare regole specifiche. L'assenza di divieti generalizzati non implica l'assenza di regole.

C'è poi un problema organizzativo che il messaggio non risolve del tutto: l'AI può aumentare la quantità di codice prodotto e, contemporaneamente, il carico di lavoro dei revisori. Una patch non diventa accettabile soltanto perché il suo autore è in grado di spiegarla; deve anche essere adeguata agli standard del progetto e sostenibile da mantenere.

In un progetto open source come il kernel Linux, dove la qualità delle modifiche e il lavoro dei maintainer sono cruciali, questo equilibrio è particolarmente delicato.

## 7. La sintesi che porterei in aula

## Tre principi per programmare nell'era dell'AI

1\. Usa gli strumenti per amplificare le capacità

Compilatori, IDE, librerie e assistenti AI permettono di lavorare a un livello di astrazione superiore. Rinunciare a uno strumento non dimostra automaticamente maggiore competenza.

2\. Non delegare la comprensione

Devi saper spiegare le decisioni importanti, riconoscere i limiti della soluzione e intervenire quando qualcosa non funziona.

3\. Assumiti la responsabilità del risultato

Il codice deve essere corretto, verificato, sicuro e manutenibile. Il fatto che sia stato scritto da una persona o generato con l'AI non elimina questa responsabilità.

La frase che sintetizza meglio il messaggio, anche dal punto di vista didattico, è questa:

Non valutare un programmatore in base agli strumenti che usa, ma in base a ciò che sa comprendere, verificare e realizzare con quegli strumenti.

È un principio valido tanto per chi mantiene il kernel Linux quanto per chi sviluppa un'applicazione aziendale o insegna programmazione a una classe ITS.

E ha una conseguenza concreta: nell'era dell'AI, la capacità di scrivere codice rimane importante, ma cresce il valore della capacità di leggere criticamente il codice, testarlo, correggerlo e giustificarne le scelte. L'AI rende queste competenze più importanti, non meno.

Per approfondire la discussione originale, puoi leggere lo scambio nella mailing list del kernel Linux: [Re: \[PATCH\] docs: remove Assisted-by references](https://mid.mail-archive.com/linux-kernel%40vger.kernel.org/msg2663526.html?utm_source=chatgpt.com).&#x20;

[image](https://www.google.com/s2/favicons?domain=https://mid.mail-archive.com\&sz=32)

mid.mail-archive.com
