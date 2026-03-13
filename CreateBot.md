# CreateBot — Bot Yaratish Qo‘llanmasi

Ushbu hujjat **Virogram ichida bot yaratish jarayoni**ni ko‘rsatadi.

> **Eslatma:** Bu yerda sizga faqat `Create Bot` ichida bot yaratish va u bilan ishlash yo‘riqnomasi beriladi

---

## ✅ Boshlanish: @CreateBot

1. `@CreateBot` ni toping va unga kiriting.
2. **`/new`** yoki **`/newbot`** ni yozing.
3. Bot nomini kiriting.
4. Bot uchun username kiriting (masalan: `my_cool_bot`).
5. Sizga **bot tokeni** (masalan: `BOT_TOKEN_...`) beriladi.

> Ushbu tokenni **hech kim bilan baham ko‘rmang** — u botni boshqarish uchun ishlatiladi.

---

## ✅ 2-qadam: Kodni tayyorlash (bot.ts)

`Create Bot` ichida **/run** buyrug‘i mavjud. U tugmasini bosing, so‘ng **bot.ts** faylini yuklang.

Fayl ichida tokeningiz bo‘lishi kerak. Misol:

```ts
const MY_BOT_TOKEN = 'YOUR_TOKEN_HERE';

registerBot(MY_BOT_TOKEN, async (message, bot, user, sharedContactId, msg) => {
  const text = message.toLowerCase().trim();

  if (text === '/start') {
    return {
      type: 'new',
      text: `Salom, ${user.name}! Bot ishga tushdi.`,
      actions: [
        { label: 'Help', action: '/help' },
      ]
    };
  }

  if (text === '/help') {
    return {
      text: 'Buyruqlar: /start, /help, /ping',
      actions: [{ label: 'Ping', action: '/ping' }]
    };
  }

  if (text === '/ping') {
    return { text: 'Pong! 🏓' };
  }

  return { text: 'Noma’lum buyruq. /help deb yozing.' };
});
```

---

## ✅ 3-qadam: Botni ishga tushirish

1. `/run` tugmasini bosib, tayyor bot.ts faylini yuklang.
2. Agar hammasi to‘g‘ri bo‘lsa, botni **ishga tushadi** va sizga xabar yuboradi.
3. Agar kodda xato bo‘lsa yoki xavfsizlik tekshiruvi (masalan, `eval`, `fs`, `process`) o‘tmasa, bot xatolik haqida xabar beradi.

---

## ✅ 4-qadam: Bot bilan muloqot qilish (sinov)

- `@CreateBot` orqali botni tanlang.
- Botga **/start** yoki boshqa buyruqlar yuboring.
- Agar bot tayyor bo‘lsa, u sizga javob beradi.

> Agar bot javob bermasa, **`/run`** orqali qayta yuklash va tokenni to‘g‘ri ishlatayotganingizni tekshirib ko‘ring.

---

## 📌 Nima uchun token muhim?

- Bu token orqali sistem botni aniqlaydi.
- Tokenni **hech qachon ochiq joyga** (public repo, forum va h.k.) qo‘ymang.
- Agar token yo‘qolsa, botni qayta yaratib tokenni yangilang.

---

## 💡 Qo‘shimcha eslatma

Agar bot ishlamasa yoki sizga xatolik (momo) kelib qolsa, **`Create Bot` ichida xato xabarini** tekshiring. U yerda nima noto‘g‘ri ekanini ko‘rsatadi (masalan: token noto‘g‘ri, /run tugmasidan oldin kod to‘g‘ri yozilmagan).
