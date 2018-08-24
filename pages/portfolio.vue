<template lang="pug">
  section.container.theme.theme--default
      div.rte
        h1 Heading 1
        h2 Heading 2
        h3 Heading 3
        h4 Heading 4
        h5 Heading 5
        h6 Heading 6
        p {{ lorem }}
        p {{ lorem }}
        p {{ lorem }}
        p {{ lorem }}
        button hello

      card

      div.card
        h1 Who dis
</template>


<script>
import Card from "~/components/Card";

export default {
  data: () => {
    return {
      lorem: "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed est elit, lacinia nec egestas quis, volutpat in nulla. Phasellus sit amet molestie dui. Vivamus eleifend et mauris eleifend congue. Aenean et maximus orci, ut placerat massa. Duis finibus sagittis ante, eget elementum erat cursus vitae. Phasellus vitae ante sem. Morbi dapibus porttitor finibus."
    };
  },
  components: {
    Card
  }
};
</script>

<style lang="scss">
.container {
  //text-align: center;
}
</style>