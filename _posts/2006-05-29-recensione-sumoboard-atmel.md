---
title: "Recensione Sumoboard ATMEL"
excerpt: "Eravamo fermi un paio di mesi alla recensione del Sumovore, questa volta analizzeremo l’espansione che permette al Sumovore di essere programmato."
author: "Raffaello Bonghi"
classes: wide
header:
  overlay_color: "#000"
  overlay_filter: "0.5"
  overlay_image: /assets/images/posts/sumovore-programmazione/p5100316.jpg
  teaser: /assets/images/posts/sumovore-programmazione/p5100316.jpg
categories:
  - Recensioni
tags:
  - Sumovore
---

Eravamo fermi un paio di mesi alla recensione del Sumovore, questa volta analizzeremo l’espansione che permette al Sumovore di essere programmato. Ed useremo la versione con il L’Atmel Mega8L.

{% include figure image_path="/assets/images/posts/sumovore-programmazione/p5100316.jpg" alt="Sotto l'etichetta" caption="Sotto l'etichetta" %}
Scheda Atmel

La scheda ci è giunta in kit di montaggio, in una busta, vi era contenuta:

* Circuito stampato
* Componentistica (resistenze, connettori, etc)
* Atmel Mega8L
* Sensore QRD1114
* Manuale per il montaggio della scheda.

Dopo il semplice montaggio della scheda, grazie alla guida presente nel prodotto in soltanto 30 minuti, la scheda permetteva già di essere provata sul robot e programmata.

Ma iniziamo a studiarne le caratteristiche hardware.

# La scheda

La scheda dalle dimensioni di 7 x 7,5 cm è dotata di tutta l’elettronica necessaria per poter gestire l’ATMEL. La prima cosa che balza all’occhio è sicuramente l’unico integrato presente sulla scheda, il microcontrollore ATMEL mega8L. Ottimo per le seguenti caratteristiche:

* Microcontrollore a 8-bit
* Architettura RISC
* 16 MIPS a 16MHz
* 512 Byte di memoria EEPROM
* 1K Byte di SRAM interna
* 3 canali PWM
* 6 canali ADC
* 4 Canali con precisione a 10-bit
* 2 Canali con precisione a 8-bit
* Oscillatore Interno RC
* 23 ingressi/uscite programmabili

La scheda di espansione ATMEL lavora come si può notare senza alcun oscillatore ceramico, anche se sulla scheda c’è lo spazio predisposto per un suo futuro montaggio, ma utilizza un circuito RC integrato nel microcontrollore.

Partendo dalla zona dove vi è posto l’Atmel possiamo notare 5 simpatici microled rossi, questi possono essere utilizzati come diagnostica del robot o per qualsiasi altra idea che abbia in mente il programmatore, sono collegati al microcontrollore, quindi sono gestibili via software.

Affianco possiamo trovare 3 connettori per servocomando, che come i precedenti led sono controllati dal microcontrollore, importante da sottolineare la presenza del transistor Q2 che abilita l’ingresso della tensione a 6 volt proveniente dalle batterie.

Poco più in alto troviamo un transistor, un LED verde ed un primo connettore, questi servono, per la programmazione attraverso l’apposito cavo (che tratteremo più avanti) per la programmazione del sumovore. Dal lato opposto della scheda è presente un secondo connettore che permette la programmazione della scheda attraverso un altro tipo di connettore STK500 affianco a questo è presente il tasto di reset che permette di riavviare il microcontrollore.

Nella parte opposta all’ATMEL è presente una millefiori utile per costruire piccoli circuiti da implementare sul robot. Ed è proprio questa zona della scheda che la rende sicuramente più grande della “Discrete brainboard” riuscendo perfino a coprire le batterie presenti sulla parte alta della scheda.

# Sul Robot

{% include figure image_path="/assets/images/posts/sumovore-programmazione/p5100318.jpg" alt="Scheda montata sul robot" caption="Scheda montata sul robot" %}

Prima di iniziare a programmare il robot è consigliato montare anche il 5 sensore di linea nella scheda sensori del robot in modo tale da sfruttare a pieno le capacità di Line Follower del robot.

Importa da notare è il funzionamento della scheda subito dopo essere stata montata sul robot, grazie al software preinstallato sul robot che gli permette di funzionare. Il programma permette al robot di funzionare in due modalità:

1. **Line Follower** – Quando tutti i sensori di linea rilevano un fondo bianco
2. **Mini Sumo** – quando i sensori di linea rilevano un fondo nero

Come detto prima la scheda per essere programmata ha bisogno di un particolare connettore che permette l’interfacciamento della scheda al computer.

Quando dovremo programmare il nostro robot sarà necessario sapere come ogni sensore e periferica sono connessi al microcontrollore, attraverso questo schema potremo sapere ogni collegamento:

