<template>
  <div class="main_box">
    <div class="top_nav">
      <div class="nav_content">
        <span>欢迎</span>
        <div>
          <span>登录 | 注册</span>
          <span>我的</span>
          <span>帮助中心</span>
          <span>全国热线：88888888</span>
        </div>
      </div>
    </div>
    <div class="full_content">
      <img src="../../assets/imges/logo.jpg" alt="">
      <el-autocomplete
        class="inline-input"
        v-model="state2"
        :fetch-suggestions="querySearch"
        :trigger-on-focus="false"
        @select="handleSelect"
      ></el-autocomplete>
      <div class="icon_box">
        <i class="el-icon-search"></i>
        <i class="el-icon-shopping-cart-2"></i>
      </div>
    </div>
    <div class="full_content" style="height:50px">
      <el-dropdown>
        <el-button type="primary" class="select_btn">
          全部产品<i class="el-icon-arrow-down el-icon--right"></i>
        </el-button>
        <el-dropdown-menu slot="dropdown">
          <el-dropdown-item>黄金糕</el-dropdown-item>
          <el-dropdown-item>狮子头</el-dropdown-item>
          <el-dropdown-item>螺蛳粉</el-dropdown-item>
          <el-dropdown-item>双皮奶</el-dropdown-item>
          <el-dropdown-item>蚵仔煎</el-dropdown-item>
        </el-dropdown-menu>
      </el-dropdown>
      <ul class="nav_list">
        <li>首页</li>
        <li>首页</li>
        <li>首页</li>
        <li>首页</li>
        <li>首页</li>
        <li>首页</li>
        <li>首页</li>
        <li>首页</li>
        <li>首页</li>
      </ul>
    </div>
    <div class="banner">
      <el-carousel :interval="5000" arrow="always" >
        <el-carousel-item v-for="item in banners" :key="banners.index"  trigger="click">
          <img :src="item" alt="" style="width:100%;height:100%">
        </el-carousel-item>
      </el-carousel>
    </div>
    <div class="popular_brands">
      <div class="titie">POPULAR BRANDS RECOMMENDED</div>
      <div class="titie_chin">热门品牌推荐</div>
      <el-carousel :interval="5000" arrow="always"  indicator-position="none">
        <el-carousel-item v-for="item in banners" :key="banners.index"  trigger="click">
        </el-carousel-item>
      </el-carousel>
    </div>
    <div class="popular_brands" id="popular_brands">
      <div class="titie">POPULAR RECOMMENDED</div>
      <div class="titie_chin">热门推荐</div>
    </div>
    <div class="popular_brands" >
      <div class="titie">POPULAR RECOMMENDED</div>
      <div class="titie_chin">热门推荐</div>
    </div>
    <div class="popular_brands" v-for="item in goods">
      <div class="titie">POPULAR RECOMMENDED</div>
      <div class="titie_chin">热门推荐</div>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'yjshopping',
    data () {
      return {
        state2: '',
        flag: true,
        restaurants: [],
        goods: [],
        banners: ['http://112.124.13.227:8080/images/1801be3f551c6b783196d6ef22b9e84c.jpg', 'http://112.124.13.227:8080/images/c83d8cefb6ca6aa07c8edd3d89623bf1.jpg', 'http://112.124.13.227:8080/images/1801be3f551c6b783196d6ef22b9e84c.jpg', 'http://112.124.13.227:8080/images/c83d8cefb6ca6aa07c8edd3d89623bf1.jpg'],
      }
    },
    methods: {
      querySearch (queryString, cb) {
        var restaurants = this.restaurants
        var results = queryString ? restaurants.filter(this.createFilter(queryString)) : restaurants
        // 调用 callback 返回建议列表的数据
        cb(results)
      },
      createFilter (queryString) {
        return (restaurant) => {
          return (restaurant.value.toLowerCase().indexOf(queryString.toLowerCase()) === 0)
        }
      },
      handleSelect (item) {
        console.log(item)
      },
      loadAll () {
        return [
          {
            'value': '三全鲜食（北新泾店）',
            'address': '长宁区新渔路144号'
          },
          {
            'value': 'Hot honey 首尔炸鸡（仙霞路）',
            'address': '上海市长宁区淞虹路661号'
          },
          {
            'value': '新旺角茶餐厅',
            'address': '上海市普陀区真北路988号创邑金沙谷6号楼113'
          },
          {
            'value': '泷千家(天山西路店)',
            'address': '天山西路438号'
          },
          {
            'value': '胖仙女纸杯蛋糕（上海凌空店）',
            'address': '上海市长宁区金钟路968号1幢18号楼一层商铺18-101'
          },
          {
            'value': '贡茶',
            'address': '上海市长宁区金钟路633号'
          },
          {
            'value': '豪大大香鸡排超级奶爸',
            'address': '上海市嘉定区曹安公路曹安路1685号'
          },
          {
            'value': '茶芝兰（奶茶，手抓饼）',
            'address': '上海市普陀区同普路1435号'
          },
          {
            'value': '十二泷町',
            'address': '上海市北翟路1444弄81号B幢-107'
          },
          {
            'value': '星移浓缩咖啡',
            'address': '上海市嘉定区新郁路817号'
          },
          {
            'value': '阿姨奶茶/豪大大',
            'address': '嘉定区曹安路1611号'
          },
          {
            'value': '新麦甜四季甜品炸鸡',
            'address': '嘉定区曹安公路2383弄55号'
          },
          {
            'value': 'Monica摩托主题咖啡店',
            'address': '嘉定区江桥镇曹安公路2409号1F，2383弄62号1F'
          },
          {
            'value': '浮生若茶（凌空soho店）',
            'address': '上海长宁区金钟路968号9号楼地下一层'
          },
          {
            'value': 'NONO JUICE  鲜榨果汁',
            'address': '上海市长宁区天山西路119号'
          },
          {
            'value': 'CoCo都可(北新泾店）',
            'address': '上海市长宁区仙霞西路'
          },
          {
            'value': '快乐柠檬（神州智慧店）',
            'address': '上海市长宁区天山西路567号1层R117号店铺'
          },
          {
            'value': 'Merci Paul cafe',
            'address': '上海市普陀区光复西路丹巴路28弄6号楼819'
          },
          {
            'value': '猫山王（西郊百联店）',
            'address': '上海市长宁区仙霞西路88号第一层G05-F01-1-306'
          },
          {
            'value': '枪会山',
            'address': '上海市普陀区棕榈路'
          },
          {
            'value': '纵食',
            'address': '元丰天山花园(东门) 双流路267号'
          },
          {
            'value': '钱记',
            'address': '上海市长宁区天山西路'
          },
          {
            'value': '壹杯加',
            'address': '上海市长宁区通协路'
          },
          {
            'value': '唦哇嘀咖',
            'address': '上海市长宁区新泾镇金钟路999号2幢（B幢）第01层第1-02A单元'
          },
          {
            'value': '爱茜茜里(西郊百联)',
            'address': '长宁区仙霞西路88号1305室'
          },
          {
            'value': '爱茜茜里(近铁广场)',
            'address': '上海市普陀区真北路818号近铁城市广场北区地下二楼N-B2-O2-C商铺'
          },
          {
            'value': '鲜果榨汁（金沙江路和美广店）',
            'address': '普陀区金沙江路2239号金沙和美广场B1-10-6'
          },
          {
            'value': '开心丽果（缤谷店）',
            'address': '上海市长宁区威宁路天山路341号'
          },
          {
            'value': '超级鸡车（丰庄路店）',
            'address': '上海市嘉定区丰庄路240号'
          },
          {
            'value': '妙生活果园（北新泾店）',
            'address': '长宁区新渔路144号'
          },
          {
            'value': '香宜度麻辣香锅',
            'address': '长宁区淞虹路148号'
          },
          {
            'value': '凡仔汉堡（老真北路店）',
            'address': '上海市普陀区老真北路160号'
          },
          {
            'value': '港式小铺',
            'address': '上海市长宁区金钟路968号15楼15-105室'
          },
          {
            'value': '蜀香源麻辣香锅（剑河路店）',
            'address': '剑河路443-1'
          },
          {
            'value': '北京饺子馆',
            'address': '长宁区北新泾街道天山西路490-1号'
          },
          {
            'value': '饭典*新简餐（凌空SOHO店）',
            'address': '上海市长宁区金钟路968号9号楼地下一层9-83室'
          },
          {
            'value': '焦耳·川式快餐（金钟路店）',
            'address': '上海市金钟路633号地下一层甲部'
          },
          {
            'value': '动力鸡车',
            'address': '长宁区仙霞西路299弄3号101B'
          },
          {
            'value': '浏阳蒸菜',
            'address': '天山西路430号'
          },
          {
            'value': '四海游龙（天山西路店）',
            'address': '上海市长宁区天山西路'
          },
          {
            'value': '樱花食堂（凌空店）',
            'address': '上海市长宁区金钟路968号15楼15-105室'
          },
          {
            'value': '壹分米客家传统调制米粉(天山店)',
            'address': '天山西路428号'
          },
          {
            'value': '福荣祥烧腊（平溪路店）',
            'address': '上海市长宁区协和路福泉路255弄57-73号'
          },
          {
            'value': '速记黄焖鸡米饭',
            'address': '上海市长宁区北新泾街道金钟路180号1层01号摊位'
          },
          {
            'value': '红辣椒麻辣烫',
            'address': '上海市长宁区天山西路492号'
          },
          {
            'value': '(小杨生煎)西郊百联餐厅',
            'address': '长宁区仙霞西路88号百联2楼'
          },
          {
            'value': '阳阳麻辣烫',
            'address': '天山西路389号'
          },
          {
            'value': '南拳妈妈龙虾盖浇饭',
            'address': '普陀区金沙江路1699号鑫乐惠美食广场A13'
          }
        ]
      },
      loading () {
        const scrolltop = window.pageYOffset;
        // const scrollTop=document.querySelector('#popular_brands').offsetTop;
        // console.log(scrollTop)
        if (scrolltop>=800) {
          if (this.flag) {
            this.flag = false;
            const loading = this.$loading({
              lock: true,
              text: 'Loading',
              spinner: 'el-icon-loading',
              background: 'rgba(0, 0, 0, 0.7)'
            });
            setTimeout(() => {
              loading.close();
            }, 2000);
          }
        }
      }
    },
    mounted () {
      this.restaurants = this.loadAll();
      window.addEventListener('scroll',this.loading);
    }
  }
