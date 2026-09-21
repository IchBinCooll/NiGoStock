# Prognose-Batterie — strukturierte Daten für die empirische Auswertung (Bachelorarbeit)

Append-only. Bestehende Zeilen werden NIEMALS gelöscht oder verändert — der Abendreport füllt
nur die Spalten `Ergebnis` und `Ist-Kurs` der jeweils fälligen Zeilen aus. Alles andere bleibt fix.

Der Morgenreport erzeugt an jedem Handelstag je Asset zwei Prognosen (nächster Handelstag = 1T,
eine Woche = 1W). Ziel: sauberer, vergleichbarer Datensatz für Trefferquote und Kalibrierung,
inklusive naiver Baseline (Random Walk) und erzeugendem Modell (für den Modellvergleich Fable vs. Opus).

## Spalten-Legende
- **Datum**: Erstellungsdatum der Prognose (YYYY-MM-DD)
- **Modell**: erzeugendes Modell (z.B. Opus-4.8, Fable-5)
- **Asset**: Ticker/Name (Einzelaktien, die 4 ETFs, Indizes SP500 & MSCIWorld)
- **Horizont**: 1T (nächster Handelstag) oder 1W (5 Handelstage)
- **Prognose**: UP oder DOWN gegenüber Referenzkurs (kein "neutral")
- **Konfidenz%**: 50–95 (50 = reines Raten)
- **Referenzkurs**: Schlusskurs am Erstellungstag
- **Baseline**: naive Prognose = Richtung der letzten Tagesbewegung des Assets (Random Walk)
- **Auflösungsdatum**: Datum, an dem die Prognose geprüft wird (YYYY-MM-DD)
- **Ergebnis**: offen / RICHTIG / FALSCH (vom Abendreport gesetzt)
- **Ist-Kurs**: tatsächlicher Schlusskurs am Auflösungsdatum (vom Abendreport gesetzt)

## Log

Datum | Modell | Asset | Horizont | Prognose | Konfidenz% | Referenzkurs | Baseline | Auflösungsdatum | Ergebnis | Ist-Kurs
2026-08-02 | Opus-5 | SP500 | 1T | UP | 62 | 7489.72 | UP | 2026-08-03 | RICHTIG | 7600.50
2026-08-02 | Opus-5 | SP500 | 1W | UP | 55 | 7489.72 | UP | 2026-08-07 | RICHTIG | 7757.64
2026-08-02 | Opus-5 | AAPL | 1T | UP | 58 | 308.91 | DOWN | 2026-08-03 | FALSCH | 303.42
2026-08-02 | Opus-5 | AAPL | 1W | UP | 55 | 308.91 | DOWN | 2026-08-07 | RICHTIG | 313.33
2026-08-02 | Opus-5 | UNH | 1T | DOWN | 55 | 414.40 | DOWN | 2026-08-03 | FALSCH | 415.36
2026-08-02 | Opus-5 | UNH | 1W | DOWN | 53 | 414.40 | DOWN | 2026-08-07 | RICHTIG | 407.08
2026-08-02 | Opus-5 | ASML | 1T | UP | 60 | 1629.00 | DOWN | 2026-08-03 | RICHTIG | 1642.52
2026-08-02 | Opus-5 | ASML | 1W | UP | 58 | 1629.00 | DOWN | 2026-08-07 | RICHTIG | 1740.99
2026-08-02 | Opus-5 | PEP | 1T | DOWN | 55 | 139.56 | DOWN | 2026-08-03 | FALSCH | 139.63
2026-08-02 | Opus-5 | PEP | 1W | DOWN | 53 | 139.56 | DOWN | 2026-08-07 | RICHTIG | 139.02
2026-08-02 | Opus-5 | ADBE | 1T | DOWN | 53 | 250.41 | UP | 2026-08-03 | RICHTIG | 247.90
2026-08-02 | Opus-5 | ADBE | 1W | DOWN | 56 | 250.41 | UP | 2026-08-07 | FALSCH | 265.21
2026-08-02 | Opus-5 | META | 1T | UP | 55 | 556.71 | UP | 2026-08-03 | RICHTIG | 590.24
2026-08-02 | Opus-5 | META | 1W | UP | 53 | 556.71 | UP | 2026-08-07 | RICHTIG | 592.10
2026-08-02 | Opus-5 | TTWO | 1T | UP | 53 | 242.92 | DOWN | 2026-08-03 | RICHTIG | 247.62
2026-08-02 | Opus-5 | TTWO | 1W | UP | 52 | 242.92 | DOWN | 2026-08-07 | RICHTIG | 246.50
2026-08-03 | Opus-5 | SP500 | 1T | UP | 70 | 7489.72 | UP | 2026-08-04 | RICHTIG | 7737.00
2026-08-03 | Opus-5 | SP500 | 1W | UP | 57 | 7489.72 | UP | 2026-08-10 | RICHTIG | 7753.11
2026-08-03 | Opus-5 | AAPL | 1T | DOWN | 55 | 308.91 | DOWN | 2026-08-04 | FALSCH | 309.38
2026-08-03 | Opus-5 | AAPL | 1W | DOWN | 54 | 308.91 | DOWN | 2026-08-10 | RICHTIG | 308.26
2026-08-03 | Opus-5 | UNH | 1T | UP | 55 | 414.40 | DOWN | 2026-08-04 | FALSCH | 407.55
2026-08-03 | Opus-5 | UNH | 1W | DOWN | 52 | 414.40 | DOWN | 2026-08-10 | RICHTIG | 408.74
2026-08-03 | Opus-5 | ASML | 1T | UP | 58 | 1629.00 | DOWN | 2026-08-04 | RICHTIG | 1711.89
2026-08-03 | Opus-5 | ASML | 1W | UP | 55 | 1629.00 | DOWN | 2026-08-10 | RICHTIG | 1733.48
2026-08-03 | Opus-5 | PEP | 1T | UP | 54 | 139.56 | DOWN | 2026-08-04 | FALSCH | 139.10
2026-08-03 | Opus-5 | PEP | 1W | DOWN | 53 | 139.56 | DOWN | 2026-08-10 | RICHTIG | 137.73
2026-08-03 | Opus-5 | ADBE | 1T | UP | 62 | 250.41 | UP | 2026-08-04 | RICHTIG | 257.49
2026-08-03 | Opus-5 | ADBE | 1W | DOWN | 53 | 250.41 | UP | 2026-08-10 | FALSCH | 272.96
2026-08-03 | Opus-5 | META | 1T | UP | 72 | 556.71 | UP | 2026-08-04 | RICHTIG | 587.94
2026-08-03 | Opus-5 | META | 1W | UP | 56 | 556.71 | UP | 2026-08-10 | RICHTIG | 594.92
2026-08-03 | Opus-5 | TTWO | 1T | UP | 58 | 242.92 | DOWN | 2026-08-04 | FALSCH | 240.22
2026-08-03 | Opus-5 | TTWO | 1W | UP | 53 | 242.92 | DOWN | 2026-08-10 | RICHTIG | 253.57

<!-- METHODIK-HINWEIS 2026-08-04:
     (a) Die Zeilen mit Datum 2026-08-03 tragen als Referenzkurs den Schluss vom 31.07.
         (Lauf um 17:05 MESZ, kein neuer Schluss verfuegbar). Ihr "1T"-Horizont umfasst
         faktisch zwei Handelstage. Nicht ungeprueft in die 1T-Trefferquote einrechnen.
     (b) Die Zeilen mit Datum 2026-08-04 wurden um 16:30 MESZ erzeugt, also nach
         US-Eroeffnung und waehrend des europaeischen Handels. Sie enthalten
         Tagesinformationen (z.B. ASML stand bereits +4 % in Amsterdam). Ebenfalls
         gesondert auswerten.
     (c) MSCIWorld fehlt am 2026-08-04: kein verifizierter Schlussstand vom 03.08.
         ermittelbar. Luecke bewusst offen gelassen statt geschaetzt.
     (d) TTWO Ist-Kurs 03.08. (247.62) steht im Konflikt mit dem aus dem Depotwert
         zurueckgerechneten Wert (~243). Richtung (UP) in beiden Faellen identisch,
         Ergebnis RICHTIG daher robust; Hoehe unsicher.
     (e) ETF-Referenzkurse in EUR (europaeischer Schluss 03.08.), aus dem Depot-Tracker
         zurueckgerechnet (Intraday-Kurs / (1 + Tagesveraenderung)). ASML wird bewusst
         gegen den US-ADR in USD gefuehrt, um Zeitzonen-Vermischung zu vermeiden.
-->
2026-08-04 | Opus-5 | SP500 | 1T | UP | 57 | 7600.50 | UP | 2026-08-05 | RICHTIG | 7723.52
2026-08-04 | Opus-5 | SP500 | 1W | UP | 55 | 7600.50 | UP | 2026-08-11 | RICHTIG | 7728.20
2026-08-04 | Opus-5 | Vanguard FTSE All-World | 1T | UP | 56 | 165.39 | UP | 2026-08-05 | RICHTIG | 167.87
2026-08-04 | Opus-5 | Vanguard FTSE All-World | 1W | UP | 55 | 165.39 | UP | 2026-08-11 | RICHTIG | 168.48
2026-08-04 | Opus-5 | Amundi Nasdaq-100 | 1T | UP | 58 | 101.64 | UP | 2026-08-05 | RICHTIG | 104.18
2026-08-04 | Opus-5 | Amundi Nasdaq-100 | 1W | UP | 54 | 101.64 | UP | 2026-08-11 | RICHTIG | 104.30
2026-08-04 | Opus-5 | HSBC MSCI EM | 1T | UP | 57 | 15.63 | DOWN | 2026-08-05 | RICHTIG | 15.93
2026-08-04 | Opus-5 | HSBC MSCI EM | 1W | UP | 53 | 15.63 | DOWN | 2026-08-11 | RICHTIG | 15.912
2026-08-04 | Opus-5 | Amundi MSCI World | 1T | UP | 56 | 158.64 | UP | 2026-08-05 | RICHTIG | 161.47
2026-08-04 | Opus-5 | Amundi MSCI World | 1W | UP | 54 | 158.64 | UP | 2026-08-11 | RICHTIG | 161.575
2026-08-04 | Opus-5 | AAPL | 1T | UP | 54 | 303.42 | DOWN | 2026-08-05 | RICHTIG | 311.00
2026-08-04 | Opus-5 | AAPL | 1W | UP | 53 | 303.42 | DOWN | 2026-08-11 | RICHTIG | 304.91
2026-08-04 | Opus-5 | UNH | 1T | DOWN | 58 | 415.36 | UP | 2026-08-05 | RICHTIG | 412.75
2026-08-04 | Opus-5 | UNH | 1W | DOWN | 52 | 415.36 | UP | 2026-08-11 | RICHTIG | 402.19
2026-08-04 | Opus-5 | ASML | 1T | UP | 72 | 1642.52 | UP | 2026-08-05 | RICHTIG | 1678.22
2026-08-04 | Opus-5 | ASML | 1W | UP | 56 | 1642.52 | UP | 2026-08-11 | RICHTIG | 1799.38
2026-08-04 | Opus-5 | PEP | 1T | DOWN | 60 | 139.63 | UP | 2026-08-05 | FALSCH | 139.68
2026-08-04 | Opus-5 | PEP | 1W | DOWN | 54 | 139.63 | UP | 2026-08-11 | RICHTIG | 138.41
2026-08-04 | Opus-5 | ADBE | 1T | DOWN | 55 | 247.90 | DOWN | 2026-08-05 | FALSCH | 259.32
2026-08-04 | Opus-5 | ADBE | 1W | DOWN | 54 | 247.90 | DOWN | 2026-08-11 | FALSCH | 263.71
2026-08-04 | Opus-5 | META | 1T | DOWN | 60 | 590.24 | UP | 2026-08-05 | RICHTIG | 588.77
2026-08-04 | Opus-5 | META | 1W | UP | 52 | 590.24 | UP | 2026-08-11 | RICHTIG | 599.12
2026-08-04 | Opus-5 | TTWO | 1T | DOWN | 55 | 247.62 | UP | 2026-08-05 | RICHTIG | 236.79
2026-08-04 | Opus-5 | TTWO | 1W | UP | 53 | 247.62 | UP | 2026-08-11 | RICHTIG | 250.50

<!-- KADENZ-WECHSEL 2026-08-04: Ab hier stellt die Studie von TÄGLICH auf WÖCHENTLICH um.
     Grund: Die tägliche Erzeugung vor/während Börsenhandel führte zu Timing- und
     Leakage-Problemen (siehe METHODIK-HINWEIS oben). Ab jetzt erzeugt ein separater
     Wochenend-Lauf (Samstag) nur noch 1W-Prognosen: Referenz = Freitagsschluss,
     Auflösung = nächster Freitagsschluss. Sauberes, konsistentes Timing ohne Intraday-Leck.
     Für die Auswertung: den täglichen Zeitraum (bis 04.08.) und den wöchentlichen Zeitraum
     (ab erstem Samstags-Lauf) getrennt behandeln. 1T-Horizont entfällt künftig. -->

<!-- METHODIK-HINWEIS 2026-08-05:
     (a) DATENKONFLIKT ADBE, offen und bewusst NICHT rueckwirkend korrigiert:
         Aus dem 04.08.-Schluss (257.49) und der Tagesveraenderung (+2.45 %) folgt ein
         03.08.-Schluss von 251.33. Geloggt ist 247.90 (Suchquelle vom 04.08.).
         Differenz 1.4 %. FOLGE: Die Zeile "2026-08-02 | ADBE | 1T" (Referenz 250.41,
         Prognose DOWN, geloggt RICHTIG) waere bei 251.33 FALSCH. Rueckwirkendes
         Editieren auf mehrdeutiger Beleglage unterbleibt bewusst - der Konflikt wird
         markiert, damit die Auswertung diese Beobachtung ggf. ausschliessen kann.
     (b) DATENKONFLIKT TTWO, dritte Schaetzung fuer den 03.08.-Schluss: aus 240.22 und
         -2.01 % folgt 245.15 (bisher: 247.62 geloggt, ~243 aus dem Depot). Alle drei
         liegen ueber dem Referenzkurs 242.92 -> Richtung UP und Ergebnis RICHTIG robust,
         Hoehe unsicher.
     (c) Die Zeilen mit Datum 2026-08-05 wurden um 09:32 MESZ erzeugt: nach vollstaendigem
         US-Schluss, vor US-Eroeffnung, kurz nach EU-Eroeffnung. ERSTMALS METHODISCH
         SAUBER im Sinne des Learnings vom 04.08. - ohne Vorbehalt auswertbar.
     (d) MSCIWorld weiterhin nicht enthalten: kein verifizierter Indexstand ermittelbar.
     (e) ETF-Referenzkurse = europaeischer Schluss 04.08. in EUR, aus dem Depot-Tracker
         zurueckgerechnet (Kurs 05.08. 09:32 / (1 + Tagesveraenderung)).
-->
2026-08-05 | Opus-5 | SP500 | 1T | UP | 55 | 7737.00 | UP | 2026-08-06 | FALSCH | 7709.96
2026-08-05 | Opus-5 | SP500 | 1W | UP | 54 | 7737.00 | UP | 2026-08-12 | RICHTIG | 7748.50
2026-08-05 | Opus-5 | Vanguard FTSE All-World | 1T | UP | 56 | 168.06 | UP | 2026-08-06 | n/v | 
2026-08-05 | Opus-5 | Vanguard FTSE All-World | 1W | UP | 54 | 168.06 | UP | 2026-08-12 | RICHTIG | 168.80
2026-08-05 | Opus-5 | Amundi Nasdaq-100 | 1T | UP | 52 | 104.94 | UP | 2026-08-06 | n/v | 
2026-08-05 | Opus-5 | Amundi Nasdaq-100 | 1W | UP | 53 | 104.94 | UP | 2026-08-12 | FALSCH | 104.84
2026-08-05 | Opus-5 | HSBC MSCI EM | 1T | UP | 53 | 15.97 | UP | 2026-08-06 | n/v | 
2026-08-05 | Opus-5 | HSBC MSCI EM | 1W | UP | 52 | 15.97 | UP | 2026-08-12 | RICHTIG | 16.1245
2026-08-05 | Opus-5 | Amundi MSCI World | 1T | UP | 55 | 160.98 | UP | 2026-08-06 | n/v | 
2026-08-05 | Opus-5 | Amundi MSCI World | 1W | UP | 54 | 160.98 | UP | 2026-08-12 | RICHTIG | 161.65
2026-08-05 | Opus-5 | AAPL | 1T | UP | 53 | 309.38 | UP | 2026-08-06 | RICHTIG | 312.41
2026-08-05 | Opus-5 | AAPL | 1W | UP | 52 | 309.38 | UP | 2026-08-12 | FALSCH | 302.25
2026-08-05 | Opus-5 | UNH | 1T | UP | 55 | 407.55 | DOWN | 2026-08-06 | RICHTIG | 408.01
2026-08-05 | Opus-5 | UNH | 1W | DOWN | 52 | 407.55 | DOWN | 2026-08-12 | RICHTIG | 405.59
2026-08-05 | Opus-5 | ASML | 1T | DOWN | 57 | 1711.89 | UP | 2026-08-06 | RICHTIG | 1710.08
2026-08-05 | Opus-5 | ASML | 1W | UP | 53 | 1711.89 | UP | 2026-08-12 | RICHTIG | 1810.07
2026-08-05 | Opus-5 | PEP | 1T | UP | 53 | 139.10 | DOWN | 2026-08-06 | FALSCH | 138.44
2026-08-05 | Opus-5 | PEP | 1W | DOWN | 52 | 139.10 | DOWN | 2026-08-12 | RICHTIG | 138.70
2026-08-05 | Opus-5 | ADBE | 1T | DOWN | 55 | 257.49 | UP | 2026-08-06 | FALSCH | 257.61
2026-08-05 | Opus-5 | ADBE | 1W | DOWN | 54 | 257.49 | UP | 2026-08-12 | FALSCH | 258.75
2026-08-05 | Opus-5 | META | 1T | UP | 53 | 587.94 | DOWN | 2026-08-06 | RICHTIG | 589.90
2026-08-05 | Opus-5 | META | 1W | UP | 52 | 587.94 | DOWN | 2026-08-12 | FALSCH | 578.85
2026-08-05 | Opus-5 | TTWO | 1T | UP | 54 | 240.22 | DOWN | 2026-08-06 | FALSCH | 232.47
2026-08-05 | Opus-5 | TTWO | 1W | DOWN | 53 | 240.22 | DOWN | 2026-08-12 | FALSCH | 243.00

<!-- METHODIK-HINWEIS 2026-08-06:
     (a) LAUFZEITPUNKT 11:00 MESZ - NACH EU-Eroeffnung, VOR US-Eroeffnung. Damit gilt eine
         GETEILTE Bewertung (Praezisierung des Learnings vom 04.08.):
         * Die US-Einzelwerte (AAPL, UNH, ASML-ADR, PEP, ADBE, META, TTWO) und SP500 sind
           SAUBERE PROGNOSEN - der US-Handel hat heute noch nicht begonnen, es liegt keine
           Tagesinformation vor.
         * Die vier ETF-Zeilen sind NOWCAST-BELASTET - der europaeische Handel laeuft seit
           09:00 MESZ, die Intraday-Bewegung war beim Prognostizieren sichtbar. Diese vier
           Zeilen duerfen nicht ungeprueft in die Trefferquote einfliessen.
     (b) ETF-Referenzkurse = europaeischer Schluss 05.08. in EUR, aus dem Depot-Tracker
         zurueckgerechnet (Kurs 06.08. 11:00 / (1 + Tagesveraenderung)). Gleiche Methode wie
         am 05.08., gleiche Genauigkeitsgrenze (+-0,05 EUR).
     (c) MSCIWorld weiterhin nicht enthalten: kein verifizierter Indexstand ermittelbar.
     (d) ADBE-Referenz 259.32 = reguleaerer US-Schluss 05.08. Der nachboersliche Kurs lag bei
         249.40 (-3,83 %) und der europaeische Handel bestaetigt dieses Niveau heute frueh.
         Die DOWN-Prognose mit 65 % stuetzt sich auf diese zwei unabhaengigen Belege, NICHT
         auf eine benannte Ursache - eine Ursache war bis 11:00 MESZ nicht auffindbar.
     (e) OFFENER DEFEKT, bewusst NICHT rueckwirkend korrigiert: Die 1T-Zeilen mit Datum
         2026-08-05 tragen Auflösungsdatum 2026-08-06 statt 2026-08-05, obwohl ihre
         Referenzkurse die Schlusskurse vom 04.08. sind. Sie umfassen damit faktisch zwei
         Handelstage. Regelkonform wird nur Ergebnis/Ist-Kurs gesetzt - identifizierbar ueber
         die Kombination Datum 2026-08-05 + Referenz = Schluss 04.08.
-->
2026-08-06 | Opus-5 | SP500 | 1T | UP | 53 | 7723.52 | DOWN | 2026-08-06 | FALSCH | 7709.96
2026-08-06 | Opus-5 | Vanguard FTSE All-World | 1T | DOWN | 55 | 167.87 | UP | 2026-08-06 | n/v | 
2026-08-06 | Opus-5 | Amundi Nasdaq-100 | 1T | DOWN | 58 | 104.18 | UP | 2026-08-06 | n/v | 
2026-08-06 | Opus-5 | HSBC MSCI EM | 1T | DOWN | 60 | 15.93 | UP | 2026-08-06 | n/v | 
2026-08-06 | Opus-5 | Amundi MSCI World | 1T | DOWN | 55 | 161.47 | UP | 2026-08-06 | n/v | 
2026-08-06 | Opus-5 | AAPL | 1T | UP | 53 | 311.00 | UP | 2026-08-06 | RICHTIG | 312.41
2026-08-06 | Opus-5 | UNH | 1T | UP | 53 | 412.75 | UP | 2026-08-06 | FALSCH | 408.01
2026-08-06 | Opus-5 | ASML | 1T | UP | 54 | 1678.22 | DOWN | 2026-08-06 | RICHTIG | 1710.08
2026-08-06 | Opus-5 | PEP | 1T | DOWN | 52 | 139.68 | UP | 2026-08-06 | RICHTIG | 138.44
2026-08-06 | Opus-5 | ADBE | 1T | DOWN | 65 | 259.32 | UP | 2026-08-06 | RICHTIG | 257.61
2026-08-06 | Opus-5 | META | 1T | UP | 53 | 588.77 | UP | 2026-08-06 | RICHTIG | 589.90
2026-08-06 | Opus-5 | TTWO | 1T | DOWN | 55 | 236.79 | DOWN | 2026-08-06 | RICHTIG | 232.47

<!-- METHODIK-HINWEIS 2026-08-07:
     (a) DATENQUELLEN-AUSFALL: Der Portfolio-Scraper (Finanzfluss) ist ausgefallen — der
         Zugang wurde anbieterseitig gesperrt ("account has been banned"). Damit fehlt die
         bisher einzige Quelle fuer die EUR-Schlusskurse der vier ETFs. Folgen:
         * Die vier ETF-1T-Zeilen vom 05.08. und 06.08. sind auf "n/v" gesetzt (Regel:
           Kurs nicht mehr ermittelbar). Sie fliessen NICHT in die Trefferquote ein.
         * Fuer den 07.08. werden KEINE ETF-Zeilen erzeugt, weil kein verifizierbarer
           Referenzkurs vorliegt. Eine Prognose ohne aufloesbaren Referenzkurs waere eine
           Zeile ohne Informationswert.
         OFFENE AUFGABE: alternative Primaerquelle fuer die vier ETF-Schlusskurse in EUR
         festlegen (z. B. eine feste Boerse mit dokumentiertem Handelsplatz), bevor die
         ETF-Reihe fortgesetzt wird. Bis dahin laeuft die Studie auf SP500 + Aktienkorb.
     (b) DATENFEHLER IN EINER FRUEHEREN REFERENZ, offen benannt, NICHT rueckwirkend
         korrigiert: Die Zeile 2026-08-06 | TTWO traegt Referenzkurs 236.79. Der tatsaechliche
         US-Schluss vom 05.08. war 234.91 (S&P Global via stockanalysis.com). Die
         Prognoserichtung (DOWN) ist gegen beide Werte identisch, das Ergebnis aendert sich
         also nicht. Regelkonform wurde nur Ergebnis + Ist-Kurs gesetzt.
     (c) LAUFZEITPUNKT: vor US-Eroeffnung. Die acht heutigen Zeilen sind damit SAUBERE
         Prognosen im Sinne des Learnings vom 06.08. (US-Handel geschlossen).
     (d) EREIGNISRISIKO HEUTE, vorab protokolliert: US-Arbeitsmarktbericht 14:30 MESZ und
         Take-Two-Quartalszahlen 14:00 MESZ (erstmals vorboerslich). Beide Ereignisse liegen
         NACH dem Prognosezeitpunkt. Die TTWO-Zeile ist damit eine Ereignis-Wette und
         KORRELIERT mit der qualitativen Prognose P4 (GTA-VI-Termin haelt).
-->
2026-08-07 | Opus-5 | SP500 | 1T | UP | 52 | 7709.96 | DOWN | 2026-08-07 | RICHTIG | 7757.64
2026-08-07 | Opus-5 | AAPL | 1T | UP | 54 | 312.41 | UP | 2026-08-07 | RICHTIG | 313.33
2026-08-07 | Opus-5 | UNH | 1T | UP | 52 | 408.01 | DOWN | 2026-08-07 | RICHTIG | 409.40
2026-08-07 | Opus-5 | ASML | 1T | UP | 53 | 1710.08 | UP | 2026-08-07 | RICHTIG | 1740.99
2026-08-07 | Opus-5 | PEP | 1T | DOWN | 53 | 138.44 | DOWN | 2026-08-07 | FALSCH | 138.82
2026-08-07 | Opus-5 | ADBE | 1T | UP | 55 | 257.61 | DOWN | 2026-08-07 | RICHTIG | 264.91
2026-08-07 | Opus-5 | META | 1T | UP | 52 | 589.90 | UP | 2026-08-07 | RICHTIG | 592.10
2026-08-07 | Opus-5 | TTWO | 1T | UP | 56 | 232.47 | DOWN | 2026-08-07 | RICHTIG | 242.47

<!-- METHODIK-HINWEIS 2026-08-08 (Samstag):
     (a) KEINE NEUE BATTERIE - kein Handelstag. Regelkonform.
     (b) Die acht 1T-Zeilen vom 07.08. wurden gegen die US-Schlusskurse vom Fr 07.08.
         aufgeloest (S&P Global via stockanalysis.com; SP500 aus dem Reuters/CNBC-
         Marktbericht). Rueckrechnungs-Checks bestanden.
     (c) DATENREVISION BEI ASML, offen benannt und NICHT rueckwirkend korrigiert:
         Die Kurshistorie weist den Schluss vom 06.08. inzwischen mit 1704.37 aus.
         Beim Lauf am 07.08. stand dort 1710.08; dieser Wert wurde als Ist-Kurs der
         06.08.-Zeilen und als Referenz der 07.08.-Zeile verwendet. Die Prognoserichtungen
         sind gegen BEIDE Werte identisch (06.08.: UP ggue. 1678.22 bzw. DOWN ggue. 1711.89;
         07.08.: UP ggue. 1740.99). Kein Ergebnis aendert sich. Regelkonform bleiben die
         geloggten Werte stehen - eine nachtraegliche Angleichung an spaeter revidierte
         Kurse wuerde die Reihe unpruefbar machen.
     (d) BEWERTUNGSHINWEIS ZUR TREFFERQUOTE VOM 07.08. (7 von 8): Der Tag endete mit
         Rekordschlusskursen im SP500 und Nasdaq nach einem Arbeitsmarktbericht, dessen
         Ausgang im Report des Vortages ausdruecklich als nicht prognostizierbar bezeichnet
         wurde. Sieben UP-Prognosen an einem marktweiten Aufwaertstag sind KEIN Koennens-
         nachweis, sondern eine Richtungswette, die zufaellig mit einem Ereignis
         zusammenfiel. Die Baseline lag am selben Tag bei 3 von 8 - das zeigt, wie stark
         der Tag gegen die Vortagesrichtung lief.
-->

<!-- METHODIK-HINWEIS 2026-08-09 (Sonntag):
     (a) KEINE NEUE BATTERIE - kein Handelstag. Regelkonform.
     (b) KEINE 1T-AUFLOESUNG NOETIG: Alle 1T-Zeilen mit Aufloesungsdatum <= 09.08. sind
         bereits erledigt; die letzten faelligen (07.08.) wurden im Samstagsreport
         aufgeloest. Der erzwungene Pruefschritt (Learning 08.08.) wurde trotzdem
         durchgefuehrt, statt ihn wegen "Wochenende" zu ueberspringen.
     (c) KEINE 1W-ZEILE ANGEFASST - dafuer ist ausschliesslich der Samstags-Task
         (portfolio-studien-prognose) zustaendig.
     (d) OFFENE LUECKE, unveraendert und heute NICHT bearbeitet (ehrlich benannt,
         Learning 06.08. - "nicht bearbeitet" ist nicht dasselbe wie "nichts gefunden"):
         Die Primaerquelle fuer die vier ETF-Schlusskurse in EUR (fester, dokumentierter
         Handelsplatz) ist weiterhin nicht festgelegt. Bis dahin laeuft die Studie bewusst
         schmaler (SP500 + Aktienkorb) statt mit Behelfswerten.
     (e) Naechste Batterie: Montag, 10.08.2026, fuer das feste Studien-Universum (13 Werte).
-->

<!-- METHODIK-HINWEIS 2026-08-10 (Montag, Handelstag):
     (a) ERZWUNGENER AUFLOESUNGS-SCHRITT ZUERST (Learning 08.08.): Alle 1T-Zeilen mit
         Aufloesungsdatum <= 10.08. geprueft. ERGEBNIS: KEINE offene 1T-Zeile faellig.
         Die letzten faelligen (07.08.) wurden im Samstagsreport aufgeloest; Sa/So waren
         keine Handelstage. Nichts angefasst, nichts nachgetragen.
     (b) KEINE 1W-ZEILE BERUEHRT - dafuer ist ausschliesslich der Samstags-Task zustaendig.
     (c) UNIVERSUM WEITERHIN SCHMAL: SP500 + Aktienkorb (8 Werte). MSCIWorld und die vier
         ETFs bleiben ausgesetzt, weil die EUR-Kursquelle nicht steht. FORTSCHRITT HEUTE
         an der offenen Zusage: Der HANDELSPLATZ ist jetzt festgelegt und dokumentiert -
         **XETRA in EUR** (justETF-Listing-Tabelle, Reuters RIC VWCE.DE fuer den All-World;
         analog XETRA-EUR-Notierung fuer die drei uebrigen ETFs). Offen bleibt der
         technische Abrufweg fuer den XETRA-Schlusskurs; die Reihe wird erst fortgesetzt,
         wenn dieser steht. "Handelsplatz definiert" ist NICHT dasselbe wie "Kurs
         verfuegbar" - der Unterschied wird hier bewusst benannt.
     (d) REFERENZKURSE = US-Schlusskurse Fr 07.08. (letzter abgeschlossener Handelstag).
         Rueckrechnungs-Check bestanden: SP500 7709.96 x 1.0062 = 7757.76 ~ 7757.64;
         AAPL 312.41 x 1.0029 = 313.32 ~ 313.33. ASML weiterhin als US-ADR in USD.
     (e) BASELINE = Richtung der letzten Tagesbewegung. Alle acht Werte stiegen am 07.08.,
         die Baseline lautet daher acht Mal UP. Meine Prognose weicht bei vier Werten
         bewusst davon ab (4x UP, 4x DOWN) - anders als am 07.08., wo sieben UP-Zeilen
         eine reine Richtungswette waren, die zufaellig mit einem Ereignis zusammenfiel.
     (f) LAUFZEITPUNKT: vor US-Eroeffnung, US-Handel geschlossen. Die acht Zeilen sind
         damit SAUBERE Prognosen im Sinne des Learnings vom 06.08.
     (g) EREIGNISRISIKO DIESE WOCHE, vorab protokolliert: US-CPI Mi 12.08., PPI Do 13.08.,
         Einzelhandelsumsaetze Fr 14.08. Alle liegen NACH dem heutigen Aufloesungsdatum.
     (h) KORRELATIONS-HINWEIS: Die DOWN-Zeilen fuer ASML und TTWO stuetzen sich auf
         dieselbe Ueberlegung (Rueckgabe nach ueberdurchschnittlichem Vorwochenmove) und
         sind daher NICHT als zwei unabhaengige Beobachtungen zu zaehlen (Learning 07.08.).
-->
2026-08-10 | Opus-5 | SP500 | 1T | UP | 54 | 7757.64 | UP | 2026-08-10 | FALSCH | 7753.11
2026-08-10 | Opus-5 | AAPL | 1T | UP | 51 | 313.33 | UP | 2026-08-10 | FALSCH | 308.26
2026-08-10 | Opus-5 | UNH | 1T | UP | 52 | 409.40 | UP | 2026-08-10 | FALSCH | 408.74
2026-08-10 | Opus-5 | ASML | 1T | DOWN | 52 | 1740.99 | UP | 2026-08-10 | RICHTIG | 1733.48
2026-08-10 | Opus-5 | PEP | 1T | UP | 52 | 138.82 | UP | 2026-08-10 | FALSCH | 137.73
2026-08-10 | Opus-5 | ADBE | 1T | DOWN | 53 | 264.91 | UP | 2026-08-10 | FALSCH | 272.96
2026-08-10 | Opus-5 | META | 1T | UP | 51 | 592.10 | UP | 2026-08-10 | RICHTIG | 594.92
2026-08-10 | Opus-5 | TTWO | 1T | DOWN | 52 | 242.47 | UP | 2026-08-10 | FALSCH | 253.57

<!-- METHODIK-HINWEIS 2026-08-11 (Dienstag, Handelstag) — ZWEI SCHWERWIEGENDE BEFUNDE:

     (A) ⚠️ ZEITSTEMPEL-KONFLIKT BEIM LAUF VOM "10.08." — offen benannt, NICHT bereinigt.
         Der Lauf, der die acht 10.08.-Zeilen erzeugt hat, fand nach Systemuhr in den
         fruehen Morgenstunden des 11.08. statt (bash: 2026-08-11). Der Report wurde
         jedoch auf den 10.08. datiert, weil der Anwendungskontext dieses Datum auswies.
         KONSEQUENZ FUER DIE STUDIE: Die acht Zeilen tragen Aufloesungsdatum 2026-08-10 —
         ein Handelstag, der zum Zeitpunkt des Schreibens BEREITS ABGESCHLOSSEN WAR.
         Formal sind sie damit potenziell look-ahead-kontaminiert und duerfen in der
         Auswertung NICHT wie saubere Prognosen behandelt werden.
         GEGENEVIDENZ, die fuer echte Unkenntnis spricht: Das Ergebnis lautet 2 von 8
         (25 %) und liegt DAMIT UNTER der Baseline (3 von 8). Wer den Ausgang kennt,
         erzielt nicht das schlechteste Tagesergebnis der ganzen Reihe. Zusaetzlich
         weisen die im Lauf verwendeten Quellen ausschliesslich Freitagsschluss und
         Montags-VORboersendaten aus. Der Befund bleibt trotzdem stehen: Nicht
         nachweisbare Unkenntnis ist keine belegte Unkenntnis.
         KONSEQUENZ AB HEUTE: Das Laufdatum wird zu Beginn jedes Laufs per Systemuhr
         verifiziert und im Report genannt, nicht aus dem Anwendungskontext uebernommen.

     (B) ⚠️ REFERENZKURS-FEHLER BEI UNH — ergebnisrelevant, offen benannt, NICHT
         rueckwirkend korrigiert.
         Geloggter Referenzkurs der UNH-Zeile vom 10.08.: 409.40.
         TATSAECHLICHER Schluss 07.08. laut Kurshistorie (S&P Global via
         stockanalysis.com): 407.08. Auch der am 07.08. geloggte Wert 408.01 fuer den
         Schluss vom 06.08. ist falsch; tatsaechlich 403.97.
         WIRKUNG: Regelkonform wurde gegen den GELOGGTEN Referenzkurs aufgeloest
         (408.74 < 409.40 -> DOWN -> Prognose UP -> FALSCH). Gegen den KORREKTEN
         Referenzkurs waere es UP und damit RICHTIG gewesen. Diese eine Zeile ist damit
         ergebnisverfaelschend und in der Auswertung zu KENNZEICHNEN.
         Die 07.08.-Zeile ist nicht ergebnisrelevant betroffen: 403.97 -> 407.08 = UP,
         die Prognose lautete UP, das Ergebnis RICHTIG bleibt gegen beide Wertepaare.
         WEITERE ABWEICHUNGEN im selben Abgleich (nicht ergebnisrelevant, aber
         protokolliert): geloggt vs. tatsaechlich fuer den Schluss 07.08. —
         PEP 138.82 vs. 139.02 · ADBE 264.91 vs. 265.21 · TTWO 242.47 vs. 246.49.
         KORREKT waren AAPL 313.33, ASML 1740.99, META 592.10, SP500 7757.64.
         Vier von acht Referenzwerten wichen ab. Das ist kein Einzelfehler, sondern ein
         Quellenproblem — siehe learnings.md 11.08.

     (C) AB HEUTE GEAENDERTES VERFAHREN: Referenzkurse werden nicht mehr aus dem
         Ist-Kurs der Vortageszeile uebernommen, sondern jeden Tag frisch gegen die
         KURSHISTORIE (stockanalysis.com /history/, Quelle S&P Global) geprueft. Die
         heutigen acht Referenzkurse sind auf diesem Weg ermittelt.

     (D) RUECKRECHNUNGS-CHECKS bestanden: SP500 7757.64 x (1-0.0006) = 7753.0 ~ 7753.11 ·
         ASML 1740.99 x (1-0.0043) = 1733.50 ~ 1733.48 · META 592.10 x 1.0048 = 594.94 ~
         594.92 · ADBE 265.21 x 1.0292 = 272.96 ✓ · UNH 407.08 x 1.0041 = 408.75 ~ 408.74.
         AAPL SONDERFALL, sauber aufgeloest: 308.26 gegen 313.33 sind -1.62 %, die Quelle
         weist -1.53 % aus. Differenz = 0.086 % = exakt die Dividende 0.27 $ / 313.33 $.
         Die Quelle rechnet gegen den dividendenbereinigten Vortagesschluss 313.06.
         Der Ex-Dividenden-Tag ist damit in den Daten sichtbar — siehe Lernbox 11.08.

     (E) BASELINE HEUTE = tatsaechliche Richtung der letzten Tagesbewegung, ermittelt
         gegen die KORRIGIERTEN Freitagsschluesse: UNH 407.08 -> 408.74 = UP;
         PEP 139.02 -> 137.73 = DOWN; ADBE 265.21 -> 272.96 = UP; TTWO 246.49 -> 253.57
         = UP. Baseline damit 4x UP / 4x DOWN, nicht mehr einheitlich.

     (F) LAUFZEITPUNKT: 06:52 MESZ, per Systemuhr verifiziert. Damit erstmals im
         sauberen Fenster 06:00-09:00 MESZ (Learning 04.08.): US-Handel geschlossen,
         EU-Handel noch nicht eroeffnet. Alle acht Zeilen sind saubere Prognosen.

     (G) EREIGNISRISIKO HEUTE: keines von Rang. US-CPI erst Mi 12.08., PPI Do 13.08.
         Die Zeilen sind damit weniger ereignis- und mehr richtungsgetrieben.

     (H) KORRELATION: SP500, AAPL, META und UNH beruhen auf derselben Annahme
         (leicht positive Futures, kein Ereignis vor dem CPI) und sind NICHT als
         unabhaengige Beobachtungen zu zaehlen. ADBE (DOWN) ist die einzige Zeile mit
         einer eigenstaendigen, wertspezifischen Begruendung.
-->
2026-08-11 | Opus-5 | SP500 | 1T | UP | 53 | 7753.11 | DOWN | 2026-08-11 | FALSCH | 7728.20
2026-08-11 | Opus-5 | AAPL | 1T | UP | 51 | 308.26 | DOWN | 2026-08-11 | FALSCH | 304.91
2026-08-11 | Opus-5 | UNH | 1T | UP | 52 | 408.74 | UP | 2026-08-11 | FALSCH | 402.19
2026-08-11 | Opus-5 | ASML | 1T | DOWN | 52 | 1733.48 | DOWN | 2026-08-11 | FALSCH | 1799.38
2026-08-11 | Opus-5 | PEP | 1T | UP | 53 | 137.73 | DOWN | 2026-08-11 | RICHTIG | 138.41
2026-08-11 | Opus-5 | ADBE | 1T | DOWN | 54 | 272.96 | UP | 2026-08-11 | RICHTIG | 263.71
2026-08-11 | Opus-5 | META | 1T | UP | 51 | 594.92 | UP | 2026-08-11 | RICHTIG | 599.12
2026-08-11 | Opus-5 | TTWO | 1T | UP | 52 | 253.57 | UP | 2026-08-11 | FALSCH | 250.50

<!-- METHODIK-HINWEIS 2026-08-12 (Mittwoch, Handelstag):

     (A) LAUFZEITPUNKT: 15:20 MESZ, per Systemuhr verifiziert (neue Regel seit 11.08.).
         AUSSERHALB des sauberen Fensters. Zwei getrennte Belastungen, zeilenweise
         gekennzeichnet statt pauschal (Learning 06.08.):
         - US-Handel noch GESCHLOSSEN (Eroeffnung 15:30 MESZ). Kein US-Kurs hat sich
           heute gebildet. Insofern sind alle acht Zeilen formal Prognosen.
         - ABER: (1) Der US-CPI wurde um 14:30 MESZ veroeffentlicht, also 50 Minuten VOR
           dem Lauf. Die Zeilen enthalten damit eine grosse, frische Makroinformation,
           die an einem normalen Morgenlauf nicht vorgelegen haette. Das ist kein
           Look-ahead (der Kurs steht noch aus), aber der Informationsstand ist REICHER
           als an anderen Tagen und deshalb nicht ohne Weiteres vergleichbar.
           (2) Der EUROPAEISCHE Handel laeuft seit 09:00. Fuer ASML und ADBE lagen mir
           beim Prognostizieren HEUTIGE europaeische Kurse vor (ASML 1.590,00 EUR
           +2,07 %; ADBE 223,65 EUR -1,93 %, beide aus dem Depot-Tracker).
           >>> DIE ZEILEN ASML UND ADBE SIND NOWCAST-BELASTET UND IN EINER SAUBEREN
           >>> AUSWERTUNG AUSZUSCHLIESSEN. Die uebrigen sechs sind davon nicht betroffen.
         Die Konfidenzen 60 bei ASML und ADBE spiegeln genau diesen Vorteil - sie sind
         deshalb KEIN Ausweis von Prognosefaehigkeit.

     (B) REFERENZKURSE frisch aus der Kurshistorie ermittelt (Verfahren seit 11.08.),
         nicht aus den Ist-Kursen der Vortageszeilen fortgeschrieben. Rueckrechnungs-
         Checks gegen die Montagsschluesse alle bestanden:
         AAPL 308.26 x (1-0.0109) = 304.90 ~ 304.91 · UNH 408.74 x (1-0.0160) = 402.20 ~
         402.19 · PEP 137.73 x 1.0049 = 138.40 ~ 138.41 · META 594.92 x 1.0071 = 599.14 ~
         599.12 · TTWO 253.57 x (1-0.0121) = 250.50 ✓ · ADBE 272.96 x (1-0.0339) = 263.71 ✓
         · ASML 1733.48 x 1.0380 = 1799.35 ~ 1799.38 · SP500 7753.11 x (1-0.0032) =
         7728.30 ~ 7728.20.
         KEINE Abweichung zwischen geloggtem Ist-Kurs und Kurshistorie - das am 11.08.
         geaenderte Verfahren hat heute erstmals eine saubere Runde geliefert.

     (C) AUFLOESUNG 11.08.: 3 von 8 richtig, Baseline ebenfalls 3 von 8. Zweiter
         schwacher Tag in Folge. Groesster Einzelfehler: ASML DOWN prognostiziert,
         tatsaechlich +3,80 % - Ursache war TSMCs Juli-Umsatz (+44,7 % y/y), also eine
         Kundenzahl, die zum Prognosezeitpunkt noch nicht veroeffentlicht war.

     (D) BASELINE heute erneut gemischt (4x UP / 4x DOWN), ermittelt aus den
         tatsaechlichen Bewegungen Mo -> Di.

     (E) KORRELATION: Sechs der acht Zeilen (SP500, AAPL, UNH, PEP, META, TTWO) stuetzen
         sich auf DIESELBE Annahme - der milde CPI traegt den Gesamtmarkt bis zum
         Schluss. Das ist EINE Wette mit sechs Zeilen und darf nicht als sechs
         unabhaengige Beobachtungen gezaehlt werden (Learning 10.08. zur effektiven
         Stichprobe, Learning 07.08. zur Unabhaengigkeit von Belegen).
-->
2026-08-12 | Opus-5 | SP500 | 1T | UP | 60 | 7728.20 | DOWN | 2026-08-12 | RICHTIG | 7748.50
2026-08-12 | Opus-5 | AAPL | 1T | UP | 55 | 304.91 | DOWN | 2026-08-12 | FALSCH | 302.25
2026-08-12 | Opus-5 | UNH | 1T | UP | 53 | 402.19 | DOWN | 2026-08-12 | RICHTIG | 405.59
2026-08-12 | Opus-5 | ASML | 1T | UP | 60 | 1799.38 | UP | 2026-08-12 | RICHTIG | 1810.07
2026-08-12 | Opus-5 | PEP | 1T | UP | 52 | 138.41 | UP | 2026-08-12 | RICHTIG | 138.70
2026-08-12 | Opus-5 | ADBE | 1T | DOWN | 60 | 263.71 | DOWN | 2026-08-12 | RICHTIG | 258.75
2026-08-12 | Opus-5 | META | 1T | UP | 54 | 599.12 | UP | 2026-08-12 | FALSCH | 578.85
2026-08-12 | Opus-5 | TTWO | 1T | UP | 52 | 250.50 | DOWN | 2026-08-12 | FALSCH | 243.00

<!-- METHODIK-HINWEIS 2026-08-13 (Donnerstag, Handelstag):

     (A) LAUFZEITPUNKT 10:15 MESZ, Systemuhr verifiziert. US-Handel geschlossen (sauber),
         EU-Handel seit 09:00 offen (75 Minuten).
         >>> NOWCAST-BELASTUNG, zeilenweise: Aus dem Depot-Tracker lagen mir HEUTIGE
         >>> europaeische Bewegungen fuer AAPL (+0,54 %), UNH (-0,45 %) und TTWO (-0,38 %)
         >>> vor. Diese drei Zeilen sind SCHWACH belastet und entsprechend zu kennzeichnen.
         Einschraenkung der Einschraenkung, ehrlich: Es handelt sich um EUR-Kurse aus
         duennem europaeischem Handel, die zusaetzlich Wechselkurseffekte enthalten - der
         Informationsvorteil ist real, aber klein. Die Prognosen wurden deshalb NICHT
         nachtraeglich angepasst; nur AAPL wurde von 52 auf 56 Konfidenz gehoben.
         SP500, ASML, PEP, ADBE, META: keine heutige Information vorhanden, sauber.

     (B) DATENQUELLEN-BEFUND, neu und wichtig fuer die Reihe:
         Die Vergleichsseite stockanalysis.com/stocks/compare/ lieferte heute einen
         ZWISCHENGESPEICHERTEN Stand vom Vortag (Dienstagsschluesse, identisch mit dem
         gestrigen Abruf). Waeren diese Werte ungeprueft als Mittwochsschluesse geloggt
         worden, waere das exakt der Fehlertyp TAG vom 22.07. gewesen. Erkannt wurde es
         durch den Rueckrechnungs-Check. KONSEQUENZ: Kurse werden ab sofort primaer ueber
         die /history/-Seiten bezogen (dort steht ein Datum an jeder Zeile); die
         Vergleichsseite nur noch als Zweitquelle und nur mit bestandener Rueckrechnung.

     (C) RUECKRECHNUNGS-CHECKS gegen die Dienstagsschluesse, alle bestanden:
         SP500 7728.20 + 20.30 = 7748.50 ✓ · AAPL 304.91 x (1-0.0087) = 302.26 ~ 302.25 ·
         UNH 402.19 x 1.0085 = 405.61 ~ 405.59 · ASML 1799.38 x 1.0059 = 1809.99 ~ 1810.07 ·
         PEP 138.41 x 1.0021 = 138.70 ✓ · ADBE 263.71 x (1-0.0188) = 258.75 ✓ ·
         META 599.12 x (1-0.0338) = 578.87 ~ 578.85 · TTWO 250.50 x (1-0.0299) = 243.01 ~ 243.00

     (D) QUELLENKONFLIKT, offen benannt: Eine Quelle nennt fuer den 12.08. einen
         Nasdaq-Composite-Schluss von 26.445,45 bei -0,6 % - das ist der DIENSTAGSwert.
         Andere Quellen weisen fuer Mittwoch +0,59 % aus (rechnerisch ~26.601). Der
         Nasdaq ist nicht Teil des Studien-Universums, das Ergebnis der Batterie ist davon
         nicht betroffen. Der SP500-Wert 7748.50 ist ueber die Punktdifferenz (+20.30)
         doppelt bestaetigt und wird verwendet.

     (E) AUFLOESUNG 12.08.: 5 von 8 richtig, Baseline ebenfalls 5 von 8. Dritter Tag in
         Folge ohne Vorsprung gegenueber dem Zufallspfad. Die beiden nowcast-belasteten
         Zeilen (ASML, ADBE) waren BEIDE richtig - rechnet man sie heraus, bleiben
         3 von 6 gegen eine Baseline von 3 von 6.

     (F) BASELINE heute 4x UP / 4x DOWN.
         SELBSTBEFUND, der in die Auswertung gehoert: Meine heutigen Prognosen stimmen bei
         SECHS von acht Werten mit der Baseline ueberein. Ein Tag, an dem das Modell
         weitgehend den Zufallspfad nachzeichnet, traegt wenig Information - unabhaengig
         davon, wie er ausgeht. Das wird hier VORHER protokolliert, nicht nachher.

     (G) EREIGNISRISIKO HEUTE, vorab protokolliert und NACH dem Prognosezeitpunkt:
         US-PPI Juli 14:30 MESZ · Erstantraege 14:30 · Applied Materials Q3 nach
         US-Schluss (trifft ASML-Zeile erst morgen).
-->
2026-08-13 | Opus-5 | SP500 | 1T | UP | 53 | 7748.50 | UP | 2026-08-13 | RICHTIG | 7798.99
2026-08-13 | Opus-5 | AAPL | 1T | UP | 56 | 302.25 | DOWN | 2026-08-13 | RICHTIG | 305.26
2026-08-13 | Opus-5 | UNH | 1T | UP | 52 | 405.59 | UP | 2026-08-13 | FALSCH | 399.06
2026-08-13 | Opus-5 | ASML | 1T | UP | 53 | 1810.07 | UP | 2026-08-13 | RICHTIG | 1847.90
2026-08-13 | Opus-5 | PEP | 1T | UP | 52 | 138.70 | UP | 2026-08-13 | RICHTIG | 140.62
2026-08-13 | Opus-5 | ADBE | 1T | DOWN | 52 | 258.75 | DOWN | 2026-08-13 | FALSCH | 270.49
2026-08-13 | Opus-5 | META | 1T | DOWN | 52 | 578.85 | DOWN | 2026-08-13 | FALSCH | 594.97
2026-08-13 | Opus-5 | TTWO | 1T | UP | 51 | 243.00 | DOWN | 2026-08-13 | FALSCH | 241.91

<!-- METHODIK-HINWEIS 2026-08-14 (Freitag, Handelstag):

     (A) LAUFZEITPUNKT 09:00 MESZ, Systemuhr verifiziert (Fri Aug 14 09:00:52 CEST 2026).
         US-Handel geschlossen (sauber), EU-Handel seit 09:00 offen — also rund zwei Minuten.
         >>> NOWCAST-BELASTUNG, zeilenweise und ehrlich: Aus dem Depot-Tracker lagen mir
         >>> zwei heutige europaeische Anfangskurse vor: TTWO 210,00 EUR (-0,47 %) und
         >>> META 514,50 EUR (-0,25 %). Diese zwei Zeilen sind SCHWACH belastet.
         >>> Einschraenkung der Einschraenkung: zwei Minuten Handel in EUR sind praktisch
         >>> Eroeffnungsrauschen plus Wechselkurs; der Informationsgehalt ist nahe null,
         >>> aber er ist nicht exakt null und wird deshalb protokolliert.
         SP500, AAPL, UNH, ASML, PEP, ADBE: keine heutige Information vorhanden, sauber.

     (B) QUELLENKONFLIKT SP500, aufgeloest durch Rueckrechnung: Eine Quelle nennt fuer den
         13.08. einen Schluss von 7.781,59 (+0,43 %), eine andere 7.798,99 (+0,65 %,
         +50,49 Pkt.). Rueckrechnung gegen den Mittwochsschluss 7.748,50:
         7.748,50 + 50,49 = 7.798,99 ✓ exakt. Der Wert 7.781,59 besteht den Check NICHT
         (er entspraeche +33,09 Pkt. bei ausgewiesenen +0,43 %; 7748.50 x 1.0043 = 7781.82,
         also auch in sich nur naeherungsweise stimmig). GEFUEHRT WIRD 7.798,99.
         Das ist der dritte Datenfehler in vier Tagen, den dieser Check gefangen hat.

     (C) RUECKRECHNUNGS-CHECKS gegen die Mittwochsschluesse, alle bestanden:
         AAPL 302.25 + 3.01 = 305.26 ✓ · UNH 405.59 x (1-0.0161) = 399.06 ✓ ·
         ASML 1810.07 x 1.0209 = 1847.99 ~ 1847.90 · PEP 138.70 x 1.0138 = 140.61 ~ 140.62 ·
         ADBE 258.75 x 1.0454 = 270.50 ~ 270.49 · META 578.85 + 16.12 = 594.97 ✓ ·
         TTWO 243.00 x (1-0.0045) = 241.91 ✓
         QUELLEN: AAPL und META aus der Kursleiste eines Marktberichts (beide exakt gegen
         den Referenzkurs rueckgerechnet), alle uebrigen aus den /history/-Seiten mit
         Datumsspalte (Konsequenz aus dem Cache-Learning vom 13.08.).

     (D) AUFLOESUNG 13.08.: 4 von 8 richtig, Baseline ebenfalls 4 von 8.
         VIERTER Tag in Folge ohne Vorsprung gegenueber dem Zufallspfad.
         Die am 13.08. VORAB protokollierte Erwartung ("sechs von acht Prognosen decken
         sich mit der Baseline, der Tag traegt wenig Information") hat sich bestaetigt:
         beide Verfahren landen exakt gleich. Das ist die sauberste moegliche Bestaetigung
         dieser Vorab-Feststellung — und ein Beleg dafuer, dass die Kennzeichnung des
         Informationsgehalts VOR dem Ergebnis funktioniert.

     (E) BASELINE heute 6x UP / 2x DOWN.
         SELBSTBEFUND, vorab protokolliert: Meine heutigen Prognosen decken sich bei
         VIER von acht Werten mit der Baseline (AAPL, UNH, PEP, TTWO) und weichen bei
         vier ab (SP500, ASML, ADBE, META). Das ist deutlich informativer als der
         13.08. (6 von 8 Deckung) — der Tag kann daher zwischen Modell und Zufallspfad
         unterscheiden, egal wie er ausgeht.

     (F) EREIGNISRISIKO HEUTE, vorab protokolliert und NACH dem Prognosezeitpunkt:
         Applied Materials Q3 kam gestern NACH US-Schluss: Umsatz 9,12 Mrd. $ (+25 % y/y,
         Konsens 8,99), adj. EPS 3,50 $ (Konsens 3,40), Q4-Guidance 10,25 Mrd. $ gegen
         Konsens ~9,54 Mrd. $, WFE-Wachstumsausblick 2026 von ~20 % auf ueber 30 %
         angehoben — und die Aktie faellt nachboerslich auf 506,51 $ (-5,24 %), weil der
         Markt auf den Margenausblick schaut. GENAU DIESER WIDERSPRUCH begruendet die
         ASML-Zeile DOWN: die Nachfragezahl ist stark, die Kursreaktion des naechsten
         Gliedes derselben Kette ist negativ, und an einem einzelnen Tag schlaegt
         erfahrungsgemaess die Reaktion die Zahl (Learning 22.07., "Sell the News").
         Das ist eine bewusste Wette GEGEN die Fundamentaldaten und fuer die Positionierung
         — sie soll pruefbar sein, deshalb steht sie hier ausformuliert.
         Weiter heute: Uni-Michigan-Verbrauchervertrauen 16:00 MESZ, Einzelhandelsumsaetze.
-->
2026-08-14 | Opus-5 | SP500 | 1T | DOWN | 52 | 7798.99 | UP | 2026-08-14 | RICHTIG | 7785.76
2026-08-14 | Opus-5 | AAPL | 1T | UP | 51 | 305.26 | UP | 2026-08-14 | RICHTIG | 305.93
2026-08-14 | Opus-5 | UNH | 1T | DOWN | 53 | 399.06 | DOWN | 2026-08-14 | FALSCH | 401.73
2026-08-14 | Opus-5 | ASML | 1T | DOWN | 55 | 1847.90 | UP | 2026-08-14 | RICHTIG | 1844.45
2026-08-14 | Opus-5 | PEP | 1T | UP | 52 | 140.62 | UP | 2026-08-14 | RICHTIG | 140.79
2026-08-14 | Opus-5 | ADBE | 1T | DOWN | 53 | 270.49 | UP | 2026-08-14 | RICHTIG | 264.02
2026-08-14 | Opus-5 | META | 1T | DOWN | 52 | 594.97 | UP | 2026-08-14 | RICHTIG | 589.85
2026-08-14 | Opus-5 | TTWO | 1T | DOWN | 51 | 241.91 | DOWN | 2026-08-14 | FALSCH | 246.95

<!-- METHODIK-HINWEIS 2026-08-15 (Samstag, KEIN Handelstag):

     (A) LAUFZEITPUNKT 11:09 MESZ, Systemuhr verifiziert (Sat Aug 15 11:09:04 CEST 2026).
         KEINE neue 1T-Batterie erzeugt — regelkonform, Samstag ist kein Handelstag.
         Es wurden AUSSCHLIESSLICH die acht faelligen 1T-Zeilen vom 14.08. aufgeloest
         (nur Spalten Ergebnis und Ist-Kurs). 1W-Zeilen NICHT angefasst (Zustaendigkeit
         des separaten Samstags-Tasks portfolio-studien-prognose).

     (B) QUELLENWECHSEL, methodisch relevant: Kurse heute ueber die
         /stocks/<ticker>/ UEBERSICHTSSEITEN bezogen statt ueber /history/.
         Grund: Die Uebersichtsseite fuehrt das Feld "Previous Close" MIT, sodass der
         Rueckrechnungs-Check auf derselben Seite abgeschlossen werden kann, ohne eine
         zweite Quelle. Zusaetzlich steht dort explizit "At close: Aug 14, 2026, 4:00 PM
         EDT" — Datum UND Uhrzeit als Selbstauskunft der Daten. Das ist die konsequente
         Fortsetzung des Cache-Learnings vom 13.08.

     (C) RUECKRECHNUNGS-CHECKS, alle bestanden:
         SP500 7798.99 - 13.23 = 7785.76 ✓ · AAPL 305.26 + 0.67 = 305.93 ✓ ·
         UNH 399.06 + 2.67 = 401.73 ✓ (Previous Close auf der Seite: 399.06 ✓) ·
         PEP 140.62 + 0.17 = 140.79 ✓ (Previous Close: 140.62 ✓) ·
         ADBE 270.49 x (1-0.0239) = 264.03 ~ 264.02 ✓ ·
         META 594.97 - 5.12 = 589.85 ✓ · TTWO 241.91 + 5.04 = 246.95 ✓ (Previous Close ✓)

     (D) QUELLENKONFLIKT ASML, offen benannt und aufgeloest: Die Kopfzeile der
         stockanalysis-Seite nennt 1.844,08 (-3,82 / -0,21 %), die datierte Tabellenzeile
         nennt Close 1.844,45 (-0,19 %). Differenz 0,37 $ = 0,02 %. GEFUEHRT WIRD DER
         TABELLENWERT 1.844,45, weil an ihm ein Datum steht (Regel vom 13.08.).
         Fuer das Ergebnis ist der Konflikt folgenlos: beide Werte liegen unter dem
         Referenzkurs 1.847,90, die Richtung DOWN ist eindeutig.

     (E) AUFLOESUNG 14.08.: 6 von 8 richtig, Baseline 2 von 8. Vorsprung +50 Prozentpunkte —
         DER BESTE TAG DER GESAMTEN REIHE.
         >>> UND DAS IST DER EIGENTLICHE BEFUND: Am 14.08. wurde VORHER protokolliert,
         >>> dass sich die Prognosen nur bei VIER von acht Werten mit der Baseline decken
         >>> und der Tag deshalb "zwischen Modell und Zufallspfad unterscheiden kann,
         >>> egal wie er ausgeht". Genau das ist eingetreten. Zusammen mit dem 13.08.
         >>> (6 von 8 Deckung angekuendigt -> beide Verfahren exakt gleich, 4:4) liegen
         >>> jetzt ZWEI aufeinanderfolgende Tage vor, an denen die VORAB gemessene
         >>> Abweichung von der Baseline den Informationsgehalt des Tages korrekt
         >>> vorhergesagt hat. Zwei Faelle sind kein Beweis, aber sie sind ein Muster,
         >>> das sich weiter pruefen laesst — und die Kennzahl ist vor der Aufloesung
         >>> berechenbar. Fuer die Bachelorarbeit ist das ein eigenstaendiges Ergebnis.

     (F) ATTRIBUTION, ehrlich: Vier der sechs Treffer (SP500, ASML, ADBE, META) standen
         auf DOWN an einem Tag, an dem der Gesamtmarkt nach Konsumdaten drehte
         (Uni-Michigan-Vertrauen 51 gegen erwartete 55; Einzelhandel Juli -0,6 % m/m,
         erster Rueckgang seit neun Monaten). Ein Teil des Vorsprungs ist also eine
         einzige richtige Marktrichtung, nicht sechs unabhaengige Einzelurteile.
         Das mindert den Wert des Tages und wird deshalb hier notiert, nicht spaeter.
         Die beiden Fehlschlaege hatten beide eine benannte firmenspezifische Ursache
         (UNH: Schuldbekenntnis Mangione · TTWO: GTA-VI-Trailer-Termin 27.08. bestaetigt).

     KEINE NEUEN ZEILEN AN DIESEM TAG.
-->

2026-08-16 | Opus-5 | SP500 | 1W | UP | 56 | 7785.76 | UP | 2026-08-21 | FALSCH | 7674.37
2026-08-16 | Opus-5 | Vanguard FTSE All-World | 1W | UP | 54 | 168.88 | UP | 2026-08-21 | FALSCH | 166.30
2026-08-16 | Opus-5 | Amundi Nasdaq-100 | 1W | UP | 54 | 105.24 | UP | 2026-08-21 | FALSCH | 102.24
2026-08-16 | Opus-5 | HSBC MSCI EM | 1W | UP | 52 | 16.091 | UP | 2026-08-21 | n/v | 
2026-08-16 | Opus-5 | Amundi MSCI World | 1W | UP | 54 | 161.76 | UP | 2026-08-21 | FALSCH | 158.615
2026-08-16 | Opus-5 | AAPL | 1W | DOWN | 52 | 305.93 | DOWN | 2026-08-21 | FALSCH | 309.35
2026-08-16 | Opus-5 | UNH | 1W | DOWN | 53 | 401.73 | DOWN | 2026-08-21 | RICHTIG | 390.11
2026-08-16 | Opus-5 | ASML | 1W | UP | 54 | 1844.45 | UP | 2026-08-21 | FALSCH | 1763.76
2026-08-16 | Opus-5 | PEP | 1W | UP | 54 | 140.79 | UP | 2026-08-21 | RICHTIG | 143.48
2026-08-16 | Opus-5 | ADBE | 1W | UP | 53 | 264.02 | DOWN | 2026-08-21 | RICHTIG | 275.30
2026-08-16 | Opus-5 | META | 1W | UP | 51 | 589.85 | DOWN | 2026-08-21 | FALSCH | 549.90
2026-08-16 | Opus-5 | TTWO | 1W | UP | 55 | 246.95 | UP | 2026-08-21 | FALSCH | 239.62

<!-- METHODIK-HINWEIS 2026-08-16 (Sonntag) — WOCHEN-TASK portfolio-studien-prognose, Horizont 1W:

     (A) LAUF AM SONNTAG STATT SAMSTAG. Der Task ist als Samstags-Lauf gedacht; dieser Lauf
         erfolgte am Sonntag, 16.08.2026. Fuer die Daten ist das folgenlos: Referenz bleibt der
         Freitagsschluss 14.08., Aufloesungsdatum bleibt der kommende Freitag 21.08.
         Es wurden AUSSCHLIESSLICH 1W-Zeilen angefasst. Keine 1T-Zeile veraendert (per diff geprueft).

     (B) ERSTE AUFLOESUNG DER 1W-BATTERIE UEBERHAUPT. Bis heute war JEDE der 40 vorhandenen
         1W-Zeilen "offen" — die 1W-Reihe war seit dem 02.08. nie ausgewertet worden.
         Alle 40 wurden jetzt aufgeloest (Faelligkeiten 07.08., 10.08., 11.08., 12.08.).
         Ergebnis: Berater 32/40 = 80,0 % · Baseline 27/40 = 67,5 % · Vorsprung +12,5 Pp.
         Nach Faelligkeitstag: 07.08. 7/8 vs 5/8 · 10.08. 7/8 vs 6/8 · 11.08. 11/12 vs 7/12 ·
         12.08. 7/12 vs 9/12 (einziger Tag, an dem die Baseline besser war).

     (C) DER ENTSCHEIDENDE VORBEHALT ZU (B): Die 40 Beobachtungen sind NICHT unabhaengig.
         Sie stammen aus nur VIER Faelligkeitsterminen und decken zum Teil dieselbe Kurswoche ab
         (z.B. nutzen die Bloecke 02.08. und 03.08. identische Referenzkurse vom 31.07.).
         In diesem Zeitraum stieg der Gesamtmarkt kraeftig (S&P 7489 -> 7785). Wer pauschal UP
         sagt, ist in einer solchen Phase fast automatisch gut. Die 80 % messen daher zu einem
         grossen Teil EINE richtige Marktrichtung, nicht 40 unabhaengige Einzelurteile.
         Effektive Stichprobe: eher n≈4 als n=40. Statistisch NICHT aussagekraeftig.

     (D) QUELLENKONFLIKT ETFs, offen benannt und methodisch relevant:
         Die ETF-Referenzkurse in den Zeilen vom 04.08. und 05.08. stammen erkennbar NICHT
         aus der Xetra-Schlusskursreihe, die heute zur Aufloesung genutzt wurde (ariva.de/Xetra):
           Vanguard 04.08.: Log 165,39 vs Xetra 167,54
           Amundi Nasdaq-100 04.08.: Log 101,64 vs Xetra 104,26 · 05.08.: Log 104,94 vs Xetra 104,68
           HSBC MSCI EM 04.08.: Log 15,63 vs Xetra 15,9875
           Amundi MSCI World 04.08.: Log 158,64 vs Xetra 160,52
         Regelkonform wurde gegen den IM LOG STEHENDEN Referenzkurs aufgeloest (append-only:
         Referenzspalte wird nie veraendert). ZWEI Zeilen kippen dadurch das Vorzeichen:
           - HSBC MSCI EM 04.08. -> 11.08.: gegen Log-Referenz 15,63 ist 15,912 UP = RICHTIG.
             Auf durchgaengiger Xetra-Reihe (15,9875 -> 15,912) waere es DOWN = FALSCH.
           - Amundi Nasdaq-100 05.08. -> 12.08.: gegen Log-Referenz 104,94 ist 104,84 DOWN = FALSCH.
             Auf durchgaengiger Xetra-Reihe (104,68 -> 104,84) waere es UP = RICHTIG.
         Die beiden Faelle heben sich in der Bilanz zufaellig auf (32/40 bleibt 32/40), aber sie
         sind ein echter Messfehler und muessen in der Bachelorarbeit als solcher stehen.
         KONSEQUENZ AB HEUTE: ETF-Referenzkurse werden ausschliesslich als Xetra-Schlusskurs
         in EUR erfasst (ariva.de, Handelsplatz Xetra), damit Referenz und Aufloesung aus
         derselben Reihe kommen.

     (E) QUELLEN DIESES LAUFS: S&P 500 = FRED (S&P Dow Jones Indices), Serie SP500, Tagesschluss.
         Einzelaktien + ASML-ADR (USD) = stockanalysis.com /history/ (Datenquelle S&P Global
         Market Intelligence, "Last updated: Aug 14, 2026"), datierte Tabellenzeilen.
         ETFs = ariva.de, Handelsplatz Xetra, EUR.
         S&P-500-Schluss 07.08. (7757.64) aus der bereits primaerquellenbelegten 1T-Zeile
         vom 07.08. uebernommen; die FRED-Tabellenseite bricht vor 2026 ab, die FRED-Serienseite
         liefert nur die letzten fuenf Werte (ab 10.08.).

     (F) RUECKRECHNUNGS-CHECKS (Schluss x (1+Change) bzw. Vortagsdifferenz), alle bestanden:
         AAPL 305,26 + 0,67 = 305,93 ✓ · UNH 399,06 + 2,67 = 401,73 ✓ · PEP 140,62 + 0,17 = 140,79 ✓
         META 594,97 - 5,12 = 589,85 ✓ · TTWO 241,91 + 5,04 = 246,95 ✓
         ADBE 270,49 x (1-0,0239) = 264,03 ~ 264,02 ✓ · ASML 1847,90 x (1-0,0019) = 1844,39 ~ 1844,45 ✓
         SP500 7798,99 - 13,23 = 7785,76 ✓

     (G) ASML-QUELLENKONFLIKT (wie am 15.08.): Kopfzeile 1.844,08 vs datierte Tabellenzeile
         1.844,45. Gefuehrt wird der Tabellenwert (Datum steht daran). Richtung in allen
         betroffenen Zeilen eindeutig, Konflikt folgenlos.

     (H) MSCIWorld ZUM FUENFTEN MAL NICHT ENTHALTEN: kein verifizierter Indexstand zum 14.08.
         ermittelbar (MSCI veroeffentlicht Tagesstaende nicht frei zugaenglich; Suchtreffer
         lieferten nur den ACWI und keine datierte Schlussangabe). Das Universum sieht 13 Werte
         vor, erzeugt wurden 12. Praktischer Ersatz ist bereits im Datensatz: der Amundi Core
         MSCI World ETF (IE000BI8OT95) bildet denselben Index ab und ist lueckenlos erfasst.

     (I) KALIBRIERUNG DER NEUEN ZEILEN: Konfidenzen 51–56, KEIN Wert ueber 65. Bewusst so:
         die 1W-Reihe hat trotz 80 % Trefferquote effektiv erst vier unabhaengige Termine.
         Richtungsverteilung 10x UP / 2x DOWN. Davon sind fuenf (SP500 + vier ETFs) faktisch
         EINE Marktprognose — die Zahl "10 UP" ueberzeichnet die Streuung der Urteile.
-->

<!-- METHODIK-HINWEIS 2026-08-17 (Montag, HANDELSTAG):

     (A) LAUFZEITPUNKT 09:53 MESZ, Systemuhr verifiziert (Mon Aug 17 09:53:04 CEST 2026).
         Neue 1T-Batterie erzeugt (8 Zeilen, Modell Opus-5). KEINE Aufloesung faellig:
         die letzten 1T-Zeilen (Aufloesungsdatum 14.08.) wurden am 15.08. vollstaendig
         ausgewertet, Sa/So waren keine Handelstage, es steht keine 1T-Zeile offen.
         1W-Zeilen NICHT angefasst (Zustaendigkeit Samstags-Task).

     (B) REFERENZKURSE = Schlusskurse Fr 14.08.2026, uebernommen aus der Ist-Kurs-Spalte
         der bereits primaerquellenbelegten 1T-Zeilen vom 14.08. (Quellen dort: S&P 500 =
         FRED/S&P Dow Jones Indices; Einzelaktien + ASML-ADR in USD = stockanalysis.com
         /history/, datierte Tabellenzeilen). Aufloesungsdatum = US-Schluss Mo 17.08.

     (C) BASELINE = Richtung der letzten abgeschlossenen Tagesbewegung (13.08. -> 14.08.):
         SP500 7798.99->7785.76 DOWN · AAPL 305.26->305.93 UP · UNH 399.06->401.73 UP ·
         ASML 1847.90->1844.45 DOWN · PEP 140.62->140.79 UP · ADBE 270.49->264.02 DOWN ·
         META 594.97->589.85 DOWN · TTWO 241.91->246.95 UP.

     (D) ETFs ZUM DRITTEN MAL NICHT ENTHALTEN. Grund unveraendert und methodisch bewusst:
         Seit 15.08. gilt, dass ETF-Referenzkurse ausschliesslich als Xetra-Schlusskurs in
         EUR erfasst werden, damit Referenz und Aufloesung aus derselben Reihe stammen.
         Ein verlaesslicher technischer Abrufweg fehlt weiterhin; heute erneut versucht
         (ariva.de ueber Browser), an der Seitenstruktur gescheitert (404 bzw. ETF-Finder
         ohne Einzelwertaufloesung). Acht saubere Werte sind besser als zwoelf mit
         gemischten Quellen — die Vermischung hat am 15.08. nachweislich zwei Vorzeichen
         gedreht. MSCIWorld zum sechsten Mal nicht enthalten (kein frei zugaenglicher,
         datierter Indexstand). Universum sieht 13 Werte vor, erzeugt wurden 8.

     (E) KALIBRIERUNG: Konfidenzen 53-70. Die einzige Zeile ueber 62 ist ASML (70) und
         sie hat einen anderen Charakter als alle uebrigen: ASMLs Primaermarkt ist
         Amsterdam, und die Aktie steht dort heute Vormittag +2,68 % (1582.40 -> 1624.80
         EUR, Quelle Finanzfluss/Depotabruf 09:53 MESZ). Der US-ADR folgt dem Amsterdamer
         Kurs ueber Arbitrage — das ist KEINE zweite unabhaengige Evidenz im Sinne von
         Learning 07.08., sondern derselbe Preis in einer anderen Waehrung. Die Konfidenz
         von 70 misst deshalb nicht Prognosequalitaet, sondern Informationsvorsprung durch
         Zeitzone. FUER DIE AUSWERTUNG DER BACHELORARBEIT IST DAS ZU KENNZEICHNEN: diese
         Zeile ist mit den uebrigen nicht vergleichbar.

     (F) MARKTKONTEXT DES TAGES (fuer die spaetere Auswertung, damit die Zeilen lesbar
         bleiben): schwaechere US-Konjunkturdaten haben die Zinserhoehungserwartung
         gesenkt; EUR/USD ~1,16 (+0,37 %), Gold 4404 $ (+0,69 %), Oel 88,71 $ (+1,12 %);
         Nikkei +0,86 %, Hang Seng +1,5 %, STOXX 600 +0,2 %, S&P-Indikation +0,18 %,
         Nasdaq-100-Indikation +0,60 %. Speicher-/Chipausruestungskomplex zweite Woche
         stark (SanDisk +35 % Woche, SK Hynix +20,6 %, Micron +10,7 %). Richtungs-
         verteilung 5x UP / 3x DOWN.
-->
2026-08-17 | Opus-5 | SP500 | 1T | UP | 60 | 7785.76 | DOWN | 2026-08-17 | FALSCH | 7745.06
2026-08-17 | Opus-5 | AAPL | 1T | UP | 58 | 305.93 | UP | 2026-08-17 | FALSCH | 305.59
2026-08-17 | Opus-5 | UNH | 1T | DOWN | 53 | 401.73 | UP | 2026-08-17 | RICHTIG | 395.62
2026-08-17 | Opus-5 | ASML | 1T | UP | 70 | 1844.45 | DOWN | 2026-08-17 | RICHTIG | 1883.12
2026-08-17 | Opus-5 | PEP | 1T | DOWN | 55 | 140.79 | UP | 2026-08-17 | RICHTIG | 138.24
2026-08-17 | Opus-5 | ADBE | 1T | UP | 55 | 264.02 | DOWN | 2026-08-17 | FALSCH | 254.04
2026-08-17 | Opus-5 | META | 1T | DOWN | 54 | 589.85 | DOWN | 2026-08-17 | RICHTIG | 568.97
2026-08-17 | Opus-5 | TTWO | 1T | UP | 56 | 246.95 | UP | 2026-08-17 | FALSCH | 241.61

<!-- METHODIK-HINWEIS 2026-08-18 (Dienstag, Handelstag) — AUFLOESUNG, KEINE NEUERZEUGUNG:

     (A) LAUFZEITPUNKT 06:50 MESZ, Systemuhr verifiziert (Tue Aug 18 06:48:36 CEST 2026).
         Aufgeloest wurden die acht 1T-Zeilen vom 17.08. (nur Spalten Ergebnis + Ist-Kurs).
         1W-Zeilen NICHT angefasst. Integritaet geprueft: 108 1T-Zeilen, 0 offen,
         52 1W-Zeilen unveraendert, 0 geloeschte oder geaenderte Zeilen.

     (B) KEINE NEUE 1T-BATTERIE ERZEUGT — bewusste Abweichung. Grund: Lauf um 06:50 MESZ,
         europaeische Boersen oeffnen 09:00, US-Boersen 15:30. Referenzkurse liegen vor,
         aber es existiert KEIN Marktdatenpunkt des laufenden Tages (keine Futures, keine
         Asien-Schluesse, keine europaeische Eroeffnung). Acht Richtungen ohne Tagesdaten
         waeren geraten. Neue stehende Vorgabe des Nutzers vom 17.08. ("nur richtige Daten",
         watchlist.md, Regel 4: keine Lueckenfuellung) hat Vorrang vor der Vollstaendigkeit
         der Abschnittsstruktur. Nachholung im Tagesverlauf mit gekennzeichnetem
         Erzeugungszeitpunkt. WICHTIG FUER DIE AUSWERTUNG: Eine spaeter am Tag erzeugte
         Prognose ist methodisch NICHT dasselbe wie eine Morgenprognose (kuerzerer Horizont,
         mehr Information) und muss getrennt ausgewertet werden.

     (C) QUELLEN DER AUFLOESUNG, alle mit Rueckrechnungs-Check (Referenz x (1+Tagesaenderung)
         = Ist-Kurs):
         Einzelaktien + ASML-ADR (USD): stockanalysis.com, Datenquelle S&P Global Market
         Intelligence, Vergleichstabelle aaal-vs-unh-vs-asml-vs-pep-vs-meta-vs-ttwo-vs-now,
         Abruf 18.08.; ADBE zusaetzlich gegen die datierte Kurshistorien-Tabellenzeile
         (Aug 17, 2026 | Close 254.04 | Change -3.78%) gegengeprueft.
         Checks: AAPL 305.93 x (1-0.0011) = 305.59 ✓ exakt · UNH 401.73 x (1-0.0152)
         = 395.62 ✓ exakt · PEP 140.79 x (1-0.0181) = 138.24 ✓ exakt · ADBE 264.02 x
         (1-0.0378) = 254.04 ✓ exakt · META 589.85 x (1-0.0354) = 568.97 ✓ exakt ·
         TTWO 246.95 x (1-0.0216) = 241.62 vs 241.61 ✓ (1 Cent Rundung).

     (D) SP500 — QUELLENKONFLIKT, OFFEN BENANNT UND NICHT AUFGELOEST:
         Anadolu Agency und TradingKey melden uebereinstimmend 7745.06 / -0.52 %.
         247wallst meldet 7749.31 / -0.47 %. FRED (bisherige Primaerquelle) liefert auf
         der Tabellenseite keine 2026er-Zeile mehr. Geloggt wurde 7745.06 (zwei Quellen
         gegen eine). Rueckrechnung 7785.76 x (1-0.0052) = 7745.27 vs 7745.06, Differenz
         0.21 Punkte = Rundung der ausgewiesenen Prozentangabe. RICHTUNG IN ALLEN DREI
         QUELLEN IDENTISCH (DOWN), das Ergebnis der Zeile ist vom Konflikt unabhaengig.

     (E) ASML — BEKANNTER REFERENZKONFLIKT, dritter Tag: Die Datenbank rechnet +2.12 %
         gegen ~1844.03, der geloggte Referenzkurs ist 1844.45 (datierte Tabellenzeile
         14.08.). 1844.45 x 1.0212 = 1883.55 vs Ist 1883.12, Differenz 0.43 = 0.02 %.
         Richtung eindeutig UP, Ergebnis unabhaengig vom Konflikt.

     (F) TAGESBILANZ 17.08.: Berater 4/8 = 50.0 % · Baseline 3/8 = 37.5 %.
         Richtig: UNH, ASML, PEP, META. Falsch: SP500, AAPL, ADBE, TTWO.
         LAUFEND (nur 1T): 100 aufgeloest · Berater 60 = 60.0 % · Baseline 46 = 46.0 % ·
         Vorsprung +14.0 Pp. Verlauf: +23.0 -> +15.0 -> +13.2 -> +10.7 -> +14.1 -> +14.0.

     (G) ⚠️ KENNZEICHNUNG FUER DIE AUSWERTUNG — DIE ASML-ZEILE IST NICHT VERGLEICHBAR:
         Sie trug Konfidenz 70 (hoechster Wert der Reihe) und ging auf. Das war jedoch
         KEIN Prognoseerfolg, sondern ein Zeitzonenvorteil: Beim Erzeugen stand ASML in
         Amsterdam bereits +2.68 %, und der US-ADR folgt dem Amsterdamer Kurs ueber
         Arbitrage. Rechnet man diese Zeile heraus, lautet die Tagesbilanz 3/7 gegen 3/7
         — KEIN Vorsprung. Wer die Reihe auswertet, muss Zeilen mit Vorabinformation aus
         einem frueher schliessenden Primaermarkt separat behandeln, sonst wird
         Informationsvorsprung als Prognosefaehigkeit gemessen.
-->

2026-08-18 | Opus-5 | SP500 | 1T | DOWN | 55 | 7745.06 | DOWN | 2026-08-18 | RICHTIG | 7691.76
2026-08-18 | Opus-5 | AAPL | 1T | UP | 58 | 305.59 | DOWN | 2026-08-18 | RICHTIG | 310.03
2026-08-18 | Opus-5 | UNH | 1T | UP | 53 | 395.62 | DOWN | 2026-08-18 | FALSCH | 393.93
2026-08-18 | Opus-5 | ASML | 1T | DOWN | 54 | 1883.12 | UP | 2026-08-18 | RICHTIG | 1802.98
2026-08-18 | Opus-5 | PEP | 1T | DOWN | 54 | 138.24 | DOWN | 2026-08-18 | FALSCH | 140.13
2026-08-18 | Opus-5 | ADBE | 1T | UP | 53 | 254.04 | DOWN | 2026-08-18 | RICHTIG | 263.14
2026-08-18 | Opus-5 | META | 1T | DOWN | 57 | 568.97 | DOWN | 2026-08-18 | RICHTIG | 543.67
2026-08-18 | Opus-5 | TTWO | 1T | UP | 52 | 241.61 | DOWN | 2026-08-18 | RICHTIG | 242.40

<!-- PROTOKOLL 2026-08-18 (Nachtrag-Lauf, Batterie-Erzeugung)

     (A) ERZEUGUNGSZEITPUNKT: 18.08.2026, ca. 07:25 MESZ. VOR EU-Eroeffnung (09:00) und
         VOR US-Eroeffnung (15:30). Keinerlei Tagesdaten des laufenden Handelstags
         verfuegbar — WEDER europaeische Kurse NOCH US-Vorboerse. Dies ist der
         METHODISCH SAUBERSTE Erzeugungszeitpunkt der bisherigen Reihe.

     (B) KORREKTUR ZUM MORGENLAUF 06:50: Der Morgenlauf hatte die Batterie mit der
         Begruendung ausgelassen, es lägen "keine Marktdatenpunkte des laufenden Tages"
         vor. Das war eine FEHLANWENDUNG der Methode. Die Batterie ist definiert als
         Prognose gegen den LETZTEN ABGESCHLOSSENEN SCHLUSSKURS; Tagesdaten sind keine
         Voraussetzung, sondern waeren ein VORTEIL, den die Methode ausdruecklich nicht
         haben soll (vgl. Kommentar (G) vom 17.08. zum ASML-Zeitzonenvorteil).
         Die Reihe hat damit KEINE Luecke am 18.08.

     (C) REFERENZKURSE: alle Schluss 17.08.2026, Quelle stockanalysis.com /
         S&P Global Market Intelligence, zusaetzlich SP500 gegengeprueft gegen WSJ
         (7745.06 / -0.52 %). Rueckrechnungs-Checks bestanden.
         Der Quellenkonflikt vom 17.08. (247wallst: 7749.31 / -0.47 %) steht damit 1:3
         und wird nicht weitergefuehrt, bleibt aber protokolliert.

     (D) KEIN ZEITZONENVORTEIL BEI ASML: Amsterdam oeffnet erst 09:00, der Lauf war
         07:25. Die heutige ASML-Zeile ist im Gegensatz zur Zeile vom 17.08. eine
         ECHTE Prognose und in der Auswertung nicht gesondert zu behandeln.

     (E) INFORMATIONSGEHALT VORAB (Learning 15.08.): 5 von 8 Prognosen weichen von der
         Baseline ab (AAPL, UNH, ASML, ADBE, TTWO), 3 decken sich mit ihr (SP500, PEP,
         META). Ueberdurchschnittlicher Informationsgehalt; die Tagesbilanz ist NICHT
         weitgehend durch die Baseline vorbestimmt.

     (F) MARKTKONTEXT beim Erzeugen: US-Iran-Waffenstillstand abgelaufen, Iran
         "fully offensive"; Brent 91.06 (+0.2 % Asien), US-30J-Rendite 5.315 %
         (Zwei-Jahrzehnte-Hoch), JGB-10J 2.945 % (Hoechststand seit 09/1996),
         Nikkei -0.3 %, S&P-E-Mini-Futures FLAT, VIX-Schluss 17.08. 15.19.
         Das Futures-Signal ist bewusst NICHT in die Richtungen eingeflossen —
         Learning 18.08.: eine Prognose auf die Marktlage des Vormittags prognostiziert
         den Vormittag, nicht den Tag.

     (G) INTEGRITAET: 108 bestehende 1T-Zeilen unveraendert (0 offen), 52 1W-Zeilen
         unveraendert (12 davon offen — Zustaendigkeit Samstags-Task, hier nicht
         angefasst). Es wurde ausschliesslich angehaengt.
-->

2026-08-19 | Opus-5 | SP500 | 1T | UP | 53 | 7691.76 | DOWN | 2026-08-19 | RICHTIG | 7707.98
2026-08-19 | Opus-5 | AAPL | 1T | DOWN | 53 | 310.03 | UP | 2026-08-19 | FALSCH | 316.83
2026-08-19 | Opus-5 | UNH | 1T | DOWN | 54 | 393.93 | DOWN | 2026-08-19 | RICHTIG | 388.61
2026-08-19 | Opus-5 | ASML | 1T | UP | 56 | 1802.98 | DOWN | 2026-08-19 | FALSCH | 1751.73
2026-08-19 | Opus-5 | PEP | 1T | UP | 53 | 140.13 | UP | 2026-08-19 | RICHTIG | 142.58
2026-08-19 | Opus-5 | ADBE | 1T | DOWN | 53 | 263.14 | UP | 2026-08-19 | FALSCH | 272.47
2026-08-19 | Opus-5 | META | 1T | UP | 55 | 543.67 | DOWN | 2026-08-19 | RICHTIG | 546.03
2026-08-19 | Opus-5 | TTWO | 1T | UP | 52 | 242.40 | UP | 2026-08-19 | FALSCH | 237.04

<!--
KOMMENTAR ZUM LAUF 19.08.2026 (Morgenreport)

  (A) ERZEUGUNGSZEITPUNKT: 19.08.2026, ca. 10:15 MESZ. NACH EU-Eroeffnung (09:00),
      VOR US-Eroeffnung (15:30). Europaeische Vormittagskurse waren technisch
      verfuegbar, sind aber BEWUSST NICHT in die Richtungen eingeflossen
      (Learning 18.08.: eine Prognose auf die Marktlage des Vormittags
      prognostiziert den Vormittag, nicht den Tag). Methodisch schwaecher als der
      Lauf vom 18.08. (07:25), weil der Zeitzonenvorteil nicht ausgeschlossen,
      sondern nur nicht genutzt wurde. Zur Auswertung entsprechend kennzeichnen.

  (B) REFERENZKURSE: alle Schluss 18.08.2026, Quelle stockanalysis.com;
      SP500 zusaetzlich gegen Reuters gegengeprueft (7691.76 / -0.69 % /
      -53.30 Punkte). Rueckrechnungs-Checks fuer alle acht Assets bestanden,
      groesste Abweichung 0.09 (ASML), alle uebrigen <= 0.03. SP500 zusaetzlich
      absolut geprueft: 7745.06 - 53.30 = 7691.76 (exakt).

  (C) AUFLOESUNG 18.08.: 8 von 8 Zeilen aufgeloest. Berater 6/8 (75.0 %),
      Baseline 3/8 (37.5 %). Laufend gesamt 1T: Berater 66/108 (61.1 %),
      Baseline 49/108 (45.4 %), Abstand +15.7 Prozentpunkte.

  (D) ASML: US-ADR-Schluss (1802.98 USD, -4.26 %). Der Amsterdamer Schluss kann
      abweichen; die Batterie fuehrt ASML durchgehend gegen den US-ADR.
      Kein Zeitzonenvorteil genutzt (siehe A).

  (E) INFORMATIONSGEHALT VORAB (Learning 15.08.): 5 von 8 Prognosen weichen von der
      Baseline ab (SP500, AAPL, ASML, ADBE, META), 3 decken sich mit ihr
      (UNH, PEP, TTWO). Ueberdurchschnittlicher Informationsgehalt.

  (F) MARKTKONTEXT beim Erzeugen: SOX -5 % / SMH -4.09 % am 18.08. (groesster
      Tagesverlust seit 29.07.), US-30J-Rendite auf dem hoechsten Stand seit 2007,
      US-10J hoechster Stand seit Januar 2025, VIX-Schluss 15.84 (+0.65),
      Sektorspreizung 5.85 Pp bei 0.69 % Indexbewegung (Quotient ~8.5 = klare
      Rotation). Trump setzte die Kanada-Zoelle zwei Stunden vor Inkrafttreten
      fuer drei Tage aus. FOMC-Protokoll heute 20:00 MESZ — ein Ereignis NACH
      dem Erzeugungszeitpunkt, das alle acht Zeilen gemeinsam betrifft;
      die Tagesbilanz ist daher NICHT als acht unabhaengige Beobachtungen
      zu lesen (Clusterrisiko, wie an allen FOMC-Tagen der Reihe).

  (G) LUECKE, AUSDRUECKLICH BENANNT: MSCIWorld und die vier ETFs des
      Studien-Universums wurden NICHT erzeugt, weil zum Laufzeitpunkt kein gegen
      eine Primaerquelle gepruefter Schlusskurs vom 18.08. vorlag (europaeische
      Notierungen). Nicht geschaetzt. Konsistent mit der 1T-Reihe seit 07.08.

  (H) INTEGRITAET: 108 bestehende 1T-Zeilen unveraendert (0 offen nach dieser
      Aufloesung), 52 1W-Zeilen unveraendert (12 davon offen — Zustaendigkeit
      Samstags-Task, hier nicht angefasst). Es wurde ausschliesslich angehaengt
      bzw. bei den acht faelligen 1T-Zeilen ausschliesslich Ergebnis + Ist-Kurs
      gesetzt.
-->

2026-08-20 | Opus-5 | SP500 | 1T | UP | 54 | 7707.98 | UP | 2026-08-20 | FALSCH | 7641.16
2026-08-20 | Opus-5 | AAPL | 1T | DOWN | 51 | 316.83 | UP | 2026-08-20 | RICHTIG | 311.30
2026-08-20 | Opus-5 | UNH | 1T | UP | 54 | 388.61 | DOWN | 2026-08-20 | FALSCH | 384.85
2026-08-20 | Opus-5 | ASML | 1T | UP | 55 | 1751.73 | DOWN | 2026-08-20 | FALSCH | 1750.31
2026-08-20 | Opus-5 | PEP | 1T | DOWN | 51 | 142.58 | UP | 2026-08-20 | RICHTIG | 142.08
2026-08-20 | Opus-5 | ADBE | 1T | DOWN | 52 | 272.47 | UP | 2026-08-20 | RICHTIG | 272.22
2026-08-20 | Opus-5 | META | 1T | UP | 52 | 546.03 | UP | 2026-08-20 | FALSCH | 545.83
2026-08-20 | Opus-5 | TTWO | 1T | UP | 52 | 237.04 | DOWN | 2026-08-20 | RICHTIG | 240.15

<!--
PROTOKOLL 2026-08-20 (Lauf 09:00-10:00 MESZ, Donnerstag, Handelstag)

  (A) AUFLOESUNG 19.08.: 8 faellige 1T-Zeilen aufgeloest. Berater 4/8 (50,0 %),
      Baseline 5/8 (62,5 %). Erster Tag der Reihe, an dem die Baseline den
      Berater schlaegt. Richtig: SP500, UNH, PEP, META. Falsch: AAPL, ASML,
      ADBE, TTWO — alle vier waren Abweichungen von der Baseline, alle vier
      Mean-Reversion-Wetten gegen den Vortagsimpuls.

  (B) QUELLE UND RUECKRECHNUNG: Einzelwerte aus stockanalysis.com-Vergleichs-
      tabelle (Abruf 20.08. ~09:30 MESZ ueber Browser). Alle sieben
      Rueckrechnungs-Checks bestanden (Referenzkurs x (1 + Tagesaenderung)
      = Ist-Kurs, Abweichung < 0,01 %).

  (C) QUELLENKONFLIKT SP500, BENANNT NICHT AUFGELOEST: Yahoo-Finance-Kopfzeile
      (Abruf 20.08.) meldet Schluss 7.707,98 (+16,22 / +0,21 %); 247wallst.com
      meldet 7.705,24. Geloggt wurde 7.707,98, weil diese Zahl den Rueckrechnungs-
      Check gegen den Reuters-belegten Schluss 18.08. (7.691,76) exakt besteht
      und Dow und Nasdaq derselben Quelle das ebenfalls tun. Richtungsneutral:
      beide Werte liegen ueber dem Referenzkurs.

  (D) NEUE ZEILEN: 8 Stueck, Horizont 1T, Referenz = Schluss 19.08.,
      Aufloesung = Schluss 20.08.

  (E) INFORMATIONSGEHALT VORAB (Learning 15.08.): 6 von 8 Prognosen weichen von
      der Baseline ab (AAPL, UNH, ASML, PEP, ADBE, TTWO), 2 decken sich mit ihr
      (SP500, META). Sehr hoher Informationsgehalt — und zugleich ein
      Warnsignal: Genau dieses Muster (viele Mean-Reversion-Abweichungen) hat
      gestern 4 von 4 Fehlschlaegen produziert. Konfidenzen deshalb bewusst
      niedrig gesetzt (51-55), keine ueber 55.

  (F) MARKTKONTEXT beim Erzeugen: S&P 500 +0,21 % (7.707,98), Nasdaq +0,16 %,
      Dow +0,22 %, VIX 14,89 (-6,00 %), Gold 4.578,40 (+3,57 %).
      Sektorspreizung 5,72 Pp (XLV +3,51 % bis SOXX -2,21 %) bei 0,21 %
      Indexbewegung — Quotient ~27, hoechster gemessener Wert der Reihe.
      Treiber: Treasury verdoppelt Rueckkaeufe langlaufender Anleihen,
      30J-Rendite -10 bp auf 5,184 %; Moderna/Merck-Melanom-Studie hebt den
      gesamten Gesundheitssektor. HEUTE nach dem Erzeugungszeitpunkt:
      Alibaba-Quartalszahlen (vorboerslich US), Walmart-Zahlen,
      Erstantraege Arbeitslosenhilfe, Philly-Fed. Kein gemeinsames Ereignis,
      das alle acht Zeilen so bindet wie ein FOMC-Termin — Clusterrisiko
      geringer als gestern, aber ueber den Gesamtmarkt nie null.

  (G) LUECKE, AUSDRUECKLICH BENANNT: MSCIWorld und die vier ETFs des
      Studien-Universums wurden NICHT erzeugt, weil kein gegen eine
      Primaerquelle gepruefter europaeischer Schlusskurs vom 19.08. vorlag.
      Nicht geschaetzt. Konsistent mit der 1T-Reihe seit 07.08.

  (H) INTEGRITAET: 116 bestehende 1T-Zeilen unveraendert (0 offen nach dieser
      Aufloesung), 52 1W-Zeilen unveraendert (12 davon offen — Zustaendigkeit
      Samstags-Task, hier nicht angefasst). Es wurde ausschliesslich angehaengt
      bzw. bei den acht faelligen 1T-Zeilen ausschliesslich Ergebnis + Ist-Kurs
      gesetzt.
-->

2026-08-21 | Opus-5 | SP500 | 1T | UP | 55 | 7641.16 | DOWN | 2026-08-21 | RICHTIG | 7674.37
2026-08-21 | Opus-5 | AAPL | 1T | UP | 52 | 311.30 | DOWN | 2026-08-21 | FALSCH | 309.35
2026-08-21 | Opus-5 | UNH | 1T | UP | 53 | 384.85 | DOWN | 2026-08-21 | RICHTIG | 390.11
2026-08-21 | Opus-5 | ASML | 1T | UP | 55 | 1750.31 | DOWN | 2026-08-21 | RICHTIG | 1763.76
2026-08-21 | Opus-5 | PEP | 1T | DOWN | 52 | 142.08 | DOWN | 2026-08-21 | FALSCH | 143.48
2026-08-21 | Opus-5 | ADBE | 1T | UP | 52 | 272.22 | DOWN | 2026-08-21 | RICHTIG | 275.30
2026-08-21 | Opus-5 | META | 1T | UP | 56 | 545.83 | DOWN | 2026-08-21 | RICHTIG | 549.90
2026-08-21 | Opus-5 | TTWO | 1T | UP | 54 | 240.15 | UP | 2026-08-21 | FALSCH | 239.62

<!-- PROTOKOLL 2026-08-21 (Freitag, Handelstag)

  (A) AUFLOESUNG 20.08.: alle acht faelligen 1T-Zeilen aufgeloest. Schlusskurse
      20.08.2026 aus stockanalysis.com (Abruf 21.08.), jeweils mit bestandenem
      Rueckrechnungs-Check gegen den in der Zeile stehenden Referenzkurs
      (Previous Close der Quelle = Referenzkurs der Zeile, alle acht identisch).
      Berater 4/8 = 50,0 % · Baseline 2/8 = 25,0 %.
      Richtig: AAPL (DOWN), PEP (DOWN), ADBE (DOWN), TTWO (UP).
      Falsch: SP500, UNH, ASML, META - alle vier waren UP-Prognosen an einem
      Tag, an dem der Gesamtmarkt -0,87 % machte. Der Fehler ist ein
      gemeinsamer Marktfaktor, keine vier unabhaengigen Fehler.

  (B) MARKTVERFASSUNG 20.08. (Eingang in die heutige Kalibrierung):
      Sektorspreizung SMH +0,31 % bis XLV -1,87 % = 2,18 Pp bei einer
      Indexbewegung von -0,87 % -> Quotient ~2,5. Zum Vergleich 19.08.: ~27.
      Das war KEIN Rotationstag, sondern ein breiter Rueckzug mit einem
      identifizierbaren Einzelausloeser (Walmart -9,15 % nach schwachster
      US-Flaechenumsatzentwicklung seit 2020; WMT-Gewicht in XLP 10,64 %,
      erklaert rund zwei Drittel des XLP-Rueckgangs) plus Oel (Trump/Iran)
      und wieder steigende lange Renditen.

  (C) KONSEQUENZ AUS LEARNING 20.08. (2): Dort war die Lehre, dass
      Mean-Reversion-Wetten an einem ROTATIONSTAG die falsche Bauform sind.
      Heute liegt der umgekehrte Fall vor - kein Rotationstag, sondern ein
      Katalysator-Tag. Deshalb bewusst wieder Gegen-Baseline-Prognosen
      (6 von 8), aber Konfidenzen strikt auf 52-56 gedeckelt.

  (D) KOHAERENZRISIKO, ausdruecklich benannt: Sechs der acht Zeilen ruhen auf
      DEMSELBEN Szenario ("der Rueckgang vom 20.08. war ausloeserbedingt und
      dreht"). Das ist eine Wette, nicht sechs. Geht das Szenario schief,
      gehen alle sechs gemeinsam schief - genau wie am 19.08.

  (E) EREIGNIS HEUTE, das die Prognosen bindet: Jackson-Hole-Rede von Fed-Chef
      Kevin Warsh (erste als Vorsitzender) sowie Flash-PMIs USA/Euroraum.
      ⚠️ Quellenkonflikt zum Termin: Reuters (21.08.) beschreibt die Rede als
      unmittelbar bevorstehend, OddsShopper (19.08.) datiert das Symposium
      ausdruecklich auf das "back end of August" und nicht auf die Woche des
      20. Konflikt benannt, nicht aufgeloest - fuer die Konfidenzdeckelung
      wurde der fruehere Termin unterstellt.

  (F) META mit der hoechsten Konfidenz (56), weil dort als einzige Zeile eine
      NEUE, geprüfte Einzelinformation vorliegt: ✅ Reuters 21.08. - die
      Klaegerin im dritten der neun Bellwether-Verfahren hat ihre Klage gegen
      Meta, Google und Snap vor dem Prozess zurueckgezogen.

  (G) LUECKE, AUSDRUECKLICH BENANNT: MSCIWorld und die vier ETFs des
      Studien-Universums wurden NICHT erzeugt - kein gegen eine Primaerquelle
      geprüfter europaeischer Schlusskurs vom 20.08. verfuegbar. Nicht
      geschaetzt. Konsistent mit der 1T-Reihe seit 07.08.

  (H) INTEGRITAET: 132 bestehende 1T-Zeilen, davon 0 offen nach dieser
      Aufloesung (124 mit Ergebnis RICHTIG/FALSCH, 8 mit n/v aus frueheren
      Laeufen); bei den acht faelligen Zeilen wurden ausschliesslich
      Ergebnis + Ist-Kurs gesetzt. 1W-Zeilen unveraendert und nicht angefasst
      (Zustaendigkeit Samstags-Task). Es wurde ausschliesslich angehaengt.

  (I) LAUFENDE 1T-BILANZ nach dieser Aufloesung: 124 aufgeloeste 1T-Zeilen,
      Berater 74 richtig = 59,7 %, Baseline 56 richtig = 45,2 %.
      Vorsprung 14,5 Prozentpunkte.
-->

<!-- PROTOKOLL 2026-08-22 (Samstag, KEIN Handelstag)

  (A) KEINE NEUE BATTERIE ERZEUGT. Samstag ist kein Handelstag; nach der stehenden
      Regel wird an Wochenenden/Feiertagen keine 1T-Batterie angelegt.

  (B) AUFLOESUNG 21.08. (Freitag): alle acht faelligen 1T-Zeilen aufgeloest.
      Schlusskurse 21.08.2026 aus stockanalysis.com (Abruf 22.08.), SP500 zusaetzlich
      gegen den Reuters-Marktbericht vom 21.08. (7.674,37 / +33,21 Pkt. / +0,43 %).
      Rueckrechnungs-Check (Kurs / (1 + Tagesaenderung) = Vortagesschluss) bei allen
      acht Zeilen BESTANDEN, groesste Abweichung 0,352 Punkte beim SP500 (Rundung der
      auf zwei Nachkommastellen gemeldeten Prozentangabe), bei den sieben Einzelwerten
      jeweils unter 0,03 Einheiten.
      Berater 5/8 = 62,5 % · Baseline 1/8 = 12,5 %.
      Richtig: SP500, UNH, ASML, ADBE, META. Falsch: AAPL, PEP, TTWO.

  (C) BEFUND ZUR BAUFORM: Am 21.08. war der Berater-Vorsprung mit 50,0 Prozentpunkten
      der groesste Tagesvorsprung der Reihe. Ursache ist NICHT bessere Einzelanalyse,
      sondern die Marktverfassung: Sechs der acht Zeilen waren bewusste Abweichungen
      von der Baseline (Protokoll 21.08., Punkt C), und der Markt drehte tatsaechlich
      (+0,43 % nach -0,87 %). Sieben von acht Assets schlossen im Plus - eine
      UP-Wette war an diesem Tag fast eine Wette auf den Index. Der Vorsprung misst
      einen richtigen Markt-Call, nicht acht richtige Werturteile. Das ist die exakte
      Spiegelung des Befunds vom 20.08. (ein falscher Markt-Call, viermal gezaehlt).

  (D) QUELLENKONFLIKT UNH, offen benannt: stockanalysis.com weist den Schluss 21.08.
      mit 390,11 $ aus, eine Yahoo-gestuetzte Zusammenfassung mit 390,14 $. Differenz
      0,03 $ (0,008 %). Fuer das Ergebnis folgenlos (Referenz 384,85, beide Werte UP).
      Geloggt wurde der Wert der Primaerquelle mit bestandenem Rueckrechnungs-Check.

  (E) LUECKE, AUSDRUECKLICH BENANNT: MSCIWorld und die vier ETFs des Studien-Universums
      standen fuer den 21.08. erneut NICHT in der Reihe (seit 07.08. keine gegen eine
      Primaerquelle geprueften europaeischen Schlusskurse verfuegbar, Portfolio-Scraper
      anbieterseitig gesperrt). Nicht geschaetzt.

  (F) INTEGRITAET: Dateilaenge vor und nach der Auflösung unveraendert (1049 Zeilen vor
      diesem Kommentar). 140 1T-Zeilen gesamt, davon 0 offen (132 mit Ergebnis
      RICHTIG/FALSCH, 8 mit n/v aus frueheren Laeufen). Bei den acht faelligen Zeilen
      wurden ausschliesslich Ergebnis + Ist-Kurs gesetzt, keine andere Spalte, keine
      Reihenfolge. 1W-Zeilen unveraendert und nicht angefasst (12 davon offen -
      Zustaendigkeit Samstags-Task portfolio-studien-prognose, hier bewusst nicht
      angefasst). Es wurde ausschliesslich angehaengt.

  (G) LAUFENDE 1T-BILANZ nach dieser Aufloesung: 132 aufgeloeste 1T-Zeilen,
      Berater 79 richtig = 59,85 %, Baseline 57 richtig = 43,18 %.
      Vorsprung 16,67 Prozentpunkte (Vortag: +14,5).
-->

2026-08-22 | Opus-5 | SP500 | 1W | DOWN | 53 | 7674.37 | DOWN | 2026-08-28 | FALSCH | 7711.76
2026-08-22 | Opus-5 | Vanguard FTSE All-World | 1W | DOWN | 53 | 166.30 | DOWN | 2026-08-28 | FALSCH | 168.54
2026-08-22 | Opus-5 | Amundi Nasdaq-100 | 1W | DOWN | 54 | 102.24 | DOWN | 2026-08-28 | FALSCH | 104.20
2026-08-22 | Opus-5 | Amundi MSCI World | 1W | DOWN | 53 | 158.615 | DOWN | 2026-08-28 | FALSCH | 161.015
2026-08-22 | Opus-5 | AAPL | 1W | UP | 52 | 309.35 | UP | 2026-08-28 | RICHTIG | 319.70
2026-08-22 | Opus-5 | UNH | 1W | DOWN | 53 | 390.11 | DOWN | 2026-08-28 | FALSCH | 392.95
2026-08-22 | Opus-5 | ASML | 1W | DOWN | 52 | 1763.76 | DOWN | 2026-08-28 | RICHTIG | 1696.16
2026-08-22 | Opus-5 | PEP | 1W | UP | 55 | 143.48 | UP | 2026-08-28 | FALSCH | 141.07
2026-08-22 | Opus-5 | ADBE | 1W | DOWN | 52 | 275.30 | UP | 2026-08-28 | FALSCH | 291.52
2026-08-22 | Opus-5 | META | 1W | DOWN | 51 | 549.90 | DOWN | 2026-08-28 | FALSCH | 578.02
2026-08-22 | Opus-5 | TTWO | 1W | UP | 57 | 239.62 | DOWN | 2026-08-28 | FALSCH | 235.39

<!-- METHODIK-HINWEIS 2026-08-22 (Samstag) — WOCHEN-TASK portfolio-studien-prognose, Horizont 1W:

     (A) AUFLOESUNG DER 12 ZEILEN VOM 16.08. (faellig 21.08.):
         Berater 3/11 = 27,3 % · Baseline 3/11 = 27,3 % · GLEICHSTAND, kein Vorsprung.
         Richtig waren nur UNH (DOWN), PEP (UP) und ADBE (UP). Eine Zeile (HSBC MSCI EM)
         steht auf n/v, siehe (D). Laufend gesamt 1W: Berater 35/51 = 68,6 % ·
         Baseline 30/51 = 58,8 %.

     (B) DAS AM 16.08. BENANNTE RISIKO IST EINGETRETEN — WOERTLICH. Im Hinweis vom 16.08.
         stand unter (I): "Richtungsverteilung 10x UP / 2x DOWN. Davon sind fuenf
         (SP500 + vier ETFs) faktisch EINE Marktprognose." Genau diese eine Marktprognose
         war falsch: der S&P 500 fiel von 7785,76 auf 7674,37 (-1,43 %), und damit kippten
         SP500 und alle drei aufloesbaren ETFs gleichzeitig — vier Zeilen, ein Irrtum.
         Von den acht falschen Zeilen sind hoechstens fuenf unabhaengige Fehlurteile
         (AAPL, ASML, META, TTWO plus der Markt-Call). Die Quote 3/11 UEBERZEICHNET das
         Versagen genauso, wie die 80 % vom 16.08. den Erfolg ueberzeichnet haben.
         >>> BEIDE Richtungen desselben Messfehlers liegen jetzt dokumentiert vor. Das ist
         >>> fuer die Bachelorarbeit wertvoller als jede der beiden Quoten fuer sich.

     (C) BAUFORM DER NEUEN ZEILEN BEWUSST GEAENDERT — und zwar nicht als Umkehr-Reflex.
         Die naheliegende Reaktion auf eine gescheiterte 10x-UP-Woche waere 10x DOWN. Das
         waere derselbe Fehler mit umgedrehtem Vorzeichen. Stattdessen: Markt-Call (SP500 +
         drei ETFs) = DOWN 53–54, begruendet mit fuenf Handelstagen fallender Hochs, der
         Walmart-Reaktion als Konsumsignal und einer hoch gelegten Latte vor dem
         Nvidia-Bericht am 26.08. Die Einzelwerte sind davon getrennt beurteilt: UP nur dort,
         wo ein eigener, benennbarer Grund vorliegt — AAPL (stieg in einer fallenden Woche,
         relative Staerke), PEP (Defensiv-Rotation, stieg gegen den Markt), TTWO (datierter
         Katalysator GTA-VI-Trailer am 27.08., liegt IM Prognosefenster). DOWN bei UNH
         (Abwaertstrend ohne Katalysator), ASML (hohes Beta zum Nvidia-Termin), ADBE
         (Anstieg war geruechtegetrieben: Workday-Uebernahmespekulation) und META
         (-6,8 % in einer Woche, kein benannter Gegenkatalysator).
         Verteilung: 7x DOWN / 4x UP. Vier davon (Markt-Call) sind EIN Urteil, nicht vier.

     (D) HSBC MSCI EM = n/v, UND DAS IST EINE ENTSCHEIDUNG, KEINE LUECKE:
         Die ariva-Xetra-Kurshistorie fuer IE000KCS7J59 endet weiterhin am 14.08.26; die
         Seite kam aus einem alten Cache (Anzeigenslot vom 15.–17.08.). Cache-Umgehung ueber
         ?month=2026-08 und ?boerse_id=6 lieferte frische Seiten, aber jeweils "keine
         historischen Kursdaten vorhanden". Ein XETRA-Schlusskurs zum 21.08. ist damit
         nicht beschaffbar.
         VERFUEGBARE RICHTUNGSINDIZIEN, beide DOWN: (1) wallstreet-online, Handelsplatz
         Stuttgart: 21.08. letzter Kurs 16,16 EUR, eine Woche zuvor 16,17 EUR (-0,07 %);
         (2) ariva-Performancebox derselben frischen Seite: "1 Woche 16,091 / -0,88 %",
         was auf rund 15,95 EUR fuehrt. Die Prognose lautete UP — sie waere also nach
         beiden Lesarten FALSCH.
         TROTZDEM n/v STATT FALSCH: Der Referenzkurs der Zeile (16,091) ist ein
         Xetra-Schluss. Ein Stuttgarter Kurs dagegenzurechnen ist exakt der Fehler, den
         der Eintrag vom 16.08. abgestellt hat ("Referenz und Aufloesung aus derselben
         Reihe"). Eine Regel, die nur gilt, wenn sie bequem ist, ist keine Regel.
         Die Richtungsindizien stehen hier, damit eine Robustheitspruefung die Zeile
         nachtraeglich als DOWN/FALSCH mitzaehlen KANN — bewusst und dokumentiert,
         statt still unterstellt.
         FOLGE: Fuer HSBC MSCI EM wurde diese Woche AUCH KEINE neue 1W-Zeile erzeugt,
         weil dafuer derselbe fehlende Xetra-Schluss als Referenz noetig waere.

     (E) QUELLEN: S&P 500 21.08. = 7674,37 aus der bereits primaerquellenbelegten 1T-Zeile
         vom 21.08. FRED war zum Laufzeitpunkt erst bis 20.08. fortgeschrieben (7641,16) —
         dieser Wert stimmt exakt mit dem Referenzkurs der 1T-Zeile vom 21.08. ueberein,
         was die Reihe gegenpruefbar macht. Einzelaktien + ASML-ADR (USD) aus den 1T-Zeilen
         vom 21.08. (Morgenreport, Primaerquelle, Rueckrechnung dort protokolliert).
         ETFs = ariva.de, Handelsplatz Xetra, EUR, datierte Tabellenzeilen 21.08.:
         Vanguard 166,30 · Amundi Nasdaq-100 102,24 · Amundi Core MSCI World 158,615.

     (F) HINWEIS ZU DEN ARIVA-PERFORMANCEBOXEN: Sie sind als Kursquelle UNBRAUCHBAR.
         Beispiel Amundi Nasdaq-100: Box "1 Woche 105,24 / -3,27 %" ergaebe 101,80 — das ist
         der Schluss vom 20.08., nicht vom 21.08. (102,24). Die Boxen rechnen gegen einen
         Realtime-Kurs eines anderen Handelsplatzes. Gefuehrt wird ausschliesslich die
         datierte Tabellenzeile (Regel vom 13.08.).

     (G) MSCIWorld zum sechsten Mal nicht enthalten (kein frei verfuegbarer, datierter
         Indexstand). Universum sieht 13 Werte vor, erzeugt wurden 11 (MSCIWorld + HSBC EM
         fehlen). Praktischer Ersatz fuer MSCIWorld bleibt der Amundi Core MSCI World ETF.

     (H) KALIBRIERUNG: Konfidenzen 51–57, kein Wert ueber 65. Nach einer 3/11-Woche waere
         alles darueber nicht zu rechtfertigen. Hoechster Wert TTWO 57 — als einzige Zeile
         mit einem DATIERTEN Ereignis im Prognosefenster.
-->

2026-08-24 | Opus-5 | SP500 | 1T | DOWN | 54 | 7674.37 | UP | 2026-08-24 | RICHTIG | 7652.86
2026-08-24 | Opus-5 | AAPL | 1T | DOWN | 52 | 309.35 | DOWN | 2026-08-24 | FALSCH | 310.34
2026-08-24 | Opus-5 | UNH | 1T | UP | 55 | 390.11 | UP | 2026-08-24 | RICHTIG | 398.76
2026-08-24 | Opus-5 | ASML | 1T | DOWN | 57 | 1763.76 | UP | 2026-08-24 | RICHTIG | 1740.13
2026-08-24 | Opus-5 | PEP | 1T | UP | 55 | 143.48 | UP | 2026-08-24 | RICHTIG | 144.67
2026-08-24 | Opus-5 | ADBE | 1T | DOWN | 52 | 275.30 | UP | 2026-08-24 | FALSCH | 276.27
2026-08-24 | Opus-5 | META | 1T | DOWN | 52 | 549.90 | UP | 2026-08-24 | FALSCH | 559.02
2026-08-24 | Opus-5 | TTWO | 1T | UP | 56 | 239.62 | DOWN | 2026-08-24 | FALSCH | 233.50

<!-- METHODIK-HINWEIS zum Lauf 24.08.2026 (Montag, Handelstag)

     (A) AUFLOESUNG: KEINE offene 1T-Zeile faellig. Die Batterie vom 21.08. wurde am
         22.08. vollstaendig aufgeloest; Sa 22.08. und So 23.08. waren keine Handelstage,
         es wurden dort keine 1T-Zeilen erzeugt. Bestand vor diesem Lauf: 140 1T-Zeilen,
         davon 132 mit Ergebnis (79 RICHTIG / 53 FALSCH), 8 n/v, 0 offen. Heute neu aus
         der Datei gerechnet, nicht aus einem frueheren Report uebernommen:
         Berater 79/132 = 59,85 % · Baseline 57/132 = 43,18 % · Vorsprung +16,67 Pp.
         1W-Zeilen NICHT angefasst (12 davon offen - Zustaendigkeit Samstags-Task).

     (B) REFERENZKURSE, alle ✅ Primaerquelle stockanalysis.com (Daten: S&P Global Market
         Intelligence), datierte Tabellenzeile 21.08.2026, Rueckrechnung jeweils bestanden:
         AAPL 309.35 (-0.63 %, Vortag 311.30) · UNH 390.11 (+1.37 %, 384.85) ·
         ASML 1763.76 (+0.77 %, 1750.31, US-ADR in USD) · PEP 143.48 (+0.99 %, 142.08) ·
         ADBE 275.30 (+1.13 %, 272.22) · META 549.90 (+0.75 %, 545.83) ·
         TTWO 239.62 (-0.22 %, 240.15).
         SP500 7674.37 (+0.43 %) unabhaengig belegt (Yahoo-Finance-Liveblog 21.08.),
         Rueckrechnung 7674.37 / 1.0043 = 7641.5 gegen 7641.16 ✅.

     (C) ⚠️ NUR 8 STATT 13 ZEILEN - QUELLENAUSFALL BEI DEN ETFs, offen benannt:
         Die ariva-Kurshistorie liefert seit heute fuer ALLE geprueften ETFs Tabellenzeilen
         aus dem August 2019 statt 2026 (getestet: Vanguard FTSE All-World und Amundi Core
         Nasdaq-100, je mit und ohne Cache-Umgehungsparameter boerse_id/month/nocache;
         der Monats-Dropdown der Seite selbst bietet nur "2019-08" an). Damit ist KEIN
         Xetra-Schlusskurs zum 21.08. beschaffbar - und, entscheidend, auch die AUFLOESUNG
         am 25.08. waere nicht moeglich.
         boerse.de liefert zwar Zeilen zum 21.08., aber vom Handelsplatz Stuttgart (EUWAX).
         Die ETF-Reihe wird seit dem 16.08. ausdruecklich auf XETRA gefuehrt, damit Referenz
         und Aufloesung aus derselben Reihe stammen. Ein Handelsplatzwechsel mitten in der
         Reihe waere exakt der Messfehler, den diese Regel verhindern soll.
         FOLGE: Keine Zeile fuer Vanguard FTSE All-World, Amundi Core Nasdaq-100,
         Amundi Core MSCI World und HSBC MSCI EM. Eine Zeile zu erzeugen, die absehbar als
         n/v endet, verschlechtert den Datensatz, statt ihn zu fuellen (Regel vom 22.08.).
         DEM NUTZER ZUR ENTSCHEIDUNG VORGELEGT (Report 24.08., Abschnitt 13): warten /
         Handelsplatz mit dokumentiertem Reihenbruch wechseln / ETFs aus dem Universum
         nehmen. Empfehlung: Wechsel, aber fruehestens nach drei Ausfalltagen in Folge.

     (D) MSCIWorld zum siebten Mal nicht enthalten (kein frei verfuegbarer, datierter
         Indexstand). Universum sieht 13 Werte vor, erzeugt wurden 8.

     (E) RICHTUNGSVERTEILUNG: 5x DOWN / 3x UP. Abweichung von der Baseline in 5 von 8
         Zeilen (SP500, ASML, ADBE, META, TTWO).

     (F) ABHAENGIGKEITEN, ausdruecklich benannt (Learning 22.08. (4)):
         VIER Zeilen ruhen auf DEMSELBEN Szenario "risk-off-Montag vor Nvidia" -
         SP500, AAPL, ADBE, META. Das ist EIN Markt-Call, vierfach gezaehlt, in beide
         Richtungen. Die uebrigen vier haben je einen eigenen benannten Grund:
         ASML  = Read-Across der Asien-Halbleiterschwaeche (Kospi -1,4 %, Samsung ueber
                 -6 %) auf die Investitionsbudgets der Kunden; deshalb die hoechste
                 Konfidenz des Tages (57) und die einzige DOWN-Zeile mit eigener Ursache.
         UNH   = Defensiv-Rotation vor Nvidia, XLV +1,29 % am 21.08., keine KI-Kopplung.
         PEP   = Kostenkanal entlastet (Oel -1,22 % heute frueh auf 91,08 $) plus
                 Defensiv-Rotation; relative Staerke seit 17.08. (+3,79 % in vier Tagen).
         TTWO  = einziger datierter Eigenkatalysator im Fenster ("GTA VI: An Extended
                 Look" am 27.08.); nachboerslich 21.08. bereits +1,28 % auf 242.69.
         ⚠️ Die ASML-Zeile und die qualitative Prognose P32 (SMH schlechter als XLV)
         ruhen auf demselben Szenario - zwei Treffer waeren EIN Urteil, zweimal gezaehlt.

     (G) KALIBRIERUNG: Konfidenzen 52-57, kein Wert darueber. Der Markt-Call bekommt
         bewusst nur 52-54, weil die Vorboersenlage ein schwacher Praediktor fuer den
         US-Schluss ist (eigener Fehlschlag P21 vom 17.08.).

     (H) INTEGRITAET: 140 bestehende 1T-Zeilen unveraendert (0 offen vor diesem Lauf),
         52 1W-Zeilen unveraendert (12 davon offen). Nur angehaengt, nichts geloescht,
         nichts ueberschrieben, keine Reihenfolge geaendert.
-->

2026-08-25 | Opus-5 | SP500 | 1T | UP | 53 | 7652.86 | DOWN | 2026-08-25 | RICHTIG | 7677.24
2026-08-25 | Opus-5 | Vanguard FTSE All-World | 1T | UP | 57 | 165.62 | DOWN | 2026-08-25 | RICHTIG | 166.30
2026-08-25 | Opus-5 | Amundi Nasdaq-100 | 1T | UP | 55 | 101.36 | DOWN | 2026-08-25 | RICHTIG | 101.86
2026-08-25 | Opus-5 | Amundi MSCI World | 1T | UP | 56 | 158.495 | DOWN | 2026-08-25 | RICHTIG | 158.91
2026-08-25 | Opus-5 | HSBC MSCI EM | 1T | UP | 53 | 15.8695 | n/v | 2026-08-25 | RICHTIG | 16.1055
2026-08-25 | Opus-5 | AAPL | 1T | UP | 53 | 310.34 | UP | 2026-08-25 | FALSCH | 309.90
2026-08-25 | Opus-5 | UNH | 1T | UP | 54 | 398.76 | UP | 2026-08-25 | FALSCH | 396.59
2026-08-25 | Opus-5 | ASML | 1T | DOWN | 53 | 1740.13 | DOWN | 2026-08-25 | FALSCH | 1744.16
2026-08-25 | Opus-5 | PEP | 1T | UP | 55 | 144.67 | UP | 2026-08-25 | FALSCH | 142.27
2026-08-25 | Opus-5 | ADBE | 1T | DOWN | 52 | 276.27 | UP | 2026-08-25 | RICHTIG | 273.92
2026-08-25 | Opus-5 | META | 1T | DOWN | 52 | 559.02 | UP | 2026-08-25 | FALSCH | 570.05
2026-08-25 | Opus-5 | TTWO | 1T | UP | 55 | 233.50 | DOWN | 2026-08-25 | FALSCH | 232.93

<!-- METHODIK-HINWEIS 2026-08-25 (Morgenreport, Horizont 1T)

     (A) AUFLOESUNG: Die 8 offenen 1T-Zeilen vom 24.08. wurden aufgeloest (Ergebnis + Ist-Kurs).
         Quelle stockanalysis.com (Datenlieferant S&P Global Market Intelligence), US-Schlusskurse
         24.08.2026. Rueckrechnungs-Check fuer alle acht bestanden.
         TAGESBILANZ: Berater 4/8 = 50,0 % · Baseline 5/8 = 62,5 %. Verlorener Tag.
         Befund: Die drei Zeilen mit EIGENSTAENDIGER Begruendung (UNH, PEP, ASML) waren alle
         richtig; von den fuenf aus dem Markt-Call ABGELEITETEN Zeilen war eine richtig (SP500).
         Ursache: Der 24.08. war eine Sektorrotation (Spreizung 4,13 Pp bei 0,28 % Indexbewegung),
         kein Markt-risk-off. Ein fallender Index bei steigender Aktienmehrheit ist genau der Fall,
         den ein abgeleiteter Markt-Call nicht abbilden kann. Siehe learnings.md 2026-08-25 (1).

     (B) ✅ ETF-DATENAUSFALL BEHOBEN. Der ariva-Ausfall vom 22./24.08. ist umgangen, ohne die
         Reihe zu brechen: Die Deutsche Boerse selbst weist auf ihren ETF-Seiten den
         "Schlusspreis des letzten Handelstages" je Handelsplatz aus - also XETRA, dieselbe
         Reihe, aus der die bisherigen Referenzkurse stammen. Primaerquelle statt Aggregator,
         kein Handelsplatzwechsel, kein dokumentierter Reihenbruch noetig.
         Erhobene Xetra-Schlusskurse 24.08.2026:
           Vanguard FTSE All-World  165,62   (21.08.: 166,30  -> -0,41 %)
           Amundi Core Nasdaq-100   101,36   (21.08.: 102,24  -> -0,86 %)
           Amundi Core MSCI World   158,495  (21.08.: 158,615 -> -0,08 %)
           HSBC MSCI EM              15,8695 (21.08.: nicht erhoben)
         Plausibilitaet gegen S&P 500 -0,28 % / Nasdaq Composite -0,76 % und EUR/USD 1,1659
         geprueft; Jahr und Groessenordnung jeder Tabellenzeile geprueft (Learning 24.08.).
         Die drei zur Entscheidung vorgelegten Optionen (warten / Handelsplatzwechsel /
         ETFs aus dem Universum nehmen) sind damit GEGENSTANDSLOS.

     (C) HSBC MSCI EM: Referenzkurs vorhanden, BASELINE = n/v. Fuer den 21.08. existiert kein
         erhobener Xetra-Schluss, die Richtung der letzten Tagesbewegung ist daher nicht
         bestimmbar. Die Zeile wird trotzdem erzeugt: Prognose und Ergebnis sind die
         auswertbaren Felder, die Baseline ist ein Vergleichsfeld. Ab dem 26.08. wieder
         berechenbar. Dokumentierte Luecke statt unterstellter Wert (Regel 22.08.).

     (D) MSCIWorld zum ACHTEN Mal nicht enthalten (kein frei verfuegbarer, datierter
         Indexstand). Universum sieht 13 Werte vor, erzeugt wurden 12.

     (E) RICHTUNGSVERTEILUNG: 9x UP / 3x DOWN. Einseitig; Grund benannt (freundliche
         europaeische Vormittagslage: DAX +0,40 %, EURO STOXX 50 +0,27 %, Nikkei +0,66 %,
         S&P-500-Indikation +0,17 %, Nasdaq-100-Indikation +0,40 %, EUR/USD 1,1659).
         Die Einseitigkeit ist das groesste Risiko dieses Satzes und wird hier ausdruecklich
         als solches vermerkt.

     (F) ABHAENGIGKEITEN, ausdruecklich benannt:
         SECHS Zeilen ruhen auf DEMSELBEN Markt-Call - SP500, alle vier ETFs, AAPL.
         Ein Urteil, sechsfach gezaehlt, in beide Richtungen. Genau dieser Effekt hat die
         Bilanz vom 24.08. gedrueckt; die Konsequenz wurde bei den QUALITATIVEN Prognosen
         gezogen (drei mit je eigenem Mechanismus), nicht hier - das feste Universum laesst
         die Korrelation innerhalb der Batterie nicht vermeiden, nur benennen.
         Die uebrigen sechs haben je einen eigenen Grund:
           UNH  = versicherer-spezifischer Treiber (Care Ratio 86,7 % vs. 89,4 %, Forbes 24.08.);
                  UNH lief 2,17 Pp besser als der eigene Sektor.
           PEP  = XLP staerkster Sektor des Tages (+1,70 %) plus Oelrueckgang -2,5 %
                  (Kostenkanal, Lernbox 18.08.); vierter Anstieg in fuenf Tagen.
           ASML = anhaltender Positionsabbau im Halbleitersektor vor Nvidia (26.08.);
                  SMH -2,43 %. GEGENEVIDENZ ausdruecklich: AMD notiert heute frueh im
                  europaeischen Handel +1,84 %, die Vorboerse spricht gegen diese Zeile.
                  Deshalb nur 53.
           ADBE = +8,75 % in fuenf Handelstagen ohne Geschaeftsnachricht; die Bewegung ruht auf
                  Uebernahme-Fantasie und einer vier Tage alten Kurszielrunde.
           META = Prozesswoche 2 in Oakland; +1,66 % am 24.08. ohne benannten Ausloeser.
           TTWO = datierter Eigenkatalysator 27.08. ("An Extended Look"); nachboerslich 24.08.
                  bereits +0,90 % auf 235,59. Gegenargument benannt: Leak-Druck seit 18.08.,
                  der genau diese Zeile gestern hat scheitern lassen.
         ⚠️ Die ASML-Zeile und die qualitative Prognose P35 (SMH am 26.08. unter 560,42)
         ruhen auf demselben Szenario - zwei Treffer waeren EIN Urteil, zweimal gezaehlt.

     (G) KALIBRIERUNG: Konfidenzen 52-57, kein Wert darueber. Nach einem 50-%-Tag ist
         Zurueckhaltung die richtige Antwort, nicht Kompensation. Der Markt-Call bekommt
         bewusst nur 53-57, weil die Vorboersenlage ein schwacher Praediktor fuer den
         US-Schluss ist (eigener Fehlschlag P21 vom 17.08.). Die ETF-Zeilen erhalten leicht
         HOEHERE Konfidenz als die SP500-Zeile, weil ihr Xetra-Schluss um 17:30 MESZ faellt
         und damit einen bereits ueberwiegend beobachtbaren Handelstag abbildet.

     (H) INTEGRITAET: 148 bestehende 1T-Zeilen unveraendert bis auf die 8 planmaessig
         aufgeloesten (Ergebnis + Ist-Kurs, sonst nichts); 63 1W-Zeilen unveraendert
         (11 davon offen, Aufloesung 28.08. durch den Samstags-Task). Nur angehaengt,
         nichts geloescht, nichts ueberschrieben, keine Reihenfolge geaendert.
-->

## Batterie 2026-08-26 (Mittwoch, Handelstag) — Horizont 1T, Modell Opus-5

2026-08-26 | Opus-5 | SP500 | 1T | DOWN | 52 | 7677.24 | UP | 2026-08-26 | RICHTIG | 7675.70 
2026-08-26 | Opus-5 | Vanguard FTSE All-World | 1T | UP | 57 | 166.30 | UP | 2026-08-26 | RICHTIG | 166.54 
2026-08-26 | Opus-5 | Amundi Nasdaq-100 | 1T | DOWN | 54 | 101.86 | UP | 2026-08-26 | FALSCH | 101.92 
2026-08-26 | Opus-5 | Amundi MSCI World | 1T | UP | 56 | 158.91 | UP | 2026-08-26 | RICHTIG | 159.055 
2026-08-26 | Opus-5 | HSBC MSCI EM | 1T | UP | 56 | 16.1055 | UP | 2026-08-26 | RICHTIG | 16.1995 
2026-08-26 | Opus-5 | AAPL | 1T | DOWN | 52 | 309.90 | DOWN | 2026-08-26 | FALSCH | 313.45 
2026-08-26 | Opus-5 | UNH | 1T | UP | 52 | 396.59 | DOWN | 2026-08-26 | RICHTIG | 401.01 
2026-08-26 | Opus-5 | ASML | 1T | UP | 55 | 1744.16 | UP | 2026-08-26 | RICHTIG | 1745.64 
2026-08-26 | Opus-5 | PEP | 1T | DOWN | 54 | 142.27 | DOWN | 2026-08-26 | RICHTIG | 142.19 
2026-08-26 | Opus-5 | ADBE | 1T | DOWN | 55 | 273.92 | DOWN | 2026-08-26 | RICHTIG | 273.47 
2026-08-26 | Opus-5 | META | 1T | DOWN | 53 | 570.05 | UP | 2026-08-26 | FALSCH | 576.14 
2026-08-26 | Opus-5 | TTWO | 1T | UP | 52 | 232.93 | DOWN | 2026-08-26 | RICHTIG | 233.45 

<!-- PROTOKOLL 26.08.2026 (1T)

     (A) REFERENZKURSE: US-Werte = Schluss 25.08.2026 (stockanalysis.com / S&P Global Market
         Intelligence), Rueckrechnung Kurs x (1 + Tagesaenderung) = Vortagesschluss fuer ALLE
         acht US-Zeilen bestanden. SP500 = Reuters-Marktbericht 25.08. (7677.24, +0,32 %),
         Rueckrechnung 7677.24 / 1,0032 = 7652,79 gegen Referenz 7652,86 - bestanden.
         ETFs = Xetra-Schlusspreis 25.08. direkt von der Deutschen Boerse
         ("Schlusspreis des letzten Handelstages"), All-World zusaetzlich gegengeprueft:
         aktueller Preis 166,54 minus Differenz zum Vortag 0,24 = 166,30 - bestanden.

     (B) MSCIWorld zum NEUNTEN Mal nicht enthalten (kein frei verfuegbarer, datierter
         Indexstand). Universum sieht 13 Werte vor, erzeugt wurden 12.

     (C) RICHTUNGSVERTEILUNG: 6x UP / 6x DOWN. Ausgewogen, und - anders als am 25.08. -
         NICHT aus einem einzigen Markt-Call abgeleitet.

     (D) DER ZENTRALE UNTERSCHIED ZU GESTERN, ausdruecklich benannt:
         Die vier ETF-Zeilen und die SP500-Zeile zeigen bewusst in TEILWEISE
         GEGENLAEUFIGE Richtungen. Das ist kein Widerspruch, sondern eine
         Handelszeiten-Aussage: Die Xetra-Schlusskurse fallen um 17:30 MESZ und bilden
         damit ueberwiegend den bereits beobachtbaren europaeischen Tag ab
         (DAX +0,20 %, EURO STOXX 50 +0,05 %, Nikkei +0,35 % um 11:45 MESZ;
         All-World notiert bereits +0,14 % ueber seinem Vortagesschluss, Amundi MSCI World
         +0,08 %). Der S&P 500 schliesst dagegen um 22:00 MESZ - NACH der PCE-Zahl
         (14:30) und VOR den Nvidia-Zahlen (~22:20). Zwei verschiedene Zeitfenster,
         zwei verschiedene Urteile.
         Der Amundi Nasdaq-100 bekommt als einziger ETF DOWN, weil die
         Nasdaq-100-Indikation um 11:45 MESZ bei -0,18 % steht und der Fonds den
         US-Index abbildet, nicht den europaeischen Handel.

     (E) ABHAENGIGKEITEN:
         Drei ETF-Zeilen (All-World, MSCI World, MSCI EM) ruhen auf DEMSELBEN Call
         "freundlicher europaeischer Tag bis 17:30". Ein Urteil, dreifach gezaehlt.
         Die uebrigen neun haben je einen eigenen Grund:
           SP500 = zwei Ereignisrisiken an einem Tag (PCE 14:30, Nvidia nachboerslich)
                   nach einem +0,32-%-Tag; Vorboerse leicht negativ. Nur 52, weil die
                   Vorboerse ein schwacher Praediktor ist (eigener Fehlschlag P21, 17.08.).
           LYMS  = Nasdaq-100-Indikation -0,18 %.
           AAPL  = Mac-mini-Vorstellung ist verarbeitet (-0,14 % am 25.08.),
                   vorboerslich 309,46 (-0,14 %); kein eigener Treiber bis zum
                   iPhone-Event am ~09.09.
           UNH   = nach dem Sprung (+2,22 % am 24.08.) und der Teil-Rueckgabe
                   (-0,54 % am 25.08.) Stabilisierung erwartet. Nur 52 - die
                   qualitative Prognose P34 mit genau diesem Wert ist gestern
                   GESCHEITERT, das ist hier eingepreist.
           ASML  = SMH +1,65 %, ASML nur +0,23 % - 1,42 Pp Rueckstand auf den eigenen
                   Sektor an einem Sektor-Tag; vorboerslich 1747,00 (+0,16 %);
                   BofA-Bestaetigung als Top Pick (25.08.).
           PEP   = XLP -1,06 % (zweitschwaechster Sektor), Rotation aus Defensiven
                   laeuft; am Nvidia-Tag bleibt Basiskonsum unattraktiv.
           ADBE  = IGV -0,59 %; Software-Investoren warten die Salesforce-Zahlen
                   (heute nachboerslich) ab.
           META  = +1,97 % am 25.08. auf ein VERGLEICHSGERUECHT (Stocktwits/Gary Black),
                   nicht auf eine Bestaetigung. Geruechte-Spruenge geben typischerweise
                   teilweise nach, solange nichts bestaetigt wird.
           TTWO  = Vortag des "An Extended Look" (27.08.).
         !! WARNUNG ZUR TTWO-ZEILE: Genau diese Begruendung ("Vorlauf auf einen datierten
            Eigenkatalysator") ist am 24.08. UND am 25.08. gescheitert - zweimal in Folge,
            beide Male am Leak-Druck. Deshalb nur 52 statt der frueheren 55-57. Wenn sie
            heute erneut scheitert, ist der Mechanismus als solcher zu verwerfen und
            gehoert in learnings.md.
         !! ABHAENGIGKEIT ZUR QUALITATIVEN SEITE: Die ADBE-Zeile und die qualitative
            Prognose P37 (IGV schlechter als SMH) ruhen auf derselben Software-Schwaeche.
            Zwei Treffer waeren teilweise EIN Urteil, zweimal gezaehlt.

     (F) KALIBRIERUNG: Konfidenzen 52-57, kein Wert darueber. Nach einem 50-%-Tag
         (6/12 am 25.08.) bleibt Zurueckhaltung die richtige Antwort. Die ETF-Zeilen
         erhalten wie am 25.08. leicht HOEHERE Konfidenz als die SP500-Zeile, weil ihr
         Schluss um 17:30 MESZ faellt und einen ueberwiegend beobachtbaren Tag abbildet -
         diese Begruendung hat sich gestern bewaehrt (alle vier ETF-Zeilen richtig).

     (G) ANGEWANDTES LEARNING 25.08. (1): Spreizung / Indexbewegung = 2,60 Pp / 0,32 % =
         ~8,1 fuer den 25.08. Unter der Schwelle von ~10, also Marktbewegung und nicht
         reine Rotation - die Marktrichtung ist damit grundsaetzlich verwertbar. Genutzt
         wird sie hier nur fuer SP500 und die ETFs; die sechs Einzelaktien-Zeilen haben
         je einen eigenen Mechanismus.

     (H) INTEGRITAET: 160 bestehende 1T-Zeilen unveraendert bis auf die 12 planmaessig
         aufgeloesten (Ergebnis + Ist-Kurs, sonst nichts); 63 1W-Zeilen unveraendert
         (11 davon offen, Aufloesung 28.08. durch den Samstags-Task). Nur angehaengt,
         nichts geloescht, nichts ueberschrieben, keine Reihenfolge geaendert.
-->

2026-08-27 | Opus-5 | SP500 | 1T | UP | 59 | 7675.70 | DOWN | 2026-08-27 | RICHTIG | 7730.99
2026-08-27 | Opus-5 | Vanguard FTSE All-World | 1T | UP | 68 | 166.54 | UP | 2026-08-27 | RICHTIG | 167.14
2026-08-27 | Opus-5 | Amundi Nasdaq-100 | 1T | UP | 68 | 101.92 | UP | 2026-08-27 | RICHTIG | 103.12
2026-08-27 | Opus-5 | Amundi MSCI World | 1T | UP | 66 | 159.055 | UP | 2026-08-27 | RICHTIG | 159.645
2026-08-27 | Opus-5 | HSBC MSCI EM | 1T | UP | 65 | 16.1995 | UP | 2026-08-27 | RICHTIG | 16.2235
2026-08-27 | Opus-5 | AAPL | 1T | DOWN | 54 | 313.45 | UP | 2026-08-27 | FALSCH | 314.58
2026-08-27 | Opus-5 | UNH | 1T | DOWN | 54 | 401.01 | UP | 2026-08-27 | RICHTIG | 395.05
2026-08-27 | Opus-5 | ASML | 1T | UP | 66 | 1745.64 | UP | 2026-08-27 | FALSCH | 1735.01
2026-08-27 | Opus-5 | PEP | 1T | DOWN | 57 | 142.19 | DOWN | 2026-08-27 | RICHTIG | 139.72
2026-08-27 | Opus-5 | ADBE | 1T | UP | 59 | 273.47 | DOWN | 2026-08-27 | RICHTIG | 289.15
2026-08-27 | Opus-5 | META | 1T | UP | 55 | 576.14 | UP | 2026-08-27 | FALSCH | 571.10
2026-08-27 | Opus-5 | TTWO | 1T | UP | 54 | 233.45 | UP | 2026-08-27 | FALSCH | 233.00

<!-- PROTOKOLL 27.08.2026 (1T)

     (A) AUFLOESUNG 26.08.: Alle 12 offenen 1T-Zeilen aufgeloest (nur Ergebnis + Ist-Kurs
         geaendert, sonst nichts). Tagesbilanz Berater 9/12 = 75,0 % gegen Baseline
         8/12 = 66,7 % (+8,3 Pp). Falsch: Amundi Nasdaq-100, AAPL, META.
         Laufender Stand nur 1T: 172 Zeilen, davon 164 aufgeloest (98 RICHTIG = 59,8 % /
         66 FALSCH), 8 n/v, 0 offen. Baseline 72 = 43,9 %. Vorsprung +15,9 Pp.

     (B) REFERENZKURSE:
         US-Werte = Schluss 26.08.2026 (stockanalysis.com / S&P Global Market Intelligence).
         Rueckrechnungs-Check Kurs / (1 + Tagesaenderung) = Vortagesschluss fuer ALLE sieben
         US-Zeilen bestanden (AAPL 313,45/1,0115 = 309,89 vs. 309,90; UNH 401,01/1,0111 =
         396,61 vs. 396,59 (Rundung der gemeldeten Tagesaenderung); ASML 1745,64/1,0008 = 1744,24 vs. 1744,16; PEP 142,19/0,9994 =
         142,28 vs. 142,27; ADBE 273,47/0,9984 = 273,91 vs. 273,92; META 576,14/1,0107 =
         570,04 vs. 570,05; TTWO 233,45/1,0022 = 232,94 vs. 232,93).
         SP500 = 7675,70 (FXEmpire-Marktbericht 26.08., -0,02 %); Rueckrechnung
         7675,70/0,9998 = 7677,24 gegen Referenz 7677,24 - bestanden.
         ⚠️ QUELLENKONFLIKT beim SP500-Vortagesschluss benannt, nicht aufgeloest:
         ts2.tech nennt fuer den 25.08. 7677,28, die bisher gefuehrte Reihe 7677,24.
         Differenz 0,04 Punkte = 0,0005 %, ohne Wirkung auf Richtung oder Ergebnis.
         ETFs = Xetra-Schlusspreis 26.08. direkt von der Deutschen Boerse
         ("Schlusspreis des letzten Handelstages", Abruf ueber echten Browser).
         Gegenprobe ueber zwei unabhaengige Felder derselben Seite bestanden:
         All-World 167,10 - 0,56 = 166,54; Nasdaq-100 103,28 - 1,36 = 101,92.
         Fuer HSBC MSCI EM und Amundi MSCI World lag kein Live-Preis vor, nur das Feld
         Schlusspreis - Gegenprobe dort nicht moeglich, ausdruecklich benannt.

     (C) MSCIWorld zum ZEHNTEN Mal nicht enthalten (kein frei verfuegbarer, datierter
         Indexstand). Universum sieht 13 Werte vor, erzeugt wurden 12.

     (D) RICHTUNGSVERTEILUNG: 9x UP / 3x DOWN - die einseitigste Verteilung seit dem
         16.08., und das ist ausdruecklich zu benennen (Learning 22.08. (4)).
         Ursache: Der 27.08. hat EINEN dominanten Treiber - Nvidia (Umsatz 96,2 Mrd. $,
         Q3-Guidance 108 Mrd. $) und Salesforce (bereinigtes EPS 5,90 $ gegen 3,27 $
         Konsens, FY27-Guidance angehoben) haben beide nachboerslich geliefert.
         Nasdaq-Futures +0,6 bis 0,9 %, KOSPI +1,5 %, SP500-Indikation +0,48 %,
         Nasdaq-100-Indikation +1,12 % (Deutsche Boerse, 11:20 MESZ).
         ABHAENGIGKEIT: SP500 + die vier ETF-Zeilen (5 von 12) sind faktisch EIN
         Markt-Call. ASML und ADBE haben je einen eigenen, aber gleichgerichteten Grund
         (Halbleiter-Read-Across / Software-Neubewertung). Realistisch stehen hinter den
         neun UP-Zeilen etwa vier unabhaengige Urteile. Wenn der Tag kippt, kippen sie
         gemeinsam - genau der Fehler, der am 22.08. in der 1W-Batterie 3/11 ergeben hat.

     (E) QUOTIENT VORTAG (Learning 26.08. (1)): Spreizung 26.08. = XLI +1,09 % gegen
         XLV -1,00 % = 2,09 Pp bei einer Indexbewegung von 0,02 %. Quotient rechnerisch
         ~105 - die Kennzahl ist bei einer Indexbewegung nahe null nicht sinnvoll
         interpretierbar, die Aussage bleibt aber eindeutig: der 26.08. war ein reiner
         Rotationstag ohne verwertbare Marktrichtung. Deshalb wurde die gestrige
         Marktrichtung NICHT fortgeschrieben; der heutige Markt-Call ruht auf einem
         neuen, benannten Ereignis (zwei Earnings-Beats), nicht auf gestriger Bewegung.

     (F) EINZELBEGRUENDUNGEN:
         SP500  = zwei grosse Beats nach Boersenschluss; dagegen: heisse Headline-PCE
                  (+0,2 % m/m, 3,7 % y/y, beide 0,1 Pp ueber Erwartung), 10-Jahres-Rendite
                  4,649 %, Warsh-Rede am Freitag. Nur 59, weil die Vorboerse ein schwacher
                  Praediktor ist (eigener Fehlschlag P21, 17.08.).
         ETFs   = Xetra-Schluss faellt 17:30 MESZ und bildet einen ueberwiegend
                  beobachtbaren Tag ab; All-World notiert 11:19 MESZ bei 167,10 (+0,34 %),
                  Nasdaq-100-ETF bei 103,28 (+1,33 %). Diese Begruendung war am 25. und
                  26.08. richtig (4/4 und 3/4).
         AAPL   = kein KI-Chip-Profiteur; vorboerslich 310,31 (-1,00 % um 05:26 EDT);
                  iPhone-Event 09.09. ist seit gestern bekannt und verarbeitet.
         UNH    = +1,11 % am 26.08. an einem Tag, an dem XLV -1,00 % machte, ohne eigene
                  Unternehmensmeldung. Divergenzen dieser Art geben typischerweise nach;
                  zusaetzlich sind Defensive an einem Risk-on-Tag unattraktiv.
         ASML   = direktester Read-Across auf den Nvidia-Beat; KOSPI +1,5 %,
                  Chipwerte in Asien fuehrend.
         PEP    = Basiskonsum an einem Risk-on-Tag; XLP -0,29 % am 26.08.
         ADBE   = Salesforce hat die "SaaSpocalypse"-These am eigenen Zahlenwerk
                  widerlegt (cRPO 33,5 Mrd. $, Agentforce); Adobe ist mit KGV 15,7 der
                  am staerksten disruptions-diskontierte Softwarewert im Depot.
         META   = Vergleich ueber die Kinder-/Jugendschutzklagen beseitigt einen
                  Verfahrens-Ueberhang. ⚠️ Betragskonflikt benannt: FXEmpire 16,7 Mrd. $,
                  AP/Reuters "bis zu 18 Mrd. $" (davon 5,3 Mrd. $ an Bedingungen geknuepft).
         TTWO   = "An Extended Look" startet 15:00 ET, also EINE Stunde vor dem
                  US-Schluss - die Reaktion faellt teilweise noch in den heutigen Schluss.
                  Nur 54: derselbe Mechanismus ("Vorlauf auf datierten Eigenkatalysator")
                  ist am 24. und 25.08. gescheitert und am 26.08. aufgegangen, also 1/3.

     (G) KALIBRIERUNG: Konfidenzen 54-68. Die ETF-Zeilen liegen erstmals ueber 60, weil
         ihr Schluss um 17:30 MESZ faellt und der Vormittag bereits deutlich positiv ist -
         das ist keine Prognose ueber die Zukunft, sondern ueberwiegend eine Feststellung
         ueber die Gegenwart. Kein Wert ueber 68, obwohl 75 % Tagesbilanz gestern zur
         Erhoehung verleiten wuerde (Ergebnis ist nicht Entscheidungsqualitaet).

     (H) INTEGRITAET: 172 bestehende 1T-Zeilen unveraendert bis auf die 12 planmaessig
         aufgeloesten (Ergebnis + Ist-Kurs, sonst nichts); 63 1W-Zeilen unveraendert
         (11 davon offen, Aufloesung 28.08. durch den Samstags-Task). Nur angehaengt,
         nichts geloescht, nichts ueberschrieben, keine Reihenfolge geaendert.
-->

2026-08-28 | Opus-5 | SP500 | 1T | DOWN | 54 | 7730.99 | UP | 2026-08-28 | RICHTIG | 7711.76
2026-08-28 | Opus-5 | Vanguard FTSE All-World | 1T | UP | 63 | 167.14 | UP | 2026-08-28 | RICHTIG | 168.54
2026-08-28 | Opus-5 | Amundi Nasdaq-100 | 1T | DOWN | 55 | 103.12 | UP | 2026-08-28 | FALSCH | 104.20
2026-08-28 | Opus-5 | Amundi MSCI World | 1T | UP | 62 | 159.645 | UP | 2026-08-28 | RICHTIG | 161.015
2026-08-28 | Opus-5 | HSBC MSCI EM | 1T | UP | 63 | 16.2235 | UP | 2026-08-28 | RICHTIG | 16.3225
2026-08-28 | Opus-5 | AAPL | 1T | UP | 53 | 314.58 | UP | 2026-08-28 | RICHTIG | 319.70
2026-08-28 | Opus-5 | UNH | 1T | UP | 56 | 395.05 | DOWN | 2026-08-28 | FALSCH | 392.95
2026-08-28 | Opus-5 | ASML | 1T | DOWN | 58 | 1735.01 | DOWN | 2026-08-28 | RICHTIG | 1696.16
2026-08-28 | Opus-5 | PEP | 1T | UP | 55 | 139.72 | DOWN | 2026-08-28 | RICHTIG | 141.07
2026-08-28 | Opus-5 | ADBE | 1T | DOWN | 58 | 289.15 | UP | 2026-08-28 | FALSCH | 291.52
2026-08-28 | Opus-5 | META | 1T | UP | 53 | 571.10 | DOWN | 2026-08-28 | RICHTIG | 578.02
2026-08-28 | Opus-5 | TTWO | 1T | UP | 68 | 233.00 | DOWN | 2026-08-28 | RICHTIG | 235.39

<!-- METHODIK-HINWEIS 2026-08-28 (Morgenreport, Horizont 1T)

     (A) DATENGRUNDLAGE. Referenzkurse = Schlusskurse 27.08.2026.
         US-Werte + SP500: stockanalysis.com (S&P Global Market Intelligence), jeweils
         mit Rueckrechnungs-Check Vortagesschluss x (1 + Tagesaenderung) bestanden:
         SP500  7675.70 x 1.0072 = 7730.9  gegen gemeldete 7730.99  OK
         UNH    401.01  x 0.9851 = 395.04  gegen 395.05             OK
         PEP    142.19  x 0.9826 = 139.72  gegen 139.72             OK
         ADBE   273.47  x 1.0573 = 289.14  gegen 289.15             OK
         META   576.14  x 0.9913 = 571.13  gegen 571.10             OK
         NOW    125.80  x 1.1004 = 138.43  gegen 138.43             OK (nicht im Universum,
                aber als Konfliktaufloesung geprueft, s. Punkt E)
         ETFs: Xetra-Schlusskurse in EUR aus der datierten Kurshistorie der Deutschen
         Boerse (Primaerquelle, Regel seit 25.08.). Jahr und Groessenordnung jeder
         Tabellenzeile geprueft (Learning 24.08.). Zusaetzliche Gegenprobe beim
         All-World ueber die Uebersichtsseite: aktueller Preis 167.72 minus
         "Differenz zum Vortag" 0.58 = 167.14 = Tabellenwert.
         ASML weiterhin als US-ADR in USD gefuehrt, NICHT als Amsterdamer Notierung.

     (B) MSCIWorld zum ELFTEN Mal nicht enthalten (kein frei verfuegbarer, datierter
         Schlusskurs in Primaerquellen-Qualitaet). Keine Ersatzgroesse eingesetzt.

     (C) QUOTIENT DES VORTAGS (vor dem Prognosesatz berechnet, Regel seit 26.08.):
         Sektorspreizung 27.08. = IGV +7.74 % bis XLP -1.38 % = 9.12 Pp
         Indexbewegung SP500 = +0.72 %  ->  Quotient ~12.7
         Das ist der zweithoechste Wert der Reihe (Hoechstwert 19.08.: ~27) und liegt
         ueber der 10er-Schwelle = Rotationstag.

     (D) ABER: Der 27.08. hat die Quotienten-Regel vom 26.08. WIDERLEGT bzw. praezisiert.
         Bei Quotient 12.7 waren die fuenf INDEXPRODUKT-Zeilen 5/5 richtig und die
         sieben EINZELAKTIEN-Zeilen nur 3/7. Die Regel sagte das Gegenteil voraus.
         Aufloesung: Der Quotient misst DISPERSION, nicht RICHTUNG. Bei hoher Dispersion
         verliert die Indexrichtung ihre Aussagekraft fuer EINZELWERTE - fuer Index-
         PRODUKTE bleibt sie per Konstruktion voll gueltig, weil diese der Index sind.
         Die heutige Verteilung folgt der praezisierten Fassung: der Markt-Call wird
         auf die Indexprodukte angewendet, die Einzelwerte bekommen eigene Gruende.

     (E) QUELLENKONFLIKT, benannt und ueber Rueckrechnung aufgeloest (Regel 5):
         ServiceNows Tagesveraenderung wird mit +10.04 % (stockanalysis), +8.96 %
         (tradingkey), "rund 5 %" (24/7 Wall St.) und "10 %" (Seeking Alpha) angegeben;
         Adobe mit +5.73 %, +5.14 %, +4.4 % und "3 %". Nur die erstgenannten Werte
         bestehen die Rueckrechnung gegen den Vortagesschluss. Die uebrigen sind
         Zwischenstaende, die VOR dem Schluss veroeffentlicht wurden. Merksatz fuer
         die Datendisziplin: Eine Prozentangabe in einem Nachrichtenartikel ist eine
         Momentaufnahme, solange der Artikel nicht nach dem Schluss datiert ist.

     (F) RICHTUNGSVERTEILUNG: 8x UP, 4x DOWN.
         DOWN: SP500, Amundi Nasdaq-100, ASML, ADBE.
         Begruendungen einzeln:
         SP500  = Warsh-Rede 16:00 MESZ nach heissem Juli-PCE (3.7 / 3.3 %),
                  Erhoehungswahrscheinlichkeit ~44 %; Nasdaq-Futures -0.3 % heute frueh.
                  Nur 54, weil der Ausgang einer Rede keine kalkulierbare Groesse ist
                  und der Verzicht vom 22.08. (Politik wird berichtet, nicht
                  prognostiziert) hier sinngemaess mitgilt.
         ETFs   = Xetra-Schluss faellt 17:30 MESZ, also 90 Minuten NACH Redebeginn -
                  nur ein Teil der Reaktion ist enthalten. Zusaetzlich lag der
                  US-Nachlauf heute Vormittag bereits im Kurs (All-World 167.72 um
                  10:40 = +0.35 %). Die UP-Zeilen sind daher ueberwiegend eine
                  Feststellung ueber die Gegenwart, nicht ueber die Zukunft.
                  Der Nasdaq-100 weicht bewusst ab: zinsempfindlichster Teil des Kerns,
                  Futures-Spreizung Dow +0.2 % gegen Nasdaq -0.3 %. Das ist eine
                  RELATIVE Aussage (Nasdaq schwaecher als All-World) und damit
                  unabhaengig vom Markt-Call, nicht widerspruechlich zu ihm.
         ASML   = -0.61 % bei SMH +3.10 % = 3.7 Pp Sektordivergenz, plausibel erklaert
                  durch die Zoll-Meldung vom 27.08. (100 % auf importierte Chips mit
                  Befreiung bei US-Fertigung - fuer einen niederlaendischen Ausruester
                  strukturell unguenstig). Der Mechanismus benennt eine Handlung
                  (Positionsabbau in nicht-US-Lieferanten), kein Ausbleiben.
         ADBE   = +5.73 % ohne eigene Unternehmensmeldung, allein aus Sektor-Sympathie.
                  Mechanismus = Gewinnmitnahme, also eine Handlung.
         TTWO 68 = hoechste Konfidenz des Satzes und der einzige Wert ueber 65:
                  Die freie Veroeffentlichung des "Extended Look" lag NACH dem
                  US-Schluss (21:00 ET), die Reaktion faellt vollstaendig in den
                  heutigen Handel, und sie ist bereits messbar (+1.79 % im europaeischen
                  Vormittagshandel). Auch das ist ueberwiegend Gegenwart, nicht Zukunft.

     (G) KALIBRIERUNG: 53-68. Bewusst kein Wert ueber 68, obwohl die Tagesbilanz von
         gestern (8/12 = 66.7 % gegen Baseline 50.0 %) dazu verleiten wuerde -
         Ergebnis ist nicht Entscheidungsqualitaet. Nach unten gedeckelt bei 53, weil
         der wichtigste Kursreiber des Tages (Warsh, 16:00 MESZ) zum Zeitpunkt der
         Prognose noch nicht stattgefunden hat. Learning 27.08. (2) (Ausgangswert 70)
         gilt hier NICHT: Es betrifft ausschliesslich die Bauform "Geschaeftszahl aus
         einer terminierten Veroeffentlichung", und davon ist heute keine dabei.

     (H) INTEGRITAET: 184 bestehende 1T-Zeilen unveraendert bis auf die 12 planmaessig
         aufgeloesten (nur Ergebnis + Ist-Kurs gesetzt, keine andere Spalte beruehrt,
         keine Reihenfolge geaendert); 63 1W-Zeilen vollstaendig unveraendert, davon
         11 offen - Aufloesung am 28.08. durch den Samstags-Task, nicht hier.
         Nur angehaengt, nichts geloescht, nichts ueberschrieben.
         Laufende 1T-Bilanz nach dieser Aufloesung: Berater 106/176 = 60.2 %,
         Baseline 78/176 = 44.3 %, Modell durchgehend Opus-5.
-->
2026-08-30 | Opus-5 | SP500 | 1W | UP | 52 | 7711.76 | UP | 2026-09-04 | RICHTIG | 7718.60
2026-08-30 | Opus-5 | MSCIWorld | 1W | UP | 52 | 4986.16 | UP | 2026-09-04 | FALSCH | 4981.85
2026-08-30 | Opus-5 | Vanguard FTSE All-World | 1W | UP | 53 | 168.54 | UP | 2026-09-04 | FALSCH | 167.88
2026-08-30 | Opus-5 | Amundi Nasdaq-100 | 1W | DOWN | 53 | 104.20 | UP | 2026-09-04 | RICHTIG | 103.22
2026-08-30 | Opus-5 | HSBC MSCI EM | 1W | DOWN | 55 | 16.3225 | UP | 2026-09-04 | FALSCH | 16.49
2026-08-30 | Opus-5 | Amundi MSCI World | 1W | UP | 52 | 161.015 | UP | 2026-09-04 | FALSCH | 160.045
2026-08-30 | Opus-5 | AAPL | 1W | DOWN | 53 | 319.70 | UP | 2026-09-04 | FALSCH | 319.97
2026-08-30 | Opus-5 | UNH | 1W | UP | 53 | 392.95 | UP | 2026-09-04 | RICHTIG | 397.14
2026-08-30 | Opus-5 | ASML | 1W | UP | 54 | 1696.16 | DOWN | 2026-09-04 | RICHTIG | 1714.88
2026-08-30 | Opus-5 | PEP | 1W | UP | 55 | 141.07 | DOWN | 2026-09-04 | FALSCH | 137.63
2026-08-30 | Opus-5 | ADBE | 1W | DOWN | 55 | 291.52 | UP | 2026-09-04 | RICHTIG | 266.51
2026-08-30 | Opus-5 | META | 1W | DOWN | 52 | 578.02 | UP | 2026-09-04 | FALSCH | 616.77
2026-08-30 | Opus-5 | TTWO | 1W | UP | 54 | 235.39 | DOWN | 2026-09-04 | FALSCH | 214.69

<!-- SAMSTAGS-TASK (Studiendaten 1W) 2026-08-30
     (A) AUFLOESUNG: 11 faellige 1W-Zeilen vom 22.08. (Aufloesungsdatum 28.08.,
         abgeschlossener Handelstag). Nur Ergebnis + Ist-Kurs gesetzt, keine andere
         Spalte, keine Reihenfolge, keine 1T-Zeile beruehrt.
         Ergebnis: Berater 2/11 = 18.2 %, Baseline 4/11 = 36.4 % (-18.2 Pp).
         Quellen: S&P 500 7,711.76 (Reuters, 28.08.); MSCI World 4,986.16 und
         AAPL 319.70, META 578.02 (Investing.com Schlusskurse 28.08.);
         TTWO 235.39 (28.08., 16:00 ET). Uebrige Werte aus der bereits
         primaerquellen-belegten 1T-Aufloesung des Morgenreports vom 28.08.
     (B) QUELLENKONFLIKTE (Richtung robust, Hoehe unsicher):
         PEP  141.07 vs. 140.42 (zweite Quelle) - beide DOWN ggue. 143.48.
         UNH  392.95 vs. "rund 396" (ad-hoc-news) - beide UP ggue. 390.11.
         AAPL 319.70 vs. 319.90 - beide UP ggue. 309.35.
         ADBE 291.52 vs. 289.14 - beide UP ggue. 275.30.
     (C) NEUE 1W-PROGNOSEN: 13 Zeilen, Referenz = Freitagsschluss 28.08.,
         Aufloesung 04.09. (Freitag). MSCIWorld erstmals ueberhaupt in der Batterie
         (Index-Level 4,986.16, Quelle Investing.com) - Luecke seit Studienbeginn.
         HSBC MSCI EM war am 22.08. nicht bepreist, daher kein 21.08.-Schluss
         verfuegbar: Baseline naeherungsweise aus 24.08. (15.8695) -> 28.08.
         (16.3225) = UP. Als Naeherung gekennzeichnet.
     (D) KALIBRIERUNG 52-55, KEIN Wert >= 65. Begruendung: die 1W-Ebene hat in
         zwei Wochen in Folge einen einzigen Marktcall 10-11-fach gezaehlt und
         beide Male verloren (16.08.: 3/10; 22.08.: 2/11). Diese Woche daher
         bewusst KEIN einheitlicher Marktcall: 8 von 13 Prognosen weichen von der
         Baseline ab (Nasdaq-100, HSBC EM, AAPL, ASML, PEP, ADBE, META, TTWO).
     (E) MARKTLAGE zum Referenzzeitpunkt: Warsh (Jackson Hole, 28.08.) hawkish;
         Sept-Hike-Wahrscheinlichkeit ~60 % (Vorwoche ~35 %), Fed-Funds-Futures
         implizieren 2.4 Erhoehungen/12M. US 5Y +1.96 %, 10Y 4.722 %, Dollar-Index
         99.64 (+0.55 %), Gold -3.43 %, VIX 14.43. Halbleiter schwach (NVDA -4.57 %,
         MRVL -10.28 %, ARM -6.33 %), Mega-Cap-Software/Plattform fest.
         Aufloesungstag 04.09. = US-Arbeitsmarktbericht August.
     (F) INTEGRITAET: 63 1W-Zeilen vorher + 13 neu = 76 1W-Zeilen.
         Alle 196 1T-Zeilen vollstaendig unveraendert und
         nicht angefasst - Zustaendigkeit Morgenreport. Nur angehaengt, nichts
         geloescht, nichts ueberschrieben.
-->

<!-- MORGENREPORT (Studiendaten 1T) 2026-08-31
     (A) AUFLOESUNG: KEINE. Es stand keine 1T-Zeile offen. Die 12 Zeilen vom 28.08.
         (Aufloesungsdatum 28.08.) wurden bereits am 29.08. aufgeloest; Sa 29.08. und
         So 30.08. waren keine Handelstage, es wurde keine Batterie erzeugt.
         Stand vor diesem Lauf: 196 1T-Zeilen, davon 188 mit Ergebnis
         (115 RICHTIG / 73 FALSCH), 8 n/v, 0 offen. Baseline 86 = 45.7 %.
         Berater 61.2 %, Vorsprung +15.4 Pp. Modell durchgehend Opus-5.
     (B) ⚠️ ERZEUGUNGSZEITPUNKT - WICHTIG FUER DIE AUSWERTUNG:
         Dieser Lauf fand um 10:10 ET statt, also 40 Minuten NACH der US-Eroeffnung.
         Alle frueheren Laeufe lagen VOR Handelsbeginn (z.B. 28.08. um 05:19 ET,
         29.08. um 04:03 ET). Fuer den heutigen Satz war ein Teil der Tagesbewegung
         bereits bekannt; zwoelf der dreizehn Prognosen sind daher teilweise
         Beobachtung statt Vorhersage. Die Zeilen werden trotzdem regulaer angehaengt
         (append-only, keine Ausnahmen), aber die Auswertung MUSS den
         Erzeugungszeitpunkt als Kontrollvariable fuehren, sonst wird die
         Trefferquote des Verfahrens ueberschaetzt. Empfehlung: Report kuenftig
         wieder vor 15:30 MESZ starten.
     (C) NEUE 1T-PROGNOSEN: 13 Zeilen, Referenz = Schluss 28.08.,
         Aufloesung 31.08. (heutiger US- bzw. Xetra-Schluss).
         Baseline = Richtung der letzten Tagesbewegung (27.08. -> 28.08.);
         fuer MSCIWorld aus dem Samstags-Eintrag vom 30.08. uebernommen (UP).
     (D) DATENGRUNDLAGE der Richtungen (Intraday, ~10:10 ET / 16:10 MESZ):
         ✅ S&P 500 7,673.66 (-0.49 %, CNN); ✅ TTWO 218.43 (-7.21 %, stockanalysis);
         Tracker-Kurse Finanzfluss fuer die ETFs in EUR gegen Xetra-Schluss 28.08.:
         All-World 167.28 (-0.75 %), Nasdaq-100 103.20 (-0.96 %),
         HSBC EM 16.26 (-0.38 %), Amundi MSCI World 159.92 (-0.68 %).
         US-Einzelwerte per ⚠️ EUR/USD 1.1601 zurueckgerechnet - Bewegungen unter
         ~0.3 % liegen im Umrechnungsrauschen und wurden entsprechend niedriger
         konfident gefuehrt (UNH 56, ASML 53).
     (E) ASML bewusst als EINZIGE Gegenrichtung (UP, 53): der zurueckgerechnete Wert
         (~-0.15 %) liegt im Rauschen, und der Technologiesektor ist mit ⚠️ -0.10 %
         (finviz) deutlich fester als der Gesamtmarkt. Konfidenz ehrlich knapp ueber
         Raten. Damit ist der Satz nicht vollstaendig ein einziger Marktcall -
         das gemeinsame Risiko einer Nachmittagsdrehung bleibt aber und ist benannt.
     (F) MARKTLAGE zum Referenzzeitpunkt: ✅ US-Angriff auf Larak Island (Hormus)
         am 30.08., iranische Gegenangriffe auf zwei US-Basen in Jordanien gemeldet;
         ✅ Brent 90.45 $ (+2.67 %), Hoch 91.52 $. ⚠️ US-10J 4.71 %, 2J 4.31 %,
         CME FedWatch 61.9 % fuer eine ERHOEHUNG im September (vor Warsh 35.7 %).
         ✅ VIX 15.34 (+6.31 %), Vortagesschluss 14.43. Sektoren intraday ⚠️ finviz:
         Energie +1.79 %, Kommunikationsdienste -1.76 %, Spreizung 3.55 Pp bei
         -0.49 % Index = Quotient ~7.2. ⚠️ Duenner Handel (UK-Feiertag, Monatsende).
     (G) INTEGRITAET: 196 bestehende 1T-Zeilen vollstaendig unveraendert (0 offen),
         76 1W-Zeilen vollstaendig unveraendert (13 davon offen - Aufloesung am
         04.09. durch den Samstags-Task, nicht hier). Nur angehaengt, nichts
         geloescht, nichts ueberschrieben, keine Reihenfolge geaendert.
-->
2026-08-31 | Opus-5 | SP500 | 1T | DOWN | 68 | 7711.76 | DOWN | 2026-08-31 | RICHTIG | 7686.14
2026-08-31 | Opus-5 | MSCIWorld | 1T | DOWN | 64 | 4986.16 | UP | 2026-08-31 | RICHTIG | 4967.92
2026-08-31 | Opus-5 | Vanguard FTSE All-World | 1T | DOWN | 74 | 168.54 | UP | 2026-08-31 | RICHTIG | 166.66
2026-08-31 | Opus-5 | Amundi Nasdaq-100 | 1T | DOWN | 74 | 104.20 | UP | 2026-08-31 | RICHTIG | 102.82
2026-08-31 | Opus-5 | HSBC MSCI EM | 1T | DOWN | 66 | 16.3225 | UP | 2026-08-31 | RICHTIG | 16.17
2026-08-31 | Opus-5 | Amundi MSCI World | 1T | DOWN | 73 | 161.015 | UP | 2026-08-31 | RICHTIG | 159.215
2026-08-31 | Opus-5 | AAPL | 1T | DOWN | 60 | 319.70 | UP | 2026-08-31 | RICHTIG | 316.85
2026-08-31 | Opus-5 | UNH | 1T | DOWN | 56 | 392.95 | DOWN | 2026-08-31 | RICHTIG | 389.41
2026-08-31 | Opus-5 | ASML | 1T | UP | 53 | 1696.16 | DOWN | 2026-08-31 | FALSCH | 1696.01
2026-08-31 | Opus-5 | PEP | 1T | DOWN | 58 | 141.07 | UP | 2026-08-31 | RICHTIG | 140.34
2026-08-31 | Opus-5 | ADBE | 1T | DOWN | 60 | 291.52 | UP | 2026-08-31 | FALSCH | 292.79
2026-08-31 | Opus-5 | META | 1T | DOWN | 64 | 578.02 | UP | 2026-08-31 | RICHTIG | 572.34
2026-08-31 | Opus-5 | TTWO | 1T | DOWN | 88 | 235.39 | UP | 2026-08-31 | RICHTIG | 219.70

<!-- MORGENREPORT (Studiendaten 1T) 2026-09-01
     (A) AUFLOESUNG: 13 faellige 1T-Zeilen vom 31.08. (Aufloesungsdatum 31.08.,
         abgeschlossener Handelstag). Nur Ergebnis + Ist-Kurs gesetzt, keine andere
         Spalte, keine Reihenfolge, keine 1W-Zeile beruehrt.
         Ergebnis: Berater 11/13 = 84.6 %, Baseline 4/13 = 30.8 % (+53.8 Pp).
         Falsch: ASML (UP prognostiziert, tatsaechlich -0.01 % = 15 Cent auf 1696 $)
         und ADBE (DOWN prognostiziert, tatsaechlich +0.44 %).
     (B) 🔴 DIESE 84.6 % SIND NICHT VERWERTBAR - die gestern angekuendigte
         Kontamination ist damit BELEGT. Der Satz vom 31.08. wurde um 10:10 ET
         erzeugt, also nach der US-Eroeffnung; ein Teil der Bewegung war bekannt.
         Vergleich: kontaminierter Satz 84.6 % gegen 61.2 % Durchschnitt der 188
         Zeilen davor. Der Unterschied ist die Uhrzeit, nicht die Methode.
         FUER DIE AUSWERTUNG: den Satz vom 31.08. als eigene Kategorie fuehren
         oder ausschliessen. Bereinigte Reihe (188 Zeilen): Berater 61.2 %,
         Baseline 45.7 %, Vorsprung +15.4 Pp.
         Gesamtreihe (201 Zeilen): Berater 126 = 62.7 %, Baseline 90 = 44.8 %.
     (C) QUELLEN DER AUFLOESUNGSKURSE, alle mit bestandener Rueckrechnung
         (Kurs / (1 + Tagesaenderung) = geloggter Referenzkurs vom 28.08.):
         US-Einzelwerte stockanalysis.com (31.08., Markt geschlossen):
         AAPL 316.85 (-0.89 %), UNH 389.41 (-0.90 %), ASML 1696.01 (-0.01 %),
         PEP 140.34 (-0.52 %), ADBE 292.79 (+0.44 %), META 572.34 (-0.98 %),
         TTWO 219.70 (-6.67 %).
         ETFs: Deutsche Boerse / Xetra, Feld "Schlusspreis des letzten
         Handelstages" - All-World 166.66, Amundi Nasdaq-100 102.82,
         HSBC MSCI EM 16.17, Amundi MSCI World 159.215. Diese Quelle war am
         24.-26.08. nicht lesbar; ueber den gerenderten Browserabruf mit
         abgelehntem Cookie-Dialog funktioniert sie zuverlaessig.
         SP500 7686.14 (-0.33 %, CNBC), Rueckrechnung bestanden.
         MSCIWorld 4967.92 (Investing.com, Feld "Prev. Close") - dieselbe Quelle
         wie beim Referenzkurs, damit reihenkonsistent.
     (D) NEUE 1T-PROGNOSEN: 13 Zeilen, Referenz = Schluss 31.08.,
         Aufloesung 01.09. (heutiger US- bzw. Xetra-Schluss).
         Baseline = Richtung der letzten Tagesbewegung (28.08. -> 31.08.);
         alle DOWN ausser ADBE (UP).
     (E) ✅ ERZEUGUNGSZEITPUNKT: 01.09., 11:30 MESZ = 05:30 ET, VOR der
         US-Eroeffnung. Damit ist dieser Satz mit allen Saetzen ausser dem vom
         31.08. vergleichbar. Keine Intraday-Information aus dem US-Handel.
         Europaeische Vormittagskurse waren bekannt und sind in die
         Xetra-bezogenen Prognosen eingeflossen - das war bei allen frueheren
         Saetzen ebenso.
     (F) KALIBRIERUNG 54-68, kein Wert >= 70. ZEHN DOWN, DREI UP - bewusst KEIN
         einheitlicher Marktcall (die 1W-Ebene ist am 22. und 28.08. zweimal daran
         gescheitert, einen einzigen Call elffach zu zaehlen). Die drei
         Gegenrichtungen sind einzeln begruendet:
         HSBC MSCI EM (UP 55): notiert heute Vormittag +0.25 % ueber dem
           Xetra-Schluss, und Asiens Sitzung ist zum Xetra-Schluss bereits gelaufen.
         UNH (UP 54): kuerzeste Cashflow-Duration im Feld, in einem Zinsschock
           relativ beguenstigt; heute frueh unveraendert.
         TTWO (UP 56): nach -6.67 % ohne neue Sachlage; Analystenlage unveraendert
           bullish, kein Hinweis auf eine vollstaendige spielbare Kopie.
     (G) MARKTLAGE zum Referenzzeitpunkt: ✅ Reuters 01.09. - globaler
         Anleihe-Ausverkauf. US 10J 4.78 % (hoechster Stand seit Anfang 2025,
         Widerstand 4.75 % gebrochen), JGB 10J 3.00 % (erstmals seit 1996),
         FR/DE-Renditen auf 15-Jahres-Hochs. Brent ueber 91 $, europaeischer
         Gaspreis 3.5-Jahres-Hoch. Hang Seng -1 %, Nikkei 225 -1.23 %,
         DAX -0.93 %, EURO STOXX 50 -0.67 %, Gold -1.70 % (Deutsche Boerse,
         11:09 MESZ). ✅ VIX Schluss 31.08. 14.92, heute frueh 15.92 (+6.70 %).
         ⚠️ EUR/USD Quellenkonflikt: 1.1596 (Deutsche Boerse) vs. 1.1619 (Reuters).
         Heute: Eurostat-Schnellschaetzung Eurozone-Inflation. Freitag 04.09.:
         US-Arbeitsmarktbericht.
     (H) INTEGRITAET: 209 bestehende 1T-Zeilen unveraendert bis auf die 13
         planmaessig aufgeloesten (maschinell geprueft: 0 Zeilen mit Aenderungen
         ausserhalb der Spalten Ergebnis und Ist-Kurs, Zeilenzahl unveraendert);
         76 1W-Zeilen vollstaendig unveraendert, davon 13 offen - Aufloesung am
         04.09. durch den Samstags-Task, nicht hier.
         Nur angehaengt, nichts geloescht, nichts ueberschrieben.
-->
2026-09-01 | Opus-5 | SP500 | 1T | DOWN | 60 | 7686.14 | DOWN | 2026-09-01 | RICHTIG | 7631.47 
2026-09-01 | Opus-5 | MSCIWorld | 1T | DOWN | 60 | 4967.92 | DOWN | 2026-09-01 | RICHTIG | 4916.10 
2026-09-01 | Opus-5 | Vanguard FTSE All-World | 1T | DOWN | 58 | 166.66 | DOWN | 2026-09-01 | RICHTIG | 166.54 
2026-09-01 | Opus-5 | Amundi Nasdaq-100 | 1T | DOWN | 65 | 102.82 | DOWN | 2026-09-01 | RICHTIG | 102.48 
2026-09-01 | Opus-5 | HSBC MSCI EM | 1T | UP | 55 | 16.17 | DOWN | 2026-09-01 | RICHTIG | 16.27 
2026-09-01 | Opus-5 | Amundi MSCI World | 1T | DOWN | 58 | 159.215 | DOWN | 2026-09-01 | RICHTIG | 158.96 
2026-09-01 | Opus-5 | AAPL | 1T | DOWN | 55 | 316.85 | DOWN | 2026-09-01 | FALSCH | 325.13 
2026-09-01 | Opus-5 | UNH | 1T | UP | 54 | 389.41 | DOWN | 2026-09-01 | RICHTIG | 396.30 
2026-09-01 | Opus-5 | ASML | 1T | DOWN | 60 | 1696.01 | DOWN | 2026-09-01 | RICHTIG | 1665.14 
2026-09-01 | Opus-5 | PEP | 1T | DOWN | 54 | 140.34 | DOWN | 2026-09-01 | RICHTIG | 139.79 
2026-09-01 | Opus-5 | ADBE | 1T | DOWN | 60 | 292.79 | UP | 2026-09-01 | RICHTIG | 286.08 
2026-09-01 | Opus-5 | META | 1T | DOWN | 60 | 572.34 | DOWN | 2026-09-01 | FALSCH | 578.54 
2026-09-01 | Opus-5 | TTWO | 1T | UP | 56 | 219.70 | DOWN | 2026-09-01 | FALSCH | 216.68 

<!--
LAUF 02.09.2026 (Mittwoch) - Morgenreport, erzeugt 06:45 ET (vor US-Eroeffnung).
  (A) AUFLOESUNG: 13 1T-Zeilen vom 01.09. aufgeloest. Berater 10/13 = 76,9 %,
      Baseline 8/13 = 61,5 %. Falsch: AAPL (DOWN prognostiziert, tatsaechlich
      +2,61 %), META (DOWN, tatsaechlich +1,08 %), TTWO (UP, tatsaechlich -1,37 %).
      Alle drei Fehler sind Einzelaktien; Indizes/ETFs 6/6.
  (B) QUELLEN: US-Werte und Sektor-ETFs stockanalysis.com (Feld "cl" = Vortagesschluss
      stimmte bei allen 13 exakt mit dem Referenzkurs ueberein = Rueckrechnungs-Check
      bestanden). Xetra-Schluesse der vier ETFs von justETF (Feld previousQuote,
      previousQuoteDate 2026-09-01, quoteTradingVenue XETRA). SP500 aus dem
      Reuters-Marktbericht (7631.47, -54.67 Pkt, -0.71 %). MSCIWorld von boerse.de
      (Feld Vortageskurs 4916.10, Serie XC0009692739 - dieselbe Serie wie die Referenz).
  (C) FIRECRAWL-AUSFALL: Der primaere Firecrawl-Zugang meldete "account has been
      banned"; Portfolio- und Kursabruf liefen ueber den Browser. Datenqualitaet
      dadurch nicht schlechter (Primaerquellen direkt), aber der Weg war anders.
  (D) DEPOT-STRUKTURBRUCH (fuer die Auswertung irrelevant, fuer die Akte wichtig):
      Amundi MSCI World ist aus dem Depot verschwunden (Verkauf synchronisiert),
      Gesamtvermoegen -1687,81 EUR bei nur -0,3 % Marktbewegung. Das STUDIEN-UNIVERSUM
      bleibt unveraendert - Amundi MSCI World wird weiter prognostiziert
      (Survivorship-Bias-Regel).
  (E) MARKTLAGE zum Referenzzeitpunkt: US 10J bis 4,80 % (hoechster Stand seit
      Januar 2025), Bund 10J ~3,36 % (15-Jahres-Hoch), JGB 10J 3,00 %. Brent am
      Morgen des 02.09. bis 96,50 $. Eurozone-Inflation August 3,3 % (Eurostat-
      Schnellschaetzung, nach 2,9 % im Juli). Fed-Erhoehungserwartung September
      68,2 % (CME FedWatch via Reuters). Marktbreite 01.09. schwach: NYSE 2,8:1
      Verlierer, 410 neue Tiefs gegen 143 Hochs. Sektoren: XLE +1,27 %, XLU +0,78 %,
      XLV +0,66 %, XLP +0,32 % gegen IGV -3,46 %, SMH -2,05 %, XLY -1,72 %.
      VIX-Schluss 01.09. nicht beschaffbar (31.08.: 14,92).
  (F) KALIBRIERUNG: Konfidenzen 53-68. Einzelaktien bewusst 4 Punkte niedriger als
      Indizes/ETFs angesetzt (Learning 02.09. (3): am 01.09. Indizes/ETFs 6/6,
      Einzelaktien 4/7 bei gleicher Konfidenzspanne). Zwei UP (UNH, PEP), elf DOWN.
  (G) SAUBERKEIT: Erzeugung 06:45 ET - fuer die sieben US-Aktien vor Handelsbeginn
      (echte Prognose). Fuer die vier ETFs und zwei Indizes war der europaeische
      Handel bereits offen; diese sechs Zeilen sind teilweise Beobachtung. Gilt fuer
      alle bisherigen Vormittagslaeufe gleichermassen - Auswertung sollte US-Aktien
      und Europa-Werte getrennt ausweisen.
  (H) INTEGRITAET: 222 bestehende 1T-Zeilen unveraendert bis auf die 13 planmaessig
      aufgeloesten (nur Spalten Ergebnis und Ist-Kurs geaendert, Zeilenzahl und
      Reihenfolge unveraendert). 76 1W-Zeilen vollstaendig unangetastet, davon 13
      offen - Aufloesung am 05.09. durch den Samstags-Task, nicht hier.
      Nur angehaengt, nichts geloescht, nichts ueberschrieben.
-->
2026-09-02 | Opus-5 | SP500 | 1T | DOWN | 58 | 7631.47 | DOWN | 2026-09-02 | FALSCH | 7666.60 
2026-09-02 | Opus-5 | MSCIWorld | 1T | DOWN | 62 | 4916.10 | DOWN | 2026-09-02 | FALSCH | 4944.04 
2026-09-02 | Opus-5 | Vanguard FTSE All-World | 1T | DOWN | 66 | 166.54 | DOWN | 2026-09-02 | FALSCH | 166.83 
2026-09-02 | Opus-5 | Amundi Nasdaq-100 | 1T | DOWN | 66 | 102.48 | DOWN | 2026-09-02 | RICHTIG | 102.34 
2026-09-02 | Opus-5 | HSBC MSCI EM | 1T | DOWN | 68 | 16.27 | UP | 2026-09-02 | RICHTIG | 16.22 
2026-09-02 | Opus-5 | Amundi MSCI World | 1T | DOWN | 65 | 158.96 | DOWN | 2026-09-02 | FALSCH | 159.31 
2026-09-02 | Opus-5 | AAPL | 1T | DOWN | 56 | 325.13 | UP | 2026-09-02 | RICHTIG | 324.96 
2026-09-02 | Opus-5 | UNH | 1T | UP | 55 | 396.30 | UP | 2026-09-02 | RICHTIG | 399.66 
2026-09-02 | Opus-5 | ASML | 1T | DOWN | 57 | 1665.14 | DOWN | 2026-09-02 | FALSCH | 1682.30 
2026-09-02 | Opus-5 | PEP | 1T | UP | 53 | 139.79 | DOWN | 2026-09-02 | RICHTIG | 140.52 
2026-09-02 | Opus-5 | ADBE | 1T | DOWN | 57 | 286.08 | DOWN | 2026-09-02 | RICHTIG | 279.79 
2026-09-02 | Opus-5 | META | 1T | DOWN | 55 | 578.54 | UP | 2026-09-02 | FALSCH | 592.85 
2026-09-02 | Opus-5 | TTWO | 1T | DOWN | 54 | 216.68 | DOWN | 2026-09-02 | RICHTIG | 216.14 

<!--
LAUF 03.09.2026 (Donnerstag) - Morgenreport, erzeugt 04:40 ET (vor US-Eroeffnung).
  (A) AUFLOESUNG: 13 1T-Zeilen vom 02.09. aufgeloest. Berater 7/13 = 53,8 %,
      Baseline 5/13 = 38,5 %. SCHLECHTESTER SATZ SEIT WOCHEN.
      Falsch: SP500, MSCIWorld, Vanguard All-World, Amundi MSCI World, ASML, META -
      ALLE SECHS in dieselbe Richtung (DOWN prognostiziert, Markt gestiegen).
  (B) URSACHENANALYSE (fuer die Auswertung wichtig): Der Satz vom 02.09. enthielt
      11 von 13 DOWN-Prognosen. Das war keine Sammlung von 13 Einschaetzungen,
      sondern EINE Makro-Wette in 13 Zeilen. Als die Makro-Lage drehte (ADP-Miss
      38k gegen 48k erwartet, Trump "will not last long" zu Iran, fallende Renditen),
      fiel der halbe Satz gemeinsam. Die drei Zeilen GEGEN die Marktrichtung
      (HSBC EM DOWN, UNH UP, PEP UP) waren dagegen ALLE DREI richtig.
      Kontrast am selben Tag: die qualitativen Prognosen mit Kohaerenz-Check
      erreichten 3/3, die Batterie ohne Kohaerenz-Check 7/13.
      -> Learnings 03.09. (1) und (2), ab heute umgesetzt.
  (C) GEGENMASSNAHME AB HEUTE: Richtungsverteilung vor dem Anhaengen gezaehlt.
      Heute 8 UP / 5 DOWN (gestern 11 DOWN / 2 UP) - nicht kuenstlich
      ausbalanciert, sondern der gedrehten Datenlage folgend. Konfidenzen 52-62,
      niedriger als gestern, weil zwei terminierte Ereignisse im Prognosefenster
      liegen (30-jaehrige JGB-Auktion, Waller-Interview 20:30 MESZ).
  (D) QUELLEN: US-Werte und Sektor-ETFs stockanalysis.com (Feld "cl" stimmte bei
      allen 13 exakt mit dem Referenzkurs ueberein = Rueckrechnung bestanden).
      Xetra-Schluesse der vier ETFs von justETF (previousQuote, previousQuoteDate
      2026-09-02, quoteTradingVenue XETRA). SP500 7666.60 (+35.13 Pkt, +0,46 %)
      aus ts2.tech, gegengeprueft mit AP/Reuters (+0,4 bis +0,5 %) und SPY +0,44 %.
      MSCIWorld 4944.04 von boerse.de (Feld Vortageskurs, Serie XC0009692739).
  (E) MARKTLAGE zum Referenzzeitpunkt: Dreitaegige Verlustserie beendet. Dow +0,56 %,
      SP500 +0,46 %, Nasdaq +0,45 %, Russell 2000 staerker als der SP500.
      ADP August +38.000 (erwartet 48.000, niedrigster Wert seit Januar).
      US 10J intraday 4,818 % (hoechster Stand seit Ende 2023), Schluss dann tiefer;
      QUELLENKONFLIKT offen: PANews "etwa 4,78 %" vs. CNBC-Rueckrechnung 4,794 %.
      US 30J ~5,27 %, Japan 30J 4,155 %. Brent unter 95 $ nach Trumps
      "will not last long"; US-Rohoelbestaende -4,5 Mio. Barrel, Raffinerie 98 %.
      Gold ueber 4.400 $, Yen +1,2 %, Dollar-Index ~99,5.
      SEKTOREN: XLB +1,69 / XLC +1,39 / SMH +0,96 / XLF +0,80 / XLV +0,75 /
      XLE +0,51 / XLP +0,33 / XLU +0,26 / XLY +0,24 / XLI +0,03 / XLK -0,02 /
      XLRE -0,70 / IGV -2,60. Software fiel ALLEIN - Google (Gemini 3.8 Flash +
      Cybersecurity-Modell) und Meta (Muse Spark 1.3) veroeffentlichten Modelle;
      Palo Alto -9,28 % und MongoDB -13 % TROTZ guter Zahlen.
      VIX-Schluss 02.09. nicht beschaffbar (letzter belegter Wert 14,92 vom 31.08.).
  (F) SAUBERKEIT: Erzeugung 04:40 ET - fuer die sieben US-Aktien vor Handelsbeginn
      (echte Prognose). Fuer die vier ETFs und zwei Indizes war der europaeische
      Handel bereits offen; diese sechs Zeilen sind teilweise Beobachtung.
  (G) INTEGRITAET: 235 bestehende 1T-Zeilen unveraendert bis auf die 13 planmaessig
      aufgeloesten (nur Spalten Ergebnis und Ist-Kurs geaendert, Zeilenzahl und
      Reihenfolge unveraendert). 76 1W-Zeilen unangetastet, davon 13 offen -
      Aufloesung am 05.09. durch den Samstags-Task, nicht hier.
-->
2026-09-03 | Opus-5 | SP500 | 1T | UP | 55 | 7666.60 | UP | 2026-09-03 | RICHTIG | 7753.65 
2026-09-03 | Opus-5 | MSCIWorld | 1T | UP | 60 | 4944.04 | UP | 2026-09-03 | RICHTIG | 5001.81 
2026-09-03 | Opus-5 | Vanguard FTSE All-World | 1T | UP | 62 | 166.83 | UP | 2026-09-03 | RICHTIG | 168.00 
2026-09-03 | Opus-5 | Amundi Nasdaq-100 | 1T | UP | 62 | 102.34 | DOWN | 2026-09-03 | RICHTIG | 103.28 
2026-09-03 | Opus-5 | HSBC MSCI EM | 1T | DOWN | 60 | 16.22 | DOWN | 2026-09-03 | FALSCH | 16.24 
2026-09-03 | Opus-5 | Amundi MSCI World | 1T | UP | 61 | 159.31 | UP | 2026-09-03 | RICHTIG | 160.56 
2026-09-03 | Opus-5 | AAPL | 1T | UP | 53 | 324.96 | DOWN | 2026-09-03 | RICHTIG | 328.21 
2026-09-03 | Opus-5 | UNH | 1T | UP | 52 | 399.66 | UP | 2026-09-03 | RICHTIG | 400.94 
2026-09-03 | Opus-5 | ASML | 1T | UP | 55 | 1682.30 | UP | 2026-09-03 | FALSCH | 1646.19 
2026-09-03 | Opus-5 | PEP | 1T | DOWN | 52 | 140.52 | UP | 2026-09-03 | RICHTIG | 140.02 
2026-09-03 | Opus-5 | ADBE | 1T | DOWN | 58 | 279.79 | DOWN | 2026-09-03 | FALSCH | 285.75 
2026-09-03 | Opus-5 | META | 1T | DOWN | 53 | 592.85 | UP | 2026-09-03 | FALSCH | 610.68 
2026-09-03 | Opus-5 | TTWO | 1T | DOWN | 52 | 216.14 | DOWN | 2026-09-03 | RICHTIG | 214.13 

<!--
LAUF 04.09.2026 (Freitag) - Morgenreport, erzeugt 07:35 ET.
  (A) AUFLOESUNG: 13 1T-Zeilen vom 03.09. Berater 9/13 = 69,2 %, Baseline 7/13 = 53,8 %.
      Falsch: HSBC EM (DOWN, tatsaechlich +0,12 %), ASML (UP, tatsaechlich -2,15 %),
      ADBE (DOWN, +2,13 %), META (DOWN, +3,01 %).
      DEUTLICHE VERBESSERUNG nach 53,8 % am Vortag. Die am 03.09. eingefuehrte
      Zaehlung der Richtungsverteilung (8 UP / 5 DOWN statt 11:2) hat gewirkt:
      alle Aggregat-Zeilen (Indizes + ETFs) richtig ausser HSBC EM; alle vier
      Fehler bis auf HSBC EM bei Einzelaktien - drittes Mal in Folge dasselbe Muster.
  (B) MARKTEREIGNIS: Fed-Gouverneur Waller deutete am Abend des 03.09. eine
      ZINSPAUSE im September an. Dow +639,18 Pkt (+1,20 %), SP500 +87,05 (+1,14 %),
      Nasdaq Composite +1,54 %, US-10J von 4,796 % auf 4,756 % (-4 Bp).
      MSCI World erstmals ueber 5.000 (5.001,81).
      SEKTOREN: IGV +3,41 / XLF +1,56 / XLY +1,39 / XLK +1,29 / XLRE +1,19 /
      XLI +1,03 / XLC +0,85 / XLU +0,84 / SMH +0,39 / XLV +0,18 / XLP -0,32 /
      XLB -0,62 / XLE -0,74. SOFTWARE war der staerkste Bereich - exakte Umkehrung
      des 02.09., als es der schwaechste war. Zscaler nach Zahlen +2,94 %.
      -> Starke Evidenz, dass der Software-Absturz vom 02.09. ZINSGETRIEBEN war
      und nicht KI-getrieben. Die Modellveroeffentlichungen (Google/Meta) waren
      der Anlass, nicht die Ursache. Diese Diagnose war am 03.09. im Kohaerenz-Check
      der qualitativen Prognosen VORAB definiert worden.
  (C) QUELLENKONFLIKT SP500 offen benannt: ts2.tech 7753.65 (+87,05 Pkt, +1,14 %)
      gegen Benzinga 7740.14 (+0,96 %). Beide intern schluessig, Differenz 13,5 Pkt.
      Eingetragen wurde 7753.65, weil die Punktangabe exakt auf den Vortagesschluss
      zurueckrechnet (7666.60 + 87.05) und SPY mit +1,05 % naeher daran liegt.
      Fuer die Richtungsprognose ohne Folge (beide Quellen zeigen UP).
  (D) HEUTIGER SATZ: 7 UP / 6 DOWN - ausgewogenster Satz der Woche, sachlich
      begruendet: der US-Arbeitsmarktbericht um 14:30 MESZ liegt VOLLSTAENDIG im
      Prognosefenster und kann den Tag in beide Richtungen entscheiden.
      Konfidenzen 51-58, die NIEDRIGSTEN der Woche. Bei einem terminierten Ereignis
      dieser Groesse waere alles ueber 60 unehrlich.
  (E) DEPOT-EREIGNIS (fuer die Akte, ohne Wirkung auf das Studien-Universum):
      Boston Scientific - am 02.09. von Meister gekauft - fiel am 03.09. um 2,94 %.
      Ursache: Cyberangriff seit 25.08. (SEC-8-K 26.08.) plus bereits Ende Juli
      gesenkte Jahresprognose (5-6 % organisch, 3,28-3,32 $ EPS). BEIDES war beim
      Vorschlag am 02.09. nicht recherchiert - Recherchefehler, dokumentiert in
      learnings.md (04.09. (2) und (3)). BSX ist NICHT im Studien-Universum und
      beeinflusst die Batterie nicht.
  (F) SAUBERKEIT: Erzeugung 07:35 ET - vor der US-Eroeffnung UND vor dem
      Arbeitsmarktbericht, fuer alle 13 Zeilen echte Prognose. Fuer die vier ETFs
      und zwei Indizes lief der europaeische Handel bereits (teilweise Beobachtung).
  (G) INTEGRITAET: 248 bestehende 1T-Zeilen unveraendert bis auf die 13 planmaessig
      aufgeloesten (nur Ergebnis und Ist-Kurs). 76 1W-Zeilen unangetastet, davon 13
      offen - Aufloesung am 05.09. durch den Samstags-Task.
-->
2026-09-04 | Opus-5 | SP500 | 1T | UP | 53 | 7753.65 | UP | 2026-09-04 | FALSCH | 7718.41
2026-09-04 | Opus-5 | MSCIWorld | 1T | UP | 54 | 5001.81 | UP | 2026-09-04 | FALSCH | 4986.90
2026-09-04 | Opus-5 | Vanguard FTSE All-World | 1T | UP | 56 | 168.00 | UP | 2026-09-04 | FALSCH | 167.86
2026-09-04 | Opus-5 | Amundi Nasdaq-100 | 1T | UP | 56 | 103.28 | UP | 2026-09-04 | FALSCH | 103.22
2026-09-04 | Opus-5 | HSBC MSCI EM | 1T | UP | 58 | 16.24 | UP | 2026-09-04 | RICHTIG | 16.51
2026-09-04 | Opus-5 | Amundi MSCI World | 1T | UP | 55 | 160.56 | UP | 2026-09-04 | FALSCH | 160.09
2026-09-04 | Opus-5 | AAPL | 1T | DOWN | 51 | 328.21 | UP | 2026-09-04 | RICHTIG | 319.97
2026-09-04 | Opus-5 | UNH | 1T | UP | 52 | 400.94 | UP | 2026-09-04 | FALSCH | 397.14
2026-09-04 | Opus-5 | ASML | 1T | UP | 56 | 1646.19 | DOWN | 2026-09-04 | RICHTIG | 1714.88
2026-09-04 | Opus-5 | PEP | 1T | DOWN | 52 | 140.02 | DOWN | 2026-09-04 | RICHTIG | 137.63
2026-09-04 | Opus-5 | ADBE | 1T | DOWN | 53 | 285.75 | UP | 2026-09-04 | RICHTIG | 266.51
2026-09-04 | Opus-5 | META | 1T | DOWN | 54 | 610.68 | UP | 2026-09-04 | FALSCH | 616.77
2026-09-04 | Opus-5 | TTWO | 1T | DOWN | 52 | 214.13 | DOWN | 2026-09-04 | FALSCH | 214.69

<!-- SAMSTAGS-TASK 05./06.09.2026 - WOCHENPROGNOSEN (Horizont 1W), erzeugt 06.09. nach Freitagsschluss
     Referenzkurs = Schlusspreis Fr 04.09.2026. Aufloesungsdatum = Fr 11.09.2026.
     Baseline = Richtung der Vorwoche (Schluss 28.08. -> Schluss 04.09.), aus den
     Referenzkursen des 30.08.-Satzes zurueckgerechnet, also selbst primaerquellenbelegt.

  (A) QUELLEN (alle nach Schluss datiert, Rueckrechnungs-Check bestanden):
      Einzelaktien + ASML-ADR: stockanalysis.com Kurshistorie, Stand 04.09. 16:00 ET.
        AAPL 319.97 (-2.51 %), UNH 397.14 (-0.95 %), ASML 1714.88 (+4.17 %),
        PEP 137.63 (-0.66 %), ADBE 266.51 (-6.73 %), META 616.77 (+1.00 %),
        TTWO 214.69 (+0.26 %). Alle sieben rechnen exakt gegen den 03.09.-Schluss zurueck.
        ASML zusaetzlich gegen EODData (NASDAQ ADR) bestaetigt: Close 1,715.
      ETFs: boerse-frankfurt.de / live.deutsche-boerse.com, regulaerer Xetra-Handel
        bis 17:30 MESZ. All-World 167.88, Amundi Nasdaq-100 103.22 EUR (17:36),
        HSBC MSCI EM 16.49, Amundi MSCI World 160.045.
      MSCIWorld: boerse.de (XC0009692739), 4981.85 (-0.40 %) - identische Quelle wie
        die Vorwoche, Rueckrechnung 5001.81 - 19.96 = 4981.85 exakt.
      SP500: 7718.60 (-0.38 % / -29.35 Pkt, Quotemedia via Investrade-Closing-Recap).

  (B) QUELLENKONFLIKT, benannt (Regel 5): Fuer den SP500 nennen TheStreet und der
      Investrade-Recap -0.38 %, der 24/7-Wall-St.-Schlussticker dagegen 7,708.20 / -0.45 %.
      Gegen den in der Batterie gefuehrten 03.09.-Schluss (7753.65) passt die
      PROZENTangabe -0.45 %, gegen den Absolutwert 7718.60 passt -0.38 %; die
      Differenz betraegt rund 6 Punkte = 0.08 %. Fuer die Auflagen dieser Woche ist
      das folgenlos: der Vergleichswert ist der 28.08.-Schluss 7711.76, und 7718.60
      liegt darueber - die RICHTUNG ist unter allen drei Quellen identisch (UP).
      Unabhaengige Bestaetigung: Der Investrade-Recap nennt fuer die Woche
      "S&P 500 climbed 0.1 %", was 7711.76 -> 7718.60 (+0.09 %) genau trifft.
      Die HOEHE des SP500-Standes wird als unsicher markiert, die Richtung als robust.

  (C) MARKTLAGE ZUM PROGNOSEZEITPUNKT (Fakten, nicht Interpretation):
      - Mo 07.09. ist Labor Day, US-Boersen geschlossen. Das Prognosefenster hat nur
        VIER US-Handelstage (08.-11.09.), fuer die ETFs fuenf Xetra-Tage.
      - August-Arbeitsmarkt 162k gegen 55k Konsens, Revisionen +55k; Zinserhoehungs-
        wahrscheinlichkeit fuer den 15./16.09. laut Terminmarkt von ~55 % auf ~65 %.
        2-jaehrige US-Rendite 4.374 %, 5-jaehrige 4.545 % - beide 52-Wochen-Hoch.
      - Terminierte Ereignisse IM Fenster: EZB-Sitzung Do 10.09. (laut BofA/Bloomberg-
        Pricing 99 % Erhoehung), US-PPI Do 10.09., US-CPI Fr 11.09. 08:30 ET.
        Der CPI liegt damit AM Aufloesungstag und wirkt sowohl auf den US-Schluss
        als auch - drei Stunden spaeter - auf den Xetra-Schluss.
      - Apple-Event Di 09.09. (erster Auftritt von John Ternus als CEO).
      - Adobe berichtet Do 10.09. nach Schluss (Guidance 6.67-6.72 Mrd. $ Umsatz,
        6.05-6.10 $ bereinigter EPS); Reaktion faellt auf den 11.09., also ins Fenster.
      - Oel +8 % auf Wochensicht (WTI 91.48), US-Diesel auf Rekordhoch.
      - VIX seit 25 Handelstagen zwischen 14 und 17.

  (D) KOHAERENZ-CHECK NACH DER NEUEN REGEL (Learning 05.09. (2)):
      Aggregat-Gruppe (2 Indizes + 4 ETFs) getrennt geprueft: 5x DOWN, 1x UP.
      KLUMPENRISIKO WIRD AUSDRUECKLICH AUSGEWIESEN: Die fuenf DOWN-Zeilen haengen an
      EINEM Treiber (Zinserhoehungs-Repricing, verstaerkt durch PPI/CPI im Fenster).
      Faellt der CPI mild aus, kippen sie gemeinsam - dann ist der Satz strukturell
      derselbe Fehler wie am 30.08., nur mit umgekehrtem Vorzeichen.
      Bewusst gegenlaeufig gebaut: HSBC MSCI EM (UP). Begruendung: Es ist der einzige
      Aggregatwert mit eigenem Nachfragetreiber, er lief in der Vorwoche als einziger
      gegen die anderen fuenf (+1.03 % in EUR), und genau dort ist die DOWN-Prognose
      vom 30.08. gescheitert. Die 52 sind ehrlich: gegen ihn steht ein festerer Dollar.
      Gesamtverteilung 5x UP / 8x DOWN. Das ist der erste 1W-Satz der Studie mit
      DOWN-Uebergewicht - relevant, weil die bisherigen 75 aufgeloesten 1W-Zeilen
      einen UP-Ueberhang von 46:29 haben (Learning-Kandidat, siehe Report).

  (E) KALIBRIERUNG: Spanne 52-57. Obergrenze bewusst NICHT bei 70 (Learning 27.08. (2),
      Bauform "Geschaeftszahl aus terminierter Veroeffentlichung") fuer ADBE: Der
      Anker gilt fuer die Konfidenz, die eine terminierte Zahl TRAGEN KANN, aber nur
      wenn das Richtungsargument selbst stark ist. Bei Adobe ist es symmetrisch
      (gedrueckte Erwartung und -6.73 % vor dem Termin gegen einen seit zwei Jahren
      intakten Abwaertstrend), deshalb 57 statt 70.
      Untergrenze 52 fuer die Zeilen ohne eigenen Treiber. Bilanz-Begruendung:
      Der Berater liegt ueber alle 75 aufgeloesten 1W-Zeilen bei 56.0 % gegen eine
      Baseline von 54.7 % - ein Vorsprung von einer einzigen Zeile. Konfidenzen
      oberhalb der 60er waeren durch nichts gedeckt.

  (F) SAUBERKEIT: Erzeugung am Wochenende bei geschlossenen Maerkten. Kein
      Intraday-Leck, kein laufender Kurs - fuer alle 13 Zeilen echte Prognose ueber
      einen vollstaendig ungehandelten Zeitraum. Das ist der methodische Vorteil
      der Wochenzeilen gegenueber den Tageszeilen.

  (G) EX-DIVIDENDEN-PRUEFUNG (Learning 05.09. (3), erstmals VOR dem Loggen angewandt):
      PepsiCo ist am 04.09. ex Dividende gegangen (1.48 $) - die mechanische
      Abwaertskomponente liegt damit VOR dem Referenzkurs und nicht im Fenster.
      Fuer die uebrigen zwoelf Werte habe ich im Fenster 08.-11.09. keinen
      Ex-Termin gefunden; das ist eine Aussage ueber meine Suche, nicht ueber die
      Welt (Learning 06.09. (2)).

  (H) INTEGRITAET: 13 1W-Zeilen des 30.08.-Satzes aufgeloest, dabei ausschliesslich
      die Spalten Ergebnis und Ist-Kurs gesetzt - Zeilendiff geprueft, keine andere
      Spalte, keine Reihenfolge, keine 1T-Zeile beruehrt. Die 13 1T-Zeilen vom 04.09.
      waren beim Lesen bereits durch den Morgenreport aufgeloest und blieben
      unveraendert. Danach nur angehaengt.
      Laufende 1W-Bilanz nach dieser Aufloesung: Berater 42/75 = 56.0 %,
      Baseline 41/75 = 54.7 %, eine Zeile "n/v" (HSBC MSCI EM, Aufl. 21.08.),
      Modell durchgehend Opus-5.
-->
2026-09-06 | Opus-5 | SP500 | 1W | DOWN | 55 | 7718.60 | UP | 2026-09-11 | RICHTIG | 7656.98
2026-09-06 | Opus-5 | MSCIWorld | 1W | DOWN | 54 | 4981.85 | DOWN | 2026-09-11 | RICHTIG | 4937.32
2026-09-06 | Opus-5 | Vanguard FTSE All-World | 1W | DOWN | 53 | 167.88 | DOWN | 2026-09-11 | RICHTIG | 166.86
2026-09-06 | Opus-5 | Amundi Nasdaq-100 | 1W | DOWN | 55 | 103.22 | DOWN | 2026-09-11 | FALSCH | 103.38
2026-09-06 | Opus-5 | HSBC MSCI EM | 1W | UP | 52 | 16.49 | UP | 2026-09-11 | FALSCH | 16.4395
2026-09-06 | Opus-5 | Amundi MSCI World | 1W | DOWN | 53 | 160.045 | DOWN | 2026-09-11 | RICHTIG | 159.06
2026-09-06 | Opus-5 | AAPL | 1W | DOWN | 53 | 319.97 | UP | 2026-09-11 | FALSCH | 332.27
2026-09-06 | Opus-5 | UNH | 1W | DOWN | 52 | 397.14 | UP | 2026-09-11 | RICHTIG | 379.09
2026-09-06 | Opus-5 | ASML | 1W | UP | 55 | 1714.88 | UP | 2026-09-11 | FALSCH | 1698.30
2026-09-06 | Opus-5 | PEP | 1W | UP | 52 | 137.63 | DOWN | 2026-09-11 | FALSCH | 136.32
2026-09-06 | Opus-5 | ADBE | 1W | UP | 57 | 266.51 | DOWN | 2026-09-11 | FALSCH | 252.23
2026-09-06 | Opus-5 | META | 1W | DOWN | 53 | 616.77 | UP | 2026-09-11 | FALSCH | 648.03
2026-09-06 | Opus-5 | TTWO | 1W | UP | 54 | 214.69 | DOWN | 2026-09-11 | RICHTIG | 215.47

<!--
  SATZ 08.09.2026 (Dienstag) - 13 1T-Zeilen, Modell Opus-5.
  Erzeugungszeitpunkt 15:20 MESZ.

  (A) AUFLOESUNG: KEINE. Zum Zeitpunkt dieses Laufs standen NULL offene 1T-Zeilen
      in der Datei - am 07.09. wurde regelkonform keine Batterie erzeugt (US-Feiertag
      Labor Day, nur 4 von 13 Studienwerten haetten gehandelt). Die 13 offenen
      1W-Zeilen vom 06.09. (Aufloesung 11.09.) sind NICHT beruehrt worden.

  (B) REFERENZKURSE - nach Anlage unterschiedlich datiert, regelkonform:
      - Die vier ETFs: XETRA-SCHLUSS MONTAG 07.09.2026 (Quelle stockanalysis.com,
        Tickers VWCE / LYMS / H4Z3 / MWRE).
      - SP500, MSCIWorld und die sieben US-Aktien: US-SCHLUSS FREITAG 04.09.2026,
        weil Montag Labor Day war.
      Das ist der Normalfall der Reihe ("letzter abgeschlossener Schlusskurs je Anlage"),
      nicht eine Ausnahme: auch an gewoehnlichen Dienstagen liegen zwischen Xetra-Schluss
      (17:30) und US-Schluss (22:00) viereinhalb Stunden.

  (C) RUECKRECHNUNGS-CHECK bestanden, alle vier ETFs (Freitag -> Montag):
      Vanguard 167.86 -> 167.78 (-0.05%) | Amundi Nasdaq-100 103.22 -> 103.50 (+0.27%)
      HSBC EM 16.51 -> 16.57 (+0.36%)    | Amundi MSCI World 160.09 -> 160.05 (-0.02%)
      Keine Spruenge, alle vier plausibel fuer einen Montag ohne US-Handel.

  (D) DATENKONFLIKTE / LUECKEN, benannt:
      - SP500: Reuters 7718.41 gegen CNN/indmoney 7718.60. Geloggt wird 7718.41
        (Primaerquelle, steht bereits als Ist-Kurs der 04.09.-Zeile).
      - MSCIWorld: fuer Montag 07.09. wurde KEIN Indexstand erhoben. Geloggt wird der
        Freitagsschluss 4986.90. Die Zeile ist damit streng genommen ein 2-Tages-Fenster
        und in der Auswertung so zu kennzeichnen. Stuetzend, nicht beweisend: der
        Amundi Core MSCI World bewegte sich am Montag um -0.02%.

  (E) LECK-OFFENLEGUNG (Learning 06.09. (7)) - heute besonders gross:
      Erzeugung 15:20 MESZ = 5h20 nach Xetra-Eroeffnung und 10 Minuten VOR der
      US-Eroeffnung. Fuer die vier ETF-Zeilen bleiben nur 2h10 bis zum Xetra-Schluss,
      und der laufende Kurs war beim Loggen bekannt (Vanguard +0.07%, Amundi N100
      +0.12%, HSBC EM 0.00%, Amundi MSCI World Tagesspanne 159.86-160.35).
      DIESE VIER ZEILEN SIND UEBERWIEGEND FESTSTELLUNG UEBER DIE GEGENWART.
      Die neun uebrigen Zeilen (SP500, MSCIWorld, 7 Einzelaktien) haben die volle
      US-Sitzung vor sich und sind echte Prognosen. In der Auswertung getrennt ausweisen.

  (F) KONFIDENZ-BEGRUENDUNG:
      Aggregate 60-64: Nasdaq-100-ETF und Vanguard sollen den Montagsgewinn, der ohne
      US-Handel entstand, gegen S&P-Futures von -0.4% bzw. Nasdaq-100-Futures von -0.2%
      wieder abgeben; HSBC EM folgt einem schwachen Asientag (Nikkei -1.7%, Kospi -0.58%,
      Hang Seng -0.38%). Einzelaktien bewusst 53-56 gehalten (1T-Einzelaktienquote der
      Reihe: 57.1% - kein Raum fuer hohe Konfidenzen). Einzige Ausnahme ASML mit 68:
      einziger Wert mit einem benannten, heute veroeffentlichten Primaerquellen-
      Katalysator (Samsung High-NA-EUV fuer DRAM-Serienfertigung bis 2028,
      Samsung Global Newsroom, 08.09.). ASML wird regelkonform als US-ADR in USD gefuehrt.

  (G) EX-DIVIDENDEN-PRUEFUNG (Learning 05.09. (3), vor dem Loggen angewandt):
      Im Fenster 07.-08.09. wurde fuer keinen der dreizehn Werte ein Ex-Termin gefunden.
      PepsiCo ging am 04.09. ex (1.48 $) - die mechanische Abwaertskomponente liegt damit
      vor dem Referenzkurs und nicht im Fenster. Das ist eine Aussage ueber meine Suche,
      nicht ueber die Welt (Learning 06.09. (2)).

  (H) INTEGRITAET: Keine Zeile geloescht, keine bestehende Zeile veraendert, keine
      1W-Zeile beruehrt. Nur angehaengt. Bestand vor diesem Lauf: 261 1T-Zeilen
      (157 R / 96 F / 8 n/v / 0 offen) und 76 1W-Zeilen, davon 13 offen.
      Laufende 1T-Bilanz unveraendert: Berater 157/253 = 62.1%, Baseline 113/253 = 44.7%.
-->
2026-09-08 | Opus-5 | SP500 | 1T | DOWN | 62 | 7718.41 | DOWN | 2026-09-08 | RICHTIG | 7673.52
2026-09-08 | Opus-5 | MSCIWorld | 1T | DOWN | 63 | 4986.90 | DOWN | 2026-09-08 | RICHTIG | 4966.17
2026-09-08 | Opus-5 | Vanguard FTSE All-World | 1T | DOWN | 60 | 167.78 | DOWN | 2026-09-08 | RICHTIG | 167.58
2026-09-08 | Opus-5 | Amundi Nasdaq-100 | 1T | DOWN | 63 | 103.50 | UP | 2026-09-08 | FALSCH | 103.56
2026-09-08 | Opus-5 | HSBC MSCI EM | 1T | DOWN | 64 | 16.57 | UP | 2026-09-08 | FALSCH | 16.63
2026-09-08 | Opus-5 | Amundi MSCI World | 1T | DOWN | 60 | 160.05 | DOWN | 2026-09-08 | RICHTIG | 159.89
2026-09-08 | Opus-5 | AAPL | 1T | DOWN | 55 | 319.97 | DOWN | 2026-09-08 | RICHTIG | 316.22
2026-09-08 | Opus-5 | UNH | 1T | DOWN | 54 | 397.14 | DOWN | 2026-09-08 | FALSCH | 400.84
2026-09-08 | Opus-5 | ASML | 1T | UP | 68 | 1714.88 | UP | 2026-09-08 | RICHTIG | 1764.85
2026-09-08 | Opus-5 | PEP | 1T | DOWN | 54 | 137.63 | DOWN | 2026-09-08 | FALSCH | 138.45
2026-09-08 | Opus-5 | ADBE | 1T | DOWN | 55 | 266.51 | DOWN | 2026-09-08 | RICHTIG | 257.26
2026-09-08 | Opus-5 | META | 1T | UP | 55 | 616.77 | UP | 2026-09-08 | FALSCH | 613.48
2026-09-08 | Opus-5 | TTWO | 1T | DOWN | 62 | 214.69 | UP | 2026-09-08 | RICHTIG | 213.29

<!--
  SATZ 09.09.2026 (Mittwoch) - 13 1T-Zeilen, Modell Opus-5. Erzeugung 11:15 MESZ.

  (A) AUFLOESUNG DES 08.09.-SATZES: alle 13 1T-Zeilen aufgeloest, ausschliesslich die
      Spalten Ergebnis und Ist-Kurs gesetzt. Zeilendiff geprueft: genau 13 geaenderte
      Zeilen, keine andere Spalte, keine Reihenfolge, keine 1W-Zeile beruehrt.
      TAGESBILANZ 08.09.: Berater 8/13 = 61.5 %, Random-Walk-Baseline 9/13 = 69.2 %.
      DER ZUFALL HAT DEN BERATER AN DIESEM TAG GESCHLAGEN.
      Aufschluesselung, die das gewohnte Muster umkehrt:
        Aggregate (2 Indizes + 4 ETFs): Berater 4/6, Baseline 6/6 (fehlerfrei).
        Einzelaktien (7):               Berater 4/7, Baseline 3/7.
      Das ist das Gegenteil des Musters aus Learning 06.09. (7) und spricht dagegen,
      dass das Intraday-Leck den Aggregatvorteil allein erklaert. Als offene Frage
      fuer die Auswertung notiert, nicht als Ergebnis.
      LAUFENDE 1T-BILANZ: Berater 165/266 = 62.0 %, Baseline 122/266 = 45.9 %,
      Vorsprung 16.1 Pp (vorher 17.4). Bestand: 274 1T-Zeilen
      (165 R / 101 F / 8 n/v / 0 offen). 13 1W-Zeilen vom 06.09. bleiben offen (Aufl. 11.09.).

  (B) KORREKTUR EINER GESTERN BENANNTEN LUECKE - MSCI WORLD:
      Am 08.09. wurde mangels Montagswert der Freitagsschluss 4986.90 als Referenz
      geloggt und ausdruecklich als 2-Tages-Fenster gekennzeichnet. Tatsaechlich EXISTIERT
      ein Montagswert: 4995.00 (+0.16 %) - der Index wird auch an US-Feiertagen aus dem
      europaeischen und asiatischen Handel fortgeschrieben (Quelle: investing.com,
      MIWO00000PUS, historische Kursreihe).
      ZWEI KONSEQUENZEN, BEIDE OFFENGELEGT:
      (a) Am ERGEBNIS aendert sich nichts: gegen 4995.00 ist der Dienstagsschluss
          4966.17 ebenfalls DOWN. Die Zeile bleibt RICHTIG.
      (b) Am BASELINE-Feld haette sich etwas geaendert: die letzte Tagesbewegung war
          +0.16 % (also UP), geloggt war DOWN.
      DAS FELD WIRD NICHT KORRIGIERT. An einer aufgeloesten Zeile wird nachtraeglich
      nichts ausser Ergebnis und Ist-Kurs veraendert - das ist die Integritaetsregel
      der Studie, und sie ist mehr wert als eine einzelne richtige Zelle.
      Der Fehler ist hier und in learnings.md dokumentiert und in der Auswertung als
      bekannte Einzelabweichung zu fuehren. Ab heute laeuft die MSCI-World-Reihe
      gegen die vollstaendige Kursreihe von investing.com.

  (C) REFERENZKURSE - alle vom Dienstag, 08.09.2026:
      Vier ETFs gegen den Xetra-Schluss (stockanalysis.com: VWCE 167.58, LYMS 103.56,
      H4Z3 16.63, MWRE 159.89). S&P 500 gegen Reuters/LSEG 7673.52. Sieben US-Aktien
      gegen den US-Schluss (stockanalysis.com). MSCI World gegen 4966.17 (investing.com).

  (D) RUECKRECHNUNGS-CHECK bestanden. Alle sieben Einzelaktien aus
      Referenzkurs x (1 + Tagesveraenderung) auf die zweite Nachkommastelle rekonstruierbar:
      AAPL 319.97 x 0.9883 = 316.23 (gemeldet 316.22) | UNH 397.14 x 1.0093 = 400.84
      ASML 1714.88 x 1.0291 = 1764.77 (gemeldet 1764.85) | PEP 137.63 x 1.0060 = 138.46
      ADBE 266.51 x 0.9653 = 257.26 | META 616.77 x 0.9947 = 613.50 (gemeldet 613.48)
      TTWO 214.69 x 0.9935 = 213.29 | SP500 7718.41 x 0.9942 = 7673.64 (gemeldet 7673.52)

  (E) LECK-OFFENLEGUNG (Learning 06.09. (7)) - heute DEUTLICH KLEINER als gestern:
      Erzeugung 11:15 MESZ = 1h15 nach Xetra-Eroeffnung (gestern 5h20) und 4h15 VOR der
      US-Eroeffnung (gestern 10 Minuten). Fuer die vier ETF-Zeilen liegen noch ueber
      sechs Handelsstunden vor der Aufloesung, fuer die neun uebrigen die volle
      US-Sitzung. DER HEUTIGE SATZ IST METHODISCH DER SAUBERSTE DER WOCHE und sollte
      in der Auswertung entsprechend gekennzeichnet werden.

  (F) KONFIDENZ-BEGRUENDUNG - bewusst niedriger als gestern (52-62 statt 54-68):
      Die gestrige Tagesbilanz lag mit 8/13 UNTER der Baseline von 9/13, und die einzige
      hohe Konfidenz des gestrigen Satzes (ASML 68) beruhte auf einem Ereignis
      (Samsung High-NA-Meldung), das es heute nicht gibt. OHNE BENANNTEN KATALYSATOR
      GIBT ES HEUTE KEINE KONFIDENZ UEBER 62.
      Marktlage beim Loggen: Brent erstmals seit Juli ueber 100 $ (US zerstoerte am 08.09.
      fuenf iranische Tanker, CENTCOM); US-Futures gemischt (Nasdaq +0.2 %, S&P +0.06 %,
      Dow -0.1 %); US 10J bei 4.80 %; CPI Freitag, FOMC naechste Woche mit 60 %
      Erhoehungswahrscheinlichkeit; Fear & Greed 39.
      Einzelne Zeilen: AAPL DOWN 58 wegen des Events heute 19:00 MESZ (historisch
      ueberwiegend schwache Vorstellungstage) und der Berichte ueber die Streichung des
      iPhone-18-Basismodells. META UP 57 nach der Muse-Vorstellung und +0.98 % im
      deutschen Handel. ADBE UP 54 als Gegenbewegung nach -10.0 % in zwei Handelstagen
      vor den Zahlen morgen.

  (G) EX-DIVIDENDEN-PRUEFUNG (Learning 05.09. (3), vor dem Loggen angewandt):
      Im Fenster 08.-09.09. fuer keinen der dreizehn Werte ein Ex-Termin gefunden.
      Aussage ueber meine Suche, nicht ueber die Welt (Learning 06.09. (2)).

  (H) INTEGRITAET: Keine Zeile geloescht, keine bestehende Zeile ausser den 13
      aufgeloesten 1T-Zeilen des 08.09.-Satzes veraendert (dort nur Ergebnis + Ist-Kurs),
      keine 1W-Zeile beruehrt. Danach nur angehaengt.
-->
2026-09-09 | Opus-5 | SP500 | 1T | DOWN | 56 | 7673.52 | DOWN | 2026-09-09 | RICHTIG | 7636.36
2026-09-09 | Opus-5 | MSCIWorld | 1T | DOWN | 62 | 4966.17 | DOWN | 2026-09-09 | RICHTIG | 4938.41
2026-09-09 | Opus-5 | Vanguard FTSE All-World | 1T | DOWN | 55 | 167.58 | DOWN | 2026-09-09 | RICHTIG | 166.22
2026-09-09 | Opus-5 | Amundi Nasdaq-100 | 1T | UP | 54 | 103.56 | UP | 2026-09-09 | FALSCH | 102.98
2026-09-09 | Opus-5 | HSBC MSCI EM | 1T | UP | 56 | 16.63 | UP | 2026-09-09 | FALSCH | 16.54
2026-09-09 | Opus-5 | Amundi MSCI World | 1T | DOWN | 54 | 159.89 | DOWN | 2026-09-09 | RICHTIG | 159.68
2026-09-09 | Opus-5 | AAPL | 1T | DOWN | 58 | 316.22 | DOWN | 2026-09-09 | RICHTIG | 315.34
2026-09-09 | Opus-5 | UNH | 1T | DOWN | 54 | 400.84 | UP | 2026-09-09 | RICHTIG | 393.06
2026-09-09 | Opus-5 | ASML | 1T | DOWN | 55 | 1764.85 | UP | 2026-09-09 | RICHTIG | 1729.52
2026-09-09 | Opus-5 | PEP | 1T | DOWN | 54 | 138.45 | UP | 2026-09-09 | RICHTIG | 136.69
2026-09-09 | Opus-5 | ADBE | 1T | UP | 54 | 257.26 | DOWN | 2026-09-09 | FALSCH | 254.86
2026-09-09 | Opus-5 | META | 1T | UP | 57 | 613.48 | DOWN | 2026-09-09 | RICHTIG | 653.69
2026-09-09 | Opus-5 | TTWO | 1T | DOWN | 52 | 213.29 | DOWN | 2026-09-09 | RICHTIG | 211.14

<!--
  SATZ 10.09.2026 (Donnerstag) - 13 1T-Zeilen, Modell Opus-5. Erzeugung 12:15 MESZ.

  (A) AUFLOESUNG DES 09.09.-SATZES: alle 13 Zeilen, nur Ergebnis + Ist-Kurs gesetzt.
      Zeilendiff geprueft: genau 13 geaenderte Zeilen, keine 1W-Zeile beruehrt.
      TAGESBILANZ 09.09.: Berater 10/13 = 76.9 %, Baseline 7/13 = 53.8 %.
      Vorsprung 23.1 Pp - der staerkste Tag der Woche und die Gegenprobe zum 08.09.,
      an dem die Baseline mit 9/13 vorne lag.
      AUFSCHLUESSELUNG: Aggregate 4/6 (Baseline 4/6, unentschieden);
      EINZELAKTIEN 6/7 gegen Baseline 3/7 - der gesamte Vorsprung kam aus den
      Einzelaktien, also dort, wo das Intraday-Leck NICHT wirkt und wo die Reihe
      historisch am schwaechsten ist (57.1 % ueber die Gesamtreihe).
      ZWEITER TAG IN FOLGE MIT DIESEM MUSTER. Offene Frage fuer die Auswertung,
      ausdruecklich noch KEIN Befund: Erklaert das Leck den Aggregatvorteil der
      Gesamtreihe womoeglich schlechter als in Learning 06.09. (7) angenommen?
      WERTVOLLSTE ZEILE: META UP bei Konfidenz 57 -> +6.55 % (613.48 auf 653.69).
      Begruendung im Log war "nach der Muse-Vorstellung und +0.98 % im deutschen
      Handel". Die RICHTUNG war aus der Produktmeldung ableitbar, die GROESSE nicht.
      LAUFENDE 1T-BILANZ: Berater 175/279 = 62.7 %, Baseline 129/279 = 46.2 %,
      Vorsprung 16.5 Pp. Bestand 287 1T-Zeilen (175 R / 104 F / 8 n/v / 0 offen).
      13 1W-Zeilen vom 06.09. bleiben offen, Aufloesung morgen durch den Samstags-Task.

  (B) REFERENZKURSE - alle vom Mittwoch, 09.09.2026:
      Vier ETFs gegen Xetra-Schluss (stockanalysis.com): VWCE 166.22, LYMS 102.98,
      H4Z3 16.54, MWRE 159.68. S&P 500 gegen Reuters/LSEG 7636.36.
      MSCI World gegen investing.com 4938.41 (vollstaendige Kursreihe, wie seit
      Learning 09.09. (4) vorgeschrieben). Sieben US-Aktien gegen US-Schluss.

  (C) RUECKRECHNUNGS-CHECK bestanden, alle sieben Einzelaktien und der S&P 500:
      AAPL 316.22 x 0.9972 = 315.33 (gemeldet 315.34) | UNH 400.84 x 0.9806 = 393.06
      ASML 1764.85 x 0.98 = 1729.55 (gemeldet 1729.52) | PEP 138.45 x 0.9873 = 136.69
      ADBE 257.26 x 0.9907 = 254.86 | META 613.48 x 1.0655 = 653.66 (gemeldet 653.69)
      TTWO 213.29 x 0.9899 = 211.14 | SP500 7673.52 x 0.9952 = 7636.71 (gemeldet 7636.36)

  (D) LECK-OFFENLEGUNG: Erzeugung 12:15 MESZ = 2h15 nach Xetra-Eroeffnung und
      3h15 VOR der US-Eroeffnung. Fuer die ETF-Zeilen bleiben ueber fuenf
      Handelsstunden, fuer die neun uebrigen die volle US-Sitzung. Vergleichbar
      sauber wie der 09.09.-Satz und deutlich sauberer als der 08.09.-Satz.

  (E) KONFIDENZ-BEGRUENDUNG - Spanne 52-62, kein Wert darueber:
      Heute fallen EZB-Entscheid (14:15), EZB-Pressekonferenz (14:45) und US-PPI
      (14:30) IN den Handelstag; deren Ausgang kenne ich nicht. Eine Konfidenz ueber
      62 waere an einem solchen Tag nicht begruendbar.
      Hoechster Wert UNH DOWN 62: gestuetzt auf den CVS-Kostenkommentar vom 09.09.
      ("high-trend cost growth", IBD), der Oscar Health und UNH gedrueckt hat, plus
      -2.42 % im deutschen Vormittagshandel.
      AAPL UP 60: Event vorbei, ein Analyst hat die iPhone-Duo-Umsatzprognose
      ueber Nacht verdoppelt, Aktie nachboerslich fester, +0.66 % im deutschen Handel.
      HSBC EM DOWN 58: Brent ueber 100 $ trifft die Schwellenlaender als
      Nettoimporteure (Indien 11.69 %, China 19.35 % Indexgewicht).
      SP500 UP 55 gegen Nasdaq-schwaechere Futures: bewusst niedrig, weil Dow- und
      S&P-Futures steigen, die Nasdaq-Futures aber fallen - ein widerspruechliches Bild.

  (F) EX-DIVIDENDEN-PRUEFUNG: im Fenster 09.-10.09. fuer keinen der dreizehn Werte
      ein Ex-Termin gefunden; erstmals ueber die Tickerseiten geprueft und nicht nur
      ueber die Suchschnittstelle (Learning 09.09. (6)).

  (G) INTEGRITAET: keine Zeile geloescht, keine bestehende Zeile ausser den 13
      aufgeloesten 09.09.-Zeilen veraendert, keine 1W-Zeile beruehrt, danach nur angehaengt.
-->
2026-09-10 | Opus-5 | SP500 | 1T | UP | 55 | 7636.36 | DOWN | 2026-09-10 | FALSCH | 7591.70
2026-09-10 | Opus-5 | MSCIWorld | 1T | UP | 53 | 4938.41 | DOWN | 2026-09-10 | FALSCH | 4935.29
2026-09-10 | Opus-5 | Vanguard FTSE All-World | 1T | UP | 56 | 166.22 | DOWN | 2026-09-10 | FALSCH | 165.26
2026-09-10 | Opus-5 | Amundi Nasdaq-100 | 1T | UP | 52 | 102.98 | DOWN | 2026-09-10 | n/v | 
2026-09-10 | Opus-5 | HSBC MSCI EM | 1T | DOWN | 58 | 16.54 | DOWN | 2026-09-10 | n/v | 
2026-09-10 | Opus-5 | Amundi MSCI World | 1T | UP | 54 | 159.68 | DOWN | 2026-09-10 | n/v | 
2026-09-10 | Opus-5 | AAPL | 1T | UP | 60 | 315.34 | DOWN | 2026-09-10 | RICHTIG | 326.57
2026-09-10 | Opus-5 | UNH | 1T | DOWN | 62 | 393.06 | DOWN | 2026-09-10 | RICHTIG | 388.28
2026-09-10 | Opus-5 | ASML | 1T | DOWN | 55 | 1729.52 | DOWN | 2026-09-10 | RICHTIG | 1687.43
2026-09-10 | Opus-5 | PEP | 1T | UP | 53 | 136.69 | DOWN | 2026-09-10 | FALSCH | 136.65
2026-09-10 | Opus-5 | ADBE | 1T | DOWN | 54 | 254.86 | DOWN | 2026-09-10 | RICHTIG | 248.83
2026-09-10 | Opus-5 | META | 1T | UP | 54 | 653.69 | UP | 2026-09-10 | FALSCH | 644.38
2026-09-10 | Opus-5 | TTWO | 1T | DOWN | 52 | 211.14 | DOWN | 2026-09-10 | FALSCH | 216.96

<!-- ERZEUGUNG 2026-09-11 (Freitag, Handelstag), Modell Opus-5, Horizont 1T
  (A) AUFLOESUNG 10.09.: 13 Zeilen faellig, 10 aufgeloest, 3 als n/v.
      Berater 4/10 = 40 % · Baseline (Random Walk) 7/10 = 70 %.
      SCHLECHTESTER TAG DER REIHE GEGEN DIE BASELINE. Ursache benannt und nicht
      wegerklaert: sechs von zehn Prognosen lauteten UP an einem Tag, an dem der
      Markt zum VIERTEN Mal in Folge fiel - darunter alle drei Breitmarkt-Zeilen.
      Das ist eine Gegenbewegungs-Vorliebe, kein Pech.
      Laufend gesamt (nur 1T, n=289): Berater 179 = 61.9 % · Baseline 136 = 47.1 %.

  (B) NUR 10 STATT 13 NEUE ZEILEN - offengelegte Regelabweichung.
      Fuer Amundi Nasdaq-100 (LYMS), HSBC MSCI EM (H4Z3) und Amundi MSCI World (MWRE)
      war KEIN Referenzkurs mit bestandenem Rueckrechnungs-Check beschaffbar.
      Abgefragte Quellwege, alle erfolglos:
        1. stockanalysis.com Xetra-Historie - Datenstand 04.09., keine neueren Kurse
        2. justETF Profil + API - Kurs per JavaScript nachgeladen, Abruf leer
        3. Yahoo Finance direkt - fuer beide Abrufwerkzeuge gesperrt
        4. Yahoo Finance ueber Suchtreffer - ohne belastbares Datum; bei H4Z3
           SCHEITERTE die Rueckrechnung (impliziter Vortagesschluss 16.58 gegen
           geloggte Referenz 16.54)
        5. onvista - liefert Tradegate/Stuttgart/L&S statt Xetra; bei MWRE ergaebe
           sich ein impliziter Vortagesschluss von ~157.5 gegen Referenz 159.68,
           Rueckrechnung ebenfalls nicht bestanden
      Nach der Datendisziplin-Regel entscheidet der bestandene Rueckrechnungs-Check.
      Er ist bei keiner der drei Zeilen bestanden -> keine Zahl geloggt, weder als
      Ist-Kurs (10.09.) noch als Referenzkurs (11.09.).
      DAS IST EIN DATENPIPELINE-AUSFALL, KEIN MARKTBEFUND. Kosten: 3 Beobachtungen.
      Zusaetzliche Ausfaelle an diesem Tag: Firecrawl-Scraper gesperrt (unveraendert),
      Linux-Arbeitsumgebung durch ein Windows-Update vom 08.09. blockiert,
      Finanzfluss-Abruf nicht angemeldet (kein Depotstand).

  (C) RUECKRECHNUNGS-CHECK der verwendeten Referenzkurse - alle bestanden:
      AAPL 315.34 x 1.0356 = 326.56 (Ist 326.57) · UNH 393.06 x 0.9878 = 388.26 (388.28)
      ASML 1729.52 x 0.9757 = 1687.49 (1687.43) · PEP 136.69 x 0.9997 = 136.65 (136.65)
      ADBE 254.86 x 0.9763 = 248.82 (248.83) · META 653.69 x 0.9858 = 644.41 (644.38)
      TTWO 211.14 x 1.0276 = 216.97 (216.96) · VWCE 165.26 + 0.96 = 166.22 = Referenz
      SP500 7591.70 / 7636.36 - 1 = -0.585 % (gemeldet -0.58 %)
      MSCIWorld 4935.29 / 4938.41 - 1 = -0.063 % (gemeldet -0.06 %)

  (D) QUELLENKONFLIKT S&P 500 benannt statt aufgeloest: eine zweite Quelle nennt
      7596.60 / -0.62 %. Nur 7591.70 besteht die Rueckrechnung gegen 7636.36.
      Verwendet: 7591.70. Ebenso ADBE: 248.95 (-2.32 %) vs. 248.83 (-2.37 %);
      nur 248.83 besteht die Rueckrechnung. Auf die Richtung wirkt sich beides nicht aus.

  (E) LECK-OFFENLEGUNG: Erzeugung vormittags MESZ, VOR dem US-CPI um 14:30 und
      VOR der US-Eroeffnung. Fuer die ETF-/Index-Zeilen bleibt die volle
      europaeische Sitzung, fuer die sieben Aktien die volle US-Sitzung.

  (F) KONFIDENZ-BEGRUENDUNG - Spanne 52-68:
      Der US-CPI faellt IN den Handelstag (14:30 MESZ) und ist laut StoneX die Zahl,
      die ueber die Fed-Entscheidung am 16.09. entscheidet. Hohe Konfidenz waere heute
      nicht begruendbar - mit EINER Ausnahme.
      ADBE DOWN 68: einzige Zeile ueber 60. Grund ist kein Marktgefuehl, sondern ein
      beobachteter Kurs - die Aktie wurde nachboerslich bereits bei ~243.50 gehandelt,
      -2.14 % unter dem Referenzkurs 248.83.
      SP500/MSCIWorld/VWCE DOWN 55-57: bewusst NICHT mechanisch der Baseline gefolgt.
      Benannter Mechanismus: asiatische Boersen gaben Freitagfrueh nach, globale
      Anleiherenditen auf neuen Hochs, WTI nach +6.7 % weiter fest. Gegen die
      Prognose spricht ein weiches Kern-CPI - deshalb keine Konfidenz ueber 57.
      AAPL DOWN 53 nach +3.56 %: schwaechste Ueberzeugung des Satzes. Nach Learning
      von heute ausdruecklich geprueft, dass das KEINE reflexhafte Gegenbewegungs-
      Annahme in die andere Richtung ist - die Begruendung ist die ungeklaerte Ursache
      des Sprungs, nicht ein Mean-Reversion-Reflex. Deshalb nur 53.
      PEP UP 52 / UNH UP 53: XLP war mit +0.05 % der einzige gruene Sektor, XLV -0.55 %;
      beide defensiv in einem Zins-/Oelumfeld.
      ASML DOWN 56: KGV 54.26 gegen Anleiherenditen auf Mehrjahreshoch.
      META UP 53 / TTWO DOWN 52: schwach begruendet, entsprechend niedrig.

  (G) EX-DIVIDENDEN-PRUEFUNG: im Fenster 10.-11.09. fuer keinen der Werte ein
      Ex-Termin erhoben. ACHTUNG: heute nur ueber die Nachrichtensuche geprueft,
      NICHT ueber die Tickerseiten (Werkzeugausfall) - schwaecher als am 10.09.

  (H) INTEGRITAET: keine Zeile geloescht, keine bestehende Zeile ausser den 13
      aufgeloesten 10.09.-Zeilen veraendert (dort nur Ergebnis + Ist-Kurs),
      keine 1W-Zeile beruehrt, danach nur angehaengt.
-->
2026-09-11 | Opus-5 | SP500 | 1T | DOWN | 55 | 7591.70 | DOWN | 2026-09-11 | FALSCH | 7656.98
2026-09-11 | Opus-5 | MSCIWorld | 1T | DOWN | 57 | 4935.29 | DOWN | 2026-09-11 | FALSCH | 4907.06
2026-09-11 | Opus-5 | Vanguard FTSE All-World | 1T | DOWN | 57 | 165.26 | DOWN | 2026-09-11 | FALSCH | 166.67
2026-09-11 | Opus-5 | AAPL | 1T | DOWN | 53 | 326.57 | UP | 2026-09-11 | FALSCH | 332.27
2026-09-11 | Opus-5 | UNH | 1T | UP | 53 | 388.28 | DOWN | 2026-09-11 | FALSCH | 379.09
2026-09-11 | Opus-5 | ASML | 1T | DOWN | 56 | 1687.43 | DOWN | 2026-09-11 | FALSCH | 1698.30
2026-09-11 | Opus-5 | PEP | 1T | UP | 52 | 136.65 | DOWN | 2026-09-11 | FALSCH | 136.32
2026-09-11 | Opus-5 | ADBE | 1T | DOWN | 68 | 248.83 | DOWN | 2026-09-11 | FALSCH | 252.23
2026-09-11 | Opus-5 | META | 1T | UP | 53 | 644.38 | DOWN | 2026-09-11 | RICHTIG | 648.03
2026-09-11 | Opus-5 | TTWO | 1T | DOWN | 52 | 216.96 | UP | 2026-09-11 | RICHTIG | 215.47

<!-- AUFLOESUNG 2026-09-12 (Samstag) — KEINE NEUE BATTERIE (kein Handelstag)
  (A) AUFGELOEST: alle 10 offenen 1T-Zeilen mit Auflösungsdatum 11.09.
      Berater 2/10 = 20 % · Baseline (Random Walk) 3/10 = 30 %.
      SCHLECHTESTER TAG DER GESAMTEN REIHE. Zweiter Tag in Folge unter der Baseline
      (10.09.: 40 % gegen 70 %).
      Laufend gesamt (nur 1T, n=299): Berater 181 = 60.5 % · Baseline 139 = 46.5 %
      · Vorsprung +14.0 Pp.

  (B) FEHLERANALYSE, nicht wegerklaert:
      Die drei Index-Prognosen lauteten DOWN und stuetzten sich auf drei am Morgen
      KORREKT beobachtete Tatsachen — nachgebende asiatische Boersen, Anleiherenditen
      auf neuen Hochs, weiter festes Oel. Alle drei Beobachtungen stimmten.
      Gebrochen ist die PRAEMISSE: eine Waffenruhe im Roten Meer drueckte WTI um
      2.79 % unter 100 $, und der Markt stieg TROTZ eines heissen Kern-CPI (0.3 %
      gegen erwartete 0.2 %) um 0.86 %.
      Reuters-Zitat (Dennis Dick, Triple D Trading): "that is probably the reason for
      the rally — not so much even the CPI data, but the weak oil."
      Ich habe die Wirkungskette richtig beschrieben und ihren ANFANG fortgeschrieben.
      NEUE REGEL (Learning 12.09. (1)): Beruht eine Prognose auf einer Wirkungskette,
      wird das TRAGENDE GLIED benannt und mit eigener Unsicherheit versehen. Haengt es
      an einem politischen Zustand (Krieg, Waffenruhe, Zoll, Wahl), gilt es als instabil
      und deckelt die Gesamtkonfidenz auf 55. Die 57er-Zeilen waeren danach unzulaessig.

  (C) ADBE DOWN 68 — hoechste Konfidenz des Satzes, und FALSCH.
      Begruendung war: "der nachboersliche Stand ist der beste Einzelpraediktor fuer
      die EROEFFNUNG des Folgetags". Der Satz stimmt — fuer die Eroeffnung.
      Adobe eroeffnete tatsaechlich schwach (Tagestief 237.50 $) und schloss bei
      252.23 $ (+1.37 %). Zwischen Eroeffnung und Schluss liegt eine volle Sitzung.
      Learning 12.09. (2).

  (D) MSCIWORLD — DATENREVISION OFFENGELEGT.
      Investing.com weist den Schlusskurs vom 10.09. heute mit 4905.88 aus; gestern
      stand dort 4935.29, und dieser Wert wurde als Referenz geloggt. Der Wert wurde
      nachtraeglich revidiert.
      Aufgeloest wurde gegen die vom Anbieter ausgewiesene TAGESRICHTUNG des 11.09.
      (+0.02 %), also FALSCH — NICHT gegen den geloggten Referenzkurs, gegen den die
      Zeile RICHTIG gewesen waere. Begruendung: prognostiziert war die Richtung des
      Tages, nicht ein Abstand zu einer Zahl im eigenen Log. Einen Treffer aus einem
      Datenfehler mitzunehmen waere die schlechtere Wahl.
      Der geloggte Referenzkurs 4935.29 bleibt UNVERAENDERT stehen (Integritaetsregel,
      wie am 09.09. bei der Baseline-Frage entschieden).

  (E) RUECKRECHNUNGS-CHECK aller acht US-Schlusskurse gegen die geloggten Referenzen —
      alle bestanden:
      AAPL 326.57 x 1.0175 = 332.28 (Ist 332.27) · UNH 388.28 x 0.9763 = 379.07 (379.09)
      ASML 1687.43 x 1.0064 = 1698.23 (1698.30) · PEP 136.65 x 0.9976 = 136.32 (136.32)
      ADBE 248.83 x 1.0137 = 252.24 (252.23) · META 644.38 x 1.0057 = 648.05 (648.03)
      TTWO 216.96 x 0.9931 = 215.46 (215.47) · NOW 131.17 x 1.0104 = 132.53 (132.53)
      SP500 7656.98 / 7591.70 - 1 = +0.86 % (gemeldet +0.86 %)
      VWCE 166.67 / 165.26 - 1 = +0.85 % (Finanzfluss-Abruf, Freitagsschluss)

  (F) QUELLENKONFLIKT ADBE benannt statt aufgeloest: drei Quellen nennen 252.23 (+1.37 %),
      253.80 und 246.91 (-0.77 %). Nur 252.23 besteht die Rueckrechnung gegen 248.83.
      Verwendet: 252.23. Ebenso AAPL: 332.27 (+1.75 %) vs. 333.58 (+2.15 %); beide
      bestehen ihre eigene Rueckrechnung, verwendet wurde stockanalysis (332.27), weil
      dessen Datenreihe explizit bis 2026-09-11 23:00 laeuft.

  (G) ETF-DATENWEG REPARIERT: Der Vanguard-Schluss kam aus dem Finanzfluss-Abruf.
      Ab Montag ist Finanzfluss die primaere Kursquelle fuer die GEHALTENEN ETF-Zeilen.
      OFFEN bleibt Amundi MSCI World — im Studien-Universum, aber keine gehaltene
      Position, taucht im Tracker nicht auf. Externe Quelle bis Montag noetig.

  (H) INTEGRITAET: keine Zeile geloescht, keine bestehende Zeile ausser den 10
      aufgeloesten 11.09.-Zeilen veraendert (dort nur Ergebnis + Ist-Kurs),
      keine 1W-Zeile beruehrt (die Wochenbilanz macht der separate Samstags-Task),
      nichts angehaengt — Samstag ist kein Handelstag.
-->

<!-- SAMSTAGS-TASK 12.09.2026 - WOCHENPROGNOSEN (Horizont 1W), erzeugt nach Freitagsschluss.
     Referenzkurs = Schlusspreis Fr 11.09.2026. Aufloesungsdatum = Fr 18.09.2026.
     Baseline = Richtung der Vorwoche (Schluss 04.09. -> Schluss 11.09.).

  (A) QUELLEN (alle nach Schluss datiert):
      Einzelaktien + ASML-ADR: stockanalysis.com Kurshistorie, Stand 11.09. 16:00 ET.
        AAPL 332.27 (+1.75 %), UNH 379.09 (-2.37 %), ASML 1698.30 (+0.64 %),
        PEP 136.32 (-0.24 %), ADBE 252.23 (+1.37 %), META 648.03 (+0.57 %),
        TTWO 215.47 (-0.69 %).
      ETFs: VWCE 166.86 / LYMS 103.38 / MWRE 159.06 (stockanalysis.com, ETR-Tickers,
        Xetra-Schluss 11.09.). HSBC MSCI EM: 16.4395 aus der Kurshistorie von
        live.deutsche-boerse.com (Xetra), weil stockanalysis fuer H4Z3 am 11.09.
        keine Zeile fuehrt (letzter Stand dort 10.09.).
      SP500: 7656.98 (+65.28 / +0.86 %), AP-Marktbericht via ABC News, bestaetigt
        durch STL.News-Schlusstabelle.
      MSCIWorld: 4937.32 (+0.64 %), Investing.com (MIWO00000PUS) - SIEHE (B).

  (B) RUECKRECHNUNGS-CHECK: bestanden fuer alle zwoelf Werte ausser MSCIWorld.
      Die sieben Aktien, SP500 und VWCE rechnen exakt gegen die Donnerstags-
      Schlusskurse zurueck, die in den 1T-Zeilen vom 11.09. dieser Datei als
      Referenzkurs stehen (AAPL 326.57, UNH 388.28, ASML 1687.43, PEP 136.65,
      ADBE 248.83, META 644.38, TTWO 216.96, SP500 7591.70, VWCE 165.26).
      LYMS 102.36 x 1.0100 = 103.38, MWRE 157.64 x 1.0090 = 159.06,
      H4Z3 16.261 -> 16.4395 = +1.10 %, alle drei aus derselben Quelle wie der Schluss.

  (C) QUELLENKONFLIKTE, ausdruecklich benannt (Regel 5):
      1. SP500: AP/STL.News 7656.98, live.deutsche-boerse.com 7656.02,
         24/7-Wall-St. 7663.20. Spannweite 6 Punkte = 0.08 %. Geloggt wird 7656.98,
         weil 7591.70 + 65.28 exakt aufgeht. RICHTUNG unter allen drei Quellen
         identisch (unter dem Referenzkurs 7718.60), HOEHE als unsicher markiert.
      2. MSCIWorld - GRAVIERENDER, weil die Reihe betroffen ist: Die Batterie hat
         MSCIWorld bisher aus boerse.de (XC0009692739) geloggt. boerse.de fuehrt am
         12.09. noch KEINEN Schluss fuer den 11.09. (letzte Zeile 10.09. = 4890.96);
         Investing.com nennt fuer denselben 10.09. 4905.88, die 1T-Zeile vom 11.09.
         in dieser Datei 4935.29. DREI Werte fuer EINEN Tag, Spannweite 0.9 %.
         Fuer die Aufloesung ist das folgenlos - alle drei Reihen liegen am 11.09.
         klar unter dem Referenzkurs 4981.85, die Richtung DOWN ist robust.
         Fuer die Zukunft nicht folgenlos: Ab dieser Zeile wird MSCIWorld
         durchgehend aus Investing.com (MIWO00000PUS) geloggt, Referenzkurs
         4937.32, Vorwoche 4986.93. Der Quellenwechsel ist eine bewusste
         Entscheidung dieses Laufs und steht hier, damit die Bruchstelle in der
         Reihe spaeter auffindbar ist statt unsichtbar zu bleiben.
      3. HSBC MSCI EM ist der einzige Wert mit zwei Quellen in EINER Zeile
         (Referenz 16.49 stammt aus stockanalysis, Ist-Kurs aus deutsche-boerse).
         Gegenprobe gemacht: die Kurshistorie von deutsche-boerse nennt fuer den
         04.09. ebenfalls 16.49 - Referenz und Ist-Kurs sind also auch innerhalb
         EINER Quelle vergleichbar, die Aufloesung DOWN haelt.

  (D) AUFLOESUNG DES 06.09.-SATZES: 13 Zeilen, nur Ergebnis + Ist-Kurs gesetzt.
      Berater 6/13 = 46.2 %, Baseline 7/13 = 53.8 % - die naive Fortschreibung
      war diese Woche BESSER als die Prognose. Laufend (alle aufgeloesten
      1W-Zeilen): Berater 48/88 = 54.5 %, Baseline 48/88 = 54.5 %. Gleichstand.
      Keine 1T-Zeile beruehrt; die zehn offenen 1T-Zeilen vom 11.09. bleiben dem
      Morgenreport ueberlassen.

  (E) NEBENBEFUND, bewusst NICHT korrigiert: Die Zeile "HSBC MSCI EM, Aufl. 21.08.,
      Ergebnis n/v" ist heute nachtraeglich aufloesbar - die Kurshistorie von
      deutsche-boerse fuehrt fuer den 21.08. 16.12. Die Zeile bleibt trotzdem auf
      n/v stehen, weil der Auftrag nur Zeilen mit Ergebnis "offen" freigibt.
      Das "n/v" war also kein Datenproblem, sondern ein Quellenproblem (Ausfall des
      damaligen Zugangs) - festgehalten in learnings.md.

  (F) MARKTLAGE ZUM PROGNOSEZEITPUNKT (Fakten):
      - August-CPI am 11.09.: Kopfrate 3.4 % j/j und +0.4 % m/m, Kern +0.3 % m/m /
        2.4 % j/j, im Rahmen der Erwartung. Danach RALLYE: SP500 +0.86 %,
        Dow +0.98 %, Nasdaq +0.96 %, neun von elf Sektoren im Plus,
        Gewinner zu Verlierern rund 2.1 zu 1. Erster Plustag nach vier Minustagen.
      - Auf Wochensicht trotzdem negativ: SP500 rund -0.8 %, Dow -1.6 %,
        Nasdaq -0.7 %, Russell 2000 -2.4 %. SP500 rund 2 % unter dem Rekordschluss.
      - FOMC am 15./16.09. IM FENSTER. Zinserhoehungswahrscheinlichkeit laut
        CME FedWatch nach dem CPI auf knapp 90 % gesprungen (Vortag rund 70 %);
        andere Quellen nennen 66-70 %. Quellenkonflikt benannt, Richtung
        eindeutig: eine Erhoehung ist weitgehend eingepreist.
      - Oel am Freitag rund -3.8 % (Brent-/WTI-Spitze abgebaut) - genau der
        Treiber, der die viertaegige Verlustserie ausgeloest hatte.
      - EUR/USD 1.1595 (-0.14 %). Eine Fed-Erhoehung stuetzt tendenziell den USD,
        was die vier EUR-notierten ETFs auf US-Basiswerte rechnerisch stuetzt und
        Schwellenlaender belastet.
      - Fr 18.09. ist grosser Verfallstag (Quadruple Witching) - erhoehte
        Schlusskurs-Volatilitaet genau am Aufloesungstag.
      - Adobe hat am 10.09. berichtet: Umsatz 6.76 Mrd. $ (+13 %), bereinigtes
        EPS 6.13 $, beides ueber Konsens, Jahresprognose angehoben, zusaetzlich
        CEO-Wechsel angekuendigt. Die Aktie fiel trotzdem (Learning 16.07.:
        die Messlatte ist die Erwartung, nicht der Konsens).

  (G) KOHAERENZ-CHECK (Learning 05.09.): Aggregat-Gruppe (2 Indizes + 4 ETFs)
      5x UP, 1x DOWN. KLUMPENRISIKO WIRD AUSDRUECKLICH AUSGEWIESEN: Die fuenf
      UP-Zeilen sind EINE Wette, nicht fuenf - Begruendung ist durchgehend
      "Erhoehung eingepreist + Oelpreis-Entlastung + CPI im Rahmen". Faellt die
      Fed-Kommunikation am 16.09. hawkischer aus als der reine Zinsschritt,
      kippen sie gemeinsam. Das ist strukturell derselbe Aufbau wie am 06.09.
      (5x DOWN), nur mit umgekehrtem Vorzeichen - und am 06.09. gingen davon
      3 auf und 2 daneben.
      Bewusst gegenlaeufig, mit eigenem Treiber: HSBC MSCI EM (DOWN 53).
      Begruendung: festerer USD nach einer Erhoehung ist der klassische
      EM-Gegenwind, und der Wert ist der einzige im Aggregat, dessen Nachfrage
      nicht an den US-Indizes haengt. Keine kosmetische Gegenposition.

  (H) KALIBRIERUNG - warum keine einzige Zeile ueber 55 steht:
      Die laufende 1W-Bilanz liegt exakt auf der Baseline (48/88 gegen 48/88).
      Eine Kante ist in 88 Beobachtungen nicht nachweisbar; Konfidenzen ueber 60
      waeren durch nichts gedeckt. Hoechster Wert diese Woche: UNH DOWN 55
      (sechs von sieben bisherigen UNH-1W-DOWN-Zeilen richtig, und der Wert
      verlor am Freitag 2.37 % gegen einen Markt, der 0.86 % zulegte - eigener,
      marktunabhaengiger Treiber). Niedrigste: AAPL / ADBE / TTWO 51.
      ADBE steht bewusst auf dem Konfidenzboden: 2 von 8 aufgeloesten
      1W-Zeilen richtig, Fehlschlaege in BEIDE Richtungen. Nach der Regel vom
      08.08. (IGV-vs-SMH) wird daraus keine Umkehrwette gebaut, sondern das
      Fehlen einer Kante protokolliert.

  (I) EX-DIVIDENDEN-PRUEFUNG: Fuer das Fenster 14.-18.09. ueber die Nachrichten-
      und Tickersuche kein Ex-Termin bei den 13 Werten erhoben. Das ist eine
      Aussage ueber meine Suche, nicht ueber die Welt (Learning 06.09.).

  (J) SAUBERKEIT: Erzeugung am Samstag bei geschlossenen Maerkten - kein
      Intraday-Leck, fuer alle 13 Zeilen echte Prognose ueber einen vollstaendig
      ungehandelten Zeitraum.

  (K) INTEGRITAET: 13 1W-Zeilen des 06.09.-Satzes aufgeloest, dabei ausschliesslich
      die Spalten Ergebnis und Ist-Kurs gesetzt - keine andere Spalte, keine
      Reihenfolge, keine 1T-Zeile beruehrt. Danach nur angehaengt.
-->
2026-09-12 | Opus-5 | SP500 | 1W | UP | 54 | 7656.98 | DOWN | 2026-09-18 | FALSCH | 7650.50
2026-09-12 | Opus-5 | MSCIWorld | 1W | UP | 53 | 4937.32 | DOWN | 2026-09-18 | FALSCH | 4913.98
2026-09-12 | Opus-5 | Vanguard FTSE All-World | 1W | UP | 53 | 166.86 | DOWN | 2026-09-18 | RICHTIG | 167.14
2026-09-12 | Opus-5 | Amundi Nasdaq-100 | 1W | UP | 53 | 103.38 | UP | 2026-09-18 | RICHTIG | 105.300
2026-09-12 | Opus-5 | HSBC MSCI EM | 1W | DOWN | 53 | 16.4395 | DOWN | 2026-09-18 | RICHTIG | 16.29
2026-09-12 | Opus-5 | Amundi MSCI World | 1W | UP | 53 | 159.06 | DOWN | 2026-09-18 | RICHTIG | 159.53
2026-09-12 | Opus-5 | AAPL | 1W | UP | 51 | 332.27 | UP | 2026-09-18 | RICHTIG | 336.13
2026-09-12 | Opus-5 | UNH | 1W | DOWN | 55 | 379.09 | DOWN | 2026-09-18 | RICHTIG | 376.90
2026-09-12 | Opus-5 | ASML | 1W | UP | 52 | 1698.30 | DOWN | 2026-09-18 | FALSCH | 1679.92
2026-09-12 | Opus-5 | PEP | 1W | DOWN | 54 | 136.32 | DOWN | 2026-09-18 | RICHTIG | 129.75
2026-09-12 | Opus-5 | ADBE | 1W | UP | 51 | 252.23 | DOWN | 2026-09-18 | FALSCH | 248.92
2026-09-12 | Opus-5 | META | 1W | UP | 52 | 648.03 | UP | 2026-09-18 | RICHTIG | 665.75
2026-09-12 | Opus-5 | TTWO | 1W | UP | 51 | 215.47 | UP | 2026-09-18 | FALSCH | 205.45

<!-- LAUF 2026-09-13 (Sonntag) — KEINE BATTERIE, KEINE AUFLOESUNG
  (A) DUBLETTENPRUEFUNG vor allem anderen (Regel aus Learning 11.09. (5)):
      Datei auf Zeilen mit Datum 2026-09-13 und Horizont 1T geprueft. ERGEBNIS: keine.
      Es wurde trotzdem NICHTS erzeugt — Begruendung unter (B).

  (B) KEINE ERZEUGUNG: Sonntag ist kein Handelstag. Der letzte abgeschlossene
      Handelstag war Freitag, 11.09.; seither existiert kein neuer Schlusskurs.
      Eine heute erzeugte "1T"-Zeile haette den Referenzkurs vom 11.09. gegen den
      Schluss vom 14.09. gestellt und damit ueber drei Kalendertage gelaufen —
      exakt der Defekt vom 03.08. (Horizont zu lang). Wird nicht wiederholt.

  (C) KEINE AUFLOESUNG FAELLIG: Alle 1T-Zeilen mit Aufloesungsdatum <= 11.09. wurden
      im Samstagslauf (12.09.) aufgeloest. Geprueft: 0 offene 1T-Zeilen.
      Sa 12.09. und So 13.09. waren keine Handelstage.

  (D) 1W-ZEILEN NICHT BERUEHRT. Die 13 Zeilen vom 2026-09-12 mit Aufloesungsdatum
      2026-09-18 stehen unveraendert offen — Zustaendigkeit liegt beim Samstags-Task
      (portfolio-studien-prognose), nicht beim Tagesreport.

  (E) INTEGRITAET: keine Zeile geloescht, keine Zeile veraendert, keine Zeile
      angehaengt. Dieser Kommentarblock ist die einzige Aenderung an der Datei.

  (F) LAUFENDER STAND ZUR KENNTNIS (nur 1T, unveraendert seit 12.09., n = 299):
      Berater 181 = 60.5 % · Baseline 139 = 46.5 % · Vorsprung +14.0 Pp.
      Einschraenkung unveraendert (Learning 10.08.): effektive Stichprobe ist die
      Zahl der Handelstage (~30), nicht die der Zeilen (299).
      1W-Stand (Zustaendigkeit Samstag): 48/88 = 54.5 % gegen Baseline 48/88 = 54.5 %.

  (G) WERKZEUGZUSTAND, getestet statt behauptet (Regel 6 der Datenqualitaetsvorgabe):
      - Firecrawl-Scraper: unveraendert gesperrt ("This account has been banned") — heute erneut getestet.
      - Linux-Arbeitsumgebung: nicht erreichbar (Windows-Update vom 08.09.), heute erneut getestet.
      - Finanzfluss-Abruf ueber den eingebauten Browser: erreichbar, aber NICHT ANGEMELDET
        -> Zustand, kein Ausfall (Learning 11.09. (4)). Meister im Report um einen
        angemeldeten Tab gebeten.
      - finviz: FUNKTIONIERT, inklusive Screener-Sammelabfrage (19 Ticker in einem Aufruf),
        Group Screener (Sektoren) und Futures-Seite (VIX/Brent/WTI/Gold). Siehe Learning 13.09. (1).
      - stockanalysis.com: funktioniert (Kurshistorie, fuer die P74-Aufloesung genutzt).
      - cnn.com/markets/fear-and-greed: gesperrt ("Content Unavailable For Legal Reasons")
        -> Fear & Greed heute nicht erhebbar. Werkzeugbefund, kein Marktbefund.
-->

<!-- LAUF 2026-09-14 (Montag, Handelstag) - 13 NEUE 1T-ZEILEN, KEINE AUFLOESUNG FAELLIG
  LAUFZEITPUNKT: ~07:20 MESZ. SAUBERES FENSTER (06:00-09:00 MESZ):
  US-Handel geschlossen (22:00 Vortag), EU-Handel noch nicht eroeffnet (09:00).
  ALLE 13 ZEILEN SIND ECHTE PROGNOSEN, KEINE NOWCASTS. Erstmals seit Wochen.
  (Learning 04.08. / 06.08.)

  (A) DUBLETTENPRUEFUNG vor Erzeugung (Regel Learning 11.09. (5)):
      Datei auf Zeilen mit Datum 2026-09-14 und Horizont 1T geprueft. ERGEBNIS: keine
      vorhanden -> Erzeugung zulaessig.

  (B) AUFLOESUNG: KEINE FAELLIG. Letzter 1T-Satz (11.09.) wurde am 12.09. aufgeloest;
      Sa 12.09. und So 13.09. waren keine Handelstage, es wurde nichts erzeugt.
      Geprueft: 0 offene 1T-Zeilen vor diesem Lauf.

  (C) *** QUELLENFESTLEGUNG - die seit 12.09. offene Zusage ist hiermit erledigt ***
      Learning 12.09. (3) forderte: je Asset genau EINE Primaerquelle mit dokumentiertem
      Handelsplatz, verbindlich fuer Morgen- UND Wochenlauf, festgeschrieben in
      studien-universum.md. Ab heute gilt:
        SP500                      -> S&P-Cash-Index, Schlusskurs (Reuters/FXEmpire)
        MSCIWorld                  -> onvista, "MSCI DAILY USD", WKN A3DR38   [WECHSEL]
        Vanguard FTSE All-World    -> stockanalysis.com, ETR:VWCE (Xetra, EUR) [WECHSEL]
        Amundi Nasdaq-100          -> onvista, LU1829221024, gettex (EUR)      [WECHSEL]
        HSBC MSCI EM               -> stockanalysis.com, ETR:H4Z3 (Xetra, EUR)
        Amundi MSCI World          -> stockanalysis.com, ETR:MWRE (Xetra, EUR)
        AAPL/UNH/ASML/PEP/ADBE/META/TTWO -> finviz, US-Schluss in USD (ASML = US-ADR)
      *** DREI EINMALIGE QUELLENWECHSEL, HIER AUSDRUECKLICH MARKIERT STATT STILL ***
      Betroffen: MSCIWorld, All-World, Amundi Nasdaq-100. Ohne diesen Schnitt haette
      die Reihe weiter zu einem messbaren Anteil Quellendifferenzen statt Prognoseguete
      gemessen (1W nutzte bereits andere Quellen als 1T). Der Bruch liegt in DIESER
      Zeile und ist datiert; alle spaeteren Zeilen sind wieder vergleichbar.
      HINWEIS: Bei VWCE bestaetigt der Wechsel die Konsistenz sogar - 166.86 - 1.60 =
      165.26 = exakt der am 11.09. geloggte 1T-Referenzkurs. Die Quelle war also
      schon immer die richtige; falsch war der Ist-Kurs aus dem Tracker (166.67).

  (D) RUECKRECHNUNGS-CHECK aller 13 Referenzkurse - ALLE BESTANDEN:
      SP500     7656.98 / 1.0086 = 7591.69  (geloggter Vortagesschluss 7591.70)  OK
      MSCIWorld 4937.32 - 31.44  = 4905.88  (onvista, +0.64 %)                   OK
      VWCE      166.86  - 1.60   = 165.26   (= geloggte 1T-Referenz vom 11.09.)  OK
      ANX/gettex 103.12 - 1.02   = 102.10   (onvista, +1.00 %)                   OK
      H4Z3      16.44   - 0.18   = 16.26    (+1.10 %)                            OK
      MWRE      159.06  - 1.43   = 157.63   (+0.90 %)                            OK
      AAPL      332.27 / 1.0175  = 326.55   (Ist 11.09. 326.57)                  OK
      UNH       379.09 / 0.9763  = 388.29   (388.28)                             OK
      ASML      1698.30 / 1.0064 = 1687.50  (1687.43)                            OK
      PEP       136.32 / 0.9976  = 136.65   (136.65)                             OK
      ADBE      252.23 / 1.0137  = 248.82   (248.83)                             OK
      META      648.03 / 1.0057  = 644.36   (644.38)                             OK
      TTWO      215.47 / 0.9931  = 216.97   (216.96)                             OK

  (E) KONFIDENZ-BEGRUENDUNG - Spanne 53-65, 12 von 13 Zeilen DOWN (einzige UP-Zeile: PEP).
      *** DIESE EINSEITIGKEIT WIRD AUSDRUECKLICH OFFENGELEGT. ***
      Sie ist NICHT die Fehlerstruktur vom 10./11.09. (Richtungsannahme aus einer
      Trendbeobachtung), sondern beruht auf BEREITS REALISIERTEN Tatsachen, die zum
      Erzeugungszeitpunkt beobachtbar waren, und laeuft AUSDRUECKLICH GEGEN die
      Baseline (die fuer 10 von 13 Werten UP lautet):
        - Asien bereits geschlossen und gefallen: SoftBank -13.2 %, Kioxia -9.8 %,
          SK Hynix -5.3 %, Tokyo Electron -3.7 %, Samsung -3.7 %, TSMC -1.2 %,
          KOSPI -2.1 %, Nikkei -0.8 %, CSI300 -0.4 % (Reuters, 14.09.)
        - S&P-Futures -0.4 bis -0.51 %, Nasdaq-Futures -1.1 bis -1.24 %
        - Brent +2.6 % auf 107.36 USD; Oman-Treffen zu Hormus VERSCHOBEN
        - 10J-Rendite 4.974 %, FOMC am 16.09. mit 86 % Erhoehungswahrscheinlichkeit
      ABER: Es sind KEINE 13 unabhaengigen Beobachtungen, sondern im Kern EINE Wette
      auf einen Risk-off-Montag. Bei der Auswertung als Cluster behandeln
      (Learning 10.08.).
      DECKELUNG NACH LEARNING 12.09. (2): Index-Futures sind ein Praediktor fuer die
      EROEFFNUNG, nicht fuer den SCHLUSS. Genau dieser Fehler kostete P78. Deshalb
      liegt KEINE der reinen Futures-getriebenen Zeilen ueber 60.
      HOECHSTE KONFIDENZ 65: HSBC MSCI EM. Grund ist kein Marktgefuehl, sondern dass
      die Ursache bereits ein ABGESCHLOSSENER Kurs ist - Samsung, SK Hynix und TSMC
      sind Indexschwergewichte und haben heute in Asien bereits geschlossen, waehrend
      der ETF noch nicht gehandelt hat. Das ist die sauberste Evidenzlage des Satzes.
      UNH DOWN 60 mit MECHANISCHER Begruendung: heute EX-DIVIDENDE (finviz, Ex-Date
      14.09.2026, ~2.27 USD Quartalsdividende = ~0.60 % des Kurses). Der Referenz-
      und der Ist-Kurs sind beide ROHkurse, der Abschlag wirkt also voll. Erstmals
      wird in dieser Reihe ein Ex-Dividenden-Effekt als eigener Mechanismus genutzt.
      PEP UP 54: die EINZIGE UP-Zeile des Satzes. Begruendung: Basiskonsum an einem
      Risk-off-Tag. Bewusst niedrig, weil der hohe Oelpreis ueber die Tankstellen-
      Impulskaeufe gegen PEP wirkt - zwei Kraefte in entgegengesetzte Richtung.
      ADBE DOWN 55 / TTWO DOWN 53 / AAPL DOWN 54: schwach begruendet, entsprechend
      niedrige Konfidenz. Bei AAPL ausdruecklich geprueft, dass es KEIN
      Gegenbewegungs-Reflex nach +1.75 % ist (Learning 11.09. (2)) - die Begruendung
      ist der Marktkontext, nicht Mean Reversion.

  (F) EX-DIVIDENDEN-PRUEFUNG im Fenster 11.-14.09. ueber die finviz-Tickerseiten:
      UNH Ex-Date 14.09.2026 (GEFUNDEN, in die Prognose eingebaut).
      AAPL, ASML, PEP, ADBE, META, TTWO: kein Ex-Termin im Fenster.

  (G) KORRELATIONSKENNZEICHNUNG: Die Zeilen ADBE/NOW-Seite gegen AMD/ASML-Seite sind
      dieselbe Analyse wie P81 im prognosen-log, die HSBC-EM-Zeile dieselbe wie P80.
      Bei Fehlschlag ist das EIN Fehler, nicht mehrere (Learning 12.09. (2)).

  (H) INTEGRITAET: keine Zeile geloescht, keine bestehende Zeile veraendert, keine
      1W-Zeile beruehrt (13 Zeilen vom 12.09. bleiben offen, Zustaendigkeit Samstag).
      Nur angehaengt.
-->
2026-09-14 | Opus-5 | SP500 | 1T | DOWN | 58 | 7656.98 | UP | 2026-09-14 | RICHTIG | 7619.98
2026-09-14 | Opus-5 | MSCIWorld | 1T | DOWN | 58 | 4937.32 | UP | 2026-09-14 | RICHTIG | 4910.28
2026-09-14 | Opus-5 | Vanguard FTSE All-World | 1T | DOWN | 57 | 166.86 | UP | 2026-09-14 | RICHTIG | 166.22
2026-09-14 | Opus-5 | Amundi Nasdaq-100 | 1T | DOWN | 60 | 103.12 | UP | 2026-09-14 | RICHTIG | 102.82
2026-09-14 | Opus-5 | HSBC MSCI EM | 1T | DOWN | 65 | 16.44 | UP | 2026-09-14 | RICHTIG | 16.07
2026-09-14 | Opus-5 | Amundi MSCI World | 1T | DOWN | 57 | 159.06 | UP | 2026-09-14 | RICHTIG | 158.77
2026-09-14 | Opus-5 | AAPL | 1T | DOWN | 54 | 332.27 | UP | 2026-09-14 | FALSCH | 333.08
2026-09-14 | Opus-5 | UNH | 1T | DOWN | 60 | 379.09 | DOWN | 2026-09-14 | FALSCH | 383.55
2026-09-14 | Opus-5 | ASML | 1T | DOWN | 60 | 1698.30 | UP | 2026-09-14 | RICHTIG | 1575.15
2026-09-14 | Opus-5 | PEP | 1T | UP | 54 | 136.32 | DOWN | 2026-09-14 | RICHTIG | 136.34
2026-09-14 | Opus-5 | ADBE | 1T | DOWN | 55 | 252.23 | UP | 2026-09-14 | FALSCH | 265.60
2026-09-14 | Opus-5 | META | 1T | DOWN | 55 | 648.03 | UP | 2026-09-14 | FALSCH | 665.60
2026-09-14 | Opus-5 | TTWO | 1T | DOWN | 53 | 215.47 | DOWN | 2026-09-14 | FALSCH | 222.91

<!-- AUFLOESUNG 2026-09-15 des Satzes vom 14.09. (13 Zeilen, Horizont 1T)
     Ergebnis Tag: Berater 8/13 = 61,5 % · Baseline 3/13 = 23,1 %.
     Quellen je Asset gemaess studien-universum.md, Rueckrechnungs-Check durchgefuehrt:
       SP500     7619.98 (-37.00 / -0.48 %) Reuters/LSEG -> 7619.98+37.00 = 7656.98 = Referenz. BESTANDEN.
       MSCIWorld 4910.28 (-27.04 / -0.55 %) onvista A3DR38, MSCI DAILY USD; onvista weist Vortag
                 11.09. mit 4937.32 aus = Referenz. BESTANDEN.
       VWCE      166.22 (-0.38 %) stockanalysis ETR:VWCE Historie; Zeile 11.09. dort 166.86 = Referenz.
                 BESTANDEN.
       AmundiNDX 102.82 abgeleitet aus onvista gettex 15.09., 09:47:32: 102.340 EUR bei -0.480 EUR
                 -> Vortagesschluss 102.820. Gegen Referenz 103.12 = -0.29 %. HINWEIS: abgeleitet aus
                 Kurs+Veraenderung derselben Quelle/desselben Handelsplatzes, nicht direkt abgelesen.
       H4Z3      16.07 (-0.37 / -2.23 %) stockanalysis ETR:H4Z3, "Last updated Sep 14, 5:30 PM CET";
                 Previous Close dort 16.44 = Referenz. BESTANDEN.
       MWRE      158.77 (-0.30 / -0.19 %) stockanalysis ETR:MWRE, "At close Sep 14";
                 Previous Close dort 159.06 = Referenz. BESTANDEN.
       US-Aktien: finviz Quote-Feld "Prev Close" am 15.09., 05:52 ET (US-Handel geschlossen) — also der
                 direkt abgelesene Schlusskurs vom 14.09., NICHT aus dem Premarket zurueckgerechnet.
                 Vier Werte zusaetzlich gegen die Prozentangaben der finviz-Newstabelle geprueft:
                 ADBE +5.30 %, NOW +7.41 %, ASML -7.25 %, AMD -4.40 % — alle vier decken sich mit der
                 Rechnung aus Referenz- und Ist-Kurs. BESTANDEN.
     Keine 1W-Zeile angefasst. -->

<!-- LAUF 2026-09-15 (Dienstag, Handelstag) - 13 NEUE 1T-ZEILEN
     DUBLETTENPRUEFUNG (Regel 11.09. (5)): Datei vor der Erzeugung auf Zeilen mit Datum 2026-09-15
     und Horizont 1T geprueft. ERGEBNIS: keine vorhanden -> Erzeugung zulaessig.
     LAUFZEITPUNKT ~12:00 MESZ — AUSSERHALB des sauberen Fensters (06:00-09:00 MESZ).
     Zeilenweise Kennzeichnung nach Learning 06.08.:
       SAUBER (Boerse geschlossen, keine Tagesinformation): SP500, AAPL, UNH, ASML, PEP, ADBE, META, TTWO
       NOWCAST-BELASTET (europaeische Sitzung laeuft seit 09:00): VWCE, Amundi Nasdaq-100,
         Amundi MSCI World, MSCIWorld (Fixing 16:00 CET), HSBC MSCI EM
       Konkret beobachtet und damit in die Prognose eingeflossen: VWCE 165.16 (-0.64 %) um 11:37 CET,
       Amundi NDX gettex 102.34 (-0.47 %) um 09:47 CET. Diese fuenf Zeilen sind fuer die Auswertung
       als belastet zu behandeln.
     Baseline = Richtung der letzten Tagesbewegung (14.09.).
     KOHAERENZ: 10 von 13 Zeilen lauten DOWN und haengen an EINEM Szenario (10J-Rendite ueber 5 %,
     Brent ueber 108 $, FOMC-Vorabend mit 92 % eingepreister Erhoehung). Das sind Ausgaben EINER
     Analyse, keine 13 unabhaengigen Belege — bei einem Fehlschlag ist es ein Fehler, nicht dreizehn. -->

2026-09-15 | Opus-5 | SP500 | 1T | DOWN | 57 | 7619.98 | DOWN | 2026-09-15 | RICHTIG | 7585.73
2026-09-15 | Opus-5 | MSCIWorld | 1T | DOWN | 62 | 4910.28 | DOWN | 2026-09-15 | RICHTIG | 4887.33
2026-09-15 | Opus-5 | Vanguard FTSE All-World | 1T | DOWN | 65 | 166.22 | DOWN | 2026-09-15 | RICHTIG | 165.36
2026-09-15 | Opus-5 | Amundi Nasdaq-100 | 1T | DOWN | 62 | 102.82 | DOWN | 2026-09-15 | RICHTIG | 102.18
2026-09-15 | Opus-5 | HSBC MSCI EM | 1T | DOWN | 60 | 16.07 | DOWN | 2026-09-15 | RICHTIG | 15.99
2026-09-15 | Opus-5 | Amundi MSCI World | 1T | DOWN | 62 | 158.77 | DOWN | 2026-09-15 | RICHTIG | 158.02
2026-09-15 | Opus-5 | AAPL | 1T | DOWN | 55 | 333.08 | UP | 2026-09-15 | RICHTIG | 331.34
2026-09-15 | Opus-5 | UNH | 1T | UP | 53 | 383.55 | UP | 2026-09-15 | FALSCH | 375.93
2026-09-15 | Opus-5 | ASML | 1T | UP | 55 | 1575.15 | DOWN | 2026-09-15 | RICHTIG | 1591.48
2026-09-15 | Opus-5 | PEP | 1T | UP | 53 | 136.34 | UP | 2026-09-15 | FALSCH | 135.50
2026-09-15 | Opus-5 | ADBE | 1T | DOWN | 56 | 265.60 | UP | 2026-09-15 | RICHTIG | 257.76
2026-09-15 | Opus-5 | META | 1T | DOWN | 55 | 665.60 | UP | 2026-09-15 | FALSCH | 670.24
2026-09-15 | Opus-5 | TTWO | 1T | DOWN | 54 | 222.91 | UP | 2026-09-15 | RICHTIG | 211.91

<!-- AUFLOESUNG 2026-09-16 des Satzes vom 15.09. (13 Zeilen, Horizont 1T)
     Ergebnis Tag: Berater 10/13 = 76,9 % · Baseline 7/13 = 53,8 % · Vorsprung +23,1 Pp.
     Aufschluesselung: Indizes/ETFs 6/6 richtig · US-Einzelaktien 4/7 richtig
       (richtig AAPL, ASML, ADBE, TTWO · falsch UNH, PEP, META).
     Quellen und FELDER gemaess studien-universum.md und Learning 15.09. (2):
       SP500     7585.73 (-0.45 %) Reuters/LSEG-Marktbericht -> 7585.73 / (1-0.0045) = 7619.99
                 = Referenz 7619.98. BESTANDEN.
       MSCIWorld 4887.33 (-22.95 / -0.47 %) onvista A3DR38, MSCI DAILY USD; onvista weist Vortag
                 14.09. mit 4910.28 aus = Referenz. BESTANDEN.
       VWCE      165.36 abgeleitet aus stockanalysis ETR:VWCE am 16.09., 13:01 CET: 166.16 bei
                 +0.80 EUR -> Vortagesschluss 165.36. Gegen Referenz 166.22 = -0.52 %. HINWEIS:
                 abgeleitet aus Kurs+Veraenderung derselben Quelle/desselben Handelsplatzes.
       AmundiNDX 102.18 abgeleitet aus onvista gettex am 16.09.: 102.640 EUR bei +0.460 EUR
                 -> Vortagesschluss 102.180. Gegen Referenz 102.82 = -0.62 %. Gleicher Hinweis.
       H4Z3      15.99 (-0.54 %) stockanalysis ETR:H4Z3, "Last updated: Sep 15, 5:30 PM CET";
                 15.99 / (1-0.0054) = 16.077 = Referenz 16.07. BESTANDEN.
       MWRE      158.02 (-0.75 / -0.47 %) stockanalysis ETR:MWRE, "At close: Sep 15";
                 158.02 / (1-0.0047) = 158.77 = Referenz. BESTANDEN.
       US-Aktien: finviz Quote, FELD "Prev Close", abgerufen 16.09. um 07:14 ET.
                 HANDELSZUSTAND DER QUELLE BEIM ABRUF: VORBOERSLICH (US-Kassamarkt geschlossen)
                 -> "Prev Close" ist der Schlusskurs vom 15.09., "Price" waere der Vorboersenstand
                 vom 16.09. gewesen. Feldtrennung nach Learning 15.09. (2) eingehalten.
     Keine 1W-Zeile angefasst, keine bestehende Zeile geloescht oder umsortiert. -->

<!-- LAUF 2026-09-16 (Mittwoch, Handelstag) - 13 NEUE 1T-ZEILEN
     DUBLETTENPRUEFUNG (Regel 11.09. (5)): Datei vor der Erzeugung auf Zeilen mit Datum 2026-09-16
     und Horizont 1T geprueft. ERGEBNIS: keine vorhanden -> Erzeugung zulaessig.
     LAUFZEITPUNKT ~13:15 MESZ - AUSSERHALB des sauberen Fensters (06:00-09:00 MESZ).
     Zeilenweise Kennzeichnung nach Learning 06.08.:
       SAUBER (US-Kassamarkt geschlossen): SP500, AAPL, UNH, ASML, PEP, ADBE, META, TTWO
       NOWCAST-BELASTET (europaeische Sitzung laeuft seit 09:00): VWCE, Amundi Nasdaq-100,
         Amundi MSCI World, MSCIWorld (Fixing 16:00 CET), HSBC MSCI EM
       Konkret beobachtet und damit eingeflossen: VWCE 166.16 (+0.48 %) um 13:01 CET,
       Amundi NDX gettex 102.64 (+0.45 %), HSBC EM im Tracker +0.96 %.
     BESONDERHEIT DES TAGES: Der Aufloesungszeitpunkt aller acht US-Zeilen liegt HINTER der
     FOMC-Entscheidung (20:00 MESZ) und der Pressekonferenz (20:30 MESZ). Die Trefferquote dieses
     Satzes misst daher zu einem grossen Teil die Einschaetzung EINES Ereignisses.
     Baseline = Richtung der letzten Tagesbewegung (15.09.).
     JE-EINZELWERT-MECHANISMUS (neue Pflicht, Learning 15.09. (1)) - erwartete Branchenspreizung
     liegt heute ueber dem Zweifachen der erwarteten Indexbewegung, deshalb KEINE Ableitung aus
     der Marktthese; jede US-Zeile traegt eine eigene Begruendung:
       AAPL  UP 54  - Consumer Electronics staerkste Tech-Branche der Woche (+5.04 %);
                      Citi sieht kuerzere Ersatzzyklen. Gegen die Zeile: Speicherpreiserhoehung.
       UNH   DOWN 53- drei von vier Sitzungen im Minus, TPG/WellMed-Margenfrage unaufgeloest,
                      angekuendigter Berichtstermin lenkt Aufmerksamkeit auf die Care Ratio.
       ASML  UP 62  - Halbleiterausruester vorboerslich +1.93 %; "110-Machine Bottleneck"
                      (Angebots-, kein Nachfrageproblem); im Depot heute bereits +2.74 %.
       PEP   UP 53  - fallendes Oel entlastet den Frachtkanal; Consumer Defensive +1.34 % Woche.
       ADBE  DOWN 57- Software-Application vorboerslich -0.18 %; Adobe gibt den Montagssprung
                      seit zwei Sitzungen zurueck; im Depot heute -1.22 %.
       META  UP 54  - Zuckerbergs Gegenposition (Pruefung statt Verlangsamung) ist die fuer Meta
                      billigste Variante; staerkster Wochenwert des Depots.
       TTWO  DOWN 52- BEWUSST nahe am Muenzwurf: die Ursache des -4.93 % ist NICHT ermittelbar
                      (Learning 16.09. (2)). Ohne Ursache keine These, also keine Konfidenz.
     KOHAERENZ: 10 von 13 Zeilen lauten UP und haengen an EINEM Szenario (Fed-Erleichterung,
     fallendes Oel, stabilisierende Renditen). Das sind Ausgaben EINER Analyse, keine 13
     unabhaengigen Belege - bei einem Fehlschlag ist es ein Fehler, nicht dreizehn.
     Der Satz laeuft dabei stark GEGEN die Baseline (11 von 13 Baselines lauten DOWN). -->

2026-09-16 | Opus-5 | SP500 | 1T | UP | 57 | 7585.73 | DOWN | 2026-09-16 | FALSCH | 7551.81 
2026-09-16 | Opus-5 | MSCIWorld | 1T | UP | 60 | 4887.33 | DOWN | 2026-09-16 | FALSCH | 4876.28 
2026-09-16 | Opus-5 | Vanguard FTSE All-World | 1T | UP | 60 | 165.36 | DOWN | 2026-09-16 | RICHTIG | 166.30 
2026-09-16 | Opus-5 | Amundi Nasdaq-100 | 1T | UP | 60 | 102.18 | DOWN | 2026-09-16 | RICHTIG | 102.72 
2026-09-16 | Opus-5 | HSBC MSCI EM | 1T | UP | 60 | 15.99 | DOWN | 2026-09-16 | RICHTIG | 16.15 
2026-09-16 | Opus-5 | Amundi MSCI World | 1T | UP | 59 | 158.02 | DOWN | 2026-09-16 | RICHTIG | 158.83 
2026-09-16 | Opus-5 | AAPL | 1T | UP | 54 | 331.34 | DOWN | 2026-09-16 | RICHTIG | 332.41 
2026-09-16 | Opus-5 | UNH | 1T | DOWN | 53 | 375.93 | DOWN | 2026-09-16 | RICHTIG | 375.26 
2026-09-16 | Opus-5 | ASML | 1T | UP | 62 | 1591.48 | UP | 2026-09-16 | RICHTIG | 1602.22 
2026-09-16 | Opus-5 | PEP | 1T | UP | 53 | 135.50 | DOWN | 2026-09-16 | FALSCH | 134.34 
2026-09-16 | Opus-5 | ADBE | 1T | DOWN | 57 | 257.76 | DOWN | 2026-09-16 | RICHTIG | 250.50 
2026-09-16 | Opus-5 | META | 1T | UP | 54 | 670.24 | UP | 2026-09-16 | RICHTIG | 673.31 
2026-09-16 | Opus-5 | TTWO | 1T | DOWN | 52 | 211.91 | DOWN | 2026-09-16 | RICHTIG | 211.81 



<!-- ERZEUGUNG 2026-09-17 (Donnerstag, Handelstag) — Modell Opus-5, Lauf ~09:40-10:10 MESZ
     REFERENZKURSE = Schlusskurse 16.09., je Asset aus der in studien-universum.md
     festgeschriebenen Primaerquelle und dem festgeschriebenen FELD (Learning 15.09. (2)):
       US-Werte: finviz, Handelszustand GESCHLOSSEN (Zeitstempel "Thu SEP 17 3:40 AM" ET,
         vor Beginn des vorboerslichen Handels) -> Feld "Price" IST hier der Schluss vom 16.09.
         Rueckrechnung Price/(1+Change) fuer alle 7 US-Werte durchgefuehrt und BESTANDEN,
         Abweichung <= 0.01 USD gegen die am 16.09. geloggten Referenzkurse.
       VWCE / H4Z3 / MWRE: stockanalysis.com Xetra, Datum der Quellenzeile je einzeln geprueft
         (VWCE "Previous Close" bei Live-Kurs 17.09.; H4Z3 "Last updated Sep 16, 5:30 PM CET";
          MWRE "At close: Sep 16").
       MSCIWorld: onvista A3DR38 MSCI DAILY USD, "gestern 16:00" = 4876.28; die Seite weist
         den Vortag mit 4887.33 aus = exakt der am 16.09. geloggte Referenzkurs.
       Amundi Nasdaq-100: gettex-Kurs ABGELEITET (103.760 aktuell minus 1.040 Tagesveraenderung
         = 102.72), nicht aus einem "Vortag"-Feld abgelesen. Gegenprobe LS Exchange identisch,
         Tradegate 102.80 (Handelsplatzdifferenz). ALS ABLEITUNG GEKENNZEICHNET.

     NOWCAST-KENNZEICHNUNG: Die 5 europaeischen Zeilen (MSCIWorld, VWCE, Amundi Nasdaq-100,
     HSBC MSCI EM, Amundi MSCI World) wurden erzeugt, als Xetra/gettex bereits ~40 Minuten
     handelten und bereits im Plus standen (VWCE 167.16 = +0.52 %, Amundi Nasdaq gettex
     103.76 = +1.01 %, HSBC EM 16.21 = +0.97 %). DIESE FUENF ZEILEN SIND NOWCASTS und in der
     Auswertung getrennt zu behandeln. Die 8 US-Zeilen sind sauber (US-Boersen geschlossen).

     LAGE: Fed hat am 16.09. einstimmig um 25 Bp auf 3.75-4.00 % erhoeht; Dot Plot zeigt bei
     16 von 18 Projektionen eine weitere Erhoehung. Warshs Pressekonferenz drehte den Tag
     (Dow -1.21 %, S&P -0.45 %, 10J-Rendite 5.016 %). HEUTE FRUEH Gegenbewegung: S&P-Futures
     +0.84 %, Nasdaq-100-Futures +1.01 %, DAX +0.78 %, VIX 18.25 (-2.54 %), ALLE Anleihe-
     Futures im Plus (10J +0.19 %, 30J +0.32 %) -> fallende lange Renditen, Brent -1.74 %
     nach Meldung zur Wiederherstellung der saudischen East-West-Pipeline.
     Fear & Greed 29 ("Fear") bei nur -3.25 % Abstand zum 52-Wochen-Hoch.

     EINZELBEGRUENDUNGEN (Learning 15.09. (1): je Einzelwert ein eigener Mechanismus,
     keine Ableitung aus der Marktthese allein):
       SP500  UP 62  - Futures +0.84 %; Renditeentspannung ist der Treiber. GEGEN die Zeile:
                       Erstantraege + Philly-Fed um 14:30 MESZ liegen VOR dem Schluss.
       MSCIWorld UP 68 - hoechste Konfidenz des Satzes, und zwar STRUKTURELL: das 16:00-Fixing
                       liegt vor der US-Hauptsitzung und ist damit weitgehend durch die schon
                       abgeschlossenen Sitzungen in Asien (Nikkei +0.49 %) und Europa
                       (DAX +0.78 %, EuroStoxx +0.78 %) determiniert. Learning 17.09. (2).
       VWCE  UP 65   - NOWCAST, steht bereits +0.52 %. Restrisiko: 1.5 h US-Ueberlappung
                       bis zum Xetra-Schluss 17:30.
       Amundi Nasdaq-100 UP 66 - NOWCAST, steht bereits +1.01 %; zinsempfindlichste Position
                       des Depots, groesster Nutznieser fallender langer Renditen.
       HSBC MSCI EM UP 64 - NOWCAST, +0.97 %; doppelt entlastet (schwaechere US-Renditen
                       stuetzen EM-Waehrungen, fallendes Oel entlastet die Importeure).
       Amundi MSCI World UP 64 - NOWCAST, analog VWCE, engerer Titelkreis.
       AAPL  UP 55   - schwaechste eigene Begruendung des US-Blocks und so gekennzeichnet:
                       Consumer Electronics nur +0.29 % am 16.09.; offener Gegenpunkt sind die
                       akzeptierten Samsung-Speicherpreise. Nasdaq-Rueckenwind, wenig Eigenes.
       UNH   UP 56   - Healthcare war am 16.09. mit +0.03 % der stabilste Sektor an einem
                       -0.45-%-Tag; Care Ratio 86.7 % (von 89.4 %) und erhoehte EPS-Guidance
                       sind eigene, unternehmensbezogene Stuetzen. VERMERK: meine letzten
                       zwei UNH-Zeilen lagen falsch, deshalb keine hoehere Zahl.
       ASML  UP 66   - staerkste Eigenbegruendung: Halbleiter +0.75 % und SMH +0.64 % am 16.09.,
                       Nasdaq-Futures +1.01 %. Amsterdam steht heute +2.18 % - das ist EVIDENZ
                       ueber die Richtung, wird aber NICHT auf den ADR uebertragen
                       (Learning 04.08.); die Zeile laeuft gegen den US-ADR in USD.
       PEP   UP 52   - BEWUSST nahe am Muenzwurf. Mechanismus: fallende lange Renditen stuetzen
                       den Dividendenwert, fallendes Oel den Frachtkanal (verzoegert).
                       GEGEN mich, ausdruecklich: meine letzten ZWEI PEP-Zeilen lauteten
                       beide UP und beide waren falsch (-0.62 %, -0.86 %). Zwei Fehlschlaege
                       in derselben Richtung sind ein Kalibrierungssignal, kein Zufall -
                       deshalb 52 und nicht 56. FedEx-Zahlen heute Abend liegen NACH dem Schluss.
       ADBE  UP 55   - Gegenbewegungszeile nach drei Verlusttagen: KGV 13.97, billigster Wert
                       im Depot, Nasdaq-Futures +1.01 %. GEGEN sich selbst: die qualitative
                       Prognose P86 sagt fuer heute einen Schluss UNTER 252.23 $ voraus -
                       beide sind vereinbar (250.50 + 0.6 % liegt noch unter 252.23), aber der
                       Zielkorridor ist eng und das ist hier offen benannt.
       META  UP 58   - zweiter Tag relativer Staerke: +0.46 % am 16.09., WAEHREND der eigene
                       Sektor (Communication Services) -0.72 % machte. Eigene Staerke,
                       nicht Marktmitnahme.
       TTWO  UP 58   - einziger Wert mit einem TERMINIERTEN Eigenkatalysator heute:
                       Hauptversammlung, und der CEO hat den GTA-VI-Termin 19.11.2026 sowie
                       die FY27-Guidance 8.0-8.2 Mrd. $ zuletzt ausdruecklich bestaetigt.
                       OFFENGELEGT: nicht unabhaengig von meiner heutigen Kaufempfehlung
                       (Tranche 1, ~98 EUR) - dieselbe Information, zwei Ausgaben.

     KOHAERENZ, unmissverstaendlich: 13 von 13 Zeilen lauten UP. Das ist EINE Wette auf ein
     Entspannungsszenario (fallende lange Renditen tragen die Aktien), nicht ein Satz aus
     dreizehn unabhaengigen Belegen. Gehen sie gemeinsam schief, ist das EIN Fehlurteil.
     Der Satz laeuft dabei bei 6 von 13 Zeilen GEGEN die Baseline (7 Baselines lauten UP).
     Das entscheidende Einzelrisiko ist benennbar und terminiert: US-Erstantraege und
     Philly-Fed um 14:30 MESZ. Ein schwacher Arbeitsmarktwert waere hier KEINE gute
     Nachricht, sondern ein Stagflationssignal.

     ANGEWANDTES LEARNING 17.09. (2) - Schlusszeitpunkt relativ zum Ereignis:
       VOR dem 14:30-Datenblock schliesst keine Zeile. MSCIWorld schliesst 16:00 MESZ
       (1.5 h danach), die vier EUR-ETFs 17:30 MESZ, die acht US-Zeilen 22:00 MESZ.
       Damit ist der Datenblock fuer ALLE Zeilen ein zulaessiges Argument - anders als
       gestern, wo der Fed-Entscheid fuer 5 von 13 Zeilen zeitlich unerreichbar war. -->

2026-09-17 | Opus-5 | SP500 | 1T | UP | 62 | 7551.81 | DOWN | 2026-09-17 | RICHTIG | 7637.71 
2026-09-17 | Opus-5 | MSCIWorld | 1T | UP | 68 | 4876.28 | DOWN | 2026-09-17 | RICHTIG | 4922.10 
2026-09-17 | Opus-5 | Vanguard FTSE All-World | 1T | UP | 65 | 166.30 | UP | 2026-09-17 | RICHTIG | 167.66 
2026-09-17 | Opus-5 | Amundi Nasdaq-100 | 1T | UP | 66 | 102.72 | UP | 2026-09-17 | RICHTIG | 104.380 
2026-09-17 | Opus-5 | HSBC MSCI EM | 1T | UP | 64 | 16.15 | UP | 2026-09-17 | RICHTIG | 16.36 
2026-09-17 | Opus-5 | Amundi MSCI World | 1T | UP | 64 | 158.83 | UP | 2026-09-17 | RICHTIG | 159.97 
2026-09-17 | Opus-5 | AAPL | 1T | UP | 55 | 332.41 | UP | 2026-09-17 | RICHTIG | 337.00 
2026-09-17 | Opus-5 | UNH | 1T | UP | 56 | 375.26 | DOWN | 2026-09-17 | FALSCH | 375.21 
2026-09-17 | Opus-5 | ASML | 1T | UP | 66 | 1602.22 | UP | 2026-09-17 | RICHTIG | 1629.67 
2026-09-17 | Opus-5 | PEP | 1T | UP | 52 | 134.34 | DOWN | 2026-09-17 | FALSCH | 133.66 
2026-09-17 | Opus-5 | ADBE | 1T | UP | 55 | 250.50 | DOWN | 2026-09-17 | RICHTIG | 252.67 
2026-09-17 | Opus-5 | META | 1T | UP | 58 | 673.31 | UP | 2026-09-17 | RICHTIG | 682.31 
2026-09-17 | Opus-5 | TTWO | 1T | UP | 58 | 211.81 | DOWN | 2026-09-17 | FALSCH | 210.62 

<!-- Lauf 18.09.2026 (Freitag, Handelstag), ~12:15 MESZ. Referenzkurse = abgeschlossene Schlusskurse
     vom 17.09.; Aufloesungsdatum = Schluss 18.09. Datenlage: US-Boersen geschlossen (Abruf 06:00 ET,
     vorboerslich) -> alle sieben US-Zeilen sauber, Referenz aus finviz-Feld "Prev Close" bzw.
     Kurs minus Dollarveraenderung (Regel Learning 15.09. (2)). Die fuenf europaeischen Zeilen sind
     Nowcasts: Xetra/gettex handeln seit ~3,5 h. MSCIWorld-Referenz = onvista A3DR38 MSCI DAILY USD,
     Fixing 17.09. 16:00. VWCE-Referenz aus stockanalysis ETR:VWCE live 167.54 + 0.12 Tagesverlust
     abgeleitet (die Quelle stand im laufenden Handel) - als einzige abgeleitete Referenz gekennzeichnet.
     Mechanismus je US-Einzelwert einzeln benannt (Learning 15.09. (1)); erwartete Sektorspreizung
     vorboerslich ~1,3 Pp gegen eine erwartete Indexbewegung von ~0,2 % -> Quotient ~6,5, also ueber
     dem Zweifachen: die Marktthese allein traegt keine Einzelwertzeile.
     Sondersituation: heute ist grosser Verfallstag (Quadruple Witching) - mechanische Flows,
     Konfidenzen deshalb durchgehend gedeckelt. -->

2026-09-18 | Opus-5 | SP500 | 1T | UP | 56 | 7637.71 | UP | 2026-09-18 | RICHTIG | 7650.50
2026-09-18 | Opus-5 | MSCIWorld | 1T | UP | 58 | 4922.10 | UP | 2026-09-18 | FALSCH | 4913.98
2026-09-18 | Opus-5 | Vanguard FTSE All-World | 1T | UP | 55 | 167.66 | UP | 2026-09-18 | FALSCH | 167.14
2026-09-18 | Opus-5 | Amundi Nasdaq-100 | 1T | UP | 63 | 104.380 | UP | 2026-09-18 | RICHTIG | 105.300
2026-09-18 | Opus-5 | HSBC MSCI EM | 1T | UP | 60 | 16.36 | UP | 2026-09-18 | FALSCH | 16.29
2026-09-18 | Opus-5 | Amundi MSCI World | 1T | UP | 55 | 159.97 | UP | 2026-09-18 | FALSCH | 159.53
2026-09-18 | Opus-5 | AAPL | 1T | DOWN | 55 | 337.00 | UP | 2026-09-18 | RICHTIG | 336.13
2026-09-18 | Opus-5 | UNH | 1T | UP | 57 | 375.21 | DOWN | 2026-09-18 | RICHTIG | 376.90
2026-09-18 | Opus-5 | ASML | 1T | UP | 65 | 1629.67 | UP | 2026-09-18 | RICHTIG | 1679.92
2026-09-18 | Opus-5 | PEP | 1T | DOWN | 60 | 133.66 | DOWN | 2026-09-18 | RICHTIG | 129.75
2026-09-18 | Opus-5 | ADBE | 1T | DOWN | 66 | 252.67 | UP | 2026-09-18 | RICHTIG | 248.92
2026-09-18 | Opus-5 | META | 1T | UP | 57 | 682.31 | UP | 2026-09-18 | FALSCH | 665.75
2026-09-18 | Opus-5 | TTWO | 1T | DOWN | 62 | 210.62 | DOWN | 2026-09-18 | RICHTIG | 205.45

<!-- SAMSTAGSLAUF 2026-09-19 - NUR HORIZONT 1W (Zustaendigkeit laut Task-Definition)

  (A) DUBLETTENPRUEFUNG vor allem anderen (Regel Learning 11.09. (5)):
      Datei auf Zeilen mit Datum 2026-09-19 geprueft. ERGEBNIS: keine. Lauf freigegeben.

  (B) REFERENZKURSE = FREITAGSSCHLUSS 18.09.2026, je Asset aus der in
      studien-universum.md ab 14.09. verbindlich festgelegten Primaerquelle:
      SP500 7650.50 (Investing.com SPX/NYSE - siehe (D) 1.)
      MSCIWorld 4913.98 (onvista A3DR38, MSCI DAILY USD, Fixing 16:00)
      Vanguard FTSE All-World 167.14 / Amundi MSCI World 159.53 /
        HSBC MSCI EM 16.29 (stockanalysis.com, ETR:VWCE / ETR:MWRE / ETR:H4Z3, Xetra)
      Amundi Nasdaq-100 105.300 (onvista LU1829221024, gettex, 22:47:08)
      AAPL 336.13 / UNH 376.90 / ASML 1679.92 (US-ADR) / PEP 129.75 /
        ADBE 248.92 / META 665.75 / TTWO 205.45 (finviz-Screener, US-Schluss)

  (C) RUECKRECHNUNGS-CHECK: bestanden fuer alle 13 Werte. Ist-Kurs / (1 + Tages-
      veraenderung) ergibt jeweils exakt den Donnerstagsschluss, der in den
      1T-Zeilen vom 18.09. dieser Datei als Referenzkurs steht (AAPL 337.00,
      UNH 375.21, ASML 1629.67, PEP 133.66, ADBE 252.67, META 682.31,
      TTWO 210.62, MSCIWorld 4922.10, VWCE 167.66, MWRE 159.97, H4Z3 16.36,
      LU1829221024 104.380, SP500 7637.71/7637.76).

  (D) QUELLENLAGE BEIM AUFLOESEN DES 12.09.-SATZES, ausdruecklich benannt:
      1. MSCIWorld - ENTWARNUNG zum am 14.09. dokumentierten Quellenbruch.
         Der 12.09.-Referenzkurs 4937.32 stammt aus Investing.com (MIWO00000PUS),
         der Ist-Kurs aus onvista (A3DR38, MSCI DAILY USD). Gegenprobe heute
         gemacht: Investing.com fuehrt fuer den 11.09. 4937.32, fuer den 17.09.
         4922.10 und fuer den 18.09. 4913.98 - Zahl fuer Zahl identisch mit onvista.
         Die beiden Quellen bilden DIESELBE Reihe ab. Der am 12.09. befuerchtete
         Bruch betraf boerse.de (XC0009692739), nicht diese beiden. Die Zeile ist
         damit sauber und braucht keinen Eintrag in batterie-ausnahmen.md.
      2. Amundi Nasdaq-100 - HANDELSPLATZBRUCH, bleibt bestehen. Referenzkurs
         103.38 stammt aus stockanalysis ETR:LYMS (Xetra), der Ist-Kurs 105.300
         aus onvista/gettex. Richtung unter BEIDEN Lesarten identisch: Xetra-
         intern 103.38 -> 104.54 = +1.12 %, gemischt +1.86 %. Richtung zaehlt
         (robust), Hoehe als unsicher markiert. Dies ist die LETZTE betroffene
         Zeile - der heutige Satz setzt Referenz und Ist beide auf gettex.
      3. HSBC MSCI EM - Referenz 16.4395 stammt aus der Kurshistorie von
         live.deutsche-boerse.com, Ist aus stockanalysis ETR:H4Z3. Gegenprobe:
         stockanalysis fuehrt fuer den 11.09. ebenfalls 16.44 - gleicher
         Handelsplatz (Xetra), gleicher Wert. Vergleich haelt.
      4. SP500 - Referenz 7656.98 und Ist 7650.50 stammen beide aus der
         SPX-Reihe von Investing.com (Gegenprobe: Investing.com fuehrt fuer den
         11.09. exakt 7656.98, den geloggten Referenzkurs). Die Zeile ist
         quellenintern konsistent. ABER: die Bewegung betraegt -0.09 %, also
         6.48 Punkte - das liegt UNTERHALB der am 12.09. dokumentierten
         Quellenspannweite von 6 Punkten zwischen AP, Deutsche Boerse und
         24/7-Wall-St. Die Zeile wird als FALSCH gewertet (Regel: Richtung
         gegenueber Referenzkurs), enthaelt aber nach Learning 18.09. (2)
         keine verwertbare Information. In der Bachelorarbeit gehoert sie in
         die Gruppe "unterhalb der Messgrenze".

  (E) AUFLOESUNG DES 12.09.-SATZES: 13 Zeilen, ausschliesslich die Spalten
      Ergebnis und Ist-Kurs gesetzt - keine andere Spalte, keine Reihenfolge,
      keine 1T-Zeile beruehrt. Zeilenzahl der Datei vor und nach dem Schreiben
      identisch (3074).
      Berater 8/13 = 61.5 % | Random Walk 10/13 = 76.9 % | Drift "immer UP" 5/13 = 38.5 %.
      Laufend ueber alle 101 aufgeloesten 1W-Zeilen:
      Berater 56/101 = 55.4 % | Random Walk 58/101 = 57.4 % | Drift 54/101 = 53.5 %.
      BEFUND, der protokolliert gehoert, WEIL er unguenstig ist: Der Random Walk
      liegt auf 1W jetzt VOR dem Berater (+2.0 Pp). Am 12.09. stand es noch
      48/88 zu 48/88, also Gleichstand. Die Fortschreibung des Learnings
      12.09. (4) lautet damit nicht mehr "kein Vorsprung", sondern "Rueckstand".

  (F) MARKTLAGE ZUM PROGNOSEZEITPUNKT (Fakten, Stand Freitagsschluss):
      - Fed hat am 16.09. auf 3.75-4.00 % erhoeht, Beschluss 12-0. Warsh:
        "timelier return" zu 2 %. 16 von 18 Projektionen sehen eine weitere
        Erhoehung 2026. Im Fenster 21.-25.09. liegt KEINE FOMC-Sitzung.
      - 10-jaehrige US-Rendite 4.996 % (+4.9 Bp), Tageshoch 5.008 %,
        52-Wochen-Hoch 5.041 %. Das Zinsniveau wirkt ueber die ganze Woche.
      - Dollar mit der staerksten Woche seit Juni. EUR/USD 1.1486 am 18.09.
        gegen 1.1595 am 11.09. = -0.94 %. Fuer die vier EUR-notierten ETFs auf
        US-Basiswerte ist das rechnerischer Rueckenwind, fuer EM Gegenwind.
      - Oel: WTI 99.53 $ (-2.34 %), Brent 103.19 $ (-1.56 %), zweiter
        Entspannungstag. Tagesspanne WTI aber 95.71-103.48 $ = 8.1 % - die
        Entspannung ist nicht stabil. Gegenbefund: US-Diesel auf Allzeithoch.
      - Marktbreite am Freitag extrem eng: genau EIN Sektor von elf im Plus
        (Technology +0.84 %). Spreizung 2.11 Pp gegen 0.17 % Indexbewegung,
        Quotient ~12 - Rotationstag, kein Markttag.
      - Sentiment widerspruechlich: CNN Fear & Greed 29 ("Fear") bei einem
        VIX von 14.81 (-4.08 %). Angstwert ohne Volatilitaet.
      - S&P 500 2.13 % unter dem 52-Wochen-Hoch.
      - Terminierte Ereignisse IM FENSTER: Trump-Xi-Gipfel am 24.09.; neue
        China-Zoelle sind bis nach dem Gipfel aufgeschoben (Bloomberg 17.09.).
      - KEINE Quartalszahlen im Fenster. Naechster Termin der 13 Werte:
        PepsiCo 08.10., UnitedHealth 13.10., ASML 14.10. (finviz-Earnings-Feld).
      - ⬜ NICHT ERHOBEN: der vollstaendige Makrokalender 21.-25.09. Der
        Wochenkalender von investrade.com ist fuer den eingebauten Browser
        nicht freigegeben, der Investing.com-Kalender lud die Folgewoche nicht.
        Das ist eine Aussage ueber meine Recherche, nicht ueber die Welt
        (Learning 06.09.).

  (G) KOHAERENZ-CHECK (Learning 05.09.: GRUPPIEREN, nicht zaehlen):
      Richtungsverteilung 10x UP / 3x DOWN - einseitig, und das wird nicht
      weggeredet. Die Gruppierung:
      * EINE Wette in fuenf Zeilen: SP500, MSCIWorld, VWCE, Amundi Nasdaq-100,
        Amundi MSCI World. Traeger ist derselbe Mechanismus (Marktdrift plus
        USD-Rueckenwind auf die EUR-notierten Huellen). Kippt die Woche nach
        unten, kippen alle fuenf gemeinsam. AUSDRUECKLICH AUSGEWIESEN.
      * Drei Zeilen mit eigenem, marktunabhaengigem Treiber, bewusst gegen die
        Mehrheit: HSBC MSCI EM (DOWN), UnitedHealth (DOWN), PepsiCo (DOWN).
      * Fuenf Einzelaktien-UP-Zeilen ohne eigenen Treiber, auf dem Konfidenz-
        boden: AAPL, ASML, ADBE, META, TTWO.
      EHRLICHE EINORDNUNG, die in den Report gehoert: Dieser Satz liegt mit
      10/13 UP dicht an der Drift-Baseline "immer UP". Er traegt deshalb WENIG
      eigenstaendige Information ueber die naive Regel hinaus. Das ist bewusst
      so gewaehlt - Learning 11.09. (2) hat meine Gegenbewegungs-Vorliebe als
      GERICHTETEN Fehler belegt, und die diszipliniertere Reaktion darauf ist,
      nicht reflexhaft gegen die letzte Bewegung zu setzen. Der Preis dafuer
      ist ein informationsarmer Satz, und der wird hier VORAB benannt statt
      hinterher erklaert (Learning 15.08.).

  (H) KALIBRIERUNG - warum keine einzige Zeile ueber 55 steht:
      Regel aus Learning 12.09. (4): Konfidenzen ueber 60 sind auf 1W nur
      zulaessig, wenn ein Treiber benannt ist, der ueber den GESAMTEN
      Fuenftagezeitraum wirkt - Quartalsbericht im Fenster, terminierte
      Notenbanksitzung, laufender Rechtsstreit. Im Fenster 21.-25.09. liegt
      weder ein Quartalsbericht der 13 Werte noch eine FOMC-Sitzung. Der
      Trump-Xi-Gipfel am 24.09. ist terminiert, wirkt aber in beide Richtungen
      und deckt keine hohe Konfidenz.
      Zweiter Grund, staerker als der erste: Die laufende 1W-Bilanz liegt mit
      55.4 % gegen 57.4 % Random Walk im RUECKSTAND, p = 0.16 gegen den
      Muenzwurf. Ein Verfahren ohne nachweisbare Kante vergibt keine hohen
      Konfidenzen. Hoechster Wert: VWCE 55. Niedrigster: ADBE 51.
      ADBE steht wieder auf dem Boden - 2 von 8 aufgeloesten 1W-Zeilen richtig,
      Fehlschlaege in BEIDE Richtungen. Nach der Regel vom 08.08. wird daraus
      KEINE Umkehrwette gebaut, sondern das Fehlen einer Kante protokolliert.
      Folge: KEIN einziger High-Confidence-Call (>= 65) in diesem Satz.

  (I) BASELINE-SPALTE = Richtung der letzten WOCHENbewegung (18.09. gegen
      11.09.), je Asset quellenintern gerechnet. Beim Amundi Nasdaq-100 aus
      der Xetra-Reihe (103.38 -> 104.54 = UP), weil die gettex-Historie ueber
      onvista nicht abrufbar war; die Richtung ist unter beiden Lesarten UP.

  (J) SAUBERKEIT: Erzeugung am Samstag bei geschlossenen Maerkten. Alle 13
      Referenzkurse sind endgueltige Freitagsschluesse, kein Nowcast, kein
      Intraday-Leck - fuer alle 13 Zeilen echte Prognose ueber einen
      vollstaendig ungehandelten Zeitraum.

  (K) INTEGRITAET: Zuerst aufgeloest (nur Ergebnis + Ist-Kurs), danach nur
      angehaengt. Keine 1T-Zeile erzeugt, keine 1T-Zeile veraendert - die
      Tagesprognosen bleiben vollstaendig dem Morgenreport ueberlassen.
-->

2026-09-19 | Opus-5 | SP500 | 1W | UP | 53 | 7650.50 | DOWN | 2026-09-25 | offen | 
2026-09-19 | Opus-5 | MSCIWorld | 1W | UP | 52 | 4913.98 | DOWN | 2026-09-25 | offen | 
2026-09-19 | Opus-5 | Vanguard FTSE All-World | 1W | UP | 55 | 167.14 | UP | 2026-09-25 | offen | 
2026-09-19 | Opus-5 | Amundi Nasdaq-100 | 1W | UP | 53 | 105.300 | UP | 2026-09-25 | offen | 
2026-09-19 | Opus-5 | HSBC MSCI EM | 1W | DOWN | 53 | 16.29 | DOWN | 2026-09-25 | offen | 
2026-09-19 | Opus-5 | Amundi MSCI World | 1W | UP | 54 | 159.53 | UP | 2026-09-25 | offen | 
2026-09-19 | Opus-5 | AAPL | 1W | UP | 52 | 336.13 | UP | 2026-09-25 | offen | 
2026-09-19 | Opus-5 | UNH | 1W | DOWN | 53 | 376.90 | DOWN | 2026-09-25 | offen | 
2026-09-19 | Opus-5 | ASML | 1W | UP | 54 | 1679.92 | DOWN | 2026-09-25 | offen | 
2026-09-19 | Opus-5 | PEP | 1W | DOWN | 54 | 129.75 | DOWN | 2026-09-25 | offen | 
2026-09-19 | Opus-5 | ADBE | 1W | UP | 51 | 248.92 | DOWN | 2026-09-25 | offen | 
2026-09-19 | Opus-5 | META | 1W | UP | 52 | 665.75 | UP | 2026-09-25 | offen | 
2026-09-19 | Opus-5 | TTWO | 1W | UP | 52 | 205.45 | DOWN | 2026-09-25 | offen | 

<!--
  SATZ 2026-09-21 (Montag, Handelstag) — 1T, Morgenreport. Kommentar zur Methode:

  (A) ZUSTAENDIGKEIT: Dieser Lauf erzeugt und loest AUSSCHLIESSLICH 1T-Zeilen.
      Die 1W-Zeilen vom 2026-09-19 (Aufloesung 2026-09-25) wurden NICHT
      angefasst - die macht der Samstags-Task.

  (B) AUFLOESUNG HEUTE: KEINE. Offene 1T-Zeilen vor diesem Lauf: 0 (geprueft
      per grep). Der Samstagsreport hat den 18.09.-Satz bereits aufgeloest;
      am 19./20.09. wurde keine 1T-Batterie erzeugt (keine Handelstage).

  (C) REFERENZKURSE = Schlusskurse Freitag, 18.09.2026, je Asset aus der in
      studien-universum.md festgelegten Primaerquelle.
      RUECKRECHNUNGS-CHECK bestanden fuer alle sieben US-Einzelwerte gegen
      finviz (21.09., ~06:15 ET vorboerslich): Kurs / (1 + Tagesaenderung)
      ergibt exakt den geloggten Referenzkurs -
      AAPL 335.36 / 0.9977 = 336.1 | ADBE 248.90 / 0.9999 = 248.9 |
      ASML 1712.52 / 1.0194 = 1680.0 | META 681.00 / 1.0229 = 665.8 |
      PEP 130.00 / 1.0019 = 129.8 | TTWO 206.24 / 1.0039 = 205.4 |
      UNH 378.12 / 1.0032 = 376.9.
      SP500 7650.50 doppelt belegt (CNN Markets 21.09. und Benzinga 21.09.).
      VWCE 167.14 direkt als "Previous Close" auf stockanalysis ETR:VWCE
      bestaetigt. H4Z3 16.29 und MWRE 159.53: stockanalysis weist diese
      Seiten noch mit "At close: Sep 18, 2026" bzw. "Last updated: Sep 18,
      2026, 5:30 PM CET" aus, der angezeigte Kurs IST also der Freitagsschluss;
      ihr Feld "Previous Close" (16.36 / 159.97) ist der Donnerstagsschluss.
      Kein Quellenkonflikt, sondern unterschiedlicher Rollover je Ticker.
      Amundi Nasdaq-100 105.300 (gettex): die onvista-Seite zur ISIN war unter
      der bisherigen Adresse nicht mit gettex-Kurs abrufbar; der Wert stammt
      aus dem Batterie-Log vom 19.09. und wurde HEUTE NICHT gegen die
      Primaerquelle neu erhoben. Ausdruecklich als einzige nicht
      nachgepruefte Referenz dieses Satzes gekennzeichnet.

  (D) BASELINE = Richtung der letzten abgeschlossenen Tagesbewegung
      (18.09. gegen 17.09.), je Asset quellenintern gerechnet.
      Baseline und Prognose stimmen in 7 von 13 Zeilen ueberein und
      widersprechen sich in 6 (MSCIWorld, VWCE, H4Z3, MWRE, META, TTWO).

  (E) SAUBERKEIT - der wichtigste Vermerk dieses Satzes:
      Erzeugungszeit 12:05-13:10 MESZ. Die europaeischen Boersen handeln seit
      drei Stunden, die US-Boersen sind geschlossen (vorboerslich).
      INTRADAY-LECK, offen benannt statt kaschiert:
      - STARK kontaminiert (Nowcast-Anteil hoch): Vanguard FTSE All-World,
        HSBC MSCI EM, Amundi MSCI World. Fuer diese drei lagen laufende
        Xetra-Kurse vor (+0.94 % / +2.05 % / abgeleitet), und sie schliessen
        bereits um 17:35 MESZ. Die Konfidenzen 72/76/68 sind deshalb BEWUSST
        hoch - eine kuenstlich niedrige Zahl waere unehrlicher als eine hohe.
        DIESE DREI ZEILEN SIND FUER DIE AUSWERTUNG ALS AUSSCHLUSSFAEHIGE
        TEILMENGE ZU BEHANDELN.
      - MITTEL kontaminiert: Amundi Nasdaq-100 (gettex, handelt bis 22:00,
        laufender Kurs +1.22 % bekannt), MSCIWorld (Feststellung 16:00 MESZ).
      - GERING kontaminiert: die sieben US-Einzelwerte und SP500 - nur
        vorboerslicher Handel beobachtet, und der ist nach Learning 12.09. (2)
        ein Praediktor fuer die EROEFFNUNG, nicht fuer den SCHLUSS.

  (F) KONFIDENZEN: hoechster Wert 76 (HSBC MSCI EM, Nowcast), niedrigster 54
      (AAPL). Von den sieben US-Einzelwerten liegt KEINER ueber 70.
      Begruendung fuer die Deckelung bleibt Learning 19.09. (3): Ueber 1T ist
      die Kante nachgewiesen (227/364 = 62.4 %), ueber laengere Horizonte
      nicht - hohe Konfidenzen werden nur dort vergeben, wo ein eigener
      benannter Treiber ODER ein hoher Feststellungsanteil vorliegt.

  (G) KOHAERENZ-CHECK: 10 von 13 Zeilen lauten UP und haengen an EINEM
      gemeinsamen Treiber - dem Risk-on-Montag (Futures im Plus, Oel vierter
      Verlusttag, Asien und Europa hoeher, Gipfelerwartung). Ein gemeinsames
      Scheitern waere EIN Irrtum ueber den Tag, nicht zehn.
      Die drei DOWN-Zeilen haben jeweils einen EIGENEN benannten Treiber:
      AAPL (vorboerslich als einziger US-Wert negativ; Kostentraeger der
      Speicherpreise statt Nutzniesser der KI-Rallye), PEP (XLP vorboerslich
      -0.60 %, vierter Sektorschwaechetag, GLP-1-Befund vom 17.09.),
      ADBE (Woche -6.29 %, Budgetverdraengung Software -> KI-Infrastruktur,
      IBM-Beleg vom 16.09.).
      DAMIT IST DIE GRUPPENTRENNUNG AUS BEOBACHTUNG 19.09. (4) FORTGESETZT:
      3 Zeilen mit eigenem Treiber, 10 aus einem gemeinsamen Markt-Call
      abgeleitet. Die Frage, ob Zeilen mit eigenem Treiber besser abschneiden,
      bleibt damit weiter messbar.

  (H) INTEGRITAET: Nur angehaengt. Keine bestehende Zeile geloescht,
      ueberschrieben oder umsortiert. Keine 1W-Zeile erzeugt oder veraendert.
-->

2026-09-21 | Opus-5 | SP500 | 1T | UP | 63 | 7650.50 | UP | 2026-09-21 | offen | 
2026-09-21 | Opus-5 | MSCIWorld | 1T | UP | 66 | 4913.98 | DOWN | 2026-09-21 | offen | 
2026-09-21 | Opus-5 | Vanguard FTSE All-World | 1T | UP | 72 | 167.14 | DOWN | 2026-09-21 | offen | 
2026-09-21 | Opus-5 | Amundi Nasdaq-100 | 1T | UP | 66 | 105.300 | UP | 2026-09-21 | offen | 
2026-09-21 | Opus-5 | HSBC MSCI EM | 1T | UP | 76 | 16.29 | DOWN | 2026-09-21 | offen | 
2026-09-21 | Opus-5 | Amundi MSCI World | 1T | UP | 68 | 159.53 | DOWN | 2026-09-21 | offen | 
2026-09-21 | Opus-5 | AAPL | 1T | DOWN | 54 | 336.13 | DOWN | 2026-09-21 | offen | 
2026-09-21 | Opus-5 | UNH | 1T | UP | 56 | 376.90 | UP | 2026-09-21 | offen | 
2026-09-21 | Opus-5 | ASML | 1T | UP | 70 | 1679.92 | UP | 2026-09-21 | offen | 
2026-09-21 | Opus-5 | PEP | 1T | DOWN | 56 | 129.75 | DOWN | 2026-09-21 | offen | 
2026-09-21 | Opus-5 | ADBE | 1T | DOWN | 58 | 248.92 | DOWN | 2026-09-21 | offen | 
2026-09-21 | Opus-5 | META | 1T | UP | 66 | 665.75 | DOWN | 2026-09-21 | offen | 
2026-09-21 | Opus-5 | TTWO | 1T | UP | 55 | 205.45 | DOWN | 2026-09-21 | offen | 
