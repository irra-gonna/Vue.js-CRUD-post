<template>
  <div>
    <HeadComponent></HeadComponent>
  </div>
  <section>
    <body >
      <div class="grid">
        <div  v-for="(note, index) in notes" :key="index">
          <div id="content-div">
            <ul id="ul">
              <li id="title">{{ note.title }}</li>
              <li id="content">{{ note.content }}</li>
              <router-link v-bind:to="'/Edit/' + note._id">MORE</router-link>
            </ul>
          </div>
        </div>
      </div>
    </body >
  </section>
</template>

<script lang='ts'>
import HeadComponent from "@/components/HeadComponent.vue";

import axios from "axios";
import { defineComponent } from "vue";

export default defineComponent({
  name: "home",
  components: {
    HeadComponent,
  },
  data(): { notes: { _id: string; title: string; content: string[] }[] } {
    return {
      notes: [],
    };
  },
  mounted() {
    this.getAll();
  },
  methods: {
    async getAll() {
      const response = await axios.get<{
        notes: { _id: string; title: string; content: string[] }[];
      }>("http://5.135.119.239:3090/notes");
      this.notes = response.data.notes;
    },
  },
});
</script>