</script>

<style scoped>
  .main_box {

  }

  .top_nav {
    width: 100%;
    height: 40px;
    background-color: #333333;
  }

  .nav_content {
    width: 70%;
    line-height: 40px;
    margin: auto;
    color: #ffffff;
    position: relative;
  }

  .nav_content div {
    position: absolute;
    top: 0;
    right: 0;
  }

  .nav_content div span {
    margin-left: 50px;
  }

  .full_content {
    display: flex;
    position:relative;
    flex-direction: row;
    width: 70%;
    height: 100px;
    /*background-color:pink;*/
    margin: auto;
    margin-bottom: 40px;
  }

  .full_content img {
    width: 100px;
    height: 100px;
  }
  /deep/ .inline-input{
    position:absolute;
    right:150px;
    top:60px;
  }
  /deep/ .inline-input div input {
    border-top: none;
    border-left: none;
    border-right: none;
    border-bottom: 2px solid #cccccc;
    outline: none;
    width: 200px;
  }

  .icon_box {
    position:absolute;
    top: 60px;
    right:0;
  }

  .icon_box i {
    margin-left: 30px;
    width: 40px;
    height: 40px;
    font-size: 40px;
  }

  /deep/ .select_btn {
    border-radius: 0;
    background-color: #232323;
    outline: none;
    border: none;
    font-size: 16px;
  }

  .nav_list {
    margin-left: 60px;
  }

  .nav_list li {
    margin-top: 5px;
    line-height: 30px;
    margin-right: 70px;
    float: left;
    font-size: 16px;
  }

  .nav_list li:hover {
    color: #cccccc;
  }

  .banner {
    width: 100%;
    box-shadow: 0px 20px 20px -20px #5E5E5E;;
  }
  /deep/.banner>div{
    width:80%;
    height:550px;
    margin:auto;
  }
  /deep/.banner>div>div{
    height:550px;
  }
  .popular_brands{
    width:80%;
    height:400px;
    background-color:pink;
    text-align:center;
    margin:auto;
  }
  .titie{
    font-size:22px;
    margin-top:40px;
  }
  .titie_chin{
    font-size:18px;
    margin-top:20px;
    color:#606266;
  }
</style>
