# 🏭 DUTA KATUP MAS - E-Commerce Frontend

Official frontend applications for **PT DUTA KATUP MAS** e-commerce platform. This repository contains two modern Next.js applications: a customer-facing storefront and an admin dashboard.

## 🏢 About PT DUTA KATUP MAS

PT. Duta Katup Mas (DKM) is a company located in East Kalimantan, specializing in mechanical & instrument maintenance services. The company focuses on repair, reconditioning, and testing of various types of valves and instrumentation services to support oil and gas industry operations as well as power generation plants.

Founded in December 1999, PT. Duta Katup Mas has continuously developed its technical capacity, enhanced human resource expertise, and improved workshop facilities to provide comprehensive solutions for valve-related and similar equipment issues.

---

## 🛠️ Tech Stack

### ![Next.js](https://img.shields.io/badge/Next.js-16.1.1-000000?style=for-the-badge&logo=next.js&logoColor=white) 
React framework with App Router and Turbopack for 10x faster development. Key features:
- **Server Components** - Reduce client-side JavaScript bundle size
- **App Router** - File-based routing with nested layouts
- **Image Optimization** - Automatic WebP conversion and lazy loading
- **Font Optimization** - Self-hosted Google Fonts without layout shift

### ![React](https://img.shields.io/badge/React-19.2.3-61DAFB?style=for-the-badge&logo=react&logoColor=black) 
UI library with best performance and latest features like React Compiler for automatic optimization.

### ![TypeScript](https://img.shields.io/badge/TypeScript-5-3178C6?style=for-the-badge&logo=typescript&logoColor=white) 
Type-safe development with IntelliSense, compile-time error detection, and better refactoring support.

### ![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-4-38B2AC?style=for-the-badge&logo=tailwind-css&logoColor=white) 
Utility-first CSS framework with JIT compiler. Responsive breakpoints:
```tsx
<div className="mx-auto p-4 sm:max-w-xl md:max-w-2xl lg:max-w-3xl xl:max-w-6xl">
```
- `sm: 640px` - Small tablets
- `md: 768px` - Medium tablets  
- `lg: 1024px` - Laptops
- `xl: 1280px` - Desktops

### ![Zustand](https://img.shields.io/badge/Zustand-5.0.7-000000?style=for-the-badge) 
Lightweight state management for shopping cart and user preferences. Simple API without boilerplate:
```tsx
const useCartStore = create((set) => ({
  items: [],
  addItem: (item) => set((state) => ({ items: [...state.items, item] })),
  removeItem: (id) => set((state) => ({ 
    items: state.items.filter((i) => i.id !== id) 
  })),
}));
```

### ![React Hook Form](https://img.shields.io/badge/React_Hook_Form-7.61.1-EC5990?style=for-the-badge&logo=reacthookform&logoColor=white) 
Performant form handling with schema validation:
```tsx
const schema = z.object({
  name: z.string().min(2),
  email: z.string().email(),
  quantity: z.number().min(1).max(100),
});

const { register, handleSubmit } = useForm({
  resolver: zodResolver(schema),
});
```

### ![Lucide React](https://img.shields.io/badge/Lucide_React-0.535.0-F56565?style=for-the-badge) 
800+ consistent SVG icons, tree-shakable and fully customizable:
```tsx
import { ShoppingCart, User, Menu } from "lucide-react";
```

### ![React Toastify](https://img.shields.io/badge/React_Toastify-11.0.5-FFA500?style=for-the-badge) 
Toast notifications for user feedback:
```tsx
toast.success("Product added to cart!");
toast.error("Failed to add product");
```

### ![pnpm](https://img.shields.io/badge/pnpm-8+-F69220?style=for-the-badge&logo=pnpm&logoColor=white) 
Fast, disk space efficient package manager. 3x faster than npm and saves 50% disk space.

---

## 📁 Project Structure

```
ecommerce-ui/
├── client/                          # Customer storefront
│   ├── src/
│   │   ├── app/
│   │   │   ├── page.tsx            # Homepage
│   │   │   ├── layout.tsx          # Root layout
│   │   │   ├── cart/page.tsx       # Shopping cart
│   │   │   └── products/[id]/page.tsx
│   │   ├── components/
│   │   │   ├── Navbar.tsx
│   │   │   └── Footer.tsx
│   │   ├── lib/                    # Utilities
│   │   └── store/
│   │       └── cartStore.ts        # Zustand store
│   ├── public/
│   │   ├── logo-dkm.png
│   │   └── banner-dkm.png
│   └── package.json
│
├── admin/                           # Admin dashboard
│   ├── src/
│   │   ├── app/
│   │   │   ├── layout.tsx          # Admin layout
│   │   │   ├── dashboard/
│   │   │   ├── products/
│   │   │   └── orders/
│   │   ├── components/
│   │   │   ├── AppSidebar.tsx      # Sidebar navigation
│   │   │   └── providers/
│   │   │       └── ThemeProvider.tsx
│   │   └── lib/
│   └── package.json
│
└── README.md
```

---

## ✨ Features

### 🛍️ Client (Customer Portal)
- 📦 Product catalog with valve specifications and technical details
- 🔍 Advanced search & filtering for industrial equipment
- 🛒 Shopping cart with Zustand state management
- 📱 Fully responsive (mobile-first design)
- 🖼️ Optimized product images with Next.js Image
- 📝 Multi-step checkout process
- 🔔 Toast notifications for order updates
- ✅ Form validation with React Hook Form + Zod

### 🔧 Admin Dashboard
- 📊 Dashboard analytics for sales and inventory
- 📦 Product CRUD operations (valves, instruments, equipment)
- 📋 Order management and tracking
- 👥 User management for customers and staff
- 📈 Inventory tracking and stock alerts
- 🎨 Dark/Light theme toggle
- 📱 Responsive sidebar with persistent state (cookies)
- 🔐 Protected routes for secure access

---

## 🚀 Installation & Running

### Prerequisites
- Node.js 18+ or 20+
- pnpm 8+ (install: `npm install -g pnpm`)

### Clone & Install

```bash
# Clone repository
git clone https://github.com/azpradipta/ecommerce-fe.git
cd ecommerce-ui

# Install client dependencies
cd client
pnpm install

# Install admin dependencies
cd ../admin
pnpm install
```

### Running Development Server

**Client (port 3000):**
```bash
cd client
pnpm dev
```
Open http://localhost:3000

**Admin (port 3001):**
```bash
cd admin
pnpm dev
```

To run admin on different port, edit `admin/package.json`:
```json
{
  "scripts": {
    "dev": "next dev --turbopack -p 3001"
  }
}
```
Open http://localhost:3001

### Production Build

```bash
# Client
cd client
pnpm build && pnpm start

# Admin
cd admin
pnpm build && pnpm start
```

### Available Commands

```bash
pnpm dev          # Start development server with Turbopack
pnpm build        # Build production bundle
pnpm start        # Start production server
pnpm lint         # Run ESLint
```

---

## 📝 License

© 2026 PT DUTA KATUP MAS. All rights reserved.

**Developer:** [@azpradipta](https://github.com/azpradipta)

---

**Built with ❤️ using Next.js 16 + TypeScript + Tailwind CSS**

*Providing Comprehensive Valve & Instrumentation Solutions Since 1999*
