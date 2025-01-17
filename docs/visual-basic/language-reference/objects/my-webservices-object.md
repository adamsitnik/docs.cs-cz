---
title: My. WebServices – objekt (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.WebServices
- My.MyProject.WebServices
helpviewer_keywords:
- My.WebServices object
ms.assetid: f188dc05-2c75-41b6-bb68-122d1c3110a2
ms.openlocfilehash: c887f9b7c5a41c0aa02016354c46d5507b103d25
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918184"
---
# <a name="mywebservices-object"></a>My.WebServices – objekt
Poskytuje vlastnosti pro vytvoření a přístup k jedné instanci každé webové služby XML, na kterou odkazuje aktuální projekt.  
  
## <a name="remarks"></a>Poznámky  
 `My.WebServices` Objekt poskytuje instanci každé webové služby, na kterou odkazuje aktuální projekt. Každá instance je vytvořena na vyžádání. K těmto webovým službám můžete přistupovat prostřednictvím vlastností `My.WebServices` objektu. Název vlastnosti je stejný jako název webové služby, ke které vlastnost přistupuje. Libovolná třída, která <xref:System.Web.Services.Protocols.SoapHttpClientProtocol> dědí z, je webová služba. Informace o tom, jak přidat webové služby do projektu, najdete v tématu [přístup k aplikačním webovým službám](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).  
  
 `My.WebServices` Objekt zveřejňuje pouze webové služby přidružené k aktuálnímu projektu. Neposkytuje přístup k webovým službám deklarovaným v odkazovaných knihovnách DLL. Chcete-li získat přístup k webové službě, kterou poskytuje knihovna DLL, je nutné použít kvalifikovaný název webové služby ve formě *Název_souboru_DLL*. *Služba WebService*. Další informace najdete v tématu [přístup k aplikačním webovým službám](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).  
  
 Objekt a jeho vlastnosti nejsou k dispozici pro webové aplikace.  
  
## <a name="properties"></a>Vlastnosti  
 Každá vlastnost `My.WebServices` objektu poskytuje přístup k instanci webové služby, na kterou odkazuje aktuální projekt. Název vlastnosti je stejný jako název webové služby, ke které vlastnost přistupuje, a typ vlastnosti je stejný jako typ webové služby.  
  
> [!NOTE]
> Pokud dojde ke kolizi názvů, název vlastnosti pro přístup k webové službě je *RootNamespace*_*obor názvů*\_*ServiceName*. Zvažte například dvě webové služby s názvem `Service1`. Pokud se jedna z těchto služeb nachází v kořenovém `WindowsApplication1` oboru názvů a v `Namespace1`oboru názvů, měli byste k této službě `My.WebServices.WindowsApplication1_Namespace1_Service1`přistupovat pomocí.  
  
 Při prvním přístupu k jedné z `My.WebServices` vlastností objektu vytvoří nová instance webové služby a uloží ji. Následné přístupy této vlastnosti vrátí tuto instanci webové služby.  
  
 Webovou službu můžete vyřadit tak, že přiřadíte `Nothing` vlastnost pro tuto webovou službu. Vlastnost setter přiřadí `Nothing` uložené hodnotě. Pokud přiřadíte jinou hodnotu než `Nothing` k vlastnosti, metoda setter <xref:System.ArgumentException> vyvolá výjimku.  
  
 Můžete otestovat, zda vlastnost `My.WebServices` objektu ukládá instanci webové služby `Is` pomocí operátoru OR `IsNot` . Tyto operátory můžete použít ke kontrole, zda je `Nothing`hodnota vlastnosti.  
  
> [!NOTE]
> `Is` Operátor OR `IsNot` obvykle musí číst hodnotu vlastnosti pro provedení porovnání. Pokud je však vlastnost aktuálně uložena `Nothing`, vytvoří vlastnost novou instanci webové služby a poté vrátí tuto instanci. Nicméně kompilátor Visual Basic považuje vlastnosti `My.WebServices` objektu za speciálně a `Is` umožňuje operátoru OR `IsNot` kontrolovat stav vlastnosti bez změny její hodnoty.  
  
## <a name="example"></a>Příklad  
 Tento příklad volá `FahrenheitToCelsius` metodu `TemperatureConverter` webové služby XML a vrátí výsledek.  
  
 [!code-vb[VbVbalrMyWebService#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWebService/VB/Form1.vb#1)]  
  
 Aby tento příklad fungoval, musí mít projekt odkaz na webovou službu s názvem `Converter`a tato webová služba musí vystavit `ConvertTemperature` tuto metodu. Další informace najdete v tématu [přístup k aplikačním webovým službám](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).  
  
 Tento kód nefunguje v projektu webové aplikace.  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="availability-by-project-type"></a>Dostupnost podle typu projektu  
  
|Typ projektu|K dispozici|  
|---|---|  
|Aplikace systému Windows|**Ano**|  
|Knihovna tříd|**Ano**|  
|Konzolová aplikace|**Ano**|  
|Knihovna ovládacích prvků Windows|**Ano**|  
|Knihovna webového ovládacího prvku|**Ano**|  
|Služba systému Windows|**Ano**|  
|Web|Ne|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Web.Services.Protocols.SoapHttpClientProtocol>
- <xref:System.ArgumentException>
- [Přístup k aplikačním webovým službám](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)
