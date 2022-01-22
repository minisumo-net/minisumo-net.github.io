---
title: "GCBASIC il compilatore Open Source per PIC"
excerpt: "Programmare un qualsiasi sistema di elaborazione dati in linguaggio assembler, ha i suoi pro e i suoi contro."
author: "Stefano Bonomi"
toc: true
toc_label: "Tavola dei contenuti"
toc_sticky: true
header:
  overlay_color: "#000"
  overlay_filter: "0.5"
  overlay_image: /assets/images/posts/BCI/PLB-with-EEG-helmet-and-BCI-up-low-task.jpg
  teaser: /assets/images/posts/BCI/PLB-with-EEG-helmet-and-BCI-up-low-task.jpg
categories:
  - Programming
tags:
  - GBASIC
---

Programmare un qualsiasi sistema di elaborazione dati in linguaggio assembler, ha i suoi pro e i suoi contro. Se da un lato il basso livello del codice macchina ci svela ogni segreto ed ogni “dietro le quinte” della nostra CPU, è altrettanto sicuro che ci obbliga a farlo, e da subito, permettendoci poco o per niente una curva di apprendimento abbordabile, soprattutto se non possiamo dedicare alla programmazione dei PIC, il tempo e la concentrazione che vorremmo.

{% include figure image_path="/assets/images/posts/gbasic/Cow.jpg" alt="Cow" caption="Cow" %}

E’ a questo punto che intervengono in nostro soccorso i cosiddetti compilatori.
Si tratta di programmi che ci permettono di scrivere i nostri software in un linguaggio maggiormente “digeribile” dell’assembler, occupandosi di fare per noi il “lavoro sporco”, la traduzione in linguaggio macchina.
Per i microcontrollori PIC sono disponibili compilatori di molti linguaggi ad alto livello…Basic, C, Pascal… quasi tutti a pagamento.
Personalmente non ho nulla contro il software a pagamento…sono io stesso un programmatore e capisco perfettamente che l’evoluzione esponenziale dell’informatica non sarebbe avvenuta senza il profitto.


Comunque mi rendo anche conto che soprattutto chi sviluppa software senza scopo di lucro, è giustamente interessato a trovare strumenti a basso costo, meglio ancora gratuiti. Great Cow Basic (di seguito GCB), è un compilatore Basic completamente open source (freeware) per i nostri PIC.

# Le potenzialità

Cionostante, vi assicuro, è molto potente, e dispone addirittura di caratteristiche avanzate che non sono disponibili neppure nei compilatori commerciali.

* Costrutti di controllo IF…THEN con ENDIF
* Chiamata di Routines definite dall’utente tramite GOSUB…RETURN
* Funzioni e SUB definibili dall’utente, con parametri locali
* Cicli iterativi For….Next, Do/While/Until….Loop
* Variabili ad 8 bit e 16 bit. Variabili stringa
* Librerie per la gestione di LCD con interfacciamento a 8, 4 e 2 pin (Predko design)
* Libreria gestione tastiera PS2
* Gestione A/D
* RS232
* PWM hard/Soft
* ...e molto altro ancora...

C’è di far venire l’acquolina in bocca, eh?

GCB scrive programmi compatibili con la maggior parte dei PIC della serie 10/12/16.

# INIZIARE CON GCB

