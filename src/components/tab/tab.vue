<template>
    <div class="tabWrap">
        <ul class="title">
            <router-link tag="li" to="/recommend">
                <span class="tab-items">个性推荐</span>
            </router-link>
            <router-link tag="li" to="/songs">
                <span class="tab-items">歌 单</span>
            </router-link>
            <router-link tag="li" to="/rank">
                <span class="tab-items">排行榜</span>
            </router-link>
            <router-link tag="li" to="/singer">
                <span class="tab-items">歌 手</span>
            </router-link>
        </ul>
    </div>

</template>

<script>
export default {
    name:"Tab"
}
</script>

<style lang="stylus" scoped>
@import "~common/styles/variable"
    .title
        box-sizing border-box
        width 100%
        height 2.2rem
        background $themeColor
        display flex
        align-items center
        list-style none
        justify-content space-around
        padding .2rem .4rem
        .tab-items
            color white
            display inline-block
            text-align center
            font-size .8rem
            height 1.3rem
            line-height 1.25rem
            padding 0 .7rem
    &.router-link-active
        .tab-items 
            border-radius .8rem
            background white
            color $themeColor

            
</style>
