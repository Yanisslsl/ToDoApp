<template>
    
<div id="app">
        <div v-if="showAlert" @click="close" class="flex items-center bg-red-500 text-white text-sm font-bold px-4 py-3" role="alert">
  <svg class="fill-current w-4 h-4 mr-2" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20"><path d="M12.432 0c1.34 0 2.01.912 2.01 1.957 0 1.305-1.164 2.512-2.679 2.512-1.269 0-2.009-.75-1.974-1.99C9.789 1.436 10.67 0 12.432 0zM8.309 20c-1.058 0-1.833-.652-1.093-3.524l1.214-5.092c.211-.814.246-1.141 0-1.141-.317 0-1.689.562-2.502 1.117l-.528-.88c2.572-2.186 5.531-3.467 6.801-3.467 1.057 0 1.233 1.273.705 3.23l-1.391 5.352c-.246.945-.141 1.271.106 1.271.317 0 1.357-.392 2.379-1.207l.6.814C12.098 19.02 9.365 20 8.309 20z"/></svg>
  <p>Vous n'avez entrez aucune tâche </p>
</div>
        <form v-on:submit.prevent="addNew">
<input type='text' v-model='newTask' placeholder='Ajouter votre tâche'>
       
        <button type="submit">Ajouter Tache</button>

        </form>
        

        
        <ul class="list-group">
            <li class="list-group-item" v-for="(task, index) in tasks" v-bind:key="task">


                {{task.text}}
                <i class="bi bi-trash" @click="closed(index)"></i>  
            </li>
            {{ message}}
           
          </ul>
           <div class="flex items-center justify-center h-screen">
    
	<div class="bg-indigo-800 text-white font-bold rounded-lg border shadow-lg p-10">
		Centered Content
	</div>
	
  </div>
    </div>
    

</template>
<script>
export default {
 
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
            this.newTask != '' ? this.tasks.push({text: this.newTask})  : this.showAlert = true
            
           
        }, 
        closed(index){
            this.tasks.splice(index, 1)
        }, 
        close(){
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