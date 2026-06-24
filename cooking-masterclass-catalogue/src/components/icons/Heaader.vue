<template>
  <header class="header">
    <h1>🍳 Cooking Masterclass</h1>
    <div class="wishlist">
      <span>❤️ Wishlist: {{ wishlistCount }}</span>
    </div>
  </header>
</template>

<script>
export default {
  name: 'Header',
  props: {
    wishlistCount: {
      type: Number,
      default: 0
    }
  }
}
</script>

<style scoped>
.header {
  background: #2c3e50;
  color: white;
  padding: 20px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.wishlist {
  font-size: 1.2rem;
}
</style>