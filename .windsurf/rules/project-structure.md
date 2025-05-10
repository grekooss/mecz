---
trigger: always_on
---

# Struktura Projektu Mecz

Ten plik opisuje zalecaną strukturę katalogów dla projektu Mecz.

Mecz/
│
├── .github/ # Konfiguracja GitHub Actions (CI/CD)
│ └── workflows/
│ ├── ci.yml # Główny workflow CI (lint, testy)
│ ├── deploy-backend.yml # Workflow CD dla Supabase
│ └── deploy-frontend.yml # Workflow CD dla Expo (OTA, build)
│
├── .vscode/ # Ustawienia VS Code
│ └── settings.json
│
├── supabase/ # Konfiguracja i kod backendu Supabase
│ ├── functions/ # Supabase Edge Functions
│ │ ├── \_shared/ # Współdzielony kod dla funkcji (np. obsługa CORS, klient Supabase admin)
│ │ │ ├── cors.ts
│ │ │ └── supabaseAdmin.ts
│ │ ├── send-invitation/ # Przykład funkcji (nazwa folderu to endpoint)
│ │ │ └── index.ts # Główny plik funkcji
│ │ ├── handle-booking/
│ │ │ └── index.ts
│ │ └── (inne funkcje...)
│ ├── migrations/ # Migracje bazy danych PostgreSQL
│ │ └── xxxxx_initial_schema.sql
│ ├── seed.sql # (Opcjonalnie) Dane początkowe dla bazy
│ └── config.toml # Główny plik konfiguracyjny Supabase CLI
│
├── app/ # APLIKACJA MOBILNA (FRONTEND - Expo / React Native)
│ ├── app/ # Katalog routingu dla Expo Router (ekrany i layouty)
│ │ ├── (auth)/ # Grupa routingu dla ekranów autentykacji
│ │ │ ├── \_layout.tsx # Layout dla grupy (auth)
│ │ │ ├── login.tsx
│ │ │ └── register.tsx
│ │ ├── (app)/ # Grupa routingu dla głównej części aplikacji (po zalogowaniu)
│ │ │ ├── \_layout.tsx # Główny layout aplikacji (np. z nawigacją tab)
│ │ │ ├── index.tsx # Ekran główny (np. mapa boisk)
│ │ │ ├── map.tsx
│ │ │ ├── bookings/
│ │ │ │ ├── \_layout.tsx
│ │ │ │ ├── index.tsx # Lista rezerwacji
│ │ │ │ └── [bookingId].tsx # Szczegóły rezerwacji
│ │ │ ├── profile.tsx
│ │ │ └── ... (inne ekrany)
│ │ ├── \_layout.tsx # Główny layout aplikacji (root layout)
│ │ ├── modal.tsx # Przykład ekranu modalnego
│ │ └── +not-found.tsx # Obsługa nieznalezionych ścieżek
│ │
│ ├── assets/ # Zasoby (fonts/, images/)
│ │
│ ├── components/ # Komponenty UI
│ │ ├── ui/ # Generyczne komponenty UI (np. Button, Input)
│ │ ├── shared/ # Komponenty współdzielone aplikacji
│ │ └── forms/ # Komponenty formularzy (np. LoginForm)
│ │
│ ├── constants/ # Stałe wartości (np. klucze MMKV, nazwy tras, domyślne konfiguracje)
│ │ ├── api.ts
│ │ ├── storageKeys.ts
│ │ └── index.ts
│ │
│ ├── contexts/ # (Opcjonalnie) Konteksty React, jeśli nie wszystko pasuje do Zustand
│ │ └── ThemeContext.tsx
│ │
│ ├── hooks/ # Niestandardowe hooki React
│ │ ├── useAuth.ts
│ │ ├── useLocation.ts
│ │ └── useNotifications.ts
│ │
│ ├── lib/ # Biblioteki pomocnicze, konfiguracja, typy
│ │ ├── supabase/ # Konfiguracja klienta Supabase dla frontendu
│ │ │ └── client.ts
│ │ ├── react-query/ # Konfiguracja TanStack Query, niestandardowe hooki query/mutation
│ │ │ ├── queryClient.ts
│ │ │ ├── useUserQuery.ts
│ │ │ └── useFieldsQuery.ts
│ │ ├── zustand/ # Sklepy Zustand
│ │ │ ├── authStore.ts
│ │ │ └── settingsStore.ts
│ │ ├── validation/ # Schematy Zod
│ │ │ ├── authSchemas.ts
│ │ │ └── bookingSchemas.ts
│ │ ├── mmkv/ # Konfiguracja i utilsy dla MMKV
│ │ │ └── storage.ts
│ │ ├── nativewind/ # (Opcjonalnie) Konfiguracja NativeWind, jeśli potrzebna
│ │ │ └── setup.ts
│ │ └── utils/ # Funkcje pomocnicze
│ │ ├── dateUtils.ts # (date-fns lub dayjs)
│ │ ├── formatters.ts
│ │ └── helpers.ts
│ │
│ ├── services/ # (Alternatywa dla lib/react-query) Bezpośrednie funkcje API
│ │
│ ├── translations/ # (Opc.) Pliki tłumaczeń (en.json, pl.json)
│ │
│ ├── types/ # Globalne typy TypeScript (api.ts, navigation.ts)
│ │
│ ├── app.config.js # Konfiguracja Expo
│ ├── babel.config.js
│ ├── eas.json # Konfiguracja EAS
│ ├── metro.config.js
│ ├── package.json # Zależności i skrypty frontendu
│ ├── tailwind.config.js # Konfiguracja NativeWind
│ └── tsconfig.json # Konfiguracja TypeScript frontendu
│
├── .env # Zmienne środowiskowe lokalne (NIE W GIT)
├── .env.example
├── .eslintignore
├── .eslintrc.js # Konfiguracja ESLint
├── .gitattributes
├── .gitignore
├── jest.config.js # Konfiguracja Jest
├── package.json # Główny package.json (monorepo)
├── prettier.config.js # Konfiguracja Prettier
├── README.md # Opis projektu
└── tsconfig.base.json # (Opc.) Wspólna bazowa konfiguracja TS (monorepo)
