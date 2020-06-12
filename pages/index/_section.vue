<template>
  <div class="section" :class="section">
    <h1>Section</h1>
    <h2>{{ section }}</h2>
  </div>
</template>

<script>
export default {
  name: 'Section',

  computed: {
    section () {
      return this.$route.params.section
    }
  }
}
</script>

<style>
.section {
  border: 1px solid teal;
  height: 500px;
  width: 500px;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
}
.section-a {
  background: teal;
}
.section-b {
  background: olive;
}
</style>
