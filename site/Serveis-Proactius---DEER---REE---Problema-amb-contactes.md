---
title: Serveis Proactius - DEER - REE - Problema amb contactes
author: Joan Sanz
creator: Àrea TIC del Departament d’Empresa i Treball
subject: Anàlisi
release: 0
keywords: [REE,DEER,Proactius]
header: ${title}  V.{$release}
footer: Generat el ${today} / Pàgina ${pageNo} de ${pageCount}
---

# Problemàtica

Els serveis proactius de la FUE ha enviat avisos a varis contactes, entre ells al titular anterior.

Això ha generat queixes quan l'anterior titular és mort, o no hi ha cap relació. Per exemple, els HUTS de Turisme. 



# Motiu

El backoffice REE emmagatzema els contactes de manera incremental. No gestiona la baixa dels anteriors contactes.

I el directori (DEER) també emmagatzema tots els contactes de manera incremental.



# Model de dades a REE

A REE hi ha 2 taules:

**DGEE_1_1.Empresa.Establiment.Contactes**

que té els contactes per a 1 titular i 1 establiment concret. té els contactes  de tots els registres, és  adir , es junten els contactes d'ascensors i de hotel del mateix edifici.

no té estat de baixa

DEER consulta aquesta  taula.

**DGEE_1_2.Registre.Contactes**

té els contactes per a 1 registre concret. té l'incremental de alta, modificacio, canvi de titular, etc.

no té estat de baixa.

dificil de saber quin és el correcte.

DEER no els consulta.



# Proposta de Solució

Quedar-se el darrer contacte, tant a REE com a DEER.

## Actualitzar les dades actuals

1a opció:

Ho fa el propi DEER -> té la data d'actualització?

2a opció:

REE proporciona les dades i DEER neteja

> [!NOTE]
>
> Concretar amb DEER

## Procés d'actualització

1r REE canvia logica a DGEE_1_2 per a que doni de baixa els anteriors contactes cada cop que es dona d'alta un nou. Aprofitar funció de baixa de la plataforma.

2n DEER canvia la logica dels contactes i consulta els contactes d'un registre, vista de DGEE_1_2. I tenin en compte les baixes, que arribarà amb data de baixa informat.

> [!WARNING]
>
> Quina és la clau primària del contacte?  El numero d'identificació és obligat? Cal crear una clau? A REE ja en té idocurrencia.

> [!NOTE]
>
> Concretar amb DEER

# Notificacions

Cal analitzar si passa el mateix amb notificacions.

I quina és la clau primària de la notificació.