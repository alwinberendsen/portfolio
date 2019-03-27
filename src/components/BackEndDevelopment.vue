<template>
    <div class="part_backend">
        <div class="text_content">
            <h1>Back-End Development</h1>
        </div>
    </div>
</template>

<script>
    export default {
        name: "BackEndDevelopment"
    }
</script>

<style scoped lang="scss">
    .part_backend{
        min-height: 100vh;
        min-width: 100%;
        background: #E3E3E3;
        // Center elements
        display: flex;
        flex-flow: row;
        align-items: center;
        vertical-align: center;

        // Text content
        .text_content{
            max-width: 400px;
            height: 55vh;
            width: 100%;
            margin: 0px 10%;
        }
    }
</style>