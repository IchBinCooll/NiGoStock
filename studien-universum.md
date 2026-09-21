# Studien-Universum — feste Prognose-Liste für die Bachelorarbeit

Diese Liste steuert NUR die Prognose-Batterie (prognose-batterie.md), also die Studiendaten.
Sie ist BEWUSST vom Depot getrennt und hat NICHTS mit dem lesbaren Morgenreport zu tun.

Regeln:
- Der Morgenreport prognostiziert jeden Handelstag GENAU diese Werte — egal, was Meister gerade hält.
- Diese Liste ändert sich NUR, wenn Meister sie hier von Hand bearbeitet. Nie automatisch durch Käufe/Verkäufe.
- Ein einmal aufgenommener Wert bleibt für immer drin — auch nach einem Verkauf. Das hält die Datenreihe
  lückenlos und verhindert Survivorship-Bias (die Daten werden nicht durch Handelsentscheidungen verzerrt).
- Wer einen Wert dauerhaft in die Studie aufnehmen will, trägt ihn hier ein. Wieder rausnehmen nur,
  wenn man ihn bewusst NIE mehr in der Auswertung haben will (besser: drinlassen).

## Indizes (fester Kern, nie entfernen)
- SP500
- MSCIWorld

## ETFs
- Vanguard FTSE All-World (IE00BK5BQT80)
- Amundi Nasdaq-100 (LU1829221024)
- HSBC MSCI EM (IE000KCS7J59)
- Amundi MSCI World (IE000BI8OT95)

## Aktien (Stand 01.08.2026 — eingefroren für die Studie)
- Apple (AAPL)
- UnitedHealth (UNH)
- ASML (ASML)
- PepsiCo (PEP)
- Adobe (ADBE)
- Meta (META)
- Take-Two (TTWO)

---

## 🔒 PRIMÄRQUELLEN JE ASSET — verbindlich ab 14.09.2026

**Warum das hier steht:** Learning 12.09. (3) hat aufgedeckt, dass für denselben Wert am
selben Tag zwei verschiedene Schlusskurse in der Batterie standen, weil Tages- und
Wochenlauf unterschiedliche Quellen benutzten (All-World 166,67 gegen 166,86; MSCI World
4.907,06 gegen 4.937,32). Keine dieser Zahlen war falsch — es waren verschiedene
Handelsplätze bzw. Indexvarianten. Genau das macht den Fehler unsichtbar. Eine
Trefferquote, die Referenzkurs aus Quelle A gegen Ist-Kurs aus Quelle B rechnet, misst
bei kleinen Bewegungen zu einem messbaren Anteil **die Quellendifferenz statt die
Prognose**.

**Regel: Referenzkurs und Ist-Kurs einer Zeile stammen IMMER aus der hier genannten
Quelle. Ist sie beim Auflösen ausgefallen, gilt „n/v" (Regel 11.09. (3)) — NICHT die
Ersatzquelle.** Gilt für Morgenlauf (1T) und Samstagslauf (1W) gleichermaßen.

| Asset | Primärquelle | Handelsplatz / Variante | Währung |
|---|---|---|---|
| SP500 | Reuters / FXEmpire Marktbericht | S&P-500-Cash-Index, Schlusskurs | Punkte |
| MSCIWorld | onvista, WKN A3DR38 | **MSCI DAILY USD** | Punkte |
| Vanguard FTSE All-World | stockanalysis.com, `ETR:VWCE` | Xetra | EUR |
| Amundi Nasdaq-100 | onvista, LU1829221024 | **gettex** | EUR |
| HSBC MSCI EM | stockanalysis.com, `ETR:H4Z3` | Xetra | EUR |
| Amundi MSCI World | stockanalysis.com, `ETR:MWRE` | Xetra | EUR |
| Apple (AAPL) | finviz Quote | US-Schluss | USD |
| UnitedHealth (UNH) | finviz Quote | US-Schluss | USD |
| ASML | finviz Quote | **US-ADR**, nie Amsterdam (Learning 04.08.) | USD |
| PepsiCo (PEP) | finviz Quote | US-Schluss | USD |
| Adobe (ADBE) | finviz Quote | US-Schluss | USD |
| Meta (META) | finviz Quote | US-Schluss | USD |
| Take-Two (TTWO) | finviz Quote | US-Schluss | USD |

⚠️ **Einmaliger, datierter Quellenbruch am 14.09.2026** bei **MSCIWorld**, **Vanguard
FTSE All-World** und **Amundi Nasdaq-100**. Zeilen vor diesem Datum sind mit späteren
Zeilen für diese drei Werte nur eingeschränkt vergleichbar; der Bruch ist im
Kommentarblock der Batterie dokumentiert. **Für den All-World bestätigt der Wechsel die
Konsistenz sogar:** 166,86 − 1,60 = 165,26 = exakt der am 11.09. geloggte Referenzkurs —
die Xetra-Quelle war schon immer die richtige, falsch war der Ist-Kurs aus dem Tracker.

❌ **Der Finanzfluss-Tracker ist ab sofort KEINE Kursquelle für die Studie.** Er ist ein
Depot-Tracking-Werkzeug; seine Kurse sind ein Nebenprodukt (Learning 07.08.). Für den
lesbaren Report bleibt er die Quelle der **Depotwerte in Euro** — das ist etwas anderes
als ein Studienkurs und wird nie vermischt.
