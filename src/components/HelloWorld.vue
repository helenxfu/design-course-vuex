<template>
  <div class="hello">
    <div class="left">
      <h1>{{custom}}</h1>
      <form @submit.prevent="addLink">
        <input class="link-input" type="text" placeholder="add link here" v-model="newLink" />
      </form>
      <ul>
        <li v-for="(link, index) in links" :key="index">{{link}}
          <button @click="removeLinks(index)" class="rm">Remove</button>
        </li>
      </ul>
    </div>
    <div class="right">
      <Stats />
    </div>
  </div>
</template>

<script>
import Stats from '@/components/Stats'
import { mapState, mapMutations, mapActions } from 'vuex'

export default {
  name: 'HelloWorld',
  components: {
    Stats
  },
  data () {
    return {
      newLink: ''
    }
  },
  computed: {
    ...mapState({
      custom: 'title', links: 'links'
    })
  },
  methods: {
    ...mapMutations(['ADD_LINK']),
    ...mapActions(['removeLink']),
    addLink () {
      this.ADD_LINK(this.newLink)
      this.newLink = ''
    },
    removeLinks (link) {
      this.removeLink(link)
    }
  }
}
</script>

<style>
 html, #app, .home {
    height: 100%;
  }
  body {
    background-color: #F4F4F4;
    margin: 0;
    height: 100%;
  }

  .hello {
    display: grid;
    grid-template-columns: repeat(2, 50%);
    grid-template-rows: 100%;
    grid-template-areas:
      "left right";
    height: 100%;
  }

  .left, .right {
    padding: 30px;
  }

  ul {
    list-style-type: none;
    padding: 0;
  }
  ul li {
    padding: 20px;
    background: white;
    margin-bottom: 8px;
  }

  .right {
    grid-area: right;
    background-color: #E9E9E9;
  }
    input {
    border: none;
    padding: 20px;
    width: calc(100% - 40px);
    box-shadow: 0 5px 5px lightgrey;
    margin-bottom: 50px;
    outline: none;
  }
    .rm {
    float: right;
    text-transform: uppercase;
    background: #f9d0e3;
    border: none;
    padding: 5px;
    color: #ff0076;
    cursor:pointer;
  }

</style>
