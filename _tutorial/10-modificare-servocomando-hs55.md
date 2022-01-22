---
title: "Modifica del servo Hitec HS-55"
excerpt: "Modifica del servo Hitec HS-55 da modellismo"
permalink: /tutorial/modificare-servocomando-hs55
author: "Roberto Vicentini"
classes: wide
header:
  overlay_color: "#000"
  overlay_filter: "0.5"
  overlay_image: /assets/images/tutorial/modifica-servo/Sviti.jpg
  teaser: /assets/images/tutorial/modifica-servo/Sviti.jpg
ingranaggio:
  - image_path: /assets/images/tutorial/servocomandoHS55/Foto04.jpg
  - image_path: /assets/images/tutorial/servocomandoHS55/Foto05.jpg
resistenze:
  - image_path: /assets/images/tutorial/servocomandoHS55/Foto09.jpg
  - image_path: /assets/images/tutorial/servocomandoHS55/Foto10.jpg
---

Tratto da [Servo Hack](http://teamur.netfirms.com/how_to/servo_hack.htm)

Questa guida l’ho ripresa da un sito in lingua inglese e la ripropongo con qualche miglioria.
Permette la modofica di un servocomando HS-55 in modo tale da permettere la rotazione continua.
Ottimo per fare piccoli robot.

Veniamo al dunque gli utensili necessari:

* Taglia balsa
* Pinza a becchi storti da modellismo
* Giravite a croce da orologiaio (x le viti del fondello del servo)
* Tronchesino
* Saldatore a stagno
* Due resistenze SMD da 3,3k (per chi non potesse reperirle metto le foto originali per l’assemblaggio di quelle da ¼ di watt)

Foto utensili:

![utensili]({{ '/assets/images/tutorial/servocomandoHS55/Foto02.jpg' | relative_url }})

Servo aperto:

![Servocomando smontato]({{ '/assets/images/tutorial/servocomandoHS55/Foto03.jpg' | relative_url }})

Cominciamo con lo smontaggio dei vari ingranaggi (ricordare la  posizione per un corretto rimontaggio)

{% include gallery id="ingranaggio" caption="Caratteristica ingranaggio" %}

Ora passiamo alle varie modifiche per rendere il nostro servo adatto all’uso come motoriduttore.

Iniziamo prendendo la parte superiore del servo, all’interno da dove esce il perno troviamo un piccolo fermo in plastica questo va rimosso per permettere il giro di 360 gradi.

![rimozione perno]({{ '/assets/images/tutorial/servocomandoHS55/Foto06.jpg' | relative_url }})

Fatto questo estraiamo il potenziometro da 5k e dissaldiamo i 3 fili che lo collegano al circuito ( in questa immagine si vede anche la saldatura delle 2 resistenze)

![Resistenze SMD]({{ '/assets/images/tutorial/servocomandoHS55/Foto07.jpg' | relative_url }})

Per chi non avesse le resistenze smd metto le foto per quelle da ¼ di watt

{% include gallery id="resistenze" caption="Montaggio resistenze" %}

Ora passiamo alla parte più delicata della modifica e cioè la lavorazione del potenziometro.
Prima di tutto eliminiamo i 3 reofori, poi, togliamo la linguetta di rame (freccia rossa) che tiene unito il perno al case del potenziometro

![Potenziometro 1]({{ '/assets/images/tutorial/servocomandoHS55/Foto08.jpg' | relative_url }})

Estraiamo il perno, all’interno ci sono due fermi li dobbiamo togliere con l’ausilio del taglierino, questo va fatto per permettere al perno la rotazione continua, le frecce rosse indicano la posizione.

![Potenziometro 2]({{ '/assets/images/tutorial/servocomandoHS55/Foto11.jpg' | relative_url }})

Le due frecce gialle indicano i pattini del potenziometro che noi andremo a togliere con il tronchesino

Ora fatto questo inseriamo il perno al suo posto, mettendo un pò di grasso da servi, fissiamo il tutto con la linguetta di rame tolta prima e inseriamo ex potenziometro nel suo alloggio fissandolo con la vitina.

Adesso è il momento di rimettere gli ingranaggi al suo posto, raccomando la precisa disposizione originaria, aggiungendo un po’grasso, non molto.

Richiudiamo il nostro servo e adesso siamo pronti per l’utilizzo nei nostri mini robot.

![Risultato finale]({{ '/assets/images/tutorial/servocomandoHS55/Foto01.jpg' | relative_url }})