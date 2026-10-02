# AI Coding Agent Rules

## Mission

NeDiyor'u production-grade, evidence-backed bir product decision platformu olarak geliştir.

Temel akış:

**Question → Evidence → Decision → Action**

## 1. Before coding

Her görevden önce şu sırayla oku:

1. `docs/README.md`
2. Görevle ilgili `docs/*.md`
3. `design.md`
4. İlgili mevcut page/route
5. İlgili componentler
6. API ve type tanımları
7. Gerçek veri akışı

Mevcut kodu incelemeden yeni mimari kurma.

## 2. Source of truth

Öncelik sırası:

1. Security/privacy requirements
2. Real data correctness
3. Existing API contract
4. Product requirements
5. Design system
6. Implementation convenience

Docs ile kod çelişirse sessizce varsayım yapma. Çelişkiyi düzelt ve ilgili dokümanı güncelle.

## 3. Never invent data

Kesinlikle uydurma:

- ürün
- fiyat
- stok
- yorum
- kaynak
- review count
- score
- confidence
- AI quote
- kullanıcı
- API response

Production ekranlarında mock data kullanma.

Mock data yalnızca açıkça development/test amacıyla kullanılabilir ve production path'e sızmamalıdır.

## 4. Never invent APIs

Yeni endpoint gerekiyorsa:

1. mevcut API'yi kontrol et
2. mevcut endpoint'in genişletilip genişletilemeyeceğini değerlendir
3. gerekli request/response contract'ı tanımla
4. server-side validation ekle
5. client'i gerçek endpoint'e bağla
6. test yaz
7. ilgili docs'u güncelle

Client tarafında sahte API response üretip görevi tamamlanmış kabul etme.

## 5. Existing functionality

Mevcut çalışan özellikleri gereksiz yere silme veya yeniden yazma.

Bir component zaten varsa yeni kopyasını oluşturma.

Önce mevcut componenti genişletmeyi dene.

Breaking change gerekiyorsa:
- sebebi belirt
- etkilenen ekranları belirle
- migration uygula
- eski davranışın artık neden kullanılamadığını dokümante et

## 6. UI/UX

Her ekran `design.md` ve ilgili `docs/03-ui-ux.md` kurallarına uymalıdır.

Her ekranın en azından uygun olduğu durumlarda:

- initial
- loading
- loaded
- empty
- partial data
- error
- offline
- refreshing
- action pending
- action success
- action failure

durumları bulunmalıdır.

Her button gerçek bir action'a bağlanmalıdır.

İşlevi hazır olmayan button'u çalışıyormuş gibi gösterme.

## 7. Mobile

Mobile uygulama web sitesinin küçültülmüş kopyası değildir.

Desktop patternlerini doğrudan mobile taşıma:

- desktop sidebar kullanma
- dense desktop table kullanma
- küçük dokunma alanları kullanma
- desktop navbar'ı küçültüp mobile koyma

Mobile için:

- bottom navigation
- bottom sheet
- sticky CTA
- horizontal rail
- full-screen search
- progressive disclosure

kullan.

Minimum touch target: **44×44 pt**.

## 8. Accessibility

Her interactive component:

- accessible label
- role
- state
- gerekli durumda hint

sağlamalıdır.

Destekle:

- VoiceOver
- TalkBack
- Dynamic Type
- large text
- reduced motion
- sufficient contrast

Renk tek başına anlam taşımaz.

Chart ve score bileşenlerinin screen-reader text karşılığı olmalıdır.

## 9. AI rules

AI, NeDiyor'da source of truth değildir.

AI yalnızca mevcut evidence üzerinden synthesis yapar.

AI şu bilgileri uyduramaz:

- review
- quote
- source
- price
- specification
- user opinion
- statistics
- confidence

AI sonucu mümkün olduğunda:

- conclusion
- evidence references
- confidence
- generatedAt
- model version
- prompt version

ile ilişkilendirilmelidir.

AI synthesis ile original source/user opinion görsel olarak ayrılmalıdır.

## 10. Evidence

Önemli her iddia mümkün olduğunca kaynağına kadar izlenebilir olmalıdır.

Kaynak yoksa kesin gerçek gibi sunma.

Belirsizliği açıkça belirt.

Negatif evidence yalnızca conversion yükseltmek amacıyla gizlenemez.

## 11. Scoring

Score hesaplama UI'da yapılmaz.

Authoritative scoring server-side olmalıdır.

Client yalnızca API'den gelen sonucu gösterir.

Score algoritması değişirse version bilgisi korunmalıdır.

Historical score'lar sonradan sessizce değiştirilmemelidir.

## 12. Search

Search ranking client'ta keyfi şekilde değiştirilmez.

Search:

- exact match
- product identity
- brand
- category
- relevance
- evidence
- freshness
- filters

sinyallerini server-side kullanmalıdır.

Natural-language shopping query mümkün olduğunda structured criteria'ya dönüştürülmelidir.

## 13. Product identity

Ürün eşleştirmede mümkün olduğunda:

- GTIN/EAN/UPC
- manufacturer model number
- brand
- normalized name
- variant attributes

kullan.

Sadece benzer isim nedeniyle iki ürün/variant'ı birleştirme.

## 14. Price

Her fiyatın:

- currency
- merchant
- timestamp
- availability

bağlamı olmalıdır.

