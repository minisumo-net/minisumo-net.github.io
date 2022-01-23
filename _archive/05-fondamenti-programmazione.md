---
title: "Fondamenti di programmazione"
excerpt: "Fondamenti di programmazione"
permalink: /tutorial/fondamenti-programmazione
author: "Raffaello Bonghi"
header:
  overlay_color: "#000"
  overlay_filter: "0.5"
  overlay_image: /assets/images/tutorial/programmazione/MPLAB.gif
  teaser: /assets/images/tutorial/programmazione/MPLAB.gif
author: "Raffaello Bonghi"
classes: wide
---

Con questa prima lezione inizieremo a prendere mano nella programmazione con il PicBasic.

Nel corso dell’articolo installeremo i software necessari alla programmazione ed alla compilazione dei programmi scritti.

MPLAB è un programma che permette di creare e sviluppare con estrema facilità. Rientra negli ambienti di sviluppo (IDE) ed è dedicato ad unun determinato linguaggio standard necessario per programmare un PIC.

Per poterlo utilizzare non avremo bisogno di alcun promt dei comandi, ma attraverso l’interfaccia grafica potremo gestire le varie fasi di programmazione (e di emulazione, se abbiamo l’ICD 2).

{% include figure image_path="/assets/images/tutorial/programmazione/MPLAB.gif" alt="Schermata MPLAB" caption="Schermata MPLAB" %}

Dopo averlo installato correttamente avremo sul nostro computer un programma che ci permetterà di trasformare il programma in Assembler, attraverso la suite integrata MPASM, di trasformarlo in codice esadecimale, codice macchina adatto al nostro microcontrollore.

Per installarlo seguiamo passo passo le istruzioni presenti fino al completamento dell’installazione.

# Il Pic Basic Pro

Il secondo programma che andremo ad installare è il PBP o PicBasic Pro. Questo infatti ci permette di decodificare il programma scritto in PicBasic Pro nel linguaggio adatto all’MPASM, l’assembler.

Potremo programmare SOLAMENTE questi PIC:

**16F627(A), 16F628(A), 16F84(A), 16F870, 16F871, 16F872, 16F873(A), 16F874(A), 16F876(A), 16F877(A)**

Avremo a disposizione **soltanto 31 LINEE** di codice (esclusi commenti e spazi bianchi).

Per poterlo installare basterà avviare l’eseguibile e seguire le istruzione presenti.

# Micro Code Studio

A questo punto siamo arrivati ad installare il Micro Code Studio.

{% include figure image_path="/assets/images/tutorial/programmazione/MicroCodeStudio.gif" alt="Micro Code Studio" caption="Micro Code Studio" %}

Il Micro Code Studio (MCS) è un ambiente di sviluppo che permette l’ingrazione del PBP e del MPLAB permettendo al programmatore di scrivere e creare il codice macchina senza dover uscire dal programma, tutto questo attraverso un semplice pulsante.
Il Micro code Studio è anche lui, come l’MPLAB IDE un software totalmente gratuito che potremo installarlo sul nostro computer.

Adesso dovremo configurare il Micro Code Studio per permettere il riconoscimento tutti i software precedentemente installati.

# Configurazione

Avviamo il Micro Code Studio e noteremo che il programma eseguirà una scansione per cercare i programmi di sviluppo. Una volta completata la ricerca dovremo andare a verificare che il Micro Code Studi abbia trovato tutti i programmi precendetemente installati.
Per fare ciò basterò andare in:

View –>  PicBasic Option

{% include figure image_path="/assets/images/tutorial/programmazione/conf1.gif" alt="Configurazione 1" caption="Configurazione 1" %}

controllare che sia stato correttamente riconosciuto il compilatore PBP, se questo non fosse così andiamo su “Find Manually” e selezioniamo la cartella dove è stato installato il PBP ( il compilatore lo troveremo all’interno di c:\pbp )
Fatto ciò clicchiamo sulla linguetta “Assembler” e verifichiamo che sia stato riconosciuto l’assemblatore.
Se non è stato rilevato dovremo fare questo:

{% include figure image_path="/assets/images/tutorial/programmazione/conf2.gif" alt="Configurazione 2" caption="Configurazione 2" %}

Prima di tutto spuntare “Microchip MPASM” e dopodiché cliccare su “Find Automatically” in modo tale da avviare automaticamente la ricerca, se il programma non riuscisse a trovare l’assemblatore possiamo cercarlo manualmente andando nella seguente cartella:

c:\programmi\microchip\mpasm suite

Verifichiamo che sia selezionato **INHX8M**.

Clicchiamo su “OK” salvando la nuova configurazione.

Notiamo che è presente all’interno del programma un menu a cascata con tutti i modelli dei PIC della microchip. Selezioniamo ogni qual volta che programmiamo il PIC di nostro utilizzo.

Quello che useremo nel corso delle lezioni sarà il 16F84 o 16F84A.

