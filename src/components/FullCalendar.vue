<template>
    <div class="full-calendar">
        <!-- Simple Calendar Display -->
        <div class="calendar-header">
            <button @click="prevMonth">Prev</button>
            <span>{{ monthNames[month] }} {{ year }}</span>
            <button @click="nextMonth">Next</button>
        </div>
        <div class="calendar-grid">
            <div v-for="day in daysInMonth" :key="day" class="calendar-day">
                <span>{{ day }}</span>
                <div class="tasks">
                    <div v-for="task in getTasksForDay(day)" :key="task.id" class="task">
                        {{ task.title }}
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'FullCalendar',
    props: {
        tasks: Array
    },
    data() {
        return {
            month: new Date().getMonth(),
            year: new Date().getFullYear(),
            monthNames: ["January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"]
        };
    },
    computed: {
        daysInMonth() {
            return new Date(this.year, this.month + 1, 0).getDate();
        }
    },
    methods: {
        prevMonth() {
            if (this.month === 0) {
                this.month = 11;
                this.year--;
            } else {
                this.month--;
            }
        },
        nextMonth() {
            if (this.month === 11) {
                this.month = 0;
                this.year++;
            } else {
                this.month++;
            }
        },
        getTasksForDay(day) {
            return this.tasks.filter(task => {
                const taskDate = new Date(task.due_date);
                return taskDate.getDate() === day && taskDate.getMonth() === this.month && taskDate.getFullYear() === this.year;
            });
        }
    }
};
</script>

<style scoped>
.full-calendar {
    width: 100%;
    max-width: 800px;
    display: flex;
    flex-direction: column;
    align-items: center;
}
.calendar-header {
    display: flex;
    justify-content: space-between;
    width: 100%;
    padding: 10px;
    background-color: #f4f4f4;
    margin-bottom: 10px;
}
.calendar-grid {
    display: grid;
    grid-template-columns: repeat(7, 1fr);
    gap: 5px;
}
.calendar-day {
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 10px;
    border: 1px solid #ddd;
}
.tasks {
    margin-top: 5px;
    width: 100%;
}
.task {
    background-color: #eee;
    padding: 5px;
    margin: 2px 0;
    border-radius: 4px;
    font-size: 12px;
}
</style>
