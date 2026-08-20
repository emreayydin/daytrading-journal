# Daytrading-Journal — Virtuelles Konto

**Startkapital:** 1.000,00 USD
**Start:** 2026-08-18
**Strategie:** Breakout + Momentum-Continuation (primär), Mean Reversion im Range-Regime (sekundär)
**Märkte:** Krypto-Majors (BTC, ETH, SOL), FX-Majors sekundär

---

## Risiko-Regelwerk (Kurzfassung)

| Parameter | Wert |
|---|---|
| Risiko/Trade | 1,5 % — **Probezeit erste 10 Trades: 1,0 %** |
| Max. Trades/Tag | 3 |
| Max. Positionen | 2 unkorreliert (BTC+ETH = 1 Position) |
| Max. Notional | 3× Equity, Isolated Margin |
| Mindest-CRV | 1:2 |
| Stop-Bandbreite | 0,4 % – 2,0 % |
| Tageslimit | −3 % (−30 USD) oder 2 Verluste in Folge |
| Wochenlimit | −6 % (−60 USD) |
| Monatslimit | −10 % |
| Drawdown-Drossel | Equity < 900 USD → Risiko halbiert auf 0,75 % |
| Handelszeiten | 09:00–11:00 und 15:30–17:30 CET |
| Overnight | Verboten — alles vor 22:00 CET glatt |

**Exit-Leiter:** 50 % @ +1R (Stop → Einstand), 25 % @ +2R (Stop → +1R), 25 % Runner mit Trail.
**Zeit-Stop:** < +0,5R nach 90 Minuten → schließen.

---

# Tag 1 — 2026-08-18

## Marktlage (Live-Daten, Quelle: Kraken Public API / Coinbase)

| Asset | Kurs | Tages-Open | Tages-Hoch | Tages-Tief | Δ Tag | Tagesrange |
|---|---|---|---|---|---|---|
| BTC/USD | 64.255,90 | 62.819,10 | 64.562,30 | 62.683,40 | **+2,29 %** | 2,99 % |
| ETH/USD | 1.903,53 | 1.874,09 | 1.913,40 | 1.870,80 | +1,57 % | 2,28 % |
| SOL/USD | 75,81 | 74,55 | 76,16 | 74,37 | +1,69 % | 2,40 % |

**Übergeordneter Kontext (recherchiert):**
- BTC seit Jahresanfang von ~93.000 auf ~64.000 gefallen — **Bärenmarkt auf höherem Zeitrahmen**
- Handel **unter den wichtigen gleitenden Durchschnitten**
- Klar definierte Range: **Support 62.500 / Resistance 65.000–70.000**
- Marktkapitalisierung BTC ~1,33 Bio. USD

**Regime-Einstufung: RANGE (bestätigt).** Damit ist das Mean-Reversion-Setup laut Regelwerk freigeschaltet.

## Analyse

Alle drei Assets steigen synchron (+1,5 % bis +2,3 %) — reine Risk-on-Korrelation, kein
idiosynkratisches Signal. Nach Regelwerk zählen BTC/ETH/SOL heute als **eine** Position.

BTC notiert bei 64.256, also im **oberen Sechstel der Tagesrange** (84 % Perzentil) und
**1,16 % unter der Range-Resistance bei 65.000**.

Das erzeugt einen Konflikt, der explizit aufgelöst werden muss:

- **Long-Momentum?** Der Tagestrend ist aufwärts. Aber: Einstieg 84 % in der Tagesrange,
  direkt gegen bekannten Widerstand, gegen einen bärischen Höherzeitrahmen. Der Stop müsste
  unter das Tagestief (−2,4 %), das Ziel liegt 1,2 % entfernt. **CRV ca. 1:0,5 — abgelehnt.**
- **Short-Rejection an der Range-Oberkante?** Regime = Range (bestätigt), HTF = bärisch,
  Preis läuft in Widerstand. Stop eng über der Resistance, Ziel zurück in die Range-Mitte.
  **CRV 1:3,4 — angenommen.**

**Entscheidung: Limit-Short in die Widerstandszone.** Kein Markteinstieg bei 64.256 —
das wäre ein Fade ohne Signal. Die Order wartet auf den besseren Preis.

## Trade #1 — BTC/USD SHORT (Limit-Order platziert)

