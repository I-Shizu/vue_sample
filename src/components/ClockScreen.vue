<template>
    <div class="container">
        <div class="clock">
            <div class="date">
                <p>{{ year }}/{{ month }}/{{ day }}</p>
            </div>
            <div class="time">
                <p>{{ hours }}:{{ mitites }}:{{ seconds }}</p>
            </div>
            <div class="button" v-on:click="showMessage()">
                <p>十秒後にアラームを設定</p>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'ClockScreen',
    data() {
        return {
            date: new Date(),
        };
    },
    computed: {
        //年
        year() {
            return this.date.getFullYear();
        },
        //月
        month() {
            return this.dateTimePadding(this.date.getMonth() + 1);
        },
        //日
        day() {
            return this.dateTimePadding(this.date.getDate());
        },
        //時
        hours() {
            return this.dateTimePadding(this.date.getHours());
        },
        //分
        mitites() {
            return this.dateTimePadding(this.date.getMinutes());
        },
        //秒
        seconds() {
            return this.dateTimePadding(this.date.getSeconds());
        },
    },
    methods: {
        setDate() {
            this.date = new Date();
        },

        dateTimePadding(num) {
            return ('0' + num).slice(-2);
        },

        showMessage() {
            setTimeout(() => {
                alert('アラーム');
            }, 10000);
        },
    },
    mounted() {
        this.setDate();

        setInterval(() => {
            this.setDate();
        }, 1000);
    },
};
</script>

<style scoped>
.container {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    background-color: black;
}
.date {
    font-size: 24px;
    color: coral;
}
.time {
    font-size: 48px;
    color: coral;
}
.button {
    border: 1px solid white;
    text-align: center;
    padding: 10px;
    color: white;
    cursor: pointer;
}
</style>