# 🥥 Pooja Coconut Scan AI — Case Study

[![React 19](https://img.shields.io/badge/Frontend-React_19-61dafb?style=for-the-badge&logo=react)](https://react.dev/)
[![AWS Amplify](https://img.shields.io/badge/Cloud-AWS_Amplify_Gen_2-FF9900?style=for-the-badge&logo=amazonaws)](https://aws.amazon.com/amplify/)
[![Capacitor](https://img.shields.io/badge/Mobile-Capacitor_Android%2FiOS-119EFF?style=for-the-badge&logo=capacitor)](https://capacitorjs.com/)
[![TFLite](https://img.shields.io/badge/AI-TensorFlow_Lite-FF6F00?style=for-the-badge&logo=tensorflow)](https://www.tensorflow.org/lite)

> **⚠️ Documentation-Only Repository**: This repository contains case study documentation and high-level architecture only. Proprietary source code, trained models, and company datasets are not published here.

---

## 📋 Project Overview

**Pooja Coconut Scan AI** is a production B2B agricultural AI platform built for the Tamil Nadu and South India coconut supply chain industry. It enables real-time, offline-capable AI quality grading of mature coconuts directly at the farm or procurement point using on-device TensorFlow Lite inference.

The platform connects coconut farmers/suppliers (sellers) with procurement teams and distributors (buyers) through a smart marketplace with AI-verified quality grades.

---

## 📱 Download & Try

| Platform | Link |
|---|---|
| **Android APK** | [⬇️ Download Latest Release](https://github.com/rahaman1711/pooja-coconut-scan-ai/releases/latest) |
| **Admin Console** | [🌐 Live Dashboard](https://temporary-rapid-timpani-kicvzzs.vercel.app) |

---

## 🎯 Key Features

- **📸 AI Coconut Quality Scan** — On-device TensorFlow Lite model classifies Good/Damaged/Reject in real-time, with zero internet dependency.
- **🛒 B2B Marketplace** — Verified seller listings and buyer procurement workflows with Cognito-secured role separation.
- **📡 Real-Time Sync** — AWS AppSync GraphQL subscriptions for live price updates and order status.
- **🔒 Secure Authentication** — Multi-role auth (Farmer / Buyer / Admin) via Amazon Cognito user pools and identity pools.
- **📊 Scan History & Reports** — DynamoDB-backed scan archives with S3 image persistence per quality event.
- **📶 Offline-First Architecture** — All AI inference runs locally on Android/iOS with queue-based sync when connectivity resumes.

---

## 🏗️ High-Level System Architecture

```
┌─────────────────────────────────────────────────────────────────┐
│                    POOJA COCONUT SCAN AI                        │
│                     System Architecture                          │
└─────────────────────────────────────────────────────────────────┘

   ┌──────────────┐        ┌─────────────────────────────────────┐
   │ Android/iOS  │        │        AWS Cloud (Amplify Gen 2)    │
   │  Mobile App  │        │                                     │
   │              │        │  ┌─────────┐    ┌──────────────┐   │
   │ ┌──────────┐ │  HTTPS │  │ AppSync │    │   Cognito    │   │
   │ │TFLite AI │ │◄──────►│  │GraphQL  │    │  Auth Pools  │   │
   │ │ Engine   │ │        │  └────┬────┘    └──────────────┘   │
   │ └──────────┘ │        │       │                             │
   │ ┌──────────┐ │        │  ┌────▼────┐    ┌──────────────┐   │
   │ │ Offline  │ │        │  │DynamoDB │    │ Amazon S3    │   │
   │ │  Queue   │ │        │  │  Store  │    │ Image Store  │   │
   │ └──────────┘ │        │  └─────────┘    └──────────────┘   │
   └──────────────┘        └─────────────────────────────────────┘
          │
          │ Capacitor Bridge
          │
   ┌──────▼───────┐        ┌─────────────────────────────────────┐
   │  React 19    │        │       Admin Web Console             │
   │  UI Layer    │        │  (React 19 + Vercel Deployment)     │
   │  (Vite PWA)  │        │  Scan Reports | User Map | QA Panel │
   └──────────────┘        └─────────────────────────────────────┘
```

---

## 🛠️ Technology Stack

| Layer | Technology |
|---|---|
| **Mobile Frontend** | React 19, Vite, TypeScript |
| **Mobile Runtime** | Capacitor (Android + iOS) |
| **AI / ML Engine** | TensorFlow Lite (on-device inference) |
| **Backend / API** | AWS AppSync, GraphQL |
| **Database** | Amazon DynamoDB |
| **File Storage** | Amazon S3 |
| **Authentication** | Amazon Cognito (User Pools + Identity Pools) |
| **Cloud Platform** | AWS Amplify Gen 2 |
| **Admin Console** | React 19 + Vercel |

---

## 👨‍💻 My Role & Contributions

As the **Lead Mobile & Frontend Engineer**, I was responsible for:

- Architecting the full React 19 + Capacitor mobile application from initial design to Android APK production release.
- Integrating and optimizing the TensorFlow Lite model pipeline for real-time offline inference on low-to-mid-range Android hardware.
- Designing and implementing the AWS Amplify Gen 2 schema (DynamoDB models, Cognito auth flows, S3 storage rules).
- Building secure multi-role authentication (Farmer/Buyer/Admin) with Cognito and AppSync authorization directives.
- Developing the buyer/seller marketplace workflows with real-time GraphQL subscription updates.
- Engineering the offline-first scan queue to handle intermittent rural connectivity reliably.

---

## 📞 Contact

**Obaidhur Rahaman**  
Portfolio: [rahaman1721.framer.website](https://rahaman1721.framer.website)  
GitHub: [@rahaman1711](https://github.com/rahaman1711)  
LinkedIn: [obaidhur-rahaman-1721z](https://www.linkedin.com/in/obaidhur-rahaman-1721z)
