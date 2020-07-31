<template>
  <div>
    <h1>GraphQL-Request</h1>
    <TextField label="Request" :content="content" />
  </div>
</template>

<script>
import TextField from "./subComponents/TextField";

export default {
  props: ["selected", "bookId"],
  components: {
    TextField,
  },
  data: () => ({
    content: null,
  }),
  created: function () {
    this.setGraphQLSyntax();
  },
  methods: {
    setGraphQLSyntax() {
      this.content = `{
    bookById (id: "book-${this.bookId}") {`;

      if (this.selected.find((o) => o.name === "id")) {
        this.content += `
        id`;
      }
      if (this.selected.find((o) => o.name === "name")) {
        this.content += `
        name`;
      }
      if (this.selected.find((o) => o.name === "pageCount")) {
        this.content += `
        pageCount`;
      }
      if (
        this.selected.find(
          (o) =>
            o.name === "firstName" || o.name === "lastName" || o.name === "age"
        )
      ) {
        this.content += `
        author {`;
        if (this.selected.find((o) => o.name === "firstName")) {
          this.content += `
            firstName`;
        }
        if (this.selected.find((o) => o.name === "lastName")) {
          this.content += `
            lastName`;
        }
        if (this.selected.find((o) => o.name === "age")) {
          this.content += `
            age`;
        }
        this.content += `
        }`;
      }
      this.content += `
    }
}`;
    },
  },
  watch: {
    selected: function () {
      this.setGraphQLSyntax();
    },
    bookId: function () {
      this.setGraphQLSyntax();
    },
    content: function () {
      this.$emit("changedSDL", this.content);
    },
  },
};
</script>

<style></style>
