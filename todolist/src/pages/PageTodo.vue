<template>
  <q-page class="q-pa-md">
    <p>Todo Page</p>


    <q-list separator bordered v-if="Object.keys(tasks).length">
      <task
        v-for="( task, key ) in tasks"
        :key="key"
        :task="task"
        :id="key"
      ></task>
    </q-list>

    <div class="absolute-bottom text-right q-ma-lg">
      <q-btn
        @click="showAddTask = true"
        round
        color="primary"
        size="16px"
        icon="add"
      />
    </div>

    <q-dialog v-model="showAddTask">
      <add-task @close="showAddTask = false" />
    </q-dialog>
  </q-page>
</template>

<script>

import { mapGetters } from 'vuex'

export default {
  data(){
    return {
      showAddTask: false
    }
  },

  computed: {
    ...mapGetters('tasks',['tasks'])
  },
  components: {
    'task' : require('components/Tasks/Task.vue').default,
    'add-task' : require('components/Tasks/Modals/AddTask.vue').default
  }

}
</script>
