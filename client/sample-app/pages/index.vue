<template>
  <div>
    <Tutorial />
    <button @click="fetchData()">fetch</button>
  </div>
</template>

<script>
export default {
  methods: {
    async fetchData() {
      try {
        const resp = await this.$axios.$get(
          "http://localhost:8080/api/test?test=aaaa"
        );
        console.log(resp);
      } catch (e) {
        console.log(e);
      }
    }
  }
};
</script>
