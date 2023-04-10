# Tailwind CSS- Tutorial Notlar 

	:chains:  TailwindCSS ve Bootstrap arasındaki fark TailwindCSS’in çok daha özelleştirilebilir olmasıdır.

    
 <h3>:link: Kurulum Aşaması</h3>

    :arrow_right: Bilgisayarda nodejs yüklüyken vs code’da terminale ```npm init -y ``` yazarsak Package json dosyasını klasörümüze otomatik olarak getirir. Node js versiyon kontrolü yapmak içinse ```npm -v yazmamız``` yeterlidir.

    :arrow_right: ``` npm install -D tailwindcss ``` tailwind css indirir.
 
    :arrow_right: ``` npx tailwindcss init ``` tailwind.config.js dosyası ekler.

<h4>  tailwind.config.js Nedir :question: </h4>

    :pushpin: Public klasörümdeki dosyaların ve bu dosyaların veya klasörlerin altında bulunan html js dosyalarını content olarak düşünebiliriz. Böylece public’in içindeki index.html’e tailwind kodlarımızı yazabileceğiz.

<h4> :link: Diğer Notlar </h4>

    :pushpin: İnput css’e yapıştırdığımız 
                ```
                 @tailwind base;
                 @tailwind components;
                 @tailwind utilities;
                 ```
            Kodları tailwind içerisindeki base component ve utilities classlarını kullanabileceğimizi gösteriyor.

    :pushpin: Daha sistemli bir çalışma için Visual Studio code’dan live server ve Tailwind CSS IntelliSense kurmamız gerek.

    :pushpin: Tekrar projeyi çalıştırmayı kolaylaştırmak için package.json’daki test kısmı yerine ``` "watch": "npx tailwindcss -i ./input.css -o ./public/css/style.css --watch" ``` yazıyoruz. Tekrar projyei çalıştırmak istediğmiz zaman ``` npm run watch ``` yazmamız yeterli olacaktır. Projeden her çıktığımızda 0’dan başlatabilmek için npm run watch komutunu çalıştırmamız gerekiyor.

    :pushpin: Bazı fontlar tailwind css’te varsayılandır bunların yanında kendi istediğimiz fontları kullanabilmek için Tailwind.config.js’in içindeki extend kısmının içindeki paranteze :

    ```
             fontFamily:
                   {
                      gemunu: ['Gemunu Libre', 'sans-serif'],
                      open: ['Open Sans', 'sans-serif']
                   }
                        şeklinde yazarız.
    ```

    :pushpin: Renkler içinde benzer bir kullanım söz konusudur. Renkleri dahil etmek içinse yine Tailwind.config.js’in içindeki extend kısmına font family’den sonra 

    ```
             colors: {

                      ‘gega-red’:’#BC1A4S’,
                      ‘gega-melon’:’#FF0369’,
                      ‘gega-grey’:’#D00DD0’,
                      ‘gega-white’:’#F7F7F7’,
                     } 
                     şeklinde yazarız.
    ```

    :pushpin: Normalde container class’ı kendisi ortalar ama Tailwind’de böyle bir şey olmaz. Tailwind kullanırken container class’ının sürekli kendini ortalamasını istiyorsak tailwind.config.js’te theme kısmının içine 
    ```
                      container: {
                      center: true,
                     }
    ```
              yazarız. Extend değil theme içine yazmamızın sebebi artık bunu tüm konteynırlar için kullanacak olmamız default yani varsılan olarak ayarlamak istememiz.
        
    :pushpin: Container flex item center dediğimizde container’deki itemların tamamını yatay olarak birbirlerine ortalamış oluyor. Elemanların birbirlerine uzaklıkları içinde justify-between kullandık. Logoyla menü arasında boşluk olması için space-x-16 yazdık.

    :pushpin: Ortadaki ve sağdaki menünün birbirinden ayrılması için justify-betwen yazarız. Flex-1 logoya göre diğerlerinin mümkün olduğu kadar çok yer kaplamasını sağlar.

    :pushpin: Alt+Shift+Alt ok satırı aynen kopyalar ve alt satıra yapıştırır.

    :pushpin: Yazının veya simgenin hemen gelmesi yerine transittonlu gelmesi için input kısmına transition duration-500 ekleriz.

    :pushpin: Container’ı daraltmak için tailwind.config.js’in içine center: true’dan hemen sonra  :
    ```
                       screens:{
                           lg: '1140px',
                           xl: '1140px',
                          '2xl': '1140px'   } 
    ```
             yazıyoruz.

    :pushpin: Tailwind CSS’te herhangi bir şeyde takılırsak tailwins css’in resmi sayfasından dökümantasyonlara bakarak sorunu çözebiliriz. 

    :pushpin: Ekran küçüldüğünde menü yazılarını da küçültmek için header class’ının içine py-6 lg:py-12 ekleriz. Aynısını container için yapmak istiyorsak header container içinde space-x-8 lg:space-x-16 yazıyoruz. Login ve Sign Up’ın birbirini ezmemesi için Sign Up’ın claass’ına  whitespace-nowrap ekliyoruz. lg= large ekran

    :pushpin: Md yerine lg kullanmamızın sebebi larg ekrana kadar bir sorun yaşamamamız. Larg ekrandan daha küçük ekranlarda sorun çıkıyor bu yüzden lg kullanıyoruz.

    :pushpin: Küçük ekranlarda menüde bozulmalar olduğu için nav classına hidden md:flex yazarak öncelikle küçük ekranda yazıları yokediyoruz. Daha sonra mobil icon yerleştiriyoruz. Menü çizgileri arasında bir boşluk oluşması için space-y-1 yazıyoruz. Çizgilerin yuvarlaklaşması için de rounded-full yazıyoruz. Menü iconu yapmak için kullandığımız kodlar ise şu şekilde:
      
    ```
         <!--Menu Icon For Small Screens-->
        <div class="block md:hidden pr-4">
          <div class="space-y-1 cursor-pointer">
            <div class="bg-gega-grey w-8 h-1 rounded-full"></div>
            <div class="bg-gega-grey w-8 h-1 rounded-full"></div>
            <div class="bg-gega-grey w-8 h-1 rounded-full"></div>
          </div>
        </div>
    ```

    :pushpin: Başlıklara ve linklere özellikler vermek için input.css’te yazdıklarımızın altına aşağıdaki kodları ekliyoruz:
    ```
               @layer base {
                    h1, h2, h3, h4, h5, h6 {
                   @apply font-gemunu uppercase;
                           }
                     h2 {
                     @apply text-2xl tracking-wider
                           }
                      a {
                     @apply font-gemunu;
                        }
                           }
    ```

    :pushpin: Tailwind css içinde olmayan farklı spacingler yani uzunluk, büyüklük rem değerleri vermek istiyorsak tailwind.config.js’in içine colorsın hemen altına   

    ```
                spacing: {
                     128: '32rem',
                         },
    ```

    Yazarız. 128 tailwind css’te hazır bulunmayan 32 rem demektir. 32 yerine 40 yazsaydık 40 rem olarak alacaktı.

    :pushpin: Görselin kendisini kapsayan hero section ile aynı boyutta olmasını istediğimizden class’ına h-full w-full veriyoruz. Tamamen kapsaması için de yine class’a object-cover yazıyoruz.
    Aşağıda olmasını istediğimiz için hero content’in classına bottom-0 verdik. Aşağıyı kapsaması için w-full’de yazdık. Resimde yukarıdan aşağıya giderken siyahlık artıyor bu özelliği verebilmek için  bg-gradient-to-b from-transparent to-black yazıyoruz.

    :pushpin: Hero Content Container’ı Hero Content’ten ayrı yazmamızın sebebi içeriği resimden  bağımsız olarak doldurmak istememiz. Harfler arasında boşluk olması için tracking-wider ekliyoruz. Group hover yukarıdaki başlıkla aşağıdaki başlık arasındaki boşluğun artmasını sağlar.

    :pushpin: h-64 md:h-96 lg:h-128 Bunun anlamı mobil durumda yükseklik 64px orta ekranlarda 96 büyük ve daha sonrası ekranlarda ise yükseklik 128 olsun demektir.

