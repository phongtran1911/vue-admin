<template>
  <div class="app-container">
    <div class="filter-container">
      <el-input v-model="listQuery.OrderCode" placeholder="Mã vận đơn" style="width: 40%" class="filter-item" />
      <el-input v-model="listQuery.PhoneName" placeholder="Tên/SĐT người nhận" style="width: 40%; margin-left: 2%;" class="filter-item" />
    </div>
    <div class="filter-container">
      <el-select v-model="listQuery.Status" :multiple="true" placeholder="Tình trạng giao hàng" clearable class="filter-item" style="width: 40%">
        <el-option v-for="item in statusTypeOptions" :key="item.key" :label="item.display_name" :value="item.key" />
      </el-select>
      <el-select v-model="listQuery.Package" :multiple="true" placeholder="Gói cước" clearable class="filter-item" style="width: 40%; margin-left: 2%;">
        <el-option v-for="item in packagesTypeOptions" :key="item.key" :label="item.display_name" :value="item.key" />
      </el-select>
    </div>
    <div class="filter-container">
      <el-date-picker v-model="listQuery.fromDate" type="datetime" format="yyyy-MM-dd HH:mm:ss" placeholder="Từ ngày" style="width: 40%" />
      <el-date-picker v-model="listQuery.toDate" type="datetime" format="yyyy-MM-dd HH:mm:ss" placeholder="Đến ngày" style="width: 40%; margin-left: 2%;" />
      <el-button v-waves class="filter-item" type="primary" icon="el-icon-search" style="margin-left: 2%;">
        Search
      </el-button>
    </div>
    <DxDataGrid
      :data-source="dataSource"
      :columns="columns"
      :show-borders="true"
    >
      <DxEditing
        :allow-updating="true"
        :allow-deleting="true"
        mode="popup"
      />
    </DxDataGrid>
    <DxPager
      :allowed-page-sizes="pageSizes"
      :show-page-size-selector="true"
    />
    <DxPaging :page-size="10" />
  </div>
</template>

<script>
import waves from '@/directive/waves' // waves directive
import { DxDataGrid, DxPager, DxPaging, DxEditing } from 'devextreme-vue/data-grid'

const statusTypeOptions = [
  { key: 'CN', display_name: 'Chờ giao hàng' },
  { key: 'US', display_name: 'Chờ trả hàng' },
  { key: 'JP', display_name: 'Đang lấy hàng' },
  { key: 'EU', display_name: 'Giao hàng thành công' }
]
const packagesTypeOptions = [
  { key: 'CN', display_name: 'Gói giao nhanh' },
  { key: 'US', display_name: 'Gói tiết kiệm' },
  { key: 'JP', display_name: 'Gói hỏa tốc' },
  { key: 'EU', display_name: 'Gói 4 giờ' }
]
export default {
  name: 'LookingOrder',
  components: {
    DxDataGrid,
    DxPager,
    DxPaging,
    DxEditing },
  directives: { waves },
  filters: {
    statusFilter(status) {
      const statusMap = {
        published: 'success',
        draft: 'info',
        deleted: 'danger'
      }
      return statusMap[status]
    }
  },
  data() {
    return {
      tableKey: 0,
      list: null,
      total: 0,
      listLoading: true,
      listQuery: {
        page: 1,
        limit: 10,
        Package: undefined,
        Status: undefined,
        OrderCode: undefined,
        PhoneName: undefined,
        fromDate: undefined,
        toDate: undefined
      },
      packagesTypeOptions,
      statusTypeOptions,
      downloadLoading: false,
      dataSource: [],
      columns: ['Id', 'UserName', 'LastName', 'FirstName', 'Email', 'Male', 'Birthday', 'FullAddress']
    }
  }
}
</script>
