<template>
  <div id="app" class="flex">
    <div class="w-1/4">
    </div>
    <CoursesTable
      class="mt-5 m-auto w-1/2"
      v-if="isCreate === false"
    >
    </CoursesTable>
    <CreateCourse
      class="mt-5 m-auto w-1/2"
      v-if="isCreate === true">
    </CreateCourse>
    <div class="w-1/4">
      <v-btn
        class="mt-10 mx-10"
        @click="isCreate = !isCreate"
      >
        Create Course
      </v-btn>
    </div>
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
    isCreate: false,
  }),
};
</script>

<style>
</style>
