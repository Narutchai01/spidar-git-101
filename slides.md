---
theme: seriph
title: Git 101 - เรียนรู้ Git สำหรับมือใหม่
info: |
  ## Git 101 - เรียนรู้ Git สำหรับมือใหม่
  สไลด์สำหรับเรียนรู้พื้นฐาน Git และ GitHub

  สำหรับนักพัฒนามือใหม่
class: text-center
drawings:
  persist: false
transition: slide-left
mdc: true
colorSchema: auto
lineNumbers: true
---

# Git 101

## เรียนรู้ Git สำหรับมือใหม่

<div class="pt-12">
  <span class="px-2 py-1 rounded cursor-pointer text-white bg-blue-500">
    Version Control System
  </span>
</div>

<div class="abs-br m-6 flex gap-2">
  <a href="https://github.com" target="_blank" alt="GitHub" title="GitHub"
    class="text-xl slidev-icon-btn opacity-50 !border-none !hover:text-white">
    <carbon-logo-github />
  </a>
</div>

---

# What is Git?

Git คือระบบควบคุมเวอร์ชัน (Version Control System) ที่ช่วยให้นักพัฒนาสามารถ:

- **ติดตามการเปลี่ยนแปลง** ของโค้ดตลอดเวลา
- **ย้อนกลับ** ไปยังเวอร์ชันก่อนหน้าได้
- **ทำงานร่วมกัน** หลายคนในโปรเจกต์เดียวกัน
- **จัดการ branch** สำหรับฟีเจอร์ต่างๆ
- **เก็บประวัติ** การทำงานทั้งหมดไว้

> Git ทำให้การพัฒนาซอฟต์แวร์เป็นระบบและปลอดภัยมากขึ้น

---

## ติดตั้ง Git

<div class="grid grid-cols-2 gap-8 mt-8">
  <div>
    <h3>🍎 macOS</h3>
    <ul>
      <li>ติดตั้งผ่าน Homebrew:</li>
    </ul>
    
```bash
brew install git
```
    
    <ul>
      <li>หรือดาวน์โหลดจาก git-scm.com</li>
    </ul>
  </div>

  <div>
    <h3>🪟 Windows</h3>
    <ul>
      <li>ดาวน์โหลด Git for Windows</li>
      <li>จาก git-scm.com</li>
      <li>ติดตั้งพร้อม Git Bash</li>
    </ul>
  </div>
</div>

<div class="mt-8">
  <h3>✅ ตรวจสอบการติดตั้ง</h3>
  
```bash
git --version
```
</div>

---

## การตั้งค่า Git เบื้องต้น

ก่อนใช้งาน Git ครั้งแรก ต้องตั้งค่าข้อมูลส่วนตัว:

```bash
# ตั้งค่าชื่อผู้ใช้
git config --global user.name "ชื่อของคุณ"

# ตั้งค่าอีเมล
git config --global user.email "your.email@example.com"

# ตรวจสอบการตั้งค่า
git config --list
```

<v-click>

**💡 เคล็ดลับ:** ใช้อีเมลเดียวกับที่ลงทะเบียนใน GitHub เพื่อให้ commit แสดงถูกต้อง

</v-click>

---

## สร้าง Repository แรก

<div class="grid grid-cols-2 gap-8">
  <div>
    <h3>📁 สร้าง Repo ใหม่</h3>
    
```bash
# สร้างโฟลเดอร์โปรเจกต์
mkdir my-project
cd my-project

# เริ่มต้น Git repository

git init

# สร้างไฟล์แรก

echo "# My Project" > README.md

````
  </div>

  <div>
    <h3>📋 Clone จาก GitHub</h3>

```bash
# Clone repository ที่มีอยู่แล้ว
git clone https://github.com/user/repo.git

# เข้าไปในโฟลเดอร์
cd repo
````

  </div>
</div>

---

# Git Workflow แบบง่าย

<div class="text-center mt-16">
  <h2 class="text-4xl mb-8">🛒 → 📦 → 📮</h2>
  <h2 class="text-2xl">เลือกของ → แพ็คของ → ส่งไปรษณีย์</h2>
  <h2 class="text-xl mt-4 text-blue-600">git add → git commit → git push</h2>
</div>

