# 🏥 Sivamed Multispeciality Hospital

### Modern Healthcare Web Experience • React 18 • Vite • Tailwind CSS • Framer Motion

<p align="center">
  <strong>A production-ready, responsive healthcare web platform designed for Sivamed Multispeciality Hospital, Pollachi.</strong>
</p>

<p align="center">
  <a href="#-live-experience">Live Experience</a> •
  <a href="#-frontend-highlights">Frontend Highlights</a> •
  <a href="#-features">Features</a> •
  <a href="#-architecture">Architecture</a> •
  <a href="#-installation">Installation</a>
</p>

---

## ✨ Project Overview

**Sivamed Multispeciality Hospital** is a modern healthcare web portal focused on delivering a fast, accessible and patient-friendly digital experience.

The application combines a polished medical UI with practical healthcare workflows such as:

* 🚑 24/7 Emergency access
* 👨‍⚕️ Doctor discovery
* 🏥 Department exploration
* 📅 Online appointment booking
* 💬 WhatsApp appointment fallback
* 🩺 Preventive health packages
* 💳 Insurance & cashless admission information
* 🛏️ Inpatient information
* 🖼️ Interactive hospital gallery
* 📚 Health education blog
* 🔐 Reception/admin appointment dashboard
* 📱 Fully responsive mobile experience

> **Design philosophy:** Reduce the friction between a patient and the healthcare service they need.

---

# 🎨 Frontend Showcase

## 🖥️ Modern Healthcare Interface

The frontend is designed around a clean medical visual language with strong hierarchy, generous spacing, responsive layouts and clear calls-to-action.

### Core UI Principles

```text
┌──────────────────────────────────────────────┐
│                TRUST                         │
│ Hospital information • Doctors • Facilities │
├──────────────────────────────────────────────┤
│                ACCESS                        │
│ Emergency • Appointment • Contact            │
├──────────────────────────────────────────────┤
│              DISCOVERY                       │
│ Departments • Doctors • Packages             │
├──────────────────────────────────────────────┤
│              INFORMATION                     │
│ Blog • FAQ • Insurance • Inpatient            │
└──────────────────────────────────────────────┘
```

---

# 🚀 Frontend Highlights

### ⚡ React 18 SPA

A Single Page Application architecture provides smooth navigation without traditional full-page reloads.

### 🧩 Component-Based UI

Reusable components are used throughout the application for:

* Navbar
* Footer
* Hero sections
* Doctor cards
* Department cards
* Package cards
* CTA sections
* Appointment forms
* FAQ accordions
* Gallery cards
* Modal/lightbox
* Loading states
* Error/404 pages

### 🎞️ Motion & Micro-Interactions

Powered by **Framer Motion** for:

* Page entrance animations
* Scroll reveal effects
* Card hover interactions
* Button feedback
* Modal transitions
* Mobile navigation animation
* Smooth UI state changes

### 📱 Responsive Design

Designed for:

```text
📱 Mobile
      ↓
📲 Tablet
      ↓
💻 Laptop
      ↓
🖥️ Desktop
```

Layouts adapt dynamically across screen sizes while maintaining usability and visual hierarchy.

### 🌓 Modern Visual System

The interface uses:

* Medical-inspired visual hierarchy
* Rounded cards
* Soft shadows
* Responsive grids
* CTA-driven sections
* Consistent typography
* Icon-based navigation
* Interactive hover states
* Accessible focus states

---

# 🧠 Core Features

## 🚑 24/7 Emergency Experience

Dedicated emergency interface containing:

* Emergency contact CTA
* Ambulance information
* Trauma information
* Chest-pain guidance
* Stroke FAST information
* Emergency department details

The emergency action remains highly visible so users can reach critical information quickly.

---

## 👨‍⚕️ Doctor Discovery

The doctor directory provides:

* Doctor search
* Specialty filtering
* Doctor profile cards
* Qualifications
* Registration details
* OPD schedules
* Department association
* Direct appointment CTA

### Dynamic Flow

```text
Department
     ↓
Specialist
     ↓
Doctor Profile
     ↓
OPD Schedule
     ↓
Book Appointment
```

---

# 🏥 Department Explorer

The application contains dedicated department pages with dynamic routes.

