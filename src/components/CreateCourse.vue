<template>
  <v-card>
      <v-card-title>
        Create Course
      </v-card-title>
    <div class="mx-10 mb-10">
      <validation-observer
          ref="observer"
          v-slot="{ invalid }"
      >
        <form @submit.prevent="submit">
        <validation-provider
            v-slot="{ errors }"
            name="courseName"
            rules="required|max:20"
        >
            <v-text-field
            v-model="course_name"
            :counter="20"
            :error-messages="errors"
            label="Course Name"
            required
            ></v-text-field>
        </validation-provider>
        <validation-provider
            v-slot="{ errors }"
            name="teacher"
            rules="required|max:10"
        >
            <v-text-field
            v-model="teacher"
            :error-messages="errors"
            label="Teacher"
            :counter="10"
            required
            ></v-text-field>
        </validation-provider>
        <validation-provider
            v-slot="{ errors }"
            name="Term"
            rules="required"
        >
            <v-select
            v-model="term"
            :items="items"
            :error-messages="errors"
            label="Term"
            data-vv-name="term"
            required
            ></v-select>
        </validation-provider>
        <v-btn
            class="mr-4"
            type="submit"
            :disabled="invalid"
        >
            submit
        </v-btn>
        <v-btn @click="clear">
            clear
        </v-btn>
        </form>
      </validation-observer>
    </div>
  </v-card>
</template>

<script>
import {
  required, max,
} from 'vee-validate/dist/rules';
import {
  extend, ValidationObserver, ValidationProvider, setInteractionMode,
} from 'vee-validate';

setInteractionMode('eager');

extend('required', {
  ...required,
  message: '{_field_} can not be empty',
});

extend('max', {
  ...max,
  message: '{_field_} may not be greater than {length} characters',
});

export default {
  components: {
    ValidationProvider,
    ValidationObserver,
  },
  data: () => ({
    course_name: '',
    teacher: '',
    term: null,
    items: [
      '110-1',
      '110-2',
    ],
  }),

  methods: {
    submit() {
      this.$refs.observer.validate();
    },
    clear() {
      this.course_name = '';
      this.teacher = '';
      this.term = null;
      this.$refs.observer.reset();
    },
  },
};
</script>

<style lang="css" scoped>

</style>
