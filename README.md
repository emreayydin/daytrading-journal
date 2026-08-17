# Daytrading-Journal — Simulation

**Dies ist eine reine Simulation.** Virtuelles Kapital, keine echten Konten, keine echten
Orders, keine Broker-Anbindung. Nichts in diesem Repo führt Trades aus oder bewegt Geld.
Keine Anlageberatung.

- **Kapital:** 1.000 USD (virtuell)
- **Start:** 2026-08-18
- **Log:** [JOURNAL.md](JOURNAL.md)

## Zweck

Übungsrahmen für eine regelbasierte Daytrading-Strategie auf Krypto-Majors. Das Journal
dokumentiert Regelwerk, Setups, Positionsgrößen, Ergebnisse und Tagesreflexionen.

Ein geplanter Cloud-Agent aktualisiert das Journal werktags um 17:30 Uhr (Europe/Berlin):
Live-Kurse abrufen, offene Orders auflösen, neue Setups nach Regelwerk prüfen,
Tagesabschluss schreiben, committen.

Dieses Repo ist öffentlich, weil der Cloud-Agent sonst keinen Zugriff hätte. Es enthält
ausschließlich Simulationsdaten — keine API-Keys, keine Broker-Zugänge, keine echten
Kontodaten.

## Datenquellen

Live-Kurse über öffentliche APIs (Kraken, Coinbase). Alles, was nicht aus Live-Daten
stammt, ist im Journal als `[ANNAHME]` gekennzeichnet.