Portiamoci alla home page di GCB digitando nel nostro browser internet [http://gcbasic.sourceforge.net/index.htm](http://gcbasic.sourceforge.net/index.htm)

Clicchiamo su Download, e scarichiamo l’ultimo installer del compilatore (attualmente la 0.9.2.0), che è comprensivo delle GPutils, necessarie a GCB.
Una volta installato il pacchetto, saremmo già pronti per compilare i nostri applicativi, ma che cos’è un compilatore senza un editor il più possibile integrato?
E’ disponibile in nostro soccorso un editor freeware anch’esso, che può essere personalizzato per lavorare con GCB.
Il suo nome è Crimson Editor. Per scaricarlo portiamoci dalla home page nella sezione “Getting Started”. A questo punto in fondo alla pagine troveremo il link per l’editor in questione. (Figura 1)

{% include figure image_path="/assets/images/posts/gbasic/Figura 1.jpeg" alt="Getting Started" caption="Getting Started" %}

Scarichiamo quindi anche il supporto per il giusto “highlighting” dei comandi GCB (appena sotto al link per il Crimson Editor). Un aspetto interessante di Crimson Editor è che possiamo far colorare in automatico le sorgenti GCB, in modo differente seguendo la sintassi del compilatore. Vi assicuro che ne vale la pena…con un pò di pratica, coglierete a colpo d’occhio buona parte degli errori di sintassi.

# Personalizzazione di Crimson Editor

Innanzitutto mettiamo il programma in grado di comportarsi da vero e proprio IDE nei confronti del nostro compilatore.
Estraiamo i due file contenuti in “CE_GCBASIC_Highlighting.zip” e copiamoli all’interno della directory “spec” che si trova dentro al folder di Crimson Editor (tipicamente C:\Programmi\Crimson Editor).

Poi, una volta lanciato Crimson, portiamoci nel menu “Tools” e selezioniamo “Preferences”.

{% include figure image_path="/assets/images/posts/gbasic/Figura 2.jpeg" alt="Configurazione" caption="Configurazione" %}

Nella finestra che comparirà, portiamoci su “Tools” – “User Tools” e definiamo l’hot key F9 come da figura e clicchiamo su OK.
Da questo momento, saremmo in grado di compilare i nostri programmi dall’interno di Crimson premendo il tasto F9.

Sarà l’editor a richiamare il compilatore e a fargli eseguire il suo lavoro. nella finestra “Output” vedremo in tempo reale i messaggi del compilatore, e soprattutto l’insorgere di eventuali problemi di compilazione.

# Le qualità del GCBASIC

Ma, direte voi, come si fa a colorare li comandi GCBASIC ? E’ possibile farlo in due modi; manuale ed automatico.

Per colorare i comandi in modo manuale, è necessario portarsi nel menù di Crimson all voce “Document” – “Syntax type” e selezionare la sintassi GCBASIC. Non è però molto pratico; meglio fare in modo che i nostri programmi siano riconosciuti dall’Editor come programmi GCBASIC automaticamente.

Se vi interessa questa possibilità (molto comoda), è necessario procedere come segue:

1. Portatevi nuovamente nel menu “Tools” – “Preferences” e selezioniamo “Filters”.
2. Portatevi alla prima voce contrassegnata come “empty” e riempite i campi come da figura.
3. Premete OK

{% include figure image_path="/assets/images/posts/gbasic/Figura 3.jpeg" alt="Opzioni" caption="Opzioni" %}

Aprite a questo punto il Blocco note di Windows e create il file “extension.gcb” come da figura.

Questo file va salvato nella sottocartella “link” di Crimson Editor. Bene! se siete arrivati fino a qui e se salverete i vostri programmi con l’estensione .GCB, Crimson Editor li riconoscerà come sorgenti Great Cow Basic e ne colorerà la sintassi in modo appropriato.

Per fare questo, selezionate “File” – “Save as” e GcBasic come formato di salvataggio.

{% include figure image_path="/assets/images/posts/gbasic/Figura 4.jpeg" alt="Blocco note" caption="Blocco note" %}

# Primo Programma

Facciamo partire Crimson Editor e cominciamo la scrittura di un nuovo programma cliccando su “File” – “New” Innanzitutto è necessario selezionare il modello del proprio PIC e la velocità di clock, usando il comando #chip

Nel mio caso trattandosi di un 16F690 che intendo “cloccare” a 4Mhz, il comando giusto è:

```basic
#chip 16F690,4
```

Poi è necessaria l’onnipresente Word di configurazione. Il comando è #config e la sintassi è uguale a quella dell’MPLAB, quindi io uso:

```
#config _INTRC_OSC_NOCLKOUT, _WDT_OFF,_PWRTE_OFF,_MCLRE_OFF,_CP_OFF,_BOR_OFF, _IESO_OFF,_FCMEN_OFF
```

GCBASIC setta automaticamente tutte le porte digitali, quindi intervenire sul parametro ANSEL, non è necessario se volete avere tutti gli I/O digitali.

I commenti cominciano con ‘ (asterisco) e Crimson Editor li colorerà in verde.

```basic
”””””””””””””
‘ Prova Great Cow Basic  ‘
”””””””””””””
#chip 16F690,4 ‘Definisce Pic e velocità di clock
#config _INTRC_OSC_NOCLKOUT, _WDT_OFF,_PWRTE_OFF,_MCLRE_OFF,_CP_OFF, _BOR_OFF, _IESO_OFF,_FCMEN_OFF
#Define LED PORTC.0 ‘Definiamo la label LED, come equivalente al pin 0 di PORTC
‘ da adesso in poi ogni riferimento a LED, in realtà punta al pin 0 della Porta C del PIC
#Define Ritardo 1 sec ‘Definiamo la label Ritardo come equivalente ad 1 secondo
‘ come vedete la direttiva #Define è molto potente
‘ possiamo definire puntatori a porte del PIC e a qualsiasi tipo di valore
DIR PORTC b’00000000′ ‘definiamo PORTC in output
PORTC = b’00000000′   ‘settiamo tutti i pin di PORTC a 0
‘ la lettera b significa che il numero compreso tra gli apici è in forma binaria
‘ non specificando la notazione il numero si intende in forma decimale,
‘ mentre 0x prima del valore numerico equivale a specificare un numero esadecimale

do
‘Accende l’ipotetico LED collegato al PIN 0 di PORTC
SET LED ON
‘Aspetta 1 secondo’
WAIT Ritardo
‘ Pone a zero il bit zero di PORTC spegnendo il LED
SET LED OFF
‘Aspetta nuovamente 1 secondo
WAIT Ritardo
‘Cicla infinitamente
loop
```

# Come funziona

Come vedete si tratta di un vero e proprio programma Basic; notate che avremmo potuto usare la direttiva #Define per definire direttamente la porta del LED ad ON e a OFF in questo modo:

```
#Define LedOn  SET PORTC.0 ON
#Define LedOff SET PORTC.0 OFF
```

Dopo aver scritto queste definizioni, nel nostro programma sarebbe stato sufficiente utilizzare LedON per portare il pin 0 di PORTC a livello logico 1 e LedOff per portarlo a 0. COMPILARE IL PROGRAMMA

Salviamo il nostro programma con “Save As” in Crimson Editor selezionando il formato GCBASIC. Premiamo a questo punto il tasto F9.
Se tutto è andato come dovrebbe, nella finestra Output, Crimson ci informerà che la compilazione è andata a buon fine.

{% include figure image_path="/assets/images/posts/gbasic/Figura 5.jpeg" alt="Interfaccia" caption="Interfaccia" %}

Il compilatore ha generato nella sua cartella 3 file; il primo prende il nome di “compiled.asm”, il secondo di “compiled.lst”, mentre il terzo “compiled.hex” “compiled.hex” è il file oggetto pronto per essere caricato sul nostro PIC, mentre il secondo è il file cosiddetto di Listing, esso contiene infatti il nostro programma convertito in linguaggio assembler con a fianco la traduzione in esadecimale, già formattato per la stampa. L’ultimo file (compiled.asm) equivale a “compiled.lst”, ma non è formattato e presenta solamente la traduzione che il compilatore ha effettuato in linguaggio assembler partendo dal nostro codice Basic.

Sarà quindi sufficiente programmare il PIC con il file compiled.hex usando il nostro programmatore.

Bene! Spero di essere riuscito ad incuriosirvi riguardo a questo compilatore semplice ma potente. Vi segnalo la presenza di file di Help e di utili esempi all’interno della cartella di Great Cow Basic. Dalla Home page di GCB, potrete navigare fino al forum di supporto, dove potrete postare le vostre richieste e consultare i POST degli altri utilizzatori.