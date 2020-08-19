<template>
  <v-app>
    <div id="app">


      <v-form>
        <v-container>
          <h1>{{ title }}</h1>
           <!-- message error -->
           <div>
             <messages v-if="message" :message="message"/>
           </div>

            <!-- new note -->
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
                >New note</v-btn
              >
            </div>
            <!-- list notes -->
            <div>
              <v-list class="note" v-for="(note, index) in notes" :key="index">
                <v-list-item class="font-weight-black">{{
                  note.title
                }}</v-list-item>
                <v-list-item>{{ note.descr }}</v-list-item>
                <v-list-item>{{ note.date }}</v-list-item>
              </v-list>
            </div>
          </v-layout>
        </v-container>
      </v-form>
    </div>
  </v-app>
</template>

<script>
import Messages from "@/components/Messages.vue"
export default {
  name: "App",

  components: {
    Messages
  },

  data: () => ({
    title: "Notes App",
    message: null,
    note: {
      title: "",
      descr: "",
    },
    notes: [
      {
        title: "First Note",
        descr: "Description for first note",
        date: new Date(Date.now()).toLocaleString(),
      },
      {
        title: "Second Note",
        descr: "Description for second note",
        date: new Date(Date.now()).toLocaleString(),
      },
      {
        title: "Third Note",
        descr: "Description for third note",
        date: new Date(Date.now()).toLocaleString(),
      },
    ],
    //
  }),
  methods: {
    addNote() {
      // console.log(this.note)
      let { title, descr } = this.note;

      if (title === "") {
        this.message = "title can`t be blank!";
        return false;
      }

      this.notes.push({
        title,
        descr,
        date: new Date(Date.now()).toLocaleString(),
      });
      this.message = null;
      this.note.title = "";
      this.note.descr = "";
    },
  },
};
</script>
