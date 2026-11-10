<div align="center">

# 🤖 Telegram AI Bot

**Kanal boshqaruvi, AI postlar va testlar uchun Telegram bot**

Muallif: [bolaxoji3-collab](https://github.com/bolaxoji3-collab)

![Python](https://img.shields.io/badge/Python-3.10%2B-3776AB?logo=python&logoColor=white)
![Telegram](https://img.shields.io/badge/Telegram-Bot-26A5E4?logo=telegram&logoColor=white)
![AI](https://img.shields.io/badge/AI-Groq-F55036)
![SQLite](https://img.shields.io/badge/DB-SQLite-003B57?logo=sqlite&logoColor=white)
![Termux](https://img.shields.io/badge/Platform-Termux-000000)

</div>

> [!NOTE]
> Bot Telegram qoidalariga va mamlakatingiz qonunlariga mos kontent uchun mo'ljallangan. Kanal va foydalanuvchilar oldidagi mas'uliyat bot egasida.

---

## 📌 Umumiy ma'lumot

**Telegram AI Bot** — ikki ishni bajaradigan bot:

1. **Kanal boshqaruvi.** Bot admin bo'lgan kanal va guruhlarga belgilangan vaqtda tayyor matnni yoki AI yozgan postni yuboradi. AI kanaldagi oxirgi postlarga qarab, ularning tili va uslubida yangi post yozadi.
2. **O'quv qismi.** Foydalanuvchilar admin yuklagan testlar va darsliklardan foydalanadi, AI yordamida test yechadi va mavzu bo'yicha ma'lumot oladi. Adminlar uchun reyting va foydalanuvchilar ro'yxati bor.

Hammasi tugmalar orqali boshqariladi, buyruq yodlash shart emas.

## ✨ Imkoniyatlar

| Modul | Tavsif |
|-------|--------|
| 📢 **Kanallar** | Bot admin bo'lgan kanal va guruhlarni qo'shish, ko'rish, o'chirish |
| ⏰ **Rejalar** | Vaqt va hafta kunlari bo'yicha avtomatik post, to'xtatish, davom ettirish, hozir yuborish |
| 🤖 **AI post** | Kanal uslubida yangi post yozish, yuborishdan oldin ko'rish va qayta yozdirish |
| 📥 **Namunalar** | Eski postlarni forward qilib, AI'ga uslubni o'rgatish |
| 📚 **Kontent** | Admin testlar va darsliklarni (matn, rasm, video, fayl, audio) yuklaydi |
| 📝 **AI testlar** | Tezkor test (5 ta savol) va mavzudan test (30 ta savol) |
| 📖 **AI ma'lumot** | Istalgan o'quv mavzusi bo'yicha tushuntirish |
| 🏆 **Reyting** | To'g'ri javoblar bo'yicha Top 20 va umumiy foydalanuvchilar soni |
| 👥 **Foydalanuvchilar** | Ro'yxat, faollik, natijalar, bloklash |
| ⚙️ **Sozlamalar** | AI modeli, kontekst hajmi, vaqt zonasi, kunlik limit |

## 🛠 O'rnatish

### Termux (Android)

```bash
pkg update -y
pkg install -y git python
cd ~
git clone https://github.com/bolaxoji3-collab/Telegram-Ai-test-.git
cd Telegram-Ai-test-
pip install -r requirements.txt
```

### Kerakli kalitlar

| Nima | Qayerdan olinadi |
|------|------------------|
| Bot tokeni | Telegramda [@BotFather](https://t.me/BotFather) → `/newbot` |
| Groq kaliti (bepul) | [console.groq.com](https://console.groq.com) → API Keys |
| Telegram ID | [@userinfobot](https://t.me/userinfobot) |

## ⚙️ Sozlash

Loyiha papkasida `.env` faylini yarating:

```bash
cat > .env << 'EOF'
BOT_TOKEN=BOTFATHER_TOKENI
AI_PROVIDER=groq
GROQ_API_KEY=GROQ_KALITI
ADMIN_IDS=SIZNING_ID
TZ_OFFSET_HOURS=5
CONTEXT_POSTS=15
EOF
```

| O'zgaruvchi | Tavsif |
|-------------|--------|
| `BOT_TOKEN` | BotFather bergan token |
| `AI_PROVIDER` | `groq` yoki `openai` |
| `GROQ_API_KEY` | Groq kaliti (`openai` tanlansa `OPENAI_API_KEY`) |
| `ADMIN_IDS` | Admin Telegram ID'lari, vergul bilan, probelsiz: `111,222` |
| `TZ_OFFSET_HOURS` | Vaqt zonasi (Toshkent va Farg'ona uchun `5`) |
| `CONTEXT_POSTS` | AI yozishda nechta oxirgi postga qarashi |
| `AI_MODEL` | Ixtiyoriy, modelni qo'lda belgilash |

## 🚀 Ishga tushirish

```bash
python bot.py
```

Ekranda **"Bot ishga tushdi"** chiqsa, bot tayyor. Botga Telegramda `/start` yozing va uni kanalga admin qilib qo'shing (kanalda **Post messages** huquqi bilan).

Fonda ishlatish:

```bash
termux-wake-lock
nohup python bot.py > bot.log 2>&1 &
```

To'xtatish: `pkill -f bot.py`

## 📖 Foydalanish

### Admin menyusi

```
📢 Kanallarim        ➕ Kanal qo'shish
➕ Yangi reja        📋 Rejalarim
🤖 AI post           ✉️ Hozir yuborish
📥 Namuna qo'shish   ⚙️ Sozlamalar
📚 Kontent           🏆 Reyting
👥 Foydalanuvchilar  👤 Foydalanuvchi menyusi
```

### Foydalanuvchi menyusi

```
📝 Testlar           📚 Ma'lumotlar
🤖 AI
   ├─ ⚡ Tezkor test
   ├─ 📖 Ma'lumot olmoqchiman
   └─ 📝 Mavzudan test
```

## 🧩 Modullar

### Rejalashtirilgan postlar

| Tur | Ishlashi |
|-----|----------|
| 📝 Tayyor matn | Admin yozgan matn belgilangan vaqtda yuboriladi |
| 🤖 AI | Har safar kanal uslubida yangi post yoziladi |

Reja vaqti `09:00` ko'rinishida, hafta kunlari ixtiyoriy tanlanadi (hech narsa tanlanmasa, har kuni).

### AI testlar

| Test | Savollar | Javob berish |
|------|----------|--------------|
| ⚡ **Tezkor test** | 5 ta | Javoblar ko'rsatilmaydi. Foydalanuvchi `1a 2b 3c 4d 5a` ko'rinishida yuboradi |
| 📝 **Mavzudan test** | 30 ta (10 ta oson, 15 ta o'rta, 5 ta qiyin) | Pastda **Javoblarni bilish** va **Javoblarni yuborish** tugmalari bor |

> [!IMPORTANT]
> Mavzudan testda javoblarni ko'rgan foydalanuvchi keyin javob yuborolmaydi, natija reytingga hisoblanmaydi.

Test boshlashdan oldin mavzu yoziladi va daraja (oson, o'rta, qiyin) tanlanadi.

### Admin kontenti

| Amal | Tavsif |
|------|--------|
| ➕ Qo'shish | Nom yoziladi, so'ng matn, rasm, video, fayl yoki audio yuboriladi |
| 📋 Ro'yxat | Foydalanuvchilar raqamlangan ro'yxatni ko'radi, raqamni bossa material yuboriladi |
| 🗑 O'chirish | Admin materialni o'chiradi |

### 🏆 Reyting

To'g'ri javoblar soni bo'yicha eng yaxshi 20 ta foydalanuvchi, test soni va aniqlik foizi bilan. Adminlarning natijalari reytingga kirmaydi.

## 📋 Talablar

| Talab | Versiya / Izoh |
|-------|----------------|
| Python | 3.10 yoki yuqori |
| `httpx` | `pip install -r requirements.txt` |
| Ma'lumotlar bazasi | SQLite (alohida o'rnatish shart emas) |
| Internet | Telegram va Groq/OpenAI API uchun |
| Platforma | Termux (Android) yoki istalgan Linux |

## 🔄 Yangilash

```bash
cd ~/Telegram-Ai-test-
git pull
```

`.env` va `bot.db` GitHub'da yo'q, shuning uchun yangilanganda o'zgarmaydi.

## 🔒 Xavfsizlik

- `.env` faylini hech qachon GitHub'ga yuklamang va hech kimga yubormang.
- Token yoki kalit oshkor bo'lsa, darhol yangilang: BotFather'da `/revoke`, Groq'da yangi kalit.
- `ADMIN_IDS` ga faqat ishonchli odamlarni qo'shing.
- Bepul AI limiti tugasa, bot "AI hozir band" xabarini ko'rsatadi.

## ⚖️ Mas'uliyat

Loyiha ta'lim va shaxsiy foydalanish uchun. Bot orqali yuboriladigan kontent uchun bot egasi javobgar. Telegram foydalanish shartlariga va O'zbekiston qonunlariga rioya qiling.

## ☁️ Bepul serverda (Render, 24/7) ishlatish

Bot ikki rejimda ishlaydi: **polling** (Termux, `.env` bilan, avvalgidek) va **webhook** (bepul server).
`WEBHOOK_URL` yoki `RENDER_EXTERNAL_URL` bor bo'lsa, o'zi webhook rejimiga o'tadi.

1. Kodni GitHub'ga yuklang (`.env` va `bot.db` ni yuklamang).
2. [render.com](https://render.com) → **New → Web Service** → repoingizni tanlang.
   Build: `pip install -r requirements.txt`, Start: `python bot.py`, Plan: **Free**.
3. **Environment** bo'limiga yozing: `BOT_TOKEN`, `GROQ_API_KEY`, `ADMIN_IDS`, `AI_PROVIDER=groq`, `TZ_OFFSET_HOURS=5`, `PYTHON_VERSION=3.12.3`.
4. Deploy tugagach, [cron-job.org](https://cron-job.org) (yoki UptimeRobot) da **har 5-10 daqiqada** `https://SIZNING-NOM.onrender.com/health` ga so'rov yuboradigan vazifa yarating.
   Busiz Render 15 daqiqada uxlatadi va rejalashtirilgan postlar chiqmay qoladi.
5. Botni `ADMIN_IDS` dagi admin akkauntidan bir marta `/start` qiling: zaxira nusxa shu chatga keladi.

**Baza qanday saqlanadi?** Render bepul rejasida disk saqlanmaydi. Shuning uchun bot `bot.db` ni har o'zgarishdan keyin
(10 daqiqada bir) va o'chirilishdan oldin adminning chatiga fayl qilib yuboradi va **pin** qiladi.
Server qayta ishga tushsa, bazani o'sha pin qilingan fayldan o'zi tiklaydi.
⚠️ Admin chatidagi pin qilingan `bot.db` faylini o'chirmang va boshqa narsani pin qilmang.

Qo'shimcha o'zgaruvchilar: `BACKUP_CHAT` (zaxira boradigan chat ID, standart: birinchi admin), `BACKUP_MINUTES` (standart 10), `WEBHOOK_SECRET`.
