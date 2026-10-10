# EquiPlus AI: Flutter web app

One Flutter codebase that builds for the web (Vercel), Android and iOS. Follows the EquiPlus AI Official Brand Sheet: Deep Sapphire background, Cyber Teal, Shariah Green and Palestine Crimson accents, Platinum White text, Montserrat headings and Inter body text. The logo is `assets/logo-dark.jpg`, taken unchanged from the brand document.

## Screens

| Screen | What it does |
|---|---|
| Login / Sign up | Email and password, terms acceptance on sign-up, demo mode when Supabase is not configured |
| Dashboard | Greeting, PSX and NYSE open/closed clocks, portfolio value and gain, local vs global split, ethical alerts, quick actions |
| Screener | BDS, strict Shariah (KMI-30) and PSX-only filters; asset detail; clean peer suggestions for flagged assets |
| Analyze | Startup inputs, three-scenario five-year growth model, break-even, risk flags, pitch deck PDF upload with 9-section review |
| Portfolio | Holdings, market value, cost and profit/loss in PKR or USD, add holding |
| Plans | PKR and USD plans from the website; checkout placeholder |
| Account | Profile name, base currency, ethical defaults, subscription, legal links, deletion request, sign out |

Navigation is a side rail on screens 900 px and wider, and a bottom bar on phones.

## Project layout

```
lib/
  main.dart               entry point, session restore, app shell switch
  config.dart             Supabase URL/key and site settings (via --dart-define)
  theme.dart              brand tokens and Material theme
  format.dart             money and percent formatting
  models.dart             Asset, Holding, UserProfile
  growth_model.dart       predictive growth engine (mirrors the website)
  deck_review.dart        9-section pitch deck check
  market_clock.dart       PSX and NYSE session status
  sample_data.dart        demo assets and holdings
  app_state.dart          signed-in user and shared data
  services/               auth, market data, PDF text extraction
  screens/                login, shell, dashboard, screener, analysis, portfolio, plans, account
  widgets/common.dart     shared cards, pills, clocks, demo banner
test/                     unit tests for the growth model, market hours and theme
assets/logo-dark.jpg      brand logo
```

## Set up

Requires Flutter 3.27 or newer (uses `withValues`, `CardThemeData`, `WidgetStateProperty`).

```bash
# 1. Generate the platform folders (web, android, ios) around this lib/ folder
cd equiplus_ai
flutter create --platforms=web,android,ios --project-name equiplus_ai .
#    When asked, keep the existing lib/, pubspec.yaml and assets/ files.

# 2. Install packages and run the tests
flutter pub get
flutter test

# 3. Run in demo mode (no backend needed)
flutter run -d chrome
```

Set the browser title and description in `web/index.html` to "EquiPlus AI" and the tagline from the brand sheet.

## Connect Supabase

Run `supabase/schema.sql` and `supabase/auth-and-billing.sql` from the website project, then build or run with your project values:

```bash
flutter run -d chrome \
  --dart-define=SUPABASE_URL=https://YOUR-PROJECT.supabase.co \
  --dart-define=SUPABASE_ANON_KEY=YOUR_ANON_KEY
```

Never put the service-role key in the app. Only the anon key belongs in client code.

## Build and deploy to Vercel

```bash
flutter build web --release \
  --dart-define=SUPABASE_URL=... --dart-define=SUPABASE_ANON_KEY=... \
  --dart-define=SITE_URL=https://equiplus.ai
```

Vercel does not install Flutter by default, so deploy the built output folder: `cd build/web && vercel --prod`. Mobile builds: `flutter build apk --release` and `flutter build ipa --release` (on a Mac with Xcode).

## Known gaps (be honest with users and stakeholders)

- **Not yet compiled in this build environment.** The Flutter SDK could not be downloaded here, so the code has not been compiled or run. Run `flutter analyze` and `flutter test` first and fix any issues.
- **Prices are placeholders.** The database has no live price column yet; holdings use average cost. Connect the PSX and US feeds through n8n first.
- **Demo FX rate.** USD and PKR conversion uses `demoUsdToPkr` in `config.dart` until a live forex feed is connected.
- **Holdings added in the app stay on the device** for the session. Saving them to the `holdings` table is the next step.
- **Account deletion** is a support request by email. Automating it needs a server function.
- **Language.** The interface is English only. The website is bilingual; Urdu for the app is the next release, with right-to-left layout.
- **Syncfusion PDF.** Syncfusion requires a free community licence registration for eligible organisations. Register the key in `main()` before release, per Syncfusion's licensing terms.
- **Payments and AI commentary** are not connected; the screens show placeholders.

## Not investment advice

All market data shown is sample data. Analysis outputs are informational estimates built from the figures entered.
