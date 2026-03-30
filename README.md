# ÖRNEK PROJE: E-TİCARET SİPARİŞ YÖNETİM SİSTEMİ YENİLEME
## Baştan Sona Proje Dokümantasyonu — Sunum Örneği

---

## PROBLEM STATEMENT

"Operasyon ekibi, mevcut sipariş yönetim sistemindeki ERP-WMS entegrasyon eksikliği
nedeniyle sipariş durumunu manuel olarak 3 farklı sistemde takip etmekte;
bu durum ortalama 45 dakikalık sipariş işleme süresi ve %34 SLA ihlali yaratmaktadır."

---

## İŞ HEDEFLERİ (SMART)

| # | Hedef | Ölçüm |
|---|-------|-------|
| 1 | Sipariş işleme süresini 45 dakikadan 8 dakikaya indirmek | Ortalama işleme süresi |
| 2 | SLA ihlal oranını %34'ten %5'in altına çekmek | Aylık SLA raporu |
| 3 | Operasyon ekibi verimlilik artışı (%25) | Ekip başına günlük işlem adedi |
| ← Hedef Tarih: Q4 2026 | | |

---

## KAPSAM (IN / OUT OF SCOPE)

### In Scope ✅
- ERP-WMS entegrasyon modülü
- Sipariş durum izleme dashboard'u
- Otomatik eskalasyon mekanizması
- Raporlama ve KPI ekranı
- Kullanıcı yetkilendirme modülü

### Out of Scope ❌
- Ödeme gateway değişikliği
- Müşteri mobil uygulaması
- Muhasebe/faturalama sistemi
- Tedarikçi portalı

---

## WBS — İŞ KIRINM YAPISI

```
1.0 E-Ticaret Sipariş Yönetim Sistemi Yenileme
│
├── 1.1 Proje Yönetimi (PMO)
│     ├── 1.1.1 Proje Şartnamesi (Project Charter)
│     ├── 1.1.2 Paydaş Yönetim Planı
│     ├── 1.1.3 İletişim Planı
│     ├── 1.1.4 Risk Yönetim Planı
│     └── 1.1.5 Haftalık Durum Raporları
│
├── 1.2 Gereksinim & İş Analizi
│     ├── 1.2.1 Paydaş Mülakatları (8 mülakat)
│     ├── 1.2.2 As-Is Süreç Haritalama
│     ├── 1.2.3 Gap Analizi
│     ├── 1.2.4 To-Be Süreç Tasarımı
│     ├── 1.2.5 BRD Yazımı ve Onayı
│     ├── 1.2.6 FRD / User Story Yazımı
│     └── 1.2.7 RTM Oluşturulması
│
├── 1.3 Mimari & Teknik Tasarım
│     ├── 1.3.1 Sistem Mimarisi Tasarımı
│     ├── 1.3.2 Veritabanı Şeması
│     ├── 1.3.3 API Kontratları (OpenAPI spec)
│     ├── 1.3.4 Güvenlik Tasarımı
│     └── 1.3.5 Teknik Design Review
│
├── 1.4 UI/UX Tasarımı
│     ├── 1.4.1 Wireframe (Lo-fi)
│     ├── 1.4.2 Prototip (Hi-fi, Figma)
│     └── 1.4.3 Kullanıcı Test Oturumları
│
├── 1.5 Geliştirme — Sprint 1-5
│     ├── 1.5.1 Backend API Geliştirme
│     │     ├── 1.5.1.1 Auth & Yetkilendirme Servisi
│     │     ├── 1.5.1.2 Sipariş Servisi
│     │     ├── 1.5.1.3 ERP Entegrasyon Servisi
│     │     ├── 1.5.1.4 WMS Entegrasyon Servisi
│     │     └── 1.5.1.5 Bildirim Servisi
│     ├── 1.5.2 Frontend Geliştirme
│     │     ├── 1.5.2.1 Dashboard Modülü
│     │     ├── 1.5.2.2 Sipariş İzleme Ekranı
│     │     ├── 1.5.2.3 Raporlama Ekranı
│     │     └── 1.5.2.4 Yönetim Paneli
│     └── 1.5.3 Veritabanı
│           ├── 1.5.3.1 Şema Oluşturma
│           ├── 1.5.3.2 Migration Script
│           └── 1.5.3.3 Performans İndeksleme
│
├── 1.6 Test
│     ├── 1.6.1 Test Planı
│     ├── 1.6.2 Unit Test Suite
│     ├── 1.6.3 Integration Test
│     ├── 1.6.4 System Test
│     ├── 1.6.5 Performans Testi
│     └── 1.6.6 Güvenlik Testi (Pentest)
│
├── 1.7 UAT
│     ├── 1.7.1 UAT Planı ve Test Senaryoları
│     ├── 1.7.2 UAT Oturumları (Operasyon Ekibi)
│     ├── 1.7.3 Bulgu Takibi ve Çözümü
│     └── 1.7.4 UAT Onay Belgesi
│
├── 1.8 Deployment & Go-Live
│     ├── 1.8.1 Deployment Planı
│     ├── 1.8.2 Veri Migrasyon Planı ve Testi
│     ├── 1.8.3 Kullanıcı Eğitimleri
│     ├── 1.8.4 Yardım Dokümanları (Run Book)
│     ├── 1.8.5 Staging Deployment
│     ├── 1.8.6 Production Deployment
│     └── 1.8.7 Hypercare (2 hafta aktif destek)
│
└── 1.9 Proje Kapanışı
      ├── 1.9.1 Lessons Learned
      ├── 1.9.2 Proje Kapanış Raporu
      └── 1.9.3 Arşivleme
```

