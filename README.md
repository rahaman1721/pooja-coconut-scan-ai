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

## 🏗️ System Architecture & Data Flow

Pooja Coconut Scan AI is engineered with a **hybrid edge-cloud architecture**, decoupling latency-critical on-farm computer vision inference from the centralized B2B marketplace and administrative audit layer.

```mermaid
flowchart TD
    subgraph EdgeDevice ["📱 Mobile Field Device (Farmer / Field Inspector)"]
        CamCapture["Live Camera / Capacitor Bridge"]
        TFLite["On-Device TensorFlow Lite Model (Quantized INT8)"]
        QualityClassifier{"Inference Engine: Good / Damaged / Reject"}
        OfflineQueue["Offline Transaction & Scan Queue (LocalStorage)"]
    end

    subgraph AWSCloud ["☁️ AWS Amplify Gen 2 Cloud Backend"]
        Cognito["Amazon Cognito (Farmer / Buyer / Admin RBAC)"]
        AppSync["AWS AppSync GraphQL API (Real-Time Subscriptions)"]
        DynamoDB[("Amazon DynamoDB (Listings, Orders, Audit Ledger)")]
        S3Storage[("Amazon S3 (Encrypted High-Res Evidence Images)")]
    end

    subgraph EnterpriseClients ["💻 Enterprise Admin & Buyer Portals"]
        AdminDashboard["React 19 Admin Web Console (Vercel Deployed)"]
        GeoMap["Live Geographic Active Farmer/Buyer Map"]
        QualityAudit["Quality Moderation & Grade Override Engine"]
        B2BMarketplace["B2B Order Routing & Payment Gateway"]
    end

    CamCapture -->|Raw Frame Buffer| TFLite
    TFLite --> QualityClassifier
    QualityClassifier -->|Instant Grade (<150ms, Zero Internet)| OfflineQueue
    
    OfflineQueue <-->|Auto-Sync on Connectivity| AppSync
    OfflineQueue -->|Signed URL Upload| S3Storage
    
    AppSync <--> Cognito
    AppSync <--> DynamoDB
    
    AppSync <-->|GraphQL Subscriptions (wss://)| AdminDashboard & B2BMarketplace
    AdminDashboard --> QualityAudit & GeoMap
    B2BMarketplace -->|Order Settlement| DynamoDB
```

### 🔬 Edge-Cloud Data Flow Breakdown

1. **Zero-Latency Agricultural Inference**:
   - Rural coconut groves in South India frequently suffer from intermittent or non-existent 4G/5G mobile connectivity.
   - The TensorFlow Lite quantized computer vision model runs 100% locally on Android/iOS CPU/GPU delegates via Capacitor, outputting real-time classifications (`Good`, `Damaged`, `Reject`) in under 150ms.
2. **Resilient Offline Sync Pipeline**:
   - Classification payloads, timestamps, and geolocation tags are queued locally. When network connectivity is re-established, the AWS Amplify Gen 2 client synchronizes mutations via AWS AppSync GraphQL.
3. **Real-Time B2B Marketplace & Administrative Audit**:
   - Verified coconut lots are published to the B2B marketplace where verified buyers can place orders against verified grades.
   - Enterprise administrators audit grading accuracy through the React 19 web console, with full authority to approve, flag, or adjust grade thresholds dynamically.

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
