<template>
  <header class="app-header">
    <h1>🍳 Cooking Masterclass</h1>
    <div class="wishlist-badge">
      ❤️ Wishlist: {{ wishlistCount }}
    </div>
  </header>
</template>

<script>
export default {
  name: "AppHeader",
  props: {
    wishlistCount: {
      type: Number,
      required: true
    }
  }
}
</script>

<style scoped>
.app-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: #2c7a4b;
  color: white;
  padding: 16px 32px;
}

.app-header h1 {
  font-size: 1.4rem;
  margin: 0;
}

.wishlist-badge {
  background-color: white;
  color: #2c7a4b;
  font-weight: bold;
  padding: 6px 14px;
  border-radius: 20px;
  font-size: 0.95rem;
}
</style>
