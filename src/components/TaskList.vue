<template>
  <div class="task-container">
    <add-task-modal v-if="showModal" :show="showModal" @submitTask="addTask" @cancelModal="showModal = false" />
    <h2>{{ msg }}</h2>
    <button class="task-container__add-btn" @click="showModal = true">Add task</button>    
    <div v-if="list.length" class="task-list">
      <div 
        class="task-list__task" 
        v-for="(item,id) in list" 
        :key="id" 
        :class="{'task--complete': item.done}" 
        @click="markTask(id)"
      >
        <span class="task-list__task__desc" :class="{'task__desc--strikethrough': item.done}">{{ item.task }}</span>
      </div>
    </div> 
    <div v-else class="empty-tasks-placeholder">No open tasks</div>   
  </div>
</template>

<script>
import AddTaskModal from './modal/AddTaskModal.vue'
import { default as list } from '../mocks/task-list.json';
export default {
  name: 'task-list',
  components: {
    AddTaskModal
  },
  props: {
    msg: String    
  },
  data(){
    return {
      list,
      showModal: false
    }
  },
  methods: {
    /**
     * This adds a brand new task to the task list
     * @param String task
     */
    addTask(task){
      this.showModal = false;
      this.list.push({
         task,
         done: false
       });
    },
    /**
     * This marks a task in the task list as complete or incomplete
     * @param Number task-id
     */
    markTask(id){
       this.list[id].done = !this.list[id].done;
    },
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.task-container {  
  height: 58vh;
}
.empty-tasks-placeholder {
  background: #fbf8f8;
  color: #675858;
  height: 100%;
  font-size: 2.2rem;
  display: flex;
  justify-content: center;
  align-items: center;
  margin-top: 20px;
}
.task-container__add-btn {
  border: none;
  font-size: 1.5rem;
  padding: 9px;
  border-radius: 4px;
  color: #675858;
  cursor: pointer;
}
.task-container__add-btn:hover {
  background: #675858;
  color: white;
}
.task-list {
  display: flex;
  flex-wrap: wrap;
  height: 88%;
  justify-content: center;
}
.task-list__task {
  flex: 1 1 31.4%;
  border-radius: 8px;
  border: 2px solid #daf5c0;
  background:#daf5c0;
  color: rgb(29, 95, 29);
  cursor: pointer;
  margin: 8px;
  padding: 8px;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
  height: 76px;
  overflow-y: auto;
}
.task-list__task:hover {
  border: 2px solid rgb(185, 189, 235);
  background: rgb(185, 189, 235);
  color: rgb(47, 47, 83);
}
.task--complete {
  border: 2px solid  rgb(247, 201, 209);
  background: rgb(247, 201, 209);
  color: rgb(221, 49, 49);
}
.task-list__task__desc {
  font-size: 1.2rem;
}
.task__desc--strikethrough {
  text-decoration: line-through;
}
</style>
