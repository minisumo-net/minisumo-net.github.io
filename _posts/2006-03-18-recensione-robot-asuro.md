---
title: "Recensione Robot Asuro"
excerpt: "Asuro è un piccolo robot programmabile in C con un microcontrollore ATMEL ATMEGA8L. Nato come robot didattico, questo è ottimo per le prime sperimentazioni nel mondo della robotica."
author: "Raffaello Bonghi"
classes: wide
header:
  overlay_color: "#000"
  overlay_filter: "0.5"
  overlay_image: /assets/images/posts/asuro/p3180191.jpg
  teaser: /assets/images/posts/asuro/p3180191.jpg
categories:
  - Recensioni
tags:
  - Asuro
architettura:
  - image_path: /assets/images/posts/asuro/Atmel.jpeg
  - image_path: /assets/images/posts/asuro/cd4081b.jpg
motori:
  - image_path: /assets/images/posts/asuro/PonteH.jpeg
  - image_path: /assets/images/posts/asuro/p3180185.jpg
encoder:
  - image_path: /assets/images/posts/asuro/ruote.jpg
  - image_path: /assets/images/posts/asuro/p3180182.jpg
meccanica:
  - image_path: /assets/images/posts/asuro/p3180187.jpg
  - image_path: /assets/images/posts/asuro/p3180191.jpg
estensione:
  - image_path: /assets/images/posts/asuro/extension3.jpg
  - image_path: /assets/images/posts/asuro/extension4.jpg
---

Il robot ci è giunto in una scatola di dimensioni 20 x 17 x 7 cm

All’interno della scatola erano presenti:
* CD con manuale
* Scheda del robot Asuro
* Scheda del trasmettitore Infrarossi
* Parti elettroniche e meccaniche
* Materiale vario ed una pallina da ping-pong.

Il robot appare senza dubbio per un pubblico giovane, anche se durante il montaggio c’è bisogno di una certa preparazione per poter saldare correttamente il robot (all’interno del manuale è presente una breve guida che spiega il corretto uso del saldatore).

Dopo aver montato il robot e la scheda per la programmazione seriale il robot risulta già operativo grazie ad un programma già caricato all’interno del PIC che verifica i motori ed i sensori del robot.

Ma adesso iniziamo ad analizzare la scheda del robot e tutte le caratteristiche fondamentali, partendo dal microcontrollore che esso adotta.

{% include figure image_path="/assets/images/posts/asuro/ComponentiA.jpeg" alt="Componenti" caption="Componenti" %}

# Il robot

Quello che colpisce di Asuro sono principalmente le sue misure, che in uno spazio di 100mm X 75mm riesca a contenere un piccolo cervello elettronico che possa far funzionare il robot facendolo interagire con il mondo. Il microcontrollore in questione è L’ ATMEL. Le caratteristiche fondamentali di questo microcontrollore sono queste:

* Architettura avanzata RISC
* 512 Byte di EEPROM
* 8 MHz di clock
* 3 Canali PWM
* 6 canali ADC

{% include gallery id="architettura" caption="architettura" %}

# I Motori

Infatti il microcontrollore gestirà sia i sensori presenti sul robot che i motori che gli permetteranno di muoversi nei pavimenti di casa nostra, la gestione viene eseguita da un ponte H ed attraverso le porte AND del secondo integrato il CD4081B presente che permetteranno ad Asuro il controllo in PWM dei motori.

{% include gallery id="motori" caption="Ponte H" %}

Il Ponte H utilizzato a differenza del Sumovore che adotta un L293D, sono 4 transistor più come detto prima in uscita dalle basi di ciascun transistor gli ingressi delle porte AND del CD4081B.

I transistori in questione sono 2 BC327 e 2 BC337 per ciascun motore, che come possiamo vedere infatti in foto sono disposti affianco ai motori del robot.

{% include gallery id="encoder" caption="Encoder" %}

I motori utilizzati da Asuro sono dei classici motori a spazzola, questi sono molto utilizzati nelle gare di mini4WD, sono legati alla scheda attraverso delle fascette, che non ne assicurano un perfetto ancoraggio. Il sistema di motoriduzione si trova montato direttamente attraverso 2 ruote di ingranaggi sulla scheda principale, questo comporta il massimo utilizzo degli spazzi presenti sulla scheda portando ad una ottimizzazione completa del robot. Sulla seconda ruota è presente un disco colorato questo permette la lettura della velocità della ruota attraverso un blocco trasmettitore ricevitore infrarosso che a seconda della riflessione della luce rimbalzante sul disco colorato emette una onda quadra che è perfettamente interpretabile dal microcontrollore per gestire la velocità dello stesso.

# I sensori

I sensori utilizzato sono 3 micro-interruttori per lato per un totale di 6. Questi permettono ad Asuro di reagire a qualsiasi ostacolo presente durante il percorso. Da notare infatti la singolare struttura della scheda che permette di riconoscere anche piccoli ostacoli frontali per mezzo della piccola rientranza.

