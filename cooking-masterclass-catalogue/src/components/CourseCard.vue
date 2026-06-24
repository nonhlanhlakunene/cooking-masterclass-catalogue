<template>
  <div class="course-card" :class="{ 'sold-out': !course.available }">
    <img :src="course.image" :alt="course.title" class="course-image" />

    <div class="card-header">
      <span class="level-badge">{{ course.level }}</span>
      <span v-if="!course.available" class="sold-out-label">Sold Out</span>
    </div>

    <h2 class="course-title">{{ course.title }}</h2>
    <p class="chef-name">👨‍🍳 {{ course.chef }}</p>
    <p class="price">R {{ course.price }}</p>

    <button
      class="save-btn"
      :disabled="!course.available || saved"
      @click="saveCourse"
    >
      {{ saved ? "Saved ✓" : "Save to Wishlist" }}
    </button>
  </div>
</template>

<script>
export default {
  name: "CourseCard",
  props: {
    course: {
      type: Object,
      required: true
    }
  },
  emits: ["save-course"],
  data() {
    return {
      saved: false
    }
  },
  methods: {
    saveCourse() {
      this.saved = true
      this.$emit("save-course")
    }
  }
}
</script>

<style scoped>
.course-card {
  background-color: white;
  border-radius: 10px;
  overflow: hidden;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.course-image {
  width: 100%;
  height: 180px;
  object-fit: cover;
}

.course-card.sold-out {
  opacity: 0.6;
}

.card-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 16px;
}

.level-badge {
  background-color: #e8f5e9;
  color: #2c7a4b;
  padding: 4px 10px;
  border-radius: 12px;
  font-size: 0.8rem;
  font-weight: bold;
}

.sold-out-label {
  background-color: #fdecea;
  color: #c0392b;
  padding: 4px 10px;
  border-radius: 12px;
  font-size: 0.8rem;
  font-weight: bold;
}

.course-title {
  font-size: 1.1rem;
  margin: 0;
  color: #1a1a1a;
  padding: 0 16px;
}

.chef-name {
  color: #555;
  margin: 0;
  font-size: 0.9rem;
  padding: 0 16px;
}

.price {
  font-size: 1.2rem;
  font-weight: bold;
  color: #2c7a4b;
  margin: 0;
  padding: 0 16px;
}

.save-btn {
  margin: 0 16px 16px 16px;
  padding: 10px;
  border: none;
  border-radius: 6px;
  background-color: #2c7a4b;
  color: white;
  font-size: 0.95rem;
  cursor: pointer;
}

.save-btn:disabled {
  background-color: #aaa;
  cursor: not-allowed;
}
</style>