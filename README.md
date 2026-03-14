# UEFI Addon Flasher

> 🛟 Emergency ISO flasher that runs directly from UEFI Shell — no OS required.

---

## ⚠️ WARNING / ПРЕДУПРЕЖДЕНИЕ

> 🚧 **This addon is in active development.**
> Security improvements and bug fixes will be released over time.
>
> **NEVER select the disk where your UEFI Shell is located!**
> If you flash the wrong disk — you will lose the UEFI Shell itself and be left with nothing.
> In that case your only option is to wait for a USB drive with a new OS.
>
> **Always double-check which disk you are writing to before confirming!**

> 🚧 **Данный аддон находится в активной разработке.**
> Будут выходить обновления с улучшениями безопасности и исправлениями.
>
> **НИ В КОЕМ СЛУЧАЕ не выбирайте диск, на котором находится UEFI Shell!**
> Если вы запишете не на тот диск — вы потеряете UEFI Shell и останетесь ни с чем.
> В таком случае единственный выход — ждать флешку с ОС.
>
> **Всегда проверяйте дважды какой диск вы выбираете перед подтверждением!**

---

## 🇬🇧 English

### What is this?

**UEFI Addon Flasher** is a lightweight `.efi` utility that lets you write an ISO image to a USB drive directly from the UEFI Shell — without any operating system.

> For maximum safety, it is recommended to run the flasher from a dedicated USB drive. This ensures that the target disk is not locked by the tool itself and prevents data corruption if the process is interrupted.

### Why does this exist?

Imagine this situation:
- You tried to flash a USB drive with Rufus or another tool
- Something went wrong — the flash drive is broken, Windows is gone
- You have **no OS to boot into**, no tools available
- You're stuck

Most people in this situation have no way out.

But almost every modern motherboard has a **UEFI Shell** accessible from the boot menu. This tool runs there — giving you a last resort to recover.

### Important: This addon requires UEFI Shell to work!

The flasher **cannot run on its own**. It needs a UEFI Shell environment to work.

**How to set up UEFI Shell on a USB drive:**

1. Format your USB drive as **FAT32**
2. Download UEFI Shell from the official EDK2 releases:
   👉 https://github.com/tianocore/edk2/releases
   (download `Shell.efi` or `shellx64.efi`)
3. On the USB drive create the folder structure:
   ```
   EFI\
   └── BOOT\
       └── BOOTX64.EFI   ← rename Shell.efi to this
   ```
