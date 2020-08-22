<template>
  <div id="app">
    <div class="wrapper">
      <span class="background-word">ВОПРОСЫ</span>
      <h3 class="header">ВСЕ ЧТО ВЫ ХОТИТЕ ЗНАТЬ</h3>
      <div class="main">
        <div class="questions">
          <Question
            v-for="(item, idx) in data"
            :key="idx"
            :data="data"
            :idx="idx"
            :openAnswer="activeElement === idx"
          />
        </div>
        <img class="broccoli" src="@/assets/img/broccoli_img-min.png" alt="broccoli" />
      </div>
    </div>
  </div>
</template>

<script>
import { mapState } from "vuex";

import Question from "@/components/Question";

export default {
  data: function() {
    return {
      data: [
        {
          question: "Как оформить заказ?"
        },
        {
          question: "Как работает служба доставки?",
          answer: `При заказе до 17:00 доставка осуществляется <span>в день заказа</span>. Среднее 
                   время доставки 2 часа. Доставка осуществляется до 20:00 ежедневно. Мы 
                   работаем без выходных и праздников, чтобы Вы всегда могли кушать 
                   вкусную и здоровую еду!
                   <p>Доставка осуществляется <span>бесплатно</span> при заказе от 1500 руб. по г.Москва в пределах МКАД</p>`
        },
        {
          question: "Условия доставки за пределами МКАД"
        },
        {
          question: "Какие способы оплаты у вас есть?"
        },
        {
          question: "У меня есть промокод, но я не понимаю как им пользоваться"
        }
      ]
    };
  },

  components: {
    Question
  },
  computed: {
    ...mapState({
      activeElement: state => state.activeElement
    })
  }
};
</script>

<style lang="scss">
@import "@/styles/main.scss";

@font-face {
  font-family: "Raleway-ExtraBold";
  src: url("~@/assets/fonts/Raleway-ExtraBold.ttf");
}
@font-face {
  font-family: "Raleway-Bold";
  src: url("~@/assets/fonts/Raleway-Bold.ttf");
}

#app {
  display: flex;
  justify-content: center;
  .wrapper {
    width: 1440px;
    margin-top: 150px;
    @media (max-width: 1439px) {
      width: 754px;
      margin-left: 3px;
      margin-top: 0px;
    }
    @media (max-width: 767px) {
      width: 304px;
      margin-left: 2px;
    }
    .background-word {
      font-family: "Raleway-ExtraBold";
      font-style: normal;
      font-weight: 800;
      font-size: 130px;
      line-height: 153px;
      text-align: center;
      margin: 0 0 0 249px;
      color: #f6f6f6;
      @media (max-width: 1439px) {
        display: flex;
        justify-content: center;
        width: 100%;
        font-size: 80px;
        line-height: 94px;
        margin: 170px 0px 0 0px;
      }
      @media (max-width: 767px) {
        font-size: 30px;
        line-height: 35px;
        margin: 200px 0px 0 0px;
      }
    }
    .header {
      font-family: "Raleway-Bold";
      font-weight: bold;
      font-size: 30px;
      line-height: 35px;
      color: #000000;
      margin: 12px 0 0 382px;
      word-spacing: -1px;
      @media (max-width: 1439px) {
        display: flex;
        justify-content: center;
        width: 100%;
        font-size: 20px;
        line-height: 23px;
        margin: 31px 0px 0 2px;
      }
      @media (max-width: 767px) {
        font-size: 20px;
        line-height: 23px;
        margin: 20px 0px 0 0px;
      }
    }
    .main {
      display: flex;
      height: 630px;
      .questions {
        width: 670px;
        height: 70px;
        margin: 75px 0 0 0;
        @media (max-width: 1439px) {
          margin: 45px 0 0 0;
        }
        @media (max-width: 767px) {
          margin: 48px 0 0 0;
          width: 304px;
        }
      }
      .broccoli {
        transform: rotate(30deg);
        width: 673px;
        height: 549px;
        margin: 119px 0 0 2px;
        @media (max-width: 1439px) {
          position: absolute;
          width: 259px;
          height: 214px;
          margin: -263px 4px 0 497px;
        }
        @media (max-width: 767px) {
          width: 195px;
          height: 159px;
          margin: -234px 4px 0 121px;
          transform: rotate(90deg);
        }
      }
    }
  }
}
</style>
