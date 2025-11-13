# ShopByCatagories
Shopyfy
<section class="shop-by-category">
  <div class="page-width">
    <h2 class="title">Shop by Category</h2>
    <div class="category-slider">
      {% for collection in collections %}
        <div class="category-item">
          <a href="{{ collection.url }}">
            <div class="category-image">
              <img src="{{ collection.image | img_url: 'medium' }}" alt="{{ collection.title }}">
            </div>
            <p>{{ collection.title }}</p>
          </a>
        </div>
      {% endfor %}
    </div>
  </div>
</section>

<style>
.shop-by-category {
  background: #fafafa;
  padding: 30px 0;
  border-radius: 12px;
}
.shop-by-category .title {
  font-weight: 700;
  font-size: 20px;
  margin-bottom: 15px;
}
.category-slider {
  display: flex;
  overflow-x: auto;
  gap: 20px;
  scroll-snap-type: x mandatory;
}
.category-item {
  flex: 0 0 auto;
  text-align: center;
  width: 120px;
  scroll-snap-align: start;
}
.category-item img {
  width: 100px;
  height: 100px;
  border-radius: 20px;
  background: white;
  box-shadow: 0 2px 6px rgba(0,0,0,0.1);
  object-fit: cover;
  margin-bottom: 8px;
}
.category-item p {
  font-size: 14px;
  font-weight: 600;
  color: #222;
}
.category-slider::-webkit-scrollbar {
  display: none;
}
</style>
