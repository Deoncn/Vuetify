<template>
  <v-container>
    <p>各种属性及效果预览</p>
    <v-form>
      <v-container>
        <v-row>
          <v-col cols="12" sm="6" md="4">
            <p>placeholder 属性</p>
            <v-text-field
              dense
              outlined
              placeholder="输入字段的提示 属性展示"
            ></v-text-field>
          </v-col>

          <v-col cols="12" sm="6" md="4">
            <p>maxlength 属性</p>
            <v-text-field
              dense
              outlined
              maxlength="10"
              placeholder="设置字符的最大长度 属性为10"
            ></v-text-field>
          </v-col>

          <v-col cols="12" sm="6" md="4">
            <p>disable 属性</p>
            <v-text-field
              dense
              outlined
              disabled="disabled"
              placeholder="元素加载时禁用此元素"
            ></v-text-field>
          </v-col>

          <v-col cols="12" sm="6" md="4">
            <p>支持复制粘贴</p>
            <v-text-field
              dense
              outlined
              placeholder="支持复制粘贴"
            ></v-text-field>
          </v-col>

          <v-col cols="12" sm="6" md="4">
            <p>不支持富文本，支持win表情文本</p>
            <v-text-field dense outlined placeholder="💌💢💥💦"></v-text-field>
          </v-col>

          <v-col cols="12" sm="6" md="4">
            <p>checked属性 type属性 name 属性</p>
            <v-text-field
              type="checkbox"
              dense
              outlined
              checked="checked"
              name="1234"
              placeholder="💌💢💥💦"
            ></v-text-field>
          </v-col>

          <v-col cols="12" sm="6" md="4">
            <p>button 属性控制音乐播放与暂停</p>
            <audio ref="audio" :src="songs[index]" controls></audio>
            <v-text-field
              type="button"
              dense
              outlined
              value="▶ ⏸ 播放/暂停"
              @click="over"
            ></v-text-field>
            <v-text-field
              type="button"
              dense
              outlined
              value="👇下一首"
              v-show="index < songs.length - 1"
              @click="next"
            ></v-text-field>
            <v-text-field
              type="button"
              dense
              outlined
              v-show="index != 0"
              value="👆上一首"
              @click="pre"
            ></v-text-field>
          </v-col>

          <v-col cols="12" sm="8" md="4">
            <p>
              最终的输入组件可支持效果<br />
              1.随着组件输入内容的增加，组件的宽度和高度可以自动扩展，宽度扩展到和组件父容器宽度相同的时候，进行高度的扩展。<br />
              2.支持换行符的输入。
            </p>
          </v-col>
        </v-row>
      </v-container>
    </v-form>
  </v-container>
</template>

<script>
export default {
  name: "Demo",

  data: () => ({
    songs: [
      "http://music.163.com/song/media/outer/url?id=25830168.mp3",
      "http://music.163.com/song/media/outer/url?id=29017078.mp3",
      "http://music.163.com/song/media/outer/url?id=29482234.mp3",
    ],
    inputtext: "",
    inputtt: "",
    spanW: 100,
    is_stop: false,
    index: 0,
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
    over() {
      console.log("音乐播放暂停");
      this.is_stop = !this.is_stop;
      if (this.is_stop) {
        this.$refs.audio.play();
      } else {
        this.$refs.audio.pause();
      }
    },
    next() {
      console.log("下一首");
      this.index++;
      this.is_stop = !this.is_stop;
    },
    pre() {
      console.log("上一首");
      this.index--;
      this.is_stop = !this.is_stop;
    },

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





