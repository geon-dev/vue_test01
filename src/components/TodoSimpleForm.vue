<template>
    <form @submit.prevent="onSubmit">
        <div class="d-flex">
            <div class="flex-grow-1 mr-2">
                <input class="form-control" type="text" v-model="todo" placeholder="Type new to-do">
            </div>
            <div>
                <button class="btn btn-primary" tyep="submit">Add</button>
            </div>
        </div>
        <div v-show="toggle" style="color:red">빈값</div>
    </form>
</template>

<script setup>
import { ref } from 'vue';

const todo = ref('');
const toggle = ref(false);
const emit = defineEmits(['add-todo']);

const onSubmit = () => {
    if (todo.value === '') {
        toggle.value = true;
    } else {
        emit('add-todo', {
            id: Date.now(),
            subject: todo.value,
            completed: false,
        });

        todo.value = '';
        toggle.value = false;
    }
};

</script>

<style lang="scss" scoped></style>