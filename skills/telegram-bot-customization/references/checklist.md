# Done checklist for any customer-facing change

Copy this into your notes and tick it honestly.

- [ ] Every new customer text exists in **every** language file (no English left in Persian
      screens, no Persian in English ones).
- [ ] Admin-only texts are in the admin language file only.
- [ ] Each new text has a registry entry (label, key, group, section) and opens in 🎨 on every
      language tab; edit, sticker, reaction and reset work.
- [ ] New buttons go through the shared renderer and belong to a button group; rename, emoji,
      premium emoji, colour, hide and layout work; required navigation remains reachable.
- [ ] The new button shows up in 📐 layout and can be moved; stable IDs keep overrides on the
      right action after reorder/insertion, including migration from legacy indices.
- [ ] Caption editors show current copyable source, variables and supported formatting. Bot
      and web reject broken markup with the same error rules and retain the working text.
- [ ] Output capabilities fit the item type (message/caption/alert/fragment/button). Unsupported
      controls are absent. If rich mode is implemented, per-language scope, normal fallback,
      safe disable and reset are checked; no blind duplicate send on timeout.
- [ ] Normal/bulk purchase, status/delivery and gateway settings stay independent. Previews show
      real defaults, explicit false/empty overrides work, and parent badges include child changes.
- [ ] Texts and extras are resolved in the receiver's language (crons, admin actions, referrals).
- [ ] Every path (platform, feature, department…) is in the path registry and has its own 🎨
      group; its texts and buttons open and change without touching the other paths.
- [ ] Keys carry the path; the flow passes the path to every lookup, async messages included.
- [ ] Items that are really shared say so on screen ("🔗 مشترک بین …"), the rest say
      "📍 فقط برای …"; copy-from-path and apply-to-all work.
- [ ] Each path has its own per-language on/off switch.
- [ ] A new feature that sells or is used shows up in 📊 آمار ربات (count and sum, per
      language, per period) and on the web panel's dashboard.
- [ ] Its events are reported to the right topic of the report group, failures after payment
      to the error topic; it appears in the nightly report if it sells; its cron (if any)
      writes a heartbeat shown on «⏱ وضعیت کرون‌ها».
- [ ] A new feature has a switch, per language unless truly global, **off by default**.
- [ ] The web panel can see and change everything the bot can for this feature.
- [ ] Web saves preserve focus/scroll and refresh affected lists/counters. Pending, failed and
      successful states are distinct; rapid choices cannot persist out of order.
- [ ] Phone layouts fit; tables/cards keep labels and vertical touch scrolling works. Persian
      typography and mixed LTR data, keyboard focus and reduced-motion mode are checked.
- [ ] Stale buttons from old messages answer with a clear alert, never a PHP/Python error.
- [ ] Money paths are idempotent: a second tap, a second approval or a retried webhook never
      charges, credits or builds twice; state is saved right after the external call succeeds.
- [ ] Tested on a local rig: fake Telegram API that logs calls, fake panel/payment APIs, a real
      database; menus crawled for errors in the log.
- [ ] A what's-new entry for the admin, beginner friendly, with the menu path and the default.