### Examples

```text
/departments
/departments/cardiology
/departments/orthopaedics
/departments/general-medicine
/departments/...
```

Each department can present:

* Overview
* Conditions treated
* Procedures
* OPD timings
* Specialist information
* Appointment CTA

---

# 📅 Smart Appointment Experience

The appointment system provides a streamlined booking journey.

```text
Select Department
        ↓
Select Doctor
        ↓
Enter Patient Details
        ↓
Select Date & Slot
        ↓
Confirm Appointment
        ↓
Appointment Success
```

### Appointment Features

* Reactive department/doctor selection
* Form validation
* Appointment summary
* Success screen
* REST API integration support
* WhatsApp fallback
* Reception queue support

### Fallback Architecture

```text
                 Appointment Form
                        │
                        ▼
              VITE_APPOINTMENT_ENDPOINT
                   /             \
                Available       Unavailable
                   │                 │
                   ▼                 ▼
                REST API         WhatsApp
                   │                 │
                   └────────┬────────┘
                            ▼
                    Booking Confirmation
```

This allows the frontend to remain useful even when a dedicated backend endpoint is unavailable.

---

# 💬 WhatsApp Integration

For demo/offline scenarios, the application generates a pre-filled WhatsApp appointment message.

Example workflow:

```text
Patient Information
       +
Doctor
       +
Date & Time
       ↓
Formatted WhatsApp Message
       ↓
Hospital Reception
```

---

# 🩺 Preventive Health Packages

A dedicated package interface presents multiple preventive health checkups.

### Available Categories

* Basic Health Checkup
* Executive Health Checkup
* Cardiac Checkup
* Diabetic Checkup
* Women's Health Checkup
* Senior Citizen Checkup

Each package can present its included tests and relevant information through a structured card-based UI.

---

# 💳 Insurance & Cashless Workflow

The insurance section explains:

```text
Insurance / TPA
       ↓
Eligibility Verification
       ↓
Pre-Authorization
       ↓
Cashless Admission
       ↓
Treatment
       ↓
Claim Processing
```

The UI is structured to make complex insurance information easier for patients and attendants to understand.

---

# 🛏️ Inpatient Experience

Dedicated inpatient pages provide information about:

* General rooms
* Semi-private rooms
* Deluxe rooms
* ICU
* Visiting hours
* Admission workflow
* Discharge process

---

# 🖼️ Interactive Gallery

The gallery uses a responsive visual grid with category filtering.

### Categories

```text
All
│
├── OT
├── ICU
├── Diagnostics
├── Rooms
├── Facilities
└── Hospital
```

### UI Features

* Responsive image grid
* Category filtering
* Modal lightbox
* Smooth transitions
* Mobile-friendly controls

---

# 📚 Healthcare Blog

A dedicated health education section provides:

* Article cards
* Category filtering
* Search/discovery
* Article detail pages
* Tags
* Author information
* Reading time
* Related articles

Dynamic structure:

```text
/blog
/blog/:slug
```

---

# ❓ FAQ Experience

Interactive accordion-based FAQ interface.

Users can expand individual questions without leaving the page.

Designed with:

* Keyboard accessibility
* ARIA states
* Smooth transitions
* Mobile-friendly interaction

---

# 🔐 Reception Admin Dashboard

A dedicated frontend dashboard provides a reception-style appointment queue.

```text
                    ADMIN
                      │
             ┌────────┴────────┐
             │                 │
          Pending           Processed
             │                 │
       ┌─────┴─────┐      ┌────┴────┐
       │           │      │         │
    Confirm      Cancel  Confirm   Cancel
```

### Dashboard Capabilities

* Appointment queue
* Patient information
* Doctor information
* Appointment status
* Confirm action
* Cancel action
* Reception-oriented workflow

> **Note:** The included demo credentials are intended only for local/demo presentation environments.

---

# 🧱 Architecture

