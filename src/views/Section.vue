<template>
    <div class="section container-fluid">
        <!--정보박스-->
        <div id="info-box"></div>

        <div class="card-box-parent">
            <!--첫번째 줄-->
            <div class="card-box row first-row-box gx-5 d-flex" :class="getJustifyClassFirstRow">
                <user-video :playerName="subscribeName2" id="video-2"></user-video>
                <user-video :playerName="subscribeName3" id="video-3"></user-video>
                <user-video :playerName="subscribeName6" id="video-6"></user-video>
                <user-video :playerName="subscribeName7" id="video-7"></user-video>
            </div>

            <!-- 두번째 줄 -->
            <div class="card-box row second-row-box gx-5">
                <user-video :playerName="subscribeName8" id="video-8"></user-video>
                <user-video
                    :playerName="subscribeName9"
                    id="video-9"
                    class="offset-md-6"
                ></user-video>
            </div>

            <!-- 세번째 줄 -->
            <div class="card-box row third-row-box gx-5 d-flex" :class="getJustifyClassThirdRow">
                <user-video :playerName="subscribeName4" id="video-4"></user-video>
                <user-video :playerName="this.publisher" id="video-mine"></user-video>
                <user-video :playerName="subscribeName5" id="video-5"></user-video>
                <user-video :playerName="subscribeName10" id="video-10"></user-video>
            </div>
        </div>
    </div>
    <button @click="enterRoom">+</button>
    <button @click="leaveRoom">-</button>
</template>
<script>
import "@/views/section.css";
import UserVideo from "@/views/UserVideo";
// import { onMounted, reactive } from "vue";

export default {
    name: "Section",
    components: {
        UserVideo,
    },
    data() {
        return {
            subscribers: ["이현정", "유태규", "김용훈", "김지훈"],
            publisher: "String",
            playerNum: 1,
            subscribeName2: "",
            subscribeName3: "",
            subscribeName4: "",
            subscribeName5: "",
            subscribeName6: "",
            subscribeName7: "",
            subscribeName8: "",
            subscribeName9: "",
            subscribeName10: "",
        };
    },
    computed: {
        getJustifyClassFirstRow: function () {
            if (this.playerNum == 2) {
                console.log("justift center", this.playerNum);
                return "justify-content-center";
            } else {
                console.log("justift between", this.playerNum);
                return "justify-content-between";
            }
        },
        getJustifyClassThirdRow: function () {
            if (this.playerNum <= 3) {
                console.log("justift center", this.playerNum);
                return "justify-content-center";
            } else {
                console.log("justift between", this.playerNum);
                return "justify-content-between";
            }
        },
    },
    mounted() {
        console.log("mounted");
        this.publisher = "최은송";

        let i;
        for (i = 0; i < this.subscribers.length; i++) {
            this.playerNum += 1;
            console.log(i + 2);

            this.passProps(i, true);
        }
    },
    methods: {
        leaveRoom() {
            if (this.playerNum == 1) return;

            let removeIdx = Math.floor(Math.random() * this.subscribers.length);
            console.log("removeIdx", removeIdx);
            if (removeIdx > -1) {
                this.subscribers.splice(removeIdx, 1);
                this.passProps(removeIdx, false);

                let idx = removeIdx;
                for (; idx < this.subscribers.length; idx++) {
                    this.passProps(idx + 1, false);
                    this.passProps(idx, true);
                }
            }

            this.playerNum -= 1;
        },
        enterRoom() {
            this.subscribers.push("최최최");
            let idx = this.subscribers.length - 1;
            this.passProps(idx, true);

            this.playerNum += 1;
        },
        passProps(i, flag) {
            console.log(this.subscribers);
            switch (i + 2) {
                case 2:
                    this.subscribeName2 = flag ? this.subscribers[i] : "";
                    // console.log(2);
                    break;
                case 3:
                    this.subscribeName3 = flag ? this.subscribers[i] : "";
                    // console.log(3);
                    break;
                case 4:
                    this.subscribeName4 = flag ? this.subscribers[i] : "";
                    // console.log(4);
                    break;
                case 5:
                    this.subscribeName5 = flag ? this.subscribers[i] : "";
                    // console.log(5);
                    break;
                case 6:
                    this.subscribeName6 = flag ? this.subscribers[i] : "";
                    // console.log(6);
                    break;
                case 7:
                    this.subscribeName7 = flag ? this.subscribers[i] : "";
                    // console.log(7);
                    break;
                case 8:
                    this.subscribeName8 = flag ? this.subscribers[i] : "";
                    // console.log(8);
                    break;
                case 9:
                    this.subscribeName9 = flag ? this.subscribers[i] : "";
                    // console.log(9);
                    break;
                case 10:
                    this.subscribeName10 = flag ? this.subscribers[i] : "";
                    // console.log(10);
                    break;
            }
        },
    },
};
</script>
