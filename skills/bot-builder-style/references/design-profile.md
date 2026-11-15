# Portable design profile — Alfred / Ciro

Use this profile when making UI/UX decisions for this owner in a new bot, dashboard, web
application or customer page. It records preferences inferred from Ciro's source, not a claim
that every line of that project is intentional or bug-free. An explicit request, an existing
project's requirements and platform capabilities take precedence over these defaults.

## Scope: carry the taste, adapt the product

- Carry Persian clarity, deliberate typography, restrained surfaces, visible feedback,
  reversible customization and continuity through a flow into other projects.
- For a bot with an existing web panel, keep its administration and customization in parity.
  A standalone website does not need a Telegram bot, wallet, payment gateway, cron or updater
  just because Ciro has one. Add product modules only when the task calls for them.
- Preserve the target project's framework, authentication and data model. Ciro's PHP file
  names, database fields, VPN panels and brand are examples, not dependencies.
- Dark «شب» and purple are a strong starting point for a new admin interface. Customer pages
  can have a different identity; Ciro itself supports multiple themes and customer designs.
  Keep an existing theme choice, and honour a new colour or light-mode request immediately.

## Visual defaults

The current reference is **«شب» (night)**: charcoal scenery, a floating glass sidebar, a
violet accent and calm opaque content. Avoid translating “glass” into blur on every card.

| Role | Ciro night value | How to use it elsewhere |
|---|---|---|
| Page background | `#0f0f13` | charcoal foundation |
| Content card | `#17181f` | opaque reading surface |
| Raised surface | `#1b1c24` | secondary panels and mobile rows |
| Card border | `#272833` | one quiet hairline |
| Accent / hover | `#ba4dff` / `#cf8aff` | selection, focus and navigation |
| Filled action | `#9b36e0` | distinct from the brighter accent line |
| Main / secondary text | `#f8f7fc` / `#d6d3e0` | clear hierarchy |
| Muted text | `#93949f` | helper text; verify contrast at its actual size |
| Success / danger / warning | `#4ade80` / `#fb7185` / `#fbbf24` | status meaning, accompanied by words or icons |

These are source values, not a blanket accessibility certification. Check actual text/fill
combinations, focus visibility and disabled states; adjust tokens where needed.

- Use semantic tokens for every theme. The night theme has subtle ribbons and grain behind
  the shell; these must remain decorative, cheap to render and clear of reading surfaces.
- Rounded geometry is consistent: about 10px for fields/buttons, 12–16px for rows/cards,
  20px for dialogs and 32px for the floating desktop sidebar. Adapt to the component size.
- Cards have a tone step and one border, usually no shadow. Shadows and translucency belong
  mainly to floating navigation, dialogs and toasts. Limit gradients to accent/decorative roles.
- Headline metrics form a connected strip separated by thin rules. Pair a quiet label with
  a larger number and a short unit; avoid a dashboard made entirely of unrelated bright tiles.
- Use one family of SVG outline icons for the panel's navigation, headings and controls.
  Keep real emoji, custom emoji and flags when they are the customer's editable bot content.
  Do not strip them from previews in the name of making the admin panel consistent.
- Empty, loading, invalid, pending, successful and failed states are designed screens too:
  a short explanation, a useful next action and a restrained icon are usually enough.

## Persian reading and mixed-direction data

- Persian screens use RTL and Vazirmatn, preferably served locally with a system fallback.
  Use natural Persian labels and short help next to the setting it explains.
- Do not apply letter spacing to joined Persian/Arabic script. Use weight, size and space
  between components for hierarchy. Table headers stay quiet and readable.
- Use tabular digits for comparable quantities. Isolate IDs, `@handles`, URLs and code as LTR
  inside RTL text (for example `bdi` / `dir="ltr"`); allow copying their real value unchanged.
- Dates, amounts and currencies are explicit. Persian date pickers can show Jalali and
  Gregorian together; keep the chosen calendar and the product's configured timezone.
- English customer screens use their proper language and direction. Do not inherit RTL
  merely because the owner speaks Persian. Admin-only screens keep the project's admin language.

## Navigation and mobile layout

- Desktop: a floating right sidebar with grouped sections, an obvious active location,
  collapse control and menu search (`Ctrl/⌘ K`); collapsed icons still have accessible labels
  and tooltips. Reuse the page's icon in its title.
- Mobile: a right drawer and a small bottom bar for frequent destinations when useful.
  Respect safe-area insets and leave room below content. A moving selection marker is an
  optional detail, never a reason to delay access or hide the destination's name.
- Forms stack; dialogs can become bottom sheets. Keep the principal action reachable.
  The page itself must fit a narrow phone. Prefer labelled row cards for management lists;
  genuinely wide editors may scroll inside their own wrapper without trapping vertical scroll.
- Inputs on touch devices should be at least 16px to avoid unintended browser zoom.
  Give icon controls accessible names, visible keyboard focus and comfortable touch targets.
- Lists keep search, status, language, sorting and date filters together. Preserve their
  state in the URL, compose them with paging, and make user IDs lead to the user's profile.

## Feedback and motion

- Saving normally keeps scroll, focus, open section and chosen language. Update the edited
  form **and** any affected list, metric or preview. Do not show an old list after a successful save.
