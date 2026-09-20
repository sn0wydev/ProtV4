# VoidGifts: redesigned, drop-in project

Everything here replaces the matching files in your repo. Keep your own `status.json` and `tonconnect-manifest.json`.

    index.html  styles.css  script.js   the app (new design)
    tos.html    privacy.html            new: Settings → Terms / Privacy used to 404
    assets/                             your 44 Lottie + SVG files (from sn0wydev/ProtV3)

## Before you ship: set these

1. **script.js → CONFIG.SUBSCRIPTION_CHANNEL_USERNAME / SUBSCRIPTION_CHANNEL_URL**
   Still the `@telegramchannelname` placeholders. The subscribe popup shows this name.
2. **script.js → CONFIG.SUPPORT_URL**
   Where "Contact Support" opens. Currently your channel; point it at a support account.
3. **tos.html and privacy.html**
   Every highlighted `[placeholder]` is something only you can fill in or confirm. Have them reviewed.
4. **assets/giftGift.json**
   Not in your repo, so the Gift Box prize has no animation. The app now falls back to Gift.svg.

## What changed in script.js (your logic is untouched apart from this)

- Wheel highlight colours: blue → gold (daily), purple → pink (void)
- Toast: new font, sits above the bottom nav
- FIX: `Object.assign(el, { dataset })` threw in strict mode (pending-NFT badges), in two places
- "Live gifts" text: `▸` removed; new `liveGiftsEmpty` string (6 languages) + `data-i18n-empty` hook
- NEW: Contact Support handler; every `t.me` link opens inside Telegram
- NEW: missing `gift*.json` Lottie files fall back to their static SVG
- FIX: the promo card's `href="#"` link fired popstate and bounced users to Home
