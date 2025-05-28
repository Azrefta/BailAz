# <div align="center">✨ BailAz - TypeScript/JavaScript WhatsApp Web API ✨</div>

<div align="center">
  <img src="https://i.pinimg.com/736x/dd/df/ff/dddfff153f1819fce8aa07ccad5582ea.jpg" width="100%">
</div>

---

## 🔔 Important Note

This is a **forked and enhanced version** of the original Baileys repository, which was once removed and later maintained by [WhiskeySockets](https://github.com/WhiskeySockets).

From that foundation, I've implemented numerous **new features**, **UI improvements**, and **functionality upgrades** that go far beyond what was previously available — designed to provide developers a smoother and more flexible experience.

---

## ⚙️ Installation

**Via `package.json`:**

```json
"dependencies": {
  "baileys": "github:nstar-y/bail"
}
````

**Or install directly via terminal:**

```bash
npm install baileys@github:nstar-y/bail
```

**Then import into your project:**

```ts
// For ESM
import makeWASocket from 'baileys'
```

```js
// For CommonJS
const { default: makeWASocket } = require('baileys')
```

---

## ✨ New Features & Improvements

* 🧩 **Send Messages to Channels**
* 🧠 **AI Icon Support for Chat Messages**
* 📸 **Original-Size Profile Picture Uploads**
* 🧾 **Support for Button and Interactive Messages**
* 🔐 **Customizable Pairing Code**
* 🔧 **Improved Libsignal Logs Cleanup**

More enhancements are planned in future updates!

---

## 🚀 Feature Showcase

### 📣 Newsletter Features

```ts
const metadata = await sock.newsletterMetadata("invite", "xxxxx")
// or
const metadata = await sock.newsletterMetadata("jid", "abcd@newsletter")
```

* Update Description:

```ts
await sock.newsletterUpdateDescription("abcd@newsletter", "New Description")
```

* Update Name:

```ts
await sock.newsletterUpdateName("abcd@newsletter", "New Name")
```

* Set / Remove Picture:

```ts
await sock.newsletterUpdatePicture("abcd@newsletter", buffer)
await sock.newsletterRemovePicture("abcd@newsletter")
```

* Mute / Unmute:

```ts
await sock.newsletterMute("abcd@newsletter")
await sock.newsletterUnmute("abcd@newsletter")
```

* Create / Delete / Follow / Unfollow:

```ts
const meta = await sock.newsletterCreate("Name", "Description")
await sock.newsletterDelete("abcd@newsletter")
await sock.newsletterFollow("abcd@newsletter")
await sock.newsletterUnfollow("abcd@newsletter")
```

* React to Message:

```ts
await sock.newsletterReactMessage("abcd@newsletter", "175", "🥳")
```

---

### 🖱️ Button & Interactive Messages

#### Text Buttons

```ts
const buttons = [
  { buttonId: 'id1', buttonText: { displayText: 'Button 1' }, type: 1 },
  { buttonId: 'id2', buttonText: { displayText: 'Button 2' }, type: 1 }
]

const msg = {
  text: "Here's a button message!",
  footer: 'Powered by BailAz',
  buttons,
  headerType: 1,
  viewOnce: true
}

await sock.sendMessage(id, msg)
```

#### Button with Media (Image/Video)

```ts
const msg = {
  image: { url: "https://example.com/image.jpg" }, // or video
  caption: "Message with image!",
  footer: 'BailAz Magic',
  buttons,
  headerType: 1,
  viewOnce: true
}

await sock.sendMessage(id, msg)
```

#### Interactive Message (Quick Reply, URL, Copy)

```ts
const interactiveButtons = [
  {
    name: "quick_reply",
    buttonParamsJson: JSON.stringify({ display_text: "Quick Reply", id: "ID" })
  },
  {
    name: "cta_url",
    buttonParamsJson: JSON.stringify({ display_text: "Visit Site", url: "https://example.com" })
  },
  {
    name: "cta_copy",
    buttonParamsJson: JSON.stringify({ display_text: "Copy Code", id: "12345", copy_code: "12345" })
  }
]

const message = {
  text: "Check this out!",
  title: "Cool Title",
  footer: "This is the footer",
  interactiveButtons
}

await sock.sendMessage(id, message)
```

---

### 🤖 AI Chat Icon

Want to show your message came from an AI? Just add this:

```ts
await sock.sendMessage(id, { text: "I'm an AI!", ai: true })
```

---

### 🔐 Custom Pairing Code

```ts
if (usePairingCode && !sock.authState.creds.registered) {
  const phoneNumber = await question('Enter your mobile number:\n')
  const custom = "NSTRCODE" // Must be exactly 8 alphanumeric characters
  const code = await sock.requestPairingCode(phoneNumber, custom)
  console.log(`Pairing code: ${code?.match(/.{1,4}/g)?.join('-') || code}`)
}
```

---

## 🤖 Official Bot

Meet **BRONYA RAND** — the official bot powered by BailAz!

<div align="center">
  <img src="https://i.pinimg.com/736x/ae/c5/e3/aec5e307938b583b61472f479f3f01fb.jpg" width="160" style="border-radius: 12px;">
</div>

---

## 🛠 Reporting Issues

Found a bug or have a feature request? Open an [issue here](https://github.com/nstar-y/Bail/issues) and let's improve together!

---

## 📝 Notes

Everything other than the modifications mentioned above remains the same as the original repository. You can check out the original repository at [WhiskeySockets](https://github.com/WhiskeySockets/Baileys)

> # [BailAz Repository](https://github.com/Azrefta/BailPatch)
