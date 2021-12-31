<template>
  <HeadComponent></HeadComponent>
    <EditComponent></EditComponent>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component';
import HeadComponent from '@/components/HeadComponent.vue';
import EditComponent from '@/components/EditComponent.vue';// @ is an alias to /src

@Options({
  components: {
    HeadComponent,
    EditComponent,
  },
})
export default class Home extends Vue {}
</script>