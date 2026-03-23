# 🏥 MedBuddy — The AI That Sits Between a Patient & Confusion

> **IAR Udaan Hackathon 2026** | Full-stack AI Medical App

[![Next.js](https://img.shields.io/badge/Next.js-14-black)](https://nextjs.org)
[![TypeScript](https://img.shields.io/badge/TypeScript-5-blue)](https://typescriptlang.org)
[![Claude](https://img.shields.io/badge/Claude-3.5%20Sonnet-orange)](https://anthropic.com)
[![Gemini](https://img.shields.io/badge/Gemini-1.5%20Flash-blue)](https://ai.google.dev)

---

## 🎯 What is MedBuddy?

MedBuddy is an AI-powered prescription simplification app that:
- **Reads** doctor handwriting via Gemini Vision OCR
- **Simplifies** every medicine using Claude 3.5 Sonnet
- **Translates** to English, Hindi, or Gujarati instantly
- **Never lets you miss a dose** with family reminders
- **Explains side effects** in color-coded severity levels

---

## 🚀 Quick Start

### 1. Clone & Install

```bash
git clone <your-repo>
cd medbuddy
npm install
```

### 2. Set up API Keys

```bash
cp .env.example .env.local
# Edit .env.local with your keys:
# GEMINI_API_KEY=...
# ANTHROPIC_API_KEY=...
```

Get your keys:
- **Gemini**: https://aistudio.google.com/app/apikey (free tier available)
- **Anthropic**: https://console.anthropic.com/settings/keys

### 3. Run Development Server

```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000)

---

## 🏗️ Project Structure

```
medbuddy/
├── app/
│   ├── page.tsx              # Landing page
│   ├── dashboard/page.tsx    # Main dashboard
│   ├── api/
│   │   ├── process/route.ts  # Gemini OCR + Claude simplify
│   │   └── translate/route.ts # Re-run Claude with new language
│   └── globals.css
├── components/
│   ├── UploadZone.tsx         # Drag & drop upload
│   ├── MedCard.tsx            # Printable health card
│   ├── ChemistTable.tsx       # Pharmacist-ready medicine list
│   ├── Timeline.tsx           # Morning/Afternoon/Evening doses
│   ├── ReminderPanel.tsx      # Family connect & reminders
│   ├── SideEffectsPanel.tsx   # Color-coded side effects
│   ├── TrustMap.tsx           # Original ↔ Simplified mapping
│   ├── LabReport.tsx          # Lab test values
│   ├── DoctorQuestions.tsx    # AI-generated questions
│   ├── FridgeMagnet.tsx       # Printable fridge reminder
│   ├── HistoryPanel.tsx       # Multi-prescription history
│   ├── PanicButton.tsx        # 2AM emergency button
│   ├── LanguageToggle.tsx     # EN/HI/GU switcher
│   ├── VoiceButton.tsx        # "Sunao Mujhe" speech
│   ├── ConfusedChat.tsx       # RAG chat on document
│   └── Sidebar.tsx            # Navigation
├── lib/
│   ├── gemini.ts              # Gemini Vision OCR
│   ├── claude.ts              # Claude simplification
│   ├── prompts.ts             # All AI prompts
│   ├── types.ts               # TypeScript interfaces
│   └── utils.ts               # Utility functions
└── store/
    └── useMedStore.ts         # Zustand state management
```

---

## 🎬 Demo Flow for Judges

### Step 1: Landing Page
- Show the hero with feature highlights
- Click **"Upload Prescription Free"**

### Step 2: Upload a Prescription
- Drag & drop a prescription image (JPG/PNG) or PDF
- Or paste text directly
- Set: Age = 65, Language = Hindi, Mode = Elder, For = For Papa
- Click **"Simplify My Prescription"**
- Watch the dual-model pipeline: Gemini OCR → Claude simplification

### Step 3: Dashboard — Patient MedCard
- Show the beautiful digital health card
- Check off morning doses with confetti animation
- Show QR code generation
- Click **Download PDF**

### Step 4: Chemist Mode
- Super-clean table for the pharmacist
- Click **Copy for Chemist** — paste in WhatsApp
- Show barcode generation per medicine

### Step 5: Medicine Timeline
- Click **Timeline** tab
- Show ☀️ Morning → 🌤️ Afternoon → 🌙 Evening cards
- Tick a dose → confetti 🎉

### Step 6: Language Toggle
- Click **HI** (Hindi) in top-right
- Watch instant re-translation (Claude only, ~2s)
- Switch to **GU** (Gujarati)

### Step 7: Family Connect
- Click **Family** tab
- Enter a demo phone number → Connect
- Click "Simulate missed-dose SMS"
- Show: "Beta, Papa ne Metformin nahi liya abhi. Please check."
- Share on WhatsApp button

### Step 8: Side Effects Panel
- Show 🔴 red (call doctor) / 🟡 yellow / 🟢 green color coding

### Step 9: Extra Features
- **Trust Map**: Side-by-side original ↔ simplified
- **🔊 Sunao Mujhe**: Press voice button — hears prescription in Hindi
- **Fridge Magnet**: Click Print preview
- **Doctor Questions**: AI-generated questions to ask
- **2AM Panic Button** (bottom-right): Emergency contacts

### Step 10: "I'm Confused" Chat
- Click green chat bubble (bottom-right)
- Ask: "Can Papa take Metformin with food?"
- RAG responds based on current prescription only

---

## 🌐 Deploy to Vercel

```bash
# Install Vercel CLI
npm i -g vercel

# Deploy
vercel

# Set environment variables in Vercel dashboard:
# GEMINI_API_KEY
# ANTHROPIC_API_KEY
```

Or use the Vercel button:

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new)

**Important**: Set `maxDuration = 60` is already configured in API routes for long-running AI calls.

---

## 🔑 Key Technical Decisions

| Decision | Why |
|----------|-----|
| Gemini 1.5 Flash for OCR | Best-in-class vision model, handles Gujarati handwriting |
| Claude 3.5 Sonnet for simplification | Most faithful, nuanced medical language simplification |
| Zustand + localStorage | Offline-first, persists across sessions |
| shadcn/ui + Tailwind | Consistent design system, fast to build |
| framer-motion | Smooth animations without performance cost |
| SpeechSynthesis API | Zero dependency, works in any modern browser |

---

## 🛡️ Safety & Ethics

- MedBuddy **never invents** medicines or diagnoses
- Low-confidence readings are **explicitly flagged**
- All output includes **"consult your doctor"** disclaimers
- No patient data is stored on servers (localStorage only)
- Side effects are **conservatively categorized** (err on the side of caution)

---

## 👥 Team

Built for **IAR Udaan Hackathon 2026** 🚀

---

*"Don't worry beta, we're simplifying…" — MedBuddy*