---

## PERT SÜRE TAHMİNLERİ (Kritik İş Paketleri)

| İş Paketi | O (gün) | M (gün) | P (gün) | E (gün) | σ |
|-----------|---------|---------|---------|---------|---|
| BRD Yazımı | 5 | 8 | 14 | **8.2** | 1.5 |
| Mimari Tasarım | 3 | 6 | 10 | **6.2** | 1.2 |
| Auth Servisi | 2 | 4 | 7 | **4.2** | 0.8 |
| ERP Entegrasyon | 8 | 15 | 30 | **15.7** | 3.7 |
| WMS Entegrasyon | 5 | 10 | 20 | **10.8** | 2.5 |
| Dashboard Frontend | 5 | 8 | 12 | **8.2** | 1.2 |
| Integration Test | 3 | 7 | 14 | **7.5** | 1.8 |
| UAT | 5 | 10 | 18 | **10.5** | 2.2 |

**ERP Entegrasyon en riskli görev** → σ=3.7 → Yakından izle, buffer ekle

---

## KRİTİK YOL ANALİZİ

```
[BRD 8.2g] → [Mimari 6.2g] → [ERP Entegrasyon 15.7g] → [Integration Test 7.5g] → [UAT 10.5g]
                                                                                            TOPLAM: ~48 gün

[BRD 8.2g] → [Mimari 6.2g] → [Auth Servisi 4.2g] → [Frontend 8.2g] → [UAT 10.5g]
                                                                              TOPLAM: ~37 gün

KRİTİK YOL: BRD → Mimari → ERP Entegrasyon → Integration Test → UAT = ~48 iş günü
```

**ERP Entegrasyon servisindeki her 1 günlük gecikme projeyi 1 gün geciktirir.**

---

## RACI MATRİSİ

| Görev | İş Analisti | PM | Lead Dev | Backend Dev | Frontend Dev | QA | Müşteri/PO |
|-------|------------|----|---------|-----------|-----------|----|-----------|
| BRD Yazımı | **A/R** | C | C | I | I | I | C |
| Süreç Haritalama | **A/R** | I | C | I | I | I | C |
| Mimari Tasarım | C | I | **A/R** | C | C | I | I |
| Sprint Planlaması | C | **A/R** | R | C | C | C | C |
| ERP Geliştirme | C | I | **A** | **R** | I | C | I |
| WMS Geliştirme | C | I | **A** | **R** | I | C | I |
| Test Planı | C | I | C | I | I | **A/R** | C |
| UAT Yürütme | C | I | I | I | I | C | **A/R** |
| Go/No-Go Kararı | C | R | C | I | I | C | **A** |

