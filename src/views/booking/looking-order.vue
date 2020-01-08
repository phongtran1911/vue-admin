<template>
  <div class="app-container">
    <div class="filter-container">
      <el-input v-model="listQuery.OrderCode" placeholder="Mã vận đơn" style="width: 40%" class="filter-item" />
      <el-input v-model="listQuery.PhoneName" placeholder="Tên/SĐT người nhận" style="width: 40%; margin-left: 2%;" class="filter-item" />
    </div>
    <div class="filter-container">
      <el-select v-model="listQuery.Status" placeholder="Tình trạng giao hàng" clearable class="filter-item" style="width: 40%">
        <el-option v-for="item in statusTypeOptions" :key="item.key" :label="item.display_name+'('+item.key+')'" :value="item.key" />
      </el-select>
      <el-select v-model="listQuery.Packge" placeholder="Gói cước" clearable class="filter-item" style="width: 40%; margin-left: 2%;">
        <el-option v-for="item in packagesTypeOptions" :key="item.key" :label="item.display_name+'('+item.key+')'" :value="item.key" />
      </el-select>

    </div>
    <div class="filter-container">
      <el-date-picker v-model="listQuery.fromDate" type="datetime" format="yyyy-MM-dd HH:mm:ss" placeholder="Từ ngày" style="width: 40%" />
      <el-date-picker v-model="listQuery.toDate" type="datetime" format="yyyy-MM-dd HH:mm:ss" placeholder="Đến ngày" style="width: 40%; margin-left: 2%;" />
      <el-button v-waves class="filter-item" type="primary" icon="el-icon-search" style="margin-left: 2%;">
        Search
      </el-button>
    </div>
  </div>
</template>

<script>
import waves from '@/directive/waves' // waves directive
const statusTypeOptions = [
  { key: 'CN', display_name: 'China' },
  { key: 'US', display_name: 'USA' },
  { key: 'JP', display_name: 'Japan' },
  { key: 'EU', display_name: 'Eurozone' }
]
const packagesTypeOptions = [
  { key: 'CN', display_name: 'abc' },
  { key: 'US', display_name: 'def' },
  { key: 'JP', display_name: 'vvv' },
  { key: 'EU', display_name: 'eee' }
]
export default {
  name: 'LookingOrder',
  directives: { waves },
  data() {
    return {
      tableKey: 0,
      list: null,
      total: 0,
      listLoading: true,
      listQuery: {
        page: 1,
        limit: 20,
        Packge: undefined,
        Status: undefined,
        OrderCode: undefined,
        PhoneName: undefined,
        fromDate: undefined,
        toDate: undefined
      },
      packagesTypeOptions,
      statusTypeOptions,
      downloadLoading: false
    }
  }
}
</script>
