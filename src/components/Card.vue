<template>
  <div class="card">
    <div class="card__side -front">
      <div class="card__focus"></div>
      <div class="card__cover">
        <img v-if="currentCardBackground" :src="currentCardBackground" alt="我是一张信用卡的背景图" class="card__bg">
      </div>
      <div class="card__wrapper">
        <div class="card__top">
          <img src="" alt="" class="card__chip">
          <div class="card__type">
            <transition name="slide-fade-up">
              <img src="" alt class="card__typeImg">
            </transition>
          </div>
        </div>

      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "card",
  props: {
    label: Object,
    fields: Object,
    isCardNumberMasked: Boolean,
    randomBackgrounds: {
      type: Boolean,
      default: true
    },
    backgroundImage: [String, Object]
  },
  data() {
    return {
      picturePrefix: 'https://raw.githubusercontent.com/muhammederdem/credit-card-form/master/src/assets/images/'
    }
  },
  computed: {
    currentCardBackground() {
      const {picturePrefix, randomBackgrounds, backgroundImage} = this
      if (randomBackgrounds && !backgroundImage) {
        const random = Math.floor(Math.random() * 25 + 1)
        return `${picturePrefix}${random}.jpeg`
      } else if (backgroundImage) {
        return backgroundImage
      }
      return null
    }
  }
}
</script>

<style lang="scss" scoped>
.card {
  max-width: 430px;
  height: 270px;
  margin: 0 auto;
  position: relative;
  z-index: 2;
  width: 100%;

  &__cover {
    position: absolute;
    height: 100%;
    background-color: #1c1d27;
  }

  &__bg {
    display: block;
    max-width: 100%; max-height: 100%;
    width: 100%; height: 100%;
    object-fit: cover;
  }

  border: 1px solid blue;
}
</style>
