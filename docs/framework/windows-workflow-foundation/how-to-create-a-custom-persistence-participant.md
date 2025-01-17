---
title: 'Postupy: Vytvoření vlastního účastníka trvalosti'
ms.date: 03/30/2017
ms.assetid: 1d9cc47a-8966-4286-94d5-4221403d9c06
ms.openlocfilehash: 47283375b618422d91a6279ee9049fae469f540a
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989671"
---
# <a name="how-to-create-a-custom-persistence-participant"></a>Postupy: Vytvoření vlastního účastníka trvalosti
Následující postup obsahuje kroky k vytvoření účastníka trvalosti. Ukázková implementace účastníků trvalosti najdete v tématu věnovaném ukázce [Persistence](https://go.microsoft.com/fwlink/?LinkID=177735) a [rozšiřitelnosti obchodu](store-extensibility.md) .  
  
1. Vytvořte třídu odvozenou z <xref:System.Activities.Persistence.PersistenceParticipant> <xref:System.Activities.Persistence.PersistenceIOParticipant> třídy nebo. Třída PersistenceIOParticipant nabízí stejné body rozšiřitelnosti jako třída PersistenceParticipant, kromě toho, že se může zúčastnit I vstupně-výstupních operací. Použijte jeden nebo několik následujících kroků.  
  
2. Implementujte <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> metodu. Metoda **CollectValues** má dva parametry slovníku, jeden pro ukládání hodnot pro čtení a zápis a druhý pro ukládání hodnot pouze pro zápis (používá se později v dotazech). V této metodě byste měli tyto slovníky naplnit daty, která jsou specifická pro účastníka trvalosti. Každý slovník obsahuje název hodnoty jako klíč a hodnotu samotnou jako <xref:System.Runtime.DurableInstancing.InstanceValue> objekt.  
  
    Hodnoty ve slovníku readWriteValues jsou zabaleny jako objekty **InstanceValue** . Hodnoty ve slovníku jen pro zápis jsou zabaleny jako objekty **InstanceValue** s nastaveným InstanceValueOptions. optional a InstanceValueOption. WriteOnly. Každý **InstanceValue** poskytovaný implementacemi **CollectValues** napříč všemi účastníky trvalosti musí mít jedinečný název.
  
    ```csharp  
    protected virtual void CollectValues(out IDictionary<XName,Object> readWriteValues, out IDictionary<XName,Object> writeOnlyValues)
    {
    }
    ```  
  
3. Implementujte <xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A> metodu. Metoda **MapValues** přebírá dva parametry podobné parametrům, které přijímá metoda **CollectValues** . Všechny hodnoty shromážděné ve fázi **CollectValues** jsou předány prostřednictvím těchto parametrů slovníku. Nové hodnoty přidané fází **MapValues** jsou přidány do hodnot pouze pro zápis.  Slovník pouze pro zápis se používá k poskytnutí dat externímu zdroji, který není přímo přidružen k hodnotám instance. Každá hodnota poskytnutá implementacemi metody **MapValues** napříč všemi účastníky trvalosti musí mít jedinečný název.  
  
    ```csharp  
    protected virtual IDictionary<XName,Object> MapValues(IDictionary<XName,Object> readWriteValues,IDictionary<XName,Object> writeOnlyValues)
    {
    }
    ```  
  
     Metoda poskytuje funkce, které <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> nejsou v tom, že umožňuje závislost na jiné hodnotě poskytované jiným účastníkem trvalosti <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> , který ještě nebyl zpracován. <xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A>  
  
4. Implementujte metodu **PublishValues** . Metoda **PublishValues** přijímá slovník obsahující všechny hodnoty načtené z úložiště trvalosti.  
  
    ```csharp  
    protected virtual void PublishValues(IDictionary<XName,Object> readWriteValues)
    {
    }
    ```  
  
5. Implementujte metodu **BeginOnSave** , pokud účastník je v/v účastníkem trvalého vstupu/výstupu. Tato metoda je volána během operace uložení. V této metodě byste měli provést vstupně-výstupní pomocný do trvalých (ukládaných) instancí pracovního postupu.  Pokud hostitel používá transakci pro odpovídající příkaz trvalosti, je stejná transakce uvedena v transakci. Current.  PersistenceIOParticipants může navíc inzerovat požadavek na konzistenci transakcí. v takovém případě hostitel vytvoří transakci pro epizodu Persistence, pokud by se nepoužilo jinak.  
  
    ```csharp  
    protected virtual IAsyncResult BeginOnSave(IDictionary<XName,Object> readWriteValues, IDictionary<XName,Object> writeOnlyValues, TimeSpan timeout, AsyncCallback callback, Object state)
    {
    }
    ```  
  
6. Implementujte metodu **BeginOnLoad** , pokud účastník je v/v účastníkem trvalého vstupu/výstupu. Tato metoda je volána během operace načítání. V této metodě byste měli provést vstupně-výstupní pomocný načtení instancí pracovního postupu. Pokud hostitel používá transakci pro odpovídající příkaz trvalosti, je stejná transakce uvedena v transakci. Current. Účastníci I/O trvalosti můžou inzerovat požadavek na konzistenci transakcí. v takovém případě hostitel vytvoří transakci pro epizodu Persistence, pokud by se nepoužila jinak.  
  
    ```csharp  
    protected virtual IAsyncResult BeginOnLoad(IDictionary<XName,Object> readWriteValues, TimeSpan timeout, AsyncCallback callback, Object state)
    {
    }
    ```
