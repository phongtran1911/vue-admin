<template>
  <div class="tab-container">
    <DxTabPanel
      :height="260"
      :data-source="companies"
      :selected-index.sync="selectedIndex"
      :loop="loop"
      :animation-enabled="animationEnabled"
      :swipe-enabled="swipeEnabled"
    >
      <template #title="{ data: company }">
        <span>{{ company.CompanyName }}</span>
      </template>
      <template #item="{ data: company }">
        <div class="tabpanel-item">
          <div>
            <p>
              <b>{{ company.City }}</b>
              (<span>{{ company.State }}</span>)
            </p>
            <p>
              <span>{{ company.Zipcode }}</span>
              <span>{{ company.Address }}</span>
            </p>
          </div>
          <div>
            <p>
              Phone: <b>{{ company.Phone }}</b>
            </p>
            <p>
              Fax: <b>{{ company.Fax }}</b>
            </p>
            <p>
              Website:
              <a
                :href="company.Website"
                target="_blank"
              >
                {{ company.Website }}
              </a>
            </p>
          </div>
        </div>
      </template>
    </DxTabPanel>
  </div>
</template>

<script>
import DxTabPanel from 'devextreme-vue/tab-panel'
const multiViewItems = [{
  'ID': 1,
  'CompanyName': 'SuprMart',
  'Address': '702 SW 8th Street',
  'City': 'Bentonville',
  'State': 'Arkansas',
  'Zipcode': 72716,
  'Phone': '(800) 555-2797',
  'Fax': '(800) 555-2171',
  'Website': 'http://www.nowebsitesupermart.com'
}, {
  'ID': 2,
  'CompanyName': "El'Depot",
  'Address': '2455 Paces Ferry Road NW',
  'City': 'Atlanta',
  'State': 'Georgia',
  'Zipcode': 30339,
  'Phone': '(800) 595-3232',
  'Fax': '(800) 595-3231',
  'Website': 'http://www.nowebsitedepot.com'
}, {
  'ID': 3,
  'CompanyName': 'K&S Music',
  'Address': '1000 Nicllet Mall',
  'City': 'Minneapolis',
  'State': 'Minnesota',
  'Zipcode': 55403,
  'Phone': '(612) 304-6073',
  'Fax': '(612) 304-6074',
  'Website': 'http://www.nowebsitemusic.com'
}, {
  'ID': 4,
  'CompanyName': 'Tom Club',
  'Address': '999 Lake Drive',
  'City': 'Issaquah',
  'State': 'Washington',
  'Zipcode': 98027,
  'Phone': '(800) 955-2292',
  'Fax': '(800) 955-2293',
  'Website': 'http://www.nowebsitetomsclub.com'
}]
export default {
  name: 'ManageOrder',
  components: { DxTabPanel },
  data() {
    return {
      selectedIndex: 0,
      loop: false,
      animationEnabled: true,
      swipeEnabled: true,
      companies: multiViewItems
    }
  }
}
</script>

<style scoped>
  .tab-container {
    margin: 30px;
  }
  .tabpanel-item {
    height: 200px;
    user-select: none;
    padding-left: 25px;
    padding-top: 55px;
}

.mobile .tabpanel-item {
    padding-top: 10px;
}

.tabpanel-item  > div {
    float: left;
    padding: 0 85px 10px 10px
}

.tabpanel-item  p {
    font-size: 16px;
    margin: 0;
}

.item-box {
    font-size: 16px;
    margin: 15px 0 45px 10px;
}

.options {
    padding: 20px;
    background-color: rgba(191, 191, 191, 0.15);
    margin-top: 20px;
}

.caption {
    font-size: 18px;
    font-weight: 500;
}

.option {
    margin-top: 10px;
}
</style>
