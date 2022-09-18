<template>
    <form @submit="onSubmit" class="add-form">
        <div class="form-control">
            <label for="task">Task</label>
            <input type="text" id="task" v-model="text" name="text" placeholder="Add Task">
        </div>
        <div class="form-control">
            <label for="day">Day & Time</label>
            <input type="text" id="day" v-model="day" name="day" placeholder="e.g. January 1 2022">
        </div>
        <div class="form-control form-control-check">
            <label for="reminder">Set Reminder</label>
            <input type="checkbox" id="reminder" v-model="reminder" name="reminder">
        </div>

        <input type="submit" value="Save Task" class="btn btn-block">
    </form>
</template>

<script>
    export default {
        name: 'addTaskComponent',
        data() {
            return {
                text: '',
                day: '',
                reminder: false
            }
        },
        methods: {
            onSubmit(e) {
                e.preventDefault();
                
                if(!this.text) {
                    alert('Please add a task');
                    return;
                }

                // create new task if task value is not empty
                const newTask = {
                    id: new Date().getTime(),
                    text: this.text,
                    day: this.day,
                    reminder: this.reminder
                }

                // emit new task to parent component and update tasks array
                this.$emit('add-task', newTask);

                // reset form value when successfully submitted
                this.text = '';
                this.day = '';
                this.reminder = false;
            }
        }
    }
</script>

<style scoped>
    .add-form {
        margin-bottom: 40px;
    }

    .form-control {
        margin: 20px 0;
    }

    .form-control label {
        display: block;
    }

    .form-control input {
        width: 100%;
        height: 40px;
        margin: 5px;
        padding: 3px 7px;
        font-size: 17px;
    }

    .form-control-check {
        display: flex;
        justify-content: space-between;
        align-items: center;
    }

    .form-control-check label {
        flex: 1;
    }

    .form-control-check input {
        flex: 2;
        height: 20px;
    }
</style>