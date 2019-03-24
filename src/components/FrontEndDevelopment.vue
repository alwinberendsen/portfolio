<template>
    <div class="part_frontend">
        <div class="text_content">
            <h1>Front-End Development</h1>
        </div>
    </div>
</template>

<script>
    export default {
        name: "FrontEndDevelopment"
    }
</script>

<style scoped lang="scss">
    .part_frontend{
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