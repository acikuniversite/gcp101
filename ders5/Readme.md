# Ders 5: Google App Engine (Google App Engine)

Bu derste, Google App Engine'i (GAE) detaylı olarak inceleyeceğiz. GAE, geliştiricilerin altyapı yönetimiyle uğraşmadan uygulamalarını dağıtmasına ve ölçeklendirmesine olanak tanıyan tam yönetimli bir platformdur.

## İçindekiler

1. Google App Engine'e Giriş
2. App Engine Uygulaması Oluşturma
3. Geliştirme Ortamı Kurulumu
4. İlk Uygulamayı Dağıtma
5. App Engine Hizmetleri ve Özellikleri
6. App Engine ile Sürüm Yönetimi
7. App Engine ile Ölçeklendirme
8. Örnek Kullanım Senaryoları

## 1. Google App Engine'e Giriş

Google App Engine (GAE), geliştiricilerin uygulamalarını yazılım altyapısı yönetimiyle uğraşmadan dağıtmasına olanak tanıyan tam yönetimli bir platformdur. App Engine, uygulamalarınızı otomatik olarak ölçeklendirir ve çeşitli programlama dillerini destekler.

## 2. App Engine Uygulaması Oluşturma

GAE ile bir uygulama oluşturmak için aşağıdaki adımları takip edin:

1. **GCP Konsoluna Giriş:** [GCP Konsolu](https://console.cloud.google.com/)na giriş yapın.
2. **App Engine Sekmesine Geçiş:** Sol menüden "App Engine" > "Dashboard" seçeneğine tıklayın.
3. **Uygulama Oluşturma:** "Create Application" butonuna tıklayın.
4. **Bölge Seçimi:** Uygulamanız için bir bölge seçin ve onaylayın.

## 3. Geliştirme Ortamı Kurulumu

App Engine ile uygulama geliştirmek için uygun geliştirme ortamını kurmanız gerekmektedir. Aşağıdaki örnek, Python ile bir uygulama geliştirmek içindir:

1. **Python Kurulumu:** [Python](https://www.python.org/downloads/)'ı indirip kurun.
2. **Google Cloud SDK Kurulumu:** [Google Cloud SDK](https://cloud.google.com/sdk/docs/install) ile GAE komut satırı araçlarını yükleyin.
3. **App Engine SDK Kurulumu:** 
    ```sh
    gcloud components install app-engine-python
    ```

## 4. İlk Uygulamayı Dağıtma

Basit bir Python uygulaması oluşturalım ve GAE'ye dağıtalım:

1. **Proje Dizini Oluşturma:** 
    ```sh
    mkdir my-app
    cd my-app
    ```
2. **main.py Dosyasını Oluşturma:**
    ```python
    import webapp2

    class MainPage(webapp2.RequestHandler):
        def get(self):
            self.response.headers['Content-Type'] = 'text/plain'
            self.response.write('Hello, World!')

    app = webapp2.WSGIApplication([
        ('/', MainPage),
    ], debug=True)
    ```
3. **app.yaml Dosyasını Oluşturma:**
    ```yaml
    runtime: python27
    api_version: 1
    threadsafe: true

    handlers:
    - url: /.*
      script: main.app
    ```
4. **Uygulamayı Dağıtma:**
    ```sh
    gcloud app deploy
    ```
5. **Uygulamayı Gözden Geçirme:**
    ```sh
    gcloud app browse
    ```

## 5. App Engine Hizmetleri ve Özellikleri

App Engine, aşağıdaki hizmetleri ve özellikleri sunar:

- **Otomatik Ölçeklendirme:** Trafik arttıkça uygulamanızı otomatik olarak ölçeklendirir.
- **Sürüm Yönetimi:** Farklı sürümleri yönetme ve dağıtma yeteneği sağlar.
- **Entegrasyon:** GCP'nin diğer hizmetleriyle kolayca entegre olur.
- **Güvenlik:** Kimlik doğrulama ve yetkilendirme gibi güvenlik özelliklerini destekler.

## 6. App Engine ile Sürüm Yönetimi

GAE, uygulamanızın farklı sürümlerini yönetmenize olanak tanır:

- **Yeni Sürüm Dağıtma:**
    ```sh
    gcloud app deploy --version v2
    ```
- **Sürüm Geçişi:**
    ```sh
    gcloud app services set-traffic --splits v1=0.5,v2=0.5
    ```

## 7. App Engine ile Ölçeklendirme

App Engine, trafik ihtiyaçlarınıza göre uygulamanızı otomatik olarak ölçeklendirir. Ayrıca, manuel ölçeklendirme ayarları yapabilirsiniz:

- **Otomatik Ölçeklendirme:** Varsayılan ayardır.
- **Manuel Ölçeklendirme:**
    ```yaml
    manual_scaling:
      instances: 5
    ```
- **Temel Ölçeklendirme:**
    ```yaml
    basic_scaling:
      max_instances: 10
      idle_timeout: 5m
    ```

## 8. Örnek Kullanım Senaryoları

Google App Engine çeşitli kullanım senaryoları için uygundur:

- **Web Uygulamaları:** Yüksek trafik alan web uygulamalarını hızlıca dağıtmak ve ölçeklendirmek.
- **Mobil Arka Plan Servisleri:** Mobil uygulamalar için arka plan servislerini barındırmak.
- **API Hizmetleri:** RESTful API'ler oluşturmak ve yönetmek.

Bu derste, Google App Engine'i detaylı olarak inceledik ve temel işlemleri öğrendik. Bir sonraki derste, Google Cloud Functions'ı inceleyeceğiz.
