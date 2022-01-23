---
title: "L’elettronica con un PIC 16F84A"
excerpt: "L’elettronica con un PIC 16F84A per un robot da minisumo"
permalink: /tutorial/elettronica-16F84A
header:
  overlay_color: "#000"
  overlay_filter: "0.5"
  overlay_image: /assets/images/tutorial/16F84A/robot.jpg
  teaser: /assets/images/tutorial/16F84A/robot.jpg
author: "Raffaello Bonghi"
classes: wide
sensori:
  - url: /assets/images/tutorial/beam/s320105.jpg
    image_path: /assets/images/tutorial/beam/s320105.jpg
    alt: "GP2D15"
    title: "GP2D15"
  - url: /assets/images/tutorial/beam/91401.jpg
    image_path: /assets/images/tutorial/beam/91401.jpg
    alt: "QRB1134"
    title: "QRB1134"
circuito-stampato:
  - url: /assets/images/tutorial/16F84A/circuito2.jpg
    image_path: /assets/images/tutorial/16F84A/circuito2.jpg
    alt: "Schema elettrico"
    title: "Schema elettrico"
  - url: /assets/images/tutorial/16F84A/stampato2.jpg
    image_path: /assets/images/tutorial/16F84A/stampato2.jpg
    alt: "Circuto stampato"
    title: "Circuto stampato"
---

Siamo arrivati finalmente a realizzare la prima scheda del nostro minisumo con una elettronica del robot gestita da un PIC 16F84A.

La prima operazione che dovremo iniziare a fare come nel precedente articolo sull’elettronica BEAM sarà reperire i componenti:

| Quantità | Componente | Riferimento |
|----------|------------|-------------|
| 5        | 0.1mF      | C3, C8, C9, C4, C5 |
| 1        | 1K Ohm     | R15 |
| 2        | 1N4148 | D1, D2 |
| 1        | 2,2K Ohm | R10 |
| 1        | 4 Mhz | Q1 |
| 6        | 10K Ohm | R4, R5, R6, R7, R13, R14 |
| 2        | 22pF | C1, C2 |
| 2        | 33mF | C6, C7 |
| 1        | 68 Ohm | R12 |
| 1        | 74HC14N | IC3 |
| 3        | 220 Ohm | R1, R2, R3 |
| 2        | 270 Ohm | R8, R9 |
| 1        | 7805T | IC2 |
| 1        | BC337 | T1 |
| 1        | RELE MONOSCAMBIO | K2 |
| 2        | LED5MM ROSSO | LED1, LED2 |
| 1        | LED5MM VERDE | LED3 |
| 1        | LED5MM GIALLO | LED4 |
| 1        | L293D | IC4 |
| 1        | PIC16F84AP | IC1 |
| 4        | Connettore 2 Poli | X1, X2, X3, X6 |
| 1        | Connettore 3 Poli | X4 |
| 3        | Connettore 2 Poli/strip | J6, J7, J8 |
| 2        | Connettore 3 Poli/strip | J1, J2 |
| 2        | Connettore 4 Poli/strip | J3, J4 |
| 1        | Connettore 5 Poli/strip | J5 |
| 1        | Interruttore | S1 |
| 1        | Pulsante | S2 |
| 1        | Dissipatore | Per 7805 |

Questa scheda rispetto alla precendete come abbiamo potuto notare utilizzerà un PIC per la gestione dei sensori, dei motori e di tutto quello che è necessario per poter far combattere il nostro minisumo.

Utilizziamo i precedenti sensori comprati per il robot vale a dire gli Shap 2 GP2D15 ed i 2 QRB1134.

{% include gallery id="sensori" caption="sensori minisumo" layout="half" %}

Fatto questo potremo finalmente iniziare a stampare la scheda del robot realizzata apposta per gli utenti di minisumo.net, qui possiamo vedere le foto.

# Il Ponte H

{% include figure image_path="/assets/images/tutorial/16F84A/ponteh3.jpg" alt="ponte H" caption="ponte H" %}

Come abbiamo notato il circuito è costituito da 2 schede, una con l’elettronica ed una con il Ponte H, costituito da 2 integrati: L’293D ed il 74HC14
Questi a differente della precedente scheda gestiscono i motori con un miglior risparmio energetico rispetto ai relè e eliminano molti disturbi provocati dai motori, rendendo la gestione del robot pulita e senza problemi.

Nella fotografia sono presenti 4 connettori ma analizziamoli partendo dall’alto a Sinistra:

* X6 Controllo dei motori, qui cambiano lo stato in ingresso del ponte H si inverte la rotazione del Motore:
  * X6-1 Blu;
  * X6-2 Bianco
* X4 Alimentazione della scheda, questa proviene dall’abilitazione del relè dell’elettronica principale:
  * X4-1 Alimentazione +5V proveniente dal relè;
  * X4-2 Alimentazione diretta dalle batterie, questa serve per alimentare i motori;
  * X4-3 GND
* J7, J8 Ingresso proveniente dai motori

# L’elettronica principale

{% include figure image_path="/assets/images/tutorial/16F84A/scheda3.jpg" alt="Scheda principale" caption="Scheda principale" %}

Come possiamo vedere il cuore pulsante del robot è costituito dal PIC della Microchip il 16F84(A) questo come è possibile leggere dalle caratteristiche tecniche:

* 18 pin di cui 13 porte per l’ I/O
* Clock: da 475Khz a 10Mhz
* 68 bytes di Data RAM
* 64 bytes di Data EEPROM

