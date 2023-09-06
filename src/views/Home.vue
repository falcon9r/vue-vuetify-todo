<template>
  <div class="home">

    <v-text-field label="Add new task" variant="outlined" append-icon="mdi-plus" class="pa-5" hide-details clickable
      v-model="newTaskTitle" @click:append="newTask" @keyup.enter="newTask"></v-text-field>

    <v-list lines="three" select-strategy="classic" class="pt-0">
      <div v-for="task in tasks" :key="task.id">
        <v-list-item :value="task.id" @click="task.done = !task.done" :class="{ 'blue-lighten-5': task.done }">
          <template v-slot:prepend>
            <v-list-item-action start>
              <v-checkbox-btn :model-value="task.done"></v-checkbox-btn>
            </v-list-item-action>
          </template>

          <v-list-item-title :class="{ 'text-decoration-line-through': task.done }">{{ task.title }}</v-list-item-title>

          <template v-slot:append>
            <v-list-item-action>
              <v-icon color="red" @click.stop="deleteTask(task.id)" icon="mdi-tab-remove" size="x-large"></v-icon>
            </v-list-item-action>
          </template>


        </v-list-item>
        <v-divider></v-divider>
      </div>
    </v-list>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTaskTitle: '',
      tasks: [
        {
          id: 1,
          title: 'Wake up',
          done: false
        },
        {
          id: 2,
          title: 'test',
          done: true
        }
      ]
    }
  },
  methods: {

    deleteTask(taskId) {
      this.tasks = this.tasks.filter(task => task.id !== taskId);
    },

    newTask() {
      let task = {
        title: this.newTaskTitle,
        id: Date.now(),
        done: false
      }
      this.new
    }
  }
}
</script>
