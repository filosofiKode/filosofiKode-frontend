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
        <img 
          src="~/static/logo-filosofi-kode-square-transparent.png"
          alt="Folosofi Kode logo"
          width="200px"
        >
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
            v-for="course in courses"
            :key="course._id"
            xs12
            md4
          >
            <course-card
              :course="course" />
          </v-flex>
        </v-layout>
      </v-container>
    </v-flex>
  </v-layout>
</template>

<script>
import CourseCard from '~/components/course/CourseCard'

import CoursesQuery from '~/graphql/queries/courses'

export default {
  components: {
    CourseCard
  },
  data() {
    return {
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
