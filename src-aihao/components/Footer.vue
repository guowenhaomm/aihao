<template>
    <div class="todo-footer">
        <label>
            <input type="checkbox" v-model="isALL" />
        </label>
        <span>
            <span>已完成{{Fulfill}}</span> / 全部{{addALL}}
        </span>
        <button class="btn btn-danger" @click="DeleteALLs">清除已完成任务</button>
    </div>
</template>

<script>
export default {
  data () {
    return {
      name: ''
    }
  },
  props:{
    userOBJ:Array,
    Alltrue:Function,
    Accomplish:Function
  },
  methods: {
    DeleteALLs(){ 
      this.Accomplish()
    }
  },
  computed:{
    // 全部任务
    addALL(){
      return this.userOBJ.length
    },
    // 完成的任务
    Fulfill(){

    return  this.userOBJ.filter((item)=> item.istrue).length
    // this.userOBJ.reduce((prev,itme,index,arr)=>{
    //     console.log(prev)
    //       if(itme.istrue){
    //          prev += 1
    //       }
    //       return prev
    //   },0)
    },
    isALL:{
      get(){
        return this.addALL === this.Fulfill && this.Fulfill >= 0
      },
      // 当我值有变化的时候就会触发
      set(val){

        this.Alltrue(val)
      }
    }
  }
}
</script>

<style scoped>
/*footer*/
.todo-footer {
  height: 40px;
  line-height: 40px;
  padding-left: 6px;
  margin-top: 5px;
}

.todo-footer label {
  display: inline-block;
  margin-right: 20px;
  cursor: pointer;
}

.todo-footer label input {
  position: relative;
  top: -1px;
  vertical-align: middle;
  margin-right: 5px;
}

.todo-footer button {
  float: right;
  margin-top: 5px;
}

</style>
