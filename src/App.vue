<template>
  <v-app>
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
        :to="{name:'TodoList'}"
      >
        Todo List
      </v-btn>
      <v-btn
        text
        :to="{name:'TryTable'}"
      >
        Try Table
      </v-btn>
    </v-app-bar>

    <v-main>
      <router-view></router-view>
    </v-main>
  </v-app>
</template>

<script>

export default {
  name: 'App',

  data: () => ({
    //
  }),
};
</script>