<!--py=yukarıdan aşağıya padding-->
    
    :pushpin: Basis-2/3 sayfanın 2/3’ünü kapsasın demek. Divide-x’i çizgilerin görünümünü sağlamak için kullandık.
    Resmin üzerine geldiğimizde resmin büyümesini istiyorsak group-hover:scale-110 grup-hover:opacity-50 duration-500 kodlarını class içine yazarız.

    :pushpin: Fotoğrafların aşağıya doğru tek tek bir satır gibi gelmesini istiyorsak flex-col yazarız. Yüksekliğin tamamını kapsaması için de h-full yazıyoruz. İçeriklerin birbirine mesafesinin orantılı olması içim justify-center yazarız.

    :pushpin: Grid-cols-4 class’ı ile içerikleri 4’er 4’er bölüyoruz 4’ü geçtiğinde bir alt satıra atmasını sağlıyoruz. Breakpointlere göre bu sayıyı değiştirebiliyoruz. Boşluk vermek için p-4 pl-4 gibi şeyler kullanıyoruz. Yanyana olduğunda birbirinden daha uzak olmasını istdeğimiz elemanlar için justify-between class’ını veririz.

    :pushpin: Justify-end class’ı elemanları sola doğru yanaştırır.

    :pushpin: Grid yapısını kullandığımızda 5 sütundan oluşmasını istiyorsak grid grid-cols-5 kullanırız. gap-2 boşluk verir.

    :pushpin: Border border-gega-red dersek border kırmızı olur. Alta geçmeleri önlemek için flex class’ını veririz. Birbini tekrar eden classlar için input.css içinde custom classlar oluşturulabilir. Tailwind.css üzerinden reusing styles yazarak detaylı bakılabilir ama custom class’lar tailwind’in utility first ilkesine karşıdır akılda tutmak ve mantıklı bir şekilde kullanmak zordur.

    :pushpin: Dark mode için 2 strateji izlenebilir birisi class birisi media stratejisi. Class stratejisini kullanmak için yapmamız gereken ilk şey dark mode’u bir class olarak belirtmek. Bunu yapabilmek için tailwind.config.js’in içinde content’in hemen altına  darkMode: 'class', Yazıyoruz. Body’e class olarak dark verdikten sonra dark modu çalıştırmak için body’nin hemen altına bir buton oluşturuyoruz.

    :dagger: Umarım tüm bu notlar işinize yarar. Çalışmalarınızda başarılar dilerim. 




                

# TailwindCSS-Tutorial-Notlar
