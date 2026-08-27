# Programmiererdoku

> Originale TradeControl-Programmiererdokumentation, als Markdown
> aufbereitet. Inhalt und Terminologie wurden nicht fachlich verändert.

## Wo ist was zu finden und wer ist zuständig

Anmerkung: \`Installation beim Kunden.doc´ liegt unter
P:`\InstallVorlagen`{=tex}

## AmyUni

-   Support hat SK nie in Anspruch genommen

-   Kontaktdaten im Outlook hmp unter
    AufbehalteneEMails`\SwEntwicklung`{=tex}`\AmyUni`{=tex}

-   Die Installationsmedien liegen unter
    P:`\InstallVorlagen`{=tex}`\Allgemein`{=tex}`\Amyuni`{=tex}`\AmyUni4.5`{=tex}.2.9

-   Dies ist allerdings nicht vollständig

-   Der Communication Daemon verwendet genau eine .net- dll - diese ist
    allerdings nur im Team-System unter Bibliotheken/AmyUni zu finden -
    es handelt sich dabei um den Creator/Viewer

-   PB und/oder die PCS.Interop verwenden die Active-X- Version von
    Converter/PrinterDriver

-   Beim Kunden und auf unseren Entwicklungsrechnern sind die Files
    unter P:`\InstallVorlagen`{=tex}`\Exec `{=tex}Verzeichnis beim
    Kunden`\AmyUni45`{=tex} zu verwenden

-   Die Original-Medien sind nicht auffindbar

-   Unter S:`\Windows`{=tex}`\Amyuni `{=tex}sind noch Versionen bis 4.0
    zu finden

-   Powerbuilder verwendet:

    -   OCX zur PDF- Anzeige ( PDFCreactiveX.dll + acPDFCrExt.dll
    -   Druckertreiber

-   Es gibt Hakerl, ob ggf. installiert werden soll - KLÄREN!!!

-   Anmerkung RB: wenn angehakt und AmyUniVeersionWechsel: entweder
    Drucker löschen, oder der Name des Druckers (= "PCS\_" +
    pfu_host_installinfo.appl_par_wert ) muss geändert werden

-   Powerbuilder im Haus: das PDF- Erstellen erfolgt immer mit der
    neuesten Version -- nur diese ist im Exe-Verzeichnis vorhanden

    -   Druckertreiber initialisieren via Interop via AmyUni.net

-   cdinft.dll

-   PDF- Aufbauen geht über Dll- Import -\> prüfen, welche Version im
    Exe- Verzeichnis --\> dynamischer DLL- Import -\> solle lt. unserer
    Erinnerung schon so erfolgen ( PRÜFEN im Source

-   Dictionarry mit AmyUni-Version (z.B. 4.5) als Key und einer Klasse
    mit Lizenzname + LizenzKey als ZielobjektTyp V

P:`\InstallVorlagen`{=tex}`\Exec `{=tex}Verzeichnis beim
Kunden`\AmyUni6`{=tex} Siehe A35257

## Communication Daemon

-   Zuständig ab 1.10.2014: hmp, kj
-   Im Team- System unter SonstigeTools`\PCS `{=tex}Communication Daemon
-   Siehe in \`Installation beim Kunden.doc´ PCS Communication Daemon

## Firewall- Regeln für Software (=uns)

-   siehe Firewall-Regeln-Für-Software=uns.xlsx

## Fixe IP-Adressen für Software (=uns)

-   wenn zum Testen von Geräten fixe IP- Adressen benötigt werden haben
    wir dafür einen Range
-   siehe FixeIpAdressen-Für-Software=uns.xlsx

## Jet- Scan- Daemon ...

-   Hier gibt es keinen dezidierten Ansprechpartner - Wissen ist
    angeblich vorhanden bei:
    -   ap
    -   akoe
-   Programme im Teamsystem + PB

## Office- Integration

-   Zuständig ab 1.10.2014: hw
-   Entwicklungsstand: siehe pfu_oi
-   Anmerkungen:
-   die Controls sind hochgradig von cst_TabPage abgeleitet
-   eigentlich sollten die Controls in der Klassenreferenz beschrieben
    werden

## Management Console

-   Gerald hat sie im Einsatz
-   Wenn Interesse daran besteht, wird sie dokumentiert

## Mobile Device Library

-   Stand 6.10.2014: akoe entwickelt damit Adeg Vertreterlösung
-   Vor weitere Verwendung bitte Rücksprache mit hmp

## Pcs.EntityFramework.Model

-   Zuständig: hmp
-   wird von .Net- Programmen/Libraries im TC- Umfeld dazu verwendet,
    auf die pfu- Tabellen u.s.w. der Tradecontrol- Datenbank zuzugreifen
-   dies erfolgt mittels Entity- Framework
-   es ist vorgesehen, dass für ein Projekt eine eigene
    Pcs.EntityFramework.Model- Assembly erstellt wird
-   diese muss immer alle Entities der Basis- Assembly enthalten
    (Ableiten ist leider nicht möglich)
-   durch diese wird dann die Basis- Assembly ersetzt
-   Der Namespace der eigenen Assembly muss gleich jenem der
    Basisassembly sein
-   die Organisation dieser Projekt- Assemblies muss noch geplant
    werden, bevor wir dies verwenden

## Pcs.Interop

-   Zuständig ab 1.10.2014: hmp
-   es gibt eine COM- Visible .net- Assembly namens Pcs.Interop.dll
-   für deren Klassen gibt es Proxy- Klassen in der pfu_sysfun.pbl bzw.
    bei neueren Klassen in der pfu_fun.pbl - diese sind in der
    Programmiererdoku nicht im Detail beschrieben, wenn sie die .net-
    Klassen 1:1 durchschleifen
-   Im Team- System unter Bibliotheken`\PCS `{=tex}Interop
-   Hier unter PCS.Interop befindet sich die Dokumentation:
    \`Installation und Konfiguration.docx´

## Pcs.Interop.UI.Controls

-   Zuständig: hmp
-   es gibt eine COM- Visible .net- Assembly namens
    Pcs.Interop.UI.Controls.dll
-   Hier befinden sich vom Powerbuilder zu verwendende OLE- Controls,
    die von der pfu_fun verwendet werden
-   Im Team- System unter Biblitheken`\PCS `{=tex}Interop UI Controls
-   ACHTUNG: Für die Entwicklung der Pcs.Interop.Ui.Controls muss das
    "Microsoft InteropForms Toolkit 2.1" installiert werden: Siehe
    P:`\InstallVorlagen`{=tex}`\Installation `{=tex}Entwicklungsrechner.docx

## Service Controller

-   Zuständig ab 1.10.2014: hmp, kj
-   Im Team- System unter SonstigeTools`\PCS `{=tex}Communication Daemon
-   Siehe in \`Installation beim Kunden.doc´ PCS Service Controller
-   Übernimmt seit A12732 auch die Aufgaben der Kontroll- Applikation
    des TCP- Reques Servers

## Tradecontrol TCP- Request Server

-   Zuständig ab 1.10.2014: hmp, kj
-   Siehe TCP- Request Server

## Tradecontrol WCF- Request Server

-   Zuständig ab 1.10.2014: hmp, kj
-   Siehe WCF- Request Server

## Visual Studio Tools

-   Hier sind Verzeichnisse, in denen man Tools aus dem Bereich des
    VisualStudiofinden kann:
    -   c:`\Program `{=tex}Files (x86)`\Microsoft `{=tex}Visual Studio
        10.0`\VSTSDB`{=tex}`\Deploy`{=tex}
    -   c:`\Program `{=tex}Files (x86)`\Microsoft `{=tex}Visual Studio
        10.0`\Common7`{=tex}`\IDE`{=tex}\
    -   c:`\Program `{=tex}Files (x86)`\Microsoft `{=tex}Visual Studio
        10.0`\VC`{=tex}`\BIN`{=tex}
    -   c:`\Program `{=tex}Files (x86)`\Microsoft `{=tex}Visual Studio
        10.0`\Common7`{=tex}`\Tools`{=tex}
    -   C:`\Windows`{=tex}`\Microsoft`{=tex}.NET`\Framework`{=tex}`\v4`{=tex}.0.30319
    -   C:`\Windows`{=tex}`\Microsoft`{=tex}.NET`\Framework`{=tex}`\v3`{=tex}.5
    -   c:`\Program `{=tex}Files (x86)`\Microsoft `{=tex}Visual Studio
        10.0`\VC`{=tex}`\VCPackages`{=tex}
    -   c:`\Program `{=tex}Files
        (x86)`\Microsoft `{=tex}SDKs`\Windows`{=tex}`\v7`{=tex}.0A`\bin`{=tex}
-   hier befinden sich
    -   gacutil
    -   mt, signtool, oleview, mc, lc, SetReg für das .net Framework 3.5
    -   c:`\Program `{=tex}Files
        (x86)`\Microsoft `{=tex}SDKs`\Windows`{=tex}`\v7`{=tex}.0A`\bin`{=tex}`\NETFX 4.0`{=tex}
        Tools
-   wie das vorige, nur für 4.0
-   regasm:
    -   C:`\Windows`{=tex}`\Microsoft`{=tex}.NET`\Framework`{=tex}`\v4`{=tex}.0.30319`\RegAsm`{=tex}.exe
    -   C:`\Windows`{=tex}`\Microsoft`{=tex}.NET`\Framework`{=tex}`\v2`{=tex}.0.50727`\RegAsm`{=tex}.exe

## Klassenreferenz

## cst_Alist (sys)

-   Liste mit Any- Werten zum Übergeben von Argumenten an z.B. ein
    mittels w_ApplObj.wf_open geöffnetes Window
-   es handelt sich um eine sogenannte "doppelt verkettete Liste"
-   jedes Listenelement hat einen Any- Wert
-   es können Listenelemente hinzugefügt, gelöscht und ausgelesen werden
-   es gibt immer ein aktuelles Listenelement

### Functions

#### uf_Add

##### Argumente

-   aa_wert
-   as_pos '\|\<' ... zu Beginn '\>\|' ... am Ende '\>' .... nach der
    aktuellen Position '\<' .... vor der aktuellen Position

##### Rückgabewert

-   Powerobject
-   Verweis auf eingefügtes Listenelement
-   dient als Argument für eine der Funktionen uf_SetPos, uf_GetObj
-   Bsp.: . cst_Alist luo_Alist; powerobject luo_pos; string ls_wert .
    luo_pos = luo_Alist.uf_add ("hallo","\>\|" ) // fügt "hallo" als
    letztes Listenelement ein . ... // das eingefügte Element wird von
    anderem // Programmteil verändert . uf_GetObj ( ls_wert, luo_pos )
    // der Wert des zuvor eingefügten Elements wird // wird wieder
    ausgelesen

##### Beschreibung

-   fügt aa_wert an der as_pos entsprechenden Position in die Liste ein
    und setzt die aktuelle Position der Liste auf das neu eingefügte
    Element (also dieses mit aa_wert)

#### uf_Del

##### Argumente

##### Rückgabewert

-   (None)

##### Beschreibung

-   löscht das aktuelle Element der Liste

#### uf_DelAll

##### Argumente

-   ab_destroy

##### Rückgabewert

-   (None)

##### Beschreibung

-   Löscht alle Elemente der Liste
-   wenn ab_destroy = true, wird die Liste selbst destroyed

#### uf_GetObj

##### Argumente

-   aa\_ , ab\_, ai\_ bzw. as\_
-   reference, für 4 Datentypen vorhanden
-   Wert des Listenelements
-   das aktuelle Listenelement wird ausgelesen
-   ACHTUNG: es muss einer der obigen Datentypen übergeben werden - ggf.
    muss zunächst in eine Any- Variable ausgelesen werden und deren Wert
    dann der eigentlichen Zielvariablen zugewiesen werden
-   es sind zusätzliche Versionen denkbar o \>
    -   apo_pos
-   Verweis auf das aktuelle Listen- Element nach dem Positionieren \>
    -   as_pos '\^' .... aktuelle Position '\|\<' ... zu Beginn '\>\|'
        ... am Ende '\>' .... nach der aktuellen Position '\<' .... vor
        der aktuellen Position

##### Rückgabewert

-   boolean: das Auslesen des Listenelements hat funktioniert

##### Beschreibung

-   Auslesen eines Listenelements abhängig von den Argumenten
-   das ausgelesene Element wird das neue aktuelle Element

#### uf_len

##### Argumente

##### Rückgabewert

-   long
-   Anzahl der Elemente in der Liste

##### Beschreibung

#### uf_GetPos

##### Argumente

##### Rückgabewert

-   Verweis auf aktuelles Listenelement
-   siehe Rückgabewert von uf_Add

##### Beschreibung

-   kann später als Argument für uf_SetPos, uf_GetObj verwendet werden

#### uf_SetPos

##### Argumente

> -   apo_pos
>
> -   Verweis auf das aktuelle Listen- Element nach dem Positionieren
>
> -   as_pos '\^' .... aktuelle Position '\|\<' ... zu Beginn '\>\|' ...
>     am Ende '\>' .... nach der aktuellen Position '\<' .... vor der
>     aktuellen Position

##### Rückgabewert

-   Verweis auf aktuelles Listenelement
-   siehe Rückgabewert von uf_Add

##### Beschreibung

-   setzt die aktuelle Position in der Liste lt. ai_pos bzw. apo_pos

## weitere

die Funktionen zum Markieren von Listenelementen und zur Positionierung
auf ein markiertes Element sind noch nicht dokumentiert, wenn jemand so
etwas \## braucht, bitte melden

## cst_ApiFun (sys)

-   Eine Sammlung von Windows API Funktionen.

### Functions

#### uf_Browse4Folder

##### Argumente

-   (None)

##### Rückgabewert

-   String
-   Der vom Anwender ausgewählte Ordner

##### Beschreibung

-   Die Funktion kann verwendet werden um vom Anwender einen Ordner
    auswählen zu lassen

#### uf_GetEnvVar

##### Argumente

-   as_Variable
-   Variablenname des Betriebssystems
    -   as_Value
-   by Reference
-   Wert der Variable

##### Rückgabewert

-   boolean

##### Beschreibung

-   Die Funktion ermittelt den Wert einer Umgebungsvariable sofern
    belegt.

#### uf_GetExe

##### Argumente

-   as_Directory
-   by Reference
-   der Verzeichnispfad der .exe des laufenden Programms
    -   as_FileName
-   by Reference
-   der Filename ohne Verzeichnispfad der .exe des laufenden Programms
    -   as_error
-   by Reference
-   ggf. Fehlerbeschreibung

##### Rückgabewert

-   boolean
-   true, wenn ok, sonst false
-   bei false wird as_error belegt

##### Beschreibung

-   Die Funktion liefert Pfad+Filenamen der exe des laufenden Programms

#### uf_RemoveTitle

##### Argumente

-   aw\_
-   Typ = Window
-   Das Window, dessen Title eliminiert werden soll

##### Rückgabewert

-   none

##### Beschreibung

-   entfernt den Titel des Windows

## cst_ApplEnv

-   das ist das "Environment"
-   Alle einem Window zugeordneten CstApplEnv müssen über uf_child
    erzeugt werden! (nie über create)
-   cst_applEnv ohne Window haben nicht die volle Funktionalität!!!

### Functions

#### uf_AddAot

##### Argumente

## o as_idname

-   Identifyer- Name des ApplikationsobjektTyps {=AOTI} \## o as_title

-   Bezeichnung für den Windowtitle \## o as_titledisp

-   1 oder 2 Buchstaben mit jeweils folgender Bedeutung: "m" Matchcode
    im Title anzeigen, "k" Key anzeigen \## o as_kuerzel

-   Kürzel für das ApplObj für verschiedene Anzeigen \## o as_command

-   freier Kommandostring in der Form "Kommando Leerzeichen Kommando
    ..."

-   Kommando darf kein Leerzeichen enthalten

-   kann leer sein oder 1 bis n Kommandos enthalten

-   folgende Kommandos werden verarbeitet:

    -   "spoolin"

-   es werden die Environment- Objekte für das Spoolin- Fenster
    hinzugefügt

-   muss bei allen Batchprogrammen, die über w_spoolin gestartet werden
    können, vorhanden sein \## o as_tabname

-   Tabellenname \## o as_pkeycolname

    -   Primarykey- Column deren Eingabe den Lookup auslöst {=AOTPKC}

-   Ist im Allgemeinen jene Column, welche nicht AOTPKC eines anderen
    AOTs ist.

-   Gibt es keine solche Column, ist jene AOTPKC zu wählen, welche in
    DWs zuletzt eingegeben wird.

-   ab pfu_fun040616 gilt:

-   in diesem Fall ist "" zu übergeben

-   ist as_pkeycolname gleich dem PKeycolumnNamen eines AEOs, das
    Keybestandteil ist, wir "" angenommen und das AOT hat keine eigene
    PKeyColumn

-   die uf_AddAot- Aufrufe für die Keybestandteil- AEOs müssen vorher
    erfolgen \## o as_pkeycolformat

-   Formatstring zum Anzeigen von Primarykey- Column \## o as_mccolname

-   Matchcode- Column

    -   ab_window

-   es gibt ein Window für das ApplObj

    -   atr\_

-   kann weggelassen werden

-   muß angegeben werden, wenn Daten des AOTs über andere DB- Connection
    gelesen werden

-   wird bei w_JobObj nicht ausgewertet (Window hat kein
    Transaktionsobjekt, dw_JobObj verwendet im TransObject standardmäßig
    sqlca)

    -   ai_LookupBufferrows

-   für den Lookup gibt es für jedes AOT genau einen DS in der
    Applikation

-   dieser ist jeweils nach dem Start der Applikation leer

-   wenn ai_LookupBufferrows \> 0 ist:

-   wird ein Lookup durchgeführt, verbleibt die Ergebnis- Row im DS

-   wird erneut ein Lookup durchgeführt und , wird zunächst versucht,
    die entsprechende Row im DS zu suchen, bevor ein Retrieve erfolgt

-   der Retrieve erfolgt immer aditiv ( die bereits im DS befindlichen
    Rows werden nicht gelöscht

-   befinden sich allerdings vor dem Retrieve bereits
    ai_LookupBufferrows im DS, wird die als erstes retrievte Row vor dem
    Retrieve gelöscht ( im DS befinden sich daher maximal
    ai_LookupBufferrows Rows

-   siehe auch uf_AddAotEo Parameter ab_LookupAktuell

-   siehe auch uf_SetDsLookupTimeRetrieve

-   kann weggelassen werden, dann wird der mittels
    uf_DefLookupBufferRows gesetzte Standardwert angenommen, ist
    uf_DefLookupBufferRows nicht aufgerufen worden, wird 0 angenommen

##### Rückgabewert

-   (None)

##### Beschreibung

-   Definition eines AOTs
-   AD Job- AOTs:
-   die MFA- Maske wird genauso wie bei einem Nicht- Job\_ AOT lt.
    as_tabname ermittelt - Die Maske hat allerdings nur einen Einfluss
    beim Spoolin- Fenster siehe auch uf_new

#### uf_AddAotEo

##### Argumente

-   as_idname
-   AOT-Name des AOTEOs
    -   ab_key
-   AOTPKC des AOTEO ist eine PKey- Column des mittels uf_addaot
    definierten AOTs
    -   ab_const
-   AOTPKC des AOTEOs kann im mittels uf_addaot definierten AOT konstant
    sein
-   bei mfa- Feldern ist ab_const automatisch true - der übergebene Wert
    wird ignoriert
    -   ab_ConstSearch
-   wird vom Window des AOTs mittels Search ein Window aufgerufen wird
    standardmäßig die AOTPKC als Konstante in das aufgerufene Window
    übergeben
-   siehe uf_SetCallConst
-   siehe dw_ApplOb.CallConstSearch
    -   as_titledisp
-   1 oder 2 Buchstaben mit jeweils folgender Bedeutung: "m" Matchcode
    im Title anzeigen, "k" Key anzeigen
    -   as_colpraefix
-   Column- Präfix: Columns von Feldern des AOTEOs haben im mittels
    uf_addaot definierten AOT den Namen wie im AOT des AOTEOs plus
    diesem Präfix
-   Bsp.: "ein:\_" für "ein_auf" ... Eingangsauftrag in der
    Auftragsposition
    -   as_kuerzelpraefix
-   Präfix für das Kürzel des AOTEOs
    -   as_titlepostfix
-   Postfix für für die Bezeichnung des AOTEOs
    -   aa_nolookupvalue
-   Null ( lookup soll immer erfolgen
-   gf_c('n') ( lookup soll nie erfolgen
-   gf_c('w') ( im Window- Event NoLookup wird ermittelt, ob Lookup
    erfolgt
-   sonst ( hat AOTPKC des AOTEOs diesen Wert, erfolgt kein lookup
-   Soll kein Lookup für den Leerstring erfolgen, ist unbedingt ""
    anzugeben (auf keinen Fall " ")
-   hat das AOT des AEOs keine PKey- Column (Typ artik_lag) wird der
    Wert ignoriert
    -   ab_SubPraefixMussGleich
-   true ( Weglaßregel bei der AOE- Abblidung wird nicht angewandt
-   kann weggelassen werden -- dann wird false angenommen
-   gilt nicht für AEOs, die im AOT lt. as_idname Keybestandteil sind
-   hat keine Auswirkung auf das Konstant-setzen beim Search (siehe ggf.
    dw_ApplObj.event CallConstSearch)
    -   ab_LookupAktuell
-   siehe uf_AddAot Parameter ai_LookupBufferrows
-   true ( die Werte beim Lookup müssen immer aktuell sein
-   dies gilt z.B. für den Artikelstamm in der Auftragsposition: die
    Verfügbarkeitsdaten müssen aktuell sein
-   false ( die Werte beim Lookup müssen nicht immer aktuell sein
-   dies gilt z.B. für den Firmenstamm in der Auftragsposition: dieser
    wird im Allgemeinen nicht geändert ( die Daten müssen nicht immer
    wieder neu aus der Datenbank gelesen werden
-   dies gilt aber z.B. auch für den Artikelstamm im Artikelstamm: hier
    sind keine Bewegungsdaten relevant
-   kann weggelassen werden -- dann wird true angenommen

##### Rückgabewert

-   (None)

##### Beschreibung

-   defineirt ein AEO zum AOT, welches zuletzt mittels uf_AddAot
    definiert wurde
-   ist zum Zeitpunkt des Funktionsaufrufs für das AOT lt. as_idname
    noch kein uf_AddAot erfolgt, muss statt uf_AddAotEo die Funktion
    uf_AddAotEoF verwendet werden - uf_AddAotEoF darf allerdings nur in
    diesem Fall verwendet werden! (Die bisherigen Nachträge gibt es
    nicht mehr.)

#### uf_AddAotEoF

##### Argumente

-   wie bei uf_AddAotEo

##### Beschreibung

-   siehe uf_AddAotEo

#### uf_AddAotMfaPraefix

##### Argumente

-   as_praefix
-   as_MaskAot
-   ID- Name des AOTs dessen MFA- Maske für MFA- Felder mit dem Praefix
    lt. as_praefix gilt

##### Beschreibung

-   bewirkt, dass für MFA- Felder mit Präfix trotzdem die MFA- Logik
    angewandt wird
-   allerdings das Konstantsetzen lt. Anmeldungs- MFA erfolgt nicht
-   Bsp.:
-   im Artikel gibt es:
    -   fa_nr
    -   fil_nr
    -   abt_nr
    -   LtzAuf_auf_nr
    -   LtzAuf_fa_nr
    -   LtzAuf \_fil_nr
    -   LtzAuf \_abt_nr
-   Artikel hat z.B. MFA- Maske (1,0,0)
-   Auftrag hat z.B. MFA- Maske (1,1,1)
-   LtzAuf\_\* sind die Keyfelder des Letzen Auftrags, in dem Dieser
    Artikel verwendet worden ist
-   fa_nr - abt_nr sind dann z.B. (2,0,0)
-   LtzAuf_fa_nr - LtzAuf_fil_nr sind dann z.B. (2,1,3)
-   für LtzAuf_fa_nr - LtzAuf_fil_nr soll die MFA- Logik gelten, wobei
    nicht die MFA- Maske von Artikel sondern die MFA- Maske von auf zum
    Tragen kommen soll
    -   as_KuerzelPraefix
    -   as_TitlePostfix
    -   aa_NoLookupValue
-   dieser Wert wird nicht gelookeuped
    -   ab_SubPraefixMussGleich
-   true schaltet die Weglassregel aus

#### uf_AddCommand

##### Argumente

-   as_command
-   Kommandowort bzw. Argumentname, wenn ein Argument- Kommando
    hinzugefügt wird
    -   as_wert
-   nur bei Argument- Kommando anzugeben
-   Argumentwert

##### Rückgabewert

-   (None)

##### Beschreibung

-   Siehe dazu: Begriffe.Kommandostring des Environments

#### uf_AddWindowMap

##### Argumente

-   as_RequestWindow
-   Windowname welcher wf_open als jener Parameter, welcher das zu
    öffnende Window definiert, übergeben wird
    -   as_OpenWindow
-   Window, welches abhängig davon geöffnet werden soll.

##### Rückgabewert

-   (None)

##### Beschreibung

-   wird in gf_InitApplEnv() aufgerufen
-   Ist anzuwenden, wenn ein Window in einer individuellen Version einer
    Applikation durch ein anderes, wahrscheinlich von ihm abgeleitetes
    Window ersetzt werden soll.
-   ACHTUNG: wird uf_AddWindowMap für ein window mehrmals aufgerufen,
    wirkt nur der erste Aufruf!

#### uf_AddRelease

##### Argumente

-   as_bezeichnung
-   Programmteil für den eine Release bekannt gegeben wird
-   für die Applikation muss hier "Applikation" stehen
    -   as_release
-   sollte für die Applikation in der Form "0017 24.12.2010" stehen
-   0017 bedeutet, dass die numerische Release- Nummer = 17 ist
-   ACHTUNG: die führenden Nullen sind notwendig, sodass bei der
    alphanumerischen Sortierung eine numerisch richtige Reihenfolge
    gewährleistet ist

##### Rückgabewert

-   (None)

##### Beschreibung

-   gibt den Release für einen Bestandteil der Applikation bekannt
-   alle Einträge werden vom Info- Menü aus angezeigt
-   der Aufruf mit as_bezeichnung = "Applikation"
-   steuert , ob die pfu_aot- Tabellen neu aufgebaut werden ( bei jedem
    Programmstand muss der Funktionsaufruf aktuallisiert werden
    (Release-Nummer inkrementieren und Datum aktuallisieren)
-   wird typischerweise in gf_InitApplEnv aufgerufen

#### uf_AnmeldApplpers

##### Argumente

-   ai_anmeldung
-   kann weggelassen werden, dann wird 0 angenommen
-   bei 0 wird die Anmeldung des aktuellen AOs herangezogen

##### Rückgabewert

-   string
-   appl_pers_cd der Anmeldung

##### Beschreibung

-   ist der Sachbearbeiter für die Applikation - also meistens eine
    Person zur Adresse
-   siehe auch uf_AnmeldUsr

#### uf_AnmeldApplPersMessageBody

##### Argumente

-   ai_anmeldung
-   kann weggelassen werden, dann wird 0 angenommen
-   bei 0 wird die Anmeldung des aktuellen AOs herangezogen

##### Rückgabewert

-   string
-   pfu_applpers.def_ap_messagebody der Anmeldung

##### Beschreibung

-   ist der MessageBody lt. Sachbearbeiter für die Applikation

#### uf_AnmeldMfa

##### Argumente

-   ai_anmeldung
-   kann weggelassen werden, dann wird 0 angenommen
-   wenn ai_anmeldung weggelassen wird, ist auch as_MaskAot wegzulassen
-   bei 0 wird die Anmeldung des aktuellen AOs herangezogen
    -   as_MaskAot
-   readonly
-   kann weggelassen werden, dann wird "" angenommem
-   wenn as_MaskAot weggelassen wird, ist auch ai_anmeldung wegzulassen
-   bei "" wird das aktuelle Aot angenommem
-   wenn weggelassen, ist auch ai_anmeldung wegzulassen
-   bei "-" wird nicht maskiert
    -   ai_mfa1_nr
-   reference
    -   ai_mfa2_nr
-   reference
    -   ai_mfa3_nr
-   reference

##### Rückgabewert

-   (none)

##### Beschreibung

-   befüllt as_mfa?\_nr mit den entsprechenden mfa- Werten maskiert
    durch die mfa- Maske lt. as_MaskAot

#### uf_AnmeldMfaTrifft

##### Argumente

-   ai_mfa1_nr
-   ai_mfa2_nr
-   ai_mfa3_nr

##### Rückgabewert

-   boolean

##### Beschreibung

-   prüft, ob die Anmeldungs- MFA der aktuellen Anmeldung die übergebene
    MFA trifft, also ob die übergebene MFA unter der Anmeldungs- MFA
    erlaubt ist

#### uf_AnmeldUsr

##### Argumente

-   ai_anmeldung
-   kann weggelassen werden, dann wird 0 angenommen
-   bei 0 wird die Anmeldung des aktuellen AOs herangezogen

##### Rückgabewert

-   string
-   usr_cd der Anmeldung

##### Beschreibung

-   ist der User, von dem die Berechtigungen ausgehen und unter dem
    Einstellungen gespeichert werden
-   siehe auch uf_AnmeldApplpers

#### uf_AoMfa

##### Argumente

-   as_MaskAot
-   readonly
-   kann weggelassen werden, dann wird "" angenommem
-   bei "" wird das aktuelle Aot angenommem
-   bei "-" wird nicht maskiert
    -   ai_mfa1_nr
-   reference
    -   ai_mfa2_nr
-   reference
    -   ai_mfa3_nr
-   reference

##### Rückgabewert

-   (none)

##### Beschreibung

-   befüllt as_mfa?\_nr mit den entsprechenden mfa- Werten des AOs
    maskiert durch die mfa- Maske lt. as_MaskAot
-   siehe uf_MaskMfa
-   ACHTUNG: darf nur für ein cst_ApplEnv mit AOT (( von w_ApplObj
    abgeleitet) verwendet werden

#### uf_AnmeldSprache

##### Argumente

-   ai_anmeldung
-   kann weggelassen werden, dann wird 0 angenommen
-   bei 0 wird die Anmeldung des aktuellen AOs herangezogen

##### Rückgabewert

-   string
-   sprache_cd der Anmeldung

##### Beschreibung

-   liefert die Sprache der Anmeldung

#### uf_ApplDiagOutput

##### Argumente

-   apo_wo
-   Powerobject
-   das Objekt, in dem die Aktivität, für die die Diagnose ausgegeben
    wird, stattfindet
-   der Klassenname dieses Objektes wird ausgegeben
-   hier wird typischerweise this übergeben
    -   as_output
-   der Diagnosetext
-   sollte den Namen des Events bzw. der Funktion und die Position dort
    enthalten

##### Rückgabewert

-   (None)

##### Beschreibung

-   Gibt eine Diagnosemeldung über cst_InteractiveDiag aus, wenn die
    Applikation im Applikationsdiagnosemodus ist
-   In der pfu_fun sind viele uf_ApplDiagOutput- Aufrufe enthalten ( im
    Applikationsdiagnosemodus produzieren diese Diagnosemeldungen im
    Diagnosefenster von cst_InteractiveDiag
-   Die Diagnoseausgaben sind hauptsächlich im Zusammenhang mit
    SetPresentation oft sehr hilfreich.
-   uf_ApplDiagOutput steht seit A21049 in dieser Form zur Verfügung

#### uf_ApplParms

##### Argumente

-   apo_ApplParms
-   das Userobjekt lt. Beschreibung das dem System bekanntgegben wird

##### Rückgabewert

-   (None) \>

##### Argumente

##### Rückgabewert

-   Powerobject
-   das Userobjekt lt. Beschreibung das dem System mittels der vorigen
    Version von uf_ApplParms bekanntgegegben worden ist

##### Beschreibung

-   Es kann damit im Environment einen Verweis auf ein Userobjekt
    eintragen werden, sodaß dann alle Scripts der Windows u.s.w. des
    Projekts auf genau diese Instanz des Userobjekts zugreifen können
-   das Instanzieren des Userobjekts und der uf_ApplParms- Aufruf zur
    Bekanntgabe dieses wird typischerweise in der Funktion
    gf_InitApplEnv durchgeführt
-   immer wenn ein Zugriff auf irgend eine Instanz von cst_ApplEnv
    (iuo_ae) besteht, kann dann mittels
    uf_ApplParms().FunktionalitätVonUserobjekt eine Funktionalität des
    Userobjekts angesprochen werden
-   ist nur für Projekt- spezifische Klassen, von denen abgeleitet wird,
    zu verwenden, diese sollten dann direkten Zugriff auf das Userobjekt
    bieten
-   Bsp.: Tradecontrol: w_ApplObj_tc.wf_TradeconParams()

#### uf_CheckLicense

##### Argumente

##### Rückgabewert

-   (None)

##### Beschreibung

-   Liest die Anzahl der Lizenzen für die Applikation aus dem Kennsatz
    aus und überprüft, ob der Lizensekey korrekt ist (dieser ist
    abhängig vom Applikationsnamen und der Anzahl Lizenzen)
-   Ist er korrekt, wird die Anzahl Lizenzen in cst_ApplEnv eingetragen
-   Ist er nicht korrekt, wird abgebrochen
-   muss im Open- Event- Script der Applikation vor dem Öffnen des Main-
    Windows aufgerufen werden
-   siehe Datenbankbeschreibung pfu_kennsatz
-   Der Licensekey kann folgendermaßen ermittelt werden: . man trägt im
    pfu_kennsatz (bei uns) die gewünschte Anzahl der Lizenzen ein . man
    Setzt in gf_CheckLicense einen Breakepoint auf die Zeile if
    ls_IstLiKey = string(ldbl_LiKey) then . Man startet im Debugger die
    Applikation . man kopiert sich den Inhalt der Variable ldbl_LiKey .
    man trägt diesen Wert bei uns im pfu_kennsatz ein

. man trägt diesen Wert beim Kunden im pfu_kennsatz ein . ändert sich
die Anzahl der Lizenzen, ist diese Prozedur zu wiederholen - ACHTUNG: es
darf nie eine größere Anzahl der Lizenzen als die gekaufte Anzahl beim
Kunden eingetragen werden (Der Kunde hat ja sonst den Key für eine zu
große Anzahl) - Falls dies doch versehentlich passiert ist, muss der
Applikationsname geändert werden.

#### uf_CliHostName

##### Argumente

##### Rückgabewert

-   string
-   Der Host- Name des Systems, auf dem der Anwender das Programm
    bedient - dies ist bei einer Terminalserverlösung der Terminalclient

#### uf_ColIsConst

##### Argumente

-   as_ColName
-   Key- Column des AEOs, für das zurückgeliefert wird, ob es konstant
    -   aa_Wert
-   kann weggelasen werden
-   Key- Wert des konstanten AEO's, wenn true rerurned wird

##### Rückgabewert

-   boolean
-   siehe as_ColName

#### uf_ConstMfa

##### Argumente

-   3 Argumente wobei X für eine der Zahlen 1, 2, 3 steht

-   reference - nur als Rückgabeparameter gedacht

-   0 ( der Rückgabewert der Funktion ist \< X

-   0 ( der Rückgabewert der Funktion ist \>= X

-   ai_mfa1_nr

-   ai_mfa2_nr

-   ai_mfa3_nr

##### Rückgabewert

-   siehe Beschreibung

##### Beschreibung

-   geht die MFA- Felder von 1 bis 3 durch und liefert die Nummer des
    letzten MFA- Feldes (0-3), bei dem eine der folgenden Bedingungen
    erfüllt ist: \> das Feld ist in der Anmeldungs- MFA \<\> 0 und kann
    konstant sein \> das Feld ist konstant und \<\> 0 \> das Feld wäre
    konstant und \<\> 0, wenn die MFA- Maske für das aktuelle AOT für
    das Feld nicht 0 wäre
-   Kann nie eine Fragen mit Ja beantwortet werden, wird 0 geliefert
-   siehe uf_AddAotEo Argument ab_const

#### uf_DefLookupBufferRows

##### Argumente

-   ai_LookupBufferRows

##### Rückgabewert

-   (none)

##### Beschreibung

-   siehe uf_AddAot Parameter ai_LookupBufferrows

#### uf_DefineAufrufConst

##### Argumente

-   as_PraefixIdName
-   z.B. "ein_auf"
    -   aa_wert
-   der Wert auf den konstant gesetzt werden soll

##### Rückgabewert

-   (none)

##### Beschreibung

-   wird vor wf_open aufgerufen
-   bewirkt, dass im aufgerufen Window der Pkey des AEO's lt.
    as_PraefixIdName konstant aa_wert ist
-   siehe auch uf_SetCallConst

#### uf_DefineMfaNamen

##### Argumente

-   mfa1_name
-   AOT der 1. mfa-Column (zB: "fa" für fa_nr)
-   siehe PfuFunOrg/Begriffe/mfa
-   wird für mfa1_name leer übergeben, wird das 1. mfa- Feld in der
    Applikation nicht verwendet
-   wird für mfa1_name leer übergeben, muss mfa2_name auch leer sein
    -   mfa2_name
-   sinngemäß wie mfa1_name
    -   mfa3_name
-   sinngemäß wie mfa1_name

##### Rückgabewert

-   (none)

##### Beschreibung

-   gibt der Applikation bekannt, welche Columns als mfa- Columns
    herangezogen werden
-   siehe

#### uf_DefineTr

##### Argumente

-   atr\_
-   Transaction

##### Rückgabewert

-   Transaction- Nummer

##### Beschreibung

-   ordnet dem Transactionobject lt. atr\_ eine Tranactionnummer zu
-   sqlca braucht nicht extra definiert zu werden und hat automatisch
    die Nummer 1
-   mit jedem weiteren Aufruf von uf_DefineTr wird die Nummer um 1
    erhöht
-   die Aufrufe sind in der Funktion gf_InitApplEnv zu platzieren
-   mittels der Funktion uf_GetTr kann dann über die Transactionnummer
    die zugehörige Transaction ermittelt werden
-   Dieser Mechanismus ist immer dann sinnvoll, wenn die Transaction
    frei wählbar sein muss und wurde für die Batch- SQL- Funktionalität
    eingeführt

#### uf_DelCommand

##### Argumente

-   as_command
-   Argument- Kommando- Name

##### Rückgabewert

-   (None)

##### Beschreibung

-   Löscht Kommando aus dem Kommandostring.
-   Siehe dazu: Begriffe.Kommandostring des Environments

#### uf_DwoExpr

##### Argumente

-   as_expr
-   DWO- ist eine Expression
-   eine beliebige Expression, wie sie in einer DWO- Computed- Column
    eingetragen werden kann
-   allerdings darf es natürlich keinen Bezug zu anderen Elementen des
    DWOs geben

##### Rückgabewert

-   any
-   Wert der Expression lt. as_expr, wenn diese gültig ist
-   sonst wird "Ausdruck ungültig" geliefert

##### Beschreibung

-   siehe Argumente + Rückgabewert
-   folgende Anwendungsmöglichkeit:
-   es gibt eine alphanumerisches Eingabefeld für eine Zahl
-   der Anwender kann z.B. "(12+25*3+17)*3" eingeben
-   die Zahl ist dann 312

#### uf_Error

##### Argumente

-   apo_wo
-   kann weggelassen werden
-   das Objekt, in dem der Fehler auftritt - dessen Name wird in der
    Fehlermeldung ausgegeben
    -   as_wo
-   wo (im Objekt) ist der Fehler aufgetreten (hier isr hochgradig der
    Funktions bzw. Event- Name anzugeben)
    -   as_errortext
-   Beschreibung des Fehlers

##### Rückgabewert

-   (None)

##### Beschreibung

-   bringt eine Fehlermeldung

#### uf_ExportKeyToParent

##### Argumente

##### Rückgabewert

-   boolean
-   = Erfolg

##### Beschreibung

-   Schreibt alle Key- Werte des aktuellen AEO's ins aktuelle DW des
    Parent w_ApplObj's
-   bringt Fehlermeldungen, wenn nicht OK

#### uf_GetCommandWert

##### Argumente

-   as_command
-   Argumentname

##### Rückgabewert

-   string
-   Argumentwert

##### Beschreibung

-   Siehe dazu: Begriffe.Kommandostring des Environments

#### uf_GetIAeo

##### Argumente

-   as_praefix
-   Praefix des AEOs wie z.B. "ein\_" für Eingangsauftrag
    -   as_IdName
-   Name des AOTs des AEOs wie z.B. "auftrag"

##### Rückgabewert

-   integer
-   interne Nummer des AEOs im AOT

##### Beschreibung

-   Wird als Rückgabewert für die Events
    DwApplObj.\[IAeoSearch\|IaeoShow\] benötigt.

#### uf_GetInstCd

##### Argumente

## keine

##### Rückgabewert

-   string
    -   Code der aktuellen Instanz

#### uf_GetTr

##### Argumente

-   ai_tr
-   Transactionnummer

##### Rückgabewert

-   Transactionobject

##### Beschreibung

-   siehe uf_DefineTr

#### uf_HostName

##### Argumente

##### Rückgabewert

-   string
-   Der Host- Name des Systems, auf dem das Programm läuft

#### uf_ImHaus

##### Argumente

##### Rückgabewert

-   boolean
-   liefert true, wenn in der Registry
    HKEY_LOCAL_MACHINE`\Software`{=tex}`\Pfundner`{=tex}`\ImHaus=1`{=tex}

#### uf_InBatch

##### Argumente

##### Rückgabewert

-   boolean
-   liefert true, wenn System im Batch- Modus ist

#### uf_InCommand

##### Argumente

-   as_command
-   Kommandowort

##### Rückgabewert

-   boolean
-   liefert true, wenn Kommandowort im Kommandostring des Environments
    enthalten ist

##### Beschreibung

-   Siehe dazu: Begriffe.Kommandostring des Environments

#### uf_InteractiveDiag

##### Argumente

-   keine

##### Rückgabewert

-   cst_InteractiveDiag

##### Beschreibung

-   liefert das Standard- mäßig zu verwendende cst_InteractiveDiag-
    Objekt

-   in cst_ApplEnv gibt es eine private Shared- Variable vom Typ \##
    cst_InteractiveDiag

-   die Funktion instanziert diese, wenn dies noch nicht erfolgt ist,
    und liefert das Objekt zurück

-   im Allgemeinen wird man allerdings cst_ApplEnv.uf_ApplDiagOutput
    verwenden

-   uf_InteractiveDiag ist erst seit A21049 in cst_AppEnv angesiedelt

#### uf_InTransaction

##### Argumente

##### Rückgabewert

-   boolean
-   true, wenn ein Window eine Transaction offen hat

#### uf_JobVInfo

##### Argumente

-   as_Title
-   as_Text

##### Rückgabewert

-   (none)

##### Beschreibung

-   Schreibt die Nachricht, bestehend aus Titel und Text, in den
    Datastore PfuJobVinfo mit dem nach der Verarbeitung des Jobs die
    Tabelle pfu_job_vinfo aufgebaut wird.
-   Wird standardmäßig nur bei w_applenv.wf_Information2nl aufgerufen

#### uf_JobVInfoAnz

##### Argumente

##### Rückgabewert

-   long
-   Anzahl der Zeilen im Datastore PfuJobVinfo

##### Beschreibung

-   siehe Rückgabewert

#### uf_JobVInfoGetMessage

##### Argumente

-   al_row
-   Zeile im Datastore PfuJobVinfo
    -   as_Title
-   Reference, wird von Funktion befüllt
-   Titel der Nachricht in der Zeile vom Datastore
    -   as_Text
-   Reference, wird von Funktion befüllt
-   Text der Nachricht in der Zeile vom Datastore

##### Rückgabewert

-   (none)

##### Beschreibung

-   Liest die Nachricht, bestehend aus Titel und Text, aus dem Datastore
    PfuJobVinfo mit dem nach der Verarbeitung des Jobs die Tabelle
    pfu_job_vinfo aufgebaut wird.
-   Kann dazu verwendet werden um Nachrichten vom System, die man nicht
    direkt zurück bekommen hat, in weiterer Folge auszulesen.

## Beispiel

## // Letzte Nachricht vor meinen Code

## ll_before = iuo_ae.uf_JobVinfoAnz()

// Code bei dem Nachrichten erzeugt werden, die wir nicht selbst
bekommen \## (zB: wf_Save() bei Fernsteuerung)

...

## // Letzte Nachricht nach meinen Code

## ll_after = iuo_ae.uf_JobVinfoAnz()

// Jetzt kann man in einer Schleife, alle erhaltenen Nachrichten
auslesen \## for ll_row = ll_before +1 to ll_after

iuo_ae.uf_JobVinfoGetMessage(ll_row, ls_title, ls_text) ... \## end for

#### uf_KeyConst

##### Argumente

##### Rückgabewert

-   boolean
-   true, wenn alle Key- Felder des aktuellen AOT's gesetzt und konstant
    sind

##### Beschreibung

-   siehe Rückgabewert

#### uf_KeyFindWhere

##### Argumente

-   as_FindWhere
-   reference, wird von Funktion befüllt
-   Where- Bedingung für die DW- Funktion find, in der alle Keyfelder
    des aktuellen AOTs vorkommen und aus dem Env belegt werden

##### Rückgabewert

-   boolean
-   true, wenn alle benötigten Felder im Environment nicht null sind,
    sonst false

##### Beschreibung

-   befüllt as_FindWhere

Siehe auch - w_ApplObj.wf_ScrollToFindWhere

#### uf_KeyWhere

##### Argumente

-   as_tabname
-   Tabelle, für die Where- Bedingung aufgebaut werden soll
-   kann weggelassen werden, dann wird die Tabelle des AOTs herangezogen
    -   atr\_
-   Transaction, über welche Tabelle zu erreichen ist
    -   as_where
-   reference, wird von Funktion befüllt
-   Where- Bedingung für obige Tabelle in der alle Keyfelder des
    aktuellen AOTs vorkommen und aus dem Env belegt werden

##### Rückgabewert

-   boolean
-   true, wenn alle benötigten Felder im Environment nicht null sind,
    sonst false

##### Beschreibung

-   Wird z.B. zum Löschen von Rows in einer Tabelle, welche in einer 1
    zu n- Beziehung zur Tabelle des AOTs steht, benötigt.

#### uf_login

##### Argumente

##### Rückgabewert

-   string
-   Ist das Windows- Login

##### Beschreibung

-   darf nicht mehr verwendet werden, weil das Windows- Login in der
    Applikation keine Rolle spielen darf!!!
-   es sind die Funktionen uf_AnmeldUsr und uf_AnmeldApplpers zu
    verwenden!!!

#### uf_MaskMfa

##### Argumente

-   ai_mfa1_nr
-   ai_mfa2_nr
-   ai_mfa3_nr
-   as_MaskAot
-   readonly
-   ID- Name eines ein AOTs wie z.B. "auf"
    -   ai_MaskMfa1_nr
-   reference
    -   ai_MaskMfa2_nr
-   reference
    -   ai_MaskMfa3_nr
-   reference

##### Rückgabewert

-   (none)

##### Beschreibung

-   befüllt as_MaskMfa?\_nr mit den via ai_maf?\_nr übergebenen mfa-
    Werten maskiert durch die mfa- Maske lt. as_MaskAot
-   siehe uf_AoMfa

#### uf_MfaMask

##### Argumente

-   as_MaskAot
-   readonly
-   kann weggelassen werden, dann wird die Maske des aktuellen AOTs
    geliefert, wenn auch as_tabname weggelassen wird
    -   as_tabname -\> nicht vernünftig implementierbar
-   readonly
-   muss weggelassen werden, wenn as_MaskAot nicht weggelassen wird
    -   as_mfa1_nr_01
-   reference
    -   as_mfa2_nr_01
-   reference
    -   as_mfa3_nr_01
-   reference

##### Rückgabewert

-   (none)

##### Beschreibung

-   befüllt as_mfa?\_nr mit den mfa- Masken- Werten des as_MaskAot
    entsprechenden AOTs bzw der as_tabname entsprechenden
    Datenbanktabelle (lt. pfu_mfamask)

## uf_MfaWhere - fehlt noch

##### Argumente

-   as_tabname
-   Tabelle, für die Where- Bedingung aufgebaut werden soll
    -   atr\_
-   Transaction, über welche Tabelle zu erreichen ist
    -   as_where
-   reference, wird von Funktion befüllt
-   Where- Bedingung für obige Tabelle in der alle mfa- Felder des
    aktuellen AOTs vorkommen und aus dem Env belegt werden, wobei Felder
    die in der mfa- Maske (lt. pfu_mfamaske) der Tabelle lt. as_tabname
    0 sind, mit 0 angenommen werden
-   ist "1=2", wenn ein MFA- Bestandteil Null ist

##### Rückgabewert

-   boolean
-   true, wenn alle benötigten Felder im Environment nicht null sind,
    sonst false

##### Beschreibung

-   Wird z.B. für den Where- String eines DDDWs benötigt - z.B.:
-   Auftrag hat mfa- MAske (1,1,1) und die aktuellen Werte für die mfa-
    Felder sind (9,3,4)
-   DDDW für Versandart
-   diese hat mfa- Maske (1,0,0)
-   Ergebnis ist dann z.B. "where fa_nr = 9 and fil_nr = 0 and abt_nr =
    0"

#### uf_NextPostNr

##### Argumente

##### Rückgabewert

-   (None)

##### Beschreibung

-   siehe posten von Statements

#### uf_ParGet

##### Argumente

-   as_parname
-   ai_mfa1_nr
-   kann weggelassen werden, dann müssen alle mfa- Parameter weggelassen
    werden
-   wenn es einen Eintrag mit 0 gibt, wird dieser verwendet, falls es
    keinen Eintrag mit dem übergebenen Wert gibt - dies gilt für alle
    mfa- Parameter
    -   ai_mfa2_nr
    -   ai_mfa3_nr

##### Rückgabewert

-   Wert des Parameters

##### Beschreibung

-   beim Applikationsstart werden aus den Tabellen pfu_param\* alle
    Werte eingelesen und in einem sortierten Array gespeichert
-   beim Aufruf wird mittels binärer Suche aus diesem Array gelesen

## uf_ParGet\*

##### Argumente

##### Rückgabewert

-   Wert eines uf_ParSet\* gesetzten Parameters

##### Beschreibung

-   siehe dazu uf_ParSet\*

## uf_ParSet\*

##### Argumente

-   Wert des Parameters

##### Rückgabewert

-   (None)

##### Beschreibung

-   Dient zur Behandlung von Releases
-   Die Funktionen werden im gf_InitApplEnv aufgerufen
-   Die Funktionen sind nur nach Rücksprache anzuwenden

uf_SetCallConst:

##### Argumente

-   adw_Praefix
-   wenn adw_Praefix ein DW- AEO- Präfix hat, wird dieses as_colname für
    die AEO- Bestimmung vorangestellt
-   kann weggelassen werden
    -   as_colname
-   DW- Columnname, deren entsprechende(r) Environment- Wert(e) im neuen
    Environment konstant ist/sind.
    -   as_praefix
-   kann weggelassen werden
-   Präfix des AEO's im neuen Environment, welches konstant sein soll
-   kann '' sein, um im neuen Environment "kein Präfix" zu erzwingen

## alternative Argumente

-   as_const
-   ein DW- Colname ( alle AEOs, deren Präfix+Keycolumnname as_const ist
    "d" ( alle AEOs, welche in einem DW des Windows vorkommen "c" ( alle
    AEOs, welche jetzt const sein können "s" ( alle AEOs, welche jetzt
    const sein können und für die beim cst_ApplEnv.uf_AddAotEo bei
    ab_ConstSearch true übergeben worden ist "cc" ( alle AEOs, welche
    jetzt const sind "a" ( alle AEOs "k" ( alle AEOs, welche im Key des
    AOTs sind
    -   ab_set
-   kann weggelassen werden
-   default ist true
-   true ( setzen
-   false ( zurücksetzen (man kann zuerst Setzen und dann gewisse AEOs
    wieder zurücksetzen)

## alternative Argumente

-   ai_aeo
-   Nummer des AEOs im AOT
-   wird von manchen Events als Argument geliefert
    -   ab_set
-   kann weggelassen werden
-   default ist true
-   true ( setzen
-   false ( zurücksetzen (man kann zuerst Setzen und dann gewisse AEOs
    wieder zurücksetzen)

##### Rückgabewert

-   (None)

##### Beschreibung

-   Ein Aufruf bezieht sich auf den nächsten Aufruf von wf_open.
-   Bewirkt, daß die entsprechenden Environment- Werte im Environment
    des geöffneten Windows konstant den Wert aus dem aufrufenden Window
    haben.
-   das Konstant- Setzen eines AEOs betrifft allerdings nur den eigenen
    Key- Wert und nicht Key- Werte von AEOs, welche beim AOT des AEOs im
    Key sind.
-   Dies gilt nur für den nächstfolgenden wf_open- Aufruf (dieser
    erfolgt implizit auch beim Search, also nach der Ausführung von
    dw_ApplObj.Event CallConstSearch)
-   Beim Konstantsetzen im aufgerufenen Window wird natürlich die MFA-
    Maske des aufgerufenen Windows berücksichtigt
-   siehe auch uf_DefineAufrufConst

#### uf_SessionNr

##### Argumente

##### Rückgabewert

-   integer

##### Beschreibung

-   liefert die pfu_fun- SessionNummer der aktuellen Session
-   siehe Datenbankbeschreibung Tabelle pfu_session
-   ist im P- Key von Pseudo- Temp- Tables (also echten Tables, die
    statt Temp- Tables verwendet werden, um Datenbankunabhängig zu
    bleiben)
-   ACHTUNG: die Session- Nummer wird für eine andere Session
    wiederverwendet, wenn die Session beendet wird oder stirbt

#### uf_SetCommand

##### Argumente

-   as_command
-   Argument- Kommando- Name
    -   as_wert
-   Argumentwert

##### Rückgabewert

-   (None)

##### Beschreibung

-   Setzen eines bestehenden oder neuen Argumentkommandos
-   Siehe dazu: Begriffe.Kommandostring des Environments

#### uf_SetPraefixTitle

##### Argumente

-   as_PraefixTitle
-   das Praefix, welches angezeigt werden soll

##### Rückgabewert

-   (None)

##### Beschreibung

-   Zeigt nur im MDE-Modus vor dem eigentlichem Title das Praefix an.
-   ist standardmäßig mit Blank belegt

#### uf_SetSharedKontext

##### Argumente

-   as_kontext_fcd
-   siehe Beschreibung

##### Rückgabewert

-   (None)

##### Beschreibung

-   setzt den Wert für den Symbolischen Wert "@shared" für den Parameter
    as_kontext_fcd von gf_Text2nlSK\[1-9\]
-   wird hochgradig via gf_SetKontext aufgerufen

#### uf_SetWorkingTextNl

##### Argumente

-   as_WorkingText
-   der Text in Anmeldungssprache, der im Working- Fenster angezeit
    werden soll
-   in Fremdsprachen- fähigen Lösungen sollte der Text mittels
    uf_Text2nl übersetzt werden

##### Rückgabewert

-   Boolean
-   true ( Working ist gestartet worden und noch nicht beendet worden (
    wir sind im Zustand working
-   false ( sonst ( es wird kein Text gesetzt, weil ja das Working-
    Fenster gar nicht aktiv ist

##### Beschreibung

-   Setzt den Text im durch uf_WorkStart erzeugten Working- Fenster
-   siehe Rückgabewert

#### uf_ShEnvVarGet

##### Argumente

-   as_name

##### Rückgabewert

-   any
-   ACHTUNG: falls die Variable nicht existiert, wird ein Typloses Null
    zurückgeliefert - dieses kann nur von einer ANY- Variable
    aufgenommen werden - bei nicht Any erfolgt ein Applikationsabbruch

##### Beschreibung

-   Dient zum Auslesen einer Shared- Env- Variablen
-   Siehe uf_ShEnvVarSet

#### uf_ShEnvVarRm

##### Argumente

-   as_name

##### Rückgabewert

-   (None)

##### Beschreibung

-   Dient zum Entfernen einer Shared- Env- Variablen
-   Siehe uf_ShEnvVarSet

#### uf_ShEnvVarSet

##### Argumente

-   as_name
-   aa_wert

##### Rückgabewert

-   (None)

##### Beschreibung

-   Dient zum Setzen einer Shared- Env- Variablen
-   Shared- Env- Variable existieren für die gesamte Aplikation genau
    einmal
-   Der Variablen- Name ist ein beliebiger String mit Länge \> 0.
    ACHTUNG: "meinname" ist nicht gleich "meinname"

#### uf_StartApplAfterConnect

##### Argumente

-   as_WAppl
-   Windowname des Hauptfensters der Applikation
-   bei einer MDI- Applikation ist dies das MDI- Frame- Window
    -   as_command
-   ein Kommandostring in der Form `<Kommando>`{=html} \[
    `<leerzeichen>`{=html} `<Kommando>`{=html} ... \]
-   folgende Kommandos werden derzeit ausgewertet:
    -   "einplatz"
-   die Anzahl der Lizenzen ist fix = 1
-   es gibt keine Lizenzprüfung
-   def pfu_host- Eintrag wird automatischj ohne Benutzerinteraktion
    erstellt
-   dabei wird ein Dummy- Standort automatisch angelegt
    -   "offline"
-   Gridschema kann nicht gespeichert werden
-   in allen pfu_win- Windows dürfen keine Änderungen durchgeführt
    werden
-   kennsatz.soll_win_aend_jn wird ignoriert und es wird "n" angenommen
-   der Feldzuordnungsmodus und der Übersetzungsmodus stehen nicht zur
    Verfügung
    -   "MdeNoTitle"
-   Wenn die Applikation im MDE- Modus läuft, bewirkt "MdeNoTitle", dass
    das MDI- Frame- Window ohne Title-Bar angezeigt wird

##### Rückgabewert

-   keiner

##### Beschreibung

-   muss im open- Scripts der Applikation gleich nach dem letzten DB-
    Connect stehen
-   darf sonst nirgends aufgerufen werden

#### uf_StartApplBeforeConnect

##### Argumente

-   aappl\_
-   hier muss this übergeben werden

##### Rückgabewert

-   keiner

##### Beschreibung

-   muss ganz zu Beginn des open- Scripts der Applikation stehen
-   darf sonst nirgends aufgerufen werden

## uf_Text2nl\[Sk\]

##### Argumente

-   as_text

-   Informationstext

-   Logik wie bei wf_information

-   folgende beiden Argumente gibt es nur in der Sk- Version:

    -   as_sprache_cd

-   in der nicht-Sk- Version wird die Sprache der Anmeldung herangezogen

-   leer ( es wird die mittels gf_SetNl gesetzte Sprache herangezogen

    -   as_kontext_fcd

-   wenn es für as_text in unterschiedlichen Kontexten unterschiedliche
    Übersetzungen gibt, können diese jeweils durch as_kontext_fcd
    definiert werden

-   wird keine Übersetzung mit as_kontext_fcd gefunden, wird die
    Übersetzung mit as_kontext_fcd="" durchgeführt

-   Wenn die Funktion in einer Expression in einem DWO verwendet wird,
    muss hier der DWO- Name stehen. Kommt im DWO as_text mehrmals in
    unterschiedlicher Bedeutung vor, ist nach dem DWO- Namen "-xy"
    anzuhängen -- xy ist ein beliebiger Text, der die Eindeutigkeit
    gewährleistet.

-   siehe auch in der Basisklassen- Datenbankbeschreibung Tabelle \##
    pfu_sprache_text

-   hier kann auch "@shared" stehen - dann wird der mittels
    gf_SetKontext gesetzte Wert herangezogen

-   in der nicht-Sk- Version wird as_kontext_fcd="" angenommen

    -   aa_par\[1-9\]

-   0 bis zu 9 Parameter

-   für den 3. Parameter muss in as_text "\[3auf_nr\]" vorhanden sein

-   3 steht hier exemplarisch für eine Ziffer von 1 bis 9

-   "auf_nr" ist ein col_name in pfu_column und ist ausschließlich für
    die Formatierung notwendig

-   dazu gibt es folgende Standardfelder, falls kein sonstiges Feld zur
    Verfügung steht:

    -   "TypeC"
    -   "TypeN"
    -   "TypeD"
    -   "TypeDt"
    -   "TypeT"

-   parameter wird lt. pfu_column auf String konvertiert - Null wird zu
    Leerstring

##### Rückgabewert

-   string
-   übersetzter Text

##### Beschreibung

-   übersetzt as_text in die Sprache lt. as_sprache_cd
-   wenn as_sprache_cd = 'd' und as_kontext_fcd = '', wird nicht
    übersetzt
-   kann auch via gf_Text2nlSK\[1-9\] aufgerufen werden

#### uf_Wert

##### Argumente

-   as_ColName
-   Name der PKey- Column eines AEOs inklusive Präfix (z.B. ab_auf_nr)

##### Rückgabewert

-   any

##### Beschreibung

-   liefert den Wert im Env für für die Column lt. as_ColName
-   gibt es keine entsprechende Column im Env, erfolgt ein
    Programmabbruch
-   Ist nur mehr aus Abwärtskompatibilitätsgründen vorhanden
-   macht leider nicht mehr genau das Gleiche wie vorher - macht jetzt
    folgendes: . bestimme das AEO, dessen PKey- Columnname inklusive
    Praefix = as_ColName . ermittle die Column in w_ApplObj.idw_list,
    die der PKey- Column des gefundnen AOEs zugeordnet ist . wenn es
    keine solche, wird die Applikation angehalten . wenn es keine
    aktuelle Row \> 0 gibt, wird NULL im Typ der gefundnen Column
    zurückgeliefert - sonst der entsprechende Wert

#### uf_WorkEnd

##### Argumente

-   ab_posted
-   wird normalerweise weggelassen, dann wird false angenommen
-   true darf nicht verwendet werden - ist dem System vorbehalten -
    uf_WorkStart(true)
-   false (also auch der Aufruf ohne Argument) darf nur verwendet
    werden, wenn zuvor ein uf_WorkStart (false,...) aufgerufen worden
    ist
    -   aw_FocusAfterWork
-   ist wegzulassen, wenn ab_posted weggelassen wird
-   Window, erhält den Focus

##### Rückgabewert

-   (None)

##### Beschreibung

-   siehe vorher uf_WorkStart
-   Enabled das Main- Window und schaltet den Mauszeiger zurück auf
    Pfeil
-   das Window lt. aw_FocusAfterWork erhält den Focus

#### uf_WorkStart

##### Argumente

-   ab_PostWorkend
-   wird normalerweise weggelassen, dann wird true angenommen
-   true -\> es wird die Funktion uf_WorkEnd gepostet, sodass der
    "working"- Zustand wieder beendet wird
-   false -\>
-   die Funktion uf_WorkEnd muss vom Anwendungsprogrammierer explizit
    aufgerufen werden, um den "working"- Zustand zu beenden
    -   ab_WWorking
-   während des "working"- Zustandes wird ein Window angezeigt
-   wird nur bei ab_PostWorkEnd = false ausgewertet

##### Rückgabewert

-   (None)

##### Beschreibung

-   Versetzt das System in den sogenannten "working"- Zustand:
-   das Main- Window ist disabled
-   der Mauszeiger ist auf Sanduhr umgeschaltet
-   Wird vom System aufgerufen, wenn angenommen wird, daß eine
    Verarbeitung länger dauert.
-   kann aber auch vom Anwendungsprogrammierer aufgerufen werden
-   So lange das Working- Fenster offen ist, kann sein Tzext mittels
    uf_SetWorkingTextNl gesetzt werden
-   Anmerkung Fremdsprachen: in einer Fremdsprachen- Fähigen Lösung
    sollte nach jedem Start des Working- Fensters uf_SetWorkingTextNl
    mit einem via uf_Text2nl übersetzten Text aufgerufen werden

## Variables

## ia_arg

-   das Argument, das mittels des Parameters aa_Arg von
    w_ApplObj.wf_open in das neue Window übergeben werden kann
-   darf nicht verändert werden!
-   ist nicht belegt, wenn das cst_ApplEnv- Objekt keinem mittels
    wf_open geöffneten Window zugeordnet ist (z.B. bei message.iuo_ae)

## ii_anmeldung

-   die Anmeldung des AOs
-   darf nicht verändert werden!

## ib_ApplicationserverProxy

-   siehe iuo_ApplicationServerProxyDataContext
-   darf nicht verändert werden!

## is_RequestedWindow

-   der wf_open übergebene Windowname
-   darf nicht verändert werden!

## iuo_ApplicationServerProxyDataContext

-   nur verfügbar wenn ib_ApplicationserverProxy = true
-   ist das Proxy- Objekt für einen Datacontext im Applicationserver
-   darf nicht verändert werden!

## iuo_ColType

-   siehe cst_ColType
-   kann verwendet werden, sodass man keine eigene Instanz erzeugen muss
-   darf nicht verändert werden!

## iw_AeAkt

-   das Window des Aplenv's
-   muss einer Variable des richtigen Typs zugewiesen werden
-   darf nicht verändert werden!

## iw_AeParent

-   das Parent- Window des Window's des Aplenv's
-   muss einer Variable des richtigen Typs zugewiesen werden
-   darf nicht verändert werden!

## iw_main

## `<iw_main>`{=html}

-   das MDI- Frame- Window
-   darf nicht verändert werden!

## if iuo_ae then

lb_ApplicationServerButNotMaster = \##
iuo_ae.iuo_ApplicationServerProxyDataContext.iw_AoDataContextMaster \<\>
this

## Events

## MessageBoxWindow

##### Argumente

##### Rückgabewert

-   MessageBoxWindow (string)

##### Beschreibung

Retouniert.den Namen für ein MessageBoxWindow, welches die Meldungen der
Application anzeigt. Wird derzeit nur im MDE-Modus ausgewertet.

## SetApplicationName

##### Argumente

##### Rückgabewert

-   ApplicationName (string)

##### Beschreibung

setzt den ApplicationName für die Application. wird benötigt beim Aufbau
der AOTs für die Application und für die Anlage der Session.

wird dann benötigt wenn ein der selbe Programmstand für zwei
verschiedene Applicationen verwendet wird.

## SetLizenzName

##### Argumente

##### Rückgabewert

-   LizenzName (string)

##### Beschreibung

setzt den LizenzName für die Application. wird benötigt beim Prüfen der
Lizenzen für die Application.

wird dann benötigt wenn ein der selbe Programmstand für zwei
verschiedene Applicationen verwendet wird.

## cst_ApplicationServerProxyDataContext

-   stellt die Schnittstelle zu einem Datacontext dar

### Functions

#### uf_CheckProcessApplicationserverMessages

##### Argumente

-   ab_markieren
-   by Reference
-   zum Durchschleifen des gleichnamigen Parameters des action- Events
    -   ai_SchwereReturn
-   ab diesem Schweregrad ist der Rückgabewert der Funktion = "r"
    -   ai_SchwereContinue
-   ab diesem Schweregrad ist der Rückgabewert der Funktion = "c"
    -   ai_SchwereMarkieren
-   ab diesem Schweregrad wird ab_markieren auf true gesetzt
    -   ab_CancelOnError
-   wenn true übergeben wird, wird der Datacontext gecanceled, wenn
    Schweregrad \>= 3
    -   auo_ae
-   cst_ApplEnv von w_JobObj

##### Rückgabewert

-   string \> "r" (wie return)
-   bedeutet, dass das action- Events mittels Return zu verlassen ist \>
    "c" (wie continue)
-   bedeutet, dass mit der nächsten zu verarbeitenden Row weitergemacht
    werden soll \> " "
-   bedeutet, dass normal weitergemacht werden kann

##### Beschreibung

-   Die Funktion dient zum Aufruf aus dem action- Event von w_JobObj
-   Ist zu verwenden, nachdem eine Funktionalität des Applicationservers
    aufgerufen worden ist
-   wertet den Schweregrad eines eventuellen Fehlers aus und sorgt
    dafür, dass die Messages der Applicationserver- Messageliste in die
    Job- Info geschrieben werden
-   der Schweregrad ist folgendermaßen definiert:
-   0 ... kein Fehler und keine Meldungen
-   1 ... es gibt informations- Meldungen
-   2 ... es gibt Warnungen
-   3 ... es gibt Fehler
-   4 ... es gibt MustCancelDatacontext- Fehler
-   5 ... es gibt MustCloseDatacontext- Fehler
-   6 ... es gibt MustCloseDataSessionFehler

## Variables

## iw_AoDataContextMaster

-   das Haupt- Window des Datacontext
-   nur über dieses kann der Datacontext gespeichert werden
-   siehe w_ApplObj. wf_open
-   darf nicht verändert werden!

## cst_DwApplObjCObj

-   repräsentiert ein Datawindow- Object Column- oder Computed- Control
-   Bei Bedarf können weitere Informationen freigegeben werden

## Variables

## is_name

-   Darf nicht verändert werden!
-   Name der \[Computed\]- Column

## cst_ColType

-   dient zum Konvertieren und Formatieren von Datenfeldern
-   wird intern verwendet aber 2 Funktionen sind für den allgemeinen
    Gebrauch bestimmt - beim Daten- Ex- bzw. Import sind diese anzuraten
-   es kann für ein Projekt davon abgeleitet werden

### Functions

#### uf_AnyToInputString

##### Argumente

-   ai_anzstellen
-   siehe as_dattyp
    -   ai_anznachkomma
-   siehe as_dattyp
    -   ab_interpunktion
-   wird ignoriert
-   kann bei einer Ableitung allerdings ausgewertet werden
    -   as_dattyp \> "b" ( boolean
-   I: "Ja", "Nein"
-   A: char - "j", "n" \> "c" ( Char = alphanumerisch
-   I: char
-   A: char \> "d" ( Date
-   I:
-   die linkeste Ziffer von ai_anzstellen gibt die Anzahl der
    numerischen Stellen an 6 ( "31.12.05" 8 ( "31.12.2005" A: date \>
    "dt" ( Datetime
-   I: `<wie date>`{=html} `<blank>`{=html} `<wie time>`{=html} z.B.
    "14.02.2005 13:39:44"
-   A: datetime \> "t" ( Time
-   I:
-   ai_anznachkomma gibt die Anzahl der numerischen Stellen an 2 ( "13"
    4 ( "13:40" 6 ( "13:40:33" A: time \> "m" ( Monat (= Kalendermonat)
-   I: char - "200509"
-   A: char - "200509" \> "n" ( numerisch
-   I: char - 234,98 bzw. 234 abhängig von ai_anznachkomma
-   A: number \> "w" ( Woche (= Kalenderwoche)
-   I: char - "200543"
-   A: char - "2005/34"
-   I: ( Darstellung als Inputstring
-   A: ( Darstellung als Any
    -   aa_wert

##### Rückgabewert

-   string

##### Beschreibung

-   Wandelt aa_wert in einen formatierten String um und gibt diesen
    zurück

#### uf_InputStringToAny

##### Argumente

-   ai_anzstellen
-   siehe uf_AnyToInputString
-   0 ( keine Prüfung
    -   ai_anznachkomma
-   siehe uf_AnyToInputString
-   wird ignoriert, wenn ai_anzstellen = 0
    -   ab_darf0
-   bedeutet: Wert darf 0 sein
    -   ab_darfminus
-   bedeutet: wert darf negativ sein
    -   as_dattyp
-   siehe uf_AnyToInputString
    -   as_input
    -   aa_output
-   reference
    -   as_error
-   reference
-   Fehlermeldung: wird bei return false gesetzt

##### Rückgabewert

-   boolean
-   bei Erfolg ( true
-   sonst ( false

##### Beschreibung

-   Wandelt as_input in den as_dattyp entsprechenden Typ um und stellt
    das Ergebnis nach as_output
-   bei folgenden Datentypen gibt es folgende symbolische Eingaben:
    (Zeichenerklärung: \[\] ... optional, {} ... eine der aufgelisteten
    Möglichkeiten) (besonders bei Defaultwerten brauchbar)
    -   "c"
    -   `anmeldusr`
-   der User der Anmeldung
    -   `anmeldapplpers`
-   der Sachbearbeiter der Anmeldung
    -   `clihostname`
-   Der Client- Hostname
    -   `ins`
-   Aktuelle Instanz
    -   "d", "dt": (nicht bei EditMask)
-   für den Datum- Anteil kann "heute" \[ {"+","-"} Zahl \] eingegeben
    werden
-   statt "heute" wird das aktuelle Datum eingesetzt
-   dazu werden ggf. +/- Zahl Tage addiert
-   statt heute gibt es weiters:
    -   "h" bzw. "a" ( gleich wie heute
    -   "g" ( gleich wie heute-1 (gestern)
    -   "m" ( gleich wie heute+1 (morgen)
    -   "v" ( gleich wie heute-2 (vorgestern)
    -   "ü" ( gleich wie heute+2 (übermorgen)
    -   "c" ( der Monatserste des aktuellen Monats (irgendjemand hat das
        offensichtilch gegoogelt c für calendae = der Monatserste)
    -   "u" ( der Monatsletzte (Ultimo) des aktuellen Monats
    -   "dt", "t": (nicht bei EditMask)
-   für den Uhrzeit- Anteil kann "jetzt" \[ {"+","-"} Zahl \] eingegeben
    werden
-   statt "jetzt" wird die aktuelle Zeit eingesetzt
-   dazu werden ggf. +/- Zahl Sekunden addiert
    -   "m":
-   es kann { "a","j","v"} \[ {"+","-"} Zahl \] eingegeben werden
-   statt "a" wird der aktuelle Monat eingesetzt
-   statt "j" wird der erste Monat (=Jänner) des aktuellen Jahres
    eingesetzt
-   statt "v" wird der erste Monat des Jahres des Vormonats des
    aktuellen Monats eingesetzt
-   dazu werden ggf. +/- Zahl Monate addiert (dabei ist das
    Überschreiten von Jahresgrenzen möglich)
    -   "w":
-   es kann "a" \[ {"+","-"} Zahl \] eingegeben werden
-   statt "a" wird die aktuelle Woche eingesetzt
-   dazu werden ggf. +/- Zahl Wochen addiert (dabei ist das
    Überschreiten von Jahresgrenzen möglich)
-   in w_AplObjQuery kann den symbolischen Werten ein "\^"- Zeichen
    vorangestellt werden, dadurch wird bei einem Job der symbolische
    Wert erst aufgelöst, wenn der Job ausgeführt wird
-   Bsp.:
-   eine Auswertung wird so eingespoolt, dass sie täglich um 20:00
    ausgeführt wird
-   für den Parameter Auswertungsdatum wird "\^h" eingetragen
-   ( als Auswerungsdatum wird dann das Tagesdatum zum jeweiligen
    Zeitpunkt der Ausführung herangezogen
-   sinngemäß gleich funktioniert die "\^"- Zeichen- Version auch beim
    von- bis- Bereich von pfu_col:
-   ohne "\^"- Zeichen wird beim Programmstart aufgelöst
-   mit erst bei der Prüfung

## cst_Exception

-   ist eine von Throwable abgeleitete Exception mit zusätzlichen
    Informationen

### Functions

## uf_GetFullText()

##### Rückgabewert

-   string
-   Text mit der gesamten verfügbaren Information der Exception

##### Rückgabewert

-   boolean
-   true, wenn die Row lt. al_NextRowNumber existiert

##### Beschreibung

-   Dient zum Auslesen aller gedraggten Datawindow- Rows

## cst DraggedDataWindowField

-   Ein Feld eines Datawindows

## Variables

## idw\_

-   Darf nicht verändert werden!
-   Das Datawindow des gedraggten Feldes

## il_Row

-   Darf nicht verändert werden!
-   Die zugehörige Row-Nummer

## iuo_Field

-   Darf nicht verändert werden!
-   cst_DwApplObjCObj

## cst DraggedDataWindowRows

-   Eine oder mehrere Rows eines Datawindows

## Variables

## idw\_

-   Darf nicht verändert werden!
-   Das Datawindow des gedraggten Feldes

## il_RowCount

-   Darf nicht verändert werden!
-   anzahl der Rows

### Functions

#### uf_GetNextRow

##### Argumente

-   al_NextRowNumber
-   by Reference
-   hier wird die Nummer der nächsten Zeile, die geliefert werden soll,
    übergeben - typischerweise wird hier eine lokale Variable übergeben,
    die vor einer Schleife über alle gelieferten Rows auf 1 gesetzt wird
-   die Funktion inkrementiert den Wert bei jedem Aufruf um 1
    -   al_DataWindowRow
-   by Reference
-   hie wird typischr Weise eine long- Variable mit dem Wert 0 übergeben
    -   es werden nur Rows im Datwindow, deren Row-Nummer \>
        al_DataWindowRow sind, berücksichtigt
-   die Funktion schreibt die Row-Nummer im Datawindow der geliferten
    Datawindow- Row hinein

##### Rückgabewert

-   boolean
-   true, wenn die Row lt. al_NextRowNumber existiert

##### Beschreibung

-   Dient zum Auslesen aller gedraggten Datawindow- Rows

## cst DraggedFileList

-   Eine Liste von File- Pfaden
-   Entsteht z.B., wenn im File- Explorer ein File bzw. mehrere
    markierte Files gedragged werden

## Variables

## is_FilePath\[\]

-   Darf nicht verändert werden!
-   Ein Array mit einem File-Path je Element

## cst_DraggedObject

-   Basisklasse für Objekte, die gedragged werden könnne

## Variables

## ic_ObjectKind

-   Darf nicht verändert werden!
-   Definiert die abgeleitete Klasse des Objekts
-   Folgende Werte: \> "r" ... cst DraggedDataWindowRows \> "f" ... cst
    DraggedDataWindowField \> "p" ... cst DraggedFileList ("p" steht für
    FilePath) \> Weitere folgen bei Bedarf

## cst_filefun (sys)

-   Objekt zum Lesen bzw. Schreiben von Dateien im Filesystem. Soll
    statt der Powerbuilderfunktionen verwendet werden, weil die
    Powebuilderfunktionen in Fehlerfall keine Fehlerursache liefern.

### Functions

#### uf_CopyFile

##### Argumente

-   as_vonFile
-   Quelldateiname
    -   as_aufFile
    -   Zieldateiname
    -   ab_FailIfExists
-   true ( es wird false geliefert, wenn die ZielDatei existiert
-   false ( die ZielDatei wird überschrieben, wenn sie existiert

##### Rückgabewert

-   boolean

##### Beschreibung

-   Kann dazu verwendet werden, um eine Datei zu kopieren und
    gegebenenfalls zu überschreiben. Wenn die Funktion false liefert,
    kann mit uf_GetLastError die Ursache ermittelt werden.

#### uf_CreateShellLink

##### Argumente

-   as_LnkName
-   Name inkl. vollem Pfad wo der Link angelegt warden soll
    -   as_Target
-   Name der Datei bzw. Verzeichnisses inkl. vollem Pfad auf den der
    Link zeigen soll.
    -   as_WorkingDirectory
-   Arbeitsverzeichniss für das Programm ...
    -   as_Arguments
-   Argumente die dem Programm mitgegeben werden soll
-   kann leer sein
    -   as_Description
-   Beschreibung für die Verküpfung
    -   as_IconFile
-   Datei inkl. vollem Pfad das für das Icon herangezogen werden soll
-   kann leer sein
    -   ai_ShowCommand
-   Argumente die dem Programm mitgegeben werden soll
-   wie das Programm gestartet werden soll
-   5 = Normal
-   3 = Maximized
-   7 = Minimized

##### Rückgabewert

-   boolean

##### Beschreibung

-   Erstellt eine Verknüpfung im FileSystem
-   ACHTUNG: PfuVBFun in der Version ab 1.01.0014 muss im System
    registriert sein.

#### uf_DeleteFile

##### Argumente

-   as_FileName

##### Rückgabewert

-   boolean

##### Beschreibung

> Löscht eine Datei im Filesystem. Retourniert boolean ob Datei gelöscht
> werden konnte. Wenn False kann mit der Funktion uf_GetLastError die
> Fehlerursache ermittelt werden.

#### uf_FileOpen

##### Argumente

-   as_FileName
-   as_FileMode 'l' ... LineMode (ließt Daten bis zum ersten CR-LF und
    gibt diese Zurück) 's' ... StreamMode (ließt in definierten Byte
    blöcken, Default: 32765 Bytes)
-   as_FileAccess 'r' ... Lesen 'w' ... Schreiben
-   as_FileLock 'rw' ... Sperrt die Datei zum Lesen und Schreiben 'r'
    ... Sperrt die Datei zum Lesen 'w' ... Sperrt die Datei zum
    Schreiben 's' ... Datei kann zum Lesen und Schreiben geöffnet werden
-   as_WriteMode 'a' ... An die Datei anhängen 'r' ... Die Datei
    überschreiben

##### Rückgabewert

-   integer: Dateinummer
-   Returniert die Dateinummer
-   Returniert -1 wenn das Öffnen der Datei fehlgeschlagen ist Die
    Funktion uf_GetLastError kann Aufschluss bringen.
-   Returniert -2 wenn der Parameter as_FileAccess einen falschen Wert
    hat.
-   Returniert -3 wenn der Parameter as_FileLock einen falschen Wert
    hat.
-   Returniert -4 wenn der Parameter as_WriteMode einen falschen Wert
    hat.
-   Returniert -5 wenn im Filenamen ungültige Zeichen sind
    (/:\*?"\<\>\|).

##### Beschreibung

-   Öffnet eine angegebene Datei im Filesystem zum schreiben oder lesen.

#### uf_FileClose

##### Argumente

-   ai_FileNum
-   Die Dateinummer, die zuvor von uf_FileOpen returniert wurde.

##### Rückgabewert

-   boolean: Das schließen der Datei hat funktioniert. Wenn nicht, kann
    die Funktion uf_GetLastError Aufschluss bringen.

##### Beschreibung

-   Schließt eine geöffnete Datei.

#### uf_FileWrite

##### Argumente

-   ai_FileNum
-   Die Dateinummer die zuvor von uf_FileOpen returniert wurde.
    -   as_Daten
-   Daten die in die Datei geschrieben werden sollen. Wenn die Datei im
    LineMode geöffnet wurde, wird automatisch ein CR-LF angehängt.

##### Rückgabewert

-   boolean: Das schreiben in die Datei hat funktioniert. Wenn nicht,
    kann die Funktion uf_GetLastError Aufschluss bringen.

##### Beschreibung

-   Schreibt in eine geöffnete Datei.

#### uf_FileWrite

##### Argumente

-   ai_FileNum
-   Die Dateinummer die zuvor von uf_FileOpen returniert wurde.
    -   ablob_Daten

##### Rückgabewert

-   boolean: Das schreiben in die Datei hat funktioniert. Wenn nicht,
    kann die Funktion uf_GetLastError Aufschluss bringen.

##### Beschreibung

-   Schreibt in eine im StreamModus geöffnete Datei.

#### uf_FileRead

##### Argumente

-   ai_FileNum
-   Die Dateinummer die zuvor von uf_FileOpen returniert wurde.
    -   as_Daten
-   reference, wird von Funktion befüllt
-   Daten die von der Datei gelesen wurde. Wenn die Datei im LineMode
    geöffnet wurde, wird bis zum nächsten CR-LF eingelesen, bzw. bis zum
    Dateiende wenn keines gefunden wird. Im StreamMode werden
    Defaultmäßig 32765 Bytes eingelesen bzw. bis zum Dateiende.
    -   optional
    -   al_Bytes2Read
-   Gibt an wie viele Bytes auf einmal gelesen werden sollen.

##### Rückgabewert

-   integer: Anzahl gelesener Bytes
-   -100 bei EOF
-   -1 bei Fehler ( uf_GetLastError kann Aufschluss bringen.

##### Beschreibung

-   Ließt von einer geöffneten Datei Daten.

#### uf_FileRead

##### Argumente

-   ai_FileNum
-   Die Dateinummer die zuvor von uf_FileOpen returniert wurde.
    -   ablob_Daten
-   reference, wird von Funktion befüllt
-   Daten die von der Datei gelesen wurde. Wenn die Datei im LineMode
    geöffnet wurde, wird bis zum nächsten CR-LF eingelesen, bzw. bis zum
    Dateiende wenn keines gefunden wird. Im StreamMode werden
    Defaultmäßig 32765 Bytes eingelesen bzw. bis zum Dateiende.
    -   optional
    -   al_Bytes2Read
-   Gibt an wie viele Bytes auf einmal gelesen werden sollen.

##### Rückgabewert

-   integer: Anzahl gelesener Bytes
-   -100 bei EOF
-   -1 bei Fehler ( uf_GetLastError kann Aufschluss bringen.

##### Beschreibung

-   Ließt von einer geöffneten Datei Daten.

#### uf_GetLastError

##### Argumente

-   as_Error
-   reference, wird von Funktion befüllt.
-   Enthält die Fehlermeldung vom Betriebssystem.
    -   aul_ErrorCode (unsigned Long)
-   reference, wird von Funktion befüllt
-   Die Fehlernummer lt. Betriebssystem

##### Rückgabewert

-   (none)

##### Beschreibung

-   Liefert die Fehlermeldung und Fehlercode des letzten Fehlers zurück.

#### uf_MoveFile

##### Argumente

-   as_vonFile
-   Quelldateiname
    -   as_aufFile
-   Zieldateiname
    -   ab_OverWrite
-   Gibt an ob eine vorhandene Datei überschrieben werden soll

##### Rückgabewert

-   boolean

##### Beschreibung

-   Kann dazu verwendet werden, um eine Datei zu verschieben/umbennen
    und gegebenenfalls zu überschreiben. Wenn die Funktion false
    liefert, kann mit uf_GetLastError die Ursache ermittelt werden.

## cst_ftp (sys)

-   Objekt zur Kommunikation mit einem FTP Server.
-   ACHTUNG: darf ab pfu_fun Release 2014-09-15 nicht mehr verwendet
    werden !!!

### Functions

#### uf_ChangeDirectory

##### Argumente

-   as_Directory
-   Remote Directory in das gewechselt werden soll V

##### Rückgabewert

-   boolean V

##### Beschreibung

-   Verzeichnis auf dem FTP Server in das gewechselt werden soll.

#### uf_Command

##### Argumente

-   as_Command
-   Commando welches an den FTP Server geschickt werden soll
    -   as_Options
-   Etwaige notwendige Optionen für das Commando

##### Rückgabewert

-   boolean V

##### Beschreibung

-   Kann dazu verwendet werden beliebige vom FTP Server verstandene
    Befehle zu senden.

#### uf_Connect

##### Argumente

-   as_Host
-   Hostname oder IP Adresse des FTP Servers
    -   as_UserName
-   Benutzername mit dem die Anmeldung beim FTP Server erfolgen sein.
    -   as_Password
-   Das Kennwort des Benutzers am FTP Server
    -   ai_TimeOutForConnect
-   Timeout für die Verbindung in Milisekunden Sekunden (lt. Beobachtung
    SC am 9.11.2010)

##### Rückgabewert

-   boolean

##### Beschreibung

-   Stellt eine Verbindung zu einem FTP Server her. V

#### uf_DeleteFile

##### Argumente

-   as_Remote

##### Rückgabewert

-   boolean

##### Beschreibung

-   Löscht eine Datei auf dem FTP Server. Retourniert boolean ob Datei
    gelöscht werden konnte. Wenn False kann mit der Funktion
    uf_GetLastError die Fehlerursache ermittelt werden.

#### uf_Disconnect

##### Argumente

##### Rückgabewert

-   boolean

##### Beschreibung

-   Schließt die Verbindung zum FTP Server.

#### uf_FileStatus

##### Argumente

-   as_FileName
-   Dateiname auf dem FTP Server für die Informationen eingeholt werden
    soll.
    -   al_FileSize
-   reference, wird von Funktion befüllt.
-   Gibt die Größe der Datei auf dem FTP Server an. Dies kann
    unterschiedlich zur
-   Größe der Datei am lokalen Filesystem sein auf Grund Betriebssystem
    unterschieden.
    -   as_FileDate
-   reference, wird von Funktion befüllt.
-   Datum und Uhrzeit der letzten Änderung
    -   as_FileOwner
-   reference, wird von Funktion befüllt.
-   Besitzer der Datei
    -   as_FileGroup
-   reference, wird von Funktion befüllt.
-   Gruppe der Datei
    -   as_FilePerms
-   reference, wird von Funktion befüllt.
-   Berechtigungen der Datei
    -   ab_IsDirectory
-   reference, wird von Funktion befüllt.

##### Rückgabewert

-   boolean: Wenn false ist die Datei auf dem Server most likely nicht
    vorhanden V

##### Beschreibung

-   Ermittelt Informationen zu einer Datei auf dem FTP Server. V V

#### uf_GetFile

##### Argumente

-   as_Lokal
-   Dateiname inkl. Verzeichnis wo die Remote Datei abgelegt werden
    soll.
    -   as_Remote
-   Datei die heruntergeladen werden soll.
    -   ab_Append
-   Remote Datei soll an lokal vorhandene Datei angehängt werden. Wenn
    die Lokale Datei nicht existiert, wird diese erzeugt. V

##### Rückgabewert

-   boolean: Die Datei wurde erfolgreich heruntergeladen. Bei false kann
    mittels uf_GetLastError der Fehler ermittelt werden. V

##### Beschreibung

-   Lädt eine Datei vom FTP Server herunter. V

#### uf_GetLastError

##### Argumente

V

##### Rückgabewert

-   string: Eine leserliche Fehlermeldung zum aufgetretenen Problem.

##### Beschreibung

-   Gibt die Beschreibung zum letzten aufgetretenen Problem zurück. V

#### uf_Initialize

##### Argumente

V

##### Rückgabewert

-   boolean V

##### Beschreibung

-   Initialisiert das Objekt! Diese Funktion muss als erstes aufgerufen
    werden. Wenn nicht (FEHLER
-   Damit cst_ftp funktionieren kann, muss auf dem Zielsystem folgende
    Datei aus dem Shared Verzeichnis registriert werden: csftpctl.ocx
    (regsvr32)
-   Geht so: in der Kommandozeile in den Sharedordner wechseln und
    "regsvr32 csftpctl.ocx" eintippen (anm. JP)

#### uf_PutFile

##### Argumente

-   as_Lokal
-   Dateiname inkl. Verzeichnis die auf den FTP Server kopiert werden
    soll.
    -   as_Remote
-   Dateiname auf dem FTP Server im aktuellen Verzeichnis
    (uf_ChangeDirectory)
    -   ab_Append
-   Lokale Datei soll an remote vorhandene Datei angehängt werden. Wenn
    die remote Datei nicht existiert, wird diese erzeugt. V

##### Rückgabewert

-   boolean V

##### Beschreibung

-   Wird verwendet, um eine Datei auf den FTP Server abzulegen.

#### uf_RenameFile

##### Argumente

-   as_Old
-   Alter, vorhandener, Dateiname
    -   as_New
-   Neuer, nicht vorhandener, Dateiname

##### Rückgabewert

-   boolean: false, falls die Datei nicht vorhanden ist, oder eine Datei
    mit dem neuen Namen bereits vorhanden ist. V

##### Beschreibung

-   Benennt eine am FTP Server vorhandene Datei um

#### uf_SetFileType

##### Argumente

-   as_FileType
-   Type der Übertragung
-   Folgende Werte sind möglich:
-   ascii
-   bin oder binary
-   ebcdic

##### Rückgabewert

-   boolean: false, falls der Filetyp auf dem Server nicht unterstützt
    wird. EBCDIC kann auf einem Linux oder Windows FTP Server nicht
    eingestellt werden. V

##### Beschreibung

-   Bestimmt den Dateityp.

## cst_FtpHelper

-   Stellt die Infrastruktur zur Kommunikation mit einem FTP-Server zur
    Verfügung.
-   Abgeleitet von cst_OleObject
-   Es ist außer dem FullyQualifiedClassname- Event nichts übersteuert -
    die COM- Klasse ist Pcs.Interop.FtpHelper.FtpHelper
-   alle Funktionalitäten stehen direkt über die COM- Klasse zu
    Verfügung
-   siehe Verwendung von COM- Klassen (PCS.Interop ...)

## cst_InteractiveDiag (sys)

-   Stellt die Infrastruktur zur Ausgabe von interaktiven
    Diagnosemeldungen zur Verfügung.
-   Die Meldungen werden in einem von der PB-Applikation unabhängigen
    Diagnosefenster angezeigt.
-   ( Die Meldungen können auf einem anderen Schirm ausgegeben werden
-   Das Diagnosefenster wird bei Bedarf geöffnet und bleibt dann offen.
-   Das Instanzieren eines InteractiveDiag- Objektes sollte, wenn die
    pfu_fun verwendet wird, Standard- mäßig nicht explizit erfolgen,
    sondern es sollte cst_ApplEnv.uf_InteractiveDiag verwendet werden
    (z.B. message.uf_InteractiveDiag.uf_PutLine())

### Functions

#### uf_PutLine

##### Argumente

-   as_Text
-   der auszugebende Text V

##### Rückgabewert

-   (None)

##### Beschreibung

-   Gibt as_text am Diagnosefenster aus.
-   Vor as_text wird der aktuelle Zeitpunkt ausgegeben, danach ein
    Zeilenwechsel

#### uf_Reset

##### Argumente

-   keine

##### Rückgabewert

-   (None)

##### Beschreibung

-   Löscht das Diagnosefenster

#### uf_Show

##### Argumente

-   keine

##### Rückgabewert

-   (None)

##### Beschreibung

-   Zeigt das Diagnosefenster an
-   Ist dazu gedacht, das Diagnosefenster anzuzeigen, bevor mit der
    Diagnose begonnen wird, sodass es auf einen anderen Schirm
    verschoben werden kann

## cst_Job

-   dient zum erstellen, speichern und Auslesen eines Jobs

### Functions

#### uf_GetItem

##### Argumente

-   as_Column
-   Column- Name aus der Tabelle pfu_job

##### Rückgabewert

-   any
-   null, wenn Column nicht vorhanden
-   Wert der Column

##### Beschreibung

-   Dient zum Auslesen eines Column- Werts des über uf_retrieve
    eingelesenen Jobs

#### uf_JobSnr

##### Argumente

##### Rückgabewert

-   long
-   die job_snr des Jobs
-   steht nur zur Verfügung, wenn der Job gespeichert ist

#### uf_new

##### Argumente

> -   dies ist die empfohlene Version für neue Programme
> -   es gibt keine Argumente
> -   stattdessen können/müssen vor dem Aufruf folgende
>     Instancevariablen belegt werden:
> -   iuo_new_applenv
> -   ist beim Einspoolen aus einem interaktiven Window zu verwendet
> -   iuo_new_job bleibt dann unbelegt
> -   in der weiteren Beschreibung wird dann von der "ApplEnv- Variante
>     gesprochen"
> -   iuo_new_job
> -   ist zu verwendet, wenn ein Job einen weiteren Job einspoolt
> -   iuo_new_applenv bleibt dann unbelegt
> -   in der weiteren Beschreibung wird dann von der "Job- Variante
>     gesprochen"
> -   is_new_erz_cli_hostname
> -   wenn unbelegt:
> -   in der ApplEnv- Variante lt. Rechner, auf dem das Programm bzw.
>     der Terminalclient bei Terminalserver läuft
> -   in der Job- Variante lt. pfu_job
> -   is_new_usr_cd, is_new_applpers_cd
> -   es muss entweder jede oder keine dieser Variablen verwendet werden
> -   wenn unbelegt:
> -   in der ApplEnv- Variante lt. Anmeldung lt. iuo_new_applenv
> -   in der Job- Variante lt. pfu_job
> -   datetime idtm_new_StartAb
> -   wenn unbelegt:
> -   in der ApplEnv- Variante dat_min
> -   in der Job- Variante lt. pfu_job
> -   is_new_will_nachricht_jn
> -   ist 'j' für true und 'n' für false
> -   wenn unbelegt:
> -   in der ApplEnv- Variante "n"
> -   in der Job- Variante lt. pfu_job
> -   ii_new_mfa1_nr, ii_new_mfa2_nr, ii_new_mfa3_nr
> -   es muss entweder jede oder keine dieser Variablen verwendet werden
> -   wenn unbelegt:
> -   in der ApplEnv- Variante lt. Anmeldung lt. iuo_new_applenv
> -   in der Job- Variante lt. pfu_job
> -   is_new_druck_nr
> -   darf , wenn ein Ausdruck erfolgt, nur in der Job- Variante
>     unbelegt sein und wird dann lt. pfu_job belegt
> -   Dient als Druck- Nummer für den Ausdruck, falls diese nicht im
>     Jobwindow ermittelt wird.
> -   Wird in dw_JobObj standardmäßig herangezogen
> -   kann im Job- Window ausgelesen werden
> -   ist z.B. eine Auftragsnummer, Lieferscheinnummer oder
>     Rechnungsnummer
> -   is_new_verarbart_kz
> -   darf nur in der Job- Variante unbelegt sein und wird dann lt.
>     pfu_job belegt
> -   is_new_windowname
> -   muss ausgefüllt werden
> -   is_new_funktional
> -   wenn nict leer und nicht null ( zum Starten des Jobs und für das
>     Einsehen des resultierenden Ausdrucks muss die Berechtigung für
>     (as_WindowName, as_funktional) vorhanden sein
> -   is_new_drucker_cd
> -   Drucker lt. Tabelle pfu_drucker für Ausdrucke
> -   es gibt folgende spezielle Bedeutungen:
> -   "kein ausdruck"
> -   es erfolgt kein Ausdruck sondern nur das Erzeugen des PDF- Files
>     und dessen Archivierung
> -   "laut zuordnung"
> -   wenn es eine Zuordnung gibt wird Drucker über diese ermittelt
>     (Dies erfolgt in dw_JobObj.uf_print)
> -   gibt es keine Zuordnung, erfolgt kein Ausdruck sondern nur das
>     Erzeugen des PDF- Files und dessen Archivierung.
> -   wenn unbelegt:
> -   in der ApplEnv- Variante "laut zuordnung"
> -   in der Job- Variante lt. pfu_job
> -   is_new_lade_cd
> -   Lade lt. Tabelle pfu_drucker_lade für Ausdrucke
> -   ist abhängig von der Belegung von is_new_drucker_cd zu belegen:
> -   lt. Job ( nicht belegen - wird lt. pfu_job belegt
> -   "kein ausdruck", "laut zuordnung" ( nicht belegen - wird mit Blank
>     belegt
> -   sont ( muss belegt sein
> -   is_new_wiedereinspool_jn
> -   wiedereinspoolmechanismus - siehe Datenbankbeschreibung
> -   wenn nicht belegt, wird 'n' angenommen
> -   in der Job- Variante wird "n" angenommen
> -   bei 'n' werden die folgenden 3 Felder ignoriert
> -   is_new_wiedereinspool_ab
> -   Kennzeichen für das Bezugsdatum für idc_new_wiedereinspool_std:
>     'j' ( Job
> -   start_ab_datz des alten Jobs 'm' ( Monatsultimo
> -   Zeit lt. start_ab_datz des alten Jobs
> -   Datum ist der nächstfolgende Monatsultimo 'w' ( Woche
> -   Zeit lt. start_ab_datz des alten Jobs
> -   Datum ist der nächstfolgende Montag 'y' ( Year (Jahr)
> -   Zeit lt. start_ab_datz des alten Jobs
> -   Datum ist der nächstfolgende Jahreserste
> -   decimal idc_new_wiedereinspool_std
> -   idt_new_StartAb des des wiedereingespoolten Jobs liegt so viele
>     Stunden nach dem is_new_wiedereinspool_ab entsprechenden Zeitpunkt
> -   ist allerdings dieser Zeitpunkt nicht in der Zukunft, wird so oft
>     idc_new_wiedereinspool_std addiert, bis dies der Fall ist
> -   decimal idc_new_maxstartdanach_std
> -   beim Starten des (wiedereingespoolten) Jobs wird die Zeispanne
>     zwischen idt_new_StartAb und jetzt betrachtet. Von dieser Zahl
>     wird solange idc_new_wiedereinspool_std abgezogen, bis die Zahl
>     kleiner als adc_maxstartdanach_std und größer oder gleich 0 ist.
>     Ist die erhaltene Zahl größer als idc_new_maxstartdanach_std, wird
>     der Job nicht gestartet.
> -   Kommunikationsdaten für Email, Fax
> -   wenn unbelegt:
> -   in der ApplEnv- Variante leer
> -   in der Job- Variante lt. pfu_job
> -   string is_new_komid_wert
> -   string is_new_zu_handen
> -   string is_new_betreff
> -   wenn unbelegt:
> -   in der ApplEnv- Variante lt. ApplikationsPerson des Jobs
> -   in der Job- Variante lt. pfu_job
> -   string is_new_absender
> -   string is_new_von_emailadr
> -   string is_new_bcc_emailadr .
> -   diese Version ist nur aus Abwärtskompatibilitätsgründen vorhanden
>     o auo_ApplEnv auo_job
> -   adt_StartAb
> -   as_will_nachricht_jn
> -   ai_mfa1_nr
> -   ai_mfa2_nr
> -   ai_mfa3_nr
> -   as_DruckNr
> -   as_verarbart_kz
> -   as_WindowName
> -   as_funktional
> -   as_DruckerCd
> -   as_LadeCd
> -   as_wiedereinspool_jn
> -   as_wiedereinspool_ab
> -   adc_wiedereinspool_std
> -   adc_maxstartdanach_std

##### Rückgabewert

-   (None)

##### Beschreibung

-   Legt einen neuen Job im Arbeitsspeicher an.
-   für den so angelegten Job muss dann uf_Save aufgerufen werden,
    sodass er in der Datenbank gespeichert ist
-   darf nicht aufgerufen werden, wenn ein mittels uf_new angelegter Job
    noch nicht mittels uf_Save gespeichert oder mittels uf_Reset
    zurückgesetzt worden ist
-   darf nicht aufgerufen werden, wenn ein mittelsuf_Retrieve
    eingelesener Job noch nicht mittels uf_Reset zurückgesetzt worden
    ist

#### uf_Reset

##### Argumente

##### Rückgabewert

##### Beschreibung

-   Setzt alles zurück, sodass uf_new bzw. uf_Retrieve aufgerufen werden
    können

#### uf_Retrieve

##### Argumente

-   adc_job_snr
-   Die Nummer des Jobs, unter dem der Job gespeichert ist (lt. uf_save)

##### Rückgabewert

-   boolean
-   true ( Job gefunden

##### Beschreibung

-   Holt einen Job mit all seinen Parametern und deren Werten aus der
    Datenbank.
-   darf nicht aufgerufen werden, wenn ein mittels uf_new angelegter Job
    noch nicht mittels uf_Save gespeichert oder mittels uf_Reset
    zurückgesetzt worden ist

#### uf_Save

##### Argumente

##### Rückgabewert

-   long

-   0 ( job_snr, Speichern des Jobs ist geglückt

-   -1 ( Fehler beim Speichern

##### Beschreibung

-   speichert den aktuellen Job mit all seinen Parametern und deren
    Werten in der Datenbank, d.h. in den Tabellen pfu_job, pfu_job_par
    und \## pfu_job_par_wert.

-   führt "commit using sqlca;" durch, wenn keine Transaktion offen ist

#### uf_Save4UPD

##### Argumente

##### Rückgabewert

-   boolean

##### Beschreibung

-   speichert den aktuellen Job mit deren Werten in der Datenbank, d.h.
    in der Tabelle pfu_job
-   führt "commit using sqlca;" durch, wenn keine Transaktion offen ist
-   schickt UPD-Signal an die Jobverarbeiter

#### uf_Set_StartAbDatz

##### Argumente

-   adtm_start_ab_datz
-   as_error

##### Rückgabewert

-   boolean

##### Beschreibung

-   setzt das Start-Ab-Datum des aktuellen Jobs lt. übergebenem
    Argument.

## Variables

## iuo_ParList

-   Darf ausschließlich zum Zugriff auf die freigegebenen
    Funktionen/Events/Variablen von cst_ParList verwendet werden!!!

-   cst_ParList

-   Parameter des Jobs

-   kann nach create befüllt werden

-   kann nach uf_retrieve ausgelesen werden

-   der Wert von iuo_ParList darf auf keinen Fall verändert werden!!!

-   string is_new_erz_cli_hostname // Client- Host des Erzeugers (bei
    Terminalsession der Terminalclient, sonst der Applikationsserver)
    \## string is_new_usr_cd, is_new_applpers_cd

## cst_Logfile (sys)

-   dient zum Protokollieren von Auswertungen in eine Datei im
    Filesystem.

### Functions

#### uf_closelog

##### Argumente

-   as_Praefix
-   Name bzw. Praefix des Logfiles

##### Rückgabewert

-   boolean
-   das schließen des Logfiles war ok.

#### uf_openlog

##### Argumente

-   as_Praefix
-   Name bzw. Praefix des Logfiles
-   Beispiele:
-   druckerdaemon
-   etikettendaemon
-   outlookaddin
    -   ab_newformat
-   optional
-   gibt an ob die Log Datei im neuen oder im alten Format geschrieben
    werden soll.
-   Das neue Format ist ähnlich aufgebaut wie syslog unter Unix

##### Rückgabewert

-   boolean
-   das öffnen des Logfiles war ok.

#### uf_write2log

##### Argumente

-   as_Praefix
-   Name bzw. Praefix des Logfiles
-   Beispiele:
-   druckerdaemon
-   etikettendaemon
-   outlookaddin
    -   as_Title
    -   Titel der im Logfile stehen soll
    -   as_Message
    -   Nachricht die im Logfile stehen soll
    -   ai_Icon
-   Icon welche die Wichtigkeit der Nachricht darstellt
-   Beispiele:
-   Information!
-   Warning!
-   StopSign!
-   Question!
-   None!

## cst_OleObject

-   soll die Basisklasse aller Klassen, die ein OLE-Objekt kapseln, sein
-   die Ableitung muss das EventScript von FullyQualifiedClassname
    überschreiben
-   siehe Verwendung von COM- Klassen (PCS.Interop ...)

## Events

## FullyQualifiedClassname

##### Argumente

##### Rückgabewert

-   string
-   der volle Klassen- Name der OLE- Klasse z.B.
    "Pcs.Interop.InteropHelper"

## Ableitung

-   muss überschrieben werden

##### Beschreibung

-   ist bei der Implementierung einer abgeleiteten Klasse zu verwenden
-   dadurch wird definiert, welche Ole- Klasse instanziert wird
-   hier können die änderbaren Instancevariablen gesetzt werden

### Functions

#### uf_ConnectToNewObject

##### Argumente

-   keine Argumente

##### Rückgabewert

-   none

##### Beschreibung

-   instanziert eine OLE-Klasse, erzeugt also ein neues OLE-Objekt
-   ist unbedingt unter Try/Catch aufzurufen

#### uf_DisconnectObject

##### Argumente

-   keine Argumente

##### Rückgabewert

-   none

##### Beschreibung

-   trennt die Verbindung zu einem OLE-Objekt, welches dadurch
    eliminiert wird
-   ist unbedingt unter Try/Catch aufzurufen

## cst_OleWrapper (sys)

-   ACHTUNG - nicht mehr verwenden - wurde durch cst_OleObject abgelöst
-   soll die Basisklasse aller Klassen, die ein OLE-Objekt kapseln, sein
-   die Ableitung muss das EventScript von FullyQualifiedClassname
    überschreiben
-   siehe uf_SetLastError für die Implementierung von Zugriffen auf das
    OleObjekt
-   ACHTUNG : OLE- Objekte können jetzt direkt aus einem w_ApplObj
    verwendet werden - siehe wf_CreateOleObject

## Events

## FullyQualifiedClassname

##### Argumente

##### Rückgabewert

-   string
-   der volle Klassen- Name der OLE- Klasse z.B.
    "Pcs.Interop.InteropHelper"

## Ableitung

-   muss überschrieben werden

##### Beschreibung

-   ist bei der Implementierung einer abgeleiteten Klasse zu verwenden
-   dadurch wird definiert, welche Ole- Klasse instanziert wird
-   hier können die änderbaren Instancevariablen gesetzt werden

### Functions

#### uf_ConnectToNewObject

##### Argumente

-   wenn eines der Argumente weggelassen wird, sind alle wegzulassen ((
    Aufruf ohne Argumente) - dies ist der Normalfall, wenn die Funktion
    von der Applikation aufgerufen wird
-   Die Version mit den Argumenten ist nur dann nötig, wenn mehrere Ole-
    Objekte verwendet werden müssen
    -   as\_ FullyQualifiedClassname
-   der volle Klassen- Name der OLE- Klasse z.B.
    "Pcs.Interop.InteropHelper"
-   kann weggelassen werden, dann wird der Returnwert des Events
    FullyQualifiedClassname herangezogen
    -   aole\_
-   OleObject
-   by Reference
-   wird von der Funktion mit dem erzeugten Ole- Objekt belegt
-   kann weggelassen werden:
-   dann wird die InstanceVariable iole\_ belegt
-   die Klasse kann dann also nur ein OleObjekt verwenden
-   es kann auch explizit iole\_ übergeben werden

##### Rückgabewert

-   boolean
-   wenn OleObjekt erfolgreich erzeugt ( true
-   sonst ( false und die Fehlermeldung kann mittels uf_GetLastError
    ausgeleden werden

##### Beschreibung

V instanziert eine OLE-Klasse, erzeugt also ein neues OLE-Objekt

#### uf_DisconnectObject

##### Argumente

-   der Aufruf ohne Argumente ist der Normalfall, wenn die Funktion von
    der Applikation aufgerufen wird
-   Die Version mit den Argumenten ist nur dann nötig, wenn mehrere Ole-
    Objekte verwendet werden müssen
    -   as\_ FullyQualifiedClassname
-   der volle Klassen- Name der OLE- Klasse z.B.
    "Pcs.Interop.InteropHelper"
-   kann weggelassen werden, dann wird der Returnwert des Events
    FullyQualifiedClassname herangezogen
    -   aole\_
-   OleObject
-   by Reference
-   wird von der Funktion mit dem erzeugten Ole- Objekt belegt
-   kann weggelassen werden:
-   dann wird die InstanceVariable iole\_ belegt
-   die Klasse kann dann also nur ein OleObjekt verwenden

##### Rückgabewert

-   boolean
-   Erfolgreiche Trennung ( true
-   sonst ( false und die Fehlermeldung kann mittels uf_GetLastError
    ausgeleden werden

##### Beschreibung

-   trennt die Verbindung zu einem OLE-Objekt, welches dadurch
    eliminiert wird

#### uf_GetLastError

##### Argumente

##### Rückgabewert

-   string
-   letzte Fehlermeldung
-   wird im Zusammenhang mit uf_SetLastError verwendet
-   nicht mehr verwenden - es sollte jetzt das unter uf_ReThrowException
    beschriebene Schema verwendet werden

#### uf_ReThrowException

##### Argumente

-   as_FunctionOrEventName
-   as_Context
-   beschreibt die Position innerhalb der Funktion
-   bei lediglich druchgeschliffenen Funktionen kann hier "" übergeben
    werden
    -   a_ex
-   Throwable
-   eine mittels Try/Catch abgefangene Exception

##### Rückgabewert

-   none

##### Beschreibung

-   wird bei der Implementierung von Funktionen/Eventscripts von von
    cst_OleWrapper abgeleiteten Klassen benötigt, wenn das neue Schema
    verwendet wird und dieses Schema sollte immer verwendet werden

-   ein Zugriff auf ein Property bzw. eine Method des Ole-Objektes
    sollte folgendermaßen erfolgen, wenn nicht sicher ist, dass bei der
    Verarbeitung kein Fehler geschieht:

-   Bsp.: Try as_x = iole\_.x iole\_.y = ai_y iole\_.z(1,"asdf") Catch (
    throwable t ) uf_ReThrowException ( "uf_kurti", "", t ) End Try
    return true

-   siehe cst_OleWrapperException

-   für einen Fehler, der nicht über TyCatch gefangen worden ist siehe
    \#### uf_ThrowException

-   Anmerkung zu den .NET- Funktionen:

-   wenn diese kein Try-Catch haben, wird die Exception über OLE
    weitergeleitet - allerdings geht der Callstack verloren

-   wenn für die Fehlerdiagnose ein Callstack nötig ist, muss dort
    folgendermaßen vorgegangen werden - Bsp (VB.NET): Try ... Catch e as
    Excetion Throw new Exception ( e.ToString() ) End Try

-   Anmerkung: es sind natürlich auch elegantere Methoden als e.ToString
    denkbar - dazu hatten wir bisher allerdings keine Zeit

-   die Verwendung der cst_OleWrapper- Funktion(en) in der Applikation
    sollte jetzt folgendermaßen geschehen - Bsp.: Try ... luo_XY.uf_ABC
    ( ... ) ... luo_XY.uf_ABC ( ... ) ... luo_XY.uf_Finish ( ... ) ...
    Catch ( cst_OleWrapperException ex ) wf_Error ( "wf_lmn", "Auslesen
    ..", ex.uf_GetFullText() ) return false End Try

-   siehe auch

#### uf_SetLastError

##### Argumente

-   a_ex
-   Throwable
-   eine mittels Try/Catch abgefangene Exception

##### Rückgabewert

-   none

##### Beschreibung

-   ACHTUNG: dieses Schema sollte nicht mehr verwendet werden - es
    sollte jetzt das unter uf_ReThrowException beschriebene Schema
    verwendet werden
-   belegt die mittels uf_GetLastError auslesbare Fehlermeldung mit dem
    Fehlertext von a_ex
-   ein Zugriff auf ein Property bzw. eine Method des Ole-Objektes
    sollte folgendermaßen erfolgen, wenn nicht sicher ist, dass bei der
    Verarbeitung kein Fehler geschieht:
-   Bsp.: Try as_x = iole\_.x iole\_.y = ai_y iole\_.z(1,"asdf") Catch (
    throwable t ) uf_SetLastError ( t ) return false End Try return true

#### uf_ThrowException

##### Argumente

-   as_FunctionOrEventName
-   as_Context
-   beschreibt die Position innerhalb der Funktion
-   bei lediglich druchgeschliffenen Funktionen kann hier "" übergeben
    werden
    -   as_error
-   Fehlerbeschreibung

##### Rückgabewert

-   none

##### Beschreibung

-   kommt zum Einsatz, wenn ein Fehler, der nicht über Try-Catch
    gefangen worden ist auftritt - wie uf_ReThrowException, außer dass
    hier ein Fehlertext statt einer Exception übergeben wird

## Variables

## iole\_

-   Darf nicht verändert werden!
-   das Ole-Objekt, das mittels uf_ConnectToNewObject ohne Argumente
    belegt worden ist
-   wenn uf_ConnectToNewObject mit Argumenten verwendet worden ist, ist
    die Variable ggf. nicht belegt

## cst_OleWrapperException (sys)

-   war ein Fehltritt bei der Implementierung von cst_xmlwriter -
    anderswo nicht verwenden !
-   siehe cst_OleWrapper.uf_ReThrowException

### Functions

-   hier sind nur die bei der Applikationsprogrammierung oder der
    implementierung einer von cst_OleWrapper abgeleiteten Klasse
    benötigten Funktionen beschrieben

#### uf_GetFullText

##### Argumente

##### Rückgabewert

-   String
-   liefert den gesamten Fehlertext der Exception

## cst_Message

-   es gibt genau ein Objekt dieser Klasse das über die Powerbuilder
    Systemvariable message anzusprechen ist

## Events

## Initialize

##### Argumente

##### Rückgabewert

-   None

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   wird beim Start der Applikation aufgerufen
-   hier können die änderbaren Instancevariablen gesetzt werden

## StringInputPlaceholder

##### Argumente

-   auo_ae
-   as_colname
-   ai_anzstellen
-   as_sprache
-   ai_anmeld
-   as_placeholder
-   as_result
-   By Refernce

##### Rückgabewert

-   Boolean
-   false ( Standard
-   true ( wenn Indiv etwas ausprogrammiert ist, muss in diesen Zweig
    true zurück kommen

## Ableitung

-   darf erweitert werden

##### Beschreibung

-   Hier können analog zu `anmeldusr` weitere Platzhalter
    ausprogrammiert werden

### Functions

## uf_CloseApplicationServerProxy Connection()

##### Argumente

##### Rückgabewert

##### Beschreibung

-   Es wird die Verbindung zum ApplicationServerProxy geschlossen.
-   Notwendig: Pcs.ApplicationServerProxy.dll registrieren

## uf_ConnectApplicationServerProxy ()

##### Argumente

-   as_error
-   by ref

##### Rückgabewert

-   Boolean

##### Beschreibung

-   Es wird eine Verbindung zum ApplicationServerProxy hergestellt.
-   Notwendig: Pcs.ApplicationServerProxy.dll registrieren

#### uf_InteractiveDiag

## wurde nach cst_ApplEnv verschoben -- siehe uf_InteractiveDiag

#### uf_RichText

##### Argumente

-   keine

##### Rückgabewert

-   cst_RichText

##### Beschreibung

-   liefert das Standard- mäßig zu verwendende cst_RichText- Objekt

-   in cst_Message gibt es eine private Instance- Variable vom Typ \##
    cst_RichText

-   die Funktion instanziert diese, wenn dies noch nicht erfolgt ist,
    und liefert das Objekt zurück

#### uf_RichText

##### Argumente

-   keine

##### Rückgabewert

-   cst_RichText

##### Beschreibung

-   liefert das Standard- mäßig zu verwendende cst_RichText- Objekt

-   in cst_Message gibt es eine private Instance- Variable vom Typ \##
    cst_RichText

-   die Funktion instanziert diese, wenn dies noch nicht erfolgt ist,
    und liefert das Objekt zurück

## uf_systemerror ()

##### Argumente

##### Rückgabewert

##### Beschreibung

-   im SystemError- Event- Script der Applikation sollte genau eine
    Zeile, nämlich
    -   message.uf_systemerror() stehen

## uf_UiHelper ()

##### Argumente

##### Rückgabewert

-   cst_UiHelper

##### Beschreibung

-   liefert eine funktionsbereite Instanz von cst_UiHelper

## Variables

## ib_ApplicationServerConnected

-   Applikation ist mit einem ApplicationServerProxy verbunden
-   Darf nicht verändert Werden !!!!

## ib_mde

-   Applikation ist im MDE- Modus
-   Darf nicht verändert Werden !!!!

## ii_MaxDsDbColNameLen

-   Maximale Länge des DbColname einer Column im DWO
-   0 -\> keine Einschränkung
-   Standard ist 18
-   kann im Event Initialize anderweitig belegt werden

## iuo_ae

-   dient zum Zugreifen auf Shared- Daten bzw. auf Funktionen, die nur
    Shared- Daten verwenden, von cst_ApplEnv
-   Beispiele:
    -   uf_halt

## iuo_FileSysFun

-   dient zum Zugreifen auf die Funktionen von cst_FileSysFunctions
-   cst_FileSysFunctions ist leider (noch?) nicht dokumentiert
-   die Funktionen sind wie globale Funktionen zu verwenden
-   cst_FileSysFunctions muss nirgends gesondert instanziert werden

## Größenangaben für Queryfenster im MDE- Modus

-   folgende Variable mit ihren Standardbelegungen:
    -   ii\_

w_ApplObj.event open: itab_ApplObj.y = -68 // restliche Verschiebung zu
y- Verschiebung x = -36 y = -132 // mehr nicht möglich

-   die Werte sind alle in Powerbuilderunits
-   können im Event Initialize anderweitig belegt werden

## Texte für Anmeldefenster unD Beenden der Applikation

-   absoluter Pfusch für Premac
-   folgende Variable mit ihren Standardbelegungen:
    -   is_TxtAnmeldAnmelden = "Anmelden"
    -   is_TxtAnmeldAbmelden = "Abmelden"
    -   is_TxtAnmeldAbbrechen = "Abbrechen"
    -   is_TxtApplikationBeenden = "Wollen Sie wirklich die Applikation
        beenden?"
-   können im Event Initialize anderweitig belegt werden

## cst_ParList

-   dient zu Übergabe von Parametern an ein anderes Objekt
-   besonders unterstützt wird die Übergabe von durch Benutzereingabe
    generierten SQL- Where- Bedingungen
-   Die Übergabeparameter mit ihren Werten können in der Datenbank zu
    einem Job gespeichert und abgerufen werden.
-   das System kann auch mehrere cst_ParList- Objekte zu einer Liste
    verketten

### Functions

#### uf_AddPar

##### Argumente

-   as_ParName
-   Names des Parameters
    -   as_Tabelle
-   kommt nur zur Anwendung, wenn as_db_col_expr leer ist bzw.
    weggelasen wird - siehe bei as_db_col_expr
    -   as_dattyp
-   Datentyp, wie er in der Tabelle pfu_col definiert wird
-   kommt nur zur Anwendung, wenn es für as_ParName keinen pfu_col-
    Eintrag gibt
    -   as_wohin
-   String in einem SQL- Statement, welcher durch einen aus allen ihm
    zugeordneten Parametern generierten Boolschen Ausdruck für die
    Where- Clause ersetzt werden soll. D.h., daß alle Parameter mit dem
    gleichen as_wohin einen Ausdruck ergeben.
    -   as_op
-   Vergleichsoperator: "\<", "\<=", "\>", "\>=", "\<\>", "=", "like",
    "not like", "between", "in", "is null", "is not null",
-   Anmerkung Benutzereingabe im Queryfenster:
-   !\~ ... not like
-   \~ .... like
-   != ... wie \<\> ( also ungleich
-   \<\> ... ungleich
-   ? ... is null
-   !? ... is not null
-   a;b;c ... in ( "a", "b", "c" )
-   !a;b;c ... not in ( "a", "b", "c" )
-   a:b ... between "a" and "b"
-   !a:b ... not between "a" and "b"
    -   as_db_col_expr
-   mit diesem Ausdruck wird die Where- Bedingung angefrtigt
-   Bsp.: für die offene Menge der Auftragsposition:
    auf_pos.auf_bst_mg - auf_pos.auf_loesch_mg - auf_pos.auf_lief_mg
-   ist auch dann notwendig, wenn es 2 Parameter für den gleichen
    Columnnamen gibt - dazu ein Bsp.:
-   select ... from auf_pos, auf ein_auf, auf ab_auf
-   1.  Parameter für ein_auf.kunde_cd ( ein_kunde_cd
-   2.  Parameter für ab_auf.kunde_cd ( ab_kunde_cd
-   im Select muss dann
    -   ein_auf.kunde_cd
    -   ab_auf.kunde_cd stehen - dies ist jeweils as_db_col_expr zu
        übergeben
-   kann weggelassen werden und wird dann mit \> as_Tabelle + "." +
    as_ParName, wenn as_Tabelle nicht leer ist \> as_ParName sonst
    belegt

##### Rückgabewert

-   (None)

##### Beschreibung

-   Bekanntgabe eines Parameters
-   Abhängig von as_op muß danach 0 bis n mal die Funktion uf_AddParWert
    aufgerufen werden

#### uf_AddParWert

##### Argumente

-   aa_wert

##### Rückgabewert

-   (None)

##### Beschreibung

-   Bekanntgabe eines Wertes zum letzten Aufruf von uf_AddPar, siehe
    dort

#### uf_Copy

##### Argumente

-   (None)

##### Rückgabewert

-   cst_Parlist
-   ParList in die Kopiert werden soll

##### Beschreibung

-   Kopiert alle vorhandenen Parmeter auf die angegebene ParList
-   Kann verwendet werden um z.B. die Auswahlkriterien eines
    Dialagprogrammes an ein Batch-Programm zu übergeben.

#### uf_GetMfa

##### Argumente

-   as_mfa1_nr
-   by reference
-   wenn es einen Parameter, dessen Operator "=" ist und dessen Name
    gleich dem ersten PKeyColumnNamen desMFA- Bestandteils 1 ist, gibt (
    Wert des Parameters
-   sonst ( 0
    -   as_mfa2_nr
-   wenn as_mfa1_nr \<\> 0 ist, dann Ermittlung wie as_mfa1_nr
    allerdings für den MFA- Bestandteil 2
-   sonst ( 0
    -   as_mfa3_nr
-   Ermittlung wie as_mfa2_nr allerdings für den MFA- Bestandteil 3

##### Rückgabewert

-   (None)

##### Beschreibung

-   siehe Parameter

#### uf_GetPar

##### Argumente

-   as_ParName

##### Rückgabewert

-   any
-   null, wenn: \> Parameter nicht vorhanden ist \> Operator nicht "="
    ist ACHTUNG: null kommt als any- Null und kann nicht in eine
    Variable, deren Typ nicht any ist, eingelesen werden - es erfolgt
    sonst Totalabsturz!!!!

##### Beschreibung

-   Dient zum Auslesen eines Parameters dessen Operator "=" ist

#### uf_GetPar

##### Argumente

-   as_ParName
-   reference as_db_col_expr
-   lt. pfu_win_qcol
    -   reference as_op
-   wie bei uf_AddPar
    -   reference ai_AnzWert
-   Anzahl der Werte zum Parameter, welche mittels uf_GetParWert
    ausgelesen werden können

##### Rückgabewert

-   boolean
-   false ( Parameter nicht vorhanden

##### Beschreibung

-   Dient zum Auslesen eines Parameters dessen Operator nicht bekannt
    bzw. nicht "=" ist
-   Liefert den Operator und die Anzahl der Werte, welche mittels
    uf_GetParWert auszulesen sind

#### uf_GetParWert

##### Argumente

-   ai_nr
-   die Nummer des zu lesenden Wertes
-   diese kann 1 bis ai_AnzWert lt. uf_GetPar sein

##### Rückgabewert

-   any

##### Beschreibung

-   Dient zum Auslesen eines Wertes eines Parameters

#### uf_GetWhere

##### Argumente

-   reference as_wohin
-   reference as_where

##### Rückgabewert

-   boolean
-   false ( es existiert keine (weitere) Expression für die Where-
    Clause true ( as_where wurde mit einer Expression für die Where-
    Clause belegt

##### Beschreibung

-   Liefert eine boolean Expression für die Where- Clause, welche alle
    Parameter mit gemeinsamem as_wohin heranzieht.
-   Das Auslesen dieser Expressions muß mit einem uf_GetWhereStart-
    Aufruf beginnen
-   Danach wird solange uf_GetWhere aufgerufen, bis die Funktion false
    liefert.

#### uf_GetWhere

##### Argumente

-   as_wohin
-   Es soll eine boolsche Expression für die Where- Clause geliefert
    werden, welche alle Parameter mit diesem as_wohin heranzieht
    -   atr\_
-   Die Expression wird in der Syntax des atr\_ entsprechenden
    Datenbanksystems aufgebaut.
    -   reference as_where

##### Rückgabewert

-   boolean
-   false ( es existiert keine derartige Expression für die Where-
    Clause true ( as_where wurde mit einer Expression für die Where-
    Clause belegt

##### Beschreibung

-   Der Aufruf ist unabhängig von einem uf_GetWhereStart- Aufruf

#### uf_GetWhereStart

##### Argumente

-   atr\_
-   der Insert erfolgt mit dieser Transaction

##### Rückgabewert

-   (None)

##### Beschreibung

-   siehe uf_GetWhere ( as_wohin, as_where )

#### uf_insert_pfu_t_job_par

##### Argumente

-   atr\_
-   mit atr\_ erfolgt der insert ino pfu_t_job_par - siehe unten.
    -   adc_job_snr
-   für diesen Job erfolgt der Insert - siehe unten

##### Rückgabewert

-   boolean
-   true bei Erfolg sonst false

##### Beschreibung

-   ist eine Hilfsfunktion für das Andrucken der Job-Parameter auf einem
    Report
-   folgende Handhabung:
-   die Funktion wird im action- Event-Script von w_JobObj aufgerufen
-   in jenem Report, in dem die Jobparameter angedruckt werden sollen,
    wird ein Subreport mit dem DWO d_lst_pfu_t_job_par, welches sich
    ebenfalls in der pfu_fun befindet, aufgerufen
-   dieser hat ein Retrievel_Argunent job_snr und liest die Rows in
    pfu_t_job_par für die übergebene job_snr aus
-   zum Übergeben der job_snr an den Subreport steht die Funktion
    gf_CurrentJobSnr zur Verfügung
-   ACHTUNG: die Funktion macht kein tr_begin !!!!!
-   hier ist anzudenken, die über einen Parameter zu steuern
-   die Einträge in pfu_t_job_par werden nach der Ausführung des action-
    Event-Scripts von der pfu_fun gelöscht - ACHTUNG: dies fehlt in der
    pfu_fun noch und wird mit a 11587 bei Bedarf erledigt !!!
-   derzeit kann man sich mit folgendem Ablauf behelfen: . wf_TrBegin()
    . uf_insert_pfu_t_job_par . ll_AnzRow = idw_job.uf_Retrieve("") .
    wf_TrRollback()

#### uf_reset

##### Argumente

##### Rückgabewert

-   (None)

##### Beschreibung

-   löscht alle Parameter

## cst_PdfViewer

-   dient zur Anzeige eines PDF- Dokuments innerhalb einer Tabpage
-   ANMERKUNG:
-   cst\_'s innerhalb einer Tabpage haben keine Tab-Order und werden vom
    Presentation- Mechanismus ignoriert
-   cst_PdfViewer stellt Funktionen zur Verfügung um dies manuell z.B.
    im OnSetPresentation des Windows auszuprogrammieren
-   nachdem cst_PdfViewer eher selten verwendet werden wird, gibt es
    keine detaillierte Doku
-   Als Vorlage kann w_pfu_job_druck herangezogen werden - suche nach
    \`uo_dok.´

## cst_RichText (sys) (Pcs.Interop)

-   enthält Funktionen zum Arbeiten mit RichText
-   werden 1:1 von Pcs.Interop.Richtext.RichTextHelper durchgeschliffen
-   siehe dort

## cst_SerCom (sys)

-   dient zur Kommunikation über eine Serielle Schnittstelle.

### Functions

#### uf_FClose

##### Argumente

-   aul_Handle
-   lt. uf_FOpen

##### Rückgabewert

-   boolean
-   true, wenn ok sonst false

#### uf_FOpen

##### Argumente

-   aul_Handle by Reference
-   erhält einen Windows- Filehandle (kann als eindeutige interne Nummer
    für die Verbindung betrachtet werden)
    -   as_ComPort
-   z.B. "com1"
    -   al_baudrate
-   derzeit implementiert (wird bei Bedarf erweitert): 1200, 2400, 4800,
    9600, 14400, 19200
-   0 wird zu 9600
    -   ai_ByteSize
-   7 bzw. 8
    -   ai_Parity
-   0: no/keine, 1: even/gerade, 2: odd/ungerade
    -   al_TimeOut
-   Timeout für Lesebefehle in Sekunden
-   0 ist kein Timeout (= ewig warten)
    -   as_ErrorTxt by Reference
-   erhält im Fehlerfall eine Fehlerbeschreibung

##### Rückgabewert

-   boolean
-   true, wenn ok sonst false

#### uf_FRead

##### Argumente

-   aul_Handle
-   lt. uf_FOpen
    -   as_gelesen by Reference
-   Text, der von der Schnittstelle gelesen wurde
    -   al_ZuLesen
-   Anzahl der zu lesenden Zeichen

##### Rückgabewert

-   boolean
-   true, wenn genau al_ZuLesen Zeichen gelesen wurden, sonst false

## Anmerkung

-   Kann derzeit nur verwendet werden, wenn man genau weiß, wie viele
    Zeichen auf der Schnittstelle zu erwarten sind.
-   Funktionalität wird bei Bedarf erweitert

#### uf_FWrite

##### Argumente

-   aul_Handle
-   lt. uf_FOpen
    -   as_text
-   Text, der zur Schnittstelle geschickt werden soll
    -   ab_CrNl
-   es soll Cr + Nl nachgeschickt werden
-   kann weggelassen werden und wird dann mit true angenommen

##### Rückgabewert

-   boolean
-   true, wenn ok sonst false

## cst_TcpHelper

-   Stellt die Infrastruktur zur Kommunikation via TCP/IP zur Verfügung.
-   Abgeleitet von cst_OleObject
-   Es ist außer dem FullyQualifiedClassname- Event nichts übersteuert -
    die COM- Klasse ist Pcs.Interop.Socket.TcpHelper
-   alle Funktionalitäten stehen direkt über die COM- Klasse zu
    Verfügung
-   siehe Verwendung von COM- Klassen (PCS.Interop ...)

## cst_UidCheck

-   Objekt checkt die Uid-Nummer beim Finzanzamt
-   Vor der Verwendung muss uf_create aufgerufen werden
-   im pfu_kennsatz müssen die Felder fion_teilnehmer_id bis
    proxy_password eingetragen werden
-   ACHTUNG: einige Felder sind verschlüsselt abgespeichert und können
    daher nur mit dem Verwaltungsprogramm eingetragen werden!!!
-   Siehe pfu_fun_db.doc
-   Für jeden Host, auf dem TC läuft muss ein Zertifikat installiert
    werden und dessen Pfad in pfu_host eingetragen werden
-   Das Zertifikat kann folgendermaßen beschafft werden: .
    https://finanzonline.bmf.gv.at/fon/ mittels Internet Explorer
    aufrufen . Auf das Schloss- Symbol klicken . Zertifikat anzeigen
    wählen . Zertifikat installieren werden (wenn man "Speicherort
    automatisch" wählt, wird das Zertifikat unter "andere Personen"
    abgelegt) . Internet-Optionen - Register Inhalte - Zertifikate -
    Register "andere Personen" (siehe oben) . Finanzonline.bmf.gv.at
    exportieren
-   Das Zertifikat sollte unter
    ?:`\PCS`{=tex}`\Daten`{=tex}`\Zertifikate `{=tex}ablegt werden
-   angeblich kann auf das Zertifikat auch via UNC- Pfad (auf anderem
    Rechner) zugegriffen werden
-   Achtung: per 8.7.14 gilt das Zertifikat nur bis zum 22.5.2016 !!!!!
-   Mit Aufgabe 7345 realisiert
-   Es ist mindestens
    P:`\InstallVorlagen`{=tex}`\Allgemein`{=tex}`\PCS`{=tex}
    Interop\\1.0.1`\Pcs`{=tex}.Interop.dll nötig

### Functions

#### uf_create

##### Argumente

##### Rückgabewert

-   Boolean
-   True: Wenn das Initialisieren des OleObjekts funktioniert hat.

##### Beschreibung

-   Muss für ein cst_uidcheck - Objekt aufgerufen werden bevor dieses
    verwendet wird.

#### uf_CheckUid

##### Argumente

-   as_eigene_uid
-   ist die Uid von der Firma, die die Abfrage startet
    -   as\_ uid
-   ist die UID die geprüft werden soll
    -   ab_request_address
-   ob auch der Name und die Adressfelder befüllt werden soll

##### Rückgabewert

-   "f" ( Fehler bei der Verarbeitung
-   "e" ( as_eigene_uid ist falsch
-   "u" ( as\_ uid ist falsch
-   "o" ( OK ( Prüfung ist gut gegangen

##### Beschreibung

-   Liefert den Status der Prüfung zurück
-   Nach dem Aufruf ist der Aufruf folgender Funktionen möglich:
-   wenn der Rückgabewert nicht = "o" ist ( uf_GetLastError
-   sonst wenn bei ab_request_address true übergeben worden ist:
    -   uf_GetName
    -   uf_GetAdressfeld

#### uf_GetLastError

##### Argumente

##### Rückgabewert

-   string

##### Beschreibung

-   bezieht sich auf den letzten uf_CheckUid- Aufruf (( es muss bereits
    ein solcher erfolgt sein - siehe dort)

#### uf_GetName

##### Argumente

##### Rückgabewert

-   string

##### Beschreibung

-   bezieht sich auf den letzten uf_CheckUid- Aufruf (( es muss bereits
    ein solcher erfolgt sein - siehe dort)
-   Liefert den Firmennamen lt. Finzanzamt zurück

#### uf_GetAdressfeld

##### Argumente

-   ai_index
-   Welches Addressfeld zurückgegeben werden soll (1-5)
-   Adressfelder haben keine bestimmte Reihenfolge da die Adressfelder
    vom Finzamt pro Land unterschiedlich belegt sind

##### Rückgabewert

-   string

##### Beschreibung

-   bezieht sich auf den letzten uf_CheckUid- Aufruf (( es muss bereits
    ein solcher erfolgt sein - siehe dort)
-   Liefert das Adressfeld lt. Finzanzamt zurück

## cst_UiHelper

-   eine Instanz muss via cst_Message. uf_UiHelper() besorgt werden!
-   stellt die Funktionen von Pcs.Interop.WindowsUi.WindowsUiHelper zur
    Verfügung

### Functions

#### uf_SendKeyCombination

##### Argumente

-   siehe w_ApplObj.wf_DefineHotKey

    -   as_KeyName
    -   ab_shift
    -   ab_control
    -   ab_alt

##### Rückgabewert

##### Beschreibung

-   simuliert eine Tastatureingabe - nämlich die Betätigung genau einer
    nicht ModifierKey- Taste gemeinsam mit einer Auswahl aus den
    ModifierKeyTasten Shift, Control und Alt
-   Bsp.:

message.uf_UiHelper().uf_SendKeyCombination ( "a", true, false, false
\## )

simuliert die Eingabe eines großen A's

#### uf_SetInputLanguage

##### Argumente

-   as_language

##### Rückgabewert

-   boolean
-   true, wenn erfolgreich

##### Beschreibung

-   setzt die InputLanguage für den aktuellen Prozess lt. as_language -
    Bsp.:

message.uf_UiHelper().uf_SetInputLanguage ( "en-US" )

-   Achtung beim Testen mit Powerbuilder: das Setzen erfolgt für den PB-
    Prozess ( nach dem Schließen des Programms, in der die Inputlanguage
    verändert worden ist, ist noch die veränderte InputLanguage gesetzt!
-   wurde zur Lösung folgenden MDE- Problems bei Grundmann eingeführt:
-   das MDE- Gerät kann nur Englisch als Input- Language
-   nachdem aber der RDB- Client die Scancodes der Tastatur überträgt,
    und für TC Deutsch als Inputlanguage eingestellt ist, kommen
    vielfach völlig falsche Zeichen - `Z´ statt`Y´, `)´ statt`(´,
    `ö´ statt`;´, ...
-   Stellt man jetzt in TC auch Englisch als Input- Language ein ist
    alles OK

## cst_udp (sys)

-   Objekt zum Lesen bzw. Schreiben von UDP Datagram Nachrichten.
    Benötigt die PfuCSFun.dll im Shared Verzeichnis und das .NET
    Framework 2.0 installiert.

### Functions

#### uf_Initialize

##### Argumente

##### Rückgabewert

-   integer

##### Beschreibung

-   Wird aufgerufen um die Objekte zu initialisieren. Sollte 0 liefern,
    ansonsten Henrik fragen.

#### uf_Bind

##### Argumente

-   al_Port
-   Der UDP-Port auf den ein Bind gemacht werden soll.

##### Rückgabewert

-   boolean
-   True: Der Bind auf den Port konnte gemacht werden
-   False: Der Bind auf den Port konnte nicht gemacht werden. Mit
    uf_GetLastError kann die Fehlerursache ermittelt werden. Ein
    typischer Fehler könnte sein, das der Port bereits von einem anderen
    Programm in Verwendung ist.

##### Beschreibung

-   Erstellt eine Verknüpfung mit dem angegebenen UDP Port

#### uf_Close

##### Argumente

##### Rückgabewert

-   boolean

##### Beschreibung

> Schließt die Verknüpfung zum UDP Port. Es kann nichts mehr gelesen
> werden. Ein neuerlicher uf_Bind ist aufzurufen.

#### uf_Receive

##### Argumente

-   al_TimeOut
-   gibt den TimeOut an, wie lange gelesen werden soll bevor die
    Funktion beendet wird. Eine Angabe von 0 bedeutet so lange lesen bis
    Daten kommen. Eventuell nicht zu empfehlen.
    -   as_Answer
-   by Reference
-   Enthält das gelesene UDP Datagram.

##### Rückgabewert

-   Boolean
-   True: Es wurden Daten empfangen \> False: Beim Empfangen ist ein
    Fehler aufgetreten oder der TimeOut ist aufgetreten. Mit
    uf_GetLastError kann die Fehlerursache ermittelt werden ( Liefert
    "TIMEOUT" wenn eben dieses aufgetreten ist.

##### Beschreibung

-   Lest vom Netzwerk bis Timeout aufgeht oder bis Daten gesendet
    wurden.
-   Bei TimeOut liefert die Funktion "False"
-   Im Fehlerfall kann mittels uf_GetLastError die Fehlerursache
    ausgelesen werden

#### uf_Send

##### Argumente

-   as_Host
-   Der Hostname oder IP Adresse wo das Paket hingeschickt werden soll.
-   Wenn der Hostname angegeben wird, muss die Namensauflösung
    funktionieren.
    -   ai_Port
-   Der Port wo das Paket hingeschickt werden soll
    -   as_Message
-   Die Nachricht die geschickt werden soll.

Rückgabewert (gibt's per 22.06.2006 - noch - nicht! - fuc) - Boolean -
True: Das Paket wurde versendet, bedeutet jedoch nicht, das der
Empfänger das Paket auch erhalten hat. - False: Das Paket konnte nicht
versendet werden. Mit uf_GetLastError kann die Fehlerursache ermittelt
werden.

##### Beschreibung

-   Sendet eine Nachricht an einen Empfänger

#### uf_GetLastError

##### Argumente

##### Rückgabewert

-   string

##### Beschreibung

> Liefert die letzte Fehlerursache im Klartext

## cst_xmlexception (sys)

### Functions

#### uf_getErrorCode

##### Rückgabewert

-   Integer
-   ErrorCode der Exception

##### Beschreibung

-   Retourniert den ErrorCode der Exception

#### uf_getErrorMessage

##### Rückgabewert

-   String
-   ErrorMessage der Exception

##### Beschreibung

-   Retourniert die ErrorMessage der Exception

#### uf_set

##### Argumente

-   as_ErrorMessage
-   Beschreibung der Exception
    -   ai_ErrorCode
-   ErrorCode der Exception
-   optional

##### Rückgabewert

-   none

##### Beschreibung

-   Setzt die Beschreibung und ErrorCode der Exception

## Variables

## ii_ErrorCode

-   darf nicht verändert werden!
-   Kann folgende Werte haben:
-   1: Fehler beim Verbinden zur Pcs.Interop
-   2: Fehler beim Trennen der Verbindung zur Pcs.Interop
-   3: Fehler beim Erzeugen eines neuen XML-Dokuments
-   4: Fehler beim Erzeugen eines neuen XML-Elements
-   5: Fehler beim Erzeugen eines neuen XML-Attributs
-   6: Fehler beim Einfügen des Root-Elements
-   7: Fehler beim Einfügen eines Elements
-   8: Fehler beim Einfügen eines Attributs
-   9: Fehler beim Setzen des Encodings
-   10: Fehler beim File-Export

## cst_xmlfun (sys)

-   ACHTUNG !!!!!
-   Zum Schreiben von Dokumenten nicht mehr verwenden ( cst_xmlwriter
    verwenden
-   Zum Lesen von XML- Dokumenten sollten wir bei Gelegenheit ebenfalls
    eine neue Klasse erstellen
-   Alternativ ist anzudenken, das Einlesen im .NET- Bereich (unter
    Verwendung der Pcs.Interop) durchzuführen und ein Zwischergebnis in
    der Datenbank abzulegen
-   Stellt Funktionalitäten für die Arbeit mit XML zur Verfügung.
-   Siehe unbedingt uf_create
-   Wenn einer Funktion die interne Repräsentation eines XML-
    Bestandteils (Cocument, Element, Attribute ) übergeben werden muss
    so erfolgt dies durch Übergabe einer internen ID welche einen
    Array-Index darstellt.
-   Wenn Funktionen eine interne Repräsentation eines XML- Bestandteils
    liefern, liefern sie ebenfalls diese ID
-   siehe als Bsp.:
    -   uf_loaddocument bzw. uf_createdocument
    -   uf_createelement

### Functions

#### uf_appendattribute

##### Argumente

-   siehe cst_xmlfun

    -   al_documentid

-   Index des XML-Dokuments

-   bei cst_xmlwriter nicht vorhanden

    -   al_elementid

-   Index des XML-Elements

    -   al_attributeid

-   Index des XML-Attributes

##### Rückgabewert

-   Boolean
-   True: Das Hinzufügen des Attributs war erfolgreich.

##### Beschreibung

-   Fügt ein XML-Attribut zu einem XML-Element hinzu.

#### uf_appendchild

##### Argumente

## siehe cst_xmlfun

-   al_documentid
-   Index des XML-Dokuments
    -   al_parentelementid
-   Index des übergeordneten XML-Elements
    -   al_childelementid
-   Index des untergeordneten XML-Elements

##### Rückgabewert

-   Boolean
-   True: Das Hinzufügen des Kindelements war erfolgreich.

##### Beschreibung

-   Fügt ein untergeordnetes XML-Element unterhalb eines übergeordneten
    XML- Elements hinzu.

#### uf_appendroot

##### Argumente

## siehe cst_xmlfun

-   al_documentid
-   Index des XML-Dokuments
    -   al_rootelementid
-   Index des Root-XML-Elements
-   §xml

##### Rückgabewert

-   Boolean
-   True: Das Hinzufügen des entsprechenden XML-Elements hat
    funktioniert.

##### Beschreibung

-   Fügt das Root-XML-Element in das Dokument lt. al_documentid ein.
-   ACHTUNG: darf für ein Dokument nur einmal aufgerufen werden!

#### uf_closedocument

##### Argumente

## siehe cst_xmlfun

-   al_documentid
-   Index des XML-Dokuments, das geschlossen werden soll

##### Rückgabewert

-   Boolean
-   True: Das Schließen des entsprechenden XML-Dokuments war
    erfolgreich.

##### Beschreibung

-   Schließt das XML-Dokument mit dem Index al_documentid.

#### uf_create

##### Argumente

##### Rückgabewert

-   Boolean
-   True: Wenn das Initialisieren des OleObjekts funktioniert hat.

##### Beschreibung

-   Muss für ein cst_xmlfun - Objekt aufgerufen werden bevor dieses
    verwendet wird.

#### uf_createattribute

##### Argumente

## siehe cst_xmlfun

-   al_documentid
-   Index des XML-Dokuments, in das ein XML-Attribut hinzugefügt wird
    -   as_attributename
-   Name des neuen XML-Attributes
    -   as_attributevalue
-   Wert des neuen XML-Attributes

##### Rückgabewert

-   Long
-   Liefert den Index des neu erstellten XML-Attributs, für die weitere
    Kommunikation, zurück.

##### Beschreibung

-   Erstellt ein neues XML-Attribut mit dem Namen as_attributename und
    dem Wert as_attributevalue.

#### uf_createdocument

##### Argumente

##### Rückgabewert

-   Long
-   Liefert den Index des neu erstellten XML-Dokuments, für die weitere
    Kommunikation, zurück.

##### Beschreibung

-   Erstellt ein neues XML-Dokument.

#### uf_createelement

##### Argumente

## siehe cst_xmlfun

-   al_documentid
-   Index des XML-Dokuments, in das ein XML-Element hinzugefügt wird
    -   as_elementname
-   Name für das neue XML-Element
    -   as_elementvalue
-   optional
-   Wert für das XML-Element

##### Rückgabewert

-   Long
-   Liefert den Index des neu erstellten XML-Elements, für die weitere
    Kommunikation, zurück.

##### Beschreibung

-   Erstellt ein neues XML-Element.

#### uf_deletedocument

##### Argumente

## siehe cst_xmlfun

-   al_documentid
-   Index des XML-Dokuments, das gelöscht werden soll

##### Rückgabewert

-   Boolean
-   True: Das XML-File, unter dem Pfad FilePath, wurde erfolgreich
    gelöscht.

##### Beschreibung

-   Löscht das XML-Dokument mit dem Index al_documentid komplett,
    mithilfe des gespeicherten FilePath.

#### uf_disconnect

##### Argumente

##### Rückgabewert

-   Boolean
-   Wenn das Freigeben des OleObjekts funktioniert hat.

##### Beschreibung

-   Muss für ein cst_xmlfun - Objekt aufgerufen werden, bevor dieses
    nicht mehr verwendet wird.

#### uf_getattributeboolean

##### Argumente

## siehe cst_xmlfun

-   al_documentid
-   Index des XML-Dokuments, indem sich das XML-Attribut befindet
    -   as_attributename
-   Name des entsprechenden XML-Attributes

##### Rückgabewert

-   Boolean
-   Wert des XML-Attributes in der Form eines Boolean

##### Beschreibung

-   Gibt den Wert des entsprechenden XML-Attributes, mit dem Name
    as_attributename, in der Form eines Boolean zurück.

## uf_GetAttribute\[Date\]\[Time\] (AKÖ)

##### Argumente

-   al_documentid
-   Index des XML-Dokuments, indem sich das XML-Attribut befindet
    -   as_attributename
-   Name des entsprechenden XML-Attributes

##### Rückgabewert

-   Date, Time bzw. Datetime je nach Funktion
-   Wert des XML-Attributes lt. as_attributename

##### Beschreibung

-   Gibt den Wert des entsprechenden XML-Attributes, mit dem Name
    as_attributename je nach Version als Date, Datetime bzw. Time
    zurück.
-   Anmerkung PCS.Interop: Übertragun .net-\>PB als Datetime

## uf_getattributedecimal (AKÖ)

##### Argumente

## siehe cst_xmlfun

-   al_documentid
-   Index des XML-Dokuments, indem sich das XML-Attribut befindet
    -   as_attributename
-   Name des entsprechenden XML-Attributes

##### Rückgabewert

-   Decimal
-   Wert des XML-Attributes in der Form eines Decimal

##### Beschreibung

-   Gibt den Wert des entsprechenden XML-Attributes, mit dem Name
    as_attributename, in der Form eines Decimal zurück.
-   Dezimaltrennzeichen lt. uf_SetDecimalSeperator
-   Anmerkung PCS.Interop: Returnwert wird als String mit Punkt als
    Dezimaltrenner und ohne Tausenderinterpolation übergeben

#### uf_getattributestring

##### Argumente

## siehe cst_xmlfun

-   al_documentid
-   Index des XML-Dokuments, indem sich das XML-Attribut befindet
    -   as_attributename
-   Name des entsprechenden XML-Attributes

##### Rückgabewert

-   String
-   Wert des XML-Attributes in der Form eines String

##### Beschreibung

-   Gibt den Wert des entsprechenden XML-Attributes, mit dem Name
    as_attributename, in der Form eines String zurück.

#### uf_getelementname

##### Argumente

## siehe cst_xmlfun

-   al_documentid
-   Index des XML-Dokuments, indem sich das entsprechende XML-Element
    befindet

##### Rückgabewert

-   String
-   Name des entsprechenden XML-Elements

##### Beschreibung

-   Gibt den Namen des aktuellen XML-Elements zurück.
-   siehe uf_loaddocument, uf_setreader....

## uf_GetElementValueXY (AKÖ)

##### Argumente

-   al_documentid
-   Index des XML-Dokuments, indem sich das XML-Attribut befindet

@Alexander: - Für jeden Datentyp, für den es eine GetAttribute- Funktion
gibt, sollte es auch eine GetElement- Funktion geben - Liest Wert des
aktuellen Elements

#### uf_loaddocument

##### Argumente

-   as_filename
-   Pfad des zu ladenden XML-Files

##### Rückgabewert

-   Long
-   Index des eingelesenen XML-Dokuments

##### Beschreibung

-   Liest ein XML-File aus und befüllt damit ein XML-Dokument, das in
    die entsprechende Liste eingefügt wird, um anschließend gleich das
    Root- Element zu setzen.

#### uf_movedocument

##### Argumente

## siehe cst_xmlfun

-   al_documentid
-   Index des XML-Dokuments, dass verschoben wird
    -   as_destinationfilename
-   Zielpfadname des XML-File

##### Rückgabewert

-   Boolean
-   True: Das Verschieben des XML-File war erfolgreich.

##### Beschreibung

-   Verschiebt ein XML-File zum angegebenen Zielpfad
    as_destinationfilename.

#### uf_savedocument

##### Argumente

## siehe cst_xmlfun

-   al_documentid
-   Index des XML-Dokuments, dass gespeichert werden soll
    -   as_filename
-   Pfad, an dem die Datei abgelegt werden soll

##### Rückgabewert

-   Boolean
-   True: Das Speichern des XML-File war erfolgreich.

##### Beschreibung

-   Speichert das XML-Dokument mit dem Index al_documentid auf
    as_filename.

## uf_Set\[Date\]\[Time\]Format (AKÖ)

##### Argumente

-   al_documentid
-   Index des XML-Dokuments, laut uf_createdocument
    -   As_FormatString
-   Siehe
    http://msdn.microsoft.com/en-us/library/8kb3ddd4(v=vs.110).aspx
-   Alle Trennzeichen sind sicherheitshalber zwischen einfache
    Anführungszeichen zu setzen
-   Bsp.: Zeitpunkt ist: Heiliger Abend 2014 17:30
-   Formatstring = "dd.MM.yyyy HH:mm:ss", Ländereinstellung Tschibuttu (
    24/12/2014 17+30+00
-   Formatstring = "dd.MM.yyyy HH:mm:ss", Ländereinstellung Österreich (
    24.12.2014 17:30:00
-   Formatstring = "dd.MM.yyyy HH.mm.ss", Ländereinstellung Tschibuttu (
    24.12.2014 17:30:00
-   ACHTUNG: wenn Trennzeichen ohne Backslash angegeben werden, werden
    sie ggf. lt. Ländereinstellung interpretiert!
-   Achtung: hh steht für 12- Stunden- Zeit

##### Rückgabewert

-   (None)

##### Beschreibung

-   Definiert das \[Date\]\[Time\]-String- Format bei der Konvertierung
    String - \[Date\]\[Time\]
-   Jeweils eigene Funktion für Date und Datetime und Time

#### uf_setreadertoattributeboolean

##### Argumente

## siehe cst_xmlfun

-   al_documentid
-   Index des XML-Dokuments, indem sich das entsprechende XML-Attribut
    befindet
    -   as_attributename
-   Name des entsprechenden XML-Attributes

##### Rückgabewert

-   Integer
-   Rückgabewerte siehe Beschreibung

##### Beschreibung

-   Prüft ob es ein XML-Attribut mit dem Namen as_attributename gibt,
    wenn nicht wird 2 retouniert, falls doch, dann wird versucht den
    Wert des Attributes in einen Boolean zu konvertieren und wenn es
    funktioniert wird 0, sonst 1 retouniert.

#### uf_setdocumentencoding

##### Argumente

## siehe cst_xmlfun

-   al_documentid
-   Index des XML-Dokuments
    -   as_encoding
-   Encoding ("ASCII", "UTF-7", "UTF-8", "UTF-32")

##### Rückgabewert

-   Boolean
-   Immer true

##### Beschreibung

-   Setzt das Encoding des XML-Files

#### uf_setreadertoattributedatetime

##### Argumente

## siehe cst_xmlfun

-   al_documentid
-   Index des XML-Dokuments, indem sich das entsprechende XML-Attribut
    befindet
    -   as_attributename
-   Name des entsprechenden XML-Attributes

##### Rückgabewert

-   Integer
-   Rückgabewerte siehe Beschreibung

##### Beschreibung

-   Prüft ob es ein XML-Attribut mit dem Namen as_attributename gibt,
    wenn nicht wird 2 retouniert, falls doch, dann wird versucht den
    Wert des Attributes in einen Datetime zu konvertieren und wenn es
    funktioniert wird 0, sonst 1 retouniert.

#### uf_setreadertoattributedecimal

##### Argumente

## siehe cst_xmlfun

-   al_documentid
-   Index des XML-Dokuments, indem sich das entsprechende XML-Attribut
    befindet
    -   as_attributename
-   Name des entsprechenden XML-Attributes

##### Rückgabewert

-   Integer
-   Rückgabewerte siehe Beschreibung

##### Beschreibung

-   Prüft ob es ein XML-Attribut mit dem Namen as_attributename gibt,
    wenn nicht wird 2 retouniert, falls doch, dann wird versucht den
    Wert des Attributes in einen Decimal zu konvertieren und wenn es
    funktioniert wird 0, sonst 1 retouniert.

#### uf_setreadertoattributestring

##### Argumente

## siehe cst_xmlfun

-   al_documentid
-   Index des XML-Dokuments, indem sich das entsprechende XML-Attribut
    befindet
    -   as_attributename
-   Name des entsprechenden XML-Attributes

##### Rückgabewert

-   Integer
-   Rückgabewerte siehe Beschreibung

##### Beschreibung

-   Prüft ob es ein XML-Attribut mit dem Namen as_attributename gibt,
    wenn nicht wird 2 retouniert, falls doch, dann wird versucht den
    Wert des Attributes in einen String zu konvertieren und wenn es
    funktioniert wird 0, sonst 1 retouniert.

#### uf_setreadertochildren

##### Argumente

## siehe cst_xmlfun

-   al_documentid
-   Index des XML-Dokuments, indem das aktuelle Kindelement gesetzt wird

##### Rückgabewert

-   Boolean
-   True: Das Setzen des "Cursor" auf das darunterliegende Kindelement
    war erfolgreich.

##### Beschreibung

-   Setzt den "Cursor" auf das erste Kindelement in der direkt
    darunterliegenden Ebene und prüft davor ob der aktuelle Knoten
    überhaupt untergeordnete Elemente hat.

#### uf_setreadertonext

##### Argumente

## siehe cst_xmlfun

-   al_documentid
-   Index des XML-Dokuments, indem das darauffolgende Element gesetzt
    wird

##### Rückgabewert

-   Boolean
-   True: Das Setzen des "Cursor" auf das darauffolgende Element war
    erfolgreich.

##### Beschreibung

-   Setzt den "Cursor" auf das Nächste, in derselben Ebene befindliche
    Element und prüft dabei ob es überhaupt nächste Knoten in derselben
    Ebene gibt.

#### uf_setreadertoparent

##### Argumente

## siehe cst_xmlfun

-   al_documentid
-   Index des XML-Dokuments, indem das darüberliegende Element gesetzt
    wird

##### Rückgabewert

-   Boolean
-   True: Das Setzen des "Cursor" auf das darüberliegende Element war
    erfolgreich.

##### Beschreibung

-   Setzt den "Cursor" auf das nächste darüberliegende Parentelement und
    prüft dabei ob das aktuelle Element nicht schon das höchste, also
    das Rootelement ist.

#### uf_setreadertoroot

##### Argumente

## siehe cst_xmlfun

-   al_documentid
-   Index des XML-Dokuments, indem das Rootelement gesetzt wird

##### Rückgabewert

-   Boolean
-   True: Das Setzen des "Cursor" auf das Rootelement war erfolgreich.

##### Beschreibung

-   Setzt den "Cursor" auf das Rootelement.

## cst_xmlwriter (sys)

-   Stellt Funktionalitäten zum Erstellen eines XML- Dokuments zur
    Verfügung.
-   ACHTUNG: die Funktionen werfen ggf. eine Exception (siehe
    Überschrift Exceptions jeweils bei der Funtionsbeschreibung) -\>
    unter Try-Catch verwenden

### Functions

#### uf_appendattribute

##### Argumente

-   al_elementid
-   Index des XML- Elements
    -   al_attributeid
-   Index des XML-Attributes

##### Rückgabewert

-   none

##### Beschreibung

-   Fügt ein XML-Attribut zu einem XML-Element hinzu.

## Exceptions

-   cst_XmlException mit ii_ErrorCode 8

#### uf_appendchild

##### Argumente

-   al_parentelementid
-   Index des übergeordneten XML-Elements
    -   al_childelementid
-   Index des untergeordneten XML-Elements

##### Rückgabewert

-   none

##### Beschreibung

-   Fügt ein untergeordnetes XML-Element unterhalb eines übergeordneten
    XML- Elements hinzu.

## Exceptions

-   cst_XmlException mit ii_ErrorCode 7

#### uf_appendroot

##### Argumente

-   al_rootelementid
-   Index des Root-XML-Elements

##### Rückgabewert

-   none

##### Beschreibung

-   Fügt das Root-XML-Element in das Dokument ein.
-   Zuvor muss das Root-Element mit uf_createelement erzeugt werden.
-   ACHTUNG: darf für ein Dokument nur einmal aufgerufen werden, da es
    genau 1 Root-Element geben muss.

## Exceptions

-   cst_XmlException mit ii_ErrorCode 6

#### uf_createattribute

##### Argumente

-   as_attributename
-   Name des neuen XML-Attributes
    -   as_attributevalue
-   Wert des neuen XML-Attributes

##### Rückgabewert

-   Long
-   Liefert den Index des neu erstellten XML-Attributs, für die weitere
    Kommunikation, zurück.

##### Beschreibung

-   Erstellt ein neues XML-Attribut mit dem Namen as_attributename und
    dem Wert as_attributevalue.

## Exceptions

-   cst_XmlException mit ii_ErrorCode 5

#### uf_createelement

##### Argumente

-   as_elementname
-   Name für das neue XML-Element
    -   as_elementvalue
-   optional
-   Wert für das XML-Element

##### Rückgabewert

-   Long
-   Liefert den Index des neu erstellten XML-Elements, für die weitere
    Kommunikation, zurück.

##### Beschreibung

-   Erstellt ein neues XML-Element.

## Exceptions

-   cst_XmlException mit ii_ErrorCode 4

#### uf_reset

##### Rückgabewert

-   None

##### Beschreibung

-   Setzt das cst_xmlwriter-Objekt zurück, dass ein neues Dokument
    begonnen werden kann

## Exceptions

-   cst_XmlException mit ii_ErrorCode 3

#### uf_savedocument

##### Argumente

-   as_filename
-   Pfad, an dem die Datei abgelegt werden soll

##### Rückgabewert

-   None

##### Beschreibung

-   Speichert das XML-Dokument auf as_filename

## Exceptions

-   cst_XmlException mit ii_ErrorCode 10

#### uf_setdocumentencoding

##### Argumente

-   as_encoding
-   Encoding ("ASCII", "UTF-7", "UTF-8", "UTF-32")

##### Rückgabewert

-   none

##### Beschreibung

-   Setzt das Encoding des XML-Files

## Exceptions

-   cst_XmlException mit ii_ErrorCode 9

## Variables

## il_DocumentId

-   darf nicht verändert werden!

## cst_zipfun (sys)

-   Stellt Funktionalitäten für die Arbeit mit ZIP-Archiven zur
    Verfügung.
-   siehe unbedingt uf_create

#### uf_AddContentFile

##### Argumente

-   al_file
-   long
-   Handle lt. uf_createzipfile bzw. uf_openzipfile
    -   as_content_file
-   string
-   Pfad (X: bzw. UNC- Notation) eines Files, welches zum Zip- Archiv
    hinzugefügt werden soll

##### Rückgabewert

-   Boolean
-   True: wenn dies erfolgreich ist
-   False wird derzeit nie geliefert (es erfolgt ggf. gf_halt)

##### Beschreibung

-   Fügt die Datei lt. as_content_file zum ZipArchiv lt. al_file hinzu

### Functions

#### uf_closezipfile

##### Argumente

-   al_file
-   long
-   Handle lt. uf_createzipfile bzw. uf_openzipfile

##### Rückgabewert

-   Boolean
-   True wenn es gut geht

##### Beschreibung

-   schließt ein ZipArchiv lt. al_file

#### uf_create

##### Argumente

##### Rückgabewert

-   Boolean
-   True: Wenn das Initialisieren des OleObjekts funktioniert hat.

##### Beschreibung

-   Muss für ein cst_zipfun - Objekt aufgerufen werden bevor dieses
    verwendet wird.

#### uf_createzipfile

##### Argumente

##### Rückgabewert

-   Long
-   Handle für das neue ZipArchiv (muss dann bei allen Funktionen, die
    etwas mit diesem ZipArchiv tun, angegeben werden)

##### Beschreibung

-   legt ein neues ZipArchiv im Speicher an und liefert einen Handle

#### uf_extractzip

##### Argumente

-   al_file
-   long
-   Handle lt. uf_createzipfile bzw. uf_openzipfile
    -   as_path
-   string

##### Rückgabewert

-   Boolean
-   True wenn es gut geht

##### Beschreibung

-   Entzippt alle Files laut ZipAcrivv in den angebeben Pfad

#### uf_openzipfile

##### Argumente

-   as_file
-   string
-   Pfad (X: bzw. UNC- Notation) eines Zip-Files

##### Rückgabewert

-   Long
-   Handle für das geöffnete ZipArchiv (muss dann bei allen Funktionen,
    die etwas mit diesem ZipArchiv tun, angegeben werden)

##### Beschreibung

-   öffnet ein ZipArchiv lt. as_file und liefert einen Handle

#### uf_savezipfile

##### Argumente

-   al_file
-   long
-   Handle lt. uf_createzipfile bzw. uf_openzipfile
    -   as_zip_file \_name
-   string
-   Pfad (X: bzw. UNC- Notation) des zu erstellenden Zip-Files

##### Rückgabewert

-   Boolean
-   True: wenn dies erfolgreich ist
-   False wird derzeit nie geliefert (es erfolgt ggf. gf_halt)

##### Beschreibung

-   speichert das ZIP-Archiv lt. al_file im File lt. as_zip_file \_name

## cst_Waehrung

-   dient zur Währungsumrechnung.

### Functions

...

#### uf_init

##### Argumente

-   atr\_
-   tr\_
-   in der atr\_ entsprechenden Datenbank müssen die Tabellen waehrung
    und waehrung_kurs lt. Tradecon- DB- Beschreibung vorhanden sein.

##### Rückgabewert

-   (None)

##### Beschreibung

-   initialisiert das Währungsobjekt
-   muß einmal zu Beginn aufgerufen werden

...

## cst_wfo

-   ein cst_wfo bildet eine Row von pfu_wfo, alle zugehörigen Rows von
    pfu_wfo_applpers ab
-   es dient zur Neuanlage und Änderung der abgebildeten Daten
-   wenn in einer Funktion al_row als Argument übergeben wird, wird
    dadurch definiert, für weche der abgebildeten pfu_wfo_applpers- Row
    Änderungen durchgeführt bzw. Daten abgefragt werden
-   der zu übergebende Wert für al_row muss mittels der Funktion
    uf_GetApplPersRow bestimmt werden.
-   alle durchgeführten Änderungen werden erst durch Aufruf der Funktion
    uf_SaveWfo in der Datenbank wirksam
-   das Argument as_error, wird von der jeweiligen Funktion mit einer
    Fehlermeldung befüllt, wenn ein Fehler passiert
-   die Funktionen und Events, die mit (!) markiert sind, sind die meist
    gebräuchlichen

### Functions

-   ACHTUNG: die durchgestrichenen Argumente sind derzeit noch
    vorhanden - es muss zuerst die API saniert werden, und dann alle
    Applikationen - diese merken es e beim Fully

#### uf_Applpers_ist_online

##### Argumente

-   as_applpers_cd
-   Sachbearbeiter, für den ermittelt werden soll, ob er online ist

##### Rückgabewert

-   boolean

##### Beschreibung

-   Ermittelt über die pfu_session (mittels pfu_session_db_sesstr =
    pfu_dbses_db_sesstr) ob der Sachbearbeiter online ist.

## uf_Create (!)

##### Argumente

-   auo_ae
-   iuo_ae des Windows von dem aus, das WFO ausgelöst wurde
-   Werte daraus werden bei der Neuanlage und Änderung des WFOs
    herangezogen

##### Beschreibung

-   MUSS für jedes cst_wfo nach dem create aufgerufen werden
-   Instanziert die benötigten DS, setzt InstanceVariablen

#### uf_ChangeW_Eskalation_Datz

##### Argumente

-   adtm_eskalation_datz
-   entspricht pfu_wfo.w_eskalation_datz (=Eskalationszeitpunkt)
    -   as_error
-   by Referenz

##### Rückgabewert

-   Boolean

##### Beschreibung

-   siehe cst_wfo
-   setzt das dem Argument entsprechende Attribut in cst_wfo

#### uf_ChangeW_W_Txt

##### Argumente

-   as_w_txt
-   entspricht pfu_wfo.wfo_txt (=Infotext)
    -   as_error
-   by Referenz

##### Rückgabewert

-   Boolean
-   as_error
-   by Referenz

##### Beschreibung

-   siehe cst_wfo
-   setzt die den Argumenten entsprechenden Attribute in cst_wfo

#### uf_GetApplPersRow

##### Argumente

-   as_applpers_cd
-   WFO-Sachbearbeiter, dessen cst_wfo- Row bestimmt werden soll
    -   as_wfpersgrp_cd
-   PersonenGruppe des WFO-Sachbearbeiters
    -   as_error
-   by Referenz
-   Fehlertext

##### Rückgabewert

-   long

-   0 = Zeile mit dem Sachbearbeiter

-   -1 = Fehler
    -   as_error

-   by Referenz

##### Beschreibung

-   dient zum ermitteln der Row eines Sachbearbeiters im cst_wfo

#### uf_GetAusApApplPersCd

##### Argumente

-   keine

##### Rückgabewert

-   string

##### Beschreibung

-   dient zum ermitteln des pfu_wfo.aus_ap_applpers_cd entsprechenden
    Attributs des aktuellen cst_wfo

#### uf_GetAusApplStr

##### Argumente

-   keine

##### Rückgabewert

-   string

##### Beschreibung

-   dient zum ermitteln des pfu_wfo.aus_appl_str ensprechenden Attributs
    des aktuellen cst_wfo

#### uf_GetData

##### Argumente

-   al_wfo_snr
-   das WFO für das die Daten ausgelesen werden sollen
    -   as_wfoart_cd
-   referenz
    -   al_ao_snr
-   referenz
    -   ai_child_level
-   referenz
    -   as_aus_applpers_cd
-   referenz
    -   as_aus_appl_str
-   referenz
    -   as_aus_kz
-   referenz
    -   adtm_gen_datz
-   referenz
    -   as_wfo_txt
-   referenz
    -   as_wfo_search_txt
-   referenz
    -   as_w_zustand_kz
-   referenz
    -   adtm_w_erl_datz
-   referenz
    -   adtm_eskalation_datz
-   referenz
    -   adtm_aktiv_ab
-   referenz
    -   as_error
-   referenz
-   bei Fehler wird hier Fehlertext zurückgeliefert

##### Rückgabewert

-   boolean
-   WFO vorhanden ( true
-   sonst ( false

##### Beschreibung

-   führt uf_RetrieveWfo mit al_wfo_snr durch und belegt die restlichen
    Argumente lt. cst_wfo

#### uf_GetWfoArtKz

##### Argumente

-   as_wfoart_cd
-   kann weggelassen werden

##### Rückgabewert

-   string

##### Beschreibung

-   dient zum ermitteln des pfu_wfoart.wfoart_kz
-   wenn as_wfoart_cd übergeben ( wfoart_kz lt. wfoart_cd
-   sonst pfu_wfoart.wfoart_kz des aktuellen cst_wfo

#### uf_GetWfoTxt

##### Argumente

-   keine

##### Rückgabewert

-   string

##### Beschreibung

-   dient zum ermitteln des pfu_wfo.wfo_txt des aktuellen cst_wfo

#### uf_GetZustandApplPers

##### Argumente

-   as_applpers_cd
-   Sachbearbeiter, dessen zustand ermittelt werden soll
    -   as_wfpersgrp_cd
-   Gruppe, in der as_applpers_cd enthalten ist

##### Rückgabewert

-   string

##### Beschreibung

-   dient zum ermitteln des Zustands eines Sachbearbeiters, einer
    bestimmten Gruppe (=pfu_wfo_applpers.wa_zustand_kz)
-   die Version mit al_row fehlt noch - siehe uf_ChangeWa_Zustand_Kz -
    wird bei Bedarf realisiert

#### uf_GetZustandWfo

##### Argumente

-   keine

##### Rückgabewert

-   string

##### Beschreibung

-   dient zum ermitteln des Zustands des WFOs (=pfu_wfo.w_zustand_kz)
    des aktuellen WFOs

## uf_New (!)

##### Argumente

-   as_wfogen_cd
-   zum Ermitteln der Row in pfu_wfogen
    -   \*as_aus_wfoart_cd
-   das WFO wird durch diese WFOArt ausgelöst
-   wenn weggelassen, wird ' ' angenommen
    -   -   as_aus_applpers_cd
-   auslösender Sachbearbeiter
-   bei Generierung über API- Funktion der applpers_cd der Anmeldung des
    bei uf_create übergebenen Windows
-   bei Eskalation der aus_applpers_cd des eskalierten WFOs
-   sonst lt. Generierungsjob - siehe dazu gen_genjob_kz
-   wenn weggelassen, wird fix der applpers des beim uf_Create ()
    übergebenen Windows angenommen.
    -   as_aus_ap_applpers_cd
-   Belegung für pfu_wfo. aus_ap_applpers_cd
    -   as_appl_str
-   Belegung für pfu_wfo.ap\_ appl_str
    -   adc_ao_snr
-   Referenze
-   abhängig von pfu_wfogen.gen_applobj_kz:
-   ' ' ( wird ignoriert
-   'f' ( wenn übergebene al_applobj_snr = 0, findet eine Neuvergabe
    mittel uf_serial statt, ansonst wird dem WFO die übergebene
    al_applobj_snr zugewiesen
-   sonst ( es muss die applobj_snr eines bestehenden AOs übergeben
    werden
    -   as_text
-   Informationstext
    -   -   adc_aus_wfo_snr
-   die wfo_snr des auslösenden WFOs (siehe Begriffsdefinition in der
    Datenbankbeschreibung)
-   siehe pfu_wfogen.gen_parent_kz
-   muss ein wfo_snr eines Wfo's sein, wenn dies lt.
    pfu_wfogen.gen_parent_kz so vorgesehen ist
    -   -   adtm_eskalation
-   Eskalationszeitpunkt
-   siehe pfu_wfogen.aus_kz='ew'
-   wenn weggelassen, wird DatMax angenommen
    -   -   adtm_aktiv_ab
-   erst ab diesem Zeitpunkt ist das WFO aktiv, vorher "schlummert es"
-   die Mitteilung an die Anwender (den Anwender) erfolgt erst ab diesem
    Zeitpunk
-   wenn weggelassen, wird Today() angenommen
    -   as_error
-   referenz
-   bei Fehler wird hier Fehlertext zurückgeliefert

##### Rückgabewert

-   boolean
-   adc_ao_snr
-   by Referenz

##### Beschreibung

-   generiert ein neues WFO (pfu_wfo) in cst_wfo und legt dazu die
    ApplikationsPersonen (pfu_wfo_applpers) an
-   Es gibt 2 Varianten des Aufrufs:
-   alle Parameter übergeben
-   nur jene Parameter übergeben die nicht mit einem \* gekennzeichnet
    sind

## uf_SaveWfo (!)

-   ab_update
-   false ( WFO wird zum ersten Mal gespeichert (neu- Zweig)
-   true ( WFO wird geändert (zB zustand,..)
    -   ab_melden
-   true ( die Sachbearbeiter des WFOs werden benachrichtigt, das rote
    Fenster erscheint
-   false ( es gibt keine Benachrichtigung, das Erscheinen des roten
    Fensters wird nicht ausglöst
    -   as_error
-   referenz
-   bei Fehler wird hier Fehlertext zurückgeliefert

##### Rückgabewert

-   long

-   -1 bei fehler update d_ds_pfu_wfo

-   -2 bei fehler update d_ds_pfu_wfo_applpers

-   -3 bei fehlendem uf_new aufruf

-   -4 fehler beim generieren neuer wfo's bzw. job einspoolen

-   -5 fehler beim setzen des gemeldet_jn

-   = 0 ( es gab kein WFO das gespeichert werden musste

-   0 ( WFO-Snr

##### Beschreibung

-   speichert ein WFO und überprüft sämtliche Zustandsänderungen des
    WFOs und der ApplPers'n des WFOs ( bei zustandsänderungen und
    vorhandener Workflow- Objekt- Generierungsvorschrift (pfu_wfogen)
    wird ein Job eingespoolt, welcher ein neues WFO generiert bzw Event
    "WfoAktion" des AOs aufruft

## uf_Reset (!)

##### Beschreibung

-   setzt cst_WFO auf den Ursprung zurück

#### uf_RetrieveWfo

-   al_wfo_snr
-   WFO-Snr mit der das WFO retrieved werden soll
    -   as_error
-   referenz
-   bei Fehler wird hier Fehlertext zurückgeliefert

##### Rückgabewert

-   boolean

##### Beschreibung

-   retrieved die beiden DS des cst_wfo

#### uf_Wfo_Snr

##### Argumente

-   keine

##### Rückgabewert

-   long
-   wfo_snr des aktuellen WFOs

##### Beschreibung

-   dient zum ermitteln der pfu_wfo.wfo_snr des aktuellen cst_wfo's

#### uf_WfoArt_Cd

##### Argumente

-   keine

##### Rückgabewert

-   string
-   wfoart_cd des aktuellen WFOs

##### Beschreibung

-   dient zum ermitteln des pfu_wfo.wfoart_cd des aktuellen cst_wfo's

## datawindowchild

-   Tritt nur als Argument bei den Events
    -   DddwAfterRetrieve
    -   DddwRetrieve der Klasse DwApplObj auf.

### Functions

## find

##### Argumente

-   as_expression
-   ein Ausdruck wie in der Where- Bedingung eines Select- Statements.
    Allerdings werden statt DB- Columns DW- Columns angesprochen
    -   al_start
-   Suche fängt bei dieser Row an
    -   al_end
-   Suche hört bei dieser Row auf
-   al_end kann \< al_start sein, dann wird rückwärts gesucht

##### Rückgabewert

-   long
-   die erste Row in der Suchrichtung von al_start weg, welche
    as_expression erfüllt
-   0 ( keine Row erfüllt die Expression
-   null ( irgendwas ist null

## GetItem\[Date\|DateTime\|Decimal\|Number\|String\|Time\]

##### Argumente

-   al_row
-   as_column

##### Rückgabewert

-   lt. Funktionsname
-   Feldinhalt

##### Beschreibung

-   liefert den Feldinhalt zu einer DS- Column

## InsertRow

##### Argumente

-   al_row
-   die Neue Zeile ist die al_row'te Zeile

##### Rückgabewert

-   long
-   -1, wenn das Einfügen nicht erfolgreich war
-   NULL, wenn al_row null ist
-   al_row, wenn das Einfügen erfolgreich war

##### Beschreibung

-   Fügt eine neue Zeile in Datawindowchild ein.

## reset

##### Argumente

##### Rückgabewert

-   integer
-   1, wenn ok - wir gehen davon aus, daß dies immer der Phall ist

##### Beschreibung

-   Ändern eines Wertes eines Feldes im Datawindowchild

## retrieve

##### Argumente

-   Retrievel- Argument i des Dw- Objects
-   soviele eben vorhanden sind

##### Rückgabewert

-   integer
-   Anzahl der retrieveten Rows
-   -1 bzw. Null, wenn versagt

##### Beschreibung

-   befüllt das Datawindowchild neu
-   nur innerhalb des Events DwApplObj.DddwRetrieve

## SetItem

##### Argumente

-   al_row
-   ai_column / as_column
-   aa_wert

##### Rückgabewert

-   (None)

##### Beschreibung

-   Ändern eines Wertes eines Feldes im Datawindowchild

## ds\_

-   Die verwendung von ds\_ erfolgt nach folgenden Schema: . ?ds\_\* =
    create ds\_ . ?ds\_*.{uf_create(...),uf_DataObject(...)} . Arbeiten
    mit dem DS . destroy ?ds\_*
-   ist ?ds\_\* eine Instance- Variable im Window, erfolgen create und
    uf_create/uf_DataObject im initialize- Event- Script und destroy im
    CleanUp- Script des Windows.
-   für die Abhandlung von varbinary(max)- Richtextfeldern gilt:
-   wenn nachfolgend von Richtextfeldern gesprochen wird, sind genau
    diese varbinary(max)- Richtextfelder gemeint
-   alle Felder, die auf \_rtxt enden werden als solche betrachtet
-   Richtextfelder werden über pfu_selkonst abgehandelt und dürfen keine
    Update- Property haben
-   alle Felder, für die gilt:
-   der Name endet mit \_txt
-   es gibt ein Richtextfeld dessen Name ohne dem abschließenden \_rtxt
    genau gleich dem Namen des hier betrachteten Feldes ohne dem
    Abschließenden \_txt ist werden als Plaintextfeld des oben genannten
    Richtextfeldes betrachtet
-   für ein solches Feld gilt:
-   es wird bei kopier- Aktivitäten (uf_GetItemInto ...) nicht
    berücksichtigt
-   es wird bei Änderung des zugehörigen Richtextfeldes automatisch
    gesetzt
-   das Plaintextfeld und Richtextfeld müssen natürlich in der Datenbank
    zur selben Tabelle gehören
-   die pfu_fun ermittelt diese Tabelle lt. Plaintextfeld
-   für jede solche Tabelle muss es sowohl in der Datenbank als auch im
    DWO ein Feld namens `<Tabellenname>`{=html} + "\_dbid" geben
-   dieses muss eine Row der Tabelle eindeutig identifizieren
-   dieses wird für das Lesen und Schreiben der Richtexte aus der bzw.
    in die Datenbank benötigt
-   Im RetrieveEnd- Eventscript (( dieses ist für die
    Applkationsprogrammierung tabu) werden alle Richtextfelder durch
    einen Select aus der Datenbank befüllt
-   wenn allerdings der Wert des DbId- Feldes \<= 0 ist, erfolgt dies
    nicht (seit A 25781)
-   Im UpdateEnd- Eventscript (( dieses ist ebenfalls für die
    Applkationsprogrammierung tabu) werden alle Richtextfelder der
    UPDATE- Table, die mittels uf_SetItem geändert worden sind, in die
    Datenbank übertragen - ACHTUNG: Felder, die mittels SetItem geändert
    worden sind, werden nicht berücksichtigt
-   siehe auch uf_create
-   ACHTUNG: PERFORMANCE: ..GetItemInto ist langsam - schneller ist die
    unter Textzeilen mit Richtext aus einer fremden Tabelle in ein DW
    bringen beschriebene Methode

### Functions

## DeleteRow

##### Argumente

-   al_row
-   die Zeile welche gelöscht werden soll

##### Rückgabewert

-   long
-   -1, wenn das Löschen nicht erfolgreich war
-   NULL, wenn al_row null ist
-   1, wenn das Löschen erfolgreich war

##### Beschreibung

-   Löscht eine Zeile aus dem DS.

## find

-   siehe dw_ApplObj.find

## GroupCalc

##### Argumente

##### Rückgabewert

-   integer
-   1 ( erfolgreich
-   sonst ( nicht erfolgreich

##### Beschreibung

-   Berechnet die Gruppensummen neu
-   Vorher muß ggf. sort erfolgen

## InsertRow

##### Argumente

-   al_row
-   die Neue Zeile ist die al_row'te Zeile

##### Rückgabewert

-   long
-   -1, wenn das Einfügen nicht erfolgreich war
-   NULL, wenn al_row null ist
-   al_row, wenn das Einfügen erfolgreich war

##### Beschreibung

-   Fügt eine neue Zeile in den DS ein.

## reset

##### Argumente

##### Rückgabewert

-   integer
-   1, wenn ok - wir gehen davon aus, daß dies immer der Phall ist

##### Beschreibung

-   Ändern eines Wertes eines Feldes im DS

## retrieve

##### Argumente

-   Retrievel- Argument i des Dw- Objects
-   soviele eben vorhanden sind
-   String- Argumente sind mit Transaktionsobjekt.uf_arg zu behandeln

##### Rückgabewert

-   long
-   Anzahl der retrieveten Rows
-   -1 bzw. Null, wenn versagt

##### Beschreibung

-   befüllt den DS neu

## SetItem

##### Argumente

-   al_row
-   ai_column / as_column
-   aa_wert

##### Rückgabewert

-   (None)

##### Beschreibung

-   Ändern eines Wertes eines Feldes im DS
-   sollte nicht mehr verwendet werden (besonders bei alphanumerischen
    Feldern)
-   es sollte uf_SetItem verwendet werden (Problematik Trim/Untrim)

## SetSort

##### Argumente

-   as_sort
-   Format: `<Feldname>`{=html} " " {"A", "D"} \[ ","
    `<Feldname>`{=html} \] ...
-   "A" ( ascending = aufsteigend, "D" ( descending = absteigend

##### Rückgabewert

-   integer
-   1 ( erfolgreich
-   sonst ( nicht erfolgreich

##### Beschreibung

-   Legt die Sortierung fest
-   Es darf in einem Script jederzeit ein sort()- Aufruf stehen, um die
    Sortierung zu aktuallisieren
-   Hat nichts mit dem ORDER BY im Select zu tun!

Siehe auch - Sort

## Sort

##### Argumente

##### Rückgabewert

-   integer
-   1 ( erfolgreich
-   sonst ( nicht erfolgreich

##### Beschreibung

-   führt Sortierung (neu) durch

#### uf_create

##### Argumente

-   atr\_
-   Transaction- Object für den DS
    -   as_select
-   das Select- Statement, aus dem das DataWindowObject des DS generiert
    wird.
-   die DS- Column- Namen sind die Column- Namen des Selects bzw. deren
    Aliasnamen
-   für Konstante und Expressions im Select sind unbedingt Alias- Namen
    zu vergeben!
-   für ein Richtextfeld (siehe für die Abhandlung von varbinary(max)-
    Richtextfeldern gilt:) ist folgende Notation zu verwenden:
    -   "{" & `<Datenbank-Column-Name>`{=html} & "," &
        `<Datawindow-Column-Name>`{=html} & "}"
-   im Select wird dies dann durch
    -   "' '" & " " & `<Datawindow-Column-Name>`{=html} ersetzt
-   das Feld erhält für das DWO-Property update den Wert no
-   beim Richtext-Feld-Select nach dem Retrieve und beim Richtext-Feld-
    Update nach dem Insert/Update wird `<Datenbank-Column-Name>`{=html}
    herangezogen

##### Rückgabewert

-   (None)

##### Beschreibung

-   Iinitialisiert den DS
-   ACHTUNG: darf nicht innerhalb einer Transaction aufgerufen werden!!!
-   Alternativ kann der DS über uf_DataObject initialisiert werden.
-   darf nur einmal aufgerufen werden

#### uf_DataObject

##### Argumente

-   atr\_
-   Transaction- Object für den DS
    -   as_DataObject
-   das DataWindowObject des DS
-   sollte folgende Namenskonvention einhalten: d_ds\_\*
    -   as_AbWhere
-   Der Teil des Selects des DWOs nach "where" beginnend wird durch
    as_AbWhere ersetzt, wenn as_AbWhere nicht leer ist.
-   "" ( keine Ersetzung
-   Dies kann dazu verwendet werden das DWO von seinen Retrieval-
    Arguments zu befreien.

##### Rückgabewert

-   (None)

##### Beschreibung

-   Iinitialisiert den DS
-   ACHTUNG: darf nicht innerhalb einer Transaction aufgerufen werden!!!
-   Alternativ kann der DS über uf_create initialisiert werden.
-   darf nur einmal aufgerufen werden

#### uf_GetDiagString

##### Argumente

-   al_row

##### Rückgabewert

-   string
-   String mit Bezeichnung und Wert für jedes Feld der Row

##### Beschreibung

-   wurde eingeführt, um im Fehlerfall die Daten der aktuellen Zeile in
    der Fehlermeldung zu haben

#### uf_GetItem

##### Argumente

-   al_row
-   { as_column, ai_column }

##### Rückgabewert

-   any
-   Feldinhalt

##### Beschreibung

-   liefert den Feldinhalt zu einer DS- Column
-   siehe GetItem{String, Number, ...} - wenn es auf die Performance
    ankommt

#### uf_GetItemInto

##### Argumente

> -   al_row
>
> -   Für die erste Row im DS wird die Row lt. al_row im Ziel- DW
>     gesucht, und jeweils alle Columns des DS in die Columns des DWs
>     übertragen
>
> -   kann weggelassen werden, dann wird 1 angenommen
>
> -   adw_target bzw. ads_target
>
> -   Ziel- DW bzw. DS
>
> -   al_RowTarget
>
> -   Es werden alle Columns der Row lt. al_row des DS in die Columns
>     der Row lt. al_RowTargert des DWs übertragen
>
> -   adw_target
>
> -   Ziel- DW
>
> -   as_keycols
>
> -   Liste von Feldnamen, die durch Leerzeichen getrennt sind.
>
> -   Für jede Row im DS werden alle Rows, bei denen die Felder lt.
>     as_keycols übereinstimmen, im Ziel- DW gesucht, und jeweils alle
>     Columns des DS in die Columns des DWs übertragen.

##### Rückgabewert

##### Beschreibung

-   Überträgt Werte von Feldern im DS in ein Ziel- DW
-   dies erfolgt je Feld mittels uf_ChangeItem
-   Fehler werden ignoriert (Wenn dies nicht tragbar ist, muß eine neue
    Version von uf_GetItemInto gepinselt werden.)

#### uf_GetItemIntoNewline

##### Argumente

-   adw_target
-   DW, in welches der Inhalt des DS eingefügt werden soll
    -   as_row
-   row, von der beginnend in adw_target eingefügt werden soll
-   siehe dazu dw_ApplObj.uf_newline
    -   as_aktion
-   Für die neu eingefügte Zeile in adw_target wird uf_aktion mit
    as_aktion aufgerufen
-   kann weggelassen werden, dann wird keine Aktion ausgeführt
-   hier kann uf_ResetItemStatus aufgerufen werden
    -   as_error (reference)
-   Fehlertext, wird im Fehlerfall belegt

##### Rückgabewert

-   boolean
-   true ( erfolgreich false ( ein Fehler ist aufgetreten (return
    erfolgt sofort beim ersten Fehler)

##### Beschreibung

-   Fügt für jede Row im DS mittels uf_NewLine eine Row in das DW
    adw_target ein und setzt dort für alle Columns, für die es eine
    gleichnamige Column im DS gibt, den Wert mittels uf_ChangeItem auf
    den entsprechenden Wert aus dem DS.
-   Tritt ein Fehler auf wird as_error belegt und false returned
-   ACHTUNG: pro Row werden die Felder in der Reihenfolge lt. Column-
    Specification des DWOs des DS abgearbeitet. Es ist also beim DWO des
    DS darauf zu achten, daß sich kein Feld, das im Ziel- DW vor einem
    anderen Feld belegt werden muß, in der genannten Reihenfolge im DWO
    des DS nach diesem anderen Feld befindet!

#### uf_ImportFile

##### Argumente

-   as_filename
-   al_ZeilenUeberlesen
-   soviele Zeilen werden überlesen
    -   al_ZeilenLesen
-   soviele Zeilen werden gelesen
-   0 bedeutet alle
    -   al_ZeilenImportiert
-   reference
    -   as_error
-   reference
-   im Fehlerfall steht hier: "Zeile 12 Feld 5 (vk_preis): Fehlertext"
-   12 ist die Zeile im Importfile (-\> kann im Extremfall die erste
    Zeile im DW sein)

##### Rückgabewert

-   boolean

##### Beschreibung

#### uf_RowCount

##### Argumente

##### Rückgabewert

-   long
-   Anzahl der Rows im DS

#### uf_SetItem

##### Argumente

-   al_row
-   as_column
-   aa_wert

##### Rückgabewert

-   boolean
-   liefert false, wenn das Setzen nicht erfolgreich ist

##### Beschreibung

-   Setzt den Wert eines Feldes im DS
-   macht bei Char- Feldern auch Untrim, sodass das Feld bis zur vollen
    Feldgröße mit Blanks aufgefüllt ist
-   bei VarChar und Text- Feldern wird ein Blank angefügt, falls aa_wert
    der Leerstring ist
-   dies ist notwendig, weil die Felder nach dem retrieve genau so
    aussehen

#### uf_SetItemStatusNew

##### Argumente

-   al_row
-   kann weggelassen werden, dann:
-   werden alle Rows behandelt

##### Rückgabewert

-   (None)

##### Beschreibung

-   Setzt den Status der Row lt. al_row auf "neu eingefügt"

#### uf_SetSelectSubst

##### Argumente

-   as_pattern
-   String der ersetzt werden soll
    -   as_text
-   String durch den ersetzt werden soll

## alternative Argumente -- nicht implementiert

-   wenn es jemand dringend braucht, kann man darüber nachdenken, diese
    zu implementieren

    -   auo_ParList

-   siehe cst_ParList

    -   as_WohinMatch

-   siehe cst_ParList.uf_AddPar

-   Es werden für alle "wohin" aus auo_ParList, für die match ( wohin,
    as_WohinMatch ) true ist, die Ersetzungen durchgeführt.

##### Rückgabewert

-   integer
-   Anzahl der Ersetzungen

##### Beschreibung

-   Ersetzt alle Vorkommnisse von as_pattern im Select. String durch
    as_text.
-   Folgender Ablauf der Aufrufe: . uf_SetSelectStart()
-   Der Select- String wird auf den Orginalzustand initialisiert . ein-
    oder mehrere Male uf_SetSelectSubst ( ... )
-   ACHTUNG: mehrere Aufrufe mit dem selben as_pattern sind nicht
    sinnvoll, da ja as_pattern nach dem ersten uf_SetSelectSubst- Aufruf
    nicht mehr vorhanden ist! . uf_SetSelectFinish()
-   uf_create bzw. uf_DataObject müssen bereits erfolgt sein!
-   kann vor jedem Retrieve erfolgen.

#### uf_SetSelectTabDazu

##### Argumente

-   as_tab
-   Tabelle, die hinzugefügt werden soll
    -   as_alias
-   Alias- Name für obige Tabelle
-   kann leer sein

##### Rückgabewert

-   boolean
-   erfolgreich = true

##### Beschreibung

-   hängt an die FROM- Clause des Selects eine zusätzliche Tabelle ung
    ggf. einen zugehörogen Aliasnamen an
-   Darf nur im BeforeSetSelectFinish- Event- Script des windows für
    idw_list verwendet werden.

Siehe auch - w_ApplObj.event BeforeSetSelectFinish

#### uf_untrim

##### Argumente

-   as_column
-   Column- Name
    -   aa_wert
-   Wert der "enttrimmt" werden soll

##### Rückgabewert

-   Any
-   wenn as_column eine CHAR- Column ist ( aa_wert mit Leerzeichen auf
    die Länge von as_column verlängert
-   sonst ( aa_wert

## Wann verwenden

-   wenn in einer char- Column sich in manchen Rows Werte aus dem Select
    und in manchen Rows mittels SetItem gesetzte Werte befinden gibt es
    folgendes Problem, das über ein Beispiel erklärt wird:
-   in einer Row, die über Select befüllt ist steht in der Column Lager
    "hpt"
-   in einer Row, die über SetItem befüllt ist steht in der Column Lager
    "hpt"
-   wird jetzt nach dieser Column und nachfolgend nach einer weiteren
    Column sortiert, kommt "hpt" vor "hpt" und die 2. Sortiercolumn hat
    keine Auswirkung
-   durch SetItem ( ... untrim("lag_cd", ls_lag_cd) ... ) kann dies
    verhindert werden
-   siehe uf_SetItem

#### uf_view

## Argumente Version 1

-   adw\_
-   Über DW wird Window ermittelt und die Funktion mit aw\_ aufgerufen

## Argumente Version 2

-   aw\_
-   um zu ermitteln, ob Window im Diagnosemodus ist
-   Die Anzeige erfolgt dann, wenn das window im Diagnosemodus ist bzw.
    der Applikationsdiagnosemodus eingeschaltet ist.

## Argumente Version 3

-   ab_diagnose
-   true ( view erfolgt nur, wenn:
-   das aktuelle Window ein w_ApplObj ist
-   dieses im Diagnosemodus ist oder der Applikationsdiagnosemodus
    eingeschaltet ist
-   dies in der Registry so eingestellt ist, was durch das Script
    \\Pfundnerlx`\projekte`{=tex}`\InstallVorlagen`{=tex}`\Zubehör`{=tex}`\RegEditViewDs`{=tex}.vbs
    bewerkstelligt wird
-   false ( view erfolgt immer

##### Rückgabewert

-   (None)

##### Beschreibung

-   dient nur zu Diagnosezwecken
-   zeigt den Inhalt des DS in einem eigenen Window an.
-   Die Anzeige erfolgt allerdings nur im Diagnosemodus, falls adw\_
    bzw. aw\_ angegeben sind

## update

##### Argumente

##### Rückgabewert

-   integer
-   1: alles ok Null oder ein anderer Wert: alles i.A.

##### Beschreibung

-   Schreibt die im DS durchgeführten Änderungen in die Datenbank

## Variables

## ib_ResetOnRetrieve

-   kann vor dem Aufruf der Funktion Retrieve verändert werden und
    bleibt dann bis zum destroy des DS erhalten
-   true -\> standardmäßiges Verhalten beim Retrieve
-   false -\> der Inhalt des DS bleibt erhalten und retrieve erfolgt
    aditiv

## dw_ao_ImmerDa

-   kann z.B. dafür verwendet werden Parameter oder Suchkriterien (wenn
    Query nicht über das Query- Fenster erfolgen soll) einzugeben
-   Abgeleitet von dw_ApplObj_Tci ( auch von dw_ApplObj
-   es ist unabhängig vom Zustand lt. uf_status immer eine Row
    vorhanden, wenn das Window Präsentiert wird ( Belegungen sollten im
    BeforeOnSetpresentation erfolgen
-   der Select des DWOs muss genau eine Zeile liefern
-   wenn im EventScript von dw_ao_immerDa bereits Code vorhanden ist,
    darf es nicht erweitert oder übersteuert werden

## dw_ApplObj

## Events

## AeoDwColName

##### Argumente

-   as_AeoColName \> Präfix + PKeyColname
-   hat das AOT des AEOs keine PKeyColumn, wird stattdessen Präfix + ID-
    Name übergeben \> Präfix + MC- Colname
-   hat das AOT des AEOs keine PKeyColumn, erfolgt dieser Aufruf nicht
    -   as_DwColName
-   reference
-   wird ignoriert, wenn das AOT des AEOs keine PKeyColumn hat

##### Rückgabewert

-   boolean
-   siehe Beschreibung

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   Für jedes DW wird beim Windowstart für jedes AEO bestimmt,
    -   ob es ein Feld mit dem Namen Pkey- Name inkl. Präfix des AEOs
        gibt
    -   ob es ein Feld mit demMatchcode- Name inkl. Präfix des AEOs gibt
-   Der Feldname lt. AEO, der im DWO gesucht wird, kann über dieses
    Event verändert werden
-   liefert das Event- Script false, wird definiert, dass es im DW kein
    entsprechendes Feld gibt
-   gibt es das Key- Feld nicht, wird das DW in Bezug auf dieses AEO
    ignoriert
-   Bsp1.: das AEO- Pkeyfeld "standort_cd" heißt im DWO
    "drucker_standort_cd" ( as_DwColName = "drucker_standort_cd"
-   Bsp2.: das Feld kunde_cd ist zwar im DWO vorhanden, soll aber den
    ENV- Wert kunde_cd nicht setzten ( return false

## AfterDeleteLine

##### Argumente

-   al_row
-   aktuelle Zeile des DWs
-   O- Ton Hr. Fuckar: "des is scho die Nochgrudschde" -- und er hat
    recht!

##### Rückgabewert

-   (None)

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   Hier können Aktionen, welche nach dem Löschen einer Row notwendig
    sind, erfolgen.
-   ACHTUNG: wenn Daten der Gelöschten Zeile notwendig sind, müssen
    diese im BeforeDeleteLine weggesichert werden.

## AfterPasteRow

##### Argumente

-   al_CpRow
-   Zeile des Copy- Buffers des DWs
    -   al_row
-   Zeile des DSs, die gerade aufgebaut wird
    -   ac_pasting
-   "a" ( gesamtes AO wird gepastet "r" ( Row wird gepastet (Row is über
    Menüpunkt in den Copy- Buffer gekommen)

##### Rückgabewert

-   (None)

## Ableitung

-   darf überschrieben werden
-   darf erweitert werden

##### Beschreibung

-   siehe dw_ApplObj.event SollPaste

## AfterResortByDragAndDrop

##### Argumente

##### Rückgabewert

-   (None)

## Ableitung

-   darf überschrieben werden

##### Beschreibung

-   wird aufgerufen, nachdem eine Umsortierung im DW durch Drag&Drop
    erfolgt ist
-   eingeführt für Ahrens w_auf_i.dw_auf_auf_pos - siehe ggf. dort
-   dient der Applikation, Änderungen, die von der Sortierung abhängig
    sind, durchzuführen

## AfterRetrieve

##### Argumente

##### Rückgabewert

-   (None)

## Ableitung

-   darf überschrieben werden
-   darf erweitert werden

##### Beschreibung

-   wird nur für Master aufgerufen
-   wird aufgerufen, nachdem
-   alle DWs des Master- Detail- Verbunds retrieved
-   alle Retrieveend- Appl- Scripts abgearbeitet sind
-   Werden Änderungen durchgeführt, kommt der MD- Verbund in den Status
    Update

## AfterUpdate

##### Argumente

##### Rückgabewert

-   boolean
-   true ( Save des Master- Detail- Verbunds wird fortgesetzt false (
    Save des Master- Detail- Verbunds wird abgebrochen

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   siehe BeforeUpdate

## AfterUpdateOk

##### Argumente

-   ac_zweig

-   "n" beim Speichern nach dem Neu- Zweig

-   "u" beim Speichern nach dem Update- Zweig

    -   ab_RollbackAll

-   by reference

-   wird Argument mit true belegt:

-   werden alle Änderungen seit dem Retrieve oder dem letzten Speichern
    vom Menü aus in den DWs und in der DB rückgängig gemacht, wenn
    speichern aus dem Menü aufgerufen wurde

-   liefert wf_Save() false

##### Rückgabewert

-   (None)

## Ableitung

-   darf überschrieben werden
-   darf erweitert werden

##### Beschreibung

-   siehe BeforeUpdate

## Aktion

##### Argumente

-   al_row

-   Zeile des DWs

    -   al_LetztRow

-   letzte Zeile des DWs, welche vom selben uf_Aktion- Aufruf bearbeitet
    wird.

-   ist = al_row, wenn uf_Aktion genau eine Row behandelt

-   ist = uf_RowCount(), wenn uf_Aktion alle Rows behandelt

-   Wurde eine Aktion (=innere Aktion) von einer anderen Aktion (=
    äußere Aktion) aus aufgerufen, so wird bei der inneren Aktion
    al_LetztRow gleich wie bei der äußeren Aktion übergeben!!!

    -   as_aktion

-   Bezeichnung der Bedingung

    -   ac_status

-   Status des Master- Detail- Verbunds, siehe uf_Status()

    -   ab_retrieving

-   true ( Master- Detail- Verbund wird gerade retrieved

-   nicht mehr verwenden, da man nicht genau weis, was er tut - nur aus
    Abwärtskompatibilitätsgründen vorhanden

    -   ac_zweig

-   '-' ( das RetrieveEndAppl- Eventscript läuft nicht restliche ( das
    RetrieveEndAppl- Eventscript läuft - siehe RetrieveEndAppl Parameter
    ac_zweig

    -   ac_ausloeser

-   was ist die unterste Aktivität im Callstack, die die Aktion direkt
    oder indirekt auslöst

-   'e' ( Edit Aufruf von uf_aktion innerhalb des ItemChangedAppl-
    Eventscripts, welches durch eine Benutzereingabe ausgelöst worden
    ist

-   'c' ( uf_ChangeItem Aufruf von uf_aktion innerhalb des
    ItemChangedAppl- Eventscripts, welches durch einen uf_ChangeItem
    ausgelöst worden ist

-   'a' ( Aufruf von uf_aktion außerhalb des ItemChangedAppl-
    Eventscripts

-   weitere Werte siehe uf_aktion - ac_ausloeser

    -   adw_ausloeser

-   ist ein DW im Master- Detailverbund

-   das DW, auf das der äußerste uf_ChangeItem- Aufruf erfolgt ist - ist
    dieses DW ein Monitor- DW, dann wird hier das gemonitorte DW
    geliefert

    -   al_RowAusloeser
    -   as_ColumnAusloeser

-   beginnt weder mit "ein:" noch mit "ist:" - siehe dazu \####
    uf_DefineEinIstCol

    -   aa_WertAltAusloeser
    -   aa_WertAusloeser

##### Rückgabewert

-   boolean
-   true, wenn die Aktion erflogreich ist, sonst false

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   siehe uf_aktion

## BeforeDeleteLine

##### Argumente

-   al_row
-   Zeile des DWs
    -   ac_AufrufVon
-   gibt an, von wo aus neue Zeile angelgt würde "m" ( "Zeile löschen"
    bzw. "Zeile ausschneiden" im Menü "s" ( von einem Script des
    Applikationsprogrammierers aus

##### Rückgabewert

-   boolean
-   true, wenn die al_Row entsprechende Row des DWs gelöscht werden
    darf, sonst false

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   Hier können Aktionen, welche vor dem Löschen einer Row notwendig
    sind, erfolgen.
-   Es kann das Löschen einer Row verhindert werden

## BeforeDrag

##### Argumente

-   auo_draggedobject
-   cst_DraggedObject
-   Ist immer valid!

##### Rückgabewert

-   boolean
-   true ( drag darf durchgeführt werden, sonst ( false

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   Hier kann verhindert werden, dass drag stattfindet
-   Aktivitäten in diesem Script müssen sehr genau überlegt werden -
    ggf. Rücksprache
-   Das Event wird nur aufgerufen, wenn ein cst_DraggedObject
    entsprechendes Objekt gedragged wird

## BeforeSelectRichtext

##### Argumente

-   al_row
-   Argumente, für die gilt:
-   ByReference
-   wenn \<\> "" ( Wert wird im Select, der die Werte für die Richtext-
    Felder ermittelt, verwendet
-   sonst ( Wert wird von der pfu_fun lt. DWO ermittelt
    -   as_DbColNameList
-   Liste der Column-Namen der Richtext- Felder im Select
-   durch Komma getrennt
    -   as_TableName
-   Name der Tabelle, aus denen die Richtext- Felder selektiert werden,
    im Select
    -   as_WhereString
-   Bedingung, die die Key- Felder in der Tabelle lt. as_TableName
    eindeutig festlegt

##### Rückgabewert

-   (none)

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   wird für jede Zeile aufgerufen, wenn die Blob- Richtextfelder aus
    der Datenbank gelesen und ins DW geschrieben werden (siehe
    uf_DefineRichtextCol Argument ab_blob)
-   wurde mit A21694 eingeführt
-   wird für die unter Textzeilen mit Richtext aus einer fremden Tabelle
    in ein DW bringen beschriebene Methode benötigt

## BeforeOnSetpresentation

##### Argumente

##### Rückgabewert

-   boolean
-   true ( Presentation des DWs geht weiter
-   false ( Presentation des DWs geht nicht weiter und Presentation wird
    von Beginn weg nochmals durchgeführt

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   das Event wird für jedes sichtbare DW, das enabled ist, im Ramen des
    SetPresentation aufgerufen
-   zum Zeitpunkt desAufrufs:
-   sind die Retrieves der sichtbaren DWs durchgeführt
-   hat das DW, das den Focus erhalten soll diesen noch nicht unbedingt
-   ist die aktuelle Row des DWs noch nicht unbedingt die, die es sein
    soll
-   ist die aktuelle Column des DWs noch nicht unbedingt die, die es
    sein soll
-   ACHTUNG: Rückgabewert beachten -- wenn jedesmal false geliefert
    wird, kommt es zu einer Endlosschleife !!!!!!!!!!
-   Wurde für folgende Konstellation eingeführt:
-   Grid DW-1
-   Darunter bzw. rechts daneben bzw. auf einer weiter rechts liegenden
    Tabpage (siehe dazu DwOrderOnTab): Grid DW-2
-   Es existiert 1-zu-n- Relation zwischen den Selects aus DW-1 und DW-2
    (DW-1 ist die 1- Seite)
-   In DW-2 sollen nur die zur aktuellen Row in DW-1 gehörigen Rows
    anzezeigt werden
-   Vorgangsweise:
-   Im BeforeOnSetpresentation- Eventscript von DW-2 wird dies mittels
    uf_filter realisiert (dazu muss die aktuelle Row von DW-1 mittels
    uf_GetRow ausgelesen werden)
-   es sind aber weiter Anwendungen denkbar - aber bitte voher
    Rücksprache halten

## BeforeUpdate

##### Argumente

##### Rückgabewert

-   boolean
-   true ( Save des Master- Detail- Verbunds wird fortgesetzt false (
    Save des Master- Detail- Verbunds wird abgebrochen

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   Ist eines der Event- Scripts, welche beim Speichern eines Master-
    Detail- Verbunds aufgerufen werden.
-   Das System führt beim Speichern folgenden Ablauf aus: . Beginn der
    Transaction, wenn Speichern vom Menü aus erfolgt . für alle DWs des
    Master- Detail- Verbunds: . gegebenenfalls Zeilennummern- Column
    setzen (siehe uf_SetLineNrCol) . gegebenenfalls Key- Felder des AOTs
    ins DW eintragen
-   hier kann allerdings der Key des AOTs noch nicht feststehen, darum
    erfolgt das Eintragen der Keyfelder weiter unten nochmals. . Aufruf
    von BeforeUpdate . gegebenenfalls Key- Felder des AOTs ins DW
    eintragen . Felder auf NULL prüfen (siehe event DarfNullOnUpdate) .
    für alle DWs des Master- Detail- Verbunds: . Aufruf von
    BeforeUpdateDetail . gegebenenfalls Key- Felder des AOTs ins DW
    eintragen . Für alle gelöschten Rows Aufruf von
    ForDeletedRowOnUpdate . Speichern des DWs mittels Event OnUpdate .
    für alle DWs des Master- Detail- Verbunds: . Aufruf von AfterUpdate
    . Master- Detail- Verbund in den Status "Display" bringen! . für
    alle DWs des Master- Detail- Verbunds: . Aufruf von AfterUpdateOk
-   Hier ist der Save- Vorgang erfolgt, es fehlt lediglich der Commit.
-   Über das Argument ab_RollbackAll des Events AfterUpdateOk kann
    allerdings ein Rollback erfolgen (siehe dort!).
-   Hier können auch Aufrufe von z.B. dw_ApplObj.uf_ChangeItem erfolgen
-   Wenn hier direkt oder indirekt ein Aufruf von wf_Save auf den
    gleichen Master- Detail- Verbund erfolgt:
-   muss bedacht werden, dass die AfterUpdateOk- Aufrufe der
    nachfolgenden DWs des Verbunds für den späteren wf_Save vor jenen
    für den früheren wf_Save erfolgen!!! - Am besten es wird nur das
    AfterUpdateOk für das Master- Dw verwendet
-   kommt es zu einer Endlosschleife, wenn die nicht durch eine
    entsprechende if- Abfrage abgefangen ist
-   ACHTUNG: nach dem AfterUpdateOk muss das gespeicherte AO wieder das
    aktuelle AO sein!!! ( Bei wf_New oder bei Änderung der Row in der
    Liste muss man
-   sich vorher die Row in der Liste mittels GetRow auslesen und merken
    und danach mittels ScrollToRow wiedeherstellen, wenn keine Rows vor
    der Aktuellen Row eingefügt oder gelöscht wurden
-   sich vorher unter Zuhilfenahme von cst_ApplEnv.uf_KeyFindWhere den
    Key der aktuellen Row in idw_list merken und danach mittels
    wf_ScrollToFindWhere diese Row wieder zur aktuellen machen, wenn
    Rows vor der Aktuellen Row eingefügt oder gelöscht wurden
-   wenn das Speichern fehlgeschlagen ist, erfolgt für jedes DW des
    Master- Detail- Verbunds ein Aufruf des Events UpdateFailed
-   wenn speichern aus dem Menü erfolgt ist: . Commit der Transaction
    bei Erfolg - Rollback, wenn Speichern abgebrochen wurde . Aufruf von
    AfterMenuSave, wenn das Speichern erfolgreich war . Aufruf von
    AfterMenuSaveFailed, wenn das Speichern nicht erfolgreich war
-   Achtung bei Fernsteuerungen - siehe w_ApplObj.wf_Save

## BeforeUpdateDetail

##### Argumente

##### Rückgabewert

-   boolean
-   true ( Save des Master- Detail- Verbunds wird fortgesetzt false (
    Save des Master- Detail- Verbunds wird abgebrochen

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   siehe BeforeUpdate

## CallConstSearch

##### Argumente

-   ai_aeo
-   Nummer des AEO's
    -   as_PraefixIdName
-   Päfix + Name des AEOs wie z.B. "ein_auf"

##### Rückgabewert

-   (None)

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   Hier wird bestimmt, welche Key- Werte beim Aufruf eines Search-
    Windows konstant sind.
-   Defaultmäßig sind dies alle, welche konstant sein können und lt.
    cst_ApplEnv.uf_AddAotEo für Search konstant sein sollen außer der
    Eigen- Key des AEOs für welches die Search- Funktion aufgerufen
    worden ist.
-   Dies Erfolgt über iuo_ae.uf_SetCallConst

## ClickedAppl

##### Argumente

-   ai_x
-   Abstand des Mauszeigers vom linken Rand des DatawondowObjects
-   Die Einheit von x/y muß erst experimentell ermittelt werden, bitte
    Ergebnis bekanntgeben! Sie wird möglicherweise jene sein, welche im
    DWO eingestellt ist.
    -   ai_y
-   Abstand des Mauszeigers vom oberen Rand des DatawondowObjects
    -   al_row
    -   as_column

##### Rückgabewert

-   boolean
-   true ( clicked soll weiterbearbeitet werden
-   false ( clicked soll ignoriert werden

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   wird aufgerufen, wenn die linke Maustaste gedrückt wird

## ColJumpOnNull

## `<ColJumpOnNull>`{=html}

##### Argumente

-   as_column
-   Feld, zu dem gesprungen werden soll

##### Rückgabewert

-   string
-   die Column auf die gesprungen werden soll

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   Wenn beim Speichern ein Feld, das nicht null sein darf, null ist,
    wird zu diesem Feld gesprungen
-   Ist das Feld aber nicht eingebbar, weil sein Wert aus einem
    eingebbaren Feld ermittelt wird, dann kann erreicht werden, dass zu
    diesem Feld gesprungen wird
-   siehe DwJumpOnNull

## ColSearchArg

##### Argumente

-   al_row
-   as_column
-   Column, für die das Search- Window aufgerufen wird
    -   aa_arg\[\]
-   by reference
-   Array von Argumenten für das Search- Window

##### Rückgabewert

-   (none)

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   siehe uf_DefineColSearch
-   das Event wird aufgerufen, nachdem das Search- Feld vom Anwender
    bestätigt worden ist
-   das erste Arrayelement enthält bereits den Eingabestring des Search-
    Feldes

## ColSearchData

##### Argumente

-   as_column
-   Column- Name im DWO
    -   as_data
-   by reference
-   die im Feld einggegebenen Daten

##### Rückgabewert

-   boolean
-   true, wenn ColSearch durchgeführt werden soll, sonst false

## Ableitung

-   darf überschrieben werden

##### Beschreibung

-   siehe dw_ApplObj.uf_DefineColSearch
-   Hier kann ColSearch verhindert werden
-   Hier können die eingegebenen Daten geändert werden
-   Standardfunktionalität des Events:
-   wenn as_data mit "\#" beginnt, wird '\#' entfernt und false
    returned - also kein ColSearch durchgeführt
-   ist dazu gedacht, dass wenn der Anwender z.B. die Artikelnummer
    weiß, dass er diese direkt eingeben kann und kein ColSearch
    durchgeführt wird
-   das Event kann sowohl in dw_ApplObj_tc\[i\] als auch in einem
    individuellen DW eines Windows übersteuert werden

## ColSearchNotFound

##### Argumente

-   al_row
-   Zeile aus der ColSearch aufgerufen worden ist
    -   as_column
-   Column- Name im DWO
    -   aw_ColSearch
-   das Window mit dem die Suche vollzogen wird (also z.B. der
    Artikelstamm für die eingegebene Artikel-ID)
    -   aa_ColSearchArg\[\]
-   siehe uf_DefineColSearch

##### Rückgabewert

-   (none)

## Ableitung

-   darf überschrieben werden

##### Beschreibung

-   siehe dw_ApplObj.uf_DefineColSearch
-   gibt die Standard- Fehlermeldung für "keine Daten gefunden" aus

## ColSelectLiteral

##### Argumente

-   ai_colid
-   Nummer der Column

##### Rückgabewert

-   boolean
-   true ( Column wird durch Lookup immer befüllt
-   false ( Column wird durch lookup beim Retrieve nicht befüllt

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   sollte nur in einer Applikations- Basisklasse verwendet werden
-   Eine Ausnahme ist gegeben, wenn alle Columns Literals sind, dann
    kann hier einfach "return true" stehen.
-   Es gibt 2 vorgeschlagene Möglichkeiten der Bestimmung:
    -   true, wenn Column keine Update- Property hat ( Defaultverhalten
        aber nicht empfohlen!
    -   true, wenn DB- Name der Column mit \_ endet ( empfohlen
-   Der DW- Column- Name darf allerdings nicht mit "\_" enden

## CstDwApplObj

##### Rückgabewert

-   cst_DwApplObj

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   dient dazu, dem DW eine eigene Ableitung von cst_DwApplObj
    "unterzujubeln"
-   damit kann die Applikation Werte, die für alle Instanzen eines DWs
    (also z.B. alle Instanzen des idw_neu eines w_artik) gelten ,
    speichern
-   wurde für dw_x_txt aus Tradecontrol eingeführt:
-   dw_x_txt hat ein Event DefineParams
-   dieses wird im definition- Eventscript aufgerufen und dient zum
    ermitteln der Werte von Konfigurationsparametern (z.B. Name des
    Textfeldes)
-   diese Werte werden dann in iuo_DwApplObj gespeichert
-   DefineParams wird dann z.B. in w_artik übersteuert - und es wird
    dort z.B. für das Textfeld "artik_txt" übergeben
-   diese Werte stehen dann bei jeder Instanzireung eine idw_neu eines
    w_artik zur Verfügung

## DarfChangeInDisplay

##### Argumente

##### Rückgabewert

-   boolean
-   true, wenn für das DW Änderungen im Status Display erlaubt sein
    sollen
-   als Änderungen gelten:
    -   ChangeItem
    -   uf_NewLine
    -   uf_DeleteLine (auch wenn diese durchBenutzereingaben initiert
        werden)

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   hiermit kann verhindert werden, dass das Window durch Änderungen in
    diesem DW in den Zustand Update kommt.
-   ACHTUNG: Auswertung erfolgt nur beim Öffnen des windows, also
    statisch!!!
-   im ApplicationServerModus kann durch return True in idw_neu
    verhindert werden, dass das Window in den Status Update kommt - noch
    nicht ganz ausgereift - Aufgabe5416

## DarfChangeItemInDisplay

##### Argumente

-   as_column

##### Rückgabewert

-   boolean
-   true, wenn für as_column uf_ChangeItem im Status Display erlaubt
    sein soll

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   uf_ChangeItem darf im Status Display nicht erfolgen
-   Diese Regel kann hier für eine Column außer Kraft gesetzt werden
-   ACHTUNG: Auswertung erfolgt nur beim Öffnen des windows, also
    statisch!!!

## DarfDeleteLine

##### Argumente

-   al_NewRow
-   Zeilennummer der potentiellen neuen Zeile
    -   ac_AufrufVon
-   gibt an, von wo aus neue Zeile angelgt würde "m" ( "Zeile löschen"
    bzw. "Zeile ausschneiden" im Menü "s" ( von einem Script des
    Applikationsprogrammierers aus

##### Rückgabewert

-   boolean
-   true, wenn das Löschen einer Zeile möglich sein soll, sonst false

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   Dient zur Entscheidung, ob der Menüpunkt "Zeile löschen" aktiviert
    ist.
-   Für idw_neu und alle DWs mit der selben Update- Table nicht
    notwendig!
-   siehe unbedingt Ancestor- Script!
-   Siehe auch Event UpdateIsPossible, NewIsPossible, dw_ApplObj.event
    Darf\*

## DarfEnable

##### Argumente

##### Rückgabewert

-   boolean
-   true, wenn das DW enabled werden darf sonst false

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   hier kann abhängig von Feldinhalten ein DW enabled werden

## DarfNewLine

##### Argumente

-   al_NewRow
-   Zeilennummer der potentiellen neuen Zeile
    -   ab_insert
-   Argument ist nur aus Abwärtskompatibilitätsgründen verhanden und
    wird irgendwann eliminiert!
    -   ac_AufrufVon
-   gibt an, von wo aus neue Zeile angelgt würde "i" ( (insert) "Zeile
    einfügen" im Menü oder paste aus Menü, wenn in der Position der
    aktuellen Zeile gepastet wird "t" ( (TabedDownOut) Durch "Pfeil nach
    unten" vom Benutzer oder durch "Zeile nach der aktuellen Zeile
    einfügen" im Menü oder paste aus Menü, wenn Zeile Kopiert ist, und
    hinter die letzte Zeile gepastet wird "s" ( von einem Script des
    Applikationsprogrammierers aus

##### Rückgabewert

-   boolean
-   true, wenn das Einfügen/Anhängen einer neuen Zeile möglich sein
    soll, sonst false

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   Dient zur Entscheidung, ob der Menüpunkt "Neue Zeile" aktiviert ist.
-   Für idw_neu und alle DWs mit der selben Update- Table nicht
    notwendig!
-   siehe unbedingt Ancestor- Script!
-   Siehe auch Event UpdateIsPossible, NewIsPossible, dw_ApplObj.event
    Darf\*

## DarfNullOnUpdate

##### Argumente

-   as_column

##### Rückgabewert

-   boolean
-   true, wenn as_column in DB null erlaubt

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   Ist eine Column vor dem INSERT/UPDATE (nach BeforeUpdate) null, ist
    dies nur erlaubt, wenn für as_column true returned wird.
-   ACHTUNG: Auswertung erfolgt nur beim Öffnen des windows, also
    statisch!!!

## DarfVisible

##### Argumente

##### Rückgabewert

-   boolean
-   true, wenn das DW visible sein soll

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   hier wird bestimmt, ob ein DW visible ist
-   ist dynamisch - wird beim Präsentieren ausgewertet

## DddwAfterRetrieve

##### Argumente

-   adwc\_
-   Datawindowchild
-   hiermit kann man aus dem DW des DDDWs Werte herausholen
-   dazu sind folgende Funktionen, erlaubt:
    -   RowCount()
-   liefert die Anzahl der Zeilen, kann bei leerem DW auch NULL liefern
    -   GetItem\[Date\|DateTime\|Decimal\|Number\|String\|Time\]
-   siehe ds\_
    -   al_row
-   betroffene Row des DWs
    -   as_Column
-   betroffene Column des DWs
    -   al_DddwRows
-   Anzahl der Rows im DDDW

##### Rückgabewert

-   (None)

## Ableitung

-   darf überschrieben werden
-   darf erweitert werden

##### Beschreibung

-   Hier kann nach dem Retrieve des entsprechenden DDDWs z.B. ein Wert
    aus dem Dddw- DW ausgelesen werden und vorgeschlagen werden
-   siehe auch uf_DddwRetrieve

## DddwBeforeRetrieve

##### Argumente

-   al_row
-   betroffene Row des DWs
    -   as_Column
-   betroffene Column des DWs

##### Rückgabewert

-   boolean
-   true ( Select des DDDWs wird neu aufgebaut.
-   false ( Select des DDDWs wird nicht neu aufgebaut

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   Hier kann vor dem Retrieve des entsprechenden DDDWs dessen Select
    mittels uf_DddwSetSelectSubst verändert werden.
-   Die Where- Bedingung der Standard- DDDWs (d_dddw_ao\*, d_dddw_kz)
    haben als Where- Bedingung standardmäßig "1 = 1". Dies kann mittels
    uf_DddwSetSelectSubst durch die gewünschte Bedingung ersetzt werden.
-   siehe auch uf_DddwRetrieve

## Wann verwenden

-   Where- Bedingung des DDDW muß dynamisch (= vor dem Retrieve)
    verändert werden.

Siehe auch - DddwWhere - uf_SetSelectSubst

## DddwRetrieve

##### Argumente

-   adwc\_
-   Typ ist DataWindowChild
-   wird für adwc.retrieve ( \[Retrievelargument\] \[,\] ... ) benötigt
    -   al_row
-   betroffene Row des DWs
    -   as_ColName
-   betroffene Column des DWs
    -   al_RetrieveRet
-   by reference, muß gesetzt werden
-   Anzahl der Rows im DDDW nach dem Retrieve
-   -1, wenn Retrieve versagt hat
-   kann 1:1 von adwc.retrieve übernommen werden
-   muß genau dann belegt werden, wenn true returned wird

##### Rückgabewert

-   boolean
-   true ( Retrieve des DDDWs ist hier im Script erfolgt
-   false ( Standard- DDDW- Retrieve soll vom System durchgeführt werden

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   Standardmäßig wird DDDW ohne Retrievel- Arguments retrieved.
-   Hier kann Retrieve mit Retrievel- Arguments erfolgen.
-   Es kann das DDDW hier allerdings auch auf andere Art und Weise als
    durch Retrieve befüllt werden. Sollte dies benötigt werden, bitte
    Rücksprache halten!
-   siehe auch uf_DddwRetrieve

## Wann verwenden

> Wenn DDDW eigenes DataWindowObject mit RetrievelArguments hat Wenn
> DDDW nicht über Retrieve befüllt wird. Siehe Beschreibung!

Siehe auch - DddwWhere

## DddwTransaction

##### Argumente

-   as_colname
-   Columnname des DDDWs
    -   ab_PfuKz
-   wird nur zur Übergabe an das Super- Script benötigt

##### Rückgabewert

-   tr\_
-   Transaction- Object für das DDDW

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   Hier kann das Standard- Transaction- Object für ein DDDW übersteuert
    werden
-   Default ist:
    -   sqlca bei d_dddw_kz
    -   die Transaction des AOTs des Windows, sonst
-   wird nicht aufgerufen, wenn die as_colname entsprechende Column die
    Key- Column eines AEOs ist - dann ist die Transaction auf jeden Fall
    diese des AOTs des AEOs
-   Siehe Anwendungsvorschlag im Ancestorscript!

## DddwWhere

##### Argumente

-   as_colname
-   Columnname des DDDWs

##### Rückgabewert

-   string
-   Standard ist "1 = 1"
-   Bedingung für Where- Clause wie z.B. "fcol_tabelle_kz = 'a'"

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   Hier kann die Where- Bedingung der Standard- DDDWs (d_dddw_ao\*,
    d_dddw_kz) übersteuert werden, sodaß nicht alle Einträge angeboten
    werden.
-   Dies erfolgt allerdings statisch, also beim Öffnen des Windows.
-   Soll diese Einschränkung dynamisch erfolgen, ist das
    DddwBeforeRetrieve- Event- Script heranzuziehen.
-   Es können auch statische und dynamische Bedingungen kombiniert
    werden. Dann ist im retournierten Where- String ein Muster wie z.B.
    "1 = 1" vorzusehen, welches dann im DddwBeforeRetrieve- Event
    ersetzt werden kann.
-   Anmerkung zur Ausführungsreihenfolge:
-   Das Definition- Event des DWs erfolgt später
-   Das Initialize- Event des Windows erfolgt später.

## Wann verwenden

-   DDDW hat kein eigenes DataWindowObject
-   eine statische Where- Bedingung soll angegeben werden

Siehe auch - DddwRetrieve - DddwBeforeRetrieve

## default

##### Argumente

-   al_row
-   ac_pasting
-   siehe event SollPaste
-   "n" ( es wird nicht gepastet "a" ( gesamtes AO wird gepastet "r" (
    Row wird gepastet (Row is über Menüpunkt in den Copy- Buffer
    gekommen)

##### Rückgabewert

-   (None)

## Ableitung

-   darf überschrieben werden
-   darf erweitert werden

##### Beschreibung

-   Wird für jede neue Zeile in einem DW aufgerufen. ( also im Zuge von
    w_ApplObj.wf_New, dw_ApplObj.uf_NewLine und beim Pasten)
-   hier sind folgende Aktivitäten sinvoll:
    -   setzen eines Wertes mit uf_ChangeItem bzw.
        uf_DefaultChangeItemNull im this- Dw
    -   Aufruf von uf_SetDefaults
    -   setzen eines Wertes mit uf_ChangeItem in anderm Dw des Master-
        Detail- Verbundes
    -   u.s.w.
-   Folgender Ablauf: (nicht vollständig) . Aufruf Event
    NewAfterInsertRow (nur bei wf_New) . Konstanten aus den Environment
    in das DW setzen . Aufruf Event RetrieveSetConst . MFA- Felder
    setzten, wenn es jeweils nur einen gültigen Wert gibt . Keyfelder
    des AOTs aus idw_list ins DW setzten - nicht bei idw_neu . Aufruf
    Event default

Siehe auch - uf_SetDefaults - w_ApplObj.event NewAfterInsertRow -
uf_DefaultChangeItemNull UNBEDINGT!!!

## definition

##### Argumente

##### Rückgabewert

-   (None)

## Ableitung

-   darf überschrieben werden
-   darf erweitert werden

##### Beschreibung

-   Hier dürfen strukturelle Zusammenhänge definiert werden.
-   Erlaubt sind folgende Funktionsaufrufe:
    -   uf_DefineColSearch
    -   uf_DefineCol2List
    -   uf_DefineColZoom
    -   uf_DefineEinIstCol
    -   uf_DefineMaster
-   siehe dw_ApplObj.event DefineMaster
    -   uf_DefineMde ff.
    -   uf_DefineMehrzeilig
    -   uf_DefineSort
    -   uf_SetLineNrCol
    -   uf_SetRetrieveLookup
    -   uf_DefineRichtextCol und das unter iuo_DwApplObj Beschriebene
-   Anmerkung zur Ausführungsreihenfolge:
-   das SetThis- Event erfolgt früher
-   das CstDwApplObj- Event erfolgt früher
-   das DefineMaster und das DefineMonitor- Event erfolgen früher
-   Das Initialize- Event des Windows erfolgt später.
-   ACHTUNG: das Event wird nur bei der 1. Instanz einer letztlich
    abgeleiteten DW- Klasse (z.B. dw_AufPosNeu) aufgerufen
-   für generische Klassen gibt es noch das Event initialize: bitte
    fragen, wenn benötigt

## DefineApplicationServer

##### Argumente

##### Rückgabewert

-   Boolean

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   wenn das DW mit dem ApplicationServer kommunizieren soll muss hier
    true retouniert werden.

## DefineGridBorder

##### Argumente

##### Rückgabewert

-   Boolean

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   standardmäßig wird bei einem Grid true retouniert.
-   true ( Border anzeigen, wenn das DW den Focus hat
-   false ( keinen Border anzeigen

## DefineMaster

##### Argumente

-   by Reference
    -   adw\_

##### Rückgabewert

-   (None)

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   ersetzt die Funktion uf_DefineMaster
-   wenn adw\_ belegt wird, wird definiert, daß this Detail von adw\_
    ist
-   siehe Master- Detail- Verbund

## DefineMonitorOf

##### Argumente

-   by Reference
    -   adw\_

##### Rückgabewert

-   (None)

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   ersetzt die Funktion uf_DefineMonitorOf
-   wenn adw\_ belegt wird, wird definiert, dass this Monitor von adw\_
    ist
-   wenn ein DW zu groß für das Window ist, kann man auf einer weiteren
    Tab- Page ein DW mit den Feldern, für die auf dem erstgenannten DW
    kein Platz ist, einführen. Dieses DW wird dann als Monitor
    bezeichnet. Das erstgenannte DW wird als gemonitortes DW bezeichnet.
-   das Monitor- DW muss auch Detail des gemonitorten DWs sein
-   Es werden keine Events des Monitor- DWs aufgerufen - davon
    ausgenommen sind:
    -   ClickedAppl
    -   definition
-   es dürfen allerdings nur folgende Funktionen aufgerufen werden:
    -   uf_SetCol1
    -   DefineMaster
    -   DefineMonitorOf
    -   DarfEnable
    -   EnableHtmlWindow
    -   Initialize
    -   NewlineCol1
    -   RetrieveByKey
    -   SetThis
    -   TabMove
-   Bei folgenden Events wird das Script des gemonitorten DW ausgeführt:
    -   Dddw\*
-   es kann dabei die "komische" Situation auftreten, dass die
    entsprechende Column im gemonitorten DW gar kein DDDW ist, weil sie
    ein Diagnosefeld ist, aber trotzdem die DDDW- Events aufgerufen
    werden - dies geschieht dann allerdings für den Monitor
    -   CallConstSearch
    -   DarfChangeInDisplay
    -   DarfChangeItemInDisplay
    -   EditChangedAppl
    -   IAeoSearch / IAeoShow
    -   OnShow
    -   protect
    -   WindowSearch
-   alle Columns des Monitor- DWS müssen namensgleich im gemonitorten DW
    vorhanden sein
-   das Monitor- DW muss die gleiche Transaction wie das gemonitorte DW
    haben
-   das Monitor- DW als auch das gemonitorte DW müssen bis auf den
    Select- Clause das gleiche Select- Statement haben
-   wird in das gemonitorte DW eine Row eingefügt, wird diese mit der
    gleichen Zeilennummer auch in all seine Monitore eingefügt
-   wird in ein Monitor- DW eine Row eingefügt, wird diese mit der
    gleichen Zeilennummer auch in das gemonitorte DW eingefügt
-   bei Benutzereingabe im Monitor- DW wird der eingegebene Wert vom
    System mittels uf_ChangeItem in die gleiche Zeile des gemonitorten
    DWs gestellt
-   ein uf_ChangeItem im gemonitorten DW setzt das entsprechende Feld
    der gleichen Zeile in allen Monitor- DWs -- das selbe gilt für den
    Lookup nach dem retrieve
-   bei Copy und Paste wird das Monitor- DW ignoriert - alerdings wird
    berücksichtigt, ob ein zu pastendes Feld in einem Monitor eingebbar
    ist ( siehe SollPasteColumn

## DoubleClickedAppl

##### Argumente

-   al_row
-   as_column
-   ab_shift
-   ab_control
-   ab_alt

##### Rückgabewert

## boolean

-   pfu_fun DoubleClicked event abbrechen

## Ableitung

-   darf überschrieben werden

##### Beschreibung

-   Hier kann man Aktionen bei DoppelClick auf bestimmte Felder setzten.
-   ACHTUNG:
-   ein eventueller RowWechsel ist noch nicht vollzogen
-   es kann sein, dass dieser auch gar nicht vollgogen werden kann, weil
    wir z.B. in der Liste sind, und die vorige Zeile nicht gespeichert
    werden kann
-   Durch Return True können die Standard DoppelClick Funktionalitäten
    verhindert werden.

## DragDropAppl

##### Argumente

-   auo_draggedobject
-   cst_DraggedObject
-   Ist immer valid!
    -   al_row
-   die Row, auf der der Mauszeiger zum Zeitpunkt des Droppens steht
-   kann auch 0 sein
    -   as_column
-   die Column, auf der der Mauszeiger zum Zeitpunkt des Droppens steht
-   kann auch leer sein
    -   ab_UnselectRows
-   by Ref, default = false
-   true ( alle markierten Zeilen werden entmarkiert

##### Rückgabewert

## Boolean

-   true ( die Applikation hat Drop abgehandelt
-   false ( die Applikation hat drop nicht abgehandelt ( es wird vom
    System die Standard- Aktivität durchgeführt, falls es eine solche
    gibt

## Ableitung

-   darf überschrieben werden

##### Beschreibung

-   hier kann die Applikation auf das Droppen des Objets lt.
    auo_auo_draggedobject reagieren
-   das Event wird nur aufgerufen, wenn ein cst_DraggedObject
    entsprechendes Objekt gedragged wird

## DwJumpOnNull

## `<DwJumpOnNull>`{=html}

##### Argumente

-   as_column
-   Feld, zu dem gesprungen werden soll

##### Rückgabewert

-   dw_ApplObj
-   das Datewindow auf das gesprungen werden soll

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   Wenn beim Speichern ein Feld, das nicht null sein darf, null ist,
    wird zu diesem Feld gesprungen
-   Ist das Feld aber versteckt und ist in einem Monitor- DW sichtbar,
    kann über DwJumpOnNull zum Feld in diesem DW gesprungen werden
-   siehe ColJumpOnNull

## DwOrderOnTab

##### Argumente

##### Rückgabewert

-   string
-   Wert für die Sortierreihenfolge der DWs auf der Tabpage
-   das Ancestorscript liefert die y und die x- Koordinate des DWs -
    siehe dort

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   wenn ein DW später retrieved werden muss als ein DW, das weiter oben
    oder weiter links liegt, muss dieses Event für alle DWs auf der
    Tabpage übersteuert werden und somit die Reihenfolge der DWs manuell
    angegeben werden

## EditChangedAppl

##### Argumente

-   al_row
-   Zeile des DWs
    -   as_Column
-   Column des DWs
    -   as_wert
-   String im Edit- Buffer

##### Rückgabewert

-   boolean
-   false, wenn Feld nicht editiert werden soll und auf den
    ursprünglichen Wert gestellt werden soll, sonst true

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   hier kann verhindert werden, daß ein Feld, welches nicht protected
    ist, verändert werden kann
-   hier können Aktionen gestartet werden, welche durch das Editieren
    eines Feldes ausgelöst werden sollen
-   hier ist eine Meldung mit wf_information2nl auszugeben, wenn der
    Anwender eine Information erhalten soll

## EnableCopyCutRow

##### Argumente

##### Rückgabewert

-   boolean

## Ableitung

-   darf überschrieben werden
-   darf erweitert werden

##### Beschreibung

-   Bestimmt, ob der Menüpunkt Zeile Kopieren aktiv ist
-   siehe dw_ApplObj.event SollPasteRow

## EnableHtmlWindow

##### Argumente

-   al_row
-   Zeile des DWs
    -   as_Column
-   Column des DWs

##### Rückgabewert

-   boolean

## Ableitung

-   darf überschrieben werden
-   darf erweitert werden - liefert allerdings in der Basisklasse fix
    false

##### Beschreibung

-   Definiert, dass für das Feld mittels CTRL+W ein HTML- Editor
    aufgerufen werden kann
-   Das Event wird dynamisch ausgewertet
-   Das Event wird für den idw_Menu aufgerufen ( ggf. für den Monitor

## ForDeletedRowOnUpdate

##### Argumente

-   al_row
-   Row- Nummer für die Funktion uf_GetDeletedItem
-   Achtung: al_row ist nur für uf_GetDeletedItem verwendbar!!!
    -   ab_NoDelete
-   true ( Row soll in DB nicht gelöscht werden

##### Rückgabewert

-   boolean
-   false ( Save wird abgebrochen

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   Wird genau vor dem OnUpdate- Event führ jede gelöschte Row des DWs,
    welche schon in der Datenbank existiert aufgerufen.
-   Hier können z.B. Updates für die gelöschte Row erfolgen.
-   Achtung: Die Row existiert zum Zeitpunkt des Events noch in der
    Datenbank.
-   siehe BeforeUpdate
-   siehe unbedingt ACHTUNG bei DeletedCount

## GridSelectRow

##### Argumente

-   al_Row
-   aktuelle Row des DWs

##### Rückgabewert

-   (None)

## Ableitung

-   darf überschrieben werden
-   darf erweitert werden

##### Beschreibung

-   Standardmäßig geschieht im Event- Script folgendes: . die ggf.
    selektierte Zeile "entselektieren" . die Zeile lt. al_row
    selektieren
-   Selektieren ist eine Windows- Funktionalität und macht die Zeile
    standardmäßig blau
-   dies kann durch eine andere Methode, die aktuelle Zeile zu
    kennzeichnen ersetzt werden (( man kann die Kennzeichnung der
    aktuellen Zeile auch gar nicht durchführen)

## IAeoSearch / IaeoShow

##### Argumente

-   al_row
-   Row des DWs
    -   as_Column
-   Column des DWs
    -   ai_ColId
-   Nummer der Column des DWs

##### Rückgabewert

-   integer
-   interne Nummer des AEOs, dessen Window aufgerufen werden soll
-   Hierzu ist die Funktion cst_ApplEnv.uf_GetIAeo ( as_praefix,
    as_IdName ) zu verwenden.
-   wird ein Wert kleiner 1 zurückgeliefert, wir das Event OnShow
    aufgerufen

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

IAeoSearch: - Wird von einem Feld aus die Suche (Ctrl+F) gestartet, wird
das Event IAeoSearch aufgerufen, um die interne Nummer des AOTs, dessen
Window aufgerufen werden soll, zu ermitteln. - Standardmäßig wird die
Nummer jenes AOTs geliefert, für welches dieses Feld Key ist. - Trifft
dies auf mehrere AOTs zu, wird irgendeines ausgewählt (meistens das
"richtige"). Sollte doch das falsche geliefert werden, kann dies im
Eventscript korrigiert werden. - Soll es z.B. möglich sein, vom
Matchcode aus das Suchwindow zu starten, ist auch dies hier zu
definieren. IAeoShow: - sinngemäß gleich wie IAeoSearch, aber nicht für
das Suchen, sondern für das Öffnen (Ctrl+O)

## Initialize

##### Argumente

-   ib_WasDefinition

##### Rückgabewert

-   (None)

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   wird für jedes DW aufgerufen, wenn ein Window "echt" geöffnet wird.
    ("echt" bedeutet, dass das Window nicht nur aus dem Versteck geholt
    wird)

-   ACHTUNG: zum Zeitpunkt des Aufrufs hat die pfu_fun bereits das
    Datawindow- Object analysiert!!!

## ItemChangedAppl

##### Argumente

-   al_row
-   Zeile des DWs
    -   ai_column
-   Feldnummer
    -   as_column
-   Feld- Bezeichnung
-   siehe auch uf_DefineEinIstCol
    -   aa_wert
-   Wert, auf den Feld geändert werden soll
-   hat jetzt auch bei null den richtigen Datentyp
    -   aa_wert_alt
-   alter Feldinhalt
-   hat jetzt auch bei null den richtigen Datentyp
    -   ai_EnvMap
-   wird beim Aufruf von uf_lookup benötigt
    -   ab_ItemChangedField
-   true, wenn Feld das gerade vom Anwender geändert worden ist (also
    nicht bei Fernsteuerung) (dies wird intern u.a. über den EditStatus
    festgestellt) und das ItemChangedAppl- Event unmittelbar durch die
    Benutzeränderung ausgelöst worden ist
-   wird das ItemChangedAppl- Event durch ein uf_ChangeItem, das direkt
    oder indirekt aus diesem ItemChangedAppl- Event aufgerufen worden
    ist, ausgelöst, ist ab_ItemChangedField = false
-   gibt es eine Ein/Ist- Logik, kann ab_ItemChangedField nur im Ein-
    Zweig true sein

##### Rückgabewert

-   boolean
-   true, wenn das Feld geändert werden kann

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   definiert die Aktionen, welche ausgeführt werden, wenn ein Feld
    geändert werden soll
-   wird vom System aufgerufen wenn:
-   Anwender in einem Feld etwas geändert hat und das Feld verläßt oder
    mit return bestätigt
-   Feld mit der uf_ChangeItem- Funktion in einem Script geändert wird
-   Achtung: Es muß immer möglich sein, das Feld auf null zu setzen.
    Dabei müssen allerdings alle Felder, welche beim erfolgreichen
    Setzen geändert werden, auf null gesetzt werden.
-   Achtung: das, was im Ancestor- Script gestanden ist, wurde entfernt,
    weil es teilweise nicht mehr aktuell ist!
-   Achtung: der Funktionsaufruf von uf_lookup hat 2 zusätzliche
    Parameter (aa_Wert und aa_WertAlt) erhalten (siehe Ancestorscript)
-   es besteht folgender Unterschied: zunächst eine Bescheibung, was
    uf_lookup durchführt:
-   es wird für jedes AEO, dessen Keyfeld das aktuelle Feld ist (lt.
    ai_EnvMap), der Lookup durchgeführt (im nachfolgenden Beispiel
    \<0\>) neue Version:
-   ist das AEO, für das der Lookup durchgeführt wird, Keybestandteil
    eines anderen AEOs, wird dessen Keyfeld auf null gesetzt (siehe im
    Beispiel \<1\>) außer: \> aa_wert und aa_wert_alt sind beide null \>
    für das AEO, dessen Keyfeld auf null zu setzen wäre, gilt:
-   in dessen AOT gibt es ein AEO, welches das selbe Keyfeld wie das AOT
    hat
-   wenn dieses Keyfeld auch das selbe Feld, das den Lookup auslöst,
    ist, geschieht nichts weiteres (siehe im Beispiel \<2\>)
-   sonst wird für das AEO ein Lookup ausgeführt (Siehe im Beispiel
    \<3\>), außer es ist ein Keyfeld seiner Keybestandteile null (siehe
    im Beispiel \<4\>)
-   dazu ein Beispiel:
-   folgende Voraussetzungen:
-   im Env von auf_pos sind u.a.: fa, artik, lag, artik_lag
-   fa_nr, artik und lag sind im Env von artik_lag Keybestandteile
-   lag und artik_lag haben beide lag_cd als Keyfeld
-   artik hat artik_cd als Keyfeld
-   fa ist auch im Env von artik, lag und artik_lag keybestandteil
-   folgende Wirkungen:
-   wenn fa_nr geändert wird: . erfolgt Lookup auf fa \<0\> . wird
    artik_cd auf null gesetzt (der Artikel mit der gleichen
    Artikelnummer ist in einer anderen Firma vielleicht ganz ein
    anderer) \<1\> . wird lag_cd auf null gesetzt \<2\> . für artik_lag
    würde ein lookup durchgeführt wenn nicht artik_cd oder lag_cd null
    wären \<4\>
-   wenn artik_cd geändert wird . erfolgt ein Lookup auf artik \<0\> .
    wird für artik_lag ein Lookup durchgeführt \<3\> (bei der Version
    Key ausnullen würde ja lag_cd null gesetzt und so das Lager
    verlorengehen)
-   wenn lag_cd geändert wird . erfolgt Lookup auf lag \<0\> . erfolgt
    Lookup auf artik_lag \<0\>, weil ja lag_cd auch Keyfeld von
    artik_lag ist . keine weitere Aktion notwendig \<2\>
-   es darf natürlich kein Ausnullen von lag_cd erfolgen (der wurde ja
    gerade eingegeben)
-   es muss kein Lookup von artik_lag erfolgen, weil dieser ist ja
    bereits erfolgt
-   Im Ancestorscript wird die neue Version aufgerufen und es sollte bei
    neuen Projekten auch diese verwendet werden
-   bei alten Projekten sollte in der Applikationsklasse von dw_ApplObj
    (z.B. dw_ApplObj_tc) die alte Version aufgerufen werden, sodass ein
    übersteuertes und ein nicht übersteuertes Script gleich reagieren!!!

## LookupAeoFailed

##### Argumente

-   as_PraefixIdName
-   z.B.: stat_kunde: stat\_ ist das Präfix und kunde der ID-Name (=AOT-
    Name) des AEOs
    -   aa_wert
-   Wert des Keyfeldes, im obigen Bsp. Wert von stat_kunde_nr
    -   al_row
    -   ab_retrieving
-   true, wenn \> Lookup durch Retrieve oder F5 ausgelöst worden ist \>
    ein RetrieveEndAppl- Eventscript im Callstack ist \>
    uf_LookupAfterLock im Callstack ist
-   sonst false
-   ACHTUNG: bei true stehen nur die Columns aus der Table des DW's und
    der Key des as_PraefixIdName entsprechenden AEO's zur Verfügung, für
    die restlichen Columns ist ggf. der Lookup noch nicht erfolgt! Bei
    F5 kann es also passieren, dass ein Feld, das bereits im DW sichtbar
    ist, hier Null ist.
    -   ac_LookupError
-   "k" ( key nicht komplett
-   "n" ( not found
-   " " ( sonstige - i.A. kann ein Feld nicht gesetzt werden
    -   as_LookupError
-   Lookup- Fehlermeldung
-   kann individuell angepasst werden. Wenn z.B. durch einen
    zusammengesetzten Aeo Key die Fehlermeldung nicht aussagekräftig
    genug ist (KeyFelder stehen nicht in der Fehlermeldung), kann das
    angepasst werden.

##### Rückgabewert

-   char
-   'f' ... Standard: Lookup liefert false
-   't' ... Lookup liefert trotzdem true
-   'n' ... die gelookupeden Felder werden genullt und lookup liefert
    true

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   Event wird aufgerufen, wenn der Lookup auf ein AEO versagt.
-   siehe Rückgabewert
-   ACHTUNG: wenn ein AEO nicht vorhanden sein muss, sollte aber nur bei
    ac_LookupError = 'n' 't' returned werden

## MapLookedupCol

##### Argumente

-   as_PraefixIdname
-   as_DwColName\[\]
-   by reference
-   der DWO- Colname, der beim Lookup der as_PraefixIdname entsprechnden
    Tabelle nicht standardmäßig befüllt werden soll
    -   as_DbColName\[\]
-   by reference
-   der Name DbColName ist nicht ganz richtig - der Name stimmt nur
    solange kein Präfix im Spiel ist
-   es ist eigentlich der Soll- DWO- Colname lt. AEO unter
    Berücksichtigung der Weglassregel
-   ist also der DWO- Colname der Column, in die der gewünschte Wert
    durch dden Lookup gestellt wird, wenn es die Column im DW gibt
-   es muss die Column allerdings nicht im DWO vorhanden sein
-   Bsp.:
-   duest_artik_mc soll beim Lookup von duest_artik nicht standardmäßig
    durch artik.artik_mc befüllt werden ( as_DwColName\[1\] =
    "duest_artik_mc" ( as_PraefixIdname = "duest_artik"
-   stattdessen soll der Wert, der vom Lookup standardmäßig in das Feld
    duest_artik_mc_hu gestellt wird, herangezogen werden (
    as_DbColName\[1\] = "duest_artik_mc_hu"
-   dabei muss das Feld duest_artik_mc_hu im DWO gar nicht vorhanden
    sein
-   in der Tabelle artik heißt das Feld artik_mc_hu

##### Rückgabewert

-   (None)

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   das Event wird beim Create des DWs (statisch) aufgerufen
-   hier kann für die DW- Column lt. as_DwColName\[i\] definiert werden,
    dass beim Lookup des AEO's lt. as_PraefixIdname der Wert aus der DB-
    Column lt. as_DbColName\[i\] herangezogen wird
-   wird as_DbColName\[i\] nicht belegt, wird as_DbColName\[i\] beim
    Lookup von as_PraefixIdname nicht befüllt ( gleiche Funktionalität
    wie durch das Event SollLookedup - siehe dort!
-   wurde für folgende Situation eingeführt:
-   beim Lookup von artik soll abhängig von der Anmeldungssprache
    artik_mc aus artik_mc_hu befüllt werden - dies funktioniert
    allerdings nur solange sich diese nach dem Programmstart nicht mehr
    ändert

## MaxDbColNameLen

##### Argumente

##### Rückgabewert

-   integer
-   maximale Länge eines DbColName im DWO
-   Standardmäßig wird 18 geliefert (wegen Informix7)

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   wird bei ImHaus=j bein Inspizieren des DWOs ausgewertet - wenn eine
    DbColName eine Länge \> 18 hat erfolgt eine Fehlermeldung
-   wird immer für das DW selbst aufgerufen (auch bei Monitor)
-   ist eigentlich für die Projektklasse (dw_ApplOb_tci) gedacht

## MdeAfterClicked

##### Argumente

-   al_row
-   row, auf die geclicked worden ist
-   kann auch 0 sein
    -   as_column
-   Name der Column, auf die geclicked worden ist
-   ist bei ac_wo="no" leer
    -   as_wo
-   "pc" .. protected Column
-   "uc" .. unprotected Column
-   "nc" .. no Column (= ein Computed)
-   "no" .. no Object (= weder Column noch computed)

##### Rückgabewert

-   None

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   wird nur im MDE- Modus aufgerufen
-   wird im Ramen des SetPresentation aufgerufen, wenn Clicked
    vorausgegangen ist
-   siehe auch MdeClicked
-   Typische Verwendung:
-   AO- Key nach ColSearch- Funktionalität ins aufrufende Window
    zurückliefern
-   dazu wird im MdeAfterClicked- Script von idw_list, wenn
    iw_ApplObj.ic_return = 'c' ist, wf_Return aufgerufen

## MdeClicked

##### Argumente

-   ai_x
-   ai_y
-   al_row
-   row, auf die geclicked worden ist
-   kann auch 0 sein
    -   as_column
-   Name der Column, auf die geclicked worden ist
-   kann auch leer sein

##### Rückgabewert

-   boolean

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   wird nur im MDE- Modus aufgerufen
-   wird aufgerufen, wenn linke Maustaste gedrückt wurde
-   wird false returned, werden die üblichen Aktivitäten, die bei
    Clicked erfolgen nicht mehr durchgeführt
-   in den meisten Fällen wird MdeAfterClicked die bessere Wahl sein

## MdeEnter

##### Argumente

-   al_row
-   aktuelle Row zum Zeitpunkt des Tastendrucks
-   kann auch 0 sein
    -   as_column
-   Name der aktuellen Column zum Zeitpunkt des Tastendrucks
-   kann auch leer sein

##### Rückgabewert

-   boolean

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   wird aufgerufen, wenn Enter- Taste betätigt worden ist - dies
    allerdings nur im MDE- Modus
-   vor A2235:
-   wenn normalerweise durch das Enter eine neue Zeile angelegt werden
    würde und im Script false geliefert wird, erfolgt das Anlegen der
    neuen Zeile nicht
-   return false kann allerdings nicht verhindern, dass in die nächste
    Row gesprungen wird, falls es eine solche gibt
-   ab A2235:
-   wenn false zurückgeliefert wird, wird der Enter- Key total ignoriert
    ( kommt also beim Powerbuilder gar nicht an
-   ( das Event wird aufgerufen, bevor der Powerbuilder überhaupt etwas
    von der Enter- Betätigung mitbekommt
-   Typische Verwendung:
-   das MDE- Gerät hat keine TAB- Taste
-   vor A2235: . uf_JumpToField ( al_row, "xxx" )
-   "xxx" ist das Feld, in das gesprungen werden soll, nachdem das
    aktuelle Feld mit Enter bestätigt worden ist . return false
-   ab A2235: . message.uf_UiHelper().uf_SendKeyCombination ( "tab",
    false, false, false ) . return false

## MdeEscape

##### Argumente

-   al_row
-   aktuelle Row zum Zeitpunkt des Tastendrucks
-   kann auch 0 sein
    -   as_column
-   Name der aktuellen Column zum Zeitpunkt des Tastendrucks
-   kann auch leer sein

##### Rückgabewert

-   None

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   wird nur im MDE- Modus aufgerufen
-   wird nur aufgerufen, wenn es kein nicht abgeschlossenes Eingabefeld
    gibt
-   Typische Verwendung: z.B. beim ColSearch im idw_list des
    aufgerufenen Windows: Window schließen, ohne etwas zurück zu geben -
    das Schließen sollte allerdings ohne uf_NextPostNr gepostet werden

## MdeKeyDot

##### Argumente

-   al_row
-   aktuelle Row zum Zeitpunkt des Tastendrucks
-   kann auch 0 sein
    -   as_column
-   Name der aktuellen Column zum Zeitpunkt des Tastendrucks
-   kann auch leer sein

##### Rückgabewert

-   boolean

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   wird aufgerufen, wenn Punkt- Taste (deutsche Tastatur) betätigt
    worden ist - dies allerdings nur im MDE- Modus
-   wenn false zurückgeliefert wird, wird Key total ignoriert ( kommt
    also beim Powerbuilder gar nicht an
-   ( das Event wird aufgerufen, bevor der Powerbuilder überhaupt etwas
    von der Enter- Betätigung mitbekommt
-   Typische Verwendung:
-   das MDE- Gerät hat Decimal-Punkt- Taste und keine Komma- Taste
-   wir brauchen aber zum Eingeben von Komma-Zahlen ein Komma
-   Lösung: . message.uf_UiHelper().uf_SendKeyCombination ( "ger,",
    false, false, false ) . return false

## MdeProtected

##### Argumente

##### Rückgabewert

-   boolean
-   true ( das DW ist im MDE- Modus nicht betretbar

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   wird nur im MDE- Modus aufgerufen

## MdeRButtonDown

##### Argumente

-   ai_x
-   ai_y
-   al_row
-   row, auf die geclicked worden ist
-   kann auch 0 sein
    -   as_column
-   Name der Column, auf die geclicked worden ist
-   kann auch leer sein

##### Rückgabewert

-   boolean
-   false ( es werden die üblichen Aktivitäten, die bei Clicked
    erfolgen, nicht mehr durchgeführt

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   wird nur im MDE- Modus aufgerufen
-   ACHTUNG: Testen (ungetestet, noch nie verwendet) - Bei (Miss-)Erfolg
    bitte melden

## NewlineCol1

##### Argumente

-   al_NewRow

##### Rückgabewert

-   string
-   Name der Column, welche in neuer Zeile den Focus haben soll, wenn
    neue Zeile die aktuelle Zeile wird.
-   " " ( aktuelle Column
-   "1" ( Column mit der kleinsten aktuellen Taborder

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   Erfolgt:
    -   bei der Neuanlage
    -   Beim Menüpunkt Zeile einfügen
    -   Wenn im Grid nach der letzten Zeile durch TAB, Enter oder
        PfeilNachUnten eine neue Zeile entsteht
    -   ggf. beim uf_NewLine
-   standardmäßig wird Leerstring geliefert - dies bedeutet:
-   bei nicht- Grid die Column mit der kleinsten Tab- Order lt. DWO
-   bei Grid die linkeste Column
-   wenn die zurückgegebene Column protected ist, wird die erste Column
    , die nicht protected ist, die aktuelle Colum - die Reihenfolge
    dabei ist bei nicht- Grid die Taborder lt. DWO und bei Grid die x-
    Position

## OnDelete

##### Argumente

##### Rückgabewert

-   boolean
-   true, wenn Delete erfolgreich war, sonst false

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   Erfolgt im Ramen des Löschens (Menüpunkt Löschen)
-   Beim Löschen erfolgt folgender Ablauf: . Aufruf von w_ApplObj.event
    BeforeDelete . für alle DWs außer idw_neu und idw_list wird in
    irgendeiner Reihenfolge das Event OnDelete aufgerufen.
-   Liefert ein OnDelete- Script false, wird das Löschen abgebrochen und
    es erfolgt Rollback.
-   Achtung: Es dürfen im ON- Delete keine Veränderungen des Zustands
    der DWs bzw. des Windows erfolgen, weil ja nur Datenbank- Daten-
    Änderungen durch den Rollback rückgängig gemacht werden.
-   Die Standardaktion im OnDelete- Script ist: DELETE FROM
    `<update- Table des DWs>`{=html} WHERE `<Key des AOTs>`{=html} = ...
    . Zum Abschluß erfolgt der Aufruf von OnDelete für idw_neu . Aufruf
    von w_ApplObj.event AfterDelete . Aufruf von w_ApplObj.event
    AfterDeleteOk
-   Das OnDelete- Script muß im Allgemeinen nicht übersteuert werden.
-   Siehe auch w_ApplObj.event BeforeDelete

## OnDragRows

##### Argumente

-   auo_DraggedDataWindowrows
-   cst DraggedDataWindowRows
    -   as_dragicon
-   string
-   by Reference
-   hier kann das Standard- Drag- Icon überschrieben werden
-   ACHTUNG: hier einen Pfad, reletiv zum exe- Verzeichnis im Ordner
    Icons angeben - muss ein .ico- File sein

##### Rückgabewert

-   boolean
-   true ( Drag darf durchgeführt werden
-   false ( Drag darf nicht durchgeführt werden
-   Standard ist true

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   hier kann:
-   Drag unterbunden werden
-   Das Drag- Icon geändert werden
-   Weitere Anwendungen fallen mir im Moment nicht ein - bitte
    Rücksprache halten, falls solche benötigt werden

## OnKeyEnter

##### Argumente

-   al_row
-   as_column
-   ab_shift
-   SHIFT wurde gedrückt
    -   ab_control
-   STRG wurde gedrückt
    -   ab_shift_control
-   SHIFT & STRG wurden gedrückt
    -   ab\_ DwMehrzeilig
-   DWO ist mehrzeilig
    -   ab_ColMehrzeilig
-   Column ist mehrzeilig (zB Info-feld)

##### Rückgabewert

-   Boolean
-   derzeit noch keine auswirkung

## Ableitung

-   darf überschrieben werden

##### Beschreibung

-   wird nach dem Accept der Column aufgerufen.
-   kann dazu verwendet werden, um bei Enter ins nächste Feld zu
    springen.

## OnShow

##### Argumente

-   al_row
-   as_column
-   ab_computed
-   ab_independent
-   true ( das Window wird unabhängig vom aufrufenden Window geöffnet

##### Rückgabewert

-   none

## Ableitung

-   darf überschrieben werden

##### Beschreibung

-   wird die Brillen=Öffnen=Show- Funktionalität aufgerufen, und das
    Event IAeoShow liefert einen Wert \< 1, wird das Event OnShow
    aufgerufen.
-   dies kann z.B. dazu verwendet werden, beim öffenen einer URL den
    WebBrowser aufzurufen

## OnUpdate

##### Argumente

##### Rückgabewert

-   boolean
-   true, wenn Update erfolgreich war, sonst false

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   erfolgt im Ramen des unter BeforeUpdate beschriebenen Ablaufs und
    führt standardmäßig den eigentlichen Update des DWs durch
-   Das OnUpdate- Script muß im Allgemeinen nicht übersteuert werden.
-   Ist z.B. zu übersteuern, wenn gar kein update auf das DW
    durchgeführt werden soll, weil Updates nicht auf die Update- Table
    des DWs erfolgen.

## OnUpdateError

##### Argumente

-   ac_row \> 'r' ( Fehler bei der Row lt. al_row \> 'd' ( Fehler beim
    Delete einer Row \> 'f' ( Fehler bei einer gefilterten Row
-   al_row
-   nur bei ac_row = 'r' zu verwenden
    -   atr\_
-   Transaction des DWs

##### Rückgabewert

-   boolean
-   true ( Fehlermeldung von der Applikation ausgegeben ( System soll
    keine Fehlermeldung ausgeben
-   false ( Fehlermeldung soll vom System ausgegeben werden

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   wird aufgerufen, wenn beim Update des DWs ein SQL- Fehler auftritt
-   "Row changed between retrieve and Update" wird allerdings vom System
    bereits vorher abgefangen und OnUpdateError geht nicht auf
-   bei einer P- Key Verletzung in idw_neu wird eine benutzerlesbare
    Meldung ausgegeben - etwa: "Auftrag 4711 ist bereits vorhanden" -
    dabei ist "Auftrag" übersetzt ( der entsprechende Programmcode steht
    im Event- Script von OnUpdateError und kann mittels Super aufgerufen
    werden
-   siehe tr\_.uf_SqlException2nl
-   hier kann eine Applikationsspezifische Meldung ausgegeben werden
-   sonst darf hier nichts erfolgen!

## PasteColumnWert

##### Argumente

-   al_CpRow
-   Zeile des Copy- Buffers des DWs
    -   al_row
-   Zeile des DWs, die gerade aufgebaut wird
    -   as_column
-   Feldname
    -   aa_wert
-   Wert aus dem Copy- Buffer
    -   ac_pasting
-   "a" ( gesamtes AO wird gepastet "r" ( Row wird gepastet (Row is über
    Menüpunkt in den Copy- Buffer gekommen)

##### Rückgabewert

-   any
-   Wert, welcher ins DW gestellt werden soll

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   Das Übersteuern des Eventscripts sollte eigentlich nicht notwendig
    sein
-   siehe dw_ApplObj.event SollPaste

## protect

##### Argumente

-   al_row
-   Zeile des DWs
    -   ai_column
-   Feldnummer
    -   as_column
-   Feldname
    -   ac_status
-   Status des Master- Detail- Verbunds, siehe uf_Status()
    -   ab_RowNew
-   true, wenn Row noch nie abgespeichert war
    -   ab_PastingAo
-   System ist beim Pasten eines Aos
-   siehe Event SollPaste

##### Rückgabewert

-   any
-   true ( auf jeden Fall protected
-   false( abhängig von der Feldberechtigung protected
-   'n' ( auf jeden Fall nicht protected

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   Hier kann der Programmierer definieren, unter welchen Bedingungen
    ein Feld protected ist.
-   für Monitor- DWs wird das Event- Script des gemonitorten DWs
    aufgerufen (siehe DefineMonitorOf)

## Beispiel

(wg.Any-Rückgabewert): \## call super::Protect

## if classname(AncestorReturnValue) = "boolean" then

if AncestorReturnValue then return true end if lb_n = false \## else

// "n" wurde returniert lb_n = true \## end if

## if uf_GetItem(1, "wf_lim_gen_kz_db") = "w" then

return true \## end if

## if lb_n then

return "n" \## end if

## return false

## RetrieveByKey

##### Argumente

##### Rückgabewert

-   integer
-   Anzahl der gefundnen Rows, wenn Select OK
-   ACHTUNG: wenn der Returnwert \>= 0 ist, muss er genau der Anzahl der
    Rows im DW entsprechen!!!!
-   -1 bzw. NULL, wenn nicht OK

## Ableitung

-   muß überschrieben werden

##### Beschreibung

-   Führt retrieve des DWs durch
-   dies erfolgt durch den Aufruf von retrieve ( Retrievelargument_1,
    ... Retrievelargument_n )
-   String- Argumente sind mit uf_arg zu behandeln
-   es müssen nicht unbedingt Retrievelargumente vorhanden sein
-   die Funktion retrieve() des Datawindowcontrols darf ausschließlich
    im RetrieveByKey- Event- Script verwendet werden!!!
-   Hat ein DW keinen SELECT, kann hier das DW anderweitig befüllt
    werden
-   Das DW kann hier auch mittels reset() gelöscht werden
-   die Funktion reset() des Datawindowcontrols darf ausschließlich im
    RetrieveByKey- Event- Script verwendet werden!!!
-   ACHTUNG:

## RetrieveEndAppl

##### Argumente

-   al_VonRow
-   von dieser Zeile an wird das Event aufgerufen
-   ist derzeit immer 1, kann aber in einem späteren Zweig lt. ac_zweig
    \> 1 sein
    -   al_BisRow
-   bis zu dieser Zeile wird das Event aufgerufen
-   ist derzeit immer die Anzahl der Rows im DW, kann aber in einem
    Späeren Zweig lt. ac_zweig kleiner sein.
    -   al_RowCount
-   Anzahl der Rows im DW
    -   ac_zweig
-   'r' ( nach Retrieve des DWs - nicht beim Aufruf von uf_Refresh 'a' (
    nach dem Aktuallisieren (F5) - oder dem Aufruf von uf_Refresh 'p' (
    Beim Paste des Aos 's' ( nach dem Sortieren
-   erfolgt nur, wenn das DW eine Sortierung hat
-   erfolgt bei nicht idw_list nur, wenn es mit uf_DefineSort definiert
    ist
-   auch beim Retrieve erfolgt Sortieren, wenn das DW eine Sortierung
    hat - Folgender Ablauf: . Retrieve . Lookup - nicht bei idw_list .
    Aufruf RetrieveEndAppl mit ac_zeig='r' . Sortieren (+
    Gruppenkalkulation) . ggf. Aufruf RetrieveEndAppl mit ac_zeig='s'
-   Auch nach uf_Sort
    -   ab_RetrievedDw
-   true ( das DW selbst wurde retrieved
-   Z.B. sind DB- Felder nur in diesem Fall mit dem Wert aus der
    Datenbank zu belegen
-   false ( das DW selbst wurde nicht retrieved

##### Rückgabewert

-   (None)

## Ableitung

-   darf überschrieben werden
-   darf erweitert werden

##### Beschreibung

-   Zu diesem Zeitpunkt sind Lookups bereits durchgeführt
-   für uf_ChangeItem's wird ItemChangedAppl aufgerufen (-\> es erfolgen
    Lookups)
-   Achtung: uf_status() liefert ggf. 'r' bzw. 'u'
-   hier dürfen keine Zeilen eingefügt werden
-   dies hat im RetrieveByKey- Eventscript zu erfolgen, wenn diese mit
    den retrieved Zeilen gleichwertig sind - weil nur dann erfolgt der
    Lookup richtig
-   für dw_ApplObjList hat dies stattdessen im RetrieveList- Eventscript
    zu erfolgen
-   dies hat im AfterRetrieve zu erfolgen, wenn das einfügen der Zeilen
    bereits im Zustand Display erfolgen soll
-   wird auch für idw_list aufgerufen

## RetrieveEndApplNachSort

##### Argumente

##### Rückgabewert

-   boolean

## Ableitung

-   sollte nur bei generischen- Applikationsklassen verwendet werden

##### Beschreibung

-   siehe uf_DefineSort

## RetrieveSetConst

##### Argumente

-   al_Row

##### Rückgabewert

-   (None)

## Ableitung

-   darf überschrieben werden
-   darf erweitert werden

##### Beschreibung

-   hier können/müssen Columns des eigenen DWs befüllt werden, welche
    einen konstanten Wert haben. Konstant bedeutet in diesem
    Zusammenhang:
-   Der Wert der Column darf von keiner anderen Column irdend eines DWs
    des aktuellen Windows abhängen. Ausgenommen davon sind andere DWs,
    welche sowohl zum Zeitpunkt des Retrieve des DWs als auch vor dem
    Neuanlegen einer Zeile immer vollständig retrieved sind.
-   Das heißt, bei idw_neu dürfen konstante Columns von keiner Column
    eines anderen DWs als idw_list des aktuellen Windows abhängen.
-   Das Event wird sowohl beim Retrieve als auch bei Neu bzw. neue Zeile
    aufgerufen.
-   Das Event wird vor dem default- Event aufgerufen
-   Das Befüllen erfolgt zwar über uf_ChangeItem, es wird aber kein
    ItemChangedAppl- Event ausgelöst (( auch kein Lookup) Beim Retrieve
    werden allerdings davon unabhängig ggf. die nötigen Lookups
    durchgeführt.
-   Bei einer neuen Zeile bzw. beim Ändern von Key- Feldern kann der
    Lookup auf ein der konstanten Column entsprechendes AEO im
    ItemChangeAppl- Event bei der Behandlung eines anderen Feldes
    nachgeholt werden. Siehe dazu z.B. Tradecontrol -
    Inventurbereichserfassung - Zeilen - Lagercode.
-   Die Konstanten Columns werden allerdings ggf. ins ENV gestellt!

## RichTextSettings

##### Argumente

## o al_Row

## o as_RichTextColName

## o auo_RichTextCol

-   folgende Werte können zb. hierüber ermittelt werden:
    -   auo_RichTextCol.ii_Precision
-   Anzahl der Stellen lt. DWO
    -   auo_RichTextCol. iuo_ColtypeCol.ii_AnzStellen
-   Anzahl der Stellen lt. pfu_coltype
-   hmp fragen, wenn zusätzliche Informationen benötigt werden \## o
    as_PlainTextColName

## o auo_PlainTextCol

-   hier könnte z.B. die Feldlänge ausgelesen werden \## o ac_CalledFrom

-   "w" ( vor dem Aufrufen des RichtextEditWindows ( um Werte für dessen
    Einstellungen zu erhalten

-   "r" ( nach dem Retrieve ( FontSize auf ai_DisplayFontSize setzen,
    wenn diese \<\> ai_DbFontSize V

-   "d" ( vor dem default- Event wird das Feld lt. as_DefaultFont und
    as_DefaultFontSize initialisiert

-   "i" ( Aufruf nach dem ItemChanged des RichTex-Feldes

-   "f" ( Aufruf nach dem ItemChanged des Fett-JN-Feldes

-   "u" ( Aufruf nach dem ItemChanged des Unterstreichen-JN-Feldes

    -   Folgende by Reference- Parameter:

-   damit werden Einschränkungen gesetzt

    -   as_DefaultFont

-   siehe as_CalledFrom

-   wenn as_DefaultFont leer oder null ist wird "arial" angenommen

-   wenn der Font lt. as_DefaultFont nicht in as_Fonts enthalten ist,
    wird der Wert von as_DefaultFont am Ende an die Font- Liste von
    as_Fonts angehängt

    -   ai_DefaultFontSize

-   siehe as_CalledFrom

-   wenn as\_ ai_DefaultFontSize leer oder null ist wird 10 angenommen

-   wenn die FontSize lt. as_DefaultFontSize nicht in as_EditFontSizes
    enthalten ist, wird der Wert von as_DefaultFontSize am Ende an die
    FontSize- Liste von as_EditFontSizes angehängt

    -   as_Fonts

-   durch Strichpunkt getrennte Liste von Font- Namen

-   wenn die Liste nach dem eventuellen Anhängen von as_DefaultFont
    genau einen Fontnamen enthält, wird beim Übernehmen aus dem
    Richtext-Eingabe-Fenster dieser Font für das gesamte TextFeld
    gesetzt

    -   as_FontSizes

-   durch Strichpunkt getrennte Liste von Schriftgrößen (jeweils in
    Punkt)

-   wenn die Liste nach dem eventuellen Anhängen von ai_DefaultFontSize
    genau eine FontSize enthält, wird beim Übernehmen aus dem Richtext-
    Eingabe-Fenster diese Font-Size für das gesamte TextFeld gesetzt

    -   ai_WidthInPixels

-   Breite des Richtext- Eingabebereichs in Pixel

-   wird von der Spaltenbreite das Datawindows vorgeschlagen

    -   ai_HeightInPixels

-   Höhe des Richtext- Eingabebereichs in Pixel

    -   ai_MaxTextHeightInPixels

-   maximale Höhe des Richtext in Pixels

-   Anmerkung: kann größer als ai_HeightInPixels sein - dann wird ggf.
    gescrollt

-   Wenn diese Höhe überschritten wird, wird dies anprominenter Stelle
    im RichTextEditWindow angezeigt und der Text kann nicht übernommen
    werden

-   REALISIERUNG: Protected Overrides Sub OnContentsResized(e As
    System.Windows.Forms.ContentsResizedEventArgs)
    MyBase.OnContentsResized(e) If PreferredSize.Height \> 100 Then
    MsgBox("zu lang") End If End Sub

    -   ab_VerticalScrollbar

-   ist entweder immer da oder nie da - sonst müsste man abhängig von
    der Textlänge die Fensterbreite ändern

##### Rückgabewert

-   (None)

## Ableitung

-   darf überschrieben werden
-   darf erweitert werden

##### Beschreibung

-   siehe Argumente

## RowFocusChangedAppl

##### Argumente

-   al_Row
-   die aktuelle Row im DW

##### Rückgabewert

-   (None)

## Ableitung

-   darf überschrieben werden
-   darf erweitert werden

##### Beschreibung

-   hier darf kein kein nicht geposteter Rowwechsel im aktuellen DW
    hervorgerufen werden!!!
-   wird im SetPresentation aufgerufen wenn sich die Row seit dem
    letzten Aufruf geändert hat

## SaveAfterPaste

##### Argumente

##### Rückgabewert

-   boolean
-   true ( nach dem Pasten des Verbunds soll Save ausgelöst werden
-   false ( nach dem Pasten des Verbunds soll das Master- Dw den Fokus
    haben und kein Save erfolgen

## Ableitung

-   darf überschrieben werden

##### Beschreibung

-   siehe dw_ApplObj.event SollPaste
-   wird nur für Master- DWs aufgerufen
-   hiermit kann nach dem Pasten des Verbunds automatisches Speichern
    ausgelöst werden

## Scrollbar

##### Argumente

##### Rückgabewert

-   (None)

## Ableitung

-   darf überschrieben werden
-   darf erweitert werden

##### Beschreibung

-   wird bei mehrzeiligen DW's im Zuge des Window- Open aufgerufen
-   hier werden Scrollbars gesetzt
-   ist im Allgemeinen nicht zu verändern
-   der horizontale Scrollbar bei einem Grid mit CurrentColumn- Column
    kann nicht beeinflusst werden
-   kann im MDE- Modus anders belegt werden (if message.ib_mde then ...)

## SetLookedupOrder

##### Argumente

-   auo_LookedupCol

##### Rückgabewert

-   (None)

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   hier wird die Reihenfolge, in der die Columns einer Datenbanktabelle
    gelookuped werden, bestimmt
-   die Lookedup- Reihenfolge ist sortiert nach:
    -   auo_LookedupCol.ii_LookedupOrder1
-   wird im Script standardmäßig auf 0 gesetzt
    -   auo_LookedupCol.ii_LookedupOrder2
-   Standardbelegung: die AOT- Nummer, falls die gelookupde Column die
    PKey- Column eines AEOs ist, sonst 9999
    -   auo_LookedupCol.ii_LookedupOrder3
-   wird im Script standardmäßig auf die Taborder der gelookupden Column
    gesetzt
-   Columns ohne Taborder erhalten intern eine Taborder, welche nach der
    höchsten echten Taborder beginnt und sortiert nach der DW- Colid
    vergeben wird
-   siehe Script

## SetThis

##### Argumente

##### Rückgabewert

-   (None)

## Ableitung

-   darf überschrieben werden
-   darf erweitert werden

##### Beschreibung

-   Hier darf folgendes stehen:
    -   idw\_`<Dw- Name>`{=html} = this
-   Im window, welches das DW enthält muß es die Instance- Variable
    idw\_`<Dw- Name>`{=html} geben
-   Für jedes DW, welches in irgend einem Script angesprochen wird, ist
    SetThis auszufüllen.
-   Für idw_neu und idw_list ist SetThis nicht auszufüllen

## SollCopyDw

##### Argumente

##### Rückgabewert

-   boolean
-   true, wenn das DW beim w_ApplObj.wf_CopyAo kopiert werden soll,
    sonst false
-   wird für ein Master- DW false returned, wird für kein DW des Master-
    Detail- Verbunds kopiert

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   siehe Rückgabewert
-   siehe dw_ApplObj.Event SollPaste

## SollJumpTo

##### Argumente

-   as_Column

##### Rückgabewert

-   boolean
-   true, wenn von as_Column aus in die Dummy-column gesprungen werden
    soll, sonst false

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   von as_Column aus wird in eine Dummy-Column (MUSS tmp_jump_to
    heißen) gesprungen und dann wieder zurück nach as_Column.
-   Damit wird der Inhalt von as_Column wieder markiert.

## SollLookedup

##### Argumente

-   as_DwColname
-   Datawindowcolumn, das vom Lookup befüllt werden soll
    -   as_PraefixIdName
-   Präfix + AOT- Name des AEOs das gelookeuped wird
    -   as_DbColname
-   Datenbankcolumnname mit dessen Wert Lookup as_DwColname befüllen
    soll

##### Rückgabewert

-   boolean
-   true, wenn as_DwColname vom Lookup befüllt werden soll

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   das Event wird beim Create des DWs (statisch) aufgerufen
-   hier kann verhindert werden, dass eine DW- Column von einem Lookup
    befüllt wird
-   siehe auch MapLookedupCol
-   es sollte - wenn möglich - aus Übersichtlichkeitsgründen nur eines
    der beiden Events verwendet werden oder zumindest durch einen
    Kommentar auf die Belegung des jeweils anderen Eventscript
    hingewiesen werden
-   siehe auch uf_SetRetrieveLookup

## SollNewlineOnTabDownOut

##### Argumente

##### Rückgabewert

-   boolean
-   true ( Neue Zeile wird angelegt
-   false ( Keine Zeile wird eingefügt

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

Abhängig vom Rückgabewert des Events wird eine neue Zeile angelegt, wenn
man in der letzten Zeile Tabulator oder Down drückt.

## SollPaste

##### Argumente

-   ac_pasting
-   "a" ( gesamtes AO wird gepastet "r" ( Row wird gepastet (Row is über
    Menüpunkt in den Copy- Buffer gekommen)

##### Rückgabewert

-   boolean
-   true ( DW soll gepastet werden.
-   false ( DW soll nicht gepastet werden:
-   Bei ac_pasting = "a"
-   wird überhaupt nicht gepastet wird, wenn DW = idw_neu ist
-   wird sonst mit dem nächsten DW fortgefahren

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   Für jedes DW gibt es einen Copy- Buffer, welcher alle Rows des DWs
    enthalten kann
-   Die Copy- Buffer werden folgendermaßen genutzt: \> mittels
    dw_ApplObj.wf_CopyAo kann für jedes DW des Windows jeweils der
    Inhalt in den Copy- Buffer kopiert werden. Im Windows- Cipboard wird
    dies mit dem Text "`<ApplObj>`{=html}" vermerkt. \> mittels
    dw_ApplObj.wf_CopyRow kann der Inhalt der aktuellen Row des
    aktuellen DWs in den Copy- Buffer kopiert werden. Im Windows-
    Cipboard wird dies mit dem Text "`<DwRow>`{=html}" vermerkt.
-   Wird der Menüpunkt Paste aufgerufen, kann aufgrund des Textes im
    Windows- Clipboard ermittelt werden, ob ein ganzes AO, eine Row oder
    etwas Anderes kopiert worden ist. ("`<ApplObj>`{=html}" und
    "`<DwRow>`{=html}" sind zusätzlich durch Instance- Variable
    abgesichert.)
-   Das Pasten eines Aos geht folgendermaßen vonstatten: . gleiche
    Funktionalität, wie bei Neu, nur das Initialisieren und Anlegen der
    Rows erfolgt folgendermaßen: . für alle DWs, welche im Master-
    Detail- Verbund mit idw_neu sind, wird "Pasten des DWs" durchgeführt
-   Wird der Master- Detail- Verbund gespeichert, wird der nächste
    Master- Detail- Verbund bearbeitet: . für alle DWs, des Master-
    Detail- Verbunds wird "Pasten des DWs" durchgeführt . Aufruf des
    Events SaveAfterPaste für das Master- DW
-   wenn im Eventscript true returned wird, erfolgt folgendes: .
    wf_Save(true), sodaß der Master- Detail- Verbund sofort gespeichert
    wird, und der Benutzer nicht speichern muß
-   Wird gecanceled, kann der Benutzer entscheiden ob weitergemacht wird
-   nach dem Speichern des letzten Verbunds wird das Event .....
    aufgerufen
-   Eine Fernsteuerung des Pastens läuf etwa so ab: . wf_New(true) . im
    idw_neu- Master- Detail- Verbund die entsprechenden Änderungen
    vornehmen . wf_Save
-   ist mit Parameter false aufzurufen (( Transaction muss abgehandelt
    werden) . für jedes weitere Master- DW des Windows hat folgendes zu
    erfolgen: . dw_ApplObj.uf_PasteMaster . ggf. Änderungen vornehmen .
    wf_Save(false) . wf_EndPasteAo, um den Paste- Zustand zu beenden!!!
    dabei ist folgendes zu beachten:
-   die Transaktion kann pro Master oder gesamt erfolgen
-   bei Abbruch ist unbedingt auch wf_EndPasteAo aufzurufen!!!
-   Das Pasten einer Row erfolgt mittels "Pasten des DWs"
-   "Pasten des DWs" hat folgenden Ablauf: . Event SollPaste . für alle
    Rows: . Event SollPasteRow . Neue Zeile anlegen wie bei uf_NewLine
-   siehe Default- Event . Für alle Columns: . wurde die Column bereits
    gesetzt, wird sie nicht mehr geändert . wenn das Event
    SollPasteColumn true liefert, Wert der Column über Event
    PasteColumnWert setzen . Event AfterPasteRow
-   Siehe:
    -   w_ApplObj:
    -   wf_CopyAo
    -   wf_CopyRow
    -   wf_EndPasteAo
    -   Event EnableCopyAo
    -   dw_ApplObj:
    -   uf_GetCopiedItem
    -   uf_PasteUebersteuert
    -   Event SollCopyDw
    -   Event SollPaste
    -   Event SollPasteRow
    -   Event PasteColumnWert
    -   Event AfterPasteRow
    -   Event AfterPasteMaster
    -   Event Default
    -   Event Protect
    -   Event EnableCopyCutRow
-   ACHTUNG: beim Pasten darf die Reihenfolge der Rows keine Rolle
    spielen wenn:
-   ein dynamischer Filter vorhanden ist
-   die Sortierung beim Kopieren nicht der Soll- Sortierung bein Pasten
    entspricht

## SollPasteColumn

##### Argumente

-   al_cprow
-   Row im Copy- Buffer
    -   al_row
-   gepastete Row im DW
    -   as_column
-   Name der Column
    -   ac_pasting
-   "a" ( gesamtes AO wird gepastet "r" ( Row wird gepastet (Row is über
    Menüpunkt in den Copy- Buffer gekommen)

##### Rückgabewert

-   boolean
-   true ( Column soll gepastet werden.
-   false ( Column soll nicht gepastet werden:

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden (allerdings darf super aufgerufen werden
    )

##### Beschreibung

-   Standardmäßig liefert das Event false wenn \> die Columnm ein
    Platzhalter- Feld ist \> die Column nicht eingebbar ist
-   "nicht eingebbar" bedeutet, dass das Feld auch in allen Monitoren
    nicht eingebbar ist (siehe DefineMonitorOf)
-   siehe dw_ApplObj.event SollPaste
-   siehe dw_ApplObj.event EnableCopyCutRow

## SollPasteRow

##### Argumente

-   al_row
-   Row im Copy- Buffer
    -   ac_pasting
-   "a" ( gesamtes AO wird gepastet "r" ( Row wird gepastet (Row is über
    Menüpunkt in den Copy- Buffer gekommen)

##### Rückgabewert

-   boolean
-   true ( Row soll gepastet werden.
-   false ( Row soll nicht gepastet werden:
-   Bei ac_pasting = "a" wird überhaupt nicht gepastet wird, wenn DW =
    idw_neu ist

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   siehe dw_ApplObj.event SollPaste
-   siehe dw_ApplObj.event EnableCopyCutRow

## SollRetrieveNachSave

##### Argumente

-   as_DwSave

##### Rückgabewert

-   boolean
-   true ( Nachdem das Datawindow lt as_DwSave gespeichert worden ist,
    soll das DW this retrieved werden.
-   Achtung as_DwSave ist immer das Master- DW!
-   Das Event wird nur für Master- DWs aufgerufen!

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   Das Default- Event- Script liefert nur für idw_neu true.

## StatusChangedBeforeOnSetPresentation

##### Argumente

-   ac_statusold
-   ac_statusnew

##### Rückgabewert

-   (None)

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   wird Aufgerufen, wenn sich seit dem letzten Presentation das Ergebis
    von uf_status geändert hat

## Verwendung

-   wurde zum Aufruf von uf_MapButtonAppl eingeführt

## TabMove

##### Argumente

-   as_FromTo
-   `<Name der vorigen Column>`{=html} "-"
    `<Name der akluellen Column>`{=html}
-   die Column- Namen können auch leer sein

##### Rückgabewert

-   (None)

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   geht auf, wenn Feld duch TAB- Taste angesprungen wird, oder durch
    TAB- Taste verlassen wird

## TransObject

##### Argumente

##### Rückgabewert

-   tr\_
-   Transaktionsobjekt für das DW

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   Hier kann das Transaktionsobjekt für das DW bestimmt werden
-   Standardmäßig ist dies das Transaktionsobjekt des AOTs

## UpdateFailed

##### Argumente

-   ac_zweig \> "n" ( Save aus Status New \> "u" ( Save aus Status
    Update
-   adw_failed
-   das DW, bei dem der Fehler passiert ist
    -   as_failed \> "BeforeUpdate"
-   das Eventscript BeforeUpdate hat false returned \> "uf_CheckNull" \>
    "BeforeUpdateDetail"
-   das Eventscript BeforeUpdateDetail hat false returned \>
    "uf_ForDeletedRowsOnUpdate"
-   die Aktivitäten für die gelöschten Rows sind nicht gutgegangen \>
    "OnDelete"
-   das Eventscript OnDelete hat false returned
-   siehe dazu \> "OnUpdate"
-   das Eventscript OnUpdate hat false returned \> "AfterUpdate"
-   das Eventscript AfterUpdate hat false returned \> "AfterUpdateOk"
-   das Eventscript AfterUpdateOk hat false returned

##### Rückgabewert

-   (None)

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   das Event wird aufgerufen, nachdem das Speichern () fehlgeschlagen
    ist
-   siehe BeforeUpdate

## WieProtect

##### Argumente

-   as_column
-   ab_ExpressionVorhanden
-   true -\> im DWO ist eine Protect- Expression vorhanden

##### Rückgabewert

-   char 'g' ... gf_protect 'd' ... lt. DWO 'p' ... fix protected 'n'
    ... fix nicht protected

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   Wird beim erstmaligen open des Windows für jede nicht Computed-
    Column aufgerufen
-   hier wird dem System mitgeteilt, wie das Protecten von Columns
    erfolgen soll
-   standardmäßig liefert das Event bei ab_ExpressionVorhanden=true 'd'
    und sonst 'g'
-   'd' sollte allerdings vermieden werden, weil es performancemäßig
    nicht gut ist

## WinAendKeyStr

##### Argumente

-   ab_4AllRows
-   true ( der unten beschriebene Keystring wird für alle Rows
    zurückgeliefert
-   false ( der unten beschriebene Keystring wird für die Row lt.
    al_RowGetItem zurückgeliefert
    -   adw_GetItem
-   wird bei Übersteuerung des Events hochgradig nicht gebraucht ( im
    Ancestor- Script sehr wohl)
-   ist für ab_4AllRows immer idw_neu
-   ist sonst das aktuelle DW
-   aus diesem DW werden die Key- Felder ausgelesen
    -   ab_deleted
-   true ( es wird der Keystring für eine gelöschte Zeile generiert
    -   al_RowGetitem
-   aus dieser Row werden die Keyfelder ausgelesen
    -   auo_KeyCol\[\]
-   wird bei Übersteuerung des Events hochgradig nicht gebraucht ( im
    Ancestor- Script sehr wohl)
-   Array mit allen Key- Columns vom Typ cst_DwApplObjCol (noch nicht
    beschrieben)
-   wird jeweils im nicht beschriebenen Event KeyColsDef befüllt -
    sollen diese Keyfelder in einem DW übersteuert werden, steht der
    Betreuer der pfu_fun gerne zur Verfügung
-   sind immer Columns aus adw_GetItem

##### Rückgabewert

-   string
-   der entsprechende Key- String

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   für das Historienspiel gibt es 2 Key- Strings (siehe
    pfu_fun_db.doc):
    -   Key- Anteil, der für alle Rows des DWs gleich ist Bsp. Person
        zur Adresse: AdressSnr + Personencode:
-   KeyString könnte sein: "12331.akainz"
    -   Key- Anteil, der für jede Row des DWs verschieden ist (Bsp. dazu
        DW mit Kommunikationsarten: Kommunikationsart)
-   KeyString könnte sein: "email"
-   abhängig von ab_4AllRows wird einer der beiden Strings aufgebaut

## WindowSearch

-   Beschreibung fehlt noch!!! - siehe solange Ancestorscript

### Functions

## DeletedCount

##### Argumente

##### Rückgabewert

-   Anzahl der Rows, die in der DB gespeichert sind und aus dem DW
    gelöscht worden sind
-   siehe auch uf_GetDeletedItem
-   ACHTUNG: lt. Wolfgang funktioniert dies alles nur, wenn das DW lt.
    UpdateProperties eine Update- Table eingestellt hat, weil ansonsten
    DeletedCount() 0 liefert

## find

##### Argumente

-   as_expression
-   ein Ausdruck wie in der Where- Bedingung eines Select- Statements.
    Allerdings werden statt DB- Columns DW- Columns angesprochen
-   alle Literals im Ausdruck sind mittels der Funktion
    gf_AnyToFindLiteral zu realisieren!
-   ACHTUNG dies Syntaxt ist allerdings nicht exekt gleich wie in SQL!!!
-   "ColX in" funktioniert nicht und muss mittels ( Colx = ? or Colx = ?
    ) umschrieben werden
    -   al_start
-   Suche fängt bei dieser Row an
    -   al_end
-   Suche hört bei dieser Row auf
-   al_end kann \< al_start sein, dann wird rückwärts gesucht

##### Rückgabewert

-   long
-   die erste Row in der Suchrichtung von al_start weg, welche
    as_expression erfüllt
-   0 ( keine Row erfüllt die Expression
-   null ( irgendwas ist null

## GroupCalc

##### Argumente

##### Rückgabewert

-   integer
-   1 ( erfolgreich
-   sonst ( nicht erfolgreich

##### Beschreibung

-   Berechnet die Gruppensummen neu
-   Vorher muß ggf. uf_sort erfolgen

#### uf_accept

##### Argumente

##### Rückgabewert

-   boolean
-   false -\> wenn es ein aktuelles Eingabefeld gibt, und dieses nicht
    übernommen werden kann
-   true -\> sonst

##### Beschreibung

-   Wenn es ein aktuelles Eingabefeld gibt, das noch nicht übernommen
    ist, wird es übernommen

#### uf_aktion

##### Argumente

-   al_row
-   Zeile des DWs, für welche die Aktion durchzuführen ist
-   wenn Argument nicht vorhanden ist:
-   wird die Aktion für alle Zeilen durchgeführt.
-   wird der Fehlertext ausgegeben, wenn das aktion- Event false
    liefert.
-   im zugehörigen aktion-Event-Script darf weder direkt noch indirekt
    uf_aktion ohne al_row aufgerufen werden.
    -   as_aktion
-   Bezeichnung der Aktion
    -   ac_ausloeser
-   ist noch nicht implementiert - dies erfolgt erst bei Bedarf
-   kann weggelassen werden und ist dann standardmäßig " "
-   darf nicht "e", "c", oder "a" sein
-   darf nur \<\> " " sein, wenn kein uf_aktion und kein
    ItemChangedAppl- Aufruf aktiv ist - sonst kommt eine Fehlermeldung
    und es wird mit false returned
-   der Wert wird im direkt durch den Funktionsaufruf ausgelösten und
    allen indirekt ausgelösten Aktion- Event- Aufrufen als Parameter
    übergeben
-   so kann z.B. der Aktion mitgeteilt werden, dass gewisse Aktivitäten
    (z.B. Prüfungen) nicht erfolgen müssen

##### Rückgabewert

-   boolean
-   true, wenn die Aktion erfolgreich war, sonst false

##### Beschreibung

-   Führt mit Hilfe des Events Aktion, die entsprechende Aktion für die
    entsprechenden Zeilen durch.
-   Wird uf_aktion aufgerufen, hat der Programmierer dafür zu sorgen,
    daß diese Aktion im Aktion- Event- Script abgehandelt wird.
-   Die Nomenklatur der Aktion erfolgt durch den Programmierer (= frei
    zu vergebender String).
-   siehe unbedingt Aktion

#### uf_AktionIsNull

##### Argumente

##### Rückgabewert

-   boolean
-   true, wenn im aktuellen Aktion- Script mindestens ein uf_IsNull-
    Aufruf true geliefert hat

##### Beschreibung

-   darf nur im Aktion- Script vor dem ersten uf_ChangeItem- Aufruf
    erfolgen!!!
-   ACHTUNG: vor dem Aufruf darf im Aktion- Script auf keinen Fall
    direkt oder indirekt (also z.B. durch einen uf_ChangeItem) uf_aktion
    für das aktuelle oder irgened ein anderes DW aufgerufen werden

#### uf_arg

##### Argumente

-   as_arg
-   Ein Retrievel- Argument für die Retrieve- Funktion eines DWs

##### Rückgabewert

-   string

##### Beschreibung

-   Immer wenn eine String als Retrieval- Argument übergeben wird, muß
    er durch die Funktion uf_arg behandelt werden ( retrieve ( ......,
    uf_arg ( ls_xy ) ... ) )
-   siehe auch tr\_.uf_arg!!!

#### uf_ChangeItem

##### Argumente

-   al_row
-   Zeile des DWs
    -   ai_column
-   Feldnummer
-   wird nicht übergeben, wenn as_column übergeben wird
    -   as_EinIst
-   wird genau dann übergeben, wenn ai_column übergeben wird
-   enthält "ein:", "ist:" oder ""
-   siehe uf_DefineEinIstCol
    -   as_column
-   Feldname
-   wird nicht übergeben, wenn ai_column übergeben wird
-   siehe auch uf_DefineEinIstCol
-   bei einem Ein- Ist- Feld muss as_colum mit "ein:" oder "ist:"
    beginnen
    -   aa_wert
-   Wert, auf den Feld gesetzt werden soll
-   kann auch null sein
    -   as_error
-   muß nicht vorhanden sein
-   wenn vorhanden und nicht null, wird eine Fehlermeldung ausgegeben,
    wenn Feld nicht gesetzt werden konnte
-   ACHTUNG: muss in die Sprache der Anmeldung übersetzt sein - dies hat
    mittels iuo_ae.uf_Text2nl zu erfolgen!
-   wenn nicht leer, wird as_error bei der Fehlermeldung zusätzlich
    angezeigt - Typischerweise sollte eine Information über die Position
    der Verarbeitung übergeben werden
-   Wenn beim Setzen von Feldern in Scripts, der Erfolg nicht abgefragt
    wird, weil man davon ausgeht, daß es sowieso erfolgreich sein muß,
    sollte zumindestens as_error eingesetzt werden!

##### Rückgabewert

-   boolean
-   true, wenn Feld geändert wurde

##### Beschreibung

-   Ändert den Inhalt eines Feldes und führt die dadurch notwendigen
    Aktionen durch.

#### uf_ChangeItemErr

##### Argumente

-   al_row
-   Zeile des DWs
    -   as_column
-   Feldname
    -   aa_wert
-   Wert, auf den Feld gesetzt werden soll
-   kann auch null sein
    -   as_error
-   by reference
-   Im Falle eines Fehlers (also bei return false) wird die
    Fehlermeldung nach as_error gestellt
-   ist bereits in die Sprache des Anwenders übersetzt

##### Rückgabewert

-   boolean
-   true, wenn Feld geändert wurde

##### Beschreibung

-   Ändert den Inhalt eines Feldes und führt die dadurch notwendigen
    Aktionen durch.
-   Man kann in Batchverarbeitungen mit vielen ChangeItem()s
    folgendermaßen Zeilen sparen: lb_err = true ls_err = '' if not
    uf-ChangeItemErr ( ..., ls_err ) then elseif not uf_ChangeItemErr (
    ..., ls_err ) then elseif not uf_ChangeItemErr ( ..., ls_err ) then
    ... else lb_err = false end if if lb_err then z.B. wf_Information2nl
    ( iuo_ae.uf_Text2nl ( "Fehlertext" ) + ls_error ) oder Speichern der
    Fehlermeldung in der Datenbank (Bsp. : Preise des Lieferanten
    importieren: im Fehlerfall wird der Fehlertext in die Import-
    Datenbanktabelle geschrieben und kommt weder in den Job noch ins
    Errorlog) z.B. continue u.s.w. end if

Die mittels wf_information ausgegebene Fehlermeldung wird jetzt in den
Job geschrieben

## uf_ChangeItemRichTextByPlainText\[Err\]

##### Argumente

## o al_row

## o as_column

## o as_PlainText

## o as_error

-   optional

##### Rückgabewert

-   boolean

##### Beschreibung

-   die Funktion ruft uf_ChangeItem\[Err\] ( al_row, as_column,
    uf_GetRichText(al_row, as_column, as_PlainText)\[, as_error\] ) auf

## uf_CountInSelect (geerbt von dw_ApplEnv)

##### Argumente

-   as_CountFrom
-   zunächst wird dieser Text von Beginn weg im Select- Statement
    gesucht.
-   Die eigentliche Suche beginnt erst ab dem obigen Vorkommnis
    -   as_text
-   Dieser Text wird gesucht
    -   ai_AnzInVirgin
-   by reference, wird gesetzt
-   Anzahl der Vorkommnisse von as_text im Orginal- Select (ohne
    Ersetzung der Suchbedinhungen)
    -   ai_AnzInAkt
-   by reference, wird gesetzt
-   Anzahl der Vorkommnisse von as_text im aktuellen Select (mit
    Ersetzung der Suchbedinhungen)

##### Rückgabewert

-   (None)

##### Beschreibung

-   Liefert die Anzahl der Vorkommnisse eines Textes im Select-
    Statement

## ScrollToRow

##### Beschreibung

-   darf nur bei idw_list verwendet werden (siehe idw_list. ScrollToRow)

#### uf_DddwSetSelectSubst

##### Argumente

-   as_pattern
-   String der ersetzt werden soll
    -   as_text
-   String durch den ersetzt werden soll

##### Rückgabewert

-   (None)

##### Beschreibung

-   Im Open- Event eines Windows wird für jedes DDDW ein Grund- Select
    abgestellt. Dieser wird vor dem Retrieve kopiert und die Kopie kann
    mittels uf_DddwSetSelectSubst verändert werden. Mit dieser
    veränderten Kopie erfolgt dann der Retrieve.
-   Ersetzt alle Vorkommnisse von as_pattern durch as_text.
-   Darf nur für DDDWs, dessen DatawindowObject kein RetrievelArgument
    haben, verwendet werden.

Siehe auch - DddwBeforeRetrieve

#### uf_DddwRetrieve

##### Argumente

-   as_column
-   Columnname des DDDWs

##### Rückgabewert

-   (None)

##### Beschreibung

-   löst den Retrieve für ein DDDW aus
-   ist notwendig, wenn dies nicht selbständig vom System erfolgt - dazu
    ein Bsp.:
-   der Retrieve des DDDWs hat Columnwerte als Retrievelarguments
-   wenn sich eine dieser Werte ändert, wird nicht automatisch ein
    Retrieve des DDDWs durchgeführt
-   uf_DddwRetrieve ist dann im ItemChangedAppl- Eventscript für die
    Retrievel- Arguments- Columns aufzurufen bzw. der Aufruf ist über
    eine Aktion abzuhandeln
-   die Events Dddw\* erhalten als al_row- Parameter die current- Row
-   ACHTUNG in einem Grid:
-   hängt das Dddw- Retrieve- Ergebnis von Feldwerten des DWs, die in
    jeder Row anders sein könnne, ab, und im Dddw wird ein anderer Wert
    als der Feldwert angezeigt, stimmt diese Anzeige nur in der
    aktuellen Zeile, weil die Werte des Dddws für alle Rows gleich sind!
-   wird auch für alle Monitore durchgeführt
-   wenn das Feld im gerade behandelten DW kein dddw ist, wird das DW
    übersprungen
-   der eigentliche Retrieve erfolgt erst beim Presentation

#### uf_DefaultChangeItemNull

##### Argumente

-   al_row
-   Zeile des DWs
    -   as_column
-   Feldname

##### Rückgabewert

-   (None)

##### Beschreibung

-   Muß eine Column unbedingt null sein, so ist sie im Default- Event-
    Script mit uf_DefaultChangeItemNull auf null zu setzen.

Siehe auch - event default

#### uf_DefineAeoPraefix

##### Argumente

-   as_praefix
-   siehe Beschreibung

##### Rückgabewert

-   (None)

##### Beschreibung

-   Beim Zuordnen von DW- Columns zu AOE's wird jedem DW- Column
    as_praefix vorangestellt
-   Anwendungsbeispiel:
-   In einem Window ist die Hauptdatenbanktabelle der Auftragskopf
-   ein Datawindow ist ein Grid mit Auftragspositionen zum Auftragskopf
-   Um zu verhindern, dass wenn das Positions-DW das aktuelle ist,
    dieses beim konstant- Setzten Werte aus idw_neu überlagert, kann dem
    Positions- Dw ein Päfix gegeben werden und der Auftragsposition im
    gf_init_applenv genau das selbe

#### uf_DefineButtonShortcut

##### Argumente

-   as_praefix
-   siehe Beschreibung

##### Rückgabewert

-   (None)

##### Beschreibung

-   Beim Zuordnen von DW- Columns zu AOE's wird jedem DW- Column
    as_praefix vorangestellt
-   Anwendungsbeispiel:
-   In einem Window ist die Hauptdatenbanktabelle der Auftragskopf
-   ein Datawindow ist ein Grid mit Auftragspositionen zum Auftragskopf
-   Um zu verhindern, dass wenn das Positions-DW das aktuelle ist,
    dieses beim konstant- Setzten Werte aus idw_neu überlagert, kann dem
    Positions- Dw ein Päfix gegeben werden und der Auftragsposition im
    gf_init_applenv genau das selbe

#### uf_DefineColSearch

##### Argumente

-   as_column
-   Column, für die Column- Search- Funktionalität durchgeführt werden
    soll

##### Rückgabewert

-   (None)

##### Beschreibung

-   wird im definition- Event- Script aufgerufen
-   wird bei Monitoren vom gemonitorten DW herangezogen
-   wenn im Feld lt. as_column vom Anwender eine Eingabe getätigt wird,
    wird jenes Window, das beim Menüpunkt "Suchen" (ctrl+f) aufgerufen
    wird, geöffnet
-   siehe dazu bei den Events
    -   CallConstSearch
    -   IAeoSearch / IAeoShow
-   es kann die Variable ib_InColSearch des auslösenden DW's ausgewertet
    werden, um z.B. beim ColSearch ein anderes Window zu öffnen als beim
    normalen search (= \^F)
-   vor dem Öffnen wird das Event ColSearchData aufgerufen - hier kann
    ColSearch verhindert werden
-   weiters wird vor dem Öffnen das Event ColSearchArg aufgerufen - Dort
    kann ein Any- Array belegt werden, welches dann im aufgerufenen
    Window in den Events ColSearchAnzSelect, BeforeSetSelectStart und
    BeforeSetSelectFinish und AfterColSearchKeySet als Parameter zur
    Verfügung steht
-   im aufgerufenen Window (w_ApplObj)
-   gibt es dann folgenden Ablauf: . Aufruf wf_query mit "noacceptquery"
    und "withnew" in as_command . Aufruf wf_AcceptQuery
-   im Zuge dessen wird das Event ColSearchNotFound des aufrufenden DWs
    aufgerufen, wenn keine Daten gefunden wurden
-   stehen für nicht standardmäßig lösbare Fälle folgende Informationen
    zu Verfügung:
-   siehe Variable w_ApplObj.ic_return
-   die Argumente stehen unter idw_return.ia_ColSearchArg zur Verfügung
-   in diesen Fällen kann auch das Event BeforeCommand übersteuert
    werden und false zurückgegeben werden und das Befüllen der Liste
    manuell erfolgen
-   es könnte sein, dass das Beschriebene in einem zukünftigen Release
    nicht mehr uneingeschränkt funktioniert

#### uf_DefineCol2List

##### Argumente

-   as_column
-   Column, für die Column- Search- Funktionalität durchgeführt werden
    soll

##### Rückgabewert

-   (None)

##### Beschreibung

-   kann im definition- Event- Script aufgerufen werden und darf nur
    dort aufgerufen werden
-   definiert, dass, wenn sich im Feld lt. as_column der Wert ändert,
    dieser in das entsprechende Feld der Liste gestellt wird
-   in idw_neu geschieht dies automatisch
-   in allen anderen DWs nur, wenn der uf_DefineCol2List- Aufruf erfolgt
    ist
-   ACHTUNG: darf nur für DWs, die maximal eine Row haben aufgerufen
    werden!!!
-   Bei Bedarf könnte es auch eine Version geben, bei der die Row nicht
    auf 1 fixiert ist - dazu würde dann allerdings ein dynamisches Event
    benötigt, durch das die Applikation dem System (ggf. sogar pro
    Column unterschiedlich) gekannt gibt, für welche Row die Werte in
    die Liste gestellt werden sollen.

#### uf_DefineColZoom

##### Argumente

-   as_Column
-   ai_dWidth
-   Breite des gezoomten Bereiches in Pixel
    -   ai_dHeight
-   Höhe des gezoomten Bereiches in Pixel

##### Rückgabewert

-   (None)

##### Beschreibung

-   darf nur im definition- Eventscript aufgerufen werden
-   das Feld wird vergrößert wenn es mit der Shift- Taste doppelgeklickt
    wird
-   die Vergrößerung erfolgt nach rechts unten, wenn kein Platz am DWO
    ist, nach oben bzw. nach links
-   für die Scrollbars des Feldes hat die Applikation in DWO zu sorgen

#### uf_DefineEinIstCol

##### Argumente

-   as_Column
-   darf keine Keycolumn eines AEOs sein -- dies wird zwar nicht
    überprüft, aber das System reagiert dann fehlerhaft

##### Rückgabewert

-   (None)

##### Beschreibung

-   darf nur im definition- Eventscript aufgerufen werden
-   darf nicht für ein Monitor- Dw aufgerufen werden
-   die Definition bewirkt, dass das Feld auf 2 logische Felder
    aufgesplittet wird
-   diese haben folgende Feldnamen:
    -   "ein:" + Feldname
    -   "ist:" + Feldname
-   die Splittung ist wirksam bei:
    -   ItemChangedAppl
    -   uf_ChangeItem
    -   DddwIdItemChanged
-   folgende Funktionalitäten, die uf_ChangeItem verwenden, belegen
    Ein/Ist folgendermaßen:
-   Lookup ( "ist:"
-   Pasten ( "ein:"
-   ACHTUNG: Wenn das Ein- Feld nicht gepastet werden soll, darf das
    Feld gar nicht gepastet werden, dies erreicht man durch
    uf_DefaultChangeItemNull auf das Ist- Feld im default- Eventscript
-   GetItemInto ( "ein:"
-   uf_SetDefaults ( "ein:"
-   siehe Wie löst man das: unerwünschte Schleifen bei Feldern, die
    sowohl eingegeben werden als auch berechnet werden

#### uf_DefineFdarst

##### Argumente

-   as_CObj
-   name einer Column oder Expression im DWO, für die die
    Felddarstellung gesetzt werden soll
-   kann weggelasen werden, dann gilt der Aufruf für alle sichtbaren
    Felder des DWs.
-   ACHTUNG - das kann bei Listen mit vielen Feldern zu massiven
    Performanceverschlechterungen führen.
    -   as_CobjFdarst
-   name einer Column oder Expression im DWO, in der der
    Felddarstellungscode steht
-   kann "" sein, damit kann für gewisse Felder der darüberliegende
    Aufruf ohne as_Cobj für ein einzelnes Feld rückgängig gemacht werden

##### Rückgabewert

-   (None)

##### Beschreibung

-   darf nur im definition- Eventscript aufgerufen werden
-   definiert, dass der Felddarstellungscode für die Felddarstellung von
    as_CObj in as_CobjFdarst steht
-   Bsp.1:
-   as_Cobj = "artikel_mc"
-   as_CobjFdarst = "warengruppen_fdarst_cd"
-   in der Warengruppe ist der Felddarstellungscode für den
    Warengruppenmatchcode verspeichert ( "warengruppen_fdarst_cd" wird
    durch den Lookup befüllt
-   so können die Matchcodes unterschiedlicher Warengruppen mit
    unterschiedlichen Felddarstellungen dargestellt werden
-   Bsp.2:
-   as_Cobj = "verfügbare_mg"
-   as_CobjFdarst = "verfügbar_fdarst_cd"
-   ist eine Expression, die von der verfügbaren Menge und von Feldern
    des Artikels abhängt
-   so kann ein "kritischer" verfügbarer Bestand mit einer
    unterschiedlichen Felddarstellung dargestellt werden

#### uf_DefineMde

##### Argumente

##### Rückgabewert

-   (None)

##### Beschreibung

-   Definiert, dass das DW im MDE- Modus zu Verfügung steht
-   siehe auch uf_DefineMdePosition, uf_DefineMdeSize
-   darf ausschließlich im definition- Script aufgerufen werden

#### uf_DefineMdePosition

##### Argumente

-   ia_x
-   X- Position am Register im MDE- Modus in Pixels
    -   ia_y
-   Y- Position am Register im MDE- Modus in Pixels

##### Rückgabewert

-   (None)

##### Beschreibung

-   siehe oben bei Argumente
-   Definiert, dass das DW im MDE- Modus zu Verfügung steht -
    uf_DefineMde muss nicht mehr aufgerufen werden, wenn
    uf_DefineMdePosition aufgerufen wird
-   darf ausschließlich im definition- Script aufgerufen werden

#### uf_DefineMdeSize

##### Argumente

-   ia_width
-   Breite des DW- Controls im MDE- Modus in Pixels
    -   ia_height
-   Höhe des DW- Controls im MDE- Modus in Pixels

##### Rückgabewert

-   (None)

##### Beschreibung

-   siehe oben bei Argumente
-   Definiert, dass das DW im MDE- Modus zu Verfügung steht -
    uf_DefineMde muss nicht mehr aufgerufen werden, wenn
    uf_DefineMdeSize aufgerufen wird
-   darf ausschließlich im definition- Script aufgerufen werden

#### uf_DefineMehrzeilig

##### Argumente

##### Rückgabewert

-   (None)

##### Beschreibung

-   definiert, dass ein DW mehrere Zeilen haben kann
-   bei einem Grid- DWO muss uf_DefineMehrzeilig nicht explizit
    aufgerufen weren
-   darf nur im definition- Eventscript aufgerufen werden

#### uf_DefineRedundantLookupCol

##### Argumente

-   as_ColName

##### Rückgabewert

-   (None)

##### Beschreibung

-   Definiert ein redundantes Lookup- Feld:
-   Colum muss im DWO Update- Property haben und ist daher kein
    Platzhalter- Feld und wird daher nicht in jeder Art von Lookup
    gesetzt
-   Column soll aber trotzdem bei jeder Art von Lookuo gesetzt werden
-   Bsp.: Adressmatchcode im Kunden:
-   Ist im Kundenstamm redundant verspeichert ( Update- Property
-   Beim Speichern der Adresse wird der redundante Matchcode im
    Kundenstamm durch einen expliziten Update abgeglichen
-   Wenn allerdings zu diesem Zeitpunkt der entsprechende Kunde gerade
    neu angelegt wird und noch nicht gespeichert ist, ist dieser Update
    natürlich wirkugslos
-   Deshalb wird vor dem Speichern bei der Neuanlage die Adresse gelockt
    und mittels uf_LookupAfterLock neu gelookuped
-   Ohne uf_DefineRedundantLookupCol würde der Matchcode nicht gesetzt
    werden

#### uf_DefineRefreshOnChangeOf

##### Argumente

-   adw_DwAenderung
-   darf nicht im Verbund sein
-   darf nicht in den Update Status kommen
    -   as_ColName

##### Rückgabewert

-   (None)

##### Beschreibung

-   Definiert, wenn sich eine bestimmte DW-Column ändert., für welches
    DW uf_Refresh aufgerufen werden soll
-   VORSICHT: passiert nur wenn per cst_DwApplObj.uf_SetItem der Wert
    gesetzt wird. Nicht bei uf_setItem's des dw_ApplEnv

#### uf_DefineRichtextCol

##### Argumente

-   as_richtextcol
-   für diese Column geschieht das nachfolgend beschriebene
    -   as_plaintextcol
-   immer wenn das via as_richtextcol definierte Feld geändert wird,
    wird der Text als Plaintext (=unformatierter Text) in das Feld
    as_plaintextcol gestellt - allerdings wird die Länge auf die Länge
    lt. pfu_column angeschnitten
    -   optionaler Block:
    -   ab_blob
-   wenn tue, steht der Inhalt des Feldes in einer Blob- Column und die
    pfu_fun kümmert sich darum, dass dieser aus der DB gelesen und in
    diese geschrieben wird.
-   Default = false
    -   ab_EnableRichText
-   true (
-   es kann mittels Strg+W das Richtext-Eingabe-Fenster aufgerufen
    werden, um den Inhalt des Richtext-Feldes zu editieren
-   false (
-   das Richtext-Eingabe-Fenster kann nicht aufgerufen werden
-   uf_ChangeItem geht folgendermaßen vor . aa_wert wird in Plaintext
    umgewandelt . dieser Plaintext wird mittels uf_GetRichText in
    Richtext umgewandelt und als aa_wert herangezogen
-   default = true
    -   as_FettJnColName
-   muss der Name einer gültigen Column oder leer sein - default ist
    leer
-   wenn as_FettJnColName \<\> "" und ab_EnableRichText = false:
-   Wenn der Wert dieser Column für eine Row auf "j" wechselt, wird für
    den Inhalt der Column lt. as_richtextcol die Formatierung auf fett
    eingestellt - bei "n" erfolgt dies gegengleich
-   siehe uf_GetRichText
-   wenn as_FettJnColName \<\> "" und ab_EnableRichText = true, wird das
    Feld lt. FettJnColName protected
    -   as_UnterstreichenJnColName
-   sinngemäß wie as_FettJnColName für Unterstreichen

##### Rückgabewert

-   (None)

##### Beschreibung

-   darf ausschließlich im definition- Eventscript aufgerufen werden
-   siehe auch unter Argumente
-   wenn die Funktion für ein Richtext-Feld aufgerufen worden ist,
-   gilt für Pfeil auf/ab:
-   mittels zusätzlich gedrückter Control- Taste kann die DW-Row
    gewechselt werden
-   Anmerkung: bei einem Richtext- Feld bewirken Pfeil auf/ab den
    Zeilenwechsel innerhalb des Richtext- Feldes
-   werden "weiche" Defaultwerte mittels uf_ChangeItemRichByPlaneText
    gesetzt ???
-   wird beim Pasten im Feld immer Planetext gepastet
-   Anmerkung Implementierung:
-   aus Paste-Buffer den PlainText auslesen und dann den PasteBuffer nur
    mit Plaintext neu setzen
-   wird das Format lt. Event RichTextSettings initialisiert
-   muss beim Setzen des Feldes mittels uf_ChangeItem (dies betrifft
    auch "harte" Defaultwerte) bzw. über die \`object.´- Notation ein
    Richtext herangezogen werden - dazu steht uf_GetRichText zur
    Verfügung
-   werden beim Übernehmen vom Richtext-Eingabe-Fenster ggf. Font und
    Fontsize für den gesamten Text gesetzt - siehe Event
    RichTextSettings
-   Anmerkung: wird der Richtext direkt im DW geändert, wird der
    geänderte Text zunächst in das Richtext- Window übertragen, dort
    ggf. nachbehandelt und wieder übernommen - allerdings ist dies für
    den Anwender nicht sichtbar ???
-   beim Editieren im Feld kann keine neue Zeile erzeugt werden (Enter
    wird ignoriert)
-   wenn die Funktion für mindestens eine Column im DW aufgerufen wird,
    wird die PB- Richtext- Toolbar unterdrückt
-   Anmerkung zu Export aus z.B. auf_pos_txt - hier sind 2 Ansätze
    angedacht:
    -   Die Export- Felder werden der Reihe nach aus den Textböcken
        entnommen
-   ( aus einem Textblock können auch die Texte für mehrere Export-
    Felder gewonnen werden
-   Bsp.:
-   folgende Textblöcke:
    -   Akku-Bohrschrauber Makita DDF446RFJ
    -   14,4Volt - mit 2 Akkus
-   3 Export- Felder mit den Längen 30, 20, 20
-   folgende Belegung der Felder:
    -   Akku-Bohrschrauber Makita
    -   DDF446RFJ 14,4Volt
    -   -   mit 2 Akkus
-   dazu ist eine DB- Funktion vorgesehen - Siehe Aufgabe-19619
-   dies ist unser Standard- Ansatz
    -   ein Exportfeld wird jeweils aus genau einem Textblock (( aus
        genau einer Row) befüllt
-   Individuell ausprogrammierte Einschrängungen für die für den Export
    herangezogenen Textblöcke über das Event RichTextSettings
-   dazu müssen allerdings noch Einschränkungsmöglichkeiten geschaffen
    werden

#### uf_DefineSort

##### Argumente

-   as_sort
-   Format: `<Feldname>`{=html} " " {"A", "D"} \[ ","
    `<Feldname>`{=html} " " {"A", "D"} \] ...
-   "A" ( ascending = aufsteigend, "D" ( descending = absteigend
-   spezielle Werte: \> Blank ( keine Sortierung \> Null ( aktuelle
    Sortierung, das ist im definition- Event- Script die Sortierung lt.
    DWO
-   kann weggelassen werden, dann wird null angenommen
    -   ab_SortAenderbar
-   true ( Sortierung kann vom Benutzer geändert werden
-   false ( nicht änderbar
    -   ab_RetrieveEndApplNachSort
-   bestimmt, ob nach uf_Sort das RetrieveEndAppl- Event aufgerufen wird
-   kann weggelasen werden - es wird dann der Wert lt.
    RetrieveEndApplNachSort angenommen und der ist standardmäßig false

##### Rückgabewert

-   (None)

##### Beschreibung

-   darf sowohl im definition- Event- Script als auch später verwendet
    werden
-   Legt die Sortierung in einem DW fest
-   Beim Retrieve und nach dem Speichern eines DWs wird vom System nach
    der definierten Sortierung im DW sortiert
-   Es darf in einem Script jederzeit ein uf_Sort- Aufruf stehen, um die
    Sortierung zu aktuallisieren bzw. umzusortieren
-   Hat nichts mit dem ORDER BY im Select zu tun!
-   Wird Sortierung vom Benutzer geändert, übersteuert dies die
    Sortierung lt. as_sort
-   Standardmäßig ist Sort im idw_list änderbar und sonst nicht
-   ACHTUNG: wird ignoriert, wenn im definition- Eventscript
    uf_SetLineNrCol mit ab_ResortByDragAndDrop=true aufgerufen wird

Siehe auch - uf_Sort

#### uf_DeleteAllLines

##### Argumente

##### Rückgabewert

-   boolean

##### Beschreibung

-   Löscht alle Zeilen aus dem DW
-   Wenn der Verbund des DWs nicht retrieved ist, wird er vorher
    retrieved

#### uf_DeleteEmptyLines

##### Argumente

-   as_column

##### Rückgabewert

-   boolean

##### Beschreibung

-   Löscht alle Zeile aus dem DW in dem die as_column null ist

#### uf_DeleteLine

##### Argumente

-   al_row

##### Rückgabewert

-   boolean

##### Beschreibung

-   Löscht Zeile aus DW

#### uf_Dial

##### Argumente

-   as_telefonnr
-   as_error
-   by referenze

##### Rückgabewert

-   boolean

##### Beschreibung

-   Verbindet sich mit der Telefonanlage und wählt die übergebene Nummer
-   kann im IaeoShow - Event aufgerufen werden

#### uf_DispResetItemChangedError

##### Argumente

-   as_error

##### Beschreibung

-   Gibt den mittels uf_SetErrorTxt2nl gesetzten Text aus und löscht
    diesen, wenn er nicht leer ist
-   wenn as_error nicht leer ist, wird auf jeden fall as_error
    ausgegeben
-   wenn beide nicht leer sind, werden beide ausgegeben
-   Anwendungsbeispiel:
-   eine Aktion wird sowohl vom ItemChangedAppl- Eventscript als auch
    von einem Script, das im Ramen des Speicherns (wf_Save) aufgerufen
    wird, aufgerufen
-   wegen ersterem werden fehlermeldungen nicht ausgegeben sonsdern
    mittels uf_SetErrorTxt2nl gesetzt
-   die Aktion wird mit der Version mit echter übergebener Zeilennummer
    von uf_aktion aufgerufen - dabei wird der Fehlertext nicht
    angezeigt, wenn das Aktion- Eventscript false liefert
-   desshalb muss der Fehler durch einen expliziten Aufruf von
    uf_DispResetItemChangedError angezeigt werden
-   CodeBsp.: if not uf_aktion ( ll_row, "haha" ) then
    uf_DispResetItemChangedError ( "beim Speichern" ) end if

## uf_error (geerbt von dw_ApplEnv)

##### Argumente

-   as_wo
-   Position im Script
    -   as_ErrorText
-   Fehlermeldung

##### Beschreibung

-   gibt eine Fehlermeldung aus
-   diese wird nicht übersetzt
-   Die Meldung enthält den Datawindownamen

Siehe auch - w_ApplObj.uf_error

## uf_ExistDwCol (geerbt von dw_ApplEnv)

##### Argumente

-   as_Column

##### Rückgabewert

-   boolean
-   true ( as_column ist ein gültiger DW- Column- Name einer nicht
    Computed- Column false ( sonst

##### Beschreibung

-   siehe Rückgabewert

#### uf_filter

##### Argumente

-   as_filter
-   z.B. "ab_dat =" + gf_AnyToFindLiteral ( ldt_irgendein_datum ) + "
    and vkkond_snr = " &
-   gf_AnyToFindLiteral ( li_fa_nr )
-   alle Literals sind mit gf_AnyToFindLiteral zu behandeln!
    -   ab_IfDiffOnly
-   tue ( Filterung wird nur durchgeführt, wenn sich der Filter geändert
    hat
-   false ( Filterung wird immer durchgeführt
-   kann weggelassen werden, dann wird false angenommen
-   false ist dann zu übergeben, wenn neu gefiltert werden muss, obwohl
    sich der Filterstring nicht geändert hat
    -   ab_sort
-   true ( Das DW auf den der Filter angewendet wird, wird neu sortiert
-   ist optional ( es wird true angenommen

##### Rückgabewert

-   boolean

##### Beschreibung

-   Setzt einen Filter auf das Datawindow und bringt diesen zur
    Anwendung
-   im Fehlerfall kommt eine Fehlermeldung und es wird false geliefert
-   immer bevor das System alle Rows des DWs bearbeitet, wird der Filter
    entfernt - die Applikation hat dafür zu sorgen, dass er bei Bedarf
    wieder gesetzt wird.
-   In folgenden Situationen wird der Filter nicht entfernt:
    -   uf_aktion für alle Rows (al_row=0)
-   hier hat die Applikation dafür zu sorgen, dass der Filter richtig
    gesetzt nzw. nicht gesetzt ist
    -   uf_LogNewlineEnd
-   ist nicht notwendig, weil der Filter hier keine Role spielt
-   wenn das ApplObject kopiert wird, wird der Filter nicht entfernt -
    allerdings werden die ausgefilterten Rows mitkopiert
-   wenn in einem Script notwendig ist, dass das DW gefiltert ist oder
    nicht gefiltet ist, hat die Applikation dies zu gewährleisten
-   der Filter kann mittels uf_unfilter entfernt werden
-   ein Monitor darf nicht gefiltert werden!!!
-   Typische Anwendung:
-   es gibt 2 Grid- DWs
-   es bestet eine 1 zu n- Beziehung zwischen der Tabelle des ersten DWs
    und der Tabelle des 2. DWs
-   beim 2. DW werden alle Rows retrieved, für die es in der Tabelle des

1.  DWs eine Row gibt

-   in der zweiten Tabelle sollen allerdings nur jene Rows angezeigt
    werden, die zur aktuellen Row in der ersten Tabelle gehören
-   dies wird über einen Filter in der 2. Tabelle gelöst
-   das Setzen des Filters erfolgt durch die Applikation:
    -   im BeforeOnSetpresentation Event- Script
-   abhängig von der aktuellen Row im 1. DW
-   um den Filter für den Benutzer zu setzen
-   hier wird im Allgemeinen ab_IfDiffOnly=true sein
    -   in Datenverarbeitungsscripts
-   immer unabhängig von der aktuellen Row lt. uf_GetRow im 1. DW
-   sodass sich im 2. DW nur jene Rows befinden, die der gerade im

1.  DW verarbeiteten Row entsprechen (Achtung: die gerade verarbeitete
    Row im 1. DW ist nicht unbedingt die aktuelle Row!)

-   prinzipiell muss also vor jedem Verarbeitungsblock (= Teil eine
    Scripts mit allen direkt oder indirekt aufgerufenen Scripts) mit
    einheitlichem Filterstring uf_filter aufgerufen werden
-   wird ein solcher Verarbeitungsblock immer nur dann aufgerufen, wenn
    der Filter richtig gesetzt ist (dies ist zu dokumentieren) braucht
    der Filter im Block nicht gesetzt zu werden.
-   Dazu eine Typische Situation:
-   Ein uf_ChangeItem im 1. DW löst eine Aktivität im ItemChangedAppl
    für alle Rows im 2. DW, die der Row lt. al_row des uf_ChangeItem
    entsprechen, aus
-   es gibt jetzt folgende zwei Möglichkeiten, von wo der uf_ChangeItem
    aufgerufen worden ist: \> direkt durch eine Benutzereingabe
-   dann ist al_row sicher die aktuelle Row und dann ist der Filter
    sicher im BeforeOnSetpresentation Event- Script gesetzt worden \>
    aus einem anderen Script
-   denn gibt es wieder zwei Möglichkeiten: \> es befindet sich davor im
    Script der entsprechende uf_filter- Aufruf \> das Script ist ein
    solcher Verarbeitungsblock, der jetzt gerade beschrieben wird
    (rekursive Definition)

#### uf_Find

##### Argumente

-   as_Find

##### Rückgabewert

-   gefundene Row
-   integer

##### Beschreibung

-   liefert die erste Row des DWs welche dem Find-String entspricht
-   sucht über alle Zeilen
-   soll in einem bestimmten Bereich gesucht werden ist weiterhin find
    zu verwenden.

#### uf_GetColumn

##### Argumente

-   as_column
-   as_dattyp
-   optional

##### Rückgabewert

-   Columnname
-   by referenz
-   Datentyp der Column
-   by referenz

##### Beschreibung

-   liefert die Column des DWs welche den Focus hat
-   liefert den Datentyp der Column

#### uf_GetCopiedItem

##### Argumente

-   al_row
-   kopierte Zeile
    -   as_column

##### Rückgabewert

-   any
-   Feldinhalt

##### Beschreibung

-   liefert den Feldinhalt zu einer DW- Column im Copy- Buffer
-   siehe dw_ApplObj.event SollPaste

#### uf_GetDeletedItem

##### Argumente

-   al_row
-   für den übergebenen Wert gibt es folgende Möglichkeiten: \>
    ll_AnzRow = DeletedCount() for ll_row = 1 to ll_AnzRow
    uf_GetDeletedItem ( ll_row, ... ) \> der Parameter al_row des Events
    ForDeletedRowOnUpdate
    -   as_column

##### Rückgabewert

-   any
-   Feldinhalt

##### Beschreibung

-   Darf nur verwendet werden, wenn das DW retrieved ist
-   liefert den Feldinhalt zum Zeitpunkt des Löschens der Column lt.
    as_column der im DW gelöschten Zeile lt. al_row
-   siehe unbedingt ACHTUNG bei DeletedCount

#### uf_GetDeletedRow

##### Argumente

-   al_KeyRow
-   sieh Beschreibung
    -   as_KeyColumns
-   Columnnamen durch Blank getrennt
-   sieh Beschreibung

##### Rückgabewert

-   long
-   al_row für einen Aufruf von uf_GetDeletedItem
-   ist 0, wenn keine entsprechende gelöschte Zeile existiert

##### Beschreibung

-   sucht die erste gelöschte Zeile mit dem gleichen Key wie die Zeile
    lt. al_KeyRow, die Keyfelder sind lt. as_KeyColumns definiert
-   der Rückgabewert wird für uf_GetDeletedItem benötigt
-   siehe unbedingt ACHTUNG bei DeletedCount

#### uf_GetEditColumn

##### Argumente

-   al_row
-   kann weggelassen werden

##### Rückgabewert

-   string
-   Name der Column, die gerade vom Anwender editiert worden ist, aber
    noch nicht übernommen ist
-   wenn es keine solche gibt, dann leer
-   wenn al_row angegeben ist, muss die Eingabe genau in dieser Row
    erfolgt sein

##### Beschreibung

-   wird typischerweise im Aktion- Eventscript verwendet

#### uf_GetItem

##### Argumente

-   al_row
-   kann entfallen
-   wenn 0 oder nicht vorhanden, wird die aktuelle Row herangezogen
    -   as_column
    -   ab_RetrievedValue
-   kann weggelassen werden, dann wird false angenommen
-   true (
-   es wird der Wert zum Zeitpunkt direkt nach dem RetrieveEndAppl
    geliefert
-   ACHTUNG: darf im neu- Zeig nicht so aufgerufen werden - sonst
    erfolgt Programmabbruch
-   siehe uf_GetRetrievedItem
-   false
-   es wird der aktuelle Wert geliefert

##### Rückgabewert

-   any
-   Feldinhalt - siehe ab_RetrievedValue

##### Beschreibung

-   liefert den Feldinhalt zu einer DW- Column

#### uf_GetItemIntoNewline

##### Argumente

-   adw_target
-   DW, in welches der Inhalt des DS eingefügt werden soll
    -   as_row
-   row, von der beginnend in adw_target eingefügt werden soll
-   siehe dazu dw_ApplObj.uf_newline
    -   as_aktion
-   Für die neu eingefügte Zeile in adw_target wird uf_aktion mit
    as_aktion aufgerufen
-   kann weggelassen werden, dann wird keine Aktion ausgeführt
-   hier kann uf_ResetItemStatus aufgerufen werden
    -   as_error (reference)
-   Fehlertext, wird im Fehlerfall belegt

##### Rückgabewert

-   boolean
-   true ( erfolgreich false ( ein Fehler ist aufgetreten (return
    erfolgt sofort beim ersten Fehler)

##### Beschreibung

-   Fügt für jede Row im DS mittels uf_NewLine eine Row in das DW
    adw_target ein und setzt dort für alle Columns, für die es eine
    gleichnamige Column im DS gibt, den Wert mittels uf_ChangeItem auf
    den entsprechenden Wert aus dem DS.
-   Tritt ein Fehler auf wird as_error belegt und false returned
-   ACHTUNG: pro Row werden die Felder in der Reihenfolge lt. Column-
    Specification des DWOs des DS abgearbeitet. Es ist also beim DWO des
    DS darauf zu achten, daß sich kein Feld, das im Ziel- DW vor einem
    anderen Feld belegt werden muß, in der genannten Reihenfolge im DWO
    des DS nach diesem anderen Feld befindet!

#### uf_GetItemStatus

##### Argumente

-   al_row
-   as_column
-   kann entfallen

##### Rückgabewert

-   DwItemStatus: \> NotModified!
-   Row/Column wurde nach dem Retieve bzw. nach dem Speichern nicht
    geändert \> DataModified!
-   Row ist nicht neu
-   Row/Column ist verändert worden \> New!
-   Row ist neu, wurde aber noch nicht verändert \> NewModified!
-   Row ist neu, und wurde schon verändert

##### Beschreibung

-   liefert den Status eines Feldes
-   wenn as_column weggelassen wird, den Status der ganzen Row
-   Die Aussagen bei den Rückgabewerten gelten seit dem letzten Retrieve
    bzw. Speichern
-   Das Speichern ist im AfterUpdate bereits vollzogen

#### uf_GetChangeItemLevel

##### Argumente

##### Rückgabewert

-   integer

##### Beschreibung

-   ist zu Aufruf im ItemChangedAppl- Eventscript gedacht
-   liefert die Schachtelungstiefe des aktuellen uf_ChangeItem- Aufrufs
-   ist beim ItemChangedAppl = 1, wenn uf_ChangeItem \> direkt durch
    eine Benutzereingabe ausgelöst worden ist -\> Wenn der
    ab_ItemChangedField- Parameter true ist, und uf_GetChangeItemLevel 1
    liefert, handelt es sich um eine Benutzereingabe im aktuellen Feld
    \> direkt aus einem Script aufgrufen worden ist, das nicht direk
    oder indirekt von einem anderen uf_ChangeItem initiert worden ist
-   beim Zurücksetzen auf den alten Wert bei einem misslungenen
    uf_Changeitem durch das System ist im entsprechenden ItemChangedAppl
    der Level mindestens 2

#### uf_GetITabPage

##### Argumente

##### Rückgabewert

-   integer
-   Nummer der tabpage, auf der sich das DW befindet
-   liefert 1, wenn es kein Tab- Control gibt

#### uf_GetNextSelectedRow

##### Argumente

-   al_row
-   by Reference
-   die übergebene Variable soll vor dem Aufruf die Row vor jener Row,
    ab der nach der ersten markierten Row gesucht werden soll, enthalten
-   Bsp: wenn mit der 1. Zeile begonnen werden soll, wird 0 übergeben
-   wenn es nach der übergebenen Row eine markierte Row gibt, wird
    al_row mit deren Nummer belegt
-   sonst wird al_row nicht verändert
    -   ab_IncludeCurrentRow
-   true ( die aktuelle Row wird als markierte Row betrachtet
-   false ( die aktuelle Row wird nicht als markierte Row betrachtet

##### Rückgabewert

-   Boolean
-   True ( wenn die oben beschriebene markierte Row gefunden worden ist
-   False ( wenn es nach der übergebenen Row lt. al_Row keine wietere
    markierte Row mehr gibt

##### Beschreibung

-   Dient zum Abarbeiten aller markierten Rows mittels einer Schleife -
    dazu ein Bsp.:

\[pic\]

#### uf_GetRetrievedItem

##### Argumente

-   al_row
-   kann entfallen
-   wenn 0 oder nicht vorhanden, wird die aktuelle Row herangezogen
    -   as_column
    -   aa_RetrivedValueNew

##### Rückgabewert

-   wenn wir im Neu- Zeig sind ( aa_RetrivedValueNew
-   sonst ( Ruft uf_GetItem ( al_row, as_column, true ) auf

#### uf_GetRichText

##### Argumente

## o al_row

-   Zeile des DWs \## o as_column

-   Feldname \## o as_PlainText

-   siehe Rückgabewert

##### Rückgabewert

-   string
-   as_PlainText wird abhängig von den den Referene-Argumenten von
    RichTextSettings übergebenen Werten und ggf. den Werten der Felder
    lt. as_FettJnColName, as_UnterstreichenJnColName in RichText
    umgewandelt - dieser Richtext ist der Rückgabewert

##### Beschreibung

-   siehe Rückgabewert

#### uf_GetRow

##### Argumente

##### Rückgabewert

-   long
-   Nummer der aktuellen Row
-   liefert 0, wenn keine Row vorhanden ist

## uf_IsNull (geerbt von dw_ApplEnv)

##### Argumente

-   al_row
-   Row, in der die Column geprüft werden soll
    -   as_column
-   Name der Column

##### Rückgabewert

-   boolean
-   true ( Wert des Feldes ist Null
-   false ( sonst

##### Beschreibung

-   sollte, wenn nur die Abfrage auf Null zu erfolgen hat statt
    uf_GetItem verwendet werden (Performance!) - dies gilt besonders im
    Null- Prüf- Teil einer Aktion
-   allerdings muss folgendes sichergestellt sein, da es nicht geprüft
    wird:
-   DW muss retrieved sein
-   Row muss vorhanden sein
-   Column muss vorhanden sein

#### uf_JumpToField

##### Argumente

-   al_row
-   gib die Row, bei welcher der Fredl stehen soll, an
-   0 = aktuelle Row zum Zeitpunkt des Aufrufs
-   numerisch null = aktuelle Row zum Zeitpunkt des eigentlichen
    Feldwechsels
-   dazu steht die vorinitialisierte Variable il_null (gibt es sowohl in
    w_ApplObj als auch in dw_ApplObj) zu Verfügung
    -   as_column
-   Name der Column, bei welcher der "Fredl" stehen soll
-   folgende Sonderfälle:
    -   "" ( aktuelle Column zum Zeitpunkt des Aufrufs
    -   "\>" ( die erste Column für die zum Zeitpunkt des eigentlichen
        Feldwechsels gilt:
-   TabOrder ist größer als die Taborder der aktuellen Column zum
    Zeitpunkt des Aufrufs
-   ist "betretbar"
    -   "\<" ( sinngemäß wie "\>"
    -   string null ( aktuelle Column zum Zeitpunkt des eigentlichen
        Feldwechsels
-   dazu steht die vorinitialisierte Variable is_null (gibt es sowohl in
    w_ApplObj als auch in dw_ApplObj) zu Verfügung
-   gib die Column, , an
    -   ab_focus
-   soll das DW den Focus erhalten
-   kann weggelassen werden, dann wird true angenommen
    -   ac_pos
-   steuert, wo im sichtbaren Ausschnitt des DWs die Row, zu der
    gesprungen werden soll, sich befinden soll: \> 'f' ... first \> 'l'
    ... last \> ' ' ... keine Vorgabe
-   kann weggelassen werden, dann wird ' ' angenommen

##### Rückgabewert

-   (None)

##### Beschreibung

-   bestimmt eine neue aktuelle Eingabeposition im DW und gibt dem DW
    den Focus
-   die Funktion setzt Instanz- Variablen und postet den eigentlichen
    Feldwechsel und Focuswechsel
-   dies funktioniert allerdings nur dann, wenn zum Zeitpunkt des
    eigentlichen Feldwechsels :
-   die aktuelle Eingabeposition verlassen werden kann.
-   das neue Feld (falls ein solches angegeben worden ist) nicht
    protected ist - ist das neue Feld protcted, wird das Feld mit der
    nächsten Taborder zum aktuellen Feld
-   für das DW uf_DefineMde aufgerufen worden ist, wenn sich die
    Applikation im MDE- Modus befindet
-   um zu einer Row zu scrollen und den Focus auf das DW zu setzen ruft
    man uf_JumpToField ( row, is_null ) auf
-   um zu einer Row zu scrollen und den Focus nicht auf das DW zu setzen
    ruft man uf_ScrollToRow auf
-   beim Fernsteuern von idw_list ist allerdins ScrollToRow zu
    verwenden, weil ja in diesem Fall nicht gepostet werden darf!
-   ACHTUNG:
-   Bei der Datenverarbeitung aller DWs außer idw_list darf die aktuelle
    Row keine Rolle spielen!!!
-   Die aktuelle Row hat nur eine Bedeutung nur für den Anwender -
    niemals aber eine Bedeutung für ein Script!!!
-   die aktuelle Column hat sowieso nie eine Bedeutung für ein Script!!!

#### uf_LogNewlineBegin

##### Argumente

##### Rückgabewert

-   (None)

##### Beschreibung

-   startet das Loggen aller mittels uf_NewLine eingefügten neuen Rows
-   dazu muss im DWO eine numerische Column "NewlineLogNr" vorhanden
    sein, diese ist über pfu_selkonst.k_integer zu realisieren
-   bevor der Anwender die Kontrolle zurückerhält, muss uf_LogNewlineEnd
    bzw. uf_LogNewlineRedo aufgerufen werden!

#### uf_LogNewlineEnd

##### Argumente

##### Rückgabewert

-   (None)

##### Beschreibung

-   beendet das Loggen aller mittels uf_NewLine eingefügten neuen Rows
    und löscht die Loginformationen
-   darf nur aufgerufen werden, wenn zuvor uf_LogNewlineBegin aufgerufen
    worden ist

#### uf_LogNewlineRedo

##### Argumente

##### Rückgabewert

-   (None)

##### Beschreibung

-   löscht alle mittels uf_NewLine seit dem Aufruf von
    uf_LogNewlineBegin eingefügten neuen Rows in der entgegengesetzten
    Reihenfolge des Einfügens
-   beendet das Loggen und löscht die Loginformationen
-   darf nur aufgerufen werden, wenn zuvor uf_LogNewlineBegin aufgerufen
    worden ist

#### uf_LookupAfterLock

-   vormals uf_lookup

##### Argumente

-   al_row
-   wenn 0, dann alle Rows
-   Bei 0 wird abgebrochen, wenn ein Lookup bei einer Row versagt hat
    -   as_praefix
-   z.B. "stat\_", wenn der Statistikkunde gelookuped werden soll
    -   as_IdName
-   z.B. "kunde", wenn der Statistikkunde gelookuped werden soll

##### Rückgabewert

-   boolean
-   Loookup war erfolgreich

##### Beschreibung

-   Führt Lookup für das AEO lt. Argumenten durch.
-   Der Aufruf dient dazu, Zustandsdaten (z.B. Zustandskennzeicehn,
    Lagerstand), die sich geändert haben können, nach dem Sperren neu
    einzulesen
-   folgende Besonderheiten:
-   es werden keine Table- Felder befüllt
-   es werden keine Felder, die Key- Column eines AEOs sind befüllt
-   die Felder werden nicht mit uf_ChangeItem gesetzt (
-   kein ItemChangedAppl- Aufruf
-   der Lookup kann auslösen, dass die Kosistenz nicht mehr gegeben ist
-   diese ist nach dem Aufruf von uf_lookup durch entsprechende Aufrufe
    von uf_ChangeItem bzw. uf_aktion ggf. wiederherzustellen - dazu ein
    Bsp.:
-   durch den lookup wurden folgende Felder geändert:
    -   artik_lag.sum_auf_off_mg
    -   artik_lag.sum_lag_mg
-   dadurch ist das daraus errechnete Feld frei_mg nicht mehr korrekt
    und muss neu berechnet werden
-   Ist der Key- Wert des AEOs NULL, wird nichts gemacht (auch kein
    "Ausnullen" wie beim uf_Lookup des ItemChangedAppl)
-   der NoLookupValue lt. iuo_ae.uf_AddAotEo und das Event
    LookupAeoFailed werden berücksichtigt.

#### uf_MapButtonAppl

##### Argumente

-   as_DwButtonName
-   as_ButtonApplName
-   kann auch leer sein, dann wird der DWO- Button funktionslos und hat
    keinen Text

##### Rückgabewert

-   (None)

##### Beschreibung

-   siehe wf_AddDwButtonAppl
-   ordnet den as_DwButtonName entsprechenden Button im DWO dem
    as_ButtonApplName entsprechenden logischen Applikationsbutton des
    Windows zu
-   einem logischen Applikationsbutton können gleichzeitig mehrere DWO-
    Buttons zugeordnet sein
-   durch die Zuordnung wird der Text des Buttons am DWO lt. dem
    logischen Applikationsbutton gesetzt

#### uf_MussZuruecksetzen

##### Argumente

##### Rückgabewert

-   boolean
-   liefert true, wenn folgendes zutrifft:
-   keine Fernsteuerung
-   im Callstack ist ein uf_ChangeItem, der ein Feld von nicht- NULL auf
    NULL ändert

##### Beschreibung

-   siehe Implementierung einer Aktion

#### uf_NewEmail

##### Argumente

-   as_name
-   Name hinter der Email- Adresse
    -   as_email
-   Email- Adresse
-   Folgende 2 Parameter können weggelassen werden, es sind dann
    allerdings beide Parameter wegzulassen
    -   as_cc
-   keine, eine oder mehrere durch Strichpunkt getrennte Email-
    Adresse(n)
    -   as_bcc
-   keine, eine oder mehrere durch Strichpunkt getrennte Email-
    Adresse(n)
    -   as_betreff
    -   as_text
-   Email- Body
-   Unformatierter Unicode- Text (UTF-16 LE)
    -   as_attachments\[\]
-   Array mit Filenamen
-   UNC- Format
    -   as_error
-   by Reference

## alternative Argumente

-   as_email
-   as_error

##### Rückgabewert

-   boolean
-   as_error by referenz

##### Beschreibung

-   ruft Email- Client auf und legt neue Mail mit der übergebenen
    EMailAdresse an
-   kann im IaeoShow - Event aufgerufen werden

#### uf_NewLine

##### Argumente

-   as_wo
-   wo soll die neue Zeile eingefügt werden
-   '\>' ( nach der aktuellen Zeile
-   '\>\|' ( zum Schluß
-   '\<' ( vor der aktuellen Zeile
-   '\|\<' ( zu Beginn
-   sonst ( long(as_wo) ist die neue Zeile
    -   ac_mode
-   kann weggelassen werden, dann wird " " angenommen
-   " " ( keine Besonderheiten
-   "s" ( die eingefügte Zeile wird die aktuelle Zeile - dies wird
    allerdings erst durch SetPresentation gemacht
    -   ac_AufrufVon
-   siehe Event DarfNewline Argument ac_AufrufVon
-   kann weggelassen werden, dann wird 's' übergeben

##### Rückgabewert

-   long
-   eingefügte Row

##### Beschreibung

-   fügt neue Row in ein DW ein

#### uf_NoGridschema

##### Argumente

##### Rückgabewert

-   (None)

##### Beschreibung

-   Bewirkt, daß der Gridschama- Mechanismus nicht angewandt wird. (Kein
    Speichern bzw. Setzen lt. Datenbank von Spaltenbreiten u.s.w.)
-   sollte im definition- Event aufgerufen werden

#### uf_OpenURL

##### Argumente

-   as_url
-   ref as_error

##### Rückgabewert

-   boolean
-   as_error by referenz

##### Beschreibung

-   ruft WebBrowser auf und übergibt die URL
-   kann im IaeoShow - Event aufgerufen werden

#### uf_OpenUNC

##### Argumente

-   as_unc
-   ref as_error

##### Rückgabewert

-   boolean
-   as_error by referenz

##### Beschreibung

-   wenn Extension (Dateityp) vorhanden ist, wird die Datei mit dem lt.
    Windows zugeordneten Programm geöffnet, sonst wird angenommen, dass
    es sich um ein Verzeichnis handelt, und es wird der Windows-
    Explorer geöffnet
-   kann im IaeoShow - Event aufgerufen werden

#### uf_PasteMaster

##### Argumente

-   as_column

##### Rückgabewert

-   boolean
-   true, wenn alles gut geht

##### Beschreibung

-   siehe dw_ApplObj.event SollPaste
-   führt das Pasten für den Master- Detail- Verbund, dessen Master this
    ist, aus

## Wann verwenden

-   ist zu verwenden, wenn das Pasten des AOs ferngesteuert wird

#### uf_PressDwButton

##### Argumente

-   al_row
-   as_DwButtonName
-   Control-Name im DWO

##### Rückgabewert

-   none

##### Beschreibung

-   simuliert das Betätigen eines Buttons des DWs
-   dieser muss allerdings mittels uf_MapButtonAppl zugeordnet worden
    sein!!!

#### uf_Protect

##### Argumente

-   al_row
-   as_column

##### Rückgabewert

-   boolean
-   false, wenn das Feld lt. al_row, as_column betreten werden kann
-   sonst true

#### uf_Refresh

##### Argumente

##### Rückgabewert

-   boolean
-   Retrieve war erfolgreich ( true sont ( false

##### Beschreibung

-   Retrieved ein DW eines Master- Detail- Verbunds neu. (das DW kann
    auch der Master sein.)
-   Zustand des Windows ändert sich nicht
-   im Zustand 'e' nicht möglich
-   im Zustand 'n' auf idw_neu nicht möglich
-   wird uf_refresh für ein DW im Status 'n' oder 'u' aufgerufen, gehen
    die Änderungen in diesem DW verloren
-   im Zustand 'n' nicht für ein DW, dessen Master nicht idw_neu ist,
    verwenden, wenn es Lookups gibt
-   Erklärung: dabei wird die Prüfung ll_row \<= uf_RowCount verletzt,
    weil uf_RowCount fix 0 liefert
-   ACHTUNG: im Status 'n' nicht für ein DW, dessen Master idw_neu ist
    und für das es eine bestimmte Anzahl von Zeilen geben muß, welche im
    default- Event von idw_neu bzw. w_ApplObj::NewAfterInsertRow- Event
    aufgebaut werden!!!
-   es erfolgt auch Lookup

#### uf_Reset

##### Argumente

-   ab_DoOnDeleteBeforeOnUpdate
-   boolean
-   kann weggelassen werden - default ist false
-   wenn true, wird vor dem Aufruf von OnUpdate OnDelte aufgerufen
-   wurde für folgenden Ablau eingeführt: . uf_Reset ( true )
-   true ist nötig, dass die Rows, die bisher im DW waren aus der DB
    gelöscht werden . uf_Refresh ()
-   Der Select ist ein Union mit folgenden Zweigen
    -   ganz normaler Select auf die Update- Table
    -   Select zum Befüllen des DWs
-   geht viel schneller als dies via GetItemIntoNewline zu lösen
-   geht natürlich nur, wenn kein ItemChangedAppl benötigt wird .
    uf_SetItemStatusNew()
-   dadurch werden die Zeilen beim Speichern ingesertet

##### Rückgabewert

-   (None)

##### Beschreibung

-   löscht das Datawindow
-   darf nur im Status Neu für ein DW aus dem Master- Detailverbund des
    Neu- DW's erfolgen außer es wird für ab_DoOnDeleteBeforeOnUpdate
    true übergeben
-   darf nicht für das Neu- DW selbst erfolgen
-   allerdings für DWs, für die DarfChangeInDisplay true liefert, darf
    uf_reset auch sonst erfolgen

#### uf_ResetItemStatus

##### Argumente

-   al_row
-   kann weggelassen werden, dann:
-   werden alle Rows behandelt
-   wird der DELETE- Buffer unschädlich gemacht

##### Rückgabewert

-   (None)

##### Beschreibung

-   Setzt den Status der Row lt. al_row auf "retrieved und nicht
    verändert"

#### uf_ResetToNull

##### Argumente

-   al_row
-   as_column

##### Rückgabewert

-   (None)

##### Beschreibung

-   Setzt das Feld auf null, wenn es nicht null ist.

## Wann verwenden

-   Wenn ein Feld, welches Key eines AEOs, das Keybestandteil eines
    anderen AEOs des selben AOTs ist, verändert wird, ist es oft
    sinnvoll den Key dieses andern AOEs auf NULL zurückzusetzen. Dies
    hat dann mittels uf_ResetToNull() zu erfolgen. (Bsp.: Wird die
    Firmennummer im Auftrags- Window verändert, wird der Kundencode
    zuückgesetzt.)
-   Dies ist deshalb mittels uf_ResetToNull durchzuführen, weil es sonst
    Probleme beim Pasten gibt.

#### uf_Retrieve

##### Argumente

##### Rückgabewert

-   Boolean

##### Beschreibung

-   retrieved den Master- Detail- Verbund neu (sofort)
-   darf für den Verbund, der im Zustand Update ist, nicht aufgerufen
    werden
-   darf im Zustand New überhapt nicht aufgerufen werden

#### uf_RowCount

##### Argumente

##### Rückgabewert

-   long
-   Anzahl der Rows im DW
-   ACHTUNG: liefert im Zustand 'n' für DWs, die nicht im Verbund mit
    idw_neu sind, 0

#### uf_ScrollToRow

##### Argumente

-   al_row

##### Rückgabewert

-   (None)

##### Beschreibung

-   bestimmt eine neue aktuelle Row im DW
-   die Funktion setzt Instanz- Variablen und postet den eigentlichen
    Rowwechsel
-   dies funktioniert allerdings nur dann, wenn zum Zeitpunkt des
    eigentlichen Rowwechsels :
-   die aktuelle Eingabeposition verlassen werden kann.
-   beim Fernsteuern von idw_list ist allerdins ScrollToRow zu
    verwenden, weil ja in diesem Fall nicht gepostet werden darf!
-   ACHTUNG:
-   Nicht in idw_list verwenden!!!
-   Bei der Datenverarbeitung(Event-Scripts/Fernsteuerung/...) aller DWs
    außer idw_list darf die aktuelle Row keine Rolle spielen!!!
-   Die aktuelle Row hat nur eine Bedeutung für den Anwender - niemals
    aber eine Bedeutung für ein Script!!t
-   das DW des Aufrufs erhält durch den Aufruf nicht den Focus. Um dies
    zu erreichen, ist stattdessen uf_JumpToField ( row, is_null ) zu
    verwenden

#### uf_serial

##### Argumente

-   as_tabname
-   Tabelle, für die eine Serial- Column vergeben werden soll
-   kann weggelassen werden, dann wird die Update- Table des DWs
    herangezogen
    -   as_SerialColumn
-   DB- Name der Serial- Column, deren Wert vergeben werden soll
    -   ab_instanz\*
-   optional
-   true ( es wird eine 14-stellige snr zurückgeliefert (4 Stellen lt.
    Instanz + 10 Stellen lt. Snr)

##### Rückgabewert

-   decimal
-   die neu vergebene Serial- Nummer

##### Beschreibung

-   Vergibt die nächste Serial- Nummer für eine DB- Column
-   Wenn im DW eine Column mit dem Namen lt. as_SerialColumn vorhanden
    ist, wird der Rückgabewert dort eingetragen.
-   verwendet intern tr\_.uf_serial
-   Bei der alten Version wurde ein long-Wert zurückgegeben !
-   Der Programmierer muss sich darum kümmern, dass die snr in eine
    decimal-Variable eingelesen wird wenn ab_instanz = true ist

## Wann verwenden

-   Sollte frühersten im BeforeUpdate und spätestens im
    BeforeUpdateDetail- Event- Script irgend eines DWs im Master-
    Detail- Verbund aufgerufen werden

#### uf_Set0width

##### Argumente

-   as_column
-   Name der Column, welche auf Breite 0 zusammengeschoben werden soll
    bzw. wieder ihre Orginalbreite erhalten soll
    -   ab\_
-   true ( zusammenschieben
-   false ( Orginalbreite

##### Rückgabewert

-   (None)

##### Beschreibung

-   Funktion definiert, daß Column- Breite lt. Argumenten gesetzt werden
    soll.
-   Dies wird allerdings erst beim Aufruf der Funktion uf_SetColWidth()
    wirksam.
-   Aufrufreihenfolge: . ein- oder mehreremale uf_Set0width(...) .
    uf_SetColWidth()

#### uf_SelectRow

##### Argumente

-   al_row
-   Row, deren Selektierung geändert werdn soll
-   0 ( alle Rows
    -   ab_select
-   true ( Markierung einschalten
-   false ( Markierung ausschalten

##### Rückgabewert

-   (None)

##### Beschreibung

-   Dient zum Markieren / Entmarkieren einer oder aller Rows im
    Datawindow
-   Wenn al_row die aktuelle Zeile oder 0 ist und ab_select true ist,
    wird die aktuelle Zeile nicht markiert (diese darf nie markiert
    sein!)

#### uf_SetCallConst

##### Argumente

-   as_column
-   as_praefix

##### Rückgabewert

-   (None)

##### Beschreibung

-   ruft iuo_ae.uf_SetCallConst ( this, as_column, as_praefix) auf

#### uf_SetCancelOnFailedSave

##### Argumente

##### Rückgabewert

-   (None)

##### Beschreibung

-   Der Aufruf darf in einem der folgenden Event- Scripts erfolgen:
    -   BeforeUpdate
    -   BeforeUpdateDetail
    -   AfterUpdate
-   Mit einem Aufruf wird erreicht, daß, wenn Save über das Menü
    aufgerufen worden ist und nicht erfolgreich ist, Cancel durchgeführt
    wird (nicht direkt Cancel, aber von der Auswirkung her das Selbe).
-   Der Aufruf ist nur für den gerade laufenden Save- Vorgang wirksam.

#### uf_SetDefaults

##### Argumente

-   al_row
-   Argument des Default- Events wird 1:1 durchgereicht

##### Rückgabewert

-   (None)

##### Beschreibung

-   Initialisiert Felder einer neuen Row mit Werten, welche dazu in der
    Datenbank verspeichert sind.
-   Wird standardmäßig im Default- Event aufgerufen.
-   Darf nur im Default- Event- Script verwendet werden.
-   Sollte auch im überschriebenen Default- Event- Script vorhanden
    sein.
-   Ausprogrammierte Defaults können entweder davor oder danach
    erfolgen, je nachdem, ob sie die in der Datenbank verspeicherten
    Defaults übersteuern sollen oder nicht.
-   hat ein Feld Ein/Ist- Logik, wird das "ein:"- Feld gesetzt - siehe
    dazu \#### uf_DefineEinIstCol

Siehe unbedingt - default- Event

#### uf_SetErrorTxtNl

##### Argumente

-   as_text

##### Beschreibung

-   wie uf_SetErrorTxt2nl, allerdings ohne Übersetzungsfunktionalität (
    as_text muss bereits in die Sprache der Anmeldung übersetzt sein

Siehe auch - uf_information - uf_DispErrorTxt

#### uf_SetErrorTxt2nl

##### Beschreibung

-   Syntax und Übersetungsfunktionalität genau wie
    w_ApplObj.wf_information
-   Soll im ItemChangedAppl- Event- Script eine nicht- Standard- Meldung
    an den Benutzer erfolgen , wenn das Feld nicht akzeptiert wird, so
    ist diese mit uf_SetErrorTxt bekanntzugeben.

Siehe auch - uf_information - uf_DispErrorTxt - uf_SetErrorTxtNl

#### uf_SetFocus

##### Argumente

##### Rückgabewert

-   (None)

##### Beschreibung

-   Setzt den Focus auf this. Dabei wird ggf. das Tab gewechselt.
-   dies geschieht allerdings erst mit dem SetPresentation
-   siehe auch uf_JumpToField

#### uf_SetItemStatusNew

##### Argumente

-   al_row
-   kann weggelassen werden, dann:
-   werden alle Rows behandelt

##### Rückgabewert

-   (None)

##### Beschreibung

-   Setzt den Status der Row lt. al_row auf "neu eingefügt"

#### uf_SetAllLineNr

##### Argumente

##### Rückgabewert

## boolean

-   false: es gibt keine mit uf_SetLineNrCol definierte Zeilennummen-
    Column
-   true: sonst

##### Beschreibung

-   Setzt in allen Zeilen im DW die mit uf_SetLineNrCol definierte
    Zeilennummen- Column auf die Zeilennummer.
-   Die Funktion wird automatisch beim Speichern vor dem BeforeUpdate-
    Event aufgerufen. Wird allerdings im BeforeUpdate oder im
    BeforeUpdateDetail- Event- Script das DW umsortiert, muß die
    Funktion nachfolgend nochmals aufgerufen werden.

#### uf_SetLineNrCol

##### Argumente

-   as_column
-   Name der Column, welche Zeilennummer des DWs enthält
    -   ab_ResortByDragAndDrop
-   optional, default = false
-   bei true:
-   können Zeilen mittels Drag&Drop verschoben werden
-   ist die Sortierung fix as_column (aufsteigend)
-   wird die Zeilennummer immer vergeben, bevor eine Sortierung erfolgt
-   ACHTUNG: es wird jeder Aufruf von uf_DefineSort ignoriert

##### Rückgabewert

-   (None)

##### Beschreibung

-   Hiermit kann dem System mitgeteilt werden, in welcher Column die
    Zeilennummer steht, sodaß diese Column vor dem Speichern vom System
    gesetzt werden kann.
-   der Aufruf darf ausschließlich im definition- Event erfolgen.

Siehe auch - uf_SetAllLineNr

#### uf_SetDsLookupTimeRetrieve

##### Argumente

##### Rückgabewert

-   (None)

##### Beschreibung

-   gaukelt vor, dass ein Retrieve von idw_master stattgefunden hat und
    somit beim Lookup ggf. nicht aus dem Buffer sondern aus der DB
    gelesen wird. - Siehe unbedingt uf_AddAot Parameter
    ai_LookupBufferrows und alle dortigen Links, falls dieser
    Mechanismus nicht schon bekannt ist.

## Wann verwenden

-   wurde für Windows, deren idw_neu keine update- Tabel haben und nur
    beim Starten/Wecken des Windows (also im BeforeCommand- Script)
    retrieved wird eingeführt. (z.B. MDE- Programm)
-   In diesem Fall würde der Lookup immer aus dem Buffer erfolgen, weill
    ja der Retrieve nur ein Mal erfolgt
-   Funktion sollte dann z.B. nach jeder Benutzerinteraktion aufgerufen
    werden

#### uf_SetRetrieveLookup

##### Argumente

-   ab\_
-   true ( Beim Retrieve sollen Lookups erfolgen
-   false (
-   Beim Retrieve sollen Keine Felder "genullt" werden und kein Lookup
    durchgeführt werden
-   Es werden kein Copy- Columns kopiert (uf_DefineCopyCol)
-   es werden die Zeilennummernfelder nicht automatisch gesetzt
    (uf_SetLineNrCol)
-   es wird das Event RetrieveSetConst nicht aufgerufen
-   es wird das Berechtigundfeld nicht gesetzt (Auslesen von
    Berechtigung auf "prog_teil"-Ebene in DWO- Expressions)

##### Rückgabewert

-   (None)

##### Beschreibung

-   ist im Definition- Event aufzurufen
-   braucht nur mit false aufgerufen zu werden
-   dies ist dann zu verwenden, wenn sehr viele Rows in einem DW
    vorkommen können - es werden dann die Lookups durch das Dazujoinen
    der entsprechenden Tabellen im Select des DWs ersetzt
-   Ein Problem ist allerdings F5 im Zustand Update - es geschieht genau
    nichts
-   siehe auch SollLookedup

## uf_SetSelectSubst (geerbt von dw_ApplEnv)

##### Argumente

-   as_pattern
-   String der ersetzt werden soll
    -   as_text
-   String durch den ersetzt werden soll

## alternative Argumente 1 - noch nicht implementiert

-   auo_ParList
-   siehe cst_ParList
    -   as_WohinMatch
-   siehe cst_ParList.uf_AddPar
-   Es werden für alle "wohin" aus auo_ParList, für die match ( wohin,
    as_WohinMatch ) true ist, die Ersetzungen durchgeführt.

## alternative Argumente 2 - noch nicht imlementiert

-   as_SelConst

-   Name der pfu_selkonst- Column im Select

    -   as_alias

-   Alias- Name der pfu_selkonst- Column im Select

    -   as_dattyp

-   Datentyp wie von cst_ParList erhalten (= in der Form wie in
    pfu_query)

    -   aa_wert

-   Konstanter Wert, welcher als Literal in den Select gesetzt werden
    soll

##### Rückgabewert

-   integer
-   Anzahl der Ersetzungen

##### Beschreibung

-   Ersetzt alle Vorkommnisse von as_pattern durch as_text
-   Bei "alternative Argumente 2" wird jeweils folgende Ersetzung
    durchgeführt:
-   im Select steht: select pfu_selkonst.k_datetime von_datum ...
-   der Funktionsaufruf mit ( "k_datetime", "von_datum", "dt",
    datetime(7.3.01 13:00) ) ergibt dann: z.B. für Informix: select
    "07.03.2001 13:00:00.000" von_datum ... z.B. für MS-SQL: select
    convert(datetime, "07.03.2001 13:00:00") von_datum ...
-   Darf nur im BeforeSetSelectFinish- Event- Script des windows für
    idw_list verwendet werden.
-   ACHTUNG: mehrere Aufrufe mit dem selben as_pattern sind nicht
    sinnvoll, da ja as_pattern nach dem ersten uf_SetSelectSubst- Aufruf
    nicht mehr vorhanden ist!

Siehe auch - w_ApplObj.event BeforeSetSelectFinish

## uf_SetSelectTabDazu (geerbt von dw_ApplEnv)

##### Argumente

-   as_tab
-   Tabelle, die hinzugefügt werden soll
    -   as_alias
-   Alias- Name für obige Tabelle
-   kann leer sein

##### Rückgabewert

-   boolean
-   erfolgreich = true

##### Beschreibung

-   hängt an die FROM- Clause des Selects eine zusätzliche Tabelle ung
    ggf. einen zugehörogen Aliasnamen an
-   Darf nur im BeforeSetSelectFinish- Event- Script des windows für
    idw_list verwendet werden.

Siehe auch - w_ApplObj.event BeforeSetSelectFinish

#### uf_SetToRetrieve

##### Argumente

##### Rückgabewert

-   boolean
-   true ( Erfolg, false ( Mißerfolg

##### Beschreibung

-   Bewirkt, daß der Master- Detail- Verbund, welchem das DW des
    Funktionsaufrufes angehöhrt, retrieved wird, sobald es sichtbar ist
    oder darauf zugegriffen wird.
-   ist der Master- Detail- Verbund, welchem das DW des
    Funktionsaufrufes angehöhrt im Status Update, wird uf_Refresh
    aufgerufen
-   ist das Window im Status Empty bzw. Neu wird nichts gemacht und
    false returned

#### uf_SetUpdate

##### Argumente

##### Rückgabewert

-   boolean
-   false, wenn es nicht funktioniert hat

##### Beschreibung

-   setzt den Master-Detail-Verbund in den Status Update

#### uf_Sort

##### Argumente

-   as_sort
-   siehe uf_DefineSort
-   kann weggelassen werden, dann wird Sortierung lt. dem letzten
    uf_sort bzw. uf_define_sort bzw. lt. gridschema herangezogen
    -   ab_Save
-   kann weggelassen werden, dann wird false angenommen
-   bei true wird die aktuelle Sortierung weggespeichert und diese kann
    dann mittels uf_SortRestore wiederhergestellt werden

##### Rückgabewert

-   boolean
-   true ( Sortieren hat funktioniert
-   false ( Fehler ist aufgetreten

##### Beschreibung

-   Sortiert DW
-   macht auch GroupCalc!

Siehe auch - uf_DefineSort

#### uf_SortRestore

##### Argumente

##### Rückgabewert

-   boolean
-   true ( Sortieren hat funktioniert
-   false ( Fehler ist aufgetreten

##### Beschreibung

-   stellt die Sortierung, die bei uf_Sort( ... ab_save=true)
    weggeseichert worden ist, wieder her

#### uf_SqlOk

-   sollte nicht mehr verwendet werden
    -   siehe tr\_.uf_SqlOk

#### uf_status

## `<uf_status>`{=html}

##### Argumente

##### Rückgabewert

-   char
-   Folgende Werte: "n" ( (new) es wird gerade ein neues AO angelegt und
    idw_master ist w_ApplObj.idw_neu "u" ( (update) in einem DW des
    Master- Detail- Verbunds wurde eine Änderung durchgeführt und es
    wurde noch nicht gespeichert "r" ( (to retrieve) DWs des Master-
    Detail- Verbunds müssen neu retrieved werden (dies wird
    ausschließlich vom System durchgeführt!) "e" ( (empty) AO- Auswahl
    ist leer (( Liste ist leer) "d" ( (display) Master- Detail- Verbund
    ist retrieved, nicht geändert und muß nicht retrieved werden

#### uf_ToColFormat

##### Argumente

-   as_column
-   name der Column, dessen Format verwendet wird
-   muss eine Column des DWOs sein
-   siehe gf_ToColFormat
    -   aa_wert
-   Wert, der auf das entsprechende Format beschnitten werden soll
-   beschnitten bedeutet dabei z.B. 3 Nachkommastellen auf eine

##### Rückgabewert

-   any
-   der auf das entsprechende Format zurechtgestutzte Wert

##### Beschreibung

-   Beschneidet aa_wert, sodass er dem Format von as_column entspricht

#### uf_TouchItem

##### Argumente

-   al_row
-   Zeile des DWs
    -   as_column
-   Feldname

##### Rückgabewert

-   boolean
-   true, wenn Feld auf Status geändert gesetzt worden ist.

##### Beschreibung

-   Setzt Feld auf Status geändert.

## Wann verwenden

> Im BeforeUpdate eines Master- DWs: - damit wird erzwungen, daß update
> erfolgt und ggf. die Column in der WHERE- Clause des UPDATE
> aufscheint - So kann abgesichert werden, daß Verbund nicht gespeichert
> werden kann, wenn anderes Window nach dem Retrieve geändert hat.

#### uf_unfilter

##### Argumente

-   ab_sort
-   true ( Das DW auf den der Filter angewendet wird, wird neu sortiert
-   ist optional ( es wird true angenommen

##### Rückgabewert

-   none

##### Beschreibung

-   entfernt den mittels uf_filter gesetzten Filter, falls ein solcher
    vorhanden ist (( kann unabhängig davon, ob man weiß ob ein Filter
    gesetzt ist, bedenkenlos aufgerufen werden)

#### uf_yes

##### Argumente

-   as_text
-   Frage an den Benutzer
    -   ac_YesNo
-   "y" ( Default- Button ist Yes
-   "n" ( Default- Button ist No

##### Rückgabewert

-   boolean
-   true, wenn der Anwender yes ausgewählt hat

##### Beschreibung

-   Sollte verwendet werden, wenn eine Ja/Nein- Entscheidung durch den
    Benutzer erforderlich ist.
-   Alternativ kann auch w_ApplObj.wf_yes verwendet werden.

## Variables

## ib_InColSearch

-   Darf nicht verändert werden!
-   ist true, wenn gerade das ColSearch- Window aufgerufen wird

## ib_InExportKeyToParent

-   Darf nicht verändert werden!
-   ist true, wenn gerade ExportKeyToParent (also Ctrl+R oder Rückgabe
    beim Colsearch) durchgeführt wird
-   eingeführt für J.Poppe für folgende Situation:
-   wenn ein bestimmtes AEO- Key- Feld durch ExportKexToParent befüllt
    wird soll nichts geschehen
-   sonst soll, unter gewissen Umständen ein Search ausgelöst werden

## ib_InRetrieveEndAppl

-   Darf nicht verändert werden!
-   true, wenn für das DW oder ein anderes DW des Master- Detail-
    Verbunds gerade das RetrieveEndAppl- Event ausgeführt wird (solange
    das Event im Callstack ist!)
-   true, wenn für das DW oder ein anderes DW des Master- Detail-
    Verbunds gerade uf_aktion ( ab_InRetrieveEndAppl=true ) ausgeführt
    wird (solange die Funktion im Callstack ist!)

## ib_MdeAppl

-   Darf nicht verändert werden!
-   true, wenn Applikation imMDE- Modus ist

## ib_pasting

-   Darf nicht verändert werden!
-   true, wenn DW gerade gepastet wird
-   ist nicht mehr true, wenn der Benutzer schon wieder die Kontrolle
    gehabt hat, also auch im protect- Eventscript

## ib_resetting

-   Darf nicht verändert werden!
-   darf nur im ItemChangedAppl- Event abgefragt werden
-   true, wenn Feld gerade auf den alten Wert zurückgesetzt wird

## ib_retrieving

-   Darf nicht verändert werden!
-   true, wenn ein DW, für das das aktuelle DW Master ist, gerade
    retrieved wird, dazu gehören auch die vom Retrieve initierten
    Lookups und das RetrieveEndAppl- Event und natürlich alle von dort
    direkt bzw. indirekt ausgelösten Scripts.
-   ist nur bei idw_master gesetzt!!!

## ib_SortAfterUpdate

-   Darf jederzeit verändert werden!
-   ist standardmäßig = true
-   Nach dem Speichern wird für jedes DW, für das
    ib_SortAfterUpdate=true ist, ein Sort() durchgeführt
-   dies störte Wolfgang bei Adeg- Auftragschnellerfassung ( Er setzt
    die Variable im BeforeCommand- Event auf false
-   sie kann aber auch im AfterUpdate- Script jedes Mal neu gesetzt
    werden
-   wird bei Monitoren von idw_function ausgewertet

## ii_null

-   Darf nicht verändert werden!
-   ist fix Null

## il_null

-   Darf nicht verändert werden!
-   ist fix Null

## is_null

-   Darf nicht verändert werden!
-   ist fix Null

## iuo_ae

-   Darf ausschließlich zum Zugriff auf die freigegebenen
    Funktionen/Events/Variablen von cst_ApplEnv verwendet werden!!!
-   Das sogenannte Environment des Windows vom Typ cst_ApplEnv

## iuo_DwApplObj

-   es dürfen Änderungen weder an noch in iuo_DwApplObj vorgenommen
    werden
-   Allerdings kann über das Event CstDwApplObj eine eigene von
    cst_DwApplObj abgeleitete Klasse für iuo_DwApplObj herangezogen
    werden
-   Members dieser eigenen Klasse dürfen im definition- Eventscript
    uneingeschränkt verwendet werden

## iw_ApplObj

-   Darf ausschließlich zum Zugriff auf die freigegebenen
    Funktionen/Events/Variablen von dw_ApplObj verwendet werden!!!
-   Window, auf dem DW klebt

## dw_ApplObjList (abgeleitet von dw_ApplObj)

-   die Beschreibung der Events und Functions ist bei dw_ApplObj
    nachzulesen

ACHTUNG: keine Event- Scripts erweitern/übersteuern!!! außer:

## Definition

-   Folgendes darf hier geschehen:
    -   uf_BerechtMapProgteil

## EditChangedAppl

-   es ist sinnvoll dies stattt protect zu verwenden und hier
    idw_neu.uf_protect aufzurufen

## IAeoSearch / IAeoShow

## RetrieveEndAppl

-   siehe dw_ApplObj.RetrieveEndAppl
-   Abweichung: uf_status() liefert 'd'
-   wenn Zeilen eingefügt werden sollen, hat dies im RetrieveList-
    Eventscript zu erfolgen

## RetrieveList

##### Argumente

##### Rückgabewert

-   (None)

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   hier wird standardmäßig der Retrieve des DW's durchgeführt
-   soll das DW anderweitig befüllt werden, kann dies hier durchgeführt
    werden

## RetrieveRow

##### Argumente

##### Rückgabewert

-   long
-   0 .. weiter retrieven
-   1 .. abbruch

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   geht für jeden Datensatz auf, welcher retrieved wird.
-   hier wird anhand von pfu_win.max_ret_rows geprüft ob weiter
    retrieved werden soll, oder ob abbgebrochen werden soll

ACHTUNG: keine Functions verwenden!!! außer:

## ScrollToRow

##### Argumente

-   al_row
-   Zeile zu der gescrollt werden soll

##### Rückgabewert

-   long

-   0 ( erfolgreich

-   ANMERKUNG:

-   in der PB- 8- Doku steht: 1 = erfolgreich , -1 = versagt - stimmt
    für PB8

-   in der PB- 10- Doku steht: al_row = erfolgreich, -1 = versagt - dies
    simmt nicht

-   sonst ( versagt

-   ACHTUNG: nachdem es immer wieder Probleme gibt, ist es besser,
    danach mittels GetRow abzufragen, ob die aktuelle Row die gewünschte
    ist.

##### Beschreibung

-   scrollt zu einer bestimmten Zeile
-   ACHTUNG:
-   darf nur im Status Display erfolgen
-   es ist danach eine anderes AO das aktuelle (z.B.: Artikelwindow:
    vorher ist Artikel "4711" aktiv, danach Artikel "4769")
-   siehe auch w_ApplObj. wf_ScrollToFindWhere

## GetRow

##### Argumente

##### Rückgabewert

-   long

-   0 ( aktuelle Zeile

-   sonst ( es gibt keine aktuelle Zeile

##### Beschreibung

-   ACHTUNG:
-   siehe vorher w_ApplObj.
-   sollte im Status "e" nicht ausgeführt werden!
-   siehe auch cst_ApplEnv.uf_KeyFindWhere

## dw_MdeButton

-   enthält DW- Buttons (siehe wf_AddDwButtonAppl) für MDE- Modus
-   Abgeleitet von dw_ApplObj_Tci ( auch von dw_ApplObj
-   es ist unabhängig vom Zustand lt. uf_status immer eine Row vorhanden
    (( die Buttons stehen zu Verfügung)

## dw_JobObj

## Events

## RetrieveByKey

##### Argumente

-   aa\_
-   kommt von uf_retrieve

##### Rückgabewert

-   long
-   Anzahl der gefundnen Rows, wenn Select OK
-   -1 bzw. NULL, wenn nicht OK

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   Führt retrieve des DWs durch
-   Hat ein DW keinen SELECT, kann hier das DW anderweitig befüllt
    werden

## TransObject

##### Argumente

##### Rückgabewert

-   tr\_
-   Transaktionsobjekt für das DW

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   Hier kann das Transaktionsobjekt für das DW bestimmt werden
-   Standardmäßig ist dies sqlca

### Functions

## filter

##### Argumente

##### Rückgabewert

-   long
-   1 (OK
-   sonst ( nicht OK

##### Beschreibung

-   aktiviert den Filter des DWOs V

## find

##### Argumente

-   as_expression
-   ein Ausdruck wie in der Where- Bedingung eines Select- Statements.
    Allerdings werden statt DB- Columns DW- Columns angesprochen
-   es werden keine Tabellennamen angegeben
    -   al_start
-   Suche fängt bei dieser Row an
    -   al_end
-   Suche hört bei dieser Row auf
-   al_end kann \> al_start sein, dann wird rückwärts gesucht

##### Rückgabewert

-   long
-   die erste Row in der Suchrichtung von al_start weg, welche
    as_expression erfüllt
-   0 ( keine Row erfüllt die Expression
-   null ( irgendwas ist null

## Siehe

-   cst_ApplEnv::uf_KeyFindWhere

#### uf_CopyFrom

##### Argumente

-   adw_from
-   dw_JobObj
-   von diesem DW wird koipiert

##### Rückgabewert

-   long
-   Anzahl der Rows

##### Beschreibung

-   Kopiert alle Rows von von adw_from von Row 1 weg ins aufrufende DW

#### uf_CopyGeneratedFile

##### Argumente

-   as_TargetFilename
-   siehe Beschreibung
    -   ab_ReplaceTargetIfExists
-   wenn das as_TargetFilename entsprechende File existiert wird bei
    ab_ReplaceTargetIfExists=true überschrieben, sonst wird -2
    zurückgeliefert

##### Rückgabewert

-   integer \> 0 ( ok \> -1 ( Fehler beim Anlegen eines Directories \>
    -2 ( Fehler beim Kopieren \> -3 ( Es wurde kein File mit uf_print
    generiert

##### Beschreibung

-   Kopiert das mit dem letzten uf_print erzeugte Druckfile auf
    as_TargetFilename
-   siehe auch is_GeneratedFileName

## uf_CountInSelect (geerbt von dw_ApplEnv)

##### Argumente

-   as_CountFrom
-   zunächst wird dieser Text von Beginn weg im Select- Statement
    gesucht.
-   Die eigentliche Suche beginnt erst ab dem obigen Vorkommnis
    -   as_text
-   Dieser Text wird gesucht
    -   ai_AnzInVirgin
-   by reference, wird gesetzt
-   Anzahl der Vorkommnisse von as_text im Orginal- Select (ohne
    Ersetzung der Suchbedinhungen)
    -   ai_AnzInAkt
-   by reference, wird gesetzt
-   Anzahl der Vorkommnisse von as_text im aktuellen Select (mit
    Ersetzung der Suchbedinhungen)

##### Rückgabewert

-   (None)

##### Beschreibung

-   Liefert die Anzahl der Vorkommnisse eines Textes im Select-
    Statement

#### uf_retrieve

##### Argumente

-   aa\_
-   wird eins zu eins an die Events BeforeRetrieve und RetrieveByKey von
    dw_JobObj weitergeleitet

##### Rückgabewert

-   long
-   Anzahl der Rows

##### Beschreibung

-   Führt Retrieve des DWs durch
-   Dazu folgende Event- Aufrufe (der Reihe nach): . RetrieveByKey

#### uf_Sort

##### Argumente

-   as_sort
-   kann weggelassen werden, dann wird Sortierung lt. dem letzten
    uf_sort
    -   ab_Save
-   kann weggelassen werden, dann wird false angenommen
-   bei true wird die aktuelle Sortierung weggespeichert und diese kann
    dann mittels uf_SortRestore wiederhergestellt werden

##### Rückgabewert

-   boolean
-   true ( Sortieren hat funktioniert
-   false ( Fehler ist aufgetreten

##### Beschreibung

-   Sortiert DW
-   macht auch GroupCalc!

#### uf_SortRestore

##### Argumente

##### Rückgabewert

-   boolean
-   true ( Sortieren hat funktioniert
-   false ( Fehler ist aufgetreten

##### Beschreibung

stellt die Sortierung, die bei uf_Sort( ... ab_save=true) weggeseichert
worden ist, wieder her

#### uf_print

ACHTUNG: wird nicht weiterentwickelt - weitere Anforderungen können über
\## die unter wf_NewDruck beschriebenen Methode realisiert werden

##### Argumente

-   es gibt 3 alternative Varianten: \> keine Argumente \> alle
    Argumente \> nur die mit \* gekennzeichneten Argumente
    -   as_DruckartCd \*
-   Art des Ausdrucks lt. Tabelle pfu_druckart
-   Anmerkung: Orginal und Kopie können eine unterschiedliche Druckart
    sein
-   Vor dem Drucken der Kopie wird im DW das Wort Kopie eingesetzt
-   "@druckart" bedeutet: Ermitteln lt. Tabelle pfu_druckart via Window-
    und Datawindow- Name
-   wenn nicht vorhanden, wird "@druckart" angenommen
    -   as_DruckNr \*
-   Drucknummer
-   z.B. Bei Rechnung die Rechnungsnummer
-   "@job" bedeutet: lt. pfu_job
-   wenn nicht vorhanden, wird "@job" angenommen
    -   MFA- Argumente:
-   bestimmen die MFA- Belegung für den Ausdruck (pfu_job_druck- Row)
-   wenn ai_mfa1_nr NULL ist, wird als MFA- Belegung für den Ausdruck
    die genaueste (= diese mit dem wenigsten 0- Werten, wobei dabei
    nicht- 0- Werte nach 0- Werten nicht als solche zählen (1,0,0 kommt
    vor 0,2,3)) der nachfolgend aufgezählten MFA- Belegungen
    heangezogen:
-   wenn die MFA- Argumente nicht vorhanden sind, wird jeweils 0
    angenommen
    -   lt. Parametern des Jobs mittels
        w_JobObj.iuo_JobParList.uf_GetMfa
    -   lt. Job
-   ACHTUNG: die Aplikation hat dafür zu sorgen, dass nie Daten, welche
    nicht der Job- MFA bzw. nicht der Parlist- MFA entsprechen, gedruckt
    werden!!!
-   sonst hätte der Ausdruck eine genauere MFA als die Daten, wodurch
    der Anwender dann Ausdrucke mit Daten, die nicht der Anmeldungs- MFA
    entsprechen anschauen bzw. nachdrucken kann
-   nenn nicht vorhanden, wird jeweils NULL angenommen
-   die ermittelte MFA ist für pfu_druckerzuord relevant (Firmenpapier)
-   ACHTUNG: die Aplikation hat dafür zu sorgen, dass nie Daten, welche
    nicht der MFA- Belegung für den Ausdruck entsprechen, gedruckt
    werden!!!
-   sonst hätte der Ausdruck eine genauere MFA als die Daten, wodurch
    der Anwender dann Ausdrucke mit Daten, die nicht der Anmeldungs- MFA
    entsprechen anschauen bzw. nachdrucken kann
    -   ai_mfa1_nr \*
    -   ai_mfa2_nr \*
    -   ai_mfa3_nr \*
    -   ai_ZuDruckenAnz \*
-   Anzahl der Exemplare
-   Wenn der Drucker nicht bestimmt ist (weder Zuordnung über
    pfu_drucker_zu noch explizite Angabe des Druckers über
    as_DruckerCd), wird Wert ignoriert.
-   wenn nicht vorhanden, wird 1 angenommen
    -   ac_komart_kz
-   Kommunikationsart 'd' ( drucken 'f' ( faxen 'e' ( Versand via Email
    'k' ( kein Ausdruck
-   standardmäßig nicht möglich
-   pfu_kz muss indiv angelegt werden
-   wirkt nur, wenn eine Zuordnung auf den Drucker "kein Ausdruck"
    vorhanden ist
-   wenn nicht vorhanden, wird "d" angenommen
-   nur relevant, wenn as_DruckerCd direkt oder indirekt (via @job) =
    "laut zuordnung"
    -   as_ApplFkz \*
-   Freies Kennzeichen für die Druckerzuordnung
-   kann leer sein
-   wenn nicht vorhanden, wird " " angenommen
    -   as_DruckerCd
-   Drucker lt. Tabelle pfu_drucker
-   "@job" bedeutet: lt. pfu_job
-   wenn nicht vorhanden, wird "@job" angenommen
-   folgende Drucker haben eine Spezialbedeutung:
    -   "laut zuordnung"
-   Drucker und Lade werden lt. Tabelle pfu_druckerzu ermittelt
    -   ""
-   nicht mehr verwenden!!!
-   gleiche Bedeutung wie "laut zuordnung"
    -   "kein ausdruck"
-   es erfolgt kein Ausdruck - es wird nur das Druckfile erstellt
    -   as_LadeCd
-   Drucker- Lade lt. Tabelle pfu_drucker_lade
-   wird ignoriert, wenn as_DruckerCd = "@job", sollte allerdings dann
    auch "@job" sein
-   wird ignoriert, wenn as_DruckerCd "laut zuordnung", "" oder "kein
    ausdruck" ist, sollte dann allerdings "" sein
    -   as_KommNr
-   "@job" bedeutet: lt. pfu_job
-   wenn nicht vorhanden, wird "@job" angenommen
-   Kommunikationsnummer für Fax oder E-Mail
-   abhängig von pfu_drucker.drucker_kz des zum Einsatz kommenden
    Druckers gilt
-   'd', 'k' ( as_KommNr wird ignoriert
-   'f' ( as_KommNr muss Faxnummer enthalten
-   'e' ( as_KommNr muss Emailadresse enthalten
    -   as_empfänger (vormals as_ZuHanden)
-   kann mehrzeilig sein
-   z.B.: Hopferwieser AG Zentrale Salzburg Hr. Prok. G. Prossinger
-   wird ignoriert, wenn as_KommNr = "@job", Wert lt. pfu_job
-   wenn nicht vorhanden, wird " " angenommen
    -   as_absender
-   kann mehrzeilig sein
-   z.B.: PCS Pfundner SC Andreas Kainz
-   wird ignoriert, wenn as_KommNr = "@job", Wert lt. pfu_job
-   wenn nicht vorhanden, wird " " angenommen
    -   as_betreff
-   wird ignoriert, wenn as_KommNr = "@job", Wert lt. pfu_job
-   wenn nicht vorhanden, wird " " angenommen
    -   as_messagebody
-   muss man sich genauer ansehen, wie und wann das funktioniert
    -   as_FileTyp
-   Filetyp des Ausdruck- Files
-   derzeit implementiert:
    -   "pdf"
    -   "txt"
-   alle Columns im Detail- Band werden durch TABs getrennt ausgegeben
-   von rechts nach links
-   es sollten alle Felder im DW nebeneinander stehen
-   Wenn nicht angegeben, wird "pdf" angenommen

##### Rückgabewert

-   integer
-   laufende Ausdrucknummer (pfu_job_druck.job_druck_lfd_nr)
-   -1, falls das Erzeugen des Ausdruck- Files nicht erfolgreich war

##### Beschreibung

-   Führt print des DWs durch. Dadurch wird ein Ausdruck- File erzeugt
    und archiviert.
-   Der eigentliche Ausdruck erfolgt erst durch die Funktion
    wf_ToPrinter.
-   Macht "commit using sqlca;", wenn keine Transaction offen ist!

## uf_SetSelect (geerbt von dw_ApplEnv)

##### Argumente

-   as_select
-   String der ersetzt werden soll

##### Rückgabewert

-   boolean
-   true, wenn erfolgreich

##### Beschreibung

-   Setzt das Selectstatement des DWO's neu.
-   Das neue Select- Statement muß die selben DW- Columns, wie der
    Orginal- Select haben (ggf. Alias- Namen verwenden!)

## uf_SetSelectSubst (geerbt von dw_ApplEnv)

##### Argumente

-   as_pattern
-   String der ersetzt werden soll
    -   as_text
-   String durch den ersetzt werden soll

## alternative Argumente

-   auo_ParList
-   siehe cst_ParList
    -   as_WohinMatch
-   siehe cst_ParList.uf_AddPar
-   Es werden für alle "wohin" aus auo_ParList, für die match ( wohin,
    as_WohinMatch ) true ist, die Ersetzungen durchgeführt.

##### Rückgabewert

-   integer
-   Anzahl der Ersetzungen

##### Beschreibung

-   Ersetzt alle Vorkommnisse von as_pattern durch as_text.
-   Folgender Ablauf der Aufrufe: . uf_SetSelectStart()
-   Der Select- String wird auf den Orginalzustand initialisiert . ein-
    oder mehrere Male uf_SetSelectSubst ( ... )
-   ACHTUNG: mehrere Aufrufe mit dem selben as_pattern sind nicht
    sinnvoll, da ja as_pattern nach dem ersten uf_SetSelectSubst- Aufruf
    nicht mehr vorhanden ist! . uf_SetSelectFinish()
-   kann vor jedem Retrieve erfolgen.

## uf_SetSelectTabDazu (geerbt von dw_ApplEnv)

#### uf_Sign

##### Argumente

-   as_SignerName
-   der Name des Signierers = String in der Spalte "Ausgestellt für" lt.
    den nachfolgenden Screenshots \[pic\] \[pic\]
-   dient zur Auswahl des Zertifikats
-   wenn eine neue Version des Zertifikats installiert wird, gibt es 2
    Zeilen mit dem gleichen "Ausgestellt für" ( was dann passiert müsste
    man testen oder man löscht die alte Version
-   wird im Dokument im Signatur- "Kastl"- angezeigt
-   wird direkt am Dokument angezeigt, wenn as_signaturepicture leer ist
    -   as_reasontosign
-   freier Text für den Grund für die Unterschrift
-   wird im Dokument im Signatur- "Kastl"- angezeigt
-   z.B. bei einer Ingram- Rechnung steht hier "Invoice"
    -   as_location
-   freier Text für den Zeichnungsort der Unterschrift
-   z.B. "Wien"
-   wird im Dokument im Signatur- "Kastl"- angezeigt
    -   as_signaturepicture
-   unc- Name des Bildfiles (.jpg wurde getestet), das im Dokument im
    Signatur- "Kastl"- angezeigt wird
-   hierfür wird z.B. die Unterschrift des Zertifikateigners
    herangezogen
-   kann leer sein
-   Bild wird direkt am Dokument angezeigt, wenn es nicht leer ist
-   statt eines UNC- Namens kann auch ein Filenamepfad relativ zum
    Verzeichnis der .exe angegeben werden (Bsp.:
    "logo`\Ferdi`{=tex}.jpg"
    -   al_printonpage
-   auf dieser Seite wird das Signatur- "Kastl"- angezeigt
-   -1 ist die letzte Seite
    -   al_horzpos_in_twips
-   horizontale Position in "Twips" von links
-   "Twips" ist ein unberechenbare astrale Längeneinheit ( ausprobieren
    nötig!!! - oder etwa doch nicht ( siehe weiter unten
    -   al_vertpos_in_twips
-   vertikale Position in "Twips" von oben
    -   al_width_in_twips
    -   al_height_in_twips

## Basierend auf der anglo-amerikanischen Längeneinheit Point (pt), bezeichnet

ein Twip die Teilung "TWentieth of an Inch Point", also 1/20 Punkt =
1/1440 Zoll. Das Twip als extrem feine Maßeinheit (knapp 0,018 mm - ca.
57 Twips ergeben einen Millimeter) findet Verwendung in Berechnungen von
Schrift und Grafik im Computerbereich, z.B. im Graphics Device Interface
(GDI) von Microsofts \## Windows-Betriebssystem, im Dateiformat Windows
Metafile (WMF) oder im

Druckdatenformat AFP.

##### Rückgabewert

-   boolean

##### Beschreibung

-   signiert das zuvor mittels uf_print erstellte pdf- Dokument
-   weiters wird das Dokument mit dem Password `<noch festlegen>`{=html}
    schreibgeschützt - ggf. als Parameter übergeben

#### uf_untrim

##### Argumente

-   as_column
-   Column- Name
    -   aa_wert
-   Wert der "enttrimmt" werden soll

##### Rückgabewert

-   Any
-   wenn as_column eine CHAR- Column ist ( aa_wert mit Leerzeichen auf
    die Länge von as_column verlängert
-   sonst ( aa_wert

## Wann verwenden

-   wenn in einer char- Column sich in manchen Rows Werte aus dem Select
    und in manchen Rows mittels SetItem gesetzte Werte befinden gibt es
    folgendes Problem, das über ein Beispiel erklärt wird:
-   in einer Row, die über Select befüllt ist steht in der Column Lager
    "hpt"
-   in einer Row, die über SetItem befüllt ist steht in der Column Lager
    "hpt"
-   wird jetzt nach dieser Column und nachfolgend nach einer weiteren
    Column sortiert, kommt "hpt" vor "hpt" und die 2. Sortiercolumn hat
    keine Auswirkung
-   durch SetItem ( ... untrim("lag_cd", ls_lag_cd) ... ) kann dies
    verhindert werden

## Variables

## is_GeneratedFileName

-   das durch den letzten Aufruf von uf_print generierte File
-   es handelt sich bereits um das archivierte File!
-   siehe auch uf_CopyGeneratedFile
-   darf nicht verändert werden!

## m_ApplObj

-   Das Menü zu einem w_ApplObj

## Menüpunkte

## m_window

-   Standart: "Window öffnen"
-   wird per Str+W aufgerufen
-   siehe SetMenuWindow

## Ableitung

-   darf überschrieben werden

### Functions

## mf_RadioClicked (geerbt von m_ApplEnv)

##### Argumente

-   am_checked
-   Menüpunkt, welcher angehakt ist
-   Dazu ist im Menü eine Instance- Variable vom typ menu für jede
    Gruppe von Menüpunkten, welche sich gemeinsam wie Radiobuttons
    verhalten, zu deklarieren.
-   Diese Instance- Variable ist zu übergeben.
    -   am_NewChecked
-   hier ist this zu übergeben

##### Rückgabewert

-   (None)

##### Beschreibung

-   Die Funktion ist im Clicked- Eventscript jedes Menüpunktes
    aufzurufen, welcher zu einem Radiobutton- Komlex gehört.

Siehe auch - w_ApplObj.wf_InitRadioMenu - w_ApplObj.event
RadioMenuClicked

## mf_ToggleClicked (geerbt von m_ApplEnv)

##### Argumente

-   am\_
-   hier ist this zu übergeben

##### Rückgabewert

-   (None)

##### Beschreibung

-   Die Funktion ist im Clicked- Eventscript jedes Menüpunktes
    aufzurufen, welcher dies Toggle- Funktionalität (anghakt/nicht
    angehakt) hat.

Siehe auch - w_ApplObj.wf_InitToggleMenu - w_ApplObj.event
ToggleMenuClicked (geerbt von w_ApplEnv)

## tr\_

## `<tr_>`{=html}

-   das Transaction- Object

### Functions

#### uf_AnyToLiteral

##### Argumente

-   aa_arg
-   Ein beliebiger Wert eines vom Transaktionsobjekt unterstützten
    Datentyps. (Dies sind standardmäßig die Standard- Datentypen einer
    Datenbank)

##### Rückgabewert

-   string

##### Beschreibung

-   macht aus aa_arg einen String, der als Literal in einem SQL-
    Statement stehen kann
-   der Aufbau des Literals ist abhängig von der Datenbank (Informix /
    Oracle / MSSQL)
-   z.B. uf_AnyToLiteral ( ad_xy_datum ) liefert '23.12.2002' und in
    einer anderen Datenbank '20021223'
-   Ist notwendig um Datenbankunabhängigkeit zu gewährleisten!!!

#### uf_arg

##### Argumente

-   as_arg
-   Ein Retrievel- Argument für die Retrieve- Funktion eines Datastores
    oder eines DWs

##### Rückgabewert

-   string

##### Beschreibung

-   Immer wenn eine String als Retrieval- Argument übergeben wird, muß
    er durch die Funktion uf_arg behandelt werden ( retrieve ( ......,
    itr\_.uf_arg ( ls_xy ) ... ) )
-   uf_arg gibt es auch für dw_ApplObj !!!

## uf_connect()

##### Argumente

-   Die Funktion kann ohne Argumente oder mit den Argumenten
    lt.uf_init() aufgerufen werden.

##### Rückgabewert

-   boolean
-   false ( Connect mißlungen
-   true ( Connect gelungen

##### Beschreibung

-   ohne Argumente:
-   es muß vorher uf_init aufgerufen worden sein
-   führt Connect zur Datenbank durch mit Argumenten:
-   ruft uf_init und dann uf_connect ohne Parameter auf
-   muss im Open- Script der Applikation aufgerufen werden
-   Für informixdatenbanken ohne Transaction siehe ib_IfxNoLogging

## uf_disconnect()

##### Argumente

##### Rückgabewert

-   boolean
-   false ( disconnect mißlungen
-   true ( disconnect gelungen

##### Beschreibung

-   Führt disconnect von der Datenbank durch

## uf_DynConnect()

##### Argumente

##### Rückgabewert

-   boolean
-   false ( connect mißlungen
-   true ( connect gelungen

##### Beschreibung

-   Dient dem Connect zur Datenbank mitten im Ablauf der Applikation
-   wurde für das aktuelle Transaktionsobjekt bereits eine Connection
    mit uf_DynConnect etabliert, wird nicht neu connected, sondern nur
    die Anzahl der offenen DynConnects erhöht
-   Es muß vorher uf_init aufgerufen worden sein

## uf_Dyndisconnect()

##### Argumente

##### Rückgabewert

-   boolean
-   false ( disconnect mißlungen
-   true ( disconnect gelungen

##### Beschreibung

-   Dient dem Disconnect von der Datenbank mitten im Ablauf der
    Applikation
-   ist die Anzahl der offenen DynConnects \>1, wird kein disconnect
    durchgeführt, sondern nur die Anzahl der offenen DynConects
    erniedrigt (eigentlich vermindert)

## uf_init()

##### Argumente

-   as_dsn
-   entweder ODBC- Datasource (User-DSN oder System- DSN)
-   oder pfunder- DB-Profile
-   HKEY_LOCALE_MACHINE`\software`{=tex}`\pfundner`{=tex}`\dbprofiles`{=tex}
    -   as_uid
-   User- ID
    -   as_pwd
-   Password
    -   ab_dynconnect
-   kann weggelassen werden, dann wird false angenommen
-   true ( der Connect erfolgt mittels uf_DynConnect()
    -   ab_DirectConnectFromOdbc
-   kann weggelassen werden, dann wird false angenommen
-   true (
-   wird ausgewertet, wenn es sich um eine ODBC- SQL-Server- Datasource
    handelt
-   die Datenverbinung erfolgt dann via SQL-Server-SNC
-   die Connection- Daten werden allerdings aus der ODBC-Datasource
    ausgelesen
-   wurde für Rich-Text- Felder, die auch Bilder enthalten können sollen
    eingeführt (über ODBC können diese nicht gehandhabt werden)
    -   ab_NCharBind
-   kann weggelassen werden, dann wird false angenommen
-   true (
-   Connect Parameter um "NCharBind=1,DisableBind=0" erweitern
-   1 = Binds string input parameter to the NChar dataype

##### Rückgabewert

-   boolean
-   false ( Initialisierung mißlungen
-   true ( Initialisierung gelungen

##### Beschreibung

-   Sucht die Datasource in der Registry (unter HKEY_CURRENT_USER, dann
    HKEY_CURRENT_MACHINE)
-   Ermittelt den Datenbanktyp und belegt belegt die Instancevariable
    is_db_kz
-   Initialisiert das Transaktionsobjekt gemäß den Argumenten
-   siehe auch uf_DynConnect()
-   muss im Open- Script der Applikation aufgerufen werden

#### uf_RowNotFound

## `<uf_RowNotFound>`{=html}

##### Argumente

-   as_context
-   Text, der die Stelle im Programm, an der fie Funktion aufgerufen
    worden ist, beschreibt
-   wird im Fehlerfall im Ramen der Fehlermeldung ausgegeben

##### Rückgabewert

-   boolean
-   false ( das letzte Select- Statement hat mindestens eine Row
    gefunden
-   true ( sonst

##### Beschreibung

-   wird typischerweise nach einem emdedded SELECT- Statement
    aufgerufen, um zu ermitteln, ob eine Row gefunden worden ist
-   ACHTUNG: Das Programm wird angehalten, wenn ein Fehler aufgetreten
    ist!!!
-   siehe auch uf_SqlHaltIfCodeNot0, uf_SqlOk, uf_SqlRows
-   siehe auch uf_SqlException2nl

#### uf_serial

##### Argumente

-   as_Tabname
-   ab_instanz
-   optional
-   true ( es wird eine 14-stellige snr zurückgeliefert (4 Stellen lt.
    Instanz + 10 Stellen lt. Snr)

##### Rückgabewert

-   decimal
-   die vergebene Serial- Nummer

##### Beschreibung

-   vergibt eine Serial- Nummer lt. Tabelle pfu_serial
-   siehe auch dw_ApplObj.uf_serial
-   Bei der alten Version wurde ein long-Wert zurückgegeben !
-   Der Programmierer muss sich darum kümmern, dass die snr in eine
    decimal-Variable eingelesen wird wenn ab_instanz = true ist

#### uf_sql_column

##### Argumente

-   as_column
-   aa_wert
-   nur nach Aufruf von uf_sql_update oder uf_sql_insert anzugeben
-   Wert, der in die Datenbankcolumn geschrieben werden soll
-   Kann eine andere Datenbankcolumn sein, dann ist ab_AnyToLit=false
    anzugeben
    -   ab_AnyToLit
-   siehe aa_wert
-   true ... es wird uf_AnyToLiteral ( aa_wert ) in den SQL- String
    gestellt
-   false .. es wird aa_wert direkt in den SQL- String gestellt ((
    aa_wert muß ein String sein)

##### Rückgabewert

##### Beschreibung

-   siehe uf_sql_select, uf_sql_update und uf_sql_insert

#### uf_sql_delete

##### Argumente

-   as_table
-   folgende 3 Argumente repräsentieren den ersten Teil der Where-
    Bedingung:
-   weitere Bedingungen können mit jeweils einem Aufruf von uf_sql_where
    hinzugefügt werden
-   die genaue Beschreibung der Argumente steht bei uf_sql_where
    -   as_where_column
    -   as_operator
    -   aa_where_wert

##### Rückgabewert

##### Beschreibung

-   Funktion leitet das Abschicken eines DELETE-Statements gegen die
    Datenbank ein
-   Folgender Ablauf: . uf_sql_delete . uf_sql_where - beliebig oft .
    uf_sql_exec

#### uf_sql_exec

##### Argumente

-   ads_Select
-   kann weggelassen werden
-   wenn nicht weggelassen, müssen alle Parameter angegeben werden
-   wird nur bei vorausgehendem uf_sql_select ausgewertet
-   wenn ein instanzierter Datastore (ds\_) übergeben wird, wird das
    Select- Statement über diesen Datastore, und nich über den internen
    Datastore von tr\_ abgehandelt
-   die Ergebnisse des Select können dann über den übergebenen Datastore
    mittels ds\_.uf_GetItem ausgelesen werden
-   die Funktion uf_sql_ret_wert kann dann nicht verwendet werden
-   Folgende Vorteile gegenüber dem Auslesen des Ergebnisses mittels
    uf_sql_ret_wert:
-   es können nicht nur die Werte der ersten vom Select gelieferten Row
    ausgelesen werden
-   die nachfolgend unter ACHTUNG in der Beschreibung genannte
    Problematik fällt weg
-   der Nachteil ist, dass das Script, welches uf_sql_exec verwendet,
    für den instanzierten Datastore und dessen Destroy sorgen muss
-   Kann weggelassen werden:
    -   al_minrows
-   uf_sql_exec liefert false, wenn nicht mindestens al_minrows Rows
    behandelt wurden
-   default ist 0
    -   al_maxrows
-   uf_sql_exec liefert false, wenn mehr als al_maxrows Rows behandelt
    wurden und al_maxrows \> 0 ist
-   default ist 0
    -   as_context
-   verbale Beschreibung der Position im Programm von der aus
    uf_sql_exec aufgerufen worden ist
-   wird im Fehlerfall in die ausgegebene Fehlermeldung integriert
-   wenn, null, dann wird keine Fehlermeldung ausgegeben (wichtig für
    insert- update- Logik)
    -   al_rows
-   reference
-   liefert die Anzahl der bearbeiteten Rows
-   kann weggelassen werden
-   kann nicht beio jeder Signatur(Version) angegeben werden

##### Rückgabewert

-   boolean
-   Fehler ( false
-   sonst ( true

##### Beschreibung

-   schickt das SQL- Statement gegen die Datenbank
-   ACHTUNG: zwichen dem ersten uf_sql\_*- Aufruf des SQL- Statements
    und uf_sql_exec darf keinesfalls ein weiters SQL- Statement über
    uf_sql\_*- Funktionen begonnen werden - es darf immer nur ein
    Statement gleichzeitig bearbeitet werden. Wird bei einem SELECT-
    Statement das Ergebnis mittels uf_sql_ret_wert ausgelesen, darf kein
    weiteres SQL- Statement bearbeitet werden, bis der letzte Wert
    ausgelesen ist! ACHTUNG: Es dürfen auch keine Funktionen und Events
    aufgerufen werden, weil diese ja uf_sql\_\*- Funktionen enthalten
    könnten!
-   siehe uf_sql_select, uf_sql_update, uf_sql_delete und uf_sql_insert
-   bringt eine Fehlermeldung, wenn false returned wird

#### uf_sql_group

##### Argumente

-   as_group_by
-   z.B. "auf_nr, pos_nr"

##### Rückgabewert

##### Beschreibung

-   siehe uf_sql_select
-   fügt eine Group By- Clause in das Select- Statement ein

#### uf_sql_insert

##### Argumente

-   as_table
-   folgende 2 Argumente repräsentieren die erste Column des Inserts
-   weitere Columns können durch jeweils einen Aufruf von uf_sql_column
    hinzugefügt werden
-   siehe dort für die Bedeutung der Argumente
    -   as_column
    -   aa_wert

##### Rückgabewert

##### Beschreibung

-   Funktion leitet das Abschicken eines INSERT-Statements gegen die
    Datenbank ein
-   Folgender Ablauf: . uf_sql_insert . uf_sql_column - beliebig oft .
    uf_sql_exec

#### uf_sql_InsertSelect

##### Argumente

-   as_table
-   as_column
-   erste Column des Insert
-   weitere Columns können durch jeweils einen Aufruf von uf_sql_column
    hinzugefügt werden
    -   as_select
-   Select- Statement, welches über uf_sql_select erzeugt werden sollte

##### Rückgabewert

##### Beschreibung

-   Funktion leitet das Abschicken eines INSERT-Statements gegen die
    Datenbank ein
-   Folgender Ablauf: . Erzeugen eines Select- Statements mit
    uf_sql_select
-   statt uf_sql_exec wird allerdings uf_sql_str aufgerufen und der
    Returnwert wird als Parameter für uf_sql_insert verwendet .
    uf_sql_insert . uf_sql_column - beliebig oft . uf_sql_exec

#### uf_sql_join

##### Argumente

-   as_where_column1
-   as_where_column2

##### Rückgabewert

##### Beschreibung

-   siehe uf_sql_select
-   fügt eine Join- Bedingung in die Where- Clause des Select-
    Statements ein

#### uf_sql_order

##### Argumente

-   as_order_by
-   z.B. "auf_nr, pos_nr"

##### Rückgabewert

##### Beschreibung

-   siehe uf_sql_select
-   fügt eine Order By- Clause in das Select- Statement ein

#### uf_sql_ret_wert

##### Argumente

##### Rückgabewert

-   any

##### Beschreibung

-   siehe uf_sql_select
-   kann aufgerufen werden, wenn der Aufruf von uf_sql_exec genau eine
    gefundene Row gebracht hat
-   es bringt dann der erste Aufruf von uf_sql_ret_wert den Wert der
    ersten Column des Selects, der zweite Aufruf den Wert der zweiten
    Column und so weiter

#### uf_sql_select

##### Argumente

-   as_table
-   hier können auch mehrere durch Beistrich getrennte Tablenames stehen
-   dann sind die Join- Bedingungen über uf_sql_join zu definieren
    -   as_column
-   die erste Column der Select- Liste
-   hier kann 'distinct' vor dem Column- Namen stehen
-   weitere Columns können durch jeweils einen Aufruf von uf_sql_column
    hinzugefügt werden
-   folgende 3 Argumente repräsentieren den ersten Teil der Where-
    Bedingung:
-   weitere Bedingungen können mit jeweils einem Aufruf von uf_sql_where
    hinzugefügt werden
-   die genaue Beschreibung der Argumente steht bei uf_sql_where
    -   as_where_column
    -   as_operator
    -   aa_where_wert

##### Rückgabewert

##### Beschreibung

-   Funktion leitet das Abschicken eines SELECT-Statements gegen die
    Datenbank ein
-   Folgender Ablauf: . uf_sql_select . uf_sql_column - beliebig oft .
    uf_sql_join - beliebig oft . uf_sql_where - beliebig oft .
    uf_sql_group . uf_sql_order . uf_sql_exec . für jede Column des
    Select: uf_sql_ret_wert bzw. Werte aus dem übergebenen Datastore
    holen

#### uf_sql_str

##### Argumente

##### Rückgabewert

-   String
-   SQL- Statement

##### Beschreibung

-   Funktion wird statt uf_sql_exec aufgerufen und liefert das SQL-
    Statement, das bei uf_sql_exec gegen die Datenbank geschickt wird

#### uf_sql_update

##### Argumente

-   as_table
-   Folgende 2 Columns definieren den ersten Eintrag des SET- Liste
    (z.B. set eledigt_jn = 'j')
-   weitere Einträge können durch jeweils einen Aufruf von uf_sql_column
    hinzugefügt werden
    -   as_column
    -   aa_wert
-   folgende 3 Argumente repräsentieren den ersten Teil der Where-
    Bedingung:
-   weitere Bedingungen können mit jeweils einem Aufruf von uf_sql_where
    hinzugefügt werden
-   die genaue Beschreibung der Argumente steht bei uf_sql_where
    -   as_where_column
    -   as_operator
    -   aa_where_wert
    -   ab_AnyToLit
-   siehe uf_sql_column
-   kann weggelassen werden, ist dann true

##### Rückgabewert

##### Beschreibung

-   Funktion leitet das Abschicken eines UPDATE-Statements gegen die
    Datenbank ein
-   Folgender Ablauf: . uf_sql_update . uf_sql_column - beliebig oft .
    uf_sql_where - beliebig oft . uf_sql_exec

#### uf_sql_where

##### Argumente

-   as_vorher
-   kann weggelassen werden, dann wird "AND" angenommen
-   hier kann z.B. "AND NOT" stehen
-   hier kann z.B. "AND (" stehen
-   bei der nächsten Bedingung (also dem nächsten uf_sql_where- Aufruf)
    kann dann "OR" stehen
    -   as_where_column
    -   as_operator
    -   aa_where_wert
    -   as_nachher
-   kann weggelassen werden, dann wird "" angenommen
-   hier kann z.B. ")" stehen
-   über as_vorher und as_nachher können alle möglichen Verknüpfungen
    von Bedingungen realisiert werden
    -   ab_AnyToLit
-   kann weggelassen werden, ist dann true
-   siehe uf_sql_column
-   hiermit können u.a. Subselects als WHERE-Bedingung realisiert werden
    (siehe uf_sql_str)

##### Rückgabewert

##### Beschreibung

-   siehe uf_sql_select und uf_sql_update
-   fügt eine Bedingung in die Where- Clause des Select- Statements ein

#### uf_sql_str

##### Argumente

## keines

##### Rückgabewert

-   string

##### Beschreibung

-   siehe uf_sql_where
-   liefert SQL-Statement, welches vorher mit uf_sql_select,
    uf_sql_where, ... aufgebaut wurde in Form eines Strings
-   dieser kann dann als WHERE-Klausel der Funktion uf_sql_where
    übergeben werden
-   HINWEIS: für das Einklammern ist der Programmierer selbst
    verantwortlich

uf_SqlException2nl:

## `<uf_SqlException2nl>`{=html}

##### Argumente

-   auo_ae
-   Environment
    -   as_exception \> "pk" ( Primary- Key bereits vorhanden \> "ui" (
        Unique- Index- Verletzung \> "fk" ( Foreign-Key-Verletzung \>
        "rl" (Row is Locked
-   Funktioniort momentan nur bei SQL-Server und da warscheinlich noch
    nicht alle Varianten \> "\*" ( irgendeine
-   as_pattern darf nicht leer sein \> ...
-   bei Bedarf weitere
    -   as_pattern
-   ist ein Regular Expression
-   es wird geprüft, ob dieser im SQL- Fehlertext enthalten ist
-   kann leer sein
    -   as_meldung
-   Fehlermeldung - wird, wenn true geliefert wird, via wf_information
    ausgegeben
-   Logik wie bei wf_information
-   wenn leer oder null, erfolgt kein wf_information
    -   aa_par\[1-9\]

##### Rückgabewert

-   boolean
-   true wenn:
-   das letzte SQL- Statement war nicht erfolgreich
-   der letzte Sql- Fehler in der Tansaction entspricht as_exception und
    enthält as_pattern (ist as_pattern leer, gilt dies als immer
    enthalten)

##### Beschreibung

-   sollte folgendermaßen verwendet werden: if uf_SqlException ( ... )
    then entsprechende Fehlermeldung ausgeben elseif uf_SqlException (
    ... ) then entsprechende Fehlermeldung ausgeben elseif ...
    uf_SqlRows () / uf_SqlOk () .... then entsprechende Fehlermeldung
    ausgeben // nur in der SqlRows- Version elseif not ... .... then
    else // ok end if
-   siehe Embeded SQL- Statements

#### uf_SqlArgAfter

## `<uf_SqlArgAfter>`{=html}

##### Argumente

-   as_arg
-   by reference

##### Rückgabewert

-   (None)

##### Beschreibung

-   macht die Behandlung durch uf_SqlArgBefore wieder rückgängig

#### uf_SqlArgBefore

## `<uf_SqlArgBefore>`{=html}

##### Argumente

-   as_arg
-   by reference

##### Rückgabewert

-   (None)

##### Beschreibung

-   behandelt as_arg mit uf_arg
-   Anwendung bei embedded SQL- Statements . sqlca .uf_SqlArgBefore (
    ls_xy_kz ) . update ... where xy_kz = :ls_ky_kz using sqlca; . sqlca
    .uf_SqlArgAfter ( ls_xy_kz )

#### uf_SqlHaltIfCodeNot0

##### Argumente

-   auo_ae
-   as_context

##### Rückgabewert

-   (None)

##### Beschreibung

-   ACHTUNG: nur pfu_fun intern zu verwenden
-   siehe Überprüfung von embeded SQL- Statements
-   stoppt das Programm, wenn sqlcode nicht 0 ist (( also auch wenn
    nichts gefunden worden ist)
-   ist zu verwenden, wenn ein sql- Statement unbedingt erfolgreich sein
    muss
-   wurde für folgende Situation eingeführt:
-   embeded select
-   nur Aggregatsfunktion ( es wird immer genau eine Row geliefert, wenn
    kein Fehler auftritt

#### uf_SqlOk

## `<uf_SqlOk>`{=html}

##### Argumente

-   auo_ae
-   Environment
-   hier wird bei w_ApplObj / dw_ApplObj- Scripts iuo_ae übergeben
    -   as_context
-   Text, der die Stelle im Programm, an der fie Funktion aufgerufen
    worden ist, beschreibt
-   wird im Fehlerfall im Ramen der Fehlermeldung ausgegeben
-   wenn null, wird keine Fehlermeldung ausgegeben
-   null sollte nicht mehr verwendet werden
-   es sollte dann uf_SqlException2nl herangezogen werden
    -   al_MinRows
-   wenn \> 0, dann müssen mindetens so viele Rows vom SQL- Statement
    bearbeitet worden sein, dies macht nur bei update einen Sinn
-   kann weggelassen werden, default ist 0

##### Rückgabewert

-   boolean
-   true ( das letzte SQL- Statement wurde fehlerfrei abgearbeitet
-   false ( Fehler ist aufgetreten

##### Beschreibung

-   siehe Embeded SQL- Statements
-   Prüft, ob ein SQL- Statement fehlerfrei ausgführt worden ist und
    gibt eine Fehlermeldung (Error) aus, falls dies nicht der Fall ist.

#### uf_SqlRows

## `<uf_SqlRows>`{=html}

##### Argumente

-   die Funktion kann auch ohne Argumente aufgerufen werden
    -   auo_ae
-   Environment
-   hier wird bei w_ApplObj / dw_ApplObj- Scripts iuo_ae übergeben
    -   as_context
-   Text, der die Stelle im Programm, an der fie Funktion aufgerufen
    worden ist, beschreibt
-   wird im Fehlerfall im Ramen der Fehlermeldung ausgegeben
-   wenn null, wird keine Fehlermeldung ausgegeben
-   null sollte nicht mehr verwendet werden
-   es sollte dann uf_SqlException2nl herangezogen werden
    -   ab_halt
-   wenn true, wird im Fehlerfall Halt- Funktion ausgeführt
-   ACHTUNG: dieses Argument darf nicht verwendet werden und ist nur
    pfu_fun- intern erlaubt

##### Rückgabewert

-   long
-   Bei Fehler -1, sonst die Anzahl der im letzten SQL- Statement
    verarbeiteten Rows

##### Beschreibung

-   siehe Embeded SQL- Statements
-   Prüft, ob ein SQL- Statement fehlerfrei ausgführt worden ist und
    gibt eine Fehlermeldung (Error) aus, falls dies nicht der Fall ist.
-   siehe Rückgabewert

## Variable

## ib_IfxNoLogging

-   wird nur für Informix- Datenbanken ausgewertet
-   muß vor dem uf_connect auf true gesetzt werden, wenn die Datenbank
    kein Logging (=keine Transactions) hat

## is_db_kz

-   Darf nicht verändert werden!
-   wird durch uf_init belegt
-   Der Anfang von is_db_kz gibt den Datenbanktyp an: "ifxon" Informix
    Online "ifxse" Informix Standard Engine "mssql" Microsoft SQL-
    Server "ora" Oracle
-   Anschließend an den oben beschriebenen Datenbanktyp können noch
    Versionsinformationen folgen, was allerdings derzeit noch nicht der
    Fall ist.
-   weitere Datenbanktypen müssen erst implementiert werden!

## is_dsn

-   der bei uf_connect() bzw. uf_init() übergebene Parameter für as_dsn
-   darf nicht verändert werden
-   kann dazu verwendet werden, eine neue DB- Conection mit den selben
    Parametern wie eine bestehende zu erzeugen V

## is_pwd

-   sinngemäß wie is_dsn

## is_uid

-   sinngemäß wie is_dsn

## SqlNRows

-   Anzahl der Rows, die beim letzten SQL- Statement bearbeitet worden
    sind.
-   Kann nicht verändert werden!

## w_anmeldung

-   abgeleitet von w_ApplEnv
-   muss für die Applikation übersteuert werden

## Events

## AfterAnmeld

##### Argumente

-   ab_applstart
-   ist true, wenn das Event das Erste Mal seit Applikatinsstart
    aufgerufen wird

##### Rückgabewert

-   (None)

## Ableitung

-   muss überschrieben werden

##### Beschreibung

-   Hier können Aktionen durchgeführt werden, die nach einer
    erfolgreichen Anmeldung passieren sollen. z.B. Start eines Windows,
    dass nicht über das Menü gesteuert werden kann.

## DefDddwDwos

##### Argumente

-   as_mfa1_nr_dwo
-   referenze
-   das DWO für das DDDW für mfa1_nr
-   leer bedeutet, dass mfa1_nr nicht zur Anwendung kommt
    -   as_mfa2_nr_dwo
-   analog zu as_mfa1_nr_dwo, folgende Abweichungen:
-   DWO muss ein Retrievelargument für mfa1_nr haben
    -   as_mfa3_nr_dwo
-   as_mfa1_nr_dwo, folgende Abweichungen:
-   DWO muss ein Retrievelargument für mfa1_nr und eines für mfa2_nr
    haben

##### Rückgabewert

-   (None)

## Ableitung

-   muss überschrieben werden

##### Beschreibung

-   hier werden der pfu_fun die oben beschriebenen DWOs bekanntgegeben

## w_Appl, w_ApplMdi

## Events

## InitOsEnv

##### Argumente

##### Rückgabewert

-   (None)

## Ableitung

-   darf überschrieben werden
-   darf erweitert werden

##### Beschreibung

-   nur beim Einrichten der Applikation verwendbar
-   hier werden User und Hostname belegt
-   siehe Script

## OnOpenAppl

##### Argumente

##### Rückgabewert

-   (None)

## Ableitung

-   Ancestor- Script muss aufgerufen werden

##### Beschreibung

-   derzeit ist nur das Setzen von ib_UseNavigation hier vogesehen -
    dies nuss vor dem Ancestor- Aufruf erfolgen

### Functions

## wf_GetPar

##### Argumente

-   as_ParName
-   Name des Parameters

##### Rückgabewert

-   string
-   Parameterwert

##### Beschreibung

-   Liest einen Kommandozeilenparameter aus
-   Beim Starten der Applikation kann ein Kommandozeilenparameterstring
    mitgegeben werden. Dieser hat folgende Syntax: \[ ParName "='"
    ParWert "'" \[ " " ... \] \] z.B.: JobDsn='wawi' WawiDsn='wawitest'

## Variables

## ib_UseNavigation

-   ACHTUNG: erst ab Release2013
-   kann im OnOpenAppl- Script auf true gestzt werden - dann wird die
    Applikation mit den Features des Release 2013 betrieben -- derzeit
    wird bei true folgendes bewirkt
    -   Navigation- Window
    -   Information- Window
    -   kein "rotes" Workflow- Window
    -   mehr horizontaler Platz für die Toolbar - noch klären, ob wir
        das davon abhängig machen - derzeit nicht
    -   Feld- Border ist lowered - noch klären, ob wir das davon
        abhängig machen - derzeit nicht
    -   noch einbauen, dass die neu eingeführten manuellen- Workflows
        nur möglich sind, wenn ib_Navigation true ist
-   ACHTUNG: die Variable wird ggf. noch umgetauft bzw. auf mehrere
    Teilaspekte aufgesplittet

## w_ApplObj

## Events

## AcceptHotKey

##### Argumente

-   siehe wf_DefineHotKey V

##### Rückgabewert

-   boolean

## Ableitung

-   darf überschrieben werden
-   darf erweitert werden

##### Beschreibung

-   siehe wf_DefineHotKey

## AfterColSearchKeySet

##### Argumente

-   adw_ColSearch
-   das DW, von dem aus ColSearch aufgerufen worden ist
    -   aa_arg
-   Any- Array
-   bezüglich Inhalt siehe ColSearchArg

##### Rückgabewert

-   (None)

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   wird aufgerufen, nachdem vom ColSearch- Mechanismus (siehe
    uf_DefineColSearch) im aufrufenden DW der Key des AEOs gesetzt
    worden ist
-   hier kann z.B., wenn im ColSearch- Feld ein Mengen- EAN- eingegeben
    worden ist, die Menge im aufrufenden DW gesetzt werden

## AfterCommand

##### Argumente

-   ac_OpenWake
-   'o' ( Event wurde vom "echten" open ausgelöst
-   'w' ( Event wurde von "wake" ausgelöst (siehe wf_open)

##### Rückgabewert

-   (None)

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   Hier können nach dem Ausführen des Environment- Kommandos Aktionen
    durchgeführt werden.
-   Das Event wird allerdings auch aufgerufen, wenn es kein Kommando
    gibt
-   Das Event wird nicht aufgerufen, wenn BeforeCommand false liefert
-   wird sowohl beim erstmaligen Öffnen des Windows als auch beim
    Aufwecken dess Windows aufgerufen

## AfterDelete

##### Argumente

##### Rückgabewert

-   boolean
-   false, wenn Löschen abgebrochen und rückgängig gemacht werden soll
    (rollbackall), sonst true

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   siehe wf_DeleteAll
-   ACHTUNG: Wenn ein DW im Zustand "r" (( zu retrieven) ist, kann der
    retrieve nicht mehr erfolgen, weil ja die Daten in der DB nicht mehr
    vorhanden sind. Nachdem man davon ausgehen muß, daß dies der Fall
    ist, muß man im BeforeDelete- Event den Retrieve auslösen, wenn man
    im AfterDelete z.B. mit uf_GetItem auf das DW zugreifen will. Dies
    kann durch uf_GetItem bzw. uf_RowCount erfolgen.

## AfterDeleteOk

##### Argumente

-   ab_RollbackAll
-   by reference
-   wird Argument mit true belegt:
-   werden alle Änderungen seit dem Retrieve oder dem letzten Speichern
    vom Menü aus in den DWs und in der DB rückgängig gemacht, wenn
    löschen aus dem Menü aufgerufen wurde
-   liefert wf_DeleteAll() false

##### Rückgabewert

-   (None)

## Ableitung

-   darf überschrieben werden
-   darf erweitert werden

##### Beschreibung

-   siehe wf_DeleteAll
-   Hier is das Window bereits wieder im Status Display bzw. empty
-   Hier sind nur Aktionen sinnvoll, von welchen man annimmt, daß sie
    erfolgreich sind
-   Hier können auch Aufrufe von z.B. dw_ApplObj.uf_ChangeItem und
    wf_Save erfolgen

## AfterMenuCancel

-   noch nicht vollständig vorhanden

##### Argumente

-   ab_status
-   Status, siehe dw_applobj.uf_status
    -   adw_canceled
-   das Master- DW des Verbunds, dessen Änderungen verworfen worden sind
    -   ab_PasingAo
-   Das System ist beim Paste des AOs
    -   ab_ResumePasteAo
-   Referenz- Parameter
-   wird nur ausgewertet, wenn ab_PastingAo = true
-   ist mit true initialisiert
-   wenn das Argument auf falsegesetzt wird, wird das Fortsetzen des
    Paste- AO auf keinen Fall durchgeführt

##### Rückgabewert

-   (None)

## Ableitung

-   darf überschrieben werden
-   darf erweitert werden

##### Beschreibung

-   wird nach dem Cancel aus dem Menü aufgerufen bevor ggf. das
    Fortsetzen des Paste- AO erfolgt

## AfterMenuSave

##### Argumente

-   ab_status
-   Status, siehe dw_applobj.uf_status
    -   adw_saved
-   das Master- DW des Verbunds, dessen Änderungen gespeichert worden
    sind
    -   ab_PasingAo
-   Das System ist beim Paste des AOs
    -   ab_ResumePasteAo
-   Referenz- Parameter
-   wird nur ausgewertet, wenn ab_PastingAo = true
-   ist mit true initialisiert
-   wenn das Argument auf falsegesetzt wird, wird das Fortsetzen des
    Paste- AO auf keinen Fall durchgeführt

##### Rückgabewert

-   (None)

## Ableitung

-   darf überschrieben werden
-   darf erweitert werden

##### Beschreibung

-   wird nach dem Save aus dem Menü aufgerufen bevor ggf. das Fortsetzen
    des Paste- AO erfolgt
-   die Transaktion ist bereits commited

## AfterMenuSaveFailed

##### Argumente

-   ab_status
-   Status, siehe dw_applobj.uf_status
    -   adw_saved
-   das Master- DW des Verbunds, dessen Änderungen gespeichert worden
    sind
    -   ab_PasingAo
-   Das System ist beim Paste des AOs

##### Rückgabewert

-   (None)

## Ableitung

-   darf überschrieben werden
-   darf erweitert werden

##### Beschreibung

-   wird nach dem Save aus dem Menü aufgerufen, wenn das eigentliche
    Save misslungen ist
-   für die Transaktion ist bereits rollback durchgeführt worden

## BeforeClose

##### Argumente

##### Rückgabewert

-   boolean
-   true ( das Schließen bzw. das Unsichtbarwerden des Windows soll
    fortgesetzt werden
-   false ( Das window wird nicht geschlossen bzw. unsichtbar gemacht

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   Hier können Aktionen, welche vor dem Schließen bzw. Unsichtbarmachen
    des Windows erfolgen müssen aufgerufen werden.
-   Hier kann verhindert werden, daß das Window geschlossen bzw.
    unsichtbar gemacht wird.
-   ACHTUNG:
-   das Schließen von Child- Windows ist bereits erfolgt
-   es darf also kein Close auf ein Child- Window durchgeführt werden,
    weil dieses ja bereits geclosed ist
-   es gibt allerdings auch BeforeCloseChilds
-   es besteht folgende Problematik: . Paket schließt resourcen . Paket
    returned true . Indiv ruft Paket auf und returned dann false . close
    wird abgebrochen . Paket hat seine gecloseten Resourcen nicht mehr

## BeforeCloseChilds

##### Argumente

##### Rückgabewert

-   boolean
-   true ( das Schließen bzw. das Unsichtbarwerden des Windows soll
    fortgesetzt werden
-   false ( Das window wird nicht geschlossen bzw. unsichtbar gemacht

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   Hier können Aktionen, welche beim Schließen des Windows vor dem
    Schließen bzw. Unsichtbarmachen der Child- Windows erfolgen müssen,
    aufgerufen werden.
-   Hier kann verhindert werden, daß das Window geschlossen bzw.
    unsichtbar gemacht wird.

## BeforeCommand

##### Argumente

-   ac_OpenWake
-   'o' ( Event wurde vom "echten" open ausgelöst
-   'w' ( Event wurde von "wake" ausgelöst (siehe wf_open)

##### Rückgabewert

-   boolean
-   true ( Das Environment- Kommando (siehe Begriffe - Kommandostring
    des Environments) soll ausgeführt werden
-   false ( Das Environment- Kommando soll nicht ausgeführt werden

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   Hier kann verhindert werden, daß das Environment- Kommando (z.B.
    'open') ausgeführt wird.
-   Hier können vor dem Ausführen des Environment- Kommandos Aktionen
    durchgeführt werden.
-   Wird hier nichts gemacht und false returned, ist das Ergebnis so,
    als wäre das Window ohne Kommando aufgerufen worden.
-   wird sowohl beim erstmaligen Öffnen des Windows als auch beim
    Aufwecken dess Windows aufgerufen
-   Das Window ist komplett initialisiert ( Initialize ist bereits
    erfolgt
-   Hier sollten Instance- Variable zurückgesetzt werden, falls dies
    nicht sofort nach deren Verwendung geschieht
-   siehe auch ib_ToClose
-   siehe auch AfterCommand

## BeforeDelete

##### Argumente

##### Rückgabewert

-   boolean
-   true, wenn löschen möglich sein soll, sonst false

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   siehe wf_DeleteAll

## BeforeMenuDelete

##### Argumente

##### Rückgabewert

-   boolean
-   false -\>Delete wird nicht durchgeführt

## Ableitung

-   darf überschrieben werden

##### Beschreibung

-   wird vor dem Delete aus dem Menü aufgerufen
-   das System ist noch nicht in der Transaction
-   es dürfen keine Datenbankändernden Statements durchgeführt werden!!!
-   hier darf im Gegensatz zum Event BeforeDelete noch
    Benutzerinteraktion erfolgen

## BeforeMenuSave

##### Argumente

-   ac_status
-   Status, siehe dw_applobj.uf_status
    -   adw_saved
-   das Master- DW des Verbunds, dessen Änderungen gespeichert worden
    sind
    -   ab_PasingAo
-   Das System ist beim Paste des AOs

##### Rückgabewert

-   boolean
-   false -\> Save wird nicht durchgeführt

## Ableitung

-   darf überschrieben werden

##### Beschreibung

-   wird vor dem Save aus dem Menü aufgerufen
-   das System ist noch nicht in der Transaction
-   das zuletzt vom Anwender bearbeitete Feld ist bereits übernommen
-   es dürfen keine Datenbankändernden Statements durchgeführt werden!!!
-   hier darf im Gegensatz zu den Events dw_ApplObj.BeforeUpdate und
    BeforeUpdateDetail noch Benutzerinteraktion erfolgen

## BeforeOnSetPresentation

##### Argumente

##### Rückgabewert

-   boolean

## Ableitung

-   darf überschrieben werden

##### Beschreibung

-   wird vom OnSetPresentation aufgerufen
-   kann verwendet werden um individuell etwas steuern zu können während
    dem Presentation

## BeforeSetSelectFinish

##### Argumente

-   ac_wo
-   'a' ( Event wird vom Auswählen- Zeig von wf_AcceptQuery aufgerufen
-   'b' ( Event wird von wf_besorgs aufgerufen
-   'c' ( Event wird vom ColSearch- Zeig von wf_AcceptQuery aufgerufen
    -   ai_Select
-   ist bei 'a' und 'c' die Nummer des Durchlaufs in wf_AcceptQuery
-   ist bei ac_wo = 'b' fix 1 und es gibt genau einen Durchlauf
    -   ab_letztSelect
-   ist beim letzten Select (= beim letzten Durchlauf) true, sonst false
    -   auo_ParList
-   siehe wf_AcceptQuery
-   ist bei ac_wo = 'b' nicht gesetzt (ACHTUNG auch iuo_ParList darf in
    diesem Fall verwendet werden!) (Es kann in diesem Fall allerdings
    auf iuo_BesorgsParList zugegriffen werden)
    -   aa_arg\[\]
-   Any- Array
-   nur bei ac_wo='c' befüllt
-   bezüglich Inhalt siehe ColSearchArg

##### Rückgabewert

-   (None)

## Ableitung

-   darf überschrieben werden
-   darf erweitert werden

##### Beschreibung

-   siehe wf_AcceptQuery
-   Hier kann das Teil- Select- Statement des List- DWs nochmals
    verändert werden, nachdem die Suchbedingungen von auo_ParList durch
    das System eingesetzt worden sind (ACHTUNG es gibt ggf. kein "1 = 1"
    mehr!!!)
-   Dazu gibt es folgende Möglichkeiten:
    -   idw_list.uf_SetSelectSubst()
    -   idw_list.uf_CountInSelect()
-   ACHTUNG: Literals im Select- Statement müssen via
    itr\_.uf_AnyToLiteral eingebracht werden!
-   idw_list ist zum Zeitpunkt des Events leer

Siehe auch - Event BeforeSetSelectStart

## BeforeSetSelectStart

##### Argumente

-   ac_wo
-   'a' ( Event wird vom Auswählen- Zeig von wf_AcceptQuery aufgerufen
-   'b' ( Event wird von wf_besorgs aufgerufen
-   'c' ( Event wird vom ColSearch- Zeig von wf_AcceptQuery aufgerufen
    -   ai_Select
-   ist bei 'a' und 'c' die Nummer des Durchlaufs in wf_AcceptQuery
-   ist bei ac_wo = 'b' fix 1 und es gibt genau einen Durchlauf
    -   ab_letztSelect
-   ist beim letzten Select (= beim letzten Durchlauf) true, sonst false
    -   auo_ParList
-   siehe wf_AcceptQuery
-   ist bei ac_wo = 'b' nicht gesetzt (ACHTUNG auch iuo_ParList darf in
    diesem Fall verwendet werden!) (Es kann in diesem Fall allerdings
    auf iuo_BesorgsParList zugegriffen werden)
    -   aa_arg\[\]
-   Any- Array
-   nur bei ac_wo='c' befüllt
-   bezüglich Inhalt siehe ColSearchArg

##### Rückgabewert

-   boolean
-   false ( Query wird abgebrochen, wenn ai_Select = 1

## Ableitung

-   darf überschrieben werden
-   darf erweitert werden

##### Beschreibung

-   Hier können die in auo_ParList vorhandenen Parameter ergänzt /
    verändert werden
-   Hier kann Query abgebrochen werden - allerdings nur bei ai_Select =
    1
-   ACHTUNG: idw_list ist ggf. nicht leer und es kann, wenn Aktivitäten
    mit idw_list durchgeführt werden, ein Zeilenwechsel ausgelöst
    werden, was zu unerwünschten Ergebnissen führen kann. Im Event
    BeforeSetSelectFinish ist idw_list leer.

Siehe auch - Event BeforeSetSelectFinish

## BeforeWinmodus

##### Argumente

-   as_WinmodusKz
-   winmodus_kz lt. Tabelle pfu_winmodus

##### Rückgabewert

-   boolean
-   false ( es wird nicht in den entsprechenden Winmodus gewechselt

## Ableitung

-   darf überschrieben werden

##### Beschreibung

-   Event wird aufgerufen, wenn sich der Winmodus ändert

Siehe auch - wf_SetWinmodus

## CancelOrSaveBeforeClose

##### Argumente

-   ac_status
-   'n' oder 'u' - siehe wf_status

##### Rückgabewert

-   Boolean

## Ableitung

-   darf überschrieben werden
-   kann nicht erweitert werden

##### Beschreibung

-   Wird aufgerufen, wenn Window geschlossen wird, und nicht geschlossen
    werden kann, weil der Status New oder Update ist
-   hier kann Cancel oder Save durchgeführt werden (vielleicht vorher
    ein wf_yes ? - aber Achtung auf transaction)
-   wird false retouniert, bleibt das Fenster offen - Um eine
    entsprechende Fehlermeldung muss man sich selbst kümmern, damit
    diese ausgegeben wird.
-   wenn danach der Status immer noch New oder Update ist, kann nicht
    geschlosen werden und es kommt der Hinweis, dass das Fenster vorher
    gespeichert oder verworfen werden muss und der Close wird nicht
    durchgeführt.

## ClassnameIdwNeu

##### Argumente

##### Rückgabewert

-   String

## Ableitung

-   darf überschrieben werden

##### Beschreibung

-   Wird aufgerufen, wenn der Name für idw_neu ermittelt wird.
-   ist zu übersteuern wenn von einem Window abgeleitet wird, welches
    bereits ein idw_neu besitzt.

## CleanUp

##### Argumente

##### Rückgabewert

-   (None)

## Ableitung

-   darf überschrieben werden
-   darf erweitert werden

##### Beschreibung

-   Wird aufgerufen, wenn Window wirklich geschlossen wird, nicht wenn
    es in den Zustand sleeping versetzt wird.
-   Hier werden Objekte, welche im Initialize- Event- Script erzeugt
    werden vernichtet (destroy).

## ColSearchAnzSelect

##### Argumente

-   aa_arg\[\]
-   Any- Array
-   Parameter lt. Windowaufruf
-   nur bei ac_wo='c' befüllt
-   hat pro AOT eine vorgegebene Anzahl von Elementen
-   im ersten Element steht normalerweise der Eingabestring des
    auslösenden Feldes

##### Rückgabewert

-   integer
-   Anzahl der durch Union verbundenen Selects (bei 1 natürlich kein
    Union)
-   muss \>= 1 sein
-   das Ancestor- Script liefert 1

## Ableitung

-   darf überschrieben werden

##### Beschreibung

-   siehe dw_ApplObj.uf_DefineColSearch

## CommandSearch

##### Argumente

-   ab_colsearch
-   li_aeo
-   ls_preafixidname

##### Rückgabewert

-   string
-   retouniert den neuen CommandString

## Ableitung

-   darf überschrieben werden
-   Super-Aufruf des Event muss passieren

##### Beschreibung

Hier kann man den CommandString beim Suchen (Str+F) anpassen und im
BeforeCommand auswerten.

## CommitAll

##### Argumente

##### Rückgabewert

-   (None)

## Ableitung

-   darf überschrieben werden
-   darf erweitert werden

##### Beschreibung

-   Im Standardeventscript erflogt Commit auf die Transaction von
    idw_neu
-   Werden im Zuge von Neu/Ändern/Delete Datenbankupdates über andere
    Transactions durchgeführt, müssen diese Transactions hier Committed
    werden.

## DefineResize

##### Argumente

##### Rückgabewert

-   (None)

## Ableitung

-   darf überschrieben werden - Achtung: im Ancestor wird definiert,
    dass idw_list resized wird
-   darf erweitert werden

##### Beschreibung

-   Hier kann definiert werden, dass ein Control seine Größe und
    Position verändert, wenn das Window in der Größe geändert wird
-   dies erfolgt durch Aufruf der Funktion wf_DefineCtrlResize
-   wird im MDE- Modus nicht aufgerufen

## DeleteIsPossible

##### Argumente

-   ac_AufrufVon
-   gibt an, von wo aus neue Zeile angelgt würde "m" ( "Löschen" im Menü
    "s" ( von einem Script des Applikationsprogrammierers aus

##### Rückgabewert

-   boolean
-   true, wenn löschen möglich sein soll, sonst false

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   Dient zur Entscheidung, ob der Menüpunkt löschen aktiviert ist.
-   Es darf auf kein anderes DW als auf idw_list zugegriffen werden!!
    Sonst wird beim Bewegen im List- DW retrieve auf das zugegriffene DW
    durchgeführt ( Performanceprobleme
-   -\> Es dürfen keine Änderungen in irgendwelchen DWs durchgeführt
    werden!!!
-   Es dürfen keine Bildchirmausgaben erfolgen!!
-   Siehe auch Event UpdateIsPossible, NewIsPossible, dw_ApplObj.event
    Darf\*

## DwButtonClicked

##### Argumente

-   adw_ao
-   as_ButtonApplName

##### Rückgabewert

-   (None)

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   siehe wf_AddDwButtonAppl

## DwFocusList

##### Argumente

##### Rückgabewert

-   dw_ApplObj
-   das DW, welches, wenn standardmäßig idw_list den Focus erhalten
    würde, den Focus erhalten soll

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   Kommt z.B. zur Anwendung, wenn nach "NeueAuswahl" auch dann auf
    idw_neu gesprungen soll, wenn mehrere Rows in der Liste sind
-   wird dynamisch ausgewertet

## DwFocusNeu

##### Argumente

##### Rückgabewert

-   dw_ApplObj
-   das DW, welches, wenn standardmäßig idw_neu den Focus erhalten
    würde, den Focus erhalten soll

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   Kommt z.B. zur Anwendung, wenn beim Neu- Zweig nicht idw_neu sondern
    ein anderes DW bearbeitet werden soll.
-   wird dynamisch ausgewertet

## DwPositionMde

##### Argumente

##### Rückgabewert

-   dw_ApplObj
-   das DW, welches für die Positionierung im herangezogen wird

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   siehe Rückgabewert

## DwStatMenuEnabled

##### Argumente

-   ac_status
-   Status des Windows ('e', 'd', 'n', 'u')
    -   ab_ListAkt
-   true, wenn idw_list das akruelle DW ist
-   ACHTUNG: ist ab_ListAkt = true, sollte nicht mittels uf_GetItem auf
    ein anderes DW als auf idw_list zugegriffen werden, weil dieses
    sonst retrieved wird, und dadurch beim Zeilenwechsel eine unnötige
    Wartezeit entsteht!!!
    -   as_DwClassname
-   Classname des aktuellen DWSs, falls ein solches vorhanden ist (siehe
    ac_status)
    -   am\_
-   Menü des Windows

##### Rückgabewert

-   (None)

## Ableitung

-   darf überschrieben werden
-   darf erweitert werden

##### Beschreibung

-   Hier können Menüpunkte und auch Buttons abhängig vom Zustand des
    Systems enabled werden. (bzw. visible/invisible gesetzt werden)
-   ACHTUNG: vom System werden alle Controls zunächst auf enabled
    gesetzt ( Controls, welche fix disabled sind, müssen hier fix auf
    disabled gesetzt werden. Eine Ausnahme ist ein Button mit dem Namen
    cb_hintergrund, dieser ist automatisch disabled!
-   ACHTUNG: hier dürfen keine anderen Controls als Buttons und
    Menüpunkte behandelt werden.
-   für Tabpages steht das Event DwStatTabEnabled zur Verfügung
-   für DWs stehen die Events DarfVisible und DarfEnable zur Verfügung
-   für DWO- Columns siehe Column- Properties
-   siehe Beispiel im Ancestorscript
-   ACHTUNG: wird mit uf_GetItem auf ein anderes DW als auf das aktuelle
    DW (as_DwClassname) zugegriffen, kann dies zu Performanceverlusten
    führen, weil ggf. das andere DW erst retrieved werden muß. ( nur
    Werte aus idw_list oder dem aktuellen DW verwenden!!!

## DwStatTabEnabled

##### Argumente

-   ac_status
-   Status des Windows ('e', 'd', 'n', 'u')

##### Rückgabewert

-   (None)

## Ableitung

-   darf überschrieben werden
-   darf erweitert werden

##### Beschreibung

-   Hier können Tabpages abhängig vom Zustand des Systems enabled
    werden.
-   ACHTUNG: vom System werden alle Tabpages zunächst auf enabled
    gesetzt ( Controls, welche fix disabled sind, müssen hier fix auf
    disabled gesetzt werden. Eine Ausnahme sind Custom- Tabpages wie
    z.B. die Henriks!
-   siehe Beispiel im Ancestorscript
-   ACHTUNG: wird mit uf_GetItem auf ein anderes DW als auf das aktuelle
    DW (as_DwClassname) zugegriffen, kann dies zu Performanceverlusten
    führen, weil ggf. das andere DW erst retrieved werden muß. ( nur
    Werte aus idw_list oder dem aktuellen DW verwenden!!!

## DynConnect, DynDisconnect

##### Argumente

##### Rückgabewert

-   boolean
-   Erfolg ist true

## Ableitung

-   darf überschrieben werden
-   darf erweitert werden

##### Beschreibung

-   Braucht ein Window eine Datenbankconnection, die nur bei Bedarf
    vorhanden sein soll, kann dies über den Aufruf von
    tr\_.uf_DynConnect im Event DynConnect und von tr\_.uf_DynDisconnect
    im Event DynDisconnect abgehandelt werden
-   DynConnect wird aufgerufen, wenn ein Window geöffnet oder geweckt
    wird
-   Dyn Disconnect wird aufgerufen, wenn ein Window geschlossen oder
    schlafen geschickt wird

## EnableCopyAo

##### Argumente

##### Rückgabewert

-   boolean

## Ableitung

-   darf überschrieben werden
-   darf erweitert werden

##### Beschreibung

-   Bestimmt, ob der Menüpunkt ApplObj Kopieren aktiv ist
-   siehe dw_ApplObj.event SollPaste

## EnablePasteObjects

##### Argumente

## string as_bildname by Refernce

## string as_outlookpfad by Reference

##### Rückgabewert

## Ableitung

-   darf überschrieben werden

##### Beschreibung

-   Returniert im Standard jeweils blank
-   Wird von wf_paste aufgerufen
-   Durch Belegung der Werte kann das Kopieren eines Bildes oder von
    Outlook Objekten aktiviert werden.
-   wf_copy legt das Verzchnis an, falls Daten zum Kopieren vorhanden
    sind und es das Verzeichnis noch nicht gibt (bei Bild wird der
    String bis zum letzten  verwendet).
-   Zum eigentlichen Auslesen der Daten aus der Zwischenablage werden
    PowerShell Scripts gestarte. Diese liegen lokal am Host im
    Verzeichnis lt. Paramert "PSScriptPath"

## HotKeyAppl

##### Argumente

-   siehe wf_DefineHotKey

##### Rückgabewert

-   boolean

## Ableitung

-   darf überschrieben werden
-   darf erweitert werden

##### Beschreibung

-   siehe wf_DefineHotKey

## Initialize

##### Argumente

##### Rückgabewert

-   (None)

## Ableitung

-   darf überschrieben werden
-   darf erweitert werden

##### Beschreibung

-   Wird aufgerufen, wenn Window wirklich geöffnet wird
-   Wird nicht aufgerufen, wenn es aus dem Zustand sleeping erweckt
    wird. Siehe dazu Event BeforeCommand
-   Hier können
    -   Instance- Variable initialisiert werden
    -   Objekte mittels create erzeugt werden
    -   DWO- Column- Properties gesetzt werden (ACHTUNG siehe dort - mit
        Vorsicht zu genießen)
-   Anmerkung zur Ausführungsreihenfolge:
-   Die Definition- Events der Datawindows erfolgen früher.
-   BeforeCommand erfolgt später

## ListRowFocusChangingInStatusNewOrUpdate

##### Argumente

-   ac_status
-   ab_ListEdited
-   true ( idw_list ist editiert worden
-   false ( nicht editiert worden
    -   ab_NotListEdited
-   true ( ein anderes DW als idw_list ist editiert worden
-   false ( nicht editiert worden

##### Rückgabewert

-   Boolean
-   true ( Zeilenwechsel in idw_list darf erfolgen
-   false ( darf nicht erfolgen

## Ableitung

-   darf überschrieben werden
-   darf erweitert werden

##### Beschreibung

-   wird aufgerufen, wenn der Status Neu oder Update ist und versucht
    wird, in idw_list die Row zu wechseln
-   führt standardmäßig save durch und liefert true, wenn ab_ListEdited
    = true und ab_NotListEdited = false, und liefert sonst false

## NewAfterInsertRow

##### Argumente

##### Rückgabewert

-   (None)

## Ableitung

-   darf überschrieben werden
-   darf erweitert werden

##### Beschreibung

-   Dient zum Anlegen von jeweils einer Row in DWs im Master- Detail-
    Verbund mittels uf_NewLine beim Neu- Zweig.
-   Für ein Monitor- DW darf keine Row angelegt werden, weil dies durch
    das System erfolgt
-   Darf nur verwendet werden, wenn im jeweiligen DW genau eine Row
    existieren muß.
-   Ist dann zu verwenden, wenn z.B. das Befüllen der Konstanten in
    idw_neu uf_ChangeItem in einem Detail- DW auslöst. Dann wäre es im
    default- Event von idw_neu zu spät, die Row im Detail- DW anzulegen.
-   Achtung: durch den oben genannten uf_NewLine erfolgt allerdings das
    default- Event des oben genannten Detail- DWs vor dem default- Event
    von idw_neu. Wenn also Columns belegt werden, deren Lookup von
    Columns abhängt, welche im Default von idw_neu belegt werden, ist
    der uf_ChangeItem nicht erfolgreich. Dies gilt auch für die
    standardmäßig im Default- Event ausgeführte Funktion uf_SetDefaults.
    Es ist also sicherer, im betroffenen Detail- DW das default- Event-
    Script zu übersteuern und dort nichts auszuführen (Script entält nur
    eine Kommentarzeile). Die uf_SetDefaults- Funktion und die manuellen
    Belegungen sind dann im default- script von idw_neu auszuführen.

## NewIsPossible

##### Argumente

-   ac_AufrufVon
-   gibt an, von wo aus neue Zeile angelgt würde "m" ( "neu" im Menü "s"
    ( von einem Script des Applikationsprogrammierers aus

##### Rückgabewert

-   boolean
-   true, wenn Neuanlage möglich sein soll, sonst false

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   Dient zur Entscheidung, ob der Menüpunkt Neu aktiviert ist.
-   siehe unbedingt Ancestor- Script!
-   Siehe auch Event UpdateIsPossible, NewIsPossible, dw_ApplObj.event
    Darf\*

## NoLookup

##### Argumente

-   as_AeoIdName
-   Präfix + AOT- Name, z.B. "ein_auf_pos"
    -   aa_key
-   bei obigem Bsp. der Wert von ein_auf_nr

##### Rückgabewert

-   boolean
-   true, wenn kein lookup erfolgen soll

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   hier kann bestimmt werden, daß für gewisse Key- Werte für ein AEO
    kein lookup erfolgt
-   wird vom System vor einem lookup aufgerufen, wenn bei
    cst_ApplEnv.uf_AddAotEo als aa_NoLookupValue gf_c("w") übergeben
    wird.
-   ACHTUNG!:
-   Bei einem AEO, dessen AOT keine eigene KeyColumn hat (wie z.B.
    ArtikelLager in Baustoff), wird ja der Lookup jeweils durch den
    Lookup jedes Key- AEOs dieses AOTs ausgelöst. (Also bei Artikel
    Lager wird der Lookup durch den Lookup von Firma, Filiale,
    Abteilung, Artikel, Lager und Kommission ausgelöst)
-   erfolgt jetzt für eines dieser AEOs aufgrund eines RETURN false in
    NoLookup kein Lookup wird auch das AEO ohne eigener Key- Column
    nicht gelookuped (bei Kommission -1 erfolgt kein Lookup ( es erfolgt
    auch kein Lookup für ArtikleLager)
-   Lösung: das AEO mit NoLookup=true muss doppelt vorhanden sein:
    einmal wegen seiner Funktion als Keybestandteil und einmal für sich
    selbst)

## Position (geerbt von w_ApplEnv)

##### Argumente

##### Rückgabewert

-   (None)

## Ableitung

-   darf überschrieben werden
-   darf erweitert werden

##### Beschreibung

-   wird beim ersten SetPresentation nach dem echten open und dem wake
    aufgerufen
-   Standardmäßig geschieht folgendes:
-   Prüfung, ob das Window auf 800\*600 paßt - Ist dies nicht der Fall,
    erfolgt Programmabbruch
-   Window Positionierung
-   Positionierung lt. den pfu_win_pos.koordinaten
-   Zentrieren des Windows (mittels wf_Center), wenn pfu_win_pos Eintrag
    fehlt, bzw das Window über den Seitenrand der Applikation
    hinausragen würde.
-   hier kann auch die Größe des Windows verändert werden - siehe dazu
    auch wf_SetMaximized
-   das Event kann sowohl vom letztlich abgeleiteten Window als auch von
    Windows, von denen abgeleitet wird (z.B. w_ApplObjTc), übersteuert
    werden

## RadioMenuClicked (geerbt von w_ApplEnv)

##### Argumente

-   as_MenuCheckedOld
-   Name des Menüpunktes, welcher bisher angehakt ist (z.B.
    "m_ListeForm1")
    -   as_MenuCheckedNew
-   Name des Menüpunktes, welcher dann angehakt ist (z.B.
    "m_ListeForm2")

##### Rückgabewert

-   boolean
-   false, wenn kein anderer Menüpunkt des Radiobutton- Menüpunkt-
    Komplexes angehakt werden darf

## Ableitung

-   darf überschrieben werden
-   darf erweitert werden

##### Beschreibung

-   wird aufgerufen, wenn ein anderer Menüpunkt eines Radiobutton-
    Menüpunkt- Komplexes angeklickt wird

Siehe auch - w_ApplObj.wf_InitRadioMenu - m_ApplObj.mf_RadioClicked

## ReturnOnColSearch

##### Argumente

##### Rückgabewert

-   (None)

## Ableitung

-   darf überschrieben werden
-   darf erweitert werden

##### Beschreibung

-   Wird aufgerufen, wenn das Window mittels ColSearch (= Komfortsuche)
    aufgerufen worden ist, und der Benutzer Return anwählt.
-   Kann überschrieben werden, wenn nicht die Standardaktivität
    durchgeführt werden soll
-   Das Event wird nur aufgerufen, wenn das Window mittels ColSearch
    aufgerufen worden ist oder beim wf_open (geerbt von w_ApplEnv)
    (siehe unbedingt dort!) der Kommandostring das Kommando "colsearch"
    enthält.
-   siehe Variables

## ReturnOnSearch

##### Argumente

##### Rückgabewert

-   (None)

## Ableitung

-   darf überschrieben werden
-   darf erweitert werden

##### Beschreibung

-   Wird aufgerufen, wenn das Window mittels Search (= Fernglas)
    aufgerufen worden ist, und der Benutzer Return anwählt.
-   Kann überschrieben werden, wenn nicht die Standardaktivität
    durchgeführt werden soll
-   Das Event wird nur aufgerufen, wenn das Window mittels Ctrl+F
    aufgerufen worden ist oder beim wf_open (geerbt von w_ApplEnv)
    (siehe unbedingt dort!) der Kommandostring das Kommando "search"
    enthält.
-   siehe Variables

## RollbackAll

##### Argumente

##### Rückgabewert

-   (None)

## Ableitung

-   darf überschrieben werden
-   darf erweitert werden

##### Beschreibung

-   Im Standardeventscript erflogt Rollback auf die Transaction von
    idw_neu
-   Werden im Zuge von Neu/Ändern/Delete Datenbankupdates über andere
    Transactions durchgeführt, müssen diese Transactions hier Rollbacked
    werden.

## Schlaefer

##### Argumente

##### Rückgabewert

-   boolean
-   liefert standadmäßig true
-   false ( window kann nicht "schlafen gehen" sprich bei Close
    versteckt werden

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

## SqlExport

##### Argumente

##### Rückgabewert

-   (None)

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   hier wird definiert, was und wie exportiert werden soll, nachdem der
    Anwender einen der Menüpunkte unter dem Menüpunkt "\# SQL erzeugen"
    aufgerufen hat
-   Durch den Menüpunktaufruf wird ein Import- Sql- Script aufgebaut:
-   es sollte sich auf die aktuelle Row in der DB- Tabelle des aktuellen
    AOs und ggf. auf zugehörige Rows in anderen Tabellen beziehen
-   der String befindet sich nach der Verarbeitung im Clippboard
-   es ist ausschließlich folgender Ablauf gestattet: . ein oder
    mehreremale Aufruf von wf_SqlExportTab . ein oder mehreremale Aufruf
    von wf_SqlExportWhere
-   ist das SqlExport- Script leer, erfolgt kein Export
-   nachdem das SqlExport- EventScript aufgerufen worden ist, wird an
    den erzeugten String noch der Rückgabewert des SqlExportAdd-
    Eventscripts angehängt und das Ergebnis ins Clippboard gestellt
-   Beispiel: siehe pfu_win.pbl: w_pfu_win

## SqlExportAdd

##### Argumente

##### Rückgabewert

-   string
-   siehe SqlExport
-   standardmäßig wird der Leerstring zurückgeliefert

## Ableitung

-   darf überschrieben werden

##### Beschreibung

-   siehe SqlExport

## SetTitle

##### Argumente

-   title

##### Rückgabewert

-   None

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   hier wird der Windowtitle gesetzt
-   allerdings gibt es seit A21049 aus Performancegründen (unglaublich
    aber wahr - siehe A21049) folgende Sauerei:
-   das Argument title wurde neu eingeführt (es entspricht absichtlich
    nicht der Namenskonvention)
-   es überlagert das Property Title des Windows - ACHTUNG: wenn jemand
    z.B. this.title verwendet, funktioniert das Ganze nicht mehr - dies
    sollte aber eher ein theoretisches Problem sein
-   window.title wird jetzt nur mehr gesetzt, wenn der Wert des
    Parameters title von window.title abweicht
-   siehe Ancestor- Script
-   kann/sollte z.B. übersteuert werden, wenn es zu einer logischen Row
    in idw_list mehrere Rows im DW gibt - folgende Möglichkeiten sind
    z.B. denkbar:
    -   es gibt eine Computet Column im DWO mit einer Kummulativen Summe
        über einen Wert, der nur einmal in einer Logischen Zeile 1 ist
-   getitem für die aktuelle Zeile ist die Nummer der aktuellen
    logischen Zeile
-   getitem für die letzte Zeile ist die Anzahl der logischen Zeilen
    -   wenn es immer gleich viele DW- Rows pro logischer Zeile gibt,
        muss einfach durch diese Anzahl dividiert werden ( z.B. 1, 2, 3
        -\> 1 / 4,5,6 -\> 2 ... int((row+2)/3) )

## SetMenuWindow

##### Argumente

-   ac_status
-   Status in dem sich das Window aktuell befindet
    -   ab_listakt
-   gibt an, ob das aktuelle DW die Liste ist

##### Rückgabewert

-   (None)

## Ableitung

-   darf überschrieben werden

##### Beschreibung

-   Event dient dazu den Menüpunkt "Window öffnen" zu übersteuern.
-   hier muss der Menüpunkt auf Visible und Enabled gesetzt werden,
    weiters kann der Text des Menüpunktes geändert werden.
-   dzt. wird das Kalender-Window in einem DateTime-Feld aufgerufen.

## ToggleMenuClicked (geerbt von w_ApplEnv)

##### Argumente

-   as_Menu
-   Name des Menüpunktes
    -   ab_checked
-   true, wenn Menüpunkt von nicht angehakt auf anghakt wechselt, sonst
    false

##### Rückgabewert

-   boolean
-   false, wenn Wechsel nicht erfolgen darf

## Ableitung

-   darf überschrieben werden
-   darf erweitert werden

##### Beschreibung

-   wird aufgerufen, wenn ein Toggle- Menüpunkt geklicked wird

Siehe auch - dw_ApplObj.wf_InitToggleMenu - m_ApplObj.mf_ToggleClicked

## UpdateIsPossible

##### Argumente

-   ac_AufrufVon
-   gibt an, von wo aus neue Zeile angelgt würde "m" ( Menüpunkt oder
    Usereingabe "s" ( von einem Script des Applikationsprogrammierers
    aus
-   ACHTUNG: beim Pasten eines DWs ist ac_AufrufVon immer = "m" - das
    ist zwar nicht ganz korrekt, es geht aber nicht anders (zumindest
    nicht leicht)
    -   adw_master
-   das Master- DW des Verbunds, das in den Update- Status kommen will

##### Rückgabewert

-   boolean
-   true, wenn irgendeine Änderung in einem DW möglich sein soll, sonst
    false

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   Dient zur Entscheidung, ob irgend ein DW in den Status 'u'=Update
    kommen kann.
-   Das Script wird auch von idw_list aus gestartet ( nur auf Felder von
    idw_list zugreifen. Performance!
-   Es dürfen keine Meldungen an den Benutzer erfolgen. Eine solche
    erfolgt über die Windows- Instance- Variable is_UpdateNotPossible.
-   Wird in is_UpdateNotPossible ein Text eingetragen, wird dieser in
    den Fehlerstring des aktuellen DWs gestellt. Dieser wird z.B.
    ausgegeben, wenn die Prüfung auf UpdateIsPossible durch eine
    Benutzereingabe hervorgerufen wurde.
-   ACHTUNG: der nach is_UpdateNotPossible gestellte Text muss in der
    Sprache der Anmeldung sein
-   Siehe auch Event NewIsPossible, dw_ApplObj.event Darf\*
-   ACHTUNG: beim Pasten eines DWs ist ac\_??????

## WinModusOnOpenWake

##### Argumente

##### Rückgabewert

-   string
-   Winmodus- Kennzeichen wie bei wf_SetWinmodus

## Ableitung

-   darf überschrieben werden
-   darf nicht erweitert werden

##### Beschreibung

-   vor dem Aufruf des Events BeforeCommand wird wf_SetWinmodus
    aufgerufen - als Wert für das Argument as_WinmodusKz wird der
    Returnwert von WinModusOnOpenWake herangezogen

## WfoAktion

##### Argumente

-   adc_wfo_snr

-   die Daten des WFOs können aufgrund des Argument- Werts mittels
    uf_GetData ausgelesen werden

    -   as_wfogen_cd

-   lt. pfu_wfogen.wfogen_cd

    -   as_wfoart_cd

-   lt. pfu_wfo.wfoart_cd lt. "auslösendes WFOs" (siehe DB- Doku)

    -   as_bea_applpers_cd

-   Sachbearbeiter lt. Anmeldung, welcher die Änderung am "auslösenden
    Wfo" (lt. DB- Doku) durchgeführt hat

    -   as_zustand_kz

-   Zustand auf den das "auslösende WFO" gesetzt wurde

-   siehe workflow_db.doc ( pfu_wfo.w_zustand_kz, \##
    pfu_wfo_applpers.wa_zustand_kz

    -   as_zustand_kz_alt

-   Zustand den das "auslösende WFO" zuvor eingenommen hatte

    -   as_aus_kz

-   siehe workflow_db.doc ( pfu_wfogen.aus_kz

    -   as_error

-   referenz

-   bei Fehler wird hier Fehlertext zurückgeliefert

##### Rückgabewert

-   Boolean
-   true (
-   die Row in pfu_wfo2gen wird gelöscht und der Job ist erfolgreich
-   false (
-   es wird vom System Rollback durchgeführt
-   der Eintrag, in pfu_wfo2gen bleibt erhalten und der Job ist
    "markiert" (siehe Beschreibung)

## Ableitung

-   darf überschrieben werden
-   darf erweitert werden

##### Beschreibung

-   Das Event wird aufgerufen, wenn sich ein WFO, dem ein AO zugeordnet
    ist ändert und dafür ein pfu_wfo2gen- Satz vorhanden ist.
-   dazu wird eine Row in pfu_wfo2gen angelegt und ein Batchjob, der
    diese verarbeitet, eingespoolt
-   zu Beginn des Events befindet sich die Applikation in einer
    Transaktion, diese wird abhängig vom Rückgabewert (siehe dort)
    beendet

### Functions

## classname

##### Argumente

##### Rückgabewert

-   string
-   Windowname
-   Achtung: Bei einer Abgeleiteten Applikation kann es Probleme geben.
    Bsp.:
-   w_kunde_duroton ist von w_kunde abgeleitet
-   in w_adr ist Abfrage, ob Parent- Window w_kunde ist
-   mit classname ergibt dies: if "w_kunde_duroton" = "w_kunde" und
    somit geht die Abfrage nicht auf
-   richtig ist: if gf_is ( lw_parent, "w_kunde" ) then
-   siehe cst_applEnv.uf_AddWindowMap

## wf_accept

##### Argumente

##### Rückgabewert

-   siehe dw_ApplObj.uf_accept

##### Beschreibung

-   ruft dw_ApplObj.uf_accept auf, wenn der Zustand des Windows "u" oder
    "n" ist, sonst wird sofort true geliefert

## wf_AcceptQuery

##### Argumente

##### Rückgabewert

-   (None)

##### Beschreibung

-   Darf nur aufgerufen werden, wenn zuvor wf_query aufgerufen worden
    ist und im Aufruf im Parameter as_command "noacceptquery" enthalten
    ist
-   sonst wird wf_AcceptQuery vom System aufgerufen: \> vom "Auswählen"-
    Button des Queryfensters
-   Der Anwender kann im Query- Fenster mehrere Sätze von Query-
    Bedingungen eingeben ("ZusAusw"- Button)
-   iuo_ParList ist dann das erste Objekt einer verketteten Liste von
    cst_ParList- Objekten (ein Objekt pro Satz)
-   dieser Zweig wird weiters mit Auswählen abgekürzt \> in Zusammenhang
    mit der ColumnSearch- Funktionalität ( dw_ApplObj.uf_DefineColSearch
-   dieser Zweig wird weiters mit ColSearch abgekürzt
-   Folgender Ablauf: (unabhängig davon, ob vom System oder von der
    Applikation aus aufgerufen!) . Aufruf event ColSearchAnzSelect - nur
    bei ColSearch . Schleife: \> Auswählen:
-   ein Durchlauf pro cst_ParList- Objekt in der verketteten Liste von
    cst_ParList- Objekten
-   normalerweise allerdings nur ein Objekt ( ein Durchlauf
-   mehrere Objekte gibt es, wenn der Anwender zusätzliche Sätze von
    Suchbedingungen erfasst hat
-   der auo_Parlist- Parameter bei den entsprechenden Events zeigt auf
    das aktuelle cst_ParList- Objekt \> ColSearch:
-   Anzahl Durchläufe lt. ColSearchAnzSelect- Event
-   der auo_Parlist- Parameter bei den entsprechenden Events zeigt
    jeweils auf ein cst_ParList- Objekt, in dem die nur die Konstanten
    vorhanden sind . Aufruf event BeforeSetSelectStart
-   hier sollten bei ColSearch die entsprechenden Parameter in
    auo_Parlist gehängt werden . Select initialisieren . auo_Parlist in
    den Select einarbeiten . Aufruf event BeforeSetSelectFinish .
    bearbeiteten Select zwischenspeichern . Alle zwischengespeicherten
    Select- Statements werden mittels union zu einem Select- Statement
    zusammengehängt . der Retrieve von idw_list wird durchgeführt

## wf_AddDwButtonAppl

##### Argumente

-   as_name
-   Name des logischen ApplikationsButtons
    -   as_txt
-   Text der auf dem DWO- Button angezeigt werden soll, wenn der DWO-
    Button dem logischen Button zugeordnet ist

##### Rückgabewert

-   (None)

##### Beschreibung

-   wurde für den MDE- Betrieb (MDE- Modus) eingeführt
-   folgende Konstellation:
-   in einenem oder mehreren DWs am Window gibt es jeweils einen oder
    mehrere Buttons (nachfolgend als DWO- Buttons bezeichnet)
-   abhängig vom Programmzustand können die Buttons ggf. eine andere
    Funktion haben (am MDE- Schirm herrscht Platzmangel)
-   ggf. haben mehrer Buttons auf unterschiedlichen DWs die gleiche
    Funktion
-   in diesem Zusammenhang wurden die logischen Applikationsbuttons
    eingeführt
-   Folgende Lösung:
-   pro window können beliebig viele Logische Applikationsbutons
    definiert werden
-   ein logischer Applikationsbutton
-   hat genau eine Funktion
-   ist primär nicht sichtbar
-   einem logischen Applikationsbutton können mehrere DWO- Buttons
    zugeordnet werden
-   die Zuordnung eines DWO- Buttons zu einem logischen
    Applikationsbutton
-   erfolgt mittels der Funktion uf_MapButtonAppl
-   bewirkt, dass, wenn der DWO- Button geklickt wird, das
    DwButtonClicked- Event des Windows "aufgeht" und der Name des
    logischen Applikationsbuttons u.a. als Argument übergeben wird
-   dass am DWO- Button der Text lt. as_txt angezeigt wird

## wf_aktualisieren

##### Argumente

##### Rückgabewert

-   boolean
-   true, wenn ok sonst false

##### Beschreibung

> Wenn aktuelles Master- DW im Zustand "\[un\]" - Für alle DWs des
> aktuellen Master- Detail- Verbunds alle Lookups durchführen Wenn
> aktuelles Master- DW im Zustand "\[dr\]" - Alle DWs des Windows (außer
> List) auf Zustand "r" setzen, und retrieven, falls sie am aktuellen
> TAB sind. Wenn aktuelles DW die Liste (idw_list) ist - die Liste wird
> mit dem gleichen Select nochmals retrieved

## wf_ApplPersWechsel

##### Argumente

##### Rückgabewert

-   (None)

##### Beschreibung

-   wenn pfu_usr.applperswechsel_jn='j', wird das Anmeldungsfenster
    aufgerufen
-   darf nicht innerhalb einer Transaction aufgerufen werden

## wf_ApplicationServerButNotMaster

##### Argumente

##### Beschreibung

-   nur im Zusammenhang mit dem Applicationserver relevant
-   liefert true, wenn iuo_ae. ib_ApplicationserverProxy = true und
    iuo_ae.iuo_ApplicationServerProxyDataContext. iw_AoDataContextMaster
    \<\> this ist

## wf_error (geerbt von w_ApplEnv)

##### Argumente

-   apo_wo
-   beliebiges Objekt, dessen Classname auch angezeigt wird
-   hier wird das Objekt angegeben, in dem der Fehler aufgetreten ist
-   kann weggelassen werden
-   das aktuelle Window sollte nicht übergeben werden
    -   as_wo
-   Position im Script
    -   as_ErrorText
-   Fehlermeldung

##### Beschreibung

-   gibt eine Fehlermeldung aus
-   diese wird nicht übersetzt
-   Die Meldung enthält den Windownamen
-   Sollte nur verwendet werden, wenn es sich um einen Sytem- /
    Programm- Fehler handelt. Bei falscher Benutzereingabe, bzw. der
    Auswahl nicht geeigneter Daten ist wf_information zu verwenden.
-   siehe wf_TrBegin, wf_BatchBegin

Siehe auch - dw_ApplObj.uf_error

## wf_BatchBegin

##### Argumente

-   die Argumente können weggelassen werden (dann aber alle) - Es wird
    dann ( true, false ) angenommen

    -   ab_DispMessages

-   true -\> während des Batch- Modus werden Meldungen (wf_information,
    ...) normal angezeigt

-   false -\> während des Batch- Modus werden Meldungen (wf_information,
    ...) nach ...`\PfundnerIinformationError`{=tex}\... geschrieben

    -   ab_WWorking

-   siehe cst_ApplEnv.uf_WorkStart

##### Rückgabewert

-   (None)

##### Beschreibung

-   Das System wird in den Batchmodus versetzt - das hat folgende
    Konsequenzen:
-   das System ist im "working"- Modus
-   DDDWs werden nicht retrieved -\> Performancegewinn (nach dem Ende
    des Batch- Modus werden alle notwendigen Dddws retrieved)
-   die Bildschirmdarstellung wird nicht aktuallisiert
-   neu geöffnete Windows werden nicht angezeigt
-   kein geposteter Check, ob Transaction beendet worden ist - siehe
    wf_TrBegin
-   ID- Dddws werden nicht abgehandelt
-   es darf keine Benutzereingabe erfolgen - wird geprüft
-   es gibt keine Berechtigungsprüfungen
-   ACHTUNG: im Batch- Modus darf kein Dw im Status Edit sein - es darf
    also kein nicht abgeschlossenes Feld geben. Dies ist ggf. mittels
    wf_accept bzw. dw_ApplObj.uf_accept zu bewerkstelligen.
-   der Batch- Modus kann mit wf_BatchEnd beendet werden - dann werden
    alle notwendigen im Batchmodus nicht durchgeführten Aktivitäten
    nachgeholt.

## wf_BatchEnd

##### Argumente

##### Rückgabewert

-   (None)

##### Beschreibung

-   siehe wf_BatchBegin

## wf_berechtigt

##### Argumente

-   as_funktional
-   lt. pfu_bertr.funktional
    -   aa_wert
-   readonly
-   kann weggelassen werden - dann:
-   es soll geprüft werden, ob der Anwender für die Funktionalität
    as_funktional berechtigt ist
-   pfu_bertr.funfilter_jn = 'n'
-   nur anzugeben, wenn für as_funktional pfu_bertr.funfilter_jn='j' -
    dann:
-   Wert für den geprüft werden soll, ob der Anwender für diesen Wert
    berechtigt ist
-   Bsp.:
-   as_funktional = "aufart"
-   aa_wert = "gut"
-   Funktion liefert true, wenn der Anwender eine Berechtigung für die
    Auftragsart "gut" hat

##### Rückgabewert

-   boolean
-   true, wenn Berechtigung vorhanden ist

## wf_BerechtigtIn

##### Argumente

-   as_funktional
-   lt. pfu_bertr.funktional
    -   atr\_
-   Transaktion für dessen Datenbanksyntax die in_clause erzeugt werden
    soll
-   kann weggelassen werden, dann wird eine in- Clause für einen DW-
    Find erzeugt
    -   as_column
-   readonly
-   Column- Name z.B. "aufart_cd"

##### Rückgabewert

-   String
-   in- Clause in der Syntax der Datenbank lt. atr\_ ( z.B. aufart_cd in
    ( 'n', 'bv' ) )
-   ist kein Wert gestattet, wird eine false- Expression geliefert
-   sind alle Werte gestattet, wird eine true- Expression geliefert

##### Beschreibung

-   erzeugt eine in- Clause mit allen Werten, für die die Funktion
    wf_berechtigt true liefert

## wf_berechtigung

##### Argumente

-   as_progteil
-   lt. pfu_bertr.funktional
    -   ab_Oeffnen
-   by reference, wird gesetzt
-   true, wenn die Berechtigung zum Öffnen vorhanden ist, sonst false
    -   ab_Aendern
-   by reference, wird gesetzt
-   liefert true, wenn die Berechtigung zum Ändern vorhanden ist, sonst
    false
-   ab_Oeffnen und ab_Aendern liefern immer den gleichen Wert!!!

##### Rückgabewert

-   (None)

##### Beschreibung

-   nur aus abwärtskompatibilitätsgründen vorhanden
-   nicht mehr verwenden!!!

## wf_besorgs

##### Argumente

-   as_wohins
-   wohin_string ";" wohin_string ...
-   siehe Beschreibung

##### Rückgabewert

-   long
-   0 ( AO weder in idw_list noch in der DB gefunden, bzw. es tritt eine
    Konstantenverletzung auf. \>0 ( Row in idw_list mit dem gesuchten AO

##### Beschreibung

-   Sorgt dafür, daß ein bestimmtes AO in idw_list vorhanden ist und
    liefert die dazugehörige Row.
-   Ablauf: . über w_ApplObj. iuo_BesorgsParList (siehe cst_ParList)
    werden über uf_AddPar() und uf_AddParWert() Query- Parameter
    definiert. . Aufruf von wf_besorgs() . wf_besorgs sucht in idw_list
    beginnend bei der ersten Row nach der entsprechenden Row.
-   die where- Bedingung dazu wird aus iuo_BesorgsParList erzeugt. Dabei
    kommen alle Parmeter mit einem wohin, welches in as_wohins enthalten
    ist zum Einsatz.
-   Wird eine Row gefunden, so wird diese zurückgeliefert. . wenn AO in
    idw_list nicht vorhanden ist, sucht wf_besorgs in der Datenbank.
-   der Where_string wird aus iuo_BesorgsParList aufgebaut.
-   Der Retrieve erfolgt aditiv. -\> Die gefundenen Rows (sollte
    eigentlich nur eine sein) stehen ganz zum Schluß.
-   es wird die letzte Row zurückgeliefert, wenn AO gefunden wurde .
    wf_besorgs führt abschließend einen Reset von iuo_BesorgsParList
    durch

## wf_Cancel

##### Argumente

##### Rückgabewert

-   (None)

##### Beschreibung

-   Verwirft alle ungespeicherten Änderungen des Master- Detail-
    Verbunds, welcher sich im Neu bzw. Ändern- Zweig befindet.
-   Darf nicht in einem Event- Script aufgerufen werden!
-   siehe auch wf_Reset

## wf_Center (geerbt von w_ApplEnv)

##### Argumente

##### Rückgabewert

-   (None)

##### Beschreibung

-   zentriert das Window

## wf_ChangeCtrlPosition (geerbt von w_ApplEnv)

##### Argumente

-   adro_ctrl
-   das Control, dessen Positon verändert werden soll
-   unterstützt werden dw_ApplObj und cb_ApplEnv
    -   as_x_kz
-   a ...Wert für x absolut setzen
-   r ... Wert für x relativ setzen
    -   al_x
-   neue x- Position des Controls innerhalb des Windows
    -   as_y_kz
-   a ...Wert für y absolut setzen
-   r ... Wert für y relativ setzen
    -   al_y
-   neue y- Position des Controls innerhalb des Windows
    -   as_width_kz
-   a ...Wert für width absolut setzen
-   r ... Wert für width relativ setzen
    -   al_width
-   neue Breite des Controls
    -   as_height_kz
-   a ...Wert für height absolut setzen
-   r ... Wert für height relativ setzen
    -   al_height
-   neue Breite des Controls

##### Rückgabewert

-   (None)

##### Beschreibung

-   ändert die Position bzw. die Größe von adro_ctrl
-   alle Längenangaben
-   sind in Powerbuilderunits (Im Windowpinsler sind auch alle Angaben
    in Powerbuilderunits)
-   beziehen sich auf die Originalgröße des Windows ( wenn das Window
    vom Anwender vergrößert worden ist, und das Control mitwächst bzw.
    sich mitverschiebt (wf_DefineCtrlResize), sind die tatsächlichen
    Längen entsprechend größer.
-   kann jederzeit aufgerufen werden (glaube ich zumindest)
-   die Änderungen gelten, bis das Window nach dem Pseudo-Close wieder
    aufgeweckt wird. Für das Initialize- Eventscript ist die Funtion
    wf_ChangeCtrlOriPosition geignet.
-   tut im MDE- Modus nichts (siehe uf_DefineMde ff)

## wf_ChangeCtrlOriPosition (geerbt von w_ApplEnv)

##### Argumente

-   adro_ctrl
-   das Control, dessen Positon verändert werden soll
-   unterstützt werden dw_ApplObj und cb_ApplEnv
    -   as_x_kz
-   a ...Wert für x absolut setzen
-   r ... Wert für x relativ setzen
    -   al_x
-   neue original x- Position des Controls innerhalb des Windows
    -   as_y_kz
-   a ...Wert für y absolut setzen
-   r ... Wert für y relativ setzen
    -   al_y
-   neue original y- Position des Controls innerhalb des Windows
    -   as_width_kz
-   a ...Wert für width absolut setzen
-   r ... Wert für width relativ setzen
    -   al_width
-   neue original Breite des Controls
    -   as_height_kz
-   a ...Wert für height absolut setzen
-   r ... Wert für height relativ setzen
    -   al_height
-   neue original Breite des Controls

##### Rückgabewert

-   (None)

##### Beschreibung

-   ändert die Original Position bzw. die Größe von adro_ctrl
-   der Funktionsaufruf wirkt sich ausschließlich beim Aufwecken nach
    einem vorausgegangenen Close aus
-   siehe auch wf_ChangeCtrlPosition
-   alle Längenangaben
-   sind in Powerbuilderunits (Im Windowpinsler sind auch alle Angaben
    in Powerbuilderunits)
-   beziehen sich auf die Originalgröße des Windows ( wenn das Window
    vom Anwender vergrößert worden ist, und das Control mitwächst bzw.
    sich mitverschiebt (wf_DefineCtrlResize), sind die tatsächlichen
    Längen entsprechend größer.
-   kann jederzeit aufgerufen werden (glaube ich zumindest), ist aber
    eigentlich nur für das Initialize- Eventscript sinnvoll
-   tut im MDE- Modus nichts (siehe uf_DefineMde ff)

## wf_CopyAo

##### Argumente

##### Rückgabewert

-   boolean
-   true, wenn erfolgreich kopiert

##### Beschreibung

-   kopiert gesamtes AO
-   siehe dw_ApplObj.event SollPaste

## wf_CreateOleObject

##### Argumente

-   as_FullyQualifiedClassname

##### Rückgabewert

-   OleObject

##### Beschreibung

-   OLE- Objekte können jetzt direkt aus einem w_ApplObj verwendet
    werden - siehe dazu in der pfu_fun in w_tcprs - w_tcprs, wf_GetField
-   ist eine Sackgasse -\> wird nicht weiter verwendet

## wf_CreatePfuJobDruck

##### Argumente

-   as_druckart_cd
-   ai_mfa1_nr
-   ai_mfa2_nr
-   ai_mfa3_nr
-   as_druck_nr
-   as_dokument_unc
-   das Dokument, das in die (TC-) Dokumentenverwaltung importiert
    werden soll
    -   as_da_orig_loe_jn
-   soll das Dokument lt. as_dokument_unc gelöscht werden
-   (da steht für Druckart)
    -   as_dokument_mc
-   optional, wenn weggelassen, wird null angenommen
-   wenn Null, dann wird dokument_mc folgendermaßen belegt:
-   pfu_druckart.druck_nr_bez + " " + pfu_job_druck.druck_nr

##### Rückgabewert

-   long
-   ok ( pfu_job_druck. job_druck_lfd_nr
-   nicht ok ( -1

##### Beschreibung

-   importiert ein Dokument in die PCS/TC- Dokumentenverwaltung - legt
    also eine neue pfu_job_druck- Row an
-   mit a17837 eingeführt

## wf_DefineCtrlResize

##### Argumente

-   adro_ctrl
-   das Control, dessen Größe und/oder Position geändert werden soll
    -   adc_DXFakt
-   die x- Position des Controls wird um "Breitenänderung des Windows"
    \* adc_DXFakt geändert
-   sollte 0 sein, wenn das Control ganz links ist
-   sollte die Summe aller adc_DWidthFakt der Controls, die links des
    aktuellen Controls sind, sein
    -   adc_DYFakt
-   die y- Position des Controls wird um "Höhenänderung des Windows" \*
    adc_DYFakt geändert
-   sollte 0 sein, wenn das Control ganz oben ist
-   sollte die Summe aller adc_DHeightFaktder Controls, die oberhalb des
    aktuellen Controls sind, sein
    -   adc_DWidthFakt
-   die Breite des Controls wird um "Breitenänderung des Windows" \*
    adc_DWidthFakt geändert
-   sollte 1 sein, wenn das Control die gesamte Windowbreite einnimmt
-   kann z.B. 0.5 sein, wenn der Breitenzuwachs des Windows auf 2
    nebeneinanderliegende Controls aufgeteilt werden soll
    -   adc_DHeightFakt
-   die Höhe des Controls wird um "Höhenänderung des Windows" \*
    adc_DHeightFakt geändert
-   sollte 1 sein, wenn das Control die gesamte Windowhöhe einnimmt
-   kann z.B. 0.5 sein, wenn der Höhenzuwachs des Windows auf 2
    übereinanderliegende Controls aufgeteilt werden soll

##### Rückgabewert

-   (None)

##### Beschreibung

-   darf nur im Eventscript von DefineResize aufgerufen werden
-   obige Beschreibung geht davon aus, dass ggf. mehrere Aufrufe der
    Funktion getätigt werden
-   die Controls werden im Allgemeinen DW- Controls sein

## wf_DefineHotKey

##### Argumente

-   as_KeyName
-   identifiziert die Taste
-   für einige Tasten gibt es mehrere KeyNames (diese sind dann durch
    Bestrich getrennt nebeneinander angeführt)
-   die KeyNames sind Case insensitive
-   folgende Tasten werden unterstützt (die Bedeutung sollte eigentlich
    klar sei):
    -   Sprach- unabhängige Zeichen- Tasten im Buchstabenblock
    -   "a"
    -   ...
    -   "z"
    -   "0"
    -   ...
    -   "9"
    -   "( )", " ","blank", "space"
    -   Sprach- abhängige Zeichen- Tasten im Buchstabenblock - deutsches
        Tastaturlayout
    -   "ger-"
    -   "ger\<"
    -   "ger,"
    -   "ger."
    -   "ger+"
    -   "gerü"
    -   "ger#"
    -   "gerö"
    -   "gerß"
    -   "ger\^"
    -   "ger´"
    -   "gerä"
    -   Sprach- unabhängige funktionale Tasten im Buchstabenblock
    -   "escape", "esc"
    -   "enter", "return"
    -   "tab"
    -   "bs", "backspace", "back", "(\<\<)"
    -   Tasten im Pfeiltasten- Block
    -   "left", "(\<)"
    -   "up", "(\^)"
    -   "down", "(v)"
    -   "right", "(\>)"
    -   Tasten im Einfügen- Block
    -   "del"
    -   "end"
    -   "insert"
    -   "home", "pos1"
    -   "next", "pagedown",
    -   "pageup", "prior", "previous"
    -   Zeichen- Tasten im Ziffernblock
    -   "num/"
    -   "num\*"
    -   "num-"
    -   "num+"
    -   "num,"
    -   "num."
    -   "num1"
    -   ...
    -   "num9"
    -   Funktionstasten
    -   "f1", "f01"
    -   ...
    -   "f12"
    -   Sonstige
    -   "menu"
-   Alt- Taste drücken und loslassen, hier sollte beim
    uf_SendKeyCombination zumindest ab_alt false sein
-   wenn es mehrere Namen für eine Taste gibt, wird in den Events
    AcceptHotKey und HotKeyAppl vom System jener Name übergeben, der
    hier dem System übergeben worden ist
    -   ab_shift
-   true, wenn zum Zeitpunkt des Tastendrucks die Shift- Taste aktiv
    sein soll bzw. war
-   es kann auch null übergeben werden, dies bedeutet, dass die Shift-
    Taste irrelevant ist - noch nicht released
    -   ab_control
-   true, wenn zum Zeitpunkt des Tastendrucks die Control- Taste aktiv
    sein soll bzw. war
-   es kann auch null übergeben werden, dies bedeutet, dass die Control-
    Taste irrelevant ist - noch nicht released
    -   ab_alt
-   true, wenn zum Zeitpunkt des Tastendrucks die Alt- Taste aktiv sein
    soll bzw. war
-   es kann auch null übergeben werden, dies bedeutet, dass die Alt-
    Taste irrelevant ist - noch nicht released
    -   as_CallbackCode
-   wird in den Events AcceptHotKey und HotKeyAppl vom System als
    Parameterwert übergeben
-   damit können mehrere Tastenkombinationen zu einer gemeinsamen
    Verarbeitung zusammengefasst werden -- as_CallbackCode könnte z.B.
    der Name einees selbst definierten Events sein, dass dann im
    Eventscript von HotKeyAppl aufgerufen wird
-   der Parameter kann frei nach Belieben verwendet werden
    -   ai_CallbackNumber
-   wird in den Events AcceptHotKey und HotKeyAppl vom System als
    Parameterwert übergeben
-   kann additiv zu oder statt as_CallbackCode verwendet werden
-   könnte z.B. als Parameterwert zur Übergabe in das unter
    as_CallbackCode beschriebene Event dienen - es könnte z.B. für f7
    hier 7 in ein Event FunktionstasteGedrückt übergeben werden
-   der Parameter kann frei nach Belieben verwendet werden

##### Rückgabewert

-   (None)

##### Beschreibung

-   definiert eine Tastenkombination, welche immer, wenn das Window
    aktiv ist, abgefangen wird und Events auslöst
-   es gibt folgenden Ablauf, wenn eine definierte Tastenkombination
    gedrückt wird: . Aufruf von AcceptHotKey
-   wenn hier false returned wird,
-   wird die Tastenkombination nicht als Shortcut behandelt, sondern
    ganz normal weiterverarbeitet
-   erfolgt kein Aufruf von HotKeyAppl (siehe nächster Ablaufpunkt)
-   ACHTUNG: alles, was hier geschieht, geschieht sofort ( meistens sind
    Aktivitäten in HotKeyAppl besser aufgehoben, weil HotKeyAppl
    gepostet wird . Aufruf von HotKeyAppl
-   Aufruf ist gepostet
-   Vorteile gegenüber einem Menüpunkt mit Shortcut:
-   kein Menüpunkt nötig
-   auch möglich, wenn Menü disabled ist (z.B. MDE- Modus)
-   es stehen alle Tasten zur Verfügung
-   es kann Stituationsbezogen die Tastenkombination nicht als Shortcut
    behandelt werden
-   Vorteile gegenüber Key- Event des DW's:
-   es stehen alle Tasten zur Verfügung
-   es kann die weitere Verarbeitung verhindert werden (siehe Ablauf)
-   die Tastenbezeichnungen müssen nicht ggf. über ein englisches
    Tastaturlayout ermittelt werden
-   es können auch Tasten (- Kombinationne) umgemapped werden
-   dies erreicht man dadurch, dass man für die Tastenkombination
    wf_DefineHotKey aufruft und dann im HotKeyAppl- Script mittels
    cst_UiHelper. uf_SendKeyCombination () die neue Tastenkombination
    sendet
-   im w_ApplMdi sollte wf_DefineHotKey im Initialze- Event aufgerufen
    werden (wenn die pfu_fun_Version noch kein Initialize- Event hat,
    kann das Open- Eventscript erweitert werden) - ACHTUNG: Im
    OnOpenAppl- Eventscript sollte der Aufruf nicht erfolgen!

## wf_DeleteAll

##### Argumente

-   ab_VonMenue
-   kann weggelassen werden und ist dann false
-   true ( es wird Delete wie vom Menü aus aufgerufen ( wf_Tr-
    Funktionen werden implizit aufgerufen
-   false ( Aufruf muß innerhalb einer mittels wf_TrBegin eingeleiteten
    Transaktion erfolgen. Bei Mißerfolg muß diese mittels wf_TrRollback
    zurückgerollt werden

##### Rückgabewert

-   boolean
-   true, wenn erfolgreich

##### Beschreibung

-   Löscht das aktuelle AO aus der Datenbank und aus idw_list
-   Folgender Ablauf: . Event DeleteIsPossible . Event BeforeMenuDelete
-   Nur wenn ab_menu=true . Beginn der Transaktion
-   Nur wenn ab_menu=true . Event BeforeDelete . für alle DWs, außer
    idw_list:
-   idw_neu kommt zu Schluß . Event OnDelete
-   hier wird Standardmäßig ein SQL- Delete auf die Update- Table des
    DWs abgesetzt. Dabei sind alle Key- Columns des AOTs in der Where-
    Bedingung vertreten
-   Das Event kann übersteuert werden . Event AfterDelete . Das Löschen
    ist abgeschlossen, AO ist bereits aus idw_list entfernt, Es gibt ein
    neues aktuelles AO bzw. die Liste ist leer . Event AfterDeleteOk .
    Ende der Transaktion
-   Nur wenn ab_menu=true

## wf_DisposeOleObject

##### Argumente

-   aole\_
-   das Ole- Objekt, das ebtsorgt werden soll

##### Rückgabewert

-   (None)

##### Beschreibung

-   entsorgt ein OLE- Objekt
-   siehe wf_CreateOleObject

## wf_DwStatMenuEnabled

##### Argumente

##### Rückgabewert

-   (None)

##### Beschreibung

-   ACHTUNG: ist nicht mehr notwendig, wenn doch bitte melden!
-   Führt das Aktiv / Passiv- Setzen von Menüs u.s.w. erneut durch.
-   Dabei wird auch das Event DwStatMenuEnabled aufgerufen

## wf_Einsehen

##### Argumente

-   as_druckart_cd
-   as_druck_ueber_nr
-   as_druck_nr

##### Rückgabewert

-   (None)

##### Beschreibung

-   Ruft w_pfu_job_druck auf wobei die Argumente als Suchbedingungen
    angewandt werden.

## wf_EndPasteAo

##### Argumente

##### Rückgabewert

-   (None)

##### Beschreibung

-   dw_ApplObj.Event SollPaste

## wf_GeaendertOk

##### Argumente

##### Rückgabewert

-   (None)

##### Beschreibung

-   ist nach wf_TrCommit genau dann aufzurufen, wenn folgende
    Bedinnungen erfüllt sind:
-   das Window wird ferngesteuert
-   im Zuge der Fernsteuerung wird wf_TrCommit nicht für dieses Window
    aufgerufen
-   die Liste soll nach dem wf_Save erhalten bleiben

## wf_GetHide (geerbt von w_ApplEnv)

##### Argumente

##### Rückgabewert

-   boolean

##### Beschreibung

-   liefert true, wenn Window versteckt ist, sonst false
-   wird close für ein Window, welches man so geöffnet hat, daß es beim
    close nur versteckt wird, aufgerufen, kann mittels wf_GetHide
    festgestellt werden, ob close funktioniert hat. (Es funktioniert
    z.B. nicht, wenn die letzte Änderung nicht gespeichert worden ist.)

## wf_HatFocus

##### Argumente

##### Rückgabewert

-   boolean

##### Beschreibung

-   liefert true, wenn Window den Focus hat

## Anmerkung

-   siehe auch gf_FocusWApplObj

## wf_InCommand

##### Argumente

-   as_command
-   Kommandowort

##### Rückgabewert

-   boolean
-   liefert true, wenn Kommandowort im Kommandostring des Environments
    enthalten ist

##### Beschreibung

-   Siehe dazu: Begriffe.Kommandostring des Environments

## wf_information2nl (geerbt von w_ApplEnv)

##### Argumente

-   as_text
-   Informationstext
-   wird in die Sprache der aktuellen Anmeldung übersetzt
-   ist keine Übersetzung vorhanden wird nicht übersetzt
    -   aa_par\[1-9\]
-   0 bis zu 9 Parameter
-   für den 3. Parameter muss in as_text "\[3auf_nr\]" vorhanden sein
-   3 steht hier exemplarisch für eine Ziffer von 1 bis 9
-   "auf_nr" ist ein col_name in pfu_column und ist ausschließlich für
    die Formatierung notwendig
-   vom System stehen statt "auf_nr" folgende eingebaute Columns zur
    Verfügung:
    -   "TypeC"
    -   "TypeN"
    -   "TypeD"
    -   "TypeDt"
    -   "TypeT"
-   parameter wird mittels uf_AnyToInputstring auf String konvertiert -
    Null wird zu Leerstring

##### Rückgabewert

-   (None)

##### Beschreibung

-   gibt einen Informationstext aus
-   Es werden Werte des Windowtitles im Title der Messagebox angezeigt
-   siehe wf_TrBegin, wf_BatchBegin
-   wird gepostet, wenn das Window noch nicht angezeigt ist
-   für Abwärtskompatibilität muss die alte Funktion im tc\_- Objekt
    bzw. als gf\_ in der tc_fun implementiert werden

## wf_informationNl (geerbt von w_ApplEnv)

##### Argumente

-   as_text
-   Informationstext in der Sprache des Anwenders

##### Rückgabewert

-   (None)

##### Beschreibung

-   gibt einen Informationstext aus
-   Es werden Werte des Windowtitles im Title der Messagebox angezeigt
-   siehe wf_TrBegin, wf_BatchBegin
-   wird gepostet, wenn das Window noch nicht angezeigt ist
-   ist dann zu verwenden, wenn der Informationstext z.B. aus einer
    Funktion zurückkommt und bereits in die Sprache des Anwenders
    übersetzt ist

## wf_InitRadioMenu

##### Argumente

-   am_checked
-   Menüpunkt, welcher zu Beginn angehakt sein soll

##### Rückgabewert

-   (None)

##### Beschreibung

-   Dient zur Initialisierung eines Radiobutten- Menü- Komplexes
-   es muß eine Instance- Variable vom Typ des abgeleiteten Menüs
    vorhanden sein
-   im Initialize- Event des Windows steht z.B. folgender Aufruf:
    wf_InitRadioMenu ( im_best_pos.m_options.m_liste_std )

Siehe auch - dw_ApplObj.event RadioMenuClicked -
m_ApplObj.mf_RadioClicked

## wf_InitToggleMenu

##### Argumente

-   am\_
-   Menüpunkt
    -   ab_checked
-   angehakt Ja/nein

##### Rückgabewert

-   (None)

##### Beschreibung

-   Dient zur Initialisierung eines Toggle- Menüpunktes
-   es muß eine Instance- Variable vom Typ des abgeleiteten Menüs
    vorhanden sein
-   im Initialize- Event des Windows steht z.B. folgender Aufruf:
    im_best_pos = im_ApplObj wf_InitToggleMenu (
    im_best_pos.m_options.m_liste_std, ... )

Siehe auch - w_ApplObj.event ToggleMenuClicked (geerbt von w_ApplEnv) -
m_ApplObj.mf_ToggleClicked (geerbt von m_ApplEnv)

## wf_InQueryCommand

##### Argumente

-   as_command
-   Teil- Kommando, für welches überprüft werden soll, ob es im
    aktuellen Query- Kommando enthalten ist

##### Rückgabewert

-   boolean
-   true ( as_command ist im aktuellen Query- Kommando enthalten

##### Beschreibung

-   wf_query erhält als Argument ein Kommando, welches sich aus mehreren
    Teilkommandos zusammensetzten kann.
-   in den Events BeforeSetSelectStart und BeforeSetSelectFinish kann
    mittels wf_InQueryCommand abgefragt werden, ob as_command beim
    vorhergegangenen Aufruf von wf_query im Kommando enthalten war.

Siehe auch - wf_query

## wf_ListeAktualisieren

##### Argumente

##### Rückgabewert

-   boolean
-   true ( as_command ist im aktuellen Query- Kommando enthalten

##### Beschreibung

-   macht das, was bei F5 in der Liste passiert
-   ACHTUNG: prüft nicht, ob der Status nicht update bzw. new ist -
    dafür ist der Aufrufer selbst verantwortlich - ANMERKUNG: wenn die
    Abprüfung gewünscht wird, bauen wir sie ein

## wf_KeyList2Dw

##### Argumente

-   adw\_
-   genau für dieses Dw soll der Key gesetzt werden

##### Rückgabewert

-   (None)

##### Beschreibung

-   Setzt den Key (also die Key- Felder lt. AOT) aus idw_list in alle
    Rows des übergebenen Datawindows

## wf_MachEmpty

##### Argumente

##### Rückgabewert

-   (None)

##### Beschreibung

-   Macht das Listdatawindow leer.
-   ACHTUNG: nicht mehr verwenden -- statt dessen wf_Reset verwenden!!!

## wf_MdeButtonClose (geerbt von w_ApplEnv)

##### Argumente

##### Rückgabewert

-   (None)

##### Beschreibung

-   Wenn im MDE- Modus von einem DW-Button (siehe wf_AddDwButtonAppl)
    aus das aktuelle Window geclosed wird, kann es zu Problemen mit dem
    Focus und dem BringToFront kommen - für diesn Fall gibt es diese
    Funktion
-   Die Funktion muss als letztes Statement im ausgeführten Code
    stehen!!!
-   Die Funktion führt den Close durch und kümmert sich um das Focus-
    Problem
-   das Problem sollte allerdings auch durch Aufgabe12267 gelöst sein -
    "sollte" ( testen

## wf_Menu

##### Argumente

##### Rückgabewert

-   (None)

##### Beschreibung

-   öffnet das Menü für die Anmeldung des Windows, wenn dieses bereits
    geöffnet ist, wird der Focus auf es gesetzt

## wf_New

##### Argumente

-   ab_paste
-   kopiertes AO soll gepastet werden
-   kann weggelassen werden, dann wird false angenommen und es müssen
    auch alle nachfolgenden Parameter weggelassen werden
-   für true siehe dw_ApplObj.Event SollPaste
    -   ab_menu
-   true ( Funktion wird vom Menü aus aufgerufen oder es soll dies
    vorgegaukelt werden
-   der Parameter ac_AufrufVon des Events NewIsPossible wird abhängig
    von ab_menu gesetzt
-   kann weggelassen werden, dann wird false angenommen und es müssen
    auch alle nachfolgenden Parameter weggelassen werden
    -   al_RowList
-   die Row für das neue Datenobjekt wird in der Liste genau an dieser
    Position eingefügt
-   kann weggelassen werden, dann wird (RowCount der Liste + 1)
    angenommen und es müssen auch alle nachfolgenden Parameter
    weggelassen werden
    -   ab_InsertRowList
-   true ( es wird eine neue Zeile in die Liste eingefügt
-   false ( es wird die vorhandene Zeile überschrieben - wird bei lgv-
    tcl_pdt.w_pdt_pos eingesetzt - Details sind nicht mehr present und
    müssen dort nachgeschaut werden, wenn false benötigt wird
-   kann weggelassen werden, dann wird true angenommen

##### Rückgabewert

-   boolean
-   true ( erfolgreich false ( nicht erfolgreich

##### Beschreibung

-   leitet das Anlegen eines neuen Datensatztes ein
-   wird im Normalfall in der Applikation ohne Parameter aufgerufen

## wf_next

##### Argumente

##### Rückgabewert

-   boolean
-   wenn erfolgreich ( true, sonst ( false

##### Beschreibung

-   macht das AO der nächsten Zeile von idw_list zum aktuellen AO
-   darf nur im Zustand Display aufgerufen werden

## wf_NoWWorking (geerbt von w_ApplEnv)

##### Beschreibung

-   siehe cst_ApplEnv.uf_NoWWorking

## wf_open (geerbt von w_ApplEnv)

##### Argumente

-   ab_wakeifpossible
-   true (
-   Wenn es ein Window gibt für das gilt:
-   wurde von this aus aufgerufen
-   ist im Zustand sleeping (= ist versteckt und deaktiviert ) wird
    dieses Window aufgeweckt, anstatt daß ein neues Window aufgemacht
    wird
-   ACHTUNG: Soll bei einer Jobverarbeitung ein Window wie z.B.
    w_auf_pos mit ab_wakeifpossible=true geöffnet werden, ist wf_open
    von cst_ApplEnv.iw_main aus aufzurufen (iw_main.wf_open ...)
    -   as_window
-   der Name des zu öffnenden/weckenden Windows
-   dabei gibt es 2 Funktionalitäten:
    -   siehe uf_AddWindowMap
    -   Variation eines Windows:
-   das Window heißt in der Applikation z.B. "w_auf"
-   übergeben wird "w_auf/umbuch", um das Window im "Umbuchungsmodus" zu
    starten
-   in diesem Modus soll es z.B.
    -   andere Berechtigungen (z.B. auch gewisse Felder nicht sichtbar)
    -   andere Query- Felder geben
-   es gibt dann für jede variation einen eigenen pfu_win- Eintrag
-   kann im aufgerufenen Window über iuo_ae.is_RequestedWindow abgefragt
    werden
-   mittels gf_WindowWName kann daraus der Windowname ohne Variation
    gewonnen werden
    -   ab_sheet
-   Window ist MDI- Client, also ein Dokumentenwindow der Aplikation
    -   aa_arg
-   Ein Any- Argument, welches vom geöffneten Window ausgewertet werden
    kann gf_c("e") ... Argument wird aus dem Environment weitergeleitet
    gf_c("n") ... Kein Argument sonst ......... Parameter ist das
    Argument
-   kann im aufgerufenen Window mittels iuo_ae.ia_arg ausgewertet werden
-   es kann auch ein Array übergeben werden - Allerdings muss dann
    ia_arg zunächst einem Array mit dem gleichen Typ wie das übergebene
    Array zugewiesen werden
    -   as_command
-   Siehe dazu: Begriffe.Kommandostring des Environments
-   wenn as_command = "e", wird es aus dem Environment genommen
    -   as_focusonclose
-   { 't', 'n', 'e' } \[ 's' \] \[{ 'w', 'W', 'b' } \]
-   Der erste Buchstabe sagt aus, welches Window den Focus erhält, wenn
    das aufgerufene Window geclosed wird. 't' ( this: das aufrufende
    Window 'a' ( Anmeldung: das Window der Anmeldung (wie beim Öffnen
    aus dem Menü) 'n' ( null: keine Angabe ( wird nach Windows- Regeln
    ermittelt 'e' ( Environment: das Window, das den Focus erhält, wenn
    das aufrufende Window geclosed wird
-   's' und { 'w', 'c', 'd' } sind nur möglich, wenn der erste Buchstabe
    'e', 'a' bzw. 't' ist
-   's' (
-   Das aufgerufene Window geht in den Zustand sleeping, wenn es
    "geclosed" wird
-   Ein Window im Zustand sleeping wird wirklich geschlossen, wenn das
    Window, von dem aus es geöffnet worden ist, geschlossen wird.
-   Wird das aufrufende Window geschlossen / sleeping gemacht, geschiet
    dies auch für das aufgerufene
-   { 'w', 'W', 'b' } (
-   Das aufrufende Window ist (teilweise) inaktiv bis das aufgerufene
    Window geclosed wird
-   dies sollte immer der Fall sein, wenn Konstanten im aufgerufenen
    Window von Feldern in einem DW mit nicht genau einer Row im
    aufrufenden Window abhängig sind
-   der Unterschied zwischen "w" und "W" ist abhängig vom Typ des
    aufrufenden Windows
-   wenn das aufrufende Window ein w_ApplObj ist gilt für dieses,
    nachdem das aufgerufene Window offen ist:
-   "w":
-   es darf, sobald der Anwender die Kontrolle erhält, nicht im Status
    update oder new sein ansonsten erfolgt wf_Cancel
-   Tabpages und DWs sind nicht disabled
-   Buttons sind disabled
-   alle Menüpunkte, die etwas verändern, sind disabled
-   es können keine Änderungen durchgeführt werden (natürlich auch nicht
    Löschen)
-   "b":
-   wie "w", allerdings sind auch die Buttons enabled
-   ACHTUNG: noch nicht implementiert!!!
-   "W":
-   Der Status darf update oder new sein
-   alle Controls des Windows sind disabled
-   alle Menüpunkt, die sich auf das Window beziehen sind disabled
    -   as_event
-   Event, dessen Script Werte vom aufgerufenen Window übernimmt, dieses
    gegebenenfalls schließt und die entsprechende Verarbeitung startet
    'e' ( wird aus dem Environment übernommen 'n' oder '' ( kein solches
    Event vorhanden sonst (
-   im aufgerufenen Window Variable gefüllt:
    -   is_AcceptEvent (mit as_event)
    -   iw_AcceptEvent (mit this)
-   Entweder 'n' verwenden, oder rückfragen!!!
    -   ab_UseAnmeldMfa
-   kann weggelassen werden, dann wird true angenommen und es muss auch
    ai_anmeldung weggelassen werden
-   false ( die Anmeldungssmfa wird ignoriert
-   wird für Fernsteuerung verwendet - z.B.:
-   Anmeldungssmfa -mfa = (1,0,0)
-   interaktives Speichern einer Auftragsposition, Mandant = 1
-   es soll automatisch eine Bestellposition mit Mandant = 2 angelgt
    werden
-   siehe auch as_command "privileged"
    -   ai_anmeldung
-   Anmeldung für das neue Window
-   kann 0 sein, dann wird die Anmeldung des Windows angenommen
-   kann weggelassen werden, dann wird die Anmeldung des Windows
    angenommen und es muss auch ab_UseAnmeldMfa weggelassen werden
-   ACHTUNG: die Applikation ist dafür verantwortlich, dass die
    ai_anmeldung entsprechende Anmeldung angemeldet ist
-   siehe auch as_command "privileged"
    -   as_datacontextstate
-   {k, e, m}
-   'k' ( für das Window wird beim Open/Wake KEIN Eigener DataContext
    erstellt -- es wird der Datacontext vom Parent- Window übernommen
-   'e' ( für das Window wird beim Open/Wake ein EIGENEN DataContext
    erstellt, das Window ist dann dessen Master
-   'm' ( für das Window wird beim Open/Wake kein Eigener DataContext
    erstellt -- es wird der Datacontext vom Parent- Window übernommen,
    allerdings wird das Window zum MASTER des übernommen Datacontext --
    dies ist aber nur möglich, wenn das vorige Master- Window im Status
    Display ist
-   kann weggelassen werden, dann wird "e" angenommen
-   nur in Verbindung mit ApplicationServer relevant

##### Rückgabewert

-   w_ApplEnv (der Windowtyp, von dem w_ApplObj abgeleitet ist)
-   das aufgerufene Window
-   Achtung: steht erst zur Verfügung, nachdem alle Scripts, welche im
    Zuge des Open des aufgerufenen Windows ablaufen, beendet sind.
-   NULL, wenn das Window nicht geöffnet werden konnte

##### Beschreibung

-   Öffnet ein Window
-   siehe auch cst_ApplEnv.( uf_SetCallConst, uf_DefineAufrufConst )

## wf_PostSetPresentation (geerbt von w_ApplEnv)

##### Argumente

##### Rückgabewert

-   (None)

##### Beschreibung

-   es wird der SetPresentation- Mechanismus gepostet
-   im Normalfall wird dies vom System durchgeführt

## Wann verwenden

-   BSP.: Itemchangedappl einer Column, die im DwStatTabEnabled
    ausgewertet wird

## wf_previous

##### Argumente

##### Rückgabewert

-   boolean
-   wenn erfolgreich ( true, sonst ( false

##### Beschreibung

-   macht das AO der vorigen Zeile von idw_list zum aktuellen AO
-   darf nur im Zustand Display aufgerufen werden

## wf_query

##### Argumente

-   as_command
-   kann weggelassen werden
-   Ein aus mehreren durch Blank getrennten Teilkommandos
    zusammengesetzer Kommandostring
-   dieser kann danach mittels wf_InQueryCommand ausgewertet werden
-   Folgende Teil- Kommandos werden intern ausgewertet:
    -   "noacceptquery"
-   Wird beim Query- Window der Ausführen- Button geklickt, wird
    normalerweise wf_AcceptQuery ausgeführt, ist "noacceptquery"
    angegeben, erfolgt dies nicht.
    -   "withnew"
-   Im Query- Window gibt es zusätzlich einen "Neu anlegen"- Button
    -   "noquerydw"
-   das Queryfenster wird nicht sichtbar, es wird automatisch der
    Ausführen- Button geklickt
-   die Query- Parameter lt. wf_open ( as_command ) werden ignoriert,
    außer as_command wird weggelassen

##### Rückgabewert

-   (None)

##### Beschreibung

-   bewirkt die Ausführung der Aktitiväten, die auch bei der Anwahl des
    Menüpunkts "neue Auswahl" ablaufen
-   Ablauf: . iuo_ParList zurücksetzen . Query- Fenster öffnen . wenn
    "noquerydw" in as_command ist (also z.B. bei ColSearch), oder keine
    Querybedingungen im Queryfenster sichtbar sind, wird sofort
    wf_AcceptQuery aussgeführt (siehe dort unter Folgender Ablauf)
-   Bsp.: Aufruf eines Windows mit programmgesteuerten Suchbedingungen:
    Folgender Ablauf: . lw\_ = wf_open ( ... )
-   as_command = "" . lw\_.wf_query
-   as_command = "noquerydw noacceptquery" . iuo_ParList.uf_AddPar /
    uf_AppParWert / uf_NewChainedParList
-   Suchbedingunen festlegen . wf_AcceptQuery

## wf_Reset

##### Argumente

##### Rückgabewert

-   (None)

##### Beschreibung

-   setzt das Window in den Zustand 'e' (= leeres Window)
-   kann auch aufgerufen werden, wenn das Window im Zustand n (=
    Neuanlage) oder 'u' (= Update) ist
-   ACHTUNG: darf nur verwendet werden, wenn das Window ferngesteuert
    wird!!!

## wf_ResumePasteAo

##### Argumente

##### Rückgabewert

-   (None)

##### Beschreibung

-   Siehe wf_New mit ab_paste = true

## wf_RethrowException

##### Argumente

-   as_FunctionOrEventName
-   as_Context
-   a_Exception
-   throwable
-   eine Exception, die mittels Try Catch abgefangen worden ist

##### Rückgabewert

-   (None)

##### Beschreibung

-   wirft eine cst_Exception (diese hat mehr Informationen als das
    normale Exception vom Typ Trowable)
-   extrahiert die entsprechenden Informationen aus Exception, wenn
    diese eine OLE- Exception ist

## wf_Return

##### Argumente

##### Rückgabewert

-   (None)

##### Beschreibung

-   liefert abhängig von ic_return den den Key des aktuellen AO's an das
    aufrufende Window zurück
-   wird beim Menüpunkt Bearbeiten(Übernehmen aufgerufen

## wf_Save

##### Argumente

-   ab_VonMenue
-   kann weggelassen werden und ist dann false
-   true ( es wird save wie vom Menü aus aufgerufen ( wf_Tr- Funktionen
    werden implizit aufgerufen
-   false ( Aufruf muß innerhalb einer mittels wf_TrBegin eingeleiteten
    Transaktion erfolgen. Bei Mißerfolg muß diese mittels wf_TrRollback
    zurückgerollt werden.

##### Rückgabewert

-   boolean
-   true ( Speichern erfolgreich
-   false ( Speichern nicht erfolgreich

##### Beschreibung

-   Speichert den Master- Detail- Verbund, welcher sich im Neu bzw.
    Ändern- Zweig befindet ab.
-   siehe BeforeUpdate

## wf_ScrollToFindWhere

##### Argumente

-   as_FindWhere
-   Where- String für die Find- Funktion in idw_list
-   wird im Anwendungsprogramm typischerweise durch einen vohergehenden
    cst_ApplEnv.uf_KeyFindWhere Aufruf ermittelt - folgender Ablauf ist
    typisch: . merken des aktuellen AO's in idw_list mittels
    uf_KeyFindWhere . herumscrollen in idw_list bzw. anlegen oder
    löschen von AOs . zum ursprünglichen AO zurückscrollen
-   dieses muß nicht in der selben Row wie voher stehen
-   erfolgt deshalb mittels wf_ScrollToFindWhere

##### Rückgabewert

-   long

-   0 ( erfolgreich

-   0 ( AO nicht in Liste vorhanden

-   -1 ( sonstiger Fehler

##### Beschreibung

-   Funktion scrollt zum idw_list zum AOT mit Key lt. as_FindWhere

## wf_SetApplKz

##### Argumente

-   as_ApplKz
-   Applikationsmoduskennzeichen - siehe Beschreibung
-   darf höchstens 3 Zeichen lang sein, sonst erfolgt
    Applikationsabbruch!

##### Rückgabewert

-   (None)

##### Beschreibung

-   Die an einem Grid vom Anwender vorgenommenen Änderungen wie
    -   Feldbreiten
    -   Spaltenüberschriften (können mit Alt+Doppelklick auf die
        Spaltenüberschrift geändert werden (Abschluss mit TAB - nicht
        ändern mit ESC))
    -   Feldpositionen
    -   Sortierung können abgespeichert und wieder abgerufen werden.
-   Die Speichererung erfolgt unter anderem abhängig vom
    Applikationsmoduskennzeichen.
-   Z.B.: TC Bestellpositionen: hier gibt es 2 Applikationsmodi:
    -   Normal
    -   Bestellvorschlag
-   wf_SetApplKz setzt für das Window das Applikationsmoduskennzeichen,
    dies hat folgende Auswirkungen:
-   für jedes Grid- DW im Window wird das entsprechende Gridschema aus
    der Datenbank gelesen und angewandt, wenn für das entsprechende Grid
    ein solches gespeichert ist
-   Beim Speichern des Gridschemas wird in der Datenbank das
    Applikationsmoduskennzeichen entsprechend gesetzt
-   siehe dw_ApplObj.uf_NoGridschema
-   Amerkung: Winmodus und Applikationsmoduskennzeichen sind voneinander
    unabhängig (Pro Windowtyp können in der Datenbank (pfu_winmodus) bis
    zu 9 Winmodi angelegt werden - der Winmodus kann vom Anwender über
    das Einstellungen- Menü angewählt werden. Die Funktionsweise ist wie
    beim Applikationsmoduskennzeichen.)

Siehe auch - BeforeWinmodus - wf_SetWinmodus

## wf_SetKeepListOnWake

##### Argumente

-   Ab\_
-   True ( ein
-   False ( aus

##### Rückgabewert

-   (None)

##### Beschreibung

-   Schaltet den "Liste bleibt erhalten"- Mechanismus ein bzw. aus
-   Wird typischer Weise im Eventscript von AfterCommand ausgeführt -
    sollte nicht in BeforeCommand oder einem früher aufgerufenen Event
    aufgerufen warden
-   Bei der Entscheidung, ob und mit welchem Parameterwert die Funktion
    aufgerufen wird, muss ic_return berücksichtigt werden!!!

## wf_SetMaximized (geerbt von w_ApplEnv)

##### Argumente

##### Rückgabewert

-   (None)

##### Beschreibung

-   maximiert das Window - allerdings nicht echt - es handelt sich um
    dieses grausliche pseudo- Maximieren, welches hmp schon seit Jahren
    ein Dorn im Auge ist aber von SC innig geliebt wird ?.

## wf_SetPresentation (geerbt von w_ApplEnv)

##### Argumente

##### Rückgabewert

-   (None)

##### Beschreibung

-   die Funktion wird normalerweise vom System gepostet
-   es geschieht jeweils ggf. folgendes:
-   Window wird enabled und angezeigt
-   es wird auf das richtige TAB gesprungen
-   es werden die sichtbaren DW's retrieved
-   es wird der Windowtitle anfgezeigt
-   ist aufzurufen, wenn eine der obigen Aktivitäten bereits während der
    Verarbeitung notwendig sind - Bsp.: Es wird ein neues Window
    geöffnet und dann ferngesteuert und der Anwender soll das neue
    Window währenddessen schon sehen
-   darf im Batch- Modus nicht aufgerufen werden

## wf_SetWinmodus

##### Argumente

-   as_WinmodusKz
-   winmodus_kz lt. Tabelle pfu_winmodus
-   für Standard ist "" zu übergeben

##### Rückgabewert

-   boolean
-   false ( hat nicht funktioniert

##### Beschreibung

-   über die Funktion kann der Winmodus, der vom Benutzer ja über das
    Einstellungen- Menü gesetzt werden kann von der Applikation aus
    gesetzt werden
-   der Winmodus wird allerdings nicht über seinen P- Key "winmodus"
    sondern über "winmodus_kz" ausgewählt
-   gibt es mehrere Winmodi mit gleichem winmodus_kz, was ja möglich
    ist, wird der entsprechende Winmodus mit der kleinsten
    Winmodusnummer herangezogen

Siehe auch - wf_SetApplKz - BeforeWinmodus - WinModusOnOpenWake

## wf_SqlExportTab

##### Argumente

-   as_tabname
-   as_keycolumns
-   die beim unten beschriebenen UPDATE- Statement verwendeten Key-
    Columns
-   Columns durch Leerzeichen getrennt
    -   as_delupdins
-   ist ein String, der durch löschen von Zeichen aus dem String "dui"
    gebildet wird
-   es können 0 bis 2 Zeichen gelöscht werden
-   jeder Buchstabe steht für ein erzeugtes SQL- Statement
-   'd' steht für DELETE
-   es wird genau ein Statement, das alle entsprechenden Rows löscht,
    erzeugt
-   'u' steht für UPDATE
-   es wird für jede Row, die der durch wf_SqlExportWhere definierten
    WHERE- Bedingung genügt, ein UPDATE- Statement erzeugt.
-   die WHERE- Bedingung entspricht dem Key lt. as_keycolumns der
    Tabelle lt. as_tabname
-   'i' steht für INSERT
-   es wird für jede Row, die der durch wf_SqlExportWhere definierten
    WHERE- Bedingung genügt, ein INSERT- Statement erzeugt.
-   das Statement ist so formuliert, dass es keinen Fehler verursacht,
    wenn die Row schon existiert ( es kann eine Update- Insert- Logik
    implementiert werden
-   die beiden folgenden Argumente sind im Allgemneinen nicht notwendig
    und können weggelassen werden:
    -   as_InTabname
-   für diese Table muss bereits ein wf_SqlExportTab- Aufruf erfolgt
    sein
    -   as_InColumn
-   folgende Bedeutung:
-   es wird für die Statements folgende Teil- WHERE- Bedingung
    eingefügt: as_tabname + "." + as_InColumn + " in (" + "select" +
    as_InColumn + " from " + as_InTabname + " where " + WhereInTab
-   dabei ist WhereInTab die gesamte Where- Bedingung für as_InTabname

##### Rückgabewert

-   (None)

##### Beschreibung

-   darf ausschließlich im Eventscript von SqlExport aufgerufen werden
-   definiert, dass die Tabelle lt. as_tabname exportiert werden soll

## wf_SqlExportWhere

##### Argumente

-   as_column
-   aa_wert
-   as_tablepatterns
-   ist ein Regular Expression, wie wir ihn aus dem vi kennen (z.B.
    \[ab\]\* trifft alle Zeichenketten beliebiger Länge (auch 0), die
    aus den Zeichen 'a' zund 'b' bestehen - siehe PB- Funktion match)
-   die unten beschriebene Teil- WHERE- Bedingung wird für die SQL-
    Statements einer Tabelle herangezogen, wenn
    wf_SqlExportTab.as_tabname as_tablepatterns entspricht

##### Rückgabewert

-   (None)

##### Beschreibung

-   darf ausschließlich im Eventscript von SqlExport aufgerufen werden
-   definiert eine Teil- WHERE- Bedingung für die durch Aufrufe von
    wf_SqlExportTab definierten SQL -Script- Generierungen
-   die Teil- WHERE- Bedingung für die Tabelle tab lautet dann: tab +
    "." + as_column + " = " + itr\_.uf_AnyToLiteral ( aa_wert )
-   die Gesamt- WHERE- Bedingung entsteht dann jeweils durch AND-
    Verknüpfen der lt. as_tablepatterns passenden Teil- WHERE-
    Bedingungen

## wf_SqlOk

-   sollte nicht mehr verwendet werden
-   siehe tr\_.uf_SqlOk

## wf_status

##### Argumente

##### Rückgabewert

-   char
-   Folgende Werte: "n" ( es wird gerade ein neues AO angelegt "u" ( in
    einem DW des Windows wurde eine Änderung durchgeführt und es wurde
    noch nicht gespeichert "e" ( AO- Auswahl ist leer (( Liste ist leer)
    "d" ( nicht in einem der anderen Stati

## wf_ThrowException

##### Argumente

-   as_FunctionOrEventName
-   as_Context
-   Position innerhalb des Scripts
-   kann auch leer sein
    -   as_Error

##### Rückgabewert

-   (None)

##### Beschreibung

-   wirft eine cst_Exception, die die Informationen lt. den Parametern
    enthält

## wf_TrBegin

##### Argumente

-   ab_TrCheck
-   kann weggelassen werden, wenn auch ab_PostMessages weggelassen wird,
    dann wird true angenommen
-   true ( es wird von System geprüft, ob die Transaktion beendet worden
    ist bevor der Benutzer die Kontrolle zurückerhält.
-   false -\>
-   ACHTUNG: es kann dann der Benutzer innerhalb der Transaction die
    Kontrolle erhalten
-   ist notwendig (Bankomatanbindung Kassa), wenn das Programm während
    der Transaction auf ein externes Ereignis warten können muss
    -   ab_PostMessages
-   kann weggelassen werden, wenn auch ab_TrCheck weggelassen wird, dann
    wird true angenommen
-   true -\> während der Transaction werden Meldungen (wf_information,
    ...) gepostet

##### Rückgabewert

-   (None)

##### Beschreibung

-   Markiert den Beginn einer Transaction in einem Window
-   Immer wenn Datenbankänderungen vorgenommen werden sollen, und das
    System nicht in einer Transaction ist, muß die Transaction des
    Windows begonnen werden.
-   Sind an einer Transaktion mehrere Windows beteiligt, ist für jedes
    beteiligte Window wf_TrBegin aufzurufen.
-   Darf nicht in einem Event- Script aufgerufen werden! ( Befindet man
    sich in einem Event- Script der Komplexe Speichern bzw. AO- Löschen,
    ist die Transaction des Windows bereits begonnen )
-   siehe auch wf_TrCommit und wf_TrRollback

## wf_TrCommit

##### Argumente

##### Rückgabewert

-   (None)

##### Beschreibung

-   Beendet eine erfolgreiche Transaction
-   Führt DB- Commits über das Event CommitAll durch
-   bestätigt alle vorhergegangenen unbestätigten Änderungen in DWs
-   Darf nicht in einem Event- Script aufgerufen werden! ( Befindet man
    sich in einem Event- Script der Komplexe Speichern bzw. AO- Löschen,
    wird die Transaktion vom System committed )
-   siehe auch wf_TrBegin und wf_TrRollback

## wf_TrRollback

##### Argumente

##### Rückgabewert

-   (None)

##### Beschreibung

-   Rollt eine Transaction zurück
-   Führt DB- Rollbacks über das Event RollbackAll durch
-   macht alle vorhergegangenen Änderungen in den DWs des Windows,
    welche nicht gespeichert und commited sind, was über das Menü,
    wf_Save(true) oder wf_Save() und wf_TrCommit erreicht werden kann,
    rückgängig. ( Es ist kein wf_Cancel notwendig. Anmerkung: Es werden
    allerdings nur DWs jenes Windows, dessen wf_TrRollback aufgerufen
    worden ist, behandelt!
-   Darf nicht in einem Event- Script aufgerufen werden! ( Befindet man
    sich in einem Event- Script der Komplexe Speichern bzw. AO- Löschen,
    wird die Transaktion vom System zurückgerollt )
-   siehe auch wf_TrBegin und wf_TrCommit

## wf_WAoParent

##### Argumente

-   aw\_
-   by reference, wird gesetzt
-   das Parent- Window, wenn ein solches vom Typ w_ApplObj vorhanden ist

##### Rückgabewert

-   boolean
-   true, wenn ein Parent- w_ApplObj- Window vorhanden ist

##### Beschreibung

-   Will man in einem von einem anderen Window aus aufgerufenen Window
    Werte des aufrufenden Windows auslesen, kann das wie folgt
    geschehen: if wf_WAoParent ( lw_auf ) then ...
    lw_auf.idw_neu.uf_GetItem ( ... ) else // kein Parent- Window
    vorhanden end if
-   mittels classname() kann Windowname ermittelt werden

## wf_WorkEnd

##### Argumente

##### Rückgabewert

-   (None)

##### Beschreibung

-   ruft_ApplEnv.uf_WorkEnd(false,this) auf

## wf_WorkStart (geerbt von w_ApplEnv)

##### Beschreibung

-   siehe cst_ApplEnv.uf_WorkStart

## wf_yes (geerbt von w_ApplEnv)

##### Argumente

-   as_text
-   Frage an den Benutzer
-   ACHTUNG: muss in die Sprache der Anmeldung übersetzt sein - dies hat
    mittels iuo_ae.uf_Text2nl zu erfolgen!
    -   ac_YesNo
-   "y" ( Default- Button ist Yes
-   "n" ( Default- Button ist No

##### Rückgabewert

-   boolean
-   true, wenn der Anwender yes ausgewählt hat

##### Beschreibung

-   Sollte verwendet werden, wenn eine Ja/Nein- Entscheidung durch den
    Benutzer erforderlich ist.
-   Alternativ kann auch dw_ApplObj.uf_yes verwendet werden.
-   Wird die Funktion innerhalb einer Transaction mit
    wf_TrBegin(ab_PostMessages=true) aufgerufen oder werden keine
    Meldungen (wf_information, ...) lt. wf_BatchBegin angezeigt, wird
    keine Benutzerentscheidung abgefragt, sondern die Betätigung des
    Default- Buttons angenommen.
-   Das Fragezeichen wird nicht vom System angehängt

## Variables

## ib_closing

-   Darf nicht verändert werden!
-   true, wenn das Window gerade geclosed wird

## ib_DisableAll

-   siehe wf_open

## ib_MdeAppl

-   Darf nicht verändert werden!
-   true, wenn Applikation im MDE- Modus ist

## ib_PastingAo

-   Darf nicht verändert werden!
-   true, wenn Window (also ganzes AO) gerade gepastet wird
-   wird erst nach dem Speichern bzw. wiederrufen des letzten DW's
    zurückgesetzt

## ib_ReturnJump

-   darf nicht verändert werden!
-   ist true, wenn "colsearch" im Environment- Kommando (siehe
    Begriffe - Kommandostring des Environments) ist und kein
    erfolgreicher ExportKeyToParent war

## ib_ToClose

-   Darf im BeforeCommand auf true gesetzt werden - dadurch wird das
    Window vor dem Anzeigen wieder geschlossen

## ic_return

-   darf nicht verändert werden
-   mögliche Werte: c ... Window wurde über die ColSearch-
    Funktionalität aufgerufen
    -   ... Window wurde mit der Fernglasfunktionalität vom Benutzer
        aufgerufen q ... Window wurde mit der Fernglasfunktionalität vom
        Suchfenster aus vom Benutzer aufgerufen n ... sonst
-   bei 'o' und 'q' steht die Variable idw_return zur Verfügung

## idw_Focus

-   Darf ausschließlich zum Zugriff auf die freigegebenen
    Funktionen/Events/Variablen von dw_ApplObj verwendet werden!!!
-   Das Datawindowcontrol, das gerade den Focus hat
-   Achtung: Wenn der Benutzer z.B. auf einen Button clickt, hat kein DW
    den Focus und idw_focus ist null

## idw_LastFocus

-   Darf ausschließlich zum Zugriff auf die freigegebenen
    Funktionen/Events/Variablen von dw_ApplObj verwendet werden!!!
-   Das Datawindowcontrol, das zuletzt den Focus erhalten hat, ihn aber
    nicht mehr haben muss

## idw_list

-   Darf ausschließlich zum Zugriff auf die freigegebenen
    Funktionen/Events/Variablen von dw_ApplObj verwendet werden!!!
-   Die Liste des Windows

## idw_neu

-   Darf ausschließlich zum Zugriff auf die freigegebenen
    Funktionen/Events/Variablen von dw_ApplObj verwendet werden!!!
-   Das DW, mit dem der Insert in die Haupttabelle des Windows erfolgt
-   muss nicht belegt sein, weil es kein sochles DW geben muss
-   wenn nicht belegt, dann ib_HatDwNeu=false sonst ib_HatDwNeu=true

## idw_return

-   Darf ausschließlich zum Zugriff auf die freigegebenen
    Funktionen/Events/Variablen von dw_ApplObj verwendet werden!!!
-   steht abhängig von der Variable ic_return zur Verfügung
-   verweist auf das Datawindow- Control, von dem aus die Fernglas-
    Funktionalität aufgerufen worden ist

## idw_ReturnJump

-   Darf ausschließlich zum Zugriff auf die freigegebenen
    Funktionen/Events/Variablen von dw_ApplObj verwendet werden!!!
-   steht abhängig von der Variable ic_return zur Verfügung
-   ist das DW in dem das ColSearch- Feld eingegeben worden ist.
    idw_return ist dann idw_ReturnJump.idw_function

## ii_null

-   Darf nicht verändert werden!
-   ist fix Null V

## ii_TabPageAkt

-   Darf nicht verändert werden!
-   Index der Aktuellen Tabpage
-   Bsp. von Adeg: if tab\_.control[ii_TabPageAkt](#ii_tabpageakt) =
    tab\_.TabPageEssenz then
-   liefert true, wenn die aktuelle Tabpage = TabPageEssenz ist

## il_null

-   Darf nicht verändert werden!
-   ist fix Null

## il_ReturnRow

-   Darf nicht verändert werden!
-   ist die Row in die returned werden soll

## im_ApplObj

-   Darf ausschließlich zum Zugriff auf die freigegebenen
    Funktionen/Events/Variablen von m_ApplObj verwendet werden!!!
-   Das Menü

## is_null

-   Darf nicht verändert werden!
-   ist fix Null

## is_WinModus

-   Darf nicht verändert werden!
-   WindowModus: wird über das Einstellungen- Menü gesetzt
-   wird beim Grigschema- Lesen ausgewertet
-   wird beim Setzen der Defaultwerte berücksichtigt

## is_WinModusKz

-   Darf nicht verändert werden!
-   Applikation kann dieses beim Setzen eines Winmodus auswerten -\> ein
    bestimmtes Window versteht bestimmte WinModusKz

## itr\_

-   Darf ausschließlich zum Zugriff auf die freigegebenen
    Funktionen/Events/Variablen von tr\_ verwendet werden!!!
-   Das Transaction- Object des DWs
-   Der Lookup von Fremd- Aos kann allerdings über eine andere
    Transaction erfolgen.

## iuo_ae

-   Darf ausschließlich zum Zugriff auf die freigegebenen
    Funktionen/Events/Variablen von cst_ApplEnv verwendet werden!!!
-   Das sogenannte Environment des Windows vom Typ cst_ApplEnv

## iuo_ParList

-   darf auf keinen Fall verändert werden!!!
-   Die Liste der Query- Parameter vom Typ cst_ParList
-   ACHTUNG
-   nur mit Vorsicht zu verwenden
-   sollte eigentlich nicht mehr nötig sein
-   im Zusammenhang mit wf_besorgs keinesfalls verwenden
-   Wird vom Query- Window belegt

## iuo_BesorgsParList

-   Darf ausschließlich zum Zugriff auf die freigegebenen
    Funktionen/Events/Variablen von cst_ParList verwendet werden!!!
-   Liste der Query- Parameter vom Typ cst_ParList für die Funktion
    wf_besorgs
-   siehe dort

## iw_AoParent

-   Darf ausschließlich zum Zugriff auf die freigegebenen
    Funktionen/Events/Variablen von w_ApplObj verwendet werden!!!
-   Das w_ApplObj, von dem aus das aktuelle Window aufgerufen worden
    ist.
-   kann null sein ( immer vor Gebrauch mit gf_hasinstance abfragen

## w_JobObj

Anmerkung: - alle Datenbankupdates auf die pfu_job- Tabellen erfolgen
mittels sqlca - die diesbetüglichen Transaktionen werden innerhalb von
w_JobObj und dw_JobObj abgehandelt

## Events

## action

##### Argumente

-   by reference ab_markieren
-   ist standardmäßig false
-   true ( der Job soll markiert werden
-   dadurch können z.B. am Tagesende fehlerhafte Verarbeitungen
    festgestellt werden
-   Es können allerdings auch Jobs markiert werden, deren Verarbeitung
    erfolgreich war, deren Ergebnis aber anzuschauen ist.
    -   by reference as_VerEndTxt
-   ist standardmäßig leer
-   Diagnosetext, welcher in den Job eingetragen wird
-   hiermit kann dem Anwender mitgeteilt werden, ob die Verarbeitung
    erfolgreich war
-   detailierte Meldungen an den Anwender sollten mittels
    wf_information\* erfolgen
-   Fehlermeldungen (nicht für den Anwender bestimmt) sollten mittels
    wf_error erfolgen
-   sowohl die mittels wf_information\* als auch die mittels wf_error
    abgesetzten Meldungen werden in die Tabelle pfu_job_vinfo und die
    Logdatei geschrieben

##### Rückgabewert

-   (None)

## Ableitung

-   darf überschrieben werden
-   darf erweitert werden

##### Beschreibung

-   Hier steht die Abfolge der Applikations- Aktionen in einem w_JobObj
-   Ein w_JobObj hat standardmäßig ein dw_JobObj namens idw_job
-   Standardmäßig erfolgt folgender Ablauf (siehe dw_JobObj): . Query-
    Parameter mit where_string in dw_job einsetzen . idw_job.uf_retrieve
    ( "" ) . idw_job.uf_print () . wf_ToPrinter ()
-   D.h. für eine einfache Liste muß nichts übersteuert werden
-   idw_job muß allerdings überhaupt nicht verwendet werden
-   Achtung: es darf keine Transaction offen sein, wenn das Script
    verlassen wird!!!

## CommitAll (geerbt von w_ApplEnv)

##### Argumente

##### Rückgabewert

-   (None)

## Ableitung

-   darf überschrieben werden
-   darf erweitert werden

##### Beschreibung

-   Im Standardeventscript erflogt Commit auf sqlca
-   hier muß commit für alle im Window vorkommenden Transaction-
    Objekten, für Welche DB- Änderungs- Stratements erfolgen,
    durchgeführt werden..

## DelaySeconds

##### Argumente

-   by reference ab_markieren
-   ist standardmäßig false
-   true ( der Job soll markiert werden
-   dadurch können z.B. am Tagesende fehlerhafte Verarbeitungen
    festgestellt werden
-   Es können allerdings auch Jobs markiert werden, deren Verarbeitung
    erfolgreich war, deren Ergebnis aber anzuschauen ist.
    -   by reference as_VerEndTxt
-   ist standardmäßig leer
-   Diagnosetext, welcher in den Job eingetragen wird
-   hiermit kann dem Anwender mitgeteilt werden, ob die Verarbeitung
    erfolgreich war
-   detailierte Meldungen an den Anwender sollten mittels
    wf_information\* erfolgen
-   Fehlermeldungen (nicht für den Anwender bestimmt) sollten mittels
    wf_error erfolgen
-   sowohl die mittels wf_information\* als auch die mittels wf_error
    abgesetzten Meldungen werden in die Tabelle pfu_job_vinfo und die
    Logdatei geschrieben

##### Rückgabewert

-   Sekunden Delay
-   Um diese Sekunden soll der Job später gestartet werden
-   0 = Stadard, Job läuft sofort

## Ableitung

-   darf überschrieben werden

##### Beschreibung

-   Wird nach Initialice und vor dem Action Event durchgeführt
-   Es kann dazu verwendet werden, dass Bedingungen für den Start des
    Jobs geprüft werden und wenn diese nicht erreicht sind, eine Zeit
    definiert wird, zu der diese Bedingungen nochmal geprüft werden
    sollen.
-   Wird 0 returniert, wird der Job abgearbeitet (Action Event
    aufgerufen).
-   Wird ein Wert \> 0 retourniert, dann wird die aktuelle Zeit +Anzahl
    Sekunden als Starten Ab Zeitpunkt eingesetzt. Es werden dabei auch
    die Regeln für Starten innerhalb von berücksichtigt.

z.B. Job läuft Täglich um 8:00, innerhalb von 2 Std. . 1. Prüfung am
2.9.2019 um 8:00 - Bedinugung ist nicht erreicht, Job wird in 1800
Sekunden (= 30 Min.) wieder gestartet . 2. Prüfung am 2.9.2019 um 8:31 -
Bedingung ist nicht erreicht ..... . 3. Prufung am 2.9.2019 um 9:01
..... . 4. Prufung am 2.9.2019 um 9:32 - Bedingung ist nicht erreich -
in 30 Minten würe 10:02, dass ist außerhalb der Starten Ab Zeit und
daher wird der Job das nächste Mal am 3.9.2019 um 8:00 gestartet. . 5.
Prüfung am 3.9.2019 um 8:00 - Bedingung ist erreicht - Job läuft durch

## RollbackAll (geerbt von w_ApplEnv)

##### Argumente

##### Rückgabewert

-   (None)

## Ableitung

-   darf überschrieben werden
-   darf erweitert werden

##### Beschreibung

-   Im Standardeventscript erflogt Rollback auf sqlca
-   hier muß Rollback für alle im Window vorkommenden Transaction-
    Objekten, für Welche DB- Änderungs- Stratements erfolgen,
    durchgeführt werden.

### Functions

## classname

##### Argumente

##### Rückgabewert

-   string
-   Windowname

## wf_AddDjDruck

##### Argumente

-   adc_job_snr
-   al_job_druck_lfd_nr

##### Beschreibung

-   legt bei der Fernsteuerung von w_pfu_dj eine neue Row im Ausdruck-
    DW an
-   siehe wf_NewDruck

## wf_AddDjIndiv

##### Argumente

-   as_ParName
-   der Druckerdaemon unterstützt derzeit:
    -   AttachmentDir
-   muss genau so geschrieben sein
-   as_ParWert ist dann ein UNC- Namen eines Verzeichnisses
-   alle Files in diesem Verzeichnis werden dann dem Druckaufteag
    angefügt
-   funktioniert derzeit nur bei EMail und Fax
    -   as_ParWert

##### Beschreibung

-   legt bei der Fernsteuerung von w_pfu_dj eine neue Row im Indiv- DW
    an
-   siehe wf_NewDruck

## wf_AddUncFile

##### Argumente

-   as_dokument_unc
-   Dokument Pfad welches hinzugefügt werden soll
    -   as_unc_verarb_kz
-   "a" ( angehängt
-   "mg" ( Merge gesamt
-   "ms" ( Merge Seitenweise
-   "k" ( Kopie
-   kann weggelassen werden dann wird "a" angenommen
-   wenn angeben muss auch as_merge_above_jn angegeben werden
    -   as_merge_above_jn
-   kann weggelassen werden dann wird "n" angenommen
-   wenn angeben muss auch as_unc_verarb_kz angegeben werden

##### Beschreibung

-   legt bei der Fernsteuerung von w_pfu_dj eine neue Row im Unc- DW an

## wf_ChangeDjItem

##### Argumente

-   as_column
-   aa_wert

##### Beschreibung

-   Setzt eine Column bei der Fernsteuerung von w_pfu_dj
-   siehe wf_NewDruck

## wf_ChangeDjDruckItem

##### Argumente

-   as_column
-   aa_wert

##### Beschreibung

-   Setzt eine Column bei der Fernsteuerung von w_pfu_dj_druck
-   siehe wf_NewDruck

## wf_ChangeDruckItem

##### Argumente

-   as_column
-   Column- Name lt. w_pfu_job_druck - siehe DB- Beschreibung - weiters:
-   "dokument_unc" (
-   das Dokument lt. aa_wert wird ins Archiv kopiert
-   ist zu verwenden, wenn bei wf_NewDruck as_dateityp nicht übergeben
    wird
-   "da_orig_loe_jn" (
-   aa_wert = "j" ( das oben beschriebene Dokument wird nach dem
    Kopieren ins Archiv gelöscht
    -   aa_wert

##### Beschreibung

-   Setzt eine Column bei der Fernsteuerung von w_pfu_job_druck
-   siehe wf_NewDruck

## wf_error (geerbt von w_ApplEnv)

##### Argumente

-   as_wo
-   Position im Script
    -   as_ErrorText
-   Fehlermeldung

##### Beschreibung

-   gibt eine Fehlermeldung aus
-   diese wird nicht übersetzt
-   Die Meldung enthält den Windownamen

Siehe auch - dw_ApplObj.uf_error

## wf_information\*

##### Beschreibung

-   Syntax und Funktionalität genau wie w_ApplObj.wf_information\*

## wf_NewDj

##### Argumente

##### Beschreibung

-   das Erzeugen einer neuen Row in pfu_dj und der zugehörigen
    pfu_dj_druck- Rows erfolgt intern über die Fernsteuerung von
    w_pfu_dj
-   siehe wf_NewDruck

## wf_NewDruck

##### Argumente

-   ab_generatedocumentfromdatawindow
-   muss nicht ausgefüllt sein
-   wenn das Feld nicht ausgefüllt ist wird
    -   true angenommen wenn ein adw_druck übergeben wird
    -   ansonsten false
    -   as_dateityp
-   muss nicht ausgefüllt sein
-   wenn das Feld ausgefüllt ist
-   dann ist auch adw_druck auszufüllen und umgekehrt
-   dann wird aus dem Inhalt von adw_druck ein entsprechendes File
    erzeugt
-   folgende Filetypen werden unterstützt:
    -   'pdf'
    -   'txt'
    -   'csv'
    -   'wmf'
    -   'xls'
    -   'xlsx'
    -   'psr'
-   ACHTUNG: die Kodierung des ausgegebenen Files ist ANSI
-   Es gäbe allerdings die möglichkeit auch in utf\* (Unicode) zu
    kodieren - dazu wäre eine pfu_fun- Änderung nötig
-   Wie die Kodierung bei .pdf ist, kann mir (hmp) niemand sagen
-   Hierbei gibt es 2 Versionen:
    -   Pdf- Erzeugung übe AMYUNI
    -   Pdf- Erzeugung über SaveAs und Ghost-Script
    -   Für Informationen wäre ich dankbar, sonst muss ich dies einmal
        selbstl überprüfen
-   wenn das Feld nicht ausgefüllt ist, muss das Dokument der
    pfu_job_druck- Row anderweitig erzeugt werden und über
    wf_ChangeDruckItem mit dem Feld dokument_unc bekannt gegeben werden
    -   as_endung
-   muss nicht ausgefüllt sein
-   wenn das Feld nicht ausgefüllt ist wird as_dateityp verwendet
-   hat nur beim Generieren einen Einfluss
    -   adw_druck
-   es muss nothing übergeben werden, wenn
    ab_generatedocumentfromdatawindow false ist

##### Rückgabewert

-   (None)

##### Beschreibung

-   siehe Datenbankbeschreibung
    -   pfu_job
    -   pfu_job_druck
    -   pfu_dj
    -   pfu_dj_druck
-   das Erzeugen einer neuen Row in pfu_job_druck erfolgt intern über
    die Fernsteuerung von w_pfu_job_druck
-   folgender Ablauf : . (1) \> DW retrieven und ggf. nachbearbeiten \>
    ein Dokument in einem temporären Verzeichnis erstellen . mittels
    wf_NewDruck das Erstellen eines Drucks (=Dokument im Archiv und die
    zugehörige pfu_job_druck- Row) einleiten . ggf. Feldwerte für Felder
    von pfu_job_druck mittels wf_ChangeDruckItem- Aufrufen setzen -
    folgende Felder sind möglich:
    -   druckart_cd
    -   mfa\[123\]\_nr
    -   druck_nr
    -   dokument_unc
-   zu setzen, wenn das Dokument aus einem temporären Verzeichnis
    übernommen werden soll
    -   da_orig_loe_jn
-   'j' ( das Dokument im temporären Verzeichnis soll nach dem
    Archivieren gelöscht werden . mittes wf_SaveDruck
    -   die nicht gesetzten Felder von pfu_job_druck lt. pfu_job setzen,
        wenn sie dort vorhanden sind
-   entspricht "@job"
    -   wenn as_dateityp ausgefüllt ist, das Dokument aus dem DW
        erzeugen
    -   das Dokument ins Archiv kopieren
    -   die pfu_job_druck- Row anlegen . ggf. weiter bei (1), um ein
        weiteres Dokument zu erzeugen - ein Druckjob (= Windows-
        Druckjob oder Email oder ...) kann mehrere Dokumente beinhalten
        . mittels wf_NewDj das Erstellen eines Druckjobs einleiten .
        ggf. Feldwerte für Felder von pfu_dj mittels wf_ChangeDjItem-
        Aufrufen setzen
-   für die Druckerfindung
    -   komart_kz
    -   appl_fcd
    -   drucker_cd
-   für elektronischen Versand (Email, Fax, ...)
    -   von_emailadr
    -   bcc_emailadr
    -   komid_wert
    -   empfaenger
    -   absender
    -   betreff
    -   dj_einspoolen_jn
-   'j' ( der Druckjob wird beim Speichern sofort dem Druckerdaemon
    übergeben (( das dj3- File wird sofort angelegt)
-   'n' ( der Druckjob wird erst beim wf_ToPrinter dem Druckerdaemon
    übergeben . für jeden Druck des Druckjobs . wf_AddDjDruck
-   dadurch werden von- Email- Adresse, bcc- Email- Adresse und Absender
    unabhängig voneinander lt. pfu_druckart gesetzt, wenn sie noch nicht
    gesetzt sind und in pfu_druckart definiert sind . ggf. Feldwerte für
    Felder von pfu_dj_druck mittels wf_ChangeDjDruckItem- Aufrufen
    setzen
    -   lade_cd
    -   zu_drucken_anz . ggf. Zusätzliche Parameter (Indiv- Section des
        dj3- Files) des Druckjobs mittels wf_AddDjIndiv setzen . (2)
        mittels wf_SaveDj den Druckjob speichern
-   vor dem eigentlichen Speichern werden die nicht gesetzten Felder lt.
    pfu_job gesetzt, wenn sie dort vorhanden sind
-   im bisherigen Ablauf muss explizit für die Transaktion gesorgt
    werden . Übergabe der Druckjobs an den Druckerdaemon mittels
    wf_ToPrinter
-   2 Möglichkeiten für die Transaktion: \> innerhalb einer Transaktion
    \> keine Transaktion aktiv ( dann wird innerhalb pro Drucker eine
    Transaktion durchgeführt
-   die Funktion dw_JobObj.uf_print führt die Schritte (1) bis (2) für
    genau einen Druck aus

## wf_open (geerbt von w_ApplEnv)

## siehe wf_open (geerbt von w_ApplEnv)

## wf_RegDiag (geerbt von w_ApplEnv)

##### Argumente

-   as\_
-   Diagnosetext

##### Rückgabewert

-   (None)

##### Beschreibung

-   Schreibt einen Diagnosetext in die Registry
    (HKEY_CURRENT_USER`\Software`{=tex}`\pfundner`{=tex}`\diag`{=tex}).
-   Jeder Eintrag hat eine forlaufende Nummer.

## wf_SaveDj

##### Argumente

##### Beschreibung

-   siehe wf_NewDruck

## wf_SaveDruck

##### Argumente

-   al_job_druck_lfd_nr
-   by reference

##### Beschreibung

-   siehe wf_NewDruck

## wf_SqlOk

##### Argumente

-   as_fehlermeldung
-   Fehlermeldung, welche angezeigt wird, wenn false retourniert wird
    -   al_MinRows
-   wenn \> 0, dann müssen minsetens so viele Rows vom SQL- Statement
    bearbeitet worden sein, dies macht nur bei update einen Sinn
-   kann weggelassen werden, default ist 0
    -   atr\_
-   Transaction die geprüft werden soll

##### Rückgabewert

-   boolean
-   true ( das letzte SQL- Statement wurde fehlerfrei abgearbeitet
-   false ( Fehler ist aufgetreten

##### Beschreibung

-   Prüft, ob ein SQL- Statement fehlerfrei ausgführt worden ist und
    gibt eine Fehlermeldung aus, falls dies nicht der Fall ist.
-   Im Fehlerfall werden Werte des Windowtitles im Title der Messagebox
    angezeigt

## wf_ToPrinter

##### Argumente

##### Rückgabewert

-   (None)

##### Beschreibung

-   übergibt alle mittels w_JobObj. wf_NewDj u.s.w. erzeugten und noch
    nicht übegebenen PDF- Files den entsprechenden Printerqueues
-   siehe wf_NewDruck
-   Anmerkung: eine Printerqueue muß nicht unbedingt einem
    physikalischen Drucker zugeordnet sein, es kann sich auch um ein
    Fax- bzw. Email- System handeln.

## wf_TrBegin (geerbt von w_ApplEnv)

##### Argumente

##### Rückgabewert

-   (None)

##### Beschreibung

-   Markiert den Beginn einer Transaction in einem Window
-   Immer wenn Datenbankänderungen vorgenommen werden sollen, und das
    System nicht in einer Transaction ist, muß die Transaction des
    Windows begonnen werden.
-   Sind an einer Transaktion mehrere Windows beteiligt, ist für jedes
    beteiligte Window wf_TrBegin aufzurufen.
-   siehe auch wf_TrCommit und wf_TrRollback

## wf_TrCommit (geerbt von w_ApplEnv)

##### Argumente

##### Rückgabewert

-   (None)

##### Beschreibung

-   Beendet eine erfolgreiche Transaction
-   Führt DB- Commits über das Event CommitAll durch
-   siehe auch wf_TrBegin und wf_TrRollback

## wf_TrRollback (geerbt von w_ApplEnv)

##### Argumente

##### Rückgabewert

-   (None)

##### Beschreibung

-   Rollt eine Transaction zurück
-   Führt DB- Rollbacks über das Event RollbackAll durch
-   siehe auch wf_TrBegin und wf_TrCommit

## Variable

## idc_job_snr

-   darf nicht geändert werden!
-   aktuelle Jobnummer

## iuo_ae

-   Darf ausschließlich zum Zugriff auf die freigegebenen
    Funktionen/Events/Variablen von cst_ApplEnv verwendet werden!!!
-   Das sogenannte Environment des Windows vom Typ cst_ApplEnv
-   Es stehen allerdings keine ApplObj- mäßigen Informationen /
    Funktionalitäten zur Verfügung

## iuo_job

-   darf nicht geändert werden!
-   Das Job- Objekt vom Typ cst_Job

## iuo_JobParList

-   darf nicht geändert werden!
-   = iuo_job.iuo_ParList
-   siehe cst_ParList

## Klassenreferenz pfu_win

## dw_pfu_applpers

-   DW zum Verwalten von pfu_applpers
-   wird im TC im w_adr_pers eingebaut
-   dazu gibt es Freeform- DWO, das allerdings übersteuert werden muss
-   muss im Verbund mit idw_neu leben
-   kann eine oder keine Row enthalten
-   prüft beim Eintragen von applpers_cd, ob er nicht schon vorhanden
    ist
-   im OnUpdateError- Event ist Unique- Key- Verletzung behandelt
-   führt beim Speichern ggf. die entsprechenden Workflow- Aktivitäten
    durch
-   folgende Felder müssen belegt, werden:
    -   applpers_cd
    -   Keyfelder von idw_neu
-   diese müssen in der Tabelle pfu_applpers indiv vorhanden sei und
    stellen die Joinbedingung dar
-   diese müssen im DWO indiv vorhanden sein
    -   applpers_mc

## Klassenreferenz OfficeIntegration

## cst_outlook

-   Object zum Anlegen von Outlook-Kontakten im Standalone-Outlook oder
    aber auch im Exchange Server
-   Funktioniert ab Version 2000

### Functions

#### uf_AddContact

##### Argumente

-   keine

##### Rückgabewert

-   boolean

##### Beschreibung

-   Initialisiert das Objekt um einen neuen Kontakt anlegen zu können.

#### uf_DeleteContact

##### Argumente

-   keine

##### Rückgabewert

-   boolean

##### Beschreibung

-   Löscht das mit uf_GetContact ausgewählte Objekt

#### uf_DeleteContact

##### Argumente

-   as_EntryID

##### Rückgabewert

-   boolean

##### Beschreibung

-   Löscht den Outlook-Kontakt der unter mitgeschickter EntryId
    verspeichert ist. Ruft uf_GetContact und danach uf_DeleteContact
    ohne Parameter auf.

#### uf_GetContact

##### Argumente

-   as_EntryID

##### Rückgabewert

-   boolean

##### Beschreibung

-   Hohlt den unter EntryID verspeichert Kontakt in den Speicher.

#### uf_Init

##### Argumente

-   ref as_Error

##### Rückgabewert

-   boolean

##### Beschreibung

-   Erstellt die Verbindung zu Outlook und ermittelt den Ordner wo die
    Kontakte verspeichert werden sollen lt. Tabelle pfu_oi.

#### uf_SetContact

##### Argumente

-   as_V_Name
-   as_N_Name
-   as_Titel
-   as_Firmenname
-   as_Persfunktion_MC
-   as_Strasse
-   as_Plz
-   as_Ort
-   as_Land_Bez

##### Rückgabewert

-   boolean

##### Beschreibung

-   Setzt für den aktuellen Kontakt die Information, speichert diese
    aber nicht.

#### uf_SetFieldData

##### Argumente

-   as_FieldName \> BusTelNum \> Bus2TelNum \> CarTelNum \> CompTelNum
    \> Department \> BusFaxNum \> Email1Adr \> Email2Adr \> Email3Adr \>
    MobTelNum \> Body \> KdNr \> Initialen \> WebPage \>
    VerrechnungsInfos
-   as_Value
-   ref as_Error

##### Rückgabewert

-   boolean

##### Beschreibung

-   Setzt für den aktuellen Kontakt die Information, speichert diese
    aber nicht. Siehe pfu_kz ( Feld outlook_kz.

#### uf_Show

##### Argumente

-   (None)

##### Rückgabewert

-   (None)

##### Beschreibung

-   Zeigt den aktuellen Kontakt an.

#### uf_UpdateContact

##### Argumente

-   ref string as_EntryID

##### Rückgabewert

-   boolean

##### Beschreibung

-   Setzt die mit uf_SetContact und uf_SetFieldData veränderten Daten am
    Kontakt ab, bzw. Speichert einen neuen. Als Reference Argument
    bekommt man einen eindeutigen String zurück der den Kontakt im
    Outlook definiert.

## DatawindowObjectProperties

-   Properties des DatawindowObjects können über folgende Syntax
    ausgelesen werden: \> dw\_.object.datawindow.property \>
    dw\_.object.columnname.property
-   Das Ergebnis ist immer vom Datentyp String.
-   Ein numerisches Property muß auf number konvertiet werden.
-   Wird der Ausdruck als Parameter in eine Function übergeben, muß auch
    auf string konvertiert werden.

## ANMERKUNG - ACHTUNG

-   Jedes Grid muss das "currentcolumn" - Feld haben
-   Die Funktion gf_diagnosefeld wird nicht mehr benötigt - also bitte
    nicht mehr verwenden!!!
-   In Grids ist ein Feld dadurch ein Diagnosefeld, dass es sich im DWO
    rechts des "currentcolumn" - Feldes befindet
-   In nicht- Grids ist ein Feld dadurch ein Diagnosefeld, dass es sich
    im DWO soweit rechts befindet, dass es im DW- Control außerhalb des
    sichtbaren Bereichs fällt
-   Felder, die nie eingegeben werden dürfen sollten entweder keine
    Taborder haben oder im Protect- Property des DWOs 1 als Expression
    eingetragen haben
-   ACHTUNG: wenn ein solches Property von einem Script aus gesetzt
    wird, ist damit zu rechnen, dass dies zu Problemen führt, da die
    pfu_fun die Werte beim open eines Windows ausliest, abspeichert und
    davon abhängig Einstellungen vornimmt und Entscheidungen trifft. Es
    kann durchaus vorkommen, dass die Probleme erst beim Upgrade auf
    eine neuere pfu_fun- Version auftreten. ( Das Setzen im Script
    sollte vermieden werden, bzw. es sollte Rücksprache gehalten werden.
-   Für Reports gilt die vorige Aussage nicht!

## Datawindow- Properties

-   beginnen mit: dw\_.object.datawindow.

## table.UpdateTable

-   die Update- Table des DWs

## Column- Properties

-   beginnen mit: dw\_.object.ColumnName.
-   gibt es die Property im DW- Painter auf der Expression- Tab- Page,
    kann diese Expression auch im Programm gesetzt werden. Dies erfolgt
    in der Form: `<initWert>`{=html} '\~t'
    `<Expression wie in Painter>`{=html}.

## font.weight

-   400 = normal 700 = fett
-   z.B.: "0\~tif ( fett_jn = 'j' , 700 , 100 )"

## protect

-   ACHTUNG: darf keinesfalls in einem Script verändert werden!!!
-   sollte nur statisch verwendet werden - also als expression 1 bzw. 0
-   ansonsten soll das Schützen von Columns über das Event protect
    erfolgen
-   ACHTUNG: wenn hier eine Expression eingetragen wird, muss sich der
    Programmerer um allfällige Benutzerberechtigungen selbst kümmern (
    dazu gibt es globale Function gf_berecht.... - Beschreibung fehlt
    noch - bei Bedarf bitte melden)
-   siehe auch ANMERKUNG - ACHTUNG

## Taborder

-   Syntax stimmt hier nicht - die Property sollte aber sowieso nicht im
    Programm angesprochen werden
-   Ein Feld braucht die Taborder nur dazu, dass es eingebbar ist
-   Allerdings bestimmt die Taborder beim Setzen von Defaultwerten und
    beim Pasten die Reihenfolge
-   Im idw_list wird die Taborder durch die pfu_fun gesetzt
-   siehe auch ANMERKUNG - ACHTUNG

## visible

-   ACHTUNG: darf keinesfalls in einem Script verändert werden!!!
-   ACHTUNG: wenn hier eine Expression eingetragen wird, muss sich der
    Programmerer um allfällige Benutzerberechtigungen selbst kümmern
-   für das Auslesen der Feld- Berechtigung bitte Rücksprache halten
-   siehe auch ANMERKUNG - ACHTUNG

## width

-   Breite der Column, bei uns in Pixels
-   z.B.: "0\~tif ( txt_kz = 'p', 252, 707 )"

## Global Functions

## Datetime Functions

## gf_dt_current

##### Argumente

##### Rückgabewert

-   datetime
-   Systemdatum+Uhrzeit lt. sqlca

## gf_dt_d

##### Argumente

-   adtm\_

##### Rückgabewert

-   Datetime
-   adtm\_ auf ganze Tage genau

## gf_dt_datmax

##### Argumente

##### Rückgabewert

-   datetime
-   Höchstes im System verwendetes Dummy-Datum (z.B.: für "gültig bis"-
    Logiken)

## gf_dt_datplus

##### Argumente

-   adtm\_
-   ai\_

##### Rückgabewert

-   datetime
-   neues Datum von adtm\_ + ai\_ Tage

## gf_dt_day

##### Argumente

-   adtm\_

##### Rückgabewert

-   integer
-   Tag des Monats von adt\_
-   Bsp.: 25.04.2000 ( 25

## gf_dt_dmy\[4\]

##### Argumente

-   ai_day
-   ai_month
-   ai_year
-   gf_dt_dmy:
-   2 oder 4- stellig
-   2- stellig ( das näherliegende Jahr von 1900+ai_year und
    2000+ai_year
-   gf_dt_dmy4:
-   es müssen die vollen 4 Stellen angegeben werden
-   so können auch historische Datümer vor 100 dargestellt werden

##### Rückgabewert

-   datetime
-   Datum aus den Argumenten und Uhrzeit = 00:00:00

## gf_dt_FirstOfMon

##### Argumente

-   adtm\_

##### Rückgabewert

-   datetime

##### Beschreibung

-   Liefert den Monatsersten des übergebenen Datums
-   zB: 01.12.2008

## gf_dt_GetDatz

##### Argumente

-   adtm_Data
-   adtm_Time

##### Rückgabewert

-   datetime
-   neues Datum --\> Datum von adtm_Date und Uhrzeit von adtm_Time

## gf_dt_h

##### Argumente

-   adtm\_

##### Rückgabewert

-   Datetime
-   adtm\_ auf ganze Stunden genau

## gf_dt_km

##### Argumente

-   adtm\_

##### Rückgabewert

-   string
-   Kalendermonat von adtm\_
-   Bsp.: 25.04.2000 ( 200004

## gf_dt_kmdiff

##### Argumente

-   as_KmSpaeter
-   Monat im Format JJJJMM
    -   as_KmFrueher
-   Monat im Format JJJJMM

##### Rückgabewert

-   long
-   Monate Differenz zwischen as_KmSpaeter und as_KmFrueher Bsp.:
    gf_KmDiff ( "200201", "200110" ) = 3

## gf_dt_kmplus

##### Argumente

-   as_km
-   Monat im Format JJJJMM
    -   ai_monate
-   kann positiv oder negativ sein

##### Rückgabewert

-   string
-   Kalendermonat von as_km + ai_monate

## gf_dt_kw

##### Argumente

-   adtm\_

##### Rückgabewert

-   string
-   Kalenderwoche 7-stellig von adtm\_
-   Bsp.: 06.09.2000 ( 2000/36

## gf_dt_kwmonday

##### Argumente

-   as_kw
-   Kalenderwoche im Format JJJJ/WW

##### Rückgabewert

-   datetime
-   Montag der Woche
-   Bsp.: 2000/37 ( 11.09.2000

## gf_dt_kwplus

##### Argumente

-   as_kw
-   Kalenderwoche im Format JJJJ/WW
    -   ai_wochen
-   kann positiv oder negativ sein

##### Rückgabewert

-   string
-   Woche im Format JJJJ/WW um ai_wochen erhöht

## gf_dt_m

##### Argumente

-   adtm\_

##### Rückgabewert

-   Datetime
-   adtm\_ auf ganze Minuten genau

## gf_dt_MonPlus

##### Argumente

-   adtm_datum
-   Datum als Datetime (Uhrzeit = 0)
    -   ai_monate
-   kann positiv oder negativ sein

##### Rückgabewert

-   Datetime
-   adtm_datum plus ai_monate

## gf_dt_MinutesDiff

##### Argumente

-   datetime adt_von
-   datetime adt_bis

##### Rückgabewert

-   long
-   Differenz in Minuten

## gf_dt_MinutesPlus

##### Argumente

-   datetime datum
-   long minuten

##### Rückgabewert

-   datetime

## gf_dt_month

##### Argumente

-   adtm\_

##### Rückgabewert

-   integer
-   Monat von adtm\_
-   Bsp.: 25.04.2000 ( 4

## gf_dt_monthname

##### Argumente

-   adtm\_

##### Rückgabewert

-   string
-   Name des Monats (1-12) \## Bsp.: 20.02.2008 ( Februar; 18.09.2013 (
    September

## gf_dt_now

##### Argumente

##### Rückgabewert

-   datetime
-   aktuelles Datum und aktuelle Uhrzeit lt. Client
-   besser ist gf_dt_current !!!

## gf_dt_s

##### Argumente

-   adtm\_

##### Rückgabewert

-   Datetime
-   adtm\_ auf ganze Sekunden genau

## gf_dt_tagediff

##### Argumente

-   adtm_1
-   adtm_2

##### Rückgabewert

-   integer
-   Tage Differenz zwischen adtm_1 und adtm_2

## gf_dt_today

##### Argumente

##### Rückgabewert

-   datetime

##### Beschreibung

-   Liefert das aktuelle Datum lt. Client mit Uhrzeit 00:00:00
-   besser ist ggf. gf_dt_current !!!

## gf_dt_ultimo

##### Argumente

-   adtm\_

##### Rückgabewert

-   datetime

##### Beschreibung

-   Liefert den Monatsletzten des übergebenen Datums
-   zB: 31.12.2008

## gf_dt_weekday

##### Argumente

-   adtm\_

##### Rückgabewert

-   integer
-   Nummer des Tages (1-7, Mo = 1)
-   Bsp.: Dienstag 25.04.2000 ( 2

## gf_dt_weekdayname

##### Argumente

-   adtm\_

##### Rückgabewert

-   string
-   Name des Tages (1-7, Mo = 1)
-   Bsp.: 20.02.2008 ( Mittwoch

## gf_dt_year

##### Argumente

-   adtm\_

##### Rückgabewert

-   integer
-   Jahr von adtm\_
-   Bsp.: 25.04.2000 ( 2000

## Time Functions

## gf_t_h

##### Argumente

-   at\_

##### Rückgabewert

-   time
-   at\_ in ganzen Stunden

## gf_t_m

##### Argumente

-   at\_

##### Rückgabewert

-   time
-   at\_ in ganzen Minuten

## gf_t_s

##### Argumente

-   at\_

##### Rückgabewert

-   time
-   at\_ in ganzen Sekunden

## Powerscriptfunktionen, welche verwendet werden dürfen

## alle Stringbehandlungsfunktionen

## close

## IsNumber

## SetNull

## today

## sonstige Functions

## gf_AnyToFindLiteral

##### Argumente

-   aa_wert

##### Rückgabewert

-   string
-   Literal für die Suchbedingung lt. Beschreibung

##### Beschreibung

-   bei der Verwendung von dw_ApplObj.find sind Literals in der
    Suchbedingung mittels der Funktion gf_AnyToFindLiteral zu
    realisieren

## gf_BerechtigtAnsehen

##### Argumente

-   auo_ae
-   Berechtigung wird für den Anmeldeuser von auo_ae
    -   as_window

##### Rückgabewert

-   boolean
-   liefert true, wenn der Anmeldeuser die Berechtigung zum Ansehen von
    as_window hat, sonst false

## gf_CheckEmailAdresse

##### Argumente

-   as_email
-   eine Email- Adresse oder meherere durch Strichpunkt getrennte Email-
    Adressen
-   zwischen Strichpunkt und nächster Email-Adresse dürfen Leerzeichen
    sein - müssen aber nicht

##### Rückgabewert

-   Boolean
-   True ( Syntax der Email-Adressen sind ok
-   False ( sonst

##### Beschreibung

-   Prüft eine oder mehrere Emailadressen syntaktisch

## gf_CmpAny

##### Argumente

-   aa_wert1
-   as_operator
-   { \<, \>, \<=, \>=, =, \<\> } \[1\] \[2\] \[b\]
-   1 bedeutet: return true, wenn aa_wert1 null ist
-   2 bedeutet: return true, wenn aa_wert2 null ist
-   b bedeutet: return true, wenn aa_wert1 und aa_wert2 null sind
    -   aa_wert2

##### Rückgabewert

-   boolean
-   Bsp.:
-   aa_wert1 = 4
-   aa_opreator = "\<"
-   aa_wert2 = 7 ( true
-   aa_wert2 = 2 ( false
-   wenn ein wert1

##### Beschreibung

-   Vergleich zweier Any- Variablen
-   Immer dann sinnvoll, wenn typloses Null vorkommen kann
-   ACHTUNG: uf_GetItem kann derzeut noch unter gewissen umständen
    typloses Null liefern, dies wird aber beseitigt!!!

## gf_CurrentJobSnr

##### Argumente

##### Rückgabewert

-   Decimal

##### Beschreibung

-   liefert, wenn sich das action- Event-Script von w_JobObj im
    CallStack befindet, die gerade verarbeitete job_snr
-   damit kann eine Expression eines DWO's auf diese zugreifen, ohne
    dass diese als RetrievelArgument übergeben wird

## gf_DecimalToInteropString

##### Argumente

-   adc_value
-   decimal

##### Rückgabewert

-   String
-   adc_value in einem Format, das in der Interop durch die Funktion
    Powerbuilder.InteropstringToDecimal wieder in Decimal umgewandelt
    werden kann

##### Beschreibung

-   wird benötigt, weil Decimal- Argumente nicht an Interop- Methoden
    übertragen werden können (Problem von Powerbuilder mit COM)

## gf_DecodeString

##### Argumente

-   as_string
-   String, in welchen die String- Werte mittels gf_EncodeString
    hineincodiert worden sind
    -   ai_pos
-   Ein- / Ausgabeparameter
-   beim ersten Aufruf wird 1 übergeben um den ersten Wert aus dem
    String zu decodieren
-   bei jedem weiteren Aufruf wird der vom vorigen Aufruf gesetzte Wert
    übergeben (Locale- Variable wird vor den Aufrufen auf 1 gesetzt und
    dann nur mehr übergeben

##### Rückgabewert

-   String

##### Beschreibung

-   siehe gf_EncodeString

## gf_DiagnoseFeld

##### Argumente

##### Rückgabewert

-   integer
-   1

##### Beschreibung

-   in der Expressions- Tab- Page des DW- Painters wird, wenn das
    Datawindow ein Grid ist, in der protect- Property
    "gf_diagnosefeld()" eingetragen, wenn das Feld nur zu
    Diagnosezwecken dient. Das Feld ist dann nur im Diagnosemodus
    sichtbar. Bei Computed Columns ist "gf_diagnosefeld()" in die
    visible- Property einzutragen. Weiters ist die Column im Definition-
    Event mittels uf_computed bekanntzugeben.

## gf_EncodeString

##### Argumente

-   as_string
-   String, welcher codiert werden soll.

##### Rückgabewert

-   String
-   codierter String

##### Beschreibung

-   dient zum Codieren von mehreren Strings in einem String durch
    Aufrufe der folgenden Art: gf_EncodeString ( column1 ) +
    gf_EncodeString ( column2 ) + ...
-   mittels hintereinanderfolgender Aufrufe von gf_DecodeString kann
    dieser Sting wieder in sein Einzelstrings zerlegt werden.
-   Bsp:
-   Computed- Field in einem DWO wird mittels gf_EncodeString- Aufrufen
    aufgebaut
-   Im Script wird die Column ausgelesen, und mittels gf_DecodeString
    zerlegt
-   Anwendung: die Datacolumn eines DDDWs enthält mehrere Werte

## gf_error

##### Argumente

-   apo_wo
-   beliebiges Objekt, dessen Classname angezeigt wird
-   hier wird das Objekt angegeben, in dem der Fehler aufgetreten ist
    -   as_wo
-   Position im Script
    -   as_ErrorText
-   Fehlermeldung

##### Beschreibung

-   gibt eine Fehlermeldung aus
-   diese wird nicht übersetzt
-   Die Meldung enthält den Windownamen des Windows, welches gerade den
    Focus hat
-   Im Script eines DWs muß uf_error verwendet werden
-   Im Script eines Windows muß wf_error verwendet werden

Siehe auch - w_ApplObj.wf_error

## gf_FocusWApplObj

##### Argumente

##### Rückgabewert

-   w_ApplObj
-   Window, das den Focus hat
-   ist uninstanziert (nicht null!) wenn kein w_ApplObj den Focus hat

## Anmerkungen

-   siehe auch wf_HatFocus

## gf_GetCliHostName

##### Argumente

##### Rückgabewert

-   string

##### Beschreibung

-   ruft intern cst_ApplEnv.uf_ClientName auf

## gf_GetExceptionDetailedText

##### Argumente

o

##### Rückgabewert

-   string

##### Beschreibung

-   ruft intern cst_ApplEnv.uf_ClientName auf

## gf_GetFilesInFolder (sys)

##### Argumente

-   as_Folder
-   Verzeichnis dessen Inhalt ausgelesen werden soll
    -   as_Filepattern
-   Kriterien für die zu findenden Dateien
-   *.*, *.txt, *.dji, ...
    -   as_Files\[\]
-   reference
-   Array mit gefundenen Dateien exklusive Ordner

##### Rückgabewert

-   Long
-   Anzahl der gefundenen Dateien

##### Beschreibung

-   Ermittelt alle Dateien mit einem bestimmten Kritierium in einem
    bestimmten Verzeichnis

## gf_GetHostName

##### Argumente

##### Rückgabewert

-   string

##### Beschreibung

-   ruft intern cst_ApplEnv.uf_HostName auf

## gf_GetLogin

##### Argumente

##### Rückgabewert

-   string

##### Beschreibung

-   ruft intern cst_ApplEnv.uf_login auf
-   darf nicht mehr verwendet werden, weil das Windows- Login in der
    Applikation keine Rolle spielen darf!!!
-   es sind die Funktionen uf_AnmeldUsr und uf_AnmeldApplpers zu
    verwenden!!!

## gf_GetNl

##### Argumente

##### Rückgabewert

-   string

##### Beschreibung

-   liefert die mittels gf_SetNl desetzte Sprache

## gf_halt

##### Argumente

-   as_object
-   Name des Objekts, aus dessen Script gf_halt aufgerufen wird
    -   as_wo
-   Beschreibung von Script und Position, von wo aus gf_halt aufgerufen
    wird
    -   as_error
-   Fehlerbeschreibung - Grund warum die Applikation beendet wird

##### Rückgabewert

-   none

##### Beschreibung

-   Dient zum Beenden der Applikation im Fehlerfall.

## gf_GetPar

##### Argumente

-   as_string
-   Name des CommandLineParameters, dessen Wert ermittelt werden soll

##### Rückgabewert

-   string

##### Beschreibung

-   Retourniert Wert des Parameters, null wenn Parameter nicht gefunden
    wurde
-   Der Parameter muß im DOS- Bereich folgendermaßen aussehen:
    parameter='parameterwert'
-   es dürfen nur einfache Hochkommas verwendet werden!

## gf_information2nl

##### Argumente

-   as_text
-   Informationstext

##### Rückgabewert

-   (None)

##### Beschreibung

-   Funktionalität wie w_ApplObj.wf_information, nur es gibt keine
    Parameter
-   Im Script eines Windows bzw. DW eines Windows muß wf_information2nl
    verwendet werden
-   werden Parameter benötigt muss man gw_AeAkt.wf_information2nl
    verwenden
-   Im Script eines DWs muß iw_ApplObj. wf_information2nl verwendet
    werden - nur für Applikationsweite DWs notwendig

## gf_InteropStringToDecimal

##### Argumente

-   as_value
-   string
-   ist ein Decimal- Wert der in der Interop mittels der Funktion
    Powerbuilder. DecimalToInteropstring in einen String umgewandelt
    worden ist

##### Rückgabewert

-   decimal
-   as_value als Decimal

##### Beschreibung

-   wird benötigt, weil Decimal- Argumente nicht an Interop- Methoden
    übertragen werden können (Problem von Powerbuilder mit COM)

## gf_is\[a\]

##### Argumente

-   apo\_
-   ein beliebiges Objekt, z,B. ein Window oder ein DW- Control
    -   as_classname
-   Ein Name einer Klasse
-   muss bei gf_is klein geschrieben sein, bei gf_isa (pfu_sysfun) nicht
    ( gf_IsA verwenden

##### Rückgabewert

-   boolean
-   true ( das Objekt lt. apo\_ ist von der Klasse lt. as_classname
    direkt bzw. indirekt abgeleitet false ( sonst

## gf_null2blank

##### Argumente

-   as\_
-   ein String

##### Rückgabewert

-   string
-   as\_ ist null -\> " ", sonst as\_

##### Beschreibung

-   z.B. gf_null2blank ( uf_getitem ( ... ) )

## gf_null2dec0

##### Argumente

-   adc\_
-   ein Decimal- Wert

##### Rückgabewert

-   decimal
-   adc\_ ist null -\> 0, sonst adc\_

##### Beschreibung

-   z.B. gf_null2dec0 ( uf_getitem ( ... ) )

## gf_null2num0

##### Argumente

-   al\_
-   ein Long- Wert (es kann auch integer übergeben werden)

##### Rückgabewert

-   long
-   al\_ ist null -\> 0, sonst al\_

##### Beschreibung

-   z.B. gf_null2num0 ( uf_getitem ( ... ) )

## gf_null2datmax

##### Argumente

-   adtm\_
-   ein Datetime

##### Rückgabewert

-   datetime
-   adtm\_ ist null -\> gf_dt_datmax(), sonst adtm\_

## gf_null2datmin

##### Argumente

-   adtm\_
-   ein Datetime

##### Rückgabewert

-   datetime
-   adtm\_ ist null -\> gf_dt_datmin(), sonst adtm\_

## gf_nullDattyp

##### Argumente

-   as_type
-   ein Powerscript- Datentyp wie z.B. "string", "integer", ...

##### Rückgabewert

-   any
-   Null im entsprechenden Datenty

## gf_NullTo

##### Argumente

-   aa_value
-   aa_ValueIfNull

##### Rückgabewert

-   any
-   wenn aa_value Null ist, dann aa_ValueIfNull, sonst aa_value

## gf_Replace (sys)

##### Argumente

-   as_string
-   reference
    -   as_von
    -   as_auf

##### Rückgabewert

##### Beschreibung

-   Funktion ersetzt in as_string alle Vorkommnisse von as_von durch
    as_auf

## gf_replace4WinFileName

##### Argumente

## o as_filename

## o as_ReplaceFordiddenWith

-   siehe Beschreibung
-   kann ein oder mehrere Zeichen lang sein
-   ACHTUNG bei mehreren Zeichen: kann dazu führen dass der Filename zu
    lang wird

##### Rückgabewert

-   string
-   siehe Beschreibung

##### Beschreibung

-   Funktion ersetzt in as_filename alle Vorkommnisse der in einem
    Windows- Filenamen nicht erlaubten Zeichen ( "\","/",":","\*","?",
    '"',"'", "\<", "\>", "\|" ) druch den Wert von
    as_ReplaceFordiddenWith
-   im Standardfall sollte gf_replace4WinFileNameStd aufgerufen werden

## gf_replace4WinFileNameStd

##### Argumente

## o as_filename

##### Rückgabewert

-   string
-   siehe Beschreibung

##### Beschreibung

-   ruft gf_replace4WinFileName mit as_ReplaceFordiddenWith = "!" auf

## gf_ReThrowException

##### Argumente

-   apo_where
-   Objekt, zu dem das Script, aus dem geworfen wird, gehört
    -   as_FunctionOrEventname
    -   as_context
-   Position und Umstände im Script
    -   a_exception

##### Beschreibung

-   dient dazu, eine gefangene Exception mit Kontext- Informationen zu
    versehen und gleich wieder zu werfen

## gf_Round

##### Argumente

-   adc_wert
-   der zu rundende Wert
    -   ai_nk
-   Anzahl der Nachkomma, auf die gerundet werden soll
-   muss \>= 0 und \<= 17 sein!!!
    -   as_wie \> "auf" ( immer aufrunden \> "ab" ( immer abrunden \>
        "kfm" ( kaufmännisch runden \> alle anderen Werte werden als
        'kfm' gewertet

##### Rückgabewert

-   gerundeter Wert

##### Beschreibung

-   Rundet den übergebenen Wert auf die Anzahl der Nachkommastellen und
    retourniert diese
-   Soll statt der PowerBuilder-Funktion Round() verwendet werden.

## gf_Rtrim

## `<gf_Rtrim>`{=html}

##### Argumente

-   as\_
-   reference

##### Rückgabewert

-   (None)

##### Beschreibung

-   as\_ = RightTrim ( as\_ )

## gf_RundenK

##### Argumente

-   adc\_

##### Rückgabewert

-   decimal
-   adc\_ kaufmännisch gerundet (= auf 2 Nachkommastellen)

## gf_serial

##### Argumente

-   as_table
-   atr\_

##### Rückgabewert

-   long

##### Beschreibung

-   ruft atr\_.uf_serial ( as_table, false ) auf

## gf_serial_instanz

##### Argumente

-   as_table
-   atr\_
-   ab_instanz

##### Rückgabewert

-   long

##### Beschreibung

-   ruft atr\_.uf_serial ( as_table, ab_instanz ) auf

## gf_SetNl

##### Argumente

-   as_sprache_cd
-   Sprache, in die übersetzt werden soll

##### Rückgabewert

-   (None)

##### Beschreibung

-   siehe gf_Text2nlSK\[1-9\]
-   siehe gf_GetNl

## gf_SetKontext

##### Argumente

-   as_kontext_fcd
-   siehe Beschreibung

##### Rückgabewert

-   (None)

##### Beschreibung

-   ruft cst_ApplEnv. uf_SetSharedKontext auf

## gf_SplitString

##### Argumente

-   as_in
-   der String, der gesplittet werden soll
    -   as_separator
-   das Trennzeichen
-   muss genau ein Zeichen sein
    -   as_result\[\]
-   by reference - es wird typischerweise ein leeres Array übergeben
-   Array mit den Teilen, in die as_in gesplittet worden ist

##### Rückgabewert

-   Long
-   Anzahl der Elemente in in as_result

##### Beschreibung

-   Es wird davon ausgegangen, dass as_in mehrere durch as_separator
    getrennte Teilstrings enthält - Bsp.:
-   "abc;efg;hijk"
-   ";" ist dabei das Trennzeichen, das für as_separator zu übergeben
    ist
-   gf_SplitString befüllt as_result\[\] mit diesen Teilstrings

## gf_SplitStringLen

##### Argumente

-   as_in
-   der String, der gesplittet werden soll
    -   al_teiler
-   Anzahl der zeichen nach der getrennt werden soll
    -   as_result\[\]
-   by reference - es wird typischerweise ein leeres Array übergeben
-   Array mit den Teilen, in die as_in gesplittet worden ist

##### Rückgabewert

-   Long
-   Anzahl der Elemente in in as_result

##### Beschreibung

-   Es wird nach jeden Enter bzw sinnvollerweise nach einen Blank
    getrennt doch maximal die Länge des Teilers!

## gf_Start_Job_Ab

##### Argumente

-   adc_job_snr
-   adtm_start_ab_datz

##### Rückgabewert

-   boolean

##### Beschreibung

-   Setzt das StartAb-Datum des per job_snr übergebenen Jobs.
-   UPD-Signal wird an die Jobverarbeiter ausgesendet.
-   So kann ein Job welcher per Datmax eingespoolt wurde, aktiviert
    werden.

## gf_StrCutT

...

## gf_Text2nlSK\[1-9\]

-   ruft message.iuo_ae. uf_Text2nlSk auf

## gf_ThrowException

##### Argumente

-   apo_where
-   Objekt, zu dem das Script, aus dem geworfen wird, gehört
    -   as_FunctionOrEventname
    -   as_context
-   Position und Umstände im Script
    -   as_error
-   Fehlerbeschreibung
-   hier sind durchaus NewLines sinnvoll

##### Beschreibung

-   dient dazu, eine Exception mit Kontext- Informationen zu werfen

## gf_ToColFormat

##### Argumente

-   as_column
-   name der Column, dessen Format verwendet wird
-   muss eine Column des DWOs sein
-   siehe uf_ToColFormat
    -   aa_wert
-   Wert, der auf das entsprechende Format beschnitten werden soll

##### Rückgabewert

-   any
-   der auf das entsprechende Format zurechtgestutzte Wert

##### Beschreibung

-   Beschneidet aa_wert, sodass er dem Format von as_column entspricht

## gf_UoAe

##### Argumente

##### Rückgabewert

-   cst_ApplEnv
-   iuo_ae lt. erstem zutreffendem Faktum:
-   des aktuellen Windows, falls dieses von w_ApplEnv abgeleitet ist
-   des MDI- Framewindows, falls diese schon vorhanden ist
-   leeres cst_ApplEnv

## gf_WaehrungUmr

##### Argumente

-   adc_betrag
-   Betrag in as_VonWaehrung
    -   as_VonWaehrung
-   Währung von der umgerechnet werden soll
    -   as_AufWaehrung
-   Währung auf die umgerechnet werden soll

##### Rückgabewert

-   decimal
-   adc_betrag umgerechnet in as_NachWaehrung

## Anmerkungen

-   beim ersten Aufruf in der laufenden Applikation wird ein Objekt vom
    Typ cst_waehrung erzeugt und folgendermaßen initialisiert:
-   Datenbank lt. sqlca
-   Datum Per = heutiges Datum
-   siehe cst_waehrung
-   Ändert sich eine Währung bzw. ein Kurs in der Datenbank, ist dies
    für gf_waehrung erst relevant, wenn die Applikation neu gestartet
    wird! Dazu ist noch eine bessere Lösung ausständig!

## gf_WApplObj

##### Argumente

-   apo_control
-   ein Control, z.B. ein Button
-   hier wird typischerweise this übergeben

##### Rückgabewert

-   w_ApplObj
-   Window auf dem sich das Control direkt oder indirekt befindet

## Anmerkungen

-   ist zu verwenden, wenn im Script eines Controls (z.B. Button) das
    zugehörige Window benötigt wird

## gf_WindowWName

##### Argumente

-   as_WName
-   z.B. "w_auf/umbuch"

##### Rückgabewert

-   z.B. "w_auf"
-   siehe wf_open Argument as_window

## Datenbank Funktionen

## PFU_NUMBER_TO_DISPLAYSTRING

##### Argumente

-   p_value
-   Integer

##### Rückgabewert

-   String
-   Value wird als Sting Konventiert

## PFU_DATE_TO_DISPLAYSTRING

##### Argumente

-   p_value
-   Datetime

##### Rückgabewert

-   String
-   Value wird als Sting Konventiert
-   CONVERT(varchar(25), @p_value, 25)

## PFU_STRING_TO_DISPLAYSTRING

##### Argumente

-   p_value
-   string

##### Rückgabewert

-   String
-   Value wird getrimmt zurückgegeben

## PFU_LTZ_WINAEND_DAT_1\[-5\]

##### Argumente

-   p_w_name
-   string
    -   p_dw_name
-   string
    -   p_key1
-   string
    -   p_key2
-   string
-   erst ab Funktion PFU_LTZ_WINAEND_DAT_2
    -   p_key3
-   string
-   erst ab Funktion PFU_LTZ_WINAEND_DAT_3
    -   p_key4
-   string
-   erst ab Funktion PFU_LTZ_WINAEND_DAT_4
    -   p_key5
-   string
-   erst ab Funktion PFU_LTZ_WINAEND_DAT_5

##### Rückgabewert

-   datetime
-   Datum der letzten Änderung laut History

## Anmerkungen

-   Beispiel: dbo.PFU_LTZ_WINAEND_DAT_3('w_auf_pos', 'dw_auf_pos',
    dbo.PFU_NUMBER_TO_DISPLAYSTRING(auf_pos.ein_auf_nr),
    dbo.PFU_NUMBER_TO_DISPLAYSTRING(auf_pos.fa_nr),
    dbo.PFU_NUMBER_TO_DISPLAYSTRING(auf_pos.auf_pos_nr)) last_date
-   Wenn mehr Keys gebraucht werden als Beschrieben - muss diese
    Funktionen erst gebaut werden - ist aber jeder Zeit machbar

## PFU_LTZ_WINAEND_USR_1\[-5\]

##### Argumente

-   p_w_name
-   string
    -   p_dw_name
-   string
    -   p_key1
-   string
    -   p_key2
-   string
-   erst ab Funktion PFU_LTZ_WINAEND_USR_2
    -   p_key3
-   string
-   erst ab Funktion PFU_LTZ_WINAEND_USR_3
    -   p_key4
-   string
-   erst ab Funktion PFU_LTZ_WINAEND_USR_4
    -   p_key5
-   string
-   erst ab Funktion PFU_LTZ_WINAEND_USR_5

##### Rückgabewert

-   string
-   User der letzten Änderung laut History

## Anmerkungen

-   Beispiel: dbo.PFU_LTZ_WINAEND_USR_3('w_auf_pos', 'dw_auf_pos',
    dbo.PFU_NUMBER_TO_DISPLAYSTRING(auf_pos.ein_auf_nr),
    dbo.PFU_NUMBER_TO_DISPLAYSTRING(auf_pos.fa_nr),
    dbo.PFU_NUMBER_TO_DISPLAYSTRING(auf_pos.auf_pos_nr)) last_applpers
-   Wenn mehr Keys gebraucht werden als Beschrieben - muss diese
    Funktionen erst gebaut werden - ist aber jeder Zeit machbar

## pfu_datmax

##### Argumente

##### Rückgabewert

-   Datetime
-   09.09.9999

## pfu_dt_add_day

##### Argumente

-   adtm_date
-   datetime
    -   al_tage
-   integer

##### Rückgabewert

-   datetime
-   adtm_date wird um al_tage erhöht

## pfu_dt_get_date_only

##### Argumente

-   adtm_date
-   datetime

##### Rückgabewert

-   datetime
-   liefert das Datum ohne Uhrzeit

## pfu_today

##### Argumente

##### Rückgabewert

-   datetime
-   liefert heutige Datum zurück

## Global Variables

## message.iuo_ae

-   ist ein Objekt vom Typ cst_ApplEnv für das gilt:
-   ist immer instanziert
-   ist bem Start der Applikation keinem Window zugeordnet
-   ist später das iuo_ae des dem MDI- Frame- Windows

## Unbedingt beachten!!!

## eigenes DWO für DDDW

-   die erste Column (siehe Column- Specifications im DW- Painter) muß
    die Data- Column sein!
-   Die Display- Column muß unbedingt eindeutig sein !!!

## Datenbankändernde Statements -- Transactions

-   Jede Transaction muß mit wf_TrBegin eingeleitet werden.
-   Jede Transaction muß mit wf_TrCommit bzw. wf_Rollback beendet
    werden.
-   wf_TrCommit bzw. wf_TrRollback müssen immer im selben Script wie der
    dazugehörige wf_TrBegin- Aufruf stehen!
-   Die eigentlichen Commits und Rollbacks stehen im Event CommitAll
    bzw. RollbackAll des Windows
-   Ist die Transaction auf mehrere Windows verteilt:
-   Sind die wf_Tr\*- Funktionen für jenes Window, in welchem die erste
    Datenbankändernde Aktion erfolgt, aufzurufen.
-   Es werden dann folglich die \*All- Events dieses Windows getriggert.
    Das heißt, daß hier gegebenenfalls auch die Transaction- Objekte der
    anderen Windows abzuhandeln sind. Dabei ist mittels Instance-
    Variablen dafür zu sogen, daß dies nur dann erfolgt, wenn auch
    wirklich Datenbankupdates mit diesen Transaction- Objekten erfolgt
    sind.
-   Es wird dann allerdings beim wf_TrRollback nur diese Window wieder
    in seinen ursprünglichen Zustand versetzt, falls der entsprechende
    Windowtyp dies tut (w_ApplObj)
-   die "inneren" Windows sollten im Fehlerfall mittels wf_Reset
    zurückgesetzt werden
-   Im RollbackAll- Event können auch ggf. Fehlermeldungen ausgegeben
    werden, diese können z.B. vor dem Aufruf von wf_TrRollback in eine
    Instance- Variable gestellt werden.
-   In allen Scripts von w_ApplObj und dw_ApplObj die im Zuge von
    Speichern und von löschen aufgerufen werden befindet sich das System
    bereits innerhalb einer Transaction. (wf_TrBegin wurde von System
    aufgerufen)
-   Commit bzw. Rollback wird hier vom System durchgeführt, und darf
    nicht explizit durchgeführt werden.

Wertänderung eines Feldes, welches Key eines anderen AEOs ist

Bsp.: ist kunde_cd bereits ausgefüll und fa_nr wird geändert, gibt es 3
Lösungsansätze: . nicht erlauben: protect- Expression des DW . kunde_cd
null setzen

## Any- Variable als Reference- Argument

Wenn eine Any- Variable mehrmals hintereinander bzw. in einer Schleife
als \## Reference- Argument übergeben wird, und dabei unterschiedliche
Datentypen

empfangen kann, ist dieser vor jeder Übergabe eine Jungfräuliche Any-
Variable zuzuweisen.

## posten von Statements

-   soll ein Statement nicht sofort ausgeführt werden gibt es dazu die
    post- Funktionalität
-   diese darf bei der Aplikationsprogrammierung bis auf nachfolgend
    beschriebene Ausnahmen nicht verwendet werden
-   Folgende Vorbedingungen für das "Posten":
-   das gepostete Statement führt keine Datenänderungen durch oder kann
    nur durch eine Bedieneraktion ausgelöst werden
-   meistens ist das "Posten" gar nicht notwendig, weil Funktionen wie
    z.B. dw_ApplObj.uf_JumpToField bzw. uf_SetFocus vom System aus schon
    gepostet werden. (Bei jeder entsprechenden Änderung bzw. bei Focus-
    Wechseln wird vom System die Funktion SetPresentation ausgeführt -
    im Zuge der Ausführung dieser Funktion werden z.B. auch die
    genannten zwei Funktionen ausgeführt)
-   soll das gepostete Statement vor der SetPresentation- Funktion
    ausgeführt werden, ist ihm ein Aufruf von cst_ApplEnv.uf_NextPostNr
    voranzustellen.
-   Dies ist der Normalfall beim "Posten"
-   die für den Aufruf herangezogene Instanz von cst_ApplEnv muss das
    cst_ApplEnv des Windows, dessen Presentation nach dem geposteten
    Event erfolgen soll, sein
-   In folgenden Beispielen ist "posten" notwendig
    -   Im Neu- Zweig eines w_ApplObj soll im ItemChangeAppl unter
        gewissen Umständen die Neuerfassung gecanceled werden und ein
        bestehendes AO angezeigt werden: . iuo_ae.uf_NextPost_nr() .
        post wf_DieDasInDerApplikationMacht()
-   dies Funktion wf_DieDasInDerApplikationMacht sieht etwa so aus: .
    wf_cancel() . ... . wf_besorgs() . idw_list.ScrollToRow() .
    idw_neu.uf_SetFocus()
-   Dieser Ablauf darf nur im interaktiven Betrieb erfolgen!

## AOT - AEO - Lookup

-   siehe Environment und Lookup

## Copy und Paste eines AOs

-   siehe dw_ApplObj.event SollPaste

## Rekursion bei uf_ChangeItem

-   wenn im ItemChangedAppl eines Feldes direkt oder indirekt ein
    uf_ChangeItem auf das selbe Feld (Row und Column gleich) erfolgt,
    muss unbegingt gelten:
-   der direkt oder indirekt rekursive uf_ChangeItem muss unbedingt
    "true" liefern
-   alle Statements, die nach diesem direkt oder indirekt rekursiven
    uf_ChangeItem- Aufruf stehen, dürfen nur im äußersten
    ItemChangedAppl ausgeführt werden
-   dies wird dadurch erreicht, dass spätestens nach dem rekursiven
    uf_ChangeItem- Aufruf "return true" erfolgt, wenn es sich nicht um
    das äußerste ItemChangedAppl handelt
-   die besagten Statements müssen die vom innersten uf_ChangeItem
    gesetzten Feld- Werte heranziehen (Feldwerte müssen also ggf.
    neuerlich mittels uf_GetItem ermittelt werden)
-   ob es sich um das äußerste ItemChangedAppl handelt, kann ggf. über
    eine boolsche Instance- Variable, die im äußersten ItemChangedAppl
    auf true und vor jedem Return wieder auf false gesetzt wird,
    ermittelt werden
-   Wenn der Feldwert nur einmal rekursiv umgesetzt werden muss erkennt
    man das äußerste ItemChangedAppl dadurch, dass vor dem rekursiven
    uf_ChangeItem- Aufruf returned wird, wenn aa_wert von
    ItemChangedAppl = dem an uf_ChangeItem übergebenen aa_wert ist. Dazu
    ein Bsp.:
-   Feld Kundennummer
-   alphanumerisch
-   muss einen numerischen Wert mit maximal n Stellen haben
-   soll mit fürenden Nullen auf n Stellen formatiert werden
-   Behandlung in ItemChangedAppl: . Wertebereichsprüfung, ggf. return
    false . ls_nummer = formatierten String . if ls_nummer = aa_wert
    then return true // geht zweiten ItemChangedAppl auf . uf_ChangeItem
    ( ..., ls_nummer ) // geht immer gut . z.B. Prüfung, ob nummer
    bereits vorhanden . z.B. Vorschlag Debitorennummer

## Fernsteuerung

## siehe Programmierhinweise: Fernsteuerung

## mfa- Logik

-   Objekte mit anderer MFA als diese des AOTs können nicht in einem DW
    des AOT- Windows verwaltet werden
-   Diese Bedingung kann umgangen werden, wenn die MFA- Felder mit einem
    Präfix versehen werden und dadurch die MFA- Logik nicht zur
    Anwendung kommt
-   Lookup
-   für jedes MFA- Feld, das lt. MFA- Maske des gelookupeden AOTs nicht
    zur Anwendung kommt, wird beim Lookup 0 verwendet
-   KeyToDw
-   keine Besonderheit
-   DDDW
-   für jedes MFA- Feld, das lt. MFA- Maske des gelookupeden AOTs nicht
    zur Anwendung kommt, wird beim Retrieve 0 verwendet
-   Event DddwRetrieve: Der ApplProgrammierer muss die mfa- Felder durch
    die Funktion ermitteln cst_ApplEnv.uf_Mfa lassen
-   immer wenn die Where- Bedingung ausprogrammiert ist, muss der Teil
    des Where- Strings für die mfa- Felder durch die Funktion
    cst_ApplEnv.uf_MfaWhere ermittelt werden
-   MFA- Felder werden durch die pfu_fun protected, wenn sie aufgrund
    der mfa- Logik nicht geändert werden dürfen
-   Wertebereich MFA- Felder
-   die pfu_fun verhindert, dass 0 in ein mfa- Feld gestellt werden
    kann, wenn dieses in der mfa- Maske des Windows nicht 0 ist
-   Copy + Paste
-   keine Besonderheit
-   OnDelete
-   Wenn ein DW ein AOT mit von der MFA des Windows abweichenden MFA
    verwaltet, muss der Appl- Programmierer dem im OnDelete Rechnung
    tragen (Bsp.: im Artikelstamm mit MfaMaske (100) werden Lagerplätze
    mit MfaMaske (111) angelegt -\> mfa- Felder der Lagerplätze müssen
    Präfixe haben und sind dadurch keine MFA- Felder im pfu_funschen
    Sinn mehr - der Where- string für den Delete muss vom Appl-
    Programierer ermittelt werden)
-   Objekte mit anderer MFA als diese des AOTs können nicht in einem DW
    des AOT- Windows verwaltet werden

## Jobs immer unter Anmeldung

Ausschließlich für die Jobverarbeitung gibt es eine Anmeldung 3. - die
Window- und DW- Berechtigungen sind fix Ja (intern: cst_WapplObj,
cst_DwApplObj, cst_DwApplObjCol und cst_dwApplObjCObj .
ib_BerDispAnm\[3\] und ib_BerUpdAnm\[3\]) - alle Funktional-
Berechtigungen sind lt. pfu_berecht (intern: lt. cst_berecht) - im Open-
Eventscript von w_JobObj wird die Anmeldung auf 3 gesetzt und mit dem
Erzeuger- User und der MFA des Jobs angemeldet

## Berechtigungsprüfung Window

-   Ob ein Window gestartet werden darf wird geprüft:
    -   Beim Anzeigen im Menü
    -   beim OnSetpresentation im w_ApplObj ( wenn ein Window nur
        ferngesteuert wird und nie angezeigt wird, braucht der User
        keine Berechtigung für das Window - dies gilt allerdings nicht
        für die wf_berecht\*- Funktionen - siehe auch wf_open (geerbt
        von w_ApplEnv) "privileged"

## Aufruf Ancestorscript in Eventscript

-   folgender Ablauf: (PB- Eigennamen sind Fett)

ggf. eigene Aktivitäten

ggf. return Returnwert

call super:: Eventname

ggf. return AncestorReturnValue // AncestorReturnValue ist der
Returnwert des Ancestors

ggf. eigene Aktivitäten

return Returnwert // Returnwert ist abhängig von AncestorReturnValue

-   hat den Vorteil, dass sich Argumente des Events ändern können
-   ist weniger Arbeit beim Tippen

## Applikation als Daemon (z.B. TCP- Server)

-   es muss für jedes Window, von dem aus ein w_ApplObj geöffnet wird
    iuo_ae.uf_anmeld ( Anmeldung, user, Applpers, .... ) aufgerufen
    werden
-   der Parameter Anmeldung wird sinnvollerweise mit 3 belegt
-   wird ein Window von einem Window, für das bereits uf_anmeld
    durchgeführt worden ist, aufgerufen, braucht uf_anmeld nicht mehr
    aufgerufen zu werden, weil die Anmeldung vererbt wird
-   Bei einem TCP- Server kann uf_anmeld im Initialize- Event- Script
    des von w_tcprs abgeleiteten Windows erfolgen

## Embeded SQL- Statements

## `<Embeded SQL- Statements>`{=html}

-   bei Literals (z.B. 'a', 23.7, 4711) in Embeded SQL -Statements ist
    folgendes zu beachten:
-   Datum bzw. Uhrzeit- Literals dürfen nicht verwendet werden - es ist
    eine Host- Variable heranzuziehen (z.B. :ldt_xy)
-   bei alphanumerischen Feldern
-   sind immer die einfachen Hochkommas zu verwenden
-   darf kein Leerstring verwendet werden, es muss stattdessen genau ein
    Blank zwichen den Hochkommas stehen
-   für varchar- Felder dürfen keine Literals verwendet werden
-   der Vollständigkeit halber sei nochmals darauf hingewiesen, dass der
    Dezimaltrenner ein Punkt (".") ist
-   alle String- Variablen müssen vor dem SQL- Statement mit
    uf_SqlArgBefore behandelt werden, falls die Variable nach dem SQL-
    Statement nochmals verwendet wird, muss sie vor der Verwendung
    mittels uf_SqlArgAfter wiederhergestellt werden
-   Anmerkung:
-   nachdem String- Variable immer rechtsgetrimmt sind, kann der Inhalt
    der Variablen der Leerstring sein - dieser wird z.B. in Oracle als
    NULL interpretiert
-   daher wird in uf_SqlArgBefore der Leerstring durch ein Blank ersetzt
-   siehe alphanumerische- Variable für Datenbankfelder
-   Embedded SQL- Statements müssen immer überprüft werden
-   dazu stehen in tr\_ folgende Funktionen zur Verfügung:
    -   uf_SqlException2nl
    -   uf_SqlOk
    -   uf_SqlRows
-   nachfolgen wird erläutert, wann welche Funktion zum Einsatz kommt
-   wenn bei gewissen SQL- Fehlern wie z.B. Fkey- Verletzung eine
    Benutzerverständliche Meldung ausgegeben werden soll ist
    uf_SqlException2nl zu verwenden
-   Wenn die Anzahl der verarbeiteten/gefundenen Rows nicht relevant
    ist, ist uf_SqlOk ohne das al_MinRows- Argument zu verwenden
-   Wenn ein Programmfehler oder ein durch einen Programmfehler
    hervorgerufener Datenfehler vorliegt, wenn nicht mindestens eine
    Bestimmte Anzahl von Rows verarbeitete/gefundenen worden ist, ist
    uf_SqlOk mit dem al_MinRows- Argument zu verwenden
-   sonst ist uf_SqlRows zu verwenden

## alphanumerische- Variable für Datenbankfelder

## `<alphanumerische- Variable für Datenbankfelder>`{=html}

-   char darf nicht verwndet werden
-   der Inhalt von string- Variablen muss rechts getrimmt sein
-   dies ist gewährleistet, wenn die Variable durch uf_GetItem befüllt
    worden ist
-   wird die Variable durch ein embedded SQL-Statement oder einen
    Zzugriff auf ein DW bzw. einen DS befüllt, ist sie danach explizit
    mittels RightTrim bzw. gf_Rtrim zu trimmen
-   siehe Embeded SQL- Statements

## Literals in Datawindowobject- Select

## `<Literals in Datawindowobject- Select>`{=html}

-   bei Literals (z.B. 'a', 23.7, 4711) in Embeded SQL -Statements ist
    folgendes zu beachten:
-   Datum bzw. Uhrzeit- Literals dürfen nicht verwendet werden - es ist
    eine Host- Variable heranzuziehen (z.B. :ldt_xy)
-   bei alphanumerischen Feldern
-   sind immer die einfachen Hochkommas zu verwenden
-   darf kein Leerstring verwendet werden, es muss stattdessen genau ein
    Blank zwichen den Hochkommas stehen
-   für varchar- Felder dürfen keine Literals verwendet werden
-   der Vollständigkeit halber sei nochmals darauf hingewiesen, dass der
    Dezimaltrenner ein Punkt (".") ist

## AutosizeHeight in GroupHeader

-   bei AutosizeHeight im GroupHeader muss auch unbedingt
    SupressGroupHeader=true gesetzt werden!!!

## CustomEvents - PBM_CUSTOM01 = WM_USER

-   folgende Custom- Events sind derzeit im Einsatz:
    -   PBM_CUSTOM01 = WM_USER = &H400 w_ApplEnv.HotKey
-   wird vom KeyboardGrabber verwendet
-   siehe w_ApplObj.wf_DefineHotKey
    -   PBM_CUSTOM02 = WM_USER+1 = &H401 w_ApplObj.DwRichtextHotkey
-   für RichText- Felder
    -   PBM_CUSTOM03 = WM_USER+2 = &H402 w_ApplObj.DwMdeApplHotkey
-   für dw_ApplObj.MdeApplHotkey ( MdeEnter, MdeKeyDot
    -   PBM_CUSTOM04 = WM_USER+3 = &H403
        w_ApplEnv.PcsInteropNotification
    -   PBM_CUSTOM05 = WM_USER+4 = &H404
        w_ApplMdi.WfoNotificationWindowActivity
    -   PBM_CUSTOM06 = WM_USER+5 = &H405 w_bar.NotifyRequest

## Verwendung von COM- Klassen (PCS.Interop ...)

-   es gibt prinzipiell drei Varianten COM- Klassen zu verwenden:
    -   Zugriff über eine von cst_OleWrapper abgeleitete Klasse
-   dies wird nur noch bei alten Klassen verwendet
-   ACHTUNG: keine neuen Klassen ableiten!!!
    -   Zugriff über eine von cst_OleObject abgeleitete Klasse
-   dies ist die einzige Methode für neue Klassen!!!
-   für eine aus dem PB zu verwendende COM- Klasse wird zunächst eine
    von cst_OleObject abgeleitete Klasse erstellt und über das
    FullyQualifiedClassname- Eventscript die COM-Klase definiert
-   dies wird im Allgemeinen in der pfu_fun geschehen
-   wenn es sich allerdings um eine Projekt- Spezifische COM-Klasse
    handelt, erfolgt dies im Projekt
-   Das Programm, das Funktionalitäten dieser COM-Klasse benötigt,
    instanziert sich diese Klasse und löst durch Aufruf der Funktion
    uf_ConnectToNewObject das Instanzieren der COM-Klasse aus
-   Wenn das COM-Objekt nicht mehr benötigt wird sollte es mittels
    uf_DisconnectObject vernichtet werden
-   die Funktionalitäten der COM-Klasse können auf 2 unterschiedliche
    Arten genutzt werden:
    -   direkter Zugriff auf die Members der COM-Klasse
-   dazu muss man wissen, dass cst_OleObject von OleObject abgeleitet
    ist
-   Bsp.: cst_FtpHelper:
-   unsere Variable im PB ist dann z.B. iuo_FtpHelper
-   die COM-Klasse ist Pcs.Interop.FtpHelper.FtpHelper, dort gibt es
    z.B. die Funktion Put - der Aufruf lautet dann iuo_FtpHelper.Put (
    ... )
-   so kann auch mittels iuo_FtpHelper.UserName auf das Property
    UserName der COM-Klasse zugegriffen werden
-   diese Members werden ausschließlich über die XML- Comments im Visual
    Studio dokumentiert und können dort über den Object Browser
    eingesehen werden.
-   Anmerkung:
-   Dadurch fällt der Aufwand der dreifachen Dokumentation (Studio,
    .NET-pdf-Doku + Programmiererdoku) weg
-   die Installation von Visual Studio kann angefordert werden
-   dies ist mit Norbert Pirochta abgesprochen
    -   indirekter Zugriff über Funktionen von cst_OleObject, die die
        Members der COM- Klasse verwenden
-   dies ist zu verwenden, wenn im PB eine Zwischenschicht benötigt
    wird - dies sollte eher vermieden werden und eine entsprechende
    Funktion für den PB- Zugriff im COM- Bereich realisiert werden
-   die Dokumentation erfolgt in der Programmiererdoku
-   alle Funktionen von cst_OleObject und die Members der COM- Klasse
    müssen unbedingt direkt oder indirekt unter Try/Catch aufgerufen
    werden
-   im Catch- Teil kann dann die Fehlerbeschreibung der Exception
    mittels gf_GetExceptionDetailedText ausgelesen werden
-   auch in der abgeleiteten Klasse zur Verfügung gestellte Wrapper-
    Funktionen können (und sollten ggf.) so konzipiert werden, dass sie
    unter Try/Catch aufzurufen sind
-   bei der Imlementierung der Funktionen muss dann ggf. eine Exception
    geworfen werden - dazu sollte gf_ThrowException verwendet werden
-   es kann eine gefangene Exception auch gleich wieder geworfen
    werden - dies sollte mittels gf_ReThrowException erfolgen (dabei
    werden Kontext- Informationen beigefügt)
    -   Zugriff über eine Instance- Variable vom Typ OleObject im Window
-   dies wird nur bei w_tcprs so verwendet und sollte in Zukunft
    hochgradig nicht mehr verwendet werden
-   siehe wf_CreateOleObject, wf_DisposeOleObject

## Report Header AutosizeHeight Felder dynamisch invisible

-   Johannes Poppe hat dazu folgendes gepostet:
    ProgrammiererDokuBeilagen`\Report `{=tex}Header AutosizeHeight
    Felder dynamisch invisible.msg

## Wie löst man das

## Diagnoseausgaben

-   interne DW- Columns anzeigen:
-   Die Columns sind im DW und haben keine Tab- Order
-   Im nicht Grid- DW sind die Felder einfach außerhalb des sichtbaren
    Bereichs zu plazieren.
-   Dadurch sind sie unsichtbar. Im Diagnosemodus werden einfach die
    horzontal undie vertical Scrollbar aktiviert, und man kann zu den
    Diagnosefeldern scrollen
-   dadurch werden sie vom System fix protexted
-   Im Grid- DW muß bei Diagnosefeldern in der Protect- Property-
    Expression "gf_diagnosefeld()" stehen.
    -   Inhalte von Datastores anzeigen:
-   bevor ein Datastore ausgewertet wird, besteht die Möglichkeit seinen
    Inhalt mittels uf_view() anzuzeigen. Die Anzeige erfolgt
    standardmäßig nur im Diagnosemodus.

## Editieren in Liste

folgende Aufgabenstellung: - der Anwender soll in der Liste (idw_list)
Felder ändern können - beim Zeilenwechsel in der Liste soll automatisch
gespeichert werden

folgende Lösung: - in der Protect- Property im DWO von idw_list muß in
der Expression 0 eingetragen sein ( dadurch erkennt das System, dass das
Feld editiert werden darf - Erklärung dazu: - das protect- Event wird
bei idw_list standardmäßig nicht aufgerufen - dies kommt daher, dass das
WieProtect- Eventscript von idw_list standardmäßig "p" für fix protected
liefert, wenn im DWO keine Expression vorhanden ist - ( wenn jemand das
protect- Event braucht, müsste er das WieProtect- Eventscript
übersteuern - das wurde allerdings noch nie versucht ( bitte melden,
falls es jemand braucht. - Im ItemChangedAppl der Liste muß für die
editierbaren Felder uf_changeItem auf idw_neu erfolgen (der Returnwert
sollte direkt weitergegeben werden)

## für gewisses AEO kein Lookup

Siehe cst_ApplEnv.uf_AddAotEo

## Gleichnamige Felder verschiedener AEOs lookupen

Siehe Programmierhinweise(Arten von Feldern in DWs und deren \##
Zusammenspiel(Def- Aeo- Lookedup- Feld

## ganzes DW "sperren"

Ein DW soll abhängig von z.B. einem Feld in einem (anderen) DW nicht
eingebbar sein: if feld = ... then return true/false end if - in: -
protect Event - DarfNewLine - DarfDeleteLine (nur wenn Zeilen vorhanden
sein können)

## mittels Dddw sollen mehrere Werte ermittelt werden

Folgende Situation: - Ein DDDW- DWO hat mehrer Columns, welche ins DW
gestellt werden müssen, wenn aus dem DDW eine Zeile gewählt wird. -
Bsp.: DDDW über Auftragspositionen des aktuellen Kunden und des
aktuellen Artikels Folgende Lösung: - DDDW- DWO enthält eine Computed
DW- Column - der Typ der Column ist String - Der Expression der Column
wandelt die zu liefernden Columns in String um und hängt sie mittels
gf_EncodeString zusammen. - diese Column ist die Data- Column - die
DDDW- Column im DW ist nur so groß, dass man gerade sieht, wenn der
Cursor auf ihr steht. - Im ItemChangeAppl wird der Wert der Column
mittels gf_DecodeString in seine Bestandteile zerlegt und es werden die
entsprechenden DW- Columns mittels uf_ChangeItem gesetzt. Geht einer
dieser uf_ChangeItem schief, wird false geliefert. - Siehe
Kommunikationsdaten im Bestellkopf von Tradecontrol.

bzw. das mittels DDDW auszuwählende Feld soll auch editiert werden
können

Folgende Lösung: - Es gibt eine eigene DDDW- Column für die Auswahl, die
nur dazu dient, die eigentliche Column zu befüllen - die DDDW- Column im
DW ist nur so groß, dass man gerade sieht, wenn der Cursor auf ihr
steht. - Im ItemChangeAppl wird der Wert der Column mittels
uf_ChangeItem gesetzt. Geht einer dieser uf_ChangeItem schief, wird
false geliefert. - Siehe Lagerort in der Eingangslieferscheinposition
von Tradecontrol.

Dddw in Grid, dessen where von aktueller Zeile abhängt

Folgende Situation: - Dddw in Grid - Feld des DDDWs ist die Nummer, im
DDDW wird der Matchcode angezeigt (Display- Column) - Die Where-
Bedingung des DDDW- Selects ist für jede Zeile anders Folgendes
Problem: - Die Where Bedingung des DDDWs gilt für alle Zeilen. - Wir
ändern die Where- Bedingung pro Zeile, sodaß der richtige Wertevorrat in
der Liste des DDDWs angezeigt wird. - Dadurch ist in den nicht Aktuellen
Zeilen der aktuelle Feldwert (Nummer) nicht im Wertevorrat und es kann
somit der Matchcode nicht aus dem Wertevorrat angezeigt werden. -
Dadurch wird bei den nicht aktuellen Zeilen die Nummer statt des
Matchcodes angezeigt. Folgende Lösung: - Die Lösung ist nur möglich,
wenn man statt Grid Freeform verwendet! - Man legt über das DDDW- Feld
mit der Nummer das Feld mit dem Matchcode. Es schaut lediglich der Pfeil
des DDDWs hervor. - Der Matchcode wird duch Lookup befüllt. - Weil der
Matchcode oben liegt, überdeckt er somit die bei nicht aktueller Zeile
falsche Anzeige im DDDW- Feld. - Das Matchcode- Feld darf allerdings
keine Taborder haben. - Ist das DDDW- Feld das aktuelle Feld, kommt es
in den Vordergrund, und weil es dann ja in der aktuellen Zeile liegt
stimmt auch die Anzeige. - Soll das DDDW- Feld allerdings auch durch
Mausklick auf das Matchcodefeld aktiviert werden, muß im Event
ClickedAppl folgendes Statement stehen: post uf_JumpToField ( al_row,
"DDDW- Feldname" ) ACHTUNG: - es wird empfohlen das Problem
organisatorisch zu lösen und sowohl das \_cd als auch das \_mc- Feld auf
der Maske zu haben - das \_cd- Feld kann ggf. so klein sein, dass nur
der DDDW- Pfeil sichtbar ist

## Verzweigungsbutton- Leiste

-   Unten am Window liegt ein Button über die gesamte Breite des
    Windows. Dieser muß cb_hintergrund heißen und wird vom System
    automatisch disabled.
-   Alle Verzweigungsbuttons liegen auf cb_hintergrund

## Zusätzliches DW für gleiche Update- Table des idw_neu

-   Version 1:
-   siehe dw_ApplObj.event DefineMasterMonitor
    -   Version 2:
-   Ist nur für Indiv- Ableitungen sinnvoll, wenn das DWO von idw_neu
    nicht angegriffen werden soll
-   Die Columns des Zusatz- DW's
-   sind auf idw:neu nicht vorhanden
-   können in der Datenbank null sein, oder haben einen Datenbank-
    Default- Wert
-   zusätzliches DW:
-   ist kein Detail von idw_neu
-   darf_newline und darf_deleteline liefern false
-   SollPaste liefert false
-   OnDelete darf nicht löschen und muss true liefern
-   Problem: Die Felder des Zusatz- DW's können nicht kopiert werden
-   Vorteil: man brauch DWO von idw_neu nicht zu ersetzen

## Befüllen von Columns aus anderen DWs

-   siehe dazu dw_ApplObj.event RetrieveSetConst

## Befüllen von Columns mit Konstanten

-   siehe dazu dw_ApplObj.event RetrieveSetConst

## Lookup funktioniert nicht

siehe Environment (AOT, AEO) und Lookup -- besonders die fett gedruckten
\## ACHTUNG- Punkte

## Lookup von AEOs ohne eigener Key- Column

-   Der Lookup kann im ItemChangedAppl- Script bei der Behandlung eines
    der impliziten Keyfelder über die Funktion uf_lookup ausgelöst
    werden.

## w_ApplObj: DWO mit Gruppen - Detail nicht anzeigen

-   Siehe z.B. Tradecontrol Umsatzabfrage (w_artums)
-   im Definition- Event: uf_NoFocusBorder() aufrufen
-   im DWO muß es Computed- Column namens "hiderow" geben:
-   muß bei der ersten Row der Gruppe 'f' und sonst 't' sein

dw_ApplObj: bei Retrieve kein lookup auf AEO, weil dieser zu früh
erfolgt

-   Siehe z.B. Reliste: Verpackungsauftrag im Auftragskopf Problematik
    dort:
-   in Firma steht Verpackungsartikel
-   im Env des Auftrags steht Verpackungsartikel, dieser ist allerdings
    nicht in der Tabelle auf vorhanden
-   Beim Retrieve des Auftrags wird augrund der umgekehrten AOT-
    Reihenfolge der Verpackungsartikel vor der Firma gelookuped. Zu
    diesem Zeitpunkt ist natürlich verp_artik_cd noch null, weil
    verp_artik_cd ja erst durch den Lookup der Firma befüllt wird.
-   Lösung: im RetrieveEndAppl- Script wird uf_lookup ( 1, "verp\_",
    "artik", true ) aufgerufen

## Copy und Paste eines AOs

-   siehe dw_ApplObj.event SollPaste

Initialisieren von Instance- Variablen, die sich auf das AOT beziehen

-   hierzu wird ggf. ein neues Event im Window eingeführt
-   dieses wird beim wf_new und beim Retrieve von idw_neu (aber nicht
    beim F5) aufgerufen
-   derzeit muss es an 2 Stellen erfolgen:
    -   im default- Eventscript von idw_neu
    -   im RetrieveEndAppl- Eventscript von idw_neu, aber nur, wenn
        ac_zweig = 'r'

unerwünschte Schleifen bei Feldern, die sowohl eingegeben werden als
auch \## berechnet werden

hierzu ein (bewusst vereinfachtes) Beispiel: - folgende Felder mit den
zugehörigen Aktivitäten bei Feldänderung: - vkp ( db_prz := (vkp - estp)
/ vkp \* 100 - db_prz ( vkp := 100 \* estp / ( 100 - db_prz ) - estp -
es können alle Felder ausser espt gesetzt werden - aufgrund von
Rundungsdifferenzen läuft das System nach einer Eingabe jetzt solange im
Kreis, bis es eine Kombination vkp zu db_prz gibt, die in beiden
Richtungen gerechnet zusammenpasst - dies kann, wenn das ganze noch
komplexer ist durchaus über 10 Sekunden dauern! - die Felder können auch
über Fernsteuerung gesetzt werden (( ab_ItemChangedField abfragen hilft
nichts!) - Lösung: für db_prz gibt es 2 Felder: - ein_db_prz ( vkp :=
100 \* estp / ( 100 - db_prz ) - ist_db_prz ( keine Aktivität - vkp (
ist_db_prz := (vkp - estp) / vkp \* 100 - Nachteil der Lösung: es wird
zusätzlicher Platz auf der Maske benötigt - Lösung dafür: Auf der Maske
ist ein Feld, logisch gibt es aber 2 Felder: - db_prz ( Maskenfeld -
ein:db_prz ( logisches Feld - ist:db_prz ( logisches Feld siehe dazu:
uf_DefineEinIstCol - 2 Beispiele:

\[pic\]

\[pic\]

Es sollen 2 Grid- DWs, deren Db- Tabellen eine 1:n- Beziehung haben im
\## Verbund sein

-   siehe dw_ApplObj.uf_filter

wird durch Änderung eines Feldinhalts das Protect des nachfolgenden
Feldes \## false

-   dann wird das nachfolgende Feld bei TAB trotzdem übersprungen
-   dies kann folgendermaßen behoben werden:
-   im TabMove- Eventscript wird bei dieser Bewegung ein uf_JumpToField
    auf da übersprungene Feld "abgefeuert" Bsp.: if as_fromto =
    "wgrart_cd-wgr_mc" then uf_JumpToField(1, "wgr_nr") end if

## Liste soll unsichtbar sein

-   Dies wird durch "return false" in den Eventscripts von
    dw_ApplObj.DarfEnable und DarfVisible realisiert.

## Übersetzung

-   Applikationswindows
-   Windowtitle
-   in der Windowverwaltung: Windowbezeichnung und Kurzbezeichnung
    -   RegisterTexte
-   im Ansicht- Menü gibt es einen Menüpunkt Übersetzenmodus
-   dieser ist nur aktiv, wenn die Anmeldungssprache nicht Deutsch ist
-   wenn der Übersetzenmodus eingeschaltet ist, kann mit der rechten
    Maustaste auf den Registertext geklickt werden und dann der Text in
    derSprache lt. Anmeldung eingegeben werden. Die Eingabe wird mit TAB
    abgeschlossen und ist damit gespeichert. Die Eingabe kann mittels
    ESC- Taste abgebrochen werden
    -   Schaltflächentexte
-   wie Registertexte
    -   Grid- Spaltenüberschriften
-   wird über da Gridschema gelöst (dieses hat als Key unter anderem die
    Sprache)
    -   Nicht- Grid- Feldtexte
-   es muss die Feldtext- Feld- Zuordnung erfolgt sein
-   dies erfolgt folgendermaßen: . mittels Menüpunkt Feldzuordnungsmodus
    im Ansicht- Menü den Feldzuordnungsmodus einschalten . mittels Drag
    and Drop den Feldtext auf das Feld, dem er zugeordnet werden soll,
    ziehen . damit ist die Zuordnung gespeichert . wird der Feldtext
    mittels Drag and Drop aus dem Window hinausgezogen, wird die
    Zuordnung wieder gelöscht
-   diese ist unabhängig von der Sprache
-   diese wird in pfu_dwo_lablemap gespeichert, der Key dabei ist
    dwo_name, col_name
-   die Übersetzung der Feldtexte erfolgt analog zu den Registertexten
    -   Menü
-   die Windows- Menüpunkte werden über die Windowsmenü- Verwaltung
    übersetzt
-   hier kommt man beim Retrieve automatisch in den Zustand Update, wenn
    nicht für alle Windowsmenüpunkte für alle angelegten Sprachen eine
    Row in der DB vorhanden ist
-   dies geschieht auch beim Cancel
-   beim Speichern werden die neu entdeckten Menüpunkte gespeichert
    -   Winmodus
-   es ist geplant die Übersetzung in pfu_win_ctrltxt zu verspichern
-   noch nicht realisiert (Releasenote Nr. 1188)
    -   Systemwindows
    -   w_ApplAnmeld
-   wird vorerst nicht übersetzt
    -   w_ApplEnvOpen (das Menü- Fenster)
-   die Buttons wie bei einem Applikationswindow
-   die Wörter "Fensterauswahl" und "Anmeldung" mittels Text2Nl
    durchgeführt
-   Die Übermenüpunkte werden über das Menüpunktverwaltungsmenü
    übersetzt
-   die eigentlichen Menüpunkte - also die Windows - werden in der
    Windowverwaltung übersetzt
-   es wird die Windowbezeichnung herangezogen
    -   w_ApplObjQuery
-   die Buttons wie bei einem Applikationswindow
-   die Feldbezeichnungen in der Queryfelderverwaltung
    (pfu_win_qmap_col)
-   das Wort "auswählen" im Windowtitle über Text2Nl
    -   w_spoolin
-   ist ein w_ApplObj ( wie Applikationswindow
    -   w_ApplObjSort
-   Alle Übersetzungen werden im Open- Event mittels Text2Nl
    durchgeführt
    -   Windowtitle
-   gibt es derzeit keinen
    -   Spaltenüberschriften
    -   der Text "Ziehen Sie bitte die ..."

Datawindow, das auch im Zustand Empty retrieved und eingebbar ist

-   Lösung: \> DW von dw_ao_immerda ableiten \> dw_ApplObj.event SyncDw
    so befüllen, wie bei dw_ao_immerda
-   ist nur für tc- und tci- Klassen vorgesehen
-   bitte vorher rückfragen

## Spoolinfenster von w_ApplObj aus aufrufen

-   Bsp.: es soll das Spoolinfenster für w_lst_bsp aufgerufen werden,
    wobei
-   Firma und Artikel sollen konstant gesetzt werden
-   folgende Programmcode:

iuo_ae.uf_SetCallConst ( "fa_nr" ) iuo_ae.uf_SetCallConst ( "artik_cd" )
wf_open ( false, "w_spoolin", true, "w_lst_bsp", "","tw", "" )

-   konstant setzen muss natürlich nicht erfolgen
-   wenn konstant gesetzt wird, müssen natürlich für das eingespoolte
    Window die entsprechenden Queryfelder vorhanden sein

Textzeilen mit Richtext aus einer fremden Tabelle in ein DW bringen

-   Bsp.: Auftragsposition: nach Eingabe der Artikelnummer sollen die
    Textzeilen von diesm Artikel vorgeschlagen werden
-   dies passiert bisher meistens mittels uf_GetItemIntoNewline - dies
    ist allerdings bei Richtex-Feldern langsam
-   folgende Methode ist erheblich schneller - die Erklärung erfolgt
    anhand des obigen auf_pos- Beispiels
-   der Select des DWOs ist ein Union aus:
    -   Select "at" zweig, ... from artik_txt
    -   Select "ap" zweig ... from auf_pos
-   im ItemChangedAppl erfolgt ein uf_Refresh
-   dabei wird im RetrieveByKey dafür gesorgt, dass nur der "at"- Zeig
    Rows bringt
-   nach dem Refresh erfolgt ein uf_SetItemStatusNew ( PB betrachtet die
    Zeilen jetzt als neue Zeilen
-   Beim "normalen" Retrieve wird im RetrieveByKey dafür gesorgt, dass
    nur der "ap"- Zeig Rows bringt
-   dass die pfu_fun für die underschiedlichen Tabellen und Columns der
    Union- Zweige die Richtexte aus der Datenbank übernehmen kann, muss
    das Applikationsprogramm mittels des BeforeSelectRichtext- Event-
    Scripts die pfu_fun unterstützen - siehe dort.

## Lizenz- Key ermitteln

-   siehe pfu_fun_db.doc
    -   pfu_kennsatz

## Zugriff auf OLE-Objekte

-   Der Zugriff auf OLE-Objekte sollte immer mittels einer von
    cst_OleWrapper (sys) abgeleiteten Klasse erfolgen !!! (Siehe dort !)
-   ACHTUNG - bitte Rücksprache mit hmp - die Doku für die letztgültige
    Version fehlt (leider) noch

## Zugriff auf ein Webservice

-   dies funktioniet nur vernünftig, wenn man mittel localhost arbeiten
    kann . . Webservice muss laufen . New - Register Project - Web
    Service Proxy . folgende 2 Masken ausfüllen: \[pic\]
-   Proxy name prefix:
-   der Klassenname jeder Proxy- Klasse := `<dieses Präfix>`{=html} +
    WCF- Klassenname \[pic\] . \[Services\]- Button drücken . in
    folgender Maske alle WCF- Klassen, die verwendet warden sollen
    anhaken \[pic\] . Project deployen -- R-Maus-Menü auf \`ws_test´--
    Deploy \[pic\]
-   sieht danach folgendermaßen aus: \[pic\] . Soap- PB-Extension-
    Klassen importieren . R-Maus-Menü auf wcftest.pbl . Import PB
    Extension ... . C:`\Program `{=tex}Files
    (x86)`\SybasePb1126`{=tex}`\Shared`{=tex}`\PowerBuilder`{=tex}`\pbwsclient`{=tex}126.pbx
    auswählen \[pic\] . jetzt kann die Proxy- Klasse verwendet werden:
    SoapConnection lsc_Example example luo_example examplerecord1
    luo_record

lsc_Example = create SoapConnection
lsc_Example.CreateInstance(luo_example, "example")

luo_example.PutInfo("habedere") messagebox ( "das kommt vom WS:",
luo_example.GetInfo() ) luo_example.Set_Info("die Sonne Scheint") //
Property setzen bin mir nicht sicher, ob das so geht messagebox (
"WS.GetInfo:", luo_example.GetInfo() ) messagebox ( "WS.Property Info:",
luo_example.Get_Info() )

luo_record = create example_examplerecord1 luo_record.s = "hahaha"
luo_record.dt = datetime ( today() ) luo_record.dtspecified = true
luo_record.dc = 17.4 luo_record.dcSpecified = true luo_record.i32 = 4711
luo_record.i32Specified = true

luo_example.PutRecord(luo_record)

luo_record = luo_example.GetRecord()

## Programmierhinweise

## Environment (AOT, AEO) und Lookup

-   es wird davon ausgegangen, dass grundsätzliches Wissen über AOT und
    AEO vorhanden ist
-   siehe uf_AddAot, uf_AddAotEo, uf_AddAotEoF

Folgendes Beispiel: AOT auf_pos und sein Environment (die AEOs)

-   auf_pos

-   (ein\_)auf

-   (ein\_)kunde ( kunde

-   (ein\_)fa ( fa

-   (ein\_)versart ( ein_versart

-   (ein\_)(kunde\_)adr ( kunde_adr

-   (ab\_)auf

-   (ab\_)kunde ( kunde

-   (ab\_)fa ( fa

-   (ab\_)versart ( versart

-   (ab\_)(kunde\_)adr ( kunde_adr

-   kunde

-   fa ( fa

-   versart ( versart

-   (kunde\_)adr ( kunde_adr

-   fa

-   (fa\_)adr ( adr

-   artik_lag

-   fa ( fa

-   artik ( artik

-   lag ( lag

-   artik

-   fa ( fa

-   lag

-   fa ( fa

-   versart

-   ein_versart

-   kunde_adr

-   adr

-   Anmerkungen zur Notation:

-   die Präfixe der AEOs stehen in Klammer (z.B. ein_auf)

-   die Pfeile werden weiter unten beschrieben

-   Die pfu_fun ermittelt für jedes AEO in der 3. Einrückungsebene ein
    passendes AEO in der 2. Einrückungsebene (die erse Ebene ist
    auf_pos)

-   Dies ist jenes AEO für das gilt:

-   hat das gleiche AOT wie das AEO in der 3. Ebene

-   das Präfix muss rechtsbündig im Praefix des AEOs in der 3. Ebene
    vorkommen

-   es ist das AEO mit dem längsten Präfix, das die obigen Bedingungen
    erfüllt

-   Es müssen also die Präfixe nicht vollständig übereinstimmen, dies
    wird Weglassregel genannt.

-   Die Pfeile (() im obigen Beispiel zeigen jeweils an, welchem AEO
    der 2. Ebene ein AEO der 3. Ebene zugeordnet wird/ist

-   Dem AEO versart sind zwei Sub- AEOs zugeordnet:

    -   ab_auf.versart
    -   kunde.versart Demnach würde versart_cd sowohl vom Lookup von
        Kunde als auch vom Lookup von ab_auf gesetzt werden. Es können
        jetzt allerdings kunde und auf einen unterschiedlichen
        versart_cd haben. Es muß also ein versart_cd gewinnen. Dies
        geschieht folgendermaßen:

-   Beim Retrieve:

-   Wurde eine Column bereits vom Lookup befüllt, wird sie nicht
    überschrieben

-   Das Lookupen der AEOs erfolgt absteigend nach AOT- Nummer es kommt
    also auf vor kunde, auf_pos vor artikel

-   In folgender Konstellation ist diese Reihenfolge nicht günstig --
    dazu ein Beispiel:

-   In eine DW in w_auf gibt es folgende Felder:

    -   spesen_auf_pos_nr (Table- Feld) - in Tabelle auf
    -   spesen_artik_cd (Lookedup- Feld) - wird von auf_pos gelookuped

-   auf Grund der oben beschriebenen Reihenfolge wird jetzt als erstes
    der Lookup für auf_pos durchgeführt ( Lookup für spesen_artik_cd

-   allerdings ist spesen_artik_cd noch null, weil ja der Lookup für
    artikel noch nicht erfolgt ist, und es erfolgt somit de facto kein
    Lookup

-   mit folgendem Workaround kann das Problem umgangen werden:

-   im RetrieveEndAppl wird uf_LookupAfterLock für spesen_artikel
    aufgerufen

-   uf_LookupAfterLock ist deshalb sinnvoll, weil er die Felder nicht
    mittels uf_ChangeItem setzt

-   Beim Lookup aus ItemChangedAppl:

-   Bei Kaskadierenden Lookups wird ein Feld durch den äußersten Lookup
    befüllt , wenn es auf verschiedenen Lookupebenen vorhanden ist.
    Bsp.: Auftragsposition lookuped Auftrag, dieser lookuped Kunde,
    beide haben Versandart --\> Versandart von Auftrag soll herangezogen
    werden, das heißt, daß die Versandart des Kunden von der des
    Auftrags überschrieben wird.

-   innerhalb einer Lookup- Ebene wird die Reihenfolge der Befüllten
    Felder durch SetLookedupOrder bestimmt

-   dem AEO ein_versart ist das AOE ein_auf.versart zugeordnet

-   gäbe es nicht das AEO ein_versart:

-   wären sowohl das AEO versart des AEOs ein_auf als auch das AEO
    versart des AEOs ab_auf dem AEO versart zugeordnet.

-   Diese Zuordnung könnte dadurch untebunden werden, dass beim
    uf_AddAotEo von ein_auf dem Parameter ab_SubPraefixMussGleich true
    übergeben wird.

-   die Versandart von ein_auf wäre dann sozusagen im Environment von
    auf_pos nicht vorhanden

-   es würde dann allerdings auch keine Zuordnung für kunde und adr
    geben

-   für fa allerdings würde es eine Zuordnung geben, weil fa
    Keybestandteil von auf ist

-   Wenn es nur um das Setzen von versart_cd durch den Lookup von
    ein_auf geht, kann dies durch return false beim Event SollLookedup
    verhindert werden (siehe Key- Felder, die vom Lookup befüllt werden)

-   dem AEO fa sind viele Sub- AEOs zugeteilt

-   zwischen ein_auf und ab_auf gibt es keine Priorität und es gewinnt
    zufällig einer der beiden!

-   dies ist egal, weil beide auf sowieso die selbe fa haben müssen

-   Diese Zuordnungen haben jetzt folgende Auswirkungen auf:

    -   Key- Beschaffung für
    -   Öffnen (Show)
    -   Lookup

-   Bsp.: der Key-Bestandteil fa von ein_auf wird durch die
    Weglassregel-bedingte Zuordnung (fa statt ein_fa) von der fa der
    auf_pos befriedigt (durch das Feld auf_pos.fa_nr)

    -   Befüllung von Key- Feldern irgend eines AOTs durch den Lookup

-   Bsp.: beim Lookup von ein_auf wird die Column auf.kunde_cd nicht in
    das Feld ein_kunde_cd sondern Weglassregel-bedingt in das Feld
    kunde_cd gestellt

-   ACHTUNG: wenn es für das AEO eines solchen Key- Feldes kein AEO, dem
    dieses AEO zugeordnet ist, gibt, wird es wie ein nicht-Key-Feld
    behandelt. ( BSsp.:

-   artik hat ein AEO (hpt\_)lief

-   auf_pos hat kein AEO mit AOT lief

-   ( artik.hpt_lief_cd wird nicht als Keyfeld behandelt

-   ACHTUNG: z.B. folgender Fall:

-   unsere auf_pos bekommt noch folgende AEOs:

    -   (alternativ\_)artik
    -   (alternativ\_)artikgrp ( artikgrp
    -   artikgrp

-   beim Lookup von alternativ_artik werden jetzt u.a.folgende Felder im
    DW befüllt, wenn sie vorhanden sind:

    -   artikgrp

-   weil die artikgrp von alternativ_artik Weglassregel-bedingt der
    artikgrp der auf_pos zugeordnet wird und der Feldname für den Lookup
    sich folgendermaßen zusammenetzt:

    -   präfix von artikgrp in auf_pos ( leer
    -   Keyfeld von artikgrp ( artikgrp_cd
    -   alternativ_artik\_\_artikgrp

-   wie nachfolgend beschrieben

-   das DW- Feld alternativ_artikgrp_cd wird demnach vom Lookup nicht
    befüllt!!!

-   das DW- Feld alternativ_artik_mc würde allerdings befüllt werden

-   ist ja kein Key-Feld (wie nachfolgend beschrieben)

-   ACHTUNG: Diese Zuordnungen haben keine Auswirkung auf die Befüllung
    durch den Lookup von Feldern, die kein Keyfeld irgend eines AOTs
    sind bzw. für deren AEO es keine solche Zuordnung gibt

-   die zu befüllenden Felder müssen in diesem Fall einer der beiden
    folgenden Nomenklaturvorschriften genügen: \>
    `<Präfix des AEOs>`{=html} +
    `<DB-Columnname im AOT des AEOs>`{=html}

-   Bsp.: ein_auf_dat

-   für Table- Feld und Lookedup- Feld \> `<Präfix des AEOs>`{=html} +
    `<Name des AOTs des AEOs>`{=html} + "\_\_" + `<DB-
    Columnname im AOT des AEOs>`{=html}

-   Bsp.: ein_auf\_\_auf_dat

-   für Def- Aeo- Lookedup- Feld

-   weiters zum Lookup:

-   ab pfu_fun040616:

-   fa ist Keybestandteil von kunde ( beim Lookup von fa wird Kunde
    ausgenullt

-   das AEO artik_lag hat keine eigene Key- Column (siehe dazu
    uf_AddAot, uf_AddAotEo) ( beim Lookup von artik und beim Lookup von
    Lag wird artik_lag gelookuped, wenn artik_cd und lag_cd nicht null
    sind - beim Lookup von fa geschähe dies auch, wenn nicht wie oben
    beschrieben vorher artik_cd und kunde_cd ausgenullt würden

-   das Setzen der Columns erfolgt:

-   beim Retrieve mit SetItem

-   sonst mit uf_ChangeItem

-   pro Applikationsrelease (Tabelle pfu_applrel) sind alle Datastores
    für die Lookups in der DB gespeichert ( wenn ein neues Feld, das vom
    Lookup befüllt werden muss, dazu kommt, muss der Applikationsrelease
    erhöht werden (( uf_AddRelease)

-   Anmerkung für pfu_fun- Programmierung:

-   siehe Kommentar zu Beginn in cst_ApplEnv.uf_aotaeolookupds

## Arten von Feldern in DWs und deren Zusammenspiel

-   folgendes gilt nicht für idw_list

## Platzhalter- Feld

Definition: - Für ein Platzhalter- Feld wird im SQL- Statement ein
Literal oder eine Dummy- Column (dazu gibt es die Datenbanktabelle
pfu_selkonst) selektiert. - Es wird vom System aufgrund des DB- Namens
im DWO erkannt siehe dazu dw_ApplObj.Event ColSelectLiteral - Es wird
vom System nach dem Retrieve zunächst auf null gesetzt. - Die
verschiedenen Arten von Platzhalter- Feldern werden nachfolgend
beschrieben

Nomenklatur: \## DB- Name = beliebig + "\_"

## DW- Name = beliebig

## Table- Feld

Definition: - ein Feld im SQL- Statements des DWOs, welches kein
Platzhalter- Feld ist

## Lookedup- Feld

Definition: - Ein Lookedup- Feld ist ein Platzhalter- Feld - Ein
Lookedup- Feld ist ein Feld, welches durch den Lookup befüllt wird - Ein
Lookedup- Feld wird nur durch den Lookup gesetzt - Anmerkung: Es kann
auch eine updatable Column durch Lookup befüllt werden, ist aber
trotzdem kein Lookedup- Feld!

Nomenklatur: \## DB- Name = beliegig + "\_"

## DW- Name = Präfix + Columnname lt. DB

## Def- Aeo- Lookedup- Feld

Definition: - Ein Def- Aeo- Lookedup- Feld ist ein Lookedup- Feld mit
folgenden Abweichungen: - Hier wird über den DW- Columnname das AEO,
durch welches das Feld gelookuped werden soll, definiert

Wann verwenden: - Bsp.: im Auftragskopf ist ein Kennzeichen x_kz
gespeichert, welches vom Kundenstamm übernommen wurde. - In der
Auftragsposition wird dieses Kennzeichen aus dem Auftragskopf
gelookuped. - Wird in der Auftragsposition der Wert aus dem Kundenstamm
benötigt, so erfolgt dies über ein Def- Aeo- Lookedup- Feld

Nomenklatur: \## DB- Name = beliegig + "\_"

DW- Name = AeoName + "*" + "*" + DB- Columnname (AeoName = Präfix +
AotName) z.B. kunde\_\_versart_cd

## SQL- Feld

Definition: - Ein SQL- Feld ist ein Platzhalter- Feld - Es verhält sich
wie ein Lookedup- Feld, allerdings muß der Lookup in der Aplikation
ausprogrammiert werden (Select).

Behandlung: - wird mittels einer Aktion über ein SQL- Statement belegt

Nomenklatur: \## DB- Name = beliebig + "\_"

## DW- Name = Feldname + "\_sq"

## Updated- Platzhalter- Feld

Definition: - Ein Updated- Platzhalter- Feld ist ein Lookedup- Feld oder
ein SQL- Feld - Ein Updated- Platzhalter- Feld entspricht einer Column
in einer DB- Tabelle - auf die dem Updated- Platzhalter- Feld
entsprechende DB- Column wird beim Speichern abhängig von anderen
Feldern ein Update durchgeführt - ein Updated- Platzhalter- Feld wird im
Allgemeinen nicht angezeigt - dafür gibt es ein eigenes Display- Feld

Behandlung: - zusätzlich zur Behandlung, die sich aus Lookedup- Feld
bzw. SQL- Feld ergibt muss der Wert im DwApplObj.AfterUpdateOk neu
gesetzt werden - dazu muss das DarfChangeItemInDisplay- Eventscript für
ein Updated- Platzhalter- Feld- Feld true returnen - wenn es ein
zugehöriges Display- Feld gibt, muss es lediglich auf dessen Wert
gesetzt werden - dies darf nicht in einer Aktion erfolgen

Beispiel: - siehe bei Display- Feld

## Display- Feld

Definition: - Ein Display- Feld ist ein Platzhalter- Feld - Es
entspricht einer Column einer Table, welche nicht die Update- Table des
DWs ist. - es tritt immer gemeinsam mit einem Updated- Platzhalter- Feld
auf - Es enthält den Wert, welcher nach dem Speichern in dieser
Datenbankcolumn stünde, wenn das DW im jetzigen Zustand gespeichert
würde. - Diese Column kann allerdings auch eine Virtuelle Redundante
Datenbankcolumn sein (z.B. Bestellwert einer Bestellung)

Behandlung: - ein Display- Feld wird von einer Aktion gesetzt

Nomenklatur: \## DB- Name = beliegig + "\_"

## DW- Name = Feldname + "\_di"

Beispiele: - Bestellwert der gesamten Bestellung in der
Bestellposition: - ist in der Datenbank eine virtuell redundante
Column - es gibt ein SQL- Feld: best_wert_sq - es gibt ein Display-
Feld: best_wert_di - aktive abhängig Felder: - best_wert_sq (SQL-
Feld) - best_pos_wert (Platzhalter- Feld) - Offene Bestellmenge über
alle Bestellungen lt. Artikelstamm in der Bestellposition: - es gibt ein
Lookedup- Feld sum_best_off_mg (Artikel) - es gibt ein Display- Feld
sum_best_off_mg_di - aktive abhängig Felder der Aktion, die das Feld
setzt: - best_off_mg (Updatetable- Feld) - sum_best_off_mg (Lookedup-
Feld)

## DB- Feld

Definition: - Wird in einem DW für eine updatable- Column der in der
Datenbank gespeicherte Wert benötigt (z.B. um die Differenz zwischen
gespeichertem und zu speicherndem Wert zu ermitteln), ist dazu eine
zusätzliche DW- Column, welche genau dieser updatable- Column
entspricht, einzuführen. Eine solche zusätzliche Column wird DB- Feld
genannt. - DB- Felder gibt es ausschließlich für Updatetable- Felder.
Eine Ausnahme stellen virtuelle Redundante Columns in der Datenbank dar
(z.B. Offene Menge der Auftragsposition).

Bemerkung: - ein DB- Feld ist ein Statisches Feld ( es darf kein aktives
abhängig Feld einer Aktion sein - ein DB- Feld ist ein Table- Feld

Behandlung: - Ein DB- Feld ist im Default- Event- Script auf 0 zu
stellen, wenn damit gerechnet wird. - Ein DB- Feld ist im
DwApplObj.AfterUpdateOk- Event- Script und im RetrieveEndAppl- Event-
Script auf den Wert der entsprechenden Column zu setzen. - dazu muss das
DarfChangeItemInDisplay- Eventscript für ein DB- Feld true returnen -
Bei RetrieveEndAppl darf dies allerdings nur dann erfolgen, wenn das
Argument ab_RetrievedDw = true ist. - das Setzen im RetrieveEndAppl-
Event- Script kann und soll weggelassen werden, wenn der SQL- Column
Expression den Wert der entsprechenden Column hat - Beispiele: -
"best_mg - lief_mg off_mg_db" - "best_mg best_mg_db" - In einem DW, in
dem Zeilen gelöscht werden dürfen, ist das DB- Feld bei Änderung des
Keys der Zeile, wenn dieser vollständig ist, mit dem Wert aus jener
gelöschten Zeile, die den selben Key wie die aktuelle Zeile hat, falls
eine solche existiert, zu belegen, ansonsten mit 0. Dazu gibt es
folgende Funktionen: - uf_GetDeletedRow - uf_GetDeletedItem - Zu einem
DB- Feld darf es keine Behandlung (case "\*\_db") im ItemChangedAppl
Eventscript geben - zum Ermitteln des Wertes eines DB- Feldes darf auf
keinen Fall ein anderes DB- Feld herangezogen werden!

Nomenklatur: \## DB- Name = beliebig + "\_db"

## DW- Name = Columnname + "\_db"

## Statisches Feld

Definition: - Ein Statisches- Feld kann sich nicht ändern, während das
Window im Satus Update bzw. Insert ist - die einzigen Ausnahmen dazu
sind: - das Setzen eines DB- Feldes auf den Wert 0 im default-
Eventscript - das entsprechende Setzen des Feldes im RetrieveSetConst-
Eventscript - Kopieren des Feldinhaltes aus einem anderen DW, das nicht
im Status update bzw. insert ist, im default- Eventscript bevor die
Aktion das erste mal aufgerufen wird - Das Setzen eines Statischen-
Feldes darf nicht voraussetzen, daß ein Nicht- Statisches- Feld gesetzt
ist. - ein DB- Feld ist ein Statisches Feld - ein indirekt Statisches
Feld ist ein Statisches Feld

## indirekt Statisches Feld

-   ist ein Feld, dessen Setzung nur in Abhängigkeit von Statischen
    Feldern erfolgt
-   ein indirekt Statisches Feld gilt ebenfalls als Statisches Feld

## Aktion

Begriffsdefinitionen:

## Denitition der Aktion selbst

-   Eine Aktion ist ein Programmteil, der Aktivitäten in einem Master-
    Detail Verbund von Datawindows abhandelt
-   die Aktion greift lesend (uf_GetItem) nur auf Felder des Typs
    abhängig Feld zu
-   es muss allerdings keine abhängig Felder geben
-   die Aktion greift schreibend (uf_ChangeItem) nur auf Felder des Typs
    geändert Feld zu
-   es muss allerdings keine geändert Felder geben
-   eine Aktion ist einem Datawindow zugeordnet (( DW der Aktion)
-   eine Aktion darf ausschließlich folgende schreibenden Aktivitäten
    durchführen:
    -   Setzen der geändert Felder
    -   Zeilen anlegen (uf_NewLine, uf_GetItemIntoNewline)
    -   Zeilen löschen (uf_DeleteLine)
-   eine Aktion liefert true oder false

DW der Aktion

-   das Datawindow welchem die Aktion zugeordnet ist

## Master DW der Aktion

-   das Master- DW des DW der Aktion

## abhängig Feld

-   ein Feld von dessen Inhalt die Aktion abhängig ist
-   abhängig Felder der Aktion sind alle Felder, auf die in der Aktion
    ein Getitem gemacht wird
-   Felder, die Kopien von Feldern eines anderen DWs im selben Master-
    Detail- Verbund sind, dürfen keine abhängig Felder sein. Statt einem
    solchen Feld muss das kopierte Feld als abhängig Feld herangezogen
    werden. Dazu als Bsp. die Lagernummer im Lagerbewegungs- DW in der
    Warenzugangsposition:
-   diese wird vom idw_neu kopiert
-   diese wird bei jeder neuen Zeile gesetzt und würde dann
    unnötigerweise Aktionen auslösen
-   daher sollte das abhängig Feld der Aktion die Lagernummer aus
    idw_neu sein
-   es gibt 2 Arten von abhängig Feldern

## passives abhängig Feld

-   ist ein abhängig Feld
-   genügt einer der folgenden Bedingungen: \> ist ein Statisches Feld
    \> ist ein Lookedup- Feld für das gilt:
-   es gibt ein Feld, das genau einmal bei der Neuanlage gesetzt wird
    und dann nicht mehr geändert werden kann V \> der Lookup wird von
    diesem Feld ausgelöst \> der Lookup wird von einem Lookedup- Feld,
    das der hier beschriebenen Definition entspricht, ausgelöst
    (rekursive Definition) \> Feld gehört zu einem DW, dessen Master
    nicht das Master DW der Aktion ist \> Feld ist ein Table- Feld und
    wird ausschließlich mittels uf_ChangeItem im default- Eventscript
    belegt \> wenn gilt:
-   das Feld ist NullToX fähig
-   das Feld wird bei "Prüfung von Zusammenhängen" in dem Sinne, wie es
    unter Implementierung einer Aktion beschrieben ist, nicht
    ausgewertet
-   das Feld wird bei "Felder Setzen, Zeilen löschen / einfügen" in dem
    Sinne, wie es unter Implementierung einer Aktion beschrieben ist,
    nicht ausgewertet
-   dieser Zweig wurde für folgenden Fall konzipiert: Aktion
    PreiseSetzen:
-   die aktiven abhängig Felder sind:
    -   Artikelnummer
    -   Auftragsmenge
-   das Feld ist "PreisManuellJn"
-   wenn es Ja ist, wird die Aktion sofort verlassen

aktives abhängig Feld

-   genügt einer der folgenden Bedingungen: \> ist ein abhängig Feld
    aber kein passives abhängig Feld \> Feld löst einen Lookup aus, bei
    dem ein Lookedup- Feld ein passives abhängig Feld (siehe dort) ist
-   Bsp.: Auftragsposition:
-   die Neuanlage kann nur erfolgen, wenn das Positionswindow konstant
    vom Kopf aus aufgerufen worden ist, oder durch eine Fernsteuerung
    erfolgt
-   die Auftragsnummer wird also in beiden Fällen genau einmal gesetzt

## NullToX fähig

-   ist eine Eigenschaft eines abhängig Feldes
-   ein abhängig Feld ist NullToX- fähig, wenn gilt:
-   wenn das Feld Null ist kann die Aktion trotzdem durchgeführt werden
-   das Feld ist kein geändert Feld
-   bei der Verarbeitung der Aktion wird (allerdings nur im Script) null
    durch einen bestimmten Wert ersetzt

## geändert Feld

-   Feld dessen Inhalt durch die Aktion verändert wird
-   muss zu einem DW, dessen Master das Master DW der Aktion ist gehören
-   darf nur geändert Feld einer Aktion sein
-   darf nur von seiner Aktion geändert werden - dazu gibt es folgende
    Ausnahmen:
    -   Änderung durch Benutzereingabe
    -   Änderung durch Fernsteuerung
    -   Setzen eines Updated- Platzhalter- Feldes im AfterUpdateOk-
        Eventscript
    -   Initialisierung im default- Eventscript
    -   initiale Befüllung eines Datawindows über
        ds\_.uf_GetItemIntoNewline

## behandeltes Feld

-   ist ein: \> abhängig Feld \> geändert Feld
-   ein Behandeltes Feld ist definiert durch:
    -   Datawindow
-   wenn nicht angegeben, das DW der Aktion
    -   Row
-   wenn nicht angegeben, die aktuelle Row
    -   Column

## im Sinne der Verarbeitung null

-   ein Feld ist im Sinne der Verarbeitung in einer Aktion null, wenn
    sein Inhalt Null ist und null nicht bei allen Aktivitäten der Aktion
    durch einen anderen Wert (z.B. 0) ersetzt wird. Bsp.: Bestellwert
    der Bestellung: wenn der Positionswert der Bestellposition noch null
    ist, wird 0 angenommen ( der Positionswert ist nicht "im Sinne der
    Verarbeitung null"

## Aufrufe einer Aktion

-   der Aufruf der Aktion erfolgt mittels dw_ApplObj.uf_aktion
-   der Aufruf erfolgt:
    -   im RetrieveEndAppl Eventscript
-   wenn alle aktiven abhängig Felder entweder Table- Felder oder
    Lookedup- Felder sind
-   weil sonst wird die Aktion ja implicit beim Setzen dieses Feldes
    ausgelöst
-   wenn es in der Aktion mindestens eine Aktivität gibt, die nicht
    prüfend ist
-   weil ja prüfende Aktivitäten in der Aktion nicht ausgeführt werden,
    wenn das Argument ac_zweig des Events Aktion nicht gleich "-" ist o
    \>
    -   für jedes aktive abhängig Feld im ItemChangedAppl- Eventscript
-   der Aufruf muss nicht erfolgen, wenn sicher ist, dass mindestens ein
    aktives abhängig Feld null ist und nicht NullToX fähig ist Bsp.:
    -   Aktion "Set-Lagerfaktor":
-   aktive abhängig Felder:
    -   Auftragsnummer (wegen der Auftragsart)
-   Annahme: die Auftragsnummer kann von Anwender nicht gesetzt werden
    und wird genau einmal vom Program gesetzt, bevor die Artikelnummer
    gesetzt wird
-   hier muss und soll im ItemChangedAppl- Eventscript kein Aufruf
    erfolgen, weil zu diesem Zeitpunkt sicher noch kein Artikel und
    demnach auch kein Lagerführungskennzeichen gesetzt ist
    -   Lagerführungskennzeichen lt. Artikel geändert Feld:
    -   Lagerfaktor
    -   Preisfindungsaktion
-   aktive abhängig Felder:
    -   Artikelnummer
    -   Menge
-   nach Änderung der Artikelnummer wird die Menge auf NULL gesetzt
-   es muss die Aktion deshalb nicht aufgerufen werden, weil ja dadurch
    sicher ist, dass die Menge und damit mindestens ein aktives abhängig
    Feld null ist
-   der Aufruf muss nicht erfolgen, wenn bei der Änderung dieses Feldes
    sicher ein anderes aktives abhängig Feld geändert wird und bei
    dessen Änderung sicher die Aktion aufgerufen wird
-   ACHTUNG: der Aufruf eines uf_ChangeItem ist noch kein Garant dafür,
    dass das Feld geändert wird, weil ja das Feld den gleichen Wert wie
    den zu Setzenden Wert des uf_ChangeItem- Aufrufs haben kann und dann
    nichts passiert!
-   diese Regel sollte nur zur Performanceoptimierung herangezogen
    werden und dann ist genau nachzudenken, was geschieht
    -   Zeile löschen:
-   wenn ein aktives abhängig Feld der Aktion in der Zeile vorhanden ist
    aber mindestens ein geändert Feld nicht in der Zeile ist
-   wenn die Prüfung der Aktion aktive abhängig Felder sowohl in der
    Zeile als auch außerhalb der Zeile hat
    -   nach uf_LookupAfterLock, wenn durch diesen abhängig Felder der
        Aktion gelookeuped werden
-   dies wird klassischerweise verwendet, wenn beim Speichern eine
    Tabelle gelockt wird und danach neu eingelesen wird. \> beim
    Speichern
-   wenn während der Erfassung ein inkonsistenter Zustand zugelassen
    wird und die Konsistenz erst vor dem Speichern gegeben sein muss
    Bsp.: Konsistenz der Zahlungskonditionsflder untereinander
    -   im RetrieveSetConst- Eventscript
-   wenn die Aktion keine aktiven abhängig Felder hat
-   wenn die geändert Felder keine Table- Felder sind
-   bevor ein geändert Feld der Aktion verwendet wird
    -   im default- Eventscript
-   wenn die Aktion keine aktiven abhängig Felder hat
-   wenn die geändert Felder Table- Felder sind
-   bevor ein geändert Feld der Aktion verwendet wird

## Implementierung einer Aktion

-   die Implementierung der Aktion erfolgt im Eventscript von Aktion
-   die Nomenklatur der Aktion sollte die behandelten Felder der Aktion
    zusammenfassen
-   zu Beginn der Aktion sind die geändert Felder dokumentiert
-   die aktiven abhängig Felder dokumentieren sich über den Source
    (siehe später)
-   die Abläufe in einer Aktion sind abhängig von den Parametern im
    Aktion- Event
-   die Abläufe in einer Aktion sehen etwa folgendermaßen aus: . Wenn
    die Aktion aufgrund des Inhalts von passiven abhängig Feldern nicht
    durchgeführt werden soll, dann erfolgt keine weitere Verarbeitung .
-   wenn der Parameter ac_zweig des Aktion- Events "-" ist . für alle
    aktiven abhängig Felder
-   für die gilt:
-   nicht NullToX fähig
-   kein geändert Feld
-   dabei sind die Null- Prüfungen in umgekehrter Reihenfolge zu der zu
    erwartenden Feldbelegungsreihenfolge bei der Neuanlage
    durchzuführen. Dadurch wird bei dieser Belegungsreihenfolge nach der
    ersten Nullprüfung true returned und nur beim Belegen des letzten
    Feldes die Prüfung durchgeführt - Dies ist besonders für eine
    Fernsteuerung wichtig. - Performance!!!
-   Dazu ein Bsp.: Berechnung Positionswert: Prüfreihenfolge: rabatt5,
    rabatt4, ..., preis, menge

if uf_IsNull (al_row, "feldname1") then elseif uf_IsNull (al_row,
"feldname2") then ... elseif uf_IsNull (al_row, "feldname-n") then end
if

. für alle geändert Felder der Aktion

if uf_AktionIsNull() then if uf_MussZuruecksetzen() then uf_ChangeItem (
al_row, "Feldname1", gf_null() ) uf_ChangeItem ( al_row, "Feldname2",
gf_null() ) ... uf_ChangeItem ( al_row, "Feldnamen", gf_null() ) end if
return true end if

-   BSP.: . Firmennummer wird vom Anwender geändert . Artikelnummer wird
    vom Lookup ausgenullt . Lookup setzt artik.SumLag_mg auf NULL .
    jetzt muss die Aktion, die die verfügbare Menge Setzt, diese
    ausnullen

-   Wenn sicher ist, dass uf_MussZuruecksetzen() immer false liefert,
    kann dieser Zweig (also der uf_MussZuruecksetzen()- if- Zweig)
    entfallen

. für alle NullToX fähigen abhängig Felder: Belegung einer Variablen mit
dem Feldwert bzw. mit X - Bsp.: Aktion: "best_best_wert_di" - unter
anderem abhängig von "best_pos_wert" - ist "best_pos_wert" noch nicht
gesetzt und deshalb null, wird für die Berechnung 0 verwendet - X ist
also in diesem Fall = 0 . ggf. Felder, die sowohl ein geändert Feld als
auch ein aktives abhängig Feld sind und null sind, setzen - ist dies
nicht möglich, weil eine Inkonsistenz innerhalb der abhängig Felder
herrscht, dann Fehlerbehandlung durchführen - wenn durch das Setzen alle
geändert Felder gesetzt sind , wird mit return true ausgestiegen, wenn
keine weiteren Ativitäten notwendig sind . jetzt gibt es für jedes
abhängig Feld einen Wert ungleich null - bei NullToX fähigen Feldern
allerdings nur im Programm . ggf. Prüfung von Zusammenhängen der
abhängig Felder untereinander durchführen - dies erfolgt nicht, wenn der
Parameter ac_zweig des Aktion- Events 'r' oder 'v' ist - wird dabei ein
Fehler entdeckt, dann Fehlerbehandlung durchführen . ggf. Felder Setzen,
Zeilen löschen / einfügen - tritt dabei ein Fehler auf, dann
Fehlerbehandlung durchführen - ...... . true zurückliefern

Fehlerbehandlung

-   ist nur, um die Beschreibung kurz zu halten, nur einmal
    beschrieben - im Programm ist das nicht so . ggf. Fehlertext mittels
    uf_SetErrorTxt2nl setzen . ggf. Fehler durch Setzen eines Feldes /
    mehrerer Felder beheben
-   tritt dabei ein Fehler auf, dann Fehlerbehandlung durchführen . ggf.
    Fehlertext ausgeben . ggf. trotz Fehler weitermachen . ggf. wird die
    Aktion beendet und false geliefert
-   ACHTUNG: wenn false returned wird, kann es sein, dass ein Lookup
    nicht gut geht - Bsp.: . durch den Lookup des Kunden wird die
    Zahlungskondition gesetzt . das Löst die Aktion "AufartVersartZk"
    aus . wenn diese false liefert, geht das Setzen der
    Zahlungskondition nicht gut . dadurch geht der Lookup nicht gut ( in
    der Aktion muss dies berücksichtigt werden - z.B.:
-   wenn die Aktion durch Kundeneingabe ausgelöst wurde, wird nicht
    false geliefert, sondern ein oder mehrere Felder ausgenullt
-   Wenn die Aktion an nur genau einer Stelle aufzurufen ist, kann sie
    direkt dort implementiert werden
-   die restlichen Implementierungsregeln gelten aber trotzdem

Problematik zwischenzeitliche Inkonsistenz:

Dazu folgendes Beispiel mit dem Auftragspositionswindow: - folgende
Felder: - offene Menge - zum Kommissionieren freigegebene Menge - diese
wird im Büro gesetzt - in bestimmten Konstellationen wird sie durch
Änderung der offenen Menge gesetzt - kommissionierte Menge - diese wird
im Lager gesetzt und darf im Büro nicht geändert werden - in bestimmten
Konstellationen wird sie durch die Aktion "SetzKomm" gesetzt - Folgende
Bedingung muss eingehalten werden: -
`zum Kommissionieren freigegebene Menge´ >=` kommissionierte Menge´ -
`zum Kommissionieren freigegebene Menge´ <=`offene Menge´ - Es wird
jetzt die
`offene Menge´ von 10 auf 8 reduziert, wobei die zum Kommissionieren freigegebene Menge auch 10 ist und wir die Konstellation, in der`zum
Kommissionieren freigegebene Menge´ gesetzt wird, haben - Die obige
Prüfung muss nach dem evtl. Setzen von
`zum Kommissionieren freigegebene Menge´  erfolgen - sonst ist ja unsere zweite Bedingung nicht erfüllt ist - Ist jetzt die`
kommissionierte Menge´ auch 10, geht das automatische Setzen von
`zum Kommissionieren freigegebene Menge´ auf 8 nicht gut, weil ja unsere erste Bedingung nicht erfüllt ist - Damit wird`zum
Kommissionieren freigegebene Menge´ auf den alten Wert 10 zurückgesetzt
und unsere 2. Bedingung ist nicht erfüllt ( Fehlermeldung: "Das
Zurücksetzten auf den alten Wert hat nicht funktioniert" - LÖSUNG: - Die
Prüfaktion wird nur durchgeführt, wenn wir beim äußersten
ItemChangedAppl der beteiligten Felder sind - dieser muss allerdings
nicht der absolut äußerste sein - Details siehe LGV:
tcl_verkauf.pbl:w_auf_pos - suche nach ib_Aktion_KomFreiMgPruef_inaktiv

## Beispiele

o - Name der Aktion: "AufartVersartZk" - aktive abhängig Felder: -
Auftragsart - alle Felder der Zahlungskondition - Versandart - Muss-
Zahlungskondition der Versandart - Muss- Zahlungskondition der
Auftragsart - Versandart- Kennzeichen - Auftragsart- Kennzeichen -
passive abhängig Felder: - Muss- Zahlungskondition der Versandart -
Muss- Zahlungskondition der Auftragsart - Versandart- Kennzeichen -
Auftragsart- Kennzeichen - geändert Felder: - alle Felder der
Zahlungskondition - Versandart - Was tut die Aktion: - Überprüfung der
Konsistenz zwischen den abhängig Feldern - Bsp.: Bei Auftragsart
Barverkauf kann die Versandart auf Selbstabholung und die
Zahlungskondition auf netto Kassa gesetzt werden, wenn dies bei
Barverkauf die einzigen gültigen Werte sind und weder die Versandart
noch die Zahlungskonditionen eingegeben worden sind. o - Name der
Aktion: "auf_off_mg" - aktive abhängig Felder: - auf_best_mg -
auf_loesch_mg - ( nicht von "ein:auf_off_mg" - diese Aussage ist nur in
Zusammenhang mit uf_DefineEinIstCol relevant! ) - passive abhängig
Felder: - auf_lief_mg - diese kann sich im update/insert- Zustand nie
ändern - geändert Feld: - auf \_off_mg (bzw. ist:auf_off_mg ( siehe
uf_DefineEinIstCol)

## Fernsteuerung

-   es handelt sich um eine Fernsteuerung, wenn:
-   Menüpunkte, die normalerweise von einem Benutzer ausgelöst werden,
    vom Programm ausgelöst werden
-   Datenfelder, die normalerweise vom Benutzer eingegeben werden, vom
    Programm gesetzt werden
-   die Definition ist nicht exakt, aber es sollte intuitiv klar sein,
    was gemeint ist
-   es gibt 3 grundsätzliche Arten von Fernsteuerung:
    -   Batch- Fernsteuerung
-   dies ist die hauptsächlich verwendete
-   das Programm bestreitet die gesamte Fernsteuerung ohne
    Benutzerinteraktion
-   Bsp. 1: Anlage der Setpositionen nach dem Speichern einer
    Auftragsposition mit Setartikel
-   Bsp. 2: Anlage/Update einer Bestellposition nach dem Speichern einer
    Auftragsposition
    -   Batch- Fernsteuerung mit Unterbrechung
-   wie Batch- Fernsteuerung, aber folgende Ausnahme:
-   Die Fernsteuerung selbst unterbricht sich und übergibt die Controlle
    an den Benutzer, der eine Interaktion im ferngesteuerten Window
    tätigen muss.
-   Die Interaktion wird vom Benutzer durch Auslösen von Speichern oder
    Verwerfen beendet
-   Das ferngesteurte Programm muss in diesem Fall die Fortsetzung der
    Fernsteuerung aufrufen
    -   Life- Fernsteuerung
-   die Fernsteuerung erfolgt parallel zur Benutzerinteraktion
-   wurde für die LGV- MDE- Lösung eingeführt (MDE- Modus):
-   Es gibt eigene Windows für ein mobiles Gerät (Bildschirmauflösung
    z.B. 320\*240)
-   Ein solches eigenes Window öffnet zu Beginn ein Window der normalen
    Desktopapplikation welches ferngesteurt wird:
-   nach jeder Benutzereingabe wird der eingegebene Wert auch in der
    Desktopapplikation gesetzt, und nur wenn dies erfolgreich ist, wird
    die Eingabe akzeptiert
-   das Speichern der Daten erfolgt über das Desktop- Window
-   Anmerkung: es gibt im MDE- Bereich aber auch Batch- Fernsteuerung
-   siehe unbedingt Datenbankändernde Statements -- Transactions
-   siehe w_ApplObj.wf_Reset, wf_Cancel, wf_besorgs

## Batch- Fernsteuerung

-   Die Verarbeitung muss mit wf_BatchBegin beginnen
-   dies gilt auch bei der Wiederaufnahme der Verarbeitung bei der
    "Batch- Fernsteuerung mit Unterbrechung"
-   in w_JobObj ist dies nicht nötig, weil es dort schon gesetzt ist
-   Die Verarbeitung muss mit wf_BatchEnd enden
-   dies für die Unterbrechung der Verarbeitung bei der "Batch-
    Fernsteuerung mit Unterbrechung"
-   in w_JobObj ist dies nicht nötig
-   ist das ferngesteuerte Window nicht das fernsteuernde Window, ist es
    fogendermaßen zu öffnen: . lw_xy = " fernsteuerndes Window ".wf_open
-   ist das fernsteuernde Window ein w_JobObj, ist es performanter ,
    wenn mit iuo_ae.iw_main. wf_open ( true, ..., "tsw" ... ) geöffnet
    wird - das ferngesteuerte Fenster wird dann Job- übergreifend wieder
    verwendet - dies ist aus Speicherplatzbedarf- Sicht allerdings nur
    für viel verwendete Windows sinnvoll
-   hierbei ist ab_wakeifpossible = true und SleepOnClose eingeschaltet
-   Beim Öffnen des ferngesteuerten Windows über das Clicked- Event
    eines Buttons muss es statt lw_xy ein iw_xy geben
-   das Öffnen und das Schließen des ferngesteuerten Windows muss im
    selben Script erfolgen
-   es wird ggf. das Kommando "privileged" mitgegeben (MFA,
    Berechtigung)- siehe wf_open
-   in as_command muss "RemCtrldByAo" enthalten sein, wenn die
    Fernsteuerung auch im MDE- Modus durchgeführt werden können soll -
    eigenlich sollte das wahrscheinlich immer erfolgen
-   wird die Transaktion mit "fernsteuerndes Window".wf_TrBegin
    eingeleitet
-   muss nach "ferngesteuertes Window".wf_Save "ferngesteuertes
    Window".wf_Reset aufgerufen werden
-   darf "ferngesteuertes Window".wf_Cancel nicht aufgerufen werden
-   muss im Fehlerfall "ferngesteuertes Window".wf_Reset aufgerufen
    werden
-   wird die Transaktion mit "ferngesteuertes Window".wf_TrBegin
    eingeleitet
-   darf "ferngesteuertes Window".wf_Cancel ggf. aufgerufen werden
-   zu verwenden, wenn "ferngesteuertes Window".wf_Reset nicht verwendet
    wird
-   kann auch "ferngesteuertes Window".wf_Reset aufgerufen werden --
    dadurch wird verhindert, dass die Anzahl der Rows in der Liste
    ungeahnte Dimensionen erreicht (O-Ton SC)

## Live- Fernsteuerung

-   es ist folgender Ablauf zu empfehlen: . lw_xy = "fernzusteuerndes
    Window".wf_open
-   in as_command muss "RemCtrldByAo" enthalten sein
-   as_FocusOnClose darf kein { 'w', 'W', 'b' } enthalten, wenn das
    fernsteurnde Window interaktiv verwendet wird
-   das ferngesteuerte Window braucht erst beim close des fernsteuernden
    Windows geschlossen zu werden
-   ACHTUNG: wenn das ferngesteuerte Window vom Fernsteuernden Window
    aus aufgerufen wird,
-   erfolgt der Close des ferngesteuerten Windows automatisch
-   muss im BeforeCloseChilds- Eventscript des fernsteuernden Windows
    folgendes vorhanden sein: . prüfen, ob sich das ferngesteuerte
    Window schießen lassen wird
-   besonders, ob es im Status new bzw. update ist - wenn ja ( return
    false . das gleiche für das fernsteuernde Window
-   wenn dies nicht so ist, kann folgendes passieren: . der User
    schließt das fernsteuernde Window . das ferngesteuerte Window wird
    geschlossen . das ferngesteuerte Window bricht den close ab, weil es
    z.B. im Status update ist . lw_xy zeigt jetzt auf ein logisch
    geschlossenes Fenster . bei der nächsten Verwendung von lw_xy kommt
    es zu einem \*f_halt . nach jeder Benutzereingabe werden die Daten
    ins ferngesteuerte Window übertragen - wenn dies nicht erfolgreich
    ist, wird die Benutzereingabe nicht zugelassen . "fernzusteuerndes
    Window".wf_TrBegin, wenn die Fernsteuerung nicht z.B. im
    AfterUpdateOk- Eventscript aufgerufen wird . wf_Save ( false ) .
    wf_TrCommit
-   wenn die Fernsteuerung nicht z.B. im AfterUpdateOk- Eventscript
    aufgerufen wird
-   bei einem Fehler wird vorher schon abgebrochen und stattdessen
    wf_TrRollback aufgerufen

## Begriffe

## Felder: verschiedene Kategorien

-   siehe Programmierhinweise -- Arten von Feldern in DWs und deren
    Zusammenspiel

## Lookup

-   siehe Environment und Lookup

## Kommandostring des Environments

-   Das Environment hat einen Kommandostring folgender Form:
    `<Kommandowort>`{=html} \[ " " `<Kommandowort>`{=html} \] ...
-   `<Kommandowort>`{=html} darf kein Leerzeichen enthalten
-   Eine Sonderform von `<Kommandowort>`{=html} ist ein Argument-
    Kommando, welches folgende Form hat: `<Argument>`{=html} "="
    `<Argumentwert>`{=html}
-   Beim Open eines Neuen Windows mittels w_ApplObj.wf_open wird der
    Kommandostring als Funktionsparameter übergeben.
-   Das Environment w_ApplObj.iuo_ae vom Typ Cst_ApplEnv bietet folgende
    Funktionen zum Behandeln des Kommandostrings:
    -   uf_InCommand() ( überprüft, ob ein Kommandowort im Kommandosting
        enthalten ist
    -   uf_GetCommandWert() ( Liest den Argumentwert eines Argument-
        Kommandos aus
    -   uf_AddCommand() ( Hängt ein Kommandowort an den Kommandostring
        an
-   Folgende Kommandos werden von w_ApplObj ausgewertet und können, wenn
    dies nicht anders beschrieben ist, beim wf_open übergeben werden:
    -   "open" ( aufgerufenes Window ruft Menüpunkt Query auf
    -   "opennew" ( aufgerufenes Window ruft Menüpunkt Query auf, wobei
        im Auswahldialogfenster zusätzlich die Schaltfläche "Neu"
        vorhanden ist
    -   "new" ( aufgerufenes Window ruft Menüpunkt New auf
    -   "noquerydw" ( aufgerufenes Window ruft beim Menüpunkt Query den
        Auswahldialog nicht auf
-   Konstante werden dabei sehr wohl eingeschränkt
-   Query-Map-Defaultwerte werden dabei nicht berücksichtigt
    -   "autoaccept" ( aufgerufenes Window schließt den Auswahldialog
        automatisch mit "Auswählen" ab
-   Query-Map-Defaultwerte werden dabei berücksichtigt
    -   "search" ( ACHTUNG: darf nicht verwendet werden außer:
-   es wird das Datawindowcontrol, in welches das aufgerufene Window
    seinen Key exportieren soll, als aa_arg übergeben (könnte ggf.
    idw_LastFocus sein)
-   das aufgerufene Window macht beim Return keinen Blödsinn - siehe
    dazu ReturnOnSearch
-   wenn das ReturnOnSearch- Script des aufgerufenen Windows übersteuert
    ist kann ggf. aa_arg auch ein anderes dw_ApplObj des aufrufenden
    Windows übergeben werden - Falls die übersterte Return-
    Funktionalität im ReturnOnSearch- Script kein solches DW benötigt
    ist trotzdem ein dw_ApplObj zu übergeben (z.B. idw_neu)
-   ist zu verwenden, wenn ein Window nicht mittels Ctrl+F aufgerufen
    wird und trotzdem die Return- Funktionalität (Ctrl+R) zur Verfügung
    stehen soll
    -   "RemCtrldByAo" ( window wird "Life"- ferngesteuert ( Life-
        Fernsteuerung
-   as_focusonclose muss so belegt sein, dass ein gültiges Window
    ermittelt wird
    -   "privileged"
-   ab_UseAnmeldMfa wird ignoriert und es wird false angenommen
-   es sind alle Berechtigungen vorhanden
-   wf_BerechtigtIn liefert "'x' = 'x'"
-   ist zu verwenden, wenn ein Window Batch- ferngesteuert wird
-   ACHTUNG: kommt ein Window im "privileged"- Modus ins
    SetPresentation, kommt eine Fehlermeldung und es wird geschlossen!!!
-   auf Visible und und Protect hat dies allerdings keinen einfluss, was
    ja egal ist, da ein Window im "privileged"- Modus sowieso nie
    sichbar sein kann
    -   "show" (
-   Window wurde vom show- Mechanismus aufgerufen
-   darf vom Anwendungsprogramm nicht gesetzt werden

## Master- Detail- Verbund

-   Normalerweise kann in höchstens einem DW etwas geändert und nicht
    gespeichert worden sein.
-   Will man, daß in mehreren DWs etwas geändert und nicht gespeichert
    worden sein kann muß man einen Master- Detail- Verbund definieren.
    Dabei ist ein DW der Master und die anderen jeweils das Detail.
-   Dies wird im DefineMaster- Eventscript von dw_ApplObj definiert
-   Ein Master darf kein Detail eines anderen Masters sein

## MDE- Modus

-   die Applikation kann im MDE- Modus betrieben werden
-   dies sollte dann erfolgen, wenn auf einem Terminalclient mit
    320\*240- Auflösung gearbeitet wird - genau dies trifft bei einem
    MDE- Gerät zu
-   Folgende Merkmale des MDE- Modus:
-   w_ApplObjTab's werden so positioniert, dass die obere linke Ecke des
    Datawindows lt. DwPositionMde (default-mäißig ist dies idw_neu) mit
    der oberen linken Ecke der MDI- Haupwindownutzfläche
-   pfu_fun- intern: dies erfolgt im open- Eventscript von w_ApplObj
    mittels wf_PositionMde()
-   eigenes Anmeldefenster (abgeleitet von w_AppAnmeld)
-   Positionierung: der oberste linke Punkt des ClientAreas liegt genau
    auf dem obersten linken Punkt des MDI-Client-Areas
-   pfu_fun- intern: dies erfolgt via w_ApplEn.wf_PositionMde()
-   eigenes Auswahlmenüfenster (abgeleitet vom w_ApplEnvOpen) - zeigt
    alle Menüpunkte des User- Menüs mit dem MDE-Hakerl an
-   Positionierung sinngemäß wie w_ApplObj
-   Menüpunkte werden durch einfaches Clicken angewählt
-   Positionierung wie das Anmeldefenster
-   w_ApplObjQuery (das Auswahlfenster)
-   ist kleiner und links oben positioniert
-   hat nur den Auswahl- und den Abbrechen- Button
-   wenn im nicht- MDE- Modus ein Window statt echt geclosed verseckt
    wird, bleibt es im MDE- Modus wo es ist - es erhält lediglich ein
    anderes Window den Focus ( alle Windows müssen die volle Größe der
    MDI- Frame- Nutzfläche haben, sonst sieht man einen Teil von ihnen,
    obwohl sie logisch gesehen geclosed sind (ggf. siehe zum besseren
    Verständnis wf_open Argument as_FocusOnClose)
-   Die Steuerung erfolgt meist über Datawindow- Buttons
-   siehe wf_AddDwButtonAppl
-   dazu gibt es auch ein eigenes DW- Control, das nur Buttons enthält (
    dw_MdeButton
-   es gibt zei Methoden, die Applikation im MDE- Modus zu starten: \>
    Commandline- Argument: "mde='j'" \> Registry- Eintrag: "mde" mit dem
    Wert "j"
-   suche in dieser Doku nach "MDE- Modus", um Events und Funktionen für
    den MDE -Modus kennenzulernen
-   im MDE- Modus gilt:
-   message.ib_mde = true
-   dw_ApplObj.ib_MdeAppl = tue
-   w_ApplObj.ib_MdeAppl = tue
-   die abweichenden Größen- und Positionierungseinstellungen werden
    meist im Open- Eventscript der entsprechenden Windows erledigt

## Weglassregel

-   siehe Environment und Lookup

## Abläufe bei der Bedienung

## Tasten

## TAB

> befindet sich der Focus innerhalb eines DW- Controls: - bewegt sich
> der Cursor ins nächste Feld sonst: - bewegt den Focus zum nächsten
> Control am Window - + Shift- Taste: umgekerte Richtung

## Enter

> befindet sich der Focus innerhalb eines DW- Controls - bewegt sich der
> Cursor in die nächste Zeile - dabei wird zunächst das aktuelle Feld
> geprüft - steht der Cursor in der letzten Zeile, wird unterhalb eine
> neue Zeile angehängt, falls dies erlaubt ist. (In einem DW mit fix
> einer Zeile erfolgt demnach ausschließlich die Feldprüfung.) - +
> Shift- Taste: umgekehrte Richtung befindet sich der Focus innerhalb
> eines Menüs - wird der aktuelle Menüpunktes gewählt befindet sich der
> Focus innerhalb des Window- Start- Dialogs - wird der aktuelle
> Menüpunktes gewählt Befindet sich der Focus innerhalb eines Suchfeldes
> des Querydialogs - wird der Wertevorrat zum aktuellen Suchfeld
> angezeigt Befindet sich der Focus innerhalb der Wertevorratliste des
> Querydialogs - wird der aktuelle Wert ins Suchfeld übertragen

## Vertikale Pfeiltasten

> befindet sich der Focus innerhalb eines DW- Controls: befindet sich
> der Cursor auf einem DDDW - wird der nächste/vorige Wert der Liste
> vorgeschlagen - + Alt- Taste: Die Liste wird angezeigt bzw.
> verschwindet, wenn sie angezeigt ist sonst - gleiche Wirkung wie
> Enter/Shift+Enter befindet sich der Focus innerhalb eines Menüs - wird
> der nächste/vorige Menüpunkt der Aktuelle befindet sich der Focus
> innerhalb des Window- Start- Dialogs - wird die nächste/vorige Zeile
> die aktuelle

## Horizontale Pfeiltasten

> befindet sich der Focus innerhalb eines Feldes mit Zeicheneingabe
> (auch innerhalb eines DW- Controls): - bewegt sich der Cursor zum
> nächsten/vorigen Zeichen befindet sich der Focus innerhalb des TAB-
> Controls: - wird das nächste/vorige Tab das aktuelle befindet sich der
> Focus innerhalb eines Menüs - wird der nächste/vorige Über- Menüpunkt
> der aktuelle (rechts/links)

## Escape

> befindet sich der Focus innerhalb eines Menüs - wird in die nächst
> höhere Menüebene gewechselt und das Menü verlassen, wenn die aktuelle
> Menüebene die höchste ist.

## Leertaste

> befindet sich der Focus auf einem Button - wird dieser ausgelöst
> befindet sich der Focus innerhalb einer Checkbox - wird deren Wert
> geändert

## Strg+"-"

-   In der Neuanlage ( Speichern und Neuanlage
-   Beim Ändern ( Speichern und zum nächsten Datensatz blättern

## Strg+"1"

-   Auf die 1. Tabpage (Liste) springen V

## Strg+"2"

-   Auf die 2. Tabpage (Detail) springen

## Menü- Shortcuts

## m_applenv

## Datei

## 1.Anmeldung Ctrl + M

## 2.Anmeldung Ctrl + Shift + M

## Menu öffnen Ctrl + Shift + O

## Beenden Alt + F4

## Ansicht

## Lookuppuffer löschen Ctrl + Alt + F4

## ?

## Hilfe F1

## Jobverarbeitung starten Ctrl + F12 (nur im Haus)

## m_applobj (inherited from m_applenv)

## Datei

## (neue) Auswahl definieren Ctrl + Q

ähnliche (neue) &Auswahl definieren Ctrl + Shift + Q \## Window
speichern Ctrl + S

## Window schließen Ctrl + F4

## Liste drucken Ctrl + P

## Bearbeiten

## Neu Ctrl + N

## Verwerfen Ctrl + U

## Übernehmen Ctrl + R

## Löschen Ctrl + D

## Datensatz Kopieren Ctrl + Y

## Zurückblättern Ctrl + G

## Vorblättern Ctrl + H

neue Zeile in der Position der aktuellen Zeile Ctrl + I neue Zeile nach
der Position der aktuellen Zeile einfügen Ctrl + E \## Zeile löschen
Ctrl + L

## Zeile ausschneiden Ctrl + A

## Zeile kopieren Ctrl + K

## Suchen Ctrl + F

## Öffnen Ctrl + O

## Window öffnen (indiv übersteuerbar) Ctrl + W

## Feld löschen Ctrl + Z

## Ausschneiden Ctrl + X

## Kopieren Ctrl + C

## Einfügen Ctrl + V

## aktuellen Bereich sortieren Ctrl + T

## Ansicht

## Aktualisieren F5

## zum Register Liste wechseln Ctrl + 1

## zum Register Detail wechseln Ctrl + 2

## m_applobjquery (inherited from m_applenv)

## Bearbeiten

## Suchen Ctrl + F

## Window öffnen (indiv übersteuerbar) Ctrl + W

## m_pfu_col (inherited from m_applobj_tci)

## Extras

Kennzeichen für Ja/Nein anlegen Ctrl + Alt + K

## m_pfu_dj (inherited from m\_ applobj\_ tci)

## Extras

Reorganisation DruckJobs Ctrl + Alt + Shift + F5

## m_pfu_help (inherited from m\_ applobj\_ tci)

## Extras

## Textblock einrücken Ctrl + Alt + E

## Textblock ausrücken Ctrl + Alt + A

## Textmarke ein-/ausschalten Ctrl + Alt + M

## Text Fett ein-/ausschalten Ctrl + Alt + F

## Text Unterstrichen ein-/ausschalten Ctrl + Alt + U

## Blockraster einblenden Ctrl + Alt + B

## Sonstige Shortcuts (unsichtbare Menüpunkte)

## dw_applobj.Key

## in das vorherige DW wechseln Ctrl + BildAuf

## in das nächste DW wechseln Ctrl + BildAb

## Maus

-   ACHTUNG: bei einem Doppelklick wird zu Beginn immer die
    Klick-Aktivität durchgeführt

## Markieren in Grids

-   In Grids, kann wie man es vom Windows- File- Explorer gewohnt ist
    Zeilen markieren - folgende Abweichungen:
-   Es gibt zwei Kategorien von Markierung:
    -   Die aktuelle Zeile, die es in Tradecontrol ja immer gegeben hat
    -   Markierte Zeilen
-   Die aktuelle Zeile kann nicht markiert werden, gilt aber als
    markiert, wenn es darum geht, alle markierten Zeilen zu manipulieren
    (z.B. Drag&Drop)
-   Shift + Click funktioniert nicht genau gleich wie beim Explorer,
    sondern: Makiere einen Block von der geklickten Zeile bis zur ersten
    markierten Zeile und von dort weiter solange die Zeilen markiert
    sind - dies erfolgt in jene Richtung in der sich die zuletzt
    geklickte Zeile befindet.
-   mittels ctrl kann verhindert werden, dass vorher alle vorigen
    Markierungen gelöscht werden

## Drag & Drop

-   funktioniert nur mit der linken Maustaste
-   derzeit können DataWindow- Felder und Rows gedragged werden
-   der Drag- Vorgang beginnt erst, nachdem die Maus mindestens um 4
    Pixel bewegt worden ist
-   für die Sortierung und das Label- Zuordnen gelten die Aussagen nicht
-   es gibt folgende Möglichkeiten:
-   -   Ctrl- Taste (
-   Grid: es werden die geclickte Row + alle markierten Rows gedragged
-   Nicht Grid: es wird das geclickte Feld
-   keine zusätzlichen Tasten (
-   wie +Ctrl, außer das geclickte Feld ist eingebbar
-   -   Alt- Taste (
-   Es wird das ceclickte Feld gedragged
-   Wird ein Datawindow im Drag- Zustand verlassen und die Ctrl- Taste
    oder die Alt- Taste ist gedrückt, beginnt das DW zu scrollen
-   nach dem Verlassen können die die Ctrl- Taste bzw. die Alt- Taste
    wieder losgelassen werden.
-   Zusätzlich kann durc h drücken der Shift- Taste das Scrollen
    beschleunigt werden
-   Erfolgt das Verlassen des DWs über den Header, wird nach oben, sonst
    nach unten gescrollt

## Sonstiges

-   Shift+Doppelklick ( Zoomen oder Öffnen
-   Durch die oben erwähnte Klick- Aktivität werden zunächst ggf. Zeilen
    markiert - desshalb löst Shift+Doppelklick zusätzlich das
    Entmakieren aller markierten Zeilen aus
    -   Doppelklick in der Liste ( alle markierten Zeilen zurückgeben
        und schließen, falls mehr als eine Zeile markiert ist
-   Beim impliziten Klick werden allerding die Markierungen entfernt und
    die aktuelle Zeile gewechselt
-   Dies kann z.B. folgendermaßen verhindert werden:
-   Alt- drücken (Alt, Shift bzw. Ctrl beim Klick auf ein Feld
    verhindern die Standard- Maus- Aktivität)
-   Ctrl auf eine nicht markierte Zeile ( dann wird diese Markiert und
    anschließend die Rückgabe durchgeführt
-   Ist das aufrufende Fenster allerdings nicht das Queryfenster, wird
    nur die aktuelle Zeile berücksichtigt
    -   Ctrl+Klick auf die aktuelle Zeile bewirkt gar nichts

## Fibuintegration

-   Die Fibuintegration orientiert sich primär an der Jetfibu
-   ist die Jetfibu im Einsatz ist folgendes notwendig:
    -   jfb_fun\*.pbl im Library- Search- Path
    -   folgende globale Variablen vom Typ tr\_ müssen instanziert sein
        und es muß eine Connection bestehen:
    -   gtr_JetfibuAnl
-   muß zur Jetfibudatenbank bzw. einer DB, welche alle benötigten
    Jetfibutabellen als View eingebunden hat, connected sein und wird
    von den Stammdatenanlagewindows herangezogen
    -   gtr_jetfibuAbf
-   in der verbundenen Datenbank müssen folgende Tabellen/Views
    vorhanden sein:
    -   pfufb_debitor
    -   pfufb_kreditor
    -   pfufb_op
    -   gtr_jetfibuBip
-   in der verbundenen Datenbank müssen folgende Tabellen/Views
    vorhanden sein:
    -   fbpfu_bibbereich
    -   fbbibel
    -   fbbibkt
-   in der Datenbank, zu der sqlca connected ist, muß die Tabelle
    ust_proz lt. Tradecontrol- DB- Beschreibung vorhanden sein
-   von gf_InitApplEnv aus muß direkt oder indirekt
    gf_InitApplEnv_jetfibu aufgerufen werden
-   Folgende Klassen müssen definiert sein: (die entsprechenden Fibu-
    Klassen sind davon abgeleitet)
    -   dw_ApplObj_fbi
    -   dw_ApplObjList_fbi
    -   w_ApplObj_fbi
    -   w_ApplObjTab_fbi
    -   m_ApplObj_fbi
-   ist eine andere, bzw. keine Fibu im Einsatz ist folgendes zusätzlich
    notwendig bzw. anders:
    -   kjfb_fun\*.pbl im Library- Search- Path
-   über pfufb_debitor und pfufb_kreditor müssen insert und update
    möglich sein
-   Die Anlage von Debitor und Kreditor erfolgt über die Windows
    -   w_pfu_debitor_kj
    -   w_pfu_kreditor_kj , welche die Tabellen pfufb_debitor und
        pfufb_kreditor verwenden.
-   Die Verwendung dieser Windows wird durch Aufruf von
    gf_InitApplEnv_kj erreicht.
-   Soll ein von eigenes Window verwendet werden, ist dies durch
    cst_ApplEnv.uf_AddWindowMap zu bewerkstelligen. Es darf dann
    allerdings gf_InitApplEnv_kj nicht aufgerufen werden und es müssen
    die restlichen dort befindlichen uf_AddWindowMap- Aufrufe selbst
    durchgeführt werden.
-   Es kann auch durch cst_ApplEnv.uf_AddWindowMap die Verwendung
    eigener, möglicherweise von w_pfu_debitor/kreditor abgeleiteter
    Windows erreicht werden.

## Tradecontrol- Request Server

## TCP- Request Server

-   Dient dazu, Tradecontrol- Funktionalitäten über eine TCP/IP-
    Verbindung extern zur Verfügung zu stellen

-   Prinzipieller Aufbau/Ablauf:

-   Es gibt eine Kontroll- Applikation, die auf einem Port lt.
    Konfiguration listend und auf Anforderungen wartet

-   Diese hat einen Pool von dedizierten Tradecontrol- Sessions, die von
    ihr gestartet worden sind

-   Diese Schnittstelle nach außen ist dabei über ein von w_tcprs
    abgeleitetes Window implementiert

-   Kommt ein Request, wird ein Port, unter dem sich der Client zu einem
    freien Tradecontol connecten kann, zurückgeliefert und die
    Verbindung beendet.

-   Der Client führt dann den Connect mit dem übergebenen Port aus

-   Zur Koordination der Tradecontrol- Sessions gibt es Kommunikation
    zwischen diesen und der Kontroll- Aplikation

-   Die Kontroll- Applikation war bis A12732 eine Powerbuilder-
    Aplikation die mittels TCP/IP mit der Kontrollapplikation
    kommuniziert hat. Mit A12732 wurden die Funktionalitäten der
    Kontroll- Applikation in den Service Controller integriert - die
    Powerbuilder-Applikation wird nicht mehr weiterentwickelt (es werden
    auch keine Fehler ausgebessert!)

-   Tradecontrol als TCP- Requestserver- Verarbeitungs- Applikatiobn
    wird weiterhin verwendet - dabei gilt:

-   Der TCP- Teil bleibt unverändert

-   Der Kommunikationsteil mit der Kontrollapplikation ist neu - die
    Kommunikation erfolgt jetzt über WCF, wobei der Service- Controller
    der Server ist. Dazu wurde in der Pcs.Interop die Klasse
    ServiceControllerClient und in der pfu_fun die zugehörige Proxy-
    Klasse cst_servicecontroller eingeführt

-   Siehe in
    `Installation beim Kunden.doc´ PCS Service Controller ## Konfiguration: siehe Konfig-Musterfile:`Process
    Name="Eshop-Anbindung"´

-   Ad Service-Controller-Source:

-   ProcessItem.vb: Klasse:ProcessItem.Property:Status

-   So weiß der Service- Controller welche TC's frei sind

-   Wenn der Servicecontroller den Port einer TC-Session an den Client
    übergibt, bekommt diese Session den Status reserviert

-   Wenn TC dann den Request entgegen nimmt, wird der Status blockiert

-   ACHTUNG: es ist noch nicht alles komplett implementiert

-   Z.B. Funktion uf_SendAlive wird nicht verwendet

## WCF- Request Server

-   Die Funktionalitäten des TCP- Request Servers können auch als WCF-
    Service zur Verfügung gestellt werden
-   Diese Funktionalität wird aditiv vom PCS Service Controller zur
    Verfügung gestellt - dies funktioniert in etwa folgendermaßen:
-   Es läuft ein WCF- Service im PCS Service Controller
-   Dieses wird allerdings durch eine Projektindividuelle Klasse
    implementiert. Diese muss allerdings ein im Service- Controller-
    Bereich definiertes Interface implementieren - damit erfolgt die
    Kommunikation
-   Es werden dabei die selben Datenstrukturen, die auch der TCP-
    Request Server- Teil verwendet, benützt (abgesichtert mittels
    mutexes)
-   Diese Projektklasse befindet sich in einer eigenen dll, die zur
    Laufzeit geladen wird und dessen Pfad im Konfigurationsfile
    eingetragen ist.

## Hinweise zu Datenbanken

## Informix

## anlegen einer Datenbank - Sortierungsname

-   der Sortierungsname "SQL_Latin1_General_CP850_CS_AS" sollte nicht
    verwendet werden!!
-   es sollte unbedingt "Latin1_General_CS_AI" verwendet werden!!
-   sonst gibt es Probleme mit der Sortierung

## ermitteln des Sortierungsnames / LOCALE

select \* from systables where tabname = ' GL_COLLATE'

## MS SQL Server

## anlegen einer Datenbank - Sortierungsname

-   der Sortierungsname "SQL_Latin1_General_CP850_CS_AS" sollte nicht
    verwendet werden!!
-   es sollte unbedingt "Latin1_General_CS_AI" verwendet werden!!
-   sonst gibt es Probleme mit der Sortierung

## WasTunWenn (FAQ)

## Feldhintergrundfarbe wird nicht richtig angezeigt

-   Mögliche Ursache: Background- Colour ist auf transparent
-   dies Kann die aktuelle Zeile in Grids, das aktuelle Feld oder
    definierte Felddarstellungen betreffen

## idw_neu soll unsichtbar sein

-   einfach im DarfVisible- Eventscript false returnieren

beim aufruf eines Windows die Konstanten nicht (richtig) gesetzt sind

-   Debug - Breakepoint auf cst_ApplEnv.uf_key4const

## beim Aufruf aller Windows ewig die Sanduhr kommt

-   in w_applobjtab_tci fehlen evt. folgende events: selectionchanged,
    rightclicked, key und/oder losefocus

dw_spoolin drucker_cd ist keine Key- Column eines AEOs und darf deshalb
\## kein DDDw mit DWO 'd_ddw_ao\_\*' haben

## in gf_initapplenv fehlt "spoolin" in as_command

z.B.: auo_ae.uf_AddAot("datueb_deb", "Datenübernahme Debitor", "","",
\##"spoolin", "","","","", true)

## Jobverarbeitung bringt Fehler-DW´s und bleibt dadurch hängen

## Im systemerror Event der Aplikation fehlt: message.uf_systemerror()

## Auswertungsdatum für täglich wiedereingespoolte Liste das Ausführungsdatum

## sein soll

sieh Bsp. bei uf_AnyToInputString - "\^h" für heute im Queryfenster
eingeben

2 DWs mit mehreren Zeilen, deren Tabellen eine 1 : n- Beziehung haben -
F- Key- Probelem beim Löschen einer Zeile der 1- Tabelle

-   Beim Speichern wird im 1- DW vom DW- Update Zeile DELETEd ( FKEY-
    Verletzung im n- DW, wenn das 1- DW als erstes gespeichert wird
-   Wenn das n- DW als erstes gespeichert wird, gibt es das gegengleiche
    Problem beim INSERT
-   Lösung:
-   im BeforeDeleteLine des 1- DWs:
-   Für alle zugehörigen Zeilen des n- DWs:
-   uf_SetItemStatusNew
-   uf_DeleteLine
-   im ForDeletedRowOnUpdate des 1- DWs:
-   SQL: DELETE FROM n-DW-Tabelle WHERE Pkey-1-DW-Tabelle

Ein Window im MDE-Modus öffnet sich und schließt sich sofort wieder

Es wird beim Öffnen der Focus auf ein nicht MDE-fähiges DW gesetzt -
muss im Event DwFocusNeu richtig gesetzt werden.

## letzte Windowgröße und Position speichern

Mit dem PfuFun Release 696 wird für jedes Window die letzte Position und
Größe beim Schließen gemerkt und beim nächsten Öffnen wird an dieser
Position mit der selben Größe das Window angezeigt. Ist ebenfalls
abhängig vom User, Winmodus und ob es von einem Parent-Window geöffnet
wurde. Die Größenprüfung des Windows auf 800x600 entfällt.

Mögliche Ursachen warum dies nicht funktioniert: - Event Position des
Windows ist übersteuert - Event OnClose des Windows ist übersteuert

Hinweis: - die Größe und Position eines minimierten bzw maximierten
Window wird nicht gespeichert. - Bei Windows die im Batch-Modus geöffnet
werden, wird die Größe und Position nicht gespeichert.

Grid Export Markierung in Clipboard für Insert in Excel - Problem \##
numerische Felder

CopyRight by Josef K.

Wenn vom Powerbuilder die Formatierung von Werten nicht richtig
übernommen wird, so liegt das an den Einstellungen. \## \[pic\]

Entweder im Betriebssystem unter "Region und Sprache" das "Symbol für
\## Zifferngruppierung" einstellen

## \[pic\]

Dann kann im Excel die Checkbox "Trennzeichen vom Betriebssystem \##
übernehmen" angehakt sein (bleiben)

## \[pic\]

Oder die Checkbox wegnehmen und das Tausendertrennzeichen hier
eintragen!

## Beispiel für Workflow

-   dazu folgende Abkürzungen
    -   WFO ... WorkFlowObjekt (Row in pfu_wfo)

    -   WFPersO ... WorkFlowPersonObjekt (Row in pfu_wfo_applpers)

    -   AO ... Applikationsobjekt (z.B. ein Artikel)

    -   Kassenmitarbeiter bemerkt, dass der Listenpreis nicht mit dem
        ausgezeichneten Preis übereinstimmt
-   in diesem Fall muss ein Mitarbeiter der Preisabteilung den Preis
    korrigieren
-   folgender Ablauf: . Kassenmitarbeiter löst die Funktionalität
    Preiskorrekturanforderung aus (die Position bleibt nicht
    verspeichert am Schirm) . dadurch wird folgendes WFO erzeugt
-   AO des WFOs ist der Artikel der Kassenposition
-   für jede Person der Preisabteilung wird ein WFPersO angelegt, und
    wenn die Person online ist, wird das "NeuesWFO"- Window eingeblendet
    (= das kleine rote oben links)
-   Art des WFO ist "zu erledigende Aufgabe -- Preiskorrektur"
-   WFO- Text beinhaltet den Preis lt. Auszeichnung (dieser muss vorher
    vom Kassenmitarbeiter eingegeben werden) . der erste Mitarbeiter der
    Preisabteilung, der Zeit hat, Klickt auf das "NeuesWFO"- Window,
    öffnet damit das "WFO"- Window und sieht unter anderem das neue WFO
    . der Mitarbeiter nimmt das WFO an ( damit bekundet er für alle
    sichtbar, dass er sich des Problems annimmt . Der Mitarbeiter öffnet
    jetzt vom "WFO"- Window aus das "Artikel"- Window für den zu
    bearbeitenden Artikel mittels der Öffnen- Funktionalität . es gibt
    jetzt 2 mögliche Szenarien:
    -   die Preisauszeichnung ist korrekt und der Listenpreis falsch
        eingetragen . Der Mitarbeiter führt die notwendige
        Preiskorrektur durch und schließt das "Artikel"- Window . der
        Mitarbeiter setzt den Zustand des WFOs auf erledigt . dadurch
        wird ein weiter unten beschriebener Job eingespoolt . der
        Mitarbeiter schließt das "WFO"- Fenster und ist fertig . der
        eingespoolte Job wird verarbeitet und es geschieht folgendes: .
        es wird lt. Generierungsstammdaten ein neues WFO erzeugt:
-   AO ist der Artikel (müsste nicht unbedingt so sein, könnte auch leer
    sein)
-   nur ein WFPersO, nämlich für den Kassenmitarbeiter
-   Art des WFO ist "Information -- Preiskorrektur erfolgt" . der
    Kassenmitarbeiter öffnet wie oben beschrieben das "WFO"- Window mit
    dem neuen WFO und bestätigt dieses - damit ist es erledigt . der
    Kassenmitarbeiter löst eine neue Preisfindung aus und der
    Kassiervorgang geht weiter
    -   der Listenpreis ist korrekt und die Preisauszeichnung falsch .
        Der Mitarbeiter gibt bekannt, dass die Preiskorrektur nicht
        durchgeführt werden darf indem er das WFO "verweigert" . dadurch
        wird ein weiter unten beschriebener Job eingespoolt . der
        Mitarbeiter schließt das "WFO"- Fenster und ist fertig . der
        eingespoolte Job wird verarbeitet und es geschieht folgendes:
-   hier gibt es unzählige Möglichkeiten, nachfolgend sind 2 Beispiele
    beschrieben:
    -   sofortige Rückmeldung an den Kassier . es wird lt.
        Generierungsstammdaten ein neues WFO erzeugt:
-   AO ist der Artikel
-   nur ein WFPersO, nämlich für den Kassenmitarbeiter
-   Art des WFO ist "Information -- Preiskorrektur abgelehnt" . der
    Kassenmitarbeiter öffnet wie oben beschrieben das "WFO"- Window mit
    dem neuen WFO und bestätigt dieses
-   damit ist es erledigt . der Kassenmitarbeiter teilt dies dem Kunden
    mit, und dieser entscheidet, was er tut (nicht kaufen, trotzdem
    kaufen, Rechtsanwalt androhen, ...)
    -   Rücksprache mit der Geschäftsleitung . es wird lt.
        Generierungsstammdaten ein neues WFO erzeugt:
-   AO ist der Artikel
-   nur ein WFPersO, nämlich für den Kassenmitarbeiter
-   Art des WFO ist "Information -- Preiskorrektur bei Geschäftsleitung"
    . es wird lt. Generierungsstammdaten ein neues WFO erzeugt:
-   AO ist der Artikel
-   je ein WFPersO, pro Mitarbeiter der Geschäftsleitung
-   Art des WFO ist "Anforderung zur Schlichtung Preisdifferenz" . die
    Geschäftsleitung bearbeitet in der oben beschriebenen Art das WFO
    und es gibt dann zwei Möglichkeiten:
    -   Preiskorrektur abgelehnt
-   wird durch "verweigern" des WFOs dem System bekanntgegeben . es geht
    weiter wie bei "sofortige Rückmeldung an den Kassier"
    -   Preiskorrektur durchführen
-   wird durch "annehmen" des WFOs dem System bekanntgegeben . es wird
    lt. Generierungsstammdaten ein neues WFO erzeugt:
-   AO ist der Artikel
-   je ein WFPersO pro Mitarbeiter der Preisabteilung
-   Art des WFO ist "zu erledigende Aufgabe - Preiskorrektur von
    Geschäftsleitung bestätigt"
-   die Aufgabe ist lt. WFO- Art zwingend zu erledigen ( WFO kann nicht
    "verweigert" werden . es geht weiter wie oben beschrieben,
    allerdings hat ein Mitarbeiter der Preisabteilung nur die
    Möglichkeit das WFO als erledigt zu melden, nachdem er es angenommen
    hat
    -   ein neu angelegter Artikel muss vom Abteilungsleiter genehmigt
        werden, dass er verwendet werden kann
-   folgender Ablauf: . Mitarbeiter legt den Artikel an und speichert -
    der Artikel ist noch inaktiv . dadurch wird folgendes WFO erzeugt
-   AO des WFOs ist der angelegte Artikel
-   nur ein WFPersO, nämlich für den Abteilungsleiter
-   Art des WFO ist "Umstand anzunehmen -neuer Artikel" . der
    Abteilungsleiter holt sich das WFO wie beschrieben "auf den Schirm"
    . zwei Möglichkeiten:
    -   der Abteilungsleiter gibt den Artikel zur Verwendung frei, indem
        er das WFO "annimmt" . bei der Verarbeitung des entsprechenden
        Jobs wird der Artikel auf "aktiv" gesetzt - dies wird
        Programmintern dadurch erreicht, dass das "Artikel"- Window
        ferngesteuert wird und das "WfoAktion"- Event aufgerufen wird -
        im Script wird dann das "aktiv"- Setzten durchgeführt.
    -   der Abteilungsleiter verweigert die Verwendung des Artikels,
        indem er das WFO "verweigert"
-   es sind mit dem bisher beschriebenen Repertoire die verschiedensten
    Abläufe realisierbar
-   der einfachste ist, den Umstand mit einem "Information"- WFO der
    Artikelabteilung mitzuteilen
-   den Grund für die Verweigerung sollte der Abteilungsleiter im
    Artikel vermerken

## Basis- bzw. Paket- übergreifende PBLs

## pfu_fun + pfu_win + pfu_sys_fun

-   ILV- Projekt: Kunde= 21694, Nr.=1 -- "Powerbuilder
    Basisinfrastruktur"
-   Aktuelle Filenamen:
-   pfu_fun_060324.pbl
-   pfu_win_060324.pbl
-   pfu_sys_fun_060324.pbl
-   Entwicklungsstand unter:
    P:`\Pfundner`{=tex}`\pfu`{=tex}\_fun\\060324`\ErledigtNichtReleased`{=tex}
-   ReleseStand unter:
    P:`\Pfundner`{=tex}`\pfu`{=tex}\_fun\\060324`\Released`{=tex}

## pfu_oi

-   ILV- Projekt: Kunde= 21694, Nr.=18 -- "Office Integration"
-   Aktueller Filename: pfu_oi_060324.pbl
-   Entwicklungsstand unter: P:`\Pfundner`{=tex}`\pfu`{=tex}\_oi\\060324
-   ReleaseStand = Entwicklungsstand

## Team-System / .Net

## Organisation einer Solutuion

## Allgemein

-   Die Bibliotheken und Programme, die im Zusammenhang mit
    TC/Powerbuilder benötigt werden befinden sich im Team-System-Server
    namens PCS auf PCS- TFS-01.pfundner-wohlmann.intern
    (Url=http://PCS-TFS-01:8080/tfs/pcs) - aktuell per 24.11.2020
-   Die Organisation ist nicht optimal, es wäre allerdings zu viel
    Arbeit dies komplett umzustellen
-   Es gibt folgende aktiven Team- Projects:
    -   Bibliotheken
-   Hier liegt z.B. \`PCS Interop´
    -   Scripts
-   Noch nicht klar, ob dies bleibt - wurde für die Scripts zu
    automatischen Manifest- Erstellung beim Build eingeführt
-   Hier befinden sich Scripts, die von Solutions / Projects verwendet
    werden
    -   Sonstige Tools
-   Hier liegt z.B. \`PCS Servicecontroller´
-   Ein Folder in einem Team- Project entspricht jeweils einer Solution
    (außer bei Scripts)
-   Für jedes Project, das nicht in die Solution verlinkt ist, gibt es
    einen Unterordner
-   Das .sln- File liegt direkt im Ordner der Solution
-   Das jeweilige Dokumentations- (Word)- Dokument ist in die Solution
    eingebunden
-   Bei einer Bibliothek im Project der eigentlichen Bibliothek (z.B.
    `\PCS`{=tex} Interop`\Pcs`{=tex}.Interop)
-   Bei einer Solution für eine Applikation liegt das Dokument direkt
    unter der Solution - im Solution- Explorer wird dazwischen
    allerdings ein virtueller Ordner \`Solution Items´ angezeigt
-   Bis jetzt wurde jede Version (einer Bibliothek / Applikation)
    aufbehalten dies galt für Dokumentation, Source und exe/dll und
    exe/dll auch noch in 32 und 64 Bit- Version - dies machen wir nicht
    mehr, weil die Daten aus dem Team-System abrufbar sind (get specific
    Version)
-   ACHTUNG: bei released Projects dürfen nur lieferbare Änderungen
    eingecheckt werden - wenn Zwischenstände eingecheckt werden sollen,
    siehe Branches
-   Um das Abrufen einer alten Version zu ermöglichen verwenden wird die
    Label- Funktionalität

## Neuanlage eines Team-Projects

. File ( NewTeamproject . \[pic\] . durchzuppen bis Finish .

## Neuanlage einer Solution im Visual Studio

. File ( NewProject . New Project- Dialog sinngemäß folgendermaßen
ausfüllen: \[pic\] . Im Source Control Explorer für den äußersten Ordner
der folgendes durchführen: . einchecken . mittels \`Kontextmenü (
rename´ sinngemäß folgendermaßen umtaufen: PCS Interop UI Controls -
Dies hat ein lieber Kollege so eingeführt, und dass wir ein
einheitliches Erscheinungsbild haben, behalten wir das bis auf weiteres
einmal bei . Einchecken

## Neuanlage eines Projects innerhalb der Solution

. Im Solution Explorer mittels Kontext-Menü auf die Solution: Add ( New
Project . New Project- Dialog sinngemäß folgendermaßen ausfüllen:
\[pic\] . Im Solution Explorer Check in auf die Solution

## Hinzufügen (= verknüpfen) eines bestehenden Projects zur Solution

. Im Solution Explorer mittels Kontext-Menü auf die Solution: Add (
Existing Project . New Project- Dialog sinngemäß folgendermaßen
ausfüllen: \[pic\] . Im Solution Explorer Check in auf die Solution -
ACHTUNG: wenn jetzt innerhalb dieser Solution etwas an Pcs.Interop
geändert wird, erfolgt dies an der Original- Pcs.Interop!!!

## Verschiedenes

-   Im Normalfall ist es sinnvoll, unter Tools ( Options ( Source
    Control ( Visual Studio Team Foundation Sever \`Get latest version
    of item on checkout´ anzuhaken.
-   Wenn man allerdings eine alte Version wieder herstellen möchte, darf
    dies nicht angehakt sein
-   der lokale Speicherort der TeamSystem- Projekte kann im
    SourceControlExplorer mittels Kontextmenü ( \`Remove Mapping´ auf
    den TeamSystemServer (pcssrv016`\PCS`{=tex}) eingestellt werden

## ACHTUNG derzeit sind nicht alle Solutions OK

-   Per 6.10.2014 sind folgende Solutions auf diesem Stand und
    funktionsfähig:
    -   Bibliotheken
    -   PCS Interop
    -   PCS Interop UI Controls
    -   Sonstige Tools
    -   PCS Communication Daemon
    -   PCS Service Controller
-   Die noch nicht umgebauten sollte man umbauen, bevor man sie
    verwendet
-   Wenn die pcs.interop referenziert wird, muss zumindest alles die
    PCS.Interop betreffende aus dem nachfolgenden Punkt durchgeführt
    werden
-   Umbau einer Solution: . Solution explorer: . Kontext- Menü der
    Solution: Project Dependencies - Abhängigkeit von der PCS.Interop
    ermitteln und aufschreiben (wird weiter unten benötigt) .
    SourceControl- Explorer: . Es dürfen keine pending changes (von
    irgendjemandem) vorhanden sein . Get specific Version - Latest
    Version - mit overwrite . für jeden Project-Folder: Kontext-Menü -
    move -- `Source-Code´ aus Pfad entfernen . die Ordner`Dokumentation´
    und `Releases´ auf`zzz nicht mehr verwenden -- ´ + den alten Namen
    umbenennen . Solution einchecken . \`Source-Code´- Ordner muss leer
    sein ( Delete ( einchecken . .sln doppelklicken
-   \`Projects have recently been added to this solution. Do you want to
    get them from source control?´ mit No beantworten . File- Explorer:
    . Dokumentationsfiles vom Dokumentation- Ordner in den Solution-
    Ordner kopieren . Solution explorer: . Pcs.Interop entfernen und neu
    hinzufügen (Add existing Project), wenn (unavailable) dahinter
    steht. (Wenn dies nicht dahinter steht handelt es sich hochgradig um
    eine lokale Kopie - bitte Rücksprache mit hmp) . Kontext- Menü der
    Solution: Project Dependencies - Abhängigkeit von der PCS.Interop
    wieder eintragen . Rebuild Solution . Fehler kontrollieren und ggf.
    Referenzen auf die Pcs.Interop eintragen . Solange Rebuild Solution
    und ggf. Korrektur, bis keine Fehler mehr
-   einige Solutions waren von der Build- Konfiguration (Debug/Release,
    x86/x64) "versaut" . Für jedes Doku- File: . Je nach dem (siehe
    oben) Kontextmenü für den Solution- Folder bzw. den Bibliothek-
    Project- Folder aufrufen und Add - Existing Item durchführen .
    Solution einchecken . Im SourceControl- Explorer Label für die
    Solution erstellen (siehe oben)

## Problematik x86 / X64

-   21.4.16: ACHTUNG - Konzept in ARBEIT
-   wir verwenden jetzt auch AnyCpu - allerdings muss das genau
    durchdacht sein
-   die Doku hier muss diesbezüglich überarbeitet werden
-   Assemblies, die von PB verwendet werden, dürfen nie AnyCpu sein!!!
-   Assemblies, die auf Assemblies mit fixer Bitness referenzieren,
    dürfen nicht AnyCpu sein !!!
-   die Referenz im Project muss im .VbProj- File manuell überarbeitet
    werden:
    `<Reference Include="1.v5.dll" Condition="'$(Platform)'=='x86'">`{=html}
    `<SpecificVersion>`{=html}False`</SpecificVersion>`{=html}
    `<HintPath>`{=html}x86\\1.v5.dll`</HintPath>`{=html}
    `<Private>`{=html}False`</Private>`{=html} `</Reference>`{=html}
    `<Reference Include="1.v5.dll" Condition="'$(Platform)'=='x64'">`{=html}
    `<SpecificVersion>`{=html}False`</SpecificVersion>`{=html}
    `<HintPath>`{=html}x64\\1.v5.dll`</HintPath>`{=html}
    `<Private>`{=html}False`</Private>`{=html} `</Reference>`{=html}

Sodass Manifest erstellt wird: \[pic\]

-   Bibliotheken müssen für den Einsatz mit Powerbuilder immer in der
    x86- Version gebuildet werden!
-   Applikationen werden derzeit hochgradig sowohl in einer x86 als auch
    einer x64- Version bereit gestellt - dabei ist folgendes unbedingt
    zu beachten:
-   Die Build- Konfiguration (Kontext- Menü der Solutuion -
    Configuration- Manager) muss sowohl für x86 als auch für x64
    angelegt sein
-   Für jedes Project muss \` Target CPU´ (Properties des Project -
    Register Compile - Button Advanced Compile Options) sowohl für die
    x86 als auch für die X64- Konfiguration lt. vorigem Punkt richtig
    eingestellt sein
-   Es darf nirgends any CPU verwendet werden!!!
-   Es darf in keiner Konfiguration x86 und x64 gemischt werden
-   Für Project- Referenzen gilt:
-   Bei Referenzen auf Assemblies, deren Project Teil der Solution ist,
    muss man sich nicht um die Bitness kümmern
-   Referenzen auf COM- Klassen müssen unbedingt als solche eingetragen
    sein ( in der Spalte Type muss COM stehen ( dann braucht man sich
    nicht um die Bitness zu kümmern (bis jetzt war es zumindest immer
    so)
-   Es wird hier eine dll im exe/dll- Verzeichnis des Build angelegt -
    diese ist aber nur für das Studio intern und ist nicht für den
    Deploy bestimmt
-   Bei Service- References braucht man sich um die Bitness ebenfalls
    nicht zu kümmern
-   Referenzen auf das .NET- Framework werden immer (also auch wenn man
    lt. aktueller Konfiguration eine x64 dll erzeugt) mit x86 angezeigt
-   Beim Verweis auf dlls, die nicht zum .net- Framework gehören und die
    nicht als Project-Reference eingetragen sind gilt folgendes:
-   Eigentlich müsste man vor dem Build die jeweilige Reference
    entfernen und eine neue der Ziel- Bitness entsprechende Referenz
    eintragen
-   Bis jetzt war dies bei uns nicht nötig
-   ACHTUNG: allerdings muss man darauf achten, dass eine solche dll für
    die Installation nicht aus dem Build- Verzeichnis (also dort wo die
    entsprechende Project- dll erzeugt wird) genommen wird!!!
-   Falls es einmal Probleme geben sollte, gibt es noch die Option die
    Referenz im .vbproj- File manuell so umzubauen, dass sie abhängig
    von der Build- Konfiguration ist (bei StackOverflow habe ich
    diesbezüglich etwas gefunden)

## Versionsnummern

-   Bei Libraries, die via COM/OLE/Active-X verwendet werden, haben wird
    folgende Konvention für die Versionsnummern:
-   1.  Nummer: Hauptversion
-   2.  Nummer: Release
-   wenn sich dies Ändert, mus auch folgendes geschehen:
-   Releasen in der ILV
-   Label erzeugen
-   nach P:`\Installationsvorlagen `{=tex}kopieren (dll+manifest)
    (bereitstellen lt. RB)
-   Anmerkung: für die ErledigtNichtReleased- pfu_fun wird entweder
    sofort ein Interop-Release (mit allen oben beschriebenen
    Aktivitäten) gemacht oder nur die 4. Nummer erhöht -\> wer die
    ErledigtNichtReleased- Version verwenden will muss sich die Interop
    aus dem Teamsystem holen
-   3.  Nummer: Branch
-   Ist Standard-mäßig 0
-   Ist beim 1. Änderungs-Branch 1, usw.
-   4.  Nummer: Build
-   Wird bei jedem Build, bei dem eine neue Klasse hinzugekommen oder
    eine Klasse gelöscht worden ist um 1 erhöht
-   Wenn es Probleme mit dem Manifest gibt, kann auch eine Erhöhung
    notwendig sein

## Branches

-   Es kann vorkommen, dass nicht lieferbare Zwischenergebnisse in das
    Teamsystem eingecheckt werden sollen/müssen - folgende mögliche
    Gründe:
-   Der Stand soll gesichert werden
-   Es arbeiten mehrere Programmierer daran
-   ... \< Es ist dann im Source Control Explorer folgendes zu
    unternehmen: . Solution einchecken
-   ACHTUNG: ( Der Branch muss angelegt werden, bevor Änderungen
    durchgeführt worden sind!!! . Kontext-Menü auf den äußersten Ordner
    der Solution ( Branching and Merging ( Branch .. . Der folgende
    Dialog ist sinngemäß folgendermaßen auszufüllen: \[pic\] . Den
    ursprünglichen Ordner und den neu entstandenen Branch-Ordner
    einchecken . Ab jetzt wird mit der Solution im Branch-Ordner
    gearbeitet . Wenn die Änderungen abgeschlossen sind: . Der
    ursprüngliche Ordner darf keine pending Changes aufweisen . Den
    Branch-Ordner einchecken . Kontextmenü auf den Branch Der folgende
    Dialog ist sinngemäß folgendermaßen auszufüllen: \[pic\] . Original-
    Ordner im Source Control Explorer markieren und File ( Source
    Control ( Branching and Merging ( Convert to Folder . Den Branch-
    Ordner löschen . Beide Ordner einchecken
-   Wenn ein alter Branch-Ordner im Weg ist (es wird eine entsprechende
    Fehlermeldung ausgegeben) und dieser aber schon gelöscht ist, muss
    dieser permanent gelöscht werden: Endgültiges Löschen aus dem
    Teamsysten
-   ACHTUNG !!! :
-   Wenn im Änderungs-Branch einer Solution Änderungen an einem Project,
    das nur in die Solution hinein verknüpft ist, durchgeführt werden,
    erfolgen diese nicht im Änderungs-Branch sondern im Original.
-   Man müsste, wenn man das nicht will, einen Branch des Solution der
    referenzierten Projects erstellen (nachfolgend als
    Änderungs-Branch-2 bezeichnet) und im Änderungsbranch der Solution
    das entsprechende Project gegen das von Änderungs-Branch-2
    austauschen - Achtung: davon sind natürlich auch Referenzes
    betroffen. Vor dem Mergen müsste man dann zuerst Änderungs-Branch-2
    mergen und dann wieder das Project von Änderungs-Branch-2 gegen das
    Original- Project tauschen.

## Labels

-   Ermöglichen mittels \`get specific Version´ eine bestimmte Version
    zu laden
-   Immer nachdem eine lieferbare Version eingecheckt worden ist, wird
    die Solution mit einem Label versehen.
-   ACHTUNG: wenn Änderungen an einem Project über eine Solution, in die
    es nur hinein-verknüpft ist, durchgeführt worden sind, ist natürlich
    der primäre Solution- Ordner dieses Project's zu labeln!
-   Hier ist die Namenskonvention für ein Label:
    -   Solution- Ordner- Name - z.B. \`PCS Communication Daemon´
-   Nachdem der Scope für den Label- Namen das Team- System ist, muss
    dieser enthalten sein, um Eindeutigkeit herzustellen
    -   " - "
    -   Version in der Form 02.02.00.00
-   Wenn ein durch Punkt getrennter Teil der Version bei einer
    gelabelten Version immer 0 ist, wann er weggelassen werden (siehe
    Versionsnummern)
    -   " - "
    -   Release- Datum lt. ILV in der Form 2014-10-06
    -   Release- Code lt. ILV (dieser ist ja meistens leer)
-   Also z.B.: \`PCS Communication Daemon - 02.03 - 2014-10-03a´
-   Wenn, was ja eigentlich nicht vorkommt .-), mit der gleichen Release
    eingecheckt wird, muss vorher das Label gelöscht werden
-   das Anbringen eines Labels erfolgt folgendermaßen: . File ( Source
    Control ( Advanced ( Apply Label

## Endgültiges Löschen aus dem Teamsysten

-   Anmerkung: gelöschte Objekte können im Source Control Explorer
    angezeigt werden: dazu unter Tools ( Options ( Source Control (
    Visual Studio Team Foundation Sever \`show deleted items ..´ anhaken
-   kann z.B. bei Branches notwendig sein
-   ist über das Visual Studio Command Prompt möglich
-   dazu ein Beispiel: tf destroy "\$/Bibliotheken/TEST x1"
-   die ausführliche Beschreibung findet man hier:
    http://msdn.microsoft.com/en-us/library/bb386005(v=VS.100).aspx

## EntityFramework

-   siehe Pcs.EntityFramework.Model
-   bis auf weiteres gibt es eine Assembly je Datenbank
-   die Assembly ist ein ClassLibrary
-   das Anlegen Entityframworks für die Datenbank läuft folgendermaßen
    ab: . Add new Item ( . \[pic\]
-   solange wir nur eine Datenbank je Assembly haben, ist der Name fix
    \`Model´ . \[pic\] . \[pic\]
-   dieses Window kommt nicht unbedingt . \[pic\] . \[pic\]
-   hier werden die Objekte aus der Datenbank, die benötigt werden
    ausgewählt
-   wenn es sich um Pcs.EntityFramework.Model handelt, muss
    ModelNamespace =
    `PcsModel´ sein . zum Betrachten der erzeugten Files`show all files´
    einschalten
-   wenn keine vb/cs- Files vorhanden sein sollten könnte folgendes
    nötig sein: . .edmx- File in Solutionexplorer doppelclicken . im
    geöffneten Fenster rechte Maustaste auf den Hintergund ( Add Code
    Generation Item . \[pic\]
-   die Assembly wird in ein Projekt, das sie Verwendet als File-
    Referenz eingebunden - zusätzlich müssen die nachfolgend
    ersichtlichen dll's referenziert werden: \[pic\]
-   bei Problemen mit MetaData kann folgendes helfen: \[pic\]

## WCF

-   Es gibt dazu 2 Demo- und Test- Solutions im Team- System
    (pcssrv016`\PCS`{=tex}):
    -   Sonstige Tools  PCS Test Wcf
-   folgende Projects in der Solution:
    -   PCS.Test.Wcf.Service ( WCF- Server
    -   PCS.Test.Wcf.Common ( von Server und Client verwendet
    -   Sonstige Tools  PCS Test Wcf Client:
-   folgendes Project in der Solution
    -   PCS.Test.Wcf.Client ( WCF- Client
-   folgendes Project in die Solution hineingelinkt:
    -   PCS.Test.Wcf.Common ( PCS.Test.Wcf.Common in Sonstige Tools\
        PCS Test Wcf

## Verschiedenes

Dll dynamisch laden:

-   siehe Assembly.CreateInstance

Files, die ins exe-Verzeichnis müssen, in Solution einbinden:

-   Add zum Projekt (ggf. as link)
-   Property "copy to output directory" auf true setzen

## Problematik COM- Klassen und Registrierung

-   COM- Klassen (Stichworte OLE, OCX, Active-X) werden normalerweise
    mittels regsvr32 bzw. regasm(wenn es sich um managed- Code von .net
    handelt) in der Windows- Registry registriert
-   dabei gibt es folgende Probleme:
-   wenn unterschiedliche Programme unterschiedliche Versionen einer
    COM- Klasse benötigen, können diese nicht am gleichen Windows-
    System installiert werden
-   bei unserer Programmstand- Verteilung müsste nach dem Kopieren jede
    COM- Klassen- dll registriert werden - danach läuft aber die alte
    Programmversion nicht mehr, wenn sich etwas ((eine Signatur) an
    einer COM- Klasse geändert hat
-   weiters würde dazu wieder Remote- Scripting benötigt - damit hatten
    wir sehr oft Probleme

## Lösung Side by Side

-   es gibt seit Windows XP eine Alternative
-   diese Technik wird als "Registration free COM" oder "Side by Side"
    bezeichent
-   beim "Googeln" ist "Side by Side" meistens zielführend
-   es wird auch die Abkürzung SXS verwendet
-   die dll's werden nicht mehr registriert sondern liegen im exe-
    Verzeichnis der Applikation
-   Anmerkung: unter Windows XP gibt es dabei eine "kleine Unschönheit"
    : jede dll muss in einem Subverzeichnis, dessen Name der der dll
    ohne Extension ist, liegen
-   (es könnte allerdings sein, dass dies nur für managed- Assemblies (=
    .net- dll's) gilt - muss man noch verifizieren!!!)
-   diese Version funktioniert allerdings auf W7 & Co auch
-   die COM- Klassen werden über ein Manifest bekanntgegeben

## Manifest

-   ein Manifest ist eine als XML- Dokument organisierte Sammlung von
    Meta- Informationen zu einer Applikation (.exe) oder einer Assembly
    (.dll) - eine Art dieser Informationen beziehen sich auf COM-
    Klassen - diese verwenden wir hier
-   für unsere Zwecke liegen Manifeste im EXE- Verzeichnis und können
    sich entweder in einem eigenen File (externes Manifest) oder direkt
    in einem .exe bzw. im .dll- File (internes Manifest) befinden
-   weiters unterscheiden wir das Applikationmanifest und die Assembly-
    Manifeste
-   alle verwendeten COM- Klassen müssen in einem Manifest beschrieben
    sein - entweder im Applikationmanifest oder im Assembly- Manifest

## externes Manifest

-   wie oben beschrieben
-   wenn wir ein Manifest erstellen, verwenden wir ein solches

## internes Manifest

-   wie oben beschrieben
-   ein internes Manifest befindet sich hochgradig als Ressource Nummer
    1 im Code- File (.exe/.dll)
-   es gibt zwar Tools um ein internes Manifest anzulegen, wir haben
    allerdings schlechte Erfahrungen damit gemacht
-   es ist z.B. oft so, dass das Codefile eine Prüfsumme gespeichert hat
    ( wenn dann im Nachhinein das Manifest eingebettet wird, ist diese
    nicht mehr gültig

## Applikationsmanifest

-   das Applikationmanifest trägt den Namen der Applikation inklusive
    ".exe" plus der Extension ".manifest" und gilt für die gesamte
    Applikation, wenn es als externes Manifest ausgebildet ist
-   auf Windows XP wird immer das externe Manifest verwendet, wenn es
    ein solches gibt
-   auf späteren Betriebsystemen wird das interne Manifest verwendet,
    wenn es ein solches gibt
-   allerdings kann dieses Verhalten folgendermaßen auf das XP-
    Verhalten umgestellt werden:
-   unter dem Registry- Key
    HKEY_LOCAL_MACHINE`\SOFTWARE`{=tex}`\Microsoft`{=tex}`\Windows`{=tex}`\CurrentVersion`{=tex}`\SideByS`{=tex}
    ide wird folgendes DWORD angelegt bzw. gesetzt:
-   Name= PreferExternalManifest
-   Wert=1
-   ACHTUNG
-   dies muss in einem 64-Bit- Windows in der 64-Bit- Registry erfolgen
-   es ist möglich, dass man sich neu anmelden muss, um die Änderung
    wirksam zu machen (nicht verifiziert)
-   nachdem dies natürlich für die gesamte Windows- Maschine gilt, muss
    man auf Nebenwirkungen achten!!!
-   bei einer fremden Applikation kann es jetzt sein, dass sie ein
    internes Manifest hat - dann hat sich folgende Vorgangsweise
    bewährt: . die ".exe" wird mittels 7zip (sehr praktisches Tool,
    unter http://www.7-zip.de downloadbar) geöffnet . hochgradig unter
    ".rsrc`\Manifest`{=tex}" ist ein Eintrag "1" - mittels rechter
    Maustaste wird dieser mit notepad++ (=unverzichtbarer Editor
    http://notepad-plus-plus.org/) geöffnet und unter dem Namen des
    Application- Manifests abgespeichert . auf Betribsystemen \> XP muss
    das .exe-File vom internen Manifest befreit werden
-   das obige gilt z.B. für pb115.exe!!!
-   Beschreibung fehlt: Assembly- Manifest für eine selbst erstellte
    .net- Applikation
-   für eine Powerbuilder- Applikation hat sich folgende Vorgangsweise
    bewährt: . im PB- Deploy- Project muss unter dem Register Security
    "external Manifest" ausgewählt werden . PB erstellt dann beim Deploy
    ein Manifest, wenn es noch keines gibt
-   ( wenn ein neues erstell werden soll, muss man das alte vorher
    weglöschen - ich sehe dazu allerdings derzeit keine Notwendigkeit .
    dieses Manifest wird dann manuell ergänzt
-   das Application- Manifest muss alle verwendeten COM- Klassen
    enthalten bzw. Referenzen auf Assembly- Manifeste enthalten - es
    gibt 2 Möglichkeiten:
    -   Verweis auf ein Assembly- Manifest :
-   dieser erfolgt aufgrund des "asseblyIdentity"- Eintrags
-   dieser steht im Assembly- Manifest direkt unter dem Assembly- Knoten
    und sieht z.B. folgendermaßen aus:
    `<assemblyIdentity name="Pcs.Lgv.Interop" version="1.0.2.0"
    publicKeyToken="1f8768c71c43aad1"
    processorArchitecture="x86">`{=html}`</assemblyIdentity>`{=html}
-   im Applikationmanifest steht dann direkt unter dem Assebly- Knoten:
    `<dependency>`{=html} `<dependentAssembly>`{=html}
    `<assemblyIdentity name="Pcs.Lgv.Interop" version="1.0.2.0"
    publicKeyToken="1f8768c71c43aad1"
    processorArchitecture="x86">`{=html}`</assemblyIdentity>`{=html}
    `</dependentAssembly>`{=html} `</dependency>`{=html}
-   ACHTUNG: beide assemblyIdentity- Einträge müssen exakt gleich sein!
-   diese Art haben wir noch nicht mit einer not managed Assembly
    getestet - sollten wir mit pdfcreactivex.dll von AmyUni Version 3
    tun
    -   Klasseneinträge das Assembly- Manifests werden ins
        Applikationmanifest kopiert
-   diese Art haben wir bis jetzt nur bei nicht managed- Assemblys
    verwendet
-   wir haben diese Art nur desshalb verwendet, weil in diesem Fall die
    referenzierte Assembly ein internes Manifest enthält (allerdings
    ohne COM- Klassen- Einträgen) und dessen Einträge sich nicht mit
    unseren COM- Klassen- Einträgen "vertragen" (vielleicht kann sich
    Stefan K an die Details erinnern)
-   dabei wird der File- Knoten des Assembly- Manifests direkt unter den
    Assembly- Knoten des Applikationmanifests kopiert
-   Bsp.: `<file name="cdintf.dll" asmv2:size="4809728">`{=html}
    `<hash xmlns="urn:schemas-microsoft-com:asm.v2">`{=html}
    `<dsig:Transforms>`{=html}
    `<dsig:Transform Algorithm="urn:schemas-microsoft-
    com:HashTransforms.Identity" />`{=html} `</dsig:Transforms>`{=html}
    `<dsig:DigestMethod
    Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />`{=html}
    `<dsig:DigestValue>`{=html}yZVu7Yr+ha8vTx/MKPvj4HDHYqI=`</dsig:DigestV
    alue>`{=html} `</hash>`{=html}

`<typelib tlbid="{4856f149-7516-11d3-bbe5-d53dcbd65107}"
version="4.5" helpdir="" resourceid="0"
flags="CONTROL,HASDISKIMAGE" />`{=html}`<comClass clsid="{68b3426b-7559-
11d3-bbe5-d53dcbd65107}" threadingModel="Apartment"
tlbid="{4856f149-7516-11d3-bbe5-d53dcbd65107}"
progid="CDIntfEx.CDIntfEx.4.5" />`{=html}

`<comClass clsid="{4475f8bb-1316-4853-82e6-c6149a7ba4c3}"
threadingModel="Apartment" tlbid="{4856f149-7516-11d3-bbe5-
d53dcbd65107}" progid="CDIntfEx.Document.4.5" />`{=html}
`</file>`{=html}

## Assembly- Manifest

-   ein Assembly- Manifest gilt für genau eine dll (= Assembly)
-   der Filename ist der Name der dll ohne Extension (.dll) plus der
    Extension ".manifest" , wenn es als externes Manifest ausgebildet
    ist
-   beim Assembly- Manifest wird sowohl das externe Manifest als auch
    das interne Manifest ausgewertet!!!
-   das interne Manifest kann entweder mittels 7zip wie oben beschrieben
    oder folgendermaßen ausgeleden werden: . Visual Studio Command
    Prompt (2010) . sigcheck -m xy.dll
-   für eigene Einträge hat sich das externe Manifest bewährt - ein
    solches stellen wir folgendermaßen her: \> Manifest für eine
    "managed Assembly" (=.net dll) . Start
    Menu`\Programs`{=tex}`\Microsoft `{=tex}Visual Studio
    2010`\Visual `{=tex}Studio Tools`\Visual `{=tex}Studio Command
    Prompt (2010) aufrufen --\> es kommt DOS- Box (unter W7 &Co kann es
    nicht schaden, dies als Administrator aufzurufen) . Wechsel ins
    Verzeichnis mit der dll . mt
    -managedassemblyname:Pcs.Lgv.Interop.dll -nodependency
    -out:Pcs.Lgv.Interop.manifest
-   Pcs.Lgv.Interop ist natürlich ein Beispiel
-   wenn das Manifest-File bereits existiert muss es vorher weggelöscht
    werden . das Manifest- File kann jetzt mittels notepad++
    strukturiert werden (Zeilenvorschübe, Einrückungen) . im erstellten
    Manifest- File muss jetzt jeweils für jede Klasse runtimeVersion=""
    durch runtimeVersion="v4.0.30319" ersetzt werden, wenn die Assebly
    unter .net- Framework \>= 4.0 erstelt worden ist
-   "v4.0.30319" lässt sich für jede .net- Version z.B. folgendermaßen
    ermitteln: . regasm Pcs.Lgv.Interop.dll /regfile . es wird dadurch
    ein File Pcs.Lgv.Interop.reg erstellt - darin steht die Version
-   dies muss allerdings nur bei Wechsel der Framework- Version gemacht
    werden
-   wenn dies nicht geschieht, kommt es zur Fehlermeldung "object could
    not be created" (oder so ähnlich) Das Erstellen des Assembly-
    Manifests kann auch automatisiert werden:

1.  folgende Tools unter
    C:`\PCS`{=tex}`\Programme`{=tex}`\Tools `{=tex}installieren -- diese
    sind unter
    P:`\InstallVorlagen`{=tex}`\Allgemein`{=tex}`\Tools `{=tex}für
    Entwicklungsrechner`\Pcs`{=tex}-Scripts zu finden

```{=html}
<!-- -->
```
a.  SetEnvVisualStudio.cmd
b.  ManifestFertigstellen.ps1

```{=html}
<!-- -->
```
2.  Im Projekt- Verzeichnis (in dieses gelangt man, wenn man im
    SolutionExplorer mit der rechten Maustaste auf das Project clickt
    und "Open Folder in Windows Explorer" wählt) das File PostBuild.bat
    erstellen - als Vorlage kann
    C:`\Projekte`{=tex}`\TFS`{=tex}`\PCS`{=tex}`\Bibliotheken`{=tex}`\PCS`{=tex}.Interop.UI.Controls`\PCS`{=tex}.Interop
    .UI.Controls`\PostBuild`{=tex}.bat verwendet werden - im Allgemeinen
    ist dabei lediglich PCS.Interop entsprechend zu ersetzen
3.  PostBuild.bat ins Team- System integrieren!
4.  Im Register Compile der Project- Properties über den Button "Build
    Events" folgendes eintragen:

\[pic\]

5.  Beim Build wird jetzt im Verzeichnis, in dem die .dll erzeugt wird
    auch ein gebrauchsfertiges Manifest erzeugt

> Manifest für eine "not managed Assembly" .dll . mittels 7zip (ähnlich
> wie oben) die Typelibrary aus der dll extrahieren: . es sollte unter
> .rsrc einen Ordenr TYPELIB geben - darunter z.B. ein Eintrag mit 1 .
> über die rechte Maustaste öffnen mit einem Hex- Editor und unter dem
> Namen xy.tlb speichern (vielleich geht es ja doch einfacher ) . Visual
> Studio Command Prompt (2010) . mt -out:xy.manifest -dll:xy.dll
> -tlb:xy.tlb -identity:"xy, version=1.1" - unter -identity können noch
> folgende Teile stehen: - processorArchitecture="x86" . xy.manifest
> kann jetzt mittels notepad++ strukturiert werden (Zeilenvorschübe,
> Einrückungen) . bei jeder Klasse muss kontrolliert werden, ob ein
> Eintrag wie - progid="Persits.MailSender" vorhanden ist - wenn nicht
> muss dieser angelegt werden. Schlimmsten Falls muss man die DLL auf
> einem sowieso versauten Rechner registrieren und jede Klasse über die
> Klass-ID in der Registry suchen (vielleicht gibt es ja auch noch eine
> Möglichkeit die PogIds anderweitig zu besorgen, vielleicht sogar vi mt
> ( ggf. testen) . wir kopieren jetzt das File- Element ins exe-
> manifest und verwenden das Assembly-Manifest nicht, weil es anders
> Probleme gegeben hat - muss aber nicht immer die Lösung sein .ocx .
> Visual Studio Command Prompt (2010) . mt -out:xy.manifest -dll:xy.ocx
> -tlb:xy.ocx -identity:"xy, version=1.1" - -identity ist notwendig,
> dass das Element \<assemblyIdentity erzeugt wird - unter -identity
> können noch folgende Teile stehen: - processorArchitecture="x86" -
> type ... dafür sehen wir derzeit keinen Bedarf - publicKeyToken ...
> dafür sehen wir derzeit keinen Bedarf . xy.manifest kann jetzt mittels
> notepad++ strukturiert werden (Zeilenvorschübe, Einrückungen)

## Powerbuilder

## MiniDump- Problem

-   PB verursacht bei Abstürzen evtl. "riesige" Dateien mit dem Namen
    *minidump*
-   Folgende Einstellungen können dagegen helfen: \[pic\]

## Bedienung Windows allgemein

## Key- Combinations RDP

## \|was will ich \|was tippe ich \|

\|Ctrl + Alt + Entf \|Ctrl + Alt + End \| \## \|Alt + Tab \|Alt + PageUp
\|

## \|Startmenü \|Alt + Home \|

\|Snapshot RDP- Session \|Ctrl + Alt + Minus \| \|Snapshot aktives
Window \|Ctrl + Alt + Plus \|

## SQL Server

## verschiedenes

-   sp_addsrvrolemember 'pcs`\hpollhammer`{=tex}', 'sysadmin'

## VB-Script

http://programming.top54u.com/post/Vbscript-String-Functions.aspx
Following are the various Vbscript String Functions that can be used in
ASP web pages: 1. InStr: Vbscript InStr string function returns the
index of the first occurrence of initial character of the specified
substring from the provided string. InStr function starts searching from
the left end of the provided string i.e. character at 1st index of the
string.

2.  InStrRev: Vbscript InStrRev string function returns the index of the
    last occurrence of the initial character of the specified substring
    from the provided string. InStrRev function starts searching from
    the right end of the provided string i.e. character at the last
    index of the string.

3.  LCase: Vbscript LCase string function returns string in lower case
    letters.

4.  UCase: Vbscript UCase string function returns the string in upper
    case letters.

5.  Len: Vbscript Len function returns the length of the specified
    string.

6.  Mid: Vbscript Mid string function returns the substring of defined
    length starting from the specified index from the string.

7.  Replace: Vbscript Replace string function replaces the specified
    substring with new string. You can also specify the number of
    matches to be replaced by replace function.

8.  LTrim: vbscript LTrim function removes white space characters from
    the left side i.e. beginning of the string.

9.  RTrim: vbscript RTrim function removes white space characters from
    the right side i.e. end of the string.

10. Trim: Vbscript Trim string function removes white space characters
    from both ends of the specified string.

11. Left: vbscript Left function returns the substring of specified
    length from the left side of a string.

12. Right: vbscript Right function returns the substring of specified
    length from the right side of a string.

13. Space: vbscript space function returns the specified number of white
    space characters.

14. StrComp: Vbscript StrComp string function compares the two string
    expression and returns a value according to the comparison.

15. StrReverse: Vbscript StrReverse string function returns the string
    in reverse order.

16. String: Vbscript string function returns repeating pattern of a
    character of specified length.
