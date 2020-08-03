<template>
  <v-app id="app">
    <v-main>
      <v-row align-content="center" justify="center">
        <v-col :cols="inputColsHeight">
          <InputGraphQL @selectedChanged="changeSelected" @bookChanged="bookChanged" />
        </v-col>
        <v-col cols="1" align-self="center" class="colText">
          <div :class="inputColsHeight == 12? 'goesToBottom charFont' : 'goesToRight charFont'">></div>
        </v-col>
        <v-col :cols="mainColsHeight">
          <RequestGraphQL :selected="selected" :bookId="bookID" @changedSDL="newRequest" />
        </v-col>
        <v-col cols="1" align-self="center" class="colText">
          <span class="charFont">=</span>
        </v-col>
        <v-col :cols="mainColsHeight">
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
  computed: {
    mainColsHeight() {
      switch (this.$vuetify.breakpoint.name) {
        case "xs":
        case "sm":
          return "12";
        case "md":
        case "lg":
        case "xl":
          return "4";
        default:
          return 0;
      }
    },
    inputColsHeight() {
      switch (this.$vuetify.breakpoint.name) {
        case "xs":
        case "sm":
          return "12";
        case "md":
        case "lg":
        case "xl":
          return "2";
        default:
          return 0;
      }
    },
  },
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

.colText {
  text-align: center;
}

.goesToBottom {
  transform: rotate(90deg);
}

.goesToRight {
  transform: rotate(0deg);
}
</style>
