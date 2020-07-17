<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <p>I'm text inside the component.</p>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  computed: {
    propertyComputed() {
      console.log('I change when this.property changes.')
      return this.property
    }
  },
  beforeCreate() {
    console.log('Nothing gets called before me!')
  },
  created() {
    this.property = 'Example property update.'
    console.log('propertyComputed will update, as this.property is now reactive.')
  },
  beforeMount() {
    console.log(`this.$el doesn't exist yet, but it will soon!`)
  },
  mounted() {
    console.log(this.$el.textContent) // I'm text inside the component.
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
