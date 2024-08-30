<template>
  <div style="margin:20px;">
    <!-- <h1 style="text-align:center">CRUD confguration</h1>
    <v-layout row wrap>
      <v-flex xs12 md6 lg3 px-5>
        <v-text-field label="Details title" v-model="detailsTitle"></v-text-field>
        <v-select label="Delete mode" :items="['none', 'soft', 'hard', 'both', 'filter']"
          v-model="deleteMode"></v-select>
        <v-switch color="green" label="Refresh button" v-model="refreshButton"></v-switch>
      </v-flex>

      <v-flex xs12 md6 lg3 px-5>
        <v-switch color="green" label="Export button" v-model="exportButton"></v-switch>
        <v-switch color="green" label="Field filters" v-model="fieldFilters"></v-switch>
        <v-switch color="green" label="Main filter" v-model="mainFilter"></v-switch>
      </v-flex>

      <v-flex xs12 md6 lg3 px-5>
        <v-switch color="green" label="Create mode" v-model="createMode"></v-switch>
        <v-switch color="green" label="Edit mode" v-model="editMode"></v-switch>
        <v-switch color="green" label="Edit button" v-model="editButton"></v-switch>
      </v-flex>

      <v-flex xs12 md6 lg3 px-5>
        <v-switch color="green" label="Select many mode" v-model="selectManyMode"></v-switch>
        <v-switch color="green" label="Update many mode" v-model="updateManyMode"></v-switch>
        <v-switch color="green" label="Remove many mode" v-model="removeManyMode"></v-switch>
      </v-flex>
    </v-layout> -->
    <h1 style="text-align:center">SAP Event Broker</h1>
    <crud
      :prefix="prefix"
      :path="path"
      :page-title="pageTitle"
      :fields-info="fieldsInfo"
      :details-title="detailsTitle"
      :delete-mode="deleteMode"
      :refresh-button="refreshButton"
      :export-button="exportButton"
      :field-filters="fieldFilters"
      :main-filter="mainFilter"
      :create-mode="createMode"
      :edit-mode="editMode"
      :edit-button="editButton"
      :select-many-mode="selectManyMode"
      :update-many-mode="updateManyMode"
      :remove-many-mode="removeManyMode"
    >
    </crud>
    <alert-box></alert-box>
  </div>
</template>

<script>
import Crud from '@/utils/crud/components/Crud.vue'
import AlertBox from '@/utils/app/components/AlertBox.vue'

