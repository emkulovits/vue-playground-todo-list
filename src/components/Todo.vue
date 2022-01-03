<template>
  <div class='ui centered card'>
    
    <!-- read-only view -->
    <div class='content' v-show="!isEditing">
        <div class='header'>
            {{ todo.title }}
        </div>
        <div class='meta'>
            {{ todo.project }}
        </div>
        <div class='ui label'>
            {{ todo.tags }}
            <i class="delete icon"></i>
        </div>
        <div class='extra content'>
           <span class='right floated edit icon' v-on:click="showForm">
            <i class='edit icon'></i>
          </span>
          <span class='right floated trash icon' v-on:click="deleteTodo(todo)">
            <i class='trash icon'></i>
          </span>
        </div>
    </div>
    
    <!-- form in editing mode-->
    <div class="content" v-show="isEditing">
      <div class='ui form'>
        <div class='field'>
          <label>Title</label>
          <input type='text' v-model="todo.title" />
        </div>
        <div class='field'>
          <label>Project</label>
          <input type='text' v-model="todo.project" />
        </div>
        <div class='field'>
          <label>Tags</label>
          <input type='text' v-model="todo.tags" />
        </div>
        <div class='ui two button attached buttons'>
          <button class='ui basic blue button' v-on:click="hideForm">
            Close X
          </button>
        </div>
      </div>
    </div>

    <div class='ui bottom attached green basic button' v-show="!isEditing &&todo.done" disabled v-on:click="uncompleteTodo(todo)">
        Completed
    </div>
    <div class='ui bottom attached red basic button' v-show="!isEditing && !todo.done" v-on:click="completeTodo(todo)" >
        Pending
    </div>

</div>
</template>

<script type="text/javascript">
  export default {
  data() {
    return {
      isEditing: false,
    };
  },
  props: ['todo'],
  methods: {
    showForm() {
      this.isEditing = true;
    },
    hideForm() {
      this.isEditing = false;
    },
    deleteTodo(todo) {
      this.$emit('delete-todo', todo);
    },
    completeTodo(todo) {
      this.$emit('complete-todo', todo);
    },
    uncompleteTodo(todo) {
      this.$emit('uncomplete-todo', todo);
    },
  },
};
</script>