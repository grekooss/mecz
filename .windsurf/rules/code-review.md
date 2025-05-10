---
trigger: always_on
description: Wytyczne i checklista do przeprowadzania przeglądów kodu (code review).
---

# Zasady Przeglądu Kodu (Code Review)

Celem przeglądu kodu jest poprawa jakości kodu, dzielenie się wiedzą w zespole, utrzymanie spójności oraz wczesne wykrywanie potencjalnych problemów.

## Ogólne Zasady dla Recenzenta

- **Bądź konstruktywny i uprzejmy:** Celem jest pomoc, a nie krytyka. Formułuj uwagi jako sugestie.
- **Zrozum kontekst:** Zapoznaj się z celem zmian (np. opisem zadania, issue) przed rozpoczęciem review.
- **Skup się na ważnych aspektach:** Nie trać czasu na drobne kwestie stylistyczne, jeśli są one obsługiwane przez lintery/formattersy. Skup się na logice, architekturze, potencjalnych błędach, czytelności i testach.
- **Proponuj rozwiązania:** Jeśli widzisz problem, staraj się zasugerować, jak można go rozwiązać.
- **Zadawaj pytania:** Jeśli czegoś nie rozumiesz, pytaj. To może pomóc autorowi wyjaśnić intencje lub zidentyfikować niejasności w kodzie.
- **Bądź terminowy:** Staraj się przeprowadzać review w rozsądnym czasie, aby nie blokować pracy innych.
- **Chwal dobre rozwiązania:** Nie zapominaj o pozytywnym feedbacku.

## Ogólne Zasady dla Autora Kodu

- **Przygotuj PR:** Upewnij się, że Twój Pull Request ma jasny tytuł i opis, wyjaśniający co i dlaczego zostało zmienione. Podlinkuj powiązane issue.
- **Samodzielne review:** Przejrzyj swój kod przed wysłaniem PR, tak jakbyś recenzował kod kogoś innego.
- **Odpowiadaj na komentarze:** Adresuj wszystkie komentarze recenzenta. Jeśli się nie zgadzasz, wyjaśnij dlaczego.
- **Nie bierz uwag personalnie:** Pamiętaj, że celem jest lepszy kod, a nie krytyka Twoich umiejętności.
- **Małe PR:** Staraj się, aby Pull Requesty były małe i skupione na jednym zadaniu. Ułatwia to review.

## Checklista Przeglądu Kodu

Podczas przeglądu kodu zwróć uwagę na następujące aspekty:

### 🎯 Cel i Funkcjonalność

- [ ] Czy kod realizuje założone cele (opisane w zadaniu/issue)?
- [ ] Czy wszystkie przypadki użycia zostały obsłużone?
- [ ] Czy kod wprowadza jakieś niepożądane efekty uboczne?

### 📐 Architektura i Design

- [ ] Czy kod jest zgodny z ogólną architekturą projektu?
- [ ] Czy zastosowano odpowiednie wzorce projektowe?
- [ ] Czy logika jest dobrze zorganizowana i czytelna?
- [ ] Czy kod jest modularny i reużywalny (tam, gdzie to zasadne)?
- [ ] Czy nie ma nadmiernej złożoności (np. zbyt wiele zagnieżdżeń, skomplikowane warunki)?

### 🐛 Potencjalne Błędy i Obsługa Błędów

- [ ] Czy kod poprawnie obsługuje przypadki brzegowe i błędy?
- [ ] Czy walidacja danych wejściowych jest wystarczająca?
- [ ] Czy nie ma ryzyka wycieków pamięci lub problemów z wydajnością?
- [ ] Czy kod jest bezpieczny (np. ochrona przed typowymi atakami, jeśli dotyczy)?

### 🧪 Testy

- [ ] Czy dodano odpowiednie testy jednostkowe i/lub integracyjne?
- [ ] Czy istniejące testy nadal przechodzą?
- [ ] Czy testy pokrywają kluczowe ścieżki i przypadki brzegowe?
- [ ] Czy testy są czytelne i łatwe w utrzymaniu?

### 📖 Czytelność i Konwencje

- [ ] Czy kod jest łatwy do zrozumienia?
- [ ] Czy nazwy zmiennych, funkcji, klas są jasne i opisowe?
- [ ] Czy kod jest zgodny z przyjętymi konwencjami nazewnictwa i formatowania (patrz `shared.mdc` i inne pliki zasad)?
- [ ] Czy usunięto zbędny, zakomentowany kod?
- [ ] Czy magiczne liczby/stringi zostały zastąpione stałymi?

### 📚 Dokumentacja i Komentarze

- [ ] Czy dodano lub zaktualizowano niezbędną dokumentację (np. JSDoc, README)?
- [ ] Czy skomplikowane fragmenty kodu są wyjaśnione komentarzami?

### 🚀 Wydajność

- [ ] Czy kod jest zoptymalizowany pod kątem wydajności (jeśli jest to krytyczny aspekt)?
- [ ] Czy nie ma oczywistych wąskich gardeł?

### ♿ Dostępność (jeśli dotyczy UI)

- [ ] Czy komponenty UI są dostępne (zgodne z zasadami z `frontend.md`)?

### ✨ Inne

- [ ] Czy PR jest odpowiednio mały i skupiony na jednym zadaniu?
- [ ] Czy opis PR jest jasny i kompletny?

--- 

Pamiętaj, że ta checklista jest przewodnikiem. Nie wszystkie punkty będą miały zastosowanie do każdego PR. Używaj jej elastycznie, dostosowując do kontekstu.
