---
title: "Rimaniamo nel Ring"
excerpt: "Rimaniamo nel Ring per un robot da minisumo"
permalink: /tutorial/rimaniamo-nel-ring
header:
  overlay_color: "#000"
  overlay_filter: "0.5"
  overlay_image: /assets/images/tutorial/rimaniamo-nel-ring/riflessione.jpg
  teaser: /assets/images/tutorial/rimaniamo-nel-ring/riflessione.jpg
author: "Antonio Rutigliano"
classes: wide
circuito-stampato-uno:
  - url: /assets/images/tutorial/rimaniamo-nel-ring/sir1.jpg
    image_path: /assets/images/tutorial/rimaniamo-nel-ring/sir1.jpg
    alt: "Schema elettrico"
    title: "Schema elettrico"
  - url: /assets/images/tutorial/rimaniamo-nel-ring/sir2.jpg
    image_path: /assets/images/tutorial/rimaniamo-nel-ring/sir2.jpg
    alt: "Circuto stampato"
    title: "Circuto stampato"
circuito-stampato-due:
  - url: /assets/images/tutorial/rimaniamo-nel-ring/sir3.jpg
    image_path: /assets/images/tutorial/rimaniamo-nel-ring/sir3.jpg
    alt: "Schema elettrico"
    title: "Schema elettrico"
  - url: /assets/images/tutorial/rimaniamo-nel-ring/sir4.jpg
    image_path: /assets/images/tutorial/rimaniamo-nel-ring/sir4.jpg
    alt: "Circuto stampato"
    title: "Circuto stampato"
---

Secondo il regolamento ufficiale delle gare di minisumo, presente nella sezione download, per non regalare degli YUKO (punti effettivi) al nostro avversario, dobbiamo rimanere nel RING senza uscirne di nostra spontanea volontà.

**Come evitare questo?**

Possiamo partire da ciò che ha detto Raffaello nell’articolo “[Il Minisumo, dalle regole al robot](/regolamento)”:

> **Come viene riconosciuto il ring?**
> 
> In genere degli emettitori e ricevitori infrarossi. Individuando il colore nero il robot saprà di essere all’interno del ring, mentre riconoscendo il bianco capirà di trovarsi al limite del campo; potrà quindi adottare una strategia di difesa per evitare l’avversario e salvarsi.

Come sappiamo il RING è un piano rotondo nero con una fascia bianca sul bordo, per rimanerci bisogna non oltrepassare la linea bianca, quindi abbiamo bisogno di equipaggiare il nostro minisumo con un sensore in grado di rilevare questa linea. Il bianco riflette la luce a differenza del nero che l’assorbe, quindi possiamo sfruttare proprio la luce. Quindi oltre all’uso dell’infrarosso si possono usare qualunque tipo di emissione luminosa, infatti, l’infrarosso è una luce.

Potremmo tranquillamente realizzare il circuito banalissimo che effettua il rilevamento della linea bianca, ma per comprendere bene il suo funzionamento e utilizzarlo in modo ottimale dovremmo capire il principio su cui si basa

# La Riflessione

Definizione: se un’onda (nel nostro caso la luce) giunge su di una superficie, con angolo di incidenza x, viene o assorbita o “rispedita” in un’altra direzione con misura dell’angolo pari a 180°-x, questo fenomeno di “rispedimento” viene detto riflessione.

{% include figure image_path="/assets/images/tutorial/rimaniamo-nel-ring/riflessione.jpg" alt="Riflessione" caption="Riflessione" %}

Il nostro sensore deve essere perciò composto da due componenti, la sorgente e da un trasduttore apposito in base al tipo di sorgente utilizzato. 

Il nostro emettitore deve generare una luce, solitamente è usata l’infrarosso invisibile all’occhio umano, che colpisca la superficie del nostro RING. Se il punto e nella zona nera il raggio viene in maggior parte assorbito ed un debole segnale viene riflesso (una superficie per riflettere deve essere un piano non scabro, cioè perfettamente liscio), naturalmente nel modo in cui gestiremo il sensore questo debolissimo segnale non vera preso in considerazione. 

Analogamente se il punto di incidenza e bianco, la luce verrà del tutto o in maggioranza riflessa, quindi il nostro trasduttore capterà un forte segnale. 

