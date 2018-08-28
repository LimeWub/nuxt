<template lang="pug">
  section.container.theme.theme--pink.spacing
      div.rte
        div.theme.theme--pink-reverse.spacing
            h1 Heading 1
            p {{ lorem }}
        div.theme.theme--purple.spacing.texture.texture--polka
          h2 Heading 2
          p {{ lorem }}
        div.theme.theme--purple-reverse.spacing.texture.texture--polka
          h3 Heading 3
          p {{ lorem }}
        div.theme.theme--yellow.spacing
          h4 Heading 4
          p {{ lorem }}
        div.theme.theme--yellow-reverse.spacing
          h5 Heading 5
          p {{ lorem }}
        div.theme.theme--pink-reverse.spacing.texture.texture--polka
          h6 Heading 6
          p {{ lorem }}
          p {{ lorem }}
          p {{ lorem }}
          p {{ lorem }}
          BloopButton(button-text="Hello")
          BloopButton(button-text="Hello" href="http://www.google.com")
          BloopButton(disabled button-text="Disabled")
        Card
        
      div.card
        h1 Who dis
</template>


<script>
import Card from "~/components/Card";
import BloopButton from "~/components/BloopButton";

export default {
  data: () => {
    return {
      lorem: "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed est elit, lacinia nec egestas quis, volutpat in nulla. Phasellus sit amet molestie dui. Vivamus eleifend et mauris eleifend congue. Aenean et maximus orci, ut placerat massa. Duis finibus sagittis ante, eget elementum erat cursus vitae. Phasellus vitae ante sem. Morbi dapibus porttitor finibus."
    };
  },
  components: {
    Card,
    BloopButton
  },
  methods: {
  },
  mounted : function() {
  //  let hmm = document.getElementsByClassName('jsParticle');
  //  console.log(hmm);
  }
};


</script>

<style lang="scss">
.container {
  //text-align: center;
}
</style>