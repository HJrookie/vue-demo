```vue
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <!-- import CSS -->
  <link rel="stylesheet" href="https://unpkg.com/element-ui/lib/theme-chalk/index.css">
</head>
<body>
  <div id="app" style="background-color: #fffeff">


    <ul >
      <li v-for="item in humanData" :key="item.id" style="list-style: none;border: 1px solid gray;">
        <div>
          <img :src = "item.avatar_url" style="width: 60px;height:60px;">
          <a :href = "item.url" style="text-decoration:none"> {{item.login}}</a>

        </div>
      </li>
    </ul>
    
    
    <el-button @click="test">Button</el-button>
    
    
    
    
    
    
  </div>
</body>
<!-- import Vue before Element -->
<script src="https://unpkg.com/vue/dist/vue.js"></script>
<!-- import JavaScript -->
<script src="https://unpkg.com/element-ui/lib/index.js"></script>
<script src="https://unpkg.com/axios/dist/axios.min.js"></script>

<script>
  new Vue({
    el: '#app',
    data(){
      return { 
        humanData:[],
      }
    },
    created(){
      let that = this;
      axios.get('https://api.github.com/users')
      .then(function (response) {
        let result = response.data;
        that.humanData.push(...result)
        console.log(result)
      })
      .catch(function (error) {
        console.log(error);
      });
    },
    methods:{
      test(){
        console.log(112)
      }
    }

  })
</script>
</html>
```
