# AI.md — Yapay Zekâ Kullanım Bildirimi

## Proje Bilgileri

**Ders:** Web Tabanlı Programlama  
**Proje Adı:** Like-Orbital-Game  
**Proje Türü:** HTML5 Canvas tabanlı 2D kaçınma / refleks oyunu  
**Kullanılan Teknolojiler:** HTML, CSS, JavaScript, HTML5 Canvas  
**Kütüphane Kullanımı:** Harici oyun motoru veya framework kullanılmamıştır. Proje saf HTML, CSS ve JavaScript ile geliştirilmiştir.

Bu proje, tarayıcı üzerinde çalışan basit bir refleks oyunudur. Oyuncu, merkez etrafında dairesel hareket eden bir nesneyi kontrol eder. Oyuncu iç ve dış yörünge arasında geçiş yaparak engellerden kaçmaya çalışır. Oyun süresi ilerledikçe skor artar ve oyun zorlaşır.

Projedeki yörünge / kaçınma mekaniği, itch.io üzerinde yer alan [Orbital v2.3.2](https://jamiemcclenaghan.itch.io/orbital) oyunundan esinlenilerek hazırlanmıştır. Ancak proje kodları grup tarafından HTML5 Canvas ve saf JavaScript kullanılarak yeniden geliştirilmiştir.

---

## Yapay Zekâ Kullanımı Hakkında Beyan

Bu proje geliştirilirken yapay zekâ araçlarından destek alınmıştır. Yapay zekâ araçları; algoritma tasarımı, Canvas oyun döngüsü, dairesel hareket matematiği, çarpışma kontrolü, hata ayıklama ve dokümantasyon düzenleme amacıyla kullanılmıştır.

Proje tamamen yapay zekâya yaptırılmamıştır. Yapay zekâdan alınan cevaplar incelenmiş, proje yapısına göre düzenlenmiş, test edilmiş ve gerekli yerlerde değiştirilmiştir.

Oyun fikrinin seçimi, oynanış kararları, görsel tasarım tercihleri, değişken değerlerinin ayarlanması, test işlemleri, hata düzeltmeleri ve son kontroller grup tarafından yapılmıştır.

---

## Kullanılan Yapay Zekâ Araçları

| Araç | Kullanım Amacı |
|---|---|
| Cursor | Kod iskeleti, JavaScript düzenlemeleri, Canvas oyun döngüsü, hata ayıklama |
| Gemini | Dairesel hareket matematiği, alternatif çözüm önerileri, mantık kontrolü |
| ChatGPT | AI.md dosyasının düzenlenmesi ve yapay zekâ kullanım beyanının yazılması |

---

## Yapay Zekâdan Yardım Alınan Konular

Yapay zekâ araçlarından aşağıdaki konularda yardım alınmıştır:

1. HTML5 Canvas üzerinde oyun alanı oluşturma
2. `requestAnimationFrame` ile oyun döngüsü kurma
3. `Math.sin()` ve `Math.cos()` ile dairesel hareket oluşturma
4. Oyuncunun iç ve dış yörünge arasında geçiş yapması
5. `lerp` mantığı ile yumuşak geçiş sağlama
6. Engellerin dizi yapısıyla yönetilmesi
7. `Math.hypot()` ile daire-daire çarpışma kontrolü yapılması
8. Skor sisteminin kurulması
9. Oyun bitişi ve yeniden başlatma mantığının oluşturulması
10. Arka plan yıldızları ve görsel efektlerin düzenlenmesi
11. Zorluk seviyesinin zamanla artırılması
12. Ses dosyalarının oyuna eklenmesi
13. Tarayıcı autoplay kısıtlamaları nedeniyle sesin kullanıcı etkileşiminden sonra başlatılması
14. README ve AI.md dosyalarının düzenlenmesi

---

## Grup Tarafından Yapılan Katkılar

Aşağıdaki kısımlar grup tarafından belirlenmiş, uygulanmış veya son haline getirilmiştir:

- Proje fikrinin seçilmesi
- Oyunun HTML, CSS ve JavaScript dosya yapısına yerleştirilmesi
- Oyunun tarayıcıda test edilmesi
- Oyuncu hareketinin kontrol edilmesi
- Oyun hızının ayarlanması
- Skor artış hızının belirlenmesi
- Engel oluşturma sıklığının düzenlenmesi
- Çarpışma hassasiyetinin test edilmesi
- Renklerin ve görsel tasarımın seçilmesi
- Ses dosyalarının seçilmesi ve `ses/` klasörüne eklenmesi
- Kodun Türkçe açıklamalarla anlaşılır hale getirilmesi
- README dosyasının hazırlanması
- AI.md dosyasının düzenlenmesi

---

# Kullanılan Promptlar ve Alınan Cevaplar

Aşağıda proje geliştirme sürecinde yapay zekâ araçlarına yöneltilen promptlar ve alınan cevaplar yer almaktadır.

---

## Kayıt 1

**Kullanılan araç:** Cursor  
**Konu:** HTML5 Canvas oyun iskeleti oluşturma

### Prompt

```text
HTML, CSS ve saf JavaScript kullanarak Canvas üzerinde çalışan basit bir oyun iskeleti oluştur. Oyunda requestAnimationFrame kullanılmalı. Oyuncu merkez etrafında dönmeli. Kütüphane kullanılmasın.

Alınan Cevap

Yapay zekâ, HTML dosyasında bir canvas etiketi oluşturulmasını, JavaScript tarafında ise canvas context'inin alınmasını önerdi. Oyun döngüsü için requestAnimationFrame kullanılmasını ve her frame'de canvas'ın temizlenip oyuncunun yeniden çizilmesini anlattı.

Önerilen temel yapı şu mantıktaydı:

const canvas = document.getElementById("gameCanvas");
const ctx = canvas.getContext("2d");

let centerX = canvas.width / 2;
let centerY = canvas.height / 2;
let angle = 0;
let radius = 120;
let speed = 0.03;

function update() {
    angle += speed;
}

function draw() {
    ctx.clearRect(0, 0, canvas.width, canvas.height);

    const playerX = centerX + Math.cos(angle) * radius;
    const playerY = centerY + Math.sin(angle) * radius;

    ctx.beginPath();
    ctx.arc(playerX, playerY, 10, 0, Math.PI * 2);
    ctx.fill();
}

function gameLoop() {
    update();
    draw();
    requestAnimationFrame(gameLoop);
}

gameLoop();

Yapay zekâ ayrıca canvas'ın boyutunun HTML veya JavaScript üzerinden ayarlanabileceğini, oyun döngüsünün update() ve draw() fonksiyonlarına ayrılmasının kodu daha düzenli hale getireceğini belirtti.

Projede Nasıl Kullanıldı?

Bu cevap, projenin ilk oyun iskeletini oluşturmak için kullanıldı. Kod doğrudan kopyalanmadı; proje dosya yapısına, değişken isimlerine ve oyun mekaniğine göre düzenlendi.

Kayıt 2

Kullanılan araç: Gemini
Konu: Dairesel hareket matematiği

Prompt
Canvas oyununda x = merkezX + Math.cos(aci) * yaricap ve y = merkezY + Math.sin(aci) * yaricap formülleriyle merkez etrafında dairesel hareket oluşturuyorum. Bu kullanım doğru mu? Açısal hızı nasıl kontrol etmeliyim?
Alınan Cevap

Yapay zekâ, kullanılan formülün dairesel hareket için doğru olduğunu açıkladı. Bir noktanın merkez etrafında dönmesi için x koordinatının kosinüs, y koordinatının ise sinüs ile hesaplanabileceğini belirtti.

Açının zamanla artırılması gerektiğini ve açısal hızın bu artış miktarıyla kontrol edilebileceğini söyledi.

Önerilen mantık şu şekildeydi:

angle += angularSpeed;

x = centerX + Math.cos(angle) * radius;
y = centerY + Math.sin(angle) * radius;

Ayrıca angularSpeed değerinin büyütülmesi durumunda oyuncunun daha hızlı döneceğini, küçültülmesi durumunda ise daha yavaş döneceğini açıkladı.

Projede Nasıl Kullanıldı?

Bu cevap, oyuncunun merkez etrafında dönmesini sağlayan matematiksel hareket yapısını doğrulamak için kullanıldı. Oyuncunun konumu her frame'de açı ve yarıçap değerlerine göre yeniden hesaplandı.

Kayıt 3

Kullanılan araç: Cursor
Konu: İç ve dış yörünge geçişi

Prompt
Space tuşuna basıldığında oyuncunun iç ve dış yörünge arasında geçmesini istiyorum. Geçiş aniden olmasın, lerp ile yumuşak şekilde gerçekleşsin. JavaScript ile örnek mantık göster.
Alınan Cevap

Yapay zekâ, oyuncunun iki farklı yarıçap arasında hareket etmesi için currentRadius ve targetRadius değişkenlerinin kullanılmasını önerdi. Space tuşuna basıldığında hedef yarıçapın değiştirilmesini, her frame'de ise mevcut yarıçapın hedef yarıçapa doğru yaklaştırılmasını anlattı.

Önerilen mantık şu şekildeydi:

let innerRadius = 90;
let outerRadius = 150;
let currentRadius = innerRadius;
let targetRadius = outerRadius;

document.addEventListener("keydown", function(e) {
    if (e.code === "Space") {
        if (targetRadius === innerRadius) {
            targetRadius = outerRadius;
        } else {
            targetRadius = innerRadius;
        }
    }
});

function lerp(start, end, amount) {
    return start + (end - start) * amount;
}

function update() {
    currentRadius = lerp(currentRadius, targetRadius, 0.1);
}

Yapay zekâ, bu yöntemle oyuncunun aniden yer değiştirmeyeceğini ve daha yumuşak bir geçiş efekti oluşacağını belirtti.

Projede Nasıl Kullanıldı?

Bu cevapta verilen currentRadius, targetRadius ve lerp mantığı projeye uyarlandı. Oyuncunun Space tuşu ile iç ve dış yörünge arasında geçmesi sağlandı.

Kayıt 4

Kullanılan araç: Cursor
Konu: Engel oluşturma ve çarpışma kontrolü

Prompt
Canvas oyununda engelleri bir dizi içinde tutmak ve oyuncuyla çarpışmayı Math.hypot kullanarak daire-daire çarpışma kontrolüyle yapmak istiyorum. Basit ve anlaşılır bir örnek verir misin?
Alınan Cevap

Yapay zekâ, engellerin bir dizi içinde nesne olarak tutulabileceğini belirtti. Her engel için x, y ve radius değerlerinin saklanmasını önerdi.

Daire-daire çarpışma kontrolü için iki nesne arasındaki mesafenin hesaplanması gerektiğini söyledi. Eğer iki merkez arasındaki mesafe, yarıçapların toplamından küçükse çarpışma gerçekleşmiş sayılacağını açıkladı.

Önerilen mantık şu şekildeydi:

let obstacles = [
    { x: 100, y: 100, radius: 15 },
    { x: 300, y: 200, radius: 20 }
];

function checkCollision(player, obstacle) {
    const dx = player.x - obstacle.x;
    const dy = player.y - obstacle.y;
    const distance = Math.hypot(dx, dy);

    return distance < player.radius + obstacle.radius;
}

for (let obstacle of obstacles) {
    if (checkCollision(player, obstacle)) {
        gameOver = true;
    }
}

Yapay zekâ ayrıca engellerin her frame'de hareket ettirilebileceğini, ekrandan çıkan engellerin diziden silinebileceğini ve belirli aralıklarla yeni engeller üretilebileceğini açıkladı.

Projede Nasıl Kullanıldı?

Bu cevap, engellerin dizi içinde tutulması ve oyuncuyla çarpışmalarının kontrol edilmesi için kullanıldı. Math.hypot() fonksiyonu ile oyuncu ve engeller arasındaki mesafe hesaplandı.

Kayıt 5

Kullanılan araç: Cursor
Konu: Skor, oyun bitişi ve yeniden başlatma

Prompt
Canvas tabanlı oyunda skor sistemi, game over durumu ve yeniden başlatma butonu mantığını nasıl kurabilirim? JavaScript ile sade bir yapı göster.
Alınan Cevap

Yapay zekâ, skor için bir score değişkeni, oyun bitişi için ise gameOver değişkeni kullanılmasını önerdi. Oyun devam ederken skorun artırılabileceğini, çarpışma durumunda ise gameOver değerinin true yapılması gerektiğini belirtti.

Önerilen yapı şu şekildeydi:

let score = 0;
let gameOver = false;

function update() {
    if (gameOver) return;

    score++;

    // oyuncu, engel ve çarpışma kontrolleri burada yapılır
}

function draw() {
    ctx.clearRect(0, 0, canvas.width, canvas.height);

    ctx.fillText("Skor: " + score, 20, 30);

    if (gameOver) {
        ctx.fillText("Oyun Bitti", canvas.width / 2, canvas.height / 2);
    }
}

function restartGame() {
    score = 0;
    gameOver = false;
    obstacles = [];
}

Yapay zekâ, yeniden başlatma işlemi yapılırken skorun, engellerin, oyuncu konumunun ve oyun durumunun sıfırlanması gerektiğini açıkladı.

Projede Nasıl Kullanıldı?

Bu cevap, skor sistemi ve yeniden başlatma mantığının kurulmasında referans olarak kullanıldı. Projedeki değişken isimlerine ve oyun akışına göre düzenleme yapıldı.

Kayıt 6

Kullanılan araç: Cursor
Konu: Arka plan yıldızları ve görsel efektler

Prompt
Canvas oyunuma basit bir yıldızlı arka plan eklemek istiyorum. Yıldızlar küçük noktalar gibi görünsün ve oyun ekranına derinlik hissi katsın. JavaScript ile nasıl yapabilirim?
Alınan Cevap

Yapay zekâ, yıldızların bir dizi içinde tutulabileceğini ve her yıldız için x, y, radius ve speed değerlerinin tanımlanabileceğini söyledi. Her frame'de yıldızların hareket ettirilerek arka planda basit bir paralaks etkisi oluşturulabileceğini açıkladı.

Örnek mantık şu şekildeydi:

let stars = [];

for (let i = 0; i < 100; i++) {
    stars.push({
        x: Math.random() * canvas.width,
        y: Math.random() * canvas.height,
        radius: Math.random() * 2,
        speed: Math.random() * 0.5
    });
}

function drawStars() {
    for (let star of stars) {
        ctx.beginPath();
        ctx.arc(star.x, star.y, star.radius, 0, Math.PI * 2);
        ctx.fill();

        star.y += star.speed;

        if (star.y > canvas.height) {
            star.y = 0;
            star.x = Math.random() * canvas.width;
        }
    }
}

Yapay zekâ, bu yapının oyunun görsel olarak daha dinamik görünmesini sağlayacağını belirtti.

Projede Nasıl Kullanıldı?

Bu cevap, arka plan yıldızlarının oluşturulması için kullanıldı. Yıldız sayısı, hızları ve görünümleri proje tasarımına göre düzenlendi.

Kayıt 7

Kullanılan araç: Gemini
Konu: Zorluk seviyesinin zamanla artırılması

Prompt
Canvas tabanlı refleks oyununda zaman ilerledikçe oyunu zorlaştırmak istiyorum. Engel hızı veya engel oluşturma sıklığı zamanla artabilir. Bunu basit şekilde nasıl yapabilirim?
Alınan Cevap

Yapay zekâ, oyunda zorluğu artırmak için zaman veya skor değerinin kullanılabileceğini belirtti. Skor yükseldikçe engel hızının artırılabileceğini veya engel oluşturma aralığının azaltılabileceğini açıkladı.

Örnek olarak şu mantığı önerdi:

let difficulty = 1;
let score = 0;

function updateDifficulty() {
    difficulty = 1 + score / 1000;
}

Engel hızında bu değerin kullanılabileceğini söyledi:

obstacle.speed = baseSpeed * difficulty;

Ayrıca zorluğun çok hızlı artmaması için üst sınır koyulabileceğini belirtti:

difficulty = Math.min(difficulty, 5);
Projede Nasıl Kullanıldı?

Bu cevap, oyunun zamanla zorlaşması için referans olarak kullanıldı. Engel hızı ve oyun temposu skor ilerledikçe kademeli olarak artırıldı.

Kayıt 8

Kullanılan araç: Cursor
Konu: Ses dosyaları ve autoplay problemi

Prompt
JavaScript oyunuma arka plan müziği ve çarpışma sesi eklemek istiyorum. Ancak tarayıcı autoplay kısıtlaması var. Kullanıcı Başlat butonuna bastıktan sonra sesleri nasıl başlatabilirim?
Alınan Cevap

Yapay zekâ, modern tarayıcıların kullanıcı etkileşimi olmadan ses oynatmayı engelleyebileceğini belirtti. Bu yüzden arka plan müziğinin veya efekt seslerinin kullanıcı bir butona bastıktan sonra başlatılması gerektiğini açıkladı.

Önerilen yapı şu şekildeydi:

const bgMusic = new Audio("ses/music.mp3");
const hitSound = new Audio("ses/hit.mp3");

bgMusic.loop = true;
bgMusic.volume = 0.3;
hitSound.volume = 0.7;

startButton.addEventListener("click", function() {
    bgMusic.play();
    startGame();
});

function playHitSound() {
    hitSound.currentTime = 0;
    hitSound.play();
}

Yapay zekâ, efekt seslerinin tekrar çalması için currentTime = 0 kullanılabileceğini de belirtti.

Projede Nasıl Kullanıldı?

Bu cevap, oyun içi seslerin eklenmesi için kullanıldı. Arka plan müziği kullanıcı oyunu başlattıktan sonra çalışacak şekilde düzenlendi. Çarpışma gibi olaylarda efekt sesi tetiklendi.

Kayıt 9

Kullanılan araç: Cursor
Konu: Kodun daha anlaşılır hale getirilmesi

Prompt
JavaScript Canvas oyun kodumu daha okunabilir hale getirmek istiyorum. Fonksiyonları update, draw, restartGame gibi bölümlere ayırmak mantıklı mı? Türkçe yorumlarla daha anlaşılır hale getirebilir misin?
Alınan Cevap

Yapay zekâ, oyun kodunun fonksiyonlara ayrılmasının daha doğru ve okunabilir bir yapı sağlayacağını belirtti. Özellikle oyunlarda güncelleme ve çizim işlemlerinin ayrılmasının yaygın bir yöntem olduğunu açıkladı.

Önerilen fonksiyon yapısı şu şekildeydi:

function update() {
    // Oyun durumunu güncelle
}

function draw() {
    // Canvas üzerindeki nesneleri çiz
}

function checkCollisions() {
    // Oyuncu ve engeller arasındaki çarpışmaları kontrol et
}

function restartGame() {
    // Oyunu başlangıç durumuna döndür
}

function gameLoop() {
    update();
    draw();
    requestAnimationFrame(gameLoop);
}

Yapay zekâ, değişken isimlerinin anlamlı seçilmesini ve karmaşık yerlerde kısa yorumlar kullanılmasını önerdi.

Projede Nasıl Kullanıldı?

Bu cevap, kodun daha düzenli ve okunabilir hale getirilmesinde kullanıldı. Fonksiyon yapısı sadeleştirildi ve bazı bölümlere Türkçe açıklamalar eklendi.

Kayıt 10

Kullanılan araç: ChatGPT
Konu: AI.md dosyasının düzenlenmesi

Prompt
Web tabanlı programlama dersinde proje ödevimiz var. Proje ödevinde şöyle bir şart var: Projenizi geliştirirken yapay zeka araçlarına sorularınızı yöneltebilirsiniz. Yararlandığınız yapay zeka araçlarını ve kullanım biçiminizi bildirmelisiniz. Kullandığınız promptların ve aldığınız cevapların tümünü, reponuzda AI.md isminde bir markdown dosyası oluşturup içerisine yerleştirmelisiniz. Tamamen yapay zekaya yaptırılmış projeler geçersiz sayılacaktır. Biz de kaba taslak bir AI.md yazdık. Bunu hocanın isteğine göre ayarlar mısın?
Alınan Cevap

ChatGPT, mevcut AI.md metninin sadece özet beyan şeklinde olduğunu ve hocanın istediği şartı tam karşılamadığını belirtti. Özellikle kullanılan promptların ve alınan cevapların ayrı ayrı yazılması gerektiğini söyledi.

ChatGPT tarafından önerilen düzenleme şunları içeriyordu:

Proje bilgileri bölümü
Yapay zekâ kullanım beyanı
Kullanılan yapay zekâ araçları tablosu
Hangi konularda yardım alındığı
Grup tarafından yapılan katkılar
Prompt ve cevap kayıtları
Projenin tamamen yapay zekâya yaptırılmadığına dair açıklama

ChatGPT ayrıca yapay zekâdan alınan gerçek cevapların uydurulmaması gerektiğini, Cursor ve Gemini geçmişinden gerçek cevapların mümkün olduğunca eklenmesinin daha doğru olacağını belirtti.

Projede Nasıl Kullanıldı?

Bu cevap, AI.md dosyasının daha düzenli ve hocanın istediği formata daha uygun hale getirilmesi için kullanıldı.

Kayıt 11

Kullanılan araç: ChatGPT
Konu: AI.md dosyasının son halinin hazırlanması

Prompt
Bana full ne yazmam gerektiğini atar mısın?
Alınan Cevap

ChatGPT, AI.md dosyasına koyulabilecek tam bir markdown metni hazırladı. Metinde proje bilgileri, yapay zekâ kullanım beyanı, kullanılan araçlar, yardım alınan konular, grup katkısı ve prompt-cevap kayıtları yer aldı.

ChatGPT ayrıca Cursor ve Gemini’den gerçekten alınmayan cevapların uydurulmaması gerektiğini, varsa gerçek konuşma geçmişlerinden alınan cevaplarla değiştirilmesi gerektiğini belirtti.