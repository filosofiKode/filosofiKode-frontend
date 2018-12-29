<template>
  <v-list 
    v-if="isLessonExist"
    two-line>
    <v-subheader>
      Playlist
    </v-subheader>
    <div
      v-for="(lesson, index) in lessons"
      :key="lesson._id">
      <v-list-tile
        nuxt
        to="/"> 
        <v-list-tile-action>
          {{ index + 1 }}.
        </v-list-tile-action>
        <v-list-tile-content>
          <v-list-tile-title>{{ lesson.title }}</v-list-tile-title>
          <v-list-tile-sub-title>4 menit</v-list-tile-sub-title>
        </v-list-tile-content>
      </v-list-tile>
      <v-divider inset/>
    </div>
  </v-list>
</template>
<script>
import _isEmpty from 'lodash/isEmpty'

export default {
  name: 'LessonList',
  props: {
    lessons: {
      type: Array,
      required: true
    }
  },
  computed: {
    isLessonExist() {
      return !_isEmpty(this.lessons)
    }
  }
}
</script>
