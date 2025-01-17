---
title: 'Postupy: Zadání vazby služby v konfiguraci'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 885037f7-1c2b-4d7a-90d9-06b89be172f2
ms.openlocfilehash: ef41514a57d08d66fcba2dbaeb8c8d88cdcf3875
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040709"
---
# <a name="how-to-specify-a-service-binding-in-configuration"></a>Postupy: Zadání vazby služby v konfiguraci
V tomto příkladu je pro základní službu kalkulačky definována smlouva `ICalculator`, služba je implementována ve třídě `CalculatorService` a poté je její koncový bod nakonfigurován v souboru Web. config, kde je určeno, že služba používá <xref:System.ServiceModel.BasicHttpBinding>. Popis postupu konfigurace této služby pomocí kódu namísto konfigurace najdete v tématu [How to: určení vazby služby v kódu](how-to-specify-a-service-binding-in-code.md).  
  
 Obvykle je osvědčeným postupem zadat vazby a informace o adrese deklarativně v konfiguraci, nikoli imperativně v kódu. Definování koncových bodů v kódu obvykle není praktické, protože vazby a adresy nasazené služby se obvykle liší od těch, které se použily při vývoji služby. Obecně platí, že zachování vazby a adresování informací z kódu umožňuje jejich změnu bez nutnosti opětovné kompilace nebo opětovného nasazení aplikace.  
  
 Pomocí [nástroje Editor konfigurací (SvcConfigEditor. exe)](configuration-editor-tool-svcconfigeditor-exe.md)můžete provádět všechny následující kroky konfigurace.  
  
 Zdrojovou kopii tohoto příkladu naleznete v tématu [BasicBinding](./samples/basicbinding.md).  
  
## <a name="to-specify-the-basichttpbinding-to-use-to-configure-the-service"></a>Určení BasicHttpBinding, který se má použít ke konfiguraci služby  
  
1. Definujte kontrakt služby pro typ služby.  
  
     [!code-csharp[C_HowTo_ConfigureServiceBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureservicebinding/cs/source.cs#1)]
     [!code-vb[C_HowTo_ConfigureServiceBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_configureservicebinding/vb/source.vb#1)]  
  
2. Implementujte kontrakt služby ve třídě služby.  
  
     [!code-csharp[C_HowTo_ConfigureServiceBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureservicebinding/cs/source.cs#2)]
     [!code-vb[C_HowTo_ConfigureServiceBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_configureservicebinding/vb/source.vb#2)]  
  
    > [!NOTE]
    > V rámci implementace služby nejsou zadány informace o adrese nebo vazbě. Také není nutné zapisovat kód pro načtení těchto informací z konfiguračního souboru.  
  
3. Vytvořte soubor Web. config pro konfiguraci koncového bodu pro `CalculatorService`, který používá <xref:System.ServiceModel.WSHttpBinding>.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.serviceModel>  
        <services>  
          <service name=" CalculatorService" >  
            
            <!-- Leave the address blank to be populated by default -->
            <!-- from the hosting environment,in this case IIS, so -->
            <!-- the address will just be that of the IIS Virtual -->
            <!-- Directory. -->

            <!-- Specify the binding configuration name for that -->
            <!-- binding type. This is optional but useful if you -->
            <!-- want to modify the properties of the binding. -->
            <!-- The bindingConfiguration name Binding1 is defined -->
            <!-- below in the bindings element. -->
            <endpoint   
                address=""   
                binding="wsHttpBinding"  
                bindingConfiguration="Binding1"  
                contract="ICalculator" />  
          </service>  
        </services>  
        <bindings>  
          <wsHttpBinding>  
            <binding name="Binding1">  
              <!-- Binding property values can be modified here. -->  
              <!-- See the next procedure. -->  
            </binding>  
          </wsHttpBinding>  
       </bindings>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
4. Vytvořte soubor Service. svc, který obsahuje následující řádek, a umístěte ho do virtuálního adresáře Internetová informační služba (IIS).  
  
    ```  
    <%@ServiceHost language=c# Service="CalculatorService" %>   
    ```  
  
## <a name="to-modify-the-default-values-of-the-binding-properties"></a>Úprava výchozích hodnot vlastností vazby  
  
1. Chcete-li upravit jednu z hodnot výchozí vlastnosti <xref:System.ServiceModel.WSHttpBinding>, vytvořte nový název konfigurace vazby-`<binding name="Binding1">`-v rámci > prvku [\<wsHttpBinding](../configure-apps/file-schema/wcf/wshttpbinding.md) a nastavte nové hodnoty atributů vazby v tomto elementu vazby. Chcete-li například změnit výchozí hodnoty časového limitu pro otevření a ukončení 1 minuty na 2 minuty, přidejte následující do konfiguračního souboru.  
  
    ```xml  
    <wsHttpBinding>  
      <binding name="Binding1"  
               closeTimeout="00:02:00"  
               openTimeout="00:02:00">  
      </binding>  
    </wsHttpBinding>  
    ```  
  
## <a name="see-also"></a>Viz také:

- [Používání vazeb ke konfiguraci služeb a klientů](using-bindings-to-configure-services-and-clients.md)
- [Zadání adresy koncového bodu](specifying-an-endpoint-address.md)
