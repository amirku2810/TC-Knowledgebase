# TradeControl -- Technische Komponentenbeschreibung

> **Herkunft:** Umgebaute interne Organisationsbeschreibung (org.docx) von TradeControl.
> **Stack:** PowerBuilder 12.6, Framework "PfuFun", SQL-Server.
> **Zweck:** Referenzdokumentation der einzelnen technischen Komponenten (Fenster, Module, Programme, Batch-Abläufe) von TradeControl -- für Ablage im Git-Repository und als Kontextquelle in Claude-Projekten.

## Inhaltsverzeichnis

- [Notationshinweise](#notationshinweise)
- [Allgemeines](#allgemeines)
  - [Kreditlimitprüfung](#kreditlimitprüfung)
  - [Freie Kennzeichen](#freie-kennzeichen)
  - [Freie Gruppen](#freie-gruppen)
  - [Rechenformel durchschnittlicher Einstandspreis](#rechenformel-durchschnittlicher-einstandspreis)
  - [Anlage Fibukonto](#anlage-fibukonto)
  - [Online UID-Prüfung](#online-uid-prüfung)
  - [Abfrageregister "BelegKette"](#abfrageregister-belegkette)
  - [WebDokFunktionalität](#webdokfunktionalität)
- [Stammdaten](#stammdaten)
  - [Diverse Stammdaten](#diverse-stammdaten)
  - [Adressen](#adressen)
  - [Personen](#personen)
  - [Kreditor](#kreditor)
  - [Lieferanten](#lieferanten)
  - [Kunden](#kunden)
  - [Debitor](#debitor)
  - [Artikel](#artikel)
  - [ArtikelIdentifikationen](#artikelidentifikationen)
  - [ArtikelEinkauf](#artikeleinkauf)
  - [ArtikelLager](#artikellager)
  - [Geräte](#geräte)
  - [VerkaufsKonditionen](#verkaufskonditionen)
  - [Wartungsverträge](#wartungsverträge)
  - [Wartungsvertragspositionen](#wartungsvertragspositionen)
  - [Massenwartung Artikel](#massenwartung-artikel)
  - [DDS-Referenznummer - EUDR](#dds-referenznummer---eudr)
- [Verkauf](#verkauf)
  - [Auftrag](#auftrag)
  - [Auftragsposition](#auftragsposition)
  - [Lieferschein](#lieferschein)
  - [Lieferscheinposition](#lieferscheinposition)
  - [Verkaufsposition](#verkaufsposition)
  - [Rechnung](#rechnung)
  - [OP-Abfrage](#op-abfrage)
  - [Auftragsbestätigung, Offert, Proforma](#auftragsbestätigung-offert-proforma)
  - [Kostenvoranschlag, Auftragsbestätigung Reparatur](#kostenvoranschlag-auftragsbestätigung-reparatur)
  - [Kommissionsscheindruck](#kommissionsscheindruck)
  - [Lieferscheinaufbau/Druck](#lieferscheinaufbaudruck)
  - [Rechnungsaufbau/Druck](#rechnungsaufbaudruck)
  - [Auftragsbestandsliste nach Kunden](#auftragsbestandsliste-nach-kunden)
  - [Auftragsbestandsliste nach Artikel](#auftragsbestandsliste-nach-artikel)
  - [Liste offene Lieferscheine Verkauf](#liste-offene-lieferscheine-verkauf)
  - [Kundenumsatz](#kundenumsatz)
  - [Artikelumsatz](#artikelumsatz)
  - [Kunden/Artikelumsatz](#kundenartikelumsatz)
  - [Umsatzabfrage Kunde](#umsatzabfrage-kunde)
  - [Umsatzabfrage Artikel](#umsatzabfrage-artikel)
  - [Kassenbon](#kassenbon)
  - [Kassenbonposition](#kassenbonposition)
  - [Ausgabe elektronische Rechnungslegung an den Bund (ebInterface 4.1) / BBG (ebInterface 4.0)](#ausgabe-elektronische-rechnungslegung-an-den-bund-ebinterface-41-bbg-ebinterface-40)
  - [Aufbau Stornorechnung](#aufbau-stornorechnung)
- [Einkauf](#einkauf)
  - [Bestellung](#bestellung)
  - [Bestellposition](#bestellposition)
  - [Bestellvorschlag Aufbau](#bestellvorschlag-aufbau)
  - [Bestellvorschlag Löschen](#bestellvorschlag-löschen)
  - [Bestellung generieren](#bestellung-generieren)
  - [Berechnung Mindestbestand](#berechnung-mindestbestand)
  - [Bestelldruck, Anfragedruck](#bestelldruck-anfragedruck)
  - [Bestellmahnung Aufbau](#bestellmahnung-aufbau)
  - [Bestellmahnung Druck](#bestellmahnung-druck)
  - [Eingangslieferschein](#eingangslieferschein)
  - [Eingangslieferscheinposition](#eingangslieferscheinposition)
  - [Warenretourschein Druck](#warenretourschein-druck)
  - [Eingangsrechnung](#eingangsrechnung)
  - [Import Eingangsrechnungen](#import-eingangsrechnungen)
  - [Import - Eingangsrechnungen Bearbeitungsprogramm](#import---eingangsrechnungen-bearbeitungsprogramm)
  - [Belastungsnote Druck](#belastungsnote-druck)
  - [Liste der offenen Bestellungen](#liste-der-offenen-bestellungen)
  - [Liste offene Lieferscheine Einkauf](#liste-offene-lieferscheine-einkauf)
  - [Verbrauchsabfrage Artikel](#verbrauchsabfrage-artikel)
  - [Umsatzabfrage Lieferant](#umsatzabfrage-lieferant)
- [Inventur](#inventur)
  - [Inventurabgrenzung](#inventurabgrenzung)
  - [Inventurzählliste Druck](#inventurzählliste-druck)
  - [Inventurbereich](#inventurbereich)
  - [Inventurzeile (Inventurerfassung)](#inventurzeile-inventurerfassung)
  - [MDE-Inventur (TC-Next)](#mde-inventur-tc-next)
  - [MDE Inventur Verbuchen](#mde-inventur-verbuchen)
  - [MDE Inventur Abfrage](#mde-inventur-abfrage)
  - [Inventurabschluß](#inventurabschluß)
  - [Inventurstorno](#inventurstorno)
  - [Aufbau Stichtagstabellen](#aufbau-stichtagstabellen)
  - [Korrektur Abgrenzung](#korrektur-abgrenzung)
- [Lager](#lager)
  - [Diverse Lagerbuchungen](#diverse-lagerbuchungen)
  - [Abfrage Lagerbewegungen](#abfrage-lagerbewegungen)
  - [Abfrage DUEST-Entwicklung](#abfrage-duest-entwicklung)
  - [**MDE-Artikelinfo**](#mde-artikelinfo)
  - [MDE-Umlagerung (TC.next)](#mde-umlagerung-tcnext)
  - [MDE Umlagerung Verbuchen](#mde-umlagerung-verbuchen)
  - [MDE (TC.Next) Warenzugang](#mde-tcnext-warenzugang)
  - [MDE Warenzugang Verbuchen](#mde-warenzugang-verbuchen)
  - [MDE Kommissionierung](#mde-kommissionierung)
- [Kassa](#kassa)
  - [Kassenstamm](#kassenstamm)
  - [Kassen Ein- und Ausgang](#kassen-ein--und-ausgang)
  - [Münzliste](#münzliste)
  - [Druck Münzliste](#druck-münzliste)
  - [Druck Tagesabschluss](#druck-tagesabschluss)
  - [Druck Abschöpfungssummenblatt](#druck-abschöpfungssummenblatt)
  - [Zahlungsbuchung -- cst_ka_zahlung](#zahlungsbuchung----cstkazahlung)
  - [KassenLadenöffnungen](#kassenladenöffnungen)
  - [Export Datenerfassungsprotokoll Version Kassenrichtlinien 2012](#export-datenerfassungsprotokoll-version-kassenrichtlinien-2012)
  - [SQL-Kommando](#sql-kommando)
  - [Auswahlgruppe](#auswahlgruppe)
  - [RKSV Signaturerstellungseinheit](#rksv-signaturerstellungseinheit)
  - [Export RKSV-Datenerfassungsprotokoll](#export-rksv-datenerfassungsprotokoll)
  - [Reorg ka_op](#reorg-kaop)
  - [Archivlauf Kassenbelege](#archivlauf-kassenbelege)
  - [Abfrage archivierte Kassenbelege](#abfrage-archivierte-kassenbelege)
  - [Abfrage archivierte Kassen Ein/Ausgänge](#abfrage-archivierte-kassen-einausgänge)
- [Auswertungen](#auswertungen)
  - [ARA](#ara)
- [CAS/CRM](#cascrm)
  - [Stammdaten](#stammdaten-1)
  - [{#section-1 .unnumbered}](#section-1-unnumbered)
  - [KundeMitbewerb](#kundemitbewerb)
  - [Aktionen](#aktionen)
  - [Kontakte aus Aktionen erzeugen](#kontakte-aus-aktionen-erzeugen)
  - [Tagesdaten Besuchsbericht/Reisekosten](#tagesdaten-besuchsberichtreisekosten)
  - [Kontakte / Besuchsberichte](#kontakte-besuchsberichte)
  - [Fahrtenbuch](#fahrtenbuch)
  - [Reisekosten](#reisekosten)
  - [Reisekosten Aufbau](#reisekosten-aufbau)
  - [Druck Fahrtenbuch](#druck-fahrtenbuch)
  - [Druck Reisekostenabrechnung](#druck-reisekostenabrechnung)
  - [Druck Besuchsbericht](#druck-besuchsbericht)
  - [Reorganisation](#reorganisation)
  - [Reorganisation Kontakte](#reorganisation-kontakte)
  - [Datenaustausch](#datenaustausch)
  - [Apollo Auftragsimport](#apollo-auftragsimport)
  - [TC. WebView](#tc-webview)
- [Versand](#versand)
  - [Versandauftrag](#versandauftrag)
  - [Speditionsetikett](#speditionsetikett)
  - [Speditionsliste](#speditionsliste)
- [TradeControl Scan](#tradecontrol-scan)
  - [Allgemein](#allgemein)
  - [Erfassung Tradecontrol Scan](#erfassung-tradecontrol-scan)
  - [Schreiben der Tabelle tcscan](#schreiben-der-tabelle-tcscan)
  - [Import der gescannten Dokumente](#import-der-gescannten-dokumente)
- [Sonstige](#sonstige)
  - [Währungsumstellung Lieferant](#währungsumstellung-lieferant)
  - [Währungsumstellung Debitor](#währungsumstellung-debitor)
  - [Auftragsrückstandsauflösung](#auftragsrückstandsauflösung)
  - [Preisreorganisation](#preisreorganisation)
  - [UID-Prüfung Batchlauf](#uid-prüfung-batchlauf)
  - [Löschen Bewegungsdaten](#löschen-bewegungsdaten)
  - [Löschen Statistikdaten](#löschen-statistikdaten)
  - [Löschen CRM-Daten](#löschen-crm-daten)
  - [Infoblatt DSGVO](#infoblatt-dsgvo)
  - [Löschen Offerte](#löschen-offerte)
  - [Archivetikettendruck Zweckform](#archivetikettendruck-zweckform)
  - [UID-Prüflog Abfrage](#uid-prüflog-abfrage)
  - [Zusammenführen Artikeldaten](#zusammenführen-artikeldaten)
- [Schnittstellen](#schnittstellen)
  - [Stammdaten Importe](#stammdaten-importe)
  - [Integration BMD-FIBU](#integration-bmd-fibu)
  - [Integration EuroFib](#integration-eurofib)
  - [Datanormschnittstelle Aufbau Tabellen](#datanormschnittstelle-aufbau-tabellen)
  - [Intrastatschnittstelle](#intrastatschnittstelle)
  - [WebShop (Magento)](#webshop-magento)
  - [Versand](#versand-1)
  - [Auftragsimport](#auftragsimport)

---

#  Allgemeines

## Notationshinweise

**Notationen bei der Beschreibung von Verwaltungswindows:**

**Auswahldialog**

Fenster, in dem Auswahlkriterien für die zu suchenden Datensätze
definiert werden können. In der Folge sind in der Beschreibung die
Standardfelder für die Suche angeführt.

**Register**

Das Verwaltungswindow wird durch Registerblätter in Bereiche geteilt. In
der Folge sind in der Beschreibung die Datenfelder des "Registers"
angeführt.

**Teilbereich**

Sind in einem Register mehrere Bearbeitungsbereiche vorhanden, so werden
diese in der Beschreibung durch die Anführung von "Teilbereichen"
getrennt

**Liste**

Wird in einem Register bzw. in einem Teilbereich von "Liste" bzw.
"Bearbeitungsliste" gesprochen, so ist darunter eine tabellarische
Anzeige/Bearbeitung von **allen** Datensätzen des Objektes zu
verstehen. (z.B.: alle Textzeilen eines Artikels)

Notationen bei den Datenfeldbeschreibungen:

Steht in der Programmbeschreibung hinter der Datenfeldbezeichnung eines
der in Spalte 1 der nachfolgenden Tabelle angeführten Kürzel, so hat
dies die in Spalte 2 beschriebene Konsequenz:

  ------- ------------------------------------------------------------------
  (f)   für das entsprechende Feld steht die "Fernglas"- Funktion zur
          Verfügung

  (d)   für das entsprechende Feld gibt es eine Dropdown- Auswahlliste

  (fd)    für das entsprechende Feld stehen beide obige Funktionen zur
          Verfügung

  (a)   Feld ist ein reines Anzeigefeld

  (c)   Feld ist durch eine Checkbox dargestellt

  (w)   Anzeige des Wertevorrats bei einem Auswahldialog

  (p)   Eingabe im Auswahldialog ist ein Parameter (= genau ein bestimmter
          Wert)
  ------- ------------------------------------------------------------------

Verwendete Aufzählungssymbole:

-   Objekt bzw. Gruppe von Objekten  
    Beispiel: Aufzählung der Datenfelder in einem
    Artikelverwaltungswindow:

-   Artikelcode

-   Artikelbezeichnung

-   Aufzählung von alternativen Fakten/Werten (eines trifft zu)  
    Beispiel: Mögliche Werte für ein Belegkennzeichen:

-   "AR" = Ausgangsrechnung

-   "ER" = Eingangsrechnung

-   Aufzählung von zwingenden Fakten/Werten (alle treffen zu)  
    Beispiel: notwendige Fakten:

-   Kunde muss Rückstandsevidenz haben

-   Artikel muss Lagerführung haben

Mathematische Formeln:

eine Variable in einer Formel ist in einfache Anführungszeichen gesetzt:
z.B. \'gelieferte Menge\'

Datenbank- Tabellennamen / Feldnamen:

Das Feld Artikelcode aus der Tabelle Artikel wird so notiert:
[artik.artik_cd]

## Allgemeines

### Kreditlimitprüfung

-   Kreditlimitprüfung im Standard nach folgender Formel:

    offener Kredit = Limit - Saldo - offener Auftragswert -
    Lieferscheine nicht fakturiert - Wechselobligo

### Freie Kennzeichen

Bearbeitungsliste mit allen freien Kennzeichen des Objektes

-   wird bei der Neuanlage mit den "Pflichtkennzeichen" vorbelegt

-   freies Kennzeichen (fd)

-   Wert

**Anmerkung**

Beim Speichern wird geprüft:

-   alle "Pflichtkennzeichen" müssen ausgefüllt sein

### Freie Gruppen

Bearbeitungsliste mit allen freien Gruppen des Objektes

-   wird bei der Neuanlage mit den "Pflichtgruppen" vorbelegt

-   freie Gruppenart (fd)

-   Gruppencode (fd)

**Anmerkung**

Beim Speichern wird geprüft:

-   alle "Pflichtgruppen" müssen ausgefüllt sein

-   ist bei einer Gruppe eine "Übergruppe" hinterlegt, so muss diese
    ebenfalls in der Liste vorhanden sein

### Rechenformel durchschnittlicher Einstandspreis

#### Version Bewerteter DUEST 

Allgemeines

-   Beim Verbuchen einer Eingangslieferscheinposition wird der
    "vorläufige DuEst" ermittelt. Beim Verbuchen einer
    Eingangsrechnung wird zunächst der "bewertete DuEst", und danach
    mit den neuen Werten der "vorläufige DuEst" ermittelt.
    Lagerbestände im "Lieferantenlager" bzw. Zugangsmengen in
    Eingangslieferscheinen auf "Lieferantenlager" werden nicht
    berücksichtigt. Eigenlager mit gleicher DuEst-Gruppe haben den
    gleichen DuEst (Lagerstände und offene Eingangslieferscheinwerte
    werden summiert)

DuEst vorläufig bewertet

folgende Größen:

-   DuEstBewertet

-   durchschnittlicher Einstandspreis ermittelt bei
    > Eingangsrechnungskontrolle

-   beinhaltet keine Eingangslieferscheine, die noch nicht mit Rechnung
    > bewertet wurden

-   LagerstandBewertet

-   analog zu DuEstBewertet, Lagerstand aktuell - Zugangsmenge in
    > unbewerteten Lieferscheinen

-   offener Eingangslieferscheinwert

-   Lieferscheinwert der unbewerteten Eingangslieferscheine

-   **durchschnittlicher Einstandspreis vorläufig**

-   (DuEstBewertet \* LagerstandBewertet + offener
    > Eingangslieferscheinwert) / Lagerstand

DuEst bewertet

-   EinstandswertArtikel

-   Zugangswert eines Artikels inklusive aller Zuschläge beim Verbuchen
    > einer Eingangsrechnung

-   ZugangsMengeArtikel

-   Summe der fakturierten Mengen eines Artikels einer Eingangsrechnung

-   **durchschnittlicher Einstandspreis bewertet**

-   **(DuEstBewertet \* LagerstandBewertet + EinstandswertArtikel) /
    > (LagerstandBewertet + ZugangsMengeArtikel)**

#### Version mit Aufrollung 

DUEST Relevante Buchungen

(Einkauf, Produktion, Umbuchung zwischen DUEST-Grppen)

-   Zu jeder Buchung werden folgende Daten ermittelt:

-   Lagerstand vor der Buchung = der aktuelle Lagerstand + alle
    > Lagerbewegungen mit einem kartei_dat > dem Warenzugangsdatum und
    > die zum Warenzugangsdatum ausgenommen Einkaufsbuchungen

-   Als Lagerstand wird dabei die Summe aller Läger in der aktuellen
    > DUEST-Gruppe verwendet

-   Da das Warenzugangsdatum im Eingangslieferschein nicht geändert
    > werden kann gibt es kein Problem mit einer nachträglichen Änderung
    > von diesem.

-   DUEST vor der BUCHUNG

-   Gibt es bereits eine Einkaufs Buchung mit einem größeren
    > Warenzugangsdatum, dann der DUEST der letzten Buchung
    > (Warenzugangsdatum, kartei_snr) mit Warenzugangsdatum <= der
    > eigenen Buchung.

-   Sonst der aktuelle DUEST

-   DUEST nach der BUCHUNG = (Lagerstand Alt \* DUEST ALT) + Zugangswert
    > der Position / Lagerstand Neu (=Lagerstand alt + Buchungsmenge)

-   Bei Lagerstand Alt < 0 oder Lagerstand Neu < 0 wird der
    > Einstandspreis der Buchung verwendet.

-   Wenn der DUEST dadurch negativ werden würde

-   und der alte DUES ist größer 0 wird der alte DUEST verwendet

-   ansonsten der Einstandspreis der Buchung

-   Es wird eine Aufrollung der DUEST´s ab dieser Buchung durchgeführt

-   Alle Lagerbewegungen deren Buchungsdatum >= dem eigenen
    > Buchungsdatum ist, werden aufgerollt

-   D.h. eine Warenzugangsbuchung am Nachmittag bewertet die Verkäufe
    > vom Vormittag neu!

-   Alle Einkäufe mit demselben Buchungsdatum nur dann, wenn die
    > kartei_snr > als die eigene ist (d.h. kann es nur bei
    > Korrekturen/ER-Kontrolle geben).

-   Um zu große Transaktionen zu vermeiden wird, wenn die Anzahl der
    > auzurollenden Positioen größer als der Parameter
    > "duestaur_max_pos" ist die Aufrollung über den Batch Job
    > gestartet.

-   Verkauf

-   Neuer DUEST/Wareneinsatz wird in die Lieferscheinposition,
    > Auftragsposition eingetragen

-   Statistikkorrektursatz wird erstellt

-   Einkauf

-   Neue DUEST Berechnung für diese Position

-   Update von Lagerstand-Alt, DUEST-Alt und DUEST-Neu

-   Der neu gerechnete DUEST-Neu ist die Basis für die folgenden
    > Lagerbewegungen

-   Bei jeder Korrektur einer Eingangslieferscheinposition, bei der
    Menge oder Einstandswert verändert werden, wird der DUEST dieser
    Position neu gerechnet und die Aufrollung wiederholt.  
    Als Basis für dieser Neuberechnung können der verspeicherte
    Lagerstand-ALT und DUEST-ALT verwendet werden.

Abgänge

Verkauf, Inventur, Diverse Lagerbuchng, Abgang Produktion

-   Wenn ein Verkauf mit einem Lieferscheindatum in der Vergangenheit
    gebucht wird, und es gibt einen Einkauf mit einem größeren
    Warenzugangsdatum, so wird der DUEST-Alt dieses nächsten Einkaufes
    statt dem aktuellen DUEST verwendet.

-   Der Lagerstand ALT dieser Einkaufsbuchung muss ebenfalls verändert
    und ab dieser Buchung muss wieder eine Aufrollung durchgeführt
    werden.

##### cst_duestrech

uf_duestrech

Parameter:

-   Firmennummer

-   Artikelnummer

-   DUEST-Gruppencode

-   Bewertungs Datum

-   kartei_snr

-   kartei_kz

-   Menge

-   Auch bei Korrekturen immer absolute Menge

-   Wert

-   Auch bei Korrekturen immer absoluter Wert

-   Aufrollmodus

-   Einstandspreis

-   Kann weggelassen werden, dann wird Wert / Menge als Einstandspreis
    > verwendet.

Retourniert:

-   boolean

-   False = Fehler ist aufgetreten

-   Der DUEST Neu kann bei Bedarf nach der Buchung aus der Variabel
    idc_duest_neu ausgelesen werden.

-   Der Aufruf muss immer nach der eigentlichen Lagerbuchung (die ja
    auch die kartei_snr liefert) passieren. Das Programm geht immer
    davon aus, dass die gebuchte Menge bereits im Lagerstand enthalten
    ist.

-   Hat der Artikel keine DUEST-Berechnung oder ist die Aufrollung nicht
    aktiviert -- return TRUE

-   Der Artikel muss bei Aufruf bereits gesperrt sein

Ablauf

-   Auslesen Artikeldaten (wenn geändert)

-   Prüfen ob kartei_duest bereits vorhanden ist.

-   Änderung

-   Sind Menge und Wert identisch und der Aufrollmodus ist nicht aktiv
    > -- wird der neu_duest lt. kartei_duest retourniert

-   Lagerstand alt und DUEST alt werden lt. kartei_duest verwendet

-   Lagerstand neu = Lagerstand alt + Menge

-   Neu

-   Lagerstand Neu  
    > = aktuelle Lagerstand  
    > - Lagerbewegungen mit eine kartei_dat > dem Bewertungs-Datum  
    > - Lagerbewegungen mit kartei_dat = Bewertungsdatum, zu denen es
    > keinen kartei_duest Eintrag gibt. . ausgenommen eigene Buchung

-   Als Lagerstand wird dabei die Summe aller Lager in der aktuellen
    > DUEST-Gruppe verwendet. Ausgenommen Lieferantenlager

-   Lagerstand Alt = Lagerstand Neu -- Menge

-   DUEST Alt

-   Gibt es bereits einen kartei_duest Eintrag mit einem größeren
    > Warenzugangsdatum, dann der DUEST vor der Buchung dieses
    > Eintrages.  
    > Erste in der Reihenfolge kartei_dat, kartei_snr

-   Sonst der aktuelle DUEST

-   Berechnung DUEST Neu =  
    (Lagerstand Alt \* DUEST Alt + Zugangswert ) / Lagerstand Neu

-   Bei Lagerstand Alt < 0 oder Lagerstand Neu < 0 wird der aktuelle
    > Einstandspreis (Wert/Menge) als DUEST Neu verwendet.  
    > Ist die Menge 0, wird in diesem Fall der DUEST Alt auch als DUEST
    > Neu verwendet.

-   Insert/Update kartei_duest

-   Aufrollung -- Lt. kartei_lagbew - ein Datensatz pro kartei_snr,
    DUEST-Gruppe mit

-   aktuellem Artikel

-   Lager in aktueller DUEST-Gruppe (kein Lieferantenlager)

-   Warenzugangsdtum > Bewertungungsdatum  
    > oder Warenzugangsdatum = Bewertungsdatum und es ist eine Buchung
    > ohne kartei_duest Eintrag  
    > oder Warenzugangsdatum = Bewertungsdatum und kartei_snr >
    > aktuelle kartei_snr

-   Wenn die Anzahl dieser auzurollenden Kartei-Lagerbewegungen größer
    > als der Parameter "duestaufr_max_pos" ist, so wird der Batch Job
    > gestartet, damit die Aufollung in einer eignen Transaktin
    > durchgeführt wird.

-   Mitrechnen aktueller Lagerstand

> Lt. Kartei-KZ

-   Lieferscheinposition -- Zugang aus Umbuchung zwischen DUEST-Gruppen
    > (es gibt kartei_duest)

-   wie bei Einkauf

-   Lieferscheinposition Normal

-   Ist der DUEST lt. vlfs_pos = dem neuen DUEST -- keine Aktion

-   Ist die Position bereits in der Statistik gebucht

-   Erstellen vlfs_pos_statkorr Datensatz mit den alten Werten

-   vlfs_pos.stat_gebucht_jn auf "n" setzen

-   vlfs_pos -- duest und weins updaten

-   auf_pos -- duest updaten

-   Ist die Position eine Set-Subposition

-   Neuberechnung des DUEST´s der SetHauptposition und Update dieser
    > (wie bei der eigenen Position)

-   Ist der Auftrag ein Produktionsauftrag

-   Update wert in kartei_duest des Produktionszuganges

-   Einspoolen der DUEST Aufrollung für diese Position (kartei_snr,
    > DUEST-Gruppe des Produktionszuganges)

-   Ist notwendig, da es sonst zu einem DEADLOCK kommen könnte.

-   Ist die Position eine Umbuchung, zu der es einen kartei_duest
    > Eintrag in einer anderen DUEST-Gruppe gibt

-   Update wert in kartei_duest

-   Aufrifen der DUEST Berechnung für dieser Position

-   Produktion

-   Wie bei Einkauf

-   Einkauf

-   Update kartei_duest (wenn nicht vorhanden -- keine Aktion)

-   Lagerstand alt = neu belegen

-   Lagerstand neu = Lagerstand alt + Buchungsmenge

-   DUEST Alt = letzter DUEST Neu

-   DUEST Neu = wird neu Berechnet und auch für die weiteren Aufroll
    > Buchungen verwendet

-   Inventur

-   Update duest + duest_b in iv_zeile

-   Diverse Lagerbuchung

-   Mit kartei_duest Eintrag -- wie bei Einkauf

-   Sonst Update duest und duest_b

-   Gibt es kartei_duest Einträge für andere DUEST-Gruppen, so wird
    > dessen Wert upgedatet und die DUEST-Berechnung dafür aufgerufen

-   Einfache Set-Produktion Abgang

-   Update esetp_set teil_duest

-   Update Einstandspreis der Hauptpositon (Summe der Sub-Positionen)

-   Update Wert in kartei_duest der Hauptposition

-   Einspoolen der DUEST Aufrollung für diese Position

-   Einfache Set-Produktion Zugang

-   Wie bei Einkauf

-   Kassa

-   Ist der DUEST lt. ka_bel_pos gleich dem neuen DUEST -- keine Aktion

-   Ist die Position bereits in der Statistik gebucht

-   Insert ka_bel_pos_statkorr

-   stat_gebucht_jn auf "n" setzen

-   Update ka_bel_pos -- duest und weins

-   Serviceauftrag

-   keine Aktion

-   Event für Ableitungen aufrufen

-   Update DUEST

-   Der letzte DUEST Neu wird in allen artik_lag Datensätzen mit der
    > aktuellen DUEST-Gruppe upgedatet

-   Wenn keine DUEST-Gruppen verwendet werden (es gibt nur eine
    > DUEST-Gruppe) dann auch am Artikelstamm.

uf_getduest

Parameter

-   Firmennummer

-   Artikelcode

-   Lagercode

-   Bewertungsdatum

-   Menge

-   Abang positiv (=der Normallfall)

-   Zugang negativ

-   0 = es wird nur der DuEst retourniert

Returniert

-   DUEST

-   Der Artikel muss beim Aufruf bereits gesperrt sein

Ablauf

-   Hat der Artikel keine DUEST-Berechnung wird der DUEST lt.
    Artikelstamm retourniert

-   Gibt es einen kartei_duest Eintrag für den Artikel, die DUEST Gruppe
    und einem größeren Bewertungsdatum

-   Nur bei aktivierter Aufrollung

-   Der zu retournierende DUEST ist der DUEST Alt dieser Buchung

-   Der Lagerstand Alt wird um die Menge vermindert

-   Aufrufen von uf_duestrech im Aufrollmodus für diese Position

-   Sonst wird der aktuelle DUEST lt. artik_lagd retourniert

##### DUEST Aufrollung -- Batch Programm

Parameter

-   Kartei_snr (p)

-   Duestgruppencode (p)

Aufruf von cst_duestrech.uf_duestrech für den jeweiligen kartei_duest
Eintrag.

-   Ist notwendig um Deadlocks bei Artikelübergreifenden DUEST
    Aufrollungen zu vermeiden (z.b. Produktionsbuchung)

### Anlage Fibukonto

Bei der Neuanlage eines Kunden bzw. eines Lieferanten, kann durch
"unbestimmt lassen" der Debitoren- bzw. Kreditorenadresse die
automatische Neuanlage des entsprechenden Fibukontos erreicht werden.
Folgende Standardbelegung:

-   Debitorennummer

-   Kundennummer \* 10 + 2

-   Kreditorennummer

-   Lieferantennummer \* 10 + 3

-   Name1

-   Name2

-   Name3

-   Strasse

-   Ländercode

-   Postleitzahl

-   Ort

-   Kontobezeichnung

-   Name1, Postleitzahl, Ort

-   Matchcode

-   Kundenmatchcode (in Großbuchstaben)

-   Telefonnummer 1 u. 2

-   Faxnummer 1 u. 2

-   Mailadresse 1 u. 2

-   Internetadresse

-   Ob ein Feld belegt wird, ist abhängig von der
    Tradecontrol-Jetfibuvariante

-   Die Werte für Telefon, Fax, Mail und Internet werden jeweils von den
    ersten beiden Kommunikationsarten mit Kennzeichen "t", "f",
    "e" oder "i" sofern vorhanden, herangezogen

-   Die übrigen Felder werden über den Vorschlagsdatensatz belegt

-   Vorschlagssatz Debitor = "deb_" + kundeerl_cd

-   Vorschlagssatz Kreditor = "kre_" + liefsach_cd

### Online UID-Prüfung

-   erfolgt über allgemeines Modul

-   UID der eigenen Firma, sowie zu prüfende UID werden übergeben

-   wenn Prüfung nicht OK

-   Ausgabe Fehlermeldung

-   Verarbeitungsfehler keine Aktion

-   eigene UID nicht ok keine Aktion

-   zu prüfende UID nicht ok

-   UID-Prüfstatus=3

-   ungültige UID=zu prüfende UID

-   UID=""

-   UID-Datum=aktuelles Datum

-   wenn OK, interaktiv (Benutzerkontrolle)

-   UID-Prüfstatus=1

-   ungültige UID=""

-   UID-Datum=aktuelles Datum

-   Ausgabe "Prüfung erfolgreich" + Name + Adresse in Ja/Nein-Box

-   Ja UID-Prüfstatus = 2

-   Nein

-   ungültige UID=zu prüfende UID

-   UID=""

-   wenn OK, Batchmodus (keine Benutzerkontrolle)

-   UID-Datum = aktuelles Datum

    **  
    **

### Abfrageregister "BelegKette"

-   Anzeigeliste mit den zum aktuellen Beleg verknüpften Belegen

-   kann für einen ganzen Beleg und auch für eine Belegposition
    > aufgerufen werden

-   WebdokFunktionalität

-   Belegart

-   Offert

-   Auftrag ([aufart_cd])

-   Lieferschein

-   Rechnung

-   Bestellung

-   E-Lieferschein

-   E-Rechnung

-   ZahlungKassa

-   Bezugsrechnung

-   Wartungsvertrag

-   Belegnummer

-   öffnen des Objektes abhängig von der Belegart möglich

-   Belegdatum

-   Belegnummer extern

-   Bestellnummer Kunde bei Auftrag

-   Auftragsnummer Lieferant bei Bestellung

-   Lieferscheinnummer Lieferant bei Eingangslieferschein

-   Eingangsrechnungsnummer Lieferant bei Eingangsrechnung

-   " ", sonst

-   Belegzustand

-   Auftragszustand

-   Lieferscheinzustand

-   Bestellzustand

-   Eingangslieferscheinzustand

-   " ", sonst

-   Adressmatchcode lt. Beleg

-   Lieferantenmatchcode

-   Kundenmatchcode

-   Sachbearbeiterkürzel Belegneuanlage

-   Datum und Zeit Belegneuanlage

### WebDokFunktionalität

-   Anzeige Dokument(e) zum aktuell in TC eingelesenen Datenobjekt im
    > Standard-WebBrowser

-   als aktuell eingelesener Datensatz versteht sich primär das aktuelle
    > Hauptdatenobjekt eines Fensters, ggf. aber auch Zeilen, die in
    > einem 1:n-Verhältnis zum Hauptdatenobjekt eines Fensters stehen

-   auf die Verfügbarkeit der WebDokFunktionalität wird in der folgenden
    > Beschreibung explizit pro Anzeigebereich hingewiesen

## Stammdaten

### Diverse Stammdaten

Verwaltung von folgenden Parametertabellen:

-   Gruppenschema Statistik

-   Periodenschema Statistik

-   Auftragsarten

-   Belegfixtexte

-   Bestellarten

-   Lagerbuchungsarten

-   Abrufgruppen

-   Artikelerlösgruppen

-   Artikelkoregruppen

-   Artikelprovisionsgruppen

-   Artikelsachkontengruppe

-   Artikelkonditionsgruppen

-   Bestellweisen

-   Mengeneinheiten

-   Erlöskonten Verkauf

-   Firmenstamm

-   Freie Kennzeichen

-   Freie Gruppenarten

-   Freie Gruppen

-   Freie Texte

-   Kommunikationsarten

-   Kundenerlösgruppen

-   Kundenkoregruppen

-   Kundenkonditionsgruppen

-   Kundenprovisionsgruppen

-   Kostenstellen Verkauf

-   Lager

-   Lieferbedingungen

-   Lieferantensachkontengrp

-   Belegkreise

-   Packstoffe ARA

-   Keine Begrenzung mehr auf maximal 10 Packstoffe in der Sortiernummer

-   Funktionscodes Personen

-   Preislisten

-   Provisionsarten

-   Provision

-   Sachkonten Einkauf

-   Textbausteine

-   Sprachen

-   USt-Codes

-   Versandarten

-   Vertreter

-   Verkaufskonditionsarten

-   Währungen

-   Zahlungsarten

-   Länder

### Adressen

#### Allgemeines

-   Copy & Paste ist verfügbar

#### Auswahldialog

-   Matchcode

-   Strasse

-   Land

-   Postleitzahl

-   Ort

-   natürliche Person (w)

-   Ja

-   Nein

-   Adresskennzeichen (p)

-   darf unbestimmt sein

-   (d)ebitoren

-   (k)unden

-   k(r)editoren

-   (l)ieferanten

#### Register "Liste"

-   Matchcode

-   Strasse

-   Land

-   Postleitzahl

-   Ort

#### Register "Detail"

**Teilbereich "Adressen"**

-   Matchcode

-   Name 1-4

-   Strasse

-   Ländercode (fd)

-   Postleitzahl

-   Ort

-   natürliche Person (c)

-   Sprachcode (fd)

-   Infotext

-   E-MailOrdner

-   Internetadresse

-   Debitoradresse (ca)

-   Kundenadresse (ca)

-   Kreditoradresse (ca)

-   Lieferantenadresse (ca)

**Teilbereich "Kommunikationsarten"**

Bearbeitungsliste mit allen Kommunikationsarten der Adresse

-   Kommunikationsart (fd)

-   Nummer (Wert)

    Sortierung: Sortiernummer

Anmerkung

Beim Speichern werden die Kommunikationsnummern der Personen mit
personeneigenem Anteil (z.B.: Durchwahl) dieser Adresse neu erstellt

Kann im CAS System verändert werden cas_datueb

#### Register "WerbeAdresse"

-   CAS-Funktionalität

-   wird bei Copy & Paste nicht mitkopiert

-   für die Werbeadresse:

-   Matchcode

-   Name 1-4 (a)

-   Strasse (a)

-   Ländercode (a)

-   Postleitzahl (a)

-   Ort (a)

    **Anmerkung:**

    Wird die Werbeadresse geändert, werden alle Personen, die die selbe
    alte Werbeadresse haben, auf die neue Werbeadresse mitgeändert.

#### Schaltflächen für Verzweigungen

-   Personen

-   Kunden

-   Debitoren

-   Lieferanten

-   Kreditoren

-   Geräte, welche sich an dieser Adresse aufhalten

-   Kontakte

-   wenn CAS-Modul aktiviert

### Personen

**Allgemeines**

Die Berechtigung wird in 2 Teilbereiche "CAS" und "Allgemein"
eingeteilt

Kann im CAS System verändert werden cas_datueb

#### Auswahldialog

-   Personencode

-   Vorname

-   Nachname

-   Matchcode der Adresse

-   Funktionscode (w)

#### Register "Liste"

-   Matchcode der Adresse

-   Personencode

-   Vorname

-   Nachname

-   Funktionscode

#### Register "Detail"

**Teilbereich "Personen"**

-   Matchcode der Adresse (af)

-   Personencode

-   Wird wenn nicht belegt beim Speichern lt. Parameter
    > pers_cd_auto_stellen vorgeschlagen.  
    > Dazu wird der maximale numerische Personencode der Adresse
    > ermittelt, um 1 erhöht und mit Vorlaufnullen aufgefüllt.

-   Applikationspersonencode (af)

-   entspricht bei Personen einer Adresse einer eigenen Firma dem
    > Personencode

-   ist sonst fix "" und nicht sichtbar

-   über öffnen können in einem eigenen Fenster weitere Daten zur
    > Applikationsperson gepflegt werden

-   Aktiv (c)

-   Titel

-   Vorname

-   Nachname

-   Geschlecht (d)

-   Geburtsdatum

-   Funktionscode (fd)

-   Kurzzeichen Korrespondenz

-   Freies Kennzeichen

-   Login

-   nur wenn es sich um die Adresse eines TradeControl-Mandanten handelt

**Teilbereich "Kommunikationsarten"**

Bearbeitungsliste mit allen Kommunikationsarten der Person

-   Kommunikationsart (fd)

-   Nummer (Wert)

-   Eingabe nur möglich, wenn der "personeneigene Anteil" leer ist

-   Personeneigener Anteil der Nummer

    Sortierung: Sortiernummer

####  Register "CAS"

-   Nur mit Modul "CAS" verfügbar

**Teilbereich "Werbeadresse"**

-   Matchcode (f) Adressen

-   Lieferadresse

-   Name 1 u. 2 (a)

-   Strasse (a)

-   Land (a)

-   Postleitzahl (a)

-   Ort (a)

-   Anrede, Vorname u. Nachname(a)

**Teilbereich "Freie Kennzeichen"**

siehe [Allgemeines](#kreditlimitprüfung)

**Teilbereich "Freie Gruppen"**

siehe [Allgemeines](#freie-gruppen)

**Teilbereich "Freie Texte"**

siehe [Allgemeines](#freie-gruppen)

#### Ordner

Für die Word Integration stehen folgende Datenfelder zur Verfügbung:

Personendaten:

-   pers_cd

-   kurzzeichen

-   persfunktion_cd

-   geschlecht_kz

-   titel

-   v_name

-   n_name

-   geburt_dat

-   pers_fkz

-   pers_telefon

-   pers_fax

-   pers_email

-   pers_internet

-   anrede1 (Herr oder Frau)

-   anrrde2 ("r Herr" oder " Frau")  
    Für z.B. "Sehr geehrt@anrede2@" "Sehr geehrter Herr" oder "Sehr
    geehrte Frau"

Folgende Blöcke sind wie unter Kunde Ordner beschrieben verfügbar:

-   Adresse und Werbeadresse

-   Firma

-   Person der Firma

#### Schaltflächen für Verzweigungen

-   Kontakte

-   wenn CAS-Modul aktiviert

### Kreditor

#### Allgemeines

-   es gibt eine eigene Ableitung für die Integration der EuroFib

-   manche Datenfelder in Detail und Bank sind abhängig von der
    eingesetzten Fibu vorhanden oder ausgeblendet

#### Auswahldialog

-   Kreditornummer

-   Matchcode

-   Kontobezeichnung

-   UID-Nummer

-   Strasse

-   Land

-   Postleitzahl

-   Ort

Anmerkung

-   wird nach einem Datenfeld einer der folgenden Tabellen gesucht, wird
    > die entsprechende Tabelle dynamisch mitgelesen

-   Freie Gruppe

-   AdressIdentifikationen

#### Register "Liste"

-   Kreditornummer

-   Name1

-   Strasse

-   Land

-   Postleitzahl

-   Ort

-   UID-Nummer

-   UID-Prüf-Status

-   ungültige UID

-   UID-Prüfdatum

#### Register "Detail"

Teilbereich "Kreditor"

-   Firma

-   nur bei der Neuanlage

-   Kreditornummer

-   nur bei der Neuanlage

-   Vorschlagscode (d)

-   Eingabe nur bei der Neuanlage

-   bei der Neuanlage ggf. lt. Kunde bzw. Lieferant vorgeschlagen

-   setzt bei der Eingabe Vorschlagscode für entsprechende
    > Fibu-Integration (EuroFib oder Jet)

-   Währungscode (fd)

-   Adressauswahlfeld (d)

-   Kreditorenmatchcode (f) Adressen

-   Kreditoradresse

-   Name 1 u. 2 (a)

-   Strasse (a)

-   Land (a)

-   Postleitzahl (a)

-   Ort (a)

-   Kontobezeichnung

-   bei EuroFib im nicht sichtbaren Bildschirmbereich

-   Vorschlag aus Adresse bei Neuanlage

-   Name1 + PLZ + Ort

-   Matchcode2

-   bei EuroFib im nicht sichtbaren Bildschirmbereich

-   Matchcode3

-   bei EuroFib im nicht sichtbaren Bildschirmbereich

-   Kreditor ist divers (c)

-   UID-Nummer

-   abhängig von Parametereinstellung [param.uid_online_kz] erfolgt
    > [Online UID-Prüfung](#online-uid-prüfung)

-   erfolgt ggf. nach einer aktivierten Syntaxprüfung

-   erfolgt nicht, wenn UID-Nummer leer ist

-   keine Eingabe, wenn UID-Prüf-Status = "9"

-   UID-Prüf-Status (d)

-   Eingabe 0 und 2 leeren ungültige UID

-   Eingabe 2 nur möglich, wenn UID-Nummer <> ""

-   Eingabe 9 leert UID-Nummer, ungültige UID und UID-Prüfdatum

-   ungültige UID

-   Eingabe/Anzeige nur, wenn Prüfstatus=1 oder 3

-   UID- Prüfdatum

-   keine Eingabe, wenn UID-Prüf-Status = "9"

-   Zahlungsart (d)

-   bei EuroFib im nicht sichtbaren Bildschirmbereich

-   Zahlungskonditionsnummer (fd)

-   Zahlungskonditionen

-   Skonto1-% (a)

-   Skonto1-Tage (a)

-   Skonto2-% (a)

-   Skonto2-Tage (a)

-   Nettotage (a)

-   Fremdkontonummer

Teilbereich "Banken"

-   Bearbeitungsliste mit den Banken des Kreditors

-   Copy&Paste wird nicht durchgeführt

-   siehe Debitor - Banken

#### Register "Zusatz"

Teilbereich "Freie Gruppen"

siehe [Allgemeines](#freie-gruppen)

Anmerkung

Beim Speichern werden bei Jetfibuintegration die zugehörigen
Jetfibutabellen sofort mitgeändert.

#### Auswahlpunkte im Menü "Extras"

-   Online UID-Prüfung

-   nur, wenn Modul aktiv

-   nur, wenn UID-Nummer belegt

-   Das Ergebnis wird im UID-Prüflog verspeichert

#### Schaltflächen für Verzweigungen

-   Lieferant

-   Person

-   UID Log

### Lieferanten

#### Auswahldialog

-   Firma

-   Lieferantennummer

-   Matchcode

-   Strasse

-   Land

-   Postleitzahl

-   Ort

-   freie Kennzeichen

-   Aktivkennzeichen (w)

#### Register "Liste"

-   Firma

-   Lieferantennummer

-   Matchcode

-   Strasse

-   Land

-   Postleitzahl

-   Ort

#### Register "Detail"

Teilbereich "Lieferant"

-   Firma

-   Lieferantennummer

-   Kreditorennummer (f) Fibukonten

-   Währungscode (fd)

-   Vorschlag bei Neuanlage lt. FIBU

-   Matchcode (f) Adressen

-   Adresse

-   Name 1 u. 2 (a)

-   Strasse (a)

-   Land (a)

-   Postleitzahl (a)

-   Ort (a)

-   Versandart (fd)

-   Lieferbedingung (fd)

-   Sachkontenzuordnung (fd)

-   Infotext

-   Liefertermine (d)

-   Mindestbestellwert

-   Lieferant ist aktiv (c)

-   keine Eingabe bei Neuanlage

-   Bestellung auspreisen (c)

-   Preis automatisch speichern (c)

-   Nexmart Name

-   Nur mit Nexmart Modul verfügbar

-   Nexmart ID

-   Nur mit Nexmart Modul verfügbar

-   Eingangsrechnungsimport Toleranzgrenze automatischer Aufbau

-   Eingangsrechnungsimport Toleranzgrenze automatische Verbuchung

Anmerkung

Wird die Lieferantenwährung geändert, so wird nach dem speichern
automatisch ein Preisumstellungsprogramm gestartet, das die
Artikeleinkaufspreise des Lieferanten in die neue Währung umrechnet.

**Teilbereich "Freie Kennzeichen"**

siehe [Allgemeines](#kreditlimitprüfung)

**Teilbereich "Freie Gruppen"**

-   siehe [Allgemeines](#freie-gruppen)

#### Register "Info"

-   Register dient nur zur Abfrage/Anzeige, es sind keine Änderungen
    möglich

-   nur mit Zusatzmodul "Info" verfügbar

**Teilbereich Lieferantendaten**

-   Firma

-   Lieferantennummer

-   aus Adresse

-   Name1

-   Name2

-   Straße

-   Land + "-" + Postleitzahl + " " + Ort

-   aus Fibu

-   Zahlungskondition

-   Versandart (d)

-   Lieferbedingung (d)

-   Mindestbestellwert

-   Bestellung mit Preisen (c)

-   Lieferanteninfo

-   Anlagedatum

-   Datum letzter Einkauf

-   Umsatz Einkauf Vorjahr

-   Umsatz Einkauf aktuelles Jahr

-   Anfragen vorhanden (c)

-   Bestellungen vorhanden (c)

-   Lieferant aktiv (c)

**Teilbereich Kommunikationsdaten Adresse**

-   Kommunikationsart (d)

-   Nummer

**Teilbereich Personendaten**

-   Name und Anrede

-   "Herr/Frau " + Titel + " " + Vorname + " " + Nachname

-   öffnen Person möglich

-   Telefonnummer

-   E-Mail Adresse

-   Faxnummer

-   Internetadresse

-   Mobiltelefonnummer

-   Vorname

-   Nachname

-   Funktionscode

#### Register Filialen

Liste über

-   Filialnummer

-   Filialmatchcode (a)

-   Kunden-Lieferantennummer

#### Register "Bestelltexte"

**  
**Bearbeitungsliste mit den Anfangs- bzw. Endtexten, die bei einer neuen
Bestellung automatisch in den Bestelltext eingefügt werden.

-   Textstelle (d)

-   Beleganfang

-   Belegende

-   Text

-   Fettdruck (c)

-   Unterstreichung (c)

    **Anmerkung**

Textbausteine können eingefügt werden, durch ein "+" am Textbeginn
versteht sich der weitere Text dieser Zeile als Textbausteincode, der
beim Einfügen in den Bestelltext aufgelöst wird

#### Auswahlpunkte im Menü "Extras"

-   Infoblatt DSGVO

-   nur, wenn Zusatzmodul "DSGVO" vorhanden [dsgvo_kz > "0"]

-   spoolt Batchjob "Infoblatt DSGVO" ein

-   aktueller Lieferant ist konstant

#### Schaltflächen für Verzweigungen

-   Bestellpositionen

-   Bestellungen

-   Eingangslieferscheinpositionen

-   Eingangslieferscheine

-   Eingangsrechnungen

-   ArtikelEinkauf

-   ArtikelIdentifikationen

-   Personen

-   Monatsumsatz

-   TC-Archiv

-   nur wenn TC-Scanmodul verfügbar

### Kunden

Allgemeines

Die Berechtigung wird in 2 Teilbereiche "CAS" und "Allgemein"
eingeteilt

#### Auswahldialog

-   Firma

-   Kundennummer

-   Matchcode

-   Strasse

-   Land

-   Postleitzahl

-   Ort

-   freie Kennzeichen

-   Aktivkennzeichen (w)

-   kein Auftrag/Offert seit (p)

-   optionaler Parameter

**Anmerkung**

-   wird Auftragsdatum ausgewählt, werden nur Kunden selektiert, für die
    > kein Auftrag/Offert mit [auf_dat >= {Parameter}] vorhanden ist

#### Register "Liste"

-   Firma

-   Kundennummer

-   Matchcode

-   Strasse

-   Land

-   Postleitzahl

-   Ort

-   letztes Auftragsdatum

-   nur belegt, wenn "kein Auftrag/Offert seit" ausgewählt

#### Register "Detail"

Teilbereich "Kunde"

-   Firma

-   Kundennummer

-   Am CAS System nur Vergabe mit Nummernkreis = cas_cd

-   Debitorennummer (f) Fibukonten

-   Debitorennummer OP (f) Fibukonten

-   Währungscode (a)

-   Matchcode (f) Adressen

-   Lieferadresse

-   Name 1 u. 2 (a)

-   Strasse (a)

-   Land (a)

-   Postleitzahl (a)

-   Ort (a)

-   Statistikkundennummer (f)

-   Vorschlag bei Neuanlage ist Kundennummer

-   Matchcode Statistikkunde (a)

-   Preisfindungskundennummer (f)

-   Vorschlag bei Neuanlage ist Kundennummer

-   Matchcode Preisfindungskunde (a)

-   Preisliste (fd)

-   wenn Preisfindungskundennummer <> Kundennummer keine Eingabe und
    > fix durch Preisliste des Preiskunden bestimmt

-   interner Aufschlag

-   Erlöszuordnung (fd)

-   Korezuordnung (fd)

-   Provisionszuordnung (fd)

-   Verkaufskondition (fd)

-   siehe Preisliste

-   Abrufgruppe (fd)

-   Versandart (fd)

-   Lieferbedingung (fd)

-   Infotext

-   Kunde ist divers (c)

-   Lieferschein hat Preis (c)

-   Rückstandsverwaltung (c)

-   Rückstandsausweis (c)

-   Kundenartikelnummer prüfen (c)

-   Zolltarifnummer auf Faktura (c)

-   Teillieferung erlaubt (c)

-   Offerte mit Endsumme drucken (c)

-   Kunde ist aktiv (c)

-   keine Eingabe bei Neuanlage

-   Fakturenart (d)

-   Debitorensammelrechnung ist bei einem diversen Debitor nicht erlaubt

-   Fakturenintervall (d)

-   Lagerkennzeichen (d)

-   Lagercode (fd)

-   Zahlungsart (fd)

-   Auftragskopfrabatt

-   Priorität Rückstände

-   Anzahl Lieferscheine

-   Anzahl Fakturen

-   Provisionsgruppe (fd)

-   Datanormausgabegruppe (fd)

-   Eingabe nur möglich, wenn Zusatzmodul aktiv

-   Datanormausgabenummer

-   Eingabe, wenn Datanormgruppe <> "-"

-   0 = Erstbestückung bei nächster Ausgabe

-   Einkäufergruppe

-   WebShop Kundengruppe (d)

    **Anmerkung**

    In der Tabelle "debitor" wird sowohl für die Debitorennummer, als
    auch für die Debitorennummer-OP ein Satz angelegt.

**Preisliste und Kundenkonditionsgruppe werden beim Speichern auf alle
Kunden kopiert, deren Preiskunde der aktuelle Kunde ist**

**Teilbereich "Freie Kennzeichen"**

siehe [Allgemeines](#kreditlimitprüfung)

**Teilbereich "Freie Gruppen"**

siehe [Allgemeines](#freie-gruppen)

#### Register "Info"

-   Register dient nur zur Abfrage/Anzeige, es sind keine Änderungen
    möglich

-   nur mit Zusatzmodul "Info" verfügbar

Teilbereich Kundendaten

-   Firma

-   Kundennummer

-   aus Adresse

-   Name1

-   Name2

-   Straße

-   Land + "-" + Postleitzahl + " " + Ort

-   Preisfindungskunde

-   sichtbar, wenn <> Kunde

-   Kundennummer

-   Kundenmatchcode

-   Zahlungsart (d)

-   Preisliste (d)

-   Verkaufskonditionsgruppe (d)

-   Grundrabatt

-   sichtbar, wenn <> 0

-   aus Fibu

-   Debitorennummer

-   Adresse des Debitoren

-   Bei einem diversen Debitoren wird hier nochmal die Kundenadresse
    > angezeigt

-   Name1

-   Name2

-   Straße

-   Land + "-" + Postleitzahl + " " + Ort

-   Zahlungskondition

-   Fakturenart (d)

-   Fakturenintervall (d)

-   Lieferschein mit Preisen (c)

-   Versandart (d)

-   Lieferbedingung (d)

-   Kundeninfo

-   Anlagedatum

-   Datum letzter Verkauf

-   Umsatz Vorjahr

-   Umsatz aktuelles Jahr

-   Kreditlimit

-   offenes Limit

-   Offerte vorhanden (c)

-   Aufträge vorhanden (c)

-   offene Posten vorhanden (c)

-   Kunde aktiv (c)

Teilbereich Kommunikationsdaten Adresse

-   Kommunikationsart (d)

-   Nummer

-   Sortierung: Sortiernummer

Teilbereich Personendaten

-   Name und Anrede

-   "Herr/Frau " + Titel + " " + Vorname + " " + Nachname

-   öffnen Person möglich

-   Telefonnummer

-   E-Mail Adresse

-   Faxnummer

-   Internetadresse

-   Mobiltelefonnummer

-   Vorname

-   Nachname

-   Funktionscode

#### Register "Servicedaten"

-   Daten müssen nicht vorhanden sein (keine Row in der Tabelle
    s_kunde).

-   Fakturenart (d)

-   Fakturenintervall (d)

-   Zahlungsart (fd)

-   Versandart (fd)

-   Lieferbedingungen (fd)

-   Anzahl Lieferscheine

-   Anzahl Fakturen

-   Preisliste (fd)

-   Reparaturschein hat Preis (c)

-   Zahlungskonditionen

-   Sethauptartikel für Wartungsvertrags- Verrechnungs- Aufträge (f)

    **Anmerkung zum Gebrauch:**

-   Die Servicedaten können mit der Funktionalität "Zeile einfügen"
    angelegt und mit "Zeile löschen" gelöscht werden.

-   Es kann maximal eine Zeile eingefügt werden.

#### Register "Auftragstexte"

**  
**Bearbeitungsliste mit den Anfangs- bzw. Endtexten, die bei einem neuen
Auftrag automatisch in den Auftragstext eingefügt werden.

-   Textstelle (d)

-   Beleganfang

-   Belegende

-   Text

-   Fettdruck (c)

-   Unterstreichung (c)  
    Belegtypen auf welchen der Text gedruckt werden soll

-   Auftragsbestätigung (c)

-   Kommissionsschein (c)

-   Lieferschein (c)

-   Rechnung (c)

-   Offert (c)

    **Anmerkung**

Textbausteine können eingefügt werden, durch ein "+" am Textbeginn
versteht sich der weitere Text dieser Zeile als Textbausteincode, der
beim Einfügen in den Bestelltext aufgelöst wird

#### Register "CAS"

-   Nur mit Modul "CAS" verfügbar

-   Am CAS-System dürfen nur Interessenten angelegt oder geändert
    werden. Die CAS Daten dürfen immer geändert werden. Diese Änderungen
    werden in der Tabelle cas_datueb mitgespeichert.

**Teilbereich "Kunde"**

-   Datum letzter Besuch (a)

-   Besuchsintervall in Wochen

-   CAS Gruppe (fd)

**Teilbereich "Freie Kennzeichen"**

siehe [Allgemeines](#kreditlimitprüfung)

**Teilbereich "Freie Gruppen"**

siehe [Allgemeines](#freie-gruppen)

**Teilbereich "Freie Texte"**

siehe [Allgemeines](#freie-gruppen)

#### Register Ordner

TC Office Ordner

In Word Vorlagen können mit folgende Platzhalter verwendet werden:

-   Im Word Dokument ist das Feld mit @<Feldname>@ anzugeben (z.B.
    @kunde_cd@ für die Kundennummer.

Kundenstammdaten:

-   kunde_cd

-   fa_nr

-   kunde_mc

-   stat_kunde_cd

-   preis_kunde_cd

-   kererl_cd

-   kundekst_cd

-   kundeprovgr_cd

-   preisli_cd

-   kundevkkondgr_cd

-   vkrab

-   vkrab2

-   vkrab3

-   abrugr_cd

-   debitor_nr

-   kunde_divers_jn

-   zuteil_prior

-   vkrech_kz

-   vkrech_sel_fkz

-   kunde_aktiv_jn

-   vklfs_preis_jn

-   zahlart_cd

-   teillief_jn

-   rueck_dru_jn

-   kd_ruck_aufb_jn

-   versart_cd

-   liefbed_cd

-   kunde_lagverw_kz

-   kunde_lag_cd

-   k_artikid_muss_jn

-   anz_vkrech

-   anz_vklfs

-   zallta_dru_jn

-   off_endsumme_jn

-   kunde_anl_dat

-   klv_kartei_snr

-   postanschr_ab_kz

-   ab_druck_kz

-   vorfakt_saldo

-   le_kont_dat

-   besint_wo

-   bes_wota

-   n_besuchs_dat

Adresse:

-   adr_mc

-   name1

-   name2

-   name3

-   name4

-   strasse

-   land_cd

-   land_bez

-   plz

-   ort

-   sprache_cd

-   fax

-   telefon

-   mail

-   internet

Werbe-Adresse (w.o mit werbe_ Präfix)

eigene Firma

-   fa_adr_mc

-   fa_name1

-   fa_name2

-   fa_name3

-   fa_name4

-   fa_strasse

-   fa_land_cd

-   fa_plz

-   fa_sprache_cd

Aktuelle Person in der eigenen Firma:

-   fa_pers_pers_cd

-   fa_pers_persfunktion_cd

-   fa_pers_geburt_dat

-   fa_pers_mail

-   fa_pers_fax

-   fa_pers_internet

-   fa_pers_kurzzeichen

-   fa_pers_telefon

-   fa_pers_titel

-   fa_pers_geschlecht_kz

-   fa_pers_v_name

-   fa_pers_n_anme

Debitor

-   off_auf_wert

-   off_vlfs_wert

-   saldo

-   saldo_faellig

-   max_mahn_stufe

-   wechselobligo

#### Register "Preisinfo"

**Teilbereich "Artikelauswahl"**

-   Artikelidentifikation

-   Eingabelogik

-   die Artikel, die der Auswahl entsprechen werden im Teilbereich
    > "Artikel" angezeigt

-   Preisfindungsdatum

-   Vorschlag=Tagesdatum

-   Standardmenge für Preisfindung

-   wenn leer, wird zunächst keine Preisfindung (bessere Performance)
    > durchgeführt

-   Eintrag von Vorschlagswert möglich

**Teilbereich "Artikel"**

-   Bearbeitungsliste der ausgewählten Artikel

-   Artikelnummer (a)

-   Artikelmatchcode (a)

-   Auslaufartikel (c) (a)

-   Verfügbarer Lagerbestand aller Dispolager (a)

-   Bestellte Menge Lieferant (a)

-   Mengenstaffel

-   wird als Menge für die Preisfindung herangezogen

-   Belegung löst die Preisfindung aus

-   wird zunächst durch Standardmenge belegt

-   Verkaufseinheit (a)

-   Verkaufspreis (a)

-   Währung (a)

-   Preiseinheit (a)

-   Rabatt 1-5 (a)

-   Nettoverkaufspreis (a)

-   Positionsbetrag (a)

-   Konditionsart (a)

**Teilbereich "Staffel"**

-   Anzeigeliste der Staffelpreise des aktuellen Artikels aus
    Teilbereich "Artikel"

-   AbMenge

-   Verkaufspreis

-   Währung

-   Rabatt 1-5

-   Nettoverkaufspreis

-   Konditionsart

-   DB-%

    **Anmerkung**

Beim Wechsel des Artikels werden die gespeicherten Staffelmengen der
Artikel/Kundenkombination ermittelt und je Staffelmenge die Preisfindung
durchgeführt. Eine Zeile wird nur dann angezeigt, wenn der Preis oder
die Rabatte von der vorigen Zeile abweichen.

#### Auswahlpunkte im Menü "Extras"

-   löschen CRM-Daten

-   nur, wenn Zusatzmodul "CRM" vorhanden und Zusatzmodul "DSGVO"
    > vorhanden [dsgvo_kz > "0"]

-   öffnet SpoolinFenster "Löschen CRM-Daten"

-   aktueller Kunde ist konstant

-   markierte Kunden inaktiv setzen

-   die markierten Kunden lt. Liste werden inaktiv gesetzt

-   nur, wenn Zusatzmodul "DSGVO" vorhanden [dsgvo_kz > "0"]

-   Funktionale Berechtigung "KundeInaktivSetzen" erforderlich

-   markierte Kunden aktiv setzen

-   die markierten Kunden lt. Liste werden aktiv gesetzt

-   nur, wenn Zusatzmodul "DSGVO" vorhanden [dsgvo_kz > "0"]

-   Funktionale Berechtigung "KundeInaktivSetzen" erforderlich

-   Infoblatt DSGVO

-   nur, wenn Zusatzmodul "DSGVO" vorhanden [dsgvo_kz > "0"]

-   spoolt Batchjob "Infoblatt DSGVO" ein

-   aktueller Kunde ist konstant

#### Schaltflächen für Verzweigungen

-   ArtikelLager

-   Auftragspositionen

-   Aufträge

-   Ausgangslieferscheine

-   Ausgangslieferscheinpositionen

-   wenn Kassenmodul vorhanden:

-   Kassenbon

-   Kassenbonpositionen

-   Umsatzabfrage

-   Ausgangsrechnungen

-   ArtikelIdentifikationen

-   Verkaufskonditionen

-   Kopieren Konditionen

-   Schaltfläche befindet sich am Register "Preisinfo"

-   funktionale Berechtigung "KopierenKonditionen" ist erforderlich

-   Fenster "Verkaufskonditionen" wird mit Parameter "KundeKopieren"
    > geöffnet

-   Firma, jedoch nicht Kunde ist konstant

-   Personen

-   Monatsumsatz

-   Offene Posten

-   mit OP-Debitor

-   Geräte, deren Standortkunde der aktuelle Kunde ist

-   wenn CAS vorhanden

-   KundeMitbewerb

-   CAS-Kontakte

-   Verkaufspositionen

-   nur wenn Kassenmodul verfügbar

-   TC-Archiv

-   nur wenn TC-Scanmodul verfügbar

-   WebShop

-   Nur wenn WebShop Kundengruppe ausgefüllt ist

### Debitor

#### Allgemeines

-   es gibt eine eigene Ableitung für die Integration der EuroFib

-   manche Datenfelder in Detail und Bank sind abhängig von der
    eingesetzten Fibu vorhanden oder ausgeblendet

#### Auswahldialog

-   Debitornummer

-   Matchcode

-   Kontobezeichnung

-   UID-Nummer

-   Strasse

-   Land

-   Postleitzahl

-   Ort

    **Anmerkung**

-   wird nach einem Datenfeld einer der folgenden Tabellen gesucht, wird
    > die entsprechende Tabelle dynamisch mitgelesen

-   Freie Gruppe

-   AdressIdentifikationen

#### Register "Liste"

-   Debitornummer

-   Name1

-   Strasse

-   Land

-   Postleitzahl

-   Ort

-   UID-Nummer

-   UID-Prüf-Status

-   ungültige UID

-   UID-Prüfdatum

#### Register "Detail"

**Teilbereich "Debitor"**

-   Firma

-   nur bei der Neuanlage

-   Debitornummer

-   nur bei der Neuanlage

-   Vorschlagscode (d)

-   Eingabe nur bei der Neuanlage

-   bei der Neuanlage ggf. lt. Kunde vorgeschlagen

-   setzt bei der Eingabe Vorschlagscode für entsprechende
    > Fibu-Integration (EuroFib oder Jet)

-   Währungscode (fd)

-   Adressauswahlfeld (d)

-   Debitorenmatchcode (f) Adressen

-   wird die Adresszuordnung geändert und elektronische Rechnung =
    > "j", wird die E-Mail-Adresse Rechnungsversand auf unbestimmt
    > gesetzt

-   Debitoradresse

-   Name 1 u. 2 (a)

-   Strasse (a)

-   Land (a)

-   Postleitzahl (a)

-   Ort (a)

-   Kontobezeichnung

-   Vorschlag aus Adresse bei Neuanlage

-   Name1 + PLZ + Ort

-   bei EuroFib im nicht sichtbaren Bildschirmbereich

-   Matchcode2

-   bei EuroFib im nicht sichtbaren Bildschirmbereich

-   Matchcode3

-   bei EuroFib im nicht sichtbaren Bildschirmbereich

-   Debitor ist divers (c)

-   UID-Nummer

-   abhängig von Parametereinstellung [param.uid_online_kz] erfolgt
    > [Online UID-Prüfung](#online-uid-prüfung)

-   erfolgt ggf. nach einer aktivierten Syntaxprüfung

-   erfolgt nicht, wenn UID-Nummer leer ist

-   keine Eingabe, wenn UID-Prüf-Status = "9" oder bei einem diversen
    > Debitor

-   UID-Prüf-Status (d)

-   Eingabe 0 und 2 leeren ungültige UID

-   Eingabe 2 nur möglich, wenn UID-Nummer <> ""

-   Eingabe 9 leert UID-Nummer, ungültige UID und UID-Prüfdatum

-   ungültige UID

-   Eingabe/Anzeige nur, wenn Prüfstatus=1 oder 3

-   UID-Prüfdatum

-   keine Eingabe, wenn UID-Prüf-Status = "9"

-   Kennzeichen Zahlungsart (d)

-   bei EuroFib im nicht sichtbaren Bildschirmbereich

-   Zahlungskonditionsnummer (fd)

-   Zahlungskonditionen

-   Skonto1-% (a)

-   Skonto1-Tage (a)

-   Skonto2-% (a)

-   Skonto2-Tage (a)

-   Nettotage (a)

-   Kreditlimit

-   Anzeigefelder

-   offener Auftragswert (a)

-   offener Lieferscheinwert (a)

-   Saldo (a)

-   Saldo fällig (a)

-   freies Limit (a)

-   höchste Mahnstufe (a)

-   Wechselobligo (a)

-   Fremdkontonummer

-   Mahnsperre (d)

-   Mahnmethode und Kommunikationsdaten

-   nur bei EuroFib im sichtbaren Bildschirmbereich

-   Mahnungsart (d)

-   Faxnummer Mahnung Auswahl (d)

-   alle Faxnummern, die der Rechnungsadresse zugeordnet sind (Adresse
    > und Personen)

-   Eingabe nur, wenn Mahnungsart = "2"

-   Vorname

-   Nachname

-   Faxnummer

-   Faxnummer Mahnung

-   Eingabe nur, wenn Mahnungsart = "2"

-   E-Mail-Adresse Mahnung Auswahl (d)

-   alle E-Mail-Adressen, die der Rechnungsadresse zugeordnet sind
    > (Adresse und Personen)

-   Eingabe nur, wenn Mahnungsart = "3"

-   Vorname

-   Nachname

-   E-Mail-Adresse

-   E-Mail-Adresse Mahnung

-   Eingabe nur, wenn Mahnungsart = "3"

-   Rechnungsversand (d)

-   bei left(vrechausart.sst_kz, 2) <> "eb" muss UID-Nummer
    > eingegeben werden

-   bei left(vrechausart.sst_kz, 2) <> "eb" muss Fremdkontonummer
    > eingegeben werden

-   E-Mail-Adresse Rechnungsversand Auswahl (d)

-   alle E-Mail-Adressen, die der Rechnungsadresse zugeordnet sind
    > (Adresse und Personen)

-   Vorname

-   Nachname

-   E-Mail-Adresse

-   E-Mail-Adresse Rechnungsversand

-   Keine Eingabe bei Diversen Debitor

-   verpflichtende Eingabe nur, wenn Rechnungsversand
    > [vrechausart.vrech_druck_kz] = „e"

-   BBG-Partnernummer

-   BBG-Geschäftszahl

**Teilbereich "Banken"**

-   Bearbeitungsliste mit den Banken des Kreditors

-   Keine Eingabe bei diversen Debitor

-   Copy&Paste wird nicht durchgeführt

-   IBAN

-   Bei Eingabe Vorschlag:

-   Ländercode -- Es wird ein Land mit den ersten beiden Stellen des
    > ISO2 Ländercodes des IBAN ermittelt. Ein Land mit IBAN Definition
    > wird dabei bevorzugt.

-   Wenn die Lönge der BLZ am Land 0 ist entfallen die weiteren
    > Vorschlagslogiken und als BLZ und Kontonummer wird blank
    > vorgeschlagen.

-   Prüfung Länge und Prüfziffer lt. Daten am Länderstamm

-   Bankleitzahl  
    > Wenn lt. Ländercode die Länge der Bankleitzahl definiert ist, wird
    > die Bankleitzahl ermittelt und vorgeschlagen. Ist die
    > entpsrechende Bank nicht angelegt, wird wenn lt. Land die Bank
    > nicht zwingend angelegt sein mus, die Dummy Bank des Landes
    > vorgeschlagen.

-   Kontonummer -- Vorschlag lt Länge Kontonummer lt. Land

-   Für nicht EU Banken kann hier auch blank eingegeben werden.

-   Land (fd)

-   Bankleitzahl (f)

-   BIC (a)

-   Bankbezeichnung (a)

-   Kontonummmer

-   nur bei EuroFib sichtbar

-   Zahlungart (d)

-   Aviso (c)

-   Aktiv (c)

-   SEPA-Mandat

-   Mandat-Druckdatum

-   Mandat-Unterschriftsdatum

#### Register "Zusatz"

**Teilbereich "Freie Gruppen"**

siehe [Allgemeines](#freie-gruppen)

Anmerkung

Beim Speichern werden bei Jetfibuintegration die zugehörigen
Jetfibutabellen sofort geändert.

#### Auswahlpunkte im Menü "Extras"

-   Online UID-Prüfung

-   nur, wenn Modul aktiv

-   nur, wenn UID-Nummer belegt

-   Das Ergebnis wird in uidprueflog gespeichert

#### Schaltflächen für Verzweigungen

-   Kunde

-   Person

-   OP\'s Debitor

-   Ausgangsrechnungen

-   UID Log

-   TC-Archiv

-   nur wenn TC-Scanmodul verfügbar

### Artikel

#### Auswahldialog

-   Firma

-   Artikelnummer

-   Matchcode

-   Artikelkennzeichen (w)

-   Lagerkennzeichen (w)

-   freie Kennzeichen

-   Aktivkennzeichen (w)

-   Konditionsgruppe (w)

-   Artikelbezeichnung

-   Identifikationsnummer

-   Lagerstand

-   verfügbare Menge

-   offene Auftragsmenge

-   offene Bestellmenge

-   Tag (Matchcode über Tabdazu Logik)

-   Attribut-Nr (w) (TabDazu)

-   Attribut-Wert (TabDazu)

-   Kann abhängig von der Attributart ein Tag-Matchcode oder ein
    > Attribut-Inhalt sein

-   Zolltrarifnummer aktiv (w)

-   Notwendig um alle Artikel mit inaktiven Zolltraifnummern zu finden

-   Ltz. DDS-Referenznummer

#### Register "Liste"

-   Firma

-   Artikelnummer

-   Matchcode

-   Artikelkennzeichen

-   Lagerkennzeichen

-   Verfügbare Menge

-   Bestellmenge

-   Internetadresse (f)

#### Register "Detail"

**  
**Teilbereich "Artikel"**

-   Firma

-   Artikelcode

-   Matchcode

-   Artikelkennzeichen (d)

-   Lagerkennzeichen (d)

-   Verkaufseinheit (=Lagereinheit) (fd)

-   Anzahl kleinste Einheiten in einer Verkaufseinheit

-   Bei Änderung nur mit einer eigenen Berechtigung änderbar

-   Änderungen siehe unten

-   Kleinste Einheit (fd)

-   Verkaufspreis per Menge (d)

-   Verkaufspreis per Einheit (d)

-   Verkauflosgröße

-   Verkaufsloseinheit

-   Verkaufslosprüfen (d)

-   Erlöszuordnung (fd)

-   Sachkontenzuordnung (fd)

-   Korezuordnung (fd)

-   Provisionsgruppe (fd)

-   Verkaufskonditionsgruppe (fd)

-   Infotext

-   Zolltarifnummer (f)

-   Es darf keine Inaktive Zolltarifnummer verwendet werden

-   Ursprungsland (fd)

-   Umrechnungsfaktor Lagereinheit Intrastateinheit

-   Besondere Maßeinheit (a)

-   Gewicht ohne Verpackung in kg

-   EUDR (c)

-   Kann nicht geändert werden, wenn lt. Zolltarifnummer fix

-   Letzte DDS-Referenznummer (f)

-   Kann nur bei EUDR Relevanten Artikeln eingegeben werden

-   Garantiemonate Verkauf

-   Garantiemonate Einkauf

-   Mindestdeckungsbeitrag in %

-   Bruttogewicht in kg

-   Kennzeichen Mindestbestand (d)

-   Beobachtungszeitraum für Bedarfsberechnung

-   Wochen

-   Eingabe bestimmt Tage

-   Tage

-   Eingabe bestimmt Wochen (immer aufgerundet)

-   Prozentsatz Maximalbestand

-   DuEst-Prozentsatz für Kassenlösung

-   Eingabe nur bei Artikeln ohne DuEst-Rechnung

-   wird im Kassenmodul für Wareneinsatzermittlung herangezogen

-   Charge mit Ablaufdatum (c)

-   Auslaufartikel (c)

-   Rückstandsverwaltung (c)

-   Artikel ist skontofähig (c)

-   DuEst-Rechnung wird durchgeführt (c)

-   Artikel ist kopfrabattfähig (c)

-   Artikel ist aktiv (c)

-   keine Eingabe bei Neuanlage

-   Artikel ist ARA-pflichtig (c)

-   Artikel ist kopfrabattfähig (c)

-   Lagerstand Dispo-Lager (a)

-   Verfügbarer Bestand Dispo-Lager (a)

-   Bestellte Menge Lieferant + offene Menge Produktion (a)

-   Durchschnittlicher Einstandspreis

-   Eingabe, wenn DuEst-Rechnung **nicht** durchgeführt wird
    > und alle Eigenlager die selbe DuEst-Gruppe besitzen, oder wenn
    > Artikel ohne Lagerführung

-   wenn alle Eigenlager die selbe DuEst-Gruppe besitzen, werden beim
    > Speichern auch die Eigenlagersätze in [artik_lag] mitgeändert

-   Durchschnittlicher Einstandspreis abgewertet

-   w.o.

-   Internetadresse (f)

-   Suchen öffnet Internetexplorer ohne bestimmter Seite

-   öffnet Internetexplorer mit aktueller Seite

-   Zusatzmodul "Produktinfo" erforderlich

-   ARA Gruppe (fd)

Ändern der Kleinsten Einheit (keh_veh_mg)

-   Wurde die keh_veh_mg verändert passieren folgende Updates beim
    Speichern (nach Locken des Artikels):

-   Wird von 1 auf irgendetwas anderes geändert, wird das
    Verkaufspreis-Kennzeichen auf "in Verkaufseinheit" gestellt.

-   Für artik_lief, auf_pos_best, best_pos, elfs_pos

-   ekpr_keh_eeh_kz = "e" wenn keh_eeh_mg vorher 1 war

-   keh_eeh_mg / alte keh_veh_mg \* neue keh_veh_mg

-   ekpr_ftr neu rechnen, wenn ekpr_keh_eeh_kz "k" bleibt

-   Bei auf_pos_best, best_pos und elfs_pos nur offene Positionen

artikid

-   keh_mg / alte keh_veh_mg \* neue keh_veh_mg (wenn nicht null)

-   auf_pos -- Nur offene noch nicht (teil) gelieferte Positionen

-   vkpr_keh_veh_kz = "v" wenn keh_veh_mg vorher 1 war

-   vkpr_ftr lt. Artikelstamm neu berechnen, wenn vkpr_keh-eeh_kz "k"
    bleibt

-   keh_veh_mg = neue keh_veh_mg

**Teilbereich "Freie Kennzeichen"**

siehe [Allgemeines](#kreditlimitprüfung)

**Teilbereich "Freie Gruppen"**

siehe [Allgemeines](#freie-gruppen)

**Teilbereich "Artikeltexte"**

Bearbeitungsliste mit allen Textzeilen des Artikels

-   Sprachcode (fd)

-   Artikeltext

-   Text auf AB drucken (c)

-   Text auf Kommissionsschein drucken (c)

-   Text auf Lieferschein drucken (c)

-   Text auf Rechnung drucken (c)

-   Text auf Bestellung drucken (c)

-   Text auf Preisliste drucken (c)

-   Text auf Offert drucken (c)

-   Text auf Wartungsvertrag drucken (c)

#### Register "Info"

-   Register dient nur zur Abfrage/Anzeige, es sind keine Änderungen
    möglich

-   nur mit Zusatzmodul "Info" verfügbar

-   Firma

-   Artikelnummer

-   Artikelmatchcode

-   Artikelkennzeichen

-   Lagerführungskennzeichen

-   Verkaufseinheit

-   nur wenn keh_veh_mg <> 1

-   Anzahl kleinste Einheiten in einer Verkaufseinheit

-   kleinste Einheit

-   Verkaufspreis pro Einheit

-   Verkaufspreis pro Menge

-   wenn > 1

-   nur wenn Verkaufslosmenge > 1

-   Losmenge

-   Verkaufseinheit

-   wenn Loseinheit <> Verkaufseinheit

-   Fixtext "per"

-   Loseinheit

-   Verkaufskonditionsgruppe

-   Artikelinfo

-   Umsatz und Umsatzmenge Vorjahr

-   Umsatz und Umsatzmenge lfd. Jahr

-   Anlagedatum

-   Datum letzter Verkauf

-   Datum letzter Einkauf

-   Lagerstand

-   alle Dispolager berücksichtigt

-   verfügbarer Lagerbestand

-   alle Dispolager berücksichtigt

-   bestellte Menge Lieferant

-   Rahmenmenge Einkauf

-   Abrufmenge Verkauf

-   Auslaufartikel (c)

-   Artikel aktiv (c)

-   Bild 4x4

-   durchschnittlicher Einstandspreis

-   lt. [fa.default_lag_cd artik_lag], bzw. wenn nicht vorhanden oder
    > Null lt. [artik]

-   letzter Einstandspreis

-   w.o.

**Teilbereich Lager**

Anzeigeliste je Lager des Artikels

-   es werden jene Lager angezeigt, bei denen Lagerstand bzw. verfügbare
    Menge <> 0 sind

-   nur Eigenlager [lag_kz = "e"]

-   Lagernummer

-   Lagerbezeichnung

-   Lagerstand

-   verfügbarer Lagerbestand

-   Dispolager (c)

-   Summenzeile

**Teilbereich Verkaufspreise**

Anzeigeliste je Preisliste des Artikels

-   es werden nur aktuelle Preise (Tagesdatum) mit der kleinsten
    Staffelmenge angezeigt

-   keine Aktionen

-   Preisliste

-   Preis

-   Währung

-   DB-%

**Teilbereich Einkaufspreise**

Anzeigeliste der Einkaufspreise des Artikels

-   es werden je Lieferant nur aktuelle Preise (Tagesdatum) mit der
    kleinsten Staffelmenge angezeigt

-   keine Aktionen

-   Lieferantenmatchcode

-   Bestellvorschlagskennzeichen

-   Preis

-   Währung

-   Rabatt 1-5

-   Nettopreis in Grundwährung

-   Einkaufspreismenge (artik_lief.ekpr_pro_mg)

-   Einkaufspreismengeneiheit

-   Wenn ekpr_keh_eeh_kz = "k" artik.keh_cd

-   Wenn ekpr_keh_ehh_kz = "e" artik_lief.eeh_cd

#### Register "Alternativen"

Bearbeitungsliste mit allen Alternativ-Artikeln des Artikels

-   Artikelnummer alternativ (f)

-   Matchcode (a)

-   Aktionskennzeichen Verkauf (d)

-   Aktionskennzeichen Einkauf (d)

-   Webshop (d)

    **Anmerkung**

    Es kann jeweils nur ein Artikel zum Ersetzen definiert sein

#### Register "Pack"

Bearbeitungsliste mit allen Packstoffen des Artikels

-   Packstoffcode (fd)

-   Bezeichnung (a)

-   Gewicht in kg

#### Register "Set"

**Teilbereich "Sethauptartikel"**

Bereich ist nur für Artikel mit Artikelart "Set" zulässig

-   Freigabeebene Set/Teil (d)

-   Preisebene Set/Teil (d)

-   Statistikebene Set/Teil (d)

-   Fibuüberleitungsebene Set/Teil (d)

-   Druckkennzeichen Set/Teil/Beide (d)

    **Teilbereich "Setbestandteile"**

    Bearbeitungsliste mit allen Setbestandteilen des Hauptartikels,
    werden Zeilen bei "Nicht-Setartikeln" angelegt, sind diese als
    Folgeartikel zu verstehen

-   Artikelcode des Setbestandteils (f)

-   Artikelmatchcode (a)

-   Menge im Set

-   Durchschnittlicher Einstandspreis

-   Eingabe nur dann, wenn DuEst des Teilartikels leer ist

-   WebShop Attribute fehlen (c) (a)

-   Ist ja wenn der Hauptartikel ein Konfigurationsartikel ist und der
    > Subartikel nicht alle Attribute definiert hat, die als
    > Konfigurationsattribute definiert wurden.

#### Register "Verkaufspreis"

**Teilbereich "Preis- Artikel"**

-   Artikelcde des Preisartikels (f)

-   Verkaufs- Konditionen / Preise werden von diesem Artikel
    > herangezogen

-   Artikelmatchcode (a)

    **Teilbereich "Preise"**

    Bearbeitungsliste mit den Listenpreisen des Preisartikels

-   Preislistencode (fd)

-   Datum gültig ab

-   Datum gültig bis (a)

-   ab Menge

-   Verkaufspreis

-   Rabatt 1 (a)

-   Rabatt 2 (a)

-   Naturalrabatt (a)

#### Register "Identifikationen"

Bearbeitungsliste mit den Identifikationsnummern des Artikels

-   Art der Identifikation (d)

-   Kundennummer (f)

-   Eingabe nur dann, wenn Identifikationsart "Kunde"

-   Lieferantennummer (f)

-   Eingabe nur dann, wenn Identifikationsart "Lieferant"

-   Matchcode Kunde bzw. Lieferant (a)

-   Menge in kleinster Einheit

-   Eingabe nur dann, wenn Identifikationsart "EAN"

-   Menge in Lagereinheit

-   Setzt bei Eingabe die Menge in kleinster Einheit und umgekehrt

-   Identifikationsnummer

-   wird bei Identifikationsart "EAN" auf EAN-13 geprüft

-   Vergeben (c)

-   Kann nur bei EAN, ausgefüllter BBN am Firmenstamm und leerer
    > Identifikationsnummer verwendet werden.

-   Bei Ja wird beim Speichen die EAN automatisch vergeben. Abhängig vom
    > Parameter eanverg_kz werden dabei bereits vergebene Nummern
    > übersprungen.

Anmerkung

-   Die Neuanlage, das Ändern und das Löschen von
    Lieferantenartikelnummern wird auch in der Tabelle artik_lief
    durchgeführt

#### Register "Service"

-   Seriennummerpflicht

-   nur bei Geräteartikel

-   Serviceartikelart

-   Service Verrechnungsart

-   Infotext

#### Register "Preisinfo"

**Teilbereich "Artikelpreise"**

Anzeigeliste mit den aktuell gültigen Preisen des Artikels

-   Preislistennummer (d)

-   Von-Datum

-   Bis-Datum

-   Ab-Menge

-   Verkaufspreis in Grundwährung

-   Grundwährungssymbol

-   Preis in "ATS", wenn Grundwährung "EUR" sonst Preis in "EUR"

-   nur wenn lt. Firmenstamm doppelte Preisauszeichnung aktiviert ist

-   Rabatt 1

-   Rabatt 2

-   Naturalrabatt

-   DB-%

**Teilbereich "Artikelaktionspreise"**

Anzeigeliste mit den aktuell gültigen Aktionspreisen des Artikels

-   Preislistennummer (d)

-   Aktionsart (Artikel, Kunde oder Konditionsgruppe)

-   Kundenmatchcode, Konditionsgruppenbezeichnung oder leer abhängig von
    Aktionsart

-   Von-Datum

-   Bis-Datum

-   Ab-Menge

-   Verkaufspreis in Grundwährung

-   Grundwährungssymbol

-   Rabatt 1-5

-   Naturalrabatt

-   DB-%

**Teilbereich "Artikeleinkaufspreise"**

Anzeigeliste mit den aktuell gültigen Einkaufspreisen des Artikels

-   Lieferantenmatchcode

-   Bestellvorschlagskennzeichen

-   Von-Datum

-   Bis-Datum

-   Ab-Menge

-   Einkaufspreis

-   Währung

-   Rabatt 1-5

-   Nettopreis in Grundwährung

**  
Teilbereich "Kundenpreisfindung"**

-   Kundennummer (f)

-   Wird lt. letzter Eingabe vorgeschlagen

-   Kundenmatchcode (a)

-   Kundeninfotext (a)

-   Preisfindungsdatum

-   Wird lt. letzter Eingabe vorgeschlagen

-   Wenn nicht definiert, dann das aktuelle Datum

-   Menge

-   Verkaufsmengeneinheit Artikel (a)

-   Preis und Rabatte lt. Preisfindung (a)

-   Betrag

-   Kundenwährung

-   Verkaufskonditionsart

-   DB-%

#### Register "WebShop"

Teilbereich Artikeldaten

-   Artikelnummer (a)

-   Artikelmatchcode (a)

-   WebShop (c)

-   Durch Umschalten auf "j" wird beim Speichern der deutsche WebShop
    > Text vorgeschlagen (Name = Matchcode)

-   Marke (d)

Teilbereich WebShopTexte

-   Sprache (d)

-   Durch Umschalten der wird der Text in dieser Sprache angezeigt. Gibt
    > es noch keinen Text in dieser Sprache, so wird eine neue Zeile mit
    > dieser Sprache erstellt.

-   WebShop Name

-   WebShop Beschreibung

-   WebShop Kurzbeschreibung

-   SEO Text

Liste der Texte (a)

-   Sprache

-   Name

-   Löschen von Zeile ist möglich

Teilbereich Attribute

Liste über

-   Attributart (d)

-   Konfig (c)

-   Tag Auswahl (d)

-   DropDown für die vorgegegebnen TagAttibute Werte

-   Wert

-   Wird bei einem Column Attribut automatisch lt. Artikelstamm Column
    > belegt

-   Keine Eingabe bei einem Tag oder bei einem Konfig Attribute

-   Bei einem Tag Attribute wird hier der deutsche Text angezeigt --
    > keine Eingabe möglich

-   Attribute mit aranzeige_jn = "n" werden nicht angezeigt und können
    auch nicht neu erfasst werden.

    Anmerkung #53668

    es darf nicht das letzte Attribut (bei Multiselect) gelöscht werden
    wenn es in einer Warengruppe oder übergeordneten Warengruppe
    zwingend ist [webshopwg_webshopattribute. webwgatt_zwingend_jn =
    "j"]

Teilbereich Objekte

Liste über:

-   Objektart (d)

-   Link

-   Eingabe nur bei Link Objektart möglich

    Anmerkung

-   Mit Drag&Drop können hier Bilder, PDF´s oder MP3 Files abgelegt
    werden.

-   Bei einer neuen Zeile muss dann die jeweilige Objektart ausgewählt
    werden.

-   Wenn eine Zeile gelöscht wird, dann wird auch das jeweilige Objekt
    aus dem Verzeichnis gelöscht.

-   Durch eine Änderung der Objektart wird das File in das jeweilig
    Verzeichnis lt. Objektart verschoben.

-   Die Objekte müssen auch beim Löschen des Artikels mitgelöscht
    werden.

-   Mit Doppelklick auf eine Zeile kann das jeweilige Objekt geöffnet
    werden

-   Download Link ist nur bei einem Verrechnungsartikel erlaubt. Es darf
    pro Artikel maximal ein Download-Link und ein Sample-Link zugeordnet
    werden.

Teilbereich WebShop Warengruppen

-   TreeView über alle WebShop Warengruppen

-   Durch Klicken auf das Symbol kann der Artikel einer WWG zugeordnet
    werden oder die Zuordnung gelöscht werden.

-   wenn eine Warengruppe ausgewählt wird muss für diese und all deren
    Parents geprüft, alle
    Warengruppe-Attribute[webshopwg_webshopattribute] anlegt werden,
    sofern nicht vorhanden #53668

-   nicht bei Konfigurationsartikel [artik.artik_kz = "k"]

-   der erste eingetragene Defaultwert [webshopwg_webshopattribute.
    > webwgatt_default] zieht (von Unten nach Oben)

-   unabsichtliches Klicken sollte Attribute wieder löschen

-   Der Zurodnungsstatus wird durch 3 verschiedenen Symbole angezeigt:

-   Keine Zuordnuner

-   Zugeordnet

-   Zurodnung in einer Untergruppenebene

Teilbereich Icons

-   Liste über alle möglichen Icons

-   Es werden die zugeordneten verspeichert

-   Zugeordnet (c)

-   ICON Matchcode

Teilbereich Tags

Liste über

-   Tag Matchcode

-   Kann bei neuen Zeilen manuell eingegeben werden und löst damit
    > sofort einem eignene Bereich die Anzeige der mit (like Eingabe%
    > ermittelten WebShop Tags aus). Aus dieser Anzeige kann ein Tag
    > ausgewählt werden.

-   Wird ein Wert erfasst, der in den WebShop Tags nicht vorkommt und
    > der User hat die Berechtigung WebShop Tags anzulegen, so erfolgt
    > eine TE "<neuer Wert> als WebShopTag anlegen? ?/Ja/Nein".  
    > Es werden dabei die Texte für die Sprache "d" und alle WebShop
    > Sprachen mit dem eingegebenen Text erstellt. Die nicht Deutschen
    > Datensätze werden dabei als zu überarbeiten markiert.

-   Sichtbar (c)

#### Register "Produktinfo"

-   Windowsordner für Produktinformationen in "Office-Form"

-   Dokumente können geöffnet werden

-   Ordner "ArtikelProduktInfo" + [fa_nr] im Hauptordner von
    TradeControl

-   Unterordner je ArtikelNummer [artik_cd]

#### Auswahlpunkte im Menü "Extras" 

-   Änderung Artikel- bzw. Lagerführungskennzeichen

-   Artikelkennzeichen:

-   Änderung "p"

-   kein offener Produktionsauftrag

-   sonst beliebig änderbar

-   wird von "s" oder "p" auf nicht "s" oder "p" geändert

-   löschen Datensätze in artik_set

-   set_\*_kz werden auf "t" gesetzt

-   Lagerführungskennzeichen:

-   Änderung "k" "n", "c", "g"

-   beliebig änderbar

-   Änderung "n" "k", "g":

-   kein Datensatz in artik_lag_sub mit lag_mg <> 0 or aufs_frei_mg
    > <> 0

-   kein Datensatz in auf_pos mit erl_ein_auf_nr=0

-   Änderung "n" "c":

-   Eingabe der Chargennummer, der der Lagerstand zugeordnet werden
    > soll,

-   update artik_lag_sub

-   update auf_pos_sub

-   Änderung "c" "k", "n", "g":

-   kein Datensatz in artik_lag_sub mit lag_mg <> 0 or aufs_frei_mg
    > <> 0

-   kein Datensatz in auf_pos mit erl_ein_auf_nr=0

-   umsetzen ablaufdat_jn auf "n"

-   von "g" auf "k", "n", "c":

-   kein Datensatz in artik_lag_sub mit lag_mg <> 0 or aufs_frei_mg
    > <> 0

-   kein Datensatz in "geraet"

-   kein Datensatz in auf_pos mit erl_ein_auf_nr=0

-   wird auf "k" geändert:

-   löschen artik_lag_sub, artik_lag_ort, artik_lag

-   umsetzen duestrech_jn auf "n"

-   wird auf <> "k" geändert:

-   Ausgabe Hinweis: "Kennzeichen DuEst-Berechnung prüfen !"

#### Schaltflächen für Verzweigungen

-   ArtikelEinkauf

-   ArtikelLager

-   Auftragspositionen

-   Ausgangslieferscheinpositionen

-   Kassenbonposition

-   Bestellpositionen

-   Eingangslieferscheinpositionen

-   Produktionsauftrag

-   nur wenn Artikelkennzeichen = "p"

-   Lagerbewegungen

-   DUEST Entwicklung

-   Umsatzabfrage

-   Verbräuche

-   Verkaufskonditionen

-   Monatsumsatz

-   Geräte

-   nur wenn aktueller Artikel Geräteartikel ist

-   Verkaufspositionen

-   nur wenn Kassenmodul verfügbar

### ArtikelIdentifikationen 

#### Auswahldialog

-   Firma (f)

-   Artikelcode (f)

-   Kundencode (f)

-   Lieferantencode (f)

-   Identifikationsart (w)

-   Identifikationsnummer

#### Register "Liste"

-   Firma

-   Artikelcode

-   Artikelmatchcode

-   Kundenmatchcode

-   Lieferantenmatchcode

-   Identifikationsart

-   Menge

-   Identifikationsnummer

    **Anmerkung  
    **

-   Identifikationsarten "Matchcode" und "Artikelcode" werden nicht
    > gelesen

#### Register "Detail"

-   Firma

-   Identifikationsart (d)

-   Identifikationsarten "Matchcode" und "Artikelcode" nicht erlaubt

-   Artikelcode (f)

-   Artikelmatchcode (a)

-   Menge in kleinster Einheit

-   Eingabe nur dann, wenn Identifikationsart "EAN"

-   Identifikationsnummer

-   Vergeben (c)

-   Ist nur bei EAN, ausgefüllter BBN am Firmenstamm und leerer
    > Identifikationsnummer möglich

-   Wenn aktiviert wird beim Speichern eine neuen EAN-Nummer vergeben

-   Kundencode (f)

-   Kundenmatchcode (a)

-   Lieferantencode (f)

-   Lieferantenmatchcode (a)

Anmerkung

-   Die Neuanlage, das Ändern und das Löschen von
    Lieferantenartikelnummern wird auch in der Tabelle artik_lief
    durchgeführt

#### Schaltflächen für Verzweigungen

-   keine

### ArtikelEinkauf

#### Auswahldialog

-   Firma (f)

-   Artikelnummer (f)

-   Artikelmatchcode

-   Lieferantennummer (f)

-   Lieferantenmatchcode

-   Aktion (p)

-   Datum für Preisfindung (p)

-   Menge für Preisfindung (p)

-   Lieferanten Artikelnummer

#### Register "Liste"

-   Firma

-   Artikelnummer

-   Artikelmatchcode

-   Lieferantennummer

-   Lieferantenmatchcode

#### Register "Detail"

**Teilbereich "Artikel/Lieferant"  
**

-   Firma (f)

-   Artikelnummer (f)

-   Artikelmatchcode (a)

-   Lieferantennummer (f)

-   Lieferantenmatchcode (a)

-   Lieferantenwährung (a)

-   Einkaufseinheit (fd)

-   Vorschlag Neuanlage lt. Artikel, wenn nicht kopiert wird

-   Anzahl kleinste Einheiten in einer Einkaufseinheit

-   Vorschlag Neuanlage lt. Artikel, wenn nicht kopiert wird

-   Kleinste Einheit (a)

-   Einkaufspreis per Menge (d)

-   Vorschlag Neuanlage lt. Artikel, wenn nicht kopiert wird

-   Einkaufspreis per Einheit (d)

-   Vorschlag Neuanlage lt. Artikel, wenn nicht kopiert wird

-   Losgröße

-   Vorschlag Neuanlage lt. Artikel, wenn nicht kopiert wird

-   Einheit Losgröße (fd)

-   Vorschlag Neuanlage lt. Artikel, wenn nicht kopiert wird

-   Aufwertungsprozentsatz 1

-   Aufwertungsprozentsatz 2

-   Aufwertungsbetrag 1 (Stückzuschlag)

-   Aufwertungsbetrag 2 (Stückzuschlag)

-   Wiederbeschaffungszeit Bestellung (+/-)

-   Wochen

-   Eingabe bestimmt Tage

-   Tage

-   Eingabe bestimmt Wochen (immer aufgerundet)

-   Wiederbeschaffungszeit Bestellvorschlag

-   Wochen

-   Eingabe bestimmt Tage

-   Tage

-   Eingabe bestimmt Wochen (immer aufgerundet)

-   Mindestebestellmenge

-   Kennzeichen Mindestbestand (a)

-   Lagereinheit (a)

-   Mindestbestand in Lagereinheit

-   Kennzeichen Bestellvorschlag

-   Lieferantenartikelnummer

-   Vorschlag Neuanlage lt. Tabelle [artikid]

-   Preisartikelnummer (f)

-   wird bei der Neuanlage von Artikelnummer vorgeschlagen

-   wird bei Copy & Paste von kopiertem Artikel vorgeschlagen, wenn
    > CopyArtikelnummer <> CopyPreisartikelnummer

-   nach der Eingabe werden die Zeilen im Preisbereich gelöscht, und die
    > Preise vom Preisartikel eingefügt

-   Matchcode Preisartikel (a)

-   **Anmerkung**

Der Lieferant für Produktionsvorschlag lt. Firmenstamm darf bei der
Neuanlage nur bei einem Produktionsartikel verwendet werden.

Die Anlage, die Änderung und das Löschen der Lieferantenartikelnummer
wird auch in der Tabelle [artikid] durchgeführt, wird der
ArtikelLieferanten-Datensatz gelöscht, bleibt die
Lieferantenartikelnummer in der Tabelle [artikid] bestehen.

-   **Teilbereich "Artikel/Lieferant/Preise"**

    Bearbeitungsliste der Preise

-   Normalpreis/Aktion (d)

-   Datum gültig ab

-   Datum gültig bis

-   Eingabe nur bei Aktionen

-   ab Menge

-   Einkaufspreis

-   Währung (fd)

-   Rabatt 1

-   Rabatt 2

-   Naturalrabatt

    **Anmerkung**

    folgender Ablauf beim Speichern:

-   alle Artikel die den aktuellen Preisartikel eingetragen haben,
    werden aufsteigend nach Artikelnummer gelockt

-   speichern des aktuellen Preisfensters

-   löschen aller Preissätze der betroffenen Artikel

-   Neuanlage der Preissätze mit den Daten des aktuellen Preisfensters

#### Schaltflächen für Verzweigungen

-   keine

### ArtikelLager

#### Auswahldialog

-   Firma (f)

-   Artikelnummer (f)

-   Identifikationsnummer

-   Matchcode

-   Artikelkennzeichen (w)

-   Lagercode (fw)

-   Lagerkennzeichen (w)

-   Lagerstand

-   verfügbare Menge

-   verfügbare Menge für Freigabe

-   offene Auftragsmenge

-   freigegebene Auftragsmenge

-   Ablaufdatum

-   lt. Tabelle [artik_lag_sub]

**Anmerkung**

-   wird ein Suchkriterium der Tabelle [artik_lag_sub] ausgewählt, so
    > wird diese Tabelle dynamisch dazugejoint

#### Register "Liste"

-   Firma

-   Artikelnummer

-   Matchcode

-   Lagercode

-   Lagerstand

-   verfügbare Menge

-   verfügbare Menge für Freigabe

-   DuEst lt. [artik_lag]

-   Lagerwert (s)

-   Ablaufdatum

-   MIN(artik_lag_sub.ablauf_dat)

#### Register "Detail"

**  
**Teilbereich "ArtikelLager"**

-   Firma (f)

-   Artikelnummer (f)

-   Artikelmatchcode (a)

-   Lagercode (f)

-   Lagermatchcode (a)

-   Lagerstand (a)

-   verfügbare Menge (a)

-   verfügbare Menge für Freigabe (a)

-   Durchschnittlicher Einstandspreis

-   Eingabe nur, wenn DuEst-Rechnung **nicht** durchgeführt
    > wird und (die Lager unterschiedliche DuEst-Gruppen besitzen oder
    > es sich nicht um ein Eigenlager handelt)

-   Feld versteht sich in Lagereinheit

-   aktuelle Inventurnummer (a)

-   aktuelles Inventurdatum (a)

-   letzte Inventurnummer (a)

-   letztes Inventurdatum (a)

**Anmerkung zum Speichern**

-   wurde der DuEst eines Eigenlagers geändert, werden auch alle anderen
    Eigenlager-Sätze mit der selben DuEst-Gruppe mitgeändert

**Teilbereich "Lagerorte"**

Bearbeitungsliste der Lagerplätze

-   Lagerort

**Teilbereich "LagerSub"**

Anzeigeliste mit den Lagersubdaten
(Lagerplätzen/SeriennummernChargennummern/)

-   Lagerort

-   Charge/Gerätenummer

-   Lagerstand

-   freigegebene Menge

-   verfügbare Menge für Freigabe

-   Ablaufdatum

-   Einlagerungsdatum

#### Schaltflächen für Verzweigungen

-   Auftragspositionen

-   Lagerbewegungen

### Geräte

#### Auswahldialog

-   Firma (f)

-   Artikelnummer (f)

-   Gerätenummer

-   Kundennummer Standortkunde (f)

#### Register "Liste"

-   Firma

-   Artikelnummer

-   Matchcode

-   Gerätenummer

-   Zustand des Geräts

-   Kennzeichen Aufenthaltsadresse des Geräts

-   Aufenthaltsadressmatchcode

-   Standortkundennummer des Geräts

-   dazu Matchcode

#### Register "Detail"

**Teilbereich "Artikel"**

-   Firma

-   Artikelnummer (f)

-   Artikelkennzeichen "Normal" und "Divers" erlaubt

-   Artikelmatchcode (a)

-   Gerätenummer

-   Standortkundennummer (f)

-   Persondencode des Sachbearbeiters, welcher beim Standortkunden für
    das Gerät zuständig ist

-   Matchcode des Standortkunden (a)

-   Weitere Daten des Standortkunden (a)

-   Soweit Platz

-   Zustand des Geräts (d)

-   siehe Datenbankbeschreibung

-   Kennzeichen Aufenthaltsadresse des Geräts (d)

-   siehe Datenbankbeschreibung

-   Wird das Kennzeichen auf "externe Reparaturadresse" gesetzt, wird
    > die Aufenthaltsadresse des Geräts auf "unbestimmt" gesetzt und
    > muß vom Benutzer vor dem Speichern gesetzt werden

-   Datum der letzten Änderung der Aufenthaltsadresse

-   Aufenthaltsadresse des Geräts (f)

-   Eingabelogik wie im Kundenstamm

-   weitere Daten der Aufenthaltsadresse (a)

-   soweit Platz vorhanden

-   Einkaufspreis

-   bei der Neuanlage, Vorschlag lt. Artikel

-   Eingabe bei der Neuanlage bzw. mit Berechtigung "Einstandspreis"
    > auch im Änderungszweig

-   Einstandspreis

-   bei der Neuanlage, Vorschlag lt. Artikel

-   Eingabe bei der Neuanlage bzw. mit Berechtigung "Einstandspreis"
    > auch im Änderungszweig

-   Abgewerteter Einstandspreis

-   Datum der letzten Abwertung

-   interner Informationstext

-   nur wenn Gerät lagernd ist:

-   Lagercode (a)

-   Lagermatchcode (a)

-   Lagerort (a)

-   reserviert mittelsFreigabe (ac)

**Teilbereich "Freie Kennzeichen"**

siehe [Allgemeines](#kreditlimitprüfung)

**Teilbereich "Einkauf"**

-   nur vorhanden, wenn Gerät über den Warenzugang angelegt worden ist

-   Warenzugangsnummer (a)

-   Eingangslieferscheinnummer (af)

-   dazu Positionsnummer (af)

-   Daten dazu (a)

-   nur wenn Platz ist

-   Garantie- Ende- Datum Lieferant

-   Lieferantencode (a)

-   Lieferantenmatchcode (a)

**Teilbereich "Verkauf"**

-   nur vorhanden, wenn Gerät über Warenwirtschaft verkauft worden ist

-   Verkaufslieferscheinnummer (a)

-   Daten dazu (a)

-   nur wenn Platz ist

-   Eingangsauftragsnummer der Auftragsposition (af)

-   Positionsnummer in diesem Auftrag (af)

-   Garantieende- Datum Verkauf

-   dazu Kundennummer (af)

-   dazu Kundenmatchcode (a)

#### Schaltflächen für Verzweigungen

-   Serviceaufträge

-   Wartungsvertragspositionen

-   Artikel- Lager

### VerkaufsKonditionen

Ist das Verkaufskonditionsfenster vom Kundenfenster über die
Schaltfläche "Kopieren Konditionen" geöffnet, so befindet es sich im
"Kopiermodus". Im Kopiermodus ist Löschen, Neuanlage und Ändern nicht
möglich.

#### Auswahldialog

-   Firma

-   Konditionsart (fw)

-   Aktionskennzeichen (w)

-   Kunden bzw. Kundenkonditionsgruppe

-   Artikel bzw. Artikelkonditionsgruppe

-   Kundennummer (p)

-   0 = alle Kunden

-   Artikelnummer (p)

-   0 = alle Artikel

-   für die Preisanzeige im Register "Liste"

-   Preisliste (p)

-   Datum (p)

-   Menge (p)

#### Register "Liste"

-   Kopiervermerk (c)

-   wird bei neuer Auswahl mit "n" belegt

-   Eingabe nur im "Kopiermodus"

-   Firma

-   Konditionsart

-   Kundenzuordnungscode

-   Kundennummer für Preisfindung

-   Kundenverkaufskonditionsgruppe

-   leer

-   Kundenbezeichnung

-   Kundenmatchcode

-   Matchcode der Kundenkonditionsgruppe

-   leer

-   Artikelzuordnungscode

-   Artikelcode

-   Artikelverkaufskonditionsgruppe

-   leer

-   Artikelbezeichnung

-   Artikelmatchcode

-   Matchcode der Artikelkonditionsgruppe

-   leer

-   Preis

-   Rabatt 1-5

#### Register "Detail"

**Teilbereich "Konditionsart"**

-   Firma

-   Konditionsart (fd)

-   Kennzeichen Aktion (c) (a)

-   Kundencode (f)

-   Eingabe, wenn lt. Konditionsart vorgesehen

-   Kundenmatchcode (a)

-   Kundenkonditionsgruppe (fd)

-   Eingabe/Anzeige, wenn lt. Konditionsart vorgesehen

-   Artikelcode (f)

-   Eingabe, wenn lt. Konditionsart vorgesehen

-   Artikelmatchcode (a)

-   Artikelkonditionsgruppe (fd)

-   Eingabe/Anzeige, wenn lt. Konditionsart vorgesehen

-   Kunden-Artikelnummer

-   Wird bei einer Konditionsart mit Kundenzuordnung = Kundennummer und
    > Artikelzuordnung = Artikelnummer angezeigt und kann eingegeben
    > werden.

-   Muss beim Retrieve und bei der Neuerfassung nach Eingabe von Artikel
    > und Kunde aktualisiert werden.

-   Löst bei eine Änderung einen Insert order Update der artikid aus.

-   Wenn der Wert auf blank oder null geändert wird, so wird die
    > entsprechende artikid gelöscht.

**Teilbereich "Preise"**

Bearbeitungsliste mit den Preisen der Kondition

-   Preislistencode (fd)

-   Datum gültig ab

-   Datum gültig bis

-   Eingabe bei Aktionen

-   Menge gültig ab

-   Verkaufspreis

-   Rabatt 1-5

-   Naturalrabatt

#### Schaltflächen für Verzweigungen

-   keine

#### Auswahlpunkte im Menü "Extras"

-   Menüpunkte stehen nur im "Kopiermodus" zur Verfügung

-   alle Zeilen auswählen

-   hinzufügend kopieren

-   lt. Konditionsart

-   kopieren auf Kunde

-   kopieren auf Konditionsgruppe

-   ersetzend kopieren

-   lt. Konditionsart

-   kopieren auf Kunde

-   kopieren auf Konditionsgruppe

    **ad Kopieren**

-   zusätzlicher Entscheid "{ersetzend\|hinzufügend} Kopieren starten
    ?"

-   Ja

-   Nein

-   pro Zeile der Liste mit Kopiervermerk = "j"

-   ermitteln ob [vkkond] der Zielkondition bereits vorhanden ist

-   mit den veränderten Schlüsselfeldern, wie unten beschrieben

-   entsprechen die Schlüsselfelder der neuen Kondition der alten
    > Kondition (= Kopieren auf sich selbst) wird der Kopiervermerk auf
    > "n" gesetzt und nicht kopiert

-   nur bei "hinzufügend kopieren"

-   ermitteln ob in [vkkond_preis] gültige Kondition vorhanden ist,
    > wenn ja, wird Kopiervermerk auf "n" gesetzt und nicht kopiert

-   bis_dat >= Tagesdatum

-   löschen [vkkond_preis]

-   Neuanlage [vkkond] mit Kundendaten lt. Kundenfenster, wenn noch
    > nicht vorhanden

-   Neuanlage [vkkond_preis]

-   nur Konditionen mit bis_dat >= Tagesdatum

-   umsetzen Kopiervermerk auf "n"

-   Endemeldung des Kopiervorganges

**Anmerkung**

wenn zwischen Kundenkondition und Kundengruppenkondition gewechselt
wird, müssen folgende Felder in der Kondition neu bestimmt werden:

-   Verkaufskonditionsart

-   [vkkondart.kunde_zuord_kz = "g" oder "n",
    > vkkondart.artik_zuord_kz = {lt. aktueller Kondition}]

-   Kundenzuordnung

-   lt. ausgewählter Konditionsgruppe des aktuellen Kunden oder lt.
    > Preiskunde des aktuellen Kunden

### Wartungsverträge

#### Auswahldialog

-   Firma

-   Kundennummer (f)

-   Wartungsvertragnummer (f)

-   Erfassungsdatum

#### Register "Liste"

-   Firma

-   Wartungsvertragsnummer

-   Erfassungsdatum

-   Kundennummer

-   Matchcode

#### Register "Detail"

-   Firma

-   Sachbearbeiter (f)

-   Wartungsvertragsnummer

-   Wartungsvertragsdatum (a)

-   Kundennummer (f)

-   Debitorennummer (af)

-   Währungscode (a)

-   Kundenmatchcode (a)

-   weitere Kundendaten (a)

-   falls Platz vorhanden

-   Zuständiger Sachbearbeiter des Kunden (d)

-   Zahlungskonditionen

-   Vorschlag vom Debitoren bzw. von s_kund, wenn vorhanden

-   Wartungsvertragsdatum (a)

-   folgende Kennzeichen, bei der Neuanlage vorgeschlagen vom
    Kundenstamm

-   werden vom Servicekunden- Register vorgeschlagen, wenn dieses
    > gefüllt ist

-   Fakturenart (d)

-   Fakturenintervall (d)

-   Zahlungsart (fd)

-   Anzahl Rechnungen

-   Auftragsrabatt

-   Zolltarifnummer auf Faktura (c)

#### Register Ordner

-   Anlage / Anzeige eines Ordner

-   Ordner befindet sich parallel zu den Kundenordnern

-   Ordnername = "WV_" + Wartungsvertragsnummer

#### Register "Belegkette"

-   siehe unter Allgemeines Abfrageregister "Belegkette"

#### Schaltflächen für Verzweigungen

-   Wartungsvertragspositionen

#### Auswahlpunkte im Menü "Extras" 

-   Abrechnung

-   nächstes Abrechnungsdatum muss <= Tagesdatum sein

-   spoolt den Wartungsvertragsaufbaulauf für diesen Wartungsvertrag ein

### Wartungsvertragspositionen

#### Auswahldialog

-   Firma

-   Kundennummer (f)

-   Wartungsvertragnummer (f)

-   Wartungsvertragsposition (f)

-   Code des unter Wartung stehenden Artikels (f)

-   dazu Gerätenummer (f)

-   Datum Beginn Wartung

-   Datum Ende Wartung

-   Code des Wartungsleistungsartikels (f)

-   Datum der nächsten Verrechnung

#### Register "Liste"

-   Firma

-   Wartungsvertragsnummer

-   Kundennummer

-   Matchcode

-   Code des unter Wartung stehenden Artikels

-   dazu Matchcode

-   dazu Gerätenummer

-   Datum Beginn Wartung

-   Datum Ende Wartung

-   Code des Wartungsleistungsartikels

-   dazu Matchcode

-   Verkaufpreis

-   Rabatt 1

-   Rabatt 2

-   Datum der nächsten Verrechnung

#### Register "Detail"

**Teilbereich "Artikel"  
**

-   Firma

-   Wartungsvertragsnummer (f)

-   Kundennummer (a)

-   Kundenmatchcode (a)

-   Währungscode Wartungsvertrag (a)

-   Wartungsvertragsdatum (a)

-   Positionsnummer

-   wird, wenn leer oder 0 bei der Neuanlage beim Speichern vergeben

-   Ist das letzte Feld in der Eingabereihenfolge

-   Artikelnummer (f)

-   Eingabelogik wie bei Serviceauftrag

-   Artikelmatchcode (a)

-   Artikelinfotext (a)

-   Gerätenummer

-   Eingabelogik wie bei Serviceauftrag

-   Gerätedaten soweit Platz vorhanden ist (a)

-   Beginn- Datum Wartung

-   Ende- Datum Wartung

-   Abrechnungsperiodendauer in Monaten

-   Anzahl der bereits erfolgten Abrechnungsläufe (a)

-   Datum des nächsten Abrechnungslaufs

-   Wartungsvertragsleistungs- Artikel (f)

-   Eingabelogik wie bei Serviceauftrag

-   dazu Artikelmatchcode (a)

-   dazu Artikelinfotext (a)

-   Verkaufspreis

-   Verkaufsrabatt 1 u. 2

-   Positionsbetrag (a)

-   Gesamtbetrag Wartungsvertrag (a)

-   Infofeld

    **Teilbereich "Artikeltexte"**

-   Bearbeitungsliste mit den Artikeltextzeilen des
    Wartungsvertragsleistungsartikels. Die Zeilen werden bei der
    Neuanlage aus den Artikeltextzeilen vorgeschlagen.

-   Artikeltext

-   Fettdruck (c)

-   Unterstreichung (c)

    **Anmerkung**

Textbausteine können eingefügt werden.

#### Register "Belegkette"

-   siehe unter Allgemeines Abfrageregister "Belegkette"

### Massenwartung Artikel

Auswahldialog Standard

-   UNC-ImportOrdner (p)

#### Ablauf Allgemein

-   verarbeitet werden alle "\*.txt"-Files, die sich im Import-Ordner
    > befinden

-   dies sind Textfiles "Text mit TAB getrennt" aus Excel-File
    > exportiert

-   Verarbeitungsreihenfolge ist durch alphanumerische Sortierung nach
    > Filenamen aufsteigend definiert

-   Header-Zeile beinhaltet Column-Überschrift

-   1. Spalte beinhaltet immer den Datenbereich für den der Import
    > erfolgt

-   Wert der 1. Daten-Zeile bestimmt den Verarbeitungszweig

-   Datenbereich muss in allen Spalten den selben Wert beinhalten

-   ARTIKEL

-   ARTIKELEINKAUF

-   ARTIKELLAGER

-   ARTIKEL[PACKSTOFF]

-   ARTIKEL[SET]

-   ARTIKEL[ALTERNATIVEN]

-   ARTIKEL[ID]

-   ARTIKEL[FCOL]

-   ARTIKEL[FGR]

-   ARTIKEL[TEXT]

-   lesen Filenamen

-   pro File

-   lesen Header

-   lesen 1. Row

-   Verzweigen in Verarbeitungsfunktion des Datenbereichs

-   Ende pro Filename

-   File in "bu_ok" bzw. "bu_nok"-Verzeichnis verschieben (Filename
    > = [Jobnummer] + "_" + Originalfilename)

#### Ablauf Artikel

-   Datenbereich "ARTIKEL"

-   fixer Spaltenbereich am Zeilenbeginn, Überschrift nicht relevant

-   Datenbereich

-   Kennzeichen Neuanlage/Änderung

-   N Neuanlage

-   A Änderung

-   Firma

-   ArtikelNr

-   Spalte darf leer bleiben, wenn Neuanlage und ArtikelNr durch System
    > vergeben wird

-   Spalte muss bei der Änderung belegt sein

-   MusterArtikelNr

-   Spalte darf leer bleiben, wenn Änderung

-   Spalte muss bei der Neuanlage belegt sein

-   variabler Spaltenbereich Artikel, Überschrift relevant

-   Felder, die im Datenbereich "Detail" verwaltet werden

-   n Spalten

-   ColumnWert für DWO-Column lt. Überschrift

-   Variabler Spaltenbereich Schnellanlage ArtikelVerkaufPreise

-   wenn Spalte "VerkaufPreisListe" vorhanden ist, müssen alle
    > folgenden Spalten bis inkl "VerkaufRabatt5" vorhanden sein

-   VerkaufPreisListe

-   VerkaufGueltigAb

-   VerkaufPreis

-   VerkaufRabatt1

-   VerkaufRabatt2

-   VerkaufRabatt3

-   VerkaufRabatt4

-   VerkaufRabatt5

-   Variabler Spaltenbereich Schnellanlage ArtikelEinkauf

-   wenn Spalte "Lieferant" vorhanden, müssen beide Spatlen vorhanden
    > sein.

-   LieferantNr

-   LieferantArtikelNr

-   Artikel-ID -- EAN13, wenn angegeben wird eine ArtikelID mit dem EAN
    angelegt.

-   EAN13

-   Variabler Spaltenbereich Schnellanlage ArtikelEinkaufPreise

-   nur möglich, wenn Spalte "Lieferant" vorhanden ist

-   wenn Spalte "EinkaufGueltigAb" vorhanden ist, müssen alle
    > folgenden Spalten bis inkl "EinkaufRabatt5" vorhanden sein

-   EinkaufGueltigAb

-   EinkaufPreis

-   Waehrung

-   EinkaufRabatt1

-   EinkaufRabatt2

-   EinkaufRabatt3

-   EinkaufRabatt4

-   EinkaufRabatt5

Anmerkung:

-   alle Spaltenbereiche müssen in der beschriebenen Reihenfolge sein

-   öffnen Fenster Artikel

-   öffnen Fenster ArtikelEinkauf

-   pro Datenzeile UNC-File

-   Beginn Transaktion

-   lesen Werte des "fixen Datenbereichs"

-   Fehler "Datenbereich <> ARTIKEL", wenn Feldwert <> "ARTIKEL"

-   Fehler "Kennzeichen Neuanlage/Änderung ungültig" wenn Feldwert
    > nicht [NA]

-   Fehler "Musterartikel nicht bestimmt", wenn Neuanlage und Feld
    > leer

-   Fehler "Artikel nicht bestimmt", wenn Änderung und Feld leer

-   Neuanlage

-   Besorgen Musterartikel

-   Fehler "Neuanlage und Musterartikel nicht vorhanden"

-   Copy&Paste

-   Beginn Neuanlage mit Paste

-   Setzen Artikelnummer

-   nur, wenn Feld nicht protected

-   Änderung

-   Besorgen Artikel

-   Fehler "Änderung und Artikel nicht vorhanden"

-   Verarbeitung variabler Spaltenbereich

-   pro variabler Spalte

-   "idw_artik."+ColumnName = SpaltenWert

-   nur, wenn Feld nicht Protected

-   Fehler "Fehler beim Setzen von [ColumnName]: "+ErrorTxt, wenn
    > Setzen Feld mit Fehler

-   Speichern Artikel

-   Anmerkung pfu_fun: letzte Information sollte aus Instance ausgelesen
    > werden können

-   Fehler "Fehler beim Speichern Artikel"+ErrorTxt, wenn Speichern
    > mit Fehler

-   Verarbeitung variabler Spaltenbereich "ArtikelVerkaufPreise"

-   wenn Spalte "VerkaufPreisListe" vorhanden

-   Neuanlage: Löschen alle Zeilen im Register "VerkaufsPreis"

-   Änderung: löschen Zeilen mit GültigAb-Datum = VerkaufGueltigAb und
    > Preisliste = VerkaufPreisListe im Register "VerkaufsPreis"

-   Neuanlage Zeile

-   Setzen Fixwerte

-   AbMenge = 0

-   Setzen Felder

-   Preisliste = VerkaufPreisListe

-   VonDatum = VerkaufGueltigAb

-   Preis = VerkaufPreis

-   Rabatt1 = VerkaufRabatt1

-   Rabatt2 = VerkaufRabatt2

-   Rabatt3 =VerkaufRabatt3

-   Rabatt4 =VerkaufRabatt4

-   Rabatt5 =VerkaufRabatt5

-   Fehler "Fehler beim Setzen von [ColumnName] bei Verkaufspreise:
    > "+ErrorTxt, wenn Setzen Feld mit Fehler

-   Speichern Artikel

-   Fehler "Fehler beim Speichern Artikel Verkaufspreise"+ErrorTxt,
    > wenn Speichern mit Fehler

-   Verarbeitung variabler Spaltenbereich "ArtikelEinkauf"

-   wenn Spalte "LieferantNr" vorhanden

-   Fehler "Lieferant nicht bestimmt", wenn Feld leer

-   Spalte EAN13 bestimmt

-   bei Neuanlage Artikel: Löschen Zeilen mit EAN-13 aus Register
    > "ArtikelIdentifikationen"

-   bei Änderung Artikel: Neuanlage Zeile, wenn noch nicht vorhanden

-   Neuanlage Zeile

-   Art der ID = "e"

-   Lieferant = LieferantNr

-   Identifikationsnummer = EAN13

-   Menge = 1

-   Fehler "Fehler beim Setzen von [ColumnName] bei EAN13:
    > "+ErrorTxt, wenn Setzen Feld mit Fehler

-   Spalte LieferantArtikelNr ist bestimmt

-   löschen Zeilen mit LieferantenArtikelnummern des aktuellen
    > Lieferanten aus Register "ArtikelIdentifikationen"

-   Neuanlage Zeile

-   Art der ID = "l"

-   Lieferant = LieferantNr

-   Identifikationsnummer = LieferantArtikelNr

-   Fehler "Fehler beim Setzen von [ColumnName] bei
    > LieferantArtikelNr: "+ErrorTxt, wenn Setzen Feld mit Fehler

-   Speichern Artikel

-   Fehler "Fehler beim Speichern Artikel Identifikationen"+ErrorTxt,
    > wenn Speichern mit Fehler

-   Besorgen ArtikelLieferant

-   nicht vorhanden

-   Beginn Neuanlage

-   Setzen Felder

-   Artikel

-   Lieferant

-   Speichern ArtikelLieferant

-   Fehler "Fehler beim Speichern ArtikelLieferant "+ErrorTxt, wenn
    > Speichern mit Fehler

-   vorhanden

-   keine Aktion

-   Verarbeitung variabler Spaltenbereich "ArtikelEinkaufPreise"

-   wenn Spalte "EinkaufGueltigAb" vorhanden

-   Anmerkung: Fenster ArtikelLieferant hat den richtigen Datensatz im
    > Status Display angezeigt

-   löschen Zeilen mit GültigAb-Datum = EinkaufGueltigAb im Teilbereich
    > "ArtikelEinkaufPreise"

-   Neuanlage Zeile

-   Setzen Fixwerte

-   Preisart = Normal

-   AbMenge = 0

-   Setzen Felder

-   VonDatum = EinkaufGueltigAb

-   Preis = EinkaufPreis

-   Währung = Waehrung

-   Rabatt1 = EinkaufRabatt1

-   Rabatt2 = EinkaufRabatt2

-   Rabatt3 =EinkaufRabatt3

-   Rabatt4 =EinkaufRabatt4

-   Rabatt5 = EinkaufRabatt5

-   Fehler "Fehler beim Setzen von [ColumnName] bei Einkaufspreise:
    > "+ErrorTxt, wenn Setzen Feld mit Fehler

-   Speichern ArtikelLieferant

-   Fehler "Fehler beim Speichern ArtikelLieferant Einkaufspreise
    > "+ErrorTxt, wenn Speichern mit Fehler

-   Ende Transaktion

-   Reset Fenster Artikel

-   Reset Fenster ArtikelLieferant

-   Schließen Fenster

-   Ende Artikel

#### Ablauf ArtikelEinkauf

-   Datenbereich "ARTIKELEINKAUF"

-   Anmerkung: keine Preisverwaltung erfolgt über EinkaufspreisImport

-   fixer Spaltenbereich am Zeilenbeginn, Überschrift nicht relevant

-   Datenbereich

-   Kennzeichen Neuanlage/Änderung

-   N Neuanlage

-   A Änderung

-   Firma

-   ArtikelNr

-   LieferantNr

-   variabler Spaltenbereich ArtikelLieferant, Überschrift relevant

-   Felder, die im Datenbereich "Detail" oder "Erweiterung"
    > verwaltet werden

-   n Spalten

-   ColumnWert für DWO-Column lt. Überschrift

-   öffnen Fenster ArtikelLieferant

-   pro Datenzeile UNC-File

-   Beginn Transaktion

-   lesen Werte des "fixen Datenbereichs"

-   Fehler "Datenbereich <> ARTIKELEINKAUF", wenn Feldwert <>
    > "ARTIKELEINKAUF"

-   Fehler "Kennzeichen Neuanlage/Änderung ungültig" wenn Feldwert
    > nicht [NA]

-   Fehler "Lieferant nicht bestimmt", wenn Feld leer

-   Fehler "Artikel nicht bestimmt", wenn Feld leer

-   Neuanlage

-   Beginn Neuanlage

-   Setzen Firma

-   Setzen Lieferantennummer

-   Fehler "Fehler beim Setzen von [ColumnName]: "+ErrorTxt, wenn
    > Fehler

-   Setzen Artikelnummer

-   Fehler "Fehler beim Setzen von [ColumnName]: "+ErrorTxt, wenn
    > Fehler

-   Änderung

-   Besorgen ArtikelLieferant

-   Fehler "Änderung und Artikel/Lieferant nicht vorhanden"

-   Verarbeitung variabler Spaltenbereich

-   pro variabler Spalte

-   "idw_neu."+ColumnName = SpaltenWert

-   nur, wenn Feld nicht Protected

-   Fehler "Fehler beim Setzen von [ColumnName]: "+ErrorTxt, wenn
    > Setzen Feld mit Fehler

-   Speichern ArtikelLieferant

-   Fehler "Fehler beim Speichern Artikel/Lieferant"+ErrorTxt, wenn
    > Speichern mit Fehler

-   Ende Transaktion

-   Reset Fenster ArtikelLieferant

-   Schließen Fenster

-   Ende ArtikelLieferant

#### Ablauf ArtikelLagerPlatz

-   Datenbereich "ARTIKELLAGER"

-   Sortierung nach Firma, ArtikelNr, LagerNr ist relevant für
    Gruppenwechsel bei Verarbeitungsart "Ersetzen"

-   beim 1. Satz der Gruppe werden die bestehenden Daten gelöscht

-   beim letzten Satz endet die Transaktion

-   fixer Spaltenbereich am Zeilenbeginn, Überschrift nicht relevant

-   Datenbereich

-   Kennzeichen Ersetzen / Anhängen

-   E Ersetzen

-   A Anhängen

-   Firma

-   ArtikelNr

-   LagerNr

-   LagerOrt

-   öffnen Fenster ArtikelLager

-   pro Datenzeile UNC-File

-   lesen Werte des "fixen Datenbereichs"

-   Fehler "Datenbereich <> ARTIKELLAGER", wenn Feldwert <>
    > "ARTIKELLAGER"

-   Fehler "Kennzeichen Ersetzen / Anhängen ungültig" wenn Feldwert
    > nicht [EA]

-   Fehler "Lager nicht bestimmt", wenn Feld leer

-   Fehler "Artikel nicht bestimmt", wenn Feld leer

-   Gruppenstart

-   beim ersten Satz der Gruppe nach Firma/Artikel/Lager

-   Beginn Transaktion

-   Besorgen ArtikelLager

-   nicht gefunden

-   Beginn Neuanlage

-   Setzen Firma

-   Setzen Lager

-   Fehler "Fehler beim Setzen von [ColumnName]: "+ErrorTxt, wenn
    > Fehler

-   Setzen Artikelnummer

-   Fehler "Fehler beim Setzen von [ColumnName]: "+ErrorTxt, wenn
    > Fehler

-   gefunden

-   löschen Zeilen im Datenbereich idw_artik_lag_ort

-   nur wenn "Ersetzen"

-   Scroll zur Zeile

-   lag_ort = LagerOrt

-   nicht gefunden

-   Zeilenanlage

-   Feldsetzen

-   lag_ort = LagerOrt

-   sonst

-   keine Aktion

-   Gruppenabschluss

-   beim letzten Satz der Gruppe nach Firma/Artikel/Lager

-   Speichern ArtikelLager

-   Fehler "Fehler beim Speichern ArtikelLager"+ErrorTxt, wenn
    > Speichern mit Fehler

-   Ende Transaktion

-   Reset Fenster ArtikelLager

-   Schließen Fenster

-   Ende ArtikelLager

#### Ablauf Artikel, Packstoff

-   Datenbereich "ARTIKEL[PACKSTOFF]"

-   Sortierung nach Firma, ArtikelNr ist relevant für Gruppenwechsel bei
    Verarbeitungsart "Ersetzen"

-   beim 1. Satz der Gruppe werden die bestehenden Daten gelöscht

-   beim letzten Satz endet die Transaktion

-   fixer Spaltenbereich am Zeilenbeginn, Überschrift nicht relevant

-   Datenbereich

-   Kennzeichen Ersetzen / Anhängen

-   E Ersetzen

-   A Anhängen

-   L Löschen

-   Firma

-   ArtikelNr

-   PackstoffCd

-   variabler Spaltenbereich ArtikelPackstoffe, Überschrift relevant

-   Felder, die im Datenbereich "ArtikelPackstoffe" verwaltet werden

-   n Spalten

-   ColumnWert für DWO-Column lt. Überschrift

-   öffnen Fenster Artikel

-   pro Datenzeile UNC-File

-   lesen Werte des "fixen Datenbereichs"

-   Fehler "Datenbereich <> "ARTIKEL[PACKSTOFF]", wenn Feldwert
    > <> "ARTIKEL[PACKSTOFF]"

-   Fehler "Kennzeichen Ersetzen / Anhängen ungültig" wenn Feldwert
    > nicht [EA]

-   Fehler "Packstoff nicht bestimmt", wenn Feld leer

-   Fehler "Artikel nicht bestimmt", wenn Feld leer

-   Gruppenstart

-   beim ersten Satz der Gruppe nach Firma/Artikel

-   Beginn Transaktion

-   Besorgen Artikel

-   Fehler "Artikel nicht vorhanden"

-   löschen Zeilen im Datenbereich idw_artik_laenge

-   nur wenn "Ersetzen"

-   nur für Zeilen, die gelöscht werden dürfen [darfdeleteline]

-   Scroll zur Zeile

-   packst_cd = Packstoff

-   nicht gefunden

-   Zeilenanlage

-   Feldsetzen

-   packst_cd = Packstoff

-   sonst

-   keine Aktion

-   Verarbeitung variabler Spaltenbereich

-   pro variabler Spalte

-   "idw_artik_packst."+ColumnName = SpaltenWert

-   nur, wenn Feld nicht Protected

-   Fehler "Fehler beim Setzen von [ColumnName]: "+ErrorTxt, wenn
    > Setzen Feld mit Fehler

-   Gruppenabschluss

-   beim letzten Satz der Gruppe nach Firma/Artikel

-   Speichern Artikel

-   Fehler "Fehler beim Speichern Artikel, Packstoff"+ErrorTxt, wenn
    > Speichern mit Fehler

-   Ende Transaktion

-   Reset Fenster Artikel

-   Schließen Fenster

-   Ende Artikel, Packstoff

#### Ablauf Artikel, Set

-   Logik wie Packstoff, nur Auswahl angegeben

-   Datenbereich "ARTIKEL[SET]"

-   fixer Spaltenbereich am Zeilenbeginn, Überschrift nicht relevant

-   Datenbereich

-   Kennzeichen Ersetzen / Anhängen

-   E Ersetzen

-   A Anhängen

-   L Löschen

-   Firma

-   ArtikelNr

-   TeilArtikelNr

-   variabler Spaltenbereich ArtikelSetteile, Überschrift relevant

-   Felder, die im Datenbereich "idw_artik_set_pos" verwaltet werden

-   n Spalten

-   ColumnWert für DWO-Column lt. Überschrift

#### Ablauf Artikel, Alternativen

-   Logik wie Packstoff, nur Auswahl angegeben

-   Datenbereich "ARTIKEL[ALTERNATIVEN]"

-   fixer Spaltenbereich am Zeilenbeginn, Überschrift nicht relevant

-   Datenbereich

-   Kennzeichen Ersetzen / Anhängen

-   E Ersetzen

-   A Anhängen

-   L Löschen

-   Firma

-   ArtikelNr

-   AlternativeArtikelNr

-   variabler Spaltenbereich ArtikelAlternativen, Überschrift relevant

-   Felder, die im Datenbereich "idw_artik_altern" verwaltet werden

-   n Spalten

-   ColumnWert für DWO-Column lt. Überschrift

#### Ablauf Artikel, Identifikationen

-   Logik wie Packstoff, nur Auswahl angegeben

-   Datenbereich "ARTIKEL[ID]"

-   fixer Spaltenbereich am Zeilenbeginn, Überschrift nicht relevant

-   Datenbereich

-   Kennzeichen Ersetzen / Anhängen

-   E Ersetzen

-   A Anhängen

-   L Löschen

-   Firma

-   ArtikelNr

-   IdentifikationArt

-   IdentifikationNr

-   variabler Spaltenbereich ArtikelIdentifikationen, Überschrift
    > relevant

-   Felder, die im Datenbereich "idw_artikid" verwaltet werden

-   n Spalten

-   ColumnWert für DWO-Column lt. Überschrift

#### Ablauf Artikel, Freie Kennzeichen

-   Logik wie Packstoff, nur Auswahl angegeben

-   Datenbereich "ARTIKEL[FCOL]"

-   fixer Spaltenbereich am Zeilenbeginn, Überschrift nicht relevant

-   Datenbereich

-   Kennzeichen Ersetzen / Anhängen

-   E Ersetzen

-   A Anhängen

-   L Löschen

-   Firma

-   ArtikelNr

-   FColCd

-   variabler Spaltenbereich ArtikelIdentifikationen, Überschrift
    > relevant

-   Felder, die im Datenbereich "idw_artikid" verwaltet werden

-   n Spalten

-   ColumnWert für DWO-Column lt. Überschrift

#### Ablauf Artikel, Freie Gruppen

-   Logik wie Packstoff, nur Auswahl angegeben

-   Datenbereich "ARTIKEL[FGR]"

-   fixer Spaltenbereich am Zeilenbeginn, Überschrift nicht relevant

-   Datenbereich

-   Kennzeichen Ersetzen / Anhängen

-   E Ersetzen

-   A Anhängen

-   L Löschen

-   Firma

-   ArtikelNr

-   FGrCd

-   variabler Spaltenbereich ArtikelIdentifikationen, Überschrift
    > relevant

-   Felder, die im Datenbereich "idw_artikid" verwaltet werden

-   n Spalten

-   ColumnWert für DWO-Column lt. Überschrift

#### Ablauf Artikel, Text

-   Datenbereich "ARTIKEL[TEXT]"

-   Sortierung nach Firma, ArtikelNr ist relevant für Gruppenwechsel

-   es gibt nur die Verarbeitungsart "Ersetzen"

-   beim 1. Satz der Gruppe werden die bestehenden Daten gelöscht

-   beim letzten Satz endet die Transaktion

-   fixer Spaltenbereich am Zeilenbeginn, Überschrift nicht relevant

-   Datenbereich

-   Kennzeichen Ersetzen

-   E Ersetzen

-   Firma

-   ArtikelNr

-   variabler Spaltenbereich ArtikelText, Überschrift relevant

-   Felder, die im Datenbereich "Detail" oder "Erweiterung"
    > verwaltet werden

-   n Spalten

-   ColumnWert für DWO-Column lt. Überschrift

-   öffnen Fenster Artikel

-   pro Datenzeile UNC-File

-   lesen Werte des "fixen Datenbereichs"

-   Fehler "Datenbereich <> "ARTIKEL[TEXT]", wenn Feldwert <>
    > "ARTIKEL[TEXT]"

-   Fehler "Kennzeichen Ersetzen / Anhängen ungültig" wenn Feldwert
    > nicht "E"

-   Fehler "Artikel nicht bestimmt", wenn Feld leer

-   Gruppenstart

-   beim ersten Satz der Gruppe nach Firma/Artikel

-   Beginn Transaktion

-   Besorgen Artikel

-   Fehler "Artikel nicht vorhanden"

-   löschen Zeilen im Datenbereich idw_artik_txt

-   Zeilenanlage

-   Verarbeitung variabler Spaltenbereich

-   pro variabler Spalte

-   "idw_artik_txt."+ColumnName = SpaltenWert

-   nur, wenn Feld nicht Protected

-   Fehler "Fehler beim Setzen von [ColumnName]: "+ErrorTxt, wenn
    > Setzen Feld mit Fehler

-   Gruppenabschluss

-   beim letzten Satz der Gruppe nach Firma/Artikel

-   Speichern Artikel

-   Fehler "Fehler beim Speichern Artikel, Text"+ErrorTxt, wenn
    > Speichern mit Fehler

-   Ende Transaktion

-   Reset Fenster Artikel

-   Schließen Fenster

-   Ende Artikel, Text

### DDS-Referenznummer - EUDR

Auswahldialog

-   DDS-Referenznummer

-   Erfassungszeitpunkt

-   Ursprungs-KZ

Liste

-   DDS-Rererenznummer

-   DDS-Prüfnummer

-   Erfassungszeitpunkt

-   Erfassungs-Sachbearbeiter

-   Infotext

-   Ursprungs-KZ

Detail

-   DDS-Rererenznummer

-   DDS-Prüfnummer

-   Erfassungszeitpunkt (a)

-   Erfassungs-Sachbearbeiter (a)

-   Infotext

-   Ursprungs-KZ (d)

Buttons

-   Bestellungen

-   Eingangslieferscheine

-   Artikel

-   Verkaufslieferscheine

## Verkauf

### Auftrag

Allgemeines

Vollständig gelieferte Aufträge dürfen nicht mehr geändert werden.

#### Auswahldialog

-   Firma

-   Auftragsnummer (f)

-   Auftragsdatum

-   Auftragsart (fw)

-   Kundennummer (f)

-   Kundenmatchcode

-   Zustandskennzeichen (w)

-   Nicht im Servicemodus

-   Erledigungskennzeichen

-   erledigt

-   offen

-   Sachbearbeiterkennzeichen (f)

-   Artikelnummer des zu reparierenden Geräts (f)

-   nur im Servicemodus

-   [lt. Tabelle s_auf_geraet]

-   Gerätenummer des zu reparierenden Geräts (f)

-   nur im Servicemodus

-   [lt. Tabelle s_auf_geraet]

-   Zustand des Serviceauftrags (w)

-   nur im Servicemodus

-   Kundenbestellnummer

-   Kundenbestelldatum

-   nächstes Einsatzdatum

-   nur im Servicemodus

-   Techniker nächster Einsatz (w)

-   nur im Servicemodus

-   Text zum nächsten Einsatz

-   nur im Servicemodus

-   Verknüpfung zu Tabelle auf_prod wenn eines der folgenden Felder
    ausgefüllt

-   Produktionsartikelnummer (f)

-   offene Produktionsmenge

-   freigegebene Produktionsmenge

-   Auftragswert anzeigen j/n

-   im Standard mit Defaultwert "n" unsichtbar

Anmerkung

-   wird ein Feld der Tabelle [s_auf_geraet] ausgewählt, wird
    > zusätzlich in der Tabelle [s_auf_geraet] gesucht

#### Register "Liste"

-   Standardreihenfolge, individuelle Änderung der Spaltenreihenfolge
    > sowie -breite jederzeit möglich

-   WebdokFunktionalität

-   Firma

-   Filiale

-   Zustandskennzeichen

-   bei Service ist es das Serviceauftragszustandskennzeichen

-   Auftragsnummer

-   Auftragsart

-   Auftragsdatum

-   Kundennummer

-   Kundenmatchcode

-   nur bei Service:

-   Artikelnummer

-   Artikelmatchcode

-   Gerätenummer

-   Anzahl der zu reparierenden Artikel

-   Datum nächster Einsatz

-   Techniker nächster Einsatz

-   Nicht bei Service:

-   Lieferdatum

-   Lieferwoche

-   Sachbearbeiterkennzeichen

-   Kundenbestellnummer

-   Kundenbestelldatum

-   Rechnung (c)

-   Auftragswert (s)

-   nur wenn "Auftragswert anzeigen" lt. Query-parameter = "j"

-   im Standard im rechten Bereich

-   DB%

-   nur wenn "Auftragswert anzeigen" lt. Query-parameter = "j"

-   im Standard im rechten Bereich

-   Erfassungszeitpunkt

#### Register "Detail"

-   Firma

-   wird automatisch belegt, wenn nur ein Mandant vorhanden

-   keine Eingabe, wenn nur ein Mandant vorhanden

-   Kundennummer (f)

-   Eingabelogik Matchcode u. Nummer

-   Kunde muss aktiv sein

-   kann bei bestimmten Auftragsarten geändert werden

-   Hinweis "gegebenenfalls neue Preisfindung durchführen"

-   ggf. Anzeige Verkaufsinfo in eigenem Fenster

-   ist zur Eingabe im Vordergrund, wenn die Auftragsart nicht bestimmt,
    > oder <> Lieferantenretoure ist

-   Lieferantennummer (f)

-   Eingabelogik Matchcode u. Nummer

-   bestimmt Kundennummer

-   ist zur Eingabe im Vordergrund, wenn die Auftragsart
    > Lieferantenretoure ist

-   befindet sich an der selben Stelle wie die Kundennummer

-   Debitorennummer (a)

-   Währungscode Debitor (a)

-   Kundenmatchcode (a)

-   Auftragsart (fd)

-   wird die Auftragsart von einer Nicht- Service- Art bzw. von leer auf
    > eine Service- Art umgestellt:

-   Wird das Register Service initialisiert

-   Wird das Register Service angezeigt

-   wird die Auftragsart von einer Service- Art auf eine Nicht- Service-
    > Art umgestellt:

-   Wird das Register Service gelöscht

-   KundenLagerkennzeichen = "i"

-   "InterneUmbuchung"

-   "InterneUmbuchungRetoure"

-   ist bei Kundennummer = Kundennummer Produktion lt. Firmenstamm fix
    > definiert "Produktion

-   wird ein Serviceoffert übernommen, nur die erlaubten
    > Serviceauftragsarten

-   wird ein Verkaufsoffert übernommen, nur die erlaubten
    > Verkaufsauftragsarten

-   kann zwischen "Normalauftrag" und "Barverkauf" geändert werden

-   Kann von Normalauftrag auf Offert geändert werden, wenn der Zustand
    > Erfasst oder Rückstand ist und es noch keinen Lieferschein gibt.
    > Update beim Speichern siehe unten.

-   kann von "Reparaturannahme" auf alle anderen Serviceauftragsarten
    > geändert werden

-   Bei Änderung wird die UID-Nummernprüfung durchgeführt (siehe
    > aufart.uid_pruef_jn)

-   Lieferadresse

-   Vorschlag Neuanlage von Kunde

-   Kundeninfotext (a)

-   Bestellnummer

-   Bestelldatum

-   Vorschlag Neuanlage ist Tagesdatum

-   Auftragseingangsart (fd)

-   Versandart (fd)

-   Vorschlag Neuanlage von Kunde

-   Lieferbedingungen (fd)

-   Vorschlag Neuanlage von Kunde

-   Liefertermintext

-   Vorschlag für neue Positionen

-   Lieferdatum

-   Vorschlag für neue Positionen

-   Lieferwoche

-   Vorschlag für neue Positionen

-   Zahlungskonditionen

-   Vorschlag Neuanlage von Debitor

-   Bei Service von s_kunde, wenn vorhanden

-   Valutadatum

-   Kundenprovisionsgruppe (fd)

-   Vorschlag lt. Kunde

-   Auftragsnummer (a)

-   wird bei der Neuanlage beim Speichern vergeben

-   Filialnummer

-   wird automatisch belegt, wenn nur eine Filiale vorhanden

-   keine Eingabe bei Änderung, bzw. wenn nur eine Filiale vorhanden

-   Erfassungsdatum (a)

-   wird bei der Neuanlage vergeben

-   Sachbearbeitercode Erfassung (a)

-   wird bei Neuanlage vergeben

-   Zustandskennzeichen Auftrag (a)

-   erfasst

-   Kommissionsschein

-   Rückstand

-   vollständig geliefert

-   AB-Datum

-   Datum, an dem die Auftragsbestätigung erstellt (gedruckt, gefaxt
    > ...) wurde

-   Fakturenart (d)

-   Vorschlag Neuanlage von Debitor

-   Bei Service von s_kunde, wenn vorhanden

-   Fakturenintervall (d)

-   Vorschlag Neuanlage von Debitor

-   Bei Service von s_kunde, wenn vorhanden

-   Zahlungsart (fd)

-   Vorschlag Neuanlage von Debitor

-   Bei Service von s_kunde, wenn vorhanden

-   Wenn auf der Zahlungsart eine Kassen-Zahlungsart eingetragen ist
    > werden folgende Prüfungen druchgeführt:

    1.  ka_host für den aktuellen Rechnung muss vorhanden sein, diese
        Kassa muss auf Kassenabschluss im TC eingestellt sein.

    2.  Der Sachbearbeiter lt. Auftragskopf muss in ka_sb vorhanden sein

-   (Zahlungsart) Fix (c)

-   Wird bei manueller Eingabe der Zahlungsarte auf j gesetzt

-   Wenn aktiviert passiert kein neuer Vorschlag der Zahlungsart bei
    > Änderung von Versandart oder Auftragsart

-   Anzahl Lieferscheine

-   Vorschlag Neuanlage von Debitor

-   Bei Service von s_kunde, wenn vorhanden

-   Anzahl Rechnungen

-   Vorschlag Neuanlage von Debitor

-   Bei Service von s_kunde, wenn vorhanden

-   Auftragsrabatt

-   folgende Kennzeichen, bei der Neuanlage vorgeschlagen vom
    Kundenstamm

-   Bei Serviceaufträgen werden diese vom Servicekunden- Register
    > vorgeschlagen, wenn dieses gefüllt ist

-   Lieferschein hat Preis (c)

-   Soloauftrag (c)

-   Auftragsfreigabe (c)

-   Vorschlag Neuanlage ist "angehakt"

-   Offert mit Endsumme drucken (c)

-   Rückstandsverwaltung (c)

-   Rückstandsausweis (c)

-   Zolltarifnummer auf Faktura (c)

-   Teillieferungen erlaubt (c)

-   Musteroffert (c)

-   Eingabe nur bei Offerten

-   setzt Offert auf "unerledigt"

-   Kommissionsablaufdatum

-   nur bei Auftragsart "k"

-   Handlieferscheinnummer und --datum

-   nur bei Auftragsart "h"

    **Anmerkung**

-   Sind Positionen von Aufträgen im Rückstand in den aktuellen Auftrag
    zu übernehmen, wird bei der Neuanlage nach dem Speichern automatisch
    auf den Register "RückstandsÜbernahme" umgeschaltet

-   Abhängig von der Auftragsart, sind manche Felder inaktiv und/oder
    mit fixen Werten belegt siehe Datenbankbeschreibung

-   Wird ein Auftrag gelöscht, so werden zuvor die Positionen mit
    gelieferter Menge = 0 gelöscht. Es muss dabei eine Transaktion pro
    Position gemacht werden.

Änderung Auftragsart von Normal auf Offert

Folgende Updates müssen in diesem Fall nach dem Speichern des
Aufragskopfes erfolgen (innerhalb der Haupt-Transaktion):

-   Nochmal Prüfen ob nicht bereits ein Lieferschein vorhanden ist und
    keine Positionen in anderen Abwicklungsaufträge übernommeh wurden
    bzw. keine Positionen von anderen Aufträgen in diesen
    Abwicklungsauftrag übernommen wurden.

-   Locken aller Artikel aus den Auftragspositionen

-   Pro Position

-   Rausrechnen von offenen Auftragswerten am Debitor

-   Rausrechnen von reservierten Mengen

-   Freigegebene Menge auf 0 setzen, auf_pos_sub Daten löschen

Drag+Drop

-   Wird ein PDF auf den Auftragskopf gedroped, so wird dieses in die
    Dokumente mit Ausdrucksart "auf_dok" und der Auftragsnummer als
    Belegnummer verspeichert.

#### Register "Service"

-   Anmerkung intern: DW bezieht sich auf die Tabelle s_auf

-   nur bei Service- Auftragsarten sichtbar

**Teilbereich "Serviceauftrag"**

-   Firma

-   Kundennummer (f)

-   Eingabelogik Matchcode u. Nummer

-   Kunde muss aktiv sein

-   kann bei bestimmten Auftragsarten geändert werden

-   Hinweis "gegebenenfalls neue Preisfindung durchführen"

-   Kundenmatchcode (a)

-   Kundeninfotext (a)

-   weitere Kundendaten soweit Platz vorhanden ist (a)

-   Artikelnummer (f)

-   Eingabelogik Nummer, Matchcode u. Identifikationen

-   Änderung nur möglich, wenn es keine Position mit wv_nr > 0 gibt.

-   Artikelmatchcode (a)

-   Gewicht (a)

-   Gerätenummer

-   Eingabelogik wie bei Artikelnummer und zusätzlich gilt:

-   Ist die Kundennummer ausgefüllt, wird sie bei der Auswahl
    > berücksichtigt

-   Ist die Artikelnummer ausgefüllt, wird sie bei der Auswahl
    > berücksichtigt

-   Die Auswahl bestimmt Artikelnummer und Gerätenummer

-   Änderung nur mögliche, wenn es keine Position mit wv_nr > 0 gibt.

-   kann leer sein

-   siehe auch Datenbank Tabelle s_auf

-   Artikelinfotext (a)

-   Geräteidentifikation zum Drucken auf den Belegen

-   nur eingebbar, wenn die Gerätenummer leer ist, sonst = Gerätenummer

-   Gerätedaten soweit Platz vorhanden ist (a)

-   Anzahl der zu reparierenden Artikel

-   ist fix 1, wenn die Gerätenummer ausgefüllt ist

-   Auftragsart (fd)

-   es sind nur Service- Auftragsarten erlaubt und es werden nur diese
    > vorgeschlagen

-   Bestellnummer

-   versteht sich bei Serviceoffert als Anfragenummer

-   Bestelldatum

-   Vorschlag Neuanlage ist Tagesdatum

-   versteht sich bei Serviceoffert als Anfragedatum

-   Evidenzdatum (=Lieferdatum)

-   Vorschlag Neuanlage ist Tagesdatum

-   für Evidenzierung von Kostenvoranschlag und Fremdreparatur

-   Auftragseingangsart (fd)

-   Auftragsnummer (a)

-   wird bei der Neuanlage beim Speichern vergeben

-   Erfassungsdatum (a)

-   wird bei der Neuanlage vergeben

-   Sachbearbeitercode Erfassung (a)

-   wird bei Neuanlage vergeben

-   Zustandskennzeichen Service- Auftrag (a)

-   erfaßt

-   zur Bearbeitung eingeteilt

-   neuerlicher Einsatz notwendig

-   zur neuerlichen Bearbeitung eingeteilt

-   abgeschlossen

-   Für den nächsten Arbeitsberichtsaufbau:

-   Kennzeichen Arbeitsbericht- Aufbau:

-   Keinen Arbeitsbericht aufbauen (es wird Blanko- Bericht gedruckt)

-   Vorschlag bei der Neuanlage

-   bei "Serviceoffert" und "Reparaturannahme" keine weitere Auswahl
    > möglich

-   Arbeitsbericht aufbauen und Auftrag auf abgeschlossen setzen

-   Arbeitsbericht aufbauen und Auftrag auf abgeschlossen setzen und
    > dabei Gerät ausscheiden

-   Arbeitsbericht aufbauen und Auftrag auf "Neuerlicher Einsatz
    > notwendig" setzen

-   Handlieferscheinnummer und --datum

-   nur bei den entsprechenden Auftragsarten (siehe Datenbank)

-   Anzahl Arbeitsberichte

-   Versandart (fd)

-   Lieferbedingung (fd)

-   Für den nächsten Einsatz:

-   Datum

-   Techniker (d)

-   Text

-   Datum

-   Techniker (d)

    **Teilbereich "Geräte"**

-   nur sichtbar, wenn [pfu_param.svc_mehrere_geraete_pro_auftrag_jn]
    = "j"

-   die Zeile, die das idente Gerät wie im Teilbereich
    "Serviceauftrag" beinhaltet, darf nicht gelöscht werden

-   Änderungen in der zeile, die das idente Gerät wie im Teilbereich
    "Serviceauftrag" beinhaltet, werden automatisch mit dem
    Teilbereich „Serviceauftrag" synchronisiert

-   Artikelnummer (f)

-   Eingabelogik Nummer, Matchcode u. Identifikationen

-   Änderung nur möglich, wenn es keine Position mit wv_nr > 0 gibt.

-   Vorschlag lt. obiger Zeile

-   Artikelmatchcode (a)

-   Gewicht (a)

-   Gerätenummer

-   Eingabelogik wie bei Artikelnummer und zusätzlich gilt:

-   Ist die Kundennummer ausgefüllt, wird sie bei der Auswahl
    > berücksichtigt

-   Ist die Artikelnummer ausgefüllt, wird sie bei der Auswahl
    > berücksichtigt

-   Die Auswahl bestimmt Artikelnummer und Gerätenummer

-   Änderung nur möglich, wenn es keine Position mit wv_nr > 0 gibt.

-   kann leer sein

-   siehe auch Datenbank Tabelle s_auf

-   Artikelinfotext (a)

-   Geräteidentifikation zum Drucken auf den Belegen

-   nur eingebbar, wenn die Gerätenummer leer ist, sonst = Gerätenummer

-   Gerätedaten soweit Platz vorhanden ist (a)

-   ident zu Teilbereich "Serviceauftrag"

-   Anzahl der zu reparierenden Artikel

-   ist fix 1, wenn die Gerätenummer ausgefüllt ist

#### Register "Debitor"

-   Debitorennummer (f)

-   Darf nur geändert werden, wenn ident mit OP-Debitorennummer diese
    > wird dann mitgeändert

-   bei Änderung werden Zahlungskonditionen aktualisiert

-   Bei Änderung wird die UID-Nummernprüfung durchgeführt (siehe
    > aufart.uid_pruef_jn)

-   Währung muss bei Änderung mit der Auftragswährung übereinstimmen

-   Rechnungsadresse manuell (c)

-   Kann nur bei einem diversen Debitor aktiviert werden

-   Rechnungsadresse

-   Vorschlag lt. Debitor, bei einem diversen Debitor wird die
    > Lieferadresse vorgeschlagen

-   ändert sich auch durch Eingabe der Lieferadresse bei diversen
    > Debitor solange Rechnungsadresse manuell nicht aktiviert ist.

-   Rechnungsversand (d)

-   bei vrechausart.vrech_druck_kz = „b" muss UID-Nummer und
    > Fremdkontonummer vorhanden sein

-   bei vrechausart.vrech_druck_kz = „e" muss E-Mailadresse am
    > Debitorenstamm vorhanden sein

-   E-Mail Adresse für den Rechnungsversand

-   E-Mail fix (c)

-   Wird gesetzt, wenn die E-Mail Adresse manuell eingegeben wird. In
    > diesem Fall wird der Auftrag aus Solo gestellt.

-   Wenn dektiviert wird wieder die E-Mail Adresse lt. Debitor
    > übernommen

-   Kombination E-Mail Fix = "j" mit vkrech_kz in (d, k, ka) nicht
    > möglich -- Fehlermeldung erfolgt beim Speichern.

-   Ust-ID (a)

-   lt. OP-Debitor

-   Kreditlimit (a)

-   Saldo Buchhaltung (a)

-   offener Auftragswert (a)

-   freier Auftragswert (a)

-   offener Lieferscheinwert (a)

-   Wechselobligo (a)

-   Saldo fällig (a)

-   offenes Limit (a)

-   siehe Allgemeines

-   maximale Mahnstufe (a)

    **Anmerkung**

    wird gemeinsam mit Register "Detail" gespeichert

    Ist das offene Limit überschritten, wird bei der Auftragsneuanlage
    automatisch in diesen Register verzweigt.

#### Register "KommDaten"

-   Kommunikationsart Kunde (fd)

-   Kommunikationsnummer Kunde (a)

-   Sachbearbeiter Kunde (fd)

-   Name SB (a)

-   ZuHanden-Feld

-   wird bei der Sachbearbeiterauswahl automatisch zusammengestellt

-   Kommunikationsart Sachbearbeiter (fd)

-   Kommunikationsnummer Sachbearbeiter (a)

-   Druckkennzeichen (d)

-   nur wenn Druckkennzeichen Fax oder E-Mail ausgewählt:

-   Kommunikationsarten und -nummern des Sachbearbeiters und des Kunden,
    > welche der ausgewählten Kommunikationsart entsprechen (d)

-   Kommunikationsart (a)

-   Kommunikationsnummer

-   Lieferung TelNr Auswahl (d)

-   Es werden alle Telefon und Mobiltelefon Komunikationsarten des
    > Kunden aller seiner Personen angezeigt. Es sind in der DDDW Liste
    > die Person (Titel Vorname Nachname) und die Telefonnummer zu
    > sehen.

-   Lieferung TelNr

-   Nach Eingabe der Kundennummer wird hier die Standard Verkaufs
    > Telefonnummer/Mobiltelefonnumer des Kunden (bzw. seiner Personen
    > vorgeschlagen)

    **Anmerkung**

1.  wird gemeinsam mit Register "Detail" gespeichert

2.  folgende Eingabereihenfolge mit TAB:

    a.  Sachbearbeiter Kunde

    b.  ZuHanden-Feld

    c.  Druckkennzeichen

    d.  Kommunikationsarten SB und Kunde

#### Register "Text"

Bearbeitungsliste mit den Anfangs- bzw. Endtexten des Auftrages

-   Textstelle (d)

-   Beleganfang

-   Belegende

-   Text

-   Fettdruck (c)

-   Unterstreichung (c)  
    Belegtypen auf welchen der Text gedruckt werden soll

-   Auftragsbestätigung (c)

-   Kommissionsschein (c)

-   Lieferschein (c)

-   Rechnung (c)

-   Offert (c)

    **Anmerkung**

 Textbausteine können eingefügt werden

#### Register "Service- Text"

-   Nur bei Service- Auftragsarten sichtbar

    **Teilbereich "Auftragstexte"**

    Bearbeitungsliste mit den Anfangs- bzw. Endtexten des Service-
    Auftrages

-   Textstelle (d)

-   Fehlerbeschreibungstext

-   Kostenvoranschlagsanfangstext

-   Kostenvoranschlagsendtext

-   Arbeitsberichtanfangstext für den aufzubauenden Arbeitsbericht

-   Arbeitsberichtendtext für den aufzubauenden Arbeitsbericht

-   Anfangsext für den Verbringungsbeleg für das Gerät

-   Endtext für den Verbringungsbeleg für das Gerät

-   interner Text

-   Text

-   Fettdruck (c)

-   Unterstreichung (c)

-   Kennzeichen Text auf Rechnung Drucken (c)

-   nur bei Fehlertext und Arbeitsberichtstexten eingebbar, sonst nein

    **Anmerkung**

 Textbausteine können eingefügt werden

**Teilbereich "Lieferscheintexte"**

Anzeigeliste mit den Anfangs- bzw. Endtexten der dem Auftrag
zugeordneten Lieferscheine

-   Lieferscheinnummer

-   Textstelle

-   Text

-   Fettdruck (c)

-   Unterstreichung (c)

-   Kennzeichen Text auf Rechnung Drucken (c)

#### Register "KS"

Bearbeitungsliste mit den aktuellen Kommissionsscheinen des Auftrages

-   Kommissionsscheinnummer (a)

-   Datum (a)

-   Kommissionsbereich (a)

-   Freigabe zum Lieferschein (c)

-   MDE Status (a)

-   Größter Status aus kommvorg_bereich lt. kommvorg_auf

Wenn eine Zeile gelöscht wird, wird geprüft ob es einen zugeordneten
Kommissionsvorgang gibt.

Hat dieser einen Bereich mit einem Status > "1" so erfolgt ein TE:

Achtung Kommissionierung ist bereits in Status <Status Text>! Trotzdem
löschen? Nein/Ja"

Bei Ja oder Status 1 werden damit auch alle kommvorg Daten gelöscht.

#### Register "SammelLfs"

Bearbeitungsliste mit den aktuellen Kommissionsscheinen des Kunden

-   Auftragsnummer (a)

-   Kommissionsscheinnummer (a)

-   Datum (a)

-   Freigabe zum Lieferschein (ac)

-   übernehmen in aktuellen Auftrag (c)

    **Anmerkung**

Die "angehakten" Kommissionsscheine werden zur Abwicklung in den
aktuellen Auftrag übernommen. Ist der aktuelle Auftrag im Zustand
"Kommissionsschein", werden die Positionen dem höchsten
Kommissionsschein zugeordnet, ansonsten wird der Kommissionschein 1
angelegt und der Auftrag in den Zustand Kommissionschein versetzt. Sind
in einem Auftrag eines angehakten Kommissions-scheins offene
Auftragspositionen ohne Kommissionsscheinzugehörigkeit vorhanden, werden
diese ebenfalls in den aktuellen Auftrag übernommen. Diese Positionen
werden keinem Kommissionschein zugeordnet.Verbleiben im Eingangsauftrag
keine Abwicklungspositionen, so wird dieser auf erledigt gesetzt.

#### Register "Rückstände"

**Teilbereich "Auftrag"**

Bearbeitungsliste mit den Rückständen des Kunden, dies sind

-   Offerte

-   eine Zeile pro Offert

-   Verkaufs- bzw. Serviceofferte abhängig von der aktuellen Auftragsart

-   Abrufaufträge

-   nicht wenn aktueller Auftrag Service

-   eine Zeile pro Abrufauftrag

-   die Abrufgruppe des Kunden wird bei der Auswahl berücksichtigt

-   Auftragsrückstände

-   nicht wenn aktueller Auftrag Service

-   eine Zeile für alle Rückstände

-   Kennzeichen Auftrag wird übernommen (c)

-   Feld wird bei Rückständen abhängig von Verarbeitungskennzeichen im
    > Firmenstamm vorbelegt

-   Abrufer sind nie automatisch für die Übernahme markiert

-   nur das zur Übernahme ausgewählte Offert ist für die Übernahme
    > markiert

-   belegt für alle Positionen das Übernahmekennzeichen

-   Fixtext

-   "Offert"

-   "Abrufer"

-   "Auftragsrückstand"

-   nur für Offerte und Abrufaufträge

-   Auftragsnummer (a)

-   Auftragsdatum (a)

-   Kundenbestellnummer (a)

-   Kundenbestelldatum (a)

-   Lieferdatum (a)

-   Lieferwoche (a)

-   Kundenname 1 (a)

-   Artikelnummer

-   Seriennummer

    **Anmerkung**

    Die Daten werden bei der Auftragsneuanlage nach Eingabe des Kunden
    eingelesen. Abhängig von der Einstellung im Firmenstamm werden
    Offerte, Abrufaufträge und/oder Rückstände eingelesen.

    Befindet sich das Programm im Modus "Offertübernahme" werden nur
    Offerte angezeigt, das angewählte Offert ist zur Übernahme markiert.
    Werden lt. Firmenstammeinstellung keine Offerte im Rückstandsfenster
    angezeigt, befinden sich keine weiteren Offerte in der Anzeige.

    Musterofferte werden nur im Modus "Offertübernahme" angezeigt.

**Teilbereich "Auftragspositionen"**

Bearbeitungsliste mit den offenen Auftragspositionen des Kunden, bei
Offerten und Abrufaufträgen werden nur die Positionen des markierten
Auftrages, bei Rückständen alle Positionen angezeigt.

-   Kennzeichen Position wird übernommen (c)

-   Feld wird abhängig von Verarbeitungskennzeichen im Firmenstamm
    > vorbelegt

-   belegt Auftragsmenge mit offener Menge bzw. mit 0

-   Auftragsnummer (a)

-   Positionsnummer (a)

-   Auftragsdatum (a)

-   Artikelnummer (a)

-   Artikelmatchcode (a)

-   Lagercode (a)

-   frei verfügbare Menge (a)

-   offene Menge (a)

-   Auftragsmenge

-   Eingabe nur bei Offert- und Abrufpositionen (maximal offene Menge)

-   ist bei Auftragsrückständen entweder 0 oder gleich mit der offenen
    > Menge

-   belegt, wenn 0 Kennzeichen Positionsübernahme mit "n"

-   Erledigungskennzeichen (c)

-   kann bei Abrufern und Offerten eingegeben werden, wenn Auftragsmenge
    > < offener Menge

-   Position wird nach Übernahme "erledigt" gesetzt

-   Lieferdatum (a)

-   Lieferwoche (a)

-   Verkaufspreis (a)

-   Rabatt 1 und 2 (a)

    **Anmerkung**

Wird eine Setposition (Sub- oder Hauptposition) verändert, werden alle
zugehörigen Positionen ebenfalls verändert.

Der Register wird bei Eingabe von Kundennummer oder Solokennzeichen
befüllt oder gelöscht. Als Auftrags-rückstände werden nur unerledigte
Auftragspositionen ohne Kommissionsscheinnummer von Aufträgen mit
SoloKennzeichen="n" angezeigt.

Rückstände:

Die ausgewählten Auftragspositionen werden zur Abwicklung in den
aktuellen Auftrag übernommen. Die Positionen sind, sofern verfügbar,
freigegeben zum Lieferschein. Verbleiben im Eingangsauftrag keine
Abwicklungspositionen, so wird dieser auf erledigt gesetzt.

Offerte, Abrufaufträge:

Die ausgewählten Auftragspositionen werden neue Auftragspositionen im
aktuellen Auftrag. Ist das Erledigungskennzeichen gesetzt, wird die
Abruf- bzw. Offertposition im Anschluss an die Übernahme auf erledigt
gesetzt

#### Register "Produktion"

**Teilbereich "Produktionsartikel"**

-   Artikelnummer (f)

-   Eingabelogik Nummer, Matchcode und Identifikation

-   Artikel muss aktiv sein

-   darf kein Auslaufartikel sein

-   Artikelart muss "p" sein

-   Artikelmatchode (a)

-   Lagerkennzeichen (a)

-   Artikelinfotext (a)

-   Lagernummer (fd)

-   Vorschlag lt. Firmenstamm

-   Lagerkennzeichen muss "e" sein

-   keine Eingabe, wenn gespeicherte freigegebene Produktionsmenge <>0
    > ist

-   offene Produktionsmenge

-   verändert bei Eingabe bestellte Menge

-   ist vorzeichengleich zu bestellter Menge

-   bestellte Menge darf nicht 0 sein

-   freigegebene Produktionsmenge

-   maximal offene Menge

-   Meldung wenn "frei verfügbare Menge Teile" überschritten

-   darf abhängig von Kennzeichen im Firmenstamm, "frei verfügbare
    > Menge Teile" nicht übersteigen

-   darf, wenn < 0 "frei verfügbare Menge Produktionsartikel" nicht
    > übersteigen

-   Vorschlag ist das Minimum aus offener Menge und verfügbarer Menge
    > bzw. 0, wenn das Freigabekennzeichen des Auftrages "n" ist

-   abhängig von Kennzeichen Freigabe Produktionsauftrag
    > [fa.auf_prod_frei_kz]:

-   Gemeinsame Freigabe

-   bestimmt, wenn <> 0 auch die Freigabemenge der Teile

-   Vorschlag Abgang

-   Freigabemenge der Teile werden vorgeschlagen

-   unabhängige Freigabe

-   Freigabemengen der Teile werden nicht verändert

-   Verkaufsmengeneinheit (a)

-   bestellte Menge (a)

-   produzierte Menge (a)

-   gelöschte Menge (a)

-   für das aktuelle Lager des Produktionsartikels

-   Lagerstand (a)

-   verfügbarer Lagerstand (a)

-   wird durch negative offene Produktionsmenge vermindert

-   für Freigabe verfügbare Menge (a)

-   wird durch negative freigegebene Produktionsmenge vermindert

-   bestellte Menge Lieferant + offene Produktionsmenge

-   für die aktuellen Lager der Teile

-   Minimum Lagerstand (a)

-   Minimum verfügbarer Lagerstand Teile (a)

-   wird durch positive offene Menge Teile vermindert

-   Minimum frei verfügbarer Lagerstand Teile (a)

-   wird durch positive freigegebene Menge Teile vermindert

-   Rückstandsverwaltung (c)

-   ist gekoppelt mit dem gleichnamigen Feld im Detail- Eingabebereich

-   ist für nachfolgend beschriebenen Ablauf auch hier einzugeben:

-   Kennzeichen wird vom Produktionskunden mit \'j\' vorgeschlagen

-   es erfolgen Teilfreigaben und die zugehörigen VLFS- Aufbauläufe

-   beim letzten Freigeben (also wenn die Produktion nach dem VLFS-
    > Aufbau abgeschlossen sein soll) wird das Kennzeichen auf \'n\'
    > umgesetzt und der VLFS- Aufbau gestartet

-   der VLFS- Aufbau setzt jetzt für den Produzierten Artikel und die
    > Bestandteile durch entsprechendes Setzen der gelöschten Menge die
    > offene Menge auf 0

-   Auftragsnummer

-   0 = Produktion ohne Bezug auf Auftrag

-   Auftragspositionsnummer

-   0 = Produktion ohne Bezug auf Auftrag

-   ist der Produktionsartikel bereits bestimmt, muss die
    > Auftragsposition den selben Artikel haben

-   durch Eingabe der Positionsnummer werden folgende Felder lt.
    > Auftragsposition bestimmt:

-   Artikelnummer

-   offene Produktionsmenge

-   lt. offener Auftragsmenge

    **Anmerkung**

Wird gemeinsam mit "Detail" gespeichert, darf bei Auftragsart "p"
nicht unbestimmt bleiben

**Teilbereich "Lager"**

Bearbeitungsliste mit der Lageraufteilung der Produktion

-   Listbox Lagerbestände (d)

-   aktiv, wenn Lagerstand auf Lagerortebene geführt wird

-   definiert Lagerort und/oder Chargen- bzw. Gerätenummer

-   folgende Felder im Auswahlfenster:

-   Lagerort

-   Chargen- bzw. Gerätenummer

-   verfügbarer Lagerbestand

-   Ablaufdatum

-   Einlagerungsdatum

-   Listbox Lagerorte (d)

-   aktiv, wenn Lagerstand auf Lagerortebene geführt wird

-   definiert Lagerort

-   folgende Felder im Auswahlfenster:

-   Lagerort

-   Lagerort

-   aktiv, wenn Lagerstand auf Lagerortebene geführt wird und der
    > Lagerort editierbar ist

-   Chargen- bzw. Gerätenummer (d)

-   aktiv, wenn Lagerführung des Produktionsartikels auf Geräte- bzw.
    > Chargenebene ist und Lager Chargen-/Geräteverwaltung [lag.
    > cg_verw_jn = "j"] hat

-   folgende Felder im Auswahlfenster

-   Chargen- bzw. Gerätenummer

-   verfügbarer Lagerbestand

-   Ablaufdatum

-   Einlagerungsdatum

-   Menge

-   keine Eingabe bei Geräteartikeln (fix 1 bzw. -1 abhängig von
    > Freigabemenge Produktion)

-   Ablaufdatum

-   aktiv, wenn Charge mit Ablaufdatum geführt wird und Lager
    > Chargen-/Geräteverwaltung [lag. cg_verw_jn = "j"] hat

-   **Anmerkung**

Für Produktionsartikel mit "normaler Lagerführung" und Buchung auf
Lager ohne Lagerorte, wird beim speichern automatisch eine Zeile
angelegt.

Wird in der Gerätenummer das Zeichen # verwendet, so verstehen sich die
Zeichen vor dem # als Startgeräte-nummer für die automatische
Generierung einer Serie. Die Zeichen nach dem # definieren die Anzahl
der Gerätezeilen, die nach der Bestätigung der Eingabe automatisch
generiert werden.

**Prüfungen beim Speichern:**

-   Sind Zeilen vorhanden, muss die Mengensumme der Freigabemenge
    Produktion entsprechen, wenn dies lt. Artikelstamm des produzierten
    Artikels gewünscht ist [artik.auf_prod_frei_kz]

-   bei negativer Menge:

-   der ArtikLagSub-Datensatz muss bereits angelegt sein

-   der verfügbare Lagerstand darf nicht kleiner 0 werden

-   bei Geräten muss das Zustandskennzeichen "l" sein

-   bei positiver Menge:

-   bei Geräten darf kein ArtikLagSub-Datensatz mit Lagerstand ungleich
    > 0 vorhanden sein

-   bei Geräten muss das Zustandskennzeichen "a" oder "r" sein, bzw.
    > das Gerät ist nicht vorhanden

**Teilbereich "Teile"**

Bearbeitungsliste mit den Bestandteilen (=Teilen) des
Produktionsartikels

-   Artikelnummer (f)

-   nur bei Neuanlage und bei Artikel ohne Lagerführung einzugeben

-   Artikelmatchcode

-   nur bei Neuanlage und bei Artikel ohne Lagerführung einzugeben

-   Menge im Produktionsartikel

-   nur bei Neuanlage und bei Artikel ohne Lagerführung einzugeben

-   Lagernummer (fd)

-   Vorschlag lt. Firmenstamm

-   Lagerkennzeichen muss "e" sein

-   keine Eingabe, wenn gespeicherte freigegebene Produktionsmenge <>
    > 0 ist

-   offene Menge

-   freigegebene Menge

-   nur wenn freigegebene Produktionsmenge = 0, einzugeben ???

-   Prüfung wie in Auftragsposition

-   durchschnittlicher Einstandspreis

-   lt. ArtikelLager bzw. lt. Artikel bzw. lt. Artikel-Set

-   ist einzugeben, wenn unbestimmt

-   Lagerstand

-   verfügbare Menge

-   für Freigabe verfügbare Menge

    **Anmerkung  
    **

    Liste wird nach Eingabe des Produktionsartikels automatisch befüllt.
    Es werden nur Setteile mit folge_aufbau_kz = \'p\' berücksichtigt.
    In der Standardlösung dürfen nur Artikel ohne Lagerführung im
    Bearbeitungszweig "Neuanlage" eingefügt bzw. gelöscht werden.

    Beim speichern werden zunächst alle Artikel (Produktionsartikel und
    Teilartikel) gesperrt, danach erfolgt die Neuanlage bzw. Änderung
    des Auftrages und der Auftragspositionen in einer Transaktion.

#### Register "Bezugsbeleg"

-   Register nur aktiv, wenn Zusatzmodul vorhanden

    **Teilbereich "Belege"**

Bearbeitungsliste mit Belegen, die storniert bzw. kopiert werden sollen

-   Belegart (d)

-   Lieferschein

-   Auftrag

-   Belegnummer (f)

-   Prüfung der Auftragsarten siehe "Bezugsbelegeinlesen" im Extramenü

-   die Positionen werden im Teilbereich "Lieferscheinpositionen"
    > eingefügt

-   Verarbeitungskennzeichen (d)

-   Vorschlag abhängig von Auftragsart (g% "Gutschrift"

-   Gutschrift

-   Kopie

-   neue Preisfindung (c)

-   wird nur bei Verarbeitungsart "Kopie" ausgewertet

-   Vorschlag lt. Defaultwert

-   ist bei "Gutschrift" fix "n"

-   Einstandspreis verwenden (c)

-   Vorschlag lt. Defaultwert

-   ist bei "Kopie" fix "n"

-   Vorschlag für "Kennzeichen Positionsübernahme"

-   Vorschlag lt. Defaultwert

    Wird eine Zeile gelöscht, werden auch die entsprechenden Zeilen aus
    dem Teilbereich "Lieferscheinpositionen" entfernt.

    **Teilbereich "Belegpositionen"**

Bearbeitungsliste mit Lieferscheinpositionen, die als Vorlage für neue
Auftragspositionen herangezogen werden

-   Kennzeichen Positionsübernahme (c)

-   Setteilpositionen können nicht angehakt werden

-   Belegnummer (a)

-   Belegdatum (a)

-   Auftragsnummer Eingang (a)

-   Positionsnummer (a)

-   Positionskennzeichen (a)

-   Artikelnummer (a)

-   Artikelmatchcode (a)

-   Menge

-   gelieferte Menge bei Lieferschein

-   bestellte Menge bei Auftrag

-   Mengeneinheit (a)

-   Verkaufspreis (a)

-   Rabatt1-5 (a)

-   Positionswert (a)

-   Lagernummer (a)

-   Kennzeichen Gutschrift (a)

    **Anmerkung**

    Beim Speichern werden aus den Beleg-Zeilen Auftragspositionen
    aufgebaut. Die Logik entspricht dem "Bezugsbelegeinlesen", es
    werden jedoch keine Texte aufgebaut.

**ad Menüpunkt "Löschen"  
**

-   ist nur möglich, wenn keine Position eine Liefermenge eingetragen
    hat

-   Prüfung mit Ein- und Abwicklungsauftragsnummer

#### Register "Belegkette"

-   siehe unter Allgemeines Abfrageregister "Belegkette"

#### Auswahlpunkte im Menü "Extras" 

-   Bei Nicht- Service- Auftragsarten:

-   Packzettel drucken

-   Druck AB intern

-   AB versenden

-   Versand per Outlook

-   steht optional für AB und Offert zur Verfügung
    > [pfu_param.outlook_mail_kz]

-   Dokument wird erstellt, jedoch nicht gedruckt

-   TC wartet bis zum Timeout auf die Dokumentenerstellung durch den
    > aufgegebenen Job

-   ist Dokument erstellt, wird neue Outlook-Nachricht geöffnet und
    > folgende Felder gesetzt:

-   E-Mail-Adresse

-   BCC-E-Mail-Adressen

-   E-Mail-Adresse Vertreter und/oder zusätzliche E-Mail

-   Betreff

-   gleiche Logik wie bei Batchverarbeitung

-   Attachment

-   Dokument des aktuellen Jobs

-   Body

-   wird nicht gesetzt, damit die Signatur des Benutzers nicht
    > überschrieben wird

-   Proformafaktura drucken

-   Kommissionsschein drucken

-   Ist keine Position freigegeben, wird eine Meldung ausgegeben

-   Lieferbeleg erstellen

-   existieren Kommissionsscheine wird auf den Register "KS"
    > umgeschalten, nach der Freigabe wird der Lieferbelegaufbau
    > gestartet

-   gibt es freigegebene Positionen, jedoch keinen Kommissionsschein,
    > wird der Lieferbelegaufbau sofort gestartet

-   nur für Auftragsarten mit Lieferbeleg

-   Faktura drucken

-   nur für Auftragsarten mit Rechnungsbeleg

-   Offert übernehmen

-   nur für Offerte verfügbar

-   Auftrag auf erledigt setzen

-   setzt alle Auftragspositionen auf erledigt

-   bei Produktionsaufträgen Produktionsartikel und Teile in einer
    > Transaktion

-   In Rückstand versetzen

-   setzt Zustand von "erfasst" auf "Rückstand"

-   Zustand zurücksetzen

-   setzt Zustand von "vollständig geliefert" auf "Rückstand"

-   für Produktionsaufträge nicht verfügbar

-   Bezugsbeleg einlesen

-   für Auftragsarten n, g, gv, gw, b, k, ka, kr

-   Bestellung generieren

-   für Auftragsarten, bei denen Bestellbezug erlaubt ist

-   AB- bzw. Offert einsehen

-   öffnen des Ausdruck-Fensters und Anzeige von allen Offert- bzw.
    > AB-Versionen des aktuellen Auftrages

-   Druckvorschau

-   Aufruf des AB- bzw. Offertdruckes mit Option "intern" und Druckart
    > "vorschau"

-   folgender Ablauf:

-   Einspoolen Druckvorschau

-   5 Sekunden warten

-   Prüfen, ob Job erledigt, nach 5 erfolglosen Versuchen Abfrage ob
    > wiederholt oder abgebrochen werden soll

-   Anzeige der Vorschau

-   5 sekunden warten, erneut prüfen

-   neue Preisfindung

-   wird für alle Positionen durchgeführt, bei denen keine manuelle
    > Preisänderung durchgeführt wurde und die nicht einem Offert oder
    > Abrufstammauftrag zugeordnet sind

-   bei Service- Auftragsarten:

-   Packzettel drucken

-   Druck Kostenvoranschlag intern

-   Kostenvoranschlag versenden

-   Proformafaktura drucken

-   Kommissionsschein drucken

-   Arbeitsbericht drucken

-   reagiert abhängig vom Arbeitsbericht- Kennzeichen im Register
    > Service

-   Verbringungsbeleg für das Gerät drucken

-   es muss ein Gerät vorhanden sein

-   Als Adresse wird die Aufenthaltsadresse des Gerätes gedruckt

-   Faktura drucken

-   Offert übernehmen

-   Auftrag auf erledigt setzen

-   In Rückstand versetzen

-   setzt Zustand von "erfasst" auf "Rückstand"

-   Zustand zurücksetzen

-   setzt Zustand von "vollständig geliefert" auf "Rückstand"

-   Bestellung generieren

-   für Auftragsarten, bei denen Bestellbezug erlaubt ist

-   AB- bzw. Kostenvoranschlag einsehen

-   öffnen des Ausdruck-Fensters und Anzeige von allen
    > Kostenvoranschlag - bzw. AB-Versionen des aktuellen Auftrages

-   Druckvorschau

-   Aufruf des AB- bzw. Kostenvoranschlagdruckes mit Option "intern"
    > und Druckart "vorschau"

-   Ablauf w.o.

**ad Bezugsbeleg einlesen**

Es muss ein Auftragskopf angelegt sein

**Auswahldialog**

-   Verarbeitungsart (p)

-   Storno mit OP-Ausgleich

-   Storno ohne OP-Bezug (Gutschrift)

-   Kopieren

-   Rechnungsnummer (p)

-   neue Preisfindung (p)

-   wird nur bei Verarbeitungsart "Kopieren" ausgewertet

-   Ja

-   Nein

-   Kundennummer

-   Lieferscheinnummer

-   Abwicklungsauftragsnummer

    Durch Customizing können zusätzliche Auswahlfelder aus der Tabelle
    vlfs eingefügt werden.

    Ist die Rechnungsnummer < 1, muss Lieferscheinnummer oder
    Auftragsnummer ausgefüllt sein

    **Storno  
    **

-   Überschrifttextzeilen mit Verweis auf Bezugsbeleg werden aufgebaut

-   1. und 2. Zeile werden nur der 1. Position zugeordnet, die 2. Zeile
    > allen Positionen

-   "Bezugsbeleg Nr 1234567 vom 12.12.2002"

-   wenn Bezugsbeleg fakturiert ist

-   "Ursprünglicher Lieferschein 1234567 vom 12.12.2002"

-   Menge des ursprünglichen Lieferscheines \* -1

-   Der durchschnittliche Einstandspreis wird fix vom ursprünglichen
    Lieferschein genommen

-   dies ist auch beim Lieferscheinaufbau so

-   Der Verkaufspreis und die Rabatte werden fix vom ursprünglichen
    Lieferschein genommen

-   Auf Faktura und Lieferschein wird die Zeile "Ihre Bestellung ..."
    nicht gedruckt

-   nur wenn Bezugsbeleg fakturiert ist

-   Zahlungsart lt. Bezugsbeleg

-   Zahlungskonditionen und Valutadatum lt. Bezugsbeleg

-   wenn mit OP-Ausgleich

-   Ist das Rechnungskennzeichen "d", "k" oder "ka", wird es
    > automatisch auf "a" gesetzt

-   Der Auftrag wird auf "SoloAuftrag" gesetzt

-   Stornokennzeichen wird in FIBU-Schnittstelle übergeleitet

-   Bezugsbelegnummer wird als OP-Nummer verwendet

    **Kopieren  
    **

-   Überschrifttextzeilen werden lt. Bezugsauftragsposition aufgebaut

-   Menge ist vorzeichengleich zu Bezugsbeleg

-   Der durchschnittliche Einstandspreis wird aktuell von ArtikelLager
    bzw. Artikel, bzw. wenn dort unbestimmt vom ursprünglichen
    Lieferschein genommen und gegebenenfalls beim Lieferscheinaufbau
    aktualisiert

-   Verkaufspreis und Rabatte werden abhängig vom Startparameter neu
    ermittelt oder wie beim Storno vom Bezugsbeleg verwendet

    **Kombinationen von Auftragsarten**

+-------------------+--------------------------------------------------+
| Ursprungsauftrag  | Neuer Auftrag                                    |
+-------------------+--------------------------------------------------+
|                   |                                                  |
+-------------------+--------------------------------------------------+
| Normalauftrag     | Normalauftrag                                    |
|                   |                                                  |
| Barverkauf        | Barverkauf                                       |
|                   |                                                  |
| Handlieferschein  | Gutschrift                                       |
|                   |                                                  |
|                   | Gutschrift Vernichtung                           |
|                   |                                                  |
|                   | Gutschrift Wert                                  |
|                   |                                                  |
|                   | Gutschrift Kunde (Kundenretoure)                 |
|                   |                                                  |
|                   | Kommission                                       |
|                   |                                                  |
|                   | -   Funktion ist automatisch "Kopieren"        |
|                   |                                                  |
|                   |     Handlieferschein                             |
|                   |                                                  |
|                   | -   Funktion ist automatisch "Kopieren"        |
|                   |                                                  |
|                   |     Offert                                       |
+-------------------+--------------------------------------------------+
| Gutschrift        | Gutschrift                                       |
|                   |                                                  |
| Strecke           | Gutschrift Kunde (Kundenretoure)                 |
+-------------------+--------------------------------------------------+
| Gutschrift        | Gutschrift Vernichtung                           |
| Vernichtung       |                                                  |
+-------------------+--------------------------------------------------+
| Gutschrift Wert   | Gutschrift Wert                                  |
+-------------------+--------------------------------------------------+
| Kommission        | Kommissionsretoure                               |
|                   |                                                  |
|                   | -   Funktion ist automatisch "Kopieren"        |
|                   |                                                  |
|                   | -   wenn Kommissionslager je Lieferschein, wird  |
|                   |     komm_lag_ort belegt                          |
|                   |                                                  |
|                   |     Kommissionsabrechnung                        |
|                   |                                                  |
|                   | -   Funktion ist automatisch "Kopieren"        |
|                   |                                                  |
|                   | -   wenn Kommissionslager je Lieferschein, wird  |
|                   |     komm_lag_ort belegt                          |
|                   |                                                  |
|                   |     Normalauftrag                                |
|                   |                                                  |
|                   | -   "Kopieren" muss ausgewählt sein            |
+-------------------+--------------------------------------------------+
| K                 | Kommission                                       |
| ommissionsretoure |                                                  |
|                   | -   Funktion ist automatisch "Kopieren"        |
+-------------------+--------------------------------------------------+
| Komm              | Normalauftrag                                    |
| issionsabrechnung |                                                  |
|                   | Gutschrift                                       |
+-------------------+--------------------------------------------------+

####  Auswahlpunkte im Menü "Einstellungen" 

-   Einer der folgenden Menüpunkte kann angehakt sein:

-   Normalmodus

-   Servicemodus

-   Auswahldialog enthält Servicedaten

-   Liste enthält Servicedaten

#### Schaltflächen für Verzweigungen

-   Auftragspositionen

-   Lieferscheine

-   OP Abfrage

-   Dokumente

### Auftragsposition

**Allgemeines**

Es gibt 2 Verarbeitungsmodi:

-   Lieferscheinkorrektur

-   automatisch gesetzt, wenn vom Lieferscheinfenster geöffnet

-   es werden die Positionen des konstanten Lieferscheins (auch jene mit
    > Liefermenge = 0) angezeigt

-   dieser Modus ist nur mit einem Zusatzmodul zum Standardpaket möglich

-   Bei einer Neuanlage wird zunächst die Position mit freier Menge = 0
    > erfasst und gespeichert. Mit dem Speichern wird sofort die
    > Lieferscheinposition mit Menge = 0 generiert und sofort danach
    > abgeändert. (Liefermenge = offene Menge).

-   Setartikel und Folgeartikel werden bei der Neuanlage nicht
    > berücksichtigt.

-   Auftragserfassung

-   automatisch gesetzt, wenn nicht vom Lieferscheinfenster geöffnet

Allgemein

-   Auftragspositionen, die eine fakturierte Lieferscheinposition haben,
    dürfen wertmäßig nicht mehr geändert werden.

-   Auftragspositionen mit gelieferter bzw. gelöschter Menge dürfen
    nicht gelöscht werden.

-   Ist der Auftrag vollständig geliefert, darf keine Position mehr neu
    angelegt werden.

-   Auftragspositionen mit setaufbau_kz <> \'e\' dürfen nicht
    verändert werden

Modus "Lieferscheinkorrektur"

-   Auftragspositionen dürfen nicht gelöscht werden

-   Auftragspositionen dürfen nicht neu angelegt werden

-   ist der Lieferschein fakturiert (Rechnungsnummer <> 0) darf keine
    Änderung erfolgen

-   eine Position darf geändert werden wenn

-   Freigabemenge = 0

-   Kommissionsscheinnummer = 0

#### Auswahldialog

-   nicht, wenn von Auftrag oder Lieferschein geöffnet

-   Firma

-   Auftragsnummer

-   Positionsnummer

-   Positionsnummer Kommissionsschein

-   Artikelnummer (f)

-   Auftragsdatum

-   Auftragsart (w)

-   Kundennummer (f)

-   Kundenmatchcode

-   Kundenbestelldatum

-   Kundenbestellnummer

-   Zustandskennzeichen Auftrag (w)

-   Lieferscheinnummer

-   Lagernummer

-   Erledigungskennzeichen

-   erledigt

-   offen

-   Sachbearbeiterkennzeichen

-   Lieferdatum

-   Lieferwoche

-   Auftragsnummer Eingang

-   Abruf der Auftragsnummer

-   Abruf der Positionsnummer

-   Auftragspositionstext

Anmerkung

-   ist Lieferscheinnummer belegt, wird zusätzlich in der Tabelle
    [vlfs_pos] gesucht

-   ist der Auftragspositionstext belegt, so wird zusätzlich in der
    Tabelle [auf_pos_txt] gesucht

#### Register "Liste"

-   Firma

-   Filiale

-   Eingangsauftrag

-   Auftragsnummer

-   Zustandskennzeichen

-   Auftragsart

-   Auftragsdatum

-   Kundennummer

-   Kundenmatchcode

-   Positionsnummer

-   Artikelnummer

-   Artikelmatchcode

-   Positionskennzeichen

-   bestellte Menge

-   offene Menge

-   Eingabe möglich

-   freigegebene Menge

-   Eingabe möglich

-   zugeteilte Menge

-   Summe der Freigegebenen Mengen aus auf_pos_sub

-   Mengeneinheit

-   Losgröße (a)

-   Kommissionsscheinnummer

-   Kommissionsscheinposition

-   Lager

-   Verkaufspreis

-   Eingabe möglich

-   Rabatt 1 u 2

-   Eingabe möglich

-   Auftragskopfrabatt

-   Kopfrabattfähig (c)

-   Auftragswert Position

-   Währung

-   DB-%

-   DB-absolut

-   Sachbearbeiterkennzeichen

-   Lieferdatum

-   Lieferwoche

-   Kundenbestellnummer

-   Kundenbestelldatum

-   Auftragseingangsnummer

-   Abruf der Auftragsnummer

-   Abruf der Positionsnummer

-   Bestellnummer

-   Bestellposition

-   Lieferscheinpositionsdaten

-   leer, wenn im Modus "Auftragserfassung"

-   Position geliefert (c)

-   "j", wenn gelieferte Menge <> 0

-   "n", wenn gelieferte Menge = 0

-   gelieferte Menge Lieferschein

-   Eingabe möglich

#### Register "Detail"

**Teilbereich "Artikel"  
**

-   Firma

-   Auftragsnummer Abwicklung (f)

-   Kundennummer (a)

-   Kundenmatchcode (a)

-   Währungscode Auftrag (a)

-   Auftragsart (a)

-   Auftragsdatum (a)

-   Auftragsnummer Eingang (a)

-   Zustandskennzeichen Auftrag (a)

-   Positionsnummer

-   wird, wenn leer oder 0 bei der Neuanlage beim Speichern vergeben

-   Ist das letzte Feld in der Eingabereihenfolge

-   Positionsnummer des Sethauptartikels (a)

-   Artikelnummer (f)

-   Eingabelogik Nummer, Matchcode u. Identifikationen

-   Artikel muss aktiv sein

-   wird gegebenenfalls durch Alternativartikel ersetzt

-   abhängig von Auftragsart sind nicht immer alle Artikelarten erlaubt

-   Wemm der Artikel ein Auslaufartikel ist erfolgt abhängig vom
    > Parameter "auslauf_hinweis" ein Hinweis "Artikel ist ein
    > Auslaufartikel" ausgegeben.

-   Nicht melden

-   Immer Melden -- sofort bei Eingabe des Artikels

-   Verfügbarkeitsabhängig -- Erst nach Eingabe der Menge im Zuge des
    > Vorschlags der freizugebnden Menge.

-   Positionskennzeichen (a)

-   Artikelmatchcode

-   Eingabe bei diversen Artikeln

-   Lagerkennzeichen (a)

-   Artikelinfotext (a)

-   Lagerauswahlfenster

-   Sätze lt. ArtikelLager mit verfügbarem Lagerbestand <> 0 oder frei
    > verfügbarem Lagerbestand <> 0

-   folgende Felder im Auswahlfenster

-   Lagernummer

-   Lagerbezeichnung

-   verfügbarer Lagerbestand

-   frei verfügbarer Lagerbestand

-   im Modus "Lieferscheinkorrektur" nur Anzeige

-   Lagernummer (fd)

-   Ist bei Kommissionsabrechnungen oder -retouren fix das Lager des
    > Kunden

-   Ist bei Vorausfaktura fix das Lager des Kunden

-   Ist bei Auftragsarten mit eingetragenem Lager bereits fix bestimmt

-   Ist sonst mit dem Default-Lager lt. Sachbearbeiter oder Firma bzw.
    > mit dem zuletzt verwendeten Lager vorbelegt

-   im Modus "Lieferscheinkorrektur" nur Anzeige

-   Gegenlager (Ziellager)

-   Ist normalerweise leer

-   Ist bei Kommissionsaufträgen, Lieferungen zur Vorausfaktura oder
    > internen Umbuchungen fix das Lager des Kunden

-   Ist bei Kommissionsretouren oder Kundenretouren einzugeben und mit
    > dem Default-Lager vorbelegt

-   im Modus "Lieferscheinkorrektur" nur Anzeige

-   offene Menge

-   verändert bei Eingabe bestellte Menge

-   Ist bei Änderung vorzeichengleich zu bestellter Menge

-   bestellte Menge darf nicht 0 sein

-   ist bei Gutschriften negativ

-   ist bei Kommissionsstellung, -retoure, -abrechnung sowie bei Offert
    > und Abruf nur positiv

-   darf bei Produktion und Setteil und Einwegpfand nicht verändert
    > werden

-   löst bei Eingabe Preisfindung aus

-   Ist sie kein Vielfaches der Verkaufslosmenge, wird eine Meldung
    > ausgegeben

-   im Modus "Lieferscheinkorrektur" nur Anzeige

-   bestellte Menge (a)

-   gelieferte Menge (a)

-   fakturierte Menge (a)

-   gelöschte (nicht gelieferte) Menge (a)

-   freigegebene Menge

-   Wenn freigeben_jn im Auftragskopf aktiviert ist, so wird, die
    > verfügbare Menge bis maximal offene Menge als freigegebene Menge
    > vorgschlagen (passiert nach Eingabe der offenen Menge oder nach
    > Änderung des Lagers).  
    > Wenn freigeben_jn lt. Auftragsart Nein ist, so wird dazu die frei
    > verfügbare Menge satt der verfügbaren Menge verwendet.

-   darf offene Menge und "für Freigabe verfügbare Menge" nicht
    > übersteigen

-   Ist bei bestimmten Auftragsarten fix die offene Menge, oder fix 0

-   im Modus "Lieferscheinkorrektur" nur Anzeige

-   Verkaufsmengeneinheit

-   kann nur bei diversen Artikeln geändert werden

-   Kommissionslieferscheinnummer (d)

-   ist nur bei Kommissionsrücknahme bzw. -abrechnung einzugeben, sonst
    > leer

-   Wird der Verkaufspreis einer Kommissionsabrechnung über den Preis
    > des Kommissionslieferscheins ermittelt, muss das Feld befüllt sein

-   Verkaufspreis

-   Eingabe löst bei Sethauptartikel Preisaufteilung im Register "Set"
    > bei den Teilen aus

-   Verkaufspreis pro Menge

-   kann nur bei diversen Artikeln geändert werden

-   Verkaufspreis per Einheit (a)

-   Verkaufsrabatt 1 u. 2

-   Eingabe löst bei Sethauptartikel Preisaufteilung im Register "Set"
    > bei den Teilen aus

-   Lieferdatum

-   leer bei Vorschlag bzw. Anfrage

-   Lieferwoche

-   leer bei Vorschlag bzw. Anfrage

-   Garantiemonate Verkauf

-   Positionsbetrag (a)

-   gerechnet von bestellter Menge

-   Gesamtbetrag Auftrag (a)

-   gerechnet von bestellter Menge

-   Liefertermintext

-   leer bei Vorschlag bzw. Anfrage

-   durchschnittlicher Einstandspreis

-   ist normalerweise nicht sichtbar

-   ist einzugeben, wenn ArtikelLagerDuEst und ArtikelDuest unbestimmt
    > sind

-   ist einzugeben, wenn die Auftragsart "Strecke" ist

-   Wird lt. Parameter duest_setzen_kz beim Speichern mit 0 belegt wenn
    > er unbestimmt sein sollte

-   n = Nicht setzen (muss immer zwingend eingegeben werden)

-   b = Batch -- bei Batch Programmen wird der DUEST mit 0 belegt

-   s = Immer auf 0 setzen

-   Termintext

-   für das aktuelle Lager

-   Lagerstand (a)

-   verfügbarer Lagerstand (a)

-   für Freigabe verfügbare Menge (a)

-   für alle Dispolager

-   Lagerstand (a)

-   verfügbare Menge (a)

-   bestellte Menge Lieferant (a)

-   Lager wird gebucht (c)

-   Defaultwert lt. Auftragsart bzw. Artikelkennzeichen

-   Nur eingebbar, wenn es das Programm erlaubt

-   Statistikmenge wird gebucht (c)

-   Defaultwert lt. Auftragsart

-   Nur eingebbar, wenn es das Programm erlaubt

-   Auftragsnummer Abruf

-   Positionsnummer Abruf

-   definiert Abrufauftragsposition von welcher abgerufen wird

-   von Abrufauftragsposition wird vorbelegt:

-   Artikelnummer

-   Verkaufspreis und Rabatte

-   Bestellnummer (a)

-   Bestellpositionsnummer (a)

-   Produktionsauftragsnummer (a)

-   Auftragsnummer Eingang (a)

-   Kommissionsscheinnummer (d)

-   bei der Neuanlage kann eine Position einem bestehendem
    > Kommissionsschein zugeordnet werden

-   im Modus "Lieferscheinkorrektur" nur Anzeige

-   Wartungsvertragsnummer (f) + Position (f)

-   nur bei Wartungsvertrags- und Serviceauftragsarten sichtbar

-   keine Eingabe bei Wartungsveträgen, wird aus Setregister bestimmt

-   Verrechnungsart Service (fd)

-   nur bei Serviceauftragsarten sichtbar

-   Artikelprovisionsgruppe (fd)

-   Vorschlag lt. Artikel

-   nicht sichtbar, nicht eingebbar, beim Customizen kann Feld aktiviert
    > werden

-   Limitprüfung (c)

-   Feld wird beim Öffnen des Fensters auf "j" gesetzt

-   Feld kann jederzeit auf "n" geändert werden

-   im Modus "Lieferscheinkorrektur" fix "n"

-   Fremdpositionsnummer

-   wird, wenn unbestimmt, beim Speichern mit 0 belegt

-   muss bei Kunden mit „elektronischer Rechnung an den Bund" und
    > Kundenbestellnummer like ‚47%' (lt. pfu_param) <> 0 sein

-   Variante (c)

-   Eingabe nur bei Offert

-   wenn nicht Offert, fix "n", nicht sichtbar

-   Feld nur sichtbar, wenn Modul "Offert erweitert" aktiviert ist

    **Anmerkung**

Bei Produktionsaufträgen darf weder angelegt, noch geändert oder
gelöscht werden.

Beim Speichern des Sethauptartikels werden die im Register "Set"
definierten Setbestandteile automatisch angelegt und der DuEst des
Hauptartikels bestimmt.

Wird der Preis oder die Rabatte manuell geändert, wird dies in der
Positionstabelle vermerkt.

Wird beim Speichern das offene Kreditlimit überschritten und soll die
Limitprüfung durchgeführt werden, erfolgt die Anzeige von "Kreditlimit
überschritten ! - Limit: 999999999,99 Limit offen: -999999999,99".

Setteilpositionen mit Kennzeichen Einwegpfand laufen sowohl bestellte
Mengen alsauch Freigabemengen immer synchron mit dem Hauptartikelmit.
So, wie es bei echten Setteilen auch passiert.

Dazu muss Bezug zum Hauptartikel bestehen. Set_pos_nr belegen wie bei
Setartikeln

**Teilbereich "Artikeltexte"**

-   Bearbeitungsliste mit den Artikeltextzeilen der Auftragsposition Die
    > Zeilen werden bei der Neuanlage aus den Artikeltextzeilen
    > vorgeschlagen, bei diversen Artikeln wird der Matchcode
    > vorgeschlagen

-   Es gibt einen Berechtigungsträger "TextÄnderung". Gibt es diese
    > Berechtigung nicht, so dürfen Texte mit auf_pos_txt_kz = "a" nur
    > bei diversen Artikeln geändert werden

-   Artikeltext

-   Fettdruck (c)

-   Unterstreichung (c)  
    Belegtypen auf welchen der Text gedruckt werden soll, Defaultwerte
    lt. Artikelstamm

-   Auftragsbestätigung (c)

-   Kommissionsschein (c)

-   Lieferschein (c)

-   Rechnung (c)

-   Offert (c)

-   Bestellung (c)

    **Anmerkung**

Textbausteine können eingefügt werden, bei Kunden mit Sprachkennzeichen
<> \'d\' werden, sofern vorhanden, die deutschen
"Kommissionsscheintextzeilen" eingefügt.

**  
**

#### Register "Lager"

-   Bearbeitungsliste mit der Lageraufteilung der Auftragsposition

-   steht im Modus "Lieferscheinkorrektur" nicht zur Verfügung

-   Listbox Lagerbestände (d)

-   aktiv, wenn Lagerstand auf Lagerortebene geführt wird

-   definiert Lagerort und/oder Chargen- bzw. Gerätenummer

-   folgende Felder im Auswahlfenster:

-   Lagerort

-   Chargen- bzw. Gerätenummer

-   verfügbarer Lagerbestand

-   Ablaufdatum

-   Einlagerungsdatum

-   Listbox Lagerorte (d)

-   aktiv, wenn Lagerstand auf Lagerortebene geführt wird

-   definiert Lagerort

-   folgende Felder im Auswahlfenster:

-   Lagerort

-   Lagerort

-   aktiv, wenn Lagerstand auf Lagerortebene geführt wird und der
    > Lagerort editierbar ist

-   Listbox Gegenlagerorte (d)

-   aktiv, wenn Lagerstand des Gegenlagers auf Lagerortebene geführt
    > wird und die Auftragsart Kommissionsretoure oder Umbuchung ist

-   definiert Gegenlagerort

-   folgende Felder im Auswahlfenster:

-   Lagerort

-   Gegenlagerort

-   aktiv, wenn Lagerstand des Gegenlagers auf Lagerortebene geführt
    > wird, die Auftragsart Kommissionsretoure oder Umbuchung ist und
    > der Lagerort editierbar ist

-   Chargen- bzw. Gerätenummer (d)

-   aktiv, wenn Lagerführung auf Geräte- bzw. Chargenebene ist und Lager
    > Chargen-/Geräteverwaltung [lag. cg_verw_jn = "j"] hat

-   folgende Felder im Auswahlfenster

-   Chargen- bzw. Gerätenummer

-   verfügbarer Lagerbestand

-   Ablaufdatum

-   Einlagerungsdatum

-   Gegenlager Chargen- bzw. Gerätenummer

-   aktiv, wenn Lagerführung auf Geräte- bzw. Chargenebene ist,
    > Gegenlager Chargen-/Geräteverwaltung [geg_lag. cg_verw_jn =
    > "j"] und Lager keine Chargen-/Geräteverwaltung [geg_lag.
    > cg_verw_jn = "n"] hat. Muss in diesem Fall <> " " sein

-   fix " " wenn Gegenlager keine Chargen-/Geräteverwaltung [geg_lag.
    > cg_verw_jn = "n"] hat

-   sonst fix [charge_geraet]

-   Menge

-   keine Eingabe bei Geräteartikeln (fix 1 bzw. -1 abhängig von
    > Freigabemenge)

-   Ablaufdatum

-   aktiv, wenn Charge mit Ablaufdatum geführt wird und Lager
    > Chargen-/Geräteverwaltung [lag. cg_verw_jn = "j"] hat

-   Gegenlager Ablaufdatum

-   aktiv, wenn Charge mit Ablaufdatum geführt wird, Gegenlager
    > Chargen-/Geräteverwaltung [geg_lag. cg_verw_jn = "j"] und
    > Lager keine Chargen-/Geräteverwaltung [geg_lag. cg_verw_jn =
    > "j"] hat. Muss in diesem Fall <> " " sein

-   fix NULL wenn Gegenlager keine Chargen-/Geräteverwaltung [geg_lag.
    > cg_verw_jn = "n"] bzw. Artikel kein Ablaufdatum hat

-   sonst fix [ablauf_dat]

-   **Anmerkung**

Für Artikel ohne Lagerführung ist der Teilbereich "Lagerdaten"
gesperrt. Für Artikel mit "normaler Lagerführung" und Buchung auf
Lager ohne Lagerorte, wird beim speichern automatisch eine Zeile
angelegt.

Wird in der Gerätenummer das Zeichen # verwendet, so verstehen sich die
Zeichen vor dem # als Startgeräte-nummer für die automatische
Generierung einer Serie. Die Zeichen nach dem # definieren die Anzahl
der Gerätezeilen, die nach der Bestätigung der Eingabe automatisch
generiert werden.

**Prüfungen beim Speichern:**

-   bei positiver Menge:

-   der ArtikLagSub-Datensatz muss bereits angelegt sein

-   der verfügbare Lagerstand darf nicht kleiner 0 werden

-   bei Geräten muss das Zustandskennzeichen "l" sein

-   bei negativer Menge:

-   bei Geräten darf kein ArtikLagSub-Datensatz mit Lagerstand ungleich
    > 0 vorhanden sein

-   bei Geräten muss das Zustandskennzeichen "k" sein

#### Register "Überschriften"

**Teilbereich "Überschriftsauswahl"**

-   Überschriftnummer (a)

-   wird bei Neuanlage einer Überschrift automatisch vergeben

-   Überschriftauswahlfeld (d)

-   pro Überschrift jeweils die 1. Zeile; zusätzlich ein Satz mit
    > "neu" für Neuanlage einer Überschrift

-   Vorschlag (c)

-   setzt Merker, ob aktuelle Überschrift bei Neuanlage von
    > Folgepositionen automatisch zugeordnet wird Überschriftnummer
    > Sortierung

-   wird, wenn beim Speichern unbestimmt mit Überschriftsnummer \* 10
    > belegt

    Folgende Felder sind nur im Modul "Offert erweitert" sichtbar
    ([pfu_param.offert_erweitert_jn] = "j"

-   Überschriftsvorlage (fd)

-   ist normalerweise unbestimmt

-   wenn bestimmt, wird automatisch eine neue Überschrift begonnen und
    > die Daten der Vorlage übernommen

-   Sortiernummer

-   neue Seite (c)

-   Summe (c)

-   wenn "j", wird bei Wechsel der Überschrift auf dem Offert eine
    > Zwischensumme gedruckt

-   Endsumme (c)

-   wenn "j", rechnen Positionen die zu dieser Überschrift gehören in
    > die Endsumme

-   Summentext

**Teilbereich "Überschriftstext"**

-   Zeilen werden durch Überschriftsauswahl automatisch angezeigt

-   Überschriftstext

-   Fettdruck (c)

-   Unterstreichung (c)

-   Belegtypen auf welchen der Text gedruckt werden soll, Userdefaults
    bei 1. Zeile, ab 2.Zeile lt. voriger Zeile

-   Auftragsbestätigung (c)

-   Offert (c)

-   Lieferschein (c)

-   Rechnung (c)

#### Register "Set"

Bearbeitungsliste mit dem Sethauptartikel und den Setbestandteilen
(=Teilen)

-   rekursive Sets lt. Artikelstamm werden hier vollständig aufgelöst

-   Wartungsvertragsnummer (a)

-   bei der Änderung Wert lt. Auftragsposition

-   bei der Neuanlage Wert lt. Auftragskopf

-   Wartungsvertragsposition

-   bei der Neuanlage leer

-   bei der Änderung

-   keine Eingabe

-   Wert lt. Auftragsposition

-   Artikelnummer (f)

-   keine Eingabe, wenn WV-Auftrag

-   Artikelmatchcode

-   kann immer übersteuert werden

-   kann auch dann übersteuert werden, wenn es eine benutzerdefinierte
    > Feldberechtigung gibt, und der Anwender keine Berechtigung hat und
    > der Matchcode leer oder unbestimmt ist

-   Setstufe

-   siehe Datenbankbeschreibung [auf_pos.set_stufe]

-   Menge im Set

-   Verkaufseinheit

-   Verkaufspreis

-   Verkaufsrabatt 1 u. 2

-   durchschnittlicher Einstandspreis

-   lt. ArtikelLager, bzw. lt. Artikel bzw. lt. Artikel-Set

-   ist einzugeben, wenn unbestimmt

-   Lagerstand

-   verfügbare Menge

-   für Freigabe verfügbare Menge

    **Anmerkung  
    **

-   Die Liste wird nach Eingabe des Sethauptartikels im Register
    "Detail" automatisch befüllt. Es werden nur Setteile mit
    folge_aufbau_kz <> \'p\' berücksichtigt.

-   Wenn die Position bereits gespeichert ist, darf nur im Modus
    "Setkorrektur" eingefügt bzw. gelöscht werden.

-   Wenn die Menge ausgefüllt ist, darf weder eingefügt, noch gelöscht
    werden, weiters dürfen die Teilmengen nicht geändert werden

-   Eine Änderung des Preises, bewirkt die Neubelegung des Preises in
    der Hauptposition.

-   Setaufbau für Set mit set_frei_kz = "s" wird entweder sofort oder
    im Batch (abhängig von TC-Parameter) verarbeitet

-   Bei Batchverarbeitung werden die dafür relevanten Daten in der
    Tabelle auf_pos_set zwischengespeichert

#### Register "Einkauf"

-   steht im Modus "Lieferscheinkorrektur" nicht zur Verfügung

-   Darf bei einem Auslaufartikel nicht verwendet werden.

-   Rahmen vorhanden (ac)

-   wird nur bei der Neuanlage der Zeile ermittelt

-   ist bei Abrufaufträgen fix "n"

-   Rahmenbestellung Auswahlfenster (d)

-   nicht bei Abrufaufträgen

-   Lieferantennummer

-   Lieferantenmatchcode

-   Bestellnummer

-   Bestelldatum

-   Menge

-   offene Menge

-   Einkaufspreis

-   Rabatt 1-4

-   Rahmenbestellnummer (f)

-   bei Abrufaufträgen fix 0

-   Rahmenbestellposition (f)

-   bei Abrufaufträgen fix 0

-   wird bei Neuanlage der Zeile ggf. durch Rahmenbestellung des
    > zugeordneten Abrufauftrages bestimmt, wenn die offene Menge der
    > Rahmenbestellung <> 0 ist.

-   bestimmt Lieferant

-   bestimmt Einkaufspreis und Einkaufsrabatte

-   offene Auftragsmenge darf offene Rahmenbestellmenge nicht
    > überschreiten

-   löscht Projekt

-   setzt "Daten lt. Artikellieferant" auf "n"

-   keine Eingabe wenn Rahmenbestellung <> 0

-   Lieferant (fd)

-   Listbox über Artikel/Lieferant

-   prüfen Projektpreise und Meldung "Projektpreise vorhanden"

-   Projekt (d)

-   wird Projekt ausgewählt, werden Preise und Rabatte übernommen

-   Lieferantenartikelnummer

-   Nur bei diversen Artikeln eingebbar, sonst lt. artikid belegt

-   Daten lt. Artikellieferantenstamm verwenden (c)

-   Defaultwert ist bei diversen Artikeln "n", sonst "j"

-   offene Menge in Einkaufseinheit (a)

-   Einkaufsmengeneinheit (fd)

-   Eingabe nur bei diversen Artikeln

-   Vorschlag bei diversen Artikeln nach Lieferantenauswahl aus
    > Verkaufseinheit der AufPos

-   Einkaufspreis

-   Einkaufswährung (a)

-   Einkaufspreis proMenge (d)

-   Vorschlag bei diversen Artikeln nach Lieferantenauswahl aus
    > Preiseinheit der AufPos

-   Einkaufspreis per Einheit (a)

-   Einkaufsrabatt 1 u. 2

-   Positionsbetrag (a)

-   gerechnet von bestellter Menge

-   Lieferdatum

-   Lieferwoche

    **Anmerkung**

-   Daten **müssen** vorhanden sein und werden, wenn
    vorhanden, automatisch beim Speichern angelegt, wenn:

-   Freie Menge = 0

-   offene Menge > 0

-   Auftragsart = "Strecke"

-   Artikelkennzeichen ist "Normal", "Divers"

-   Daten **müssen nicht** vorhanden sein, werden aber, wenn
    genau ein ArtikelLieferant vorhanden ist, automatisch beim Speichern
    angelegt wenn:

-   Freie Menge = 0

-   offene Menge > 0

-   Auftragsart erlaubt auftragsbezogene Bestellung

-   Artikelkennzeichen = "Divers" oder {Anpassung durch Customizing}

-   Ist bei Strecke eine Zeile aufzubauen, aber nicht genau ein Satz im
    Artikellieferantenstamm vorhanden, wird beim Speichern automatisch
    auf den Register "Einkauf" verzweigt

-   Ist ansonsten eine Zeile automatisch aufzubauen, aber nicht genau
    ein Satz im Artikellieferantenstamm vorhanden, wird beim Speichern
    eine Meldung "keine Einkaufsdaten aufgebaut !" ausgegeben

-   Bei Auftragsarten ohne auftragsbezogene Bestellung bzw. bei
    Artikelarten die nicht bestellt werden können, ist der Register
    deaktiviert

-   Ist der Einkaufspreis beim Speichern bestimmt, wird der ermittelte
    Einstandspreis (Rechenlogik wie Artikelstamm) als Einstandspreis der
    Auftragsposition abgestellt

#### Register "Abrufpositionen"

Anzeigeliste der offenen Abrufpositionen des Artikels und der aktuellen
Kundenabrufgruppe bzw. wenn leer, des aktuellen Kunden

-   Auswahlfeld (c)

-   nur dieses Feld kann eingegeben werden

-   von aktueller Position wird abgerufen, Auftragsnummer und
    > -positionsnummer werden im Detail eingetragen

-   Auftragsnummer

-   Positionsnummer

-   Auftragsdatum

-   Kundenbestellnummer

-   Kundenbestelldatum

-   Kundennummer

-   Kundenmatchcode

-   lt. Abrufstammauftrag

-   Name 1

-   Straße

-   Postleitzahl

-   Ort

-   offene Abrufmenge

-   Gesamtabrufmenge

-   bereits abgerufene Menge

-   Verkaufspreis

-   Rabatte 1-5

    **Anmerkung**

-   Wenn Kunde und Artikel bestimmt sind, wird dieses Register befüllt.
    Werden Daten gefunden, wird automatisch auf diesen Register
    verzweigt, es muss jedoch keine Position ausgewählt werden. Wird
    eine Position ausgewählt, wird diese ins Detail übernommen.

#### Register "Alternativen"

Anzeigeliste der möglichen Alternativartikel
[artik_altern.altern_vkz_kz not in ("-", "e")]

Für diese Anzeige ist ein Zusatzmodul zum Standardpaket erforderlich

-   Auswahlfeld (c)

-   nur dieses Feld kann eingegeben werden

-   dieser Artikel wird als Alternative gewählt

-   Artikelnummer

-   Artikelmatchcode

-   Kennzeichen Auslaufartikel

-   lt. aktuellem Lager

-   das ist das Lager lt. Sachbearbeiter bzw. lt. Firma

-   Lagerstand

-   verfügbarer Lagerstand

-   bestellte Menge Lieferant

    **Anmerkung**

-   Ist der Artikel bestimmt, wird dieses Register befüllt. Befindet
    sich darin ein Artikel mit Alternativkennzeichen "a" für
    "Anzeigen", wird automatisch auf diesen Register verzweigt.

-   Wird ein Artikel ausgewählt, wird wieder automatisch auf das
    Detailregister umgeschaltet

#### Register "Lieferscheinkorrektur" 

-   Register steht nur im Modus "Lieferscheinkorrektur" zur Verfügung
    und beinhaltet die Daten der aktuellen Lieferscheinposition

-   ist nicht verfügbar, wenn Statistik bereits bei Lieferschein
    aufgebaut wird (TC-Parameter)

-   ist nur für Lieferscheine mit Rechnungsnummer = 0 verfügbar

-   ist für Setbestandteile nicht verfügbar

-   ist für folgende Auftragsarten verfügbar

-   Normal

-   Gutschrift (alle Varianten)

-   Kundenretoure

-   Interne Umbuchung (auch Retoure)

-   Handlieferschein

-   Strecke

-   ist für Buchungen mit Gegenlager (interne Umbuchung und
    Kundenretoure) nur verfügbar, wenn die Gegenlagerbuchung noch nicht
    erfolgt ist

-   **Teilbereich "Lieferschein"**

-   Lieferscheinnummer (a)

-   Lieferscheindatum (a)

-   Positionsnummer (a)

-   Artikelnummer (a)

-   Artikelmatchcode (a)

-   Lagernummer (a)

-   Lagerbezeichnung (a)

-   gelieferte Menge Lieferschein

-   bestimmt gelieferte Menge Position

-   bei Sethauptartikel nur 0 oder ursprüngliche Menge erlaubt

-   offene Menge Position

-   bestimmt auch bestellte Menge

-   bestellte Menge Position (a)

-   gelieferte Menge Position (a)

-   bestimmt wie folgt, auch die anderen Mengen

-   gelieferte Menge >= bestellte Menge

-   gelöschte Menge = 0

-   offene Menge = 0

-   bestellte Menge = gelieferte Menge

-   gelieferte Menge < bestellte Menge

-   gelöschte Menge = 0

-   offene Menge = bestellte Menge - gelieferter Menge

-   gelöschte Menge <> 0

-   gelöschte Menge = bestellte Menge - gelieferter Menge

-   gelöschte Menge Position (a)

    **Teilbereich "Lagerbewegung"**

-   Bearbeitungsliste mit den Lagerbuchungen der
    Verkaufslieferscheinposition

-   bestehende Zeilen dürfen nicht gelöscht oder geändert werden

-   ist für Positionen ohne Lagerbewegung gesperrt

-   Lagernummer (f)

-   kann nur in einer neuen Zeile eingegeben werden

-   muss der Wert einer bereits gespeicherten Zeile sein

-   gibt es nur einen möglichen Wert, ist das Feld bestimmt und nicht
    > einzugeben

-   Listbox Lagerorte (d)

-   aktiv, wenn Lagerstand des eingegebenen Lagers auf Lagerortebene
    > geführt wird

-   definiert Lagerort

-   folgende Felder im Auswahlfenster:

-   Lagerort

-   Lagerort

-   aktiv, wenn Lagerstand des eingegebenen Lagers auf Lagerortebene
    > geführt wird und der Lagerort editierbar ist

-   Chargen- bzw. Gerätenummer

-   aktiv, wenn Lagerführung auf Geräte- bzw. Chargenebene ist und Lager
    > Chargen-/Geräteverwaltung [lag. cg_verw_jn = "j"] hat

-   Karteimenge in Lagereinheit

-   bei Geräteartikeln nur 1 bzw. -1 erlaubt

-   Vorschlag -1 bzw. +1 abhängig von Vorzeichen der Differenzmenge
    > zwischen Liefermenge alt und Liefermenge

-   ACHTUNG: die Menge ist aus der Sicht des Lagers, daher
    > vorzeichenverkehrt zur Liefermenge

-   Ablaufdatum

-   aktiv, wenn Charge mit Ablaufdatum geführt wird und Lager
    > Chargen-/Geräteverwaltung [lag. cg_verw_jn = "j"] hat

-   Buchungsdatum und Zeit (a)

-   Jahr bis Sekunde

-   Sachbearbeitercode (a)

Anmerkung

Das Buchungsdatum wird nicht gespeichert, sonder durch die Datenbank
vergeben nach dem Speichern wird der Lagerdatenbereich neu eingelesen

Der optionale Karteitext der Position wird durch eigenes Event befüllt
(Logik wie Warenzugang)

Wurde bei Artikeln mit "normaler Lagerführung" und Buchung auf Lager
ohne Lagerortführung keine manuelle Zeile angelegt, wird beim Speichern
automatisch eine Lagerbewegungszeile (Karteimenge = Liefermenge alt -
Liefermenge) angelegt. Dies erfolgt pro Lager, damit wird auch eine
interne Umbuchung automatisch korrigiert

Wenn die gelieferte Menge auf 0 geändert wird und es wurden keine
manuellen Lagerbuchungszeilen erfasst, werden alle vorhanden
Lagerbuchungszeilen mit umgekehrten Vorzeichen vorgeschlagen.Wenn die
gelieferte Menge geändert wird (nicht auf 0) und es gibt nur eine
Lagerbuchungszeile, so wird die Differenzmenge mit den Daten dieser
Lagerbuchungszeile vorgeschlagen. (z.B. Artikel mit Lagerort wurde nur
von einem Lagerort entnommen, damit legen wir es wieder aus diesen
Lagerort zurück, wenn die Entnahme von mehreren Lagerorten erfolgt ist,
so muss der User eingeben auf welchen die Waren zurück kommt).

Ist beim Speichern der Modus "Setkorrektur" aktiviert, so wird er beim
Speichern automatisch zurückgesetzt.

**Prüfungen beim Speichern:**

-   die Summe der Karteimengen muss pro Lager mit der Liefermenge in
    Lagereinheit übereinstimmen (für die Prüfung werden Absolutwerte
    verwendet)

-   bei negativer Menge:

-   der ArtikLagSub-Datensatz muss bereits angelegt sein

-   der verfügbare Lagerstand darf nicht kleiner 0 werden

-   bei Geräten muss das Zustandskennzeichen "l" sein

-   bei positiver Menge:

-   bei Geräten darf kein ArtikLagSub-Datensatz mit Lagerstand ungleich
    > 0 vorhanden sein

-   Bei Buchungen mit Gegenlager (Kundenretoure, interne Umbuchung) muss
    > bei Geräten das Zustandskennzeichen "l" sein

-   sonst muss bei Geräten das Zustandskennzeichen "k" sein

Allgemeines zum Speichern einer Position im Modus
"Lieferscheinkorrektur"

-   der Auftragszustand des Auftrages kann zwischen "vollständig
    geliefert" und "Rückstand" wechseln

-   der Positionszustand kann zwischen "offen" und "erledigt"
    wechseln

-   wird die Gerätestatistik mit "Einstandspreis" geführt
    (TC-Parameter) wird diese anhand der neuen Karteizeilen gelöscht
    bzw. neu aufgebaut

-   der Verbrauch wird, wenn bereits gebucht, sofort in der Statistik
    korrigiert

-   bei der Korrektur der Positionswerte der Lieferscheinposition werden
    die alten Werte heraus und die neuen hineingerechnet

-   Es muss auch die die DUEST-Ermittlung der Position mit der
    Differenzmenge aufgerufen werden. Da sich dadurch evt. die DUEST
    Berechnung von nachfolgenden Zugängen verändert.

-   Speichern einer Sethauptposition mit Menge=0

-   es werden automatisch alle zugehörigen Setteile der Reihe nach
    > eingelesen

-   die Menge wird automatisch auf 0 gestellt

-   die Karteipositionen werden vorzeichengedreht dupliziert

-   dies erfolgt in einer Transaktion --> bei einem Fehler wird das
    > Speichern abgebrochen und die Sethauptposition unverändert
    > angezeigt

#### Register "Belegkette"

-   siehe unter Allgemeines Abfrageregister "Belegkette"

#### Auswahlpunkte im Menü "Extras"

-   Auftragsposition erledigt setzen

-   Position wird erledigt gesetzt, die offene Menge wird zur gelöschten
    > Menge addiert

-   Auftragsposition splitten

-   nur wenn offene Menge <> freigegebener Menge, nicht für Sethaupt-
    > und -unterpositionen

-   neue Preisfindung

-   nur, wenn Auftragsart und Verrechnungsart Preise vorsieht

-   nicht, wenn Auftragsposition bereits fakturiert ist, oder (bereits
    > geliefert ist und die Statistik beim Lieferschein aufgebaut wird)

-   ist auch im "geändert"-Zustand erlaubt

-   Feld "Preise manuell geändert" wird auf "n" zurückgesetzt

-   Beginn Setkorrektur

-   nur, wenn es sich um eine Sethauptposition der Setstufe 0 handelt

-   setzt Modus Setkorrektur

-   Merken der offenen Menge

-   Ausnullen der offenen Menge, damit Korrekturen am Setregister
    > durchgeführt werden können

-   Ende Setkorrektur

-   nur, wenn Modus Setkorrektur gesetzt ist

-   Setzt die offene Menge

-   Start Setaufbau im Batch

-   nur, wenn setaufbau_kz <> \'e\'

-   spoolt BatchSetaufbau erneut ein

**ad Auftragsposition splitten**

-   aktuelle Auftragsposition wird kopiert

-   automatisch "Neu" durch Programm

-   kopierte Felder werden eingefügt

-   Vorschlag offene Menge = Differenz zwischen bestellter Menge und
    > freigegebener Menge der ursprünglichen Position

-   Splitt-Positionsnummer wird lt. Positionsnummer der ursprünglichen
    > Position belegt, um Zusammengehörigkeit zu kennzeichnen

-   Kontrolle des Programmablaufes wird an den Anwender übergeben, es
    kann geändert, gespeichert oder verworfen werden

-   keine Änderung der Artikelnummer möglich

-   offene Menge kann Vorschlagsmenge nicht übersteigen

-   Mengeneingabe löst keine Preisfindung aus

-   nach dem Speichern wird automatisch die bestellte Menge der
    ursprünglichen Position um die offene Menge der neuen Position
    verringert

#### Schaltflächen für Verzweigungen

-   AbrufAuftragsposition

-   Lieferscheinpositionen

-   Verkaufskonditionen

-   Preiskunde und Preisartikel sind konstant

-   ist auch im "geändert"-Zustand erlaubt, wenn Kunde und Artikel
    > bestimmt sind

-   Kassa-Belegpositionen

-   zeigt die zugehörige(n) Kassa-Belgpositionen an

-   für den Fall, dass der Auftrag über die Kassa erledigt wurde

-   

### Lieferschein

Allgemeines

-   Fenster dient zur Abfrage der Ausgangslieferscheine, es können
    jedoch bis auf das Feld Selektionskriterium und die Versanddaten des
    "Duplikatdrucks" keine Änderungen durchgeführt werden

#### Auswahldialog

-   Firma

-   Lieferscheinnummer (f)

-   Lieferscheindatum

-   Rechnungsnummer (f)

-   Rechnungsdatum

-   Kundennummer (f)

-   Kundenmatchcode

-   Auftragsnummer

-   Auftragsdatum

-   Auftragsart (w)

-   Sachbearbeiterkennzeichen

-   Kundenbestellnummer

-   Kundenbestelldatum

-   Selektionskriterium Faktura

-   Zustandskennzeichen (w)

-   Defaultwert (a)ktiv

-   Jobnummer

#### Register "Liste"

-   WebdokFunktionalität

-   Firma

-   Filiale

-   Lieferscheinnummer

-   Lieferscheindatum

-   Rechnungsnummer

-   Rechnungsdatum

-   Kundennummer

-   Kundenmatchcode

-   Sachbearbeiterkennzeichen

-   Auftragsnummer

-   Auftragsart

-   Auftragsdatum

-   Kundenbestellnummer

-   Kundenbestelldatum

-   Selektionskriterium Faktura (c)

-   Lieferadresse

-   Name1

-   Name2

-   Straße

-   PLZ

-   Ort

-   Ländercode

-   Erfassungszeitpunkt

#### Register "Detail"

-   Firma (a)

-   Kundennummer (a)

-   Debitorennummer (a)

-   Währungscode (a)

-   Kundenmatchcode (a)

-   Lieferadresse (a)

-   Kundenbestellnummer (a)

-   Kundenbestelldatum (a)

-   Versandart (a)

-   Lieferscheinnummer (a)

-   Lieferscheindatum (a)

-   Lieferschein gedruckt (ac)

-   Rechnungsnummer (a)

-   Rechnungsdatum (a)

-   Auftragsnummer (a)

-   Filiale (a)

-   Auftragsdatum (a)

-   Auftragsart (a)

-   nur bei Serviceauftragsarten:

-   Einsatzdatum

-   Einsatztechniker

-   Selektionskriterium Faktura (c)

-   Zustandskennzeichen (a)

-   Jobnummer (a)

-   Versanddaten Duplikatdruck

-   nur einzugeben, wenn Extramenüpunkt „Duplikat drucken" aktiv ist

-   Druckkennzeichen Lieferschein (d)

-   Vorschlag = "d"

-   (d)rucken

-   (f)axen

-   (e)mail

-   nur wenn Druckkennzeichen Fax oder E-Mail ausgewählt:

-   Kommunikationsarten und -nummern des Kunden, welche dem ausgewählten
    > Kommunikationsartenkennzeichen entsprechen (d)

-   Kommunikationsnummer

    **Teilbereich "Produktion"**

-   Nur bei Auftragsart "Produktion" sichtbar

-   Artikelnummer (a)

-   Artikelmatchode (a)

-   Lagerkennzeichen (a)

-   Artikelinfotext (a)

-   Lagernummer (a)

-   produzierte Menge (a)

-   Einstandspreis (a)

-   Einstandswert (a)

#### Register "Ware unterwegs"

-   Nur bei Auftragsart (\'i%\' oder \'gk\') und vrech_nr = 0 (noch
    nicht zugebuchte Umbuchungsaufträge bzw. Kundenretouren)

-   Liste über Daten aus vlfs_pos_wu

-   Zeile löschen wird nicht erlaubt, wenn danach für jede Kombination
    Lieferscheinposition und Charge zumindest eine Zeile in der Liste
    vorhanden ist.

-   Zeile Einfügen

-   kopiert den Inhalt der aktuellen Zeile in die neue Zeile, die Menge
    > der neuen Zeile wird 0

-   Beim Speichern wird überprüft:

-   für jede Kombination Lieferscheinposition und Charge muss die
    > Mengensumme in der Liste gleich der entsprechenden Mengensumme der
    > Lieferscheinposition sein

-   Auftragspositionsnummer (a)

-   Artikelnummer (a)

-   Artikelmatchcode (a)

-   Chargen / Gerätenummer (a)

-   Menge

-   nur eingebbar, wenn für die aktuelle Kombination
    > Lieferscheinposition und Charge mehr als eine Zeile in der Liste
    > vorhanden ist

-   muss positiv sein

-   ist die aktuelle Zeile gerade vorher durch kopieren hervorgegangen,
    > wird die eingegebene Menge von der Menge der Zeile, von der
    > Kopiert worden ist, abgezogen.

-   Listbox Lagerorte (d)

-   aktiv, wenn Lagerstand auf Lagerortebene geführt wird (lt.
    > auf_pos.ziel_lag_cd)

-   definiert Lagerort

-   folgende Felder im Auswahlfenster:

-   Lagerort

-   Lagerort

-   aktiv, wenn Lagerstand auf Lagerortebene geführt wird und der
    > Lagerort editierbar ist

#### Register "Service- Text"

-   Nur bei Service- Auftragsarten sichtbar

-   kann geändert werden, wenn der Lieferschein noch nicht fakturiert
    ist

-   Textstelle (d)

-   Arbeitsberichtanfangstext für den aufzubauenden Arbeitsbericht

-   Arbeitsberichtendtext für den aufzubauenden Arbeitsbericht

-   Text

-   Fettdruck (c)

-   Unterstreichung (c)

-   Kennzeichen Text auf Rechnung Drucken (c)

-   nur bei Fehlertext und Arbeitsberichtstexten eingebbar, sonst nein

#### Register "Belegkette"

-   siehe unter Allgemeines Abfrageregister "Belegkette"

#### Auswahlpunkte im Menü "Extras" 

-   Lieferschein drucken

-   nur wenn Kennzeichen gedruckt auf "n" gestellt und DruckJobNr
    > ungleich 0

-   Duplikat drucken

-   nur wenn Kennzeichen gedruckt auf "j" gestellt ist

-   Benutzer erhält Kontrolle, Duplikatdruck wird ausgelöst, wenn
    > Benutzer speichert

-   zurücksetzen Druckkennzeichen

-   nur wenn Kennzeichen gedruckt auf "j" und Berechtigung vorhanden

-   Lieferschein einsehen

-   abhängig von Schalter wird Dokument mit AcrobatReader oder mittels
    > AusdruckFenster geöffnet

-   Ware unterwegs zubuchen

-   nur aktiv wenn Auftragsart = \'i%\' und vrech_nr = 0

-   siehe Funktionalität vlfs Gegenlager Buchung in db.doc

-   Es wird geprüft, ob bei einem Lager mit Lagerorten alle Lagerorte
    > eingegeben wurden

-   für Auftragsart "i%" erfolgt bei unterschiedlichen DuEst-Gruppen
    > von Abgangslager und Ziellager eine Neuberechnung des gleitenden
    > Durchschnittspreises

#### Schaltflächen für Verzweigungen

-   Lieferscheinposition

-   Lieferscheinkorrektur

-   Auftragsposition im Verarbeitungsmodus "Lieferscheinkorrektur"

-   nur aktiv, wenn Rechnungsnummer = 0

-   Lagerbewegungen

-   bei Auftragsart "Produktion" aktiv

-   bei Servicelieferschein aktiv, wenn Gerät über Reparaturabschluss
    > ausgeschieden wurde

-   Versand

-   Es werden die Versand-Aufträge für den Lieferschien aufgerufen

-   Bei Rechnung=Lieferbeleg erfolgt die Anzeige für die Rechnungsbelege

-   Dokumente

### Lieferscheinposition

**Allgemeines**

-   Fenster dient zur Abfrage der Ausgangslieferscheinpositionen, es
    können jedoch keine Änderungen durchgeführt werden

#### Auswahldialog

-   Firma

-   Lieferscheinnummer

-   Lieferscheindatum

-   Rechnungsnummer

-   Rechnungsdatum

-   Kundennummer (f)

-   Kundenmatchcode

-   Auftragsnummer

-   Positionsnummer

-   Auftragsdatum

-   Auftragsart (w)

-   Artikelnummer (f)

-   Kundenbestelldatum

-   Kundenbestellnummer

-   Bestellart (w)

-   Sachbearbeiterkennzeichen

-   DDS-Referenznuzmmer (f)

#### Register "Liste"

-   Firma

-   Filiale

-   Lieferscheinnummer

-   Lieferscheindatum

-   Rechnungsnummer

-   Rechnungsdatum

-   Kundennummer

-   Kundenmatchcode

-   Artikelnummer

-   Artikelmatchcode

-   Positionskennzeichen

-   gelieferte Menge

-   Mengeneinheit

-   Verkaufspreis Lieferscheinposition

-   Währungscode Lieferschein

-   Rabatt 1

-   Rabatt 2

-   Rabatt 3

-   Rabatt 4

-   Rabatt 5

-   Lieferscheinwert Position

-   Wareneinsatz (s)

-   DUEST

-   DB-%

-   DB-absolut

-   Sachbearbeiterkennzeichen

-   Auftragsnummer

-   Positionsnummer

-   Auftragsart

-   Auftragsdatum

-   Kundenbestellnummer

-   Kundenbestelldatum

-   Lagernummer

-   Gegenlagernummer

-   Verrechnungsart Service

-   Wartungsvertragsnummer + Positionsnummer

-   DDS-Referenznummer

-   DDS-Prüfnummer

#### Register "Belegkette"

-   siehe unter Allgemeines Abfrageregister "Belegkette"

#### Schaltflächen für Verzweigungen

-   Lagerbewegungen

-   Lagerbewegungen Gegenlager

### Verkaufsposition

**Allgemeines**

-   Fenster dient zur Abfrage der Ausgangslieferscheinpositionen und der
    Kassenbarverkaufpositionen (Bons), es können jedoch keine Änderungen
    durchgeführt werden

#### Auswahldialog

-   Firma

-   Belegart

-   (k)assenbon

-   (l)ieferschein

-   Belegnummer

-   Lieferscheinnummer

-   Bonnummer

-   Belegdatum

-   Lieferscheindatum

-   Bondatum

-   Kassanummer

-   0 bei Belegart "l"

-   Rechnungsnummer

-   Bonnummer bei Belegart "k"

-   Rechnungsdatum

-   Bondatum bei Belegart "k"

-   Kundennummer (f)

-   Kundenmatchcode

-   Auftragsnummer

-   Bonnummer bei Belegart "k"

-   Positionsnummer

-   Auftragsdatum

-   Bondatum bei Belegart "k"

-   Auftragsart (w)

-   " " bei Belegart "k"

-   Artikelnummer (f)

-   Kundenbestelldatum

-   Bondatum bei Belegart "k"

-   Kundenbestellnummer

-   " " bei Belegart "k"

-   Bestellart (w)

-   " " bei Belegart "k"

-   Sachbearbeiterkennzeichen

#### Register "Liste"

-   Firma

-   Filiale

-   Belegart

-   (k)assenbon

-   (l)ieferschein

-   Belegnummer

-   öffnen des Objektes lt. Belegart möglich

-   Lieferscheinnummer

-   Bonnummer

-   Kassanummer

-   Belegdatum

-   Rechnungsnummer

-   Rechnungsdatum

-   Kundennummer

-   Kundenmatchcode

-   Artikelnummer

-   Artikelmatchcode

-   Positionskennzeichen

-   gelieferte Menge (s)

-   Mengeneinheit

-   Verkaufspreis Lieferscheinposition

-   Währungscode Lieferschein

-   Rabatt 1 u 2

-   Lieferscheinwert Position (s)

-   DB-% (s)

-   DB-absolut (s)

-   Sachbearbeiterkennzeichen

-   Auftragsnummer

-   Positionsnummer

-   öffnen des Objektes lt. Belegart möglich

-   Auftragsart

-   Auftragsdatum

-   Kundenbestellnummer

-   Kundenbestelldatum

-   Lagernummer

-   Gegenlagernummer

-   Verrechnungsart Service

-   Wartungsvertragsnummer + Positionsnummer

#### Register "Belegkette"

-   siehe unter Allgemeines Abfrageregister "Belegkette"

-   nur bei Belegart "Lieferschein" verfügbar

#### Schaltflächen für Verzweigungen

-   Lagerbewegungen

-   Lagerbewegungen Gegenlager

-   nicht bei Kassenbons

### Rechnung

**Allgemeines**

-   Fenster dient zur Abfrage der Ausgangsfakturen, es können mit
    Ausnahme der Versanddaten bei Funktionalität "Duplikat drucken"
    keine Änderungen durchgeführt werden

#### Auswahldialog

-   Firma

-   Rechnungsnummer

-   Rechnungsdatum

-   Debitorennummer (f)

-   Rechnungsanschrift Zeile 1

-   Jobnummer

#### Register "Liste"

-   WebdokFunktionalität

-   Firma

-   Rechnungsnummer

-   Rechnungsdatum

-   Debitorennummer

-   Rechnungsanschrift Zeile 1

-   Rechnungsbetrag netto

-   Währungscode

-   Versandfreigabe (c)

-   eingebbar, Logik wie Detail

-   elektronischer Versand (c)

-   eingebbar, Logik wie Detail

-   E-Mail-Adresse

-   eingebbar, Logik wie Detail

-   Erfassungszeitpunkt

#### Register "Detail"

**Teilbereich "Rechnungskopf"**

-   Firma

-   Rechnungsnummer

-   Debitorennummer

-   OP-Debitorennummer

-   Währungscode (a)

-   Rechnungsanschrift

-   Zahlungskonditionen

-   Valutadatum

-   Rechnungsdatum

-   Rechnungsbetrag netto

-   Rechnung gedruckt (ac)

-   Jobnummer (a)

-   Bezugsbelegnummer

-   nur sichtbar, wenn <> Rechnungsnummer

-   Versandfreigabe (c)

-   darf geändert werden, wenn Rechnung noch nicht gedruckt wurde

-   Rechnungsversand (d)

-   Bund (wenn eb_job_snr >= 0)

-   Mail (wenn e_vrech_jn = „j")

-   Druck

-   darf geändert werden, wenn Rechnung noch nicht gedruckt wurde.

-   darf nicht auf „Bund" geändert werdenE-Mail-Adresse

-   darf geändert werden, wenn Rechnung noch nicht gedruckt wurde

-   muss belegt sein, wenn beim Speichern gilt: [e_vrech_jn = "j"]

-   Versanddaten Duplikatdruck

-   nur einzugeben, wenn Extramenüpunkt „Duplikat drucken" aktiv ist

-   Druckkennzeichen Rechnung (d)

-   Vorschlag = "d"

-   (d)rucken

-   (f)axen

-   (e)mail

-   Es wird die E-Mail Adresse für den Rechnungsversand lt. Debitorals
    > Kommunikationsnummer vorgeschlagen

-   nur wenn Druckkennzeichen Fax oder E-Mail ausgewählt:

-   Kommunikationsnummern des Debitoren, sowie der Kunden lt.
    > Lieferscheine, welche dem ausgewählten Druckkennzeichen
    > entsprechen (d)

-   Kommunikationsnummer

-   Stornodatum für Stornorechnung

-   nur einzugeben, wenn Extramenüpunkt „Stornorechnung erstellen" aktiv
    > ist

-   Bei einer Storonrechnung wird hier das aktuelle Datum vorgeschlagen
    > und kann vor dem Speichern noch geändert werden.  
    > Wenn das Rechnungsdatum jedoch nicht im aktuellen Monat ist, so
    > erfolgt zuvor noch ein TE: "Datum Stornorechnung liegt nicht in
    > derselben Buchungsperiode wie die Origanalrechnung -- trotzdem
    > beibehalten?"

**Teilbereich "Ust-Daten"**

Anzeigeliste mit den Ust-Kontierungen der Faktura

-   Ust-Code

-   Ust-Prozentsatz

-   Ust-Basis

-   Umsatzsteuer

-   Bruttobetrag

#### Register "Belegkette"

-   siehe unter Allgemeines Abfrageregister "Belegkette"

-   nur für Lieferscheinpositionen, für Bonpositionen keine Anzeige

#### Auswahlpunkte im Menü "Extras" 

-   Rechnung drucken

-   nur wenn Kennzeichen gedruckt auf "n" gestellt und DruckJobNr
    > ungleich 0

-   Duplikat drucken

-   nur wenn Kennzeichen gedruckt auf "j" gestellt ist

-   Benutzer erhält Kontrolle, Duplikatdruck wird ausgelöst, wenn
    > Benutzer speichert

-   zurücksetzen Druckkennzeichen

-   nur wenn Kennzeichen gedruckt auf "j" und Berechtigung vorhanden

-   das Druckkennzeichen für Kopien wird ebenfalls auf "n"
    > zurückgesetzt

-   setzt ggf. Feld vrech.eb_job_snr = 0 (wenn > 0 oder -1 und
    > vrechausart.sst_kz <> "-") (Prüfung mit wf_Yes)

-   alle Rechnungen drucken

-   Aufgabe Rechnungsdruck für alle Rechnungen für die gilt:
    > [vrech_gedruckt_jn] = "n", [vrech_dfrei_jn] = "j" und
    > [vrech_dat] > {Tagesdatum - 90}

-   Rechnung einsehen

-   abhängig von Schalter wird Dokument mit AcrobatReader oder mittels
    > AusdruckFenster geöffnet

-   Stornorechnung erstellen

-   Nur enabled, wenn lt. gf_initapplenv Parameter erlaubt

-   Nicht erlaubt bei Stornorechnungen (Kein Storno vom Storno)

-   Nicht erlaubt bei Jetfibu-Integration

-   Benutzer erhält Kontrolle, Stornojob wird ausgelöst, wenn Benutzer
    > speichert

#### Schaltflächen für Verzweigungen

-   Lieferscheinkopf

-   Lieferscheinposition

-   OP Abfrage

-   mit konstanter Bezugsbelegnummer

-   mit OP-Debitor

-   Zahlungen

-   Nur verfügbar wenn Kassen-Modul aktiviert ist

-   Aufruf aller Kassenbeleg, die eine Zahlung zu dieser Rechnung sind

-   Dokumente

### OP-Abfrage

-   WebdokFunktionalität

### Auftragsbestätigung, Offert, Proforma

Listbild:

[ab.doc](file:///\\pcssrv019\projekte\tradecon\org\ab.doc)

Aufruf:

Werteingaben:

-   Auftragsnummer (Eingang)

-   Firmennummer

Seitenkopf:

-   Logo (sofern vorhanden)

-   Rechnungsanschrift [vrech.debitor_name1 bis vrech.debitor_ort]

-   UID-Nummer wenn vorhanden

-   Lieferanschrift [auf.kunde_name1 bis auf.kunde_ort]

-   Fixtext "AUFTRAGSBESTÄTIGUNG" oder "PROFORMARECHNUNG" bzw.
    "ANGEBOT" abhängig von Auftragsart

-   Auftragsnummer (Eingang)

-   Tagesdatum

-   Kundennummer

-   Fixtext "Ihre Bestellung" bzw. "Ihre Anfrage" abhängig von
    Auftragsart

-   Kundenbestelldatum

-   Kundenbestellnummer (wahre Länge)

-   Besteller (wahre Länge)

-   Anrede "Hr. " bzw. "Fr." lt. [auf.kunde_pers_cd
    > adr_pers.geschlecht_kz]

-   Nachname lt. [auf.kunde_pers_cd adr_pers.n_name]

-   Sachbearbeiter Vor- und Nachname [adr_pers.v_name, n_name]

-   Versandart [versart.versart_bez]

-   Lieferbedingung [liefbed.liefbed_bez]

-   Auftragsrabatt, wenn ungleich 0

-   Seitennummer und Seitenanzahl

Auf der 1. Seite vor den Positionen:

-   Anfangstextzeilen lt. [fa.ab_a_txt_cd txt_txt.txt_txt]

-   Auftragsbestätigungstext Einleitung [auf_txt]

Positionsüberschrift je Seite:

-   Fixtexte lt. Listbild

-   "Preis inkl" bzw. "Preis" abhängig von Inklusivpreiskennzeichen

-   Währungscode

**Pro Positionsüberschrift:**

-   Druck Überschriftstext

-   auf_ueb_txt.{off\|ab}_jn="j"

-   ggf. neue Seite

Pro Auftragsposition

unter Berücksichtigung des Set-Druckkennzeichens:

-   Artikelnummer

-   Artikelbezeichnung und sonstige Texte lt. [auf_pos_txt]

-   offene Menge (wenn ganzzahlig ohne Nachkomma)

-   Mengeneinheit [eh_sprache.druck_eh_txt]

    unter Berücksichtigung des Set-Preisdruckkennzeichens:

-   Verkaufspreis

-   Positionsbetrag

-   nur wenn Verkaufspreis nicht per 1 bzw. Verkaufspreismengeneinheit
    nicht gleich Verkaufseinheit:

-   Fixtext "per"

-   Menge für die sich der Verkaufspreis versteht

-   Verkaufspreismengeneinheit

-   Positionsrabatt 1, wenn ungleich 0

-   Positionsrabatt 2, wenn ungleich 0

-   Fixtext "Liefertermin" + Liefertermintext, wenn nicht leer

Nach der Positionsüberschrift:

-   wenn Überschriftensumme gewünscht [summe_jn = "j"]

-   Druck Summentext lt. Überschrift

-   Druck Summenbetrag exkl. USt

-   wenn auf die Überschrift eine Ust entfällt

-   UstKennzeichen Druck <> "" oder UstProzentsatz <> 0

-   Pro Ustkennzeichen und Prozentsatz

-   UstProzentsatz

-   Fixtext "% Ust"

-   UstBetrag

-   Ustkennzeichen

-   Fixtext "Summe inkl."

-   Summenbetrag inkl. USt

Nach der letzten Position:

-   Trennlinie

-   bei Auftragsbestätigung und Proformarechnung immer, bei Offerten nur
    wenn Endsumme gewünscht:

-   Druckvariante ohne USt:

-   Währungscode

-   Fixtext "inkl" bzw. "exkl" abhängig von Inklusivpreiskennzeichen

-   Endbetrag

-   Druckvariante mit USt:

-   Währungscode

-   Rechnungsendbetrag inkl. Umsatzsteuer

-   je Umsatzsteuercode, wenn Inlandskunde

-   USt-Symbol

-   USt-Prozentsatz

-   USt-Basis

-   USt-Betrag

-   Zahlungskonditionen lt. Formular bzw. Zahlungskonditionstext lt
    [zahlart]

-   Textbaustein lt. Zahlungskonditionstext [zahlart.zahlkond_ab_txt_cd
    txt_txt.txt_txt]

-   USt-Befreiungstext, wenn Binnenmarktkunde

-   Auftragsbestätigungstext Ende [auf_txt]

-   Endetextzeilen lt. [fa.ab_txt_cd txt_txt.txt_txt]

Im Seitenfuß:

-   Logo sofern vorhanden

Auswahl der Daten:

-   auf

-   aufart_cd not in (\'i\', \'p\' )

-   zustand_kz in (\'e\', \'k\', \'r\')

-   auf_pos

-   auf_pos.auf_off_mg <> 0 and auf.auf_nr = auf_pos.ein_auf_nr

Sortierung:

-   Positionsnummer

Update:

-   auf

-   ab_druck_dat

### Kostenvoranschlag, Auftragsbestätigung Reparatur

Listbild:

[kv.doc](file:///\\pcssrv019\projekte\tradecon\org\kv.doc)

Aufruf:

Werteingaben:

-   Auftragsnummer (Eingang)

-   Firmennummer

Seitenkopf:

Daten wie AB, Ausnahmen:

-   Fixtext "KOSTENVORANSCHLAG" bzw. "AUFTRAGSBESTÄTIGUNG" abhängig
    von Auftragsart

Auf der 1. Seite vor den Positionen:

[pro Datensatz in [s_auf_geraet]]{.underline}

**Gruppe pro Artikel**

-   Artikelnummer Gerät

-   Artikelbezeichnung Gerät

-   artik_txt.rech_jn = "j"

-   Gerätenummer

-   s_auf.s_geraet_dr

-   Fehlerbeschreibung

-   Einleitungstext lt. Firmenstamm

-   für Kostenvoranschlag

-   Individueller Einleitungstext lt. Auftrag

-   Servicetext mit s_auf_wo_kz = "ka", bei Kostenvoranschlag

-   Auftragstext mit ab_jn = "j", bei Auftragsbestätigung

Positionsüberschrift je Seite:

Daten wie AB

Pro Auftragsposition

Daten wie AB

Nach der letzten Position:

Daten wie AB, Ausnahmen:

-   Individueller Schlusstext lt. Auftrag

-   Servicetext mit s_auf_wo_kz = "ke", bei Kostenvoranschlag

-   Auftragstext mit ab_jn = "j", bei Auftragsbestätigung

-   Schlusstext lt. Firmenstamm

-   für Kostenvoranschlag bzw. AB, abhängig von Auftragsart

Im Seitenfuß:

-   Logo sofern vorhanden

Auswahl der Daten:

-   auf

-   aufart_cd not in (\'i\', \'p\' )

-   zustand_kz in (\'e\', \'k\', \'r\')

-   auf_pos

-   auf_pos.auf_off_mg <> 0 and auf.auf_nr = auf_pos.ein_auf_nr

Sortierung:

-   Positionsnummer

Update:

-   auf

-   ab_druck_dat

### Kommissionsscheindruck

Werteingaben:

-   Auftragsnummer (Abwicklungsauftrag)

-   Firmennummer

Auswahl der Daten:

-   freigegebene Menge <> 0

-   Kommissionsscheinnummer = 0

-   Keine Verrechnungsartikel

Listbild:[kommsch.doc](\\\\pcssrv019\\projekte\\tradecon\\org\\kommsch.doc)

Seitenkopf:

-   Auftragsnummer (Abwicklungsauftrag)

-   Kommissionsnummer

-   Firmenkurzbezeichnung [fa.fa_adr_snr adr.adr_mc]

-   Tagesdatum

-   Uhrzeit

-   Seitennummer und Seitenanzahl

-   Lieferanschrift [auf.kunde_name1 bis auf.kunde_ort]

-   Auftragsdatum

-   Auftragsart

-   Auftragsartkurzbezeichnung [aufart.aufart_mc]

-   Kundennummer

-   Kundenbestellnummer und -datum

-   Sachbearbeiter Vor- und Nachname [erf_adr_pers.v_name, n_name]

-   Versandart [versart.versart_bez]

-   Lieferbedingung [liefbed.liefbed_bez]

-   Kommissionsbereich

Auf der 1. Seite vor den Positionen:

-   Anfangstextzeilen lt. [aufart.komm_a_txt_cd txt_txt.txt_txt]

-   Kommissionsscheintext Einleitung [auf_txt]

-   eine Zeile je Kommissionsschein des aktuellen Auftrages (aktueller
    ausgenommen)

-   Kommissionsscheinnummer

-   Kommissionsscheindatum

-   Kommissionsbereich

Auf der 1. Seite vor den Positionen nur bei Produktionsauftrag:

-   Lagercode:

-   Lagermatchcode

-   Lagerort

-   wenn lag.lag_ort_inp_jn = \'n\': [artik_lag.inp_n_lag_ort]

-   Artikelnummer

-   Textzeilen des Artikels, welche auf dem Kommissionsschein gedruckt
    werden

-   freigegebene Menge [auf­_prod.prod_frei_mg]

-   Mengeneinheit [artik.veh_cd]

-   Fixtext "___" zum Eintrag eines Vermerkes, nicht bei Geräte-
    oder Chargenartikeln [artik.lag_kz in (\'c\' , \'g\')] und bei
    Lagerortführung [lag.lag_ort_inp_jn = \'j\']

-   Liste mit einer Zeile Pro AuftragsProduktionSub, bei (Geräte- oder
    Chargenartikeln und Lager ist Chargen-/Gerätelager) oder bei
    Lagerortführung

-   Lagerort

-   Fixtext lt. Listbild + Geräte / Chargen- Nummer

-   nur wenn Lager Chargen-/Gerätelager ist

-   Menge [prods_frei_mg], nicht bei Geräten

-   Fixtext "___" zum Eintrag eines Vermerkes

> Sortierung:

-   Lagerort

-   Seriennummer/Chargennummer

-   Wenn obige Liste leer ist, werden bei Seriennummernartikeln
    [prod_frei_mg] Zeilen und wird bei Chargenartikeln eine Zeile
    lt.Listbild gedruck.

-   nur wenn Lager Chargen-/Gerätelager ist

Positionsüberschrift je Seite:

Laut Listbild.

Gruppenüberschrift Pro Lager:

-   Lagercode:

-   auf_pos.geg_lag_cd bei auf_art_cd = \'kr\'

-   auf_pos.lag_cd sonst

-   Lagermatchcode

Pro Auftragsposition und Lagerort:

Anmerkung Programmierung: Dies ist das Detail- Band im nested DW (=
Positionsreport).

-   Positionsnummer

-   Laufende Nummer, wird beim Druck vergeben und in auf_pos abgestellt.

-   wird nur beim jeweils ersten Vorkommnis einer Auftragsposition
    > vergeben (-> inkrementiert). Bei allen weiteren Vorkommnissen
    > wird die Nummer des ersten Vorkommnisses gedruckt.

-   Lagerort

-   nicht beim Set- Hauptartikel

-   der Lagerort aus auf_pos_sub, wenn lag.lag_ort_inp_jn = \'j\'

-   [geg_lag_ort] bei auf_art_cd = \'kr\'

-   [lag_ort sonst]

-   [artik_lag.inp_n_lag_ort] sonst

Die restlichen Werte dieses Blocks werden nur beim ersten Vorkommnis
einer Auftragsposition gedruckt:

-   Artikelnummer

-   Textzeilen, welche auf dem Kommissionsschein gedruckt werden

-   freigegebene Menge [auf­_pos.auf_frei_mg]

-   Mengeneinheit [artik.veh_cd]

Die restlichen Werte dieses Blocks werden beim Sethauptartikel nicht
gedruckt:

-   Fixtext "___" zum Eintrag eines Vermerkes, nicht bei Geräte-
    oder Chargenartikeln [artik.lag_kz in (\'c\' , \'g\')] und bei
    Lagerortführung [lag.lag_ort_inp_jn = \'j\']

-   Positionsnummer (lt. 1. Spalte) des Sethauptartikels bei
    Setbestandteilen

-   Liste mit einer Zeile Pro AuftragspositionSub, bei Geräte- oder
    Chargenartikeln und bei Lagerortführung

-   Lagerort

-   [geg_lag_ort] bei [auf_art_cd] = \'kr\'

-   [lag_ort] sonst

-   Fixtext lt. Listbild + Geräte / Chargen- Nummer

-   Menge [aufs_frei_mg], nicht bei Geräten

-   Fixtext "___" zum Eintrag eines Vermerkes

> Sortierung:

-   Lagerort

-   Seriennummer/Chargennummer

-   Wenn obige Liste leer ist, werden bei Seriennummernartikeln
    [auf_frei_mg] Zeilen und wird bei Chargenartikeln eine Zeile
    lt.Listbild gedruck.

Nach der letzten Position:

-   Kommissionsscheintext Ende [auf_txt]

-   Endetextzeilen lt. [aufart.komm_txt_cd txt_txt.txt_txt]

Sortierung :

-   Firma

-   Auftragsnummer

-   Kommissionsbereich

-   bei Wechsel neuer Beleg

-   Lagernummer

-   Lagerplatz

-   Artikelnummer

Update:

-   auf

-   auf_pos

-   auf_komm

#### Vorbereitung MDE-Kommissionierung

Wenn lt. Kommissionsbereich die MDE Kommissionierung aktiviert ist, so
wird zusätzlich ein Kommissionsvorgang aufgebaut.

-   Ist momentan nur möglich, wenn für alle lagerführenden freigegebenen
    Positionen auch die auf_pos_sub Daten vorhanden sind.

-   Datenbankkonzept ist für Sammelkommissionierung vorbereitet, die
    Sammelkommissionierung ist aber noch nicht umgesetzt

-   kommvorg

-   kommvorg_bereich (In TC Standard fix 1 Datensatz mit Bereich-Nr. 1)

-   kommvorg_pos

-   Wird für Lagerführende Artikel pro auf_pos_sub Lagerort Eintrag
    > aufgebaut

-   Für diverse Aritkel wir ein Datensatz pro auf_pos mit
    > lag.mde_div_lag_ort erstellt

### Lieferscheinaufbau/Druck

Listbild:[lfs.doc](lfs.doc)  
Aufruf:

Werteingaben:

-   Firmennummer (p)

-   Auftragsnummer

Seitenkopf:

-   Logo (sofern vorhanden)

-   Lieferanschrift [auf.kunde_name1 bis auf.kunde_ort]

-   Belegtitel für Lieferschein [aufart.lfs_beleg_txt]

-   Lieferscheinnummer

-   Lieferscheindatum

-   Kundennummer

-   Auftragsnummer (Abwicklung)

-   Sachbearbeiter Vor- und Nachname [adr_pers.v_name, n_name]

-   Versandart [versart.versart_bez]

-   Lieferbedingung [liefbed.liefbed_bez]

-   Seitennummer und Seitenanzahl

Auf der 1. Seite vor den Positionen:

-   Liefer-Telefonnummer

-   Anfangstextzeilen lt. [aufart.lfs_a_txt_cd txt_txt.txt_txt]

-   Lieferscheintext Einleitung [auf_txt]

Positionsüberschrift je Seite:

Abhängig von [auf.vklfs_preis_jn] werden die
Positionsüberschriftstexte

-   "ArtNr" bis "Betrag " + vlfs.waehrung_cd

    bzw.

-   "ArtNr" bis "Eh"

    gedruckt

Enthält der Auftrag Inklusivpreise, wird der Text

-   "Preis inkl"

    ansonsten

-   "Preis"

    gedruckt

Nur bei Produktionsaufträgen:

-   Fixtext

-   Artikelnummer

-   Artikelbezeichnung lt. [artik_txt]

-   Menge (wenn ganzzahlig ohne Nachkomma)

-   Mengeneinheit [artik.veh_cd]

-   Chargen- bzw. Gerätenummernblock wie im Positionsbereich

-   nur, wenn es ein Chargen-/Gerätelager ist

Pro Auftrag (Eingang) von dem geliefert wird:

-   Fixtext

-   Kundenbestellnummer (wahre Länge)

-   Kundenbestelldatum

-   Besteller (wahre Länge)

-   Anrede "Hr. " bzw. "Fr." lt. [auf.kunde_pers_cd
    > adr_pers.geschlecht_kz]

-   Nachname lt. [auf.kunde_pers_cd adr_pers.n_name]

-   Auftragsnummer (Eingang)

-   Auftragskopfrabatt, wenn ungleich 0

Pro Position mit Liefermenge:

-   unter Berücksichtigung des Set-Druckkennzeichens:

-   Artikelnummer

-   Artikelbezeichnung und sonstige Texte lt. [auf_pos_txt]

-   Menge (wenn ganzzahlig ohne Nachkomma)

-   Mengeneinheit [eh_sprache.druck_eh_txt]

-   Bei Artikel mit Lagerkennzeichen "Gerät" je Seriennummer aus
    AuftragspositionSub:

-   Fixtext "SerienNr:"

-   Gerätenummer

-   nur, wenn es ein Chargen-/Gerätelager ist

-   Bei Artikel mit Lagerkennzeichen "Charge" je Chargennummer aus
    AuftragspositionSub:

-   Fixtext "Charge:"

-   Chargennummer

-   Summe der Freigabemengen lt. [auf_pos_sub]

-   nur, wenn es ein Chargen-/Gerätelager ist

-   Bei Aufträgen mit Lieferscheinauspreisung unter Berücksichtigung von
    Set-Preisdruckkennzeichen:

-   Verkaufspreis aus Lieferscheinposition

-   Positionsbetrag

-   nur wenn Verkaufspreis nicht per 1 bzw. Verkaufspreismengeneinheit
    > nicht gleich Verkaufseinheit:

-   Fixtext "per"

-   Menge für die sich der Verkaufspreis versteht

-   Verkaufspreismengeneinheit

-   Positionsrabatt 1, wenn ungleich 0

-   Positionsrabatt 2, wenn ungleich 0

-   Wenn die DDS-Referenznummer belegt ist

-   DDS-Referenznummer

-   DDS-Prüfnummer

Nach der letzten Position mit Liefermenge:

-   Trennlinie

-   Bei Aufträgen mit Lieferscheinauspreisung:

    Enthält der Auftrag Inklusivpreise

-   "Lieferwert inkl USt"

    ansonsten

-   "Lieferwert exkl USt"

-   Lieferwert

Rückstandsblock:

nur wenn [auf.rueck_dru_jn = \'j\']:

-   unter Berücksichtigung des Set-Druckkennzeichens:

-   Positionen mit offener Menge [vlfs_pos.off_mg_kz = \'r\']:

-   Positionsüberschrift " ... werden nachgeliefert"

-   Artikelnummer

-   Artikeltextzeilen wie oben, jedoch nicht die Zolltarifnummernzeile
    > die Artikeltextzeilen [auf_pos_txt_kz <> \'z\']

-   offene Menge

-   Mengeneinheit w.o.

-   Positionen mit offener Menge welche keine Auslaufartikel sind
    [vlfs_pos.off_mg_kz = \'n\']

-   Positionsüberschrift " ... bitte neu bestellen"

-   sonst w.o.

-   Positionen mit gelöschter Menge welche Auslaufartikel sind
    [vlfs_pos.off_mg_kz = \'a\']

-   Positionsüberschrift " ... nicht mehr lieferbar"

-   sonst w.o.

Nach den Positionen:

-   Lieferscheintext Ende [auf_txt]

-   Endetextzeilen lt. [aufart.lfs_txt_cd txt_txt.txt_txt]

Im Seitenfuß:

-   Logo sofern vorhanden

Auswahl der Daten:

-   siehe vlfs-Aufbau

Sortierung:

-   gelieferte Positionen

-   Auftragsnummer Eingang

-   Positionsnummer

-   Seriennummer/Chargennummer

Rückstandsblock

-   Meldeart (siehe oben)

-   Artikelnummer

    **Besonderheit "interne Umbuchung" und
    "Kommissionsbelieferung"**

    DUEST Berechnung

-   erfolgt nicht bei Kommissionsretoure (kr) oder Kundenretoure (gk)

-   erfolgt nicht, wenn das Gegenlager ein "Ware-Unterwegs-Lager" ist

-   handelt es sich beim Gegenlager um eine andere DuEst-Gruppe (=
    abweichendes Lagerkennzeichen oder abweichende DuEst-Gruppe)

    **Besonderheit "Lieferantenretoure"**

-   Eingangslieferschein Lieferant wird aufgebaut

-   Kopfdaten werden in eigenem Event belegt, folgende Standardwerte

-   Lieferant lt. Auftrag

-   Firma und Filiale lt. Auftrag

-   Eingangslieferscheindatum Lieferant = Verkaufslieferscheindatum

-   Eingangslieferscheinnummer Lieferant = Verkaufslieferscheinnummer

-   Positionsdaten werden in eigenem Event belegt, folgende
    Standardwerte lt. Auftrag

-   Artikelnummer

-   Artikelmatchcode

-   bei diversen Artikeln

-   Einkaufseinheit

-   Einkaufspreis pro Menge

-   Texte lt. Auftragsposition

-   Liefermenge (Vorzeichen gedreht)

-   Lagerdaten (kartei_lagbew) müssen aus artik_lag_sub übernommen
    > werden  
    > Die Lieferscheinposition selbst darf keine Lagerbuchung
    > durchführen muss aber die Reservierung rückgängig machen.

-   Der Bezug zum Eingangslieferschein wird in der vlfs_pos verspeichert
    > und beim Lieferscheindruck muss die Kartei_snr der
    > Eingangslieferscheinposition zum Andurck der Chargen/Gerätedaten
    > verwendet werden.

### Rechnungsaufbau/Druck

Listbild:

[fakt.doc**  
**](file:///\\pcssrv019\projekte\tradecon\org\fakt.doc)

Aufruf:

Werteingaben:

-   Firmennummer (p)

-   Debitorennummer

-   Kundennummer

-   Lieferscheinnummer

-   Lieferscheindatum

-   Auftragsnummer

-   Fakturenart (w)

-   Fakturenintervall (w)

-   Lieferscheine freigegeben

-   Rechnungsdatum (p)

-   muss im Periodenbereich lt. Firmenstamm liegen

-   Prüfung im Batchprogramm, wenn Datum nicht gültig, Ausgabe
    > Fehlermeldung in Job

Seitenkopf:

-   Logo (sofern vorhanden)

-   Rechnungsanschrift [vrech.debitor_name1 bis vrech.debitor_ort]

-   UID-Nummer wenn vorhanden

-   Fixtext "RECHNUNG" bei positivem Endbetrag, bzw. "GUTSCHRIFT"
    bei negativem Endbetrag

-   Rechnungsnummer

-   Rechnungsdatum

-   Debitorennummer

-   wenn Lieferschein=Rechnung:

-   Auftragsnummer Abwicklungsauftrag

-   Sachbearbeiter Vor- und Nachname [adr_pers.v_name, n_name]

-   Versandart [versart.versart_bez]

-   Lieferbedingung [liefbed.liefbed_bez]

-   Liefer Telefonnummer wenn ausgefüllt

-   Seitennummer und Seitenanzahl

Auf der 1. Seite vor den Positionen:

-   Anfangstextzeilen

-   [fa.bv_a_txt_cd txt_txt.txt_txt], wenn Barverkauf

-   [fa.gu_a_txt_cd txt_txt.txt_txt], wenn Betrag < 0

-   [fa.lfsfakt_a_txt_cd txt_txt.txt_txt], wenn Lieferschein=Rechnung

-   [fa.fakt_a_txt_cd txt_txt.txt_txt], sonst

    nur wenn durch das Rechnungskennzeichen gewährleistet wird, dass es
    nur einen Abwicklungsauftrag gibt:

-   Rechnungstext Einleitung [auf_txt]

Positionsüberschrift je Seite:

-   "Preis inkl" bzw. "Preis" abhängig von Inklusivpreiskennzeichen

-   Währungscode

Pro Lieferschein:

nur wenn durch das Rechnungskennzeichen gewährleistet ist, dass ein
Lieferschein gedruckt wurde:

-   Fixtext

-   Lieferscheinnummer lt. vlfs.druck_vlfs_nr

-   Lieferscheindatum lt vlfs.druck_vlfs_dat

Pro Auftrag (Eingang):

-   Fixtext

-   Kundenbestellnummer (wahre Länge)

-   Kundenbestelldatum

-   Besteller (wahre Länge)

-   Anrede "Hr. " bzw. "Fr." lt. [auf.kunde_pers_cd
    > adr_pers.geschlecht_kz]

-   Nachname lt. [auf.kunde_pers_cd adr_pers.n_name]

-   Auftragsnummer (Eingang)

-   Auftragskopfrabatt, wenn ungleich 0

Pro Position:

unter Berücksichtigung des Set-Druckkennzeichens:

-   Artikelnummer

-   Artikelbezeichnung und sonstige Texte lt. [auf_pos_txt]

-   Menge (wenn ganzzahlig ohne Nachkomma)

-   Mengeneinheit [eh_sprache.druck_eh_txt]

-   Bei Artikel mit Lagerkennzeichen "Gerät" je Seriennummer aus
    Lagerbewegungskartei

-   Fixtext "SerienNr:"

-   Gerätenummer

-   nur, wenn es ein Chargen-/Gerätelager ist

-   Bei Artikel mit Lagerkennzeichen "Charge" je Chargennummer aus
    Lagerbewegungskartei

-   Fixtext "Charge:"

-   Chargennummer

-   Summe der Buchungsmengen lt. [kartei_lagbew]

-   nur, wenn es ein Chargen-/Gerätelager i

    unter Berücksichtigung des Set-Preisdruckkennzeichens

-   Verkaufspreis aus Lieferscheinposition

-   Positionsbetrag

-   USt-Symbol, wenn Inlandskunde

-   nur wenn Verkaufspreis nicht per 1 bzw. Verkaufspreismengeneinheit
    nicht gleich Verkaufseinheit:

-   Fixtext "per"

-   Menge für die sich der Verkaufspreis versteht

-   Verkaufspreismengeneinheit

-   Positionsrabatt 1, wenn ungleich 0

-   Positionsrabatt 2, wenn ungleich 0

Nach der letzten Position:

-   Trennlinie

-   Währungscode

-   Rechnungsendbetrag inkl. Umsatzsteuer

-   Bei Barverkaufsrechnungen

-   Skontoprozentsatz 1

-   Skontobetrag

-   Zahlungsbetrag

-   je Umsatzsteuercode, wenn Inlandskunde

-   USt-Symbol

-   USt-Prozentsatz

-   USt-Basis

-   USt-Betrag

-   wenn doppelte Preisauszeichnung aktiviert

-   Belegwährung ist EUR

-   Rechnungsendbetrag in ATS

-   Belegwährung ist nicht EUR

-   Rechnungsendbetrag in EUR

-   wenn nicht Barverkaufsrechnung:

-   Zahlungskonditionen lt. Formular unter Berücksichtigung der
    > Skontofähigkeit bzw. Zahlungskonditionstext lt [zahlart],

-   Textbaustein lt. Zahlungskonditionstext [zahlart.zahlkond_ab_txt_cd
    > txt_txt.txt_txt]

-   QR-Code für Zahlung über Code lt. Definition [QR-Code und BCD
    > Definitionen 2.pdf](QR-Code%20und%20BCD%20Definitionen%202.pdf)

-   BIC lt. zahlart

-   Empfänger lt. zahlart (die 2x40 Stellen Empfertext für Erlagschein
    > werden auf maximal 70 Stellen zusammengefasst).

-   IBAN lt. zahlart

-   Betrag  
    > Wird wenn kein Skonto in Verwendung ist oder das KZ für die
    > Belegung des Betrages im QR Code lt. Zahlungsart auf Endbetrag
    > steht, wird der Endbetrag verwendet. Sonst lt. KZ der um den
    > Skonto verminderte oder gar kein Betrag.

-   Zahlungsreferenz: Rechnungsnnummer

-   Anzeigetext: "ReNr <verech_nr> vom <Rechnungsdatum
    > dd.mm.yyyy>"

-   USt-Text lt. USt-Tabelle

-   Rechnungstext Ende [auf_txt], Logik w.o.

-   Endetextzeilen

-   [fa.bv_txt_cd txt_txt.txt_txt], wenn Barverkauf

-   [fa.gu_txt_cd txt_txt.txt_txt], wenn Betrag < 0

-   [fa.lfsfakt_txt_cd txt_txt.txt_txt], wenn Lieferschein=Rechnung

-   [fa.fakt_txt_cd txt_txt.txt_txt], sonst

Im Seitenfuß:

-   Logo sofern vorhanden

Auswahl der Daten:

-   siehe vrech-Aufbau

Sortierung:

-   Lieferscheinnummer

-   Auftragsnummer Eingang

-   Positionsnummer

-   Seriennummer/Chargennummer

**Rechnung an den Bund**

Das PDF-File der Rechnung wird aufgebaut und mit dem ApplFkz „bund"
gedruckt. Über die Druckzuordnung kann man damit individuell einstellen,
ob die Rechnung tatsächlich gedruckt werden soll.

Der Job für den Versand wird für die aktuelle Rechnung eingespoolt.

#### Zahlscheindruck

Abhängig vom Erlagschein-Druck KZ der Zahlungsart wird zu der Rechnung
ein Zahlschein Ausgedruckt.

Dabei gibt es folgende Varianten

Alter Zahlschein

-   Format A4 Quer mit Zahlscheine auf der rechten Seitenhälfte
    (Auftragsbestätigung oben, Zahlungsanweisung unten).

Auftragsbestätigung (oben):

-   Bank Bezeichnung lt. Zahlungsart (wenn bereits vorgedruckt, dann
    Textfeld in Zahlungsart leer lassen)

-   Rechnungsendbetrag

-   nur wenn Skonto = 0

-   Kontonummer lt. Zahlungsart

-   Bankleitzahl lt. Zahlungsart

-   2xEmpfängertext lt. Zahlungsart

-   Verwendungszweck:

-   Rechnungsnummer

-   Rechnungsdatum

-   Rechnungsadresse

Zahlschein (unten):

-   Bank Bezeichnung lt. Zahlungsart (wenn bereits vorgedruckt, dann
    Textfeld in Zahlungsart leer lassen)

-   Rechnungsendbetrag

-   nur wenn Skonto = 0

-   Kontonummer lt. Zahlungsart

-   Bankleitzahl lt. Zahlungsart

-   2xEmpfängertext lt. Zahlungsart

-   Verwendungszweck:

-   Debitorennummer

-   Rechnungsnummer

-   Rechnungsdatum

-   Rechnungsadresse

-   Zahlungskonditionen

-   Lesezone (OCR-B)

-   Bezugsbelegnummer (Firmennummer + Rechnungsnnummer 9stellig) +
    > "<"

-   Kontonommer + "+"

-   Bankleitzahl + ">"

-   Bruttowert + "<"

-   Wenn Skonto = 0

-   Zahlschein-KZ lt. Zahlungsart ("40+"

SEPA-Zahlschein A4-Quer

-   Alle Felder werden in OCR-B gedruckt, ausgenommen der
    Verwendungszweck

Auftragsbestätigung (oben):

-   Bank Bezeichnung lt. Zahlungsart (wenn bereits vorgedruckt, dann
    Textfeld in Zahlungsart leer lassen)

-   Empfängertext lt. Zahlungsart (nur 1 Zeile)

-   IBAN lt. Zahlungsart

-   BIC lt. Zahlungsart

-   Rechnungsendbetrag

-   nur wenn Skonto = 0

-   Rechnungsadresse

-   Verwendungszweck:

-   Rechnungsnummer

-   Rechnungsdatum

Zahlschein (unten):

-   Alle Felder werden in OCR-B gedruckt, ausgenommen der
    Verwendungszweck

-   Bank Bezeichnung lt. Zahlungsart (wenn bereits vorgedruckt, dann
    Textfeld in Zahlungsart leer lassen)

-   Empfängertext lt. Zahlungsart (nur 1 Zeile)

-   IBAN lt. Zahlungsart ("+" am Zeileneinde)

-   BIC lt. Zahlungsart

-   Rechnungsendbetrag

-   nur wenn Skonto = 0

-   Bezugsbelegnummer (Firmennummer 3stellige mit Vorlaufnullen +
    Rechnungsnummer 9stellig)

    \+ "+" am Zeilenende

-   Verwendungszweck

-   1.Zeile: (KdNr <DebNr>, ReNr <123456789> vom 12.12.2011)

-   2.Zeile "Bei E-Banking im Feld Kundendaten "001012345678"
    > angeben!"

-   Rechnungsadresse Name 1

-   Wenn Skonto = 0

-   "+"

-   Rechnungsendbetrag + "<"

-   Zahlschein KZ lt. Zahlungsart

SEPA-Zahlschein A4-Hoch

Auftragsbestätigung (links unten schmal) -- kleinere Schrift:

-   Empfängertext lt. Zahlungsart (nur 1 Zeile)

-   IBAN lt. Zahlungsart

-   BIC lt. Zahlungsart

-   Rechnungsendbetrag

-   nur wenn Skonto = 0

-   Bezugsbelegnummer (Firmennummer 3stellige mit Vorlaufnullen +
    Rechnungsnummer 9stellig)

-   Verwendungszweck:

-   Debitorennummer

-   Rechnungsnummer

-   Rechnungsdatum

Die Zahlungsanweisung ist gleich wie bei der A4-Quer Version

### Auftragsbestandsliste nach Kunden

Listbild:

[offaufkd.doc](file:///\\pcssrv019\projekte\tradecon\org\offaufkd.doc)

Aufruf:

Werteingaben:

-   Firmennummer (p)

-   Kundennummer

-   Auftragsart

-   Zustandskennzeichen

-   Lagernummer

-   Lieferwoche

-   Lieferdatum

-   Verarbeitungskennzeichen

-   Alle Artikel

-   nur Artikel mit frei verfügbarer Menge > 0

Seitenkopf:

-   Firmenkurzbezeichnung [fa.fa_adr_snr adr.adr_mc]

-   Tagesdatum

-   Uhrzeit

-   Positionsüberschriftszeile

    **Pro Kunde**

-   Kundennummer

-   Kundenmatchcode

Pro Auftrag (Abwicklung)

-   Auftragsart

-   Auftragsnummer

-   Auftragsdatum

-   Währungscode

-   Kundenbestellnummer

-   Kundenbestelldatum

Pro Auftragsposition

-   Positionsnummer

-   Artikelnummer

-   Positionskennzeichen

-   Lagernummer

-   verfügbarer Bestand des Lagers

-   frei verfügbarer Bestand des Lagers

-   offene Menge

-   Verkaufseinheit

-   Verkaufspreis

-   Rabatt 1

-   Rabatt 2

-   Positionsbetrag in Auftragswährung

-   Lieferwoche

-   Lieferdatum

-   Folgezeile:

-   Artikelmatchcode aus Auftragsposition

-   Auftragsrabatt des Eingangsauftrages wenn ungleich 0

-   wenn Lieferantenbestellnummer ungleich 0:

-   Bestellnummer

-   Bestellposition

-   gelieferte Menge lt. Bestellposition

Summenzeile Kunde

-   Währungscode Grundwährung

-   Auftragswert Kunde in Grundwährung

-   Setpositionen [auf_pos_kz = \'t\'] werden nicht mitgerechnet

Summenzeile Gesamt

-   Währungscode Grundwährung

-   Auftragswert Gesamt in Grundwährung

-   Setpositionen [auf_pos_kz = \'t\'] werden nicht mitgerechnet

Auswahl der Daten:

-   auf_pos

-   auf_pos.auf_off_mg <> 0

-   auf.auf_nr = auf_pos.ab_auf_nr

-   erl_ein_auf_nr = 0

Sortierung:

-   Kundenmatchcode

-   Kundennummer

-   Auftragsnummer

### Auftragsbestandsliste nach Artikel

Listbild:

[offaufar.doc](file:///\\pcssrv019\projekte\tradecon\org\offaufar.doc)

Aufruf:

Werteingaben:

-   Firmennummer (p)

-   Artikelnummer

-   Auftragsart

-   Zustandskennzeichen

-   Lagernummer

-   Lieferwoche

-   Lieferdatum

-   Verarbeitungskennzeichen

-   Alle Artikel

-   nur Artikel mit frei verfügbarer Menge > 0

Seitenkopf:

-   Firmenkurzbezeichnung [fa.fa_adr_snr adr.adr_mc]

-   Tagesdatum

-   Uhrzeit

-   Positionsüberschriftszeile

    **Pro Artikel**

-   Artikelnummer

-   Artikelmatchcode

-   bestellte Menge Lieferant

Pro Lager

-   Lagernummer

-   Lagerstand

-   verfügbarer Bestand des Lagers

-   frei verfügbarer Bestand des Lagers

Pro Auftragsposition

-   Auftragsnummer

-   Positionsnummer

-   Auftragsart

-   Kundennummer

-   Kundenmatchcode

-   offene Menge

-   Verkaufseinheit

-   Verkaufspreis

-   Auftragswährung

-   Rabatt 1

-   Rabatt 2

-   Auftragsrabatt des Eingangsauftrages

-   Lieferwoche

-   Lieferdatum

-   Folgezeile, wenn Preis pro Menge <>1 oder Verrechnungseinheit <>
    Verkaufseinheit:

-   nur sichtbar wenn Verkaufseinheit <> Verrechnungseinheit

-   offene Menge in Verrechnungseinheit

-   Verrechnungseinheit

-   "per " + vkpr_pro_mg + " " + vveh_cd

Auswahl der Daten:

-   auf

-   erl_auf_nr = 0

-   auf_pos

-   auf_pos.auf_off_mg <> 0

-   auf.auf_nr = auf_pos.ab_auf_nr

-   erl_ein_auf_nr = 0

-   auf_pos_kz <> "s"

Sortierung:

-   Artikelnummer

-   Lagernummer

-   Auftragsnummer

-   Positionsnummer

### Liste offene Lieferscheine Verkauf

Listbild:

[offvlfskd.doc](file:///\\pcssrv019\projekte\tradecon\org\offvlfskd.doc)

Aufruf:

Werteingaben:

-   Firmennummer (p)

-   Kundennummer

-   Auftragsart

-   Lieferscheindatum

Seitenkopf:

-   Firmenkurzbezeichnung [fa.fa_adr_snr adr.adr_mc]

-   Tagesdatum

-   Uhrzeit

-   Positionsüberschriftszeile

    **Pro Kunde**

-   Kundennummer

-   Kundenmatchcode

Pro Lieferschein

-   Lieferscheinnummer

-   Lieferscheindatum

Pro Auftrag (Eingang)

-   Auftragsart

-   Auftragsnummer

-   Auftragsdatum

-   Währungscode

-   Kundenbestellnummer

-   Kundenbestelldatum

Pro Lieferscheinposition

-   Positionsnummer

-   Artikelnummer

-   Artikelmatchcode (Auftragsposition)

-   gelieferte Menge

-   Verkaufseinheit

-   Verkaufspreis

-   Rabatt 1

-   Rabatt 2

-   Aufragskopfrabatt

-   Positionsbetrag in Auftragswährung

Summenzeile Kunde

-   Währungscode Grundwährung

-   Auftragswert Kunde in Grundwährung

-   Setpositionen [auf_pos_kz = \'t\'] werden nicht mitgerechnet

Summenzeile Gesamt

-   Währungscode Grundwährung

-   Auftragswert Gesamt in Grundwährung

-   Setpositionen [auf_pos_kz = \'t\'] werden nicht mitgerechnet

Auswahl der Daten:

-   vlfs

-   vrech_nr = 0

-   vlfs_pos

-   lief_mg <> 0

-   vlfs_pos.ein_auf_nr = auf_pos.ein_auf_nr

-   auf.auf_nr = auf_pos.ein_auf_nr

Sortierung:

-   Kundenmatchcode

-   Kundennummer

-   Lieferscheinnummer

-   Auftragsnummer Eingang

-   Positionsnummer

### Kundenumsatz

**Allgemeines**

-   Fenster dient zur Abfrage der Kundenumsätze, es können jedoch keine
    Änderungen durchgeführt werden

#### Auswahldialog

-   Firma

-   Kundennummer (f)

-   Code Periodenschema (p) (t)

-   Auswertungsmonat (p)

-   Darstellungsschema (p)

#### Register "Liste"

-   Firma

-   Kundennummer

-   Kundenmatchcode

-   Daten lt. Darstellungsschema

**Anmerkung**

Die Abweichung wird dann berechnet, wenn es in dem ausgewählten
Periodenschema eine Vergleichszeile (a2 oder b2) gibt. Die Abweichung
wird dann in der ersten Zeile (a1 oder b1) angezeigt.

#### Schaltflächen für Verzweigungen

-   Kunden/Artikelumsatz

### Artikelumsatz

**Allgemeines**

-   Fenster dient zur Abfrage der Artikelumsätze, es können jedoch keine
    Änderungen durchgeführt werden

#### Auswahldialog

-   Firma

-   Artikelnummer (f)

-   Code Periodenschema (p) (t)

-   Auswertungsmonat (p)

-   Darstellungsschema (p)

#### Register "Liste"

-   Firma

-   Artikelnummer

-   Artikelmatchcode

-   Daten lt. Darstellungsschema

**Anmerkung**

Die Abweichung wird dann berechnet, wenn es in dem ausgewählten
Periodenschema eine Vergleichszeile (a2 oder b2) gibt. Die Abweichung
wird dann in der ersten Zeile (a1 oder b1) angezeigt.

#### Schaltflächen für Verzweigungen

-   Kunden/Artikelumsatz

###  Kunden/Artikelumsatz

**Allgemeines**

-   Fenster dient zur Abfrage der Kunden/Artikelumsätze, es können
    jedoch keine Änderungen durchgeführt werden

#### Auswahldialog

-   Firma

-   Kundennummer (f)

-   Artikelnummer(f)

-   Code Periodenschema (p) (t)

-   Auswertungsmonat (p)

-   Darstellungsschema (p)

#### Register "Liste"

-   Firma

-   Kundennummer

-   Kundenmatchcode

-   Artikelnummer

-   Artikelmatchcode

-   Daten lt. Darstellungsschema

**Anmerkung**

Die Abweichung wird dann berechnet, wenn es in dem ausgewählten
Periodenschema eine Vergleichszeile (a2 oder b2) gibt. Die Abweichung
wird dann in der ersten Zeile (a1 oder b1) angezeigt.

#### Schaltflächen für Verzweigungen

-   Keine

###  Umsatzabfrage Kunde

**Allgemeines**

-   Fenster dient zur Abfrage der monatlichen Kundenumsätze, es können
    jedoch keine Änderungen durchgeführt werden

#### Auswahldialog

-   Firma (p)

-   Kundennummer (p)

#### Register "Liste"

-   Daten je Monat und Jahr ( 4 Spalten mit dem aktuellen Jahr und den
    letzten 3 Jahren)

-   Monat

-   Umsatz

-   DB-%

**Anmerkung**

Die Spalten sind absummiert und zeigen die jeweilige Jahressumme

### Umsatzabfrage Artikel

**Allgemeines**

-   Fenster dient zur Abfrage der monatlichen Artikelumsätze, es können
    jedoch keine Änderungen durchgeführt werden

#### Auswahldialog

-   Firma (p)

-   Artikelnummer (p)

#### Register "Liste"

-   Daten je Monat und Jahr ( 4 Spalten mit dem aktuellen Jahr und den
    letzten 3 Jahren)

-   Monat

-   Umsatz

-   DB-%

-   Umsatzmenge

**Anmerkung**

Die Spalten sind absummiert und zeigen die jeweilige Jahressumme

### Kassenbon

**Allgemeines**

-   Fenster dient zur Abfrage der Kassenbons, es können jedoch keine
    Änderungen durchgeführt werden

#### Auswahldialog

-   Firma

-   Belegnummer

-   Belegdatum

-   Kundennummer (f)

-   Rechnungsanschrift Zeile 1

-   SachbearbeiterCode

-   Belegart (t)

-   Kassennummer (f)

-   Rechnungsnummer (f)

-   Wenn eingegeben wird die Tabelle ka_bel_vrech fix mitgejoint d.h. es
    > werden nur Rechnungsausgleich Belege angezeigt

-   **Anmerkung**

-   Es werden nur Belege angezeigt, die bereits verbucht wurden
    > (erl_bel_nr > 0)

#### Register "Liste"

-   Firma

-   Belegnummer

-   Belegdatum

-   Belegart

-   Kundennummer

-   Rechnungsanschrift Zeile 1

-   Rechnungsbetrag brutto

-   Kassennummer

#### Register "Detail"

**Teilbereich "Bonkopf"**

-   Firma

-   Belegnummer

-   Belegdatum

-   Belegzeit

-   Belegart

-   Belegsubart

-   Beleganschrift

-   Sachbearbeitercode

-   Rechnungsbetrag brutto

-   Kassanummer

-   Kassabezeichnung

-   Auftragsnummer Anzahlung

-   StornoBelegnummer

**Teilbereich "Ust-Daten"**

-   Bei Rechnungsausgleich nicht vorhanden

Anzeigeliste mit den Ust-Kontierungen des Kassenbons

-   Ust-Code

-   Ust-Prozentsatz

-   Ust-Basis

-   Umsatzsteuer

-   Bruttobetrag

**Teilbereich "Rechnungen" (a)**

-   Nur bei Rechnungsausgleich vorhanden

Anzeigeliste mit den bezahlten Rechnungen des Kassenbons

-   Rechnungsnummer

-   Rechnungdatum

-   Rechnungsbetrag

-   Skonto %

-   Skonto Betrag

-   Zahlungsbetrag

#### Schaltflächen für Verzweigungen

-   Positionen

-   zugehörige KassenbonPositionen

### Kassenbonposition

**Allgemeines**

-   Fenster dient zur Abfrage der Kassenpositionen, es können jedoch
    keine Änderungen durchgeführt werden

#### Auswahldialog

-   Firma

-   Belegnummer

-   Belegdatum

-   Kundennummer (f)

-   KundenName1 lt. Bonkopf

-   Belegart

-   Wertebereich "Tabelle"

-   Kassennummer (f)

-   Wertebereich "Tabelle"

-   Positionsnummer

-   Artikelnummer (f)

-   SachbearbeiterCode

#### Register "Liste"

-   Firma

-   Belegnummer

-   Belegdatum

-   Kundennummer

-   KundenName1 lt. Bonkopf

-   Artikelnummer

-   Artikelmatchcode

-   Menge

-   Mengeneinheit

-   Verkaufspreis brutto

-   Rabatt 1 u 2

-   Positionswert inkl. USt

-   Positionswert exkl. USt

-   = (Umsatz)

-   Lagernummer

-   DB-absolut

-   DB-%

#### Schaltflächen für Verzweigungen

-   Lagerbewegungen

### Ausgabe elektronische Rechnungslegung an den Bund (ebInterface 4.1) / BBG (ebInterface 4.0)

Auswahl der Daten

-   alle Ausgangsrechnungen, die zur Ausgabe gekennzeichnet sind
    (vrech.eb_job_snr = 0) und deren Versand freigegeben ist
    (vrech_dfrei_jn = ‚j')

Ablauf

Ausgabe folgender Daten

-   Anmeldedaten

-   User

-   Passwort

-   Archivpfad

-   Test

-   Pro Rechnung

-   Rechnungsdaten

-   Währung

-   Rechnungsnummer

-   Rechnungsdatum

-   Rechnungssteller

-   eigene UID-Nummer

-   eigene Anschrift(Name1, Strasse, Länderbezeichnung, PLZ, Ort,
    > E-Mailadresse, Telefonnummer)

-   Fremdkundennummer lt. Debitor

-   Rechnungsempfänger

-   UID-Nummer

-   Debitorennummer

-   Rechnungsanschrift (Name1, Strasse, Länderbezeichnung, PLZ, Ort)

-   Pro Lieferschein

-   Lieferscheindaten

-   Lieferscheinnummer

-   Lieferscheindatum

-   Lieferanschrift (Name1, Strasse, Länderbezeichnung, PLZ, Ort)

-   Auftragstextzeilen (in Description) die für Rechnung markiert sind

-   Pro Eingangsauftrag

-   Bestelldaten

-   Kundenbestellnummer

-   wenn diese nicht mit dem Präfix lt. Parameter beginnt, dann wird die
    > Einkäufergruppe (inkl. „:") vorangestellt.

-   Kundenbestelldatum

-   Auftragsnummer

-   Auftragsdatum

-   Pro Lieferscheinposition

-   Artikeldetails

-   eigene Positionsnummer

-   Artikelnummer

-   Verrechnungsmenge

-   Verrechnungseinheit

-   Einzelpreis (netto)

-   Steuersatz

-   skontofähig j/n

-   Fremdpositionsnummer (=Positionsnummer des Bundes) (wenn <> 0)

-   Positionsbetrag netto

-   4 x Positionstexte

-   Pro Rabatt (Kopf-/Positionsrabatte)

-   Kz Rabatt/Aufschlag

-   Basisbetrag

-   Rabatt in %

-   Rabattbetrag

-   Pro Steuersatz

-   Nettobetrag

-   Steuersatz

-   Steuerbetrag

-   Zahlungsart

-   bei eb_payment_kz = „u"

-   eigener IBAN

-   eigener BIC

-   bei eb_pament_kz = „l"

-   IBAN lt. debitor_bank

-   BIC lt. debitor_bank

-   Kommentar (statt_zkond_txt) bzw. Fixtext wenn leer

-   Zahlungskonditionen

-   Fälligkeitsdatum

-   Skonto1

-   Skontodatum 1

-   Skonto2

-   Skontodatum 2

-   skontofähiger Betrag

### Aufbau Stornorechnung

Werteingaben:

-   Firmennummer (p)

-   Rechnungsnummer (p)

-   Stornorechnung (p)

Einschränkung

-   Rechnung darf selbst keine Stornorechnung sein

-   Funktionalität Stornorechnung muss lt. gf_initapplenv-Parameter
    > freigeschalten sein

-   Bei Jetfibu Integration nicht möglich (da Logik fbbibel, bibkt nicht
    > gemacht ist)

-   Der erste der es braucht kann Jetfibu-Integration machen und
    > Einschränkung danach entfernen

-   Bei Einsatz von „Sammellieferschein" kann es Probleme mit dem
    > Auftragsrabatt geben. Der erste der darauf stösst, kann sich darum
    > kümmern.

Ablauf

-   Kompletter Stornovorgang ist eine einzelne Transaktion

-   Alle vlfs und vlfs_pos der zu Stornierenden Faktura werden gelesen

-   Vlfs und vlfs_pos werden 2x neu geschrieben

-   Event für Nummernkreis vergabe vlfs_nr vorstehen

-   Default Barverkaufsnummernkreis für vlfs

-   Verb_gebucht_jn = ja, stat_gebucht_jn = nein

-   Kartei_snr, geg_kartei_snr = -1

-   Beim ersten mal ident zum Original-LFS

-   Die Originalrechnung wird diesem vlfs zugeordnet

-   Druck_vlfs_nr und druck_vlfs_dat lt. Originalvlfs

-   Vrech_mon wird von den originalen vlfs_pos übernommen

-   Beim Zweiten mal die Werte mit \* -1 multipliziert

-   Pro vlfs beim zweiten Mal:

-   Original vlfs die vrech_nr auf 0 setzen

-   Betroffene Originalaufträge die ein_hat_rech_jn auf n wenn es ausser
    > der Originalrechnung keine weiteren Rechnungen gab

-   Pro vlfs_pos beim Zweiten Mal:

-   Vermindern originale auf_pos um auf_pos.auf_fakt_mg =
    > auf_pos.auf_fakt_mg -- stornoliefmg

-   Setzen originale auf_pos.hat_vrech_jn = n wenn es ausser der
    > Originalrechnung keine andere Rechnung für die Auftragsposition
    > gab

-   Rechnung wird neu geschrieben, Werte mit \*-1 multipliziert

-   Vrech, vrech_ust, vrech_kont jeweils \*-1

-   Zuordnen Rechnung zum zweiten LFS

-   Event für Vergabe Renr vorsehen

-   Vrech_job_nr = <aktuell>

-   Vfbueb_job_nr = 0, ao_snr = 0, eb_job_snr = 0, vrechn_datz =
    > getdate(), vrech_barcode lt. neuer Rechnungsnummer, vrechausart_cd
    > = „d"

-   Vlfs_pos.vrech_mon wird lt. Datum der Stornorechnung belegt.

-   Event für Druck vorsehen. Standard: vrech_gedruckt_jn = n und
    > Belegdruck einspoolen

-   Setzen Stornorechnungsnummer

-   Ende Transaktion

    Anmerkungen zur Programmierung: Was ist ausserhalb zu tun:

    Dieser Absatz kann nach erledigung aus der Org gelöscht werden

-   Lieferscheinaufbau muss folgendes schreiben:

-   Vlfs.druck_vlfs_nr = vlfs_nr

-   Vlfs.druck_vlfs_dat = vlfs_dat

-   Vlfs.vkrab = auf.vkrab

-   Vlfs_pos.vkrab1 = auf_pos.vkrab1

-   Vlfs_pos.vkrab2 = auf_pos.vkrabs

-   Vlfs_pos.vkrab3 = auf_pos.vkrab3

-   Vlfs_pos.vkrab4 = auf_pos.vkrab4

-   Vlfs_pos.vkrab5 = auf_pos.vkrab5

-   Vlfs_pos.vkpr_pro_mg = auf_pos.vkpr_pro_mg

-   Vlfs_pos.vkpr_keh_veh_kz = auf_pos.vkpr_keh_veh_kz

-   Vlfs_pos.veh_cd = auf_pos.veh_cd

-   Rechnungsaufbau muss folgendes schreiben:

-   Storno_vrech_nr = 0

-   Vlfs_pos.vkrab1 = auf_pos.vkrab1

-   Vlfs_pos.vkrab2 = auf_pos.vkrabs

-   Vlfs_pos.vkrab3 = auf_pos.vkrab3

-   Vlfs_pos.vkrab4 = auf_pos.vkrab4

-   Vlfs_pos.vkrab5 = auf_pos.vkrab5

-   5 Rabatte aktualisieren, könnten sich ja ändern

-   Lieferscheindruck

-   Druck Preise und Rabatte lt. vlfs_pos, Auftragsrabatt lt. vlfs

-   Rechnungsdruck

-   Druck Preise und Rabatte lt. vlfs_pos, Auftragsrabatt lt. vlfs

-   Im Lieferscheinteil werden LFS-Nummer und LFS-Datum lt.
    > Druck-Nummer(Datum) angedruckt

-   Andruck „Stornorechnung" als Belegtitel wenn vrech_nr <>
    > storno_vrech_nr

-   Andruck „Stornorechnung zu Re:" + Rechnungsnummer, unterhalb der
    > Re-Anschrift, wenn vrech_nr <> storno_vrech_nr

-   SQL für Releaseupdate

-   SQL für Erstbefüllung der neuen Felder lt. auf_pos bzw. lt. auf.

-   Kein Defaultwert für die Felder notwendig, ausnahme
    > vrech.storno_vrech_nr, dort Default 0

## Einkauf

### Bestellung

**Allgemeines**

Vollständig gelieferte Bestellungen dürfen nicht mehr geändert werden.

#### Auswahldialog

-   Firma

-   Bestellnummer

-   Bestelldatum

-   Bestellart (w)

-   Bestellvorschlagscode (w)

-   Lieferantennummer (f)

-   Lieferantenmatchcode

-   Zustandskennzeichen (w)

-   Erledigungskennzeichen

-   erledigt

-   offen

-   Sachbearbeiterkennzeichen

-   Auftragsnummer Lieferant

-   automatisch generiert

-   Ja

-   Nein

-   EUDR Status (w)

#### Register "Liste"

-   WebdokFunktionalität

-   Firma

-   Filiale

-   Zustandskennzeichen

-   Bestellnummer

-   Bestellart

-   Bestelldatum

-   Lieferantennummer

-   Lieferantenmatchcode

-   Bestellvorschlagscode

-   Lieferdatum

-   Lieferwoche

-   Sachbearbeiterkennzeichen

-   Auftragsnummer Lieferant

-   Mindestbestellwert Lieferant

-   offener Bestellwert

-   Währungscode

-   Kennzeichen "automatisch generiert"

-   Erfassungszeitpunkt

-   EUDR Status

#### Register "Detail"

-   Firma

-   wird automatisch belegt, wenn nur ein Mandant vorhanden ist

-   keine Eingabe, wenn nur ein Mandant vorhanden

-   Lieferantennummer (f)

-   Eingabelogik Matchcode u. Nummer

-   Lieferant muss aktiv sein

-   ggf. Anzeige Bestellinfo in eigenem Fenster

-   Lieferantenmatchcode (a) (f) Adressen

-   Währungscode Kreditor (a)

-   Bestellart (d)

-   Anfrage

-   Bestellung

-   Bestellvorschlag

-   Rahmenbestellung

-   Lieferantenadresse

-   Vorschlag Neuanlage von Lieferant

-   Lieferanteninfotext (a)

-   Versandart (fd)

-   Vorschlag Neuanlage von Lieferant

-   Lieferbedingung (fd)

-   Liefertermintext

-   Vorschlag für neue Positionen

-   Lieferdatum

-   Vorschlag für neue Positionen

-   Lieferwoche

-   Vorschlag für neue Positionen

-   Auftragsnummer des Lieferant

-   Zahlungskonditionen

-   Vorschlag Neuanlage von Kreditor

-   Valutadatum

-   Bestellinfotext

-   Dispobestellung (c)

-   Defaultwert = "j"

-   Bei einer Änderung werden die Lagerbuchungsfaktoren der Positionen
    > neu vergeben.

-   Bestellnummer (a)

-   wird bei der Neuanlage beim Speichern vergeben

-   Filiale

-   wird automatisch belegt, wenn nur eine Filiale vorhanden

-   keine Eingabe bei Änderung, bzw. wenn nur eine Filiale vorhanden

-   Erfassungsdatum (a)

-   wird bei der Neuanlage vergeben

-   Bestelldatum

-   Datum, an dem die Bestellung ausgeführt (gedruckt, gefaxt ...) wurde

-   Sachbearbeitercode Erfassung (a)

-   wird bei Neuanlage bzw. Bestellvorschlag vergeben

-   Fixtext lt Bestellart

-   "Bestellvorschlagscode"

-   "Anfragehauptnummer"

-   Bestellvorschlagscode (f)

-   Vorschlag Neuanlage = blank

-   nur bei Anfragen einzugeben

-   Bestellvorschlagskennzeichen muss bei Anfragen blank oder "a" sein

-   Zustandskennzeichen Bestellung (a)

-   erfasst

-   bestellt

-   vollständig geliefert

-   EUDR Status (a)

-   Kennzeichen automatisch generiert (ac)

-   Bestellung mit Preisen drucken (c)

-   Vorschlag Neuanlage lt. Lieferant

-   Bestellungbarcode (Proforma)

-   Eingabe nur, wenn Bestellung gescannt wird [archiv.beleg_kz =
    > "be"]

-   sonst fix ""

-   fixer Defaultwert ""

**Anmerkung zum Speichern**

-   wird ein Barcode ungleich "" eingetragen, wird dieser in der
    Tabelle [pfu_scanzu] zusätzlich abgespeichert

-   wird ein Barcode geändert, wird der alte Wert aus Tabelle
    [pfu_scanzu] gelöscht

-   wird die Dispobestellung geändert, so muss der Lagerfaktor in jeder
    Bestellposition [best_pos.best_lag_ftr] per Fernsteuerung neu
    bestimmt werden.

Drag+Drop

-   Wird ein PDF auf den Bestellkopf gedroped, so wird dieses in die
    Dokumente mit Ausdrucksart "best_dok" und der Bestellnummer als
    Belegnummer verspeichert.

#### Register "Warenempfänger"

-   Adresse des Warenempfängers

-   Vorschlag Neuanlage eigene Filialanschrift

-   kann manuell übersteuert werden

-   in der ersten Zeile der Adresse kann in das AdressWindow verzweigt
    > werden

    **Anmerkung**

    wird gemeinsam mit Register "Detail" gespeichert

#### Register "KommDaten"

-   Kommunikationsart Lieferant (fd)

-   Kommunikationsnummer Lieferant (a)

-   Sachbearbeiter Lieferant (fd)

-   Vorname SB (a)

-   Nachname SB (a)

-   ZuHanden-Feld

-   wird bei der Sachbearbeiterauswahl automatisch zusammengestellt

-   Kommunikationsart Sachbearbeiter (fd)

-   Kommunikationsnummer Sachbearbeiter (a)

-   Bestellweise (fd)

-   nur wenn Bestellweise mit Bestellart Fax oder E-Mail ausgewählt:

-   Kommunikationsarten und -nummern des Sachbearbeiters und des
    > Lieferanten, welche der ausgewählten Bestellart entsprechen (d)

-   Kommunikationsart (a)

-   Kommunikationsnummer

    **Anmerkung**

3.  wird gemeinsam mit Register "Detail" gespeichert

4.  folgende Eingabereihenfolge mit TAB:

    a.  Sachbearbeiter Lieferant

    b.  ZuHanden-Feld

    c.  Bestellweise

    d.  Kommunikationsarten SB und Lieferant

#### Register "Text"

Bearbeitungsliste mit den Anfangs- bzw. Endtexten der Bestellung

-   Textstelle (d)

-   Beleganfang

-   Belegende

-   Text

-   Fettdruck (c)

-   Unterstreichung (c)

    **Anmerkung**

 Textbausteine können eingefügt werden

**ad Menüpunkt "Löschen"  
**

-   bei Bestellart ungleich "b" werden vor dem Löschen zunächst die
    Positionen und deren Texte gelöscht

-   ist der Bestellvorschlagscode ungleich blank wird nach dem Löschen
    auch der Satz in der Tabelle bestvor gelöscht, wenn keine andere
    Bestellung mehr auf den Bestellvorschlag referenziert

#### Register "Belegkette"

-   siehe unter Allgemeines Abfrageregister "Belegkette"

#### Auswahlpunkte im Menü "Extras" 

-   Druck intern

-   Bestellung ausführen

-   nicht für Bestellvorschlag und Produktionsvorschlag

-   nicht wenn Zustand "bestellt" oder "erledigt" (=vollständig
    > geliefert)

-   Bestellweise muss <> " " sein

-   Versand per Outlook

-   steht optional für Bestellung zur Verfügung
    > [pfu_param.outlook_mail_kz]

-   Dokument wird erstellt, jedoch nicht gedruckt

-   TC wartet bis zum Timeout auf die Dokumentenerstellung durch den
    > aufgegebenen Job

-   ist Dokument erstellt, wird neue Outlook-Nachricht geöffnet und
    > folgende Felder gesetzt:

-   E-Mail-Adresse

-   BCC-E-Mail-Adressen

-   E-Mail-Adresse Vertreter und/oder zusätzliche E-Mail

-   Betreff

-   gleiche Logik wie bei Batchverarbeitung

-   Attachment

-   Dokument des aktuellen Jobs

-   Body

-   wird nicht gesetzt, damit die Signatur des Benutzers nicht
    > überschrieben wird

-   Zustand zurücksetzen

-   nicht für Bestellvorschlag und Produktionsvorschlag

-   nicht wenn Zustand "erledigt"

-   setzt nach Entscheid Zustand von "bestellt" auf "erfasst"

-   Anfrage kopieren

-   nur für Anfragen

-   Umwandeln Anfrage in Bestellung

-   nur für Anfragen

-   setzt Lieferdatum und KW in Positionen

-   disponiert Positionen

-   bucht Liefermengen in zugeordneten Rahmenbestellungen

-   gilt bei der Übernahme für die Rahmenbestellung (best_lief_mg >
    > best_best_mg - best_loesch_mg) erfolgt die Ausgabe einer
    > Fehlermeldung und die Zuordnung zur Rahmenbestellung wird nicht
    > durchgeführt

-   löscht ggf. Datensatz in Tabelle [bestvor]

-   Umwandeln Vorschlag in Bestellung

-   nur für Bestellvorschlag

-   setzt Lieferdatum und KW in Positionen

-   disponiert Positionen

-   löscht ggf. Datensatz in Tabelle [bestvor]

-   Aufbau Produktionsauftrag

-   nur für Produktionsvorschlag

-   Liefertermin setzen

-   Eingabe von Lieferdatum, Lieferwoche und Termintext

-   Felder werden in Positionen abgestellt

-   nicht für erledigte Positionen

-   Termin bestätigen

-   AB-Termin in Positionen abstellen

-   nicht für erledigte Positionen

**ad Aufbau Produktionsauftrag**

-   Anlage Produktionsauftrag

-   Kundennummer lt. Firmenstamm

-   Auftragseingangsart = "auto"

-   pro Bestellposition Anlage eines Produktionsauftrages

-   Bestellposition hat zugeordnete Auftragsposition eingetragen

    1.  setzen Auftragsnummer und Auftragspositionsnummer

-   Bestellposition hat keine Auftragsposition eingetragen

    1.  setzen Artikelnummer und offene Produktionsmenge

-   löschen der Bestellpositionen und ggf. auf 0 stellen der
    Bestellzuordnung in der zugehörigen Auftragsposition

-   löschen des Bestellkopfes

**ad Anfrage kopieren**

-   Kopf wird kopiert

-   Lieferantennummer wird geleert

-   beim Speichern werden die Positionen kopiert

-   Preis der Positionen ist leer, Rabatte sind 0

#### Schaltflächen für Verzweigungen

-   Bestellpositionen

-   Dokumente

### Bestellposition

Allgemeines

-   Vollständig gelieferte Bestellpositionen dürfen nicht mehr geändert
    werden, Bestellpositionen mit gelieferter bzw. gelöschter Menge
    dürfen nicht gelöscht werden. Ist die Bestellung vollständig
    geliefert, darf keine Position mehr neu angelegt werden.

-   Es gibt eingenen WinModus für Bestellvorschlag. Dieser wird
    automatisch gesetzt, wenn die Bestellposition aus dem Bestellkopf
    für einen Bestellvorschlag aufgerufen wird.

#### Auswahldialog

-   Firma

-   Bestellnummer

-   Positionsnummer

-   Artikelnummer (f)

-   Bestelldatum

-   Bestellart (w)

-   Bestellvorschlagscode (w)

-   Mahnvorschlagscode (w)

-   Lieferantennummer (f)

-   Lieferantenmatchcode

-   Zustandskennzeichen Bestellung (w)

-   Erledigungskennzeichen

-   erledigt

-   offen

-   Sachbearbeiterkennzeichen

-   Auftragsnummer Lieferant

-   Lieferdatum

-   Lieferwoche

-   Infotext

-   Rahmenbestellnummer

-   Rahmenbestellposition

-   DDS-Referenznummer

#### Register "Liste"

**Teilbereich "Liste"**

-   Firma

-   Filiale

-   Bestellnummer

-   Positionsnummer

-   Bestelldatum

-   Lieferantennummer

-   Lieferantenmatchcode

-   Artikelnummer

-   Artikelmatchcode

-   Lagerstand

-   reservierte Menge Kunde

-   bestellte Menge Lieferant

-   Verfügbare Menge Einkauf

-   Mindestbestand

-   Mindestbestandkennzeichen

-   Losmenge

-   bestellte Menge in Verkaufseinheit

-   Verkaufseinheit

-   bestellte Menge

-   offene Menge

-   Eingabe vorsehen

-   Einkaufsmengeneinheit

-   Einkaufspreis

-   Währungscode

-   Rabatt 1 u 2

-   Preis Manuell (c)

-   Bestellwert Position

-   Lieferdatum

-   bestätigtes Lieferdatum

-   Lieferwoche

-   bestätigte Lieferwoche

-   AVISO Menge

-   Bestellart

-   Bestellvorschlagscode

-   Mahnvorschlagscode

-   Mahnstufe

-   Mahndatum

-   Sachbearbeiterkennzeichen

-   Auftragsnummer Lieferant

-   Zustandskennzeichen

-   Rahmen vorhanden (c)

-   Rahmenbestellnummer

-   Rahmenbestellposition

-   Lieferantenartikelnummer

-   Staffelmenge

-   EUDR (c)

-   DDS-Referenznummer

Teilbereich "Verbrauch"

-   wird abhängig von einem TC-Parameter angezeigt

-   nicht im Verbund mit anderen Eingabe/Anzeigebereichen

-   wird nur Retrieved, nicht bei Neuanlage oder Änderung befüllt

-   zeigt die Verbrauchsdaten des Artikels der aktuellen
    Bestellposition, analog zum Fenster "Verbrauchsabfrage Artikel"

#### Register "Detail"

**Teilbereich "Artikel"  
**

-   Firma

-   Bestellnummer (f)

-   Lieferantennummer (a)

-   Lieferantenmatchcode (a)

-   Währungscode Bestellung (a)

-   Bestellart (a)

-   Bestelldatum (a)

-   Zustandskennzeichen Bestellung (a)

-   Positionsnummer (a)

-   wird bei der Neuanlage beim Speichern vergeben

-   Artikelnummer (f)

-   Eingabelogik Nummer, Matchcode u. Identifikationen

-   Artikel muss aktiv sein

-   darf kein Set- und kein Verrechnungsartikel sein

-   darf kein Auslaufartikel sein

-   wird gegebenenfalls durch Alternativartikel ersetzt

-   Infofenster, wenn Rahmen vorhanden

-   Artikelmatchcode

-   Eingabe bei diversen Artikeln

-   Artikelinfotext (a)

-   Lieferantenartikelnummer

-   Nur bei diversem Artikel eingebbar, sonst automatisch aus artikid
    > belegt

-   offene Menge

-   verändert bei Eingabe bestellte Menge

-   bestellte Menge darf bei Bestellart <> "Vorschlag/Anfrage" nicht
    > 0 sein

-   löst bei Eingabe Preisfindung aus (nicht bei Anfrage)

-   Informationsfenster wenn kein Vielfaches der Losgröße

-   Informationsfenster wenn nach Preisfindung Staffelmenge belegt ist:  
    > "Staffelpreis ab <Staffelmenge> <Einheitscode des
    > Einkaufspreises>"

-   Darf nicht kleiner als die AVISO Menge sein.

-   Losgröße (a)

-   Einkaufsmengeneinheit

-   Eingabe, bei diversen Artikeln

-   Einkaufspreis

-   Einkaufspreis per Menge

-   Eingabe, bei diversen, bei der Neuanlage

-   Einkaufspreis per Einheit

-   Einkaufsrabatt 1 u. 2

-   Preis manuell (ca)

-   Positionsbetrag (a)

-   gerechnet von bestellter Menge

-   Gesamtbetrag Bestellung (a)

-   gerechnet von bestellter Menge

-   Lieferdatum

-   leer bei Vorschlag bzw. Anfrage

-   Lieferwoche

-   leer bei Vorschlag bzw. Anfrage

-   bestätigtes Lieferdatum

-   keine Eingabe bei Neuanlage

-   bestätigte Lieferwoche

-   keine Eingabe bei Neuanlage

-   Projekt

-   Liefertermintext

-   leer bei Vorschlag bzw. Anfrage

-   Bestellpositionsinfotext

-   Mahnsperre (ac)

-   keine Eingabe bei Neuanlage, bei Vorschlag, Anfrage oder
    > Rahmenbestellung

-   Mahnvorschlagscode (a)

-   Mahnstufe (a)

-   Datum letzte Mahnung (a)

-   DDS-Referenznummer (f)

-   Kein Lookupfehler -- Neue dds werden beim Speichern der Position
    > automatisch neu angelegt

-   DDS-Prüfnummer

-   Eingabe nur möglich, wenn DDS-Referenznummer eigegeben wurde

-   Auftragsnummer

-   0 = Bestellung ohne Bezug auf Auftrag

-   0, bei Vorschlag bzw. Anfrage

-   Auftragspositionsnummer

-   0 = Bestellung ohne Bezug auf Auftrag

-   Auftragsposition muss selben Artikel haben

-   0, bei Vorschlag bzw. Anfrage

-   Lieferadresse Zeile 1 u. 2 aus Auftrag (a)

-   nur bei Bestellung und Bestellvorschlag

-   Rahmen vorhanden (ac)

-   wird nur bei der Neuanlage der Bestellposition ermittelt

-   Rahmenbestellung Auswahlfenster (d)

-   Anzeige Daten nur wenn Artikel und Lieferant bestimmt sind

-   Bestellnummer

-   Bestelldatum

-   Menge

-   offene Menge

-   Einkaufspreis

-   Rabatt 1-4

-   Rahmenbestellnummer (f)

-   Rahmenbestellposition (f)

-   bestimmt bei der Neuanlage auch Artikel

-   bestimmt Einkaufspreis und Einkaufsrabatte

-   Bestellmenge darf offene Rahmenbestellmenge nicht überschreiten

-   bestellte Menge (a)

-   AVISO Menge (a)

-   im TC Standard nicht im sichtbaren Bereich

-   gelieferte Menge (a)

-   gelöschte (nicht gelieferte) Menge (a)

-   Mindestbestellmenge (a)

-   Mengenverhältnis:

-   1 Einkaufsmengeneinheit (a)

-   n Verkaufsmengeneinheiten (a)

-   in Einkaufsmengeneinheit sowie in Verkaufsmengeneinheit:

-   Lagerstand Dispolager (a)

-   reservierte Menge Kunden Dispolager (a)

-   bestellte Menge Lieferant (a)

-   verfügbare Menge (a)

-   Mindestbestand (a)

-   Wiederbeschaffungszeit Wochen (a)

-   Wiederbeschaffungszeit in Tagen (a)

-   Kennzeichen Mindestbestand (a)

    **Anmerkung**

Ist kein Artikel/Lieferanten-Datensatz vorhanden, so ist dies in der
Regel nur bei diversen Artikeln zulässig. Durch Parametrierung kann dies
jedoch auch für lagerführende Artikel erlaubt werden . Die
Einkaufs-mengeneinheiten sind in diesem Fall die Verkaufseinheiten lt.
Artikelstamm.

Bei Bezug auf eine Rahmenbestellung wird die Liefermenge der
Rahmenbestellung erhöht und die offene Rahmenbestellmenge am
Artikelstamm vermindert. Überschreitet die Liefermenge die offene
Rahmenbestell-menge wird eine Fehlermeldung ausgegeben, das Speichern
ist nicht möglich.

Automatisches Speichern von Einkaufspreisen

-   Wenn am Lieferantenstamm aktiviert, werden manuelle Änderungen von
    Einkaufspreisen in den Artikel-Lieferantendarten verspeichert.

-   Der Preis und die Rabatte werden dabei als Normal-Einkaufspreis
    gültig ab heute und Ab-Menge 0 angelegt.

-   Eventuell vorhanden zukünftige Normal-Einkauspreise werden dabei
    gelöscht.

-   Das darf nicht bei Positionen mit Preis 0 geschehen

EUDR-Daten

-   Der EUDR-Status im Bestellkopf wird bei Drittland-Lieferanten beim
    Speichern von EUDR-Relevanten Artikelpositionen aktualisiert.

    **Teilbereich "Artikeltexte"**

-   Bearbeitungsliste mit den Artikeltextzeilen der Bestellposition Die
    Zeilen werden bei der Neuanlage aus den Artikeltextzeilen
    vorgeschlagen, bei diversen Artikeln wird der Matchcode
    vorgeschlagen.

-   Bei Bezug zu einer Auftragsposition werden werden die Texte der
    Auftragsposition mit Bestellung="j" eingelesen wenn gilt: Sprache
    Lieferant entspricht Sprache Kunde Auftrag oder Artikel ist divers

-   Artikeltext

-   Kennzeichen fett drucken (c)

-   Kennzeichen unterstrichen drucken (c)

#### Register "Bestellungen/Lieferungen"

**Teilbereich "andere Bestellungen"**

Anzeigeliste von anderen Bestellpositionen, in denen der aktuelle
Artikel verspeichert ist

-   Bestellart

-   Lieferantennummer

-   Lieferantenmatchcode

-   Bestellnummer

-   Postionsnummer

-   Bestellerfassungsdatum

-   bestellte Menge

-   offene Menge

-   Einkaufsmengeneinheit

-   Einkaufspreis

-   Einkaufsrabatt 1-4

-   Lieferdatum

-   Lieferwoche

-   bestätigtes Lieferdatum

-   bestätigte Lieferwoche

**Teilbereich "Zugänge"**

Anzeigeliste mit den bereits gebuchten Eingangslieferscheinen zur
aktuellen Bestellposition

-   Warenzugangsnummer

-   Positionsnummer

-   Lieferscheinnummer

-   Lieferscheindatum

-   gelieferte Menge

-   Einkaufsmengeneinheit lt. Eingangslieferscheinposition

#### Register "Alternativen"

Teilbereich Alternativartikel

Anzeigeliste der möglichen Alternativartikel
[artik_altern.altern_ekz_kz not in ("-", "e")]

Für diese Anzeige ist ein Zusatzmodul zum Standardpaket erforderlich

-   Auswahlfeld (c)

-   nur dieses Feld kann eingegeben werden

-   dieser Artikel wird als Alternative gewählt

-   Artikelnummer

-   Artikelmatchcode

-   Kennzeichen Auslaufartikel

-   lt. aktuellem Lager

-   das ist das Lager lt. Sachbearbeiter bzw. lt. Firma

-   Lagerstand

-   verfügbarer Lagerstand

-   bestellte Menge Lieferant

    **Anmerkung**

-   Ist der Artikel bestimmt, wird dieses Register befüllt. Befindet
    sich darin ein Artikel mit Alternativkennzeichen "a" für
    "Anzeigen", wird automatisch auf diesen Register verzweigt.

-   Wird ein Artikel ausgewählt, wird wieder automatisch auf das
    Detailregister umgeschaltet

Teilbereich "Alternative Lieferanten"

-   Ist nur bei einem Bestellvorschlag ohne Auftragsbezug verfügbar

-   Liste über alle Artikel-Lieferanten Einträge dieses Artikels

-   Als Einkaufspreis wird der zum Bestelldatum gültige Einkaufspreis
    für die aktuelle bestellte Menge angezeigt.

-   Lieferantennummer

-   Öffnen öffnet die Artikel-Lieferantendaten

-   Lieferantenmatchcode

-   ab Menge

-   Einkaufspreis

-   Währungscode

-   Rabatt 1

-   Rabatt 2

-   Rabatt 3

-   Rabatt 4

-   Rabatt 5

-   Nara Menge

-   Netto Einkaufspreis in GW

-   GW

-   Ab Menge nächste Mengenstaffel

-   Durch Doppelclick wird die Konditinen für diese Menge angezeigt.
    > Gibt es mehr keine nächste Kondition, so wird wieder die erste
    > Kondition angezeigt.

-   Einkaufseinheit

-   Wiederbeschaffungszeit in Tagen für Bestellung

-   Bestellen (c)

-   Das ist das einzige Feld, das geändert werden kann.

-   Es ist beim aktuellen Lieferanten aktiviert und kann dort nicht
    > geändert werden.

Bei Auswahl bei einem anderen Lieferanten erfolgt ein TE "Position bei
Lieferant <lief_cd> <lief_mc> betellen? Ja/Nein".  
Bei Ja wird:

-   Ein Bestellkopf mit folgenden Bedingungen gesucht:

-   Bestellart Bestellvorschlag

-   Firma/Filiale lt. aktueller Bestellung

-   Lieferant lt. Auswahl

-   Bestellvorschlagscode lt. aktueller Bestellung

-   Wenn nicht gefunden wird ein neuer Bestellkopf erstellt

-   In dieser Bestellung wird eine neue Bestellposition erstellt  
    Folgende Daten werden dabei von der aktuellen Bestellposition
    übernommen

-   Artikelcode

-   Artikelmatchcode

-   Offene Menge (muss evt. zwischen den Einkaufseinheiten umgerechnet
    > werden, wenn die Lieferanten unterschiedliche Einkaufseinheiten
    > haben) und wird auf die Losgröße des Lieferanten aufgerundet.

-   Positions Infotext

-   Zugeordnete Auftragsnummer und Positionsnummer

-   Manuelle Textzeilen werden ebenfalls übernommen

-   Die ursprüngliche Bestellposition wird gelöscht.

#### Register "Belegkette"

-   siehe unter Allgemeines Abfrageregister "Belegkette"

#### Auswahlpunkte im Menü "Extras"

-   Bestellposition erledigt setzen

-   nicht für Bestellvorschlag oder Anfrage

-   nicht wenn die AVISO Menge <> 0 ist

-   Position wird erledigt gesetzt, die offene Menge wird zur gelöschten
    > Menge addiert

#### Auswahlpunkte im Menü "Ansicht"

-   Standard

-   Bestellvorschlag

#### Schaltflächen für Verzweigungen

-   Artikelverbräuche

-   Einkauf

-   RahmenPositionen

###  Bestellvorschlag Aufbau

#### Auswahldialog

-   Firma (p)

-   Filiale (o)

-   Lieferantennummer (f)

-   Artikelnummer (f)

-   Selektionskennzeichen Bestellvorschlag

-   Bestellvorschlagscode (p)

-   Verarbeitungskennzeichen (w) (p)

-   Artikel mit Verfügbarkeitsunterschreitung

-   alle Artikel

-   Verarbeitungskennzeichen2

-   Lager- und auftragsbezogen

-   Nur auftragsbezogen

-   Nur lagerbezogen

Auswahl der Daten

-   Nur Artikel mit Lagerführung oder diverse

-   Keine Auslaufartikel

-   nur aktive Artikel

-   alle Sätze aus [artik_lief] welche der Auswahl entsprechen

Ablauf

-   Verarbeitung der Daten sortiert nach Lieferant und Artikel

-   In der Hauptauswahl wird bereits je Artikel geprüft, ob es eine
    Auftragsposition gibt, für die eine Bestellposition aufgebaut werden
    soll:

-   offene Menge > 0

-   Bestellnummer = 0

-   vorhandener Auftragspositionsbestellsatz [auf_pos_best] für den
    > gilt

-   Auftragsart <> "Strecke"

-   Ermittlung folgender Daten bei Artikel mit Lagerführung

-   verfügbare Menge =  
    > Lagerstand Dispolager + bestellte Menge Lieferant +offene
    > Produktionsmenge + [  
    > ]{.mark}offene Menge aus Umbuchungen - reservierte Menge Kunde
    > Dispolager

-   Mindestbestand aus [artik_lief]

-   Ist ein Artikel in den Bestellvorschlag aufzunehmen (= verfügbare
    Menge kleiner Mindestbestand oder Auftragsposition die bestellt
    werden soll, vorhanden) erfolgt zuerst je Auftragsposition und
    danach bei lagerführenden Artikeln einmal für die Lagerbestellung
    dieser Ablauf:

-   Beginn / Ende Transaktion

-   Abspeichern des Bestellvorschlagscodes in [bestvor]

-   nur beim 1. Artikel der Verarbeitung

-   Ist der Code bereits vorhanden, Druck einer Fehlermeldung und
    > Abbruch

-   Abspeichern einer Bestellung

-   nur beim 1. Artikel eines Lieferanten

-   Vergabe einer Bestellvorschlagsnummer

-   entspricht die Lieferantennummer der Lieferantennummer für
    > Produktion im Firmenstamm, so wird die Bestellart auf "p", sonst
    > auf "v" gesetzt

-   bei Bezug zu Auftragsposition:

-   Abspeichern der Bestellposition

-   Bestellmenge = offene Auftragsmenge

-   Einkaufsdaten lt. Tabelle auf_pos_best

-   Einkaufskonditionen

-   Liefertermin

-   Zuordnung zu Rahmenbestellung

-   Projekt lt. Tabelle auf_pos_best

-   Lieferantenartikelnummer (nur bei diversem Artikel)

-   bei lagerführenden Artikeln für die Lagerbestellung :

-   verfügbare Menge neu = verfügbare Menge + bereits aufgebaute
    > Bestellmenge aus Auftragspositionen

-   Vorschlagsmenge

-   0, wenn verfügbare Menge neu >= Mindestbestand

-   Mindestbestand erhöht um "Mehrbestell"-Prozentsatz -- verfügbare
    > Menge neu, umgerechnet auf Einkaufseinheit, mindestens
    > Mindestbestellmenge, aufgerundet auf Losgröße

-   Abspeichern der Bestellposition, wenn Vorschlag > 0 bzw. bei
    > Verarbeitungskennzeichen "alleArtikel" auch mit Vorschlagsmenge
    > = 0

-   Endemeldung des Batchlaufes

### Bestellvorschlag Löschen

**Auswahldialog**

-   Firma (p)

-   Lieferantennummer (f)

-   Bestellnummer (f)

-   Selektionskennzeichen Bestellvorschlag (w) (p)

Auswahl der Daten

-   alle Bestellvorschläge, die der Auswahl entsprechen

Ablauf

-   Verarbeitung der Daten sortiert nach Lieferant, Bestellung und
    Positionsnummer

-   pro Bestellposition

-   Beginn / Ende Transaktion

-   löschen der Bestellpositionstexte

-   löschen der Bestellposition

-   löschen der Bestellung

-   nur bei der letzten Bestellposition der Bestellung

-   löschen des Bestellvorschlagcodes

-   nur bei der letzten Bestellposition der Verarbeitung

-   Endemeldung des Batchlaufes

### Bestellung generieren

#### Auswahldialog

-   Firma (p)

-   Auftragsnummer (p)

-   0 = alle Streckenaufträge

-   <> 0 = genau dieser Auftrag unabhängig von der Auftragsart

-   Lieferant (f)

-   Artikel eines Lieferanten (p)

-   optional, darf unbestimmt sein

Auswahl der Daten

-   nicht erledigte Abwicklungsauftragspositionen

-   offene Auftragsmenge > 0

-   Bestellnummer in Auftragsposition = 0

-   Bestelldaten für Auftragsposition [auf_pos_best] vorhanden

-   alle Artikel bei denen der optional ausgewählte Lieferant, als
    möglicher Lieferant hinterlegt ist

Ablauf

-   Verarbeitung der Daten sortiert nach Lieferant,
    Abwicklungsauftragsnummer und Artikelnummer

-   Je Auftrag und Lieferant wird ein neuer Bestellkopf angelegt

-   Beginn / Ende Transaktion

-   Lieferant ist nicht der Produktionslieferant lt. Firmenstamm

-   Abspeichern einer Bestellung

-   nur beim 1. Artikel eines Lieferanten bzw. Auftrages

-   Vergabe einer Bestellnummer

-   handelt es sich beim aktuellen Auftrag um einen Abrufauftrag wird
    > die Bestellart auf "r", ansonsten auf "b" gesetzt

-   bei Streckenaufträgen wird die Empfängeradresse lt. Lieferadresse
    > des Auftrages belegt und das Dispolagerkennzeichen lt.
    > Streckenlager belegt

-   Abspeichern der Bestellposition

-   je Auftragsposition eine Bestellposition

-   Bestellmenge = offene Auftragsmenge

-   Einkaufsdaten lt. Auftragspositionsbestelldaten (Lieferwoche bzw.
    > -datum nur wenn belegt)

-   Einkaufskonditionen

-   Liefertermin

-   Abruf von Rahmenbestellung

-   Lieferantenartikelnummer (nur bei diversem Artikel)

-   Lieferant ist der Produktionslieferant

-   Neuanlage eines Produktionsauftrages

-   setzen Produktionskundennummer, Auftragsnummer und
    > Auftragspositionsnummer

-   Endemeldung des Batchlaufes

### Berechnung Mindestbestand

Auswahl der Daten

-   alle Artikel/Lieferanten-Sätze mit Kennzeichen Mindestbestand =
    "e"

-   Artikelanlagedatum liegt im Beobachtungszeitraum der
    Verbrauchsrechnung

Ablauf

-   automatische Abarbeitung aller Artikel/Lieferantensätze

-   Berechnung Mindestbestand

-   Update des Mindestbestandes

-   Endemeldung des Batchlaufes

Rechenformel Mindestbestand

-   Beobachtungszeitraum Verbrauch

-   Beobachtungstageanzahl > 0:  
    > VonDatum = aktueller Tag - Anzahl Beobachtungstage  
    > BisDatum = aktueller Tag - 1

-   wenn Beobachtungswochenanzahl < 0:  
    > VonDatum = aktueller Tag - 365  
    > BisDatum = aktueller Tag - (365 - Anzahl Beobachtungstage)

-   Ist das VonDatum < als das Artikelanlagedatum, wird der
    > Mindestbestand nicht berechnet

-   Verbrauch

-   Summe Verbrauchsmengen aus [st_ar_tag], Datum liegt zwischen
    > VonDatum und BisDatum

-   durchschnittlicher Tagesbedarf (6 NK)

-   Verbrauch / Anzahl Beobachtungstage

-   Mindestbestand

-   durchschnittlicher Tagesbedarf \* Wiederbschaffungstage für
    > Bestellvorschlag

### Bestelldruck, Anfragedruck

Listbild:

[best.doc](\\\\pcssrv019\\projekte\\tradecon\\org\\best.doc)

Aufruf:

Werteingaben:

-   Bestellnummer

-   Firmennummer

-   Verarbeitungskennzeichen (Ausführung, Druck intern)

Seitenkopf:

-   Lieferantenanschrift [best.lief_name1 bis best.lief_ort]

-   "Z.Hd."- Zeile

-   Lieferanschrift [best.we_name1 bis best.we_ort]

-   Liefertermintext

-   wenn nicht leer

-   Fixtext "RAHMEN", wenn Rahmenbestellung

-   Fixtext "BESTELLUNG" bzw. "ANFRAGE" abhängig von Bestellart

-   Fixtext "-INTERN" bei internem Druck

-   Bestellnummer

-   Tagesdatum

-   Lieferantennummer

-   Sachbearbeiter Vor- und Nachname [adr_pers.v_name, n_name]

-   Versandart [versart.versart_bez]

-   Lieferbedingung [liefbed.liefbed_bez]

-   Seitennummer und Seitenanzahl

Auf der 1. Seite vor den Positionen:

-   Bestelltext Einleitung [best_txt]

Positionsüberschrift je Seite:

-   Währungscode

-   wenn Bestellung mit Preisen gedruckt wird

Pro Bestellposition:

-   Artikelnummer

-   Artikelbezeichnung und sonstige Texte lt. [best_pos_txt]

-   bei Abrufen von Rahmenbestellungen

-   Fixtext "Abruf von Rahmen"

-   Bestellnummer

-   Bestelldatum (Druckdatum)

-   wenn Auftragsnummer Lieferant vorhanden

-   Fixtext "Ihre Nr"

-   Auftragsnummer Lieferant

-   offene Menge (wenn ganzzahlig ohne Nachkomma)

-   Mengeneinheit [eh_sprache.druck_eh_txt]

-   wenn Bestellung mit Preisen gedruckt wird

-   Einkaufspreis

-   Positionsbetrag

-   nur wenn Einkaufspreis nicht per 1 bzw. Einkaufspreismengeneinheit
    > nicht gleich Einkaufseinheit:

-   Fixtext "per"

-   Menge für die sich der Einkaufspreis versteht

-   Einkaufspreismengeneinheit

-   Positionsrabatt 1, wenn ungleich 0

-   Positionsrabatt 2, wenn ungleich 0

-   Liefertermintext

-   wenn nicht leer und ungleich zu Termintext lt. Kopf

-   Fixtext "Ihre Nr: " + Lieferantenartikelnummer lt. Tabelle
    best_pos (wenn diverser Artikel), wenn nicht leer

Nach der letzten Position:

-   Trennlinie

-   wenn Bestellung mit Preisen gedruckt wird

-   Fixtext lt. Listbild

-   Währungscode

-   Endbetrag

-   Zahlungskonditionen lt. Formular

-   Bestelltext Ende [best_txt]

-   Endetextzeilen lt. [fa.best_txt_cd bzw. fa.anfr_txt_cd
    txt_txt.txt_txt]

Im Seitenfuß:

-   Logo sofern vorhanden

Auswahl der Daten:

-   bestart_cd <> \'v\'

-   zustand_kz = \'e\'

-   bestweise_cd <> \' \'

Sortierung:

-   Positionsnummer

Update:

-   best

-   best_zustand_kz abhängig von max(p_erl_best_nr) auf "b" bzw. auf
    > "t"

-   Bei einer Nexmart Bestellung (lt. Bestellweise) wird die Nexmart SST
    generiert und per E-Mail an die E-Mail Adresse lt. Parameter
    "nexmart_email" versendet.

### Bestellmahnung Aufbau

#### Auswahldialog

-   Firma (p)

-   Lieferantennummer (f)

-   Artikelnummer (f)

-   Mahnvorschlagscode (p)

-   Mahnrhythmus in Tagen (p)

-   Lieferdatum (p)

Auswahl der Daten

-   keine Anfragen und Bestellvorschläge

-   Zustand der Bestellung muss "bestellt" sein

-   keine Bestellpositionen mit Mahnsperre oder eingetragenem
    Mahnvorschlagscode

-   alle Sätze aus [best_pos] welche der Auswahl entsprechen

Ablauf

-   Verarbeitung der Daten sortiert nach Lieferant, Bestellung,
    Positionsnummer

-   Prüfungen:

-   Tagesdatum >= Vergleichsdatum Mahnrhythmus

-   Lieferdatum >= Vergleichsdatum Liefertermin

-   Ist eine Bestellposition in den Mahnvorschlag aufzunehmen:

-   Abspeichern des Mahnvorschlagscodes in [mahnvor]

-   nur beim 1. Artikel der Verarbeitung

-   Ist der Code bereits vorhanden, Druck einer Fehlermeldung und
    > Abbruch

-   Abspeichern des Mahnvorschlagscodes in der Bestellposition

-   Endemeldung des Batchlaufes

Ermittlung Vergleichsdatumfelder

-   Vergleichsdatum für Mahnrhythmus

-   Bestellausführungsdatum + Mahnrhythmustage, wenn Mahnstufe = 0

-   Mahndatum + Mahnrhythmustage, wenn Mahnstufe > 0

-   Vergleichsdatum für Liefertermin

-   Lieferdatum, wenn AB-Lieferdatum leer

-   AB-Lieferdatum, wenn belegt

### Bestellmahnung Druck

Listbild:

[bestmahn.doc](file:///\\pcssrv019\projekte\tradecon\org\bestmahn.doc)

Aufruf:

Werteingaben:

-   Mahnvorschlagskennzeichen (p)

-   Lieferant

-   Druckausgabe (p)

-   drucken (d)

-   lt. Bestellweise Lieferant (l)

Seitenkopf:

-   Lieferantenanschrift [best.lief_name1 bis best.lief_ort]

-   Fixtext "LIEFERERINNERUNG"

-   Tagesdatum

-   Lieferantennummer

-   Seitennummer und Seitenanzahl

Pro Bestellposition

-   Artikelnummer

-   Artikelbezeichnung und sonstige Texte lt. [best_pos_txt]

-   bei Abrufen von Rahmenbestellungen

-   Fixtext "Abruf von Rahmen"

-   Bestellnummer

-   Bestelldatum (Druckdatum)

-   wenn Auftragsnummer Lieferant vorhanden

-   Fixtext "Ihre Nr"

-   Auftragsnummer Lieferant

-   offene Menge (wenn ganzzahlig ohne Nachkomma)

-   Mengeneinheit [eh_sprache.druck_eh_txt]

-   Lieferdatum

-   Lieferdatum, wenn bestätigter Liefertermin leer

-   bestätigter Liefertermin, wenn ungleich leer

-   Fixtext "B"

-   nur wenn Lieferdatum bestätigter Termin ist

-   aktuelle Mahnstufe

-   Datum der letzten Mahnung

    Fixtext "Ihre Nr: " + Lieferantenartikelnummer, wenn nicht leer

Nach der letzten Position

-   Endetextzeilen lt. [fa.bestmahn_txt_cd txt_txt.txt_txt]

Sortierung:

-   Lieferantennummer

-   Bestellnummer

-   Positionsnummer

elektronischer Versand:

-   Absender- und Empfängerdaten werden aus den Stammdaten automatisch
    generiert

-   für die Empfängerdaten wird die Standardeinkaufskommunikation lt.
    > Adresse verwendet, wenn nicht vorhanden, wird gedruckt

-   für den Absender wird der User, der den Bestellmahnungsdruck
    > aufgegeben hat herangezogen, Aufbau ident mit Bestellung

-   Betreff: "gf_uebersetz(LIEFERERINNERUNG)

Update:

-   best_pos

-   mahn_stufe

-   mahn_dat

-   mahnvor_cd

-   mahnvor

-   löschen Mahnvorschlagscode

### Eingangslieferschein

**Allgemeines**

-   Vollständig fakturierte Eingangslieferscheine dürfen nicht mehr
    geändert werden.

#### Auswahldialog

-   Firma

-   Warenzugangsnummer

-   Lieferscheinnummer

-   Lieferscheindatum

-   Lieferantennummer (f)

-   Lieferantenmatchcode

-   Zustandskennzeichen (w)

-   Erledigungskennzeichen (w)

-   offen

-   erledigt

-   Sachbearbeiterkennzeichen

#### Register "Liste"

-   WebdokFunktionalität

-   Firma

-   Filiale

-   Zustandskennzeichen (w)

-   Warenzugangsnummer

-   Lieferscheinnummer

-   Lieferscheindatum

-   Lieferantennummer (f)

-   Lieferantenmatchcode

-   Währungscode lt. Lieferschein

-   Sachbearbeiterkennzeichen

-   Erfassungszeitpunkt

-   Lieferscheinwert in FW (s)

-   Summe Einkaufswert Position der Eingangslieferscheinpositionen

-   Lieferscheinwert (Warenwert) in GW (s)

-   Summe der Eingangslieferscheinpsotionen veh_estpr \* veh_lief_mg

#### Register "Detail"

-   Firma

-   wird automatisch belegt, wenn nur ein Mandant vorhanden ist

-   keine Eingabe, wenn nur ein Mandant vorhanden

-   Lieferantennummer (f)

-   Eingabelogik Matchcode u. Nummer

-   Lieferant muss aktiv sein

-   ggf. Anzeige Warenzugangsinfo in eigenem Fenster

-   Lieferantenmatchcode (a)

-   Währungscode

-   Vorschlag Neuanlage lt. Lieferant

-   darf übersteuert werden

-   Bestellnummer

-   darf leer bleiben

-   definiert, wenn vorhanden, den Lieferanten

-   dient als Vorschlag für die Position

-   Lieferscheinnummer

-   Lieferscheindatum

-   Eingangslieferscheinbarcode

-   Eingabe nur, wenn Eingangslieferschein gescannt wird
    > [archiv.beleg_kz = "el"]

-   sonst fix ""

-   fixer Defaultwert ""

-   Lager (fd)

-   Lieferantenadresse

-   Vorschlag Neuanlage von Lieferant

-   Lieferanteninfotext (a)

-   Versandart (fd)

-   Vorschlag Neuanlage von Lieferant

-   dient für Lieferantenretoure

-   Bestellinfotext (a)

-   darf leer bleiben

-   wird nur angezeigt, wenn Bestellnummer eingegeben

-   Warenzugangsnummer (a)

-   wird bei der Neuanlage vergeben

-   Filiale

-   wird automatisch belegt, wenn nur eine Filiale vorhanden

-   keine Eingabe bei Änderung, bzw. wenn nur eine Filiale vorhanden

-   Warenzugangsdatum

-   Kann nur bei der Neuerfassung und bei einem Lieferaviso geändert
    > werden

-   Wenn kein Lieferaviso bzw. bei der Zubuchung eines Lieferavisos
    > wird, wenn nicht ausgefüllt das aktuelle Datum verwendet

-   Erfassungszeitpunkt (a)

-   Sachbearbeitercode Erfassung (a)

-   wird bei Neuanlage vergeben

-   Zustandskennzeichen Lieferschein

-   Vorschlag bei Neuerfassung ist erfasst, kann wenn AVISO aktiviert
    > ist bei der Neuerfassung und wenn noch keine Positionen vorhanden
    > sind manuell auf AVISO geändert werden

-   AVISO

-   erfasst / Lager gebucht

-   teilweise verrechnet

-   vollständig verrechnet

-   MDE Zustand (a)

-   MDE Freigabe (c)

-   Ist nur bei Liefercheinen im Zustand AVISO und MDE-Zustand < 3
    > verfügbar.

-   Durch die Aktivierung wird der MDE-Zustand auf 1 (Freigegeben)
    > gesetzt durch Deaktiviertung wieder auf 0 (nicht freigegeben)
    > zurückgesetzt.

**Anmerkung zum Speichern**

-   Hinweis "Scanbarcode fehlt !", wenn [archiv.beleg_kz = "el"]
    und Barcode ""

-   wird ein Barcode ungleich "" eingetragen, wird dieser in der
    Tabelle [pfu_scanzu] zusätzlich abgespeichert

-   wird ein Barcode geändert, wird der alte Wert aus Tabelle
    [pfu_scanzu] gelöscht

#### Register "Text"

Bearbeitungsliste mit den Anfangs- bzw. Endtexten der
"Lieferantenretoure"

-   Textstelle

-   Beleganfang

-   Belegende

-   Text

-   Fettdruck (c)

-   Unterstreichung (c)

    **Anmerkung**

Textbausteine können eingefügt werden

#### Register "Schnellbuchung" 

**Teilbereich "Bestellung"  
**

Bearbeitungsliste mit den Bestellungen des Lieferanten, es darf keine
neue Zeile eingefügt werden, wenn der Zustand "vollständig verrechnet"
ist. Der Register "Schnellbuchung" wird nicht gemeinsam mit dem
Detailregister gespeichert.

-   Listbox (d)

-   nur bei neuer Zeile aktiv, zeigt die offenen Bestellungen des
    > aktuellen Lieferanten

-   Bestellnummer

-   Bestelldatum

-   Auftragsnummer Lieferant

-   Bestellnummer (f)

-   nur bei neuer Zeile und wenn unbestimmt, aktiv

-   Bestellung muss offen und dem aktuellen Lieferanten zugeordnet sein

-   ist im Detail eine Bestellnummer definiert, wird diese bei Zeile 1
    > automatisch eingesetzt

-   Bestelldatum (a)

-   Auftragsnummer Lieferant (a)

-   Währungscode (a)

-   Infotext gekürzt (a)

-   VerarbeitungskennzeichenZugangsmenge=offene Menge (c)

-   wird durch individuellen Default belegt

-   leer, kein Vorschlag für Zugangsmenge

-   n, Vorschlag Zugangsmenge=0

-   j, Vorschlag Zugangsmenge=offene Menge

**Anmerkung**

Nach Definition der Bestellnummer werden die Zeilen im Teilbereich
"Bestellpositionen" automatisch aufgebaut. Es werden nur
Bestellpositionen mit offener Menge abzüglich Lieferaviso Menge > 0
verwendet. Durch das Löschen einer Zeile werden die zugehörigen
Positionen entfernt. Das Belegen des Verarbeitungskennzeichens bewirkt
die Belegung der Zugangsmenge.

**Teilbereich "BestellPositionen"  
**

Bearbeitungsliste mit den Bestellpositionen, es dürfen manuell keine
Zeilen eingefügt oder gelöscht werden.

-   Positionsnummer (a)

-   Artikelnummer (a)

-   Lieferantenartikelnummer (a)

-   Artikelmatchcode

-   lt. Bestellposition

-   Lagercode (fd)

-   Defaultbelegung lt. Register "Detail"

-   "Öffnen" öffnet ArtikelLager

-   "Suchen" öffnet Lager

-   offene Menge (a)

-   Abzüglich Lieferavisomenge

-   darf nicht < 0 werden

-   Zugangsmenge

-   verringert offene Menge

-   Einkaufsmengeneinheit (a)

-   Erledigungskennzeichen (c)

-   setzt "gelöschte" Menge

-   darf nicht eingegeben werden, wenn offene Menge = 0

-   Einkaufspreis

-   Rabatt 1

-   Rabatt 2

-   Einkaufspreis per Menge (a)

-   EUDR (c) (a) lt.Artikelstamm

-   DDS-Referenznummer

-   DDS-Prüfnummer

-   Infotext (a)

-   Auftragsnummer (a)

-   öffnen Funktion

-   Auftragspositionsnummer (a)

-   öffnen Funktion

-   Name1 lt. Auftrag (a)

**Anmerkung zum Speichern**

Die Bestellpositionen werden in einem Hilfsspeicher zur Verbuchung
vorgemerkt und der Inhalt des Registers komplett gelöscht. Die
Eingangslieferscheinposition wird automatisch geöffnet (nicht im
Batchmodus) und die Verarbeitung der eingegebenen Zeilen mit
Zugangsmenge > 0 gestartet.

Abweichend zur normalen Erfassung wird nur die aktuelle Bestellposition
in den Teilbereich "Bestellpositionen" der Warenzugangsposition
geladen.

Das Belegen der Felder sowie das Speichern der Zugangsposition erfolgt
in der Regel automatisch, tritt jedoch ein Fehler auf oder handelt es
sich um einen Artikel bei dem eine Eingabe im Lagerbereich notwendig
ist, erhält der Benutzer die Kontrolle.

Durch Speichern des Benutzers wird die Verarbeitung fortgesetzt.

Verwirft der Benutzer die Eingabe erfolgt eine Ja/Nein-Abfrage
"Schnellzubuchung vorzeitig beenden ?". Bei Ja-Entscheid wird die
Buchungsautomatik beendet und keine weiteren Positionen verbucht. Bei
Nein-Entscheid erfolgt eine weitere Ja/Nein-Abfrage "Position
überspringen ?". Wird Ja ausgewählt, setzt die Verarbeitung bei der
nächsten Position fort, wird Nein gewählt, wird die aktuelle Position
neu eingelesen.

**Anmerkung zum Löschen**

Ein Eingangslieferschein kann gelöscht werden, wenn keine Positionen
vorhanden sind und kein Eingangslieferscheinbarcode vorhanden ist

#### Register "Belegkette"

-   siehe unter Allgemeines Abfrageregister "Belegkette"

#### Auswahlpunkte im Menü "Extras"

-   AVISO Zubuchen

-   Nur bei Zustand Lieveraviso möglich

-   Druck Lieferantenretourschein

-   kann beliebig oft angewählt werden

-   Erledigt setzen

Ad AVISO Zubuchen

-   Es wird geprüft ob in allen Positionen alle notwendigen Lagerdaten
    ausgefüllt sind (Lagerorte, Chargen und Gerätenummern). Wenn nicht
    erfolgt eine entsprechende Fehlermeldung, aus der ersichtlich ist
    was fehlt, es werden die Positionen geöffnet und sofort in den Lager
    Bereich der ersten fehlerhaften Position verzweigt.

-   Wenn das Warenzugangsdatum ([elfs_dat]) noch nicht belegt ist,
    wird jetzt das aktuelle Datum eingetragen.

-   Es wird für alle noch nicht auf Lager gebuchten Positionen die
    Lagerzubuchung durchgeführt -- siehe Eingangslieferscheinposition

-   Eine Transaktion pro Position

-   Wenn alle Positionen erfolgreich auf Lager gebucht wurde, wird der
    Status von Aviso auf erfasst umgesetzt.  
    Prüfung und Update müssen in einer Transaktion unter Sperre des
    Lieferanten erfolgen.

Ad Erledigt setzen

-   Ist nur möglich, wenn die DUEST Berechnung Aufrollung im Einsatz
    ist.

-   Zustand muss e oder t sein

-   Ist nur möglich wenn der Eingangslieferscheinwert der noch keiner ER
    zugeordnete Positionen 0 ist (Prüfung erfolgt nach Lock).

Updates:

-   Bei allen Eingangslieferscheinpositionen mit erech_nr = 0

-   erech_nr = -1

-   est_wert wird gesetzt (veh_estpr \*veh_lief_mg)

-   erech_mon wird mit dem Monat lt. Warenzugangsdatum belegt

-   Eingangslieferscheinkopf

-   elfs_zustand_kz = "v"

-   erl_elfs_nr = elfs_nr

#### Schaltflächen für Verzweigungen

-   Eingangslieferscheinpositionen

-   Dokumente

### Eingangslieferscheinposition

Allgemeines

-   Eingangslieferscheinpositionen dürfen nicht gelöscht werden.
    Änderungen können bis zur Eingangs-rechnungsverbuchung durchgeführt
    werden, der Infotext auch noch danach. Alle Teilbereiche des
    "Detail"-Registers werden gemeinsam gespeichert. Die
    Lieferscheinkorrektur ist nur mit einem Zusatzmodul zum
    Standardpaket möglich

-   Lieferavisopositionen, die noch keiner ER zugeordnet sind können
    jedoch schon gelöscht werden.

-   Es gibt einen einen WinModus "aviso", der automatisch verwendet
    wird, wenn die Eingangslieferscheinposition aus dem
    Eingangslieferscheinkopf im Zustand Aviso geöffnet wird.

#### Auswahldialog

-   Firma

-   Lieferantennummer (f)

-   Lieferantenmatchcode

-   Warenzugangsnummer

-   Positionsnummer

-   Artikelnummer (f)

-   Lieferscheinnummer

-   Lieferscheindatum

-   Zustandskennzeichen Eingangslieferschein (w)

-   Eingangsrechnungsnummer intern

-   Eingangsrechnungsbelegnummer

-   Eingangsrechnungsbelegdatum

-   Eingangsrechnungsdatum

-   Sachbearbeiterkennzeichen

-   Infotext

-   DDS-Referenznummer

#### Register "Liste"

-   Firma

-   Filiale

-   Warenzugangsnummer

-   Positionsnummer

-   Lieferscheinnummer

-   Lieferscheindatum

-   Lieferantennummer

-   Lieferantenmatchcode

-   Artikelnummer

-   Artikelmatchcode

-   gelieferte Menge

-   Einkaufsmengeneinheit

-   Eingangsrechnungsnummer

-   Eingangsrechnungsbelegnummer

-   Eingangsrechnungsbelegdatum

-   fakturierte Menge

-   Einkaufspreis

-   Währungscode lt. Lieferschein

-   Rabatt 1 u 2

-   Preis manuell (c)

-   Einkaufswert Position

-   gelieferte Menge in Lagereinheit

-   Lagereinheit

-   Einstandspreis

-   Sachbearbeiterkennzeichen

-   Lieferantenartikelnummer

-   MDE (c)

-   EUDR (c)

-   DDS-Referenznummer

-   DDS-Prüfnummer

#### Register "Detail"

**Teilbereich "Eingangslieferscheinposition"**

-   Firma

-   Warenzugangsnummer (f)

-   Positionsnummer (a)

-   wird bei der Neuanlage beim Speichern vergeben

-   Lieferantennummer (a)

-   Lieferantenmatchcode (a)

-   Währungscode Lieferschein (a)

-   Lieferscheinnummer (a)

-   Lieferscheindatum (a)

-   Rechnungsnummer (a)

-   Rechnungsbelegnummer (a)

-   Rechnungsbelegdatum (a)

-   Bestellnummer

-   kann leer bleiben

-   wird von Bestellung bzw. von letzter Buchung vorgeschlagen

-   Bestellpositionsnummer

-   kann leer bleiben

-   definiert gemeinsam mit Bestellnummer die Hauptposition im
    > Teilbereich "Bestellpositionen"

-   Artikelnummer (f)

-   keine Eingabe, wenn Bestellposition definiert

-   Eingabelogik Nummer, Matchcode u. Identifikationen

-   Artikel muss aktiv sein

-   darf kein Set- und kein Verrechnungsartikel sein

-   Hinweis, wenn Auslaufartikel

-   Artikelmatchcode (a)

-   Defaultwert lt. Artikel bzw. lt. Bestellposition

-   Eingabe bei diversen Artikeln

-   Artikelinfotext (a)

-   Zugangsmenge

-   löst bei Eingabe Preisfindung aus

-   bei der Neuanlage, wenn Teilbereich "Bestellpositionen" leer ist

-   kein Vorzeichenwechsel bei der Änderung

-   Einkaufseinheit (fd)

-   Anzahl kleinste Einheiten in einer Einkaufseinheit

-   Kleinste Einheit (a)

-   Einkaufspreis per Menge (d)

-   Einkaufspreis per Einheit (d)

-   Einkaufspreis

-   Einkaufsrabatt 1 u. 2

-   Preis manuell (ca)

-   Positionsbetrag (a)

-   Lieferscheinpositionsinfotext

-   Bestellpositionsinfotext (a)

-   gebucht (c) (a)

-   Ist Nein, wenn die kartei_snr -1 ist (Lieferaviso, dass noch nicht
    > auf Lager gebucht ist

-   Sonst Ja

-   MDE (c) (a)

-   EUDR (c) (a)

-   DDS-Referenznummer

-   Eingabe nur bei EUDR relevanten Artikeln möglich

-   Kein Lookup Error -- wird beim Speichern automatisch angelegt, wenn
    > noch nicht vorhanden

-   DDS-Prüfnummer

-   Eingabe nur möglich, wenn DDS-Referenznummer eingegeben wurde

-   Ist in dem Fall bei Drittlandslieferanten zwingend

Anmerkung

Die Einkaufsmengeneinheiten, sowie Preis und Rabatte sind durch die
Definition der Hauptbestellposition im Teilbereich "Bestellpositionen"
vorgegeben. Gibt es keine Bestellung zum angewählten Artikel, sind die
Einkaufsmengeneinheiten durch den Artikel/Lieferantenstamm vorgegeben,
Preise und Rabatte ergeben sich über die Einkaufspreisfindung.

Wird für den gebuchten Artikel ein "durchschnittlicher Einstandspreis"
geführt, erfolgt bereits jetzt eine bis zur Eingangsrechnung
"vorläufige" Berechnung.

Ist kein Artikel/Lieferanten-Datensatz vorhanden, so ist dies in der
Regel nur bei diversen Artikeln zulässig. Durch Parametrierung kann dies
jedoch auch für lagerführende Artikel erlaubt werden . Die
Einkaufs-mengeneinheiten sind in diesem Fall die Verkaufseinheiten lt.
Artikelstamm.

Automatisches Speichern von Einkaufspreisen

-   Wenn am Lieferantenstamm aktiviert, werden manuelle Änderungen von
    Einkaufspreisen in den Artikel-Lieferantendarten verspeichert. Das
    muss auch geschehen, wenn die Änderung in der Schnellzubuchung
    vorgenommen wurde.

-   Der Preis und die Rabatte werden dabei als Normal-Einkaufspreis
    gültig ab heute und Ab-Menge 0 angelegt.

-   Eventuell vorhanden zukünftige Normal-Einkauspreise werden dabei
    gelöscht.

-   Das darf nicht bei Positionen mit Preis 0 geschehen

Lieferaviso auf Lager buchen

-   Kann durch den Extramenüpunkt im Eingangslieferscheinkopf oder in
    der Position ausgelöst werden.

Prüfungen:

-   Die Summe der Mengen im Lager bereich (AVISO Datensätze) muss der
    gelieferten Menge entsprechen.

-   Bei Chargen oder Geräteartikeln müssen die Chargen oder
    Gerätenummern in allen Zeilen ausgefüllt sein.

-   Bei Lager mit Lagoertgenauer Lagerführung muss der Lagerort
    ausgefüllt sein.

Updates

-   Ist das Warenzugangsdatum im Eingangslieferscheinkopf noch null, so
    muss es mit dem aktuellen Datum belegt werden.

-   In den zugeordneten Bestellpositionen muss die AVISO Menge
    vermindert und die gelieferte Menge erhöht werden. Evt. wird auch
    eine gelöschte Menge gesetzt, wenn die Bestellposition damit
    erledigt werden soll.

-   Die offene Bestellmenge am Artikel muss vermindert werden.

-   Es muss eine Kartei-Snr vergeben werden.

-   Die Daten aus den AVISO Positionen müssen in die
    Kartei-Lagerbewegungsdaten übernommen und dadurch die Lagerbuchung
    ausgelöst werden.

-   Wenn damit alle Positionen eines Lieferavisos gebucht sind, muss der
    Zustand des Eingangslieferscheines auf Lager gebucht und der
    aktuelle User als Warenzugangs User upgedatet werden.

EUDR Daten/Prüfung

-   Bei einem Drittlandslieferanten und einem EUDR Pflichtigen Artikel
    müssen DDS Daten erfasst werden, damit der Artikel auf Lager gebucht
    werden kann. D.h. in diesem Fall ist ohne DDS-Daten nur ein
    Lieferaviso möglich.

-   Die DDS-Referenznummer wird (nur bei Drittlandslieferanten) am
    Artikelstamm als letzten DDS verspeichert.

-   Eine Warenzugangsbuchung von einem anderen Lieferanten löscht die
    letzte DDS am Artikelstamm wieder.

Teilbereich "Bestellpositionen"

-   Bearbeitungsliste mit den nicht erledigten Bestellpositionen des
    definierten Artikels bei der Neuanlage

-   Liste der mit dieser Lieferscheinposition gebuchten Bestellungen bei
    der Änderung

-   Bestellnummer (a)

-   Positionsnummer (a)

-   Bestelldatum (a)

-   offene Menge (a)

-   in der Einheit lt. Eingangslieferscheinposition

-   wird durch Änderung der gelieferten Menge oder des
    > Erledigungskennzeichens gesetzt

-   bestellte Menge - gelieferte Menge -- AVISO-Menge, wenn
    > Erledigungskennzeichen nicht gesetzt ist

-   0, wenn Erledigungskennzeichen nicht gesetzt ist

-   gelieferte Menge des Zugangs

-   keine Eingabe bei negativer Zugangsmenge

-   darf in Summe mit der bereits gelieferten Menge, die
    > Gesamtbestellmenge nicht überschreiten

-   Einkaufsmengeneinheit (a)

-   lt. Eingangslieferscheinposition

-   Erledigungskennzeichen (c)

-   bestimmt auch offene Menge

-   Hauptpositionskennzeichen (c)

-   folgende Felder wenn Bestellung mit Auftragsbezug:

-   Auftragsnummer (a)

-   Auftragspositionsnummer (a)

-   Lieferadresse 1 und 2 aus Auftrag (a)

Anmerkung

Nach der Definition des Artikels wird dieser Teilbereich automatisch
befüllt. Die Sortierung ergibt sich aus Bestellnummer und
Positionsnummer, wobei die im Teilbereich "Eingangslieferschein"
gewählte Position automatisch die 1. Position (=Hauptposition) ist.

Die Eingabe der Zugangsmenge bzw. eines Einheitenfeldes bewirkt eine
automatische Neuaufteilung der Zugangsmengen. Die positive Zugangsmenge
wird bei der 1. Position beginnend den Bestellpositionen zugeteilt,
wobei beim erreichen der offenen Menge das Erledigungskennzeichen
gesetzt wird.

Wird die Menge manuell geändert, wird beim Speichern geprüft, dass die
Summe die Zugangsmenge der Lieferscheinposition nicht übersteigt.

Ist eine Position einer Auftragsposition zugeordnet, wird der DuEst der
Auftragsposition mit dem Einstandspreis der Zubuchung belegt. Weiters
wird die zugeteilte Liefermenge automatisch in der Auftragsposition
freigegeben.

Bei diversen Artikeln kann ein Bezug zu einer Bestellposition nur durch
die Definition von Bestellnummer und -positionsnummer im Teilbereich
"Eingangslieferschein" hergestellt werden.

Beim Speichern der Neuanlage werden Bestellpositionen mit Liefermenge =
0 aus der Liste entfernt

Die Bestellung wird bei der Neuanlage und Änderung aktualisiert

-   AVISO Menge

-   gelieferte Menge

-   gelöschte Menge

-   Erledigungsnummer Bestellposition

-   Erledigungsnummer Bestellung

-   Zustand Bestellung

    **Teilbereich "Lagerdaten"**

-   Bei einer Lieveravisoposition, die noch nicht verbucht wurde
    ([elfs_pos.kartei_snr] = -1) werden die Daten lt. elfs_pos_aviso
    verwendet, sonst die Daten lt. kartei_lagbew zur kartei_snr.

-   bestehende Zeilen dürfen nur bei Lieveraviso gelöscht oder geändert
    werden

-   Lagercode (fd)

-   Vorschlag lt. Lieferscheinkopf

-   Vorschlag lt. Lager der zugehörigen Streckenauftragsposition

-   "Öffnen" öffnet ArtikelLager

-   "Suchen" öffnet Lager

-   Listbox Lagerbestände (d)

-   aktiv, wenn Lagerstand auf Lagerortebene geführt wird

-   definiert Lagerort und/oder Chargen- bzw. Gerätenummer

-   folgende Felder im Auswahlfenster:

-   Lagerort

-   Chargen- bzw. Gerätenummer

-   verfügbarer Lagerbestand

-   Ablaufdatum

-   Einlagerungsdatum

-   Listbox Lagerorte (d)

-   aktiv, wenn Lagerstand auf Lagerortebene geführt wird

-   definiert Lagerort

-   folgende Felder im Auswahlfenster:

-   Lagerort

-   Lagerort

-   aktiv, wenn Lagerstand auf Lagerortebene geführt wird und der
    > Lagerort editierbar ist

-   Chargen- bzw. Gerätenummer (d)

-   aktiv, wenn Lagerführung auf Geräte- bzw. Chargenebene und Lager
    > Chargen-/Geräteverwaltung [lag. cg_verw_jn = "j"] hat

-   folgende Felder im Auswahlfenster

-   Chargen- bzw. Gerätenummer

-   verfügbarer Lagerbestand

-   Ablaufdatum

-   Einlagerungsdatum

-   Menge in Einkaufseinheit

-   bei Geräteartikeln sowie Chargen-/und Gerätelager nur 1 bzw. -1
    > erlaubt

-   Vorschlag -1 bzw. +1 abhängig von Vorzeichen der Differenzmenge
    > zwischen Zugangsmenge und Zugangsmenge alt

-   Ablaufdatum

-   aktiv, wenn Charge mit Ablaufdatum geführt wird und Lager
    > Chargen-/Geräteverwaltung [lag. cg_verw_jn = "j"] hat

-   Buchungsdatum und -zeit (a)

-   Jahr bis Sekunde

-   Nicht bei Lieferaviso

-   Sachbearbeitercode (a)

-   Nicht bei Lieferaviso

Anmerkung

Für Positionen ohne Lagerbuchung ist der Teilbereich "Lagerdaten"
gesperrt. Ist bei Artikeln mit "normaler Lagerführung" beim Speichern
keine Lageraufteilung erfolgt, wird automatisch eine Zeile mit dem
Standardlager (=Defaultlager bzw. Lager der letzten
Lieferscheinposition) und der Zugangsmenge angelegt. Im Änderungszweig
ist das eine Zeile mit der Differenzmenge aus Zugangsmenge -
Zugangsmenge alt

Wird in der Gerätenummer das Zeichen # verwendet, so verstehen sich die
Zeichen vor dem # als Startgeräte-nummer für die automatische
Generierung einer Serie. Die Zeichen nach dem # definieren die Anzahl
der Gerätezeilen, die nach der Bestätigung der Eingabe automatisch
generiert werden.

Das Buchungsdatum wird nicht gespeichert, sondern durch die Datenbank
vergeben nach dem Speichern wird der Lagerdatenbereich neu eingelesen

Bei DUEST-Aufrollung:

-   Pro Verwendeter DUEST-Gruppe Aufruf der DUEST-Berechnung

Prüfungen beim Speichern:

Die Summe der Karteimengen muss mit der Zugangsmenge in Lagereinheit
übereinstimmen Ausgabe Meldung und automatisches Verzweigen in
Teilbereich Lagerdaten. Das gilt nicht fürs Lieferaviso.

-   bei negativer Menge:

-   der ArtikLagSub-Datensatz muss bereits angelegt sein

-   der verfügbare Lagerstand darf nicht kleiner 0 werden

-   bei Geräten muss das Zustandskennzeichen "l" sein

-   bei positiver Menge:

-   bei Geräten darf kein ArtikLagSub-Datensatz mit Lagerstand ungleich
    > 0 vorhanden sein

-   Ist bei Geräten der Gerätestamm-Datensatz vorhanden, sind nur
    > folgende Zustandskennzeichen zulässig: "r", "a"

#### Register "Text"

-   Bearbeitungsliste mit den Artikeltextzeilen der
    Eingangslieferscheinposition. Die Zeilen werden bei der Neuanlage
    aus den Artikeltextzeilen vorgeschlagen und für die
    Lieferantenretoure verwendet.

-   Artikeltext

-   Kennzeichen fett drucken (c)

-   Kennzeichen unterstrichen drucken (c)

#### Register "Belegkette"

-   siehe unter Allgemeines Abfrageregister "Belegkette"

#### Auswahlpunkte im Menü "Extras"

-   AVISO zubuchen

-   Nur bei Zustand Lieveraviso möglich

#### Schaltflächen für Verzweigungen

-   Auftragsposition

-   ArtikelEinkauf

### Warenretourschein Druck

Listbild:

[wret.doc](file:///\\pcssrv019\projekte\tradecon\org\wret.doc)

Seitenkopf:

-   Lieferantenanschrift [lief.lief_name1 bis lief.lief_ort]

-   Fixtext "RETOURSCHEIN"

-   Eingangslieferscheinnummer intern

-   Tagesdatum

-   Lieferantennummer

-   Lieferscheinnummer Lieferant

-   Lieferscheindatum Lieferant

-   Sachbearbeiter Vor- und Nachname [adr_pers.v_name, n_name]

-   Seitennummer und Seitenanzahl

Auf der 1. Seite vor den Positionen:

-   Retourscheintext Einleitung [elfs_txt]

Pro Eingangslieferscheinposition:

-   Artikelnummer

-   Artikelbezeichnung und sonstige Texte lt. [elfs_pos_txt]

-   Menge in Einkaufseinheit

-   Einkaufsmengeneinheit

-   Bei Artikel mit Lagerkennzeichen "Gerät" je Seriennummer aus
    Lagerbewegungskartei

-   Fixtext "SerienNr:"

-   Gerätenummer

-   nur, wenn Lager ein Chargen-/Gerätelager ist

-   Bei Artikel mit Lagerkennzeichen "Charge" je Chargennummer aus
    Lagerbewegungskartei

-   Fixtext "Charge:"

-   Chargennummer

-   Summe der Buchungsmengen lt. [kartei_lagbew]

-   nur, wenn Lager ein Chargen-/Gerätelager ist

Nach der letzten Position:

-   Trennlinie

-   Retourscheintext Ende [elfs_txt], Logik w.o.

Im Seitenfuß:

-   Logo sofern vorhanden

Auswahl der Daten:

-   Eingangslieferscheinpositionen mit negativer Menge

Sortierung:

-   Artikelnummer

### Eingangsrechnung

Allgemeines

Vollständig abgeschlossene Eingangsrechnungen (FIBU und Warenwirtschaft)
dürfen mit Ausnahme des Infotextes nicht mehr geändert werden.

#### Auswahldialog

-   Firma

-   Rechnungsnummer intern

-   Rechnungsnummer Lieferant

-   Rechnungsdatum Lieferant

-   Lieferantennummer (f)

-   Lieferantenmatchcode

-   Sachbearbeiterkennzeichen

-   Rechnungsart

-   Erledigungskennzeichen Wawi (w)

-   offen

-   erledigt

-   Erledigungskennzeichen FIBU (w)

-   offen

-   erledigt

-   Prüf-Rechnungsnummer

-   KZ Dokumentenstatus (w)

-   Status (w)

#### Register "Liste"

-   WebdokFunktionalität

-   Firma

-   Rechnungsart

-   Rechnungsnummer Lieferant

-   Rechnungsdatum Lieferant

-   Lieferantennummer

-   Lieferantenmatchcode

-   Rechnungsbetrag exklusive Umsatzsteuer

-   Sollwert aus [elfs_pos]

-   Währungscode

-   Sachbearbeiterkennzeichen

-   Erledigungskennzeichen Wawi (c)

-   Zeitpunkt Wawi Verbucht

-   Erledigungskennzeichen FIBU (c)

-   Zeitpunkt FIBU verbucht

-   Prüf-Rechnungnsummer

-   Erfassungszeitpunkt

-   KZ-Dokumentenstatus

-   Status

#### Register "Detail"

-   Firma

-   Lieferantennummer (f)

-   Eingabelogik Matchcode u. Nummer

-   Lieferant muss aktiv sein

-   ggf. Anzeige Rechnungsinfo in eigenem Fenster

-   keine Eingabe bei Eingangsrechnungsart = "Storno" , Belegung lt.
    > Bezugsrechnung

-   Lieferantenmatchcode (a)

-   Kreditorennummer (f)

-   Vorschlag Neuanlage von Lieferant

-   Änderung erlaubt, wenn

-   keine Lieferscheinzeilen vorhanden

-   Rechnung noch nicht in FIBU verbucht

-   keine Eingabe bei Eingangsrechnungsart = "Storno" , Belegung lt.
    > Bezugsrechnung

-   evt. Prüfung der UID-Nummer -- siehe unten

-   wenn Kreditorennummer Lieferant <> Kreditorennummer

-   Name 1 Kreditor (a)

-   Name 2 Kreditor (a)

-   Lieferantensachkontenzuordnung (fd)

-   Vorschlag Lieferant

-   Änderung erlaubt, wenn

-   keine Lieferscheinzeilen vorhanden

-   Rechnung noch nicht in FIBU verbucht

-   keine Eingabe bei Eingangsrechnungsart = "Storno" , Belegung lt.
    > Bezugsrechnung

-   evt. Prüfung der UID-Nummer -- siehe unten

-   UID-Nummer des Kreditors (a)

-   Lieferantenadresse (a)

-   Status (a)

-   Rechnungsart (fd)

-   Rechnungsnummer Lieferant

-   bei Eingangsrechnungsart = "Storno", Vorschlag lt. Bezugsrechnung

-   Wenn es bereits eine ER bei diesem Lieferanten mit Belgdatem >=
    > Heute -- 365 Tagen gibt, so erfolgt ein Heinweis.

-   Rechnungsdatum Lieferant

-   bei Eingangsrechnungsart = "Storno", Vorschlag lt. Bezugsrechnung

-   Bezugsrechnungsnummer (f)

-   bei Rechnungsart = "Storno" nur bei der Neuanlage einzugeben

-   Bezugsrechnung muss bei Rechnungsart = "Storno" vollständig
    > verbucht sein [erech_zustand_kz = "v"]

-   wird, wenn unbestimmt, bei allen anderen Rechnungsarten beim
    > Speichern bestimmt

-   Eingangsrechnungsbarcode

-   Eingabe nur, wenn Eingangsrechnung gescannt wird [archiv.beleg_kz =
    > "er"]

-   sonst fix ""

-   fixer Defaultwert ""

-   KZ-Dokumentenstatus (d)

-   Kann manuell zwischen Fehlt und "Kein PDF" geändert werden.

-   Prüf Rechnungsnummer

-   Eingabe ist nur möglich, wenn die Rechnung noch nicht in der
    > Warenwirtschaft gebucht wurde.

-   Es kann hier auch nur eine Rechnung verwendet werden, die sich
    > selbst als Prüf-Rechnungsnummer eingetragen hat und die noch nicht
    > in der Warenwirtschaft gebucht wurde.

-   Prüf ER Belegnummer (a)

-   Prüf ER Belegdatum (a)

-   Zahlungskonditionen

-   Vorschlag Neuanlage von Kreditor

-   keine Eingabe bei Eingangsrechnungsart = "Storno", Belegung lt.
    > Bezugsrechnung

-   Valutadatum

-   keine Eingabe bei Eingangsrechnungsart = "Storno", Belegung lt.
    > Bezugsrechnung

-   Rechnungsinfotext

-   folgende Felder werden bei der Neuanlage vergeben:

-   Sachbearbeitercode Erfassung (a)

-   Interne Rechnungsnummer (a)

-   Erfassungsdatum (a)

-   Belastungsnote erstellen (d)

-   nur wenn lt. Firmenstamm Eingabe erlaubt

-   keine Eingabe bei Eingangsrechnungsart = "Storno", Belegung lt.
    > Bezugsrechnung

-   Rechnungs-Zu-/Abschlag Soll

-   keine Eingabe, wenn

-   Wawi verbucht

-   Belastungsnote bereits erstellt

-   Rechnungsart "ungeprüfte Eingangsrechung" und Fibu noch nicht
    > verbucht

-   bestimmt auch Zu-/Abschlag Ist

-   wenn Fibu nicht verbucht ist

-   bei Rechnungsart "ungeprüfte Eingangsrechnung"

-   Rechnungs-Zu-/Abschlag Ist

-   keine Eingabe, wenn

-   Rechnungsart "Belastungsanzeige"

-   Rechnungsart "Eingangsrechnung" und Fibu bereits verbucht

-   Rechnungsart "ungeprüfte Eingangsrechnung" und Fibu noch nicht
    > verbucht

-   keine Belastungsnote erstellt wird

-   Wawi und Fibu bereits verbucht

-   Rechnungs-Zu-/Abschlag Wawi absolut

-   keine Eingabe, wenn Wawi verbucht

-   Rechnungs-Zu-/Abschlag Wawi in %

-   keine Eingabe, wenn Wawi verbucht

-   Währungscode

-   Vorschlag Neuanlage lt. Lieferant

-   darf übersteuert werden

-   keine Eingabe bei Eingangsrechnungsart = "Storno", Belegung lt.
    > Bezugsrechnung

-   Wawi verbucht (c) (a)

-   Zeitpunkt Wawi verbucht (c)

-   FIBU verbuchucht (c) (a)

-   Zeitpunkt FIBU verbucht (c)

Anmerkung

-   Ist die Rechnung in der FIBU verbucht, dürfen die Felder
    Rechnungsnummer, Rechnungsdatum, Zahlungskondition und Valuta nicht
    mehr geändert werden.

UID-Prüfung

-   Die UID-Prüfung wird aufgerufen, wenn sich die Kreditorennummer oder
    die Lieferantensachkontengruppe ändern und wenn FIBU oder Wawi
    gebucht wird (nur bei der ersten).

-   Nicht bei Storno ERs

-   Wenn das UID-Prüf KZ lt. Lieferantensachkontengruppe auf Hinweis
    oder Sperre gesetzt ist.

-   Ist eine UID-Nummer am Kreditor hinterlegt und gültig (Prüf-KZ ohne
    UID oder Prüf-KZ = Alles ok und Datum letzte Prüfung > Today --
    Anzahl Tage lt. Parmeter uidpruef_tg)Im Dialog wird, wenn die FION
    Prüfung aktviert ist und die UID-Nummer ist gepfüft aber die Anzahl
    der Prüftage ist überschritten oder die UID-Nummer ist ungeprüft,
    die FION-Prüfung der UID-Nummer des Kreditor durchgeführt.

-   Es wird ein Hinweis mit der Fehlerursache ausgegeben:

-   Es ist keine UID-Nummer am Kreditor hinterlegt

-   UID-Nummer ist ungeprüft

-   UID-Nummer -- Adresse prüfen

-   UID-.Nummer ungültig

-   Letzte Prufung der UID-Nummer liegt zu weit zurück

-   Wird die Prüfung bei der Erfassung aufgerufen, so erfolgt nur ein
    Hinweis.

-   Wird die Prüfung im Zuge des Verbuchens aufgerufen und es eine
    Sperre definiert, so ist das Buchen nicht möglich.

**Anmerkung zum Speichern**

-   Hinweis "Scanbarcode fehlt !", wenn [archiv.beleg_kz = "er"]
    und Barcode ""

-   wird ein Barcode ungleich "" eingetragen, wird dieser in der
    Tabelle [pfu_scanzu] zusätzlich abgespeichert

-   wird ein Barcode geändert, wird der alte Wert aus Tabelle
    [pfu_scanzu] gelöscht

Drag+Drop

-   Wird ein PDF auf die ER gedroped, so wird dieses in die Dokumente
    mit Ausdrucksart "er_dok" und der Eingangsrechnungsnummer als
    Belegnummer verspeichert.

-   In diesem Fall wird auch das KZ-Dokumentestatus auf vorhanden
    gesetzt.

**Anmerkung zu "Stornorechnungen"**

Beim Speichern wird der Rechnungszustand der Bezugsrechnung erneut auf
"vollständig verrechnet" geprüft und auf "zu stornieren" gesetzt.
Folgende Datenbereiche werden automatisch mit den Daten der
Bezugsrechnung befüllt, wobei Mengen und Werte vorzeichengedreht
abgestellt werden:

-   Register "Spesen"

-   Register "Rechnungssumme" Kontierung und USt-Aufteilung

-   Register "StornoPos"

    Anmerkung zu Einwegpfand

Wenn er_ewpfand_jn = „j" , dann passiert bei jedem speichern wie folgt:

-   Es wird für die komplette ER die Summe des Einwegpfandes ermittelt
    und als SOLL und IST Wert in den Zuschlag(Spesen) lt
    artik.er_ewpfand_zuab_cd des Pfandartikels geschrieben.

-   Das sind alle Positionen, die einen Setteilartikel mit set_folge_kz
    = „e" haben

-   Liefermenge des Artikels multipliziert mit der Setteilmenge mal
    Verkaufspreis des Pfandartikels ergibt den Zuschlagswert pro
    Position

-   Wird dort ermittelt, wo auch die Kontierung aufgebaut wird.

#### Register "Lieferschein"

-   Bearbeitungsliste mit den, der Rechnung zugeteilten, Lieferscheinen

-   bei Rechnungsart "ungeprüfte Eingangsrechnung" nur aktiv, wenn die
    Verbuchung in der Fibu bereits erfolgt ist

-   für Stornorechnungen nicht verfügbar

-   Lieferscheinnummer (fd)

-   nur offene Lieferscheine

-   nur aktueller Lieferant

-   nur aktuelle Währung

-   Lieferscheindatum (a)

-   interne Lieferscheinnummer (a)

-   Lieferscheinwert Soll (a)

-   Lieferscheinwert Ist (a)

-   nur, wenn Belastung erstellt wird

-   Lieferschein-Zu-/Abschlag Soll

-   keine Eingabe wenn Wawi verbucht oder Belastungsnote bereits
    > erstellt

-   bestimmt auch Zu-/Abschlag Ist

-   wenn Fibu nicht verbucht ist

-   bei Rechnungsart "ungeprüfte Eingangsrechnung"

-   Lieferschein-Zu/Abschlag Ist

-   keine Eingabe wenn

-   Rechnungsart "Belastungsanzeige"

-   Rechnungsart "Eingangsrechnung" und Fibu bereits verbucht

-   keine Belastungsnote erstellt wird

-   Wawi und Fibu bereits verbucht

-   Lieferschein-Zu-/Abschlag Wawi absolut

-   keine Eingabe wenn Wawi verbucht

-   Lieferschein-Zu-/Abschlag Wawi in %

-   keine Eingabe wenn Wawi verbucht

    **Anmerkung**

-   Ist Wawi verbucht, darf bei Rechnungsart "ungeprüfte
    Eingangsrechnung" nicht eingefügt oder gelöscht werden.

-   Bei den Rechnungsarten "Eingangsrechnung" und
    "Belastungsanzeige" darf nicht eingefügt oder gelöscht werden,
    wenn die Rechnung in Wawi oder in Fibu verbucht ist.

    Nach Eingabe der Lieferscheinnummer werden die
    Lieferscheinpositionen sofort in den Register
    "Lieferschein-Detail" übertragen und die Lieferscheinwerte
    angezeigt. Wird eine Zeile gelöscht, werden auch die entsprechenden
    Detail-Zeilen entfernt.

    Nach Eingabe der Lieferscheinnummer kommt bei abweichenden
    Zahlungskonditionen von eventuell zugeordneten Bestellungen ein
    Tastentscheid, ob die Zahlungskonditionen lt. Bestellung übernommen
    werden soll.

    Wurde der Zu-/Abschlag Ist geändert und ist die Rechnung noch nicht
    in der Fibu verbucht, wird die Fibu-Kontierung gelöscht und neu
    aufgebaut. Die USt-Basis lt. Eingangslieferschein wird bei
    Rechnungsart "ungeprüfte Eingangsrechnung" auch bei bereits
    verbuchter Fibu neu aufgebaut.

#### Register "StornoPos"

-   nur für Stornorechnungen verfügbar

-   Anzeigeliste mit den stornierten Positionen der Rechnung

-   Lieferscheinnummer

-   Lieferscheindatum

-   Warenzugangsnummer

-   Positionsnummer

-   Artikelnummer

-   Artikelnummer Lieferant

-   Artikelmatchcode

-   gelieferte Menge Einkaufseinheit

-   Einkaufseinheit Einkaufspreis per Menge

-   Sollwerte der Position

-   fakturierte Menge in Einkaufseinheit

-   Einkaufspreis

-   Rabatt 1 - 5

-   Positionswert

-   Istwerte der Position

-   fakturierte Menge in Einkaufseinheit

-   Einkaufspreis

-   Rabatt 1 - 5

-   Positionswert

#### Register "LieferscheinPosition"

-   Bearbeitungsliste mit den Lieferscheinpositionen der Rechnung

-   für Stornorechnungen nicht verfügbar

-   bei Rechnungsart "ungeprüfte Eingangsrechnung" nur aktiv, wenn die
    Verbuchung in der Fibu bereits erfolgt ist

-   Lieferscheinnummer (a)

-   Positionsnummer (a)

-   Artikelnummer (a)

-   Artikelmatchcode (a)

-   Einkaufspreis per Menge (d)

-   gelieferte Menge (a)

-   Einkaufspreis per Einheit (d)

-   Einkaufseinheit

-   kleinste Einheit

-   Einkaufsmengeneinheit (a)

-   Sollwerte der Position

-   Die Veränderung eines Sollwertes, ändert automatisch den
    > entsprechenden Istwert

-   keine Eingabe, wenn Wawi verbucht oder Belastungsnote bereits
    > erstellt

-   bestimmt auch den entsprechenden Istwert

-   wenn Fibu nicht verbucht ist

-   bei Rechnungsart "ungeprüfte Eingangsrechnung"

-   fakturierte Menge

-   Einkaufspreis

-   Einkaufsrabatt 1

-   Einkaufsrabatt 2

-   Positionswert

-   Speichern (c)

-   Vorschlag "j" bei manueller Änderung von Preis oder Rabatt und
    > Automatischen Speichern ist am Lieferanten aktiviert.

-   Wenn aktiviert wird der Einkaufspreis in der
    > Aritkel-Lieferantendaten verspeichert -- siehe
    > Eingangslieferscheinposition.

-   Istwerte der Position

-   keine Eingabe wenn

-   Rechnungsart "Belastungsanzeige"

-   Rechnungsart "Eingangsrechnung" und Fibu bereits verbucht

-   keine Belastungsnote erstellt wird

-   fakturierte Menge

-   Einkaufspreis

-   Einkaufsrabatt 1

-   Einkaufsrabatt 2

-   Positionswert

Anmerkung

-   Neue Positionen können nur über den Register "Lieferschein"
    eingefügt werden. Ist Wawi verbucht, darf bei Rechnungsart
    "ungeprüfte Eingangsrechnung" keine Zeile gelöscht werden. Bei den
    Rechnungsarten "Eingangsrechnung" und "Belastungsanzeige" darf
    keine Zeile gelöscht werden, wenn die Rechnung in Wawi oder in Fibu
    verbucht ist.

-   Die Änderung eines Positionsbetrages wird sofort in den Register
    "Lieferschein" übertragen.

-   Wurde der Positionswert Ist verändert und ist die Rechnung noch
    nicht in der Fibu verbucht, wird die Fibu-Kontierung gelöscht und
    neu aufgebaut. Die USt-Basis lt. Eingangslieferschein wird bei
    Rechnungsart "ungeprüfte Eingangsrechnung" auch bei bereits
    verbuchter Fibu neu aufgebaut.

    Register wird gemeinsam mit Register "Lieferschein" gespeichert.

#### Register "Spesen"

-   Bearbeitungsliste mit den Zu-/Abschlägen der Rechnung

-   keine Änderungsmöglichkeit, wenn Rechnungsart = "Storno"

-   bei Rechnungsart "ungeprüfte Eingangsrechnung" nur aktiv, wenn die
    Verbuchung in der Fibu bereits erfolgt ist

-   Zu-/Abschlagscode (f)

-   Schnellsuche über Code und Matchcode

-   Zu-/Abschlagsmatchcode (a)

-   Lieferscheinauswahlfeld (d)

-   alle Lieferscheine lt. [erech_elfs]

-   zusätzlich ein Lieferscheinsatz für die Zuordnung "komplette
    > Rechnung"

-   Lieferscheinnummer = "Rechnung"

-   Lieferscheindatum = NULL

-   Warenzugangsnummer = 0

-   Lieferscheinnummer

-   Lieferscheindatum

-   Warenzugangsnummer

-   Lieferscheinnummer (a)

-   Warenzugangsnummer (a)

-   Zu-/Abschlag Soll

-   keine Eingabe wenn Wawi verbucht oder Belastungsnote bereits
    > erstellt

-   bestimmt auch Zu-/Abschlag Ist

-   wenn Fibu nicht verbucht ist

-   bei Rechnungsart "ungeprüfte Eingangsrechnung"

-   Rechnungs-Zu-/Abschlag Ist

-   keine Eingabe wenn

-   Rechnungsart "Belastungsanzeige"

-   Rechnungsart "Eingangsrechnung" und Fibu bereits verbucht

-   keine Belastungsnote erstellt wird

-   Wawi und Fibu bereits verbucht

-   Zuschlag nicht in Fibu gebucht wird

-   Infotext

**Anmerkung**

wurde ein für die Fibu massgeblicher Zuschlag geändert, wird die
Fibu-Kontierung gelöscht und neu aufgebaut.

#### Register "Rechnungssumme"

Keine Änderungsmöglichkeit, wenn Fibu verbucht oder wenn Rechnungsart =
"Storno"

**Teilbereich "Kopfdaten"**

-   Firma (a)

-   Lieferantennummer (a)

-   Lieferantenmatchcode (a)

-   Währungscode (a)

-   Rechnungsnummer Lieferant (a)

-   Rechnungsdatum Lieferant (a)

-   Rechnungsnummer intern (a)

-   Belastungsnote erstellen (a) (c)

-   Buchungsperiode

**Teilbereich "Kontierung"**

Bearbeitungsliste mit der Buchhaltungskontierung der Rechnung.

-   Rechnungsart "ungeprüfte Eingangsrechnung"

-   keine Vorbelegung durch Lieferscheindaten

-   keine Eingabe, wenn Wawi verbucht

-   Windowmodus ist "u"

-   Rechnungsart "Eingangsrechnung" oder "Belastungsanzeige"

-   Vorbelegung der Zeilen durch Lieferscheindaten

-   keine Eingabe, wenn Fibu verbucht

-   Windowmodus ist " "

-   Artikelsachkontenzuordnung (fd)

-   bestimmt gemeinsam mit der Lieferantensachkontenzuordnung, das
    > Sachkonto und die Ust

-   Eingabe nur bei Rechnungsart "ungeprüfte Eingangsrechnung"

-   Artikelkostenstellenzuordnung (fd)

-   bestimmt Kostenart, Kostenstelle und Kostenträger

-   Eingabe nur bei Rechnungsart "ungeprüfte Eingangsrechnung"

-   USt-Code (fd)

-   Sachkontonummer

-   Kostenstellennummer

-   Kostenartennummer

-   Kostenträgernummer

-   USt-Prozentsatz (a)

-   Änderung bewirkt Neuberechnung von Ust-Betrag

-   Differenz USt-Basis errechnet zu gebucht

-   USt-Basis lt. Elfs errechnet - USt-Basis gebucht

-   USt-Basis lt. Eingangslieferschein

-   USt-Basis

-   Ust-Betrag

-   Buchungstext

    **Summenzeile**

-   Differenz USt-Basis errechnet zu gebucht

    **Anmerkung**

    Durch eine Änderung wird der Teilbereich "UstSummen" neu
    berechnet. Ist in der Kontierungszeile eine Ust-Basis für die
    Belastungsnote hinterlegt, so kann die Zeile nicht gelöscht werden.

    Ist beim Speichern die Toleranzgrenze lt. Firmenstamm verglichen mit
    der Differenz der USt-Basen überschritten, wird ein Hinweis
    ausgegeben. Bei Rechnungsart "ungeprüfte Eingangsrechnung" ist das
    Speichern trotz überschrittener Toleranz erlaubt, bei allen anderen
    Rechnungsarten nicht.

**Teilbereich "UstSummen"**

Bearbeitungsliste mit den Summen je Ust-Code

-   Ust-Code (a)

-   Ust-Basis (a)

-   Ust-Prozentsatz (a)

-   Ust-Betrag (a)

-   Bruttobetrag (a)

-   Skontofähiger Betrag

-   als eigenes Felder unter der Tabelle

-   Summe Nettobetrag (a)

-   Summe Bruttobetrag (a)

**Teilbereich "UstSummen-EingangsrechnungsImport**

-   nur befüllt, wenn die Eingangsrechnung über den Import aufgebaut
    > wurde

Anzeigeliste mit den Summen je Ust-Code

-   Steuersatz

-   Nettobetrag

-   Ust-Betrag

-   Bruttobetrag

Teilbereich "Belastungsnote"

Wurde im Zuge der Rechnungsverbuchung eine Belastungsnote erstellt, so
werden bei späterer Abfrage folgende Felder angezeigt:

-   Belastungsnotennummer

-   Datum der Belastung

-   Nettobetrag

Teilbereich Summen(a):

-   Nettobetrag (eigene Rechnung)

-   Bruttobetrag (eigene Rechnung)

-   Summen über Prüf-Eingangsrechnung

-   Ust-Basen

-   Ust-Basen lt. Elfs

-   Differenzbetrag

#### Register "Text"

Bearbeitungsliste mit den Anfangs- bzw. Endtexten der "Belastungsnote"

-   Textstelle

-   Beleganfang

-   Belegende

-   Text

-   Fettdruck (c)

-   Unterstreichung (c)

Anmerkung

-    Textbausteine können eingefügt werden

#### Register "Belegkette"

-   siehe unter Allgemeines Abfrageregister "Belegkette"

#### Auswahlpunkte im Menü "Extras"

-   Rechnung in Wawi verbuchen

-   nicht, wenn bereits verbucht

-   für Stornorechnungen nicht verfügbar

-   ein Lieferschein muss zugeordnet sein oder eine Spesen-Zeile muss
    > vorhanden sein

-   Nicht möglich, wenn ein zugeordneter Lieferschein noch im Zustand
    > AVISO ist.

-   Belastungsnote zur Eingangsrechnung wird automatisch erstellt, wenn
    > Fibu bereits verbucht ist und Belastungsnote noch nicht gebucht
    > ist

-   für Rechnungsart "ungeprüfte Eingangsrechnung" nur möglich, wenn
    > Fibu bereits verbucht ist

-   bei Rechnungsart "ungeprüfte Eingangsrechnung" wird noch die
    > Toleranzgrenze geprüft, dabei wird allerdings die Summe aller
    > Eingangsrechnungen lt. pruef_erech_nr geprüft.

-   stammt die Rechnung aus dem Import, dann wird bei Abweichung der
    > Nettobeträge zwischen Import und Eingangsrechnung der User
    > gefragt, ab die Rechnung tatsächlich verbucht werden soll (nicht,
    > wenn bereits fibumäßig verbucht)

-   Rechnung in Fibu verbuchen

-   nicht, wenn lt. Firmenstamm keine Fibubuchung vorgesehen ist

-   für Stornorechnungen nicht verfügbar

-   nicht, wenn bereits verbucht

-   Kontierung muss vorhanden sein

-   Belastungsnote zur Eingangsrechnung wird automatisch erstellt, wenn
    > Wawi bereits verbucht ist, oder Belastung mit Fibu verbucht wird

-   Belastungsnote wird erstellt, wenn
    > Eingangsrechnung=Belastungsanzeige

-   stammt die Rechnung aus dem Import, dann wird bei Abweichung der
    > Nettobeträge zwischen Import und Eingangsrechnung der User
    > gefragt, ab die Rechnung tatsächlich verbucht werden soll (nicht,
    > wenn bereits wawimäßig verbucht)

-   Rechnung verbuchen

-   nur wenn Rechnung weder in Wawi noch in Fibu verbucht wurde

-   führt Wawi- und eventuell Fibu-Buchung durch

-   für Rechnungsart "ungeprüfte Eingangsrechnung" nicht möglich

-   führt bei Stornorechnungen die Stornobuchung durch

-   Rechnung erledigt setzen

-   nur möglich, wenn Wawi noch nicht verbucht und kein Lieferschein
    > zugeordnet ist

-   setzt bei Stornorechnungen

-   Bezugsrechnungsnummer auf Stornorechnungsnummer

-   Zustand "vollständig verbucht" bei Bezugsrechnung

-   FIBU Freigbe aufheben

-   Ist nur verfügbar, wenn das Rechnung in FIBU verbuchen durchgeführt
    > wurde und die FIBU Überleitung nocht nicht erfolgt ist
    > (efbueb_job_nr = 0 -- Locken und Prüfen) und wenn keine
    > Belastungsnote erstellt wurde.

-   Lösen Verbindung zu Eingangsrechnungsimport

-   setzt erechimp.erech_snr und erechimp.erech_nr auf 0,
    > erechimp.erechimp_status_kz auf "e" sowie erl_erechimp_snr auf
    > -1

-   nur, wenn Eingangsrechnung noch nicht verbucht ist

#### Schaltflächen für Verzweigungen

-   Dokumente

-   Zugeordnete Rechnungen

-   ER\`s mit dieser Prüf-ERNr

-   Importdaten

Verbuchung WAWI

-   Wird immer für alle ER´s mit derselben Prüf-Erech-Nr durchgeführt
    (das gilt auch für die oben beschriebenen Prüfungen).

-   Spesenaufteilung wird nicht durchgeführt, wenn Positionen mit
    positiver und negativer Menge vorhanden sind UND der
    Soll-Rechnungsbetrag der Spesensumme entspricht

-   Update Rechnungsdaten Eingangslieferscheinposition

-   Update Eingangsrechnung

-   Update Artikel und Gerät

-   durchschnittliche Einstandspreise (bewertet, vorläufig, abgewertet)

-   Spesen je Lieferschein bzw. für die ganze Rechnung berücksichtigt

-   durchschnittlicher Einkaufspreis

Verbuchung FIBU

-   Verbuchung der Kontierung in der FIBU

-   wenn Belastungsnote erstellt wird:

-   Druck der Belastungsnote mit Verbuchung lt. Kontierung in der FIBU

-   Aufbau von [erech_bn] für die Abfrage

    **Verbuchung Storno  
    **

-   Verbuchung ist eine Transaktion

-   Bezugsrechnung

-   Zustand wird auf "storniert" gesetzt

-   Bezugseingangslieferschein

-   Zustand wird auf "erfasst" oder auf "teilweise verrechnet"
    > gesetzt

-   Erledigt-Nummer wird auf 0 gesetzt

-   Bezugseingangslieferscheinposition

-   Einstandswert und Einkaufswert werden auf 0 gestellt

-   Rechnungsmonat wird auf "" gestellt

-   Rechnungsnummer, Ist-Felder und SollRechnungsmenge werden auf 0
    > gestellt

-   Statistik ist gebucht wird auf "n" gestellt

-   Stornorechnung

-   Zustand wird auf "vollständig verbucht" gesetzt

-   Eingangsrechnungsmonat wird gesetzt

-   Ist- und Sollwert des Eingangslieferscheins bleiben 0

-   Erledigtnummern für Wawi und Fibu werden gesetzt

-   Stornopos

-   Rechnungsmonat wird lt. Buchungsperiode gesetzt

-   DuEst-Berechnung pro Artikel, wie bei Eingangsrechnungsverbuchung

-   Rechnungssumme

-   Fibu-Verbuchung analog zu "Verbuchung FIBU"

-   neue Belastungsnote wird ggf. aufgebaut und zum Drucken vorgemerkt

#### Allgemeines

**Anmerkung zum Löschen**

-   wird eine Stornorechnung gelöscht, wird der Zustand der
    > Bezugsrechnung auf "vollständig verbucht" gesetzt

-   löschen ist nicht möglich, wenn die Rechnung in der Wawi bzw. der
    > Fibu verbucht ist oder ein Lieferschein zugeordnet ist

### Import Eingangsrechnungen

Auswahldialog

-   Firmennummer (p)

-   Quelle (pw)

-   Importpfad (p)

-   Archivpfad (o)

-   Wenn nicht angegeben dann der Importpfad + /bu

Ablauf

-   wenn Quelle = "sc"

-   Lesen aller \*.txt Dateien im angegebenen Verzeichnis

-   Pro Datei im angegebenen Verzeichnis

-   Öffnen Datei (im Lockmodus)

-   Befüllen der erechimp\*-Tabellen

-   Verschieben Datei in den Archiv-Ordner

-   bei fehlerhafter Datei: Job markieren und mit nächster Datei
    > weitermachen

-   Lesen aller \*.pdf-Dateien im angegebenen Verzsichnis

-   Pro Datei

-   Auslesen der Lieferantennummer(alles vor dem Bindestrich im
    > Filenamen) und der Rechnungsnummer (alles nach dem Bindestrich im
    > Filenamen)

-   Prüfen, ob es bereits eine importierte Rechnung mit dieser Nummer
    > gibt: wenn ja, Anlage eines pfu_job_druck-Datensatzes mit Druckart
    > = erechimp und DruckNr = erechimp_snr

-   Andere Quellen können individuell abgehandelt werden

-   Konvertieren der importierten Eingangsrechnungen

-   siehe EingangsrechnungImport-Extramenüpunkt

-   Autoaufbau/Autoverbuchung der Eingangsrechnungen

-   Status der Importrechnung muss "v" sein

-   nur Rechnungen, die mit dem aktuellen Job importiert wurden

-   Differenz zwischen den Beträgen der Rechnung und den Warenzugängen
    > in TradeControl muss jeweils kleiner als die Toleranzgrenze lt.
    > Lieferantenstamm sein

### Import - Eingangsrechnungen Bearbeitungsprogramm

Auswahldialog

-   Firmennummer (p)

-   Lieferantennummer

-   Quelle (w)

-   Rechnungsnummer Lieferant

-   Rechnungsdatum Lieferant

-   interne Eingangsrechnungsnummer

-   Status (w)

-   Erledigungskennzeichen (w)

Register Liste

-   Firmennummer

-   Lieferantennummer

-   Lieferantenmatchcode

-   Quelle

-   Rechnungsnummer Lieferant

-   Rechnungsdatum Lieferant

-   interne Eingangsrechnungsnummer

-   Status

-   Rechnungsbetrag Brutto

-   Rechnungsbetrag Netto

-   Infotext

Register Detail

Teilbereich Kopfdaten

-   Firmennummer (a)

-   Lieferantennummer

-   Lieferantenmatchcode (a)

-   ILN-Nummer Lieferant (a)

-   Name+Anschrift Lieferant lt. SST (a)

-   Quelle (ad)

-   Rechnungsnummer Lieferant (a)

-   Rechnungsdatum Lieferant (a)

-   interne Eingangsrechnungsnummer (a)

-   Rechnungsdatum intern(a)

-   Zustand (a)

-   Status (a)

-   Statustext (a)

-   Skonto1% (a)

-   Skonto1-Tage (a)

-   Nettotage (a)

-   Nettowert lt. SST (a)

-   Bruttowert lt. SST (a)

-   Skontobasis lt. SST (a)

-   Nettowert lt. TC (a)

-   Bruttowert lt. TC (a)

-   Infotext

    Teilbereich Belege (Bestellungen/Lieferscheine)

-   Bearbeitungsliste mit den konvertierten Belegen

-   manuelles hinzufügen möglich

-   Belegart

-   nicht eingebbar, wenn interne Lieferschein- oder Bestellnummer <>
    > 0

-   Firma

-   Filiale

-   interne Belegnummer

-   nicht eingebbar, wenn Belegart = "unbestimmt"

-   SST-Lieferscheinnummer (a)

-   SST-Lieferscheindatum (a)

-   SST-Bestellnummer (a)

-   SST-Bestelldatum (a)

-   Lieferadresse (a)

    Teilbereich UstSummen

-   Anzeigeliste

-   Ust-Code

-   Nettowert (s)

-   Steuerwert (s)

-   Bruttowert (s)

Teilbereich ZuAbschläge (a)

-   ZuAbKZ

-   ZuAbCd

-   Text

-   Proz

-   Wert

-   Steuersatz

    Teilbereich PositionsdatenBeleg

-   Anzeigeliste über den aktiven Beleg (Bestellung/Warenzugang) aus dem
    > Teilbereich "Beleg"

-   Übernahme (c)

-   nur dieses Feld darf eingegeben werden

-   bei Anklicken wird die Zeile im Teilbereich "PositionErfassung"
    > angelegt

-   Eingabe nur möglich, wenn im Teilbereich "Beleg" eine Zeile zum
    > "WarenzugangBuchen" markiert ist

-   Positionsnummer

-   Artikelnummer

-   Artikelmatchcode

-   Menge

-   Lagereinheit

-   Preis

-   PreisProMenge

-   Einkaufsverrechnungseinheit

-   Rabatt 1

-   Rabatt 2

-   Rabatt 3

-   Rabatt 4

-   Rabatt 5

-   Positionswert (s)

    Teilbereich PositionsdatenSST

-   Bearbeitungsliste mit den Positionedaten aus der Import-SST

-   Artikelnummer

-   Artikelbezeichnung 1-4 (a)

-   EAN-Nummer lt. SST (a)

-   Lieferantenartikelnummer lt. SST (a)

-   Menge (a)

-   Mengeneinheit lt. SST (a)

-   Mengeneinheit (a)

-   Verkaufspreis (a)

-   PreisProMenge (a)

-   Rabatt 1 (a)

-   Rabatt 2 (a)

-   Rabatt 3 (a)

-   Rabatt 4 (a)

-   Rabatt 5 (a)

-   Nettowert (as)

-   Steuersatz (a)

-   Auftragsnummer beim Lieferanten (a)

-   Auftragsdatum beim Lieferanten (a)

-   Lieferscheinnummer beim Lieferanten (a)

-   Lieferscheindatum beim Lieferanten (a)

-   Bestellnummer beim Lieferanten (a)

-   Bestelldatum beim Lieferanten (a)

-   interne Bestellnummer (a)

-   Lieferadresse (a)

-   Statustext (a)

-   Wird eine Artikelnummer zugeordnet, so werden beim Speichern ggf.
    > die EAN-Nummer/Lieferantenartikelnummer als Artikelidentifikation
    > hinzugefügt

#### Auswahlpunkte im Menü "Extras"

-   Daten konvertieren

-   noch nicht konvertierte Felder (Lieferantennummer, Artikelnummer,
    > Beleg) werden konvertiert

-   Daten konvertieren für alle Zeilen

-   Rechnung aufbauen

-   es müssen Belege vorhanden sein

-   alle Belege müssen Belegart = "Lieferschein" haben

-   alle Positionen der zugeordneten Belege müssen einen Preis haben

-   Ust-Abgleich

-   Der Ust Abgleich wird nur durchgeführt, wenn die Summe der Ust-Basis
    > oder der Ust-Beträge des Imports und der TC-ER voneinander
    > abweichen.

-   Wenn nicht jeder Steuersatz, der vom Import verwendet wird genau 1x
    > auch in der ER verwendet wird oder umgekehrt wird dein Fehler beim
    > Ust-Abgleich gemeldet.

-   Ansonsten werden Ust-Basis und Ust-Betrag aus dem Import übernommen

-   interne Rechnung wird aufgebaut

-   zugeordnete PDF\'s werden der Eingangsrechnung übertragen (nur bei
    > sc)

-   ist der Aufbau ok, so bleibt die Eingangsrechnung geöffnet

-   Rechnung ausbauen und verbuchen

-   siehe Menüpunkt "Rechnung aufbauen"

-   zusätzlich wird die Eingangsrechnung sofort verbucht

-   ist der Aufbau ok und nur das Verbuchen fehlerhaft, so bleibt die
    > Eingangsrechnung geöffnet

-   Rechnung erledigen

#### Schaltflächen 

-   Dokumente

-   Position

-   öffnet das Positionefenster
    > (Eingangslieferscheinposition/Bestellposition) des aktuellen
    > Belegs aus dem Teilbereich "Belege"

-   nur aktiv, wenn die Tabpage "Detail" die aktive Tabpage ist

### Belastungsnote Druck

Listbild:

[bn.doc](file:///\\pcssrv019\projekte\tradecon\org\bn.doc)**  
**

Seitenkopf:

-   Adresskopf

-   Lieferantenanschrift [lief.lief_name1 bis lief.lief_ort], wenn
    > Kreditorennummer Lieferant = Kreditorennummer Eingangsrechnung

-   Kreditorenanschrift [name1 bis ort], wenn Kreditorennummer
    > Lieferant <> Kreditorennummer Eingangsrechnung

-   Belegtitel lt. erechart_sprache.bn_beleg_txt

-   Belastungsnotennummer

-   Tagesdatum

-   Lieferantennummer

-   Rechnungsnummer Lieferant

-   Rechnungsdatum Lieferant

-   Sachbearbeiter Vor- und Nachname [adr_pers.v_name, n_name]

-   Seitennummer und Seitenanzahl

Auf der 1. Seite vor den Positionen:

-   Belastungsnotentext Einleitung [erech_txt]

Positionsüberschrift je Seite:

-   Währungscode

Pro Eingangslieferschein:

-   Vor den Positionen:

-   Warenzugangsnummer

-   Eingangslieferscheinnummer

-   Eingangslieferscheindatum

-   Nach den Positionen

-   Zuschlag Ist

-   wenn Belastung zur Eingangsrechnung

-   Zuschlag Soll

-   Differenzbetrag

-   wenn Eingangsrechnung=Belastung

-   Positionsbetrag (=Zuschlag Ist)

Pro Eingangslieferscheinposition:

-   Artikelnummer

-   Artikelbezeichnung und sonstige Texte lt. [elfs_pos_txt]

-   Fixtext "Ihre Nr:" und Lieferantenartikelnummer

-   wenn Belastung zur Eingangsrechnung

-   in 2 Zeilen Ist- und Sollwerte der Eingangslieferscheinposition

-   Fixtext "bestellt" bzw. "Ihre Faktura"

-   fakturierte Menge

-   Mengeneinheit

-   Einkaufspreis

-   Rabatt 1, wenn ungleich 0

-   Rabatt 2, wenn ungleich 0

-   Nettodifferenzbetrag zwischen Soll und Ist

-   wenn Eingangsrechnung=Belastung, folgende Istwerte

-   fakturierte Menge

-   Mengeneinheit

-   Einkaufspreis

-   Rabatt 1, wenn ungleich 0

-   Rabatt 2, wenn ungleich 0

-   Nettobetrag

Nach der letzten Position:

-   Rechnungszuschlag Soll

-   wenn Belastung zur Eingangsrechnung

-   Zuschlag Ist

-   Differenzbetrag

-   wenn Eingangsrechnung=Belastung

-   Positionsbetrag (=Zuschlag Ist)

-   Trennlinie

-   Währungscode

-   Rechnungsendbetrag inkl. Umsatzsteuer

-   je Umsatzsteuercode, wenn Inlandskunde

-   USt-Symbol

-   USt-Prozentsatz

-   USt-Basis

-   USt-Betrag

-   wenn doppelte Preisauszeichnung aktiviert

-   Belegwährung ist EUR

-   Rechnungsendbetrag in ATS

-   Belegwährung ist nicht EUR

-   Rechnungsendbetrag in EUR

-   USt-Text lt. USt-Tabelle

-   Belastungsnotentext Ende [erech_txt], Logik w.o.

-   Endetextzeilen lt. [fa.bn_txt_cd txt_txt.txt_txt]

Im Seitenfuß:

-   Logo sofern vorhanden

Auswahl der Daten:

-   wenn Belastung zu Eingangsrechnung, Differenzen zwischen Soll- und
    Ist-Werten in

-   Lieferscheinpositionen

-   Lieferscheinzuschlägen

-   Rechnungszuschlägen

Sortierung:

-   Artikelnummer

Update:

-   erech_bn, wenn Belastung zu Eingangsrechnung

-   Sonst - erech.erech_pdf_kz = \'v\'

### Liste der offenen Bestellungen

Listbild:

[offbest.doc](file:///\\pcssrv019\projekte\tradecon\org\offbest.doc)

Aufruf:

Werteingaben:

-   Firmennummer (p)

-   Bestellvorschlagscode (w)

-   Bestellart (w)

-   Lieferantennummer (f)

-   Zustandskennzeichen (w)

-   Lieferwoche

-   Lieferdatum

-   Verarbeitungskennzeichen (p)

-   mit Bestellvorschlagsdaten

-   ohne Bestellvorschlagsdaten

Seitenkopf:

-   Firmenkurzbezeichnung [fa.fa_adr_snr adr.adr_mc]

-   Tagesdatum

-   Uhrzeit

-   Seitennummer und Seitenanzahl

-   Positionsüberschriftszeile

-   Positionsüberschriftszeile Bestellvorschlag wenn ausgewählt

    **Pro Lieferant**

-   Lieferantennummer

-   Lieferantenmatchcode

Pro Bestellung

-   Bestellart

-   Bestellnummer

-   Bestelldatum

-   Währungscode

-   Lieferantenauftragsnummer

Pro Bestellposition

-   Positionsnummer

-   Artikelnummer

-   bestellte Menge

-   offene Menge

-   Einkaufsseinheit

-   Einkaufspreis

-   Rabatt 1

-   Rabatt 2

-   Staffelmenge (fett)

-   Positionsbetrag in Bestellwährung

-   Lieferwoche bzw. wenn nicht leer bestätigte Lieferwoche

-   "B" wenn bestätigt

-   Lieferdatum bzw. wenn nicht leer bestätigtes Lieferdatum

-   "B" wenn bestätigt

-   Mahnstufe

-   Datum zuletzt gemahnt

-   Auftragsnummer

-   Auftragspositionsnummer

-   Folgezeile:

-   Artikelmatchcode aus Bestellposition

-   Kundenmatchcode lt. Kunde des zugeordneten Auftrages (rechtsbündig)

-   Folgezeilen wenn Bestellvorschlag ausgewählt:

-   Lagerstand

-   reservierte Menge aus Kundenaufträgen

-   bestellte Menge aus Lieferantenbestellungen

-   verfügbare Menge

-   Kennzeichen Mindestbestand (f/e)

-   Mindestbestand

-   Verkaufsmengeneinheit

-   Mindestbestellmenge (wenn größer 1)

-   Einkaufsmengeneinheit (wenn Mindestbestellmenge gedruckt)

-   Verbrauchsdaten lfd. Jahr (Gruppenschema "verbrauch", "a1")

-   Verbrauchsdaten Vorjahr (Gruppenschema "verbrauch", "a2")

Summenzeile Lieferant

-   Währungscode Grundwährung

-   Bestellwert in Grundwährung

Summenzeile Gesamt

-   Währungscode Grundwährung

-   Bestellwert Gesamt in Grundwährung

Auswahl der Daten:

-   best

-   erl_best_nr = 0

-   best_pos

-   best_pos.best_off_mg <> 0

-   p_erl_best_nr = 0

Sortierung:

-   Lieferantenmatchcode

-   Lieferantennummer

-   Bestellnummer

-   Positionsnummer

### Liste offene Lieferscheine Einkauf

Listbild:

[offelfs.doc](file:///\\pcssrv019\projekte\tradecon\org\offelfs.doc)

Aufruf:

Werteingaben:

-   Firmennummer (p)

-   Lieferantennummer

-   Eingangslieferscheindatum

Seitenkopf:

-   Firmenkurzbezeichnung [fa.fa_adr_snr adr.adr_mc]

-   Tagesdatum

-   Uhrzeit

-   Seitennummer und Seitenanzahl

-   Positionsüberschriftszeile

    **Pro Lieferant**

-   Lieferantennummer

-   Lieferantenmatchcode

Pro Eingangslieferschein

-   Warenzugangsnummer intern

-   Warenzugangsdatum

-   Währungscode

-   Lieferscheinnummer Lieferant

-   Lieferscheindatum

Pro Lieferscheinposition

-   Positionsnummer

-   Artikelnummer

-   Matchcode aus Lieferscheinposition

-   gelieferte Menge

-   Einkaufsseinheit

-   folgende Soll-Felder

-   Einkaufspreis

-   Rabatt 1

-   Rabatt 2

-   Rabatt 3

-   Betrag

Summenzeile Lieferant

-   Währungscode Grundwährung

-   Bestellwert in Grundwährung

Summenzeile Gesamt

-   Währungscode Grundwährung

-   Bestellwert Gesamt in Grundwährung

Auswahl der Daten:

-   elfs

-   elfs_pos

-   erech_nr = 0

Sortierung:

-   Lieferantenmatchcode

-   Lieferantennummer

-   Warenzugangsnummer

-   Positionsnummer

### Verbrauchsabfrage Artikel

**Allgemeines**

-   Fenster dient zur Abfrage der monatlichen Artikelverbräuche, es
    können jedoch keine Änderungen durchgeführt werden

#### Auswahldialog

-   Firma (p)

-   Artikelnummer (p)

#### Register "Liste"

-   Daten je Monat und Jahr ( 4 Spalten mit dem aktuellen Jahr und den
    letzten 3 Jahren)

-   Monat

-   Verbrauch

**Anmerkung**

Die Spalten sind absummiert und zeigen die jeweilige Jahressumme

### Umsatzabfrage Lieferant

**Allgemeines**

-   Fenster dient zur Abfrage der monatlichen Lieferantenumsätze, es
    können jedoch keine Änderungen durchgeführt werden

#### Auswahldialog

-   Firma (p)

-   Lieferantennummer (p)

#### Register "Liste"

-   Daten je Monat und Jahr ( 4 Spalten mit dem aktuellen Jahr und den
    letzten 3 Jahren)

-   Monat

-   Umsatz

**Anmerkung**

Die Spalten sind absummiert und zeigen die jeweilige Jahressumme

## Inventur

### Inventurabgrenzung

#### Auswahldialog

-   Firma (p)

-   Lagernummer (w)

-   Artikelnummer (f)

-   Datum der letzten Inventur

-   Lagerort

-   Lagerortauswahl bezieht sich auf fixen Lagerort 1 lt. ArtikelLager

-   keine Funktion bei Lagerführung auf Lagerortebene, da ArtikelLager
    > die kleinste inventierbare Einheit darstellt

-   Inventurabgrenzungsdatum (p)

-   Vorschlag Systemdatum

-   Belegung Istlagerstand (p)

-   unbestimmt

-   0

-   Solllagerstand

Auswahl der Daten

-   Nur Artikel mit Lagerführung

-   Nur [artik_lag]-Sätze für die keine Inventur offen ist

-   Nur [artik_lag]-Sätze mit Lagerstand <> 0 oder Bewegung seit
    letzter Inventur

-   Nur eigene Lager [lag.lag_kz = \'e\']

-   Alle Sätze aus [artik, artik_lag] die der Auswahl entsprechen

Ablauf

-   Verarbeitung der Daten sortiert nach Lagernummer, Lagerort 1 lt.
    [artik_lag] und Artikelnummer

-   Ist ein Artikel in die Inventur aufzunehmen:

-   Abspeichern des Inventursatzes [iv]

-   nur bei der 1. Position der Verarbeitung

-   Vergabe der Inventurnummer

-   Abspeichern des Inventurbereichsatzes [iv_bereich]

-   nur bei Wechsel des Inventurbereiches (abhängig von Zeilenanzahl im
    > Firmenstamm)

-   wenn Anzahl Stellen Regal lt. Firmenstamm [fa.iv_regal_stellen]
    > <> 0 wird ein neuer Bereich nur pro Lager erstellt

-   Vergabe der laufenden Bereichsnummer

-   Abspeichern der Inventurposition [iv_zeile]

-   entspricht einem Datensatz aus [artik_lag_sub]

-   Belegung Sortiernummern

-   optional, wenn [fa.iv_regal_stellen] <> 0

-   Endemeldung des Batchlaufes

-   Inventurnummer

-   Bereichsanzahl

### Inventurzählliste Druck

Listbild:

[ivzaehl.doc](\\\\pcssrv019\\projekte\\tradecon\\org\\ivzaehl.doc)

Aufruf:

Werteingaben:

-   Firma (p)

-   Inventurnummer (p)

-   Inventurbereichsnummer

-   Sollstand drucken (p)

-   Iststand drucken (p)

-   Differenzen drucken (p)

Auswahl der Daten:

-   lt. Eingabe aus den Inventurtabellen

-   bei Auswahl "Differenzen" nur jene Zeilen für die gilt: Sollmenge
    <> Istmenge

**1. Liste nach Bereichen**

-   [fa.iv_regal_stellen = 0]

Seitenkopf:

-   Inventurnummer

-   Lagernummer

-   Inventurbereich

-   Firmenkurzbezeichnung [fa.fa_adr_snr adr.adr_mc]

-   Tagesdatum

-   Uhrzeit

-   Seitennummer und Seitenanzahl

Pro Lagerplatz/Artikel:

-   Lagerplatz

-   Artikelnummer

-   Artikelmatchcode

Pro Inventurzeile:

-   Fixtext "SN:" bzw. "CH:" bei Artikel mit Seriennummern- bzw.
    Chargenverwaltung

-   Serien- bzw. Chargennummer aus Inventurzeile

-   Sollmenge

-   wenn ausgewählt

-   Istmenge

-   wenn ausgewählt

-   Differenzmenge

-   wenn ausgewählt

-   Differenzwert

-   wenn ausgewählt

-   am Ende Summe

-   Trennstrich

Sortierung:

-   Inventurbereich

-   Lagerplatz

-   Artikelnummer

-   Chargen/Gerätenummer

**2. Liste nach Sortiernummern**

-   [fa.iv_regal_stellen <> 0]

Seitenkopf:

-   Inventurnummer

-   Lagernummer

-   Bereich

-   Sortiernummer 1

-   Firmenkurzbezeichnung [fa.fa_adr_snr adr.adr_mc]

-   Tagesdatum

-   Uhrzeit

-   Seitennummer und Seitenanzahl

Pro Inventurzeile:

-   Positionsnummer

-   Sortiernummer 2

-   Lagerplatz

-   ListeLagerOrt

-   Artikelnummer

-   Artikelmatchcode

-   Fixtext "SN:" bzw. "CH:" bei Artikel mit Seriennummern- bzw.
    Chargenverwaltung

-   Serien- bzw. Chargennummer aus Inventurzeile

-   Sollmenge

-   wenn ausgewählt

-   Istmenge

-   wenn ausgewählt

-   Differenzmenge

-   wenn ausgewählt

-   Differenzwert

-   wenn ausgewählt

-   am Ende Summe

-   Trennstrich

Sortierung:

-   Inventurbereich >

-   Sortiernummer 1 > bei Wechsel, neue Seite

-   Sortiernummer 2

### Inventurbereich

**Allgemeines**

-   Neuanlage und Löschen nicht möglich

#### Auswahldialog

-   Firma

-   Inventurnummer

-   Inventurbereichsnummer

-   Lagernummer (w)

-   Inventureröffnungsdatum

-   Inventurabschlussdatum

-   Artikelnummer (f)

-   erledigte Inventuren anzeigen (w)

-   Zustand Inventur (w)

#### Register "Liste"

-   Firma

-   Inventurnummer

-   Inventurbereichsnummer

-   Lagernummer

-   Inventureröffnungsdatum

-   Inventurabschlussdatum

-   Zustandskennzeichen

#### Register "Detail"

-   Firma (a)

-   Inventurnummer (a)

-   Inventurbereichsnummer (a)

-   Lagernummer (a)

-   Lagerbezeichnung (a)

-   Zustandskennzeichen (a)

-   Inventureröffnungsdatum (a)

-   Inventurabschlussdatum (a)

#### Schaltflächen für Verzweigungen

-   Inventurzeile

-   MDE

### Inventurzeile (Inventurerfassung)

Auswahldialog

-   Firma

-   Inventurnummer (w)

-   Lagernummer (w)

-   Artikelnummer (f)

-   Lagerort

-   Chargen/Gerätenummer

-   Sortiernummer 1

-   Sortiernummer 2

-   Differenzmenge

-   Istmenge -- Sollmenge

-   Wertevorrat

-   > 0

-   < 0

-   <> 0

Register "Liste"

-   Kennzeichen "Position verbucht"

-   Artikelnummer

-   Artikelmatchcode

-   Lagerort

-   Eingabe möglich

-   Chargen- bzw. Gerätenummer

-   Eingabe möglich, wenn Lagerführung auf Geräte- bzw. Chargenebene und
    > Lager Chargen-/Geräteverwaltung [lag. cg_verw_jn = "j"] hat

-   Sollmenge

-   Istmenge

-   Eingabe möglich

-   Lagereinheit (a)

-   Ablaufdatum

-   Eingabe möglich wenn Charge mit Ablaufdatum geführt wird und Lager
    > Chargen-/Geräteverwaltung [lag. cg_verw_jn = "j"] hat

-   Kennzeichen manuell angelegte Position

-   Firma

-   Inventurnummer

-   Inventurbereichsnummer

-   Lagernummer

-   Sortiernummer 1

-   Sortiernummer 2

Register "Detail"

-   Firma (a)

-   Inventurnummer (a)

-   Inventurbereichsnummer (a)

-   Lagernummer (a)

-   Kennzeichen "Position verbucht" (a)

-   Artikelnummer (f)

-   Artikel muss aktiv sein

-   Artikel muss Lagerführung haben

-   aktiv, wenn Zeile neu angelegt wird

-   Artikelmatchcode

-   Listbox Lagerorte (d)

-   aktiv, wenn Lagerstand auf Lagerortebene geführt wird und die
    > Sollmenge 0 ist

-   definiert Lagerort

-   folgende Felder im Auswahlfenster:

-   Lagerort

-   Lagerort

-   aktiv, wenn Lagerstand auf Lagerortebene geführt wird, der Lagerort
    > editierbar ist und die Sollmenge 0 ist

-   Chargen- bzw. Gerätenummer

-   aktiv, wenn Lagerführung auf Geräte- bzw. Chargenebene, die
    > Sollmenge 0 ist und Lager Chargen-/Geräteverwaltung [lag.
    > cg_verw_jn = "j"] hat

-   Sollmenge (a)

-   bei Neuanlage 0

-   Istmenge

-   bei Geräteartikel nur 0 oder 1 erlaubt

-   Mengeneingabefenster

-   Sortiernummer1

-   Sortiernummer2

-   Lagereinheit (a)

-   Ablaufdatum

-   aktiv, wenn Charge mit Ablaufdatum geführt wird und Lager
    > Chargen-/Geräteverwaltung [lag. cg_verw_jn = "j"] hat

-   Kennzeichen manuell angelegte Position (a)

Anmerkungen

-   bereit verbuchte Zeilen [iv_zeile.erl_iv_nr > 0] dürfen nicht
    geändert und nicht gelöscht werden

-   wenn Inventurbereich erledigt ist [iv_bereich.zustand_kz = "e",
    "s"], ist eine Neuanlage nicht erlaubt

-   Neuanlage nur möglich, wenn von Inventurbereich geöffnet

-   ist eine Zeile durch die Inventurabgrenzung (d.h. nicht manuell)
    angelegt worden, so darf sie nicht gelöscht werden.

**Prüfungen beim Speichern:**

-   wenn Sortiernummer 1 unbestimmt

-   höchste Sortiernummer der Inventur

-   wenn Sortiernummer 2 unbestimmt

-   0, wennSortiernummer1 = 0

-   höchste Sortiernummer2 + 1 der Inventur innerhalb von Sortiernummer
    > 1, wenn Sortiernummer1 > 0

-   Geräte mit Sollstand = 1 und Iststand = 0 müssen lagernd sein und
    dürfen nicht reserviert sein. Das Zustandskennzeichen im Gerätestamm
    darf nicht "kr" und nicht "lr" sein.

-   ist bei Geräten mit Sollstand = 0 und Iststand = 1 ein
    Gerätestamm-Datensatz vorhanden, so sind nur folgende
    Zustandskennzeichen zulässig: "k", "r", "a"

-   ist bei Artikeln mit Lagerplatz und/oder Geräte- bzw.
    Chargenverwaltung eine Ist-Menge <> 0 eingetragen, so muss der
    Lagerplatz und/oder die Geräte- bzw. Chargennummer gefüllt sein

-   Die eingelesenen Daten müssen beim Speichern den Daten in der
    Datenbank entsprechen

Buttons

-   MDE

### MDE-Inventur (TC-Next)

Einstiegsmaske:

-   Userkürzel

-   Lager (d)

-   Kann über User Konstant gesetzt werden

-   Inventurnummer

-   Auswahl aus allen offenen Inventuren des Lagers (lt. iv_bereich)
    > möglich

-   Inventurbereich

Buttons

-   Erfassen

-   Abfrage

Erfassen

-   Lagerort

-   Eingabe nur bei Lager mit Lagerortverwaltung

-   Artikel-Scannfeld

-   EAN oder Artikelcode

-   EAN128 ist ebenfalls Möglich -- siehe Unten

-   Artikel muss im aktuellem Lager der aktuellen Inventur oder noch
    > keine Inventur zugeordnet sein.

-   In einem Lager mit Lagerortverwaltung wird geprüft, ob der der
    > Artikel in diesem Lagerort bereits erfasst wurde. Wenn ja erfolgt
    > ein TE "Artikel an diesem Lagerort bereits gebucht. Diese Buchung
    > Ändern ?/Ja/Nein.

-   Artikelcode (a)

-   Artikelmatchcode (a)

-   Chargen-/Gerätenummer

-   Eingabe nur bei Geräte oder Chargenartikel möglich

-   Auswahl über Liste über die in artik_lag_sub vorhandenen
    > Geräte/Chargen

-   Menge in Einheit

-   Zwingende Eingabe für jede Position

-   Bei einem Geräteartikel nur 1 oder -1 erlaubt

-   Durch diese Menge darf die Summe der erfassten Mengen für den
    > Artikel/Lagerort nicht negativ werden

-   Mengeneinheit (d)

-   Es können die Lagereinheit (Default, wenn nicht über EAN bestimmt),
    > die Verkaufs- und Einkaufseinheiten verwendet werden.

-   Wenn über EAN eine Einheit zugewiesen werden kann, dann wird diese
    > Einheit vorgeschlagen.

-   Ist Menge bisher in Lagereinheit

-   Summer der erfassten Menge des Artikels auf diesem Lagerort in der
    > aktuellen Inventur

-   Kann bei einer Änderung eingegeben werden, damit wird die Differenz
    > als erfasste Menge eingetragen.

-   Darf bei Gerät nur 1 oder 0 sein

-   Lagereinheit (a)

EAN128:

Es werden folgende Teile (AI) des EAN 128 interpretiert:

-   01 = EAN

-   Der EAN ist im EAN128 14stellig enthalten. Wenn die erste Stelle
    > eine 0 ist, können die nächsten 13stellen als EAN verwendet
    > werden.

-   Wenn die erste Stelle eine 9 ist, so müssen die nächsten 12stellen
    > verwendet werden und die Prüfziffer für den in TC hinterlegten EAN
    > neu berechnet werden, da die Prüfziffer im EAN128 Code inklusive
    > der führenden 9 berechnet wurde.

-   02 = EAN (kann nur vorkommen wenn 01 nicht angegeben wurde)

-   10 = Chargennummr

-   11 = Herstelldateum im Format JJMMTT

-   15 = MHD im Format JJMMTT

-   17 = Verfalldatum im Format JJMMTT

-   21 = Seriennummer

-   Sind Chargennummer und Seriennummer vorhanden wird abhängig vom
    > Artikel Lager Kennzeichen eines der beiden übernommen. Wenn der
    > Artikel weder Chargen- noch Gerätelagerführung hat, wird in diesem
    > Fall die Gerätenummer verwendet.  
    > Dadurch, dass damit eine Chargennummer auch bei nicht
    > Chargenartikeln in der Erfassungtabelle verwendet wird, erfolgt
    > beim Abscannen unterschiedlicher Chargen keine Summierung der
    > Mengen und damit auch keine Frage ob ich den Artikel wirklich
    > nochmal erfassen möchte.

-   30 = Menge in der Einheit des EAN´s (wird nur bei EAN 01 beginnend
    mit 0 verwendet)

-   310(x) = Nettogewicht in KG (wird nur bei EAN 01 beginnend mit 9
    verwendet)  
    Das x sagt aus wieviele gedachte Nachkommastellen im 6stelligen
    Gewichtsfeld enthalten sind.  
    z.B. 3103005097 = 5,097 KG

-   37 = Menge in EAN Einheit -- wird nur bei EAN 02 verwendet.

Buttons

-   Speichern

-   Verwerfen

-   Ende

Abfrage

Liste über die Inventurpositionen der aktuellen Person:

-   Lagerort

-   Artikelcode

-   Artikelmatchcode

-   Menge

-   Einheit

-   Zeitpunkt der Erfassung

-   Chargen-/Gerätenummer

**  
**

### MDE Inventur Verbuchen

Auswahlkriterien

-   Firma (p)

-   Inventurnummer (w)

-   Inventurbereich

Ablauf

Pro zu verbuchenden Datensatz in iv_mdeerf

-   Sperren iv_mdeerf

-   Prüfen Status iv_mdeerf (wenn inzwischen erledigt, weiter mit
    nächstem Datensatz)

-   Ist die entsprechende Inventur Zeile nicht vorhanden -- Neuanlage

-   Es mus dabei bereücksichtigt werden, dass die Chargen/Gerätenummer
    > bei iv_mdeerf Datensätzen, die über EAN128 eingelesen wurden auch
    > bei Artikeln belegt sein könnten, die in TC keine Lagerführung auf
    > Chargen- oder Geräteebene haben könnten.

-   Gezählte Menge in der Inventurzeile erhöhen

-   Update Status und erledigt Zeitpunkt iv_mdeerf

-   Job wird nicht markiert, wenn es keine zu verarbeitenden Daten gibt

### MDE Inventur Abfrage

Auswahlkriterien

-   Firma

-   Inventurnummer

-   Inventurbereich

-   Artikelnummer

-   Artikelmatchcode

-   Lagerort

-   Erfassungzeitpunkt

Liste

-   laufende Nr.

-   Firma

-   Inventurnummer

-   Inventurbereich

-   Artikelnummer

-   Artikelmatchcode

-   Lagerort

-   Charge/Gerät

-   Menge

-   Mengeneineheit

-   Herstellungdatum

-   MHD Datum

-   Ablaufdatum

-   MDE Personencode

-   MDE User

-   Erfassungszeitpunkt

-   Buchungszeitpunkt

###  Inventurabschluß

**Auswahldialog**

-   Firma (p)

-   Inventurnummer (p)

Auswahl der Daten

-   Daten der ausgewählten Inventur

-   Inventurzustand muss "eröffnet" oder "teilweise erledigt" sein

Ablauf

-   Vorlauf

-   bei allen Inventurzeilen wird geprüft

-   Ist-Menge darf nicht leer sein

-   bei allen Geräten mit Sollstand = 1 und Iststand = 0 wird geprüft

-   Gerät muss lagernd sein und darf nicht reserviert sein

-   Das Zustandskennzeichen im Gerätestamm darf nicht "kr" und nicht
    > "lr" sein.

-   bei allen Geräten mit Sollstand = 0 und Iststand = 1 wird geprüft

-   Gerät darf nicht lagernd sein

-   Ist ein Gerätestamm-Datensatz vorhanden, so muss das
    > Zustandskennzeichen "k", "r" oder "a" sein

-   Im Fehlerfall Druck eines Protokolls und Abbruch

-   Verarbeitung der Inventurzeilen sortiert nach Bereich und
    Artikelnummer

-   nur jene Zeilen, welche noch nicht gebucht wurden

-   pro Artikel im Bereich:

-   Korrektur Lagerbestände [artik, artik_lag]

-   Eintrag Inventurnummern in [artik_lag]

-   Beginn/Ende Transaktion

-   bei der 1. Zeile

-   Inventur auf "teilweise erledigt" setzen

-   pro Zeile

-   Korrektur Lagerbestand in [artik_lag_sub]

-   Anlage von Datensatz in [kartei_lagbew]

-   Prüfungen wie bei Vorlauf, im Fehlerfall Druck Protokoll und Abbruch

-   nach der letzten Zeile

-   Inventur auf "erledigt" setzen

-   Endemeldung des Batchlaufes

-   Inventurnummer

-   Bereichsanzahl

### Inventurstorno

#### Auswahldialog

-   Firma (p)

-   Inventurnummer (p)

Auswahl der Daten

-   Daten der ausgewählten Inventur

-   Inventurzustand muss "eröffnet" oder "teilweise storniert" sein

Ablauf

-   Verarbeitung der Inventurzeilen sortiert nach Bereich und
    Artikelnummer

-   pro Artikel im Bereich:

-   Eintrag 0 bei offener Inventurnummer in [artik_lag]

-   Beginn/Ende Transaktion

-   bei der 1. Zeile

-   Inventur auf "teilweise storniert" setzen

-   pro Zeile

-   löschen Inventurzeile

-   nach dem letzen Artikel im Bereich

-   Bereich löschen

-   nach dem letzen Bereich

-   Inventur auf "storniert" setzen

-   Druck Endemeldung des Batchlaufes

-   Inventurnummer

-   Bereichsanzahl

### Aufbau Stichtagstabellen

#### Auswahldialog

-   Firma (p)

-   Stichtagsdatum (p)

-   Gerätetabelle aufbauen (p)

-   Ja

-   Nein

-   Verarbeitungskennzeichen (p)

-   Standlauf

-   Wertlauf

-   Gesamtlauf

-   FIFO -- Gesamt

-   FIFO -- Pro Lager

Auswahl der Daten

-   Stichtagstabelle Lager

-   alle Artikel mit Lagerstand ungleich 0 zum Stichtagsdatum

-   Stichtagstabelle Geräte

-   alle lagernden Geräte zum Stichtagsdatum

Ablauf

-   Aufbau [artik_lag_st]-Datensatz

-   Menge = Lagerstand - [sum(kartei_lagbew.bew_mg) where kartei_dat >
    > Stichtagsdatum]

-   Belegung bei Stand- bzw. Gesamtlauf

-   Bewertungsfelder

-   Belegung bei Gesamt- und Wertlauf

-   werden auch bei "Standlauf" gesetzt, wenn Datensatz neu angelegt
    > wird

-   Abwertungsprozentsatz

-   wird bei Neuanlage Datensatz mit 0 initialisiert

-   Aufbau [artik_lag_g_st]-Datensatz bei Geräteartikeln

-   Menge = Buchungsmenge (+1/-1) des Karteisatzes mit der höchsten
    > internen Nummer für den gilt:

-   kartei_dat <= Stichtagsdatum

-   Endemeldung des Batchlaufes

Bewertungsfelder

-   FiFo-Bewertung

-   Ermittlung der Warenzugangsbuchungen des Artikels mit Buchungsdatum
    > <= Stichtagsdatum

-   kartei.kartei_dat <= Stichtagsdatum

-   kartei_kz in ("e", "p", "s")

-   kartei.lag_cd = {aktuelles Lager} wenn Verarbeitungskennzeichen = "
    > FIFO -- Pro Lager"

-   Eingangslieferscheinpositionen, denen eine Auftragsposition
    > zugeordnet ist, die bereits geliefert ist werden nicht
    > berücksichtigt.

-   Berechnung des Gesamtlagerwertes

-   Summieren der Zugangswerte nach Eingangslieferscheindatum absteigend

-   (Einstandswert lt. elfs_pos.veh_estpr) \* (Zugangsmenge aktuelles
    > Lager lt. kartei_lagbew.bew_mg, ggf. restlicher Lagerstand lt.
    > artik_lag_st.sum_lag_mg)

-   Berechnung des FiFo-Durchschnittspreises

-   Gesamtlagerwert / Lagerstand lt. Stichtagstabelle

-   alle Bewertungsfelder werden belegt

-   Wird bei FIFO Gesamt immer in Summe für einen Artikel gemacht

-   DuEst-Bewertung

-   lt. cst_duestrech zum Stichtag

-   Belegung nur beim Wertlauf

### Korrektur Abgrenzung

**Anwendung**

Müssen die Zähllisten aus organisatorischen Gründen bereits vor den
letzten Lagerbewegungen gedruckt werden, können mit diesem Programm die
abgestellten Sollstände aktualisiert werden. Die Zähllisten sollten ohne
Sollbestände gedruckt worden sein

#### Auswahldialog

-   Firma (p)

-   Inventurnummer (p)

-   Inventurabgrenzungsdatum (p)

-   Vorschlag Systemdatum

-   Belegung Istlagerstand (o)

-   unbestimmt

-   0

-   Solllagerstand

-   Wenn nicht angegeben, bleibt der Ist-Lagerstand unverändert

Auswahl der Daten

-   Inventur und Inventurzeilen lt. Auswahl

-   Fehlermeldung und Programmende wenn

-   Inventur nicht vorhanden

-   Zustand nicht "a" oder "ka"

-   Zustand eines zugehörigen Inventurbereiches nicht "a"

Ablauf

-   Update Tabelle [iv]

-   iv_dat = Inventurabgrenzungsdatum

-   iv_soll_dat = Systemdatum

-   iv_zustand_kz = "ka"

-   iv_kartei_snr = aktuell höchste Karteinummer

-   pro Datensatz in Tabelle [iv_zeile]

-   Update Tabelle [iv_zeile]

-   soll_lag_mg = Lagerstand lt. Tabelle [artik_lag_sub], bzw. 0 wenn
    > kein Lagersatz vorhanden

-   soll_zus_lag_mg = 0

-   ist_lag_mg = lt. Auswahlparameter

-   ablauf_dat = lt. Tabelle [artik_lag_sub]

-   duest_b = lt. Tabelle [artik_lag]

-   duest = lt. Tabelle [artik_lag]

-   mit der letzten Inventurzeile in einer Transaktion

-   Update Tabelle [iv]

-   iv_zustand_kz = "a"

## Lager

### Diverse Lagerbuchungen

**Allgemeines**

-   Diverse Lagerbuchungen dürfen nicht geändert bzw. gelöscht werden.
    Alle Teilbereiche des "Detail"-Registers werden gemeinsam
    gespeichert.

#### Auswahldialog

-   Firma

-   Belegnummer

-   Belegdatum

-   Artikelnummer (f)

-   Buchungsart (w)

-   Infotext

-   Sachbearbeiterkennzeichen

#### Register "Liste"

-   Firma

-   Buchungsart

-   Belegnummer

-   Belegdatum

-   Artikelnummer

-   Artikelmatchcode

-   Sachbearbeiterkennzeichen

-   Infotext

#### Register "Detail"

**Teilbereich "Artikel"  
**

-   Firma

-   Buchungsart (fd)

-   Berechtigungsprüfung

-   Belegnummer (a)

-   wird bei der Neuanlage beim Speichern vergeben

-   Belegdatum (a)

-   wird bei der Neuanlage beim Speichern vergeben

-   Artikelnummer (f)

-   Artikel muss aktiv sein

-   Artikel muss lagerführend sein

-   bei Buchungsart "Chargenkorrektur" muss die Lagerführung auf
    > Chargenebene sein

-   Artikelmatchcode (a)

-   Artikelinfotext (a)

-   Buchungstext

-   Sachbearbeiterkennzeichen (a)

    **Teilbereich "Lagerdaten"**

Bearbeitungsliste mit der Lageraufteilung der diversen Lagerbuchung

-   Lagercode (fd)

-   Listbox Lagerbestände (d)

-   aktiv, wenn Lagerstand auf Lagerortebene geführt wird

-   definiert Lagerort und/oder Chargen- bzw. Gerätenummer

-   folgende Felder im Auswahlfenster:

-   Lagerort

-   Chargen- bzw. Gerätenummer

-   verfügbarer Lagerbestand

-   Ablaufdatum

-   Einlagerungsdatum

-   Listbox Lagerorte (d)

-   aktiv, wenn Lagerstand auf Lagerortebene geführt wird

-   definiert Lagerort

-   folgende Felder im Auswahlfenster:

-   Lagerort

-   Lagerort

-   aktiv, wenn Lagerstand auf Lagerortebene geführt wird und der
    > Lagerort editierbar ist

-   Chargen- bzw. Gerätenummer (d)

-   aktiv, wenn Lagerführung auf Geräte- bzw. Chargenebene und Lager
    > Chargen-/Geräteverwaltung [lag. cg_verw_jn = "j"] hat

-   folgende Felder im Auswahlfenster

-   Chargen- bzw. Gerätenummer

-   verfügbarer Lagerbestand

-   Ablaufdatum

-   Einlagerungsdatum

-   Menge in Lagereinheit

-   bei Geräteartikeln nur 1 bzw. -1 erlaubt

-   bei Buchungsart "Chargenkorrektur" automatisch frei verfügbarer
    > Lagerbestand (negativ)

-   Ablaufdatum

-   aktiv, wenn Charge mit Ablaufdatum geführt wird, Buchungsart
    > "Zugang" ist und Lager Chargen-/Geräteverwaltung [lag.
    > cg_verw_jn = "j"] hat

-   User (a)

**Prüfungen beim Speichern:**

-   bei negativer Menge:

-   der ArtikLagSub-Datensatz muss bereits angelegt sein

-   der verfügbare Lagerstand darf nicht kleiner 0 werden

-   bei Geräten muss das Zustandskennzeichen "l" sein

-   bei positiver Menge:

-   bei Geräten darf kein ArtikLagSub-Datensatz mit Lagerstand ungleich
    > 0 vorhanden sein

-   Ist bei Geräten der Gerätestamm-Datensatz vorhanden, sind bei
    > Lagerzugang die Zustandskennzeichen "r", "a" und "k" sowie
    > bei Lagerumbuchung "l" zulässig

-   Prüfung der Buchungsmenge auf "Abgang" bzw. "Zugang" abhängig
    von der Buchungsart

-   Der Protokolldruck erfolgt hier automatisch, wenn lt. Buchungsart
    und lt. ib_divlgb_protokoll vorgesehen.

**Anmerkung zu Buchungsart "Chargenkorrektur":**

-   Zeilen anlegen bzw. löschen durch User nicht möglich

-   2 Zeilen werden automatisch nach Eingabe der Buchungsart angelegt

-   die Sortierung erfolgt nach Menge

-   in der 2. Zeile ist nur die Chargennummer einzugeben, alle anderen
    Werte (auch Ablaufdatum und Einlagerungsdatum !) werden von der
    1.Zeile kopiert

-   die Buchungsmenge der 2. Zeile entspricht der Menge der 1. Zeile \*
    -1

### Abfrage Lagerbewegungen

**Allgemeines**

-   Fenster dient zur Abfrage der Lagerbewegungen, es können keine
    Änderungen durchgeführt werden

#### Auswahldialog

-   Firma

-   Artikelnummer (f)

-   Buchungsdatum

-   Lagernummer

-   Lagerort

-   Chargen- bzw. Gerätenummer

-   Buchungssymbol

-   Buchungsart (w)

#### Register "Liste"

-   Firma

-   Buchungsdatum

-   Buchungssymbol

-   Lagernummer

-   Lagerort

-   Chargen- bzw. Gerätenummer

-   Buchungsmenge

-   Artikelnummer

-   Artikelmatchcode

-   Buchungsdatum und --zeit

-   Sachbearbeitercode

#### Schaltflächen für Verzweigungen

-   Buchungszeile

-   öffnet abhängig von Karteikennzeichen eines der folgenden Fenster

-   Ausgangslieferscheinposition

-   Eingangslieferscheinposition

-   diverse Lagerbuchung

-   Inventurzählmengenerfassung

-   Ausgangslieferschein (bei Produktion und Gerätausscheidung über
    > Reparaturabschluss)

-   Kassenbonposition

-   DUEST Buchung

### Abfrage DUEST-Entwicklung

Allgemeines

-   Fenster dient zur Abfrage der DUEST-Bewegungen, es können keine
    Änderungen durchgeführt werden

Auswahldialog

-   Firma

-   Artikelnummer (f)

-   Datum

-   DUEST-Gruppe

-   Buchungsart (w)

#### Register "Liste"

-   Firma

-   Datum

-   DUEST-Gruppe

-   Artikelnummer

-   Artikelmatchcode

-   Buchungsart (kartei_kz)

-   Lagerstand alt

-   Mengeneiheit

-   DUEST Alt

-   Buchungsmenge

-   Buchungswert

-   Einstandspreis (=Wert/Menge)

-   DUEST Neu

-   Lagerstand Neu

Schaltflächen für Verzweigungen

-   Buchungszeile

-   öffnet abhängig von Karteikennzeichen eines der folgenden Fenster

-   Ausgangslieferscheinposition

-   Eingangslieferscheinposition

-   diverse Lagerbuchung

-   Inventurzählmengenerfassung

-   Ausgangslieferschein (bei Produktion und Gerätausscheidung über
    > Reparaturabschluss)

-   Kassenbonposition

### **MDE-Artikelinfo**

-   **Lager (d)**

-   **Kann durch User fixiert werden**

-   **Scannen Artikel**

-   EAN

-   Artikel-Code

-   EAN-128

Anzeige

-   Artikelcode

-   Artikelmatchcode

-   Lagerstand Lager

-   Lagerstand Zentrale

-   offene bestellte Menge

-   offene Auftragsmenge

    Liste Lagerstände pro Lagerort

-   Lagerort

-   Lagerstand

-   verfügbarer Bestand

Button

-   Etikettendruck

-   Es kann über einen Applikationsparameter gesteuert werden, ob der
    > MDE-Etikettendruck vorhanden ist.

Etikettendruck

-   Artikelcode (a)

-   Artikelmatchcode (a)

-   Lagerstand Lager (a)

-   Einheitencode (d)

-   Vorschlag ist die Lagereinheit

-   Es können alle Liefereinheiten ausgewählt werden

-   Anzahl

Buttons:

-   Drucken

-   Speichert die Zeilen mit erfassten Mengen in mdeeti und Spoolt den
    > MDE-Etikettendruck ein (w_vab_mdeeti).

-   Zurück

### MDE-Umlagerung (TC.next)

-   Von Lager

-   Einschränkung nur Eigenlager mit Lagerortverwaltung der Filiale des
    > Users

-   Auf Lager

-   Vorschlag = Von Lager

-   Muss selbe Filiale wie Von Lager haben

-   Von Lagerort

-   Auf Lagerort

-   Artikel-Scannfeld

-   Auswahl über am Von-Lagerort lagernde Artikel möglich

-   EAN, EAN128 oder Artikelcode

-   Durch das Scannen des EAN128 kann auch die Chargennummer gesetzt
    > werden

-   Der Artikel muss am Von-Lagerort einen positiven verfügbaren
    > Lagerstand haben wenn lt. Lager kein negativer Lagerstand erlaubt
    > ist.

-   Durch Scannen des nächsten Artikels wird die Position gespeichert

-   Wird der gescannte Wert nicht als Artkel aber als Auf-Lagerort
    > gefunden, so wird der Auf-Lagerort gesetzt.

-   Artikelcode (a)

-   Artikelmatchcode (a)

-   Chargen/Grätenummer

-   Eingabe nur bei Chargen oder Geräetartikel

-   Lagerstand des von Lagerorts (a)

-   Frei Verfügbar (a)

-   ist abzüglich offener MDE-Umlagerungspositionen

-   Mengeneinheit (artik.eh_cd) (a)

-   Menge in Einheit

-   Vorschlag Frei Verfügbare Menge

-   Darf nicht größer als die Frei Verfügbare Menge sein, wenn lt. Lager
    > kein negativer Lagerstand erlaubt ist

-   Ist bei einem Geräteartikel fix 1

-   Einheit (d)

-   Vorschlag lt. EAN bzw. Lagereinheit, wenn nicht über EAN erfasst
    > wurde.

-   Es sind die Lager-Einheit, die Verkaufs- und die Einkaufs-Einheiten
    > erlaubt.

Buttons

-   Speichern

-   gebuchte Positionen

-   Artikelinfo

-   Verwerfen

-   Ende

gebuchte Positionen

Anzeige einer Liste der Umlagerungspositionen des aktuellen Users vom
aktuellen Tag

-   Von Lagerort

-   Auf Lagerort

-   Artikelcode

-   Artikelmatchcode

-   Menge in Lagereinheit

### MDE Umlagerung Verbuchen

Ablauf

Pro offener MDE Umlagerungsposition

-   Update mdeumlag job_nr, erl_datz

-   Es wird eine neue diverse Lagerbuchung erstellt

-   Firma lt. mdeumlag

-   Lagerbuchungsart lt. Parameter mdeumlag_divlgbart_cd

-   User lt. mdeumlag, wenn dieser User als TC-User anelegt ist.

-   Artikel lt. mdeumlag

-   Infotext blank

-   lt. Von/Auf Lagerort eine Zeile

-   Lager lt. mdeumlag

-   Lagerort von oder auf Lagerort lt. mdeumlag

-   Charge/Gerät lt. mdeumlag

-   Menge lt. Mdeumlag

-   Beim von Lagerort negativ

-   Beim auf Lagerort psoitiv

### MDE (TC.Next) Warenzugang

Einstiegsmaske

-   Auswahl Lager

-   Erlaubt sind die Eigenlager der Filiale des aktuellen Users

Gibt es offene MDE Warenzugänge in dem Lager kommen wir in die
Auswahlliste offene MDE Warenzugänge:

Auswahl offene MDE Warenzugange

-   Lieferantenmatchcode

-   Startzeitpunkt

Buttons

-   Auwählen

-   Wir springen in die Positionen der markierten Zeile

-   Neu

-   Zurück

MDE Warenzugang Kopf / Auswahl Eingangslieferscheine

Auswahlliste der offenen Eingangslieferscheine im Zustand Aviso mit MDE
Freigabe

-   Aus elfs: offene Eingangslieferscheine des ausgewählten Lagers,
    mde_zustand_kz 1 oder 3, elfs_zustand_kz = "a"

-   Belegnummer

-   Belegdatum

-   Lieferantenmatchcode

-   Status

-   Auswahl (c)

-   Bei Mehrfachauswahl können nur Eingangslieferscheine mit derselben
    > Lieferantennummer verwendet werden. Wird ein anderer Lieferant
    > ausgewählt erfolgt ein TE: "Der Lieferant weicht von den bereits
    > ausgewählten ab! Ersetzen? Ja/Nein".

Buttons:

-   Weiter

-   In den ausgewählten Eingangslieferscheinen wird der MDE Status auf
    > begonnen gesetzt.

-   Zurück

-   Zürck zur Einstiegsmaske

Positionen

-   Lagerort

-   Nur wenn Lager eine Lagerortverwaltung hat

-   Wird immer von der letzten Position vorgeschlagen

-   Artikelcode

-   Ist der Artikel im Einangslieferschein nicht vorhanden erfolgt ein
    > TE "Artikel nicht im Aviso! Trotzdem buchen? Ja/Nein"

-   Artikelmatchcode (a)

-   Lieferantenartikelnummer (a)

-   Scannfeld

-   Lagerort

-   EAN / Artikelnummer (EAN oder EAN128)

-   Wenn mit der Menge des EAN eine Einheit Liefermengeneinheit gefunden
    > werden kann, so wird diese Vorgeschlagen

-   Chargen/Gerätenummer

-   Nur bei Chargen/Geräteartikel eingebbar

-   Einheitscode (d)

-   Fix die Lagereinheit bei einem Geräteartikel

-   Zugangsmenge in Einheit

-   Fix 1 bei einem Geräteartikel

-   Summe Zugangsmenge des Artikels / Lagerorts / Charge in Lagereinheit

-   Durch die Änderung der Summe, wird die Zugangsmenge berechnet

-   Wenn die Menge in Lagereinheit auf die aktuelle Einheit ohne
    > Nachkomma umgerechnet werden kann, so wird diese verwendet,
    > ansonsten muss dadurch auf Lagereinheit umgeschaltet werden.

-   Die Summe darf damit nicht negativ werden.

-   Darf bei einem Geräteartikel nur 0 oder 1 sein.

-   Lagereinheitscode (a)

-   offene Menge aus Eingangslieferschein in Lagereinheit (a)

-   Summe der gelieferten Menge aus allen Eingangslieferscheipositionen
    > dieses Artikels, Abzüglich aller gescannten Mengen dieses Artikels

Buttons:

-   Speichern

-   Liste

-   offen

-   Liste offene Eingangslieferscheinpositionen

-   Abbruch

-   Verwirft die aktuelle Positionserfassung

-   Ende

-   Wenn es keine Differenzen gibt, wird das Verbuchen eingespoolt.

-   Gibt es Differenzen -- Weiter mit Liste offene Positionen.

Liste erfasste Positionen

Es wird eine Summe der Erfassten Mengen pro Lagerort und Artikel
angezeigt.

-   Lagerort

-   Artikelcode

-   Artikelmatchcode

-   Charge

-   Menge in EH

-   Mengeneinheit der Buchung

-   Menge in Lagereinheit

-   Lagereinheit

-   Lieferantenartikelnummer

Es kann eine Position zur Änderung ausgewählt werden (Vorschlag Lagerort
und Artikel).

Liste offene Positionen

Eine Summe pro Artikel, der Artikeln aus den
Eingangslieferscheinpositionen, deren gelieferte Menge noch nicht durch
die erfassten MDE-Warenzugangspositionen gedeckt ist.

-   Artikelcode

-   Artikelmatchcode

-   LFS Menge (lt. elfs_pos)

-   erf. Menge (lt. mdewzpos)

-   Mengeneinheitscode

-   Lieferantenartikelnummer

Buttons:

-   Erfassen

-   Unterbrechen

-   Erfassung wird später fortgesetzt oder es arbeiten mehrere
    > Mitarbeiter auf einen Warenzugang und die ersten sind mit ihrem
    > Teil fertig.

-   Ende mit Fehler

-   Einspoolen Verbuchen Warenzugang mit Fehler

-   w_name = "w_vab_mdewazu"

-   parameter = "elfsmde_upid=xx"

### MDE Warenzugang Verbuchen

Auswahlkriterien

-   ElfsMDE UPID

Auswahl der Daten

-   offene Datensäteze aus elfsmde_pos (erl_job_snr = 0)

Ablauf

Pro elfsmde_pos

-   Retrieven von Eingangslieferscheinpositionen, die noch nicht auf
    Lager gebucht (AVISO) sind mit dem Artikel lt. elfsmde_pos in den
    dem elfmde zugeodneten Eingangslieferscheinen.

-   Wenn es keinen gibt, dann wird eine neuen Position im ersten
    > zugeordneten Eingangslieferschein mit dem Artikel und Menge 0
    > angelegt

-   Wenn es genau eine Position gibt, dann wird in bie dieser in den
    > AVISO Lagerbuchungszeilen bei der Zeile mit dem
    > Lagerort/Charge-Gerätecode die Menge erhöht bzw. eine
    > entsprechende Zeile angelegt.

-   Wenn es mehrere Positinen mit der Artikelnummer gibt, so wird die
    > gebuchte Menge auf diese aufgeteilt, bis die Mengen der Positionen
    > durch die AVISO Mengen gedeckt sind. Wenn dabei noch zu buchenden
    > Mengen übrig bleiben, so werden diese auf die letzte Position
    > gebucht.

-   Wenn die bebuchte Positon noch keine MDE-Zuordnung hat
    > (elfs_pos.mde_elp_jn = "n") werden bereits vorhandene
    > elfs_pos_aviso Daten gelöscht und die mde_elp_jn (c) auf "j"
    > gestellt.

    Pro elfsmde

-   Es wird geprüft ob in allen Eingangslieferscheinpositionen alle
    Positionsmengen durch die AVISO Mengen gedeckt sind und es mehr
    lagerführenden keine Positionen mit elfs_pos_jn = "n" gibt.

-   Wenn das der Fall ist, wird bei den Eingangslieferscheinen der
    > MDE-Zustand auf MDE Warenzugang abgeschlossen upgedatet und das
    > AVISO Zubuchen durchgeführt.  
    > In der elfmde wird der Zustand auf Vollständig erledigt upgedatet.

-   Wenn es Differenzen gibt, so wird der MDE Zustand der
    > Eingangslieferscheine auf MDE Warenzugang Fehlerhaft upgedatet  
    > In der elfsmde wird der Zustand auf Fehlerhaft upgedatet.

### MDE Kommissionierung

-   Wenn beim Programmstart ein Kommissioniervorgang im Zustand in
    Kommissionierung für den User vorhanden ist, so wird sofort in die
    Positionserfassung dieses Auftrags gesprungen.

Einstiegsmaske

Auswahlliste der offenen Kommissionsvorgänge

-   Aus kommvorg_bereich mit Filiale des Users, Status ist freigegeben
    oder Pausiert

-   Kommissionsvorgangsnummer

-   Bereichsnummer

-   frühester Liefertermin

-   Kommissionsvorgangsbezeichnung

-   Anzahl Positionen

-   Kommissionierer

-   Ist nur bei Pausiert belegt

-   Priorität (Ampel)

Sortierung: Priorität, Liefertermin, Kommissioniervorgangsnummer

Buttons:

-   [Auswahl]{.mark}

-   Durch Auswahl einer Position wird in auf_komm, der Status wird auf 2
    > upgedatet und die mde_person und Beginnzeit eingetragen.

-   [Neu Laden]{.mark}  
    Aktualisiert die Auswahlliste

-   Ende  
    Beendet das Programm

Positionsbearbeitung

-   Es wird die erste offene Position des Kommissionsvorganges in der
    Reihenfolge Sortiernummer (lt. Gewichtsklassenfaktor und Lagerort)
    und Lagerortcode vorgeschlagen.  
    Es werden dabei nur lagerführende Positionen verwendet.

-   Kommissionsvorgangsbezeichung (a)

-   Lagerort (a)

-   Artikelcode (a)

-   Artikelmatchcode (a)

-   offene SollKommissionierMenge in Lagereinheit (a)

-   Lagereinheit (a)

-   Menge in Lagereinheit

-   Darf nicht > Soll Kommissionier Menge sein

-   Mit Eingabe 0 wird die Position ohne Scannen abschlossen (= Ware
    > nicht im Lager gefunden)

-   Menge aufgelöst in Übereinheiten (a)

-   zb. 10 Stk (= 1 Ktn + 4 Stk)

-   Scannfeld

-   Es muss ein EAN des aktuellen Artikels gescannt werden

-   Es können dabei auch EAN128 oder GS1 Datamatrix Codes mit Chargen
    > oder Gerätenummern verwendet werden.

-   Durch das Scannen wird die Position abgeschlossen, wurde keine Menge
    > eingegeben, so wird die Position mit der Soll Menge abgeschlossen

-   Chargen-/Seriennummer

-   wird ggf. durch den Scan belegt

-   muss bei Chargen-/Geräteartikel ausgefüllt sein

    Abschluss der Position

-   wurde die komplette Menge bestätigt ist die Positon damit erledigt

-   Wenn eine Restmenge bleibt (auch bei Mengeneingabe 0), so wird der
    nächste mögliche Lagerort für den Artikel ermittelt Dazu wird eine
    Prozedure aufgerufen Mit diesem Lagerort wird eine neue Position
    erstellt.  
    Bei einem Chargen oder Geräteartikel kann das auch derselbe Lagerort
    wieder sein.

-   Es wird sofort die nächste offene Position in der Reihenfolge der
    Lagerort-Sortiernummer angzeigt

-   Gibt es mehr keine offene Position, so erfolgt ein Hinweis "fertig
    kommissioniert".

-   Der Kommissionscheinstatus wird auf MDE Kommissionierungsverbuchung
    > läuft (auf_komm.komm_status_kz = "5") upgedatet.

-   Es wird das Verbuchen der MDE-Kommissioniertung für den
    > Kommissionsschein eingespoolt

-   Es wird wieder die Liste der offenen Kommissionsscheine angezeigt
    > (Einstiegsmaske)

    Buttons:

-   Speichern

-   Artikelinfo

-   offene Positionen

-   gebuchte Positionen

Liste der gebuchten Positionen

Liste der Positionen: (sortiert nach Sortiernummer, Lagerort)

-   Lagerort

-   Artikelcode

-   Artikelmatchcode

-   Soll Menge

-   kommissionierte Menge

-   Charge/Gerät

Buttons:

-   Zurück (Zurück zur Positionserfassung mit der vorher aktuellen
    Position)

-   Korrektur

Liste der offenen Positionen

Liste der Positionen: (sortiert nach Sortiernummer, Lagerort)

-   Lagerort

-   Artikelcode

-   Artikelmatchcode

-   Soll Menge

Buttons:

-   Zurück (Zurück zur Positionserfassung mit der aktuell ausgewählten
    Position lt. Liste).

-   Abbruch

-   Einspoolen des Verbuchen Jobs.

-   Pause

-   Kommissionsbereich wird auf Pausiert gesetzt

## Kassa 

-   Kassenprograme in TC

### Kassenstamm

Auswahlkriterien

-   Kassennummer

Liste

-   Kassennummer

-   Kassenmatchcode

-   Pause in Sek.

-   Archiv Tage

-   Firma

-   Lager

-   Tagesabschluss auf Kassa (c)

-   Lizenz (c)

-   RKSV-Status

Register Detail

-   Kassennummer

-   Kassenmatchcode

-   Firma (f)

-   Darf nur bei RKSV-Status (DB) = Nicht registriert geändert werden

-   Lager (f)

-   Lagermatchcode (a)

-   Kassengruppe (d)

-   SB-Eingabe (d)

-   Kassenart (d)

-   Lade Öffnen (d)

-   Münzlistendruck (d)

-   Zahlbest. Druck (d)

-   Sprache (d)

-   Kundenmatchcode (a)

-   Gutscheintext

-   Kreditkartenbeleg Kopftext (d)

-   Kreditkartenbeleg Endtext (d)

-   Gutschein Kopftext (d)

-   Gutschein Endtext (d)

-   Pause in Sekunden

-   Archiv Tage

-   Transaktion in der Pause offen lassen (c)

-   Tagesabschluss auf Kassa möglich (c)

-   Nur möglich, wenn die die Kassennummer gleich der Kassengruppe ist
    > und es einen entsprechenden Kassenbestand mit SB-Gruppe blank
    > gibt.

-   Kassa aktiv (c)

-   setzt evt. auch Kassenart

-   Lizenz (c)

-   RKSV Status (d)  
    Folgende Änderungen sind möglich (Von Wert ist der DB Wert)

-   Von -- auf n

-   Von -- auf r

-   Von n auf r

-   Von n auf -

-   Von r auf n

-   Von r auf a

-   Von a auf r

-   Von a auf n

-   Ein neuer Datensatz hat immer "n"

-   Eine Änderung löst beim Speichern die jeweilige FinanzOnline Meldung
    > aus (Zugansdaten lt. ka_fa)

-   Eine Registrierung ist nur möglich, wenn der AES Schlüssel (ka_fa)
    > ausgefüllt ist -- Mindestlänge sind 8 Zeichen.

-   Eine Änderung von "n" oder "-" auf "r" und eine Erfolgreiche
    > Registrierung löst auch einen kassa,U,rksv-init Eintrag in der
    > ka_datueb aus.

-   Zeitpunkt der Registrierung (a)

-   Wir durch die FinanzOnline Registrierung gesetzt

-   Zeitpunkt des Ausfalls/Ausserbetriebnahme

-   Bei Umsetzen des Status von r auf n oder a wird hier der aktuelle
    > Zeitpunkt vorgeschlagen und kann vor dem Speichern noch geändert
    > werden -- sonst ist keine Eingabe möglich.

-   Ausfall-Begründung (d)

-   Kann nur bei Änderung von r auf a Eingegeben werden, dann jedoch
    > zwingend (Ausnullen)

-   In allen anderen Fällen fix 0

-   Ausserbetriebnahme-Begründung (d) (a)

-   Wird bei einer Änderung von Status r auf n auf 7 (Außerbetriebnahme
    > aufgrund eines irreparablen Ausfalls)

-   Kann nur über einen Ausserbetriebnahmebeleg auf 6 (Planmäßge
    > Außerbetriebnahme) gesetzt werden.

-   In allen anderen Fällen fix 0

-   Kundennummer für RKSV Belege (f)

-   Muss ausgefüllt sein, wenn RKSV angemeldet ist

-   Kundenmatchcode (a)

-   RKSV-Gruppe (d)

-   Maschinenlesbarer Code (d)

Register TouchKassa

-   Default Kundennummer (f)

-   Service Pfad

-   Bilder Pfad

-   Kassenbelggruppennummer

-   BarButton Betrag 1 -- 4

-   MPD Felder

-   Sprache (d)

-   Terminal-ID

-   DeviceID

-   AutoMode

-   Druckerbreite

-   DruckerOpt

Register Belegtexte

Liste über

-   Belegart (d)

-   Sub-Belegart (d)

-   Kopftextbaustein (d)

-   Endtextbaustein (d)

Register Geräte

Liste über

-   Geräte-KZ (d)

-   Bezeichnung

-   Device

-   Init Kommando

-   Ende Kommando

-   Anschluss (d)

-   Baudrate (d)

-   Bytesize (d)

-   Parity KZ (d)

Register Nummernkreise

Liste aus Tabelle nummern über alle Einträge deren Nummernkreis oder
Spaltenname der Kassennummer entspricht.

-   Tabelle

-   Kassa (Spaltenname)

-   Nummernkreis

-   Vergabe/Eingabe (d)

-   Von-Nummer

-   Bis-Nummer

-   Nächste Nummer

-   Bei einer Änderung eines Eintrages mit Spaltenname = Kassennummer
    wird ein entsprechender Datensatz in ka_datueb abgestellt.

Register Rechner

Liste über

-   Hostname (d)

-   Hostname

-   Rechner-Matchcode (a)

Register Warrify

Geschützt über gf_initapplenv_parameter „hat_warrify_jn". Wenn nein,
dann Register Disabled

-   Warrify ist Aktiv

-   Belegdruck Verhalten

-   Name

-   Branchname

-   BranchId

-   Legalname

-   Emailadress

-   WebsiteUrl

-   Phonenumber

-   VatId

-   Streetadress

-   LocalizedCityName

-   Postalcode

-   LocalizedCountryName

-   IsoCountryCode

Extra Menüpunkte

-   Löschen Bewegungsdaten

-   Nur möglich, wenn es noch keine Verbuchten Belege der Kassa gibt und
    > wenn die Kassa nicht als RKSV aktiviert ist (nur im Testbestrieb
    > oder Status = nicht registriert)

-   Es werden alle Kassenbelege, Diversen Ein-/Ausgänge, Gutscheine und
    > Kassenabschlüsse der Kassa gelöscht.

-   Es erfolgt ein TE ob die Nummernkreise zurückgesetzt werden sollen.

### Kassen Ein- und Ausgang

-   Kein Löschen möglich

-   Ändern ist nur dann möglich, wenn der Kassenabschluss im TC gemacht
    > wird, und für den entsprechenden Kassenbestand noch kein Abschluss
    > erfolgt ist.

-   Neueingabe ist nur möglich, wenn der Kassenabschluss im TC gemacht
    > wird.

Wertbereicheingabe

-   Kassennummer

-   Belegnummer

-   Sachbearbeiter

-   Belegdatum

-   Uhrzeit

-   KEA-Art

-   Betrag

-   Zahlungsart

-   Betrag gegeben

Listenbereich

-   Firmennummer

-   Kassennummer

-   Kassenmatchcode

-   Belegnummer

-   Datum

-   Uhrzeit

-   Sachbearbeiter

-   Sachbearbeitername

-   Betrag

-   SubBelegart

-   Sub-Belegart-Matchcode

-   3xText

Detailbereich

-   Firma (a)

-   Kassa (d)

-   wenn ka_host Datensatz vorhanden, dann fix dieser, sonst Eingabe.

-   Belegnummer (a)

-   Vergabe lt. nummern, nr_kreis = Kassennummer

-   Betrag (a)

-   Summe der Zahlungsarten

-   Subbelegart (d)

-   Sachbearbeitercode (a)

-   Belegdatum

-   Wird ein Datum eingegeben, das <= dem letzten Abschlussdatum lt.
    > Kassenbestand ist, erfolgt ein Hinweis:  
    > ACHUNG: Kassenabschlüße ab dem tt.mm.yyyy müssen wiederholt
    > werden!

-   Uhrzeit (a)

-   Wird beim Speichern belegt

-   Fibu-Belegnummer (a)

-   Text

Zahlungsdaten

Liste über:

-   Zahlungsart (d)

-   Es sind nur aktive Zahlungsarten, mit kea_jn = \'j\' erlaubt

-   Betrag

-   Vorzeichen lt. Subbelegart.

Allgemeines

-   Beim Speichern erfolgt ein Update des offene-Beleg Datums am
    > Kassenstamm (darf nur kleiner werden)

Extra Menü:

-   Storno

-   Nur möglich wenn auch Neu möglich ist.

-   Datumsprüfung wie bei Neuerfassung

-   Es wird der Beleg kopiert, wobei die Vorzeichen der Beträge
    > vertauscht werden.

-   Das ist die Einzige Möglichkeit, bei einer negativen Sub-Belegart
    > einen Positiven Betrag zu erzeugen (uu).

### Münzliste 

-   Löschen ist nicht möglich

Auswahlkriterien

-   Münzlistennummer

-   Datum

-   Kassennummer

-   Sachbearbeitercode

Liste

-   Münzlistennummer

-   Datum

-   Zeit

-   Kassennummer

-   Kassenbezeichnung

-   Sachbearbeiter

-   Sachbearbeitername

-   Tagesabschluss auf Kassa

-   Sollbestand

-   Istbestand

-   Differenz

-   In Darstellung "achtung" wenn ungleich 0

-   In Darstellung "fehler" wenn Außerhalb der Bagetellgrenzen

-   Tagesumsatz

Detailbereich

-   Keine Änderung möglich

-   Münzlistennummer (a)

-   Vergabe lt. Tabelle nummer, nr_kreis = Kassennummer

-   Uhrzeit (a)

-   Wird beim Speichern belegt

-   Kassa (d)

-   wenn kassa_host Datensatz vorhanden, dann fix dieser, sonst Eingabe.

-   Sachbearbeiter (a)

-   Datum (a)

-   Ist bei Neuanlage das Datum des letzten offenen Beleges lt.
    > Kassenbestand

-   Wenn dieses ungleich das Tagesdatum ist denn erfolgt ein Hinweis
    > "ACHTUNG -- Tagesabschluss für tt.mm.yyyy wird durchgeführt"

-   Sollbestand (a)

-   Istbestand (a)

-   Differenz (a)

-   In Darstellung "achtung" wenn ungleich 0

-   In Darstellung "fehler" wenn Außerhalb der Bagetellgrenzen

-   Tagesumsatz (a)

Teilbereich Münzliste

-   Bei Neuanlage Vorschlag lt. mzl_vg

-   Eingabe nur in Neu Zweig möglich

-   Zahlungsartentext

-   Einheit

-   Anzahl

-   Betrag (+Summe)

Teilbereich Abschöpfung

-   Rechts neben Münzliste

-   Wie Teilbereich Münzliste

-   Nur verfügbar bei fixen Endbestand und Münzliste im Zustand
    > "Abschöpfung fehlt"

-   Speichern nur möglich, wenn die Summe der Beträge dem
    > Abschöpfungsbetrag entspricht

-   Bei negativen Abschöpfungsbetrag werden alle Eingabe automatisch
    > negativ abgestellt.

-   Beim Speichern wird über diesen Abschöpfungsbetrag ein Diverser
    > Kassenein/Ausgang erstellt

-   Über Fernsteuerung von Diversen Kassenein/Ausgang

-   Kassennummer, Sachbearbeiter und Datum lt. Münzliste

-   Sub-Belegart ist die erste gefunden mit Abschöpfung = "j"

-   Eine Zahlungszeile mit "Bar" und dem Abschöpfungsbetrag

-   Danach wird nochmals der Kassenabschluss durchgeführt und ggf.
    > gedruckt.

Vorschlag von Abschöpfungen:

-   Abschöpfungsbetrag = Soll-Endbestand -- Fixer Endbestand

-   Wenn negativ -- kein Vorschlag

-   Beginnend mit der Größten Stückelung (nur Bar) wird der
    > Abschöpfungsbetrag aufgeteilt

-   Es werden auch Zeilen mit Anzahl 0 aufgebaut, jedoch beim Speichern
    > gelöscht.

z.B.

Endbestand = 2377,34

Fixer Endbstand = 1000,00

Abschöpfungsbetrag = 1377,34

Münzliste: Abschöpfung

1 x 500 1 x 500

4 x 100 4 x 100

12 x 50 9 x 50

16 x 20 1 x 20

32 x 10

14 x 5 1 x 5

27 x 2 1 x 2

80 x 1

43 x 0,5

27 x 0,2 1 x 0,20

38 x 0,1 1 x 0,10

33 x 0,05

18 x 0,02 2 x 0,02

63 x 0,01

Register: Kassensummen

-   Wie auf Kassa

Sonstiges:

-   Beim Speichern einer neuen Münzliste

-   Update des offene-Beleg Datums am Kassenbestand (darf nur kleiner
    > werden -- die neue Münzliste gilt als offener Beleg -- der
    > Kassenabschluss ist noch nicht durchgeführt)

-   Wenn der automatische Münzlistedruck aktiviert ist wird der
    > Münzlistendruck gestartet

-   es wird der Kassenabschluss durchgeführt und die
    > Kassenabschlussdaten werden sofort angezeigt

-   Bei Druck Kassenabschluss Vorläufig oder Beide wird der
    > Kassenabschluss-Druck gestartet

-   Bei fixen Endbestand

-   Status wird auf "Abschöpfung fehlt" gesetzt

-   Wenn die Differenz Außerhalb der Bagatellgrenzen liegt erfolgt ein
    > Hinweis "ACHTUNG Kassendifferenz zu groß"

-   In diesem Fall muss entweder eine neue Münzliste erfasst werden
    > (Falsch gezählt)

-   oder es muss eine Korrekturbuchung (Kassenbeleg oder Ein-/Ausgang)
    > erfolgen und der Abschluss über den Extra Menüpunkt wiederholt
    > werden

-   Vorschlag der Abschöpfungen - siehe Teilbereich der Abschöpfungen

-   Bei variablen Endbestand

-   Status wird auf "Tagesabschluss vollständig" gesetzt

Kassenabschluß:

-   Aufbau der Daten in ka_tagab.... lt. Datenbankbeschreibung (wenn
    > bereits vorhanden vorher löschen)

-   Nur bei endgültigem Kassenabschluss

-   d.h. nicht bei fixen Endbestand vor Erstellung der Abschöpfung

-   ka_bst -- Datum letzter Kassenbschluss

-   ka_bst -- offen Belegdatum neu ermitteln (Kleinstes Belegdatum von
    > Belegen nach dem Kassenabschluss), evt. Null

-   ka_bst -- Anfangsbestand wird NUR bei variablen Kassenabschluss auf
    > den Soll-Endbestand gesetzt

-   Alle anderen Münzlisten in den gleichen Gruppen am selben Tag werden
    > auf storniert gesetzt

Extras:

-   Münzliste drucken

-   Kassenabschluss drucken

-   Kassenabschluss rechnen

-   Nur bei Zustand "e" oder "a"  
    > oder Variablen Kassenbestand und das Datum des letzten
    > Kassenabschlusses ist gleich dem Münzlistendatum

-   Storno

-   Nur möglich wenn Datum letzte Abschluss gleich Münzlistendatum

-   Zustand KZ wird auf Storno gesetzt

-   Update ka_bst --

-   Datum letzter Kassenabschluss wird auf max(Münzlistendatum) von
    > Tagesabschluss-Münzliste für die Gruppen gesetzt.

-   Datum offenen Beleg wird auf der Münzlistendatum gesetzt

-   Anfangsbestand muss auf den Anfangsbestand lt. Tagesabschluss
    > zurückgesetzt werden

-   Tagesabschluss Einträge löschen

### Druck Münzliste

Auswahlkriterien:

-   Münzlistennummer

-   Kassennummer (w)

-   Datum

-   Firma (w)

Im Kopf:

-   Münzlistennummer

-   Druck Datum Uhrzeit

-   Seitennummer

-   Kassennummer

-   Kassenbezeichnung

-   Kassen-Sachbearbeitercode

-   Münzlistendatum

-   Grundwährungstext

Pro Münzlistenposition:

-   Zahlungsartencode

-   Zahlungsartentext

-   Anzahl

-   Einheiten

-   Grundwährungstext

-   Positionsbetrag (Anzahl \* Einheiten)

-   Summe Bargeld in Grundwährung

Version TC

1 2 3 4 5 6 7 8 9

1234567890123456789012345678901234567890123456789012345678901234567890123456789012345678901234

----------------------------------------------------------------------------------------------

Münzliste Nr 1234567 Datum TT.MM.JJJJ HH:MM Seite 123 von 123

Kassa 12 XXXXXXXXXXXXXXXXXXXX SB XXXXX vom tt.mm.jjjj

Bargeld Anzahl Einheiten Wert XXXX

XXX XXXXXXXXXXXXXXXXXXXXXXXXXXXXXX 1234 1.234.567,12 XXXX 1.234.567,12

XXX XXXXXXXXXXXXXXXXXXXXXXXXXXXXXX 1234 1.234.567,12 XXXX 1.234.567,12

XXX XXXXXXXXXXXXXXXXXXXXXXXXXXXXXX 1234 1.234.567,12 XXXX 1.234.567,12

-----------------------------------------------------------------------

T o t a l 1.234.567,12

=======================================================================

### Druck Tagesabschluss

Auswahlkriterien:

-   Datum

-   Firmennummer

-   Kassenbestandsgruppe

-   Sachbearbeiterbestandsgruppe

-   Summenblatt drucken (p)

Folgende Daten werden angedruckt:

-   Belegdatum

-   Datum des Ausdrucks

-   Uhrzeit des Ausdrucks

-   Seitennummer

-   Sachbearbeitercode

-   Sachbearbeitername

-   Tagesumsatz (=Summe der Barverkäufe und Anzahlungen)

-   Anzahlungen erhalten

-   Anzahlungen eingelöst

-   Anfangsbestand (lt. Tabelle sb)

-   Pro Beleggruppe

-   Beleggruppenbezeichnung

-   Anzahl der Belege

-   Summe Betrag

-   Pro Zahlungsart

-   Eingang

-   Ausgang

-   Automatische Abschöpfung (Summe der Zahlungsarten-Soll ohne Bar)
    > werden lt. Sub-Belegart Abschöpfung mitgerechnet.

-   Rundungsdifferenzen (Summe über Restwert)

-   Endbestand - Summe der oben angeführten Beträge = SOLL Kassenstand

-   Wert der Münzliste = Ist Bestand

-   Differenz (= Ist -- Soll)

    Listbild siehe Kassenabschluß auf Kassa -- Version Slip

### Druck Abschöpfungssummenblatt

Auswahlkriterien:

-   Firma (w)

-   Datum

-   Kassenbestandsgruppe

Im Kopf:

-   Druck Datum Uhrzeit

-   Kassenbestandsgruppencode

-   Kassenbestandsgruppenmatchcode

-   Münzlistendatum

-   Grundwährungstext

-   Summe pro Datum/Kassenbestandsgruppe/Zahlungsart und Einheit, auf
    > ka_mzl_absch

-   Sortierung nach Einheiten absteigend

-   Zahlungsartencode

-   Zahlungsartentext

-   Summe Anzahl

-   Einheiten

-   Grundwährungstext

-   Positionsbetrag (Anzahl \* Einheiten)

-   Summe Bargeld in Grundwährung

Version TC

1 2 3 4 5 6 7 8 9

1234567890123456789012345678901234567890123456789012345678901234567890123456789012345678901234

----------------------------------------------------------------------------------------------

Abschöpfungssummenblatt Datum TT.MM.JJJJ HH:MM

Kassengruppe xxxxx xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx vom
tt.mm.jjjj

Bargeld Anzahl Einheiten Wert XXXX

XXX XXXXXXXXXXXXXXXXXXXXXXXXXXXXXX 1234 1.234.567,12 XXXX 1.234.567,12

XXX XXXXXXXXXXXXXXXXXXXXXXXXXXXXXX 1234 1.234.567,12 XXXX 1.234.567,12

XXX XXXXXXXXXXXXXXXXXXXXXXXXXXXXXX 1234 1.234.567,12 XXXX 1.234.567,12

-----------------------------------------------------------------------

T o t a l 1.234.567,12

=======================================================================

### Zahlungsbuchung -- cst_ka_zahlung

Parameter:

-   Firmennummer

-   Rechnungsnummer

-   Sachbearbeitercode

-   Hostname

-   Verarbeitungsendtext (by Reference)

Returns Boolean

Ablauf:

Insert ka_bel

  ----------------------------------------------------------------------------
  bel_nr           Rechnunungsnummer
  ---------------- -----------------------------------------------------------
  kassa_nr         aus pfu_host lt. Parameter Hostname

  fa_nr            lt. Parameter

  bel_dat          Rechnungsdatum

  bel_zeit         aktuelle Zeit

  bel_art          "r"

  bel_art_sub_cd   \'\'

  kunde_cd         lt. erster auf der Rechnung

  adr_snr          lt. kunde

  sb_cd            lt. Parameter

  gen_sb_cd        " "

  vkrab            0

  betrag           Bruttowert der Rechnung in Grundwährung

  zahl_betr        Bruttowert abzüglich Skonto Wert in Grundwährung

  rest_betr        0

  storno_bel_nr    0

  auf_nr           0

  tax_free_jn      \'n\'

  tax_free_betr    0

  erl_bel_nr       = bel_nr
  ----------------------------------------------------------------------------

Insert ka_bel_vrech

  ---------------------------------------------------------------------------
  op_nr         vrech.bez_vrech_nr
  ------------- -------------------------------------------------------------
  vrech_nr      = bel_nr

  zahl_betr     wie oben

  skonto_betr   Skontobetrag in Grundwährung

  skonto_prz    Skonto Prozentsatz
  ---------------------------------------------------------------------------

Insert ka_kartei

  ---------------------------------------------------------------------------
  rund_diff     0
  ------------- -------------------------------------------------------------
  retourgeld    0

  text_...    " "

  fibu_bel_nr   0
  ---------------------------------------------------------------------------

Insert ka_kartei_zp

  ---------------------------------------------------------------------------
                Zahlungsbetrag            Wenn Skonto <> 0 für Skonto
  ------------- ------------------------- -----------------------------------
  pos_nr        1                         2

  zahlung_cd    zahlart.ka_zahlung_cd     ka_fa.skonto_zahlung_cd

  betrag        Rechnungsbetrag exkl.     Skontobetrag
                Skonto                    

  waehrung_cd   lt. vrech                 lt. vrech

  betrag_gw     betrag in Grundwährung    Betrag in Grundwährung

  gus_nr        0                         0

  kk\*          " "                     " "
  ---------------------------------------------------------------------------

### KassenLadenöffnungen

Auswahlkriterien:

-   Kassennummer (w)

-   Datum/Zeit

-   Kassen-Sachbearbeiter

-   Belegart (w)

-   Belegnummer

Liste

-   Kassennummer

-   Kassenmatchcode

-   Zeitpunkt

-   Kassenusercode

-   Kassenusermatchcode

-   Belegnummer

-   Öffenen öffnet abhängig von der Belegart den Kassenbeleg, den
    > diversen Ein/Ausgang oder die Münzliste

-   Belegart

-   Es gibt einen Button auf den Kassen-Belegkopf der hierher zeigt.

### Export Datenerfassungsprotokoll Version Kassenrichtlinien 2012

Auswahlkriterien:

-   Filenamen (p)

-   Firmennummer (w)

-   Kassennummer (w)

-   Kassensachbearbeiter (w)

-   Buchungszeitpunkt

Es wird ein CSV File (Trennzeichen = ";") mit folgenden Spalten
erstellt

-   Laufende Nummer (innerhalb des Protokolls)

-   Firmennummer

-   Kassennummer

-   Sachbearbeitercode

-   Datenexport-KZ

-   p = Belegposition

-   r = Rechnungsausgleich

-   z = Zahlungsbuchung

-   m = Münzlistenbuchung

-   l = Ladenöffnung

-   s = Stornierte Position

-   Buchungszeitpunkt (Datum + Uhrzeit)

-   Belegart

-   Belegnummer

-   Positionsnummer

-   Artikel-Code

-   Positionstext

-   Menge

-   Positionswert Brutto (inkl. MwSt)

-   MwSt Prozentsatz

-   MwSt Wert

-   Zahlungscode

-   ist nur bei Zahlungsbuchung belegt

-   OP-Nummer

-   ist nur bei Rechnungsausgleich belegt

-   Bei Ladenöffnung die Bezugsbelegnummer

-   HASH-Wert

### SQL-Kommando 

Auswahlkriterien

-   SQL-KommandoSnr

Liste:

-   SQL-KommadnoSnr

-   Kommando

    **Detail**

    Teilbereich Kommandos

-   SQL-KommadnoSnr

-   Kommando

-   Alle Kassa (c)

-   Nicht gespeicherter Feld

-   Wenn ausgewählt wird in allen Zeilen im Teilbereich Kassa das Feld
    > "Auswahl" gesetzt

    Teilbereich Kassa

-   Liste aller aktiven Kassen [kassa.ka_aktiv_jn = "j"]

-   Auswahl

-   KassaNr (a)

-   KassaBezeichnung (a)

    Anmerkung Speichern

-   für jede ausgewählt Kassa wird ein Insert in die Datenübernahme
    [ka_datueb] manuell ausgelöst

-   kassa_nr = ?

-   tabname = "ka_sqlcmd"

-   akt_kz = "I"

-   cd1 = ka_sqlcmd_snr

### Auswahlgruppe

Auswahlkriterien

-   Firma

-   Auswahlgruppencode

-   Artikelcode (f)

-   TabDazu

Liste:

-   Firma

-   Auswahlgruppencode

-   Auswahlgruppenmatchcode

-   Sortiernummer

Detail

Teilbereich Auswahlgruppe

-   Firma

-   Auswahlgruppencode

-   Auswahlgruppenmatchcode

-   Wird bei Änderung automatisch als Deutscher Text vorgeschlagen, wenn
    > vorher gleich oder noch nicht vorhanden

-   Sortiernummer

Teilbereich Sprache

-   Sprache (d)

-   Label Text

Teilbereich Artikel

-   Artikelcode (f cs)

-   Artikelmatchcode (a)

-   Sortieren der Zeilen über DragDrop möglich. Die Sortiernummer wird
    beim Speichern nach dieser Reihenfolge vergeben.

### RKSV Signaturerstellungseinheit

Auswahlkriterien

-   Seriennummer

-   Firma

Liste:

-   Seriennummer

-   Firma

-   Status

-   Registrierungs Zeitpunkt

-   Ausfall/Abgemeldet Zeitpunkt

Detail

Teilbereich Auswahlgruppe

-   Seriennummer

-   Status (d)  
    Folgende Änderungen sind möglich (Von Wert ist der DB Wert)

-   Von n auf r

-   Von r auf n

-   Von r auf a

-   Von a auf r

-   Ein neuer Datensatz hat immer "n"

-   Eine Änderung löst beim Speichern die jeweilige FinanzOnline Meldung
    > aus (Zugansdaten lt. ka_fa)

-   Firma (\*)

-   VDA (d) (\*)

-   Zeitpunkt der Registrierung (a)

-   Wir durch die FinanzOnline Registrierung gesetzt

-   Zeitpunkt des Ausfalls/Ausserbetriebnahme

-   Bei Umsetzen des Status von r auf n oder a wird hier der aktuelle
    > Zeitpunkt vorgeschlagen und kann vor dem Speichern noch geändert
    > werden -- sonst ist keine Eingabe möglich.

-   Ausfall-Begründung (d)

-   Kann nur bei Änderung von r auf a Eingegeben werden, dann jedoch
    > zwingend (Ausnullen)

-   In allen anderen Fällen fix 0

-   Ausserbetiebnahme-Begründung (d)

-   Kann nur bei Änderung von Status r auf n eingegeben werden, dann
    > jedoch zwingend (Ausnullen)

-   In allen anderen Fällen fix 0

-   Infotext

(\*) -- Änderung nur möglich wenn der Zustand (lt. DB) "n" war

### Export RKSV-Datenerfassungsprotokoll

Auswahlkriterien

-   Ausgabe Pfad (p)

-   Variante (p)

-   Normal

-   Sicherung

-   Kassennummer

-   ID SubNummer

-   **Belegdatum**

-   **Belegnummer**

Auswahl der Daten

-   Aus ka_rksvdep lt. Auswahlkriterien

-   Bei Variante Sicherung immer alle Kassen und Subnummern, zu dem es
    Datensätze mit export_job_snr = 0 gibt

Ablauf

Pro Kassa und Subnummer wird ein File erstellt. Filename =
ka<Kassa_nr>[s<RKSV_id_sub_nr>]_JobNr.dep

-   s+IDSubNr werden nur verwendet, wenn die SubNummer <> 0 ist.

-   Bei Variante Sicherung

-   select kassa_nr, rksv_id_sub_nr, max(dep_snr)  
    > from ka_rksvdep, ka_bel  
    > where join  
    > and export_job_snr = 0  
    > and ka_bel.bel_art = "S"

-   eine Transaktion pro Kassa und Subnummer

-   Update export_job_snr aller Datensätze mit dieser Kassen und
    > Subnummer bis zum letzten Monats- od. Jahresende Beleg  
    > lt. RKSV §7 hat die Sicherung als letzten Beleg immer einen
    > Monats/Jahresendebeleg zu enthalten.

-   Erstellt wird das File im Lokalen Temp Verzeichnis

-   Aufbau siehe
    [..\\kassa\\org\\A-Trust\\2016-09-05-Detailfragen-RKSV-V1.2.pdf](../kassa/org/A-Trust/2016-09-05-Detailfragen-RKSV-V1.2.pdf)
    -- Abschnitt 5 -- siehe "Beispiel des DEPs wenn keine
    Signaturzertifikate vorhanden sind"

-   Verschieben des Files zum Ausgabe Pfad

-   Bei der Variante Sicherung Commit

Im folgenden Beispiel wird davon ausgegangen, dass kein
Signaturzertifikat vorhanden ist. Alle Belege -- auch wenn Sie mit
unterschiedlichen Zertifikaten signiert wurden -- werden in einer Gruppe
chronologisch abgelegt.

{

"Belege-Gruppe": [

{

"Signaturzertifikat": "",

"Zertifizierungsstellen": [],

"Belege-kompakt": [

"JWS-REP-BELEG",

"JWS-REP-BELEG",

"JWS-REP-BELEG",

"JWS-REP-BELEG",

"JWS-REP-BELEG",

"JWS-REP-BELEG",

"JWS-REP-BELEG",

"JWS-REP-BELEG"

]

}

]

}

### Reorg ka_op

Auswahlkriterien

-   Firmennummer

-   Symbol

-   Neue OP´s aufbauen (p)

-   Nicht aufbauen

-   Nur TC Rechnungen

-   Alle

Auswahl der Daten

-   Offene Posten aus pfufb_op lt. Auswahlkriterien

Ablauf

-   Pro ka_op Eintrag Update des Offenen Wertes lt. pfufb_op.  
    Wenn in pfufb_op nicht vorhanden und der OP älter als die Tage lt.
    ka_fa sind wird der ka_op gelöscht.  
    Bei "Nicht aufbauen" darf der offene Betrag nicht wieder erhöht
    werden (absolut).

-   Bei Neue OP´s Aufbauen

-   Pro OP, der nicht in ka_op vorhanden ist

-   Ermitteln Kundennummer

-   Lt. Rechnung (vrech_nr = op_nr, debitor_nr, fa_nr) und zugeordneten
    > Lieferscheinen (max kunde_cd)

-   Bei der Varinte nur TC Rechnungen werden nur Rechnungen
    > berücksichtigt, die lt. Zahlungsart auf die Kassa übergeleitet
    > werden.

-   Lt. Debitor (max kunde_cd) (nur bei Variante Alle)

-   Wenn kein Kunde ermittelt werden kann wird der OP ignoriert

-   Insert ka_op

### Archivlauf Kassenbelege

Auswahlkriterien

-   Firmennummer (p)

-   Archivieren Bis Datum (p)

-   Kassennummer

-   Belegart

Auswahl der Daten

-   Datenbasis ist ka_kartei mit bel_art = „K" UNION ka_bel

-   Maximal 500.000 Rows (Select Top 500000....)

-   Power Builder Datastores werden ab einer gewissen Anzahl Rows
    > instabil

-   Belegdatum muss älter sein als <heute> minus
    ka_fa.archiv_sicherheit_tg

-   Belege müssen verbucht und Fibugebucht sein.

-   Daten werden mit einem Dynamischen Datastore retrieved (Select \*
    from ....)

-   Damit sind Indiv-Felder berücksichtigt.

Ablauf

-   Eine Transaktion pro Row aus idw_job

-   Je Row:

-   Inserten alle ka_archiv_tabellen

-   Inserts passieren Grafisch über Datastore-Updates, damit sind
    > Indiv-Felder berücksichtigbar.

-   Bei Union Teil ka_kartei keine ka_bel... Tabellen

-   Bei Lieferscheinen keine ka_kartei

-   Nach Inserts Delete der Originaltabellen

-   Reihenfolge des Deletes beachten für Fkeys

-   Event vorsehen für etwaige Indivtabellen

-   Commit Transaktion

### Abfrage archivierte Kassenbelege

-   Keine Neuanlage, Kein Löschen, Kein Ändern.

Auswahlkriterien

-   Datum

-   Kassennummer

-   Sachbearbeitercode

-   Belegart

Liste

-   Datenbasis ist ka_archiv_bel

-   Firmennummer

-   Kassennummer

-   Kassenmatchcode

-   Belegart

-   Subbelegart

-   Kundennummer

-   Belegnummer

-   Datum

-   Uhrzeit

-   Sachbearbeiter

-   Sachbearbeitername

-   Betrag

Detail

-   Datenbasis ist ka_archiv_bel

-   Teilbereich Zahlungen

-   Teilbereich UST

-   Teilbereich vrech

    **Positionen**

-   Grid, Datenbasis ist ka_archiv_bel_pos

    **Bon**

-   Grid, Datenbasis ist ka_archiv_dj

### Abfrage archivierte Kassen Ein/Ausgänge

-   Keine Neuanlage, Kein Löschen, Kein Ändern.

Auswahlkriterien

-   Datum

-   Kassennummer

-   Sachbearbeitercode

Liste

-   Datenbasis ist ka_archiv_kartei

-   Firmennummer

-   Kassennummer

-   Kassenmatchcode

-   Belegnummer

-   Datum

-   Uhrzeit

-   Sachbearbeiter

-   Sachbearbeitername

-   Betrag

Detail

-   Datenbasis ist ka_archiv_kartei

-   Buchungstext 1-3

-   Teilbereich Zahlungen

    **Bon**

-   Grid, Datenbasis ist ka_archiv_dj

## Auswertungen

### ARA

Es sind folgende Stammdaten für die ARA-Abrechnung zu pflegen:

-   ARA-Gruppe  
    Zuordnung von Artikeln zu ARA-Gruppen. Die Auswertungen haben
    Zwischensummen pro ARA-Gruppe, da die Erfassung der zu
    entpflichtenden Packstoffe im ARA Portal nach diesen Gruppen zu
    erfolgen hat.

-   Packstoffe

-   Entsorger  
    Kunden können unterschiedlichen Entsorgern zugeordnet werden und die
    unterschiedlichen Entsorgen können unterschiedliche Tarife pro
    Packstoff haben. Das ist allerdings ein Relikt aus der reinen
    Verkaufsbezogenen Abrechnung. Die Eingangsseitige Entpflichtung kann
    mit unterschiedlichen Entsorgern, die erst durch den Verkauf
    definiert werden nicht funktionieren.

-   Am Artikel kann pro Packstoff das Gewicht pro Packstoff definiert
    werden.  
    Es ist auch möglich am Artikel Packstoffe zu pflegen und den Artikel
    trotzdem als nicht ARA-Pflichtig einzustellen.

Entpflichtung:

Lt. Verpackungsverordnung 2014 (§ 3 Z13) sind seit 1.1.2015 (mit
Übergangsfristen bis spätestens 1.1.2018) die Verpackungen bereits beim
Import/Lagereingang zu entpflichten.

TradeControl verwendet die "**Vereinfachte Eingangsseitige Feststellung
der Entpflichtungsmassen für Importverpackungen**". Siehe:
[ARA-2018.pdf](ARA-2018.pdf)

In TradeControl sind dazu 2 Auswertungen vorgesehen:

-   Die "ARA-Auswertung Stichtag/Differenz" ist zu verwenden, um die
    Packstoffe in kg für den Lagerstand zu einem Stichtag
    (Jahresendbestand) zu ermitteln.  
    Dazu wird diese Auswertung einmalig bei Umstellung oder Einführung
    der Eingangsseitigen Entpflichtung ohne Vorjahres Stichtag
    gestartet.

-   Unterm Jahr ist die ARA-Auswertung Verkaufsmengen zu verwenden.  
    Diese ermittelt die zu entpflichtenden Packstoffe in kg für die
    Verkäufe an Kunde die dem jeweiligen Entsorger zugeordnet sind.

-   Am Jahresende ist zusätzlich zur ARA-Auswertung Verkaufsmengen
    wieder eine ARA-Auswertung Stichtag/Differenz zu erstellen.

-   Zum Ultimo des Kalender- bzw. Bilanzjahres werden die
    > Importverpackungen, die auf Lager liegen, erhoben und der
    > Lagerbestand mit jenem zum Umstellungszeitpunkt verglichen. Es
    > werden dazu die Lagerstände aus der Artikel-Lager-Stichtags
    > Tabelle verwendet.

-   Ist die Lagermenge zum Ultimo des Kalender- bzw. Bilanzjahres höher,
    > ist die Differenz an das betreffende Sammel- und Verwertungssystem
    > nachzuzahlen (Importe waren höher als der Lagerausgang).

-   Ist sie geringer, kann die Differenz bei den Meldungen an das
    > betreffende Sammel- und Verwertungssystem abgezogen werden
    > (Importe waren geringer als der Lagerausgang).

#### Entsorger-Stammdatenliste

Listbild:
[arastamm.doc](file:///\\pcssrv019\projekte\tradecon\org\arastamm.doc)

Auswahldialog

-   Firma (p)

-   Sortierung (p)

-   Artikelnummer

-   Artikelmatchcode

-   Entsorgercode (pw)

-   Lieferantennummer

-   wenn ausgewählt, wird Tabelle [artik_lief] zusätzlich mitgelesen

Auswahl der Daten

-   nur arapflichtige Artikel [artik.ara_jn="j"]

-   nur Artikel mit mindestens einem zugeordneten Packstoff
    [artik_packst packst_entsorger]

-   nur Packstoffe mit Spaltenzuordnung [packst_entsorger.spalte_nr
    <> 0]

Seitenkopf:

-   Firmenkurzbezeichnung [fa.fa_adr_snr adr.adr_mc]

-   Tagesdatum

-   Uhrzeit

-   Entsorgerbezeichnung lt. [entsorger.entsorger_mc]

-   Seitennummer und Seitenanzahl

-   Spaltenüberschrift mit bis zu 10 Packstoffen

-   Bezeichnung gekürzt

-   Preis pro kg

pro Artikel:

-   Artikelnummer

-   Artikelkurzbezeichnung

-   Gewichtsangabe in kg je Packstoff (bis zu 10)

#### ARA-Auswertung Verkaufsmengen

Listbild:

[arameld.doc](file:///\\pcssrv019\projekte\tradecon\org\arameld.doc)

Auswahldialog

-   Firma (p)

-   Von Auswertungsmonat (p)

-   Bis Auswertungsmonat (p)

-   Sortierung (p)

-   Artikelnummer

-   Artikelmatchcode

-   Entsorgercode (pw)

-   Artikeldetail (p)

-   Ja

-   Nein

-   Lieferantennummer

-   wenn ausgewählt, wird Tabelle [artik_lief] zusätzlich mitgelesen

Auswahl der Daten

-   nur arapflichtige Artikel [artik.ara_jn="j"]

-   nur Artikel mit mindestens einem zugeordneten Packstoff
    [artik_packst]

-   nur Artikel mit mindestens einem zugeordneten Packstoff
    [artik_packst packst_entsorger]

-   nur Packstoffe mit Spaltenzuordnung [packst_entsorger.spalte_nr
    <> 0]

-   nur Statistiksätze von Kunden die dem ausgewählten Entsorger
    zugeordnet sind [kunde.entsorger_cd entsorger]

-   Daten aus [vlfs_pos], Menge = [lief_mg], nur Sätze für die gilt

-   vlfs_pos.vrech_mon <> ""

-   aufart_cd <> "gw"

Seitenkopf:

-   Firmenkurzbezeichnung [fa.fa_adr_snr adr.adr_mc]

-   Tagesdatum

-   Uhrzeit

-   Auswertungszeitraum

-   Entsorgerbezeichnung lt. [entsorger.entsorger_mc]

-   Seitennummer und Seitenanzahl

-   Spaltenüberschrift mit bis zu 10 Packstoffen

-   Bezeichnung gekürzt

-   Preis pro kg

pro Artikel:

-   nur wenn mit Artikeldetail

-   Artikelnummer

-   Artikelkurzbezeichnung

-   Umsatzmenge

-   Gesamtgewicht (Umsatzmenge\*Packstoffgewicht) in kg je Packstoff
    (bis zu 10)

nach dem letzten Artikel:

-   Summenzeile Gewicht je Packstoff

-   Summenzeile Betrag (Gewicht \* Packstofftarif) je Packstoff

-   Zeile mit Gesamtbetrag

#### ARA-Auswertung Stichtag/Differenz

Listbild: [wie](file:///\\pcssrv019\projekte\tradecon\org\arameld.doc)
ARA-Auswertung, jedoch ohne Zeitraum

Auswahldialog

-   Firma (p)

-   Stichtag 1 Vorjahr(o)

-   Stichtag 2 Aktuell (p)

-   Sortierung (p)

-   Artikelnummer

-   Artikelmatchcode

-   Artikeldetail (p)

-   Ja

-   Nein

-   Lager

Auswahl der Daten

-   Entsorgercode muss „ara" sein

-   nur arapflichtige Artikel [artik.ara_jn="j"]

-   nur Artikel mit mindestens einem zugeordneten Packstoff
    [artik_packst]

-   nur Artikel mit mindestens einem zugeordneten Packstoff
    [artik_packst packst_entsorger]

-   nur Packstoffe mit Spaltenzuordnung [packst_entsorger.spalte_nr
    <> 0]

-   nur Eigenlager werden gelesen

-   Artikel aus artik

Ablauf:

-   Löschen aller Daten aus hilf_ara_stichtag mit dieser Job_snr

-   Pro Artikel aus Artikelstamm

-   Lesen Daten aus artik_lag_st mit Stichtag 1 (Summe über alle Läger)

-   Menge ist 0 wenn Datensatz nicht vorhanden oder Lager negativ oder
    > parameter nicht eingegeben

-   Lesen Daten aus artik_lag_st mit Stichtag 2 (Summe über alle Läger)

-   Menge ist 0 wenn Datensatz nicht vorhanden oder Lager negativ

Allgemein

-   Die Mengen im Ausdruck verstehen sich immer als Menge2 abzüglich
    Menge1

-   Sind beide Stichtage beim Programmstart ausgewählt, so versteht sich
    > das dann als „Differenz"

-   Ist der erste Stichtag nicht ausgewählt, sind die Mengen1 überall 0,
    > d.h. die Subtraktion hat keine Auswirkung. Das versteht sich dann
    > als komplette Lagerentpflichtung

Seitenkopf:

-   Firmenkurzbezeichnung [fa.fa_adr_snr adr.adr_mc]

-   Tagesdatum

-   Uhrzeit

-   Überschrift „ARA Auswertung lt. Stichtag gesamt" wenn nur das Datum2
    ausgefüllt ist

-   Überschrift „ARA Differenz Auswertung" wenn beide Stichtage
    ausgefüllt sind

-   Stichtag 1 und 2

-   Entsorgerbezeichnung lt. [entsorger.entsorger_mc]

-   Seitennummer und Seitenanzahl

-   Spaltenüberschrift mit bis zu 10 Packstoffen

-   Bezeichnung gekürzt

-   Preis pro kg

pro Artikel:

-   nur wenn mit Artikeldetail

-   Artikelnummer

-   Artikelkurzbezeichnung

-   Lagerstand (bzw. Differenz der beiden Stichtage

-   Gesamtgewicht ((Lagerstand bzw. Differenzmenge)\*Packstoffgewicht)
    in kg je Packstoff (bis zu 10)

nach dem letzten Artikel:

-   Summenzeile Gewicht je Packstoff (ist das Gewicht < 0 0)

-   Summenzeile Betrag (Gewicht \* Packstofftarif) je Packstoff

-   Zeile mit Gesamtbetrag

Ende des Jobs:

-   Löschen Daten aus hilf_ara_stichtag mit dieser Job_snr

## CAS/CRM

### Stammdaten

Diverse Stammdaten

-   CAS

-   CAS-Gruppen

-   Mitbewerbergruppen

-   Schaltfläche für KundeMitbewerb

-   KFZ

-   Schaltfläche für Fahrtenbuch

-   Kontaktergebnisse

-   Kontaktgruppen

-   Kontakttextgrupen

-   Unterlagen

-   Reisekostengruppe (inkl. Kilometergeld und Ausnahme-PLZ´s)

TC Stammdaten die im auch CAS gewartet werden können:

-   Kunden

-   CAS Daten von allen Kunden

-   Interessenten

-   Adressen

-   Personen

###   {#section-1 .unnumbered}

### KundeMitbewerb

#### Auswahldialog

-   Firma

-   Kundennummer (f)

-   Kundenmatchcode

-   Mitbewerbergruppe (w)

-   Mitbewerbercode (f)

-   Mitbewerbermatchcode

#### Register "Liste"

-   Firma

-   Kundennummer

-   Kundenmatchcode

-   Mitbewerbergruppencode

-   Mitbewerbercode

-   Mitbewerbermatchcode

-   Umsatz

-   Datum letzte Änderung

#### Register "Detail"

-   Firma (n)

-   Kundennummer (n)

-   Matchcode (a)

-   Kunden-Infotext (a)

-   Mitbewerbergruppe (nd)

-   Mitbewerber (nd)

-   Umsatz

-   Infotext

-   Datum letzte Änderung (a)

-   Sachbearbeitercode letzte Änderung (a)

### Aktionen

#### Auswahldialog

-   Firma

-   Aktionsnummer

-   Erfassungsdatum

-   Aktionsdatum

-   Kontaktgruppe (w)

-   Kurztext (Betreff)

-   CAS Code (Notebook)

-   Offen

-   cas_aktion.erl_aktion_nr

-   Vorschlag = Offene

#### Register "Liste"

-   Firma

-   CAS-Code

-   Atkionsnummer

-   Erfassungsdatum

-   Kontaktgruppe

-   Betreff

#### Register "Detail"

-   wenn „erl_aktion_nr <> 0" nur Anzeige, keine Änderungsmöglichkeit

-   Am CAS System cas_datueb inserten

**  
**Teilbereich "Aktion"**

-   Firma

-   Eingabelogik lt. TC

-   Aktionsnummer (a)

-   CAS Code (a)

-   Erfassungsdatum (a)

-   Aktionsdatum

-   Vorschlag = Tagesdatum

-   Zustand (a)

-   offen

-   erledigt

-   Betreff

-   Kontaktgruppe (fd)

-   Kontakttextgruppe (fd)

-   Default-Kontaktergebnis für Kontaktaufbau (fd)

-   es darf kein Ergebnis, das eine Wiedervorlage auslöst, ausgewählt
    > werden

-   Kontakte erzeugen (d)

-   Nein

-   Kundenbezogen

-   Personenbezogen

#### Schaltflächen für Verzweigungen

-   Kontakte / Besuchsberichte

### Kontakte aus Aktionen erzeugen

#### Auswahldialog - Kundenbezogen

-   Land

-   PLZ

-   Ort

-   CAS Gruppe

-   Verkaufskonditionsgruppe (w)

-   Preislistencode (w)

-   Erlöszuordnungsgruppe (w)

-   Abrufgruppe (w)

-   Debitorennummer

-   0 = Nur Interessenten

-   >0 = Keine Interessenten

-   Datum des letzten Kontaktes

-   DatMin = Noch nie kontaktiert

-   Besuch lt. Intervall fällig Ja/Nein (p) (Nein = Default)

-   Vorlauftage für fällige Besuche lt. Intervall (p)

-   Freie Gruppen (3x)

-   Gruppenart (p)

-   Keine ist möglich

-   Gruppenwert

-   Freie Columns (3x)

-   Freie CAS Columns (3x)

-   Freie CAS Gruppen (3x)

-   Umsatz Periode(n)

-   Umsatz

#### Auswahldialog - Personenbezogen

-   Land (Werbeadresse)

-   PLZ (Werbeadresse)

-   Ort (Werbeadresse)

-   CAS Gruppe

-   Verkaufskonditionsgruppe (w)

-   Preislistencode (w)

-   Erlöszuordnungsgruppe (w)

-   Abrufgruppe (w)

-   Debitorennummer

-   0 = Nur Interessenten

-   >0 = Keine Interessenten

-   Datum des letzten Kontaktes

-   DatMin = Noch nie kontaktiert

-   Besuch lt. Intervall fällig Ja/Nein (p) (Nein = Default)

-   Vorlauftage für fällige Besuche lt. Intervall (p)

-   Freie Gruppen (3x)

-   Gruppenart (p)

-   Keine ist möglich

-   Gruppenwert

-   Freie Columns (3x)

-   Freie CAS Columns (3x)

-   Freie CAS Gruppen (3x)

-   Geburtsdatum

-   Funktion der Person (w)

-   Freie Gruppen - Personen (3x)

-   Freie Columns - Personen (3x)

-   Umsatz Periode(n)

-   Umsatz

#### Register "Liste"

-   Kundennummer

-   Kundenmatchcode

-   Strasse

-   Land

-   PLZ

-   Ort

-   Bei Personen

-   Personencode

-   Titel

-   Vorname

-   Nachname

-   Funktion

-   Bei Kunden

-   Umsatzwert

-   Kontakt aufbauen (c)

-   Defaultwert "j"

-   kann editiert werden

#### Auswahlpunkte im Menü "Extras" 

-   Kontakte aufbauen

-   Für die gekennzeichneten Zeilen wird ein Kontakt aufgebaut

Allgemeines

-   Es werden nur aktive Kunden verwendet

-   Für die gekennzeichneten Kunden/Personen wird je ein offener Kontakt
    aufgebaut

-   Neuanlage und Löschen ist nicht möglich

-   werden "nur fällige Besuche" ausgewählt, nehmen jene Kunden an der
    Aktion teil, deren Sollbesuchsdatum (= Datum letzter Besuch lt.
    Kunde + Besuchsintervall \* 7) <= (Aktionsdatum + Vorlauftage) ist.
    Das tatsächliche Besuchsdatum ist das nächste Datum auf den der
    Besuchswochentag fällt. Ist dieser Tag jedoch kleiner als das
    Aktionsdatum, ist das Besuchsdatum der nächste Besuchswochentag >=
    Aktionsdatum; Ist das Aktionsdatum unbestimmt, wird das Tagesdatum
    herangezogen

-   ansonsten wird das Aktionsdatum als Kontaktdatum abgestellt

### Tagesdaten Besuchsbericht/Reisekosten

Tabelle: castag

Auswahlkriterien

-   Firma (f)

-   Personencode

-   Datum

-   KFZ (w)

-   Reisekosten Tages KZ (w)

Liste

-   Firma

-   Personencode

-   Nachname

-   Vorname

-   Datum

-   KFZ Code

-   KFZ Matchcode

-   Reiko KZ

-   Stunden (s)

-   Tag Nr

-   Von Zeit

-   Bis Zeit

-   AZ Stunden (s)

-   Text

-   Nächtigung (c)

-   Spesen (s)

-   gef. km (s)

-   keine Privatfahrten

Detail

-   Firma

-   Personencode

-   Datum

-   Tages KZ (d)

-   KFZ (d)

-   Vorschlag lt. letzten Tag der Person

-   Abfahrts Zeit

-   Abfahrts km-Stand

-   Vorschlag lt. letztem Fahrtenbucheintrag des KFZ, wenn es diesen
    > nicht gibt ist eine freie Eingabe möglich

-   Keine Änderung bei einem lückenlosen Fahrtenbuch

-   Keine Änderung möglich wenn bereits Fahrtenbucheinträge für den Tag
    > oder danach vorhanden sind

-   Anzahl Stunden Reisekosten

-   Text

-   Von Zeit AZ

-   Bis Zeit AZ

-   AZ Pause Stunden

-   Bei Eingabe wird die AZ Vermindert

-   AZ Stunden

-   Erfassungszeitpunkt (a)

-   Spesen (a)

-   TagesNr (a)

-   Nächtigung (c)

-   Manuell (c)

-   Ja wenn reiko_rech_kz = manuell

-   Wenn es deaktiviert wird, wird das reiko_rech_kz auf offen gesetzt

Allgemeines

-   Wenn die TC.next ADM Lösung in Betrieb ist (Parameter tcnext_adm
    = j) ist hier nur eine Abfrage möglich (kein Neuerfassen, kein
    Löschen).  
    Es können das Tages-KZ, KFZ und Fahrtenbuchdaten nicht mehr geändert
    werden.

Register Buchungen

-   reine Abfrage einer kombinierten Liste von Besuchsbericht und
    Fahrtenbuch

-   KZ Fahrtenbuch / Besuch (f/b)

-   Von Zeit

-   Über Von oder Bis Zeit kann das Fahrtenbuch oder der Besuchsbericht
    > geöffnet werden

-   Bis Zeit

-   Zeit (s)

-   Differenz Von/Bis-Zeit im Forma HH:MM

-   KFZ

-   Von KM

-   Nur bei Fahrtenbuch

-   Bis KM

-   Nur bei Fahrtenbuch

-   gefahrene KM (s)

-   Privat (c)

-   Start/Ziel

-   Bei einem Besuchsbericht sind beide gleich

-   Kundennummer

-   Wenn ausgefüllt

-   Kundenmatchcode

-   Wenn ausgefüllt

-   Straße

-   Land

-   PLZ

-   Ort

-   Kontaktgruppe

-   Nur bei Besuchsbericht

-   Text

-   Fahrtenbuch: fabu_txt

-   Besuchsbericht: kont_mc

Buttons

-   Besuchsbericht

-   Fahrtenbuch

-   Lt. Datum und Person

-   Reisekosten

### Kontakte / Besuchsberichte

#### Auswahldialog

-   Firma

-   Kontaktnummer

-   Erfassungsdatum

-   Kontaktdatum

-   Kontaktgruppe (w)

-   Kontaktergebnis (w)

-   Kundennummer (f)

-   Kundenmatchcode

-   Plz

-   Ort

-   Personencode Ansprechpartner (f)

-   Kurztext (Betreff)

-   CAS Code (Notebook)

-   Aktionsnummer

-   Offen

-   cas_kont.erl_kont_nr

-   Vorschlag = Offene

#### Register "Liste"

-   Firma

-   CAS-Code

-   Kontaktnummer

-   Erfassungsdatum

-   Kontaktdatum

-   Von Uhrzeit

-   Kontakt-Gruppe

-   Kontaktergebnis

-   Betreff

-   Person der eigenen Firma

-   Kundennummer

-   Name 1

-   Plz

-   Ort

-   Personencode Ansprechpartner

-   Wert

-   Aktionsnummer

-   Aktionsmatchcode

-   Dokumentname

-   TC-Offert- bzw. Auftragsnummer

Sortierung: Kontaktdatum

#### Register "Detail"

-   wenn „erl_kont_nr <> 0" nur Anzeige, keine Änderungsmöglichkeit

-   Am CAS System cas_datueb inserten

Teilbereich "Kontakt"

-   Firma

-   Eingabelogik lt. TC

-   Kontaktnummer (a)

-   Erfassungsdatum (a)

-   Sachbearbeiter der eigenen Firma (d)

-   Vorschlag lt. usr_login

-   Kundennummer

-   Eingabelogik Nummer und Matchcode

-   Kundenmatchcode(a)

-   Name 1

-   Name 2-4

-   Strasse

-   Land

-   Postleitzahl

-   Ort)

-   Ansprechpartner Code (fd)

-   Personencode

-   Vorname + Nachname

-   Funktion

-   Ansprechpartner

-   Titel + Vorname + Nachname

-   Kontaktdatum

-   Uhrzeit von/bis

-   Aktion (fd)

-   Im DropDown wird der Matchcode von offenen Aktionen angezeigt

-   Betreff

-   Kontaktgruppe (fd)

-   Ergebnis (fd)

-   Datum für Wiedervorlage

-   Eingabe erforderlich wenn lt. Ergebnis notwendig

-   bestimmt auch Wiedervorlagewoche

-   Woche für Wiedervorlage

-   bestimmt auch Wiedervorlagedatum (immer Montag der Woche)

-   Datum muss größer Kontaktdatum sein

-   Wert

-   Dokumentname (f)

-   öffnen-Funktion

-   suchen-Funktion

-   der Ordner lt. Dokumentenpfad wird geöffnet

-   Nach Dokumentenauswahl wird Pfad und Name belegt

-   TC-Offert- bzw. Auftragsnummer (f)

-   Priorität für Reorg

-   Fahrzeug (d)

-   Es wird das Fahrzeug des letzten Fahrtenbuchrelevanten
    > Besuchsberichts des Sachbearbeiters ansonsten lt. castag.

-   Änderung möglich, wenn es keinen Fahrtenbucheintrag zum
    > Besuchsbericht gibt

-   Wenn von einem Fahrzeug ohne Fahrtenbuch auf eines mit Fahrtenbuch
    > geändert wird, muss die Beginnzeit des Termins nach dem letzten
    > Fahrtenbucheintrag liegen.

-   Abfahrtstzeit

-   Keine Eingabe od. Anzeige, wenn das Fahrzeug kein Auto ist (fabu_kz
    > = "s").

-   Es wird die Bis Uhrzeit des letzten Fahrtenbuchrelevanten
    > Besuchsberichts des Sachbearbeiters an diesem Tag vorgeschlagen,
    > ansonsten lt. castag.

-   Muss < der Beginnzeit des Termines sein

-   Muss > der Zeit des letzten Fahrtenbucheintrags und des letzten
    > Fahrtbuchrelevanten Besuchsberichts sein

-   KM Stand

-   Ist der Bis-KM Stand der Anfahrt

-   Keine Eingabe, wenn lt. Fahrzeug kein Fahrtenbucheintrag erstellt
    > werden soll

-   Bei Neuerfassung des Fahrtbucheintrags muss er > als der letzte KM
    > Stand sein

-   Bei einer Änderung muss er > des Von-KM Standes dieser Buchung und
    > < des Bis-KM Standes des nächsten Fahrtenbucheintrags sein.

-   Mit diesen Daten wird ein Fahrtenbucheintrag erstellt.

-   gefahrene KM (a)

-   Bei Neuerfassung Fahrtenbuch Differenz le. KM Stand zu erfasster KM
    > Stand

-   Bezugskontaktnummer (a)

Teilbereich "Texte"

Liste mit folgenden Daten:

-   Ansprechpartner (fd)

-   Logik wie Detail

-   Vorschlag 1. Zeile: Detail

-   Vorschlag ab 2. Zeile: vorhergehende Zeile

-   Textgruppe (fd)

-   Text

-   Sachbearbeiter der eigenen Firma für Benachrichtigung (d)

-   Bei Eintrag eines Sachbearbeiters wird diesem ein E-Mail geschickt.

-   Abhängig von cas.email_jn wird die E-Mail beim Speichern des
    > Kontakts erstellt, ansonsten bei der Übernahme in TC.

-   Betreff: "Kontakt " Kontaktnummer / CAS-Code / Firmennummer

-   Text:  
    > Kunde: kunde_cd kunde_mc  
    > Betreff: kont_mc  
    >   
    > Texte

-   Der Ansprechpartner, die Textgruppe und der Sachbearbeiter für
    Benachrichtigungen werden bei einer neuen Zeile von der
    vorhergehenden vorgeschlagen.

**Teilbereich "Unterlagen"**

Liste mit folgenden Daten:

-   Person des Kunden, dem die Unterlagen übergeben wurden (d)

-   Unterlage (fd)

-   Text

Schaltflächen für Verzweigungen

-   Fahrtenbuch

-   Reisekosten

-   Personen

**Allgemeines**

-   Wenn die TC.next ADM Lösung in Betrieb ist (Parameter tcnext_adm
    = j) ist hier nur eine Abfrage möglich (kein Neuerfassen, kein
    Ändern, kein Löschen).

-   Wird der Status des Kontaktes geändert, wird nach dem Speichern der
    Status der Aktion überprüft und evt. geändert. - Muss in der DFÜ
    berücksichtigt werden.

-   Beim Speichern wird

-   abhängig von der Kontaktgruppe das Datum "Letzter Kontakt" bzw.
    > das Datum "nächster Besuch" am Kundenstamm aktualisiert.

-   castag Eintrag erstellt bzw. der Status gesetzt

-   der Fahrtenbucheintrag lt. Abfahrtszeit und bis-KM Stand wird
    > erstellt

#### Auswahlpunkte im Menü "Extras"

-   Dokument auf alle Kontakte der Aktion kopieren

-   aktuelle Aktionsnummer muss <> 0 sein

-   Dokumentenname muss belegt sein

### Fahrtenbuch

Auswahldialog

-   Fahrtenbuch Nr

-   Firma

-   KFZ (w)

-   Von km

-   Bis km

-   Von Datum

-   Bis Datum

-   Text

-   Fahrer

-   Privat Ja/Nein

Register "Liste"

-   FahrtenbuchNr

-   Firma

-   KFZ

-   KFZ Matchcode

-   Von km

-   Bis km

-   gef. km (s)

-   Von Datum/Zeit

-   Bis Datum/Zeit

-   Text

-   Fahrer

-   Privat Ja/Nein

-   Betrag (s)

-   Betrag Text

-   Start/Ziel

-   Kundennummer

-   Kundenmatchcode

-   Straße

-   Land

-   PLZ

-   Ort

Register "Detail"

-   Fahrtenbuchnummer

-   Firma

-   Eingabelogik lt. TC

-   KFZ (d)

-   Fahrer (Person der eigenen Firma) (d)

-   Vorschlag lt. usr_login

-   Von km

-   Vorschlag von letztem bis_km

-   kann abgeändert werden, wenn lt. KFZ erlaubt

-   muss >= letzter bis_km sein

-   Bis km

-   Muss > von_km sein

-   Gefahrene km

-   Errechnet sich aus bis - von_km

-   Bei Eingabe wird Bis km ausgerechnet

-   Erfassungsdatum (a)

-   Von Datum

-   Vorschlag = Tagesdatum

-   Muss >= letztem Datum lt. kfz sein

-   Von Zeit

-   HH und MM getrennt eingeben

-   Bis Datum

-   Vorschlag = Von Datum

-   Bis Zeit

-   HH und MM getrennt eingeben

-   Zweck (d)

-   Durch Auswahl von Heimfahrt, wird die Werbeadresse der Person als
    > Ziel Adresse vorgeschlagen, wenn diese von der Firmenadresse
    > abweiche (werbe_adr_srn <> adr_snr)

-   Text

-   Betrag

-   Betrags Text

-   Privatfahrt (c)

-   Start/Ziel:

-   Als Start Kunde/Adresse wird immer die letzte Ziel Adresse des KFZ
    > lt. Fahrtenbuch vorgeschlagen

-   KundeNr (f)

-   ColSearch

-   Es wird die Adresse des Kunden als Adresse vorgeschlagen

-   Kundenmatchcode (a)

-   Name 1

-   Name 2

-   Name 3

-   Strasse

-   Land

-   Plz

-   Ort

**Allgemeines**

-   Wenn die TC.next ADM Lösung in Betrieb ist (Parameter tcnext_adm
    = j) ist hier nur eine Abfrage möglich (kein Neuerfassen, kein
    Ändern, kein Löschen).

-   Von Datum/Zeit muss < als Bis Datum/Zeit sein

-   Der Bis-Kilometerstand und das Bis Datum wird in die Tabelle kfz als
    letzter Kilometerstand upgedatet.

-   Ist das Datum mehr als die Anzahl Werktage für die Änderung von
    Fahrtenbucheinträgen lt. pfu_param "fabu_aend_tg" in der
    Vergangenheit, ist kein Löschen und kein Ändern von Daten möglich.

-   Beim Löschen wird im kfz der Kilometerstand auf den von_km, und das
    Datum auf das Bis Datum des letzten Fahrtenbucheintrages gesetzt.  
    In einem zugeordneten Kontakt wird der kfz_cd und von_km auf "", 0
    gestellt.

-   Bei Änderung des Bis-KM Standes oder des Bis-Zeitpunkts

-   Bei der letzten Buchung -- Update KFZ

-   Ansonsten Von KM der nächsten Buchung

-   Insert od. Update castag. Der Insert erfolgt nicht, wenn es sich um
    eine Privatfahrt handelt.

Schaltflächen für Verzweigungen

-   Kontakte/Besuchsberichte

### Reisekosten

Auswahldialog

-   Firma

-   Sachbearbeiter (w)

-   Datum

-   Reisekostenpos KZ

-   Reisekostennummer

-   Buchungstext

-   Kontaktnummer

Register "Liste"

-   Firma

-   Reisekostennummer

-   Datum

-   Sachbearbeiter

-   Reisekostpos-KZ

-   Spesen (s)

-   Text

Register "Detail"

-   Firma

-   Eingabelogik lt. TC

-   Reisekostennummer (a)

-   Sachbearbeiter

-   lt. usr_login

-   Datum

-   Vorschlag = Tagesdatum, bei Aufruf aus Kontakt Kontaktdatum

-   Reisekostenart (d)

-   Betrag

-   Text

-   Belegnummer

-   Kontaktnummer

-   Kontaktmatchcode (a)

-   Manu (c)

-   Bild (a)

### Reisekosten Aufbau

Ablauf

Pro Person wird der kleinste Datum mit reiko_rech_kz = "o" aus castag
ermittelt.

-   Beginnend mit diesem Daten werden auch alle nachfolgenden Tage neu
    berechnet

-   Dazu werden alle Fahrten und Besuchsberichte des Tages/Users
    > eingelesen und pro Datensatz bestimmt, ob dieser
    > Reisekostenrelevant ist

-   Ein Fahrtbucheintrag ist reisekostenrelevant

-   wenn es keine Privatfahrt ist

-   wenn die Zieladresse nicht in den PLZs lt. casreikogrp_plz vorkommt
    > (Die Filiale ist dabei die Filiale des Defaultlagers der Person).
    > Bei der Heimfahrt oder der Fahrt ins Büro wird die Startadresse
    > und nicht die Zieladresse geprüft.

-   Ein Besuchsbericht ist reisekostenrelevant

-   wenn die Kontakgruppe Reisekostenrelevant ist

-   wenn die Adresse nicht in den PLZs lt. casreikogrp_plz vorkommt

-   Wenn reiko_rech_kz <> "m"

-   Die erste Von Zeit einer Buchung wird als AZ.Von/Zeit und die letzte
    > Bis-Zeit einer Buchung wird als AZ-Bis-Zeit eingetragen.
    > (unabhägig von der Reisekostenrelevanz). Es dürfen dabei jedoch
    > keine Privatfahrten berücksichtigt werden.

-   Als Abeitszeit-Stunden wird die Differenz zwischen Von und Bis Zeit
    > ermittelt.

-   Ist dies Zeit >= der Mindest-Stunden für die AZ Pause, wird die
    > AZ-Pause eingetragen und diese von der Arbeitszeit abgezogen.

-   Die Reisekosten-Stunden sind die Summe der Zeiten der
    > reisekostenrelevanten Datensätze.  
    > Bei einer Nächtigung wird auch die Zeit nach der letzten Buchung
    > bis zum Tagesende und bei einer Nächtigung am Vortag die Zeit vor
    > der ersten Buchung mitgerechnet.

-   Sind die Reisekosten Std. >= der Diäten Mindest Stunden lt.
    > Reisekostengruppe, wird

-   die reiko_tag_nr neu bestimmt (max reiko_tag_nr in dem Monat für den
    > User vor unserem Datum +1), sonst auf 0 gesetzt.

-   Es wird ein Diäten Reisekosten Eintrag erstellt, geändert oder auch
    > wieder gelöscht (ausgenommen es ist bereits ein manuelle erfasstet
    > Reisekonsten Datensatz vorhanden).

-   reikopos_kz = \'di\'

-   spesen_wt = Diätensatz oder vermindertet Diäntensatz lt.
    > Reisekostengruppe.  
    > Sind die Stunden kleiner der Stunden für den Tagessatz, so
    > spesen_wt / di_tagsatz_std \* reiko_anz_std

-   Für die nicht privat KM mit Privatautos wird ein Reisekosteneintrag
    > generiert

-   Dazu werden die bereits mit Privat KFZ gefahrenen nicht Privat KM
    > des Users im Kalenderjahr summiert

-   Es wird der der gültige Kilometer Satz und die Reisekostenart lt.
    > caskmg ermittelt

-   die gefahrenden KM \* Kilometer Satz ergibt den Spesen Betrag.

-   Wenn es dabei eine Staffel Stufe überschritten wird, kann es sein,
    > dass mehrere Reisekosteneinträge mit Unterschiedlichen
    > Reisekostenarten generiert werden müssen.

-   Es erfolgt keine Neuberechneung, wenn für den User/Tag bereits ein
    > manueller km-Geld Reisekosteneintrag vorhanden ist.

-   Als Text für die Reisekostenabrechnung wird folgender Text generiert
    > (eigenes Event):

-   Erste Start Adresse (Ort PLZ), wenn die PLZ und die Straße der
    > Startadresse der Werbeadresse der Person entsprechen dann wird
    > statt dessen das Kürzel lt. adr_pers_fa verwendet.

-   Pro Besuchsbericht mit caskontgrp.fabu_jn = "j"
    > <Kunden-Matchcode> <PLZ>

-   Letzte Ziel Adresse (Ort PLZ), hier ebenfalls Kürzel lt. Person,
    > wenn die PLZ und Strasse der Werbeadresse der Person entsprechen.

-   <Start> - <1.Kunde> - <2.Kunde> - <Ziel>

-   z.B. "WA - ASMAG 4644 - MIBA 4655 - KUNSTSTOFF 4550 - GRUNDNER
    > 4550 - AGRU 4540 - MOULD 4563 - WA"

### Druck Fahrtenbuch

Listbild: [fabu.docx](fabu.docx)

Auswahldialog

-   Firma (p)

-   KFZ (w)

-   Von Datum (p)

-   Bis Datum (p)

Folgende Daten werden angedruckt:

Im Kopf:

-   KFZ-Code

-   KFZ-Matchcode

-   Druckdatum/Zeit

-   Seitennummer/Anzahl

Erste Start Adresse

-   Kundenmatchcode

-   Kundennummer

-   PLZ

-   Ort

-   Straße

Pro Fahrtenbucheintrag:

-   Von Datum/Zeit

-   Bis Datum/Zeit

-   Reisewegtext (lt. Zieldaten)

-   Kundenmatchcode

-   Kundennummer

-   PLZ

-   Ort

-   Straße

-   Zweck der Fahrt

-   Text

-   von KM

-   bis KM

-   Gefahrene KM

-   Priv (c)

-   Fahrercode

-   Betrag

-   Betrag Text

Am Ende:

-   Summe gefahrene km

-   Summe Betrag

-   Summe gefahrene km Beruflich

-   Summe gefahrene km Privat

-   Summe gefahrene km seit Wirtschaftsjahresbeginn vom von_datz der
    letzten Position Beruflich

-   Summe gefahrene km seit Witschaftsjahresbeginn vom von_datz der
    letzten Position Privat

### Druck Reisekostenabrechnung

Listbild: [reiko.docx](reiko.docx)

Auswahldialog

-   Firma

-   Monat (o)

-   Datum (o)

-   Es muss entweder Datum oder Monat angegeben werden. Das Datum dient
    > nur zum Ermitteln des Monats, wenn dieses nicht angegeben ist.  
    > Dient zum automatischen Versenden der vorläufigen RK Abrechnung an
    > alle Vertreter für das Monat vor einer Woche.

-   Sachbearbeiter (w)

-   Endgültig/Vorläufig (p)

-   Versenden/Drucken (p)

-   Bei Versenden wird die Reisekostenabrechnung an den Sachbearbeiter
    > per E-Mail gesendet.

Ablauf

-   Update der Jobnummer in castag (nur bei Endgültig)

-   Aufbau PDF

-   Bei Versenden wird es, wenn am Sachbearbeiter eine E-Mail Adresse
    > hinterlegt ist, an diese versendet. Ansonsten gedruckt

Folgende Daten werden gedruckt:

Im Kopf:

-   Monat

-   Druckdatum

-   Uhrzeit

-   Seitennummer

-   Seitenanzahl

-   Personen Code

-   SB Name (Vorname + " " + Nachname)

-   Text "ENDGÜLTIG" od. "VORLÄUFIG"

Pro Tag:

-   Tagesnummer

-   Tag (lt. Datum)

-   Von Zeit

-   Bis Zeit

-   Stunden

-   \+ "N" bei Nächtigung

-   Text

-   Arbeitszeit in Std.

-   Pausenzeit

-   gefahrene Km (des Users an diesen Tag -- keine Privatfahrten)

Pro Position:

-   Positionsart

-   Spesen

-   Belegnummer

Am Ende:

-   Summe Reisezeiten

-   Summe Arbeitszeiten

-   Summe gef. km

Pro Spesenart:

-   Positionsart

-   Spesen

-   Endsumme

### Druck Besuchsbericht

Auswahlkriterien:

-   Kontakt Nummer

-   Firmennummer (w)

-   Kundennummer (f)

-   Kundenmatchcode

-   Kontakt-Datum

-   Sachbearbeitercode (w)

-   Kontaktgruppe (w)

-   Kontaktergebnissgruppe (w)

-   Kontakttextgruppencode (w)

-   Dient nur zur Suche der Kontakte (tabdazu).Wenn ein Kontakt einen
    > Text mit einer passenden Gruppe enthält werden zu dem Kontakt alle
    > Text gedruckt.

-   Endgültig (o)

-   Wenn aktiviert, werden nur Besuchsberichte mit Druck Job-Nr. 0
    > verwendet und nach dem Drucken die Druck Job-Nummer auf die
    > aktuelle Jobnummer upgedatet.

Listbild: [besuchsbericht.docx](besuchsbericht.docx)

Folgende Daten werden angedruckt:

Im Kopf:

-   Sachbearbeitername

-   Seitenwechsel pro Sachbearbeiter

-   Druckdatum + Zeit

-   Seitennummer + Seitenanzahl

Pro Kontakt:

-   Adresse

-   Kundennummer

-   Kontaktnummer

-   Betreff (Matchcode)

-   Kontakt-Datum

-   Kontakte-Gruppen Matchcode

-   Von/Bis Zeit

-   Kontakte-Ergebnis

Pro Kontakttextgruppe

-   Kontakttextgruppenmatchcode

Pro Ansprechpartner

-   Ansprechpartner Name (Titel + Vorname + Nachname)

Pro Textzeile

-   Text

Sortierung:

-   Sachbearbeitercode

-   Kontakt-Datum - VonZeit

-   Kontakttextgruppe

-   Ansprechpartner-Code

-   Zeilennummer

### Reorganisation

Anmerkung WS: es ist hier nicht alles beschrieben

#### Reorganisation Offert

-   Offerte, deren Gültigkeit [auf.lief_dat] <= Tagesdatum +
    [fa.offert_erledigt_tg] ist, werdenauf erledigt gesetzt

### Reorganisation Kontakte

#### Auswahldialog

-   Firma (p)

-   Bis Kontaktdatum (p)

-   CAS-Code

-   Priorität Reorganisation

Auswahl der Daten

-   erledigte Kontakte

Ablauf

-   Lock Debitor (je Kontakt)

-   Lock Kontakt

-   Löschvorgang

-   cas_kont_txt

-   cas_kont_casunt

-   cas_kont

### Datenaustausch

-   Alle Änderungen in der TC DB werden mittels Trigger in der Tabelle
    cas_trig mitprotokolliert. Die Trigger werden pro Kunde individuell
    erstellt.

-   Ein Batch Programm baut für die eigentliche DFÜ die Tabelle cas_dfue
    auf

-   Bei einem Update Satz wird versucht den Datenstring eines
    > bestehenden Insert oder Update Satzes (gleiche Tabelle und gleiche
    > Key Felder) upzudaten. Gibt es nichts zum updaten erfolgt ein
    > Insert.

-   Dies erfolgt nur für CAS Systeme mit dem selben DB(i) Release wie im
    > TC

-   Bei der eigentlichen DFÜ werden die Datensätze auf cas_dfue
    übertragen

#### Erstmalige Datenübernahme

Auswahlkriterien

-   Notebook (cas_cd) (w)

Ablauf

-   Zuerst werden alle Daten mit dem betreffenden cas_cd aus der
    cas_trig gelöscht und die letzte DFÜ-Nummer in cas auf 0 gestellt.

-   Es werden die Primary Key´s aller Datensätze in den Tabellen lt.
    cas_tab in der Reihenfolge der sort_nr durch Abarbeiten eines
    Datastores ( d_casdu_<Tabelle>) in die Datenübernahme Tabelle
    geschrieben.

-   Wenn lt. cas_tab ein Datastore verwendet wird, so wird dieser mit
    > d_casdu_<Tabelle> aufgerufen. Eine evt. CAS-Gruppe wird dabei
    > als erster Parameter, eine Zeitraum als 2. Parameter übergeben.

-   Ansonsten wird ein Datastore über die Primary Key Felder der Tabelle
    > aufgebaut (über die View siehe sql/div/pfu_tab_pk.sql)

-   Eine Transaktion pro Datensatz.

-   Die Zuordnung der Kunden zu einem bestimmten CAS-System (Notebook)
    erfolgt über die CAS-Gruppe am Kundenstamm. Bei den betroffenen
    Datastores muss der Kunde und die Zuordnungstabelle mitgejoint
    werden.

-   Es muss gewährleistet sein, das Preishaupt- und Subkunde entweder in
    der selben CAS Gruppe sind, oder der Hauptkunde muss in einer CAS
    Gruppe sein, die an alle Notebooks übertragen wird.

-   Wird eine neue CAS - CAS-Gruppenzuordnung eingetragen, werden alle
    CAS-Gruppenbezogenen Tabellen wie bei der Erstbestückung übertragen.
    Bzw. beim Löschen in umgekehrter Reihenfolge als gelöscht
    übertragen. Das betrifft die Tabelle kunde_casgr und cas_casgr.  
    Dazu müssen alle Grupenbezogenen Tabellen über ein Datastore gelöst
    werden, welches auch den Kundenstamm beinhaltet. Die where Bedingung
    kann in diesem Fall um die Kundennummer ergänzt werden.

Im Standard sind folgende Tabellen vorgesehen

  -----------------------------------------------------------------------
  Tabelle                                           CASGr          Zr
  ------------------------------------------------- -------------- ------
  abrugr                                                           

  adr                                                              

  adr_pers                                                         

  adr_pers_fa                                                      

  adr_pers_komid                                                   

  debitor                                                          

  entsorger                                                        

  fa                                                               

  fil                                                              

  komidart                                                         

  kunde                                             x              

  kundeerl                                                         

  kundekst                                                         

  kuneprovgr                                                       

  kundevkkondgr                                                    

  lag                                                              

  land                                                             

  liefbed                                                          

  persfunktion                                                     

  preisli                                                          

  sprache                                                          

  st_kd_mon                                         x              x

  waehrung                                                         

  zahlart                                                          

  pfufb_debitor                                                    

  pfu_.... Tabellen                                              
  -----------------------------------------------------------------------

#### Laufende Datenübernahme TC CAS

Trigger

-   Die Änderungen in den TC Tabellen werden durch Trigger in die
    Tabelle cas_trig geschrieben

-   Diverse Reorganisationsprogramme sollten auf unnötige Updates
    überprüft werden.  
    z.B. Update set resmg = 0 where 1 = 1; um and resmg <> 0 erweitern
    ...

FIBU-Daten

-   Auf den Notebooks ist immer die Version ohne FIBU aktiv. d.h.
    pfufb_debitor und pfufb_kreditor sind Tabellen.

#### Export aus TC

Auswahlkriterien

-   CAS-Code

Ablauf

-   Es werden die Daten lt. cas_trig ausgelesen und als ASCII File
    ausgegeben

-   Prüfen ob im Verzeichniss c:\\temp\\cas ein Ausgefile mit der
    letzten DFÜ Nummer als Filename vorhanden ist. Wenn dass der Fall
    ist, wird keine neue dfue_nr vergeben und dieses File wird ergänzt.

-   Vergabe und Update der DFÜ Nummer in der Tabelle CAS  
    Im Verzeichniss cas.dfue_exp_path lt. eingegebenen CAS-Code  
    Filename: <cas_cd>-<dfue_nr>.tce

> Kopfsatz:

-   Empfäger CAS-cd,

-   DFÜ-Nummer

-   3 x DB-Rel. (aus cas mit cas_cd = " ")

-   Ermitteln der größten snr in cas_trig für den CAS-Code

-   Aufbau eines DS mit alle Datensätzen für den CAS-Code sortiert nach:

-   Tabname

-   cd1 -- 8

-   cas_trig_snr

-   Bei Wechsel der Tabelle wird ein neuer Datastore definiert

-   Ein Lösch Datensatz wird ignoriert, wenn danach ein weiterer Eintrag
    für denselben Datensatz (tabname, cd1 -- 8) folgt.

-   Bei einem Lösch Datensatz werden keine Daten abgestellt

-   Bei einem Insert oder Update Datensatz werden alle darauf folgenden
    Update oder Insert Datensätze ignoriert

-   Bei Insert und Update werden über den Datastore alle Felder der
    Tabelle ausgelesen

-   jeder abgearbeitete Datensatz wird sofort aus der Tabelle cas_trig
    gelöscht (jeweils eine eigene Transaktion)

Es wird folgender Datensatz -- Trennzeichen Tabulator -- ausgegeben:

-   cas_trig_snr

-   tabname

-   akt_kz

-   cd1 -- 7

-   Alle Datenfelder sortiert nach Spaltennamen

-   Am Ende wird ein Ende Datensatz Ausgegeben: "%%ENDE%%"

-   Das File wird in das Verzeichniss cas.drue_exp_path verschoben.

-   Ist eine E-Mail Adresse eingetragen, wird das File sofort per E-Mail
    an diese Adresse geschickt.

> Betreff: TC-Update Nr. <dfue_nr>  
> Text: Bitte speichern sie den Anhang im Verzeichniss:
> <dfue_imp_path>

#### Empfang TC-Daten (eigene Applikation)

-   Es wird im Import Verzeichniss das Import File mit der nächsten
    DFÜ-Nummer lt. cas gesucht.

-   Es wird der Kopfsatz geprüft, cas_cd, dfue_nr und alle 3 DB-Rel.
    müssen mit den Daten der eigenen Datenbank übereinstimmen.  
    Wenn der Release nicht übereinstimmt, werden die Fehlenden Release
    Updates ausgeführt.

-   Die Daten werden in die Tabelle cas_dfue importiert

-   Wenn kein Ende Datensatz übermittelt wurde wird keine Verarbeitung
    der Daten durchgeführt.

-   Das Input File wird gelöscht.

Verarbeitung

-   Abarbeiten der Tabelle cas_dfue sortiert nach cas_trig_snr

-   Update, Insert oder Delete lt. akt_kz

-   Wenn bei einem Insert der Datensatz bereits vorhanden ist, wird
    statt dessen ein Update gemacht

-   Wenn bei einem Update der Datensatz noch nicht vorhanden ist, wird
    statt dessen ein Insert gemacht

-   Im Fall eines Fehlers wird die Fehlermeldung in cas_dfue.err_txt
    upgedatet.

-   Wenn alles gut geht wird der cas_dfue Datensatz gelöscht.

-   Hat es Fehler gegeben, so wird ein 2 Durchgang versucht (da jetzt
    evt. F-Key Probleme nicht mehr vorhanden sind).

-   Updae der letzten ltz_dfue_nr in der Tabelle cas

Aussnahmen

-   pfu_inst

-   Die inst_nr wird auf den Notebooks fix auf 1 gesetzt.

-   Dadurch ist gewährleistet, dass sich die SNR´s der Gridschemas mit
    > keinen anderen Gridschemas überschneiden, da keine Daten in die
    > Zentrale zurückübertragen werden.

-   pfu_db

-   Die Datenbankspeziefischen Daten werden Fix aus der aktuellen
    > Datenbank ausgelesen.

Release Updates

-   In der Datenbank (Tabelle cas) ist der aktuelle Rel. der Datenbank
    verspeichert.

-   Im TC-Stand selbst werden keine Rel. Update Scripts bereitsgestellt

-   In der individuellen Ableitung muss man sich beim Hochziehen des
    Standes darum kümmern, dass auch die Rel. Update Scripts gemacht
    werden.

#### Wie setzte ich ein neues Notebook auf

1.  Installation MS-SQL-Server (Einplatzversion)

2.  Einrichten einer leeren TC-Datenbank

3.  Insert eines Datensatzes in der CAS-Tabelle

4.  Installation TradeControl

5.  Eintagen des CAS-Codes in der Registry

6.  Starten der Estbestückung für das neue Notebook

7.  Starten des Daten-Exportes für das neue Notebook

8.  Starten des TC-Empangs am Notebook

    a.  macht auch evt. DB-Updates

Notwendige Änderungen im TC oder pfu_fun

-   Sperren aller Änderungen wenn cas_cd belegt ist.

### Apollo Auftragsimport

Auswahlkriterien

-   laufende Nr. apollo_auf

Ablauf

-   Daten aus apollo_auf + apollo_auf_pos mit apollo_auf_pos.auf_nr = 0

    Pro Auftragskopf

-   Suchen eines Auftrages über die Apollo-ID Felder  
    Wenn nicht gefunden wird ein neuer Auftrag mit folgenden Werten aus
    apollo_auf angelegt

-   Firmennummer

-   Filialnummer

-   Usercode (Sachbearbeiter der eigenen Firma)

-   Auftragsdatum = erf_dat

-   Kundencode

-   Auftragsart

-   Lieferadresse

-   Ist die lief_adr_snr > 0, so werden die Daten dieser Adresse
    > verwendet, ansonsten die Datenfelder (name1 -- ort) aus apollo_auf

-   Bestellnummer Kunde

-   Bestelldatum Kunden

-   Kunden-Sachbearbeitercode

-   Wenn Einzrelchnung_jn = "j"

-   Solo_jn wird auf "j" gesetzt

-   vkrech_kz wird auf "a" gesetzt wenn nicht in (a, l, lr oder r)

-   Teillieferung erlaubt

-   Lieferdatum (wenn belegt)

-   Zahlungskonditionen (Skonto 1 -- Nettotage)

-   Kopfrabatte

-   Währung

-   inkl. Ust

-   AB an E-Mail als Kommunikationsnummer

-   Apollo-UUID

-   Apollo-Auftrags-ID

-   Ist der Belegtext ausgefüllt wird dieser als Kopftext mit Druck auf
    > allen Belegen übernommen

-   Ist der Interne Text ausgefüllt wird dieser als Kopftext mit Druck
    > nur am Kommissionsschein übernommen

-   Event für Übersteuerungen aufrufen

-   Kopf speichern

-   Im Fehlerfall Update err_txt und auf_nr auf -1

-   Neue Auftragspostion erstellen

-   Firmennummer

-   Aufragsnummer lt. oben erstelltem bzw. gefindenen Auftrag

-   Zuordnung Offert (abruf_ein_auf_nr, abruf_auf_pos_nr)

-   Ist offert_pos_snr belegt, so werden die Daten aus apollo_auf_pos
    > mit pos_snr = aktuelle offert_pos_snr ermittelt.

-   Ist archiv_offert_nr und archiv_offert_pos_nr belegt, so werden
    > diese verwendet.

-   Artitkelcode

-   Offene Menge (auf_best_mg)

-   Verkaufskonditionen -- nur wenn Preis manu_jn = "j"

-   vkpr -- vkrab5

-   preis_manu_jn

-   Faktor Kopfrabattfähig lt. vkrabk_jn

-   Positionsbelegetext als Zusätzliche Positionstexte mit Drucken auf
    > allen Belegen

-   Bei einem diversen Artikel muss vorher ein evt. schon vorhandener
    > Positionstext gelöscht werden

-   Interner Text als zusätzliche Positionstexte mit Drucken auf
    > Kommissionsschein

-   Evenvt für Übersteurung Position aufrufen

-   Speichern Position

-   Update auf_nr und auf_pos_nr in der apollo_auf_pos / bzw. Fehlertext
    und auf_nr auf -1

Wenn alle Positionen erledigt sind

-   Update apollo_auf.auf_nr

-   Wenn es einen Fehler gegeben hat Ausdruck Protokoll

-   Wenn kein Fehler war

-   wenn die E-Mail Adresse für die AB ausgefüllt war starten des AB
    > Versendens für den Auftrag

-   Wenn es eine Position mir freigegebener Menge > 0 gibt --
    > Einspoolen des Kommissionsscheindruckes

### TC. WebView

#### Besuchsbericht Tag

-   Gibt es für den User und den Tag noch keinen Eintrag und der letzte
    gebuchte Tag des Users hat Reisekosten-KZ Reisekosten und hat ein
    Fahrzeug mit Fahrtenbuch (keine Sonstigen Fahrzeuge) eingetragen und
    es gibt für diesen Tag keine Heimfahrt, so wird eine Messagebox
    "Heimfahrt des Vortags fehlt noch" ausgegeben und die Erfassung
    der Heimfahrt (Abschließen Button) für den Vortag aufgerufen. Danach
    wird der neue Tag begonnen.

-   Wenn für den aktuellen Tag noch kein Eintrag in castag vorhanden
    ist, starten wir mit der Neuerfassung

-   Änderungen sind nur möglich, solange die Reisekostenabrechnung noch
    nicht endgültig gedruckt wurde (castag.dru_job_snr = 0)

Datenfelder:

-   Personencode und Firmennumer werden konstant vom User definiert

-   Datum (Vorschlag Tagesdatum)

-   KFZ (d)

-   Vorschlag lt. letzten Tag

-   Es können nur KFZ verwendet werden die dem aktuellen oder keinem
    > User zugeordnet sind.

-   Abfahrts Zeit

-   Vorschlag Jetzt

-   Keine zwingende Eingabe bei Sonstigem KFZ

-   KM Stand Vortag (a)

-   Abfahrts KM Stand

-   Vorschlag = letzter KM Stand des Fahrzeugs

-   Kann nur auf einen größeren Wert geändert werden

-   Wenn schon nachfolgende Fahrtenbucheinträge vorhanden sind, dann nur
    > auf einen Wert < des Bis km Standes des nächsten
    > Fahrtenbuch-Eintrags. Damit wir der Privat-KM und der folgende
    > Fahrtenbucheinträg geändert.

-   Privat KM (a)

-   Differenz Abfahrts KM Stand zu KM Stand Vortag, nur wenn das
    > Fahrzeug ein durchgehendes Fahrtenbuch benötigt

-   Bei einer Differenz wird automatisch eine Privatfahrt erstellt

-   von_km = letzter KM Stand (Vortag)

-   bis_km = eingegebener Abfahrts KM Stand

-   von/bis_dat = Datum

-   von/bis_zeit = 0:00

-   privat_jn = \'j\'

-   start_ und ziel_ Adresse werden von der lezten Fahrt übernommen

-   fabu_kz = p

Erweiterte Daten:

-   Tages-KZ (d)

-   Nächtigung (c)

-   Text

Buttons

-   Besuche

-   Besuchsberichtserfassung

-   Fahrtenbuch

-   Reisekosten

-   Ende

-   Ruft das Fahrtenbuch für die Heimfahrt auf, wenn ein KFZ ausgewählt
    > ist

#### Besuchsbericht 

-   Startet in der Liste, wenn es für den User und den Tag bereits
    Kontakte gibt (das können auch geplante sein).

-   Änderungen sind möglich, solange der Endgültige Druck noch nicht
    erfolgt ist

Datenfelder:

-   Kundennummer

-   Suche über Kundennnummer / Kundenmtachcode möglich

-   Standardmäßig werden nur Kunden, die dem aktuellen User zugeordnet
    > sind angzeigt (lt. Default kundeprovgr_cd)

-   Kundenmatchcode (a)

-   Von KM Stand (a)

-   KM Stand

-   Eingabe nur bei Fahrzeugen

-   Muss größer als der letzte KM Stand des Fahrzeugs sein

-   Kann wenn das Fahrtenbuch schon erstellt wurde nur geändert werden,
    > wenn es der letzte KM Stand des Fahrzeugs ist

-   gefahrene KM (a)

-   KFZ (d)

-   Vorschlag lt. Tag. Der Vorschlag muss auch bei geplanten
    > Besuchsberichten, die ausgewählt wurden erfolgen.

-   Ist Fix "" wenn eine Besuchsart mit fabu_jn = "n" ausgewählt
    > wurde

-   Kann wenn das Fahrtenbuch schon erstellt wurde nur geändert werden,
    > wenn es der letzte KM Stand des Fahrzeugs ist

-   Es können nur KFZ verwendet werden, die dem aktuellen oder keinem
    > User zugeordnet sind.

-   Besuchsart (d) (= Kontaktgruppe)

-   Betreff

-   Von Zeit Kundentermin (Vorschlag = aktuelle Uhrzeit)

-   Bis Zeit

-   Ansprechpartner (d)

-   Panel Zusatzdaten

-   Datum nächster Besuch

-   Nur wenn lt. Kontaktgruppe das letzte Kontaktdatum aktualisiert
    > werden soll

-   Vorschlag = aktuelles Datum + Besuchsintervall in Wochen lt.
    > Kundenstamm

-   Wird am Kunden als Datum nächster Besuch eingetragen.

-   Name 1

-   Name 2

-   Straße

-   Land (d)

-   PLZ

-   Ort

-   Zusatztext für Fahrtenbuch

Buttons

-   Weiter

-   Wenn die Bis-Zeit noch nicht definiert ist, so wird sie jetzt mit
    > der aktuellen Uhrzeit belegt (wenn das Datum der aktuelle Tag
    > ist).

-   Speichert den Besuchsbericht und eventuell den Fahrtenbucheintrag.

-   Update KM-Stand am KFZ und letzter und nächster Besuchstermin am
    > Kunden

-   Es wird sofort ein neuer Besuchsbericht begonnen

-   Texte

-   Liste

EndeTexte

-   Wenn bereits Texte vorhanden sind wird eine Liste der Texte
    angezeint, ist noch kein Text vorhanden wird sofort eine
    Neuerfassung begonnen.

Liste:

-   Anpsprechpartner

-   Text Gruppe

-   Text

Buttons:

-   Auswahl

-   Neu

-   Zurück

Text Detail:

-   Textgruppe (d)

-   Text

-   Ansprechpartner (d)

-   Vorschlag vom Besuchsbericht

Buttons:

-   Fertig

-   Liste

-   Zurück

Liste

-   Von Zeit

-   Bis Zeit

-   Kundenmatchcode

-   Besuchsart

-   Es kann eine Position zur Änderung ausgewählt werden

    Button:

-   Neu

-   Ende

Kundenauswahl

Selektionskriterien:

-   Kundenprovisionsgruppe (Default lt. User, kann ausgeschaltet werden)

-   PLZ

-   Matchcode

Liste (Cards):

-   Kundennummer

-   Matchcode

-   PLZ

-   Ort

-   Straße

#### Fahrtenbuch

Datenfelder

-   KFZ (d)

-   Vorschlag lt. Tag

-   Es können nur KFZ verwendet werden, die dem aktuellen oder keinem
    > User zugeordnet sind

-   Von KM

-   Vorschlag letzter KM-Stand (lt. letzten Buchung am Fahrzeug --
    > letzes Datum)

-   Kann gändert werden, wenn lt. KFZ erlaubt (keine KM-Stand Prüfung)

-   Bis km

-   Muss > von_km sein

-   Bei Eingabe wird gefahrene km berechnet

-   Kann bei Änderung maximal auf den Bis-KM der nächsten Buchung
    > geändert werden

-   Gefahrene km (a)

-   Von Zeit

-   Vorschlag größeres aus Bis Zeit letzter Besuchsbericht oder
    > Fahrtenbuch am Tag

-   Bis Zeit

-   Zusatztext

-   Zweck (d)

-   Bei einer Heimfahrt wird die Ziel Adresse mit der WerbeAdresse des
    > Sachbearbeiters belegt

-   Bei einer Privatfahrt wird die Start Adresse als Ziel Adresse
    > vorgeschlagen

-   Bei einer Fahrt ins Büro wird die Adresse der Filiale vorgeschlagen
    > (Filiale des Defaultlagers des Fahrers).

-   Start / Ziel

-   Als Start Adresse wird die letzte Ziel-Adresse vorgeschlagen

-   KundeNr (f)

-   Kundenmatchcode (a)

-   Name 1

-   Name 2

-   Strasse

-   Land

-   Plz

-   Darf nicht blank sein

-   Ort

Heimfahrt:

-   Wenn es aus dem Tag über den Button Ende aufgerufen wird, wird hier
    die Heimfahrt vorgeschlagen.

-   Zweck = Heimfahrt

Buttons

-   Weiter

-   Wenn die Bis-Zeit noch nicht definiert ist, so wird sie jetzt mit
    > der aktuellen Uhrzeit belegt (wenn das Datum der aktuelle Tag
    > ist).

-   Speichert den Fahrtenbucheintrag.

-   Update KM-Stand am KFZ

-   Es wird sofort ein neuerFahrtenbucheintrag erstellt

-   Texte

-   Liste

-   Ende

Liste

-   Von Zeit

-   Bis Zeit

-   Von km

-   Bis km

-   Von PLZ

-   Bis PLZ

    Button:

-   Neu

-   Ende

Für die Nachbearbeitung im Büro muss es eine Desktop Version geben, in
der auch der Fahrer eingegeben werden kann.

Desktop Version

Für Korrekturen gibt es eine Desktop Version.

-   Es muss immer gewährleistet sein, dass innerhalb eines Fahrzeugs mit
    KM-Stand Prüfung die Reihenfolge lt. KM-Stand mit der Reihenfolge
    lt. Abfahrtszeit übereinstimmt.

-   Es muss möglich sein im Nachhinein z,B eine Privatfahrt auf eine
    Heimfahrt des Vortages zu ändern.

-   Es muss möglich sein eine Privitfahr auf Heimfahrt + Privatfahrt
    aufzuteilen

#### Reisekosten

-   Bei Aufruf aus Besuchsbericht Tag wird sofort die Liste mit den
    Reisekosten des Users/Tags angezeigt

Liste

-   Reisekosten-KZ

-   Wert

-   Text

-   Bild Vorhanden

Buttons:

-   Neu

-   Zurück

-   Auswahl

Datenfelder bei Neu/Ändern

-   Datum (a)

-   Reisekosten-KZ (d)

-   Spesen Wert

-   Text

-   Foto

Buttons

-   Abbrechen

-   Fertig

#### Kundenabfrage

Verknüpfungen:

-   Umsatzabfrage

.....

##### Tab Sonderkonditionen

View AG-Konditionen

-   Wird sofort retrieved

-   Liste über alle aktuellen und Zukünftigen Arikelgruppen Konditionen
    des Kunden oder dessen Kundengruppen

-   K / G (= Kunde oder Gruppe)

-   Artikelverkaufskonditionsgruppenmatchcode

-   Ab-Datum

-   Bis-Datum

-   Preisliste

-   Rabatt 1

-   Rabatt 2

View Artikelkonditionen

-   Retrieve muss manuell ausgelöst werden

-   Liste über alle aktuellen und zukünftigen Artikel Konditionen des
    Kunden oder dessen Kundengruppen

-   K / G (= Kunde oder Gruppe)

-   Artikelnummer

-   Artikelmatchcode

-   Ab-Datum

-   Bis-Datum

-   Ab-Menge

-   Preisliste

-   Verkaufspreis

-   Rabatt 1

-   Rabatt 2

View Preisfindung

-   Detailmaske zur Abfrage von Artikelpreisen

-   Eingabe Artikelnummer (Schnellsuche)

-   Artikelmachcode (a)

-   Verfügbarer Lagerstand (a)

-   Disponiebler Lagerstand -- offene Auftragsmenge

-   Verkaufspreis (a)

-   Währung (a)

-   Preiseinheitsmenge (a)

-   Mengeneinheit (a)

-   Rabatt 1 (a)

-   Rabatt 2 (a)

-   Nettopreis (a)

-   Naturalrabatt (a)

-   Nächste Ab Menge (a)

-   Preisfindungsdatum

-   Vorschlag = Today

-   Preisfindungsmenge

-   Vorschlag = 1

#### Umsatzabfrage

Register BenutzerPerioden

-   Hier können die zu verwendenden Von/Bis Periode für den aktuellen
    Benutzer eingestellt werden

-   Von Monat Periode A

-   Bis Monat Periode A

-   Von Monat Periode B

-   Bis Monat Periode B

Register Umsätze

Suchkriterien:

-   Stamm Vertrager (Vorschlag = nur eigene Kunden)

-   Kunde

-   Kundenverkaufskonditionsgruppe

-   Artikel

-   Artikelverkaufskonditionsgruppe

Liste über:

-   Kunde (Matchcode + Nummer)

-   Stamm Vertreter

-   Beleg Vertreter

-   Kundenverkaufskonditionsgruppe

-   Artikel

-   Verkaufseinheitscode

-   Artikelverkaufskonditionsgruppe

-   Umsatzmenge A

-   Umsatzwert A

-   Wareneinsatz A

-   DB Absolut A

-   DB % A

-   Aufschl. % A

-   UmsAbw% A zu B

-   Umsatzwert B

-   Umsatzmenge B

-   Wareneinstz B

-   DB Absolut B

-   DB % B

-   Auschl. % B

Grupierung ist aktiviert

-   Kunde

-   Artikel

#### Auftragserfassung

##### Auftragskopf

-   Kann nicht mehr geändert oder gelöscht werden, wenn der Zustand
    bereits auf Übertragen ist

-   Firma/Fililale

-   Ist im Normalfall vom User Konstant vorgegeben

-   Kunde

-   Schnellsuche mit Default Einstellung nur Kunden des Vertreters

-   Evt. durch Aufruf aus Kunde oder Besuchtsbericht konstant

-   Kundenmatchcode (a)

-   Status (d)

-   Kann nicht manuell auf Übertragen geändert werden

-   Auftragsart (d)

-   Kundenbestellnummer

-   Kundenbestelldatum

-   Vorschlagswert = aktuelles Datum

-   Person (d)

-   Auswahl aus Personen des Kunden, Es kann aber auch die Dummy Person
    > verwendet werden.

-   AB an Email

-   Freie Eingabe und Auswahl aus allen E-Mail-Adressen des Kunden
    > möglich

-   Kopfrabatt

-   Auftragswert (a)

Panel Lieferdaten

-   Liefertermin

-   Versandart (d)

-   Lieferadresse Manuell (c)

-   Lieferadresse

-   Kann nur bei manuell eingegeben werden

-   Belegtext

-   Interner Text

##### Auftragsposition

-   Berechtigung wie bei Auftraskopf

-   Artikel

-   Schnellsuche über Artikelnummer, EAN, Kunden-Artikelnummer und
    > Artikelmatchcode möglich

-   Artikelmatchcode (a)

-   Menge

-   Mengeneinheit (a)

-   Verkaufspreis manuell (c)

-   Verkaufspreis

-   Rabatt 1

-   Rabatt 2

-   Positionsbetrag

-   Verfügbare Menge (a)

-   Bestellte Menge (a)

-   Menge von offenen Aufträgen (dieser Kunde/Artikel).

-   Belegtext

-   Interner Text

## Versand

### Versandauftrag

-   Ist noch unvollständig -- wird laufend ergänzt

Detail:

-   Bruttogewicht

-   Anzahl Pakete

-   Nur eingebbar bei Neuanlage und wenn Teilbereich Pakete aktiv ist

-   Bei Eingabe werden im Teilbereich Pakete vorhandene Zeilen gelöscht
    > und so viele Paktezeilen mit dem Bruttogewicht / Anzahl Pakete
    > angelegt.

### Speditionsetikett

Auswahlkriterien:

-   Versandauftragsnummer (p)

Auswahl der Daten

-   Es wird eine Etikett pro Paket [vs_auf_paket] gedruckt

-   Das Vorlagenfile wird dabei auch als Applikationskennzeichen für die
    Druckerzuordnung mitgegeben

Folgende Daten werden bei Etikettetyp "sped" an den Etikettendruck
übergeben:

-   Vorlagenfile lt. Versandart

-   (0) Anzahl zu Druckender Etiketten im Format "0000"  
    Im Standard wird hier fix 1 ausgegeben

-   (1) Absender Name1

-   (2) Absender Name2

-   (3) Absender Straße

-   (4) Absender Land+PLZ+Ort

-   (5) Empfänger Name1

-   (6) Empfänger Name2

-   (7) Empfänger Name3

-   (8) Empfänger Straße

-   (9) Empfänger Land+PLZ+Ort

-   (10) Absenden Name3

-   (11) Versandart-Matchcode

-   (12) Bruttogewicht in kg (als Text mit 2 Nachkommastellen)

-   (13) Colli-Nummer (laufende Nr. des Collis innerhalb des
    Versandauftrags)

-   (14) Beleg-Nummern

-   Wenn es mehrere Belege gibt, werden alle Belegnummern zu einem
    > String zusammengestellt.  
    > Es darf dabei die maximale Länge der Belegnummer für den
    > Etikettendruck nicht überschritten werden.

-   (15) "00" + Paketnummer

-   (16) Anzahl der Collis

-   (17) Verapckungsart Etikettentext

-   (18) Kundennummer

-   (19) Sendungsnummer Versandauftrag (z.B. Ladenummer bei GW)

-   (20) Versanddatum im Format DD.MM.YYYY

-   (21) Text Bestellnummer Kunde

-   Alle Kundenbestellnummern der Abwicklungsaufträge lt. vs_auf_beleg.
    > Begrenzung der Zeichlänge wie bei Beleg-Nummern

### Speditionsliste

Auswahlkriterien

-   Firma (p)

-   Versandort (p)

-   Versandart (p)

-   Versandatum

-   Speditionslistennummer (o)

-   0 = Noch nicht gedruckten (= Default)

-   > 0 = Nachdruck einer Speditionsliste

-   Druck endgütlig j/n (p)

-   Wird nur bei Speditionslistennumer 0 angewendet

-   Beliebige Kriterien lt. vs_auf

-   Anzahl Drucke (o)

-   Default = 1

Auswahl der Daten:

-   Versandaufträge lt. Auswahlkriterien

-   Bei der Varinte mit Speditionslistennummer 0 muss eine neue
    Speditionslistennummer vergeben werden, wenn der endgültige Druck
    verwendet wurde.

Listbild: [versand\\spedlist.docx](versand/spedlist.docx)

Folgende Daten werden angedruckt:

Im Kopf:

-   Speditionslistennummer

-   Druckdatum+Zeit

-   Seitennummer + Seitenanzahl

-   Unsere Kundennummer beim Spediteur

-   Versandartenmatchcode

-   Adresse des Versandortes

-   Sendungsnummer -- wenn bei allen Positionen gleich (min = max)

Pro Versandauftrag:

-   Pro Beleg

-   Belegnummer

-   Belegdatum

-   PLZ

-   Lieferadresse

-   Telefonnummer

-   Kundennummer

-   Sendungsnummer

-   Pro Verpackunsart (aus Paketdaten)

-   Anzahl

-   Verpackungsartencode

-   Gewicht in Kg

-   Pro Paket mit Paket-Sendungsnummer

-   Paket Sendunsnummer

-   Anz. Colli Summe Versandaufrag

-   Bruttogewicht Summe Versandauftrag

Summblock pro Verpackungsart

-   Anzahl Colli

-   Verpackungsartencode

-   Summe Gewicht

Endsumme

-   Anzahl Colli

-   Summe Gewicht

## TradeControl Scan 

###  Allgemein

-   Eigene Library „tc_scan", um bei Bedarf einfach in andere Pakete zu
    > übernehmen

-   Tabelle wird für Externe Belege manuell befüllt

-   Tabelle wird wird für eigenerzeugte Belege automatisch geschrieben

### Erfassung Tradecontrol Scan

####  Suchkriterien

-   Barcode

-   Scangruppe (t)

-   Belegnummer

-   Belegdatum

-   Tags

-   Dynamischer Join zu tcscan_tags

-   Wert des Tags

-   Dynamischer Join zu tcscan_tags

-   Scantext

-   Dynamischer Join zu tcscan_txt

-   Adressmatchcode

-   Dokument vorhanden

-   Kundennummer

-   Dynamischer Join zu kunde

-   Lieferantennummer

-   Dynamischer Join zu Lieferant

-   Debitorennummer

-   Dynamischer Join zu Debitor

####  Register Liste

-   Barcode

-   Firma

-   Belegnummer

-   Belegdatum

-   Scangruppe Code

-   Scangruppe Bezeichnung

-   Dokument vorhanden (cb)

-   1. Textzeile aus tcscan_txt

-   Adressmatchcode

####  Register Detail

-   Löschen nur erlaubt, wenn dokument_vorh_jn = nein und
    > tcscangrp.darf_manuell_jn = Ja

-   Neuanlage nur erlaubt, wenn lt. pfu_param (archivart_kz)
    > freigeschaltet

-   Barcode

-   Nur bei Neuanlage eingebbar

-   Kann leer bleiben

-   Firma

-   Belegnummer

-   Beim Öffnen wird der zugehörige Beleg geöffnet

-   Belegdatum

-   Scangruppe (dddw)

-   Nur Scangruppen mit darf_manuell_jn = „j" dürfen händisch erfasst
    > werden

-   Solche mit „nein" werden aus dem Drop Down ausgeblendet

-   Wenn Tag-Vorschlage vorhanden, werden diese gleich aufgebaut

-   AdressauswahlDDDW

-   Adressmatchcode (Anzeige)

-   Dokument vorhanden (Anzeige)

####  Teilbereich „Tags"

-   Erfassung im Grid

-   Eingabe Tag

-   Eingabe Wert zu Tag. Collation in der Datenbank ist **COLLATION
    > Latin1_General_CI_AI,** damit ist bei der Suche Gross/Klein/Umlaut
    > irrelevant

####  Teilbereich „Texte"

-   Erfassung im Grid

-   Erfassung Texte zu Scan. Collation in der Datenbank ist **COLLATION
    > Latin1_General_CI_AI,** damit ist bei der Suche Gross/Klein/Umlaut
    > irrelevant

####  Register „PDF"

-   Anzeige des Dokuments so wie in pfu_job_druck

-   Ermittlung der Relevanten Daten wie Filename... aus pfu_job_Druck

-   Key dazu ist in tcscan mitgespeichert

#### Verzweigungsbutton „Dokumente"

-   Konstantsetzen beleg_nr_kz

-   Konstantsetzen beleg_nr

-   Öffnen pfu_job_druck

###  Schreiben der Tabelle tcscan

-   Global Function zum Schreiben von tcscan

-   Wird in gf_writearchiv und gf_updatearchiv aufgerufen, wenn
    > gf_initapplenv.ib_ha_tscan = true

-   Nur Insert, kein Update!

-   Auch in gf_updatearchiv wird nur geschrieben

-   Funktion erhält beleg_nr_kz und ermittelt sich tcscangrp_cd (Top 1)

-   Kein Insert wenn nichts gefunden

###  Import der gescannten Dokumente

-   Dokumente liegen in einem Verzeichnis lt. pfu_param

-   Barcode ist der Filename

-   Sofortiger Programmabbruch wenn TcScan lt. pfu_param nicht aktiv

-   Reorg des Feldes tcscan.dokument_vorh_jn

-   Ablauf

-   Durchgehen Scanverzeichnis, pro File:

-   Auslesen Filename excl. Dateiendung, dies ist der Barcode

-   Ermittlung des Datensatzes in Tcscan

-   Wenn nicht gefunden, File ignorieren und weiter mit nächstem File

-   Ab_markieren auf true, damit ggf. ein WFO aufgeht

-   Die Files, die hier übrigbleiben, sind dann solche, wo der tcscan
    > eintrag fehlt

-   Wenn gefunden:

-   Ermitteln ausdruckart lt. Scangruppe

-   Beginn Transaktion

-   Anlage Dokument (pfu_job_druck) (So wie bei Import Jetscan)

-   Update tcscan, dokument_vorh_jn = ja

-   Event für Updates aufrufen

-   Im TC Standard wird hier bei einer Eingangsrechnung das erech_pdf_kz
    > auf "v" upgedatet.

-   Commit Transaktion

-   File löschen

## Sonstige

### Währungsumstellung Lieferant

#### Auswahldialog

-   Firma

-   Lieferantennummer (f)

-   Denominationskennzeichen (w)

-   Ja

-   Nein

-   Auf-Währung (p)

-   Bestellungen umrechnen (p)

-   Ja

-   Nein

-   Bestellnummer

-   Warenzugänge umrechnen (p)

-   Ja

-   Nein

-   Warenzugangsnummer

-   Mindestbestellwert Lieferant umrechnen (p)

-   Ja

-   Nein

Auswahl der Daten

-   Artikeleinkaufspreise deren Währung ungleich der Auf-Währung sind

-   Artikeleinkaufsprojektpreise deren Währung ungleich der Auf-Währung
    sind

-   unerledigte Bestellungen (Bestellungen mit zumindest noch einer
    nicht gelieferten Positione)

-   erfasste und noch nicht (auch nicht teilweise) verrechnete
    Eingangslieferscheine

Ablauf

-   lesen der ausgewählten Lieferanten

-   Pro Lieferant

-   sperren Lieferant

-   umrechnen Mindestbestellwert

-   Pro Lieferant und Artikel

-   sperren Lieferant

-   umrechnen der Einkaufspreise

-   umrechnen der Projektpreise

-   Pro Lieferant und Bestellung

-   sperren Lieferant

-   umsetzen der Bestellwährung

-   umrechnen der Bestellpreise aller Positionen

-   Pro Lieferant und Eingangslieferschein

-   sperren Lieferant

-   umsetzen der Lieferscheinwährung

-   umrechnen der Lieferscheinpreise (Soll- und Ist) aller Positionen

-   Endemeldung des Batchlaufes

    **Anmerkung**

    Dieses Programm wird auch durch Änderung der Lieferantenwährung im
    Lieferantenfenster für den aktuellen Lieferanten automatisch
    gestartet. In diesem Fall werden jedoch nur die
    Artikeleinkaufspreise sowie die Projektpreise umgerechnet.
    Bestellungen, Eingangslieferscheine sowie der Mindestbestellwert des
    Lieferanten bleiben unverändert.

### Währungsumstellung Debitor

#### Auswahldialog

Auswahl der Daten

-   alle Aufträge mit Währung <> Fibu-Debitorenwährung

-   alle noch nicht fakturierten Lieferscheine mit Rechnungsnummer = 0

Ablauf

-   lesen der ausgewählten Debitoren

-   Pro Auftrag

-   sperren Debitor

-   update Auftrag

-   Währungskennzeichen

-   update Auftragspositionen (Abwicklung)

-   Verkaufspreis

-   update Verkaufslieferscheine

-   Pro nicht fakturiertem Lieferschein

-   update Verkaufslieferschein

-   Währungskennzeichen

-   update Verkaufslieferscheinposition

-   Verkaufspreis

-   Positionsbetrag inkl. USt

-   Positionsbetrag exkl. Ust

-   Endemeldung des Batchlaufes

### Auftragsrückstandsauflösung

#### Auswahldialog

-   Firmennummer (p)

-   BisLieferdatum (p)

-   freigegebene Auftragspositionen berücksichtigen (p)

-   Ja

-   Nein

-   Auftragsnummer Abwicklung

-   Artikelnummer (f)

-   Kundennummer (f)

-   Lagercode (f)

-   Auftragszustandskennzeichen (w)

-   Kreditlimitprüfung (p)

-   Ja

-   Nein

Auswahl der Daten

-   Aufträge deren Lieferdatum <= der Eingabe ist

-   offene Auftragspositionen, ohne Kommissionsscheinzuordnung

-   Bei Lagerführung auf Lagerort- bzw. Chargen- oder Geräteebene darf
    noch keine Zuordnung in der Tabelle auf_pos_sub erfolgt sein

Ablauf

-   Verarbeitung der Auftragspositionen sortiert nach Artikel, Priorität
    Kunde, Lieferdatum, Auftragsnummer

-   Aufruf des Freigabemoduls für die ausgewählten Auftragspositionen

-   Je Artikel:

-   Locken aller beteiligten Debitoren

-   Locken des Artikels

-   Verarbeiten aller Auftragspositionen

-   Ermittlung der Freigabemenge je Auftragsposition

-   Neuberechnung des freigegebenen Auftragswertes in Tabelle debitor
    > und Kreditlimitprüfung

-   ist das Kreditlimit überschritten, wird die Position nicht
    > freigegeben und bei der nächsten Auftragsposition fortgesetzt

-   Freigabe der Position

-   Speichern der Lagerdaten des Artikels

-   Verarbeitung der offenen Produktionsaufträge sortiert nach Priorität
    Kunde, Lieferdatum, Auftragsnummer

-   Aufruf der Auftragsbearbeitung und Freigabe

-   Endemeldung des Batchlaufes

### Preisreorganisation

#### Auswahldialog

-   Firma (p)

-   Verarbeitungskennzeichen (p)

-   Einkauf (e)

-   Verkauf (v)

-   Einkauf und Verkauf (ev)

-   BisGültigkeitsdatum (p)

-   Aktionskennzeichen Einkauf

-   wird nur ausgewertet, wenn Einkauf reorganisiert wird

-   Projektpreise löschen

-   Ja

-   Nein

-   wird nur ausgewertet, wenn Einkauf reorganisiert wird

-   Verkaufskonditionsart

-   wird nur ausgewertet, wenn Verkauf reorganisiert wird

Auswahl der Daten

-   Einkaufs- und Verkaufspreise und mit "BisDatum" kleiner oder
    gleich der Auswahl

-   Verkaufskonditionsarten lt. Auswahl

-   Einkaufspreise bzw. Projektpreise lt. Auswahl

Ablauf

-   Verkauf

-   lesen der ausgewählten Verkaufskonditionen [vkkond, vkkond_preis]

-   pro Verkaufskondition [vkkond.vkkond_snr]

-   sperren vkkond

-   löschen der alten Preissätze

-   löschen vkkond wenn kein Preissatz mehr vorhanden ist und kein
    > Artikel diese Kondition hat [artik.o_artikvkkond_snr]

-   Einkauf

-   lesen der Einkaufsdaten [artik_lief, artik_lief_ekpr]

-   pro Einkaufssatz [artik_lief]

-   sperren artik_lief

-   löschen der alten Preissätze [artik_lief_ekpr]

-   EinkaufProjektpreise

-   lesen der Einkaufsdaten [artik_lief, artik_lief_projpr]

-   pro Einkaufssatz [artik_lief]

-   sperren artik_lief

-   löschen der alten Preissätze [artik_lief_projpr]

### UID-Prüfung Batchlauf

#### Auswahldialog

-   Firma (p)

-   Kontoart (pw)

-   "d" Debitor

-   "k" Kreditor

-   "dk" Debitoren und Kreditoren

Auswahl der Daten

-   Debitorensätze [debitor] bzw. Kreditorensätze [kreditor] für die
    gilt

-   [kod_uid_chk_nr in ("1", "2")]

-   [deb_\|kred_uid_job_snr <> {aktuelle}]

Ablauf

-   öffnen Debitorenfenster

-   öffnen Kreditorenfenster

-   lesen Datensätze

-   pro Datensatz

-   Beginn Transaktion

-   Besorgen Debitor im Debitorfenster

-   Besorgen Kreditor im Kreditorfenster

-   Setzen JobNummer letzte Prüfung = {aktuelle}

-   Prüfen Wert UID-Nummer

-   wenn Blank und Status = 2

-   Prüf-Status = "0"

-   Prüfdatum={Tagesdatum}

-   Auslösen UID-Prüfung Batch

-   siehe "Online UID-Prüfung"

-   Ende Transaktion

-   Reseten Window

-   Endemeldung

### Löschen Bewegungsdaten

#### Auswahldialog

-   Firma (p)

-   Verarbeitungskennzeichen (p)

-   Einkauf (e)

-   Verkauf (v)

-   Lagerbuchungen (l)

-   Kassa (k)

-   Einkauf, Verkauf, Lagerbuchungen und Kassa (evlk)

-   Bis Belegdatum (p)

Ablauf

Prüfung Mindestbehaltedauer

-   Bestimmung höchstes im System mögliches Löschdatum {MaxLöschDatum}

-   ist immer ein Jahresletzter, also 31.12.JJJJ

-   JJJJ = Jahr lt. Systemdatum - [param.bewdat_mindestjahr_anz] - 1

-   Bsp: Systemdatum 15.10.2018 höchstes Löschdatum 31.12.2010 unter der
    > Annahme, dass die gesetzliche Mindestbehaltedauer von 7 Jahren als
    > Parameter gesetzt ist

-   wenn Daten eines Jahres in die Mindestbehaltedauer fallen, wird das
    > ganze Jahr behalten

-   Ausgabe Fehlermeldung "Auswahldatum ist größer als das maximal
    > mögliche Löschdatum: {MaxLöschDatum}" und Programmende

-   wenn BisBelegDatum > MaxLöschDatum

-   löschen [belegloe_temp]

-   eigenes Event

-   aktueller Job

-   eigene Transaktion

-   Abwicklung Verkauf

-   löschen [belegloe_temp]

-   Abwicklung Einkauf

-   löschen [belegloe_temp]

-   Abwicklung Lager

-   löschen [belegloe_temp]

-   Abwicklung Kassa

-   löschen [belegloe_temp]

#### Verkauf

-   lesen Rechnungen [vrech] into [belegloe_temp]

-   vrech_nr > 0

-   vrech_dat <= Auswahldatum

-   belegtab_kz = "vrech"

-   fa_nr = ?

-   eigene Transaktion

-   lesen Lieferscheine [vlfs] into [belegloe_temp]

-   jene, die zu den vorgemerkten Rechnungen gehören

-   vlfs_pos joins [belegloe_temp where job_snr = ? and belegtab_kz =
    > "vrech" and vlfs.vrech_nr = belegloe_temp.beleg_nr and
    > vlfs.fa_nr = ?]

-   belegtab_kz = "vlfs"

-   eigene Transaktion

-   Löschen vorgemerkte Lieferscheine

-   eigenes Event

-   Beginn Transaktion

-   Aufruf Event für Ableitung

-   update [geraet_vk]

-   where exists [from belegloe_temp where belegtab_kz = "vlfs" and
    > vlfs_key]

-   vlfs_nr = 0

-   ein_auf_nr = 0

-   auf_pos_nr = 0

-   löschen [vlfs_pos_gerstat, vlfs_pos_statkorr, vlfs_pos_wu,
    > vlfs_pos]

-   where exists [belegloe_temp where belegtab_kz = "vlfs" and
    > vlfs_key]

-   Aufruf Event für Ableitung

-   löschen [vlfs_prod, s_vlfs_txt, vlfs]

-   where exists [from belegloe_temp where belegtab_kz = "vlfs" and
    > vlfs_key]

-   Ende Transaktion

-   Löschen vorgemerkte Rechnungen

-   Beginn Transaktion

-   Aufruf Event für Ableitung

-   update [ka_bel_vrech]

-   where exists [belegloe_temp where belegtab_kz = "vrech" and
    > vrech_nr = beleg_nr and fa_nr = ?]

-   vrech_nr = 0

-   löschen [vrech_kont, vrech_ust, vrech]

-   where exists [belegloe_temp where belegtab_kz = "vrech" and
    > vrech_nr = beleg_nr and fa_nr = ?]

-   Ende Transaktion

-   löschen [belegloe_temp]

-   aktueller Job

-   eigene Transaktion

-   lesen Lieferscheine ohne Faktura [vlfs] into [belegloe_temp]

-   vlfs.vrech_nr < 0

-   vlfs_dat <= Auswahldatum

-   belegtab_kz = "vlfs"

-   eigene Transkation

-   Löschen vorgemerkte Lieferscheine

-   Event w.o.

-   löschen [belegloe_temp]

-   aktueller Job

-   eigene Transaktion

-   lesen Auftragspositionen [auf, auf_pos, outer vlfs_pos] into
    [belegloe_temp]

-   erl_ein_auf_nr = ein_auf_nr

-   vlfs_pos.lief_mg = NULL

-   auf.auf_dat <= Auswahldatum

-   belegtab_kz = "auf_pos"

-   Löschen vorgemerkte Auftragspositionen

-   Beginn Transaktion

-   Aufruf Event für Ableitung

-   update [(set_)auf_pos]

-   where exists [belegloe_temp where belegtab_kz = "auf_pos" and
    > auf_pos_key and set_pos_nr <> auf_pos_nr]

-   set_pos_nr = auf_pos_nr

-   update [(abruf_)auf_pos]

-   Abrufpositionen, die nicht gelöscht werden und die vorgemerkten
    > referenzieren

-   where exists [belegloe_temp where belegtab_kz = "auf_pos" and
    > fa_nr = ? and abruf_ein_auf_nr = belegloe_temp.beleg_nr and
    > abruf_auf_pos_nr = belegloe_temp.beleg_pos_nr and
    > (abruf_ein_auf_nr <> ein_auf_nr OR abruf_auf_pos_nr <>
    > auf_pos_nr)]

-   abruf_ein_auf_nr = ein_auf_nr

-   abruf_auf_pos_nr = auf_pos_nr

-   update [best_pos]

-   Bestellpositionen, welche die vorgemerkten Auftragspositionen
    > referenzieren

-   where exists [belegloe_temp, best_pos where belegtab_kz =
    > "auf_pos" and auf_pos_key and zuo_ein_auf_nr =
    > belegloe_temp.beleg_nr and zuo_auf_pos_nr =
    > belegloe_temp.beleg_pos_nr]

-   zuo_ein_auf_nr = 0

-   zuo_auf_pos_nr = 0

-   Ende Transaktion

-   Beginn Transaktion

-   löschen [auf_pos_best, auf_pos_set, auf_pos_sub, auf_pos_txt,
    > auf_pos_komm, auf_pos]

-   where exists [belegloe_temp where belegtab_kz = "auf_pos" and
    > auf_pos_key]

-   Ende Transaktion

-   lesen Aufträge [auf] into [belegloe_temp]

-   (auf.auf_dat <= today - 365))

-   where not exists [ab_auf_pos] and not exists [ein_auf_pos] and
    > not exists [vlfs]

-   belegtab_kz = "auf "

-   Löschen vorgemerkte Aufträge

-   Beginn Transaktion

-   Aufruf Event für Ableitung

-   update [cas_kont]

-   where exists [belegloe_temp where belegtab_kz = "auf" and
    > auf_key]

-   auf_nr = 0

-   löschen [auf_komm, auf_prod_sub, auf_prod, auf_txt, auf_ueb_txt,
    > s_auf_txt, s_auf, s_vlfs_txt, vlfs, auf]

-   where exists [belegloe_temp where belegtab_kz = "auf" and
    > auf_key]

-   Ende Transaktion

-   Löschen Apollo-Aufträge

-   Beginn Transaktion

-   apollo_auf_pos where apollo.erf_dat <= Auswahldatum

-   Apollo_auf where not exists [apollo_auf_pos]

-   Ende Transaktion

#### Einkauf

-   lesen Rechnungen [erech] into [belegloe_temp]

-   erech_nr > 0

-   erech_dat <= Auswahldatum

-   erech_beleg_dat <= Auswahldatum

-   fa_nr = ?

-   belegtab_kz = "erech"

-   eigene Transaktion

-   lesen Einkaufslieferscheinpositionen [elfs_pos] into
    [belegloe_temp]

-   jene, die zu den vorgemerkten Rechnungen gehören

-   elfs_pos joins [belegloe_temp where job_snr = ? and belegtab_kz =
    > "erech" and elfs_pos.erech_nr = belegloe_temp.beleg_snr and
    > elfs_pos.fa_nr = ?]

-   belegtab_kz = "elfs_pos"

-   eigene Transaktion

-   Löschen vorgemerkte Lieferscheine

-   eigenes Event

-   Beginn Transaktion

-   Aufruf Event für Ableitung

-   löschen [elfs_pos_txt, elfs_pos_best, geraet_ek, elfs_pos]

-   where exists [belegloe_temp where belegtab_kz = "elfs_pos" and
    > elfs_pos_key]

-   Aufruf Event für Ableitung

-   löschen [elfs_txt, erech_elfs, elfs]

-   where exists [from belegloe_temp where belegtab_kz = "elfs_pos"
    > and elfs_key]  
    > and not exists [elfs_pos where elfs_key]

-   Ende Transaktion

-   Löschen vorgemerkte Rechnungen

-   Beginn Transaktion

-   Aufruf Event für Ableitung

-   löschen [erech_zuab, erech_ust, erech_txt, erech_kont, erech_elfs,
    > erech_bn, erech]

-   where exists [belegloe_temp where belegtab_kz = "erech" and
    > erech_nr = beleg_nr]

-   Ende Transaktion

-   löschen [belegloe_temp]

-   aktueller Job

-   eigene Transaktion

-   lesen Lieferscheinpositionen ohne Faktura [elfs, elfs_pos] into
    [belegloe_temp]

-   elfs_pos.erech_nr < 0

-   elfs_dat <= Auswahldatum

-   elfs_beleg_dat <= Auswahldatum

-   belegtab_kz = "elfs_pos"

-   Löschen vorgemerkte Lieferscheine

-   Event w.o.

-   löschen [belegloe_temp]

-   aktueller Job

-   eigene Transaktion

-   lesen Bestellpositionen [best, best_pos, outer elfs_pos_best] into
    [belegloe_temp]

-   p_erl_best_nr = best_nr

-   elfs_pos_best.elfs_nr = NULL

-   best.best_dat <= Auswahldatum

-   belegtab_kz = "best_pos"

-   Löschen vorgemerkte Bestellpositionen

-   Beginn Transaktion

-   Aufruf Event für Ableitung

-   update [(rahmen_)best_pos]

-   Rahmenpositionen, die nicht gelöscht werden und die vorgemerkten
    > referenzieren

-   where exists [belegloe_temp where belegtab_kz = "best_pos" and
    > fa_nr = ? and rahmen_best_nr = belegloe_temp.beleg_nr and
    > rahmen_best_pos_nr = belegloe_temp.beleg_pos_nr AND
    > (rahmen_best_nr <> best_nr OR rahmen_best_pos_nr <>
    > best_pos_nr)]

-   rahmen_best_nr = best_nr

-   rahmen_best_pos_nr = best_pos_nr

-   update [auf_pos]

-   Auftragspositionen, welche die vorgemerkten Bestellpositionen
    > referenzieren

-   where exists [belegloe_temp, best_pos where belegtab_kz =
    > "best_pos" and best_pos_key and zug_best_nr =
    > belegloe_temp.beleg_nr and zug_best_pos_nr =
    > belegloe_temp.beleg_pos_nr]

-   zug_best_nr = 0

-   zug_best_pos_nr = 0

-   Ende Transaktion

-   Beginn Transaktion

-   löschen [best_pos_txt, best_pos]

-   where exists [belegloe_temp where belegtab_kz = "best_pos" and
    > best_pos_key]

-   Ende Transaktion

-   lesen Bestellungen [best] into [belegloe_temp]

-   (best.best_dat <= today - 365))

-   where not exists [best_pos]

-   belegtab_kz = "best "

-   Löschen vorgemerkte Bestellungen

-   Beginn Transaktion

-   Aufruf Event für Ableitung

-   löschen [best_txt, best]

-   where exists [belegloe_temp where belegtab_kz = "best" and
    > best_key]

-   Ende Transaktion

#### Lagerbuchungen

-   lesen diverse Lagerbuchungen [divlgb] into [belegloe_temp]

-   divlgb_dat <= Auswahldatum

-   belegtab_kz = "divlgb "

-   Löschen vorgemerkte Lagerbuchungen

-   Beginn Transaktion

-   Aufruf Event für Ableitung

-   löschen [divlgb]

-   where exists [belegloe_temp where belegtab_kz = "divlgb" and
    > divlgb_key]

-   Ende Transaktion

-   lesen Setproduktion [esetp] into [belegloe_temp]

-   esetp_dat <= Auswahldatum

-   belegtab_kz = "esetp"

-   Löschen vorgemerkte Setproduktionen

-   Beginn Transaktion

-   Aufruf Event für Ableitung

-   löschen [esetp_set, esetp]

-   where exists [belegloe_temp where belegtab_kz = "esetp" and
    > esetp_key]

-   Ende Transaktion

-   lesen Inventur [iv] into [belegloe_temp]

-   iv_dat <= Auswahldatum

-   iv_zustand_kz in ("e", "s")

-   iv_nr > 0

-   erl_iv_nr > 0

-   belegtab_kz = "iv"

-   Löschen vorgemerkte Inventuren

-   Beginn Transaktion

-   Aufruf Event für Ableitung

-   update [artik_lag]

-   where exists [belegloe_temp where belegtab_kz = "iv" and iv_key]

-   ltz_iv_nr = 0

-   löschen [iv_zeile, iv_bereich, iv]

-   where exists [belegloe_temp where belegtab_kz = "iv" and iv_key]

-   Ende Transaktion

#### Kassa 

-   siehe TradeControlBaustoff

### Löschen Statistikdaten

Auswahldialog

-   Firma (p)

-   Verarbeitungskennzeichen (p)

-   Einkauf (e)

-   Verkauf (v)

-   Einkauf und Verkauf (ev)

-   Von Periode (p)

-   Bis Periode (p)

-   Neuaufbau Statistik (p)

-   Ja

-   Nein

Ablauf

-   Die Verarbeitung erfolgt unabhängig von der Auswahl immer für ein
    > Monat

-   für den aktuellen Monatsbereich wird auch ein Von- /Bis-
    > Datumsbereich durch 1.1. des Von-Monats und durch den 1.1. des
    > Folgemonats - 1 bestimmt

-   pro Monat

-   beginnend bei Von-Periode lt. Auswahl

-   ein Schleifendurchlauf pro Monat bis zur Bis-Periode lt. Auswahl

-   Transaktion pro Tabelle, die verändert wird

-   Aufruf Event für Ableitung

-   löschen [st_ar_mon, st_ar_tag, st_kd_ar_mon, st_kd_mon, st_lf_mon,
    > st_lf_ar_mon]

-   mon = {aktuelles Monat}

-   Verarbeitungskennzeichen like "%v%"

-   update [vlfs_pos], stat_gebucht_jn "n"

-   vrech_mon = {aktuelles Monat}

-   stat_gebucht_jn = "j"

-   Verarbeitungskennzeichen like "%v%"

-   Neuaufbau Statistik = "j"

-   update [vlfs_pos], verb_gebucht_jn "n"

-   vlfs_mon = {aktuelles Monat}

-   verb_gebucht_jn = "j"

-   Verarbeitungskennzeichen like "%v%"

-   Neuaufbau Statistik = "j"

-   update [ka_bel_pos], stat_gebucht_jn "n"

-   bel_mon = {aktuelles Monat}

-   stat_gebucht_jn = "j"

-   Verarbeitungskennzeichen like "%v%"

-   Neuaufbau Statistik = "j"

-   löschen [vlfs_pos_statkorr] über DataStore

-   zugehörige Lieferscheinposition hat vrech_mon = {aktuelles Monat}

-   Verarbeitungskennzeichen like "%v%"

-   löschen [st_lf_mon, st_lf_ar_mon]

-   mon = {aktuelles Monat}

-   Verarbeitungskennzeichen like "%e%"

-   update [elfs_pos], stat_gebucht_jn "n"

-   erech_mon = {aktuelles Monat}

-   stat_gebucht_jn = "j"

-   Verarbeitungskennzeichen like "%e%"

-   Neuaufbau Statistik = "j"

-   nach dem letzten Monat

-   Aufgabe Job Statistikaufbau

-   wenn Neuaufbau Statistik = "j"

### Löschen CRM-Daten

Auswahldialog

-   Firma (f)

-   Kunde (f)

-   Verarbeitungskennzeichen (p)

-   KundenKontakte (k)

-   CRM-Daten (c)

-   KundenKontakte u. CRM-Daten (ck)

-   KundenKontakte bis (p)

-   Vorschlag {DatMax}

Ablauf

-   pro Kunde

-   CRM-Daten

-   eigene Transaktion pro Tabelle

-   löschen [adr_pers_fgr, adr_pers_fcol, adr_pers_ftxt]

-   löschen [kunde_casgr, kunde_casmitbew, kunde_ftxt]

-   löschen [cas_kunde_fgr]

-   fgrart.fgrart_tabelle_kz = "c"

-   löschen [cas_kunde_fcol]

-   fcol.fcol_tabelle_kz = "c"

-   Update [kunde]

-   budget_wert = 0

-   besint_wo = 0

-   bes_wota = 0

-   le_kont_dat = {DatMin}

-   n_besuchs_dat = {DatMin}

-   KundenKontakte

-   lesen [cas_kont]

-   erf_dat <= {KundenKontakte bis}

-   pro Kontakt

-   Beginn Transaktion

-   löschen [cas_kont_casunt, cas_kont_txt]

-   Update [casreiko]

-   kont_nr = 0

-   löschen [cas_kont]

-   Programmende

### Infoblatt DSGVO

Listbild:

[KundeStammBlatt.doc](KundeStammBlatt.doc)

Auswahldialog Kunde

-   Firma (f)

-   Kunde (f)

Auswahldialog Lieferant

-   Firma (f)

-   Lieferant (f)

Seitenkopf

-   Fixtexte

-   "[Kunden\|Lieferanten]informationsblatt"

-   "[Kunde\|Lieferant]Nr:"

-   "[Kunden\|Lieferanten]Adresse"

-   GeschäftspartnerNummer

-   Kundennummer

-   Lieferantennummer

-   Datum

-   Belegnummer

DatenGeschäftspartner

-   GeschäftspartnerAdresse

-   lt. [kunde_adr_snr]

-   lt. [lief_adr_snr]

-   ohne Leerzeilen

-   Name1-4

-   Straße

-   Postleitzahl + " " + Ort

-   Länderbezeichnung

-   frei konfigurierte Werte

-   lt. [kunde_dsgvo]

-   lt. [lief_dsgvo]

-   Text1

-   Text2

-   freie Gruppen Kunde bzw. Lieferant

-   fgrart_tabelle_kz in ("k", "c")

-   fgrart_tabelle_kz = "l"

-   fgrart_stammblatt_jn = "j"

-   Sortiert nach ÜbergruppenCode, GruppenCode

-   Label+":"

-   Wert

-   freie Kennzeichen Kunde bzw. Lieferant

-   fcol_tabelle_kz in ("k", "c")

-   fcol_tabelle_kz = "l")

-   fcol_stammblatt_jn = "j"

-   Sortiert nach ColumnCode

-   Label+":"

-   Wert

-   Kommunikationsdaten Geschäftspartner

-   Sortiert nach KommunikationsartSortNr, Kommunikationsart

-   Bezeichnung Kommunikationsart

-   Wert Kommunikationsart

-   Personendaten Geschäftspartner

-   Sortiert nach PersonenCode, KommunikationsartSortNr,
    > Kommunikationsart

-   Leerzeile

-   Personenstring, gebildet aus

-   "Hr." bzw. "Fr." lt. Geschlecht

-   Titel

-   Vorname

-   Nachname

-   Geburtsdatum

-   Bezeichnung Funktionscode

-   Kommunikationsdaten der Person

-   Bezeichnung Kommunikationsart

-   Wert Kommunikationsart

-   freie Gruppen Person

-   fgrart_tabelle_kz ="p"

-   fgrart_stammblatt_jn = "j"

-   Sortiert nach ÜbergruppenCode, GruppenCode

-   Label+":"

-   Wert

-   freie Kennzeichen Person

-   fcol_tabelle_kz ="p"

-   fcol_stammblatt_jn = "j"

-   Sortiert nach ColumnCode

-   Label+":"

-   Wert

-   WerbeAdresse

-   nur, wenn WerbeAdresse <> GeschäftspartnerAdresse

-   Fixtext "Werbeadresse"

-   Adress-, Personen- und Kommunikationsdaten wie unter
    > "GeschäftspartnerAdresse", "Kommunikationsdaten
    > Geschäftspartner" und "Personendaten Geschäftspartner"

-   Debitoren- bzw. Kreditorenadresse mit Kommunikationsdaten

-   Felder wie w.o.

-   [debitor_adr_snr]

-   [kreditor_adr_snr]

-   frei konfigurierte Werte

-   lt. [debitor_dsgvo]

-   lt. [kreditor_dsgvo]

-   Text1

-   Text2

-   Personendaten Rechnungsadresse

-   nur, wenn Debitorenadresse <> Kundenadresse

-   nur, wenn Kreditorenadresse <> Lieferantenadresse

-   sonst wie bei Persondendaten Geschäftspartner

### Löschen Offerte

#### Auswahldialog

-   Firma (p)

-   Offertdatum (!)

-   z.B: "<h-180"

-   Löschen, wenn möglich (p)

-   Ja

-   Nein

Ablauf

-   Verarbeitung von offenen Offertpositionen

-   [auf.aufart_cd = "o"]

-   [auf.erl_ein_auf_nr = 0]

Anmerkung "Löschen, wenn möglich"

-   darf eine Position gelöscht werden, dann wird gelöscht, ansonsten
    > "erledigt"-gesetzt

-   gelöscht werden darf, wenn

-   Parameter = "j"

-   [auf_lief_mg = 0]

-   keine Referenzierung der aktuellen vorhanden [abruf_ein_auf_nr = ?
    > and abruf_auf_pos_nr = ?]

-   pro Offertposition

-   Beginn Transaktion

-   prüfen, ob Löschen oder erledigen

-   Löschen oder erledigen

-   Ende Transaktion

-   Programmende

### Archivetikettendruck Zweckform

**Auswahldialog**

-   Blattanzahl

Drucklayout

Zweckform 3658 (24 Etiketten je Blatt)

-   je Etikett fortlaufende EAN-Nummer (wird mittels gf_serial in einer
    Transaktion je Blatt vergeben)

### UID-Prüflog Abfrage

Auswahldialog:

-   Firmennummer

-   Debitorennummer (f)

-   Kreditorennummer (f)

-   UID-Nummer

-   Prüfungszeitpunkt

Liste

-   Firmennummer

-   Debitorennummer

-   Debitorenmatchcode

-   Kreditorennummer

-   Kreditorenmatchcode

-   UID-Nummer

-   Ergebniscode

-   Ergebnistext

-   In Darstellung "info" wenn Ergebnisstatus <> ok

-   Zeitpunkt der Prüfung

-   User der die Prüfung durchgeführt hat

Detail

-   Nur Abfrage keine Änderung/Löschen oder Neuanlage möglich

-   Firmennummer

-   Debitorennummer

-   Debitorenmatchcode

-   Kreditorennummer

-   Kreditorenmatchcode

-   UID-Nummer

-   Ergebniscode

-   Ergebnistext

-   Zeitpunkt der Prüfung

-   User der die Prüfung durchgeführt hat

-   FION Name

-   FION Adresse 1 -- 5

-   TC Name 1 -- 4

-   TC Ländercode

-   TC PLZ

-   TC Ort

### Zusammenführen Artikeldaten

Ablauf

-   Einlesen der Daten

-   pro Datensatz

-   prüfen Lock

-   wenn zf_lock_jn = "j", fortsetzen bei nächstem Datensatz

-   Beginn Transaktion

-   setzen Lockkennzeichen zf_lock_jn "j"

-   setzen Beginnzeit dat_beginn aktuelles Datum+Uhrzeit

-   Ende Transaktion

-   Prüfungen

-   Kopieren/Zusammenführen

    **Prüfungen**

-   nur wenn Bewegungen übernommen werden sollen [zf_beweg_jn = "j"]

-   lesen offene Bewegungen Verkauf [auf_pos] alter Artikel

-   auf_pos.erl_ein_auf_nr = 0

-   auf_lag_ftr <> 0

-   wenn offene Bewegung vorhanden

-   zf_txt "offener Auftrag vorhanden"

-   zf_status_kz "p"

-   dat_ende aktuelles Datum+Uhrzeit

-   Ende Verarbeitung

-   lesen offene Produktionsaufträge [auf_prod] alter Artikel

-   auf.erl_auf_nr = 0

-   wenn offene Bewegung vorhanden

-   zf_txt "offener Produktionsauftrag vorhanden"

-   zf_status_kz "p"

-   dat_ende aktuelles Datum+Uhrzeit

-   Ende Verarbeitunglesen offene Bewegungen Einkauf [best_pos] alter
    Artikel

-   best_pos. p_erl_best_nr = 0

-   wenn offene Bewegung vorhanden

-   zf_txt "offene Bestellung vorhanden"

-   zf_status_kz "p"

-   dat_ende aktuelles Datum+Uhrzeit

-   Ende Verarbeitung

-   lesen offene Bewegungen Einkauf [elfs] alter Artikel

-   elfs_zustand_kz = "ve"

-   zf_txt "offene Warenübernahme vorhanden"

-   zf_status_kz "p"

-   dat_ende aktuelles Datum+Uhrzeit

-   Ende Verarbeitung

-   lesen Gerätetabelle [geraet] beider Artikel

-   wenn Seriennummern mehrfach vorhanden

-   zf_txt "Seriennummern nicht eindeutig"

-   zf_status_kz "p"

-   dat_ende aktuelles Datum+Uhrzeit

-   Ende Verarbeitung

-   lesen Lagersätze [artik_lag] beider Artikel

-   wenn offene Inventur [offen_iv_nr <> 0] vorhanden

-   zf_txt "Inventur offen"

-   zf_status_kz "p"

-   dat_ende aktuelles Datum+Uhrzeit

-   Ende Verarbeitung

    **Kopieren/Zusammenführen**

-   ArtikelEinkauf/Artikelproduktion

-   wenn zf_ek_kz in ("v", "k")

-   Beginn Transaktion

-   sperren Lieferant, sperren alten und neuen Artikel

-   löschen artik_lief\* - Tabellen des neuen Artikel

-   Übernahme artik_lief\* - Tabellen des alten Artikel in DataStore

-   Anlage artik_lief\* - Tabellen mit neuem Artikel und den Daten der
    > DataStore

-   setzen neu_artik_cd

-   löschen artik_lief\* - Tabellen des alten Artikel

-   wenn zf_ek_kz = "v"

-   zf_status_kz "e"

-   Ende Transaktion

-   Artikelverkaufskonditionen

-   wenn zf_vk_kz in ("v", "k")

-   Beginn Transaktion

-   sperren alten und neuen Artikel

-   löschen vkkond\* - Tabellen des neuen Artikel

-   artik_zuord = neu_artik_cd

-   vkkondart.artik_zuord_kz = "n"

-   vkkond_snr not in (neu_artikvkkond_snr)

-   Übernahme vkkond\* - Tabellen des alten Artikel in DataStore

-   artik_zuord = artik_cd

-   vkkondart.artik_zuord_kz = "n"

-   vkkond_snr not in (artikvkkond_snr)

-   Anlage vkkond\* - Tabellen mit neuem Artikel und den Daten der
    > DataStore

-   setzen neu_artik_cd

-   vergeben und setzen neu_vkkond_snr

-   löschen vkkond\* - Tabellen des alten Artikel

-   wenn zf_vk_kz = "v"

-   zf_status_kz "v"

-   Ende Transaktion

-   Artikelidentifikationen

-   wenn zf_id_kz = "v"

-   Beginn Transaktion

-   sperren alten und neuen Artikel

-   löschen Tabelle [artikid] des neuen Artikel

-   artik_cd = neu_artik_cd

-   artikid_kz in (e, l, k, s, d)

-   lesen Tabelle [artikid] des alten Artikel in DataStore

-   setzen neue Artikelnummer

-   speichern Datastore

-   löschen alte Datensätze

-   Anlage neue Datensätze

-   zf_status_kz "i"

-   Ende Transaktion

-   ArtikelLager

-   wenn zf_beweg_jn = "j"

-   Funktionalität des Lagermoduls

-   Beginn Transaktion

-   sperren alten und neuen Artikel

-   Neuanlage bzw Update Tabelle [artik_lag] neuer Artikel

-   Lagerstand erhöhen

-   letzte Inventurnummer wird auf 0 gesetzt

-   Lagerort wird blank bei Neuanlage bzw. bei Update nicht verändert

-   letzte Karteinummer wird auf das Maximum aus den beiden Lagersätzen
    > gesetzt

-   Neuanlage bzw Update Tabelle [artik_lag_sub] neuer Artikel

-   Lagerstand erhöhen

-   Update Tabelle [artik] beider Artikel

-   erhöhen bzw. vermindern Lagerstand

-   löschen Tabelle [artik_lag_sub] alter Artikel

-   löschen Tabelle [artik_lag] alter Artikel

-   zf_status_kz "l"

-   Ende Transaktion

-   Gerätedaten

-   wenn zf_beweg_jn = "j"

-   wenn Lagerführungskennzeichen "g"

-   Beginn Transaktion

-   sperren alten und neuen Artikel

-   Transaktion je Gerät

-   Übernahme geraet_\* - Tabellen des alten Artikel in DataStores

-   Update Tabelle [geraet]

-   setzen neue Artikelnummer

-   setzen neue Artikelnummer in die Datastores

-   Speichern Datastores

-   zf_status_kz "s"

-   Ende Transaktion

-   Buchungszeilen und Kartei

-   wenn zf_beweg_jn = "j"

-   zf_status_kz "b"

-   je Tabelle werden alle Sätze mit alter Artikelnummer gelesen

-   die neue Artikelnummer wird eingetragen

-   Transaktion je Datensatz

-   Tabelle [auf_pos]

-   Tabelle [auf_pos_set]

-   Tabelle [auf_pos_sub]

-   Tabelle [auf_prod]

-   Tabelle [apollo_auf_pos]

-   Tabelle [best_pos]

-   Tabelle [divlgb]

-   Tabelle [elfs_pos]

-   wird Satz geändert, wird Statistiklöschprogramm für Zweig
    > "Einkauf" am Ende des Laufes eingespoolt "200001" bis
    > {aktuelles Monat}

-   Tabelle [erechimp_pos]

-   Tabelle [esetp]

-   Tabelle [esetp_set]

-   Tabelle [fa]

-   Tabelle [iv_zeile]

-   Tabelle [ka_bel_pos]

-   Tabelle [ka_fa]

-   Tabelle [kartei_lagbew]

-   Tabelle [kartei_duest]

-   Tabelle [magento_bestell_pos]

-   Tabelle [s_auf]

-   Tabelle [s_kunde]

-   Tabelle [versart]

-   Tabelle [vlfs_pos]

-   ist Verbrauch oder Statistik bereits gebucht, wird das entsprechende
    > Kennzeichen auf "n" umgesetzt und ein Korrektursatz mit
    > negativen Werten in Tabelle [st_statkorr] angelegt

-   Tabelle [vlfs_pos_gerstat]

-   Tabelle [wv_pos]

-   Tabelle [artik]

-   aktiv_jn "n", bei alter Artikelnummer

-   dat_ende aktuelles Datum+Uhrzeit

-   zf_status_kz "o"

## Schnittstellen

### Stammdaten Importe

#### Einkaufspreisimportschnittstelle

Auswahldialog

-   Pfad inklusive Dateiname der ASCII-Datei (p)

-   Kennzeichen Artikelidentifikation (p)

-   a = Artikelnummer

-   e = EAN-Nummer

-   l = Lieferantenartikelnummer

-   Offset (p)

-   Anzahl Zeilen zum Beginn der ASCII-Datei, die nicht verarbeitet
    > werden sollen

Auswahl der Daten

-   alle Zeilen in der Schnittstelle

Fileformat

-   variable Satzlänge

-   Felder duch TAB getrennt

-   nach dem letzten Feld CR + LF (kein TAB mehr)

-   kein CTRL+Z am Ende

-   Windows- Zeichensatz (8859)

-   ACHTUNG: der Filename darf nicht länger als 51 Zeichen sein! (Weil
    ein Job- Parameter nicht länger sein darf)

-   **Excel- Speicher- Format: Text (Tabs getrennt**)

Schnittstellenaufbau

-   Firmennummer

-   Lieferantennummer

-   Artikelidentifikation

-   Aktionskennzeichen

-   a = Aktion

-   n = Normalaktion

-   Gültig-Ab-Datum

-   Gültig-Bis-Datum

-   darf bei Aktionskennzeichen "n" leer sein

-   Ab-Menge

-   leer = 0

-   Einkaufspreis

-   leer = NULL, bzw. unverändert lt. letztgültiger Kondition

-   Währungscode

-   leer = lt. Lieferant, bzw. unverändert lt. letztgültiger Kondition

-   Einkaufsrabatt 1 u. 2

-   leer = 0, bzw. unverändert lt. letztgültiger Kondition

-   Naturalrabatt

-   leer = 0, bzw. unverändert lt. letztgültiger Kondition

**Anmerkung**

Durch Anpassung der Standardparameter folgende individuelle
Einstellungen der Schnittstelle möglich:

-   Firmennummer kann entfallen, die kleinste Firma lt. Tabelle [fa]
    wird verwendet

-   Aktionskennzeichen kann entfallen, "n" wird verwendet

-   in diesem Fall entfällt auch das "Gültig-Bis-Datum"

-   Ab-Menge kann entfallen, 0 wird verwendet

-   Währung kann entfallen, es wird die Währung lt. Tabelle [lief]
    verwendet

-   Naturalrabatt kann entfallen, 0 wird verwendet

-   Die Anzahl der Rabatte kann bis auf 5 erhöht werden

Ablauf

-   einlesen der ASCII-Schnittstelle

-   Pro Datensatz

-   Anlage einer neuen Zeile im Teilbereich "Einkaufspreise" des
    > Artikel/Lieferanten

-   setzen des Gültig-Bis-Datums bei der vorhergehenden Zeile (bei
    > Aktionskennzeichen "n")

-   Druck eines Fehlerprotokolls

-   wenn Artikel/Lieferant nicht gefunden

-   wenn durch sonstigen Fehler die Anlage nicht möglich war

-   Endemeldung des Batchlaufes

#### Verkaufspreisimportschnittstelle

Auswahldialog

-   Pfad inklusive Dateiname der ASCII-Datei (p)

-   Offset (p)

-   Anzahl Zeilen zum Beginn der ASCII-Datei, die nicht verarbeitet
    > werden sollen

Auswahl der Daten

-   alle Zeilen in der Schnittstelle

Fileformat

-   variable Satzlänge

-   Felder duch TAB getrennt

-   nach dem letzten Feld CR + LF (kein TAB mehr)

-   kein CTRL+Z am Ende

-   Windows- Zeichensatz (8859)

-   ACHTUNG: der Filename darf nicht länger als 51 Zeichen sein! (Weil
    ein Job- Parameter nicht länger sein darf)

-   **Excel- Speicher- Format: Text (Tabs getrennt)**

Schnittstellenaufbau

-   Firmennummer

-   Konditionsart

-   Artikelzuordnung

-   Artikelnummer

-   Artikelkonditionsgruppe

-   leer

-   Kundenzuordnung

-   Kundennummer

-   Kundenkonditionsgruppe

-   leer

-   Preislistencode

-   Gültig-Ab-Datum

-   Gültig-Bis-Datum

-   darf bei Konditionsarten die keine Aktionen sind, leer sein

-   Ab-Menge

-   leer = 0

-   Verkaufspreis

-   leer = NULL, bzw. unverändert lt. letztgültiger Kondition

-   Verkaufsrabatt 1 u. 2

-   leer = 0, bzw. unverändert lt. letztgültiger Kondition

-   Naturalrabatt

-   leer = 0, bzw. unverändert lt. letztgültiger Kondition

Anmerkung für individuelle Ableitungen

Durch Anpassung der Standardparameter folgende individuelle
Einstellungen der Schnittstelle möglich:

-   Firmennummer kann entfallen, die kleinste Firma lt. Tabelle [fa]
    wird verwendet

-   Preislistencode kann entfallen, der kleinste Code lt. Tabelle
    [preisli] wird verwendet

-   Ab-Menge kann entfallen, 0 wird verwendet

-   Naturalrabatt kann entfallen, 0 wird verwendet

-   Die Anzahl der Rabatte kann bis auf 5 erhöht werden

Ablauf

-   einlesen der ASCII-Schnittstelle

-   Pro Datensatz

-   Anlage einer neuen Zeile im Teilbereich "Verkaufspreise" des
    > Verkaufskonditionsfenseters

-   setzen des Gültig-Bis-Datums bei der vorhergehenden Zeile (bei
    > Aktionskennzeichen "n")

-   Druck eines Fehlerprotokolls

-   wenn Kondition nicht gefunden

-   wenn durch sonstigen Fehler die Anlage nicht möglich war

-   Endemeldung des Batchlaufes

#### Import Artikelbilder für TC.next

Auswahlkriterien

-   Firma (p)

-   Bildart-KZ (w)

-   Import Pfad (p)

-   Präfix (o)

-   Suffix (z.B. .jpg) (p)

-   Archiv Pfad (o)

Ablauf:

Pro File im Import Pfad, mit dem Angegebenen Präfix und Suffix:

-   Prüfen ob mit dem Teil des Filenames zwischen Präfix und Suffix als
    artik_cd ein Artikel angelegt ist (z.B. Präfix = "k_" Suffix =
    ".jpg", File = k_4711.jpg -- dann ist 4711 der artik_cd).

-   Wenn der Artikel vorhanden ist

-   Insert/Update artik_bild

-   Wenn ein Archiv Pfad angegeben ist, wird das File in den Archiv Pfad
    > verschoben

-   Löschen des Files  
    > Das Löschen erfolgt nach dem Commit des DB Updates

-   Ansonsten wird das File ignoriert

#### Import Zolltarifnummern

Auswahkriterien

-   Filename (inkl. Pfad) (p)

-   Alte Zolltarifnummern deaktivieren j/n (p)

    Es wird ein csv-File (Trennzeichen ;) importiert.

    Das File enthält eine Überschriftszeile.

    Folgende Spalten sind vorhanden:

-   Zolltarifnummer (KN8)

-   Text

-   Besondere Maßeinheit (KZ)

Wenn die Zolltarifnummer angelegt ist, wird bei dieser der Text, die
Besondere Maßeinheit und die Import-Jobnummer aktualisiert und die
Zolltarifnummer auf aktiv gestellt.

Wenn sie nicht angelegt ist, wird sie geinsertet.

-   is_zollta_nr = KN8

-   ztnr_mc = Text (maximal 1000 Zeichen)

-   bmaeh_kz = Besondere Maßeinheit

-   is_veh_bmaeh_ftr = 0

-   ztnr_aktiv_jn = j

-   eudr_jn = n

-   import_job_snr = aktuelle Jobnummer

Wenn alte Zolltarifnummern deaktivieren ausgewählt wurde, werden alle
Zolltarifnummer die nicht die aktuekke Jobnummer haben auf inaktiv
gesetzt. Ausgenommer ist der Dummy Eintrag.

Der gesamte Import ist eine Transaktion.

### Integration BMD-FIBU

#### Ausgabe BMD-Stammdaten

Auswahldialog

-   Firma (p)

-   Pfad (p)

Ablauf allgemein

-   alle Debitoren/Kreditoren deren Änderungsdatum jünger als das letzte
    Ausgabedatum lt. Firmenstamm ist werden ausgegeben

-   Dateiformat ist ASCII mit fixer Satzlänge ohne Trennzeichen

-   numerische Werte werden mit Vorlaufnullen ausgegeben

-   alphanumerische Werte werden mit Space am Ende ausgegeben

Dateiaufbau

-   Gesamtlänge 1000 Zeichen

-   Detailbeschreibung siehe "TradeConHolz\\Org\\BMD-Stammdaten.doc"

+-----------------+-------------------+-------------------+---+-----------+
|                 | Debitor           | Kreditor          | L |           |
|                 |                   |                   | ä |           |
|                 |                   |                   | n |           |
|                 |                   |                   | g |           |
|                 |                   |                   | e |           |
+=================+===================+===================+===+===========+
| Kontonummer     | d                 | kre               | n |           |
|                 | ebitor.debitor_nr | ditor.kreditor_nr | 9 |           |
+-----------------+-------------------+-------------------+---+-----------+
| Bezeichnung     | adr.name1         | adr.name1         | a |           |
|                 |                   |                   | 3 |           |
|                 |                   |                   | 5 |           |
+-----------------+-------------------+-------------------+---+-----------+
| Matchcode       | d                 | kre               | a |           |
|                 | ebitor.debitor_mc | ditor.kreditor_mc | 2 |           |
|                 |                   |                   | 0 |           |
+-----------------+-------------------+-------------------+---+-----------+
| Titel           | \' \'             | \' \'             | a |           |
|                 |                   |                   | 1 |           |
|                 |                   |                   | 5 |           |
+-----------------+-------------------+-------------------+---+-----------+
| Branche         | adr.name2         | adr.name2         | a |           |
|                 |                   |                   | 3 |           |
|                 |                   |                   | 5 |           |
+-----------------+-------------------+-------------------+---+-----------+
| Strasse         | adr.strasse       | adr.strasse       | a |           |
|                 |                   |                   | 3 |           |
|                 |                   |                   | 0 |           |
+-----------------+-------------------+-------------------+---+-----------+
| PLZ             | adr.plz           | adr.plz           | a |           |
|                 |                   |                   | 1 |           |
|                 |                   |                   | 2 |           |
+-----------------+-------------------+-------------------+---+-----------+
| Ort             | adr.ort           | adr.ort           | a |           |
|                 |                   |                   | 2 |           |
|                 |                   |                   | 0 |           |
+-----------------+-------------------+-------------------+---+-----------+
| Postfach        | \' \'             | \' \'             | a |           |
|                 |                   |                   | 2 |           |
|                 |                   |                   | 0 |           |
+-----------------+-------------------+-------------------+---+-----------+
| Postfach-PLZ    | \' \'             | \' \'             | a |           |
|                 |                   |                   | 1 |           |
|                 |                   |                   | 2 |           |
+-----------------+-------------------+-------------------+---+-----------+
| Stra            | \' \'             | \' \'             | a |           |
| ssenkennzeichen |                   |                   | 4 |           |
+-----------------+-------------------+-------------------+---+-----------+
| Staat           | adr.land_cd       | adr.land_cd       | a |           |
|                 |                   |                   | 3 |           |
+-----------------+-------------------+-------------------+---+-----------+
| Kontaktperson   | \' \'             | \' \'             | a |           |
|                 |                   |                   | 3 |           |
|                 |                   |                   | 0 |           |
+-----------------+-------------------+-------------------+---+-----------+
| Telefonnummer   | adr_pers          | adr_pers          | a |           |
|                 | _komid.komid_wert | _komid.komid_wert | 1 |           |
|                 | mit MIN(sort_nr)  |                   | 8 |           |
|                 | WHERE komidart_kz | mit MIN(sort_nr)  |   |           |
|                 | = \'t\'           | WHERE komidart_kz |   |           |
|                 |                   | = \'t\'           |   |           |
+-----------------+-------------------+-------------------+---+-----------+
| Faxnummer       | adr_pers          | adr_pers          | a |           |
|                 | _komid.komid_wert | _komid.komid_wert | 1 |           |
|                 | mit MIN(sort_nr)  | mit MIN(sort_nr)  | 8 |           |
|                 | WHERE komidart_kz | WHERE komidart_kz |   |           |
|                 | = \'f\'           | = \'f\'           |   |           |
+-----------------+-------------------+-------------------+---+-----------+
| E-Mailadresse   | adr_pers          | adr_pers          | a |           |
|                 | _komid.komid_wert | _komid.komid_wert | 5 |           |
|                 | mit MIN(sort_nr)  | mit MIN(sort_nr)  | 0 |           |
|                 | WHERE komidart_kz | WHERE komidart_kz |   |           |
|                 | = \'e\'           | = \'e\'           |   |           |
+-----------------+-------------------+-------------------+---+-----------+
| In              | adr_pers          | adr_pers          | a |           |
| ternet-Homepage | _komid.komid_wert | _komid.komid_wert | 3 |           |
|                 | mit MIN(sort_nr)  | mit MIN(sort_nr)  | 5 |           |
|                 | WHERE komidart_kz | WHERE komidart_kz |   |           |
|                 | = \'w\'           | = \'w\'           |   |           |
+-----------------+-------------------+-------------------+---+-----------+
| B               | debit             | kredit            | a |           |
| ank-Kontonummer | or_bank.bankkonto | or_bank.bankkonto | 2 |           |
|                 |                   |                   | 0 |           |
+-----------------+-------------------+-------------------+---+-----------+
| Bankleitzahl    | debi              | debi              | a |           |
|                 | tor_bank.bank_blz | tor_bank.bank_blz | 1 |           |
|                 |                   |                   | 2 |           |
+-----------------+-------------------+-------------------+---+-----------+
| IBAN-Nummer     | debitor_bank.iban | k                 | a |           |
|                 |                   | reditor_bank.iban | 3 |           |
|                 |                   |                   | 4 |           |
+-----------------+-------------------+-------------------+---+-----------+
| Swiftcode       | bank.bic          | bank.bic          | a |           |
|                 |                   |                   | 1 |           |
|                 |                   |                   | 2 |           |
+-----------------+-------------------+-------------------+---+-----------+
| Bank Ländercode | debitor_          | debitor_          | a |           |
|                 | bank.bank_land_cd | bank.bank_land_cd | 2 |           |
+-----------------+-------------------+-------------------+---+-----------+
| UStID           | debitor.ustid     | kreditor.ustid    | a |           |
|                 |                   |                   | 1 |           |
|                 |                   |                   | 5 |           |
+-----------------+-------------------+-------------------+---+-----------+
| Zess            | \' \'             | \' \'             | a |           |
| ionskennzeichen |                   |                   | 1 |           |
+-----------------+-------------------+-------------------+---+-----------+
| Datum (freie    | 0                 | 0                 | n |           |
| Verwendung)     |                   |                   | 8 |           |
+-----------------+-------------------+-------------------+---+-----------+
| Zahlsperre      | 0                 | 0                 | n |           |
|                 |                   |                   | 2 |           |
+-----------------+-------------------+-------------------+---+-----------+
| Zahlspesen      | 1                 | 1                 | n |           |
|                 |                   |                   | 2 |           |
+-----------------+-------------------+-------------------+---+-----------+
| Zahlgrund       | 1                 | 1                 | n |           |
|                 |                   |                   | 2 |           |
+-----------------+-------------------+-------------------+---+-----------+
| ZahlumsatzPos   | 0                 | 0                 | n |           |
|                 |                   |                   | 4 |           |
+-----------------+-------------------+-------------------+---+-----------+
| Zahlungs        | 1                 | 1                 | n |           |
| überweisungsArt |                   |                   | 2 |           |
+-----------------+-------------------+-------------------+---+-----------+
| Zahlbank        | 0                 | 0                 | n |           |
|                 |                   |                   | 4 |           |
+-----------------+-------------------+-------------------+---+-----------+
| Bankeinzug      | 0                 | 0                 | n |           |
|                 |                   |                   | 4 |           |
+-----------------+-------------------+-------------------+---+-----------+
| F               | debitor.frktonr   | kreditor.frktonr  | n |           |
| remdkontonummer |                   |                   | 9 |           |
+-----------------+-------------------+-------------------+---+-----------+
| Ausländer       | land              | land              | n |           |
|                 | .inl_eu_drittl_kz | .inl_eu_drittl_kz | 2 |           |
|                 | = \'i\' 0         | = \'i\' 0         |   |           |
|                 |                   |                   |   |           |
|                 | sonst 1           | sonst 1           |   |           |
+-----------------+-------------------+-------------------+---+-----------+
| Keine           | \'0\' wenn        | \'0\' wenn        | n |           |
| St              | inl_eu_drittl_kz  | inl_eu_drittl_kz  | 2 |           |
| euerkennzeichen | =\'i\'            | =\'i\'            |   |           |
|                 |                   |                   |   |           |
|                 | \'1\' sonst       | \'1\' sonst       |   |           |
+-----------------+-------------------+-------------------+---+-----------+
| Nettotage       | zahlkond.netto_tg | zahlkond.netto_tg | n |           |
|                 |                   |                   | 6 |           |
+-----------------+-------------------+-------------------+---+-----------+
| 1.             | zah               | zah               | n |           |
| Sk              | lkond.skonto1_prz | lkond.skonto1_prz | 5 |           |
| ontoprozentsatz |                   |                   | ( |           |
|                 |                   |                   | 3 |           |
|                 |                   |                   | V |           |
|                 |                   |                   | K |           |
|                 |                   |                   | , |           |
|                 |                   |                   | 2 |           |
|                 |                   |                   | N |           |
|                 |                   |                   | K |           |
|                 |                   |                   | ) |           |
+-----------------+-------------------+-------------------+---+-----------+
| Zieltage 1      | za                | za                | n |           |
|                 | hlkond.skonto1_tg | hlkond.skonto1_tg | 4 |           |
+-----------------+-------------------+-------------------+---+-----------+
| 2.             | zah               | zah               | n |           |
| Sk              | lkond.skonto2_prz | lkond.skonto2_prz | 5 |           |
| ontoprozentsatz |                   |                   | ( |           |
|                 |                   |                   | 3 |           |
|                 |                   |                   | V |           |
|                 |                   |                   | K |           |
|                 |                   |                   | , |           |
|                 |                   |                   | 2 |           |
|                 |                   |                   | N |           |
|                 |                   |                   | K |           |
|                 |                   |                   | ) |           |
+-----------------+-------------------+-------------------+---+-----------+
| Zieltage 2      | za                | za                | n |           |
|                 | hlkond.skonto2_tg | hlkond.skonto2_tg | 4 |           |
+-----------------+-------------------+-------------------+---+-----------+
| Kondition 2     | 0                 | 0                 | n |           |
|                 |                   |                   | 4 |           |
+-----------------+-------------------+-------------------+---+-----------+
| max.            | 0                 | 0                 | n |           |
| S               |                   |                   | 5 |           |
| kontoabweichung |                   |                   | ( |           |
| in %            |                   |                   | 3 |           |
|                 |                   |                   | V |           |
|                 |                   |                   | K |           |
|                 |                   |                   | , |           |
|                 |                   |                   | 2 |           |
|                 |                   |                   | N |           |
|                 |                   |                   | K |           |
|                 |                   |                   | ) |           |
+-----------------+-------------------+-------------------+---+-----------+
| Mahnsperre      | debitor.          | 0                 | n |           |
|                 | mhktosperre_kz    |                   | 2 |           |
+-----------------+-------------------+-------------------+---+-----------+
| Mahnkosten      | 0                 | 0                 | n |           |
|                 |                   |                   | 2 |           |
+-----------------+-------------------+-------------------+---+-----------+
| MahnVerbuchKz   | 0                 | 0                 | n |           |
|                 |                   |                   | 2 |           |
+-----------------+-------------------+-------------------+---+-----------+
| Mahndatum       | 0                 | 0                 | n |           |
|                 |                   |                   | 8 |           |
+-----------------+-------------------+-------------------+---+-----------+
| Mahnformular    | 0                 | 0                 | n |           |
|                 |                   |                   | 4 |           |
+-----------------+-------------------+-------------------+---+-----------+
| Mahnkontoauszug | 0                 | 0                 | n |           |
|                 |                   |                   | 2 |           |
+-----------------+-------------------+-------------------+---+-----------+
| Bonität         | 0                 | 0                 | n |           |
|                 |                   |                   | 4 |           |
+-----------------+-------------------+-------------------+---+-----------+
| Gegenve         | 0                 | 0                 | n |           |
| rrechnungskonto |                   |                   | 9 |           |
+-----------------+-------------------+-------------------+---+-----------+
| Div Code        | debitor_divers_jn | k                 | n |           |
|                 | = \'j\' 1         | reditor_divers_jn | 2 |           |
|                 |                   | = \'j\' 1         |   |           |
|                 | sonst 0           |                   |   |           |
|                 |                   | sonst 0           |   |           |
+-----------------+-------------------+-------------------+---+-----------+
| SammelkontoKZ   | pfufb_persk       | pfufb_persk       |   | n 2       |
|                 | to_vor.psakid_psa | to_vor.psakid_psa |   |           |
|                 | wenn <=9         | wenn <=9         |   |           |
+-----------------+-------------------+-------------------+---+-----------+
| Sammelkonto     | pfufb_persk       | pfufb_persk       |   | n 9       |
|                 | to_vor.psakid_psa | to_vor.psakid_psa |   |           |
|                 | wenn >9          | wenn >9          |   |           |
+-----------------+-------------------+-------------------+---+-----------+
| Rechnungskonto  | 0                 | 0                 | n |           |
|                 |                   |                   | 9 |           |
+-----------------+-------------------+-------------------+---+-----------+
| UStID-Datum     | debitor.ustiddat  | kreditor.ustiddat | J |           |
|                 |                   |                   | J |           |
|                 |                   |                   | J |           |
|                 |                   |                   | J |           |
|                 |                   |                   | M |           |
|                 |                   |                   | M |           |
|                 |                   |                   | D |           |
|                 |                   |                   | D |           |
+-----------------+-------------------+-------------------+---+-----------+
| Firmenanrede    | 0                 | 0                 | n |           |
|                 |                   |                   | 4 |           |
+-----------------+-------------------+-------------------+---+-----------+
| Persönliche     | 0                 | 0                 | n |           |
| Anrede          |                   |                   | 4 |           |
+-----------------+-------------------+-------------------+---+-----------+
| Z               | 0                 | 0                 | n |           |
| u-Handen-Anrede |                   |                   | 4 |           |
+-----------------+-------------------+-------------------+---+-----------+
| Briefanrede     | 0                 | 0                 | n |           |
|                 |                   |                   | 4 |           |
+-----------------+-------------------+-------------------+---+-----------+
| BranchenKz      | 0                 | 0                 | n |           |
|                 |                   |                   | 4 |           |
+-----------------+-------------------+-------------------+---+-----------+
| Vertreter 1     | 0                 | 0                 | n |           |
|                 |                   |                   | 6 |           |
+-----------------+-------------------+-------------------+---+-----------+
| Vertreter 2     | 0                 | 0                 | n |           |
|                 |                   |                   | 6 |           |
+-----------------+-------------------+-------------------+---+-----------+
| Versandart      | 0                 | 0                 | n |           |
|                 |                   |                   | 4 |           |
+-----------------+-------------------+-------------------+---+-----------+
| Verkaufsgebiet  | 0                 | 0                 | n |           |
|                 |                   |                   | 4 |           |
+-----------------+-------------------+-------------------+---+-----------+
| Handelsring     | 0                 | 0                 | n |           |
|                 |                   |                   | 4 |           |
+-----------------+-------------------+-------------------+---+-----------+
| KM-Entfernung   | 0                 | 0                 | n |           |
|                 |                   |                   | 4 |           |
+-----------------+-------------------+-------------------+---+-----------+
| Rabattcode      | 0                 | 0                 | n |           |
|                 |                   |                   | 4 |           |
+-----------------+-------------------+-------------------+---+-----------+
| Rabatt          | 0                 | 0                 | n |           |
|                 |                   |                   | 9 |           |
|                 |                   |                   | ( |           |
|                 |                   |                   | 6 |           |
|                 |                   |                   | V |           |
|                 |                   |                   | . |           |
|                 |                   |                   | 2 |           |
|                 |                   |                   | N |           |
|                 |                   |                   | ) |           |
+-----------------+-------------------+-------------------+---+-----------+
| Auftragsstand   | 0                 | 0                 | n |           |
|                 |                   |                   | 1 |           |
|                 |                   |                   | 8 |           |
|                 |                   |                   | ( |           |
|                 |                   |                   | 1 |           |
|                 |                   |                   | 5 |           |
|                 |                   |                   | V |           |
|                 |                   |                   | . |           |
|                 |                   |                   | 2 |           |
|                 |                   |                   | N |           |
|                 |                   |                   | ) |           |
+-----------------+-------------------+-------------------+---+-----------+
| Kreditlimit     | de                | 0                 | n |           |
|                 | bitor.kreditlimit |                   | 1 |           |
|                 |                   |                   | 5 |           |
|                 |                   |                   | . |           |
|                 |                   |                   | 2 |           |
|                 |                   |                   | ( |           |
|                 |                   |                   | 1 |           |
|                 |                   |                   | 8 |           |
|                 |                   |                   | ) |           |
+-----------------+-------------------+-------------------+---+-----------+
| Wechselobligo   | 0                 | 0                 | n |           |
|                 |                   |                   | 1 |           |
|                 |                   |                   | 8 |           |
|                 |                   |                   | ( |           |
|                 |                   |                   | 1 |           |
|                 |                   |                   | 5 |           |
|                 |                   |                   | V |           |
|                 |                   |                   | . |           |
|                 |                   |                   | 2 |           |
|                 |                   |                   | N |           |
|                 |                   |                   | ) |           |
+-----------------+-------------------+-------------------+---+-----------+
| Staaten-Nummer  | 0                 | 0                 | n |           |
|                 |                   |                   | 4 |           |
+-----------------+-------------------+-------------------+---+-----------+
| Fi              | 0                 | 0                 | n |           |
| pKurz-Zahlmodus |                   |                   | 2 |           |
+-----------------+-------------------+-------------------+---+-----------+
| VarCode1        | 0                 | 0                 | n |           |
|                 |                   |                   | 4 |           |
+-----------------+-------------------+-------------------+---+-----------+
| UmstKonto       | 0                 | 0                 | n |           |
|                 |                   |                   | 9 |           |
+-----------------+-------------------+-------------------+---+-----------+
| Platzhalter     | 0                 | 0                 | n |           |
|                 |                   |                   | 6 |           |
|                 |                   |                   | 0 |           |
+-----------------+-------------------+-------------------+---+-----------+
| Platzhalter     | 0                 | 0                 | n |           |
|                 |                   |                   | 8 |           |
|                 |                   |                   | 5 |           |
+-----------------+-------------------+-------------------+---+-----------+
| DL-Code         | 0                 | 0                 | n |           |
|                 |                   |                   | 4 |           |
+-----------------+-------------------+-------------------+---+-----------+
| NTCS            | 0                 | 0                 | n |           |
| Kontogruppe     |                   |                   | 1 |           |
+-----------------+-------------------+-------------------+---+-----------+
| Zweitwährung    | 0                 | 0                 | n |           |
|                 |                   |                   | 4 |           |
+-----------------+-------------------+-------------------+---+-----------+
| Freifeld alpha  | d                 | kr                | a |           |
| 1               | ebitor_fgr.fgr_cd | editor_fgr.fgr_cd | 2 |           |
|                 | where fgrart_cd = | where fgrart_cd = | 0 |           |
|                 | ‚dalf1'           | ‚kalf1'           |   |           |
+-----------------+-------------------+-------------------+---+-----------+
| Freifeld alpha  | d                 | kr                | a |           |
| 2               | ebitor_fgr.fgr_cd | editor_fgr.fgr_cd | 2 |           |
|                 | where fgrart_cd = | where fgrart_cd = | 0 |           |
|                 | ‚dalf2'           | ‚kalf2'           |   |           |
+-----------------+-------------------+-------------------+---+-----------+
| Freifeld alpha  | d                 | kr                | a |           |
| 3               | ebitor_fgr.fgr_cd | editor_fgr.fgr_cd | 1 |           |
|                 | where fgrart_cd = | where fgrart_cd = |   |           |
|                 | ‚dalf3'           | ‚kalf2'           |   |           |
+-----------------+-------------------+-------------------+---+-----------+
| Freifeld1       | d                 | kr                | n |           |
|                 | ebitor_fgr.fgr_cd | editor_fgr.fgr_cd | 1 |           |
|                 | where fgrart_cd = | where fgrart_cd = | 8 |           |
|                 | ‚dnum1'           | ‚knum1'           | ( |           |
|                 |                   |                   | 1 |           |
|                 |                   |                   | 5 |           |
|                 |                   |                   | V |           |
|                 |                   |                   | . |           |
|                 |                   |                   | 2 |           |
|                 |                   |                   | N |           |
|                 |                   |                   | ) |           |
+-----------------+-------------------+-------------------+---+-----------+
| Freifeld2       | d                 | kr                | n |           |
|                 | ebitor_fgr.fgr_cd | editor_fgr.fgr_cd | 1 |           |
|                 | where fgrart_cd = | where fgrart_cd = | 8 |           |
|                 | ‚dnum2'           | ‚knum2'           | ( |           |
|                 |                   |                   | 1 |           |
|                 |                   |                   | 5 |           |
|                 |                   |                   | V |           |
|                 |                   |                   | . |           |
|                 |                   |                   | 2 |           |
|                 |                   |                   | N |           |
|                 |                   |                   | ) |           |
+-----------------+-------------------+-------------------+---+-----------+
| Freifeld3       | d                 | kr                | n |           |
|                 | ebitor_fgr.fgr_cd | editor_fgr.fgr_cd | 4 |           |
|                 | where fgrart_cd = | where fgrart_cd = |   |           |
|                 | ‚dnum3'           | ‚knum3'           |   |           |
+-----------------+-------------------+-------------------+---+-----------+
| Varcode2        | 0                 | 0                 | n |           |
|                 |                   |                   | 9 |           |
+-----------------+-------------------+-------------------+---+-----------+
| FW-Code         | 0                 | 0                 | n |           |
|                 |                   |                   | 4 |           |
+-----------------+-------------------+-------------------+---+-----------+
| Landkennzeichen | 0                 | 0                 | n |           |
|                 |                   |                   | 4 |           |
+-----------------+-------------------+-------------------+---+-----------+
| EB-Buchkonto    | 0                 | 0                 | n |           |
|                 |                   |                   | 9 |           |
+-----------------+-------------------+-------------------+---+-----------+
| Buchungssperre  | 0                 | 0                 | n |           |
|                 |                   |                   | 2 |           |
+-----------------+-------------------+-------------------+---+-----------+
| EB-Übernahme Kz | 0                 | 0                 | n |           |
|                 |                   |                   | 2 |           |
+-----------------+-------------------+-------------------+---+-----------+
| L               | 0                 | 0                 | n |           |
| öschkennzeichen |                   |                   | 1 |           |
+-----------------+-------------------+-------------------+---+-----------+
| Kontrollzeichen | \*                | \*                | a |           |
|                 |                   |                   | 1 |           |
+-----------------+-------------------+-------------------+---+-----------+

Updates

-   Am Ende der Verarbeitung muss das letzte Überleitungsdatum am
    Firmenstamm gesetzt werden (Datum wird vor dem Retrieve der Daten
    bestimmt)

#### Ausgabe BMD-Belege

Auswahldialog

-   Firma (p)

-   Verzeichnis + Dateiname der FibuBelegschnittstelle (p)

-   Verzeichnis + Dateiname (ohne JobNr) der Backupdatei (p)

-   Buchungszweige (p)

-   v - Verkauf

-   e - Einkauf

-   k -- Kassa

-   jede Kombination der angeführten Werte ist gültig

-   Belegdatum für Kassa-Buchungen

-   KassaFibuProtokoll drucken ja/nein (p)

-   eigenes File je Jahr (p)

-   wenn "j", dann besteht die Ausgabe aus 1 Transaktion(kein
    > Restart); wird ein File mit fortlaufender Nummerierung erstellt.

-   Header-Sätze bestehend aus

-   Vorlaufsatz(p)

Ablauf allgemein

-   alle noch nicht übergeleiteten Rechnungen (AR, ER, BN) werden unter
    Berücksichtigung des Verbuchungszeitraums lt. Firmenstamm ausgegeben

-   ist die FibuÜberleitungs-JobNummer am Firmenstamm
    [fa.fbueb_job_nr] <> 0, ist automatisch "Restart" als
    Verarbeitungsart eingeschaltet

-   bei Restart

-   die Backupdatei lt. BackupVerzeichnis + "_Vor_[JobNr]" wird
    > auf die FibuBelegschnittstelle zurückkopiert

-   bei Fehler sofortiges Programmende

-   locken der Backupdatei

-   bei Fehler sofortiges Programmende

-   umbenennen der Belegschnittstelle auf "tmp_schnittstelle.txt"

-   bei normaler Verarbeitung

-   Eintragen JobNr=aktuelle im Kennsatz

-   prüfen, ob Belegschnittstelle vorhanden

-   wenn nein, Anlage Belegschnittstelle mit Vorlaufsatz

-   kopieren Belegschnittstelle in BackupVerzeichnis +
    > "_Vor_[JobNr]"

-   bei Fehler sofortiges Programmende

-   locken der Backupdatei

-   umbenennen der Belegschnittstelle auf "tmp_schnittstelle.txt"

-   wenn Buchungszweig "Verkauf" ausgewählt

-   Transaktion je Verkaufsrechnung

-   es werden die Belege mit JobNr=0 lt. Auswahl und deren Datum dem
    > Datumsbereich lt. Firmenstamm entspricht gelesen

-   bei Restart werden zusätzlich die Verkaufsrechnungen verarbeitet,
    > welcher bereits der aktuellen JobNr zugeordnet sind

-   setzen JobNr in Vrech

-   Ausgabe Buchungen des Beleges in temporäre Schnittstelle

-   Aufruf Event für individuelle Buchungen zur aktuellen
    > Ausgangsrechnung

-   wenn Buchungszweig "Einkauf" ausgewählt

-   Transaktion je Einkaufsrechnung

-   es werden die Belege mit JobNr=0 lt. Auswahl und deren Datum dem
    > Datumsbereich lt. Firmenstamm entspricht gelesen

-   bei Restart werden zusätzlich die Einkaufsrechnungen verarbeitet,
    > welcher bereits der aktuellen JobNr zugeordnet sind

-   Ausgabe Buchungen des Beleges in temporäre Schnittstelle

-   Aufruf Event für individuelle Buchungen zur aktuellen
    > Eingangsrechnung

-   umbenennen der temporären Schnittstelle in Belegschnittstelle

-   kopieren Belegschnittstelle in BackupVerzeichnis +
    > "_Nach_[JobNr]"

-   eintragen JobNummer=0 im Kennsatz

-   Endemeldung des Programmes

Anmerkung

-   Die ASCII-Datei wird mit variabler Satzlänge und Trennzeichen ";"
    verwendet

-   die Datei wird im Zuge der Übernahme in die BMD-Fibu (durch die
    BMD-Fibu) gelöscht.

Dateiaufbau Verkauf / Einkauf

+---------------+-----------------+-----------------+-----------------+
|               | vrech           | erech           | erech_bn        |
+===============+=================+=================+=================+
| Kontonummer   | v               | er              | er              |
|               | rech.debitor_nr | ech.kreditor_nr | ech.kreditor_nr |
| (konto)       |                 |                 |                 |
+---------------+-----------------+-----------------+-----------------+
| Gegenkonto    | vr              | er              | er              |
|               | ech_kont.kto_nr | ech_kont.kto_nr | ech_kont.kto_nr |
| (gkto)        |                 |                 |                 |
+---------------+-----------------+-----------------+-----------------+
| Belegnummer   | vrech.vrech_nr  | erech.erech_nr  | erech           |
|               |                 | bzw.            | _bn.erech_bn_nr |
| (belegnr)     |                 | erech           |                 |
|               |                 | .erech_beleg_nr |                 |
+---------------+-----------------+-----------------+-----------------+
| Buchungsdatum | vrech.vrech_dat | erech.erech_dat | erech.erech_dat |
|               |                 |                 |                 |
| (buchdat)     |                 |                 |                 |
+---------------+-----------------+-----------------+-----------------+
| Belegdatum    | vrech.vrech_dat | erech.          | erech.          |
|               |                 | erech_beleg_dat | erech_beleg_dat |
| (belegdat)    |                 |                 |                 |
+---------------+-----------------+-----------------+-----------------+
| Buchungscode  | 1               | 2               | 2               |
|               |                 |                 |                 |
| (bucod)       |                 |                 |                 |
+---------------+-----------------+-----------------+-----------------+
| Steuercode    | ust_prz.ust_nr  | ust_prz.ust_nr  | ust_prz.ust_nr  |
|               |                 |                 |                 |
| (steucod)     |                 |                 |                 |
|               |                 |                 |                 |
| (mit          |                 |                 |                 |
| Vorlaufnull)  |                 |                 |                 |
+---------------+-----------------+-----------------+-----------------+
| Betrag in GW  | vrech_k         | erech_k         | erech_kont.u    |
| (0.00)        | ont.ust_basis + | ont.ust_basis + | st_basis_belast |
|               | vrec            | erec            | \* (1 + ust_prz |
| eventuell FW  | h_kont.ust_betr | h_kont.ust_betr | / 100) \* -1    |
| umrechnen     |                 | \* -1           |                 |
|               |                 |                 |                 |
| (betrag)      |                 |                 |                 |
+---------------+-----------------+-----------------+-----------------+
| Steu          | u               | u               | u               |
| erprozentsatz | st_prz.ust_proz | st_prz.ust_proz | st_prz.ust_proz |
| (00)          |                 | bzw.            |                 |
|               |                 | ust_prz         |                 |
| (mwst)        |                 | .erwerb_ust_prz |                 |
|               |                 | wenn            |                 |
|               |                 | liefsach.i      |                 |
|               |                 | nl_eu_drittl_kz |                 |
|               |                 | = \'e\'         |                 |
+---------------+-----------------+-----------------+-----------------+
| Steuer in GW  | vrec            | erec            | erech_kont.u    |
| (0.00)        | h_kont.ust_betr | h_kont.ust_betr | st_basis_belast |
|               | \* -1           |                 | \* (ust_prz /   |
| eventuell FW  |                 | muss bei        | 100)            |
| umrechnen     |                 | liefsach.i      |                 |
|               |                 | nl_eu_drittl_kz | muss bei        |
| (steuer)      |                 | = \'e\'         | liefsach.i      |
|               |                 | errechnet       | nl_eu_drittl_kz |
|               |                 | werden          | = \'e\'         |
|               |                 |                 | errechnet       |
|               |                 |                 | werden          |
+---------------+-----------------+-----------------+-----------------+
| Betrag in FW  | vrech_k         | erech_k         | erech_kont.u    |
| (0.00)        | ont.ust_basis + | ont.ust_basis + | st_basis_belast |
|               | vrec            | erec            | \* (1 + ust_prz |
| nur wenn      | h_kont.ust_betr | h_kont.ust_betr | / 100) \* -1    |
| waehrung_cd   |                 | \* -1           |                 |
| <>          |                 |                 |                 |
| g             |                 |                 |                 |
| w_waehrung_cd |                 |                 |                 |
|               |                 |                 |                 |
| (fwbetrag)    |                 |                 |                 |
+---------------+-----------------+-----------------+-----------------+
| Steuer in FW  | vrec            | erec            | erech_kont.u    |
| (0.00)        | h_kont.ust_betr | h_kont.ust_betr | st_basis_belast |
|               | \* -1           |                 | \* (ust_prz /   |
| nur wenn      |                 | muss bei        | 100)            |
| waehrung_cd   |                 | liefsach.i      |                 |
| <>          |                 | nl_eu_drittl_kz | muss bei        |
| g             |                 | = \'e\'         | liefsach.i      |
| w_waehrung_cd |                 | errechnet       | nl_eu_drittl_kz |
|               |                 | werden          | = \'e\'         |
| (fwsteuer)    |                 |                 | errechnet       |
|               |                 |                 | werden          |
+---------------+-----------------+-----------------+-----------------+
| Buchungstext  | vrec            | erec            | erec            |
|               | h_kont.buch_txt | h_kont.buch_txt | h_kont.buch_txt |
| (text)        |                 |                 |                 |
+---------------+-----------------+-----------------+-----------------+
| Nettotage     | vrech.netto_tg  | erech.netto_tg  | erech.netto_tg  |
| (000)         |                 |                 |                 |
|               |                 |                 |                 |
| (zziel)       |                 |                 |                 |
+---------------+-----------------+-----------------+-----------------+
| 1.           | vr              | er              | er              |
| Skon          | ech.skonto1_prz | ech.skonto1_prz | ech.skonto1_prz |
| toprozentsatz |                 |                 |                 |
| (0.00)        |                 |                 |                 |
|               |                 |                 |                 |
| (skontopz)    |                 |                 |                 |
+---------------+-----------------+-----------------+-----------------+
| Zieltage      | v               | e               | e               |
|               | rech.skonto1_tg | rech.skonto1_tg | rech.skonto1_tg |
| (skontotage)  |                 |                 |                 |
+---------------+-----------------+-----------------+-----------------+
| 2.           | vr              | er              | er              |
| Skon          | ech.skonto2_prz | ech.skonto2_prz | ech.skonto2_prz |
| toprozentsatz |                 |                 |                 |
| (0.00)        |                 |                 |                 |
|               |                 |                 |                 |
| (skontopz2)   |                 |                 |                 |
+---------------+-----------------+-----------------+-----------------+
| Zieltage      | v               | e               | e               |
|               | rech.skonto2_tg | rech.skonto2_tg | rech.skonto2_tg |
| (skontotage2) |                 |                 |                 |
+---------------+-----------------+-----------------+-----------------+
| Symbol        | fa.fb_ar_sy     | erech           | erech           |
|               | bzw.            | art_fa.fb_er_sy | art_fa.fb_bn_sy |
| (symbol)      | fa.fb_gu_sy     | bzw.            |                 |
|               |                 | erech           |                 |
|               |                 | art_fa.fb_eg_sy |                 |
+---------------+-----------------+-----------------+-----------------+
| GegenbuchKz   | E               | E               | E               |
|               |                 |                 |                 |
| (gegenbuchkz) |                 |                 |                 |
+---------------+-----------------+-----------------+-----------------+
| VerbuchungsKz | A               | A               | A               |
|               |                 |                 |                 |
| (verbuchkz)   |                 |                 |                 |
+---------------+-----------------+-----------------+-----------------+
| Kostenstelle  | vr              | er              | er              |
|               | ech_kont.kst_nr | ech_kont.kst_nr | ech_kont.kst_nr |
| (kost)        |                 |                 |                 |
+---------------+-----------------+-----------------+-----------------+
| Kostenträger  | vr              | er              | er              |
|               | ech_kont.ktr_nr | ech_kont.ktr_nr | ech_kont.ktr_nr |
| (kotraeger)   |                 |                 |                 |
+---------------+-----------------+-----------------+-----------------+
| skonto        | 0               | 0               | 0               |
+---------------+-----------------+-----------------+-----------------+

Dateiaufbau Kassabuchungen

KassaKd = ka_bst.kunde_cd

KassaFil = kassa.fil_nr

PosArtik = ka_bel_pos.artik_cd

+---------------+------------------+-----------------+----------------+
|               | **Erlöse**       | **Rundun        | **Zahlungen    |
|               |                  | gsdifferenzen** | Barverkauf**   |
|               |                  |                 |                |
|               |                  |                 | ka_            |
|               |                  |                 | kartei.bel_art |
|               |                  |                 | in             |
|               |                  |                 | (\'B\',\'A\')  |
|               |                  |                 |                |
|               |                  |                 | event. 2x      |
|               |                  |                 |                |
|               |                  |                 | a              |
|               |                  |                 | Betrag+        |
|               |                  |                 | Skonto-positiv |
|               |                  |                 |                |
|               |                  |                 | b.Betrag+      |
|               |                  |                 | Skonto-negativ |
+===============+==================+=================+================+
| konto         | kunde.debitor_nr | k               | ku             |
|               |                  | unde.debitor_nr | nde.debitor_nr |
|               | < KassaKd       |                 |                |
|               |                  | < KassaKd      | < KassaKd     |
+---------------+------------------+-----------------+----------------+
| gkto          | erl. erlkto_nr   | erl. erlkto_nr  | ka             |
|               |                  |                 | _bst.kassa_kto |
|               | < KassaFil      | < KassaFil     |                |
|               |                  |                 |                |
|               | <               | <              |                |
|               | PosArti          | ka              |                |
|               | k...artikerl_cd | _fa.artikerl_cd |                |
|               |                  |                 |                |
|               | <               | <              |                |
|               | KassaK           | KassaKd         |                |
|               | d...kundeerl_cd | ...kundeerl_cd |                |
|               |                  |                 |                |
|               | (so auch ust_cd  | (so auch ust_cd |                |
|               | ermitteln!)      | ermitteln!)     |                |
+---------------+------------------+-----------------+----------------+
| belegnr       | lfd.aus          | lfd.aus         | lfd.aus        |
|               | [nummern] pro  | [nummern] pro | [nummern]    |
|               |                  |                 | pro            |
|               | Tag und          | Tag und         |                |
|               | Sachbearbeiter   | Sachbearbeiter  | Tag und        |
|               |                  |                 | Sachbearbeiter |
+---------------+------------------+-----------------+----------------+
| buchdat       | k                | ka              | ka_            |
|               | a_kartei.bel_dat | _kartei.bel_dat | kartei.bel_dat |
+---------------+------------------+-----------------+----------------+
| belegdat      | k                | ka              | ka_            |
|               | a_kartei.bel_dat | _kartei.bel_dat | kartei.bel_dat |
+---------------+------------------+-----------------+----------------+
| bucod         | 1                | 1               | 2              |
+---------------+------------------+-----------------+----------------+
| steucod       | Integer(         | Integer(u       | 0              |
|               | ust_proz.ust_nr) | st_proz.ust_nr) |                |
+---------------+------------------+-----------------+----------------+
| betrag (in    | sum(ka_bel_      | sum(ka_ka       | ka             |
| GW)           | pos.pos_wert_iu) | rtei.rund_diff) | _kartei.betrag |
|               |                  |                 | \* -1          |
+---------------+------------------+-----------------+----------------+
| mwst          | ust_proz.ust_prz | u               | 0              |
|               |                  | st_proz.ust_prz |                |
+---------------+------------------+-----------------+----------------+
| steuer (in    | sum(ka_bel       | sum(ka_ka       | 0              |
| GW)           | _pos.pos_wert_iu | rtei.rund_diff) |                |
|               |                  |                 |                |
|               | -               | \* -1           |                |
|               | ka_b             |                 |                |
|               | el_pos.fibu_ums) |                 |                |
|               | \* -1            |                 |                |
+---------------+------------------+-----------------+----------------+
| fwbetrag      | 0                | 0               | 0              |
| (n.w.FW)      |                  |                 |                |
+---------------+------------------+-----------------+----------------+
| fwsteuer      | 0                | 0               | 0              |
| (n.w.FW)      |                  |                 |                |
+---------------+------------------+-----------------+----------------+
| text          | ka_bst.          | ka_bst.         | ka_bst.        |
|               | ka_kabst_cd      | ka_kabst_cd     | ka_kabst_cd    |
|               |                  |                 |                |
|               | \+ \' \' +       | \+ \' \' +      | \+ \' \' +     |
|               | ka_bst.          | ka_bst.         | ka_bst.        |
|               | ka_sbbst_cd      | ka_sbbst_cd     | ka_sbbst_cd    |
+---------------+------------------+-----------------+----------------+
| zziel         | 1                | 1               | 14             |
+---------------+------------------+-----------------+----------------+
| skontopz      | 0                | 0               | 0              |
+---------------+------------------+-----------------+----------------+
| skontotage    | 0                | 0               | 0              |
+---------------+------------------+-----------------+----------------+
| skontopz2     | 0                | 0               | 0              |
+---------------+------------------+-----------------+----------------+
| skontotage2   | 0                | 0               | 0              |
+---------------+------------------+-----------------+----------------+
| symbol        | ka_fa.fb_bv_sy   | ka_fa.fb_bv_sy  | ka_fa.fb_za_sy |
+---------------+------------------+-----------------+----------------+
| gegenbuchkz   | E                | E               | E              |
+---------------+------------------+-----------------+----------------+
| verbuchkz     | A                | A               | A              |
+---------------+------------------+-----------------+----------------+
| kost          | kst.kst_nr       | kst.kst_nr      | lfd.aus        |
|               |                  |                 | [nummern]    |
|               | < KassaFil      | < KassaFil     | pro            |
|               |                  |                 |                |
|               | < PosArtik...  | <              | Tag und        |
|               | artikkst_cd      | ka              | Sachbearbeiter |
|               |                  | _fa.artikkst_cd |                |
|               | < KassaKd...   |                 |                |
|               | kundekst_cd      | < KassaKd...  |                |
|               |                  | kundekst_cd     |                |
+---------------+------------------+-----------------+----------------+
| kotraeger     | kst.ktr_nr       | kst.ktr_nr      | 0              |
|               |                  |                 |                |
|               | < KassaFil      | < KassaFil     |                |
|               |                  |                 |                |
|               | < PosArtik...  | <              |                |
|               | artikkst_cd      | ka              |                |
|               |                  | _fa.artikkst_cd |                |
|               | < KassaKd...   |                 |                |
|               | kundekst_cd      | < KassaKd...  |                |
|               |                  | kundekst_cd     |                |
+---------------+------------------+-----------------+----------------+
| skonto        | 0                | 0               | ka_karte       |
|               |                  |                 | i_zp.betrag_gw |
|               |                  |                 |                |
|               |                  |                 | (ka_zahlu      |
|               |                  |                 | ng.zahlung_art |
|               |                  |                 | = \'S\')       |
+---------------+------------------+-----------------+----------------+

+---------------+------------------+------------------+---------------+
|               | **Rech           | **Abschöpfung**  |               |
|               | nungsausgleich** |                  |               |
|               |                  |                  |               |
|               | k                |                  |               |
|               | a_kartei.bel_art |                  |               |
|               | = \'R\'          |                  |               |
+===============+==================+==================+===============+
| konto         | vrech.debitor_nr | ka_bs            |               |
|               |                  | t_zahlung.fb_kto |               |
|               | < ka_bel_vrech  |                  |               |
|               |                  | (hier auch       |               |
|               |                  | ka_bs            |               |
|               |                  | t_zahlung.ust_cd |               |
|               |                  |                  |               |
|               |                  | ermitteln)       |               |
+---------------+------------------+------------------+---------------+
| gkto          | ka_bst.kassa_kto | ka_bst.kassa_kto |               |
+---------------+------------------+------------------+---------------+
| belegnr       | ka_bel.bel_nr    | lfd.aus          |               |
|               |                  | [nummern] pro  |               |
|               |                  |                  |               |
|               |                  | Tag und          |               |
|               |                  | Sachbearbeiter   |               |
+---------------+------------------+------------------+---------------+
| buchdat       | k                | k                |               |
|               | a_kartei.bel_dat | a_kartei.bel_dat |               |
+---------------+------------------+------------------+---------------+
| belegdat      | k                | k                |               |
|               | a_kartei.bel_dat | a_kartei.bel_dat |               |
+---------------+------------------+------------------+---------------+
| bucod         | 2                | 1                |               |
+---------------+------------------+------------------+---------------+
| steucod       | 0                | Integer(         |               |
|               |                  | ust_proz.ust_nr) |               |
+---------------+------------------+------------------+---------------+
| betrag (in    | ka_bel           | sum(ka_kart      |               |
| GW)           | _vrech.zahl_betr | ei_zp.betrag_gw) |               |
|               |                  |                  |               |
|               | \+               | < bei manueller |               |
|               | ka_bel_v         | Abschöpfung \*   |               |
|               | rech.skonto_betr | -1               |               |
|               |                  |                  |               |
|               | \* -1            | < bei           |               |
|               |                  | K                |               |
|               |                  | reditorenbuchung |               |
|               |                  | \* -1            |               |
+---------------+------------------+------------------+---------------+
| mwst          | 0                | ust_proz.ust_prz |               |
+---------------+------------------+------------------+---------------+
| steuer (in    | 0                | 0                |               |
| GW)           |                  |                  |               |
+---------------+------------------+------------------+---------------+
| fwbetrag      | 0                | sum(ka_k         |               |
| (n.w.FW)      |                  | artei_zp.betrag) |               |
|               |                  |                  |               |
|               |                  | < bei manueller |               |
|               |                  | Abschöpfung \*   |               |
|               |                  | -1               |               |
|               |                  |                  |               |
|               |                  | < bei           |               |
|               |                  | K                |               |
|               |                  | reditorenbuchung |               |
|               |                  | \* -1            |               |
+---------------+------------------+------------------+---------------+
| fwsteuer      | 0                | 0                |               |
| (n.w.FW)      |                  |                  |               |
+---------------+------------------+------------------+---------------+
| text          | ka_bst.          | ka_bst.          |               |
|               | ka_kabst_cd      | ka_kabst_cd      |               |
|               |                  |                  |               |
|               | \+ \' \' +       | \+ \' \' +       |               |
|               | ka_bst.          | ka_bst.          |               |
|               | ka_sbbst_cd      | ka_sbbst_cd      |               |
+---------------+------------------+------------------+---------------+
| zziel         | 14               | 1                |               |
+---------------+------------------+------------------+---------------+
| skontopz      | 0                | 0                |               |
+---------------+------------------+------------------+---------------+
| skontotage    | 0                | 0                |               |
+---------------+------------------+------------------+---------------+
| skontopz2     | 0                | 0                |               |
+---------------+------------------+------------------+---------------+
| skontotage2   | 0                | 0                |               |
+---------------+------------------+------------------+---------------+
| symbol        | ka_fa.fb_ra_sy   | ka_bst_zah       |               |
|               |                  | lung.fb_absch_sy |               |
+---------------+------------------+------------------+---------------+
| gegenbuchkz   | E                | E                |               |
+---------------+------------------+------------------+---------------+
| verbuchkz     | A                | A                |               |
+---------------+------------------+------------------+---------------+
| kost          | ka               | 0                |               |
|               | _bel_vrech.op_nr |                  |               |
+---------------+------------------+------------------+---------------+
| kotraeger     | 0                | 0                |               |
+---------------+------------------+------------------+---------------+
| skonto        | ka_bel_v         | 0                |               |
|               | rech.skonto_betr |                  |               |
+---------------+------------------+------------------+---------------+

Updates

-   Für jede Buchung "Erlöse" und "Rundungsdifferenzen" muss ein
    Datensatz in der Tabelle [ka_fibu_erloes] angelegt bzw. upgedatet
    werden.  
    Im Falle des Restarts müssen bereits getätigte Einträge gelöscht
    werden.

-   Für jede Buchung "Kassa Zahlungen Barverkauf" und
    "Rechnungsausgleich" muss ein Datensatz in die Tabelle
    [ka_fibu_zahl] geschrieben werden.  
    Im Falle des Restarts müssen bereits getätigte Einträge gelöscht
    werden.

-   Am Ende der Verarbeitung muss das letzte Überleitungsdatum am
    Firmenstamm gesetzt werden (Datum wird vor dem Retrieve der Daten
    bestimmt)

#### OP-Import BMD

Auswahldialog

-   Firma (p)

-   Dateiname der Importdatei (p)

-   Offset (p)

Ablauf allgemein

-   Öffnen der Datei

-   wenn keine Datei vorhanden ist Ende

-   Löschen der Tabelle pfufb_op

-   Überlesen von Offset-Zeilen

-   Pro Zeile Aufbau pfufb_op-Satz

-   Schliessen der Datei

-   Löschen der Datei

Dateiaufbau

-   Felder mit ";" getrennt

-   Vorlauf-Blanks entfernen

-   Debitorennummer

-   Buchungsdatum

-   Belegdatum

-   Belegnummer

-   Buchungsbetrag

-   Skontobetrag

-   offener Betrag

-   Symbol

-   Mahnstufe

-   Zieltage

### Integration EuroFib

#### Ausgabe EuroFib -Stammdaten

Ablauf allgemein

-   Update erfolgt ONLINE sofort nach dem Speichern von Debitor bzw.
    Kreditor in TradeControl

-   Daten werden über UserObject cst_eurofib_konten in die Fibu
    geschrieben

-   die kritischen pfu_col-Dimensionen (z.B: Adressfelder, Matchcode)
    > müssen in TC auf EURO-FIB-Dimensionen angepasst werden
    > (SetDimensionenEUROFIB.sql)

Tabellenaufbau

-   Felder, die nicht beschrieben sind, werden nicht upgedated (sind in
    EURO-FIB nullfähig bzw. haben Datenbankdefaultwert)

-   es gibt eine eigene Personenkonten-Vorschlagstabelle [pkv_eurofib]
    für die EURO- FIB, in der Folge nur mehr [pkv] genannt

+-------------+--------------+--------------+----------------+--------+
|             |              | **s          | **K            |        |
|             |              | esfibu.kon** | ontrolltabelle |        |
|             |              |              | Kontonummern** |        |
|             |              |              |                |        |
|             |              |              | -   **nur bei  |        |
|             |              |              |     der        |        |
|             |              |              |                |        |
|             |              |              |    Neuanlage** |        |
+=============+==============+==============+================+========+
| Column      | Beschreibung | Debitor      | Kreditor       | Type   |
+-------------+--------------+--------------+----------------+--------+
|             |              |              |                |        |
+-------------+--------------+--------------+----------------+--------+
| kon_klient  | Man          | fa_nr        | fa_nr          | n      |
| (p1)        | dantennummer |              |                | umeric |
|             |              |              |                | (4,0)  |
+-------------+--------------+--------------+----------------+--------+
| kon_konto   | Kontonummer  | debitor_nr   | kreditor_nr    | vc     |
| (p2)        |              |              |                | har(8) |
+-------------+--------------+--------------+----------------+--------+
| kon_sa (p3) | Satzart      | 2            | 3              | n      |
|             |              |              |                | umeric |
|             | 1 = Sach, 2  |              |                | (2,0)  |
|             | = Debitor, 3 |              |                |        |
|             | = Kreditor   |              |                |        |
+-------------+--------------+--------------+----------------+--------+

+-------------+--------------+--------------+---------------+---------+
|             |              | **sesfibu    | **Debitoren   |         |
|             |              | .debitoren** | u.            |         |
|             |              |              | Kred          |         |
|             |              |              | itorenstamm** |         |
+=============+==============+==============+===============+=========+
| Column      | Beschreibung | Debitor      | Kreditor      | Type    |
+-------------+--------------+--------------+---------------+---------+
|             |              |              |               |         |
+-------------+--------------+--------------+---------------+---------+
| kod_klient  |              | d            | k             | numeric |
| (p1)        |              | ebitor.fa_nr | reditor.fa_nr | (4,0)   |
+-------------+--------------+--------------+---------------+---------+
| kod_konto   |              | debito       | kredito       | v       |
| (p2)        |              | r.debitor_nr | r.kreditor_nr | char(8) |
+-------------+--------------+--------------+---------------+---------+
| kod_sa      |              | 2            | 3             | numeric |
|             |              |              |               | (2,0)   |
+-------------+--------------+--------------+---------------+---------+
| ko          | Matchcode    | de           | kr            | vc      |
| d_matchcode |              | bitor.debito | editor.kredit | har(20) |
|             |              | r_mc[1:20] | or_mc[1:20] |         |
|             |              |              |               |         |
|             |              | -   upshift  | -   upshift   |         |
+-------------+--------------+--------------+---------------+---------+
| kod_plan    | Kontenplan   | "N"        |               | v       |
|             | (J/N)        |              |               | char(1) |
|             |              | -            |               |         |
|             | -   nur bei  |              |               |         |
|             |     der      |              |               |         |
|             |              |              |               |         |
|             |    Neuanlage |              |               |         |
+-------------+--------------+--------------+---------------+---------+
| kod_aktiv   | Konto        | "J"        |               | v       |
|             | gesperrt     |              |               | char(1) |
|             | (J/N)        |              |               |         |
|             |              |              |               |         |
|             | -   nur bei  |              |               |         |
|             |     der      |              |               |         |
|             |              |              |               |         |
|             |    Neuanlage |              |               |         |
+-------------+--------------+--------------+---------------+---------+
| k           | Konto ist    | d            | kreditor.     | v       |
| od_diverser | divers (J/N) | ebitor.debit | kredi         | char(1) |
|             |              | or_divers_jn | tor_divers_jn |         |
|             |              |              |               |         |
|             |              | -   upshift  | upshift       |         |
+-------------+--------------+--------------+---------------+---------+
| kod_zuname  | Zuname       | adr.n        |               | vc      |
|             | (Name1)      | ame1[1:40] |               | har(40) |
+-------------+--------------+--------------+---------------+---------+
| kod_name2   | Name2        | adr.n        |               | vc      |
| +n          |              | ame2[1:40] |               | har(40) |
+-------------+--------------+--------------+---------------+---------+
| kod_strasse | Straße       | adr.strasse  |               | vc      |
| +n          |              |              |               | har(80) |
+-------------+--------------+--------------+---------------+---------+
| kod_land    | Land         | adr.land_cd  |               | v       |
|             |              |              |               | char(3) |
+-------------+--------------+--------------+---------------+---------+
| kod_plz +n  | Postleitzahl | adr.plz      |               | vc      |
|             |              |              |               | har(16) |
+-------------+--------------+--------------+---------------+---------+
| kod_ort +n  | Ort          | adr.ort      |               | vc      |
|             |              |              |               | har(80) |
+-------------+--------------+--------------+---------------+---------+
| kod_telefon | Telefon      | a            |               | vc      |
| +n          |              | dr_pers_komi |               | har(30) |
|             |              | d.komid_wert |               |         |
|             |              | [1:30]     |               |         |
|             |              | where        |               |         |
|             |              | komidart_kz  |               |         |
|             |              | = \'t\',     |               |         |
|             |              | 1.Row order  |               |         |
|             |              | by sort_nr   |               |         |
+-------------+--------------+--------------+---------------+---------+
| kod_telefax | Fax          | w.o.         |               | vc      |
| +n          |              | komidart_kz  |               | har(30) |
|             |              | = \'f\'      |               |         |
+-------------+--------------+--------------+---------------+---------+
| kod_email   | e            | w.o.         |               | vc      |
| +n          | Mail-Adresse | komidart_kz  |               | har(60) |
|             |              | = \'e\'      |               |         |
+-------------+--------------+--------------+---------------+---------+
| kod_uid +n  | UID-Nummer   | d            | k             | vc      |
|             |              | ebitor.ustid | reditor.ustid | har(15) |
+-------------+--------------+--------------+---------------+---------+
| kod_        | Samme        | pkv.kod      |               | numeric |
| sammelkonto | lkontonummer | _sammelkonto |               | (3,0)   |
+-------------+--------------+--------------+---------------+---------+
| kod_fwcd    | Währung      | debitor.     | kredito       | var     |
|             |              | waehrung_ccd | r.waehrung_cd | char(3) |
+-------------+--------------+--------------+---------------+---------+
| kod_netto   | Nettotage    | zahlk        |               | numeric |
|             |              | ond.netto_tg |               | (4,0)   |
+-------------+--------------+--------------+---------------+---------+
| kod_sktage1 | Skontotage 1 | zahlkon      |               | numeric |
|             |              | d.skonto1_tg |               | (4,0)   |
+-------------+--------------+--------------+---------------+---------+
| kod_skproz1 | S            | zahlkond     |               | numeric |
|             | kontoprozent | .skonto1_prz |               | (4,2)   |
|             | 1            |              |               |         |
+-------------+--------------+--------------+---------------+---------+
| kod_sktage2 | Skontotage 2 | zahlkon      |               | numeric |
|             |              | d.skonto2_tg |               | (4,0)   |
+-------------+--------------+--------------+---------------+---------+
| kod_skproz2 | S            | zahlkond     |               | numeric |
|             | kontoprozent | .skonto2_prz |               | (4,2)   |
|             | 2            |              |               |         |
+-------------+--------------+--------------+---------------+---------+
| k           | Mahnkennung  | debitor.mh   | pkv.m         | v       |
| od_mahnkenn |              | ktosperre_kz | hktosperre_kz | char(1) |
|             | J=mit        |              |               |         |
|             | Mahnung,     |              |               |         |
|             | K=nur        |              |               |         |
|             | Kontoauszug, |              |               |         |
|             | S            |              |               |         |
|             | =Mahn-sperre |              |               |         |
+-------------+--------------+--------------+---------------+---------+
| kod         | Mahnspes     | pkv.ko       | pkv.k         | v       |
| _mahnspesen | enberechnung | d_mahnspesen | od_mahnspesen | char(1) |
|             | (J/N)        |              |               |         |
+-------------+--------------+--------------+---------------+---------+
| kod_verzug  | Verzugszins  | pk           | p             | v       |
|             | enberechnung | v.kod_verzug | kv.kod_verzug | char(1) |
|             | (J/N)        |              |               |         |
+-------------+--------------+--------------+---------------+---------+
| kod         | Ver          | pkv.ko       | pkv.k         | v       |
| _verzugrech | zugsrechnung | d_verzugrech | od_verzugrech | char(1) |
|             | (J/N)        |              |               |         |
+-------------+--------------+--------------+---------------+---------+
| ko          | Intervall    | pkv.k        | pkv.          | numeric |
| d_intervall | Mahnung in   | od_intervall | kod_intervall | (3,0)   |
|             | Tg           |              |               |         |
+-------------+--------------+--------------+---------------+---------+
| k           | Mahnungsart  | debitor.     | pkv.          | numeric |
| od_mahn_art |              | kod_mahn_art | kod_mahn_art  | (3,0)   |
|             | 1=Druck      |              |               |         |
|             |              |              |               |         |
|             | 2=Fax        |              |               |         |
|             |              |              |               |         |
|             | 3=Mail       |              |               |         |
+-------------+--------------+--------------+---------------+---------+
| k           | Faxnummer f. | debitor.     | NULL          | vc      |
| od_mahn_fax | Mahnung      | kod_mahn_fax |               | har(50) |
| +n          |              |              |               |         |
+-------------+--------------+--------------+---------------+---------+
| ko          | eMailadresse | debitor.k    | NULL          | vc      |
| d_mahn_mail | f. Mahnung   | od_mahn_mail |               | har(50) |
| +n          |              |              |               |         |
+-------------+--------------+--------------+---------------+---------+
| kod_klimit  | Kreditlimit  | debitor      | pk            | numeri  |
|             |              | .kreditlimit | v.kreditlimit | c(18,0) |
|             | -            |              |               |         |
|             |   ganzzahlig |              |               |         |
|             |     gerundet |              |               |         |
+-------------+--------------+--------------+---------------+---------+
| kod_zession | Zession      | pkv          | pk            | numer   |
|             | skennzeichen | .kod_zession | v.kod_zession | ic(3,0) |
+-------------+--------------+--------------+---------------+---------+
| ko          | Vertreter    | debitor.k    | pkv.          | numer   |
| d_vertreter |              | od_vertreter | kod_vertreter | ic(4,0) |
+-------------+--------------+--------------+---------------+---------+
| kod_sprache | Sprachcode   | pkv          | pk            | numer   |
|             |              | .kod_sprache | v.kod_sprache | ic(3,0) |
+-------------+--------------+--------------+---------------+---------+
| ko          | Anlagedatum  | g            |               | date    |
| d_anlagedat |              | f_dt_current |               |         |
|             |              |              |               |         |
|             |              | -   nur      |               |         |
|             |              |              |               |         |
|             |              |    Neuanlage |               |         |
+-------------+--------------+--------------+---------------+---------+
| kod         | An           | pkv.ko       | pkv.k         | v       |
| _anlageuser | lagebenutzer | d_anlageuser | od_anlageuser | char(3) |
+-------------+--------------+--------------+---------------+---------+
| ko          | Än           | g            |               | date    |
| d_aenderdat | derungsdatum | f_dt_current |               |         |
+-------------+--------------+--------------+---------------+---------+
| kod         | Änder        | pkv.ko       | pkv.k         | v       |
| _aenderuser | ungsbenutzer | d_aenderuser | od_aenderuser | char(3) |
+-------------+--------------+--------------+---------------+---------+
| kod         | Ver          | pkv.ko       | pkv.k         | numer   |
| _verzug_tab | zugszinsenta | d_verzug_tab | od_verzug_tab | ic(3,0) |
|             | bellennummer |              |               |         |
+-------------+--------------+--------------+---------------+---------+
| kod_sel     | Selekti      | debito       | kredit        | vc      |
| e_[1\|6] | onskriterium | r_fgr.fgr_cd | or_fgr.fgr_cd | har(10) |
|             | 1-6          | where        | where         |         |
|             |              | fgrart_cd =  | fgrart_cd =   |         |
|             |              | "d_se       | "k_s         |         |
|             |              | le_[1\|6] | ele_[1\|6] |         |
+-------------+--------------+--------------+---------------+---------+
| kod         | Prü          | debitor.ko   | kreditor.k    | numer   |
| _uid_chk_nr | fkennzeichen | d_uid_chk_nr | od_uid_chk_nr | ic(3,0) |
|             | UID-Nummer   |              |               |         |
|             |              |              |               |         |
|             | 0=ungeprüft  |              |               |         |
|             |              |              |               |         |
|             | 1=Status 1   |              |               |         |
|             | (Nummer      |              |               |         |
|             | geprüft,     |              |               |         |
|             | Z            |              |               |         |
|             | ugehörigkeit |              |               |         |
|             | Debitor      |              |               |         |
|             | nicht)       |              |               |         |
|             |              |              |               |         |
|             | 2=Status 2   |              |               |         |
|             | (Nummer+Z    |              |               |         |
|             | ugehörigkeit |              |               |         |
|             | Debitor      |              |               |         |
|             | geprüft)     |              |               |         |
|             |              |              |               |         |
|             | 3 = ungültig |              |               |         |
+-------------+--------------+--------------+---------------+---------+
| kod_ui      | Prüfdatum zu | debit        | kredi         | date    |
| d_chk_datum | PrüfKz       | or.ustid_dat | tor.ustid_dat |         |
+-------------+--------------+--------------+---------------+---------+
| k           |              | N            | N             | v       |
| od_verzugop |              |              |               | char(1) |
+-------------+--------------+--------------+---------------+---------+
| kod_ver     |              | 0            | 0             | numer   |
| zugop_tabnr |              |              |               | ic(3,0) |
+-------------+--------------+--------------+---------------+---------+
| kod_xfi     |              | 0            | 0             | numer   |
| bu_mischkto |              |              |               | ic(3,0) |
+-------------+--------------+--------------+---------------+---------+

+-------------+--------------+--------------+---------------+---------+
|             |              | **sesfibu.z  | **Debitoren   |         |
|             |              | ahlungsdef** | u.            |         |
|             |              |              | Kr            |         |
|             |              |              | editorenstamm |         |
|             |              |              | Ban           |         |
|             |              |              | kverbindung** |         |
+=============+==============+==============+===============+=========+
| Column      | Beschreibung | Debitor      | Kreditor      | Type    |
+-------------+--------------+--------------+---------------+---------+
|             |              |              |               |         |
+-------------+--------------+--------------+---------------+---------+
| zah_klient  |              | d            | k             | numeric |
| (p1)        |              | ebitor.fa_nr | reditor.fa_nr | (4,0)   |
+-------------+--------------+--------------+---------------+---------+
| zah_konto   |              | debito       | kredito       | v       |
| (p2)        |              | r.debitor_nr | r.kreditor_nr | char(8) |
+-------------+--------------+--------------+---------------+---------+
| zah_nummer  | laufende     | debitor_b    | kreditor_     | numeric |
| (p3)        | Nummer je    | ank.zeile_nr | bank.zeile_nr | (3,0)   |
|             | Konto        |              |               |         |
+-------------+--------------+--------------+---------------+---------+
| zah_sa      |              | 2            | 3             | numeric |
|             |              |              |               | (2,0)   |
+-------------+--------------+--------------+---------------+---------+
| zah_art     | Zahlungsart  | debitor_     | kreditor      | v       |
|             |              | bank.zah_art | _bank.zah_art | char(1) |
|             | E=Einzug     |              |               |         |
|             |              |              |               |         |
|             | U            |              |               |         |
|             | =Überweisung |              |               |         |
|             |              |              |               |         |
|             | S=Scheck     |              |               |         |
+-------------+--------------+--------------+---------------+---------+
| z           | Name der     | b            |               | vc      |
| ah_bankname | Bank         | ank.bank_bez |               | har(40) |
+-------------+--------------+--------------+---------------+---------+
| z           | Bankleitzahl | debitor_b    | kreditor_     | vc      |
| ah_leitzahl |              | ank.bank_blz | bank.bank_blz | har(20) |
+-------------+--------------+--------------+---------------+---------+
| za          | Ban          | debitor_ba   | kreditor_b    | vc      |
| h_bankkonto | kkontonummer | nk.bankkonto | ank.bankkonto | har(35) |
+-------------+--------------+--------------+---------------+---------+
| zah_swift   | Swift-Code   | bank.bic     |               | vc      |
|             | Bank         |              |               | har(15) |
+-------------+--------------+--------------+---------------+---------+
| za          | Land der     | d            | kreditor_bank | v       |
| h_bank_land | Bank         | ebitor_bank. | .bank_land_cd | char(3) |
|             |              | bank_land_cd |               |         |
+-------------+--------------+--------------+---------------+---------+
| zah_iban_nr | IBAN         | debit        | kredi         | vc      |
| +n          |              | or_bank.iban | tor_bank.iban | har(35) |
+-------------+--------------+--------------+---------------+---------+
| zah_aktiv   | Aktiv im     | debitor_ba   | kreditor_b    | v       |
|             | Zah          | nk.zah_aktiv | ank.zah_aktiv | char(1) |
|             | lungsverkehr |              |               |         |
|             | (J/N)        |              |               |         |
+-------------+--------------+--------------+---------------+---------+

#### Ausgabe EuroFib-Belege

Auswwahlkriterien:

-   Firma (p)

-   Bis Datum (o)

-   Wenn angegeben werden nur Belege bis zu diesem Datum ausgegeben

-   Buchungszweig (p)

-   Kombination aus folgenden Buchstaben

-   v = Verkauf

-   e = Einkauf

-   k = Kassa

Allgemein

-   Pro Bereich wird ein Stapel in der EuroFib DB erstellt (Tabelle
    sesfibu.stapel)

-   Die Buchungen selbst werden in die Tabelle sesfibu.work_hauptbuch
    geschrieben

Verkauf

-   Eine Transaktion für alle Verkaufsbelegt

-   Es werden alle Rechnungen mit passenden Belegdatum und
    vfbueb_job_snr = 0 gelockt (Update vfbueb_job_snr auf JobNr \* -1).

-   Die so gelockten Rechnungen werden dann ausgegeben.

-   Es wird dabei ein Stapel pro fibufa_nr erstellt und freigegeben. Die
    fibufa_nr ist im TC-Standard mit der fa_nr belegt und kann im DS
    übersteuer werden.

Einkauf

Kassa

### Datanormschnittstelle Aufbau Tabellen

Auswahldialog

-   Firmennummer (p)

-   Datanormausgabegruppe (fpw)

-   Datum (p)

-   für Preisfindung maßgebliches Datum

-   Vorschlag=Tagesdatum

-   Erstbestückung (p)

-   Ja

-   Nein (=Vorschlag)

Allgemeines

-   Es werden DATNORM Files im Format DATANORM 5.0 ausgegeben.

-   Warengruppen und Rabatt werden immer vollständig ausgegeben, Bei
    Artikeln und Preisen werden nur Änderungen ausgegeben. Um diese
    ermitteln zu können werden die zuletzt ausgegebenen Daten in den
    dn_ Tabellen pro Datanormgruppe verpseichert.

-   Über eine Datanorgruppe können mehrer Kunden zusammengefasst werden,
    für die diese Änderungen gemeinsam Ermittelt werden, die aber auch
    immer gemeinsam (im gleichen Intervall) ausgegeben werden müssen.

Ablauf

-   Wiederanlauf = lt. [dn.restart_jn]

-   wenn Erstbestückung = Ja

-   lesen der ausgewählten Kunden aus Tabelle [kunde]

-   pro Kunde

-   kunde.dn_lfd_nr = 0

-   wenn Erstbestückung = Nein

-   folgender Ablauf erfolgt bis zu 2 x

-   in einem ersten Durchlauf für alle Kunden mit kunde.dn_lfd_nr > 0,
    > das sind jene Kunden für die eine "Updateausgabe" erfolgt; nur
    > für diesen Durchlauf wird der Umstand "Wiederanlauf" geprüft

-   in einem zweiten Durchlauf für alle Kunden mit kunde.dn_lfd_nr = 0,
    > das sind jene Kunden für die eine "Erstbestückung" erfolgt; für
    > diesen Durchlauf ist der Umstand "Wiederanlauf" ohne Bedeutung

-   lesen der ausgewählten Kunden aus Tabelle [kunde]

-   pro Kunde

-   Update [dn]

-   nur beim 1. Kunden der "Updateausgabe"

-   dn.restart_jn = "j"

> **1. Rabatttabelle**

-   löschen der Rabattabelle [dn_rab]

-   lesen der Artikelverkaufskonditionsgruppen

-   pro Konditionsgruppe und Kunde

-   ermitteln höchsten Mischrabattsatz des Kunden

-   vkkondart.aktpreis_jn = "n"

-   vkkondart.artik_zuord_kz = "g"

-   vkkond_preis.preisli_cd = fa.dn_preisli_cd

-   vkkond.artik_zuord = {Konditionsgruppe}

-   ((vkkondart.kunde_zuord_kz = "n" and vkkond.kunde_zuord =
    > {PreisKundenNr}) or (vkkondart.kunde_zuord_kz = "g" and
    > vkkond.kunde_zuord = {PreisKundenKondGrp})

-   Anlage Datensatz in [dn_rab]

-   rab = 0, wenn keine Rabattkondition vorhanden

-   rabgr_kz = 2, wenn mehr als ein Rabatt vorhanden, Mischsatz wird als
    > Multiplikator abgestellt

> **2. Artikeltabelle**
>
> Der Update auf Tabelle [dn_artik] beinhaltet wegen des
> Wiederanlaufes immer: {and verarb_kz = "-"}

-   nur beim 1. Kunden je Durchlauf

-   Beginn Transaktion

-   "Updateausgabe" und Wiederanlauf = Nein

-   löschen der Datensätze in [dn_artik]

-   verarb_kz = "l"

-   ändern der verbleibenden Datensätze in [dn_artik]

-   verarb_kz = "-"

-   "Erstbestückung"

-   keine zuvor erfolgte "Updateausgabe"

-   löschen aller Datensätze in [dn_artik]

-   zuvor erfolgte "Updateausgabe"

-   ändern Datensätze in [dn_artik] auf verarb_kz = "n"

-   verarb_kz <> "l"

-   Ende Transaktion

-   lesen der Tabelle Artikel [artik]

-   aktiv_jn = "j"

-   artik_kz = "n"

-   pro Artikel

-   Beginn Transaktion

-   bestimmen der neuen Werte für [dn_artik]

-   Aufruf Event für Ableitung

-   Eintragen der neuen Werte in [dn_artik]

-   n, wenn Neuanlage

-   a, wenn Änderung eines Feldes notwendig war

-   o, wenn alle neuen Werte ident mit den alten Werten

-   Ende Transaktion

-   ändern der nicht veränderten Datensätze (das sind jene, die aus
    > [artik] nicht mehr gelesen werden konnten) in [dn_artik]

-   verarb_kz = "l" where verarb_kz = "-"

> **3. Preistabelle**
>
> Der Update auf Tabelle [dn_preis] beinhaltet wegen des
> Wiederanlaufes immer: {and verarb_kz = "-"}

-   Beginn Transaktion

-   "Updateausgabe" und Wiederanlauf = Nein

-   löschen der Datensätze in [dn_preis]

-   verarb_kz = "l"

-   kunde_cd = {kunde_cd}

-   ändern der verbleibenden Datensätze in [dn_preis]

-   verarb_kz = "-"

-   "Erstbestückung"

-   löschen aller Datensätze in [dn_preis]

-   kunde_cd = {kunde_cd}

-   Ende Transaktion

-   lesen Distinct Artikel aus [dn_artik] für die Sonderpreis
    > vorhanden ist

-   vkkondart.aktpreis_jn = "n"

-   vkkondart.artik_zuord_kz = "n"

-   vkkond.fa_nr = dn_artik.artik_cd

-   vkkond.artik_zuord = dn_artik.artik_cd

-   preisli_prfind.preisli_cd = {PreisKundenPreisliCd}

-   vkkond_preis.preisli_cd = preisli_prfind.prfind_preisli_cd

-   ((vkkondart.kunde_zuord_kz = "-" and vkkond_preis.preisli_cd <>
    > fa.dn_preisli_cd) or vkkondart.kunde_zuord_kz = "g" and
    > vkkond.kunde_zuord = {PreisKundenKondGrp}) or
    > (vkkondart.kunde_zuord_kz = "n" and vkkond.kunde_zuord =
    > {PreisKundenNr}))

-   pro Artikel und Kunde

-   Beginn Transaktion

-   Preisfindung

-   Eintragen Nettopreis in [dn_preis]

-   a, wenn Neuanlage oder Änderung des Preises notwendig war

-   o, wenn alter Preis ident mit neuen Preis

-   keine Aktion, wenn Nettopreis größer oder gleich Listenpreis
    > [dn_artik] abzgl. Rabatt aus [dn_rab]

-   ändern der nicht veränderten Datensätze in [dn_preis]

-   verarb_kz = "l", vkp = dn_artik.vkp where verarb_kz = "-"

> **4. Warengruppentabelle**

-   nur beim 1. Kunden, unabhängig vom Durchlauf

-   löschen der Warengruppentabelle [dn_wgr]

-   lesen distinct Hauptwarengruppe und Warengruppe aus [dn_artik]

-   verarb_kz <> "l"

-   pro Hauptwarengruppe

-   Aufruf Event für Ermittlung Hauptwarengruppenbezeichnung

-   Anlage Datensatz der Hauptwarengruppe

-   pro Warengruppe

-   Aufruf Event für Ermittlung Warengruppenbezeichnung

-   Anlage Datensatz der Warengruppe, wenn Warengruppe <> ""

> **5. Ausgabe Files**

-   FileBaseName = fa.dn_pfad + "/" + kunde_mc + kunde_cd + "/"

-   löschen aller Files im Ordner FileBaseName

-   wenn Erstbestückung = Ja

-   Ausgabe der Warengruppentabelle [dn_wgr]

-   beim 1. Kunden nach c:\\temp\\dn_wgr

-   Feldbelegung lt. Datanormversion (V, E und S-Satz)

-   Filename = FileBaseName + "DATANORM.WRG"

-   kopieren c:\\temp\\dn_wgr nach Filename

-   Ausgabe der Rabattgruppentabelle [dn_rab]

-   Feldbelegung lt. Datanormversion (V, E und R-Satz)

-   Filename = FileBaseName + "DATANORM.RAB"

-   Ausgabe der Artikeltabelle [dn_artik]

-   beim 1. Kunden je Durchlauf nach c:\\temp\\dn_artik

-   Feldbelegung lt. Datanormversion (V, E und A-Satz)

-   Filename = FileBaseName + "DATANORM." + dn_lfd_nr

-   kopieren c:\\temp\\dn_artik nach Filename

-   Ausgabe der Preisänderungstabelle [dn_preis]

-   Feldbelegung lt. Datanormversion (V, E und P-Satz)

-   Filename = FileBaseName + "DATPREIS." + dn_lfd_nr

-   Update Kunde

-   kunde.dn_lfd_nr = kunde.dn_lfd_nr + 1

-   Update [dn]

-   nur beim letzten Kunden der "Updateausgabe"

-   dn.restart_jn = "n"

-   löschen Hilfsfiles

-   c:\\temp\\dn_artik

-   c:\\temp\\dn_wgr

-   Endemeldung des Programmes

#### DATANORM Einheiten

-   CMK Quadratzentimeter

-   CMQ Kubikzentimeter

-   CMT Zentimeter

-   DZN Dutzend

-   GRM Gramm

-   HLT Hektoliter

-   KGM Kilogramm

-   KMT Kilometer

-   LTR Liter

-   MMT Millimeter

-   MTK Quadratmeter

-   MTQ Kubikmeter

-   MTR Meter

-   PCE Stück

-   PR Paar

-   SET Satz

-   TNE Tonne

-   STG Stange

###  Intrastatschnittstelle

Werteingaben:

-   Export Verzeichnis (p)

-   Firma (p)

-   Auswertungsmonat (p)

-   Verarbeitungskennzeichen Einkauf/Verkauf (p)

-   Einkaufsdaten = \'e\'

-   Verkaufsdaten = \'v\'

-   Ein- und Verkauf = \'b\'

Allgemeines

-   Der Intrastat Export wird im Normalfall am 10. des Folgemonat
    durchgeführt

Auswahl der Daten:

-   land.inl_eu_drittl_kz = "e"

-   artik.is_zollta_nr <> "", "0"

Verkauf

-   vlfs_pos.vrech_mon lt. Auswahl

Einkauf

Im Einkauf muss zuerst das INTRASTAT Auswertungsmonat bestimmt werden.

-   Bei Eingangslieferscheinpositionen mit is_mon lt. Auswertungsmonat
    wird is_mon wieder auf Null gesetzt.

-   Eingangsliefscheinpositionen ohne Intrastatdatum mit einem
    ER-Rechnungsdatum im Auswertungsmonat werden auf das
    Auswertungsmonat upgedatet.

-   Eingangslieferscheinpositionen ohne Intrastatdatum mit
    Warenzugangsdatum vor dem Abrechungsmonat erhalten das
    Abrechnungsmonat

Datensatzaufbau RTIC:

-   Filename [EK\|VK]JJJJMM.csv

-   CSV mit ";" als Trennzeichen

-   Zolltarifnummer [artik.is_zollta_nr]

-   Warenbezeichnung [artik.artik_mc]

-   Bestimmungs- bzw. Versendungsland [auf bzw. lief adr.land_cd
    land.land_iso]

-   Ursprungsland [artik.is_urspland_cd land.land_iso]

-   Im Einkauf wird hier das Versendungsland verwendet, wenn das
    > Ursprungsland am Artikelstamm blank oder das Inland ist

-   Geschäftsart

-   12, wenn UstId = "" und Verkaufszweig

-   11, wenn Rechnungsbetrag > 0

-   21, wenn Rechnungsbetrag < 0

-   32, wenn Rechnungsbetrag = 0

-   Absolutwert der Eigenmasse in kg

-   Einkauf: [elfs_pos.veh_lief_mg \* artik.is_masse]

-   Verkauf: [vlfs_pos.umsmg \* artik.is_masse]

-   1 wenn < 1

-   Absolutwert der Menge in besonderer Maßeinheit

-   Einkauf: [elfs_pos.veh_lief_mg \* artik.is_veh_bmaeh_ftr]

-   Verkauf: [vlfs_pos.umsmg \* artik.is_veh_bmaeh_ftr]

-   Absolutwert des Rechnungsbetrages in Grundwährung

-   Einkauf: [elfs_pos.veh_lief_mg \* veh_ekpr -- s_ekrab1-5]

-   Verkauf: [vlfs_pos.ums]

-   Absolutwert Statistischer Wert w.o.

-   UstId

-   Einkauf: ""

-   Verkauf:

-   [auf.ustid] wenn <> ""

-   sonst, "QN999999999999"

Sortierung:

-   Statistisches Verfahren

-   Zolltarifnummer

### WebShop (Magento)

#### Export Stammdten

Die Stammdaten werden über die DB Views

-   magento_attributes

-   magento_categories

-   magento_customers

-   magento_customers_addresses

-   magento_products

ausgegeben.

Detailbeschreibung: [..\..\\Webshops\\Org\\Exportbeschreibung
Magento-M2IF.xlsx](../../Webshops/Org/Exportbeschreibung%20Magento-M2IF.xlsx)

####  Webshop Objektart

##### Auswahlkriterien

-   Objektart

-   Objektart Matchcode

##### Liste

-   Objektart

-   Firma

-   Objektart Matchcode

-   Präfix des Dokumentes

-   Typ

-   Sortiernummer

##### Detail

Teilbereich "Objektart"

-   Objektart

-   Firma

-   Objektart Matchcode

-   Typ

-   Präfix des Dokumentes

-   keine Eingabe bei Typ Link [webshopobj_kz = "l"]

-   Pfad im Filesystem lt. Stammdaten (Artikel) #53662

-   keine Eingabe bei Typ Link [webshopobj_kz = "l"]

-   Webshoppfad (Artikel) #53662

-   Pfad im Filesystem lt Warengruppe #53662

-   Webshoppfad (Warengruppe) #53662

-   Ausgabeart

-   keine Eingabe bei Typ PDF oder mp2 [webshopobj_kz in( "p",
    > "m")]

-   Sortiernummer

    **Teilbereich "Sprache"**

-   Sprache

-   Label

#### WebShop Warengruppe

##### Auswahlkriterien

-   WarengruppenNr

-   Parent WarengruppenNr (f)

-   Warengruppen Matchcode

##### Register Liste

-   WarengruppenNr

-   Warengruppen Matchcode

-   Webshop Pfad

-   ermittelt über DB-Funktion [dbo.webshopwg_anzeige]

##### Register Detail

**Teilbereich "Warengruppe"**

-   WarengruppenNr

-   Warengruppen Matchcode

-   aktiv (c)

-   Sprache-Felder:

-   Sprache (d)

-   wird eine Sprache ausgewählt die es noch nicht im Teilbereich
    > "Sprache" wird eine neue Zeile angelegt

-   alle weiteren Felder in "Sprache-Felder" werden von
    > [webshopwg_sprache] lt Sprache angezeigt und ändert auch die
    > entsprechende Zeile ab

-   Warengruppenbezeichnung

-   Beschreibungstext

-   Text für seitliche Navigation

-   SEO Title Text

-   SEO Beschreibungstext

-   SEO Text

    **Teilbereich "Sprache" (a)**

-   manuelle Neuanlage nicht möglich, wird über den Teilbereich
    "Warengruppe" neuangelegt

-   Auswahl der Zeile setzt Sparche im Teilbereich "Warengruppe"

-   Sprache

-   Warengruppenbezeichnung

    **Teilbereich "Artikel"**

-   Liste über alle Artikel die dieser Warengruppe zugeordnet sind

-   Firma

-   Artikelnummer

-   Artikelmatchcode (a)

-   Attribute ok (ca) #53662

-   "n", wenn ein zwingendes Attribut [webshopwg_webshopattribute.
    > webwgatt_zwingend_jn = "j"] nicht in Artikel Webshopattribut
    > [artik_webshopattribute] vorhanden ist

-   "j", sonst

    **Teilbereich "Parent"**

-   Liste über alle direkten Parents

-   Parent WarengruppenNr

-   Warengruppen Matchcode (a)

-   SortierNr

-   anzeigen (c)

    **Teilbereich "Untergruppen"**

-   Liste über alle direkten Untergruppen

-   Untergruppen WarengruppenNr

-   Untergruppen Matchcode (a)

    **Anmerkung Speichern**

-   es darf kein Kreisbezug bei den Parents und Untergruppen geben

##### Register Objekte #53662

-   Objektart (d)

-   Link

-   Eingabe nur bei Link Objektart möglich

    Anmerkung

-   Mit Drag&Drop können hier Bilder, PDF´s oder MP3 Files abgelegt
    werden.

-   Bei einer neuen Zeile muss dann die jeweilige Objektart ausgewählt
    werden.

-   Wenn eine Zeile gelöscht wird, dann wird auch das jeweilige Objekt
    aus dem Verzeichnis gelöscht.

-   Durch eine Änderung der Objektart wird das File in das jeweilig
    Verzeichnis lt. Objektart verschoben.

-   Die Objekte müssen auch beim Löschen des Artikels mitgelöscht
    werden.

-   Mit Doppelklick auf eine Zeile kann das jeweilige Objekt geöffnet
    werden

-   Es darf kein Download Link verwendet werden

##### Register Attributte #53662

-   AttributNr

-   Attribut Matchcode (a)

-   zwingend (c)

-   Auswahl DDDW für Tag-Attribute (d)

-   Defaultwert

-   Artikel Updaten (d)

-   nicht gespeichertes Feld

-   Kein Update (= Default)

-   Nur neue anlegen (kann nur mit augefüllten Defaultwert ausgewählt
    > werden)

-   Update alle Artikel

-   Nicht möglich bei leerem Defaultwert + zwingend = Ja

-   Bei leerem Defaultwert kommt ein TE: "Achtung damit löschen sie
    > dieses Attribut von allen zugeordneten Artikeln! Fortsetzen
    > Nein/Ja"

    **Anmerkung Speichern**

-   für alle Zeile die zur Übernahme vorgemerkt sind werden für die
    Warengruppen und alle Untergruppen, deren Artikel die Attribubte mit
    den Defaultwert eingetragen bzw. upddatet oder glöscht wenn der
    Defaultwert nicht ausgefüllt ist.

-   Konfigurationsartikel [artik.artik_kz = "k"] werden übersprungen

#### WebShop User

Auswahlkriterien:

-   Firma

-   User-Nummer

-   Kundennummer (f)

-   Kunden-Matchcode

-   E-Mail Adresse

-   Nachname

-   System-ID

Liste:

-   User-Nummer

-   Kundennummer

-   Kunden-Matchcode

-   Vorname Lieferadresse

-   Nachname Lieferadresse

-   Telefon

-   E-Mail

-   Company Lieferadresse

-   Land Lieferadresse

-   Plz Lieferadresse

-   Ort Lieferadresse

-   Zeitpunkt lt. Übertragung

-   System-ID

-   WebShop Kundengruppe

-   WebShop Code

Detail

-   User-Nummer (a)

-   Haupt-Usernummer (a)

-   WebShop Code (a)

-   WebShop Kundengruppe (d)

-   Geschlecht (d) (a)

-   Geburtsdatum (a)

-   Telefonnummer (a)

-   E-Mail (a)

-   Rechnungs E-Mail (a)

-   Rechnungs- und Lieferadresse

-   Titel (a)

-   Vorname (a)

-   Nachname (a)

-   Firmenname (a)

-   Straße (a)

-   Land (a)

-   PLZ (a)

-   Ort (a)

-   UstID (a)

-   Zeitpunkt ltz. Übermittlung (a)

-   System-ID (a)

-   Adress-System ID (a)

-   Status (da)

-   Aktiv (c)

-   Firma (a)

-   Kundennummer (fc)

-   Muss ein aktiver Kunde mit ausgefüllter WebShop Kundengruppe sein

-   Kundenmatchcode (a)

-   Personen des Kunden (d)

-   Person des Debitoren (d)

Speichern - Kundenzuordnung

-   Wurde eine Kundennummer eingegeben und der Personencode ist noch
    null, so wird jetzt eine neue Person angelegt. Der Personencode wird
    dabei mit dem größten numerischen Personencode der Adresse +1
    vergeben. Wenn eine vorhandene Person zugeordnet wurde, so werden
    die Daten aktualisiert. Es darf dabei jedoch kein Datenfeld, dass am
    Personenstamm ausgefüllt ist, mit einem leeren lt. WebShop User
    überschrieben werden. Personenstamm wird im Modus "webshop"
    geöffnet

Folgende Datenfelder werden gesetzt:

-   Geschlecht

-   Titel

-   Vorname

-   Nachname

-   Geburtsdatum

-   Aktiv = "j"

-   Kommunikationsarten (wenn ausgefüllt)

-   Telefonnummer (Kommunikationsart lt. pfu_param
    > default_tel_komidart_cd)

-   E-Mal (Kommunikiationsart lt. pfu_param default_mail_komidart_cd)

Teilbereich Kundenauswahl (a)

-   Nur Aktiv wenn die Kundennummer noch Null ist

Liste über Kunden der Firma:

-   zu Debitoren bei denen die UID-Nummer übereinstimmt (nur wenn die
    UID-Nummer ausgefüllt ist)

-   zu Personen mit dieser E-Mail Adresse

-   zu Personen zu Debitoren mit dieser E-Mail Adresse

-   Eine Zeile für Neuanlage

-   Auswählen (c)

-   Nur dieses Feld kann eingegeben werden. Dadurch wird die
    > Kundennummer übernommen, bzw. die Neuanlage eines Kunden
    > durchgeführt.

-   In diesem Fall wird am bestehenden Kunden die WebShop Kundengruppe
    > eingetragen, falls diese noch null ist.

-   Kundennummer

-   Matchcode

-   Name 1

-   Straße

-   Land

-   PLZ

-   Ort

-   Vorname

-   Nur bei Ermittlung über E-Mail

-   Nachname

-   Nur bei Ermittlung über E-Mail

Neuanlage Kunde

-   Es wird eine neue Adresse angelegt

-   Es wird dabei die Lieferadresse verwendet, die Rechnungsadresse wird
    > nur dann als eigene Adresse angelegt, wenn sie von der
    > Lieferadresse abweicht.

-   Ist Company Belegt, so werden Name1 bis Name 4 aus diesem belegt. Es
    > wird abhängig von der eingestellten Länge für Name1 ein Umbruch
    > bei einem Leerzeichen versucht. Ist keien Leezeichen in den ersten
    > x Stellen vorhanden, dann wird der Text abgeschnitten.

-   Wenn der Company Text nicht belegt ist, so werden Name1 -- 4 aus dem
    > Text Titel + Vorname + Nachnahme w.o. belegt.

-   Name 1

-   Name 2

-   Name 3

-   Land

-   Plz

-   Ort

-   Matchcode

-   Wenn Name1 beleg dann dieser, sonst Nachname + Vorname (gekürzt auf
    > Feldlänge)

-   Natürliche Person

-   Wird aktiviert, wenn Company leer ist.

-   Es wird der Kundenstamm im Modus lt. WebShop Kundengruppe geöffnet.

Folgende Daten werden gesetzt

-   LieferAdresse

-   kundeerl_cd lt. webshopkdgr_land der Lieferadresse

-   Debitorennummer

-   Wenn webshopkdgr_land. debitor_nr ausgefüllt ist und die
    > Lieferadresse gleich der Rechnungsadresse ist wird diese
    > debitor_nr verwendet, ansonsten wird der Debitor neu angelegt.

-   Ist die UID Nummer ausgefüllt wird ein Debitor mit dieser UID-Nummer
    > und dieser Rechnungsadresse gesucht.

Am Debitorenstamm:

-   Nur wenn der Debitor neu angelegt wird.

-   Rechnungsadresse (falls unterschiedlich zur Lieferadresse)

-   UID-Nummer

-   Es wird die UID Prüfung durchgeführt wenn das Modul aktiviert ist

-   Wenn die Prüfung fehlschlägt, wird die UID-Nummer als
    > ustid_ungueltig eingetragen und kod_uid_chk_nr auf "e" gesetzt.

-   Rechnungs-E-Mail Adresse

-   Wenn Rechnungs E-Mail Adresse ausgefüllt ist vrechausart_cd auf
    "e"

-   Es werden Events für das Setzen von individuellen Datenfeldern in
    Adresse, Kunde und Debitor vorgesehen.

Extra Menü:

-   Zuordnung zu Hauptuser

-   Das Feld Haupt-System-ID ist zur Eingabe offen

-   Kunde trägt hier die System-ID des Hauptusers ein

-   Beim speichern wird die Emailadresse randomisiert mit
    > system-id@......

##### Register „Zugeordnete Kunden"

-   Anzeige der User wo gilt: Haupt-System-ID = meine System-Id

-   Nur Verfügbar, wenn hpt_webshopusr_nr is null

-   Löschen von bereits gespeicherten Datensätzen ist nicht mehr möglich

Liste über:

-   Kundennummer (f)

-   ColSearch ist aktiv

-   Es sind nur aktive Kunden erlaubt

-   Kundenmatchcode (a)

-   Aktiv (c)

    Bei Neuanlage wird ein neuen webshopusr Sub-Datensatz erstellt -
    sieht db.docx

##### Neuanlage WebShop User

-   Wir ein neuer WebShop User manuell in TC angelegt, so muss die
    Kundennummer erfasst werden (keine Kundenauswahl verfügbar).

-   Vom Kunden werden die WebShop-Kundengruppe, Adresse, UstID und
    Rechnungs E-Mail Adresse übernommen

-   Es muss ein Person ausgewählt werden, die eine E-Mail Adresse
    hinterlegt hat. Es werden alle Personenbezeogenen Datenfelder von
    diesem User übernommen.

-   Falls der Debitor eine vom Kunden abweichende Lieferadresse hat, so
    muss auch die Rechnungs Person ausgewählt werden. Hier kann auch die
    Dummy Person verwendet werden.

-   Der WebShop Code wird im Standard über einen Defaultwert belegt

#### WebShop User Import

Auswahkriterien

-   Usernummer

Ablauf

Pro webshopusr mit Status-KZ n oder a

-   Neuer Hauptuser (hpt_webshopusr_nr ist null)

-   Je nach WebShop Kundengruppe wird

-   der WF ausgelöst

-   Der Kunde und oder die Person werden über folgende Varianten gesucht

-   E-Mail Adresse, UID-Nummer, Lieferadresse

-   UID-Nummer, Lieferadresse

-   Bei der Adresse wird immer nur über Land, PLZ und Ort gesucht.

-   der Kunde über die Fernsteuerung des Webshopusers neu angelegt

-   Neuer Subuser (hpt_webshopusr_nr ist nicht null)

-   Es wird der Kunde des Hauptusers ermittelt

-   Gibt es beim Kunden bereits eine Person mit dieser E-Mail Adresse,
    > dann wird diese Person zugeordnet und die Änderungen gebucht --
    > ansonsten wird eine neue Person angelegt.

-   Der Status wird auf Erledigt gesetzt

-   Änderungen

-   Es werden die Änderungen im Personenstamm durchgeführt.

-   Wenn lt. WebShop Kundengruppe aktiviert werden auch Änderungen an
    > der Adresse übernommen.  
    > Dabei kann es vorkommen, dass die Rechnungsadresse neu angelegt
    > werden muss, da sie jetzt von der Lieferadresse abweichend ist.

-   Der Status wird auf Erledigt gesetzt

Workflow "neuer WebShop Kunde"

  -----------------------------------------------------------------------
  Code              wsusr
  ----------------- -----------------------------------------------------
  Auslöser          Wenn ein neuer WebShop Hauptuser übermittelt wurde

  Infotext          --

  Applkz            --

  Applpers          --

  Bezugsobjekt      Debitor

  Empfänger         Sachbearbeiter für Kundenstammpflege

  Positive          nur Info
  Erledigung        

  Negative          --
  Erledigung        
  -----------------------------------------------------------------------

#### Auftragsimport

Der Magento WebShop speichert die Daten in der Tabelle magento_bestell
und magento_bestell_pos. Es wird dabei ein Auftrag als eine Transaktion
übergeben.

Auswahlkriterien

-   Firmennummer (p)

-   Auftragseingangsart (p)

-   Protokolldruck (p)

-   a = Alle Aufträge drucken

-   f = Nur Fehlerhafte Aufträge drucken

-   AB-Senden j/n (p)

-   Kommissionsscheindruck j/n (p)

-   Zahlungsart bereits bezahlt (p)

-   Preise übernehmen

-   Nein

-   Ja

-   Nur bei Zahlung am WebShop

Ablauf

Pro Datensatz in magento_bestell_pos mit auf_nr = 0 und
magento_bestell.store_name = fa.webshop_website_code (Committed Read).

-   Sperren Kopf und Position

-   Wenn magento_bestell.auf_nr = 0 (erste Position) -- Aufbauen
    Auftragskopf. Folgende Datenfelder im Auftragskopf werden lt.
    magento_bestell belegt

-   Bei einem Auftrag bei dem Digitale Produkte (downloadable) und
    > normale Positonen gemischt sind, müssen 2 Aufträge aufgebaut
    > werden. Die Shipping Position bleibt dabei bei den normalen
    > Positionen.

-   Firma = lt. Firmenstamm

-   Auftragsnummer = bestell_nr

-   Es muss ein Nummernkreis für den WebShop freigehalten werden

-   Bei einem Splitt Auftrag gilt das nur für die normalen Positionen
    > nicht für die Digitalen Produkte.

-   Kundennummer

-   Wenn in magento_bestell leer dann wird die Kundenummer Gastkunde lt.
    > webshopkdgrp_land (lt. Lieferadresse) verwendet (Event vorsehen).

-   Ist diese nicht ausgefüllt, so muss der gesamte Auftrag am
    > Fehlerprotokoll gedruckt werden.

-   Auftragsart = \'n\'

-   Lieferadresse

-   Nur bei einem Gastkunden oder bei einem Diversen Debitoren

-   Rechnungsadresse

-   ustid

-   Kundenbestellnummer

-   Bei einem Split Auftrag die bestell_nr

-   Kundenbestelldatum

-   Wenn die E-Mail Adresse belegt ist wird

-   die AB-Kommunikationsart auf fa.webshop_email_komidart_cd gesetzt

-   die AB-Kommunikationsnummer mit der E-Mail Adresse belegt

-   Wenn die Shipping-Telefonnummer belegt ist wird sie als
    > Lieferung-Kommunikationsnummer übernommen

-   Versandart -- Es wird die Versandart lt. shipping_method ermittelt.
    > Wenn diese nicht gefunden werden kann wird die Versandart nicht
    > gesetzt (es bleibt die lt. Kunde).

-   Fakturenart wird bei Digitalen Produkten auf "Rechnung =
    > Lieferbeleg" gestellt.

-   Ist die billing_email belegt und weicht von der lt. Debitor ab:

-   Wird vrechausart_cd auf "e" gestellt

-   Die Rechnungs-E-Mail Adresse mit der billing_email belegt und auf
    > Fix gestellt.

-   Ist vkrech_kz in (d,k,ka) wird sie auf "a" geändert

-   Ist payment_type "online"

-   wird die Zahlungsart gesetzt, dabei gilt folgende Reihenfolge bei
    > der Ermittlung

-   Aus webshopzahlart mit payment_method + card aus payment_info

-   Aus webshopzahlart mit payment_method und payment_info = blank

-   lt. Paramameter

-   Zahlungsart fix wird auf "j" gesetzt

-   Die Zahlungs-Refferenznummer wird aus payment_info ref übernommen

-   Währung

-   Auftragseingangsart lt. Parameter

-   ab_zhd wird mit Vorname + Nachnahme belegt, wenn diese Ausgefüllt
    > sind

-   Der Interne Text wird als Kopftext mit Drucken auf Kommissionsschein
    > übernommen

-   Der Kunden-Bestell-Text wird als Kopftext mit Drucken auf allen
    > Belegen übernommen

-   Bei der Plain Text Varinte müssen die Text sinnvoll auf mehrere
    > Zeilen aufgeteilt werden.

-   In einer Variable, die bei einer Ableitung übersteuert werden kann,
    > kann dazu die maximale Zeilenlänge des Textes definiert werden.

-   Event für die Belegung von individuellen Datenfeldern in Ableitungen
    > vorsehen

-   Ist die Auftragnummer bereits belegt (Wiederanlauf) wird geprüft ob
    der Auftrag noch offen ist, Wenn nicht wird ein neuer Auftrag (siehe
    oben) erstellt.

-   Pro Position wird eine neue Position mit folgenden Datenfeldern
    erstellt

-   Firmennummer und Auftragsnummer lt. Auftragskopf

-   Artikelnummer

-   Menge

-   Freigabemenge bei Digitalen Produkten

-   Sollen Preise übernommen werden und weicht der Positionsbetrag
    > (unter Berücksichtigung aller Kopfrabatte) vom jeweils
    > übermittelten Positionsbetrag ab (unter Berücksichtigung von
    > iu_jn) wird die Position auf nicht Kopfrabattfähig gestellt, alle
    > Rabatte auf 0 gestellt und ein Nettopreis gesetzt um den
    > Positionsbetrag lt. WebShop zu erreichen.

-   magento_item_id

-   Der Positionstext wird als Text mit Druck auf allen Belegen
    > übernommen.

-   Event für die Belegung von individuellen Datenfeldern in Ableitungen
    > vorsehen

-   Event für Individuelle Aktionen nachdem alle Positionen erstellt
    wurden vorsehen (z.B. für Lagerzuordnung bei f&b)

-   Für Aufträge, bei denen es keine Fehlerhafte Position gibt

-   Bei Digitalen Produkten wird der Lieferbelegaufbau eingespoolt
    > (keine AB keine KS)

-   und die AB Per E-Mail erhalten wird nach Bearbeitung der letzten
    > Position das AB-Versenden eingespoolt, wenn das lt. Parameter
    > erfolgen soll.

-   und die freigegebene Positionen haben wird der Kommissionscheindruck
    > eingspoolt, wenn das lt. Parameter passieren soll.

Fehlerbehandlung

-   Grundsätzlich werden alle Alphanumerischen Felder auf die maximale
    Feldlänge in TC gekürzt

-   Bei einem Fehler wird der entsprechende Datensatz auf auf_nr = -1
    upgedatet und ein entsprechender Text in err_txt geschrieben. Es
    wird dann immer mit dem nächsten Datensatz fortgesetzt.

-   Gibt es einen Fehler beim Kopf Datensatz werden auch alle Positionen
    auf auf_nr -1 upgedatet.

Protokolldruck

lt. Parameter werden entweder alle oder nur die Fehlerhaften Aufträge
gedruckt,

Ist eine Position Fehlerhaft, muss der komplette Auftrag gedruckt
werden.

Listbild: [webshopImportProtokoll.docx](webshopImportProtokoll.docx)

In der Position wird der Artikelmatchcode gedruckt. Wenn der Artikel
nicht gefunden wurde, dann bleibt der Artikelmatchcode leer.

#### Export Versanddaten

Auswahlkriterien

-   Firmennummer (p)

-   Filialnummer (o)

Schnittstellenbeschreibungen; https://magento.redoc.ly/2.3.7-admin/

Beispiel:
<https://magecomp.com/blog/create-shipment-with-magento-2-api/>

Auswahl der Daten:

-   Alle noch nicht versendeten Lieferschiene lt. Auswahlkriterien

Pro vlfs mit magento_shipm_nr = 0 (eine Transaktion)

-   Wenn lt. Versandart magento_shipm_kz = v und es gibt zu dem
    Lieferschein noch keine Versanddaten, wird der Lieferschein
    überlesen.

-   Sperren Debitor

-   Pro Eingangsauftrag (aus vlfs_pos) mit Magento Order ID

-   POST einer order/<magento_order_id>/ship Nachricht

-   Items mit itim_id und Menge von allen Positionen mit einer
    > Magento-Item ID

-   notify lt. versandart

-   tracks nur bei Versanpaket pro Paketnummer aus dem Versanddaten

-   carrier_code = lt. Versandart

-   title = lt. Versandart

-   track_number = Paketnummer lt. Versandpaket

-   Update vlfs Magento-Versand Jobnummer

### Versand

#### IFTMIN

Auswahlkriterien

-   Firma (p)

-   Versanddatum

Allgemeines

-   IFTMIN ist ein EDI Transportauftrag --

-   Detailbeschreibung siehe
    > <https://www.publikationen.gs1-germany.de/Complete/IFL_2.3/profiles/iftmin/de/index.html>

Auswahl der Daten:

-   Datensätze aus vs_auf mit export_job_snr = 0, spedliste_nr > 0 und
    > vs_versart.edi_kz = \'iftmin\'

Ablauf

Pro Versandart/Versandort

-   Eine Transaktion pro Versandart/Versandort

-   Update der aktuellen Jobnummer in den betroffenen vs_auf Datensätzen
    (die noch 0 sind)

-   Neu Retrieven der vs_auf Daten mit der Jobnummer

-   Erstellen eine Files im lokalen temp Verzeichnis

-   Löschen falls bereits vorhanden

-   Ausgabe Daten -- siehe unten

-   Verschieben des Files nach vs_versart.edi_pfad

-   Platzhalter müssen dabei ersetzt werden

-   Commit

    Folgende Segmente/Daten werden ausgebeben

+----+------+----------------------------------------------------------+
| *  | DE   | Belegung aus TC                                          |
| *S |      |                                                          |
| eg |      |                                                          |
| ** |      |                                                          |
+====+======+==========================================================+
| *  |      | Fix "UNA:+.? \'"                                       |
| *U |      |                                                          |
| NA |      | -   Wird 1x pro File ausgegeben                          |
| ** |      |                                                          |
+----+------+----------------------------------------------------------+
| *  |      | Wird 1x pro File ausgegeben                              |
| *U |      |                                                          |
| NB |      |                                                          |
| ** |      |                                                          |
+----+------+----------------------------------------------------------+
|    | S001 | Fix "UNOA:3"                                           |
+----+------+----------------------------------------------------------+
|    | S002 | Absender Mailbox GLN lt. vs_versart                      |
+----+------+----------------------------------------------------------+
|    | S003 | Empfänder Mailbox GLN lt. vs_versart                     |
+----+------+----------------------------------------------------------+
|    | S004 | aktuelles Datum und Uhrzeit                              |
+----+------+----------------------------------------------------------+
|    | 0020 | Datenaustauschreferenz: Jobnummer                        |
+----+------+----------------------------------------------------------+
| *  |      | 1xpro vs_auf                                             |
| *U |      |                                                          |
| NH |      |                                                          |
| ** |      |                                                          |
+----+------+----------------------------------------------------------+
|    | 0062 | Laufende Nummer des UNH Segments in der Nachricht        |
+----+------+----------------------------------------------------------+
|    | S009 | Fix: "ITFMIN:D:96A:UN:FIIN01"                          |
+----+------+----------------------------------------------------------+
| *  | C002 | Fix 610 (= Speditionsauftrag)                            |
| *B |      |                                                          |
| GM |      |                                                          |
| ** |      |                                                          |
+----+------+----------------------------------------------------------+
|    | C106 | vs_auf.spedliste_nr                                      |
+----+------+----------------------------------------------------------+
| *  | C507 | Datum zu BGM                                             |
| *D |      |                                                          |
| TM |      |                                                          |
| ** |      |                                                          |
+----+------+----------------------------------------------------------+
|    | 2005 | Fix 137                                                  |
+----+------+----------------------------------------------------------+
|    | 2380 | Versanddatum                                             |
+----+------+----------------------------------------------------------+
|    | 2379 | Fix 102                                                  |
+----+------+----------------------------------------------------------+
| *  |      | Service 1x pro UNH fix "PRO+W24"                       |
| *T |      |                                                          |
| SR |      |                                                          |
| ** |      |                                                          |
+----+------+----------------------------------------------------------+
| *  |      | Wird ausgegegeben, wenn vs_auf.sendungsnummer belegt ist |
| *F |      |                                                          |
| TX |      |                                                          |
| ** |      |                                                          |
+----+------+----------------------------------------------------------+
|    | 4451 | Fix "DEL"                                              |
+----+------+----------------------------------------------------------+
|    | 4453 | ""                                                     |
+----+------+----------------------------------------------------------+
|    | C107 | ""                                                     |
+----+------+----------------------------------------------------------+
|    | C108 | sendungsnummer                                           |
+----+------+----------------------------------------------------------+
| *  |      | Wird 1x pro UNH ausgegeben                               |
| *T |      |                                                          |
| OD |      |                                                          |
| ** |      |                                                          |
+----+------+----------------------------------------------------------+
|    | 4055 | Fix 6                                                    |
+----+------+----------------------------------------------------------+
|    | 4215 | Fix ""                                                 |
+----+------+----------------------------------------------------------+
|    | C100 | liefbed.incoterm_kz                                      |
+----+------+----------------------------------------------------------+
| *  | C506 | 1xPro UNH                                                |
| *R |      |                                                          |
| FF |      |                                                          |
| ** |      |                                                          |
+----+------+----------------------------------------------------------+
|    | 1153 | fix "CU"                                               |
+----+------+----------------------------------------------------------+
|    | 1154 | Belegnummer                                              |
+----+------+----------------------------------------------------------+
| *  | C506 | 1xPro Beleg (vs_auf_beleg ausgenommen die unter RFF+CU   |
| *R |      | ausgegebene Belegnummer)                                 |
| FF |      |                                                          |
| ** |      |                                                          |
+----+------+----------------------------------------------------------+
|    | 1153 | fix "CUA"                                              |
+----+------+----------------------------------------------------------+
|    | 1154 | Belegnummer                                              |
+----+------+----------------------------------------------------------+
| *  | C506 | 1xPro Kundenbstellnummer aus zugeordneten Aufträgen      |
| *R |      | (Join über vs_auf_beleg -- Abwicklungsauftrag der        |
| FF |      | Lieferscheine)                                           |
| ** |      |                                                          |
+----+------+----------------------------------------------------------+
|    | 1153 | fix "CUA"                                              |
+----+------+----------------------------------------------------------+
|    | 1154 | Kundenbestellnummer                                      |
+----+------+----------------------------------------------------------+
| *  |      | 1xPro UNH                                                |
| *T |      |                                                          |
| DT |      | fix "TDT+20++30"                                       |
| ** |      |                                                          |
+----+------+----------------------------------------------------------+
| *  |      | 2xPro UNH                                                |
| *N |      |                                                          |
| AD |      |                                                          |
| ** |      |                                                          |
+----+------+----------------------------------------------------------+
|    | 3035 | -   CZ für Absender -- lt. vs_versort                    |
|    |      |                                                          |
|    |      | -   CN für Empfänger -- lt. vs_auf                       |
+----+------+----------------------------------------------------------+
|    | C082 | ""                                                     |
+----+------+----------------------------------------------------------+
|    | C058 | ""                                                     |
+----+------+----------------------------------------------------------+
|    | C080 | Name 1 -- 3 der Adresse (max. ja 35 Zeichen)             |
+----+------+----------------------------------------------------------+
|    | C059 | Straße (max je 35 Zeichen)                               |
+----+------+----------------------------------------------------------+
|    | 3164 | Ort (max je 35 Zeichen)                                  |
+----+------+----------------------------------------------------------+
|    | C819 | ""                                                     |
+----+------+----------------------------------------------------------+
|    | 3251 | PLZ                                                      |
+----+------+----------------------------------------------------------+
|    | 3207 | Land ISO2 Code                                           |
+----+------+----------------------------------------------------------+
| *  |      | Pro Verpackungsart aus vs_auf_paket                      |
| *G |      |                                                          |
| ID |      |                                                          |
| ** |      |                                                          |
+----+------+----------------------------------------------------------+
|    | 1496 | laufende Nummer innerhalb von vs_auf                     |
+----+------+----------------------------------------------------------+
|    | C213 |                                                          |
+----+------+----------------------------------------------------------+
|    | 7224 | Anzahl der vs_auf_paket Einträge mit dieser              |
|    |      | Verpackungsart                                           |
+----+------+----------------------------------------------------------+
|    | 7065 | IFTMIN Verpackungsartencode                              |
+----+------+----------------------------------------------------------+
| *  |      | Pro GID wenn vs_fa.iftmin_warenbez <> ""             |
| *F |      |                                                          |
| TX |      |                                                          |
| ** |      |                                                          |
+----+------+----------------------------------------------------------+
|    | 4451 | Fix "AAA"                                              |
+----+------+----------------------------------------------------------+
|    | C108 | vs_fa.iftmin_warenbez                                    |
|    |      |                                                          |
|    |      | -   hier könnten bis zu 5x512 Zeichen Text ausgegeben    |
|    |      |     werden                                               |
+----+------+----------------------------------------------------------+
|    | 3453 | Fix "DE"                                               |
+----+------+----------------------------------------------------------+
| *  |      | Pro GID                                                  |
| *M |      |                                                          |
| EA |      |                                                          |
| ** |      |                                                          |
+----+------+----------------------------------------------------------+
|    | 6311 | Fix "AAE"                                              |
+----+------+----------------------------------------------------------+
|    | C502 | Fix "G"                                                |
+----+------+----------------------------------------------------------+
|    | C174 |                                                          |
+----+------+----------------------------------------------------------+
|    | 6411 | Fix "KGM"                                              |
+----+------+----------------------------------------------------------+
|    | 6314 | Summe Bruttogewicht der Verpackungsart aus vs_auf_paket  |
+----+------+----------------------------------------------------------+
| *  |      | Pro GID wenn Abmessungen auf der Verpackungart angegeben |
| *D |      | sind (<> 0)                                            |
| IM |      |                                                          |
| ** |      |                                                          |
+----+------+----------------------------------------------------------+
|    | 6145 | Fix "2"                                                |
+----+------+----------------------------------------------------------+
|    | 6411 | Fix "MTR"                                              |
+----+------+----------------------------------------------------------+
|    | 6168 | Lönge lt. Verpackungsart                                 |
+----+------+----------------------------------------------------------+
|    | 6140 | Breite lt. Verpackungsart                                |
+----+------+----------------------------------------------------------+
|    | 6008 | Höhe lt. Verpackungsart                                  |
+----+------+----------------------------------------------------------+
| *  |      | Fix "33E" -- pro GID                                   |
| *P |      |                                                          |
| CI |      |                                                          |
| ** |      |                                                          |
+----+------+----------------------------------------------------------+
| *  |      | Wird pro vs_auf_paket mit der jeweiligen Verapckungsart  |
| *G |      | ausgegeben                                               |
| IN |      |                                                          |
| ** |      |                                                          |
+----+------+----------------------------------------------------------+
|    | 7405 | Fix "BJ"                                               |
+----+------+----------------------------------------------------------+
|    | C208 | vs_auf_paket.paket_sendung_nr                            |
+----+------+----------------------------------------------------------+
| *  |      | Pro vs_auf wenn es Ladehilfsmittel Verpackungsarten      |
| *E |      | gibt.                                                    |
| QN |      |                                                          |
| ** |      |                                                          |
+----+------+----------------------------------------------------------+
|    | C523 | Anzahl der Ladehilfsmittel Einheiten (=GID 7224)         |
+----+------+----------------------------------------------------------+
| *  |      | 1x pro vs_auf (Ende)                                     |
| *U |      |                                                          |
| NT |      |                                                          |
| ** |      |                                                          |
+----+------+----------------------------------------------------------+
|    | 0074 | Anzahl der Segmente in der Nachricht (UNH bis inkl.      |
|    |      | diese Segment)                                           |
+----+------+----------------------------------------------------------+
|    | 0062 | Nachrichten Referenznummer (selbe wie in UNH)            |
+----+------+----------------------------------------------------------+
| *  |      | Ende der Nachricht                                       |
| *U |      |                                                          |
| NZ |      |                                                          |
| ** |      |                                                          |
+----+------+----------------------------------------------------------+
|    | 0036 | Anzahl der Versand Auftrage (UNH Segmente)               |
+----+------+----------------------------------------------------------+
|    | 0020 | Datenaustauschreferenz lt. UNB                           |
+----+------+----------------------------------------------------------+

###  Auftragsimport

#### Import aus anderen Systemen

##### TC.WebView

Auswahlkriterien

-   Firma

-   casauf_upid

-   Std für erfasst Aufträge (o)

Pro Datensatz aus casauf mit Status "f" oder "e" und der
Erfassungszeitpunkt liegt mind. x Std. in der Vergangenheit:

-   Wurden keine Std. angegeben, werden Aufträge mit Status "e" nicht
    verarbeitet.

-   Start Transaction

-   Update Status auf "u" (mit Lock Logik)

-   Insert aufimp

-   evt. aufimp_txt

-   pro casauf_pos -- Insert aufimp_pos

-   Commit Transaction

    Wenn mindestsens ein Auftrag übernommen wurde wird die Verarbeitung
    Auftragsimport für die Quelle "cas" eingespoolt.

#### Auftragsimport Verarbeitung

Auswahlkriterien

-   Firma (p)

-   Quelle (w)

-   ... Diverse Kriterien lt. aufimp

Ablauf

-   Für alle Auftragimport Daten mit Status "u" wird das Konvertieren
    durchgeführt

-   Für alle Aufragsimport Daten mit Status "v" wird der Aufbau der
    Aufträge durchgeführt

-   Siehe Extra Menü im Auftragsimport Dialog Programm

#### Aufragsimport

-   keine Neuanlage möglich

-   kein Löschen möglich

-   Keine Änderung möglich wenn aufimp_status_kz = ‚a'

Auswahldialog

-   Firmennummer (w)

-   Filiale (w)

-   Kundennummer (f)

-   Quelle (w)

-   Kundenbestellnummer

-   Kundenbestelldatum

-   Auftragsnummer

-   Status (w)

Register Liste

-   Firmennummer

-   Filiale

-   Kundennummer

-   Kundenmatchcode

-   Quelle

-   Kundenbestellnummer

-   Kundenbestelldatum

-   Auftragsnummer

-   Status

-   Datum ltz. Statusänderung

-   Fehlertext-Auftragsimport

Register Detail

**Teilbereich Kopfdaten**

-   Quelle (ad)

-   Status (a)

-   Statusdatum (a)

-   Referenznummer (a)

-   Referenzdatum (a)

-   Erfassung-User Code (a)

-   Firma (a)

-   Filiale (a)

-   Auftragsart (a)

-   Kundennummer

-   Ist das einzige Feld das geändert werden darf solange die tc_auf_nr
    > 0 ist

-   Kundennmatchcode (a)

-   Person (a)

-   Titel + Vorname + Nachname

-   AB-Email (a)

-   Kunde GLN (a)

-   Lieferanschrift GLN (a)

-   Lieferanschrift Name1 (a)

-   Lieferanschrift Name2 (a)

-   Lieferanschrift Name3 (a)

-   Lieferanschrift Name4 (a)

-   Lieferanschrift Strasse (a)

-   Lieferanschrift Ländercode (a)

-   Lieferanschrift Postleitzahl (a)

-   Lieferanschrift Ort (a)

-   Kundenbestellnummer (a)

-   Kundenbestelldatum (a)

-   Kopfrabatt (a)

-   Auftragsnummer (a)

-   Auftragsdatum (a)

-   Lieferdatum (a)

-   Versandart (a)

-   Fehlertext (a)

    **Teilbereich Kopftexte**

-   Anzeigeliste mit den Kopftexten

-   Text

-   KZ

    **Teilbereich Positionen**

-   Anzeigeliste mit den Import-Auftragspositionen

-   Positionsnummer Import (a)

-   Artikelnummer

-   Artikelmatchcode (a)

-   Artikel Aktiv (ac)

-   EAN-Nummer lt. SST (a)

-   Artikelnummer lt. SST (a)

-   Kundenartikelnummer lt. SST (a)

-   Artikelbezeichnung lt. SST (a)

-   Menge in Verkaufseinheit (a)

-   Verkaufseinheit (a)

-   Verkaufspreis (a)

-   Rabatt 1 (a)

-   Rabatt 2 (a)

-   Positionsnummer TradeControl (a)

-   Nicht übernehmen (c)

-   Setzt die Auftragspositionsnummer auf -1

-   Positionen können nicht mehr geändert werden, wenn die TC PosNr > 0
    ist.

Auswahlpunkte im Menü "Extras"

-   Daten konvertieren

-   Status muss "u" sein

-   noch nicht konvertierte Felder (Kundennummer, Lieferadresse,
    > Artikelnummer, Menge) werden für den aktuellen Datensatz
    > konvertiert

-   mittels cst_aufimp

-   Daten konvertieren für alle Zeilen

-   für alle Zeilen im Status "u"

-   siehe auch Menüpunkt "Daten konvertieren"

-   Auftrag aufbauen

-   Status muss "v" sein

-   Auftrag wird aufgebaut (siehe Auftragsaufbau)

-   ist der Aufbau ok, so bleibt der Auftrag geöffnet

-   Auftrag stornieren

-   Status darf nicht "a" bzw. "e" sein

-   setzt Auftragsstatus auf "e"

-   setzt Auftragsnummer auf -1

ad Auftragsaufbau

-   Beginn Transaction

-   Locken Debitor

-   Prüfen Status (Auftragsnummer und Status neu einlesen)

-   Wenn der Status bereits „a" ist -- Abbruch mit Meldung „Auftrag
    > bereits aufgebaut"

-   Wenn die AufNr > 0 ist  
    > Prüfen ob der Auftrag vorhanden und noch offen ist, wenn nicht
    > wird wie mit Auftragnummer = 0 fortgesetzt.

-   Neuanlage Auftragskopf wenn TC-AufNr = 0

-   Firma

-   Filiale

-   Auftragsart (wenn ausgefüllt, sonst fix "n")

-   Kundennummer

-   ggf. Lieferadresse

-   Kundenbestellnummer

-   Kundenbestelldatum

-   Sachbearbeiter des Kunden (wenn ausgefüllt)

-   Lieferdatum (wenn ausgefüllt)

-   Versandart (wenn ausgefüllt)

-   Kopfrabatt 1 -- 3 (wenn ausgefüllt)

-   Auftragseingangsart lt. Auftragsimportquelle

-   Wenn die An-E-Mail Adresse ausgefüllt ist

-   Ab-Druck KZ wird auf E-Mail gesetz

-   AB Komid Wert wird mit der E-Mail Adresse beleg

-   Kundenprovisiongruppe (wenn ausgefüllt)

-   Erfassungs-User

-   Nur wenn der User lt. Auftragsimport Tabelle als Person zur Adresse
    > der Firma angelegt ist

-   Speichern Auftragskopf

-   Update AufNr in aufimp

-   Ende Transaktion

-   pro Position mit tc_auf_pos_nr = 0

-   Begin Transaktion

-   Neuanlage Auftragsposition

-   Belegen der Felder

-   Firma

-   Auftragsnummer

-   Ist die Bezugs-Auftrags und Positionsnummer belegt werden diese
    > gesetzt.

-   Artikelnummer

-   Menge

-   Wenn Preis Manuell:

-   Verkaufspreis

-   Rabatt 1 - 5

-   Bei einem diversen Artikel wird

-   der Matchcode durch die ersten x Stellen der Positions-Belegtextes
    > erssetzt

-   ein evt. Positionstext gelöscht

-   der Positions-Belegtext wird wenn belegt als Positionstext mit Druck
    > auf allen Belegen übernommen

-   der Interne Positionstext wird, wenn belegt, als Positionstext mit
    > Druck nur am Kommissionsschein übernommen

-   FremdPosNr aus aufimp_pos_nr nur wenn lt. aufimpquelle aktiviert.

-   Speichern Auftragsposition

-   Update Auftragspositionsbezug in aufimp_pos (wenn nicht mehr 0 --
    > rollback und weiter mit nächster Pos).

-   Bei der letzen Position

-   Update Status in aufimp

-   Wenn die AB-Email Adresse belegt ist -- Einspoolen der AB-Drucks

-   Ende Transaction

-   Bei Fehler in der Verarbeitung wird diese abgebrochen und der
    > ImportAuftrag als fehlerhaft (Setzen Fehlermeldung) markiert
