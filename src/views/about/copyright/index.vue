<template>
    <transition name='slide' mode='out-in'>
        <div class="statement-wrapper">
            <v-header title='版权声明' text='返回' @back='back'>
                <i class="iconfont icon-jiantouzuo" slot='back'></i>
            </v-header>
            <ul class="statement-list">
                <li class="copy-statement">版权声明</li>
                <li class="rule" v-for='(rule,index) in statement' :key='index'>
                    <i class="circle"></i>
                    <p class="desc" v-text='rule.descriable'></p>
                </li>
            </ul>
            <p class="copyright">芜湖摩灿智能有限公司运营</p>
        </div>
    </transition>
</template>
<script>
    import vHeader from 'components/header'
    export default {
        name: 'copyright',
        data () {
            return {
                statement: [
                    {
                        descriable: '是由独立开发并运营的智能充电系统。'
                    },
                    {
                        descriable: '对其发行的或合作公司共同发行的包括但不限于产品或服务的全部内容及网站上的材料拥有版权等知识产权，收法律保护。'
                    },
                    {
                        descriable: '未经本公司书面许可，任何单位及个人不得以任何方式或理由对上述产品、服务、信息、材料的任何部分进行使用、复制、修改、抄录、传播或与其他产品捆绑使用销售。'
                    },
                    {
                        descriable: '凡侵犯本公司版权等知识产权的，本公司必依法追究其法律责任。'
                    }
                ]
            }
        },
        components: {
            vHeader
        },
        methods: {
            back () {
                this.$router.go(-1)
            }
        }
    }
</script>
<style lang="scss" scoped>
    @import '~styles/variables.scss';
    .statement{
        &-wrapper{
            @include fixed;
            .copyright{
                position: relative;
                margin-top:-2.2rem;
                // bottom: 3rem;
                height: 2.2rem;
                line-height: 2.2rem;
                width: 100%;
                text-align: center;
                color: #bbbbbb;
                font-size: .7rem;
            }
        }
        &-list{
            min-height: calc(100% - 2.2rem );
            padding-bottom: 2.2rem;
            .copy-statement{
                height: 2rem;
                line-height: 2rem;
                padding-left: 1rem;
                color:$color-text-d;
            }
            .rule{
                display: flex;
                align-items: flex-start;
                padding: .8rem;
                background-color: #fff;
                .circle{
                    display: inline-block;
                    flex:0 0 10PX;
                    width: 10PX;
                    height: 10PX;
                    margin-top: 5px;
                    border-radius: 50%;
                    background-color:$color-background;
                }
                .desc{
                    flex:1;
                    line-height: 25Px;
                    margin-left: .5rem;
                    font-size: .7rem;
                    color:$color-text-d;
                }
            }
        }
    }
</style>
