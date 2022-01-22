---
title: "Il Nutchip, un integrato dai mille utilizzi"
excerpt: "Il Nutchip è un importante integrato che permette il controllo di qualsiasi apparecchiatura, dalle più semplici per domotizzare la propria casa fino a creare piccoli robottini."
author: "Raffaello Bonghi"
classes: wide
header:
  overlay_color: "#000"
  overlay_filter: "0.5"
  overlay_image: /assets/images/posts/nutchip/sotto.jpg
  teaser: /assets/images/posts/nutchip/sotto.jpg
categories:
  - Recensioni
tags:
  - Nutchip
pinout:
  - image_path: /assets/images/posts/nutchip/PinoutATMEL.jpeg
  - image_path: /assets/images/posts/nutchip/pinoutNUTCHIP.gif
---

Il Nutchip è un importante integrato che permette il controllo di qualsiasi apparecchiatura, dalle più semplici per domotizzare la propria casa fino a creare piccoli robottini.

Le qualità di questo integrato sono innumerevoli, prima di tutto partendo dalla facilità di programmazione, fino alla facilità di realizzazione del circuito.

Ma andiamo ad analizzare questo integrato.

![Nutchip]({{ '/assets/images/posts/nutchip/nut_logo_main.gif' | relative_url }})

Molto spesso si sente parlare del Nutchip, un circuito integrato che come recita il sito ufficiale è adatto:

* hobby ed elettronica ricreativa
* telecomandi intelligenti
* piccoli automatismi
* didattica ed esperimenti scolatici
* home automation

Le caratteristiche dichiarate dal sito Nutchip sono molto utili per chi ha bisogno di un “cervello” capace di essere gestito con pochi comandi e risultare subito efficiente dopo la sua installazione.

Infatti questo permette attraverso il riempimento di una tabella contenuta nel programma di gestione di:

* un decodificatore di telecomandi
* una matrice digitale programmabile a 4 ingressi e 4 uscite
* un timer regolabile da 1 millesimo di secondo a mille ore
* un comparatore capace di valutare un sensore
* 3 ingressi digitali preprogrammati.

Ma per capire come questo microcontrollore riesce a decodificare e gestire tutte le porte dovremo analizzare con più attenzione il Nutchip.

# “Sotto” il Nutchip

La prima cosa che colpisce dopo aver rimosso la linguetta presente sull’integrato, è il microcontrollore utilizzato, questo infatti è il AT90S2313 prodotto dalla Atmel.

Leggendo le specifiche tecniche contenute nel datasheet possiamo scoprire da cosa sono dovute queste particolari doti.

{% include figure image_path="/assets/images/posts/nutchip/sotto.jpg" alt="Sotto l'etichetta" caption="Sotto l'etichetta" %}

Il AT90S2313 lavora tra i 4Mhz ed i 10Mhz ma quella richiesta per il funzionamento dal Firmware interno è di 4Mhz.
La memoria interna dove risiede il firmware è di 2K mentre la memoria dove andremo a caricare il programma è una EEPROM da 128Bytes, questa infatti si può riprogrammare attraverso le porte seriali del Microcontrollore.

La capacità di queste memorie è quella di resistere a più di 100.000 scritture e letture prima di diventare inutilizzabili.

Questo integrato contiene al suo interno un Comparatore analogico che permette il confronto di tensioni, al suo interno è predisposto un Watchdog Timer  ed un sistema ICP (in-circuit programming).

Le tensioni di Lavoro per la versione AT90S2313-10 è di:
– 4.0 – 6.0V (AT90S2313-10)

# Il Pinout

Confrontando il pinout presentato sul sito del Nutchip con quello esposto dalla Atmel si riesce a interpretare come è stato progettato il firmware interno ed a capire le caratteristiche del prodotto:

{% include gallery id="pinout" caption="Pinout" %}

Si può notare come l’ingresso “Remote” è in realtà gestito come interrupt, infatti ogni qual volta andremo ad inviare un comando attraverso il trasmettitore radio o il telecomando il programma si interromperà permetteno di decodificare il segnale.

Per quanto riguarda la porta **ST0** o **INT1** per quanto riguarda la classificazione ATMEL si scopre facilmente il suo funzionamento. Infatti questo come il precedente blocca il programma in esecuzione ma questa volta lo porta lo resetta a “caldo”.

Le ultime due porte dedicate: **HOLD** e **STOP**, sono delle normalissime porte che interagiscono all’interno del programma, ma non sono di Interrupt.

Infine troviamo il Comando **RESET**, questo non è gestibile a livello software e permette un RESET del Nutchip portando anche alla perdita dei dati nella memoria del microcontrollore.

Le altre porte come:
* **RX**
* **TX**

Sono state configurate come porte dedicate per la riprogrammazione o il controllo attraverso la porta seriale.

* IN1 – 4 sono delle porte I/O definite internamente dal firmware soltanto come ingresso.
* OUT1 – 4 sono delle porte I/O definite internamente dal firmware soltanto come uscita.

Adesso passiamo all’analisi del Software di controllo del Nutchip.

# NutStation

Questo programma premette attraverso una semplice tabella della verità la gestione dell’integrato permettendo così di controllare una grande varietà di componenti, dai motori alle lampade.

Non serve un linguaggio di programmazione, per questo è facile da usare. Basta riempire la tabella che compare a video, per determinare le combinazioni di ingressi e uscite da ottenere. Quindi si trasferisce la matrice al chip tramite la porta seriale del computer.

Con la tecnologia ICP (in-circuit programming) la programmazione avviene senza smontare il chip dal circuito finale.

Il programma si presenta all’avvio con questa schermata:

{% include figure image_path="/assets/images/posts/nutchip/sshot_table.gif" alt="Shot table" caption="Shot table" %}

Appare chiaro infatti il suo comportamento e la facilità di utilizzo… ma per maggiori informazioni basta leggere la guida presente sul sito del Nutchip:

http://www.nutchip.com/state_machines/tables.htm

# Dove acquistarlo

Il Nutchip è in vendita presso [**Siro Elettronica**](http://www.siroelettronica.it/) (grazie per la disponibilità per l’invio del Sample)

{% include figure image_path="/assets/images/posts/nutchip/ultima foto.jpg" alt="Rivenditore" caption="Rivenditore" %}

Il prodotto si può acquistare sia online che direttamente in negozio nella nuova sede (a partire da settembre):

**Via Renier, 67 10141 Torino Tel: 0113855103**