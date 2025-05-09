---
trigger: manual
glob:
description: Reguły zarządzania stanem aplikacji (Zustand, TanStack Query, React Hook Form).
---

# Zustand

- Używaj Zustand do globalnego zarządzania stanem aplikacji.
- Twórz przejrzyste i modularne store'y, unikaj duplikacji kodu.
- Stosuj TypeScript interfaces do typowania stanu.
- Unikaj enumów na rzecz typów literalnych.
- Minimalizuj użycie useEffect i setState – preferuj stan pochodny i memoizację.
- Eksportuj funkcje i store'y jako named exports.

# TanStack React Query

- Używaj do pobierania, cache’owania i synchronizacji danych z API.
- Stosuj query keys zgodnie z zasadami unikalności i czytelności.
- Obsługuj loading, error i success states w komponentach.
- Implementuj optymistyczne aktualizacje tam, gdzie to możliwe.

# React Hook Form + Zod

- Używaj React Hook Form do zarządzania formularzami.
- Waliduj dane formularzy za pomocą Zod.
- Typuj dane wejściowe formularzy przez inferencję typów ze schematów Zod.
