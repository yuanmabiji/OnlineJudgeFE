<template>
  <div>
  <panel class="container">
      <div slot="title">关于“云台”</div>
<div class="content">
       <p>  云台是一个支持多编程语言的在线知识竞赛系统。希望将技术交流融入到日常中，让大家更加方便的交流学习，从而构建了一个面向行内的在线知识竞赛平台。
        </p><p>平台拥有在线实时代码评测功能，支持高并发。 平台目的不仅程序设计类课程，未来将提供容纳客观题（如选择、填空题）和主观题（如问答题）的题库，
        未支持各种线上学习测评使用。</p><p>平台以云计算技术架构作为基础，建立一个弹性的、支持大规模并发访问的系统，不断迭代构建完善。</p>
        </div>
       </panel>


    <panel class="container">
      <div slot="title">平台使用的编译器</div>
      
      <div class="content markdown-body">
      <p>     判题机运行在Linux平台下，C、C++均使用的是GCC编译器，文本编码格式为UTF-8.
      平台支持的C,C++,JAVA,PYTHON编译器，包含默认通用库,<font color="#0000FF">不支持第三方库</font>。</p>
        <ul>
          <li v-for="lang in languages">{{lang.name}} ( {{lang.description}} )
            <pre>{{lang.config.compile.compile_command}}</pre>
          </li>
        </ul>
      </div>
    </panel>

    <panel :padding="15" class="container">
      <div slot="title">评判结果状态解释</div>
      <div class="content">
        <ul>
          <li><b>Pending & Juding</b> : {{$t('m.Pending_Juding')}}</li>
          <li><b>Compile Error</b> :	{{$t('m.Compile_Error')}}
      </li>
          <li><b>Accepted</b> :	{{$t('m.Accepted')}}</li>
          <li><b>Wrong Answer</b> :	{{$t('m.Wrong_Answer')}}</li>
          <li>
            <b>Runtime Error</b>
            :	{{$t('m.Runtime_Error')}}
          </li>
          <li><b>Time Limit Exceeded</b>
            :	{{$t('m.Time_Limit_Exceeded')}}
          </li>
          <li><b>Memory Limit Exceeded</b> :	{{$t('m.Memory_Limit_Exceeded')}}</li>
          <li><b>System Error</b> :	{{$t('m.System_Error')}}
          </li>
        </ul>
      </div>
    </panel>
     <panel :padding="15" class="container">
      <div slot="title">平台判题流程</div>
      <div class="content">
        <img src="../../../../assets/line.png" class="about_img">
        <p>系统编译用户提交的源代码，运行程序并注入测试数据，然后等待程序应答输出结果并结束。 程序运行结束后，再和标准结果进行比较，比较包括字符、数字、标点符号以及空格、换行符等， 若输出结果与参考答案数据严格相同，则判定为通过（Accepted）。如果程序输出的内容和预设的数据不能正确匹配， 则会判为答案错误等。如果程序代码不能被正确编译，则报编译错误。评测结束后，结果数据将被保存在系统的数据库中以便向用户反馈。</p>
        </div>
    </panel>

  </div>
</template>

<script>
  import utils from '@/utils/utils'

  export default {
    data () {
      return {
        languages: []
      }
    },
    beforeRouteEnter (to, from, next) {
      utils.getLanguages().then(languages => {
        next(vm => {
          vm.languages = languages
        })
      })
    }
  }
</script>

<style scoped lang="less">
  .container {
    margin-bottom: 20px;

    .content {
      font-size: 16px;
      margin: 0 50px 20px 50px;
      > ul {
        list-style: disc;
        li {
          line-height: 2;
          .title {
            font-weight: 500;
          }
        }
      }
    }
  }
 
</style>
