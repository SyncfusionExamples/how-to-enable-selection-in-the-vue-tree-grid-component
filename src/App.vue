<template>
  <ejs-button :onclick="btnClick" cssClass="e-btn">Selection API</ejs-button>
  <ejs-treegrid :dataSource="data" ref="treegridObj"
    childMapping="subtasks"
    :treeColumnIndex="2"
    :selectionSettings="selectionOptions" 
    :selectedRowIndex="2"
    :height='400' 
    :allowPaging='true' 
    :pageSettings='pageSettings'>
    <e-columns>
      <e-column type="Checkbox" width="50"></e-column>
      <e-column field='taskID' headerText='Task ID' width='80' textAlign='Right'></e-column>
      <e-column field='taskName' headerText='Task Name' width='190'></e-column>
      <e-column field='startDate' headerText='Start Date' width='100' format="yMd" textAlign='Right'></e-column>
      <e-column field='duration' headerText='Duration' width='90' textAlign='Right'></e-column>
      <e-column field='progress' headerText='Progress' width='90' textAlign='Right'></e-column>
    </e-columns>
  </ejs-treegrid>
</template>

<script>
import { TreeGridComponent, ColumnsDirective, ColumnDirective, Page} from "@syncfusion/ej2-vue-treegrid";
import { ButtonComponent} from '@syncfusion/ej2-vue-buttons';
import {sampleData} from './data.js';

export default{
  name: 'App',
  components: {
    'ejs-treegrid': TreeGridComponent,
    'e-columns': ColumnsDirective,
    'e-column': ColumnDirective,
    'ejs-button': ButtonComponent
  },
  data: () => {
    return {
      data: sampleData,
      // mode: "Cell", cellSelectionMode: "Box"
      selectionOptions: {type: "Multiple", checkboxOnly: false, checkboxMode: "ResetOnRowClick", enableToggle: false},
      pageSettings: { pageSize: 12 }
    }
  },
  methods: {
    btnClick: function(){
      let treegrid = this.$refs.treegridObj.ej2Instances;
      treegrid.selectRows([5,6,7]);
      //treegrid.clearSelection(); //To clear the selection
    }
  },
  provide:{
    treegrid:[Page]
  }
}
</script>

<style>
  @import "../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-calendars/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-dropdowns/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-inputs/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-navigations/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-popups/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-treegrid/styles/material.css";

  .e-btn{
    margin: 1%;
  }
</style>
