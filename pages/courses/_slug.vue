<template>
  <div>
    <h1>{{ course.title }}</h1>
    <span>oleh {{ course.instructors[0].name }}</span>
  </div>
</template>
<script>
import courseBySlugQuery from '~/graphql/queries/course-by-slug'
export default {
  data() {
    return {
      course: {}
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
