<template>
    <div class="home-page">
        <TaskForm @taskAdded="fetchTasks"/>
        <TaskList :tasks="tasks" @taskUpdated="fetchTasks" @taskDeleted="fetchTasks"/>
    </div>
</template>

<script>
import axios from 'axios';
import TaskForm from '@/components/TaskForm.vue';
import TaskList from '@/components/TaskList.vue';

export default {
    name: 'HomePage',
    components: { TaskForm, TaskList },
    data() {
        return {
            tasks: []
        };
    },
    methods: {
        fetchTasks() {
            axios.get('http://localhost:3000/api/tasks')
                .then(response => {
                    this.tasks = response.data;
                })
                .catch(error => {
                    console.error('Error fetching tasks:', error);
                });
        }
    },
    mounted() {
        this.fetchTasks();
    }
};
</script>

<style scoped>
.home-page {
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 20px;
}
</style>
