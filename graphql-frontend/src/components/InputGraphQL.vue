<template>
  <div>
    <v-row>
      <h1>Input</h1>
    </v-row>
    <v-row>
      <v-col cols="12">
        <v-combobox
          v-model="checkBoxSelected"
          :items="checkBox"
          label="Select a Book ID"
          outlined
          dense
          id="combo"
        ></v-combobox>
      </v-col>
    </v-row>
    <v-row>
      <v-treeview selectable open-all hoverable return-object :items="items" v-model="selected"></v-treeview>
    </v-row>
  </div>
</template>

<script>
export default {
  data: () => ({
    selected: [],
    checkBoxSelected: 1,
    checkBox: [1, 2, 3],
    items: [
      {
        id: 1,
        name: "id",
      },
      {
        id: 2,
        name: "name",
      },
      {
        id: 3,
        name: "pageCount",
      },
      {
        id: 4,
        name: "Author :",
        children: [
          { id: 5, name: "firstName" },
          { id: 6, name: "lastName" },
          { id: 7, name: "age" },
        ],
      },
    ],
  }),
  watch: {
    selected: function () {
      this.$emit("selectedChanged", this.selected);
    },
    checkBoxSelected: function () {
      this.$emit("bookChanged", this.checkBoxSelected);
    },
  },
};
</script>

<style>
#id {
  width: "50%";
}
</style>
