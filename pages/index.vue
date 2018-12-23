<template>
  <v-layout
    column
    justify-center
    align-center
  >
    <v-flex
      xs12
      sm8
      md6
    >
      <div class="text-xs-center">
        <logo />
      </div>
      <v-container
        fluid
        grid-list-lg
      >
        <v-layout
          row
          wrap
        >
          <v-flex
            v-for="i in 6"
            :key="i"
            xs12
            md4
          >
            <course-card :course="course" />
          </v-flex>
        </v-layout>
      </v-container>
    </v-flex>
  </v-layout>
</template>

<script>
import Logo from '~/components/Logo.vue'
import CourseCard from '~/components/course/CourseCard'

import CoursesQuery from '~/graphql/queries/courses'

export default {
  components: {
    Logo,
    CourseCard
  },
  data() {
    return {
      course: {
        title: 'This is a course'
      },
      courses: []
    }
  },
  apollo: {
    courses: {
      query: CoursesQuery
    }
  }
}
</script>
