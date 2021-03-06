---
uid: web-forms/overview/deployment/configuring-server-environments-for-web-deployment/configuring-a-web-server-for-web-deploy-publishing-remote-agent
title: Bir Web sunucusunu yapılandırma için Web dağıtımı yayımlama (Uzak Aracı) | Microsoft Docs
author: jrjlee
description: Bu konu, Web'de yayımlama ve IIS Web dağıtımı kullanarak dağıtımını desteklemek için bir Internet Information Services (IIS) web sunucusu yapılandırmanız açıklar...
ms.author: riande
ms.date: 05/04/2012
ms.assetid: 239c7aa8-d09a-4d02-9c0e-6bd52be5f0d5
msc.legacyurl: /web-forms/overview/deployment/configuring-server-environments-for-web-deployment/configuring-a-web-server-for-web-deploy-publishing-remote-agent
msc.type: authoredcontent
ms.openlocfilehash: 7350e986130af7426603e861622949f580512339
ms.sourcegitcommit: 45ac74e400f9f2b7dbded66297730f6f14a4eb25
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/16/2018
ms.locfileid: "41756171"
---
<a name="configuring-a-web-server-for-web-deploy-publishing-remote-agent"></a>Bir Web sunucusunu Web dağıtımı yayımlama (Uzak Aracı) için yapılandırma
====================
tarafından [Jason Lee](https://github.com/jrjlee)

[PDF'yi indirin](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/63/56/8130.DeployingWebAppsInEnterpriseScenarios.pdf)

> Bu konuda, Web'de yayımlama ve IIS Web Dağıtım Aracı (Web dağıtımı) uzak aracı hizmetini kullanarak dağıtımını desteklemek için bir Internet Information Services (IIS) web sunucusu yapılandırma konusunda açıklanmaktadır.
> 
> Web dağıtımı 2.0 veya üzeri çalışırken, uygulamaları veya web sunucusuna siteleri almak için kullanabileceğiniz üç ana yaklaşım vardır. Şunları yapabilirsiniz:
> 
> - Kullanım *Web dağıtımı aracı uzak hizmet*. Bu yaklaşım web sunucusunun daha az yapılandırma gerektirir, ancak hiçbir şey sunucuya dağıtmak için bir yerel sunucu yöneticisinin kimlik bilgilerini sağlamanız gerekir.
> - Kullanım *Web dağıtımı işleyicisi*. Bu yaklaşım, çok daha karmaşıktır ve web sunucusu kurmak için ilk daha fazla çaba gerektirir. Ancak, bu yaklaşımı kullandığınızda, dağıtım gerçekleştirmek yönetici olmayan kullanıcıların IIS yapılandırabilirsiniz. Web dağıtımı işleyicisi, yalnızca IIS 7 veya sonraki bir sürümü kullanılabilir.
> - Kullanım *çevrimdışı dağıtım*. Bu yaklaşım web sunucusunun en az yapılandırma gerektirir, ancak sunucu yönetici el ile web paketi sunucuya kopyalayın ve IIS Yöneticisi'yle içe aktarın.
> 
> Anahtar özellikler, avantajları ve dezavantajları bu yaklaşımların hakkında daha fazla bilgi için bkz. [Web dağıtımı için doğru yaklaşımı seçme](choosing-the-right-approach-to-web-deployment.md).


## <a name="is-the-web-deploy-remote-agent-the-right-approach-for-you"></a>Web dağıtımı uzak aracı aldığı doğru yaklaşım sizin için mi?

İçerik dağıtacak kullanıcının hedef sunucuda bir yönetici kimlik bilgilerini sağlayabilir, Evet. Bu yaklaşım genellikle bu senaryoları türlerinde tercih edilir:

- Geliştirici hedef web sunucusu ve veritabanı sunucusu üzerinde tam denetime sahip olduğu geliştirme ve test ortamları.
- Daha küçük kuruluşlar, tek bir kullanıcı veya kullanıcıların küçük bir grup tüm uygulama yaşam döngüsü denetime sahiptir.

Çok sayıda büyük kuruluşların ve hazırlık veya üretim ortamları için özellikle, bu kullanıcılara, web sunucuları üzerinde yönetici hakları vermek için gerçekçi değildir genellikle. Barındırılan web sunucusu durumunda, bu durum özellikle beklenmez. Ayrıca, bir yapı sunucusunun dağıtımı otomatik hale getirmek planlıyorsanız, dağıtım işlemi için yönetici kimlik bilgilerini kullanın istemeyebilirsiniz. Bu senaryolarda, web sunucularınızın dağıtımını kullanarak destekleyecek şekilde yapılandırma [Web dağıtımı işleyicisi](configuring-a-web-server-for-web-deploy-publishing-web-deploy-handler.md) daha tatmin edici bir seçim sağlayabilir.

## <a name="task-overview"></a>Görev genel bakış

Bu konuda kabul edin ve Web dağıtımı uzak aracısının yaklaşımı kullanarak uzak bir bilgisayardan web paketleri dağıtmak için bir Internet Information Services (IIS) 7.5 web sunucusunun nasıl yapılandırılacağı açıklanmaktadır. Şunları yapmanız gerekir:

- IIS 7.5 ve IIS 7 önerilen Yapılandırması'nı yükleyin.
- Web dağıtımı 2.1 veya üzerini yükleyin.
- Dağıtılan içerik barındırmak için bir IIS Web sitesi oluşturun.
- Web dağıtım aracı hizmetinin çalıştığından emin olun.

Örnek çözüm özellikle barındırmak için için gerekir:

- .NET Framework 4. 0'ı yükleyin.
- ASP.NET MVC 3 yükleyin.

Bu konuda, bu yordamların her biri gerçekleştirme gösterilmektedir. Bu konudaki yönergeler ve görevleri ile birlikte Windows Server 2008 R2 çalıştıran bir temiz sunucusu derleme başlatılıyor varsayılır. Devam etmeden önce şunlardan emin olun:

- Windows Server 2008 R2 Service Pack 1 ve tüm kullanılabilir güncelleştirmeler yüklenir.
- Etki alanına katılmış sunucusudur.
- Sunucuda bir statik IP adresi var.

> [!NOTE]
> Bilgisayarlarının bir etki alanına katılmasını sağlama hakkında daha fazla bilgi için bkz: [katılan bilgisayarların etki alanı ve günlüğe kaydetme üzerinde](https://technet.microsoft.com/library/cc725618(v=WS.10).aspx). Statik IP adreslerini yapılandırma hakkında daha fazla bilgi için bkz. [statik bir IP adresi yapılandırın](https://technet.microsoft.com/library/cc754203(v=ws.10).aspx). Uzak Aracı hizmeti tarafından IIS 6 ve sonraki sürümlerde desteklenir ve bir etki alanına katılmış olmasını gerektirmez. Ancak, bu öğreticideki adımlarda geliştirilen ve IIS 7.5 üzerinde test ve yordamlar diğer sürümleri için değişebilir.


## <a name="install-products-and-components"></a>Ürünler ve bileşenlerini yükleme

Bu bölümde, bileşenleri ve gerekli ürün web sunucusunda yüklenmesinde size kılavuzluk eder. Başlamadan önce iyi sunucunuzun tam olarak güncel olduğundan emin olmak için Windows Update çalıştırmaktır.

Bu durumda, bunları yüklemeniz gerekir:

- **IIS 7 önerilen Yapılandırması**. Böylece **Web sunucusu (IIS)** , web sunucusu rolü ve IIS modüllerini ve bir ASP.NET uygulamasını barındırmak için gereken bileşenleri yükler.
- **.NET framework 4.0**. Bu, .NET Framework'ün bu sürümünde oluşturulmuş uygulamaları çalıştırmak için gereklidir.
- **Web dağıtım aracı 2.1 veya üzeri**. Bu seçenek, Web dağıtımı (ve temel alınan çalıştırılabilir, MSDeploy.exe) sunucunuzda yükler. Bu işlemin bir parçası olarak, yükler ve Web dağıtım aracı hizmetini başlatır. Bu hizmet, web paketlerden uzak bir bilgisayara dağıtmanızı sağlar.
- **ASP.NET MVC 3**. Bu, MVC 3 uygulamaları çalıştırmak için gereken bütünleştirilmiş kodları yükler.

> [!NOTE]
> Bu izlenecek yol gerekli bileşenlerini yükleme ve yapılandırma için Web Platformu yükleyicisi kullanımını açıklar. Web Platformu Yükleyicisi'ni kullanmanız gerekmez ancak otomatik olarak bağımlılıkları algılamasını ve her zaman en son ürün sürümlerini alma sağlayarak yükleme işlemini basitleştirir. Daha fazla bilgi için [Microsoft Web Platformu yükleyicisi 3.0](https://go.microsoft.com/?linkid=9805118).


**Gerekli ürün ve bileşenlerini yüklemek için**

1. İndirme ve yükleme [Web Platformu yükleyicisi](https://go.microsoft.com/?linkid=9805118).
2. Web Platformu yükleyicisi, yükleme tamamlandıktan sonra otomatik olarak başlatılır.

    > [!NOTE]
    > Şimdi Web Platformu yükleyicisi diledikleri zaman başlatabilirsiniz **Başlat** menüsü. Bunu yapmak için **Başlat** menüsünü tıklatın **tüm programlar**ve ardından **Microsoft Web Platformu yükleyicisi**.
3. Üst kısmındaki **Web Platformu yükleyicisi 3.0** penceresinde tıklayın **ürünleri**.
4. Gezinti bölmesinde, pencerenin sol tarafındaki tıklayarak **çerçeveleri**.
5. İçinde **Microsoft .NET Framework 4** .NET Framework zaten yüklü değilse, satırı tıklatın **Ekle**.

    > [!NOTE]
    > Windows Update aracılığıyla .NET Framework 4.0 zaten yüklü olabilir. Bir ürün veya bileşeni zaten yüklüyse, Web Platformu yükleyicisi bu değiştirerek gösterecektir **Ekle** metnini içeren düğmeye **yüklü**.

    ![](configuring-a-web-server-for-web-deploy-publishing-remote-agent/_static/image1.png)
6. İçinde **ASP.NET MVC 3 (Visual Studio 2010)** satır, tıklayın **Ekle**.
7. Gezinti bölmesinde **sunucu**.
8. İçinde **IIS 7 önerilen Yapılandırması** satır, tıklayın **Ekle**.
9. İçinde **Web dağıtım aracı 2.1** satır, tıklayın **Ekle**.
10. **Yükle**'ye tıklatın. Web Platformu yükleyicisi ürünleri &#x2014; herhangi bir ilişkili bağımlılıkları &#x2014; yüklenecek birlikte listesini gösterir ve lisans koşullarını kabul isteyip istemediğinizi sorar.

    ![](configuring-a-web-server-for-web-deploy-publishing-remote-agent/_static/image2.png)
11. Lisans koşullarını gözden geçirin ve koşulları kabul ediyorsa **kabul ediyorum**.
12. Yükleme tamamlandığında, tıklayın **son**ve ardından kapatın **Web Platformu yükleyicisi 3.0** penceresi.

IIS yüklemeden önce .NET Framework 4.0 yüklü değilse, çalıştırmanız gerekir [ASP.NET IIS Kayıt Aracı](https://msdn.microsoft.com/library/k6h9cz8h(v=VS.100).aspx) (aspnet\_regiis.exe) IIS ile ASP.NET en son sürümünü kaydetmek için. Bunu yapmazsanız, herhangi bir sorun IIS (HTML dosyaları gibi) statik içerik sunmak bulabilirsiniz, ancak onu döndürür **HTTP Hatası 404.0 – bulunamadı** çalıştığınızda ASP.NET içeriği gidin. ASP.NET 4.0 kayıtlı olduğundan emin olmak için bu yordamı kullanabilirsiniz.

**ASP.NET 4. 0'ı IIS ile kaydetmeniz için**

1. Tıklayın **Başlat**, Anahtar'a tıklayın ve **komut istemi**.
2. Arama sonuçlarında sağ **komut istemi**ve ardından **yönetici olarak çalıştır**.
3. Komut İstemi penceresinde gidin **%WINDIR%\Microsoft.NET\Framework\v4.0.30319** dizin.
4. Bu komutu yazın ve Enter tuşuna basın:

    [!code-console[Main](configuring-a-web-server-for-web-deploy-publishing-remote-agent/samples/sample1.cmd)]
5. Herhangi bir noktada 64-bit web uygulamalarını barındırmak için planlıyorsanız, ASP.NET 64-bit sürümü de IIS ile kaydetmeniz. Komut İstemi penceresinde bunu yapmak için gidin **%WINDIR%\Microsoft.NET\Framework64\v4.0.30319** dizin.
6. Bu komutu yazın ve Enter tuşuna basın:

    [!code-console[Main](configuring-a-web-server-for-web-deploy-publishing-remote-agent/samples/sample2.cmd)]

İyi bir yöntem olarak, Windows Update yeniden bu noktada yeni ürünler ve yüklediğiniz bileşenler için güncelleştirmeleri karşıdan yüklenip kurulacak kullanın.

## <a name="configure-the-iis-website"></a>IIS Web sitesi yapılandırma

Sunucunuza web içeriği dağıtmadan önce oluşturulup bir IIS Web sitesi içeriğini barındırmak için yapılandırılması gerekir. Web dağıtımı, web paketleri yalnızca var olan bir IIS Web sitesine dağıtabilirsiniz; Bu Web sitesi sizin için oluşturulamıyor. Yüksek düzeyde, bu görevleri tamamlamak gerekir:

- İçeriğinizi barındırmak için dosya sisteminde bir klasör oluşturun.
- İçerik sunmak için bir IIS Web sitesi oluşturma ve yerel klasör ile ilişkilendirebilirsiniz.
- Uygulama havuzu kimliği yerel klasör izinlerini okuma izni ver.

Bu yaklaşım olmasa da nothing IIS'de varsayılan Web sitesine içerik dağıtımını durdurmak, test ya da gösterim senaryoları dışında her şey için önerilmez. Bir üretim ortamının benzetimini yapmak için uygulamanızın gereksinimleri için belirli ayarlarla yeni bir IIS Web sitesi oluşturmanız gerekir.

**Oluşturma ve bir IIS Web sitesi yapılandırma**

1. Yerel dosya sisteminde içeriğinizi depolamak için bir klasör oluşturun (örneğin, **C:\DemoSite**).
2. Üzerinde **Başlat** menüsünde **Yönetimsel Araçlar**ve ardından **Internet Information Services (IIS) Yöneticisi'ni**.
3. IIS Yöneticisi'nde, **bağlantıları** bölmesinde sunucu düğümünü genişletin (örneğin, **TESTWEB1**).

    ![](configuring-a-web-server-for-web-deploy-publishing-remote-agent/_static/image3.png)
4. Sağ **siteleri** düğümünü ve ardından **Web sitesi Ekle**.
5. İçinde **Site adı** IIS Web sitesi için bir ad yazın (örneğin, **DemoSite**).
6. İçinde **fiziksel yolu** kutusuna yazın (veya göz atın), yerel bir klasör yolu (örneğin, **C:\DemoSite**).
7. İçinde **bağlantı noktası** istediğiniz Web sitesini barındırmak bağlantı noktası numarasını yazın (örneğin, **85**).

    > [!NOTE]
    > Standart bağlantı noktası numaralarını, HTTP için 80 ve HTTPS için 443 ' dir. Ancak, bu Web sitesi bağlantı noktası 80 üzerinde barındırıyorsanız, sitenizi erişebilmeniz için önce varsayılan Web sitesini Durdur gerekir.
8. Bırakın **ana bilgisayar adı** kutusunu boş, Web sitesi için bir etki alanı adı sistemi (DNS) kaydı yapılandırın ve ardından istediğiniz sürece **Tamam**.

    ![](configuring-a-web-server-for-web-deploy-publishing-remote-agent/_static/image4.png)

    > [!NOTE]
    > Bir üretim ortamında, büyük olasılıkla, Web sitesi bağlantı noktası 80 üzerinde barındırmak ve DNS kayıtlarını eşleşen birlikte bir konak üstbilgisi yapılandırma isteyeceksiniz. IIS 7'de konak üstbilgileri yapılandırma hakkında daha fazla bilgi için bkz. [bir Web sitesi (IIS 7) için bir konak üstbilgisi yapılandırma](https://technet.microsoft.com/library/cc753195(WS.10).aspx). Windows Server 2008 R2'de DNS sunucusu rolü hakkında daha fazla bilgi için bkz. [DNS sunucusuna genel bakış](https://technet.microsoft.com/en-gb/library/cc770392.aspx) ve [DNS sunucusu](https://technet.microsoft.com/windowsserver/dd448607).
9. **Eylemler** bölmesinde, **Site Düzenle**altında, **Bağlamalar**'ı tıklatın.
10. İçinde **Site bağlamaları** iletişim kutusu, tıklayın **Ekle**.

    ![](configuring-a-web-server-for-web-deploy-publishing-remote-agent/_static/image5.png)
11. İçinde **Site bağlaması Ekle** iletişim kutusu, kümesi **IP adresi** ve **bağlantı noktası** var olan site yapılandırmanızla eşleşecek şekilde.
12. İçinde **ana bilgisayar adı** web sunucunuzun adını yazın (örneğin, **TESTWEB1**) ve ardından **Tamam**.

    ![](configuring-a-web-server-for-web-deploy-publishing-remote-agent/_static/image6.png)

    > [!NOTE]
    > İlk site bağlaması IP adresi ve bağlantı noktasını kullanarak yerel olarak site erişmenize olanak sağlayan veya `http://localhost:85`. Makine adını kullanarak etki alanındaki diğer bilgisayarlardan siteye erişmek ikinci bir site bağlaması sağlar (örneğin, http://testweb1:85).
13. İçinde **Site bağlamaları** iletişim kutusu, tıklayın **Kapat**.
14. İçinde **bağlantıları** bölmesinde tıklayın **uygulama havuzları**.
15. İçinde **uygulama havuzları** bölmesinde, uygulama havuzunuzu adına sağ tıklayın ve ardından **temel ayarları**. Varsayılan olarak, Web sitenizin adı, uygulama havuzunun adı eşleşir (örneğin, **DemoSite**).
16. İçinde **.NET Framework sürümünü** listesinden **.NET Framework v4.0.30319**ve ardından **Tamam**.

    ![](configuring-a-web-server-for-web-deploy-publishing-remote-agent/_static/image7.png)

    > [!NOTE]
    > Örnek çözüm, .NET Framework 4.0 gerektirir. Bu bir gereksinim Web dağıtımı için genel olarak geçerli değildir.

Sırayla içerik sunmak bir Web siteniz için uygulama havuzu kimliği içeriği depolayan bir yerel klasör izinlerini okuma olmalıdır. IIS 7.5 uygulama havuzları (aksine, IIS, burada ağ hizmeti hesabını kullanarak genellikle uygulama havuzlarında çalışır önceki sürümleri için) varsayılan olarak benzersiz bir uygulama havuzu kimliği ile çalıştırın. Uygulama havuzu kimliği gerçek kullanıcı hesabı değil ve tüm kullanıcılar veya gruplar &#x2014 listelerde görünmüyor; uygulama havuzunu başlatıldığında, bunun yerine, bunu dinamik olarak oluşturulur. Her uygulama havuzu kimliği için yerel eklenir **IIS\_IUSRS** gizli öğe olarak güvenlik grubu.

Bir uygulama havuzu kimliği bir dosya veya klasör izinleri vermek için iki seçeneğiniz vardır:

- İzinleri aşağıdaki biçimi kullanarak uygulama havuzu kimliği için doğrudan atayın. <strong>IIS uygulama havuzu\</ strong ><em>[uygulama havuzu adı]</em>(örneğin, <strong>IIS AppPool\DemoSite</strong>).
- Atama izinleri **IIS\_IUSRS** grubu.

Yerel izinler atamak için en yaygın yaklaşımdır **IIS\_IUSRS** bu yaklaşım, dosya sistemi izinleri yapılandırmadan uygulama havuzları değiştirmenize izin verdiğinden grubu. Sonraki yordam, bu grup tabanlı bir yaklaşım kullanır.

> [!NOTE]
> IIS 7.5, uygulama havuzu kimlikleri hakkında daha fazla bilgi için bkz. [uygulama havuzu kimlikleri](https://go.microsoft.com/?linkid=9805123).


**Bir IIS Web sitesi için klasör izinlerini yapılandırmak için**

1. Windows Gezgini'nde yerel klasörünüz konumuna göz atın.
2. Klasörü sağ tıklatın ve ardından **özellikleri**.
3. Üzerinde **güvenlik** sekmesinde **Düzenle**ve ardından **Ekle**.
4. Tıklayın **konumları**. İçinde **konumları** iletişim kutusunda, yerel sunucuyu seçin ve ardından **Tamam**.

    ![](configuring-a-web-server-for-web-deploy-publishing-remote-agent/_static/image8.png)
5. İçinde **kullanıcıları veya Grupları Seç** iletişim kutusuna **IIS\_IUSRS**, tıklayın **Adları Denetle**ve ardından **Tamam**.
6. İçinde <strong>izinlerini</strong><em>[klasör adı]</em>iletişim kutusunda, yeni gruba atanmış olan bildirim <strong>okuma &amp; yürütme</strong>, <strong>klasörü Listele içeriği</strong>, ve <strong>okuma</strong> varsayılan izinleri. Bu değiştirmeden bırakın ve tıklayın <strong>Tamam</strong>.
7. Tıklayın <strong>Tamam</strong> kapatmak için <em>[klasör adı]</em><strong>özellikleri</strong> iletişim kutusu.

Sunucunuza, tüm web paketleri dağıtma girişiminde bulunmadan önce son bir görev olarak Web dağıtım aracı hizmetinin çalıştığından emin emin olmalısınız. Uzak bir bilgisayardan bir paket dağıttığınızda, Web Dağıtım Aracı hizmeti ayıklanması ve paketin içeriği yüklemek için sorumludur. Hizmet, Web dağıtım aracını yüklediğinizde varsayılan olarak başlatılır ve Network SERVICE kimliği altında çalışır.

Çeşitli komut satırı yardımcı programları veya Windows PowerShell cmdlet'lerini kullanarak bir hizmet birden çok farklı şekilde çalışıp çalışmadığını denetleyebilirsiniz. Bu yordam, basit bir kullanıcı Arabirimi tabanlı yaklaşım açıklar.

**Web dağıtım aracı hizmetinin çalışıp çalışmadığını denetlemek için**

1. **Başlat** menüsünde, **Yönetim Araçları**'na gelin ve ardından **Hizmetler**'e tıklayın.
2. Bulun **Web Dağıtım Aracı hizmeti** satır ve doğrulayın **durumu** ayarlanır **başlatıldı**.

    ![](configuring-a-web-server-for-web-deploy-publishing-remote-agent/_static/image9.png)
3. Hizmeti zaten başlamamışsa tıklayın **Başlat**.

## <a name="configure-firewall-exceptions"></a>Güvenlik Duvarı özel durumlarını yapılandırma

Varsayılan olarak, Uzak Aracı hizmeti TCP bağlantı noktası 80 şu URL dinler:

<http://servername.com/MSDEPLOYAGENTSERVICE>

Çoğu durumda, web sunucuları genellikle bağlantı noktası 80 üzerinde HTTP isteklerini dinlemek için uzaktan Aracı hizmeti için herhangi bir ek güvenlik duvarı kuralları yapılandırma gerekmez. Standart olmayan bir bağlantı noktasında dinleyecek şekilde yüklemenizi özelleştirdiyseniz, gerektiği gibi configure firewall exceptions gerekecektir.

## <a name="conclusion"></a>Sonuç

Bu noktada, web sunucunuza kabul etmek ve uzak bir bilgisayardan web paketleri yüklemek hazırdır. Sunucuya bir web uygulaması dağıtma girişiminde bulunmadan önce aşağıdaki önemli noktalara denetlemek isteyebilirsiniz:

- IIS ile ASP.NET 4.0 kaydolduğundan?
- Uygulama havuzu kimliği, Web siteniz için kaynak klasöre okuma erişimi yok?
- Web Dağıtım Aracı hizmeti çalışıyor mu?

## <a name="further-reading"></a>Daha Fazla Bilgi

Web paketleri ve Uzak Aracı hizmeti dağıtmak için özel Microsoft Build Engine (MSBuild) proje dosyalarının nasıl yapılandırılacağı hakkında yönergeler için bkz. [bir hedef ortam için dağıtım özellikleri yapılandırma](configuring-deployment-properties-for-a-target-environment.md).

> [!div class="step-by-step"]
> [Önceki](scenario-configuring-a-production-environment-for-web-deployment.md)
> [İleri](configuring-a-web-server-for-web-deploy-publishing-web-deploy-handler.md)
