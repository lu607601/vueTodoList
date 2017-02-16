<template>
  <li class="todo" @mouseenter="showDeleteTag" @mouseleave="hideDeleteTag">
      <input type="checkbox" @click="itemCheck(item)" >
      <p class="item-label" :class="{'line-through': checked }">{{index+1}}. {{label}}</p>
      <p class="item-label" v-if="isShowDel" @click="delClick">del</p>   
  </li>
</template>

<script>
export default {
  name: 'todo',
  data () {
    return {
      isShowDel: false,
      checked: false
    }
  },
  props: {
    label: '',
    index: ''
  },
  methods: {
    itemCheck: function (item) {
      this.checked = !this.checked
    },
    showDeleteTag: function () {
      this.isShowDel = true
    },
    hideDeleteTag: function () {
      this.isShowDel = false
    },
    delClick: function () {
      this.$emit('delete', this.index)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}

li {
  list-style: none;
  margin: 0 10px;
  height: 36px;
  line-height: 36px;
}
a {
  color: #42b983;
}
.item-label {
  display: inline;
}
.line-through {
  text-decoration: line-through;
}
</style>
