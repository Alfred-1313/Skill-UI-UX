<div dir="rtl">

# 🎨 Skill UI/UX — اسکیل‌های ساخت ربات تلگرام

این ریپو دو تا **اسکیل** داره. اسکیل یعنی یک دستورالعمل آماده که به هوش مصنوعی می‌دی تا هر بار که برات ربات می‌سازه، از همون اول همون‌طوری بسازه که دوست داری؛ دیگه لازم نیست هر بار همه‌چیز رو از اول توضیح بدی.

این دو اسکیل از تجربهٔ ساخت ربات فروش **[Ciro](https://github.com/Alfred-1313/Ciro)** درآمدن. ولی به هیچ زبان برنامه‌نویسی و هیچ ربات خاصی بسته نیستن و روی هر ربات تلگرامی جواب می‌دن: PHP، Python، Node.js، Go و بقیه.

---

## 📦 داخلش چیه؟

| اسکیل | کارش چیه |
|---|---|
| 🎨 **`telegram-bot-customization`** | یاد می‌ده سیستم «🎨 شخصی‌سازی» رو توی هر ربات بسازی: ادمین بتونه **هر متن، دکمه، استیکر، ری‌اکشن، ایموجی پریمیوم، رنگ دکمه، چیدمان و کلید روشن/خاموش** رو جدا برای هر زبان عوض کنه؛ هم از داخل ربات، هم از پنل وب. |
| 🧭 **`bot-builder-style`** | سلیقه و روش کار خودت: جواب فارسی و روان، قابلیت جدید پیش‌فرض خاموش، هر قابلیت هم توی ربات و هم پنل وب و هم 🎨، پرداخت دقیق و بدون دوبار کسر یا دوبار ساخت، تست قبل از تحویل، یادداشت «تازه‌ها» برای ادمین تازه‌کار، و قوانین گیت. |

### ساختار فایل‌ها

<div dir="ltr">

```
skills/
├── telegram-bot-customization/
│   ├── SKILL.md                  ← اصل اسکیل
│   └── references/
│       ├── data-model.md         ← شکل ذخیرهٔ متن‌ها، دکمه‌ها، استیکرها و تنظیمات
│       ├── admin-screens.md      ← صفحه‌های ادمین، یکی‌یکی، با نمونهٔ متن
│       ├── web-panel.md          ← صفحه‌های پنل وب
│       └── checklist.md          ← چک‌لیست «تموم شد»
└── bot-builder-style/
    └── SKILL.md
dist/                             ← فایل‌های آماده برای نصب روی Claude.ai
AGENTS.md                         ← برای Codex، Cursor، Windsurf، Aider و …
GEMINI.md                         ← برای Gemini CLI
.github/copilot-instructions.md   ← برای GitHub Copilot
prompts/short-instructions.md     ← نسخهٔ کوتاه برای ChatGPT و Gemini (وب)
build.sh                          ← سه فایل بالا رو از روی اسکیل‌ها می‌سازه
```

</div>

---

## 🚀 نصب روی هر هوش مصنوعی

### Claude Code (ترمینال، اپ دسکتاپ، وب)

<div dir="ltr">

```bash
git clone https://github.com/Alfred-1313/Skill-UI-UX.git
# برای همهٔ پروژه‌هات:
cp -r Skill-UI-UX/skills/* ~/.claude/skills/
# یا فقط برای یک پروژه (داخل پوشهٔ همون پروژه):
mkdir -p .claude/skills && cp -r Skill-UI-UX/skills/* .claude/skills/
```

</div>

بعد از نصب، Claude هر وقت کار مربوط به ربات باشه خودش اسکیل رو باز می‌کنه.

### Claude.ai (سایت و اپ موبایل)

1. فایل‌های `dist/telegram-bot-customization.skill` و `dist/bot-builder-style.skill` رو دانلود کن.
2. برو به **Settings ← Capabilities ← Skills** (یا **Customize ← Skills**).
3. دکمهٔ **Upload skill** رو بزن و هر دو فایل رو آپلود کن.

### ChatGPT، Codex، Cursor، Windsurf، Aider

فایل **`AGENTS.md`** رو بذار ریشهٔ پروژهٔ رباتت. این ابزارها خودشون از روی همین فایل دستورها رو می‌خونن.

### Gemini CLI

فایل **`GEMINI.md`** رو بذار ریشهٔ پروژهٔ رباتت.

### GitHub Copilot

فایل **`.github/copilot-instructions.md`** رو با همین مسیر توی پروژه‌ات کپی کن.

### ChatGPT یا Gemini (نسخهٔ وب) و هر چت دیگه با جای محدود

متن داخل **`prompts/short-instructions.md`** (زیر ۱۵۰۰ کاراکتر) رو کپی کن و بچسبون:
- **ChatGPT:** Settings ← Personalization ← Custom instructions
- **Gemini:** یک Gem بساز و متن رو توی دستورهاش بذار

---

## 💬 بعد از نصب چطور ازش استفاده کنم؟

لازم نیست اسم اسکیل رو بیاری؛ عادی درخواستت رو بنویس. چند مثال:

- «یه ربات فروش اشتراک با پایتون می‌خوام که کیف پول و درگاه کارت‌به‌کارت داشته باشه.»
- «به رباتم یه بخش کد تخفیف اضافه کن.»
- «پیام خوش‌آمد و دکمه‌های منوی اصلی باید از پنل ادمین قابل تغییر باشن.»
- «رباتم رو دوزبانه کن (فارسی و انگلیسی).»

هوش مصنوعی خودش این کارها رو انجام می‌ده:
- متن‌ها و دکمه‌ها رو قابل شخصی‌سازی می‌سازه.
- قابلیت جدید رو پیش‌فرض خاموش می‌ذاره.
- قابلیت رو هم به پنل وب اضافه می‌کنه.
- قبل از تحویل تست می‌کنه.
- آخر کار یه یادداشت «تازه‌ها» با مسیر منو برات می‌نویسه.

---

## ✏️ ویرایش اسکیل‌ها

1. فقط فایل‌های داخل پوشهٔ `skills/` رو عوض کن.
2. بعد این دستور رو اجرا کن:

<div dir="ltr">

```bash
./build.sh
```

</div>

این دستور `AGENTS.md`، `GEMINI.md` و `.github/copilot-instructions.md` رو از روی اسکیل‌ها دوباره می‌سازه تا همه یکی بمونن.

3. اگه فایل‌های `dist/*.skill` رو هم برای Claude.ai می‌خوای به‌روز کنی، پوشهٔ هر اسکیل رو zip کن و پسوند فایل رو `.skill` بذار.

---

## ❓ سؤال‌های رایج

**چرا متن اسکیل‌ها انگلیسیه؟**
چون همهٔ هوش‌های مصنوعی دستور انگلیسی رو دقیق‌تر دنبال می‌کنن. ولی خود اسکیل بهشون می‌گه با تو فارسی و روان حرف بزنن، و نمونهٔ متن‌های ربات هم فارسیه.

**فقط برای ربات‌های VPN به درد می‌خوره؟**
نه. هر ربات تلگرامی که مشتری و ادمین داره (فروشگاه، رزرو، پشتیبانی، آموزش و …) می‌تونه ازش استفاده کنه.

**می‌تونم سلیقهٔ خودم رو بهش اضافه کنم؟**
آره. فایل `skills/bot-builder-style/SKILL.md` رو باز کن، چیزی که می‌خوای رو اضافه یا کم کن، بعد `./build.sh` رو اجرا کن.

</div>

---

<details>
<summary>English</summary>

Two portable AI skills extracted from building the [Ciro](https://github.com/Alfred-1313/Ciro) Telegram shop bot:

- **telegram-bot-customization**: build a full admin-editable, per-language customization system (texts, buttons, stickers, reactions, premium emoji, colours, layout, feature switches) into any Telegram bot, in the bot and in a web panel.
- **bot-builder-style**: one builder's working style and product taste (Persian replies, features off by default, bot + web panel + 🎨 parity, exact money handling, test before done, beginner-friendly release notes, git rules).

Install: copy `skills/*` to `~/.claude/skills/` (Claude Code), upload `dist/*.skill` (Claude.ai), drop `AGENTS.md` / `GEMINI.md` / `.github/copilot-instructions.md` into a project (Codex, Cursor, Gemini CLI, Copilot), or paste `prompts/short-instructions.md` into ChatGPT or Gemini. Edit only `skills/`, then run `./build.sh`.

</details>