Stale fiyatı canlı fiyat gibi gösterme.

Fake countdown, fake scarcity veya fake stock kullanma.

## 15. Security

Asla:

- secret commit etme
- API key client bundle'a koyma
- password loglama
- session token loglama
- authorization'ı client'a bırakma

Protected mutation'larda server-side ownership check zorunludur.

User yalnızca kendi:

- watchlist
- price alerts
- reviews
- preferences

verisini değiştirebilmelidir.

Input'ları server-side validate et.

## 16. Privacy

Gereksiz kişisel veri toplama.

AI provider'a yalnızca gerekli veri gönder.

Analytics consent gerektiren akışları uygun consent modeliyle çalıştır.

Account deletion kullanıcıya açık ve anlaşılır olmalıdır.

## 17. Components

Aynı UI pattern'i ikinci kez yazmadan önce mevcut componentleri ara.

Öncelikli shared componentler:

- AppHeader
- BottomTabBar
- ProductCard
- DecisionHero
- ScoreBadge
- VerdictBadge
- EvidenceCard
- SourceCard
- ReviewCard
- PriceCard
- DealCard
- AlternativeCard
- FilterSheet
- SortSheet
- EmptyState
- ErrorState
- Skeleton
- Toast

One-off component ancak gerçekten farklı UX gerektiğinde oluşturulabilir.

## 18. Design system

Yeni renk, spacing, radius veya typography değeri eklemeden önce mevcut design tokenlarını kontrol et.

İkinci bir design system oluşturma.

Hard-coded random spacing kullanma.

## 19. Performance

Gereksiz dependency ekleme.

Uzun listelerde virtualization kullan.

Ağır componentleri lazy-load et.

Gereksiz re-render oluşturma.

Görselleri optimize et.

API'de N+1 query oluşturma.

Performance regression core flow'u etkiliyorsa release defect olarak kabul edilir.

## 20. Error handling

Error'ları swallow etme.

Her kritik hata:

- kullanıcıya anlaşılır mesaj
- retry
- preserved input/state
- request ID/log context

sağlamalıdır.

Backend stack trace kullanıcıya gösterilmez.

## 21. Loading

Her yerde generic spinner kullanma.

Product, search, compare ve home için içerik yapısına uygun skeleton kullan.

Fake percentage progress kullanma.

AI loading aşamaları gerçek backend durumlarını yansıtmıyorsa sahte ilerleme yüzdesi gösterme.

## 22. Offline

Offline durumda mevcut cache kullanılabilir.

Ancak cached price veya availability güncelmiş gibi gösterilmez.

Mutation offline destekleniyorsa queue/idempotency kuralları tanımlı olmalıdır.

## 23. Analytics

Yeni kullanıcı davranışı oluşturan önemli action'larda analytics event'i düşün.

Event isimleri:

`lowercase_snake_case`

Örnek:

- product_viewed
- decision_viewed
- evidence_viewed
- product_saved
- price_alert_created
- comparison_started
- ai_question_asked

Analytics için kullanıcı gizliliğini ihlal eden gereksiz payload gönderme.

## 24. Testing

Değişiklikten sonra uygun olanları çalıştır:

- typecheck
- lint
- unit tests
- integration tests
- API tests
- relevant E2E
- visual checks

Core journey:

**Search → Product → Decision → Evidence → Price → Action**

kırılmamalıdır.

## 25. Database

Schema değişiklikleri migration ile yapılmalıdır.

Migration:

- deterministik
- review edilebilir
- mümkünse reversible
- production data'yı koruyan

olmalıdır.

Ad-hoc production data mutation yapma.

## 26. Git

Commit mesajları değişikliğin amacını açıklamalıdır.

Örnek:

- `feat: add price alert flow`
- `fix: preserve search filters on back navigation`
- `refactor: extract decision hero`
- `docs: define mobile source explorer`

Unrelated değişiklikleri aynı commit'e doldurma.

## 27. Documentation

Mimari veya davranış değişirse ilgili docs dosyasını güncelle.

Yeni feature için gerekirse:

- product docs
- UI/UX docs
- API docs
- data model docs
- analytics docs
- testing docs

birlikte güncellenmelidir.

## 28. Definition of done

Görev yalnızca kod yazıldığında tamamlanmış sayılmaz.

Tamamlanması için:

- gerçek data bağlı
- UI doğru
- UX states tamam
- navigation çalışıyor
- accessibility kontrol edilmiş
- responsive/mobile kontrol edilmiş
- loading/error/empty kontrol edilmiş
- analytics bağlı
- testler çalışıyor
- runtime error yok
- mock production path'te yok
- docs güncel

olmalıdır.

## 29. If blocked

Bir API veya veri eksikse:

**Mock ile devam edip eksikliği gizleme.**

Şu formatta eksikliği tanımla:

- Missing contract
- Why needed
- Request
- Response
- Data source
- Security consideration
- Implementation plan

Sonra en küçük doğru değişiklikle çöz.

## 30. Final principle

NeDiyor'da amaç daha fazla ekran, daha fazla animasyon veya daha fazla AI üretmek değildir.

Amaç:

**Kullanıcının doğru ürünü, doğru kanıtla, doğru zamanda seçmesine yardımcı olmak.**

Her teknik ve tasarım kararı bu amaca hizmet etmiyorsa yeniden değerlendirilmelidir.