<div class="mt-16">
  <h3>ขั้นตอนการทำงาน:</h3>
  <ol>
    <li><strong>Working Directory</strong> - โฟลเดอร์ที่เราทำงาน</li>
    <li><strong>Staging Area</strong> - เลือกไฟล์ที่จะ commit</li>
    <li><strong>Repository</strong> - บันทึกการเปลี่ยนแปลง</li>
    <li><strong>Remote Repository</strong> - ส่งไปยัง GitHub</li>
  </ol>
</div>

---

# Keywords ของ Git

- **Repository (Repo)**: โฟลเดอร์ที่เก็บโค้ดและประวัติการเปลี่ยนแปลง
- **Clone**: การคัดลอก Repo จาก GitHub มาที่เครื่องเรา
- **Stage**: การเลือกไฟล์ที่ต้องการจะบันทึกการเปลี่ยนแปลง
- **Add**: การเพิ่มไฟล์ที่เลือกไปยัง Stage
- **Commit**: การบันทึกการเปลี่ยนแปลงที่เลือกไว้ใน Stage
- **Push**: การส่งการเปลี่ยนแปลงที่บันทึกไป
- **Pull**: การดึงการเปลี่ยนแปลงล่าสุดจาก Repo บน GitHub มาที่เครื่องเรา

---

# Git Add

<span class="text-2xl">🛒</span>

**เลือกไฟล์ที่ต้องการบันทึก**

- ใช้คำสั่ง `git add <file>` เพื่อเพิ่มไฟล์เฉพาะ
- ใช้คำสั่ง `git add .` เพื่อเพิ่มไฟล์ทั้งหมดในโฟลเดอร์ปัจจุบัน
- ใช้คำสั่ง `git add *.js` เพื่อเพิ่มไฟล์ JavaScript ทั้งหมด

```bash
# เพิ่มไฟล์เฉพาะ
git add index.html

# เพิ่มไฟล์หลายไฟล์
git add index.html style.css script.js

# เพิ่มไฟล์ทั้งหมด
git add .

# เพิ่มไฟล์ตามรูปแบบ
git add *.css
```

<v-click>

**💡 เคล็ดลับ:** ใช้ `git add -A` เพื่อเพิ่มไฟล์ทั้งหมด รวมถึงไฟล์ที่ถูกลบด้วย

</v-click>

---

# Git Commit

<span class="text-2xl">📦</span>

**บันทึกการเปลี่ยนแปลงอย่างถาวร**

- ใช้คำสั่ง `git commit -m "ข้อความ"` เพื่อบันทึกการเปลี่ยนแปลงที่อยู่ใน Staging Area
- ข้อความควรอธิบายการเปลี่ยนแปลงที่ทำอย่างชัดเจน
- แต่ละ commit จะมี ID เฉพาะ (hash) สำหรับการอ้างอิง

```bash
# Commit พร้อมข้อความ
git commit -m "เพิ่มหน้า login สำหรับผู้ใช้"

# Commit และ add ไฟล์ที่แก้ไขทั้งหมดในคำสั่งเดียว
git commit -am "แก้ไข bug ในการ validation"

# ดูประวัติ commit
git log --oneline
```

<div class="mt-4">
  <h3>✍️ เขียน Commit Message ให้ดี:</h3>
  <ul>
    <li>✅ "เพิ่มระบบ authentication"</li>
    <li>✅ "แก้ไข bug การแสดงผลใน mobile"</li>
    <li>❌ "update"</li>
    <li>❌ "fix stuff"</li>
  </ul>
</div>

---

# Git Push

<span class="text-2xl">📮</span>

**ส่งการเปลี่ยนแปลงไปยัง Remote Repository**

- ใช้คำสั่ง `git push origin <branch>` เพื่อส่งการเปลี่ยนแปลงไปยัง GitHub
- `<branch>` คือชื่อสาขาที่ต้องการส่ง เช่น `main` หรือ `master`
- ต้องมีการเชื่อมต่อกับ Remote Repository ก่อน

```bash
# Push ไปยัง branch หลัก
git push origin main

# Push ครั้งแรก (ตั้งค่า upstream)
git push -u origin main

# Push branch ใหม่
git push origin feature-login

# ดู remote repositories
git remote -v
```

<div class="mt-4">
  <h3>🔗 เชื่อมต่อกับ GitHub:</h3>
  
