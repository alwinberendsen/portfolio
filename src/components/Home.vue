<template>
    <div class="part_home">
        <div class="text_content">
            <h1>Alwin Berendsen</h1>
            <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</p>
        </div>
    </div>
</template>

<script>
    export default {
        name: "Home",
    }
</script>

<style scoped lang="scss">
    // Styling elements
    .part_home{
        background: #E3E3E3;
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
            height: 55vh;
            width: 100%;
            margin: 0px 10%;
        }
    }
</style>