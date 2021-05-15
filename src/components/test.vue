<template>
    
<div id='test'>
  <p class="text-8xl">TODO List</p>
    
    
       <alert v-if='showAlert' @close='hideAlert'></alert>

<div class="flex items-center justify-center">
        <form v-on:submit.prevent="addNew" class="w-1/2 bg-white shadow-md rounded px-8 pt-6 pb-8 mb-4 space-x-20">
<input type='text' v-model='newTask' placeholder='Ajouter votre tâche'>
       
        <button type="submit">Ajouter Tâche</button>

        </form>
        </div>
        

        
<div class=" flex items-center justify-center w-full">
        <ul class="w-1/2">
        <list-item  @mouseover='selected' v-for="(item,index) in tasks"
                :key="index"
                :item="item.text" @closed="closed(index)">{{item.text}}</list-item>
            
           
           
          </ul>
    </div>
         
   </div>
    
    

</template>
<script>
import alert from './alert.vue'
import ListItem from './listItem.vue'
export default {
  data () {
    return {
    }
  },
  components: { alert,  ListItem },
 
  name: 'test',
  props: {
    
      message: {
          type: String,
          default: 'salut les copaiins'
      },
        newTask: {
            type: String,
            default: ""
        },
        tasks: {
            type: Array,
            default:() => [
            {text: "manger"},
            {text: 'nager'},
            {text: "se mouvoir"}
            
    ]
        },
        showAlert: {type: Boolean,
        default: false
        }
       
  }, 
  methods: {
        addNew(){
          if(this.newTask != ''){
            this.tasks.push({text: this.newTask}) 
            this.newTask = ''
          } else {
            this.showAlert = true
          }
           
            
           
        }, 
        selected(){

        },
        closed(index){
            this.tasks.splice(index, 1)
        }, 
        hideAlert(){
            this.showAlert = false
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