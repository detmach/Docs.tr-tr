---
title: "Entity Framework Çekirdek - 10 Öğreticisi 1 ile ASP.NET Core MVC"
author: tdykstra
description: 
keywords: "ASP.NET Core, Entity Framework Çekirdek Öğreticisi"
ms.author: tdykstra
manager: wpickett
ms.date: 03/15/2017
ms.topic: get-started-article
ms.assetid: b67c3d4a-f2bf-4132-a48b-4b0d599d7981
ms.technology: aspnet
ms.prod: asp.net-core
uid: data/ef-mvc/intro
ms.openlocfilehash: 5095def776f79d0bb76d5a8e94a4228ef0abed75
ms.sourcegitcommit: a80d35647aff66323160b2cb413b65d79d98f7a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/08/2017
---
# <a name="getting-started-with-aspnet-core-mvc-and-entity-framework-core-using-visual-studio-1-of-10"></a><span data-ttu-id="44c5d-103">ASP.NET Core MVC ve Entity Framework Visual Studio (1 / 10) kullanarak çekirdek ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="44c5d-103">Getting started with ASP.NET Core MVC and Entity Framework Core using Visual Studio (1 of 10)</span></span>

<span data-ttu-id="44c5d-104">Tarafından [zel Dykstra](https://github.com/tdykstra) ve [Rick Anderson](https://twitter.com/RickAndMSFT)</span><span class="sxs-lookup"><span data-stu-id="44c5d-104">By [Tom Dykstra](https://github.com/tdykstra) and [Rick Anderson](https://twitter.com/RickAndMSFT)</span></span>

<span data-ttu-id="44c5d-105">Bu öğretici Razor sayfalarının sürümü [burada](xref:data/ef-rp/intro).</span><span class="sxs-lookup"><span data-stu-id="44c5d-105">A Razor Pages version of this tutorial is available [here](xref:data/ef-rp/intro).</span></span> <span data-ttu-id="44c5d-106">Razor sayfalarının sürümü izleyin daha kolaydır ve daha fazla EF özellikleri kapsar.</span><span class="sxs-lookup"><span data-stu-id="44c5d-106">The Razor Pages version is easier to follow and covers more EF features.</span></span> <span data-ttu-id="44c5d-107">Takip ettiğiniz öneririz [Razor sayfalarının sürüm bu öğreticinin](xref:data/ef-rp/intro).</span><span class="sxs-lookup"><span data-stu-id="44c5d-107">We recommend you follow the [Razor Pages version of this tutorial](xref:data/ef-rp/intro).</span></span>

<span data-ttu-id="44c5d-108">Contoso University örnek web uygulaması Entity Framework (EF) çekirdek 2.0 ve Visual Studio 2017 kullanarak ASP.NET Core 2.0 MVC web uygulamalarının nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="44c5d-108">The Contoso University sample web application demonstrates how to create ASP.NET Core 2.0 MVC web applications using Entity Framework (EF) Core 2.0 and Visual Studio 2017.</span></span>

<span data-ttu-id="44c5d-109">Örnek uygulama, kurgusal bir Contoso üniversite için bir web sitesidir.</span><span class="sxs-lookup"><span data-stu-id="44c5d-109">The sample application is a web site for a fictional Contoso University.</span></span> <span data-ttu-id="44c5d-110">Öğrenci giriş, indirmelere oluşturma ve Eğitmen atamaları gibi işlevselliği içerir.</span><span class="sxs-lookup"><span data-stu-id="44c5d-110">It includes functionality such as student admission, course creation, and instructor assignments.</span></span> <span data-ttu-id="44c5d-111">Sıfırdan Contoso University örnek uygulamasının nasıl oluşturulacağını açıklayan eğitim serileri ilk budur.</span><span class="sxs-lookup"><span data-stu-id="44c5d-111">This is the first in a series of tutorials that explain how to build the Contoso University sample application from scratch.</span></span>

[<span data-ttu-id="44c5d-112">İndirme veya tamamlanan uygulama görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="44c5d-112">Download or view the completed application.</span></span>](https://github.com/aspnet/Docs/tree/master/aspnetcore/data/ef-mvc/intro/samples/cu-final)

<span data-ttu-id="44c5d-113">EF çekirdek 2.0 EF en son sürümü ancak henüz EF tüm özelliklerini yok 6.x.</span><span class="sxs-lookup"><span data-stu-id="44c5d-113">EF Core 2.0 is the latest version of EF but does not yet have all the features of EF 6.x.</span></span> <span data-ttu-id="44c5d-114">EF arasında seçim yapma hakkında bilgi için bkz: 6.x ve EF çekirdek [EF çekirdek vs. EF6.x](https://docs.microsoft.com/ef/efcore-and-ef6/).</span><span class="sxs-lookup"><span data-stu-id="44c5d-114">For information about how to choose between EF 6.x and EF Core, see [EF Core vs. EF6.x](https://docs.microsoft.com/ef/efcore-and-ef6/).</span></span> <span data-ttu-id="44c5d-115">EF seçerseniz 6.x, bkz: [Bu öğretici seri'nın önceki sürümünü](https://docs.microsoft.com/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/creating-an-entity-framework-data-model-for-an-asp-net-mvc-application).</span><span class="sxs-lookup"><span data-stu-id="44c5d-115">If you choose EF 6.x, see [the previous version of this tutorial series](https://docs.microsoft.com/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/creating-an-entity-framework-data-model-for-an-asp-net-mvc-application).</span></span>

> [!NOTE]
> * <span data-ttu-id="44c5d-116">Bu öğretici ASP.NET Core 1.1 sürümü için bkz: [PDF biçimi Bu öğreticide VS 2017 güncelleştirme 2 sürümü](https://github.com/aspnet/Docs/blob/master/aspnetcore/data/ef-mvc/intro/_static/efmvc1.1.pdf).</span><span class="sxs-lookup"><span data-stu-id="44c5d-116">For the ASP.NET Core 1.1 version of this tutorial, see the [VS 2017 Update 2 version of this tutorial in PDF format](https://github.com/aspnet/Docs/blob/master/aspnetcore/data/ef-mvc/intro/_static/efmvc1.1.pdf).</span></span>
> * <span data-ttu-id="44c5d-117">Visual Studio 2015 sürümünde Bu öğretici için bkz: [ASP.NET Core belgeleri PDF biçimli VS 2015 sürümü](https://github.com/aspnet/Docs/blob/master/aspnetcore/common/_static/aspnet-core-project-json.pdf).</span><span class="sxs-lookup"><span data-stu-id="44c5d-117">For the Visual Studio 2015 version of this tutorial, see the [VS 2015 version of ASP.NET Core documentation in PDF format](https://github.com/aspnet/Docs/blob/master/aspnetcore/common/_static/aspnet-core-project-json.pdf).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="44c5d-118">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="44c5d-118">Prerequisites</span></span>

[!INCLUDE[install 2.0](../../includes/install2.0.md)]

## <a name="troubleshooting"></a><span data-ttu-id="44c5d-119">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="44c5d-119">Troubleshooting</span></span>

<span data-ttu-id="44c5d-120">Olamaz çözmek bir sorunla çalıştırırsanız, genellikle çözümün kodunuzu karşılaştırarak bulabilirsiniz [projeyi](https://github.com/aspnet/Docs/tree/master/aspnetcore/data/ef-mvc/intro/samples/cu-final).</span><span class="sxs-lookup"><span data-stu-id="44c5d-120">If you run into a problem you can't resolve, you can generally find the solution by comparing your code to the [completed project](https://github.com/aspnet/Docs/tree/master/aspnetcore/data/ef-mvc/intro/samples/cu-final).</span></span> <span data-ttu-id="44c5d-121">Sık karşılaşılan hataları ve bunları çözmek nasıl listesi için bkz: [serideki son Öğreticisi sorun giderme bölümüne](advanced.md#common-errors).</span><span class="sxs-lookup"><span data-stu-id="44c5d-121">For a list of common errors and how to solve them, see [the Troubleshooting section of the last tutorial in the series](advanced.md#common-errors).</span></span> <span data-ttu-id="44c5d-122">Var. gerekenler bulamazsanız, bir soru için StackOverflow.com nakledebilirsiniz [ASP.NET Core](https://stackoverflow.com/questions/tagged/asp.net-core) veya [EF çekirdek](https://stackoverflow.com/questions/tagged/entity-framework-core).</span><span class="sxs-lookup"><span data-stu-id="44c5d-122">If you don't find what you need there, you can post a question to StackOverflow.com for  [ASP.NET Core](https://stackoverflow.com/questions/tagged/asp.net-core) or [EF Core](https://stackoverflow.com/questions/tagged/entity-framework-core).</span></span>

> [!TIP] 
> <span data-ttu-id="44c5d-123">Bu, her biri önceki eğitimlerine bitti üzerinde derlemeler 10 öğreticileri dizisidir.</span><span class="sxs-lookup"><span data-stu-id="44c5d-123">This is a series of 10 tutorials, each of which builds on what is done in earlier tutorials.</span></span>  <span data-ttu-id="44c5d-124">Her başarılı öğretici tamamlandıktan sonra projeyi bir kopyasını kaydetme göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="44c5d-124">Consider saving a copy of the project after each successful tutorial completion.</span></span>  <span data-ttu-id="44c5d-125">Sorunlarla karşılaşırsanız, daha sonra yeniden tüm dizileri başlangıcına geri dönerseniz yerine önceki öğreticiden başlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44c5d-125">Then if you run into problems, you can start over from the previous tutorial instead of going back to the beginning of the whole series.</span></span>

## <a name="the-contoso-university-web-application"></a><span data-ttu-id="44c5d-126">Contoso University web uygulaması</span><span class="sxs-lookup"><span data-stu-id="44c5d-126">The Contoso University web application</span></span>

<span data-ttu-id="44c5d-127">Bu öğreticiler oluşturmakta uygulama basit university web sitesidir.</span><span class="sxs-lookup"><span data-stu-id="44c5d-127">The application you'll be building in these tutorials is a simple university web site.</span></span>

<span data-ttu-id="44c5d-128">Kullanıcıların görüntüleyebileceği ve Öğrenci, indirmelere ve Eğitmen bilgileri güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="44c5d-128">Users can view and update student, course, and instructor information.</span></span> <span data-ttu-id="44c5d-129">Oluşturacağınız ekranlar bazılarını aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="44c5d-129">Here are a few of the screens you'll create.</span></span>

![Öğrenciler dizin sayfası](intro/_static/students-index.png)

![Öğrenciler Düzenle sayfası](intro/_static/student-edit.png)

<span data-ttu-id="44c5d-132">Öğretici Entity Framework çoğunlukla nasıl kullanılacağı hakkında odaklanabilmeniz bu sitenin UI Stili yerleşik şablonlar tarafından oluşturulan yakın tutulmuştur.</span><span class="sxs-lookup"><span data-stu-id="44c5d-132">The UI style of this site has been kept close to what's generated by the built-in templates, so that the tutorial can focus mainly on how to use the Entity Framework.</span></span>

## <a name="create-an-aspnet-core-mvc-web-application"></a><span data-ttu-id="44c5d-133">Bir ASP.NET Core MVC web uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="44c5d-133">Create an ASP.NET Core MVC web application</span></span>

<span data-ttu-id="44c5d-134">Visual Studio'yu açın ve "ContosoUniversity" adlı yeni bir ASP.NET Core C# web projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="44c5d-134">Open Visual Studio and create a new ASP.NET Core C# web project named "ContosoUniversity".</span></span>

* <span data-ttu-id="44c5d-135">Gelen **dosya** menüsünde, select **yeni > Proje**.</span><span class="sxs-lookup"><span data-stu-id="44c5d-135">From the **File** menu, select **New > Project**.</span></span>

* <span data-ttu-id="44c5d-136">Sol bölmeden seçin **yüklü > Visual C# > Web**.</span><span class="sxs-lookup"><span data-stu-id="44c5d-136">From the left pane, select **Installed > Visual C# > Web**.</span></span>

* <span data-ttu-id="44c5d-137">Seçin **ASP.NET çekirdek Web uygulaması** proje şablonu.</span><span class="sxs-lookup"><span data-stu-id="44c5d-137">Select the **ASP.NET Core Web Application** project template.</span></span>

* <span data-ttu-id="44c5d-138">Girin **ContosoUniversity** tıklatın ve adı olarak **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="44c5d-138">Enter **ContosoUniversity** as the name and click **OK**.</span></span>

  ![Yeni Proje iletişim kutusu](intro/_static/new-project.png)

* <span data-ttu-id="44c5d-140">Bekle **yeni ASP.NET çekirdek Web uygulaması (.NET Core)** görünmesi iletişim</span><span class="sxs-lookup"><span data-stu-id="44c5d-140">Wait for the **New ASP.NET Core Web Application (.NET Core)** dialog to appear</span></span>

* <span data-ttu-id="44c5d-141">Seçin **ASP.NET Core 2.0** ve **Web uygulaması (Model-View-Controller)** şablonu.</span><span class="sxs-lookup"><span data-stu-id="44c5d-141">Select **ASP.NET Core 2.0** and the **Web Application (Model-View-Controller)** template.</span></span>

  <span data-ttu-id="44c5d-142">**Not:** ASP.NET Core 2.0 ve EF çekirdek 2.0 veya üstü--emin olun, Bu öğretici gerektirir **ASP.NET Core 1.1** seçilmemiş.</span><span class="sxs-lookup"><span data-stu-id="44c5d-142">**Note:** This tutorial requires ASP.NET Core 2.0 and EF Core 2.0 or later -- make sure that **ASP.NET Core 1.1** is not selected.</span></span>

* <span data-ttu-id="44c5d-143">Emin olun **kimlik doğrulaması** ayarlanır **doğrulaması yok**.</span><span class="sxs-lookup"><span data-stu-id="44c5d-143">Make sure **Authentication** is set to **No Authentication**.</span></span>

* <span data-ttu-id="44c5d-144">**Tamam**’a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="44c5d-144">Click **OK**</span></span>

  ![Yeni ASP.NET projesi iletişim kutusu](intro/_static/new-aspnet.png)

## <a name="set-up-the-site-style"></a><span data-ttu-id="44c5d-146">Site stil ayarlama</span><span class="sxs-lookup"><span data-stu-id="44c5d-146">Set up the site style</span></span>

<span data-ttu-id="44c5d-147">Birkaç basit değişiklikler sitesi menüsü, Düzen ve giriş sayfası ayarlar.</span><span class="sxs-lookup"><span data-stu-id="44c5d-147">A few simple changes will set up the site menu, layout, and home page.</span></span>

<span data-ttu-id="44c5d-148">Açık *Views/Shared/_Layout.cshtml* ve aşağıdaki değişiklikleri yapın:</span><span class="sxs-lookup"><span data-stu-id="44c5d-148">Open *Views/Shared/_Layout.cshtml* and make the following changes:</span></span>

* <span data-ttu-id="44c5d-149">Her oluşumu "ContosoUniversity", "Contoso University" değiştirin.</span><span class="sxs-lookup"><span data-stu-id="44c5d-149">Change each occurrence of "ContosoUniversity" to "Contoso University".</span></span> <span data-ttu-id="44c5d-150">Üç oluşum vardır.</span><span class="sxs-lookup"><span data-stu-id="44c5d-150">There are three occurrences.</span></span>

* <span data-ttu-id="44c5d-151">Menü girişlerini eklemek **Öğrenciler**, **kurslar**, **Eğitmen**, ve **Departmanlar**ve silme **kişi** menü girişi.</span><span class="sxs-lookup"><span data-stu-id="44c5d-151">Add menu entries for **Students**, **Courses**, **Instructors**, and **Departments**, and delete the **Contact** menu entry.</span></span>

<span data-ttu-id="44c5d-152">Değişiklikler vurgulanır.</span><span class="sxs-lookup"><span data-stu-id="44c5d-152">The changes are highlighted.</span></span>

[!code-cshtml[](intro/samples/cu/Views/Shared/_Layout.cshtml?highlight=6,30,36-39,48)]

<span data-ttu-id="44c5d-153">İçinde *Views/Home/Index.cshtml*, dosyanın içeriğini bu uygulamayla ilgili metin ile ASP.NET MVC hakkında metni değiştirmek için aşağıdaki kod ile değiştirin:</span><span class="sxs-lookup"><span data-stu-id="44c5d-153">In *Views/Home/Index.cshtml*, replace the contents of the file with the following code to replace the text about ASP.NET and MVC with text about this application:</span></span>

[!code-cshtml[](intro/samples/cu/Views/Home/Index.cshtml)]

<span data-ttu-id="44c5d-154">Projeyi çalıştırın veya seçmek için CTRL + F5 tuşuna basın **hata ayıklama > hata ayıklama olmadan Başlat** menüsünde.</span><span class="sxs-lookup"><span data-stu-id="44c5d-154">Press CTRL+F5 to run the project or choose **Debug > Start Without Debugging** from the menu.</span></span> <span data-ttu-id="44c5d-155">Bu öğreticiler oluşturacaksınız sayfalar için sekmelerle giriş sayfasına bakın.</span><span class="sxs-lookup"><span data-stu-id="44c5d-155">You see the home page with tabs for the pages you'll create in these tutorials.</span></span>

![Contoso University giriş sayfası](intro/_static/home-page.png)

## <a name="entity-framework-core-nuget-packages"></a><span data-ttu-id="44c5d-157">Entity Framework Core NuGet paketleri</span><span class="sxs-lookup"><span data-stu-id="44c5d-157">Entity Framework Core NuGet packages</span></span>

<span data-ttu-id="44c5d-158">Bir projeye EF çekirdek desteği eklemek için hedeflemek istediğiniz veritabanı sağlayıcısı yükleyin.</span><span class="sxs-lookup"><span data-stu-id="44c5d-158">To add EF Core support to a project, install the database provider that you want to target.</span></span> <span data-ttu-id="44c5d-159">Bu öğreticide SQL Server kullanır ve sağlayıcı paketi [Microsoft.EntityFrameworkCore.SqlServer](https://www.nuget.org/packages/Microsoft.EntityFrameworkCore.SqlServer/).</span><span class="sxs-lookup"><span data-stu-id="44c5d-159">This tutorial uses SQL Server, and the provider package is [Microsoft.EntityFrameworkCore.SqlServer](https://www.nuget.org/packages/Microsoft.EntityFrameworkCore.SqlServer/).</span></span> <span data-ttu-id="44c5d-160">Bu paket dahil [Microsoft.AspNetCore.All](xref:fundamentals/metapackage) yüklemek zorunda kalmamak için metapackage.</span><span class="sxs-lookup"><span data-stu-id="44c5d-160">This package is included in the [Microsoft.AspNetCore.All](xref:fundamentals/metapackage) metapackage, so you don't have to install it.</span></span>

<span data-ttu-id="44c5d-161">Bu paketi ve bağımlılıklarını (`Microsoft.EntityFrameworkCore` ve `Microsoft.EntityFrameworkCore.Relational`) EF çalışma zamanı desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="44c5d-161">This package and its dependencies (`Microsoft.EntityFrameworkCore` and `Microsoft.EntityFrameworkCore.Relational`) provide runtime support for EF.</span></span> <span data-ttu-id="44c5d-162">Bir araç paketi ekleyeceksiniz daha sonra [geçişler](migrations.md) Öğreticisi.</span><span class="sxs-lookup"><span data-stu-id="44c5d-162">You'll add a tooling package later, in the [Migrations](migrations.md) tutorial.</span></span> 

<span data-ttu-id="44c5d-163">Entity Framework Çekirdek için kullanılabilir olan diğer veritabanı sağlayıcıları hakkında daha fazla bilgi için bkz: [veritabanı sağlayıcıları](https://docs.microsoft.com/ef/core/providers/).</span><span class="sxs-lookup"><span data-stu-id="44c5d-163">For information about other database providers that are available for Entity Framework Core, see [Database providers](https://docs.microsoft.com/ef/core/providers/).</span></span>

## <a name="create-the-data-model"></a><span data-ttu-id="44c5d-164">Veri modeli oluşturma</span><span class="sxs-lookup"><span data-stu-id="44c5d-164">Create the data model</span></span>

<span data-ttu-id="44c5d-165">Sonraki Contoso University uygulama için varlık sınıfları oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="44c5d-165">Next you'll create entity classes for the Contoso University application.</span></span> <span data-ttu-id="44c5d-166">Aşağıdaki üç varlık ile başlayacağız.</span><span class="sxs-lookup"><span data-stu-id="44c5d-166">You'll start with the following three entities.</span></span>

![İndirmelere kayıt Öğrenci veri modeli diyagramı](intro/_static/data-model-diagram.png)

<span data-ttu-id="44c5d-168">Arasında bir-çok ilişkisi olduğundan `Student` ve `Enrollment` varlıkları ve arasında bir-çok ilişkisi olduğundan `Course` ve `Enrollment` varlıklar.</span><span class="sxs-lookup"><span data-stu-id="44c5d-168">There's a one-to-many relationship between `Student` and `Enrollment` entities, and there's a one-to-many relationship between `Course` and `Enrollment` entities.</span></span> <span data-ttu-id="44c5d-169">Diğer bir deyişle, öğrencinin herhangi bir sayıda kurslar kaydedilebilir ve bir indirmelere içinde kayıtlı Öğrenciler herhangi bir sayıda olabilir.</span><span class="sxs-lookup"><span data-stu-id="44c5d-169">In other words, a student can be enrolled in any number of courses, and a course can have any number of students enrolled in it.</span></span>

<span data-ttu-id="44c5d-170">Aşağıdaki bölümlerde bu varlıkların her biri için bir sınıf oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="44c5d-170">In the following sections you'll create a class for each one of these entities.</span></span>

### <a name="the-student-entity"></a><span data-ttu-id="44c5d-171">Öğrenci varlık</span><span class="sxs-lookup"><span data-stu-id="44c5d-171">The Student entity</span></span>

![Öğrenci varlık diyagramı](intro/_static/student-entity.png)

<span data-ttu-id="44c5d-173">İçinde *modelleri* klasörünü adlı bir sınıf dosyası oluşturma *Student.cs* ve şablon kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="44c5d-173">In the *Models* folder, create a class file named *Student.cs* and replace the template code with the following code.</span></span>

[!code-csharp[Main](intro/samples/cu/Models/Student.cs?name=snippet_Intro)]

<span data-ttu-id="44c5d-174">`ID` Özelliği, bu sınıfa karşılık gelen veritabanı tablosunun birincil anahtar sütunu hale gelir.</span><span class="sxs-lookup"><span data-stu-id="44c5d-174">The `ID` property will become the primary key column of the database table that corresponds to this class.</span></span> <span data-ttu-id="44c5d-175">Varsayılan olarak, Entity Framework adlı bir özellik yorumlar `ID` veya `classnameID` birincil anahtar olarak.</span><span class="sxs-lookup"><span data-stu-id="44c5d-175">By default, the Entity Framework interprets a property that's named `ID` or `classnameID` as the primary key.</span></span>

<span data-ttu-id="44c5d-176">`Enrollments` Özelliği bir gezinti özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="44c5d-176">The `Enrollments` property is a navigation property.</span></span> <span data-ttu-id="44c5d-177">Gezinti özellikleri bu varlıkla ilgili diğer varlıklar tutun.</span><span class="sxs-lookup"><span data-stu-id="44c5d-177">Navigation properties hold other entities that are related to this entity.</span></span> <span data-ttu-id="44c5d-178">Bu durumda, `Enrollments` özelliği bir `Student entity` tüm tutacak `Enrollment` için ilişkili olan varlıkların `Student` varlık.</span><span class="sxs-lookup"><span data-stu-id="44c5d-178">In this case, the `Enrollments` property of a `Student entity` will hold all of the `Enrollment` entities that are related to that `Student` entity.</span></span> <span data-ttu-id="44c5d-179">Diğer bir deyişle, belirli bir öğrenci satır, veritabanındaki iki kayıt (birincil anahtar değerini kendi StudentID yabancı anahtar sütunu, öğrencinin içeren satırları) ilişkili satırları sahiptir, `Student` varlığın `Enrollments` gezinti özelliği olanlar içerecek iki `Enrollment` varlıklar.</span><span class="sxs-lookup"><span data-stu-id="44c5d-179">In other words, if a given Student row in the database has two related Enrollment rows (rows that contain that student's primary key value in their StudentID foreign key column), that `Student` entity's `Enrollments` navigation property will contain those two `Enrollment` entities.</span></span>

<span data-ttu-id="44c5d-180">Bir gezinti özelliği (çok- veya -çok ilişkileri) olduğu gibi birden çok varlık tutarsanız türünü hangi girişleri eklenebilir, silinen ve gibi güncelleştirilmiş bir listesi olmalıdır `ICollection<T>`.</span><span class="sxs-lookup"><span data-stu-id="44c5d-180">If a navigation property can hold multiple entities (as in many-to-many or one-to-many relationships), its type must be a list in which entries can be added, deleted, and updated, such as `ICollection<T>`.</span></span>  <span data-ttu-id="44c5d-181">Belirleyebileceğiniz `ICollection<T>` veya gibi bir tür `List<T>` veya `HashSet<T>`.</span><span class="sxs-lookup"><span data-stu-id="44c5d-181">You can specify `ICollection<T>` or a type such as `List<T>` or `HashSet<T>`.</span></span> <span data-ttu-id="44c5d-182">Belirtirseniz `ICollection<T>`, EF oluşturur bir `HashSet<T>` varsayılan koleksiyon.</span><span class="sxs-lookup"><span data-stu-id="44c5d-182">If you specify `ICollection<T>`, EF creates a `HashSet<T>` collection by default.</span></span>

### <a name="the-enrollment-entity"></a><span data-ttu-id="44c5d-183">Kayıt varlık</span><span class="sxs-lookup"><span data-stu-id="44c5d-183">The Enrollment entity</span></span>

![Kayıt varlık diyagramı](intro/_static/enrollment-entity.png)

<span data-ttu-id="44c5d-185">İçinde *modelleri* klasörü oluşturmak *Enrollment.cs* ve var olan kodu aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="44c5d-185">In the *Models* folder, create *Enrollment.cs* and replace the existing code with the following code:</span></span>

[!code-csharp[Main](intro/samples/cu/Models/Enrollment.cs?name=snippet_Intro)]

<span data-ttu-id="44c5d-186">`EnrollmentID` Birincil anahtar özelliği olacaktır; bu varlığı kullanan `classnameID` yerine desen `ID` yazarken kendi başına gördüğünüz `Student` varlık.</span><span class="sxs-lookup"><span data-stu-id="44c5d-186">The `EnrollmentID` property will be the primary key; this entity uses the `classnameID` pattern instead of `ID` by itself as you saw in the `Student` entity.</span></span> <span data-ttu-id="44c5d-187">Normalde bir desen seçin ve veri modelinizi kullanmak.</span><span class="sxs-lookup"><span data-stu-id="44c5d-187">Ordinarily you would choose one pattern and use it throughout your data model.</span></span> <span data-ttu-id="44c5d-188">Burada, değişim ya da Desen kullanabileceğiniz gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="44c5d-188">Here, the variation illustrates that you can use either pattern.</span></span> <span data-ttu-id="44c5d-189">İçinde bir [sonraki öğretici](inheritance.md), nasıl classname Kimliğini kullanarak, veri modelinde devralma uygulamak kolaylaştırır görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="44c5d-189">In a [later tutorial](inheritance.md), you'll see how using ID without classname makes it easier to implement inheritance in the data model.</span></span>

<span data-ttu-id="44c5d-190">`Grade` Özelliği bir `enum`.</span><span class="sxs-lookup"><span data-stu-id="44c5d-190">The `Grade` property is an `enum`.</span></span> <span data-ttu-id="44c5d-191">Soru işareti sonra `Grade` türü bildirimi gösterir `Grade` özelliği boş değer atanabilir.</span><span class="sxs-lookup"><span data-stu-id="44c5d-191">The question mark after the `Grade` type declaration indicates that the `Grade` property is nullable.</span></span> <span data-ttu-id="44c5d-192">Null bir düzeyde bir sıfır ataması farklı.--null anlamına gelir bir düzeyde bilinen değil veya henüz atanmamış.</span><span class="sxs-lookup"><span data-stu-id="44c5d-192">A grade that's null is different from a zero grade -- null means a grade isn't known or hasn't been assigned yet.</span></span>

<span data-ttu-id="44c5d-193">`StudentID` Özelliği bir yabancı anahtar ve karşılık gelen gezinme özelliğini `Student`.</span><span class="sxs-lookup"><span data-stu-id="44c5d-193">The `StudentID` property is a foreign key, and the corresponding navigation property is `Student`.</span></span> <span data-ttu-id="44c5d-194">Bir `Enrollment` varlıktır biriyle ilişkili `Student` özelliği yalnızca tek bir tutmak için varlık `Student` varlık (aksine `Student.Enrollments` gezinti özelliği gördüğünüz daha önceki sürümlerde, birden çok tutabilir `Enrollment` varlıklar).</span><span class="sxs-lookup"><span data-stu-id="44c5d-194">An `Enrollment` entity is associated with one `Student` entity, so the property can only hold a single `Student` entity (unlike the `Student.Enrollments` navigation property you saw earlier, which can hold multiple `Enrollment` entities).</span></span>

<span data-ttu-id="44c5d-195">`CourseID` Özelliği bir yabancı anahtar ve karşılık gelen gezinme özelliğini `Course`.</span><span class="sxs-lookup"><span data-stu-id="44c5d-195">The `CourseID` property is a foreign key, and the corresponding navigation property is `Course`.</span></span> <span data-ttu-id="44c5d-196">Bir `Enrollment` varlıktır biriyle ilişkili `Course` varlık.</span><span class="sxs-lookup"><span data-stu-id="44c5d-196">An `Enrollment` entity is associated with one `Course` entity.</span></span>

<span data-ttu-id="44c5d-197">Entity Framework onu ise bu özellik bir yabancı anahtar özellik olarak yorumlar `<navigation property name><primary key property name>` (örneğin, `StudentID` için `Student` gezinti özelliği bu yana `Student` varlığın birincil anahtarının `ID`).</span><span class="sxs-lookup"><span data-stu-id="44c5d-197">Entity Framework interprets a property as a foreign key property if it's named `<navigation property name><primary key property name>` (for example, `StudentID` for the `Student` navigation property since the `Student` entity's primary key is `ID`).</span></span> <span data-ttu-id="44c5d-198">Yabancı anahtar özellikleri de adlı yalnızca `<primary key property name>` (örneğin, `CourseID` beri `Course` varlığın birincil anahtarının `CourseID`).</span><span class="sxs-lookup"><span data-stu-id="44c5d-198">Foreign key properties can also be named simply `<primary key property name>` (for example, `CourseID` since the `Course` entity's primary key is `CourseID`).</span></span>

### <a name="the-course-entity"></a><span data-ttu-id="44c5d-199">İndirmelere varlık</span><span class="sxs-lookup"><span data-stu-id="44c5d-199">The Course entity</span></span>

![İndirmelere varlık diyagramı](intro/_static/course-entity.png)

<span data-ttu-id="44c5d-201">İçinde *modelleri* klasörü oluşturmak *Course.cs* ve var olan kodu aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="44c5d-201">In the *Models* folder, create *Course.cs* and replace the existing code with the following code:</span></span>

[!code-csharp[Main](intro/samples/cu/Models/Course.cs?name=snippet_Intro)]

<span data-ttu-id="44c5d-202">`Enrollments` Özelliği bir gezinti özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="44c5d-202">The `Enrollments` property is a navigation property.</span></span> <span data-ttu-id="44c5d-203">A `Course` varlık herhangi bir sayıda için ilgili olabileceğini `Enrollment` varlıklar.</span><span class="sxs-lookup"><span data-stu-id="44c5d-203">A `Course` entity can be related to any number of `Enrollment` entities.</span></span>

<span data-ttu-id="44c5d-204">Daha fazla hakkında dediğimiz `DatabaseGenerated` özniteliğini bir [sonraki öğretici](complex-data-model.md) bu serideki.</span><span class="sxs-lookup"><span data-stu-id="44c5d-204">We'll say more about the `DatabaseGenerated` attribute in a [later tutorial](complex-data-model.md) in this series.</span></span> <span data-ttu-id="44c5d-205">Temel olarak, bu öznitelik indirmelere yerine için oluşturmak veritabanı birincil anahtarı girmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="44c5d-205">Basically, this attribute lets you enter the primary key for the course rather than having the database generate it.</span></span>

## <a name="create-the-database-context"></a><span data-ttu-id="44c5d-206">Veritabanı bağlamı oluşturma</span><span class="sxs-lookup"><span data-stu-id="44c5d-206">Create the Database Context</span></span>

<span data-ttu-id="44c5d-207">Verilen veri modeli için Entity Framework işlevselliği koordinatları ana veritabanı bağlamı sınıfının sınıftır.</span><span class="sxs-lookup"><span data-stu-id="44c5d-207">The main class that coordinates Entity Framework functionality for a given data model is the database context class.</span></span> <span data-ttu-id="44c5d-208">Bu sınıf türetme tarafından oluşturduğunuz `Microsoft.EntityFrameworkCore.DbContext` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="44c5d-208">You create this class by deriving from the `Microsoft.EntityFrameworkCore.DbContext` class.</span></span> <span data-ttu-id="44c5d-209">Kodunuzda hangi varlıkların veri modelinde bulunan belirtin.</span><span class="sxs-lookup"><span data-stu-id="44c5d-209">In your code you specify which entities are included in the data model.</span></span> <span data-ttu-id="44c5d-210">Ayrıca, belirli bir Entity Framework davranış özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44c5d-210">You can also customize certain Entity Framework behavior.</span></span> <span data-ttu-id="44c5d-211">Bu projede adlı sınıfı `SchoolContext`.</span><span class="sxs-lookup"><span data-stu-id="44c5d-211">In this project, the class is named `SchoolContext`.</span></span>

<span data-ttu-id="44c5d-212">Proje klasöründe adlı bir klasör oluşturun *veri*.</span><span class="sxs-lookup"><span data-stu-id="44c5d-212">In the project folder, create a folder named *Data*.</span></span>

<span data-ttu-id="44c5d-213">İçinde *veri* klasörü oluşturun adlı yeni bir sınıf dosya *SchoolContext.cs*ve şablon kodu aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="44c5d-213">In the *Data* folder create a new class file named *SchoolContext.cs*, and replace the template code with the following code:</span></span>

[!code-csharp[Main](intro/samples/cu/Data/SchoolContext.cs?name=snippet_Intro)]

<span data-ttu-id="44c5d-214">Bu kod oluşturur bir `DbSet` özelliği her bir varlık kümesi.</span><span class="sxs-lookup"><span data-stu-id="44c5d-214">This code creates a `DbSet` property for each entity set.</span></span> <span data-ttu-id="44c5d-215">Entity Framework terminoloji, bir varlık kümesine genellikle bir veritabanı tablosuna karşılık gelir ve bir varlık tablosunda bir satırı karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="44c5d-215">In Entity Framework terminology, an entity set typically corresponds to a database table, and an entity corresponds to a row in the table.</span></span>

<span data-ttu-id="44c5d-216">Atlanmış `DbSet<Enrollment>` ve `DbSet<Course>` deyimleri ve çalışır.</span><span class="sxs-lookup"><span data-stu-id="44c5d-216">You could have omitted the `DbSet<Enrollment>` and `DbSet<Course>` statements and it would work the same.</span></span> <span data-ttu-id="44c5d-217">Entity Framework bunları örtük olarak dahil `Student` varlık başvuruları `Enrollment` varlık ve `Enrollment` varlık başvuruları `Course` varlık.</span><span class="sxs-lookup"><span data-stu-id="44c5d-217">The Entity Framework would include them implicitly because the `Student` entity references the `Enrollment` entity and the `Enrollment` entity references the `Course` entity.</span></span>

<span data-ttu-id="44c5d-218">Veritabanı oluşturulduğunda EF aynı adlara sahip tablolar oluşturur `DbSet` özellik adları.</span><span class="sxs-lookup"><span data-stu-id="44c5d-218">When the database is created, EF creates tables that have names the same as the `DbSet` property names.</span></span> <span data-ttu-id="44c5d-219">Koleksiyonlar için özellik adları olan genellikle çoğul (Öğrenciler yerine Öğrenci), ancak geliştiriciler katılmıyorum olup tablo adları veya pluralized hakkında.</span><span class="sxs-lookup"><span data-stu-id="44c5d-219">Property names for collections are typically plural (Students rather than Student), but developers disagree about whether table names should be pluralized or not.</span></span> <span data-ttu-id="44c5d-220">Bu öğreticileri için DbContext tekil tablo adları belirterek varsayılan davranışı geçersiz kılma.</span><span class="sxs-lookup"><span data-stu-id="44c5d-220">For these tutorials you'll override the default behavior by specifying singular table names in the DbContext.</span></span> <span data-ttu-id="44c5d-221">Bunu yapmak için en son DbSet özellik sonra aşağıdaki vurgulanmış kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="44c5d-221">To do that, add the following highlighted code after the last DbSet property.</span></span>

[!code-csharp[Main](intro/samples/cu/Data/SchoolContext.cs?name=snippet_TableNames&highlight=16-21)]

## <a name="register-the-context-with-dependency-injection"></a><span data-ttu-id="44c5d-222">Bağlam bağımlılık ekleme ile kaydetme</span><span class="sxs-lookup"><span data-stu-id="44c5d-222">Register the context with dependency injection</span></span>

<span data-ttu-id="44c5d-223">ASP.NET Core uygulayan [bağımlılık ekleme](../../fundamentals/dependency-injection.md) varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="44c5d-223">ASP.NET Core implements [dependency injection](../../fundamentals/dependency-injection.md) by default.</span></span> <span data-ttu-id="44c5d-224">Hizmetleri (örneğin, EF veritabanı bağlamı), uygulama başlatma sırasında bağımlılık ekleme ile kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="44c5d-224">Services (such as the EF database context) are registered with dependency injection during application startup.</span></span> <span data-ttu-id="44c5d-225">Bu Hizmetleri (örneğin, MVC denetleyicileri) gerektiren bileşenler bu hizmetlere Oluşturucu parametreleri yoluyla sağlanır.</span><span class="sxs-lookup"><span data-stu-id="44c5d-225">Components that require these services (such as MVC controllers) are provided these services via constructor parameters.</span></span> <span data-ttu-id="44c5d-226">Daha sonra Bu öğreticide bir bağlam örneğini alır denetleyicisi Oluşturucusu kod görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="44c5d-226">You'll see the controller constructor code that gets a context instance later in this tutorial.</span></span>

<span data-ttu-id="44c5d-227">Kaydetmek için `SchoolContext` bir hizmet olarak açmak *haline*, vurgulanan satırlar ekleyin `ConfigureServices` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="44c5d-227">To register `SchoolContext` as a service, open *Startup.cs*, and add the highlighted lines to the `ConfigureServices` method.</span></span>

[!code-csharp[Main](intro/samples/cu/Startup.cs?name=snippet_SchoolContext&highlight=3-4)]

<span data-ttu-id="44c5d-228">Bağlantı dizesinin adını bağlamına üzerinde bir yöntemini çağırarak geçirilen bir `DbContextOptionsBuilder` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="44c5d-228">The name of the connection string is passed in to the context by calling a method on a `DbContextOptionsBuilder` object.</span></span> <span data-ttu-id="44c5d-229">Yerel geliştirme için [ASP.NET Core yapılandırma sistemi](xref:fundamentals/configuration/index) bağlantı dizesinden okur *appsettings.json* dosya.</span><span class="sxs-lookup"><span data-stu-id="44c5d-229">For local development, the [ASP.NET Core configuration system](xref:fundamentals/configuration/index) reads the connection string from the *appsettings.json* file.</span></span>

<span data-ttu-id="44c5d-230">Ekleme `using` deyimleri için `ContosoUniversity.Data` ve `Microsoft.EntityFrameworkCore` ad alanları ve projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="44c5d-230">Add `using` statements for `ContosoUniversity.Data`  and `Microsoft.EntityFrameworkCore` namespaces, and then build the project.</span></span>

[!code-csharp[Main](intro/samples/cu/Startup.cs?name=snippet_Usings)]

<span data-ttu-id="44c5d-231">Açık *appsettings.json* dosyası ve bir bağlantı dizesi aşağıdaki örnekte gösterildiği gibi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="44c5d-231">Open the *appsettings.json* file and add a connection string as shown in the following example.</span></span>

[!code-json[](./intro/samples/cu/appsettings1.json?highlight=2-4)]

### <a name="sql-server-express-localdb"></a><span data-ttu-id="44c5d-232">SQL Server Express LocalDB</span><span class="sxs-lookup"><span data-stu-id="44c5d-232">SQL Server Express LocalDB</span></span>

<span data-ttu-id="44c5d-233">Bir SQL Server yerel veritabanı veritabanı bağlantı dizesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="44c5d-233">The connection string specifies a SQL Server LocalDB database.</span></span> <span data-ttu-id="44c5d-234">Yerel veritabanı, SQL Server Express veritabanı Motoru'nu hafif sürümüdür ve uygulama geliştirme, üretim kullanımı için amaçlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="44c5d-234">LocalDB is a lightweight version of the SQL Server Express Database Engine and is intended for application development, not production use.</span></span> <span data-ttu-id="44c5d-235">Yerel veritabanı isteğe bağlı olarak başlar ve bu yüzden karmaşık yapılandırma kullanıcı modunda çalışır.</span><span class="sxs-lookup"><span data-stu-id="44c5d-235">LocalDB starts on demand and runs in user mode, so there is no complex configuration.</span></span> <span data-ttu-id="44c5d-236">Varsayılan olarak, yerel veritabanı oluşturur *.mdf* veritabanı dosyası `C:/Users/<user>` dizin.</span><span class="sxs-lookup"><span data-stu-id="44c5d-236">By default, LocalDB creates *.mdf* database files in the `C:/Users/<user>` directory.</span></span>

## <a name="add-code-to-initialize-the-database-with-test-data"></a><span data-ttu-id="44c5d-237">Test verileri veritabanıyla başlatmak için kod ekleme</span><span class="sxs-lookup"><span data-stu-id="44c5d-237">Add code to initialize the database with test data</span></span>

<span data-ttu-id="44c5d-238">Entity Framework boş bir veritabanı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="44c5d-238">The Entity Framework will create an empty database for you.</span></span>  <span data-ttu-id="44c5d-239">Bu bölümde, test verileri ile doldurmak için veritabanı oluşturulduktan sonra çağrılan yöntemi yazın.</span><span class="sxs-lookup"><span data-stu-id="44c5d-239">In this section, you write a method that is called after the database is created in order to populate it with test data.</span></span>

<span data-ttu-id="44c5d-240">Burada kullanacağınız `EnsureCreated` otomatik olarak veritabanını oluşturmak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="44c5d-240">Here you'll use the `EnsureCreated` method to automatically create the database.</span></span> <span data-ttu-id="44c5d-241">İçinde bir [sonraki öğretici](migrations.md) model değişiklikleri bırakarak ve veritabanını yeniden oluşturma yerine veritabanı şeması değiştirmek için Code First Migrations kullanılarak nasıl ele alınacağını görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="44c5d-241">In a [later tutorial](migrations.md) you'll see how to handle model changes by using Code First Migrations to change the database schema instead of dropping and re-creating the database.</span></span>

<span data-ttu-id="44c5d-242">İçinde *veri* klasörünü adlı yeni bir sınıf dosyası oluşturun *DbInitializer.cs* şablonu kodu gerekli olduğunda oluşturulacak bir veritabanı neden olan aşağıdaki kodla değiştirin ve yükleri test yeni verileri Veritabanı.</span><span class="sxs-lookup"><span data-stu-id="44c5d-242">In the *Data* folder, create a new class file named *DbInitializer.cs* and replace the template code with the following code, which causes a database to be created when needed and loads test data into the new database.</span></span>

[!code-csharp[Main](intro/samples/cu/Data/DbInitializer.cs?name=snippet_Intro)]

<span data-ttu-id="44c5d-243">Kod veritabanındaki tüm Öğrenciler varsa ve bu değilse, veritabanını yeni ve test verilerle sağlanmış gerekiyor, varsayar denetler.</span><span class="sxs-lookup"><span data-stu-id="44c5d-243">The code checks if there are any students in the database, and if not, it assumes the database is new and needs to be seeded with test data.</span></span>  <span data-ttu-id="44c5d-244">Diziye test verileri yükler yerine `List<T>` performansı iyileştirmek için koleksiyonları.</span><span class="sxs-lookup"><span data-stu-id="44c5d-244">It loads test data into arrays rather than `List<T>` collections to optimize performance.</span></span>

<span data-ttu-id="44c5d-245">İçinde *Program.cs*, değişiklik `Main` yöntemi uygulama başlangıcında üzerinde aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="44c5d-245">In *Program.cs*, modify the `Main` method to do the following on application startup:</span></span>

* <span data-ttu-id="44c5d-246">Bir veritabanı bağlamını örneği bağımlılık ekleme kapsayıcıdan alın.</span><span class="sxs-lookup"><span data-stu-id="44c5d-246">Get a database context instance from the dependency injection container.</span></span>
* <span data-ttu-id="44c5d-247">İçin bağlamı geçirme çekirdek yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="44c5d-247">Call the seed method, passing to it the context.</span></span>
* <span data-ttu-id="44c5d-248">Seed yöntemi yapıldığında bağlamını siler.</span><span class="sxs-lookup"><span data-stu-id="44c5d-248">Dispose the context when the seed method is done.</span></span>

[!code-csharp[Main](intro/samples/cu/Program.cs?name=snippet_Seed&highlight=3-20)]

<span data-ttu-id="44c5d-249">Ekleme `using` deyimleri:</span><span class="sxs-lookup"><span data-stu-id="44c5d-249">Add `using` statements:</span></span>

[!code-csharp[Main](intro/samples/cu/Program.cs?name=snippet_Usings)]

<span data-ttu-id="44c5d-250">Eski eğitimlerine benzer bir kod görebilirsiniz `Configure` yönteminde *haline*.</span><span class="sxs-lookup"><span data-stu-id="44c5d-250">In older tutorials, you may see similar code in the `Configure` method in *Startup.cs*.</span></span> <span data-ttu-id="44c5d-251">Kullanmanızı öneririz `Configure` yalnızca istek ardışık düzenini ayarlamak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="44c5d-251">We recommend that you use the `Configure` method only to set up the request pipeline.</span></span> <span data-ttu-id="44c5d-252">Uygulama başlangıç koduna ait `Main` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="44c5d-252">Application startup code belongs in the `Main` method.</span></span>

<span data-ttu-id="44c5d-253">Şimdi uygulamayı çalıştırın ilk kez veritabanı oluşturulur ve test verilerle sağlanmış.</span><span class="sxs-lookup"><span data-stu-id="44c5d-253">Now the first time you run the application, the database will be created and seeded with test data.</span></span> <span data-ttu-id="44c5d-254">Veri modelinizi değiştirdiğinizde veritabanını silin, seed yöntemi güncelleştirin ve yeni bir veritabanı ile aynı şekilde afresh başlatın.</span><span class="sxs-lookup"><span data-stu-id="44c5d-254">Whenever you change your data model, you can delete the database, update your seed method, and start afresh with a new database the same way.</span></span> <span data-ttu-id="44c5d-255">Sonraki öğreticileri, veritabanı veri değişiklikleri, model silinmesi ve yeniden oluşturma, değiştirme görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="44c5d-255">In later tutorials, you'll see how to modify the database when the data model changes, without deleting and re-creating it.</span></span>

## <a name="create-a-controller-and-views"></a><span data-ttu-id="44c5d-256">Bir denetleyici ve görünümler oluşturma</span><span class="sxs-lookup"><span data-stu-id="44c5d-256">Create a controller and views</span></span>

<span data-ttu-id="44c5d-257">Ardından, MVC denetleyicisi ve EF sorgu ve veri kaydetmek için kullanacağı görünümleri eklemek için Visual Studio'da yapı iskelesi altyapısı kullanacağınız.</span><span class="sxs-lookup"><span data-stu-id="44c5d-257">Next, you'll use the scaffolding engine in Visual Studio to add an MVC controller and views that will use EF to query and save data.</span></span>

<span data-ttu-id="44c5d-258">CRUD eylem yöntemleri ve görünümler otomatik olarak oluşturulmasını yapı iskelesi olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="44c5d-258">The automatic creation of CRUD action methods and views is known as scaffolding.</span></span> <span data-ttu-id="44c5d-259">İskele kurulmuş kodu oluşturulan kod genellikle değiştirmeyin ancak kendi gereksinimlerinize uyacak şekilde değiştirebilirsiniz bir başlangıç noktası kod oluşturma farklıdır.</span><span class="sxs-lookup"><span data-stu-id="44c5d-259">Scaffolding differs from code generation in that the scaffolded code is a starting point that you can modify to suit your own requirements, whereas you typically don't modify generated code.</span></span> <span data-ttu-id="44c5d-260">Oluşturulan kodun özelleştirme gerektiğinde, değişiklik olduğunda kodu yeniden oluşturmak veya kısmi sınıflar kullanın.</span><span class="sxs-lookup"><span data-stu-id="44c5d-260">When you need to customize generated code, you use partial classes or you regenerate the code when things change.</span></span>

* <span data-ttu-id="44c5d-261">Sağ **denetleyicileri** klasöründe **Çözüm Gezgini** seçip **Ekle > Yeni iskele kurulmuş öğe**.</span><span class="sxs-lookup"><span data-stu-id="44c5d-261">Right-click the **Controllers** folder in **Solution Explorer** and select **Add > New Scaffolded Item**.</span></span>

* <span data-ttu-id="44c5d-262">İçinde **MVC bağımlılıkları ekleyin** iletişim kutusunda **en az bağımlılıkları**seçip **Ekle**.</span><span class="sxs-lookup"><span data-stu-id="44c5d-262">In the **Add MVC Dependencies** dialog, select **Minimal Dependencies**, and select **Add**.</span></span>

  ![Bağımlılıkları ekleyin.](intro/_static/add-depend.png)

  <span data-ttu-id="44c5d-264">Visual Studio bir denetleyici iskele için gerekli bağımlılıkların ekler.</span><span class="sxs-lookup"><span data-stu-id="44c5d-264">Visual Studio adds the dependencies needed to scaffold a controller.</span></span> <span data-ttu-id="44c5d-265">Yalnızca proje dosyasında eklenmesi değişikliktir `Microsoft.VisualStudio.Web.CodeGeneration.Design` paket.</span><span class="sxs-lookup"><span data-stu-id="44c5d-265">The only change in the project file is the addition of the `Microsoft.VisualStudio.Web.CodeGeneration.Design` package.</span></span>

  <span data-ttu-id="44c5d-266">A *ScaffoldingReadMe.txt* dosyası oluşturuldu, silebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44c5d-266">A *ScaffoldingReadMe.txt* file is created which you can delete.</span></span>

* <span data-ttu-id="44c5d-267">Bir kez daha sağ **denetleyicileri** klasöründe **Çözüm Gezgini** seçip **Ekle > Yeni iskele kurulmuş öğe**.</span><span class="sxs-lookup"><span data-stu-id="44c5d-267">Once again, right-click the **Controllers** folder in **Solution Explorer** and select **Add > New Scaffolded Item**.</span></span>

* <span data-ttu-id="44c5d-268">İçinde **İskele Ekle** iletişim kutusunda:</span><span class="sxs-lookup"><span data-stu-id="44c5d-268">In the **Add Scaffold** dialog box:</span></span>

  * <span data-ttu-id="44c5d-269">Seçin **Entity Framework kullanarak görünümleri ile MVC denetleyicisi**.</span><span class="sxs-lookup"><span data-stu-id="44c5d-269">Select **MVC controller with views, using Entity Framework**.</span></span>

  * <span data-ttu-id="44c5d-270">**Ekle**'yi tıklatın.</span><span class="sxs-lookup"><span data-stu-id="44c5d-270">Click **Add**.</span></span>

* <span data-ttu-id="44c5d-271">İçinde **denetleyici Ekle** iletişim kutusunda:</span><span class="sxs-lookup"><span data-stu-id="44c5d-271">In the **Add Controller** dialog box:</span></span>

  * <span data-ttu-id="44c5d-272">İçinde **Model sınıfı** seçin **Öğrenci**.</span><span class="sxs-lookup"><span data-stu-id="44c5d-272">In **Model class** select **Student**.</span></span>

  * <span data-ttu-id="44c5d-273">İçinde **veri bağlamı sınıfı** seçin **SchoolContext**.</span><span class="sxs-lookup"><span data-stu-id="44c5d-273">In **Data context class** select **SchoolContext**.</span></span>

  * <span data-ttu-id="44c5d-274">Varsayılanı kabul **StudentsController** adı.</span><span class="sxs-lookup"><span data-stu-id="44c5d-274">Accept the default **StudentsController** as the name.</span></span>

  * <span data-ttu-id="44c5d-275">**Ekle**'yi tıklatın.</span><span class="sxs-lookup"><span data-stu-id="44c5d-275">Click **Add**.</span></span>

  ![İskele Öğrenci](intro/_static/scaffold-student.png)

  <span data-ttu-id="44c5d-277">Tıkladığınızda **Ekle**, Visual Studio yapı iskelesi motoru oluşturur bir *StudentsController.cs* dosyası ve bir görünüm kümesi (*.cshtml* dosyaları) Denetleyici ile çalışır.</span><span class="sxs-lookup"><span data-stu-id="44c5d-277">When you click **Add**, the Visual Studio scaffolding engine creates a *StudentsController.cs* file and a set of views (*.cshtml* files) that work with the controller.</span></span>

<span data-ttu-id="44c5d-278">(El ile oluşturmayın varsa yapı iskelesi altyapısı ayrıca veritabanı bağlamı için oluşturabilirsiniz önce bu öğreticide daha önce yaptığınız gibi.</span><span class="sxs-lookup"><span data-stu-id="44c5d-278">(The scaffolding engine can also create the database context for you if you don't create it manually first as you did earlier for this tutorial.</span></span> <span data-ttu-id="44c5d-279">Yeni bir bağlam sınıfta belirtebilirsiniz **denetleyici Ekle** kutusunun sağ tarafındaki artı işaretine tıklayarak **veri bağlamı sınıfı**.</span><span class="sxs-lookup"><span data-stu-id="44c5d-279">You can specify a new context class in the **Add Controller** box by clicking the plus sign to the right of **Data context class**.</span></span>  <span data-ttu-id="44c5d-280">Visual Studio sonra oluşturacak, `DbContext` sınıfı denetleyici ve görünüm yanı sıra.)</span><span class="sxs-lookup"><span data-stu-id="44c5d-280">Visual Studio will then create your `DbContext` class as well as the controller and views.)</span></span>

<span data-ttu-id="44c5d-281">Denetleyici sürdüğünü fark edeceksiniz bir `SchoolContext` Oluşturucusu parametre olarak.</span><span class="sxs-lookup"><span data-stu-id="44c5d-281">You'll notice that the controller takes a `SchoolContext` as a constructor parameter.</span></span>

[!code-csharp[Main](intro/samples/cu/Controllers/StudentsController.cs?name=snippet_Context&highlight=5,7,9)]

<span data-ttu-id="44c5d-282">ASP.NET bağımlılık ekleme örneğini geçirerek dikkatli `SchoolContext` denetleyicisi içine.</span><span class="sxs-lookup"><span data-stu-id="44c5d-282">ASP.NET dependency injection will take care of passing an instance of `SchoolContext` into the controller.</span></span> <span data-ttu-id="44c5d-283">Uygulamasında yapılandırılmış *haline* önceki dosya.</span><span class="sxs-lookup"><span data-stu-id="44c5d-283">You configured that in the *Startup.cs* file earlier.</span></span>

<span data-ttu-id="44c5d-284">Denetleyicisi içeren bir `Index` veritabanındaki tüm Öğrenciler görüntüler eylem yöntemi.</span><span class="sxs-lookup"><span data-stu-id="44c5d-284">The controller contains an `Index` action method, which displays all students in the database.</span></span> <span data-ttu-id="44c5d-285">Öğrenciler listesini yöntemi Öğrenciler varlık okuyarak kümesini alır `Students` veritabanı bağlam örneğinin özelliği:</span><span class="sxs-lookup"><span data-stu-id="44c5d-285">The method gets a list of students from the Students entity set by reading the `Students` property of the database context instance:</span></span>

[!code-csharp[Main](intro/samples/cu/Controllers/StudentsController.cs?name=snippet_ScaffoldedIndex&highlight=3)]

<span data-ttu-id="44c5d-286">Öğreticide daha sonra bu kodu zaman uyumsuz programlama öğeleri hakkında öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="44c5d-286">You'll learn about the asynchronous programming elements in this code later in the tutorial.</span></span>

<span data-ttu-id="44c5d-287">*Views/Students/Index.cshtml* görünüm bu listesi bir tabloda görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="44c5d-287">The *Views/Students/Index.cshtml* view displays this list in a table:</span></span>

[!code-cshtml[](intro/samples/cu/Views/Students/Index1.cshtml)]

<span data-ttu-id="44c5d-288">Projeyi çalıştırın veya seçmek için CTRL + F5 tuşuna basın **hata ayıklama > hata ayıklama olmadan Başlat** menüsünde.</span><span class="sxs-lookup"><span data-stu-id="44c5d-288">Press CTRL+F5 to run the project or choose **Debug > Start Without Debugging** from the menu.</span></span>

<span data-ttu-id="44c5d-289">Test verileri görmek için Öğrenciler sekmesini tıklatın, `DbInitializer.Initialize` eklenen yöntemi.</span><span class="sxs-lookup"><span data-stu-id="44c5d-289">Click the Students tab to see the test data that the `DbInitializer.Initialize` method inserted.</span></span> <span data-ttu-id="44c5d-290">Bağlı olarak nasıl dar tarayıcı pencerenizi, göreceğiniz `Student` sekmesini bağlantı sayfası veya üstündeki bağlantıyı görmek için sağ üst köşesindeki gezinti simgeyi tıklatın zorunda.</span><span class="sxs-lookup"><span data-stu-id="44c5d-290">Depending on how narrow your browser window is, you'll see the `Student` tab link at the top of the page or you'll have to click the navigation icon in the upper right corner to see the link.</span></span>

![Contoso University giriş sayfası dar](intro/_static/home-page-narrow.png)

![Öğrenciler dizin sayfası](intro/_static/students-index.png)

## <a name="view-the-database"></a><span data-ttu-id="44c5d-293">Veritabanı görüntüleyin</span><span class="sxs-lookup"><span data-stu-id="44c5d-293">View the Database</span></span>

<span data-ttu-id="44c5d-294">Uygulama başlatıldığında `DbInitializer.Initialize` yöntem çağrılarını `EnsureCreated`.</span><span class="sxs-lookup"><span data-stu-id="44c5d-294">When you started the application, the `DbInitializer.Initialize` method calls `EnsureCreated`.</span></span> <span data-ttu-id="44c5d-295">EF gördüğünüz hiçbir veritabanı oluştu ve bu nedenle onu oluşturan bir sonra geri kalan `Initialize` yöntemi kodu veritabanı verilerle doldurulur.</span><span class="sxs-lookup"><span data-stu-id="44c5d-295">EF saw that there was no database and so it created one, then the remainder of the `Initialize` method code populated the database with data.</span></span> <span data-ttu-id="44c5d-296">Kullanabileceğiniz **SQL Server Nesne Gezgini** (Visual Studio veritabanı görüntülemek için SSOX).</span><span class="sxs-lookup"><span data-stu-id="44c5d-296">You can use **SQL Server Object Explorer** (SSOX) to view the database in Visual Studio.</span></span>

<span data-ttu-id="44c5d-297">Tarayıcıyı kapatın.</span><span class="sxs-lookup"><span data-stu-id="44c5d-297">Close the browser.</span></span>

<span data-ttu-id="44c5d-298">SSOX penceresi açık değilse, dosyayı seçin **Görünüm** Visual Studio menüsünde.</span><span class="sxs-lookup"><span data-stu-id="44c5d-298">If the SSOX window isn't already open, select it from the **View** menu in Visual Studio.</span></span>

<span data-ttu-id="44c5d-299">SSOX içinde tıklatın **(localdb) \MSSQLLocalDB > veritabanları**, bağlantı dizesinde yer veritabanı adı için giriş'a tıklayın, *appsettings.json* dosya.</span><span class="sxs-lookup"><span data-stu-id="44c5d-299">In SSOX, click **(localdb)\MSSQLLocalDB > Databases**, and then click the entry for the database name that is in the connection string in your *appsettings.json* file.</span></span>

<span data-ttu-id="44c5d-300">Genişletme **tabloları** veritabanınızdaki tablolar görmek için düğüm.</span><span class="sxs-lookup"><span data-stu-id="44c5d-300">Expand the **Tables** node to see the tables in your database.</span></span>

![SSOX tablolarında](intro/_static/ssox-tables.png)

<span data-ttu-id="44c5d-302">Sağ **Öğrenci** tablosu ve'ı tıklatın **görünüm verilerini** oluşturulan sütunları ve tablosuna satır görmek için.</span><span class="sxs-lookup"><span data-stu-id="44c5d-302">Right-click the **Student** table and click **View Data** to see the columns that were created and the rows that were inserted into the table.</span></span>

![SSOX Öğrenci tabloda](intro/_static/ssox-student-table.png)

<span data-ttu-id="44c5d-304">*.Mdf* ve *.ldf* veritabanı dosyaları olan *C:\Users\<kullanıcıadınız >* klasör.</span><span class="sxs-lookup"><span data-stu-id="44c5d-304">The *.mdf* and *.ldf* database files are in the *C:\Users\<yourusername>* folder.</span></span>

<span data-ttu-id="44c5d-305">Aradığınız çünkü `EnsureCreated` uygulama başlangıç çalıştıran Başlatıcı yönteminde artık bir değişiklik yapabilir `Student` sınıfı, veritabanını silin, uygulamayı yeniden çalıştırın ve veritabanı otomatik olarak değişikliğinizin eşleşecek şekilde yeniden oluşturulmuş olabilir.</span><span class="sxs-lookup"><span data-stu-id="44c5d-305">Because you're calling `EnsureCreated` in the initializer method that runs on app start, you could now make a change to the `Student` class, delete the database, run the application again, and the database would automatically be re-created to match your change.</span></span> <span data-ttu-id="44c5d-306">Örneğin, eklerseniz bir `EmailAddress` özelliğine `Student` sınıfı, göreceksiniz yeni bir `EmailAddress` yeniden oluşturulan tablonun sütun.</span><span class="sxs-lookup"><span data-stu-id="44c5d-306">For example, if you add an `EmailAddress` property to the `Student` class, you'll see a new `EmailAddress` column in the re-created table.</span></span>

## <a name="conventions"></a><span data-ttu-id="44c5d-307">Kurallar</span><span class="sxs-lookup"><span data-stu-id="44c5d-307">Conventions</span></span>

<span data-ttu-id="44c5d-308">Sizin için tam bir veritabanı oluşturabilmek için Entity Framework sırayla yazma gerekiyordu kod miktarını kuralları veya Entity Framework yapar varsayımlar kullanımı nedeniyle düzeydedir.</span><span class="sxs-lookup"><span data-stu-id="44c5d-308">The amount of code you had to write in order for the Entity Framework to be able to create a complete database for you is minimal because of the use of conventions, or assumptions that the Entity Framework makes.</span></span>

* <span data-ttu-id="44c5d-309">Adlarını `DbSet` özellikleri Tablo adları olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="44c5d-309">The names of `DbSet` properties are used as table names.</span></span> <span data-ttu-id="44c5d-310">Tarafından başvurulan olmayan varlıklar için bir `DbSet` özelliği, varlık sınıfı adları tablo adları olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="44c5d-310">For entities not referenced by a `DbSet` property, entity class names are used as table names.</span></span>

* <span data-ttu-id="44c5d-311">Varlık özellik adlarını sütun adları için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="44c5d-311">Entity property names are used for column names.</span></span>

* <span data-ttu-id="44c5d-312">Kimliği veya classnameID adlı varlık özellikleri birincil anahtar özelliği kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="44c5d-312">Entity properties that are named ID or classnameID are recognized as primary key properties.</span></span>

* <span data-ttu-id="44c5d-313">Bu adlı bir özelliği bir yabancı anahtar özellik olarak yorumlanır  *<navigation property name> <primary key property name>*  (örneğin, `StudentID` için `Student` gezinti özelliği bu yana `Student` varlığın birincil anahtar `ID`).</span><span class="sxs-lookup"><span data-stu-id="44c5d-313">A property is interpreted as a foreign key property if it's named *<navigation property name><primary key property name>* (for example, `StudentID` for the `Student` navigation property since the `Student` entity's primary key is `ID`).</span></span> <span data-ttu-id="44c5d-314">Yabancı anahtar özellikleri de adlı yalnızca  *<primary key property name>*  (örneğin, `EnrollmentID` beri `Enrollment` varlığın birincil anahtarının `EnrollmentID`).</span><span class="sxs-lookup"><span data-stu-id="44c5d-314">Foreign key properties can also be named simply *<primary key property name>* (for example, `EnrollmentID` since the `Enrollment` entity's primary key is `EnrollmentID`).</span></span>

<span data-ttu-id="44c5d-315">Geleneksel davranışı geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="44c5d-315">Conventional behavior can be overridden.</span></span> <span data-ttu-id="44c5d-316">Örneğin, bu öğreticide daha önce anlatıldığı gibi tablo adları açıkça belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44c5d-316">For example, you can explicitly specify table names, as you saw earlier in this tutorial.</span></span> <span data-ttu-id="44c5d-317">Sütun adları Ayarla ve içinde anlatıldığı gibi herhangi bir özelliği birincil anahtarı veya yabancı anahtar olarak ayarlayın ve bir [sonraki öğretici](complex-data-model.md) bu serideki.</span><span class="sxs-lookup"><span data-stu-id="44c5d-317">And you can set column names and set any property as primary key or foreign key, as you'll see in a [later tutorial](complex-data-model.md) in this series.</span></span>

## <a name="asynchronous-code"></a><span data-ttu-id="44c5d-318">Zaman uyumsuz kodu</span><span class="sxs-lookup"><span data-stu-id="44c5d-318">Asynchronous code</span></span>

<span data-ttu-id="44c5d-319">Zaman uyumsuz programlama ASP.NET Core ve EF çekirdek için varsayılan moddur.</span><span class="sxs-lookup"><span data-stu-id="44c5d-319">Asynchronous programming is the default mode for ASP.NET Core and EF Core.</span></span>

<span data-ttu-id="44c5d-320">Bir web sunucusu kullanılabilir iş parçacıklarının sınırlı sayıda sahiptir ve yüksek yük durumlarda tüm kullanılabilir iş parçacıklarının kullanımda olabilir.</span><span class="sxs-lookup"><span data-stu-id="44c5d-320">A web server has a limited number of threads available, and in high load situations all of the available threads might be in use.</span></span> <span data-ttu-id="44c5d-321">Bu durum oluştuğunda sunucu yukarı serbest iş parçacığı kadar yeni istekleri işleyemiyor.</span><span class="sxs-lookup"><span data-stu-id="44c5d-321">When that happens, the server can't process new requests until the threads are freed up.</span></span> <span data-ttu-id="44c5d-322">G/ç tamamlamak bekliyorsunuz çünkü bunlar herhangi bir iş gerçekte yapmamanız sırasında zaman uyumlu koduyla birçok iş parçacığı bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="44c5d-322">With synchronous code, many threads may be tied up while they aren't actually doing any work because they're waiting for I/O to complete.</span></span> <span data-ttu-id="44c5d-323">Bir işlemin g/ç tamamlanması beklenirken zaman uyumsuz koduyla diğer istekleri işlemek için kullanılacak sunucuyu kaydınızı kendi iş parçacığı serbest bırakılır.</span><span class="sxs-lookup"><span data-stu-id="44c5d-323">With asynchronous code, when a process is waiting for I/O to complete, its thread is freed up for the server to use for processing other requests.</span></span> <span data-ttu-id="44c5d-324">Sonuç olarak, zaman uyumsuz kod sunucu kaynaklarını daha verimli bir şekilde kullanılmak üzere etkinleştirir ve sunucu gecikme olmadan daha fazla trafik işlemek için etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="44c5d-324">As a result, asynchronous code enables server resources to be used more efficiently, and the server is enabled to handle more traffic without delays.</span></span>

<span data-ttu-id="44c5d-325">Zaman uyumsuz kod yükünü az miktarda çalışma zamanında sağladıkları gerektirmez, ancak performans isabet yüksek trafik durumlarda, çalışırken edilebilir olduğu düşünülerek trafiği düşük durumlarda, olası performans geliştirmesi önemli.</span><span class="sxs-lookup"><span data-stu-id="44c5d-325">Asynchronous code does introduce a small amount of overhead at run time, but for low traffic situations the performance hit is negligible, while for high traffic situations, the potential performance improvement is substantial.</span></span>

<span data-ttu-id="44c5d-326">Aşağıdaki kodda, `async` anahtar sözcüğü, `Task<T>` dönüş değeri, `await` anahtar sözcüğü ve `ToListAsync` yöntemi zaman uyumsuz yürütme kodu olun.</span><span class="sxs-lookup"><span data-stu-id="44c5d-326">In the following code, the `async` keyword, `Task<T>` return value, `await` keyword, and `ToListAsync` method make the code execute asynchronously.</span></span>

[!code-csharp[Main](intro/samples/cu/Controllers/StudentsController.cs?name=snippet_ScaffoldedIndex)]

* <span data-ttu-id="44c5d-327">`async` Anahtar sözcüğü söyler yöntemi gövde bölümlerinin geri aramalar oluşturun ve otomatik olarak oluşturmak için derleyici `Task<IActionResult>` döndürülen nesne.</span><span class="sxs-lookup"><span data-stu-id="44c5d-327">The `async` keyword tells the compiler to generate callbacks for parts of the method body and to automatically create the `Task<IActionResult>` object that is returned.</span></span>

* <span data-ttu-id="44c5d-328">Dönüş türü `Task<IActionResult>` temsil eden bir sonuç türü ile devam eden iş `IActionResult`.</span><span class="sxs-lookup"><span data-stu-id="44c5d-328">The return type `Task<IActionResult>` represents ongoing work with a result of type `IActionResult`.</span></span>

* <span data-ttu-id="44c5d-329">`await` Anahtar sözcüğü yöntemi iki parçalara bölmek derleyici neden olur.</span><span class="sxs-lookup"><span data-stu-id="44c5d-329">The `await` keyword causes the compiler to split the method into two parts.</span></span> <span data-ttu-id="44c5d-330">İlk bölümü ile zaman uyumsuz olarak başlatıldığında işlemi sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="44c5d-330">The first part ends with the operation that is started asynchronously.</span></span> <span data-ttu-id="44c5d-331">İkinci bölümü işlem tamamlandığında çağrılan bir geri çağırma yöntemi konur.</span><span class="sxs-lookup"><span data-stu-id="44c5d-331">The second part is put into a callback method that is called when the operation completes.</span></span>

* <span data-ttu-id="44c5d-332">`ToListAsync`zaman uyumsuz sürümü `ToList` genişletme yöntemi.</span><span class="sxs-lookup"><span data-stu-id="44c5d-332">`ToListAsync` is the asynchronous version of the `ToList` extension method.</span></span>

<span data-ttu-id="44c5d-333">Entity Framework kullanan zaman uyumsuz kod zaman yazıyorsanız dikkat edilecek bazı noktalar:</span><span class="sxs-lookup"><span data-stu-id="44c5d-333">Some things to be aware of when you are writing asynchronous code that uses the Entity Framework:</span></span>

* <span data-ttu-id="44c5d-334">Sorguları ya da veritabanına gönderilen komutları neden deyimleri zaman uyumsuz olarak çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="44c5d-334">Only statements that cause queries or commands to be sent to the database are executed asynchronously.</span></span> <span data-ttu-id="44c5d-335">İçeren, örneğin, `ToListAsync`, `SingleOrDefaultAsync`, ve `SaveChangesAsync`.</span><span class="sxs-lookup"><span data-stu-id="44c5d-335">That includes, for example, `ToListAsync`, `SingleOrDefaultAsync`, and `SaveChangesAsync`.</span></span>  <span data-ttu-id="44c5d-336">Bu, örneğin, yalnızca değiştirme deyimleri içermez bir `IQueryable`, gibi `var students = context.Students.Where(s => s.LastName == "Davolio")`.</span><span class="sxs-lookup"><span data-stu-id="44c5d-336">It does not include, for example, statements that just change an `IQueryable`, such as `var students = context.Students.Where(s => s.LastName == "Davolio")`.</span></span>

* <span data-ttu-id="44c5d-337">EF bağlamı iş parçacığı içinde korumalı değil: paralel birden çok işlemleri yapmak denemeyin.</span><span class="sxs-lookup"><span data-stu-id="44c5d-337">An EF context is not thread safe: don't try to do multiple operations in parallel.</span></span> <span data-ttu-id="44c5d-338">Herhangi bir zaman uyumsuz EF yöntemini çağırdığınızda, her zaman kullanabilirsiniz `await` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="44c5d-338">When you call any async EF method, always use the `await` keyword.</span></span>

* <span data-ttu-id="44c5d-339">Zaman uyumsuz kod performans yararlarını yararlanmak isterseniz herhangi bir kitaplığı paketleri emin olun (örneğin disk belleği için olduğu gibi) kullanıyorsanız, veritabanına gönderilmek üzere sorgular neden herhangi bir Entity Framework yöntem çağırırsanız zaman uyumsuz da kullanın.</span><span class="sxs-lookup"><span data-stu-id="44c5d-339">If you want to take advantage of the performance benefits of async code, make sure that any library packages that you're using (such as for paging), also use async if they call any Entity Framework methods that cause queries to be sent to the database.</span></span>

<span data-ttu-id="44c5d-340">. NET'te zaman uyumsuz programlama hakkında daha fazla bilgi için bkz: [zaman uyumsuz genel bakış](https://docs.microsoft.com/dotnet/articles/standard/async).</span><span class="sxs-lookup"><span data-stu-id="44c5d-340">For more information about asynchronous programming in .NET, see [Async Overview](https://docs.microsoft.com/dotnet/articles/standard/async).</span></span>

## <a name="summary"></a><span data-ttu-id="44c5d-341">Özet</span><span class="sxs-lookup"><span data-stu-id="44c5d-341">Summary</span></span>

<span data-ttu-id="44c5d-342">Şimdi, depolamak ve verileri görüntülemek için Entity Framework Çekirdek ve SQL Server Express LocalDB kullanan basit bir uygulama oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="44c5d-342">You've now created a simple application that uses the Entity Framework Core and SQL Server Express LocalDB to store and display data.</span></span> <span data-ttu-id="44c5d-343">Aşağıdaki öğreticide, temel CRUD gerçekleştirme öğreneceksiniz (Oluştur, oku, Güncelleştir, Sil) işlemleri.</span><span class="sxs-lookup"><span data-stu-id="44c5d-343">In the following tutorial, you'll learn how to perform basic CRUD (create, read, update, delete) operations.</span></span>

>[!div class="step-by-step"]
[<span data-ttu-id="44c5d-344">Sonraki</span><span class="sxs-lookup"><span data-stu-id="44c5d-344">Next</span></span>](crud.md)  