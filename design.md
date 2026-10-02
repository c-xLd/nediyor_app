# NeDiyor Mobile App — Design System & UX Specification

Bu dosya NeDiyor mobil uygulamasının ana UI/UX kaynağıdır.

## Core experience

**Question → Evidence → Decision → Action**

Mobil uygulama web sitesinin küçültülmüş hali değildir. Kullanıcıyı ürün sorusundan kanıta, kanıttan karara ve karardan aksiyona götüren hızlı bir karar motorudur.

## Navigation

Beş ana sekme:
1. Ana Sayfa
2. Keşfet
3. Fırsatlar
4. Kıyasla
5. Takibim

## Product detail

Öncelik:
Product identity → Decision Hero → Confidence → AI Summary → Strengths → Risks → Topics → Price → Sources → Alternatives → Questions.

Karar durumları:
- ALINIR
- DÜŞÜNÜLEBİLİR
- ALTERNATİFLERE BAK
- YETERSİZ VERİ

AI synthesis ve source evidence görsel olarak ayrılmalıdır.

## Screens

P0:
- Splash
- Onboarding
- Home
- Explore
- Category
- Search
- Search Results
- Filters / Sort
- Product Detail
- Image Viewer
- AI Summary
- AI Q&A
- Topics
- Sources
- Reviews
- Price
- Price Alert
- Deals
- Compare
- Product Finder
- Upgrade Advisor
- Community Pulse
- Watchlist
- Notifications
- Login
- Profile
- Settings

## Screen state contract

Her ilgili ekranda:
Initial, Loading, Loaded, Empty, Partial, Error, Offline, Refreshing, Pending, Success, Failure.

## UI rules

- Minimum touch target: 44×44pt
- Primary CTA: 48–52px
- Bottom sheets for filters/actions
- Full-screen search
- Progressive disclosure
- Sticky primary action where useful
- Essential actions must not be gesture-only
- Respect Dynamic Type and reduced motion

## Design tokens

Background #F8FAFC
Surface #FFFFFF
Border #E2E8F0
Primary text #0F172A
Secondary #475569
Brand #4F46E5
Brand dark #3730A3
Positive #16A34A
Warning #D97706
Negative #DC2626
Info #0284C7

Spacing: 4 / 8 / 12 / 16 / 20 / 24 / 32 / 40 / 48 / 64.

Radius: card 20, large 24, button 14, input 16, chip 999.

## Components

AppHeader, BottomTabBar, SearchField, ProductCard, ProductHero, DecisionHero, ScoreBadge, VerdictBadge, ConfidenceBadge, TopicScore, EvidenceCard, SourceCard, ReviewCard, PriceCard, DealCard, AlternativeCard, ComparisonTable, FilterSheet, SortSheet, ActionSheet, AIAnswer, EmptyState, ErrorState, OfflineBanner, Skeleton, Toast, BottomSheet.

## Trust

Never invent prices, reviews, sources, confidence, stock or AI quotes. Show source count, evidence type, freshness and confidence for important conclusions.

## Mobile quality gate

Every screen must support appropriate:
- accessibility
- loading
- empty
- error
- offline
- analytics
- real API data
- dark mode
- small/large screen layouts

No mock production path.
