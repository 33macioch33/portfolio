# Maciej Ageev — AI Tools Specialist · Portfolio

> Praktyczne wykorzystanie narzędzi AI: lokalne modele LLM, systemy RAG, automatyzacja
> i orkiestracja asystentów kodowania w realnym, wieloskładnikowym projekcie badawczym.

📍 Serock · ✉ ageevmaciek@gmail.com · 📞 790 778 332

---

## Kim jestem

Nie tylko *używam* modeli językowych — **buduję wokół nich działające systemy**.
Samodzielnie postawiłem i utrzymuję prywatny projekt badawczy do analizy rynków
finansowych, w którym łączę: lokalnie hostowane modele LLM, własny system RAG offline,
pamięć między sesjami oraz zautomatyzowane pipeline'y z bramkami jakości.

Wykształcenie techniczne (technik mechatronik) daje mi inżynierską dyscyplinę:
**weryfikuję wyniki zamiast im ufać** i myślę w kategoriach „gdzie to się może zepsuć".

> ⚠️ Główny projekt jest **prywatny** (zawiera autorskie badania). Poniżej znajduje się
> sanityzowany przegląd architektury i kompetencji — bez wrażliwych szczegółów.

---

## Mój główny projekt — widok grafu wiedzy (Obsidian)

Cały projekt prowadzę jako połączoną bazę wiedzy w Obsidian. Graf poniżej pokazuje
skalę i strukturę powiązań notatek badawczych, decyzji i komponentów systemu:

![Graf główny projektu](assets/graph-overview.jpg)

<sub>Pełny graf wiedzy projektu badawczego — każdy węzeł to notatka (strategia, audyt,
decyzja, komponent infrastruktury AI), krawędzie to powiązania między nimi. Gęsty
rdzeń to rdzeń badawczy, satelitarne klastry to wydzielone obszary tematyczne.</sub>

---

## Co realnie zbudowałem

### 🧠 Lokalne modele LLM (self-hosting / offline)
- Stawianie i zarządzanie modelami lokalnie przez **Ollama** (m.in. `qwen3:4b`) — pełny offline
- Integracja z edytorem przez **Continue.dev** w VS Code (asystent kodowania na własnym GPU)
- Zarządzanie ograniczeniami sprzętu (GPU 4 GB VRAM): dobór modelu, throughput, tryby pracy
- Świadomy podział zadań: rutynowe → model lokalny; krytyczne → model chmurowy premium

### 🔎 RAG i wyszukiwanie semantyczne
- Zbudowany od zera **lokalny RAG offline**: embeddingi `bge-m3` + własny indeks wektorowy
- Pipeline ingest → search; pilotaż na realnym korpusie (~1300 fragmentów) z wysoką trafnością
- Token-efficient czytanie dokumentów (ekstrakcja/wyszukiwanie zamiast ładowania całości)

### ⚙️ Automatyzacja i orkiestracja AI
- **Bramkowany pipeline badawczy** w stylu mini-działu R&D: generowanie → kod → audyt →
  walidacja → raport, z automatycznymi bramkami jakości
- Praca z **MCP (Model Context Protocol)** — serwery narzędziowe rozszerzające asystentów AI
- Własny **system pamięci między sesjami** (pliki + synchronizacja), by narzędzie AI
  „pamiętało" wnioski z poprzedniej pracy
- Web scrapery do pozyskiwania danych (z obsługą throttlingu i edge-case'ów)

### 🧪 Dyscyplina weryfikacji (to mnie wyróżnia)
- Wbudowana zasada: **„każdy wynik jest podejrzany, dopóki nie udowodnię, że jest poprawny"**
- Wykrywanie błędów typu *lookahead / data leakage*, które fałszują wyniki analiz
- Testy out-of-sample, walk-forward i symulacje Monte Carlo jako standard, nie dodatek

---

## Stack i narzędzia

| Kategoria | Narzędzia |
|---|---|
| Modele lokalne | Ollama, Continue.dev, qwen3 |
| RAG / embeddings | bge-m3, własny indeks wektorowy (numpy) |
| Asystenci AI | Claude (Anthropic), ChatGPT (OpenAI), Gemini, Grok |
| Automatyzacja | MCP, pipeline z bramkami, pamięć między sesjami |
| Język / narzędzia | Python, Git/GitHub, PowerShell/CLI, Markdown/Obsidian |
| Generatywne (obraz) | Midjourney, NanoBanana Pro |

---

## Wykształcenie i języki

- **Technik Mechatronik** — ukończone 2025 (elektronika, automatyka, sterowniki PLC)
- **Certyfikat** — kurs programowania w Python
- **Angielski B2/B2+** — swobodna praca z dokumentacją techniczną

---

## Kontakt

✉ ageevmaciek@gmail.com · 📞 790 778 332 · 📍 Serock

<sub>Repozytorium jest przeglądem portfolio. Główny kod projektu pozostaje prywatny
ze względu na autorski charakter badań — chętnie omówię szczegóły na rozmowie.</sub>
