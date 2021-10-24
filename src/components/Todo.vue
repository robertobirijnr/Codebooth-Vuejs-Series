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
            {{ task.text }}
            <button
              v-bind:title="message"
              class="btn btn-danger btn-sm float-right delete"
            >
              X
            </button>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      message: "click to remove todo item",
      seen: false,
      items: [
        { text: "Take your bath" },
        { text: "Learn Vue js" },
        { text: "Take coffee" },
        { text: "Sleep" },
      ],
      title: "",
      description: "",
    };
  },
  methods: {
    addTodo() {
      this.items.push({
        text: this.title,
      });
    },
  },
};
</script>

<style lang="scss" scoped></style>