```text
                    ┌───────────────────────┐
                    │       index.html      │
                    │       Vite Entry      │
                    └───────────┬───────────┘
                                │
                                ▼
                    ┌───────────────────────┐
                    │       main.jsx        │
                    │   HelmetProvider      │
                    └───────────┬───────────┘
                                │
                                ▼
                    ┌───────────────────────┐
                    │        App.jsx        │
                    │     React Router      │
                    └───────────┬───────────┘
                                │
             ┌──────────────────┼──────────────────┐
             ▼                  ▼                  ▼
         Navbar             Routes              Footer
                                │
                       Lazy Loaded Pages
                                │
        ┌───────────────────────┼────────────────────────┐
        │                       │                        │
        ▼                       ▼                        ▼
     Core Pages            Clinical Pages          Services
        │                       │                        │
    Home/About             Departments              Emergency
    Technology             Doctors                  Packages
    Gallery                Blog                     Insurance
    Testimonials           FAQ                      Inpatient
    Contact                                         Appointment
```

---

# 🗺️ Route Architecture

| Route                  | Purpose                           |
| ---------------------- | --------------------------------- |
| `/`                    | Hospital homepage                 |
| `/about`               | Hospital journey & information    |
| `/departments`         | Department directory              |
| `/departments/:slug`   | Department details                |
| `/doctors`             | Doctor directory                  |
| `/doctors/:slug`       | Doctor profile                    |
| `/emergency`           | 24/7 emergency information        |
| `/packages`            | Health checkup packages           |
| `/insurance`           | Insurance & cashless information  |
| `/inpatient`           | Admission & inpatient information |
| `/technology`          | Medical technology                |
| `/gallery`             | Interactive gallery               |
| `/testimonials`        | Patient testimonials              |
| `/blog`                | Health education                  |
| `/blog/:slug`          | Article details                   |
| `/faq`                 | Frequently asked questions        |
| `/contact`             | Contact & appointment             |
| `/appointment/success` | Booking confirmation              |
| `/admin`               | Reception dashboard               |
| `/privacy-policy`      | Privacy information               |
| `/terms-of-service`    | Terms & disclaimer                |
| `/sitemap`             | HTML sitemap                      |
| `*`                    | Custom 404 page                   |

---

# ⚡ Performance Engineering

Performance was considered at the application architecture level.

### Code Splitting

Routes are dynamically imported using React lazy loading.

```jsx
const Home = lazy(() => import("./pages/Home"));
const Doctors = lazy(() => import("./pages/Doctors"));
const Departments = lazy(() => import("./pages/Departments"));
```

Pages are rendered through:

```jsx
<Suspense fallback={<Loading />}>
  <Routes>
    ...
  </Routes>
</Suspense>
```

### Benefits

* Smaller initial JavaScript payload
* Faster initial loading
* Route-level code splitting
* Better scalability
* Reduced unnecessary downloads

---

# 🔎 SEO Architecture

SEO is implemented through a reusable SEO layer.

### Included

* Dynamic page titles
* Meta descriptions
* Canonical URLs
* Open Graph metadata
* Structured data
* XML sitemap
* HTML sitemap
* Route-specific metadata

### Structured Data

The application supports healthcare-oriented structured information such as:

```text
Hospital
MedicalBusiness
EmergencyService
Breadcrumb
Article
```

---

# ♿ Accessibility

Accessibility was considered throughout the frontend.

### Implemented Features

* Skip-to-content navigation
* Semantic HTML
* Keyboard navigation
* Visible focus states
* ARIA labels
* ARIA expanded states
* Accessible accordions
* Proper form labels
* Large touch targets
* Responsive typography
* High-contrast interface elements

---

# 🛠️ Technology Stack

## Frontend

| Technology            | Purpose                        |
| --------------------- | ------------------------------ |
| ⚛️ React 18           | UI architecture                |
| 🚀 Vite 5             | Development & production build |
| 🎨 Tailwind CSS       | Styling & responsive design    |
| 🎞️ Framer Motion     | Animations & transitions       |
| 🧭 React Router v6    | Client-side routing            |
| 🔎 React Helmet Async | SEO metadata                   |
| 🟢 Node.js            | Runtime & tooling              |

## Development

| Tool    | Purpose               |
| ------- | --------------------- |
| VS Code | Development           |
| Git     | Version control       |
| GitHub  | Repository hosting    |
| npm     | Dependency management |

---

# 📁 Project Structure

