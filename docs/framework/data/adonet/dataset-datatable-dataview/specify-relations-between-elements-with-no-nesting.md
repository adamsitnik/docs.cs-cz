---
title: Určení relací mezi elementy bez vnoření
ms.date: 03/30/2017
ms.assetid: e31325da-7691-4d33-acf4-99fccca67006
ms.openlocfilehash: 4b7b216e58f36302db29c4b4b5176339521b0f17
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61607914"
---
# <a name="specify-relations-between-elements-with-no-nesting"></a><span data-ttu-id="9b54a-102">Určení relací mezi elementy bez vnoření</span><span class="sxs-lookup"><span data-stu-id="9b54a-102">Specify Relations Between Elements with No Nesting</span></span>
<span data-ttu-id="9b54a-103">Pokud nejsou vnořené elementy, vytvoří se žádné implicitní vztahy.</span><span class="sxs-lookup"><span data-stu-id="9b54a-103">When elements are not nested, no implicit relations are created.</span></span> <span data-ttu-id="9b54a-104">Můžete však explicitně zadat relací mezi elementy, které nejsou vnořené pomocí **msdata:Relationship** poznámky.</span><span class="sxs-lookup"><span data-stu-id="9b54a-104">You can, however, explicitly specify relations between elements that are not nested by using the **msdata:Relationship** annotation.</span></span>  
  
 <span data-ttu-id="9b54a-105">Následující příklad ukazuje schématu XML, ve kterém **msdata:Relationship** je určena anotace mezi **pořadí** a **OrderDetail** prvky, které nejsou vnořené.</span><span class="sxs-lookup"><span data-stu-id="9b54a-105">The following example shows an XML Schema in which the **msdata:Relationship** annotation is specified between the **Order** and **OrderDetail** elements, which are not nested.</span></span> <span data-ttu-id="9b54a-106">**Msdata:Relationship** poznámka určena jako podřízený prvek **schématu** elementu.</span><span class="sxs-lookup"><span data-stu-id="9b54a-106">The **msdata:Relationship** annotation is specified as the child element of the **Schema** element.</span></span>  
  
```xml  
<xs:schema id="MyDataSet" xmlns=""   
             xmlns:xs="http://www.w3.org/2001/XMLSchema"   
             xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
 <xs:element name="MyDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
      <xs:element name="OrderDetail">  
       <xs:complexType>  
         <xs:sequence>  
           <xs:element name="OrderNo" type="xs:string" />  
           <xs:element name="ItemNo" type="xs:string" />  
         </xs:sequence>  
       </xs:complexType>  
      </xs:element>  
      <xs:element name="Order">  
       <xs:complexType>  
         <xs:sequence>  
           <xs:element name="OrderNumber" type="xs:string" />  
           <xs:element name="EmpNumber" type="xs:string" />  
         </xs:sequence>  
       </xs:complexType>  
      </xs:element>  
    </xs:choice>  
  </xs:complexType>  
  
  </xs:element>  
   <xs:annotation>  
     <xs:appinfo>  
       <msdata:Relationship name="OrdOrderDetailRelation"  
                            msdata:parent="Order"   
                            msdata:child="OrderDetail"   
                            msdata:parentkey="OrderNumber"   
                            msdata:childkey="OrderNo"/>  
     </xs:appinfo>  
  </xs:annotation>  
</xs:schema>  
```  
  
 <span data-ttu-id="9b54a-107">Vytvoří proces mapování schématu XML definice jazyk (XSD) schématu <xref:System.Data.DataSet> s **pořadí** a **OrderDetail** tabulky a relace určena v rozsahu mezi těmito dvěma tabulkami, jak je znázorněno níže.</span><span class="sxs-lookup"><span data-stu-id="9b54a-107">The XML Schema definition language (XSD) schema mapping process creates a <xref:System.Data.DataSet> with **Order** and **OrderDetail** tables and a relationship specified between these two tables, as shown below.</span></span>  
  
```  
RelationName: OrdOrderDetailRelation  
ParentTable: Order  
ParentColumns: OrderNumber   
ChildTable: OrderDetail  
ChildColumns: OrderNo   
Nested: False  
```  
  
## <a name="see-also"></a><span data-ttu-id="9b54a-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9b54a-108">See also</span></span>

- [<span data-ttu-id="9b54a-109">Generování relací datové sady ze schématu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="9b54a-109">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="9b54a-110">Mapování omezení schématu XML (XSD) k omezením datové sady</span><span class="sxs-lookup"><span data-stu-id="9b54a-110">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="9b54a-111">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="9b54a-111">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
