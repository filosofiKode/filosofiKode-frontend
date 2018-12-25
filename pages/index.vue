<template>
  <div>
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
  </div>
</template>

<script>
import CourseCard from '~/components/course/CourseCard'

import coursesQuery from '~/graphql/queries/courses'

export default {
  components: {
    CourseCard
  },
  async asyncData({ app }) {
    let client = app.apolloProvider.defaultClient
    let { data } = await client.query({
      query: coursesQuery
    })
    return {
      courses: data.courses
    }
  },
  data() {
    return {
      courses: []
    }
  }
}
</script>
