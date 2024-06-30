# Ders 8: Google Cloud Pub/Sub (Google Cloud Pub/Sub)

Bu derste, Google Cloud Pub/Sub'ı (GCP Pub/Sub) detaylı olarak inceleyeceğiz. Pub/Sub, olay tabanlı mesajlaşma hizmetidir ve uygulamalarınız arasında güvenilir ve ölçeklenebilir bir şekilde veri iletmenizi sağlar.

## İçindekiler

1. Google Cloud Pub/Sub'a Giriş
2. Pub/Sub Kurulumu ve Yapılandırma
3. Konu (Topic) ve Abonelik (Subscription) Oluşturma
4. Mesaj Yayınlama ve Abone Olma
5. Pub/Sub ile Mesaj İşleme
6. Pub/Sub ile Güvenlik ve Erişim Kontrolü
7. Örnek Kullanım Senaryoları

## 1. Google Cloud Pub/Sub'a Giriş

Google Cloud Pub/Sub, olay tabanlı mesajlaşma hizmetidir. Pub/Sub, yayıncı (publisher) ve abone (subscriber) modellerini kullanarak uygulamalarınız arasında veri iletimi sağlar. Bu model, bileşenler arasında asenkron iletişime olanak tanır ve yüksek performanslı, ölçeklenebilir sistemler oluşturmanıza yardımcı olur.

## 2. Pub/Sub Kurulumu ve Yapılandırma

Google Cloud Pub/Sub ile çalışmaya başlamak için GCP Konsolu'nda Pub/Sub API'sini etkinleştirmeniz gerekmektedir:

1. **GCP Konsoluna Giriş:** [GCP Konsolu](https://console.cloud.google.com/)na giriş yapın.
2. **Pub/Sub API'sini Etkinleştirme:** Sol menüden "APIs & Services" > "Library" seçeneğine gidin ve "Cloud Pub/Sub API"yi etkinleştirin.

## 3. Konu (Topic) ve Abonelik (Subscription) Oluşturma

### Konu Oluşturma

1. **Pub/Sub Konsolu:** [Pub/Sub Konsolu](https://console.cloud.google.com/cloudpubsub)na gidin.
2. **Yeni Konu:** "Create Topic" butonuna tıklayın.
3. **Konu Ayarları:** Konu için bir isim girin ve gerekli ayarları yapılandırın.
4. **Oluşturma:** "Create" butonuna tıklayarak konuyu oluşturun.

### Abonelik Oluşturma

1. **Abonelik Oluşturma:** Oluşturduğunuz konunun yanında "Create Subscription" butonuna tıklayın.
2. **Abonelik Ayarları:** Abonelik için bir isim girin ve gerekli ayarları yapılandırın.
3. **Oluşturma:** "Create" butonuna tıklayarak aboneliği oluşturun.

## 4. Mesaj Yayınlama ve Abone Olma

### Mesaj Yayınlama

Python kullanarak bir mesaja yayınlamak için şu adımları izleyin:

1. **Gerekli Kütüphaneleri Yükleyin:**
    ```sh
    pip install google-cloud-pubsub
    ```

2. **Mesaj Yayınlama Kodu:**
    ```python
    from google.cloud import pubsub_v1

    # Proje ID'si ve Konu Adı
    project_id = "YOUR_PROJECT_ID"
    topic_id = "YOUR_TOPIC_ID"

    publisher = pubsub_v1.PublisherClient()
    topic_path = publisher.topic_path(project_id, topic_id)

    # Mesaj Yayınlama
    message = "Hello, Pub/Sub!"
    future = publisher.publish(topic_path, message.encode("utf-8"))
    print(f"Published message ID: {future.result()}")
    ```

### Mesaj Aboneliği

Python kullanarak mesajlara abone olmak için şu adımları izleyin:

1. **Mesaj Aboneliği Kodu:**
    ```python
    from google.cloud import pubsub_v1

    # Proje ID'si ve Abonelik Adı
    project_id = "YOUR_PROJECT_ID"
    subscription_id = "YOUR_SUBSCRIPTION_ID"

    subscriber = pubsub_v1.SubscriberClient()
    subscription_path = subscriber.subscription_path(project_id, subscription_id)

    def callback(message):
        print(f"Received message: {message.data}")
        message.ack()

    streaming_pull_future = subscriber.subscribe(subscription_path, callback=callback)
    print(f"Listening for messages on {subscription_path}...")

    with subscriber:
        try:
            streaming_pull_future.result()
        except KeyboardInterrupt:
            streaming_pull_future.cancel()
            streaming_pull_future.result()
    ```

## 5. Pub/Sub ile Mesaj İşleme

Pub/Sub ile mesajları işlemek için aşağıdaki adımları takip edebilirsiniz:

1. **Mesaj Yayınlama ve Alma:** Mesajları yayınlamak ve almak için yukarıdaki kod örneklerini kullanın.
2. **Mesaj İşleme:** Mesajları aldığınızda, gerekli işleme mantığını `callback` fonksiyonunda uygulayın.
3. **Mesajların Onaylanması:** Mesajları aldıktan sonra `message.ack()` fonksiyonu ile mesajları onaylayın.

## 6. Pub/Sub ile Güvenlik ve Erişim Kontrolü

### IAM Rolleri ve İzinler

IAM kullanarak Pub/Sub erişimini kontrol edebilirsiniz. Kullanıcılara ve hizmet hesaplarına gerekli izinleri atayabilirsiniz.

### Şifreleme

Pub/Sub, mesajları otomatik olarak şifreler. Ayrıca, kendi şifreleme anahtarlarınızı kullanarak ek güvenlik sağlayabilirsiniz.

## 7. Örnek Kullanım Senaryoları

Google Cloud Pub/Sub çeşitli kullanım senaryoları için uygundur:

- **Gerçek Zamanlı Veri İşleme:** Gerçek zamanlı veri akışlarını işlemek ve analiz etmek.
- **Mikroservisler:** Mikroservisler arasında asenkron iletişim sağlamak.
- **Olay Tabanlı Mimariler:** Olay tabanlı mimariler oluşturmak ve olayları tetiklemek.
- **İş Akışları:** Dağıtık sistemlerde iş akışlarını yönetmek ve koordine etmek.

Bu derste, Google Cloud Pub/Sub'ı detaylı olarak inceledik ve temel işlemleri öğrendik. Bir sonraki derste, Google Cloud IAM ve Güvenliği inceleyeceğiz.
