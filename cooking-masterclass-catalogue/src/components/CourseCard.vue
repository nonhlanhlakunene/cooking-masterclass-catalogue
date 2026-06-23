<template>
  <div class="course-card" :class="{ 'sold-out': !course.isAvailable }">
    <div class="card-image">
      <div v-if="!course.isAvailable" class="sold-out-overlay">SOLD OUT</div>
      <span class="icon">🍳</span>
    </div>
    <div class="card-body">
      <span class="level">{{ course.level }}</span>
      <h3>{{ course.title }}</h3>
      <p>Chef: {{ course.chef }}</p>
      <div class="card-footer">
        <span class="price">R {{ course.price }}</span>
        <button 
          :disabled="!course.isAvailable" 
          @click="$emit('toggle-wishlist', course.id)"
          :class="{ 'saved': isSaved }"
        >
          {{ isSaved ? '❤️ Saved' : '🤍 Save' }}
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CourseCard',
  props: {
    course: {
      type: Object,
      required: true
    },
    isSaved: {
      type: Boolean,
      default: false
    }
  }
}
</script>

<style scoped>
.course-card {
  background: white;
  border-radius: 8px;
  overflow: hidden;
  box-shadow: 0 4px 10px rgba(0,0,0,0.05);
  display: flex;
  flex-direction: column;
  position: relative;
}
.sold-out { opacity: 0.6; }
.card-image {
  height: 140px;
  background: #f0f0f0;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 3rem;
}
.sold-out-overlay {
  position: absolute;
  top: 0; left: 0; right: 0; bottom: 0;
  background: rgba(231, 76, 60, 0.8);
  color: white;
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: bold;
}
.card-body { padding: 15px; flex-grow: 1; display: flex; flex-direction: column; }
.level { font-size: 0.8rem; color: #e67e22; font-weight: bold; }
.card-footer { margin-top: auto; display: flex; justify-content: space-between; align-items: center; padding-top: 15px; }
.price { font-weight: bold; font-size: 1.2rem; }
button { padding: 6px 12px; border-radius: 4px; border: 1px solid #ccc; cursor: pointer; background: white; }
button.saved { background: #ffebee; border-color: #e74c3c; color: #e74c3c; }
button:disabled { cursor: not-allowed; background: #eee; color: #aaa; }
</style>
