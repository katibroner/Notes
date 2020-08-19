<template>
  <div>
    <v-layout column wrap>
      <v-flex xs12 sm6 md3>
        <v-text-field v-model="note.title" type="text"></v-text-field>
      </v-flex>
      <v-flex xs12 sm6 md3>
        <v-text-field v-model="note.descr"></v-text-field>
      </v-flex>
      <!-- button -->
      <div class="text-center">
        <v-btn rounded color="primary" dark @click="addNote"
        >New note
        </v-btn>
      </div>
    </v-layout>
  </div>

</template>

<script>
export default {
name: "NewNote",
  props:{
    note:{
      type: Object,
      required: true
    }
  },
  methods:{
    addNote(){
      this.$emit('newNote', this.note)
    }
  }

}
</script>

<style scoped>

</style>
