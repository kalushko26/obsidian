---
title: Исправление ошибки WslRegisterDistribution в Ubuntu
draft: false
tags:
  - "#ubuntu"
info:
---
**Ошибка WslRegisterDistribution failed with error: 0x80370114** может возникать при установке Linux дистрибутива в Windows Subsystem for Linux (WSL). Эта ошибка обычно связана с проблемами взаимодействия между Windows и WSL.

Для решения этой проблемы можно попробовать следующие шаги:

1. Выполните следующие команды в PowerShell от имени администратора:

```
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
Перезапустите компьютер.
```

![[Pasted image 20230529094857.png]]

2. Запустите PowerShell от имени администратора и выполните следующую команду:

```
wsl --set-default-version 2
```

![[Pasted image 20230529094908.png]]

3. Установите нужный вам Linux дистрибутив (WSL). Если ошибка все еще возникает, попробуйте установить другой дистрибутив.

![[Pasted image 20230529094926.png]]