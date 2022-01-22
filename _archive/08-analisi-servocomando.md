---
title: "Analisi servocomando"
excerpt: "I servocomandi che vengono usati nel campo della robotica sono gli stessi che nel campo del modellismo"
permalink: /tutorial/analisi-servocomando
author: "Raffaello Bonghi"
toc: true
toc_label: "Tavola dei contenuti"
toc_sticky: true
header:
  overlay_color: "#000"
  overlay_filter: "0.5"
  overlay_image: /assets/images/tutorial/servocomando/intro.gif
  teaser: /assets/images/tutorial/servocomando/intro.gif
servocomandi:
  - image_path: /assets/images/tutorial/servocomando/Sanyo.gif
  - image_path: /assets/images/tutorial/servocomando/futaba.gif
  - image_path: /assets/images/tutorial/servocomando/Hitec.gif
---

I servocomandi che vengono usati nel campo della robotica sono gli stessi che nel campo del modellismo, questi contengono in un unico contenitore:

* un motorino
* demoltiplica a ingranaggi
* un circuito elettronico di controllo
* un potenziometro per il controllo della posizione.

{% include figure image_path="/assets/images/tutorial/servocomando/standardbody.jpg" alt="Dimensioni standard" caption="Dimensioni standard" %}

I servocomandi rispettando le specifiche vanno spesso alimentati da i 4,8 ai 6V, ma certi possono anche arrivare a 7V.
E’ sempre importante leggere le specifiche di ogni servocomando prima di iniziarlo ad usare.
Infatti in ogni confezione è presente una etichetta dove sono contenute tutte le caratteristiche salienti del prodotto.
Sulla confezione c’è scritta la forza torcente (torque) all’alimentazione richiesta 6V (la forza si intende applicata a un centimetro di distanza dall’asse), anche la velocità angolare del servocomando.

Quindi possiamo dire che un servomotore, non è che un motore dotato di un circuito di autocontrollo.

La principale caratteristica che differenzia un motore a spazzola da un servomotore è senza dubbio il circuito che permette di controllare il movimento in velocità con una buona precisione.

I servocomandi da modellismo come abbiamo notato nei precedenti articoli hanno un meccanismo di controreazione che, in base all’impulso che riceve, consente unicamente il posizionamento desiderato entro i 180°, questo meccanismo è gestito dal potenziometro e dal dente finecorsa presente su uno degli ingranaggi.

![ingranaggio]({{ '/assets/images/tutorial/servocomando/ingranaggio.jpg' | relative_url }})

Effettuando quindi la modifica, eliminando quindi il dentino e isolando il potenziometro, il servocomando diventa un ottimo strumento di locomozione del nostro robot.

Come avremo notato i sercomandi sono dotati di un cavetto costituito al suo interno di 3 poli di cui:

* Rosso
* Nero
* Giallo o bianco

Il 3° permette attraverso l’invio di un segnale PWM, cioè una serie di impulsi che ne regolano la velocità di rotazione del servocomando.

Questo impulso non è altro che una brusca e momentanea variazione della tensione di un segnale da uno stato alto ad uno stato basso.

I parametri da cui dipende sono la durata e l’intervallo, dove si alternano picchi alti e picchi bassi di tensione in tempi brevissimi.

Questo segnale è ciclico, vale a dire si ripete alla fine di un periodo allo stesso modo.

{% include figure image_path="/assets/images/tutorial/servocomando/pwm.gif" alt="Impulsi" caption="Impulsi" %}


* **t** = Duty
* **T** = Periodo
* **U** = Tensione

Il rapporto tra il tempo di tensione alta ed il tempo di tensione bassa viene detto duty cycle ed è quasi sempre espresso in percentuale, dove al raggiungimento del valore massimo la velocità raggiunta dal motore raggiunge anche questa il massimo.

Come avremo potuto capire i parametri che ci permetto di controllare il nostro servocomando dipendono unicamente dalle specifiche del costruttore.
I maggiori costruttori di servocomandi sono:

{% include gallery id="servocomandi" caption="costruttori servocomandi" %}

Ma una cosa che contraddistingue qualsiasi modello sono la durata in microsecondi dell’impulso per il valore alto.

L’impulso in genere è compreso tra 1 e 2 microsecondi

* Dove ad 1 microsecondo il servocomando gira in senso antiorario
* Dove ad 1,5 microsecondi il servocomando resta fermo, per meglio dire in stallo
* Dove ad 2 microsecondi il servocomando gira in senso orario

Per quanto riguarda il valore basso questo di solito è compreso tra 10 e 40 millisecondi.

Ogni qual volta che andremo quindi a programmare il nostro microcontrollore per generare l’impulso adeguato per far muovere il nostro servocomando dovremo rispettare le regole appena descritte.

La generazione di un impulso da parte di un micorcontrollore è strettamente legata al clock che questo possiede.

Un microcontrollore con quarzo a **4 Mhz** dovrà generare degli impulsi di:

* **100** antiorario
* **150** stallo
* **200** orario

Con un tempo di low di 4 millisencodi

Un microcontrollore con quarzo a **8 Mhz** dovrà generare degli impulsi di:

* **200** antiorario
* **300** stallo
* **400** orario

Con un tempo di low di 8 millisencodi

Un microcontrollore con quarzo a **20 Mhz** dovrà generare degli impulsi di:

* **500** antiorario
* **750** stallo
* **1000** orario

Con un tempo di low di 20 millisencodi

# Servocomandi digitali

Di recente produzione si trovano in commercio nuovi sercomandi con caratteristiche del tutto nuove rispetto ai servocomandi analogici precedentemente descritti.

{% include figure image_path="/assets/images/tutorial/servocomando/hs5245MG.jpg" alt="HS-5245MG" caption="HS-5245MG" %}

I servocomandi Digitali offrono caratteristiche del tutto migliori, questi infatti possono essere programmati, permettendo di controllare la direzione di rotazione, il centraggio, il fine corsa, il failsafe, la velocità e la prontezza della risposta utilizzando l’unità di programmazione per quanto riguarda l’Hitec del HFP-10.

{% include figure image_path="/assets/images/tutorial/servocomando/hfp10.jpg" alt="HFP-10" caption="HFP-10" %}

La risposta  di un servocomando digitale è 5 volte superiore rispetto a quelli normali con una maggiore risoluzione ed una maggiore coppia.

Sono di recente usciti nuovi servocomandi costruiti apposta per apparecchiature robotiche come ad esempio il HSR-8498HB.

{% include figure image_path="/assets/images/tutorial/servocomando/Servorobot.jpg" alt="Servo robot" caption="Servo robot" %}

La meccanica di questi servi e’ estremamente robusta, gli ingranaggi sono realizzati in Karbonite, un materiale sviluppato dalla Hitec che offre un’altissima resistenza all’usura e dei giochi ridottissimi, anche dopo un uso intensivo del servo.

Le principali peculiarità di questi servi sono:

## L’interfaccia HMI

I servi HSR-8498HB hanno una nuova interfaccia sviluppata da Hitec appositamente per la robotica. Il protocollo HMI (HiTEC Multi-protocol Interface) consente di interrogare il servo per ottenere dati relativamente a: Tensione, Corrente e Posizione. Come gli altri servi digitali, anche questi sono programmabili dall’utente, occorre un’interfaccia disponibile in futuro.

## Il Case

Questi servocomandi hanno un versatile case che permette 3 diverse combinazioni. Grazie agli accessori forniti e’ infatti possibile modificare il case per adattarsi all’applicazione specifica. Sara’ cosi’ molto semplice realizzare robuste applicazioni per grippers, androidi da Robo One, esapodi e altri robot walkers.