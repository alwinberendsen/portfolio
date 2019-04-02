<template>
    <div class="editor">
        <div class="topbar">
            <a v-on:click="closeEditor()">
                <span class="dots" ></span>
            </a>
            <span class="dots"></span>
            <span class="dots"></span>
        </div>
        <div class="code_content">
            <!--<div class="type_code" id="code"></div>-->
            <vue-typed-js :strings="code" :typeSpeed="10" :showCursor="false" ref="type_component">
                <div class="typing" id="typing_element"></div>
            </vue-typed-js>
        </div>
    </div>
</template>

<script>
    import VueTypedJs from 'vue-typed-js/src/components/VueTypedJs.vue'

    export default {
        name: "Editor",
        props: {
          code : Array,
        },
        components: {
            VueTypedJs,
        },
        methods: {
          closeEditor: function () {
              document.getElementById('codeEditor').classList.remove('open-Editor');
          }
        },
        watch: {
            code: function () {
                this.$refs.type_component.typedObj.destroy();
            }
        },
        mounted() {
            this.$refs.type_component.initTypedJS();
        }
    }
</script>

<style scoped lang="scss">
    // General styling Home

    // Styling elements
    .editor{
        background: #fff;
        max-width: 750px;
        width: 100%;
        min-height: 100%;
        -webkit-border-radius: 5px;
        -moz-border-radius: 5px;
        border-radius: 5px;
        margin: 0px;
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
            }
            a{
                .dots{
                    margin-left: 10px;
                    transition: all 0.2s;
                    &:hover{
                        background: red;
                        cursor: pointer;
                    }
                }
            }
        }
        .code_content{
            padding-top: 40px;
            padding-left: 20px;
            padding-right: 20px;
            font-size: 16px;
            color: #eaeaea;
            background-color: #474747;
            min-height: 100%;
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