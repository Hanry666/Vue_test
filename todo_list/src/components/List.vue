<template lang="">
    <div id="box">
        <input type="text" placeholder="请输入你的任务名称名称，按回车健确认" @keydown.enter="AddList" v-model="val">
        <ul>     
            <li v-for="(p,index) of ShowList" :key="index"><input type="radio" @click="Change" >{{p}} <button @click="">删除</button></li>
        </ul>
        <span>已完成</span>
    </div>
</template>
<script>
export default {
       name:'List',
       data(){
        return {
            ListArr:[
               
            ],
            val:'',
            done:0,

        }
       },
       methods:{
         AddList(e){
            this.ListArr.push(this.val);
            console.log(this.ListArr);
            e.target.blur();
            this.val='';
         },
         Change(){
           this.value=!this.value;
         }
       },
       computed:{
          ShowList(){
            console.log(123);
            return this.ListArr;
          }
       }
}
</script>
<style scoped>
    #box {
       position: absolute;
       left: 50%;
       top: 50%;
       transform: translate(-50%,-200px);
    }
    input {
        height: 50px;
        width: 300px;
    }
    ul li {
        font-size: 20px;
    }
    ul li input {
        float: left;
        height: 20px;
        width: 20px;    
    }
   ul li button {
    float: right;
   }
</style>