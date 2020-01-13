<template>
  <div class="app-container">
    <div style="width:45%; float: left;">
      <!-- OrgChart -->
      <!-- general form elements disabled -->
      <div class="box box-warning">
        <div class="box-header with-border">
          <h3 class="box-title">Organization tree</h3>
        </div>
        <!-- /.box-header -->
        <div class="box-body">
          <DxDataGrid
            :data-source="dataSource"
            :columns="columns"
            :show-borders="true"
          >
            <DxSearchPanel
              :visible="true"
              :highlight-case-sensitive="true"
            />
          </DxDataGrid>
          <DxPager
            :allowed-page-sizes="pageSizes"
            :show-page-size-selector="true"
          />
          <DxPaging :page-size="10" />
        </div>
        <!-- /.box-body -->
      </div>
      <!-- /.box -->
    </div>
    <div style="width:45%; float: left;margin-left: 5%;">
      <!-- OrgChart -->
      <!-- general form elements disabled -->
      <div class="box box-warning">
        <div class="box-header with-border">
          <h3 class="box-title">User</h3>
        </div>
        <!-- /.box-header -->
        <div class="box-body">
          <DxDataGrid
            :data-source="dataSource"
            :columns="columns"
            :show-borders="true"
          >
            <DxEditing
              :allow-adding="true"
              mode="popup"
            />
            <DxSearchPanel
              :visible="true"
              :highlight-case-sensitive="true"
            />
          </DxDataGrid>
          <DxPager
            :allowed-page-sizes="pageSizes"
            :show-page-size-selector="true"
          />
          <DxPaging :page-size="10" />
        </div>
        <!-- /.box-body -->
      </div>
      <!-- /.box -->
    </div>
  </div>
</template>
<script>

import { DxDataGrid, DxSearchPanel, DxPager, DxPaging, DxEditing } from 'devextreme-vue/data-grid'

export default {
  components: {
    DxDataGrid,
    DxSearchPanel,
    DxPager,
    DxPaging,
    DxEditing
  },
  data() {
    return {
      dataSource: [],
      columns: ['Name', 'Active']
    }
  }
}
</script>
