<div dir="rtl">

# 🎨 Skill UI/UX — سلیقهٔ طراحی و اسکیل‌های ساخت ربات

این ریپو دو تا **اسکیل** داره. اسکیل یعنی یک دستورالعمل آماده که به هوش مصنوعی می‌دی تا هر بار که برات ربات می‌سازه، از همون اول همون‌طوری بسازه که دوست داری؛ دیگه لازم نیست هر بار همه‌چیز رو از اول توضیح بدی.

این دو اسکیل از تجربهٔ ساخت ربات فروش **[Ciro](https://github.com/Alfred-1313/Ciro)** درآمدن. ولی به هیچ زبان برنامه‌نویسی و هیچ ربات خاصی بسته نیستن و روی هر ربات تلگرامی جواب می‌دن: PHP، Python، Node.js، Go و بقیه.

## 🧭 سلیقهٔ من در پروژه‌های بعدی

اسکیل حالا یک **پروفایل طراحی مستند از Ciro** هم دارد: تم شب زغالی با تأکید بنفش،
نوار کناری شناور و شیشه‌ای، کارت‌های ساده، وزیرمتن، طراحی درست موبایل، حرکت‌های کوتاه و
ذخیره بدون پرش صفحه. [خلاصهٔ فارسی سلیقه](docs/taste-profile.fa.md) و
[جزئیات همراه با شواهد کد](skills/bot-builder-style/references/design-profile.md) را ببین.

در پروژهٔ تازه، سلیقهٔ مرتبط استفاده می‌شود؛ قابلیت‌های مخصوص ربات فروش و VPN به یک سایت
یا داشبورد مستقل تحمیل نمی‌شوند. رنگ و سبک جدیدی که درخواست کنی بر این پیش‌فرض‌ها اولویت دارد.
برای انتقال فقط سلیقهٔ طراحی، `bot-builder-style`؛ برای ساخت سیستم شخصی‌سازی ربات، هر دو اسکیل را استفاده کن.

این ارتقا ویرایشگر متن فعلی، اعتبارسنجی HTML، جداسازی خرید عادی/عمده و وضعیت/تحویل،
شناسهٔ ثابت دکمه‌ها و حالت مقاله با بررسی پشتیبانی و خروجی جایگزین را هم پوشش می‌دهد.
تحلیل بر اساس کد بوده؛ Ciro برای این ارتقا تغییر نکرده است.

---

## 📦 داخلش چیه؟

| اسکیل | کارش چیه |
|---|---|
| 🎨 **`telegram-bot-customization`** | یاد می‌ده سیستم «🎨 شخصی‌سازی» رو توی هر ربات بسازی: ادمین بتونه **هر متن، دکمه، استیکر، ری‌اکشن، ایموجی پریمیوم، رنگ دکمه، چیدمان و کلید روشن/خاموش** رو جدا برای هر زبان عوض کنه؛ هم از داخل ربات، هم از پنل وب. اگه ربات چند **مسیر** داشته باشه (مثلاً دانلودر اینستاگرام و تیک‌تاک و توییتر، یا بخش‌های مختلف یک فروشگاه)، کپشن و دکمه‌های **هر مسیر جدا** شخصی‌سازی می‌شن. بخش **«📊 آمار ربات»** رو هم مثل Ciro می‌سازه (آمار کلی، امروز و دیروز و ماه، تاریخ دلخواه، هر زبان و هر پنل جدا، و داشبورد پنل وب). **«گزارش وضعیت»** رو هم مثل Ciro می‌سازه (گروه گزارش با تاپیک برای هر نوع گزارش، گزارش شبانه، صفحهٔ وضعیت کرون‌ها و هشدار قطعی پنل‌ها). قابلیت **«🔄 آپدیت ربات»** رو هم دقیقاً مثل Ciro می‌سازه: آپدیت با یک دکمه از داخل ربات، بکاپ قبل از آپدیت، دست‌نخوردن تنظیمات و دیتابیس، برگشت خودکار اگه خراب شد، برگشت به نسخهٔ قبلی از داخل ربات، و اعلان «تازه‌ها» به ادمین‌ها. |
| 🧭 **`bot-builder-style`** | سلیقه و روش کار خودت، همراه با پروفایل بصری برای ربات، داشبورد و وب‌اپ: تم شب، موبایل، فونت و آیکون، رفتار ذخیره و بازخورد، جواب فارسی و روان، قابلیت جدید پیش‌فرض خاموش، هر قابلیت هم توی ربات و هم پنل وب و هم 🎨، پرداخت دقیق و بدون دوبار کسر یا دوبار ساخت، تست قبل از تحویل، یادداشت «تازه‌ها» برای ادمین تازه‌کار، و قوانین گیت. |

### ساختار فایل‌ها

<div dir="ltr">

```
skills/
├── telegram-bot-customization/
│   ├── SKILL.md                  ← اصل اسکیل
│   └── references/
│       ├── data-model.md         ← شکل ذخیرهٔ متن‌ها، دکمه‌ها، استیکرها و تنظیمات
│       ├── admin-screens.md      ← صفحه‌های ادمین، یکی‌یکی، با نمونهٔ متن
│       ├── web-panel.md          ← صفحه‌های پنل وب، ذخیره و موبایل
│       ├── content-editing.md    ← متن فعلی، HTML، مقاله و زمینه‌های مستقل
│       ├── bot-stats.md          ← بخش «📊 آمار ربات» و داشبورد پنل وب (مثل Ciro)
│       ├── status-reports.md     ← «گزارش وضعیت»: گروه گزارش، گزارش شبانه، کرون‌ها، هشدار قطعی
│       ├── self-update.md        ← قابلیت «🔄 آپدیت ربات»، بکاپ، برگشت و «تازه‌ها» (مثل Ciro)
│       └── checklist.md          ← چک‌لیست «تموم شد»
└── bot-builder-style/
    ├── SKILL.md
    └── references/design-profile.md ← سلیقهٔ قابل انتقال با شواهد Ciro
dist/                             ← فایل‌های آماده برای نصب روی Claude.ai
AGENTS.md                         ← برای Codex، Cursor، Windsurf، Aider و …
GEMINI.md                         ← برای Gemini CLI
.github/copilot-instructions.md   ← برای GitHub Copilot
prompts/short-instructions.md     ← نسخهٔ کوتاه برای ChatGPT و Gemini (وب)
docs/taste-profile.fa.md           ← خلاصهٔ فارسی سلیقه
build.sh                          ← دستورها و بسته‌های dist را از روی اسکیل‌ها می‌سازد
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
- «به این پروژه قابلیت آپدیت از داخل ربات اضافه کن، مثل Ciro.»
- «یه بخش 📊 آمار ربات مثل Ciro اضافه کن.»
- «گزارش وضعیت مثل Ciro بذار: گروه گزارش با تاپیک‌ها و گزارش شبانه.»
- «یه ربات دانلودر اینستاگرام، تیک‌تاک و توییتر بساز که کپشن و دکمه‌های هر کدوم جدا قابل تغییر باشه.»

هوش مصنوعی خودش این کارها رو انجام می‌ده:
- متن‌ها و دکمه‌ها رو قابل شخصی‌سازی می‌سازه.
- قابلیت جدید رو پیش‌فرض خاموش می‌ذاره.
- قابلیت رو هم به پنل وب اضافه می‌کنه.
- قبل از تحویل تست می‌کنه.
- آخر کار یه یادداشت «تازه‌ها» با مسیر منو برات می‌نویسه.

---

## ✏️ ویرایش اسکیل‌ها

1. منبع دستورها فایل‌های داخل `skills/` است؛ نسخه‌های تولیدشده را دستی ویرایش نکن. برای تغییر سلیقه، `skills/bot-builder-style/references/design-profile.md` را هم می‌توانی ویرایش کنی.
2. بعد این دستور رو اجرا کن:

<div dir="ltr">

```bash
./build.sh
```

</div>

این دستور با Bash و Python 3، فایل‌های `AGENTS.md`، `GEMINI.md` و `.github/copilot-instructions.md` و هر دو بستهٔ `dist/*.skill` را از روی اسکیل‌ها دوباره می‌سازد. منابع جدید هم داخل خروجی می‌آیند؛ بسته‌ها به مرحلهٔ zip دستی نیاز ندارند.

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

Two portable AI skills, including a source-evidenced design profile, extracted from building the [Ciro](https://github.com/Alfred-1313/Ciro) Telegram shop bot:

- **telegram-bot-customization**: build a full admin-editable, per-language customization system (texts, buttons, stickers, reactions, premium emoji, colours, layout, feature switches) into any Telegram bot, in the bot and in a web panel; plus a self-update feature built like Ciro's (update button, snapshot, automatic rollback, what's-new announcements).
- **bot-builder-style**: Alfred's portable visual profile (night/charcoal/violet, restrained surfaces, Persian typography, mobile layouts, continuity on save), with pinned Ciro source evidence, plus working style and product taste (Persian replies, features off by default, bot + web panel + 🎨 parity, exact money handling, test before done, beginner-friendly release notes, git rules).

Install: copy `skills/*` to `~/.claude/skills/` (Claude Code), upload `dist/*.skill` (Claude.ai), drop `AGENTS.md` / `GEMINI.md` / `.github/copilot-instructions.md` into a project (Codex, Cursor, Gemini CLI, Copilot), or paste `prompts/short-instructions.md` into ChatGPT or Gemini. Edit instructions under `skills/`, then run `./build.sh` (Bash + Python 3) to regenerate all instruction files and both installable archives. Apply only relevant product modules; explicit user/project requirements override inferred defaults.

</details>
