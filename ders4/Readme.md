# Ders 4: Google Cloud Storage (Google Cloud Storage)

Bu derste, Google Cloud Storage'i (GCS) detaylı olarak inceleyeceğiz. GCS, GCP'nin ölçeklenebilir ve güvenli dosya depolama hizmetidir ve çeşitli uygulamalar için geniş depolama çözümleri sunar.

## İçindekiler

1. Google Cloud Storage'a Giriş
2. Cloud Storage Kavramları
3. Depolama Alanı (Bucket) Oluşturma
4. Dosya Yükleme ve İndirme
5. Cloud Storage Sınıfları
6. Erişim Kontrolü ve Güvenlik
7. Cloud Storage ile Versiyonlama
8. Örnek Kullanım Senaryoları

## 1. Google Cloud Storage'a Giriş

Google Cloud Storage (GCS), Google Cloud Platform'un ölçeklenebilir ve güvenli dosya depolama hizmetidir. GCS, düşük maliyetli depolama çözümleri sunar ve verilerinizi dünya çapında erişilebilir kılar.

## 2. Cloud Storage Kavramları

### Bucket

Bucket, GCS'de verilerinizi depoladığınız konteynerdir. Her dosya bir bucket içinde depolanır ve her bucket, benzersiz bir isimle tanımlanır.

### Object

Object, GCS'de depolanan temel veri birimidir. Her object, bir dosya ve ona ait metadata içerir.

### Metadata

Metadata, bir object hakkında bilgileri içerir. Metadata, object'in kimliğini, türünü, boyutunu ve diğer özelliklerini tanımlar.

## 3. Depolama Alanı (Bucket) Oluşturma

GCS'de bir bucket oluşturmak için aşağıdaki adımları takip edin:

1. **GCP Konsoluna Giriş:** [GCP Konsolu](https://console.cloud.google.com/)na giriş yapın.
2. **Cloud Storage Sekmesine Geçiş:** Sol menüden "Storage" > "Browser" seçeneğine tıklayın.
3. **Bucket Oluşturma:** "Create bucket" butonuna tıklayın.
4. **Bucket Ayarları:**
    - **İsim:** Bucket için benzersiz bir isim girin.
    - **Bölge:** Verilerinizin depolanacağı bölgeyi seçin.
    - **Depolama Sınıfı:** İhtiyacınıza uygun bir depolama sınıfı seçin (örneğin, Standard, Nearline, Coldline, veya Archive).
    - **Erişim Kontrolü:** Erişim kontrolü seviyesini seçin (örneğin, Fine-grained veya Uniform).
5. **Oluşturma:** "Create" butonuna tıklayarak bucket'ı oluşturun.

## 4. Dosya Yükleme ve İndirme

### Dosya Yükleme

1. **GCP Konsolunda Bucket Seçimi:** Yüklemek istediğiniz bucket'ı seçin.
2. **Dosya Yükleme:** "Upload files" butonuna tıklayın ve yüklemek istediğiniz dosyaları seçin.

### Dosya İndirme

1. **GCP Konsolunda Bucket Seçimi:** İndirmek istediğiniz dosyanın bulunduğu bucket'ı seçin.
2. **Dosya İndirme:** İndirmek istediğiniz dosyaya tıklayın ve "Download" butonuna tıklayın.

## 5. Cloud Storage Sınıfları

GCS, farklı kullanım senaryoları için çeşitli depolama sınıfları sunar:

- **Standard:** Sık erişilen veriler için uygundur.
- **Nearline:** Ayda bir veya daha az erişilen veriler için uygundur.
- **Coldline:** Yılda bir veya daha az erişilen veriler için uygundur.
- **Archive:** Uzun süreli arşivleme ve nadiren erişilen veriler için uygundur.

## 6. Erişim Kontrolü ve Güvenlik

### IAM ile Erişim Kontrolü

Identity and Access Management (IAM) ile kullanıcı ve hizmet hesaplarının bucket'lara ve object'lere erişimini yönetebilirsiniz. IAM rolleri ve izinleri kullanarak erişim kontrolü sağlayabilirsiniz.

### ACL ile Erişim Kontrolü

Access Control Lists (ACLs) kullanarak daha detaylı erişim kontrolü sağlayabilirsiniz. ACL'ler ile bireysel kullanıcılar veya gruplar için izinler belirleyebilirsiniz.

### Şifreleme

GCS, verilerinizi otomatik olarak şifreler. Ayrıca, kendi şifreleme anahtarlarınızı kullanarak ek güvenlik sağlayabilirsiniz.

## 7. Cloud Storage ile Versiyonlama

GCS, object'lerinizin farklı versiyonlarını saklamanıza olanak tanır. Versiyonlama, yanlışlıkla silinen veya değiştirilen dosyaları kurtarmak için faydalıdır.

### Versiyonlamayı Etkinleştirme

1. **Bucket Ayarları:** Versiyonlama etkinleştirmek istediğiniz bucket'ı seçin.
2. **Versiyonlama Seçeneği:** "Enable versioning" seçeneğini işaretleyin.
3. **Kaydet:** Ayarları kaydedin.

## 8. Örnek Kullanım Senaryoları

Google Cloud Storage çeşitli kullanım senaryoları için uygundur:

- **Yedekleme ve Arşivleme:** Verilerinizi güvenli ve düşük maliyetli bir şekilde yedekleyin ve arşivleyin.
- **Medya Dosyaları:** Video, ses ve görüntü dosyalarını depolayın ve dünya çapında erişilebilir hale getirin.
- **Veri Analizi:** Büyük veri setlerini depolayın ve analiz için BigQuery veya diğer analiz araçlarıyla entegre edin.
- **Web Uygulamaları:** Statik web içeriğini depolayın ve hızlı bir şekilde sunun.

Bu derste, Google Cloud Storage'i detaylı olarak inceledik ve temel işlemleri öğrendik. Bir sonraki derste, Google App Engine'i inceleyeceğiz.
