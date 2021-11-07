<template>
  <div>
    <div class="container">
      <div id="main" class="card card-body">
        <h2 class="title">Add Item</h2>
        <form class="my-5">
          <div class="form-group">
            <label for="title">Title</label>
            <input
              v-model="title"
              class="form-control"
              placeholder="enter your title"
            />
          </div>
          <div class="form-group">
            <label for="description">Description</label>
            <textarea
              name="description"
              placeholder="please enter your description here!"
              class="form-control"
              rows="4"
              v-model="description"
            ></textarea>
          </div>
          <button @click.prevent="addTodo" class="btn btn-primary btn-block">
            Add task
          </button>
        </form>

        {{ title }}

        <ul
          v-for="(task, key) in items"
          :key="key"
          id="items"
          class="list-group"
        >
          <li class="list-group-item">
            {{ task.title }}
            <button
              v-bind:title="message"
              @click="getkey(key)"
              data-toggle="modal"
              data-target="#todoModal"
              class="btn btn-danger btn-sm float-right  delete"
            >
              <i class="fa fa-trash"></i>
            </button>
              <!-- Modal -->
            <div
              class="modal fade"
              id="todoModal"
              tabindex="-1"
              aria-labelledby="todoModalLabel"
              aria-hidden="true"
            >
              <div class="modal-dialog">
                <div class="modal-content">
                  <div class="modal-header">
                    <h5 class="modal-title" id="todoModalLabel">Delete</h5>
                    <button
                      type="button"
                      class="close"
                      data-dismiss="modal"
                      aria-label="Close"
                    >
                      <span aria-hidden="true">&times;</span>
                    </button>
                  </div>
                  <div class="modal-body">
                    Are you sure you want to do this?
                  </div>
                  <div class="modal-footer">
                    <button
                      type="button"
                      class="btn btn-secondary"
                      data-dismiss="modal"
                    >
                      Close
                    </button>
                    <button @click.prevent="deleteTodo" type="button" class="btn btn-danger">
                      confirm
                    </button>
                  </div>
                </div>
              </div>
            </div>


            <button
              v-bind:title="message"
              data-toggle="modal"
              data-target="#todoModal"
              class="btn btn-danger btn-sm mr-3 float-right delete"
            >
              <i class="fa fa-pencil"></i>
            </button>

          
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";


export default {
  data() {
    return {
      message: "click to remove todo item",
      seen: false,
      items: [],
      title: "",
      description: "",
      key :""
    };
  },
  methods: {
    addTodo() {
      const payload = {
        description: this.description,
        title: this.title,
      };

      axios.post(
        `${baseUrl}/todos.json`,
        payload
      );
    },

    getkey(key){
      this.key = key
    },

    deleteTodo(){
     
      const data = Object.keys(this.items).map(key =>{
        return this.items[key]
      })

       const index = data.findIndex(todo => console.log(todo))
      console.log(index)

    }
  },

  mounted(){
   axios.get(`${baseUrl}/todos.json`)
   .then(response =>{
     console.log(response.data)
     this.items = response.data
   })
  
  
 }

};
</script>

<style lang="scss" scoped></style>
