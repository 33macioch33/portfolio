# 🧠 Architektura lokalnego stacku AI

> Jak zbudowałem własną infrastrukturę AI działającą **lokalnie / offline**, żeby ograniczyć
> zależność od płatnych API i pracować na własnym sprzęcie.

---

## Schemat

```mermaid
flowchart TB
    subgraph CLOUD[☁️ Chmura]
        CLAUDE[🤖 Claude Code<br/>główny asystent:<br/>współtworzy bazę wiedzy, kod i audyt]
        GPT[ChatGPT / inne modele<br/>uzupełniająco]
    end

    subgraph LOCAL[💻 Mój komputer - offline]
        direction TB
        OLL[🦙 Ollama<br/>lokalny serwer modeli<br/>qwen3:4b]
        CONT[🧩 Continue.dev<br/>asystent w VS Code]
        RAG[🔎 RAG offline<br/>bge-m3 + indeks wektorowy]
        MEM[💾 Pamięć między sesjami<br/>pliki + synchronizacja]
        MCP[🔌 Serwery MCP<br/>narzędzia: PDF, indeks, kontekst]
    end

    VAULT[(📚 Baza wiedzy<br/>Obsidian)]

    CLAUDE ==>|tworzy i edytuje notatki + kod| VAULT
    CLAUDE -.->|czyta kontekst| MCP
    GPT -.uzupełniająco.-> VAULT
    CONT --> OLL
    RAG --> VAULT
    MCP --> VAULT
    MEM --> VAULT
    CONT -.rutynowe.-> OLL
    CONT -.krytyczne.-> CLAUDE

    style CLOUD fill:#16555e,color:#fff
    style LOCAL fill:#0d343a,color:#fff
    style VAULT fill:#2bb3a3,color:#fff
    style CLAUDE fill:#11434b,color:#fff,stroke:#2bb3a3,stroke-width:2px
```

<sub>Bazę wiedzy (Obsidian) współtworzę głównie z <b>Claude Code</b> — asystent czyta kontekst
przez RAG/MCP i bezpośrednio tworzy oraz edytuje notatki i kod. Modele lokalne obsługują
pracę offline i rutynową.</sub>

---

## Komponenty

### 🦙 Lokalne modele LLM (Ollama)
- Stawianie i zarządzanie modelami uruchamianymi **lokalnie** (m.in. `qwen3:4b`) — pełny offline.
- Realne zarządzanie ograniczeniami sprzętu: dobór rozmiaru modelu pod **GPU 4 GB VRAM**, throughput.
- Integracja z edytorem przez **Continue.dev** w VS Code jako asystent kodowania.

### 🔎 RAG offline (wyszukiwanie semantyczne)
- Zbudowany **od zera**: embeddingi `bge-m3` + własny indeks wektorowy.
- Pipeline ingest → search nad bazą wiedzy; pilotaż na realnym korpusie (~1300 fragmentów).
- Pozwala „rozmawiać" z własnymi notatkami bez wysyłania ich do chmury.

### 🔌 MCP (Model Context Protocol)
- Serwery narzędziowe rozszerzające możliwości asystentów AI (np. token-efficient czytanie PDF,
  indeksowanie dużych outputów zamiast ładowania ich w całości).

### ⌨️ Własne narzędzia CLI (scrapery + auto-notatki)
- Skrypty wiersza poleceń w Pythonie, które **zbierają dane z internetu** (z obsługą throttlingu
  i błędów dostępu) i **automatycznie tworzą notatki** w bazie wiedzy — od surowego źródła do
  gotowej, połączonej notatki bez ręcznego przepisywania.
- Reużywalne i parametryzowane (jeden scraper, wiele źródeł) zamiast jednorazowych skryptów.

### 💾 Pamięć między sesjami
- Własny system, dzięki któremu narzędzie AI „pamięta" wnioski z poprzedniej pracy
  (pliki + synchronizacja do bazy wiedzy) — kolejna sesja czyta wniosek, zamiast mielić kontekst od zera.

### ⚖️ Podział pracy lokalne vs chmura
- **Współtworzenie bazy wiedzy, kod i audyt** → **Claude Code** (główny asystent, bezpośrednio
  tworzy i edytuje notatki oraz kod w projekcie).
- **Rutynowe / lekkie i w pełni offline** zadania → model lokalny (za darmo, prywatnie).
- Inne modele chmurowe → uzupełniająco, do porównania odpowiedzi.

---

## Dlaczego lokalnie

| Korzyść | Znaczenie |
|---|---|
| **Prywatność** | Dane i notatki nie opuszczają komputera |
| **Koszt** | Brak opłat za API przy rutynowej pracy |
| **Kontrola** | Pełne panowanie nad modelem, wersją, zachowaniem |
| **Nauka** | Realne zrozumienie, jak działają modele i ich ograniczenia |

---

🔙 [Powrót do README](../README.md) · ⚙️ [Pipeline badawczy](workflow.md)
