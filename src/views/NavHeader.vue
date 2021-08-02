<template>
    <nav class="navbar navbar-expand-sm navbar-light bg-light">
        <div>
            <img src="@/assets/sun.png" id="sun-logo" />
            <span id="sun-logo-title font-Jua">READY</span>
        </div>
        <div style="margin-left: 70px">
            <img
                src="https://w7.pngwing.com/pngs/969/744/png-transparent-mafia-block-game-android-computer-icons-mafia-game-emblem-logo.png"
                alt=""
                style="width: 50px; margin-right: 2% display: inline-block"
            />
            <span id="alive-mafia-num">2</span>
        </div>

        <button type="button" class="btn" id="start-button">게임 시작</button>

        <span id="timer" class="margin-top: 10px;">100</span>
        <i class="fad fa-info-circle fa-2x" id="rule-book"></i>
    </nav>
</template>

<script>
import "./navheader.css";
export default {
    name: "NavHeader",
};
</script>
