---
trigger: always_on
description: Reguły i konwencje dla frontendu (Expo, React Native, TypeScript, Zustand, TanStack Query, React Hook Form, Zod, NativeWind, dostępność, struktura).
---

# Frontend – zasady ogólne

- Cały frontend budujemy w Expo (React Native) z TypeScript.
- Komponenty piszemy jako funkcjonalne (hooks), unikamy klas.
- Logikę wydzielamy do customowych hooków (`/hooks`).
- Stosujemy modularną strukturę katalogów (`/components`, `/screens`, `/hooks`, `/lib`, `/assets`).
- Każdy ekran to osobny plik/folder w `/screens`.
- Komponenty UI trzymamy w `/components/ui` (np. z nativecn-ui lub własne).
- Typy współdzielone umieszczamy w `/types` lub `/lib/types`.
- Preferuj interfejsy (`interface`) nad aliasami typów (`type`) do definiowania kształtów obiektów; `type` stosuj dla typów prostych, unii, кортеży itp.

# Stylowanie (NativeWind/Tailwind CSS)

- Używamy NativeWind (Tailwind CSS dla React Native) do stylowania.
- Stosujemy klasy utility, unikamy stylów inline.
- Stosuj podejście mobile-first przy projektowaniu responsywnym.
- Konfigurujemy tailwind.config.js dla wspólnego motywu, kolorów i responsywności.
- Preferujemy klasy dark: do obsługi trybu ciemnego.
- Responsywność: używamy klas sm:, md: itd.
- Dla pojedynczych, niestandardowych wartości stosujemy notację w nawiasach kwadratowych (np. w-[120px]).
- Rozważnie używaj dyrektywy `@apply` – jej nadużywanie może prowadzić do utraty czytelności i zalet utility classes. Stosuj ją głównie do grupowania często powtarzających się, specyficznych kombinacji klas w komponentach.

# Dostępność

- Używamy odpowiednich ról i atrybutów dostępności (np. `accessibilityRole`, `accessibilityLabel`).
- Zapewniamy czytelność tekstów, odpowiedni kontrast i rozmiary czcionek.
- Komponenty interaktywne muszą być obsługiwalne z klawiatury i screen readera.
- Stosujemy aria-\* tylko tam, gdzie nie wystarczają natywne propsy dostępności.

# Zarządzanie stanem i danymi

- Globalny stan: Zustand, store’y modularne, typowane przez TypeScript.
- Pobieranie i synchronizacja danych: TanStack Query (obsługa loading/error/success, cache, optimistic updates).
- Formularze: React Hook Form + Zod (walidacja, typowanie przez inferencję ze schematów).
- Komunikacja z backendem (Supabase) przez `supabase-js`.

# Testowanie

- Testy jednostkowe: Jest, React Native Testing Library.
- Testy E2E: Detox.
- Mockujemy zewnętrzne integracje i API.
- Pokrywamy testami wszystkie eksportowane funkcje i komponenty.

# Praktyki kodowania

- Stosujemy TypeScript wszędzie (brak plików .js).
- Early return i obsługa błędów na początku funkcji.
- Unikamy zagnieżdżonych if/else – preferujemy guard clauses.
- Nazwy plików i komponentów w stylu PascalCase (np. UserProfile.tsx).
- Nazwy hooków z prefixem use (np. useUserStore).
- Każdy komponent/ekran z krótką dokumentacją w komentarzu.
- **Safe Area:** Używaj `SafeAreaView` z `react-native-safe-area-context` na najwyższym poziomie ekranów, aby poprawnie obsługiwać wcięcia systemowe (notche, paski statusu) na iOS i Android. Unikaj hardkodowania paddingów/marginesów dla safe area.
- **Optymalizacja List (FlatList/SectionList):**
    - Stosuj `keyExtractor` lub `key` prop dla elementów listy.
    - Używaj `React.memo` dla komponentów elementów listy, aby unikać niepotrzebnych re-renderów.
    - Rozważ użycie propów optymalizacyjnych jak `removeClippedSubviews`, `maxToRenderPerBatch`, `windowSize`, `initialNumToRender` dla długich list.
    - Unikaj anonimowych funkcji w `renderItem`.
- **Optymalizacja Obrazów:**
    - Używaj odpowiednich formatów (np. WebP, jeśli wspierane przez `expo-image`).
    - Podawaj wymiary obrazów, jeśli są znane.
    - Implementuj lazy loading dla obrazów poza widocznym obszarem (np. za pomocą `expo-image`).
- **Globalna Obsługa Błędów:** Rozważ implementację globalnego mechanizmu do łapania nieobsłużonych błędów (np. Error Boundaries w React lub dedykowane rozwiązania Expo/React Native) i logowania ich do serwisu monitorującego (np. Sentry).

# Struktura katalogów (przykład)

- `/app` – główny katalog kodu aplikacji (Expo Router)
- `/app/screens` – ekrany aplikacji
- `/app/components` – komponenty wielokrotnego użytku
- `/app/components/ui` – komponenty UI (np. przyciski, inputy)
- `/app/hooks` – customowe hooki
- `/app/lib` – pomocnicze funkcje, serwisy, typy
- `/app/assets` – obrazy, ikony, fonty
- `/app/types` – typy współdzielone

# Inne narzędzia i praktyki

- Do dat: `date-fns` lub `dayjs`.
- Dane lokalne: `react-native-mmkv`.
- Konfiguracja środowiskowa: `app.config.js`, `eas.json`.
- Dokumentujemy workflow i decyzje architektoniczne w README i .docs.

# Bezpieczeństwo (Frontend)

- **Walidacja Danych Wejściowych:** Waliduj wszystkie dane wprowadzane przez użytkownika (np. w formularzach) przed wysłaniem ich na backend, używając Zod.
- **Sanityzacja Danych:** W przypadku wyświetlania danych pochodzących z zewnętrznych źródeł (np. treści generowane przez użytkowników), upewnij się, że są one odpowiednio sanityzowane, aby zapobiec atakom XSS.
- **Bezpieczne Przechowywanie Danych:** Do przechowywania wrażliwych danych lokalnie (np. tokeny sesji) używaj bezpiecznych mechanizmów jak `react-native-encrypted-storage` (jeśli używasz) lub `expo-secure-store`.
- **Komunikacja HTTPS:** Upewnij się, że cała komunikacja z backendem odbywa się poprzez HTTPS.

# Inspiracje i źródła

- [Expo](https://docs.expo.dev/)
- [React Native](https://reactnative.dev/)
- [NativeWind](https://www.nativewind.dev/)
- [TanStack Query](https://tanstack.com/query/latest/docs/react-native/overview)
- [Zustand](https://docs.pmnd.rs/zustand/getting-started/introduction)
- [React Hook Form](https://react-hook-form.com/)
- [Zod](https://zod.dev/)
- [Supabase](https://supabase.com/docs)
- [Cursor Directory Rules](https://cursor.directory/rules)
