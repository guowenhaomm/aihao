<template>
    <div class="todo-header">
    <input type="text" placeholder="请输入你的任务名称，按回车键确认" v-model="tile" @keyup.13='testKey'/>
    </div>
</template>

<script>
export default {
  data () {
    return {
      name: '',
      tile:''
    }
  },
  methods: {
    testKey(){
      // 判断是否为空
      if(this.tile.trim()){
        // 获取框的内容
        let {tile} = this;
        // 创建随机id
        let id = new Date().getTime();
        // 创建添加的对象 记得一样要和之前那个对象数据一致
        let obj ={
          id,
          tile,
          istrue:false
        }
        // 启动回调 
        this.$emit('AddHobby',obj)
      }else{
        // 回应用户
        alert('请输入合法的任务')
      }

      this.tile = ''
    }
  }
}
</script>

<style scoped>
/*header*/
.todo-header input {
  width: 560px;
  height: 28px;
  font-size: 14px;
  border: 1px solid #ccc;
  border-radius: 4px;
  padding: 4px 7px;
}

.todo-header input:focus {
  outline: none;
  border-color: rgba(82, 168, 236, 0.8);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 8px rgba(82, 168, 236, 0.6);
}
</style>
