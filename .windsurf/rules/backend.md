---
trigger: always_on
description: Reguły backendowe dla Supabase, Edge Functions (TypeScript/Deno), bezpieczeństwa, walidacji oraz integracji z Stripe.
---

# Supabase

- Używaj Supabase do autentykacji, bazy danych, storage i funkcji edge.
- Pisząc funkcje edge, korzystaj z TypeScript i środowiska Deno.
- Do interakcji z bazą używaj oficjalnej biblioteki `supabase-js`.
- Waliduj dane wejściowe i wyjściowe za pomocą Zod.
- Unikaj enumów – stosuj typy literalne lub mapy.
- Stosuj wzorce wczesnego zwracania (early return) w obsłudze błędów.
- Loguj błędy i obsługuj przypadki brzegowe na początku funkcji.
- Wrażliwe operacje wykonuj tylko z odpowiednimi uprawnieniami (np. `service_role_key` używaj tylko tam, gdzie jest to absolutnie konieczne i nie ma innego sposobu na osiągnięcie celu z uprawnieniami użytkownika).
- Synchronizuj status subskrypcji Stripe z użytkownikiem w Supabase.
- Testuj funkcje edge lokalnie przed wdrożeniem.

# Bezpieczeństwo

- Waliduj i sanityzuj wszystkie dane wejściowe.
- Stosuj zasady minimalnych uprawnień dla kluczy API i tokenów.
- Zabezpiecz endpointy przed nieautoryzowanym dostępem.
- Weryfikuj uprawnienia użytkownika w każdej operacji na backendzie.
- Stosuj logikę obsługi błędów globalnie (np. error boundaries).

# Walidacja

- Używaj Zod do walidacji danych (zarówno wejściowych, jak i z API).
- Twórz schematy Zod dla każdego endpointu/funkcji.

# Integracja Stripe

- Implementuj webhooki Stripe do obsługi subskrypcji.
- Zabezpiecz webhooki przed nieautoryzowanym dostępem.
- Aktualizuj status subskrypcji użytkownika na podstawie eventów Stripe.

# Testowanie

- Pisz testy jednostkowe i integracyjne dla funkcji edge.
- Stosuj mocki dla zewnętrznych integracji podczas testów.
