<template>
    <nav class="navbar navbar-expand-sm navbar-light bg-light">
        <div>
            <img src="@/assets/sun.png" id="sun-logo" />
            <span id="sun-logo-title" class="font-jua">READY</span>
        </div>
        <div style="margin-left: 70px">
            <img
                src="https://www.clipartmax.com/png/full/110-1108103_home-expansion-syndicate-mafia-logo.png"
                alt=""
                style="width: 50px; margin-right: 2% display: inline-block"
            />
            <span id="alive-mafia-num" class="font-jua">2</span>
        </div>

        <!-- playerNum가 4 이상 됐을 때 활성화 되기 -->
        <button @click="startCountDown" type="button" class="font-jua" id="start-button">
            게임 시작
        </button>

        <span id="timer" class="font-jua">{{ this.time }}</span>
        <!-- <span id="timer" class="font-jua">300</span> -->
        <i @click="openRuleBook" class="fas fa-info-circle fa-2x" id="rule-book"></i>
    </nav>
</template>

<script>
import "./navheader.css";
export default {
    name: "NavHeader",
    data() {
        return {
            maxTime: 100,
            time: this.maxTime,
            leftTime: 0,
        };
    },
    methods: {
        openRuleBook() {},
        startCountDown() {
            this.time = this.maxTime;
            this.leftTime = 0;
            this.$emit("setTime", this.leftTime);
            setTimeout(() => {
                this.countDownTimer();
            }, 200);
        },
        countDownTimer() {
            var interval = setInterval(() => {
                this.time -= 1;
                this.leftTime = this.maxTime - this.time;
                this.$emit("setTime", this.leftTime);
            }, 1000);

            setTimeout(() => {
                clearInterval(interval);
            }, 1000 * this.maxTime);
        },
    },
};
</script>
