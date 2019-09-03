<template>
  <div class="tableComp" v-if="loadStatus">
   <el-table
      :data="jsonFile"
      :span-method="arraySpanMethod"
      border
      style="width: 100%">
      <el-table-column
        prop="partID"
        label="ID"
        width="80">
      </el-table-column>
      <el-table-column
        prop="parttype"
        label="parttype">
      </el-table-column>
      <el-table-column
        prop="InovoPN"
        sortable
        label="InovoPN">
      </el-table-column>
      <el-table-column
        prop="Description"
        sortable
        label="Description">
      </el-table-column>
      <el-table-column
        prop="Manufacturer"
        sortable
        label="Manufacturer">
      </el-table-column>        
      <el-table-column
        prop="MPN"
        sortable
        label="MPN">
      </el-table-column>
      <el-table-column
        prop="IntLib"
        sortable
        label="IntLib">
      </el-table-column>
      <el-table-column
        prop="createdDate"
        sortable
        label="createdDate">
      </el-table-column>
      <el-table-column
        prop="createdDate"
        sortable
        label="createdDate">
      </el-table-column>
      <el-table-column
        prop="createdBy"
        sortable
        label="createdBy">
      </el-table-column>
    </el-table>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'tableComp',
  data() {
    return {
      title: "Table Component",
      jsonFile: [],
      loadStatus: false
    }
  },
  methods: {
    getJSONfromUrl () {
    // const baseURI = 'https://api.coindesk.com/v1/bpi/currentprice.json'
    const baseURI = 'http://127.0.0.1:8080/getParts.json'
      var vm = this.loadStatus
      return axios.get(baseURI)
            .then((response) => {
                this.jsonFile = response.data;
            })
            .catch(function (error) {
              console.log(error);
            })
            .finally(function () {
            });
    },
    arraySpanMethod ({ row, column, rowIndex, columnIndex }) {
      if (rowIndex % 2 === 0) {
        if (columnIndex === 0) {
          return [1, 2]
        } else if (columnIndex === 1) {
          return [0, 0]
        }
      }
    },
    objectSpanMethod ({ row, column, rowIndex, columnIndex }) {
      if (columnIndex === 0) {
        if (rowIndex % 2 === 0) {
          return {
            rowspan: 2,
            colspan: 1
          };
        } else {
          return {
            rowspan: 0,
            colspan: 0
          }
        }
      }
    }
  },
  mounted () {
    this.getJSONfromUrl()
    var self = this;
            setTimeout( function () {
                self.loadStatus = true
            }, 200);
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>

</style>
