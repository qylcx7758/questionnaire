<!--
 * @Description: gwgoAct.js
 * @version: 1.0
 * @Company: HSZ
 * @Author: Qiu Yiliang
 * @Date: 2019-08-06 14:48:11
 * @LastEditors: 
 * @LastEditTime: 2019-08-12 10:17:58
 -->
<template>
  <div class="box" id="question">
    <div class="content top">
      <h1>2019年培训需求调查问卷</h1>
      <div class="toptext">
        <p>
          <strong>致各位员工:</strong>
        </p>
        <p
          class="topp2"
        >为了准确的了解员工的培训需求，更有针对性的安排培训计划，我们特邀请您参与本次培训需求调研。请您抽空填写此表，我们将根据本次调查结果制定2019年的培训课程，真诚感谢您的参与和支持！</p>
        <p class="topp3">
          <strong>填写说明：</strong>
          <span class="top-span1">请填写此表，并在</span>
          <span class="top-span2">8月12日前</span>
          <span class="top-span1">反馈</span>
        </p>
      </div>
    </div>
    <div class="main content">
      <el-row class="userinfo">
        <el-col :span="12" :class='warnList.name?"warnstyle":""'>
          <el-col :span="8" class="name">
            <span>填写人姓名：</span>
          </el-col>
          <el-col :span="12">
            <el-input v-model="form.name" size="medium" placeholder="请填写姓名" @blur="judgeName"></el-input>
          </el-col>
        </el-col>
        <el-col :span="12" :class='warnList.department?"warnstyle":""'>
          <el-col :span="6" class="department">
            <span>部门：</span>
          </el-col>
          <el-col :span="12">
            <el-input v-model="form.department" size="medium" placeholder="请填写部门"></el-input>
          </el-col>
        </el-col>
      </el-row>
      <div class="section1 section">
        <p class="section-title">
          <strong>第一部分 培训认同度</strong>
        </p>
        <el-row class="questionline">
          <el-col class="questiontitle" :span="24" :class='warnList.radio1?"warnstyle":""'>
            1、您认为公司对培训工作的重视程度如何：
            <span class="tip">* (必填, 单选)</span>
          </el-col>
          <el-radio-group v-model="form.radio1" class="optionbox">
            <el-col :span="12" class="option">
              <el-radio label="1">
                <span class="text">非常重视</span>
              </el-radio>
            </el-col>
            <el-col :span="12" class="option">
              <el-radio label="2">比较重视</el-radio>
            </el-col>
            <el-col :span="12" class="option">
              <el-radio label="3">一般</el-radio>
            </el-col>
            <el-col :span="12" class="option">
              <el-radio label="4">不够重视</el-radio>
            </el-col>
            <el-col :span="12" class="option">
              <el-radio label="5">很不重视</el-radio>
            </el-col>
          </el-radio-group>
        </el-row>
        <el-row class="questionline">
          <el-col class="questiontitle" :span="24" :class='warnList.radio2?"warnstyle":""'>
            2、您认为，培训对于提升您的工作绩效、促进个人职业发展能否起到实际帮助作用，您是否愿意参加培训：
            <span class="tip">* (必填, 单选)</span>
          </el-col>
          <el-radio-group v-model="form.radio2" class="optionbox">
            <el-col :span="24" class="option">
              <el-radio label="1">
                <span class="text">非常有帮助，希望多组织各种培训</span>
              </el-radio>
            </el-col>
            <el-col :span="24" class="option">
              <el-radio label="2">有较大帮助，乐意参加</el-radio>
            </el-col>
            <el-col :span="24" class="option">
              <el-radio label="3">多少有点帮助，会去听听</el-radio>
            </el-col>
            <el-col :span="24" class="option">
              <el-radio label="4">有帮助，但是没有时间参加</el-radio>
            </el-col>
            <el-col :span="24" class="option">
              <el-radio label="5">基本没有什么帮助，不会参加</el-radio>
            </el-col>
          </el-radio-group>
        </el-row>
        <el-row class="questionline">
          <el-col class="questiontitle" :span="24" :class='warnList.radio3?"warnstyle":""'>
            3、部门内部关于行业和市场信息、岗位工作技能的培训、学习、分享是否充分：
            <span class="tip">* (必填, 单选)</span>
          </el-col>
          <el-radio-group v-model="form.radio3" class="optionbox">
            <el-col :span="12" class="option">
              <el-radio label="1">
                <span class="text">非常充分</span>
              </el-radio>
            </el-col>
            <el-col :span="12" class="option">
              <el-radio label="2">充分</el-radio>
            </el-col>
            <el-col :span="12" class="option">
              <el-radio label="3">还可以</el-radio>
            </el-col>
            <el-col :span="12" class="option">
              <el-radio label="4">不够充分</el-radio>
            </el-col>
            <el-col :span="12" class="option">
              <el-radio label="5">基本没有分享</el-radio>
            </el-col>
          </el-radio-group>
        </el-row>
      </div>

      <div class="section2 section">
        <p class="section-title">
          <strong>第二部分 培训的组织和安排</strong>
        </p>
        <el-row class="questionline">
          <el-col class="questiontitle" :span="24" :class='warnList.checkList1?"warnstyle":""'>
            1、鉴于公司的业务特点，您认为最有效的培训方法是什么？ 请选出您认为最有效的3种：
            <span class="tip">* (必填, 多选, 至少选择2项, 最多选择4项)</span>
          </el-col>
          <el-checkbox-group v-model="form.checkList1" :max="4">
            <div class="optionbox">
              <el-col :span="12" class="option">
                <el-checkbox label="1">
                  <span class="text">邀请外部讲师到公司进行集中讲授</span>
                </el-checkbox>
              </el-col>
              <el-col :span="12" class="option">
                <el-checkbox label="2">部门内部组织经验交流与分享讨论</el-checkbox>
              </el-col>
              <el-col :span="12" class="option">
                <el-checkbox label="3">由公司内部有经验的人员进行讲授</el-checkbox>
              </el-col>
              <el-col :span="12" class="option">
                <el-checkbox label="4">光碟、视频等声像资料学习</el-checkbox>
              </el-col>
              <el-col :span="24" class="option">
                <el-checkbox label="5">建立公司图书库，供借阅</el-checkbox>
              </el-col>
              <el-col :span="24" class="option">
                <el-checkbox label="6">
                  其他（请填写您的建议：
                  <el-input class="ideainput" v-model="idea1" size="mini" maxlength="25"></el-input>）
                </el-checkbox>
              </el-col>
            </div>
          </el-checkbox-group>
        </el-row>

        <el-row class="questionline">
          <el-col class="questiontitle" :span="24" :class='warnList.checkList2?"warnstyle":""'>
            2、您认为，最有效的培训方式方法是什么?请选出您认为最有效的3种：
            <span class="tip">* (必填, 多选, 至少选择2项, 最多选择4项)</span>
          </el-col>
          <el-checkbox-group v-model="form.checkList2" :max="4">
            <div class="optionbox">
              <el-col :span="12" class="option">
                <el-checkbox label="1">
                  <span class="text">课堂讲授</span>
                </el-checkbox>
              </el-col>
              <el-col :span="12" class="option">
                <el-checkbox label="2">技术交流会/学习</el-checkbox>
              </el-col>
              <el-col :span="12" class="option">
                <el-checkbox label="3">技能竞赛</el-checkbox>
              </el-col>
              <el-col :span="12" class="option">
                <el-checkbox label="4">微信群学习研讨</el-checkbox>
              </el-col>
              <el-col :span="24" class="option">
                <el-checkbox label="5">读书分享会</el-checkbox>
              </el-col>
              <el-col :span="24" class="option">
                <el-checkbox label="6">
                  其他（请填写您的建议：
                  <el-input class="ideainput" v-model="idea2" size="mini" maxlength="25"></el-input>）
                </el-checkbox>
              </el-col>
            </div>
          </el-checkbox-group>
        </el-row>

        <el-row class="questionline">
          <el-col class="questiontitle" :span="24" :class='warnList.checkList3?"warnstyle":""'>
            3、您认为过去半年内的培训课程哪些地方有待改进：
            <span class="tip">* (必填, 多选)</span>
          </el-col>
          <el-checkbox-group v-model="form.checkList3">
            <div class="optionbox">
              <el-col :span="8" class="option">
                <el-checkbox label="1">
                  <span class="text">培训内容理论程度应深化</span>
                </el-checkbox>
              </el-col>
              <el-col :span="8" class="option">
                <el-checkbox label="2">培训内容实用程度应加强</el-checkbox>
              </el-col>
              <el-col :span="8" class="option">
                <el-checkbox label="3">提高讲师水平</el-checkbox>
              </el-col>
              <el-col :span="8" class="option">
                <el-checkbox label="4">培训时间安排更合理</el-checkbox>
              </el-col>
              <el-col :span="8" class="option">
                <el-checkbox label="5">培训形式应多样化</el-checkbox>
              </el-col>
              <el-col :span="8" class="option">
                <el-checkbox label="6">培训次数太少，可适当增加</el-checkbox>
              </el-col>
              <el-col :span="8" class="option">
                <el-checkbox label="7">培训时间安排更合理</el-checkbox>
              </el-col>
              <el-col :span="16" class="option">
                <el-checkbox label="8">
                  其他（请填写您的建议：
                  <el-input class="ideainput" v-model="idea3" size="mini" maxlength="25"></el-input>）
                </el-checkbox>
              </el-col>
            </div>
          </el-checkbox-group>
        </el-row>

        <el-row class="questionline">
          <el-col class="questiontitle" :span="24" :class='warnList.radio4?"warnstyle":""'>
            4、假如，鉴于您在某一领域的丰富经验，您被推荐担任某一门课程的内部讲师，您是否乐意：
            <span class="tip">* (必填, 单选)</span>
          </el-col>
          <el-radio-group v-model="form.radio4" class="optionbox">
            <el-col :span="24" class="option">
              <el-radio label="1">
                <span class="text">非常乐意，既可以锻炼自己，又可以分享知识，何乐而不为</span>
              </el-radio>
            </el-col>
            <el-col :span="24" class="option">
              <el-radio label="2">乐意，但是没有经验，希望公司能提供关于讲师技能提升方面的培训</el-radio>
            </el-col>
            <el-col :span="24" class="option">
              <el-radio label="3">乐意，但是没有时间做这个事情</el-radio>
            </el-col>
            <el-col :span="24" class="option">
              <el-radio label="4">需要考虑一下</el-radio>
            </el-col>
            <el-col :span="24" class="option">
              <el-radio label="5">不会担任</el-radio>
            </el-col>
          </el-radio-group>
        </el-row>

        <el-row class="questionline">
          <el-col class="questiontitle" :span="24" :class='warnList.radio5?"warnstyle":""'>
            5、您希望的或者所能接受的培训频次是怎样的：
            <span class="tip">* (必填, 单选)</span>
          </el-col>
          <el-radio-group v-model="form.radio5" class="optionbox">
            <el-col :span="8" class="option">
              <el-radio label="1">
                <span class="text">每周一次</span>
              </el-radio>
            </el-col>
            <el-col :span="8" class="option">
              <el-radio label="2">半月一次</el-radio>
            </el-col>
            <el-col :span="8" class="option">
              <el-radio label="3">每月一次</el-radio>
            </el-col>
            <el-col :span="8" class="option">
              <el-radio label="4">两月一次</el-radio>
            </el-col>
            <el-col :span="8" class="option">
              <el-radio label="5">每季度一次</el-radio>
            </el-col>
            <el-col :span="8" class="option">
              <el-radio label="6">半年一次</el-radio>
            </el-col>
            <el-col :span="8" class="option">
              <el-radio label="7">每年一次</el-radio>
            </el-col>
            <el-col :span="16" class="option">
              <el-radio label="8">
                其他（请填写您的建议：
                <el-input class="ideainput" v-model="idea4" size="mini" maxlength="25"></el-input>）
              </el-radio>
            </el-col>
          </el-radio-group>
        </el-row>

        <div class="section3 section">
          <p class="section-title">
            <strong>第三部分 培训需求信息</strong>
          </p>

          <el-row class="questionline">
            <el-col class="questiontitle" :span="24" :class='warnList.checkList4?"warnstyle":""'>
              1、您认为个人2019年培训需求重点在于哪些方面：
              <span class="tip">* (必填, 多选)</span>
            </el-col>
            <el-checkbox-group v-model="form.checkList4">
              <div class="optionbox">
                <el-col :span="8" class="option">
                  <el-checkbox label="1">
                    <span class="text">岗位知识</span>
                  </el-checkbox>
                </el-col>
                <el-col :span="8" class="option">
                  <el-checkbox label="2">岗位专业技能</el-checkbox>
                </el-col>
                <el-col :span="8" class="option">
                  <el-checkbox label="3">个人职业化修炼</el-checkbox>
                </el-col>
                <el-col :span="8" class="option">
                  <el-checkbox label="4">管理技能</el-checkbox>
                </el-col>
                <el-col :span="8" class="option">
                  <el-checkbox label="5">互联网架构</el-checkbox>
                </el-col>
                <el-col :span="24" class="option">
                  <el-checkbox label="6">
                    其他（请填写您的建议：
                    <el-input class="ideainput" v-model="idea5" size="mini" maxlength="25"></el-input>)
                  </el-checkbox>
                </el-col>
              </div>
            </el-checkbox-group>
          </el-row>

          <el-row class="questionline">
            <el-col class="questiontitle" :span="24" :class='warnList.checkList5?"warnstyle":""'>
              2、您认为个人目前最需要哪方面的培训：
              <span class="tip">* (必填, 多选)</span>
            </el-col>
            <el-checkbox-group v-model="form.checkList5">
              <div class="optionbox">
                <el-col
                  :span="skills.indexOf(item)==23?24:(skills.indexOf(item)==24?24:8)"
                  class="option"
                  v-for="item in skills"
                  :key="item"
                >
                  <el-checkbox :label="(skills.indexOf(item)+1).toString()">
                    <span class="text">
                      {{item}}
                      <span v-if="skills.indexOf(item)==(skills.length-1)">
                        <el-input class="ideainput" v-model="idea6" size="mini" maxlength="25"></el-input>)
                      </span>
                    </span>
                  </el-checkbox>
                </el-col>
              </div>
            </el-checkbox-group>
          </el-row>

          <el-row class="questionline">
            <el-col class="questiontitle" :span="24" :class='warnList.checkList6?"warnstyle":""'>
              3、您觉得，您部门的主管2019年的培训需求重点可能在于哪些方面：
              <span class="tip">* (必填, 多选)</span>
            </el-col>

            <el-checkbox-group v-model="form.checkList6">
              <div class="optionbox">
                <el-col :span="8" class="option">
                  <el-checkbox label="1">
                    <span class="text">管理技能</span>
                  </el-checkbox>
                </el-col>
                <el-col :span="8" class="option">
                  <el-checkbox label="2">团队领导力</el-checkbox>
                </el-col>
                <el-col :span="8" class="option">
                  <el-checkbox label="3">团队建设</el-checkbox>
                </el-col>
                <el-col :span="8" class="option">
                  <el-checkbox label="4">互联网思维</el-checkbox>
                </el-col>
                <el-col :span="8" class="option">
                  <el-checkbox label="5">技术层面提升</el-checkbox>
                </el-col>
                <el-col :span="24" class="option">
                  <el-checkbox label="6">
                    其他（请补充：
                    <el-input class="ideainput" v-model="idea7" size="mini" maxlength="25"></el-input>)
                  </el-checkbox>
                </el-col>
              </div>
            </el-checkbox-group>
          </el-row>
        </div>

        <div class="section4 section">
          <p class="section-title" >
            <strong>第四部分 其他意见及建议</strong>
          </p>
          <el-row>
            <el-col :lg="20" :md="24">
              <ul>
                <li class="suggest">
                  <el-input clearable v-model="form.suggestion[0]" maxlength="100">
                    <template slot="prepend">1、</template>
                  </el-input>
                </li>
                <li class="suggest">
                  <el-input clearable v-model="form.suggestion[1]" maxlength="100">
                    <template slot="prepend">2、</template>
                  </el-input>
                </li>
                <li class="suggest">
                  <el-input clearable v-model="form.suggestion[2]" maxlength="100">
                    <template slot="prepend">3、</template>
                  </el-input>
                </li>
              </ul>
            </el-col>
          </el-row>
        </div>
      </div>
    </div>

    <div class="footer">
      <el-col :span="24" class="footerp">
        <p>感谢您抽空填写此问卷，谢谢！</p>
      </el-col>
      <el-col :lg="20" :md="24" class="footerbtnbox">
        <el-button type="primary" @click="onSubmit">提交</el-button>
      </el-col>
    </div>
  </div>