Il PIC16F84A grazie alle 13 porte disponibili per l’I/O ci permetterà di gestire tutti i sensori del robot e poter controllare il movimento del robot.

La Memoria EEPROM invece ci permetterà di riprogrammare più di una volta il microcontrollore per poter provare il robot ed imparare a programmare.

Un’altra parte fondamentale di questa scheda è costituita dal relé posto nella parte bassa della scheda affianco all’interruttore principale. Questo come detto in precedenza permette ldi abilitare la scheda del controllo motori. Sempre sulla stessa scheda come possiamo vedere nella foto sono presenti anche 5 connettori/strip e 3 connettori a 2 poli, partendo dall’alto:

* J3, J4 I connettori per i sensori di linea
* J1, J2 Connettori per gli Sharp GP2D15
* J5 ICSP
* J6 Reset
* X3 Controllo motori
* X2 Alimentazione Ponte H
* X1 Alimentazione dalle batterie

Al centro della scheda sono presenti 4 LED che ci permettono di interpretare i messaggi provenienti dal PIC e poter capire come si stia comportando il robot

Possiamo vedere Un Led Rosso collegato alla porta A.1 ed un Led Verde collegato alal porta A.0

Subito dopo sono presenti due Led di cui il primo giallo ci segnala l’attivazione del relè ed il secondo rosso, che ci fa da spia per la corretta alimentazione dei motori.

Per poter programmare il PIC montato sulla scheda. Questa contiene un particolare connettore a 5 poli che ci permette di riprogrammare il PIC senza smontarlo dal proprio zoccolo. Infatti ci basterà collegare il programmatore di PIC sulla scheda e potremo tranquillamente caricare il nuovo programma in pochissimi passi.

Le connessioni presenti in questo connettore sono costituite, partendo dall’alto verso il basso da:

* GND
* VDD
* CLOCK
* DATA
* VPP

# Il montaggio della scheda

{% include figure image_path="/assets/images/tutorial/16F84A/motaggio.jpg" alt="motaggio componenti" caption="motaggio componenti" %}

Come prima operazione dovremo rimuovere le precedenti schede montate sul robot, della versione BEAM, vale a dire la scheda relé posta sotto al robot e rimuovere la scheda a 5 neuroni BEAM posta sulla superficie del telaio.

{% include figure image_path="/assets/images/tutorial/16F84A/montata.jpg" alt="Scheda montata" caption="Scheda montata" %}

Montiamo il nostro circuito stampato partendo dai componenti più bassi per continuare con quelli più alti fino a completare le due schede.

A questo punto sostituiamo la scheda controllo motori con la nuova scheda Ponte H ricollegando i motori ed i cavi di alimentazione e di controllo dei motori, ma dovremo aggiungere rispetto alla precedente versione un cavo che nel nostro caso metteremo giallo per poterlo distinguere dagli altri che porterà alimentazione direttamente dalle batterie.

{% include figure image_path="/assets/images/tutorial/16F84A/basso.jpg" alt="Vista dal basso" caption="Vista dal basso" %}

Adesso possiamo iniziare ad avvitare anche la scheda principale collegando prima i cavetti provenienti dal Ponte H nel seguente ordine:

{% include figure image_path="/assets/images/tutorial/16F84A/cavi.jpg" alt="Cavi" caption="Cavi" %}

* Il cavetto GIALLO al connettore X1-1
* Il cavetto ROSSO al connettore X2-1
* Il cavetto NERO al connettore X2-2
* Il cavetto BIANCO al connettore X3-1
* Il cavetto BLU al connettore X3-2

{% include figure image_path="/assets/images/tutorial/16F84A/montaggio.jpg" alt="Montaggio dei cavetti" caption="Montaggio dei cavetti" %}

Dopodiché avviamo la scheda e completiamo il collegamento montando i sensori di Lina ai connettori J3 e J4; L’alimentazione proveniente dalle batterie al connettore X1 e stando attendo alla polarità del connettore Sharp GP2D15 alle porte J1 e J2

{% include figure image_path="/assets/images/tutorial/16F84A/robot.jpg" alt="Robot assemblato" caption="Robot assemblato" %}

Finalmente abbiamo montato la scheda al robot, adesso è il turno della programmazione.

# Programmazione

Prima di poter programmare il nostro robot studiamo i collegamenti di tutti i sensori presenti sulla scheda guardando questa tabella:

| Porta | Connessione |
|-------|-------------|
| PortA.0 | LED Verde |
| PortA.1 | LED Rosso |
| PortA.2 | Motore Destra |
| PortA.3 | Motore Sinistra |
| PortA.4 | / / |
| PortB.0 | Pulsante |
| PortB.1 | Sensore Linea Destra |
| PortB.2 | Sensore Linea Sinistra |
| PortB.3 | Sharp Destra |
| PortB.4 | Sharp Sinistra |
| PortB.5 | Relé |
| PortB.6 | Clock ICSP |
| PortB.7 | Data ICSP |

Questo ci sarà utile per qualsiasi programma che scriveremo in futuro, ma per questa prima prova vi lascio a disposizione il primo programma che permette al robot di fare combattimenti di minisumo.

Nelle prossime lezioni si inizierà ad imparare la programmazione in Basic ed utilizzeremo questo robot per poter iniziare a programmare.
Qui di seguito vi lascio comunque il codice e l’.HEX da caricare sul PIC

{% include download.html name="20060403PICore.zip" url="https://drive.google.com/file/d/1gtRB_SkIscBpu0QeAHX-V5waLERuWRoL/view?usp=sharing" %}