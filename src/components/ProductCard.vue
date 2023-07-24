<template>
  <div
    class="product-card"
    :class="{ hovered: isHovered }"
    @mouseover="isHovered = true"
    @mouseout="isHovered = false"
  >
    <div class="product-image">
      <img :src="selectedImage" :alt="product.name" />
      <div class="color-bar">
        <div
          v-for="(color, index) in product.colors"
          :key="index"
          :style="{ 'background-color': color }"
          class="color-circle"
          @mouseover="changeImage(index)"
        ></div>
      </div>
    </div>
    <div class="product-details">
      <h3 class="product-name">{{ product.name }}</h3>
      <p class="product-description">{{ product.description }}</p>
      <p class="product-price">{{ product.price }}</p>
      <button class="product-button">Buy Now</button>
      <a class="product-link">Learn more ></a>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    product: {
      type: Object,
      required: true,
    },
  },
  data() {
    return {
      isHovered: false,
      selectedImage: this.product.image,
    };
  },
  methods: {
    changeImage(index) {
      this.selectedImage = this.product.images[index];
    },
  },
};
</script>


<style lang="scss" scoped>
.product-card {
  width: 300px;
  border-radius: 10px;
  background-color: #fff;
  padding: 20px;
  border-bottom: 1px solid lightgray;
  transition: all 0.3s ease;
  display: inline-block;
  margin: 5px;
  color: #000;

  &:hover {
    border: 2px solid #0071e3;
    box-shadow: 0 0px 0px rgba(0, 0, 0, 0);
  }
}

.product-image {
  position: relative;
  cursor: pointer;
}

.product-image img {
  width: 80%;
  height: auto;
  transition: all 0.5s ease;

  &:hover {
    width: 100%;
  }
}

.color-bar {
  display: flex;
  justify-content: center;
  margin-top: 10px;
}

.color-circle {
  width: 20px;
  height: 20px;
  border-radius: 50%;
  margin: 0 5px;
}

.product-details {
  margin-top: 20px;
}

.product-name {
  font-size: 24px;
  font-weight: bold;
}

.product-description {
  font-size: 18px;
}

.product-price {
  margin-top: 40px;
  font-size: 14px;
}

.product-button {
  padding: 10px 20px;
  background-color: #000;
  color: #fff;
  border: none;
  border-radius: 25px;
  box-shadow: 0 4px 4px rgba(0, 0, 0, 0.5);
  transition: all 0.3s ease;
  font-weight: bold;

  &:hover {
    font-size: 18px;
    background: #0071e3;
    box-shadow: none;
    border-radius: 10px;
    padding: 10px 50px;
    cursor: pointer;
  }
}

.product-link {
  display: block;
  margin: 20px 0;
  font-size: 14px;
  color: #0071e3;

  &:hover {
    text-decoration: underline;
    cursor: pointer;
  }
}
</style>