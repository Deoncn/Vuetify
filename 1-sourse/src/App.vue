<template>
  <v-app>
    <v-container>
      <h1>INPUI COMPONET DEMO</h1>
    </v-container>

    <v-container>
      <Demo />
    </v-container>
    <v-container>
      <Input />
    </v-container>
  </v-app>
</template>

<script>
import Demo from "./components/Demo";
import Input from "./components/Input";

export default {
  name: "App",

  components: {
    Input,
    Demo,
  },

  data: () => ({
    //
  }),
};
</script>
