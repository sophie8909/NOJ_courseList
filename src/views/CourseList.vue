<template>
  <div id="app">
    <CoursesTable></CoursesTable>
  </div>
</template>

<script>
import CoursesTable from '../components/CoursesTable.vue';

export default {
  name: 'Courses',
  components: {
    CoursesTable,
  },
  data: () => ({
  }),
};
</script>

<style>
</style>
