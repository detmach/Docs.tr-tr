---
uid: web-forms/overview/ajax-control-toolkit/dynamicpopulate/using-dynamicpopulate-with-a-user-control-and-javascript-cs
title: "Bir kullanıcı denetimi ve JavaScript (C#) ile DynamicPopulate kullanarak | Microsoft Docs"
author: wenz
description: "ASP.NET AJAX Denetim Araç Seti DynamicPopulate denetiminde bir web hizmeti (veya sayfa yöntemi) çağırır ve sonuçta elde edilen değerin t hedef denetime doldurur..."
ms.author: aspnetcontent
manager: wpickett
ms.date: 06/02/2008
ms.topic: article
ms.assetid: 38ac8250-8854-444c-b9ab-8998faa41c5a
ms.technology: dotnet-webforms
ms.prod: .net-framework
msc.legacyurl: /web-forms/overview/ajax-control-toolkit/dynamicpopulate/using-dynamicpopulate-with-a-user-control-and-javascript-cs
msc.type: authoredcontent
ms.openlocfilehash: 3f78da3898d44cc2cf1db6623ebcaf6a73ebbf3e
ms.sourcegitcommit: 9a9483aceb34591c97451997036a9120c3fe2baf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/10/2017
---
<a name="using-dynamicpopulate-with-a-user-control-and-javascript-c"></a><span data-ttu-id="b9b70-103">DynamicPopulate kullanarak bir kullanıcı denetimi ve JavaScript (C#)</span><span class="sxs-lookup"><span data-stu-id="b9b70-103">Using DynamicPopulate with a User Control And JavaScript (C#)</span></span>
====================
<span data-ttu-id="b9b70-104">tarafından [Christian Wenz](https://github.com/wenz)</span><span class="sxs-lookup"><span data-stu-id="b9b70-104">by [Christian Wenz](https://github.com/wenz)</span></span>

<span data-ttu-id="b9b70-105">[Kodu indirme](http://download.microsoft.com/download/d/8/f/d8f2f6f9-1b7c-46ad-9252-e1fc81bdea3e/dynamicpopulate2.cs.zip) veya [PDF indirin](http://download.microsoft.com/download/b/6/a/b6ae89ee-df69-4c87-9bfb-ad1eb2b23373/dynamicpopulate2CS.pdf)</span><span class="sxs-lookup"><span data-stu-id="b9b70-105">[Download Code](http://download.microsoft.com/download/d/8/f/d8f2f6f9-1b7c-46ad-9252-e1fc81bdea3e/dynamicpopulate2.cs.zip) or [Download PDF](http://download.microsoft.com/download/b/6/a/b6ae89ee-df69-4c87-9bfb-ad1eb2b23373/dynamicpopulate2CS.pdf)</span></span>

> <span data-ttu-id="b9b70-106">ASP.NET AJAX Denetim Araç Seti DynamicPopulate denetiminde bir web hizmeti (veya sayfa yöntemi) çağırır ve çıkan değeri bir sayfa yenileme olmadan sayfasında hedef denetime doldurur.</span><span class="sxs-lookup"><span data-stu-id="b9b70-106">The DynamicPopulate control in the ASP.NET AJAX Control Toolkit calls a web service (or page method) and fills the resulting value into a target control on the page, without a page refresh.</span></span> <span data-ttu-id="b9b70-107">Özel istemci tarafı JavaScript kodu kullanarak popülasyon tetiklemek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="b9b70-107">It is also possible to trigger the population using custom client-side JavaScript code.</span></span> <span data-ttu-id="b9b70-108">Ancak, bir kullanıcı denetimi genişletici bulunduğu olduğunda gerçekleştirilecek özellikle dikkat edilmelidir.</span><span class="sxs-lookup"><span data-stu-id="b9b70-108">However special care has to be taken when the extender resides in a user control.</span></span>


## <a name="overview"></a><span data-ttu-id="b9b70-109">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b9b70-109">Overview</span></span>

<span data-ttu-id="b9b70-110">`DynamicPopulate` ASP.NET AJAX Denetim Araç Seti denetiminde bir web hizmeti (veya sayfa yöntemi) çağırır ve sayfa yenileme olmadan sayfasında hedef denetime sonuç değeri doldurur.</span><span class="sxs-lookup"><span data-stu-id="b9b70-110">The `DynamicPopulate` control in the ASP.NET AJAX Control Toolkit calls a web service (or page method) and fills the resulting value into a target control on the page, without a page refresh.</span></span> <span data-ttu-id="b9b70-111">Özel istemci tarafı JavaScript kodu kullanarak popülasyon tetiklemek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="b9b70-111">It is also possible to trigger the population using custom client-side JavaScript code.</span></span> <span data-ttu-id="b9b70-112">Ancak, bir kullanıcı denetimi genişletici bulunduğu olduğunda gerçekleştirilecek özellikle dikkat edilmelidir.</span><span class="sxs-lookup"><span data-stu-id="b9b70-112">However special care has to be taken when the extender resides in a user control.</span></span>

## <a name="steps"></a><span data-ttu-id="b9b70-113">Adımlar</span><span class="sxs-lookup"><span data-stu-id="b9b70-113">Steps</span></span>

<span data-ttu-id="b9b70-114">Öncelikle, ASP.NET Web hizmeti çağrılacak yöntemin uygulayan gereksinim `DynamicPopulateExtender` denetim.</span><span class="sxs-lookup"><span data-stu-id="b9b70-114">First of all, you need an ASP.NET Web Service which implements the method to be called by the `DynamicPopulateExtender` control.</span></span> <span data-ttu-id="b9b70-115">Web hizmeti yöntemi uygulayan `getDate()` adlı dize türünde bir bağımsız değişken bekler `contextKey`, bu yana `DynamicPopulate` denetim bağlam bilgilerini bir parçasını her web hizmeti çağrısı ile gönderir.</span><span class="sxs-lookup"><span data-stu-id="b9b70-115">The web service implements the method `getDate()` that expects one argument of type string, called `contextKey`, since the `DynamicPopulate` control sends one piece of context information with each web service call.</span></span> <span data-ttu-id="b9b70-116">Kod aşağıdaki gibidir (dosya `DynamicPopulate.cs.asmx`) üç biçimlerden birinde geçerli tarihi alır:</span><span class="sxs-lookup"><span data-stu-id="b9b70-116">Here is the code (file `DynamicPopulate.cs.asmx`) which retrieves the current date in one of three formats:</span></span>

[!code-aspx[Main](using-dynamicpopulate-with-a-user-control-and-javascript-cs/samples/sample1.aspx)]

<span data-ttu-id="b9b70-117">Sonraki adımda, yeni bir kullanıcı denetimi oluşturma (`.ascx` dosyası), ilk satırı aşağıdaki bildiriminde tarafından başlar:</span><span class="sxs-lookup"><span data-stu-id="b9b70-117">In the next step, create a new user control (`.ascx` file), denoted by the following declaration in its first line:</span></span>

[!code-aspx[Main](using-dynamicpopulate-with-a-user-control-and-javascript-cs/samples/sample2.aspx)]

<span data-ttu-id="b9b70-118">A &lt; `label` &gt; öğesi, sunucudan gelen verileri görüntülemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b9b70-118">A &lt;`label`&gt; element will be used to display the data coming from the server.</span></span>

[!code-aspx[Main](using-dynamicpopulate-with-a-user-control-and-javascript-cs/samples/sample3.aspx)]

<span data-ttu-id="b9b70-119">Ayrıca kullanıcı denetimi dosyasında kullanacağız üç radyo düğmeleri, web hizmeti tarafından desteklenen üç olası tarih biçimlerinden birini temsil eden her biri.</span><span class="sxs-lookup"><span data-stu-id="b9b70-119">Also in the user control file, we will use three radio buttons, each one representing one of the three possible date formats supported by the web service.</span></span> <span data-ttu-id="b9b70-120">Kullanıcı radyo düğmeleri birinde tıkladığında tarayıcı şöyle JavaScript kodunu yürütün:</span><span class="sxs-lookup"><span data-stu-id="b9b70-120">When the user clicks on one of the radio buttons, the browser will execute JavaScript code which looks like this:</span></span>

[!code-powershell[Main](using-dynamicpopulate-with-a-user-control-and-javascript-cs/samples/sample4.ps1)]

<span data-ttu-id="b9b70-121">Bu kod erişen `DynamicPopulateExtender` (garip kimliği hakkında endişe etmeyin henüz, bunu daha sonra ele alınacaktır) ve verilerle dinamik popülasyon tetikler.</span><span class="sxs-lookup"><span data-stu-id="b9b70-121">This code accesses the `DynamicPopulateExtender` (do not worry about the strange ID yet, this will be covered later on) and triggers the dynamic population with data.</span></span> <span data-ttu-id="b9b70-122">Geçerli radyo düğmesi bağlamında `this.value` olan değerine başvuruyor `format1`, `format2` veya `format3` tam olarak hangi web yöntemi bekliyor.</span><span class="sxs-lookup"><span data-stu-id="b9b70-122">In the context of the current radio button, `this.value` refers to its value which is `format1`, `format2` or `format3` exactly what the web method expects.</span></span>

<span data-ttu-id="b9b70-123">Kullanıcı denetimi henüz eksik tek şey `DynamicPopulateExtender` radyo düğmeleri web hizmetine bağlayan denetim.</span><span class="sxs-lookup"><span data-stu-id="b9b70-123">The only thing missing in the user control yet is the `DynamicPopulateExtender` control which links the radio buttons to the web service.</span></span>

[!code-aspx[Main](using-dynamicpopulate-with-a-user-control-and-javascript-cs/samples/sample5.aspx)]

<span data-ttu-id="b9b70-124">Yeniden denetiminde kullanılan garip Kimliğini Not: `mcd1$myDate` yerine `myDate`.</span><span class="sxs-lookup"><span data-stu-id="b9b70-124">Again you may note the strange ID used in the control: `mcd1$myDate` instead of `myDate`.</span></span> <span data-ttu-id="b9b70-125">Daha önce kullanılan JavaScript kodu `mcd1_dpe1` erişimi `DynamicPopulateExtender` yerine `dpe1`. Bu adlandırma stratejisi özel gereksinim kullanıldığında `DynamicPopulateExtender` bir kullanıcı denetimi içinde.</span><span class="sxs-lookup"><span data-stu-id="b9b70-125">Previously, the JavaScript code used `mcd1_dpe1` to access the `DynamicPopulateExtender` instead of `dpe1`.This naming strategy is a special requirement when using `DynamicPopulateExtender` within a user control.</span></span> <span data-ttu-id="b9b70-126">Ayrıca, tüm çalışması için özel bir biçimde kullanıcı öne katıştırmak vardır.</span><span class="sxs-lookup"><span data-stu-id="b9b70-126">Furthermore, you have to embed the user contol in a specific way to make it all work.</span></span> <span data-ttu-id="b9b70-127">Yeni bir ASP.NET sayfası oluşturun ve yalnızca uyguladık kullanıcı denetimi için etiket öneki kaydedin:</span><span class="sxs-lookup"><span data-stu-id="b9b70-127">Create a new ASP.NET page and register a tag prefix for the user control you have just implemented:</span></span>

[!code-aspx[Main](using-dynamicpopulate-with-a-user-control-and-javascript-cs/samples/sample6.aspx)]

<span data-ttu-id="b9b70-128">Ardından, ASP.NET AJAX dahil `ScriptManager` yeni sayfasında denetimi:</span><span class="sxs-lookup"><span data-stu-id="b9b70-128">Then, include the ASP.NET AJAX `ScriptManager` control on the new page:</span></span>

[!code-aspx[Main](using-dynamicpopulate-with-a-user-control-and-javascript-cs/samples/sample7.aspx)]

<span data-ttu-id="b9b70-129">Son olarak, kullanıcı denetimi sayfasına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b9b70-129">Finally, add the user control to the page.</span></span> <span data-ttu-id="b9b70-130">Yalnızca ayarlamanız gerekir, `ID` özniteliği (ve `runat="server"`, Elbette), ancak belirli bir ad ayarlamak de: `mcd1` bu içinde kullanıcı denetimini JavaScript kullanarak erişmek için kullanılan önek olduğundan.</span><span class="sxs-lookup"><span data-stu-id="b9b70-130">You only have to set its `ID` attribute (and `runat="server"`, of course), but you also have to set it to a specific name: `mcd1` since this is the prefix used within the user control to access it using JavaScript.</span></span>

[!code-aspx[Main](using-dynamicpopulate-with-a-user-control-and-javascript-cs/samples/sample8.aspx)]

<span data-ttu-id="b9b70-131">Ve bu kadar!</span><span class="sxs-lookup"><span data-stu-id="b9b70-131">And that's it!</span></span> <span data-ttu-id="b9b70-132">Sayfa beklendiği gibi davranır: bir kullanıcı üzerinde bulunan radyo düğmelerinin tıklarsa, araç seti, denetimi web hizmeti çağrıları ve istenen biçiminde geçerli tarihi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="b9b70-132">The page behaves as expected: A user clicks on on of the radio buttons, the control in the Toolkit calls the web service and displays the current date in the desired format.</span></span>


<span data-ttu-id="b9b70-133">[![Bir kullanıcı denetimi radyo düğmeleri bulunur](using-dynamicpopulate-with-a-user-control-and-javascript-cs/_static/image2.png)](using-dynamicpopulate-with-a-user-control-and-javascript-cs/_static/image1.png)</span><span class="sxs-lookup"><span data-stu-id="b9b70-133">[![The radio buttons reside in a user control](using-dynamicpopulate-with-a-user-control-and-javascript-cs/_static/image2.png)](using-dynamicpopulate-with-a-user-control-and-javascript-cs/_static/image1.png)</span></span>

<span data-ttu-id="b9b70-134">Bir kullanıcı denetimi radyo düğmeleri bulunur ([tam boyutlu görüntüyü görüntülemek için tıklatın](using-dynamicpopulate-with-a-user-control-and-javascript-cs/_static/image3.png))</span><span class="sxs-lookup"><span data-stu-id="b9b70-134">The radio buttons reside in a user control ([Click to view full-size image](using-dynamicpopulate-with-a-user-control-and-javascript-cs/_static/image3.png))</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="b9b70-135">[Önceki](dynamically-populating-a-control-using-javascript-code-cs.md)
[sonraki](dynamically-populating-a-control-vb.md)</span><span class="sxs-lookup"><span data-stu-id="b9b70-135">[Previous](dynamically-populating-a-control-using-javascript-code-cs.md)
[Next](dynamically-populating-a-control-vb.md)</span></span>