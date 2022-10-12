<template lang="">
    <div id="box">
        <input type="text" placeholder="请输入你的任务名称名称，按回车健确认" @keydown.enter="AddList" v-model="val" id="textin">
        <ul>     
            <li v-for="p of ShowList" :key="p.Id" v-if="!p.Isdel" @mouseover="Over" @mouseout="Out">
                <input type="checkbox" @click="Change($event,p)">
                {{p.Val}}
                <button @click="" v-show="isShow" @click="Delete(p)">删除</button>
            </li>
        </ul>
        <span>已完成{{done}}/总共有{{all}}</span>
        <button id="queren" @click="DelAll">确认完成</button>
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
            all:0,
            isShow:false,
            id:0
        }
       },
       methods:{
         AddList(e){
            this.ListArr.push({Id:this.id++,Val:this.val,Ischose:false,Isdel:false});
            e.target.blur();
            this.val='';
            this.all++;
         },
         Change(e,p){
          if(e.target.checked){
            this.done++;
            p.Ischose=true;
          }
           else{
            this.done--;
            p.Ischose=false;
           }
           
         },
         Over(e){
            this.isShow=true;
            e.target.style.background='rgba(0,0,0,.3)';
         },
         Out(e){
            this.isShow=false;
            e.target.style.background='rgba(0,0,0,0)';
         },
         Delete(p){
            if(p.Ischose){
                p.Ischose=false;
                this.done--;
            }
           p.Isdel=true;
           this.all--;
         },
         DelAll(){
            for(let i=0;i<this.ListArr.length;i++){
                if(this.ListArr[i].Ischose){
                    this.Delete(this.ListArr[i]);
                }
            }
         }
         
       },
       computed:{
          ShowList(){
            return this.ListArr;
          }
       },
};

</script>

<style scoped>
    #box {
       position: absolute;
       left: 50%;
       top: 50%;
       padding:20px;
       transform: translate(-50%,-200px);
       border:1px solid black;
    }
    #textin {
        height: 30px;
        width: 300px;
        margin-bottom: 10px;
    }
    ul li {
        font-size: 20px;
        margin:5px 0;
    }
    ul li input {
        float: left;
        height: 20px;
        width: 20px;    
        margin:3px 0;
    }
   ul li button {
    float: right;
    margin:3px 0;
   }
   #queren {
    float: right;
   }
</style>