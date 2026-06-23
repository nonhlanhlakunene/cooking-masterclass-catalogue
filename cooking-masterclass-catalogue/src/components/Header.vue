<template>
  <header class="page-header">
    <div class="header-container">
      <h1>Cooking <span class="highlight">Masterclass</span></h1>
      <div class="wishlist-badge">
        <span>❤️ Wishlist: {{ wishlistCount }}</span>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  name: 'Header',
  props: {
    wishlistCount: {
      type: Number,
      required: true
    }
  }
}
</script>

<style scoped>
.page-header {
  background-color: #2c3e50;
  color: white;
  padding: 20px;
  box-shadow: 0 4px 6px rgba(0,0,0,0.1);
}
.header-container {
  max-width: 1200px;
  margin: 0 auto;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.highlight {
  color: #e67e22;
}
.wishlist-badge {
  background: rgba(255, 255, 255, 0.1);
  padding: 8px 16px;
  border-radius: 20px;
  font-weight: bold;
}
</style>
