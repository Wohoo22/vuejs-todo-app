<template>
    <div>
        <form @submit='addTodo'>
            <input type='text' v-model='title' name='title'>
            <button type='submit'>Add</button>
        </form>
    </div>
</template>

<script>
    function uuidv4() {
        return 'xxxxxxxx-xxxx-4xxx-yxxx-xxxxxxxxxxxx'.replace(/[xy]/g, function(c) {
            var r = Math.random() * 16 | 0, v = c == 'x' ? r : (r & 0x3 | 0x8);
            return v.toString(16);
        });
    }

    export default {
        name: 'AddTodo',
        data() {
            return {
                title: ''
            }
        },
        methods: {
            addTodo(e) {
                e.preventDefault();

                const newTodoObj = {
                    id: uuidv4(),
                    title: this.title,
                    completed: false
                }

                this.$emit('add-todo', newTodoObj);
                this.title = '';
            }
        },
    }
</script>

<style scoped>
</style>