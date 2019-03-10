---
title: 'Postupy: Vytvořit nastavení aplikace'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application settings [Windows Forms], Windows Forms
- application settings [Windows Forms], creating
ms.assetid: 1e7aa347-af75-41e5-89ca-f53cab704f72
ms.openlocfilehash: d540715c0b4c69b2981cc65f55b0fa950c5a4eaf
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57721239"
---
# <a name="how-to-create-application-settings"></a><span data-ttu-id="b8304-102">Postupy: Vytvořit nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="b8304-102">How to: Create Application Settings</span></span>
<span data-ttu-id="b8304-103">Pomocí spravovaného kódu, můžete vytvořit nové nastavení aplikace a svázat ho s vlastnostmi na formulář nebo ovládací prvky do formuláře, takže tato nastavení jsou načtena a za běhu automaticky uloženy.</span><span class="sxs-lookup"><span data-stu-id="b8304-103">Using managed code, you can create new application settings and bind them to properties on your form or your form's controls, so that these settings are loaded and saved automatically at run time.</span></span>  
  
 <span data-ttu-id="b8304-104">V následujícím postupu vytvoříte ručně obálkovou třídu, která je odvozena z <xref:System.Configuration.ApplicationSettingsBase>.</span><span class="sxs-lookup"><span data-stu-id="b8304-104">In the following procedure, you manually create a wrapper class that derives from <xref:System.Configuration.ApplicationSettingsBase>.</span></span> <span data-ttu-id="b8304-105">Do této třídy přidat vlastnost veřejně přístupné pro každé nastavení aplikace, kterou chcete zveřejnit.</span><span class="sxs-lookup"><span data-stu-id="b8304-105">To this class you add a publicly accessible property for each application setting that you want to expose.</span></span>  
  
 <span data-ttu-id="b8304-106">Můžete také provést tento postup pomocí minimálního psaní kódu v návrháři aplikace Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b8304-106">You can also perform this procedure using minimal code in the Visual Studio designer.</span></span>  <span data-ttu-id="b8304-107">Viz také [jak: Vytvořit nastavení aplikace pomocí návrháře](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/wabtadw6(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="b8304-107">Also see [How to: Create Application Settings Using the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/wabtadw6(v=vs.100)).</span></span>  
  
### <a name="to-create-new-application-settings-programmatically"></a><span data-ttu-id="b8304-108">Chcete-li vytvořit nové nastavení aplikace prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="b8304-108">To create new Application Settings programmatically</span></span>  
  
1.  <span data-ttu-id="b8304-109">Přidejte novou třídu do projektu a přejmenujte jej.</span><span class="sxs-lookup"><span data-stu-id="b8304-109">Add a new class to your project, and rename it.</span></span> <span data-ttu-id="b8304-110">V tomto postupu budeme volat tuto třídu `MyUserSettings`.</span><span class="sxs-lookup"><span data-stu-id="b8304-110">For this procedure, we will call this class `MyUserSettings`.</span></span> <span data-ttu-id="b8304-111">Změnit definici třídy, takže je odvozena z třídy <xref:System.Configuration.ApplicationSettingsBase>.</span><span class="sxs-lookup"><span data-stu-id="b8304-111">Change the class definition so that the class derives from <xref:System.Configuration.ApplicationSettingsBase>.</span></span>  
  