4. Place `Flasher.efi` in the same `EFI\BOOT\` folder:
   ```
   EFI\
   └── BOOT\
       ├── BOOTX64.EFI   ← UEFI Shell
       └── Flasher.efi   ← this addon
   ```
5. Boot from the USB drive via your motherboard's boot menu (`F2` / `Del` / `F12`)
6. You will land in the UEFI Shell automatically

### NTFS Support (optional)

By default the flasher works on FAT32 drives. To enable reading ISO files from NTFS drives:

1. Download `ntfs_x64.efi` from https://github.com/pbatard/ntfs-3g
2. Place it next to `Flasher.efi`
3. In UEFI Shell run:
   ```
   load ntfs_x64.efi
   map -r
   ```
4. Now Flasher can find ISO files on NTFS drives

### Usage

```
flasher search           - find ISO files on all volumes
flasher disk             - list available disks
flasher select N         - select disk by number
flasher iso fs0:\file.iso - select ISO file
flasher start            - write ISO to selected disk
flasher check N          - check disk health
flasher wipe N           - wipe disk with zeros
flasher format N fat32   - prepare disk for FAT32
```

**Example workflow:**
```
flasher search
flasher disk
flasher select 1
flasher iso fs1:\windows.iso
flasher start
```

### What's new in v1.2

- `flasher check N` — disk diagnostics, checks for read errors
- `flasher wipe N` — wipes entire disk with zeros
- `flasher format N fat32` — clears MBR and partition table
- Protection: blocks any operation if UEFI Shell files are detected on the target disk
- NTFS support via external driver

### Download

Ready-to-use `Flasher.efi` available in [Releases](../../releases).

### 🐛 Bug Reports

If you found a bug in the addon, please report it to **straightpeaceyt@gmail.com**
Describe what the bug is.
As a reward, you will be added to the **Flasher Beta Team** —
your name or nickname will be displayed in the project.

---

## 🇷🇺 Русский

### Что это такое?

**UEFI Addon Flasher** — лёгкая утилита `.efi`, которая позволяет записать ISO образ на USB флешку прямо из UEFI Shell, без какой-либо операционной системы.

> Для максимальной безопасности рекомендуется запускать флешер с отдельной USB-флешки. Это гарантирует, что целевой диск не будет занят самой программой, и предотвратит порчу данных при внезапной остановке записи.

### Зачем это нужно?

Представь ситуацию:
- Ты пытался записать флешку через Rufus или другую программу
- Что-то пошло не так — флешка сломана, Windows слетела
- **Загрузиться некуда**, никаких инструментов нет
- Ты в тупике

Большинство людей в такой ситуации не имеют выхода.

Но почти на каждой современной материнской плате есть **UEFI Shell**, доступный из меню загрузки. Этот инструмент запускается прямо там — давая тебе последний шанс восстановить систему.

### Важно: аддон не работает без UEFI Shell!

Флешер **не запускается сам по себе**. Для его работы необходима среда UEFI Shell.

**Как установить UEFI Shell на флешку:**

1. Отформатируй USB флешку в **FAT32**
2. Скачай UEFI Shell с официального репозитория EDK2:
   👉 https://github.com/tianocore/edk2/releases
   (скачай файл `Shell.efi` или `shellx64.efi`)
3. Создай на флешке следующую структуру папок:
   ```
   EFI\
   └── BOOT\
       └── BOOTX64.EFI   ← переименуй Shell.efi в этот файл
   ```
4. Положи `Flasher.efi` в ту же папку `EFI\BOOT\`:
   ```
   EFI\
   └── BOOT\
       ├── BOOTX64.EFI   ← UEFI Shell
       └── Flasher.efi   ← этот аддон
   ```
5. Загрузись с флешки через меню загрузки материнской платы (`F2` / `Del` / `F12`)
6. Ты автоматически попадёшь в UEFI Shell

### Поддержка NTFS (опционально)

По умолчанию флешер работает с FAT32 дисками. Чтобы читать ISO файлы с NTFS:

1. Скачай `ntfs_x64.efi` с https://github.com/pbatard/ntfs-3g
2. Положи рядом с `Flasher.efi`
3. В UEFI Shell выполни:
   ```
   load ntfs_x64.efi
   map -r
   ```
4. Теперь Flasher видит ISO файлы на NTFS дисках

### Использование

```
flasher search            - найти ISO файлы на всех томах
flasher disk              - список доступных дисков
flasher select N          - выбрать диск по номеру
flasher iso fs0:\file.iso - выбрать ISO файл
flasher start             - записать ISO на выбранный диск
flasher check N           - проверка диска на ошибки
flasher wipe N            - затереть диск нулями
flasher format N fat32    - подготовить диск под FAT32
```

**Пример:**
```
flasher search
flasher disk
flasher select 1
flasher iso fs1:\windows.iso
flasher start
```

### Что нового в v1.2

- `flasher check N` — диагностика диска, проверка на ошибки чтения
- `flasher wipe N` — затирание диска нулями
- `flasher format N fat32` — очистка MBR и таблицы разделов
- Защита: блокировка операций если на диске обнаружены файлы UEFI Shell
- Поддержка NTFS через внешний драйвер

### Скачать

Готовый `Flasher.efi` доступен в разделе [Releases](../../releases).

### 🐛 Сообщить об ошибке

Если нашёл баг — напиши на **straightpeaceyt@gmail.com**
Опиши что за ошибка.
В награду ты будешь добавлен в **Flasher Beta Team** —
твоё имя или псевдоним будет отображаться в проекте.

---

*Created as a last-resort recovery tool for situations where no OS is available.*
*Copyright (c) 2025 StraightPeaceYT and 01AiR_PrIcH — MIT License*
