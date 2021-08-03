<template>
    <div class="app">
        <nav-header @setTime="setLeftTime"></nav-header>
        <div class="progress">
            <div
                class="progress-bar"
                role="progressbar"
                :style="'width: ' + getLeftTime + '%'"
                aria-valuenow="100"
                aria-valuemin="0"
                aria-valuemax="100"
            ></div>
        </div>

        <Section></Section>
    </div>
</template>

<script>
import "./assets/common.css";
import NavHeader from "./views/NavHeader";
import Section from "./views/Section";
export default {
    name: "App",
    components: {
        NavHeader,
        Section,
    },
    data() {
        return {
            time: 0,
            maxTime: 100,
            value: 0,
            leftTime: this.maxTime,
        };
    },
    methods: {
        setLeftTime(value) {
            this.leftTime = value;
            this.time = this.maxTime - this.leftTime;
        },
    },
    computed: {
        getLeftTime() {
            console.log("leftTime", this.leftTime);
            console.log(this.value * this.leftTime);
            return this.value * this.leftTime;
        },
    },
    created() {
        this.value = 100 / this.maxTime;
        console.log(this.value);
    },
};
</script>
<style>
.app {
    height: 100vh;
}

.progress {
    height: 20px;
    background: #484949;
    position: relative;
    margin: auto;
}

.progress-bar {
    background-image: linear-gradient(to right, #152fc0, #9c16a8);
}
</style>
