# Shopify Category Slider Section

This is a **custom Shopify section** for displaying a category slider with the following features:

- Editable heading
- Title editable per block
- Optional icon/image
- Autoplay 2.5 sec
- Right-to-left scroll (RTL)
- Hover zoom effect
- No arrows
- Icon size 60px
- Max 20 icons
- 10 icons visible on desktop, 3 icons on mobile/tablet
- Clean solid card design
- Fully Shopify compatible, no Liquid errors

---

## Screenshot / Cover

![Category Slider Screenshot](./assets/category-slider-screenshot.png)

> Make sure to place your screenshot in the `assets` folder of your repo.  
> Replace `category-slider-screenshot.png` with your actual screenshot file name.

---

## Code

```liquid
{% schema %}
{
  "name": "Shop by Category Slider",
  "settings": [
    { "type": "text", "id": "heading", "label": "Heading", "default": "Shop by Category" }
  ],
  "blocks": [
    {
      "type": "category",
      "name": "Category Item",
      "settings": [
        { "type": "image_picker", "id": "icon", "label": "Category Icon / Image" },
        { "type": "text", "id": "title", "label": "Category Title", "default": "Category Name" },
        { "type": "url", "id": "link", "label": "Category Link" }
      ]
    }
  ],
  "max_blocks": 20,
  "presets": [ { "name": "Shop by Category Slider", "category": "Custom" } ]
}
{% endschema %}

<div class="category-wrapper" style="padding:20px;">
  <h2 style="text-align:center; color:#000;">{{ section.settings.heading }}</h2>
  <div class="swiper category-swiper" style="padding:20px 0;">
    <div class="swiper-wrapper">
      {% for block in section.blocks %}
        <div class="swiper-slide">
          <a href="{{ block.settings.link }}" class="glass-card">
            {% if block.settings.icon != blank %}
              <img src="{{ block.settings.icon | img_url: '200x200' }}" class="category-icon" alt="{{ block.settings.title }}">
            {% endif %}
            <p class="category-title">{{ block.settings.title }}</p>
          </a>
        </div>
      {% endfor %}
    </div>
  </div>
</div>

<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/swiper@10/swiper-bundle.min.css"/>
<script src="https://cdn.jsdelivr.net/npm/swiper@10/swiper-bundle.min.js"></script>

<style>
.glass-card {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 10px;
  padding: 16px;
  border-radius: 12px;
  background: #fff;
  border: 1px solid #e0e0e0;
  text-decoration: none;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}
.glass-card:hover { transform: translateY(-3px) scale(1.05); box-shadow: 0 6px 15px rgba(0,0,0,0.1); }
.category-icon { width: 60px; height: 60px; object-fit: contain; transition: transform 0.3s ease; }
.glass-card:hover .category-icon { transform: scale(1.2); }
.category-title { font-size: 14px; font-weight: 600; color: #000; margin-top: 4px; text-align: center; }
</style>

<script>
document.addEventListener('DOMContentLoaded', function() {
  new Swiper('.category-swiper', {
    slidesPerView: 10,
    spaceBetween: 15,
    loop: true,
    rtl: true,
    autoplay: { delay: 2500, disableOnInteraction: false },
    navigation: false,
    breakpoints: {
      0: { slidesPerView: 3, spaceBetween: 8 },
      480: { slidesPerView: 3, spaceBetween: 10 },
      1024: { slidesPerView: 10, spaceBetween: 15 }
    },
  });
});
</script>
