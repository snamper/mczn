<template>
    <div class="header_wrapper" :style='bgColor'>
        <div class="back" @click='back'>
            <slot name='back'></slot>
            <span class="text" v-text='text'></span>
        </div>
        <div class="title" v-text='title'></div>
        <div class="right">
            <slot name='right'></slot>
        </div>
    </div>
</template>
<script>
    export default {
        name: 'v-header',
        props: {
            text: {
                type: String,
                default: ''
            },
            title: {
                type: String,
                default: ''
            },
            bg: {
                type: String,
                default: ''
            }
        },
        computed: {
            bgColor () {
                switch (this.bg) {
                case 'agent':
                    return `background: linear-gradient(#55c2fa, #4e93ff)`
                default:
                    return `background: linear-gradient(#40e399, #26bfb7)`
                }
            }
        },
        methods: {
            back () {
                // 基础组件 不应该有耦合度，它不应该关心业务逻辑，只派发事件
                this.$emit('back')
            }
        }
    }
</script>
<style lang="scss" scoped>
    @import '~styles/variables.scss';
    .header_wrapper{
        position: relative;
        display: flex;
        align-items: center;
        justify-content: space-between;
        padding: 0 10px;
        width: 100%;
        height: 2.2rem;
        line-height: 2.2rem;
        // background: $color-background-line;
        .back{
            display: flex;
            align-items: center;
            font-size: 0;
            .iconfont {
                font-size: .8rem;
                color: $color-text;
            }
            .text{
                font-size: .8rem;
                color: $color-text;
            }
        }
        .title{
            position: absolute;
            top:50%;
            left: 50%;
            transform: translate(-50%,-50%);
            color:$color-text;
            font-size: .9rem;
        }
        .right{
            font-size: .8rem;
            i{
                color: $color-text;
                font-size: 1rem;
            }
        }
    }
</style>
