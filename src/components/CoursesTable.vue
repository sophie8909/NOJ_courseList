<template>
    <v-card>
      <v-data-table
        :headers="headers"
        :items="courses"
        :loading="isLoading"
        hide-default-footer
      ></v-data-table>
    </v-card>
</template>

<script>
const headers = [
  {
    text: 'Course',
    align: 'start',
    filterable: false,
    value: 'name',
    width: '40%',
  },
  { text: 'Term', value: 'term', width: '10%' },
  { text: 'Teacher', value: 'teacher', width: '20%' },
  { text: 'Enrolled as', value: 'role', width: '20%' },
];
export default {
  data: () => ({
    isLoading: false,
    item_key: 'name',
    headers,
    courses: [
      {
        name: '程式設計（一）',
        term: 109,
        teacher: '紀博文',
        role: 'Student',
      },
      {
        name: '資料結構',
        term: 110,
        teacher: '柯佳伶',
        role: 'Student',
      },
      {
        name: '演算法',
        term: 109,
        teacher: '葉梅珍',
        role: 'Student',
      },
    ],
  }),
};
</script>

<style lang="css" scoped>

</style>
