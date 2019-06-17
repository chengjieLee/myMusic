<template>
    <div class="MusicList-warp">
        <my-scroll ref="myScroll" :data="songsListData" class="myScroll"  v-show="songsListData.length">
            <div class="scroll-content">
                <div class="content">
                    <div class="title">{{MusicListTitle}}</div>
                    <div class="item" v-for="(item,index) in songsListData" :key="index" @click="onClick(item.id,item.type,index)">
                        <div v-if="item.imageUrl" class="cover-img">
                            <img v-lazy="`${item.imageUrl}?param=60y60`" :key="item.imageUrl" alt="" class="item-img">
                        </div>
                        <div class="info">
                            <div class="song-info">
                                <div class="song-name">{{item.name}}</div>
                                <div v-if="item.album" class="singer-list">{{item.album}}</div>
                            </div>
                            <div class="play">
                                <img src="@/assets/listPlayIcon.png" alt="" class="play-img">
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </my-scroll>
        <loading :opacity="opacity" v-show="loadingStatus"></loading>
    </div>
</template>

<script>
import myScroll from 'base/myScroll'
import loading from "base/loading"


export default {
    name:'MusicList',
    components:{
        myScroll,
        loading
    },
    data(){
        return {
            opacity:0,
        }
    },
    props:{
        songsListData:{
            type:Array
        },
        MusicListTitle:{
            type:String,
            default:''
        },
        loadingStatus:Boolean
    },
    methods:{
        onClick(id,type,index){
            this.$emit('selectTarget',{id,type,index})
        },
        scrollTo(){
            // this.$refs.myScroll.scrollTo(...arguments)   //都行
            this.$refs.myScroll.scrollTo.call(null,...arguments)   //都行
            
        }
    }
}
</script>

<style lang="stylus" scoped>
@import "~common/styles/variable"
    .MusicList-warp
        width 100%
        .myScroll
            width 100%
            height 100%
            overflow hidden
            background white
            .scroll-content
                width 100%
                min-height 100%
                padding 0.25rem 0 0 0
                background white
                .content
                    width 100%
                    .title
                        font-weight 600
                        margin 0.4rem .8rem .5rem .8rem
                        font-size .9rem
                    .item
                        width 100%
                        height 2.5rem
                        display flex
                        align-items center
                        margin-top .5rem
                        background white
                        box-sizing border-box
                        justify-content space-between
                        border-bottom 0.05rem solid #eee
                        .cover-img
                            flex-shrink 0
                            .item-img
                                margin-left .5rem
                                width 2.5rem
                                height 2.5rem
                        .info
                            display flex
                            box-sizing border-box
                            height 100%
                            width 100%
                            flex-grow 1
                            overflow hidden
                            .song-info
                                width 90%
                                box-sizing border-box
                                display flex
                                flex-direction column
                                // flex-basis 50%
                                // flex-grow 1
                                justify-content center
                                overflow hidden
                                .song-name 
                                .singer-list
                                    padding 0 .5rem
                                    font-size 0.75rem
                                    width 90%
                                    overflow hidden
                                    white-space nowrap
                                    text-overflow ellipsis
                                .singer-list
                                    margin-top 0.3rem
                                    font-size .6rem
                                    color $fontGray
                            .play
                                flex-shrink 0
                                width 10%
                                display flex
                                align-items center
                                .play-img
                                    width 1rem

            
</style>
