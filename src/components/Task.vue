<template>
    <div class="task my-style">
        <div>
            <span>{{ model.description }}</span>
        </div>
        <div>
            <div class="task__button" v-on:click="emitOnRemove">&#215;</div>
        </div>
    </div>
</template>

<script>
    //@click="emitOnRemove"
    export default {
        emits: ['onRemove'],
        props: {
            model: {
                required: true,
                default: {
                    id: 0,
                    description: 'Create todo list'
                }
            }
        },
        setup(props, { emit }) {
            const emitOnRemove = () => {
                emit('onRemove')
            }

            return {
                emitOnRemove
            }
        }
    }
</script>

<style scoped>
    .task{
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 10px;
        border-radius: 5px;
    }

    .task__button{
        font-size: 30px;
        font-weight: 100;
        color: #ff0000;
        cursor: pointer;
        -webkit-touch-callout: none;
	    -webkit-user-select: none;
	    -khtml-user-select: none;
	    -moz-user-select: none;
	    -ms-user-select: none;
	    user-select: none;
    }
</style>
