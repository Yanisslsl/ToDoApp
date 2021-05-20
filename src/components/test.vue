<template>
    
<div id='test'>
  <p class="text-8xl">TODO List</p>
    
<!--     
       <alert v-if='showAlert' @close='hideAlert'></alert> -->

<!-- <div class="flex items-center justify-center md:flex">
        <form v-on:submit.prevent="addNew" class="w-1/2 bg-white shadow-md rounded px-8 pt-6 pb-8 mb-4 space-x-20">
<input type='text' v-model='newTask' placeholder='Ajouter votre tâche'>
       
        <button class="items-center" type="submit">Ajouter Tâche</button>

        </form>
        </div>
         -->

        
<div class=" flex items-center justify-center w-full">
        <ul class="w-1/2">
        <!-- <list-item  @mouseover='selected' v-for="(item,index) in tasks"
                :key="index"
                :item="item.text"  @closed="closed(index)" @edit="edit()" :isEditing="isEditing">{{item.text}}</list-item> -->
          <li  class=" bg-white shadow-md rounded px-8 pt-6 pb-8 mb-4  " v-for="task in taskList" v-bind:key="task">
            <strong v-if='!task.editing'>{{task.content}}</strong>
            <input v-model="task.content" v-if='task.editing' @keyup.enter="edit(task)" type="text" >
            <div class ="flex items-center justify-between" v-if='!task.isDone'>
              
              <img src="../assets/checked.png" @click='completeTask(task)' class='h-6 w-6'>
              <img src='../assets/edit-button.png' @click='task.editing = true' class='h-6 w-6'>
              <img src='../assets/delete.png' @click='closed(task)' class='h-6 w-6'>
              
                        
                 
            </div>
            <div class="flex items-center justify-center text-base" v-else>

            <button type='button' class='line-through text-2xl font-bold text-green-600' >Completed</button>
            </div>

          </li>
            <alert v-if="isAlert" @close='close' ></alert>
           <li class="bg-white shadow-md rounded px-8 pt-6 pb-8 mb-4  ">
                <input v-model="newTask" @keyup.enter="addNew" type="text" class="">
                <button class="pl-2 font-bold" @click="addNew">Add Task</button>
            </li>
            
           
           
          </ul>
    </div>
         
   </div>
    
    

</template>
<script>
import Alert from './alert.vue'
// import alert from './alert.vue'
// import ListItem from './listItem.vue'
export default {
  data () {
    return {
      taskList : [
        {content:'Allez faire les courses', isDone: false, editing: false},
        {content:'Manger', isDone: false, editing: false},
        {content:'ALlez faire le ménage', isDone: false, editing: false}
      ],
      newTask : '',
      isDone: null,
      completed: false,
      isAlert : false
    }
  },
  components: {Alert   },
 
  name: 'test',

  methods: {
        addNew(){
          if(this.newTask != ''){
            this.taskList.push({content: this.newTask, isDone: false, editing: false}) 
            this.newTask = ''
          } else {
            this.isAlert = true
          }
           
            
           
        }, 
        completeTask(task){
          
          task.isDone = true
          console.log(task.isDone)
        },
        closed(task){
            this.taskList.splice(this.taskList.indexOf(task), 1)
        }, 
        edit(task){
          task.editing = false
          

        },
        hideAlert(){
            this.showAlert = false
        },
        close(){
          this.isAlert= false
        }
    }
}
</script>


<style>
body {
  margin: 0;
  font-family: Arial, Helvetica, sans-serif;
}

.topnav {
  overflow: hidden;
  background-color: #333;
}

.topnav a {
  float: left;
  color: #f2f2f2;
  text-align: center;
  padding: 14px 16px;
  text-decoration: none;
  font-size: 17px;
}

.topnav a:hover {
  background-color: #ddd;
  color: black;
}

.topnav a.active {
  background-color: #04AA6D;
  color: white;
}
</style>