<template>
  <div>
    <h1>JSON-Response</h1>
    <TextField v-if="!response" label="Response" content="No Content" />
    <TextField v-else label="Response" :content="response" />
  </div>
</template>

<script>
import TextField from "./subComponents/TextField";
import axios from "axios";

export default {
  components: { TextField },
  props: ["request"],
  data: () => ({
    response: null,
  }),
  watch: {
    request: function(query) {
      let body = {
        query: query,
        variables: {},
      };

      axios
        .post("http://localhost:8080/graphql", body)
        .then((succ) => (this.response = JSON.stringify(succ.data, null, "\t")))
        .catch((err) => (this.response = err.message));
    },
  },
};
</script>

<style></style>
