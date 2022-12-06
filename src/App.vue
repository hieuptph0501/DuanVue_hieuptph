<script>
import HelloWorld from './components/HelloWorld.vue'
import Modalss from './components/Modalss.vue'
import Grid from './components/Grid.vue'
import Login from './components/Login.vue'
export default {
  data() {
    return {
      names: ['Emil, Hans', 'Mustermann, Max', 'Tisch, Roman'],
      selected: '',
      prefix: '',
      first: '',
      last: '',
      keyname: 0,
      showModal: false,
      showLogin: false,
      searchQuery: '',
      gridColumns: ['name', 'power'],
      gridData: [
        { name: 'Chuck Norris', power: Infinity },
        { name: 'Bruce Lee', power: 9000 },
        { name: 'Jackie Chan', power: 7000 },
        { name: 'Jet Li', power: 8000 }
      ]
    }
  },
  components: {
    HelloWorld,
    Modalss,
    Grid,
    Login,
  },
  computed: {
    filteredNames() {
      return this.names.filter((n) =>
        n.toLowerCase().startsWith(this.prefix.toLowerCase())
      )
    }
  },
  watch: {
    selected(name) {
      [this.last, this.first] = name.split(', ')
      // this.keyname = this.names.selected(this.names.length)
    }
  },
  methods: {
    create() {
      if (this.hasValidInput()) {
        const fullName = `${this.last}, ${this.first}`
        if (!this.names.includes(fullName)) {
          this.names.push(fullName)
          this.first = this.last = ''
        }
      }
    },
    update() {
      if (this.hasValidInput() && this.selected) {
        const i = this.names.indexOf(this.selected)
        this.names[i] = this.selected = `${this.last}, ${this.first}`
      }
    },
    del() {
      if (this.selected) {
        const i = this.names.indexOf(this.selected)
        this.names.splice(i, 1)
        this.selected = this.first = this.last = ''
      }
    },
    hasValidInput() {
      return this.first.trim() && this.last.trim()
    }
  }
}
</script>

<template>
  <div class="container">
    <img class="imgWestmall"
      src="data:image/jpeg;base64,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" />

    <label>West mall June holidays family activitie</label>
    <button id="show-modal" @click="showLogin = true">Login</button>
     <Teleport to="body">
      <Login :show="showLogin" @close="showLogin = false">
        <template #header>
          <h3>Pham Trung Hieu</h3>
        </template>
      </Login>
    </Teleport> 

    <button id="show-modal" @click="showModal = true">Show Model</button>
    <Teleport to="body">
      <Modalss :show="showModal" @close="showModal = false">
        <template #header>
          <h3>Pham Trung Hieu</h3>
        </template>
      </Modalss>
    </Teleport>
    <HelloWorld msg="Hello Vue 3.0 + Vite" />
    <div><input v-model="prefix" placeholder="Filter prefix"></div>
    <select size="5" v-model="selected">
      <option v-for="name in filteredNames" :key="name">{{ name }}</option>
    </select>
    <label class="name">Name: <input v-model="first"></label>
    <label>Surname: <input v-model="last"></label>
    <label class="name">Get ID: {{ keyname }}</label>
    <div class="buttons">
      <button @click="create">Create</button>
      <button @click="update">Update</button>
      <button @click="del">Delete</button>
    </div>
    <form id="search">
      Search <input class="inputsearch" name="query" v-model="searchQuery">
    </form>
    <Grid :data="gridData" :columns="gridColumns" :filter-key="searchQuery">
    </Grid>

  </div>


</template>
<style>
* {
  font-size: inherit;
}

#search {
  justify-content: center;
}

.inputsearch {
  justify-content: center;
  align-items: center;
}

#show-modal {
  margin-bottom: 10px;
  margin-top: 10px;
}

.container {
  margin-left: 10px;
  margin-right: 5px;
  background-color: rgb(236, 225, 211);
}

.imgWestmall {
  width: 85%;
  height: 50%;
  margin-left: 10%;
  margin-right: 10%;
  margin-bottom: 10px;
}

label {
  margin-left: 50px;
  justify-content: center;
  display: block;
}

input {
  display: block;
  margin-bottom: 10px;
}

select {
  float: left;
  margin: 0 1em 1em 0;
  width: 14em;
}

button+button {
  margin-left: 5px;
}
</style>
