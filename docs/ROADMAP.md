
# Proje tanımlama Dokümanı

## Amaç

Tecrübesi olmayan kişilerin bir araya gelerek intermediate seviyesinde yardımlaşarak projeler yapmalarını sağlayacak bir sistem.

## 1. Aşama
1. Aşamada ekstra özellikler olmayacak
    Bu aşamada sadece projenin en temel özellikleri olacak. Yani görevler, aktiviteler ve projeler olacak sistemde.
    - Proje anasayfasında 
        - Proje Başlığı
        - Proje Açıklaması
        - Belki üyelerin listesi (right sidebar içinde)
        - Aktivitelerin horizontal şeklinde listesi (frontend, backend, mobile vs.)
        - Projenin kaçta kaçı'nın bittiğinin yüzdesi
        - Kaç kullanıcı olduğu
        - Kaç görev ve aktivite tanımlandığını gösteren widgetler olacak.
        - Akış: hangi kullanıcının hangi task'ı yarattığı, tamamladığı, süresini geçirdiği görülmeli. Bu da feed olacak. Widgetlerin altında görülecek.

    - Aktiviteler ana sayfasında
        - Aktivite başlığı
        - Aktivite Açıklaması
        - Aktivitenin projesi (bunu breadcrumb şeklinde gösterebilirsiniz.)
        - Bu Aktiviteye katılan kaç üye olduğu (Burada bir sürü join sorgusu yapmanız gerekecek)
        - Aktivitedeki toplam görev sayısı
        - Görevlerin tamamlanma yüzdesi
        - Ve yine akış widgeti olacak. Projeler sayfasındaki aynı componenti kullanabilirsiniz. Sadece aktiviteye göre filtreleme yapacaksınız.

    - Görev Sayfasında
        - Görev Başlığı
        - Varsa açıklaması
        - Görevin aktivitesi ve projesi (bunu breadcrumb şeklinde gösterebilirsiniz.)
        - Görevi yapan kullanıcı
        - Tamamlanıp tamamnlanmadığı
        - Varsa deadline (Burada da datepicker kullanmanız gerek)

    - Üyenin sayfasında, hangi projelere katıldığı, hangi aktivitelere üye olduğu ve hangi görevleri tamamladığı görülecek
    - Ayrıca üye kendi sayfasını görüyorsa parolasını ve epostasını değiştiebileceği bir form olmalı.

### Database Model
    - projects
        - id
        - title
        - description
        - project_type_id FK

    - project_types
        - id
        - title
        - description

    - activities 
        - id
        - title
        - description
        - project_id FK
        - activity_type_id FK

    - activity_types
        - id
        - title

    - tasks 
        - id
        - title
        - description
        - deadline
        - completed
        - activity_id FK
        - user_id FK

    - users
        - id
        - username
        - email
        - password
        - role_id

    - projects_users
        - user_id FK
        - project_id FK
    
    - roles (admin, project_owner, member)
        - id
        - title
    
    - logs
        - id
        - content (json: content: string, type: feed or debug)
        - datetime


## 2. Aşama
Birinci aşamayı tamamladığınızda görevlere yorum yapma, projeleri topluca puanlama, proje fikirlerine yorum yapma, otomatik olarak arka planda GPT'ye bağlanıp görevleri aktiviteleri ve taskları ona generate ettirme gibi fantastik şeyler yapacağız ama şimdilik birinci aşamayı tamamlayalım.
