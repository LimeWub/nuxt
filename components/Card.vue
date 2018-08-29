<template lang="pug">
  article.card 
    img.card__image(:src="image")
    div.card__container
      div
        h1 {{ title }}
        p {{ subtitle }}
        a.card__link(href="#")
</template>


<script>
export default {
  data: () => {
    return {};
  },
  props: {
    image: {
      type: String,
      required: true
    },
    theme: {
      type: String,
      required: false
    },
    title: {
      type: String,
      required: false
    },
    subtitle: {
      type: String,
      required: false
    },
    description: {
      type: String,
      required: false
    }
  },
  components: {}
};
</script>

<style lang="scss" scoped>
@import '~/styles/_variables.scss';
@import '~/styles/_mixins.scss';

.card {
  width: 100%;
  position: relative;
  overflow: hidden;
  background: var( --bg-color , #{$white});

  &::after {
    content: "";
    display: block;
    padding-top: 70%;
  }
}

.card__image {
  position: absolute;
  top: 50%;
  left: 0;
  width: 100%;
  height: 100%;
  transform: translateY(-50%);
  opacity: .5;
  mix-blend-mode: multiply;

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
  background: none;
}

.card__link{
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;

  &:focus, &:hover {
    background: red;
    mix-blend-mode: color-dodge;
  }
}
</style>