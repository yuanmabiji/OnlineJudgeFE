<template>
  <panel>
    <div slot="title">{{$t('m.Frequently_Asked_Questions')}}</div>
    <div class="content markdown-body">
      <ul>
      <li>ACM排名规则
          <p>比赛排名按照ACM-ICPC的标准。根据解题数量进行排名。如果答题数量相同，则根据总用时和惩罚时间排名。每道试题从比赛开始到提交正确结果为止，期间<b><font color="#0000FF">每一次运行出错(Wrong Answer)</font></b>，将被<b><font color="#0000FF">罚时20分钟</font></b>,编译错误（Compile Error）不计入罚时.</p>
        </li>
        <li>关于输入输出?
          <p>判题机在判题过程中会将题目的每一组测试单元的<code>Input文件流</code>链接到<code>stdin</code>，将stdout重定向到用户的<code>Output文件流</code> 
          因此，你的程序应该从标准输入流<code>stdin</code>获取输出，并将结果输出到标准输出流<code>stdout</code>中。
          </p><p> 
          对于交互评测的题目，在每次输出内容到<code>stdout</code>后，请刷新<code>stdout</code>的缓冲区，以便让判题程序能够正确的读取到你的回答。 </p> </li>
         <li>关于多组测试数据？
          <p>平台中每个题目可以存在多个测试数据单元（文件），每个测试单元可以存在多组测试数据。 
          当存在多组测试数据的时候，你的程序应当不停的从<code>stdin</code>中获取测试数据，直到达到文件末端<code>EOF（End of File）</code>。</p>
           <p> 幸运的是，如果你使用了语言封装的标准流操作函数， 如：<code>C</code>语言的<code>scanf、printf</code>等；
            <code>C++</code>语言的<code>cin、cout</code>等；<code>Java</code>语言的<code>System.out，Scanner</code>等；
            <code>python</code>语言的<code>input()、print()</code>等，
            你将很方便的能够得知当前的读写是否到达了<code>EOF</code>。
            </p><p>你可以借助循环语句来连续读取数据和计算结果，并在抵达<code>EOF</code>后终止循环，退出程序。
          </p>
          <p>
          我们在<font color="#0000FF">tets1000 A+B问题中，提供了标准代码</font>，希望能给你一些灵感
          </p>
          <p><font color="#0000FF">注意java程序必须用class Main包裹</font></p>
        </li>
        <li>为什么我的程序在VC++/VC下能正常编译，但是在平台上就会出现Compilation Error？
        <p>C语言、C++语言不具有跨平台特性，由于在不同操作系统中，系统API、动态链接库或编译环境不相同，通常会出现函数缺失的现象。常见的问题如：
          </p><p>a.在G++/GCC下 main 函数必须定义成int型，定义成 void main 会得到Compilation Error。
          </p><p>b.在G++/GCC中itoa不是一个标准的ANSI函数。
          </p><p>c.GNU C/C++ Compiler环境下，请使用long long替代__int64（或者#define __int64 long long)，使用%lld替代%I64d
          </p><p>d.atoi()不是C语言的标准支持函数，在GNU GCC环境下不支持。
          </p><p>e.scanf_s 为Visual Studio 2005以上版本提供的安全输入函数，GNU GCC环境不支持。
        </p></li>
        <li>提交时执行时间的含义
        <p>评判程序的时候，可能会执行多个用例进行测试。
          如果程序在时间限制范围内，成功执行每一个输入输出，则执行时间取测试用例花费时间最长的那一个，否则没有意义。
        </p>
        </li>
        
        
        <li>显示错误结果
          <p>平台不输出运行的错误结果.评价器黑盒测试程序的输出，如果和标准的输出结果不同，会给出<code>Wrong Answer</code>的判定.</p>
        </li>
        <li>问题与建议
          <p>欢迎联系技术支持：时媛媛 020-31362346.
          </p>
        </li>
      </ul>
    </div>
  </panel>
</template>

<script>
</script>

<style lang="less" scoped>
  .content {
    font-size: 16px;
    margin: 0 50px 40px 50px;
    > ul {
      list-style: disc;
      li {
        font-size: 16px;
        margin-top: 20px;
        &:first-child {
          margin-top: 0;
        }
        p {
          font-size: 14px;
          margin-top: 5px;
        }
      }
    }
  }
</style>
