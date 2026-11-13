# 🥥 Pooja Coconut Scan AI — Case Study

[![React 19](https://img.shields.io/badge/Frontend-React_19-61dafb?style=for-the-badge&logo=react)](https://react.dev/)
[![AWS Amplify](https://img.shields.io/badge/Cloud-AWS_Amplify_Gen_2-FF9900?style=for-the-badge&logo=amazonaws)](https://aws.amazon.com/amplify/)
[![Capacitor](https://img.shields.io/badge/Mobile-Capacitor_Android%2FiOS-119EFF?style=for-the-badge&logo=capacitor)](https://capacitorjs.com/)
[![TFLite](https://img.shields.io/badge/AI-TensorFlow_Lite-FF6F00?style=for-the-badge&logo=tensorflow)](https://www.tensorflow.org/lite)

> **Documentation-Only Repository** — Proprietary source code, trained AI models, and company datasets are not published. APK available as a release download below.

---

## 📱 Download

| Platform | Link |
|---|---|
| **Android APK** | [⬇️ Download Latest Release](https://github.com/rahaman1721/pooja-coconut-scan-ai/releases/latest) |
| **Admin Console** | [🌐 Live Web Dashboard](https://temporary-rapid-timpani-kicvzzs.vercel.app) |

> Status: Under Play Store / App Store review.

---

## 🌐 Overview

**Pooja Coconut Scan AI** is a full B2B agricultural platform for the coconut supply chain in Tamil Nadu and South India. It connects coconut farmers and suppliers with buyers and distributors through an AI-verified quality grading marketplace with integrated payments, real-time orders, and a connected admin dashboard.

---

## ✨ Full Feature Set

### 📸 AI Quality Scanning
- On-device TensorFlow Lite model for real-time coconut grading
- Classifies: Good / Damaged / Reject — zero internet required
- Camera integration with live scan preview
- Microphone input support
- Scan results saved with image to AWS S3
- Full scan history with timestamps and grades

### 🛒 B2B Marketplace
- Seller listings with AI-verified quality grades
- Buyer browsing, search, and filtering by grade and location
- Product listing management for sellers
- Real-time price updates via AppSync GraphQL subscriptions
- Order placement and confirmation workflow
- Multi-role access: Farmer / Buyer / Admin

### 💳 Payment Integration
- Integrated payment flow for marketplace transactions
- Order value calculation based on grade and quantity
- Payment confirmation and receipt generation
- Transaction history per buyer and seller

### 📦 Order Management
- End-to-end order lifecycle: Placed → Confirmed → Dispatched → Delivered
- Real-time order status updates
- Seller order dashboard with pending/active/completed views
- Buyer order tracking with status visibility

### 🔗 Admin Web Console Connection
- Standalone React 19 Admin Web Console (Vercel deployed)
- Connected to the same AWS Amplify Gen 2 backend
- Admin can view all scan reports across all users
- Quality moderation: approve / flag / override scan grades
- User map: live geographic view of active sellers and buyers
- Full user management: role assignment, account status
- Analytics: scan volume, marketplace activity, order trends

### 🔒 Authentication & Security
- Multi-role auth via Amazon Cognito (Farmer / Buyer / Admin)
- Identity pool integration for secure S3 access
- JWT-secured API calls to AppSync
- Role-based data access control via AppSync authorization directives

### 📶 Offline-First Architecture
- All AI inference runs locally on-device
- Offline scan queue for areas with no connectivity
- Queue syncs automatically when connection resumes
- LocalStorage cache for recent listings and order history

---

## 🏗️ High-Level System Architecture

```
┌───────────────────────────────────────────────────────────────────┐
│                     POOJA COCONUT SCAN AI                         │
└───────────────────────────────────────────────────────────────────┘

   ┌────────────────────┐         ┌─────────────────────────────────┐
   │  Android / iOS     │         │     AWS Cloud (Amplify Gen 2)   │
   │  Mobile App        │  HTTPS  │                                 │
   │                    │◄───────►│  ┌──────────┐  ┌────────────┐  │
   │  ┌──────────────┐  │         │  │ AppSync  │  │  Cognito   │  │
   │  │ TFLite AI    │  │         │  │ GraphQL  │  │ Auth Pools │  │
   │  │ Engine       │  │         │  └────┬─────┘  └────────────┘  │
   │  └──────────────┘  │         │       │                        │
   │  ┌──────────────┐  │         │  ┌────▼─────┐  ┌────────────┐ │
   │  │ Offline      │  │         │  │ DynamoDB │  │ Amazon S3  │ │
   │  │ Scan Queue   │  │         │  │ Store    │  │ Image Store│ │
   │  └──────────────┘  │         │  └──────────┘  └────────────┘ │
   │  ┌──────────────┐  │         │                                │
   │  │ Payment Flow │  │         │  ┌──────────────────────────┐  │
   │  └──────────────┘  │         │  │   Payment Processing     │  │
   │  ┌──────────────┐  │         │  └──────────────────────────┘  │
   │  │ Order Mgmt   │  │         └─────────────────────────────────┘
   │  └──────────────┘  │
   └────────┬───────────┘
            │ Capacitor Bridge
            │
   ┌────────▼───────────┐         ┌─────────────────────────────────┐
   │  React 19 UI Layer │         │   Admin Web Console             │
   │  (Vite PWA)        │         │   React 19 + Vercel             │
   └────────────────────┘         │   Scan Reports | User Map       │
                                  │   Quality Moderation | Analytics│
                                  │   User Management | Orders      │
                                  └─────────────────────────────────┘
```

---

## 🛠️ Technology Stack

| Layer | Technology |
|---|---|
| Mobile Frontend | React 19, Vite, TypeScript |
| Mobile Runtime | Capacitor (Android + iOS) |
| AI / ML Engine | TensorFlow Lite (on-device inference) |
| Backend / API | AWS AppSync, GraphQL |
| Database | Amazon DynamoDB |
| File Storage | Amazon S3 |
| Authentication | Amazon Cognito (User Pools + Identity Pools) |
| Cloud Platform | AWS Amplify Gen 2 |
| Payment | Payment gateway integration |
| Admin Console | React 19 + Vercel |

---

## 👨‍💻 My Role & Contributions

As **Lead Mobile & Frontend Engineer**:

- Architected the full React 19 + Capacitor mobile app from design to Android/iOS production
- Integrated and optimized the TensorFlow Lite pipeline for real-time offline inference on Android hardware
- Designed and implemented the AWS Amplify Gen 2 schema (DynamoDB models, Cognito auth, S3 rules)
- Built secure multi-role authentication with Cognito and AppSync authorization
- Developed the complete B2B marketplace with real-time GraphQL subscriptions
- Implemented payment integration and order management workflows
- Connected mobile app to the Admin Web Console via shared Amplify backend
- Engineered offline-first scan queue for rural connectivity conditions

---

## 📞 Contact

**Obaidhur Rahaman**
Portfolio: [rahaman1721.framer.website](https://rahaman1721.framer.website)
GitHub: [@rahaman1721](https://github.com/rahaman1721)
LinkedIn: [obaidhur-rahaman-1721z](https://www.linkedin.com/in/obaidhur-rahaman-1721z)