```text
Hospital-website/
│
├── public/
│   ├── images/
│   ├── icons/
│   ├── favicon/
│   └── sitemap.xml
│
├── src/
│   ├── assets/
│   │
│   ├── components/
│   │   ├── Navbar/
│   │   ├── Footer/
│   │   ├── Hero/
│   │   ├── DoctorCard/
│   │   ├── DepartmentCard/
│   │   ├── PackageCard/
│   │   ├── Gallery/
│   │   └── ...
│   │
│   ├── pages/
│   │   ├── Home.jsx
│   │   ├── About.jsx
│   │   ├── Departments.jsx
│   │   ├── DepartmentDetails.jsx
│   │   ├── Doctors.jsx
│   │   ├── DoctorDetails.jsx
│   │   ├── Emergency.jsx
│   │   ├── Packages.jsx
│   │   ├── Insurance.jsx
│   │   ├── Inpatient.jsx
│   │   ├── Technology.jsx
│   │   ├── Gallery.jsx
│   │   ├── Testimonials.jsx
│   │   ├── Blog.jsx
│   │   ├── BlogDetails.jsx
│   │   ├── FAQ.jsx
│   │   ├── Contact.jsx
│   │   ├── AppointmentSuccess.jsx
│   │   ├── Admin.jsx
│   │   ├── PrivacyPolicy.jsx
│   │   ├── Terms.jsx
│   │   └── NotFound.jsx
│   │
│   ├── data/
│   ├── hooks/
│   ├── utils/
│   ├── App.jsx
│   ├── main.jsx
│   └── index.css
│
├── index.html
├── package.json
├── vite.config.js
├── tailwind.config.js
├── postcss.config.js
└── README.md
```

---

# 💻 Installation

### 1. Clone the repository

```bash
git clone https://github.com/kala3013/sivamed-hospital.git
```

### 2. Enter the project

```bash
cd sivamed-hospital
```

### 3. Install dependencies

```bash
npm install
```

### 4. Start development server

```bash
npm run dev
```

### 5. Open in browser

```text
http://localhost:5173
```

---

# 🏗️ Production Build

Create an optimized production build:

```bash
npm run build
```

Preview the production build:

```bash
npm run preview
```

---

# 🔐 Demo Admin

For local presentation/demo purposes:

```text
URL:
http://localhost:5173/admin

Username:
admin

Password:
sivamed2024
```

> ⚠️ These credentials are demonstration credentials only. A production deployment should use secure server-side authentication, hashed passwords, sessions/JWT and role-based authorization.

---

# 🎯 UX Journey

The application is designed around the real-world journey of a hospital visitor.

```text
                 PATIENT
                    │
        ┌───────────┼───────────┐
        ▼           ▼           ▼
    Emergency    Find Doctor   Explore
        │           │           │
        ▼           ▼           ▼
     Contact     Profile      Department
        │           │           │
        └───────────┼───────────┘
                    ▼
              Appointment
                    │
                    ▼
              Confirmation
                    │
                    ▼
             Hospital Visit
```

---

# 🧪 Key Engineering Challenges

### Challenge 01 — Broken React Entry Point

**Problem**

The original React application did not have a valid Vite mounting configuration.

**Solution**

Restored the Vite entry structure:

```text
index.html
     ↓
main.jsx
     ↓
App.jsx
     ↓
React Router
```

---

### Challenge 02 — Appointment Communication

**Problem**

A frontend-only website cannot guarantee backend availability.

**Solution**

Implemented an adaptable booking flow:

```text
API configured?
      │
 ┌────┴────┐
YES        NO
 │          │
 ▼          ▼
REST      WhatsApp
API       fallback
```

---

### Challenge 03 — Large Route Structure

**Problem**

Loading every page on initial startup increases JavaScript payload.

**Solution**

Implemented route-level lazy loading and Suspense boundaries.

---

### Challenge 04 — Mobile Navigation

**Problem**

A large hospital website contains too many navigation destinations for a small screen.

**Solution**

Implemented:

* Responsive navigation
* Mobile drawer
* Dropdown navigation
* Accessible controls
* Touch-friendly targets

---

# 🏆 Project Highlights