{% include figure image_path="/assets/images/posts/sumovore-programmazione/connessioniAtmel.jpeg" alt="connessioni Atmel" caption="connessioni Atmel" %}

# Il connettore per la programmazione

Per poterlo costruire avremo bisogno di un cavo elettrico a 5 poli, una connettore per porta parallela maschio e del connettore strip a 5 vie.

{% include figure image_path="/assets/images/posts/sumovore-programmazione/p5100305.jpg" alt="Connettore" caption="Connettore" %}

Per montarlo basterà seguire questo schema:

{% include figure image_path="/assets/images/posts/sumovore-programmazione/connettore2.jpeg" alt="Montaggio connettore" caption="Montaggio connettore" %}

Il risultato che avremo sarà questo:

{% include figure image_path="/assets/images/posts/sumovore-programmazione/p5100321.jpg" alt="Assemblaggio" caption="Assemblaggio" %}

# Il WinAVR

{% include figure image_path="/assets/images/posts/sumovore-programmazione/WinWAR.jpeg" alt="WinWAR" caption="WinWAR" %}

La suite di programmazione dell’Atmel utilizzata e consigliata dalla Solarbotics è il WinAVR.

Questa è una potente suite di sviluppo che permette la programmazione in C, C++ ed in altri linguaggi.

Nello ZIP presente nel WinAVR della Solarbotics vi è spiegato come installare correttamente la suite e come interfacciare il robot al computer, Queste sono le informazioni più importanti da dover seguire:

1. Fare doppio click su “WinAVR-20040404-bin-install.exe” installandolo sul computer. Seguire la procedura guidata. E’ consigliato installarlo su “c:\WinAVR” in modo tale da avere un path breve.
Una volta installato si aprirà il README del [WinAVR].
2. Il programma installerà 7 icone sul desktop del computer, il “Programmers Notepad” permette di programmare la brain board del Sumovore.Il resto si può pure eliminare.
3. Se si utilizza un sistema con Windows NT o XP si deve installare “install_giveio.bat”, Questo permetterà la corretta gestione della porta seriale  e della gestione del robot.
4. Per imparare a fare pratica con la programmazione del sumovore , basta aprire dal “Programmers Notepad” il file “Sumoline.c” ed andando su “Tools” cliccare “[WinAVR] Program”.
5. Il programma inizierà la compilazione del programma e l’invio del programma al microcontrollore Atmel presente sulla scheda, a patto che questa sia accesa e collegata al computer.

La suite utilizzata è il WinAVR scaricabile da:

http://downloads.solarbotics.com/PDF/Sumovore_Atmel_Brainboard_WinAVR.zip il file è da 11,5MB

Questa scheda è acquistabile, come il robot al sito della solarbotics http://www.solarbotics.com/ o dal rivenditore ufficiale italiano: http://www.robot-italy.com/ .

# Il sensore posteriore

Un problema che molto spesso capita quando si usa il Sumovore è la visione posteriore.
Il nostro sumovore è dotato di uno spazio per il montaggio di un sensore infrarosso posteriore, evitando spiacevoli partire perse.

Per poterlo montare avremo bisogno di pochi componenti:

{% include figure image_path="/assets/images/posts/sumovore-programmazione/p5100309.jpg" alt="Componenti sensore posteriore" caption="Componenti sensore posteriore" %}

* Un sensore PNA 4602
* Un cavetto
* Un condensatore da 0.1uF

{% include figure image_path="/assets/images/posts/sumovore-programmazione/connessione.jpeg" alt="Connessione" caption="Connessione" %}

La rotazione che effettuerà il robot sarà a nostra discrezione se a sinistra o a destra, basta saldare il cavo su uno dei due punti indicati

{% include figure image_path="/assets/images/posts/sumovore-programmazione/montaggioretro.jpeg" alt="Montaggio retro" caption="Montaggio retro" %}

Il risultato che avremo sarà questo:

{% include figure image_path="/assets/images/posts/sumovore-programmazione/p5100315.jpg" alt="Risultato finale" caption="Risultato finale" %}

Come possiamo notare la scheda non predispone di una uscita a 38Khz per l’emettitore, ma se stiamo attenti, guardando lo schema potremo notare che la spia di accensione rossa in realtà è collegata gli emettitori frontali della scheda, permettendo quindi l’emissione a 38Khz ideale per il nostro minisumo.

Per fare ciò basterà aggiungere un piccolo LED infrarosso nella stessa connessione della spia di accensione.

{% include figure image_path="/assets/images/posts/sumovore-programmazione/LEDposteriore.jpeg" alt="LED posteriore" caption="LED posteriore" %}

**IL SENSORE POSTERIORE NON FUNZIONA CON L’ESPANSIONE SUMOBOARD ATMEL**