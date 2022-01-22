---
title: "Drummybot"
author: "Giovanni di Dio Bruno"
toc: true
toc_label: "Tavola dei contenuti"
toc_sticky: true
header:
  overlay_color: "#000"
  overlay_filter: "0.5"
  overlay_image: /assets/images/posts/drummybot/Drummybot.jpg
  teaser: /assets/images/posts/drummybot/Drummybot.jpg
categories:
  - Robots
tags:
  - DrummyBot
---

Abstract: drummybot was the first robot that I developed with a Microchip’s PIC and it was built on October 2009.

Its name derives from “DRUMs is MY roBOT”, in fact this robot can play the drums and read music.  Drummybot plays the drums at the same speed as you clap your hands.

Its drums consists of one bass drum, one drum and one cymbal.

Drummybot è un robot che suona la batteria e proprio da ciò deriva il suo nome (DRUMs is MY roBOT).

Il robot legge uno spartito e dopo aver rilevato due battiti di mani imposta il tempo di esecuzione del brano letto.


# La meccanica

Tutta la struttura è realizzata in poliver e alluminio e ogni parte è stata lavorata a mano.

Le bacchette sono state ricavate da un tondino di legno.

I motori usati sono dei motori DC a 5V.

{% include figure image_path="/assets/images/posts/drummybot/ModuloLett.jpg" alt="Motori" caption="Motori" %}

Le parti che richiedono maggior interesse sono i tamburi, il piatto e il lettore di schedine.

I tamburi sono stati ricavati da due barattoli di plastica trasparente che ho comprato in un comune ipermercato.  Ogni membrana è stata montata per mezzo di due anelli che permettono il serraggio.

{% include figure image_path="/assets/images/posts/drummybot/SistemaFissaggioMembrane.jpg" alt="sistema di fissaggio per le membrane" caption="sistema di fissaggio per le membrane" %}

Le membrane sono dei guanti “vileda gialli”, quelli spessi e felpati internamente, che grazie alla tensione permettono un suono apprezzabile.

{% include figure image_path="/assets/images/posts/drummybot/Tamburo.jpg" alt="Tamburo" caption="Tamburo" %}

Il piatto è tagliato da un foglio di alluminio e martellato su di un’anima in legno.  Dopo essere stato forato è stato anche rigato per essere più realistico.

{% include figure image_path="/assets/images/posts/drummybot/Piatto.jpg" alt="Piatto" caption="Piatto" %}

Il lettore di schedine è realizzato sempre in poliver e alluminio.  Per poter trascinare le schedine, è stato montato un motoriduttore dotato di ruote gommate.

{% include figure image_path="/assets/images/posts/drummybot/Motoriduttore.jpg" alt="Motoriduttore" caption="Motoriduttore" %}

{% include figure image_path="/assets/images/posts/drummybot/ModuloLett.jpg" alt="Modulo di lettura" caption="Modulo di lettura" %}

Lo spartito che deve essere letto è una schedina di carta, preferibilmente con grammatura pesante, e  le note devono essere scritte con un uniPOSCA nero.  Questo tipo di pennarello acrilico permette un colore molto matto e coprente e può essere ben distinto dal bianco con i sensori.


# Elettronica

L’elettronica del robot è molto semplice.

Tutte le operazioni vengono gestite da un PIC 16F84A.

Poi con un comune driver (L293B) vengono pilotati i motori.

In effetti ho voluto rendere un po’ più generale il pilotaggio dei motori, creando un’ulteriore scheda con dei fotoaccoppiatori (4N25) e transistor (BD441).  In questo modo ho pensato che cambiando questa scheda sia possibile cambiare anche il tipo di motori (per esempio quelli dei frullatori) e batteria (magari una per bambini).

Per poter leggere le note sono stati usati 4 CNY70 mentre per il sensore di suono è stata usata una capsula microfonica elecret.

# Programmazione

Il PIC è stato programmato in assembler.

Per poter memorizzare le note è stato usato l’indirizzamento indiretto nella memoria del PIC, rendendo possibile la memorizzazione di molte centinaia di note.  Ho preferito non usare la EEPROM data la sua lentezza di archiviazione.

{% include figure image_path="/assets/images/posts/drummybot/Codice.jpg" alt="Algoritmo" caption="Algoritmo" %}

Questo algoritmo è molto riduttivo ma può far capire qual è la logica del programma.

La prima operazione è quella dei settaggi del PIC, poi vengono fatti dei controlli tra i quali uno dei più importanti è quello della carta.
Dopo vengono memorizzate le note fino a che non finisce lo spartito.

Tramite il microfono, il PIC calcola il tempo tra i due battiti di mani e dopo viene eseguito il brano, finché non viene premuto l’interruttore di ricalcolo tempo o quello di reset.

# Video