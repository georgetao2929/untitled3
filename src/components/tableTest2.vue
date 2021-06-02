<template>
  <div class="container">
    <!-- Watermark container -->
    <div class="container__wrapper">
      <!-- The watermark -->
      <div class="container__watermark">
        Draftft
      </div>
    </div>
    <el-button @click="addData">addData</el-button>
    <el-button type="primary" style="background-color: #0086b3" @click="exportExcel">导出</el-button>
    <div>
      <el-table
          class="table"
          :data="tableData"
          style="width: 100%"
          max-height="500">
        <el-table-column
            prop="date"
            label="日期"
            width="150">
        </el-table-column>
        <el-table-column label="配送信息">
          <el-table-column
              prop="name"
              label="姓名"
              width="120">
          </el-table-column>
          <el-table-column label="地址">
            <el-table-column
                prop="province"
                label="省份"
                width="120">
            </el-table-column>
            <el-table-column
                prop="city"
                label="市区"
                width="120">
            </el-table-column>
            <el-table-column
                prop="address"
                label="地址"
                width="300">
            </el-table-column>
            <el-table-column
                prop="zip"
                label="邮编"
                width="120">
            </el-table-column>
          </el-table-column>
        </el-table-column>
      </el-table>
    </div>

  </div>

</template>

<script>
import FileSaver from 'file-saver'
import XLSX from 'xlsx'
export default {
  data() {
    return {
      tableData: [{
        date: '2016-05-03',
        name: '王小虎',
        province: '上海',
        city: '普陀区',
        address: '上海市普陀区金沙江路 1518 弄',
        zip: 200333
      }, {
        date: '2016-05-02',
        name: '王小虎',
        province: '上海',
        city: '普陀区',
        address: '上海市普陀区金沙江路 1518 弄',
        zip: 200333
      }, {
        date: '2016-05-04',
        name: '王小虎',
        province: '上海',
        city: '普陀区',
        address: '上海市普陀区金沙江路 1518 弄',
        zip: 200333
      }, {
        date: '2016-05-01',
        name: '王小虎',
        province: '上海',
        city: '普陀区',
        address: '上海市普陀区金沙江路 1518 弄',
        zip: 200333
      }, {
        date: '2016-05-08',
        name: '王小虎',
        province: '上海',
        city: '普陀区',
        address: '上海市普陀区金沙江路 1518 弄',
        zip: 200333
      }, {
        date: '2016-05-06',
        name: '王小虎',
        province: '上海',
        city: '普陀区',
        address: '上海市普陀区金沙江路 1518 弄',
        zip: 200333
      }, {
        date: '2016-05-07',
        name: '王小虎',
        province: '上海',
        city: '普陀区',
        address: '上海市普陀区金沙江路 1518 弄',
        zip: 200333
      }]
    }
  },
  mounted() {
    //this.addData()
  },
  methods:{
    exportExcel () {
      /* generate workbook object from table */
      //table的class名
      var wb = XLSX.utils.table_to_book(document.querySelector('.table'))
      /* get binary string as output */
      var wbout = XLSX.write(wb, { bookType: 'xlsx', bookSST: true, type: 'array' })
      try {
        FileSaver.saveAs(new Blob([wbout], { type: 'application/octet-stream' }), 'order.xlsx')
      } catch (e) { if (typeof console !== 'undefined') console.log(e, wbout) }
      return wbout
    },
    addData(){
      var i
      for(i=0;i<2000;i++)
      {
        this.tableData.push({
          date: '2016-05-07',
          name: '王小虎',
          province: '上海',
          city: '普陀区',
          address: '上海市普陀区金沙江路 1518 弄',
          zip: 200333
        })
      }
    }
  }
}
</script>

<style type="text/css">
.table{
  width: 100%;
  height: 800px;
}

.container {
  /* Used to position the watermark */
  position: relative;
}

.container__wrapper {
  /* Center the content */
  align-items: center;
  display: flex;
  justify-content: center;

  /* Absolute position */
  left: 40%;
  position: absolute;
  top: 50%;

  /* Take full size */
  height: 1%;
  width: 1%;

  z-index: 1;

  /*虽然在最上层，但是不影响下层事件触发*/
  pointer-events: none;
}

.container__watermark {
  /* Text color */
  color: rgba(0, 0, 0, 0.1);

  /* Text styles */
  font-size: 15rem;
  font-weight: bold;
  text-transform: uppercase;

  /* Rotate the text */
  transform: rotate(0deg);

  /* Disable the selection */
  user-select: none;

}

</style>
