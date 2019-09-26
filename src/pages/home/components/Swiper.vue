<template>
    <div class="wrapper">
        <swiper :options="swiperOption" v-if="showSwiper">
            <!-- ref="mySwiper" @someSwiperEvent="callback"现在用不上 -->
            <swiper-slide v-for="item of list" :key="item.id"><!-- v-for 后面必须要有 :key -->
                <img class="swiper-img" :src="item.imgUrl" alt="去哪儿门票" style="opacity: 1;">
                <!-- 自: 要用vue的东西,动态改变,属性就要加v-bind -->
            </swiper-slide>
            <div class="swiper-pagination" slot="pagination"></div>
            <!-- <div class="swiper-button-prev" slot="button-prev"></div>
            <div class="swiper-button-next" slot="button-next"></div> 左右箭头-->
            <!-- <div class="swiper-scrollbar" slot="scrollbar"></div> 滚动条-->
        </swiper>
    </div>
</template>

<script>
export default {
    name: 'HomeSwiper',
    props: {
        list: Array //类型为数组
    },
    data() {
        return {
            swiperOption: {
                pagination: {//这里没法直接用pagination: '.swiper-pagination' ,不知道为什么? ? ?
                    el: '.swiper-pagination' 
                },
                loop: true,  //让轮播支持循环轮播
                autoplay: true
            }
        }
    },
    computed: {
        showSwiper () {
            return this.list.length
        }
    },
}
</script>

<style lang="stylus" scoped>
    .wrapper >>> .swiper-pagination-bullet-active
        background: #fff
        // 为什么要这样写呢,因为.swiper-pagination-bullet-active本来是没有在我们这个.wrapper组件里的
    .wrapper
        overflow: hidden
        width: 100%
        height: 0
        padding-bottom: 31.25%
        // padding-top/bottom的百分比值，是依赖父容器宽度的
        //为什么不直接设置height,因为width和height的百分百比相对的不一样,也可以写height: 31.25vw,但是又兼容性问题
        background: #eee
        .swiper-img
            width: 100%
</style>