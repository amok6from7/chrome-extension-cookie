<template>
  <div>
    <p>Get Cookie Extension</p>
    <button @click="getCookie">GET Cookie</button>
    <ul>
      <li v-for="(cookie, index) in cookies" :key="index">
        <span>{{ index }}. {{ cookie.name }} : {{ cookie.value }}</span>
      </li>
    </ul>
  </div>
</template>

<script>
  export default {
    data () {
      return {
        cookies: null,
        text: null
      }
    },
    methods: {
      getCookie() {
        chrome.cookies.getAll({domain:'yahoo.co.jp'},(function(c) {
          console.log(c)
            this.cookies = c;
        }.bind(this)))
      }
    }
  }
</script>

<style lang="scss" scoped>
  p {
    font-size: 20px;
    min-width: 300px;
  }
  ul {
    list-style: none;
  }
</style>
