# 💸 ExpenseTracker — Personal Finance App

Auto-reads bank notifications and SMS to track your debits and credits.  
Built with **React Native (Expo)** — compile to APK yourself.

---

## ✨ Features

- 📲 **Auto notification reader** — reads ICICI, SBI, HDFC, Axis, PhonePe, GPay alerts in real-time
- 📨 **SMS paste parser** — paste any bank SMS and it extracts amount, merchant, category automatically
- ✍️ **Manual entry** — add transactions by hand
- 📊 **Dashboard** — monthly debit/credit summary, top spending categories
- 📈 **Analytics** — 6-month trend chart, category breakdown
- 🔍 **Search & filter** — find any transaction by merchant, bank, or category
- 🔒 **100% offline** — all data stored locally on device, nothing leaves your phone
- 🗑️ **Long press to delete** any transaction

---

## 🏦 Supported Banks & Parsers

| Bank / App     | Support Level     |
|----------------|-------------------|
| ICICI Bank     | ✅ Full            |
| SBI            | ✅ Full            |
| HDFC Bank      | ✅ Full            |
| Axis Bank      | ✅ Full            |
| PhonePe        | ✅ UPI             |
| Google Pay     | ✅ UPI             |
| Paytm          | ✅ UPI             |
| Kotak Bank     | ✅ Full            |
| PNB / BOB      | ⚡ Partial         |

---

## 🚀 Setup & Build Instructions

### Prerequisites
- Node.js 18+
- Expo CLI: `npm install -g expo-cli eas-cli`
- An [Expo account](https://expo.dev) (free)

### 1. Install dependencies

```bash
cd ExpenseTracker
npm install
```

### 2. Add missing navigation packages

```bash
npm install @react-navigation/native @react-navigation/bottom-tabs @react-navigation/native-stack react-native-screens react-native-safe-area-context
```

### 3. Run on your phone (Expo Go)

```bash
npx expo start
```
Scan the QR code with **Expo Go** app. Most features work except background SMS reading (needs a full APK).

### 4. Build APK (for full functionality)

```bash
# Login to Expo
eas login

# Configure your project
eas build:configure

# Build preview APK (free, ~10 min on Expo servers)
eas build --platform android --profile preview
```

After build completes, download the `.apk` from the Expo dashboard and install on your phone.

---

## ⚠️ Android Notification Listener Setup

After installing the APK:

1. Open **Settings** → **Apps** → **ExpenseTracker**
2. Tap **Permissions** → Enable **Notifications**
3. Go to **Settings** → **Notifications** → **Notification Access**
4. Enable **ExpenseTracker**

This allows the app to read bank notification text in the background.

---

## 📂 Project Structure

```
ExpenseTracker/
├── App.tsx                         # Root with navigation
├── src/
│   ├── screens/
│   │   ├── HomeScreen.tsx          # Dashboard
│   │   ├── TransactionsScreen.tsx  # History + search
│   │   ├── AnalyticsScreen.tsx     # Charts
│   │   ├── AddTransactionScreen.tsx# Manual + SMS paste
│   │   └── SettingsScreen.tsx      # Permissions + data
│   ├── hooks/
│   │   └── useNotificationListener.ts  # Real-time notification hook
│   └── utils/
│       ├── smsParser.ts            # SMS/notification parser (ICICI, SBI, etc.)
│       ├── storage.ts              # AsyncStorage CRUD + summaries
│       └── theme.ts                # Colors, category icons/colors
├── app.json                        # Expo config + Android permissions
├── eas.json                        # EAS build profiles
└── package.json
```

---

## 💡 Tips

- **Long press** any transaction to delete it
- Use **Settings → Load Sample Data** to test the app with real-looking bank messages
- The ← → arrows on the home screen let you browse past months
- All amounts are stored in INR (₹)

---

Made with ❤️ for Pantho
