<template>
<div id="container">
  <div class="serach">
<input id="target" type="text" class="serach-input" placeholder="输入IP">
    <el-button id="btn" type="primary" @click="initData" icon="el-icon-search">查询</el-button>
  </div>
<table id="table">
  <tr>
    <th>IP</th>
    <th>SERVICE</th>
    <th>PORT</th>
    <th>OS</th>
  </tr>
</table>
</div>
</template>

<script>
export default {
name: "pythonflask",
data(){
  return{
    IP:'',
    PORT:[],
    SERVICE:[],
    OS:'',
    len :0
  }
},
methods:{
  initData(){
    this.IP = document.getElementById('target').value
    this.$ajax.get('http://127.0.0.1:5000/?name='+this.IP).then(res=> {
      this.IP=res.data.IP
      this.PORT=res.data.PORT
      this.SERVICE=res.data.SERVICE
      this.OS =res.data.OS
      this.len =this.PORT.length
      for (let i=0;i<this.len;i++){
        let tableObj=document.getElementById('table')
        let tr=document.createElement('tr')
        let tdIP=document.createElement('td')
        tdIP.innerHTML=this.IP
        tr.appendChild(tdIP)
        let tdSERVICE=document.createElement('td')
        tdSERVICE.innerHTML=this.SERVICE[i]
        tr.appendChild(tdSERVICE)
        let tdPORT=document.createElement('td')
        tdPORT.innerHTML= this.PORT[i]
        tr.appendChild(tdPORT)
        let tdOS=document.createElement('td')
        tdOS.innerHTML=this.OS
        tr.appendChild(tdOS)
        tableObj.appendChild(tr)
      }
    })
  },

}
}
</script>

<style scoped>
table{
  width: 80%;
  border: 1px solid #ccc;
  box-shadow: 0 1px 1px #ccc;
  font:15px 'trebuchet MS';
  margin: 50px 100px 50px 100px;
}
.serach{
  width: 30%;
  margin-left: 100px;
  display: flex;
}
#btn{

}
#target{
width: 250px;
}


</style>