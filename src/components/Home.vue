<template>
    <div class="part_home">
        <div class="text_content">
            <h1>Alwin Berendsen</h1>
        </div>
    </div>
</template>

<script>
    export default {
        name: "Home",
    }
</script>

<style scoped lang="scss">
    // General styling Home
    h1{
        font-family: Arial;
    }

    // Styling elements
    .part_home{
        background-image: url("../assets/header-bg.jpg");
        -webkit-background-size: cover;
        background-size: cover;
        background-position: center;
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