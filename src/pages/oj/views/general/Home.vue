<template>
  <Row class="index-content">
    <div>
      <div class="carousel-top">
          <a href="#"><img src="../../../../assets/cloud.png"></a>
      </div>
      <div class="announcement-top">
        <Announcements class="announcement"></Announcements>
      </div>

    </div>
      
      <section class="box-warrper dark sec-data-science">
        <div class="card-warrper shadow el-row">
          <div class="el-col el-col-8">
            <a  class="card">
              <div align="center"><img src="../../../../assets/child.png" class="sec-data-science__img"></div>
                <transition name="titlebox" mode="out-in"> <div class="sec-data-science__titlebox">
                  <div class="sec-data-science__inner" v-on:mouseover>
                     <h2 class="sec-data-science__title">开始练习</h2> 
                    <div class="sec-data-science__subtitle">收录各类算法题目，你想要的我们都有</div> 
                    <a href="/problems"> <span class="sec-data-science__span">
                      去练习
                      <span>»</span> 
                    </span> </a>
                </div>
              </div>
              </transition>
            </a>
          </div>
           <div class="el-col el-col-8">
            <a  class="card">
              <div align="center"><img src="../../../../assets/blueCup.png" class="sec-data-science__img"></div>
                 <div class="sec-data-science__titlebox">
                  <div class="sec-data-science__inner">
                    <h2 class="sec-data-science__title">挑战一场数据竞赛</h2> 
                    <div class="sec-data-science__subtitle">与同事们同台竞技，实时排名</div> 
                   <a href="/contests"> <span class="sec-data-science__span">
                      去挑战
                      <span>»</span> 
                    </span> </a>
                </div>
              </div>
            </a>
          </div>
          <div class="el-col el-col-8">
            <a  class="card">
              <div align="center"><img src="../../../../assets/tab.png" class="sec-data-science__img"></div>
                 <div class="sec-data-science__titlebox">
                  <div class="sec-data-science__inner">
                    <h2 class="sec-data-science__title">了解平台</h2> 
                    <div class="sec-data-science__subtitle">一个相互交流，一起提升自我的平台</div> 
                   <a href="/about"> <span class="sec-data-science__span">
                      去探索
                      <span>»</span>
                    </span> </a>
                </div>
              </div>
            </a>
          </div>
  
        </div>
      </section>
      
    <div class="carousel-mid">
        <h3>{{$t('m.UpcomingContests')}}</h3>
        <p><a href="/contests/">{{$t('m.MoreContestes')}}>></a></p>
        <el-carousel :interval="3000" type="card">
          <el-carousel-item>
            <a href="/contest/4"><img src="../../../../assets/fig2.png"></a>
          </el-carousel-item>
          <el-carousel-item>
            <a href="#"><img src="../../../../assets/fig3.png"></a>
          </el-carousel-item>
          <el-carousel-item>
            <a href="#"><img src="../../../../assets/fig4.png"></a>
          </el-carousel-item>
        </el-carousel>
     </div>
  </Row>
</template>

<script>
  import Announcements from './Announcements.vue'
  import api from '@oj/api'
  import time from '@/utils/time'
  import { CONTEST_STATUS } from '@/utils/constants'

  export default {
    name: 'home',
    components: {
      Announcements
    },
    data () {
      return {
        contests: [],
        index: 0
      }
    },
    mounted () {
      let params = {status: CONTEST_STATUS.NOT_START}
      api.getContestList(0, 5, params).then(res => {
        this.contests = res.data.data.results
      })
    },
    methods: {
      getDuration (startTime, endTime) {
        return time.duration(startTime, endTime)
      },
      goContest () {
        this.$router.push({
          name: 'contest-details',
          params: {contestID: this.contests[this.index].id}
        })
      }
    }
  }
</script>

<style lang="less" scoped>
  .index-content{
/*    margin-top: -80px;*/
    margin-left:-2%;
    margin-right: -2%;
  }

  .carousel-top{
    width: 60%;
    height: 300px;
    display: inline-block;
 margin-left:1%;
    img{
      width: 100%;
      height: 300px;
    }
  }
  .announcement-top{
    width: 40%;
    display: inline-block;
    position: absolute;
  }

  .intro{
    height: 300px;

  }

  .carousel-mid{
    padding: 0 10%;
    h3{
      text-align: center;
      font-size: 25px;
      margin: 15px 0;
    }
    p{
      text-align: right;
      a{
        color: #666666;
      }
    }
  }
  
  
  .transitions,.box-warrper,.card-warrper{
    
    padding: 10px 5px 10px 5px;
  }
  .el-col-8{
    width:33.33333%;
  }
  [class*=el-col-]{
    float:left;
    box-sizing:auto;
  }
  .card-warrper.shadow.card{
    box-shadow:0 0 6px 0 rgba(0,0,0,.08)
  }
  .sec-data-science__titlebox{
    margin:10px ;
    height:80px;
    display:block;
    overflow:hidden;
      overflow-x:hidden;
      overflow-y:hidden;
  }
    .card{
      text-align:center;
      justify-content:center;
      padding:24px 24px 24px 24px;
        img{
         
          height:80px;
      };
    
      :hover{
        .sec-data-science__title{opacity:0;transition:all 0.4s ease;transform:translateY(-15px);}
        .sec-data-science__subtitle{transition:all 0.4s ease;transform:translateY(-15px);}
        .sec-data-science__span{opacity:1;transition:all 0.4s ease;transform:translateY(-15px);}
      }}
  .sec-data-science__title{
    font-size:18px;
    color:#000;
    line-height:20px;
    font-weight:600;

  }
  .sec-data-science__subtitle{
    font-style:normal;
    font-size:16px;
    line-height:1em;
    padding:8px 0;
    margin-bottom:lem;
  }
  .sec-data-science__span{
    font-size:20px;
    color:#333;
    line-height:20px;
    font-weight:600;
    transition:all 0.4s ease;
    opacity:0;
  }
  


  .announcement {
    margin-left: -1%;
    margin-right: 4%;
    height: 300px;
    background: url('../../../../assets/cloud3.png');
    filter: alpha(opacity=40)
  }
</style>
