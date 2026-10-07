# Ganga Jewellers — Local Development & Setup Guide

This guide contains step-by-step instructions for team members and managers to clone, configure, and run the **Ganga Jewellers (Zewar Ganga)** Shopify theme locally on their machine.

---

## 1. Shopify Account & Access Setup (Important)

> [!IMPORTANT]
> **Do not share personal Google/Shopify accounts.**  
> The manager should use **their own email address**. The store owner or lead developer will invite them as a Staff member or Collaborator.

### How to Grant the Manager Access:
1. The Store Owner goes to **Shopify Admin** -> **Settings** (bottom left) -> **Users and permissions**.
2. Click **Add staff** (or Collaborator).
3. Enter the manager's email address.
4. Grant permissions:
   * **Online Store** (Themes, Blog posts, Pages, Navigation)
   * **Products & Collections**
   * (Optional) **Settings**
5. Send the invitation.
6. **The manager must accept the email invite and create/log into their Shopify account before proceeding.**

---

## 2. Prerequisites (Install Once)

Ensure the following tools are installed on your system:

### 1. Git
* **Windows:** Download & install from [git-scm.com](https://git-scm.com/)
* **macOS:** Run `xcode-select --install` in Terminal or `brew install git`
* **Linux (Ubuntu/Debian):** Run `sudo apt update && sudo apt install git -y`

### 2. Node.js & npm (LTS Recommended: v18+ or v20+)
* Verify if Node.js is already installed:
  ```bash
  node -v
  npm -v
  ```
* If not installed, download the LTS version from [nodejs.org](https://nodejs.org/) (includes npm).

---

## 3. Clone Repository & Setup

1. Open your terminal / command prompt.
2. Clone the repository:
   ```bash
   git clone https://github.com/Chintan2180/zewar-ganga-shopify.git
   ```
3. Navigate into the project folder:
   ```bash
   cd zewar-ganga-shopify
   ```
4. Switch to the active development branch (`dev`):
   ```bash
   git checkout dev
   git pull origin dev
   ```

---

## 4. Run the Local Development Server

Start the local Shopify development server with the following command:

```bash
npx shopify theme dev --store zewar-ganga-golds-silver-5y1mpz5b.myshopify.com
```

### First-Time Login Prompt:
* The CLI will display a link and a device verification code:
  ```text
  To run this command, log in to Shopify.
  User verification code: XXXX-XXXX
  Opened link to start the auth process: https://accounts.shopify.com/activate-with-code?...
  ```
* Open the link in your browser, log in with **your staff email account**, and authorize the CLI.
* Once authorized, the CLI will start syncing the theme files to a private development preview.

### Accessing the Local Store:
Once started, the CLI will output:
* **Local Development Preview:** [http://127.0.0.1:9292](http://127.0.0.1:9292)
* **Shareable Theme Preview:** A Shopify preview URL with `?preview_theme_id=...`
* **Theme Editor / Customizer:** Direct link to customize the theme in the Shopify admin interface.

Any changes made to local files (`.liquid`, `.json`, `.css`, `.js`) will hot-reload in real-time.

---

## 5. Accessing Shopify Store Admin & Theme Settings

To manage store products, settings, and themes directly in the browser:

* **Shopify Admin Dashboard:**  
  [https://admin.shopify.com/store/zewar-ganga-golds-silver-5y1mpz5b](https://admin.shopify.com/store/zewar-ganga-golds-silver-5y1mpz5b)
* **Themes Configuration:**  
  [https://admin.shopify.com/store/zewar-ganga-golds-silver-5y1mpz5b/themes](https://admin.shopify.com/store/zewar-ganga-golds-silver-5y1mpz5b/themes)

---

## 6. Daily Workflow & Useful Commands

| Action | Command |
| :--- | :--- |
| **Start Local Dev Server** | `npx shopify theme dev --store zewar-ganga-golds-silver-5y1mpz5b.myshopify.com` |
| **Pull latest changes from Shopify Admin** | `npx shopify theme pull --store zewar-ganga-golds-silver-5y1mpz5b.myshopify.com` |
| **Pull only theme settings (logo, colors)** | `npx shopify theme pull --only config/settings_data.json --store zewar-ganga-golds-silver-5y1mpz5b.myshopify.com` |
| **Open Theme Editor in browser** | `npx shopify theme open --store zewar-ganga-golds-silver-5y1mpz5b.myshopify.com` |
| **Log out of Shopify CLI** | `npx shopify auth logout` |

---

## 7. Troubleshooting

### 1. "You are not authorized to use the CLI to develop in the provided store"
* Ensure your staff invitation has been accepted in the browser.
* Double-check that the store domain contains `-5y1mpz5b`:  
  `zewar-ganga-golds-silver-5y1mpz5b.myshopify.com` (not `zewar-ganga-golds-silver.myshopify.com`).

### 2. "GraphQL Error (Code: 401) / Token expired"
* Run `npx shopify auth logout` to clear old tokens.
* Re-run the `shopify theme dev` command and log in again via the browser prompt.

### 3. Port 9292 is already in use
* If port 9292 is occupied, specify a custom port:
  ```bash
  npx shopify theme dev --store zewar-ganga-golds-silver-5y1mpz5b.myshopify.com --port 9293
  ```
