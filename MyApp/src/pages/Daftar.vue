<template>
  <q-page class="bg-grey-3 column">
    <q-list 
    class="bg-white"
    separator
    bordered>
      <q-item 
      v-for="(task, index) in tasks"
      :key="task.title"
      @click="task.done = !task.done" 
      :class="{ 'done bg-blue-1' : task.done }"
      clickable
      v-ripple>
        <q-item-section avatar top>
          <q-checkbox 
          v-model="task.done"  
          class="no-pointer-events"
          color="primary" />
        </q-item-section>
        <q-item-section>
          <q-item-label>{{ task.title }}</q-item-label>
        </q-item-section>
            <q-item-section
            v-if="task.done"
            side>
          <q-btn 
          @click.stop="deleteTask(index)"
          flat 
          dense
          round 
          color="primary" 
          icon="delete" />
        </q-item-section>
      </q-item>
    </q-list>
  </q-page>
</template>

<script>
export default {
  data() {
    return {
      tasks: [
        {
          title: 'Get pict',
          done: false
        },
        {
          title: 'Up pict',
          done: true
        },
        {
          title: 'Load pict',
          done: false
        }
      ]
    }
  },
  methods: {
    deleteTask(index) {
      this.tasks.splice(index, 1)
    }
  }
}
</script>

<style lang="scss">
  .done {
    .q-item__label {
      text-decoration: line-through;
      color: #bbb;
    }
  }
</style>