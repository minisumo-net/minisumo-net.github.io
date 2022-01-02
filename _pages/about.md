---
title: "I minisumo"
excerpt: "La categoria minisumo"
permalink: /about/
classes: wide
header:
  overlay_color: "#000"
  overlay_filter: "0.5"
  overlay_image: /assets/images/intro.jpg
  teaser: /assets/images/intro.jpg
  actions:
    - label: ":sparkling_heart: Sponsor"
      url: "https://github.com/sponsors/rbonghi"
sidebar:
  - nav: "about"
---

Il minisumo, la categoria robotica più conosciuta nel mondo "sportivo", in questo articolo analizzeremo le regole fondamentali di questa categoria. Gli elementi pricipali di un robot di questo genere fino ad capire cosa può essere realmente utile a questi robot. iniziamo partendo dalla storia di questo "sport".

Il sumo robotico è una competizione organizzata dalle scuole, nella quale robot costruiti da ragazzi, professori, hobbisti che  si sfidano in un campo rotondo chiamato “Dohyo”.

Questa competizione rispecchia il regolamento tradizionale delle gare di sumo. La sfida tra i robot si svolge infatti nel Dohyo. Il Dohyo era un particolare campo dalla forma circolare costruito con paglia e sabbia; all’interno del ring c’erano scudi, armi ed oggetti preziosi degli antichi samurai. Le gare di sumo avevano infatti una grande importanza religiosa.

Le competizioni robotiche hanno abbandonato la valenza religiosa delle gare originali, in compenso hanno adottato nuove caratteristiche che rendono questo “sport” più emozionante e divertente.

I robot per poter partecipare alle gare che si tengono nelle scuole devono però essere costruiti secondo uno specifico regolamento.
Il robot deve rispettare un regolamento molto preciso, così come ben definita è anche la struttura del ring all’interno del quale dovranno scontrarsi.

I robot vengono divisi in diverse categorie in base al loro peso ed alla loro forma, secondo lo schema riportato nella tabella che segue:

| Categoria         | Lunghezza | Larghezza | Altezza                 | Peso Max | Diametro Ring |
|-------------------|-----------|-----------|-------------------------|----------|---------------|
| 3 KG (Giapponese) | 20 cm     | 20 cm     | Senza limite di altezza | 3 kg     | 154 cm        |
| Minisumo          | 10 cm     | 10 cm     | Senza limite di altezza | 500 g    | 77 cm         |
| Microsumo         | 5 cm      | 5 cm      | 5 cm                    | 100 g    | 38,5 cm       |
| Nanosumo          | 2,5 cm    | 2,5 cm    | 2,5 cm                  | N.D.     | 19,25 cm      |
| Pesi leggeri      | 20 cm     | 20 cm     | Senza limite di altezza | 1 kg     | 154 cm        |
| Pesi medi         | 20 cm     | 20 cm     | Senza limite di altezza | 1,5 kg   | 154 cm        |
| Lego              | 20 cm     | 20 cm     | Senza limite di altezza | 3 kg     | 77 cm         |

Il campo quindi che noi utilizzeremo per questa categoria è il campo da minisumo, di diametro 77 centimetri, con un bordo bianco di 1,5 centimetri. Al centro del ring vengono disegnate due linee marroni dal nome “Shikiri-Sen” (vedi figura). Le Shikiri-sen individuano le aree di posizionamento di partenza dei robot.

{% include figure image_path="/assets/images/cosa-sono/minisumo-competition.jpg" alt="Ring da minisumo" caption="Ring da minisumo" %}

Parliamo adesso di cosa deve avere il robot per rientrare nella categoria minisumo:
Leggendo il regolamento ufficiale di minisumo.net si evince che il robot deve rispettare dei rigorosi comandi come:

Non poter lanciare oggetti, dividersi, rovinare il robot avversario, il campo o peggio ancora arrecare danno al pubblico.

Ma vediamo cosa può essere realmente utile per il nostro robot, rispondendo a delle domande fondamentali:


> **Come viene riconosciuto il ring?**
> 
> In genere degli emettitori e ricevitori infrarossi. Individuando il colore nero il robot saprà di essere all’interno del ring, mentre riconoscendo il bianco capirà di trovarsi al limite del campo; potrà quindi adottare una strategia di difesa per evitare l’avversario e salvarsi.

{% include figure image_path="/assets/images/cosa-sono/infrarossi.jpg" alt="I sensori infrarossi" caption="I sensori infrarossi" %}

> Come viene riconoscono l’avversario?
> 
> Anche qui la tecnologia ad infrarossi viene utilizzata per il riconoscimento dell’avversario, rispetto ai sensori sonar, come quelli dei sommergibili, o perfino telecamere. Tutti questi dispositivi, consentono di riconoscere l’avversario e cercare di utilizzare una strategia difensiva o di attacco all’avversario.

> **Quale tecnologia adottare?**
> 
> Robot con microcontrollore
> La prima categoria utilizza un microcontrollore (PIC), il più conosciuto, capace di eseguire le istruzioni di un programma ed in grado di ricevere segnali da sensori ambientali. Un robot con microcontrollore reagisce agli ordini eseguendo le istruzione predefinite.
> Robot B.E.A.M.
> 
> Per quanto riguarda la seconda categoria, il nome B.E.A.M. è l’acronimo di:
> * **B**iology
> * **E**lectronics
> * **A**esthetics
> * **M**echanics.
> 
> che letteralmente sta per: Biologia, Elettronica, Estetica e Meccanica.

La cosa importante di questi robot, è che funzionano senza un microntrollore: sia l’elettronica che la meccanica vengono gestite non attraverso un programma, ma sfruttando un insieme di circuiti e di regole di retroazione positiva o negativa. I circuiti di un robot B.E.A.M. sono costituiti da diodi e vengono chiamati dagli appassionati “rete neurale”.

Mark Tilden è l’inventore di questa tecnica robotica che per lui è un’autentica filosofia di vita.