<template>
    <div class="editor">
        <div class="topbar">
            <span class="dots"></span>
            <span class="dots"></span>
            <span class="dots"></span>
        </div>
        <div class="code_content">
            <div class="type_code" id="code"></div>
        </div>
    </div>
</template>

<script>
    import typed from 'typed.js';
    export default {
        name: "Editor",
        props: {
          code : String,
        },
        watch: {
            code: function (newCode) {
                document.getElementById('code').innerHTML = '';
                var Typed = new typed('.type_code', {
                    strings: [newCode],
                    typeSpeed: 10,
                    showCursor: false,
                    contentType: 'html'
                });
            }
        },
        mounted() {
            var Typed = new typed('.type_code', {
                strings: [this.code],
                typeSpeed: 10,
                showCursor: false,
                contentType: 'html'
            });

            Typed.reset();
        }
    }
</script>

<style scoped lang="scss">
    // General styling Home

    // Styling elements
    .editor{
        background: #fff;
        max-width: 600px;
        width: 100%;
        min-height: 400px;
        -webkit-border-radius: 5px;
        -moz-border-radius: 5px;
        border-radius: 5px;
        margin: 0px 5%;
        position: relative;
        -webkit-box-shadow: -5px 6px 30px 0px rgba(102,102,102,1);
        -moz-box-shadow: -5px 6px 30px 0px rgba(102,102,102,1);
        box-shadow: -5px 6px 30px 0px rgba(102,102,102,1);
        .topbar{
            background: black;
            height: 30px;
            position: absolute;
            width: 100%;
            -webkit-border-radius: 5px 5px 0px 0px;
            -moz-border-radius: 5px 5px 0px 0px;
            border-radius: 5px 5px 0px 0px;
            line-height: 30px;
            .dots{
                background: #fff;
                border-radius: 50px;
                width: 10px;
                height: 10px;
                display: inline-block;
                margin: 0px 3px;
                &:first-of-type{
                    margin-left: 10px;
                }
            }
        }
        .code_content{
            padding-top: 40px;
            padding-left: 20px;
            padding-right: 20px;
            font-size: 14px;
            color: #eaeaea;
            background-color: #474747;
            min-height: 370px;
            border-radius: 5px;
            font-family: Monaco;
            .type_code{
                span{
                    color: green;
                }
                .command{
                    color: green;
                }
            }

        }
    }
</style>