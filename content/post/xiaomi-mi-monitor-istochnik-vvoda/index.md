+++
title = 'Монитор Xiaomi Mi Curved Gaming: как поменять источник сигнала?'
description = 'Заметка о том, как программно поменять источник сигнала, не переключая кабели'
tags = [ 'способ', 'Xiaomi']
slug = 'monitor-xiaomi-mi-curved-gaming-kak-pomenyat-istochnik-signala'
image = 'index.jpg'
date = '2023-06-19'
categories = ["Быт", "Технологии"]
+++

Возник вопрос: как поменять источник сигнала на мониторе Xiaomi Mi Curved Gaming Monitor 34, не отсоединяя кабели?

Достаточно просто. **В Windows** в поиске пишем "PowerShell" и запускаем Windows PowerShell (возможно понадобится запуск от администратора), в ней пишем команду, которая программно отключит текущий монитор, после чего система переключится на другой:

```
(Add-Type -MemberDefinition "[DllImport(""user32.dll"")]`npublic static extern int SendMessage(int hWnd, int hMsg, int wParam, int lParam);" -Name "Win32SendMessage" -Namespace Win32Functions -PassThru)::SendMessage(0xffff, 0x0112, 0xF170, 2)
```

**Для Linux тоже есть аналогичная команда:**

`xset dpms force off`

**Для Mac:**

`pmset displaysleepnow`