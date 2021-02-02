<template>
    <form @submit.prevent="onSubmit">
        <input type="text" v-model="title">
        <button type="submit">Create</button>
    </form>
</template>

<script>
    export default {
        data() {
            return {
                title: ''
            }
        },
        methods: {
            onSubmit () {
                //проверяем, что в переданном значении есть что-то
                if (this.title.trim()) {
                    //создаем новый объект
                    const newTodo = {
                        id: Date.now(),
                        title: this.title,
                        completed: false
                    }

                    //генерируем событие
                    this.$emit('add-todo', newTodo)

                    //чистим поле ввода
                    this.title=''
                }
            }
        }
    }
</script>

<style>
    form {
        display: flex;
    }

    input {
        width: 400px;
    }
</style>
