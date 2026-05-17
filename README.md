# 🇻🇳 Vietnam Terminal Setup

### Bạn Muốn Terminal Của Bạn Như Thế Này?:
<img width="1248" height="674" alt="image" src="https://github.com/user-attachments/assets/dcdae052-8a2d-4409-b432-dcab061ce3ab" />


> Terminal setup với **Oh My Posh** theme Việt Nam — đỏ & vàng chuẩn cờ đỏ sao vàng.

![OS](https://img.shields.io/badge/OS-Windows%2010%2F11-blue?style=flat-square&logo=windows)
![OhMyPosh](https://img.shields.io/badge/Oh%20My%20Posh-v24%2B-DA251D?style=flat-square)
![PowerShell](https://img.shields.io/badge/PowerShell-5.1%2B-FFCD00?style=flat-square&logo=powershell)

---

## 📥 Tải file

Vào trang repo này, tải về các file sau:

| File | Mô tả |
|---|---|
| `vietnam.omp.json` | Theme Oh My Posh màu đỏ-vàng VN |
| `config.jsonc` | Config Fastfetch |
| `vietnam_ascii.txt` | ASCII art logo cho Fastfetch |
| `settings.json` | Windows Terminal settings |

> **Cách tải:** Click vào tên file → nhấn nút **Download raw file** (biểu tượng tải xuống góc phải) → lưu vào thư mục `Downloads`.

---

## 📋 Yêu cầu

- Windows 10/11
- [Windows Terminal](https://aka.ms/terminal) (tải miễn phí trên Microsoft Store)
- PowerShell 5.1+
- Kết nối Internet

---

## 🚀 Cài đặt từng bước

### Bước 1 — Cài Oh My Posh

Mở **PowerShell** và chạy lệnh sau:

```powershell
winget install JanDeDobbeleer.OhMyPosh -s winget
```

✅ Sau khi xong → **đóng và mở lại PowerShell**.

---

### Bước 2 — Cài Nerd Font

Oh My Posh cần **Nerd Font** để hiển thị icon đúng. Chạy lệnh:

```powershell
oh-my-posh font install JetBrainsMono
```

Sau đó vào **Windows Terminal → Settings → Defaults → Appearance → Font face** và chọn:

```
JetBrainsMono Nerd Font Mono
```

✅ Nhấn **Save**.

---

### Bước 3 — Cài PSReadLine (fix lỗi)

```powershell
Install-Module PSReadLine -Force -SkipPublisherCheck -Scope CurrentUser
```

✅ Sau khi xong → **đóng và mở lại PowerShell**.

---

### Bước 4 — Áp dụng theme Vietnam

Mở file PowerShell Profile:

```powershell
notepad $PROFILE
```

> ⚠️ Nếu báo lỗi file không tồn tại, chạy lệnh này trước:
> ```powershell
> New-Item -Path $PROFILE -Type File -Force
> ```

**Xóa toàn bộ nội dung cũ** và dán đoạn sau vào (thay `YourUsername` bằng tên user của bạn):

```powershell
Set-Location "C:\Users\YourUsername"
oh-my-posh init pwsh --config "C:\Users\YourUsername\Downloads\vietnam.omp.json" | Invoke-Expression
```

✅ Nhấn **Ctrl+S** để lưu → đóng Notepad → **restart PowerShell**.

---

### Bước 5 — (Tùy chọn) Cài Fastfetch

Fastfetch hiển thị thông tin máy tính mỗi khi mở terminal.

**Cài Fastfetch:**
```powershell
winget install fastfetch-cli.fastfetch
```

**Tạo thư mục config:**
```powershell
mkdir "$env:USERPROFILE\.config\fastfetch"
```

**Copy file config vào:**
```powershell
copy "C:\Users\YourUsername\Downloads\config.jsonc" "$env:USERPROFILE\.config\fastfetch\"
copy "C:\Users\YourUsername\Downloads\vietnam_ascii.txt" "$env:USERPROFILE\.config\fastfetch\"
```

✅ Restart PowerShell là xong.

---

### Bước 6 — (Tùy chọn) Đổi màu Windows Terminal sang Vietnam

1. Mở **Windows Terminal**
2. Nhấn `Ctrl+,` để mở Settings
3. Góc dưới bên trái → nhấn **biểu tượng bánh răng ⚙️** (Open JSON file)
4. Nhấn `Ctrl+A` để chọn tất cả → **xóa đi**
5. Dán toàn bộ nội dung file `settings.json` đã tải vào
6. Nhấn `Ctrl+S` để lưu

✅ Đóng và mở lại Windows Terminal.

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

| Segment | Mô tả |
|---|---|
| 📁 Path | Đường dẫn hiện tại, home hiện `~` |
| 🌿 Git | Branch, trạng thái working/staging |
| ✅ Status | `♥` nếu OK, `💔` nếu lỗi |
| 🌐 Network | Icon kết nối mạng |
| 🔋 Battery | % pin + trạng thái sạc |
| ⏱ Exec Time | Thời gian lệnh vừa chạy |
| 📅 Time | Ngày + giờ |
| 💻 OS | Icon hệ điều hành |
| 👤 Username | Tên user (+ SSH icon nếu remote) |

---

## ❓ Troubleshooting

**❌ Icon hiện ký tự lạ thay vì icon đẹp?**
→ Chưa cài hoặc chưa chọn đúng Nerd Font trong Windows Terminal. Làm lại Bước 2.

**❌ Lỗi `Get-PSReadLineKeyHandler` khi mở terminal?**
→ Chạy: `Install-Module PSReadLine -Force -SkipPublisherCheck -Scope CurrentUser`

**❌ Theme không load khi mở tab mới?**
→ Kiểm tra file `$PROFILE` có đúng đường dẫn tới `vietnam.omp.json` chưa. Đảm bảo **chỉ có 1 dòng** `oh-my-posh init`.

**❌ Vẫn thấy dòng `Loading personal and system profiles took...`?**
→ Đảm bảo trong `$PROFILE` có dòng `Clear-Host` **sau** dòng `oh-my-posh init`.

## 📞 Hỗ trợ

- **Discord:** [Nhấn vào tôi để join server Discord](https://discord.gg/q2DzqWgpTC)
- **GitHub:** [Nhấn vào tôi để xem repo GitHub](https://github.com/Minh1234ngudot)
---
---

# 🇬🇧 English Version

### You Want Your Terminal Like This?:
<img width="1248" height="674" alt="image" src="https://github.com/user-attachments/assets/9a90cfc0-9e6c-4817-a533-dca311c61e09" />


> A beautiful terminal setup using **Oh My Posh** with a Vietnam-themed prompt — red & yellow inspired by the Vietnamese flag.

---

## 📥 Download Files

Go to this repo and download the following files:

| File | Description |
|---|---|
| `vietnam.omp.json` | Oh My Posh theme (red & yellow) |
| `config.jsonc` | Fastfetch configuration |
| `vietnam_ascii.txt` | ASCII art logo for Fastfetch |
| `settings.json` | Windows Terminal settings |

> **How to download:** Click the filename → click the **Download raw file** button (download icon, top right) → save to your `Downloads` folder.

---

## 📋 Requirements

- Windows 10/11
- [Windows Terminal](https://aka.ms/terminal) (free on Microsoft Store)
- PowerShell 5.1+
- Internet connection

---

## 🚀 Step-by-Step Installation

### Step 1 — Install Oh My Posh

Open **PowerShell** and run:

```powershell
winget install JanDeDobbeleer.OhMyPosh -s winget
```

✅ When done → **close and reopen PowerShell**.

---

### Step 2 — Install a Nerd Font

Oh My Posh needs a **Nerd Font** to display icons correctly. Run:

```powershell
oh-my-posh font install JetBrainsMono
```

Then go to **Windows Terminal → Settings → Defaults → Appearance → Font face** and select:

```
JetBrainsMono Nerd Font Mono
```

✅ Click **Save**.

---

### Step 3 — Fix PSReadLine Errors

```powershell
Install-Module PSReadLine -Force -SkipPublisherCheck -Scope CurrentUser
```

✅ When done → **close and reopen PowerShell**.

---

### Step 4 — Apply the Vietnam Theme

Open your PowerShell Profile:

```powershell
notepad $PROFILE
```

> ⚠️ If it says the file doesn't exist, run this first:
> ```powershell
> New-Item -Path $PROFILE -Type File -Force
> ```

**Clear all existing content** and paste the following (replace `YourUsername` with your Windows username):

```powershell
Set-Location "C:\Users\YourUsername"
oh-my-posh init pwsh --config "C:\Users\YourUsername\Downloads\vietnam.omp.json" | Invoke-Expression
```

✅ Press **Ctrl+S** to save → close Notepad → **restart PowerShell**.

---

### Step 5 — (Optional) Install Fastfetch

Fastfetch displays system information every time you open a terminal.

**Install Fastfetch:**
```powershell
winget install fastfetch-cli.fastfetch
```

**Create the config folder:**
```powershell
mkdir "$env:USERPROFILE\.config\fastfetch"
```

**Copy the config files:**
```powershell
copy "C:\Users\YourUsername\Downloads\config.jsonc" "$env:USERPROFILE\.config\fastfetch\"
copy "C:\Users\YourUsername\Downloads\vietnam_ascii.txt" "$env:USERPROFILE\.config\fastfetch\"
```

✅ Restart PowerShell and you're done.

---

### Step 6 — (Optional) Apply Vietnam Color Scheme in Windows Terminal

1. Open **Windows Terminal**
2. Press `Ctrl+,` to open Settings
3. Bottom left corner → click the **gear icon ⚙️** (Open JSON file)
4. Press `Ctrl+A` to select all → **delete it**
5. Paste the entire contents of the downloaded `settings.json` file
6. Press `Ctrl+S` to save

✅ Close and reopen Windows Terminal.

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

## 🔧 Prompt Structure

```
[path] [git branch] [git status] [exit status]     [network] [battery] [time]
[os] [username]                                              ♥♥♥ Việt Nam
```

| Segment | Description |
|---|---|
| 📁 Path | Current directory, home shown as `~` |
| 🌿 Git | Branch name, working/staging status |
| ✅ Exit Status | `♥` on success, `💔` on error |
| 🌐 Network | Network connection icon |
| 🔋 Battery | Battery percentage + charging status |
| ⏱ Exec Time | Duration of the last command |
| 📅 Date & Time | Current date and time |
| 💻 OS | Operating system icon |
| 👤 Username | Current user (+ SSH icon if remote session) |

---

## ❓ Troubleshooting

**❌ Icons showing as weird characters instead of icons?**
→ Nerd Font is not installed or not selected in Windows Terminal. Redo Step 2.

**❌ `Get-PSReadLineKeyHandler` errors on startup?**
→ Run: `Install-Module PSReadLine -Force -SkipPublisherCheck -Scope CurrentUser`

**❌ Theme not loading when opening a new tab?**
→ Check that `$PROFILE` has the correct path to `vietnam.omp.json`. Make sure there is **only one** `oh-my-posh init` line.

**❌ Still seeing `Loading personal and system profiles took...`?**
→ Make sure `Clear-Host` comes **after** the `oh-my-posh init` line in your `$PROFILE`.

## 📞 Support

- **Discord:** [Click me to join me Discord Server](https://discord.gg/q2DzqWgpTC)
- **GitHub:** [Click me to watch my GitHub Repo](https://github.com/Minh1234ngudot)
---

<div align="center">
  Made with ❤️ MinhZ
</div>
