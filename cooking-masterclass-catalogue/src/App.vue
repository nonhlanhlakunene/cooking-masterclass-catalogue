<template>
  <div id="app">
    <Header :wishlistCount="wishlist.length" />
    <main class="container">
      <div class="filters">
        <label>Filter: </label>
        <select v-model="filterSelection">
          <option value="all">All Modules</option>
          <option value="available">Available Only</option>
        </select>
      </div>
      
      <CourseList 
        :courses="visibleCourses" 
        :wishlist="wishlist"
        @toggle-wishlist="toggleWishlistItem"
      />
    </main>
  </div>
</template>

<script>
import Header from './components/Header.vue';
import CourseList from './components/CourseList.vue';
import { courseData } from './courses';

export default {
  name: 'App',
  components: { Header, CourseList },
  data() {
    return {
      courses: courseData,
      wishlist: [],
      filterSelection: 'all'
    };
  },
  computed: {
    visibleCourses() {
      if (this.filterSelection === 'available') {
        return this.courses.filter(c => c.isAvailable);
      }
      return this.courses;
    }
  },
  methods: {
    toggleWishlistItem(id) {
      const position = this.wishlist.indexOf(id);
      if (position === -1) {
        this.wishlist.push(id);
      } else {
        this.wishlist.splice(position, 1);
      }
    }
  }
}
</script>

<style>
body { margin: 0; font-family: sans-serif; background: #f8f9fa; }
.container { max-width: 1200px; margin: 0 auto; padding: 20px; }
.filters { margin: 20px 0 0 0; }
.filters select { padding: 6px; border-radius: 4px; }
</style>

