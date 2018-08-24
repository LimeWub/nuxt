<template lang="pug">
  article.card
      div.card__container
        div.card__content
            h1 123
            p 456
</template>


<script>
export default {
  data: () => {
    return {
      bob: 'Because something about visions here'
    }
  },
  components: {}
}
</script>

<style lang="scss" scoped>
  .card {
    width: 100%;
    position: relative;

    &::after {
        content: '';
        display: block;
        padding-top: 50%;
    }
  }

  .card__container {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      display: flex;
      align-items: center;
      justify-content: center;
  }

  .card__content {
  }
</style>