# Ders 6: Google Cloud Functions (Google Cloud Functions)

Bu derste, Google Cloud Functions'ı (GCF) detaylı olarak inceleyeceğiz. GCF, olay bazlı sunucusuz bilgi işlem hizmetidir ve küçük, tek amaçlı işlevleri çalıştırmanızı sağlar.

## İçindekiler

1. Google Cloud Functions'a Giriş
2. Cloud Functions Kurulumu ve Yapılandırma
3. İlk Cloud Function Oluşturma
4. Cloud Functions ile Olay Tetikleme
5. Cloud Functions ile Loglama ve Hata Ayıklama
6. Cloud Functions ile Güvenlik ve Erişim Kontrolü
7. Örnek Kullanım Senaryoları

## 1. Google Cloud Functions'a Giriş

Google Cloud Functions (GCF), olay bazlı sunucusuz bilgi işlem hizmetidir. GCF, olaylar tetiklendiğinde küçük işlevler çalıştırmanıza olanak tanır ve sunucu yönetimini ortadan kaldırır. Bu işlevler HTTP istekleri, Cloud Pub/Sub mesajları, Cloud Storage değişiklikleri gibi çeşitli olaylar tarafından tetiklenebilir.

## 2. Cloud Functions Kurulumu ve Yapılandırma

GCF ile çalışmak için gerekli araçları kurmanız gerekmektedir:

1. **GCP Konsoluna Giriş:** [GCP Konsolu](https://console.cloud.google.com/)na giriş yapın.
2. **Cloud Functions API'sini Etkinleştirme:** Sol menüden "APIs & Services" > "Library" seçeneğine gidin ve "Cloud Functions API"yi etkinleştirin.
3. **Google Cloud SDK Kurulumu:** [Google Cloud SDK](https://cloud.google.com/sdk/docs/install)'yi indirip kurun.
4. **Cloud Functions SDK Kurulumu:**
    ```sh
    gcloud components install beta
    ```

## 3. İlk Cloud Function Oluşturma

Basit bir HTTP tabanlı Cloud Function oluşturalım ve dağıtalım:

1. **Proje Dizini Oluşturma:**
    ```sh
    mkdir my-function
    cd my-function
    ```
2. **main.py Dosyasını Oluşturma:**
    ```python
    def hello_world(request):
        return 'Hello, World!'
    ```
3. **requirements.txt Dosyasını Oluşturma:**
    ```
    # Boş bırakabilirsiniz veya gerekli bağımlılıkları ekleyebilirsiniz.
    ```
4. **Cloud Function Dağıtma:**
    ```sh
    gcloud functions deploy hello_world --runtime python37 --trigger-http --allow-unauthenticated
    ```

## 4. Cloud Functions ile Olay Tetikleme

GCF, çeşitli olaylarla tetiklenebilir:

### HTTP Tetikleme

HTTP istekleri ile tetiklenen işlevler:

```sh
gcloud functions deploy hello_http --runtime python37 --trigger-http --allow-unauthenticated
```

## Cloud Pub/Sub Tetikleme
Cloud Pub/Sub mesajları ile tetiklenen işlevler:

1. main.py dosyası

```python
import base64

def hello_pubsub(event, context):
    if 'data' in event:
        name = base64.b64decode(event['data']).decode('utf-8')
    else:
        name = 'World'
    print(f'Hello, {name}!')
```

2. Cloud Function Dağıtma:

```sh
gcloud functions deploy hello_pubsub --runtime python37 --trigger-topic YOUR_TOPIC_NAME
```

## Cloud Storage Tetikleme
Cloud Storage değişiklikleri ile tetiklenen işlevler:

1. main.py dosyası
```python
def hello_gcs(event, context):
    print(f"Processing file: {event['name']}.")
```
2. Cloud Function Dağıtma:
```sh
gcloud functions deploy hello_gcs --runtime python37 --trigger-resource YOUR_BUCKET_NAME --trigger-event google.storage.object.finalize
```

## 5. Cloud Functions ile Loglama ve Hata Ayıklama
GCF, yerleşik loglama ve hata ayıklama özellikleri sunar:

- Log Mesajları Yazma:
```python
import logging

def hello_world(request):
    logging.info('Hello logs!')
    return 'Hello, World!'
```
- Logları Görüntüleme:
```sh
gcloud functions logs read hello_world
```

## 6. Cloud Functions ile Güvenlik ve Erişim Kontrolü
### IAM Rolleri ve İzinler
IAM kullanarak Cloud Functions erişimini kontrol edebilirsiniz. Örneğin, işlevlerinize kimlerin erişebileceğini belirlemek için IAM rolleri atayabilirsiniz.

### HTTP İşlevlerinde Kimlik Doğrulama
HTTP işlevlerine erişimi kısıtlamak için kimlik doğrulama kullanabilirsiniz. İşlevi kimlik doğrulaması gerektirecek şekilde dağıtabilirsiniz:

```sh
gcloud functions deploy hello_world --runtime python37 --trigger-http
```

## 7. Örnek Kullanım Senaryoları
Google Cloud Functions çeşitli kullanım senaryoları için uygundur:

- **HTTP API'leri:** Hızlı ve ölçeklenebilir HTTP tabanlı API'ler oluşturmak.
- **Veri İşleme:** Cloud Storage veya Cloud Pub/Sub olayları ile tetiklenen veri işleme işlevleri oluşturmak.
- **Arka Plan Görevleri:** Zamanlanmış arka plan görevleri ve iş akışları oluşturmak.

Bu derste, Google Cloud Functions'ı detaylı olarak inceledik ve temel işlemleri öğrendik. Bir sonraki derste, Google BigQuery'i inceleyeceğiz.

