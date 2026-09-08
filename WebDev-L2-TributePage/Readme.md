Nikola Tesla: Visionary of the Electrical AgeAn interactive, museum-curated Single Page Web Application (SPA) designed to explore the life, groundbreaking inventions, patents, and visionary intellect of Nikola Tesla. Built with a human-centric editorial aesthetic, tactile design elements, and responsive interactive engines.🌟 Key FeaturesThe Mind & The Machine (Executive Bio): Paraphrased historical biography covering Tesla's early life, the War of the Currents against Thomas Edison, his high-frequency wireless research at Colorado Springs, and his enduring legacy.AC Induction Motor & Rotating Field Simulator: An interactive step engine demonstrating Tesla's 2-phase AC sinusoidal currents and rotating magnetic vector field ($0^\circ, 90^\circ, 180^\circ, 270^\circ$) with live stator coil updates and physical explanations.Archival Patent & Life Ledger: A real-time filterable timeline and patent ledger supporting category filters (Early Life, AC Power & Motors, Wireless & High Freq, Legacy & Honors) and search queries.Chart.js Analytical Visualizations:Patent Portfolio Distribution: Canvas-rendered pie chart detailing Tesla's patent output across key technological domains.Inventive Mindset Radar: Multi-dimensional analysis mapping Tesla's strengths (Theoretical Physics, Mechanical Design, High-Voltage Power, Commercial Strategy, Visionary Forecasting).Curated Quote Vault: Filterable collection of authentic Tesla quotes categorized by theme (Energy & Universe, Invention, Future, Visualizations) with a randomizer.Knowledge Challenge Quiz: A 4-question interactive quiz providing instant scoring and detailed historical rationale explanations for every answer.🛠️ Tech Stack & DependenciesStructure & Markup: HTML5 (Semantic elements)Styling Framework: Tailwind CSS (loaded via CDN)Typography: Google Fonts (Playfair Display, Plus Jakarta Sans, Courier Prime)Data Visualizations: Chart.js v4 (Canvas rendering, responsive boundaries)Scripting: Pure Vanilla JavaScript (ES6+, DOM Manipulation, State Management)🚀 Quick Start GuideDownload or clone the single HTML file (index.html).Open the file directly in any modern web browser (Google Chrome, Mozilla Firefox, Apple Safari, or Microsoft Edge).No build step, Webpack, or npm server required. All dependencies (Tailwind CSS, Chart.js, Google Fonts) load automatically via CDN.📂 Project Architecture├── index.html                   # Single-Page Application (HTML + Tailwind + Inline JS)
└── README-Tesla-Tribute.md      # Project Documentation
Application Structure & NavigationThe application uses tabbed SPA state navigation:#overview – Hero header, biography, and "Egg of Columbus" anecdote.#simulator – AC Motor phase-shift step visualizer.#timeline – Archival search engine & chronological patent grid.#analytics – Canvas Chart.js visualizations.#quotes – Categorized quote vault.#quiz – Interactive knowledge evaluation test.📜 LicenseContent adapted from public historical records and Wikimedia Commons. Open-source for educational and research purposes.eof

```markdown:README - Client-Side Authentication System:README-Auth-System.md
# Client-Side Authentication System

A secure, lightweight, single-page client-side authentication application built using HTML5, Tailwind CSS, Vanilla JavaScript, and the browser's native **Web Crypto API**.

This system handles user registration, password strength enforcement, cryptographic SHA-256 hashing, generic error messaging, protected route guarding, and complete session termination without requiring a backend server.

---

## 📋 Feature Checklist Alignment

- [x] **Registration View:** Fields for username, email address, and password with a clear registration action.
- [x] **Password Validation Rules:** Dynamic real-time validation enforcing a minimum of 8 characters and at least 1 numeric digit (0–9).
- [x] **Duplicate Identity Prevention:** Searches `localStorage` for existing usernames or emails and displays contextual error alerts.
- [x] **Login View:** Accepts either username or email address along with password credentials.
- [x] **Generic Failure Handling:** Obscured authentication failure messages (`Invalid username/email or password provided.`) to prevent account enumeration attacks.
- [x] **Protected Route Guard:** `#dashboard` is strictly guarded. Unauthenticated access attempts automatically trigger a security banner and redirect to `#login`.
- [x] **Session Termination:** Logout functionality clears active session data from `localStorage` and redirects to the login view.
- [x] **Cryptographic Hash Storage:** Zero plain-text password storage. Uses native Web Crypto `crypto.subtle.digest('SHA-256')` to hash passwords prior to persisting in `localStorage`.
- [x] **Form Validation:** Client-side prevention of empty submissions and invalid email formats.

---

## 🛠️ Tech Stack & Security Tools

- **Frontend Framework:** HTML5 & Vanilla JavaScript (ES6+)
- **Styling:** [Tailwind CSS CDN](https://tailwindcss.com/)
- **Cryptography:** Native Web Browser `crypto.subtle.digest('SHA-256')`
- **Data Persistence:** Browser `localStorage`
- **Routing:** Hash-based SPA Routing (`#login`, `#register`, `#dashboard`)

---

## 🔒 Security Architecture

### 1. SHA-256 Password Hashing
When a user registers or logs in, the raw password is converted into a Uint8Array buffer and processed through the browser's native `crypto.subtle` engine:
```javascript
async function hashSHA256(text) {
  const encoder = new TextEncoder();
  const data = encoder.encode(text);
  const hashBuffer = await crypto.subtle.digest('SHA-256', data);
  const hashArray = Array.from(new Uint8Array(hashBuffer));
  return hashArray.map(b => b.toString(16).padStart(2, '0')).join('');
}
Only the resulting 64-character hexadecimal digest string (passwordHash) is stored or compared.2. Route Guarding LogicWhenever the browser hash changes (e.g. #dashboard), handleRoute() verifies the presence of an active token in localStorage:If unauthenticated and requesting #dashboard $\rightarrow$ Redirected to #login with an alert.If authenticated and requesting #login or #register $\rightarrow$ Automatically forwarded to #dashboard.🚀 Quick Start GuideSave the application code into an index.html file.Double-click or open index.html in your web browser.Test the flow:Click Register to create a user (e.g. user: alex, email: alex@example.com, pass: Password123).Try registering a duplicate email to verify error handling.Log in with your new credentials and inspect the protected Dashboard.Note the SHA-256 hash output displayed in the security inspector.Click Logout to safely terminate the session.📂 File Structure├── index.html                   # Complete SPA Application (HTML + Tailwind + JS)
└── README-Auth-System.md        # Technical Documentation
eof

I have created both documentation files (`README-Tesla-Tribute.md` and `README-Auth-System.md`). They cover all required details, setup steps, feature checklists, and technical explanations. Let me know if you need any adjustments!
