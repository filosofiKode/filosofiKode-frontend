<template>
  <v-container
    grid-list-md
    text-xs-center
  >
    <v-layout
      row
      wrap>
      <v-flex xs12>
        <h1>{{ course.title }}</h1>
        <span>oleh {{ course.instructors[0].name }}</span>
      </v-flex>
    </v-layout>
    <v-layout
      row
      wrap
    >
      <v-flex
        xs12
        md8
      >
        <youtube 
          :video-id="videoId"
          fit-parent/>
      </v-flex>
      <v-flex
        d-flex
        xs12
        sm4
      >
        <lesson-playlist :lessons="course.lessons"/>
      </v-flex>
    </v-layout>
  </v-container>
</template>
<script>
import LessonPlaylist from '~/components/lesson/LessonPlaylist'
import courseBySlugQuery from '~/graphql/queries/courses/by-slug'

export default {
  components: {
    LessonPlaylist
  },
  data() {
    return {
      course: {},
      videoId: 'lG0Ys-2d4MA',
      playerVars: {
        autoplay: 1
      }
    }
  },
  async asyncData({ app, params }) {
    let client = app.apolloProvider.defaultClient
    const { data } = await client.query({
      query: courseBySlugQuery,
      variables: {
        slug: params.slug
      }
    })
    return {
      course: data.courses[0] // we get the one and only data
    }
  }
}
</script>