Le sorgenti che si posso utilizzare sono varie, una piccola lampadina, un normale led di qualunque colore, ovviamente noi useremo un emettitore di luce infrarossa che è sempre un led; di conseguenza abbiamo bisogno di un trasduttore che rilevi la luce generata dalla nostra sorgente, si possono usare delle comuni foto-resistenze o per l’infrarosso dei foto-diodo o foto-trasistor.

*Perché l’infrarosso è il più usato?*

La risposta e semplice: se si utilizza la classica luce si possono avere molte interferenze causate dalla luce ambientale che possono far impazzire il minisumo, ovvio che con dei piccoli accorgimenti si può evitare questo problema, ma con gli infrarossi il rischio e molto basso.

# Vi propongo due circuiti

Il primo fa uso di un foto-diodo trasmittente ed un ricevente di facile reperibilità.
Il secondo invece usa un piccolo “blocchetto” composto da un foto-diodo trasmittente ed un foto-transitor come ricevitore.

## Primo circuito

{% include gallery id="circuito-stampato-uno" caption="Primo circuito" layout="half" %}

Elenco componenti

* LED1= Foto diodo Trasmittente
* LED2= BPW41N (Foto diodo ricevente, va bene anche il pd410pi acquistabile dall’rs-componets)
* R1= 4,7Kohm
* R2= trimmer 10Kohm
* Q1= BC547
* 
Come vedete il circuito e semplicissimo.

L’alimentazione viene fornita sui pin 1 e 3 di JP1, rispettivamente il positivo ed il negativo, sulla piastra il positivo e il pin vicino al trimmer, l’uscita si preleva sul pin 2 e si ha la tensione di alimentazione se c troviamo sul bianco, mentre 0 se c troviamo sul nero.

Il LED1 va montato a 90° verso il basso, come da foto

{% include figure image_path="/assets/images/tutorial/rimaniamo-nel-ring/sir.jpg" alt="Rilevatore 1" caption="Rilevatore 1" %}

Questa foto e riferita ad una 1° versione del PCB

Questo circuito va tarato per funzionare egregiamente eseguendo questi passi:

Posizionate il sensore su di una superficie scura, se avete a disposizione un ring per minisumo e l’ideale, collegate sul pin d’uscita del sensore un led, collegato a massa, in serie ad una resistenza (da 1kohm e sufficiente), ruotate il trimmer a metà corso, date alimentazione, se il led e spento, provate a passare dalla zona nera alla bianca del ring (o superficie chiara), se il led si accende non ci sono grossi problemi, se il led è acceso sulla superficie nera, regolate il trimmer in modo che sia spento, procedete come prima per vedere se passando dalla superficie scura a chiara si accende il led, altrimenti regolare il trimmer in modo d’avere l’accensione del led in corrispondenza della superficie chiara, e spento sulla scura.

**ATTENZIONE… QUANDO SI’ TARA IL TRIMMER NON FARLO ARRIVARE MAI NELLA POSIZIONE DI CORTO CIRCUITO, RISCHIATE DI BRUCIARE IL FOTO-DIODO.**

## Secondo circuito

{% include gallery id="circuito-stampato-due" caption="Secondo circuito" layout="half" %}

Elenco componenti

* R1= 10Kohm
* R2=220ohm
* C1=0.01uf
* JP1=QRD1114

Ancora più semplice del circuito precedente

Il QRD1114 (in foto) e un piccolo “blocchetto” contenente al suo interno un foto diodo ir (quello chiaro) ed un foto-transistor ricevente (quello scuro). Con i valori dati nello schema sul pin dell’uscita, il pin 1 di JP2, e presente un valore simile a quella del precedente circuito. Se è poco sensibile potete cambiare la resistenza R2 con una di valore inferiore, o se volete potete metterci un trimmer e tararlo come il circuito precedente per la piedinatura del QRD basta controllarla sul datasheets.

{% include figure image_path="/assets/images/tutorial/rimaniamo-nel-ring/qrd1114.jpg" alt="QRD1114" caption="QRD1114" %}

Questi sensori si possono usare per altri scopi come ad esempio in un circuito line-follower o per contare i giri di un motore (montando sull’asse del motore un disco con strisce bianche e nere) ecc.

Nella sezione download potete scaricare gli zip con i file per EAGLE dei circuiti proposti.

L’uso dei sensori su un minisumo lo vedrete nei prossimi articoli.