<template>
    <div v-if="playerName" class="cell-box col-md-3">
        <div class="cell col-md-12 first">
            <div class="video">{{ this.playerName }}</div>
        </div>
    </div>
</template>
<script>
import "./uservideo.css";
export default {
    name: "UserVideo",
    props: {
        playerName: String,
    },
    data() {
        return {};
    },
};
</script>
