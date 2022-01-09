---
title: "Il primo programma"
excerpt: "Il primo programma per un robot da minisumo"
permalink: /tutorial/primo-programma
author: "Raffaello Bonghi"
classes: wide
header:
  overlay_color: "#000"
  overlay_filter: "0.5"
  overlay_image: /assets/images/tutorial/programmazione/MPLAB.gif
  teaser: /assets/images/tutorial/programmazione/MPLAB.gif
---

Il primo programma ci permetterà di gestire i 2 LED presenti nel robot attraverso il pulsante.

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
‘*****************************************************************
‘********************* DEFINIZIONE PORTE ************************
OUTPUT LEDV ‘LED Verde posto a Destra
OUTPUT LEDR ‘LED Rosso posto a Sinistra
INPUT PULSANTE ‘Pulsante Di controllo
‘****************************************************************
‘********************* PROGRAMMA *****************************
Loop:
IF PULSANTE  =  0 THEN
HIGH LEDV
LOW LEDR
ELSE
LOW LEDV
HIGH LEDR
ENDIF
GOTO Loop
```

**DEFINE** Come detto nel precedente articolo è una istruzione che definisce delle impostazioni presenti nell’hardware.

Queste istruzioni sono istruzioni dedicate e come è logico pensare non sono strettamente relative al programma, ma al compilatore ed all’assemblatore che prepareranno il programma nel giusto formato che richiede l’elettronica.

Nel nostro caso l’istruzione DEFINE OSC definisce il quarzo presente nel circuito e nel nostro caso è da 4 Mhz quindi scriveremo l’istruzione DEFINE OSC 4

**DEFINE** OSC 4 ‘Velocità in MHz: 3(3.58) 4 8 10 12 16 20 24 25 32 33 40

Queste sono tutte le velocità impostabili dal programmatore

La seconda istruzione che incontriamo è:

Label **VAR** Size

Questa definisce la variabile che useremo all’interno del programma o nel nostro caso le porte che utilizzeremo nel circuito.

Le variabili sono delle istruzioni che una volta definite occupano un certo spazio nella memoria.

I formati disponibili per chi usa il PicBasic Pro sono 3

* **BIT** occupa 1 Bit quindi tra valori compresti da 0 a 1
* **BYTE** occupa 8 Bit quindi valori compresi da 0 e 255
* **WORD** occupa 16 Bit quindi valori compresi da 0 a 65535

**INPUT** ed **OUTPUT** invece sono delle istruzioni che definiscono gli ingressi e le uscite del microcontrollore

Come vediamo nel programma l’istruzione
* **OUTPUT** LEDV definisce come uscita LEDV vale a dire PortA.0
* **INPUT** PULSANTE al contrario, definisce come ingresso PortB.0

Dopo le prime istruzioni abbiamo notato che finalmente siamo giunti al programma

Loop:

```basic
IF PULSANTE  =  0 THEN
HIGH LEDV
LOW LEDR
ELSE
LOW LEDV
HIGH LEDR
ENDIF
GOTO Loop
```

Questo è il vero e proprio programma che attraverso il ciclo racchiuso tra Loop…GOTO Loop

L’istruzione **GOTO** permette di saltare da una istruzione ad un’altra, ed in questo caso tornando alla Label “Loop”.

Per poter scegliere tra percorsi di azioni alternative si usano le strutture di selezione, questa struttura è il comando: **IF… THEN**

```basic
IF Comp {AND/OR Comp…} THEN
Programma
ELSE
Programma
ENDIF
```

A seconda del comando che riceve compie una azione o un’altra, nel caso del nostro programma
Se il pulsante viene premuto questo da tensione al LEDR (LED Rosso) e se questo viene rilasciato abilita il LEDV (LED Verde)

# Secondo Programma

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
Variabile VAR BYTE
i VAR BYTE

LOW LEDV
LOW LEDR
LOW RELE
Loop:
FOR i = 0 TO 50
IF PULSANTE = 0 THEN
Variabile = Variabile + 1
ENDIF
PAUSE 100
NEXT i

SELECT CASE Variabile
CASE 0
GOTO Loop
CASE 1
FOR i = 0 TO 2
HIGH LEDV
PAUSE 200
LOW LEDV
PAUSE 200
NEXT i
CASE 2
FOR i = 0 TO 2
HIGH LEDR
PAUSE 200
LOW LEDR
PAUSE 200
NEXT i
CASE IS > 3
FOR i = 0 TO 2
HIGH LEDV
HIGH LEDR
PAUSE 200
LOW LEDV
LOW LEDR
PAUSE 200
NEXT i
END SELECT
```

Come abbiamo notato il secondo programma ha delle nuove caratteristiche rispetto il precedente che abbiamo appena analizzato.

Questa volta utilizziamo una variabile per poter riconoscere la quantità di volte che premiamo il pulsante:
```
Variabile VAR BYTE
IF PULSANTE = 0 THEN
Variabile = Variabile + 1
ENDIF
```

Ogni volta che premeremo il pulsante la variabile aumenterà di uno il suo valore originale, questo permetterà alla fine del ciclo FOR…NEXT di riconoscere la quantità di Click e attraverso l’istruzione SELECT CASE compiere una istruzione o un’altra.

Come anticipato l’istruzione

|--------|-----------|
| FOR i = 0 TO 50 | FOR Variabile = Inizio TO Fine {STEP {–} Inc} | 
| ... | {Body} |
| PAUSE 100 | NEXT {Variabile} | 
| NEXT i | |

Il ciclo **FOR...NEXT** ripete un’istruzione sulla base di una variabile che parte da un valore predefinito, e si perpetua fino ad un valore maggiore, ripetendo quindi il ciclo fino al raggiungimento del valore.

L’istruzione **STEP** permette di saltare ad un passo specifico fino al raggiungimento del valore definito.

come ultima istruzione troviamo **SELECT CASE**

```
SELECT CASE var
CASE expr1 {, expr…}
statements
CASE expr2 {, expr…}
statements
{CASE ELSE statements}
END SELECT
```

che svolge una funzione molto simile alla istruzione IF…THEN infatti ad ogni condizione che avremo sulla variabile questa comporterà un risultato differente del programma.

Infatti a seconda delle volte che schiacceremo sul pulsante si accenderà un LED o l’altro o tutti e due.