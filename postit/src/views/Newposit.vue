<template>
  <HeadComponent></HeadComponent>
  <AddComponent></AddComponent>
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";
import AddComponent from "@/components/AddComponent.vue";
import HeadComponent from "@/components/HeadComponent.vue"; // @ is an alias to /src

@Options({
  components: {
    AddComponent,
    HeadComponent,
  },
})
export default class Home extends Vue {}
</script>

