---
title: "RDS-X01 Un robot versatile!"
excerpt: "Ma questa settimana recensiremo un famoso robot della RoboTech Srl. Questo è una buona piattaforma per chi si avvicina per la prima volta nel mondo della robotica vuole saggiare le caratteristiche di questo mondo."
author: "Raffaello Bonghi"
classes: wide
header:
  overlay_color: "#000"
  overlay_filter: "0.5"
  overlay_image: /assets/images/posts/rds-x01/robot.jpg
  teaser: /assets/images/posts/rds-x01/robot.jpg
categories:
  - Recensioni
tags:
  - RDS-X01
ruote:
  - image_path: /assets/images/posts/rds-x01/rdp8071.jpg
  - image_path: /assets/images/posts/rds-x01/rdp806.jpg
sensori:
  - image_path: /assets/images/posts/rds-x01/RDI2012_big.jpg
  - image_path: /assets/images/posts/rds-x01/RDI202_big.jpg
programmazione:
  - image_path: /assets/images/posts/rds-x01/ticolla1.jpg
  - image_path: /assets/images/posts/rds-x01/ticolla2.jpg
---

Siamo ad agosto ed il periodo delle ferie e delle vacanze estive si fa sentire. Ma questa settimana recensiremo un famoso robot della RoboTech Srl. Questo è una buona piattaforma per chi si avvicina per la prima volta nel mondo della robotica vuole saggiare le caratteristiche di questo mondo.

La scatola inviataci da Fare Elettronica, si dimostra subito ricca di contenuti e ottima per realizzare il primo robot.

Infatti troviamo dentro:

{% include figure image_path="/assets/images/posts/rds-x01/dscn0001.jpg" alt="Scatola" caption="Scatola" %}

# Contenuto del kit RDS-X01

Scheda di controllo RDC-101

Input:
* 2 Sensori di contatto RDI-201
* 2 Sensori analogici a infrarossi RDI-202

Output:
* 2 Motori DC con meccanica di trasmissione RDO-501

Parti strutturali:
* Piastre Universali RDP-801
* 1 Piastra Universale a L RDP-802
* 5 Sostegni universali RDP-803
* 3 Cavi (3-pin) RDP-804
* 2 Cavi (3-pin) RDP-805
* 1 Perno Universale RDP-806
* 2 Ruote e pneumatici RDP-807
* 1 Cavo (6-pin) RDP-808
* 1 Alloggio per batterie RDP-809

Scheda di comunicazione:
* 1 scheda di comunicazione seriale 232C RDI-301

Programmazione:
* Software TiColla* (CD-ROM) RDP-901
* 1 cavo seriale

{% include figure image_path="/assets/images/posts/rds-x01/dscn0003.jpg" alt="Il Contenuto" caption="Il Contenuto" %}

# La meccanica

Le grandi capacità di questo robot si trovano facilmente nella parte meccanica, che ricorda il Meccano. Grazie infatti ad una struttura a “groviera” permette il montaggio di qualsiasi componente in qualsiasi posizione.
Questo permette sperimentazioni e prove del robot su qualsiasi superficie.

![Telaio]({{ '/assets/images/posts/rds-x01/rdp801.jpg' | relative_url }})

I motori sono costituiti da una particolare motoriduzione che permette una alta coppia ed una discreta velocità. Unico neo è l’eccessivo rumore prodotto dall’attrito degli ingranaggi, ma può essere facilmente ridotto aggiungendo un buon quantitativo di grasso.

![Riduttore]({{ '/assets/images/posts/rds-x01/rdo501.jpg' | relative_url }})

I punti di appoggio del robot sono principalmente 3:
I più importati sono costituite dalle ruote in ABS che permettono la locomozione del robot e dal ruotino universale costituito da una sfera di 27mm di diametro.

{% include gallery id="ruote" caption="ruote" %}

Dalle prove effettuate, RDS-X01 riesce a muoversi con facilità su superfici lisce, come ad esempio il pavimento di casa e leggermente accidentate come può essere il ciottolato di un giardino.

# Elettronica

Passando all’elettronica del robot si iniziano a scoprire piccoli difetti dovuti principalmente all’assemblaggio dei componenti elettronici sul PCB, notiamo la presenza di bolle di stagno ed anche gravi errori di saldatura sui piccoli componenti SMD, ma questo credo sia dovuto eccezionalmente.

{% include figure image_path="/assets/images/posts/rds-x01/dscn0007.jpg" alt="Particolare Elettronica" caption="Particolare Elettronica" %}

La scheda principale dove vi è il cuore del robot è la Scheda di controllo RDC-101.

Questa scheda è costituita da due parti fondamentali:
Il cervello del robot, con il microcontrollore atto ad eseguire le operazioni, la EEPROM con il programma ed una ingegnosa serie di LED che permettono di segnalare guasti o avvisi.
La seconda parte della scheda è indubbiamente la parte per il controllo motori, costituita da 2 driver per la gestione dei motori. Di particolare interesse si dimostra il connettore di alimentazione secondario che permette di divedere le alimentazioni dei motori e dell’elettronica.
Il microcontrollore JRT-101 come si può notare è costituito da 16 pin ma soltanto 6 sono porte di comunicazione I/O.
Dove 3 vengono sprecate per il controllo dei motori, rimanendone disponibili soltanto altrettante 3 per il controllo dei sensori, sufficienti a malapena per l’utilizzo dei sensori inclusi.

{% include gallery id="sensori" caption="Sensori" %}

Come anticipato prima i sensori non sono particolarmente presenti nel Kit che, come abbiamo visto comprende 2 sensori di conttatto e 2 sensori infrarossi (a seconda del montaggio permettono la rilevazione degli ostacoli a distanza o discriminare il colore del terreno utili per un robot line-follower).

La scheda di comunicazione seriale è costituita da un MAX202, un integrato che permette la comunicazione tra il PC ed il microcontrollore.
Ed è proprio con  questo che potremo inviare il nostro programma scritto con Ticolla al Robot e permettere di vedere il robot in funzione.

{% include figure image_path="/assets/images/posts/rds-x01/rdi301.jpg" alt="Adattore seriale" caption="Adattore seriale" %}

# Programmazione

![Ticolla]({{ '/assets/images/posts/rds-x01/ticollalogo.jpg' | relative_url }})

Ticolla è un software che permette di gestire il comportamento del robot utilizzando i diagrammi di flusso. Con questo è possibile selezionare i comportamenti del robot a seconda degli ostacoli che si trova di fronte.
Per chi non ha mai programmato si dimostra particolarmente efficiente e semplice, ma al contempo il programma non permette con particolare facilità la creazione di programmi complessi dove il robot possa esprimere durante il funzionamento.

{% include gallery id="programmazione" caption="Programmazione" %}

# Conclusioni

Concludendo il robot si dimostra interessante per chi si avvicina nel mondo della robotica ma estremamente limitato per chi cerca qualcosa di affidabile ed espandibile.

{% include figure image_path="/assets/images/posts/rds-x01/robot.jpg" alt="Robot Assemblato" caption="Robot Assemblato" %}

Con questo voglio ringraziare Fare Elettronica e RoboTech Srl che ci hanno inviato il materiale in modo da poter essere recensito.

![Logo Fare Elettronica]({{ '/assets/images/posts/rds-x01/logo_fe.jpg' | relative_url }})

![RTlogo]({{ '/assets/images/posts/rds-x01/RTlogo.gif' | relative_url }})