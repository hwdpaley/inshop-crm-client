<template>
  <is-main-template
    title="company_list"
    route-add="CompanyCreate"
    entity="company"
  >
    <api-table
      entity="Company"
      route="companies"
      path="company"
      :filterable="filterable"
      :custom-filters="customFilters"
      :sortable="sortable"
      :columns="columns"
      :templates="templates"
    >
      <template slot="filter__labels.id">
        <labels-filter />
      </template>
    </api-table>
  </is-main-template>
</template>

<script>
import ApiTable from '../../components/ApiTable'
import columnContacts from '../../table/ColumnContacts'
import columnLabels from '../../table/ColumnLabels'
import columnAddressCountry from '../../table/ColumnAddressCountry'
import columnAddressPostCode from '../../table/ColumnAddressPostCode'
import LabelsFilter from '../../components/filters/LabelsFilter'
import columnIsActive from '../../table/ColumnIsActive'

export default {
  components: { LabelsFilter, ApiTable },
  data() {
    return {
      columns: [
        'id',
        'name',
        'contacts.value',
        'contactPerson',
        'addresses.country.name',
        'addresses.city',
        'addresses.postCode',
        'labels.id',
        'isActive',
        'columnCreatedAt',
        'columnUpdatedAt',
        'actions'
      ],
      filterable: [
        'id',
        'name',
        'contacts.value',
        'contactPerson',
        'addresses.country.name',
        'addresses.city',
        'addresses.postCode',
        'isActive',
        'columnCreatedAt',
        'columnUpdatedAt'
      ],
      customFilters: ['labels.id'],
      sortable: [
        'id',
        'name',
        'contactPerson',
        'isActive',
        'columnCreatedAt',
        'columnUpdatedAt'
      ],
      templates: {
        'contacts.value': columnContacts,
        'addresses.country.name': columnAddressCountry,
        'addresses.postCode': columnAddressPostCode,
        'labels.id': columnLabels,
        isActive: columnIsActive
      }
    }
  }
}
</script>
