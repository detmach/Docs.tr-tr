---
uid: web-forms/overview/ajax-control-toolkit/getting-started/get-started-with-the-ajax-control-toolkit-vb
title: AJAX Denetim Araç Seti ile (VB) kullanmaya başlayın | Microsoft Docs
author: microsoft
description: AJAX Denetim Araç Seti ile çalışmaya başlamak için bilmeniz gereken her şeyi öğrenin.
ms.author: riande
ms.date: 05/12/2009
ms.assetid: 9f8fa166-49a2-402c-b236-20caef0c658f
msc.legacyurl: /web-forms/overview/ajax-control-toolkit/getting-started/get-started-with-the-ajax-control-toolkit-vb
msc.type: authoredcontent
ms.openlocfilehash: bbf90d65a0be0eeb4150609aca9cf192f516abf3
ms.sourcegitcommit: 45ac74e400f9f2b7dbded66297730f6f14a4eb25
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/16/2018
ms.locfileid: "41757265"
---
<a name="get-started-with-the-ajax-control-toolkit-vb"></a>AJAX Denetim Araç Seti ile (VB) kullanmaya başlayın
====================
tarafından [Microsoft](https://github.com/microsoft)

> AJAX Denetim Araç Seti ile çalışmaya başlamak için bilmeniz gereken her şeyi öğrenin.


AJAX Denetim Araç Seti, ASP.NET uygulamalarınızda kullanabileceğiniz 30'dan fazla ücretsiz denetimleri içerir. Bu öğreticide, AJAX Denetim Araç Seti indirme ve araç seti denetimlerini, Visual Studio/Visual Web Developer Express araç kutusuna ekleme hakkında bilgi edinin.

## <a name="downloading-the-ajax-control-toolkit"></a>AJAX Denetim Araç Seti yükleniyor

[AJAX Denetim Araç Seti](http://devexpress.com/act) ASP.NET topluluğu ve ASP.NET takım üyeleri tarafından geliştirilen bir açık kaynak projesi.


[![AJAX Denetim Araç Seti yükleniyor](get-started-with-the-ajax-control-toolkit-vb/_static/image1.jpg)](get-started-with-the-ajax-control-toolkit-vb/_static/image1.png)

**Şekil 01**: AJAX Denetim Araç Seti indiriliyor ([tam boyutlu görüntüyü görmek için tıklatın](get-started-with-the-ajax-control-toolkit-vb/_static/image2.png))


Dosyayı indirdikten sonra dosyayı engelini kaldırmak gerekir. Dosyaya sağ tıklayın, Özellikler'i seçin ve tıklayın **Engellemeyi Kaldır** (bkz: Şekil 2) düğmesi.


[![AJAX Denetim Araç Seti ZIP dosyası kaldırma](get-started-with-the-ajax-control-toolkit-vb/_static/image2.jpg)](get-started-with-the-ajax-control-toolkit-vb/_static/image3.png)

**Şekil 02**: AJAX Denetim Araç Seti ZIP dosyası kaldırma ([tam boyutlu görüntüyü görmek için tıklatın](get-started-with-the-ajax-control-toolkit-vb/_static/image4.png))


Dosya engelini kaldırdıktan sonra dosyayı sıkıştırılmış dosyayı açabilirsiniz: dosyaya sağ tıklayıp **tümünü Ayıkla** menü seçeneği. Şimdi, araç seti Visual Studio/Visual Web Developer araç kutusuna ekleme hazırız.

## <a name="adding-the-ajax-control-toolkit-to-the-toolbox"></a>AJAX Denetim Araç Seti araç kutusuna ekleme

AJAX Denetim Araç Seti kullanmanın en kolay yolu, Visual Studio/Visual Web Developer araç için araç seti eklemektir (bkz: Şekil 3). Bunu kullanmak istediğinizde bu şekilde, yalnızca bir araç seti denetim bir sayfaya sürükleyebilirsiniz.


[![AJAX Denetim Araç Seti araç kutusunda görünür.](get-started-with-the-ajax-control-toolkit-vb/_static/image3.jpg)](get-started-with-the-ajax-control-toolkit-vb/_static/image5.png)

**Şekil 03**: AJAX Denetim Araç Seti araç kutusunda görünür ([tam boyutlu görüntüyü görmek için tıklatın](get-started-with-the-ajax-control-toolkit-vb/_static/image6.png))


İlk olarak, bir AJAX Denetim Araç Seti sekmesi, araç kutusuna ekleme gerekir. Bu adımları izleyin.

1. Dosya, yeni Web sitesi menü seçeneğini seçerek yeni bir ASP.NET Web sitesi oluşturun. Çözüm Gezgini penceresinde Default.aspx Düzenleyicisi'nde dosyayı açmak için çift tıklayın.
2. Genel sekmesi altında araç kutusunu sağ tıklatın ve menü seçeneğini **Sekme Ekle** (bkz: Şekil 4).
3. AJAX Denetim Araç Seti adlı yeni bir sekme girin.


[![Yeni bir sekme ekleme](get-started-with-the-ajax-control-toolkit-vb/_static/image4.jpg)](get-started-with-the-ajax-control-toolkit-vb/_static/image7.png)

**Şekil 04**: yeni bir sekme ekleme ([tam boyutlu görüntüyü görmek için tıklatın](get-started-with-the-ajax-control-toolkit-vb/_static/image8.png))


Ardından, yeni bir sekmeye AJAX Denetim Araç Seti denetim eklemek gerekir. Aşağıdaki adımları uygulayın:

- AJAX Denetim Araç Seti sekmesi sağ tıklayın ve menü seçeneğini **seçin (bkz: Şekil 5) öğeleri**.
- Burada AJAX Denetim Araç Seti sıkıştırması açılan ve AjaxControlToolkit.dll derlemeyi seçin konumuna göz atın.


[![Araç kutusuna eklenecek öğeleri seçin](get-started-with-the-ajax-control-toolkit-vb/_static/image5.jpg)](get-started-with-the-ajax-control-toolkit-vb/_static/image9.png)

**Şekil 05**: araç kutusuna eklenecek öğeleri seçin ([tam boyutlu görüntüyü görmek için tıklatın](get-started-with-the-ajax-control-toolkit-vb/_static/image10.png))


Bu adımları tamamladıktan sonra tüm araç seti denetimlerini, araç kutusunda görünür.

## <a name="upgrading-to-a-new-version-of-the-toolkit"></a>Araç Seti yeni bir sürüme yükseltme

Araç Seti eski bir sürümünü kullanıyor ve taşımak artık gereksinim burada sonraki bir sürümü önerilen adımlar şunlardır:

- İkili - AjaxControlToolkit.dll derlemenin eski sürümü, Web sitesi Bin klasöründen silin.
- Araç kutusu öğeleri - AJAX Denetim Araç Seti sekmesini silme ve AjaxControlToolkit.dll derlemenin yeni sürümünü içeren sekmeye yeniden oluşturmak için yukarıdaki adımları izleyin.

> [!div class="step-by-step"]
> [Önceki](creating-a-custom-ajax-control-toolkit-control-extender-cs.md)
> [İleri](using-ajax-control-toolkit-controls-and-control-extenders-vb.md)
