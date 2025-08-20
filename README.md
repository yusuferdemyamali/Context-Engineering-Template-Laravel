# Laravel Context Engineering Template

Bu proje, yeni Laravel projelerine başlarken "Context Engineering" (Bağlam Mühendisliği) prensiplerini kullanarak proje planlama, görev oluşturma ve dağıtım süreçlerini otomatikleştirmek için tasarlanmış bir başlangıç şablonudur. Projenin temel amacı, proje gereksinimlerini, teknik özellikleri ve kuralları yapılandırılmış metin dosyaları (`context/` klasörü) olarak tanımlayarak, bu bağlamdan otomatik olarak görev listeleri, raporlar ve dağıtım planları (`output/` klasörü) üretmektir.

## ✨ Temel Felsefe

Bu şablon, geliştirme sürecinin başlangıcındaki belirsizlikleri azaltmayı hedefler. Geliştirme ekibi, kod yazmaya başlamadan önce aşağıdaki adımları izleyerek projenin tüm yönlerini netleştirir:

1.  **Bağlamı Tanımla (`context/`):** Proje hedefleri, müşteri gereksinimleri, teknik şartnameler ve geliştirme kuralları gibi tüm bilgiler Markdown dosyalarına işlenir.
2.  **Komutları Çalıştır (`commands/`):** Tanımlanmış komutlar, `context` dosyalarını ve `prompts` içindeki şablonları kullanarak anlamlı çıktılar üretir.
3.  **Çıktıyı Kullan (`output/`):** Oluşturulan görev listeleri, planlar ve raporlar, proje yönetimi ve geliştirme süreçleri için doğrudan kullanılabilir hale gelir.

## 📂 Dizin Yapısı

Projenin ana mantığını oluşturan klasörler şunlardır:

```
.
├── commands/               # Otomasyon komutlarını içeren dosyalar
│   ├── breakdown_task_step_by_step.txt
│   ├── code_quality_audit.txt
│   ├── generate_tasks.txt
│   ├── performance_security_report.txt
│   └── refine_and_deploy.txt
├── context/                # Proje bağlamını tanımlayan dokümanlar
│   ├── client_requirements.md
│   ├── database_schema.md
│   ├── design_mockups_description.md
│   ├── development_rules.md
│   ├── performance_goals.md
│   ├── project_brief.md
│   ├── security_best_practices_laravel.md
│   └── technical_specifications.md
├── output/                 # Komutlar tarafından üretilen dosyaların kaydedildiği yer
└── prompts/                # Çıktı formatlarını belirleyen şablonlar
    ├── breakdown_task_step_by_step.tpl
    ├── generate_tasklist.tpl
    ├── performance_security_report.tpl
    └── refine_and_deploy.tpl
```

## 🚀 Nasıl Kullanılır?

Bu şablonu kullanarak yeni bir projeye başlamak için aşağıdaki adımları izleyin:

### Adım 1: Proje Bağlamını Doldurun

[`context/`](context/) klasöründeki tüm `.md` dosyalarını projenizin gereksinimlerine göre düzenleyin. Bu, projenizin "tek doğruluk kaynağı" (single source of truth) olacaktır.

-   **[`project_brief.md`](context/project_brief.md):** Projenin genel hedeflerini ve özetini tanımlayın.
-   **[`client_requirements.md`](context/client_requirements.md):** Müşterinin fonksiyonel ve fonksiyonel olmayan tüm isteklerini listeleyin.
-   **[`technical_specifications.md`](context/technical_specifications.md):** Kullanılacak teknoloji yığınını, mimariyi ve standartları belirtin.
-   **[`development_rules.md`](context/development_rules.md):** Kodlama standartları, Git akışı ve test kurallarını belirleyin.
-   Diğer dosyaları (`database_schema.md`, `performance_goals.md` vb.) projenize uygun şekilde doldurun.

### Adım 2: Komutları Çalıştırın

[`commands/`](commands/) klasöründeki komutlar, `context` ve `prompts` klasörlerini kullanarak çeşitli çıktılar üretir. Bu komutları manuel olarak veya bir otomasyon betiği aracılığıyla çalıştırabilirsiniz.

-   **`generate_tasks.txt`:** Proje belgelerinden yola çıkarak ayrıntılı bir görev listesi oluşturur.
-   **`refine_and_deploy.txt`:** Mevcut planı analiz eder ve dağıtım (deployment) için optimize edilmiş talimatlar üretir.
-   **`performance_security_report.txt`:** Kod parçacıklarını veya dosyaları güvenlik ve performans açısından analiz eder.
-   **`breakdown_task_step_by_step.txt`:** Tek bir büyük görevi daha küçük, yönetilebilir alt adımlara böler.

### Adım 3: Çıktıları İnceleyin ve Kullanın

`output/` klasöründe oluşturulan dosyaları proje planlama, görev atama ve geliştirme süreçlerinde kullanın. Örneğin, `generated_tasks.md` dosyasını proje yönetim aracınıza (Jira, Trello, vb.) aktarabilirsiniz.

## 🛠️ Komutlar ve Amaçları

-   **[`generate_tasks`](commands/generate_tasks.txt):** Proje gereksinimlerinden yola çıkarak geliştirme ekibi için bir yapılacaklar listesi (to-do list) oluşturur.
-   **[`breakdown_task_step_by_step`](commands/breakdown_task_step_by_step.txt):** Karmaşık bir görevi (örneğin, "Kimlik doğrulama sistemi kur") adım adım uygulanabilir alt görevlere ayırır.
-   **[`performance_security_report`](commands/performance_security_report.txt):** Mevcut kodu, projenin güvenlik ve performans hedeflerine göre denetleyerek bir rapor oluşturur.
-   **[`code_quality_audit`](commands/code_quality_audit.txt):** Kodun kalite standartlarına (PSR, SOLID vb.) uygunluğunu denetler ve iyileştirme önerileri sunar.
-   **[`refine_and_deploy`](commands/refine_and_deploy.txt):** Proje planını son haline getirir ve canlı ortama dağıtım için adım adım bir kılavuz hazırlar.

## 🤝 Katkıda Bulunma

Bu şablonu geliştirmek için katkıda bulunabilirsiniz. Lütfen bir "issue" açın veya "pull request" gönderin.

1.  Projeyi Fork'layın.
2.  Yeni bir özellik dalı oluşturun (`git checkout -b feature/yeni-ozellik`).
3.  Değişikliklerinizi commit'leyin (`git commit -m 'feat: Yeni bir özellik eklendi'`).
4.  Dalınızı push'layın (`git push origin feature/yeni-ozellik`).
5.  Bir Pull Request açın.

## 📄 Lisans

Bu proje MIT Lisansı ile lisanslanmıştır. Detaylar için `LICENSE` dosyasına
