---
title: Wie konfiguriere ich den ESR Zahlschein ?
layout: default
tags:
  - Systemadministration
  - ESR
lang: de
---

# ESR-Aktivierung im System

## via SQL

1. [SQL Script ausführen](https://github.com/metasfresh/metasfresh-dist-orgs/blob/master/misc/sql/configuration/5475402_cli_ESR_enable.sql)
1. Anwendungsserver neustarten

## ESR-Aktivierung manuell

Alternativ zu dem oben augeführten Skript kannst Du den ESR auch manuell einrichten:

1. melde Dich mit der Rolle "System Administrator" am Mandanten "System" an
1. Systemschalter `de.metas.payment.esr.Enabled` [aktivieren](Systemschalter)

### Referenzen aktivieren

1. Öffne [Fenster "Reference Number Type"](Wie_finde_und_öffne_ich_ein_Fenster)
1. setze den Haken im Feld **aktiv** bei den Einträgen mit den Namen "ESRReferenceNumber"
1. [Speichern](Wie_lege_ich_einen_neuen_datensatz_an)
1. setzen den Haken ebenfalls im unteren Register "assigned tables"
1. [Speichern](Wie_lege_ich_einen_neuen_datensatz_an)
1. setze den Haken im Feld **aktiv** bei den Einträgen mit den Namen "InvoiceReference"
1. setzen den Haken ebenfalls im unteren Register "assigned tables"
1. [Speichern](Wie_lege_ich_einen_neuen_datensatz_an)

![img](..\images\de_reference_number_type.png)

### Server Neustart
Starte den Anwendungsserver einmal neu. Falls Du nicht weißt wie das geht, kontaktiere den Serveradmin.

# fachliche ESR-Einrichtung

Nach der Aktivierung des ESR braucht es dann noch die Fachliche Einrichtung.

## Einrichtung Organisation

Damit der ESR für eine Organisation erzeugt wird müssen die folgenden Kriterien erfüllt sein:
- Der Suchschlüssel der Organisation muss numerisch und nicht länger als 3 Zeichen lang sein, da er Teil der ESR Nummer wird. z.B. 001
- Der Geschäftspartner der Organisation muss eine Schweizer Adresse,  ein ESR Konto und die gleiche Nummer wie die Sektion haben (z.B. 001).
- Die ESR Teilnehmer Nummer darf nicht länger als 7 Stellen haben ("-" und 0 nicht mitgezählt)

## Einrichtung Bankkonto

Damit der ESR Zahlschein-String erstellt werden kann braucht es ein ESR Konto beim Geschäftspartner der Organisation:

1. Feld **ESR-Konto** aktivieren
1. Feld **ESR-Teilnehmer Nummer** füllen. z.B. 1-23456-7
1. Feld **Rendered ESR Receiver** eintragen


# Überprüfung System Konfig via SQL

```
select * from ad_sysconfig where name = 'de.metas.payment.esr.Enabled';
select name,isactive from c_referenceno_type where name in ('InvoiceReference','ESRReferenceNumber');
select * from c_referenceno_type_table where c_referenceno_type_id in (select c_referenceno_type_id from c_referenceno_type where isactive = 'Y');
```
