<template>
  <div class="app-container">
    <DxDataGrid
      :data-source="dataSource"
      :columns="columns"
      :show-borders="true"
    >
      <DxEditing
        :allow-adding="true"
        :allow-updating="true"
        :allow-deleting="true"
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
      columns: ['Id', 'UserName', 'LastName', 'FirstName', 'Email', 'Male', 'Birthday', 'FullAddress']
    }
  }
}
</script>