{% include figure image_path="/assets/images/tutorial/programmazione/conf3.gif" alt="Configurazione 3" caption="Configurazione 3" %}

Finalmente abbiamo completato la configurazione del Micro Code studio, possiamo finalmente passare alla programmazione in Pic Basic Pro dei nostri robot.

# L’Hardware

Utilizzeremo come scheda per i nostri corsi quella del minisumo con 16F84(A)

{% include figure image_path="/assets/images/tutorial/programmazione/scheda3.jpg" alt="Elettronica" caption="Elettronica" %}

Il programma che andremo a scrivere è molto semplice ma al contempo utile per iniziare a prendere mano con la suite da poco installata sul PC.

# Il primo programma

```basic
DEFINE OSC 4 ‘definisce la velocità  dell’oscillatore
‘********************* VARIABILI ********************************
LEDV VAR PortA.0 ‘LED Verde posto a Destra
LEDR VAR PortA.1 ‘LED Rosso posto a Sinistra
MOTORR VAR PortA.2 ‘Controllo Motore Destra
MOTORL VAR PortA.3 ‘Controllo Motore Sinistra
PULSANTE VAR PortB.0 ‘Pulsante Di controllo
LINEAR VAR PortB.1 ‘Sensore di Linea Infrarosso QRB1134 Destra
LINEAL VAR PortB.2 ‘Sensore di Linea Infrarosso QRB1134 Sinistra
SHARPR VAR PortB.3 ‘Sensore rilevamento avversario GP2D15 Destra
SHARPL VAR PortB.4 ‘Sensore rilevamento avversario GP2D15 Sinistra
RELE VAR PortB.5 ‘Relè Abilitazione PonteH
‘****************************************************************

OUTPUT LEDV ‘setta come uscita PortA.0
‘Per il PIC16F84(A) è il pin 6
Loop: ‘l’etichetta del ciclo
HIGH LEDV ‘Porta a valore alto PortA.0 (da 5V su PortB.0)
PAUSE 200 ‘Mette in pausa il programma per 200 millisecondi
LOW LEDV ‘Porta a valore basso PortA.0 (da 0V su PortB.0)
PAUSE 200 ‘Mette in pausa il programma per 200 millisecondi
GOTO Loop ‘Ritorna sull’etichetta “loop”
```

Una volta scritto il programma nell’ambiente di sviluppo potremo notare che certe istruzioni, parole chiave, vengono evidenziate in grassetto ed altre vengono colorate di blu.
Questo perché Micro Code Studio discrimina i commenti dai comandi e dalle impostazioni che andremo a scrivere.

In questa prima guida vedremo molto rapidamente il significato di queste istruzioni.

* **DEFINE** definisce il quarzo presente nella nostra scheda nel nostro caso è da 4 Mhz
* **VAR** definisce all’interno del programma la variabile che andremo ad utilizzare, ma nel caso della programmazione con i PIC anche la porta su cui è collegato il nostro sensore, pulsante o altro hardware.
* **OUTPUT** definisce la porta come uscita.
* **HIGH** e LOW generano in una determinata porta un valore alto (5V ) o basso (0V) *Nel nostro caso illumini o spenga il LED presente nel circuito.*
* **PAUSE** genera una pausa all’interno ciclo rallentando le operazioni del 16F84A
* **GOTO** permette di tornare in un punto specifico del programma.
  
Nel nostro caso l’istruzione GOTO crea un “loop”, quindi un ciclo continuo.

Il risultato finale di questo programma sarà infatti un lampeggio del LED verde abbastanza accentuato.
Si spegnerà ed accenderà ogni 0.2 secondi

Adesso è il turno di caricare il programma sul PIC del robot.

# Caricamento sul PIC

La prima operazione sarà quella di far partire la compilazione in modo tale da avere il giusto file da caricare sul PIC.

{% include figure image_path="/assets/images/tutorial/programmazione/conf3.gif" alt="Compilazione" caption="Compilazione" %}

Per fare ciò basta premere il tasto “Compile Only” affianco alla lista dei processi, o schiacciare F9.

Ci verrà chiesto di salvare il programma: lo salveremo con “Lezione1”

In poco tempo vedremo che il MCS avvierà tutti i programmi in modo tale da creare il codice macchina adatto al PIC.
Andiamo nella cartella di default del MCS (Micro Code Studio): C:\Programmi\Mecanique\MCS

Troveremo ben **6** file generati nel corso della compilazione:

* **Lezione1.bas** questo è il nostro programma come lo abbiamo scritto
* **Lezione1.asm** questo è il programma trasformato in assembler
* **Lezione1.cod**
* **Lezione1.lst**
* **Lezione1.mac**

Lezione1.hex questo è il programma scritto in codice macchina adatto per il nostro robot.

A questo punto useremo il nostro programmatore di PIC e scaricheremo il file Lezione1.hex sul PIC 16F84 in modo tale da vedere il programma in funzione.