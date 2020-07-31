<template>
  <div>
    <h1>JSON-Response</h1>
    <TextField label="Response" content="Comming Soon" />
  </div>
</template>

<script>
import TextField from "./subComponents/TextField";
// import gql from "graphql-tag";

export default {
  components: { TextField },
  props: ["request"],
  data: () => ({
    response: null,
  }),
  watch: {
    request: function (newVal) {
      // eslint-disable-next-line no-console
      console.log(`${newVal}`);
      // this.$apollo
      //   .query(
      //     gql`
      //       ${newVal}
      //     `
      //   )
      //   // eslint-disable-next-line no-console
      //   .then((succ) => console.log(succ))
      //   // eslint-disable-next-line no-console
      //   .catch((err) => console.log(err.mesage));
    },
  },
};
</script>

<style></style>