2.  <span data-ttu-id="b8304-112">Definovat vlastnost na této obálkové třídy pro každé nastavení aplikace, budete potřebovat a použít tuto vlastnost buď <xref:System.Configuration.ApplicationScopedSettingAttribute> nebo <xref:System.Configuration.UserScopedSettingAttribute>, v závislosti na rozsahu nastavení.</span><span class="sxs-lookup"><span data-stu-id="b8304-112">Define a property on this wrapper class for each application setting you require, and apply that property with either the <xref:System.Configuration.ApplicationScopedSettingAttribute> or <xref:System.Configuration.UserScopedSettingAttribute>, depending on the scope of the setting.</span></span> <span data-ttu-id="b8304-113">Další informace o nastavení oboru, naleznete v tématu [přehled nastavení aplikace](application-settings-overview.md).</span><span class="sxs-lookup"><span data-stu-id="b8304-113">For more information about settings scope, see [Application Settings Overview](application-settings-overview.md).</span></span> <span data-ttu-id="b8304-114">Nyní váš kód by měl vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="b8304-114">By now, your code should look like this:</span></span>  
  
     [!code-csharp[ApplicationSettings.Create#1](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/MyAppSettings.cs#1)]
     [!code-vb[ApplicationSettings.Create#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/MyAppSettings.vb#1)]  
  
3.  <span data-ttu-id="b8304-115">Vytvoření instance této obálkové třídy ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="b8304-115">Create an instance of this wrapper class in your application.</span></span> <span data-ttu-id="b8304-116">Běžně je soukromý člen hlavního formuláře.</span><span class="sxs-lookup"><span data-stu-id="b8304-116">It will commonly be a private member of the main form.</span></span> <span data-ttu-id="b8304-117">Teď, když jste definovali vaší třídy, je potřeba ho vytvořit vazbu na vlastnost; v takovém případě <xref:System.Windows.Forms.Form.BackColor%2A> vlastnost formuláře.</span><span class="sxs-lookup"><span data-stu-id="b8304-117">Now that you have defined your class, you need to bind it to a property; in this case, the <xref:System.Windows.Forms.Form.BackColor%2A> property of your form.</span></span> <span data-ttu-id="b8304-118">Můžete to udělat v formuláře `Load` obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="b8304-118">You can accomplish this in your form's `Load` event handler.</span></span>  
  
     [!code-csharp[ApplicationSettings.Create#2](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/Form1.cs#2)]
     [!code-vb[ApplicationSettings.Create#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/Form1.vb#2)]  
  
4.  <span data-ttu-id="b8304-119">Pokud zadáte způsob, jak změnit nastavení v době běhu, je potřeba uložit aktuální nastavení uživatele na disk, když se zavře formulář, jinak tyto změny budou ztraceny.</span><span class="sxs-lookup"><span data-stu-id="b8304-119">If you provide a way to change settings at run time, you will need to save the user's current settings to disk when your form closes, or else these changes will be lost.</span></span>  
  
     [!code-csharp[ApplicationSettings.Create#3](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/Form1.cs#3)]
     [!code-vb[ApplicationSettings.Create#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/Form1.vb#3)]  
  
     <span data-ttu-id="b8304-120">Jste teď úspěšně vytvořili nové nastavení aplikace a vázán na zadanou vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b8304-120">You have now successfully created a new application setting and bound it to the specified property.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="b8304-121">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b8304-121">.NET Framework Security</span></span>  
 <span data-ttu-id="b8304-122">Ve výchozím nastavení <xref:System.Configuration.LocalFileSettingsProvider>, opakuje informace ke konfiguračním souborům jako prostý text.</span><span class="sxs-lookup"><span data-stu-id="b8304-122">The default settings provider, <xref:System.Configuration.LocalFileSettingsProvider>, persists information to configuration files as plain text.</span></span> <span data-ttu-id="b8304-123">Toto omezení zabezpečení k zabezpečení přístupu k souboru v operačním systému k dispozici pro aktuálního uživatele.</span><span class="sxs-lookup"><span data-stu-id="b8304-123">This limits security to the file access security provided by the operating system for the current user.</span></span> <span data-ttu-id="b8304-124">Z tohoto důvodu musíte věnovat pozornost s informacemi uloženými v konfiguračních souborech.</span><span class="sxs-lookup"><span data-stu-id="b8304-124">Because of this, care must be taken with the information stored in configuration files.</span></span> <span data-ttu-id="b8304-125">Jeden běžně používá pro nastavení aplikace je například ukládání připojovacích řetězců, které odkazují na úložiště dat aplikace.</span><span class="sxs-lookup"><span data-stu-id="b8304-125">For example, one common use for application settings is to store connection strings that point to the application's data store.</span></span> <span data-ttu-id="b8304-126">Kvůli zajištění zabezpečení, ale tyto řetězce by neměl obsahovat hesla.</span><span class="sxs-lookup"><span data-stu-id="b8304-126">However, because of security concerns, such strings should not include passwords.</span></span> <span data-ttu-id="b8304-127">Další informace o připojovacích řetězcích najdete v tématu <xref:System.Configuration.SpecialSetting>.</span><span class="sxs-lookup"><span data-stu-id="b8304-127">For more information about connection strings, see <xref:System.Configuration.SpecialSetting>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8304-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b8304-128">See also</span></span>
- <xref:System.Configuration.SpecialSettingAttribute>
- <xref:System.Configuration.LocalFileSettingsProvider>
- [<span data-ttu-id="b8304-129">Přehled nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="b8304-129">Application Settings Overview</span></span>](application-settings-overview.md)
- [<span data-ttu-id="b8304-130">Postupy: Ověření nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="b8304-130">How to: Validate Application Settings</span></span>](how-to-validate-application-settings.md)
