<template>

  <div
    class="card"
    :class="{ reveal: reveal }"
    :style="matchingDegree"
  >

    <div v-if="reveal" class="revealed">
      {{payload}}
    </div>

    <div v-else class="hidden">
      {{title}}
    </div>

  </div>

</template>

<script>

  import _ from 'lodash';

  export default {
    name: 'HelloWorld',
    props: ['title', 'payload', 'input'],
    computed: {
      reveal() {
        return this.input.toLowerCase() === this.title.toLowerCase();
      },
      matchingDegree() {
        const { title, input } = this;
        // let matchedChars = 0;
        // if (title.toLowerCase().includes(input.toLowerCase())) {
        //   matchedChars = input.length;
        // }
        const matchedChars = _.intersection(title.split(''), input.split('')).length;
        return {
          'background-color': `rgba(0,128, 128, ${matchedChars/title.length})`
        }
      }
    }
  }

</script>

<style scoped lang="scss">

  .card {
    padding: 10px 0px;
    width: 300px;
    border: 1px solid teal;
    margin: 0 auto;
    margin-bottom: 16px;
    border-radius: 4px;
    &.reveal {
      background-color: teal !important;
      color: white
    }
  }

  .revealed {
    transition: ease-in 300ms;
    transform: rotateY(180deg) scaleX(-1);
  }

</style>
