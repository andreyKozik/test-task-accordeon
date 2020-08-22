<template>
  <div class="wrapper-question">
    <div @click="open()" :class="setClasses">
      <img class="plus" :src="require(`@/assets/img/${src}`)" alt="plus" />
    </div>
    <div class="content">
      <div class="question">{{ data[idx].question }}</div>
      <transition name="open">
        <div class="answer" v-html="data[idx].answer" v-show="openAnswer"></div>
      </transition>
    </div>
  </div>
</template>

<script>
import { mapActions } from "vuex";

export default {
  name: "Question",
  data: function() {
    return {
      src: "plus.svg",
      flagOpen: ""
    };
  },
  props: {
    data: Array,
    idx: Number,
    openAnswer: Boolean
  },
  computed: {
    setClasses() {
      return this.openAnswer ? this.setClassOpen() : this.setClassClose();
    }
  },
  methods: {
    ...mapActions({
      setNumberActiveElement: "setNumberActiveElement"
    }),

    setClassOpen() {
      this.src = "close.svg";
      return { open: true, close: false };
    },

    setClassClose() {
      this.src = "plus.svg";
      return { open: false, close: true };
    },

    open() {
      this.openAnswer
        ? this.setNumberActiveElement(false)
        : this.setNumberActiveElement(this.idx);
    }
  }
};
</script>

<style lang="scss">
@import "@/styles/main.scss";
@import "@/styles/Question/close.scss";
@import "@/styles/Question/open.scss";
@import "@/styles/Question/retractableBlock.scss";
@import "@/styles/Question/helperTeg.scss";

@font-face {
  font-family: "Raleway-ExtraBold";
  src: url("~@/assets/fonts/Raleway-ExtraBold.ttf");
  font-display: swap;
}
@font-face {
  font-family: "Raleway-Bold";
  src: url("~@/assets/fonts/Raleway-Bold.ttf");
  font-display: swap;
}
@font-face {
  font-family: "Raleway-Medium";
  src: url("~@/assets/fonts/Raleway-Medium.ttf");
  font-display: swap;
}

.wrapper-question {
  display: flex;
  margin: 0 0 45px 0;
  .button {
    img {
      pointer-events: none;
    }
  }
  .content {
    width: 568px;
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    overflow: hidden;
    @media (max-width: 767px) {
      width: 224px;
    }
    .question {
      position: relative;
      height: 70px;
      font-family: "Raleway-ExtraBold";
      font-weight: bold;
      font-size: 16px;
      line-height: 19px;
      display: flex;
      align-items: center;
      color: #000000;
      word-spacing: -2px;
      background-color: white;
      @media (max-width: 1439px) {
        word-spacing: -2px;
      }
      @media (max-width: 767px) {
        font-size: 16px;
        line-height: 19px;
        width: 224px;
      }
    }
    .answer {
      width: 570px;
      font-family: "Raleway-Medium";
      font-style: normal;
      font-weight: normal;
      font-size: 16px;
      line-height: 19px;
      margin: 0 0 0 0;
      word-spacing: -1.2px;
      @media (max-width: 767px) {
        width: 221px;
        font-size: 14px;
        line-height: 24px;
      }
    }
  }
}
</style>
