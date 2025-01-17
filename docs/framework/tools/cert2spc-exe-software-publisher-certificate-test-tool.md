---
title: Cert2spc.exe (nástroj pro testování certifikátu vydavatele softwaru)
ms.date: 03/30/2017
helpviewer_keywords:
- SPC
- Software Publisher Certificate Test tool
- Software Publisher Certificate
- Cert2spc.exe
- certificates, Software Publisher's Certificate
ms.assetid: be434d7d-9c0d-46e7-8392-58a9b542d11d
ms.openlocfilehash: 809b7d0383f172a5fbcb2ac4ac3ffb96ff0b8e20
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129890"
---
# <a name="cert2spcexe-software-publisher-certificate-test-tool"></a>Cert2spc.exe (nástroj pro testování certifikátu vydavatele softwaru)
Nástroj Software Publisher Certificate Test vytvoří certifikát Software Publisher's Certificate (SPC) z jednoho nebo více certifikátů X.509. Nástroj Cert2spc.exe slouží pouze k testování. Platný certifikát SPC lze získat od certifikačního úřadu, například VeriSign nebo Thawte. Další informace o vytváření certifikátů X. 509 najdete v tématu [Makecert. exe (Nástroj pro vytváření certifikátů)](/windows/desktop/SecCrypto/makecert).  
  
 Tento nástroj je automaticky nainstalován se sadou Visual Studio. Chcete-li spustit nástroj, použijte Developer Command Prompt pro Visual Studio (nebo příkazový řádek sady Visual Studio v systému Windows 7). Další informace najdete v tématu [výzvy k zadání příkazu](developer-command-prompt-for-vs.md).  
  
 V příkazovém řádku zadejte následující:  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
cert2spc cert1.cer | crl1.crl [... certN.cer | crlN.crl] outputSPCfile.spc  
```  
  
## <a name="parameters"></a>Parametry  
  
|Argument|Popis|  
|--------------|-----------------|  
|`certN.cer`|Název certifikátu X.509, který má být zahrnut do souboru SPC. Můžete zadat více názvů oddělených mezerami.|  
|`crlN.crl`|Název seznamu odvolání certifikátu, který má být zahrnut do souboru SPC. Můžete zadat více názvů oddělených mezerami.|  
|`outputSPCfile.spc`|Název objektu PKCS #7, který bude obsahovat certifikáty X.509.|  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/?**|Zobrazí syntaxi příkazu a možnosti nástroje.|  
  
## <a name="examples"></a>Příklady  
 Následující příkaz vytvoří SPC z `myCertificate.cer` a umístí ho do `mySPCFile.spc`.  
  
```console
cert2spc myCertificate.cer mySPCFile.spc  
```  
  
 Následující příkaz vytvoří SPC z `oneCertificate.cer` a `twoCertificate.cer`a umístí ho do `mySPCFile.spc`.  
  
```console
cert2spc oneCertificate.cer twoCertificate.cer mySPCFile.spc  
```  
  
## <a name="see-also"></a>Viz také:

- [Nástroje](index.md)
- [Makecert. exe (Nástroj pro vytvoření certifikátu)](/windows/desktop/SecCrypto/makecert)
- [Příkazové řádky](developer-command-prompt-for-vs.md)
