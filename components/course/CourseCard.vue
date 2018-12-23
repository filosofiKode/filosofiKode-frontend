<template>
  <v-card href="/courses/">
    <v-img
      src="https://cdn.vuetifyjs.com/images/cards/sunshine.jpg"
      height="200px"
    />

    <v-card-title primary-title>
      <div>
        <div class="headline">{{ course.title }}</div>
        <span class="grey--text">1,000 miles of wonder</span>
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
