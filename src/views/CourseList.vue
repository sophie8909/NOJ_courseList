<template>
  <div id="app" class="flex">
    <div class="w-1/4">
    </div>
    <div class="w-1/2">
    <CoursesTable
      class="mt-5 m-auto"
      v-if="isCreating === false"
    >
    </CoursesTable>
    <CreateCourse
      class="mt-5 m-auto"
      v-if="isCreating === true">
    </CreateCourse>
    <v-alert
        prominent
        type="error"
        v-if="isChecking"
        class="mt-5"
      >
        <v-row align="center">
          <v-col class="grow">
            是否取消建立課程
          </v-col>
          <v-col class="shrink flex">
            <v-btn @click="isChecking = false, isCreating = false">是</v-btn>
            <v-btn @click="isChecking = false" class="ml-1">否</v-btn>
          </v-col>
        </v-row>
     </v-alert>
    </div>
    <div class="w-1/4">
      <v-btn
        class="mt-10 mx-10"
        @click="switchcreator"
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
    isCreating: false,
    isChecking: false,
  }),
  methods: {
    switchcreator() {
      if (!this.isCreating) {
        this.isCreating = true;
      } else {
        this.isChecking = true;
      }
    },
  },
};
</script>

<style>
</style>
