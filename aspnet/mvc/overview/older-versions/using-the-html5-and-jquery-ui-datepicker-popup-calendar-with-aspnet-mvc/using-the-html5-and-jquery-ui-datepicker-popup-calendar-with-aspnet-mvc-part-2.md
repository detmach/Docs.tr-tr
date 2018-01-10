---
uid: mvc/overview/older-versions/using-the-html5-and-jquery-ui-datepicker-popup-calendar-with-aspnet-mvc/using-the-html5-and-jquery-ui-datepicker-popup-calendar-with-aspnet-mvc-part-2
title: "HTML5 ve jQuery UI Datepicker Popup Calendar ASP.NET MVC - bölüm 2 ile kullanma | Microsoft Docs"
author: Rick-Anderson
description: "Bu öğretici Düzenleyicisi şablonları, görüntüleme şablonları ve jQuery UI datepicker popup calendar ASP.NET MV içinde çalışmak nasıl temellerini öğretmek..."
ms.author: aspnetcontent
manager: wpickett
ms.date: 08/29/2011
ms.topic: article
ms.assetid: 21a178de-4c5a-4211-8a9c-74ec576c0f30
ms.technology: dotnet-mvc
ms.prod: .net-framework
msc.legacyurl: /mvc/overview/older-versions/using-the-html5-and-jquery-ui-datepicker-popup-calendar-with-aspnet-mvc/using-the-html5-and-jquery-ui-datepicker-popup-calendar-with-aspnet-mvc-part-2
msc.type: authoredcontent
ms.openlocfilehash: 271c244ab0b9e2524a33ea6ff4d41893ce22472f
ms.sourcegitcommit: 9a9483aceb34591c97451997036a9120c3fe2baf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/10/2017
---
<a name="using-the-html5-and-jquery-ui-datepicker-popup-calendar-with-aspnet-mvc---part-2"></a><span data-ttu-id="c84f0-103">HTML5 ve jQuery UI Datepicker Popup Calendar ASP.NET MVC - bölüm 2 ile kullanma</span><span class="sxs-lookup"><span data-stu-id="c84f0-103">Using the HTML5 and jQuery UI Datepicker Popup Calendar with ASP.NET MVC - Part 2</span></span>
====================
<span data-ttu-id="c84f0-104">Tarafından [Rick Anderson](https://github.com/Rick-Anderson)</span><span class="sxs-lookup"><span data-stu-id="c84f0-104">by [Rick Anderson](https://github.com/Rick-Anderson)</span></span>

> <span data-ttu-id="c84f0-105">Bu öğretici Düzenleyicisi şablonları, görüntüleme şablonları ve jQuery UI datepicker popup calendar bir ASP.NET MVC Web uygulamasında çalışmak nasıl temellerini öğretmek.</span><span class="sxs-lookup"><span data-stu-id="c84f0-105">This tutorial will teach you the basics of how to work with editor templates, display templates, and the jQuery UI datepicker popup calendar in an ASP.NET MVC Web application.</span></span>


## <a name="adding-an-automatic-datetime-template"></a><span data-ttu-id="c84f0-106">Otomatik bir DateTime şablonu ekleme</span><span class="sxs-lookup"><span data-stu-id="c84f0-106">Adding an Automatic DateTime Template</span></span>

<span data-ttu-id="c84f0-107">Bu öğreticinin ilk bölümü nasıl biçimlendirme açıkça belirtmek için modeli için öznitelikler ekleyebilirsiniz ve nasıl açıkça modeli işlemek için kullanılan şablonu belirtebilirsiniz gördünüz.</span><span class="sxs-lookup"><span data-stu-id="c84f0-107">In the first part of this tutorial, you saw how you can add attributes to the model to explicitly specify formatting, and how you can explicitly specify the template that's used to render the model.</span></span> <span data-ttu-id="c84f0-108">Örneğin, [DisplayFormat](https://msdn.microsoft.com/en-us/library/system.componentmodel.dataannotations.displayformatattribute.aspx) aşağıdaki kodu açıkça özniteliğinde belirtir için biçimlendirme `ReleaseDate` özelliği.</span><span class="sxs-lookup"><span data-stu-id="c84f0-108">For example, the [DisplayFormat](https://msdn.microsoft.com/en-us/library/system.componentmodel.dataannotations.displayformatattribute.aspx) attribute in the following code explicity specifies the formatting for the `ReleaseDate` property.</span></span>

[!code-csharp[Main](using-the-html5-and-jquery-ui-datepicker-popup-calendar-with-aspnet-mvc-part-2/samples/sample1.cs)]

<span data-ttu-id="c84f0-109">Aşağıdaki örnekte, [DataType](https://msdn.microsoft.com/en-us/library/system.componentmodel.dataannotations.datatype.aspx) özniteliğini kullanarak `Date` numaralandırma, belirtir tarih şablonu modeli işlemek için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c84f0-109">In the following example, the [DataType](https://msdn.microsoft.com/en-us/library/system.componentmodel.dataannotations.datatype.aspx) attribute, using the `Date` enumeration, specifies that the date template should be used to render the model.</span></span> <span data-ttu-id="c84f0-110">Yerleşik tarih şablonu projenizde tarih şablon ise kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c84f0-110">If there's no date template in your project, the built-in date template is used.</span></span>

[!code-csharp[Main](using-the-html5-and-jquery-ui-datepicker-popup-calendar-with-aspnet-mvc-part-2/samples/sample2.cs)]

<span data-ttu-id="c84f0-111">Ancak, ASP. MVC türüyle eşleşen bir tür adıyla eşleşen bir şablon bakarak kuralı-üzerinden-Yapılandırması'nı kullanarak gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c84f0-111">However, ASP.MVC can perform type matching using convention-over-configuration, by looking for a template that matches the name of a type.</span></span> <span data-ttu-id="c84f0-112">Bu öznitelik ya da kod hiç kullanmadan verileri otomatik olarak biçimlendirir bir şablonu oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="c84f0-112">This lets you create a template that automatically formats data without using any attributes or code at all.</span></span> <span data-ttu-id="c84f0-113">Model türü özelliklerine otomatik olarak uygulanan bir şablon oluşturmak için bu bölümü öğreticinin [DateTime](https://msdn.microsoft.com/en-us/library/system.datetime.aspx).</span><span class="sxs-lookup"><span data-stu-id="c84f0-113">For this part of the tutorial, you'll create a template that's automatically applied to model properties of type [DateTime](https://msdn.microsoft.com/en-us/library/system.datetime.aspx).</span></span> <span data-ttu-id="c84f0-114">Şablon türü tüm özelliklerde modeli işlemek için kullanılması gerektiğini belirtmek için bir öznitelik veya diğer yapılandırma kullanmanız gerekmez [DateTime](https://msdn.microsoft.com/en-us/library/system.datetime.aspx).</span><span class="sxs-lookup"><span data-stu-id="c84f0-114">You won't need to use an attribute or other configuration to specify that the template should be used to render all model properties of type [DateTime](https://msdn.microsoft.com/en-us/library/system.datetime.aspx).</span></span>

<span data-ttu-id="c84f0-115">Ayrıca, tek tek özellikleri veya hatta tek tek alanların görüntüsünü özelleştirmek için bir yol da öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="c84f0-115">You'll also learn a way to customize the display of individual properties or even individual fields.</span></span>

<span data-ttu-id="c84f0-116">Başlamak için şimdi varolan biçimlendirme bilgilerini kaldırın ve uygulamada tam tarihlerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="c84f0-116">To begin, let's remove existing formatting information and display full dates in the application.</span></span>

<span data-ttu-id="c84f0-117">Açık *Movie.cs* çıkışı açıklamadan çıkarın ve dosya `DataType` özniteliği `ReleaseDate` özelliği:</span><span class="sxs-lookup"><span data-stu-id="c84f0-117">Open the *Movie.cs* file and comment out the `DataType` attribute on the `ReleaseDate` property:</span></span>

[!code-csharp[Main](using-the-html5-and-jquery-ui-datepicker-popup-calendar-with-aspnet-mvc-part-2/samples/sample3.cs)]

<span data-ttu-id="c84f0-118">Uygulamayı çalıştırmak için CTRL + F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="c84f0-118">Press CTRL+F5 to run the application.</span></span>

<span data-ttu-id="c84f0-119">Dikkat `ReleaseDate` özelliği şimdi görüntüler tarih ve saat biçimlendirme hiçbir bilgi sağlandığında, varsayılan olduğundan.</span><span class="sxs-lookup"><span data-stu-id="c84f0-119">Notice that the `ReleaseDate` property now displays both the date and time, because that's the default when no formatting information is provided.</span></span>

![](using-the-html5-and-jquery-ui-datepicker-popup-calendar-with-aspnet-mvc-part-2/_static/image1.png)

### <a name="adding-css-styles-for-testing-new-templates"></a><span data-ttu-id="c84f0-120">CSS stilleri yeni şablonlar test etmek için ekleme</span><span class="sxs-lookup"><span data-stu-id="c84f0-120">Adding CSS Styles for Testing New Templates</span></span>

<span data-ttu-id="c84f0-121">Tarihleri biçimlendirmek için bir şablonu oluşturmadan önce yeni şablonlar uygulayabilirsiniz birkaç CSS stil kurallarını ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="c84f0-121">Before you create a template for formatting dates, you'll add a few CSS style rules that you can apply to the new templates.</span></span> <span data-ttu-id="c84f0-122">Bu, işlenen sayfa yeni şablonu kullandığından emin olun yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="c84f0-122">These will help you verify that the rendered page is using the new template.</span></span>

<span data-ttu-id="c84f0-123">Açık *Content\Site.cs*s dosya ve aşağıdaki CSS kuralları dosyasının en altına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c84f0-123">Open the *Content\Site.cs*s file and add the following CSS rules to the bottom of the file:</span></span>

[!code-css[Main](using-the-html5-and-jquery-ui-datepicker-popup-calendar-with-aspnet-mvc-part-2/samples/sample4.css)]

### <a name="adding-datetime-display-templates"></a><span data-ttu-id="c84f0-124">DateTime görüntüleme şablonları ekleme</span><span class="sxs-lookup"><span data-stu-id="c84f0-124">Adding DateTime Display Templates</span></span>

<span data-ttu-id="c84f0-125">Artık yeni şablonu oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c84f0-125">Now you can create the new template.</span></span> <span data-ttu-id="c84f0-126">İçinde *Views\Movies* klasörü oluşturmak bir *DisplayTemplates* klasör.</span><span class="sxs-lookup"><span data-stu-id="c84f0-126">In the *Views\Movies* folder, create a *DisplayTemplates* folder.</span></span>

<span data-ttu-id="c84f0-127">İçinde *görünümler/paylaşılan* klasörü oluşturmak bir *DisplayTemplates* klasör ve bir *EditorTemplates* klasör.</span><span class="sxs-lookup"><span data-stu-id="c84f0-127">In the *Views\Shared* folder, create a *DisplayTemplates* folder and an *EditorTemplates* folder.</span></span>

<span data-ttu-id="c84f0-128">Ekran şablonları *views\shared\displaytemplates konumunda* klasörü tüm denetleyicileri tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c84f0-128">The display templates in the *Views\Shared\DisplayTemplates* folder will be used by all controllers.</span></span> <span data-ttu-id="c84f0-129">Ekran şablonları *Views\Movie\DisplayTemplates* klasörü yalnızca kullanılacak `Movie` denetleyicisi.</span><span class="sxs-lookup"><span data-stu-id="c84f0-129">The display templates in the *Views\Movie\DisplayTemplates* folder will be used only by the `Movie` controller.</span></span> <span data-ttu-id="c84f0-130">(Şablonda her iki klasörde aynı ada sahip bir şablon görünüyorsa, *Views\Movie\DisplayTemplates* klasörü — diğer bir deyişle, daha özel şablonu — tarafından döndürülen görünümler için önceliklidir `Movie` denetleyici.)</span><span class="sxs-lookup"><span data-stu-id="c84f0-130">(If a template with the same name appears in both folders, the template in the *Views\Movie\DisplayTemplates* folder — that is, the more specific template — takes precedence for views returned by the `Movie` controller.)</span></span>

<span data-ttu-id="c84f0-131">İçinde **Çözüm Gezgini**, genişletin *görünümleri* klasörünü genişletin *paylaşılan* klasörünü ve ardından sağ tıklayarak *views\shared\displaytemplates konumunda* klasör.</span><span class="sxs-lookup"><span data-stu-id="c84f0-131">In **Solution Explorer**, expand the *Views* folder, expand the *Shared* folder, and then right-click the *Views\Shared\DisplayTemplates* folder.</span></span>

<span data-ttu-id="c84f0-132">Tıklatın **Ekle** ve ardından **Görünüm**.</span><span class="sxs-lookup"><span data-stu-id="c84f0-132">Click **Add** and then click **View**.</span></span> <span data-ttu-id="c84f0-133">**Görünüm Ekle** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="c84f0-133">The **Add View** dialog box is displayed.</span></span>

<span data-ttu-id="c84f0-134">İçinde **Görünüm adı** kutusuna `DateTime`.</span><span class="sxs-lookup"><span data-stu-id="c84f0-134">In the **View name** box, type `DateTime`.</span></span> <span data-ttu-id="c84f0-135">(, Bu ad türünün adını eşleştirmek için kullanmanız gerekir.)</span><span class="sxs-lookup"><span data-stu-id="c84f0-135">(You must use this name in order to match the name of the type.)</span></span>

<span data-ttu-id="c84f0-136">Seçin **kısmi görünüm olarak oluştur** onay kutusu.</span><span class="sxs-lookup"><span data-stu-id="c84f0-136">Select the **Create as a partial view** check box.</span></span> <span data-ttu-id="c84f0-137">Olduğundan emin olun **düzen veya ana sayfa kullanmak** ve **kesin türü belirtilmiş görünüm oluşturmak** onay kutularının seçili değil.</span><span class="sxs-lookup"><span data-stu-id="c84f0-137">Make sure that the **Use a layout or master page** and **Create a strongly-typed view** check boxes are not selected.</span></span>

![](using-the-html5-and-jquery-ui-datepicker-popup-calendar-with-aspnet-mvc-part-2/_static/image2.png)

<span data-ttu-id="c84f0-138">**Ekle**'yi tıklatın.</span><span class="sxs-lookup"><span data-stu-id="c84f0-138">Click **Add**.</span></span> <span data-ttu-id="c84f0-139">A *DateTime.cshtml* şablonu oluşturulur *views\shared\displaytemplates konumunda*.</span><span class="sxs-lookup"><span data-stu-id="c84f0-139">A *DateTime.cshtml* template is created in the *Views\Shared\DisplayTemplates*.</span></span>

<span data-ttu-id="c84f0-140">Aşağıdaki resimde gösterildiği *görünümleri* klasöründe **Çözüm Gezgini** sonra `DateTime` görüntüleme ve düzenleyici şablonları oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c84f0-140">The following image shows the *Views* folder in **Solution Explorer** after the `DateTime` display and editor templates are created.</span></span>

![](using-the-html5-and-jquery-ui-datepicker-popup-calendar-with-aspnet-mvc-part-2/_static/image3.png)

<span data-ttu-id="c84f0-141">Açık *Views\Shared\DisplayTemplates\DateTime.cshtml* dosya ve kullandığı aşağıdaki biçimlendirmeleri eklemek [String.Format](https://msdn.microsoft.com/en-us/library/system.string.format.aspx) özelliği bir tarih saat olmadan olarak biçimlendirmek için yöntem.</span><span class="sxs-lookup"><span data-stu-id="c84f0-141">Open the *Views\Shared\DisplayTemplates\DateTime.cshtml* file and add the following markup, which uses the [String.Format](https://msdn.microsoft.com/en-us/library/system.string.format.aspx) method to format the property as a date without the time.</span></span> <span data-ttu-id="c84f0-142">( `{0:d}` Biçimi kısa tarih biçimi belirtir.)</span><span class="sxs-lookup"><span data-stu-id="c84f0-142">(The `{0:d}` format specifies short date format.)</span></span>

[!code-csharp[Main](using-the-html5-and-jquery-ui-datepicker-popup-calendar-with-aspnet-mvc-part-2/samples/sample5.cs)]

<span data-ttu-id="c84f0-143">Oluşturmak için bu adımı yineleyin bir `DateTime` şablonunda *Views\Movie\DisplayTemplates* klasör.</span><span class="sxs-lookup"><span data-stu-id="c84f0-143">Repeat this step to create a `DateTime` template in the *Views\Movie\DisplayTemplates* folder.</span></span> <span data-ttu-id="c84f0-144">Aşağıdaki kodda kullanmak *Views\Movie\DisplayTemplates\DateTime.cshtml* dosya.</span><span class="sxs-lookup"><span data-stu-id="c84f0-144">Use the following code in the *Views\Movie\DisplayTemplates\DateTime.cshtml* file.</span></span>

[!code-csharp[Main](using-the-html5-and-jquery-ui-datepicker-popup-calendar-with-aspnet-mvc-part-2/samples/sample6.cs)]

<span data-ttu-id="c84f0-145">`loud-1` CSS sınıfı tarihi kırmızı kalın metin olarak görünen neden olur.</span><span class="sxs-lookup"><span data-stu-id="c84f0-145">The `loud-1` CSS class causes the date to be display in bold red text.</span></span> <span data-ttu-id="c84f0-146">Eklediğiniz `loud-1` ne zaman bu özel şablonu kullanılıyor kolayca görebilmek için yalnızca bir geçici önlemi olarak CSS sınıfı.</span><span class="sxs-lookup"><span data-stu-id="c84f0-146">You added the `loud-1` CSS class just as a temporary measure so you can easily see when this particular template is being used.</span></span>

<span data-ttu-id="c84f0-147">Neler yaptığınızı oluşturulur ve ASP.NET tarihleri görüntülemek için kullanacağı şablonları özelleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="c84f0-147">What you've done is created and customized templates that ASP.NET will use to display dates.</span></span> <span data-ttu-id="c84f0-148">Daha fazla genel şablonu (içinde *views\shared\displaytemplates konumunda* klasörü) basit bir kısa tarih görüntüler.</span><span class="sxs-lookup"><span data-stu-id="c84f0-148">The more general template (in the *Views\Shared\DisplayTemplates* folder) displays a simple short date.</span></span> <span data-ttu-id="c84f0-149">Özellikle olan şablon `Movie` denetleyici (içinde *Views\Movies\DisplayTemplates* klasörü) de biçimlendirilen tarih kırmızı kalın metin olarak görüntüler.</span><span class="sxs-lookup"><span data-stu-id="c84f0-149">The template that's specifically for the `Movie` controller (in the *Views\Movies\DisplayTemplates* folder) displays a short date that's also formatted as bold red text.</span></span>

<span data-ttu-id="c84f0-150">Uygulamayı çalıştırmak için CTRL + F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="c84f0-150">Press CTRL+F5 to run the application.</span></span> <span data-ttu-id="c84f0-151">Tarayıcı uygulaması için Index görünümünü işler.</span><span class="sxs-lookup"><span data-stu-id="c84f0-151">The browser renders the Index view for the application.</span></span>

<span data-ttu-id="c84f0-152">`ReleaseDate` Özelliği artık tarihi görüntüler süresi olmadan koyu kırmızı yazı tipi. Bu, onaylayın yardımcı olur `DateTime` şablonlu yardımcı *Views\Movies\DisplayTemplates* klasörü üzerinde seçili `DateTime` paylaşılan klasörde şablonlu Yardımcısı (*Views\Shared\ DisplayTemplates*).</span><span class="sxs-lookup"><span data-stu-id="c84f0-152">The `ReleaseDate` property now displays the date in a bold red font without the time.This helps you confirm that the `DateTime` templated helper in the *Views\Movies\DisplayTemplates* folder is selected over the `DateTime` templated helper in the shared folder (*Views\Shared\DisplayTemplates*).</span></span>

![](using-the-html5-and-jquery-ui-datepicker-popup-calendar-with-aspnet-mvc-part-2/_static/image4.png)

<span data-ttu-id="c84f0-153">Şimdi yeniden adlandırmak *Views\Movies\DisplayTemplates\DateTime.cshtml* dosya *Views\Movies\DisplayTemplates\LoudDateTime.cshtml*.</span><span class="sxs-lookup"><span data-stu-id="c84f0-153">Now rename the *Views\Movies\DisplayTemplates\DateTime.cshtml* file to *Views\Movies\DisplayTemplates\LoudDateTime.cshtml*.</span></span>

<span data-ttu-id="c84f0-154">Uygulamayı çalıştırmak için CTRL + F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="c84f0-154">Press CTRL+F5 to run the application.</span></span>

<span data-ttu-id="c84f0-155">Bu süre `ReleaseDate` özelliği bir tarih saat ve kalın kırmızı yazı tipi olmadan görüntüler.</span><span class="sxs-lookup"><span data-stu-id="c84f0-155">This time the `ReleaseDate` property displays a date without the time and without the bold red font.</span></span> <span data-ttu-id="c84f0-156">Veri adına sahip bir şablon türünün, bu gösterir (Bu durumda `DateTime`) otomatik olarak bu türdeki tüm model özelliklerini görüntülemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c84f0-156">This illustrates that a template that has the name of the data type (in this case `DateTime`) is automatically used to display all model properties of that type.</span></span> <span data-ttu-id="c84f0-157">Sonra yeniden adlandırılmış *DateTime.cshtml* dosya *LoudDateTime.cshtml*, ASP.NET artık bulunan bir şablonda *Views\Movies\DisplayTemplates* kullanılabilmesi için klasör *DateTime.cshtml* şablondan * Views\Movies\Shared\* klasör.</span><span class="sxs-lookup"><span data-stu-id="c84f0-157">After you renamed the *DateTime.cshtml* file to *LoudDateTime.cshtml*, ASP.NET no longer found a template in the *Views\Movies\DisplayTemplates* folder, so it used the *DateTime.cshtml* template from the *Views\Movies\Shared\* folder.</span></span>

<span data-ttu-id="c84f0-158">(Tüm büyük/küçük harf ile şablon dosyası adı oluşturulan şablon eşleştirme büyük küçük harf duyarsız olduğundan.</span><span class="sxs-lookup"><span data-stu-id="c84f0-158">(The template matching is case insensitive, so you could have created the template file name with any casing.</span></span> <span data-ttu-id="c84f0-159">For example, *DATETIME.chstml, datetime.cshtml*, ve *DaTeTiMe.cshtml* tüm eşleşir `DateTime` türü.)</span><span class="sxs-lookup"><span data-stu-id="c84f0-159">For example, *DATETIME.chstml, datetime.cshtml*, and *DaTeTiMe.cshtml* would all match the `DateTime` type.)</span></span>

<span data-ttu-id="c84f0-160">Gözden geçirmek için: Bu noktada, `ReleaseDate` alanı görüntülenir kullanarak *Views\Movies\DisplayTemplates\DateTime.cshtml* verileri kısa tarih biçimini kullanarak görüntüler, ancak Aksi durumda özel bir biçime ekler şablonu.</span><span class="sxs-lookup"><span data-stu-id="c84f0-160">To review: at this point, the `ReleaseDate` field is being displayed using the *Views\Movies\DisplayTemplates\DateTime.cshtml* template, which displays the data using a short date format, but otherwise adds no special format.</span></span>

### <a name="using-uihint-to-specify-a-display-template"></a><span data-ttu-id="c84f0-161">Bir görüntü şablonu belirtmek için UIHint kullanma</span><span class="sxs-lookup"><span data-stu-id="c84f0-161">Using UIHint to Specify a Display Template</span></span>

<span data-ttu-id="c84f0-162">Çoğu web uygulamanız varsa, `DateTime` alanları ve varsayılan olarak tüm veya çoğu salt tarih biçiminde görüntülemek istediğiniz *DateTime.cshtml* iyi bir yaklaşım şablonudur.</span><span class="sxs-lookup"><span data-stu-id="c84f0-162">If your web application has many `DateTime` fields and by default you want to display all or most of them in date-only format, the *DateTime.cshtml* template is a good approach.</span></span> <span data-ttu-id="c84f0-163">Ancak, birkaç tarihleri tam tarihi ve saati görüntülemek istediğiniz yoksa ne?</span><span class="sxs-lookup"><span data-stu-id="c84f0-163">But what if you have a few dates where you want to display the full date and time?</span></span> <span data-ttu-id="c84f0-164">Sorun değil.</span><span class="sxs-lookup"><span data-stu-id="c84f0-164">No problem.</span></span> <span data-ttu-id="c84f0-165">Ek bir şablon oluşturma ve kullanma [UIHint](https://msdn.microsoft.com/en-us/library/system.componentmodel.dataannotations.uihintattribute.uihint.aspx) tam tarih ve saat için biçimlendirme belirtmek için özniteliği.</span><span class="sxs-lookup"><span data-stu-id="c84f0-165">You can create an additional template and use the [UIHint](https://msdn.microsoft.com/en-us/library/system.componentmodel.dataannotations.uihintattribute.uihint.aspx) attribute to specify formatting for the full date and time.</span></span> <span data-ttu-id="c84f0-166">Bu şablon seçerek geçerli olabilir.</span><span class="sxs-lookup"><span data-stu-id="c84f0-166">You can then selectively apply that template.</span></span> <span data-ttu-id="c84f0-167">Kullanabileceğiniz [UIHint](https://msdn.microsoft.com/en-us/library/system.componentmodel.dataannotations.uihintattribute.uihint.aspx) özniteliği model düzeyinde veya, şablon bir görünüm içindeki belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c84f0-167">You can use the [UIHint](https://msdn.microsoft.com/en-us/library/system.componentmodel.dataannotations.uihintattribute.uihint.aspx) attribute at the model level or you can specify the template inside a view.</span></span> <span data-ttu-id="c84f0-168">Bu bölümde, nasıl kullanılacağını görürsünüz `UIHint` tarih-saat alanları için bazı örnekler biçimlendirme seçmeli olarak değiştirmek için öznitelik.</span><span class="sxs-lookup"><span data-stu-id="c84f0-168">In this section, you'll see how to use the `UIHint` attribute to selectively change the formatting for some instances of date-time fields.</span></span>

<span data-ttu-id="c84f0-169">Açık *Views\Movies\DisplayTemplates\LoudDateTime.cshtml* dosya ve var olan kodu aşağıdakilerle değiştirin:</span><span class="sxs-lookup"><span data-stu-id="c84f0-169">Open the *Views\Movies\DisplayTemplates\LoudDateTime.cshtml* file and replace the existing code with the following:</span></span>

[!code-cshtml[Main](using-the-html5-and-jquery-ui-datepicker-popup-calendar-with-aspnet-mvc-part-2/samples/sample7.cshtml)]

<span data-ttu-id="c84f0-170">Bu tam tarih ve saat görüntülenmesine neden olur ve yeşil ve büyük metni CSS sınıfı ekler.</span><span class="sxs-lookup"><span data-stu-id="c84f0-170">This causes the full date and time to be displayed and adds the CSS class that makes the text green and large.</span></span>

<span data-ttu-id="c84f0-171">Açık *Movie.cs* dosya ve ekleme [UIHint](https://msdn.microsoft.com/en-us/library/system.componentmodel.dataannotations.uihintattribute.uihint.aspx) özniteliğini `ReleaseDate` özelliği, aşağıdaki örnekte gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="c84f0-171">Open the *Movie.cs* file and add the [UIHint](https://msdn.microsoft.com/en-us/library/system.componentmodel.dataannotations.uihintattribute.uihint.aspx) attribute to the `ReleaseDate` property, as shown in the following example:</span></span>

[!code-csharp[Main](using-the-html5-and-jquery-ui-datepicker-popup-calendar-with-aspnet-mvc-part-2/samples/sample8.cs)]

<span data-ttu-id="c84f0-172">Ne zaman bu ASP.NET MVC, bildirir `ReleaseDate` özelliği (özellikle ve yalnızca hiçbir `DateTime` nesnesi), kullanması gereken *LoudDateTime.cshtml* şablonu.</span><span class="sxs-lookup"><span data-stu-id="c84f0-172">This tells ASP.NET MVC that when it displays the `ReleaseDate` property (specifically, and not just any `DateTime` object), it should use the *LoudDateTime.cshtml* template.</span></span>

<span data-ttu-id="c84f0-173">Uygulamayı çalıştırmak için CTRL + F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="c84f0-173">Press CTRL+F5 to run the application.</span></span>

<span data-ttu-id="c84f0-174">Dikkat `ReleaseDate` özelliği şimdi tarih ve saat büyük yeşil yazı tipiyle görüntüler.</span><span class="sxs-lookup"><span data-stu-id="c84f0-174">Notice that the `ReleaseDate` property now displays the date and time in a large green font.</span></span>

<span data-ttu-id="c84f0-175">Dönün `UIHint` özniteliğini *Movie.cs* dosyası ve yorum teslim böylece *LoudDateTime.cshtml* şablonu olmaz kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c84f0-175">Return to the `UIHint` attribute in the *Movie.cs* file and comment it out so the *LoudDateTime.cshtml* template won't be used.</span></span> <span data-ttu-id="c84f0-176">Uygulamayı yeniden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c84f0-176">Run the application again.</span></span> <span data-ttu-id="c84f0-177">Yayın tarihi büyük ve yeşil görüntülenmez.</span><span class="sxs-lookup"><span data-stu-id="c84f0-177">The release date is not displayed large and green.</span></span> <span data-ttu-id="c84f0-178">Bu doğrular *Views\Shared\DisplayTemplates\DateTime.cshtml* şablon dizini ve ayrıntıları görünümlerinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c84f0-178">This verifies that the *Views\Shared\DisplayTemplates\DateTime.cshtml* template is used in the Index and Details views.</span></span>

<span data-ttu-id="c84f0-179">Daha önce belirtildiği gibi aynı zamanda bazı verileri tek bir örneğini Şablonu Uygula olanak sağlayan bir görünümde bir şablon uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="c84f0-179">As mentioned earlier, you can also apply a template in a view, which lets you apply the template to an individual instance of some data.</span></span> <span data-ttu-id="c84f0-180">Açık *Views\Movies\Details.cshtml* görünümü.</span><span class="sxs-lookup"><span data-stu-id="c84f0-180">Open the *Views\Movies\Details.cshtml* view.</span></span> <span data-ttu-id="c84f0-181">Ekleme `"LoudDateTime"` ikinci parametre olarak [Html.DisplayFor](https://msdn.microsoft.com/en-us/library/ee407420.aspx) çağrısı `ReleaseDate` alan.</span><span class="sxs-lookup"><span data-stu-id="c84f0-181">Add `"LoudDateTime"` as the second parameter of the [Html.DisplayFor](https://msdn.microsoft.com/en-us/library/ee407420.aspx) call for the `ReleaseDate` field.</span></span> <span data-ttu-id="c84f0-182">Tamamlanan kodu şöyle görünür:</span><span class="sxs-lookup"><span data-stu-id="c84f0-182">The completed code looks like this:</span></span>

[!code-cshtml[Main](using-the-html5-and-jquery-ui-datepicker-popup-calendar-with-aspnet-mvc-part-2/samples/sample9.cshtml)]

<span data-ttu-id="c84f0-183">Bu belirleyen `LoudDateTime` şablonu, hangi özeliklerin modeline uygulanan bağımsız olarak model özelliği görüntülemek için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c84f0-183">This specifies that the `LoudDateTime` template should be used to display the model property, regardless of what attributes are applied to the model.</span></span>

<span data-ttu-id="c84f0-184">Uygulamayı çalıştırmak için CTRL + F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="c84f0-184">Press CTRL+F5 to run the application.</span></span>

<span data-ttu-id="c84f0-185">Film dizin sayfası kullandığını doğrulayın *Views\Shared\DisplayTemplates\DateTime.cshtml* şablonu (kırmızı kalın) ve *Movie\Details* sayfasını kullanarak *Views\Movies\ DisplayTemplates\LoudDateTime.cshtml* şablonu (büyük ve yeşil).</span><span class="sxs-lookup"><span data-stu-id="c84f0-185">Verify that the movie index page is using the *Views\Shared\DisplayTemplates\DateTime.cshtml* template (red bold) and the *Movie\Details* page is using the *Views\Movies\DisplayTemplates\LoudDateTime.cshtml* template (large and green).</span></span>

![](using-the-html5-and-jquery-ui-datepicker-popup-calendar-with-aspnet-mvc-part-2/_static/image5.png)

<span data-ttu-id="c84f0-186">Sonraki bölümde, karmaşık bir tür için bir şablon oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="c84f0-186">In the next section, you'll create a template for a complex type.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="c84f0-187">[Önceki](using-the-html5-and-jquery-ui-datepicker-popup-calendar-with-aspnet-mvc-part-1.md)
[sonraki](using-the-html5-and-jquery-ui-datepicker-popup-calendar-with-aspnet-mvc-part-3.md)</span><span class="sxs-lookup"><span data-stu-id="c84f0-187">[Previous](using-the-html5-and-jquery-ui-datepicker-popup-calendar-with-aspnet-mvc-part-1.md)
[Next](using-the-html5-and-jquery-ui-datepicker-popup-calendar-with-aspnet-mvc-part-3.md)</span></span>