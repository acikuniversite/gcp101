# Ders 7: Google BigQuery (Google BigQuery)

Bu derste, Google BigQuery'i (GBQ) detaylı olarak inceleyeceğiz. GBQ, büyük veri analizi için tam yönetimli, sunucusuz bir veri ambarıdır ve büyük veri kümelerini hızla analiz etmenizi sağlar.

## İçindekiler

1. Google BigQuery'e Giriş
2. BigQuery Kurulumu ve Yapılandırma
3. Veri Seti ve Tablo Oluşturma
4. Veri Yükleme ve İçe Aktarma
5. BigQuery SQL Sorguları
6. BigQuery ile Veri Analizi ve Görselleştirme
7. BigQuery ile Güvenlik ve Erişim Kontrolü
8. Örnek Kullanım Senaryoları

## 1. Google BigQuery'e Giriş

Google BigQuery (GBQ), büyük veri analizi için tam yönetimli, sunucusuz bir veri ambarıdır. GBQ, büyük veri kümelerini hızlı ve ölçeklenebilir bir şekilde analiz etmenizi sağlar. SQL benzeri sorgular kullanarak verileriniz üzerinde analizler yapabilirsiniz.

## 2. BigQuery Kurulumu ve Yapılandırma

BigQuery ile çalışmaya başlamak için GCP Konsolu'nda BigQuery'yi etkinleştirmeniz gerekmektedir:

1. **GCP Konsoluna Giriş:** [GCP Konsolu](https://console.cloud.google.com/)na giriş yapın.
2. **BigQuery Sekmesine Geçiş:** Sol menüden "BigQuery" seçeneğine tıklayın.
3. **BigQuery API'sini Etkinleştirme:** Eğer etkin değilse, BigQuery API'sini etkinleştirin.

## 3. Veri Seti ve Tablo Oluşturma

### Veri Seti Oluşturma

1. **BigQuery Konsolu:** [BigQuery Konsolu](https://console.cloud.google.com/bigquery)na gidin.
2. **Yeni Veri Seti:** "Create dataset" butonuna tıklayın.
3. **Veri Seti Ayarları:** Veri seti için bir isim girin ve gerekli ayarları yapılandırın.
4. **Oluşturma:** "Create dataset" butonuna tıklayın.

### Tablo Oluşturma

1. **Veri Seti Seçimi:** Oluşturduğunuz veri setini seçin.
2. **Yeni Tablo:** "Create table" butonuna tıklayın.
3. **Tablo Ayarları:** Tablo için bir isim girin ve şema yapılandırmasını (schema) belirtin.
4. **Oluşturma:** "Create table" butonuna tıklayın.

## 4. Veri Yükleme ve İçe Aktarma

BigQuery'ye veri yüklemek için çeşitli yöntemler mevcuttur:

### CSV veya JSON Dosyaları

1. **Tablo Seçimi:** Veriyi yüklemek istediğiniz tabloyu seçin.
2. **Veri Yükleme:** "Upload" sekmesine gidin ve dosyanızı seçin.
3. **Dosya Formatı:** Dosya formatını (örneğin, CSV veya JSON) belirtin.
4. **Yükleme:** "Upload" butonuna tıklayın.

### Google Cloud Storage

1. **Tablo Seçimi:** Veriyi yüklemek istediğiniz tabloyu seçin.
2. **Veri Kaynağı:** "Source" sekmesine gidin ve "Google Cloud Storage" seçeneğini seçin.
3. **GCS Yolu:** Veri dosyanızın GCS yolunu belirtin.
4. **Yükleme:** "Upload" butonuna tıklayın.

## 5. BigQuery SQL Sorguları

BigQuery, SQL benzeri bir sorgu dili kullanır. Temel sorgularla başlayalım:

### Basit Sorgu

```sql
SELECT name, age FROM my_dataset.my_table WHERE age > 30;
```

### Gruplama ve Agrega Fonksiyonları
```sql
SELECT gender, COUNT(*) as count FROM my_dataset.my_table GROUP BY gender;
```
### JOIN İşlemleri
```sql
SELECT a.name, b.salary FROM my_dataset.employees a JOIN my_dataset.salaries b ON a.id = b.employee_id;
```

## 6. BigQuery ile Veri Analizi ve Görselleştirme
BigQuery ile analiz sonuçlarını görselleştirmek için çeşitli araçlar kullanabilirsiniz:

### Google Data Studio

**Data Studio'ya Bağlanma:** Google Data Studioya gidin ve BigQuery veri kaynağınızı bağlayın.
**Rapor Oluşturma:** BigQuery'den veri çekerek grafikler ve raporlar oluşturun.

### Jupyter Notebook
1. BigQuery Paketi Kurulumu: Jupyter Notebook üzerinde BigQuery paketini kurun
```sh
pip install google-cloud-bigquery
```
2. Veri Çekme ve Analiz: BigQuery'den veri çekip analiz yapın.
```python
from google.cloud import bigquery

client = bigquery.Client()

query = """
SELECT name, age
FROM `my_dataset.my_table`
WHERE age > 30
"""

results = client.query(query)
for row in results:
    print(row)
```

## 7. BigQuery ile Güvenlik ve Erişim Kontrolü
### IAM Rolleri ve İzinler
IAM kullanarak BigQuery erişimini kontrol edebilirsiniz. Kullanıcılara ve hizmet hesaplarına gerekli izinleri atayabilirsiniz.

### Veri Maskeleme ve Şifreleme
BigQuery, verilerinizi otomatik olarak şifreler ve veri maskeleme gibi ek güvenlik özellikleri sunar.

## 8. Örnek Kullanım Senaryoları
Google BigQuery çeşitli kullanım senaryoları için uygundur:

**Büyük Veri Analizi:** Petabayt ölçeğindeki verileri hızlı bir şekilde analiz etmek.
**İş Zekası:** İş zekası araçları ile entegre ederek veri analitiği yapmak.
**Gerçek Zamanlı Analiz:** Gerçek zamanlı veri akışlarını analiz etmek.
**Veri Ambarı:** Verilerinizi güvenli bir şekilde saklamak ve analiz etmek.

Bu derste, Google BigQuery'i detaylı olarak inceledik ve temel işlemleri öğrendik. Bir sonraki derste, Google Cloud Pub/Sub'ı inceleyeceğiz.
