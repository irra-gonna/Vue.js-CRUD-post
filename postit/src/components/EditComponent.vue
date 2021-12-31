<template>
  <section>
    <div id="main-div-add">
      <ul id="form-ul">
        <li id="title-delt">{{ note.title }}</li>
        <li id="content-delt">{{ note.content }}</li>
        <div>
          <button id="button-dlte" @click="deleteNotes(note._id)">DELETE</button>
          <router-link id="button-dlt" v-bind:to="'/Edition/' + note._id">EDIT</router-link>
        </div>
      </ul>
    </div>
  </section>
</template>

<script>
import axios from "axios";
import { defineComponent } from "vue";

export default defineComponent({
  name: "EditComponent",
  mounted() {
    this.getNotes(this.$route.params.id);
  },
  data() {
    return {
      notesId: null,
      note: {
        content: "",
        title: "",
      },
    };
  },
  methods: {
    async getNotes(notesId) {
      console.log(notesId);
      try {
        const res = await axios.get(
          "http://5.135.119.239:3090/notes/" + notesId
        );
        this.note = res.data.note;
        console.log(res);
      } catch (error) {
        console.log(error);
      }
    },
    deleteNotes(notesId) {
      console.log("in delete function");
      axios.delete("http://5.135.119.239:3090/notes/" + notesId).then((res) => {
        console.log(res);
        this.$router.push("/");
        }).catch((error) => {
        console.log(error);
      });
    },
  },
});
</script>
