<template>
  <v-layout class="hello">
    <h1>{{ msg }}</h1>
    <div v-for="item in fields" :key="item.index" >
      <v-text-field v-model="item.name" >
      </v-text-field>
      <v-text-field v-for="(val, key, index) in item.values" :key="index" v-model="item.values[key]" >
      </v-text-field>
      <v-btn flat icon color="pink" @click="littleadd(item.index)">
        <v-icon>add</v-icon>
      </v-btn>
    </div>
    <v-btn @click="add()">
      Add
    </v-btn>
    <v-btn @click="build()">
      Build
    </v-btn>
  </v-layout>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      fields: [
        { index: 0, values: [''] }
      ]
    }
  },
  methods: {
    add: function () {
      console.log('add')
      this.fields.push({ index: this.fields.length, values: [''] })
    },
    littleadd: function (id) {
      console.log('little' + id)
      this.fields[id].values.push('')
    },
    build: function () {
      var build = {}
      for (var key in this.fields) {
        build[this.fields[key].name] = this.fields[key].values
      }
      console.log(build)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
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
