*![img](https://github.com/user-attachments/assets/57ad6660-e56d-46c4-831e-c0891c4e1406)*

# Flight Punctuality Analysis (2015–2017) – Power BI Dashboard

### Ein Data-Analytics-Projekt von **Kamila Rojek**

Willkommen!  
Dieses Repository enthält ein End-to-End Data-Analytics-Projekt zur Analyse der Flugpünktlichkeit an **Airport A** auf Basis historischer Daten aus den Jahren **2015–2017**.  
Ziel der Analyse ist es, **operative Engpässe zu identifizieren**, **Verspätungsmuster sichtbar zu machen** und **datenbasierte Empfehlungen** für das Operations- und Planungsteam des Flughafens abzuleiten.

## Überblick – Was ist das Dashboard?

Dieses Dashboard zeigt die Pünktlichkeit von 1,26 Mio. Flügen an Airport A.
Wichtigster KPI: **70% der Flüge sind unpünktlich (≥ 5 Minuten Abweichung).**
Ziel: Verzögerungsmuster erkennen & operative Entscheidungen unterstützen.

## Was zeigt die Analyse?

- Große Airlines verursachen >80% der Verspätungen → größter Hebel liegt bei ihnen.
- Starke saisonale Schwankungen: Winter & Jahresende besonders kritisch.
- Frühmorgens (2–4 Uhr) kommt es zu massiven Verspätungen, v. a. wegen verspäteter Ankünfte.
- Wochen- und Wochentagsmuster sind stabil → Verzögerungen sind strukturell, nicht zufällig.
- Das Dashboard liefert klare Zusammenhänge zwischen Airlines, Jahreszeiten, Wochen & Tageszeiten.


## Welche Entscheidungen unterstützt sie?

- Ressourcenplanung für Winter & Peak-Phasen
- Enge Steuerung & Monitoring der Top-Airlines
- Optimierung von Gate- und Turnaround-Prozessen
- Verbesserte Arrival-Management-Strategien
- Ableitung operativer SLAs für Airlines

# Dieses Dashboard ermöglicht Führungskräften, Engpässe, saisonale Muster und airline-spezifische Verzögerungen sofort zu erkennen und operative Entscheidungen datenbasiert zu treffen.

 
## Tech Stack: Power BI Desktop (inkl. Power Query & DAX) – komplette Datenaufbereitung, Modellierung und Visualisierung direkt in Power BI ohne externes SQL/Datenbank-Backend
### OLAP-Modell & Datenpipeline

Im Rahmen des Abschlussprojekts habe ich ein holistisches OLAP-System aufgebaut, das den gesamten Lebenszyklus der Flugdaten am Los Angeles International Airport (LAX) abdeckt – von der Rohdatenabfrage bis zur Visualisierung in Power BI.

1. **Datenaufnahme (PostgreSQL + CSV)**  
   - Verbindung zur PostgreSQL-Datenbank `Flight_Data`, Tabelle `flights`, per benutzerdefinierter SQL-Query in Power BI.  
   - Filter bereits auf Datenbankebene: Zeitraum **2015–2017**, nur Flüge **von/nach LAX**, ohne gestrichene oder umgeleitete Flüge (`cancelled = FALSE`, `diverted = FALSE`).  
   - Einlesen der Referenztabelle `UNIQUE_CARRIERS.csv` mit Airline-Codes und -Namen und Verknüpfung über `flights.op_carrier = UNIQUE_CARRIERS.Code`.

2. **Datenbereinigung & Transformation**  
   - Entfernen nicht benötigter Spalten und Umgang mit fehlenden bzw. fehlerhaften Werten.  
   - Konvertierung der Uhrzeiten aus dem numerischen Format `hhmm` in echte Zeitfelder (inkl. Sonderfall `2400`, der auf eine gültige Zeit knapp vor Mitternacht abgebildet wird).  
   - Berechnung zusätzlicher Felder: absolute Verspätungen (Abflug/Ankunft), Klassifikation *pünktlich / unpünktlich* (Schwellwert ≥ 5 Minuten, zu früh und zu spät), Kennzeichnung *arrival/departure* sowie Kalenderattribute (Jahr, Quartal, Monat, Kalenderwoche, Wochentag, Stunde).

3. **OLAP-Modellierung**  
   - Aufbau eines analytischen Modells mit `flights` als zentraler Faktentabelle und `UNIQUE_CARRIERS` als Airline-Dimension.  
   - Trennung von Messgrößen (z. B. Anzahl Flüge, Anteil unpünktlicher Flüge, durchschnittliche Unpünktlichkeit) und Analyseachsen (Airline, Richtung, Zeitraum, Tageszeit).  
   - Vorbereitung der Daten für OLAP-Analysen zu den Kernfragen des Projekts: Top-3-Airlines nach Unpünktlichkeit, Entwicklung der Pünktlichkeit über die Zeit und Muster nach Jahr, Quartal, Monat, Kalenderwoche, Wochentag und Stunde.

4. **Visualisierung & Data Storytelling in Power BI**  
   - Laden des bereinigten Modells nach Power BI Desktop und Aufbau interaktiver Dashboards (Übersicht, Airline-Analyse, Zeit- und Saisonalitätsanalyse).  
   - Einsatz von Slicern (Abflug vs. Ankunft), DAX-Measures und geeigneten Visualisierungen (z. B. Linien-, Balken- und KPI-Kacheln), um die Geschäftsanforderungen des Flughafens zu beantworten.  
   - Verdichtung der Ergebnisse in einer ca. 15-minütigen Management-Präsentation mit Fokus auf Kontext, Narrativ und Handlungsempfehlungen.

5. **Erweiterbarkeit**  
   - Die Kombination aus SQL-Filterung und wiederverwendbaren Power-Query- und DAX-Schritten ist so gestaltet, dass zusätzliche Zeiträume (weitere Monate/Jahre) mit demselben Prozess eingespielt und nahtlos in das bestehende Modell integriert werden können.


# Mehr Infos:
# Projekt-Hintergrund

Airport A ist ein großes US-Drehkreuz mit mehr als **1,26 Millionen An- und Abflügen** im betrachteten Zeitraum (2015–2017). Der Flughafen operiert in einem hochfrequentierten, kapazitätskritischen Umfeld mit zahlreichen nationalen Fluggesellschaften.

Als Data Analyst im Bereich **Operations & Planning** bestand das Ziel der Analyse darin:

- strukturelle Ursachen für Flugverspätungen zu verstehen  
- Leistungsunterschiede zwischen Airlines zu identifizieren  
- saisonale sowie stundenbezogene Pünktlichkeitsmuster sichtbar zu machen  
- operative Entscheidungen durch klare, messbare Insights zu unterstützen  

Die wichtigsten Erkenntnisse und Empfehlungen strukturieren sich in vier Kategorien:

**Kategorie 1:** Performance der Fluggesellschaften  
**Kategorie 2:** Langfristige & saisonale Entwicklungen  
**Kategorie 3:** Muster nach Wochen & Wochentagen  
**Kategorie 4:** Stündliche Delay-Dynamiken & Unterschiede zwischen Ankunft und Abflug  

---

# Datenstruktur & Erste Prüfungen

Das Dataset stammt aus den operativen Flugdaten des Flughafens. Nach der Bereinigung wurden **stornierte und umgeleitete Flüge ausgeschlossen**, und „unpünktliche“ Flüge wurden gemäß Branchenstandard als Abweichung von **≥ 5 Minuten** definiert.

### Datenquellen & Datenmodell

- **`flights`** – Zentrale Tabelle mit allen Flügen von und nach Flughafen A (2015–2017). Enthält u. a. `flight_id`, Airline-Code (`op_carrier`), Route (`origin`, `dest`), geplante und tatsächliche Abflug- und Ankunftszeiten, Verspätungsmetriken (`dep_delay_abs`, `arr_delay_abs`, `abs_delay`, `unpunctual_delay`, `punctuality_status`) sowie abgeleitete Kalenderattribute (Jahr, Quartal, Monat, Woche, Wochentag, Stunde am Flughafen A).
- **`unique_carriers`** – Lookup-Tabelle mit allen im Datensatz vorkommenden Airlines. Beinhaltet den Carrier-Code (`Code`) und den vollständigen Namen der Fluggesellschaft (`Description`) und ist über `flights.op_carrier = unique_carriers.Code` mit der Flugdaten-Tabelle verknüpft.


*<img width="737" height="837" alt="Bildschirmfoto 2025-12-05 um 16 18 45" src="https://github.com/user-attachments/assets/a228e9b5-5b63-48d8-ab5e-947276dcb9a5" />* 

---

# Executive Summary

Airport A weist **erhebliche Pünktlichkeitsprobleme** auf: **70,15 %** aller Flüge weichen um ≥ 5 Minuten vom Zeitplan ab. Drei zentrale Erkenntnisse stechen hervor:

1. **Große Netzwerk-Fluggesellschaften verursachen den Großteil aller Verspätungen**  
   (Southwest, American, SkyWest = >80 % aller unpünktlichen Flüge).

2. **Die Verspätungen folgen einem ausgeprägten saisonalen Muster**,  
   mit starken Spitzen im Winter und in den Feiertagsmonaten zum Jahresende.

3. **In den Nacht- und frühen Morgenstunden treten extreme Verspätungen auf**,  
   insbesondere bei Ankünften, verursacht durch sogenannte *cascading inbound delays*.

Diese Ergebnisse verdeutlichen strukturelle operative Belastungen, die eine **datenbasierte Planung**, eine gezieltere **Ressourcenallokation** und eine intensivere **Koordination mit den wichtigsten Fluggesellschaften** erfordern.

*<img width="1718" height="461" alt="Bildschirmfoto 2025-12-04 um 14 09 14" src="https://github.com/user-attachments/assets/2ec5e41f-119b-41a1-9b29-fa379341dc09" />*

# Insights Deep Dive

---

## **Kategorie 1: Performance der Fluggesellschaften**

- **Insight 1:** Große Airlines (Southwest, American, SkyWest) sind für **über 80 %** aller unpünktlichen Flüge verantwortlich.  
- **Insight 2:** Kleinere Airlines wie Envoy, Frontier und JetBlue weisen **extreme durchschnittliche Verspätungen** von bis zu **40 Minuten** auf, stellen jedoch nur **3,5 %** aller Fälle dar.  
- **Insight 3:** Netzwerk-Airlines mit hohem Flugvolumen zeigen mittlere Verzögerungswerte, prägen jedoch das **gesamte Zuverlässigkeitsprofil** des Flughafens am stärksten.  
- **Insight 4:** Die Leistungsunterschiede verdeutlichen, dass der **größte operative Hebel** bei den Top-5-Airlines liegt.  


*<img width="1486" height="447" alt="Bildschirmfoto 2025-12-04 um 14 12 00" src="https://github.com/user-attachments/assets/d7b0110d-2d77-445d-a46f-9180f8d27d31" />*
*<img width="1496" height="864" alt="Bildschirmfoto 2025-12-04 um 14 12 16" src="https://github.com/user-attachments/assets/4704948a-038f-41ab-a872-cc0e71343d64" />*

---

## **Kategorie 2: Jährliche & Saisonale Trends**

**Insight 1:** Die Pünktlichkeit verschlechterte sich zwischen 2015 und 2017 um nahezu **5 Prozentpunkte**.  
**Insight 2:** Es zeigt sich eine ausgeprägte **U-förmige Saisonalität**: Verbesserungen im Frühling/Sommer, deutliche Einbrüche im Herbst/Winter.  
**Insight 3:** Der Dezember weist durchgehend die **höchste Unpünktlichkeit (>72 %)** auf.  
**Insight 4:** Die Ergebnisse deuten auf eine **zunehmende strukturelle Belastung** hin – verursacht durch steigendes Verkehrsaufkommen, Kapazitätsgrenzen und winterbedingte Betriebsprozesse.  


*<img width="1505" height="868" alt="Bildschirmfoto 2025-12-04 um 14 14 35" src="https://github.com/user-attachments/assets/2f4b329a-a008-4666-a46d-0addbe11dace" />*

## **Kategorie 3: Wöchentliche & Tägliche Muster**

- **Insight 1:** Die Wochen **50–52** zeigen den deutlichsten Peak mit **über 75 %** Unpünktlichkeit.  
- **Insight 2:** Im restlichen Jahresverlauf bleibt die Unpünktlichkeit relativ stabil (ca. **70 %**).  
- **Insight 3:** Es gibt **keine nennenswerten Unterschiede zwischen den Wochentagen** → die Verspätungen sind **nicht kalenderbedingt**, sondern strukturell.  
- **Insight 4:** Die gleichbleibenden Muster über die Wochentage hinweg weisen auf **zugrunde liegende operative Engpässe** hin.  


*<img width="1498" height="859" alt="Bildschirmfoto 2025-12-04 um 14 15 32" src="https://github.com/user-attachments/assets/341e124b-e246-489f-bfa9-b9e188c1a86a" />*

---

## **Kategorie 4: Stündliche Delay-Dynamiken**

- **Insight 1:** Detaillierte Analyse der Verspätungsmuster nach Tageszeit, einschließlich Zeitfenster, quantitativer Werte und erkennbarer Trends.  

- **Insight 2:** Präzisere Beschreibung der Delay-Entwicklung über spezifische Stundenbereiche hinweg, mit Fokus auf Spitzenlasten und deren Ursachen.  

- **Insight 3:** Darstellung von Durchschnitten, Extremwerten und Zusammenhängen zwischen Ankunfts- und Abflugsverhalten über den Tagesverlauf.  

- **Insight 4:** Vertiefende Analyse zur Erklärung struktureller Muster, inkl. Vergleich von Zeiträumen, Trendänderungen und operativen Auswirkungen.  

*<img width="1052" height="600" alt="Bildschirmfoto 2025-12-04 um 14 23 34" src="https://github.com/user-attachments/assets/940c0a38-b634-4c71-846a-bc8cd56bd716" />*

---

# Empfehlungen

Basierend auf den Analyseergebnissen sollte das Operations- und Planungsteam des Flughafens folgende Maßnahmen in Betracht ziehen:

1. **Priorisierung der operativen Zusammenarbeit mit den großen Airlines**, insbesondere jenen, die das höchste Verspätungsvolumen verursachen.  
2. **Optimierung der Winterbetriebsplanung**, einschließlich zusätzlicher Ressourcen für Bodenabfertigung und Enteisung.  
3. **Entwicklung eines Vorhersagemodells** für die besonders kritischen Wochen 50–52 sowie den Dezember-Reiseverkehr.  
4. **Stärkung des Arrival-Managements**, um kaskadierende Verspätungen eintreffender Flüge zu reduzieren.  
5. **Optimierung der Gate- und Turnaround-Planung** während der frühen Morgenstunden, in denen Störungen besonders ausgeprägt auftreten.  

---

# Annahmen und Einschränkungen

Zur Sicherstellung einer klaren analytischen Grundlage wurden folgende Annahmen getroffen:

- Stornierte und umgeleitete Flüge wurden aufgrund mangelnder Vergleichbarkeit ausgeschlossen.  
- „Unpünktlich“ wurde gemäß Branchenstandard als Abweichung von **≥ 5 Minuten** definiert.  
- Verspätungswerte über **500 Minuten** wurden geprüft und nur ausgeschlossen, wenn sie eindeutig fehlerhaft waren.  
- Alle Zeitangaben wurden auf die lokale Flughafenzeit normalisiert.  
- Spitzen in den frühen Morgenstunden wurden als Folge verspäteter Ankünfte aus der Nacht interpretiert (kaskadierende Inbound-Delays).  

---

# Weitere Ressourcen

- **Power BI Dashboard:** [Link]  
- **PDF-Report:** im Repository enthalten

---

# Vielen Dank!



