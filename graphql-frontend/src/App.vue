<template>
  <v-app id="app">
    <v-main>
      <v-row>
        <v-col cols="2">
          <InputGraphQL @selectedChanged="changeSelected" @bookChanged="bookChanged" />
        </v-col>
        <v-col cols="1" align-self="center">
          <span class="charFont">></span>
        </v-col>
        <v-col cols="4">
          <RequestGraphQL :selected="selected" :bookId="bookID" @changedSDL="newRequest" />
        </v-col>
        <v-col cols="1" align-self="center">
          <span class="charFont">=</span>
        </v-col>
        <v-col cols="4">
          <ResponseGraphQL :request="request" />
        </v-col>
      </v-row>
    </v-main>
  </v-app>
</template>

<script>
import InputGraphQL from "./components/InputGraphQL";
import RequestGraphQL from "./components/RequestGraphQL";
import ResponseGraphQL from "./components/ResponseGraphQL";

export default {
  name: "App",

  components: {
    InputGraphQL,
    ResponseGraphQL,
    RequestGraphQL,
  },

  methods: {
    newRequest(val) {
      this.request = val;
    },
    changeSelected(selected) {
      this.selected = selected;
    },
    bookChanged(bookID) {
      this.bookID = bookID;
    },
  },

  data: () => ({
    bookID: 1,
    selected: [],
    request: null,
  }),
};
</script>

<style>
#app {
  padding: 15px;
}

h1 {
  padding-bottom: 10px;
}

.charFont {
  font-size: 85pt;
  color: lightgray;
}
</style>
