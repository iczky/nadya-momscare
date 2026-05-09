# MomsCare - Spesifikasi Website Telekonseling Nifas

## 1. Concept & Vision

MomsCare adalah platform telekonseling kesehatan ibu nifas berbasis web yang dirancang sederhana namun fungsional. Memberikan kemudahan bagi ibu nifas untuk berkonsultasi dengan bidan, mendapatkan edukasi kesehatan, dan melakukan skrining mandiri dari rumah. Desainnya hangat, menenangkan, dan mudah digunakan - mencerminkan kepedulian dan dukungan untuk ibu baru.

---

## 2. Design Language

### Aesthetic Direction
Soft, nurturing healthcare aesthetic dengan sentuhan hangat dan ramah. Menggunakan rounded shapes dan gentle gradients untuk menciptakan kesan aman dan nyaman.

### Color Palette (Soft White-Pink Healthcare Theme)
| Role | Color | Hex |
|------|-------|-----|
| Primary | Soft Coral Pink | `#F8BBD9` |
| Primary Dark | Rose Pink | `#EC4899` |
| Primary Light | Blush Pink | `#FCE7F3` |
| Secondary | Soft Lavender | `#E9D5FF` |
| Accent | Warm Peach | `#FED7AA` |
| Background | Cream White | `#FFFBF7` |
| Surface | Pure White | `#FFFFFF` |
| Text Primary | Dark Rose | `#831843` |
| Text Secondary | Warm Gray | `#7A6B5E` |
| Border | Soft Pink | `#F9D0E3` |
| Success | Soft Mint | `#A7F3D0` |
| Warning | Soft Amber | `#FDE68A` |
| Danger | Soft Red | `#FCA5A5` |

### Typography
- **Headings**: `Nunito` (rounded, friendly, approachable)
- **Body**: `Poppins` (clean, readable, modern)
- **Fallback**: `system-ui, sans-serif`

### Spatial System
- Base unit: 4px
- Spacing scale: 4, 8, 12, 16, 24, 32, 48, 64px
- Border radius: 8px (small), 12px (medium), 16px (large), 24px (card)
- Max content width: 1200px

### Motion Philosophy (Enhanced Healthcare Animations)
- **Entry Animations:** Fade-in (400ms), slide-up (500ms), scale-in (300ms) with staggered delays
- **Micro-interactions:** Hover lift with soft shadow elevation, button press (150ms scale 0.98)
- **Focus States:** Pink glow ring effect (focus:ring-4 focus:ring-pink-200)
- **Loading States:** Shimmer skeleton screens with pink gradient
- **Decorative:** Gentle floating animations for visual interest
- **Reduced Motion:** Full support via `prefers-reduced-motion` media query
- **Transitions:** 200ms for hover, 300ms for page changes, ease-out easing throughout

### Visual Assets
- **Icons**: Lucide React icons (consistent stroke weight) — no emoji icons
- **Illustrations**: Simple, flat illustrations with primary palette colors
- **Images**: Placeholder illustrations, no stock photos needed for spec

### Animation Keyframes (CSS)
```css
@keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }
@keyframes slideUp { from { opacity: 0; transform: translateY(20px); } to { opacity: 1; transform: translateY(0); } }
@keyframes slideLeft { from { opacity: 0; transform: translateX(30px); } to { opacity: 1; transform: translateX(0); } }
@keyframes scaleIn { from { opacity: 0; transform: scale(0.95); } to { opacity: 1; transform: scale(1); } }
@keyframes shimmer { 0% { background-position: -200% 0; } 100% { background-position: 200% 0; } }
@keyframes softPulse { 0%, 100% { opacity: 1; } 50% { opacity: 0.6; } }
```

### Animation Utility Classes
```html
<!-- Entry animations -->
<div class="animate-fade-in animate-slide-up animate-scale-in">...</div>

<!-- Staggered delays -->
<div class="animate-slide-up delay-100">...</div>
<div class="animate-slide-up delay-200">...</div>

<!-- Hover effects with pink theme -->
<button class="transition-all duration-200 hover:-translate-y-1 hover:shadow-lg hover:bg-pink-500 focus:ring-4 focus:ring-pink-200">
  Hover Lift
</button>
```

---

## 3. Layout & Structure

### Page Architecture

