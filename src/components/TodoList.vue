<template>
    <div class="card mt-2" v-for="(item, index) in items" :key="item.id">
        <div class="card-body p-2 d-flex align-items-center">
            <div class="form-check flex-grow-1">
                <input class="form-check-input" type="checkbox" @change="toggleTodo(index)">
                <label :style="item.completed ? todoStyle : {}" class="form-check-label">
                    {{ item.subject }}
                </label>
            </div>
            <div>
                <button class="btn btn-danger btn-sm" @click="deleteTodo(index)">delete</button>
            </div>
            <div>
                <button class="btn btn-warning btn-lg" v-on:click="checkTest(testData)">test01</button>
            </div>
        </div>
    </div>
</template>

<script setup>

const testData = '테스트데이타';

const props = defineProps(['items']);

const emit = defineEmits([
    'toggleTodo',
    'delete-toto',
    'check-data',
]);

const toggleTodo = (index) => {
    emit('toggleTodo', index);
};

const deleteTodo = (index) => {
    emit('delete-toto', index);
};

const checkTest = (data) => {
    emit('check-data', data);
};

</script>

<style lang="scss" scoped></style>