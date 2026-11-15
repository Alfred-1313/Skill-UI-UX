# Content editing, output capabilities and independent contexts

This extends the basic 🎨 system with preferences visible in Ciro's later editing flows.
Use the platform API/SDK version the target project actually supports; the source project is
evidence of taste, not documentation of what every Telegram deployment can send.

## 1. Edit the text that exists

Every caption editor opens with the **effective current text**, not just the factory default:

```
✏️ ویرایش کپشن — 🇮🇷 فارسی
📍 فقط برای خرید عادی ← موجودی کافی نیست
<blockquote>متن فعلی رو کپی کن، تغییرش بده و دوباره بفرست.
متغیرها: {need} کسری · {price} قیمت · {balance} موجودی</blockquote>
[copyable current source, with literal HTML tags escaped for display]
[📋 کپشن پیش‌فرض] [🔙 انصراف]
```

- Keep the raw source separate from the rendered preview. Escape source shown in a code
  block; do not execute it as the editor's own HTML. A preview uses representative values
  and never triggers a purchase, sends a customer message or overwrites settings.
- Accept Telegram entities (bold, code, quotes, custom emoji) as well as supported explicit
  markup. Preserve offsets correctly, including Telegram's UTF-16 entity offsets; slicing
  emoji with byte offsets corrupts the saved text. Test emoji at start, middle and end.
- Name the supported variables, their meaning and a small example next to the editor.
  Escape substituted user data according to its output context, not the entire trusted template.
- Validate server-side through the same validator for bot and web saves: balanced supported
  tags, allowed attributes, links and limits for the output type. On invalid HTML, reject the
  edit, name the error and keep the previous working value. Do not “save successfully” and
  wait for the customer send to fail.
- Missing optional variables get a clear warning. Missing required transactional data (amount,
  destination, invoice identity) must be corrected or explicitly reviewed before accepting a
  template that would hide it. Preserve existing overrides during validation/migration.

## 2. A message's type decides which controls exist

Declare output type and capabilities in the registry; both editors use them.

| Type | Editing behaviour |
|---|---|
| Full text message | supported formatting, variables, allowed extras; rich/article mode only if supported |
| Media caption | caption-specific length/format rules; no assumption of article support |
| Callback popup/alert | plain text, callback-specific limit (Ciro uses 200 characters); no article/sticker |
| Button label | plain label plus dedicated emoji fields; no message HTML or article control |
| Message fragment | preserves the containing message's contract; no independent sticker/article send |

Reactions only appear when there is an eligible target message and the API allows it.
Sticker support is explicit per item. An unavailable control has a short reason instead of
an editor that lets the admin save something the sender cannot use.

## 3. Optional rich/article presentation

Ciro exposes «📰 حالت مقاله» for eligible full messages. Carry the product idea where the
target API/SDK supports it, without inventing an API field or treating arbitrary web HTML as
Telegram HTML.

- Presentation mode is per `(language, path/context, message key)`, **off by default**.
  Both the bot and web editor expose the same setting. Legacy data means normal mode.
- Show only the supported rich tags/structures in that mode's help. Long readable content
  may use headings, paragraphs, lists, tables and images when the API actually supports them.
- Use a separate renderer with a normal-message fallback: headings become bold, lists become
  readable bullets, tables become labelled lines, images retain useful links. Keep variables,
  language, buttons and the meaning of the message; never let the message silently disappear.
- Retry in normal mode only for a definite unsupported-format response. An ambiguous network
  timeout is not proof the first message was rejected; blindly sending again can duplicate it.
- If the platform has no rich-message support, explain the limitation briefly and use the
  normal supported renderer. Do not create a broken switch to mimic the reference project.
- Turning rich mode off while its saved source contains rich-only tags asks the owner to
  simplify/reset it first, or explicitly accept a converted preview. Never discard their text.
- Resetting all settings for that message clears its rich mode as well as its text and extras.
  The item and every parent group reflect the 📰/customized state.

## 4. Identity, inheritance and previews

- Button identity is a stable ID in its **context**, not its current index or caption. Adding,
  renaming or rearranging buttons cannot move an override onto another action. Keep old
  index-based layouts readable through an explicit migration map.
- Separate `buy.single.confirm`, `buy.bulk.confirm`, `services.status`, `services.delivery`
  and each gateway's invoice/receipt/error states. Sharing a default does not share an override.
- When separating formerly shared settings, seed both new contexts from the old effective
  values so nothing unexpectedly changes; future edits/resets affect only the selected scope.
- Render the same effective defaults in the preview and runtime. A default-blue button is
  shown blue before the admin ever customizes it. Cycling colour starts at that effective
  value. “Default” and an explicitly chosen uncoloured style are distinct when needed.
- A plain emoji replaces the configured default/premium emoji; it is not appended beside it.
  Plain mode removes decorative emoji. Normal emoji can follow the supported side setting;
  a custom emoji icon follows the API's placement (Ciro notes one before the label), rather
  than promising free placement. Caption custom emoji are a separate text/entity mechanism.
- Gate colours/custom emoji by actual client/library capabilities; fallback preserves the
  readable label and its action. Do not retry an unrelated failed request as if it were a style issue.
- Let optional parts be hidden, but preserve a route out and a route forward. Ciro sometimes
  permits hiding a particular back/close button; the portable rule is **no dead ends**. Keep
  required navigation visible by default; allow hiding it only when another usable exit exists.
  If all number presets/step controls are hidden, keep manual input reachable, for example.
- Group badges aggregate text, buttons, layout, extras and presentation changes recursively.
  Reset/copy/apply-to-all name their scope; a bulk change confirms once and does not leak
  into another language or a context the admin did not select.

## 5. Review by behaviour

Check these cases using the target project's rig or focused fixtures:

1. Copy/edit/save a current custom caption with variables, nested formatting and custom emoji.
2. Submit invalid markup from bot and web: both explain it and retain the old working source.
3. Edit/reset normal purchase while bulk purchase stays unchanged; migrate a legacy shared override.
4. Render a default-coloured button, reorder/insert a button, replace an emoji and use plain mode.
5. Open an alert/fragment/media caption: incompatible controls are absent; limits are enforced.
6. If rich mode is implemented: per-language toggle, valid output, definite-unsupported fallback,
   mode-off guard and reset; distinguish that from an ambiguous network timeout.
7. Hide optional controls and verify a complete customer path remains. Parent badges and web
   preview must match the effective stored state, including explicitly false/empty overrides.
