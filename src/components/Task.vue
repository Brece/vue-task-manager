<template>
    <div @:dblclick="$emit('toggle-reminder', task.id)" :class="[ task.reminder ? 'reminder' : '' , 'task']">
        <h3>
            {{ task.text }}
            <i @click="onDelete(task.id)" class="fa-solid fa-circle-xmark"></i>
        </h3>
        <h3>{{ task.day }}</h3>
    </div>
</template>

<script>
    export default {
        name: 'TaskComponent',
        props: {
            task: Object
        },
        methods: {
            onDelete(id) {
                this.$emit('delete-task', id);
            }
        },
        emits: ['toggle-reminder']
    }
</script>

<style scoped>
    .task {
        background: #f4f4f4;
        margin: 5px;
        padding: 10px 20px;
        cursor: pointer;
    }

    .task.reminder {
        border-left: 5px solid green;
    }

    .task h3 {
        display: flex;
        justify-content: space-between;
        align-items: center;
    }

    .task i {
        color: red;
    }
</style>