```
├── Landing Page (/)
│   ├── Hero Section
│   ├── Features Overview
│   ├── Materi Edukasi Preview
│   └── CTA Registration
│
├── Login/Register (/login, /register)
│
├── Dashboard (/dashboard)
│   ├── Summary Cards
│   ├── Quick Actions
│   └── Recent Activity
│
├── Telekonseling (/chat)
│   ├── Chat List
│   └── Chat Room
│
├── Edukasi (/education)
│   ├── Category List
│   └── Article Detail
│
├── Skrining (/screening)
│   ├── Form Skrining
│   └── Result Display
│
└── Profil (/profile)
    ├── Data Diri
    ├── Data Bayi
    └── Riwayat Konsultasi
```

### Responsive Strategy
- Mobile-first approach
- Breakpoints: 640px (sm), 768px (md), 1024px (lg)
- Single column on mobile, 2-column grid on tablet+
- Bottom navigation on mobile, sidebar on desktop

---

## 4. Features & Interactions

### 4.1 Autentikasi

**Registrasi:**
- Form fields: Nama lengkap, Usia, Hari ke-n nifas, Riwayat persalinan
- Validation: semua field required, usia 15-60 tahun
- Success: redirect ke dashboard dengan welcome message

**Login:**
- Email + password
- "Lupa password" link (mock functionality)
- Remember me checkbox

**Logout:** Clear session, redirect ke landing

### 4.2 Dashboard

**Summary Cards:**
- Hari ke-n nifas (dihitung otomatis)
- Status kesehatan terakhir
- Jumlah konsultasi bulan ini

**Quick Actions:**
- "Mulai Konsultasi" button
- "Skrining Sekarang" button
- "Baca Materi" shortcut

### 4.3 Telekonseling (Chat)

**Chat List:**
- List conversa dengan bidan
- Timestamps (relative: "2 jam lalu", "Kemarin")
- Unread badge indicator

**Chat Room:**
- Message bubbles (user right, bidan left)
- Timestamp per message
- Input field dengan send button
- Category selector: Umum, Laktasi, KB

### 4.4 Edukasi Nifas (Materi)

**Kategori Materi:**

```
📖 Masa Nifas
├── Pengertian Masa Nifas
├── Tahapan Nifas (Early, Middle, Late Postpartum)
└── Perawatan Masa Nifas

🤱 Menyusui
├── Teknik Menyusui yang Benar
├── ASI Eksklusif: Panduan Lengkap
├── Cara Mengatasi Puting Lecet
├── Memerah dan Menyimpan ASI
└── Posisi Menyusui yang Nyaman

💊 KB Pasca Persalinan
├── Jenis-Jenis KB Pasca Persalinan
├── IUD: Kelebihan dan Cara Kerja
├── Implant: Informasi Lengkap
├── Suntik KB: Jadwal dan Efek Samping
├── Pil KB: Penggunaan yang Tepat
└── Metode Amenorrhea Laktasi (MAL)

⚠️ Tanda Bahaya Nifas
├── Perdarahan Banyak (Hemoragi)
├── Demam Tinggi Pasca Persalinan
├── Nyeri Perut Hebat
├── Payudara Bengkak (Mastitis)
└── Depresi Postpartum: Kenali dan Atasi
```

**Article Detail:**
- Title, content dalam markdown-like format
- Estimated reading time
- Related articles di bottom

### 4.5 Skrining Kesehatan

**Skrining Form:**
1. **Pertanyaan Depresi Postpartum (EPDS simplified - 10 pertanyaan)**
   - Menggunakan scoring 0-3 per pertanyaan
   - Total score menunjukkan level risiko

2. **Skrining Tanda Bahaya**
   - Perdarahan
   - Demam
   - Nyeri hebat
   - Pembengkakan payudara
   - Gangguan psikologis

3. **Penilaian Kondisi Umum**
   - Tekanan darah (sys/dia)
   - Suhu tubuh
   - Kondisi luka jahitan

**Output Rekomendasi:**
| Score Range | Result | Action |
|-------------|--------|--------|
| 0-8 | Aman | Edukasi rutin |
| 9-12 | Perlu Konsultasi | Rekomendasi konsultasi bidan |
| 13+ | Segera ke Fasilitas Kesehatan | Tampilkan kontak darurat |

### 4.6 Profil Pengguna

**Data Diri:**
- Nama, usia, tanggal persalinan
- Edit functionality

**Data Bayi:**
- Nama bayi, jenis kelamin, berat badan lahir, tanggal lahir
- Tanggal automatically calculated

**Riwayat Konsultasi:**
- List chronologically
- Filter by date range

### 4.7 Kontak Darurat

- Nomor hotline bidan
- Alamat fasilitas kesehatan terdekat (mock data)
- Instruksi pertolongan pertama

---

## 5. Component Inventory

### Navigation
| State | Appearance |
|-------|------------|
| Desktop | Sidebar with icons + labels, 240px width |
| Mobile | Bottom tab bar, 5 items max |
| Active | Primary color highlight + bold text |

