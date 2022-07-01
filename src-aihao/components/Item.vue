<template>
<li @mouseenter="Issue = true" @mouseleave="Issue = false" :class="{isBackground : Issue}">
    <label>
    <!-- <input type="checkbox" :checked='userOBJS.istrue'/> -->
    <input type="checkbox" v-model="ISoevr" @click="Repeatedly"/>
    <span>{{userOBJS.tile}}</span>
    </label>
    <button class="btn btn-danger" v-show="Issue" @click="DeleteS">删除</button>
</li>
</template>

<script>
export default {
  data () {
    return {
      name: '',
      Issue:false
    }
  },
  // props:['userOBJS'],
  props:{
    userOBJS:Object,
    index:{
      type:Number,
      default:0
    },
    isAddtrue:Function,
    DeleteOclik:Function
  },
  methods: {
    Repeatedly(){
      this.isAddtrue(this.index)
    },
    DeleteS(){
      this.DeleteOclik(this.index)
    }
  },
  computed:{
    ISoevr:{
      get(){
        return this.userOBJS.istrue
      },
      set(){
        
      }
    }
  }
}
</script>

<style scoped>
.isBackground {
  background-color: pink;
} 

/*item*/
li {
  list-style: none;
  height: 36px;
  line-height: 36px;
  padding: 0 5px;
  border-bottom: 1px solid #ddd;
}

li label {
  float: left;
  cursor: pointer;
}

li label li input {
  vertical-align: middle;
  margin-right: 6px;
  position: relative;
  top: -1px;
}

li button {
  float: right;
  /* display: none; */
  margin-top: 3px;
}

li:before {
  content: initial;
}

li:last-child {
  border-bottom: none;
}
</style>
