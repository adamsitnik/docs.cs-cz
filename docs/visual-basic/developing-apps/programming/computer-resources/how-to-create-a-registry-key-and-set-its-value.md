---
title: 'Postupy: Vytvořte klíč registru a nastavte jeho hodnotu v Visual Basic'
ms.date: 07/20/2015
f1_keywords:
- RegistryKey.CreateSubKey
- RegistryKey.SetValue
helpviewer_keywords:
- registry keys [Visual Basic], creating
- registry [Visual Basic], adding values
- registry [Visual Basic], adding keys
- registry keys [Visual Basic], setting values
- examples [Visual Basic], registry
ms.assetid: d3e40f74-c283-480c-ab18-e5e9052cd814
ms.openlocfilehash: 84fc824ad5911621c679d70f480d9b5e83c095ad
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71054135"
---
# <a name="how-to-create-a-registry-key-and-set-its-value-in-visual-basic"></a>Postupy: Vytvořte klíč registru a nastavte jeho hodnotu v Visual Basic

`CreateSubKey` Metodu`My.Computer.Registry` objektu lze použít k vytvoření klíče registru.

## <a name="procedure"></a>Postup

### <a name="to-create-a-registry-key"></a>Vytvoření klíče registru

- `CreateSubKey` Použijte metodu, která určuje, který podregistr umístit klíč, a také název klíče. V parametru `Subkey` se nerozlišují malá a velká písmena. Tento příklad vytvoří klíč `MyTestKey` registru pod HKEY_CURRENT_USER.

    [!code-vb[VbResourceTasks#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#17)]

### <a name="to-create-a-registry-key-and-set-a-value-in-it"></a>Vytvoření klíče registru a nastavení jeho hodnoty

1. `CreateSubkey` Použijte metodu, která určuje, který podregistr umístit klíč, a také název klíče. Tento příklad vytvoří klíč `MyTestKey` registru pod HKEY_CURRENT_USER.

    [!code-vb[VbResourceTasks#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#17)]

2. Nastavte hodnotu pomocí `SetValue` metody. V tomto příkladu se nastaví hodnota řetězce. "MyTestKeyValue" na "Toto je testovací hodnota".

    [!code-vb[VbResourceTasks#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#14)]

## <a name="example"></a>Příklad

Tento příklad vytvoří klíč `MyTestKey` registru pod HKEY_CURRENT_USER a pak nastaví hodnotu `MyTestKeyValue` řetězce na `This is a test value`.

[!code-vb[VbResourceTasks#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#15)]

## <a name="robust-programming"></a>Robustní programování

Projděte si strukturu registru, kde najdete vhodné umístění pro váš klíč. Můžete například chtít otevřít HKEY_CURRENT_USER\Software klíč aktuálního uživatele a vytvořit klíč s názvem vaší společnosti. Pak přidejte hodnoty registru do klíče vaší společnosti.

Při čtení registru z webové aplikace závisí aktuální uživatel na ověřování a zosobnění implementované ve webové aplikaci.

Je bezpečnější zapsat data do složky uživatele (<xref:Microsoft.Win32.Registry.CurrentUser>) místo do místního počítače (<xref:Microsoft.Win32.Registry.LocalMachine>).

Když vytváříte hodnotu registru, musíte se rozhodnout, co dělat, pokud tato hodnota již existuje. Jiný proces, pravděpodobně škodlivý, již mohl vytvořit hodnotu a mít k ní přístup. Při vložení dat do hodnoty registru jsou data k dispozici pro druhý proces. Chcete-li tomu zabránit, <xref:Microsoft.Win32.RegistryKey.GetValue%2A> použijte metodu. Vrátí `Nothing` , pokud klíč ještě neexistuje.

Není bezpečné ukládat tajné klíče, jako jsou hesla, v registru jako prostý text, a to i v případě, že je klíč registru chráněný pomocí seznamů ACL (seznamy Access Control).

Následující podmínky mohou způsobit výjimku:

- Název klíče je `Nothing` (<xref:System.ArgumentNullException>).

- Uživatel nemá oprávnění k vytváření klíčů registru (<xref:System.Security.SecurityException>).

- Název klíče překračuje limit 255 znaků (<xref:System.ArgumentException>).

- Klíč je uzavřený (<xref:System.IO.IOException>).

- Klíč registru je jen pro čtení (<xref:System.UnauthorizedAccessException>).

## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework

Pro spuštění tohoto procesu vaše sestavení vyžaduje úroveň oprávnění udělené <xref:System.Security.Permissions.RegistryPermission> třídou. Pokud používáte v kontextu s částečným vztahem důvěryhodnosti, proces může vyvolat výjimku z důvodu nedostatečných oprávnění. Podobně uživatel musí mít správné seznamy ACL pro vytvoření nebo zápis do nastavení. Například místní aplikace, která má oprávnění zabezpečení přístupu kódu, nemusí mít oprávnění operačního systému. Další informace najdete v tématu [Základy zabezpečení přístupu ke kódu](../../../../framework/misc/code-access-security-basics.md).

## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy.CurrentUser%2A>
- <xref:Microsoft.Win32.RegistryKey.CreateSubKey%2A>
- [Čtení z registru a zápis do něj](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
- [Základy zabezpečení přístupu ke kódu](../../../../framework/misc/code-access-security-basics.md)