### Cards
| Variant | Use Case |
|---------|----------|
| Feature Card | Landing page feature showcase |
| Materi Card | Education article preview |
| Chat Preview | Chat list item |
| Stat Card | Dashboard metrics |

### Buttons
| Variant | Usage |
|---------|-------|
| Primary | CTA, submit forms |
| Secondary | Secondary actions |
| Ghost | Less prominent actions |
| Danger | Destructive actions |

| State | Appearance |
|-------|------------|
| Default | Solid pink background |
| Hover | Scale 1.02, shadow elevation, darker pink (#EC4899) |
| Active | Scale 0.98, press effect, 150ms ease-in |
| Disabled | 50% opacity, no pointer |
| Loading | Spinner icon, disabled, pink shimmer |
| Focus | Pink glow ring (ring-4 ring-pink-200) |

### Form Inputs
- Text input dengan floating label
- Select dropdown dengan custom styling
- Radio/Checkbox dengan custom styling
- Textarea untuk message input

### Chat Bubbles
- User: Right-aligned, primary color background, white text
- Bidan: Left-aligned, surface background, dark text, with avatar

### Modals
- Centered, backdrop blur
- Close button di corner
- Smooth fade-in animation

---

## 6. Technical Approach

### Stack
- **Framework**: React (Vite) atau Next.js
- **Styling**: Tailwind CSS
- **Icons**: Lucide React
- **State**: React useState/useContext (local state, no backend for MVP)
- **Storage**: localStorage untuk persistensi data

### Data Model

```typescript
interface User {
  id: string;
  name: string;
  email: string;
  age: number;
  birthDate: Date;
  deliveryDate: Date;
  deliveryHistory: string;
}

interface Baby {
  id: string;
  name: string;
  gender: 'L' | 'P';
  birthDate: Date;
  birthWeight: number;
}

interface ChatMessage {
  id: string;
  sender: 'user' | 'bidan';
  category: 'umum' | 'laktasi' | 'kb';
  content: string;
  timestamp: Date;
}

interface ChatThread {
  id: string;
  participantId: string;
  participantName: string;
  lastMessage: string;
  lastMessageTime: Date;
  unreadCount: number;
}

interface ScreeningResult {
  id: string;
  date: Date;
  epdsScore: number;
  dangerSigns: string[];
  generalCondition: object;
  recommendation: 'aman' | 'konsultasi' | 'urgent';
}

interface Article {
  id: string;
  category: string;
  title: string;
  content: string;
  readingTime: number;
}
```

### File Structure (Next.js)

```
/src
├── app/
│   ├── page.tsx (Landing)
│   ├── login/page.tsx
│   ├── register/page.tsx
│   ├── dashboard/page.tsx
│   ├── chat/page.tsx
│   ├── chat/[id]/page.tsx
│   ├── education/page.tsx
│   ├── education/[slug]/page.tsx
│   ├── screening/page.tsx
│   ├── profile/page.tsx
│   └── layout.tsx
├── components/
│   ├── ui/ (Button, Card, Input, etc.)
│   ├── Navigation.tsx
│   ├── ChatBubble.tsx
│   └── ArticleContent.tsx
├── data/
│   └── articles.ts (Static content)
├── lib/
│   ├── utils.ts
│   └── context.tsx
└── styles/
    └── globals.css
```

### Deployment
- Vercel atau Netlify
- Static export possible dengan Next.js
- Environment: Not required for MVP (all data in localStorage)

---

## 7. Content (Bahasa Indonesia)

### Landing Page Copy
- Hero: "Selamat Datang, Ibu! MomsCare siap menemani masa nifas Anda."
- Subtitle: "Konsultasi dengan bidan, pelajari perawatan nifas, dan pantau kesehatan Anda dengan mudah."

### Edukasi Content (Summary)
Semua materi dalam Bahasa Indonesia dengan bahasa yang ramah dan mudah dipahami. Untuk implementasi MVP, materi disajikan dalam format teks biasa dengan heading hierarchy yang jelas.

---

## 8. Scope Boundaries (MVP)

**Included:**
- Landing page dengan informasi fitur
- Autentikasi (mock, localStorage-based)
- Dashboard dengan summary
- Chat interface (UI only, mock responses)
- Halaman edukasi dengan materi lengkap
- Form skrining dengan hasil
- Profil dengan data diri dan bayi

**Deferred (Future):**
- Backend API integration
- Real-time chat dengan bidan actual
- Push notifications
- Multi-language support
- Dark mode
- Export laporan PDF