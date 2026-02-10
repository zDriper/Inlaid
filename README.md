---

# Script Inlaid

**Script Inlaid** is a scanner that detects **Windows PE (EXE) executables embedded inside PNG images** using binary concatenation techniques such as:

```
copy /b image.png + payload.exe image.png
```

This technique is commonly used to create **PNG/EXE polyglot files** for basic steganography, or evasion.

---

## Features

* Scans PNG files for embedded PE executables
* Validates real PE headers (`MZ` → `PE\0\0`) to avoid false positives
* Automatically extracts detected executables

---

## ¿How does it work?

1. The script scans common user directories:

   * Desktop
   * Downloads
   * Documents
   * Pictures / Images

2. It analyzes only `.png` files and reads them entirely in binary mode.

3. It searches for the `MZ` signature, the standard header of Windows PE executables.

4. When `MZ` is found, the script:

   * Reads the PE header offset (`e_lfanew`)
   * Confirms the presence of the `PE\0\0` signature
   * Ensures the executable size is valid

5. If a PE executable is embedded inside the PNG:

   * The payload is extracted starting from its offset
   * It is saved as `image.png.extracted.exe`

---
