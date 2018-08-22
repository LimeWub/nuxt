<template lang="pug">
  section.container
      div
        h1 Hello darkness my old friend
        h2 Heading 2
        h3 Heading 3
        h4 Heading 4
        h5 Heading 5
        h6 Heading 6

        p I've come to talk to you MULTI
        | LINE 
        | {{ bob }}
        |<br>
        | I've come to talk to you MULTI
        | LINE 
        | {{ bob }}
        |<br>
        | I've come to talk to you MULTI
        | LINE 
        | {{ bob }}
        |<br>
        | I've come to talk to you MULTI
        | LINE 
        | {{ bob }}

        card

        div.card
          h1 Who dis
</template>


<script>
import Card from "~/components/Card";

export default {
  data: () => {
    return {
      bob: "Because something about visions here"
    };
  },
  components: {
    Card
  }
};
</script>

<style lang="scss">
.container {
  text-align: center;
  color: red;
}
</style>