<template>
<div class="index-wrap">
  <div class="index-left">
    <div class="index-left-block">
      <h2>全部作业</h2>

      <template v-for="hwtype in hwList">
      <h3>{{ hwtype.title}}</h3>
        <ul>
          <li v-for="item in hwtype.list">
            <a :href="item.url">{{ item.name }}</a>
            <span v-if="item.hot" class="hot-tag">HOT</span>
          </li>
        </ul>
        <div v-if="!hwtype.last" class="hr"></div>
      </template>
    </div>
    <div class="index-left-block lastest-news">
      <h2>最新消息</h2>
      <ul>
        <li v-for="item in newsList">
          <a :href="item.url" class="new-item">{{ item.title }}</a>
        </li>
      </ul>
    </div>
  </div>
  <div class="index-right">
    <slide-show :slides="slides" :inv="invTime"></slide-show>
    <div class="index-board-list">
      <div
      class="index-board-item"
      v-for="(item, index) in boardList"
      :class="[{'line-last' : index % 2 !== 0}, 'index-board-' + item.id]">
        <div class="index-board-item-inner" >
          <h2>{{ item.title }}</h2>

          <p>{{ item.description }}</p>
          <div class="index-board-button">
            <router-link class="button" :to="{path: 'detail/' + item.toKey}">立即划水</router-link>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>
</template>

<script>
import slideShow from '../components/slideShow'
export default {
components: {
    slideShow
  },
  data(){
  return{
      invTime: 2000,
      slides: [
        {
          src: require('../assets/slideShow/pic1.jpg'),
          title: 'xxx1',
          href: 'detail/1'
        },
        {
          src: require('../assets/slideShow/pic2.jpg'),
          title: 'xxx2',
          href: 'detail/2'
        },
        {
          src: require('../assets/slideShow/pic3.jpg'),
          title: 'xxx3',
          href: 'detail/3'
        },
        {
          src: require('../assets/slideShow/pic4.jpg'),
          title: 'xxx4',
          href: 'detail/4'
        }
      ],
      boardList: [
        {
          title: '百度题库',
          description: '拯救没时间备考的你',
          id: '0',
          toKey: 'baidutiku',
          saleout: false
        },
        {
          title: '作业帮',
          description: '让学习更简单',
          id: '1',
          toKey: 'zuoyebang',
          saleout: false
        },
        {
          title: '学霸君',
          description: '让作业变得更简单',
          id: '2',
          toKey: 'xuebajun',
          saleout: true
        },
        {
          title: '猿题库',
          description: '从此爱上学习',
          id: '3',
          toKey: 'yuantiku',
          saleout: false
        }
      ],
      newsList: {
        rendie:{
          title:'ddl is coming',
          url:'https://github.com/sheep1998/js'


        }
      },
      hwList: {
        ics: {
          title: 'ics-homework',
          list: [
            {
              name: 'homework',
              url: 'http://ipads.se.sjtu.edu.cn/courses/ics/'
            },
            {
              name: 'labs',
              url: 'http://ipads.se.sjtu.edu.cn/courses/ics/schedule.shtml',
              hot:true
            }
          ]
        },
        algorithm: {
          title: 'algorithm',
          last: true,
          list: [
            {
              name: 'Ualgo17/',
              url: 'https://basics.sjtu.edu.cn/~liguoqiang/teaching/Ualgo17/',
              hot: true
            },
            {
              name: 'Galgo17/',
              url:'https://basics.sjtu.edu.cn/~liguoqiang/teaching/Galgo17/'
            },
            {
              name: 'algo/',
              url:'https://basics.sjtu.edu.cn/~liguoqiang/teaching/algo/'
            },
            {
              name:'comp/',
              url:'https://basics.sjtu.edu.cn/~liguoqiang/teaching/comp/'
            }

          ]
        }
      }
    }
  }

}
</script>

<style scoped>
.index-wrap {
  width: 1200px;
  margin: 0 auto;
  overflow: hidden;
}
.index-left {
  float: left;
  width: 300px;
  text-align: left;
}
.index-right {
  float: left;
  width: 900px;
}
.index-left-block {
  margin: 15px;
  background: #fff;
  box-shadow: 0 0 1px #ddd;
}
.index-left-block .hr {
  margin-bottom: 20px;
}
.index-left-block h2 {
  background: #4fc08d;
  color: #fff;
  padding: 10px 15px;
  margin-bottom: 20px;
}
.index-left-block h3 {
  padding: 0 15px 5px 15px;
  font-weight: bold;
  color: #222;
}
.index-left-block ul {
  padding: 10px 15px;
}
.index-left-block li {
  padding: 5px;
}
.index-board-list {
  overflow: hidden;
}
.index-board-item {
  float: left;
  width: 400px;
  background: #fff;
  box-shadow: 0 0 1px #ddd;
  padding: 20px;
  margin-right: 20px;
  margin-bottom: 20px;
}
.index-board-item-inner {
  min-height: 125px;
  padding-left: 120px;
}
.index-board-0 .index-board-item-inner{
  background: url(../assets/images/1.png) no-repeat;
}
.index-board-1 .index-board-item-inner{
  background: url(../assets/images/2.png) no-repeat;
}
.index-board-2 .index-board-item-inner{
  background: url(../assets/images/3.png) no-repeat;
}
.index-board-3 .index-board-item-inner{
  background: url(../assets/images/4.png) no-repeat;
}
.index-board-item h2 {
  font-size: 18px;
  font-weight: bold;
  color: #000;
  margin-bottom: 15px;
}
.line-last {
  margin-right: 0;
}
.index-board-button {
  margin-top: 20px;
}
.lastest-news {
  min-height: 512px;
}
.hot-tag {
  background: red;
  color: #fff;
}
.new-item {
  display: inline-block;
  width: 230px;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}
</style>
