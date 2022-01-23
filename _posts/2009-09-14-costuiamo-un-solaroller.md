---
title: "Costruiamo un Solaroller"
excerpt: "Il robot sarà dotato di 2 ruote e due punti di appoggio omnidirezionali, di un microprocessore PIC 16F876"
author: "Raffaello Bonghi"
classes: wide
header:
  overlay_color: "#000"
  overlay_filter: "0.5"
  overlay_image: /assets/images/posts/solarroller-robot/solaroller-1.jpg
  teaser: /assets/images/posts/solarroller-robot/solaroller-1.jpg
categories:
  - Robots
tags:
  - Solaroller
---

Dopo la breve introduzione della settimana scorsa, questa volta andremo a realizzare un robot capace di muoversi nel campo dei solaroller.

Per poterlo realizzare avremo bisogno di pochissimi componenti:

Un pannello solare dalle dimensioni standard, come ci viene chiaramente espresso dal regolamento dalle dimensioni di: 24 x 33 cm

{% include figure image_path="/assets/images/posts/solarroller-robot/sc2433.jpg" alt="Cella solare" caption="Cella solare" %}

Dopodiché a seconda dello schema che seguiremo utilizzeremo componenti elettronici differenti.

Gli schemi più conosciuti sono di solito due, dove la differenza principale è il sensore che gestisce la carica del condensatore.

# Il primo schema

{% include figure image_path="/assets/images/posts/solarroller-robot/f08-03.jpg" alt="Schema 1" caption="Schema 1" %}

Il primo schema che andremo ad analizzare utilizza l’integrato 1381-C questo infatti controlla la tensione e cambia lo stato del pin di uscita quando viene raggiunta la soglia nominale.

La lettera indica la tensione di soglia, infatti questo integrato è disponibile in molti formati:

|    | Voltaggio |
|----|-----------|
| C | 2.0 |
| D | 2.1 |
| E | 2.2 |
| F | 2.3 |
| G | 2.4 |
| H | 2.5 |
| J | 2.6 |
| K | 2.7 |
| L | 3.0 |
| M | 3.2 |
| N | 3.4 |
| P | 3.6 |
| Q | 3.8 |
| R | 4.0 |
| S | 4.2 |
| T | 4.4 |
| U | 4.6 |

Ma quelli di cui avremo bisogno saranno i modelli C o E.

Gli altri componenti sono facilmente reperibili e sono

* Un transistor 2N3904 o un 2N2222
* Un condensatore elettrolitico da minimo 4700uF
* Un Condensatore ceramico da 0.47uF
* Un Diodo 1N914
* Un motorino elettrico, possiamo utilizzare quello presente nei lettori CD dei computer per aprire il cassetto.

A Questo punto seguendo questo schema, riusciremo facilmente a realizzare il robot.

La tecnica migliore per la saldatura è il freeforming, vale a dire saldare i componenti senza usare basette o circuiti stampati.

Il risultato che otterremo sarà questo.

Il robot realizzato è di Luciano Bernardi ed utilizza lo schema lo schema sopra citato per potersi caricare e compiere il percorso.

{% include figure image_path="/assets/images/posts/solarroller-robot/solaroller-1.jpg" alt="Solaroller 1" caption="Solaroller 1" %}

# Secondo Schema

Il secondo schema che utilizzeremo utilizzerà due transistor molto conosciuti i:

* 2N3904
* 2N3906
* Avremo sempre bisogno di un condensatore da 4700uF,
* FLED ( un LED lampeggiante)
* una resistenza da 2.2Kohm

{% include figure image_path="/assets/images/posts/solarroller-robot/Schema2.jpg" alt="Schema 2" caption="Schema 2" %}

Il robot anche qui risulterà molto semplice e pronto dal primo istante, basterà metterlo in pista per poter saggiare già le prime vittorie.

La parte fondamentale di questo robot è sicuramente la realizzazione del telaio per poter compiere il percorso.

{% include figure image_path="/assets/images/posts/solarroller-robot/Solaroller2.jpg" alt="Solaroller" caption="Solaroller" %}