---
name: ohmypack-website
description: ใช้ skill นี้ทุกครั้งที่ผู้ใช้ต้องการออกแบบ แก้ไข หรือปรับปรุงเว็บไซต์ ohmypack.com ซึ่งสร้างด้วย WordPress + Avada Theme ครอบคลุมทั้งการแก้ไข CSS, PHP, HTML, Layout, หน้าสินค้า, หน้า Service, บทความ และการตั้งค่าต่างๆ ใน Avada Fusion Builder ให้ trigger skill นี้เมื่อผู้ใช้พูดถึง ohmypack, เครื่องรัดกล่อง, แก้เว็บ, ปรับหน้าเว็บ, เพิ่มสินค้า, แก้สี, แก้ Layout, แก้ข้อความ หรืองานใดๆ ที่เกี่ยวข้องกับเว็บไซต์นี้
aliases: [ohmypack, เว็บรัดกล่อง, avada ohmypack]
---

# OhMyPack Website Skill

## ข้อมูลเว็บไซต์

- **URL:** https://ohmypack.com
- **บริษัท:** บริษัท โอ้วมายแพ็ค จำกัด (OHMYPACK Co., Ltd.)
- **ธุรกิจ:** จำหน่ายและซ่อมเครื่องรัดกล่อง, สายรัดพลาสติก, อุปกรณ์แพ็คสินค้า
- **Platform:** WordPress + Avada Theme (Fusion Builder)
- **Plugin เพิ่มเติม:** WooCommerce (ระบบขายสินค้า), WP Rocket (Cache), GTM
- **ภาษาหลัก:** ภาษาไทย
- **เบอร์ติดต่อ:** 063-421-4082
- **Line:** @ohmypack

---

## โครงสร้างเว็บไซต์

### หน้าหลัก (Pages)
| หน้า | URL |
|------|-----|
| หน้าแรก | / |
| รับซ่อมเครื่องรัดกล่อง | /service/ |
| หมวดหมู่สินค้า | /shop/ |
| บทความ | /category/blog/ |
| ผลงานซ่อมเครื่อง | /portfolio/ |
| เกี่ยวกับเรา | /about-us/ |
| ติดต่อเรา | /contact-us/ |

### หมวดหมู่สินค้า (WooCommerce)
| หมวดหมู่ | URL |
|----------|-----|
| เครื่องรัดกล่องระบบแบตเตอรี่ | /battery/ |
| เครื่องรัดกล่องไต้หวัน | /strapping-machin-tw/ |
| เครื่องรัดกล่องจีน | /strapping-machin-chaina/ |
| สายรัด PET | /pet/ |
| สายรัดพลาสติก | /plastic-strap/ |
| กิ๊บล๊อคสายรัด | /lock-plastic/ |
| เครื่องรัดกล่องมือโยก | /tensioner/ |

---

## การแก้ไขเว็บไซต์ด้วย Avada

### วิธีเข้าถึง Fusion Builder
1. Login WordPress Admin: `https://ohmypack.com/wp-admin`
2. ไปที่หน้าที่ต้องการแก้ไข → คลิก **Edit with Fusion Builder**
3. หรือไปที่ Pages/Posts → เลือกหน้า → **Edit**

### วิธีแก้ไขที่นิยมใช้

#### 1. แก้ไขข้อความ/เนื้อหา
- คลิกที่ Element ที่ต้องการใน Fusion Builder
- แก้ไข Text ใน Text Block หรือ Heading element
- กด **Save** และ **Publish**

#### 2. แก้ไขสี / Typography
- ไปที่ **Avada > Theme Options > Typography** หรือ **Colors**
- หรือใช้ CSS Custom ผ่าน **Avada > Theme Options > Custom CSS**

#### 3. แก้ไขสินค้า (WooCommerce)
- **Products > All Products** → เลือกสินค้าที่ต้องการ
- แก้ชื่อ, ราคา, รูปภาพ, คำอธิบาย
- ใช้ Fusion Builder แก้ layout หน้าสินค้าเพิ่มเติม

---

## Custom CSS สำหรับ ohmypack.com

### วิธีเพิ่ม CSS
**ตำแหน่ง:** Avada > Theme Options > Advanced > Custom CSS

หรือผ่าน WordPress Customizer:
**Appearance > Customize > Additional CSS**

### ตัวอย่าง CSS ที่มักใช้บ่อย

```css
/* ปรับสีปุ่มหลัก */
.fusion-button.button-default {
    background-color: #YOUR_COLOR;
    border-color: #YOUR_COLOR;
}

/* ปรับขนาด Font หัวข้อ */
h1.fusion-title-heading {
    font-size: 36px;
}

/* ปรับสี Header */
#wrapper .fusion-header-wrapper {
    background-color: #YOUR_COLOR;
}

/* ปรับ Mobile Menu */
@media (max-width: 768px) {
    .fusion-mobile-nav-holder {
        background: #YOUR_COLOR;
    }
}

/* ซ่อน Element บน Mobile */
@media (max-width: 640px) {
    .hide-on-mobile {
        display: none !important;
    }
}
```

