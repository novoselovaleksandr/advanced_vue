<template>
  <div class="container pt-5" id="App" v-cloak>
    <div class="card center">
      <div v-html="myHtml"></div>
      <!--<h2 v-text="title"></h2>
      <h2 v-once>{{ title }}</h2>
      <h2 v-pre>{{ title }}</h2>
      <button class="btn" @click="title = 'теперь я другое название'">
        Изменить название
      </button>
      -->

      <input type="text" v-model="counter" />
      <button @click="getNumber">ИБАС</button>
      {{ length }}

      <div class="form-control">
        <input type="text" @keyup.shift.enter="addItem($event)" ref="myInput" />
      </div>

      <ul class="list" v-if="items.length">
        <li
          class="list-item"
          :key="item"
          v-for="(item, i) in items"
          @click.right.prevent="remove(i), log(item)"
        >
          <strong>{{ item }}</strong
          >&nbsp;
          <input type="text" @click.stop />
        </li>

        <!--<li class="list-item" v-bind:key="value" v-for="(value, key) in person">
          <strong>{{ key }}</strong
          >{{ value }}
        </li>-->
      </ul>
      <h3 v-else>Элементов нет</h3>
      <h3 v-show="items.length === 0">Элементов нет</h3>
    </div>
  </div>
</template>

<script>
export default {
  name: "advanced",
  components: {},
  data: () => ({
    myHtml: "<h1>Vue 3 App</h1>",
    title: "Я есть Грут",
    person: {
      firstName: "Aleksandr",
      lastName: "Novoselov",
      age: 27,
    },
    items: [1, 2],
    counter: 0,
  }),
  methods: {
    addItem(event) {
      this.items.unshift(this.$refs.myInput.value);
      console.log(event);
    },
    remove(i) {
      this.items.splice(i, 1);
    },
    log(item) {
      console.log("Log item: ", item);
    },
    getNumber() {
      this.$emit("callBack", this.counter);
    },
  },
  computed: {
    enevItems() {
      return this.items.filter((i) => i % 2 === 0);
    },
  },
  props: {
    length,
  },
};
</script>
