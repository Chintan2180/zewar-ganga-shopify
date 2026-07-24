# Information Architecture: Zewar Ganga Golds & Silver

This document details the navigation, collection structure, product schemas, and metadata requirements for the **Zewar Ganga Golds & Silver** Shopify store.

---

## 1. Site Navigation Map

### A. Header (Main Navigation)
* **Home**
* **Gold Jewelry** (Dropdown)
    * All Gold Jewelry
    * Rings
    * Chains & Necklaces
    * Bangles & Bracelets
    * Earrings
* **Silver Jewelry** (Dropdown)
    * All Silver Jewelry
    * Rings & Bands
    * Anklets (Payal)
    * Silver Utensils & Gift Items
* **Coins & Bars** (Dropdown)
    * Gold Coins (1g, 2g, 5g, 10g)
    * Silver Coins & Bars (10g, 20g, 50g, 100g, 250g, 500g, 1kg)


### B. Footer Navigation
* **Customer Support:**
  * Contact Us (Direct link to WhatsApp Support: `https://wa.me/<number>`)
  * Shipping & Delivery
  * Returns & Exchange Policy
  * FAQ
* **About Us:**
  * Our Heritage
  * Authenticity & Certification (Hallmark BIS 916)
  * Store Locator
* **Legal:**
  * Terms of Service
  * Privacy Policy
* **Social Media Handles:**
  * Instagram, Facebook, and Pinterest links

---

## 2. E-commerce Collections (Product Categories)

| Collection Title | Handle | Type | Description |
| :--- | :--- | :--- | :--- |
| **Gold Jewelry** | `gold-jewelry` | Automated | Products tagged with `metal: Gold` |
| **Silver Jewelry** | `silver-jewelry` | Automated | Products tagged with `metal: Silver` |
| **Coins & Bars** | `coins-bars` | Automated | Products tagged with `category: Bullion` |
| **Wedding Collection** | `wedding-jewelry` | Manual | Curated high-value bridal sets, heavy chokers, necklaces, and bangles |
| **New Arrivals** | `new-arrivals` | Automated | Products created within the last 30 days |
| **Gifting Collection** | `gifting` | Manual | Curated silver articles and lightweight coins suitable for festivals & weddings |

---

## 3. Product Variant & Custom Attributes Schema

Jewelry items require highly specific variant handling. We will set up the following parameters:

### A. Standard Variants
1. **Metal Purity:**
   * **Gold:** `24K (999 Purity)`, `22K (916 BIS Hallmark)`, `20K (833 BIS Hallmark)`, `18K (750 BIS Hallmark)`.
   * **Silver:** `92.5 Sterling Silver`, `Fine Silver (999 Purity)`.
2. **Size / Length:**
   * Ring Sizes: `5` to `15` (Standard Indian Ring Sizes).
   * Bangle Sizes: `2.2`, `2.4`, `2.6`, `2.8`.
   * Chain Length: `18 inch`, `20 inch`, `22 inch`, `24 inch`.

### B. Dynamic Pricing Attributes (Using Metafields & Backend API)
Because gold and silver prices fluctuate daily, the storefront will compute product prices dynamically:
* **Metal Weight (Grams):** `custom.metal_weight` (Decimal field).
* **Making Charges (Per Gram or Flat):** `custom.making_charges` (Decimal field).
* **Gemstone Weight (Carats):** `custom.gemstone_weight` (Decimal field, optional).
* **Gemstone Price:** `custom.gemstone_price` (Decimal field, optional).

#### Pricing Calculation Engine:
1. **Fetch Rates:** Fetch the live daily metal rates (Gold/Silver per gram for each purity level) from the backend database/API.
2. **Calculate Price:**
   $$\text{Subtotal} = (\text{Metal Weight} \times \text{Daily Metal Rate}) + \text{Making Charges} + \text{Gemstone Price}$$
3. **Add Taxes:** Add standard GST (typically 3% on precious metal jewelry) to calculate the final storefront display price.
4. **Discounts & Offers:** Apply any active promotional discounts/coupon codes, displaying the original vs. discounted price in both the storefront and the cart drawer.

---

## 4. Trust Badges & BIS Hallmark Signage
To establish online credibility for high-value purchases, we will integrate trust markers on the product details page:
* **BIS 916 Hallmark Logo** (For Gold)
* **BIS 999 Fine Silver Certificate Stamp** (For Silver bullion)
* **SGL/IGI Diamond Certification** (For diamond-encrusted jewelry)
* **Secure Insured Shipping Badge** (100% transit insurance cover)

