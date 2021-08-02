<template>
    <div class="app">
        <nav-header></nav-header>
        <div class="progress">
            <div
                class="progress-bar"
                role="progressbar"
                style="width: 50%"
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
};
</script>
<style>
.app {
    height: 100%;
}
</style>
