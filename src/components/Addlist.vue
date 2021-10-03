<template>

    <div class="continer">
        <h1>To Do List</h1>
      <div class="divinput">
        <input type="text" v-model="newItem" placeholder="Type and enter..." @keyup.enter="addItem()">
        <button class="btnadd"  @click="add()">+Add</button>
      </div>

      <div class="divbtn">
       <button class="btnHeader" @click="items.filter(completeAll)">Complete all</button>
      <button class="btnHeaderClear" @click="items.filter(clearCompleted)">Clear Completed</button>   
      
    </div> 

    <div class="divAddRemove">
      <ul v-for:= "item in items"  v-show="item.status" >
        <li @click="lineThrough(item)" :class="{checked:item.check}">{{ item.name }}</li>
        <button class="btnClose" @click="remove(item)">x</button>
      </ul>
    </div>
    <div class="divfooter">
     
    </div>
     <button @click="items.filter(viewAll)"  class="btnFooter">All</button>
      <button @click="items.filter(viewCompleted)" :class="{active:items.check}" class="btnFooter">Completed</button>
      <button @click="items.filter(viewUncompleted)" :class="{active:items.check}" class="btnFooter">Un completed</button>
  </div>
</template>

<script>
export default {
  name: "Addlist",
  data(){
    return{
      newItem:"",
      items: [
         {name: 'Clean' ,status:true , check: false},
         {name: 'Bye Bitcoin', status:true, check: false},
         {name: 'Bye Doge', status:true, check: false},
      ],
    }
  },
  methods:{
    addItem: function(){
      if(this.newItem ===''){
        alert("You must write something!")
      }
      else{
        this.items.push({
        name : this.newItem,
        status: true ,
        check:false,
        })
      }
      this.newItem = ''
    },
    remove(item) {
        this.items.splice(this.items.indexOf(item), 1)
      
    },
    lineThrough(item){
      item.check = !item.check
    },
    completeAll(arry){
      if(!arry.check)
        arry.check = true
    },
    clearCompleted(arry){
      if(arry.check){
        arry.check = false
        
      }
    },
    viewAll(arry){
      if(arry)
        arry.status = true
    },
    viewCompleted(arry){
      if(!arry.check)
        arry.status = false
      if(arry.check)
        arry.status = true
    },
    viewUncompleted(arry){
      if(!arry.check)
        arry.status = true
      if(arry.check)
        arry.status = false
    },

  },
    
}
</script>

<style scoped>
  .continer{
    width: 90%;
    margin: auto;
    color: #303030;
  }
  .divheader{
    display: flex;
    justify-content: center;
    border-radius: 40px;
  }
  h1{
    color: rgba(56, 53, 206, 0.685);
    background-color: transparent;
    box-shadow: 1px 1px 40px -10px #31505f30, 1px 1px 0px 0px #31505f30;
    text-shadow: 1px 1px #31505f30;
    padding: 10px;
    border-radius:10px;
  }
  h1:hover{
    color:transparent;
  }
  .divinput{
    width: 100%;
    display: flex;
    justify-content: space-between;
  }
  .btnadd{
    height: 40px;
    width: 50px;
    font-size: 16px;
    font-weight: bolder;
    background-color:transparent;
    border:0;
    border-radius: 0 5px 5px 0;
    cursor: pointer;
    color: rgb(227, 250, 227);
    background-color: #51ed51bd;
    box-shadow: 1px 1px 40px -10px #31505f30, 1px 1px 0px 0px #31505f30;
  }
  .btnadd:hover{
    background-color:#51ed51;
  }
  .divinput input {
    width: 100%;
    height: 40px;
    border:0;
    background-color: #f0f0f0d5;
    color: darkgray;
    font-size: 15px;
    font-weight:bold;
    border-radius: 5px 0 0 5px;
    padding:0px 0px 0px 5px;
    box-shadow: 1px 1px 40px -10px #31505f30, 0px 1px 2px 0px #31505f30;
    outline: none;

  }
  .divAddRemove{
    width: 90%;
    font-size: 12px;
    text-shadow: 1px 1px #31505f30;
    font-weight: bold;
    margin: auto;
  }
  ul{
    padding: 5px;
    position: relative;
  }
  ul li{
    cursor: pointer;
    list-style: none;
    border-bottom: 1px solid rgb(192, 190, 211);
    display: flex;
    font-size: 15px;
    padding-bottom: 20px;
  }
  ul li:hover{
    color: rgb(15, 194, 2);
  }
  ul li.checked {
    text-decoration: line-through;
    color: rgb(15, 194, 2);
  }
 .btnClose {
    font-size: 20px;
    background-color: transparent;
    border: 0;
    padding: 0;
    cursor: pointer;
    position:absolute;
    top: 0;
    right: 0;
  }
  .btnClose:hover{
    color:rgb(255, 0, 0);

  }
  .divbtn{
    display: flex;
    padding: 10px;  
  }
  .btnHeader{
    min-width: 50%;
    margin: auto;
    height: 40px;
    margin: 3px;
    font-size: 11px;
    font-weight: bold;
    border: 0;
    color: rgb(78, 78, 78);
    cursor: pointer;
    background-color:transparent;
    box-shadow: 1px 1px 20px -5px #31505f30, 0px 1px 2px 0px #31505f30;
  }
  .btnHeader:hover{
    background-color: #70ed51bd;

  }
  .btnHeaderClear{
    min-width: 50%;
    margin: auto;
    height: 40px;
    margin: 3px;
    font-size: 11px;
    font-weight: bold;
    border: 0;
    color: rgb(78, 78, 78);
    cursor: pointer;
    background-color:transparent;
    box-shadow: 1px 1px 20px -5px #31505f30, 0px 1px 2px 0px #31505f30;
  }
  .btnHeaderClear:hover{
    background-color: #ed5151bd;
  }
 
  .divfooter{
    display: flex;
    justify-content: space-around;
    padding: 5px;
  }
  .btnFooter{
    min-width: 30%;
    margin: auto;
    height: 40px;
    margin: 3px;
    font-size: 11px;
    font-weight: bold;
    border: 0;
    color: rgb(78, 78, 78);
    cursor: pointer;
    background-color:transparent;
    box-shadow: 1px 1px 20px -2px #31505f30, 0px 1px 2px 0px #31505f30;
  }
  .btnFooter:hover{
    background-color: #5451edbd;
  }
  .btnFooter.active{
    background-color: #5451edbd;

  }
  

</style>