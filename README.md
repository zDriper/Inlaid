Script Inlaid

It is a PNG scanner that detects embedded PE (EXE) executables using binary concatenation (copy /b image.png + exe.exe).

¿How does it work?

It scans common user folders (Desktop, Downloads, Documents, Pictures, Images).
It only analyzes .png files. It opens them in full binary and looks for the MZ signature, which is the typical header of a PE executable. With this information, it validates that it is a real EXE. If the EXE is embedded, it extracts it from the starting offset and saves it as image.png.extracted.exe