| Feld | Wert |
|---|---|
| **Einstiegssignal** | Limit-Sell in Range-Resistance 65.000; Trigger bei Antesten der Zone |
| **Begründung** | Mean Reversion an bestätigter Range-Oberkante; HTF bärisch (unter MAs, −31 % YTD); Preis 84 % in Tagesrange = ungünstiges Long-Chance-Profil; Ziel = Rückkehr Range-Mitte |
| **Einstiegspreis** | 64.900,00 USD (Limit) |
| **Stop-Loss** | 65.450,00 USD (−0,847 % Abstand, 450 USD Puffer über Resistance) |
| **Take-Profit 1** | 64.350,00 (+1,0R) → 50 % schließen, Stop auf Einstand |
| **Take-Profit 2** | 63.800,00 (+2,0R) → 25 % schließen, Stop auf +1R |
| **Finalziel** | 63.050,00 (+3,36R) → Runner 25 %, Trail hinter 15m-Swing |
| **Risiko** | 10,00 USD (1,0 % — Probezeit) |
| **Positionsgröße** | **1.180,00 USD Notional / 0,01819 BTC** |
| **Impliziter Hebel** | 1,18× (Cap 3,0× — eingehalten) |
| **CRV (Finalziel)** | **1:3,36** ✅ |
| **CRV (geleitert, gewichtet)** | 1:1,84 ⚠️ siehe Reflexion |
| **Gebühren R/T** | ~1,18 USD (0,10 % Notional) = 11,8 % des Risikos |
| **Status** | **Order platziert — noch nicht ausgelöst** |

**Invalidierung:** 15m-Schlusskurs über 65.100 mit steigendem Volumen = Range-Bruch,
These tot. Der Stop bei 65.450 puffert genau diesen Fehlausbruch ab.

## Nicht genommene Trades

| Kandidat | Warum abgelehnt |
|---|---|
| ETH Long | Korreliert mit BTC → gleiche Position nach Regelwerk. Kein zusätzlicher Edge, doppeltes Risiko |
| SOL Long | Ebenso korreliert; zusätzlich +1,7 % bereits gelaufen, Einstieg nahe Tageshoch |
| BTC Long Breakout | CRV ca. 1:0,5 → unter Mindest-CRV 1:2. Automatische Ablehnung |
| EUR/USD | Keine Live-Daten geprüft, außerhalb der definierten Session |

## Tagesabschluss

| Kennzahl | Wert |
|---|---|
| **Kontostand** | **1.000,00 USD** (unverändert) |
| **Realisierte P&L** | 0,00 USD |
| **Offene Positionen** | keine |
| **Pending Orders** | 1× BTC Short Limit @ 64.900 (Risiko 10 USD) |
| **Genutztes Tageslimit** | 0 von 30 USD |
| **Trades ausgeführt** | 0 von max. 3 |

### Reflexion Tag 1

**Was gut lief:**
- Der Regime-Filter hat funktioniert. Ohne den Kontext "BTC in Range 62,5k–65k, unter den MAs"
  wäre der naheliegende Trade ein Long-Momentum-Einstieg gewesen — direkt in den Widerstand.
  Genau der Trade, den die Strategie ausschließen soll.
- Die Korrelationsregel hat drei potenzielle Positionen auf eine reduziert. Bei 1.000 USD wäre
  BTC+ETH+SOL long gleichzeitig faktisch ein dreifach gehebelter Einzeltrade gewesen.
- CRV-Mindestfilter hat objektiv entschieden, nicht das Bauchgefühl.

**Was schlecht lief / Schwachstellen:**
- **Die Exit-Leiter verwässert das CRV.** Nominal 1:3,36, gewichtet aber nur 1:1,84 — unter
  meiner eigenen Mindestschwelle. Das Teilgewinn-System schützt die Psyche, kostet aber
  Erwartungswert. → **Anpassung:** TP1 wird von +1,0R auf **+1,5R** verschoben. Gewichtetes
  CRV steigt damit auf 1:2,09.
- **Gebührenquote von 11,8 % des Risikos ist hoch.** Bei einem 0,85-%-Stop ist das systembedingt.
  Bei Stops unter 0,6 % würde die Quote über 15 % steigen — dort lohnt der Trade nicht mehr.
  → **Anpassung:** Mindest-Stop-Abstand von 0,4 % auf **0,6 %** angehoben.
- **Kein ausgeführter Trade an Tag 1.** Das ist regelkonform, aber es erzeugt Handlungsdruck
  für Tag 2. Genau daraus entstehen erzwungene Trades. Bewusst notiert als Warnung.

**Regeländerungen ab Tag 2:**
1. TP1 von +1,0R → **+1,5R**
2. Mindest-Stop-Abstand von 0,4 % → **0,6 %**
3. Kein Trade nur, weil der Vortag leer war — Setup-Qualität bleibt der einzige Filter

---

## Datenherkunft & Annahmen

| Element | Quelle |
|---|---|
| BTC/ETH/SOL Kurse, Tagesrange, Open | ✅ **Live** — Kraken Public API + Coinbase Spot API, 2026-08-18 |
| Range-Levels 62.500 / 65.000 | ✅ **Recherchiert** — Marktberichte August 2026 |
| HTF-Trend (unter MAs, −31 % YTD) | ✅ **Recherchiert** |
| Gebühren 0,05 % Taker/Seite | ⚠️ **ANNAHME** — vor Realbetrieb am eigenen Broker verifizieren |
| ATR-Puffer für Stop-Platzierung | ⚠️ **ANNAHME** — aus Tagesrange abgeleitet, kein echter ATR(14) |
| Volumenprofil / Orderbuchtiefe | ⚠️ **NICHT geprüft** — nur 24h-Volumen bekannt |

---

