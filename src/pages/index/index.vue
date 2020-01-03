<template>
  <div> 
    <swiper
      :indicator-dots="indicatorDots"
      :autoplay="autoplay"
      :interval="interval"
      :duration="duration"
      style="height:200px"
    >
    <block v-for="item in imgUrls" :key="item">
      <swiper-item>
        <image :src="item" style="width:100%;"/>
      </swiper-item>
    </block>
   </swiper>
    <i-grid i-class="no-border">
    <i-grid-item @click="goType(grid)" v-for="grid in grids" :key="grid" i-class="no-border">
        <i-grid-icon>
            <image :src="grid.image" />
        </i-grid-icon>
        <i-grid-label>{{grid.title}}</i-grid-label>
    </i-grid-item>
  </i-grid>
  <i-panel :title="title_name">
    <view style="padding: 15px;">
      <i-card v-for="item in top" :key="item" i-class="split" :title="item.name" :thumb="item.image">
      <view slot="content">{{item.remark}}</view>
      <view slot="footer">{{item.address}}</view>
      </i-card>
    </view>
</i-panel>
  </div>
</template>

<script>
export default {
  data () {
    return {
      title_name:"热门",
      grids:[
        {title:"免费",image:"/static/images/1.png"},
        {title:"男频",image:"/static/images/2.png"},
        {title:"女频",image:"/static/images/3.png"}
      ],
      top:[
        {name:"星辰变",address:"我吃西红柿",image:"cloud://novel-vs4zy.6e6f-novel-vs4zy-1301052078/xingchengbian.jpg",remark:"玄幻"},
        {name:"我不喜欢这个世界，我只喜欢你",address:"乔一",image:"cloud://novel-vs4zy.6e6f-novel-vs4zy-1301052078/555.jfif",remark:"爱情"}
      
      
      ],
      imgUrls: [
        'cloud://novel-vs4zy.6e6f-novel-vs4zy-1301052078/f9ba39ced139b4df0e57c3cad4e54aad.jpg',
        'cloud://novel-vs4zy.6e6f-novel-vs4zy-1301052078/5d3b8cbd3b9216e67440a604ba1c80ae.jpg',
        'cloud://novel-vs4zy.6e6f-novel-vs4zy-1301052078/44d12ba15c29a04b83f36a50c15a1fa8.jpg'
      ],
      indicatorDots: true,
      autoplay: true,
      interval: 5000,
      duration: 1000,
    }
  },

  methods: {
    goType(type){
      console.log(type)
      let url = '../list/main?type=' + type.title
      mpvue.navigateTo({ url })
    }
  },

  created () {
  }
}
</script>

<style scoped>
div >>> .no-border {
  border-width: 0pt;
}
div >>> .split {
  margin-bottom: 10pt;
}
</style>