---

## การแก้ไขผ่าน WordPress Admin

### จัดการเนื้อหา
- **หน้าหลัก:** Pages > หน้าแรก > Edit with Fusion Builder
- **บทความ:** Posts > Blog > แก้ไข
- **ผลงานซ่อม:** Portfolio > แก้ไข

### จัดการสินค้า WooCommerce
```
Products > Add New
- Product name (ชื่อสินค้า)
- Product description (คำอธิบาย)
- Price (ราคา)
- Product image (รูปภาพหลัก)
- Product gallery (รูปภาพเพิ่มเติม)
- Product category (หมวดหมู่)
```

### ตั้งค่า Avada Theme Options
- **Avada > Theme Options > Colors** — สีหลักของเว็บ
- **Avada > Theme Options > Header** — ตั้งค่า Header
- **Avada > Theme Options > Footer** — ตั้งค่า Footer
- **Avada > Theme Options > Typography** — ฟอนต์และขนาด
- **Avada > Theme Options > Custom CSS** — CSS เพิ่มเติม

---

## Fusion Builder Elements ที่ใช้บ่อย

| Element | ใช้สำหรับ |
|---------|-----------|
| **Fusion Text** | ข้อความทั่วไป |
| **Fusion Title** | หัวข้อ H1-H6 |
| **Fusion Button** | ปุ่ม CTA |
| **Fusion Image** | รูปภาพ |
| **Fusion Columns** | จัดวาง Layout หลายคอลัมน์ |
| **Fusion Separator** | เส้นคั่น |
| **Fusion Slider** | Slider/Carousel รูปภาพ |
| **WooCommerce Products** | แสดงสินค้า |
| **Fusion Map** | แผนที่ Google Maps |
| **Fusion Contact Form** | ฟอร์มติดต่อ |

---

## PHP Snippets สำหรับ functions.php

> **วิธีเพิ่ม:** Appearance > Theme Editor > functions.php  
> หรือใช้ Plugin Code Snippets เพื่อความปลอดภัยกว่า

```php
// เพิ่มขนาดรูปภาพ Custom
add_image_size('ohmypack-product', 500, 500, true);

// แก้ข้อความใน WooCommerce (Thai)
add_filter('woocommerce_product_add_to_cart_text', function() {
    return 'เพิ่มในตะกร้า';
});

// ปรับ Excerpt length
add_filter('excerpt_length', function() {
    return 20; // จำนวนคำ
});
```

---

## ข้อมูลสำคัญสำหรับการแก้ไขเนื้อหา

### โทนสีและ Branding
- สีหลัก: ดูจาก Theme Options > Colors (ต้อง login เพื่อยืนยัน hex code)
- โลโก้: `https://ohmypack.com/wp-content/uploads/2026/08/OHM-logo-1-1-150x150.png`
- Favicon: `https://ohmypack.com/wp-content/uploads/2025/05/web-icon.png`

### ข้อความ CTA หลักของเว็บ
- โทรหาเรา: `tel:0634214082`
- Line: `https://line.me/R/ti/p/@ohmypack`

### SEO Meta Description (ปัจจุบัน)
```
ศูนย์รวมเครื่องรัดกล่องและเครื่องแพ็คกล่องทุกระบบ จำหน่ายสายรัดพลาสติก 
พร้อมบริการซ่อมด่วนโดยช่างมืออาชีพ มีเครื่องสำรองระหว่างซ่อม โทร 063-421-4082
```

---

## แนวทางการแก้ไขที่ดี

1. **สำรองข้อมูลก่อนแก้ไขทุกครั้ง** — ใช้ Plugin UpdraftPlus หรือ Duplicator
2. **ทดสอบบน Staging** ก่อน Push ขึ้น Production (ถ้ามี)
3. **Clear Cache หลังแก้ไข** — WP Rocket > Dashboard > Clear All Cache
4. **ทดสอบบนมือถือ** — เว็บนี้มีลูกค้าใช้งานจากมือถือจำนวนมาก
5. **ระวังการแก้ไข functions.php** — ผิดพลาดอาจทำให้เว็บล่ม ใช้ Code Snippets Plugin แทน

---

## การขอความช่วยเหลือจาก Claude

เมื่อใช้ skill นี้ ให้ระบุ:
1. **ต้องการแก้อะไร** — เช่น "แก้สีปุ่ม", "เพิ่มสินค้าใหม่", "ปรับ Layout หน้าแรก"
2. **หน้าไหน** — URL หรือชื่อหน้า
3. **แนบ Screenshot** — ถ้ามีปัญหาด้าน Visual
4. **Code ที่มีอยู่** — ถ้าต้องการแก้ไข CSS/PHP ที่มีอยู่แล้ว

Claude จะให้:
- Code CSS / PHP / HTML พร้อมคำอธิบาย
- ขั้นตอนการทำงานใน Avada Fusion Builder
- คำแนะนำ Step-by-step
- ทางเลือกหลายแบบให้เลือก
