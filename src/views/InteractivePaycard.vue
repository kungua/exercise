<template>
  <div class="pageContent">
    <div class="toolbox">
      <button @click="onClickFlip">切换正反面</button>
      <br>
      <input v-model="cardCvv" style="margin-top: 8px;" type="text" placeholder="我是cvv的内容">
    </div>
    <div class="paycard" :class="{'-active': isCardFlipped}">
      <div class="paycard__side -front">
        <span class="text">我是正面</span>
      </div>
      <div class="paycard__side -back">
        <div class="paycard__cover">
          <img :src="bdsb" alt="" class="paycard__bg">
        </div>
        <div class="paycard__band"></div>
        <div class="paycard__cvv">
          <div class="paycard__cvvTitle">CVV</div>
          <div class="paycard__cvvBand">
            <span v-for="(n, index) in cardCvv" :key="index">*</span>
          </div>
          <div class="paycard_type">
            <img src="" alt="">
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: "InteractivePaycard",
  data() {
    return {
      isCardFlipped: false,
      cardCvv: '',
      picturePrefix: 'https://raw.githubusercontent.com/muhammederdem/credit-card-form/master/src/assets/images/',
      bdsb: 'http://img3.imgtn.bdimg.com/it/u=367187066,1693012591&fm=26&gp=0.jpg'
    }
  },
  methods: {
    onClickFlip() {
      this.isCardFlipped = !this.isCardFlipped
    },
  }
}
</script>

<style lang="scss" scoped>
.pageContent {

  .paycard {
    width: 430px;
    height: 270px;
    position: relative;
    z-index: 2;


    &__side {
      border-radius: 15px;
      overflow: hidden;
      box-shadow: 0 20px 60px rgba(14, 42, 90, .55);
      height: 100%;

      transform: perspective(2000px) rotateY(0deg) rotateX(0) rotate(0);
      transform-style: preserve-3d;
      transition: all .8s cubic-bezier(.71, .03, .56, .85);
      backface-visibility: hidden;

      border: 1px solid red;

      &.-back {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;

        transform: perspective(2000px) rotateY(-180deg) rotateX(0) rotate(0);
        border: 1px solid gray;
      }
    }

    &.-active {
      .paycard__side {
        &.-front {
          transform: perspective(2000px) rotateY(180deg) rotateX(0) rotate(0);
        }
        &.-back {
          transform: perspective(2000px) rotateY(0deg) rotateX(0) rotate(0);
        }
      }
    }

    &__cover {
      position: absolute; left: 0; top: 0; height: 100%; width: 100%;
      border-radius: 15px;
      overflow: hidden;
      background-color: #1c1d27;
      background-image: linear-gradient(147deg, #354fce 0%, #0c296b 74%);

      &:after {
        content: "";
        position: absolute;
        top: 0; left: 0; width: 100%; height: 100%;
        background: rgba(6, 2, 29, .45);
      }
    }

    &__bg {
      display: block;
      height: 100%;
      width: 100%;
      object-fit: cover;
    }

    &__band {
      background: rgba(0, 0, 19, .8);
      width: 100%;
      height: 50px;
      margin-top: 30px;
      z-index: 2;
      position: relative;
    }

    &__cvv {
      text-align: right;
      position: relative;
      z-index: 2;
      padding: 15px;
      .paycard__type {
        opacity: .7;
      }
    }

    &__cvvTitle {
      padding-right: 10px;
      font-size: 16px;
      font-weight: 400;
      color: #fff;
      margin-bottom: 8px;
    }

    &__cvvBand {
      height: 45px;
      background: #fff;
      margin-bottom: 30px;
      text-align: right;
      display: flex;
      justify-content: flex-end;
      align-items: center;
      padding-right: 10px;
      color: #1a3b5d;
      font-size: 16px;
      border-radius: 4px;
      box-shadow: 0px 10px 20px -7px rgba(32, 56, 117, 0.35);
    }

    border: 1px solid blue;
  }

  .toolbox {
    margin-bottom: 16px;
  }
}
</style>
