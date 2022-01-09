---
title: "Partiamo dal telaio"
excerpt: "Partiamo dal telaio per costruire un robot da minisumo"
permalink: /tutorial/partiamo-dal-telaio
author: "Raffaello Bonghi"
header:
  overlay_color: "#000"
  overlay_filter: "0.5"
  overlay_image: /assets/images/tutorial/telaio/telaioComp.jpg
  teaser: /assets/images/tutorial/telaio/telaioComp.jpg
toc: true
toc_label: "Tavola dei contenuti"
toc_sticky: true
telaio:
  - url: /assets/images/tutorial/telaio/telaio1.jpg
    image_path: /assets/images/tutorial/telaio/telaio1.jpg
    alt: "Telaio Parte 1"
    title: "Telaio Parte 1"
  - url: /assets/images/tutorial/telaio/telaio2.jpg
    image_path: /assets/images/tutorial/telaio/telaio2.jpg
    alt: "Telaio Parte 2"
    title: "Telaio Parte 2"
box:
  - url: /assets/images/tutorial/telaio/box.jpg
    image_path: /assets/images/tutorial/telaio/box.jpg
    alt: "Box"
    title: "Box"
  - url: /assets/images/tutorial/telaio/boxA.jpg
    image_path: /assets/images/tutorial/telaio/boxA.jpg
    alt: "Box ripiegato"
    title: "Box ripiegato"
  - url: /assets/images/tutorial/telaio/parti.jpg
    image_path: /assets/images/tutorial/telaio/parti.jpg
    alt: "Parti"
    title: "Parti"
box-motori:
  - url: /assets/images/tutorial/telaio/BoxMotori.jpg
    image_path: /assets/images/tutorial/telaio/BoxMotori.jpg
    alt: "Box motori"
    title: "Box motori"
  - url: /assets/images/tutorial/telaio/BoxMotori2.jpg
    image_path: /assets/images/tutorial/telaio/BoxMotori2.jpg
    alt: "Box motori"
    title: "Box motori"
---

Finalmente è il turno di costruire il nostro minisumo. Oggi inizieremo dal Telaio, cercheremo di capire cosa serve realmente e quali sono le caratteristiche principali per poterlo far funzionare all’interno del campo e poter iniziare a vincere le prime gare.

Prima di iniziare a costruire il nostro minisumo dovremo iniziare a reperire tutti i componenti che possono essere utili alla realizzazione, iniziamo ad elencare gli elementi più importanti:

* Motori
* Ruote
* Gomme
* Assi di metallo, o legno o altro
* Viti e bulloni
* Questo possiamo dire che è la parte che più ci servono per poter iniziare a realizzare il nostro robot da mini sumo.

# Componenti

Entriamo nel dettaglio, vediamo cosa ci serve di preciso:

## Motore

Motoriduttore DC con rapporto di riduzione 224:1. Potenza comparabile ad un Servo R/C.

{% include figure image_path="/assets/images/tutorial/telaio/1Motore.jpg" alt="motore minisumo" caption="motore minisumo" %}

## Ruote

Si adatta perfettamente all’asse dei motoriduttori SBGM2 e 3, e’ inclusa una banda in gomma per migliorare l’aderenza al suolo. E’ il sistema piu’ pratico per realizzare un robot potente ed economico.

{% include figure image_path="/assets/images/tutorial/telaio/2Ruote.jpg" alt="ruote minisumo" caption="ruote minisumo" %}

## Gomme

Vanno bene degli elastici, ma le gomme che hanno più aderenza senza dubbio sono “Finalmente disponibili, queste Gomme sono il massimo in fatto di trazione per i Robot da MiniSumo che usano le ruote in ABS da 63mm.”

{% include figure image_path="/assets/images/tutorial/telaio/2Ruote.jpg" alt="ruote minisumo" caption="ruote minisumo" %}

## Asse di Alluminio

lamiera a foro quadrato,foro da 3mm 300x150x0,5mm 803041 OPITEC

