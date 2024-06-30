# Ders 3: Google Compute Engine (Google Compute Engine)

Bu derste, Google Compute Engine'i (GCE) detaylı olarak inceleyeceğiz. GCE, Google Cloud Platform'un sanal makine hizmetidir ve çeşitli uygulamaları çalıştırmak için güçlü bir altyapı sunar.

## İçindekiler

1. Google Compute Engine'e Giriş
2. Sanal Makine (VM) Oluşturma
3. VM Yönetimi
4. VM'ye Bağlanma
5. Örnek Kullanım Senaryoları
6. VM Güvenliği

## 1. Google Compute Engine'e Giriş

Google Compute Engine, GCP'nin sanal makine hizmetidir. Kullanıcılar, GCE ile sanal makineler oluşturabilir, yönetebilir ve bu makinelerde uygulamalarını çalıştırabilirler. GCE, yüksek performans ve ölçeklenebilirlik sunarak her türlü uygulama için uygun bir altyapı sağlar.

## 2. Sanal Makine (VM) Oluşturma

GCE ile bir sanal makine oluşturmak için aşağıdaki adımları takip edin:

1. **GCP Konsoluna Giriş:** [GCP Konsolu](https://console.cloud.google.com/)na giriş yapın.
2. **Compute Engine Sekmesine Geçiş:** Sol menüden "Compute Engine" > "VM instances" seçeneğine tıklayın.
3. **VM Oluşturma:** "Create instance" butonuna tıklayın.
4. **VM Ayarları:**
    - **İsim:** Sanal makinenize bir isim verin.
    - **Bölge:** VM'inizi çalıştırmak istediğiniz bölgeyi seçin.
    - **Makine Türü:** İhtiyacınıza uygun bir makine türü seçin (örneğin, f1-micro).
    - **Boot Disk:** İşletim sistemini ve diski seçin (örneğin, Debian GNU/Linux).
5. **Firewall Kuralları:** "Allow HTTP traffic" ve "Allow HTTPS traffic" seçeneklerini işaretleyin.
6. **Oluşturma:** "Create" butonuna tıklayarak VM'inizi oluşturun.

## 3. VM Yönetimi

Oluşturduğunuz VM'leri yönetmek için GCP Konsolu'nu kullanabilirsiniz. Aşağıdaki işlemleri gerçekleştirebilirsiniz:

- **Başlatma/Durdurma:** VM'inizi başlatabilir veya durdurabilirsiniz.
- **Yeniden Başlatma:** VM'inizi yeniden başlatabilirsiniz.
- **Silme:** VM'inizi silebilirsiniz.
- **Yapılandırma Değişiklikleri:** VM'inizin yapılandırmasını değiştirebilirsiniz (örneğin, disk ekleme veya makine türünü değiştirme).

## 4. VM'ye Bağlanma

Oluşturduğunuz VM'e SSH üzerinden bağlanabilirsiniz:

1. **GCP Konsolu:** VM instances sayfasında, bağlanmak istediğiniz VM'in yanındaki "SSH" butonuna tıklayın.
2. **Terminal:** Alternatif olarak, aşağıdaki komutu kullanarak terminal üzerinden bağlanabilirsiniz:
    ```sh
    gcloud compute ssh [INSTANCE_NAME] --zone=[ZONE]
    ```
    Örneğin:
    ```sh
    gcloud compute ssh my-vm-instance --zone=us-central1-a
    ```

## 5. Örnek Kullanım Senaryoları

Google Compute Engine çeşitli kullanım senaryoları için idealdir:

- **Web Uygulamaları:** Yüksek trafik alan web uygulamalarını barındırmak.
- **Veritabanları:** Büyük ölçekli veritabanlarını çalıştırmak.
- **Veri Analizi:** Büyük veri setleri üzerinde analiz yapmak.
- **Geliştirme ve Test:** Yazılım geliştirme ve test ortamları oluşturmak.

## 6. VM Güvenliği

Sanal makinelerinizin güvenliğini sağlamak için aşağıdaki önlemleri alabilirsiniz:

- **Firewall Kuralları:** İhtiyacınıza göre firewall kuralları oluşturun ve yapılandırın.
- **SSH Anahtarları:** Güvenli bağlantılar için SSH anahtarlarını kullanın.
- **Güncellemeler:** İşletim sisteminizi ve yazılımlarınızı düzenli olarak güncelleyin.
- **IAM Rolleri:** Kullanıcı erişimlerini yönetmek için IAM (Identity and Access Management) rollerini kullanın.

Bu derste, Google Compute Engine ile sanal makineler oluşturmayı ve yönetmeyi öğrendiniz. Bir sonraki derste, Google Cloud Storage'ı inceleyeceğiz.
