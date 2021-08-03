<template>
    <div v-if="playerName" class="cell-box col-md-3" @click="votePlayer">
        <div class="cell col-md-12" :style="'background-color: ' + this.playerName.color">
            <div class="video"></div>
            <span id="nickname" class="font-jua">
                {{ this.playerName.name }}
            </span>
            <div class="vote-box">
                <span v-for="voter in this.playerName.voters" :key="voter" class="voter-icon-span"
                    ><i class="fas fa-user-circle fa-2x" :style="'color:' + voter.color"></i
                ></span>
            </div>
        </div>
    </div>
</template>
<script>
import "./uservideo.css";
export default {
    name: "UserVideo",
    props: {
        playerName: Object,
    },
    data() {
        return {
            hello: "hello",
            isFirstVote: false,
        };
    },
    methods: {
        // 투표한 상대 플레이어의 playerId를 얻어오는 method
        votePlayer: function () {
            this.isFirstVote = !this.isFirstVote;
            this.$emit("setVoteData", {
                playerId: this.playerName.name,
                isFirstVote: this.isFirstVote,
            });
        },
    },
};
</script>
