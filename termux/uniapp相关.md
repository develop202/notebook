# 1. 原生下拉刷新、上拉触底

```javascript
// 下拉刷新
  onPullDownRefresh() {
    // this.list = []
    //调用获取数据方法
    // this.getData()
    setTimeout(() => {
      uni.reLaunch({
        url: '/pages/index/index'
      })
      //结束下拉刷新
      uni.stopPullDownRefresh()
    }, 500);
  },
  // 上拉加载更多
  onReachBottom() {
    setTimeout(() => {
      for (let i = 0; i < 6; i++) {
        this.videos.push({
          img: "../../static/sources/画江湖之不良人第六季.jpeg",
          poster: "../../static/sources/画江湖之不良人第六季.jpeg",
          name: "画江湖之不良人第六季",
          category_performer: [
            "武侠江湖",
            "原创动画",
            "江湖恩怨",
          ],
          binge_sum: 2305497,
          description: "12-雪儿揭下大帅面具，将臣拿出改良版九幽玄天神功",
          degree_of_heat: 21346,
          score: 9.5
        })
      }
    }, 200)
  },
```
