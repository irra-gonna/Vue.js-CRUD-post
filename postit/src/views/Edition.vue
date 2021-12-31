<template>
  <section>
    <HeadComponent></HeadComponent>
    <div id="main-div-add">
      <form id="form">
        <div>
          <input id="title-add" v-model="note.title" placeholder="Title" required />
        </div>
        <textarea id="content-add" v-model="note.content" placeholder="Content" required />
        <button id="button" @click.prevent="sendPut()">EDIT POST</button>
      </form>
    </div>
  </section>
</template>


<script>
import axios from "axios";
import HeadComponent from "@/components/HeadComponent.vue";
import { defineComponent } from "vue";

export default defineComponent({
  name: "Edition",
  components: {
    HeadComponent,
  },
  mounted() {
    this.getNotes(this.$route.params.id);
  },
  data() {
    return {
      notesId: null,
      note: [],
    };
  },
  methods: {
    async getNotes(notesId) {
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
    sendPut() {
      const post = {
        title: this.note.title,
        content: this.note.content,
      };

    axios
        .put(`http://5.135.119.239:3090/notes/${this.$route.params.id}`, post)
        .then((result) => {
          console.log(result);
          console.log(this.note.title);
          this.$router.push("/");
          }).catch((error) => {
          console.log(error);
        });
    },
  },
});
</script>