</template>
<script>
export default {
  name: "question",
  props: {
    msg: String
  },

  data() {
    return {
        isJudgeName:"",
        // 是否开启严格的表单验证
    isStrict:true,
        //新的对象用于修改数据并提交
        submitForm:{},
      // 状态清空的数组
      emptyForm:{},
      // 填写缺失提示样式相关
      warnList: {},
      // 是否填写完整，可以提交
      submitStatus: "1",
      mincheckNum: 2,
      maxcheckNum: 4,
      //   是否正确提交过
      hasSubmit: "0",
      idea1: "",
      idea2: "",
      idea3: "",
      idea4: "",
      idea5: "",
      idea6: "",
      idea7: "",
      form: {
        name: "",
        department: "",
        radio1: "",
        radio2: "",
        radio3: "",
        checkList1: [],  //idea1
        checkList2: [],     //idea2
        checkList3: [], //idea3
        radio4: "",     
        radio5: "",          //idea4
        checkList4: [],        //idea5
        checkList5: [],        //idea6
        checkList6: [],           //idea7
        suggestion: []
      },

      skills: [
        "时间管理",
        "技术文档编写技巧",
        "编码规范（c/c++,java）",
        "云手机控制技术及实现",
        "Python",
        "大数据分析",
        "测试自动化工具",
        "安卓、IOS、WIN客户端崩溃原理",
        "自动化运维",
        "绩效管理",
        "互联网架构",
        "项目管理",
        "PMP",
        "Spring Cloud",
        "设计模式",
        "进程和线程深入理解",
        "多线路编程",
        "线程锁、数据库锁的深入理解",
        "jvm内存回收机制",
        "开发测试流程及工具使用",
        "内核及虚拟机原理",
        "基于libevent的socket异步编程",
        "安卓开发关于兼容性稳定性的最佳实践",
        "从设备（物理机，虚拟机）到remotePlay到sdk到客户端的流程分工详细",
        "其他（请补充： "
      ],
      //当选项为建议时的补充
      keyArray:[
          {
              "key":"checkList1",
              "label":"6",
              "idea":"idea1"
          },
           {
              "key":"checkList2",
              "label":"6",
              "idea":"idea2"
          },
           {
              "key":"checkList3",
              "label":"8",
              "idea":"idea3"
          },
           {
              "key":"radio5",
              "label":"8",
              "idea":"idea4"
          },
           {
              "key":"checkList4",
              "label":"6",
              "idea":"idea5"
          },
           {
              "key":"checkList5",
              "label":"25",
              "idea":"idea6"
          },
           {
              "key":"checkList6",
              "label":"6",
              "idea":"idea7"
          },
      ]
    };
  },
  created() {
    //   查询缓存中是否有成功提交记录
    if (window.localStorage.getItem("hasSubmit") == "0") {
      this.hasSubmit = "0";
    } else if (window.localStorage.getItem("hasSubmit") == "1") {
      this.hasSubmit = "1";
    }
    this.createWarnList();
    // 创造清空的表单数据，用于提交后清空
    this.emptyForm=Object.assign("",this.form)
    // console.log(this.warnList);
  },
  methods: {
    //   当选择为建议时，填补文字
    // obj:表单对象;itemKey:具体的key;keyArray:和建议挂钩的数组；
      addIdea(obj,itemKey,keyArray){
          var that=this;
        //   console.log(this)
          for(let i=0;i<keyArray.length;i++){
            //   console.log(keyArray[i])
            //   console.log(this)
              if(keyArray[i].key==itemKey){
                  //为可以有建议的选项
                //   let index=i
                //表单具体项
                let item=obj[itemKey];
                //建议数组
                let arrayItem=keyArray[i];
                  if(that.isArray(item)){
                      var selectIndex=item.indexOf(arrayItem.label);
                      if(selectIndex>-1){
                            let idea=that[arrayItem.idea];
                          //用建议的值替换数组中数据
                           item.splice(selectIndex,1,idea)
                           return item
                      }
                  }else if(item==arrayItem.label){
                    let value=that[arrayItem.idea]
                    //   为单选的字符串
                    return value
                  }
              }
          }
      },

    isArray(o) {
      return Object.prototype.toString.call(o) == "[object Array]";
    },
    // 创造用于制造缺失填写提示的数组
    createWarnList() {
      this.warnList = Object.assign({}, this.form, {
        checkList1: "",
        checkList2: "",
        checkList3: "",
        checkList4: "",
        checkList5: "",
        checkList6: ""
      });
    },
    changeMinCheckNum() {
      // this.mincheckNum=2;
    },
    //判断姓名
    judgeName(){
          let reg=/^[\u4E00-\u9FA5\uf900-\ufa2d·s]{2,20}$/;
          let name=this.form.name.trim();
        if(name && reg.test(name)){
            this.isJudgeName=true;
            this.warnList.name=""
        }else{
            this.isJudgeName=false;
            this.warnList.name="1"
             const h = this.$createElement;
            this.$notify({
            message: h('i', { style: 'color: teal'}, '请填写正确格式的姓名'),
            duration:1500
            });         
        }
    },
    // clear
    onSubmit() {
      // if(this.hasSubmit=="1"){
      //      this.$alert('问卷只能提交一次', {
      //   confirmButtonText: '确定'
      // })
      // return
      // }
      // console.log(this.form);
      const form = this.form;
      for (const key in form) {
        if (form.hasOwnProperty(key)) {
          const ele = form[key];
          if (!ele) {
            //打上未填写完整的标记
            this.warnList[key]="1";
          }else if(this.isArray(ele)){
              if((key == "checkList1" || key=="checkList2")&&  (ele.length < 2 || ele.length > 4)){
                 
                   this.warnList[key]="1";
              }else if(ele.length==0){
                  this.warnList[key]="1";
              }else{
                   this.warnList[key]=""; 
              }
          }else if(key=="name"){
              if(!this.isJudgeName){
                  this.warnList[key]="1";
              }
          }else{
            //   填写完整的项
              this.warnList[key]="";
          }


          if( this.warnList[key]=="1"){
              this.submitStatus = "0";
          }
        }
      }
        if ( this.submitStatus == "1" || !this.isStrict) {
            // 需要重新创造一个数组提交
            this.submitForm=Object.assign({},this.form);
            
            for (const key in  this.submitForm) {
                if (this.submitForm.hasOwnProperty(key)) {
                    // console.log(this)
                    // const element = object[key];
                    var value=this.addIdea( this.submitForm,key,this.keyArray)
                    if(value){
                        this.submitForm[key]=value;
                    }
                }
               
            }
            // console.log(this.submitForm)
            // console.log(JSON.stringify(this.submitForm))
            this.submitForm={};
            //用清空的对象来清空，因为有挂载属性，所以不能直接清空
            this.form=Object.assign({},this.emptyForm)
            //  console.log(this.submitForm)
            //  console.log(this.form)
            this.$message({
              message: "提交成功，真诚感谢您的参与和支持!",
              type: "success"
            });
             window.localStorage.setItem("hasSubmit", "1");
            //  表示已经成功提交过
            this.hasSubmit = 1;
            this.submitStatus = 1;
          } else {
            this.submitStatus = 1;
            this.$message({
              message: "请将问卷信息填写完全，不符合的项已做标记",
              type: "warning"
            });
          }
    }
  }
};
</script>
<style>
* {
  margin: 0;
  padding: 0;
}
li {
  list-style: none;
}
.warnstyle {
  /* background-color: #e6a23c; */
  color: #e6a23c;
}
.box {
  width: 100%;
  height: 100%;
  border: 1px solid red;
  box-sizing: border-box;
  padding: 20px 40px;
  min-width: 992px;
  /* background-color: rgba(128, 133, 144, 0.15); */
}
.top {
  margin-bottom: 20px;
  border-bottom: 1px teal solid;
}
.content {
  background-color: #fff;
}

