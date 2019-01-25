---
title: MsmqTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 1c89f073-9ed3-4025-a8c5-13535a0f526b
ms.openlocfilehash: d37ee4527226d9347e24fc2ee8007a263c71f198
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54564874"
---
# <a name="msmqtransportbindingelement"></a><span data-ttu-id="35c36-102">MsmqTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="35c36-102">MsmqTransportBindingElement</span></span>
<span data-ttu-id="35c36-103">MsmqTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="35c36-103">MsmqTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35c36-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="35c36-104">Syntax</span></span>  
  
```csharp
class MsmqTransportBindingElement : MsmqBindingElementBase  
{  
  sint32 MaxPoolSize;  
  string QueueTransferProtocol;  
  boolean UseActiveDirectory;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="35c36-105">Metody</span><span class="sxs-lookup"><span data-stu-id="35c36-105">Methods</span></span>  
 <span data-ttu-id="35c36-106">Třída prvkem MsmqTransportBindingElement nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="35c36-106">The MsmqTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="35c36-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="35c36-107">Properties</span></span>  
 <span data-ttu-id="35c36-108">Třída prvkem MsmqTransportBindingElement má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="35c36-108">The MsmqTransportBindingElement class has the following properties:</span></span>  
  
### <a name="maxpoolsize"></a><span data-ttu-id="35c36-109">MaxPoolSize</span><span class="sxs-lookup"><span data-stu-id="35c36-109">MaxPoolSize</span></span>  
 <span data-ttu-id="35c36-110">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="35c36-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="35c36-111">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="35c36-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="35c36-112">Maximální velikost fondu, který obsahuje objekty interní MSMQ zprávy.</span><span class="sxs-lookup"><span data-stu-id="35c36-112">The maximum size of the pool that contains internal MSMQ message objects.</span></span>  
  
### <a name="queuetransferprotocol"></a><span data-ttu-id="35c36-113">QueueTransferProtocol</span><span class="sxs-lookup"><span data-stu-id="35c36-113">QueueTransferProtocol</span></span>  
 <span data-ttu-id="35c36-114">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="35c36-114">Data type: string</span></span>  
  
 <span data-ttu-id="35c36-115">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="35c36-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="35c36-116">Hodnota výčtu, která označuje přenos zařazených do fronty komunikačního kanálu, který tato vazba používá.</span><span class="sxs-lookup"><span data-stu-id="35c36-116">An enumeration value that indicates the queued communication channel transport that this binding uses.</span></span>  
  
### <a name="useactivedirectory"></a><span data-ttu-id="35c36-117">UseActiveDirectory</span><span class="sxs-lookup"><span data-stu-id="35c36-117">UseActiveDirectory</span></span>  
 <span data-ttu-id="35c36-118">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="35c36-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="35c36-119">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="35c36-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="35c36-120">Vrátí logickou hodnotu, která určuje, zda mají být adresy fronty převedeny pomocí služby Active Directory.</span><span class="sxs-lookup"><span data-stu-id="35c36-120">Returns a Boolean value that indicates whether queue addresses should be converted using Active Directory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35c36-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="35c36-121">Requirements</span></span>  
  
|<span data-ttu-id="35c36-122">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="35c36-122">MOF</span></span>|<span data-ttu-id="35c36-123">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="35c36-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="35c36-124">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="35c36-124">Namespace</span></span>|<span data-ttu-id="35c36-125">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="35c36-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="35c36-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="35c36-126">See also</span></span>
- <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>