```text
⚛️ React 18 SPA
🚀 Vite-powered development
🎨 Tailwind responsive UI
🎞️ Framer Motion interactions
🧭 Dynamic routing
📅 Appointment workflow
💬 WhatsApp fallback
👨‍⚕️ Doctor directory
🏥 14 clinical departments
🚑 Emergency workflow
💳 Insurance information
🩺 Health packages
🖼️ Interactive gallery
📚 Medical blog
🔐 Reception dashboard
🔎 SEO architecture
♿ Accessibility-focused UI
📱 Mobile-first experience
⚡ Route-level code splitting
```

---

# 📊 Frontend Feature Matrix

| Feature                | Status |
| ---------------------- | :----: |
| Responsive UI          |    ✅   |
| React SPA              |    ✅   |
| Dynamic Routing        |    ✅   |
| Lazy Loading           |    ✅   |
| Doctor Directory       |    ✅   |
| Department Explorer    |    ✅   |
| Appointment UI         |    ✅   |
| WhatsApp Fallback      |    ✅   |
| Emergency Page         |    ✅   |
| Health Packages        |    ✅   |
| Insurance Section      |    ✅   |
| Inpatient Section      |    ✅   |
| Gallery Lightbox       |    ✅   |
| Blog System            |    ✅   |
| FAQ Accordion          |    ✅   |
| Admin Queue UI         |    ✅   |
| SEO Metadata           |    ✅   |
| JSON-LD                |    ✅   |
| Accessibility Features |    ✅   |
| Custom 404             |    ✅   |

---

# 📸 Screenshots

Add your actual screenshots here after uploading them to the repository:

```text
docs/
├── home.png
├── departments.png
├── doctors.png
├── doctor-profile.png
├── appointment.png
├── emergency.png
├── packages.png
├── insurance.png
├── gallery.png
└── admin.png
```

Example showcase:

```md
## 🖥️ Homepage

![Sivamed Homepage](./docs/home.png)

## 👨‍⚕️ Doctor Directory

![Doctor Directory](./docs/doctors.png)

## 📅 Appointment Experience

![Appointment](./docs/appointment.png)
```

---

# 🌐 Live Experience

### 🏥 Hospital Website

**Sivamed Multispeciality Hospital — Pollachi**

> Replace this section with the verified production URL when the project is deployed.

### 💻 Local Development

```text
http://localhost:5173
```

---

# 🎓 Academic / Portfolio Value

This project demonstrates practical knowledge of:

* Modern React architecture
* Component-driven frontend development
* Responsive web design
* SPA routing
* Dynamic data rendering
* Form handling
* Client-side state management
* API integration patterns
* SEO implementation
* Accessibility
* Performance optimization
* UI/UX design
* Animation systems
* Healthcare workflow modelling
* Git/GitHub development practices

---

# 👨‍💻 Developer

### Kalanidhi M C

**B.E. Computer Science Engineering**

Anna University Regional Campus, Coimbatore

### Technical Focus

```text
Frontend Development
Full Stack Development
React
JavaScript
Node.js
Cloud & DevOps
AI-Integrated Applications
UI/UX
```

### Connect

<p align="center">

<a href="https://github.com/kala3013">
  <img src="https://img.shields.io/badge/GitHub-kala3013-181717?style=for-the-badge&logo=github" />
</a>

<a href="mailto:kalanidhimurugan@gmail.com">
  <img src="https://img.shields.io/badge/Email-Contact-EA4335?style=for-the-badge&logo=gmail&logoColor=white" />
</a>

</p>

---

# ⭐ Why This Project Stands Out

This is more than a static hospital website.

It demonstrates how a modern frontend can transform a traditional hospital information portal into an **interactive digital patient experience**.

From emergency access and doctor discovery to appointment booking, insurance information and health education, every major section is designed around a practical patient journey.

```text
             SIVAMED
                │
       ┌────────┴────────┐
       │                 │
    Healthcare          UX
       │                 │
       ├──── Doctors ────┤
       ├── Departments ──┤
       ├── Emergency ────┤
       ├── Appointment ──┤
       ├── Insurance ────┤
       └──── Services ───┘
                │
                ▼
       DIGITAL PATIENT
          EXPERIENCE
```

---

<p align="center">

### 🏥 Built with React • Designed for Patients • Engineered for the Web

⭐ **If you find this project useful, consider giving the repository a star.**

</p>
