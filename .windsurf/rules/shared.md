---
trigger: always_on
---

# Shared Rules for Mecz

W tym pliku znajdziesz wspólne zasady obowiązujące w całym projekcie (frontend, backend, testy, architektura, workflow).

## Tech Stack

- Expo SDK (React Native)
- TypeScript 5
- Zustand
- TanStack Query
- React Hook Form + Zod
- NativeWind (Tailwind CSS)
- Supabase (backend)
- date-fns / dayjs
- react-native-mmkv
- Jest, React Native Testing Library, Detox

> Szczegóły i uzasadnienia wyboru znajdziesz w `.docs/tech-stack.md`.

## Struktura Projektu

Szczegółowy opis zalecanej struktury katalogów projektu MeczApp znajduje się w osobnym pliku:

- [`project-structure.md`](./project-structure.md)

> Jeśli zmieniasz strukturę katalogów, zaktualizuj plik `project-structure.md` oraz powiązane sekcje w innych plikach zasad.

## Coding practices (Wspólne zasady)

- Stosuj TypeScript wszędzie (brak plików .js).
- Używaj feedbacku z linterów do poprawy kodu.
- Early return i obsługa błędów na początku funkcji (guard clauses).
  - Staraj się, aby 'happy path' (główna, poprawna ścieżka wykonania) znajdował się na końcu funkcji, po obsłużeniu przypadków brzegowych i błędów.
- Unikaj zagnieżdżonych if/else – preferuj if-return.
- Nazwy plików i komponentów w stylu PascalCase (np. UserProfile.tsx).
- Nazwy hooków z prefixem use (np. useUserStore).
- Każdy komponent/ekran z krótką dokumentacją w komentarzu.
- Priorytet: obsługa przypadków brzegowych i czytelność kodu.
- Unikaj duplikacji kodu – stosuj modularność.
- Dokumentuj workflow i decyzje architektoniczne w README i .docs.
- Use guard clauses to handle preconditions and invalid states early.
- Implement proper error logging and user-friendly error messages.
- Consider using custom error types or error factories for consistent error handling.

## Konwencje Nazewnictwa (TypeScript & Ogólne)

- **Klasy, Typy, Interfejsy:** `PascalCase` (np. `UserProfile`, `AuthResponse`).
- **Zmienne, funkcje, metody:** `camelCase` (np. `userName`, `getUserData`).
- **Stałe, wartości enumów (jeśli używane):** `UPPER_CASE_SNAKE_CASE` (np. `MAX_USERS`, `OrderStatus.COMPLETED`).
- **Pliki komponentów `.tsx`:** `PascalCase.tsx` (np. `UserProfile.tsx`).
- **Inne pliki `.ts` (np. hooki, utils, serwisy):** `kebab-case.ts` (preferowane) lub `camelCase.ts` (np. `use-auth-store.ts`, `string-utils.ts`).
- **Katalogi:** `kebab-case` (np. `user-profile`, `shared-components`).
- **Funkcje:** Powinny zaczynać się od czasownika opisującego działanie (np. `fetchUserData`, `calculateTotalPrice`, `isValidInput`).
- **Zmienne boolowskie:** Powinny używać prefiksów `is`, `has`, `should`, `can` (np. `isLoading`, `hasPermission`, `shouldUpdate`).

## Zasady Pisania Funkcji (TypeScript)

- **Krótkie i jedna odpowiedzialność:** Dąż do tego, aby funkcje były krótkie i realizowały jedno zadanie (sugestia: poniżej 20-25 linii kodu).
- **RORO (Request Object - Return Object):** Dla funkcji przyjmujących wiele parametrów (np. > 3) lub zwracających wiele wartości, rozważ użycie obiektu jako argumentu i/lub wartości zwrotnej. Zdefiniuj dla nich odpowiednie typy/interfejsy.
- **Wartości domyślne:** Używaj wartości domyślnych dla parametrów funkcji tam, gdzie to zasadne.
- **Czyste funkcje:** Preferuj czyste funkcje (pure functions), które dla tych samych danych wejściowych zawsze zwracają ten sam wynik i nie mają efektów ubocznych.

## Praca z Danymi (TypeScript)

- **Niemutowalność:** Preferuj niemutowalne struktury danych.
  - Używaj `readonly` dla właściwości obiektów i tablic, które nie powinny być modyfikowane po utworzeniu.
  - Używaj `as const` dla literałów obiektowych i tablicowych, aby uczynić je w pełni niemutowalnymi i zawęzić typy.
- **`import type`:** Jeśli importujesz typy lub interfejsy, które są używane tylko w kontekście typowania (nie jako wartości w kodzie wykonawczym), używaj składni `import type { MyType } from './myModule';`.

## Dokumentacja Kodu

- **JSDoc:** Stosuj JSDoc dla wszystkich eksportowanych funkcji, klas (jeśli używane), typów i interfejsów. Opisuj parametry, wartości zwracane i ogólne przeznaczenie.
- **Komentarze:** Używaj komentarzy do wyjaśniania skomplikowanych fragmentów logiki lub decyzji projektowych, które nie są oczywiste z samego kodu.
- **README:** Dbaj o aktualność głównego pliku `README.md` projektu oraz `README.md` w kluczowych modułach/katalogach, opisując ich zawartość i sposób użycia.
- **Google Technical Writing Style Guide:** Przy pisaniu dokumentacji i komentarzy staraj się stosować do zasad z tego przewodnika (aktywna strona, czas teraźniejszy, zwięzłość, jasność).
