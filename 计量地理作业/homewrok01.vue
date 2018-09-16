<template>
    <div id="homewrok01">
      <el-button type="primary" @click="turnOff()">删除</el-button>
      <el-button type="primary" @click="tableMaking(1)">2000-2016年人均GDP变化折线图</el-button>
      <el-button type="primary" @click="tableMaking(2)">各省份年人均GDP平均值</el-button>
      <el-button type="primary" @click="tableMaking(3)">年份变异系数</el-button>
      <div id="mountNode"  ></div>
    </div>
</template>

<script>
  import G2 from '@antv/g2';
    export default {
        name: "homewrok01",
      data(){
          return{
            year:[2000,	2001 ,2002 ,2003 ,2004 ,2005 ,2006,2007,2008 ,	2009 ,2010 ,2011 ,2012 ,2013 	,2014 ,2015 ,2016],
            province:[
              '北京','天津市','河北省','山西省','内蒙古自治区', '辽宁省','吉林省','黑龙江省','上海市','江苏省','浙江省','安徽省','福建省','江西省','山东省','河南省','湖北省','湖南省','广东省','广西壮族自治区','海南省','重庆市','四川省','贵州省','云南省','西藏自治区','陕西省','甘肃省','青海省','宁夏回族自治区','新疆维吾尔自治区',
            ],
          
            GDPdata:[24122,26998,30840,34892,41099,45444,49505,60096,64491,66940,73856,81658,87475,94648,99995,106497,114690,17353,19141,21387,25544,30575,35783,40961,47970,58656,62574,72994,85213,93173,100105,105231,107960,115613,7592,8251,8960,10251,12487,14782,16894,19662,22986,24581,28668,33969,36584,38909,39984,40255,42866,5722,6226,7082,8642,10742,12495,14106,17805,21506,21522,26283,31357,33628,34984,35070,34919,35285,6502,7216,8162,10039,12767,16331,20047,26521,34869,39735,47347,57974,63886,67836,71046,71101,74204,11177,12015,13000,14270,15835,18983,21802,26057,31739,35149,42355,50760,56649,61996,65201,65354,50292,7351,7893,8714,9854,11537,13348,15625,19383,23521,26595,31599,38460,43415,47428,50160,51086,54073,8294,8900,9541,10638,12449,14434,16268,18580,21740,22447,27076,32819,35711,37697,39226,39462,40362,29671,32201,35329,39128,46338,51474,57310,62041,66932,69165,76074,82560,85373,90993,97370,103796,113731,11765,12882,14396,16830,20223,24560,28685,33837,40014,44253,52840,62290,68347,75354,81874,87995,95394,13416,14713,16978,20444,24352,27703,31684,36676,41405,43842,51711,59249,63374,68805,73002,77644,83923,4779,5313,5736,6375,7681,8670,10044,12039,14448,16408,20888,25659,28792,32001,34425,35997,39254,11194,11892,12938,14333,16469,18646,21152,25582,29755,33437,40025,47377,52763,58145,63472,67966,74288,4851,5221,5829,6624,8097,9440,10679,13322,15900,17335,21253,26150,28800,31930,34674,36724,40220,9326,10195,11340,13268,16413,20096,23546,27604,32936,35894,41106,47335,51768,56885,60879,64168,68049,5450,5959,6487,7376,9201,11346,13279,16012,19181,20597,24446,28661,31499,34211,37072,39123,42363,6293,6867,7437,8378,9898,11431,13150,16386,19858,22677,27906,34197,38572,42826,47145,50654,55191,5425,6120,6734,7589,9165,10426,11830,14869,18147,20428,24719,29880,33480,36943,40271,42754,46063,12736,13849,15361,17795,20870,24435,28077,33272,37638,39436,44736,50807,54095,58833,63469,67503,73290,4652,5058,5558,6169,7461,8788,10240,12277,14652,16045,20219,25326,27952,30741,33090,35190,38042,6798,7052,7781,8592,9812,10871,12650,14923,17691,19254,23831,28898,32377,35663,38924,40818,44396,5616,6219,7052,8091,9624,10982,12437,16629,20490,22920,27596,34500,38914,43223,47850,52321,58199,4956,5376,5890,6623,7895,9060,10546,12963,15495,17339,21182,26133,29608,32617,35128,36775,39835,2759,3000,3257,3701,4317,5052,5750,7878,9855,10971,13119,16413,19710,23151,26437,29847,33242,4769,5015,5366,5871,7012,7835,8961,10609,12570,13539,15752,19265,22195,25322,27264,28806,31358,4572,5324,6117,6893,8103,9114,10396,12083,13588,15008,17027,20077,22936,26326,29252,31999,35496,4968,5506,6145,7028,8587,9899,11762,15546,19700,21947,27133,33464,38564,43117,46929,47626,50528,4129,4386,4768,5429,6566,7477,8749,10614,12421,13269,16113,19595,21978,24539,26433,26165,27508,5138,5774,6478,7346,8693,10045,11753,14507,18421,19454,24115,29522,33181,36875,39671,41252,43750,5376,6039,6647,7734,9199,10239,11784,15142,19609,21777,26860,33043,36394,39613,41834,43805,47157,7372,7945,8457,9828,11337,13108,14871,16999,19797,19942,25034,30087,33796,37553,40648,40036,40466,],
            gdpArray:[],
            yearAverage:[],
            provinceAverage:[],
            yearSDvalue:[],
            provinceSDvalue:[],
            yearCV:[],
            provinceCV:[],
            chart:[]
          }
      },methods:{
        //计算平均值
        yearAverageCompute:function(data,index){
            var sum = 0;
            var average = 0;
            //计算各省市的年份平均值
            if (index==='year_average'){
              for (var i =0;i<data.length;i++){
                for (var j = 0;j<data[i].length;j++){
                  sum+=data[i][j];
                }
                average = sum/17;
                sum=0;
                this.yearAverage.push(average);
                average=0;
              }
              console.log(this.yearAverage)
            }
            //计算各年份的省市平均值
            else if (index==='province_average'){
              var province_average_data=[];
              //最后获取每个年份的省市平均值，因此第一个i是year数组的长度
              for (i=0;i<this.year.length;i++){
                //获取各个年份各个省市的gdp，因此这里的j是省市数组的长度
                for ( j =0;j<data.length;j++){
                  province_average_data.push(data[j][i]);
                  sum+=province_average_data[j];
                }
                average=sum/this.province.length;
                this.provinceAverage.push(average);
                sum=0;
                average=0;
                province_average_data=[]
              }
              console.log(this.provinceAverage)
            }

        },
        //计算标准差和变异系数
        SDcompute_CV:function(data,index){
            var sum = function (x,y) {return x+y};
            var square =function (x) {return x*x};
            var squrt = function (x) {
              var temp = [];
              for (var n = 0;n<x.length;n++){
                temp.push(Math.sqrt(x[n]/16))
              }
              return temp;
            };
            var decreaseValue=[];
            var sumvalue=[];
            //各省市不同年份的标准差和变异系数
            if (data==='year'){
              for (var i =0;i<this.yearAverage.length;i++){
                for (var j =0;j<this.gdpArray[i].length;j++){
                  var yearAverage = parseInt(this.yearAverage[i]);
                  var yearValue = parseInt(this.gdpArray[i][j]);
                  var temp = (yearValue-yearAverage)*(yearValue-yearAverage);
                  decreaseValue.push(temp);
                }
                sumvalue.push(decreaseValue.reduce(sum));
                decreaseValue=[]
              }
              this.yearSDvalue=squrt(sumvalue);
              for (var n = 0;n<this.yearSDvalue.length;n++){
                this.yearCV.push(this.yearSDvalue[n]/this.yearAverage[n])
              }
              console.log(this.yearCV);
              console.log(squrt(sumvalue));
              console.log(decreaseValue)
            }
            //各年份不同省份的标准差和变异系数
            else if (data==='province'){
              var difProvince=[];
              for (i=0;i<this.provinceAverage.length;i++){
                for (j = 0;j<this.gdpArray.length;j++){
                  for ( n =0;n<17;n++){
                    //先获取每个年份不同省份的gdp
                    difProvince.push(this.gdpArray[j][i]);
                    break;
                  }
                }
                //平均值
                var mean = parseInt(this.provinceAverage[i]);
                //通过函数式编程将diffProvince数组中的每个值减去平均值
                var devitations = difProvince.map(function (x) {return x-mean});
                //通过函数式编程得到标准差
                var stddev = Math.sqrt(devitations.map(square).reduce(sum)/30);
                this.provinceSDvalue.push(stddev);
                this.provinceCV.push(stddev/mean);
                difProvince=[];
              }
              console.log(difProvince);
              console.log(this.provinceSDvalue);
              console.log(this.provinceCV)
            }


        },
        //创建gdp数组
        createArray:function () {
            var n;
            //for循环遍历GDP数组
            for (var i =1;i<=this.GDPdata.length;i++){
              //每17个往gdpArray里面添加一个数组
              if (i%17===0){
                n=i;
                var arr=[];
                for (var j=n-17;j<n;j++){
                  arr.push(this.GDPdata[j])
                }
                this.gdpArray.push(arr);
                arr =[]
              }
            }
            if (this.gdpArray.length===0){
              console.log('wrong')
            }
            else{
              console.log(this.gdpArray)
            }
        },
        //图表制作
        tableMaking:function(index){
          var data=[];
          var chart = new G2.Chart({
            container: 'mountNode',
            forceFit: true,
            height:600,
            width:300
          });
          this.chart=chart;
          //2000-2016年期间中国大陆年人均GDP变化折线图
          if (index===1){
            for (var i =0;i<this.year.length;i++){
              var temp={year:this.year[i],value:this.provinceAverage[i]};
              data.push(temp);
            }
            chart.source(data);
            chart.scale('value', {
              min: 0
            });
            chart.scale('year', {
              range: [0, 1]
            });
            chart.tooltip({
              crosshairs: {
                type: 'line'
              }
            });
            chart.line().position('year*value');
            chart.point().position('year*value').size(4).shape('circle').style({
              stroke: '#fff',
              lineWidth: 1
            });
          }
          //中国大陆各省份年人均GDP的多年平均值（2000-2016年）
          else if (index===2){
            data=[];
            for (i = 0;i<this.province.length;i++){
              temp={province:this.province[i],value:this.yearAverage[i]};
              data.push(temp)
            }
            chart.source(data);
            chart.scale('province', {
              tickInterval: 20
            });
            chart.interval().position('province*value');
          }
          else if (index ===3){
              data=[];
              for (i=0;i<this.year.length;i++){
                temp={year:this.year[i],value:this.provinceCV[i]};
                data.push(temp)
              }
            chart.source(data);
            chart.scale('value', {
              min: 0
            });
            chart.scale('year', {
              range: [0, 1]
            });
            chart.tooltip({
              crosshairs: {
                type: 'line'
              }
            });
            chart.line().position('year*value');
            chart.point().position('year*value').size(4).shape('circle').style({
              stroke: '#fff',
              lineWidth: 1
            });
          }
          chart.render();
        },
        turnOff(){
         this.chart.destroy();
        }
      },mounted(){
        this.createArray();
        this.yearAverageCompute(this.gdpArray,'year_average');
        this.yearAverageCompute(this.gdpArray,'province_average');
        this.SDcompute_CV('year');
        this.SDcompute_CV('province')
  }

    }
</script>

<style scoped>

</style>
