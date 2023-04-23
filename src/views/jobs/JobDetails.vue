<template>
  <h1>Job details page</h1>
  <div v-if="job">
    <!-- <p>The job id is {{$route.params.id }}</p> -->
    <p>{{ job.title }}</p>
    <p>The job id is {{ id }}</p>
    <p>{{ job.details }}</p>
  </div>
  <div v-else> loading ... </div>
</template>

<script>
export default {
  props: ["id"],
  data() {
    return {
      job: null,
    };
  },
  mounted() {
    fetch("http://localhost:3000/jobs/" + this.id)
      .then((res) => res.json())
      .then((data) => (this.job = data))
      .catch((err) => console.log(err.message));
  },
};
</script>

<style>
</style>