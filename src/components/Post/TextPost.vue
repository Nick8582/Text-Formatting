<template>
  <span v-for="text in textColors" :class="text.class">
    {{text.text}}
  </span>
</template>

<script>
export default {
  name: 'TextPost',
  props: ['text', 'textTones'],
  computed: {
    textColors() {
      let textString = this.text;
      let indexText = 0;
      let massText = [];

      const textSearch = (a, b) => {
        return textString.slice(a, b)
      }

      const textBgColor = (tone) => {
        if (0 > tone) {
          return 'color__red'
        } else if ((0.35 > tone) || (-0.35 > tone)) {
          return 'color__yellow'
        } else if (0 < tone) {
          return 'color__green'
        }
      }

      this.textTones.map((date, index) => {
            indexText++;
            if (index === 0) {
              if (date.position != 0) {
                massText.push({text: (textSearch(0, date.position)), class: ''});
              }
            }

            massText.push({text: (textSearch(date.position, (date.position + date.length))), class: (textBgColor(date.tone))})

            if (index < this.textTones.length - 1) {
              massText.push({text: (textSearch((date.position + date.length), (this.textTones[indexText].position))), class: ''});
            } else {
              massText.push({text: (textSearch((date.position + date.length), textString.length)), class: ''});
            }
          }
      )
      return massText
    }
  }
}
</script>

<style>
.color__red {
  background-color: rgba(255, 0, 0, 0.60);
}

.color__green {
  background-color: rgba(0, 255, 0, 0.77);
}

.color__yellow {
  background-color: rgba(255, 255, 0, 0.65);
}
</style>
