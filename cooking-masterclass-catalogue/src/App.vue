<template>
  <div>
    <AppHeader :wishlistCount="wishlistCount" />

    <main class="catalogue">
      <h2 class="section-title">Available Courses</h2>
      <div class="card-grid">
        <CourseCard
          v-for="course in courses"
          :key="course.id"
          :course="course"
          @save-course="addToWishlist"
        />
      </div>
    </main>
  </div>
</template>

<script>
import AppHeader from "./components/AppHeader.vue"
import CourseCard from "./components/CourseCard.vue"
import courses from "./courses.js"

export default {
  name: "App",
  components: {
    AppHeader,
    CourseCard
  },
  data() {
    return {
      courses: courses,
      wishlistCount: 0
    }
  },
  methods: {
    addToWishlist() {
      this.wishlistCount++
    }
  }
}
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
  font-family: "Segoe UI", sans-serif;
}

body {
  background-color: #f4f7f4;
}

.catalogue {
  max-width: 1100px;
  margin: 0 auto;
  padding: 32px 16px;
}

.section-title {
  font-size: 1.5rem;
  color: #1a1a1a;
  margin-bottom: 24px;
}

.card-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
  gap: 24px;
}
</style>
