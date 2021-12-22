<template>
  <v-container>
      <p>输入组件</p>
    <v-card outlined width="100%">
    
      <v-sheet
        class="pa-4"
        :ripple="{ class: 'blue--text' }"
        min-width="20%"
        max-width="100%"
        :width="stylewidth"
      >
        <v-textarea
          dense
          outlined
          auto-grow
          rows="1"
          v-model="inputtext"

          placeholder="hello"
        ></v-textarea>
      </v-sheet>
    </v-card>
    <span id="text" ref="box1"> {{ inputtext }}</span>
  </v-container>
</template>

<script>
export default {
  name: "Input",

  data: () => ({
    inputtext: "",
    inputtt: "",
    spanW: 100,
  }),
  computed: {
    stylewidth: function () {
      return this.spanW + 70 + "px";
    },
  },
  watch: {
    inputtext: {
      handler() {
        this.inputtt = this.inputtext;
        console.log("inputtext动了");
        this.spanW = this.$refs.box1.getBoundingClientRect().width;
      },
    },
    // inputtt: {
    //   handler() {
    //     console.log(this.$refs.box1.getBoundingClientRect().width);
    //     this.spanW = this.$refs.box1.getBoundingClientRect().width
    //   },
    // },
  },
  methods: {
    divdragover() {
      let a = event.target; // 这里就是获取到的dom元素
      console.log(a.getBoundingClientRect().width);
      this.spanW = a.getBoundingClientRect().width;
    },
  },
};
</script>

<style lang="scss">
#text {
  white-space: pre-wrap;
  max-width: 100%;
  min-width: 100px;
  font-size: 16px;
  line-height: 1.5;
  font-family: "Roboto", sans-serif;
  visibility: hidden;
}
</style>>





