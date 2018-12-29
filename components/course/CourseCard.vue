<template>
  <v-card 
    :to="{ name: 'courses-slug', params: { slug: course.slug }}"
    flat
    hover>
    <v-img
      src="https://cdn.vuetifyjs.com/images/cards/sunshine.jpg"
      height="200px"
    />

    <v-card-title primary-title>
      <div>
        <div class="headline">{{ course.title }}</div>
        <span class="grey--text">{{ course.description }}</span>
      </div>
    </v-card-title>

    <v-card-actions>
      <v-btn flat>Pelajari</v-btn>
      <v-spacer/>
    </v-card-actions>
  </v-card>
</template>
<script>
export default {
  props: {
    course: {
      type: Object,
      required: true
    }
  }
}
</script>
