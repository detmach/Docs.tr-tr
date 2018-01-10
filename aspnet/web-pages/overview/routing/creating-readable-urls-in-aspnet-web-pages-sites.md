---
uid: web-pages/overview/routing/creating-readable-urls-in-aspnet-web-pages-sites
title: "Okunabilir URL'ler oluşturma ASP.NET Web sayfaları (Razor) siteleri | Microsoft Docs"
author: tfitzmac
description: "Bu makalede, bir ASP.NET Web sayfaları (Razor) Web sitesi ve nasıl bu daha okunabilir ve SEO için daha iyi URL'leri kullanmanıza olanak sağlayan yönlendirme açıklanmaktadır. Ne artıracaksınız..."
ms.author: aspnetcontent
manager: wpickett
ms.date: 02/17/2014
ms.topic: article
ms.assetid: a8aac1ac-89de-4415-afe0-97a41c6423d2
ms.technology: dotnet-webpages
ms.prod: .net-framework
msc.legacyurl: /web-pages/overview/routing/creating-readable-urls-in-aspnet-web-pages-sites
msc.type: authoredcontent
ms.openlocfilehash: 7858b7cbd6dccafb2867ed9a1d102561e211e435
ms.sourcegitcommit: 9a9483aceb34591c97451997036a9120c3fe2baf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/10/2017
---
<a name="creating-readable-urls-in-aspnet-web-pages-razor-sites"></a><span data-ttu-id="10b64-104">ASP.NET Web sayfaları (Razor) sitelerinde okunabilir URL'ler oluşturma</span><span class="sxs-lookup"><span data-stu-id="10b64-104">Creating Readable URLs in ASP.NET Web Pages (Razor) Sites</span></span>
====================
<span data-ttu-id="10b64-105">tarafından [zel FitzMacken](https://github.com/tfitzmac)</span><span class="sxs-lookup"><span data-stu-id="10b64-105">by [Tom FitzMacken](https://github.com/tfitzmac)</span></span>

> <span data-ttu-id="10b64-106">Bu makalede, bir ASP.NET Web sayfaları (Razor) Web sitesi ve nasıl bu daha okunabilir ve SEO için daha iyi URL'leri kullanmanıza olanak sağlayan yönlendirme açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="10b64-106">This article describes routing in an ASP.NET Web Pages (Razor) website, and how this lets you use URLs that are more readable and better for SEO.</span></span>
> 
> <span data-ttu-id="10b64-107">Öğrenecekleriniz:</span><span class="sxs-lookup"><span data-stu-id="10b64-107">What you'll learn:</span></span>
> 
> - <span data-ttu-id="10b64-108">Nasıl ASP.NET yönlendirme daha okunabilir ve aranabilir URL'lere kullanmanıza izin vermek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="10b64-108">How ASP.NET uses routing to let you use more readable and searchable URLs.</span></span>
>   
> 
> ## <a name="software-versions-used-in-the-tutorial"></a><span data-ttu-id="10b64-109">Öğreticide kullanılan yazılım sürümleri</span><span class="sxs-lookup"><span data-stu-id="10b64-109">Software versions used in the tutorial</span></span>
> 
> 
> - <span data-ttu-id="10b64-110">ASP.NET Web sayfaları (Razor) 3</span><span class="sxs-lookup"><span data-stu-id="10b64-110">ASP.NET Web Pages (Razor) 3</span></span>
>   
> 
> <span data-ttu-id="10b64-111">Bu öğreticide, ASP.NET Web Pages 2 ile de çalışır.</span><span class="sxs-lookup"><span data-stu-id="10b64-111">This tutorial also works with ASP.NET Web Pages 2.</span></span>


## <a name="about-routing"></a><span data-ttu-id="10b64-112">Yönlendirme hakkında</span><span class="sxs-lookup"><span data-stu-id="10b64-112">About Routing</span></span>

<span data-ttu-id="10b64-113">Sitenizdeki sayfalar için URL'leri site ne kadar iyi çalıştığı bir etkisi olabilir.</span><span class="sxs-lookup"><span data-stu-id="10b64-113">The URLs for the pages in your site can have an impact on how well the site works.</span></span> <span data-ttu-id="10b64-114">Bir URL bu &quot;kolay&quot; sitesini kullanmak üzere kişiler için daha kolay hale getirebilir.</span><span class="sxs-lookup"><span data-stu-id="10b64-114">A URL that's &quot;friendly&quot; can make it easier for people to use the site.</span></span> <span data-ttu-id="10b64-115">Site için arama motoru iyileştirme (SEO) de yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="10b64-115">It can also help with search-engine optimization (SEO) for the site.</span></span> <span data-ttu-id="10b64-116">ASP.NET Web siteleri kolay URL'leri otomatik olarak kullanma yeteneğini içerir.</span><span class="sxs-lookup"><span data-stu-id="10b64-116">ASP.NET websites include the ability to use friendly URLs automatically.</span></span>

<span data-ttu-id="10b64-117">ASP.NET, yalnızca sunucu üzerindeki bir dosyaya işaret eden yerine kullanıcı eylemleri açıklayan anlamlı URL'leri oluşturmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="10b64-117">ASP.NET lets you create meaningful URLs that describe user actions instead of just pointing to a file on the server.</span></span> <span data-ttu-id="10b64-118">Bu URL'ler için kurgusal bir blog göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="10b64-118">Consider these URLs for a fictional blog:</span></span>

- `http://www.contoso.com/Blog/blog.cshtml?categories=hardware`
- `http://www.contoso.com//Blog/blog.cshtml?startdate=2009-11-01&enddate=2009-11-30`

<span data-ttu-id="10b64-119">Bu URL'leri aşağıdaki olanlara karşılaştırın:</span><span class="sxs-lookup"><span data-stu-id="10b64-119">Compare those URLs to the following ones:</span></span>

- `http://www.contoso.com/Blog/categories/hardware/`
- `http://www.contoso.com/Blog/2009/November`

<span data-ttu-id="10b64-120">İlk çiftinin bir kullanıcı blog kullanılarak görüntülenir bilmesi gerekir *blog.cshtml* sayfasında ve sağ kategori veya tarih aralığı alır bir sorgu dizesi oluşturmak sahip.</span><span class="sxs-lookup"><span data-stu-id="10b64-120">In the first pair, a user would have to know that the blog is displayed using the *blog.cshtml* page, and would then have to construct a query string that gets the right category or date range.</span></span> <span data-ttu-id="10b64-121">Örnekler ikinci kümesi kavrama ve oluşturmak çok daha kolaydır.</span><span class="sxs-lookup"><span data-stu-id="10b64-121">The second set of examples is much easier to comprehend and create.</span></span>

<span data-ttu-id="10b64-122">İlk örnek için URL'leri de doğrudan belirli bir dosyaya işaret (*blog.cshtml*).</span><span class="sxs-lookup"><span data-stu-id="10b64-122">The URLs for the first example also point directly to a specific file (*blog.cshtml*).</span></span> <span data-ttu-id="10b64-123">Herhangi bir nedenden dolayı sunucu üzerinde başka bir klasöre blog taşınan veya blog başka bir sayfaya kullanacak şekilde yeniden yazılmıştır, bağlantıları yanlış olabilir.</span><span class="sxs-lookup"><span data-stu-id="10b64-123">If for some reason the blog were moved to another folder on the server, or if the blog were rewritten to use a different page, the links would be wrong.</span></span> <span data-ttu-id="10b64-124">Belirli bir sayfaya URL'leri ikinci kümesi gösteremiyor da blog uygulama veya konumu değişirse, URL'leri hala geçerli olacaktır.</span><span class="sxs-lookup"><span data-stu-id="10b64-124">The second set of URLs doesn't point to a specific page, so even if the blog implementation or location changes, the URLs would still be valid.</span></span>

<span data-ttu-id="10b64-125">ASP.NET Web sayfaları, ASP.NET kullandığından Yukarıdaki örneklerde gelenler yaşamanızı URL'leri oluşturabilirsiniz *yönlendirme*.</span><span class="sxs-lookup"><span data-stu-id="10b64-125">In ASP.NET Web Pages, you can create friendlier URLs like those in the above examples because ASP.NET uses *routing*.</span></span> <span data-ttu-id="10b64-126">Yönlendirme mantıksal eşleme isteği gerçekleştirmek bir URL'den bir sayfa (veya sayfaları) oluşturur.</span><span class="sxs-lookup"><span data-stu-id="10b64-126">Routing creates logical mapping from a URL to a page (or pages) that can fulfill the request.</span></span> <span data-ttu-id="10b64-127">Eşleme mantıksal olduğundan (fiziksel, belirli bir dosya için), yönlendirme URL'leri siteniz için nasıl tanımladığınız büyük esneklik sağlar.</span><span class="sxs-lookup"><span data-stu-id="10b64-127">Because the mapping is logical (not physical, to a specific file), routing provides great flexibility in how you define the URLs for your site.</span></span>

## <a name="how-routing-works"></a><span data-ttu-id="10b64-128">Yönlendirmenin nasıl çalışır</span><span class="sxs-lookup"><span data-stu-id="10b64-128">How Routing Works</span></span>

<span data-ttu-id="10b64-129">ASP.NET bir isteği işlerken yönlendirmek nasıl belirlemek için URL'yi okur.</span><span class="sxs-lookup"><span data-stu-id="10b64-129">When ASP.NET processes a request, it reads the URL to determine how to route it.</span></span> <span data-ttu-id="10b64-130">ASP.NET, diskte dosyalar soldan sağa giderek URL'sini tek tek parçaları eşleştirmeyi dener.</span><span class="sxs-lookup"><span data-stu-id="10b64-130">ASP.NET tries to match individual segments of the URL to files on disk, going from left to right.</span></span> <span data-ttu-id="10b64-131">Bir eşleşme varsa, URL'de kalan her şey için sayfa olarak geçirilen *yol bilgisi*.</span><span class="sxs-lookup"><span data-stu-id="10b64-131">If there's a match, anything remaining in the URL is passed to the page as *path information*.</span></span>

<span data-ttu-id="10b64-132">Birisi bu URL'yi kullanarak bir isteği yapar düşünün:</span><span class="sxs-lookup"><span data-stu-id="10b64-132">Imagine that someone makes a request using this URL:</span></span>

`http://www.contoso.com/a/b/c`

<span data-ttu-id="10b64-133">Arama şöyle geçer:</span><span class="sxs-lookup"><span data-stu-id="10b64-133">The search goes like this:</span></span>

1. <span data-ttu-id="10b64-134">Bir dosya yolu ve adı yok */a/b/c.cshtml*?</span><span class="sxs-lookup"><span data-stu-id="10b64-134">Is there a file with the path and name of */a/b/c.cshtml*?</span></span> <span data-ttu-id="10b64-135">Öyleyse, bu sayfayı çalıştırın ve hiçbir bilgi ona geçirin.</span><span class="sxs-lookup"><span data-stu-id="10b64-135">If so, run that page and pass no information to it.</span></span> <span data-ttu-id="10b64-136">Aksi takdirde...</span><span class="sxs-lookup"><span data-stu-id="10b64-136">Otherwise ...</span></span>
2. <span data-ttu-id="10b64-137">Bir dosya yolu ve adı yok */a/b.cshtml*?</span><span class="sxs-lookup"><span data-stu-id="10b64-137">Is there a file with the path and name of */a/b.cshtml*?</span></span> <span data-ttu-id="10b64-138">Bu nedenle, bu sayfayı çalıştırın ve değerini geçirin `c` ona.</span><span class="sxs-lookup"><span data-stu-id="10b64-138">If so, run that page and pass the value `c` to it.</span></span> <span data-ttu-id="10b64-139">Aksi takdirde...</span><span class="sxs-lookup"><span data-stu-id="10b64-139">Otherwise …</span></span>
3. <span data-ttu-id="10b64-140">Bir dosya yolu ve adı yok */a.cshtml*?</span><span class="sxs-lookup"><span data-stu-id="10b64-140">Is there a file with the path and name of */a.cshtml*?</span></span> <span data-ttu-id="10b64-141">Bu nedenle, bu sayfayı çalıştırın ve değerini geçirin `b/c` ona.</span><span class="sxs-lookup"><span data-stu-id="10b64-141">If so, run that page and pass the value `b/c` to it.</span></span>

<span data-ttu-id="10b64-142">Hayır tam arama için eşleşiyorsa *.cshtml* belirtilen klasörlerine dosyalarında, ASP.NET devam bu dosyalar sırayla aranıyor:</span><span class="sxs-lookup"><span data-stu-id="10b64-142">If the search found no exact matches for *.cshtml* files in their specified folders, ASP.NET continues looking for these files in turn:</span></span>

1. <span data-ttu-id="10b64-143">*/a/b/c/default.cshtml* (yol bilgisi yok).</span><span class="sxs-lookup"><span data-stu-id="10b64-143">*/a/b/c/default.cshtml* (no path information).</span></span>
2. <span data-ttu-id="10b64-144">*/a/b/c/index.cshtml* (yol bilgisi yok).</span><span class="sxs-lookup"><span data-stu-id="10b64-144">*/a/b/c/index.cshtml* (no path information).</span></span>

> [!NOTE]
> <span data-ttu-id="10b64-145">Açık olması açısından belirli sayfaları için istekleri (diğer bir deyişle, içeren isteklerin *.cshtml* dosya adı uzantısı) yalnızca beklediğiniz gibi çalışır.</span><span class="sxs-lookup"><span data-stu-id="10b64-145">To be clear, requests for specific pages (that is, requests that include the *.cshtml* filename extension) work just like you'd expect.</span></span> <span data-ttu-id="10b64-146">Bir istek ister `http://www.contoso.com/a/b.cshtml` sayfasının çalışacağı *b.cshtml* yalnızca iyi.</span><span class="sxs-lookup"><span data-stu-id="10b64-146">A request like `http://www.contoso.com/a/b.cshtml` will run the page *b.cshtml* just fine.</span></span>


<span data-ttu-id="10b64-147">İçinde bir sayfa, sayfanın yolu bilgisini elde edebilirsiniz `UrlData` bir sözlük özelliği.</span><span class="sxs-lookup"><span data-stu-id="10b64-147">Inside a page, you can get the path information via the page's `UrlData` property, which is a dictionary.</span></span> <span data-ttu-id="10b64-148">Adlı bir dosya olduğunu düşünün *ViewCustomers.cshtml* ve bu istek, sitenizi alır:</span><span class="sxs-lookup"><span data-stu-id="10b64-148">Imagine that you have a file named *ViewCustomers.cshtml* and your site gets this request:</span></span>

`http://mysite.com/myWebSite/ViewCustomers/1000`

<span data-ttu-id="10b64-149">Yukarıdaki kurallara açıklandığı gibi istek sayfanıza gidin.</span><span class="sxs-lookup"><span data-stu-id="10b64-149">As described in the rules above, the request will go to your page.</span></span> <span data-ttu-id="10b64-150">Sayfanın içinde aşağıdaki gibi bir kod almak ve yol bilgileri görüntülemek için kullanabilirsiniz (Bu durumda, değer &quot;1000&quot;):</span><span class="sxs-lookup"><span data-stu-id="10b64-150">Inside the page, you can use code like the following to get and display the path information (in this case, the value &quot;1000&quot;):</span></span>

[!code-html[Main](creating-readable-urls-in-aspnet-web-pages-sites/samples/sample1.html)]

> [!NOTE]
> <span data-ttu-id="10b64-151">Yönlendirme tam dosya adlarının içermeyen çünkü olabilir belirsizlik aynı olan sayfaları varsa ad ancak farklı dosya adı uzantıları (örneğin, *MyPage.cshtml* ve *MyPage.html*) .</span><span class="sxs-lookup"><span data-stu-id="10b64-151">Because routing doesn't involve complete file names, there can be ambiguity if you have pages that have the same name but different file-name extensions (for example, *MyPage.cshtml* and *MyPage.html*).</span></span> <span data-ttu-id="10b64-152">Yönlendirme sorunlarını önlemek için bunların uzantısı yalnızca, adları farklı sitenizdeki sayfaları yok emin olmak en iyisidir.</span><span class="sxs-lookup"><span data-stu-id="10b64-152">In order to avoid problems with routing, it's best to make sure that you don't have pages in your site whose names differ only in their extension.</span></span>


<a id="Additional_Resources"></a>
## <a name="additional-resources"></a><span data-ttu-id="10b64-153">Ek Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="10b64-153">Additional Resources</span></span>

<span data-ttu-id="10b64-154">[WebMatrix - URL'leri, UrlData ve SEO için yönlendirme](http://www.mikesdotnetting.com/Article/165/WebMatrix-URLs-UrlData-and-Routing-for-SEO).</span><span class="sxs-lookup"><span data-stu-id="10b64-154">[WebMatrix - URLs, UrlData and Routing for SEO](http://www.mikesdotnetting.com/Article/165/WebMatrix-URLs-UrlData-and-Routing-for-SEO).</span></span> <span data-ttu-id="10b64-155">Bu blog girişi CAN Brind tarafından yönlendirmenin nasıl çalıştığını ASP.NET Web Pages'de bazı ek ayrıntılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="10b64-155">This blog entry by Mike Brind provides some additional details on how routing works in ASP.NET Web Pages.</span></span>