- Choices respond immediately; show pending/saved/failed distinctly. A failed write must not
  leave an optimistic selection looking saved. Text editing has an explicit save action;
  safe choices can autosave. Serialize rapid choices so an old reply cannot win.
- Prefer one compact result toast near the bottom over a large success block that shifts the
  page. A save button can briefly become a tick after confirmed success. Keep errors readable
  and preserve the unsaved text so the owner can correct or retry it.
- Default motion: roughly 140–150ms for feedback, 220–320ms for arrivals, with ease-out;
  prefer opacity/transform. Sidebar/drawer motion can be longer when it clarifies navigation.
  Avoid lifting every hover target, perpetual pulsing statuses or replaying entrance motion
  after each save. Any counter animation is brief and occasional, not a live-data effect.
- `prefers-reduced-motion` gets the final state directly. Functionality, status and navigation
  remain complete with motion disabled. Hover treatments apply only where hover exists.

## Customization should feel complete

- Scope is visible: selected language, path, message type and what is shared. Normal versus
  bulk purchases, delivery versus status messages, and different gateways can look alike today
  but need independent overrides tomorrow.
- Show the actual current text/name/colour before editing, a copyable source, useful variables,
  a preview, and reset to the real default. Never make the owner reconstruct an existing caption.
- Parent groups reflect changes in children, including button-only changes and rich mode.
  “Customized” is computed from overrides; it is not a second flag that can go stale.
- Layout and delivery are product choices too: message parts, ordering, visibility and
  supported output formats. Keep a usable path even when optional parts are hidden.
- Live previews are for experimenting before saving. Reserve space for unsaved-state labels
  so the layout does not jump during dragging. Always preserve a required primary action.
- A confirmed action gets a clear result. A plain switch toggles once without an extra
  question; destructive resets/restores explain the scope and ask once before execution.

## Evidence and confidence

Reviewed source snapshot:
[`Alfred-1313/Ciro@8b892d932be651c29ea3f17642129920d10eca1e`](https://github.com/Alfred-1313/Ciro/tree/8b892d932be651c29ea3f17642129920d10eca1e).
These are source observations, not a claim of having run the live bot or tested its production UI.

| Evidence in that snapshot | Observation | Transfer |
|---|---|---|
| [`panel/css/shab.css`](https://github.com/Alfred-1313/Ciro/blob/8b892d932be651c29ea3f17642129920d10eca1e/panel/css/shab.css), [`panel/js/theme-init.js`](https://github.com/Alfred-1313/Ciro/blob/8b892d932be651c29ea3f17642129920d10eca1e/panel/js/theme-init.js) | current default is night; opaque cards, glass sidebar, purple, themes, touch and motion refinements | strong visual starting point, not mandatory brand colours |
| [`panel/inc/layout_head.php`](https://github.com/Alfred-1313/Ciro/blob/8b892d932be651c29ea3f17642129920d10eca1e/panel/inc/layout_head.php), [`panel/js/app.js`](https://github.com/Alfred-1313/Ciro/blob/8b892d932be651c29ea3f17642129920d10eca1e/panel/js/app.js) | grouped searchable/collapsible navigation and page identity | strong navigation preference |
| [`panel/js/ajaxform.js`](https://github.com/Alfred-1313/Ciro/blob/8b892d932be651c29ea3f17642129920d10eca1e/panel/js/ajaxform.js), [`panel/js/ui.js`](https://github.com/Alfred-1313/Ciro/blob/8b892d932be651c29ea3f17642129920d10eca1e/panel/js/ui.js) | quiet background saves, focus/scroll continuity, fresh lists, toasts and small confirmations | strong interaction preference; copy the outcome, improve failure handling as needed |
| [`panel/menu.php`](https://github.com/Alfred-1313/Ciro/blob/8b892d932be651c29ea3f17642129920d10eca1e/panel/menu.php), [`panel/looks.php`](https://github.com/Alfred-1313/Ciro/blob/8b892d932be651c29ea3f17642129920d10eca1e/panel/looks.php), [`panel/svclook.php`](https://github.com/Alfred-1313/Ciro/blob/8b892d932be651c29ea3f17642129920d10eca1e/panel/svclook.php) | separate contexts, stable button identities, editable layout/delivery | strong customization preference; exact settings depend on the product |
| [`panel/bottext.php`](https://github.com/Alfred-1313/Ciro/blob/8b892d932be651c29ea3f17642129920d10eca1e/panel/bottext.php), [`whatsnew.php`](https://github.com/Alfred-1313/Ciro/blob/8b892d932be651c29ea3f17642129920d10eca1e/whatsnew.php) entries 87–89 | current-copy editing, validation, per-message rich mode with fallback, precise release paths | strong editing preference; advanced Telegram formats need capability checks |
| [`panel/inc/daterange.php`](https://github.com/Alfred-1313/Ciro/blob/8b892d932be651c29ea3f17642129920d10eca1e/panel/inc/daterange.php), [`panel/users.php`](https://github.com/Alfred-1313/Ciro/blob/8b892d932be651c29ea3f17642129920d10eca1e/panel/users.php) | composable date filters and direct profile access | strong management UX preference |

Keep observed choices separate from engineering recommendations. For example, explicit save
failure recovery and contrast checks above make the preference reliable; their presence here
does not assert that Ciro already implements every case perfectly. Do not copy its bugs or
silently replace a different project's choices with Ciro's implementation.
