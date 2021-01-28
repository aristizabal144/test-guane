<template>
    <b-row>

        <b-col cols="9">

            <b-col cols="12">
                <div style="background-color: #343a40; height: 55px ; border-top-left-radius: 3px; border-top-right-radius:3px;">
                    <b-button variant="primary" style="margin-right:10px; float: left; margin:10px;" v-on:click="remove()">Delete</b-button>
                </div>
            </b-col>

            <b-col cols="12">
                <b-table striped hover :items="items_prop" bordered style="widht:100%">
                    <template #cell(select)="data">
                        <b-form-checkbox
                        :id="data.index.toString()"
                        :v-model="items_remove"
                        :value="data.select"
                        :unchecked-value="false"
                        @change="select_remove(data)"
                        >
                        </b-form-checkbox>
                    </template>
                </b-table>
            </b-col>

        </b-col>

        <b-col cols="3">

            <div style="background-color: #343a40; height: 155px ; border-radius: 3px;">
                <b-button variant="primary" style="margin-left:10px; float: left;  margin:10px;" v-on:click="addRow()">Add new row</b-button>

                <b-row style="padding:10px">
                    <b-col cols="12" >
                        <b-form-input v-model="data_row.hu_count" placeholder="Hu count" style="float:left"></b-form-input>
                    </b-col>
                    <b-col cols="12" style="margin-top: 10px">
                        <b-form-input v-model="data_row.dimensions" placeholder="Dimensions" style="float:left"></b-form-input>
                    </b-col>
                    <b-col cols="12" style="margin-top: 10px">
                        <b-form-input v-model="data_row.weight" placeholder="Weight" style="float:left"></b-form-input>
                    </b-col>
                </b-row> 
            </div>

        </b-col>
        
    </b-row>
    

</template>

<script>
export default {
  data : () => ({
      data_row: {
          select: false,
          hu_count: "",
          dimensions: "",
          weight: ""
      },

      items_remove:[]
  }),

  methods: {
        addRow(){
          this.items_prop.push(Object.assign({} , this.data_row));
          this.data_row.hu_count = "";
          this.data_row.dimensions = "";
          this.data_row.weight = "";
        },

        select_remove(data){

            var index = this.items_remove.indexOf(data.index);

            if(index == -1){
                this.items_remove.push(data.index);
            }else if(index > -1){
                this.items_remove.splice(index, 1);
            }
        },

        remove(){

            for (let index = 0; index < this.items_remove.length; index++) {
                this.items_prop[this.items_remove[index]] = null;
            }
            this.items_prop = this.items_prop.filter(Boolean);
            this.items_remove= [];
        }
  },

  props: {
      items_prop: Array
  }
}
</script>

<style scoped>

</style>