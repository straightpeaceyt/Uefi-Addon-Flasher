# UEFI Addon Flasher

> 🛟 Emergency ISO flasher that runs directly from UEFI Shell — no OS required.

---

EN: For maximum safety, it is recommended to run the flasher from a dedicated USB drive. This ensures that the target disk is not locked by the tool itself and prevents data corruption if the process is interrupted.

RU: Для максимальной безопасности рекомендуется запускать флешер с отдельной USB-флешки. Это гарантирует, что целевой диск не будет занят самой программой, и предотвратит порчу данных при внезапной остановке записи.

## ⚠️ WARNING / ПРЕДУПРЕЖДЕНИЕ

> 🚧 **This addon is in active development.**
> Security improvements and bug fixes will be released over time.
>
> **NEVER select the disk where your UEFI Shell is located!**
> If you flash the wrong disk — you will lose the UEFI Shell itself and be left with nothing.
> In that case your only option is to wait for a USB drive with a new OS.
>
> **Always double-check which disk you are writing to before confirming!**

---

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

### Why does this exist?

Imagine this situation:
- You tried to flash a USB drive with Rufus or another tool
- Something went wrong — the flash drive is broken, Windows is gone
- You have **no OS to boot into**, no tools available
- You're stuck

Most people in this situation have no way out.

But almost every modern motherboard has a **UEFI Shell** accessible from the boot menu. This tool runs there — giving you a last resort to recover.

### Usage

```
flasher.efi                        - show help
flasher.efi search                 - find ISO files on all volumes
flasher.efi disk                   - list available disks
flasher.efi select N               - select disk by number
flasher.efi iso fs0:\file.iso      - select ISO file
flasher.efi start                  - write ISO to selected disk
```

**Example workflow:**
```
flasher.efi search
flasher.efi disk
flasher.efi select 1
flasher.efi iso fs0:\windows.iso
flasher.efi start
```

### How to run

1. Copy `IsoFlasher.efi` to your EFI partition or any FAT32 USB drive
2. Boot into UEFI Shell (usually via `F2` / `Del` / `F12` → Boot menu)
3. Navigate to the drive: `fs0:` then `ls`
4. Run: `IsoFlasher.efi`

---

## 🇷🇺 Русский

### Что это такое?

**UEFI Addon Flasher** — лёгкая утилита `.efi`, которая позволяет записать ISO образ на USB флешку прямо из UEFI Shell, без какой-либо операционной системы.

### Зачем это нужно?

Представь ситуацию:
- Ты пытался записать флешку через Rufus или другую программу
- Что-то пошло не так — флешка сломана, Windows слетела
- **Загрузиться некуда**, никаких инструментов нет
- Ты в тупике

Большинство людей в такой ситуации не имеют выхода.

Но почти на каждой современной материнской плате есть **UEFI Shell**, доступный из меню загрузки. Этот инструмент запускается прямо там — давая тебе последний шанс восстановить систему.

### Использование

```
flasher.efi                        - показать помощь
flasher.efi search                 - найти ISO файлы на всех томах
flasher.efi disk                   - список доступных дисков
flasher.efi select N               - выбрать диск по номеру
flasher.efi iso fs0:\file.iso      - выбрать ISO файл
flasher.efi start                  - записать ISO на выбранный диск
```

**Пример:**
```
flasher.efi search
flasher.efi disk
flasher.efi select 1
flasher.efi iso fs0:\windows.iso
flasher.efi start
```

### Как запустить

1. Скопируй `IsoFlasher.efi` на EFI раздел или любую FAT32 флешку
2. Зайди в UEFI Shell (обычно через `F2` / `Del` / `F12` → меню загрузки)
3. Перейди на нужный диск: `fs0:` затем `ls`
4. Запусти: `IsoFlasher.efi`

---

*Created as a last-resort recovery tool for situations where no OS is available.*
