# 🌿 Eco Start-up Club - İdarəetmə və İnnovasiya Platforması

ADNSU nəzdində Sənaye və Texnologiya Kollecinin **Eco Start-up Club** tələbə platformasının rəsmi veb-sayt və idarəetmə sistemidir. Bu sistem klubun daxili kommunikasiyasını rəqəmsallaşdırmaq, departamentlər arası iş bölgüsünü tənzimləmək və ekoloji start-up layihələrini idarə etmək üçün hazırlanmışdır.

---

## 🔐 1. Login və Avtorizasiya Sistemi (Ətraflı İzah)

Sistemdə istifadəçilərin qeydiyyatı və təhlükəsizliyi **Firebase Authentication** ilə idarə olunur. Hər bir istifadəçinin daxil olduğu hesabın hansı səlahiyyətə (`tier`) və ya departamentə aid olduğu isə daxil edilən **istifadəçi adının (username)** strukturuna əsasən avtomatik olaraq sistem tərəfindən müəyyən edilir.

### 👥 Rol İyerarxiyası və Struktur Qaydaları:

1. **Tier 1 (Ali Rəhbərlik - Sədr / Məsələn: `ibrahim1`):**
   * **Səlahiyyət:** Sistemdəki bütün elanları və arxiv fayllarını yaza, redaktə edə, silə və idarə edə bilir. Bütün kanallara tam giriş hüququ vardır.
2. **Tier 2 (İdarə Heyəti - Kurator, Müavin, Katib / Məsələn: `gunel2`):**
   * **Səlahiyyət:** Ümumi kanallarda və digər şöbələrdə elanlar paylaşa bilir. Öz paylaşımlarını və özündən aşağı rolların (`tier3`, `tier4`) məlumatlarını idarə edə bilir.
3. **Tier 3 (Departament Koordinatorları / Məsələn: `zaxundov3it`, `malik3sl`):**
   * **Səlahiyyət:** İstifadəçi adının sonundakı kod vasitəsilə konkret departatora bağlanır. Bütün kanalları oxuya bilir, lakin yazı yaza/arxivə fayl əlavə edə bilər yalnız **Ümumi kanala** və ya **öz departamentinə**. Yalnız öz yazdığı elanları/faylları silə və ya redaktə edə bilər.
   * **Departament Kodları:**
     * `sl` — Startup və Layihələr Departamenti
     * `ti` — Tədbirlər və İnkişaf Departamenti
     * `it` — IT Departamenti
     * `iet` — İctimai Əlaqələr və Tərəfdaşlıq
     * `d` — Dizayn Departamenti
4. **Tier 4 (Klub Üzvləri / Məsələn: `lfeteliyeva4` və ya digərləri):**
   * **Səlahiyyət:** Standart oxuma hüququ. Saytdakı bütün elanları və arxivləri görə bilir, lakin idarə panelində heç bir məlumat yaza və ya silə bilməz (yazma formaları gizlidir).

---

## 🚀 2. Sistemimizin Digər Əsas Xüsusiyyətləri

* **Çoxdilli Dəstək:** Azərbaycan, İngilis və Rus dillərində interfeys keçidləri.
* **Real-Time İdarə Paneli (Dashboard):** Elanlar lövhəsi, sənəd/arxiv bazası və departament filtrləri.
* **Gecə və Gündüz Rejimi (Dark/Light Theme):** Göz yormayan dinamik tema dəyişdiricisi.

---

## ⚙️ 3. Texniki Arxitektura

* **Frontend:** Təmiz HTML5, CSS3 (daxili stil olaraq inteqrasiya edilib ki, heç vaxt keş/cache və ya dizayn pozulması problemi yaşanmasın) və Vanilla JavaScript.
* **Hostinq:** GitHub Pages üzərindən ödənişsiz və avtomatik deployment.
* **Verilənlər Bazası:** Firebase Auth (giriş üçün) + `localStorage` (elanlar, arxivlər və sürətli sessiya idarəetməsi üçün).

---

## 💎 4. Sistemimizin Üstünlükləri

1. **Tamamilə Responsive:** Smartfon, planşet və kompüterlərdə qüsursuz görünüş.
2. **Sürətli və Yüngül:** Əlavə ağır freymvorklara ehtiyac duyulmadan millisaniyələr ərzində işləyir.
3. **Məxfi və İyerarxik Təhlükəsizlik:** Üzvlər səlahiyyətləri xaricində heç bir məlumatı dəyişə bilməz.

---

## 🔮 5. Gələcəkdə Əlavə Edəcəyimiz Şeylər (Roadmap)

* [ ] **Real-Time Firebase Firestore İnteqrasiyası:** Məlumatların `localStorage` əvəzinə birbaşa bulud verilənlər bazasından oxunması.
* [ ] **Onlayn Üzvlük Müraciət Forması:** Sayt üzərindən kluba qoşulmaq istəyənlər üçün qeydiyyat paneli.
* [ ] **Layihə İzləmə Sistemi (Kanban Taxtası):** Eko-start-up ideyalarının mərhələlərini izləmək üçün daxili modul.
