<template>
  <div id="app">
    <img class="logo" alt="Vue logo" src="./assets/logo.png" />
    <HelloWorld msg="Welcome to Your Vue.js App" />
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";

export default {
  name: "App",
  components: {
    HelloWorld,
  },
  mounted() {
    // array.reduce(function(total, currentValue, currentIndex, arr), initialValue);
    /*
      total: 必需。初始值, 或者计算结束后的返回值。
      currentValue： 必需。当前元素。
      currentIndex： 可选。当前元素的索引；                     
      arr： 可选。当前元素所属的数组对象。
      initialValue: 可选。传递给函数的初始值，相当于total的初始值。
    */

    //  数组求和
    // const arr = [12, 34, 23];
    // const sum = arr.reduce((total, num) => total + num);
    // const sum = arr.reduce((total, num) => total + num, 10);
    var result = [
      { subject: "math", score: 88 },
      { subject: "chinese", score: 95 },
      { subject: "english", score: 80 },
    ];
    // const sum = result.reduce((accumulator, cur) => accumulator + cur.score, 0);
    const sum = result.reduce(
      (accumulator, cur) => accumulator + cur.score,
      -10
    );
    console.log(sum);

    // 数组最大值
    const a = [12, 34, 23, 6];
    const max = a.reduce((pre, cur) => (pre > cur ? pre : cur));
    console.log(max);

    const objArr = [{ name: "老大" }, { name: "老二" }, { name: "老三" }];
    const res = objArr.reduce((pre, cur, index, arr) => {
      if (index === 0) {
        return cur.name;
      } else if (index === arr.length - 1) {
        return pre + "和" + cur.name;
      } else {
        return pre + "、" + cur.name;
      }
    }, "");
    console.log(res);

    // 求字符串中字母出现的次数
    const str = "sfhjasfjgfasjuwqrqadqeiqsajsdaiwqdaklldflas-cmxzmnha";
    const res1 = str.split("").reduce((pre, cur) => {
      pre[cur] ? pre[cur]++ : (pre[cur] = 1);
      return pre;
    }, {});
    console.log(res1);
    // 数组转数组
    var arr1 = [2, 3, 4, 5, 6]; // 每个值的平方
    const res2 = arr1.reduce((pre, cur) => {
      pre.push(cur * cur);
      return pre;
    }, []);
    console.log(res2);

    // 数组转对象
    var streams = [
      { name: "技术", id: 1 },
      { name: "设计", id: 2 },
    ];

    var obj = streams.reduce((pre, cur) => {
      pre[cur.id] = cur;
      return pre;
    }, {});
    console.log(obj);

    // 多维的叠加执行操作
    var result1 = [
      { subject: "math", score: 88 },
      { subject: "chinese", score: 95 },
      { subject: "english", score: 80 },
    ];
    var dis = {
      math: 0.5,
      chinese: 0.3,
      english: 0.2,
    };

    const res3 = result1.reduce((pre, cur) => dis[cur.subject] * cur.score + pre, 0)
    console.log(res3);
    
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.logo {
  width: 400px;
  height: 600px;
}
</style>
