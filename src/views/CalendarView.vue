<template>
    <div class="calendar-view">
        <Calendar :tasks="tasks"/>
    </div>
</template>

<script>
import axios from 'axios';
import Calendar from '@/components/FullCalendar.vue';

export default {
    name: 'CalendarView',
    components: { Calendar },
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
.calendar-view {
    display: flex;
    justify-content: center;
    padding: 20px;
}
</style>
