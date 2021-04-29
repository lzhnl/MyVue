<template>
  <div class="hello">
    <h1>IP记录</h1>
    <el-table
        :data="tableData"
        border
        style="width: 100%">
      <el-table-column
          fixed
          prop="ip"
          label="IP"
          width="150">
      </el-table-column>
      <el-table-column
          prop="service"
          label="SERVICE"
          width="120">
      </el-table-column>
      <el-table-column
          prop="port"
          label="PORT"
          width="120">
      </el-table-column>
      <el-table-column
          prop="state"
          label="STATE"
          width="120">
      </el-table-column>

      <el-table-column
          prop="os"
          label="OS"
          width="120">
      </el-table-column>
      <el-table-column
          fixed="right"
          label="操作"
          >
        <template slot-scope="scope">
          <el-button @click="handleClick(scope.row)" type="text" size="small">查看</el-button>
          <el-button type="text" size="small">编辑</el-button>
        </template>
      </el-table-column>
    </el-table>
  </div>
</template>
  <script>
export default {
  methods:{
    handleClick(row) {
      console.log(row);}

  },
  name: 'HelloWorld',



  props: {
    msg: String
  },
  data() {
    return {
      tableData: [{
        ip:'10.12.5.186',
        port: '25/tcp',
        service: 'smtp',
        state: 'open',
        os: 'windows',

      }, {
        ip:'10.12.5.186',
        port: '25/tcp',
        service: 'smtp',
        state: 'open',
        os: 'windows',

      }, {
        ip:'10.12.5.186',
        port: '25/tcp',
        service: 'smtp',
        state: 'open',
        os: 'windows',
      }, {
        ip:'10.12.5.186',
        port: '25/tcp',
        service: 'smtp',
        state: 'open',
        os: 'windows',
      },{
        ip:'10.12.5.186',
        port: '25/tcp',
        service: 'smtp',
        state: 'open',
        os: 'windows',
      }
      ]
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.hello{
  margin: 0 400px 100px 400px;
  padding: 0 0 0 0;
}
</style>