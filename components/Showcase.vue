<template lang="pug">
  section.showcase.theme.theme--purple-reverse
    ul.showcase__listing
        li.showcase__item(v-for="index in 10" :key="index")
            Card(:image="placeholderImage" :title="placeholderTitle" :subtitle="placeholderSubtitle" :description="placeholderDescription")
</template>


<script>
import Card from "~/components/Card";

export default {
  data: () => {
    return {
      placeholderImage:
        "http://informationcommunicationtechnology.com/wp-content/uploads/2018/06/Images-111.jpg",
      placeholderTitle: "Item",
      placeholderSubtitle: "Subtitle",
      lorem:
        "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed est elit, lacinia nec egestas quis, volutpat in nulla. Phasellus sit amet molestie dui. Vivamus eleifend et mauris eleifend congue. Aenean et maximus orci, ut placerat massa. Duis finibus sagittis ante, eget elementum erat cursus vitae. Phasellus vitae ante sem. Morbi dapibus porttitor finibus."
    };
  },
  computed: {
    placeholderDescription: function() {
      return `<p> ${this.lorem} </p><p> ${this.lorem} </p>`;
    }
  },
  components: {
    Card
  },
  methods: {},
  mounted: function() {}
};
</script>

<style lang="scss">
@import '~/styles/_variables.scss';
@import '~/styles/_mixins.scss';

$item-spacing: .5vw;

.showcase {
    overflow: hidden;
}

.showcase__listing {
  padding: 0;
  margin: -#{$item-spacing/2};
  display: flex;
  flex-flow: row wrap;
}

.showcase__item {
  display: block;
  width: 100%;
  margin: $item-spacing/2;

  @include breakpoint(sm) {
    width: calc(50% - #{$item-spacing});
  }

  @include breakpoint(md) {
    width: calc(33.333% - #{$item-spacing});
  }
}
</style>