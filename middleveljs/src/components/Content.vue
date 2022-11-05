<template>
  <div>
    <p>{{ name }}</p>
    <p>{{ isSubescribed ? "Subescribed" : "not Subescribed" }}</p>
    <p>your first test name is {{ completeTest[0].testName }}</p>
    <p>test result {{ completeTest[0].testResult }}</p>
    <p>{{ sayMyname() }}</p>

    <ul>
      <!-- eslint-disable-next-line vue/require-v-for-key -->
      <li v-for="(test, index) in completeTest">
        {{ index }}
        {{ test.testName }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: "Content",
  props: {
    msg: String,
  },
  data() {
    return {
      name: "mohamed",
      isSubescribed: false,
      age: 21,
      completeTest: [
        {
          testName: "first test",
          testResult: "80%",
        },
        {
          testName: "second test",
          testResult: "50%",
        },
      ],
    };
  },
  methods: {
    sayMyname: function () {
      return this.age * 365;
    },
  },
};
</script>

<style scoped>
</style>