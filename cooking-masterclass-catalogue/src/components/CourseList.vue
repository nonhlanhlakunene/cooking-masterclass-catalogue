<template>
  <div class="course-list-grid">
    <CourseCard 
      v-for="item in courses" 
      :key="item.id" 
      :course="item"
      :isSaved="wishlist.includes(item.id)"
      @toggle-wishlist="$emit('toggle-wishlist', $event)"
    />
  </div>
</template>

<script>
import CourseCard from './CourseCard.vue';

export default {
  name: 'CourseList',
  components: { CourseCard },
  props: {
    courses: {
      type: Array,
      required: true
    },
    wishlist: {
      type: Array,
      required: true
    }
  }
}
</script>

<style scoped>
.course-list-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
  gap: 20px;
  padding: 20px 0;
}
</style>