---

## SPRINT PLANI (5 Sprint × 2 Hafta)

### Sprint 0 (2 hafta) — Hazırlık
- [ ] BRD onaylandı
- [ ] Teknik mimari kararlaştırıldı
- [ ] Development ortamları hazır
- [ ] Backlog hazırlandı ve groomed
- [ ] Definition of Done tanımlandı

### Sprint 1 — Temel Altyapı
```
Story                               | SP | Sahip
────────────────────────────────────|────|──────
Auth & Yetkilendirme servisi        | 8  | Dev A
Veritabanı şeması v1                | 5  | Dev B
CI/CD pipeline kurulumu             | 5  | DevOps
Temel API gateway konfigürasyonu    | 3  | Dev A
────────────────────────────────────|────|──────
TOPLAM                              | 21 SP
```

### Sprint 2 — Çekirdek İş Mantığı
```
Story                               | SP | Sahip
────────────────────────────────────|────|──────
Sipariş servisi CRUD               | 13 | Dev A
ERP bağlantı katmanı               | 8  | Dev B
Sipariş izleme API'leri            | 5  | Dev A
────────────────────────────────────|────|──────
TOPLAM                              | 26 SP
```

### Sprint 3 — Entegrasyon
```
Story                               | SP | Sahip
────────────────────────────────────|────|──────
WMS entegrasyon servisi            | 13 | Dev B
ERP senkronizasyon mekanizması     | 8  | Dev A
Bildirim servisi                   | 5  | Dev A
Entegrasyon test hazırlığı         | 3  | QA
────────────────────────────────────|────|──────
TOPLAM                              | 29 SP
```

### Sprint 4 — Frontend & Dashboard
```
Story                               | SP | Sahip
────────────────────────────────────|────|──────
Dashboard ana ekran                | 8  | Frontend Dev
Sipariş takip ekranı               | 8  | Frontend Dev
Raporlama ekranı                   | 5  | Frontend Dev
Admin yönetim paneli               | 5  | Frontend Dev
────────────────────────────────────|────|──────
TOPLAM                              | 26 SP
```

### Sprint 5 — Test, UAT, Deployment
```
Story                               | SP | Sahip
────────────────────────────────────|────|──────
Integration test tamamlama         | 8  | QA
Performans test                    | 5  | QA/DevOps
UAT hazırlık ve yürütme            | 8  | QA + PO
Bug fix buffer                     | 5  | Tüm ekip
Deployment & Hypercare             | 5  | DevOps
────────────────────────────────────|────|──────
TOPLAM                              | 31 SP
```

**Toplam Backlog:** ~133 SP | **Ortalama Velocity:** ~27 SP/sprint | **Toplam Süre:** ~10 hafta + Sprint 0 (2 hafta) = **12 Hafta**

---

## KRİTİK RİSKLER

| Risk | Olasılık | Etki | Skor | Önlem |
|------|----------|------|------|-------|
| ERP API dökümantasyonu eksik/yanlış | Yüksek | Yüksek | 🔴 Kritik | Erken spike, ERP vendor ile workshop |
| Paydaş onay süreçleri gecikebilir | Orta | Yüksek | 🟠 Yüksek | SLA tabanlı onay mekanizması |
| Personel değişikliği (kilit rol) | Düşük | Yüksek | 🟠 Yüksek | Bilgi aktarımı (knowledge transfer) süreçleri |
| Veri migrasyon hataları | Orta | Yüksek | 🟠 Yüksek | Staging'de tam test, rollback planı |
| Performans hedefleri tutturulamazsa | Düşük | Orta | 🟡 Orta | Erken load test, caching stratejisi |

---

*Örnek proje dokümantasyonu — Sunum sırasında referans olarak kullanılacak*
