<template>
    <div class="icons">
        <!-- 为了让多出来的可以轮播滑动 -->
        <swiper :options="swiperOption">
            <swiper-slide v-for="(page,index) of pages" :key="index"><!-- 第一个v-for循环几页 -->
                <div class="icon" v-for="item of page" :key="item.id">
                    <div class="icon-img">
                        <img class="icon-img-content" :src="item.imgUrl" alt="景点门票">
                    </div>
                    <p class="icon-desc">{{ item.desc }}</p>
                </div>
            </swiper-slide>
        </swiper>
    </div>
</template>

<script>
export default {
    name: 'HomeIcons',
    props: {
        list: Array
    },
    data() {
        return {
            swiperOption: {
                autoplay: false
            }
        }
    },
    computed: {//实现两页显示
        pages () {
            const pages = []
            this.list.forEach((item,index) => {//对iconList做一个循环项
                const page = Math.floor(index / 8) //该item显示在第几页,利用Math.floor向下取整
                if(!pages[page]) { //如果pages中的page项不存在
                    pages[page] = []
                }
                pages[page].push(item)
            })
            return pages
        }   
    }
}
</script>

<style lang="stylus" scoped>
    @import '~@/assets/styles/varibles.styl'
    @import '~@/assets/styles/mixins.styl'
    .icons >>> .swiper-container
        height: 0
        padding-bottom: 50%
    .icons
        margin-top .15rem
        .icon
            position relative
            overflow hidden
            float: left
            width 25%
            height 0
            padding-bottom 25%
            .icon-img
                position absolute
                top 0
                right 0
                left 0
                bottom .40rem
                box-sizing border-box
                // padding .1rem
                .icon-img-content
                    display block
                    margin: 0 auto 
                    height 100%
            .icon-desc
                position absolute
                left 0
                right 0
                bottom 0
                height .40rem
                line-height .40rem
                text-align center
                color: $darkTextColor
                ellipsis() //这是原先包装好的函数,用来当字数多时省略显示
</style>