export default {
  data () {
    return {
      selectManyMode: false,
      updateManyMode: false,
      removeManyMode: false,
      exportButton: true,
      fieldFilters: true,
      deleteMode: false,
      editMode: false,
      createMode: false,
      prefix: 'demo',
      path: 'tasks',
      searchField: 'FID',
      pageTitle: 'task.demo',
      /* paths: {
        i: 'http://localhost:8000/api/demo/tasks',
        sh: 'http://localhost:8000/api/demo/tasks',
        server: 'http://localhost:8000/api/demo/tasks',
      }, */
    }
  },
  created () {
    this.detailsTitle = this.$t('detailsTitle')
  },
  computed: {
    fieldsInfo () {
      return [
        {
          text: this.$t('fields.FID'),
          name: 'FID',
          column: 'FID',
          type: 'input',
          required: true,
          details: true,
          sortable: false,
        },
        {
          type: 'input',
          column: 'RESTROOMS',
          text: this.$t('fields.RESTROOMS'),
          name: 'RESTROOMS',
          required: true,
          details: true,
          sortable: false,
        },
        {
          type: 'input',
          column: 'PICNIC',
          text: this.$t('fields.PICNIC'),
          name: 'PICNIC',
          required: false,
          sortable: false,
        },
        {
          type: 'input',
          column: 'FISHING',
          text: this.$t('fields.FISHING'),
          name: 'FISHING',
          required: false,
          sortable: false,
        },
        {
          type: 'input',
          column: 'AKA',
          text: this.$t('fields.AKA'),
          name: 'AKA',
          required: false,
          sortable: false,
        },
        {
          type: 'input',
          column: 'AccessType',
          text: this.$t('fields.AccessType'),
          name: 'AccessType',
          required: false,
          sortable: false,
        },
        {
          type: 'input',
          column: 'AccessID',
          text: this.$t('fields.AccessID'),
          name: 'AccessID',
          required: false,
          sortable: false,
        },
        {
          type: 'input',
          column: 'Class',
          text: this.$t('fields.Class'),
          name: 'Class',
          required: false,
          sortable: false,
        },
        {
          type: 'input',
          column: 'Address',
          text: this.$t('fields.Address'),
          name: 'Address',
          required: false,
          sortable: false,
        },
        {
          type: 'input',
          column: 'Fee',
          text: this.$t('fields.Fee'),
          name: 'Fee',
          required: false,
          sortable: false,
        },
        {
          type: 'input',
          column: 'BikeRack',
          text: this.$t('fields.BikeRack'),
          name: 'BikeRack',
          required: true,
          sortable: false,
        },
        {
          type: 'input',
          column: 'BikeTrail',
          text: this.$t('fields.BikeTrail'),
          name: 'BikeTrail',
          required: true,
          sortable: false,
        },
        {
          type: 'input',
          column: 'DogTube',
          text: this.$t('fields.DogTube'),
          name: 'DogTube',
          required: false,
          sortable: false,
        },
        {
          type: 'input',
          column: 'DogTube',
          text: this.$t('fields.DogTube'),
          name: 'DogTube',
          required: false,
          sortable: false,
        },
        {
          type: 'input',
          column: 'Grills',
          text: this.$t('fields.Grills'),
          name: 'Grills',
          required: false,
          sortable: false,
        },
        {
          type: 'input',
          column: 'TrashCans',
          text: this.$t('fields.TrashCans'),
          name: 'TrashCans',
          required: false,
          sortable: false,
        },
        {
          type: 'input',
          column: 'ParkSpaces',
          text: this.$t('fields.ParkSpaces'),
          name: 'ParkSpaces',
          required: false,
          sortable: false,
        },
        {
          type: 'input',
          column: 'ADAsurface',
          text: this.$t('fields.ADAsurface'),
          name: 'ADAsurface',
          required: false,
          sortable: false,
        },
        {
          type: 'input',
          column: 'ADAtoilet',
          text: this.$t('fields.ADAtoilet'),
          name: 'ADAtoilet',
          required: false,
          sortable: false,
        },
        {
          type: 'input',
          column: 'ADAfishing',
          text: this.$t('fields.ADAfishing'),
          name: 'ADAfishing',
          required: false,
          sortable: false,
        },
        {
          type: 'input',
          column: 'ADAcamping',
          text: this.$t('fields.ADAcamping'),
          name: 'ADAcamping',
          required: false,
          sortable: false,
        },
        {
          type: 'input',
          column: 'ADApicnic',
          text: this.$t('fields.ADApicnic'),
          name: 'ADApicnic',
          required: false,
          sortable: false,
        },
        {
          type: 'input',
          column: 'ADAtrail',
          text: this.$t('fields.ADAtrail'),
          name: 'ADAtrail',
          required: false,
          sortable: false,
        },
        {
          type: 'input',
          column: 'ADAfacilit',
          text: this.$t('fields.ADAfacilit'),
          name: 'ADAfacilit',
          required: false,
          sortable: false,
        },
        {
          type: 'input',
          column: 'ADAfacName',
          text: this.$t('fields.ADAfacName'),
          name: 'ADAfacName',
          required: false,
          sortable: false,
        },
        {
          type: 'input',
          column: 'HorseTrail',
          text: this.$t('fields.HorseTrail'),
          name: 'HorseTrail',
          required: false,
          sortable: false,
        },
        {
          type: 'input',
          column: 'DateFrom',
          text: this.$t('fields.DateFrom'),
          name: 'DateFrom',
          required: false,
          sortable: false,
        },
        {
          type: 'input',
          column: 'DateTo',
          text: this.$t('fields.DateTo'),
          name: 'DateTo',
          required: false,
          sortable: false,
        },
        {
          type: 'input',
          column: 'RecycleBin',
          text: this.$t('fields.RecycleBin'),
          name: 'RecycleBin',
          required: false,
          sortable: false,
        },
        {
          type: 'input',
          column: 'AccessName',
          text: this.$t('fields.AccessName'),
          name: 'AccessName',
          required: false,
          sortable: false,
        },
        {
          type: 'input',
          column: 'DogCompost',
          text: this.$t('fields.DogCompost'),
          name: 'DogCompost',
          required: false,
          sortable: false,
        },
      ]
    },
  },
  components: {
    Crud,
    AlertBox,
  },
  i18n: {
    messages: {
      en: {
        detailsTitle: 'Task',
        fields: {
          FID: 'FID',
          RESTROOMS: 'RESTROOMS',
          PICNIC: 'PICNIC',
          FISHING: 'FISHING',
          AKA: 'AKA',
          AccessType: 'AccessType',
          AccessID: 'AccessID',
          Class: 'Class',
          Address: 'Address',
          Fee: 'Fee',
          BikeRack: 'BikeRack',
          BikeTrail: 'BikeTrail',
          DogTube: 'DogTube',
          Grills: 'Grills',
          TrashCans: 'TrashCans',
          ParkSpaces: 'ParkSpaces',
          ADAsurface: 'Surface',
          ADAtoile: 'Toile',
          ADAfishing: 'Fishing',
          ADAcamping: 'Camping',
          ADApicnic: 'Picnic',
          ADAtrail: 'Trail',
          ADAparking: 'Parking',
          ADAfacilit: 'Facilit',
          ADAfacName: 'FacName',
          HorseTrail: 'HorseTrail',
          DateFrom: 'DateFrom',
          DateTo: 'DateTo',
          RecycleBin: 'RecycleBin',
          DogCompost: 'DogCompost',
          AccessName: 'AccessName',
          ADAtoilet: 'Toilet',
        },
      },
    },
  },
}

</script>
