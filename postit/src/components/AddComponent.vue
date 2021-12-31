<template>
  <section>
    <div id="main-div-add">
      <form id="form">
        <div>
        <input id="title-add" v-model="title" placeholder="Title" required />
        </div>
        <textarea id="content-add" v-model="content" placeholder="Content" required />
        <button id="button" @click.prevent="sendPost()">SUBMIT</button>
      </form>
    </div>
  </section>
</template>

<script>
import axios from "axios";

export default {
  name: "AddComponent",
  data: function () {
    return {
      title: "",
      content: "",
    };
  },
  methods: {
    sendPost() {
      const postData = { title: this.title, content: this.content };
      axios.post("http://5.135.119.239:3090/notes", postData).then((res) => {
        console.log(res.content);
        this.$router.push('/');
        }).catch((error) => {
        console.log(error);
      });
    },
  },
};
</script>