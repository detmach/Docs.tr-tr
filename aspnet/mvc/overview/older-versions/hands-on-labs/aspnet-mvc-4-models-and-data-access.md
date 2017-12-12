---
uid: mvc/overview/older-versions/hands-on-labs/aspnet-mvc-4-models-and-data-access
title: "ASP.NET MVC 4 modelleri ve veri erişimi | Microsoft Docs"
author: rick-anderson
description: "Not: Bu uygulamalı Laboratuvar ASP.NET MVC temel bilgiye sahip olduğunu varsayar. ASP.NET MVC önce kullanmadıysanız, ASP.NET MVC 4 gitmenizi öneririz..."
ms.author: aspnetcontent
manager: wpickett
ms.date: 02/18/2013
ms.topic: article
ms.assetid: 634ea84b-f904-4afe-b71b-49cccef4d9cc
ms.technology: dotnet-mvc
ms.prod: .net-framework
msc.legacyurl: /mvc/overview/older-versions/hands-on-labs/aspnet-mvc-4-models-and-data-access
msc.type: authoredcontent
ms.openlocfilehash: bf4bb5c6f9ad8339c3597b0d6666c7077ac476e0
ms.sourcegitcommit: 9a9483aceb34591c97451997036a9120c3fe2baf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/10/2017
---
<a name="aspnet-mvc-4-models-and-data-access"></a><span data-ttu-id="6d0b6-104">ASP.NET MVC 4 modelleri ve veri erişimi</span><span class="sxs-lookup"><span data-stu-id="6d0b6-104">ASP.NET MVC 4 Models and Data Access</span></span>
====================
<span data-ttu-id="6d0b6-105">tarafından [Web Camps ekibi](https://twitter.com/webcamps)</span><span class="sxs-lookup"><span data-stu-id="6d0b6-105">by [Web Camps Team](https://twitter.com/webcamps)</span></span>

> [!NOTE]
> <span data-ttu-id="6d0b6-106">Bu uygulamalı Laboratuvar temel bilgiye sahip varsayar **ASP.NET MVC**.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-106">This Hands-on Lab assumes you have basic knowledge of **ASP.NET MVC**.</span></span> <span data-ttu-id="6d0b6-107">Değil kullandıysanız **ASP.NET MVC** gitmenizi öneririz önce **ASP.NET MVC 4 Temelleri** uygulamalı Laboratuvar.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-107">If you have not used **ASP.NET MVC** before, we recommend you to go over **ASP.NET MVC 4 Fundamentals** Hands-on Lab.</span></span>
> 
> <span data-ttu-id="6d0b6-108">Bu Laboratuvar, kaynak klasöre sağlanan örnek bir Web uygulamasına küçük değişiklikler uygulayarak daha önce açıklanan yeni özellikleri ve geliştirmeleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-108">This lab walks you through the enhancements and new features previously described by applying minor changes to a sample Web application provided in the Source folder.</span></span>
> 
> <span data-ttu-id="6d0b6-109">Tüm örnek kod ve parçacıkları Web Camps eğitim Seti, adresinde yer alan [https://www.microsoft.com/en-us/download/29843](https://www.microsoft.com/en-us/download/29843).</span><span class="sxs-lookup"><span data-stu-id="6d0b6-109">All sample code and snippets are included in the Web Camps Training Kit, available at [https://www.microsoft.com/en-us/download/29843](https://www.microsoft.com/en-us/download/29843).</span></span>


<span data-ttu-id="6d0b6-110">İçinde **ASP.NET MVC Temelleri** uygulamalı Laboratuvar, sabit kodlanmış veri geçirerek denetleyicilerinden görünüm şablonları.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-110">In **ASP.NET MVC Fundamentals** Hands-on Lab, you have been passing hard-coded data from the Controllers to the View templates.</span></span> <span data-ttu-id="6d0b6-111">Ancak, gerçek bir Web uygulaması oluşturmak için gerçek bir veritabanını kullanmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-111">But, in order to build a real Web application, you might want to use a real database.</span></span>

<span data-ttu-id="6d0b6-112">Bu uygulamalı Laboratuvar depolamak ve müzik deposu uygulaması için gereken verileri almak için bir veritabanı motoru kullanmak nasıl yapacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-112">This Hands-on Lab will show you how to use a database engine in order to store and retrieve the data needed for the Music Store application.</span></span> <span data-ttu-id="6d0b6-113">Bunu yapmaya yönelik var olan bir veritabanı başlatın ve varlık veri modeli oluşturmak.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-113">To accomplish that, you will start with an existing database and create the Entity Data Model from it.</span></span> <span data-ttu-id="6d0b6-114">Bu Laboratuvar, karşılayacağını **veritabanı ilk** yaklaşım yanı sıra **Code First** yaklaşım.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-114">Throughout this lab, you will meet the **Database First** approach as well as the **Code First** approach.</span></span>

<span data-ttu-id="6d0b6-115">Ancak, aynı zamanda kullanabilirsiniz **Model First** yaklaşımını, araçları kullanarak aynı modelin oluşturun ve ondan veritabanı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-115">However, you can also use the **Model First** approach, create the same model using the tools, and then generate the database from it.</span></span>

<span data-ttu-id="6d0b6-116">![Veritabanı ilk vs. Model ilk](aspnet-mvc-4-models-and-data-access/_static/image1.png "veritabanı ilk vs. İlk model")</span><span class="sxs-lookup"><span data-stu-id="6d0b6-116">![Database First vs. Model First](aspnet-mvc-4-models-and-data-access/_static/image1.png "Database First vs. Model First")</span></span>

<span data-ttu-id="6d0b6-117">*Veritabanı ilk vs. İlk model*</span><span class="sxs-lookup"><span data-stu-id="6d0b6-117">*Database First vs. Model First*</span></span>

<span data-ttu-id="6d0b6-118">Model oluşturma sonra StoreController sabit kodlanmış verileri kullanmak yerine veritabanından alınan veri deposu görünümlerini sağlamak için uygun düzeltmeleri yapar.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-118">After generating the Model, you will make the proper adjustments in the StoreController to provide the Store Views with the data taken from the database, instead of using hard-coded data.</span></span> <span data-ttu-id="6d0b6-119">Görünüm şablonları için aynı ViewModels StoreController döndürme çünkü bu kez veritabanından veri gelir ancak herhangi bir değişiklik görünüm şablonlarda yapmak gerekmez.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-119">You will not need to make any change to the View templates because the StoreController will be returning the same ViewModels to the View templates, although this time the data will come from the database.</span></span>

<span data-ttu-id="6d0b6-120">**İlk kod yaklaşımı**</span><span class="sxs-lookup"><span data-stu-id="6d0b6-120">**The Code First Approach**</span></span>

<span data-ttu-id="6d0b6-121">Code First yaklaşım bize genellikle framework ile birlikte sınıfları oluşturmadan kodu modelden tanımlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-121">The Code First approach allows us to define the model from the code without generating classes that are generally coupled with the framework.</span></span>

<span data-ttu-id="6d0b6-122">Kodda, ilk olarak, model nesneleri POCOs ile tanımlanan &quot;düz eski CLR nesnelerini&quot;.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-122">In code first, model objects are defined with POCOs, &quot;Plain Old CLR Objects&quot;.</span></span> <span data-ttu-id="6d0b6-123">POCOs hiçbir devralma ve arabirimleri kullanılmaz basit düz sınıflarıdır.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-123">POCOs are simple plain classes that have no inheritance and do not implement interfaces.</span></span> <span data-ttu-id="6d0b6-124">Biz otomatik olarak veritabanı onlardan oluşturabilir veya biz varolan bir veritabanını kullanın ve sınıf eşleme kodundan oluşturduğunuz.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-124">We can automatically generate the database from them, or we can use an existing database and generate the class mapping from the code.</span></span>

<span data-ttu-id="6d0b6-125">Bu yaklaşımı kullanmanın avantajları olan POCOs sınıfları eşleme framework ile bağlı değil olarak Model (Bu durumda, Entity Framework), Kalıcılık çerçeveden bağımsız olarak kalır.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-125">The benefits of using this approach is that the Model remains independent from the persistence framework (in this case, Entity Framework), as the POCOs classes are not coupled with the mapping framework.</span></span>

> [!NOTE]
> <span data-ttu-id="6d0b6-126">Bu Laboratuvar ASP.NET MVC 4 temel alır ve müzik deposu örnek uygulama sürümü özelleştirilmiş ve yalnızca bu uygulamalı laboratuar ortamında gösterilen özellikleri uyacak şekilde simge durumuna küçültülmüş.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-126">This Lab is based on ASP.NET MVC 4 and a version of the Music Store sample application customized and minimized to fit only the features shown in this Hands-On Lab.</span></span>
> 
> <span data-ttu-id="6d0b6-127">Bütün araştırmak istiyorsanız **müzik deposu** içinde bulabilirsiniz öğretici uygulama [MVC müzik deposu](https://github.com/evilDave/MVC-Music-Store).</span><span class="sxs-lookup"><span data-stu-id="6d0b6-127">If you wish to explore the whole **Music Store** tutorial application you can find it in [MVC-Music-Store](https://github.com/evilDave/MVC-Music-Store).</span></span>


<a id="Prerequisites"></a>

<a id="Prerequisites"></a>
### <a name="prerequisites"></a><span data-ttu-id="6d0b6-128">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="6d0b6-128">Prerequisites</span></span>

<span data-ttu-id="6d0b6-129">Bu laboratuvarı tamamlamak için aşağıdaki öğeleri sahip olmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="6d0b6-129">You must have the following items to complete this lab:</span></span>

- <span data-ttu-id="6d0b6-130">[Web için Visual Studio Express 2012 Microsoft](https://www.microsoft.com/visualstudio/eng/products/visual-studio-express-for-web) veya daha üstün (okuma [ek A](#AppendixA) nasıl yükleneceği hakkında yönergeler için).</span><span class="sxs-lookup"><span data-stu-id="6d0b6-130">[Microsoft Visual Studio Express 2012 for Web](https://www.microsoft.com/visualstudio/eng/products/visual-studio-express-for-web) or superior (read [Appendix A](#AppendixA) for instructions on how to install it).</span></span>

<a id="Setup"></a>

<a id="Setup"></a>
### <a name="setup"></a><span data-ttu-id="6d0b6-131">Kurulum</span><span class="sxs-lookup"><span data-stu-id="6d0b6-131">Setup</span></span>

<span data-ttu-id="6d0b6-132">**Kod parçacıkları yükleme**</span><span class="sxs-lookup"><span data-stu-id="6d0b6-132">**Installing Code Snippets**</span></span>

<span data-ttu-id="6d0b6-133">Kolaylık olması için bu Laboratuvar yönetme kod çoğunu Visual Studio kod parçacıkları kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-133">For convenience, much of the code you will be managing along this lab is available as Visual Studio code snippets.</span></span> <span data-ttu-id="6d0b6-134">Çalıştırma kod parçacıkları yüklemek için **.\Source\Setup\CodeSnippets.vsi** dosya.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-134">To install the code snippets run **.\Source\Setup\CodeSnippets.vsi** file.</span></span>

<span data-ttu-id="6d0b6-135">Visual Studio kod parçacıkları ve bunları nasıl kullanacağınızı öğrenmek istiyorsanız bilmiyorsanız, bu belgedeki eke başvurabilir &quot; [ek C: kullanarak kod parçacıkları](#AppendixC)&quot;.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-135">If you are not familiar with the Visual Studio Code Snippets, and want to learn how to use them, you can refer to the appendix from this document &quot;[Appendix C: Using Code Snippets](#AppendixC)&quot;.</span></span>

* * *

<a id="Exercises"></a>

<a id="Exercises"></a>
## <a name="exercises"></a><span data-ttu-id="6d0b6-136">Alıştırmaları</span><span class="sxs-lookup"><span data-stu-id="6d0b6-136">Exercises</span></span>

<span data-ttu-id="6d0b6-137">Bu uygulamalı Laboratuvar tarafından aşağıdaki alıştırmaları oluşmaktadır:</span><span class="sxs-lookup"><span data-stu-id="6d0b6-137">This Hands-on Lab is comprised by the following exercises:</span></span>

1. [<span data-ttu-id="6d0b6-138">Alıştırma 1: bir veritabanına ekleme</span><span class="sxs-lookup"><span data-stu-id="6d0b6-138">Exercise 1: Adding a Database</span></span>](#Exercise1)
2. [<span data-ttu-id="6d0b6-139">Alıştırma 2: Code First kullanarak veritabanı oluşturma</span><span class="sxs-lookup"><span data-stu-id="6d0b6-139">Exercise 2: Creating a Database using Code First</span></span>](#Exercise2)
3. [<span data-ttu-id="6d0b6-140">Alıştırma 3: parametrelerle veritabanını sorgulama</span><span class="sxs-lookup"><span data-stu-id="6d0b6-140">Exercise 3: Querying the Database with Parameters</span></span>](#Exercise3)

> [!NOTE]
> <span data-ttu-id="6d0b6-141">Her alıştırma tarafından eşlik bir **son** elde alıştırmaları tamamladıktan sonra sonuçta elde edilen çözümü içeren klasör.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-141">Each exercise is accompanied by an **End** folder containing the resulting solution you should obtain after completing the exercises.</span></span> <span data-ttu-id="6d0b6-142">Alıştırmaları ile çalışma hakkında ek Yardım gerekirse, bu çözüm bir kılavuz olarak kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-142">You can use this solution as a guide if you need additional help working through the exercises.</span></span>


<span data-ttu-id="6d0b6-143">Bu laboratuvarı tamamlamak için süre tahmini: **35 dakika**.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-143">Estimated time to complete this lab: **35 minutes**.</span></span>

<a id="Exercise1"></a>

<a id="Exercise_1_Adding_a_Database"></a>
### <a name="exercise-1-adding-a-database"></a><span data-ttu-id="6d0b6-144">Alıştırma 1: bir veritabanına ekleme</span><span class="sxs-lookup"><span data-stu-id="6d0b6-144">Exercise 1: Adding a Database</span></span>

<span data-ttu-id="6d0b6-145">Bu alıştırmada, kendi veri tüketmek için çözüm MusicStore uygulamaya tablolar ile bir veritabanı eklemek öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-145">In this exercise, you will learn how to add a database with the tables of the MusicStore application to the solution in order to consume its data.</span></span> <span data-ttu-id="6d0b6-146">Veritabanı modeli ile oluşturulan ve çözüme eklendi sonra Görünüm şablonu sabit kodlanmış değerler yerine veritabanından alınan veri sağlamak için StoreController sınıfı değiştirecektir.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-146">Once the database is generated with the model, and added to the solution, you will modify the StoreController class to provide the View template with the data taken from the database, instead of using hard-coded values.</span></span>

<a id="Ex1Task1"></a>

<a id="Task_1_-_Adding_a_Database"></a>
#### <a name="task-1---adding-a-database"></a><span data-ttu-id="6d0b6-147">Görev 1 - bir veritabanı ekleme</span><span class="sxs-lookup"><span data-stu-id="6d0b6-147">Task 1 - Adding a Database</span></span>

<span data-ttu-id="6d0b6-148">Bu görevde, çözüme MusicStore uygulamasının ana tablolarla önceden oluşturulmuş bir veritabanına ekler.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-148">In this task, you will add an already created database with the main tables of the MusicStore application to the solution.</span></span>

1. <span data-ttu-id="6d0b6-149">Açık **başlamak** çözüm bulunan **kaynak/Ex1-AddingADatabaseDBFirst/başlangıç/** klasörü.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-149">Open the **Begin** solution located at **Source/Ex1-AddingADatabaseDBFirst/Begin/** folder.</span></span>

    1. <span data-ttu-id="6d0b6-150">Bazı eksik NuGet paketlerini indirmek gerekir devam etmeden önce.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-150">You will need to download some missing NuGet packages before continue.</span></span> <span data-ttu-id="6d0b6-151">Bunu yapmak için tıklatın **proje** menü ve select **NuGet paketlerini Yönet**.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-151">To do this, click the **Project** menu and select **Manage NuGet Packages**.</span></span>
    2. <span data-ttu-id="6d0b6-152">İçinde **NuGet paketlerini Yönet** iletişim kutusunda, tıklatın **geri** eksik paketleri indirmesine için.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-152">In the **Manage NuGet Packages** dialog, click **Restore** in order to download missing packages.</span></span>
    3. <span data-ttu-id="6d0b6-153">Son olarak, tıklayarak çözümü derleme **yapı** | **yapı çözümü**.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-153">Finally, build the solution by clicking **Build** | **Build Solution**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="6d0b6-154">NuGet kullanarak avantajlarından biri, projenizdeki tüm kitaplıkları dağıtmayı proje boyutunun azaltılması gerekmemesidir.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-154">One of the advantages of using NuGet is that you don't have to ship all the libraries in your project, reducing the project size.</span></span> <span data-ttu-id="6d0b6-155">NuGet güç araçları ile Packages.config dosyasında paket sürümlerini belirterek, tüm gerekli kitaplıkları ilk kez proje çalıştırdığınızda indirebilirsiniz olacaktır.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-155">With NuGet Power Tools, by specifying the package versions in the Packages.config file, you will be able to download all the required libraries the first time you run the project.</span></span> <span data-ttu-id="6d0b6-156">Varolan bir çözümü bu Laboratuvar açtıktan sonra aşağıdaki adımları çalıştırmanız gerekecek nedeni budur.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-156">This is why you will have to run these steps after you open an existing solution from this lab.</span></span>
2. <span data-ttu-id="6d0b6-157">Ekleme **MvcMusicStore** veritabanı dosyası.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-157">Add **MvcMusicStore** database file.</span></span> <span data-ttu-id="6d0b6-158">Bu uygulamalı laboratuar ortamında adlı bir veritabanı zaten oluşturuldu kullanacağı **MvcMusicStore.mdf**.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-158">In this Hands-on Lab, you will use an already created database called **MvcMusicStore.mdf**.</span></span> <span data-ttu-id="6d0b6-159">Bunu yapmak için sağ **uygulama\_veri** klasörünü **Ekle** ve ardından **varolan öğeyi**.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-159">To do that, right-click **App\_Data** folder, point to **Add** and then click **Existing Item**.</span></span> <span data-ttu-id="6d0b6-160">Gözat **\Source\Assets** seçip **MvcMusicStore.mdf** dosya.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-160">Browse to **\Source\Assets** and select the **MvcMusicStore.mdf** file.</span></span>

    <span data-ttu-id="6d0b6-161">![Var olan bir öğe ekleme](aspnet-mvc-4-models-and-data-access/_static/image2.png "var olan bir öğe ekleme")</span><span class="sxs-lookup"><span data-stu-id="6d0b6-161">![Adding an Existing Item](aspnet-mvc-4-models-and-data-access/_static/image2.png "Adding an Existing Item")</span></span>

    <span data-ttu-id="6d0b6-162">*Var olan bir öğe ekleme*</span><span class="sxs-lookup"><span data-stu-id="6d0b6-162">*Adding an Existing Item*</span></span>

    <span data-ttu-id="6d0b6-163">![MvcMusicStore.mdf veritabanı dosyası](aspnet-mvc-4-models-and-data-access/_static/image3.png "MvcMusicStore.mdf veritabanı dosyası")</span><span class="sxs-lookup"><span data-stu-id="6d0b6-163">![MvcMusicStore.mdf database file](aspnet-mvc-4-models-and-data-access/_static/image3.png "MvcMusicStore.mdf database file")</span></span>

    <span data-ttu-id="6d0b6-164">*MvcMusicStore.mdf veritabanı dosyası*</span><span class="sxs-lookup"><span data-stu-id="6d0b6-164">*MvcMusicStore.mdf database file*</span></span>

    <span data-ttu-id="6d0b6-165">Veritabanı projeye eklendi.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-165">The database has been added to the project.</span></span> <span data-ttu-id="6d0b6-166">Veritabanı içinde çözüm bile bulunur, sorgu ve onu farklı bir veritabanı sunucusu barındırılan gibi güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-166">Even when the database is located inside the solution, you can query and update it as it was hosted in a different database server.</span></span>

    <span data-ttu-id="6d0b6-167">![Çözüm Gezgini'nde MvcMusicStore veritabanı](aspnet-mvc-4-models-and-data-access/_static/image4.png "Çözüm Gezgini'nde MvcMusicStore veritabanı")</span><span class="sxs-lookup"><span data-stu-id="6d0b6-167">![MvcMusicStore database in Solution Explorer](aspnet-mvc-4-models-and-data-access/_static/image4.png "MvcMusicStore database in Solution Explorer")</span></span>

    <span data-ttu-id="6d0b6-168">*Çözüm Gezgini'nde MvcMusicStore veritabanı*</span><span class="sxs-lookup"><span data-stu-id="6d0b6-168">*MvcMusicStore database in Solution Explorer*</span></span>
3. <span data-ttu-id="6d0b6-169">Veritabanı bağlantısı doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-169">Verify the connection to the database.</span></span> <span data-ttu-id="6d0b6-170">Bunu yapmak için çift **MvcMusicStore.mdf** bağlantı kuramıyor.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-170">To do this, double-click **MvcMusicStore.mdf** to establish a connection.</span></span>

    <span data-ttu-id="6d0b6-171">![MvcMusicStore.mdf için bağlanma](aspnet-mvc-4-models-and-data-access/_static/image5.png "MvcMusicStore.mdf için bağlanma")</span><span class="sxs-lookup"><span data-stu-id="6d0b6-171">![Connecting to MvcMusicStore.mdf](aspnet-mvc-4-models-and-data-access/_static/image5.png "Connecting to MvcMusicStore.mdf")</span></span>

    <span data-ttu-id="6d0b6-172">*MvcMusicStore.mdf için bağlanma*</span><span class="sxs-lookup"><span data-stu-id="6d0b6-172">*Connecting to MvcMusicStore.mdf*</span></span>

<a id="Ex1Task2"></a>

<a id="Task_2_-_Creating_a_Data_Model"></a>
#### <a name="task-2---creating-a-data-model"></a><span data-ttu-id="6d0b6-173">Görev 2 - bir veri modeli oluşturma</span><span class="sxs-lookup"><span data-stu-id="6d0b6-173">Task 2 - Creating a Data Model</span></span>

<span data-ttu-id="6d0b6-174">Bu görevde, önceki görevde eklenen veritabanıyla etkileşim kurmak için bir veri modeli oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-174">In this task, you will create a data model to interact with the database added in the previous task.</span></span>

1. <span data-ttu-id="6d0b6-175">Veritabanı temsil edecek bir veri modeli oluşturun.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-175">Create a data model that will represent the database.</span></span> <span data-ttu-id="6d0b6-176">Bu, Çözüm Gezgini içinde yapmak için sağ **modelleri** klasörünü **Ekle** ve ardından **yeni öğe**.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-176">To do this, in Solution Explorer right-click the **Models** folder, point to **Add** and then click **New Item**.</span></span> <span data-ttu-id="6d0b6-177">İçinde **Yeni Öğe Ekle** iletişim kutusunda **veri** şablonu ve ardından **ADO.NET varlık veri modeli** öğesi.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-177">In the **Add New Item** dialog, select the **Data** template and then the **ADO.NET Entity Data Model** item.</span></span> <span data-ttu-id="6d0b6-178">Veri modeli adı değiştirmek **StoreDB.edmx** tıklatıp **Ekle**.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-178">Change the data model name to **StoreDB.edmx** and click **Add**.</span></span>

    <span data-ttu-id="6d0b6-179">![StoreDB ADO.NET varlık veri modeli ekleme](aspnet-mvc-4-models-and-data-access/_static/image6.png "StoreDB ADO.NET varlık veri modeli ekleme")</span><span class="sxs-lookup"><span data-stu-id="6d0b6-179">![Adding the StoreDB ADO.NET Entity Data Model](aspnet-mvc-4-models-and-data-access/_static/image6.png "Adding the StoreDB ADO.NET Entity Data Model")</span></span>

    <span data-ttu-id="6d0b6-180">*StoreDB ADO.NET varlık veri modeli ekleme*</span><span class="sxs-lookup"><span data-stu-id="6d0b6-180">*Adding the StoreDB ADO.NET Entity Data Model*</span></span>
2. <span data-ttu-id="6d0b6-181">**Varlık veri modeli Sihirbazı** görünür.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-181">The **Entity Data Model Wizard** will appear.</span></span> <span data-ttu-id="6d0b6-182">Bu sihirbaz, modeli katmanı oluşturulmasını yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-182">This wizard will guide you through the creation of the model layer.</span></span> <span data-ttu-id="6d0b6-183">Model eklenen varolan veritabanı recentyl tabanlı oluşturulmalıdır beri seçin **veritabanından Oluştur** tıklatıp **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-183">Since the model should be created based on the existing database recentyl added, select **Generate from database** and click **Next**.</span></span>

    <span data-ttu-id="6d0b6-184">![Model içeriğinin seçme](aspnet-mvc-4-models-and-data-access/_static/image7.png "model içeriğinin seçme")</span><span class="sxs-lookup"><span data-stu-id="6d0b6-184">![Choosing the model content](aspnet-mvc-4-models-and-data-access/_static/image7.png "Choosing the model content")</span></span>

    <span data-ttu-id="6d0b6-185">*Model içeriğinin seçme*</span><span class="sxs-lookup"><span data-stu-id="6d0b6-185">*Choosing the model content*</span></span>
3. <span data-ttu-id="6d0b6-186">Model bir veritabanından oluşturma olduğundan, bağlantıyı kullanacak şekilde belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-186">Since you are generating a model from a database, you will need to specify the connection to use.</span></span> <span data-ttu-id="6d0b6-187">Tıklatın **yeni bağlantı**.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-187">Click **New Connection**.</span></span>
4. <span data-ttu-id="6d0b6-188">Seçin **Microsoft SQL Server veritabanı dosyası** tıklatıp **devam**.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-188">Select **Microsoft SQL Server Database File** and click **Continue**.</span></span>

    <span data-ttu-id="6d0b6-189">![Veri Kaynağı Seç](aspnet-mvc-4-models-and-data-access/_static/image8.png "Seç veri kaynağı")</span><span class="sxs-lookup"><span data-stu-id="6d0b6-189">![Choose data source](aspnet-mvc-4-models-and-data-access/_static/image8.png "Choose data source")</span></span>

    <span data-ttu-id="6d0b6-190">*Veri kaynağı iletişim seçin*</span><span class="sxs-lookup"><span data-stu-id="6d0b6-190">*Choose data source dialog*</span></span>
5. <span data-ttu-id="6d0b6-191">Tıklatın **Gözat** ve veritabanını seçin **MvcMusicStore.mdf** içinde bulunan **uygulama\_veri** klasörü ve tıklatın **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-191">Click **Browse** and select the database **MvcMusicStore.mdf** you located in the **App\_Data** folder and click **OK**.</span></span>

    <span data-ttu-id="6d0b6-192">![Bağlantı özellikleri](aspnet-mvc-4-models-and-data-access/_static/image9.png "bağlantı özellikleri")</span><span class="sxs-lookup"><span data-stu-id="6d0b6-192">![Connection properties](aspnet-mvc-4-models-and-data-access/_static/image9.png "Connection properties")</span></span>

    <span data-ttu-id="6d0b6-193">*Bağlantı özellikleri*</span><span class="sxs-lookup"><span data-stu-id="6d0b6-193">*Connection properties*</span></span>
6. <span data-ttu-id="6d0b6-194">Oluşturulan sınıf varlık bağlantı dizesi ile aynı ada sahip, bu nedenle adının değiştirmek **MusicStoreEntities** tıklatıp **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-194">The generated class should have the same name as the entity connection string, so change its name to **MusicStoreEntities** and click **Next**.</span></span>

    <span data-ttu-id="6d0b6-195">![Veri bağlantısı seçme](aspnet-mvc-4-models-and-data-access/_static/image10.png "veri bağlantısı seçme")</span><span class="sxs-lookup"><span data-stu-id="6d0b6-195">![Choosing the data connection](aspnet-mvc-4-models-and-data-access/_static/image10.png "Choosing the data connection")</span></span>

    <span data-ttu-id="6d0b6-196">*Veri bağlantısı seçme*</span><span class="sxs-lookup"><span data-stu-id="6d0b6-196">*Choosing the data connection*</span></span>
7. <span data-ttu-id="6d0b6-197">Kullanmak için veritabanı nesneleri seçin.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-197">Choose the database objects to use.</span></span> <span data-ttu-id="6d0b6-198">Varlık modeli yalnızca veritabanı tabloları kullanacak şekilde seçin **tabloları** seçeneği ve olduğundan emin olun **yabancı anahtar sütunlarını modele dahil** ve **Pluralize veya tekil hale getirin oluşturulan Nesne adları** seçenekleri da seçilir.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-198">As the Entity Model will use just the database's tables, select the **Tables** option, and make sure that the **Include foreign key columns in the model** and **Pluralize or singularize generated object names** options are also selected.</span></span> <span data-ttu-id="6d0b6-199">Model Namespace değiştirme **MvcMusicStore.Model** tıklatıp **son**.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-199">Change the Model Namespace to **MvcMusicStore.Model** and click **Finish**.</span></span>

    <span data-ttu-id="6d0b6-200">![Veritabanı nesneleri seçme](aspnet-mvc-4-models-and-data-access/_static/image11.png "veritabanı nesneleri seçme")</span><span class="sxs-lookup"><span data-stu-id="6d0b6-200">![Choosing the database objects](aspnet-mvc-4-models-and-data-access/_static/image11.png "Choosing the database objects")</span></span>

    <span data-ttu-id="6d0b6-201">*Veritabanı nesneleri seçme*</span><span class="sxs-lookup"><span data-stu-id="6d0b6-201">*Choosing the database objects*</span></span>

    > [!NOTE]
    > <span data-ttu-id="6d0b6-202">Bir güvenlik uyarısı iletişim kutusu gösterilirse, tıklatın **Tamam** şablonu çalıştırın ve model varlıkların sınıfları oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-202">If a Security Warning dialog is shown, click **OK** to run the template and generate the classes for the model entities.</span></span>
8. <span data-ttu-id="6d0b6-203">Veritabanı için bir varlığın diyagram, her tablo veritabanına eşlemeleri ayrı bir sınıf oluşturulacak sırada görünür.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-203">An entity diagram for the database will appear, while a separate class that maps each table to the database will be created.</span></span> <span data-ttu-id="6d0b6-204">Örneğin, **albümleri** tabloda belirtildiği bir **albüm** sınıfı, burada tablodaki her sütun eşlemek için bir sınıf özelliği.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-204">For example, the **Albums** table will be represented by an **Album** class, where each column in the table will map to a class property.</span></span> <span data-ttu-id="6d0b6-205">Bu, sorgu ve veritabanında satır temsil eden nesneler üzerinde çalışmak olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-205">This will allow you to query and work with objects that represent rows in the database.</span></span>

    <span data-ttu-id="6d0b6-206">![Varlık diyagram](aspnet-mvc-4-models-and-data-access/_static/image12.png "varlık diyagramı")</span><span class="sxs-lookup"><span data-stu-id="6d0b6-206">![Entity diagram](aspnet-mvc-4-models-and-data-access/_static/image12.png "Entity diagram")</span></span>

    <span data-ttu-id="6d0b6-207">*Varlık diyagramı*</span><span class="sxs-lookup"><span data-stu-id="6d0b6-207">*Entity diagram*</span></span>

> [!NOTE]
> <span data-ttu-id="6d0b6-208">T4 şablonları (.tt) varlıklar sınıfları oluşturmak için kodu çalıştırın ve aynı ada sahip mevcut sınıflarını üzerine yazar.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-208">The T4 templates (.tt) run code to generate the entities classes and will overwrite the existing classes with the same name.</span></span> <span data-ttu-id="6d0b6-209">Bu örnekte, sınıfları &quot;albüm&quot;, &quot;Tarz&quot; ve &quot;sanatçı&quot; ile oluşturulan kodun verilerinin üzerine yazıldı.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-209">In this example, the classes &quot;Album&quot;, &quot;Genre&quot; and &quot;Artist&quot; were overwritten with the generated code.</span></span>


<a id="Ex1Task3"></a>

<a id="Task_3_-_Building_the_Application"></a>
#### <a name="task-3---building-the-application"></a><span data-ttu-id="6d0b6-210">Görev 3 - uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="6d0b6-210">Task 3 - Building the Application</span></span>

<span data-ttu-id="6d0b6-211">Model oluşturma kaldırıldı. ancak bu görevde, kontrol eder **albüm**, **Tarz** ve **sanatçı** modeli sınıfları, projenin başarıyla kullanarak oluşturur Yeni veri modeli sınıfları.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-211">In this task, you will check that, although the model generation have removed the **Album**, **Genre** and **Artist** model classes, the project builds successfully by using the new data model classes.</span></span>

1. <span data-ttu-id="6d0b6-212">Seçerek Projeyi derlemek **yapı** menü öğesini ve ardından **yapı MvcMusicStore**.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-212">Build the project by selecting the **Build** menu item and then **Build MvcMusicStore**.</span></span>

    <span data-ttu-id="6d0b6-213">![Proje derleme](aspnet-mvc-4-models-and-data-access/_static/image13.png "projesi oluşturma")</span><span class="sxs-lookup"><span data-stu-id="6d0b6-213">![Building the project](aspnet-mvc-4-models-and-data-access/_static/image13.png "Building the project")</span></span>

    <span data-ttu-id="6d0b6-214">*Proje derleme*</span><span class="sxs-lookup"><span data-stu-id="6d0b6-214">*Building the project*</span></span>
2. <span data-ttu-id="6d0b6-215">Proje başarıyla oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-215">The project builds successfully.</span></span> <span data-ttu-id="6d0b6-216">Neden hala çalışır?</span><span class="sxs-lookup"><span data-stu-id="6d0b6-216">Why does it still work?</span></span> <span data-ttu-id="6d0b6-217">Veritabanı tablolarını kaldırılan sınıflarda kullanmakta olduğunuz özellikleri içeren alanlar olduğundan çalışır **albüm** ve **Tarz**.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-217">It works because the database tables have fields that include the properties that you were using in the removed classes **Album** and **Genre**.</span></span>

    <span data-ttu-id="6d0b6-218">![Başarılı bir şekilde derlemeleri](aspnet-mvc-4-models-and-data-access/_static/image14.png "başarılı derlemeleri")</span><span class="sxs-lookup"><span data-stu-id="6d0b6-218">![Builds succeeded](aspnet-mvc-4-models-and-data-access/_static/image14.png "Builds succeeded")</span></span>

    <span data-ttu-id="6d0b6-219">*Derlemeleri başarılı oldu*</span><span class="sxs-lookup"><span data-stu-id="6d0b6-219">*Builds succeeded*</span></span>
3. <span data-ttu-id="6d0b6-220">Tasarımcı varlıklar diyagramı biçiminde görüntüler olsa da, bunlar gerçekten C# sınıflarıdır.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-220">While the designer displays the entities in a diagram format, they are really C# classes.</span></span> <span data-ttu-id="6d0b6-221">Genişletme **StoreDB.edmx** Çözüm Gezgini'nde düğümünü ve ardından **StoreDB.tt**, yeni oluşturulan varlıkları görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-221">Expand the **StoreDB.edmx** node in the Solution Explorer and then **StoreDB.tt**, you will see the new generated entities.</span></span>

    <span data-ttu-id="6d0b6-222">![Oluşturulan dosyaları](aspnet-mvc-4-models-and-data-access/_static/image15.png "oluşturulan dosyaları")</span><span class="sxs-lookup"><span data-stu-id="6d0b6-222">![Generated files](aspnet-mvc-4-models-and-data-access/_static/image15.png "Generated files")</span></span>

    <span data-ttu-id="6d0b6-223">*Oluşturulan dosyalar*</span><span class="sxs-lookup"><span data-stu-id="6d0b6-223">*Generated files*</span></span>

<a id="Ex1Task4"></a>

<a id="Task_4_-_Querying_the_Database"></a>
#### <a name="task-4---querying-the-database"></a><span data-ttu-id="6d0b6-224">Görev 4 - veritabanını sorgulama</span><span class="sxs-lookup"><span data-stu-id="6d0b6-224">Task 4 - Querying the Database</span></span>

<span data-ttu-id="6d0b6-225">Bu görevde, sabit kodlanmış verileri kullanmak yerine, bu bilgileri almak için veritabanı sorgulayacak böylece StoreController sınıfı güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-225">In this task, you will update the StoreController class so that, instead of using hardcoded data, it will query the database to retrieve the information.</span></span>

1. <span data-ttu-id="6d0b6-226">Açık **Controllers\StoreController.cs** ve aşağıdaki alan örneği tutacak sınıfına ekleyin **MusicStoreEntities** adlı sınıf **storeDB**:</span><span class="sxs-lookup"><span data-stu-id="6d0b6-226">Open **Controllers\StoreController.cs** and add the following field to the class to hold an instance of the **MusicStoreEntities** class, named **storeDB**:</span></span>

    <span data-ttu-id="6d0b6-227">(Kod parçacığını - *modelleri ve veri erişimi - Ex1 storeDB*)</span><span class="sxs-lookup"><span data-stu-id="6d0b6-227">(Code Snippet - *Models And Data Access - Ex1 storeDB*)</span></span>


    [!code-csharp[Main](aspnet-mvc-4-models-and-data-access/samples/sample1.cs)]
2. <span data-ttu-id="6d0b6-228">**MusicStoreEntities** sınıfı veritabanındaki her tablo için bir koleksiyon özelliği sunar.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-228">The **MusicStoreEntities** class exposes a collection property for each table in the database.</span></span> <span data-ttu-id="6d0b6-229">Güncelleştirme **Gözat** bir tarzını tüm almak için eylem yöntemini **albümleri**.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-229">Update **Browse** action method to retrieve a Genre with all of the **Albums**.</span></span>

    <span data-ttu-id="6d0b6-230">(Kod parçacığını - *modelleri ve veri erişimi - Ex1 deposu Gözat*)</span><span class="sxs-lookup"><span data-stu-id="6d0b6-230">(Code Snippet - *Models And Data Access - Ex1 Store Browse*)</span></span>


    [!code-csharp[Main](aspnet-mvc-4-models-and-data-access/samples/sample2.cs)]

    > [!NOTE]
    > <span data-ttu-id="6d0b6-231">Adlı .NET yeteneğini kullanarak **LINQ** (veritabanında kod yürütmek ve dönüş bu koleksiyonları karşı-kesin türü belirtilmiş sorgu ifadeleri yazmak için dil ile tümleşik sorgu) nesneleri, programlama yapabilirsiniz karşı.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-231">You are using a capability of .NET called **LINQ** (language-integrated query) to write strongly-typed query expressions against these collections - which will execute code against the database and return objects that you can program against.</span></span>
    > 
    > <span data-ttu-id="6d0b6-232">LINQ hakkında daha fazla bilgi için lütfen ziyaret [msdn sitesini](https://msdn.microsoft.com/en-us/library/bb397926&amp;#040;v=vs.110&amp;#041;.aspx).</span><span class="sxs-lookup"><span data-stu-id="6d0b6-232">For more information about LINQ, please visit the [msdn site](https://msdn.microsoft.com/en-us/library/bb397926&amp;#040;v=vs.110&amp;#041;.aspx).</span></span>
3. <span data-ttu-id="6d0b6-233">Güncelleştirme **dizin** tüm türler almak için eylem yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-233">Update **Index** action method to retrieve all the genres.</span></span>

    <span data-ttu-id="6d0b6-234">(Kod parçacığını - *modelleri ve veri erişimi - Ex1 deposu dizini*)</span><span class="sxs-lookup"><span data-stu-id="6d0b6-234">(Code Snippet - *Models And Data Access - Ex1 Store Index*)</span></span>


    [!code-csharp[Main](aspnet-mvc-4-models-and-data-access/samples/sample3.cs)]
4. <span data-ttu-id="6d0b6-235">Güncelleştirme **dizin** tüm türler almak ve bir liste koleksiyona dönüştürmek için eylem yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-235">Update **Index** action method to retrieve all the genres and transform the collection to a list.</span></span>

    <span data-ttu-id="6d0b6-236">(Kod parçacığını - *modelleri ve veri erişimi - Ex1 deposu GenreMenu*)</span><span class="sxs-lookup"><span data-stu-id="6d0b6-236">(Code Snippet - *Models And Data Access - Ex1 Store GenreMenu*)</span></span>


    [!code-csharp[Main](aspnet-mvc-4-models-and-data-access/samples/sample4.cs)]

<a id="Ex1Task5"></a>

<a id="Task_5_-_Running_the_Application"></a>
#### <a name="task-5---running-the-application"></a><span data-ttu-id="6d0b6-237">Görev 5 - Uygulama çalışıyor</span><span class="sxs-lookup"><span data-stu-id="6d0b6-237">Task 5 - Running the Application</span></span>

<span data-ttu-id="6d0b6-238">Bu görevde deposu dizin sayfası kodlanmış olanları yerine veritabanında depolanan türler artık göstereceğini kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-238">In this task, you will check that the Store Index page will now display the Genres stored in the database instead of the hardcoded ones.</span></span> <span data-ttu-id="6d0b6-239">Şablonu görüntüleme çünkü değiştirmenize gerek yoktur **StoreController** bu kez veritabanından veri gelir ancak aynı varlık önceki gibi döndüren.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-239">There is no need to change the View template because the **StoreController** is returning the same entities as before, although this time the data will come from the database.</span></span>

1. <span data-ttu-id="6d0b6-240">Tuşuna basın ve çözüm yeniden **F5** uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-240">Rebuild the solution and press **F5** to run the Application.</span></span>
2. <span data-ttu-id="6d0b6-241">Proje giriş sayfası başlatır.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-241">The project starts in the Home page.</span></span> <span data-ttu-id="6d0b6-242">Doğrulayın menüsünü **türler** artık sabit kodlanmış bir listesidir ve verileri doğrudan veritabanından alınır.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-242">Verify that the menu of **Genres** is no longer a hardcoded list, and the data is directly retrieved from the database.</span></span>

    ![BrowsingGenresFromDataBase](aspnet-mvc-4-models-and-data-access/_static/image16.png)

    <span data-ttu-id="6d0b6-244">*Veritabanından gözatma türler*</span><span class="sxs-lookup"><span data-stu-id="6d0b6-244">*Browsing Genres from the database*</span></span>
3. <span data-ttu-id="6d0b6-245">Şimdi bir tarzını gözatın ve albümleri veritabanından doldurulur doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-245">Now browse to any genre and verify the albums are populated from database.</span></span>

    <span data-ttu-id="6d0b6-246">![Veritabanından albümleri gözatma](aspnet-mvc-4-models-and-data-access/_static/image17.png "gözatma albümleri veritabanından")</span><span class="sxs-lookup"><span data-stu-id="6d0b6-246">![Browsing Albums from the database](aspnet-mvc-4-models-and-data-access/_static/image17.png "Browsing Albums from the database")</span></span>

    <span data-ttu-id="6d0b6-247">*Veritabanından albümleri gözatma*</span><span class="sxs-lookup"><span data-stu-id="6d0b6-247">*Browsing Albums from the database*</span></span>

<a id="Exercise2"></a>

<a id="Exercise_2_Creating_a_Database_Using_Code_First"></a>
### <a name="exercise-2-creating-a-database-using-code-first"></a><span data-ttu-id="6d0b6-248">Alıştırma 2: İlk kod kullanarak bir veritabanı oluşturma</span><span class="sxs-lookup"><span data-stu-id="6d0b6-248">Exercise 2: Creating a Database Using Code First</span></span>

<span data-ttu-id="6d0b6-249">Bu alıştırmada, kod ilk yaklaşım MusicStore uygulama tablolarla bir veritabanı oluşturmak için nasıl kullanılacağı ve onun verilere nasıl erişileceğini öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-249">In this exercise, you will learn how to use the Code First approach to create a database with the tables of the MusicStore application, and how to access its data.</span></span>

<span data-ttu-id="6d0b6-250">Model oluşturulduktan sonra Görünüm şablonu sabit kodlanmış değerler yerine veritabanından alınan veri sağlamak için StoreController değiştirecektir.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-250">Once the model is generated, you will modify the StoreController to provide the View template with the data taken from the database, instead of using hardcoded values.</span></span>

> [!NOTE]
> <span data-ttu-id="6d0b6-251">Alıştırma 1 tamamladıktan ve veritabanı ilk yaklaşımda zaten çalıştıysa farklı bir işlem ile aynı sonuçları almak nasıl şimdi öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-251">If you have completed Exercise 1 and have already worked with the Database First approach, you will now learn how to get the same results with a different process.</span></span> <span data-ttu-id="6d0b6-252">Alıştırma 1 ortak olan görevleri okuma kolaylaştırmak için işaretlendi.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-252">The tasks that are in common with Exercise 1 have been marked to make your reading easier.</span></span> <span data-ttu-id="6d0b6-253">Alıştırma 1 tamamlamadıysanız, ancak ilk kod yaklaşımı öğrenmek ister misiniz Bu alıştırmada başlatın ve tam kapsamı konunun alın.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-253">If you have not completed Exercise 1 but would like to learn the Code First approach, you can start from this exercise and get a full coverage of the topic.</span></span>


<a id="Ex2Task1"></a>

<a id="Task_1_-_Populating_Sample_Data"></a>
#### <a name="task-1---populating-sample-data"></a><span data-ttu-id="6d0b6-254">Görev 1 - doldurma örnek veriler</span><span class="sxs-lookup"><span data-stu-id="6d0b6-254">Task 1 - Populating Sample Data</span></span>

<span data-ttu-id="6d0b6-255">Kod ilk kullanılarak başlangışta oluşturulduğunda bu görevde, veritabanı örnek verileri ile doldurur.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-255">In this task, you will populate the database with sample data when it is intially created using Code-First.</span></span>

1. <span data-ttu-id="6d0b6-256">Açık **başlamak** çözüm bulunan **kaynak/Ex2-CreatingADatabaseCodeFirst/başlangıç/** klasörü.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-256">Open the **Begin** solution located at **Source/Ex2-CreatingADatabaseCodeFirst/Begin/** folder.</span></span> <span data-ttu-id="6d0b6-257">Aksi takdirde kullanarak devam edebilir **son** çözüm elde önceki alıştırmada tamamlayarak.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-257">Otherwise, you might continue using the **End** solution obtained by completing the previous exercise.</span></span>

    1. <span data-ttu-id="6d0b6-258">Sağlanan açtıysanız **başlamak** çözümü gerekir bazı eksik NuGet paketlerini indirmek devam etmeden önce.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-258">If you opened the provided **Begin** solution, you will need to download some missing NuGet packages before continue.</span></span> <span data-ttu-id="6d0b6-259">Bunu yapmak için tıklatın **proje** menü ve select **NuGet paketlerini Yönet**.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-259">To do this, click the **Project** menu and select **Manage NuGet Packages**.</span></span>
    2. <span data-ttu-id="6d0b6-260">İçinde **NuGet paketlerini Yönet** iletişim kutusunda, tıklatın **geri** eksik paketleri indirmesine için.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-260">In the **Manage NuGet Packages** dialog, click **Restore** in order to download missing packages.</span></span>
    3. <span data-ttu-id="6d0b6-261">Son olarak, tıklayarak çözümü derleme **yapı** | **yapı çözümü**.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-261">Finally, build the solution by clicking **Build** | **Build Solution**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="6d0b6-262">NuGet kullanarak avantajlarından biri, projenizdeki tüm kitaplıkları dağıtmayı proje boyutunun azaltılması gerekmemesidir.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-262">One of the advantages of using NuGet is that you don't have to ship all the libraries in your project, reducing the project size.</span></span> <span data-ttu-id="6d0b6-263">NuGet güç araçları ile Packages.config dosyasında paket sürümlerini belirterek, tüm gerekli kitaplıkları ilk kez proje çalıştırdığınızda indirebilirsiniz olacaktır.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-263">With NuGet Power Tools, by specifying the package versions in the Packages.config file, you will be able to download all the required libraries the first time you run the project.</span></span> <span data-ttu-id="6d0b6-264">Varolan bir çözümü bu Laboratuvar açtıktan sonra aşağıdaki adımları çalıştırmanız gerekecek nedeni budur.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-264">This is why you will have to run these steps after you open an existing solution from this lab.</span></span>
2. <span data-ttu-id="6d0b6-265">Ekleme **SampleData.cs** dosya **modelleri** klasör.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-265">Add the **SampleData.cs** file to the **Models** folder.</span></span> <span data-ttu-id="6d0b6-266">Bunu yapmak için sağ **modelleri** klasörünü **Ekle** ve ardından **varolan öğeyi**.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-266">To do that, right-click **Models** folder, point to **Add** and then click **Existing Item**.</span></span> <span data-ttu-id="6d0b6-267">Gözat **\Source\Assets** seçip **SampleData.cs** dosya.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-267">Browse to **\Source\Assets** and select the **SampleData.cs** file.</span></span>

    <span data-ttu-id="6d0b6-268">![Örnek verileri doldurmak kod](aspnet-mvc-4-models-and-data-access/_static/image18.png "örnek verileri doldurmak kodu")</span><span class="sxs-lookup"><span data-stu-id="6d0b6-268">![Sample data populate code](aspnet-mvc-4-models-and-data-access/_static/image18.png "Sample data populate code")</span></span>

    <span data-ttu-id="6d0b6-269">*Örnek verileri kod doldurma*</span><span class="sxs-lookup"><span data-stu-id="6d0b6-269">*Sample data populate code*</span></span>
3. <span data-ttu-id="6d0b6-270">Açık **Global.asax.cs** dosya ve aşağıdakileri ekleyin *kullanarak* deyimleri.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-270">Open the **Global.asax.cs** file and add the following *using* statements.</span></span>

    <span data-ttu-id="6d0b6-271">(Kod parçacığını - *modelleri ve veri erişimi - Ex2 genel Asax kullanımları*)</span><span class="sxs-lookup"><span data-stu-id="6d0b6-271">(Code Snippet - *Models And Data Access - Ex2 Global Asax Usings*)</span></span>


    [!code-csharp[Main](aspnet-mvc-4-models-and-data-access/samples/sample5.cs)]
4. <span data-ttu-id="6d0b6-272">İçinde **uygulama\_Start()** yöntemi veritabanı Başlatıcısı ayarlamak için aşağıdaki satırı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-272">In the **Application\_Start()** method add the following line to set the database initializer.</span></span>

    <span data-ttu-id="6d0b6-273">(Kod parçacığını - *modelleri ve veri erişimi - Ex2 genel Asax SetInitializer*)</span><span class="sxs-lookup"><span data-stu-id="6d0b6-273">(Code Snippet - *Models And Data Access - Ex2 Global Asax SetInitializer*)</span></span>


    [!code-csharp[Main](aspnet-mvc-4-models-and-data-access/samples/sample6.cs)]

<a id="Ex2Task2"></a>

<a id="Task_2_-_Configuring_the_connection_to_the_Database"></a>
#### <a name="task-2---configuring-the-connection-to-the-database"></a><span data-ttu-id="6d0b6-274">Görev 2 - veritabanı bağlantısı yapılandırma</span><span class="sxs-lookup"><span data-stu-id="6d0b6-274">Task 2 - Configuring the connection to the Database</span></span>

<span data-ttu-id="6d0b6-275">Projemizin için bir veritabanı zaten eklenmiş, yazacağınız **Web.config** bağlantı dizesi dosya.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-275">Now that you have already added a database to our project, you will write in the **Web.config** file the connection string.</span></span>

1. <span data-ttu-id="6d0b6-276">Konumunda bir bağlantı dizesi eklemek **Web.config**. Bunu yapmak için açık **Web.config** proje kök ve bağlantı dizesi bu satırda ile DefaultConnection adlı Değiştir  **&lt;connectionStrings&gt;**  bölümü:</span><span class="sxs-lookup"><span data-stu-id="6d0b6-276">Add a connection string at **Web.config**. To do that, open **Web.config** at project root and replace the connection string named DefaultConnection with this line in the **&lt;connectionStrings&gt;** section:</span></span>

    <span data-ttu-id="6d0b6-277">![Web.config dosyası konumu](aspnet-mvc-4-models-and-data-access/_static/image19.png "Web.config dosyası konumu")</span><span class="sxs-lookup"><span data-stu-id="6d0b6-277">![Web.config file location](aspnet-mvc-4-models-and-data-access/_static/image19.png "Web.config file location")</span></span>

    <span data-ttu-id="6d0b6-278">*Web.config dosyası konumu*</span><span class="sxs-lookup"><span data-stu-id="6d0b6-278">*Web.config file location*</span></span>


    [!code-xml[Main](aspnet-mvc-4-models-and-data-access/samples/sample7.xml)]

<a id="Ex2Task3"></a>

<a id="Task_3_-_Working_with_the_Model"></a>
#### <a name="task-3---working-with-the-model"></a><span data-ttu-id="6d0b6-279">Görev 3 - modeli ile çalışma</span><span class="sxs-lookup"><span data-stu-id="6d0b6-279">Task 3 - Working with the Model</span></span>

<span data-ttu-id="6d0b6-280">Veritabanı bağlantısı zaten yapılandırdığınıza göre veritabanı tablolarını modeliyle bağlayacaksınız.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-280">Now that you have already configured the connection to the database, you will link the model with the database tables.</span></span> <span data-ttu-id="6d0b6-281">Bu görevde, Code First olan veritabanına bağlı bir sınıf oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-281">In this task, you will create a class that will be linked to the database with Code First.</span></span> <span data-ttu-id="6d0b6-282">Değiştirilmesi gereken mevcut bir POCO model sınıfı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-282">Remember that there is an existent POCO model class that should be modified.</span></span>

> [!NOTE]
> <span data-ttu-id="6d0b6-283">Alıştırma 1 tamamladıysa, bu adım sihirbaz tarafından gerçekleştirildi Not.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-283">If you completed Exercise 1, you will note that this step was performed by a wizard.</span></span> <span data-ttu-id="6d0b6-284">Code First yaparak, veri varlıklarına bağlı sınıfları el ile oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-284">By doing Code First, you will manually create classes that will be linked to data entities.</span></span>


1. <span data-ttu-id="6d0b6-285">POCO model sınıfı açmak **Tarz** gelen **modelleri** proje klasörünü ve bir kimliğini de ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-285">Open the POCO model class **Genre** from **Models** project folder and include an ID.</span></span> <span data-ttu-id="6d0b6-286">İnt özelliği addaki **GenreId**.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-286">Use an int property with the name **GenreId**.</span></span>

    <span data-ttu-id="6d0b6-287">(Kod parçacığını - *modelleri ve veri erişimi - Ex2 kod ilk Tarz*)</span><span class="sxs-lookup"><span data-stu-id="6d0b6-287">(Code Snippet - *Models And Data Access - Ex2 Code First Genre*)</span></span>


    [!code-csharp[Main](aspnet-mvc-4-models-and-data-access/samples/sample8.cs)]

    > [!NOTE]
    > <span data-ttu-id="6d0b6-288">Code First kuralları ile çalışmak için Tarz sınıfı otomatik olarak algılanır bir birincil anahtar özelliği olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-288">To work with Code First conventions, the class Genre must have a primary key property that will be automatically detected.</span></span>
    > 
    > <span data-ttu-id="6d0b6-289">Daha fazla bilgiyi bu kod ilk kuralları hakkında [msdn makalesine](https://msdn.microsoft.com/en-us/library/hh161541&amp;#040;v=vs.103&amp;#041;.aspx).</span><span class="sxs-lookup"><span data-stu-id="6d0b6-289">You can read more about Code First Conventions in this [msdn article](https://msdn.microsoft.com/en-us/library/hh161541&amp;#040;v=vs.103&amp;#041;.aspx).</span></span>
2. <span data-ttu-id="6d0b6-290">Şimdi, POCO model sınıfı açmak **albüm** gelen **modelleri** proje klasörünü ve yabancı anahtarlar dahil, adlarıyla özellikleri oluşturma **GenreId** ve  **ArtistId**.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-290">Now, open the POCO model class **Album** from **Models** project folder and include the foreign keys, create properties with the names **GenreId** and **ArtistId**.</span></span> <span data-ttu-id="6d0b6-291">Bu sınıf zaten **GenreId** birincil anahtar.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-291">This class already have the **GenreId** for the primary key.</span></span>

    <span data-ttu-id="6d0b6-292">(Kod parçacığını - *modelleri ve veri erişimi - Ex2 kod ilk albüm*)</span><span class="sxs-lookup"><span data-stu-id="6d0b6-292">(Code Snippet - *Models And Data Access - Ex2 Code First Album*)</span></span>


    [!code-csharp[Main](aspnet-mvc-4-models-and-data-access/samples/sample9.cs)]
3. <span data-ttu-id="6d0b6-293">POCO model sınıfı açmak **sanatçı** ve dahil **ArtistId** özelliği.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-293">Open the POCO model class **Artist** and include the **ArtistId** property.</span></span>

    <span data-ttu-id="6d0b6-294">(Kod parçacığını - *modelleri ve veri erişimi - Ex2 kod ilk sanatçı*)</span><span class="sxs-lookup"><span data-stu-id="6d0b6-294">(Code Snippet - *Models And Data Access - Ex2 Code First Artist*)</span></span>


    [!code-csharp[Main](aspnet-mvc-4-models-and-data-access/samples/sample10.cs)]
4. <span data-ttu-id="6d0b6-295">Sağ **modelleri** proje klasörünü ve select **Ekle | Sınıf**.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-295">Right-click the **Models** project folder and select **Add | Class**.</span></span> <span data-ttu-id="6d0b6-296">Dosya adı **MusicStoreEntities.cs**.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-296">Name the file **MusicStoreEntities.cs**.</span></span> <span data-ttu-id="6d0b6-297">Ardından **Ekle.**</span><span class="sxs-lookup"><span data-stu-id="6d0b6-297">Then, click **Add.**</span></span>

    <span data-ttu-id="6d0b6-298">![Sınıf ekleme](aspnet-mvc-4-models-and-data-access/_static/image20.png "sınıf ekleme")</span><span class="sxs-lookup"><span data-stu-id="6d0b6-298">![Adding a class](aspnet-mvc-4-models-and-data-access/_static/image20.png "Adding a class")</span></span>

    <span data-ttu-id="6d0b6-299">*Yeni bir öğe ekleme*</span><span class="sxs-lookup"><span data-stu-id="6d0b6-299">*Adding a new item*</span></span>

    <span data-ttu-id="6d0b6-300">![Bir Ders2 ekleme](aspnet-mvc-4-models-and-data-access/_static/image21.png "bir Ders2 ekleme")</span><span class="sxs-lookup"><span data-stu-id="6d0b6-300">![Adding a class2](aspnet-mvc-4-models-and-data-access/_static/image21.png "Adding a class2")</span></span>

    <span data-ttu-id="6d0b6-301">*Sınıf ekleme*</span><span class="sxs-lookup"><span data-stu-id="6d0b6-301">*Adding a class*</span></span>
5. <span data-ttu-id="6d0b6-302">Az önce oluşturduğunuz, sınıfın açık **MusicStoreEntities.cs**ve ad alanlarını dahil **System.Data.Entity** ve **System.Data.Entity.Infrastructure**.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-302">Open the class you have just created, **MusicStoreEntities.cs**, and include the namespaces **System.Data.Entity** and **System.Data.Entity.Infrastructure**.</span></span>


    [!code-csharp[Main](aspnet-mvc-4-models-and-data-access/samples/sample11.cs)]
6. <span data-ttu-id="6d0b6-303">Genişletmek için sınıf bildirimi Değiştir **DbContext** sınıfı: Genel bildirme **DBSet** ve geçersiz kılma **OnModelCreating** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-303">Replace the class declaration to extend the **DbContext** class: declare a public **DBSet** and override **OnModelCreating** method.</span></span> <span data-ttu-id="6d0b6-304">Bu adımdan sonra modelinizi Entity Framework bağlayacak bir etki alanı sınıf alırsınız.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-304">After this step you will get a domain class that will link your model with the Entity Framework.</span></span> <span data-ttu-id="6d0b6-305">Bunu yapmak için sınıf kodu aşağıdakilerle değiştirin:</span><span class="sxs-lookup"><span data-stu-id="6d0b6-305">In order to do that, replace the class code with the following:</span></span>

    <span data-ttu-id="6d0b6-306">(Kod parçacığını - *modelleri ve veri erişimi - Ex2 kod ilk MusicStoreEntities*)</span><span class="sxs-lookup"><span data-stu-id="6d0b6-306">(Code Snippet - *Models And Data Access - Ex2 Code First MusicStoreEntities*)</span></span>


    [!code-csharp[Main](aspnet-mvc-4-models-and-data-access/samples/sample12.cs)]

    > [!NOTE]
    > <span data-ttu-id="6d0b6-307">Entity Framework **DbContext** ve **DBSet** POCO sınıfı Tarz sorgu kuramaz.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-307">With Entity Framework **DbContext** and **DBSet** you will be able to query the POCO class Genre.</span></span> <span data-ttu-id="6d0b6-308">Genişletme tarafından **OnModelCreating** yöntemi, belirtmenin **kod** tarzı bir veritabanı tablosuna nasıl eşleşecektir.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-308">By extending **OnModelCreating** method, you are specifying in the **code** how Genre will be mapped to a database table.</span></span> <span data-ttu-id="6d0b6-309">Bu msdn makalesinde DBContext ve DBSet hakkında daha fazla bilgi bulabilirsiniz: [bağlantı](https://msdn.microsoft.com/en-us/library/system.data.entity.dbcontext(v=vs.103).aspx)</span><span class="sxs-lookup"><span data-stu-id="6d0b6-309">You can find more information about DBContext and DBSet in this msdn article: [link](https://msdn.microsoft.com/en-us/library/system.data.entity.dbcontext(v=vs.103).aspx)</span></span>

<a id="Ex2Task4"></a>

<a id="Task_4_-_Querying_the_Database"></a>
#### <a name="task-4---querying-the-database"></a><span data-ttu-id="6d0b6-310">Görev 4 - veritabanını sorgulama</span><span class="sxs-lookup"><span data-stu-id="6d0b6-310">Task 4 - Querying the Database</span></span>

<span data-ttu-id="6d0b6-311">Bu görevde, sabit kodlanmış verileri kullanmak yerine, onu veritabanından alır, böylece StoreController sınıfı güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-311">In this task, you will update the StoreController class so that, instead of using hardcoded data, it will retrieve it from the database.</span></span>

> [!NOTE]
> <span data-ttu-id="6d0b6-312">Bu görev ortak alıştırma 1 ' dir.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-312">This task is in common with Exercise 1.</span></span>
> 
> <span data-ttu-id="6d0b6-313">Alıştırma 1 tamamladıysanız şu adımları her iki yaklaşımın aynı olduğunu unutmayın (ilk veritabanı veya ilk kod).</span><span class="sxs-lookup"><span data-stu-id="6d0b6-313">If you completed Exercise 1 you will note these steps are the same in both approaches (Database first or Code first).</span></span> <span data-ttu-id="6d0b6-314">Verileri nasıl modelle bağlı olarak farklı, ancak veri varlıklara erişim henüz denetleyicisinden saydamdır.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-314">They are different in how the data is linked with the model, but the access to data entities is yet transparent from the controller.</span></span>


1. <span data-ttu-id="6d0b6-315">Açık **Controllers\StoreController.cs** ve aşağıdaki alan örneği tutacak sınıfına ekleyin **MusicStoreEntities** adlı sınıf **storeDB**:</span><span class="sxs-lookup"><span data-stu-id="6d0b6-315">Open **Controllers\StoreController.cs** and add the following field to the class to hold an instance of the **MusicStoreEntities** class, named **storeDB**:</span></span>

    <span data-ttu-id="6d0b6-316">(Kod parçacığını - *modelleri ve veri erişimi - Ex1 storeDB*)</span><span class="sxs-lookup"><span data-stu-id="6d0b6-316">(Code Snippet - *Models And Data Access - Ex1 storeDB*)</span></span>


    [!code-csharp[Main](aspnet-mvc-4-models-and-data-access/samples/sample13.cs)]
2. <span data-ttu-id="6d0b6-317">**MusicStoreEntities** sınıfı veritabanındaki her tablo için bir koleksiyon özelliği sunar.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-317">The **MusicStoreEntities** class exposes a collection property for each table in the database.</span></span> <span data-ttu-id="6d0b6-318">Güncelleştirme **Gözat** bir tarzını tüm almak için eylem yöntemini **albümleri**.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-318">Update **Browse** action method to retrieve a Genre with all of the **Albums**.</span></span>

    <span data-ttu-id="6d0b6-319">(Kod parçacığını - *modelleri ve veri erişimi - Ex2 deposu Gözat*)</span><span class="sxs-lookup"><span data-stu-id="6d0b6-319">(Code Snippet - *Models And Data Access - Ex2 Store Browse*)</span></span>


    [!code-csharp[Main](aspnet-mvc-4-models-and-data-access/samples/sample14.cs)]

    > [!NOTE]
    > <span data-ttu-id="6d0b6-320">Adlı .NET yeteneğini kullanarak **LINQ** (veritabanında kod yürütmek ve dönüş bu koleksiyonları karşı-kesin türü belirtilmiş sorgu ifadeleri yazmak için dil ile tümleşik sorgu) nesneleri, programlama yapabilirsiniz karşı.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-320">You are using a capability of .NET called **LINQ** (language-integrated query) to write strongly-typed query expressions against these collections - which will execute code against the database and return objects that you can program against.</span></span>
    > 
    > <span data-ttu-id="6d0b6-321">LINQ hakkında daha fazla bilgi için lütfen ziyaret [msdn sitesini](https://msdn.microsoft.com/en-us/library/bb397926(v=vs.110).aspx).</span><span class="sxs-lookup"><span data-stu-id="6d0b6-321">For more information about LINQ, please visit the [msdn site](https://msdn.microsoft.com/en-us/library/bb397926(v=vs.110).aspx).</span></span>
3. <span data-ttu-id="6d0b6-322">Güncelleştirme **dizin** tüm türler almak için eylem yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-322">Update **Index** action method to retrieve all the genres.</span></span>

    <span data-ttu-id="6d0b6-323">(Kod parçacığını - *modelleri ve veri erişimi - Ex2 deposu dizini*)</span><span class="sxs-lookup"><span data-stu-id="6d0b6-323">(Code Snippet - *Models And Data Access - Ex2 Store Index*)</span></span>


    [!code-csharp[Main](aspnet-mvc-4-models-and-data-access/samples/sample15.cs)]
4. <span data-ttu-id="6d0b6-324">Güncelleştirme **dizin** tüm türler almak ve bir liste koleksiyona dönüştürmek için eylem yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-324">Update **Index** action method to retrieve all the genres and transform the collection to a list.</span></span>

    <span data-ttu-id="6d0b6-325">(Kod parçacığını - *modelleri ve veri erişimi - Ex2 deposu GenreMenu*)</span><span class="sxs-lookup"><span data-stu-id="6d0b6-325">(Code Snippet - *Models And Data Access - Ex2 Store GenreMenu*)</span></span>


    [!code-csharp[Main](aspnet-mvc-4-models-and-data-access/samples/sample16.cs)]

<a id="Ex2Task5"></a>

<a id="Task_5_-_Running_the_Application"></a>
#### <a name="task-5---running-the-application"></a><span data-ttu-id="6d0b6-326">Görev 5 - Uygulama çalışıyor</span><span class="sxs-lookup"><span data-stu-id="6d0b6-326">Task 5 - Running the Application</span></span>

<span data-ttu-id="6d0b6-327">Bu görevde deposu dizin sayfası kodlanmış olanları yerine veritabanında depolanan türler artık göstereceğini kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-327">In this task, you will check that the Store Index page will now display the Genres stored in the database instead of the hardcoded ones.</span></span> <span data-ttu-id="6d0b6-328">Şablonu görüntüleme çünkü değiştirmenize gerek yoktur **StoreController** aynı döndürmektir **StoreIndexViewModel** eskisi ancak bu kez verileri veritabanından gelen.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-328">There is no need to change the View template because the **StoreController** is returning the same **StoreIndexViewModel** as before, but this time the data will come from the database.</span></span>

1. <span data-ttu-id="6d0b6-329">Tuşuna basın ve çözüm yeniden **F5** uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-329">Rebuild the solution and press **F5** to run the Application.</span></span>
2. <span data-ttu-id="6d0b6-330">Proje giriş sayfası başlatır.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-330">The project starts in the Home page.</span></span> <span data-ttu-id="6d0b6-331">Doğrulayın menüsünü **türler** artık sabit kodlanmış bir listesidir ve verileri doğrudan veritabanından alınır.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-331">Verify that the menu of **Genres** is no longer a hardcoded list, and the data is directly retrieved from the database.</span></span>

    ![BrowsingGenresFromDataBase](aspnet-mvc-4-models-and-data-access/_static/image22.png)

    <span data-ttu-id="6d0b6-333">*Veritabanından gözatma türler*</span><span class="sxs-lookup"><span data-stu-id="6d0b6-333">*Browsing Genres from the database*</span></span>
3. <span data-ttu-id="6d0b6-334">Şimdi bir tarzını gözatın ve albümleri veritabanından doldurulur doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-334">Now browse to any genre and verify the albums are populated from database.</span></span>

    <span data-ttu-id="6d0b6-335">![Veritabanından albümleri gözatma](aspnet-mvc-4-models-and-data-access/_static/image23.png "gözatma albümleri veritabanından")</span><span class="sxs-lookup"><span data-stu-id="6d0b6-335">![Browsing Albums from the database](aspnet-mvc-4-models-and-data-access/_static/image23.png "Browsing Albums from the database")</span></span>

    <span data-ttu-id="6d0b6-336">*Veritabanından albümleri gözatma*</span><span class="sxs-lookup"><span data-stu-id="6d0b6-336">*Browsing Albums from the database*</span></span>

<a id="Exercise3"></a>

<a id="Exercise_3_Querying_the_Database_with_Parameters"></a>
### <a name="exercise-3-querying-the-database-with-parameters"></a><span data-ttu-id="6d0b6-337">Alıştırma 3: parametrelerle veritabanını sorgulama</span><span class="sxs-lookup"><span data-stu-id="6d0b6-337">Exercise 3: Querying the Database with Parameters</span></span>

<span data-ttu-id="6d0b6-338">Bu alıştırmada parametreleri kullanarak veritabanını sorgulama ve sorgu sonucu şekillendirme kullanmayı öğreneceksiniz, numara veritabanı azaltan bir özellik alma verileri daha verimli bir şekilde erişir.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-338">In this exercise, you will learn how to query the database using parameters, and how to use Query Result Shaping, a feature that reduces the number database accesses retrieving data in a more efficient way.</span></span>

> [!NOTE]
> <span data-ttu-id="6d0b6-339">Sorgu sonucu şekillendirme hakkında daha fazla bilgi için aşağıdaki ziyaret [msdn makalesine](https://msdn.microsoft.com/en-us/library/bb896272&amp;#040;v=vs.100&amp;#041;.aspx).</span><span class="sxs-lookup"><span data-stu-id="6d0b6-339">For further information on Query Result Shaping, visit the following [msdn article](https://msdn.microsoft.com/en-us/library/bb896272&amp;#040;v=vs.100&amp;#041;.aspx).</span></span>


<a id="Ex3Task1"></a>

<a id="Task_1_-_Modifying_StoreController_to_Retrieve_Albums_from_Database"></a>
#### <a name="task-1---modifying-storecontroller-to-retrieve-albums-from-database"></a><span data-ttu-id="6d0b6-340">Görev 1 - değiştirme StoreController albümleri veritabanından almak için</span><span class="sxs-lookup"><span data-stu-id="6d0b6-340">Task 1 - Modifying StoreController to Retrieve Albums from Database</span></span>

<span data-ttu-id="6d0b6-341">Bu görevde, değişiklik yapacağınız **StoreController** belirli bir tarzını albümleri almak için veritabanına erişmek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-341">In this task, you will change the **StoreController** class to access the database to retrieve albums from a specific genre.</span></span>

1. <span data-ttu-id="6d0b6-342">Açık **başlamak** çözüm bulunan **Source\Ex3 QueryingTheDatabaseWithParametersCodeFirst\Begin** ilk kod yaklaşımı kullanmak istiyorsanız, klasör veya **Source\ Ex3 QueryingTheDatabaseWithParametersDBFirst\Begin** veritabanı ilk yaklaşımı kullanmak istiyorsanız, klasör.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-342">Open the **Begin** solution located at the **Source\Ex3-QueryingTheDatabaseWithParametersCodeFirst\Begin** folder if you want to use Code-First approach or **Source\Ex3-QueryingTheDatabaseWithParametersDBFirst\Begin** folder if you want to use Database-First approach.</span></span> <span data-ttu-id="6d0b6-343">Aksi takdirde kullanarak devam edebilir **son** çözüm elde önceki alıştırmada tamamlayarak.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-343">Otherwise, you might continue using the **End** solution obtained by completing the previous exercise.</span></span>

    1. <span data-ttu-id="6d0b6-344">Sağlanan açtıysanız **başlamak** çözümü gerekir bazı eksik NuGet paketlerini indirmek devam etmeden önce.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-344">If you opened the provided **Begin** solution, you will need to download some missing NuGet packages before continue.</span></span> <span data-ttu-id="6d0b6-345">Bunu yapmak için tıklatın **proje** menü ve select **NuGet paketlerini Yönet**.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-345">To do this, click the **Project** menu and select **Manage NuGet Packages**.</span></span>
    2. <span data-ttu-id="6d0b6-346">İçinde **NuGet paketlerini Yönet** iletişim kutusunda, tıklatın **geri** eksik paketleri indirmesine için.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-346">In the **Manage NuGet Packages** dialog, click **Restore** in order to download missing packages.</span></span>
    3. <span data-ttu-id="6d0b6-347">Son olarak, tıklayarak çözümü derleme **yapı** | **yapı çözümü**.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-347">Finally, build the solution by clicking **Build** | **Build Solution**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="6d0b6-348">NuGet kullanarak avantajlarından biri, projenizdeki tüm kitaplıkları dağıtmayı proje boyutunun azaltılması gerekmemesidir.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-348">One of the advantages of using NuGet is that you don't have to ship all the libraries in your project, reducing the project size.</span></span> <span data-ttu-id="6d0b6-349">NuGet güç araçları ile Packages.config dosyasında paket sürümlerini belirterek, tüm gerekli kitaplıkları ilk kez proje çalıştırdığınızda indirebilirsiniz olacaktır.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-349">With NuGet Power Tools, by specifying the package versions in the Packages.config file, you will be able to download all the required libraries the first time you run the project.</span></span> <span data-ttu-id="6d0b6-350">Varolan bir çözümü bu Laboratuvar açtıktan sonra aşağıdaki adımları çalıştırmanız gerekecek nedeni budur.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-350">This is why you will have to run these steps after you open an existing solution from this lab.</span></span>
2. <span data-ttu-id="6d0b6-351">Açık **StoreController** değiştirmek için sınıf **Gözat** eylem yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-351">Open the **StoreController** class to change the **Browse** action method.</span></span> <span data-ttu-id="6d0b6-352">Bunu yapmak için **Çözüm Gezgini**, genişletin **denetleyicileri** klasörü ve çift **StoreController.cs**.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-352">To do this, in the **Solution Explorer**, expand the **Controllers** folder and double-click **StoreController.cs**.</span></span>
3. <span data-ttu-id="6d0b6-353">Değişiklik **Gözat** belirli bir tarzını albümleri almak için eylem yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-353">Change the **Browse** action method to retrieve albums for a specific genre.</span></span> <span data-ttu-id="6d0b6-354">Bunu yapmak için aşağıdaki kodu değiştirin:</span><span class="sxs-lookup"><span data-stu-id="6d0b6-354">To do this, replace the following code:</span></span>

    <span data-ttu-id="6d0b6-355">(Kod parçacığını - *modelleri ve veri erişimi - Ex3 StoreController BrowseMethod*)</span><span class="sxs-lookup"><span data-stu-id="6d0b6-355">(Code Snippet - *Models And Data Access - Ex3 StoreController BrowseMethod*)</span></span>


    [!code-csharp[Main](aspnet-mvc-4-models-and-data-access/samples/sample17.cs)]

    > [!NOTE]
    > <span data-ttu-id="6d0b6-356">Varlık koleksiyonu doldurmak için kullanmanız gerekir **INCLUDE** yöntemi albümleri çok almak istediğiniz belirtin.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-356">To populate a collection of the entity, you need to use the **Include** method to specify you want to retrieve the albums too.</span></span> <span data-ttu-id="6d0b6-357">Kullanabilirsiniz. **Single()** uzantısı LINQ bu durumda bir albüm için yalnızca bir tarzını beklendiğinden.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-357">You can use the .**Single()** extension in LINQ because in this case only one genre is expected for an album.</span></span> <span data-ttu-id="6d0b6-358">**Single()** yöntemi bir Lambda ifadesi tanımlanan değer adıyla eşleşen şekilde, bu durumda tek bir tarzını nesne belirten bir parametre olarak alır.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-358">The **Single()** method takes a Lambda expression as a parameter, which in this case specifies a single Genre object such that its name matches the value defined.</span></span>
    > 
    > <span data-ttu-id="6d0b6-359">Tarz nesnesi alınırken de yüklenen istediğiniz diğer ilgili varlıklar belirtmenize olanak sağlayan bir özelliği avantajlarından yararlanmak.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-359">You will take advantage of a feature that allows you to indicate other related entities you want loaded as well when the Genre object is retrieved.</span></span> <span data-ttu-id="6d0b6-360">Bu özellik adında **sorgu sonucu şekillendirme**ve bilgi almak için veritabanına erişmek için gerekli sayısını azaltmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-360">This feature is called **Query Result Shaping**, and enables you to reduce the number of times needed to access the database to retrieve information.</span></span> <span data-ttu-id="6d0b6-361">Bu senaryoda, Albümler aldığınız Tarz için önceden getirme isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-361">In this scenario, you will want to pre-fetch the Albums for the Genre you retrieve.</span></span>
    > 
    > <span data-ttu-id="6d0b6-362">Sorgu içeren **Genres.Include (&quot;albümleri&quot;)** ilgili Albümler istediğinizi belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-362">The query includes **Genres.Include(&quot;Albums&quot;)** to indicate that you want related albums as well.</span></span> <span data-ttu-id="6d0b6-363">Tek veritabanı isteği tarz ve albüm verilerde alacak beri bu daha verimli bir uygulamayla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-363">This will result in a more efficient application, since it will retrieve both Genre and Album data in a single database request.</span></span>

<a id="Ex3Task2"></a>

<a id="Task_2_-_Running_the_Application"></a>
#### <a name="task-2---running-the-application"></a><span data-ttu-id="6d0b6-364">Görev 2 - uygulama çalışıyor</span><span class="sxs-lookup"><span data-stu-id="6d0b6-364">Task 2 - Running the Application</span></span>

<span data-ttu-id="6d0b6-365">Bu görevde, uygulamayı çalıştırın ve belirli bir tarzını albümleri veritabanından.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-365">In this task, you will run the application and retrieve albums of a specific genre from the database.</span></span>

1. <span data-ttu-id="6d0b6-366">Tuşuna **F5** uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-366">Press **F5** to run the Application.</span></span>
2. <span data-ttu-id="6d0b6-367">Proje giriş sayfası başlatır.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-367">The project starts in the Home page.</span></span> <span data-ttu-id="6d0b6-368">URL'ye değiştirin **/deposu/Gözat? Tarz Pop =** sonuçları veritabanından alınmakta olduğunu doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-368">Change the URL to **/Store/Browse?genre=Pop** to verify that the results are being retrieved from the database.</span></span>

    <span data-ttu-id="6d0b6-369">![Türe göre gözatma](aspnet-mvc-4-models-and-data-access/_static/image24.png "türe göre gözatma")</span><span class="sxs-lookup"><span data-stu-id="6d0b6-369">![Browsing by genre](aspnet-mvc-4-models-and-data-access/_static/image24.png "Browsing by genre")</span></span>

    <span data-ttu-id="6d0b6-370">*Tarama/deposu/Gözat? Tarz Pop =*</span><span class="sxs-lookup"><span data-stu-id="6d0b6-370">*Browsing /Store/Browse?genre=Pop*</span></span>

<a id="Ex3Task3"></a>

<a id="Task_3_-_Accessing_Albums_by_Id"></a>
#### <a name="task-3---accessing-albums-by-id"></a><span data-ttu-id="6d0b6-371">Görev 3 - kimliği albümlerini erişme</span><span class="sxs-lookup"><span data-stu-id="6d0b6-371">Task 3 - Accessing Albums by Id</span></span>

<span data-ttu-id="6d0b6-372">Bu görevde, Albümler kimliklerine göre almak için önceki yordamı tekrar edilir</span><span class="sxs-lookup"><span data-stu-id="6d0b6-372">In this task, you will repeat the previous procedure to get albums by their Id.</span></span>

1. <span data-ttu-id="6d0b6-373">Gerekirse Visual Studio'ya dönmek için tarayıcıyı kapatın.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-373">Close the browser if needed, to return to Visual Studio.</span></span> <span data-ttu-id="6d0b6-374">Açık **StoreController** değiştirmek için sınıf **ayrıntıları** eylem yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-374">Open the **StoreController** class to change the **Details** action method.</span></span> <span data-ttu-id="6d0b6-375">Bunu yapmak için **Çözüm Gezgini**, genişletin **denetleyicileri** klasörü ve çift **StoreController.cs**.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-375">To do this, in the **Solution Explorer**, expand the **Controllers** folder and double-click **StoreController.cs**.</span></span>
2. <span data-ttu-id="6d0b6-376">Değişiklik **ayrıntıları** albümleri ayrıntıları almak için eylem yöntemine bağlı olarak kendi **kimliği**. Bunu yapmak için aşağıdaki kodu değiştirin:</span><span class="sxs-lookup"><span data-stu-id="6d0b6-376">Change the **Details** action method to retrieve albums details based on their **Id**. To do this, replace the following code:</span></span>

    <span data-ttu-id="6d0b6-377">(Kod parçacığını - *modelleri ve veri erişimi - Ex3 StoreController DetailsMethod*)</span><span class="sxs-lookup"><span data-stu-id="6d0b6-377">(Code Snippet - *Models And Data Access - Ex3 StoreController DetailsMethod*)</span></span>


    [!code-csharp[Main](aspnet-mvc-4-models-and-data-access/samples/sample18.cs)]

<a id="Ex3Task4"></a>

<a id="Task_4_-_Running_the_Application"></a>
#### <a name="task-4---running-the-application"></a><span data-ttu-id="6d0b6-378">Görev 4 - Uygulamayı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="6d0b6-378">Task 4 - Running the Application</span></span>

<span data-ttu-id="6d0b6-379">Bu görevde, uygulama bir web tarayıcısında çalışacak ve kimliklerine göre Albüm ayrıntılarını alma</span><span class="sxs-lookup"><span data-stu-id="6d0b6-379">In this task, you will run the Application in a web browser and obtain album details by their Id.</span></span>

1. <span data-ttu-id="6d0b6-380">Tuşuna **F5** uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-380">Press **F5** to run the Application.</span></span>
2. <span data-ttu-id="6d0b6-381">Proje giriş sayfası başlatır.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-381">The project starts in the Home page.</span></span> <span data-ttu-id="6d0b6-382">URL'ye değiştirin **/Store/Details/51** veya türler göz atın ve sonuçları veritabanından alınmakta olduğunu doğrulamak için bir albümü seçin.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-382">Change the URL to **/Store/Details/51** or browse the genres and select an album to verify that the results are being retrieved from the database.</span></span>

    <span data-ttu-id="6d0b6-383">![Ayrıntılar gözatma](aspnet-mvc-4-models-and-data-access/_static/image25.png "ayrıntıları gözatma")</span><span class="sxs-lookup"><span data-stu-id="6d0b6-383">![Browsing Details](aspnet-mvc-4-models-and-data-access/_static/image25.png "Browsing Details")</span></span>

    <span data-ttu-id="6d0b6-384">*/Store/details/51 gözatma*</span><span class="sxs-lookup"><span data-stu-id="6d0b6-384">*Browsing /Store/Details/51*</span></span>

> [!NOTE]
> <span data-ttu-id="6d0b6-385">Ayrıca, Windows Azure Web siteleri aşağıdaki bu uygulamayı dağıtabilmek için [ek B: yayımlama Web dağıtımı kullanarak bir ASP.NET MVC 4 uygulaması](#AppendixB).</span><span class="sxs-lookup"><span data-stu-id="6d0b6-385">Additionally, you can deploy this application to Windows Azure Web Sites following [Appendix B: Publishing an ASP.NET MVC 4 Application using Web Deploy](#AppendixB).</span></span>


* * *

<a id="Summary"></a>

<a id="Summary"></a>
## <a name="summary"></a><span data-ttu-id="6d0b6-386">Özet</span><span class="sxs-lookup"><span data-stu-id="6d0b6-386">Summary</span></span>

<span data-ttu-id="6d0b6-387">ASP.NET MVC modelleri ve veri erişimi temelleri öğrenilen Bu uygulamalı Laboratuvar Tamamlanıyor, kullanarak **veritabanı ilk** yaklaşım yanı sıra **Code First** yaklaşım:</span><span class="sxs-lookup"><span data-stu-id="6d0b6-387">By completing this Hands-on Lab you have learned the fundamentals of ASP.NET MVC Models and Data Access, using the **Database First** approach as well as the **Code First** Approach:</span></span>

- <span data-ttu-id="6d0b6-388">Bir veritabanı çözümü kendi veri tüketmek için ekleme</span><span class="sxs-lookup"><span data-stu-id="6d0b6-388">How to add a database to the solution in order to consume its data</span></span>
- <span data-ttu-id="6d0b6-389">Görünüm şablonları sabit kodlanmış bir yerine veritabanından alınan veri sağlamak için denetleyicileri güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="6d0b6-389">How to update Controllers to provide View templates with the data taken from the database instead of hard-coded one</span></span>
- <span data-ttu-id="6d0b6-390">Parametreleri kullanarak veritabanını sorgulama</span><span class="sxs-lookup"><span data-stu-id="6d0b6-390">How to query the database using parameters</span></span>
- <span data-ttu-id="6d0b6-391">Sorgu sonuç verileri daha verimli bir şekilde alma şekillendirme, veritabanı erişimlerine sayısını azaltan bir özellik kullanma</span><span class="sxs-lookup"><span data-stu-id="6d0b6-391">How to use the Query Result Shaping, a feature that reduces the number of database accesses, retrieving data in a more efficient way</span></span>
- <span data-ttu-id="6d0b6-392">Veritabanı ilk ve Code First yaklaşımlar Microsoft Entity Framework modelini veritabanıyla bağlantı için nasıl kullanılacağını</span><span class="sxs-lookup"><span data-stu-id="6d0b6-392">How to use both Database First and Code First approaches in Microsoft Entity Framework to link the database with the model</span></span>

<a id="AppendixA"></a>

<a id="Appendix_A_Installing_Visual_Studio_Express_2012_for_Web"></a>
## <a name="appendix-a-installing-visual-studio-express-2012-for-web"></a><span data-ttu-id="6d0b6-393">Ek A: Yükleme Web Visual Studio Express 2012 için</span><span class="sxs-lookup"><span data-stu-id="6d0b6-393">Appendix A: Installing Visual Studio Express 2012 for Web</span></span>

<span data-ttu-id="6d0b6-394">Yükleyebileceğiniz **Web için Visual Studio Express 2012 Microsoft** veya başka bir &quot;Express&quot; sürümü kullanılarak  **[Microsoft Web Platformu yükleyicisi](https://www.microsoft.com/web/downloads/platform.aspx)** .</span><span class="sxs-lookup"><span data-stu-id="6d0b6-394">You can install **Microsoft Visual Studio Express 2012 for Web** or another &quot;Express&quot; version using the **[Microsoft Web Platform Installer](https://www.microsoft.com/web/downloads/platform.aspx)**.</span></span> <span data-ttu-id="6d0b6-395">Aşağıdaki yönergeler yüklemek için gereken adımlarda size kılavuzluk *Web için Visual studio Express 2012* kullanarak *Microsoft Web Platformu yükleyicisi*.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-395">The following instructions guide you through the steps required to install *Visual studio Express 2012 for Web* using *Microsoft Web Platform Installer*.</span></span>

1. <span data-ttu-id="6d0b6-396">Git [ [https://go.microsoft.com/?linkid=9810169](https://go.microsoft.com/?linkid=9810169)](https://go.microsoft.com/?linkid=9810169).</span><span class="sxs-lookup"><span data-stu-id="6d0b6-396">Go to [[https://go.microsoft.com/?linkid=9810169](https://go.microsoft.com/?linkid=9810169)](https://go.microsoft.com/?linkid=9810169).</span></span> <span data-ttu-id="6d0b6-397">Web Platformu yükleyicisi zaten yüklü değilse, alternatif olarak, bunu ve ürün için arama açabilirsiniz &quot; *Visual Studio Express 2012 için Windows Azure SDK'sı Web*&quot;.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-397">Alternatively, if you already have installed Web Platform Installer, you can open it and search for the product &quot;*Visual Studio Express 2012 for Web with Windows Azure SDK*&quot;.</span></span>
2. <span data-ttu-id="6d0b6-398">Tıklayın **Şimdi Yükle**.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-398">Click on **Install Now**.</span></span> <span data-ttu-id="6d0b6-399">Sahip değilse **Web Platformu yükleyicisi** indirip önce yüklemek için yönlendirilir.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-399">If you do not have **Web Platform Installer** you will be redirected to download and install it first.</span></span>
3. <span data-ttu-id="6d0b6-400">Bir kez **Web Platformu yükleyicisi** açık tıklatın **yükleme** Kurulum'u başlatmak için.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-400">Once **Web Platform Installer** is open, click **Install** to start the setup.</span></span>

    <span data-ttu-id="6d0b6-401">![Visual Studio Express yükleme](aspnet-mvc-4-models-and-data-access/_static/image26.png "yükleme Visual Studio Express")</span><span class="sxs-lookup"><span data-stu-id="6d0b6-401">![Install Visual Studio Express](aspnet-mvc-4-models-and-data-access/_static/image26.png "Install Visual Studio Express")</span></span>

    <span data-ttu-id="6d0b6-402">*Visual Studio Express yükleme*</span><span class="sxs-lookup"><span data-stu-id="6d0b6-402">*Install Visual Studio Express*</span></span>
4. <span data-ttu-id="6d0b6-403">Tüm ürünlerin lisans koşullarını okuyup ve tıklayın **kabul ediyorum** devam etmek için.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-403">Read all the products' licenses and terms and click **I Accept** to continue.</span></span>

    ![Lisans koşulları kabul ediliyor](aspnet-mvc-4-models-and-data-access/_static/image27.png)

    <span data-ttu-id="6d0b6-405">*Lisans koşulları kabul ediliyor*</span><span class="sxs-lookup"><span data-stu-id="6d0b6-405">*Accepting the license terms*</span></span>
5. <span data-ttu-id="6d0b6-406">İndirme ve yükleme işlemi tamamlanana kadar bekleyin.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-406">Wait until the downloading and installation process completes.</span></span>

    ![Yükleme ilerleme durumu](aspnet-mvc-4-models-and-data-access/_static/image28.png)

    <span data-ttu-id="6d0b6-408">*Yükleme ilerleme durumu*</span><span class="sxs-lookup"><span data-stu-id="6d0b6-408">*Installation progress*</span></span>
6. <span data-ttu-id="6d0b6-409">Yükleme tamamlandığında tıklatın **son**.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-409">When the installation completes, click **Finish**.</span></span>

    ![Yükleme tamamlandı](aspnet-mvc-4-models-and-data-access/_static/image29.png)

    <span data-ttu-id="6d0b6-411">*Yükleme tamamlandı*</span><span class="sxs-lookup"><span data-stu-id="6d0b6-411">*Installation completed*</span></span>
7. <span data-ttu-id="6d0b6-412">Tıklatın **çıkış** Web Platformu Yükleyicisi'ni kapatın.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-412">Click **Exit** to close Web Platform Installer.</span></span>
8. <span data-ttu-id="6d0b6-413">Web için Visual Studio Express açmak için Git **Başlat** ekranında ve yazmaya başlayın &quot; **VS Express**&quot;, tıklayın **VS Express Web** Döşeme.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-413">To open Visual Studio Express for Web, go to the **Start** screen and start writing &quot;**VS Express**&quot;, then click on the **VS Express for Web** tile.</span></span>

    ![VS Express Web döşemeye](aspnet-mvc-4-models-and-data-access/_static/image30.png)

    <span data-ttu-id="6d0b6-415">*VS Express Web döşemeye*</span><span class="sxs-lookup"><span data-stu-id="6d0b6-415">*VS Express for Web tile*</span></span>

<a id="AppendixB"></a>

<a id="Appendix_B_Publishing_an_ASPNET_MVC_4_Application_using_Web_Deploy"></a>
## <a name="appendix-b-publishing-an-aspnet-mvc-4-application-using-web-deploy"></a><span data-ttu-id="6d0b6-416">Ek B: Web dağıtımı kullanarak bir ASP.NET MVC 4 uygulama yayımlama</span><span class="sxs-lookup"><span data-stu-id="6d0b6-416">Appendix B: Publishing an ASP.NET MVC 4 Application using Web Deploy</span></span>

<span data-ttu-id="6d0b6-417">Bu ekte Windows Azure Yönetim Portalı'ndan yeni bir web sitesi oluşturmak ve Laboratuvar izleyerek Windows Azure tarafından sağlanan Web dağıtımı Yayımlama özelliğini avantajlarını elde ettiğiniz uygulama yayımlamak nasıl yapacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-417">This appendix will show you how to create a new web site from the Windows Azure Management Portal and publish the application you obtained by following the lab, taking advantage of the Web Deploy publishing feature provided by Windows Azure.</span></span>

<a id="ApxBTask1"></a>

<a id="Task_1_-_Creating_a_New_Web_Site_from_the_Windows_Azure_Portal"></a>
#### <a name="task-1---creating-a-new-web-site-from-the-windows-azure-portal"></a><span data-ttu-id="6d0b6-418">Görev 1 - yeni bir Web sitesi oluşturma Windows Azure portalı</span><span class="sxs-lookup"><span data-stu-id="6d0b6-418">Task 1 - Creating a New Web Site from the Windows Azure Portal</span></span>

1. <span data-ttu-id="6d0b6-419">Git [Windows Azure Yönetim Portalı](https://manage.windowsazure.com/) ve aboneliğinizle ilişkili Microsoft kimlik bilgilerini kullanarak oturum açın.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-419">Go to the [Windows Azure Management Portal](https://manage.windowsazure.com/) and sign in using the Microsoft credentials associated with your subscription.</span></span>

    > [!NOTE]
    > <span data-ttu-id="6d0b6-420">Windows Azure ile 10 ASP.NET Web siteleri ücretsiz barındırma ve ardından trafiğiniz büyüdükçe ölçeğinizi.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-420">With Windows Azure you can host 10 ASP.NET Web Sites for free and then scale as your traffic grows.</span></span> <span data-ttu-id="6d0b6-421">Kaydolabilirsiniz [burada](http://aka.ms/aspnet-hol-azure).</span><span class="sxs-lookup"><span data-stu-id="6d0b6-421">You can sign up [here](http://aka.ms/aspnet-hol-azure).</span></span>

    <span data-ttu-id="6d0b6-422">![Windows Azure portalında oturum açtığı](aspnet-mvc-4-models-and-data-access/_static/image31.png "Windows Azure Portal'da oturum açın")</span><span class="sxs-lookup"><span data-stu-id="6d0b6-422">![Log on to Windows Azure portal](aspnet-mvc-4-models-and-data-access/_static/image31.png "Log on to Windows Azure portal")</span></span>

    <span data-ttu-id="6d0b6-423">*Windows Azure yönetim portalında oturum açtığı*</span><span class="sxs-lookup"><span data-stu-id="6d0b6-423">*Log on to Windows Azure Management Portal*</span></span>
2. <span data-ttu-id="6d0b6-424">Tıklatın **yeni** komut çubuğunda.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-424">Click **New** on the command bar.</span></span>

    <span data-ttu-id="6d0b6-425">![Yeni bir Web sitesi oluşturma](aspnet-mvc-4-models-and-data-access/_static/image32.png "yeni bir Web sitesi oluşturma")</span><span class="sxs-lookup"><span data-stu-id="6d0b6-425">![Creating a new Web Site](aspnet-mvc-4-models-and-data-access/_static/image32.png "Creating a new Web Site")</span></span>

    <span data-ttu-id="6d0b6-426">*Yeni bir Web sitesi oluşturma*</span><span class="sxs-lookup"><span data-stu-id="6d0b6-426">*Creating a new Web Site*</span></span>
3. <span data-ttu-id="6d0b6-427">Tıklatın **işlem** | **Web sitesi**.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-427">Click **Compute** | **Web Site**.</span></span> <span data-ttu-id="6d0b6-428">Ardından **hızlı Oluştur** seçeneği.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-428">Then select **Quick Create** option.</span></span> <span data-ttu-id="6d0b6-429">Yeni web sitesi için kullanılabilir bir URL girin ve tıklayın **Web sitesi oluştur**.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-429">Provide an available URL for the new web site and click **Create Web Site**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="6d0b6-430">Windows Azure Web sitesi, denetleyebileceğiniz ve yönetebileceğiniz bulutta çalışan bir web uygulaması için ana bilgisayardır.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-430">A Windows Azure Web Site is the host for a web application running in the cloud that you can control and manage.</span></span> <span data-ttu-id="6d0b6-431">Hızlı oluştur seçeneği, tamamlanan web uygulaması için Windows Azure Web sitesinden portal dışındaki dağıtmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-431">The Quick Create option allows you to deploy a completed web application to the Windows Azure Web Site from outside the portal.</span></span> <span data-ttu-id="6d0b6-432">Bir veritabanını ayarlamak için adımları içermez.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-432">It does not include steps for setting up a database.</span></span>

    <span data-ttu-id="6d0b6-433">![Hızlı oluşturma yöntemini kullanarak yeni bir Web sitesi oluşturma](aspnet-mvc-4-models-and-data-access/_static/image33.png "hızlı oluşturma yöntemini kullanarak yeni bir Web sitesi oluşturma")</span><span class="sxs-lookup"><span data-stu-id="6d0b6-433">![Creating a new Web Site using Quick Create](aspnet-mvc-4-models-and-data-access/_static/image33.png "Creating a new Web Site using Quick Create")</span></span>

    <span data-ttu-id="6d0b6-434">*Hızlı oluşturma yöntemini kullanarak yeni bir Web sitesi oluşturma*</span><span class="sxs-lookup"><span data-stu-id="6d0b6-434">*Creating a new Web Site using Quick Create*</span></span>
4. <span data-ttu-id="6d0b6-435">Yeni kadar bekleyin **Web sitesi** oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-435">Wait until the new **Web Site** is created.</span></span>
5. <span data-ttu-id="6d0b6-436">Web sitesi oluşturulduktan sonra altında bağlantıyı tıklatın **URL** sütun.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-436">Once the Web Site is created click the link under the **URL** column.</span></span> <span data-ttu-id="6d0b6-437">Yeni Web sitesi çalıştığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-437">Check that the new Web Site is working.</span></span>

    <span data-ttu-id="6d0b6-438">![Yeni web sitesi için gözatma](aspnet-mvc-4-models-and-data-access/_static/image34.png "yeni web sitesi için gözatma")</span><span class="sxs-lookup"><span data-stu-id="6d0b6-438">![Browsing to the new web site](aspnet-mvc-4-models-and-data-access/_static/image34.png "Browsing to the new web site")</span></span>

    <span data-ttu-id="6d0b6-439">*Yeni web sitesi için gözatma*</span><span class="sxs-lookup"><span data-stu-id="6d0b6-439">*Browsing to the new web site*</span></span>

    <span data-ttu-id="6d0b6-440">![Çalışan Web sitesi](aspnet-mvc-4-models-and-data-access/_static/image35.png "çalışan Web sitesi")</span><span class="sxs-lookup"><span data-stu-id="6d0b6-440">![Web site running](aspnet-mvc-4-models-and-data-access/_static/image35.png "Web site running")</span></span>

    <span data-ttu-id="6d0b6-441">*Çalışan Web sitesi*</span><span class="sxs-lookup"><span data-stu-id="6d0b6-441">*Web site running*</span></span>
6. <span data-ttu-id="6d0b6-442">Portalına geri dönün ve web sitesi altında adına tıklayın **adı** yönetim sayfaları görüntülemek için sütun.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-442">Go back to the portal and click the name of the web site under the **Name** column to display the management pages.</span></span>

    <span data-ttu-id="6d0b6-443">![Web sitesi Yönetim sayfalarının açma](aspnet-mvc-4-models-and-data-access/_static/image36.png "web sitesi Yönetim sayfalarının açma")</span><span class="sxs-lookup"><span data-stu-id="6d0b6-443">![Opening the web site management pages](aspnet-mvc-4-models-and-data-access/_static/image36.png "Opening the web site management pages")</span></span>

    <span data-ttu-id="6d0b6-444">*Web Sitesi Yönetim sayfalarının açma*</span><span class="sxs-lookup"><span data-stu-id="6d0b6-444">*Opening the Web Site management pages*</span></span>
7. <span data-ttu-id="6d0b6-445">İçinde **Pano** sayfasında **Hızlı Bakış** 'yi tıklatın **yayım profili indirin** bağlantı.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-445">In the **Dashboard** page, under the **quick glance** section, click the **Download publish profile** link.</span></span>

    > [!NOTE]
    > <span data-ttu-id="6d0b6-446">*Yayımlama profili* her etkin yayımlama yöntemi için bir Windows Azure Web sitesi bir web uygulamasına yayımlamak için gereken bilgilerin tümünü içerir.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-446">The *publish profile* contains all of the information required to publish a web application to a Windows Azure website for each enabled publication method.</span></span> <span data-ttu-id="6d0b6-447">Yayımlama profili URL'leri, kullanıcı kimlik bilgilerini ve bağlanmak ve her bir yayımlama yönteminin etkinleştirildiği uç noktaları karşı kimlik doğrulaması için gerekli veritabanı dizelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-447">The publish profile contains the URLs, user credentials and database strings required to connect to and authenticate against each of the endpoints for which a publication method is enabled.</span></span> <span data-ttu-id="6d0b6-448">**Microsoft WebMatrix 2**, **Microsoft Visual Studio Express Web** ve **Microsoft Visual Studio 2012** okuma destek yayımlamak için bu programlar yapılandırılmasını otomatikleştirmek için profilleri Windows Azure Web siteleri için Web uygulamaları yayımlama.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-448">**Microsoft WebMatrix 2**, **Microsoft Visual Studio Express for Web** and **Microsoft Visual Studio 2012** support reading publish profiles to automate configuration of these programs for publishing web applications to Windows Azure websites.</span></span>

    <span data-ttu-id="6d0b6-449">![Yayımlama profili web sitesi Yükleniyor](aspnet-mvc-4-models-and-data-access/_static/image37.png "yayımlama profili web sitesi yükleniyor")</span><span class="sxs-lookup"><span data-stu-id="6d0b6-449">![Downloading the web site publish profile](aspnet-mvc-4-models-and-data-access/_static/image37.png "Downloading the web site publish profile")</span></span>

    <span data-ttu-id="6d0b6-450">*Yayımlama profili Web sitesi yükleniyor*</span><span class="sxs-lookup"><span data-stu-id="6d0b6-450">*Downloading the Web Site publish profile*</span></span>
8. <span data-ttu-id="6d0b6-451">Yayımlama profili dosyasını bilinen bir konuma indirin.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-451">Download the publish profile file to a known location.</span></span> <span data-ttu-id="6d0b6-452">Daha fazla Bu alıştırmada Visual Studio'dan bir web uygulaması için bir Windows Azure Web siteleri yayımlamak için bu dosyayı kullanmak nasıl göreceksiniz.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-452">Further in this exercise you will see how to use this file to publish a web application to a Windows Azure Web Sites from Visual Studio.</span></span>

    <span data-ttu-id="6d0b6-453">![Yayımlama profili dosyasını kaydetme](aspnet-mvc-4-models-and-data-access/_static/image38.png "yayımlama profilini kaydetme")</span><span class="sxs-lookup"><span data-stu-id="6d0b6-453">![Saving the publish profile file](aspnet-mvc-4-models-and-data-access/_static/image38.png "Saving the publish profile")</span></span>

    <span data-ttu-id="6d0b6-454">*Yayımlama profili dosyasını kaydetme*</span><span class="sxs-lookup"><span data-stu-id="6d0b6-454">*Saving the publish profile file*</span></span>

<a id="ApxBTask2"></a>

<a id="Task_2_-_Configuring_the_Database_Server"></a>
#### <a name="task-2---configuring-the-database-server"></a><span data-ttu-id="6d0b6-455">Görev 2 - veritabanı sunucusunu yapılandırma</span><span class="sxs-lookup"><span data-stu-id="6d0b6-455">Task 2 - Configuring the Database Server</span></span>

<span data-ttu-id="6d0b6-456">Uygulamanızı SQL Server'ın kullanmak yaparsa veritabanlarının bir SQL veritabanı sunucusu oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-456">If your application makes use of SQL Server databases you will need to create a SQL Database server.</span></span> <span data-ttu-id="6d0b6-457">SQL Server kullanmayan basit bir uygulamayı dağıtmak istiyorsanız, bu görevi atlamak.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-457">If you want to deploy a simple application that does not use SQL Server you might skip this task.</span></span>

1. <span data-ttu-id="6d0b6-458">Uygulama veritabanını depolamak için bir SQL veritabanı sunucusu gerekir.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-458">You will need a SQL Database server for storing the application database.</span></span> <span data-ttu-id="6d0b6-459">Aboneliğiniz Windows Azure Yönetim Portalı'nda SQL veritabanı sunucularının görüntüleyebilirsiniz **Sql veritabanları** | **sunucuları** | **sunucunun Pano**.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-459">You can view the SQL Database servers from your subscription in the Windows Azure Management portal at **Sql Databases** | **Servers** | **Server's Dashboard**.</span></span> <span data-ttu-id="6d0b6-460">Oluşturulan bir sunucu yoksa kullanarak bir tane oluşturabilirsiniz **Ekle** komut çubuğundan düğme.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-460">If you do not have a server created, you can create one using the **Add** button on the command bar.</span></span> <span data-ttu-id="6d0b6-461">Not edin **sunucu adı ve URL, yönetici oturum açma adı ve parola**sonraki görevleri kullanacağı gibi.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-461">Take note of the **server name and URL, administrator login name and password**, as you will use them in the next tasks.</span></span> <span data-ttu-id="6d0b6-462">Daha sonraki bir aşamada oluşturulacak şekilde veritabanı henüz oluşturmayın.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-462">Do not create the database yet, as it will be created in a later stage.</span></span>

    <span data-ttu-id="6d0b6-463">![SQL veritabanı sunucusu Pano](aspnet-mvc-4-models-and-data-access/_static/image39.png "SQL veritabanı sunucu Panosu")</span><span class="sxs-lookup"><span data-stu-id="6d0b6-463">![SQL Database Server Dashboard](aspnet-mvc-4-models-and-data-access/_static/image39.png "SQL Database Server Dashboard")</span></span>

    <span data-ttu-id="6d0b6-464">*SQL veritabanı sunucu Panosu*</span><span class="sxs-lookup"><span data-stu-id="6d0b6-464">*SQL Database Server Dashboard*</span></span>
2. <span data-ttu-id="6d0b6-465">İşlemin sonraki görev, sunucunun listesinde, yerel IP adresi içermesi gereken bu nedenle veritabanı bağlantısı Visual Studio'dan test edecek **izin verilen IP adreslerini**.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-465">In the next task you will test the database connection from Visual Studio, for that reason you need to include your local IP address in the server's list of **Allowed IP Addresses**.</span></span> <span data-ttu-id="6d0b6-466">Bunu yapmak için tıklatın **yapılandırma**, IP adresi seçin **geçerli istemci IP adresi** üzerinde yapıştırın **başlangıç IP adresi** ve **bitiş IP adresi** metin kutuları ve tıklatın ![add-client-ip-address-ok-button](aspnet-mvc-4-models-and-data-access/_static/image40.png) düğmesi.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-466">To do that, click **Configure**, select the IP address from **Current Client IP Address** and paste it on the **Start IP Address** and **End IP Address** text boxes and click the ![add-client-ip-address-ok-button](aspnet-mvc-4-models-and-data-access/_static/image40.png) button.</span></span>

    ![İstemci IP adresi ekleme](aspnet-mvc-4-models-and-data-access/_static/image41.png)

    <span data-ttu-id="6d0b6-468">*İstemci IP adresi ekleme*</span><span class="sxs-lookup"><span data-stu-id="6d0b6-468">*Adding Client IP Address*</span></span>
3. <span data-ttu-id="6d0b6-469">Bir kez **istemci IP adresi** izin verilen IP adreslerine eklenen listesinde, tıklayın **kaydetmek** değişiklikleri onaylamak için.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-469">Once the **Client IP Address** is added to the allowed IP addresses list, click on **Save** to confirm the changes.</span></span>

    ![Değişiklikleri onaylamak](aspnet-mvc-4-models-and-data-access/_static/image42.png)

    <span data-ttu-id="6d0b6-471">*Değişiklikleri onaylamak*</span><span class="sxs-lookup"><span data-stu-id="6d0b6-471">*Confirm Changes*</span></span>

<a id="ApxBTask3"></a>

<a id="Task_3_-_Publishing_an_ASPNET_MVC_4_Application_using_Web_Deploy"></a>
#### <a name="task-3---publishing-an-aspnet-mvc-4-application-using-web-deploy"></a><span data-ttu-id="6d0b6-472">Görev 3 - Web dağıtımı kullanarak bir ASP.NET MVC 4 uygulama yayımlama</span><span class="sxs-lookup"><span data-stu-id="6d0b6-472">Task 3 - Publishing an ASP.NET MVC 4 Application using Web Deploy</span></span>

1. <span data-ttu-id="6d0b6-473">ASP.NET MVC 4 çözüme geri dönün.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-473">Go back to the ASP.NET MVC 4 solution.</span></span> <span data-ttu-id="6d0b6-474">İçinde **Çözüm Gezgini**, web sitesi projesine sağ tıklatın ve **Yayımla**.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-474">In the **Solution Explorer**, right-click the web site project and select **Publish**.</span></span>

    <span data-ttu-id="6d0b6-475">![Uygulama yayımlama](aspnet-mvc-4-models-and-data-access/_static/image43.png "uygulama yayımlama")</span><span class="sxs-lookup"><span data-stu-id="6d0b6-475">![Publishing the Application](aspnet-mvc-4-models-and-data-access/_static/image43.png "Publishing the Application")</span></span>

    <span data-ttu-id="6d0b6-476">*Web sitesi yayımlama*</span><span class="sxs-lookup"><span data-stu-id="6d0b6-476">*Publishing the web site*</span></span>
2. <span data-ttu-id="6d0b6-477">İlk görevde kaydettiğiniz yayımlama profilini içeri aktarın.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-477">Import the publish profile you saved in the first task.</span></span>

    <span data-ttu-id="6d0b6-478">![Yayımlama profilini içeri aktarma](aspnet-mvc-4-models-and-data-access/_static/image44.png "yayımlama profilini içeri aktarma")</span><span class="sxs-lookup"><span data-stu-id="6d0b6-478">![Importing the publish profile](aspnet-mvc-4-models-and-data-access/_static/image44.png "Importing the publish profile")</span></span>

    <span data-ttu-id="6d0b6-479">*Yayımlama profilini içeri aktarma*</span><span class="sxs-lookup"><span data-stu-id="6d0b6-479">*Importing publish profile*</span></span>
3. <span data-ttu-id="6d0b6-480">Tıklatın **bağlantısı doğrulama**.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-480">Click **Validate Connection**.</span></span> <span data-ttu-id="6d0b6-481">Doğrulama tamamlandıktan sonra tıklayın **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-481">Once Validation is complete click **Next**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="6d0b6-482">Yanındaki bağlantıyı doğrula düğmesi görünür yeşil bir onay işareti gördüğünüzde doğrulama tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-482">Validation is complete once you see a green checkmark appear next to the Validate Connection button.</span></span>

    <span data-ttu-id="6d0b6-483">![Bağlantı doğrulama](aspnet-mvc-4-models-and-data-access/_static/image45.png "bağlantısı doğrulanıyor")</span><span class="sxs-lookup"><span data-stu-id="6d0b6-483">![Validating connection](aspnet-mvc-4-models-and-data-access/_static/image45.png "Validating connection")</span></span>

    <span data-ttu-id="6d0b6-484">*Doğrulama bağlantısı*</span><span class="sxs-lookup"><span data-stu-id="6d0b6-484">*Validating connection*</span></span>
4. <span data-ttu-id="6d0b6-485">İçinde **ayarları** sayfasında **veritabanları** bölümünde, veritabanı bağlantının textbox yanındaki düğmesini tıklatın (yani **DefaultConnection**).</span><span class="sxs-lookup"><span data-stu-id="6d0b6-485">In the **Settings** page, under the **Databases** section, click the button next to your database connection's textbox (i.e. **DefaultConnection**).</span></span>

    <span data-ttu-id="6d0b6-486">![Web dağıtımı yapılandırma](aspnet-mvc-4-models-and-data-access/_static/image46.png "Web dağıtımı yapılandırma")</span><span class="sxs-lookup"><span data-stu-id="6d0b6-486">![Web deploy configuration](aspnet-mvc-4-models-and-data-access/_static/image46.png "Web deploy configuration")</span></span>

    <span data-ttu-id="6d0b6-487">*Web dağıtımı yapılandırma*</span><span class="sxs-lookup"><span data-stu-id="6d0b6-487">*Web deploy configuration*</span></span>
5. <span data-ttu-id="6d0b6-488">Veritabanı bağlantısı aşağıdaki gibi yapılandırın:</span><span class="sxs-lookup"><span data-stu-id="6d0b6-488">Configure the database connection as follows:</span></span>

    - <span data-ttu-id="6d0b6-489">İçinde **sunucu adı** , SQL veritabanı sunucusu URL'yi kullanarak yazın *tcp:* öneki.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-489">In the **Server name** type your SQL Database server URL using the *tcp:* prefix.</span></span>
    - <span data-ttu-id="6d0b6-490">İçinde **kullanıcı adı** sunucunuzun yönetici oturum açma adını yazın.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-490">In **User name** type your server administrator login name.</span></span>
    - <span data-ttu-id="6d0b6-491">İçinde **parola** sunucu yönetici oturum açma parolasını yazın.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-491">In **Password** type your server administrator login password.</span></span>
    - <span data-ttu-id="6d0b6-492">Yeni bir veritabanı adı yazın.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-492">Type a new database name.</span></span>

    <span data-ttu-id="6d0b6-493">![Hedef bağlantı dizesi yapılandırma](aspnet-mvc-4-models-and-data-access/_static/image47.png "hedef bağlantı dizesi yapılandırma")</span><span class="sxs-lookup"><span data-stu-id="6d0b6-493">![Configuring destination connection string](aspnet-mvc-4-models-and-data-access/_static/image47.png "Configuring destination connection string")</span></span>

    <span data-ttu-id="6d0b6-494">*Hedef bağlantı dizesi yapılandırma*</span><span class="sxs-lookup"><span data-stu-id="6d0b6-494">*Configuring destination connection string*</span></span>
6. <span data-ttu-id="6d0b6-495">Sonra **Tamam**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-495">Then click **OK**.</span></span> <span data-ttu-id="6d0b6-496">Veritabanı oluşturmak isteyip istemediğiniz sorulduğunda **Evet**.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-496">When prompted to create the database click **Yes**.</span></span>

    <span data-ttu-id="6d0b6-497">![Veritabanı oluşturma](aspnet-mvc-4-models-and-data-access/_static/image48.png "veritabanı dizesi oluşturma")</span><span class="sxs-lookup"><span data-stu-id="6d0b6-497">![Creating the database](aspnet-mvc-4-models-and-data-access/_static/image48.png "Creating the database string")</span></span>

    <span data-ttu-id="6d0b6-498">*Veritabanı oluşturuluyor*</span><span class="sxs-lookup"><span data-stu-id="6d0b6-498">*Creating the database*</span></span>
7. <span data-ttu-id="6d0b6-499">Windows Azure SQL veritabanına bağlanmak için kullanacağı bağlantı dizesini varsayılan bağlantı textbox içinde gösterilir.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-499">The connection string you will use to connect to SQL Database in Windows Azure is shown within Default Connection textbox.</span></span> <span data-ttu-id="6d0b6-500">Sonra **İleri**'ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-500">Then click **Next**.</span></span>

    <span data-ttu-id="6d0b6-501">![SQL veritabanına işaret eden bağlantı dizesi](aspnet-mvc-4-models-and-data-access/_static/image49.png "SQL veritabanına işaret eden bağlantı dizesi")</span><span class="sxs-lookup"><span data-stu-id="6d0b6-501">![Connection string pointing to SQL Database](aspnet-mvc-4-models-and-data-access/_static/image49.png "Connection string pointing to SQL Database")</span></span>

    <span data-ttu-id="6d0b6-502">*SQL veritabanına işaret eden bağlantı dizesi*</span><span class="sxs-lookup"><span data-stu-id="6d0b6-502">*Connection string pointing to SQL Database*</span></span>
8. <span data-ttu-id="6d0b6-503">İçinde **Önizleme** sayfasında, **Yayımla**.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-503">In the **Preview** page, click **Publish**.</span></span>

    <span data-ttu-id="6d0b6-504">![Web uygulaması yayımlama](aspnet-mvc-4-models-and-data-access/_static/image50.png "web uygulaması yayımlama")</span><span class="sxs-lookup"><span data-stu-id="6d0b6-504">![Publishing the web application](aspnet-mvc-4-models-and-data-access/_static/image50.png "Publishing the web application")</span></span>

    <span data-ttu-id="6d0b6-505">*Web uygulaması yayımlama*</span><span class="sxs-lookup"><span data-stu-id="6d0b6-505">*Publishing the web application*</span></span>
9. <span data-ttu-id="6d0b6-506">Yayımlama işlemi tamamlandıktan sonra varsayılan tarayıcınız yayımlanan web sitesini açın.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-506">Once the publishing process finishes, your default browser will open the published web site.</span></span>

<a id="AppendixC"></a>

<a id="Appendix_C_Using_Code_Snippets"></a>
## <a name="appendix-c-using-code-snippets"></a><span data-ttu-id="6d0b6-507">Ek C: kod parçacıkları</span><span class="sxs-lookup"><span data-stu-id="6d0b6-507">Appendix C: Using Code Snippets</span></span>

<span data-ttu-id="6d0b6-508">Kod parçacıkları ile parmaklarınızın ucunda gerek duyduğunuz tüm koduna sahip.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-508">With code snippets, you have all the code you need at your fingertips.</span></span> <span data-ttu-id="6d0b6-509">Laboratuvar belgenin tam olarak ne zaman, kullanabilmek için aşağıdaki resimde gösterildiği gibi size bildirir.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-509">The lab document will tell you exactly when you can use them, as shown in the following figure.</span></span>

<span data-ttu-id="6d0b6-510">![Kod projenize eklemek için Visual Studio kod parçacıkları](aspnet-mvc-4-models-and-data-access/_static/image51.png "kod projenize eklemek için Visual Studio kullanarak kod parçacıkları")</span><span class="sxs-lookup"><span data-stu-id="6d0b6-510">![Using Visual Studio code snippets to insert code into your project](aspnet-mvc-4-models-and-data-access/_static/image51.png "Using Visual Studio code snippets to insert code into your project")</span></span>

<span data-ttu-id="6d0b6-511">*Kod projenize eklemek için Visual Studio kod parçacıkları*</span><span class="sxs-lookup"><span data-stu-id="6d0b6-511">*Using Visual Studio code snippets to insert code into your project*</span></span>

<span data-ttu-id="6d0b6-512">***Klavye (C# yalnızca) kullanarak bir kod parçacığı eklemek için***</span><span class="sxs-lookup"><span data-stu-id="6d0b6-512">***To add a code snippet using the keyboard (C# only)***</span></span>

1. <span data-ttu-id="6d0b6-513">İmleci, burada kod eklemek istediğiniz yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-513">Place the cursor where you would like to insert the code.</span></span>
2. <span data-ttu-id="6d0b6-514">(Olmadan, boşluk veya tire) parçacığı adını yazmaya başlayın.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-514">Start typing the snippet name (without spaces or hyphens).</span></span>
3. <span data-ttu-id="6d0b6-515">Kod parçacıkları adlarla eşleşen IntelliSense görüntüler izleyin.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-515">Watch as IntelliSense displays matching snippets' names.</span></span>
4. <span data-ttu-id="6d0b6-516">Doğru parçacığı seçin (veya tüm kod parçacığını kişinin adı seçilene kadar yazmaya devam edin).</span><span class="sxs-lookup"><span data-stu-id="6d0b6-516">Select the correct snippet (or keep typing until the entire snippet's name is selected).</span></span>
5. <span data-ttu-id="6d0b6-517">İki kez parçacığını İmleç konumuna eklemek için SEKME tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-517">Press the Tab key twice to insert the snippet at the cursor location.</span></span>

<span data-ttu-id="6d0b6-518">![Kod parçacığında adını yazmaya başlayın](aspnet-mvc-4-models-and-data-access/_static/image52.png "parçacığı adını yazmaya başlayın")</span><span class="sxs-lookup"><span data-stu-id="6d0b6-518">![Start typing the snippet name](aspnet-mvc-4-models-and-data-access/_static/image52.png "Start typing the snippet name")</span></span>

<span data-ttu-id="6d0b6-519">*Kod parçacığında adını yazmaya başlayın*</span><span class="sxs-lookup"><span data-stu-id="6d0b6-519">*Start typing the snippet name*</span></span>

<span data-ttu-id="6d0b6-520">![Vurgulanan kod parçacığını seçmek için SEKME tuşuna basın](aspnet-mvc-4-models-and-data-access/_static/image53.png "vurgulanan kod parçacığını seçmek için SEKME tuşuna basın")</span><span class="sxs-lookup"><span data-stu-id="6d0b6-520">![Press Tab to select the highlighted snippet](aspnet-mvc-4-models-and-data-access/_static/image53.png "Press Tab to select the highlighted snippet")</span></span>

<span data-ttu-id="6d0b6-521">*Vurgulanan kod parçacığını seçmek için SEKME tuşuna basın*</span><span class="sxs-lookup"><span data-stu-id="6d0b6-521">*Press Tab to select the highlighted snippet*</span></span>

<span data-ttu-id="6d0b6-522">![Yeniden SEKME tuşuna basın ve kod parçacığını genişletin](aspnet-mvc-4-models-and-data-access/_static/image54.png "yeniden SEKME tuşuna basın ve kod parçacığını genişletin")</span><span class="sxs-lookup"><span data-stu-id="6d0b6-522">![Press Tab again and the snippet will expand](aspnet-mvc-4-models-and-data-access/_static/image54.png "Press Tab again and the snippet will expand")</span></span>

<span data-ttu-id="6d0b6-523">*Yeniden SEKME tuşuna basın ve kod parçacığını genişletin*</span><span class="sxs-lookup"><span data-stu-id="6d0b6-523">*Press Tab again and the snippet will expand*</span></span>

<span data-ttu-id="6d0b6-524">***Fareyi (C#, Visual Basic ve XML) kullanarak bir kod parçacığı eklemek için*** 1.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-524">***To add a code snippet using the mouse (C#, Visual Basic and XML)*** 1.</span></span> <span data-ttu-id="6d0b6-525">Kod parçacığını eklemek istediğiniz yeri sağ tıklatın.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-525">Right-click where you want to insert the code snippet.</span></span>

1. <span data-ttu-id="6d0b6-526">Seçin **Ekle parçacığı** arkasından **My kod parçacıkları**.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-526">Select **Insert Snippet** followed by **My Code Snippets**.</span></span>
2. <span data-ttu-id="6d0b6-527">Tıklayarak ilgili kod parçacığında listeden seçin.</span><span class="sxs-lookup"><span data-stu-id="6d0b6-527">Pick the relevant snippet from the list, by clicking on it.</span></span>

<span data-ttu-id="6d0b6-528">![Sağ tıklatın, istediğiniz kod parçacığını eklemek ve Ekle parçacık](aspnet-mvc-4-models-and-data-access/_static/image55.png "sağ tıklatın, istediğiniz kod parçacığını eklemek ve parçacık Ekle")</span><span class="sxs-lookup"><span data-stu-id="6d0b6-528">![Right-click where you want to insert the code snippet and select Insert Snippet](aspnet-mvc-4-models-and-data-access/_static/image55.png "Right-click where you want to insert the code snippet and select Insert Snippet")</span></span>

<span data-ttu-id="6d0b6-529">*Kod parçacığını eklemek ve parçacık eklemek istediğiniz yeri sağ tıklatın*</span><span class="sxs-lookup"><span data-stu-id="6d0b6-529">*Right-click where you want to insert the code snippet and select Insert Snippet*</span></span>

<span data-ttu-id="6d0b6-530">![Tıklayarak ilgili kod parçacığında listeden çekme](aspnet-mvc-4-models-and-data-access/_static/image56.png "tıklayarak ilgili kod parçacığında listeden seçin")</span><span class="sxs-lookup"><span data-stu-id="6d0b6-530">![Pick the relevant snippet from the list, by clicking on it](aspnet-mvc-4-models-and-data-access/_static/image56.png "Pick the relevant snippet from the list, by clicking on it")</span></span>

<span data-ttu-id="6d0b6-531">*Tıklayarak ilgili kod parçacığında listeden seçin*</span><span class="sxs-lookup"><span data-stu-id="6d0b6-531">*Pick the relevant snippet from the list, by clicking on it*</span></span>