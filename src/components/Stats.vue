<template>
  <div>
    <h2>Stats</h2>
    <p>{{countLinks}} links</p>
    <button @click="removeAllLinks">Remove All</button>
    <p>{{msg}}</p>
  </div>
</template>

<script>
import { mapGetters, mapMutations, mapActions } from 'vuex'

export default {
  name: 'Stats',
  computed: {
    ...mapGetters(['countLinks'])
  },
  data () {
    return {
      msg: ''
    }
  },
  methods: {
    ...mapMutations(['REMOVE_ALL']),
    ...mapActions(['removeAll']),
    removeAllLinks () {
      this.removeAll().then(() => {
        this.msg = 'removed'
      })
    }
  }
}
</script>

<style scoped>
button {
    padding: 10px;
    margin-top: 30px;
    width: 100%;
    background: none;
    border: 1px solid lightgray;
    outline: 0;
    cursor: pointer;
}
</style>
