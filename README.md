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

### Usage

```
flasher search                 - find ISO files on all volumes
flasher disk                   - list available disks
flasher select N               - select disk by number
flasher iso fs0:\file.iso      - select ISO file
flasher start                  - write ISO to selected disk
```

**Example workflow:**
```
flasher search
flasher disk
flasher select 1
flasher iso fs1:\windows.iso
flasher start
```

### Download

Ready-to-use `Flasher.efi` available in [Releases](../../releases).

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

### Использование

```
flasher search                 - найти ISO файлы на всех томах
flasher disk                   - список доступных дисков
flasher select N               - выбрать диск по номеру
flasher iso fs0:\file.iso      - выбрать ISO файл
flasher start                  - записать ISO на выбранный диск
```

**Пример:**
```
flasher search
flasher disk
flasher select 1
flasher iso fs1:\windows.iso
flasher start
```

### Скачать

Готовый `Flasher.efi` доступен в разделе [Releases](../../releases).

---

*Created as a last-resort recovery tool for situations where no OS is available.*
