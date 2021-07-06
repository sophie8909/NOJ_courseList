<template>
  <div id="app">
    <CoursesTable class="mt-5 m-auto w-1/2"></CoursesTable>
    <CreateCourse class="mt-5 m-auto w-1/2"></CreateCourse>
  </div>
</template>

<script>
import CoursesTable from '../components/CoursesTable.vue';
import CreateCourse from '../components/CreateCourse.vue';

export default {
  name: 'Courses',
  components: {
    CoursesTable,
    CreateCourse,
  },
  data: () => ({
  }),
};
</script>

<style>
</style>
