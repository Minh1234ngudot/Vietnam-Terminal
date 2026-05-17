# 🇻🇳 Vietnam Terminal Setup

> Terminal setup với **Oh My Posh** theme Việt Nam — đỏ & vàng chuẩn cờ đỏ sao vàng.

![Preview](https://img.shields.io/badge/OS-Windows%2011-blue?style=flat-square&logo=windows)
![OhMyPosh](https://img.shields.io/badge/Oh%20My%20Posh-v24%2B-DA251D?style=flat-square)
![PowerShell](https://img.shields.io/badge/PowerShell-5.1%2B-FFCD00?style=flat-square&logo=powershell)

---

## 📋 Yêu cầu

- Windows 10/11
- Windows Terminal
- PowerShell 5.1+
- Kết nối Internet

---

## 🚀 Cài đặt

### Bước 1 — Cài Oh My Posh

Mở PowerShell và chạy:

```powershell
winget install JanDeDobbeleer.OhMyPosh -s winget
```

Sau khi cài xong, **restart PowerShell**.

---

### Bước 2 — Cài Nerd Font

Oh My Posh cần **Nerd Font** để hiển thị icon đúng. Tải font **JetBrainsMono Nerd Font**:

```powershell
oh-my-posh font install JetBrainsMono
```

Sau đó vào **Windows Terminal → Settings → Defaults → Font face** và chọn:
```
JetBrainsMono Nerd Font Mono
```

---

### Bước 3 — Tải file theme Vietnam

Tải file `vietnam.omp.json` từ repo này và đặt vào thư mục Downloads:
```
C:\Users\<tên_của_bạn>\Downloads\vietnam.omp.json
```

---

### Bước 4 — Cài PSReadLine (fix lỗi key handler)

```powershell
Install-Module PSReadLine -Force -SkipPublisherCheck -Scope CurrentUser
```

Restart PowerShell sau khi cài xong.

---

### Bước 5 — Cấu hình PowerShell Profile

Mở file profile:

```powershell
notepad $PROFILE
```

> Nếu file chưa tồn tại, tạo mới:
> ```powershell
> New-Item -Path $PROFILE -Type File -Force
> ```

Thêm nội dung sau vào file (thay `YourUsername` bằng username của bạn):

```powershell
Set-Location "C:\Users\YourUsername"
oh-my-posh init pwsh --config "C:\Users\YourUsername\Downloads\vietnam.omp.json" | Invoke-Expression
```

Lưu file và **restart PowerShell**.

---

### Bước 6 — (Tùy chọn) Cài Fastfetch

Fastfetch hiển thị thông tin hệ thống khi mở terminal:

```powershell
winget install fastfetch-cli.fastfetch
```

Tạo thư mục config:

```powershell
mkdir "$env:USERPROFILE\.config\fastfetch"
```

Copy file config vào:

```powershell
copy "C:\Users\YourUsername\Downloads\config.jsonc" "$env:USERPROFILE\.config\fastfetch\"
copy "C:\Users\YourUsername\Downloads\vietnam_ascii.txt" "$env:USERPROFILE\.config\fastfetch\"
```

---

### Bước 7 — (Tùy chọn) Vietnam Color Scheme cho Windows Terminal

Mở Windows Terminal Settings (`Ctrl+,`) → **nhấn vào biểu tượng Bánh răng để Open JSON file** nhấn Ctrl + A và dán code ở dưới vào file settings.json đã mở trước đó:

```json
{
    "$help": "https://aka.ms/terminal-documentation",
    "$schema": "https://aka.ms/terminal-profiles-schema",
    "actions": 
    [
        {
            "command": 
            {
                "action": "copy",
                "singleLine": false
            },
            "id": "User.copy.644BA8F2"
        },
        {
            "command": "paste",
            "id": "User.paste"
        },
        {
            "command": "find",
            "id": "User.find"
        },
        {
            "command": 
            {
                "action": "splitPane",
                "split": "auto",
                "splitMode": "duplicate"
            },
            "id": "User.splitPane.A6751878"
        }
    ],
    "alwaysOnTop": false,
    "copyFormatting": "none",
    "copyOnSelect": false,
    "defaultProfile": "{61c54bbd-c2c6-5271-96e7-009a87ff44bf}",
    "keybindings": 
    [
        {
            "id": "User.copy.644BA8F2",
            "keys": "ctrl+c"
        },
        {
            "id": "User.find",
            "keys": "ctrl+shift+f"
        },
        {
            "id": "User.paste",
            "keys": "ctrl+v"
        },
        {
            "id": "User.splitPane.A6751878",
            "keys": "alt+shift+d"
        }
    ],
    "newTabMenu": 
    [
        {
            "type": "remainingProfiles"
        }
    ],
    "profiles": 
    {
        "defaults": 
        {
            "colorScheme": "Vietnam",
            "cursorShape": "filledBox",
            "cursorColor": "#FFCD00",
            "experimental.retroTerminalEffect": false,
            "font": 
            {
                "builtinGlyphs": true,
                "cellHeight": "1.2",
                "colorGlyphs": true,
                "face": "JetBrainsMono Nerd Font Mono",
                "size": 10,
                "weight": "extra-black"
            },
            "intenseTextStyle": "all",
            "opacity": 85,
            "padding": "8",
            "useAcrylic": true
        },
        "list": 
        [
            {
                "commandline": "%SystemRoot%\\System32\\WindowsPowerShell\\v1.0\\powershell.exe",
                "guid": "{61c54bbd-c2c6-5271-96e7-009a87ff44bf}",
                "hidden": false,
                "name": "Windows PowerShell"
            },
            {
                "commandline": "%SystemRoot%\\System32\\cmd.exe",
                "guid": "{0caa0dad-35be-5f56-a8ff-afceeeaa6101}",
                "hidden": false,
                "name": "Command Prompt"
            },
            {
                "guid": "{b453ae62-4e3d-5e58-b989-0a998ec441b8}",
                "hidden": false,
                "name": "Azure Cloud Shell",
                "source": "Windows.Terminal.Azure"
            }
        ]
    },
    "schemes": 
    [
        {
            "name": "Vietnam",
            "background": "#1A0A0A",
            "foreground": "#F5E6C8",
            "black": "#2A1010",
            "red": "#DA251D",
            "green": "#A6E3A1",
            "yellow": "#FFCD00",
            "blue": "#89B4FA",
            "purple": "#F5C2E7",
            "cyan": "#94E2D5",
            "white": "#F5E6C8",
            "brightBlack": "#5C2A2A",
            "brightRed": "#FF4136",
            "brightGreen": "#69FF94",
            "brightYellow": "#FFE033",
            "brightBlue": "#B4D4FF",
            "brightPurple": "#FF92DF",
            "brightCyan": "#A4FFFF",
            "brightWhite": "#FFFFFF",
            "cursorColor": "#FFCD00",
            "selectionBackground": "#8B1A1A"
        },
        {
            "background": "#1E1E2E",
            "black": "#45475A",
            "blue": "#89B4FA",
            "brightBlack": "#585B70",
            "brightBlue": "#89B4FA",
            "brightCyan": "#94E2D5",
            "brightGreen": "#A6E3A1",
            "brightPurple": "#F5C2E7",
            "brightRed": "#F38BA8",
            "brightWhite": "#A6ADC8",
            "brightYellow": "#F9E2AF",
            "cursorColor": "#F5E0DC",
            "cyan": "#94E2D5",
            "foreground": "#CDD6F4",
            "green": "#A6E3A1",
            "name": "Catppuccin Mocha",
            "purple": "#F5C2E7",
            "red": "#F38BA8",
            "selectionBackground": "#585B70",
            "white": "#BAC2DE",
            "yellow": "#F9E2AF"
        },
        {
            "background": "#000000",
            "black": "#0C0C0C",
            "blue": "#0037DA",
            "brightBlack": "#767676",
            "brightBlue": "#3B78FF",
            "brightCyan": "#61D6D6",
            "brightGreen": "#16C60C",
            "brightPurple": "#B4009E",
            "brightRed": "#E74856",
            "brightWhite": "#F2F2F2",
            "brightYellow": "#F9F1A5",
            "cursorColor": "#FFFFFF",
            "cyan": "#3A96DD",
            "foreground": "#FFFFFF",
            "green": "#13A10E",
            "name": "Color Scheme 15",
            "purple": "#881798",
            "red": "#C50F1F",
            "selectionBackground": "#FFFFFF",
            "white": "#CCCCCC",
            "yellow": "#C19C00"
        },
        {
            "background": "#282A36",
            "black": "#21222C",
            "blue": "#BD93F9",
            "brightBlack": "#6272A4",
            "brightBlue": "#D6ACFF",
            "brightCyan": "#A4FFFF",
            "brightGreen": "#69FF94",
            "brightPurple": "#FF92DF",
            "brightRed": "#FF6E6E",
            "brightWhite": "#FFFFFF",
            "brightYellow": "#FFFFA5",
            "cursorColor": "#F8F8F2",
            "cyan": "#8BE9FD",
            "foreground": "#F8F8F2",
            "green": "#50FA7B",
            "name": "Dracula",
            "purple": "#FF79C6",
            "red": "#FF5555",
            "selectionBackground": "#44475A",
            "white": "#F8F8F2",
            "yellow": "#F1FA8C"
        }
    ],
    "tabWidthMode": "titleLength",
    "themes": [],
    "useAcrylicInTabRow": true
}
```
---

## 🎨 Màu sắc theme

| Thành phần | Màu | Hex |
|---|---|---|
| Đỏ chính | 🔴 | `#DA251D` |
| Vàng chính | 🟡 | `#FFCD00` |
| Background | ⬛ | `#1A0A0A` |
| Foreground | 🟫 | `#F5E6C8` |
| Cursor | 🟡 | `#FFCD00` |

---

## 🔧 Cấu trúc Prompt

```
[path] [git branch] [git status] [exit status]     [network] [battery] [time]
[os] [username]                                              ♥♥♥ Việt Nam
```

### Các segment trong prompt

| Segment | Mô tả |
|---|---|
| 📁 Path | Đường dẫn hiện tại, home hiện `~` |
| 🌿 Git | Branch, trạng thái working/staging |
| ✅ Status | `♥` nếu OK, `💔` nếu lỗi |
| 🌐 Network | Icon kết nối mạng |
| 🔋 Battery | % pin + trạng thái sạc |
| ⏱ Exec time | Thời gian lệnh vừa chạy |
| 📅 Time | Ngày + giờ |
| 💻 OS | Icon hệ điều hành |
| 👤 Username | Tên user (+ SSH icon nếu remote) |

---

## ❓ Troubleshooting

**Icon bị lỗi/hiện ký tự lạ?**
→ Chưa cài Nerd Font hoặc chưa set font trong Windows Terminal.

**Lỗi `Get-PSReadLineKeyHandler`?**
→ Chạy: `Install-Module PSReadLine -Force -SkipPublisherCheck -Scope CurrentUser`

**Theme không load khi mở tab mới?**
→ Kiểm tra `$PROFILE` đã có dòng `oh-my-posh init pwsh --config ...` chưa. Đảm bảo **không có 2 dòng** `oh-my-posh init`.

**Vẫn còn dòng `Loading personal and system profiles took...`?**
→ Đảm bảo trong `$PROFILE` có dòng `Clear-Host` sau `oh-my-posh init`.

---

## 📁 Files

| File | Mô tả |
|---|---|
| `vietnam.omp.json` | Theme Oh My Posh màu đỏ-vàng VN |
| `config.jsonc` | Config Fastfetch |
| `vietnam_ascii.txt` | ASCII art logo cho Fastfetch |
| `settings.json` | Windows Terminal settings |

---
---

# 🇬🇧 English Version

> A beautiful terminal setup using **Oh My Posh** with a Vietnam-themed prompt — red & yellow inspired by the Vietnamese flag.

---

## 📋 Requirements

- Windows 10/11
- Windows Terminal
- PowerShell 5.1+
- Internet connection

---

## 🚀 Installation

### Step 1 — Install Oh My Posh

Open PowerShell and run:

```powershell
winget install JanDeDobbeleer.OhMyPosh -s winget
```

Once installed, **restart PowerShell**.

---

### Step 2 — Install a Nerd Font

Oh My Posh requires a **Nerd Font** to render icons correctly. Install **JetBrainsMono Nerd Font**:

```powershell
oh-my-posh font install JetBrainsMono
```

Then go to **Windows Terminal → Settings → Defaults → Font face** and set:
```
JetBrainsMono Nerd Font Mono
```

---

### Step 3 — Download the Vietnam Theme

Download `vietnam.omp.json` from this repo and place it in your Downloads folder:
```
C:\Users\<your_username>\Downloads\vietnam.omp.json
```

---

### Step 4 — Fix PSReadLine Key Handler Errors

```powershell
Install-Module PSReadLine -Force -SkipPublisherCheck -Scope CurrentUser
```

Restart PowerShell after installing.

---

### Step 5 — Configure Your PowerShell Profile

Open your profile file:

```powershell
notepad $PROFILE
```

> If the file does not exist yet, create it first:
> ```powershell
> New-Item -Path $PROFILE -Type File -Force
> ```

Add the following (replace `YourUsername` with your actual username):

```powershell
Set-Location "C:\Users\YourUsername"
oh-my-posh init pwsh --config "C:\Users\YourUsername\Downloads\vietnam.omp.json" | Invoke-Expression
Clear-Host
fastfetch
```

Save the file and **restart PowerShell**.

---

### Step 6 — (Optional) Install Fastfetch

```powershell
winget install fastfetch-cli.fastfetch
```

Create the config directory:

```powershell
mkdir "$env:USERPROFILE\.config\fastfetch"
```

Copy the config files:

```powershell
copy "C:\Users\YourUsername\Downloads\config.jsonc" "$env:USERPROFILE\.config\fastfetch\"
copy "C:\Users\YourUsername\Downloads\vietnam_ascii.txt" "$env:USERPROFILE\.config\fastfetch\"
```

---

### Step 7 — (Optional) Apply Vietnam Color Scheme in Windows Terminal

Open Windows Terminal Settings (`Ctrl+,`) → **Open JSON file** press ctrl + A and paste the code below into the settings.json file that you opened earlier:

```json
{
    "$help": "https://aka.ms/terminal-documentation",
    "$schema": "https://aka.ms/terminal-profiles-schema",
    "actions": 
    [
        {
            "command": 
            {
                "action": "copy",
                "singleLine": false
            },
            "id": "User.copy.644BA8F2"
        },
        {
            "command": "paste",
            "id": "User.paste"
        },
        {
            "command": "find",
            "id": "User.find"
        },
        {
            "command": 
            {
                "action": "splitPane",
                "split": "auto",
                "splitMode": "duplicate"
            },
            "id": "User.splitPane.A6751878"
        }
    ],
    "alwaysOnTop": false,
    "copyFormatting": "none",
    "copyOnSelect": false,
    "defaultProfile": "{61c54bbd-c2c6-5271-96e7-009a87ff44bf}",
    "keybindings": 
    [
        {
            "id": "User.copy.644BA8F2",
            "keys": "ctrl+c"
        },
        {
            "id": "User.find",
            "keys": "ctrl+shift+f"
        },
        {
            "id": "User.paste",
            "keys": "ctrl+v"
        },
        {
            "id": "User.splitPane.A6751878",
            "keys": "alt+shift+d"
        }
    ],
    "newTabMenu": 
    [
        {
            "type": "remainingProfiles"
        }
    ],
    "profiles": 
    {
        "defaults": 
        {
            "colorScheme": "Vietnam",
            "cursorShape": "filledBox",
            "cursorColor": "#FFCD00",
            "experimental.retroTerminalEffect": false,
            "font": 
            {
                "builtinGlyphs": true,
                "cellHeight": "1.2",
                "colorGlyphs": true,
                "face": "JetBrainsMono Nerd Font Mono",
                "size": 10,
                "weight": "extra-black"
            },
            "intenseTextStyle": "all",
            "opacity": 85,
            "padding": "8",
            "useAcrylic": true
        },
        "list": 
        [
            {
                "commandline": "%SystemRoot%\\System32\\WindowsPowerShell\\v1.0\\powershell.exe",
                "guid": "{61c54bbd-c2c6-5271-96e7-009a87ff44bf}",
                "hidden": false,
                "name": "Windows PowerShell"
            },
            {
                "commandline": "%SystemRoot%\\System32\\cmd.exe",
                "guid": "{0caa0dad-35be-5f56-a8ff-afceeeaa6101}",
                "hidden": false,
                "name": "Command Prompt"
            },
            {
                "guid": "{b453ae62-4e3d-5e58-b989-0a998ec441b8}",
                "hidden": false,
                "name": "Azure Cloud Shell",
                "source": "Windows.Terminal.Azure"
            }
        ]
    },
    "schemes": 
    [
        {
            "name": "Vietnam",
            "background": "#1A0A0A",
            "foreground": "#F5E6C8",
            "black": "#2A1010",
            "red": "#DA251D",
            "green": "#A6E3A1",
            "yellow": "#FFCD00",
            "blue": "#89B4FA",
            "purple": "#F5C2E7",
            "cyan": "#94E2D5",
            "white": "#F5E6C8",
            "brightBlack": "#5C2A2A",
            "brightRed": "#FF4136",
            "brightGreen": "#69FF94",
            "brightYellow": "#FFE033",
            "brightBlue": "#B4D4FF",
            "brightPurple": "#FF92DF",
            "brightCyan": "#A4FFFF",
            "brightWhite": "#FFFFFF",
            "cursorColor": "#FFCD00",
            "selectionBackground": "#8B1A1A"
        },
        {
            "background": "#1E1E2E",
            "black": "#45475A",
            "blue": "#89B4FA",
            "brightBlack": "#585B70",
            "brightBlue": "#89B4FA",
            "brightCyan": "#94E2D5",
            "brightGreen": "#A6E3A1",
            "brightPurple": "#F5C2E7",
            "brightRed": "#F38BA8",
            "brightWhite": "#A6ADC8",
            "brightYellow": "#F9E2AF",
            "cursorColor": "#F5E0DC",
            "cyan": "#94E2D5",
            "foreground": "#CDD6F4",
            "green": "#A6E3A1",
            "name": "Catppuccin Mocha",
            "purple": "#F5C2E7",
            "red": "#F38BA8",
            "selectionBackground": "#585B70",
            "white": "#BAC2DE",
            "yellow": "#F9E2AF"
        },
        {
            "background": "#000000",
            "black": "#0C0C0C",
            "blue": "#0037DA",
            "brightBlack": "#767676",
            "brightBlue": "#3B78FF",
            "brightCyan": "#61D6D6",
            "brightGreen": "#16C60C",
            "brightPurple": "#B4009E",
            "brightRed": "#E74856",
            "brightWhite": "#F2F2F2",
            "brightYellow": "#F9F1A5",
            "cursorColor": "#FFFFFF",
            "cyan": "#3A96DD",
            "foreground": "#FFFFFF",
            "green": "#13A10E",
            "name": "Color Scheme 15",
            "purple": "#881798",
            "red": "#C50F1F",
            "selectionBackground": "#FFFFFF",
            "white": "#CCCCCC",
            "yellow": "#C19C00"
        },
        {
            "background": "#282A36",
            "black": "#21222C",
            "blue": "#BD93F9",
            "brightBlack": "#6272A4",
            "brightBlue": "#D6ACFF",
            "brightCyan": "#A4FFFF",
            "brightGreen": "#69FF94",
            "brightPurple": "#FF92DF",
            "brightRed": "#FF6E6E",
            "brightWhite": "#FFFFFF",
            "brightYellow": "#FFFFA5",
            "cursorColor": "#F8F8F2",
            "cyan": "#8BE9FD",
            "foreground": "#F8F8F2",
            "green": "#50FA7B",
            "name": "Dracula",
            "purple": "#FF79C6",
            "red": "#FF5555",
            "selectionBackground": "#44475A",
            "white": "#F8F8F2",
            "yellow": "#F1FA8C"
        }
    ],
    "tabWidthMode": "titleLength",
    "themes": [],
    "useAcrylicInTabRow": true
}
```

---

## 🎨 Color Palette

| Element | Color | Hex |
|---|---|---|
| Primary Red | 🔴 | `#DA251D` |
| Primary Yellow | 🟡 | `#FFCD00` |
| Background | ⬛ | `#1A0A0A` |
| Foreground | 🟫 | `#F5E6C8` |
| Cursor | 🟡 | `#FFCD00` |

---

## ❓ Troubleshooting

**Icons showing as weird characters?** → Nerd Font is not installed or not set in Windows Terminal.

**`Get-PSReadLineKeyHandler` errors?** → Run: `Install-Module PSReadLine -Force -SkipPublisherCheck -Scope CurrentUser`

**Theme not loading in new tabs?** → Ensure only **one** `oh-my-posh init` line exists in `$PROFILE`.

**Still seeing the loading time message?** → Make sure `Clear-Host` comes after `oh-my-posh init` in `$PROFILE`.

---

## 📁 File Reference

| File | Description |
|---|---|
| `vietnam.omp.json` | Oh My Posh theme (red & yellow) |
| `config.jsonc` | Fastfetch configuration |
| `vietnam-small.txt` | ASCII art logo for Fastfetch |
| `settings.json` | Windows Terminal settings |

---

<div align="center">
  Made with ❤️ 🇻🇳
</div>
