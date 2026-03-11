<div align="center">
<pre>
  _   _   ______   __   __   _    _    _____ 
 | \ | | |  ____|  \ \ / /  | |  | |  / ____|
 |  \| | | |__      \ V /   | |  | | | (___  
 | . ` | |  __|      > <    | |  | |  \___ \ 
 | |\  | | |____    / . \   | |__| |  ____) |
 |_| \_| |______|  /_/ \_\   \____/  |_____/ 

               ╔═══════════════════╗
               ║     O N E A P P   ║
               ╚═══════════════════╝
</pre>

**Ein Gerät. Ein Protokoll. Eine neue Zivilisation.**

[![License: AGPL v3](https://img.shields.io/badge/License-AGPL_v3-blue.svg)](https://www.gnu.org/licenses/agpl-3.0)
[![Flutter](https://img.shields.io/badge/Flutter-Dart-02569B?logo=flutter)](https://flutter.dev)
[![Substrate](https://img.shields.io/badge/Blockchain-Substrate-E6007A?logo=polkadot)](https://substrate.io)
[![Status](https://img.shields.io/badge/Status-Phase_0-yellow)]()

</div>

---

## Was ist die OneApp?

Die OneApp ist die **Referenz-Implementierung des N.E.X.U.S.-Protokolls** — ein dezentrales, zensurresistentes Betriebssystem für eine souveräne Gesellschaft. Sie vereint verschlüsselten Mesh-Chat, eine postkapitalistische Ökonomie und demokratische Governance in einer einzigen App.

```
Protokoll, nicht Plattform.
Killer-App zuerst, Ökosystem danach.
Wer alles auf einmal baut, baut nichts.
```

**Wir bauen den Chat. Dann die Wirtschaft. Dann die Gesellschaft.**

---

## Aktueller Status

| Phase | Beschreibung | Status |
| :--- | :--- | :--- |
| **Phase 0** | Fundament — Flutter-Projekt, Identität (Seed Phrase) | 🔨 In Arbeit |
| Phase 1a | Killer-App #1 — BLE Mesh-Chat | ⏳ Nächster Schritt |
| Phase 1b | Killer-App #2 — VITA-Wallet + Lokaler Marktplatz | 📋 Geplant |
| Phase 2 | Killer-App #3 — Care-System + Governance | 📋 Geplant |
| Phase 3 | Sphären-Plugins (Gesundheit, Bildung, Ernährung, Wohnen) | 📋 Geplant |

---

## Architektur

Die OneApp folgt dem Prinzip **„Protokoll, nicht Plattform"** (Bauplan Kap. 4.8):

- **Schicht 1: Das NEXUS-Protokoll** — Offene Spezifikation für Identität, Transaktionen, Governance, Messaging
- **Schicht 2: Die OneApp** — Der offizielle Open-Source-Client (dieses Repo)
- **Schicht 3: Das Ökosystem** — Community-Apps, Sphären-Plugins, spezialisierte Tools

```
┌─────────────────────────────────────────────┐
│              NUTZER-GERÄT                    │
│                                             │
│  OneApp UI (Flutter)                        │
│       │                                     │
│  NEXUS SDK / Core Library                   │
│  ┌────────┐ ┌────────┐ ┌──────┐ ┌───────┐  │
│  │Identity│ │ Wallet │ │ Chat │ │Govern.│  │
│  │ (DID)  │ │(AETHER)│ │(E2EE)│ │(Liq.D)│  │
│  └────────┘ └────────┘ └──────┘ └───────┘  │
│       │                                     │
│  Solid POD (Lokaler Datentresor)            │
└─────────────┬───────────────────────────────┘
              │
    ┌─────────┼─────────┐
    ▼         ▼         ▼
 BLE Mesh   Nostr     LoRa
 (lokal)  (Internet) (Notfall)
    │         │         │
    └────┬────┘         │
         ▼              │
   NEXUS-Netzwerk ──────┘
   (Substrate Chain + IPFS + Home-Nodes)
```

---

## Tech-Stack

| Bereich | Technologie | Begründung |
| :--- | :--- | :--- |
| **App** | Flutter (Dart) | Eine Codebase → Android, iOS, Linux, Raspberry Pi, Web |
| **Blockchain** | Substrate (Polkadot SDK) | Eigene souveräne Chain, Forkless Upgrades, Rust |
| **Mesh-Chat** | BLE 5.0 + Nostr | BitChat-Blaupause (Nepal 2025: 50K Downloads/Tag) |
| **Verschlüsselung** | Noise Protocol + NIP-17 | E2E für Mesh + Nostr |
| **Identität** | did:key + BIP-39 Seed Phrase | W3C-Standard, selbstsouverän |
| **Datensouveränität** | Solid PODs | Daten gehören dir, nicht der App |
| **Offline-DB** | SQLite + CRDTs (Automerge) | Funktioniert ohne Internet |
| **Post-Quanten** | CRYSTALS-Kyber + Dilithium | NIST-standardisiert, zukunftssicher |

---

## Plattformen

Die OneApp läuft überall — und ist von niemandem abhängig:

| Plattform | Status | Distribution |
| :--- | :--- | :--- |
| Android | ✅ Primär | F-Droid, Direkt-APK, GitHub Releases |
| Google-freies Android (GrapheneOS, CalyxOS, /e/OS) | ✅ Gleicher Build | F-Droid |
| iOS | ✅ | TestFlight, Sideloading |
| Linux Desktop | ✅ | Flatpak, Snap |
| Raspberry Pi (Home-Node) | ✅ | ARM-Linux Build |
| Web | ✅ | Browser |

**Kein Google Play. Kein Apple App Store. Die App gehört den Nutzern.**

---

## Schnellstart (Entwickler)

### Voraussetzungen
- Flutter SDK (stable channel)
- Rust + Cargo (für Substrate-Komponenten)
- Android Studio oder VS Code mit Flutter-Extension

### Setup
```bash
# Repository klonen
git clone https://github.com/project-nexus-official/oneapp.git
cd oneapp

# Dependencies installieren
flutter pub get

# App starten (Debug)
flutter run
```

### Projektstruktur
```
oneapp/
├── lib/
│   ├── core/           # Identität, Krypto, Storage
│   ├── features/
│   │   ├── chat/       # BLE Mesh-Chat + Nostr
│   │   ├── wallet/     # AETHER Wallet (VITA/TERRA/AURA)
│   │   ├── marketplace/# Lokaler Marktplatz
│   │   └── governance/ # Liquid Democracy
│   └── shared/         # UI-Komponenten, Theme, Utils
├── rust/               # Substrate Pallets (VITA, AURA, PoUW)
├── test/               # Unit + Integration Tests
├── docs/               # Technische Dokumentation
└── CLAUDE.md           # KI-Entwicklungs-Briefing
```

---

## Roadmap (Solo-Entwicklung mit KI-Unterstützung)

| Woche | Meilenstein |
| :--- | :--- |
| 1-2 | Flutter-Projekt steht, Identität (Seed Phrase) funktioniert |
| 3-4 | BLE-Scanner findet andere NEXUS-Geräte |
| 5-6 | Zwei Handys chatten direkt über Bluetooth |
| 7-8 | Multi-Hop und Verschlüsselung funktionieren |
| 9-10 | Gruppenkanäle und Nostr-Fallback |
| 11-12 | **Killer-App #1: Mesh-Chat ist funktionsfähig** |
| 13-20 | Substrate-Testnet, VITA-Pallet mit Demurrage |
| 21-30 | **Killer-App #2: Lokaler Marktplatz** |
| 31-52 | **Killer-App #3: Care-System** |

---

## Mitarbeiten

Wir suchen Architekten, keine Zuschauer.

### Gesucht (nach Priorität)

| Priorität | Rolle | Fokus |
| :--- | :--- | :--- |
| 🔴 Sofort | Flutter/Dart-Entwickler | OneApp UI, BLE-Mesh, Offline-First |
| 🔴 Sofort | Rust-Entwickler | Substrate-Pallets, Crypto |
| 🟡 Bald | Netzwerk-Engineer | BLE Mesh, Nostr, P2P |
| 🟡 Bald | Kryptograf | ZKPs, Post-Quanten |
| 🟢 Später | UX-Designer | „So einfach wie WhatsApp" |

### So fängst du an

1. Lies den [Bauplan](https://github.com/project-nexus-official/terminal/blob/docs/de/BAUPLAN_%20PROJEKT%20NEXUS_V12.0.pdf) (mindestens Kap. 1, 5, 9)
2. Lies den [Implementierungsplan](docs/IMPLEMENTIERUNGSPLAN.md) in diesem Repo
3. Schau dir die [Issues](../../issues) an — nimm dir eins oder eröffne ein neues
4. Tritt dem [Discord](DISCORD-LINK) bei (Kreis: Code)

### Code-Standards

- **Sprache:** Code + Kommentare auf Englisch, UI-Texte auf Deutsch (i18n-ready)
- **Style:** Effective Dart, Clippy-clean für Rust
- **Tests:** Jede neue Funktion braucht Unit-Tests
- **Commits:** [Conventional Commits](https://www.conventionalcommits.org/) (`feat:`, `fix:`, `docs:`)
- **Branching:** `main` = stabil, Feature-Branches = `feature/beschreibung`

---

## Warum diese Entscheidungen?

| Entscheidung | Begründung |
| :--- | :--- |
| **Flutter statt React Native** | Eine Codebase für alles, inkl. Raspberry Pi. Dart-BLE-Libraries. |
| **Substrate statt Ethereum** | Eigene Chain, keine Gas-Abhängigkeit, Demurrage nativ als Pallet |
| **Nostr statt Matrix** | Keine eigenen Server nötig. Dezentrale Relays existieren weltweit |
| **BitChat als Blaupause** | Nepal 2025 hat bewiesen, dass BLE Mesh funktioniert. Protokoll übernommen, nicht geforkt |
| **F-Droid statt Play Store** | Keine Abhängigkeit von Google oder Apple |
| **Lokale KI erst Phase 3** | Home-Node (Raspberry Pi 5) hostet das LLM. Kein Cloud-Zwang |

---

## Links

| Ressource | Link |
| :--- | :--- |
| 🌐 Webseite | [nexus-terminal.org](https://www.nexus-terminal.org) |
| 📋 Hauptrepository | [project-nexus-official/terminal](https://github.com/project-nexus-official/terminal) |
| 💬 Discord | [Genesis Circle](https://discord.gg/UpgRBnAm) |
| 📢 Telegram | [NexusProjectOfficial](https://t.me/NexusProjectOfficial) |
| ✉️ Email | [nexus.blueprint@proton.me](mailto:nexus.blueprint@proton.me) |

---

<div align="center">

*"Wer alles auf einmal baut, baut nichts. Wir bauen den Chat. Dann die Wirtschaft. Dann die Gesellschaft."*

© 2026 Projekt N.E.X.U.S. — AGPL v3 — Open Source. Open Mind. Open Future.

</div>

