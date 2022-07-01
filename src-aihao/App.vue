<template>
  <div class="todo-container">
    <div class="todo-wrap">
      <Header @AddHobby='AddHobby'/>
      <List :userOBJ='userOBJ' :isAddtrue='isAddtrue' :DeleteOclik='DeleteOclik'/>
      <Footer :userOBJ='userOBJ' :Alltrue='Alltrue' :Accomplish='Accomplish'/>
    </div>
  </div>
</template>

<script>
import Header from '@/components/Header.vue'
import Footer from '@/components/Footer.vue'
import List from '@/components/List.vue'

export default {
  data () {
    return {
      name: '',
      //创建假数据
      userOBJ:[
        {id:1,tile:'篮球',istrue:false},
        {id:2,tile:'兵乒球',istrue:true},
        {id:3,tile:'足球',istrue:true}
      ]
    }
  },
  components:{
    // 注册组件
    Header,
    Footer,
    List
  },
  methods: {
    //header 回车然后添加当前输入对象
    AddHobby(obj){
      this.userOBJ.unshift(obj);
    },
    // 是否打对错
    isAddtrue(index){
      this.userOBJ[index].istrue = !this.userOBJ[index].istrue
    },
    // 删除一个
    DeleteOclik(index){
      this.userOBJ.splice(index,1)
    },
    // 是否所以任务完成   完成就打对    没有完成就不打对
    Alltrue(val){
      this.userOBJ.forEach(item => item.istrue = val);
    },
    // 点击把所以已完成的任务消除
    Accomplish(){
      this.userOBJ = this.userOBJ.filter((item)=> !item.istrue)
    }
  }
}
</script>

<style scoped>
/*app*/
.todo-container {
  width: 600px;
  margin: 0 auto;
}
.todo-container .todo-wrap {
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 5px;
}
</style>
