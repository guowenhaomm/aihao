<template>
      <ul class="todo-main">
      <Item v-for="(userOBJi, index) in userOBJ" :key="userOBJi.id" :userOBJS='userOBJi' :index='index' :isAddtrue='isAddtrue' :DeleteOclik='DeleteOclik'/>
      </ul>
</template>

<script>
import Item from '@/components/Item.vue'
export default {
  data () {
    return {
      name: ''
    }
  },
  props:['userOBJ','isAddtrue','DeleteOclik'],
  components:{
    Item
  },
  methods: {

  }
}
</script>

<style scoped>
/*main*/
.todo-main {
  margin-left: 0px;
  border: 1px solid #ddd;
  border-radius: 2px;
  padding: 0px;
}

.todo-empty {
  height: 40px;
  line-height: 40px;
  border: 1px solid #ddd;
  border-radius: 2px;
  padding-left: 5px;
  margin-top: 10px;
}
</style>
