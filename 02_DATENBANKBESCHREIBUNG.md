@DB TradeControl
@FMT DBMD-1
@ABOUT Datenbankbeschreibung; Client-Server-Warenwirtschaft; TradeControl
@LEGEND @S=Bereich @T=Tabelle/Schema @D=Beschreibung @F=Feld|Typ|Flags|Beschreibung @I=Index @N=Hinweis @E=Ende
@FLAGS pN=Primary-Key-Komponente N; f=Foreign-Key; n=bei Neuanlage, nicht änderbar; g=generiert; r=redundant; ng=nicht generiert
@RULE Alle Inhalte stammen aus der Quelldatei. Word-Formatierung und Merge-Artefakte werden entfernt; fachlich wird nichts ergänzt.

@TITLE Datenbankbeschreibung
@N Client- Server- Warenwirtschaft
@N TradeControl
@S Allgemeines
@T Datentypen
@D char(9)|Alphanumerisches Feld mit 9 Stellen
@D date|Datumsfeld
@D integer(9)|Ganzzahliges Feld. (9) kann weggelassen werden und ist nur eine Information fürr die Feldgrösse auf Bildschirmmasken und Ausdrucken
@D decimal(9,2)|Decimales Feld mit 9 Ziffern, wovon 2 Ziffern Nachkommastellen sind: also 7 Vorkommastellen und 2 Nachkommastellen
@D smallint(4)|ganzzahliges Feld (maximal 4-stellig)
@D computed|logisches Feld welches in der Datenbank nicht vorhanden ist, aber in der Beschreibung verwendet wird / z.B.: offene Menge
@E
@T Endungen
@D Die Endungen von Feldnamen haben folgende Bedeutungen
@D _cd|Code: Alphanumerischer Schlüssel. Z.B. artik_cd (dieser identifiziert einen Artikel eindeutig) / Kommt sowohl als Primärschlüssel (z.B. Artikelnummer in der Tabelle Artikel) als auch als Fremdschlüssel (z.B. Artikelnummer in der Tabelle Auftragsposition) vor.
@D _bez|Bezeichnung
@D _dat|Datum
@D _datz|Datum mit Uhrzeit
@D _fcd|Freier Code: Alphanumerischer Fremdschlüssel (siehe _cd) welcher auf Daten verweist, welche nicht innerhalb der Anwendersoftware verwaltet werden.
@D _ftr|Faktor
@D _jn|Ja/Nein- Feld: enthält „j“ oder „n“
@D _km|Kalendermonat in der Form 199911
@D _knr|Kontonummer in Fibu inklusive Kategorie
@D _kw|Kalenderwoche in der Form 199949
@D _kz|Kennzeichen: Ein Kennzeichen hat im Programm fix codierte Werte, welche den Ablauf steuern
@D _mo|Anzahl Monate
@D _mc|Matchcode
@D _mg|Menge
@D _nr|Nummer
@D _prz|Prozentsatz
@D _wert|Wert
@D _snr|„serial“- Nummer: ursprünglich eine vom Datenbanksystem vergebene eindeutige laufende Nummer pro eingefügtem Datensatz (wird nie zurückgestellt). Wird jetzt von der Anwendersoftware vergeben. / In der Organisationsbeschreibung ein solches Feld interne Nummer genannt (z.B.: interne Auftragsnummer)
@D _tg|Anzahl Tage
@D _txt|Text
@D _wo|Anzahl Wochen
@D _wota|Wochentag (numerisch 1-7, Montag=1)
@E
@T Notationen
@D column(p1)|Feld ist der Primary Key der Tabelle, auch bei Composite-Primary-Keys in der Notation (p1) - (pn) in Verwendung
@D column(f)|Feld ist ein Foreign-Key, das bedeutet, daß es eine Tabelle gibt, in welcher das Feld ein Primary-Key ist.
@D column(n)|Feld wird nur bei der Neuanlage eingegeben, es ist nicht änderbar
@D table(n)|Row dieser Tabelle wird nur angelegt, nicht geändert
@D column(g)|Feld wird nicht eingegeben, sondern generiert
@D table(g)|Row dieser Tabelle wird nicht über Verwaltungsprogramm erzeugt, sondern generiert
@D column(r)|redundantes Feld, alle redundanten Felder sind natürlich automatisch (g)
@E
@S Dimensionen
@N ACHTUNG: alle Date- Felder sind in der Datenbank in Wirklichkeit Datetime bzw. Timestamp mit vollem Wertebereich, werden allerdings nur als Datum eingegeben
@N Folgende DECIMAL- Dimensionen:
@N (09,3) Mengenfaktor zwischen Einheiten
@N (11,2) Preise, Beträge, Werte
@N (12,3) Mengen
@S Locking
@N Immer wenn Auftragsdaten (dazu gehören auch alle Folgedaten wie z.B.Lieferschendaten) geändert werden bzw. deren Werte Voraussetzungen für eine Verarbeitung sind, sind vorher alle in der Transaktion betroffenen Debitoren zu locken. Das Locken der Debitoren muß in folgender Reihenfolge erfolgen:
@N Debitorennummer aufsteigend
@N Firmennummer
@N Immer wenn Einkaufsdaten geändert werden bzw. deren Werte Voraussetzungen für eine Verarbeitung sind, sind vorher alle in der Transaktion betroffenen Lieferanten zu locken. Das Locken der Lieferanten muß in folgender Reihenfolge erfolgen:
@N Lieferanten aufsteigend
@N Firmennummer
@N Immer wenn Lagerstands- bzw. Verfügbarkeitsdaten geändert werden bzw. deren Werte Voraussetzungen für eine Verarbeitung sind, sind vorher alle in der Transaktion betroffenen Artikel zu locken. Das Locken der Artikel muß in folgender Reihenfolge erfolgen:
@N Setartikel vor nicht- Setartikel
@N Artikelnummer aufsteigend
@N Firmennummer
@N Das Artikel Locken muss vor einem eventuellen ?f_serial auf die kartei_snr erfolgen !!!
@S Tabellenbeschreibung
@T abrugr
@D Gruppe von Kunden, welche gemeinsame Abrufaufträge haben / Es gibt eine Dummy- Gruppe mit abrugr_cd = " ", ist ein Kunde dieser Gruppe zugeordnet, kann er nur eigene Abrufaufträge abrufen.
@F abrugr_cd|char(10)|p1|z.B. "ikea"
@F fa_nr|smallint(3)|p2,f
@E
@T adr
@D Adressen für Kunden, Lieferanten, ... / Es gibt einen Dummy-Satz mit adrs_snr = 0 / Als Adresse ist eine Kombination aus / Firmenwortlaut / Anschrift / Kommunikationsdaten / zu verstehen. /  / verändert beim Speichern auch kunde_mc und lief_mc
@F adr_upid|bigint +n|
@F adr_snr|integer(7)|p1|Vergabe über cas.adr_snr
@F adr_mc|char(30)|
@F name1|char(50)||Anschrift
@F name2|char(50)|
@F name3|char(50)|
@F name4|char(50)|
@F strasse|char(50)|
@F land_cd|char(3)|f
@F plz|char(10)|
@F ort|char(50)|
@F natpers_jn|char(1)||Adresse ist natürliche Person / Daten einer natürlichen Person, keiner Firma / Daten lt. DSGVO daher besonders schützenswert
@F sprache_cd|char(5)|f|Sprache (0: " ")
@F adr_info|interner Infotext zur Adresse|
@F email_subordner|char(40)||Subordner zum pfu_oi.emailordner / Office-Funktionalität
@F outlook_jn|char(1)||Outlook-Kontakt soll für diese Adresse mitgepflegt/angelegt werden / Eingabemöglichkeit nur, wenn Zusatzmodul aktiv
@F manuelle_adr_jn|char(1)||dient der Unterscheidung von echten Stammdatenadressen und im Beleg manuell (einmaligen) Adressen / Defaultwert Neuanlage = "n" / Adressen die automatisch von der Kassen Datenübernahme erstelltl werden werden mit "j" angelegt / Maneuelle Adressen werden nicht in der Orts/PLZ Auswahl angezeigt
@E
@I index i1_adr (adr_mc)
@I index i2_adr (land_cd, plz)
@I index i0_adr_upid(adr_upid)
@T adr_pers
@D Person zu einer Adresse / zu jeder Adresse wird automatisch eine Person mit pers_cd = ' ' angelegt. Diese ist in der Personenverwaltung nicht sichtbar und wird im Personenwindow verwaltet. Die Kommunikationsnummern dieser Person sind die der Adresse. / bei Personen einer Adresse einer eigenen Firma erfolgt beim Speichern / ggf. Anlage neuer Datensatz in [pfu_applpers] / applpers_cd = pers_cd / applpers_mc = n_name + " "+ v_name / ggf. Update von [applpers_mc] / where applpers_mc = n_name_db + " " + v_name_db
@F adr_pers_upid|bigint +n|
@F adr_upid|bigint +n|
@F adr_snr|integer(7)|p1,f
@F pers_cd|char(5)|p2|Personencode
@F kurzzeichen|char(5)||Kurzzeichen bei der Korrespondenz
@F persfunktion_cd|char(10)|f|Funktion der Person
@F geschlecht_kz|char(1)||m|männlich
@F geschlecht_kz|char(1)||w|weiblich
@F geschlecht_kz|char(1)||bei Firma/Kunde/Lieferant selbst
@F titel|char(30)||Titel
@F v_name|char(30)||Vorname
@F n_name|char(30)||Nachname
@F geburt_dat|date +n||Geburtsdatum
@F pers_fkz|char(40)||Freies Kennzeichen für Auswertungen
@F werbe_adr_upid|bigint +n|
@F werbe_adr_snr|integer||Werbeadresse der Person / CAS-Funktionalität, Default= werbe_adr_snr der " "-Person / Wird bei Personen der eigenen Firma für die Wohnadresse verwendet. /
@F telefon|varchar(255)|r|Telefonnummer / 1. Vorkommnis in adr_pers_komid mit komidart_kz = 't', sortiert nach komidart.sort_nr
@F mobiltelefon|varchar(255)|r|Mobiltelefonnummer / 1. Vorkommnis in adr_pers_komid mit komidart_kz = 'm', sortiert nach komidart.sort_nr
@F fax|varchar(255)|r|Faxnummer / 1. Vorkommnis in adr_pers_komid mit komidart_kz = 'f', sortiert nach komidart.sort_nr
@F email|varchar(255)|r|Email-Adresse / 1. Vorkommnis in adr_pers_komid mit komidart_kz = 'e', sortiert nach komidart.sort_nr
@F internet|varchar(255)|r|Internetadresse / 1. Vorkommnis in adr_pers_komid mit komidart_kz = 'i', sortiert nach komidart.sort_nr
@F outlook_id|char(255)||Zuordnung zum Outlook-Kontakt / ' ' kein Outlook-Kontakt zugeordnet
@F outlook_zustand_kz|char(1)||Zustandskennzeichen / 'o' Outlook-Daten synchronisiert / 'u' Outlook-Daten müssen noch synchronisiert werden (TC Outlook)
@F pers_aktiv_jn|char(1)||Person ist aktiv
@E
@I index i0_adr_pers_upid (adr_pers_upid)
@I index i01_adr_pers (adr_upid)
@I index i02_adr_pers (werbe_adr_upid)
@T adr_pers_ad
@D Person zu einer Adresse – AD-Zuordnung(en) / Zuordnungstabelle für die Ausgabe der Apollo-SST ("welcher User bekommt welche Kunden") / nur bei Adresse der Firma eingebbar
@F adr_snr|integer(7)|p1
@F pers_cd|char(5)|p2,f|Personencode
@F ad_zuord_kz|char(1)|p3|Zuordnungsart / k…Kunde / c … CAS - Besuchsbericht / f…Filialen (ad_zuord muss numerisch sein) / a…Artikel (im Standard ist ad_zuord *)
@F ad_zuord|char(10)|p4|Bei "k" zB. die Vertreternummer oder die Provisionsgruppe / * = alle möglichen Zuordnungen / Bei "c" der Personencode / * = alle möglichen Zuordnungen / Bei "f" die Fillialnummer(n) / Bei "a" zB. die Warengruppe / * = alle möglichen Zuordnungen
@E
@T adr_pers_fa
@D Firmenspezifische Daten zu einer Person zu einer Adresse / Verwaltung im Fenster der Personen
@F adr_snr|integer(7)|p1
@F pers_cd|char(5)|p2,f|Personencode
@F fa_nr|smallint(3)|p3,f|Einschränkung: / fa.adr_snr = adr_pers_fa.adr_snr
@F pers_lag_cd|char(11)|f|Default Lager des Sachbearbeiters / wenn <> " " übersteuert dieses Lager den Defaultwert lt. fa
@F casreikogrp_cd|char(5)|f|Reiskostengruppencode / Defaultwert: "ang"
@F reiko_adr_kuerzel|char(5)||Kürzel, das bei der Wohnadresse im Reisekostentext verwendet werden soll
@E
@T adr_pers_fcol
@D Freie Columns zur Person / CAS-Funktionalität / (zu Personen mit pers_cd = ' ' gibt es keine Rows)
@F adr_snr|integer(7)|p1
@F pers_cd|char(5)|p2,f|Personenkurzzeichen
@F pers_fcol_cd|char(10)|p3,f|Code der Art des freien Kennzeichens
@F pers_fcol_wert|char(40)||Column- Wert
@E
@T adr_pers_fgr
@D Zuordnung Adress_Person -> Freie Gruppe / CAS-Funktionalität
@F adr_snr|integer(7)|p1
@F pers_cd|char(5)|p2,f
@F fgrart_cd|char(10)|p3|Code der Art der freien Gruppe
@F fgr_cd|char(10)|f|Code der freien Gruppe
@E
@T adr_pers_ftxt
@D Freies Adress_Personentexte / CAS-Funktionalität
@F adr_snr|integer(7)|p1
@F pers_cd|char(5)|p2
@F adr_pers_ftxt_cd|char(10)|p3,f|Code der Art des freien Textes
@F txt_typ_kz|char(1)|p3|Texttyp / "r" Richtext / wenn [param.appl_txt_kz <> "p"] / Standardfont "Arial 10" / "p" Plaintext / wenn [param.appl_txt_kz = "p"]
@F zeile_nr|smallint|p5|Zeilennummer
@F adr_pers_ftxt_txt|varchar(max)||Freier Text / generierter Plaintext (adr_pers_ftxt_rtxt), wenn [txt_typ_kz = "r"] / eingegebener Text, sonst
@F adr_pers_ftxt_dbid|integer identity||ROWID für Retrieve Richtext / durch DB-Default mit serieller Nummer belegt
@F adr_pers_ftxt_rtxt|varbinary(max)||freier Personentext Richtext / wenn [txt_typ_kz = "p"], durch DB-Default mit Leerstring belegt
@E
@I unique index i1_ adr_pers_ftxt (adr_pers_ftxt_dbid)
@T adr_pers_komid
@D Kommunikations- Identifikationscodes zur Person / (Telefonnummer, Faxnummer, Email, ...) / (Die Rows der Personen mit pers_cd = ' ' werden im Personen- Window verwaltet.)
@F adr_pers_komid_upid|bigint +n|
@F adr_upid|bigint +n|
@F adr_snr|integer(7)|p1
@F adr_pers_upid|bigint +n|
@F pers_cd|char(5)|p2,f|Personenkurzzeichen
@F komidart_cd|char(10)|p3,f|Code der Art des freien Kennzeichens
@F komid_wert|varchar(255)||z.B. Telefonnummer / Faxnummer / EmailAdresse / Telefon- und Faxnummer sollten im Format "+43 (1) 25038-128 eingegeben werden / bei Einsatz von GFI-Faxlösung und komidart_kz in ("f", "t"), wird bei der Eingabe wie folgt geprüft / es sind nur Ziffern, Leerstellen und die Zeichen "+", "(", ")", "-" erlaubt / 1. Stelle muss ein "+" sein / die Zeichen "+", "(" und ")" müssen in dieser Reihenfolge im String vorkommen und müssen durch mindestens eine Ziffer getrennt sein / die Zeichen "+", "(" und ")" dürfen jeweils nur einmal im String vorkommen / die Zahl zwischen den Zeichen "(" und ")" darf nicht mit 0 beginnen / zwischen den Zeichen "(" und ")" und nach dem Zeichen "+" darf keine Leerstelle vorkommen / wird das Sonderzeichen "-" verwendet, darf es erst nach der Ziffer, die nach dem Zeichen ")" steht vorkommen / die letzte Stelle darf kein Sonderzeichen sein
@F komid_pers_anteil|varchar(50)||Personeneigener Anteil an komid_wert: / Ist dieser ausgefüllt, kann komid_wert im Verwaltungsprogramm nicht eingegeben werden sondern wird aus adr_pers_komid.komid_wert mit pers_cd = ' ' und gleichem komidart_cd und komid_pers_anteil zusammengesetzt. Die Zusammensetzungsmethode hängt von komidart_kz ab.
@F ek_hpt_jn|char(1)||j…Hauptkommunikationsnummer für EK und komidart_cd / es darf nur einen Satz mit ‚j’ pro adr_snr und komidart_cd geben
@F vk_hpt_jn|char(1)||j…Hauptkommunikationsnummer für VK und komidart_cd / es darf nur einen Satz mit ‚j’ pro adr_snr und komidart_cd geben
@F mach_uni_ek|char(16)||wenn ek_hpt_jn = ‚j’ komidart_kz lt. komidart / sonst pers_cd + ‚-‚ + komidart_cd
@F mach_uni_vk|char(16)||wenn vk_hpt_jn = ‚j’ komidart_kz lt. komidart_cd / sonst pers_cd + ‚-‚ + komidart_cd
@F adr_pers_komid_snr|integer(9)||wird laufend vergeben / ist eindeutiger Index für view [pfu_komid]
@N /  /
@E
@I unique index i1_adr_pers_komid ( adr_snr, mach_uni_ek )
@I unique index i2_adr_pers_komid ( adr_snr, mach_uni_vk )
@I index i0_adr_pers_komid_upid (adr_pers_komid_upid)
@I index i01_adr_pers_komid (adr_upid)
@I index i02_adr_pers_komid (adr_pers_upid)
@T adr_versand
@D Versanddaten für die Adresse
@F adr_snr|integer(7)|p1
@F bex_lc_plz|char(4)||Bahnlagernd: Postleitzahl des Logistikcenters
@F bex_lc_mc|char(20)||Bahnlagernd: Logistikcenter
@F bex_kunde_nr|char(10)||Kundennummer bei der Bahn
@F bex_serviceart_kz|char(2)||Bahnexpress-Serviceart / 'be' = BahnExpress / 're' = RailExpress / 'rs' = RailStandard
@F bex_unfrank_exw_jn|char(1)||Unfrankiert EXW / 'j' = Empfänger trägt die Frachtspesen / 'n' = Absender trägt die Frachtspesen / ist fix 'n', wenn bex_serviceart_kz = 're'
@F versand_info|char(255) n+||Versandinfo
@E
@T adrid
@D Adressidentifikationscode
@F adrid_cd|char(40)|p1|eine Identifikation für eine Adresse / wird von TC bei Adressen-Änderungsimport verwendet / z.B.: Firmenbuchnummer oder Heroldnummer
@F adrid_kz|char(1)|p2|Art der Identifikation / kann durch Customizing bestimmt werden / standardmäßig ist nichts vorgesehen
@F adr_snr|integer(7)|ng
@E
@I unique index i1_adrid (adr_snr, adrid_kz)
@S apollo
@T apollo_auf
@D Apollo Auftragsimport / wird über Apollo TCP Request befüllt
@F apollo_auf_snr|bigint (p)|
@F apollo_uuid|varchar(50)||Unique User Identifyer / eindeutige Nummer der App-Installation
@F apollo_aa_id|integer||eindeutige Apollo-Besuchsbericht-ID / ist nur in Verbindung mit [apollo_uuid] eindeutig, da in der App vergeben
@F fa_nr|smallint(3)||Firma
@F fil_nr|smallint(3)||Filiale
@F usr_cd|char(10)||User Kontakt
@F erf_dat|date||Erfassungsdatum
@F kunde_cd|char(10)||Kundennummer
@F aufart_cd|char(2)||Auftragsart / n = Normalauftrag / o = Offert
@F lief_adr_snr|integer||Adressnummer Lieferung Auftrag / ist 0, wenn Adresse manuell eingegeben wurde
@F kunde_baust_cd|char(10)||Baustellencode
@F name1|varchar(50)||Adressdaten nur belegt wenn lief_adr_snr = 0 / in TC wird neue Adresse angelegt werden
@F name2|varchar(50)|
@F name3|varchar(50)|
@F strasse|varchar(50)|
@F land_cd|char(3)|
@F plz|varchar(10)|
@F ort|varchar(50)|
@F kd_best_txt|varchar(40)||Bestellnummer Kunde
@F kd_best_dat|date||Bestelldatum Kunde
@F kunde_sb_pers_cd|char(5)||Sachbearbeitercode Kunde (= Besteller)
@F zuab_kz|char(1)||z = Zustellung / a = Abholung
@F einzelrechnung_jn|char(1)||Einzelrechnung erwünscht
@F teillief_jn|char(1)||Teillieferung erlaubt
@F lief_dat|date +n||Lieferdatum
@F skonto1_prz|decimal(4,2)||1. Skontoprozentsatz
@F skonto1_tg|smallint(3)||dazu Ziel- Tage
@F skonto2_prz|decimal(4,2)||2. Skontoprozentsatz
@F skonto2_tg|smallint(3)||dazu Ziel- Tage
@F netto_tg|smallint(3)||Ziel- Tage für Netto- Zahlung
@F vkrabk1|decimal(4,2)||Kopfrabatt 1
@F vkrabk2|decimal(4,2)||Kopfrabatt 2
@F vkrabk3|decimal(4,2)||Kopfrabatt 3
@F waehrung_cd|char(4)||Wählungscode lt. Debitor
@F iu_jn|char(1)||Inkl. Ust / derzeit fix "n"
@F bel_txt|varchar(500)||Endtext für Andruck auf Belegen / ein Zeilenumbruch wird mit \n übermittelt
@F int_txt|varchar(500)||Interner Text / wird auf keinem Beleg gedruckt / Zeilenumbruch möglich
@F stammdaten_datz|datetime||Datum und Uhrzeit der Stammdaten / für Nachvollziehbarkeit Preisfindung, Zahlungskondition etc.
@F ab_an_email|varchar(250)||Wenn ausgefüllt wird nach einem erfolgreichen Import eine AB/Offert an diese E-Mail Adresse gesendet. / Beim Import müssen die Beistriche (",") durch Strichpunkte (";") ersetzt werden.
@F auf_nr|integer||Auftragnummer in TC / Bei Insert 0 / Nach Import aller Position in TC die letzte Auftragsnummer / -1 bei Fehler im Kopf
@F err_txt|varchar(200)||Fehlertext – ist bei Import Fehlern beleg
@E
@T apollo_auf_pos
@D Apollo Auftragsimport Positionen / wird über Apollo TCP Request befüllt
@F apollo_auf_snr|bigint|p1
@F pos_snr|bigint|p2
@F artik_cd|char(20)|
@F fa_nr|smallint|r
@F artik_laenge|decimal(7,1)||Länge
@F auf_best_mg|decimal(12,3)||Menge in eh_cd
@F eh_cd|char(5)||Einheit / eine Einheit lt. [A_artik_eh]
@F vkpr|decimal(11,2)||Verkaufspreis lt. waehrung_cd und iu_jn
@F vkrab1|decimal(4,2)|
@F vkrab2|decimal(4,2)|
@F vkrab3|decimal(4,2)|
@F vkrab4|decimal(4,2)|
@F vkrab5|decimal(4,2)|
@F vkzus_betr|decimal(12,3)|
@F preis_manu_jn|char(1)||Preis od. Rabatte wurde manuell erfasst
@F vkrabk_jn|char(1)||Kopfrabattfähig
@F pos_bel_txt|varchar(500)||Wird auf allen Belegen gedruckt (zusätzlich zum Standard Artikeltext) / Bei einem diversen Artikel muss dieser Text als Artikelmatchcode und Artikeltext (ersetzend) übernommen werden / Zeilenumbruch möglich
@F pos_int_txt|varchar(500)||Wird nur am Kommissionsschein gedruckt / Zeilenumbruch möglich
@F pos_zus_txt|varchar(30)||Zusatztext (Ausprägung, Farbton usw.)
@F offert_pos_snr|bigint +n||Zugeordnete Position / Bei einer Auftragsposition die aus einem Apollo Offert entstanden ist, die Auftragsnummer des Offertes – ist nur gemeinsam mit Apollo-UID eindeutig.
@F archiv_offert_nr|integer +n||Zugeordnete Auftragsnummer / Bei einer Auftragsposition, die aus einem TC Offert aus dem Beleg-Archiv übernommen wurde, die A_belpos.ein_auf_nr des Offertes
@F archiv_offert_pos_nr|smallint +n||Zugeordnete Auftragspositionsnummer / Bei einer Auftragsposition, die aus einem TC Offert aus dem Beleg-Archiv übernommen wirde, die A_belpos.bel_pos_nr der Offertposition
@F auf_nr|integer||Auftragnummer / 0 nach Import / Auftragsnummer die erstellt wurde / -1 bei fehlerhafter Position
@F auf_pos_nr|smallint||Auftragspositionsnummer (siehe auf_nr)
@F err_txt|varchar(200)||Fehlertext der Auftragspositionserstellung
@E
@I index i1_apollo_auf_pos (auf_nr, auf_pos_nr, apollo_auf_snr)
@I index i2_apollo_auf_pos (pos_snr)
@T apollo_fabu
@F b|Fahrtenbuchschnittstellendaten Apollo|
@F apollo_fabu_snr|decimal(14,0) (p)|
@F apollo_uuid|varchar(50)||Unique User Identifyer / eindeutige Nummer der App-Installation
@F apollo_fb_id|integer||eindeutige Apollo-Fahrtenbucheintrag-ID / ist nur in Verbindung mit [apollo_uuid] eindeutig, da in der App vergeben / Damit ist auch eine Änderung von bereits Übermittelten Fahrtenbucheinträgen möglich
@F kfz_cd|char(10)||Fahrzeug
@F usr_cd|char(10)||User Kontakt
@F von_km|integer||Kilometerstand Reisebegin
@F bis_km|integer||Kilometerstand Reisende
@F erf_dat|date||Erfassungsdatum
@F von_dat|date||Von Datum
@F von_uhrzeit|char(5)||VonZeit (HH:MM)
@F bis_dat|date||Bis Datum
@F bis_uhrzeit|char(5)||BisZeit (HH:MM)
@F privat_jn|char(1)||Privatfahrt j/n
@F fabu_txt|varchar(255)||Zusatztext
@F fabu_wt|decimal(10,2)||Wert (z.B. Tanken)
@F fabu_wt_txt|varchar(70)||Text zum Wert
@F fa_nr|smallint||Firmennummer für Kunden
@F start_kunde_cd|char(10)||Kundennummer Start Adresse / wenn leer kein Kunde
@F start_name1|varchar(50)||Nur bei manueller Adresse belegt
@F start_name2|varchar(50)|
@F start_name3|varchar(50)|
@F start_strasse|varchar(50)|
@F start_land_cd|char(3)|
@F start_plz|varchar(10)|
@F start_ort|varchar(50)|
@F ziel_kunde_cd|char(10)||Kundennummer Start Adresse / wenn leer kein Kunde
@F ziel_name1|varchar(50)||Nur bei manueller Adresse belegt
@F ziel_name2|varchar(50)|
@F ziel_name3|varchar(50)|
@F ziel_strasse|varchar(50)|
@F ziel_land_cd|char(3)|
@F ziel_plz|varchar(10)|
@F ziel_ort|varchar(50)|
@F heimfahrt_jn|char(1)||Es handelt sich um die Heimfahrt
@F fabu_snr|bigint||Fahrtenbuchnummer / 0 = noch nicht im TC aufgebaut bzw abgearbeitet
@E
@I index i1_apollo_fabu (fabu_snr)
@T aragrp
@D Ara Gruppen / Es gibt einen Satz mit <leer> = „Ohne Zuordnung“
@F aragrp_cd|char(10)|p1|Ara Gruppe / Satz mit Leer anlegen / In Liste nicht anzeigen
@F aragrp_mc|char(40)||Matchcode
@E
@T archiv
@D Archivstamm / gibt an, welche Belege archiviert werden
@F archiv_beleg_kz|char(2)|p1|Belegarten mit Vergabe Barcode über virtuelle Tabelle [archiv1] / „ab“ Auftragsbestätigung/Offert / "al" Ausgangslieferschein / "ko" Kommissionsschein / „vr“ Verkaufsrechnung / Belegarten mit Eingabe Barcode im Verwaltungsfenster / Vergabe über Pickerldruckprogramm über virtuelle Tabelle [archiv2] / "be" Bestellung (Lieferantenproforma) / "el" Eingangslieferschein / "er" Eingangsrechnung / „bn“ Belastungsnote
@F druckart_cd|char(8)||Druckart f. gescanten Beleg / für Anlage [pfu_scanzu]
@F scan_archiv_loe_jn|char(1)||urspr. Dokument löschen / für Anlage [pfu_scanzu]
@F barcode_kz|char(1)||Barcodekennzeichen für Vergabe (al, ko) und Prüfung (be,el,er) / "e" ean13 / Barcode wird nach Vergabe auf 13 Stellen Alphanumerisch mit EAN-13 Prüfziffer erweitert (rechtsbündig mit Vorlaufnullen) / "c" code39 / Barcode wird nach Vergabe nicht mehr verändert
@E
@T archivart
@D Archivartentabelle für externes Dokumentenarchiv / wird von Modul cst_archiv verwendet
@F archivart_kz|char(20)|p1|Art der Archivierung / "dokuware" / "easyarchiv" / „jetscan“ / "tcscan" / etc.
@F archivart_mc|char(40)||Bezeichnung
@F archivart_info|text +n||Info
@F archiv_viewer_kz|char(1)||"p" Programm, das beim Anzeigen gestartet wird / "l" Link, der beim Anzeigen in Standardbrowser aufgerufen wird
@E
@T archivart_prog
@D Programme zur Archviart
@F archivart_kz|char(20)|p1|Art der Archivierung
@F archivartprog_kz|char(10)|p2|zB: "v" Viewer / "c" Clipboard / "i" Pfad für Import /  / Anmerkung Easyarchiv / "c"- und "i"-Sätze nicht angelegt / Anmerkung Jetscan / keine Einträge vorhanden
@F pfad|varchar(255)||Pfad+ggf. Dateiname zur entsprechenden Funktion /  / Anmerkung Eaysarchiv - Viewer-Link / z.B: "http://172.16.10.13:8080/jsp/qv?pri=DA40927" / DA40927 versteht sich als Lizenznummer
@E
@T archivart_dok
@D Dokumente, welche archiviert werden sollen
@F archivart_kz|char(20)|p1|Art der Archivierung
@F druckart_cd|char(20)|p2|Druckart lt. pfu_druckart / ist hier vorrausschauender Weise in der Datenbank 20 Stellen / keine Auswahl über DDDW / wird Dokument nur gescannt, aber nie gedruckt (z.B: Einganglieferschein oder Eingangsrechnung) muss Satz mit Dummy-Druckart ("erech_scan") angelegt werden
@F beleg_table|char(20)||entsprechende Tabelle in TC mit den Belegdaten / für Beschlagwortung / für Schnittstellentabelle / auf / vlfs / vrech / best / elfs / erech / erech_bn
@F archiv_belegtyp_fkz|char(10)||Belegtyp für Archiv
@E
@T archivart_param
@D Parameter der Archivart für Aufruf / zB: Viewer bzw. Clipboard / Parameter bei Viewer bzw. variable Bestandteile des Internet-Link / Anmerkung Aufbau Aufrufstring Viewer / Programmaufruf / Programmpfad + " -" + ParameterName1 + "-" + ParameterWert1 … / Parameterwert unter doppelten Anführungszeichen / Aufruf Internetlink / Linkpfad + ParameterName1 + "=" + ParameterWert1 … / ParameterName beginnt mit "&" / ParameterWert ohne Anführungszeichen
@F archivart_kz|char(20)|p1|Art der Archivierung
@F w_name|char(80)|p2|Windowname
@F zeile_nr|smallint|p3|Zeilennummer
@F par_name|char(20)||Parametername für Aufruf des Archivs
@F par_col_name|char(40)||Parameterwert / Wert ist mit " eingegrenzt (z.B: "Fixwert") / konstanter Wert / sonst / Name des Datawindow-Feldes in idw_neu des Windows, welches den Parameterwert trägt
@F sort_nr|Smallint||Sortiernummer für Aufruf Docuware Reihenfolge der Parameterübergabe
@F fixwert_jn|char(1)||Fixwert
@E
@T artik
@D Artikel- Stammdaten / im BeforeUpdate bei der Neuanlage: / Anlage von vkkond für Listenpreis und setzen von vkkond_snr im DW /  / Im Select- Statement der "Liste" muß artik_fcol mitselektiert werden
@F artik_upid|bigint +n|
@F artik_cd|char(20)|p1|Artikelnummer / Vergabe/Kontrolle mittels Tabelle nummern
@F fa_nr|smallint(3)|p2,f|Firmennummer
@F artik_mc|char(40)||Artikelmatchcode
@F artik_kz|char(2)|n|n|Normalartikel (Warenbewegung)
@F artik_kz|char(2)|n|d|diverser Artikel (Warenbewegung) / lagfuehr_kz = 'k'
@F artik_kz|char(2)|n|s|Set (Warenbewegung der Unterartikel) siehe auch artik_set / lagfuehr_kz = 'k' / Im Verkauf wird als Duest die Summe der Einzelduests mal Teilmengen herangezogen – dies gilt ggf. rekursiv
@F artik_kz|char(2)|n|p|Produktionsset: abhängig von Auftragsart: siehe auch artik_set / Normalauftrag: wie Normalartikel / Produktionsauftrag: Unterartikel wie bei Set, Hauptartikel löst Zugang aus (umgekehrte Warenbewegung) / lagfuehr_kz <> 'k'
@F artik_kz|char(2)|n|v|Verrechnungsartikel (keine Warenbewegung) / sind automatisch freigegeben (Vorschlag) / lagfuehr_kz = 'k' / Werden beim Kommissionsschein nicht angedruckt, sind dem ersten Kommissionsbreich lt. Lager (Artikelkommissionsbreich wird ignoriert) zugeordnet. Wenn im Auftrag kein solcher vorkommt, dann der erste des Auftrags.
@F artik_kz|char(2)|n|w|WartungsVertragsLeistungsartikel / Leistung in einem Wartungsvertrag / lagfuehr_kz = 'k'
@F artik_kz|char(2)|n|k|Konfigurationsartikel / Artikel in ein Konfigurierbarer Artikel für den WebShop und wird nur für den WebShop Export verwendet / Die Detailartikel sind unter artik_set verspeichert / lagfuehr_kz = 'k'
@F lagfuehr_kz|char(2)|n|k|Keine Lagerführung / duestrech_jn = 'n'
@F lagfuehr_kz|char(2)|n|n|normale Lagerführung
@F lagfuehr_kz|char(2)|n|c|Chargenartikel
@F lagfuehr_kz|char(2)|n|g|Gerät mit Gerätenummer/Seriennummer (Lagerführung Warenbewegung)
@F ablaufdat_jn|char(1)||bei lagfuehr_kz = 'c': / Chargen dieses Artikels werden mit Ablaufdatum geführt / bei lagfuehr_kz <> 'c': / fix "n"
@F duestrech_jn|char(1)|n|folgende Konsequenzen, wenn = "j": / Duestrechnung beim Warenzugang / Wenn Summe über alle Lagerstände = 0 wird nach Eingabe einer Einkaufspreiskondition der Einstandspreis errechnet und in artik.duest abgestellt. / Duest darf im Artikelstamm nicht eingegeben werden / Bei der Auftragspositionserfassung darf der Duest nie eingegeben werden.
@F set_frei_kz|char(1)||'s' = Freigabe auf Setebene / 't' = Freigabe auf Teilebene / Es müssen alle anderen set_- Felder 't' sein! / Wird bei der Anlage einer Auftragsposition ein solcher Artikel gewählt, wird für den Sethauptartikel keine Position angelegt und für die Teile Normalpositionen (auf_pos_kz='n') angelegt. / in einem Set mit mehr als einer Stufe muss set_frei_kz immer = 's' sein
@F set_preis_dru_kz|char(1)||'s' = Setgesamtpreis auf Kundenbelegen drucken / Achtung: ust_cd muß auch, wenn set_fibu_kz = "t", auf Setebene / ausgewertet werden. Dabei könnten allerdings Ust- reine Erlöskonten / mit unterschiedlichen Ust- Sätzen befüllt werden. / (ust_cd aus Set, Erlöskonto aus Teil) / 't' = Teilpreise auf Kundenbelegen drucken / Achtung: ust_cd muß auch, wenn set_fibu_kz = "s", auf Teilebene / ausgewertet werden. Dabei könnten allerdings Ust- reine Erlöskonten / mit unterschiedlichen Ust- Sätzen befüllt werden. / (ust_cd aus Teil, Erlöskonto aus Set)
@F set_stat_kz|char(1)||'s' = Statistik auf Setebene befüllen / 't' = Statistik auf Teilebene befüllen
@F set_fibu_kz|char(1)||'s' = Fibuüberleitung (Erlös / Kore- Aufteilung) auf Setebene, die Ust- Zuordnung erfolgt allerdings lt. set_preis_dru_kz.. / 't' = Fibuüberleitung auf Teilebene, die Ust- Zuordnung erfolgt allerdings lt. set_preis_dru_kz.
@F set_teil_dru_kz|char(1)||Ausdruck auf Kundenbelegen: / 's' = nur Sethauptartikel / set_preis_dru_kz muß 's' sein / 't' = nur Teile / set_preis_dru_kz muß 't' sein / 'b' = beide
@F auf_prod_best_kz|char(1)||Kennzeichen bestellte Menge bei Produktionssets / regelt, wann die bestellte Menge bei Produktionssetauftragspositionen änderbar ist / 's' Standard / die bestellte Menge ist fix mit [auf_prod.prod_best_mg] * [artik_set.teil_mg] belegt. / bei der Neuanlage eines Produktionsauftrags muss für manuell erfasste Positionen die entspr. Teilmenge definiert werden / 'f' frei änderbar / die bestellte Menge ist änderbar wie bei Normalauftragspositionen – dies kann allerdings auch im Set- DW erfolgen – siehe Org / das Hinzufügen und Löschen von Positionen ist ist möglich wie bei Normalauftragspositionen – dies kann allerdings auch im Set- DW erfolgen – siehe Org / auch hier gilt: [auf_prod.prod_best_mg] * [auf_pos.teil_mg] = [auf_pos.auf_best_mg]
@F keh_cd|char(5)|f|kleinste Einheit / Änderung betrifft nur die Nomenklatur, jedoch nicht den Inhalt der Verpackung
@F veh_cd|char(5)|f|Verkaufseinheit = Lagereinheit / Änderung betrifft nur die Nomenklatur, jedoch nicht den Inhalt der Verpackung
@F keh_veh_mg|decimal(9,3)||Anzahl Keh's in einer Veh / Ist bei Geräten fix 1
@F vkpr_keh_veh_kz|char(1)||Verkaufspreismengeneinheit: / k = Verkaufspreis in kleinster Einheit, v = in Verkaufseinheit
@F vkpr_pro_mg|decimal(4,0)||Verkaufspreis bezieht sich auf diese Anzahl Einheiten lt. vkpr_keh_veh_kz
@F vkpr_ftr|Decimal(13,7)|g|Faktor, sodaß gilt: / Menge * Preis * Faktor = Positionsbetrag / vkpr_keh_veh_kz = k: / vkpr_ftr = keh_veh_mg / vkpr_pro_mg / vkpr_keh_veh_kz = v: / vkpr_ftr = 1 / vkpr_pro_mg
@F vk_los_eh_cd|char(5)|f|Losgröße
@F vk_los_mg|decimal(9,3)||Losgröße Verkauf in veh / Verkaufsmenge in veh solte ein Vielfaches von los_mg sein / Prüfung bei Auftragserfassung
@F vk_los_pruef_kz|char(1)||Mengeneingabe in Auftragserfassung auf Vielfaches der Losgröße prüfen / '-' …keine Prüfung / 'h' …Hinweis / 's'…Sperre
@F preis_artik_upid|bigint +n||ID des Preisartikels
@F preis_artik_cd|char(20)|f|Artikel, der für die Preisfindung herangezogen wird / bestimmt artikvkkond_snr
@F artikvkkond_upid|bigint +n|
@F artikvkkond_snr|integer|f,g|Verkaufskondition, in der der Artikelgrundpreis verspeichert ist / dies ist die vkkond_snr des Preisartikels / lt. preis_artik_cd
@F o_artikvkkond_snr|integer|f,g|Originalverkaufskondition des Artikels / lt. artik_cd
@F artikvkkondgr_cd|char(10)|f|Artikelverkaufskonditionsgruppe
@F artik_aktiv_jn|char(1)||Artikel ist aktiv, d.h. kann verwendet werden
@F auslauf_jn|char(1)||Artikel ist Auslaufartikel / wenn 'j' / Artikel darf nicht bestellt werden / ar_rueck_aufb_jn = 'n'
@F ar_rueck_aufb_jn|char(1)||Rückstände aufbauen / wenn 'n' / Artikel darf nicht in Rückstand genommen werden / (auf_pos.auf_best_mg = auf_pos.auf_frei_mg)
@F min_lag_mg_kz|char(1)||f|fix
@F min_lag_mg_kz|char(1)||e|errechnet
@F bedarfbeobzeit_tg|decimal(4,0)||Beobachtungszeitraum für den durchschnittlichen Tagesbedarf in Tagen
@F mehrbest_prz|decimal(3,0)||Die Bestellmenge beim Bestellvorschlag errechnet sich: / Mindestbestand +% mehrbest_prz - verfügbare_menge ...
@F vkrabk_ftr|smallint(1)||Auftragskopfrabatt soll bei diesem Artikel zur Anwendung gebracht werden. / Feld hat die Werte 0 oder 1 / Auftragskopfrabatte werden bei der Berechnung mit vkrabk_ftr multipliziert / Feld wird bei Auftragspositionsneuanlage in Tabelle auf_pos übernommen
@F vk_skonto_jn|char(1)||Artikel ist verkaufsseitig skontofähig
@F vk_stat_ftr|smallint(1)||Artikel wird verkaufsseitig in die Statistik gerechnet / ist normalerweise 1 / kann mit Berechtigung auf 0 gesetzt werden
@F artikerl_cd|char(10)|f|Erlöskontenzuordnungscode (beinflußt auch Ust Verkauf)
@F artiksach_cd|char(10)|f|Bestands/Wareneinsatzkontenzuordnungscode (beeinflußt auch Ust Einkauf)
@F artikkst_cd|char(10)|f|Kostenrechnungszuordnungscode
@F artikprovgr_cd|char(10)|f|Provisionsgruppe Artikel / Vorschlag für auf_pos / siehe Tabelle provision
@F artikkomber_cd|char(10)|f|Artikelkommissionsbereich / Dummy-Satz darf ausgewählt werden
@F artik_info|+n||interner Informationstext
@F gar_mo_vk|smallint(3)||Garantiemonate Verkauf
@F gar_mo_ek|smallint(3)||Garantiemonate Einkauf
@F gewicht_bto|decimal(8,3)||Gewicht inkl. Verpackung in KG
@F ara_jn|char(1)||Artikel ist ARA- pflichtig (Info)
@F is_zollta_nr|char(8)|f|Intrastat Zolltarifnummer / Die aktuellen ZTNRs können hier abgefragt werden: https://www.statistik.at/ueber-uns/erhebungen/unternehmen/aussenhandel-intrastat
@F is_urspland_cd|char(3)|f|Intrastat Ursprungsland
@F is_masse|decimal(8,3)||Intrastat Gewicht in kg je veh / = Nettogewicht
@F is_veh_bmaeh_ftr|decimal(12,6)||Intrastat Umrechnungsfaktor von veh auf besondere Maßeinheit lt. Zolltarif
@F duek_b|decimal(15,6) +n|g|DuEk bewertet pro Lagereinheit in GW / wird nur bei duestrech_jn = 'j' geführt / Logik DuEst-Gruppe siehe [artik.duest]
@F duest_b|decimal(15,6) +n||DuEst bewertet pro Lagereinheit in GW / wird nur bei Eingangsrechnung ermittelt / wird bei duestrech_jn = 'n' durch manuelle Eingabe von duest bestimmt / Logik DuEst-Gruppe siehe [artik.duest]
@F duest_abgew_b|decimal(15,6) +n||DuEst pro Lagereinheit abgewertet / wird sonst 1:1 wie duest_b behandelt / kann durch Abwertungsprogramm vermindert werden / Logik DuEst-Gruppe siehe [artik.duest]
@F duest|decimal(15,6) +n||DuEst pro Lagereinheit in GW / darf im Verwaltungsprogramm nur mit Berechtigung verändert werden. / Eingabe, wenn keine Lagerführung [duestrech_jn = "n" and lagfuehr_kz = "k"] / Eingabe, wenn [duestrech_jn = "n"] und alle Eigenlager [lag_kz = "e"] die selbe DuEst-Gruppe besitzen - alle [artik_lag]-Sätze der Eingenlager werden mitgeändert / wird durch DuEst-Rechnung bestimmt, wenn [duestrech_jn = "j"] und alle Eigenlager die selbe DuEst-Gruppe besitzen / Wenn der Duest NULL ist, muß er bei der Auftragsposition eingegeben werden, siehe auch artik.duestrech_jn
@F min_db_prz|decimal(5,2) +n||Mindestdeckungsbeitragsprozentsatz / is null keine Auswertung / is not null Meldung beim Speichern der Auftragsposition wenn mind_db_proz nicht erreicht
@F ka_duest_prz|decimal(5,2)||Kassen Duest Prozentsatz / Wenn bei Übernahme von Belegposition aus der Kassa duest null ist, so wird der duest aus Nettoverkaufspreis * ka_duest_prz errechnet
@F ltzt_abw_dat|date +n|g|Datum letzte Abwertung
@F artik_anl_dat|date|ng|Datum Artikelanlage
@F sum_prod_off_mg|decimal(12,3)|g|= sum (prod_off_mg) from auf_prod
@F sum_best_off_mg|decimal(12,3)|g|= sum(best_off_mg * best_lag_ftr * best_pos.keh_eeh_mg / artik.keh_veh_mg) from best_pos
@F sum_ra_best_off_mg|decimal(12,3)|g|= sum(best_off_mg * best_pos.keh_eeh_mg / artik.keh_veh_mg) from best_pos where bestart_cd = "r"
@F sum_abr_auf_off_mg|decimal(12,3)|g|= sum(auf_off_mg) from auf_pos where aufart_cd = "a"
@F disp_umb_off_mg|decimal(12,3)|g|= sum(auf_off_mg * auf_lag_ftr) from auf_pos where auf.aufart_cd = 'i' and kunde.kunde_lag_cdlag.dispo_jn = 'j' / + sum(lief_mg*auf_pos.lag_ftr) from vlfs_pos where auf_pos wie oben and vlfs_pos.geg_kartei_snr = 0
@F disp_auf_off_mg|decimal(12,3)||= - sum ( auf_off_mg * auf_lag_ftr ) from auf_pos where lag.dispo_jn = 'j' and auf_off_mg > 0 / Reservierte Menge für Verfügbarkeit bei der Disposition
@F disp_lag_mg|decimal(12,3)||= sum ( artik_lag_sub.lag_mg ) where lag_dispo_jn = 'j' / Lagerstand für Verfügbarkeit bei der Disposition
@F ale_kartei_snr|integer|r|kartei_snr des letzten Einkaufs, 0 = noch nie eingekauft
@F alv_kartei_snr|integer|r|kartei_snr des letzten Verkaufs, 0 = noch nie verkauft
@N Service:
@F muss_geraet_cd_jn|char(1)||Serviceauftrag muß sich auf genau eine Gerätenummer beziehen / ist bei artik_kz <> "g" immer "n"
@F s_artikart_cd|char(10)|f|Artikelart: z.B. Arbeitszeit, Wegpauschale, Wegzeit, Material
@F s_artik_info|varchar(255)||interner Informationstext Service
@F s_verrechart_cd|char(5)|f|Verrechnungsart für Service- Auftragspositionen, welche sich auf eine Wartungsvertragsposition, dessen Wartungs- Leistungs- Artikel dieser Artikel ist, beziehen. / ist bei artik_kz <> "w" immer ""
@F bild_auf_ab_jn|char(1)||Bild soll auf AB gedruckt werden
@F bild_auf_off_jn|char(1)||Bild soll auf Offert gedruckt werden
@F ao_snr|integer||AO-Snr / ist eindeutig / dient zum Finden eines AOs
@F internet_link|varchar(255)||Internetlink
@F aragrp_cd|char(10)|f|Ara-Gruppe
@F vargew_jn|char(1)||Artikel ist ein Gewichtsartikel / im Standard fix ‚n‘ und rechts draußen / wird für Ableitungen mit Touch Kassa mit Waage verwendet / wenn ‚j‘: / keh_veh_mg fix 1 / vkpr_pro_mg fix 1 / keh_cd = veh_cd lt. pfu_param („kilo_eh_cd“)
@F taragew_kg|decimal(5,3)||Taragewicht des Artikels / im Standard fix 0 und rechts draußen / wird für Ableitungen mit Touch Kassa mit Waage verwendet / fix 0 wenn vargew_jn = ‚n‘
@F webshop_jn|char(1)||Artikel ist am WebShop verfügbar
@F marke_nr|integer|f|Markennummer
@F webshop_attribute2table_jn|char(1)||Attribute des Artikels in Tabellenform darstellen / Belegung lt. pfu_param „webshop_attribute2table_kz“
@F er_ewpfand_zuab_cd|Char(10) + n|f|Zuschlagscode für Einwegpfandartikeln in ER / Im Standard NULL und rechts aussen / Ist am Pfandartikel zu hinterlegen
@F eudr_jn|char(1)||Artikel fällt unter die EUDR, es ist eine Sorgfälltigkeitserklärung (DDS) zu führen.
@F kommgewkl_kz|char(1)||Faktor für Kommissionierweg bei MDE Kommissionierung / h = schwere Artikel (Hinweg) (=Default) / r = leiche Artikel (Rückweg)
@N /  /  /
@E
@I index i1_artik (artik_mc)
@I index i2_artik (ao_snr)
@I index i0_artik_upid(artik_upid)
@T artik_altern
@D Alternative Artikel zu Artikel / Im Verwaltungsprogramm muß es ein Event zum Setzen von mach_uni geben.
@F artik_cd|char(20)|p1,f
@F fa_nr|smallint(3)|p2
@F altern_artik_cd|char(20)|p3,f|alternativer Artikel
@F altern_vk_kz|char(1)||Verkauf: / 'e' = ersetzen / '-' = keine Aktion / individuell weitere Kennzeichenwerte möglich, z.B.: / 'a' = aktives anzeigen in Auftragserfassung / in der Auftragsposition werden alle Kennzeichen <> "e", "-" eingelesen
@F altern_ek_kz|char(1)||Einkauf: / 'e' = ersetzen / '-' = keine Aktion / individuell weitere Kennzeichenwerte möglich, z.B.: / 'a' = aktives anzeigen in Bestellerfassung / in der Bestellposition werden alle Kennzeichen <> "e", "-" eingelesen
@F mach_uni|char(20)|g|wenn lt. altern_vk_kz bzw. lt. altern_ek_kz Artikel automatisch ersetzt werden soll, dann ' ' sonst altern_artik_cd
@F altern_webshop_kz|char(1)||Alternativartikel wir an WebShop als … Ausgegeben / n = Nicht an WebShop ausgeben / z = Zubehör (Magento Upsell) / v = Verwante Produkte (Magento Related) / c = Crossell (Megento Kauften auch)
@E
@I unique index i1_artik_altern ( artik_cd, fa_nr, mach_uni )
@T artik_bild
@D Artikelbilder / Die Tabelle wird über den Import Artikelbilder generiert
@F artik_cd|char(20)|p1,f
@F fa_nr|smallint(3)|p2
@F arbildart_kz|char(2)|p3|Artikelbildart / la = Listenansicht / Kann in Ableitungen beliebig erweitert werden
@F image|varbinary(max) +n||Bilddaten
@F bild_import_daz|datetime||Zeitpunkt des Bild Imports
@F bild_endung|varchar(5)||Endung des Importieren Bildes / jpg / png
@F artik_bild_upid|ID|
@F artik_upid|bigint||Artikel
@E
@N i1_artik_bild (artik_bild_upid)
@N i2_artik_bild(artik_upid, bildart_cd)
@T artik_eragrp
@D Zuordnung Artikel -> ERA-Gruppen
@F artik_cd|char(20)|p1,f
@F fa_nr|smallint(3)|p2
@F eragrp_cd|char(10)|p1
@F era_masse|decimal(8,3)||Intrastat Gewicht in kg je veh
@F hpt_jn|char(1)||Gewicht des Hauptartikels / darf nur 1 Zeile mit ‚j’ vorhanden sein / das Gewicht dieser Zeile wird durch is_masse automatisch gesetzt / die anderen Zeilen sind für die Batterien
@E
@T artik_fcol
@D Zuordnung Artikel -> Freies Artikelkennzeichen
@F artik_cd|char(20)|p1,f
@F fa_nr|smallint(3)|p2
@F artik_fcol_cd|char(10)|p3,f|Code der Art des freien Kennzeichens
@F artik_fcol_wert|char(40)||Column- Wert
@E
@T artik_fgr
@D Zuordnung Artikel -> Freie Artikelgruppe
@F artik_cd|char(20)|p1,f
@F fa_nr|smallint(3)|p2
@F fgrart_cd|char(10)|p3|Code der Art der freien Artikelgruppe
@F fgr_cd|char(10)|f|Code der freien Artikelgruppe
@E
@T artik_lag
@D Artikel- Lagerdaten (g) / Datensatz wird nie gelöscht
@F artik_lag_upid|bigint +n|
@N artik_upid
@F artik_cd|char(20)|p1,f
@F fa_nr|smallint(3)|p2
@F lag_cd|char(11)|p3,f
@F sum_auf_off_mg|decimal(12,3)||= - sum ( auf_off_mg * auf_lag_ftr ) from auf_pos where auf_off_mg > 0 + sum (prod_off_mg * -1) from auf_prod where prod_off_mg < 0 / Reservierte Menge für Verfügbarkeit bei der Disposition / Ohne Rahmenaufträge
@F sum_auf_frei_mg|decimal(12,3)||= - sum ( auf_frei_mg * auf_lag_ftr ) from auf_pos where auf_frei_mg > 0 + sum (prod_frei_mg * -1) from auf_prod where prod_frei_mg < 0 / Reservierte Menge für Verfügbarkeit bei der Freigabe
@F sum_umb_off_mg|decimal(12,3)|g|= sum(auf_off_mg * auf_lag_ftr) from auf_pos where auf.aufart_cd = 'i' and artik_lag.lag_cd = kunde_lag_cd / + sum(lief_mg*auf_pos.lag_ftr) from vlfs_pos where auf_pos wie oben and vlfs_pos.geg_kartei_snr = 0
@F frei_verf_mg /|computed||= sum_lag_mg - sum_auf_frei_mg / diese Menge darf nicht < 0 werden / Eine Ausnahme stellt ein Kundenkommissionslager bei auf.aufart_cd = 'vr' dar
@F sum_lag_mg|decimal(12,3)||= sum ( artik_lag_sub.lag_mg )
@F duek_b|decimal(15,6) +n|g|DuEk bewertet pro Lagereinheit in GW / wird nur bei duestrech_jn = 'j' geführt / siehe auch [artik.duest]
@F duest_b|decimal(15,6) +n||DuEst bewertet pro Lagereinheit in GW / wird nur bei Eingangsrechnung ermittelt / wird bei duestrech_jn = 'n' durch manuelle Eingabe von duest bestimmt / siehe auch [artik.duest]
@F duest_abgew_b|decimal(15,6) +n||DuEst pro Lagereinheit abgewertet / wird sonst 1:1 wie duest_b behandelt / kann durch Abwertungsprogramm vermindert werden / siehe auch [artik.duest]
@F duest|decimal(15,6) +n||DuEst pro Lagereinheit in GW / darf im Verwaltungsprogramm nur mit Berechtigung verändert werden. / Eingabe, wenn [duestrech_jn = "n"] und (kein Eigenlager oder die Eigenlager unterschiedliche DuEst-Gruppen besitzen) - alle [artik_lag]-Sätze der Eigenlager mit gleicher DuEst-Gruppe werden mitgeändert / haben alle Eigenlager die selbe DuEst-Gruppe, gelten auch Kommissionslager (für die DuEst-Berechnung und Belegung) als Eigenlager / wird durch DuEst-Rechnung bestimmt / Wenn der Duest NULL ist, muß er bei der Auftragsposition eingegeben werden, siehe auch artik.duestrech_jn
@F ltz_iv_nr|integer(7)|f|letzte abgeschlossene Inventur / ist der iv- Dummy- Satz, wenn noch keine Inventur abgeschlossen ist
@F offen_iv_nr|integer(7)|f|offene Inventur / ist der iv- Dummy- Satz, wenn keine Inventur offen ist
@F ltz_kartei_snr|integer||Karteisatznummer der letzten Lagerbewegung / Inventurdifferenzbuchungen werden hier nicht abgestellt
@F inp_n_lag_ort|char(20)||= artik_lag_ort.lag_ort where zeile_nr = 1 wenn gilt: / lag.lag_ort_inp_jn = 'n' / = ' ' wenn gilt: / lag.lag_ort_inp_jn = 'j'
@E
@I index i1_artik_lag (lag_cd, artik_cd, fa_nr)
@I index i0_artik_lag (artik_lag_upid)
@I index i01_artik_lag (artik_upid)
@T artik_lag_ort
@D Artikel- Lagerdaten- Lagerorte / Lagerort siehe lag.lag_ort_inp_jn , lag.lag_ort_edit_jn, fa.komm_pro_lfs_kz /  / Beim Speichern wird automatisch auch artik_lag.inp_n_lag_ort gesetzt.
@F artik_cd|char(20)|p1
@F fa_nr|smallint(3)|p2
@F lag_cd|char(11)|p3,f|artik_lag
@F lag_ort|char(20)|p4|Lagerort = Lagerplatz
@F zeile_nr|smallint||Sortierungsreihenfolge im DW / Ist nach dem Speichern immer von 1 - n / Die Row mit zeile_nr = 1 hat den Hauptlagerort für artik_lag.inp_n_lag_ort
@E
@T artik_lag_g_st
@D Lagerdaten Gerät zum Stichtag (g) / Kann jederzeit für ein bestimmtes Datum aufgebaut werden. (Für die Entscheidung ob zum Stichtag lagernd zählt der Karteisatz mit der größten internen Nummer für den gilt: kartei_dat <= Stichtagsdatum). Die Duest- Felder werden mit dem jeweils aktuellen DUEST des Geräts befüllt. Achtung: Wenn eine Inventur offen ist, sind die Inventurdifferenzen noch nicht vorhanden für eine Lagerbewertung einer Stichtagsinventur darf der Aufbau erst nach Abschluß der Inventur erfolgen!.
@F artik_cd|char(20)|p1
@F fa_nr|smallint(3)|p2
@F lag_cd|char(11)|p3
@F geraet_cd|char(40)|p4|= artik_lag_sub.geraet_cd
@F st_dat|date|p5|Stichtagsdatum
@F sum_lag_mg|decimal(12,3)||= artik_lag.sum_lag_mg - Bewegungen
@F ekpr|decimal(12,3)||Einkaufspreis pro Lagereinheit in GW
@F estpr|decimal(12,3)||Einstandspreis pro Lagereinheit in GW
@F estpr_abw|decimal(12,3)||Einstandspreis pro Lagereinheit abgewertet in GW
@F geraet_abw_proz|decimal(5,2)||Abwertungsprozentsatz / wird mit 0 initialisiert / wird durch individuelles Abwertungsprogramm gesetzt
@E
@T artik_lag_st
@D Artikel- Lagerdaten zum Stichtag (g) / Kann jederzeit für ein bestimmtes Datum aufgebaut werden. (aktueller Lagerstand - Karteibewegungen mit kartei_dat > st_dat) Die Duest- Felder werden mit dem jeweils aktuellen DUEST befüllt. Achtung: Wenn eine Inventur offen ist, sind die Inventurdifferenzen noch nicht vorhanden für eine Lagerbewertung einer Stichtagsinventur darf der Aufbau erst nach Abschluß der Inventur erfolgen ! /  / Wertlauf setzt aktuelle Preise / Standlauf setzt Stände des Stichtages für vorhandene Sätze bzw. auch Preise bei neuen Sätzen / Gesamtlauf führt Wert- und Standlauf durch /  / wird am Tagesende der Stichtagslagerstand für den aktuellen Tag ermittelt, kann dieser ungleich dem Lagerstand sein wenn es Lagerbewegungen für den nächsten Tag gibt / Der Stichtagslagerstand per Inventurdatum muß nicht unbedingt gleich der Inventurzählmenge sein: / die Inventurabgrenzung erfolgt nach dem Inventurdatum / alle Bewegungen vom Inventurdatum bis zum Abgrenzungsdatum sind in den Zählmengen enthalten im Stichtagslagerstand allerdings natürlich nicht. / es erfolgt nach dem Inventurabschluß eine Lagerbuchung mit Lagerbuchungsdatum <= Inventurdatum
@F artik_cd|char(20)|p1
@F fa_nr|smallint(3)|p2
@F lag_cd|char(11)|p3
@F st_dat|date|p4|Stichtagsdatum
@F sum_lag_mg|decimal(12,3)||= artik_lag.sum_lag_mg - Bewegungen
@F duek_b|decimal(15,6) +n||DuEk pro Lagereinheit in GW lt. [artik_lag]
@F duest|decimal(15,6) +n||DuEst pro Lagereinheit in GW lt. [artik_lag]
@F duest_b|decimal(15,6) +n||DuEst pro Lagereinheit in GW lt. [artik_lag]
@F duest_abgew_b|decimal(15,6) +n||DuEst pro Lagereinheit abgewertet in GW lt. [artik_lag]
@F abw_proz|decimal(5,2)||Abwertungsprozentsatz / wird mit 0 initialisiert / wird durch individuelles Abwertungsprogramm gesetzt
@E
@T artik_lag_sub
@D Artikel- Lagerdaten / wird gelöscht (Tagesabschluß), wenn alle Mengen 0 sind. / Es gibt einen Applobjtyp „lag_ort“, welcher keine echte Tabelle hat. Weiters geht lookup immer gut, obwohl keine Daten vorhanden sind. / nach Änderung einer Row mit artik.lagfuehr_kz = ‚g‘ und charge_geraet <> ‚‘ ist insert/update für die entsprechende row der Tabelle geraet auszuführen
@F artik_lag_sub_upid|bigint + n|
@F artik_cd|char(20)|p1,f
@F fa_nr|smallint(3)|p2
@F lag_cd|char(11)|p3,f
@F lag_ort|char(20)|p4|Lagerort / siehe: / lag.lag_ort_inp_jn / vlfs.lag_ort
@F charge_geraet /|char(40)|p5|bei artik.lagfuehr_kz = 'c' und lag_mg >= 0 die Chargennummer / bei artik.lagfuehr_kz = 'g' und lag_mg >= 0 die Gerätenummer / sonst leer / Anmerkung: Ausschließlich auf Kundenkommissionslagern kann es negative Lagermengen geben: dann ist bei Chargen/Geräten charge_geraet leer
@F lag_mg /|decimal(12,3)|g|Lagerstand / diese Menge darf nicht < 0 werden, wenn fa.darf_lag_minus_jn = "n" / eine Ausnahme stellt ein Kundenkommissionslager bei einer Vorausfaktura dar. (auf.aufart_cd = 'vr) / ist, wenn artik.lagfuehr_kz = 'g', 0 oder 1 bzw. beim Kundenkommissionslager ggf. <0 / ist eigentlich redundant: / = iv_zeile.soll_lag_mg + sum(kartei.bew_mg) / where key= and kartei_snr > iv.iv_kartei_snr
@F sum_aufs_frei_mg|decimal(12,3)|g|= - sum ( aufs_frei_mg * auf_lag_ftr ) from auf_pos_sub where aufs_frei_mg > 0 + sum (prods_frei_mg * -1) from auf_prod_sub where prods_frei_mg < 0 / Reservierte Menge für Verfügbarkeit bei der Freigabe / ACHTUNG: sum ( artik_lag_sub.sum_aufs_frei_mg ) muß nicht = artik_lag.sum_auf_frei_mg sein / diese Menge darf nicht < 0 werden
@F ablauf_dat|date +n||Ablaufdatum bei artikel.lagfuehr_kz = 'c' und artikel.ablaufdat_jn = 'j', / sonst NULL
@F einlag_dat|date +n|g|wird bei INSERT der Zeile, bzw. bei UPDATE über Warenzugang belegt
@F mach_uni /|char(72)|g|bei artikel.lagfuehr_kz = 'g' und charge_geraet nicht leer: / "b", geraet_cd / sonst: "a", lag_cd, lag_ort, charge_geraet
@F geraet_cd|char(40)|g|charge_geraet bei artikel.lagfuehr_kz = 'g', sonst blank / Feld ist notwendig, um in der Lagerstandsabfrage ins Gerät abzubiegen.
@E
@I unique index i1_artik_lag_sub ( artik_cd, fa_nr, mach_uni )
@I index i2_artik_lag_sub (lag_cd, fa_nr, artik_cd)
@T artik_lagd
@D Artikel- Lagerdaten DuEst / ist View über [artik] und [lag]
@F artik_cd|char(20)|
@F fa_nr|smallint(3)|
@F lag_cd|char(11)|
@N folgende Felder werden über StoredProcedure ermittelt / Ermittlung ist hierarchisch, wenn auf einer Ebene ein DuEst ermittelt wurde, wird die Findung beendet / [duest] ist Beispiel für alle anderen Felder (columnname wird an Procedure übergeben) / artik_lag vorhanden / artik_lag.duest / wenn lag.lag_kz = "e" / Min(artik_lag.duest) where fa_nr = ? and duestgrp_cd = ? / wenn artik.duest nicht Null / artik.duest
@F duek_b|decimal(15,6) +n|
@F duest_b|decimal(15,6) +n|
@F duest_abgew_b|decimal(15,6) +n|
@F duest|decimal(15,6) +n|
@E
@T artik_lief
@D Artikel- Lieferanten
@F artik_cd|char(20)|p1,f
@F fa_nr|smallint(3)|p2
@F lief_cd|char(10)|p3,f
@F eeh_cd|char(5)|f|Einkaufseinheit
@F keh_eeh_mg|decimal(9,3)||Anzahl kleinste Einheit = Einkaufseinheit (10 stk = 1 kart)
@F ekpr_keh_eeh_kz|char(1)||Einkaufspreismengeneinheit: / k = Einkaufspreis in kleinster Einheit, e = in Einkaufseinheit
@F ekpr_pro_mg|decimal(4,0)||Einkaufspreis bezieht sich auf diese Anzahl Einheiten lt. ekpr_keh_eeh_kz
@F ekpr_ftr|decimal(13,7)|g|Faktor, sodaß gilt: / Menge * Preis * Faktor = Positionsbetrag / ekpr_keh_eeh_kz = k: / ekpr_ftr = keh_eeh_mg / ekpr_pro_mg / ekpr_keh_eeh_kz = e: / ekpr_ftr = 1 / ekpr_pro_mg
@F los_mg|decimal(9,3)||Losgröße Bestellung in eeh / Bestellmenge in eeh muss ein Vielfaches von los_mg sein / Berechnung der Bestellmenge bei Bestellvorschlag: Bedarf / Losmenge aufgerundet auf Ganze * Losmenge
@F los_eh_cd|char(5)|f|Losgröße
@F wbzeit_best_tg|decimal(3,0)||Wiederbeschaffungszeit in Tagen für Bestellposition
@F wbzeit_bevor_tg|decimal(3,0)||Wiederbeschaffungszeit in Tagen für Errechnung Mindestbestand
@F min_lag_mg|decimal(12,3)||Mindestbestand in Verkaufseinheit
@F bestvor_kz|char(3)||Kennzeichen für Selektion der Lieferanten beim Bestellvorschlag
@F aufw_prz1|decimal(4,2)||1. Aufwertungsprozentsatz für Einstandspreis
@F aufw_prz2|decimal(4,2)||2. Aufwertungsprozentsatz für Einstandspreis
@F aufw_bet1|decimal(11,2)||1. Aufwertungsbetrag für Einstandspreis / in GW / in der ekpr_ftr entsprechenden Einheit / versteht sich in Einkaufseinheit, wenn Preis in Einkaufseinheit / versteht sich in kleinster Einheit, wenn Preis in kleinster Einheit / erhöht für die Bewertung den Einkaufspreis (nach den %) / wird nach den Prozentmäßigen Aufwertungen angewandt
@F aufw_bet2|decimal(11,2)||2. Aufwertungsbetrag für Einstandspreis
@F min_best_mg|decimal(12,3)||Mindestbestellmenge in Einkaufseinheit
@F lief_artikid_cd|char(40)||Lieferantenartikelnummer
@F ekpr_artik_cd|char(20)|f|Artikelnummer Preisfindung / wird artik_lief_ekpr geändert, werden automatisch alle Artikel mitgewartet für die gilt: artik_cd in (select artik_cd from artik_lief where ekpr_artik_cd = ?)
@E
@I index i1_artik_lief (lief_cd, fa_nr, artik_cd)
@T artik_lief_ekpr
@D Artikel - Lieferant: Preise / Rabatte / Im Verwaltungs- DW gibt es 2 Gruppen: / aktion_kz / aktion_kz, ab_dat / Es sind FirstOf, LastOf- Group- Felder zu verwenden.
@F artik_cd|char(20)|p1,f
@F fa_nr|smallint(3)|p2
@F lief_cd|char(10)|p3,f
@F aktion_kz|char(1)|p4|a=Aktion, n=Normalpreis
@F ab_dat|date|p5|Datum gültig ab
@F bis_dat|date||Datum gültig bis: / Bei aktion_kz="n": / Keine Eingabe im Verwaltungsprogramm / wird entweder auf DATMAX oder ab_dat-1 des nächstgrößeren ab_dat's gesetzt. / Bei aktion_kz="a": / Eingabe im Verwaltungsprogramm
@F ab_mg|decimal(12,3)|p6|ab Menge
@F bis_mg|decimal(12,3)||bis Menge
@F waehrung_cd|char(4)|f|Währung
@F ekpr|decimal(12,3) +n||Einkaufspreis in waehrung_cd
@F ekrab1|decimal(4,2)||Rabatt 1
@F ekrab2|decimal(4,2)||Rabatt 2
@F ekrab3|decimal(4,2)||Rabatt 3
@F ekrab4|decimal(4,2)||Rabatt 4
@F ekrab5|decimal(4,2)||Rabatt 5
@F natrab|decimal(12,3)||wird indiv. ausgewertet / dazu ist im Preisfindungsobjekt ein Event vorzusehen!
@E
@T artik_lief_projpr
@D Artikel - Lieferant: Projektpreise / Im Verwaltungs- DW gibt es 2 Gruppen: / aktion_kz / aktion_kz, ab_dat / Es sind FirstOf, LastOf- Group- Felder zu verwenden.
@F artik_cd|char(20)|p1,f
@F fa_nr|smallint(3)|p2
@F lief_cd|char(10)|p3,f
@F ek_projekt|char(20)|p4|Projektnummer
@F ab_dat|date|p5|Datum gültig ab
@F bis_dat|date||Datum gültig bis: / Eingabe im Verwaltungsprogramm
@F ab_mg|decimal(12,3)|p6|ab Menge
@F bis_mg|decimal(12,3)||bis Menge
@F waehrung_cd|char(4)|f|Währung
@F ekpr|decimal(12,3) +n||Einkaufspreis in lief.waehrung_cd
@F ekrab1|decimal(4,2)||Rabatt 1
@F ekrab2|decimal(4,2)||Rabatt 2
@F ekrab3|decimal(4,2)||Rabatt 3
@F ekrab4|decimal(4,2)||Rabatt 4
@F ekrab5|decimal(4,2)||Rabatt 5
@F natrab|decimal(12,3)||wird indiv. ausgewertet / dazu ist im Preisfindungsobjekt ein Event vorzusehen!
@E
@T artik_packst
@D Artikel- Packstoffe
@F artik_cd|char(20)|p1,f
@F fa_nr|smallint(3)|p2
@F packst_cd|char(10)|p3,f|Packstoffcode
@F gewicht|decimal(8,5)||Gewicht des Packstoffes in kg
@E
@S artik_set
@D Artikel- Setbestandteile
@F artik_set_upid|bigint +n|
@F set_artik_upid|bigint +n|
@F set_artik_cd|char(20)|p1,f
@F fa_nr|smallint(3)|p2
@F teil_artik_upid|bigint +n|
@F teil_artik_cd|char(20)|p3,f|Artikel des Bestandteilsartik_kz des Sets = 'p' artik_kz des Teils <> 's' / artik_kz des Sets = 's' artik_kz des Teils kann auch 's' sein, was rekursive Sets ergibt / rekursive Sets werden erst beim Anlegen einer Auftragsposition aufgelöst – siehe auf_pos.set_stufe / für rekursive Sets: siehe artik.set_frei_kz / Teil Artikel darf kein Konfigurationsartikel sein
@F teil_mg|decimal(15,6)||Menge des Bestandteils im Set / Ist bei einem Konfigurationsartikel fix 1
@F teil_duest|decimal(15,6) +n||kalkulatorischer Einstandspreis für Bestandteile deren Artikel keinen duest haben / kommt nur zum Einsatz, wenn / 1.) artik_lag.duest null ist / 2.) artik.duest null ist
@F zeile_nr|smallint||Zeilennummer im DW
@F folge_aufbau_kz|char(1)||Soll Artikel bei Funktion als Folgeartikel aufgebaut werden / i…immer (Default, fix bei artik_kz = "s") / o…nur bei Offert / n…nie / p…Produktion (Setteile werden nur bei der Produktion berücksichtigt) – darf nur bei Artikel mit artik_kz = 'p' verwendet werden / e…Einwegpfand, reagiert wie i im TC, abweichend auf Kassa
@E
@I index i1_artik_set (teil_artik_cd, fa_nr, set_artik_cd)
@I index i0_artik_set_upid (artik_set_upid)
@I index i01_artik_set_upid (set_artik_upid)
@T artik_txt
@D Artikelbezeichnungs- Textzeilen
@F artik_cd|char(20)|p1,f
@F fa_nr|smallint(3)|p2|Firmennummer
@F txt_typ_kz|char(1)|p3|Texttyp / "r" Richtext / wenn [param.appl_txt_kz = "r"] / Standardfont und -größe lt. Parameter / "p" Plaintext / wenn [param.appl_txt_kz <> "r"]
@F zeile_nr|smallint|p4|Zeilennummer
@F sprache_cd|char(5)|f|Sprachencode
@F fett_jn|char(1)||Fettdruck / fix "n", wenn [txt_typ_kz = "r"]
@F unterstrichen_jn|char(1)||unterstrichen drucken / fix "n", wenn [txt_typ_kz = "r"]
@F ab_jn|char(1)||auf der AB drucken
@F kommsch_jn|char(1)||auf Kommissionsschein drucken
@F lfs_jn|char(1)||auf Lieferschein drucken
@F rech_jn|char(1)||auf Rechnung drucken
@F best_jn|char(1)||auf Bestellung bzw. Belastungsnote Lieferant drucken
@F preisliste_jn|char(1)||auf Preisliste drucken
@F off_jn|char(1)||auf Offert drucken
@F wv_jn|char(1)||Text für Wartungsvertragsrechnung in Wartungsvertragsposition übernehmen
@F kassa_jn|char(1)||auf die Kassa übernehmen / nur bei Kassalösung sichtbar/eingebbar / es gibt pro Artikel nur einen Datensatz mit "j"
@F artik_txt|varchar(max)||Artikeltext- Zeile / generierter Plaintext (artik_rtxt), wenn [txt_typ_kz = "r"] / eingegebener Text, sonst
@F artik_txt_dbid|integer identity||ROWID für Retrieve Richtext / durch DB-Default mit serieller Nummer belegt
@F artik_rtxt|varbinary(max)||Artikeltext Richtext / wenn [txt_typ_kz = "p"], durch DB-Default mit Leerstring belegt
@E
@I unique index i1_artik_txt (artik_txt_dbid)
@T artik_webshopattribute
@D Artikel – WebShop Attribute
@F artik_cd|char(20)|p1,f
@F fa_nr|smallint|p2
@F zeile_nr|smallint|p3
@F webshopattribute_snr|bigint|f|Muss pro Artikel eindeutig sein, ausgenommen multiselect attribute die nicht konfigattrib_jn sind.
@F webshopattribute_value|varchar(8000) ci +n||Attributs Inhalt / Wird bei Column Attributen vom jeweiligen Feld vom Artikelstamm befüllt
@F konfigattrib_jn|char(1)||Das Attribut ist als Konfigurationskriterium zu verwenden / Kann nur bei einem Konfigurationsartikel auf j gesetzt werden / Kann nur bei einem Atribute mit webshopattribute_typ_fkz = select auf j gesetzt werden / Bei Zuordnung werden Column Attribute automatisch bei allen Sub-Artikeln angelegt wenn sie noch nicht vorhanden sein sollten. / Das passiert beim Zuordnen des Konfig-Attributs zum Konfig Artikel für alle Sub-Artikeln und beim Zuordnen des Set-Subartikels zum Konfig Artikel für alle Konfig-Attribute.
@F webshoptag_snr|bigint +n||WebshopTag bei WebshopTag Attributen
@F tableattrib_jn|char(1)||Fix 'j‘ wenn Konfigurationskriterium / Eingabe nur bei Konfigurationsartikel möglich – sonst "n"
@E
@I index i1_artik_webshopattribute (webshpattribute_snr, fa_nr, artik_cd)
@T artik_webshopicon
@F v|Artikel – WebShop Icons|
@F artik_cd|char(20)|p1,f
@F fa_nr|smallint|p2
@F webshopicon_cd|char(5)|p3,f
@E
@I index i1_artik_webshopicon (webshopicon_cd, artik_cd, fa_nr)
@T artik_webshopobj
@F v|Artikel – WebShop Objekt|
@F artik_cd|char(20)|p1,f
@F fa_nr|smallint|p2
@F webshopobj_cd|char(5)|p3,f
@F webshopobj_link|varchar(500) +n||Link – Bei Link Objekt
@F bild_endung|varchar(5)||Endung bei Bild Objekt / jpg / png
@F ltz_aend_datz|datetime||Zeitpunkt der letzten Änderung
@F webshopobj_filename|varchar(255)||Dateiname (ohne Endung)
@E
@I index i1_artik_webshopobj (webshopobj_cd, fa_nr, artik_cd)
@T artik_webshoptag
@F v|Artikel – WebShop Tag|
@F artik_cd|char(20)|p1,f
@F fa_nr|smallint|p2
@F webshoptag_snr|bigint|p3,f
@F sichtbar_jn|char(1)||j = wird als tags ausgegeben / n = wird als hidden_tags ausgegeben
@E
@I index i1_artik_webshoptag (webshoptag_snr, artik_cd, fa_nr)
@T artik_webshoptxt
@D Artikel – WebShop Texte
@F artik_cd|char(20)|p1,f
@F fa_nr|smallint|p2
@F sprache_cd|char(5)|p3,f|Sprachencode
@F webshop_name|varchar(255) (ci)||Webshopname
@F webshop_desc|varchar(max) (ci)||Beschreibungstext
@F webshop_short_desc|varchar(max) (ci)||Short Description
@F webshop_seo_txt|varchar(max) (ci)||SEO Text
@E
@T artikerl
@D ArtikelErlöskontenzuordnungsgruppe
@F artikerl_upid|bigint +n|
@F artikerl_cd|char(10)|p1|ArtikelErlöskontenzuordnungscode
@F artikerl_mc|char(40)|
@F ka_mwst_cd|smallint(1)|f|MwSt Code Kassa / 0 = Keine Übertragung an Kassa / Änderungen des MwSt Codes oder der MwSt Prozentsatzes werden auf der Kassa erst nach einer erstmaligen Datenübernahme gültig
@F artikerl_ust_cd|char(10)|f|Standard-InlandsUstCd aller Artikel in dieser Artikelerlösgruppe
@F webshop_mwst_fkz|varchar(64)||WebShop Steurcodes / Magento: / standard – für 20% / reduced – für 10%
@E
@T artikid
@D Artikelidentifikationscode
@F artikid_upid|bigint +n|
@F artikid_cd|char(40)|p1|eine Artikelidentifikation für einen Artikel
@F fa_nr|smallint(3)|p2
@F artikid_kz|char(1)|p3|Art der Artikelidentifikation
@F artikid_kz|char(1)|p3|a|Artikelcode, kunde_cd = blank & lief_cd = blank
@F artikid_kz|char(1)|p3|m|Matchcode, kunde_cd = blank & lief_cd = blank
@F artikid_kz|char(1)|p3|e|EAN- Code: / kunde_cd = blank & lief_cd = blank: selbstvergeben oder Herkunft unbekannt / kunde_cd = blank & lief_cd > blank: Code des Lieferanten / kunde_cd > blank & lief_cd = blank: Code des Kunden
@F artikid_kz|char(1)|p3|8|EAN-8- Code: / kunde_cd = blank & lief_cd = blank: eigener oder Herkunft unbekannt / kunde_cd = blank & lief_cd > blank: Code des Lieferanten / kunde_cd > blank & lief_cd = blank: Code des Kunden
@F artikid_kz|char(1)|p3|l|Lieferantenartikelnummer, kunde_cd = blank & lief_cd > blank
@F artikid_kz|char(1)|p3|k|Kundenartikelnummer , kunde_cd > blank & lief_cd = blank
@F artikid_kz|char(1)|p3|s|Sonder-EAN für Kassenlösung (Gewichts- oder Preis EAN´s) / 5stellig / EAN Aufbau / 2 Stellen EAN-ID lt. Firmenstamm Kassa / 5 Stellen Artikel-ID (diese) / 5 Stellen Gewicht/Menge/Preis je nach EAN-Art / 1 Stelle Prüfziffer / kunde_cd = blank & lief_cd = blank
@F ?|alle übrigen Kennzeichen (bei Belegung der mach_unis wie 'm') / Diese Kennzeichen befinden sich standardmäßig nicht in pfu_kz|
@F kunde_cd|char(10)||Kundennummer, siehe artikid_kz
@F lief_upid|bigint +n|
@F lief_cd|char(10)||Lieferantennummer, siehe artikid_kz
@F keh_mg|decimal(9,3) +n||Eine mit dieser ArtikId beschriftete Verpackung des Artikels beinhaltet keh_mg kleinste Einheiten des Artikels. / In einem Erfassungsprogramm wird, wenn der Artikel durch die aktuelle ID ausgewählt wird, diese Menge umgerechnet in Einheit des Programmes (Verkaufseinheit bzw. Einkaufseinheit) vorgeschlagen.
@F artik_upid|bigint +n|
@F artik_cd|char(20)|f|Artikelcode
@N redundante Felder:
@F mach_uni|char(20)|p4,g|Um Pkey eindeutig zu machen, folgende Belegung:
@F mach_uni|char(20)|p4,g|l|lief_cd
@F mach_uni|char(20)|p4,g|e|blank
@F mach_uni|char(20)|p4,g|8|blank
@F mach_uni|char(20)|p4,g|k|kunde_cd
@F mach_uni|char(20)|p4,g|m|artik_cd
@F mach_uni|char(20)|p4,g|a|blank
@F mach_uni|char(20)|p4,g|s|blank
@F mach_uni_i1|char(21)|g|Um Index i1_ eindeutig zu machen, folgende Belegung:
@F mach_uni_i1|char(21)|g|l|lief_cd
@F mach_uni_i1|char(21)|g|e|Belegung im TC-Standard: / artikid_cd /  / Möchte man je Menge nur eine EAN zulassen, kann man wie folgt customizen: / "l"+lief_cd+null2blank(string(keh_mg)), wenn lief_cd <> "" / "k"+kunde_cd+null2blank(string(keh_mg)), wenn kunde_cd <> "" / " "+null2blank(string(keh_mg)), wenn lief_cd & kunde_cd = ""
@F mach_uni_i1|char(21)|g|8|siehe "e"
@F mach_uni_i1|char(21)|g|k|kunde_cd
@F mach_uni_i1|char(21)|g|m|blank
@F mach_uni_i1|char(21)|g|a|blank
@F mach_uni_i1|char(21)|g|s|blank
@E
@I unique index i1_artikid ( artik_cd, fa_nr, artikid_kz, mach_uni_i1 )
@I index i2_artikid (search_artikid_cd, fa_nr, artikid_kz )
@I index i0_artikid (artikid_upid)
@I index i01_artikid (artik_upid)
@T artikimpfehl
@D Artikelimportfehler
@F job_snr|decimal(14)|p1
@F filename|vchar(255)|p2
@F zeile_nr|integer|p3|wenn Fehler beim Setzen einer Spalte, die konkrete Zeile lt. Excel / wenn Fehler beim Speichern, die letzte Zeile lt. Excel
@F fa_nr|smallint||FaNr
@F artik_cd|char(20)||ArtikCd
@F l_cd|char(11)||LagCd oder LiefCd
@F fehler_txt|vchar(1024)||Fehlertext
@E
@T artikkst
@D ArtikelKorezuordnungsgruppen
@F artikkst_cd|char(10)|p1|ArtikelKorezuordnungscode
@F artikkst_mc|char(40)|
@F kst_nr|integer(9)||Kostenstellennummer Eingangsrechnung bei Sachkonto ist Aufwandskonto
@F koart_nr|integer(9)||Kostenartnummer Eingangsrechnung bei Sachkonto ist Aufwandskonto
@F ktr_nr|integer(9)||Kostenträgernummer Eingangsrechnung bei Sachkonto ist Aufwandskonto
@E
@T artikkomber
@D Artikelkommissionsbereich / es gibt einen Dummy-Satz, der im Verwaltungsprogramm nicht sichtbar ist
@F artikkomber_upid|bigint +n|
@F artikkomber_cd|char(10)|p1
@F artikkomber_mc|char(40)|
@E
@T artikprovgr
@D Artikelprovisionsgruppen / siehe Tabelle provision
@F artikprovgr_cd|char(10)|p1
@F artikprovgr_mc|char(40)|
@E
@T artiksach
@D ArtikelSachkontenzuordnungsgruppe Bestand + Wareneinsatz / die Erlöskontengruppierung erfolgt über artikerl
@F artiksach_cd|char(10)|p1
@F artiksach_mc|char(40)|
@E
@T artikvkkondgr
@D Artikelverkaufskonditionsgruppe
@F artikvkkondgr_upid|bigint +n|
@F artikvkkondgr_cd|char(10)|p1
@F artikvkkondgr_mc|char(40)||Bezeichnung
@E
@T auf
@D Kunden- Auftrag
@F auf_nr|integer(7)|p1|Auftragsnummer / Vergabe/Kontrolle mittels Tabelle nummern unter Berücksichtigung von aufart.nr_kreis
@F fa_nr|smallint(3)|p2|Firmennummer
@F fil_nr|smallint(3)|f|Filiale
@F auf_dat|date|ng|Auftragsdatum = Erfassungsdatum
@F aufart_cd|char(2)|f,n|Auftragsart:
@F aufart_cd|char(2)|f,n|n|Normalauftrag
@F aufart_cd|char(2)|f,n|g|Gutschrift / solo_jn = 'j'
@F aufart_cd|char(2)|f,n|gv|Vernichtungsgutschrift / keine Lagerbuchung / auf_pos.auf_lag_ftr = 0 / kein Kommissionsscheindruck / solo_jn = 'j'
@F aufart_cd|char(2)|f,n|gw|Wertgutschrift / keine Lagerbuchung / auf_pos.auf_lag_ftr = 0 / kein Kommissionsscheindruck / keine Statistikmengenbuchung / auf_pos.stat_mg_ftr = 0 / kein Wareneinsatz / solo_jn = 'j'
@F aufart_cd|char(2)|f,n|gk|Kundenretoure / entspricht grundsätzlich der Gutschrift "g" / Lager der Auftragsposition ist ein "WareUnterwegsLager" und durch [aufart_fa.lag_cd] fix bestimmt / Ziellager wird durch Default belegt (wie sonst das Abgangslager) und ist einzugeben / Gegenlager ist durch Abgangslager fix bestimmt / Rechnungskennzeichen [vkrech_kz] not in ("lr", "r", "n") / Lieferschein beliefert "WareUnterwegsLager", bucht jedoch nicht auf Gegenlager / durch "WareUnterwegsZubuchen" wird auf Ziellager umgebucht
@F aufart_cd|char(2)|f,n|gl|Lieferantenretoure / wird nie fakturiert Rechnungskennzeichen [vkrech_kz] fix "n" / Auftragsart kann nicht ausgewählt werden, sondern wird durch Eingabe der Lieferantennummer bestimmt / Kundendaten werden durch Dummykunden für Lieferantenretouren bestimmt / Lieferant bestimmt nur Lieferadresse / Debitor darf (sollte) 0 sein / keine Preisfindung, Preis u. Rabatte fix 0 / keine Verbrauchsbuchung / keine Änderung der Kundennummer im Änderungszweig
@F aufart_cd|char(2)|f,n|a|Abrufauftrag / keine Lagerbuchung / auf_pos.auf_lag_ftr = 0 / keine Statistikmengenbuchung / auf_pos.stat_mg_ftr = 0 / kein Wareneinsatz / solo_jn = 'j' / Freigegebene Menge immer 0 / wird nie ausgeliefert / Gelieferte Menge der Positionen erhöht sich durch Abruf (andere Auftragsposition) / Freigabe, Kommissionsscheindruck, Lieferbelegaufbau nicht möglich
@F aufart_cd|char(2)|f,n|k|Belieferung eines Kommissionslagers / solo_jn = 'j' / Lagerzugang auf dem Kommissionslager des Kunden beim Lieferbelegaufbau / kein Rechnungsaufbau / vkrech_kz = 'n' / keine Änderung der Kundennummer im Änderungszweig
@F aufart_cd|char(2)|f,n|kr|Retoure aus einem Kommissionslager / solo_jn = 'j' / Lagerzugang auf einem normalen Lager / Lagerabgang auf dem Kommissionslager des Kunden beim Lieferbelegaufbau / kein Rechnungsaufbau / vkrech_kz = 'n' / negative Verbrauchsbuchung / auf_pos.verb_mg_ftr = -1 / keine Änderung der Kundennummer im Änderungszweig
@F aufart_cd|char(2)|f,n|ka|Abrechnung einer Kommission / solo_jn = 'j' / Lagerabgang auf dem Kommissionslager des Kunden beim Lieferbelegaufbau / kein Kommissionscheindruck / keine Verbrauchsbuchung / auf_pos.verb_mg_ftr = 0 / keine Änderung der Kundennummer im Änderungszweig
@F aufart_cd|char(2)|f,n|vr|Vorausrechnung (= Faktura deren Lieferung später erfolgt) / Baut negativen Lagerstand im Kundenkommissionslager auf, dieser wird durch die Auftragsart 'vw' wieder ausgeglichen / solo_jn = 'j' / vkrech_kz = 'r' / kein Kommissionscheindruck / kann auch Positionen mit negativen Mengen enthalten Gutschrift / keine Verbrauchsbuchung / auf_pos.verb_mg_ftr = 0 / keine Änderung der Kundennummer im Änderungszweig
@F aufart_cd|char(2)|f,n|vw|Warenlieferung zu Vorausfaktura / Löst den negativen Lagerstand am Kundenkommissionslager wieder auf / solo_jn = 'j' / Lagerzugang auf dem Kommissionslager des Kunden beim Lieferbelegaufbau / kein Rechnungsaufbau / vkrech_kz = 'n' / kann auch Positionen mit negativen Mengen enthalten Retoure / keine Änderung der Kundennummer im Änderungszweig
@F aufart_cd|char(2)|f,n|i|Belieferung eines normalen Lagers (=Lagerumbuchung über die Auftragsabwicklung) / solo_jn = 'j' / Lagerzugang auf dem Gegenlager beim Lieferbelegaufbau / kein Rechnungsaufbau / vkrech_kz = 'n' / keine negativen Mengen erlaubt / auf_pos.stat_mg_ftr = 0 / Verkaufspreis = 0 / keine Verbrauchsbuchung / auf_pos.verb_mg_ftr = 0 / keine Änderung der Kundennummer im Änderungszweig
@F aufart_cd|char(2)|f,n|ir|Belieferung eines normalen Lagers (=Lagerumbuchung über die Auftragsabwicklung) - Retoure / solo_jn = 'j' / Lagerzugang auf dem Gegenlager (=normales Lager) beim Lieferbelegaufbau / Lagerabgang auf dem Lager des internen Kunden beim Lieferbelegaufbau / keine negativen Mengen erlaubt / kein Rechnungsaufbau / vkrech_kz = 'n' / auf_pos.stat_mg_ftr = 0 / Verkaufspreis = 0 / Gegenlager entspricht / keine Verbrauchsbuchung / auf_pos.verb_mg_ftr = 0 / keine Änderung der Kundennummer im Änderungszweig
@F aufart_cd|char(2)|f,n|h|Handlieferschein / solo_jn = 'j' / Lieferscheinnummer u. Datum werden eingegeben / kein Kommissionsscheindruck / Prüfung des Lieferscheinnummernkreises mit nummern_kz = 'p'
@F aufart_cd|char(2)|f,n|o|Offert / solo_jn = 'j' / keine Freigabe, keine Lagerbewegung, und –reservierung / auf_pos.auf_lag_ftr = 0 / nur Offertdruck, keine weiteren Belege / kd_best_dat beinhaltet Anfragedatum / kd_best_txt beinhaltet Anfragenummer / lief_dat beinhaltet Evidenz- oder gültig-Bis-Datum / debitor_nr darf 0 sein Interessent
@F aufart_cd|char(2)|f,n|b|Barverkauf / solo_jn = 'j' / vkrech_kz = 'r' / Zahlungskonditionen werden nicht gedruckt / sktonto1_prz wird auf Rechnung als Skonto nach dem Bruttoendbetrag als Abzug ausgewiesen
@F aufart_cd|char(2)|f,n|p|Produktionsauftrag / solo_jn = 'j' / kunde.kunde_lagverw_kz = 'p' / Datensatz mit Produktionsartikel muß in auf_prod vorhanden sein / Beim Speichern des Produktionsauftrages werden die Teile lt. artik_set in der Tabelle auf_pos gespeichert / kein Rechnungsaufbau / vkrech_kz = 'n' / rueck_dru_jn = 'n' / kd_rueck_aufb_jn = 'j' / auf_pos.stat_mg_ftr = 0 / Verkaufspreis = 0 / keine Änderung der Kundennummer im Änderungszweig
@F aufart_cd|char(2)|f,n|s|Serviceauftrag / kann über die "normale" Auftragsabwicklung nicht bearbeitet werden / solo_jn = 'j' / Rückstandsaufbau immer ja / keine Änderung der Kundennummer im Änderungszweig
@F aufart_cd|char(2)|f,n|sh|Kombination der Auftragsarten 's' und 'h' / es darf nur ein Arbeitsbericht aufgebaut werden / keine Änderung der Kundennummer im Änderungszweig
@F aufart_cd|char(2)|f,n|sg|Serviceauftrag Gutschrift / kann über die "normale" Auftragsabwicklung nicht bearbeitet werden / solo_jn = 'j' / keine Änderung der Kundennummer im Änderungszweig
@F aufart_cd|char(2)|f,n|si|Seviceauftrag intern / kann über die "normale" Auftragsabwicklung nicht bearbeitet werden / solo_jn = 'j' / Verkaufspreis = 0 / über aufart.fibu_ueb_kz keine Überleitung / über aufart.vrech_nr_kreis eigener Nummernkreis für intere Rechnung / keine Änderung der Kundennummer im Änderungszweig
@F aufart_cd|char(2)|f,n|so|Serviceoffert (=Kostenvoranschlag) / solo_jn = 'j' / keine Freigabe, keine Lagerbewegung, und –reservierung / auf_pos.auf_lag_ftr = 0 / nur Kostenvoranschlagdruck, keine weiteren Belege / kd_best_dat beinhaltet Anfragedatum / kd_best_txt beinhaltet Anfragenummer / lief_dat beinhaltet Evidenz- oder gültig-Bis-Datum / s_auf_zustand_kz = "e" / abericht_kz = " " / debitor_nr darf 0 sein Interessent / keine Änderung der Kundennummer im Änderungszweig
@F aufart_cd|char(2)|f,n|su|Serviceauftrag ungeprüft (=Reparaturannahme) / solo_jn = 'j' / nur Arbeitsberichtsdruck, keine weiteren Belege / s_auf_zustand_kz = "e" / abericht_kz = " " / keine Positionsanlage möglich / Auftragsart kann auf alle Serviceauftragsarten, auch auf "Serviceoffert" geändert werden / keine Änderung der Kundennummer im Änderungszweig
@F aufart_cd|char(2)|f,n|st|Streckenauftrag: / folgende Abweichungen zu Normalauftrag: / Die Auftragsart [aufart_fa] hat ein Lager eingetragen / Dieses Lager ist ein Lager des Lieferanten (siehe Lager) / Das Lager in der Auftragsposition ist fix dieses Lager / Der Lieferscheinaufbau verwendet immer "DuEst" der Auftragsposition / keine Verbrauchsbuchung / auf_pos.verb_mg_ftr = 0 / Der Lauf zur Berechnung der Mindestbestände berücksichtigt keine Lieferscheine aus "Strecke" / Zu jeder Streckenauftragsposition muß eine dieser Position zugeordnete Bestellposition angelegt werden.
@F aufart_cd|char(2)|f,n|w|Wartungsvertragsabrechnungsauftrag / solo_jn = 'j' / keine Lagerbuchung / auf_pos.auf_lag_ftr = 0 / kein Kommissionsscheindruck / Anzahl vlfs immer 0 / es dürfen nur Artikel mit artik_kz = "w" verwendet werden / keine Änderung der Kundennummer im Änderungszweig
@F aufart_cd|char(2)|f,n|wg|Gutschrift zu Wartungsvertragsabrechnungsauftrag / wie "w" / keine Änderung der Kundennummer im Änderungszweig
@F aufart_cd|char(2)|f,n|vf|pauschale Vorausfaktura (=Faktura deren Lieferung später erfolgt) / keine Lagerbuchung (die Artikel die der Kunde tatsächlich erhalten wird, stehen im Unterschied zu "vr" noch nicht fest) / kein Kommissionscheindruck / solo_jn = 'j' / vkrech_kz = 'r' / Auftragspositionen sind immer komplett freigegeben / Saldo am Kundenstamm wird erhöht / keine Statistikbuchung bei Rechnungsaufbau / keine Änderung der Kundennummer im Änderungszweig
@F aufart_cd|char(2)|f,n|vl|Warenlieferung zu pauschaler Vorausfaktura / solo_jn = 'j' / vkrech_kz = 'n' / Saldo am Kundenstamm wird vermindert / wird vorgeschlagen, wenn der Saldo am Kundenstamm > 0 ist, und die aktuelle Auftragsart keine Serviceauftragsart ist / Statistikbuchung bei Lieferscheinaufbau / keine Änderung der Kundennummer im Änderungszweig
@F kunde_cd|char(10)|f|Kundennummer / Ist kunde_cd = fa.fa_kunde_cd kann nur eine Auftragsart gewählt werden für die gilt: / Preis = 0 / keine Überleitung in Fibu / Im Grundpaket gilt dies nur für die Auftragsart 'si', diese wird dann automatisch vorgeschlagen / darf bei bestimmten Auftragsarten (siehe dort) geändert werden, wenn / keine Auftragsposition ist zur Abwicklung einem anderen Auftrag zugeordnet / keine Auftragsposition ist zur Abwicklung dem aktuellen Auftrag zugeordnet / keine Auftragsposition ist bereits fakturiert / Auftragsart darf sich nicht ändern / ist Änderung möglich, werden beim Speichern / die redundanten Felder in auf_pos, vlfs und vlfs_pos mitgeändert / der offene Auftrags-, Lieferschein- und freigegebene Auftragswert umgebucht / bei Geräten in Lieferscheinen des Auftrages der Standortkunde, der Aufenthaltsort sowie die Verkaufsdaten geändert
@F gl_lief_cd|char(10)|f|Lieferantennummer / ist normalerweise " " / ist bei Auftragsart "gl" der Lieferant, an den die Ware retourniert wird / bestimmt nur Lieferadresse / restliche Kundendaten werden durch Dummy-Kunde für Lieferantenretouren bestimmt / befindet sich im Standardpaket im rechten Windowbereich und kann zum Customizen herangezogen werden
@F solo_jn|char(1)||'j' = Positionen des Auftrags dürfen in keinen anderen Auftrag übernommen werden und es dürfen auch keine Positionen eines anderen Auftrags in diesen übernommen werden / Muß 'j' sein wenn: / kunde.divers_jn = 'j' / valuta_dat is not null' / Hinweis für den Anwender: Soll 'j' sein, wenn: / Zahlungskonditionen übersteuert wurden / Auftrag wird anders als normal versendet / ...
@F vkrech_kz|char(2)||Art der Fakturierung
@F vkrech_kz|char(2)||d|Sammelrechnung pro Debitorennummer
@F vkrech_kz|char(2)||k|Sammelrechnung pro Kundennummer
@F vkrech_kz|char(2)||ka|Sammelrechnung pro Kundenauftragsnummer + Datum
@F vkrech_kz|char(2)||a|Sammelrechnung je Auftrag
@F vkrech_kz|char(2)||l|Einzelrechnung pro Lieferschein
@F vkrech_kz|char(2)||lr|Lieferschein + Rechnung sofort
@F vkrech_kz|char(2)||r|Rechnung = Lieferbeleg
@F vkrech_kz|char(2)||n|nur Lieferschein, keine Rechnung
@F vkrech_kz|char(2)||bei aufart_cd="w" nur jene erlaubt, welche bei wv erlaubt sind
@F vkrech_sel_fkz|char(3)||Selektionskennzeichen zum Zusammenstellen von Lieferscheinen zu einer Sammelrechnung / Es sollte aber pfu_kz angelegt werden.
@F musteroffert_jn|char(1)||kann nur bei Auftragsart = "o", "j" sein, ist sonst fix "n" / wird Offert auf "j" geändert, werden alle Positionen auf "offen" gesetzt, die Verbindung zu bereits zugeordneten Aufträgen wird aufgehoben / wird ein Musteroffert übernommen, erfolgt keine Verknüpfung mit dem Auftrag, es werden keine Liefermengen eingetragen / Musterofferte werden im Rückstandsregister nur angezeigt, wenn die Offertübernahme über Extramenü ausgewählt wurde
@F debitor_nr|integer(9)|f,ng|wird bei der Anlage = kunde.debitor_nr
@F debitor_name1|char(50)|ng|Debitorendaten für Belege (derzeit AB, LFS): / Wird bei debitor.divers_jn = / 'j' jeweils von der Lieferadresse kopiert, bzw. ustid = ' ' / 'n' jeweils vom Debitoren kopiert. / Das Kopieren erfolgt bei: / Neuanlage / Lieferscheinaufbau / Adresse wird bei debitor.divers_jn = 'j' in die Buchhaltung übergeleitet.
@F debitor_name2|char(50)|ng|Debitorendaten für Belege (derzeit AB, LFS): / Wird bei debitor.divers_jn = / 'j' jeweils von der Lieferadresse kopiert, bzw. ustid = ' ' / 'n' jeweils vom Debitoren kopiert. / Das Kopieren erfolgt bei: / Neuanlage / Lieferscheinaufbau / Adresse wird bei debitor.divers_jn = 'j' in die Buchhaltung übergeleitet.
@F debitor_name3|char(50)|ng|Debitorendaten für Belege (derzeit AB, LFS): / Wird bei debitor.divers_jn = / 'j' jeweils von der Lieferadresse kopiert, bzw. ustid = ' ' / 'n' jeweils vom Debitoren kopiert. / Das Kopieren erfolgt bei: / Neuanlage / Lieferscheinaufbau / Adresse wird bei debitor.divers_jn = 'j' in die Buchhaltung übergeleitet.
@F debitor_name4|char(50)|ng|Debitorendaten für Belege (derzeit AB, LFS): / Wird bei debitor.divers_jn = / 'j' jeweils von der Lieferadresse kopiert, bzw. ustid = ' ' / 'n' jeweils vom Debitoren kopiert. / Das Kopieren erfolgt bei: / Neuanlage / Lieferscheinaufbau / Adresse wird bei debitor.divers_jn = 'j' in die Buchhaltung übergeleitet.
@F debitor_strasse|char(50)|ng|Debitorendaten für Belege (derzeit AB, LFS): / Wird bei debitor.divers_jn = / 'j' jeweils von der Lieferadresse kopiert, bzw. ustid = ' ' / 'n' jeweils vom Debitoren kopiert. / Das Kopieren erfolgt bei: / Neuanlage / Lieferscheinaufbau / Adresse wird bei debitor.divers_jn = 'j' in die Buchhaltung übergeleitet.
@F debitor_land_cd|char(3)|f,ng|Debitorendaten für Belege (derzeit AB, LFS): / Wird bei debitor.divers_jn = / 'j' jeweils von der Lieferadresse kopiert, bzw. ustid = ' ' / 'n' jeweils vom Debitoren kopiert. / Das Kopieren erfolgt bei: / Neuanlage / Lieferscheinaufbau / Adresse wird bei debitor.divers_jn = 'j' in die Buchhaltung übergeleitet.
@F debitor_plz|char(10)|ng|Debitorendaten für Belege (derzeit AB, LFS): / Wird bei debitor.divers_jn = / 'j' jeweils von der Lieferadresse kopiert, bzw. ustid = ' ' / 'n' jeweils vom Debitoren kopiert. / Das Kopieren erfolgt bei: / Neuanlage / Lieferscheinaufbau / Adresse wird bei debitor.divers_jn = 'j' in die Buchhaltung übergeleitet.
@F debitor_ort|char(50)|ng|Debitorendaten für Belege (derzeit AB, LFS): / Wird bei debitor.divers_jn = / 'j' jeweils von der Lieferadresse kopiert, bzw. ustid = ' ' / 'n' jeweils vom Debitoren kopiert. / Das Kopieren erfolgt bei: / Neuanlage / Lieferscheinaufbau / Adresse wird bei debitor.divers_jn = 'j' in die Buchhaltung übergeleitet.
@F ustid|char(14)|ng|Debitorendaten für Belege (derzeit AB, LFS): / Wird bei debitor.divers_jn = / 'j' jeweils von der Lieferadresse kopiert, bzw. ustid = ' ' / 'n' jeweils vom Debitoren kopiert. / Das Kopieren erfolgt bei: / Neuanlage / Lieferscheinaufbau / Adresse wird bei debitor.divers_jn = 'j' in die Buchhaltung übergeleitet.
@F kunde_name1|char(50)||Lieferanschrift für Lieferbeleg /
@F kunde_name2|char(50)||Lieferanschrift für Lieferbeleg /
@F kunde_name3|char(50)||Lieferanschrift für Lieferbeleg /
@F kunde_name4|char(50)||Lieferanschrift für Lieferbeleg /
@F kunde_strasse|char(50)||Lieferanschrift für Lieferbeleg /
@F kunde_land_cd|char(3)|f|Lieferanschrift für Lieferbeleg /
@F kunde_plz|char(10)||Lieferanschrift für Lieferbeleg /
@F kunde_ort|char(50)||Lieferanschrift für Lieferbeleg /
@F vklfs_preis_jn|char(1)||beim Lieferschein sollen Preise gedruckt werden / bei aufart_cd in ('i', 'p') 'n'
@F zahlart_cd|char(5)|f|Zahlungsart
@F op_debitor_nr|integer(9)|f,ng|wird bei der Anlage = kunde.debitor_nr / Debitor für Bonitätsprüfung (Saldo, AufWert etc.) und Fibuschnittstelle bei Überleitung / wird wenn debitor_nr von 0 auf gültigen Wert gesetzt wird, mitgeändert
@F teillief_jn|char(1)||Auftrag darf Teillieferungen enthalten / Vorschlag von Kundenstamm / Ist keine Teillieferung erlaubt, wird geprüft, dass bei Lieferschein und Kommissionsschein für alle Positionen Freigabemenge gleich offener Menge sein muss.
@F rueck_dru_jn|char(1)||Rückstände auf Lieferbeleg drucken ja/nein
@F kd_rueck_aufb_jn|char(1)||Rückstände aufbauen ja/nein
@F versart_cd|char(5)|f|Versandart
@F liefbed_cd|char(5)|f|Lieferbedingung
@F anz_vkrech|smallint(2)||Anzahl Rechnungen
@F anz_vklfs|smallint(2)||Anzahl Lieferscheine / muß > 0 sein, wenn vkrech_kz <> 'r' und auf_art_kz <> "w*" / ist sonst 0
@F waehrung_cd|char(4)|f,ng|Währung für Rechnung / (Belegung bei der Neuanlage lt. Debitor)
@F preisli_cd|char(5)|f,ng|Preislistencode / Bei Service, wenn vorhanden aus s_kunde
@F vkrab|decimal(4,2)||Auftragsrabatt: / wird als 6. Positionsrabatt gerechnet und somit im Positionsbetrag ausgewiesen / wird auf der Rechnung vor jedem Eingangsauftrag ausgewiesen / ist bei aufart_cd = 'a' fix 0 / darf nicht mehr verändert werden wenn: / auf (ein) auf_pos vlfs_pos vlfs
@F vkrabk2|decimal(4,2)||Auftragsrabatt (momentan noch inaktiv): / wird als 7. Positionsrabatt gerechnet und somit im Positionsbetrag ausgewiesen / wird auf der Rechnung vor jedem Eingangsauftrag ausgewiesen / ist bei aufart_cd = 'a' fix 0 / darf nicht mehr verändert werden wenn: / auf (ein) auf_pos vlfs_pos vlfs
@F vkrabk3|decimal(4,2)||Auftragsrabatt: (momentan noch inaktiv) / wird als 8. Positionsrabatt gerechnet und somit im Positionsbetrag ausgewiesen / wird auf der Rechnung vor jedem Eingangsauftrag ausgewiesen / ist bei aufart_cd = 'a' fix 0 / darf nicht mehr verändert werden wenn: / auf (ein) auf_pos vlfs_pos vlfs
@N Zahlungskonditionen:
@F skonto1_prz|decimal(4,2)||1. Skontoprozentsatz
@F skonto1_tg|smallint(3)||dazu Ziel- Tage
@F skonto2_prz|decimal(4,2)||2. Skontoprozentsatz
@F skonto2_tg|smallint(3)||dazu Ziel- Tage
@F netto_tg|smallint(3)||Ziel- Tage für Netto- Zahlung
@F valuta_dat|date +n||Valutadatum für Einzelrechnung / ist bei vkrech_kz in ( 'd', 'k' ) null / ist bei aufart_cd = "w*" null
@F zollta_dru_jn|char(1)||Zolltarifnummer auf Rechnungsbelegen drucken / Vorschlag lt. Kundenstamm
@F off_endsumme_jn|char(1)||Offert mit Endsumme drucken / Vorschlag lt. Kundenstamm
@F kd_best_dat|date||Kundenbestelldatum
@F kd_best_txt|char(40)||Kundenbestellnummer
@F kunde_sb_pers_cd|char(5)||Sachbearbeiter des Kunden, welcher bestellt hat bzw. die AB oder das Offert erhalten soll
@F auf_fa_pers_cd|char(5)|ng|Sachbearbeiter der eigenen Firma, welcher Auftrag erfaßt hat
@F aufeinart_cd|char(10)|f|Auftragseingangsart
@F lief_dat|date||gewünschtes Lieferdatum >= auf_dat / wird auf den Montag von lief_kw gesetzt, wenn lief_kw eingegeben wird / ist nur Vorschlag für neu anzulegende Positionen / wird bei Neuanlage eines Offerts aus Tagesdatum + [fa.offert_gueltig_tg] vorgeschlagen / bestimmt bei aufart_cd='p' auch bei Änderung Lieferdatum der Position
@F lief_kw|char(7)||gewünschte Lieferwoche / ist immer die Woche in der lief_dat liegt / ist nur Vorschlag für neu anzulegende Positionen / bestimmt bei aufart_cd='p' auch bei Änderung Lieferdatum der Position
@F lief_txt|char(60)||Text zum Lieferdatum / siehe auch lief_dat
@F freigeben_jn|char(1)||"j" = Bei der Neuanlage einer Auftragsposition wird die bestellte Menge unter Berücksichtigung der Verfügbarkeit für die freigegebene Menge vorgeschlagen. / Vorschlag durch aufart.freigeben_jn / wird gegebenenfalls automatisch mit "n" belegt, wenn nichts freizugeben ist / wird gegebenenfalls automatisch mit "j" belegt, wenn alles freizugeben ist / muss bei Aufträgen deren Lieferzeit in der Zukunft liegt, auf 'n' umgesetzt werden (durch customizen eventuell automatisch)
@F zuteil_prior|char(10)||Zuteilungspriorität beim automatischen Freigeben, " " ist die höchste Priorität.
@N die folgenden Felder mit Präfix ab_ / verstehen sich bei auf_art: / 'o' Offert / 's' Kostenvoranschlag / '*' Auftragsbestätigung
@F ab_druck_dat|date +n|g|AB zu diesem Datum gedruckt, wird bei jedem AB- Druck gesetzt
@F ab_druck_kz|char(2)||Kommunikationskennzeichen für die AB / 'fs' sofort faxen / 'fz' zeitversetzt faxen / 'e' email / 'd' druck /  / 1. Stelle wird für Kommunikationsart Druckzuordnung verwendet
@F ab_zhd|char(50)||zu Handen für AB
@F ab_komidart_cd|char(10)||Code der Art der Kommunikations- Identifikation von komidart_cd / nur belegt, wenn ab_druck_kz in ( "e", "f*" )
@F ab_komid_wert|varchar(255)||Faxnummer bzw. Emailadresse des Empfängers / nur belegt, wenn ab_druck_kz in ( "e", "f*" )
@F komm_abl_dat|date +n|n|Kommissionsablaufdatum / Ist bei aufart_cd = 'k' gefüllt
@F kundeprovgr_cd|char(10)|f|Provisionsgruppe Kunde / Vorschlag lt. kunde / siehe Tabelle provision
@F kundeerl_cd|char(10)|f|Kundenerlöszuordnung / Vorschlag lt. Kunde / Wenn der Kunde eine WebShop Kundengruppe mit Kundenerlösgruppe lt. Lieferadresse eingetragen hat, so wird abhängig von der Versandart das Land der Lieferadresse oder der Filialadresse zur Bestimmung der Kundenerlösgruppe lt. WebShopKundengruppe-Land verwendet.
@F kundekst_cd|char(10)|f|Kostenstellenzuordnung Kunde / Vorschlag lt. Kunde
@F hand_vlfs_nr|integer(7)|n|Lieferscheinnummer für den nächsten vlfs- Aufbau / muß bei aufart_cd in ('h','sh') gefüllt sein / prüfen durch Tabelle nummern / kann bei übrigen aufart_cd like 's%' gefüllt sein / wird beim Blankoarbeitsbericht- Druck vor dem eigentlichen Druck lt. Tabelle Nummern vergeben, wenn null / ist sonst 0
@F hand_vlfs_dat|date +n|n|Lieferscheindatum für den nächsten vlfs- Aufbau / muß bei aufart_cd in ('h','sh') gefüllt sein / kann bei übrigen aufart_cd like 's%' gefüllt sein / ist sonst null
@F l_komm_nr|smallint(2)|g|letzte Kommissionscheinnummer innerhalb des Auftrags / Default Neuanlage = 0 / wird beim Kommissionscheindruck erhöht
@F autofrei_jn|char(1)|g|Auftrag wurde durch Rückstandsauflösung automatisch freigegeben / Default Neuanlage = "n" / wird durch Lieferschein oder Tagesende auf "n" gesetzt
@F auf_zustand_kz|char(1)|g|e|erfaßt / (Auftrag wird gerade neu erfaßt und es ist noch nicht entschieden, was weiter mit ihm passiert)
@F auf_zustand_kz|char(1)|g|k|Kommissionsschein gedruckt / wird vom Kommissionsscheindruck gesetzt
@F auf_zustand_kz|char(1)|g|r|Rückstand / (Auftrag soll bis zum Eintritt eines Ereignisses warten) / Der Tagesabschluß setzt alle 'e' auf 'r' / Der Lieferscheinaufbau setzt auf 'r', wenn der Abwicklungsauftrag nicht komplett ausgeliefert ist
@F auf_zustand_kz|char(1)|g|l|Es wird gerade ein Lieferschein aufgebaut / wird im Zuge der Einleitungs- Transaktion des vlfs- Aufbaus gesetzt. / wird im Zuge der Abschluß- Transaktion des vlfs- Aufbaus auf 'r' oder 'g' umgesetzt / Auftragspositionen mit auf_frei_mg = 0 dürfen nicht verändert werden (Das sind jene, für welche bereits eine vlfs_pos aufgebaut wurde, bzw. jene, welche sowieso nicht geliefert werden sollen.)
@F auf_zustand_kz|char(1)|g|g|vollständig geliefert / Der Tagesabschluß setzt auf 'g', wenn für alle Abwicklungs- Positionen gilt: auf_off_mg = 0 / so tut es auch der Lieferscheinaufbau
@F auf_zustand_kz|char(1)|g|b|Setposition im Batchaufbau / wird beim Speichern der Sethauptposition gesetzt, wenn Setteilpositionen im Batch verarbeitet werden / wird wieder auf den alten Wert zurückgesetzt, wenn die Batchverarbeitung erfolgreich beendet wurde / alter Wert wird in ori_auf_zustand_kz gesichert
@F ori_auf_zustand_kz|char(1)|g|Originalauftragszustand / wird nur bei auf_zustand_kz = 'b' belegt / sonst leer
@F erl_auf_nr|integer|r|0, wenn Auftrag noch offene Mengen hat, sonst = auf_nr siehe dazu auf_zustand_kz = 'g'
@F ein_hat_rech_jn|char(1)|r|Es gibt eine verrechnete Lieferscheinposition zu einer Auftragsposition, deren Eingangsauftrag der aktuelle Auftrag ist.
@F ein_hat_vlfs_jn|char(1)|r|Es gibt eine Lieferscheinposition zu einer Auftragsposition
@F iu_jn|char(1)|n,r|lt. Tabelle kunde
@F mach_uni_vlfs|integer|n,r|bei aufart_cd in ('h','sh') hand_vlfs_nr / sonst auf_nr * -1
@F wv_nr|integer(7)||Wartungsvertragsnummer / bei auf_art_cd = "w*" die Nummer des betroffenen Wartungsvertrags / sonst = 0
@F wv_abrech_dat|date +n||Wartungsvertrag- Abrechnungsdatum / wird nur vom automatischen Wartungsvertragsabrechnungslauf gesetzt und ist dann der Monatserste des ersten Monats der abgerechneten Periode / ist sonst null
@F postanschr_ab_kz|char(1)||r…Rechnungsadresse wird oben gedruckt / l….Lieferadresse wird oben gedruck / bei der oberen Adresse wird die zu-handen-Zeile gedruckt
@F storno_kz|char(2)||ist normalerweise blank / wird durch Bezugsbelegeinlesen auf folgende Werte gesetzt / "so" Storno ohne Fibubezug / "sm" Storno mit Fibubezug / "k" Kopie
@F bez_vrech_nr|integer(7)|f|OP-Nummer des Bezugsbeleges / ist normalerweise 0 / ist bei storno_kz = "sm" die Rechnungsnummer des Bezugsbeleges
@F debadr_manu_jn|char(1)||wenn "j", wird die Rechnungsadresse wird bei diversen Kunden beim speichern nicht aus der Lieferadresse belegt, die Rechnungsadresse kann manuell geändert werden
@F auf_kassa_kz|char(2)||Kennzeichen Kassa / blank keine Übertragung von/nach Kassensystem / "lk" Auftrag wurde durch "Lieferschein auf Kassa" im Zuge des Verbuchens der Kassa im TC angelegt (keine Änderungsmöglichkeit der Positionen) / "ia" In Aufbau – Kassenbeleg wurde noch nicht komplett aufgebaut
@F ao_snr|integer||AO-Snr / ist eindeutig / dient zum Finden eines AOs
@F vrechausart_cd|char(10)|f|Ausgangsrechnung Ausgabeart / Belegung lt. Debitor / kann übersteuert werden
@F auf_barcode|char(13)||Barcode für Dokumentenarchiv / wird beim AB-/Offertdruck vergeben, wenn [archiv. beleg_kz = "ab"] vorhanden ist / ist sonst fix ""
@F apollo_uuid|varchar(50) +n||Unique User Identifyer / eindeutige Nummer der App-Installation
@F apollo_aa_id|integer +n||eindeutige Apollo-Auftrags-ID / ist nur in Verbindung mit [apollo_uuid] eindeutig, da in der App vergeben
@F aufn_datz|date|ng|Erfassungsdatum des Datensatzes [dd.mm.yyyy hh:mm:ss] / durch DB-Default (CURRENT) belegt / Erstbelegung: [auf_dat] 00:00:00
@F e_vrech_komid_wert|varchar(255) +n||E-Mail-Adresse für elektronischen Versand Ausgangsrechnung
@F e_vrech_fix_jn|char(1)||E-Mail Adresse für den elektronischen Versand ist Fix (wurde manuell erfasst oder über WebShop SST belegt. / Bei "n" wird weiterhin debitor.e_rech_komid_wert für den Versand verwendet.
@F zahlungsref|varchar(100) +n||Zahlungsreferenznummer
@F magento_entity_id|integer +n||Magento ID der Bestellung
@F kunde_telefon|varchar(255)||Lieferung Telefonnummer / Wird mit VK markierter Telefonnummer (Telefon oder Mobil) der dem Kunden zugeordneten Personen vorgeschlagen
@F auf_upid|bigint +n|
@F kunde_upid|bigint +n|
@F debitor_upid|bigint +n|
@F op_debitor_upid|bigint +n|
@F zahlart_fix_jn|char(1)||Zahlungsart wurde manuell geändert (oder durch SST gesetzt) und darf durch Vorschlagslogiken nicht mehr geändert werden.
@E
@I index i0_auf_upid (auf_upid)
@I index i1_auf (erl_auf_nr, kunde_cd, fa_nr)
@I unique index i2_auf (mach_uni_vlfs, fa_nr)
@I index i3_auf (hand_vlfs_nr, fa_nr)
@I index i4_auf (op_debitor_nr, fa_nr, erl_auf_nr)
@I index i5_auf (ao_snr)
@I index i6_auf (apollo_uuid, apollo_aa_id)
@T auf_komm
@D Kunden- Auftrag- Kommissionsschein / nur offene Kommissionsscheine
@F auf_nr|integer(7)|p1,f
@F fa_nr|smallint(3)|p2
@F komm_nr|smallint(2)|p3
@F komm_dat|date||Kommissionsscheindatum
@F vklfs_sel_jn|char(1)||"j" der Lieferscheinaufbau soll diesen Kommissionsschein berücksichtigen.
@F komber_cd|char(10)|f
@F komm_barcode|char(13)||Barcode für Dokumentenarchiv / wird beim Kommissionscheindruck vergeben, wenn [archiv. beleg_kz = "ko"] vorhanden ist / ist sonst fix ""
@E
@I index i1_auf_komm (komber_cd, fa_nr, auf_nr)
@T auf_pos
@D Kunden- Auftrag- Position / siehe unbedingt auch auf, artik, artik_lag
@F ein_auf_nr|integer(7)|p1,f|Auftragsnummer des Erzeugungsauftrages: siehe ab_auf_nr
@F fa_nr|smallint(3)|p2|Firmennummer
@F auf_pos_nr|smallint(4)|p3|kann wahlweise in Schritten vergeben bzw. übersteuert werden
@F auf_pos_kz|char(1)|ng|'s' = Sethauptposition / 't' = Setteil / 'n' = Normalposition / 'e' = Einwegpfandposition (wie Setteil aber nur für Menge) / siehe auch set_- Columns und unbedingt set_stufe
@F ab_auf_nr|integer(7)|f,g|Auftragsnummer des Abwicklungsauftrages. / Abwicklung bedeutet: / Rückstandsauflösung / Kommissionierung / Auslieferung / Fakturierung / ist bei der Neuanlage = ein_auf_nr / Eine Auftragsposition kann unter folgenden Bedingungen einem anderen Auftrag zur weiteren Abwicklung zugeordnet werden: / folgende Felder sind ident: / fa_nr / kunde_nr / preisli_cd / währung_cd / aufart_cd = 'n' / nur wenn lief_dat der zu übernehmenden Position <= auf.lief_dat des aufnehmenden Abwicklungsauftrags / nur wenn für beide Aufträge gilt: solo_jn ='n' / der empfangende Auftrag muß auf_zustand_kz = 'e' und der abgebende Auftrag muß auf_zustand_kz = 'r' bzw. ( auf_zustand_kz = 'k' mit auf_frei_mg = 0) haben / siehe unbedingt fa.ab_auf_kz / Aktionen: / auf_pos.ab_auf_nr wird zu auf_nr des aufnehmenden Abwicklungsauftrags
@F komm_nr|smallint(2)||Kommissionscheinnummer innerhalb des Abwicklungsauftrags / Defaultwert Neuanlage 0 / wird beim Kommissionscheindruck lt. Auftragskopf gesetzt / wird Freigabemenge 0 eingetragen, wird auf 0 zurückgestellt / gibt es nach dem "auf 0 zurückstellen" keine weitere Auftragsposition mit dieser komm_nr, wird der entsprechende Datensatz aus der Tabelle "auf_komm" gelöscht
@F komm_pos_nr|smallint(4)|g|Positionsnummer am Kommisionsschein / wird beim Kommissionsscheindruck vergeben / wird beim Lieferschein auf 0 gesetzt, wird beim 0-setzen der Freigabemenge auf 0 gesetzt
@F abruf_ein_auf_nr|integer(7)|n|Auftragsposition des Abrufauftrags od. Offertes, von dem die aktuelle Position abgerufen wurde. Ist die Position selbst, falls nicht von Abrufauftragsposition abgebucht wurde (wenn in Neuanlage nicht ausgefüllt).
@F abruf_auf_pos_nr|smallint(4)|f,n|Auftragsposition des Abrufauftrags od. Offertes, von dem die aktuelle Position abgerufen wurde. Ist die Position selbst, falls nicht von Abrufauftragsposition abgebucht wurde (wenn in Neuanlage nicht ausgefüllt).
@F set_stufe|smallint||Set- Stufe: / bei nicht- Set- Positionen = 0 / es werden auch rekursive Sets unterstützt (d.h., dass ein Setbestandteil wiederum ein Set sein kann) – set_stufe gibt die Rekursionstiefe an: / beim äußersten Set = 0 / bei allen Bestandteilen des äußersten Sets = 1 / bei allen Bestandteilen eines Sets, das selbst Setstufe 1 hat, = 2 / u.s.w. / also: für einen Setbestandteil = auf_pos(Set).set_stufe+1 / es gilt: set_stufe > 0 auf_pos_kz = 't' / siehe "auf_pos – Set"
@F set0_pos_nr|smallint(4)|f,ng|auf_pos_kz = 't' Positionsnummer des zugehörigen Sethauptartikels mit set_stufe = 0 / auf_pos_kz <> 't' auf_pos_nr / ist also bei Setteilen der äußerste Sethauptartikel
@F set_pos_nr|smallint(4)|f,ng|auf_pos_kz = 't' Positionsnummer des zugehörigen Sethauptartikels mit set_stufe = set_stufe-1 / auf_pos_kz <> 't' auf_pos_nr / ist also bei Setteilen der nächstäußere Sethauptartikel
@F set_teil_mg|decimal(15,6) +n|ng|auf_pos_kz = 't' Menge in einem Set ( = artik_set.teil_mg) / auf_pos_kz = 'n' & aufart_cd = 'p': / Menge für einen Produktionsartikel / sonst: / NULL
@F set_frei_kz|char(1)|ng|aus artik befüllen, Verwendung der Felder: siehe artik!!! / Felder werden nur mehr aus Abwärtskompatibilitätsgründen gesetzt und werden vom Programm nicht mehr verwendet / die Auswertung der Felder außerhalb des Programms sollte allerdings bei neuen Auswertungen/Programmteilen nicht mehr erfolgen / die Felder sind nur bei einstufigen Sets richtig belegt
@F set_preis_dru_kz|char(1)|ng|aus artik befüllen, Verwendung der Felder: siehe artik!!! / Felder werden nur mehr aus Abwärtskompatibilitätsgründen gesetzt und werden vom Programm nicht mehr verwendet / die Auswertung der Felder außerhalb des Programms sollte allerdings bei neuen Auswertungen/Programmteilen nicht mehr erfolgen / die Felder sind nur bei einstufigen Sets richtig belegt
@F set_stat_kz|char(1)|ng|aus artik befüllen, Verwendung der Felder: siehe artik!!! / Felder werden nur mehr aus Abwärtskompatibilitätsgründen gesetzt und werden vom Programm nicht mehr verwendet / die Auswertung der Felder außerhalb des Programms sollte allerdings bei neuen Auswertungen/Programmteilen nicht mehr erfolgen / die Felder sind nur bei einstufigen Sets richtig belegt
@F set_fibu_kz|char(1)|ng|aus artik befüllen, Verwendung der Felder: siehe artik!!! / Felder werden nur mehr aus Abwärtskompatibilitätsgründen gesetzt und werden vom Programm nicht mehr verwendet / die Auswertung der Felder außerhalb des Programms sollte allerdings bei neuen Auswertungen/Programmteilen nicht mehr erfolgen / die Felder sind nur bei einstufigen Sets richtig belegt
@F set_teil_dru_kz|char(1)|ng|aus artik befüllen, Verwendung der Felder: siehe artik!!! / Felder werden nur mehr aus Abwärtskompatibilitätsgründen gesetzt und werden vom Programm nicht mehr verwendet / die Auswertung der Felder außerhalb des Programms sollte allerdings bei neuen Auswertungen/Programmteilen nicht mehr erfolgen / die Felder sind nur bei einstufigen Sets richtig belegt
@F ap_preis_dru_jn|char(1)|ng|wenn auf_pos_kz = 'n' 'j' / Bedeutung der einzelnen Felder siehe artik.set_..._kz / 'j' bedeutet, dass für die aktuelle Position die entsprechende Aktivität durcheführt werden kann/muss / z.B. set_preis_dru_jn = 'j Preise werden gedruckt / die Kennzeichen sind bei der Set- Position und allen zugehörigen Teilpositionen nicht gleich / ap_fibu_kont_jn Kontierung dieser Position wird verwendet / ap_fibu_jn diese Position wird in die Fibu gebucht / ap_fibu_jn ist für auf_pos_kz = 's' nur dann 'j', wenn gilt: ap_preis_dru_jn = 'j' AND ap_fibu_kont_jn = 'j' / ap_fibu_jn ist für auf_pos_kz = 't' nur dann 'j', wenn gilt: ap_preis_dru_jn = 'j' OR ap_fibu_kont_jn = 'j'
@F ap_stat_jn|char(1)|ng|wenn auf_pos_kz = 'n' 'j' / Bedeutung der einzelnen Felder siehe artik.set_..._kz / 'j' bedeutet, dass für die aktuelle Position die entsprechende Aktivität durcheführt werden kann/muss / z.B. set_preis_dru_jn = 'j Preise werden gedruckt / die Kennzeichen sind bei der Set- Position und allen zugehörigen Teilpositionen nicht gleich / ap_fibu_kont_jn Kontierung dieser Position wird verwendet / ap_fibu_jn diese Position wird in die Fibu gebucht / ap_fibu_jn ist für auf_pos_kz = 's' nur dann 'j', wenn gilt: ap_preis_dru_jn = 'j' AND ap_fibu_kont_jn = 'j' / ap_fibu_jn ist für auf_pos_kz = 't' nur dann 'j', wenn gilt: ap_preis_dru_jn = 'j' OR ap_fibu_kont_jn = 'j'
@F ap_fibu_jn|char(1)|ng|wenn auf_pos_kz = 'n' 'j' / Bedeutung der einzelnen Felder siehe artik.set_..._kz / 'j' bedeutet, dass für die aktuelle Position die entsprechende Aktivität durcheführt werden kann/muss / z.B. set_preis_dru_jn = 'j Preise werden gedruckt / die Kennzeichen sind bei der Set- Position und allen zugehörigen Teilpositionen nicht gleich / ap_fibu_kont_jn Kontierung dieser Position wird verwendet / ap_fibu_jn diese Position wird in die Fibu gebucht / ap_fibu_jn ist für auf_pos_kz = 's' nur dann 'j', wenn gilt: ap_preis_dru_jn = 'j' AND ap_fibu_kont_jn = 'j' / ap_fibu_jn ist für auf_pos_kz = 't' nur dann 'j', wenn gilt: ap_preis_dru_jn = 'j' OR ap_fibu_kont_jn = 'j'
@F ap_dru_jn|char(1)|ng|wenn auf_pos_kz = 'n' 'j' / Bedeutung der einzelnen Felder siehe artik.set_..._kz / 'j' bedeutet, dass für die aktuelle Position die entsprechende Aktivität durcheführt werden kann/muss / z.B. set_preis_dru_jn = 'j Preise werden gedruckt / die Kennzeichen sind bei der Set- Position und allen zugehörigen Teilpositionen nicht gleich / ap_fibu_kont_jn Kontierung dieser Position wird verwendet / ap_fibu_jn diese Position wird in die Fibu gebucht / ap_fibu_jn ist für auf_pos_kz = 's' nur dann 'j', wenn gilt: ap_preis_dru_jn = 'j' AND ap_fibu_kont_jn = 'j' / ap_fibu_jn ist für auf_pos_kz = 't' nur dann 'j', wenn gilt: ap_preis_dru_jn = 'j' OR ap_fibu_kont_jn = 'j'
@F ap_fibu_kont_jn|char(1)|ng|wenn auf_pos_kz = 'n' 'j' / Bedeutung der einzelnen Felder siehe artik.set_..._kz / 'j' bedeutet, dass für die aktuelle Position die entsprechende Aktivität durcheführt werden kann/muss / z.B. set_preis_dru_jn = 'j Preise werden gedruckt / die Kennzeichen sind bei der Set- Position und allen zugehörigen Teilpositionen nicht gleich / ap_fibu_kont_jn Kontierung dieser Position wird verwendet / ap_fibu_jn diese Position wird in die Fibu gebucht / ap_fibu_jn ist für auf_pos_kz = 's' nur dann 'j', wenn gilt: ap_preis_dru_jn = 'j' AND ap_fibu_kont_jn = 'j' / ap_fibu_jn ist für auf_pos_kz = 't' nur dann 'j', wenn gilt: ap_preis_dru_jn = 'j' OR ap_fibu_kont_jn = 'j'
@F setpr_netto_jn|char(1)||gibt an, ob bei Sethauptartikel der Preis die Summe der Nettopreis der Teile ist / bei artik_kz <> 's' fix 'n'
@F veh_cd|char(5)|f|Verkaufseinheit / Vorschlag von Artikelstamm / zu übersteuern bei diversen Artikeln
@F vkpr_keh_veh_kz|char(1)|ng
@F vkpr_pro_mg|decimal(4,0)|n|zu übersteuern bei diversen Artikeln
@F keh_veh_mg|decimal(9,3)||zu übersteuern bei diversen Artikeln
@F vkpr_ftr|decimal(13,7)|ng|wird bei Änderung von [vkpr_pro_mg], [vkpr_keh_veh_kz] oder [keh_veh_mg] neu bestimmt
@F artik_cd|char(20)|f,n|Artikelnummer, siehe auch artik_altern
@F artik_mc|char(40)||Artikelmatchcode / wird bei artik_kz = 'd' für Abfragen überschrieben
@F gar_mo_vk|smallint(3)||Garantiemonate Verkauf
@F duest|decimal(15,6)||Belegungsregeln nach Priorität (wenn eine Regel zur Anwendung kommt sind die nachfolgenden Regeln hinfällig): / wird ggf. fix belegt – siehe ap_duest_fix_jn / wird bei auftragsbezogener Bestellung über auf_pos_best bestimmt und durch Warenzugang und Eingangsrechnung aktualisiert / ist ggf. lt. Serviceverrechnungsart fix 0 / wenn Statistik bei Geräten auf Ebene "Geräteidentpreis" geführt wird und ap_duest_fix_jn = "n" und sum(geraet.estpr) is not null / sum(geraet.estpr) / auf_frei_mg / [artik_lag.duest] wenn nicht NULL / [artik.duest] wenn nicht NULL / wird lt. artik_set.teil_duest belegt, wenn dieser nicht null ist und es sich um einen Setteil handelt / ansonsten muss er eingegeben werden / siehe ap_duest_fix_jnkann eingegeben werden, wenn lt. Serviceverrechnungsart vorgesehen oder Abgangslager ein Lieferantenlager ist
@F ap_duest_fix_jn|char(1)||bei Lieferscheinaufbau wird fix der DuEst lt auf_pos.duest verwendet / ist "j", wenn / lt. Serviceverrechnungsart DuEst eingegeben wird oder 0 ist / Lager der Auftragsposition ein Lieferantenlager ist / Position über Bezugsbelegeinlesen aufgebaut wurde und Stornokennzeichen[1] des Auftrages = "s" / Position über Bezugsbelegeinlesen aufgebaut wurde und "Einstandspreis verwenden" angehakt wurde / Lagerfaktor der Auftragsposition 0 ist / auftragsbezogener Bestellung (zug_best_nr > 0) ??? soll das wirklich so sein ???
@F lief_dat|date||gewünschtes Lieferdatum >= auf_dat / wird auf den Montag von lief_kw gesetzt, wenn lief_kw eingegeben wird / keine Eingabe bei Offert/Serviceoffert
@F lief_kw|char(7)||gewünschte Lieferwoche / ist immer die Woche in der lief_dat liegt / keine Eingabe bei Offert/Serviceoffert
@F lief_txt|char(60)||Text zum Lieferdatum
@F lag_cd /|char(11)|f|Lager / freigegebene Menge bezieht sich auf dieses Lager / Beim Lieferbelegaufbau wird von diesem Lager gebucht / bei aufart_cd = 'ka', 'kr', 'vr' kunde.kunde_lag_cd / Achtung bei Änderung: Reservierungen ändern!!! / nicht änderbar, wenn auf_pos.auf_frei_mg <> 0 / bei Auftragsart "gk" fix durch Auftragsart [aufart_fa.lag_cd] bestimmt
@F geg_lag_cd|char(11)|f,n|Gegenlager / Lager, auf welches beim Lieferbelegaufbau umgebucht wird / bei aufart_cd = "gk" fix durch lag_cd bestimmt / wird von ziel_lag_cd bestimmt / entspricht normalerweise ziel_lag_cd / weicht bei aufart_cd = "i%" von ziel_lag_cd ab, wenn über lag_lag.geg_lag_cd ein Umbuchungslager (=WareUnterwegsLager) definiert ist / befindet sich im rechten Bereich des Fensters keine Eingabe
@F ziel_lag_cd|char(11)|f,n|Ziellager (Lager, auf welches umgebucht werden soll) / aufart_cd = 'k', 'vw', 'i' kunde.kunde_lag_cd / aufart_cd = 'kr', 'ir', "gk" Eingabe (Vorschlag Defaultlager) / sonst " "
@F artikkomber_cd|char(10)|f|Artikelkommissionsbereich / lag_kz = "k" " " / lag_kz <> "k" artik.artikkomber_cd
@F komm_lag_ort /|char(20)|n|Lagerort für Auftragsarten mit Kommissionslagerbezug: / bestimmt Lagerort im Kommissionslager (dies ist abhängig von der Auftragsart das Lager bzw. das Gegenlager) / notwendig für Preisbestimmung durch vlfs bei Abrechnung / Eindeutige Bestimmung des Lieferscheins(=Lagerort) in auf_pos_sub / bei aufart_cd <> 'ka', 'kr' " " / muss bei aufart_cd = 'k[ar]' und fa.komm_pro_lfs_kz in ("p", "l") ein Lagerort, der einem Lieferschein bzw. einer Lieferscheinposition entspricht sein .
@F auf_best_mg|decimal(12,3)||bestellte Menge / aufart_cd like 'k%', in ( 'o', 'a' ) nur positiv / darf bei aufart_cd = 'p' nur abhängig von artik.auf_prod_best_kz verändert werden / darf bei auf_pos_kz = 't' nicht verändert werden
@F auf_off_mg|computed||= (auf_best_mg - auf_lief_mg - auf_loesch_mg) siehe auch artik_lag
@F auf_frei_mg /|decimal(12,3)||freigegebene Menge / aufart_cd = 'ka', 'kr', 'vr', 'h', 'b' ist fix die bestellte Menge (die Bestellte Menge kann dann nicht größer als die verfügbare Menge sein) / ist vorzeichengleich zur bestellten Menge / aufart_cd = 'o', 'a' fix 0 / lag.lag_ort_inp = 'n' und artik.lagfuehr_kz = 'n' –> / Es gibt genau einen auf_pos_sub- Satz, welcher beim Speichern automatisch angelegt werden kann. Siehe dazu auch komm_lag_ort. / siehe auf.auf_zustand_kz / bei auf_pos_kz = 's' werden ggf. bei Änderung auch die frei_mg der Teil Positionen geändert / wird vom Lieferscheinaufbau auf 0 gesetzt / darf bei aufart_cd = 'p' nur abhängig von fa.auf_prod_frei_kz verändert werden / darf bei auf_pos_kz = 't' nicht verändert werden
@F auf_lief_mg|decimal(12,3)|r|gelieferte Menge / bei Abrufauftragspositionen steht hier die abgerufene Menge (= Summe der bestellten Menge aller Auftagspositionen, welche von dieser Position abrufen) / Wird beim Lieferbelegaufbau inkrementiert / Wird beim Speichern einer zugehörigen Abrufposition richtiggesetzt
@F auf_fakt_mg|decimal(12,3)|r|fakturierte Menge / Wird beim Fakturenaufbau inkrementiert
@F auf_loesch_mg|decimal(12,3)|g|gelöschte, nicht gelieferte Menge / Kann eine Auftragsposition nicht vollständig ausgeliefert/abgerufen werden, wird hier die restliche offene Menge eingetragen. / siehe vlfs_pos.off_mg_kz / kann im Auftragspositionswindow über Extras- Menüpunkt gesetzt werden.
@F auf_lag_ftr|smallint(1)|ng|Lagerbewegungsfaktor (0, -1) / ist, wenn nicht anders beschrieben, -1 / Menge * auf_lag_ftr = Menge, die zum Lagerstand lt. auf_pos.lag_cd addiert wird / siehe auch auf.aufart_cd, artik.lagfuehr_kz
@F vk_stat_ftr|smallint(1)||wird bei der Neuanlage der Position vom Artikel genommen / kann zum Customizen verwendet werden
@F stat_mg_ftr|smallint(1)|ng|Mengenfaktor Statistik (0, 1) steht in Realunion mit dem Wareneinsatzfaktor, welcher ein virtueller ist. / ist, wenn nicht anders beschrieben, 1 / Menge * stat_mg_ftr = Menge, die für statistische Auswertungen verwendet wird / duest * stat_mg_ftr = Wareneinsatz, welcher für statistische Auswertungen verwendet wird / siehe auch auf.aufart_cd
@F verb_mg_ftr|smallint(1)|ng|Mengenfaktor Verbrauch (0, 1) / ist bei auf_lag_ftr = 0 ebenfalls 0 / ist bei aufart_cd = "kr" -1 / ist bei Auftragsarten ohne Verbrauch 0 / ist bei aufart_cd <> "kr" 1 / siehe auch auf.aufart_cd
@F vkpr|decimal(12,3)||Verkaufspreis / darf nicht mehr geändert werden, wenn es bereits eine fakturierte Lieferscheinposition gibt / versteht sich in auf.waehrung_cd / auf.iu_jn (also entweder inkl. Ust oder exkl. Ust) / Die Vorschlagswerte bei der Neuanlage werden lt. Preisfindung ermittelt.
@F vkrab1|decimal(4,2)||Rabatt 1, siehe vkpr
@F vkrab2|decimal(4,2)||Rabatt 2, siehe vkpr
@F vkrab3|decimal(4,2)||Rabatt 3, siehe vkpr
@F vkrab4|decimal(4,2)||Rabatt 4, siehe vkpr
@F vkrab5|decimal(4,2)||Rabatt 5, siehe vkpr
@F preis_manu_jn|char(1)||Preis oder Rabatte der Auftragsposition wurden manuell übersteuert
@F vkrabk_ftr|smallint(1)||Auftragskopfrabatt soll bei diesem Artikel zur Anwendung gebracht werden. Siehe dazu artik
@F zug_best_nr|integer|ng|Index der zugeordneten Bestellposition / wenn <> 0, ist die Auftragsposition dieser Bestellposition zugeordnet
@F zug_best_pos_nr|smallint(4)|ng|Index der zugeordneten Bestellposition / wenn <> 0, ist die Auftragsposition dieser Bestellposition zugeordnet
@F zug_prod_auf_nr|integer|ng|Index zum zugeordneten Produktionsauftrag / wenn <> 0, ist die Auftragsposition diesem Prod.Auftrag zugeordnet
@F stat_vkpr|decimal(15,6)|r|statistischer Verkaufspreis exkl. Ust, Rabatt nicht abgezogen, in GW und in Verkaufseinheit = Lagereinheit / (die unten genannten Kurse werden per Tagesdatum bei der Neuberechnung gelesen) / iu_jn = 'n' / vkpr * gw_kurs / fw_kurs * vkpr_ftr / iu_jn = 'j' vkpr * gw_kurs / fw_kurs / (1+ust_prz/100) * vkpr_ftr / wird bei jedem Speichern der Position neu errechnet (Dies ist auch beim Fakturieren der Fall.) /
@F stat_?_betr|computed||Positionsbetrag: ? steht für: / auf_best / auf_off / auf_frei / vlfs_pos.lief / = ?_mg * stat_vkpr -% vkrab1 -% vkrab2 -% auf.vkrab
@F artikprovgr_cd|char(10)|f|Provisionsgruppe Artikel / Vorschlag lt. artik / siehe Tabelle provision
@F ueb_nr|smallint||Zuordnung zu Positionsüberschrift
@F variante_jn|char(1)||Position ist "Variante" / wird bei Offertdruck ausgewertet / ist bei Auftragsarten <> "o" fix "n"
@F erl_ein_auf_nr|integer|r|Erledigungskennzeichen: / wird durch folgende Aktionen gesetzt: / Auftragspositionsbearbeitung / Lieferscheinaufbau / wenn <> 0, darf auf_off_mg nicht mehr verändert werden
@F erl_ein_auf_nr|integer|r|= 0|auf_off_mg <> 0 nicht erledigt
@F erl_ein_auf_nr|integer|r|= ein_auf_nr|auf_off_mg = 0 erledigt
@F hat_rech_jn|char(1)|r|Es gibt verrechnete Lieferscheinposition zu dieser Auftragsposition.
@F hat_vlfs_jn|char(1)|r|Es gibt eine Lieferscheinposition zu dieser Auftragsposition
@F kunde_cd|char(10)|r|Kunde lt. Tabelle auf
@N Service:
@F wv_nr|integer(7)||zugeordnete Wartungsvertragsposition: / Bei einer Serviceauftragsposition die Wartungsvertragsposition, über welche die erbrachte Leistung abgerechnet wird, wenn diese durch einen Wartungsvertag abgedeckt ist. / bei Wartungsvertragsabrechnungsauftrag die Wartungsvertragsposition, welche abgerechnet wird / sonst keine zugeordnete Position / wv_nr = 0, wv_pos_nr = 0
@F wv_pos_nr|smallint(4)||zugeordnete Wartungsvertragsposition: / Bei einer Serviceauftragsposition die Wartungsvertragsposition, über welche die erbrachte Leistung abgerechnet wird, wenn diese durch einen Wartungsvertag abgedeckt ist. / bei Wartungsvertragsabrechnungsauftrag die Wartungsvertragsposition, welche abgerechnet wird / sonst keine zugeordnete Position / wv_nr = 0, wv_pos_nr = 0
@F s_verrechart_cd|char(5)|f|Verrechnungsart Service / Blank bei nicht Service / Wenn Auftragsposition zu einem Serviceauftrag gehört und sich auf Wartungsvertragsposition bezieht wird s_vrechart_cd über folgende Beziehungskette initialisiert: auf_pos wv_pos wl_artik
@F splitt_pos_nr|smallint(4)||Splittpositionsnummer / wird normalerweise wie auf_pos_nr vergeben / wird durch Funktion "Position splitten" mit der splitt_pos_nr der ursprünglichen Position belegt
@F bild_auf_ab_jn|char(1)||Bild soll auf AB gedruckt werden / wird von Artikelstamm vorgeschlagen / befindet sich im rechten Bereich kann durch Customizen abgeändert werden
@F bild_auf_off_jn|char(1)||Bild soll auf Offert gedruckt werden / wird von Artikelstamm vorgeschlagen / befindet sich im rechten Bereich kann durch Customizen abgeändert werden
@F setaufbau_kz|char(1)||Status des Setaufbaus / e...erledigt bzw. kein Set, bzw. sofortiger Setaufbau / n...Neuanlage der Teilpositionen auf auf_pos_set erforderlich / k...Setkorrektur erforderlich / u..Update erforderlich / Änderung der Position nur bei setaufbau_kz = 'e' erlaubt
@F ao_snr|integer||AO-Snr / ist eindeutig / dient zum Finden eines AOs
@F fremd_pos_nr|smallint||Fremdpositionsnummer der Auftragsposition / ist ggf. bei Auftrag durch den Bund zu erfassen und in der Rechnungs-SST anzugeben / wenn unbestimmt, wird beim Speichern 0 angenommen / wenn <> 0, muss es eindeutig sein innerhalb eines Auftrages
@F magento_item_id|integer +n||Positionsnummer / Ist die eindeutige order_item_id von Magento / Ist bei Versandkostenpositionen immer 0 oder 1 / Wird für die Rückmeldung des Versandes benötigt
@F ewpfand_kz|char(1)||Einwegpfandkennzeichen / Notwendig für leichtere Mengensynchro und spätere Abfragen / h… Hauptartikel („Die Flasche Cola“) / p….Pfandposition („Das Flaschenpfand“) / <blank> … Nicht Pfandrelevant.
@F auf_pos_upid|bigint +n|
@F ein_auf_upid|bigint +n|
@F ab_auf_upid|bigint +n|
@F artik_upid|bigint +n|
@E
@I index i0_auf_pos_upid (auf_pos_upid)
@I index i1_auf_pos (ab_auf_nr, fa_nr, ein_auf_nr, auf_pos_nr )
@I index i2_auf_pos (erl_ein_auf_nr, ein_auf_nr )
@I index i3_auf_pos (artik_cd, fa_nr, erl_ein_auf_nr)
@I index i4_auf_pos (kunde_cd, fa_nr, erl_ein_auf_nr)
@I index i5_auf_pos (zug_best_nr, fa_nr, zug_best_pos_nr)
@I index i6_auf_pos (ao_snr)
@I index i7_auf_pos (abruf_ein_auf_nr, fa_nr, abruf_auf_pos_nr)
@T auf_pos_best
@D Kunden- Auftrag- Position Bestelldaten /
@F ein_auf_nr|integer(7)|p1
@F fa_nr|smallint(3)|p2
@F auf_pos_nr|smallint(4)|p3,f
@F lief_cd|char(10)|f|Lieferant
@F alf_verwenden_jn|char(1)||Einkaufsdaten werden bei der Anlage der Bestellposition lt. artik_lief bzw. artik_lief_ekpr verwendet
@F lief_artikid_cd|char(40)||Lieferantenartikelnummer
@F eeh_cd|char(5)|f|Einkaufseinheit / bei Artikel mit artik_kz = "d" einzugeben, default lt. auf_pos, sonst protected
@F keh_eeh_mg|decimal(9,3)|ng
@F ekpr_keh_eeh_kz|char(1)|ng
@F ekpr_pro_mg|decimal(4,0)||Einkaufspreis bezieht sich auf diese Anzahl Einheiten lt. ekpr_keh_eeh_kz
@F ekpr_ftr|decimal(13,7)|ng
@F ekpr|decimal(12,3) +n||Einkaufspreis
@F waehrung_cd|char(4)|f|Währung / lt. artik_lief_ekpr, bzw. lief wenn kein artik_lief_ekpr vorhanden
@F ekrab1|decimal(4,2)||Rabatt 1
@F ekrab2|decimal(4,2)||Rabatt 2
@F ekrab3|decimal(4,2)||Rabatt 3
@F ekrab4|decimal(4,2)||Rabatt 4
@F ekrab5|decimal(4,2)||Rabatt 5
@F lief_dat|date +n||gewünschtes Lieferdatum / wird, wenn <> leer ausgewertet / ist null, wenn lief_kw belegt
@F lief_kw|char(7) +n||gewünschte Lieferwoche / wird, wenn <> leer, ausgewertet / ist null, wenn lief_dat belegt
@F ek_projekt|char(20) +n||Projektnummer, nur bei Bezug auf Projektpreis gefüllt
@F rahmen_jn|char(1) (gn)||wird bei der Neuanlage der AufPosBest-Zeile belegt / "j" es gibt eine offene Rahmenbestellung zum Artikel dieser Auftragsposition
@F rahmen_best_nr|integer(7)||Bestellposition der Rahmenbestellung, von der die neu aufzubauende (Bestellgenerierung oder Bestellvorschlag) Bestellposition abrufen soll / ist bei Abrufaufträgen immer 0 / hat Auftragsposition Zuordnung zu Abrufauftragsposition (ein_auf_nr <> abruf_ein_auf_nr) wird die zugeordnete Rahmenbestellung (abruf_zug_best_nr <> 0) vorgeschlagen
@F rahmen_best_pos_nr|smallint(4)||Bestellposition der Rahmenbestellung, von der die neu aufzubauende (Bestellgenerierung oder Bestellvorschlag) Bestellposition abrufen soll / ist bei Abrufaufträgen immer 0 / hat Auftragsposition Zuordnung zu Abrufauftragsposition (ein_auf_nr <> abruf_ein_auf_nr) wird die zugeordnete Rahmenbestellung (abruf_zug_best_nr <> 0) vorgeschlagen
@E
@T auf_pos_set
@D Setteile für aufzubauende Sethauptposition / Wird beim Speichern einer Setposition befüllt, wenn die Setpositionen im Batch verarbeitet werden / Wird durch den Setaufbau im Batch wieder gelöscht
@F ein_auf_nr|integer(7)|p1|Feldbeschreibungen ident mit auf_pos, wenn nicht anders beschrieben
@F fa_nr|smallint(3)|p2
@F auf_pos_nr|smallint(4)|p3
@F teil_auf_pos_nr|smallint|p4
@F teil_artik_cd|char(20)|
@F teil_mg|decimal(15,6)|
@F teil_vkpr|decimal(12,3)|
@F teil_vkrab1|decimal(4,2)|
@F teil_vkrab2|decimal(4,2)|
@F teil_vkrab3|decimal(4,2)|
@F teil_vkrab4|decimal(4,2)|
@F teil_vkrab5|decimal(4,2)|
@F teil_duest|decimal(15,6)|
@F teil_auf_off_mg|decimcal(12,3)|
@F teil_auf_frei_mg|decimal(12,3)|
@F wv_nr|integer +n|
@F wv_pos_nr|smallint +n|
@F set_stufe|smallint|
@F set_zeile_nr|smallint|
@F teil_artik_mc|char(40)|
@F teil_auf_pos_nr_db|smallint||alte Positionsnummer / 0..Neuanlage
@F offert_erl_kz|char(1)|
@F set_frei_kz|char(1)|
@F set_preis_dru_kz|char(1)|
@F set_stat_kz|char(1)|
@F set_fibu_kz|char(1)|
@F set_teil_dru_kz|char(1)|
@F ap_preis_dru_jn|char(1)|
@F ap_dru_jn|char(1)|
@F ap_stat_jn|char(1)|
@F ap_fibu_jn|char(1)|
@F ap_fibu_kont_jn|char(1)|
@F setpr_netto_jn|char(1)|
@F ewpfand_kz|char(1)|
@E
@T auf_pos_sub
@D Kunden- Auftrag- Position – Freigabedaten / siehe unbedingt auch artik_lag_sub / ist bei auf_pos.auf_lag_ftr = 0 nicht vorhanden / kann für eine auf_pos keine Rows enthalten, wenn auf_pos.auf_frei_mg = 0 / für eine Auftragsposition gilt: / sum(aufs_frei_mg) = auf_pos.auf_frei_mg / oder / count(*) = 0 / Anmerkung: bei Umbuchung eines Chargen-/Geräteartikels von einem Nicht-Chargen-/Gerätelager auf ein Chargen-/Gerätelager muss pro Chragen-/Gerätenummer eine eigene Position erfasst werden
@F ein_auf_nr|integer(7)|p1
@F fa_nr|smallint(3)|p2
@F auf_pos_nr|smallint(4)|p3,f
@F artik_cd|char(20)|r|lt. auf_pos
@F lag_cd|char(11)|r|lt. auf_pos
@F lag_ort /|char(20)|p4|Lagerort / aufart_cd = 'kr', 'ka' siehe fa.komm_pro_lfs_kz / aufart_cd = 'vr' leer / aufart_cd <> 'kr, 'ka' Eingeben siehe lag.lag_ort_inp_jn
@F charge_geraet /|char(40)|p5|Leer, Gerätenummer oder Chargennummer siehe artik_lag_sub / aufart_cd = 'vr' leer / sonst bei Geräten und Chargen- Artikeln nicht leer (ausgenommen [lag.cg_verw_jn] = "n"
@F aufs_frei_mg|decimal(12,3)||freigegebene Menge / die Summe über eine Auftragsposition muß zum Zeitpunkt des Lieferbelegaufbaus = auf_pos.auf_frei_mg sein / muß gleiches Vorzeichen wie auf_pos.auf_frei_mg haben / kann absolutbetragsmäßig nie größer als auf_pos.auf_frei_mg sein (kann aber kleiner sein)
@F geg_lag_ort|char(20)||Gegenlagerort (Lagerort, auf welchen umgebucht wird) / aufart_cd = 'k' & fa.komm_pro_lfs_kz in ("p", "l") siehe fa.komm_pro_lfs_kz / aufart_cd = 'kr', 'i' Eingeben / sonst " "
@F geg_charge_geraet|char(40)||Geräte oder Chargennummer / nur eingebbar, wenn [lag.cg_verw_jn] = "n" und [geg_lag.cg_verw_jn] = "j" und [geg_lag_cd] <> " " / bei Umbuchungslagern wird angenommen, dass dieser dasselbe cg_verw_jn hat wie das Ziellager / sonst fix [charge:geraet] / Zubuchung auf Gegenlager im Lieferscheinaufbau erfolgt mit dieser Chargen-/Gerätenummer
@F ablauf_dat|date +n||Ablaufdatum bei artik.lagfuehr_kz = 'c', artik.ablaufdat_jn = 'j' und [lag.cg_verw_jn] = "j" / sonst NULL
@F geg_ablauf_dat|date +n||Ablaufdatum bei artik.lagfuehr_kz = 'c' und artik.ablaufdat_jn = 'j' / sonst NULL / nur eingebbar, wenn [lag.cg_verw_jn] = "n" und [geg_lag.cg_verw_jn] = "j" und [geg_lag_cd] <> " " / sonst fix [ablauf_dat] / Zubuchung auf Gegenlager im Lieferscheinaufbau erfolgt mit dieser Chargen-/Gerätenummer
@E
@T auf_pos_komm
@D Kunden- Auftrag- Position – Daten für Kommissionsscheindruck / wird beim Kommissionsscheindruck automatisch generiert / Datensätze gelten nur temporär für einen Kommissionscheindruck / wird nur zur Sortierung innerhalb des Kommissionsscheins verwendet, hat sonst keine Bedeutung
@F ein_auf_nr|integer(7)|p1
@F fa_nr|smallint(3)|p2
@F auf_pos_nr|smallint(4)|p3,f
@F sort_lag_ort|char(20)|p4|Lagerort, nach dem am Kommissionsschein sortiert wird / sort_lag_cdlag.lag_ort_inp_jn = "j" / aufart_cd = 'kr' siehe auf_pos_sub.geg_lag_ort / aufart_cd <> 'kr' siehe auf_pos_sub.lag_ort / sonst / artik_lag.inp_n_lag_ort
@F sort_lag_cd|char(11)||Lager, nach dem am Kommissionsschein sortiert wird / aufart_cd = 'kr' siehe auf_pos.geg_lag_cd / aufart_cd <> 'kr' siehe auf_pos.lag_cd /
@F ab_auf_nr|integer(7)||Auftragsnummer Abwicklung
@F veh_cd|char(5)||Verkaufsmengeneinheit
@F lagfuehr_kz|char(1)||lt. artik.lagfuehr_kz
@F zeilen_anz|smallint(4)||Anzahl der zu druckenden "Dummy"-Zeilen
@F erstes_vork_jn|char(1)||Auftragsposition kommt im Kommissionsschein erstmals vor
@E
@T auf_pos_txt
@D Auftragspositions- Textzeilen mit Artikelbezeichnung /  / wenn artik_kz <> 'd': / Wird bei der auf_pos-Neuanlage aus artik_txt vorbelegt, wobei Rows berücksichtig werden für die gilt: / sprache_cd = adr.sprache_cd and kunde.kunde_adr_snr = adr.adr_snr and (ab_jn = 'j' or lfs_jn = 'j' or rech_jn = 'j' or off_jn = 'j' or best_jn = 'j') / union / sprache_cd = adr.sprache_cd and fa.adr_snr = adr.adr_snr and kommsch_jn = 'j' /  / Bei Rows mit sprache_cd <> fa_adr.sprache_cd wird kommsch_jn = 'n'. /  / Weiters wird nach den Artikeltextzeilen abgestellt: / "ZT-Nr:" in adr.sprache_cd + artik.is_zollta_nr wenn Zolltarifnummer nicht leer und auf.zollta_dru_jn = 'j', (nur rech_jn = 'j') / "Ihre Nr:" in adr_sprache_cd + artikid.artikid_cd wenn Kundenartikelnummer definiert ist (nur kommsch_jn = 'n') /  / wenn artik_kz = 'd' / Wird bei der auf_pos-Neuanlage aus auf_pos.artik_mc vorbelegt
@F ein_auf_nr|integer(7)|p1
@F fa_nr|smallint(3)|p2
@F auf_pos_nr|smallint(4)|p3,f
@F txt_typ_kz|char(1)|p4|Texttyp / "r" Richtext / wenn [param.appl_txt_kz = "r"] / Standardfont und -größe lt. Parameter / "p" Plaintext / wenn [param.appl_txt_kz <> "r"]
@F zeile_nr|smallint|p5|Zeilennummer
@F ab_jn|char(1)||auf der AB drucken
@F kommsch_jn|char(1)||auf Kommissionsschein drucken
@F lfs_jn|char(1)||auf Lieferschein drucken
@F rech_jn|char(1)||auf Rechnung drucken
@F off_jn|char(1)||auf Offert drucken
@F fett_jn|char(1)||fett drucken / fix "n", wenn [txt_typ_kz = "r"]
@F unterstrichen_jn|char(1)||unterstrichen drucken / fix "n", wenn [txt_typ_kz = "r"]
@F auf_pos_txt|varchar(max)||Auftragspositionstext- Zeile / generierter Plaintext (auf_pos_rtxt), wenn [txt_typ_kz = "r"] / eingegebener Text, sonst
@F auf_pos_txt_kz|char(1)|ng|'a' = automatisch aus artik_txt bzw. auf_pos.artik_mc generiert / 'z' = automatisch aus Zolltarifnummer generiert / 'k' = automatisch aus Kundenartikelnummer generiert / 'm' = manuell erfasst / weitere durch Customizen möglich, diese sollten Werte von 0-9 haben, um sich mit zukünftigen Werten im TC nicht zu überschneiden
@F best_jn|char(1)||für Zeilen mit best_jn gilt: / werden bei Artikeln mit artik_kz <> "d" nach den sprachabhängigen Artikeltextzeilen aus artik_txt zusätzlich in best_pos_txt gespeichert / werden bei Artikeln mit artik_kz = "d" statt den Artikeltextzeilen in best_pos_txt gespeichert
@F auf_pos_txt_dbid|integer identity||ROWID für Retrieve Richtext / durch DB-Default mit serieller Nummer belegt
@F auf_pos_rtxt|varbinary(max)||Auftragspositionstext Richtext / wenn [txt_typ_kz = "p"], durch DB-Default mit Leerstring belegt
@E
@I unique index i1_auf_pos_txt (auf_pos_txt_dbid)
@T auf_prod
@D Auftrag- Produktionsdaten
@F auf_nr|integer(7)|p1,f
@F fa_nr|smallint(3)|p2
@F artik_cd|char(20)|f|Artikelnummer / artik.artik_kz = 'p'
@F prod_best_mg|decimal(12,3)||bestellte Menge
@F prod_off_mg|computed||= (prod_best_mg – prod_lief_mg) siehe auch artik_lag
@F prod_frei_mg|decimal(12,3)||freigegebene Menge / vorzeichengleich zu prod_best_mg / wird beim Lieferscheinaufbau auf 0 gesetzt / abhängig von fa.auf_prod_frei_kz werden bei Änderungen auch die auf_pos.auf_frei_mg der Teil- Positionen geändert
@F prod_lief_mg|decimal(12,3)|g|gelieferte Menge (=produzierte Menge) / wird beim Lieferscheinaufbau inkrementiert
@F prod_loesch_mg|decimal(12,3)|g|gelöschte Menge / bei erledigten Produktionsaufträgen (prod_best_mg – prod_lief_mg)
@F lag_cd|char(11)|f|Lager / freigegebene Menge bezieht sich auf dieses Lager / Beim Lieferbelegaufbau wird auf dieses Lager zugebucht
@F zuo_ein_auf_nr|integer(7)||Index der zuordnenden Auftragsposition / wenn <> 0, ist der Produktionsauftrag dieser Auftragsposition zugeordnet
@F zuo_auf_pos_nr|smallint(4)||Index der zuordnenden Auftragsposition / wenn <> 0, ist der Produktionsauftrag dieser Auftragsposition zugeordnet
@F auf_prod_frei_kz|char(1)||Kennzeichen Freigabe Produktionsauftrag / wenn artik.lagfuehr_kz = „g“ fix „g“ sonst fix fa.auf_prod_frei_kz
@E
@I index i1_auf_prod (artik_cd, lag_cd, fa_nr)
@T auf_prod_sub
@D Auftrag- Produktions- Freigabedaten / sum(prods_frei_mg) = auf_prod.prod_frei_mg oder / count(*) = 0
@F auf_nr|integer(7)|p1,f
@F fa_nr|smallint(3)|p2
@F lag_ort|char(20)|p3|Lagerort
@F charge_geraet|char(40)|p4|Leer, Gerätenummer oder Chargennummer, siehe artik_lag_sub (ausgenommen [lag.cg_verw_jn] = "n"
@F prods_frei_mg|decimal(12,3)||freigegebene Menge / die Summe über den Produktionsauftrag muß zum Zeitpunkt des Lieferbelegaufbaus = auf_prod.prod_frei_mg sein / muß gleiches Vorzeichen wie auf_prod.prod_frei_mg haben
@F ablauf_dat|date +n||Ablaufdatum bei artikel.lagfuehr_kz = 'c', artikel.ablaufdat_jn = 'j', und [lag.cg_verw_jn] = "j" / sonst NULL
@E
@T auf_txt
@D Auftrag- Textzeilen
@F auf_nr|integer(7)|p1,f
@F fa_nr|smallint(3)|p2
@F txt_typ_kz|char(1)|p3|Texttyp / "r" Richtext / wenn [param.appl_txt_kz <> "p"] / Standardfont "Arial 10" / "p" Plaintext / wenn [param.appl_txt_kz = "p"]
@F zeile_nr|smallint|p4|Zeilennummer
@F wo_kz|char(1)||'a' = Anfang / 'e' = Ende
@F ab_jn|char(1)||auf der AB drucken
@F kommsch_jn|char(1)||auf Kommissionsschein drucken
@F lfs_jn|char(1)||auf Lieferschein drucken
@F rech_jn|char(1)||auf Rechnung drucken
@F off_jn|char(1)||auf Offert drucken
@F fett_jn|char(1)||fett drucken / fix "n", wenn [txt_typ_kz = "r"]
@F unterstrichen_jn|char(1)||unterstrichen drucken / fix "n", wenn [txt_typ_kz = "r"]
@F auf_txt|varchar(max)||Auftragstext- Zeile / generierter Plaintext (auf_txt), wenn [txt_typ_kz = "r"] / eingegebener Text, sonst
@F auf_txt_dbid|integer identity||ROWID für Retrieve Richtext / durch DB-Default mit serieller Nummer belegt
@F auf_rtxt|varbinary(max)||Auftragstext Richtext / wenn [txt_typ_kz = "p"], durch DB-Default mit Leerstring belegt
@E
@I unique index i1_auf_txt (auf_txt_dbid)
@T auf_ueb
@D Auftragspositionsüberschrift / beim Speichern eines Auftrages werden automatisch die Dummy-Zeilen mit ueb_nr = 0 bzw. ueb_nr = 9999 angelegt
@F ein_auf_nr|integer(7)|p1,f
@F fa_nr|smallint(3)|p2|Firma
@F ueb_nr|smallint|p3|Überschriftsnummer
@F sort_ueb_nr|smallint(4)||Überschriftsnummer für die Sortierung auf Belegen / wird, wenn beim Speichern unbestimmt, mit ueb_nr * 10 belegt / Dummy: 0 bzw. 9999
@F newpage_jn|char(1)||Seitenvorschub bevor Überschrift gedruckt wird / wird beim Offertdruck ausgewertet / ist bei Auftragsarten <> "o" fix "n" / Dummy: "n"
@F summe_jn|char(1)||Summe wird nach der letzten Artikelposition dieser Überschrift angedruckt / wird beim Offertdruck ausgewertet / ist bei Auftragsarten <> "o" fix "n" / Dummy: "n"
@F endsumme_jn|char(1)||Positionen, die dieser Überschrift zugeordnet sind, rechnen in Endsumme / wird beim Offertdruck ausgewertet / ist bei Auftragsarten <> "o" fix "j" / Dummy: "j"
@F newpage_nr|smallint +n||Offertdruck bestimmt vor dem eigentlichen Ausdruck den Wert für den Seitengruppenwechsel
@F summe_txt|varchar(60)||Textierung für Überschriftssumme / nur wesentlich, wenn summe_jn = "j" / wenn "", wird als Summentext "Summe" gedruckt
@E
@T auf_ueb_txt
@D Auftragspositionsüberschrift-Textzeilen
@F ein_auf_nr|integer(7)|p1
@F fa_nr|smallint(3)|p2
@F ueb_nr|smallint|p3,f
@F txt_typ_kz|char(1)|p4|Texttyp / "r" Richtext / wenn [param.appl_txt_kz <> "p"] / Standardfont "Arial 10" / "p" Plaintext / wenn [param.appl_txt_kz = "p"]
@F zeile_nr|smallint|p5|Zeilennummer
@F ab_jn|char(1)||auf der AB drucken
@F lfs_jn|char(1)||auf Lieferschein drucken
@F rech_jn|char(1)||auf Rechnung drucken
@F off_jn|char(1)||auf Offert drucken
@F fett_jn|char(1)||fett drucken / fix "n", wenn [txt_typ_kz = "r"]
@F unterstrichen_jn|char(1)||unterstrichen drucken / fix "n", wenn [txt_typ_kz = "r"]
@F auf_ueb_txt|varchar(max)||Auftragstext- Zeile / generierter Plaintext (auf_ueb_rtxt), wenn [txt_typ_kz = "r"] / eingegebener Text, sonst
@F auf_ueb_txt_dbid|integer identity||ROWID für Retrieve Richtext / durch DB-Default mit serieller Nummer belegt
@F auf_ueb_rtxt|varbinary(max)||Auftragsüberschriftstext Richtext / wenn [txt_typ_kz = "p"], durch DB-Default mit Leerstring belegt
@E
@I unique index i1_auf_ueb_txt (auf_ueb_txt_dbid)
@T auf_ust
@D Auftrag- USt/Zeilen / Inhalt temporär für AB- bzw. Offertdruck
@F auf_nr|integer(7) (p1|
@F fa_nr|smallint(3)|p2
@F ueb_nr|smallint|p3,f
@F ust_cd|char(10)|p4,f|USt-Code
@F ust_prz|decimal(4, 2)||USt-Prozentsatz
@F ust_basis|decimal(11,2)||USt-Basis
@F ust_betr|decimal(11,2)||UST-Betrag
@F brutto_betr|decimal(11,2)||Bruttobetrag
@F ust_basis_sktof|decimal(11,2)||skontofähige Ust-Basis
@F brutto_betr_sktof|decimal(11,2)||skontofähiger Bruttobetrag
@E
@T aufart
@D Auftragsarten / Hier sind die, beim Kunden aktivierten Auftragsarten verspeichert, die Neuanlage eines Datensatzes ist über das Verwaltungs-Window nicht möglich. Funktionalitäten sind im Programm codiert, siehe auf.aufart_cd
@F aufart_cd|char(2)|p1|Auftragsart
@F aufart_mc|char(30)|
@F nr_kreis|char(10)||Nummernkreis für die Vergabe der Auftragsnummer
@F vrech_nr_kreis|char(10)||Nummernkreis für die Vergabe der Rechnungsnummer
@F vlfs_nr_kreis|char(10)||Nummernkreis für die Vergabe der Lieferscheinnummer
@F kartei_symbol|char(3)||Symbol für Suche in Lagerbewegungskartei
@F fibu_ueb_kz|char(1)||'j' überleiten / 'n' nicht überleiten / durch customizen weitere Möglichkeiten wie z.B.: / 'z' Zahlungsbuchung bei Barverkauf
@F a_muss_vkrech_kz|char(2)||wenn <> " " Auftrag muß diese Fakturierungsart haben / gilt vor kunde.vkrech_kz
@F a_muss_anz_vklfs|smallint(2) +n||wenn <> leer Auftragsart muß diese Anzahl an Lieferscheinen haben
@F freigeben_jn|char(1)||Vorschlagswert für Auftrag / Nein bedeutet, dass bei Auftragserfassung und Import nicht automatisch freigegeben wird. Wenn dann in Folge ein Auftrag freigegeben wird, wird dabei bis zur Frei Verfügbaren Menge vorgeschalgen. / Ja bedeutet, dass bei der Auftragerfassung/Import bereits die freigegebene Menge vorgeschlagen wird. Dabei darf dann nur die verfügbare Menge berücksichtigt werden. Sobald mehr Reservierungen als Lagerstand vorhanden sind, muss sich jemand definieren, wer die Ware zuerst erhält.
@F limitpruef_jn|char(1)||Kreditlimit bei Auftragserfassung bzw. bei Änderung der Auftragsart prüfen
@F uid_pruef_jn|char(1)||UID-Nummer in Auftragserfassung prüfen / wenn kundeerl.uid_pruef_kz = ‚h’ Ausgabe einer Meldung, (Erfassung ist trotzdem zulässig) / wenn kundeerl.uid_pruef_kz = ‚s’Ausgabe einer Fehlermeldung (Erfassung nicht möglich) / wenn kundeerl.uid_pruef_kz = ‚k’ keine Prüfung / "n" keine Prüfung
@F vrech_liefbeleg_jn|char(1)||gibt an, ob bei dieser Auftragsart Verkaufsrechnungen mit vkrech_kz = "r" tatsächlich Lieferbelege sind / "j" / Rechnung ist Lieferbeleg (Barverkauf, Normalauftrag) / ist der Normalfall / "n" / Rechnung ist kein Lieferbeleg (z.B: GutschriftWert) / ist die Ausnahme / bewirkt, dass Rechnungen mit [vkrech_kz = "r"], trotzdem per E-Mail versandt werden und beim Rechnungsdruck NICHT "RECHNUNG + LIEFERSCHEIN" als Belegtitel verwendet wird.
@F aufart_upid|bigint +n|
@E
@T aufart_fa
@D Auftragsarten Firma / wenn lag_cd <> ' ', ist das Lager der Auftragsposition dadurch bestimmt / z.B.: für Auftragsart Strecke (Streckenlager) oder Gutschrift (Prüflager)
@F aufart_cd|char(2)|p1,f
@F fa_nr|smallint(3)|p2
@F lag_cd|char(11)|f|lag_kz in "e", "l" / dummy-Satz erlaubt
@F lag_fix_jn|char(1)||Lager lt. aufart_fa.lag_cd ist in der Auftragsposition nicht änderbar / darf nur "j" sein, wenn lag_cd <> " "
@F lfs_txt_cd|char(20)||Code des Textbausteines welcher am Lieferscheinende gedruckt wird
@F lfs_a_txt_cd|char(20)||Code des Textbausteines welcher am Lieferscheinanfang gedruckt wird
@F komm_txt_cd|char(20)||Code des Textbausteines welcher am Kommissionsschein in Firmensprache gedruckt wird
@F komm_a_txt_cd|char(20)||Code des Textbausteines welcher am Kommissionsscheinanfang in Firmensprache gedruckt wird
@F a_muss_zahlart_cd|char(5)||wenn <> " " Auftrag muß diese Zahlungsart haben / gilt vor versart.muss_zahlart_cd und kunde.zahlart_cd / Derzeit sinvoll für Barverkauf, weil hier ggf. eine automatische Zahlungsbuchung erfolgt Es muß z.B. als Kondition "Netto Kassa" gedruckt werden.
@E
@T aufart_sprache
@D Auftragsarten Sprachen
@F aufart_cd|char(2)|p1,f
@F sprache_cd|char(5)|p2,f
@F lfs_beleg_txt|char(30)||Belegtitel für Lieferscheinkopf Original
@F lfs_dupl_txt|char(30)||Belegtitel für Lieferscheinkopf der Kopie / wenn <> " " und letzte Kopie / wird dieser Text statt dem Belegtext auf die Duplikate gedruckt / entfällt Kopievermerk
@E
@T aufeinart
@D Auftragseingangsart / Es muß eine Row mit "auto" angelegt sein
@F aufeinart_cd|char(10) (p)||Auftragseingangsart
@F aufeinart_mc|varchar(60)||Auftragseingangsart
@E
@T aufimp
@D Auftragskopf – Importdaten
@F aufimp_snr|biging (p)||interne fortlaufende Nummer
@F aufimpquelle_cd|char(10)||Quelle / zB. welcher Shop, welche Schnittstelle / entspricht Auftragseingangsart / "avenum" / "cas" – TC.WebView Auftragserfassung
@F aufimp_status_kz|char(1)||Status Auftragsimport / u…unvollständig / fehlerhaft / v…Daten vollständig / a…Auftrag aufgebaut (inkl. aller Positionen) / e…ohne Buchung erledigt / Storniert
@F aufimp_status_datz|datetime||Datum der letzten Statusänderung
@F imp_job_snr|bigint||Import-Jobummer
@F tc_auf_nr|integer||TradeControl-Auftragsnummer / wird bei Neuanlage mit 0 belegt / Auftragsimport setzt nach Anlage des Auftragskopfes die Auftragsnummer / wird beim ErledigtSetzen mit -1 belegt
@F fehlertext|varchar(255) +n||Fehlertext
@F referenznummer|varchar(40) +n||Referenznummer der Nachricht / Avenum: <Beleg>-<NachrichtenReferenzNummer> / CAS: casauf_upid
@F referenzdatum|datetime +n||Referenzdatum der Nachricht / Avenum: <Beleg>-<NachrichtenReferenzDatum> / casauf.erf_datz
@F fa_nr|smallint||Firma
@F fil_nr|smallint||Filiale
@F kunde_cd|char(10) +n||Kundennummer / wird aus [la_gln] konvertiert, wenn unbestimmt / wird aus [kunde_gln] konvertiert, wenn unbestimmt / cas: lt. kunde_upid
@F kunde_gln|varchar(20) +n||Kunden-GLN / Avenum: <Beleg>-<Kaeufer>-<PartnerId>
@F la_gln|varchar(20) +n||Lieferanschrift-GLN / ggf. Baustelle / Avenum: <Beleg>-<Lieferort>-<PartnerId>
@F la_name1|varchar(50) +n||Name1 Lieferanschrift / Avenum: <Beleg>-<Lieferort>-<PartnerName01>
@F la_name2|varchar(50) +n||Name2 Lieferanschrift / Avenum: <Beleg>-<Lieferort>-<PartnerName02>
@F la_name3|varchar(50) +n||Name3 Lieferanschrift
@F la_name4|varchar(50) +n||Name4 Lieferanschrift
@F la_strasse|varchar(50) +n||Strasse Lieferanschrift / Avenum: <Beleg>-<Lieferort>-<PartnerAnschrift01>
@F la_ort|varchar(50) +n||Ort Lieferanschrift / Avenum: <Beleg>-<Lieferort>-<Ort>
@F la_plz|varchar(10) +n||Postleitzahl Lieferanschrift / Avenum: <Beleg>-<Lieferort>-<PostleitZahl>
@F la_land_cd|varchar(5) +n||Land Lieferanschrift / Avenum: <Beleg>-<Lieferort>-<LandCodiert>
@F kd_best_dat|datetime +n||Kundenbestelldatum / Avenum: <Beleg>-<AuftragsDatumVerkaeufer>
@F kd_best_txt|varchar(40) +n||Kundenbestellnummer / Avenum: <Beleg>-<AuftragsNummerVerkaeufer>
@F kunde_sb_pers_cd|char(5) +n||Person des Kunden
@F ab_an_email|varchar(250) +n||AB wird bei erfolgreichen Auftragsimport sofort an diese E-Mail gesendet
@F lief_dat|datetime +n||Wunsch-Lieferdatum / Avenum: <Beleg>-<LieferDatumGefordert>
@F erf_usr_cd|varchar(20) +n||Usercode / Bei CAS MDE-User, der der den Auftrag erfasst hat
@F aufart_cd|char(2) +n||Auftragsart
@F versart_cd|char(5) +n||Versandart
@F vkrab|decimal(4,2) +n||Kopfrabatte
@F vkrabk2|decimal(4,2) +n|
@F vkrabk3|decimal(4,2) +n|
@F kundeprovgr_cd|char(10) +n|
@E
@I index i1_aufimp(aufimp_status_kz)
@T aufimp_pos
@D Auftragspositionen – Importdaten
@F aufimp_snr|bigint|p1,f|= siehe aufimp.aufimp_snr
@F aufimp_pos_nr|smallint (4)|p2|Positionsnummer Kunde / Import erfolgt sortiert nach dieser Nummer / Avenum: <Beleg>-<Position>-<PositionsNummer>
@F fa_nr|smallint|r|Firmennummer
@F tc_ein_auf_nr|integer||Auftragsnummer in TC / (0 bei Nauanlage
@F tc_auf_pos_nr|smallint||Auftragspositionsnummer TradeControl / 0 bei Neuanlage
@F artik_cd|char(20) +n||Artikelnummer / wird ggf. aus der EAN-Nummer, kd_artikid_cd bzw. SST-Artikelnummer konvertiert
@F ean_artikid_cd|varchar(20) +n||EAN-Nummer / Avenum: <Beleg>-<Position>-<GTIN>
@F sst_artik_cd|varchar(20) +n||Artikelnummer (Verkäufer) lt. SST (=eigene Artikelnummer) / Avenum: <Beleg>-<Position>-<ArtikelnummerVerkaeufer>
@F kd_artikid_cd|varhar(20) +n||Kundenartikelnummer / Avenum: <Beleg>-<Position>-<Kaeufer>
@F art_bez|varchar(1000) +n||Artikelbezeichnung / Ist nur für die Fehlerbehandlung gedacht
@F sst_mg|decimal(12,3)||Menge in Mengeneinheit / Avenum: <Beleg>-<Position>-<BestellteMenge>
@F sst_eh|char(5) +n||Mengeneinheit / Avenum: <Beleg>-<Position>-<BestellteMengeEinheit>
@F tc_mg|decimal(12,3) +n||Menge in Lagereinheit / wird aus [sst_mg] und [sst_eh] konvertiert
@F veh_mg|decimal(12,3) +n||Verpackungseinheitsmenge
@F vkpr|decimal(11,2) +n||Verkaufspreis / Ist der Verkaufspres belegt müssen auch alle anderen Preis Felder vkrab1 – natrab belegt werden. / cas : wird nur belegt, wenn der Preis manuell ist
@F vkrab1|decimal(4,2) +n||Verkaufspreis / Ist der Verkaufspres belegt müssen auch alle anderen Preis Felder vkrab1 – natrab belegt werden. / cas : wird nur belegt, wenn der Preis manuell ist
@F vkrab2|decimal(4,2) +n||Verkaufspreis / Ist der Verkaufspres belegt müssen auch alle anderen Preis Felder vkrab1 – natrab belegt werden. / cas : wird nur belegt, wenn der Preis manuell ist
@F vkrab3|decimal(4,2) +n||Verkaufspreis / Ist der Verkaufspres belegt müssen auch alle anderen Preis Felder vkrab1 – natrab belegt werden. / cas : wird nur belegt, wenn der Preis manuell ist
@F vkrab4|decimal(4,2) +n||Verkaufspreis / Ist der Verkaufspres belegt müssen auch alle anderen Preis Felder vkrab1 – natrab belegt werden. / cas : wird nur belegt, wenn der Preis manuell ist
@F vkrab5|decimal(4,2) +n||Verkaufspreis / Ist der Verkaufspres belegt müssen auch alle anderen Preis Felder vkrab1 – natrab belegt werden. / cas : wird nur belegt, wenn der Preis manuell ist
@F natrab_mg|decimal(12,3) +n||Verkaufspreis / Ist der Verkaufspres belegt müssen auch alle anderen Preis Felder vkrab1 – natrab belegt werden. / cas : wird nur belegt, wenn der Preis manuell ist
@F bez_ein_auf_nr|integer +n||Bezug zu einer Offertposition
@F bez_auf_pos_nr|smallint +n||Bezug zu einer Offertposition
@E
@T aufimp_txt
@D Auftragskopf/Positions – Texte
@F aufimp_snr|decimal(14,0)|p1,f|interne fortlaufende Nummer
@F aufimp_pos_nr|smallint|p2|Positionsnummer / 0 = Kopftext / >0 = Positionstext
@F zeile_nr|smallint|p3|Zeilennummer
@F aufimp_txt|varchar(255)||Auftragstext / Avenum: <Beleg>-<BelegTexte>-<BelegFreiText>-<FreierText>
@F aufimp_txt_kz|char(1)||KZ Text / b = Belegtext (wird auf allen Belegen angedruckt) / i = Interner Text (wird nur am Kommissionsschein verwendet)
@E
@T aufimpquelle
@D Auftragsimport Quelle
@F aufimpquelle_cd|char(10) (p)||Auftragsimport Quelle
@F aufimpquelle_mc|varchar(60)|
@F aufimp quelle_kz|char(10)||Quelle KZ / zB. welcher Shop, welche Schnittstelle / "avenum" / "cas" – TC.WebView Auftragserfassung / Individuelle Quellen beginnen immer mit "i_"
@F aufeinart_cd|char(10)|f|Auftragseingangsart – Defaultwert für Auftragsanlage mit dieser Quelle
@F artik_bestimmung_kz|char(5)||Wie wird der Aritkel bestimmt / Ist eine Kombination aus folgenden Buchstaben, die in dieser Reihenfolge abgearbeitet werden / a = Schnittstellen Artikelcode / e = EAN / k = Kunden-Artikelnummer / z.,B. "ek" = Zuerste wird versucht den Artikel über die EAN zu finden, danach über die Kunden-Artikelnummer
@F fremd_pos_nr_jn|char(1)||Soll die Auftragsimport Positionsnnummer als Fremdpositionsnummer übernommen werden.
@E
@T bank
@D Banken / ist bei Jetfibuintegration ein View auf die Tabelle anbanken / bei BMD-Fibu oder EuroFib echte Tabelle (Ländercodes müssen mit Fibu konform gehen)
@F bank_land_cd|char(3)|p1,f
@F bank_blz|char(11)|p2
@F bank_bez|char(40)||Bankbezeichnung
@F bic|char(11)||Bank Identifier Code (auch SWIFT-Code oder SWIFT-BIC, oder BIC-Code) / für ausländischen Zahlungsverkehr
@E
@T belegloe_temp
@D Hilfstabelle für Löschen Bewegungsdaten
@F job_snr|decimal(14)|p0|JobNummer
@F belegtab_kz|char(10)|p1|Belegtabelle / "vrech" / "vlfs" / "auf_pos" / "auf" / "erech" / "elfs_pos" / "best" / "best_pos" / "divlgb" / "esetp" / "pk" / "iv" / "ka_gus" / "ka_bel" / "ka_mzl"
@F beleg_nr|integer|p2|Belegnummer / "vlfs" vlfs_nr / "vrech" vrech_nr / "auf_pos" ein_auf_nr / "auf" auf_nr / "erech" erech_nr / "elfs_pos" elfs_nr / "best", "best_pos" best_nr / "divlgb" divlgb_nr / "esetp" esetp_snr / "pk" pk_nr / "iv" iv_nr / "ka_gus" gus_nr / "ka_bel" bel_nr / "ka_mzl" muenzli_nr
@F beleg_pos_nr|integer|p3|Positionsnummer / "vlfs_pos" auf_pos_nr / "vrech", "auf", "erech", "best", "divlgb", "esetp", "pk", "iv", "ka_bel", "ka_mzl" 0 / "auf_pos" auf_pos_nr / "elfs_pos" elfs_pos_nr / "best_pos" best_pos_nr
@F fa_nr|smallint(3)|p4|Firma lt. Belegtabelle / "ka_gus", "ka_bel", "ka_mzl" 0
@F kassa_nr|smallint(3)|p5|Kassennummer / Ist nur bei Kassenbelegen belegt
@E
@T belegtxt
@D Belegfixtexte
@F belegtxt_cd|char(40)|p1|Code eines Belegfixtextes / z.B.: "menge", "preis_iu" ...
@E
@T belegtxt_sprache
@D Belegfixtexte Sprachen
@F belegtxt_cd|char(40)|p1,f
@F sprache_cd|char(5)|p2,f
@F beleg_txt|char(120)||Fixtext für Beleg / z.B.: "Menge", "Preis inkl Ust"
@E
@T best
@D Bestellung
@F best_nr|integer(7)|p1|Bestellnummer
@F fa_nr|smallint(3)|p2|Firma
@F fil_nr|smallint(3)|f|Filiale
@F best_dat|date|ng|Bestelldatum = Erfassungsdatum
@F bestart_cd|char(1)|g,f|v|Bestellvorschlag / best_lag_ftr = 0
@F bestart_cd|char(1)|g,f|b|Bestellung / best_lag_ftr = 1
@F bestart_cd|char(1)|g,f|a|Anfrage an den Lieferanten / best_lag_ftr = 0
@F bestart_cd|char(1)|g,f|p|Produktionsvorschlag / best_lag_ftr = 0
@F bestart_cd|char(1)|g,f|r|Rahmenbestellung / best_lag_ftr = 0
@F bestvor_cd|char(10)|f,ng|Bestellvorschlag / wird beim Bestellvorschlagsgenerierungslauf gesetzt / kann bei Anfragen eingegeben werden, Vorschlag Blank / ist bei manuell erfassten Bestellungen Blank
@F best_dispo_jn|char(1)||Bestellung erfolgt für ein Dispolager / ist normalerweise "j" / wird bei der Bestellgenerierung aus einem Streckenauftrag auf "n" gesetzt, wenn das Streckenlager lt. aufart_fa kein Dispolager ist / darf mit Berechtigung definiert werden / bei Änderung wird für jede Bestellposition das Feld best_pos.best_lag_ftr über Fernsteuerung neu bestimmt
@F waehrung_cd|char(4)|f,ng|Währung für Rechnung / (Belegung bei der Neuanlage lt. Kreditor)
@F lief_cd|char(10)|f,n|Lieferantennummer
@F lief_name1|char(50)||Anschrift des Lieferanten
@F lief_name2|char(50)|
@F lief_name3|char(50)|
@F lief_name4|char(50)|
@F lief_strasse|char(50)|
@F lief_land_cd|char(3)|f
@F lief_plz|char(10)|
@F lief_ort|char(50)|
@F we_name1|char(50)||Anschrift des Warenempfängers lt. fil
@F we_name2|char(50)|
@F we_name3|char(50)|
@F we_name4|char(50)|
@F we_strasse|char(50)|
@F we_land_cd|char(3)|f
@F we_plz|char(10)|
@F we_ort|char(50)|
@F bestweise_cd|char(10)|f|Bestellweise / Ist beim Aufbau des Bestellvorschlages ' ' / wird als Applikationskennzeichen für die Druckzuordnung herangezogen
@F lief_dat|date +n||gewünschtes Lieferdatum >= auf_dat / wird auf den Freitag von lief_kw gesetzt, wenn lief_kw eingegeben wird / dient als Vorschlag für die Positionen, wenn nicht NULL / Ist beim Aufbau des Bestellvorschlages NULL
@F lief_kw|char(7) +n||gewünschte Lieferwoche / wird auf die Woche von lief_dat gesetzt, wenn lief_dat eingegeben wird / dient als Vorschlag für die Positionen, wenn nicht NULL / Ist beim Aufbau des Bestellvorschlages NULL
@F lief_txt|char(60)||Text zum Liefertermin
@F versart_cd|char(5)|f|Versandart
@F liefbed_cd|char(5)|f|Lieferbedingung
@F skonto1_prz|decimal(4,2)||1. Skontoprozentsatz
@F skonto1_tg|smallint(3)||dazu Ziel- Tage
@F skonto2_prz|decimal(4,2)||2. Skontoprozentsatz
@F skonto2_tg|smallint(3)||dazu Ziel- Tage
@F netto_tg|smallint(3)||Ziel- Tage für Netto- Zahlung
@F valuta_dat|date +n||Valutadatum
@F best_info|char(255) +n||Interner Informationstext Bestellung
@F best_fa_pers_cd|char(5)|ng|Sachbearbeiter der eigenen Firma, welcher Bestellung erfasst hat / Bei Bestellvorschlag ist dies zunächst jene Person, welche den Bestellvorschlagslauf gestartet hat, und dann jene, welche den Bestellvorschlag in eine Bestellung umgewandelt hat.
@F lief_sb_pers_cd|char(5)||Sachbearbeiter beim Lieferanten, welcher Bestellung erhält / Ist beim Aufbau des Bestellvorschlages ' '
@F best_zhd|char(50)||zu Handen für Bestellung / Ist beim Aufbau des Bestellvorschlages ' '
@F best_komidart_cd|char(10)||Code der Art der Kommunikations- Identifikation von lief_komidart_cd / nur belegt, wenn bestweise.bestart_kz in ( "e", "f" ) / Ist beim Aufbau des Bestellvorschlages ' '
@F best_komid_wert|varchar(255)||Faxnummer bzw. Emailadresse des Bestellempfängers / nur belegt, wenn bestweise.bestart_kz in ( "e", "f" ) / Ist beim Aufbau des Bestellvorschlages ' '
@F best_zustand_kz|char(1)|g|e|erfasst
@F best_zustand_kz|char(1)|g|b|bestellt (= gedruckt, gefaxt oder gemailt)
@F best_zustand_kz|char(1)|g|t|teilweise geliefert (wird auch durch ein Lieferaviso gesetzt)
@F best_zustand_kz|char(1)|g|g|vollständig geliefert
@F best_best_dat|date +n||Datum zu dem Bestellung ausgeführt (=gedruckt, gefaxt, ... lt. bestart_kz) wurde. / soll auch manuell übersteuerbar sein / wird bei jedem Ausführungslauf gesetzt
@F lief_auf_nr_txt|char(20)||Auftragsnummer des Lieferanten
@F erl_best_nr|integer|g,r|0, wenn Bestellung noch offene Mengen hat, sonst = best_nr siehe dazu best_zustand_kz = 'g'
@F autogen_jn|char(1)|g|automatisch generiert / normalerweise "n" / bei Bestellvorschlag und Bestellgenerierung "j"
@F best_preis_jn|char(1)||Bestellung wird mit Preisen gedruckt / Vorschlag lt. Lieferant / ist bei Anfragen bei der Neuanlage fix "n"
@F ao_snr|integer||AO-Snr / ist eindeutig / dient zum Finden eines AOs
@F best_barcode|char(13)||Barcode für Dokumentenarchiv / kann im Bestellfenster eingegeben werden, wenn [archiv. beleg_kz = "be"] vorhanden ist, / sonst fix ""
@F bestn_datz|date|ng|Erfassungsdatum des Datensatzes [dd.mm.yyyy hh:mm:ss] / durch DB-Default (CURRENT) belegt / Erstbelegung: [best_dat] 00:00:00
@N /  /  /
@E
@I index i1_best ( erl_best_nr, lief_cd, fa_nr )
@I index i2_best(ao_snr)
@T best_txt
@D Bestellung- Textzeilen
@F best_nr|integer(7)|p1,f
@F fa_nr|smallint(3)|p2
@F txt_typ_kz|char(1)|p3|Texttyp / "r" Richtext / wenn [param.appl_txt_kz <> "p"] / Standardfont "Arial 10" / "p" Plaintext / wenn [param.appl_txt_kz = "p"]
@F zeile_nr|smallint|p4|Zeilennummer
@F wo_kz|char(1)||'a' = Anfang / 'e' = Ende
@F fett_jn|char(1)||fett drucken / fix "n", wenn [txt_typ_kz = "r"]
@F unterstrichen_jn|char(1)||unterstrichen drucken / fix "n", wenn [txt_typ_kz = "r"]
@F best_txt|varchar(max)||Bestelltext- Zeile / generierter Plaintext (best_rtxt), wenn [txt_typ_kz = "r"] / eingegebener Text, sonst
@F best_txt_dbid|integer identity||ROWID für Retrieve Richtext / durch DB-Default mit serieller Nummer belegt
@F best_rtxt|varbinary(max)||Bestelltext Richtext / wenn [txt_typ_kz = "p"], durch DB-Default mit Leerstring belegt
@E
@I unique index i1_best_txt (best_txt_dbid)
@T best_pos
@D Bestellung / alle Mengen in best_pos.eeh_cd Menge in kleinster Einheit = best_best_mg * best_pos.keh_eeh_mg
@F best_nr|integer|p1,f
@F fa_nr|smallint(3)|p2
@F best_pos_nr|smallint(4)|p3
@F artik_cd|char(20)|f|artik.artik_kz in ('n', 'd', 'p')
@F artik_mc|char(40)||Artikelmatchcode
@F gar_mo_ek|smallint(3)||Garantiemonate Einkauf
@F eeh_cd|char(5)|f,ng|lt. artik_lief
@F keh_eeh_mg|decimal(9,3)|ng
@F ekpr_keh_eeh_kz|char(1)|ng
@F ekpr_pro_mg|decimal(4,0)|ng
@F ekpr_ftr|decimal(13,7)|ng
@F los_mg|decimal(9,3)|ng
@F wbzeit_best_tg|decimal(3,0)||Wiederbeschaffungszeit in Tagen für Bestellposition
@F wbzeit_bevor_tg|decimal(3,0)||Wiederbeschaffungszeit in Tagen für Errechnung Mindestbestand
@F min_lag_mg|decimal(12,3)||Mindestbestand in Verkaufseinheit
@F best_best_mg|decimal(12,3)||bestellte Menge / nur positiv
@F best_off_mg|computed||= (best_best_mg – best_lief_mg – best_loesch_mg) siehe auch artik
@F best_aviso_mg|decimal(12,3)|r|Menge aus einem offenen Lieferaviso / Eine Bestellposition mit eine Lieferavisomenge <> 0 darf nicht gelöscht oder erledigt gesetzt werden. / Entspricht der Liefermenge von zugeordneten Einganglieferscheinpositionen maximal bis zur offenen Menge. / Wird mit der Lagerbuchung des Lieferavisos wieder vermindert und in die gelieferte Menge verschoben.
@F best_lief_mg|decimal(12,3)|r|gelieferte Menge / wird beim Buchen der Eingangslieferscheinposition inkrementiert / ist bei Rahmenbestellungen die abgerufene (tatsächlich bestellte) Bestellmenge sum(best_best_mg - best_loesch_mg) from best_pos where rahmen_best_nr = best_nr and rahmen_best_pos_nr = best_pos_nr
@F best_loesch_mg|decimal(12,3)|g|gelöschte, nicht gelieferte Menge / Wird eine Position nicht vollständig geliefert, kann hier die restliche offene Menge eingetragen werden um die Position in den Zustand erledigt zu versetzen / kann im Bestellpositionswindow über Extras- Menüpunkt gesetzt werden.
@F ekpr|decimal(12,3) +n||Einkaufspreis
@F ekrab1|decimal(4,2)||Rabatt 1
@F ekrab2|decimal(4,2)||Rabatt 2
@F ekrab3|decimal(4,2)||Rabatt 3
@F ekrab4|decimal(4,2)||Rabatt 4
@F ekrab5|decimal(4,2)||Rabatt 5
@F preis_manu_jn|char(1)||Preis oder Rabatte der Bestellposition wurden manuell übersteuert
@F lief_dat|date||gewünschtes Lieferdatum / Vorschlag bei Neuanlage ist best.lief_dat wenn dieses nicht NULL, bzw. Tagesdatum + artik_lief.wbzeit_best_tg / wird auf den Freitag von lief_kw gesetzt, wenn lief_kw eingegeben wird
@F lief_kw|char(7)||gewünschte Lieferwoche / ist immer die Woche in der lief_dat liegt
@F lief_txt|char(60)||Text zum Liefertermin
@F ab_lief_dat|date +n||bestätigtes Lieferdatum / wird auf den Freitag von ab:lief_kw gesetzt, wenn ab_lief_kw eingegeben wird / kann positionsweise oder für die gesamte Bestellung gesetzt werden
@F ab_lief_kw|char(7) +n||bestätigtes Lieferwoche / ist immer die Woche in der ab_lief_dat liegt / kann positionsweise oder für die gesamte Bestellung gesetzt werden
@F mahnvor_cd|char(10)|f,g|wird beim Mahnvorschlagsgenerierungslauf gesetzt / ist bei nicht zu mahnenden Positionen, bzw. nach der Ausführung der Mahnung leer
@F mahn_stufe|smallint(3)|g|aktuelle Mahnstufe / ist bei der Neuanlage 0 / wird durch Ausführung der Mahnung gesetzt
@F mahn_dat|date +n|g|Mahndatum / ist bei der Neuanlage NULL / wird durch Ausführung der Mahnung gesetzt
@F mahn_sp_jn|char(1)||Defaultwert 'n' / kann manuell gesetzt werden / wenn 'j', wird die Position vom Mahnvorschlagsgenerierungslauf nicht verarbeitet
@F best_pos_info|char(255) +n||Interner Infotext
@F zuo_ein_auf_nr|integer(7)||Index der zuordnenden Auftragsposition / wenn <> 0, ist die Bestellposition dieser Auftragsposition zugeordnet / ist bei einer Rahmenbestellung die zugeordnete Abrufauftragsposition (Rahmenbestellung für genau einen Abrufauftrag)
@F zuo_auf_pos_nr|smallint(4)||Index der zuordnenden Auftragsposition / wenn <> 0, ist die Bestellposition dieser Auftragsposition zugeordnet / ist bei einer Rahmenbestellung die zugeordnete Abrufauftragsposition (Rahmenbestellung für genau einen Abrufauftrag)
@F best_lag_ftr|smallint(1)|r|Lagerbewegungsfaktor (0, 1) / ist, wenn nicht anders beschrieben, 1 / Menge * best_lag_ftr = Menge, die disponiert wird und zum Lagerstand addiert werden wird / siehe auch best.bestart_cd, best.dispo_jn und artik.lagfuehr_kz
@F p_erl_best_nr|integer|r|Bestellnummer wenn Position erledigt, d.h. offene Menge = 0, / 0 bedeutet noch nicht erledigt.
@F lief_cd|char(10)|r|Lieferant lt. Tabelle best
@F ek_projekt|char(20) +n||Projektnummer, nur bei Bezug auf Projektpreis gefüllt
@F staffel_mg|decimal(12,3) +n||Ab dieser Menge gibt es den nächsten Staffelpreis / Wird von der Preisfindung mit Bis Menge + 0,001 belegt, wenn die Bis-Menge 999999999,999 ist, wird NULL abgestellt.
@F rahmen_jn|char(1) (gn)||wird bei der Neuanlage der Bestellposition belegt / "j" es gibt eine offene Rahmenbestellung zu Lieferant und Artikel dieser Bestellposition
@F rahmen_best_nr|integer(7)|n|Bestellposition der Rahmenbestellung, von der die aktuelle Position abgerufen wurde. / ist die Position selbst, falls nicht von Rahmenposition abgebucht wurde (wenn in Neuanlage nicht ausgefüllt).
@F rahmen_best_pos_nr|smallint(4)|f,n|Bestellposition der Rahmenbestellung, von der die aktuelle Position abgerufen wurde. / ist die Position selbst, falls nicht von Rahmenposition abgebucht wurde (wenn in Neuanlage nicht ausgefüllt).
@F lief_artikid_cd|char(40)||Lieferantenartikelnummer
@F ao_snr|integer||AO-Snr / ist eindeutig / dient zum Finden eines AOs
@N /
@E
@I index i1_best_pos ( p_erl_best_nr, artik_cd, fa_nr, best_nr )
@I index i2_best_pos (lief_cd, fa_nr, p_erl_best_nr)
@I index i3_best_pos(ao_snr)
@T best_pos_txt
@D Bestellpositions- Textzeilen mit Artikelbezeichnung /  / wenn artik_kz <> 'd' / Wird bei der best_pos-Neuanlage aus artik_txt vorbelegt, wobei Rows berücksichtig werden für die gilt: / sprache_cd = adr.sprache_cd and lief.lief_adr_snr = adr.adr_snr and best_jn = 'j' / gibt es zu obigem Select keine Row, erfolgt: sprache_cd = fa_adr.sprache_cd and best_jn = 'j' /  / wenn artik_kz = 'd' / Wird bei der best_pos-Neuanlage aus best_pos.artik_mc vorbelegt
@F best_nr|integer(7)|p1
@F fa_nr|smallint(3)|p2
@F best_pos_nr|smallint(4)|p3,f
@F txt_typ_kz|char(1)|p4|Texttyp / "r" Richtext / wenn [param.appl_txt_kz = "r"] / Standardfont und -größe lt. Parameter / "p" Plaintext / wenn [param.appl_txt_kz <> "r"]
@F zeile_nr|smallint|p5|Zeilennummer
@F fett_jn|char(1)||fett drucken / fix "n", wenn [txt_typ_kz = "r"]
@F unterstrichen_jn|char(1)||unterstrichen drucken / fix "n", wenn [txt_typ_kz = "r"]
@F best_pos_txt|varchar(max)||Bestellpositionstext- Zeile / generierter Plaintext (best_pos_rtxt), wenn [txt_typ_kz = "r"] / eingegebener Text, sonst
@F best_pos_txt_kz|char(1)|ng|'a' = automatisch aus artik_txt bzw. best_pos.artik_mc generiert / 'm' = manuell erfasst
@F best_pos_txt_dbid|integer identity||ROWID für Retrieve Richtext / durch DB-Default mit serieller Nummer belegt
@F best_pos_rtxt|varbinary(max)||Bestellpositionstext Richtext / wenn [txt_typ_kz = "p"], durch DB-Default mit Leerstring belegt
@E
@I unique index i1_best_pos_txt (best_pos_txt_dbid)
@T bestart
@D Bestellart / Hier sind die, beim Kunden aktivierten Bestellarten verspeichert, die Neuanlage eines Datensatzes ist über das Verwaltungs-Window nicht möglich. Funktionalitäten sind im Programm codiert, siehe best.bestart_cd
@F bestart_cd|char(1)|p1
@F bestart_mc|char(40)||Matchcode
@F nr_kreis|char(10)||Nummernkreis für die Vergabe der Bestellnummer
@E
@T bestvor
@D Bestellvorschlag / wird vom Bestellvorschlagsaufbau angelegt und vom Umwandlungslauf Bestellvorschlag->Bestellung gelöscht / Es muß auch ein Satz mit bestvor_cd = "" angelegt sein. / kann auch verwendet werden, um Anfragen zu einer "Hauptanfrage" zusammenzufassen / Siehe auch Bestellung.
@F bestvor_cd|char(10)|p1
@F bestvor_kz|char(1)||"v" --> Vorschlag / "a" --> Anfrage / " " --> Dummy-Satz / Bestellvorschlag legt immer Datensätze mit "v" an / Verwaltungswindow legt neue Datensätze immer mit "a" an
@E
@T bestweise
@D Bestellweise
@F bestweise_cd|char(10)|p1|z. B.: / vertreter / fax sofort / fax zeitversetzt / tel / nexmart
@F komidart_kz|char(1)||'f' = Fax / 'e' = E-Mail / 'd' = Ausdruck / 'k' = keine Aktion
@E
@T cas
@D CAS-Datenbanken / Notebooks / ' ' = Zentrale
@F cas_cd|char(10)|p1|Code der CAS-Datenbank / Leer = Zentrale
@F cas_mc|char(40)|
@F aktiv_jn|char(1)||Bei ‚n’ werden keine Daten übertragen (kein Trigger)
@F email_jn|char(1)||Kontakt E-Mails sofort versenden / Bei n wird das E-Mail erst bei der Datenübername im TC aufgebaut
@F adr_snr|integer||Nächste Adressnummer
@F db_rel|char(15)||Datenbank Release
@F dfue_exp_path|varchar(255)||Pfad des DFÜ Verzeichnisses für Exporte
@F dfue_imp_path|varchar(255)||Pfad des DFÜ Verzeichnisses für Importe / Lokaler Pfad auf Empfänger Notebook
@F dfue_email_adr|varchar(255)||Wenn ausgefüllt werden Export Files an diese Adresse gesendet
@F ltz_dfue_nr|integer||letzte DFÜ Nummer
@E
@T cas_aktion
@D CAS Aktionen
@F aktion_nr|integer|p1|Aktions Nummer / Vergabe mittels Tabelle Nummern, Nummernkreis = cas_cd / Dummy Satz mit 0 notwendig
@F fa_nr|smallint|n,p2|Firma
@F kont_mc|char(40)||Kontaktkurztext / Suchbegriff / Betreff
@F aktion_erf_dat|date|ng|Erfassungsdatum
@F aktion_dat|date +n||Aktionsdatum / gilt auch als Basisdatum für den automatischen Aufbau der Kontakte
@F aktion_fa_pers_cd|char(5)|ng|Sachbearbeiter der eigenen Firma, welcher den Kontakt erfaßt hat
@F caskontgrp_cd|char(10)|f|Kontakt-Gruppe / 0 = ' '
@F caskonttxtgrp_cd|char(10)|f|Kontakttextgruppencode / 0 = ' '
@F caskonterg_cd|char(10)|f|Default-Kontakt-Ergebniscode für automatischen Kontaktaufbau / es dürfen nur Ergebnisse mit wiedervorlage_jn = "n" verwendet werden
@F erl_aktion_nr|integer||0 = Aktion offen - Es gibt einen Kontakt, der noch nicht erledigt ist / > 0 = Aktion erledigt- Alle Kontakte sind erledigt / Erledigte Aktionen dürfen nicht mehr verändert werden / Wird von der Reorganisation gesetzt
@F dokument_path|char(128)||Pfadname zu einem dieser Aktion zugeordnetem Dokument
@F dokument_file|char(64)||Filename inkl. Extension des Windows-Dokumentes (.doc, .xls etc.)
@E
@I index i1_cas_aktion erl_aktion_nr
@T cas_casgr
@D Zuordnung Notebook / CASGruppe / Datensatz kann nicht gelöscht werden / Zum Löschen wird er auf inaktiv gesetzt das Löschen erfolgt über ein eigenes Batch-Programm, welches die Zugeordneten Daten von dem Notebooks löscht
@F cas_cd|char(10)|p1,f|Code der CAS-Datenbank
@F casgr_cd|char(5)|p2,f
@F aktiv_jn|char(1)|
@E
@T cas_dfue
@D CAS - DFÜ Tabelle / Wird aus cas_trig aufgebaut
@F cas_cd|char(10)|p1,f|Notebook
@F cas_trig_snr|integer|p2|laufende Nummer
@F tabname|char(20)||Tabellenname
@F akt_kz|char(1)||Aktionskennzeichen / i = Insert / u = Update / d = Delete
@F cd1|varchar(40)|
@F cd2|varchar(40)|
@F cd3|varchar(40)|
@F cd4|varchar(40)|
@F cd5|varchar(40)|
@F cd6|varchar(40)|
@F cd7|varchar(40)|
@F cd8|varchar(40)|
@F dfue_txt|text||Der Inhalt aller Datenfelder der jeweiligen Tabelle mit Trennzeichen Tabulator, sortiert nach Spaltennamen
@F err_txt|varchar(255)||Fehlermeldung des letzten Versuchs
@E
@I index i1_ka_trig (tabname, cd1, cd2, cd3, cd4, cd5, cd6, cd7)
@T cas_kont
@D CAS Kundenkontakte / Erfassung in TC oder über TC-Next / Wird aus Apollo Audi SST befüllt
@F kont_nr|bigint|p1|Kontakt Nummer / Vergabe mittels Tabelle Nummern
@F fa_nr|smallint|p2|Firma
@F kont_mc|char(40)||Kontaktkurztext / Suchbegriff / Betreff
@F kunde_cd|char(10)|f,n|Kundennummer
@F erf_datz|datetime|ng|Erfassungszeitpunkt
@F fa_pers_cd|char(5)||Sachbearbeiter der eigenen Firma
@F kont_dat|date +n||Besuchsdatum
@F von_uhrzeit|char(5)||Uhrzeit Beginn / Format HH:MM
@F bis_uhrzeit|char(5) +n||Uhrzeit Ende / Ist Null, wenn der Besuch in der MDE Lösung gerade erfasst wird. Erfassung wurde begonnen ist aber noch nicht abgeschlossen.
@F caskontgrp_cd|char(10)||Kontakt-Gruppe
@F caskonterg_cd|char(10)|f|Kontakt-Ergebniscode
@F kont_wert|decimal(12,2)||Wert (z.B. Auftragswert od. Angebotswert)
@F aktion_nr|integer|f|Aktionsnummer / 0 = Keine Zuordnung zu einer Aktion
@F kfz_cd|char(10)||KFZ-Nummer
@F von_km|integer|g|Kilometerstand Reisebeginn / Wird von kfz.le_km vorgeschlagen
@F erl_kont_nr|bigint||0 = Kontakt offen / bei > 0 darf nichts mehr geändert werden / Wird abhängig von konterg_cd gesetzt
@F kunde_pers_cd|char(5)||Hauptansprechpartner
@F reorg_prior|char(10)||Priorität für Reorganisation / Vorschlag von caskontgrp
@F auf_nr|integer(7)||TC-Auftrag bzw. -Offert, das diesem Kontakt zugeordnet ist / 0 = nolookupvalue / Kunde des Auftrages muss Kontaktkunden entsprechen
@F dokument_path|char(128)||Pfadname zu einem diesem Kontakt zugeordnetem Dokument / wird nach Definition des Kunden mit dem Kundenordner vorbelegt
@F dokument_file|char(64)||Filename inkl. Extension des Windows-Dokumentes (.doc, .xls etc.)
@F bez_kont_nr|bigint|f|Bezugs-Kontakt Nummer / ist normalerweise ident mit Kontaktnummer / ist bei der automatischen Anlage eines "Wiedervorlagekontaktes" die Bezugskontaktnummer des aktuellen Kontaktes
@F dru_job_snr|bigint||Jobnummer des endgültigen Drucks / 0 = Endgültiger Druck ist noch nicht erfolgt (=Default)
@F name1|varchar(50)|
@F name2|varchar(50)|
@F name3|varchar(50)|
@F strasse|varchar(50)|
@F land_cd|char(3)|
@F plz|varchar(10)|
@F ort|varchar(50)|
@E
@I index i1_cas_kont (erl_kont_nr)
@I index i2_cas_kont (kfz_cd, von_km)
@I index i3_cas_kont (bez_kont_nr)
@I index i4_cas_kont (dru_job_snr, fa_pers_cd)
@T cas_kont_casunt
@D CAS Kontakt - abgegebene Unterlagen
@F kont_nr|bigint|p1,f|Kontakt Nummer
@F fa_nr|smallint|p3|Firma
@F kunde_unt_pers_cd|char(5)|p4|Personencode
@F casunt_cd|char(10)|p5,f|CAS Unterlagencode
@F casunt_txt|char(60)||Text
@E
@T cas_kont_txt
@D CAS Kontakt Personen / Wenn keine Ansprechpartner eingegeben werden, wird ein Datensatz mit kunde_pers_cd = ' ' und caskonttxtgrp_cd = ' ' angelegt.
@F kont_nr|bigint|p1,f|Kontakt Nummer
@F fa_nr|smallint|p3|Firma
@F zeile_nr|smallint|p5|Zeilennummer
@F kunde_txt_pers_cd|char(5)||Ansprechpartner
@F caskonttxtgrp_cd|char(10)|f|Kontakttextgruppe
@F kont_txt|varchar(max)||Textteile
@F fa_pers_cd|char(5)||Person in der Zentrale, die eine Mitteilung erhalten soll / " " = Keine Nachricht
@E
@T cas_kunde_fcol
@D Zuordnung CAS-Kunde -> Freies Kundenlennzeichen
@F kunde_cd|char(10)|p1,f
@F fa_nr|smallint(3)|p2
@F kunde_fcol_cd|char(10)|p3,f|Code der Art des freien Kennzeichens
@F kunde_fcol_wert|char(40)||Column- Wert
@E
@T cas_kunde_fgr
@D Zuordnung CAS-Kunde -> Freie Kundengruppe
@F kunde_cd|char(10)|p1,f
@F fa_nr|smallint(3)|p2
@F fgrart_cd|char(10)|p3|Code der Art der freien Kundengruppe
@F fgr_cd|char(10)|f|Code der freien Kundengruppe
@E
@T cas_tab
@D CAS-Tabellen für erstmalige Datenübernahme
@F cas_cd|char(10)|p1,f|Code der CAS-Datenbank
@F sort_nr|smallint|p2
@F tabelle|char(20)|
@F casgr_jn|char(1)||Übernahme ist von CASGruppe abhängig
@F zr_kz|char(1)||Kennzeichen Zeitraum / In welcher Einheit ist der Zeitraum ein einzuschränkender Zeitraum in der Tabelle angegeben / k = Keine Einschränkung / m = Monate / w = Wochen / t = Tage
@F zr_anz|integer||Anzahl der Zeiteinheiten, die in die Vergangenheit übernommen werde
@F zr_colname|char(18)||Columnname des Zeitraum Feldes / Nur Notwendig wenn ein Zeitraum angegeben wird, und kein Datastore verwendet wird
@F ds_jn|char(1)||Datastore verwenden / Bei casgr_jn = "j" fix "j"
@E
@I unique index i1_cas_tab tabelle, cas_cd
@T cas_trig
@D CAS - Trigger - Datenübernahme / Diese Tabelle wird mit Hilfe von Trigger oder durch die Erstübernahme befüllt
@F cas_trig_snr|serial (p)||laufende Nummer
@F cas_cd|char(10)|f|Notebook
@F tabname|char(20)||Tabellenname
@F akt_kz|char(1)||Aktionskennzeichen / i = Insert / u = Update / d = Delete
@F cd1|varchar(40)|
@F cd2|varchar(40)|
@F cd3|varchar(40)|
@F cd4|varchar(40)|
@F cd5|varchar(40)|
@F cd6|varchar(40)|
@F cd7|varchar(40)|
@F cd8|varchar(40)|
@E
@I index i1_cas_trig (cas_cd, tabname, cd1)
@T casauf
@D CAS-Auftrag / Erfassung der Daten erfolgt in TC-WebView
@F casauf_upid|bigint (p)|
@F fil_upid|bigint||Filiale
@F kunde_upid|bigint||Kunde
@F erf_fa_pers_cd|varchar(10)||Sachbearbeiter der den Auftrag erfasst hat
@F erf_datz|datetime||Erfassungszeitpunkt
@F casauf_status_kz|char(1)||Status / e = erfasst / f = Fertig zur Übertragung / h = Halten / u = Übertragen / Wird im Normalfall automatisch von erfasst auf Fertig zur Übertragung geändert. / Änderungen von Auftrags oder Positionsdaten sind nur im Zustand erfasst oder halten möglich. / Wird vom Auftragsimport auf Übertragen geändert. / Der Auftragsimport verwendet alle im Zustand Fertig zur Übertragung und erfasst, die älter als x Std. sind
@F casaufart_kz|char(2)||Auftragsart / n = Normalauftrag / o = Offert
@F kd_best_txt|varchar(40)||Kundenbestellnummer
@F kd_best_dat|date||Kundenbestelldatum
@F liefadrmanu_jn|char(1)||Lieferadresse ist manuell / Default Nein, nur bei Ja darf die Lieferadresse manuell eingegeben werden
@F name1|varchar(50)|
@F name2|varchar(50)|
@F name3|varchar(50)|
@F name4|varchar(50)|
@F strasse|varchar(50)|
@F land_upid|bigint|
@F plz|varchar(10)|
@F ort|varchar(50)|
@F adr_pers_upid|bigint||Person des Kunden
@F versart_upid|bigint||Versandart
@F vkrabk1|decimal(4,2)||Kopfrabatt 1
@F vkrabk2|decimal(4,2)|
@F vkrabk3|decimal(4,2)|
@F bel_txt|varchar(255) +n||Belegtext / Wird mit Druck auf allen Belegen = "j" übernommen
@F int_txt|varchar(255) +n||Interner Text / Wird nur mit Druck auf Kommissionsschein übernommen
@F lief_dat|date +n||Liefertermin
@F auf_wert|decimal(11,2)||Auftragswert in Währung lt. waehrung_upid / = Summe der Positionswerte
@F aufimp_snr|bigint||Nummer des Auftragsimport Datensatzes
@F ab_an_email|varchar(255) +n||AB wird bei Auftragsimport an diese E-Mail versendet
@F kundeprovgr_upid|bigint||Wird mit einem Defaultwert lt. Erfassungs User belegt
@E
@D /
@E
@T casauf_pos
@D CAS-Auftragsposition / Erfassung der Daten erfolgt in TC-WebView
@F casauf_pos_upid|bigint (p)|
@F casauf_upid|bigint|f
@F artik_upid|bigint||Artikel
@F eh_upid|bigint||Einheit / Ist in Standatd TC immer fix die Lagereinheit
@F auf_best_mg|decimal(12,3)||Bestellte Menge in Einheit
@F vkpr|decimal(11,2)||Verkaufspreis
@F vkrab1|decimal(4,2)|
@F vkrab2|decimal(4,2)|
@F vkrab3|decimal(4,2)|
@F vkrab4|decimal(4,2)|
@F vkrab5|decimal(4,2)|
@F vkpr_keh_veh_kz|char(1)|
@F vkpr_pro_mg|decimal(4,0)|
@F keh_veh_mg|decimal(9,3)|
@F vkpr_ftr|decimal(13,7)||Verkaufspreis Faktor
@F vkrabk_ftr|decimal(1,0)||Kopfrabattfähig Faktor (1/0)
@F natrab_mg|decimal(12,3)||Zusätzliche Naturalrabattmenge
@F pos_wert|decimal(11,2)||Positionswert = auf_best_mg * vkpr_ftr * vkpr / Positionsrabatte / Kopfrabatte * vkrabk_ftr
@F vkpr_manu_jn|char(1)||Verkaufspreis manuell
@F prfind_gefunden_jn|char(1)|
@F prfind_vkpr|decimal(11,2) +n||Verkaufspreis
@F prfind_vkrab1|decimal(4,2) +n|
@F prfind_vkrab2|decimal(4,2) +n|
@F prfind_vkrab3|decimal(4,2) +n|
@F prfind_vkrab4|decimal(4,2) +n|
@F prfind_vkrab5|decimal(4,2) +n|
@F prfind_vkpr_keh_veh_kz|char(1) +n|
@F prfind_vkpr_pro_mg|decimal(4,0) +n|
@F prfind_keh_veh_mg|decimal(9,3) +n|
@F prfind_vkpr_ftr|decimal(13,7) +n||Verkaufspreis Faktor
@F prfind_vkrabk_ftr|decimal(1,0) +n||Kopfrabattfähig Faktor (1/0)
@F prfind_natrab_mg|decimal(12,3) +n|
@F prfind_natrab_basis_mg|decimal(12,3) +n|
@F pos_bel_txt|varchar(255) +n||Wird auf allen Belegen gedruckt (zusätzlich zum Standard Artikeltext) / Bei einem diversen Artikel muss dieser Text als Artikelmatchcode und Artikeltext (ersetzend) übernommen werden / Zeilenumbruch möglich
@F pos_int_txt|varchar(255) +n||Wird nur am Kommissionsschein gedruckt / Zeilenumbruch möglich
@F bez_auf_pos_upid|bigint||Offert Auftragsposition bei Offert Bezug
@F bez_casauf_pos_upid|bigint||Offert CAS-Auftragsposition bei Offert Bezug
@F ist_erledigt_jn|char(1)||um Offertposition zu erledigen
@F casauf_bezbel_upid|bigint|
@F offueb_menge|decimal(12,3)||Abgerufene Offertmenge
@E
@T casgr
@D CAS-Gruppen / Es gibt einen Dummy-Satz mit casgr_cd = " "
@F casgr_cd|char(5)|p1|Code
@F casgr_mc|char(40)|
@E
@T caskfz
@D KFZ für Fahrtenbuch / Beförderungsmittel / Dummy Datensatz mit "" vorhanden (fabu_kz = s)
@F kfz_cd|char(10)|p1|KFZ-Nummer
@F kfz_mc|char(40)|
@F le_km|integer|g|letzter Kilometerstand
@F le_km_dat|datetime|g|Datum + Uhrzeit des letzten Kilometerstandes (Bis Zeit der letzten Fahrt oder des letzten Besuchsberichtes mit diesem KFZ).
@F km_pruefen_jn|char(1)||Fahrtenbucheintragungen für dieses KFZ müssen lückenlose von- bis-Kilometer nachweisen / Bei Firmenauto Fix j / Bei Privatauto auswählbar / Sonst Fix "n"
@F kfz_aktiv_jn|char(1)||KFZ ist aktiv / Inaktive KFZ werden nicht an Apollo ausgegeben und können nicht im Fahrtenbuch verwendet werden
@F apollo_applpers_cd|char(10) +n||Zugeordnete Person für Apollo Export / Wird auch für die TC.Next ADM Lösung verwendet. Hier sind nur Fahrzeuge auswählbar die den eigenen oder keinen User eingetragen haben.
@F kfzart_kz|char(1)||KFZ / Beförderungsmittel KZ / f = Firmenauto / p = Privatauto / s = Sonstiges (kein Fahrtenbuch – zuFuss, Bahn …)
@E
@T caskfz_fabu
@D Fahrtenbuch
@F fabu_snr|bigint (p)||= TC-Next Upid
@F kfz_cd|char(10)|f|KFZ-Nummer
@F von_km|integer||Kilometerstand Reisebeginn / Wird bei Neuanlage von kfz.le_km vorgeschlagen / kann bei csdkfz.km_pruefen_jn = "j" nicht geändert werden / Ist bei Sonstigen Beförderungsmittel lt. KFZ fix 0
@F bis_km|integer||Kilometerstand Reiseende / Darf nicht kleiner als von_km sein / Ist bei Sonstigen Beförderungsmittel lt. KFZ fix 0
@F von_dat|datetime||Von Datum/Zeit
@F von_uhrzeit|char(5)|
@F bis_dat|datetime||Bis Datum/Zeit
@F bis_uhrzeit|char(5)|
@F privat_jn|char(1)||KZ, ob private oder geschäftliche Fahrt
@F erf_dat|datetime|ng|Datum/Uhrzeit der Erfassung
@F fa_nr|smallint||Firma
@F fa_pers_cd|char(5)||Sachbearbeiter der eigenen Firma (Fahrer)
@F fabu_wt|decimal(10,2)||Betrag
@F fabu_wt_txt|varchar(70)||Text zu Betrag
@F fabu_txt|varchar(255)||Text
@F start_kunde_cd|char(10) +n||Kundennummer Start Adresse / wenn leer kein Kunde
@F start_name1|varchar(50)|
@F start_name2|varchar(50)|
@F start_name3|varchar(50)|
@F start_strasse|varchar(50)|
@F start_land_cd|char(3)|
@F start_plz|varchar(10)|
@F start_ort|varchar(50)|
@F ziel_kunde_cd|char(10) +n||Kundennummer Start Adresse / wenn leer kein Kunde
@F ziel_name1|varchar(50)|
@F ziel_name2|varchar(50)|
@F ziel_name3|varchar(50)|
@F ziel_strasse|varchar(50)|
@F ziel_land_cd|char(3)|
@F ziel_plz|varchar(10)|
@F ziel_ort|varchar(50)|
@F fabu_kz|char(3)||Fahrtenbuch-KZ (Zweck der Fahrt) / k = Kundenbesuch (privat_jn = "n") / p = Privat (privat_jn = "j") / h = Heimfahrt / b = Fahrt ins Büro / Wird gesetzt, wenn der Fahrtenbucheintrag aus einem Büro Besuchsbericht erstellt wird. Wenn das jedoch die erste Fahrt am Tag ist, wird statdessen Privat verwendet.
@F apollo_uuid|varchar(50) +n||Eindeutige Identifikation der Apollo App (Geräte + Installation)
@F apollo_fb_id|integer +n||Eindeutige Apollo Farhtenbuchnummer innerhalt einner apollo_uuid
@E
@I index i1_caskfz_fabu (kfz_cd, von_datz)
@I index i2_caskfz_fabu (kfz_cd, von_km)
@I index i3_caskfz_fabu (apollo_uuid, apollo_fb_id)
@I index i4_caskfz_fabu (kfz_cd, bis_km)
@T caskfz_fabu_kont
@D Fahrtenbuch-Kontakt
@F fabu_snr|bigint|p1|interne Nummer
@F kont_nr|bigint|p2|Kontaktnummer
@F fabu_kont_kz|char(1)||1 = Anfahrt / 2 =Abfahrt
@E
@I index i1_caskfz_fabu_kont (kont_nr, fabu_kont_kz)
@T caskmg
@D CAS Kilometergeld / Verwaltung auf der Reisekostengruppe
@F casreikorgr_cd|char(5)|p2,f
@F fa_nr|smallint|p2|Firmennummer
@F ab_dat|date|p3|Ab-Datum
@F bis_dat|date|g|Bis-Datum
@F ab_km|integer|p4|Ab gefahrene KM pro Jahr
@F bis_km|integer|g|Bis gefahrene KM pro Jahr
@F kmg_wt|decimal(8,2)||Kilometergeld pro gefrahrenden km
@F reikopos_kz|char(2)||Reisekostenpositions KZ / Wird für den automatischen Aufbau von Kilometergeld in den Resekosten verwendet / km = Kilometergeld / ku = Kilometergeld über maximale Kilometer
@E
@T caskonterg
@D CAS Kontaktergebniss / Dummysatz mit caskonterg_cd = ' ' erforderlich, dieser wird automatisch bei der Anlage der Kontaktgruppe generiert
@F caskontgrp_cd|char(10)|p1
@F caskonterg_cd|char(10)|p2
@F caskonterg_mc|char(40)|
@F caskonterg_kz|char(1)||o|offen (Dummysatz)
@F caskonterg_kz|char(1)||p|Positiv erledigt / Datum letzter Besuch am Kundenstamm wird upgedatet
@F caskonterg_kz|char(1)||n|Negativ erledigt
@F wiedervorlage_jn|char(1)||Bei Offen immer 'n' / Bei 'j' wird automatisch ein neuer offener Kontakt an den selben Kunden erzeugt.
@E
@T caskontgrp
@D CAS Kontaktgruppe / Dummy Satz ' '
@F rp_cd|char(10)|p1
@F caskontgrp_mc|char(40)||Kontaktgruppentext
@F reorg_prior|char(10)||Priorität für Reorganisation der Kontakte
@F le_kont_dat_jn|char(1)||Bei jenen Kontakten soll das letzte Kontaktdatum am Kundenstamm aktualisiert werden
@F caskontgrp_apollo_jn|char(1)||Ausgabe Apollo
@F fabu_jn|char(1)||Fahrtenbucheintrag soll erstellt werden.
@F diaet_jn|char(1)||Diäten werden berechnet
@F buero_jn|char(1)||Bürotätigkeit
@E
@T caskonttxtgrp
@D CAS Kontakttextgruppe / Dummy = ' '
@F caskonttxtgrp_cd|char(10)|p1
@F caskonttxtgrp_mc|char(40)|
@E
@T casmitbew
@D CAS-Mitbewerber
@F casmitbew_cd|char(10)|p1
@F casmitbew_mc|char(40)||Bezeichnung
@E
@T casmitbewgr
@D CAS-Mitbewerbergruppe / Hier können z.b. Produktgruppen für die Zuordnung Mitbewerber-Kunde definiert werden
@F casmitbewgr_cd|char(10)|p1
@F casmitbewgr_mc|char(40)||Bezeichnung
@E
@T casreiko
@D Reisekosten
@F reiko_nr|bigint|p1|Reisekostennummer / =TC.Next ID
@F fa_nr|smallint|p2|Firma
@F fa_pers_cd|char(5)||Sachbearbeiter der eigenen Firma
@F tag_dat|date||Datumreiko
@F reikopos_kz|char(2)||Reisekostenpositions KZ / di = Diäten / ns = Nächtigungsspesen / kb = KFZ-Kosten Bar / km = Kilometergeld / ku = Kilometergeld über maximale Kilometer / sk = Sonstige Kosten / … Beliebig erweiterbar
@F spesen_wt|decimal(8,2)||Spesen Wert
@F reiko_bel_fcd|varchar(20)||Externe Belegnummer des Spesen Beleges
@F reiko_manu_jn|char(1)||Reisekosten wurden manuell erfasst (oder über Apollo SST übermittelt) / wird bei manueller Änderung des Spesenwerts gesetzt
@F reiko_txt|varchar(1000)||Buchungstext
@F kont_nr|bigint +n||Verknüpfung mit Kontakt (0 erlaubt)
@F reiko_bild|blob +n||Reisekosten Bild
@E
@I index i1_casreiko (fa_pers_cd, fa_nr, tag_dat)
@I index i2_casreiko (kont_nr, fa_nr)
@T casreikogrp
@D Reisekostengruppe / Dient zur Hinterlegung von unterschiedlichen Sätzen für die Reisekostenabrechnung von z.B. Angestellten und Arbeitern
@F casreikogrp_cd|char(5)|p1|Reisekostengruppencode / ang = Angestellte (= TC Default) / arb = Arbeiter
@F fa_nr|smallint|f,p2|Firmennummer
@F casreikoprg_mc|varchar(60)||Reisekostengruppen Matchcode
@F di_tagsatz|decimal(8,2)||Diäten Tagessatz
@F di_ver_tagsatz_tg|smallint(2)||Diaten Ab-Tage für verringerten Tagessatz / Bei Angestellten am dem 13. Tag
@F di_ver_tagsatz|decimal(8,2)||Diäten verringerter Tagessatz
@F di_min_std|smallint(2)||Mindest Stunden für die Diäten / Bei Angestellten momentan 3 / Bei Arbeitern momentan 6
@F di_tagsatz_std|smallint(2)||Stunden für die der Tagsatz gilt / Bei Angestellten momentan 12 – damit wird bei unter 12 Stunden pro Stunde ein 12tel des Tagsatzes verwenden / Bei Arbeitern momentan 6 / Da das auch den Mindeststunden entspricht wird dadurch immer der komplette Tagessatz verwendet
@F reikostd_rund_kz|char(3)||Reisekosten-Stunden Rundungsregel / auf = Aufrunden / ab - = Abrunden / kfm = Kaufmännisch runden
@F az_pause_std|decimal(4,2)||Automatische Pause in Stunden
@F az_pause_min_std|decimal(4,2)||Mindest Arbeitszeit in Stund für Pausenabzug
@E
@T casreikogrp_plz
@D Reisekostengruppe – PLZs für die keine Diäten gerechnet werden dürfen / Abnängig von der Filiale des Lagers der Person werde bei Fahrten zu/von Adresse mit diesen PLZ´s keine Diäten berechnet
@F casreikogrp_cd|char(5)|p1,f|Reisekostengruppencode / ang = Angestellte (= TC Default) / arb = Arbeiter
@F fa_nr|smallint|p2|Firmennummer
@F fil_nr|smallint|p3,f|Filialnummer
@F land_cd|char(3)|p4|Ländercode
@F von_plz|char(10)|p5|Von PLZ
@F bis_plz|char(10)||Bis PLZ
@E
@T castag
@D Tagesdaten für Besuchsbericht / Fahrtenbucherfassung / Wird wenn nicht vorhanden aus den Besuchsberichten, Reisekosten oder Fahrtenbuchdaten automatisch erstellt
@F fa_nr|smallint|p1|Firma
@F fa_pers_cd|char(5)|p2|Sachbearbeiter der eigenen Firma (Fahrer)
@F tag_dat|date|p3|Datum
@F kfz_cd|char(10)||Fahrzeug mit dem man an diesem Tag unterwegs ist / Dient als Vorschlag für die Besuchsbericht/Fahrtenbucherfassung kann aber übersteuert werden
@F abfahrts_datz|datetime +n||Abfahrtszeit am Morgen
@F abfahrt_km|integer +n||Abfahrts KM Stand / Ist bei einem lücklosen Fahrtenbuch der letzte KM-Stand des Fahrzeugs
@F ankunfts_datz|datetime +n||Ankuftszeit am Abend
@F ankunfts_km|integer +n||Ankunfts KM Stand am Abend
@F reikotag_kz|char(2) /||Reisekosten Tages KZ / r = Reisekosten (= Fixer Wert bei Erfassung in TC.Next) / Nur hier können Reisekosten erfasst werden / Bei allen anderen sind reiko_von/bis_zeit null, die reiko_anz_std und di reiko_tag_nr fix 0 / b = Bürotätigkeit / u = Urlaub / k = Krankenstand / …. beliebig erweiterbar
@F reiko_tag_nr|smallint||Tag im Monat mit Reisekosten / Ist bei Positionen ohne Diäten immer 0 / Sonst pro Monat und Mitarbeiter eindeutig
@F reiko_txt|varchar(1000)||Text
@F erf_datz|datetime||Zeitpunkt der Erfassung
@F dru_job_snr|decimal(14,0)|g|Jobnummer des Ausdruckes
@F reiko_anz_std|smallint||Anzahl Stunden für die Diätenberechnung / Runden lt. casreikogrp
@F reiko_rech_kz|char(1)||Reisekostenberechnungs KZ / o = Offen – Reisekosten müssen noch berechnet werden / m = Manuell – Von/Bis AZ oder Reiko/AZ Stunden/Pause wurde manuelle geändert / e = Erledigt – Reisekosten wurden erstellt / Wird von Fahrtenbuch oder Besuchsbericht von e auf o gesetzt, wenn an diesem Tag für diese Person etwas geändert wird.
@F az_von_zeit|datetime +n||Von Zeit für die Arbeitszeitberechnung
@F az_bis_zeit|datetime +n||Bis Zeit für die Arbeitszeitberechnung
@F az_std|decimal(4,2)||Arbeitszeit in Std.
@F az_pause_std|decimal(4,2)||Pause, die in der Arbeitszeit berücksichtigt ist
@F naechtigung_jn|char(1)|
@E
@T casunt
@D CAS-Unterlagen
@F casunt_cd|char(10)|p1
@F casunt_mc|char(40)|
@F casunt_info|char(255)|
@E
@N /  /  /
@E
@T debitor
@D Debitorendaten, welche nicht in der Fibu verspeichert sind (g) / Datensatz wird beim Speichern des Kunden angelegt, falls er nicht vorhanden ist / Es gibt einen Datensatz mit debitor_nr = 0, das sind alle Interessenten / Auftragswerte werden über auf.op_debitor_nr gelesen bzw. geschrieben
@F debitor_upid|bigint +n|
@F debitor_nr|integer(9)|p1|Debitorennummer inkl. Kategorie
@F fa_nr|smallint(3)|p2,f
@F debitor_mc|char(30)|g|Matchcode / In die Jetfibu werden nur die ersten 15 Stellen übergeleitet
@F debitor_adr_upid|bigint +n|
@F debitor_adr_snr|integer|f
@F debitor_mc2|char(15)||Matchcode 2 / bei Einsatz von EuroFib im rechten Bildschirmbereich
@F debitor_mc3|char(15)||Matchcode 3 / bei Einsatz von EuroFib im rechten Bildschirmbereich
@F debitor_ktobez|char(40)||Kontobezeichnung / wird bei der automatischen Anlage mit adr.name1 + ' ' + adr.plz + ' ' + adr.ort belegt / bei Einsatz von EuroFib im rechten Bildschirmbereich
@F waehrung_cd|char(4)|f|Währung
@F debitor_divers_jn|char(1)||Debitor ist divers / Wenn einem nicht diversen Kunden ein diverser Debitor zugeordnet ist, so muss immer die Lieferadresse auch als Rechnungsadresse verwendet werden. / Ein diversen Debitor kann keine UID-Nummer hinterlegt haben.
@F ustid|char(14)||UST-Identifikationsnummer
@F ustid_dat|datetime +n||UST-Identifikationsnummer – Datum / wird bei der Überleitung in die Jetfibu im Format JJJJMMDD ausgegeben
@F kreditlimit|decimal(11,2)||Kreditlimit
@F zahlkond_nr|integer|f|Zahlungskondition / F-Key nur in Version ohne Jetfibuintegration vorhanden
@F frktonr|char(15)||Fremdkontonummer
@F mhktosperre_kz|char(1)||Kennzeichen für Mahnsperre des Kontos / bei Jetfibuintegration folgende Werte / 0...Konto für Mahnung nicht gesperrt / 1...Konto für Mahnung gesperrt / für BMD folgende Werte / 0..der Kunde wird gemahnt / 1..der Kunde wird beim nächsten Mahnlauf nicht gemahnt / 2..der Kunde wird nie gemahnt / für EURO-FIB folgende Werte / J… Mahnung / K … nur Kontoauszug / N … Mahnsperre
@F zahlungsart_kz|char(3)||Kennzeichen Zahlungsart / bei Jetfibuintegration müssen die Kennzeichen lt jetfibu.anzlgart angelegt werden / bei Einsatz von EuroFib im rechten Bildschirmbereich
@F vorschlag_cd|char(15)||für holen Vorschlagsrecord bei Neuanlage
@F off_auf_wert|decimal(11,2)||Summe offener Auftragswert (gerechnet von auf_off_mg) in GW / Bebuchung bei Auftragserfassung und Verkaufslieferschein- Aufbau / wird durch den Tagesabschluß neu errechnet
@F frei_auf_wert|decimal(11,2)||Summe freigegebener Auftragswert (gerechnet von auf_frei_mg) in GW / Bebuchung bei Auftragserfassung, Verkaufslieferschein- Aufbau, Rückstandauflösungslauf / wird durch den Tagesabschluß neu errechnet
@F off_vlfs_wert|decimal(11,2)||Summe offener Lieferscheinwert in GW / wird beim vlfs- Aufbau bebucht / der vrech- Aufbau hat keinen Einfluß / wird durch den Tagesabschluß neu errechnet
@F saldo|decimal(11,2)||Saldo lt. Fibu + Belege aus Schnittstelle in GW / wird ausschließlich durch den Tagesabschluß errechnet / Ist keine (Jet-) Fibu vorhanden, muß dafür gesorgt werden, dass die Schnittstelle auch wieder gelöscht wird, da sonst der Saldo immer größer wird.
@F saldo_faellig|decimal(11,2)||Saldo lt. Fibu fällig in GW / wird ausschließlich durch den Tagesabschluß errechnet
@F max_mahn_stufe|smallint(2)||höchste Mahnstufe aller Ops
@F wechselobligo|decimal(11,2)||Wechselobligo in GW
@F vrechausart_cd|char(10)|f|Ausgangsrechnung Ausgabeart
@F e_vrech_komid_wert|char(255)||E-Mail-Adresse für elektronischen Versand Ausgangsrechnung / muss bei vrechausrt.vrech_druck_kz = „e“ ausgefüllt sein
@F deba_dat|datetime||letztes Änderungsdatum des Debitor / wird bei jedem Speichern mit dem Tagesdatum+Zeit belegt
@F nur für EURO-FIB|bei Einsatz von JetFibu oder BMD-Fibu im rechten Bildschirmbereich|
@F kod_mahn_art|char(1)||Mahnungsart / 1 = Druck / 2 = Fax / 3 = Email
@F kod_mahn_fax|varchar(255) +n||Faxnummer Mahnung
@F kod_mahn_mail|varchar(255) +n||Mailadresse Mahnung
@F kod_vertreter|smallint(4)||Vertreter - keine Plausibilitätsprüfung
@F kod_uid_chk_nr|char(1)||Prüfkennzeichen UID-Datum / "0"=ungeprüft / "1"= Status 1 - UID ok, Adresse nicht ok / "2" = Status 2 - UID ok, Adresse ok / "3" = ungültig / "9" = ohne UID
@F ustid_ungueltig|char(14)||nur bei ungültiger UID belegt [kod_uid_chk_nr in (1, 3)]
@F bbg_partner_fcd|varchar(30)||BBG-Partnernummer
@F bbg_geszahl_fcd|varchar(60)||BBG-Geschäftszahl / Ihre Vertragsnummer
@F deb_uid_job_snr|decimal(14)||Jobnummer letzte Online-UID-Prüfung / fixer Default Neuanlage 0
@F debitor_dbid|integer identity||ROWID für TcNext / durch DB-Insert mit serieller Nummer belegt
@F skonto1_prz|decimal(4,2)||Skonto1InProzent / Bei zahlkond_nr <> 0 Skton1-Nettotage fix lt. Zahlkond, wird auch von dort upgedatet (ausg. JetFIBU)
@F skonto1_tg|smallint(3)||Skonto1Tage
@F skonto2_prz|decimal(4,2)||Skonto2InProzent
@F skonto2_tg|smallint(3)||Skonto2Tage
@F netto_tg|smallint (3)||NettoTage
@E
@I unique index i1_debitor (debitor_dbid)
@I index i0_debitor_upid(debitor_upid)
@T debitor_bank
@D Zuordnung Debitor -> Banken
@F debitor_nr|integer|p1,f
@F fa_nr|smallint(3)|p2
@F zeile_nr|smallint|p3|lfd. Zeilennummer / Zeile 1 ist Standardbankverbindung / Applikation sortiert nicht
@F bank_land_cd|char(3)|
@F bank_blz|char(11)|f
@F bankkonto|char(20)||Bankkontonummer
@F iban|char(34)||Iban bestehend aus / wird in Fibu übergeleitet (als Kontonummer) / ## Iso-Länderkennzeichen / ## Prüfziffer / ##### Bankleitzahl / ########### Bankkontonr / in Österreich ist die Iban 20-stellig, kann aber je Land anders sein. Max. Länge 34
@F nur für EURO-FIB|bei Einsatz von JetFibu oder BMD-Fibu nicht sichtbar|
@F zah_art|char(1)||Zahlungsart / U=Überweisung / E=Einzug / S=Scheck / L = SEPA-Lastschrift / F = SEPA-Firmenlastschrift
@F zah_aktiv|char(1)||Aktiv im Zahlungsverkehr (J/N)
@F aviso_jn|char(1)||Aviso (J/N)
@F sepa_mandat|char(35)||Sepamandat (Referenznummer)
@F sepa_mandat_ddat|date +n||Mandat Druckdatum
@F sepa_mandat_udat|date +n||Mandat Unterschriftsdatum
@E
@T debitor_dsgvo
@D DSGVO-Daten Debitor / View für Generierung Infoblatt Kunde / ist durch Betreuer zu Customizen / im Standard nur "from pfu_selkonst" / Beispiel Verwendung siehe [kunde_dsgvo]
@F debitor_dbid|integer|p1
@F zeile_nr|integer|p2|Sortiernummer
@F txt1|char(100)||Text1, Label
@F txt2|char(100)||Text2, Wert
@E
@T debitor_fgr
@D Zuordnung Debitor -> Freie Debitorengruppe / bei Jetfibuintegration werden hier die scrit*-Felder verwaltet / bei EURO-FIB werden hier die d_sele_*-Felder verwaltet / bei BMD-Fibu werden hier die Freifelder (alf[1-3]; num[1-3]) verwaltet
@F debitor_nr|integer|p1,f
@F fa_nr|smallint(3)|p2
@F fgrart_cd|char(10)|p3|Code der Art der freien Debitorengruppe
@F fgr_cd|char(10)|f|Code der freien Debitorengruppe
@E
@T debitor_op
@D Offene Posten / ist bei Jetfibuintegration ein View
@F debitor_nr|integer|p1,f
@F fa_nr|smallint(3)|p2
@F vrech_nr|integer||Rechnungsnummer
@F symbol|char(3)||Symbol
@F mahnstufe|smallint||Mahnstufe
@F mhsperre_kz|smallint||Kennzeichen Mahnsperre
@F beleg_dat|datetime||Belegdatum
@F faellig_dat|datetime||Fälligkeitsdatum
@F fakt_betr|decimal(11,2)||Rechnungsbetrag
@F offen_betr|decimal(11,2)||offener Rechnungsbetrag
@F zahl_betr|decimal(11,2)||bezahlter Rehcnungsbetrag
@F skonto_betr|decimal(11,2)||Skontobetrag
@F zahl_dat|datetime||Zahlungsdatum
@F belegart_kz|smallint||Kennzeichen Belegart
@E
@T divlgb
@D Diverse Lagerbuchung (n) / bei positiven Differenzen zu einem Artikel ohne DUEST werden die DUEST- Felder mit 0 belegt / es dürfen in den Buchungszeilen nur Lager mit gleicher DuEst-Gruppe [lag.duestgrp_cd] verwendet werden
@F divlgb_nr|integer(7)|p1|Vergabe mittels Tabelle nummern
@F fa_nr|smallint(3)|p2,f|Firma
@F divlgb_dat|date||Datum der Lagerbewegung
@F divlgbart_cd|char(3)|f|siehe dort / es gibt im Buchungsprogramm Berechtigungen "abgang" und "zugang" / Es dürfen nur solche Symbole gewählt werden, für welche die entsprechenden Berechtigungen vorhanden sind.
@F artik_cd|char(20)|f|artik.artik_kz in ('n', 'p')
@F duest_b|decimal(15,6) +n||lt. [artik_lag] der 1. Buchungszeile
@F duest|decimal(15,6) +n||w.o.
@F divlgb_info|char(255) +n||interner Infotext
@F divlgb_fa_pers_cd|char(5)|ng|Sachbearbeiter, welcher gebucht hat
@F kartei_snr|integer|g|Lagerbewegungen in Kartei / eine Kartei- Row entspricht einer Zeile im Bewegungs- DW
@F verb_mg_ftr|smallint(1)|ng|lt. divlgbart
@F verbmg|computed||Verbrauchsmenge / = sum(kartei_lagbew.bew_mg) * divlgb.verb_mg_ftr / wird bei der Mindestbestandsberechnung als Verbrauch verwendet
@F divlgb_mon|char(6)|r|Monat lt. divlgb_dat
@F verb_gebucht_jn|char(1)||Verbrauchsmenge verbucht / wird vom "Statistikverbuchen" gesetzt
@E
@I index i1_divlgb(kartei_snr)
@I index i2_divlgb(artik_cd, divlgb_dat)
@I index i3_divlgb(verb_gebucht_jn)
@T divlgbart
@D Diverse Lagerbuchungsart
@F Buchungsart|abgang_jn||zugang_jn
@F Umbuchung|n|
@F allgemeine Lagerkorrektur|j|
@F diverser Zugang|n||j
@F diverser Abgang|j||n
@F divlgbart_cd|char(3)|p1
@F divlgbart_mc|char(20)||für DDDW
@F abgang_jn|char(1)||Lagerabgang je charge_geraet erlaubt / bei 'n' muß gelten: / für jeden Wert von charge_geraet muß gelten: / Summe über alle Zeilen mit diesem Wert >= 0
@F zugang_jn|char(1)||Lagerzugang je charge_geraet erlaubt / bei 'n' muß gelten: / für jeden Wert von charge_geraet muß gelten: / Summe über alle Zeilen mit diesem Wert <= 0
@F chargen_korr_jn|char(1)||Buchungsart ist Chargenkorrektur / abgang_jn und zugang_jn sind bei Chargenkorrektur fix "j"
@F nr_kreis|char(10)||Nummernkreis für die Vergabe der Belegnummer
@F verb_mg_ftr|smallint(1)||Mengenfaktor Verbrauch (0, -1) / siehe auch divlgb / ist abweichend zu auf_pos negativ, da Abgänge in kartei_lagbew negativ
@F protokoll_jn|char(1)||Protokolldruck soll erzeugt werden
@F divlgb_txt_cd|char(10)||EndTextbaustein für Protokoll
@E
@T dn
@D Datanorm / es gibt einen nicht sichtbaren Satz mit dn_cd = "-", diesem sind alle Kunden zugeordnet, die keine Datanorm erhalten
@F dn_cd|char(3)|p1
@F fa_nr|smallint|p2,f
@F dn_mc|char(20)||Matchcode
@F dn_restart_jn|char(1)|
@F ltz_lfd_nr|smallint(3)|g|Laufende Nummer der letzten Ausgabe
@E
@T dn_artik
@D Datanorm Artikelstamm
@F dn_cd|char(3)|p1
@F fa_nr|smallint|p2
@F artik_cd|char(15)|p3|Stellen 1-15 der Artikelnummer / Es werden nur Normalartikel verwendet
@F verarb_kz|char(1)||Verarbeitungskennzeichen / n = Neuanlage / a = Änderung / l = Löschen / o = Ok, keine Ausgabe notwendig
@F kurz_txt1|varchar(40)||siehe fa.dn_txt_kz
@F kurz_txt2|varchar(40)|
@F eh_txt|char(4)||Mengeneinheit des Preises / lt. artik. vkpr_keh_veh_kz in Sprache "dn"
@F preis_kz|char(1)||Preiskennzeichen / 1 = Listenpreis (Standard) / 9 = Preis auf Anfrage / Wird verwendet, wenn der Artikel keinen Standard Verkaufspeis hinterlegt hat
@F vkpr_pro_mg|decimal(4,0)||Preiseinheit lt. Artikelstamm
@F vkpr|decimal(12,3)||Lt. fa.dn_preisli_cd, menge = 1und Datum lt. Auswahlparameter
@F rabgr|char(4)||Rabattgruppe / artikvkkondgr_cd
@F hptwg|char(3)||Hauptwarengruppe / muss in Ableitung bestimmt werden / ist in TradeControl fix "xyz"
@F wg|varchar(10)||Warengruppe / ""
@F artik_mc|varchar(15)||Stelle 1-15 von artik.artik_mc
@F alternartik_kz|varchar(13)||Kürzel für den Ersteller einer Alternativartikelnummer / ""
@F alternartik_nr|varchar(15)||Alternativartikelnummer / ""
@F herstartik_kz|varchar(13)||Kürzel für den Ersteller der Herstellernummer / "" / kann ggf. Lieferantenkürzel sein
@F herstartik_nr|varchar(35)||Herstellerartikelnummer / "" / kann ggf. Lieferantenartikelnummer sein
@F hersttype|varchar(35)||Herstellertype / "" / kann ggf. Lieferantenartikelnummer sein
@F ean_nr|varchar(18)||EAN Nummer / Min aus artikid mit artikid_kz = "e" und menge = artik.keh_veh_mg
@F anbind_nr|varchar(15)||Anbindenummer für Grafik (leer)
@F mindverp_mg|integer(5)||Mindestverpackungsmenge / = artik.keh_veh_mg wenn der Preis in kleinster Einheit ausgegeben wird, ansonsten 1
@F katalogseite|varchar(15)||Katalogseite (leer)
@F text_kz|smallint(1)||Textkennzeichen (=0)
@F langtxt_nr|varchar(15)||Langtextnummer (leer)
@F kostenart|smallint(2) +n||Kostenart (Null)
@F lagermerker|smallint(1) +n||Lagermerker (Null)
@F refnr_kz|varchar(13)||Kürzel für den Ersteller der Referenznummer
@F refnr|varchar(17)||Referenznummer
@F dn_ust_kz|char(1) +n||Mehrwertsteuerkennzeichen (lt. ust)
@E
@T dn_preis
@D Datanorm Preise
@F kunde_cd|char(10)|p1
@F fa_nr|smallint|p2
@F artik_cd|char(15)|p3|Artikelnummer / Es werden nur Normalartikel verwendet
@F verarb_kz|char(1)||Verarbeitungskennzeichen / a = Änderung / o = Ok, keine Ausgabe notwendig / Es gibt in der DATANORM 5.0 kein Löschen für bereits übermittelte Preisdaten. D.h. wurde für einen Kunden einmal ein Sonderpreis übermittelt, so muss, wenn dieser wieder gelöscht wird, ab diesem Zeitpunkt immer der Artikelpreis als Sonderpreis übermittelt werden.
@F vkpr_pro_mg|decimal(4,0)||Preiseinheit lt. Artikelstamm
@F vkp|decimal(11,2)||Nettoverkaufspreis bei verarb_kz = "a", Listenpreis bei vkp = "l"
@E
@T dn_rab
@D Datanorm Rabattgruppen
@F kunde_cd|char(10)|p1
@F fa_nr|smallint|p2
@F rabgr|char(4)|p3|Rabattgruppe
@F rabgr_bez|char(40)||Bezeichnung
@F rabgr_kz|char(1)||1 = Rabattsatz / 2 = Multiplikator
@F rab|decimal(5,3)||Rabatt bzw. Multiplikator / wenn Rabatt 2. NK gerundet
@E
@T dn_wgr
@D Datanorm Warengruppen
@F hptwg|char(3)|p1|Hauptwarengruppe
@F wg|char(10)|p2|Warengruppe
@F fa_nr|smallint|p3
@F wg_bez|char(40)||Bezeichnung / wg="", Bezeichnung der Hauptwarengruppe
@E
@T duestgrp
@D Durchschnittspreisgruppen / es gibt einen Dummy-Satz mit duestgrp_cd=""
@F duestgrp_cd|char(10)|p1
@F duestgrp_mc|char(30)|
@E
@T eh
@D Einheiten / Bei der Neuanlage in der Verwaltung sollte ein Satz für "d" in der Tabelle eh_sprache angelegt werden.
@F eh_upid|bigint +n|
@F eh_cd|char(5)|p1|Einheitencode
@E
@T eh_fremdsys
@D Einheiten – Umschlüsselungstabelle für Fremdsysteme
@F eh_cd|char(5)|p1,f|Einheitencode
@F fremdsys_kz|char(5)|p2|Fremdsystem KZ / mage = Magento WebShop / Kann in Ableitungen jederzeit erweitert werden
@F fremdsys_eh_txt|char(5)|p3|Einheitenkürzel in der jeweiligen Sprache für den Druck auf Belegen
@F exp_hpt_jn|char(1)||Haupt Einheitscode für Export / Es darf nur einen Haupt Export pro eh_cd und Fremdsystem geben
@F imp_hpt_jn|char(1)||Haupt Einheitscode für Imprt / Es darf nur einen Haupt Import pro frmdsys_kz und fremdsys_eh_txt geben
@E
@T eh_sprache
@D Einheiten – Sprachen
@F eh_cd|char(5)|p1,f|Einheitencode
@F sprache_cd|char(5)|p2,f|Sprachencode
@F druck_eh_txt|char(5)||Einheitenkürzel in der jeweiligen Sprache für den Druck auf Belegen
@E
@T elfs
@D Eingangslieferschein
@F elfs_nr|integer(7)|p1|Warenzugangsnummer / Vergabe/Kontrolle mittels Tabelle nummern
@F fa_nr|smallint(3)|p2|Firma
@F fil_nr|smallint(3)|f|Filiale
@F elfs_beleg_nr|char(20)|n|Lieferscheinnummer des Lieferanten
@F elfs_beleg_dat|date|n|Lieferscheindatum
@F waehrung_cd|char(4)|f,n|Währung des Lieferscheins / Vorschlag Neuanlage lt. Tabelle lief / darf bei der Erfassung geändert werden / erhält bei der 1. Eingangsrechnung den endgültigen Wert
@F lief_cd|char(10)|f,n|Lieferantennummer
@F lief_name1|char(50)||Anschrift des Lieferanten
@F lief_name2|char(50)|
@F lief_name3|char(50)|
@F lief_name4|char(50)|
@F lief_strasse|char(50)|
@F lief_land_cd|char(3)|f
@F lief_plz|char(10)|
@F lief_ort|char(50)|
@F versart_cd|char(5)|f|Versandart lt. Tabelle lief für Retoure
@F elfs_fa_pers_cd|char(5)|ng|Sachbearbeiter der eigenen Firma, welcher Zugang gebucht hat / Wird bei AVISO Zubuchen aktualisiert.
@F elfs_zustand_kz|char(1)|n|a|Aviso (noch nicht auf Lager gebucht)
@F elfs_zustand_kz|char(1)|n|e|erfasst / Lager gebucht
@F elfs_zustand_kz|char(1)|n|t|teilweise verrechnet
@F elfs_zustand_kz|char(1)|n|v|vollständig verrechnet
@F elfs_dat|date +n|n|Datum zu dem Eingangslieferschein gebucht wurde. Warenzugangsdatum. / Bleibt bei einem Lieferaviso bei der Erfassung leer und kann manuell geändert werden, bis das Lieferaviso auf Lager gebucht wird. / Falls es dann noch immer nicht ausgefüllt ist, wird das aktuelle Datum verwendet. / Darf nicht in der Zukunft liege, darf nicht mehr als x Tage in der Vergangenheit liegen (Absicherung über pfu_col).
@F erl_elfs_nr|integer|r|0, wenn Lieferschein noch nicht fakturierte Positionen hat, sonst = elfs_nr siehe dazu elfs_zustand_kz = 'v'
@F default_lag_cd|char(11)|f|Defaultlager für die Eingangslieferscheinpositionen / Vorschlag lt. fa bzw. adr_pers_fa
@F ao_snr|integer||AO-Snr / ist eindeutig / dient zum Finden eines AOs
@F elfs_barcode|char(13)||Barcode für Dokumentenarchiv / kann im Eingangslieferscheinfenster eingegeben werden, wenn [archiv. beleg_kz = "el"] vorhanden ist, / sonst fix ""
@F elfsn_datz|date|ng|Erfassungsdatum des Datensatzes [dd.mm.yyyy hh:mm:ss] / Erstbelegung: [elfs_dat] 00:00:00
@F lief_upid|bigint +n||ID der Lieferanten
@F elfsmde_upid|bigint +n||ID des MDE Warenzugangs / 0 = keine MDE Warenzugang
@F elfs_upid|bigint +n||ID
@F mde_zustand_kz|char(1)||MDE Zustandskennzeichen / "0" – Nicht freigegeben / Keine MDE Warenzugang / "1" – Freigegeben für MDE Warenzugang / Kann nur für Eingangslieferscheine im Zustand Aviso aktiviert werden / "3" – MDE Warenzugang begonnen / "5" – MDE Warenzugang abgeschlossen / "9" – MDE Warenzugang mit Fehler/Differenzen abgeschlossen
@F mde_zuweis_jn|char(1)||Eingangslieferschein wurde im MDE Warenzugang ausgewählt (= mde_zustand_kz > 1)
@F default_lag_upid|bigint +n||ID des Default Lagers
@E
@I index i1_elfs (erl_elfs_nr, lief_cd, fa_nr)
@I index i2_elfs (elfs_beleg_nr)
@I index i3_elfs (elfs_beleg_dat)
@I index i4_elfs (ao_snr)
@I index i5_elfs (elfs_upid)
@T elfs_txt
@D Eingangslieferschein- Textzeilen für Lieferantenretoure
@F elfs_nr|integer(7)|p1
@F fa_nr|smallint(3)|p2,f
@F txt_typ_kz|char(1)|p3|Texttyp / "r" Richtext / wenn [param.appl_txt_kz <> "p"] / Standardfont "Arial 10" / "p" Plaintext / wenn [param.appl_txt_kz = "p"]
@F zeile_nr|smallint|p4|Zeilennummer
@F wo_kz|char(1)||'a' = Anfang / 'e' = Ende
@F fett_jn|char(1)||fett drucken / fix "n", wenn [txt_typ_kz = "r"]
@F unterstrichen_jn|char(1)||unterstrichen drucken / fix "n", wenn [txt_typ_kz = "r"]
@F elfs_txt|varchar(max)||Lieferantenretourschein Textzeile / generierter Plaintext (elfs_rtxt) , wenn [txt_typ_kz = "r"] / eingegebener Text, sonst
@F elfs_txt_dbid|integer identity||ROWID für Retrieve Richtext / durch DB-Default mit serieller Nummer belegt
@F elfs_rtxt|varbinary(max)||Eingangslieferscheintext Richtext / wenn [txt_typ_kz = "p"], durch DB-Default mit Leerstring belegt
@E
@I unique index i1_elfs_txt (elfs_txt_dbid)
@T elfs_pos
@D Eingangslieferscheinposition / alle Mengen in elfs_pos.eeh_cd Menge in kleinster Einheit = lief_mg * elfs_pos.keh_eeh_mg
@F elfs_nr|integer(7)|p1,f
@F fa_nr|smallint(3)|p2
@F elfs_pos_nr|smallint(4)|p3
@F artik_cd|char(20)|f|artik.artik_kz in ('n', 'd', 'p')
@F artik_mc|char(40)||Artikelmatchcode
@F gar_mo_ek|smallint(3)||Garantiemonate Einkauf
@F eeh_cd|char(5)|f,n|lt. artik_lief bzw. best_pos
@F keh_eeh_mg|decimal(9,3)|n
@F ekpr_keh_eeh_kz|char(1)||siehe s_ekpr / bei Änderung wird ekpr_ftr und daher auch s_ekpr neu ermittelt
@F ekpr_pro_mg|decimal(4,0)||siehe s_ekpr / bei Änderung wird ekpr_ftr und daher auch s_ekpr neu ermittelt
@F ekpr_ftr|decimal(13,7)||siehe s_ekpr / bei Änderung wird ekpr_ftr und daher auch s_ekpr neu ermittelt
@F lief_mg|decimal(12,3)|n|gelieferte Menge
@F elfs_pos_info|char(255) +n||Interner Infotext
@F kartei_snr|integer|ng|-1 Lieferavisoposition, die noch nicht gebucht wurde. / 0 keine Lagerbewegung / > 0 Verweis auf die zugehörigen Lagerbewegungen (eine oder mehrere Rows in kartei_lagbew)
@F elfs_lag_ftr|smallint(1)|n|Lagerbewegungsfaktor (0, 1) / wird bei der Neuanlage durch Lagerführungskennzeichen Artikel [artik.lagfuehr_kz] bestimmt / kann ev. in Ableitung mit Berechtigung verändert werden
@N Felder für Rechnung: / sind bis zum Eintrag der erech_nr nicht endgültig
@F s_fakt_mg|decimal(12,3)||fakturierte Menge Soll / default lt. lief_mg
@F i_fakt_mg|decimal(12,3)||fakturierte Menge Ist / lt. ER-Beleg / bei der Neuanlage 0 / wird im Zuge des INSERT ins DW der Eingangsrechnung mit s_fakt_mg belegt / wird bei jeder Änderung von s_fakt_mg mitgeändert, wenn Fibu nicht verbucht
@F s_ekpr|decimal(12,3) +n||Einkaufspreis Soll / default lt. elfs_pos_best where zeile_nr = 1 umgerechnet auf elfs.waehrung_cd unter Berücksichtigung von ekpr_ftr, falls vorhanden / default lt. artik_lief_ekpr umgerechnet auf elfs.waehrung_cd unter Berücksichtigung von ekpr_ftr, falls vorhanden und elfs_pos_best nicht vorhanden / wird im Zuge der ER-Kontrolle auf erech.waehrung_cd umgerechnet / kann übersteuert werden
@F i_ekpr|decimal(12,3) +n||Einkaufspreis Ist / lt. ER-Beleg / bei der Neuanlage NULL / wird im Zuge des INSERT ins DW der Eingangsrechnung mit neu ermitteltem s_ekpr belegt / wird bei jeder Änderung von s_ekpr mitgeändert, wenn Fibu nicht verbucht
@F s_ekrab1|decimal(4,2)||Rabatt 1 Soll / siehe s_ekpr
@F i_ekrab1|decimal(4,2)||Rabatt 1 Ist / Logik entspricht i_fakt_mg
@F s_ekrab2|decimal(4,2)||Rabatt 2 Soll / siehe s_ekpr
@F i_ekrab2|decimal(4,2)||Rabatt 2 Ist / Logik entspricht i_fakt_mg
@F s_ekrab3|decimal(4,2)||Rabatt 3 Soll / siehe s_ekpr
@F i_ekrab3|decimal(4,2)||Rabatt 3 Ist / Logik entspricht i_fakt_mg
@F s_ekrab4|decimal(4,2)||Rabatt 4 Soll / siehe s_ekpr
@F i_ekrab4|decimal(4,2)||Rabatt 4 Ist / Logik entspricht i_fakt_mg
@F s_ekrab5|decimal(4,2)||Rabatt 5 Soll / siehe s_ekpr
@F i_ekrab5|decimal(4,2)||Rabatt 5 Ist / Logik entspricht i_fakt_mg
@F aufw_prz1|decimal(4,2)|g|1. Aufwertungsprozentsatz für Einstandspreis lt. artik_lief
@F aufw_prz2|decimal(4,2)|g|2. Aufwertungsprozentsatz für Einstandspreis lt. artik_lief
@F aufw_bet1|decimal(11,2)|g|1. Aufwertungsbetrag für Einstandspreis lt. artik_lief
@F aufw_bet2|decimal(11,2)|g|2. Aufwertungsbetrag für Einstandspreis lt. artik_lief
@F erech_nr|integer(7)|f,g|Interne Eingangsrechnungsnummer / 0 = noch keiner erech zugeordnet / wenn <> 0 mus erech noch nicht verbucht sein
@F veh_estpr|decimal(15,6)|r|Einstandspreis in GW und pro Lagereinheit/Verkaufseinheit
@F veh_ekpr|decimal(15,6)|r|Einkaufspreis in GW und pro Lagereinheit/Verkaufseinheit / Die Rabatte sind bereits abgezogen
@F veh_lief_mg|decimal(12,3)|r|gelieferte Menge in Lagereinheit/Verkaufseinheit
@F ek_wert|decimal(11,2)|r|Einkaufswert in GW / (veh_ekpr * veh_lief_mg) - s_ekrab%, wenn ER in Wawi und Fibu verbucht / ist bei der Neuanlage 0
@F est_wert|decimal(11,2)|r|Einstandswert in GW / veh_estpr * veh_lief_mg, wenn ER in Wawi und Fibu verbucht / ist bei der Neuanlage 0
@F lief_cd|char(10)|r|Lieferant lt. elfs
@F erech_mon|char(6)|r|wird bei der Neuanlage mit blank belegt / wird bei der Wawi-Verbuchung der erech mit "0" belegt, bzw. mit erech_buper wenn fibumäßig bereits verbucht wurde, oder nie fibumäßig verbucht wird / wird bei der Fibu-Verbuchung mit Monat lt. erech_buper belegt, sofern Wawi bereits verbucht ist
@F stat_gebucht_jn|char(1)||Statistik ist gebucht / ist bei der Neuanlage 'n' / wird durch das Statistikaufbauprogramm auf 'j' umgesetzt
@F ao_snr|integer||AO-Snr / ist eindeutig / dient zum Finden eines AOs
@F preis_manu_jn|char(1)||Preis oder Rabatte der Bestell-/Eingangslieferscheinposition wurden manuell übersteuert
@F mde_elp_jn|char(1)||Position wurde über einen MDE-Warenzugang bebucht / Bei der ersten MDE Warenzugangs Zuordnung werden zuvor vorhandene elfs_pos_aviso Zeilen gelöscht / Bei einer MDE Position wird die elfs_pos_aviso Zeile nicht mehr automatisch mit der gelieferten Menge syncronisiert
@F is_mon|char(6) +n||INTRASTAT Monat / Wird bei der Ausgabe INTRASTAT Daten belegt
@E
@I index i1_elfs_pos (erech_nr, artik_cd, fa_nr)
@I index i2_elfs_pos (lief_cd, fa_nr, erech_nr)
@I index i3_elfs_pos (kartei_snr)
@I index i4_elfs_pos (erech_mon, artik_cd, fa_nr)
@I index i5_elfs_pos (ao_snr)
@I index i6_elfs_pos (is_mon, fa_nr)
@T elfs_pos_aviso
@D Eingangslieferschein- Position- AVISO Daten / Dient zum Erfassen von Lager/Chargen und Gerätedaten für Lieferavisos die noch nicht auf Lager gebucht sind.
@F elfs_nr|integer(7)|p1
@F elfs_pos_nr|smallint(4)|p2,f
@F fa_nr|smallint(3)|p3
@F zeile_nr|smallint|p4,g|Laufende Zeilennummer
@F lag_cd|char(11)|
@F lag_ort|varchar(20)||Lagerort siehe lag.lag_ort_inp_jn
@F charge_geraet|varchar(40)||Leer, Gerätenummer oder Chargennummer, siehe artik_lag_sub
@F bew_mg|decimal(11,3)||bewegte Menge in Lagereinheit (Minus ist Abgang)
@F ablauf_dat|date +n||Ablaufdatum bei artik.lagfuehr_kz = 'c' und artik.ablaufdat_jn = 'j', / sonst NULL
@F geraet_cd|varchar(40)|
@E
@T elfs_pos_best
@D Eingangslieferschein- Position- Bestellungen (gn)
@F elfs_nr|integer(7)|p1
@F elfs_pos_nr|smallint(4)|p2,f
@F fa_nr|smallint(3)|p3
@F best_nr|integer(7)|p4
@F best_pos_nr|smallint(4)|p5,f
@F teil_lief_mg|decimal(12,3)||gelieferte Menge in Einkaufsmengeneinheit lt. elfs_pos
@F zeile_nr|smallint||Laufende Nummer je Lieferscheinposition (DW-Reihenfolge)
@E
@I unique index I1_elfs_pos_best (elfs_nr, elfs_pos_nr, fa_nr, zeile_nr)
@I index I2_elfs_pos_best (best_nr, best_pos_nr)
@T elfs_pos_txt
@D Eingangslieferschein- Textzeilen mit Artikelbezeichnung / für Lieferantenretoure und/oder Belastungsnote /  / wenn artik_kz <> 'd' / Wird bei der elfs_pos-Neuanlage aus artik_txt vorbelegt, wobei Rows berücksichtig werden für die gilt: / sprache_cd = adr.sprache_cd and lief.lief_adr_snr = adr.adr_snr and best_jn = 'j' /  / wenn artik_kz = 'd' / Wird bei der elfs_pos-Neuanlage mit Bestellbezug aus best_pos_txt sonst, aus artik.artik_mc vorbelegt
@F elfs_nr|integer(7)|p1
@F fa_nr|smallint(3)|p2
@F elfs_pos_nr|smallint(4)|p3,f
@F txt_typ_kz|char(1)|p4|Texttyp / "r" Richtext / wenn [param.appl_txt_kz = "r"] / Standardfont und -größe lt. Parameter / "p" Plaintext / wenn [param.appl_txt_kz <> "r"]
@F zeile_nr|smallint|p5|Zeilennummer
@F fett_jn|char(1)||fett drucken / fix "n", wenn [txt_typ_kz = "r"]
@F unterstrichen_jn|char(1)||unterstrichen drucken / fix "n", wenn [txt_typ_kz = "r"]
@F elfs_pos_txt|varchar(max)||Positionstext- Zeile / generierter Plaintext (elfs_pos_rtxt), wenn [txt_typ_kz = "r"] / eingegebener Text, sonst
@F elfs_pos_txt_kz|char(1)|ng|'a' = automatisch aus artik_txt bzw. best_pos.artik_mc generiert / 'm' = manuell erfasst
@F elfs_pos_txt_dbid|integer identity||ROWID für Retrieve Richtext / durch DB-Default mit serieller Nummer belegt
@F elfs_pos_rtxt|varbinary(max)||Eingangslieferscheinpositionstext Richtext / wenn [txt_typ_kz = "p"], durch DB-Default mit Leerstring belegt
@E
@I unique index i1_elfs_pos_txt (elfs_pos_txt_dbid)
@T elfsmde
@D Eingangslieferschein MDE Warenzugang / ist ein View auf gdo.MdeWarenzugang
@F elfsmde_upid|bigint (p)|
@F fa_upid|bigint|
@F lag_upid|bigint||Es können nur Eingangslieferscheine verwendet werden, die dieses Lager als Defaultlager haben.
@F start_datz|datetime||Zeitpunkt der Erstellung
@F fertig_datz|datetime +n||Zeitpunkt der Fertigstellung
@F elfsmde_zustand_kz|char(1)||Zustandskennzeichen / "b" – Begonnen / "v" - vollständig erfasst (ohne Fehler) / "f" – Fehlerhaft abgeschlossen
@F lief_upid|bigint|
@E
@T elfsmde_pos
@D Eingangslieferschein MDE Warenzugang / ist ein View auf gdo.MdeWarenzugangPosition
@F elfsmde_pos_upid|bigint (p)|
@F elfsmde_upid|bigint|
@F lag_ort|char(20)||Lagerort
@F charge_geraet|char(40)||Chargen Gerätenummer / ACHTUNG in Standard noch nicht umgesezt
@F artik_upid|bigint|
@F erf_mg|decimal(12,3)||Erfasste Menge in Lagereinheit
@F artik_cd|char(20)|
@F fa_nr|smallint|
@F herst_dat|date +n||Herstellungdatum aus EAN128
@F mhd_dat|date +n||Mindesthaltberkeitsdatum aus EAN128
@F ablauf_dat|date +n||Ablaufdatum/Verfallsdatum aus EAN128
@F mde_person|varchar(20)||MDE Sachbearbeiter
@F mde_erf_datz|datetime||Zeitpunkt schreiben dieses Satzes
@F erl_job_snr|bigint||Datensatz in TC verbucht / 0 = noch nicht verbucht / >0 – Jobnummer mit der die Daten in die Eingangslieferscheinpostion übernommen wurden / -1 = Fehler bei der Verbuchung aufgetreten
@E
@I index i1_elfsmde_pos (erl_job_snr)
@T entsorger
@D Packstoff-Entsorger / es gibt einen Dummy-Entsorger " "
@F entsorger_cd|char(10)|p1
@F entsorger_mc|char(30)||Ensorgerbezeichnung
@F linzenz_nr|char(20)||Lizenznummer
@E
@T eragrp
@D ERA-Gruppen / es gibt eine Dummy-Gruppe " "
@F eragrp_cd|char(10)|p1
@F eragrp_txt|char(60)||ERA-Gruppenbezeichnung
@F hptgrp_kz|char(1)||Hauptgruppe Haushalt(1)/Gewerbe(2)
@E
@T eragrp_preis
@D ERA: Tarife.
@F eragrp_cd|char(10)|p1,f
@F ab_dat|date|p2|Datum gültig ab
@F bis_dat|date||Datum gültig bis: / Keine Eingabe im Verwaltungsprogramm / wird auf DATMAX
@F tarif|decimal(11,3)||ERA-tarif je kg / in Grundwährung
@E
@T erech
@D Eingangsrechnung
@N Es muß eine Row mit erech_nr = 0 für "noch nicht verrechnet" geben. / Die Column- Werte dieser Row sind bei den einzelnen Columns unter (0: beschrieben.
@F erech_nr|integer(7)|p1
@F fa_nr|smallint(3)|p2,f|Firmennummer (0: 1)
@F lief_cd|char(10)|f,n|Lieferantennummer (0: irgend ein Pseudolieferant)
@F kreditor_nr|integer(9)||Kreditorennummer (0:0) / Vorschlag lt. Lieferant / kann mit Berechtigung übersteuert werden
@F liefsach_cd|char(10)|f|Zuordnung Bestands/Wareneinsatzkonten (0: " ") / bestimmt auch Inland/Eu/Drittland / Vorschlag lt. Lieferant, kann mit Berechtigung übersteuert werden
@F erechart_cd|char(1) (p)||Eingangsrechnungsart / "e" Eingangsrechnung / "b" Belastungsanzeige / "s" StornoEr
@F waehrung_cd|char(4)|f,n|Währung für Rechnung / Default lt. Kreditor / darf übersteuert werden
@F erech_beleg_nr|char(20)||Eingangsrechnungsnummer des Lieferanten (0:' ') / darf bei Jetfibu maximal 8stellig numerisch
@F erech_beleg_dat|date||Rechnungsdatum des Lieferanten (0: "9.9.9999")
@F erech_buper|char(6)||Buchungsperiode im Format JJJJMM / default lt. erech_beleg_dat / muß zwischen fa.min_erech_buper und fa.max_erech_buper liegen
@F s_erech_zuab_we|decimal(11,2)||Wertmäßiger Rechnungs- Zu/Abschlag in Belegwährung Soll (0: 0)
@F i_erech_zuab_we|decimal(11,2)||Wertmäßiger Rechnungs- Zu/Abschlag in Belegwährung Ist (0: 0)
@F erech_dzuab_prz|decimal(4,2)||Prozentmäßiger Rechnungs- Zu/Abschlag nur duest (0: 0)
@F erech_dzuab_we|decimal(7,2)||Wertmäßiger Rechnungs- Zu/Abschlag in Belegwährung nur duest (0: 0)
@F skonto1_prz|decimal(4,2)||1. Skontoprozentsatz (0:0)
@F skonto1_tg|smallint(2)||dazu Ziel- Tage (0:0)
@F skonto2_prz|decimal(4,2)||2. Skontoprozentsatz (0:0)
@F skonto2_tg|smallint(2)||dazu Ziel- Tage (0:0)
@F netto_tg|smallint(2)||Ziel- Tage für Netto- Zahlung (0:0)
@F valuta_dat|date +n||Valutadatum
@F erech_dat|date +n||Erfassungsdatum (0: "9.9.9999")
@F erech_info|char(255) +n||Informationstext intern
@F dabge_erech_nr|integer|g|Rechnung ist duestmäßig abgeschlossen dann erech_nr, sonst 0
@F fabge_erech_nr|integer|g|Rechnung ist fibumäßig abgeschlossen dann erech_nr, sonst 0
@F erech_mon|char(6)|r|entspricht elfs_pos.erech_mon
@F erech_fa_pers_cd|char(5)|ng|Sachbearbeiter der eigenen Firma, welcher Rechnung gebucht hat
@F erech_elfs_we|decimal(11,2)||entspricht dem errechneten Netto-Ist-Wert aller Eingangslieferscheinpositionen / dient zur Prüfung der Toleranzgrenze bei der manuellen Änderung der Kontierung / in Belegwährung
@F erech_bn_kz|char(2)||Belastungsnote wird erstellt / "ff" mit Fibuverbuchung (fix) / "fv" mit vollständiger Verbuchung WaWi und Fibu (fix) / "fn" niemals (fix) / "vf" mit Fibuverbuchung (Vorschlag) / "vv" mit vollständiger Verbuchung WaWi und Fibu (Vorschlag) / "vn" niemals (Vorschlag) / ist bei belastung_jn = "j" fix "fv" / kann geändert werden, wenn weder Fibu noch Wawi verbucht ist
@F zvksperre_jn|char(1)||gesperrt für Zahlungsverkehr / wird bei Integration der Jetfibu beim Speichern automatisch in fbbibkt bzw. fbop gesetzt / Vorschlag lt. erechart_fa / wird bei ungeprüfter Eingangsrechnung beim Wawi-Verbuchen auf "n" gesetzt
@F efbueb_job_nr|integer||Jobnummer des Fibuüberleitungsprogrammes / ist bei Neuanlage fix 0 wenn in Fibu übergeleitet wird bzw. -1 wenn nie in die Fibu übergeleitet wird / ist bei sofortiger integrierter Jetfibuverbuchung 1
@F ao_snr|integer||AO-Snr / ist eindeutig / dient zum Finden eines AOs
@F erech_barcode|char(13)||Barcode für Dokumentenarchiv / kann im Eingangsrechnungsfenster eingegeben werden, wenn [archiv. beleg_kz = "er"] vorhanden ist, / sonst fix ""
@F pruef_erech_nr|integer(7)||Rechnungsnummer für gemeinsame Prüfung der Rechnungsendsumme
@F erechn_datz|date|ng|Erfassungsdatum des Datensatzes [dd.mm.yyyy hh:mm:ss] / durch DB-Default (CURRENT) belegt / Erstbelegung: [erech_dat] 00:00:00
@F bez_erech_nr|integer(7)||Bezugsrechnungsnummer für Belegart ER-Storno
@F er_ewpfand_jn|Char(1)||Einwegpfand ermittelt als Zuab, kommt von Lief, standard rechts draussen
@F erech_pdf_kz|char(1)||KZ Dokumentenstatus für DATEV Export / Kann bei FIBU Exporten mit Übergabe der Belege verwendet werden um den Eport zurückzuhalten bis der Beleg vorhanden ist. / f = Fehlt noch (Defautl bei Neuanlage) / v = Vorhanden / Wird vom TC-Scann Import oder wenn die Belastungsnote von TC gedruckt wird oder wenn ein PDF mit Drag&Drop der ER zugeordnet wird gesetzt. / k = Kein PDF (kann manuell gesetzt werden)
@F erech_status_kz|char(1)||Status der Eingangsrechnung / e = Erfasst / f = FIBU gebucht / w = WAWI gebucht / g = vollständig gebucht / x = Storniert (über Menüpunkt erledigt setzen)
@F dabge_datz|datetime +n|g|Zeitpunkt zu dem die Rechnung in Wawi Verbuchucht wurde
@F fabge_datz|dateteim +n|g|Zeitpunkt zu dem die Rechnung in FIBU gebucht wurde
@E
@I index i1_erech ( lief_cd, erech_beleg_nr, fa_nr )
@I index i2_erech (dabge_erech_nr, lief_cd)
@I index i3_erech (fabge_erech_nr, lief_cd)
@I index i4_erech (ao_snr)
@I index i5_erech (pruef_erech_nr, fa_nr)
@T erech_bn
@D Eingangsrechnung Belastungsnote (gn)
@F erech_nr|integer(7)|p1
@F fa_nr|smallint(3)|p2,f
@F erech_bn_nr|integer(7)||Belegnummer Belastung / Vergabe mittels Tabelle nummern
@F erech_bn_dat|date||Belegdatum
@F erech_bn_betr|decimal(11,2)||Belastungsnotenbetrag (=Summe Ust- Basen)
@F ebnfbueb_job_nr|integer||Jobnummer des Fibuüberleitungsprogrammes / ist bei Neuanlage fix 0 wenn in Fibu übergeleitet wird bzw. -1 wenn nie in die Fibu übergeleitet wird / ist bei sofortiger integrierter Jetfibuverbuchung 1
@F erech_bn_barcode|char(13)||Barcode für Dokumentenarchiv
@E
@T erech_elfs
@D Eingangsrechnung- Lieferschein
@F erech_nr|integer(7)|p1,f
@F fa_nr|smallint(3)|p2
@F elfs_nr|integer(7)|p3,f
@F s_erechl_zuab_we|decimal(11,2)||Wertmäßiger Rechnungs- Zu/Abschlag in Belegwährung Soll
@F i_erechl_zuab_we|decimal(11,2)||Wertmäßiger Rechnungs- Zu/Abschlag in Belegwährung Ist
@F erechl_dzuab_prz|decimal(4,2)||Prozentmäßiger Rechnungs- Zu/Abschlag nur duest
@F erechl_dzuab_we|decimal(7,2)||Wertmäßiger Rechnungs- Zu/Abschlag in Belegwährung nur duest
@E
@I index i1_erech_elfs (elfs_nr, fa_nr, erech_nr)
@T erech_kont
@D Eingangsrechnung- Kontierungszeilen für Fibubuchung
@F erech_nr|integer(7)|p1,f
@F fa_nr|smallint(3)|p2
@F zeile_nr|smallint|p3|Zeile im DW
@F ust_cd|char(10)|f|Ustcode
@F kto_nr|integer(9)||Sachkontennummer
@F kst_nr|integer(9)||Kostenstellennummer
@F koart_nr|integer(9)||Kostenartnummer
@F ktr_nr|integer(9)||Kostenträgernummer
@F ust_prz|decimal(4,2)||Ust- Prozentsatz
@F ust_basis|decimal(11,2)||Ust- Basis / wird bei den Rechnungsarten "Eingangsrechnung" und "Belastungsanzeige" bei Änderung der ElfsPos-IstWerte neu berechnet / wird bei Rechnungsart "ungeprüfte Eingangsrechnung" manuell eingegeben
@F ust_basis_elfs|decimal(11,2)||Ust-Basis aus Istwerten der [elfs_pos] und [erech_zuab] berechnet / kann durch User nicht verändert werden / wird bei allen Rechnungsarten bei Änderung der ElfsPos-IstWerte neu bestimmt
@F ust_betr|decimal(11,2)||Ust- Betrag / siehe ust_basis
@F buch_txt|char(25)||Buchungstext für Jetfibu
@F ust_basis_belast|decimal(11,2)||Ust- Basis f. Belastungsnote / (Differenz zwischen Soll u. Ist)
@E
@T erech_stornopos
@D Eingangslieferscheinpositionen, die storniert wurden / nur bei Rechnungen mit Rechnungsart "storno" / alle Felder lt. [elfs_pos] / kein LookUp
@F erech_nr|integer(9)|p1,f
@F fa_nr|smallint(3)|p2
@F zug_elfs_nr|integer(9)|p3
@F zug_fa_nr|smallint(3)|p4
@F zug_elfs_pos_nr|smallint(4)|p5,f
@F artik_cd|char(20)|
@F artik_mc|char(60)|
@F eeh_cd|char(5)|f
@F keh_eeh_mg|decimal(9,3)|
@F ekpr_pro_mg|decimal(4,0)|
@F ekpr_keh_eeh_kz|char(1)|
@F ekpr_ftr|decimal(13,7)|
@F lief_mg|decimal(12,3)||{vorzeichengedreht}
@F s_fakt_mg|decimal(12,3)||{vorzeichengedreht}
@F i_fakt_mg|decimal(12,3)||{vorzeichengedreht}
@F s_ekpr|decimal(12,3) +n|
@F i_ekpr|decimal(12,3) +n|
@F s_ekrab1|decimal(4,2)|
@F i_ekrab1|decimal(4,2)|
@F s_ekrab2|decimal(4,2)|
@F i_ekrab2|decimal(4,2)|
@F s_ekrab3|decimal(4,2)|
@F i_ekrab3|decimal(4,2)|
@F s_ekrab4|decimal(4,2)|
@F i_ekrab4|decimal(4,2)|
@F s_ekrab5|decimal(4,2)|
@F i_ekrab5|decimal(4,2)|
@F aufw_prz1|decimal(4,2)|g
@F aufw_prz2|decimal(4,2)|g
@F aufw_bet1|decimal(13,4)|g
@F aufw_bet2|decimal(13,4)|g
@F veh_estpr|decimal(15,6)|r
@F veh_ekpr|decimal(15,6)|r
@F ek_wert|decimal(11,2)|r|{vorzeichengedreht}
@F est_wert|decimal(11,2)|r|{vorzeichengedreht}
@F veh_lief_mg|decimal(12,3)||{vorzeichengedreht}
@F erech_mon|char(6)|r|wird bei der Neuanlage mit blank belegt / wird bei der Storno-Verbuchung mit erech_buper belegt
@F stat_gebucht_jn|char(1)||Statistik ist gebucht / ist bei der Neuanlage 'n' / wird durch das Statistikaufbauprogramm auf 'j' umgesetzt / Statistikaufbauprogramm verarbeitet Sätze mit [erech_mon] > ""
@F lief_cd|char(10)|
@E
@T erech_txt
@D Eingangsrechnung- Textzeilen für Belastungsnote
@F erech_nr|integer(7)|p1,f
@F fa_nr|smallint(3)|p2
@F txt_typ_kz|char(1)|p3|Texttyp / "r" Richtext / wenn [param.appl_txt_kz <> "p"] / Standardfont "Arial 10" / "p" Plaintext / wenn [param.appl_txt_kz = "p"]
@F zeile_nr|smallint|p4|Zeilennummer
@F wo_kz|char(1)||'a' = Anfang / 'e' = Ende
@F fett_jn|char(1)||fett drucken / fix "n", wenn [txt_typ_kz = "r"]
@F unterstrichen_jn|char(1)||unterstrichen drucken / fix "n", wenn [txt_typ_kz = "r"]
@F erech_txt|varchar(max)||Belastungsnote Textzeilen / Plaintext (erech_rtxt), wenn [txt_typ_kz = "r"] / eingegebener Text, sonst
@F erech_txt_dbid|integer identity||ROWID für Retrieve Richtext / durch DB-Default mit serieller Nummer belegt
@F erech_rtxt|varbinary(max)||Eingangsrechnungstext Richtext / wenn [txt_typ_kz = "p"], durch DB-Default mit Leerstring belegt
@E
@I unique index i1_erech_txt (erech_txt_dbid)
@T erech_ust
@D Eingangsrechnung- Ustzeilen
@F erech_nr|integer(7)|p1,f
@F fa_nr|smallint(3)|p2
@F ust_cd|char(10)|p3,f|Ustcode
@F ust_prz|decimal(4,2)||Ust- Prozentsatz
@F ust_basis|decimal(11,2)||Ust- Basis
@F ust_betr|decimal(11,2)||Ust- Betrag
@F sktofae_betr|decimal(11,2)||skontofähige Ust-Basis
@E
@T erech_zuab
@D Eingangsrechnung- Zu/Abschläge / wird nie über [LookUp] gelesen
@F erech_nr|integer(9)|p1,f
@F fa_nr|smallint(3)|p2|Firma
@F zeile_nr|smallint|p3|interne Zeilennummer
@F zuab_cd|char(10)|f|ZuabschlagCd
@F elfs_nr|integer (9)||Warenzugangsnummer für die der Zuabschlag gilt / 0=für die ganze Rechnung
@F s_erech_zuab_we|decimal(11,2)||wertmäßiger Rechnungs- Zu/Abschlag in Belegwährung Soll
@F i_erech_zuab_we|decimal(11,2)||wertmäßiger Rechnungs- Zu/Abschlag in Belegwährung Ist
@F ez_info_txt|char(80)||Infotext / freie Eingabe
@E
@T erechart
@D Eingangsrechnungsarten
@F erechart_cd|char(1) (p)||Eingangsrechnungsart / "e" Eingangsrechnung / "b" Belastungsanzeige / "u" ungeprüfte Eingangsrechnung / „s“ Storno ER
@F erechart_mc|char(20)||Matchcode
@F belastung_jn|char(1)||Rechnungsart ist eine Belastungsanzeige / keine Soll/Ist-Differenzen möglich / keine Buchung in erech_bn, gesamte Eingangsrechnung versteht sich als Belastungsnote
@F ungepr_erech_jn|char(1)||Rechnungsart ist eine ungeprüfte Eingangsrechnung
@F spalte|char(18)||Spalte für Vergabe Eingangsrechnungsnummer / "erech_nr" bzw. "erech_bn_nr"
@F nr_kreis|char(10)||Nummernkreis für Vergabe Eingangsrechnungsnummer
@E
@T erechart_fa
@D Eingangsrechnungsarten Firma / Datensatz muss vorhanden sein, damit erech angelegt werden kann
@F erechart_cd|char(1)|p1,f
@F fa_nr|smallint(3)|p2,f
@F bn_txt_cd|char(20)||Code des Textbausteines, der am Ende der Belastungsnote gedruckt wird
@F fb_er_sy|char(2)||Fibu Buchungssymbol Eingangsrechnung / wird bei Rechnungsverbuchung mit erechart.belastung_jn = "n" verwendet
@F fb_eg_sy|char(2)||Fibu Buchungssymbol Eingangsgutschrift / wird bei Rechnungsverbuchung mit erechart.belastung_jn = "n" verwendet
@F fb_bn_sy|char(2)||Fibu Buchungssymbol Belastungsnote / wird bei Rechnungsverbuchung mit erechart.belastung_jn = "j", bzw. beim Verbuchen der Belastung verwendet / "" keine Fibuverbuchung der Belastungsnote
@F erech_fb_kz|char(1)||'-' keine Überleitung in die FIBU / 'b' Bestandskonto (ohne Kostenstelle) an Kreditor / 'a' Aufwandskonto (ev. mit Kostenstelle) an Kreditor
@F erech_belnr_kz|char(1)||Belegnummer in Fibuschnittstelle Eingangsrechnung ist: / 'l' Lieferantenrechnungsnummer (erech_beleg_nr) / 'i' interne Eingangsrechnungsnummer (erech_nr) / ist bei belastung_jn = "j" fix "i" / bestimmt bei Einsatz von "EURO-Fibu" auch [erech_op_kz]
@F erech_op_kz|char(1)||OP-Nummer in Fibuschnittstelle Eingangsrechnung ist: / 'l' Lieferantenrechnungsnummer (erech_beleg_nr) / 'i' interne Eingangsrechnungsnummer (erech_nr) / findet bei Eingangsrechnung und Belastungsnote Anwendung / muss bei Einsatz von "EURO"-Fibu ident mit [erech_belnr_kz] sein
@F bn_op_kz|char(1)||OP-Nummer in Fibuschnittstelle Belastung ist: / 'b' Belegnummer Belastungsnote / 'o' OP-Nummer zugehörige Eingangsrechnung / wird bei Rechnungsverbuchung mit erechart.belastung_jn = "n" verwendet / bei EURO-Fibu nicht relevant
@F bn_beldat_kz|char(1)||Belegdatum in Fibuschnittstelle Belastung ist: / 'l' Datum der Lieferantenrechnung (erech_beleg_dat) / 'i' internes Eingangsrechnungsdatum (erech_dat) / wird bei Rechnungsverbuchung mit erechart.belastung_jn = "n" verwendet
@F erech_gw_tol_we|decimal(11,2)||Toleranzbetrag für Endbetrag der ER / wird bei ER in Belegwährung umgerechnet
@F erech_bn_kz|char(2)||Belastungsnote wird erstellt / "ff" mit Fibuverbuchung (fix) / "fv" mit vollständiger Verbuchung WaWi und Fibu (fix) / "fn" niemals (fix) / "vf" mit Fibuverbuchung (Vorschlag) / "vv" mit vollständiger Verbuchung WaWi und Fibu (Vorschlag) / "vn" niemals (Vorschlag) /  / ist bei belastung_jn = "j" oder ungepr_erech_jn = "j", fix "fv"
@F zvksperre_jn|char(1)||gesperrt für Zahlungsverkehr / Vorschlag für Neuanlage Eingangsrechnung
@E
@T erechart_sprache
@D Eingangsrechnungsarten Sprachen
@F erechart _cd|char(2)|p1,f
@F sprache_cd|char(5)|p2,f
@F bn_beleg_txt|char(30)||Belegtitel für Belastungsnote
@E
@T erechimp
@D Eingangsrechnung – Importdaten
@F erechimp_snr|decimal(14,0)|p1|interne fortlaufende Nummer
@F lief_cd|char(10)||Lieferantennummer / SC: Kopfsatz Feld 2, wenn Lieferant angelegt ist
@F erechimp_kz|char(2)||Kennzeichen Quelle / sc…Scan /
@F erech_beleg_nr|char(20)||Rechnungsnummer Lieferant / SC: Kopfsatz Feld 3
@F erech_beleg_dat|datetime||Rechnungsdatum Lieferant / SC: Kopfsatz Feld 4
@F fa_nr|smallint||Firma
@F erech_nr|integer||interne Eingangsrechnungsnummer / bei Neuanlage 0 / wird beim Aufbau der Eingangsrechnung belegt
@F erechimp_status_kz|char(1)||Status der Rechnung / a…im Aufbau / u…unvollständig / fehlerhaft / v…Daten vollständig / r…Rechnung aufgebaut / e…ohne Buchung erledigt
@F imp_job_snr|decimal(14,0)||Importjob
@F status_txt|varchar(max) +n||Infotext, beinhaltet die aktuellen Fehlermeldungen auf Kopfebene(zB. Lieferant nicht definiert, Kein Lieferschein zugeordnet, ..)
@F erechimp_info_txt|varchar(max) +n||Infotext, durch den User eingebbar
@F skonto1_prz|decimal(4,2)||Skonto1-% / SC: Kopfsatz Feld 5
@F skonto1_tg|smallint||Skontotage 1 / SC: Kopfsatz Feld 6
@F skonto2_prz|decimal(4,2)||Skonto2-% / SC: Kopfsatz Feld 7
@F skonto2_tg|smallint||Skontotage 2 / SC: Kopfsatz Feld 8
@F netto_tg|smallint||Nettotage / Kopfsatz Feld 9
@F lief_iln_nr|decimal(13,0) +n||ILN-Nummer des Warenlieferanten / SC: Kopfsatz Feld 2
@F lief_name|varchar(max)+n||Anschrift des Warenlieferanten / derzeit ohne Verwendung
@F netto_wert|decimal(11,2) +n||Nettowert / SC: Kopfsatz Feld 10
@F brutto_wert|decimal(11,2) +n||Bruttowert / SC: Kopfsatz Feld 11
@F skontobasis|decimal(11,2) +n||Skontobasis / SC: Kopfsatz Feld 12
@F erl_erechimp_snr|decimal(14,0)||Erledigt-Nummer / Bei Aufbau Eingangsrechnung = erechimp_snr / Bei Erledigt-Setzen -1 / sonst 0
@F import_path|varchar(255) +n||Archiv Verzeichnis beim Import
@F import_file|varchar(255) +n||Filename des Importieren Files
@E
@N i1_erechimp (erl_erechimp_snr)
@T erechimp_beleg
@D Eingangsrechnung – Belege (Bestellungen, Lieferscheine)
@F erechimp_snr|decimal(14,0)|p1,f|interne fortlaufende Nummer
@F beleglfd_nr|smallint|p2|laufende Nummer innerhalb der Rechnung
@F ei_belegart_kz|char(1)||Belegart / 'l' …Lieferschein / 'b'…Bestellung / 'u'…unbestimmt
@F fa_nr|smallint||Firma des Eingangslieferscheins/der Bestellung
@F fil_nr|smallint||Filiale des Eingangslieferscheins/der Bestellung
@F elfs_nr|integer||interne Eingangslieferscheinnummer / 0 = ohne Zuordnung
@F best_nr|integer||interne Bestellnummer / 0 = ohne Zuordnung
@F sst_lfs_nr|varchar(35)|g|Lieferscheinnummer aus der SST
@F sst_lfs_dat|datetime +n|g|Lieferscheindatum aus der SST
@F sst_best_nr|varchar(35)|g|Bestellnummer aus der SST
@F sst_best_dat|datetime +n|g|Bestelldatum aus der SST
@F liefadr_name|varchar(max)|g|Lieferadresse aus der SST
@E
@T erechimp_pos
@D Eingangsrechnung – Importdaten – Positonsatz
@F erechimp_snr|decimal(14,0)|p1,f|interne fortlaufende Nummer
@F lfd_nr|smallint|p2|laufende Nummer der Positionen innerhalb einer Eingangsrechnung
@F artik_cd|char(20) +n||Artikelnummer
@F fa_nr|smallint +n||Firma
@F fil_nr|smallint +n||Filiale
@F netto_betr|decimal(11,2)||Nettobetrag / SC: Positionssatz Feld 15
@F ean_artikid_cd|char(13) +n||EAN-Nummer
@F lief_artikid_cd|char(20) +n||Lieferantenartikelnummer / SC: Positionssatz Feld 2
@F artik_bez1|varchar(40)||Artikelbezeichnung 1 / SC: Positionssatz Feld 3
@F artik_bez2|varchar(40)||Artikelbezeichnung 2 / SC: Positionssatz Feld 4
@F artik_bez3|varchar(40)||Artikelbezeichnung 3 / SC: Positionssatz Feld 5
@F artik_bez4|varchar(40)||Artikelbezeichnung 4 / SC: Positionssatz Feld 6
@F lief_mg|decimal(12,3)||Menge / SC: Positionssatz Feld 7
@F ekpr|decimal(12,3) +n||Einkaufspreis / SC: Positionssatz Feld 9
@F ekpr_pro_mg|decimal(4,0) +n||Preis pro Menge / SC: Positionssatz Feld 8
@F ekrab1|decimal(4,2)||Einkaufsrabatt 1 / SC: Positionssatz Feld 10
@F ekrab2|decimal(4,2)||Einkaufsrabatt 2 / SC: Positionssatz Feld 11
@F ekrab3|decimal(4,2)||Einkaufsrabatt 3 / SC: Positionssatz Feld 12
@F ekrab4|decimal(4,2)||Einkaufsrabatt 4 / SC: Positionssatz Feld 13
@F ekrab5|decimal(4,2)||Einkaufsrabatt 5 / SC: Positionssatz Feld 14
@F ssteh_cd|char(4) +n||Mengeneinheit / SC: Positionssatz Feld 17
@F steuersatz|decimal(4,2)||Steuersatz / SC: Positionssatz Feld 16
@F sst_auf_nr|varchar(35) +n||Auftragsnummer beim Lieferanten / SC: Positionssatz Feld 23
@F sst_auf_dat|datetime +n||Auftragsdatum beim Lieferanten / SC: Positionssatz Feld 24
@F sst_lfs_nr|varchar(35) +n||Lieferscheinnummer beim Lieferanten / SC: Positionssatz Feld 18
@F sst_lfs_dat|datetime +n||Lieferscheindatum beim Lieferanten / SC: Positionssatz Feld 19
@F sst_best_nr|varchar(35) +n||Unsere Bestellnummer beim Lieferanten / SC: Positionssatz Feld 20
@F sst_best_dat|datetime +n||Unser Bestelldatum beim Lieferanten / Positionssatz Feld 21
@F liefadr_name|varchar(max)+n||Anschrift der Lieferadresse / Positionssatz Feld 22
@E
@T erechimp_ust
@D Eingangsrechnung – Importdaten – UstDaten
@F erechimp_snr|decimal(14,0)|p1,f|interne fortlaufende Nummer
@F steuersatz|decimal(4,2)|p2|Steuersatz / SC: Steuer-Satz Feld 2
@F netto_betr|decimal(11,2)||Nettobetrag / SC:Steuer-Satz Feld 3
@F ust_betr|decimal(11,2)||Steuerbetrag / SC: Steuer-Satz Feld 4
@E
@T erechimp_zuab
@D Eingangsrechnung – Importdaten – UstDaten
@F erechimp_snr|decimal(14,0)|p1,f|interne fortlaufende Nummer
@F lfd_nr|smallint|p2
@F erechimp_zuab_kz|char(1)||a = Abschlag / z = Zuschlag
@F erechmip_zuab_fcd|char(3)||Zuabschlagscode lt. Import Datei / z.B. bei EDI INVOIC / DI = Rabatt / FC = Fracht
@F erechimp_zuab_txt|varchar(35)||Text
@F zuab_prz|decimal(10,4)||Prozentsatz
@F zuab_wt|decimal(18,3)||Zuabschlag Wert / Summe aus zuab_wt (unter Berücksichtigung von zuab_kz) wird als i_erech_zuab_wt übernommen
@F steuersatz|decimal(4,2) +n||Steuersatz
@E
@T erl
@D Erlöskontenzuordnung
@F artikerl_cd|char(10)|p1,f|ArtikelErlöskontenzuordnungscode
@F kundeerl_cd|char(10)|p2,f|KundenErlöskontenzuordnungscode
@F erlkto_nr|integer(9)||Erlöskontennummer
@F ust_cd|char(10)|f|Ustcode
@E
@T esetp
@D einfache Setproduktion
@F esetp_snr|integer (p)|
@F artik_cd|char(20)||Set- Hauptartikel, diese wird Produziert
@F fa_nr|smallint|f
@F p_lag_cd|char(11)|f|Zugangslager
@F p_mg|decimal(12,3)||Zugangsmenge
@F veh_estpr|decimal(15,6)||Einstandspreis pro 1 Verkaufseinheit
@F esetp_info|char(255)|
@F esetp_fa_pers_cd|char(5)||Sachbearbeiter der Neuanlage
@F p_kartei_snr|integer||kartei_snr Zugang
@F verbgebu_esetp_snr|integer||0 Verbrauch noch nicht gebucht / esetp_snr Verbrauch gebucht
@F esetp_dat|datetime||Datum der Lagerbewegung
@E
@I unique index i1_esetp (p_kartei_snr)
@I index i2_esetp (verbgebu_esetp_snr)
@T esetp_set
@D einfache Setproduktion
@F esetp_snr|integer|p1
@F teil_artik_cd|char(20)|p2,f|Set- Hauptartikel, diese wird Produziert
@F fa_nr|smallint|
@F teil_mg|decimal(12,3)||Abgangsmenge pro zugegangenem Set
@F teil_duest|decimal(15,6)||Einstandspreis pro 1 Verkaufseinheit
@F teil_kartei_snr|integer||kartei_snr Abgang
@E
@I unique index i1_esetp_set (teil_kartei_snr)
@T fa
@D Firmen- Stammdaten
@F fa_upid|bigint +n|
@F fa_nr|smallint(3)|p1|Firmennummer
@F fa_adr_snr|integer(7)|f|Adresse / Anschrift der Firma
@F komm_pro_lfs_kz|char(1)||"a" Kommissionslager wird bei Kommissionsauftragsarten artikelgenau geführt [artik_lag_sub.lag_ort] = "" / "l" Kommissionslager wird bei Kommissionsauftragsarten lieferscheingenau geführt [artik_lag_sub.lag_ort] = "lfs"+vlfs.vlfs_nr / "p" Kommissionslager wird bei Kommissionsauftragsarten lieferscheinpositionsgenau geführt [artik_lag_sub.lag_ort] = "lfs"+vlfs.vlfs_nr+"-"+vlfs_pos.auf_pos_nr /
@F komm_vkpr_bezug_jn|char(1)||'j' Der Preis einer Auftragsposition der Auftragsart 'ka' (= Kommissions-abrechnung) wird vom Bezugslieferschein 'j' ist nur bei komm_pro_lfs_kz in ("l", "p") möglich.
@F ab_auf_kz|char(1)||'a' Alle Rückstände werden in Abwicklungsauftrag übernommen / 'k' keine Rückstände werden in Abwicklungsauftrag übernommen / 'v' verfügbare Positionen werden in Abwicklungsauftrag übernommen / 'd' Positionen können im Dialog zur Übernahme ausgewählt werden / weitere Möglichkeiten durch Customizing
@F abruf_jn|char(1)||offene Abrufaufträge werden im Rückstandsregister des Auftrages angezeigt und können übernommen werden
@F offert_jn|char(1)||offene Offerte werden im Rückstandsregister des Auftrages angezeigt und können übernommen werden
@F db_ou_kz|char(1)||Deckungsbeitragsprozentsatz rechnet sich: / 'o' von oben (DB%) / 'u' von unten (Aufschlag%)
@N Prüfungsabfolge für die folgenden 4 Textbausteine beim Fakturendruck: / aufart_cd = "b" bv_txt_cd / brutto_betr < 0 gu_txt_cd / vkrech_kz = "r" lfsfakt_txt_cd / sonst fakt_txt_cd
@F fakt_txt_cd|char(20)||Code des Textbausteines welcher am Fakturenende gedruckt wird
@F bv_txt_cd|char(20)||Code des Textbausteines welcher am Barverkaufsende gedruckt wird
@F gu_txt_cd|char(20)||Code des Textbausteines welcher bei Rechnungen mit negativem Endbetrag gedruckt wird
@F lfsfakt_txt_cd|char(20)||Code des Textbausteines welcher bei Rechnung = Lieferschein gedruckt wird
@F ab_txt_cd|char(20)||Code des Textbausteines welcher am Ende der AB gedruckt wird
@F off_txt_cd|char(20)||Code des Textbausteines welcher am Ende des Offertes gedruckt wird
@F pf_txt_cd|char(20)||Code des Textbausteines welcher am Ende der Proforma gedruckt wird
@F best_txt_cd|char(20)||Code des Textbausteines welcher am Ende der Bestellung gedruckt wird
@F anfr_txt_cd|char(20)||Code des Textbausteines welcher am Ende der Anfrage gedruckt wird
@F bestmahn_txt_cd|char(20)||Code des Textbausteines welcher am Ende der Bestellmahnung gedruckt wird
@F wret_txt_cd|char(20)||Code des Textbausteines welcher am Ende der Warenretoure (Retourlieferschein) gedruckt wird
@F fakt_a_txt_cd|char(20)||Code des Textbausteines welcher am Fakturenanfang gedruckt wird
@F bv_ a_txt_cd|char(20)||Code des Textbausteines welcher am Barverkaufsanfang gedruckt wird
@F gu_ a_txt_cd|char(20)||Code des Textbausteines welcher am Anfang bei Rechnungen mit negativem Endbetrag gedruckt wird
@F lfsfakt_ a_txt_cd|char(20)||Code des Textbausteines welcher bei Rechnung = Lieferschein am Anfang gedruckt wird
@F ab_ a_txt_cd|char(20)||Code des Textbausteines welcher am Anfang der AB gedruckt wird
@F off_ a_txt_cd|char(20)||Code des Textbausteines welcher am Anfang des Offertes gedruckt wird
@F pf_ a_txt_cd|char(20)||Code des Textbausteines welcher am Anfang der Proforma gedruckt wird
@F best_ a_txt_cd|char(20)||Code des Textbausteines welcher am Anfang der Bestellung gedruckt wird
@F anfr_ a_txt_cd|char(20)||Code des Textbausteines welcher am Anfang der Anfrage gedruckt wird
@F bestmahn_a_txt_cd|char(20)||Code des Textbausteines welcher am Anfang der Bestellmahnung gedruckt wird
@F wret_a_txt_cd|char(20)||Code des Textbausteines welcher am Anfang der Warenretoure (Retourlieferschein) gedruckt wird
@F dopraz_jn|char(1)||doppelte Preisauszeichnung ist aktiviert
@F fb_ar_sy|char(2)||Fibu Buchungssymbol Rechnung
@F fb_gu_sy|char(2)||Fibu Buchungssymbol Gutschrift
@F fb_bereich_vk|char(4)||Fibu Bereichskennung Verkauf
@F fb_bereich_ek|char(4)||Fibu Bereichskennung Einkauf
@F kartei_symbol_iv|char(3)||Symbol für Inventurbuchung in kartei_lagbew
@F kartei_symbol_ek|char(3)||Symbol für Warenzugangsbuchung in kartei_lagbew
@F kartei_symbol_ga|char(3)||Symbol für ausscheiden Gerät über Serviceauftrag in kartei_lagbew
@F gw_waehrung_cd|char(4)||Währungscode der Grundwährung
@F min_rech_buper|char(6)||Bereich der in der Buchhaltung eröffneten Buchungsperioden im Format JJJJMM für Eingangsrechnungen
@F max_rech_buper|char(6)||Bereich der in der Buchhaltung eröffneten Buchungsperioden im Format JJJJMM für Eingangsrechnungen
@F min_vrech_buper|char(6)||Bereich der gültigen Buchungsperioden für den Verkauf
@F max_vrech_buper|char(6)||Bereich der gültigen Buchungsperioden für den Verkauf
@F iv_bereich_anz|smallint(4)||Anzahl Zeilen in einem Inventurbereich
@F iv_regal_stellen|smallint(2)||Anzahl Stellen Regal im Feld LagerOrt / verwendet von Inventurabgrenzung / gibt an, wie viele Stellen des Lagerortes das Regal definieren / siehe auch [iv_zeile.iv_sort1_nr] / wenn <> 0 / wird bei der Inventurabgrenzug unabhängig von [iv_bereich_anz] ein neuer Bereich immer nur pro Lager erstellt / wird die Inventurzählliste nach Sortiernummern gedruckt
@F wret_anz|smallint(2)||Beleganzahl für Retourschein im Eingangslieferschein / muss mindestens 1 sein
@F bn_anz|smallint(2)||Beleganzahl für Belastungsnote in der Eingangsrechnungsverbuchung / muss mindestens 1 sein
@F leer_adr_snr|integer(7)|f|Adresse / Anschrift, welche leer ist / zB. für den Aufenthalt eines Gerätes, welches verschrottet wurde
@F gj_start_monat|smallint(2)||z.B. : / 1 Geschäftsjahr = Kalenderjahr / 10 Oktober 2000 ist der erste Monat des Geschäftsjahres 2000 / ErsterMonatDesJahres ( AM – (gj_start_monat-1)
@F default_lag_cd|char(11)||Standardlager / wird bei Warenzugang verwendet, wenn keine Lagerzuordnung durchgeführt wurde / Vorschlag für Auftragserfassung / Vorschlag für diverse Lagerbuchung
@F bbn|integer(7)||BBN-Nummer für 1. Teil der eigenen EAN-Nummer / Vergabe der laufenden EAN-Nr über Tabelle nummern mittels tabelle = "artikid", spalte = "artikid_cd", nr_kreis = "e"
@F auf_pos_sw|smallint(2)||Schrittweite für Vergabe Auftragspositionsnummer
@F fb_kore_kz|char(1)||Fibu Korekennzeichen für Überleitung / 'b' lt. Batchinput / 'k' lt. Konto / '-' keine Koreüberleitung
@F dummy_artik_cd|char(20)||Dummy- Artikel: / kann irgend ein Artikel sein / wird lediglich zu Überlistung eines F- Keys benötigt / Wenn der Artikel als Dummy- Artikel verwendet wird: / darf kein Lookup erfolgen / darf er nicht bebucht werden
@F dummy_kunde_cd|char(10)||Dummy- Kunde analog Dummy- Artikel / muss Erlöszuordnung "Inland" haben, da der UST-Prozentsatz eines Artikels (z.B in der Artikelinfo) über diesen Kunden bestimmt wird
@F dummy_gl_kunde_cd|char(10)||Dummy- Kunde für Lieferantenretouren über Auftragsbearbeitung / blank oder ein angelegter Kunde
@F abericht_e_txt_cd|char(20)||Textbaustein für das Arbeitsbericht- Ende / muß ein Kopftext sein
@F kv_a_txt_cd|char(20)||Textbaustein für den Kostenvoranschlag- Anfang / muß ein Kopftext sein
@F kv_e_txt_cd|char(20)||Textbaustein für das Kostenvoranschlag- Ende / muß ein Kopftext sein
@F rv_e_txt_cd|char(20)||Textbaustein für das Ende des Reparatur- Verbringungs- Begleitscheins / muß ein Kopftext sein
@F wv_s_artik_cd|char(20) +n||Sethauptartikel für Wartungsvertragsauftrag / setfrei_kz muß "s" sein / Beim Aufbau eines Wartungsvertragsverrechnungsauftrages wird dieser Artikel herangezogen / Der Artikel darf keine Setbestandteile haben / wird, wenn vorhanden, von s_kunde übersteuert
@F prod_kunde_cd|char(10)||Kunde, der für Produktionsauftrag verwendet wird
@F prod_lief_cd|char(10)||lieferant, der für Bestellvorschlag (=Produktionsvorschlag) verwendet wird
@F prfind_aend_jn|char(1)||Preisfindung soll in der Auftragsbearbeitung auch im Ändern-Modus erfolgen
@N Verwaltung der folgenden Felder auf dem Register "Datanorm"
@F dn_preisli_cd|char(5)||Preisliste unter der die Listenpreise verspeichert sind (z.B. für Datanorm Ausgabe)
@F dn_sprache_cd|char(5)||Sprachcode für Datanorm Mengeneinheit
@F dn_txt_kz|char(1)||m = Kurztext1 = artik_mc, Kurztext2 = "" / t = Kurztext1 + 2 sind die ersten 2 Texte lt. artik_txt mit fakt_jn = "j" und sprache_cd = "d"
@F dn_pfad|varchar(255)||Freigabe eines Ordners im Netzwerk, unter dem die Datanormfiles angelegt werden / Ordner wird bei Ausgabe um Kundenmatchcode+Kundennummer ergänzt
@F picture_pfad|char(40)||Freigabe eines Ordners im Netzwerk, in dem die Artikelstamm-Bilder abgelegt werden / ersetzt, wenn <> "", den Wert des RegistryEintrags "PcsDirPictures"
@F vrech_txt_kz|char(1)||Textkennzeichen Faktura / "a" "Auftragsfaktura" / Auftragstexte werden für den Abwicklungsauftrag vor bzw. nach den Positionen gedruckt / allerdings nur, wenn die Faktura nicht über mehrere Aufträge erstellt wird [vkrech_kz in ("l", "lr", "a")] / "s" Sammelfaktura / Auftragstexte werden vor der 1. bzw. nach der letzten Position des zugehörigen Eingangsauftrages gedruckt / dies erfolgt beim Service vor bzw. nach der Auftragsnummerngruppe / dies erfolgt beim Verkauf vor bzw. nach der Eingangsauftragsgruppe / im Verkauf kann bei dieser Einstellung daher ein Text ggf. mehrfach angedruckt werden, wenn der Auftrag in mehreren Lieferscheinen der Rechnung vorkommt
@F auf_prod_frei_kz|char(1)||Kennzeichen Freigabe Produktionsauftrag / 'g' Gemeinsame Freigabe: Zugang und Abgang können nur gemeinsam freigegeben weren – Die Menge wird beim Zugang freigegeben / 'v' Vorschlag Abgang: bei der Eingabe der Zugangsfreigabemenge werden die Abgangsfreigabemengen vorgeschlagen, können aber übersteuert weden / 'u' unabhängige Freigabe: Zugang und Abgang werden voneinander unabhängig freigegeben
@F fa_uid_nr|char(15)||eigene UID-Nummer
@F era_uid_nr|char(15)||ERA - UID-Nummer
@F era_nr|integer(5)||ERA-Vertragspartnernummer
@F era_kontakt|char(30)||Kontakperson für ERA
@F era_adr_snr|integer(7)||ERA Adresse / Anschrift
@F era_ust_cd|char(10)||ERA Ustcode
@F era_txt_cd|char(20)||Code des Textbausteines welcher als Einleitungstext der ERA-Abrechnung gedruckt wird
@F sofort_e_vrech_jn|char(1)||E-Mail-Ausgangsrechnung sofort versenden / "j" Rechnung wird sofort gemailt, Kopien sofort gedruckt / "n" Kopien werden sofort gedruckt, die Rechnung jedoch nicht
@F ltz_fbstueb_dat|datetime||letztes Datum+Zeit der Fibu-Stammdatenüberleitung
@F fb_von_dat|datetime||Beginndatum für Fibuüberleitung / es werden nur Belege in die Fibu übergeleitet, für die gilt: / beleg_dat >= fb_von_dat
@F fb_bis_dat|datetime||Endedatum für Fibuüberleitung / es werden nur Belege in die Fibu übergeleitet, für die gilt: / beleg_dat <= fb_bis_dat
@F fbueb_job_nr|decimal(14,0)||aktuelle Fibuüberleitungsjobnummer / notwendig für Restart
@F vab_wv_job_snr|decimal(14,0)||aktuelle Wartungsvertragsaufbaunummer / notwendig wegen Doppelzugriff
@N folgende Felder werden in einem eigenen Register „E-Rechnung an Bund“ verwaltet
@F bmd_fibunr|integer||letztes Monat des Wirtschaftsjahres in der BMD-FIBU
@F eb_iban|char(34)||eigener IBAN, an den der Bund überweist
@F eb_bic|char(11)||eigener BIC, an den der Bund überweist
@F eb_bank_bez|char(40)||Bankbezeichnung, an den der Bund überweist
@F ad_abbel_dat|datetime||Datum, ab dem die Belege für die AD-SST ausgegeben werden / wird beim täglichen Ausgabelauf auf den 1. des Vormonats gesetzt / wird bei der Erstbestückung nicht verändert
@F ad_abstat_dat|datetime||Datum, ab dem die Statistik für die AD-SST ausgegeben werden / wird beim täglichen Ausgabelauf auf den 1. des Vormonats gesetzt / wird bei der Erstbestückung nicht verändert
@F webshop_preisli_cd|char(5) +n||Webshop Preisliste / Es wird der aktuelle Verkaufspreis für Menge 1 als Standard Artikelpreis beim WebShop Export verwendet. / Inkl. / Exkl. Ust muss so eingestellt sein, wie es der WebShop benötigt.
@F webshop_website_code|varchar(255)||Umschlüsselung TC Firma/Webshop Firma - Shopname
@F webshop_email_komidart_cd|char(10)|f|Für Personenanlage aus Webshop
@F webshop_telefon_komidart_cd|char(10)|f|Für Personenanlage aus Webshop
@F webshop_persfunktion_cd|char(10)|f|Für Personenanlage aus Webshop
@F webshop_konfig_layout_kz|char(1)||Webshop Layout Konfigurationsartikel / „s“ sichtbar / „n“ nicht direkt sichtbar
@F offert_gueltig_tg|smallint||Gültigkeitstage Offert
@F offert_erledigt_tg|smallint||Erledigt-Tage Offert / Offert, deren Gültigkeitsdatum [auf.lief_dat] >= Tagesdatum + [offert_erledigt_tg] ist, werden im Reorglauf auf erledigt gesetzt
@E
@T fcol
@D Freie Column für folgende Tabellen / artik / kunde / lieferant / adr_pers / geraet / Eine dieser Tabellen wird weiters mit $tab notiert. / siehe auch $tab_fcol / Im List-DW von $tab sollte $tab_fcol mitverjoint werden sodaß nach $tab_fcol_wert gesucht werden kann. Achtung: distinct verwenden
@F fcol_cd|char(10)|p1
@F fcol_tabelle_kz|char(1)|n|a = artik, k = kunde, l = lief, p=adr_pers, g=geraet, c = CAS-Kunde
@F fcol_dtyp|char(1)|n|siehe pfu_query
@F fcol_laen_vk|smallint|n|Anzahl der Zeichen/Stellen (vor dem Komma bei numerisch)
@F fcol_laen_nk|smallint|n|Nachkommastellen (bei numerisch)
@F fcol_pflicht_jn|chat(1)|n|z.B. Artikel muß mit fcol_cd einen Satz in artik_fcol besitzen
@F fcol_label|char(20)||Name des Feldes auf dem Data Window
@F fcol_default|char(40) +n||Defaultwert für freie Column / muss bei fcol_tabelle_kz = "g" und fcol_pflicht_jn = "j" ungleich Null sein
@F fcol_info|char(100) +n|
@F fcol_stammblatt_jn|char(1)||Daten werden auf Kundenstammblatt gedruckt / fix "n", wenn tabelle_kz in ("a", "b", "l", "o")
@E
@T fgr
@D Freie Auswertungsgruppe für Artikel, Kunden und Lieferanten
@F fgrart_cd|char(10)|p1,f
@F fgr_cd|char(10)|p2|Gruppencode
@F fgr_mc|char(40)|
@F ueb_fgrart_cd|char(10)||Gruppenart der Übergruppe, fgrart_cd, falls keine Übergruppe vorhanden ist
@F ueb_fgr_cd|char(10)|f|Gruppencode der Übergruppe, fgr_cd, falls keine Übergruppe vorhanden ist
@E
@T fgrart
@D Art für freie Auswertungsgruppe für Artikel, Kunden und Lieferanten / Ist in der Tabelle artik/kunde/lief eine Column mit anschließend beschriebenem Namen vorhanden, wird beim insert/update in der Tabelle / artik/kunde/lief_fgr der eingegebene fgr_cd in die obengenannte Column der Tabelle artik/kunde/lief gestellt. / ls_colname = ls_fgrart_cd + "fgr_cd" / Beim Customizen müssen die entsprechenden Columns gegebenenfalls in der Tabelle artik/kunde/lief angelegt werden (alter table). Die Felder müssen NULL erlauben!
@F fgrart_cd|char(10)|p1|Auswertungsgruppenart- Code
@F fgrart_label|char(20)||Name des Feldes auf dem Data Window
@F fgrart_tabelle_kz|char(1)|n|a = artik, k = kunde, l = lief, c = CAS-Kunde, p = adr_pers
@F fgrart_pflicht_jn|char(1)|n|z.B. Artikel muß mit fgrart_cd einen Satz in artik_fgr besitzen
@F fgrart_info|char(100) +n|
@F ueb_fgrart_cd|char(10)|n|Gruppenart der Übergruppe, fgrart_cd, falls keine Übergruppe vorhanden ist
@F fgr_cd_default|char(10) +n||Defaultwert für freie Gruppen
@F fgrart_stammblatt_jn|char(1)||Daten werden auf Kundenstammblatt gedruckt / fix "n", wenn tabelle_kz = ("a")
@E
@T fil
@D Filialen / es gibt eine Dummyfiliale 0 je Firma, diese wird vor dem Speichern automatisch angelegt
@F fa_nr|smallint(3)|p1|firma
@F fil_nr|smallint(3)|p2|Filiale
@F fil_mc|char(30)||= adr.adr_mc
@F fil_adr_snr|integer|f|Adresse der Filiale
@F fil_upid|bigint|
@E
@T ftxt
@D Freie Texte für folgende Tabellen / kunde / adr_pers / Eine dieser Tabellen wird weiters mit $tab notiert. / siehe auch $tab_ftxt
@F ftxt_cd|char(10)|p1
@F ftxt_label|char(20)||Label
@F ftxt_tabelle_kz|char(1)|n|c = CAS-kunde, p=adr_pers
@F ftxt_info|char(100) +n|
@E
@T geraet
@D Artikel- Gerätedaten / Achtung: Lage r- UserObject anpassen!
@F artik_cd|char(20)|p1,f
@F fa_nr|smallint(3)|p2
@F geraet_cd|char(40)|p3|Gerätenummer
@F geraet_zustand_kz|char(2) /|g|Zustand des Geräts / Mögliche Aktionen bei noch nicht vorhandenem Gerät: siehe Zustand ausgeschieden.
@F geraet_zustand_kz|char(2) /|g|l|lagernd und betriebsbereit / Mögliche Aktionen: / Verkauf Abgang 'k' / erfolgt beim vlfs- Aufbau- Lauf / Produktion Abgang (Zerlegung) 'a' / erfolgt beim vlfs- Aufbau- Lauf / Einkauf Retour 'r' / erfolgt mit der Anlage kartei_lagbew / in Reparatur schicken 'lr' / erfolgt mit der Anlage s_auf / Abgang Divers 'a' / Diverse Lagerumbuchung 'l' / Inventur: / soll 1, ist 0 'a' / soll 0, ist 1 'l' (kann theoretisch nicht sein)
@F geraet_zustand_kz|char(2) /|g|lr|lagernd und in Reparatur / Mögliche Aktionen: / Reparatur abschließen 'l' / Erfolgt mit dem Arbeitsberichtaufbau, wenn abericht_kz = "a" / Reparaturabschluß + Abgang + ausscheiden 'a' / Erfolgt mit dem Arbeitsberichtaufbau, wenn abericht_kz = "s" / Diverse Lagerumbuchung 'lr'
@F geraet_zustand_kz|char(2) /|g|k|gehört dem Kunden und ist beim Kunden / dies wird bei manueller Anlage des Gerätes automatisch gesetzt / Mögliche Aktionen: / Verkauf Zugang 'l' / in Reparatur schicken 'kr' / ausscheiden 'a' / über Geräteverwaltung / Inventur: / soll 1, ist 0 'a' (kann theoretisch nicht sein) / soll 0, ist 1 'l' / Zugang divers 'l'
@F geraet_zustand_kz|char(2) /|g|kr|gehört dem Kunden und ist in Reparatur / Mögliche Aktionen: / Reparatur abschließen 'k' / Erfolgt mit dem Arbeitsberichtaufbau, wenn abericht_kz = "a" / Reparaturabschluß + ausscheiden 'a' / Erfolgt mit dem Arbeitsberichtaufbau, wenn abericht_kz = "s"
@F geraet_zustand_kz|char(2) /|g|r|an den Lieferanten retourniert / Mögliche Aktionen: / Einkauf Zugang 'l' / erfolgt mit Anlage kartei_lagbew / Inventur / soll 1, ist 0 'a' (kann theoretisch nicht sein) / soll 0, ist 1 'l' / Zugang Divers 'l' / Geräteverwaltung 'k', 'a' / Produktion Zugang 'l'
@F geraet_zustand_kz|char(2) /|g|a|ausgeschieden / Mögliche Aktionen: / Einkauf Zugang 'l' / (bei Inventur gelöscht, weil nie geliefert wurde) / erfolgt mit der Anlage kartei_lagbew / Zugang Divers 'l' / Inventur / soll 1, ist 0 'a' (kann theoretisch nicht sein) / soll 0, ist 1 'l' / Geräteverwaltung 'k' / Produktion Zugang 'l'
@F wo_adr_snr|integer(7)|f,g|Adresse des derzeitigen Aufenthaltsortes des Geräts: / ist laut wo_adr_kz belegt
@F wo_adr_kz|char(1)|g|Bedeutung von wo_adr_snr:
@F wo_adr_kz|char(1)|g|"f"|wo_adr ist firma.fa_adr / bei geraet_zustand_kz 'l', 'k', 'lr', 'kr' möglich
@F wo_adr_kz|char(1)|g|"k"|wo_adr ist kunde.kunde_adr / bei geraet_zustand_kz 'k', 'kr' möglich
@F wo_adr_kz|char(1)|g|"r"|wo_adr ist externe Reparaturadresse / bei geraet_zustand_kz 'lr', 'kr' möglich
@F wo_adr_kz|char(1)|g|" "|wo_adr ist fa.leer_adr (unbekannter Aufenthalt) / bei geraet_zustand_kz 'a' und 'r' möglich
@F wo_adr_kz|char(1)|g|wird bei Lagerzugang auf 'f' gesetzt / wird bei Lagerabgang / beimAusgangslieferschein auf 'k' / wird bei allen übrigen Abgängen auf '' / gesetzt / Kann auf 'f', 'k' oder 'r' gesetzt werden, wobei bei 'r' die Adresse manuell auszuwählen ist.
@F wo_adr_dat|date||Datum, an dem wo_adr_snr verändert wurde
@F standort_kunde_cd|char(10)|f|Standort des Geräts / hier steht das Gerät, wenn es in Betrieb ist / Serviceaufträge haben normalerweise diesen Kunden / ist fa.dummy_kunde_cd, wenn das Gerät nicht dem Kunden gehört also geraet_zustand_kz nicht 'k' oder 'kr' ist. / es erfolgt kein Lookup, wenn das Gerät nicht dem Kunden gehört.
@F standort_pers_cd|char(5)||Person beim Standort- Kunden, welche für das Gerät zuständig ist / kann auch die Pseudo- Person " " sein. / ist " ", wenn das Gerät nicht dem Kunden gehört. / es erfolgt kein Lookup, wenn das Gerät nicht dem Kunden gehört.
@F ekpr|decimal(12,3)||Einkaufspreis in GW / Wird beim Insert mit DuEk belegt und gegebenenfalls geändert
@F estpr|decimal(12,3)||Einstandspreis in GW / Wird beim Insert mit DuEst belegt und gegebenenfalls geändert / Estp- Ermittlung der entsprechenden Warenzugangsposition bei der ER- Kontrolle / Diverse Lagerbuchung / Inventur
@F estpr_abw|decimal(12,3)||Einstandspreis abgewertet in GW / Wird beim Insert mit DuEst belegt und gegebenenfalls geändert: / Estp- Ermittlung der entsprechenden Warenzugangsposition bei der ER- Kontrolle / Diverse Lagerbuchung / Inventur / Geräteverwaltung
@F ltz_abw_dat|date +n|g|Datum der letzten Abwertung
@F geraet_info|text +n||interne Information
@F geraet_info_search|char(255) +n||die ersten 255 Zeichen der internen Information
@F geraet_upid|bigint +n|
@E
@I unique index i1_geraet ( geraet_cd, artik_cd, fa_nr )
@I index i2_geraet (geraet_upid)
@T geraet_ek
@D Artikel- Gerätedaten- Einkauf (ng) / Nur vorhanden, wenn Gerät über den Warenzugang eingegangen ist. / Wird bei jedem Lagerabgang außer beim Verkauf wieder gelöscht.
@F artik_cd|char(20)|p1
@F fa_nr|smallint(3)|p2
@F geraet_cd|char(40)|p3,f|Gerätenummer
@F elfs_nr|integer(7)||Eingangslieferscheinnummer
@F elfs_pos_nr|smallint(4)|f|dazu Positionsnummer
@F gar_end_dat|date +n||Garantieendedatum / = Lieferscheindatum + .gar_mo_ek lt. artik bzw. best_pos
@E
@I index i1_geraet_ek(elfs_nr, fa_nr, elfs_pos_nr)
@T geraet_fcol
@D Zuordnung Gerät -> Freies Gerätekennzeichen
@F artik_cd|char(20)|p1,f
@F fa_nr|smallint(3)|p2
@F geraet_cd|char(40)|p3,f|Gerätenummer
@F geraet_fcol_cd|char(10)|p3,f|Code der Art des freien Kennzeichens
@F geraet_fcol_wert|char(40)||Column- Wert
@E
@T geraet_vk
@D Artikel- Gerätedaten- Verkaufsdaten (ng) / Nur vorhanden, wenn Gerät verkaufsseitig an den Kunden geliefert wurde. Wird bei Gutschrift wieder gelöscht.
@F artik_cd|char(20)|p1
@F fa_nr|smallint(3)|p2
@F geraet_cd|char(40)|p3,f
@F vlfs_nr|integer(7)||vlfs_pos, alle 0, wenn kein Bezug
@F ein_auf_nr|integer(7)||vlfs_pos, alle 0, wenn kein Bezug
@F auf_pos_nr|smallint(4)||vlfs_pos, alle 0, wenn kein Bezug
@F kunde_cd|char(10)||= ein_auf.kunde_cd
@F gar_end_dat|date +n||Garantieendedatum / = Lieferscheindatum + auf_pos.gar_mo_vk
@E
@I index i1_geraet_vk (vlfs_nr, fa_nr)
@T hilf_ara_stichtag
@D Temporäre Tabelle zum Druck der Lagerentpflichtung nzw. Differenzentpflichtung
@F job_snr|decimal(14,0)|p1|Job-Snr
@F artik_cd|char(20)|p2|Artikel
@F fa_nr|smallint|p3|Firma
@F lag_mg_dat1|decimal(12,3)||Lagermenge Stichtag 1
@F lag_mg_dat2|decimal(12,3)||Lagermenge Stichtag 2
@E
@T impfehl
@D Fehlertabelle Import EK/VK
@F impfehl_snr|integer|
@F id_txt|char(80)||ID Importierte Zeile / VK / fa_nr + " / " + vkkondart_cd + " / " + artik_zuord + " / " + kunde_zuord / EK / fa_nr + " / " + lief_cd + " / " + artikid_cd
@F fehler_txt|char(200)||Fehlertext
@E
@T iv
@D Inventur / Es gibt einen Dummy- Satz mit / iv_nr = 0 / iv_dat = "1.1.1111" / iv_kartei_snr = / -1 bei der Erstinventur ohne vorhergegangenen Lagerbewegungen werden alle artik_lag- Rows abgegrenzt / 0 bei der Erstinventur ohne vorhergegangenen Lagerbewegungen wird keine artik_lag- Row abgegrenzt / die kleinste Einheit, die inventiert werden kann ist eine Row in artik_lag / Beim Inventurabschluß ist folgendes zu berücksichtigen: / Die Differenzbuchungen haben als Buchungsdatum das Inventurabgrenzungsdatum. / bei positiven Differenzen zu einem Artikel ohne DUEST werden die DUEST- Felder mit 0 belegt / eine Inventur kann nur Lager mit lag_kz = 'e' beinhalten
@F iv_nr|integer(7)|p1|vergabe mittels Tabelle nummern
@F fa_nr|smallint(3)|p2,f|Firma
@F iv_dat|date||Lagerbewegungsdatum welches bei der Inventurdifferenzbuchung herangezogen wird
@F iv_soll_dat|date|ng|Datum der Inventurabgrenzung Datum an dem die Soll- Mengen abgestellt worden sind / wird bei der Inventurabgrenzung auf today gesetzt / Buchungen, die während einer offenen Inventur erfolgen und deren Lagerbewegungsdatum (= kartei_dat) vor iv_soll_dat liegen, werden zusätzlich in iv_zeile.soll_zus_lag_mg eingerechnet.
@F iv_buch_dat|date +n||Datum des Inventurabschlusses = der Inventurbuchung
@F iv_zustand_kz|char(2)||'a' Inventur abgegrenzt (eröffnet) / 'ka' Korrektur Abgrenzung läuft / 'e' Inventur erledigt (abgeschlossen) / 's' Inventur storniert / 'te' Inventur teilweise erledigt / Abschluss musste abgebrochen werden / 'ts' Inventur teilweise storniert / Storno musste abgebrochen werden
@N "j" iv_zustand_kz in ("e", "s") / "n" sonst
@F erl_iv_nr|integer(7)|g|0 Inventur ist offen / iv_nr Inventur ist abgeschlossen
@F iv_kartei_snr|integer|ng|letzte kartei_snr vor der Abgrenzung
@F iv_upid|bigint +n||ID
@E
@I index i0_iv (iv_upid)
@I index i1_iv (erl_iv_nr, fa_nr)
@T iv_bereich
@D Inventur- Bereich / siehe iv_zeile / Die Inventur- Zeilen sind in Bereiche gegliedert. / Die Inventurzeilen sind nach / Lager / Lagerort / Artikel / Charge/Seriennummer / sortiert. / Ein Bereich umfasst hintereinanderliegende Zeilen bis zu einem Bereichswechsel / Ein Bereichswechsel erfolgt / beim Wechsel des Lagers / beim Erreichen der maximalen Zeilenanzahl je Bereich lt. Firma / Die artik_lag_sub – Daten eines Artikels befinden sich immer innerhalb eines Bereiches
@F iv_nr|integer(7)|p1,f|vergabe mittels Tabelle nummern
@F iv_bereich_nr|integer(7)|p2|Laufende Nummer innerhalb der Inventur
@F fa_nr|smallint(3)|p3|Firma
@F lag_cd|char(11)|f|Lager = iv_zeile.lager
@F bereich_zustand_kz|char(2)||'a' Inventurbereich abgegrenzt (eröffnet) / 'e' Inventurbereich erledigt (abgeschlossen) / 's' Inventur storniert / 'te' Inventurbereich teilweise erledigt / Abschluss musste abgebrochen werden / 'ts' Inventurbereich teilweise storniert / Storno musste abgebrochen werden
@N "j" iv_zustand_kz in ("e", "s") / "n" sonst
@F iv_bereich_upid|bigint +n||ID
@E
@N i0_iv_bereich (iv_bereich_upid)
@T iv_mdeerf
@D Inventurerfassungsdaten aus TC-Next MDE Lösung
@F iv_mdeerf_snr|bigint (p)||Eindeutige Nummer
@F mde_person|varchar(20)||MDE Sachbearbeiter
@F mde_erf_datz|datetime||Zeitpunkt schreiben dieses Satzes
@F mdeerf_usr|char(10)||Freier Usercode fürdie MDE Erfassung / Zur Inventur arbeiten User, die nicht als MDE User im System angelegt sind mit den Geräten, diese können hier ohne Prüfung eingegeben werden.
@F mde_status|smallint||Gilt für alle Tabellen der Kommissionierung / 0 Daten werden geschrieben / 1 Daten können verarbeitet werden / 2 Daten wurden verarbeitet
@F fa_nr|smallint|
@F iv_nr|integer||Inventurnummer
@F iv_bereich_nr|integer||Bereichsnummer
@F lag_ort|char(20)||Lagerort (Null bei Abschluss)
@F artik_cd|char(20)||Artikelnummer (Null bei Abschluss)
@F charge_geraet|char(40)||Charge (Null bei Abschluss) / Kann bei Verwendung von EAN128 auch belegt sein, wenn der Artikel keine Chargen- oder Geräete-Lagerführung hat.
@F menge|decimal(12,3)||gezählte Menge in Lagereinheit
@F erl_datz|datetime +n||Zeitpunkt der Verbuchung in der TC Inventur
@F herst_dat|date +n||Herstellungdateum aus EAN128
@F mhd_dat|date +n||Mindesthaltberkeitsdatum aus EAN128
@F ablauf_dat|date +n||Ablaufdatum/Verfallsdatum aus EAN128
@F artik_eh_upid|bigint||Einheit in der Zugebucht wurde
@F ive_mg|decimal(12,3)||Inventur Menge in Einheit
@E
@I index i1_iv_mdeerf (mde_status,iv_mdeerf_snr)
@T iv_zeile
@D Inventurzeile / entspricht einer Row in artik_lag_sub bzw. einer Row in artik_lag, zu welcher es keine Row in artik_lag_sub gibt und für die gilt: artik_lag.ltz_iv_nr = iv.iv_nr and /  / Bei der Inventurabgrenzung wird iv_zeile mittels folgendem Select befüllt: / select … / from artik_lag, outer artik_lag_sub, iv / where artik_lag joins artik_lag_sub / and artik_lag joins iv using artik_lag.ltz_iv_nr / and ( artik_lag.lag_mg <> 0 or artik_lag.ltz_kartei_snr > iv.iv_kartei_snr ) / and via QBE iv.iv_dat < z.B. Geschäftsjahresbeginn
@F iv_nr|integer(7)|p1|vergabe mittels Tabelle nummern
@F iv_bereich_nr|integer(7)|p2,f|Laufende Nummer innerhalb der Inventur
@F fa_nr|smallint(3)|p3|Firma
@F lag_cd|char(11)|r,f|Lagercode lt. Bereich
@F lag_ort|char(20)|p4|Lagerort lt. artik_lag_sub / darf nicht blank sein, wenn soll_lag_mg – ist_lag_mg <> 0 und lag.lag_ort_inp_jn = 'j' / wird automatisch auf Blank gesetzt, wenn lag.lag_ort_inp_jn = 'n'
@F artik_cd|char(20)|p5,f|Artikel
@F charge_geraet|char(40)|p6|Leer, Gerätenummer oder Chargennummer / darf nicht blank sein, wenn soll_lag_mg – ist_lag_mg <> 0 und der Artikel Charge oder Gerät ist / wird automatisch auf Blank gesetzt, wenn der Artikel weder Charge noch Gerät ist
@F soll_lag_mg|decimal(12,3)|ng|artik_lag_sub.lag_mg bei der Abgrenzung / wird bei de Abgrenzung auf artik_lag_sub.lag_mg gesetzt, falls eine Row vorhanden ist, ansonsten auf 0.
@F soll_zus_lag_mg|decimal(12,3) /||siehe iv.iv_soll_dat / dient zum Abbilden von Belegen, deren Warenbewegung physikalisch vor der Inventur stattgefunden hat, die allerdings erst nach der Inventurabgrenzung gebucht werden. (z.B. weil man im Zuge der Inventur bemerkt hat, daß eine Eingangslieferung zu buchen vergessen worden ist.) / Auf der Inventurliste ist als Sollstand soll_lag_mg+soll_zus_lag_mg auszuweisen. / Beim Rekonstruieren des Lagerstandes aus dem Sollstand der letzten Inventur ist diese Menge nicht zu berücksichtigen, weil das Rekonstruieren ja nach kartei_snr erfolgt, und diese Buchungen in der Kartei ja nach der Abgrenzung stehen
@F ist_lag_mg|decimal(12,3) +n||gezählte Menge, bei der Neuanlage NULL
@F liste_lag_ort|char(20)|ng|lag.lag_ort_inp_jn = 'n' artik_lag.inp_n_lag_ort / sonst artik_lag_sub.lag_ort
@F ablauf_dat|date +n||Ablaufdatum bei artikel.lagfuehr_kz = 'c' und artikel.ablaufdat_jn = 'j', / sonst NULL
@F iv_manuell_jn|char(1)||'j': / Inventurzeile wurde manuell eingegeben / Zeile darf im Buchungsprogramm gelöscht werden / 'n' / Inventurzeile wurde im Zuge des Abgrenzungsprogrammes erstellt / Zeile darf nicht gelöscht werden
@F kartei_snr|integer|g|0 keine Lagerbewegung: entweder Inventur ist nicht abgeschlossen, oder es gibt keine Differenz / > 0 Verweis auf die zugehörige Lagerbewegung (genau eine Row in kartei_lagbew) (= die Inventurdifferenzbuchung)
@F erl_iv_nr|integer||Erledigungsnummer / 0…offen / >0 verbucht
@F duest_b|decimal(15,6) +n||lt. [artik_lag] zum Zeitpunkt der Inventurabgrenzung
@F duest|decimal(15,6) +n||siehe duest_b
@F iv_sort1_nr|integer(7)||Sortiernummer 1 Inventur / für Inventurerfassung nach Lagerorten / wird beim Abgrenzungslauf optional in einem 2. Step vergeben / Start pro Lager mit 1 / Vergabe bei Wechsel Stellen [1-n] des Lagerortes / n = [fa.iv_regal_stellen] / Sortierung aller Inventurzeilen: [lag_cd, liste_lag_ort, artik_cd, charge_geraet]
@F iv_sort2_nr|integer(7)||Sortiernummer 2 Inventur / wird beim Abgrenzungslauf optional in einem 2. Step vergeben / Start pro Sortiernummer1 mit 1
@E
@I index i1_iv_zeile (kartei_snr, artik_cd)
@I index i2_iv_zeile (artik_cd, iv_nr, fa_nr)
@I index i3_iv_zeile (kartei_snr)
@I index i4_iv_zeile (iv_nr, iv_sort1_nr, iv_sort2_nr)
@T kassa
@D Kassenstamm / Filiale der Kassa ist über lag.lag_fil_nr bestimmt
@F kassa_nr|smallint(3) (p)||Kassennummer
@F kassa_bez|char(20)||Kassenbezeichnung
@F pause_sek|integer||Pause in Sekunden für Datenaustausch
@F troffen_jn|char(1)||Transaktion bei Datenübernahme während der Pause offen lassen
@F loe_tage|integer||Nach wievielen Tagen werden Belege am Kassensystem gelöscht
@F fa_nr|smallint(3)||Firmennummer
@F lag_cd|char(11)|f|Lagercode / wenn [lag.cg_verw_jn] = "n", dann werden auch Chargen-/Geräteartikel an die Kassa (als lagfuehr_kz = "n") ausgegeben
@F gus_txt|char(40)||Text zum Andruck am Gutschein (vor dem Datum, enthällt im Normallfall den Ort).
@F ka_kabst_cd|char(5)|f|Kassa - Kassenbestandsgruppencode
@F sb_eingabe_kz|char(1)||f|Fix lt. Windows Login
@F sb_eingabe_kz|char(1)||v|Vorschlag lt. Windows Login
@F sb_eingabe_kz|char(1)||z|Zwingende Eingabe - kein Vorschlag
@F sb_eingabe_kz|char(1)||l|Vorschlag lt. letzter Eingabe
@F sb_eingabe_kz|char(1)||h|Hardware zur Identifikation vorhanden
@F mzldru_kz|char(1)||s|Münzliste und Tagesabschluss wird auf Slip ausgedruckt
@F mzldru_kz|char(1)||b|Münzliste und Tagesabschluss wird auf Bon ausgedruckt
@F tagabsch_jn|char(1)||Tagesabschluss auf Kassa möglich (c) / Ja ist nur möglich, wenn die Kassenbestandsgruppe gleich der Kassennummer ist, und es einen Kassenbestand mit dieser Kassenbestandsgruppe und Sachbearbeitercode = " " gibt, der keinen fixen Endbestand hat
@F kk_kopf_ka_txt_cd|char(10)||Textbausteincode Kreditkartenbeleg Kopftext
@F kk_ende_ka_txt_cd|char(10)||Textbausteincode Kreditkartenbeleg Endtext
@F gus_kopf_ka_txt_cd|char(10)||Textbausteincode Gutscheinkopf
@F gus_ende_ka_txt_cd|char(10)||Textbausteincode Gutscheinende
@F ka_aktiv_jn|char(1)||Kassa ist Aktiv / Bei "n" werden keine ka_datueb Datensätze über Trigger aufgebaut. / D.h. ka_datueb_kz wird fix auf "-" gesetzt.
@F lade_oeffnen_kz|char(1)||Zeitpunkt zum Öffnen der Kassenlade / a = Abschluss Beleg / z = Eingabe Zahlungsart
@F lizenz_jn|char(1)||Kassa hat eine gültige Lizenz / Bei "n" ist es nicht möglich das Kassenprogramm zu starten / Es darf maximal soviele Kassen mit Lizenz geben, wie Kassen-Lizenzen in der Applikation vorhanden sind. / Wenn zu wenige vorhanden sind, funktioniert das Verbuchen Kassa in TC nicht. / Beim Verbuchen Kassa in TC werden nur Kassen mit Lizenz berücksichtigt.
@F zahlbest_dru_kz|char(1)||Druckversion Zahlungsbestätigung / b = Bondrucker (Standard) / s = Slipdrucker, Andruck direkt auf TC-Rechnung (muß Customized werden)
@F def_kunde_cd|varchar(10) +n||Default Kundennummer für neue Kassa
@F ka_datueb_kz|char(1)||Kassen-Art für Kassen-Datenübernahme / - = Nicht aktiv – es wird nichts übertragen / a = TC-Kassa (jede Kassa erhält ihre Daten) / h = Hauptkassa (TouchPos) / Die Hauptkassa erhält alle Daten
@F svccli_path|varchar(128)||Service Programmstand Client Pfad / Im Normallfall "c:\pcs\Programme\PcsPosService
@F artikbildcli_path|varchar(128)||Artikel Bilder Client Pfad
@F kassabelgrp_nr|smallint(3)||Kassenbeleggruppennummer / Wenn beim Speichern leer wird die Kassennummer vorgeschlagen
@F rksvka_status_kz|char(1)||Status der RKSV Registrierkasse / '-' = RKSV nicht aktiv (Bei Registrierkassen in Österreich nicht erlaubt) / 'n' = Nicht in Betrieb / 'r' = Registriert / 'a' = Ausfall / 'o' = Offene Abmeldung / Es wurde ein Abmeldebeleg erstellt, der noch nicht verbucht ist / 'd' = Deutsche TSE über ESR (EFSTA Simple Receipt)
@F reg_datz|datetime +n|g|Zeitpunkt der Registrierung der Registrierkasse auf Finanz-Online / Wenn nicht Null, dann ist die Kassa angemeldet
@F ausfall_datz|datetime +n||Ausfall/Abgemeldet seit Datum/Uhrzeit
@F rksvka_ausfall_kz|smallint||Ausfall Codierung für FinanzOnline SST / 0 = Kein Ausfall / 1 = Diebstahl oder sonstiger Verlust / 5 = Erfassung der Geschäftsvorfälle oder / 99 = Sonstiger Grund
@F rksv_ende_kz|smallint||Außerbetriebnahme Codierung für FinanzOnline SST / 0 = " " / 6 = Planmäßige Außerbetriebnahme / 7 = Außerbetriebnahme aufgrund eines irreparablen Ausfalls
@F rksv_mlco_kz|char(1)||Maschinenlesbarer Code – Variante / q = QR (Default) / o = OCR
@F rksv_kunde_cd|char(10) +n|f|Kundennummer für RKSV-Sonderbelege / Muss bei RKSV ein angelegter Kunden sein
@F rksv_id_sub_nr|smallint|g|Subnummer der RKSV-Kassen-ID / Wird bei Neuanlage mit 0 initialisiert / Wird bei jeder FON Abmeldung um 1 erhöht
@F rksvgrp_cd|char(5)|f|RKSV-Gruppencode
@F (g)|RKSV Daten / Diese werden nur bei einer Erstbestückung von TC auf die Kassa übernommen (nur bei Insert – nicht bei Update). / Sie werden jedoch regelmäßig an TC retour übertragen|
@F rksv_ums|decimal(12,2)||Umsatzzähler lt. RKSV
@F rksv_le_bel_dat|date +n||Datum letzter Beleg
@F rksv_le_ums_mon|char(6)||Letzter Umsatzzähler Monatsabschluss / Ist bei Start Blank / Wird mit dem Start-Beleg auf das Vormonat gestellt. / Wird mit dem Monatsabschluss gesetzt / Monatsabschluss/Jahresabschluss wird automatisch bei Start des Barverkaufs durchgeführt, wenn das Monat in der Vergangenheit ist.
@F rksv_le_sig|char(32)||Signatur des letzten Belegs
@F rksvseh_cd|char(20) +n||Signaturerstellungseinheit Seriennummer der letzten erfolgreichen Signatur – notwendig um diese bei einem SEH-Ausfall für QR und DEP Code zu haben.
@N Ende RKSV Daten
@F mpd_deviceid|integer +n||MPD: Id of the Terminal
@F mpd_automode|integer +n||MPD: AutoMode
@F mpd_terminalid|char(12)||MPD: Terminal-ID
@F mpd_printerwidth|integer||MPD: Druckerbreite in Zeichen
@F mpd_language|char(4)||MPD: Sprache / de = Deutsch / en = Englisch
@F mpd_ReceiptOptions|integer +n||MPD: Druckeroptionen (Default = 1473) / EFT_RCP_SUPPRESS_HEADER = 1 (Def.) / EFT_RCP_PRINT_DOP = 2, / EFT_RCP_SUPPRESS_SIGNATURE = 4, / EFT_RCP_SMALL_FORMAT = 8, / EFT_RCP_SUPERSMALL_FORMAT = 16, / EFT_RCP_WITH_CONTROL_CHARS= 32, / EFT_RCP_WITH_MERCHANT_RECEIPT = 64 (Def) / EFT_RCP_SUPPRESS_ECR_INFORMATION = 128 (Def) / EFT_RCP_SUPPRESS_EFT_INFORMATION = 256 (Def) / EFT_RCP_COMPACT_FORMAT = 512, / EFT_RCP_SUPER_COMPACT_FORMAT = 1024 (Def) / EFT_RCP_ULTRA_COMPACT_FORMAT = 2048, / EFT_RCP_SUPPRESS_EFT_DCCDISCLAIMERTEXT = 4096, / EFT_RCP_SUPPRESS_EFT_FEEDISCLAIMERTEXT = 8192, / EFT_RCP_SUPPRESS_MERCHANT_SIG = 2*8192
@F waage_geraet_fcd|varchar(20)||Seriennummer der Waage / Muss bei einer Waagenintegration vorhanden sein / Wird in der Verisions Anzeige der Waage angezeigt
@F kassa_geraet_fcd|varchar(20)||Seriennummer des Kassen PC / Muss bei einer Waagenintegration vorhanden sein / Wird in der Versions Anzeige der Waage enagezeigt
@F esr_tl|varchar(30)||EFSTA ESR Transaction Location / Store ID / Definiert gemeinsam mit esr_tt die Kassa / Diese Kombination muss in einer Firma eindeutig sein wenn die Deutsche TSE aktiviert ist
@F esr_tt|varchar(30)||EFSTA ESR Transaction Terminal / Cash Register Terminal Number / Definiert gemeinsam mit esr_tl die Kassa / Diese Kombination muss in einer Firma eindeutig sein, wenn die Deutsche TSE aktiviert ist
@F a4d_logoname|varchar(50)||Name des Logofiles (inkl. Endung) für A4 Belegdrucke / Das Logo ist auf der Kassa im Unterverzeichnis logo verspeichert
@F a4d_logo_zeilen|smallint(2)||Anzahl der Zeilen für Logo bei A4 Druck
@F warrify_jn|char(1)||Warrify ist aktiv
@F warrify_beldru_kz|char(1)||Belegdruckverhalten bei Warrify / n = Beleg nicht drucken / j = Beleg trotzdem drucken
@F warrify_tenant_id|varchar(255)||The id oft he tenant
@F warrify_country|char(5)||Iso2 Land der Filiale
@F warrify_locale|char(5)||Language Tag, bei uns normalerweise de-DE
@F warrify_name|Varchar(50)||Name des Unternehmens
@F warrify_legalname|Varchar(50)||Name des Unternehmens
@F warrify_branchname|Varchar(50)||Name der Filiale
@F warrify_brandname|Varchar(50)||Brandname
@F warrify_branchid|Varchar(50)||Id der Filiale, z.b. Filialnummer
@F warrify_legalname|Varchar(50)||Legalname? Was immer das ist
@F warrify_emailadress|Varchar(255)||Email der Filiale
@F warrify_websiteurl|Varchar(255)||Website der Filiale
@F warrify_phonenumber|Varchar(50)||Telefon der Filiale
@F warrify_streetadress|Varchar(50)||Strasse der Filiale
@F warrify_city|Varchar(50)||Ort der Filiale
@F warrify_postalcode|Varchar(50)||PLZ der Filiale
@F warrify_countryname|Varchar(50)||Landbezeichnung der Filiale
@F warrify_isocountrycode|Varchar(50)||ISO der Filiale
@F warrify_taxid|Varchar(50)||UID/VAT
@F guspruef_kz|Char(3)||Prüfkennzeichen Gutscheine / off = Offline, wie bisher / on = Online, Livedurchgriff. Wenn nicht möglich, wird gus nicht akzeptiert / oo = Zuerst online, wenn nicht möglich, dann offline
@E
@S ka_archiv_....
@N Ebenbilder folgender Tabellen, zur Archivierung alter Kassenbelege:
@N ka_bel (=ka_archiv_bel)
@N ka_bel_pos (=ka_archiv_bel_pos)
@N ka_bel_pos_stkorr (=ka_archiv_bel_pos_stkorr)
@N ka_bel_vrech (=ka_archiv_bel_vrech)
@N ka_bel_ust (=ka_archiv_bel_ust)
@N ka_dj (=ka_archiv_dj)
@N ka_kartei (=ka_archiv_kartei)
@N ka_kartei_zp (=ka_archiv_kartei_zp)
@N ka_kartei_zp_txt (=ka_archiv_kartei_zp_txt)
@T ka_auswgrp
@D Auswahlgruppe / Wird auf POS Kassa für Anzeige der Auswahl über Artikel-Bilder verwendet
@F auswgrp_cd|char(10)|p1|Auswahlgruppencode
@F fa_nr|smallint|p2,f
@F auswgrp_mc|varchar(40)||Matchcode
@F sort_nr|smallint||Sortierreihenfolge
@E
@T ka_auswgrp_artik
@D Auswahlgruppe Artikelzuordnungen
@F auswgrp_cd|char(10)|p1,f|Auswahlgruppencode
@F fa_nr|smallint|p2
@F artik_cd|char(20)|p3,f|Artikelcode
@F sort_nr|integer||Sortiernummer
@E
@T ka_auswgrp_sprache
@D Auswahlgruppe Label Texte in Fremdsprache
@F auswgrp_cd|char(10)|p1,f|Auswahlgruppencode
@F fa_nr|smallint|p2
@F sprache_cd|char(5)|p3,f|Sprache
@F auswgrp_txt|varchar(40)||Label Text in Sprache für Button
@E
@T ka_bel
@D Kassen Belgkopf
@F bel_nr|integer(7)|p1|Belegnummer
@F kassa_nr|smallint(2)|p2,f|Kassanummer
@F fa_nr|smallint(3)|f|Firmennummer
@F bel_dat|date||Belegdatum
@F bel_zeit|datetime||Zeit des erstmaligen Ausdruckes
@F bel_art|char(1)||Belegart / b = Barverkaufsbon / a = Anzahlung / r = Rechnungsausgleich (Restzahlung) / l = Lieferschein / s = RKSV Sonderbeleg
@F bel_art_sub_cd|char(2)|f|Sub-Belegart / Im Normalfall blank oder "st" für Storno / Bei RKSV Belegen die jeweilge Vartiante / TC.Next – Bolean Storno j/n
@F kunde_cd|char(10)|f|Kundennummer
@F adr_snr|integer|f|Belegadresse / Bei der Datenübernahme wird, wenn die Belegadresse mit der Kundenadresse übereinstimmt die kunden-adr_snr eingetragen. / Gibt es eine übereinstimmende Adresse, so wird diese snr eingetragen / Gibt es die Adresse noch nicht, wird eine neue adr (+adr_pers) angelegt
@F sb_cd|char(5)|f|Sachbearbeitercode
@F gen_sb_cd|char(5)||Sachbearbeiter der den Beleg genehmigt hat / " " wenn der Beleg nicht genehmigungspflichtig ist oder der Sachbearbeiter selbst die Berechtigung hat etwas zu genehmigen.
@F vkrab|decimal(4,2)||Kopfrabatt / Wird als 3 Positionsrabatt gerechnet
@F betrag|decimal(8,2)||Gesamtbetrag
@F zahl_betr|decimal(8,2)||Zahlungsbetrag / exkl. Skonto
@F rest_betr|decimal(6,2)||Restbetrag/Retourgeld
@F storno_bel_nr|integer(7)||Belegnummer welche mit dieser Buchung storniert wurde
@F auf_nr|integer(8)||Auftragsnummer / bei Belegart a die Auftragsnummer für die die Anzahlung gemacht wurde / Bei Belegart l die Auftragsnummer die im TC generiert wurde
@F tax_free_jn|char(1)||TAX FREE Beleg drucken j/n
@F tax_free_betr|decimal(8,2)||TAX FREE Betrag
@F erl_bel_nr|interger(7)||0 noch nicht alle Positionen im TC verbucht / >0 alle Positionen im TC verbucht
@F wawiueb_datz|datetime||Übertragungszeitpunkt der Datenübernahme / Nur für PCS zur Fehlersuche
@F neu_kd_nr|char(10)||Kundennummer neu / Wird im Normallfall mit der Kundennummer belegt / Beim Belegdruck wird die Kundennummer neu statt die Kundennummer verwendet / Wird zur Anlage des Kunden im TC als Kundennummer verwendet
@F rksv_string|varchar(2000) +n||Signatur die als QR oder OCR Code am Beleg auszudrucken ist
@F rksvseh_ausfall_jn|char(1)||RKSV-Sicherheitseinrichtung war bei Belegerstellung ausgefallen
@F rksv_pruef_datz|datetime +n|g|Beleg wurde über Finanz Online geprüft
@F rksv_pruef_txt|varchar(3000) +n||Ergebnistext der Finanz Online Prüfung
@F tse_start_datz|datetime +n|g|Zeitpunkt des Beginns der Belegerfassung / Wird nur bei Touch Kassa ab Version mit TSE belegt
@F druck_auf_kz|char(2) +n||Kennzeichen Ausdruck auf welches Gerät / Wird im Standard von ka_belart_sub belegt. / Ist Nullfähig wegen Performance Umstellung von Altdaten bei Kunden mit vielen Kassenblegen. / b = Bondrucker / s = Slip-Drucker / a = A4 Drucker
@F warrify_code|Varchar(255) +n||Gescannter Warrify Code
@E
@N i1_ka_bel (erl_bel_nr)
@N i2_ka_bel (bel_dat)
@T ka_bel_vrech
@D Rechnungsausgleich – Aufteilung auf Rechnungen / Nur bei Belegart Rechnungsausgleich vorhanden / Der Beleg-Betrag ergibt sich aus Summe zahl_betr + Summe skonto_betr
@F bel_nr|integer(7)|p1,f|Belegnummer
@F kassa_nr|smallint|p2
@F fa_nr|smallint(3)||Firmennummer
@F op_nr|integer(8)|p3|OP-Nummer
@F vrech_nr|integer(8)||Rechnungsnummer / 0 = Zahlung ohne Bezug auf eine Rechnung
@F zahl_betr|decimal(8,2)||Zahlungsbetrag / exkl. Skonto
@F skonto_betr|decimal(8,2)||Skonto-Betrag
@F skonto_prz|decimal(4,2)||Skontoprozentsatz
@E
@T ka_bel_pos
@D Kassen Belegposition
@F bel_nr|integer(7)|p1,f|Belegnummer
@F kassa_nr|smallint(3)|p2|Kassennummer
@F pos_nr|smallint|p3|interne Positionsnummer
@F fa_nr|smallint(3)||Firmennummer
@F artik_cd|char(20)||Artikelnummer
@F art_bez|varchar(60)||Artikelbezeichnung
@F menge|decimal(12,3)||Menge
@F vk_pr|decimal(8,2)||Verkaufspreis inkl. Mehrwertsteuer
@F vkrab1|decimal(4,2)||Rabatt 1
@F vkrab2|decimal(4,2)||Rabatt 2
@F vkrab3|decimal(4,2)||Positionsrabatt 3 – 4 können in individuellen Ableitungen verwendet werden
@F vkrab4|decimal(4,2)||Positionsrabatt 3 – 4 können in individuellen Ableitungen verwendet werden
@F vkrab5|decimal(4,2)||Positionsrabatt 3 – 4 können in individuellen Ableitungen verwendet werden
@F vkpr_ftr|decimal(13,7)|r|Faktor, sodaß gilt: / Menge * Preis * Faktor = Positionsbetrag
@F vkrab_ftr|smallint(1)||Kopfrabatt Faktor / 1 = Kopfrabatt berücksichtigen / 0 = Kopfrabatt nicht berücksichtigen
@F manuell_jn|char(1)||Preis oder Rabatt wurden manuell übersteuert
@F ust_cd|smallint(1)|f|MwSt Code
@F set_pos_kz|char(1)|ng|'s' = Sethauptposition / 't' = Setteil / 'n' = Normalposition
@F set_pos_nr|smallint(4)|ng|set_pos_kz = 't' Positionsnummer des Sethauptartikels / set_pos_kz <> 't' auf_pos_nr / Bei set_pos_kz 'n' ist set_pos_nr = pos_nr (aber erst bei Belegen welche mit Release 776 erstellt wurden).
@F set_teil_mg|decimal(12,3) +n|ng|set_pos_kz = 't' Menge in einem Set (siehe auch artik_set.teil_mg) / sonst: NULL
@F set_frei_kz|char(1)|ng|aus kassa-belpos bzw. artik befüllen, Verwendung der Felder: siehe artik!!!
@F set_preis_dru_kz|char(1)|ng|aus kassa-belpos bzw. artik befüllen, Verwendung der Felder: siehe artik!!!
@F set_stat_kz|char(1)|ng|aus kassa-belpos bzw. artik befüllen, Verwendung der Felder: siehe artik!!!
@F set_fibu_kz|char(1)|ng|aus kassa-belpos bzw. artik befüllen, Verwendung der Felder: siehe artik!!!
@F set_teil_dru_kz|char(1)|ng|aus kassa-belpos bzw. artik befüllen, Verwendung der Felder: siehe artik!!!
@F zug_auf_nr|integer|ng|Zugeordnete Eingangs-Auftragsnummer ~807~
@F zug_auf_pos_nr|smallint|ng|Zugeordnete Auftragspositionsnummer ~807~
@F lag_cd|char(11)|f,n|Lager / bei Datenübernahme " " / wird beim TC-verbuchen belegt
@F duest|decimal(15,6)||bei der Datenübernahme 0 / wird beim TC-verbuchen belegt / artik_lag.duest is not null artik_lag.duest / artik.duest is null vkpr abzüglich Ust * artik.ka_duest_prz / 100 / artik.duest is not null artik.duest
@F pos_wert_iu|decimal(11,2)|r|Positionsbetrag inkl. Ust / round(menge * vk_pr * (1 - vkrab1/100) * (1 - vkrab2/100) * vkpr_ftr * (1 - ka_bel.vkrab/100*vkrab_ftr),2)
@F ums|decimal(11,2)||Umsatz / pos_wert_iu / (100+ka_bel_ust.ust_prz ) * 100 / Fix 0 bei Belegart Lieferschein und Setpositionen siehe set_stat_kz
@F fibu_ums|decimal(11,2)||Umsatz für FIBU Buchung / Fix 0 bei Belegart Lieferschein, Anzahlungsauftrag und Setpositionen siehe set_fibu_kz. / Bei Anzahlungsaufträgen ist die "AnzahlungsArtikelPosition" ausgenommen und wird normal - wie die Artikelposition eines Barverkaufes - behandelt.
@F umsmg|decimal(12,2)||Umsatzmenge / Fix 0 bei Belegart Lieferschein, Anzahlungsauftrag und Setpositionen siehe set_stat_kz. / Bei Anzahlungsaufträgen ist die "AnzahlungsArtikelPosition" ausgenommen und wird normal - wie die Artikelposition eines Barverkaufes - behandelt.
@F verbmg|decimal(12,2)||Verbrauchsmenge / Fix 0 bei Belegart Lieferschein, Anzahlungsauftrag und nicht lagerführenden Artikeln. / Bei Anzahlungsaufträgen ist die "AnzahlungsArtikelPosition" ausgenommen und wird normal - wie die Artikelposition eines Barverkaufes - behandelt.
@F weins|decimal(11,2)||Wareneinsatz / wird bei der Neuanlage mit 0 belegt / wird beim Verbuchen überschrieben (menge * duest) / Fix 0 bei Belegart Lieferschein, Anzahlungsauftrag und Setpositionen siehe set_stat_kz. / Bei Anzahlungsaufträgen ist die "AnzahlungsArtikelPosition" ausgenommen und wird normal - wie die Artikelposition eines Barverkaufes - behandelt.
@F kartei_snr|integer||bei der Datenübernahme 0 / wird beim TC-verbuchen belegt, wenn Artikel mit Lagerführung / 0 keine Lagerbewegung / > 0 Verweis auf die zugehörigen Lagerbewegungen (eine oder mehrere Rows in kartei_lagbew)
@F kunde_cd|char(10)|r|Kunde lt. ka_bel
@F bel_mon|char(6)|r|bei Datenübernahme " " / wird beim TC-verbuchen lt. ka_bel.bel_dat belegt
@F bel_dat|date|r|Belegdatum lt. ka_bel
@F stat_gebucht_jn|char(1)||Statistikdaten und Verbräuche sind gebucht / bei Datenübernahme "n" / wird beim TC-verbuchen "j"
@F erl_bel_nr|integer||0 in TC noch nicht verbucht (Datenübernahme) / > 0 in TC verbucht
@F sum_ftr|decimal(1,0)||Summenfaktor für Berechnung der Belegsummen: / Bei Artikelpositionen von Anzahlungsbelegen 0. / Bei Setpositionen, welche nicht verrechnet werden ( / set_preis_dru_kz = "s" und set_pos_kz <> "s" / oder / set_preis_dru_kz = "t" und set_pos_kz <> "t") auch 0.
@F ewpfand_kz|Char(1) +n||Einwegpfandkennzeichen / Notwendig für leichtere Mengensynchro und spätere Abfragen / h… Hauptartikel („Die Flasche Cola“) / p….Pfandposition („Das Flaschenpfand“) / <blank> … Nicht Pfandrelevant.
@F storno_pos_nr|smallint +n||Ist bei Storno Positionen die Positionsnummer des urspünglichen Belegs (lt. ka_bel.storno_bel_nr)
@E
@I index i1_ka_bel_pos (erl_bel_nr)
@I index i2_ka_bel_pos (artik_cd, bel_mon)
@I index i3_ka_bel_pos (kunde_cd, bel_mon)
@I index i4_ka_bel_pos (bel_mon)
@I index i5_ka_bel_pos (kartei_snr)
@I index i6_ka_bel_pos (kunde_cd, bel_dat)
@I index i7_ka_bel_pos (artik_cd, bel_dat)
@I index i8_ka_bel_pos (zug_auf_nr, fa_nr, zug_auf_pos_nr)
@T ka_bel_pos_stkorr
@D Kassen Belegposition – Statistikkorrektur / Wird bei ER-Kontrolle befüllt, wenn sich durch die ER-Kontrolle der DUEST ändert.
@F bel_nr|integer(7)|p1|Belegnummer
@F kassa_nr|smallint(3)|p2|Kassennr
@F pos_nr|smallint|p3,f|interne Positionsnummer
@F ums|decimal(11,2)||Umsatz / pos_wert_iu / (100+ka_bel_ust.ust_prz ) * 100 / Fix 0 bei Belegart Lieferschein und Setpositionen siehe set_stat_kz
@F umsmg|decimal(12,2)||Umsatzmenge / Fix 0 bei Belegart Lieferschein, Anzahlungsauftrag und Setpositionen siehe set_stat_kz. / Bei Anzahlungsaufträgen ist die "AnzahlungsArtikelPosition" ausgenommen und wird normal - wie die Artikelposition eines Barverkaufes - behandelt.
@F verbmg|decimal(12,2)||Verbrauchsmenge / Fix 0 bei Belegart Lieferschein, Anzahlungsauftrag und nicht lagerführenden Artikeln. / Bei Anzahlungsaufträgen ist die "AnzahlungsArtikelPosition" ausgenommen und wird normal - wie die Artikelposition eines Barverkaufes - behandelt.
@F weins|decimal(11,2)||Wareneinsatz / wird bei der Neuanlage mit 0 belegt / wird beim Verbuchen überschrieben (menge * duest) / Fix 0 bei Belegart Lieferschein, Anzahlungsauftrag und Setpositionen siehe set_stat_kz. / Bei Anzahlungsaufträgen ist die "AnzahlungsArtikelPosition" ausgenommen und wird normal - wie die Artikelposition eines Barverkaufes - behandelt.
@E
@T ka_bel_ust
@D Kassenkartei MWSt Aufteilung
@F bel_nr|integer(7)|p1,f|Belegnummer
@F kassa_nr|smallint(3)|p2|Kassennummer
@F ust_cd|smallint(10)|p3,f|MWSt Code
@F netto_betrag|decimal(8,2)||Nettobetrag
@F ust_betrag|decimal(8,2)||MWSt Betrag
@F ust_prz|decimal(4,2)||Mehrwertsteuerprozentsatz
@F sktfhg_betrag|decimal(8,2)||Skontofähiger Betrag inkl. MwSt
@E
@T ka_belart
@D Kassen Belegarten
@F bel_art|char(1) (p)||Belegart / B = Barverkaufsbon / A = Anzahlung / R = Rechnungsausgleich / K = Kassenein-/Ausgang / L = Lieferschein / S = Sonderbeleg für RKSV
@F bel_art_bez|char(30)||Belegartentext
@E
@T ka_belart_sub
@D Kassen-Subbelegarten
@F bel_art|char(1)|f,p1|Belegart
@F bel_art_sub_cd|char(2)|p2|Sub Belegart / st = Stornobuchung (muss für "B" angelegt werden) / RKSV Sonderbelege (sind hier extra angelegt, da evt. eigene Textbausteine notwendig sind). / ' ' = Prüfbeleg (0er) (nur dieser kann manuell ausgewählt werden) / sb = Startbeleg / me = Monatsende / je = Jahresende / as = Ausfall-Sammelbeleg / ka = Kassen-Abmeldung
@F keaart_bez|char(20)||Kasseneinausgangsart Bezeichnung
@F text_1|char(30)||Buchungstext
@F belanz_ftr|smallint(1)||Faktor für Anzahl Belege am Tagesendbericht / 1 = Normal mitrechnen / 0 = Nicht mitrechnen (z.B. für Diversen Kassenausgang) / -1 = Negativ mitrechnen (z.B. für Barverkaufsstorno)
@F absch_jn|char(1)||Diese Belegart ist eine manuelle Abschöpfung
@F nr_kreis|char(10)||Nummernkreis
@F kopien_anz|smallint(2)||Anzahl Belgkopien auf Kassa
@F vz_kz|char(1)||b = beides möglich / p = nur positive Werte möglich / n = nur negative Werte möglich
@F belgrp_cd|char(5)|f|Beleggruppencode
@F belart_aktiv_jn|char(1)||Darf nur bei bel_art = "K" auf inaktiv gesetzt werden.
@F druck_auf_kz|char(2)||Kennzeichen Ausdruck auf: / b = Bon-Drucker (Default) / s = Slip-Drucker / a = A4 Drucker
@E
@T ka_belart_sub_ka
@D Kassen-Subbeleg- Kassa / Dient zur Definitionder Kopf und Fußtexte pro Kassa und Belegart
@F bel_art|char(1)|p1|Buchungssymbol / siehe ka_belart
@F bel_art_sub_cd|char(2)|p2,f|Sub Belegart
@F kassa_nr|smallint|p3,f|Kassennummer
@F kopf_ka_txt_cd|char(10)||Textbausteincode Beleg Kopftext
@F ende_ka_txt_cd|char(10)||Textbausteincode Beleg Endtext
@E
@T ka_belgrp
@D Belegartengruppe / wird auf alle Kassen getriggert
@F belgrp_cd|char(5)|p1|Belegartengruppencode
@F belgrp_mc|char(20)|
@F sort_kz|char(3)||Sortierkriterium für Tagesendbericht
@F ea_kz|char(1)||Auf Tagesendbericht unter Einnahmen oder Ausgaben drucken
@E
@T ka_bertr
@D Kassen Berechtigungsträger / für POS-Kassa
@F ka_bertr_snr|bigint (p)||Laufende Nummer / Um eine Problemlosen Insert in abgeleiteten DB´s durchführen zu können, sollte hier mit der Instanzlogik gearbeitet werden
@F ka_bertr_bereich|varchar(60)||Bereich / Auswahl über pfu_kz / Blank = Allgemein
@F ka_bertr_col|varchar(40)||Feldname / Blank = gilt für gesamten Bereich
@F ka_bertr_fun|varchar(80)||Funktional / Wenn ausgefüllt handet es sich um eine Funktioniale Berechtigung, die ausprogrammiert werden muss
@F ka_bertr_info|varchar(255)||Infotext
@E
@T ka_bertr_usrgrp
@D Kassen Berechtigungsträger / Eine nicht vorhandene Zuordnung bedeutet keine Berechtigung / für POS-Kassa
@F ka_bertr_snr|bigint|p1|Laufende Nummer / Um eine Problemlosen Insert in abgeleiteten DB´s durchführen zu können, sollte hier mit der Instanzlogik gearbeitet werden
@F usrgrp_cd|char(20)|p2|kap_usrgrp
@F disp_jn|char(1)||Anzeige ist erlaubt
@F aend_jn|char(1)||Änderung ist erlaubt
@E
@T ka_bktjou
@D Kassa - Bankomat/Kreditkartenterminal Journalzeilen
@F kassa_nr|smallint(2)|p1,f|Kassennummer
@F bktjou_nr|integer|p2|laufende Nummer
@F bktjou_dat|datetime||Datum/Uhrzeit
@F bktjou_txt|varchar(500)||Text
@F bktjou_sa|char(1)||Satzart
@E
@T ka_bst
@D Kassa - Bestand / Anfangsbestand einer Kassa bzw. Kasssenlade bei Verwaltung der Kassenbestände pro Benutzer
@F ka_kabst_cd|char(5)|p1|Kassenbestandgruppencode
@F fa_nr|smallint(3)|p2|Firmennummer
@F ka_sbbst_cd|char(5)|p3|Sachbearbeiter Kassenbestandsgruppencode
@F kunde_cd|char(10)|f|Kundennummer für FIBU Überleitung Barverkauf
@F kassa_kto|integer(9)||Kassenkonto
@F anfangsbest|decimal(12,2)||Kassenladen Bargeld Anfangsbestand
@F anfangsbest_fix_jn|char(1)||Fixer Anfangs (=Endbestand) / Ja nur möglich, wenn es für die Kassenbestandsgruppe keine Kassa mit Kassenabschluss auf Kassa gibt
@F le_tagabsch_dat|date +n||Datum des letzten Tagesabschlusses
@F offen_bel_dat|date +n||kleinstes Datum eines noch nicht abgeschlossenen Beleges
@F bagatell_betr_neg|decimal(11,2)||Bagatellgrenze für fixen Endbestand für Fehlbetrag (ist – Soll)
@F bagatell_betr_pos|decimal(11,2)||Bagatellgrenze für fixen endbestand für Überschuss (ist – Soll)
@F tagab_dru_kz|char(1)||Münzlistendruckkennzeichen für fixen Endbestand / v = nur vorläufig (Vor Abschöpfung) / e = nur endgültig (Nach Abschöpfung) / b = vor und nach Abschöpfung
@F automzldru_jn|char(1)||Münzliste wird automatisch gedruckt (Gilt nur für Tagesabschluß im Tradecontrol)
@F soll_endbest|Decimal(12,2)||Soll-Endbestand bei Fixem Anfangsbestand
@E
@T ka_bst_zahlung
@D Kassa-Zahlungsarten
@F ka_kabst_cd|char(5)|p1|Kassenbestandgruppencode
@F fa_nr|smallint(3)|p2|Firmennummer
@F ka_sbbst_cd|char(5)|p3,f|Sachbearbeiter Kassenbestandsgruppencode
@F zahlung_cd|char(3)|p1,f|Zahlungscode
@F fb_kto|integer(9)||Fibu-Konto mit Kategorie
@F fb_absch_kz|char(1)||n = nicht buchen / k = Kreditorenbuchung / d = Debitorenbuchung / s = Sachkontenbuchung / c = Kassenbuch / g = Kassenbuch – fb_kto ist das Kassenkonto für das Kassenbuch / Diese Variante ist Notwendig, wenn die Abschöpfung eine Umbuchung auf eine Allgemeine Kassa ist, für die in der JetFIBU ein Kassenkonto verwendet werden soll.
@F fb_absch_sy|char(2)||FIBU Buchungssymbol für Abschöpfungen
@F ust_cd|char(10) +n||Ust-Code für Abschöpfungsbuchung
@F fb_bu_txt|varchar(50)||Buchungstext
@E
@T ka_button
@D Kassa - Button / Wird nur von Touch Kassa Verwendet / Definition der Buttons im rechten mittleren Bereich / Verwaltung über Register am Kassenstamm
@F kassa_nr|smallint|p1,f|Kassennummer
@F kabt_zeile_nr|smallint|p2|Zeilennummer / Im TC Standard 1 – 5 erlaubt ( Im Standard nur 4 Buttons auf Kassa sichtbar, 9 und 10 für Indiv Verwendung)
@F kabt_spalte_nr|smallint|p3|Spaltennummer / Im TC Standart 1 – 2 erlaubt
@F kabt_label|varchar(20)||Label Text
@F kabtart_kz|char(2)||Buttonart / z = Zahlung / Zahlungsart muss ausgefüllt sein / Ist der Wert 0 wird die Zahlungsart auf 0 zurückgesetzt, ist der Wert 99999 so wird der gesamte offene Betrag als mit dieser Zahlungsart bezahlt vorgeschlagen, ansonsten wird der Wert zum bezahlt Wert dieser Zahlungsart addiert / ist der Gesamtbetrag negativ wird negativ erhöht / pw = Position Wiegen auslösen / pl = Position löschen / pm = Position Menge / Verändert die Menge der aktuellen Position um den Wert
@F zahlung_cd|char(3) +n|f|Zahlungsart / Ist bei Buttonart <> z fix null
@F kabt_wt|integer||Wert
@E
@T ka_cancel
@D Kassa – Verworfene Belege / Wird bei jedem „Rückgängig“ erstellt (wenn der entsprechende Nummernkreis vorhanden ist)
@F kassa_nr|Smallint|p1|Kassennummer
@F ka_cancel_nr|integer|p2|laufende Nummer , / Vergabe lt. nummern 1x pro Cancel /
@F lfd_nr|Smallint|p3|Laufende Nummer pro Position
@F cancel_datz|datetime||Datum/Uhrzeit
@F sb_cd|char(5) +n||Sachbearbeitercode
@F kunde_cd|char(10) +n||Kundennummer
@F fa_nr|smallint||Firma
@F artik_cd|char(20) +n||Artikelnummer
@F pos_wert|Decimal(11,2) +n||Positionswert / Bei Preisinfo Verkaufspreis
@F auf_nr|Integer + n||Auftragsnummer für Anzahlungen
@F ka_cancel_kz|char(1)||c = Cancel (Default für PB Kassa) / i = Preisinfo (nur POS Kassa)
@E
@T ka_datueb
@D Kassa - Datenübernahme / Diese Tabelle wird mit Hilfe von Trigger befüllt / Beim Feld cd1 sind bei den Tabellen in Klammer die zulässigen Kassen-Arten angegeben.
@F ka_datueb_snr|serial (p)||laufende Nummer
@F kassa_nr|smallint(2)|f|Kassennummer
@F tabname|char(18)||Tabellenname / loebew = Bewegungsdaten von Kassa löschen / ende = Abdrehen der Kassen-Datenübernahme / ka_sqlcmd = führt das SQL-Statment hinter [ka_sqlcmd. ka_sqlcmd_snr] = cd1 aus
@F akt_kz|char(1)||Aktionskennzeichen / I = Insert / U = Update / D = Delete / ACHTUNG muss auch bei den Sonderlogiken (ende, pruefen) mit einem gültigen Wert (z.B. U) belegt sein
@F cd1|varchar(40)||artikel|Artikelcode (a,h,m) / i_artik / u_artik / d_artik / Erstbestückung
@F cd1|varchar(40)||artikid|Artikelcode (a,h,m) / i_artikid / u_artikid / d_artikid / Erstbestückung
@F cd1|varchar(40)||artik_txt|artik_cd / i_artik_txt (a,h,m) / u_artik_txt (a,h,m) / d_artik_txt (h,m) / Erstbestückung (h,m)
@F cd1|varchar(40)||artik_set|Artikelcode (a,h,m) / i_artik_set / u_artik_set / d_artik_set / Erstbestückung
@F cd1|varchar(40)|
@F cd1|varchar(40)||belart|bel_art (a,h) / i_ka_belart / u_ka_belart / d_ka_belart / Erstbestückung
@F cd1|varchar(40)||belart_sub|bel_art (a,h) / i_ka_belart_sub / u_ka_belart_sub / d_ka_belart_sub / i_ka_belart_sub_ka / u_ka_belart_sub_ka / d_ka_belart_sub_ka / Erstbestückung
@F cd1|varchar(40)||belart_sub_ka|bel_art (a,h,m,f,n) / Erstbestückung (h,m,f,n)
@F cd1|varchar(40)||belgrp|belgrp_cd (a,h) / i_ka_belgrp / u_ka_belgrp / d_ka_belgrp / Erstbestückung
@F cd1|varchar(40)||geraet|geraet_kz (a,h,m,f,n) / i_ka_geraet / u_ka_geraet / d_ka_geraet / Erstbestückung
@F cd1|varchar(40)||gus|Gutscheinnummer (a,h,m) / i_ka_gus / u_ka_gus / d_ka_gus / Erstbestückung
@F cd1|varchar(40)||eh|eh_cd (h)
@F cd1|varchar(40)||eh_sprache|eh_cd (h)
@F cd1|varchar(40)||kassa|kassa_nr (a,h,m,f,n) / u_kassa / Erstbestückung / "rksv-init" bei einer RKSV-Neu-Registrierung eine Kassa
@F cd1|varchar(40)||auswgrp|auswgrp_cd (h,m) / Insert/Delete/Update auf ka_auswgrp_sprache für Firma und Sprache der Kassa
@F cd1|varchar(40)||auswgrp_artik|auswgrp_cd (h,m) / I/D/U für Kassa lt Firma
@F cd1|varchar(40)||belkopf|Bel_nr (a,h,m,f,n) / Erstbestückung (Rücksicherung)
@F cd1|varchar(40)||ka_button|kabt_zahlung_nr / I/D/U für kassa lt. Firma
@F cd1|varchar(40)||ka_kartei|Bel_nr (a,h,m,f,n) / Erstbestückung (Rücksicherung)
@F cd1|varchar(40)||kennsatz|ka_fa - fa_nr (a,h,m) / i_ka_fa / u_ka_fa / d_ka_fa / Erstbestückung
@F cd1|varchar(40)||kunde|kunde_cd (a,h,m) / u_adr / u_debitor / i_kunde / u_kunde / d_kunde / u_adr_pers / Erstbestückung
@F cd1|varchar(40)||kunde_auf_txt|kunde_cd (a,h,m) / i_kunde_auf_txt / u_kunde_auf_txt / d_kunde_auf_txt / Erstbestückung
@F cd1|varchar(40)||kunde_vkkondgr|kunde_cd / i_kunde / u_kunde / d_kunde / Erstbestückung
@F cd1|varchar(40)||land|land_cd (a,h) / i_land / u_land / d_land / i_land_fa / u_land_fa / d_land_fa / Erstbestückung
@F cd1|varchar(40)||mwst|mwst_cd (a,h) / i_ka_mwst / u_ka_mwst / d_ka_mwst / Erstbestückung
@F cd1|varchar(40)||muenzli_vg|lfd_nr (a,h,m) / i_ka_mzlvg / u_ka_mzlvg / d_ka_mzlvg / Erstbestückung
@F cd1|varchar(40)||nummern|Tabelle (a,h,m,f,n) / Erstbestückung / In w_nummern und w_kassa fix ausprogrammiert
@F cd1|varchar(40)||op|op_nr (a) / i_ka_op / u_ka_op / d_ka_op / Erstbestückung
@F cd1|varchar(40)|
@F cd1|varchar(40)||preisli_prfind|preisli_cd (a,h) / i_preisli_prfind / u_preisli_prfind / d_preisli_prfind / Erstbestückung
@F cd1|varchar(40)||ka_rksvseh|rksvseh_cd / i/u/d + Erstbestückung
@F cd1|varchar(40)||sb|sb_cd (a,h) / i_ka_sb / u_ka_sb / d_ka_sb / Erstbestückung
@F cd1|varchar(40)||tax_free|mwst_cd (a) / i_ka_taxfree / u_ka_taxfree / d_ka_taxfree / Erstbestückung
@F cd1|varchar(40)||ka_txt|ka_txt_cd (h) / i_ka_txt / d_ka_txt / Erstbestückung
@F cd1|varchar(40)||ka_txt_txt|ka_txt_cd (a,h) / i_ka_txt_txt / u_ka_txt_txt / d_ka_txt_txt / Erstbestückung
@F cd1|varchar(40)||vkkond|vkkond_snr (a,h,m) / i_vkkond / u_vkkond / d_vkkond / Erstbestückung
@F cd1|varchar(40)||vkkond_preis|vkkond_snr (a,h,m) / i_vkkond_preis / u_vkkond_preis / d_vkkond_preis / Erstbestückung
@F cd1|varchar(40)||vkkondart|vkkondart_cd (a,h) / Änderung kassa_jn von j auf n: akt_kz = D, Es werden auch alle dazugehörigen Datensätze in vkkond und vkkond_preis gelöscht / Änderung kassa_jn von n auf J: akt_kz = I, Es werden alle dazugehörigen vkkond und vkkond_preis Datensätze übertragen / i_vkkondart / u_vkkondart / d_vkkondart / Erstbestückung
@F cd1|varchar(40)||waehrung|waehrung_cd (a,h) / i_waehrung / u_waehrung / d_waehrung / Erstbestückung
@F cd1|varchar(40)||waehrung_kurs|waehrung_cd (a,h) / i_waehrung_kurs / u_waehrung_kurs / d_waehrung_kurs / Erstbestückung
@F cd1|varchar(40)||zahlung|zahlung_cd (a,h,m) / i_ka_zahlung / u_ka_zahlung / d_ka_zahlung / Erstbestückung
@F cd1|varchar(40)||pfu_amenu|amenu_cd (a) / i_kap_amenu / u_kap_amenu / d_kap_amenu / Erstbestückung
@F cd1|varchar(40)||pfu_amenu_sprache|amenu_cd (a ) / i_kap_amenu_sprache / u_kap_amenu_sprache / d_kap_amenu_sprache / Erstbestückung
@F cd1|varchar(40)||pfu_berecht|usrgrp_cd (a ) / i_kap_berecht / u_kap_berecht / d_kap_berecht / Erstbestückung
@F cd1|varchar(40)||pfu_bertr|bertr_snr (a ) / i_kap_bertr / u_kap_bertr / d_kap_bertr / Erstbestückung
@F cd1|varchar(40)||pfu_bertr_col|bertr_snr (a ) / i_kap_bertr_col / u_kap_bertr_col / d_kap_bertr_col / Erstbestückung
@F cd1|varchar(40)||pfu_col|col_name (a ) / i_kap_col / u_kap_col / d_kap_col / Erstbestückung
@F cd1|varchar(40)||pfu_col_sprache|col_name (a ) / i_kap_col_sprache / u_kap_col_sprache / d_kap_col_sprache / Erstbestückung
@F cd1|varchar(40)||pfu_darsch|darsch_cd (a ) / i_kap_darsch / u_kap_darsch / d_kap_darsch / Erstbestückung
@F cd1|varchar(40)||pfu_darsch_fdarst|darsch_cd (a ) / i_kap_darsch_fdarst / u_kap_darsch_fdarst / d_kap_darsch_fdarst / Erstbestückung
@F cd1|varchar(40)||pfu_darschzu|winlogin (a ) / i_kap_darschzu / u_kap_darschzu / d_kap_darschzu / Erstbestückung
@F cd1|varchar(40)||pfu_dwo_lablemap|dwo_name (a ) / i_kap_dwo_lablemap / u_kap_dwo_lablemap / d_kap_dwo_lablemap / Erstbestückung
@F cd1|varchar(40)||pfu_fdarst|fdarst_cd (a ) / i_kap_fdarst / u_kap_fdarst / d_kap_fdarst / Erstbestückung
@F cd1|varchar(40)||pfu_gridschema|gridschema_snr (a ) / i_kap_gridschema / u_kap_gridschema / d_kap_gridschema / Erstbestückung
@F cd1|varchar(40)||pfu_gridschema_col|gridschema_snr (a ) / i_kap_gridschema_col / u_kap_gridschema_col / d_kap_gridschema_col / Erstbestückung
@F cd1|varchar(40)||pfu_menu|menu_name (a ) / i_kap_menu / u_kap_menu / d_kap_menu / Erstbestückung
@F cd1|varchar(40)||pfu_menui_sprache|menu_name (a ) / i_kap_menui_sprache / u_kap_menui_sprache / d_kap_menui_sprache / Erstbestückung
@F cd1|varchar(40)||pfu_sprache|sprache_cd (a,h ) / i_kap_sprache / u_kap_sprache / d_kap_sprache / Erstbestückung
@F cd1|varchar(40)||pfu_sprache_txt|sprache_cd (a ) / i_kap_sprache_txt / u_kap_sprache_txt / d_kap_sprache_txt / Erstbestückung
@F cd1|varchar(40)||pfu_usergrp|usergrp_cd (a ) / i_kap_usrgrp / u_kap_usrgrp / d_kap_usrgrp / Erstbestückung
@F cd1|varchar(40)||pfu_usrgrp_map|usr_cd (a ) / i_kap_usrgrp_map / u_kap_usrgrp_map / d_kap_usrgrp_map
@F cd1|varchar(40)||pfu_win|w_name (a ) / i_kap_win / u_kap_win / d_kap_win / Erstbestückung
@F cd1|varchar(40)||pfu_win_ctrltxt|w_name (a ) / i_kap_win_ctrltxt / u_kap_win_ctrltxt / d_kap_win_ctrltxt / Erstbestückung
@F cd1|varchar(40)||pfu_win_qcol|w_name (a ) / i_kap_win_qcool / u_kap_win_qcol / d_kap_win_qcol / Erstbestückung
@F cd1|varchar(40)||pfu_win_qcol_pwin|w_name (a ) / i_kap_win_qcol_pwin / u_kap_win_qcol_pwin / d_kap_win_qcol_pwin / Erstbestückung
@F cd1|varchar(40)||pfu_win_qmap|w_name (a ) / i_kap_win_qmap / u_kap_win_qmap / d_kap_win_qmap / Erstbestückung
@F cd1|varchar(40)||pfu_win_qcmap_col|w_name (a ) / i_kap_win_qmap_col / u_kap_win_qmap_col / d_kap_win_qmap_col / Erstbestückung
@F cd1|varchar(40)||pfu_win_qtab|w_name (a ) / i_kap_win_qtap / u_kap_win_qtab / d_kap_win_qtab / Erstbestückung
@F cd1|varchar(40)||pfu_win_verarbart|w_name (a ) / i_kap_win_verarbart / u_kap_win_verarbart / d_kap_win_verarbart / Erstbestückung
@F cd1|varchar(40)||pfu_winmodus|w_name (a ) / i_kap_winmodus / u_kap_winmodus / d_kap_winmodus / Erstbestückung
@F cd1|varchar(40)||pfu_serial|tabname (a JP?) / Erstbestückung
@F cd1|varchar(40)||pfu_berechtigung|usr_login (a)
@F cd1|varchar(40)||pfu_default|usr_cd (a) / i_kap_default / u_kap_default / d_kap_default / Erstbestückung
@F cd1|varchar(40)||pfu_format|col_name (a)
@F cd1|varchar(40)||pfu_kz|col_name (a) / i_kap_kz / u_kap_kz / d_kap_kz / Erstbestückung
@F cd1|varchar(40)||pfu_proglist|u_id_nr (a)
@F cd1|varchar(40)||pfu_progteil|id_name (a)
@F cd1|varchar(40)||pfu_query|applobjtyp (a)
@F cd1|varchar(40)||pfu_gridschema|gridschema_snr (a) / i_kap_gridschema / u_kap_gridschema / d_kap_gridschema
@F cd1|varchar(40)||pfu_gridschema_col|gridschema_snr (a) / i_kap_gridschema_col / u_kap_gridschema_col / d_kap_gridschema_col
@F cd1|varchar(40)|
@F cd2|varchar(40)||belart_sub|bel_art_sub_cd
@F cd2|varchar(40)||belart_sub_ka|bel_art_sub_cd
@F cd2|varchar(40)||artikid|artikid.artikid_kz
@F cd2|varchar(40)||artik_txt|zeile_nr
@F cd2|varchar(40)||auswgrp_artik|artik_cd
@F cd2|varchar(40)||eh_sprache|sprache_cd
@F cd2|varchar(40)||nummern|Spalte
@F cd2|varchar(40)||ka_button|kdbt_spalte_nr
@F cd2|varchar(40)||kunde_auf_txt|zeile_nr
@F cd2|varchar(40)||kunde_vkkondgr|kundevkkondgr_cd
@F cd2|varchar(40)||preisli|kassa_jn / Bei n werden auf der Kassa alle Datensätze in der Tabelle vkkond_preis mit dieser Preisliste gelöscht / Bei j werden alle Datensätze in der Tabelle vkkond_preis aus der Warenwirtschaft in die Kassen-Datenbanken übertragen
@F cd2|varchar(40)||tax_free|ab_betrag
@F cd2|varchar(40)||vkkond_preis|preisli_cd
@F cd2|varchar(40)||waehrung_kurs|von_dat
@F cd2|varchar(40)||pfu_amenu_sprache|sprache_cd
@F cd2|varchar(40)||pfu_berecht|bertr_snr
@F cd2|varchar(40)||pfu_bertr_col|col_name
@F cd2|varchar(40)||pfu_col_sprache|sprache_cd
@F cd2|varchar(40)||pfu_darsch_fdarst|fdarst_cd
@F cd2|varchar(40)||pfu_darschzu|mde_jn
@F cd2|varchar(40)||pfu_dwo_lablemap|col_name
@F cd2|varchar(40)||pfu_gridschema_col|col_name
@F cd2|varchar(40)||pfu_menui_sprache|menui_name
@F cd2|varchar(40)||pfu_sprache_txt|von_txt
@F cd2|varchar(40)||pfu_usrgrp_map|mfa1_nr
@F cd2|varchar(40)||pfu_win_ctrltxt|sprache_cd
@F cd2|varchar(40)||pfu_win_qcol|q_col_name
@F cd2|varchar(40)||pfu_win_qcol_pwin|q_col_name
@F cd2|varchar(40)||pfu_win_qmap|winmodus
@F cd2|varchar(40)||pfu_win_qmap_col|winmodus
@F cd2|varchar(40)||pfu_win_qtab|tabname
@F cd2|varchar(40)||pfu_win_verarbart|verarbart_kz
@F cd2|varchar(40)||pfu_winmodus|winmodus
@F cd2|varchar(40)||pfu_serial|snr
@F cd2|varchar(40)||pfu_berechtigung|id_name
@F cd2|varchar(40)||pfu_default|w_name
@F cd2|varchar(40)||pfu_kz|kz_wert
@F cd2|varchar(40)||pfu_proglist|id_nr
@F cd2|varchar(40)||pfu_userconst|aot
@F cd3|varchar(40)||artikid|artikid.mach_uni
@F cd3|varchar(40)||ka_host|hostname
@F cd3|varchar(40)||nummern|Nummernkreis / Es werden keine Updates geschickt
@F cd3|varchar(40)||vkkond_preis|ab_dat
@F cd3|varchar(40)||pfu_menui_sprache|sprache_cd
@F cd3|varchar(40)||pfu_sprache_txt|kontext_fcd
@F cd3|varchar(40)||pfu_usrgrp_map|mfa2_nr
@F cd3|varchar(40)||pfu_win_ctrltxt|ctrlname
@F cd3|varchar(40)||pfu_win_qcol_pwin|p_w_name
@F cd3|varchar(40)||pfu_win_qmap|parent_w_name
@F cd3|varchar(40)||pfu_win_qmap_col|parent_w_name
@F cd3|varchar(40)||pfu_serial|kassa_nr
@F cd3|varchar(40)||pfu_berechtigung|teil_id_name
@F cd3|varchar(40)||pfu_default|dw_name
@F cd3|varchar(40)||pfu_progteil|teil_id_name
@F cd3|varchar(40)||pfu_query|kommando
@F cd3|varchar(40)||pfu_gridschema_col|col_name
@F cd3|varchar(40)||pfu_userconst|aeo
@F cd4|varchar(40)||artikid|artikid.artikid_cd (kann in TC.Next 160 Stellen haben)
@F cd4|varchar(40)||vkkond_preis|ab_mg
@F cd4|varchar(40)||pfu_default|col_name
@F cd4|varchar(40)||pfu_usrgrp_map|mfa3
@F cd4|varchar(40)||pfu_win_ctrltxt|subctrl_name
@F cd4|varchar(40)||pfu_win_qmap|usr_cd
@F cd4|varchar(40)||pfu_win_qmap_col|usr_cd
@F cd4|varchar(40)||pfu_query|zeile_nr
@F cd5|varchar(40)||cd5 pfu_usrgpr_map usrgrp_cd / cd5 pfu_win_qmap_col q_col_name / Dummy Felder für individuelle Ableitungen mit mehr Primary Keys
@F cd6|varchar(40)||cd5 pfu_usrgpr_map usrgrp_cd / cd5 pfu_win_qmap_col q_col_name / Dummy Felder für individuelle Ableitungen mit mehr Primary Keys
@F cd7|varchar(40)||cd5 pfu_usrgpr_map usrgrp_cd / cd5 pfu_win_qmap_col q_col_name / Dummy Felder für individuelle Ableitungen mit mehr Primary Keys
@F cd8|varchar(40)||cd5 pfu_usrgpr_map usrgrp_cd / cd5 pfu_win_qmap_col q_col_name / Dummy Felder für individuelle Ableitungen mit mehr Primary Keys
@F err_txt|varchar(255) +n||Fehlertext
@E
@I index i1_ka_datueb (kassa_nr, ka_datueb_snr)
@T index i2_ka_datueb (tabname, cd1, cd2, cd3, cd4)
@F Haupt|Haupt Mandant||Haupt Filiale|Neben|TC
@F artikel|X|
@F artikel_ean|X|
@F artik_txt|X|
@F artik_set|X|
@F auf|X|
@F belart|X|
@F belart_sub|X|
@F belgrp|X|
@F geraet|X|
@F gus|X|
@F eh|X|
@F eh_sprache|X|
@F kassa|X|
@F belkopf|X|
@F ka_kartei|X|
@F kennsatz|X|
@F kunde|X|
@F kunde_auf_txt|X|
@F land|X|
@F mwst|X|
@F muenzli_vg|X|
@F nummern|X|
@F op|X|
@F preisli_prfind|X|
@F sb|X|
@F tax_free|X|
@F txt_txt|X|
@F vkkond|X|
@F vkkond_preis|X|
@F vkkondart|X|
@F waehrung|X|
@F waehrung_kurs|X|
@F zahlung|X|
@F pfu_amenu|X|
@F pfu_amenu_sprache|X|
@F pfu_berecht|X|
@F pfu_bertr|X|
@F pfu_bertr_col|X|
@F pfu_col|X|
@F pfu_col_sprache|X|
@F pfu_darsch|X|
@F pfu_darsch_fdarst|X|
@F pfu_darschzu|X|
@F pfu_dwo_lablemap|X|
@F pfu_fdarst|X|
@F pfu_gridschema|X|
@F pfu_gridschema_col|X|
@F pfu_menu|X|
@F pfu_menui_sprache|X|
@F pfu_sprache|X|
@F pfu_sprache_txt|X|
@F pfu_usergrp|X|
@F pfu_usrgrp_map|X|
@F pfu_win|X|
@F pfu_win_ctrltxt|X|
@F pfu_win_qcol|X|
@F pfu_win_qcol_pwin|X|
@F pfu_win_qmap|X|
@F pfu_win_qcmap_col|X|
@F pfu_win_qtab|X|
@F pfu_win_verarbart|X|
@F pfu_winmodus|X|
@F pfu_serial|X|
@F pfu_berechtigung|X|
@F pfu_default|X|
@F pfu_format|X|
@F pfu_kz|X|
@F pfu_gridschema|X|
@F pfu_gridschema_col|X|
@E
@T ka_dj
@D Kassa – Drucke
@F bel_nr|integer(7)|p1|Belegnummer
@F kassa_nr|smallint(3)|p2,f|Kassennummer
@F lfd_nr|smallint|p3|laufende Nummer
@F txt|varchar(150)||Text
@F txt_kz|char(1)||Textkennzeichen / " " = Normale Textzeile / "k" = Zeile für Kopietext / "i" = Zeile mit Init ESC-Sequenz / "e" = Zeile mit Ende ESC-Sequenz (Cut) / "s" = Seitenwechsel durchführen
@E
@T ka_fa
@D Kassen Firmenstamm (Kennsatz)
@F fa_nr|smallint(3) (p)||Firmennummer
@F gw_waehrung_cd|char(4)|f|Grundwährung
@F zw_waehrung_cd|char(4)|f|Zweitwährung für Info am Kassenbeleg / z.B. / Vor EURO GW = ATS, ZW = EUR / Nach EURO GW = EUR, ZW = ATS / Später GW = EUR, ZW = EUR
@F min_eh|decimal(7,2)||Kleinste Einheit beim Retourgeld
@F tax_free_ab|smallint(4)||Ab Rechnungsbetrag für TAX FREE Logik
@F anz_artik_cd|char(20) +n (f artik)||Artikelnummer Anzahlung / Null = es gibt keine Anzahlungsartikel
@F gus_ab_wt|decimal(5,2)||Ab Betrag für Gutscheine / Ab diesem Betrag werden bei Gutschriften als Zahlungsart Gutscheinverkauf vorgeschlagen
@F gus_zahlung_cd|char(3) +n||Zahlungsart Gutscheinverkauf / Null = Es gibt keinen automatischen Gutscheinverkauf
@F gue_zahlung_cd|char(3) +n||Zahlungsart Gutscheineinlösung / Null = Es gibt keine Gutscheineinlösung mit Barcode
@F skonto_zahlung_cd|char(3) +n||Zahlungsart Skonto / Null = Es gibt keinen Skonto auf der Kassa
@F max_skonto_prz|decimal(4,2)||Maximaler Skontoprozentsatz
@F gew_ean|char(2)||Präfix für Gewichts EAN (3+2 Stellen)
@F stk_ean|char(2)||Präfix für Stk EAN (5stellig ohne Nachkomma)
@F pr_ean|char(2)||Präfix für Preis EAN (3+2 Stellen)
@F kd_ean|char(2)||Präfix für Kundenkarten EAN
@F op_ean|char(2)||Präfix für OP-EAN
@F anz_ean|char(2)||Präfix für Auftragsnummer Anzahlung
@F kom_ean|char(2)||Präfix für Kommissionsschein EAN
@F gus_ean|char(2)||Präfix für Gutschein EAN
@F kartei_symbol|char(3)||Symbol für Kassabuchung in kartei_lagbew
@F fb_bv_sy|char(2)||Fibu Buchungssymbol für Barverkäufe
@F fb_za_sy|char(2)||Fibu Buchungssymobl für Zahlungsbuchung Barverkäufe und Anzahlungen
@F fb_ra_sy|char(2)||Fibu Buchungssymbol für Rechnungsausgleich Zahlungsbuchung
@F artikerl_cd|char(10)|f|Artikelerlöszuordungscode für Rundungsdifferenzen
@F artikkst_cd|char(10)|f|KostenrechnungszuordnungsCode für Rundungsdifferenzen
@F versart_cd|char(5)||Versandart
@F liefbed_cd|char(5)||Lieferbedingung
@F aufeinart_cd|char(10)||Auftragseingangsart
@F op_reo_tg|smallint (3)||Alle Kassen-OP´s deren Belegdatum kleiner (älter) als Tagesdatum minus op_reo_tg ist, werden gelöscht, wenn es sie in den FIBU-OP´s nicht gibt.
@F min_eh_kz|char(1)||KZ für Minimale Einheit/Rundungsdifferenz Behandlung beim Retourgeld / - = Keine Rundungsdifferenz möglich / min_eh ist fix 0 / d = Fix Abrunden (Down) / u = Fix Aufrunden (Up) / k = Fix Kaufmännisch runden / Der Vorgeschlagene oder eingegebene Betrag wird auf min_eh gerundet. / e = lt. Eingabe / Wenn ein Betrag eingegeben wird, der um weniger als min_eh vom vorgeschlagenen Betrag abweicht, wird der Rest als Rundungsdifferenz verbucht.
@F svcsrv_path|varchar(128)||Service Programmstand Server Pfad für Kassa Neu
@F artikbildsrv_path|varchar(128)||Artikel Bilder Server Pfad für Kassa Neu
@F dummy_preisli_cd|char(5)|f|Preisliste die auf der Kassa für Kunden verwendet wird, die eine nicht Kassen Preisliste eingetragen haben. / Muss eine Preisliste mit kassa_jn = "j" sein
@F rksv_aes|char(50)|g|AES Schlüssel für AES256 Verschlüsselung des Umsatzzählers / Eingegeben wird ein 32 Stellen langer Text der dann Base64 verschlüsselt wird. Dieser wird verspeichert. / Darf nicht geändert werden, wenn es eine angemeldete Kassa gibt / 256Bit Schlüssel 32Byte 32 Zeichen (Anm. AKOE)
@F warrify_praefix|Char(20)||Präfix für Warrify, derzeit fix „p=wrfy „
@F warrify_client_id|varchar(255)||Wird für die Generierung eines Warrify Access Tokens verwendet
@F warrify_client_secret|varchar(255)||Wird für die Generierung eines Warrify Access Tokens verwendet
@F qarrify_code_kz|Char(1)||Art des Warrify Codes / g = Gs1 Code 128 / q = QR-Code
@F warrify_ai|Char(10)||Warrify Application ID
@F archiv_sicherheit_tg|smallint||Archivierung Sicherheitstage. Default 9999
@E
@T ka_fibu_erloes
@D Kassa - Fibu - Erlöse / Erlösbuchungen in FIBU für Ausdruck auf Kassa-FIBU Protokoll
@F fibu_bel_nr|integer(7)|p1|FIBU Belegnummer
@F fa_nr|smallint|p2|Firmennummer
@F artikerl_cd|char(10)|p3|Artikelerlöszuordungscode /
@F sh_kz|char(1)|p4|Soll/Haben Kennzeichen
@F erlkto_nr|integer(9)||ErlöskontoNr
@F netto_betrag|decimal(10,2)||Nettobetrag
@F ust_betrag|decimal(10,2)||MwStBetrag
@E
@T ka_fibu_zahl
@D Kassa - Fibu - Zahlungen / Zahlungsbuchungen in FIBU für Ausdruck auf Kassa-FIBU Protokoll
@F fibu_bel_nr|integer(7)|p1|FIBU Belegnummer
@F fa_nr|smallint|p2|Firmennummer
@F lfd_nr|smallint|p3|laufende Nummer
@F debitor_nr|integer(9)||Debitorennummer
@F kunde_mc|char(40)||Kundenmatchcode
@F zahl_bel_nr|integer(7)||Belegnummer des Zahlungsbeleges
@F op_nr|integer(7)||OP-Nummer
@F zahl_betr|decimal(8,2)||Zahlungsbetrag
@F skonto_betr|decimal(8,2)||Skontobetrag
@E
@T ka_geraet
@D Kassen Peripheriegeräte / Die Wartung erfolgt über die Datenbank
@F kassa_nr|smallint(2)|p1,f|Kassennummer
@F geraet_kz|char(4)|p2|Gerätecode / bon = Bondrucker / slip = Slip Drucker (Auf PosKassa nicht verfügbar) / lade = Kassenlade / disp = Kassendisplay / kkt = Kredit-/Bankomatkartenterminal / mtw = Mettler Toledo Waage mit Mettler Toledo 8217 Protokoll (nur PosKassa) / a4d = A4 Drucker (Windows Drucker)
@F geraet_bez|char(30)||Gerätebezeichnung
@F device|char(70)||Ausgabe Device (z.B. com1:) / Bei Windows—Drucker oder USB der Windows Druckername
@F init_cmd|char(70)||Init Kommando / bei mtw / „sofort“ – es wird nach Eingabe Artikelnummer der Wagenstand abgelesen / „abruf“ – es wird Mittels Button das Wagenstand ausgelesen
@F ende_cmd|char(70)||Ende Kommando
@F anschluss_kz|char(1)||p = Parallel (nicht auf der Pos Kassa) / s = Seriell / ist Bei Kreditkarten-/Bankomatterminal EPS42/48 Protokoll / f = File Ausgabe wird in ein File umgeleitet (Bei Pos Kassa - Gerät nicht aktiv) / d = Windows-Drucker (nicht auf der Pos Kassa)kd / wird standardmäßig nicht angeboten, da im Falle der Verwendung auf jeden Fall der Belegdruck auf der Kassa übersteuert werden muss / o = OPOS Treiber (nur Pos Kassa) / v = VGA (für 2. Bildschirm – nur Pos Kassa) / u = USB (nur Pos Kassa) / m = MPD- Kreditkarten/Bankomat MultiProtocalDriver / Internationale Version der SIX (Paylife) Anbindung
@F baudrate_kz|integer||Baud Rate für serielle Schnittstelle
@F bytesize_kz|smallint(1)||ByteSize für serielle Schnittstelle
@F parity_kz|smallint||0 = Keine / 1 = Even / 2 = Odd / 3 = Mark
@E
@T ka_gus
@D Kassen Gutscheine
@F gus_nr|char(40)|p1|Gutscheinnummer
@F fa_nr|smallint(3)||Firmennummer / Ist die Firma die den Gutschein ausgegeben hat / Im Standard, kann der Gutschein auch nur in dieser Firma eingelöst werden
@F gus_betr|decimal(10,2)|g|Gutscheinbetrag in Grundwährung / Ist die Summe auf ka_gus_trans.trans_betr_gw mit reserv_kz = 'b' / Für die Prüfung des noch offenen Gutscheinbetrages müssen noch die ka_gus_trans Positionen mit reserv_kz = "r" mitgerechnet werden.
@F ausg_betr|decimal(10,2)||Ausgabebetrag des Gutscheines in Grundwährung / ist der gus_betr beim ersten Verkauf
@F gus_zustand_kz|char(1)||o = offen (gus_betr <> 0) / v = Vollständig eingelöst / n = Noch nicht verkauft (ist noch nicht umgesetzt)
@F teileinloesen_jn|Char(1)||Gutschein darf auf Kassa Teil eingelöst werden / Default nein für Bestandsdaten
@E
@N i1_ka_gus (gus_zustand_kz, fa_nr)
@T ka_gus_trans
@D Gutschein Transaktion
@F ka_gus_trans_nr|Integer identity|p1|Interne SNR
@F gus_nr|char(40)|f
@F trans_bel_nr|Integer||Belegnummer / Kassa – Belegnummer / WebShop – magento_bestell.magento_entity_id / Sonst (Datueb, Bonusgutschriften …) – 0 oder ?
@F kassa_nr|Integer||Kassa – Kassennummer / Sonst 0
@F trans_datz|Datetime +n|
@F trans_betr_gw|Decimal(11,2)||Transaktionbetrag, positiv bei Verkauf, Negativ bei Einlösung oder Reservierung
@F reserv_datz|datetime +n||Reservierungszeitpunkt / Wird nur vom WebShop verwendet
@F reserv_kz|char(1)||Transaktion ist eine Reservierung, wird auf n updgedate, wenn aus der Reservierung eine fixe Transaktion wird. / b = Buchung (keine Reservierung oder Reservierung bestätigt) / r = Reservierung (WebShop Auftrag hat Gutschein Reserviert, der ist / x = Stornierte Reservierug / Damit ist es möglich, dass über den Reservierungszeitpung alte offene Reservierungen wieder gelöscht werden.
@F trans_herkunft_kz|Char(1)||s = Shop / k = Kassa / t = TradeControl (manuelles Einlösen über Extramenü) /
@F transart_kz|char(1)||a = Ausgabe / e = Einlösen / w = Weitere Aufladung
@E
@I Index i1_ka_gus_trans (gus_nr, trans_bel_nr, kassa_nr)
@T ka_gusformat
@D Kassen Gutscheinformate / Notwendig für die Definition welche im Artikel-Scanfeld eingegebenen Werte als Gutscheinnummern interpretiert werden sollen / Die alte EAN Logik muss hier nicht abgebildet werden / Wird von ka_zahlung bei Eingabe einer gusnr_syntax generiert kann aber auch manuell gewartet werden / Wird auf alle Kassen lt. fa_nr übertragen
@F ka_gusformat_snr|smallint (p)||laufende Nummer
@F fa_nr|smallint(3)|f|Firmennummer
@F gusnr_lng|smallint||Länge des Gutscheincodes
@F gusnr_praefix|varchar(20)||Präfix
@F gusformat_info|varchar(200)||Infotext / Bei Automatischer Anlage aus ka_zahlung: "Zahlungart: <zahlart_cd>"
@E
@T ka_host
@D Kassen Host-Zuordnung / Zuordnung eines Hosts zu einer Kassa für Kassa Light
@F hostname|char(40) (p)|f
@F kassa_nr|smallint(3)|f|Kassennummer
@E
@T ka_kabst
@D Kassa - Kassenbestandsgruppe
@F ka_kabst_cd|char(5)|p1|Kassa - Kassenbestandsgruppencode
@F fa_nr|smallint(3)|p2,f|Firmennummer
@F ka_kabst_mc|char(40)|
@E
@T ka_kartei
@D Kassenkartei (Zahlungskopf)
@F bel_nr|integer(7)|p1|Belegnummer
@F fa_nr|smallint (3)|f|Firmennummer
@F kassa_nr|smallint(2)|f,p2|Kassennummer
@F bel_art|char(1)||Buchungssymbol / b = Barverkauf / k = Kassenaus- bzw. Eingang / a = Anzahlung / r = Rechnungsausgleich
@F bel_art_sub_cd|char(2)|f|Kasseneinausgangsartcode
@F bel_dat|date||Belegdatum
@F bel_zeit|datetime HHMM||Uhrzeit
@F sb_cd|char(5)|f|Sachbearbeitercode
@F betrag|decimal(8,2)||Gesamtbetrag in Grundwährung
@F rund_diff|decimal(6,2)||Rundungsdifferenz
@F retourgeld|decimal(8,2)||Retourgeld
@F text_1|char(30)||Buchungstext
@F text_2|char(60)||Buchungstext
@F text_3|char(60)||Buchungstext
@F fibu_bel_nr|integer(7)||Beleg in FIBU gebucht / 0 = noch nicht in FIBU Gebucht / -1 = wird gerade gebucht
@F kfbueb_job_nr|decimal(14,0)||aktuelle Fibuüberleitungsjobnummer / notwendig für Restart
@E
@I index i1_ka_kartei (fibu_bel_nr)
@I index i2_ka_kartei (bel_dat, kassa_nr, sb_cd)
@T ka_kartei_zp
@D Kassenkartei Zahlungspositionen
@F bel_nr|integer(7)|p1,f|Belegnummer
@F kassa_nr|smallint(3)|p2|Kassennummer
@F pos_nr|smallint|p3|interne Positionsnummer
@F zahlung_cd|char(3)|f|Zahlungscode
@F fa_nr|smallint|r|Firmennummer für Join Zahlungsart
@F betrag|decimal(8,2)||Zahlungsbetrag
@F waehrung_cd|char(4)|f|Fremdwährungscode
@F betrag_gw|decimal(8,2)||Betrag in Grundwährung
@F gus_nr|char(40)||Gutscheinnummer / Bei Zahlungsart Gutschein (Einlösen oder Verkauf), sonst 0 oder blank
@F kkg_name|varchar(64)||Name der Kreditkartengesellschaft / MPD: ApplicationName
@F kk_nr|varchar(32)||Kreditkartennummer inkl. Ablaufdatum / MPD: CardNumber
@F kkg_uid|varchar(16)||Kreditkartengesellschaft UID (Vertragspartnernummer) / MPD: BrandId
@F kkt_nr|varchar(12)||Terminalnummer der Kreditkartenaplikation / MPD: TerminalId
@F kk_bel_nr|integer(6)||Kreditkartenbelegnummer / MPD: Actseq
@F kk_gen_nr|varchar(6)||Kreditkarten Genehmigungsnummer / MPD: AuthCode
@F kk_txt|varchar(64)||Text der Kreditkartentransaktion / MPD: AuthText
@F kk_ergebnis|varchar(40)||Ergebnistext der Kreditkartentransaktion / MPD: RefNumber
@F kk_betrag|varchar(8)||Betrag der Kreditkartentransaktion
@F kk_lese|char(1)||Herkunfstbestimmung der Kartendaten / m = MPD Protokoll
@F kk_duplikat|char(1)|
@F kk_ref_bel|integer(6)||Referenzbeleg für Andruck am Beleg
@F kk_ref_bet|varchar(8)||Referenzbetrag für Andruck am Beleg
@E
@T ka_kartei_zp_txt
@D Kassenkartei Zahlungspositionen Kreditkarten Belegtexte
@F bel_nr|integer(7)|p1|Belegnummer
@F kassa_nr|smallint(3)|p2|Kassennummer
@F pos_nr|smallint|p3,f|interne Positionsnummer
@F zeile_nr|smallint|p4|Zeilennummer
@F kk_bel_txt|varchar(150)||Kreditkartenbelegtextzeile
@E
@T ka_ladeopen
@D Kassa – Ladenöffnungen / Wird bei jeder Ladenöffnung erstellt (in einer eigenen Transaktion – wenn der entsprechende Nummernkreis vorhanden ist)
@F kassa_nr|smallint|p1|Kassennummer
@F ka_ladeopen_nr|integer|p2|laufende Nummer / Vergabe lt. nummern
@F ladeopen_datz|datetime||Datum/Uhrzeit
@F sb_cd|char(5)||Sachbearbeitercode
@F bezbel_nr|integer(7)||Belegnummer / 0 = ohne Bezug (z.B. Barverkauf wurde wieder abgebrochen)
@F bezbelart_kz|char(1)||bel_art bei Barverkauf und Div/EinAusgang / M = Münzliste
@E
@T ka_mwst
@D Kassen MwSt Prozentsätze
@F mwst_cd|smallint (p)||MwSt Code
@F mwst_proz|decimal(4,2)||Mehrwertsteuerprozentsatz
@F rksv_ust_kz|char(1)||Registrierkassenverordnung Ust-KZ für Ausgabe Ust in Datenerfassungsprotokoll / 1 = Normal (20%) / 2 = Ermäßigt 1 (10%) / 3 = Ermäßigt 2 (13%) / 4 = 0 % / 5 = Besonder (alle anderen)
@F esr_taxg_fk1|char(1)||ESR TaxGroup für Deutsche TSE / A = Normal (19 %) / B = Ermäßigt (7 %) / C = Durchschnittssatz §24(1)Nr. 3 UStG (10,7 %) / D = Durchschnittssatz §24(1)Nr. 1 UStG (5,5 %) / E = Nicht Steuerbar (0%) / F = Umsatzsteuerfrei (0%) / G = Umsatzsteuer nicht ermittelbar (0%)
@F mwst_kz|char(1)||Ust-Symbol für Bondruck
@E
@T ka_mzl
@D Münzliste
@F muenzli_nr|integer(7)|p1|Münzlistennummer
@F kassa_nr|smallint(2)|p2,f|Kassennummer
@F mzl_dat|date||Datum des Ausdruckes
@F mzl_zeit|datetime HHMM||Uhrzeit des Ausdruckes
@F sb_cd|char(5)|f|Sachbearbeitercode
@F mzl_tagabsch_jn|char(1)||Kenneichen "kassa.tagabsch_jn" (vom Kassen-Datenbestand) zum Zeitpunkt der Erstellung der Münliste.
@F mzl_zust_kz|char(1)||Zustand der Münzliste / e = erfasst, kein Tagesabschluß (Mzl kommt von Kassa) / a = Abschöpfung fehlt (Tagesabschluß aber erstellt) / t = Tagesabschluß vollständig / s = Storniert
@F mzl_sollbestand|decimal(12,2)||Soll-Kassenbestand
@F ka_kabst_cd|char(5)||Kassenbestandgruppencode (zum Joinen auf ka_bst)
@F fa_nr|smallint(3)||Firmennummer (zum Joinen auf ka_bst)
@F ka_sbbst_cd|char(5)||Sachbearbeiter Kassenbestandsgruppencode (zum Joinen auf ka_bst)
@E
@I index i1_ka_mzl (mzl_dat, kassa_nr, sb_cd)
@T ka_mzl_pos
@D Münzlistenposition
@F muenzli_nr|integer(7)|p1,f|Münzlistennummer
@F kassa_nr|smallint(3)|p2|Kassennummer
@F pos_nr|smallint(3)|p3|interne Positionsnummer
@F zahlung_cd|char(3)|f|Zahlungscode
@F fa_nr|smallint|r|Firmennummer
@F einheit|decimal(8,2)||Einheit lt. muenzli_vg (sonst 1)
@F anzahl|decimal(8,2)||eingegebene Anzahl bzw. Betrag
@F betrag_gw|decimal(8,2)||Betrag in Grundwährung
@E
@T ka_mzl_absch
@D Münzlistenposition Abschöpfung
@F muenzli_nr|integer(7)|p1,f|Münzlistennummer
@F kassa_nr|smallint(3)|p2|Kassennummer
@F einheit|decimal(8,2)|p3|Einheit
@F zahlung_cd|char(3)|f|Zahlungscode
@F fa_nr|smallint|r|Firmennummer
@F anzahl|decimal(8,2)||eingegebene Anzahl bzw. Betrag
@F betrag_gw|decimal(8,2)||Betrag in Grundwährung
@E
@T ka_mzlvg
@D Münzliste - Vorgabewerte
@F fa_nr|smallint(3)|f,p1|Firmennummer
@F lfd_nr|smallint(3)|p2|interne laufende Nummer
@F zahlung_cd|char(3)|f|Zahlungscode
@F einheit|decimal(8,2)||Einheit (z.B. 0,10 ATS, 0,50 ATS, 1 ATS, 5 ATS .....)
@E
@T ka_op
@D Kassa - Offene Posten / Wird vom Rechnungsaufbau erzeugt, wenn lt. Zahlungsart aktiviert. / Satz wird beim Tagesabschluss gelöscht, wenn Satz in fb_op ausgeglichen ist
@F op_nr|integer(8)|p1|OP Nummer
@F fa_nr|smallint(3)|p2
@F kunde_cd|char(10) (f kunde)||Kundennummer
@F off_betr|decimal(11,2)||Offener Betrag
@F re_betr|decimal(11,2)||Rechnungsbetrag
@F op_dat|date||Belegdatum
@F skonto1_prz|decimal(4,2)||1. Skontoprozentsatz
@F skonto1_tg|smallint(3)||dazu Ziel- Tage
@F skonto2_prz|decimal(4,2)||2. Skontoprozentsatz
@F skonto2_tg|smallint(3)||dazu Ziel- Tage
@F netto_tg|smallint(3)||Ziel- Tage für Netto- Zahlung
@F valuta_dat|date||Valutadatum für Einzelrechnung
@F faell_dat|date||Fälligkeitsdatum
@F skfaeh_betr|decimal(11,2)||Skontofähiger Betrag
@F name_1|char(50)||Kundenname 1
@F name_2|char(50)||Kundenname 2
@F name_3|char(50)||Kundenname 3
@F strasse|char(50)||Straße
@F land_cd|char(3)|f|Ländercode
@F plz|char(10)||Postleitzahl
@F ort|char(50)||Ortsbezeichnung
@E
@I index i1_ka_op (kunde_cd, fa_nr, op_dat)
@T ka_rksvdep
@D RKSV Datenerfassungsprotokoll
@F kassa_nr|smallint|p1,f|Kassennummer
@F dep_snr|bigint|p2|laufende Nummer
@F dep_datz|datetime||Zeitpunkt der Buchung (Datenbankdefault) / ESR/TES: Belegendezeitpunkt
@F bel_nr|integer||Belegnummer / Kann bei Fehlerhaften/abgebrochenen ESR/TES Belegen auch 0 sein
@F dep_string|varchar(2000)||DEP String / ESR/TES: QR-Code
@F export_job_snr|decimal(14,0)||Jobnummer Sicherungs-Export / 0 wenn noch nicht gesichert
@F rksv_id_sub_nr|smallint||Subnummer der RKSV-Kassen-ID / Kassen ID im Sinn des RKSV = <kassa_nr> [S<rksv_id_sub_nr>(nur wenn <> 0)] / Z.B. 25 oder 1S3
@F tse_status_kz|char(1) +n||Status der TSE/ESR Transaktion / Null = RKSV Transaktion (keine ESR/TSE) / b = Begonnen – noch offen (wawi_kz = B) / e = Erfolgreich abgeschlossen / f = Mit Fehler abgeschlossen / s = Storniert durch automatisches Storno nach Programmabsturz
@F tse_start_datz|datetime +n||Startzeitpunkt lt. TSE
@F tse_tid|integer +n||TransaktionsID lt. TSE
@F tse_rc|char(3) +n||TSE Returncode
@F tse_errorcode|varchar(30) +n||Errorcode
@F tse_usermessage|varchar(500) +n||Fehlertext
@E
@I index i1_ka_rksvdep (export_job_snr, kassa_nr)
@I index i2_ka_rksvdep (bel_nr, kassa_nr)
@T ka_rksvdep_label
@D ESR Label Tags zum Andruck am Beleg
@F kassa_nr|smallint|p1
@F dep_snr|bigint|p2,f|laufende Nummer
@F zeile_nr|smallint|p3|Zeilennummer
@F tag_name|varchar(30)||Name aus Tag Element
@F tag_label|varchar(20)||Label aus Tag Element
@F tag_value|varchar(500)||Value aus Tag Element
@E
@T ka_rksvgrp
@D RKSV Gruppe / Notwendig für Zugriff auf FION RKSV-Dienste / Im Nomalfall gibt es einen Datensatz pro ka_fa / Mehrere Datensätze sind nur dann notwendig, wenn über einen Mandanten im TC mehrere Firmen bei FION zu verwalten sind
@F fa_nr|smallint|p1,f|Firmennummer
@F rksvgrp_cd|char(5)|p2|RKSV-Gruppencode
@F rksvgrp_mc|char(40)||RKSV-Gruppenmatchcode
@F rksv_fion_tid|varchar(128)||RKSV Finanz-Online Teilnehmer-Identifikation des Übermittlers
@F rksv_fion_benid|varchar(128)||RKSV Finanz-Online Benutzer-Identifikation des Webservice-Benutzers
@F rksv_fion_pin|varchar(256)||RKSV Finanz-Online Benutzer-Pin
@E
@T ka_rksvseh
@F ka_datueb lt. fa|RKSV Signaturerstellungseinheit (SEH) / * = Änderung nur bei "Nicht in Betrieb" möglich|
@F rksvseh_cd|char(20) (p)||Signaturerstellungseinheit Seriennummer im Hex Format / Zertifikat Seriennummer im Hex-Format / Es dürfen nur die Zeichen 0-9 und A-F verwendet werden
@F fa_nr|smallint(3) *||Firmennummer / SEH ist dieser Firma zugeordnet / Kann nicht geändert werden, wenn die SEH angemeldet ist
@F vda_id|char(3) *||ID des Zertifikateausstellers / "AT1" = A-Trust (Vorläufig ist nur dieser Wert verfügbar)
@F rksvseh_status_kz|char(1)||Status der RKSV SEH / 'n' = Nicht in Betrieb / 'r' = Registriert / 'a' = Ausfall
@F reg_datz|datetime +n|g|Zeitpunkt der Registrierung der Signatureinheit auf Finanz-Online / Wenn nicht Null, dann ist die SEH angemeldet (*)
@F ausfall_datz|datetime +n|g|Ausfall/Abgemeldet seit Datum/Uhrzeit
@F rksvseh_ausfall_kz|smallint||Ausfall Begründung für FinanzOnline SST / 0 = Kein Ausfall / 1 = Diebstahl oder sonstiger Verlust / 2 = Signaturerstellung unmöglich oder fehlerhaft / 99 = Sonstiger Grund
@F rksv_ende_kz|smallint||Außerbetriebnahme Begründung für FinanzOnline SST / 0 = " " / 6 = Planmäßige Außerbetriebnahme / 7 = Außerbetriebnahme aufgrund eines irreparablen Ausfalls
@F rksvseh_info|varchar(256)||Infotext
@F rksvgrp_cd|char(5) *|f|RKSV-Gruppencode
@E
@T ka_sb
@D Kassen-Sachbearbeiter / Es gibt einen Dummy Sachbearbeiter mit sb_cd = ''. / Ist notwendig für RKSV-Belege wenn kein SB-Vorgeschlagen wird. / Dieser darf über das Verwaltungsprogramm nicht gelöscht werden. Es kann aber die Kassen-Sachbearbeitergruppe geändert werden.
@F sb_cd|char(5) (p)||Sachbearbeitercode
@F sb_name|char(30)||Sachbearbeiter Name
@F usr_login|char(20)||Windows Login
@F ka_sbbst_cd|char(5)|f|Sachbearbeiter Kassenbestandsgruppe / Zur Definition, auf welcher Ebene der Kassen Anfangsbestand geführt wird. siehe ka_bst
@F id_fcd|char(20)||Freier Identifikationscode für HW-Identifikation
@F gen_jn|char(1)||Genehmigungsberechtigt
@F sprache_cd|char(5)|
@F aktiv_jn|Char(1)||Sachbearbeiter ist aktiv
@E
@I unique index i2_sb usr_login
@N Usergruppen werden über ein neues Register verwaltet, welches siche auf die kap_usrgrp_map bezieht, achtung auf unterschiedliche pkey.
@T ka_sbbst_cd
@D Sachbearbeiter Kassenbestandsgruppe
@F ka_sbbst_cd|char(5) (p)||Sachbearbeiter Kassenbestandsgruppencode
@F ka_sbbst_mc|char(40)|
@E
@T ka_sql_update_stmt
@D DB Update Statements für Kassen Releaseupdates
@F updstmt_snr|bigint (p)|
@F rel_fcd|nvarchar(40)||Releasecode / Format: JJJJMMTTx
@F sql_stmt|nvarchar(max)||SQL-Statement
@F rel_ablstufe_nr|smallint||Stufe der Ableitung / 0 = TC Basis / 1 = 1. Ableitung (z.B. Farben, L.Reiter) / 2 = 2. Ableitung (z.B. Morscher der von Farben abgeleitet ist)
@E
@T ka_sqlcmd
@D Kassa SQL Kommandos
@F ka_sqlcmd_snr|integer (p)||Vergabe pfu_serial
@F ka_sqlcmd_stmt|varchar(4000)||SQL Statement
@E
@T ka_tagab
@D Kassa – Tagesabschlusskopfdaten
@F ka_kabst_cd|char(5)|p1|Kassenbestandgruppencode
@F fa_nr|smallint(3)|p2|Firmennummer
@F ka_sbbst_cd|char(5)|p3|Sachbearbeiter Kassenbestandsgruppencode
@F tagesdatum|date|p4|Datum des Kassenabschlusses
@F anfangsbestand|decimal(11,2)||Kassenlade Bargeld Anfangsbestand
@F endbestand|decimal(11,2)||Kassenlade Bargeld Endgestand
@F tagesumsatz|decimal(11,2)||Tagesumsatz (Barverkäufe + Anzahlungen)
@F lfs_wert|decimal(11,2)||Wert der Lieferscheine
@F von_muenzli_nr|integer||1. Münzlistennummer des Tages
@F bis_muenzli_nr|integer||letzte Münzlistennummer des Tages
@F ka_tagabsch_jn|char(1)||Tagesabschluss auf dem KassenPc durchgefüht j/n
@F mzl_wert|decimal(11,2)||Wert der Münzliste (= bis_muenzli_nr)
@F rund_diff|decimal(11,2)||Summe der Rundungsdifferenzen
@F anz_erhalten_wt|decimal(11,2)||Anzahlung Erhalten / Wert der Anzahlungsbelege / Nur bei Touch Version im Einsatz
@F anz_eingeloest_wt|decimal(11,2)||Anzahlung Eingelöst / Wert der Anzahlungsartikel in den Barverkäufen * -1 (wird aus dem Tagesumsatz rausgerechnet. / Nur bei Touch Version im Einsatz
@E
@T ka_tagab_belgrp
@D Kassa – Tagesabschluss - Belegarten
@F ka_kabst_cd|char(5)|p1|Kassenbestandgruppencode
@F fa_nr|smallint(3)|p2|Firmennummer
@F ka_sbbst_cd|char(5)|p3|Sachbearbeiter Kassenbestandsgruppencode
@F tagesdatum|date|f,p4|Datum des Kassenabschlusses
@F belgrp_cd|char(5)|f,p5|Beleggruppencode
@F anzbel|integer||Anzahl der Belege
@F saldo|decimal(11,2)||Positionssaldo
@E
@T ka_tagab_belgrp_za
@D Kassa – Tagesabschluss - Belegarten
@F ka_kabst_cd|char(5)|p1|Kassenbestandgruppencode
@F fa_nr|smallint(3)|p2|Firmennummer
@F ka_sbbst_cd|char(5)|p3|Sachbearbeiter Kassenbestandsgruppencode
@F tagesdatum|date|p4|Datum des Kassenabschlusses
@F belgrp_cd|char(5)|f,p5|Beleggruppencode
@F zahlung_cd|char(3)|f,p6|Zahlungscode
@F eingang|decimal(11,2)||Summe Kasseneingang
@F ausgang|decimal(11,2)||Summe Kassenausgang
@E
@T ka_taxfree
@D TAX-Free Staffeln / Wird nicht mehr an Kassa übertragen -. kann bei nächster Gelegenheit entfernt werden.
@F mwst_cd|smallint(1)|p1,f|Mehrwertsteuerkennzeichen (1-3)
@F ab_betrag|integer(5)|p2|Ab Bruttobetrag
@F rueckerst|decimal(8,2)||Rückerstattungswert bzw. Prozentsatz
@F wp_kz|char(1)||w = Wert / p = Prozentsatz
@E
@T ka_txt
@D Kassen-Textbaustein
@F ka_txt_cd|char(10)|p1|Textbausteincode
@F ka_txt_mc|varchar(40)||Matchcode
@E
@T ka_txt_txt
@D Kassen-Textbaustein- Textzeile
@F ka_txt_cd|char(10)|p1|Textbausteincode
@F zeile_nr|smallint|p2|Zeilennummer
@F sprache_cd|char(5)|f|Sprachencode
@F fett_jn|char(1)||Fettdruck
@F unterstrichen_jn|char(1)||unterstrichen drucken
@F ka_txt|varchar(56)||Text
@E
@T ka_waageprot
@D Kassen-Waagenprotokoll
@F kassa_nr|smallint|p1|Kassennummer
@F wiege_datz|datetime|p2|Zeitpunkt der Wiegung
@F gewicht_kg|decimal(8,3)||Gewicht in KG
@F wiegefehler_jn|char(1)||Es wurde ein Wiegefehler von der SST retourniert
@F waage_rohdaten|varchar(255)||Von der SST übermittelter Datenstring
@E
@T ka_ueb_err
@D Kassa - Hilfstabelle für Protokolldruck Verbuchen Kassa in TC / Inhalt nur temporär, wird nach Druck des Protokolls wieder gelöscht
@F job_snr|integer(8)|p1
@F bel_nr|integer(7)|p2|Belegnummer
@F kassa_nr|smallint(3)|p3|Kassennummer
@F pos_nr|smallint|p4|interne Positionsnummer
@F fehler_txt|char(100)||Fehlertext
@E
@T ka_zahlung
@D Kassa-Zahlungsarten
@F zahlung_cd|char(3)|p1|Zahlungscode
@F fa_nr|smallint|p2|Firmennummer / Notwendig wenn Sprache und/oder Währung in den Firmen unterschiedlich sind
@F zahlung_bez|char(30)||Zahlungsbezeichnung
@F waehrung_cd|char(4)|f|Fremdwährungscode
@F kea_jn|char(1)||Bei Kasseinein-/ausgang erlaubt J/N
@F min_eh|decimal(7,2)||Minimale Einheit in dieser Zahlungsart / Bei der Zahlungsbuchung wird beim Vorschlagswert auf diesen Wert aufgerundet
@F zahlung_art|char(1)||Zahlungsart / B = Bar in Grundwährung / D = Diverse/Sonstige (Scheck) / E = EPS Universalzahlung (Paylife/SIX) / kann nur bei Online Bankomat verwendet werden / Wenn vorhanden, werden die "K" Zahlungsarten dann nicht angezeigt. / F = Fremdwährung / G = Gutschein / K = Kreditkarten / S = Skonto / U = Übertrag / V = Verkauf von Gutscheinen / Es wird der Gutschein bedruckt / nicht auf Münzliste drucken /
@F skonto_jn|char(1)||Bei dieser Zahlungsart ist Skonto erlaubt
@F autoabsch_jn|char(1)||Automatische Abschöpfung
@F lade_oeffnen_jn|char(1)||Bei dieser Zahlungsart wird die Kassenlade geöffnet
@F zahlung_aktiv_jn|char(1)||Zahlung kann verwendet werden
@F gusdru_kz|char(1)||Kennzeichen Gutscheindruck / b = Bondruck / s = Slip (Individuelle Übersteuerung des Gutscheindruckes notwendig)
@F min_eh_kz|char(1)||KZ für Minimale Einheit/Rundungsdifferenz Behandlung / - = Keine Rundungsdifferenz möglich / min_eh ist fix 0 / Ist diese bei zahlung_art in (K,G,V,S,U) / d = Fix Abrunden (Down) / u = Fix Aufrunden (Up) / k = Fix Kaufmännisch runden / Der Vorgeschlagene oder eingegebene Betrag wird auf min_eh gerundet. / e = lt. Eingabe / Wenn ein Betrag eingegeben wird, der um weniger als min_eh vom vorgeschlagenen Betrag abweicht, wird der Rest als Rundungsdifferenz verbucht.
@F sort_nr|smallint||Sortiernummr für PosTouch Kassa
@F esr_pay_dsc|varchar(30)||Pay Description für TSE EFSTA ESR Schnittstelle
@F von_gus_nr|integer(9) +n||Von Gutscheinnummer / Nur bei zahlungs_art V eingebbar. / Wenn definiert, muss die Gutscheinnummer beim Gutscheinverkauf eingebeben werden / ist momentan nur in der Touch Version verfügbar
@F bis_gus_nr|integer(9) +n||Bis Gutscheinnummer / Muss ausgefüllt sein, wenn die von_gus_nr ausgefüllt ist
@F Warrify_zahlung_kz|Varchar(20)||Bezeichnung für Warrify. Derzeitige Werte: / CASH / CARD / GIFT_CARD / VOUCHER / ONLINE / OTHER
@F teileinloesen_jn|Char(1)||Gilt nur bei Gutscheinverkauf als Datenfeld für verkaufte Gutscheine
@F gusnr_syntax|varchar(128)||Syntax erstellung Gutscheinnummer, folgende / [Ln] = Alphanumerischer Zufallswert in n Wiederholungen (Letter) / [Dn] = Numerischer Zufallswert in n Wiederholungen (Digit) / [Kn] = Kassennummer using n Stellen / [Nn] = Laufende Nr. lt. Nummernkreis using n Stellen /  / Beispiel: ka-[K4]-[L4]-[D4]-[N4] / Könnte also Ergebnis sein: / ka-0001-ARTZ-9875-0047 /  / wenn leer, dann wie bisher rein lt. Nummernkreis /
@F gusdru_barcode_kz|Char(1)||Barcodedruck Gutscheinnummer am Gutscheinbon / Wird nur bei Gutscheinverkauf berücksichtigt / e = EAN, wie bisher / q = QR-Code (Nur bei dieser Variante darf gusnr_syntax eingegeben werden)
@E
@T ka_zahlung_kkzu
@D Kassa-Zahlungsarten – Kreditkartenzuordnung / Es muss entweder kkg_uid <> blank oder mpd_brandid <> 0 sein
@F zahlung_cd|char(3)|p1|Zahlungscode
@F fa_nr|smallint|p2
@F zeile_nr|smallint|p3|Laufende Nummer
@F kkg_uid|varchar(20)||UID für EPS42/48 SST / Muss wenn ungleich blank innerhalb der Firma eindeutig sein
@F mpd_brandid|smallint(3)||Brand ID für MPD SST / Muss wenn ungleich 0 innerhalb der Firma eindeutig sein
@E
@S kap_.....
@N Basis für die kap_... Tabellen ist die pfu_fun 672, vom 25.06.2007
@N Folgende Pfu Tabellen werden für die Kassa getrennt geführt. Die Verwaltung erfolgt auf der Kassa und wird mit Trigger auf alle anderen Kassen übertragen:
@N amenu
@N amenu_sprache
@N berecht
@N bertr
@N betr_col
@N col
@N col_sprache
@N darsch
@N darsch_fdarst
@N darschzu
@N fdarst
@N default
@N dwo_lablemap
@N gridschema
@N gridschema_col
@N kz
@N menu
@N menui_sprache
@N sprache
@N sprache_txt
@N usrgrp
@N usrgrp_map
@N win
@N win_ctrltxt
@N win_qcol
@N win_qcol_pwin
@N win_qmap
@N win_qmap_col
@N win_qtab
@N win_verarbart
@N winmodus
@T kap_serial
@D kap_serial / ierHier Hier werden die letzten Serial Nummern der Kassen verspeichert, daher die Erweiterung des P-Key um die Kassennummer. / Es gibt hier keinen Trigger in TC, diese Daten werden nur bei der Erstbestückung vonTC an die jeweilige Kassa geschickt
@F tabname|char(18)|p1|Tabellenname / pfu_bertr / pfu_gridschema
@F snr|decimal(14,0)|p2|Seiennummer
@F kassa_nr|smallint|p3,f|Kassennummer
@E
@T kartei
@D Buchungsposition (ng) / Die Tabelle kartei gibt es in der DB nicht, das einzige Feld wäre kartei_snr, diese kann aber auch so über pfu_serial mit tabname = "kartei" vergeben werden. Siehe kartei_lagbew.kartei_kz.
@E
@T kartei_duest
@D Buchungsposition: DUEST-Berechnung (g) ~20419 / Zu jeder DUEST Relevanten Buchung gibt es hier einen Datensatz / vlfs_pos (evt. zugang Ware unterwegs) / vlfs_prod / elfs_pos / divlgb (evt. Umbuchungen) / esetp
@F kartei_snr|integer|p1|siehe kartei
@F duestgrp_cd|char(10)|p2|Durchschnittspreisgruppe
@F artik_cd|char(20)|r|Artikelcode
@F fa_nr|smallint|r|Firmennummer
@F kartei_kz|char(1)|r|gibt an, auf welche Art von Buchungszeile sich die aktuelle Row bezieht: / siehe kartei_lagbew
@F kartei_dat|date|r|Lagerbewegungsdatum, abhängig von kartei_kz: / siehe kartei_lagbew
@F alt_lag_mg|decimal(12,3)||Lagerstand vor der Buchung
@F alt_duest|decimal(15,6)||DUEST vor der Buchung
@F bew_mg|decimal(12,3)||Buchungsmenge
@F bew_wt|decimal(11,2)||Buchungswert (Gesamtwert in EUR)
@F neu_duest|decimal(15,6)||DUEST nach der Buchung
@E
@I index i1_kartei_duest (artik_cd, fa_nr, duestgrp_cd, kartei_dat, kartei_snr)
@T kartei_lagbew
@D Buchungsposition: Lagerbewegungen (ng) / hier stehen jeweils die Lagerbewegungen zu je einer Row einer der folgenden Tabellen: / vlfs_pos / vlfs_prod / elfs_pos / divlgb / iv_zeile / esetp / esetp_set / vlfs / Änderungen müssen in Einklang mit der entsprechenden row der entsprechenden table sein. Siehe dazu entsprechende table bzw. die zugehörigen Funktionalitäten.
@F kartei_snr|integer|p1|siehe kartei
@F lag_cd|char(11)|p2
@F lag_ort|char(20)|p3|Lagerort siehe lag.lag_ort_inp_jn
@F charge_geraet|char(40)|p4|Leer, Gerätenummer oder Chargennummer, siehe artik_lag_sub
@F buch_datzeit|datetime|p5|Datum und Uhrzeit der Datensatzanlage / YEAR to Fraction / wird durch Datenbankdefault bei der Neuanlage des Datensatzes automatisch belegt
@F bew_mg|decimal(11,3)||bewegte Menge in Lagereinheit (Minus ist Abgang)
@F ablauf_dat|date +n||Ablaufdatum bei artikel.lagfuehr_kz = 'c' und artikel.ablaufdat_jn = 'j', / sonst NULL
@F kartei_symbol|char(3)||Buchungssymbol für Suche: / Verkauf lt. aufart.kartei_symbol / diverse Lagerbuchung lt. divlgbart.divlgbart_cd / Inventur lt. fa.kartei_symbol_iv / Einkauf lt. fa.kartei_symbol_ek / Gerätausscheiden lt. fa.kartei_symbol_ga / einfache Setproduktion: / "pz" für Zugang / "pa" für Abgang
@F kartei_kz|char(1)|r|gibt an, auf welche Art von Buchungszeile sich die aktuelle Row bezieht: / 'v' Verkauf: vlfs_pos.kartei_snr = kartei_snr / 'p' Produktion: vlfs_prod.kartei_snr = kartei_snr / 'e' Einkauf: elfs_pos.kartei_snr = kartei_snr / 'i' Inventur: iv_zeile.kartei_snr = kartei_snr / 'd' diverseLagerbuchung: divlgb.kdartei_snr = kartei_snr / 's' einfache Setproduktion (esetp) / 'k' Kassa: ka_bel_pos.kartei_snr = kartei_snr / 'a' Serviceauftrag lagerndes Gerät, Abschluss mit "ausscheiden Gerät", vlfs.s_kartei_snr = kartei_snr
@F artik_cd|char(20)|r|= buchungszeile.artik_cd
@F fa_nr|smallint(3)||= buchungszeile.fa_nr
@F kartei_dat|date|r|Lagerbewegungsdatum, abhängig von kartei_kz: / v' vlfs.vlfs_dat / 'p' vlfs.vlfs_dat / 'e' elfs.elfs_dat / 'i' iv.iv_dat / 'd' divlgb.divlgb_dat / 's' esetp.esetp_dat / 'k' ka_bel.bel_dat / 'a' vlfs.vlfs_dat
@F buch_dat|date||= Buchungsdatum (TODAY)
@F geraet_cd|char(40) I||charge_geraet bei artikel.lagfuehr_kz = 'g', sonst blank / Feld ist notwendig, um in der Lagerbewegungsabfrage ins Gerät abzubiegen.
@F kartei_txt|char(beliebig, Standard = ?)||Durch Customizen können hier projektindividuell Daten wie z.B. Kundennummer, Kunden- MC, Lfs- Nr. abgestellt werden, sodaß in der Lagerbewegungsabfrage nicht immer in die Buchungszeile verzweigt werden muß. / Weiters ist es möglich, bei der Altdatenübernahme (Bewegungsdaten) nur die Kartei zu übernehmen und hier die Felder der Kartei des Altsystems einzutragen.
@F applpers_cd|varchar(10) +n||User der die Lagerbuchung durchgeführt hat
@E
@I index i1_kartei_lagbew ( artik_cd, kartei_snr desc, fa_nr )
@I index i3_kartei_lagbew ( artik_cd, charge_geraet, kartei_dat, fa_nr )
@I index i2_kartei_lagbew ( artik_cd, geraet_cd, kartei_dat, fa_nr )
@T kreditor
@D Kreditorendaten / Datensatz wird beim Speichern des Lieferanten angelegt, falls er nicht vorhanden ist / Es gibt pro Firma einen Dummysatz mit kreditor_nr = 0
@F kreditor_nr|integer(9)|p1|Kreditorennummer inkl. Kategorie
@F fa_nr|smallint(3)|p2,f
@F kreditor_mc|char(30)|g|Matchcode / In die Jetfibu werden nur die ersten 15 Stellen übergeleitet
@F kreditor_adr_snr|integer|f
@F kreditor_mc2|char(15)||Matchcode 2 / bei Einsatz von EuroFib im rechten Bildschirmbereich
@F kreditor_mc3|char(15)||Matchcode 3 / bei Einsatz von EuroFib im rechten Bildschirmbereich
@F kreditor_ktobez|char(40)||Kontobezeichnung / wird bei der automatischen Anlage mit adr.name1 + ' ' + adr.plz + ' ' + adr.ort belegt / bei Einsatz von EuroFib im rechten Bildschirmbereich
@F waehrung_cd|char(4)|f|Währung
@F kreditor_divers_jn|char(1)||Kreditor ist divers
@F ustid|char(14)||UST-Identifikationsnummer
@F ustid_dat|datetime +n||UST-Identifikationsnummer - Datum / wird bei der Überleitung in die Jetfibu im Format JJJJMMDD ausgegeben
@F zahlkond_nr|integer|f|Zahlungskondition / F-Key nur in Version ohne Jetfibuintegration vorhanden
@F frktonr|char(15)||Fremdkontonummer
@F zahlungsart_kz|char(3)||Kennzeichen Zahlungsart / bei Jetfibuintegration müssen die Kennzeichen lt jetfibu.anzlgart angelegt werden / bei Einsatz von EuroFib im rechten Bildschirmbereich
@F vorschlag_cd|char(15)||für holen Vorschlagsrecord bei Neuanlage
@F kreda_dat|date||letztes Änderungsdatum des Kreditor / wird bei jedem Speichern mit dem Tagesdatum+Zeit belegt
@N nur für EURO-FIB
@F kod_uid_chk_nr|char(1)||Prüfkennzeichen UID-Datum / 0=ungeprüft / 1= Status 1 - UID ok, Adresse nicht ok / 2 = Status 2 - UID ok, Adresse ok / 3 = ungültig / 9 = ohne UID
@F ustid_ungueltig|char(14)||nur bei ungültiger UID belegt [kod_uid_chk_nr in (1, 3)]
@F kred_uid_job_snr|decimal(14)||Jobnummer letzte Online-UID-Prüfung / fixer Default Neuanlage 0
@F kreditor_dbid|integer identity||ROWID für TcNext / durch DB-Insert mit serieller Nummer belegt
@E
@I unique index i1_kreditor (kreditor_dbid)
@T kreditor_bank
@D Zuordnung Kreditor -> Banken
@F kreditor_nr|integer|p1,f
@F fa_nr|smallint(3)|p2
@F zeile_nr|smallint|p3|lfd. Zeilennummer / Zeile 1 ist Standardbankverbindung / Applikation sortiert nicht
@F bank_land_cd|char(3)|
@F bank_blz|char(11)|f
@F bankkonto|char(20)||Bankkontonummer
@F iban|char(34)||Iban bestehend aus / wird in Fibu übergeleitet (als Kontonummer) / ## Iso-Länderkennzeichen / ## Prüfziffer / ##### Bankleitzahl / ########### Bankkontonr / in Österreich ist die Iban 20-stellig, kann aber je Land anders sein. Max. Länge 34
@F nur für EURO-FIB|bei Einsatz von JetFibu oder BMD-Fibu nicht sichtbar|
@F zah_art|char(1)||Zahlungsart / U=Überweisung / E=Einzug / S=Scheck / L = SEPA-Lastschrift / F = SEPA-Firmenlastschrift
@F zah_aktiv|char(1)||Aktiv im Zahlungsverkehr (J/N)
@F aviso_jn|char(1)||Aviso (J/N)
@F sepa_mandat|char(35)||Sepamandat (Referenznummer)
@F sepa_mandat_ddat|date +n||Mandat Druckdatum
@F sepa_mandat_udat|date +n||Mandat Unterschriftsdatum
@E
@T kreditor_dsgvo
@D DSGVO-Daten Kreditor / View für Generierung Infoblatt Kunde / ist durch Betreuer zu Customizen / im Standard nur "from pfu_selkonst" / Beispiel Verwendung siehe [kunde_dsgvo]
@F kreditor_dbid|integer|p1
@F zeile_nr|integer|p2|Sortiernummer
@F txt1|char(100)||Text1, Label
@F txt2|char(100)||Text2, Wert
@E
@T kreditor_fgr
@D Zuordnung kreditor -> Freie Kreditorengruppe / bei Jetfibuintegration werden hier die scrit*-Felder verwaltet / bei EURO-FIB werden hier die k_sele_*-Felder verwaltet
@F kreditor_nr|integer|p1,f
@F fa_nr|smallint(3)|p2
@F fgrart_cd|char(10)|p3|Code der Art der freien Kreditorengruppe
@F fgr_cd|char(10)|f|Code der freien Kreditorengruppe
@E
@T komber
@D Kommissionsbereich / es gibt einen Dummy-Satz, der im Verwaltungsprogramm nicht sichtbar ist
@F komber_cd|char(10)|p1|es wird je komber_cd ein eigener Kommissionsschein erstellt
@F komber_mc|char(40)|
@F komber_appl_fcd|char(20)||Applikationskennzeichen für Druckzuordnung / Kann auch dazu verwendet werden, um den eigentlichen Ausdruck des KS bei einer MDE Kommissionierung zu unterdrücken
@F komber_upid|bigint +n|
@F kb_mde_jn|char(1)||Kommissionsbereich wird mittels MDE kommissioniert
@F vlfs_autodru_jn|char(1)||Lieferscheine werden nach Abschluss der MDE Kommissionierung automatisch gedruckt
@F komber_upid|bigint +n|
@E
@I index i1_komber_upid (komber_upid)
@T kommvorg
@D Kommissioniervorgang / es gibt einen Dummy-Satz [kommvorg_nr = 0] / wird angelegt, wenn Kommissionierauftrag zu einem Lager mit 2stufiger-Kommissionierung aufgebaut wird oder MDE-Kommissionierung für den entsprechenden Kommissionsbereich aktiv ist / wird im Zuge des Reorgs gelöscht, wenn es keinen Kommissionierauftrag mehr gibt, der den Kommissioniervorgang referenziert / Ist derzeit in TC noch nicht vollständig umgesetzt / Funktioniert nur mit Vorgabe von Lagerortzuweisungen in auf_pos_sub / Job zum Verbuchen in TC fehlt noch
@F kommvorg_nr|bigint|p1|Kommissioniervorgang / Vergabe mittels pfu_serial / = ID für TC.Next
@F fa_nr|smallint||Firma
@F komber_cd|char(10) (f komber)||Kommissionsbereich
@F komber_upid|bigint|
@F erst_datz|datetime||Zeitpunkt der Erstellung
@F min_lief_dat|date||frühestes Lieferdatum
@F kommvorg_mc|varchar(80)|g|Bezeichnung / kann mittels Event individuell belegt werden / Bei Einzelkommissionierung: "AufNr: <AufNr> Kunde: <KundeMc>"
@E
@T kommvorg_auf
@D Kommissioniervorgang – Auftragsbezug / Ist wg. Vorbereitung zum Sammelauftrag eine eigene Tabelle / Ist nicht auf auf_komm da auf_komm mit dem Lieferbeleg gelöscht wird
@F kommvorg_nr|bigint|p1|Kommissioniervorgang / Vergabe mittels pfu_serial / = ID für TC.Next
@F auf_nr|integer|p2|Auftragsnummer
@F fa_nr|smallint|p3|Firmennummer
@F komm_nr|smallint|p4|Kommissionsscheinnummer des Aufrags
@E
@I index i1_kommvorg_auf (auf_nr, fa_nr, komm_nr)
@T kommvorg_bereich
@D Kommissioniervorgang Bereich / es gibt einen Dummy-Satz
@F kommvorg_nr|bigint|p1|Kommissioniervorgang, Dummy: 0
@F fa_nr|smallint||Firma
@F fil_nr|smallint||Filiale
@F fil_upid|bigint +n|
@F kommvorg_bereich_nr|smallint (2)|p2|Kommissioniervorgang Teilbereich, / Dummy: 0 / in TC Fix: 1 / Wird im Baustoff dazu verwendet um eine Sammelkommissionierung über eine maximale Anzahl von Positionen auf mehrere Bereiche auzuteilen.
@F kommvorg_bereich_upid|bigint|g|= kommvorg_nr * 100 + kommvorg_bereich_nr
@F kommvorg_bereich_status_kz|char(1)||KommissioniervorgangBereichStatus / 1 freigegeben / 2 begonnen / 3 pausiert / 5 Verbuchen läuft / 7 Kommissionierung abgeschlossen / 9 Kommissionierung mit Fehler abgeschlossen
@F kommvorg_bereich_status_datz|datetime||Zeitpunkt letzte Statusänderung
@F komm_ks_pers_cd|char(5)||Kommissionierer / Default = " "
@F komm_pos_anz|smallint||Anzahl Positionen
@E
@I index iu_kommvorg_bereich (kommvorg_bereich_upid)
@T kommvorg_pos
@D Kommissioniervorgang Position / ist eine Tabelle für MDE-Kommissionierung / wird bei MDE Kommissionierungen beim Kommissionsscheindruck aufgebaut / wird in TradeControl selbst nicht benötigt (ggf. nur beim Verbuchen aus MDE)
@F kommvorg_pos_upid|bigint|p1|Wenn von TC Erstellt: gf_serial, TC.Next: UPID
@F kommvorg_nr|bigint|f
@F fa_nr|smallint|
@F fil_nr|smallint|
@F fil_upid|bigint +n|
@F kommvorg_bereich_nr|smallint|
@F kommvorg_bereich_lfd_nr|smallint|
@F kommvorg_bereich_upid|bigint|g|= kommvorg_nr * 100 + kommvorg_bereich_nr
@F artik_cd|char(20)|
@F artik_upid|bigint|
@F artik_mc|varchar(60)||Ist für diverse Artikel hier notwendig
@F lag_cd|char(11)|
@F lag_upid|bigint|
@F ko_snr|integer||In TC fix 0
@F lag_ort|char(20)|
@F lag_ort_upid|bigint|
@F soll_komm_mg|decimal(12,3)||zu kommissioniernde Menge / wird mit [kommvorg_zeile.sum_auf_frei_mg] bei der Anlage belegt / wird mit [splitt_mg] bei Splitten der Position belegt
@F leh_cd|char(5)|
@F leh_upid|bigint +n|
@F komm_sort_nr|integer||Sortiernummer lt. Lagerplätzen und Kommissionierklassenfaktor
@F durchgang_nr|smallint||Durchgangsnummer / Wird beim ersten Aufbau mit 0 belegt / Wird bei gesplitteten Position, die auf einen Lagerort mit einer Soriternummer < als die aktuelle Sortiernummer geändert wird um 1 erhöht. / Wird um 1 erhöht, wenn Positionen in der Verarbeitung übersprungen werden.
@F ist_komm_mg|decimal(12,3) +n||kommissionierte Menge / Ist Null solange noch keine Buchung erfolgt ist
@F splitt_mg|decimal(12,3) +n||Menge, welche in eine neue Kommissionierposition übergeben wurde
@F splitt_lag_ort|char(20)||Lagerplatz, von welchem die Restmenge kommissioniert werden muss
@F splitt_lag_ort_upid|bigint|
@F charge_geraet|varchar(60)||Charge-/Geräte
@F komm_datz|datetime +n||Kommissionierzeitpunkt
@F ein_artikid_cd|varchar(200) +n||Eingabe Artikelcode / gescannter Barcode
@F verarb_job_snr|decimal(14,0)||Jobnummer der Verbuchung in TradeControl / 0 = Default
@F auf_pos_upid|bigint||Ist nur bei diversen Artikeln belegt – Zeiger auf die Auftragsposition
@E
@I index i1_kommvorg_pos (kommvorg_nr, kommvorg_bereich_nr, kommvorg_bereich_lfd_nr)
@I index i2_kommvorg_pos (verarb_job_snr, artik_cd, lag_cd, lag_ort) – Notwendig für rasche Ermittlung der reservierten Mengen
@I index i3_kommvorg_pos (kommvorg_nr, artik_cd, auf_pos_upid)
@T komidart
@D Kommunikations- Identifikations- Art / (Haupttelefonnummer, Mobiltelefonnummer, Faxnummer, Emailadresse, ... ) / es gibt einen Dummy-Satz mit komidart_cd = "" für Bestellungen und Aufträge die gedruckt werden
@F komiart_upid|bigint +n|
@F komidart_cd|char(10)|p1
@F komidart_label|char(20)||Name des Feldes auf dem Data Window
@F komidart_kz|char(1)||t=Telefon, f=fax, e=email, i=internet, m=Mobiltelefon
@F outlook_kz|char(10)||Umschlüsselungscode für Zuordnung zu Outlook
@F mach_uni|char(20)||wenn outlook_kz = ' ': komidart_cd || outlook_kz / wenn outlook_kz <> ' ': ' ' || outlook_kz
@F sort_nr|smallint(4)||Sortiernummer
@E
@I unique index i1_komidart (mach_uni )
@T kst
@D Kostenrechnungszuordnung
@F artikkst_cd|char(10)|p1,f|KostenrechnungszuordnungsCode Artikel
@F kundekst_cd|char(10)|p2,f|KostenrechnungszuordnungsCode Kunde
@F kst_nr|integer(9)||Kostenstellennummer
@F koart_nr|integer(9)||Kostenartnummer
@F ktr_nr|integer(9)||Kostenträgernummer
@E
@T kunde
@D Kunden- Stammdaten /  / Beim Speichern werden implizit die Rows in folgenden Tabellen angelegt bzw. geändert / debitor /  / Im Select- Statement der "Liste" muß kunde_fcol mitselektiert werden
@F kunde_upid|bigint +n|
@F kunde_cd|char(10)|p1|Kundennummer / Vergabe/Kontrolle mittels Tabelle nummern /
@F fa_nr|smallint(3)|p2|Firma
@F kunde_mc|char(30)|g|= adr.adr_mc
@F kunde_adr_snr|integer(7)|f|Kundenadresse = Lieferadresse
@F stat_kunde_upid|bigint +n|
@F stat_kunde_cd|char(10)|f|Kunde, welcher statistisch ausgewertet wird
@F preis_kunde_upid|bigint +n|
@F preis_kunde_cd|char(10)|f|Kunde für: / Kundenartikelnummer lt. artikid / Verkaufskondition auf Ebene kunde_cd lt. vkkondart
@F kundeerl_cd|char(10)|f|Kundenerlöszuordnung / bestimmt auch Inland/Eu/Drittland
@F kundekst_cd|char(10)|f|KundenKorezuordnung
@F kundeprovgr_cd|char(10)|f|Provisionsgruppe Kunde / Vorschlag für auf / siehe Tabelle provision
@F preisli_cd|char(5)|f|Preislistencode / entspricht der Preisliste des Preiskunden
@F intauf_prz|decimal(4,2)||interner Aufschlag / wenn <> 0, wird als Verkaufspreis der aktuelle DuEst erhöht um diesen Aufschlag berechnet / Berechung erfolgt auch beim Lieferscheinaufbau / befindet sich im TC im rechten Bereich des Windows, kann in Ableitungen zur Eingabe herangezogen werden
@F iu_jn|char(1)||Aufträge des Kunden beinhalten InklusiveUst-Preise / Feld wird durch LookUp der Preisliste befüllt / befindet sich im TC im rechten Bereich des Windows, kann in Ableitungen zur Eingabe herangezogen werden
@F kundevkkondgr_cd|char(10)|f|Kundenverkaufskonditionsgruppe / entspricht der Verkaufskonditionsgruppe des Preiskunden
@F vkrab|decimal(4,2)||Auftragskopfrabatt, Vorschlag für Auftragserfassung
@F vkrabk2|decimal(4,2)||Auftragskopfrabatt 2, Vorschlag für Auftragserfassung
@F vkrabk3|decimal(4,2)||Auftragskopfrabatt 3, Vorschlag für Auftragserfassung
@F abrugr_cd|char(10)|f|Abrufgruppencode z.B. "akh"
@F debitor_upid|bigint +n|
@F debitor_nr|integer(9)|f|Debitorennummer mit Kategorie / 0 = Interessent, sonst muß Debitor in FIBU vorhanden sein / wird, wenn im Neuanlagezweig leer, automatisch belegt / Debitor, der auf dem Rechnungsbeleg gedruckt wird
@F op_debitor_upid|bigint +n|
@F op_debitor_nr|integer(9)|f|Debitor für Fibuschnittstelle und Bonität / wird, wenn leer oder gleich debitor_nr, bei Änderung von debitor_nr mitgeändert
@F divers_jn|char(1)|n|bei j: / Rechnungsadresse wird in Fibu übergeleitet / Lieferadresse wird bei Auftragserfassung in die Rechnungsadresse gestellt
@F zuteil_prior|char(10)||Vorschlag für Auftrag: Zuteilungspriorität beim automatischen Freigeben, " " ist die höchste
@F vkrech_kz|char(2)||Art der Fakturierung
@F vkrech_kz|char(2)||d|Sammelrechnung pro Debitorennummer
@F vkrech_kz|char(2)||k|Sammelrechnung pro Kundennummer
@F vkrech_kz|char(2)||a|Sammelrechnung pro Auftrag
@F vkrech_kz|char(2)||l|Rechnung pro Lieferschein
@F vkrech_kz|char(2)||lr|Lieferschein + Rechnung sofort
@F vkrech_kz|char(2)||r|Rechnung = Lieferbeleg
@F vkrech_sel_fkz|char(3)||Selektionskennzeichen zum Zusammenstellen von Lieferscheinen zu einer Sammelrechnung / Auswahl über pfu_kz
@F kunde_aktiv_jn|char(1)||Kunde ist aktiv, d.h. kann verwendet werden
@F vklfs_preis_jn|char(1)||beim Lieferschein sollen Preise gedruckt werden
@F zahlart_cd|char(5)|f|Zahlungsart
@F teillief_jn|char(1)||Kunde darf Teillieferung erhalten / Vorschlag für auf
@F rueck_dru_jn|char(1)||Rückstände auf Lieferbeleg drucken ja/nein
@F kd_rueck_aufb_jn|char(1)||Rückstände aufbauen ja/nein
@F kd_aktpreis_jn|char(1)||Kunde erhält Aktionspreise / dies sind Konditionen die mit vkkondart.aktpreis_jn="j" gekennzeichnet sind
@F versart_cd|char(5)|f|Versandart
@F liefbed_cd|char(5)|f|Lieferbedingung
@F kunde_info|text +n||interner Infotext zum Kunden
@F kunde_info_search|char(255) +n||die ersten 255 Zeichen des internern Infotextes zum Kunden
@F varchar(1000)|über Funktion ermittelt / from kunde_auf_txt where wo_kz = "v"|
@F kunde_lagverw_kz|char(1)||siehe auch lag.lag_cd / 'k' Kunde darf Kommissionsware erhalten / 'i' Kunde dient nur für Auftragsart "interne Umbuchung" / '-' Kunde darf keine Kommissionsware erhalten und auch nicht für Auftragsart interne Umbuchung herangezogen werden / Möglichkeiten der Änderung: / '-' k: immer / Bei kunde_lag_cd = ' ' wird ein Kundenkommissionslager angelegt. / 'k' '-': immer / '-' 'i': nur, wenn kunde_lag_cd = ' '
@F kunde_lag_cd|char(11)|f,g|Lager für Auftragsarten bei denen Lagerzugang beim Kunden erfolgt. / Hier steht der Lagercode des Pseudolagers lag_cd="", wenn beim Kunden keine derartigen Auftragsarten erlaubt sind. / Verwaltungswindow: / Eingabe nur bei kunde_lagverw_kz = 'i' und dann zwingend / muß bei manueller Eingabe ein Lager mit lag_kz = 'e' sein / wird bei kunde_lagverw_kz = 'k' mit kunde_cd + 'k' belegt
@F k_artikid_muss_jn|char(1)||Es muß für den Artikel einer Auftragsposition ein Kundenartikel in der Tabelle artikid eingetragen sein
@F anz_vkrech|smallint(2)||Anzahl Rechnungen
@F anz_vklfs|smallint(2)||Anzahl Lieferscheine, muß > 0 sein, wenn vkrech_kz <> 'r', sonst 0
@F zollta_dru_jn|char(1)||Zolltarifnummer auf Rechnungsbelegen drucken
@F off_endsumme_jn|char(1)||Offert mit Endsumme drucken
@F kunde_anl_dat|date|ng|Datum Kundenanlage
@F klv_kartei_snr|integer|g|kartei_snr des letzten Verkaufs, 0 = noch nie verkauft
@F klv_vlfs_dat|date +n|g|Datum letzter Verkauf / wird bei Verkauflieferschein und bei Kassaverbuchen gesetzt / wird abweichend zu [klv_kartei_snr] auch belegt, wenn ein Artikel ohne Lagerführung verkauft wird
@F postanschr_ab_kz|char(1)||r…Rechnungsadresse wird oben gedruckt / l….Lieferadresse wird oben gedruck / bei der oberen Adresse wird die "zu Handen"-Zeile gedruckt
@F ab_druck_kz|char(2)||Kommunikationskennzeichen für die AB / 'fs' sofort faxen / 'fz' zeitversetzt faxen / 'e' email / 'd' druck
@F dn_cd|char(3)|f|Datanormgruppe / Datanormausgabe erfolgt pro Datanormgruppe
@F dn_lfd_nr|smallint(3)||Fortlaufende Nummer der Datanormausgaben / wird ggf von 999 wieder auf 1 umgestellt / Fixwert Neuanlage = 0 (0 = Erstbestückung)
@F vorfakt_saldo|decimal(11,2)||Saldo für VorausfakturaPauschal / darf nur mit Berechtigung verändert werden / ist bei Neuanlage 0 / befindet sich im Diagnosebereich und ist durch Customizen sichtbar zu machen
@N für CAS
@F le_kont_dat|date||Datum des letzten Kontaktes / Default: datmin
@F besint_wo|smallint||Besuchsintervall in Wochen
@F bes_wota|smallint||Besuchwochentag
@F n_besuchs_dat|date|g|Datum des nächsten Besuchs / wird automatisch aus le_kont_dat + besint_wo * 7 berechnet
@F ka_vklfs_jn|char(1)||Lieferschein auf Kassa erlaubt j/n
@F entsorger_cd|char(10)|f|Entsorgercode / Dummyentsorger erlaubt Kunde entpflichtet selbst, oder ist kein Inländer
@F era_jn|char(1)||Kunde auf ERA-Abrechnung ja/nein
@F eb_ekgrp_fcd|char(35)||Einkaufsgruppe / für Ausgabe EB-Interface – Rechnung an Bund
@F ao_snr|integer||AO-Snr / ist eindeutig / dient zum finden eines AOs
@F kunde_dbid|integer identity||ROWID für TcNext / durch DB-Insert mit serieller Nummer belegt
@F webshopkdgrp_cd|varchar(20) +n|f|WebShopkundengruppencode / Null = kein WebShop Kunde
@E
@I index i1_kunde (kunde_mc)
@I index i2_kunde (ao_snr)
@I unique index i3_kunde (kunde_dbid)
@I index i0_kunde_upid(kunde_upid)
@T kunde_auf_txt
@D Vorschlag für Auftrag- Textzeilen
@F kunde_cd|char(10)|p1,f
@F fa_nr|smallint(3)|p2
@F txt_typ_kz|char(1)|p3|Texttyp / "r" Richtext / wenn [param.appl_txt_kz <> "p"] / Standardfont "Arial 10" / "p" Plaintext / wenn [param.appl_txt_kz = "p"]
@F zeile_nr|smallint|p4|Zeilennummer
@F wo_kz|char(1)||'a' = Anfang / 'e' = Ende / 'v' = VerkaufsInfo / 'k' = KassenInfo
@F ab_jn|char(1)||auf der AB drucken
@F kommsch_jn|char(1)||auf Kommissionsschein drucken
@F lfs_jn|char(1)||auf Lieferschein drucken
@F rech_jn|char(1)||auf Rechnung drucken
@F off_jn|char(1)||auf Offert drucken
@F fett_jn|char(1)||fett drucken / fix "n", wenn [txt_typ_kz = "r"]
@F unterstrichen_jn|char(1)||unterstrichen drucken / fix "n", wenn [txt_typ_kz = "r"]
@F auf_txt|varchar(max)||Auftragstext- Zeile / wenn in der Zeile +abc steht ist dies beim Vorschlagen im Auftrag als Textbaustein (#abc) aufzulösen / generierter Plaintext (auf_rtxt), wenn [txt_typ_kz = "r"] / eingegebener Text, sonst
@F kunde_auf_txt_dbid|integer identity||ROWID für Retrieve Richtext / durch DB-Default mit serieller Nummer belegt
@F auf_rtxt|varbinary(max)||KundenAuftragstext Richtext / wenn [txt_typ_kz = "p"], durch DB-Default mit Leerstring belegt
@E
@I unique index i1_erech_txt (erech_txt_dbid)
@T kunde_casgr
@D Zordnung Kunde CAS-Gruppe(n) / es gibt je Kunde einen Dummy-Satz mit casgr_cd = " ", der im Verwaltungsregister nicht sichtbar ist und bei der Neuanlage des Kunden automatisch generiert wird
@F kunde_cd|char(10)|p1,f
@F fa_nr|smallint(3)|p2
@F casgr_cd|char(5)|p3,f|CAS-Gruppe
@E
@T kunde_casmitbew
@D Zordnung Kunde CAS-Mitbewerber
@F kunde_cd|char(10)|p1,f
@F fa_nr|smallint(3)|p2
@F casmitbewgr_cd|char(10)|p3,f
@F casmitbew_cd|char(10)|p4,f
@F mitbew_ums|decimal(11,2)||Geschätzer Jahresumsatz
@F fa_pers_cd|char(5)|g|Sachbearbeiter der den Satz erfasst hat
@F le_aend_dat|date|g|Anlage /letzte Änderung
@F mitbew_info|char(255)+n|
@E
@T kunde_dsgvo
@D DSGVO-Daten Kunde / View für Generierung Infoblatt Kunde / ist durch Betreuer zu Customizen / im Standard nur "from pfu_selkonst"
@F kunde_dbid|integer|p1
@F zeile_nr|integer|p2|Sortiernummer
@F txt1|char(100)||Text1, Label
@F txt2|char(100)||Text2, Wert
@N Beispiel: / create view kunde_dsgvo (kunde_dbid, zeile_nr, txt1, txt2) as /  / select k_integer, k_integer, k_char100, k_char100 / from pfu_selkonst / UNION / select kunde_dbid , 2, 'Besuchsintervall/zuletzt', cast(besint_wo as varchar) + ' Wo / ' + convert(varchar, le_kont_dat, 104) / from kunde
@E
@T kunde_fcol
@D Zuordnung Kunde -> Freies Kundenlennzeichen
@F kunde_cd|char(10)|p1,f
@F fa_nr|smallint(3)|p2
@F kunde_fcol_cd|char(10)|p3,f|Code der Art des freien Kennzeichens
@F kunde_fcol_wert|char(40)||Column- Wert
@E
@T kunde_fgr
@D Zuordnung Kunde -> Freie Kundengruppe
@F kunde_cd|char(10)|p1,f
@F fa_nr|smallint(3)|p2
@F fgrart_cd|char(10)|p3|Code der Art der freien Kundengruppe
@F fgr_cd|char(10)|f|Code der freien Kundengruppe
@E
@T kunde_ftxt
@D Freie Kundentexte
@F kunde_cd|char(10)|p1,f
@F fa_nr|smallint(3)|p2
@F kunde_ftxt_cd|char(10)|p3,f|Code der Art des freien Textes
@F txt_typ_kz|char(1)|p4|Texttyp / "r" Richtext / wenn [param.appl_txt_kz <> "p"] / Standardfont "Arial 10" / "p" Plaintext / wenn [param.appl_txt_kz = "p"]
@F zeile_nr|smallint|p5|Zeilennummer
@F kunde_ftxt_txt|varchar(max)||Freier Text / generierter Plaintext (kunde_ftxt_rtxt), wenn [txt_typ_kz = "r"] / eingegebener Text, sonst
@F kunde_ftxt_dbid|integer identity||ROWID für Retrieve Richtext / durch DB-Default mit serieller Nummer belegt
@F kunde_ftxt_rtxt|varbinary(max)||freier Kundentext Richtext / wenn [txt_typ_kz = "p"], durch DB-Default mit Leerstring belegt
@E
@I unique index i1_kunde_ftxt (kunde_ftxt_dbid)
@T kunde_kundevkkondgr
@D Kunden-Kundenverkaufskonditiongruppenzuordnung / Ist im TC-Standard in View auf Kunden mit kundevkkondgr_cd <> ""
@F kunde_cd|char(10)|p1|Kundennummer
@F fa_nr|smallint(3)|p2|Firma
@F kundevkkondgr_cd|char(10)|p3
@E
@T kundeerl
@D Kunden- Erlöszuordnungsgruppe
@F kundeerl_upid|bigint +n|
@F kundeerl_cd|char(10)|p1|Kundenerlöszuordnung
@F kundeerl_mc|char(40)|
@F inl_eu_drittl_kz|char(1)||i = Inland oder EU ohne UID- Nr. / e = EU / Löst bei JetFIBU Buchung die Erwerbsteuer aus / d = Drittland
@F uid_pruef_kz|char(1)||UID Prüfung KZ / k = Keine Prüfung / h = Hinweis wenn nicht vorhanden / s = Sperre – Auftragserfassung ohne UID Nummer ist nicht möglich
@E
@T kundekst
@D Kunden- Korezuordnungsgruppe
@F kundekst_cd|char(10)|p1|KundenKorezuordnung
@F kundekst_mc|char(40)|
@E
@T kundeprovgr
@D Kundenprovisionsgruppe / siehe Tabelle provision
@F kundeprovgr_upid|bigint +n|
@F kundeprovgr_cd|char(10)|p1
@F kundeprovgr_mc|char(40)|
@F kundeprovgr_aktiv_jn|char(1)|
@E
@T kundevkkondgr
@D Kundenverkaufskonditionsgruppe
@F kundevkkondgr_upid|bigint +n|
@F kundevkkondgr_cd|char(10)|p1
@F kundevkkondgr_mc|char(40)||Bezeichnung
@E
@T lag
@D Lager / es muß eine Row mit lag_cd = " " geben: dies ist ein Dummy- Satz für "kein Lager" und ist im Verwaltungsprogeramm nicht sichtbar. / bei der Neuanlage wird automatisch ein Datensatz für Tabelle lag_artikkomber geschrieben
@F lag_upid|bigint +n|
@F lag_cd|char(11)|p1|Lagercode, abhängig von lag_kz: / 'e' bis zu 10 Stellen lt. Benutzereingabe (11. Stelle leer) / 'k' 10 Stellen kunde_cd, 11. Stelle = 'k'
@F fa_nr|smallint(3)|p2,f
@F lag_kz|char(1)|n|'e' = eigenes Lager / 'k' = Kommissionslager beim Kunden / 'l' = Lager eines oder mehrerer Lieferanten / Lagerstand dieser Lager werden nicht für die DuEst-Rechnung berücksichtigt (Warenzugang, ER-Kontrolle) / bei der Auftragspositionserfassung ist der DuEst einzugeben und beim Lieferscheinaufbau dann auch zu verwenden / Strecken- oder Konsignationslager sind so gekennzeichnet / Strecke: / Ware gehört der Firma, ist aber bereits beim Kunden / Ware ist nur für die kurze Zeitspanne vom Warenzugang bis zum Lieferbelegaufbau auf diesem Lager / Konsignation: / Kommissionslager des/mehrerer Lieferanten / noch nicht realisiert / Diese Lager rechnen nicht in den Inventurwert
@F lag_mc|char(40)|
@F lag_fil_nr|smallint(3)|f|Lager gehört dieser Filiale / wenn lag_kz <> "e", fix 0
@F lag_ort_inp_jn|char(1)|n|'j' bei Lagerbewegungsbuchungen ist der Lagerort eingebbar, mögliche Lagerorte durch DDDW von artik_lag_ort / 'n' artik_lag_sub.lag_ort = " " / Der Lagerort nach dem eventuell sortiert wird ist artik_lag.inp_n_lag_ort /  / Wird nach Lagerort sortiert, ist immer nach artik_lag_sub.lag_ort, artik_lag.inp_n_lag_ort zu sortieren
@F lag_ort_edit_jn|char(1)||Der Lagerort wird beim Eingabeprogramm mittels DDDW ermittelt. Ist edit_jn = 'j', ist das Edit- Property = TRUE, und der Lagerort kann somit frei eingegeben werden. / Kennzeichen wird ausgewertet wenn lag.lag_ort_inp_jn = 'j'
@F disp_jn|char(1)||Lager wird für die Disposition berücksichtigt
@F vorgabe_fifo_kz|char(1)||"f" FiFo-Aufteilung:Bei Auftragsfreigabe werden die Lagerort und Chargenzuordnungen nach FIFO Prinzip vorgeschlagen, die freigegebene Menge in auf_pos_sub muss mit Freigabemenge in auf_pos übereinstimmen / "v" Vorgabe erforderlich: Lagerort bzw. Charge muss in Auftragsbearbeitung für Kommissionierung vorgegeben werden / "k"' Lagerort bzw. Charge muss erst zum Zeitpunkt des Lieferscheindruckes definiert sein (Platz auf Kommissionsschein zum Eintrag) / ist bei Kommissionslager durch automatische Anlage im Kundenfenster fix "k"
@F verfpruef_jn|char(1)||Verfügbarkeit prüfen / bei 'n' wird die Meldung, daß die Ware nicht frei verfuegbar ist, nicht angezeigt (für Kunden ohne Lager) und der Vorschlag der freigegebenen Menge erfolgt ohne Berücksichtigung der Verfügbarkeit
@F darf_lag_minus_jn|char(1)||'j' Lagerstand darf bei Artikel mit lagfuehr_kz <> 'g' negativ werden
@F duestgrp_cd|char(10)|f|Durchschnittspreisgruppe / keine Eingabe, wenn nur eine DuEst-Gruppe "" vorhanden ist / Eingabe nur bei Eigenlagern [lag_kz = "e"], bei allen anderen Lagern fix "" / DuEst in [artik_lag] versteht sich bei Eigenlagern je [duestgrp_cd], bei allen anderen Lagern je [lag_cd] / gibt es nur die DuEst-Gruppe "", gelten auch Kommissionslager für die DuEst-Rechnung als Eigenlager bei Verwendung von Kommissionsauftragsarten sollten alle Lager die gemeinsame DuEstGruppe "" besitzen, da sonst auf den n Kommissionslagern kein DuEst aktualisiert wird
@F webshoplager_cd|varchar(20)|f|WebShop Lagercode / An den WebShop werden nur Läger mit webshoplager_cd <> "" ausgegeben. / Es wird pro Artikel eine Summe pro webshoplager_cd für die Ausgabe gebildet. / "default" wenn es am Webshop nur einen Lagerstand gibt, alles andere muss mit dem WebShop koordiniert werden.
@F cg_verw_jn|char(1)||Lager mit/ohne Chargen-/Geräteführung / wenn "n", dann ist die Chargen-/Gerätenummer auf diesem Lager fix " " bzw. das Ablaufdatum fix unbestimmt
@F filhptlag_jn|char(1)||Ist das Hauptlager der Filiale. / Darf nur bei einem Eigenlager aktiviert werden / Es darf pro Filiale nur ein Lager auf aktiviert werden (alle anderen werden dadurch automaitsch deaktiviert) / Im TC Next werden bei diesem Lager die offenen Bestellungen angezeigt
@F mde_div_lag_ort|char(20)||Lagerort für Diverse-Artikel in der MDE Kommissionierung
@F webview_anzeigen_jn|char(1)||Lager wird in TC.WebView Artikel-Lagerstandsabfrage angezeigt
@E
@T lag_artikkomber
@D Zuordnung Lager – Artikelkommissionsbereich zu einem Kommissionsbereich / Verwaltung im Lagerfenster / es gibt je Lager einen Dummysatz der bei der Lageranlage generiert wird
@F lag_cd|char(11)|p1,f|Lager
@F fa_nr|smallint(3)|p2
@F artikkomber_cd|char(10)|p3,f
@F komber_cd|char(10)|f
@E
@T lag_lag
@D Beziehung Lager -- Gegenlager
@F lag_cd|char(11)|p1,f|Lager
@F fa_nr|smallint(3)|p2
@F ziel_lag_cd|char(11)|p3,f|Ziellager
@F geg_lag_cd|char(11)|f|Lager für Ware Unterwegs bei einer Umbuchung von lag_cd nach ziel_lag_cd über Auftragsart 'i%' / kann leer sein / sonst: / muss disp_jn = 'n' haben / es müssen lag_cd, geg_lag_cd und ziel_lag_cd lag_kz = 'e' haben / muß lag_ort_inp_jn = 'n' haben /
@E
@T lag_ort
@D Lagerorte – nur für TC-WebView Test in Standard TC / Es gibt in der TC Basis kein Verwaltungsprogramm. Ist nur zum Testen der TC.WebView Lager MDE Logiken vorgesehen. / Script zum Aufbauen aller vorhandenen Lagerorte aus artik_lag_ort und artik_lag_sub ist vorhanden. / Wird im Releasupdate nicht verwendet, da es zu viele Indiv Versionen gibt. / D.h. wenn TC.WebView Lager MDE zum Einsatz kommen sollte, muss diese Tabelle in der Kundenversion angelegt werden. / Es muss einen Dummy Satz mit ID 0 geben. / Es muss einen Dummy Satz pro Lager ohne Lagerortverwaltung geben.
@F lag_ort_upid|serial (p)|
@F lag_cd|char(11)||Lager
@F fa_nr|smallint(3)|
@F lag_ort|char(20)||Lagerort
@F lag_ort_sort_nr|integer(6)||Sortiernummer / darf nicht größer als 6-stellig sein, da diese Nummer temporär auf Gewichtsklassen umgerechnet wird / Gewichtsklasse Hinweg: Es wird die lag_ort_sort_nr verwendet. / Gewichtsklasse Rückweg: 2.000.000 – lag_ort_sort_nr
@F lag_upid|bigint|
@F lag_ort_aktiv_jn|char(1)||Lagerort ist aktiv / Es dürfen keine Lagerorte, die einmal in TC.WebView verwendet wurden wieder gelöscht werden, da das zu Abstürzen im TC.WebView führt.
@E
@I unique index i1_lag_ort (lag_upid, lag_ort)
@T land
@D Land / es gibt einen Dummy-Satz mit land_cd = " "
@F land_upid|bigint +n|
@F land_cd|char(3)|p1|Ländercode (= das postalische Länderkennzeichen)
@F land_bez|char(30)||Länderbezeichung für Kassa
@F land_iso|char(2)||der 2stellige ISO-Code
@F iban_blz_lng|smallint||Länge der Bankleitzahl im IBAN
@F iban_ktonr_lng|smallint||Länge der Kontonummer im IBAN
@F iban_bank_jn|char(1)||Bank lt. IBAN muss angelegt sein. / Bei "n" wird eine Dummy Bank für das Land generiert falls diese noch nicht vorhanden ist. Das gilt nicht wenn JetFIBU im Einsatz ist.
@E
@T land_fa
@D Land / es gibt einen Dummy-Satz mit land_cd = " "
@F land_cd|char(3)|p1,f|Ländercode (= das postalische Länderkennzeichen)
@F fa_nr|smallint|p2,f
@F inl_eu_drittl_kz|char(1)||i = Inland / e = EU / d = Drittland
@E
@T lief
@D Lieferanten- Stammdaten / Es gibt einen Dummy-Satz mit fa_nr = aktuell und lief_cd = " " /  / Im Select- Statement der "Liste" muß lief_fcol mitselektiert werden
@F lief_upid|bigint +n|
@F lief_cd|char(10)|p1
@F fa_nr|smallint(3)|p2,f
@F lief_mc|char(30)|g|= adr.adr_mc
@F waehrung_cd|char(4)|f|Währung für artik_lief_ekpr (0: EUR)
@F lief_adr_upid|bigint +n|
@F lief_adr_snr|integer(7)|f|Lieferantenadresse (0: 0)
@F kreditor_nr|integer(9)|f|Kreditorennummer mit Kategorie
@F lief_aktiv_jn|char(1)||Lieferant ist aktiv, d.h. kann verwendet werden
@F versart_cd|char(5)|f|Versandart (0: " ")
@F liefbed_cd|char(5)|f|Lieferbedingungen (0: " ")
@F liefsach_cd|char(10)|f|Zuordnung Bestands/Wareneinsatzkonten (0: " ") / bestimmt auch Inland/Eu/Drittland
@F mindbest_wert|decimal(11,2)||Mindestbestellwert
@F lief_info|text +n||interner Infotext zum Lieferanten
@F lief_info_search|char(255) +n||die ersten 255 Zeichen des internern Infotextes zum Lieferanten
@F lief_anl_dat|date|ng|Datum Lieferantenanlage
@F lle_kartei_snr|integer|r|kartei_snr des letzten Einkaufs, 0 = noch nie eingekauft
@F lief_term_kz|char(1)||Lieferterminkennzeichen / w…Woche / d...Datum / k...kein Vorschlag
@F termtxt_lt_inp_jn|char(1)||wird bei Terminkennzeichen "w" oder "d" ausgewertet / automatischer Aufbau (Bestellvorschlag, Bestellgenerierung, individuelle Fernsteuerungen) berücksichtigt Feld nicht / "n" bei manueller Eingabe des Termins wird Termintext lt. Terminkennzeichen aufgebaut / "j" bei manueller Eingabe des Termins wird Termintext lt. eingegebenen Feld aufgebaut (Datum Lieferdatum, Woche Lieferwoche)
@F bestweise_cd|char(10)|f|Bestellweise / Defaultwert für Bestellneuanlage
@F best_preis_jn|char(1)||Bestellung wird mit Preisen gedruckt
@F ao_snr|integer||AO-Snr / ist eindeutig / dient zum Finden eines AOs
@F nexmart_name|varchar(35)||Nexmart Lieferantennahme / in Kleinschreibung
@F nexmart_id|varchar(9)||Nexmart Händler ID
@F lief_dbid|integer identity||ROWID für TcNext / durch DB-Insert mit serieller Nummer belegt
@F ei_autobuch_tol_we|decimal(11,2) +n||Toleranzwert unter welcher beim Eingangsrechnungsimport eine automatische Verbuchung der Eingangsrechnung durchgeführt wird / NULL = keine Verbuchung / 0 = nur Verbuchung, wenn Werte exakt übereinstimmen / fix NULL, wenn ei_autoaufb_tol_we NULL ist / muss <= ei_autoaufb_tol_we sein
@F ei_autoaufb_tol_we|decimal(11,2) +n||Toleranzwert unter welcher beim Eingangsrechnungsimport eine automatische Verbuchung der Eingangsrechnung durchgeführt wird / NULL = keine Verbuchung / 0 = nur Verbuchung, wenn Werte exakt übereinstimmen
@F ekpr_autosave_jn|char(1)||Einkaufspreise werden bei Änderung in Bestellposition und Eingangslieferscheinposition automatisch gespeichert.
@F er_ewpfand_jn|Char(1)||In ER wird Einwegpfand ermittelt als Zuab, default n und rechts draussen
@E
@I index i1_lief (lief_mc)
@I index i2_lief(ao_snr)
@I unique index i3_lief (lief_dbid)
@T lief_best_txt
@D Vorschlag für Bestellung- Textzeilen
@F lief_cd|char(10)|p1,f
@F fa_nr|smallint(3)|p2
@F txt_typ_kz|char(1)|p3|Texttyp / "r" Richtext / wenn [param.appl_txt_kz <> "p"] / Standardfont "Arial 10" / "p" Plaintext / wenn [param.appl_txt_kz = "p"]
@F zeile_nr|smallint|p4|Zeilennummer
@F wo_kz|char(1)||'a' = Anfang Bestellung / 'e' = Ende Bestellung / 'b' = BestellInfo / 'w' = WarenzugangsInfo / 'r' = RechnungsInfo / weitere Kennzeichen durch Customizen möglich
@F fett_jn|char(1)||fett drucken / fix "n", wenn [txt_typ_kz = "r"]
@F unterstrichen_jn|char(1)||unterstrichen drucken / fix "n", wenn [txt_typ_kz = "r"]
@F best_txt|varchar(max)||Bestelltext- Zeile / generierter Plaintext (best_rtxt), wenn [txt_typ_kz = "r"] / eingegebener Text, sonst
@F lief_best_txt_dbid|integer identity||ROWID für Retrieve Richtext / durch DB-Default mit serieller Nummer belegt
@F best_rtxt|varbinary(max)||Lieferantenbestelltext Richtext / wenn [txt_typ_kz = "p"], durch DB-Default mit Leerstring belegt
@E
@I unique index i1_lief_best_txt (lief_best_txt_dbid)
@T lief_dsgvo
@D DSGVO-Daten Lieferant / View für Generierung Infoblatt Kunde / ist durch Betreuer zu Customizen / im Standard nur "from pfu_selkonst" / Beispiel Verwendung siehe [kunde_dsgvo]
@F lief_dbid|integer|p1
@F zeile_nr|integer|p2|Sortiernummer
@F txt1|char(100)||Text1, Label
@F txt2|char(100)||Text2, Wert
@E
@T lief_fcol
@D Zuordnung Lieferant -> Freies Lieferantenlennzeichen
@F lief_cd|char(10)|p1,f
@F fa_nr|smallint(3)|p2
@F lief_fcol_cd|char(10)|p3,f|Code der Art des freien Kennzeichens
@F lief_fcol_wert|char(40)||Column- Wert
@E
@T lief_fgr
@D Zuordnung Lieferant -> Freie Lieferantengruppe
@F lief_cd|char(10)|p1,f
@F fa_nr|smallint(3)|p2
@F fgrart_cd|char(10)|p3|Code der Art der freien Lieferantengruppe
@F fgr_cd|char(10)|f|Code der freien Lieferantengruppe
@E
@T lief_fil
@D Lieferanten Filialdaten
@F lief_cd|char(10)|p1,f
@F fa_nr|smallint(3)|p2
@F fil_nr|smallint|p3,f|Filialnummer
@F lief_kd_fcd|varchar(20)||Die Kundennummer der Filiale beim Lieferanten
@E
@T liefbed
@D Lieferbedingungen Einkauf / Es gibt einen Dummy-Satz mit liefbed_cd = " "
@F liefbed_cd|char(5)|p1
@F liefbed_bez|char(40)||Bezeichnung
@F incoterm_kz|char(3)||Incoterms Code für Versand EDI IFTMIN Ausgabe / '' = Lieferbedingung nicht für IFTMIN Ausgabe möglich / CFR = Kosten und Fracht / CIF = Kosten, Versicherung und Fracht / CIP = Frachtfrei versichert / CPT = Frachtfrei / DAF = Frei Grenze / DDP = frei Haus verzollt / DDU = frei Haus unverzollt / EXW = Ab Werk / FCA = frei Frachtführer
@E
@T liefsach
@D Lieferanten- ER- Sachkontenzuordnungsgruppe / Es gibt einen Dummy-Satz mit liefsach_cd = " "
@F liefsach_cd|char(10)|p1
@F liefsach_mc|char(40)|
@F inl_eu_drittl_kz|char(1)||i = Inland oder EU ohne UID- Nr. / e = EU / d = Drittland
@F uid_pruef_kz|char(1)||UID Prüfung KZ / k = Keine Prüfung / h = Hinweis wenn nicht vorhanden / s = Sperre – ER kann ohne gültige UID Nummer nicht gebucht werden.
@E
@T logoname
@D Logofilename im Windows
@F logobeleg_kz|char(10)|p1|Belegname, z.B.: fakt, lfs, ab, abericht_b, vb, best, bn, wret, bestmahn
@F fa_nr|smallint(3)|p2
@F kopf_fuss_kz|char(1)|p3|"k" Kopflogo / "f" Fusslogo
@F appl_fkz|char(10)|p4|freies Kennzeichen Applikation / ist in TC immer "" / wird in Ableitungen ggf. durch Event LogoApplFkz bestimmt
@F logoname_ori|char(40)||Filename Originallogo
@F logoname_dupl|char(40)||Filename Kopielogo
@F logoname_elektr|char(40)||Logoname für elektronischen Versand
@E
@S magento
@T magento_bestell
@D Magento Bestellungen / Über diese Tabelle werden Aufträge aus dem WebShop an TC übermittelt
@F magento_entity_id|integer (p)||Magento ID der Bestellung
@F bestell_nr|varchar(24)||Auftragsnummer des WebShop Auftrags, die der Kunde erhalten hat
@F bestell_dat|datetime||Zeitpunkt der Auftragserfassung am WebShop
@F erf_dat|datetime||Zeitpunkt des Inserts in TC DB
@F kunde_cd|varchar(16) +n||Kundennummer in TC / Leer (blank) bei einem Gastkunden
@F kunde_taxvat|varchar(24) +n||UID Nummer
@F kunde_bestell_nr|varchar(255) +n||Bestellnummer Kunde / Diese wird als Bestellnummer Kunde verwendet wenn angegeben
@F kunde_kunde_nr|varchar(40) +n||?????
@F kunde_email|varchar(255)||E-Mail Adresse
@F shipping_method|varchar(40)||Versandartv
@F shipping_type|varchar(16)||versand = Zustellung / abholung = Abholung
@F shipping_title|varchar(30) +n||Lieferadresse Titel
@F shipping_fistname|varchar(30) +n||Lieferadresse Vorname
@F shipping_lastname|varchar(30) +n||Lieferadresse Nachname
@F shipping_company|varchar(255) +n||Lieferadresse Fimenwortlaut
@F shipping_country|varchar(2)||Land im ISO 2 Format
@F shipping_street|varchar(50)||Lieferadresse Straße
@F shipping_city|varchar(50)||Lieferadresse Ort
@F shipping_postcode|varchar(10)||Lieferadresse PLZ
@F shipping_telephone|varchar(255) +n||Lieferadresse Telefonnummer
@F billing_title|varchar(30) +n||Rechnungsadresse Titel
@F billing_fistname|varchar(30) +n||Rechnungsadresse Vorname
@F billing _lastname|varchar(30) +n||Rechnungsadresse Nachname
@F billing _company|varchar(255) +n||Rechnungsadresse Firmenname
@F billing _country|varchar(2)||Land im ISO 2 Format
@F billing _street|varchar(50)||Rechnungsadresse Straße
@F billing _city|varchar(50)||Rechnungsadresse Ort
@F billing _postcode|varchar(10)||Rechnungsadresse PLZ
@F billing _telephone|varchar(255) +n||Rechnungsadresse Telefonnummer
@F billing_email|varchar(255) +n||E-Mail Adresse für Rechnungsversand
@F payment_method|varchar(255)||Zahlungsart
@F payment_type|varchar(16)||offline – Zahlung muss noch abgewickelt werden / online – Zahlung ist bereits über WebShop erfolgt
@F curreny|char(3)||Währung
@F currency_rate|decimal(12,4)||Wechselkurs
@F total|decimal(12,4)||Gesamtwert exkl. Ust
@F total_incl_tax|decimal(12,4)||Gesamtwert inkl. Ust (Wert der bezahlt wurde)
@F tax|decimal(12,4)||Steueranteil
@F store_name|varchar(255)||Shop-Name
@F err_txt|text +n||Fehlertext
@F int_txt|text|
@F kunde_bestell_txt|text +n||Kunden Bestellbemerkungen
@F locale|varchr(5)||Sprachcode in der der WebShop Aufrag erfasst wurde / z.B. de_AT;en_US;…..
@F source_code|varchar(255)+n||Webshop Lager (nur bei Abholung)
@F auf_nr|integer +n||Auftragsnummer in TC / 0 = wurde noch nicht übernommen / -1 = Fehler bei der Übernahme – siehe err_txt / >0 = Es wurde der Auftragskopf mit dieser Auftragsnummer aufgebaut
@F fa_nr|smallint +n||Firmennummer in TC
@F imp_job_snr|bigint||Jobnummer des Imports / Notwendig für Druck Fehlerprotokoll
@E
@I index i1_magento_bestell (auf_nr, fa_nr)
@T magento_bestell_pos
@D Magento Bestellpositionen / Über diese Tabelle werden Aufträge aus dem WebShop an TC übermittelt
@F magento_entity_id|integer|p1|Magento ID der Bestellung
@F magento_item_id|integer|p2|Positionsnummer / Ist die eindeutige order_item_id von Magento / Ist bei Versandkostenpositionen immer 0 oder 1
@F artik_cd|varchar(64)||Artikelcode
@F artik_type|varchar(16)||Positionsart / products – Artikel / shipping – Versandkosten / virtual – Zuschlag (wird im TC Standard nicht übernommen) / downloadable – Digitales Produkt Es wird sofort ausfakturiert
@F menge|decimal(12,4)||Bestellmenge
@F artik_price|decimal(12,4)||Verkaufspreis ohne Rabatt und ohne Steuer
@F artik_price_incl_tax|decimal(12,4)||Verkaufspreis ohne Rabatt und mit Steuer
@F price|decimal(12,4)||Verkaufspreis mit Rabatt und ohne Steuer
@F price_incl_tax|decimal(12,4)||Verkaufspreis mit Rabatt und mit Steuer
@F discount|decimal(12,4)||Rabattwert ohne Steuer
@F discount_incl_tax|decimal(12,4)||Rabattwert mit Steuer
@F tax|decimal(12,4)||Steueranteil von price_gross
@F tax_percentage|decimal(12,4)||Steuerprozentsazt
@F row_amount_incl_tax|decimal(12,4)||Zeilensumme mit Rabatt und Steuer
@F row_amount_excl_tax|decimal(12,4)||Zeilensumme mit Rabatt und ohne Steuer (Umsatz)
@F bestell_pos_txt|text +n||Positionstext
@F product_options|text +n||Zusatzinformationen im JSON Format
@F err_txt|varchar(255) +n||Fehlertext
@F fa_nr|smallint||Firmennummer des TC Auftrags / 0 = noch nicht übernommen (Default)
@F auf_nr|integer||Auftragsnummer in TC / 0 = noch nicht übernommen (=Default) / -1 = Fehler / >0 = Auftragsnummer in die es übernommen wurde
@F auf_pos_nr|smallint||Auftragspositionsnummer in TC / 0 = noch nicht übernommen (=Default)
@E
@I index i1_magento_bestell_pos (auf_nr, fa_nr, auf_pos_nr, magento_entity_id)
@T magento_bestell_gus
@D Magento Bestellpositionen Gutschein / Über diese Tabelle werden Aufträge aus dem WebShop an TC übermittelt
@F magento_bestell_gus_snr /|Integer identity|p1
@F magento_entity_id|integer||Magento ID der Bestellung
@F magento_item_id|integer||Positionsnummer
@F gus_nr|Varchar(38)|
@F gus_betr|Decimal(11,2)|
@F waehrung_cd|Char(5)||Währung
@F ve_kz|Char(1)||Kennzeichen (v)erkauf oder €inlösen
@F magento_bestell_gus_erl_snr /|integer||0 ist noch offen / Wenn ident mit Pkey, dann in ka_gus+ka_gus_trans eingearbeitet / Passiert durch Triffer und Procedure
@E
@N Insert Trigger auf Tabelle, ruft Procedure auf.
@N Procedure schreibt ka_gus_trans bzw. ggf. Ka_gus und korrigiert ka_gus.
@N Procedure Updatet magento_bestell_gus.magento_bestell_gus_erl_snr
@N Korrekt Locken!!
@T magento_zus
@D Magento Zussatzkosten / Über die magento_zus… Tabellen erfolgt die Berechnung der Zustellkosten aus TC / Hierzu ist die StoredProcedure magento_zus_clac_indiv zu verwenden
@F magento_zus_id|varchar(255) (p)||ID
@F website_code|varchar(255)||WebShop
@F fil_nr|smallint +n||Filiale
@F abt_nr|smallint +n||Abteilung
@F kunde_cd|char(20)||Kundennummer
@F lief_land_iso|char(2)||Land der Lieferadresse im ISO2 Code
@F lief_plz|char(20)||PLZ der Lieferadresse
@F shipping_method|varchar(40) +n||Versandart
@F shipping_type|varchar(16)||Versandart Type / versand / abholung
@F payment_method|varchar(255) +n||Zahlungsart
@F payment_type|varchar(16)||Zahlungsart Type
@F currency|char(3)||Währung
@F erf_datz|datetime||Zeitpunkt des Inserts
@E
@T magento_zus_detail
@D Magento Zussatzkosten - Details / Diese Tabelle wird von der Procedure beschrieben und damit die Spesen an Magento retourniert
@F magento_zus_id|varchar(255)|p1|ID
@F zeile_nr|smallint|p2
@F artik_cd|varchar(255)||Artikelcode
@F zus_txt|varchar(255)||Text
@F vkpr|decimal(15,6)||Verkaufspreis exkl. Ust (Spesenwert)
@F vkpr_iu|decimal(15,6)||Verkaufspreis/Spesenwert inkl. Ust
@E
@T magento_zus_pos
@D Magento Zussatzkosten Positionen / Diese Tabelle wird von Magento vor dem Aufruf der Berechnung mit den bestellten Positionen befüllt
@F magento_zus_id|varchar(255)|p1|ID
@F zeile_nr|smallint|p2
@F website_code|varchar(255)||WebShop
@F fil_nr|smallint +n|
@F abt_nr|smallint +n|
@F artik_cd|char(20)|
@F menge|decimal(12,3)||bestellte Menge in Lagereinheit
@F preis|decimal(15,6)||Verkaufspreis pro Lagereinheit exkl. Ust
@F preis_iu|decimal(15,6)||Verkaufspreis pro Lagereinheit inkl. Ust
@E
@T mahnvor
@D Mahnvorschlag (gn) / wird vom Mahnvorschlagsaufbau angelegt und vom Mahnausführungslauf gelöscht / Es muß auch ein Satz mit mahnvor_cd = " " angelegt sein.
@F mahnvor_cd|char(10)|p1
@E
@T marke
@D Marke / Es gibt einen Dummy Satz mit 0, der im Verwaltungsprogramm nicht sichtbar ist, aber im Artikelstamm ausgewählt werden kann / Im Verwaltungsprogramm kann mit Drag&Drop ein Bild eingefügt werden und wird auch dort angezeigt.
@F marke_nr|integer (p)||Markennummer / Vorschlag bei Neuanlage max + 1
@F marke_mc|varchar(40) ci||Marken Matchcode für Anzeige in TC
@F marke_bild|varchar(40)|g|Filename des Markenbildes – wird automatisch aus marke_mc generiert: / Grundsätzlich gleich marke_mc in Kleinbuchstaben / Umlaute ersetzten (ä a …) / Leezeichen am Anfang werden automatisch weggetrimmt / Alle anderen nicht alphanumerischen Zeichen werden zu einem Bindestich "-" ersetzt. Dabei werden mehrere Aufeinanderfolgende Sonderzeichen zu einem Bindestrich zusammengefasst. / Die Bilder sind für den WebShop in einem Verzeichniss (lt. Parameter marke_pfad) unter <marke_bild>.jpg verspeichert. / D.h. bei Änderung des Matchcodes muss auch das Bild umbenannt werden. / Ist im WebShop der eindeutige Key der Marke / Optimale Bildgröße wäre 210 x 50
@F marke_sort_nr|smallint(3)||Sortiernummer für WebShop
@F marke_ext|char(4)||Marke Extention (png, jpg, bmp oder jpeg)
@E
@T unique index i1_marke (marke_bild)
@E
@T mdeumlag
@D MDE - Umlagerungen
@F mdeumlag_upid|bigint (p)|
@F fa_nr|smallint|
@F lag_cd|char(11)|
@F lager_upid|bigint||Lager
@F artik_cd|char(20)||Artikelcode
@F artik_upid|bigint|
@F von_lag_ort|varchar(20)||Von Lagerort
@F auf_lag_ort|varchar(20)||Auf Lagerort
@F charge_geraet|varchar(40)||Chargen/Gerätenummer
@F erf_mg|decimal(12,3)||Erfasste Menge in Lagereinheit
@F herst_dat|date +n||Herstellungdatum aus EAN128
@F mhd_dat|date +n||Mindesthaltberkeitsdatum aus EAN128
@F ablauf_dat|date +n||Ablaufdatum/Verfallsdatum aus EAN128
@F erf_datz|datetime||Erfassungszeitpunkt
@F mde_usr_cd|char(20)||MDE Usercode
@F job_snr|integer||0 = Insert erfolgt / >0 = Jobnummer mit dem die Verbuchung der Umlagerung erfolgt ist / -1 = Fehler beim Verbuchen aufgetreten – siehe err_txt
@F erl_datz|datetime +n||Zeitpunkt der Erledigung
@F auf_lag_cd|char(11) +n||Auf Lager / Null Altdaten bei denen nicht zwischen Lagern umgebucht werden konnte
@F auf_lager_upid|bigint +n||Upid des Auf Lagers
@F mdeumlag_vorgang_upid|bigint +n||Updid des urpsprünglichen gdo Datensatzes
@F err_txt|varchar(255) +n||Fehlertext
@F umlag_mg|decimal(12,3)||Erfasste Menge in Einheit
@F artik_eh_id|bigint||ID der Artikeleinheit
@E
@I index i1_mdeumlag (job_snr)
@T nummern
@D Nummernkreise / Beispiele: / 1) Artikelnummer / Abhängig davon, ob Artikelnummer bei der Neuanlage eingegeben wurde oder nicht, wird der Satz mit nummern_kz 'p' bzw. 'v' gelesen, wobei nr_kreis im allgemeinen konstant ' ' sein wird. / Gibt es keinen Satz mit nummern_kz = 'p', darf die Nummer nicht eingegeben werden. Gibt es keinen Satz mit nummern_kz = 'v', muß die Nummer eingegeben werden. / Soll die eingegebene Artikelnummer nicht geprüft werden, ist beim Satz mit nummen_kz = 'p' die von_nr gleich null. / 2) Rechnungsnummer / Abhängig von z.B. Auftragsart / Kunde / ... wird der Satz mit entsprechendem nr_kreis gelesen; nummern_kz ist konstant 'v'
@F tabelle|char(18)|p1|tabname der Tabelle
@F spalte|char(18)|p2|colname der Column / Bei Kassentabellen die Kassennummer
@F fa_nr|smallint(3)|p3,f
@F nr_kreis|char(10)|p4|abhängig vom Programm, das die Nummer vergibt, ist im Standardpaket / sofern nicht anders beschrieben " "
@F nummern_kz|char(1)|p5|v = Vergabe, keine Eingabe / p = Eingabe und Prüfung
@F von_nr|integer +n||erste Nr. des Nummernkreises / wenn is null: keine Prüfung
@F bis_nr|integer +n||letztmögliche Nr. des Nummernkreises
@F naechste_nr|integer||0 bedeutet keine automatische Vergabe
@E
@T outlook_kontakt
@D Outlook-Kontakte / Hier werden die Outlookidentifikationsnummern verspeichert, welche mittels eines Reorgs im Outlook gelöscht werden sollen
@F outlook_id|char(255)|p1|Outlook-Identifikationsnummer
@E
@T packst
@D Packstoffe
@F packst_cd|char(10)|p1|Packstoffcode
@F packst_bez|char(40)||Packstoffbezeichnung
@E
@T packst_entsorger
@D Packstoffe
@F packst_cd|char(10)|p1|Packstoffcode
@F entsorger_cd|char(10)|p2|Entsorgercoce
@F preis_kg|decimal(11,3)||Preis je kg
@F spalte_nr|smallint(2)||Spaltennummer für Auswertung / Werte 0 – 99 / Auf Ausdruck werden nur 10 gedruckt / 0 keine Auswertung
@F packst_kurzbez|char(10)||Spaltenbezeichnung für Entsorger-Listen
@E
@T persfunktion
@D Funktion einer Person einer Adresse / Es gibt einen Dummy-Satz mit persfunktion_cd = " "
@F persfunktion_upid|bigint +n|
@F persfunktion_cd|char(10)|p1
@F persfunktion_mc|char(40)|
@F techniker_jn|char(1)||Person ist Techniker
@E
@T pfu_komid
@D logische Tabelle zur Auswahl von Mail und Fax im SpoolIn-Fenster / komidart.komidart_kz in ("f", "e")
@F komid_snr|integer (p)||adr_pers_komid.adr_pers_komid_snr
@F komid_wert|varchar(255)||adr_pers.komid_wert
@F empfaenger|char(150)||sp_zhd(geschlecht_kz, sprache_cd, titel, v_name, n_name) / wenn pers_cd <> " " / adr.name1 / wenn pers_cd = " "
@F komidart_kz|char(1)||komidart.komidart_kz
@F adr_mc|char(30)||lt. [adr]
@F name1|char(50)|
@F name2|char(50)|
@F name3|char(50)|
@F name4|char(50)|
@F strasse|char(50)|
@F land_cd|char(3)|
@F plz|char(10)|
@F ort|char(50)|
@F komid_mc|char(40)||adr.adr_mc / wenn pers_cd = " " / lower(adr_pers.n_name + adr_pers.v_name) / wenn pers_cd <> " "
@E
@T pfu_param
@F MFA|PCS||Beschreibung / Werte werden in Tabelle pfu_param gespeichert / PCS = Darf nicht vom User geändert werden
@F apollo_jn|sys||J|Apollo aktiviert (Shop bzw. IPAD)
@F appl_txt _kz|sys||n|Textkennzeichen Applikation / "r" Richtext komplette Applikation / "m" Mischvariante / Plaintext Artikeltexte (Positionstexte) / Richtext Kopf-/Endtexte und Überschriften / "p" Plaintext only
@F archivart_kz|sys||j|Art der Archivierung (easyarchiv; dokuware; jetscan; tcscan; -)
@F bewdat_mindestjahr_anz|sys||n|Die Bewegungsdaten sind für mindestens [bewdat_mindestjahr_anz] zu behalten / Prüfung bei Löschen Bewegungsdaten
@F dsgvo_kz|sys||j|Zusatzmodul DSGVO vorhanden / "0" nicht vorhanden / "1" DSGVO / "2" DSGVO Plus
@F duestaufr_max_pos|j||n|Maximale Anzahl von Positionen, die die DUEST-Aufrollung im Vordergrund durchführt. / Sind mehr Positionen aufzurollen, so wird der Batch Job gestartet, um z.B. in der ER-Kontrolle nicht zu lange Transaktionen zu haben.
@F eanverg_kz|j||n|f = Fixe Vergabe (alte Logik) / l = Lücken Suchen (Prüfen ob die nächste Nummer frei ist und weitersuchen)
@F erechimp_autoid_anl_kz|n||j|Kennzeichen automatische Anlage Artikelidentifikation bei der manuell Zuordnung der Artikelnummer / el=EAN und Lieferantenartikelnummer / l=Lieferantenartikelnummer / e=EAN-Nummer / = keine Zuordnung
@F kilo_eh_cd|n||j|Definiert die Kilo Einheit für Gewichtsartikel lt. artik.vargew_jn
@F mdeumlag_divlgbart_cd|j||n|Diverse Lagerbuchungsart für MDE Umlagerung
@F offert_erweitert_jn|n||j|Modul Offert erweitert verfügbar
@F outlook_mail_kz|n||j|Kennzeichen, ob Mailversand des Beleges über Outlook erfolgen soll / "o" Offert (gilt nicht für Service) / "a" Auftragsbestätigung / "b" Bestellung / Bsp: / "oa" bzw. "ao" Offert und Auftragsbestätigung /  / Versand erfolgt halbautomatisch / Jobverarbeitung erstellt Dokument / TC wartet / ist Dokument vorhanden, öffnet TC über OLE-Objekt Outlooknachricht und setzt die Nachrichtenfelder (To, BCC, Subject, Attachment) / Benutzer ist für Versand selbst verantwortlich
@F outlook_mail_timeout|n||j|Timeout für Mailversand in Sekunden / z.B: 15 / TC macht 15 Versuche, das Dokument zu lesen und wartet jeweils 1 Sekunde vor einem Versuch
@F pers_cd_auto_stellen|n||Anzahl der Stellen für automatische Vergabe des Personencodes / 0 = keine Automatik / Sonst die Anzahl der Stellen auf die die nächste mögliche Nummer mit Vorlaufnullen aufgefüllt wird.
@F praefix_bund_bestnr|n||j|Präfix für Bestellnummer des Bundes / abhängig davon ist die Eingabe der positionsnummer verpflichtend
@F rt_defaultfont|sys||j|Default Schriftart
@F rt_defaultfontsize|sys||j|Default Schriftgröße Kopf-/Fußtext
@F rt_defaultfontsize_pos|sys||j|Default Schriftgröße Artikel/Positionstext
@F rt_fonts|sys||j|erlaubte Schriftarten, durch ";" getrennt
@F rt_fontsizes|sys||j|erlaubte Schriftgrößen, durch ";" getrennt
@F rt_heightinpixels_kopf|sys||j|Größe RT-Window Kopf/Fußtext
@F rt_heightinpixels_pos|sys||j|Größe RT-Window Positionstext
@F rt_maxheightinpixels|sys||j|maximale Höhe des Richtext in Pixels
@F rt_verticalsscrollbar_jn|sys||j|RT-Window hat Vertical Scroll-Bar
@F rt_tabstop|sys||j|Tab-Stops, durch ";" getrennt
@F svc_mehrere_geraete_pro_auf_jn|n||j|In einem Serviceauftrag können mehrere Geräte gleichzeitg erfasst werden
@F svc_mehrmals_pro_geraet_jn|n||j|Ein Gerät kann in mehreren Serviceaufträgen gleichzeitig vorhanden sein / Bei Anlage wird geprüft, ob das Gerät bereits in einem Serviceauftrag vorhanden ist. Wenn nicht dann entsprechende Updates / Bei Abschluss wird geprüft, ob das Gerät in anderen offenen Aufträgen vorhanden ist. Wenn nicht dann entsprechende Updates
@F uid_online_kz|n||j|UID-Nummer wird bei Debitoren- bzw. Kreditorenanlage Online geprüft / "-" keine Prüfung / "fion" Prüfung via Finanz-Online
@F uidpruef_tg|j||n|Anzahl Tage für automatische Prüfung der UID-Nummer des Kreditior bei der ER Buchung. D.h. letzte Prüfung der UID-Nummer darf maximal so viele Tage in der Vergangenheit liegen. / 0 = Es gibt kein Ablaufdatum von geprüften UID-Nummern
@F marke_pfad|n||Pfad für Webshop Marken Bilder
@F webshopwg_bildpfad|n||Ablagepfad für Webshop Warengruppenbilder
@E
@T pkv_eurofib
@D Personenkontenvorschlagstabelle EuroFib / für Vorschlagswerte Debitoren- Kreditorenanlage TC / für Ergänzung-Fibu-Felder, die in TC nicht gewartet werden, bei der Kontenanlage in EuroFib
@F fa_nr|smallint (3)|p1
@F vorschlag_cd|char(10)|p2|Belegung / Debitoren: "deb_"+[kundeerl_cd] / Kreditoren: "kre_"+[liefsach_cd]
@F kreditlimit|decimal(11,2)||Kreditlimit
@F zahlkond_nr|integer||Zahlungskondition
@F mhktosperre_kz|char(1)||Kennzeichen für Mahnsperre des Kontos / J… Mahnung / K … nur Kontoauszug / S … Mahnsperre
@F kod_sammelkonto|smallint(3)||Sammelkonto
@F kod_mahnspesen|char(1)||Mahnspesenberechnung (J/N)
@F kod_verzug|char(1)||Verzugszinsenberechnung (J/N)
@F kod_verzugrech|char(1)||Verzugsrechnung (J/N)
@F kod_verzugs_vs_std|char(1)||Verzugszinsen Kontokorrent VorSaldoStd (J/N)
@F kod_verzugs_vs_berueck|char(1)||Verzugszinsen Kontokorrent VorSaldoBerueck(J/N)
@F kod_verzugop|char(1)||Verzugsrechnung OP (J/N)
@F kod_verzugop_tabnr|smallint(3)||Verzugszinsentabellennummer OP
@F kod_vop_respiro_tage|smallint(3)||Respirotage Verzugszinsen OP
@F kod_intervall|smallint(3)||Intervall Mahnung in Tg
@F kod_mahn_art|char(1)||Mahnungsart / 1=Druck / 2=Fax / 3=Mail
@F kod_vertreter|smallint(4)||Vertreter - keine Plausibilitätsprüfung
@F kod_uid_chk_nr|char(1)||Prüfkennzeichen UID-Datum / 0=ungeprüft / 1= Status 1 / 2 = Status 2 / 3 = ungültig
@F kod_zession|smallint(3)||Zessionskennzeichen
@F kod_sprache|smallint(3)||Sprachcode
@F kod_anlageuser|char(3)||Anlagebenutzer
@F kod_aenderuser|char(3)||Änderungsbenutzer
@F kod_verzug_tab|smallint(3)||Verzugszinsentabellennummer
@F zah_komprimieren|smallint(1)||Komprimieren SEPA
@E
@T preisli
@D Preislisten
@F preisli_cd|char(5)|p1
@F pl_waehrung_cd|char(4)|f,n
@F iu_jn|char(1)|n|Preis enthält Umsatzsteuer
@F kassa_jn|char(1)||Konditionen dieser Art werden ins Kassensystem übernommen
@F tcnext_jn|char(1)||Preisliste wird im TC-Next Außendienst verwendet um die Listepreise zu finden, es darf nur eine mit ja geben
@E
@T preisli_prfind
@D Preislistenzuordnung Preisfindung / für Kunden mit Preislistencode = preisli_cd kommen die Preislisten lt. prfind_preisli_cd zur Anwendung / bei der Neuanlage einer Preisliste wird der Datensatz mit prfind_preisli_cd = preisli_cd automatisch angelegt, bzw. beim Löschen automatisch gelöscht / Die Verwaltung der Datensätze für die gilt: preisli_cd <> prfind_preisli_cd erfolgt auf einem eigenen Register im Preislistenfenster
@F preisli_cd|char(5)|p1,f
@F prfind_preisli_cd|char(5)|p2,f
@F rel_prfind_nr|smallint(4)||Wert wird zu vkkondart.prfind_nr addiert / bei preisli_cd = prfind_preisli_cd fix 0
@E
@T provart
@D Provisionsart / siehe Tabelle provision
@F provart_cd|char(10)|p1
@F provart_mc|char(40)|
@F kundeprovgr_jn|char(1)||'j' bei der Zuordnung einer Provision mit dieser provart_cd muß auf.kundeprovgr_cd = provision.kundeprovgr_cd gelten / 'n' obiges muß nicht gelten
@F artikprovgr_jn|char(1)||'j' bei der Zuordnung einer Provision mit dieser provart_cd muß auf_pos.artikprovgr_cd = provision.artikprovgr_cd gelten / 'n' obiges muß nicht gelten
@E
@T provision
@D Provision / definiert eine Provision für Rechnungspositionen mit auf.kundeprovgr_cd entspricht und auf_pos.artikprovgr_cd= / Es kann eine Provision pro provart_cd je Rechnungsposition geben / siehe Tabelle provart
@F kundeprovgr_cd|char(10)|p1,f|ist bei provart.kundeprovgr_jn = 'n' leer
@F artikprovgr_cd|char(10)|p2,f|ist bei provart.artikprovgr_jn = 'n' leer
@F provart_cd|char(10)|p3,f
@F info_txt|char(255)||Informationstext
@F vert_cd|char(10)|f|Vertreter
@E
@T provision_prz
@D Provisionsprozentsatz
@F kundeprovgr_cd|char(10)|p1|ist bei provart.kundeprovgr_jn = 'n' leer
@F artikprovgr_cd|char(10)|p2|ist bei provart.artikprovgr_jn = 'n' leer
@F provart_cd|char(10)|p3,f
@F ab_dat|date|p4|Datum gültig ab
@F bis_dat|date||Datum gültig bis: / wird entweder auf DATMAX oder ab_dat-1 des nächstgrößeren ab_dat's gesetzt.
@F prov_ab_wert|decimal(11,2)|p5|ab Wert für einen Wert der Rechnung: / dieser Wert kann z.B. DB% der Position sein / in Grundwährung
@F prov_bis_wert|decimal(11,2)||ab Wert für einen Wert der Rechnung: / wird entweder auf 999999999,99 oder ab_wert-0,01 des nächstgrößeren ab_wert's gesetzt. / in Grundwährung
@F provision_prz|decimal(4,2)||Provisionsprozentsatz
@E
@T sach
@D Sachkontenzuordnung Bestand + Wareneinsatz / Erlöskonten werden über erl abgehandelt
@F artiksach_cd|char(10)|p1,f|Artikelsachkontenzuordnungscode
@F liefsach_cd|char(10)|p2,f|Lieferantensachkontenzuordnungscode
@F bestkto_nr|integer(9)||Bestandskontennummer für ER
@F weinskto_nr|integer(9)||Wareneinsatzkontennummer für ER
@F ust_cd|char(10)|f|Ustcode für ER
@E
@T sprache
@D Sprachen / Es gibt einen Dummy-Satz mit sprache_cd = " "
@F sprache_upid|bigint +n|
@F sprache_cd|char(5)|p1
@F hpt_sprache_jn|char(1)||Hauptsprache in der die Daten angelegt sind / nur ein Satz hat "j", dient nur zur Info, System bedient sich bei der Abfrage der Hauptsprache aus dem Parameter "appl_sprache_cd" / es gibt auch noch die Sprache der Anmeldung, diese wird durch den Sachbearbeiter, der sich anmeldet bestimmt
@F apollo_sprache_fkz|char(5)||Apollo-Sprachkennzeichen
@F webshop_sprache_fkz|char(5)||Sprachcode für Webshop / Magento: Deutsch sollte hier mit blank angelegt werden, damit wird es als Defaultwert für alle Sprachen verwendet, wenn diese nicht selbst angelegt ist.
@E
@T s_artikart
@D Artikelart für Service
@F s_artikart_cd|char(10)|p1|Artikelart: z.B. Arbeitszeit, Wegpauschale, Wegzeit, Material
@F s_artikart_mc|char(20)|
@E
@T s_auf
@D Servicedaten zum Auftrag
@F fa_nr|smallint(3)|p2
@F auf_nr|integer(7)|p1,f
@F s_artik_cd|char(20)|f|der zu servicierende Artikel
@F s_artik_mc|char(40)|r|Artikelmatchcode
@F s_geraet_cd|char(40)|f|das Gerät muß abhängig von artik.muss_geraet_cd_jn angegeben werden / das Gerät muß bei der Neuanlage den selben Kunden, wie der Auftrag haben, dies gilt natürlich nicht für das Dummy- Gerät
@F s_geraet_artik_cd|char(20)||nur für den f- Key auf das Gerät: / kein AEO / 2 möglichkeiten: / Kein Gerät angegeben: / s_geraet_cd = "" / s_geraet_artik_cd = fa.dummy_artik_cd / dies ist ein Dummy- Gerät / dies ist nur erlaubt, wenn artik.muss_geraet_cd_jn = 'n' / Gerät angegeben: / s_geraet_cd = lt. Eingabe / s_geraet_artik_cd = s_artik_cd / F- Key: s_geraet_cd, s_geraet_artik_cd, fa_nr geraet
@F s_auf_mg|decimal(9,0)||Menge der zu Reparierenden Geräte / = 1, wenn s_geraet_cd <> "" / hat keinen Einfluß auf die Positionen
@F s_geraet_dr|char(40)||Gerätenummer zum Andrucken / ist fix s_geraet_cd, wenn s_geraet_cd nicht leer ist / kann eingegeben werden, wenn s_geraet_cd leer ist
@F s_auf_zustand_kz|char(2)|g|Zustand des Serviceauftrags
@F s_auf_zustand_kz|char(2)|g|e|erfasst / auf_zustand_kz = 'e'
@F s_auf_zustand_kz|char(2)|g|b|zur Bearbeitung eingeteilt / auf_zustand_kz = 'e'
@F s_auf_zustand_kz|char(2)|g|ne|neuerlicher Einsatz notwendig / auf_zustand_kz = 'r' / wird vom Arbeitsberichtsaufbau gesetzt, wenn abericht_kz = 'n' und n_einsatz_datz leer ist
@F s_auf_zustand_kz|char(2)|g|nb|zur neuerlichen Bearbeitung eingeteilt / auf_zustand_kz = 'r' / wird vom Arbeitsberichtsaufbau gesetzt, wenn abericht_kz = 'n' und n_einsatz_datz nicht leer ist
@F s_auf_zustand_kz|char(2)|g|a|abgeschlossen / auf_zustand_kz = 'g'
@F n_einsatz_dat|date +n||Datum des nächsten Einsatzes / Beim Setzen wird s_auf_zustand_kz auf 'b' gesetzt, wenn s_auf_zustand_kz = "e", bzw. auf "nb" gesetzt, wenn s_auf_zustand_kz = "ne" / wird beim Arbeitsbericht- Aufbau gelöscht, wenn abericht_kz = 'a'
@F n_einsatz_txt|char(80)||Text zum nächsten Einsatz / wird beim Arbeitsbericht- Aufbau gelöscht, wenn abericht_kz = 'a'
@F n_tech_fa_pers_cd|char(5)||Techniker, welcher den nächsten Einsatz durchführen soll / kann leer sein / wird beim Arbeitsbericht- Aufbau gelöscht, wenn abericht_kz = 'a'
@F abericht_kz|char(1)||Kennzeichen für den Arbeitsbericht- Aufbau / wird vom Arbeitsberichtaufbau auf leer gesetzt / Anmerkung für das Verwaltungsprogramm: beim Setzen auf 'a' oder 'n' werden die Werte der n_einsatz_datz und n_tech_fa_pers_cd entsprechenden Felder in die a_einsatz_dat und a_tech_fa_pers_cd entsprechenden Felder gestellt Weiters wird das n_einsatz_datz entsprechende Feld gelöscht.
@F abericht_kz|char(1)||' '|es soll kein Arbeitsbericht- Aufbau erfolgen
@F abericht_kz|char(1)||'a'|Arbeitsbericht aufbauen und Auftrag auf abgeschlossen setzen
@F abericht_kz|char(1)||'s'|wie 'a', zusätzlich wird das Gerät ausgeschieden
@F abericht_kz|char(1)||'n'|Arbeitsbericht aufbauen und Auftrag auf "neuerlicher Einsatz notwendig" setzen
@F a_einsatz_dat|date +n||Einsatz- Datum für Arbeitsbericht- Aufbau / kann null sein / Wird beim Aufbau des Arbeitsberichtes gelöscht / Beim Setzen wird n_einsatz_datz gelöscht,
@F a_tech_fa_pers_cd|char(5)||Techniker für Arbeitsbericht- Aufbau / kann leer sein / Wird beim Aufbau des Arbeitsberichtes auf leer gesetzt
@F vb_dat|date +n||Datum, an dem der Verbringungsbeleg gedruckt wurde
@E
@T s_auf_geraet
@D Geräte zum Serviceauftrag / wird für das "Standardgerät" lt. Tabelle s_auf automatisch angelegt / hier können weitere Geräte erfasst werden, wenn lt Parameter [pfu_param.svc_mehrere_geraete_pro_auftrag_jn] vorgesehen
@F fa_nr|smallint(3)|p2
@F auf_nr|integer(7)|p1,f
@F s_artik_cd|char(20)|f|der zu servicierende Artikel
@F s_geraet_cd|char(40)||das Gerät muß abhängig von artik.muss_geraet_cd_jn angegeben werden / das Gerät muß bei der Neuanlage den selben Kunden, wie der Auftrag haben, dies gilt natürlich nicht für das Dummy- Gerät
@F s_geraet_artik_cd|char(20)|p3,f|nur für den f- Key auf das Gerät: / kein AEO / 2 möglichkeiten: / Kein Gerät angegeben: / s_geraet_cd = "" / s_geraet_artik_cd = fa.dummy_artik_cd / dies ist ein Dummy- Gerät / dies ist nur erlaubt, wenn artik.muss_geraet_cd_jn = 'n' / Gerät angegeben: / s_geraet_cd = lt. Eingabe / s_geraet_artik_cd = s_artik_cd / F- Key: s_geraet_cd, s_geraet_artik_cd, fa_nr geraet
@F s_auf_mg|decimal(9,0)||Menge der zu Reparierenden Geräte / = 1, wenn s_geraet_cd <> "" / hat keinen Einfluß auf die Positionen
@F s_geraet_dr|char(40)|p4|Gerätenummer zum Andrucken / ist fix s_geraet_cd, wenn s_geraet_cd nicht leer ist / kann eingegeben werden, wenn s_geraet_cd leer ist
@E
@T s_auf_txt
@D Text zum Service Auftrag
@F fa_nr|smallint(3)|p2
@F auf_nr|integer(7)|p1,f
@F txt_typ_kz|char(1)|p3|Texttyp / "r" Richtext / wenn [param.appl_txt_kz <> "p"] / Standardfont "Arial 10" / "p" Plaintext / wenn [param.appl_txt_kz = "p"]
@F zeile_nr|smallint|p4|Zeilennummer
@F s_auf_wo_kz|char(2)||Art des Textes
@F s_auf_wo_kz|char(2)||f|Fehlerbeschreibungstext
@F s_auf_wo_kz|char(2)||ka|Kostenvoranschlaganfangstext
@F s_auf_wo_kz|char(2)||ke|Kostenvoranschlagendtext
@F s_auf_wo_kz|char(2)||aa|Arbeitsberichtanfangstext für den aufzubauenden Arbeitsbericht / wird beim Aufbau des Arbeitsberichtes gelöscht / wird vor den Positionen gedruckt
@F s_auf_wo_kz|char(2)||ae|Arbeitsberichtendtext für den aufzubauenden Arbeitsbericht / wird beim Aufbau des Arbeitsberichtes gelöscht / wird nach den Positionen gedruckt
@F s_auf_wo_kz|char(2)||ra|Anfangsext für den Beleg, welcher das Verbringen des Geräts an die externe Reparaturstelle begleitet
@F s_auf_wo_kz|char(2)||re|Endtext für den Beleg, welcher das Verbringen des Geräts an die externe Reparaturstelle begleitet
@F s_auf_wo_kz|char(2)||i|interner Text
@F rech_jn|char(1)||auf Rechnung drucken / ist bei wo_kz in ( "ka", "ke", "i", "ra", "re" ) fix "n"
@F fett_jn|char(1)||fett drucken / fix "n", wenn [txt_typ_kz = "r"]
@F unterstrichen_jn|char(1)||unterstrichen drucken / fix "n", wenn [txt_typ_kz = "r"]
@F s_auf_txt|varchar(max)||Auftragstext- Zeile / generierter Plaintext (s_auf_rtxt) , wenn [txt_typ_kz = "r"] / eingegebener Text, sonst
@F s_auf_txt_dbid|integer identity||ROWID für Retrieve Richtext / durch DB-Default mit serieller Nummer belegt
@F s_auf_rtxt|varbinary(max)||Serviceauftragstext Richtext / wenn [txt_typ_kz = "p"], durch DB-Default mit Leerstring belegt
@E
@I unique index i1_s_auf_txt (s_auf_txt_dbid)
@T s_kunde
@D Servicedaten zum Kunden / muß nicht vorhanden sein / wenn vorhanden, werden bei der Auftragsanlage die entsprechenden Felder aus s_kunde vorgeschlagen
@F kunde_cd|char(10)|p1,f|Kundennummer
@F fa_nr|smallint(3)|p2|Firma
@F vkrech_kz|char(2)||Art der Fakturierung
@F vkrech_kz|char(2)||d|Sammelrechnung pro Debitorennummer
@F vkrech_kz|char(2)||k|Sammelrechnung pro Kundennummer
@F vkrech_kz|char(2)||a|Sammelrechnung pro Auftrag
@F vkrech_kz|char(2)||ka|Sammelrechnung pro Kundenauftragsnummer + Datum
@F vkrech_kz|char(2)||l|Sammelrechnung pro Lieferschein
@F vkrech_kz|char(2)||lr|Lieferschein + Rechnung sofort
@F vkrech_kz|char(2)||r|Rechnung = Lieferbeleg
@F vkrech_sel_fkz|char(3)||Selektionskennzeichen zum Zusammenstellen von Lieferscheinen zu einer Sammelrechnung / Es sollte aber pfu_kz angelegt werden.
@F zahlart_cd|char(5)|f|Zahlungsart
@F versart_cd|char(5)|f|Versandart
@F liefbed_cd|char(5)|f|Lieferbedingung
@F anz_vkrech|smallint(2)||Anzahl Rechnungen
@F anz_vklfs|smallint(2)||Anzahl Lieferscheine, muß > 0 sein, wenn vkrech_kz <> 'r', sonst 0
@F preisli_cd|char(5)|f|Preislistencode
@F vklfs_preis_jn|char(1)||auf dem Reparaturschein sollen Preise gedruckt werden
@N Zahlungskonditionen:
@F skonto1_prz|decimal(4,2)||1. Skontoprozentsatz
@F skonto1_tg|smallint(3)||dazu Ziel- Tage
@F skonto2_prz|decimal(4,2)||2. Skontoprozentsatz
@F skonto2_tg|smallint(3)||dazu Ziel- Tage
@F netto_tg|smallint(3)||Ziel- Tage für Netto- Zahlung
@F wv_s_artik_cd|char(20)|f|Sethauptartikel für Wartungsvertragsauftrag / setfrei_kz muß "s" sein / Beim Aufbau eines Wartungsvertragsverrechnungsauftrages wird dieser Artikel herangezogen / Der Artikel darf keine Setbestandteile haben
@E
@T s_verrechart
@D Verrechnungsart für Serviceposition / es muß folgende Row geben: / s_vrechart_cd = "" / s_vrechart_mc = "keine Serviceposition" / verrechnenbar_jn = "j" / duest_kz = "d"
@F s_verrechart_cd|char(5) (p)|
@F s_verrechart_mc|char(40)|
@F verrechenbar_jn|char(1)||verrechenbar
@F duest_kz|char(1)||"d" ... Duest wie nicht Service / "k" … Duest = 0 / "e" … Duest immer eingeben
@E
@T s_vlfs_txt
@D Arbeitsbericht- Text
@F vlfs_nr|integer(7)|p1,f
@F fa_nr|smallint(3)|p2
@F txt_typ_kz|char(1)|p3|Texttyp / "r" Richtext / wenn [param.appl_txt_kz <> "p"] / Standardfont "Arial 10" / "p" Plaintext / wenn [param.appl_txt_kz = "p"]
@F zeile_nr|smallint|p4|Zeilennummer
@F s_auf_wo_kz|char(2)||Art des Textes
@F s_auf_wo_kz|char(2)||aa|Arbeitsberichtanfangstext für den aufzubauenden Arbeitsbericht / wird beim Aufbau des Arbeitsberichtes gelöscht / wird vor den Positionen gedruckt
@F s_auf_wo_kz|char(2)||ae|Arbeitsberichtendtext für den aufzubauenden Arbeitsbericht / wird beim Aufbau des Arbeitsberichtes gelöscht / wird nach den Positionen gedruckt
@F rech_jn|char(1)||auf Rechnung drucken
@F fett_jn|char(1)||fett drucken / fix "n", wenn [txt_typ_kz = "r"]
@F unterstrichen_jn|char(1)||unterstrichen drucken / fix "n", wenn [txt_typ_kz = "r"]
@F s_vlfs_txt|varchar(max)||Auftragstext- Zeile / generierter Plaintext (s_vlfs_rtxt), wenn [txt_typ_kz = "r"] / eingegebener Text, sonst
@F s_vlfs_txt_dbid|integer identity||ROWID für Retrieve Richtext / durch DB-Default mit serieller Nummer belegt
@F s_vlfs_rtxt|varbinary(max)||Servicelieferscheintext Richtext / wenn [txt_typ_kz = "p"], durch DB-Default mit Leerstring belegt
@E
@I unique index i1_s_vlfs_txt (s_vlfs_txt_dbid)
@S st Statistiktabellen
@T st_ar_mon
@D Artikelmonatsstatistik (g)
@F artik_cd|char(20)|p1
@F fa_nr|smallint(3)|p2
@F fil_nr|smallint(3)|p3|Filiale
@F mon|char(6)|p4|Monat in Form JJJJMM
@F ums|decimal(11,2)||Umsatz
@F weins|decimal(11,2)||Wareneinsatz
@F umsmg|decimal(11,2)||Umsatzmenge
@F verbmg|decimal(11,2)||Verbrauchsmenge / Summe aus ka_bel_pos.menge + vlfs_pos.verbmg + divlgb.verbmg
@E
@I index i1_st_ar_mon (mon, fa_nr, fil_nr)
@T st_ar_tag
@D Artikelmonatsstatistik (g)
@F artik_cd|char(20)|p1
@F fa_nr|smallint(3)|p2
@F fil_nr|smallint(3)|p3|Filiale
@F tag|date|p4|Tag
@F ums|decimal(11,2)||Umsatz
@F weins|decimal(11,2)||Wareneinsatz
@F umsmg|decimal(11,2)||Umsatzmenge
@F verbmg|decimal(11,2)||Verbrauchsmenge / Summe aus ka_bel_pos.menge + vlfs_pos.verbmg + divlgb.verbmg
@E
@I index i1_st_ar_tag (tag, fa_nr, fil_nr)
@T st_kd_mon
@D Kundenmonatsstatistik (g)
@F kunde_cd|char(10)|p1
@F fa_nr|smallint(3)|p2
@F fil_nr|smallint(3)|p3|Filiale
@F mon|char(6)|p4|Monat in Form JJJJMM
@F ums|decimal(11,2)||Umsatz
@F weins|decimal(11,2)||Wareneinsatz
@F umsmg|decimal(11,2)||Umsatzmenge
@E
@I index i1_st_kd_mon (mon, fa_nr, fil_nr)
@T st_kd_ar_mon
@D Kundenartikelmonatsstatistik (g)
@F kunde_cd|char(10)|p1
@F artik_cd|char(20)|p2
@F fa_nr|smallint(3)|p3
@F fil_nr|smallint(3)|p4|Filiale
@F mon|char(6)|p5|Monat in Form JJJJMM
@F ums|decimal(11,2)||Umsatz
@F weins|decimal(11,2)||Wareneinsatz
@F umsmg|decimal(11,2)||Umsatzmenge
@E
@I index i1_st_kd_ar_mon ( artik_cd, fa_nr, mon, kunde_cd )
@I index i2_st_kd_ar_mon (mon, fa_nr, fil_nr)
@T st_lf_mon
@D Lieferantenmonatsstatistik (g)
@F lief_cd|char(10)|p1
@F fa_nr|smallint(3)|p2
@F fil_nr|smallint(3)|p3|Filiale
@F mon|char(6)|p4|Monat in Form JJJJMM
@F ek_wert|decimal(11,2)||Einkaufswert
@F est_wert|decimal(11,2)||Einstandswert
@F ek_mg|decimal(11,2)||Einkaufsmenge
@E
@I index i1st_lf_ar_mon (mon, fa_nr, fil_nr)
@T st_lf_ar_mon
@D Lieferantenmonatsstatistik (g)
@F lief_cd|char(10)|p1
@F artik_cd|char(20)|p2
@F fa_nr|smallint(3)|p3
@F fil_nr|smallint(3)|p4|Filiale
@F mon|char(6)|p5|Monat in Form JJJJMM
@F ek_wert|decimal(11,2)||Einkaufswert
@F est_wert|decimal(11,2)||Einstandswert
@F ek_mg|decimal(11,2)||Einkaufsmenge
@E
@I index i1_st_lf_ar_mon ( artik_cd, fa_nr, mon, lief_cd )
@I index i1_st_lf_ar_mon (mon, fa_nr, fil_nr)
@T st_statkorr
@D Statistik Korrektur(ng) / wird vom Statistikaufbau verarbeitet und gelöscht / Werte müssen aus vlfs_pos * -1 selektiert werden / vlfs_pos.stat_gebucht_jn und vlfs_pos.verb_gebucht_jn müssen auf 'n' gesetzt werden
@F beleg_art|char(1)|p0|v vlfs_pos / b ka_bel_pos / e elfs_pos
@F vlfs_nr|integer(7)|p1|entspricht vlfs_pos.vlfs_nr bzw. ka_bel_pos.bel_nr bzw. elfs_pos.elfs_nr
@F fa_nr|smallint(3)|p2|entspricht vlfs_pos.fa_nr bzw. ka_bel_pos.fa_nr bzw. elfs_pos.fa_nr
@F ein_auf_nr|integer(7)|p3|entspricht vlfs_pos.ein_auf_nr bzw. 0 bzw. 0
@F auf_pos_nr|smallint(4)|p4|entspricht vlfs_pos.auf_pos_nr bzw. ka_bel_pos.pos_nr nzw. elfs_pos.elfs_pos_nr
@F ums|decimal(11,2)||Umsatz bzw. Einkaufswert
@F weins|decimal(11,2)||Wareneinsatz kzw. Einstandswert
@F umsmg|decimal(12,3)||Umsatzmenge bzw. Einkaufsmenge
@F verbmg|decimal(12,3)||Verbrauchsmenge bze. 0
@F alt_artik_cd|char(20)|
@F alt_kunde_cd|char(10)||AltKunde bzw. AltLieferant
@E
@T sts_grpschema
@D Definition eines Gruppenschemas für eine statistische Auswertung
@F grpschema_cd|char(10)|p1
@F grpschema_mc|char(40)|
@F summe_jn|char(1)||Der Summenblock wird gedruckt / wird, wenn "n" sinnvollerweise mit Gruppe 1 verwendet keine Endsumme auf Vertreterauswertung, aber Seitenwechsel je Vertreter
@N 1. Gruppe der Liste / ist diese in Verwendung, erfolgt beim Gruppenwechsel ein Seitenvorschub / es kann jede Gruppe unabhängig davon, ob eine Untergruppe definiert ist oder nicht, verwendet werden
@F g1_cd_name|char(100)||z.B. "artik.ahg_fgr_cd", "artik.artik_cd" / "'#'" Daten der Gruppe sind im DW invisible
@F g1_mc_name|char(100)||z.B.: "fgr1.fgr_mc", "artik.artik_mc"
@F g1_titel|char(20)||z.B.: "Artikelhauptgruppe", "Artikel"
@F g1_sort_kz|char(1)||Sortierung innerhalb der Gruppe nach / 'm'..g1_mc_name (Matchcode) / 'c'…g1_cd_name (Gruppencode)
@N 2. Gruppe der Liste
@F g2_cd_name|char(100)||z.B. "artik.ahg_fgr_cd", "artik.artik_cd" / "'#'" Daten der Gruppe sind im DW invisible
@F g2_mc_name|char(100)||z.B.: "fgr1.fgr_mc", "artik.artik_mc"
@F g2_titel|char(20)||z.B.: "Artikelhauptgruppe", "Artikel"
@F g2_sort_kz|char(1)||Sortierung innerhalb der Gruppe nach / 'm'..g2_mc_name (Matchcode) / 'c'…g2_cd_name (Gruppencode)
@N 3. Gruppe der Liste
@F g3_cd_name|char(100)||z.B. "artik.ahg_fgr_cd", "artik.artik_cd" / "'#'" Daten der Gruppe sind im DW invisible
@F g3_mc_name|char(100)||z.B.: "fgr1.fgr_mc", "artik.artik_mc"
@F g3_titel|char(20)||z.B.: "Artikelhauptgruppe", "Artikel"
@F g3_sort_kz|char(1)||Sortierung innerhalb der Gruppe nach / 'm'..g3_mc_name (Matchcode) / 'c'…g3_cd_name (Gruppencode)
@N 4. Gruppe der Liste
@F g4_cd_name|char(100)||z.B. "artik.ahg_fgr_cd", "artik.artik_cd" / "'#'" Daten der Gruppe sind im DW invisible
@F g4_mc_name|char(100)||z.B.: "fgr1.fgr_mc", "artik.artik_mc"
@F g4_titel|char(20)||z.B.: "Artikelhauptgruppe", "Artikel"
@F g4_sort_kz|char(1)||Sortierung innerhalb der Gruppe nach / 'm'..g4_mc_name (Matchcode) / 'c'…g4_cd_name (Gruppencode)
@N Detail der Liste
@F d_cd_name|char(100)||z.B. "artik.ahg_fgr_cd", "artik.artik_cd"
@F d_mc_name|char(100)||z.B.: "fgr1.fgr_mc", "artik.artik_mc"
@F d_titel|char(20)||z.B.: "Artikelhauptgruppe", "Artikel"
@F d_sort_kz|char(1)||Sortierung innerhalb der Gruppe nach / 'm'..d_mc_name (Matchcode) / 'c'…d_cd_name (Gruppencode)
@F ums_col_name|char(200)||z.B.: "st_.ums"
@F weins_col_name|char(200)||z.B.: "st_.weins" / "0" Deckungsbeitrags- Columns und Überschriften sind unsichtbar
@F umsmg_col_name|char(200)||z.B.: "st_.umsmg" / "0" Menge und zugehörige Überschrift sind unsichtbar
@F from|char(128)|
@F where1|char(255)|
@F where2|char(255)|
@F ums_tab_name|char(200)||Name der Umsatztabelle (zB: st_ar_mon)
@F mon_col_name|char(200)||Name der Periodencolumn (zB: mon bzw. vrech_mon)
@E
@T sts_mon_per
@D Periode eines Auswertungsperiodenschemas zu einem konkreten Kalendermonat (g)
@F perschema_cd|char(10)|p1
@F auswert_mon|char(6)|p2
@F per_kz|char(2)|p3
@F von_mon|char(6)|
@F bis_mon|char(6)|
@E
@T sts_darstellung
@D Definition eines Darstellungsschemas für statistische Auswertungen
@F darstellung_cd|char(10)|p1
@F darstellung_mc|char(40)|
@F zeilig_kz|char(1)||1 ... einzeilig / 2 ... zweizeilig: Periode-1, Periode-2 / 3 ... dreizeilig: Periode-1, Periode-2, Abweichung von 2 nach 1 (2=100%) / Anmerkung: / jede Zeile besteht aus: / Periode a, Periode b, Abweichung von b nach a (b=100%)
@F umsmg_colw_a|integer||Spaltenbreite Umsatzmenge in Pixels Periode a
@F ums_colw_a|integer||Spaltenbreite Umsatz in Pixels
@F weins_ colw_a|integer||Spaltenbreite Wareneinsatz in Pixels
@F dbabs_colw_a|integer||Spaltenbreite DB-absolut in Pixels
@F dbproz_ colw_a|integer||Spaltenbreite DB% in Pixels
@F umsmg_colw_b|integer||Spaltenbreite Umsatzmenge in Pixels Periode b
@F ums_colw_b|integer||Spaltenbreite Umsatz in Pixels
@F weins_ colw_b|integer||Spaltenbreite Wareneinsatz in Pixels
@F dbabs_colw_b|integer||Spaltenbreite DB-absolut in Pixels
@F dbproz_ colw_b|integer||Spaltenbreite DB% in Pixels
@F umsmg_colw_abw|integer||Spaltenbreite Umsatzmenge in Pixels Abweichung
@F ums_colw_abw|integer||Spaltenbreite Umsatz in Pixels
@F weins_ colw_abw|integer||Spaltenbreite Wareneinsatz in Pixels
@F dbabs_colw_abw|integer||Spaltenbreite DB-absolut in Pixels
@F format_ums_weins|char(20)||Formatangabe Umsatz, Wareneinsatz / z.B: "#,##0.00"
@F fromat_umsmg|char(20)|
@F format_dbabs|char(20)|
@F format_dbproz|char(20)|
@F format_abwproz|char(20)|
@F orientation|char(1)||h ….. A4 hoch / q ..... A4 quer
@F margin_left|integer||linker Rand in Pixels
@F margin_right|integer||rechter Rand in Pixels
@F margin_top|integer||Rand oben in Pixels
@F margin_bottom|integer||Rand unten in Pixels
@F font_size|smallint||Fontgröße in Punkt (10, 8, etc.)
@F grid_display_jn|char(1)||Gitternetzlinien drucken
@F mc_colw|integer||Spaltenbreite Code + Matchcode
@E
@T sts_perschema
@D Definition eines Auswertungsperiodenschemas für statistische Auswertungen
@F perschema_cd|char(10)|p1
@F perschema_mc|char(40)|
@F fa_nr|smallint(3)|f|Firmennummer für Geschäftsjahresermittlung
@E
@T sts_perschema_per
@D Definition einer Periode in einem Auswertungsperiodenschema / Beim Insert werden für die Monate des Zeitraumes vom aktuellen Jahr – 2 bis zum aktuellen Jahr + 5 die entsprechenden Rows in st_mon_per inseriert. Bei einer Änderung werden die entsprechenden Rows in st_mon_par deletiert und neu inseriert, beim Löschen deletiert. / (Einer Row entsprechen also 96 Rows in st_mon_per.)
@F perschema_cd|char(10)|p1,f
@F per_kz|char(2)|p2|"a1" links oben / "a2" links unten / "b1" rechts oben / "b2" rechts unten
@F von_mon_basis_kz|char(1)||"m" Auswertungsmonat / "g" 1. Monat des Geschäftsjahres, in dem der Auswertungsmonat liegt / "j" 1. Monat des Kalenderjahres, in dem der Auswertungsmonat liegt
@F von_mon_relativ|smallint(2)||Von- Monat der Auswertungsperiode relativ zum Monat lt. von_mon_basis_kz / Beispiele (gelten äquivalent auch für bis_mon_relativ):
@F von_mon_relativ|smallint(2)||von_mon_basis_kz|von_mon_relativ
@F von_mon_relativ|smallint(2)||Auswertungsmonat|m|0
@F von_mon_relativ|smallint(2)||1. Monat des 2. Quartals des Geschäftsjahres des Auswertungsmonats|g|3
@F von_mon_relativ|smallint(2)||letzter Monat des Geschäftsjahres des Auswertungsmonats|g|11
@F von_mon_relativ|smallint(2)||Auswertungsmonat des Vorjahres|m|-12
@F bis_mon_basis_kz|char(1)||"m" Auswertungsmonat / "g" 1. Monat des Geschäftsjahres, in dem der Auswertungsmonat liegt / "j" 1. Monat des Kalenderjahres, in dem der Auswertungsmonat liegt
@F bis_mon_relativ|smallint(2)||Bis- Monat der Auswertungsperiode relativ zum Monat lt. von_mon_basis_kz
@F per_mc|char(20)||Matchcode der Periode / wird in Auswertungen als Überschrift angezeigt bzw. gedruckt
@E
@T tc2easy
@D Schnittstellentabelle EasyArchiv /  / Ermittlung der Felder über View [tc2easy_V]
@F tc2easy_snr|decimal(14,0) (p)|
@F fa_nr|smallint(3)||Firma lt.Beleg
@F fil_nr|smallint(3)||Filiale lt. Beleg
@F abt_nr|smallint(3)||Abteilung lt.Beleg
@F beleg_nr|integer (9)||Belegnummer / lt. Beleg [auf_|vlfs_|vrech_|best_|elfs_|erech_nr|erech_bn_nr]
@F archiv_belegtyp_fkz|char(10)||Belegtyp für Archiv / lt. [archiv_dok]
@F archiv_matchcode|varchar(60)||Matchcode Geschäftspartner / lt. Adresse Beleg [kunde_|lief_|debitor_mc]
@F archiv_name|varchar(200)||Name Geschäftspartner / lt. Adresse Beleg / name1 + " " + name2 + " " + name3 + " " name4
@F archiv_beleg_dat|date||Belegdatum / lt. Beleg [auf_|vlfs_|vrech_|best_|elfs_|erech_dat|erech_bn_dat]
@F archiv_kdlf_cd|char(10)||Geschäftspartnernummer / lt. Beleg [kunde_|lief_cd] oder [debitor_|kreditor_nr]
@F archiv_betr|decimal(11,2)||Rechnungsbetrag inkl. USt / lt. vrech bzw. erech / sonst 0
@F archiv_bc|char(13)||Barcode (lt. Beleg) / [auf_|vlfs_|vrech]_barcode / [best_|elfs_|erech|erech_bn_]_barcode
@F archiv_file|varchar(255)||Filename inklusive Pfad / Pfad zu TC-Archiv-Dokument
@F archiv_bereich|char(5)||Bereichszuordnung Archiv / "vk" "Verkauf" / "ek" "Einkauf"
@F erl_tc2easy_snr|integer(9)||Erledigungsnummer / 0 nicht verarbeitet / >0 verarbeitet
@E
@I index i1_tc2easy (erl_tc2easy_snr)
@T tc2easy_V
@D SchnittstellenView EasyArchiv /  / Join [archiv_dok] mit den möglichen TC-Tabellen / UNION-Select / PKEY muss eindeutig sein / Columns ident mit [tc2easy] / damit individuelle Anpassungen der Schnittstelle einfach möglich
@F fa_nr|p1|
@F beleg_nr|p4|
@F archiv_belegtyp_fkz|p5|
@N archiv_matchcode
@N archiv_name
@N archiv_beleg_dat
@N archiv_kdlf_cd
@N archiv_betr
@N archiv_bc
@N archiv_ext_beleg_nr
@N archiv_bereich
@E
@T tcscangrp
@D Scangruppen für TCScan
@F tcscangrp_cd|char(10)|p1|Scangruppe
@F tcscangrp_mc|char(40)||Matchcode
@F druck_nr_kz|char(10)||Druckkenzzeichen lt. pfu_Druckart / a = Auftrag / b = Bestellung / el = Eingangsalieferschein / er = Eingangsrechnung / vl = Verkaufslieferschein / vr = Verkaufsrechnung
@F archiv_beleg_kz|char(2)||Archivbelegkennzeichen / siehe auch archiv.archiv_beleg_kz
@F darf_manuell_jn|char(1)||Scangruppe darf manuell ausgewählt werden.
@F druckart_cd|char(8)|f|Druckart für Dokument
@E
@T tcscangrp_druckart
@D Druckarten ein Scangruppe, die im TCScan-Fenster angezeigt werden sollen / nur diese Druckarten werden im Register "PDF" des TCScan-Fensters angezeigt / Anmerkung: über die Dokumente-Schaltfläche werden alle Dokumente des DruckNrKz angezeigt / ist ein Dokument dieser Druckart vorhanden, wird [tcscan.dokument_vorh_jn = "j"] gesetzt (Kundenbeleg gilt als zurückgescannt oder signiert)
@F tcscangrp_cd|char(10)|p1|Scangruppe
@F druckart_cd|char(8)|p2,f|Druckart für Dokument
@E
@T tcscantag
@D Tags für TCScan
@F tcscantag_cd|char(10)|p1|Code des Tags
@F tcscantag_mc|char(40)||Bezeichnung des Tags
@E
@T tcscangrp_tag
@D Vorschlag Tags zu Scangruppe / Vorschlag bei Erfassung TCscan
@F tcscangrp_cd|char(10)|p1,f|Scangruppe
@F tcscantag_cd|char(10)|p2,f|Tag
@F tag_pflicht_jn|char(1)||Pflichteingabe im TC-Scan [tcscan_tags.tcscantag_wert <> ""]
@E
@T tcscan
@D Trade Control Scan
@F tcscan_snr|integer|p1|Serial, vergabe über pfu_Serial
@F scan_barcode|varchar(128)||Eindeutiger Barcode
@F fa_nr|smallint||Firma
@F tcscangrp_cd|char(10)|f|Scangruppe
@F druckart_cd|char(8) (gn)|f|Druckart / bei neuanlage auf [tcscangrp] belegt
@F scan_beleg_nr|char(20)||Belegnummer
@F scan_beleg_dat|datetime||Belegdatum
@F dokument_vorh_jn|char(1)||Es gibt zumindest 1 zugeordnetes PDF
@F scan_adr_snr|integer||Adresse des Scans z.b. Kundenmatchcode / Kann auch 0 sein
@F scan_mach_uni|integer||Um den Datensatz eindeutig zu gestalten / Wenn scan_barcode = blank tcscan_snr / Wenn scan_barcode belegt 0
@E
@I Unique index(scan_Barcode,mach_uni)
@I index (dokument_vorh_jn)
@I index (scan_adr_snr)
@T tcscan_tags
@D Zuordnung Tags zum Scan / Vorschlag nach eingabe Scangruppe
@F tcscan_snr|integer|p1,f|Serial, vergabe über pfu_Serial
@F tcscantag_cd|char(10)|p2,f|Tag zum Scan
@F tcscantag_wert|varchar(255)||Beschlagwortung des Tags COLLATION LATIN1_GENERAL_CI_AI
@E
@T tcscan_txt
@D tcscan_txt (neu), Texte zum Scan
@F tcscan_snr|integer|p1,f|Serial, vergabe über pfu_Serial
@F zeile_nr|smallint|p2|Laufende Zeilennummer
@F tcscan_txt|varchar(255)||Text, COLLATION Latin1_General_CI_AI
@E
@T txt
@D Textbaustein
@F txt_cd|char(20)|p1|Textbausteincode
@F txt_kz|char(1)||p|Positionstext
@F txt_kz|char(1)||e|Anfang- oder Endtext
@E
@T txt_txt
@D Textbaustein- Textzeile
@F txt_cd|char(20)|p1|Textbausteincode
@F txt_typ_kz|char(1)|p2|Texttyp / "r" Richtext / Standardfont "Arial 10", wenn txt_kz = "e" / Standardfont Position, wenn txt_kz = "p" / "p" Plaintext /  / Belegung abhängig von [param.appl_txt_kz] u. [txt.txt_kz]: / txt_kz = "e" "p", wenn appl_txt_kz = "p", sonst "r" / txt_kz = "p" "r", wenn appl_txt_kz = "r", sonst "p"
@F zeile_nr|smallint|p3|Zeilennummer
@F sprache_cd|char(5)|f|Sprachencode
@F fett_jn|char(1)||Fettdruck / fix "n", wenn [txt_typ_kz = "r"]
@F unterstrichen_jn|char(1)||unterstrichen drucken / fix "n", wenn [txt_typ_kz = "r"]
@F ab_jn|char(1)||Andruck auf der AB / wird nur bei Auflösung eines Textbausteincodes (#-Logik) im Dialog verwendet / wird nicht bei fix lt. Firmenstamm, Auftragsart,...definierten Textbausteinen, die erst beim Druck aufgelöst warden, verwendet
@F kommsch_jn|char(1)||Andruck am Kommissionsschein / siehe oben
@F lfs_jn|char(1)||Andruck am Lieferschein / siehe oben
@F rech_jn|char(1)||Andruck auf der Rechnung / siehe oben
@F off_jn|char(1)||Andruck am Offert / siehe oben
@F best_jn|char(1)||Andruck auf der Bestellung / siehe oben
@F txt_txt|varchar(max)||Text / generierter Plaintext (txt_rtxt) , wenn [txt_typ_kz = "r"] / eingegebener Text, sonst
@F txt_txt_dbid|integer identity||ROWID für Retrieve Richtext / durch DB-Default mit serieller Nummer belegt
@F txt_rtxt|varbinary(max)||Artikeltext Richtext / wenn [txt_typ_kz = "p"], durch DB-Default mit Leerstring belegt
@E
@I unique index i1_txt_txt (txt_txt_dbid)
@T ueb
@D Überschriftsvorlagen für Auftragspositionsüberschrift
@F ueb_cd|char(20) (p)|
@F newpage_jn|char(1)||Seitenvorschub bevor Überschrift gedruckt wird
@F summe_jn|char(1)||Summe wird nach der letzten Artikelposition dieser Überschrift angedruckt
@F endsumme_jn|char(1)||Positionen, die dieser Überschrift zugeordnet sind, rechnen in Endsumme
@F summe_txt|varchar(60)||Textierung für Überschriftssumme
@F ueb_txt_cd|char(20)||Textbausteincode, der Überschriftstext beinhaltet
@E
@T uidprueflog
@D Logfile der UID-Prüfungen
@F uidprueflog_snr|bigint(p)||Serial Number / Vergabe über pfu_serial
@F ustid|char(14)||UID Nummer
@F uidpruef_datz|datetime||Zeitpunkt der Prüfung
@F applpers_cd|char(10)||User, der die Prüfung durchgeführt hat
@F fa_nr|smallint||Firmennummer
@F debitor_nr|integer +n||Debitorennummer
@F kreditor_nr|integer +n||Kreditiorennummer
@F fion_returncode_nr|integer||Finanz Online Returncode
@F fion_name|varchar(500) +n||Name lt. Finanzonline
@F fion_adr1|varchar(100) +n||Adresszeilen lt. Finanzonlie
@F fion_adr2|varchar(100) +n|
@F fion_adr3|varchar(100) +n|
@F fion_adr4|varchar(100) +n|
@F fion_adr5|varchar(100) +n|
@F tc_name1|varchar(50)||Adresse in TC zum Zeitpunkt der Prüfung
@F tc_name2|varchar(50)|
@F tc_name3|varchar(50)|
@F tc_name4|varchar(50)|
@F tc_strasse|varchar(50)|
@F tc_land_cd|char(3)|
@F tc_plz|varchar(10)|
@F tc_ort|varchar(50)|
@F adrpruef_kz|char(1)||Adressprüfung KZ / "-" – Es ist keine Prüfung der Adresse erfolgt / "j" = Manuelle Prüfung – Adresse wurde bestätigt / "n" – Manuelle Prüfung – Adresse wurde als falsch interpretiert
@E
@I index i1_uidprueflog (debitor_nr, fa_nr, uidpruef_datz)
@I index i2_uidprueflog (kreditor_nr, fa_nr, uidpruef_datz)
@T ust
@F ust_cd|char(10)|p1|Ustcode
@F ust_mc|char(20)|
@F ust_kz|char(1)||Ust-Symbol für Faktura
@F ust_txt_cd|char(20)||Code des Textbausteines welcher am Ende der Faktura, bzw. der AB gedruckt wird / select distinct txt_cd, zeile_nr, txt_txt from vrech_ust, ust, txt_txt / where join and ust_txt_cd <> ' ' and sprache_cd = ? order by 1, 2
@F dn_ust_kz|char(1) +n||Datanorm UST-Kennzeichen / 1 = Normaler Mwst-Satz / 2 = erhöhter Mwst-Satz / 3 = verminderter Mwst-Satz
@F ek_ustart_kz|char(1)||Umsatzsteuerart-Kennzeichen für Eingangsrechnung bei Verbuchung in Jetfibu (ab Release 15) / 1 = Vorsteuer / 3 = Erwerbsteuer
@E
@T ust_proz
@F ust_cd|char(10)|p1,f|Ustcode
@F ab_dat|date|p2|gültig ab / Der richtige Satz wird immer mit dem Rechnungsdatum ermittelt!
@F bis_dat|date||gültig bis
@F ust_nr|char(4)||Ust- Nummer lt. Fibu
@F ust_prz|decimal(4,2)||Ust- Prozentsatz
@F erwerb_ust_prz|decimal(4,2)||Ust- Prozentsatz, der bei der Erstellung der Fibuschnittstelle herangezogen wird, wenn bei Erwerbsteuer [liefsach_kz = "e"] der Prozentsatz oder der Steuerbetrag angegeben werden muss
@E
@T versart
@D Versandarten / Es gibt einen Dummy-Satz mit versart_cd = " "
@F versart_upid|bigint +n|
@F versart_cd|char(5)|p1
@F versart_bez|char(40)|
@F muss_zahlart_cd|char(5)||Wenn nicht Leer, muß Auftrag diese Zahlungsart haben. / gilt vor kunde.zahlart_cd / gilt nach aufart.a_muss_zahlart_cd
@F is_verkzweig|smallint(1)||Intrastat Verkehrszweig 1-9
@F shipping_method|varchar(40)||WebShop Versandart
@F magento_shipm_kz|char(1)||KZ Magento Shipment Schnittstelle / "k" = Keine Magento Shipmente Daten ausgeben / "l" = Lieferschein wird sofort mit dem Druck als versendet übertragen / "v" = Lieferschein wird nach Bearbeitung im Versandpaket als versendet (inkl. Tracingnummern) übertragen.
@F magento_notify_jn|char(1)||Bei Magento Shipment soll eine Versandbestätigung von Magento versendet werden.
@F magento_carrier_code|varchar(40)||Magento Carrier Code für Magento Versanddaten Schnittstelle
@F magento_shipm_title|varchar(40)||Titel für Paketversand
@F kundeerl_liefadr_kz|char(1)||KZ Bestimmung des Landes für die Ermittlung der Kundenerlösgruppe / l = Lieferadresse / f = Filialadresse (Abholung)
@E
@T vert
@D Vertreter
@F vert_cd|char(10)|p1
@F vert_mc|char(40)|
@E
@T vkkond
@D Verkaufskonditionen / siehe unbedingt vkkondart
@F vkkond_upid|bigint +n|
@F vkkond_snr|integer|p1
@F fa_nr|smallint(3)|f|Firmennummer
@F vkkondart_cd|char(5)|f
@F artik_zuord|char(20)||Artikelzuordnung: Artikelnummer / Artikelkonditionsgruppe / nichts lt. vkkondart.artik_zuord_kz
@F kunde_zuord|char(20)||Kundenzuordnung: Kundennummer / Kundenkonditionsgruppe / nichts lt. vkkondart.kunde_zuord_kz
@F ao_snr|integer||AO-Snr / ist eindeutig / dient zum Finden eines AOs
@E
@I unique index i1_vkkond ( artik_zuord, kunde_zuord, fa_nr, vkkondart_cd )
@I index i2_vkkond (kunde_zuord, fa_nr )
@I index i3_vkkond (ao_snr)
@I index i0_vkkond(vkkond_upid)
@T vkkond_preis
@D Verkaufskonditionen: Preise / Rabatte / Im Verwaltungs- DW gibt es 2 Gruppen: / preisli_cd / preisli_cd, ab_dat / Es sind FirstOf, LastOf- Group- Felder zu verwenden.
@F vkkond_preis_upid|bigint +n|
@F vkkond_upid|bigint +n|
@F vkkond_snr|integer|p1,f
@F preisli_cd|char(5)|p2,f|Preisliste
@F ab_dat|date|p3|Datum gültig ab
@F bis_dat|date||Datum gültig bis: / Bei aktion_kz="n": / Keine Eingabe im Verwaltungsprogramm / wird entweder lt. vkkondart.bis_dat_kz oder ab_dat-1 des nächstgrößeren ab_dat's gesetzt. / Bei aktion_kz="a": / Eingabe im Verwaltungsprogramm
@F ab_mg|decimal(12,3)|p4|ab Menge
@F bis_mg|decimal(12,3)||bis Menge
@F vkpr|decimal(12,3) +n||Verkaufspreis / in Währung lt. preisli / inkl. bzw. exkl Ust lt. preisli
@F vkrab1|decimal(4,2)||Rabatt 1
@F vkrab2|decimal(4,2)||Rabatt 2
@F vkrab3|decimal(4,2)||Rabatt 3
@F vkrab4|decimal(4,2)||Rabatt 4
@F vkrab5|decimal(4,2)||Rabatt 5
@F natrab|decimal(12,3)||wird in TC indiv. ausgewertet / dazu ist im Preisfindungsobjekt ein Event vorzusehen! / Wird in der Touch Kassa verwendet / Es ist dabei die Ab-Menge als Menge inkl. Natrab zu definieren / z.B. bei 3 + 1 Gratis muss ab_mg 4 sein und natrab 1
@E
@I index i0_vkkond_preis_upid (vkkond_preis_upid)
@I index i01_vkkond_preis (vkkond_upid)
@T vkkondart
@D Verkaufskonditionsarten / Preisfindung: / select in einen Datastore / from vkkond, vkkondart, vkkond_preis / dann Preis lt. Kondition bzw. Artikelgrundpreis lt. Preisliste setzen und Nettopreis berechnen. / Der Artikelgrundpreis ist in jener Zeile, deren vkkondart aktion_kz="n" und artik_zuord_kz="n" und kunde_zuord_kz="-" hat. / dann sort nach prfind_nr, Nettopreis und alle Rabatte Desc / die erste Zeile enthält dann die richtige Kondition
@F vkkondart_cd|char(5)|p1
@F prfind_nr|smallint||Definiert die Position in der Preisfindungsreihenfolge. / Für alle Konditionen mit gleicher prfind_nr gilt das Bestpreisprinzip / Achtung: wirkt übergreifend über Aktionen und Normalkonditionen!
@F aktion_kz|char(1)||Bis Datum ist eingebbar / a=Aktion / Bis Datum ist eingebbar / n=Normalpreis / Bis Datum darf nicht eingegeben werden.
@F artik_zuord_kz|char(1)||'n'=Artikelnummer, 'g'=Artikelkonditionsgruppe, '-'=keine Einschränkung
@F kunde_zuord_kz|char(1)||'n'=Kundennummer Preisfindung, 'g'=Kundenkonditionsgruppe, '-'=keine Einschränkung
@F kassa_jn|char(1)||Konditionen dieser Art werden ins Kassensystem übernommen
@F vkpr_jn|char(1)||Verkaufspreis darf eingegeben werden
@F vkrab1_jn|char(1)||Rabatt1 darf eingegeben werden
@F vkrab2_jn|char(1)||Rabatt2 darf eingegeben werden
@F natrab_jn|char(1)||Naturalrabatt darf eingegeben werden
@F preisli_jn|char(1)||Die Preisliste des Kunden ist bei dieser Kondition eine Einschränkung / Ist bei kunde_zuord_kz = "-" fix "j"
@F aktpreis_jn|char(1)||Kondition ist im Sinne von kunde.kd_aktpreis_jn eine Aktion (z.B: Kunden/Artikelkondition soll mit Ablaufdatum geführt werden (daher Aktionskondition), soll aber auch für Kunden, die keine Aktionspreise erhalten gültig sein, daher aktpreis_jn="n")
@F datueberschn_jn|char(1)||Datum kann überschneidend sein. / Bei aktions_kz = "n" fix "n" / Bei "n" wird bei Eingabe eines neuen Verkaufspreises das Bis-Datum eines anderen Verkaufspreises, das größer als das neue Von Datum ist auf den Tag vor dem neuen VonDatum gesetzt.
@F bis_dat_kz|smallint||Kennzeichen Bis-Datum / -9 = kein Vorschlag (= Default für aktion_kz = "a") / -1 = kein Endedatum (=Default) es wird dann DatMax genommen / 0 = 31.12. lt. Jahr Ab-Datum / 1 = 31.12. lt. Folgejahr Ab-Datum /
@E
@I unique index i1_vkkondart ( aktion_kz, artik_zuord_kz, kunde_zuord_kz )
@T vlfs
@D Verkaufslieferschein (ng) / Kann nicht mehr geändert / gelöscht werden, wenn vrech_nr <> 0, dies gilt auch für die Positionen. / In nicht perversen Versionen kann vlfs & Co. überhaupt nicht mehr geändert werden! (außer vkrech_sel_jn)
@F vlfs_nr|integer(7)|p1|Vergabe mittels Tabelle nummern / Nummernkreis [nummern.nr_kreis]: / auf.vkrech_kz = 'r' 'r', sonst aufart.vlfs_nr_kreis
@F fa_nr|smallint(3)|p2,f
@F vlfs_dat|date||Lieferschein / Lieferbeleg- Datum / = :beleg_dat
@F ab_auf_nr|integer(7)|f,r|Auftragsnummer des Abwicklungsauftrages
@F kunde_cd|char(10)|r|Kunde des Abwicklungsauftrages
@F debitor_nr|integer(9)||Debitor des Abwicklungsauftrages / siehe op_debitor_nr
@F op_debitor_nr|integer(9)||OP-Debitor des Abwicklungsauftrages / wird bei der Neuanlage lt. ab_auf belegt / wird bei Änderung des Debitors im Auftrag mitgeändert, wenn der Lieferschein noch nicht fakturiert ist (vlfs.vrech_nr = 0)
@F waehrung_cd|char(4)|f|ist die Währung des Auftrages, wenn vrech_nr <= 0 / ist die Währung der Faktura, wenn vrech_nr > 0 / kann nur dann von Auftragswährung abweichen, wenn vlfs bereits Faktura hat und Auftrag auf andere Währung umgestellt wurde (dies kann nur mittels einem eigenen Programm erfolgen)
@F lag_ort|char(20)||ab_auf.aufart_cd = 'k' und fa.komm_pro_lfs_kz in ("p", "l") / Lagerort des Kommissionslagers / man findet von artik_lag_sub eindeutig den zugehörigen vlfs mit: / where lag_ort = and fa_nr = / artik_lag_sub findet man über / auf_pos.artik_cd / auf_pos.fa_nr / auf_pos.lag_cd / vlfs.lag_ort / sonst / ' '
@F vkrech_sel_jn|char(1)||'n' bei der Neuanlage / Kann als weiteres Selektionskriterium für den Rechnungsaufbau auf 'j' gesetzt werden.
@F vrech_nr|integer(7)|f|Rechnung, folgende Dummy- Rechnungen für Lieferscheine ohne zugehörige Rechnung: / 0 = noch nicht verrechnet / -1 = wird nie verrechnet / bei Auftragsart 'i': / wenn es mindestens eine vlfs_pos gibt, für die gilt: / geg_kartei_snr = 0 / 0 / sonst -1
@F komm_abl_dat|date +n||Kommissionsablaufdatum / Wird bei aufart_cd = 'k' mit ab_auf.komm_abl_dat gefüllt
@F mach_uni|varchar(10)||ab_auf.aufart_cd = 'k' und fa.komm_pro_lfs_kz in ("l", "p") ' ' / sonst vlfs_nr
@F vlfs_job_nr|integer||Nummer des Druckjobs, der den Aufbau durchgeführt hat
@F vlfs_gedruckt_jn|char(1)||Lieferschein wurde bereits gedruckt
@F anz_vklfs|smallint(2)||Anzahl Lieferscheine
@F s_einsatz_dat|date +n||Einsatz- Datum / nur bei Serviceauftrag belegt
@F s_tech_fa_pers_cd|char(5)||Techniker / nur bei Serviceauftrag nicht leer
@F s_kartei_snr|integer||0 Serviceabschluss ohne ausscheiden des Gerätes / > 0 Serviceabschluss mit ausschieden des Gerätes
@F wu_offen_jn|char(1)||Ware unterwegs ist offen / aufart_cd = "gk" und "i%" mit Umbuchung auf Ziellager "j" / sonst "n" / Fakturenaufbau selektiert nur Lieferscheine für die gilt [wu_offen_jn = "n"] / WareUnterwegsZubuchen setzt auf "n", wenn kein Satz mehr in vlfs_pos_wu vorhanden
@F vlfs_barcode|char(13)||Barcode für Dokumentenarchiv / wird bei Lieferscheinaufbau vergeben, wenn [archiv. beleg_kz = "al"] vorhanden ist und [auf.vkrech_kz <> "r"] / ist sonst ""
@F ao_snr|integer||AO-Snr / ist eindeutig / dient zum Finden eines AOs
@F vlfs_zustand_kz|char(1)||Lieferschein aktiv - KZ / im Lieferscheinfenster werden normalerweise nur aktive angezeigt / "e" wird erstellt / darf nicht fakturiert werden / "a" aktiv / "g" gelöscht / tritt durch Änderung der Lieferscheinpositionen dynamisch ein, wenn für alle Lieferscheinpositionen gilt: lief_mg = 0 (wird im Reorglauf gesetzt) / erl_vlfs_nr wird belegt / Lieferschein wird nie fakturiert
@F vlfsn_datz|date|ng|Erfassungsdatum des Datensatzes [dd.mm.yyyy hh:mm:ss] / durch DB-Default (CURRENT) belegt / Erstbelegung: [vlfs_dat] 00:00:00
@F magento_shipm_nr|integer||Status der Magento Versanddaten SST / -1 = wird nicht übertragen (kein Ausgabe lt. Versandart) oder es ist im Lieferschein keine Position mit einer magento_item_id >1 enthalten / -2 = Fehler bei der Übertragung / 0 = Übertragung offen / >0 = Jobnummer des Jobs mit dem die Übertragung stattgefunden hat
@F druck_vlfs_nr|Integer||LFS-Nummer für Andruck auf Rechnung / Default die eigene Lieferscheinnummer / Die Lieferscheinnummer des Originallieferscheins bei Stornorechnung /
@F druck_vlfs_dat|datetime||LFS-Datum für Andruck auf Rechnung / Default das eigene Lieferscheindatum / Das Lieferscheindatum des Originallieferscheins bei Stornorechnung /
@F vkrab|Decimal(4,2)||Lt. Auf
@F vkrabk2|decimal(4,2)||lt. auf
@F vkrabk3|decimal(4,2)||lt. auf
@E
@I unique index i1_vlfs ( lag_ort, fa_nr, mach_uni )
@I index i2_vlfs (kunde_cd, fa_nr, vrech_nr)
@I index i3_vlfs (debitor_nr, fa_nr, vrech_nr)
@I index i4_vlfs ( vrech_nr, fa_nr, vlfs_nr )
@I index i5_vlfs (vlfs_job_nr) / index i6_vlfs (s_kartei_snr)
@I index i7_vlfs (op_debitor_nr, fa_nr, vrech_nr)
@I index i8_vlfs (ao_snr)
@I index i9_vlfs (ab_auf_nr, fa_nr, vlfs_nr)
@I index i10_vlfs (magento_shipm_nr, fa_nr)
@T vlfs_pos
@D Verkaufslieferschein – Position (ng) / siehe unbedingt vlfs / siehe unbedingt auf_pos
@F vlfs_nr|integer(7)|p1,f|Vergabe mittels Tabelle nummern
@F fa_nr|smallint(3)|p2
@F ein_auf_nr|integer(7)|p3
@F auf_pos_nr|smallint(4)|p4,f|Auftragsposition
@F lag_cd|char(11)|f,n|Lager / wird bei Auftragsart Kundenretoure von "WareUnterwegsZubuchen" auf [auf_pos.ziel_lag_cd] gesetzt
@F lief_mg|decimal(12,3)||gelieferte Menge / wird bei der Neuanlage mit auf_pos.frei_mg belegt /  / bei Änderung muß auch kartei_lagbew entsprechend geändert werden siehe dazu vlfs_aufbau
@F off_mg|decimal(12,3)||offene Menge / wird bei der Neuanlage mit auf_pos.auf_off_mg – auf_pos.frei_mg belegt
@F off_mg_kz|char(1)||a_rueck_aufb_jn = ((auf_pos.set_pos_nrauf_pos.auf_pos_nr)artik).ar_rueck_aufb_jn / a_auslauf_jn = ((auf_pos.set_pos_nrauf_pos.auf_pos_nr)artik).auslauf_jn
@F off_mg_kz|char(1)||r|Rückstand / a_rueck_aufb_jn = 'j' and auf.rueck_aufb_jn = 'j'
@F off_mg_kz|char(1)||n|neu bestellen / a_rueck_aufb_jn = 'n' or auf.rueck_aufb_jn = 'n' / a_auslauf_jn = 'n'
@F off_mg_kz|char(1)||a|Auslaufartikel nicht mehr lieferbar / a_auslauf_jn = 'j'
@F vkpr|decimal(12,3)||Verkaufspreis / wird beim Lieferscheinaufbau aus auf_pos belegt und beim Rechnungsaufbau aus auf_pos aktualisiert / siehe vlfs.waehrung_cd
@F pos_wert_iu|decimal(11,2)|r|Positionsbetrag inkl. Ust / siehe vkpr
@F pos_wert|decimal(11,2)|r|Positionsbetrag exkl. Ust / siehr vkpr
@F ust_cd|char(10)|f|Ustcode
@F vk_skonto_jn|char(1)||Position ist skontofähig
@F duest|decimal(15,6)||Belegung bei der Neuanlage nach folgender Hierarchie: / ap_duest_fix_jn = "j" auf_pos.duest / wenn Statistik bei Geräten auf Ebene "Geräteidentpreis" geführt wird und sum(geraet.estpr) is not null sum(geraet.estpr) / auf_frei_mg / artik_lag.duest is null auf_pos.duest / ansonsten artik_lag.duest /
@F ums|decimal(11,2)||Umsatz / wird bei der Neuanlage mit 0 belegt / wird beim Rechnungsaufbau überschrieben (auf_pos.stat_vkpr * lief_mg * auf_pos.vk_stat_ftr) * (1 – vkrab1-n / 100) * (1 - auf.vkrabk1-n * auf_pos.vkrabk_ftr / 100)
@F weins|decimal(11,2)||Wareneinsatz / wird bei der Neuanlage mit 0 belegt / wird beim Rechnungsaufbau überschrieben / = lief_mg * vlfs_pos.duest * auf_pos.stat_mg_ftr * auf_pos.vk_stat_ftr
@F umsmg|decimal(11,2)||Umsatzmenge / wird bei der Neuanlage mit 0 belegt / wird beim Rechnungsaufbau überschrieben (lief_mg * auf_pos.stat_mg_ftr * auf_pos.vk_stat_ftr)
@F verbmg|decimal(11,2)||Verbrauchsmenge / wird bei der Anlage mit lief_mg * auf_pos.verb_mg_ftr belegt / wird bei der Mindestbestandsberechnung als Verbrauch verwendet
@F kartei_snr|integer|n|0 keine Lagerbewegung / > 0 Verweis auf die zugehörigen Lagerbewegungen (eine oder mehrere Rows in kartei_lagbew)
@F geg_kartei_snr|integer|n|-1 keine Gegenlagerbewegung / 0 noch keine Gegenlagerbewegung / bei Auftragsart "gk" / bei Auftragsart 'i%' und auf_pos.geg_lag_cd <> auf_pos.ziel_lag_cd / ist der Fall, wenn vlfs- Gegenlager- Buchung noch nicht erfolgt ist / > 0 Verweis auf die zugehörigen Gegenlagerbewegungen (eine oder mehrere Rows in kartei_lagbew) /
@F artik_cd|char(20)|r|Artikel lt. auf_pos
@F kunde_cd|char(10)|r|Kunde lt. auf
@F vlfs_mon|char(6)|r|Monat lt. vlfs_dat
@F vrech_mon|char(6)|r|wird bei der Neuanlage mit blank belegt / wird beim Rechnungsaufbau lt. vrech.vrech_dat belegt
@F vlfs_dat|date|r|Liefersscheindatum lt. vlfs
@F stat_gebucht_jn|char(1)||Rechnungsstatistikdaten sind gebucht / wird vom "Statistikverbuchen" gesetzt
@F verb_gebucht_jn|char(1)||Verbrauchsmenge verbucht / wird vom "Statistikverbuchen" gesetzt
@F erf_gu_jn|char(1)|g|Position wurde bereits gutgeschrieben / Default Neuanlage ist "n" / wird beim automatischen Aufbau einer Auftragsposition zum Gutschreiben auf "j" gesetzt
@F komm_lag_ort|char(20)||Blank, wenn / keine Kommissionsbelieferung / fa.komm_pro_lfs_kz <> "p" / "lfs"+vlfs.vlfs_nr+"-"+auf_pos_nr, sonst
@F elfs_nr|integer +n||Eingangslieferscheinnummer / Ist nur belegt, wenn zur Verkaufslieferscheinposition eine Eingangslieferscheinposition aufgebaut wurde (z.B. Lieferantenrtouere) / Ist notwendig um beim Lieferbelegdruck die Chargen/Geräte Informationen auch bei Lieferantenretouren andrucken zu können.
@F elfs_pos_nr|smallint +n||Eingangslieferscheinpositionsnummer / w.o.
@F vkrab1|Decimal(4,2)||aus auf_pos
@F vkrab2|Decimal(4,2)||aus auf_pos
@F vkrab3|Decimal(4,2)||aus auf_pos
@F vkrab4|Decimal(4,2)||aus auf_pos
@F vkrab5|Decimal(4,2)||aus auf_pos
@F vkpr_pro_mg|Decimal(4,0)||aus auf_pos
@F vkpr_keh_veh_kz|Char(1)||aus auf_pos
@F veh_cd|Char(5)|f|Aus auf_pos
@F vkpr_ftr|decimal(13,7)||aus auf_pos
@N /
@E
@I index i1_vlfs_pos (artik_cd, vrech_mon)
@I index i2_vlfs_pos (kunde_cd, vrech_mon)
@I index i3_vlfs_pos (vrech_mon)
@I index i4_vlfs_pos (artik_cd, vlfs_dat)
@I index i5_vlfs_pos (kartei_snr)
@I index i6_vlfs_pos (kunde_cd, vlfs_dat)
@I index i7_vlfs_pos (ein_auf_nr, fa_nr, auf_pos_nr)
@I index i8_vlfs_pos (geg_kartei_snr)
@T vlfs_pos_gerstat
@D Verkaufslieferschein – Einstandspreis Geräte / TC-Param ib_GerStat_mit_estpr = TRUE / artik.lagfuehr_kz = "g" / auf_pos.auf_lag_ftr <> 0
@F vlfs_nr|integer(7)|p1
@F fa_nr|smallint(3)|p2
@F ein_auf_nr|integer(7)|p3
@F auf_pos_nr|smallint(4)|p4,f|Lieferscheinposition
@F artik_cd|char(20)|r
@F geraet_cd|char(40)|p5,f|Gerätenummer
@F estpr|decimal(12,3)||siehe vlfs_pos.duest
@E
@T vlfs_pos_statkorr
@D Verkaufslieferschein – Position Korrektur Statistik (ng) / wird beim Verbuchen der Eingangsrechnung aufgebaut, wenn Auftragsbezug vorhanden und Statistik des Verkaufslieferscheins bereits gebucht wurde. / wird bei der Lieferscheinkorrektur aufgebaut, wenn die Statistik (bei Statistik mit Lieferschein buchen) bereits gebucht ist / wird beim Statistikaufbau wieder gelöscht.
@F vlfs_nr|integer(7)|p1
@F fa_nr|smallint(3)|p2
@F ein_auf_nr|integer(7)|p3
@F auf_pos_nr|smallint(4)|p4,f|Auftragsposition
@F ums|decimal(11,2)||Umsatz / wird bei der Neuanlage mit dem ursprünglichem Wert lt. vlfs_pos belegt / wird beim Statistikaufbau von Statistikwerten subtrahiert
@F weins|decimal(11,2)||Wareneinsatz / siehe ums
@F umsmg|decimal(11,2)||Umsatzmenge / siehe ums
@E
@T vlfs_pos_wu
@D Verkaufslieferschein – Position Ware unterwegs / Wird bei Auftragsart 'i%' aufgebaut, wenn die Gegenlagerbuchung auf ein Lager Ware unterwegs durchgeführt wird / wird bei Auftragsart "gk" aufgebaut / Wird bei der Gegenlagerbuchung gelöscht
@F vlfs_nr|integer(7)|p1|Verkaufslieferscheinnummer
@F fa_nr|smallint(3)|p2|Firmennummer
@F ein_auf_nr|integer(7)|p3|Auftragsnummer
@F auf_pos_nr|smallint(4) (f vlfs_pos)|p4|Auftragspositionsnummer
@F charge_geraet /|char(40)|p5|Leer, Gerätenummer oder Chargennummer siehe artik_lag_sub / aufart_cd = 'vr' leer / sonst bei Geräten und Chargen- Artikeln nicht leer
@F geg_lag_ort|char(20)|p6|Gegenlagerort (Lagerort, auf welchen umgebucht wird)
@F lief_mg|decimal(12,3)|n|gelieferte Menge
@F ablauf_dat|date +n||Ablaufdatum
@F einlag_dat|date +n||Einlagerungsdatum
@E
@T vlfs_prod
@D Verkaufslieferschein- Produktionsdaten (ng) / kann weder geändert noch gelöscht werden
@F vlfs_nr|integer(7)|p1,f
@F fa_nr|smallint(3)|p2
@F lief_mg|decimal(12,3)||gelieferte Menge (=produzierte Menge)
@F lag_cd|char(11)|f|Lager
@F duest|decimal(15,6)||Belegung bei der Neuanlage: / summe ( vlfs_pos.duest * auf_pos.teil_mg )
@F kartei_snr|integer||Verweis auf die zugehörigen Lagerbewegungen (eine oder mehrere Rows in kartei_lagbew)
@E
@I index i1_vlfs_prod (kartei_snr)
@T vrech
@D Verkaufsrechnung (ng) / Es muß folgende "unsichtbare" Rechnungen geben: / vrech_nr = 0: dieser sind alle vlfs, welche noch nicht verrechnet sind, zugeordnet. / vrech_nr = -1: dieser sind alle vlfs, welche nie verrechnet werden werden, zugeordnet. /  / Siehe auch auf.hat_rech_jn, auf_pos.hat_rech_jn: beide müssen gegebenenfalls beim Rechnungsaufbau belegt werden.
@F vrech_nr|integer(7)|p1|Rechnungsnummer / Vergabe mittels Tabelle nummern / nr_kreis lt. aufart.vrech_nr_kreis / es werden nur Aufträge mit gleichem aufart.vrech_nr_kreis zu einer Rechnung zusammengefaßt
@F fa_nr|smallint(3)|p2|Columns sind beim Rechnungsaufbau Gruppierfelder und kommen aus vlfs.ab_auf_nrauf.* /
@F debitor_nr|integer(9)|f|Columns sind beim Rechnungsaufbau Gruppierfelder und kommen aus vlfs.ab_auf_nrauf.* /
@F op_debitor_nr|integer(9)|f|Columns sind beim Rechnungsaufbau Gruppierfelder und kommen aus vlfs.ab_auf_nrauf.* /
@F vkrech_kz|char(2)||Columns sind beim Rechnungsaufbau Gruppierfelder und kommen aus vlfs.ab_auf_nrauf.* /
@F zahlart_cd|char(5)||Columns sind beim Rechnungsaufbau Gruppierfelder und kommen aus vlfs.ab_auf_nrauf.* /
@F anz_vkrech|smallint(2)||Columns sind beim Rechnungsaufbau Gruppierfelder und kommen aus vlfs.ab_auf_nrauf.* /
@F waehrung_cd|char(4)||Columns sind beim Rechnungsaufbau Gruppierfelder und kommen aus vlfs.ab_auf_nrauf.* /
@F iu_jn|char(1)||Columns sind beim Rechnungsaufbau Gruppierfelder und kommen aus vlfs.ab_auf_nrauf.* /
@F skonto1_prz|decimal(4,2)||Columns sind beim Rechnungsaufbau Gruppierfelder und kommen aus vlfs.ab_auf_nrauf.* /
@F skonto1_tg|smallint(3)||Columns sind beim Rechnungsaufbau Gruppierfelder und kommen aus vlfs.ab_auf_nrauf.* /
@F skonto2_prz|decimal(4,2)||Columns sind beim Rechnungsaufbau Gruppierfelder und kommen aus vlfs.ab_auf_nrauf.* /
@F skonto2_tg|smallint(3)||Columns sind beim Rechnungsaufbau Gruppierfelder und kommen aus vlfs.ab_auf_nrauf.* /
@F netto_tg|smallint(3)||Columns sind beim Rechnungsaufbau Gruppierfelder und kommen aus vlfs.ab_auf_nrauf.* /
@F valuta_dat|date +n||Columns sind beim Rechnungsaufbau Gruppierfelder und kommen aus vlfs.ab_auf_nrauf.* /
@F zollta_dru_jn|char(1)||Columns sind beim Rechnungsaufbau Gruppierfelder und kommen aus vlfs.ab_auf_nrauf.* /
@F debitor_name1|char(50)||Rechnungsadresse + Ust- ID / Columns werden abhängig von kunde.divers_jn von / 'j' ab_auf / 'n' pfu_debitor / kopiert. / Bei kunde.divers_jn = 'j' kann eine Rechnung nur einen Auftrag und demnach auch nur einen Kunden haben. / Adresse wird bei kunde.divers_jn = 'j' in die Buchhaltung übergeleitet.
@F debitor_name2|char(50)||Rechnungsadresse + Ust- ID / Columns werden abhängig von kunde.divers_jn von / 'j' ab_auf / 'n' pfu_debitor / kopiert. / Bei kunde.divers_jn = 'j' kann eine Rechnung nur einen Auftrag und demnach auch nur einen Kunden haben. / Adresse wird bei kunde.divers_jn = 'j' in die Buchhaltung übergeleitet.
@F debitor_name3|char(50)||Rechnungsadresse + Ust- ID / Columns werden abhängig von kunde.divers_jn von / 'j' ab_auf / 'n' pfu_debitor / kopiert. / Bei kunde.divers_jn = 'j' kann eine Rechnung nur einen Auftrag und demnach auch nur einen Kunden haben. / Adresse wird bei kunde.divers_jn = 'j' in die Buchhaltung übergeleitet.
@F debitor_name4|char(50)||Rechnungsadresse + Ust- ID / Columns werden abhängig von kunde.divers_jn von / 'j' ab_auf / 'n' pfu_debitor / kopiert. / Bei kunde.divers_jn = 'j' kann eine Rechnung nur einen Auftrag und demnach auch nur einen Kunden haben. / Adresse wird bei kunde.divers_jn = 'j' in die Buchhaltung übergeleitet.
@F debitor_strasse|char(50)||Rechnungsadresse + Ust- ID / Columns werden abhängig von kunde.divers_jn von / 'j' ab_auf / 'n' pfu_debitor / kopiert. / Bei kunde.divers_jn = 'j' kann eine Rechnung nur einen Auftrag und demnach auch nur einen Kunden haben. / Adresse wird bei kunde.divers_jn = 'j' in die Buchhaltung übergeleitet.
@F debitor_land_cd|char(3)|f|Rechnungsadresse + Ust- ID / Columns werden abhängig von kunde.divers_jn von / 'j' ab_auf / 'n' pfu_debitor / kopiert. / Bei kunde.divers_jn = 'j' kann eine Rechnung nur einen Auftrag und demnach auch nur einen Kunden haben. / Adresse wird bei kunde.divers_jn = 'j' in die Buchhaltung übergeleitet.
@F debitor_plz|char(10)||Rechnungsadresse + Ust- ID / Columns werden abhängig von kunde.divers_jn von / 'j' ab_auf / 'n' pfu_debitor / kopiert. / Bei kunde.divers_jn = 'j' kann eine Rechnung nur einen Auftrag und demnach auch nur einen Kunden haben. / Adresse wird bei kunde.divers_jn = 'j' in die Buchhaltung übergeleitet.
@F debitor_ort|char(50)||Rechnungsadresse + Ust- ID / Columns werden abhängig von kunde.divers_jn von / 'j' ab_auf / 'n' pfu_debitor / kopiert. / Bei kunde.divers_jn = 'j' kann eine Rechnung nur einen Auftrag und demnach auch nur einen Kunden haben. / Adresse wird bei kunde.divers_jn = 'j' in die Buchhaltung übergeleitet.
@F ustid|char(14)||Rechnungsadresse + Ust- ID / Columns werden abhängig von kunde.divers_jn von / 'j' ab_auf / 'n' pfu_debitor / kopiert. / Bei kunde.divers_jn = 'j' kann eine Rechnung nur einen Auftrag und demnach auch nur einen Kunden haben. / Adresse wird bei kunde.divers_jn = 'j' in die Buchhaltung übergeleitet.
@F vrech_dat|date||Rechnungsdatum / wird beim Rechnungsaufbau vom Anwender vorgegeben
@F vrech_mon|char(6)|r|Monat lt. vrech_dat
@F inl_eu_drittl_kz|char(1)||lt. kundeerl
@F sprache_cd|char(5)||Sprachcode lt. Kunde des ersten Lieferscheins
@F vrech_vlfs_we|decimal(11,2)|r|entspricht dem errechneten Netto -Wert aller Verkaufslieferscheinpositionen / dient für Abfrage
@F vrech_bt_we|decimal(11,2)|r|Brutto Gesamtwert der Rechnung
@F vrech_bt_we_sktof|decimal(11,2)|r|Brutto Gesamtwert der Rechnung skontofähig
@F vrech_job_nr|integer||Nummer des Druckjobs, der den Aufbau durchgeführt hat
@F vrech_gedruckt_jn|char(1)||Rechnung wurde bereits gedruckt
@F vrechk_gedruckt_jn|char(1)||Rechnungskopien wurden bereits gedruckt
@F vrech_kz|char(1)||'r' Rechnung / 'g' Gutschrift (vrech_bt_we < 0) / 'b' Barverkauf
@F bez_vrech_nr|integer(7)|f|OP-Nummer in FIBU / ist normalerweise vrech_nr / ist bei Storno mit OP-Bezug ursprüngliche Rechnungsnummer
@F vfbueb_job_nr|integer||Jobnummer des Fibuüberleitungsprogrammes / ist bei Neuanlage fix 0 wenn in Fibu übergeleitet wird bzw. -1 wenn nie in die Fibu übergeleitet wird / ist bei sofortiger integrierter Jetfibuverbuchung 1
@F vrechausart_cd|char(10)||Ausgangsrechnung Ausgabeart / Belegung lt. auf.vrechausart_cd / mit "d", wenn gilt / [vrech.vkrech_kz] = "r" und [aufart.vrech_liefbeleg_jn] = "j" / auf.vrechausart.vrech_druck_kz = "e" und debitor.e_vrech_komid_wert = ""
@F vrech_dfrei_jn|char(1)||Druckfreigabe für Originalrechnung / wird beim Rechnungsaufbau gesetzt / Wird verwendet um E-Mail Rechnungen vor dem Versenden kontrollieren zu Können. / Belegung mit "j", wenn gilt / [vrechausart.vrech_druck_kz] = "d" oder [fa.sofort_e_vrech_jn] = "j" / Sonst Belegung mit "n",
@F email_adr|varchar(255)||E-Mail-Adresse, an die versandt wird / wird beim Rechnungsaufbau gesetzt / wenn auf.e_vrech_fix_jn = "j" dann auf.e_vrech_komid_wert / sonst debitor.e_vrech_komid_wert
@F ao_snr|integer||AO-Snr / ist eindeutig / dient zum Finden eines AOs
@F eb_job_snr|decimal(14,0)||Rechnung an den Bund ausgegeben / Jobnummer des Ausgabeprogramms / wird mit 0 bzw. -1 aufgebaut / 0 = noch nicht ausgegeben / -1 = wird nie ausgegeben [left(vrechausart.sst_kz, 2) <> "eb"]
@F vrech_barcode|char(13)||Barcode für Dokumentenarchiv / wird beim Rechnungsdruck vergeben, wenn [archiv. beleg_kz = "vr"] vorhanden ist / ist sonst fix ""
@F vrechn_datz|date|ng|Erfassungsdatum des Datensatzes [dd.mm.yyyy hh:mm:ss] / durch DB-Default (CURRENT) belegt / Erstbelegung: [vrech_dat] 00:00:00
@F zahlungsref|varchar(100) +n||Zahlungsreferenznummer / Ist nur belegt, wenn der Rechnung genau ein Auftrag zugeordnet ist.
@F storno_vrech_nr|integer||Storno Rechnungsnummer, wird vom Stornoaufbau vergeben / 0 = Kein Storno / Originale Rechnungsnummer bei Stornorechnung / Storno Rechnungsnummer bei Originalrechnung
@F vrech_upid|bigint +n|
@E
@I index i1_vrech_upid (vrech_upid)
@I index i1_vrech (vrech_dat)
@I index i2_vrech (vrech_job_nr)
@I index i3_vrech (debitor_name1)
@I index i4_vrech (ao_snr)
@T vrech_kont
@D Verkaufsrechnung - Kontierungszeilen / wird durch Zuordnungen in Tabelle erl + kst beim Rechnungsaufbau automatisch erzeugt / muss wertmässig vrech_ust entsprechen
@F vrech_nr|integer(7)|p1,f
@F fa_nr|smallint(3)|p2
@F ust_cd|char(10)|p3,f|Ustcode
@F kto_nr|integer(9)|p4|Erlöskontennummer
@F kst_nr|integer(9)|p5|Kostenstellennummer
@F koart_nr|integer(9)|p6|Kostenartnummer
@F ktr_nr|integer(9)|p7|Kostenträgernummer
@F ust_prz|decimal(4,2)||Ust- Prozentsatz
@F ust_basis|decimal(11,2)||Ust- Basis
@F ust_betr|decimal(11,2)||Ust- Betrag
@F buch_txt|char(25)||Buchungstext für Fibu
@F ust_basis_sktofae|decimal(11,2)||Ust- Basis skontofähig / wird für BMD FIBU Überleitung benötigt
@F ust_betr_sktofae|decimal(11,2)||Ust- Betrag skontofähig
@E
@T vrech_ust
@D Verkaufsrechnung- Ustzeilen
@F vrech_nr|integer(7)|p1,f
@F fa_nr|smallint(3)|p2
@F ust_cd|char(10)|p3,f|Ustcode
@F ust_prz|decimal(4,2)||USt- Prozentsatz
@F ust_basis|decimal(11,2)||USt- Basis
@F ust_betr|decimal(11,2)||Ust- Betrag
@F ust_basis_sktofae|decimal(11,2)||Ust- Basis skontofähig
@F ust_betr_sktofae|decimal(11,2)||Ust- Betrag skontofähig
@E
@T vrechausart
@D Verkaufsrechnung- Ausgabeart
@F vrecvhausart_upid|bigint +n|
@F vrechausart_cd|char(10)|p1|Ausgabeart
@F fa_nr|smallint|p2|Firma
@F vrechausart_mc|char(20)||Ausgabeart-Matchcode
@F vrech_druck_kz|char(2)||DruckKennzeichen / "e" E-Mail / "d" Druck / "b" kein Ausdruck
@F va_bbg_partner_fcd|varchar(30)||eigene BBG-Partnernummer / nur bei BBG-Ausgabe relevant
@F sst_ kz|char(10)||Schnittstellen-Kennzeichen EB-Interface / "eb4.0" – EB-Interface 4.0 / "eb4.1" – EB-Interface 4.1 / "-" – keine / "eb" am Anfang steht für EB-Interface und löst damit auch die ensprechenden Prüfungen aus
@F sst_versand_kz|char(1)||Versandart der SST / fix "-" wenn sst_kz = "-" / "w" – Webservice / "e" – E-Mail / "s" - SFTP
@F vrech_pdf_jn|char(1)||Rechnungs-PDF mitsenden / ist fix "n", wenn sst_versand_kz not in ("e", "s")
@F vrech_druckart_cd|char(8)||Druckart der Ausgangsrechnung, die versendet werden soll / fix "", wenn vrech_pdf_jn = "n"
@F sftp_hostname|vchar(100)||Hostname für SFTP / fix "", wenn sst_versand_kz <> "s"
@F sftp_username|vchar(100)||User
@F sftp_passwort|vchar(100)||Passwort
@F sftp_pfad|vchar(255)||Pfad
@F sst_url|varchar(255)||URL für sst_versand_kz = ‚w‘ / Bei Bund muss es zur Zeit nicht gesetzt werden, da in der InterOp der Bund-Endpunkt der Defaultwert ist!
@F sst_usr|varchar(30)||User für sst_versand_kz = ‚w‘
@F sst_pwd|varchar(30)||Passwort für sst_versand_kz = ‚w‘
@F sst_mail_adr|varchar(255)||Mailadresse des Empfängers, wenn sst_versand_kz = ‚e‘ (zB. BBG)
@F rm_mail_adr|varchar(255)||Mailadresse für eventuelle Rückmeldung
@E
@S vs Versandtabellen
@T vs_adresse
@D Kundenstammdaten / ist bei Anbindung an TradeControl ein View
@F adr_kz|char(1)||Adresskennzeichen / 'k' = Kunde / 'l' = Lieferant / 's' = sonstige Adresse
@F kd_lief_cd|char(10)|p1|Kundennummer aus der Warenwirtschaft / kunde.kunde_cd / lief.lief_cd / ' '
@F fa_nr|smallint|p2|Firmennummer aus Warenwirtschaft / kunde.fa_nr / lief.fa_nr / fa.fa_nr
@F adr_mc|char(30)||Matchcode / adr.adr_mc
@F name1|char(50)||Anschrift / adr.name1
@F name2|char(50)||adr.name2
@F name3|char(50)||adr.name3
@F name4|char(50)||adr.name4
@F strasse|char(50)||adr.strasse
@F land_cd|char(3)||adr.land_cd
@F plz|char(10)||adr.plz
@F ort|char(50)||adr.ort
@F telefon|varchar(255)||adr_pers.telefon
@F fax|varchar(255)||adr_pers.fax
@F email|varchar(255)||adr_pers.email
@F internet|varchar(255)||adr_pers.internet
@F ustid|char(14)||pfufb_debitor.ustid / pfufb_kreditor.ustid / ' '
@F bex_lc_plz|char(4)||adr_vs.bex_lc_plz
@F bex_lc_mc|char(20)||bex_lc_mc
@F bex_kunde_nr|char(8)||bex_kunde_nr
@F bex_serviceart_kz|char(2)||bex_serviceart_kz
@F bex_unfrank_exw_jn|char(1)||bex_unfrank_exw_jn
@E
@T vs_auf
@D Versand-Auftrag
@F vs_auf_snr|integer(8)|p1|Interne Versandauftragsnummer
@F fa_nr|smallint(3)||Firma
@F vs_adr_kz|char(1)||Adresskennzeichen / 'k' = Kunde / 'l' = Lieferant / 's' = sonstige Adresse
@F kd_lief_cd|char(10)||abhängig von Adresskennzeichen / adr_kz = 'k' Kundennummer / adr_kz = 'l' Lieferantennummer / adr_kz = 's' leer
@F adr_mc|char(30)||Matchcode zu Adresse
@F name1|char(50)||Firmenanschrift
@F name2|char(50)|
@F name3|char(50)|
@F name4|char(50)|
@F strasse|char(50)|
@F land_cd|char(3)|
@F plz|char(10)|
@F ort|char(50)|
@F ustid|char(14)||UID-Nummer
@F telefon|varchar(255)||Telefonnummer
@F versand_dat|date||Versanddatum / Vorschlag Tagesdatum
@F versart_cd|char(10)|f|Versandart
@F nn_betrag|decimal(11,2)||Nachnahme-Betrag
@F gewicht_bto|decimal(8,3)||Bruttogewicht der Sendung in kg
@F gewicht_nto|decimal(8,3)||Nettogewicht der Sendung in kg
@F gedruckt_jn|char(1)||Versandpapiere gedruckt
@F sendungsnummer|varchar(20) +n||Vergabe bzw. Eingabe lt. Tabelle Nummern / Nummernkreis lt. vs_versart.nr_kreis
@F versort_nr|smallint(3)||Versandortnummer
@F vs_gebuehr|decimal(7,2)||Versandgebühr
@F kontpers|char(50)||Kontaktperson
@F vs_beleg_kz|char(1) +n||L = Lieferschein / R = Rechnung
@F beleg_nr|integer +n||Belegnummer lt. vs_beleg_kz
@F email|varchar(255)||E-Mail Adresse
@F spedliste_nr|decimal(14,0)||Speditionslistennummer / 0 = Speditionsliste noch nicht gedruckt
@F liefbed_cd|char(5) +n||Lieferbedingung / Bei IFTMIN EDI Versandarten dürfen nur Lieferbedingungen mit belegten incoterm_kz verwendet werden.
@F export_job_snr|bigint||Job-Nummer des Export Jobs / -1 = Wird nicht Exportiert / keine Versandart mit IFTMIN SST / 0 = Export noch offen / >0 = Jobnummer des IFTMIN File Exports
@E
@I Index i1_vs_auf (export_job_snr)
@I index i2_vs_auf (spedliste_nr, fa_nr, versart_cd, versort_nr)
@T vs_auf_abh
@D Versand-Auftrag-Abholung
@F vs_auf_snr|integer(8)|p1,f|Interne Versandauftragsnummer
@F abgeholt_jn|char(1)||Sendung abgeholt ja/nein
@F abhol_dat|date +n||Datum der Abholung / fix NULL bei [abgeholt_jn] =n / kenn eigegeben werden bei [abeholt_jn] =j, Vorschlag = Systemdatum
@F anz_etik|smallint(4)||Anzahl Etiketten
@E
@T vs_auf_abh_sub
@D Versand-Auftrag-Abholung
@F vs_auf_snr|integer(8)|p1,f|Interne Versandauftragsnummer
@F zeile_nr|smallint|p2|lfd. Zeilennummer
@F anz_vpe|smallint(3)||Anzahl Verpackungseinheiten
@F paket_gewicht_bto|decimal(8,3)||Paketgewicht brutto
@E
@T vs_auf_beleg
@D Versand-Auftrag / pro Auftrag muß es mindestens 1 Satz geben
@F vs_auf_snr|integer(8)|p1,f|Interne Versandauftragsnummer
@F fa_nr|smallint(3)|p2,f|Firma
@F vs_beleg_kz|char(1)|p3|Belegkennzeichen / 'L' = Lieferschein (Verkauf) / 'R' = Rechnung (Verkauf) / 'W' = Warenretoure / 'M' = manuell erfasster Beleg
@F beleg_nr|integer(9)|p4|Belegnummer / abhängig von beleg_kz Lieferscheinnummer/Rechnungsnummer/Retourlieferscheinnummer/bzw. Vergabe lt. Tabelle nummern
@F beleg_dat|date +n||Belegdatum
@E
@T vs_auf_bex
@D Versand-Auftrag
@F vs_auf_snr|integer(8)|p1,f|Interne Versandauftragsnummer
@F bex_serviceart_kz|char(2)||Bahnexpress-Serviceart / 'be' = BahnExpress / 're' = RailExpress / 'rs' = RailStandard
@F bex_unfrank_exw_jn|char(1)||Unfrankiert EXW / 'j' = Empfänger trägt die Frachtspesen / 'n' = Absender trägt die Frachtspesen / ist fix 'n', wenn bex_serviceart_kz = 're' / es darf entweder bex_unfrank_exw_jn oder franko_ddu_jn = 'j' sein
@F rid_jn|char(1)||Gefahrengut j/n
@F bex_franko_ddu_jn|char(1)||Franko DDU j/n / es darf entweder bex_unfrank_exw_jn oder franko_ddu_jn = 'j' sein
@F bex_sonstige_1|char(20)||Sonstige Vermerke 1
@F bex_sonstige_2|char(20)||Sonstige Vermerke 2
@F bex_sonstige_3|char(20)||Sonstige Vermerke 3
@F bex_laenge|decimal(4,2)||Länge
@F bex_breite|decimal(4,2)||Breite
@F bex_hoehe|decimal(4,2)||Höhe
@E
@T vs_auf_dpd
@D Versand-Auftrag-DPD
@F vs_auf_snr|integer(8)|p1,f|Interne Versandauftragsnummer
@F dpd_kp_jn|char(1)||Kleinpaket ja/nein / bei vs_versart.nachnahme_jn = j fix ‚n’
@F dpd_lst_nr|integer(10)||DPD-Listennummer / 0 = DPD-Liste nicht endgültig gedruckt
@F o_sort|char(4)||Ursprungssortierung
@F d_depot|char(4)||Zieldepot
@F group_prior|char(1)||Gruppierungspriorität
@F d_sort|char(4)||Zielsortierung
@F barcode_id|smallint(3)||Barcode-ID (ASCII-Code des Startzeichens z.B 37 = %)
@F iata_cd|char(3) +n||IATA ähnlicher Code
@F service_txt|char(16)||Servicetext
@F service_mark_kz|char(1)||Markierung
@F service_info_txt|char(100)||Infotext
@F iso_num|smallint(3)||ISO numerisch
@F version|char(8)||Versionsdatum / aus Tabelle [vs_dpd_kennsatz] where [vs_dpd_kennsatz.filename] = ‚routes’
@F service_cd|smallint(3)||Sericecode / 101 ... DPD / 136 ... DPD – Kleinpaket / wenn dpd_kp_jn = j: [vs_versart.dpd_service_kp_cd] / sonst [vs_versart.dpd_service_cd]
@E
@T vs_auf_edi
@D Versand-Auftrag EDI Daten / Wird bisher nur für Dachser verwendet
@F vs_auf_snr|integer(8)|p1,f|Interne Versandauftragsnummer
@F fremd_kunde_nr|char(10)|
@F anz_vpe|smallint|
@F anz_pal|smallint|
@F gewicht_bto|decimal(8,3)|
@F eti_v|char(20)|
@F eti_b|char(20)|
@F erledigt_jn|char(1)|
@F bordero_nr|char(50)|
@F anz_pal_ew|smallint|
@E
@T vs_auf_paket
@D Versand-Auftrag Paketdaten
@F vs_auf_snr|integer(8)|p1,f|Interne Versandauftragsnummer
@F paket_referenz_snr|integer(9)|p2|laufende Paketnummer
@F paket_gewicht_bto|decimal(8,3)||Bruttogewicht in kg
@F paket_sendung_nr|varchar(40)||Paket Sendungsnummer (Barcode am Paket)
@F verpart_cd|char(10)|f|Verpackungsartencode / Bei Umstellung wird vs_verpart "pkt' angelegt und als Defaultwert (DB + TC) verwendet.
@E
@T vs_auf_sped
@D Versand-Auftrag-Spedition
@F vs_auf_snr|integer(8)|p1,f|Interne Versandauftragsnummer
@F fracht_kz|char(1)||n = Normalfracht / t = Terminfracht
@F sped_frei_jn|char(1)||Versand frei/unfrei
@F abhol_dat|date +n||Datum der Abholung durch Spedition
@F anz_etik|smallint(4)||Anzahl Etiketten
@E
@T vs_auf_sped_sub
@D Versand-Auftrag-Spedition
@F vs_auf_snr|integer(8)|p1,f|Interne Versandauftragsnummer
@F zeile_nr|smallint|p2|lfd. Zeilennummer
@F signo|char(14)||Signo
@F anz_vpe|smallint(3)||Anzahl Verpackungseinheiten
@F verpart_cd|char(10)|f|Verpackungsart (DDDW)
@F anz_pal|smallint(4)||Anzahl Paletten
@F anz_pal_ew|smallint(4)||davon Anzahl Einwegpaletten / muss <= anz_pal sein
@E
@T vs_auf_verpart
@D Versand-Auftrag-Verpackungsarten
@F vs_auf_snr|integer(8)|p1,f|Interne Versandauftragsnummer
@F verpart_cd|char(10)|p2,f|Verpackungsart
@F inhalt_cd|char(10)|p3,f|Inhalt
@F anz_verp|smallint||Anzahl der Verpackungen
@E
@T vs_beleg
@D ist ein View auf die bestehende WWS-Datenbank bzw. Schnittstellendatei
@F fa_nr|smallint|
@F vs_beleg_kz|char(1)||Belegkennzeichen / 'L' = Lieferschein (Verkauf) / 'R' = Rechnung (Verkauf) / 'W' = Warenretoure (Retourwarenschein aus Einkauf)
@F beleg_nr|integer(7)||Belegnummer / abhängig von beleg_kz Lieferscheinnummer/Rechnungsnummer/Retourlieferscheinnummer
@F beleg_dat|date||Belegdatum
@F vs_adr_kz|char(1)||k = Kunde / l = Lieferant
@F kd_lief_cd|char(10)||Kunden- / Lieferantencode
@F adr_mc|char(30)||Matchcode zu Adresse
@F name1|char(50)||Empfängeranschrift
@F name2|char(50)|
@F name3|char(50)|
@F name4|char(50)|
@F strasse|char(50)|
@F land_cd|char(3)|
@F plz|char(10)|
@F ort|char(50)|
@F ustid|char(14)||UID-Nummer
@F telefon|varchar(255)||Telefonnummer
@F gewicht_nto|decimal(8,3)||Nettogewicht der Sendung in kg
@F lieferwert_iu|decimal(11,2)||Lieferwert inkl. Ust
@F versart_cd|char(10)|
@F email|varchar(255)||E-Mail Adresse
@F kontpers|varchar(255)||Kontaktperson
@F liefbed_cd|char(10)||Lieferbedingungscode
@F sendungsnummer|varchar(20)||Sendungsnummer, wenn diese vorgegeben werden kann / z.B. Ladenummer bei KUWOPA/Geb. Weiss
@E
@T vs_dpd_allow
@D DPD-Prüfungstabelle, ob für die Routenberechnung die Eingabeparameter korrekt / kein Verwaltungprogramm / wird über „Import DPD-Routen-DB“ verwaltet
@F iso_kurz|char(2) p1||Landkennzeichen (ISO Code 2 stellig) / für Import: / NULL „ „ / ist der Ländercode = „ „ gilt die Eintragung für alle Ländercodes
@F von_plz|char(9) p2||von Postleitzahl / für Import: / NULL „ „
@F bis_plz|char(9) p3||bis Postleitzahl / für Import: / wenn NULL: / wenn [von_plz] = NULL od. „ „: [bis_plz] = zzzzzzzzz / sonst: [bis_plz] = [von_plz]
@F von_service_cd|smallint(3) p4||von Servicecode / für Import / in der Import-Datei werden alle möglichen Services in einem Datensatz übergeben / diese können im Format Saaa und/oder Sbbbccc sein / Mehrfacheintragungen sind durch Komma getrennt / z.B: / Saaa: aaa wird in [von_service_cd] und [bis_service_cd] gestellt / Sbbbccc: bbb = [von_service_cd], ccc = [bis_service_cd] / Saaa, Sbbbccc: 1 Datensatz mit aaa = [von_service_cd] und [bis_service_cd] + 1 Datensatz mit [von_service_cd] und ccc = [bis_service_cd] / kann aber auch Saaa, Sbbbccc, Sddd usw. sein
@F bis_service_cd|smallint(3) p5||bis Servicecode / siehe auch [von_service_cd]
@F routen_kz|char(1) p6||Routen-Kz: / [von_routen_wert] und [bis_routen_wert] sind bei: / D ... Depotnummern (4 stellig) / C ... Ländercodes (2 stellig) / G ... Depotgruppen (4 stellig) / für Import: / das Feld „Routungort“ ist vom Datentyp „text“ in dem alle möglichen Werte in einem Datensatz übergeben werden / dieses Feld kann folgende Formate haben / Daaaa: aaaa = [von_routen_wert] u. [bis_routen_wert] / Dbbbbcccc: bbbb = [von_routen_wert], cccc = [bis_routen_wert] / Caa: aa = [von_routen_wert] u. [bis_routen_wert] / Gaaaa: aaaa = [von_routen_wert] u. [bis_routen_wert] / wobei Kombinationen von diesen Formaten vorkommen können / in solchen Fällen, muss für jede dieser Kombinationen ein Datensatz ausgegeben werden
@F von_routen_wert|char(4) p7||von Depot-, Länder- oder Depotgruppen-Code (Routungsorte) / abhängig von [routen_kz]
@F bis_routen_wert|char(4) p8||bis Depot-, Länder- oder Depotgruppen-Code (Routungsorte) / abhängig von [routen_kz]
@E
@T vs_dpd_country
@D DPD-Ländercodes / kein Verwaltungprogramm / wird über „Import DPD-Routen-DB“ verwaltet
@F iso_num|smallint(3) p1||ISO numerisch
@F iso_kurz|char(2)||ISO Code 2 stellig
@F iso_lang|char(3)||ISO Code 3 stellig
@F sprachen_txt|char(50)||Ländercoes der im Land gesprochenen Sprachen / ist ein ‚text’-Datentyp, es werden max. 50 importiert
@F flag_pc_no|smallint(1)||kein Postleitzahlensystem / 0 = mit Postleitzahlensystem / 1 = ohne Postleitzahlensystem
@E
@T vs_dpd_depot
@D DPD-Depotstamm / kein Verwaltungprogramm / wird über „Import DPD-Routen-DB“ verwaltet
@F depot_cd|char(4) p1||Depotnummer
@F iata_cd|char(3) +n||IATA ähnlicher Code / wird nicht verwendet
@F depot_name1|char(35)||Depotanschrift / kann für die Ermittlung der Versanddepotanschrift bei DPD-Versand (Service = 101) herangezpgen werden
@F depot_name2|char(35)|
@F depot_adr1|char(35)||Depotadresse 1
@F depot_adr2|char(35)||Depotadresse 2
@F depot_plz|char(9)|
@F depot_ort|char(60)|
@F depot_land|char(2)||(ISO-Alpha2CoutnryCode)
@F depot_tel|char(35)|
@F depot_fax|char(35)|
@F depot_mail|char(35)|
@F depot_web|char(35)|
@E
@T vs_dpd_depotgrp
@D DPD-Zuordnung Depot zu Depotgruppen / kein Verwaltungprogramm / wird über „Import DPD-Routen-DB“ verwaltet
@F depot_cd|char(4) p1||Depotnummer
@F depot_grp|char(4) p2||Depotgruppe / (GroupID)
@E
@T vs_dpd_location
@D DPD-Location (wenn es keine Postleitzahlen gibt Pseudo-Postleitzahl) / kein Verwaltungprogramm / wird über „Import DPD-Routen-DB“ verwaltet
@F bereich|char(35) p1||Bezirk, Landkreis, ...
@F ort|char(35) p2||Ortsname
@F iso_kurz|char(2)||Land-Kz
@F plz|char(9)||Pseudo-Postleitzahl
@E
@T vs_dpd_kennsatz
@D DPD-Datenbank – Inpportdateien
@F filename|char(20) p1||Dateiname
@F version|char(8)||Versionsdatum = 1. Tag der Gültigkeit
@F expiration|char(8)||Datum der letzten Gültigkeit
@E
@T vs_dpd_routes
@D DPD-Routentabelle / kein Verwaltungprogramm / wird über „Import DPD-Routen-DB“ verwaltet
@F iso_kurz|char(2) p1||Land-KZ
@F von_plz|char(9) p2||von Postleitzahl / für Import: / NULL „ „
@F bis_plz|char(9) p3||bis Postleitzahl / für Import: / wenn NULL: / wenn [von_plz] = NULL od. „ „: [bis_plz] = zzzzzzzzz / sonst: [bis_plz] = [von_plz]
@F von_service_cd|smallint(3) p4||von Servicecode / für Import / in der Import-Datei werden alle möglichen Services in einem Datensatz übergeben / diese können im Format Saaa und/oder Sbbbccc sein / Mehrfacheintragungen sind durch Komma getrennt / z.B: / Saaa: aaa wird in [von_service_cd] und [bis_service_cd] gestellt / Sbbbccc: bbb = [von_service_cd], ccc = [bis_service_cd] / Saaa, Sbbbccc: 1 Datensatz mit aaa = [von_service_cd] und [bis_service_cd] + 1 Datensatz mit [von_service_cd] und ccc = [bis_service_cd] / kann aber auch Saaa, Sbbbccc, Sddd usw. sein
@F bis_service_cd|smallint(3) p5||bis Servicecode / siehe auch [von_service_cd] / [von_service_cd] und [bis_service_cd] = 0 ... Default-Datensatz (gilt für alle Services), wenn keine andere Eintragung gefunden wurde
@F routen_kz|char(1) p6||Routen-Kz: / [von_routen_wert] und [bis_routen_wert] sind bei: / D ... Depotnummern (4 stellig) / C ... Ländercodes (2 stellig) / G ... Depotgruppen (4 stellig) / „ „ ... wenn [von_routen_wert] und [bis_routen_wert] = „ „ (Defaultsatz, s.u.) / für Import: / das Feld „Routungort“ ist vom Datentyp „text“ in dem alle möglichen Werte in einem Datensatz übergeben werden / dieses Feld kann folgende Formate haben / Daaaa: aaaa = [von_routen_wert] u. [bis_routen_wert] / Dbbbbcccc: bbbb = [von_routen_wert], cccc = [bis_routen_wert] / Caa: aa = [von_routen_wert] u. [bis_routen_wert] / Gaaaa: aaaa = [von_routen_wert] u. [bis_routen_wert] / wobei Kombinationen von diesen Formaten vorkommen können / in solchen Fällen, muss für jede dieser Kombinationen ein Datensatz ausgegeben werden
@F von_routen_wert|char(4) p7||von Depot-, Länder- oder Depotgruppen-Code (Routungsorte) / abhängig von [routen_kz] / [von_routen_wert] und [bis_routen_wert] = „ „ ... Default-Datensatz für alle Standorte, für die es sonst keine Eintragung gibt
@F bis_routen_wert|char(4) p8||bis Depot-, Länder- oder Depotgruppen-Code (Routungsorte) / abhängig von [routen_kz]
@F sende_datum|char(10) +n||Sendedatum / wird z.Z. nicht verwendet
@F o_sort|char(4)||Ursprungssortierung
@F d_depot|char(4)||Zieldepot
@F group_prior|char(1)||Gruppierungspriorität
@F d_sort|char(4)||Zielsortierung
@F barcode_id|smallint(3)||Barcode-ID (ASCII-Code des Startzeichens z.B 37 = %)
@E
@T vs_dpd_service
@D DPD-Servicestamm / kein Verwaltungprogramm / wird über „Import DPD-Routen-DB“ verwaltet
@F service_cd|smallint(3) p1||Servicecode
@F service_txt|char(16)||Text
@F service_mark_kz|char(1)||Markierung
@F service_element|char(50)||Serviceelement / ist ein ‚text’-Datentyp, es werden max. 50 importiert
@E
@T vs_dpd_serviceinfo
@D DPD-Serviceinfo-Stamm / kein Verwaltungprogramm / wird über „Import DPD-Routen-DB“ verwaltet / es muss kein Datensatz zu einem Service vorhanden sein!
@F service_cd|smallint(3) p1||Servicecode
@F service_info_txt|char(100)||Infotext
@E
@T vs_fa
@D Versand-Firmenstamm
@F fa_nr|smallint(3)|p1
@F fa_name1|char(50)||Firmenanschrift
@F fa_name2|char(50)|
@F fa_name3|char(50)|
@F fa_name4|char(50)|
@F fa_strasse|char(50)|
@F fa_land_cd|char(3)|
@F fa_plz|char(10)|
@F fa_ort|char(50)|
@F fa_ustid|char(14)||UID-Nummer
@F fa_telefon|varchar(255)|
@F fa_bbn|integer(7)||BBN-Nummer
@F iftmin_warenbez|varchar(512)|
@E
@T vs_inhalt
@D Inhalt – Güterbezeichnungen
@F inhalt_cd|char(10) (p)|
@F inhalt_txt|char(30)||Text
@E
@T vs_verpart
@D Verpackungsarten
@F verpart_cd|char(10)|p1|Verpackungsart
@F verpart_mc|char(40)||Matchcode
@F iftmin_verpart|varchar(17)||Verpackungsartencode für EDI IFTMIN GID Segment / BND – Bund / CON – Container / EIM = Eimer / EUP – Euro Palette / EWP – Einweg Palette / FAS – Fass / GIX - Gitterbox / KRT – Karton / LOS = Lose / PKT = Paket / ROC = Rollcontainer / SAK = Sack / TRO = Trommel / …
@F iftmin_eqn_jn|char(1)||Wird als Ladehilfsmittel IFTMIN Segment EQN ausgegeben
@F verpart_eti_txt|char(10)||Text für Etikettendruck / Sollte im Standard auf 5 Stellen beschränkt sein
@F verpart_laenge_m|decimal(5,3)||Länge in m
@F verpart_breite_m|decimal(5,3)||Breiter in m
@F verpart_hoehe_m|decimal(5,3)||Höhe in m
@F verpart_kg|decimal(5,3)||Gewicht der Verpackung in kg für Vorschlag Bruttogewicht
@E
@T vs_versart
@D Versandarten / Umschlüsselungstabelle der Versandart auf die Verarbeitungsarten
@F versart_cd|char(10)|p1|Versandartencode lt. Warenwirtschaft
@F fa_nr|smallint|p2
@F versort_nr|smallint|p3|Versandortnummer
@F versart_mc|char(40)||Matchcode
@F vs_verarb_kz|char(10)||Verarbeitungskennzeichen / 'bex' = Bahnexpress / 'dhl' = DHL / 'diverse' = Diverse / 'dpd' / 'gls' / 'kvs' = Briefsendung ohne PostVersandSST / 'post' = Postversand / 'sped' = Spedition
@F fremd_kunde_nr|char(10)||Kundennummer beim Versanddienstleister
@F nummernvergabe_jn|char(1)||Bei Versandart gibt es eine Sendungsnummer / (bei „Dachser“ = „n“ – Nummernvergabe erfolgt beim Etikettendruck) / Abhänging von vs_verarb_kz: / bei „dpd“: bei numemrnvergabe_jn = „j“ wird Sendungnummer aus 4-stelliger Depotnummer + 10-stelliger lfd.Nummer, die über eigene Nummernvergabe (siehe [vs_versart]) vergeben wird / bei „n“ kann die Sendungsnummer eingegeben werden / "p" = die Nummernvergabe erfolgt pro Paket
@F nummernandruck_jn|char(1)||Andruck Sendungsnummer auf Versandschein / Gilt nur für bex
@F nr_kreis_sdg|char(10)||Nummernkreis für die Vergabe der Sendungsnummer / nummern.nr_kreis = vs_versart.nr_kreis + vs_auf.versort_nr ??? / bei „dpd“ = „ „ (da Nummervergabe über [vs_versart] erfolgt)
@F nr_kreis_lst|char(10)||Nummernkreis für die Vergabe der Listennummer
@F nachnahme_jn|char(1)||Sendung per Nachnahme möglich
@F vol_gew_koeff|decimal(8,4)||Volums/Gewichtskoeffizient (nur BEX)
@F edi_kz|char(10)||Kennzeichen für EDI-Variante / derzeit nur: / " " = kein EDI / "dachser" = EDI-Schnittstelle für Dachser / iftmin = IFTMIN 96A Spedition Gebrüder Weiss
@F edi_pfad|varchar(255)||Pfad + Dateiname für EDI-Schnittstelle / fix " " bei [edi_kz] = " " / bei IFTMIN können folgende Platzhalter verwendet werden / @DAT@ = aktuelles Datum im Format JJJJMMDD / @ZEIT@ = aktuelle Uhrzeit im Format JJMMSS / @JOB@ = Jobnummer
@F etikdruck_jn|char(1)||Versandetikett drucken j/n
@F vorlagenfile|char(10)||Vorlagenfile für Etiketten / fix " " bei [etikdruck_jn] = "n"
@F dpd_depot_cd|char(4)||DPD: / DPD-Depotnummer
@F dpd_service_cd|smallint(3)||DPD-Servicecode
@F dpd_service_kp_cd|smallint(3)||DPD-Servicecode für Kleinpakete
@F dpd_von_paket_nr|decimal(10,0)||DPD-Paketnummernkreis von
@F dpd_bis_paket_nr|decimal(10,0)||DPD-Paketnummernkreis bis
@F dpd_n_paket_nr|decimal(10,0)||DPD nächste Paketnummer
@F gls_version2d|char(1)||GLS: / Version des 2D-Codes (Data Matrix) / "A"
@F gls_cust_id|char(10)||Kundennummer bei GLS
@F gls_cont_id|char(10)||Kontaktnummer bei GLS
@F gls_gepard_nr|integer(9)||Gepard-Kundennummer bei GLS
@F gls_prodcode|char(2)||GLS Produktcode / "AA"
@F gls_cashcode|char(1)||GLS Cash-Servicecode / "D"
@F gls_prodcode_eu|char(2)||GLS Produktcode Export EU / "CC"
@F spedschein_jn|char(1)||Speditionsschein drucken J/N
@F vs_sst_kz|char(20)||Kennzeichen für Versandschnittstelle / " " … keine Schnittstelle / "p" … Polling, Schnittstelle zu Client-Software des Versanddienstleisters / "ws" … WebService des Versanddienstleisters / Eingabe nur möglich wenn [edi_kz] = " " / sonst fix " "
@F vs_sst_pfad|varchar(255)||Pfad für Versandschnittstelle / fix " " bei [vs_sst_kz] <> "p"
@F vs_sst_pfad_retour|varchar(255)||Pfad für Reoturmeldung Versandschnittstelle
@F edi_abs_mb_gln|varchar(35)||EDI Sender ID im UNB Segment / Mailbox Absender GLN Nummer / Ist bei GW ein GW interner Code
@F edi_empf_mb_gln|varchar(35)||EDI Reciver ID im UNB Segment / Mailbox Empfänger GLN Nummer / Ist bei GW ein GW interner Code
@F eti_belegnr_max_lng|smallint(3)||Maximale Länge der Belegnummern am Etikett / Default 10 / GW 32
@F versart_eti_txt|varchar(40)||Text für Etikettendruck
@F def_verpart_cd|char(10) +n||Default Verpackungsart für Pakete / Wenn angegeben wird mit der Erfassung auch sofort eine Paket Zeile vorgeschlagen.
@E
@T vs_versart_geb
@D Gebühren / Regisetr im Verwaltungsprogramm von vs_versart
@F versart_cd|char(10)|p1,f|Versandart
@F fa_nr|smallint|p2
@F versort_nr|smallint|p3
@F ab_dat|datetime|p4|gültig ab Datum
@F bis_dat|datetime||gültig bis Datum
@F ab_kg|decimal(7,2)|p5|ab Gewicht / keine Eingabe im Verwaltungsprogramm / st entweder 0 oder ab_kg + 0,01 des nächst kleinereeen bis_mg-Satzes
@F bis_kg|decimal(7,2)||bis Gewicht
@F gebuehr|decimal(7,2)||Gebühr
@E
@T vs_versort
@D Versandortstamm (statt vs_fa) / Bei Verwendung der IFTMIN EDI SST sollten die Feldlängen auf 35 Stellen begrenzt werden.
@F fa_nr|smallint(3)|p1
@F versort_nr|smallint(3)|p2|Versandortnummer
@F vo_name1|char(50)||Firmenanschrift
@F vo_name2|char(50)|
@F vo_name3|char(50)|
@F vo_name4|char(50)|
@F vo_strasse|char(50)|
@F vo_land_cd|char(3)|
@F vo_plz|char(10)|
@F vo_ort|char(50)|
@F vo_ustid|char(14)||UID-Nummer
@F vo_telefon|varchar(255)|
@F vo_mc|char(30)||Matchcode
@E
@T vs_waage
@D Versand – Waagenanbind
@F hostname|char(40) (p)|f|Hostname / Ist der Clientname auf dem das Versandprogramm läuft / Bei Serieller SST muss Client und Host identisch sein, damit die Waagenansteuerung möglich ist
@F waage_anschluss_kz|char(1)||Anschluss-KZ / s = Seriell (momentan ist im Standard nur seriell möglich)
@F device|char(70)||Ausgabe Device (z.B. com1:)
@F baudrate_kz|integer||Baud Rate für serielle Schnittstelle
@F bytesize_kz|smallint(1)||ByteSize für serielle Schnittstelle
@F parity_kz|smallint||0 = Keine / 1 = Even / 2 = Odd / 3 = Mark
@F waagensst_kz|char(10)||Waagen-SST KZ / "mt-sics" = Mettler Toledo – Standard Interface Command Set
@E
@T waehrung
@D Währungstabelle / Es muß einen Satz mit waehrung_cd = "EUR" geben
@F waehrung_upid|bigint +n|
@F waehrung_cd|char(4)|p1
@F waehrung_mc|char(20)|
@F denom_jn|Char(1)||Denominationskennzeichen
@E
@T waehrung_kurs
@D Währungstabelle Kurse
@F waehrung_cd|char(4)|p1,f
@F von_dat|date|p2|von Datum
@F bis_dat|date||bis Datum
@F kurs|decimal(20,10)||Kurs
@E
@T webshopattribute
@D Webshopnto Attribute
@F webshopattribute_snr|bigint (p)||Attribut lfdNr
@F webshopattribute_mc|varchar(40) ci||Attribute Matchcode
@F webshopattribute_code|varchar(40)||Attribute Label im WebShop
@F webshopattribute_kz|char(1)||a = Attribut / c = Column vom Artikelstamm
@F col_name|varchar(40)||Colum Name des Feldes am Artikelstamm
@F webshopattribute_typ_fkz|varchar(32)||Attributetype im WebShop / select / Sind Filterbar und können aus Auswahl für konfigurierbare Artikel verwendet werden / text - Wird nur angezeigt / string – wird nur angezeigt / boolean / ist Filterbar / Kann NICHT für konfigurierbare Artikel verwendet werden / int / Wird nur angezeigt / decimal / Wird nur angezeigt / multiselect / Es können mehrere Werte pro Artikel hinterlegt werden
@F sort_nr|integer||Sortiernummer
@F suchindex_jn|char(1)||Soll das Attribut im Suchindex verwendet werden
@F frontendfilter_jn|char(1)||Soll im Frontend ein Filter angezeigt werden / Kann nur bei select und boolean auf Ja gesetzt werden
@F vergleichsliste_jn|char(1)||Soll der Wert in der Vergleichsliste verwendet werden
@F produktdeatilanz_jn|char(1)||Auf der Produktdetailseite Anzeigen
@F html_jn|char(1)||Der Wert kann HTML beinhalten
@F suchgewichtung|decimal(8,4)||Gewichtung des Attributs in der Suche (um so größer um so wichtiger)
@F webshoptags_jn|char(1)||Die möglichen Attributwerte müssen über webshopattribute_tag vordefiniert bzw. ausgewählt werden.
@F aranzeige_jn|char(1)||Attribut wird am Artikelstamm angezeigt / Nein ist für Attribute, die kundenindividuell automatisiert generiert werden aber nicht am Artikelstamm angezeigt werden sollten um die Anzeige übersichtlich zu halten.
@E
@T webshopattribute_sprache
@D Webshopnto Attribute
@F webshopattribute_snr|bigint|p1,f|Attribut lfdNr
@F sprache_cd|char(5)|p2|Sprache
@F webshopattribute_txt|varchar(255)||Attributetext der im WebShop angezeigt wird
@E
@T webshopattribute_tag
@D Webshop Attribute / Mögliche Values für select und multiselect Attribute, die keine Columns sind
@F webshopattribute_snr|bigint|p1,f|Attribut lfdNr
@F webshoptag_snr|bigint|p2,f|WebShop Tag Nr
@E
@N /
@T webshopicon
@D WebShop Icons
@F webshopicon_cd|char(5) (p)||Icon Code
@F webshopicon_mc|varchar(40) ci|
@F iconfile|varchar(255)||Filiname des Icons am WebShop / Die Files sind nicht in TC zuordenbar, der ICONFilename bezieht sich immer nur auf Files, die am WebShop vorhanden sind
@F sort_nr|smallint||Sortiernummer
@F internet_link|varchar(255)||Internet Link
@F icon_label_txt|varchar(500)||Label Text
@F webshopicon_kz|char(3)||Kennzeichen, z.b. Sicherheit….. / default = blank / s = Sicherheitshinweise /  / Kundenindividualfelder sind immer 3-stellig anzulegen und mit dem Shopteam abzusprechen
@E
@T webshoplager
@D WebShopLager (Dummy Satz mit „“)
@F webshoplager_cd|varchar(20) (p)||WebShopLager Code
@F webshoplager_mc|varchar(40)||WebShopLager Bezeichnung
@F fa_nr|smallint|p2|Firmennummer
@F fil_nr|smalint|f
@F webshoplager_aktiv_jn|char(1)|
@F latitude|decimal(9,6) +n|
@F longitude|decimal(9,6) +n|
@F shipping_jn|char(1)|
@F pickup_jn|char(1)|
@F ws_def_lag_cd|char(11) + n|f|lag_kz in (‚e‘, ‚l‘) Default Lager für Import, wenn Null lst. TC Standard
@F webshoplager_bez|varchar(255)||Bezeichnung im Shop (magento_source_codes.name) / muss <> ‚‘ und unique sein, wenn webshoplager_cd <> ‚‘
@E
@T webshopkdgrp
@D WebShopkundengruppe
@F webshopkdgrp_cd|varchar(20) (p)||WebShopkundengruppencode / Im Standard sind folgende Werte vorhanden: / b2b – Firmenkunden / b2c - Privatkunden
@F webshopkdgrp_mc|varchar(40)||WebShop Kundengruppenmatchcode
@F winmodus_kz|char(3)||Winmodus für Artikelanlage (Default = web) / Darüber ist es möglich unterschiedliche Defaultwerte für die Kundengruppen vorzusehen
@F wskdanl_kz|char(1)||WebShop Kundenanlage KZ für neue Kunden / a = werden automatisch angelegt / w = Workflow wird ausgelöst (nur bei WF-Modul verfügbar) / z = Zuordnen von vorhandenen Kunden (und Automatische Anlegen wenn nicht zuordenbar) / - = Keine automatische Anlage /
@F adrupd_jn|char(1)||Adressänderungen sollen durchgeführt werden / Standard: b2b Nein, b2c Ja
@F kundeerl_liefadr_jn|char(1)||Kundenerlösgruppe des Auftrags lt Land der Lieferadresse bestimmen
@E
@T webshopkdgrp_land
@D WebShopundengruppen - Ländereinstellungen
@F webshopkdgrp_cd|varchar(20)|p1,f|WebShopkundengruppencode / Im Standard sind folgende Werte vorhanden: / b2b – Firmenkunden / b2c - Privatkunden
@F land_cd|char(3)|p2,f|Ländercode lt. Lieferadresse
@F fa_nr|smallint|p3
@F kundeerl_cd|char(10) +n|f|Kundenerlöszuordnung für neue Firmenkunden
@F debitor_nr|integer +n|f|Debitorennummer für die automatische Kundenanlage
@F gast_kunde_cd|char(10) +n|f|Kundennummer für WebShop Gast Aufträge
@E
@T webshopobj
@D WebShop Objekte
@F webshopobj_cd|char(5)|p1|Objektartencode / arb = Artikelbild – wird bei der WebShop Ausgabe als Haupt-Artikelbild verwendet
@F fa_nr|smallint|p2,f|Firmennummer
@F webshopobj_mc|varchar(40) ci|
@F webshopobj_path|varchar(255)||Pfad im Filesystem für File lt. Stammdaten (Artikel)
@F wg_ webshopobj_path|varchar(255)||Pfad im Filesystem für File lt. Warengruppe #53662
@F webshopobj_praefix|char(10)||Praefix des Dokumentes
@F webshopobj_kz|char(1)||Webshop Objekttyp / b = Bild (jpg oder png) / p = PDF / m = mp3 / l = Link / v = Video
@F webshopobj_webshop_path|varchar(255)||Relativer Pfad des Bild Verzeichnisses am WebServer (Artikel)
@F wg_webshopobj_webshop_path|varchar(255)||Relativer Pfad des Bild Verzeichnisses am WebServer (Warengruppe) #53662
@F wsobj_ausg_kz|char(1)||Webshopobjekt Ausgabe KZ / a = Artikelhauptbild (Es darf nur einen Eintrag mit a geben = arb) / b = (zusatz) Bilder (Vorschlag bei Bild) / wird als additional_images ausgegeben / d = Documents (Fix bei pdf und mp3) / l = Link / w = Download Link / Kann nur bei Link verwendet werden / Es darf pro Artikel nur einen geben. / Wenn es bei einem Verrechnungsartikel ein solches Objekt gibt, dann wird der Artikel als Digitiales Produkt (downloadable) an den Magento WebShop ausgegeben. / s = Sample Link / kann nur bei Link verwendet werden / Es darf pro Artikel nur einen geben
@F sort_nr|smallint||Sortiernummer
@E
@T webshopobj_sprache
@D WebShop Objekte – Labeltexte / N
@F webshopobj_cd|char(5)|p1,f|Objektartencode
@F fa_nr|smallint|p2|Firmennummer
@F sprache_cd|char(5)|p3,f|Sprache
@F webshopobj_label|varchar(100)||Label Text für das WebShopObjekt / Darf keine Beistriche und keine Anführungszeichen (") enthalten
@E
@T webshoptag
@D Webshop Tags
@F webshoptag_snr|bigint (p)||WebShop Tag interne Nummer / Vergabe über pfu_serial
@F webshoptag_mc|varchar(60) (ci)||Tag
@E
@I unique index i1_webshoptag (webshoptag_mc)
@T webshoptag_sprache
@D Webshop Tags - Sprache
@F webshoptag_snr|bigint|p1|WebShop Tag interne Nummer / Vergabe über pfu_serial
@F sprache_cd|char(5)|p2|Sprache / Es muss pro webshop_snr einen Datensatz mit "d" geben.
@F webshoptag_txt|varchar(60) (ci)||Tag
@F ueberarbeiten_jn|char(1)||Datensatz in Fremdsprache wurde automatisch aus dem deutschen Text kopiert und muss überarbeitet werden. / Wird durch eine manuelle Änderung des Textes im Verwaltungsprogramme (auch in Liste möglich) auf "n" gesetzt.
@E
@T webshopusr
@D WebShop User / Wird von WebShop Angelegt und hier geinsertet und kann auch in TC angelegt werden. / Wenn der User am WebShop angelegt wurde, kann in TC der User nur einem Kunden zugeordnet oder inaktiv gesetzt werden.
@F webshopusr_nr|integer(8) (p)||WebShop Usernummer / = Vergabe über pfu_serial
@F hpt_webshopusr_nr|integer(8) +n||Hauptusernummer / Wenn null dann handelt es sich um einen Hauptuser / Sonst ein SubUser (s:)
@F kunde_system_id|varchar(32)||Magento Kunden System ID / Eindeutige Kennung des Users in Magento /
@F address_system_id|varchar(32) +n||Magento Adress ID / Eindeutige ID der Adresse in Magento / Wenn User von TC angelegt wird, muss hier die tc_<adr_snr> verwendet werden
@F kunde_system_parrent_id|varchar(32) +n||Magento Hauptuser System ID /
@F geschlecht_kz|char(1)||m|männlich
@F geschlecht_kz|char(1)||w|weiblich
@F geschlecht_kz|char(1)||bei Firma/Kunde/Lieferant selbst – Gast
@F geschlecht_kz|char(1)|
@F titel|varchar(30)||Titel /
@F v_name|varchar(30)||Vorname /
@F n_name|varchar(30)||Nachname /
@F geburt_dat|date +n||Geburtsdatum /
@F telefon|varchar(50)|r|Telefonnummer / Bei pers_cd " " lt. Standard Kommunikationsart adr_belartkom / 1. Vorkommnis in adr_pers_komid mit komidart_kz = 't' /
@F email|varchar(50)|r|Email-Adresse / Bei pers_cd " " lt. Standard Kommunikationsart adr_belartkom 1. Vorkommnis in adr_pers_komid mit komidart_kz = 'e' / In einem WebShop (mage_website_code ) muss die E-Mail Adresse unter den aktiven Usern eindeutig sein /
@F company|varchar(255) ci||–Firmenname - Lieferadresse /
@F strasse|varchar(50) ci|
@F land_cd|char(3)|f
@F plz|varchar(10)|
@F ort|varchar(40) ci|
@F ustid|varchar(14)||UID Nummer /
@F vrech_email|varchar(255)||E-Mail Adresse für E-Mail Versand /
@F fa_nr|smallint||Firmennummer /
@F kunde_cd|char(10) +n|f|Kundennummer in TC / Wenn noch nicht zugeordnet dann null / Wird bei der Anlage in TC gesetzt / Kann manuell geändert werden
@F kunde_adr_snr|decimal(14,0) +n|r|lt. Kundenstamm
@F kunde_pers_cd|char(10) +n||Personencode in TC /
@F webshop_datz|datetime||Zeitpunkt der Übernahme vom WebShop /
@F webshopusr_status_kz|char(1)||Status des Imports von WebShop in TC / n = Neuer User (Default bei Neuanlage vom WebShop) / a = Änderung offen / e = Erledigt
@F webshopusr_aktiv_jn|char(1)|
@F ao_snr|decimal(14,0)|
@F rech_titel|varchar(30)||Rechnungsadresse /
@F rech_v_name|varchar(30)|
@F rech_n_name|varchar(30)|
@F rech_company|varchar(255) ci|
@F rech_strasse|varchar(50) ci|
@F rech_land_cd|char(3)|f
@F rech_plz|varchar(10)|
@F rech_ort|varchar(40) ci|
@F rech_address_system_id|varchar(32) +n||Magento Adress ID / Eindeutige ID der Adresse in Magento / Wenn die Adresse von TC generiert wird, muss hier "tc_<adr_snr>" verwendet werden.
@F rech_geburt_dat|date+n|
@F rech_geschlecht_kz|char(1)|
@F rech_adr_snr|decimal(14,0) +n|r|lt Debitor
@F rech_pers_cd|char(10) +n||Personencode in TC /
@F mage_website_code|varchar(250)||WebShop Code /
@F webshopkdgrp_cd|varchar(20)||WebShop Kundengruppencode / Im Standard Vorhanden: / b2b – Business/Firmenkunden / b2c – Privatkunden (alte Logik – keine UID Nummer ausgefüllt) /
@E
@I index i1_webshopusr (ao_snr)
@I index i2_webshopus4 (kunde_cd, fa_nr)
@I index i3_webshopusr (email)
@T webshopwg
@D Magento/WebShop Warengruppe / Es gibt einen Dummy Satz mit 0
@F webshopwg_snr|integer(8) (p)||Magento Warengruppennummer / Vergabe über pfu_serial
@F webshopwg_mc|varchar(100) ci||Webshopwarengruppen Matchcode / Darf keinen Beistrich (,) oder Schrägstrich (/) enthalten
@F bild_endung|varchar(5)||Endung bei Bild Objekt / jpg / jpeg / png / bmp
@F webshop_wg_aktiv_jn|char(1)||Aktivkennzeichen / Inaktive werden im Shop nicht angezeigt
@E
@T webshopwg_parent
@D Zuordnung Warengruppe zu ParentWarengruppe
@F webshopwg_snr|integer(8)|p1,f|Magento Warengruppennummer
@F parent_webshopwg_snr|integer(8)|p2,f|Parent Warengruppennummer / Verweis auf eine übergeordnete Warengruppe / Es darf keine Schleife gebildet werden / Bei einer Haupt-WG wird hier 0 verwendet
@F sort_nr|integer||Sortierunummer innerhalb eines Zweiges
@F ws_anzeigen_jn|char(1)||Warengruppe soll im Webshopmenü unter diesem Parent angezeigt werden (oder ausgeblendet sein). steuert magento_categories. include_in_menu und vererbt sich in diesem Zweig auf alle childs
@E
@T webshopwg_artik
@D Magento/WebShop Warengruppe – Artikelzuordnung
@F webshopwg_snr|integer|p1,f|Magento Warengruppennummer
@F artik_cd|char(20)|p2,f|Artikelnummer
@F fa_nr|smallint|p3|Firmennummer
@E
@I index i1_magewg_artik (artik_cd, fa_nr, magewg_snr)
@T webshopwg_sprache
@D Magento/WebShop Warengruppe/Sprache
@F webshopwg_snr|integer(8)|p1,f|Magento Warengruppennummer
@F sprache_cd|char(5)|p2|Sprache
@F webshopwg_name|varchar(255)||Warengruppenbezeichnung / Aus diesen Bezeichnungstexten wird der Pfad für die Warengruppe im WebShop gebildet.
@F webshopwg_desc|varchar(max)||Beschreibungstext
@F seitennavi_txt|varchar(255)||Text für seitliche Navigation / Wird bei der Änderung der Warengruppenbezeichenung aus dieser vorgeschlagen, solange sie identisch ist.
@F meta_title|varchar(70) +n||SEO Title Text
@F meta_description|varchar(255) +n||SEO Beschreibungstext
@F webshopwg_seo_txt|varchar(max)ci +n||SEO Text für magento_categories
@E
@T webshopwg_webshopattribute #53662
@D Magento/WebShop Warengruppe/Attribute
@F webshopwg_snr|integer(8)|p1,f|Magento Warengruppennummer
@F webshopattribute_snr|bigint|p2,f|Attribut lfdNr
@F webwgatt_zwingend_jn|char(1)||Zwingende Warenguppe beim Artikel / sobald eine Warengruppe vom Artikel das Attribut als zwingend hinterlegt darf dieses nicht gelöscht werden
@F webwgatt_default|varchar(8000) +n||Defaultwert
@E
@T webshopwg_webshopobj #53662
@F v|Magento/WebShop Warengruppe/Objekt|
@F webshopwg_snr|integer(8)|p1,f|Magento Warengruppennummer
@F webshopobj_cd|char(5)|p2,f
@F fa_nr|smallint|p3
@F webshopobj_link|varchar(500) +n||Link – Bei Link Objekt
@F bild_endung|varchar(5)||Endung bei Bild Objekt / jpg / png
@F ltz_aend_datz|datetime||Zeitpunkt der letzten Änderung
@F webshopobj_filename|varchar(255)||Dateiname (ohne Endung)
@E
@T webshopzahlart
@D Magento/WebShop Zahlungsarten / Umschlüsselung Magento Payment Type auf TC Zahlungsart für Online Zahlungen
@F payment_method|varchar(255)|p1|Magento Zahlungsart
@F magento_card|varchar(50)|p2|Kartentype / Es wird zuerst der Datensatz mit der richtigen magento_card verwendet, wenn nicht gefunden wird der Datenstz mit magento_card = blank verwendet.
@F fa_nr|samllint|p3
@F zahlart_cd|char(5)|f
@E
@T wv
@D Wartungsvertrag
@F wv_nr|integer(7)|p1|Wartungsvertragsnummer / Vergabe/Kontrolle mittels Tabelle nummern
@F fa_nr|smallint(3)|p2
@F fil_nr|smallint(3)|f|Filiale
@F kunde_cd|char(10)|f,n|Kundennummer
@F wv_dat|date|ng|Erfassungsdatum
@F vkrech_kz|char(2)||Art der Fakturierung
@F vkrech_kz|char(2)||d|Sammelrechnung pro Debitorennummer
@F vkrech_kz|char(2)||k|Sammelrechnung pro Kundennummer
@F vkrech_kz|char(2)||r|Einzel- Rechnung
@F vkrech_sel_fkz|char(3)||Selektionskennzeichen zum Zusammenstellen von Lieferscheinen zu einer Sammelrechnung / Es sollte aber pfu_kz angelegt werden.
@F debitor_nr|integer(9)|f,ng|wird bei der Anlage = kunde.debitor_nr
@F zahlart_cd|char(5)|f|Zahlungsart
@F anz_vkrech|smallint(2)||Anzahl Rechnungen
@F wv_waehrung_cd|char(4)|f,ng|Währung für Preise der Positionen / Beim Auftragsaufbau wird Wartungsvertrag auf Währung des Debitoren konvertiert, falls diese eine andere ist.
@F wv_preisli_cd|char(5)|f,ng|Preislistencode / wenn vorhanden aus s_kunde
@F wv_vkrab|decimal(4,2)||Auftragsrabatt für die für die Verrechnung aufzubauenden Aufträge
@N Zahlungskonditionen:
@F skonto1_prz|decimal(4,2)||1. Skontoprozentsatz
@F skonto1_tg|smallint(3)||dazu Ziel- Tage
@F skonto2_prz|decimal(4,2)||2. Skontoprozentsatz
@F skonto2_tg|smallint(3)||dazu Ziel- Tage
@F netto_tg|smallint(3)||Ziel- Tage für Netto- Zahlung
@F wv_zollta_dru_jn|char(1)||Zolltarifnummer auf Rechnungsbelegen drucken
@F kunde_sb_pers_cd|char(5)||Sachbearbeiter des Kunden, welcher für den Wartungsvertrag zuständig ist
@F wv_fa_pers_cd|char(5)|ng|Sachbearbeiter der eigenen Firma, welcher Wartungsvertrag erfaßt hat
@E
@T wv_pos
@D Wartungsvertragsposition
@F wv_nr|integer(7)|p1,f
@F fa_nr|smallint(3)|p2
@F wv_pos_nr|smallint(4)|p3|kann wahlweise in Schritten vergeben bzw. übersteuert werden
@F wv_artik_cd|char(20)||Gerät, welches unter Wartung steht
@F wv_geraet_cd|char(40)||Gerät, welches unter Wartung steht
@F wv_geraet_artik_cd|char(20)|f|nur für den f- Key auf das Gerät: / kein AEO / 2 möglichkeiten: / Kein Gerät angegeben: / wv_geraet_cd = "" / wv_geraet_artik_cd = fa.dummy_artik_cd / dies ist ein Dummy- Gerät / dies ist nur erlaubt, wenn artik.muss_geraet_cd_jn = 'n' / Gerät angegeben: / wv_geraet_cd = lt. Eingabe / wv_geraet_artik_cd = s_artik_cd / F- Key: wv_geraet_cd, wv_geraet_artik_cd, fa_nr geraet
@F wv_ende_dat|date||Ende Datum / Bis zu diesem Datum ist Gerät unter Wartung / muß ein Monatsletzter sein / Ist das Ende offen, ist das größtmögliche Datum einzutragen (gf_DatMax())
@F abrech_mo|decimal(2,0)||Abrechnungsperiodendauer in Monaten
@F abrech_anz|decimal(3,0)||Anzahl der erfolgten Abrechnungsläufe / bei der Neuanlage 0 / wird nur vom Abrechnungslauf erhöht
@F n_abrech_dat|date||Datum des nächsten Abrechnungslaufs / die Rechnung betrifft dann die Abrechnungsperiode, die / mit n_rech_dat beginnt, wenn n_rech_dat ein Monatserster ist, / sonst mit dem nächstfolgenden Monatsersten beginnt. / wenn die Wartung noch nicht zu ende ist muß gelten: / n_rech_dat > wv_beginn_dat + ( arech_mo * abrech_anz – 1 ) Monate / n_rech_dat <= wv_beginn_dat + ( arech_mo * abrech_anz ) Monate / n_rech_dat <= Monatserster von wv_ende_dat / Die letzte Rechnung kann weniger als abrech_mo Monate umfassen / Wird vom Aufbau des Abrechnungsauftrages um abre_mo Monate erhöht, ist das erhöhte Datum zu groß, ist die Wartung zu Ende und n_rech_dat wird auf das größtmögliche Datum (gf_DatMax()) gesetzt. / kann nur das größtmögliche Datum (gf_DatMax()) sein, wenn der Auftrag für die letzte Abrechnung bereits aufgebaut ist.
@F wl_artik_cd /|char(20)|f,n|Artikelnummer der Wartungs- Leistung / artik_kz muß "w"sein / bestimmt den Leistungsumfang der Wartungsvertragsposition
@F wl_vkpr|decimal(12,3)||Verkaufspreis pro Monat / versteht sich in wv.waehrung_cd / exkl. USt / Die Vorschlagswerte bei der Neuanlage werden lt. Preisfindung ermittelt. / Siehe dazu vkkond
@F wl_vkrab1|decimal(4,2)||Rabatt 1, siehe vkpr
@F wl_vkrab2|decimal(4,2)||Rabatt 2, siehe vkpr
@F wl_vkrab3|decimal(4,2)||Rabatt 3, siehe vkpr
@F wl_vkrab4|decimal(4,2)||Rabatt 4, siehe vkpr
@F wl_vkrab5|decimal(4,2)||Rabatt 5, siehe vkpr
@F erl_wv_nr|integer(7)||0 Wartungsvertrag ist aktiv / wv_nr Wartungsvertrag ist erledigt: wird beim letzten Verrechnungslauf gesetzt
@E
@I index i1_wv_pos ( n_rech_dat, wv_nr )
@I index i2_wv_pos ( erl_wv_nr, wv_nr, pos_nr )
@T wv_pos_txt
@D Wartungsvertragspositions- Textzeilen mit Artikelbezeichnung /  / Wird bei der auf_pos-Neuanlage aus artik_txt vorbelegt, wobei Rows berücksichtig werden für die gilt: / sprache_cd = adr.sprache_cd and kunde.kunde_adr_snr = adr.adr_snr and rech_jn = 'j'
@F wv_nr|integer(7)|p1
@F fa_nr|smallint(3)|p2
@F wv_pos_nr|smallint(4)|p3,f
@F txt_typ_kz|char(1)|p4|Texttyp / "r" Richtext / wenn [param.appl_txt_kz = "r"] / Standardfont und -größe lt. Parameter / "p" Plaintext / wenn [param.appl_txt_kz <> "r"]
@F zeile_nr|smallint|p5|Zeilennummer
@F fett_jn|char(1)||fett drucken / fix "n", wenn [txt_typ_kz = "r"]
@F unterstrichen_jn|char(1)||unterstrichen drucken / fix "n", wenn [txt_typ_kz = "r"]
@F auf_pos_txt|varchar(max)||Auftragspositionstext- Zeile / generierter Plaintext(auf_pos_rtxt), wenn [txt_typ_kz = "r"] / eingegebener Text, sonst
@F wv_pos_txt_dbid|integer identity||ROWID für Retrieve Richtext / durch DB-Default mit serieller Nummer belegt
@F auf_pos_rtxt|varbinary(max)||Wartungsvertragspositionstext Richtext / wenn [txt_typ_kz = "p"], durch DB-Default mit Leerstring belegt
@E
@T unique index i1_wv_pos_txt (wv_pos_txt_dbid)
@D /
@E
@T zahlart
@D Zahlungsart / z.B.: Zahlschein, Nachnahme, Bankeinzug / Es gibt einen Dummy-Satz mit zahlart_cd = " "
@F zahlart_upid|bigint +n|
@F zahlart_cd|char(5)|p1
@F fa_nr|smallint(3)|p2,f
@F zahlart_mc|char(40)||Bezeichnung
@F erlagschein_dru_kz|char(2)||Erlagschein Druck KZ / n = Nicht drucken / j = Zahlschein (alte Version) / sh = SEPA-Zahlschein A4-Hoch / sq = SEPA-Zahlschein A4-Quer / qr = QR-Code drucken
@F bank_bez|char(40)||Bankbezeichnung
@F blz|char(6)||Bankleitzahl
@F konto_nr|char(11)||Kontonummer
@F bic|char(11)||Bank Identifier Code / für SEPA-Zahlscheindruck
@F iban|char(34)||Iban für Andruck am SEPA-Zahlschein
@F empf_bez1|char(40)||Empfänger
@F empf_bez2|char(40)|
@F statt_zkond_txt|char(100)||Text, welcher statt den Zahlungskonditionen auf Rechnungsbeleg gedruckt wird. Leer bedeutet Zahlungskonditionen lt. Tabelle vrech.
@F statt_zkond_ab_jn|char(1)||Zahlungskonditionstext wird auch auf AB und Kostenvoranschlag gedruckt / damit können Texte wie "Betrag dankend erhalten" von AB, Offert, Proforma und Kostenvoranschlag ferngehalten werden
@N wenn eines der folgenden Konditions-Datenfelder <> 0 ist, wird diese Kondition anstelle der Kundenkondition beim Auftrag verwendet
@F skonto1_prz|decimal(4,2)||1. Skontoprozentsatz
@F skonto1_tg|smallint(3)||dazu Ziel- Tage
@F skonto2_prz|decimal(4,2)||2. Skontoprozentsatz
@F skonto2_tg|smallint(3)||dazu Ziel- Tage
@F netto_tg|smallint(3)||Ziel- Tage für Netto- Zahlung
@F ka_aufueb_jn|char(1)||offene Aufträge an Kassa übertragen / Das sind jene Aufträge zu denen evt. eine Anzahlung auf der Kassa erfasst werden kann.
@F ka_opueb_jn|char(1)||Offene Posten an Kassa übertragen
@F ka_zahlung_cd|char(3) +n||Kassa-Zahlungsart / Wenn ungleich Null – die Kassen-Zahlungsert mit der die Zahlungsbuchung der Rechnung aufgebaut wird.
@F zahlbetr_dru_jn|char(1)||Skonto u. Zahlungsbetrag werden wie bei Barverkauf betragsmäßig ausgewiesen
@F fibukto_nr|integer(9)||Zahlungskonto / wenn <> 0, wird in der Buchhaltung nach dem Verbuchen der AR sofort die Zahlung gebucht
@F fb_za_sy|char(2)||Buchungssymbol für Zahlungsbuchung
@F zahlschein_kz|char(3)||Wert für Zahlscheinlesezone / " " wenn bereits vorgedruckt / "30+" für SEPA Zahlschein / "40+" für Inlands Zahlschein (alte Version) / weitere durch customizen möglich
@F zkond_txt_cd|char(20)||Code des Textbausteines welcher nach Zahlungskondition oder Zahlungskonditionstext auf Rechnungsbeleg gedruckt wird
@F zkond_ab_txt_cd|char(20)||Code des Textbausteines welcher nach Zahlungskondition oder Zahlungskonditionstext auf AB, Offert, Proforma oder Kostenvoranschlag gedruckt wird
@F eb_payment_kz|char(1)||Zahlungsmethode für ebInterface (Zahlung an Bund) / ‚u‘ – Überweisung (UniversalBankTransaction) / ‚l‘– Lastschriftverfahren (DirectDebit) / ‚ ‚ - keine
@F qr_betrag_kz|char(1)||Welcher Betrag wird im Zahlungs-QR-Code übergeben, wenn Skonto verwendet wird. / k = kein Betrag ausgeben / s = Den um den Skonto vermindertenBetrag ausgeben / e = Endbetrag ohne Skontoabzug ausgeben
@E
@T zahlkond
@D Zahlungskondition / ist bei Jetfibuintegration ein View auf die Tabelle ankond / bei BMD-Fibu oder EuroFib echte Tabelle / Ohne Jetfibuintegration gibt es einen Dummysatz mit zahlkond_nr = 0
@F zahlkond_nr|integer|p1|interne Nummer / fortlaufende Vergabe mit MAX + 1
@F standard_jn|smallint (1)||Kondition ist eine Standardkondition / 0 (n) / 1 (j)
@F zahlkond_info|char(20)||Infotext
@F skonto1_prz|decimal(4,2)||1. Skontoprozentsatz
@F skonto1_tg|smallint(3)||dazu Zieltage
@F skonto2_prz|decimal(4,2)||2. Skontoprozentsatz
@F skonto2_tg|smallint(3)||dazu Zieltage
@F netto_tg|smallint (3)||Nettotage
@E
@T zeile
@D Zeile / dient dazu, um in einem genesteten Report n Zeilen mit einem Fixtext zu drucken / z.B.: Kommissionsschein auf_pos.frei_mg Zeilen zum eintragen der Seriennummern
@F zeile_nr|smallint|p1|Zeilennummer (1 - 1000)
@E
@T zfartik
@D Vormerktabelle zum Zusammenführen von Artikeldaten
@F artik_cd|char(20)|p1,f|Artikel alt
@F fa_nr|smallint(3)|p2
@F neu_artik_cd|char(20)|f|Artikel neu / neu_artik_kz = artik_kz / neu_lagfuehr_kz = lagfuehr_kz / neu_chargen_kz = chargen_kz
@F zf_ek_kz|char(1)||Einkaufsdaten (artik_lief, artik_lief_ekpr, artik_lief_projpr) / Produktionsdaten (artik_prodart; artik_prodart_ag) / "k" kopieren / "v" verschieben / "-" keine Aktion
@F zf_vk_kz|char(1)||Verkaufskonditionen (vkkond, vkkond_preis) / "k" kopieren / "v" verschieben / "-" keine Aktion / "k" nur erlaubt, wenn neu_artik_cd = neu_preis_artik_cd / "v" nur erlaubt, wenn neu_artik_cd = neu_preis_artik_cd & artik_cd = preis_artik_cd
@F zf_id_kz|char(1)||ArtikelId's (Kennzeichen: e, l, k, s, d) / "v" verschieben / "-" keine Aktion
@F zf_beweg_jn|char(1)||Lager- und Bewegungsdaten werden übernommen
@F zf_status_kz|char(1)|g|"n" neu / "p" Prüfung erfolgt / "e" Einkauf erfolgt / "i" Identifikationen erfolgt / "l" Lager erfolgt / "s" Gerätedaten erfolgt / "b" Buchungszeilen läuft / "o" Umstellung OK /  / n Ändern, Löschen erlaubt / o Löschen erlaubt / sonstige Ändern (nicht Artikelnummern) erlaubt
@F zf_txt|char(60)|g
@F zf_lock_jn|char(1)||Datensatz in Bearbeitung / ist bei der Neuanlage fix "n" / wird vom Zusammenführungsprogramm beim abarbeiten des Datensatzes auf "j" umgestellt / wird nach dem erfolgreichen Zusammenführen der beiden Artikel wieder auf "n" umgestellt / kann mit Berechtigung im Anlageprogramm auf "n" gesetzt werden
@F dat_beginn|datetime +n||Beginn Umstellung
@F dat_ende|datetime +n||Ende Umstellung
@E
@T ztnr
@D Zolltarifnummern / Es gibt einen Dummy Satz mit Blank
@F is_zollta_nr|char(8) (p)||Zolltarifnummer (=KN8 Code)
@F ztnr_mc|varchar(1000) (ic)||Zolltarifnummer Matchcode
@F bmaeh_kz|varchar(20)||Besondere Maßeinheit Kennzeichen lt. Statistik-Austria
@F is_veh_bmaeh_ftr|decimal(12,6)||Besondere Maßeinheit – Vorschlagswert für Artikelstammdaten
@F ztnr_aktiv_jn|char(1)||Zolltarifnummer ist aktiv
@F eudr_jn|char(1)||EUDR ist bei dieser Zolltarifnummer verpflichtend
@F import_job_snr|bigint|g|Import ist mit dieser Jobnummer erfolgt / 0 = manuell erfasst
@F eudr_fix_jn|char(1)||EUDR am Artikelstamm ist fix die lt. Zolltarifnummer und kann nicht geändert werden. / Bei Fix j wird das eudr_jn bei allen Artikeln mit dieser Zolltarifnummer gleich gehalten.
@E
@T zuab
@D Zu- /Abschläge / dzt. nur für Einkaufszu- bzw. abschläge / dient auch für die Verbuchung von "nicht"-Handelswarenrechnungen
@F zuab_cd|char(10)|p1
@F fa_nr|smallint(3)|p2|Firma
@F zuab_mc|char(40)||Matchcode
@F zuab_artik_cd|char(20)||Zuschlagsartikel / bestimmt Kore- und Sachkontenzuordnung
@F fibu_jn|char(1)||Zuschläge werden in Fibu (Kontierung) gebucht
@F wawi_jn|char(1)||Zuschläge werden in Wawi für die DuEst-Berechnung auf Artikelpositionen aufgeteilt
@E
