---
title: "Gestiamo i sensori"
excerpt: "Gestiamo i sensori programma per un robot da minisumo"
permalink: /tutorial/gestiamo-i-sensori
author: "Raffaello Bonghi"
classes: wide
header:
  overlay_color: "#000"
  overlay_filter: "0.5"
  overlay_image: /assets/images/tutorial/rimaniamo-nel-ring/qrd1114.jpg
  teaser: /assets/images/tutorial/rimaniamo-nel-ring/qrd1114.jpg
---

Il Robot Enigma utilizza come sappiamo i sensori di Linea QRB1134 per poter riconoscere il bordo campo ed evitare di cadere.

{% include figure image_path="/assets/images/tutorial/rimaniamo-nel-ring/qrd1114.jpg" alt="QRB1134" caption="QRB1134" %}

I sensori sono controllati in modo digitale dal PIC questo per noi comporta due valori di gestione. Questi sono associati:

* **0** al riconoscimento della linea bianca
* **1** riconoscimento del campo nero

Quindi come abbiamo notato con il pulsante dell’articolo precedente avremo soltanto due stati di gestione, che facilmente potremo usare attraverso un **IF … THEN**

```basic
DEFINE OSC 4 ‘definisce la velocità dell’oscillatore
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
RELE CON 5 ‘Relè Abilitazione PonteH
‘****************************************************************
‘********************* DEFINIZIONE PORTE ************************
OUTPUT LEDV ‘LED Verde posto a Destra
OUTPUT LEDR ‘LED Rosso posto a Sinistra
OUTPUT MOTORR ‘Controllo Motore Destra
OUTPUT MOTORL ‘Controllo Motore Sinistra
INPUT Pulsante ‘Pulsante Di controllo
INPUT LINEAR ‘Sensore di Linea Infrarosso QRB1134 Destra
INPUT LINEAL ‘Sensore di Linea Infrarosso QRB1134 Sinistra
INPUT SHARPR ‘Sensore rilevamento avversario GP2D15 Destra
INPUT SHARPL ‘Sensore rilevamento avversario GP2D15 Sinistra
OUTPUT RELE ‘Relè Abilitazione PonteH
‘****************************************************************

LOW LEDV
LOW LEDR
LOW RELE

Loop:
IF LINEAL = 0 AND LINEAR = 0 THEN
HIGH LEDV
HIGH LEDR
ELSE
LOW LEDV
LOW LEDR
ENDIF

IF LINEAL = 0 THEN
HIGH LEDR
ELSE
LOW LEDR
ENDIF

IF LINEAR = 0 THEN
HIGH LEDV
ELSE
LOW LEDV
ENDIF
GOTO loop
```

Come abbiamo notato il comando in PicBasic per la gestione del sensore è il noto IF…THEN

```
IF LINEAL = 0 AND LINEAR = 0 THEN
…
ENDIF
```

Particolare questa istruzione infatti attraverso un singolo comando IF se le due variabili non assumono un determinato valore, questa non viene eseguita.

Il risultato finale che avremo sarà un accensione in contemporanea dei LED presenti sul circuito.

# Il secondo programma

Adesso passiamo al secondo programma per provare ad interfacciare i sensori per la ricerca dell’avversario.

La scheda di Enigma, L’elettronica con un PIC 16F84A, Utilizza i famosi GP2D15 che permettono nel nostro caso una gestione semplice di rilevamento, proprio come i nostri sensori di linea!

Questi sensori della SHARP hanno integrato una logica che permette l’uscita dei  valori in digitale, infatti sono utilissimi nei casi dove non è presente un convertitore A/D, come  nel caso del 16F84A.

Quindi anche in questo caso avremo una gestione analoga a quella del sensore di linea, ma questa volta cambieranno i valori di controllo:

* 1 quando effettua una rilevazione dell’avversario
* 0 quando non sono presenti avversari
  
Il secondo programma, come il precedente, permetterà quindi l’accensione dei LED presenti sulla scheda a seconda della rilevazione dei due sensori presenti sulla scheda.

```basic
DEFINE OSC 4 ‘definisce la velocità dell’oscillatore
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
RELE CON 5 ‘Relè Abilitazione PonteH
‘****************************************************************
‘********************* DEFINIZIONE PORTE ************************
OUTPUT LEDV ‘LED Verde posto a Destra
OUTPUT LEDR ‘LED Rosso posto a Sinistra
OUTPUT MOTORR ‘Controllo Motore Destra
OUTPUT MOTORL ‘Controllo Motore Sinistra
INPUT Pulsante ‘Pulsante Di controllo
INPUT LINEAR ‘Sensore di Linea Infrarosso QRB1134 Destra
INPUT LINEAL ‘Sensore di Linea Infrarosso QRB1134 Sinistra
INPUT SHARPR ‘Sensore rilevamento avversario GP2D15 Destra
INPUT SHARPL ‘Sensore rilevamento avversario GP2D15 Sinistra
OUTPUT RELE ‘Relè Abilitazione PonteH
‘****************************************************************

LOW LEDV
LOW LEDR
LOW RELE

Loop:
IF SHARPL = 1 AND SHARPR = 1 THEN
HIGH LEDV
HIGH LEDR
ELSE
LOW LEDV
LOW LEDR
ENDIF

IF SHARPL = 1 THEN
HIGH LEDR
ELSE
LOW LEDR
ENDIF

IF SHARPR = 1 THEN
HIGH LEDV
ELSE
LOW LEDV
ENDIF
GOTO loop
```