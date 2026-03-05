**Goal:** по требованиям подобрать правильные числовые права и применить их.

---
### A) `exercise.txt`
**Требование:**
- owner: `rwx`
- group: `r-x`
- others: `---`
✅ **Ответ:** `750`
chmod 750 exercise.txt

---
### B) `secret.txt`
**Требование:**
- owner: `rw-`
- group: `---`
- others: `---`
✅ **Ответ:** `600`
chmod 600 secret.txt

---
### C) `shared_dir` (directory)
**Требование:**
- owner: `rwx`
- group: `r-x`
- others: `r-x`
✅ **Ответ:** `755`
chmod 755 shared_dir

---
### 🔎 Быстрая проверка
```
ls -l exercise.txt secret.txt  
ls -ld shared_dir
```