# Backtest — 2 Wochen (05.08.–20.08.2026)

**Was das ist:** Das Regelwerk mechanisch über echte 30-Minuten-Kerzen der letzten zwei
Wochen gerechnet. Kein Vorwärtstest — die Kursdaten lagen bereits vor. Datenquelle:
Kraken OHLC API, 721 Kerzen je Asset.

**Was das nicht ist:** Kein Beweis für einen Edge. Siehe Signifikanz unten.

## Mechanische Regelumsetzung

| Regel | Umsetzung im Code |
|---|---|
| Setup A (ORB) | Opening Range = erste Stunde des Fensters; Einstieg bei 30m-Schluss jenseits der OR-Kante; Trendfilter SMA(50) |
| Setup B (Fade) | Nur bei ADX(14) < 20; Einstieg an 24h-Range-Kante gegen SMA(50) |
| Stop | Gegenseite der OR ± 0,25 × ATR(14); nur 0,6 %–2,0 % zugelassen |
| Exits | TP1 +1,5R (50 %), TP2 +2,0R (25 %, Stop→+1R), TP3 +3,0R (25 %) |
| Zeit-Stop | < +0,5R nach 3 Kerzen (90 Min) |
| Risiko | 1,0 % (Probezeit), Notional-Cap 3× |
| Gebühren | 0,05 % je Seite |
| Sequenzierung | Stop und Ziel in derselben Kerze → **Stop zählt zuerst** |

## Ergebnis

| | Ideal (nur Gebühren) | Realistisch (+ Slippage) |
|---|---|---|
| Trades | 15 | 16 |
| Trefferquote | 53,3 % | 50,0 % |
| **Endkapital** | **1.056,81 USD (+5,68 %)** | **1.023,51 USD (+2,35 %)** |
| Erwartungswert | +0,279R | **+0,098R** |
| Standardabweichung | 0,809R | 0,710R |
| **t-Statistik** | **1,34** | **0,55** |
| Max Drawdown | −1,50 % | −2,42 % |

Slippage-Annahme realistisch: 0,05 % beim Einstieg, 0,15 % bei Stop-Ausführungen.

## Die entscheidende Zahl

**t = 1,34 (ideal) bzw. 0,55 (realistisch).** Signifikanz beginnt bei ~2,0.

Bei dieser Streuung bräuchte es **~34 Trades** (ideal) bzw. **~209 Trades** (realistisch),
um den Erwartungswert von Zufall zu unterscheiden. Bei 1,4 Trades pro Tag sind das
**5 Wochen** bzw. **7 Monate**.

**Diese zwei Wochen beweisen nichts.** Sie sind mit einer Strategie ohne jeden Edge
vollständig vereinbar.

## Was auffällt (aber NICHT geändert wird)

| Beobachtung | Zahl | Warum keine Änderung |
|---|---|---|
| Zeit-Stop ist der größte Verlustbringer | 8 von 15 Exits, in Summe **−1,11R** | Er schneidet Trades ab, bevor sie arbeiten. Bei n=8 wäre eine Anpassung reines Curve-Fitting |
| SOL liefert nichts | 8 Trades, in Summe **−0,12R** | Bindet 53 % der Trades für null Ertrag. Bei n=8 statistisch bedeutungslos |
| BTC trägt alles | 4 Trades, **+3,05R** | Ein einziger Trade (+1,94R) macht die Hälfte davon aus |
| Setup B ist nie ausgelöst | **0 von 15** | Der Range-Filter (ADX < 20) hat in zwei Wochen nie gegriffen. Ungetestet, nicht widerlegt |
| Nur 1 Trade erreichte das Endziel | 1 von 15 | Der Runner-Anteil trägt kaum |

**Regeländerungen: keine.** Nach 15 Trades an den Parametern zu drehen, würde die
Strategie an genau diese zwei Wochen anpassen — und damit jede Aussagekraft der
nächsten 15 Trades zerstören.

## Gefundene Spezifikations-Lücke

Der Backtest hat an **Samstag (08.08.) und Sonntag (09.08.)** gehandelt — Krypto läuft
24/7, das Zeitfenster-Filter kennt keine Wochentage. Die Cloud-Routine läuft dagegen
nur **Mo–Fr**. Beide Trades waren Verlierer (−0,21R, −0,01R).

Das ist ein echter Widerspruch im Regelwerk und muss vor dem nächsten Lauf entschieden
werden: entweder 7 Tage handeln (Krypto ist durchgehend offen) oder Wochenenden
explizit ausschließen. Aktuell steht beides nebeneinander.

## Fazit

Die Strategie ist über zwei Wochen **leicht positiv** — und das ist die ehrlichste
Formulierung, die die Daten hergeben. Der Sprung von +5,68 % auf +2,35 % allein durch
realistische Slippage zeigt, wie dünn die Marge ist: **Slippage frisst 65 % des
Erwartungswerts.**

Bei 0,5 % Gebühren statt 0,05 % wäre das Ergebnis negativ. Die Wahl der Börse
entscheidet hier mehr als die Strategie.