{% include figure image_path="/assets/images/tutorial/telaio/4Lamiera.jpg" alt="Asse di Alluminio" caption="Asse di Alluminio" %}

## Viti

Un set di viti da 3mm con bulloni

Adesso possiamo dire che possiamo iniziare a progettare il telaio del nostro minisumo.

# Il Progetto


Il robot nel progetto che adesso vi illustrerò si basa su un progetto pubblicato su Fare Elettronica del Settembre 2003 di Luigi Carnevale, per il 90% modificato, ma per dovere di cronaca era giusto citare il progetto originario.
Il robot che staremo per iniziare a costruire è un robot con una tipica struttura aggressiva ed ottimo quando lo scontro è frontale, la forza del robot è convogliata principalmente per gli attacchi frontali. Quindi dovremo tenere in mente, per poter avere un robot al massimo delle proprie facoltà, di sfruttare al massimo le possibilità che il robot si trovi con l’avversario di fronte.
Dopo aver capito questa importante questione potremo finalmente iniziare a lavorare sul progetto del telaio.

{% include gallery id="telaio" caption="telaio minisumo" layout="half" %}

Guardando le foto si può vedere chiaramente come poter iniziare a lavorare, nelle foto sono presenti tutte le misure per poter riportare le dimensioni corrette nella lamiera di metallo:
Le linee Rosse significano che dovremo tagliare, mentre le linee verdi serviranno ad avere le misure precise per poter piegare la lamiera al fine di avere una scatola capace di contenere i motori e la futura elettronica.
Quindi prendiamo il telaio ed iniziamo a riportare le misure

{% include figure image_path="/assets/images/tutorial/telaio/lamiera.jpg" alt="lamiera di Alluminio" caption="lamiera di Alluminio" %}

E adesso possiamo iniziare a tagliare la lamiera in modo tale da avere i pezzi da poter piegare ed assemblare.

{% include gallery id="box" caption="lamiera tagliata minisumo" %}

Adesso è il turno di montare le staffe agli estremi del Box ed allargare i buchi in modo tale da poter fa passare l’asse del motore dall’altra parte del telaio e poter infine montare le ruote.

{% include figure image_path="/assets/images/tutorial/telaio/staffe.jpg" alt="Montaggio Staffette" caption="Montaggio Staffette" %}


Dopo aver fatto questa importante parte del robot, iniziamo a preparare i motori per essere incassati all’interno del telaio.

Recuperiamo del cavo elettrico, possibilmente uno rosso ed uno nero, 2 condensatori ceramici da 0.1mF, per motore, ed iniziamo a montarli.I condensatori servono per evitare possibili disturbi generati dalle testine del motore. Queste vanno montate con un capo sull’uscita del motore e l’altro sulla cassa del motore.
Dopo aver montato il tutto dovremo avere questo risultato:

{% include figure image_path="/assets/images/tutorial/telaio/motori.jpg" alt="Motori Assemblati" caption="Motori Assemblati" %}


Adesso Possiamo incassarli all’interno del Box e possibilmente bloccandoli con delle strip e montando le vite nei punti richiesti.

{% include gallery id="box-motori" caption="box motori" layout="half" %}

Dopo aver fatto, il telaio è giunto al 70% della costruzione, manca poco e già potremo iniziare a vedere la forma del nostro minisumo.

Adesso è il turno dell’asse da 10×5,5cm da montare, in modo tale da dare maggiore solidità alla struttura e permettere anche un futuro montaggio di componenti sulla struttura.

{% include figure image_path="/assets/images/tutorial/telaio/AsseSupM.jpg" alt="Asse Superiore Montato" caption="Asse Superiore Montato" %}

E possiamo concludere montando la benna del robo sulla parte frontale del robot

{% include figure image_path="/assets/images/tutorial/telaio/telaioComp.jpg" alt="Telaio Completato" caption="Telaio Completato" %}

Da qui possiamo dire che il telaio è completato. Nel prossimo articolo costruiremo l’elettronica, che per la prima versione, sarà BEAM, dopodiché sarà con un PIC.