.toptext {
  /* border: 1px saddlebrown solid; */
  padding: 20px 0;
  text-align: left;
}
.topp2 {
  padding: 10px 0 20px;
}

.top-span1 {
  color: blue;
}
.top-span2 {
  color: red;
}

.questionline {
  margin-bottom: 10px;
}
.main {
  /* border: 1px pink solid; */
}
.ideainput input {
  border: 1px solid #000;
  border-top: none;
  border-left: none;
  border-right: none;
  border-radius: 0;
}
.ideainput {
  width: 80%;
}

.userinfo {
  margin-bottom: 20px;
  border-bottom: 1px teal solid;
  padding: 0px 0 20px;
}
.name,
.department {
  height: 36px;
  line-height: 36px;
  font-weight: bold;
}

.section {
  padding-top: 20px;
}
.suggest {
  border: 1px solid #000;
  border-bottom: none;
}
.suggest:nth-of-type(3) {
  border-bottom: 1px solid #000;
}
.suggest .el-input-group__prepend {
  padding: 0 5px 0 10px;
   /* border-top: none;
  border-left: none;
  border-right: none; */
}

.suggest input{
  line-height: 1;
    border-top: none;
  border-left: none;
  border-right: none;
  border-radius: 0;
}
.footer {
  box-sizing: border-box;
  padding-top: 30px;
  /* border: 1px blue solid; */
  height: 100px;
  background-color: #fff;
}
.footerp {
  text-align: left;
}
.footerbtnbox {
  padding-top: 10px;
  text-align: center;
}
/* 下面是section1 部分 */
.section-title {
  text-align: left;
  margin-bottom: 15px;
  font-size: 20px;
}
.questiontitle {
  text-align: left;
  margin-bottom: 10px;
}
.optionbox {
  text-align: left;
  padding-left: 25px;
  width: 100%;
}
.optionbox .option span {
  /* padding: 10px 0; */
  font-family: "微软雅黑";
  font-size: 16px;
  /* font-weight: bold; */
}
.option {
  padding: 8px 0;
}
.tip {
  color: red;
}
/* .el-row {
  margin-bottom: 20px;
}
.el-col {
  border-radius: 4px;
} */
/* .bg-purple-dark {
  background: #99a9bf;
}
.bg-purple {
  background: #d3dce6;
}
.bg-purple-light {
  background: #e5e9f2;
}
.grid-content {
  border-radius: 4px;
  min-height: 36px;
}
.row-bg {
  padding: 10px 0;
  background-color: #f9fafc;
} */
</style>
