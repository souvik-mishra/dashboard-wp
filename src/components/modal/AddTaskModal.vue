<template>
  <div v-if="show" class="modal-bd">
    <div class="add-task">
        <header class="add-task__header">
            <span class="add-task__header__text">What do you want to do?</span>
            <span class="add-task__header__cancel" @click="cancel">X</span>
        </header>
        <section class="add-task__input">
            <textarea class="add-task__input__box" type="text" v-model="task" placeholder="Type in your task"/>
        </section>        
        <footer class="add-task__footer">
            <button class="add-task__footer__cancel-btn" @click="cancel">Cancel</button>
            <button class="add-task__footer__submit-btn" @click="submit">Submit</button>
        </footer>
    </div>
 </div>  
</template>

<script>
export default {
  name: 'add-task-modal',
  props: {
    show: Boolean   
  },
  data(){
    return {
      task: ""
    }
  },
  methods: {
    /**
     * This submits a brand new task to the task list
     */
    submit(){
       this.$emit("submitTask", this.task);
    },
    /**
     * This cancels the task addition
     */
    cancel(){
       this.$emit("cancelModal");
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.modal-bd {
    position: fixed;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
    background-color: rgba(0, 0, 0, 0.3);
    display: flex;
    justify-content: center;
    align-items: center;
}
.add-task {
    background: white;
    width: 33vw;    
    border-radius: 8px;
}
.add-task__header {
    display: flex;
    padding: 12px;
    justify-content: space-between;
    height: 20px;
    border-bottom: 1px solid lightgrey;
    font-size: 1.1rem;
}
.add-task__header__cancel {
    cursor: pointer;
}
.add-task__input {
    height: 134px;
    display: flex;
    justify-content: center;
    align-items: center;
}
.add-task__input__box {
    resize: none;
    height: 80%;
    width: 90%;
    font-family: 'Roboto', sans-serif;
    font-size: 1rem;
}
.add-task__footer {
    border-top: 1px solid lightgrey;
    height: 36px;
    padding: 12px;
    display: flex;
    justify-content: flex-end;
}

.add-task__footer > button {
    border: none;
    font-size: 1.1rem;
    padding: 8px;
    border-radius: 4px;
    cursor: pointer;
}

.add-task__footer > button:hover{
    background: #675858;
    color: white;
}
.add-task__footer__cancel-btn {
    background: rgb(185, 189, 235);
    color: rgb(47, 47, 83);
}
.add-task__footer__submit-btn {    
    margin-left: 8px;
    color: white;
    background: rgb(47, 47, 83);
}
</style>