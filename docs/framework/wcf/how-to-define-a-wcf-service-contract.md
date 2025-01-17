---
title: 'Kurz: Definování kontraktu Windows Communication Foundation služby'
ms.date: 03/19/2019
helpviewer_keywords:
- service contracts [WCF], defining
dev_langs:
- CSharp
- VB
ms.assetid: 67bf05b7-1d08-4911-83b7-a45d0b036fc3
ms.openlocfilehash: ba88fc6ba4cba8d46ed1b43080d471b1b7c4bd75
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928876"
---
# <a name="tutorial-define-a-windows-communication-foundation-service-contract"></a>Kurz: Definování kontraktu Windows Communication Foundation služby

Tento kurz popisuje prvních pět úloh nutných k vytvoření aplikace Basic Windows Communication Foundation (WCF). Přehled kurzů najdete v tématu [kurz: Začněte s Windows Communication Foundation aplikacemi](getting-started-tutorial.md).

Při vytváření služby WCF je vaším prvním úkolem Definování kontraktu služby. Kontrakt služby určuje, které operace služba podporuje. Operaci lze představit jako metodu webové služby. Kontrakty služby vytvoříte tak, že definujete rozhraní Visual C# nebo Visual Basic (VB). Rozhraní má následující vlastnosti:

- Každá metoda v rozhraní odpovídá konkrétní operaci služby. 
- Pro každé rozhraní je nutné použít <xref:System.ServiceModel.ServiceContractAttribute> atribut.
- Pro každou operaci/metodu je nutné použít <xref:System.ServiceModel.OperationContractAttribute> atribut. 

V tomto kurzu se naučíte:
> [!div class="checklist"]
>
> - Vytvořte projekt **knihovny služby WCF** .
> - Definujte rozhraní kontraktu služby.

## <a name="create-a-wcf-service-library-project-and-define-a-service-contract-interface"></a>Vytvoření projektu knihovny služby WCF a definování rozhraní kontraktu služby

1. Otevřete Visual Studio jako správce. Provedete to tak, že v nabídce **Start** vyberete program Visual Studio a v místní nabídce vyberete **Další** > **Spustit jako správce** .

2. Vytvořte projekt **knihovny služby WCF** .

   1. Z **souboru** nabídce vyberte možnost **nový** > **projektu**.

   2. V dialogovém okně **Nový projekt** rozbalte na levé straně položku  **C# Visual** nebo **Visual Basic**a pak vyberte kategorii **WCF** . Visual Studio zobrazí seznam šablon projektů v části Center v okně. Vyberte **knihovnu služby WCF**.

      > [!NOTE]
      > Pokud nevidíte kategorii šablony projektů **WCF** , bude pravděpodobně nutné nainstalovat **Windows Communication Foundation** součást sady Visual Studio. V dialogovém okně **Nový projekt** vyberte odkaz **otevřít instalační program pro Visual Studio** na levé straně. Vyberte kartu **jednotlivé součásti** a v kategorii **vývojové aktivity** vyhledejte a vyberte **Windows Communication Foundation** . Chcete-li zahájit instalaci komponenty, klikněte na tlačítko **Upravit** .

   3. V dolní části okna zadejte *GettingStartedLib* pro **název** a *soubor GettingStarted* pro **název řešení**. 

   4. Vyberte **OK**.

      Visual Studio vytvoří projekt, který má tři soubory: *IService1.cs* (nebo *IService1. vb* pro projekt Visual Basic), *Service1.cs* (nebo *Service1. vb* pro Visual Basic projekt) a *App. config*. Visual Studio definuje tyto soubory následujícím způsobem: 
      - Soubor *IService1* obsahuje výchozí definici kontraktu služby. 
      - Soubor *Service1* obsahuje výchozí implementaci kontraktu služby. 
      - Soubor *App. config* obsahuje informace o konfiguraci potřebné k načtení výchozí služby pomocí nástroje pro hostování služby Visual Studio WCF. Další informace o nástroji pro hostování služby WCF najdete v tématu [Hostitel služby WCF (WcfSvcHost. exe)](wcf-service-host-wcfsvchost-exe.md).

      > [!NOTE]
      > Pokud jste nainstalovali Visual Studio s Visual Basic nastavení vývojářského prostředí, řešení může být skryté. Pokud se jedná o tento případ, vyberte **Možnosti** v nabídce **nástroje** a pak v okně **Možnosti** vyberte **projekty a řešení** > **Obecné** . Vyberte možnost **vždy zobrazit řešení**. Ověřte také, že je vybrána možnost **Uložit nové projekty při vytvoření** .

3. Z **Průzkumník řešení**otevřete soubor **IService1.cs** nebo **IService1. vb** a nahraďte jeho kód následujícím kódem:

    ```csharp
    using System;
    using System.ServiceModel;

    namespace GettingStartedLib
    {
            [ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]
            public interface ICalculator
            {
                [OperationContract]
                double Add(double n1, double n2);
                [OperationContract]
                double Subtract(double n1, double n2);
                [OperationContract]
                double Multiply(double n1, double n2);
                [OperationContract]
                double Divide(double n1, double n2);
            }
    }
    ```

    ```vb
    Imports System.ServiceModel

    Namespace GettingStartedLib

        <ServiceContract(Namespace:="http://Microsoft.ServiceModel.Samples")> _
        Public Interface ICalculator

            <OperationContract()> _
            Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double
            <OperationContract()> _
            Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double
            <OperationContract()> _
            Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double
            <OperationContract()> _
            Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double
        End Interface
    End Namespace
    ```

     Tato Smlouva definuje online kalkulačku. Všimněte si `ICalculator` , že rozhraní je označeno <xref:System.ServiceModel.ServiceContractAttribute> atributem ( `ServiceContract`zjednodušeno jako). Tento atribut definuje obor názvů pro jednoznačnost názvu kontraktu. Kód označí každou operaci <xref:System.ServiceModel.OperationContractAttribute> kalkulačky atributem (zjednodušeno jako `OperationContract`).

## <a name="next-steps"></a>Další postup

V tomto kurzu jste se naučili:
> [!div class="checklist"]
>
> - Vytvořte projekt knihovny služby WCF.
> - Definujte rozhraní kontraktu služby.

Přejděte k dalšímu kurzu, kde se dozvíte, jak implementovat kontrakt služby WCF.

> [!div class="nextstepaction"]
> [Kurz: Implementace kontraktu služby WCF](how-to-implement-a-wcf-contract.md)
