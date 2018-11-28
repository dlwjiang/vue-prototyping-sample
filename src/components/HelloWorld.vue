
<template>

  <div class="hello">

    <h1>Type in an animal:</h1>

    <input type="text" v-model="input">

    <card
      v-for="card in cards"
      :key="card.title"
      :title="card.title"
      :payload="card.description"
      :input="input"
    />

  </div>

</template>

<script>

  import card from './Card.vue';

  export default {
    name: 'HelloWorld',
    components: {
      'card' : card
    },
    data: function() {
      return {
        input: '',
        cards: [
          { title: 'Fox', description: 'Knows many things'},
          { title: 'Hedgehog', description: 'Knows one important thing'},
          { title: 'Weasel', description: 'Knows everything yet nothing'},
          { title: 'Cactus', description: 'Knows only one thing'},
          { title: 'Dog', description: 'Knows society'},
          { title: 'Cat', description: 'Knows the self'}
        ]
      }
    }
  }

</script>


<style scoped lang="scss">

  input {
    margin-bottom: 24px;
    width: 300px;
    height: 30px;
    border-radius: 4px;
  }

</style>
