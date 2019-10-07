---
title: 'Postupy: generování objektového modelu jako externího souboru'
ms.date: 03/30/2017
ms.assetid: 2496fa06-3df4-4ecb-86c4-70a49ea08565
ms.openlocfilehash: 915c02de55211efa24a4aa9f21ddc2c7e60fa41a
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002736"
---
# <a name="how-to-generate-the-object-model-as-an-external-file"></a>Postupy: generování objektového modelu jako externího souboru
Jako alternativu k mapování na základě atributů můžete vytvořit objektový model jako externí soubor XML pomocí nástroje příkazového řádku SQLMetal. Další informace naleznete v tématu [SqlMetal. exe (Nástroj pro generování kódu)](../../../../tools/sqlmetal-exe-code-generation-tool.md). Pomocí externího souboru mapování XML můžete v kódu zmenšit přehlednost. Můžete také změnit chování úpravou externího souboru bez nutnosti opětovné kompilace binárních souborů aplikace. Další informace najdete v tématu [externí mapování](external-mapping.md).  
  
> [!NOTE]
> Návrhář relací objektů nepodporuje generování externího mapovacího souboru.  
  
## <a name="example"></a>Příklad  
 Následující příkaz generuje externí mapovací soubor z ukázkové databáze Northwind.  
  
```console  
sqlmetal /server:myserver /database:northwind /map:externalfile.xml  
```  
  
## <a name="example"></a>Příklad  
 Následující úryvek z externího souboru mapování zobrazuje mapování pro tabulku Customers v ukázkové databázi Northwind. Tento úryvek byl vygenerován spuštěním SQLMetal s možností **/map** .  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Database xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" Name="northwnd">  
  <Table Name="Customers">  
    <Type Name=".Customer">  
      <Column Name="CustomerID" Member="CustomerID" Storage="_CustomerID" DbType="NChar(5) NOT NULL" CanBeNull="False" IsPrimaryKey="True" />  
      <Column Name="CompanyName" Member="CompanyName" Storage="_CompanyName" DbType="NVarChar(40) NOT NULL" CanBeNull="False" />  
      <Column Name="ContactName" Member="ContactName" Storage="_ContactName" DbType="NVarChar(30)" />  
      <Column Name="ContactTitle" Member="ContactTitle" Storage="_ContactTitle" DbType="NVarChar(30)" />  
      <Column Name="Address" Member="Address" Storage="_Address" DbType="NVarChar(60)" />  
      <Column Name="City" Member="City" Storage="_City" DbType="NVarChar(15)" />  
      <Column Name="Region" Member="Region" Storage="_Region" DbType="NVarChar(15)" />  
      <Column Name="PostalCode" Member="PostalCode" Storage="_PostalCode" DbType="NVarChar(10)" />  
      <Column Name="Country" Member="Country" Storage="_Country" DbType="NVarChar(15)" />  
      <Column Name="Phone" Member="Phone" Storage="_Phone" DbType="NVarChar(24)" />  
      <Column Name="Fax" Member="Fax" Storage="_Fax" DbType="NVarChar(24)" />  
      <Association Name="FK_CustomerCustomerDemo_Customers" Member="CustomerCustomerDemos" Storage="_CustomerCustomerDemos" ThisKey="CustomerID" OtherTable="CustomerCustomerDemo" OtherKey="CustomerID" DeleteRule="NO ACTION" />  
      <Association Name="FK_Orders_Customers" Member="Orders" Storage="_Orders" ThisKey="CustomerID" OtherTable="Orders" OtherKey="CustomerID" DeleteRule="NO ACTION" />  
    </Type>  
  </Table>  
</Database>  
```  
  
## <a name="see-also"></a>Viz také:

- [Vytvoření objektového modelu](creating-the-object-model.md)
- [Externí mapování](external-mapping.md)
- [Postupy: Generování objektového modelu v jazyce Visual Basic nebo C#](how-to-generate-the-object-model-in-visual-basic-or-csharp.md)
