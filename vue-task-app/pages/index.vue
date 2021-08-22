<template>
  <div class="container h-100">
    <div class="row h-100">
      <div class="col-12 mx-auto">
        <div class="jumbotron text-center mt-5">
       <a href="https://www.xhostcom.com" target="_blank" title="Fish">
                                        <img src="@/assets/img/logo_small.png" alt="Task">
   </a>
   <p class="lead">Yip, its an app to send tasks to a todo api repeatedly!</p>
   <h3>
   Input task in a one liner.
   </h3>
   </div>
   <div class="mb-5">
  <form>
  <div class="form-group">
  <label for="name">Describe Tash</label>
    <input id="name" type="text" class="form-control" ref="task" v-model="task">
    
     </div>
     <button class="btn btn-success mb-3" @click.prevent="getFormValues()">
    Save It
  </button>
   <button class="btn btn-secondary mb-3" @click.prevent="pushApi()">
    Send To Api
  </button>
  </form>
  <h3>{{task}}</h3>
   </div>
  </div>  
  </div>
  </div>
  
</template>

<script>
import axios from 'axios';
export default {
   data() {
     return {
   task: '',
     }
  },
 
  methods: {
    getFormValues () {
      let task
      this.task = this.$refs.task.value
      task =  { "task": `${this.task}` }
      console.log(task)
     
  },
  //example Rails api to post task data to.
  pushApi() {
    let task
    task =  { "task": `${this.task}` }
    const postTask = task;
      axios
  .post('http://localhost:3000/todos', postTask)
  .then(function (response) {
    console.log(response);
  })
}
}
}

</script>
<style>
#__layout {
  height: 100vh;
}
.jumbotron {
  background-color: rgb(238, 228, 228);
}

</style>

