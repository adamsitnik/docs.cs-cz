---
title: 'Postupy: Deserializace objektu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- deserializing objects
- objects, deserializing steps
ms.assetid: 287129c8-035a-4fea-b7b3-4790057ca076
ms.openlocfilehash: e1a960d39319beee1c3c257fcd3ade207de11010
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2019
ms.locfileid: "65881141"
---
# <a name="how-to-deserialize-an-object"></a>Postupy: Deserializace objektu
Při deserializaci objektu, formát přenosu Určuje, zda vytváříte objekt datového proudu nebo souboru. Po formát přenosu je určen, můžete volat <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> nebo <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> metod, podle potřeby.  
  
### <a name="to-deserialize-an-object"></a>K deserializaci objektu  
  
1. Vytvořit <xref:System.Xml.Serialization.XmlSerializer> pomocí typ objektu určeného k deserializaci.  
  
2. Volání <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> metodu za účelem vytvoření repliky objektu. Při deserializaci, musíte přetypovat vráceného objektu na typ původní, jak je znázorněno v následujícím příkladu, který deserializuje objekt ze souboru (Ačkoli může být také deserializovat z datového proudu).  
  
    ```vb  
    Dim myObject As MySerializableClass  
    ' Construct an instance of the XmlSerializer with the type  
    ' of object that is being deserialized.  
    Dim mySerializer As XmlSerializer = New XmlSerializer(GetType(MySerializableClass))  
    ' To read the file, create a FileStream.  
    Dim myFileStream As FileStream = _  
    New FileStream("myFileName.xml", FileMode.Open)  
    ' Call the Deserialize method and cast to the object type.  
    myObject = CType( _  
    mySerializer.Deserialize(myFileStream), MySerializableClass)  
    ```  
  
    ```csharp  
    MySerializableClass myObject;  
    // Construct an instance of the XmlSerializer with the type  
    // of object that is being deserialized.  
    XmlSerializer mySerializer =   
    new XmlSerializer(typeof(MySerializableClass));  
    // To read the file, create a FileStream.  
    FileStream myFileStream =   
    new FileStream("myFileName.xml", FileMode.Open);  
    // Call the Deserialize method and cast to the object type.  
    myObject = (MySerializableClass)   
    mySerializer.Deserialize(myFileStream)  
    ```  
  
## <a name="see-also"></a>Viz také:

- [Představení serializace XML](../../../docs/standard/serialization/introducing-xml-serialization.md)
- [Postupy: Serializace objektu](../../../docs/standard/serialization/how-to-serialize-an-object.md)
