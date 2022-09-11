<template>
    <div class="task-input">
        <input class="task-input__text my-style" v-model="description" placeholder="Напишите задачу" type="text">
        <button @click="onAddTask" class="task-input_button my-style" >Добавить задачу</button>
    </div>
</template>

<script>
    import { ref } from 'vue'

    export default {
        emits: {
            onAddTask({ description }) {
                if(description === '') {
                    alert('Задача не может быть пустой')
                    return false
                }
                return true
            }
        },
        setup(props, { emit }) {
            const description = ref('')

            const onAddTask = () => {
                emit('onAddTask', { description: description.value })
                description.value = ''
            }

            return {
                description,
                onAddTask
            }
        }
    }
</script>

<style scoped>
    .task-input {
        display: flex;
        justify-content: space-between;
        margin: 10px 0;
    }

    .task-input__text{
        border-radius: 5px 0 0 5px;
        flex-grow: 1;
        padding: 15px;
    }

    .task-input_button{
        background-color: #33aa33;
        border-radius: 0 5px 5px 0;
        color: #ffffff;
        margin-left: 10px;
        padding: 5px 15px; 
    }
</style>