Nel corredo del robot è presente anche un sistema line follower che permette di riconoscere una linea sul terreno.

Questo sistema è costituito da 2 foto-diodi sensibili alla luce rossa ed un led rosso centrale, che a seconda della luce riflessa permettono grazie al fenomeno della riflessione il riconoscimento del colore del terreno, ma per maggiori informazioni vi lascio leggere il precedente articolo presentato da Antonio: Rimaniamo nel ring

{% include figure image_path="/assets/images/posts/asuro/p3180186.jpg" alt="Sensori" caption="Sensori" %}

# La Meccanica

Come anticipato prima la meccanica di Asuro è costituita da un blocco Motore Motoriduzione direttamente montato sulla scheda comportanto una particolare compattezza del sistema. Ma l’ultima parte che ci manca di analizzare è la ruota. Questa è in PVC ed hanno un diametro di 40mm.
Per quanto riguarda il terzo appoggio del robot non si può dire che la soluzione trovata dalla AREXX sia geniale, questa è costituita da una semisfera di una pallina da ping-pong incollata sotto la scheda, tra il sensore di linea e le fascette che legano i motori alla scheda, permettendo un movimento fluido su qualsiasi superficie.

{% include gallery id="meccanica" caption="Vista robot" %}

# Le altre schede

{% include figure image_path="/assets/images/posts/asuro/p3180192.jpg" alt="Comunicazione infrarossi" caption="Comunicazione infrarossi" %}

La seconda scheda inclusa nel corredo del Robot, permette ad Asuro la riprogrammazione attraverso il PC del Microcontrollore ATMEL presente. La scheda utilizza la porta Seriale 232 che attraverso l’integrato NE555 ed un sistema Infrarossi ritrasmette il segnale al robot senza dover collegare nessun connettore. Sempre su questa scheda è presente un trimmer da 10K che permette di regolare la potenza del segnale in uscita del trasmettitore infrarosso in modo da permettere una programmazione di Asuro anche da una discreta distanza.

La AREXX vende anche per chi non disponesse di una porta seriale un trasmettitore via USB.

{% include figure image_path="/assets/images/posts/asuro/usb.jpg" alt="USB" caption="USB" %}

Asuro non possiede molte schede di espansione le uniche presenti sono la“Extension Board”

{% include gallery id="estensione" caption="Estensione" %}

Mentre è prevista in uscita una futura scheda che permetterà ad Asuro di gestire un LCD e 3 pulsanti.

{% include figure image_path="/assets/images/posts/asuro/lcd_panel.jpg" alt="Pannello LCD" caption="Pannello LCD" %}

# Il software di programmazione

Dopo aver trattato delle caratteristiche hardware del robot possiamo notare anche le interessanti doti di questo robot per quanto riguarda la programmazione.

Nel corredo di questo robot infatti è presente una suite sia Windows che Linux del sistema di programmazione di Asuro
I programmi presenti sono per chi utilizza Windows:
* WinAVR Suite ufficiale dell’Atmel per la programmazione in C del robot
* ASURO Flash che permette di inviare il codice dal PC al Robot

Il robot si programma in C e per chi utilizza Windows la suite inclusa nel CD è WinAVR.

{% include figure image_path="/assets/images/posts/asuro/Software.jpeg" alt="Software" caption="Software" %}

Per quanto riguarda chi Utilizza Linux “AVR-Binutils-2.13.90 – i386” la suite che permette di programmare in C il robot
ASURO Flash è il programma che permette il download del codice dal PC al robot .
Utili anche i codici di prova per poter provare il robot questi codici di esempio sono utilizzabili sia per chi utilizza Linux che Windows

Sono molto importanti le istruzioni che permettono il corretto funzionamento del sistema di programmazione.

{% include figure image_path="/assets/images/posts/asuro/SoftwareLinux.jpeg" alt="Software Linux" caption="Software Linux" %}

# Conclusioni

Come detto all’inizio di questa recensione il robot nell’ambito didattico risulta essere all’avanguardia soprattutto per i sensori e per il sistema di programmazione che questo adotta.
Per chi non ha mai usato un saldatore può risultare difficoltoso saldare l’intero robot e la mancanza di un kit completo comporta la vendita per un pubblico  ristretto.
Ciò non toglie che possa rimanere come ottimo punto di partenza per chi inizia ad usare un robot del genere per i primi esperimenti di robotica.

![Arexx]({{ '/assets/images/posts/asuro/main_logo.gif' | relative_url }})

* Per poter scaricare gli aggiornamenti di [WinAVR](http://winavr.sourceforge.net/)
* Per quanto riguarda gli aggiornamenti di [ASURO](http://www.arexx.com/) e le ultime novità

![Farnell]({{ '/assets/images/posts/asuro/logo1.gif' | relative_url }})

Asuro è in vendita su **Farnell In One** con il seguente codice: **809-2575 al prezzo di 41,50€** iva esclusa