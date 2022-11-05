<template>
  <div>
    <Content msg="Lorem ipsum dolor sit amet consectetur. !" />
    <!-- directives -->
    <p v-text="name"></p>
    <p v-html="title"></p>
    <!-- v-for -->
    <!-- eslint-disable-next-line vue/require-v-for-key -->
    <li v-for="(item, index) in items">
      {{ index }} -
      {{ item }}
    </li>
    <div>
      <p v-if="name">welcome {{ name }}</p>
      <p v-else>no name saved</p>
    </div>
    <p v-if="age > 20">your age is too old {{ age }}</p>
    <p v-else-if="age < 20">your age is too young {{ age }}</p>

    <p v-once>your second name set as {{ secName }}</p>
    <!-- display: none; -->
    <p v-show="thirdName">your third name set as {{ thirdName }}</p>

    <img :src="imageSrc" :alt="alt" />

    <p>counter is {{ counter }}</p>
    <button class="btn btn-danger m-3" @click="counter += 10">counting</button>
    <form action="" class="m-3">
      <input
        type="text"
        :value="source"
        placeholder="use v-bind"
        class="form-control w-75"
      />
      <br />
      <input
        type="text"
        v-model="source"
        placeholder="v-modal updating data because is two way binding"
        class="form-control w-75"
      />
      <input type="checkbox" v-model="checked" id="checkbox" />
      <label for="checkbox" class="mx-1">{{ checked }}</label>
    </form>
    <p>your name is {{ source }}</p>
    <h5>{{ calcAge }}</h5>
    <h5>{{ calcAge }}</h5>
    <h5>{{ calcAge }}</h5>
    <h5>{{ calcAge }}</h5>
    <input type="text" v-model="findlangs" />
    <ul>
      <!-- eslint-disable-next-line vue/require-v-for-key -->
      <li v-for="lang in filterLanguages">
        {{ lang }}
      </li>
    </ul>
    <input type="text" v-model.lazy="userName" />
    <p>{{ validate }}</p>

    <input type="text" v-model="eg" />
    <input type="text" v-model="sar" />
  </div>
</template>

<script>
import Content from "./Content.vue";
export default {
  components: { Content },
  // eslint-disable-next-line vue/multi-word-component-names
  name: "Popup",
  data() {
    return {
      name: "Farah",
      secName: "Yasser",
      thirdName: "mohamed",
      title: "<b class='rank'>mms</b>",
      items: ["Foo", "Bar"],
      age: 30,
      imageSrc:
        "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQk1H6FKdz9nHtvEN5FxBF9wo6KDZAvvPrh74LzhWFA&s",
      alt: "image name",
      counter: 0,
      source: "osama",
      checked: false,
      findlangs: "",
      langs: ["html", "css", "java", "sass", "javascript"],
      userName: "",
      eg: 0,
      sar: 0,
    };
  },
  methods: {},
  computed: {
    calcAge: function () {
      console.log("run");
      return this.age * 2;
    },
    filterLanguages: function () {
      console.log("run filter");
      const filtering = new RegExp(this.findlangs, "i");
      return this.langs.filter(function (el) {
        return el.match(filtering);
      });
    },
    // eslint-disable-next-line vue/return-in-computed-property
    validate: function () {
      if (!this.userName) {
        return "user can not be empty";
      } else if (this.userName.length > 8) {
        return "letter must small than 8 char";
      } else if (!isNaN(this.userName)) {
        return `user char cant be only numbers`;
      } else {
        return `hello ${this.userName} <3`;
      }
    },
  },
  watch: {
    eg: function (value) {
      this.sar = value / 6;
      console.log("eg run");
    },
    sar: function (value) {
      this.eg = value * 6;
      console.log("sar run");
    },
  },
};
</script>

<style lang="scss" scoped>
</style>