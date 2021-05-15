<template>
    
 <li @click="closed" class=" bg-white shadow-md rounded px-8 pt-6 pb-8 mb-4  " >
                
            


                {{item}}
                
            </li>

</template>
<script>
export default {
  methods: {
      closed(){
          this.$emit('closed')
      }
  },
 name: 'listItem',
 props : {
     item: String
 }
  
 
}
</script>
