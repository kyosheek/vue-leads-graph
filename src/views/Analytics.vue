<template>
  <div class="analytics">
    <h1>Analytics</h1>
    <h2>Analytics for visits</h2>
    <Graph />
  </div>
</template>

<script>
// @ is an alias to /src
import Graph from '@/components/Graph.vue';

export default {
  name: 'Analyics',
  components: {
    Graph,
  },
};
</script>
