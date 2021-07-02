<template>
  <div class="home">
    <v-app-bar
      app
      color="primary"
      dark
    >
      <v-btn
        text
        exact
        :to="{name:'Home'}"
      >
        Home
      </v-btn>
      <v-btn
        text
        :to="{name:'CourseList'}"
      >
        Courses
      </v-btn>
    </v-app-bar>

    <v-main>
      <router-view></router-view>
    </v-main>
  </div>
</template>

<script>
export default {

};
</script>

<style>

</style>
