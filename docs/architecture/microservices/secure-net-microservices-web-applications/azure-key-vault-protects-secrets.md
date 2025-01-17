---
title: Ochrana tajných kódů při produkci pomocí Azure Key Vault
description: Zabezpečení v mikroslužbách a webových aplikacích .NET – Azure Key Vault je skvělým způsobem, jak zpracovávat tajné klíče aplikací, které jsou zcela řízené správci. Správci mohou dokonce přiřazovat a odvolávat hodnoty vývoje bez vývojářů, kteří je chtějí zpracovat.
author: mjrousos
ms.author: wiwagn
ms.date: 10/19/2018
ms.openlocfilehash: 63bf357c95b82a820b6dfb6a2d24a5d89f66de72
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296478"
---
# <a name="use-azure-key-vault-to-protect-secrets-at-production-time"></a>Použití Azure Key Vault k ochraně tajných kódů v produkčním čase

Tajné klíče uložené jako proměnné prostředí nebo uložené nástrojem Správce tajných klíčů jsou pořád uložené místně a v počítači nejsou zašifrované. Bezpečnější je možnost ukládání tajných kódů je [Azure Key Vault](https://azure.microsoft.com/services/key-vault/), což zajišťuje zabezpečené, centrální umístění pro ukládání klíčů a tajných kódů.

Balíček **Microsoft. Extensions. Configuration. AzureKeyVault** umožňuje aplikaci ASP.NET Core číst informace o konfiguraci z Azure Key Vault. Pokud chcete začít používat tajné klíče z Azure Key Vault, postupujte podle těchto kroků:

1. Zaregistrujte svoji aplikaci jako aplikaci Azure AD. (Přístup k trezorům klíčů spravuje Azure AD.) To se dá udělat na portálu pro správu Azure. \

   Případně, pokud chcete, aby se aplikace ověřovala pomocí certifikátu místo hesla nebo tajného klíče klienta, můžete použít rutinu [New-AzADApplication](/powershell/module/az.resources/new-azadapplication) prostředí PowerShell. Certifikát, který zaregistrujete pomocí Azure Key Vault potřebuje jenom svůj veřejný klíč. Vaše aplikace bude používat privátní klíč.

2. Udělte registrované aplikaci přístup k trezoru klíčů vytvořením nového instančního objektu. Můžete to provést pomocí následujících příkazů PowerShellu:

   ```powershell
   $sp = New-AzADServicePrincipal -ApplicationId "<Application ID guid>"
   Set-AzKeyVaultAccessPolicy -VaultName "<VaultName>" -ServicePrincipalName $sp.ServicePrincipalNames[0] -PermissionsToSecrets all -ResourceGroupName "<KeyVault Resource Group>"
   ```

3. Zahrňte Trezor klíčů jako zdroj konfigurace v aplikaci voláním <xref:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault%2A?displayProperty=nameWithType> metody rozšíření při <xref:Microsoft.Extensions.Configuration.IConfigurationRoot> vytváření instance. Všimněte si, `AddAzureKeyVault` že volání vyžaduje ID aplikace, které bylo zaregistrováno a kterému byl udělen přístup k trezoru klíčů v předchozích krocích.

   Můžete také použít přetížení `AddAzureKeyVault` , které přijímá certifikát místo tajného klíče klienta, a to jenom tak, že obsahuje odkaz na balíček [Microsoft. IdentityModel. clients. Active](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory) .

> [!IMPORTANT]
> Doporučujeme, abyste jako poslední Poskytovatel konfigurace zaregistrovali Azure Key Vault, takže může přepsat hodnoty konfigurace z předchozích zprostředkovatelů.

## <a name="additional-resources"></a>Další zdroje

- **Použití Azure Key Vault k ochraně tajných klíčů aplikací** \
  [https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault](/azure/guidance/guidance-multitenant-identity-keyvault)

- **Bezpečné ukládání tajných kódů aplikací během vývoje** \
  [https://docs.microsoft.com/aspnet/core/security/app-secrets](/aspnet/core/security/app-secrets)

- **Konfigurace ochrany dat** \
  [https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview](/aspnet/core/security/data-protection/configuration/overview)

- **Správa a životnost klíče ochrany dat v ASP.NET Core** \
  [https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings](/aspnet/core/security/data-protection/configuration/default-settings)

- **Microsoft. Extensions. Configuration. KeyPerFile** – úložiště GitHub. \
  <https://github.com/aspnet/Configuration/tree/master/src/Config.KeyPerFile>

>[!div class="step-by-step"]
>[Předchozí](developer-app-secrets-storage.md)Další
>[](../key-takeaways.md)
