# ThriftTrack

A sleek, minimalist inventory and drop management platform designed for vintage clothing curators and merchants. ThriftTrack bridges a clean, professional vendor dashboard with a fast, mobile-friendly customer storefront.

---

## 📂 Project Structure

```text
├── index_4.html      # Vendor Dashboard & Inventory Command Center
├── storefront.html   # Public Buyer Lookbook & Checkout Interface
├── login_2.html      # Secure Admin Sign-In Gateway
└── config.js         # Shared Database Configuration & Environment Keys


✨ Key Features

1.Vendor Dashboard (index_4.html)The central hub where merchants run their day-to-day operations:

Real-Time Metrics: Instantly tracks your Active Listings, Pending Orders, and Total Revenue in Nigerian Naira (₦).

Live Order Pipeline: Monitors active buyer activity and customer holds as they happen.

Smart Hold Logic: Tracks customer checkouts with an automated 15-minute timer for storefront claims, or lets you apply manual holds for social media requests. 
If a hold expires, the dashboard flags it so you can quickly release it back to the store floor.

AI Caption Generator: Instantly builds copy-and-paste ready marketing captions using your item's title and price, complete with clear purchase instructions for your social pages.

Inventory Control Matrix: Full control to add, edit inline, copy direct checkout links, or delete items with responsive layouts tailored for both desktop and mobile views.


2. Public Storefront (storefront.html)
A clean, high-conversion catalog optimized for mobile buyers:  

Deep-Linking Support: Accepts direct item links from your social bios, automatically opening the exact item's checkout screen for the buyer without making them scroll through the entire catalog.

Secure Claims: Checks the database instantly to make sure an item is active before letting a customer claim it, preventing double-selling.  Checkout Reservation: Holds the item for the buyer for 15 minutes, showing a live countdown timer based on when the item was locked.

Direct Bank Transfer Details: Shows your shop's banking details (bank_name, account_number, account_name) directly on the checkout screen and lets buyers input their social handle to confirm their transfer.


3. Admin Gateway (login_2.html)
A secure, beautiful login panel built with a smooth, hardware-accelerated 3D tilt effect and custom animated light beams.
It connects straight to Supabase Auth to handle secure user creation and sign-ins.


🛠️ Tech StackFrontend: Ultra-lightweight HTML5 and Vanilla JavaScript styled with Tailwind CSS.

Backend & Auth: Powered completely by the Supabase JavaScript SDK. 

Live Syncing: Uses live database listeners to update your storefront and dashboard metrics instantly without needing manual page refreshes[cite: 28, 29].



📊 Database Schema (Supabase / PostgreSQL)

The application communicates with a custom thrifttrack schema containing two primary tables[cite: 28, 29]:

profiles TableManages vendor shop settings and payout details. 

id (uuid, primary_key) -> Matches the Supabase Auth User ID.

store_name (text) -> The name of your vintage shop. 

instagram_handle / whatsapp_number (text) -> Social handles for contact and links.

bank_name / account_number / account_name (text) -> Your verified payout details.

items TableTracks individual product data and checkout states.

id (uuid, primary_key) -> Unique product tracking identifier.

user_id (uuid) -> Connects the item to the merchant who owns it.

item_name (text) / price (numeric) -> The item's display title and cost.

status (text) -> Current state: active | pending | sold.

is_paid (boolean) -> Tracks if payment has been confirmed by the vendor.

ingestion_channel (text) -> Where the order came from (storefront, instagram, or whatsapp).

instagram_handle (text) -> The buyer's handle for hold verification.

locked_at (timestamp) -> Tracks exactly when a 15-minute checkout timer started.



🚀 Local Setup & Deployment

1. Configure KeysCreate a config.js file in your root folder and add your project's credentials: 

JavaScriptwindow.ENV_SUPABASE_URL = "YOUR_SUPABASE_PROJECT_URL";
window.ENV_SUPABASE_ANON_KEY = "YOUR_SUPABASE_ANON_PUBLIC_KEY";

2. Run or HostBecause the project is built completely on web standards without heavy build tools, you can run it using any simple local server:  Bashnpx servor . index_4.html --reload


You can deploy these files directly to GitHub Pages or connect the repository to Vercel for instant, global production hosting without any extra configuration steps.
