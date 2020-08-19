<template>
  <v-app>
    <div id="app">


      <v-form>
        <v-container>
          <h1>{{ title }}</h1>
          <!-- module message error -->
          <div>
            <messages v-if="message" :message="message"/>
          </div>
          <!-- module new note-->
          <div>
            <NewNote
                :note="note"
                @newNote="addNote"

            />
          </div>

          <!-- new note -->


          <!-- list notes -->
          <div>
            <v-list class="note" v-for="(note, index) in notes" :key="index">
              <v-list-item class="font-weight-black">{{
                  note.title
                }}
              </v-list-item>
              <v-list-item>{{ note.descr }}</v-list-item>
              <v-list-item>{{ note.date }}</v-list-item>
            </v-list>
          </div>

        </v-container>
      </v-form>
    </div>
  </v-app>
</template>

<script>
import Messages from "@/components/Messages.vue"
import NewNote from "@/components/NewNote.vue"

export default {
  name: "App",

  components: {
    Messages,
    NewNote
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
      let {title, descr} = this.note;

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
