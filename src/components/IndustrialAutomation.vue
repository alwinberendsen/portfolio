<template>
    <div class="part_IA">
        <div class="text_content">
            <h1>Industrial Automation</h1>
        </div>
    </div>
</template>

<script>
    export default {
        name: "IndustrialAutomation"
    }
</script>

<style scoped lang="scss">
    .part_IA{
        background: aqua;
        min-height: 100vh;
        min-width: 100%;
        // Center elements
        display: flex;
        flex-flow: row;
        align-items: center;
        vertical-align: center;

        // Text content
        .text_content{
            max-width: 400px;
            width: 100%;
            margin: 0px 10%;
        }
    }
</style>