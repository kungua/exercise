<template>
  <div class="cardForm">
    <card/>
  </div>
</template>

<script>
import Card from './Card'

export default {
  name: "cardForm",
  components: {
    Card
  }
}
</script>

<style lang="scss" scoped>
.cardForm {
  width: 100%;
  margin: auto;
  max-width: 570px;

  border: 1px solid gray;
}

</style>