```bash
# เพิ่ม remote repository
git remote add origin https://github.com/username/repo.git

# ตรวจสอบการเชื่อมต่อ

git remote -v

````
</div>

---

## Git Pull

<span class="text-2xl">⬇️</span>

**ดึงการเปลี่ยนแปลงล่าสุดจาก Remote Repository**

- ใช้เมื่อต้องการอัปเดตโค้ดในเครื่องให้เป็นเวอร์ชันล่าสุด
- ควรทำก่อน push เสมอเพื่อหลีกเลี่ยง conflict

```bash
# ดึงการเปลี่ยนแปลงล่าสุด
git pull origin main

# ดูความแตกต่างก่อน pull
git fetch origin
git diff main origin/main
````

---

## คำสั่ง Git ที่ใช้บ่อย

| คำสั่ง         | คำอธิบาย                    |
| -------------- | --------------------------- |
| `git status`   | ดูสถานะไฟล์                 |
| `git log`      | ดูประวัติ commit            |
| `git diff`     | ดูความแตกต่างของไฟล์        |
| `git branch`   | จัดการ branch               |
| `git checkout` | เปลี่ยน branch หรือย้อนกลับ |
| `git reset`    | ยกเลิกการเปลี่ยนแปลง        |
| `git stash`    | เก็บการเปลี่ยนแปลงชั่วคราว  |

---

## เคล็ดลับและ Best Practices

<div class="grid grid-cols-2 gap-8">
  <div>
    <h3>✅ ควรทำ:</h3>
    <ul>
      <li>Commit บ่อยๆ ในชิ้นงานเล็กๆ</li>
      <li>เขียน commit message ที่มีความหมาย</li>
      <li>Pull ก่อน push เสมอ</li>
      <li>ใช้ .gitignore สำหรับไฟล์ที่ไม่ต้องการ</li>
      <li>สำรองข้อมูลบน remote repository</li>
    </ul>
  </div>

  <div>
    <h3>❌ ไม่ควรทำ:</h3>
    <ul>
      <li>Commit ไฟล์ที่มี sensitive data</li>
      <li>Force push ใน branch หลัก</li>
      <li>Commit โค้ดที่ยังทำงานไม่ได้</li>
      <li>ใช้ commit message แบบไม่มีความหมาย</li>
      <li>ลืม pull ก่อน push</li>
    </ul>
  </div>
</div>

---

## ไฟล์ .gitignore

**ระบุไฟล์ที่ไม่ต้องการให้ Git ติดตาม**

```bash
# ไฟล์ระบบ
.DS_Store
Thumbs.db

# Dependencies
node_modules/
vendor/

# Build outputs
dist/
build/
*.log

# Environment variables
.env
.env.local

# IDE files
.vscode/
.idea/
*.swp
```

<v-click>

**💡 สร้างไฟล์ .gitignore ในรูท directory ของโปรเจกต์**

</v-click>

---

## สรุป

<div class="text-center">
  <h2 class="text-3xl mb-8">🎯 สิ่งที่เราได้เรียนรู้</h2>
</div>

<div class="grid grid-cols-2 gap-8">
  <div>
    <h3>📚 ความรู้พื้นฐาน:</h3>
    <ul>
      <li>Git คือระบบควบคุมเวอร์ชัน</li>
      <li>GitHub คือแพลตฟอร์มเก็บโค้ด</li>
      <li>Repository คือที่เก็บโปรเจกต์</li>
      <li>Commit คือการบันทึกการเปลี่ยนแปลง</li>
    </ul>
  </div>

  <div>
    <h3>⚡ คำสั่งหลัก:</h3>
    <ul>
      <li><code>git status</code> - ดูสถานะ</li>
      <li><code>git add</code> - เลือกไฟล์</li>
      <li><code>git commit</code> - บันทึก</li>
      <li><code>git push</code> - อัปโหลด</li>
      <li><code>git pull</code> - ดาวน์โหลด</li>
    </ul>
  </div>
</div>

<div class="mt-8 text-center">
  <h3>🚀 ขั้นตอนต่อไป: ฝึกใช้ Git ในโปรเจกต์จริง!</h3>
</div>

---

<div class="text-center mt-48">
  <h2 class="text-6xl mb-8">🙋‍♂️</h2>
  <h2 class="text-4xl">Q&A</h2>
  <p class="text-xl mt-4 opacity-75">มีคำถามเกี่ยวกับ Git ไหม?</p>
</div>
