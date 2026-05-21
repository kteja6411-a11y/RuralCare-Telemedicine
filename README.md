# RuralCare — Telemedicine & Medicine Delivery Platform for Rural India

RuralCare is a multilingual, mobile-friendly telemedicine and medicine delivery web platform designed specifically for rural populations in India. The application features bilingual layouts, medical emergency hotlines, prescription downloads, virtual consultations, and a medicine cart with cost-saving generic suggestions.

---

## 🚀 Key Features

* 🌐 **Multi-Language UI**: Seamless toggle between English, Hindi, Telugu, Tamil, Malayalam, and Kannada, with an optional bilingual visual layout.
* 🩺 **Telemedicine Consultation**: Search doctors by language/specialty, fill symptom profiles, launch mock WebRTC calls with caption transcripts, and download PDF clinical prescriptions.
* 💊 **Generic-First Medicine Store**: Medicine listing highlighting affordable generic alternatives, helping families save on critical healthcare purchases.
* 📸 **Image-Based Medicine Scan**: Camera-based OCR search and drag-and-drop file upload to identify medicine labels, paired with a Google Translate language assistance helper card.
* 👨‍👩‍👧 **Family Accounts**: Link and manage dependent health files (age, relation, history) under one main telephone number.
* 💳 **Simulated UPI Checkout**: Quick checkout with simulated QR code scanning for payments, mobile wallets, and cash on delivery.
* 📄 **Printable Invoices & Reports**: Professional HTML-to-PDF invoice printing and medical prescriptions.
* 🚴 **Delivery Partner Portal**: Interactive portal and onboarding forms for local village delivery riders.

---

## 🛠️ Tech Stack

### Frontend
- **Framework**: React 19 + Vite 8 + TypeScript
- **Styling**: Tailwind CSS v4 (configured via `@tailwindcss/postcss` for seamless CSS config rules) + Lucide Icons

### Backend
- **Server**: Node.js + Express + TypeScript
- **Database**: Dual-Mode Database (Mongoose for **MongoDB** with an automatic **local JSON-file database fallback** `server/data/db-fallback.json` if MongoDB is offline).

---

## 📂 Project Directory Structure

```
ruralcare/
├── package.json          # Monorepo configuration
├── .gitignore            # Git exclusion rules
├── README.md             # Project documentation
├── client/               # Vite React Frontend
│   ├── src/
│   │   ├── components/   # Shared UI (Header, VideoCall, DownloadReport)
│   │   ├── context/      # State management (Theme, Language, Cart, Auth)
│   │   └── pages/        # Views (Home, Medicines, Cart, Orders, Consult, Subscription, Search, Family, Login)
│   ├── tailwind.config.js
│   ├── postcss.config.js
│   ├── vite.config.ts
│   └── package.json
└── server/               # Express Backend API
    ├── src/
    │   ├── db.ts         # Unified Database CRUD & Fallback Service
    │   ├── index.ts      # Express Router & Endpoints
    │   └── types.ts      # TypeScript interfaces
    ├── data/
    │   └── db-fallback.json # Local database storage
    └── tsconfig.json
```

---

## ⚙️ Getting Started

### Prerequisites
- Node.js (version 18 or above)
- npm (version 9 or above)
- *Optional*: MongoDB running locally on `mongodb://localhost:27017`

### 1. Installation
Install workspace dependencies for both `client` and `server`:
```bash
npm run install-all
```

### 2. Running in Development Mode
You can start both the backend server and frontend client concurrently:

- **Start Backend API Server** (runs on port 5000):
  ```bash
  npm run dev:server
  ```
- **Start Frontend App Client** (runs on port 5173):
  ```bash
  npm run dev:client
  ```

### 3. Database Customization
By default, if the database cannot connect to a live MongoDB instance, it will log a warning and fall back to `server/data/db-fallback.json`. To connect to a specific MongoDB instance, configure your environment variables:

Create a `.env` file in the `server` directory:
```env
PORT=5000
MONGO_URI=mongodb+srv://<username>:<password>@cluster.mongodb.net/ruralcare
```

### 4. Build
To compile the projects for production deployment:
```bash
npm run build:server
npm run build:client
```
