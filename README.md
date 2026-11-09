# 🌿 Eco Start-up Club - İdarəetmə və İnnovasiya Platforması

ADNSU nəzdində Sənaye və Texnologiya Kollecinin **Eco Start-up Club** tələbə platformasının rəsmi veb-saytı və daxili idarəetmə sistemidir. Bu sistem klubun daxili kommunikasiyasını rəqəmsallaşdırmaq, departamentlər arası iş bölgüsünü tənzimləmək, sənədləşməni mərkəzləşdirmək və ekoloji start-up layihələrini idarə etmək üçün hazırlanmışdır.

---

## 🔐 1. Login və Avtorizasiya Sistemi (Ətraflı İzah)

Sistemdə istifadəçilərin qeydiyyatı və autentifikasiyası xarici auth xidmətlərindən tamamilə azad edilmiş, **Firebase Cloud Firestore** üzərində təcrid olunmuş **`club_secret_users`** kolleksiyası ilə idarə olunur. Hər bir istifadəçi üçün bazada `username`, `password`, `name`, `role` və `department` sahələri saxlanılır.

Giriş zamanı sistem daxil edilən məlumatları həmin təhlükəsiz kolleksiyada sorğulayır (`login.html`) və istifadəçinin roluna (`tier`) uyğun olaraq idarə panelindəki (`dashboard.html`) icazələri avtomatik tənzimləyir.

### 👥 Rol İyerarxiyası, Səlahiyyətlər və Məxfilik Qaydaları:

1. **Tier 1 (Ali Rəhbərlik - Sədr / Məsələn: `ipasayev1`):**
   * **İstifadəçi İdarəsi:** Dashboard-da yalnız Tier 1 üçün görünən **İstifadəçi İdarəsi (Tier 1)** moduluna malikdir. `club_secret_users` kolleksiyasına yeni istifadəçi (ad-soyad, username, şifrə, rol və departament) əlavə edə və ya mövcud istifadəçiləri silə bilər.
   * **Məxfilik İcazəsi:** İdarəetmə panelindəki sistem istifadəçiləri siyahısında həm **Ad-Soyadı**, həm də **`username`**-i görə bilir.
   * **Paylaşım Səlahiyyəti:** Bütün elanları və arxiv fayllarını yaza, redaktə edə, silə və idarə edə bilir. Bütün kanallara tam giriş hüququ vardır.

2. **Tier 2 (İdarə Heyəti / Koordinatorlar):**
   * **Səlahiyyət:** Ümumi kanallarda və şöbələrdə elanlar/arxivlər paylaşa bilir. Öz paylaşımlarını və özündən aşağı rolların (`tier3`, `tier4`) məlumatlarını idarə edə bilir.

3. **Tier 3 (Departament Koordinatorları - Məsələn: IT, Startup və s.):**
   * **Səlahiyyət:** Bütün kanalları oxuya bilir, lakin elan paylaşa və ya arxivə fayl əlavə edə bilər yalnız **Ümumi kanala** və ya **öz departamentinə**. Yalnız öz yazdığı elanları/faylları silə və ya redaktə edə bilər.
   * **Departament Kodları:**
     * `sl` — Startup və Layihələr Departamenti
     * `ti` — Tədbirlər və İnkişaf Departamenti
     * `it` — IT Departamenti
     * `iet` — İctimai Əlaqələr və Tərəfdaşlıq
     * `d` — Dizayn Departamenti

4. **Tier 4 (Klub Üzvləri):**
   * **Səlahiyyət & Məxfilik:** Standart oxuma hüququ. Saytdakı bütün elanları və arxivləri görə bilir. Elanlarda və arxivlərdə müəlliflərin **yalnız Ad və Soyadı** (məs: *İbrahim Alpaşayev*) görünür, `username`-lər məxfilik üçün gizlədilir. Yazma və idarəetmə panelləri bu istifadəçilər üçün gizlidir.

---

## 🚀 2. Saytın Əsas Modulları və Xüsusiyyətləri

* **Canlı Firestore İnteqrasiyası:** Elanlar (`announcements`), arxiv faylları (`archives`) və istifadəçi qeydləri birbaşa bulud verilənlər bazasından canlı oxunur.
* **Departament Filtrləri:** Elanlar və arxivlər bölməsində həm ümumi kanal, həm də şöbələr üzrə filtr seçimləri.
* **Gecə və Gündüz Rejimi (Dark/Light Theme):** Üst paneldə yerləşən ikon vasitəsilə dinamik tema dəyişdiricisi.
* **Təhlükəsiz Sessiya İdarəetməsi (`localStorage`):** İstifadəçi daxil olduqdan sonra sessiya məlumatları brauzerdə qorunur və çıxış (`logout`) edildikdə təmizlənir.

---

## ⚙️ 3. Texniki Arxitektura

* **Frontend:** Təmiz HTML5, CSS3 (Flexbox/Grid, Custom CSS Variables) və Vanilla JavaScript (ES6 Modules).
* **Verilənlər Bazası:** Firebase Cloud Firestore (`club_secret_users`, `announcements`, `archives`).
* **Hostinq:** GitHub Pages vasitəsilə avtomatlaşdırılmış yayım.

---

## 💎 4. Sistemimizin Üstünlükləri

1. **Tamamilə Responsive:** Smartfon, planşet və kompüterlərdə qüsursuz və səliqəli interfeys.
2. **Sürətli və Yüngül:** Əlavə ağır freymvorklara ehtiyac duyulmadan millisaniyələr ərzində işləyir.
3. **Məxfilik və Təhlükəsizlik:** İstifadəçi məlumatları `club_secret_users` daxilində izolyasiya edilib, üzvlər üçün isə yalnız Ad-Soyad məlumatları nümayiş olunur.

---

## 🔮 5. Gələcək Planlar (Roadmap)

* [x] **Real-Time Firebase Firestore İnteqrasiyası:** Məlumatların `localStorage` əvəzinə birbaşa bulud verilənlər bazasından oxunması. *(Tamamlandı)*
* [x] **Xüsusi Təhlükəsiz Giriş Paneli:** `club_secret_users` kolleksiyası əsasında rol əsaslı yoxlama sistemi. *(Tamamlandı)*
* [ ] **Onlayn Üzvlük Müraciət Forması:** Sayt üzərindən kluba qoşulmaq istəyənlər üçün qeydiyyat paneli.
* [ ] **Layihə İzləmə Sistemi (Kanban Taxtası):** Eko-start-up ideyalarının mərhələlərini izləmək üçün daxili modul.
