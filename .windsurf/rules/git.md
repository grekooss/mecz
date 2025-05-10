---
trigger: always_on
description: Zasady pracy z Git, konwencje commitów, strategia branchowania i Pull Requesty.
---

# Zasady Pracy z Git

Utrzymanie czystej i zrozumiałej historii Git jest kluczowe dla efektywnej pracy zespołowej i łatwiejszego zarządzania projektem.

## Konwencje Nazewnictwa Commitów

Stosujemy **Conventional Commits**. Format wiadomości commita powinien być następujący:

```
<typ>[opcjonalny zakres]: <opis>

[opcjonalne ciało]

[opcjonalna stopka]
```

- **Typy commitów:**
  - `feat`: Dodanie nowej funkcjonalności.
  - `fix`: Poprawka błędu.
  - `docs`: Zmiany w dokumentacji.
  - `style`: Zmiany dotyczące formatowania kodu, które nie wpływają na jego działanie (białe znaki, formatowanie, średniki itp.).
  - `refactor`: Zmiany w kodzie, które ani nie naprawiają błędu, ani nie dodają nowej funkcjonalności (np. restrukturyzacja kodu).
  - `perf`: Zmiany poprawiające wydajność.
  - `test`: Dodawanie brakujących testów lub poprawianie istniejących.
  - `build`: Zmiany wpływające na system budowania lub zależności zewnętrzne (np. Expo, npm).
  - `ci`: Zmiany w konfiguracji CI/CD (np. GitHub Actions).
  - `chore`: Inne zmiany, które nie modyfikują kodu źródłowego ani testów (np. aktualizacja narzędzi, konfiguracji projektu).

- **Opis:** Krótki, zwięzły opis zmian w czasie teraźniejszym, tryb rozkazujący (np. "Add login component" zamiast "Added login component" lub "Adds login component").
- **Ciało (opcjonalne):** Bardziej szczegółowy opis zmian, motywacja, kontekst.
- **Stopka (opcjonalna):** Informacje o łamaniu kompatybilności (BREAKING CHANGE) lub powiązanych issue (np. `Closes #123`).

## Strategia Branchowania

Sugerowana prosta strategia (podobna do GitHub Flow):

1.  **`main` (lub `master`):** Główny branch, zawsze zawiera stabilną, gotową do wdrożenia wersję aplikacji. Bezpośrednie commity do `main` są zabronione.
2.  **Feature Branches:** Każda nowa funkcjonalność, poprawka błędu czy refaktoryzacja powinna być tworzona na osobnym branchu wychodzącym z `main`.
    - Nazewnictwo branchy: `typ/opis-zadania` (np. `feat/user-authentication`, `fix/login-button-bug`, `refactor/simplify-payment-service`).
    - Małe, częste commity na feature branchu.
3.  **Pull Request (PR):** Po zakończeniu prac na feature branchu, tworzony jest Pull Request do `main`.

## Pull Requesty (PR)

- **Opis PR:** Powinien jasno opisywać, co zostało zrobione, dlaczego i jak to przetestować. Jeśli PR zamyka jakieś issue, należy je podlinkować.
- **Code Review:** Każdy PR musi zostać zrecenzowany przez co najmniej jednego innego członka zespołu przed mergowaniem (patrz `code-review.md`).
- **Testy:** Wszystkie testy muszą przechodzić pomyślnie.
- **Aktualność z `main`:** Przed mergowaniem, feature branch powinien być zaktualizowany względem `main` (preferowany rebase, jeśli to możliwe i bezpieczne w kontekście zespołu, w przeciwnym razie merge).
- **Squash and Merge / Rebase and Merge:** Rozważ użycie "Squash and Merge" lub "Rebase and Merge" (jeśli zespół jest z tym komfortowy) przy mergowaniu PR do `main`, aby utrzymać czystą historię commitów na głównym branchu. Decyzja zależy od preferencji zespołu.

## Inne Dobre Praktyki

- **Częste pobieranie zmian:** Regularnie pobieraj zmiany z repozytorium zdalnego (`git pull --rebase` na feature branchach, jeśli pracujesz sam na branchu).
- **Unikaj dużych commitów:** Staraj się, aby commity były atomowe i dotyczyły jednej logicznej zmiany.
- **Nie commituj niepotrzebnych plików:** Używaj `.gitignore` do ignorowania plików generowanych przez IDE, zależności, logów itp.
- **Rozwiązywanie konfliktów:** Rozwiązuj konflikty lokalnie, dokładnie analizując zmiany.
