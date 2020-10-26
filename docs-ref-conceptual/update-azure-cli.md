---
title: Update the Azure CLI
description: Reference for the update of Azure CLI
author: dbradish-microsoft
ms.author: dbradish
manager: barbkess
ms.date: 10/19/2020
ms.topic: conceptual
ms.service: azure-cli
ms.devlang: azurecli 
ms.custom: devx-track-azurecli
---

# Update the Azure CLI

You can rely on package managers to update Azure CLI on Windows, macOS and Linux environments (see the `Update` section in each platform-specific install instruction). The CLI also provides in-tool commands to upgrade manually or automatically.

## Manual Update
[!INCLUDE [az-upgrade](includes/az-upgrade.md)]

`az upgrade` is supported on Windows, macOS and some Linux distros as long as installation is supported. It only supports upgrading to the latest version.

When `azure-cli` is already the latest version, running `az upgrade` will check and update all installed [extensions](azure-cli-extensions-overview.md).

## Automatic Update

If you would like to keep up with the latest version of Azure CLI, you can enable the CLI to upgrade automatically through [configuration](/cli/azure/config).

```azurecli
az config set auto-upgrade.enable=yes
```

The Azure CLI will check new versions regularly and prompt you to upgrade after any command finishes running once the update is available.

The prompt message and output messages during upgrade may interrupt your command result if it is assigned to some variable or in an automated flow. To avoid interruption, you can use the following configuration to allow the update to happen automatically without confirmation and only show warnings and errors during the upgrade.

```azurecli
az config auto-upgrade.prompt=no
```

By default, all installed extensions will also be updated. You can disable extension update through configuration.

```azurecli
az config auto-upgrade.all=no
```

> [!NOTE]
> Please wait for `az upgrade` to complete before proceeding to the next set of commands, else the new versions of the CLI (+extensions) may have breaking changes.

If you decide not to use the automatic update feature any more for cases like keeping command scripts running stably, you can turn it off through configuration.
```azurecli
az config set auto-upgrade.enable=no
```