# 🧠 How to Avoid Cyrillic Characters in File or Folder Names (macOS)

Sometimes your terminal or script may not work because a folder or file name contains a **Cyrillic character** that looks like a Latin one. This is especially common with the letter **`c`**.

---

## ❗ Example Mistake:

| Correct (Latin) | Incorrect (Cyrillic) |
|------------------|----------------------|
| `scripts`        | `sсripts` *(with Cyrillic 'с')*

They look identical — but are **different Unicode characters**!

---

## 📌 How to Check:

1. Copy the file or folder name  
2. Paste it into a code editor (like VS Code or Sublime Text)  
3. Highlight the suspicious character  
4. Check the Unicode:

| Character | Code    | Meaning       |
|-----------|---------|---------------|
| `c`       | `U+0063` | Latin ✅       |
| `с`       | `U+0441` | Cyrillic ❌    |

---

## ✅ How to Fix It:

- Rename the folder or file manually  
- Delete the incorrect character and retype it using **English keyboard layout**  
- Avoid auto-complete or switching keyboard while typing paths  

---

##  Update your PATH if the folder name has changed:

```bash
echo 'export PATH=$PATH:$HOME/Desktop/tech/scripts' >> ~/.zprofile
source ~/.zprofile





~ V.R