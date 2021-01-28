<template>
    <div style="padding: 30px;">
        <b-row> 
            <b-col cols="6">
                <div> 
                    <Card title="Pick-Up" color="#06CB00" :city="city_from" :zip="zip_from"/>
                </div>
            </b-col>
            <b-col cols="6">
                <div> 
                    <Card title="Delivery" color="#FF0808" :city="city_to" :zip="zip_to"/>
                </div>
            </b-col>
        </b-row> 

        <b-row style="margin-top:30px"> 
            <b-col cols="12">
                <div> 
                    <Accessorial title="Accesorials" :accessorials_props="accesorials" color="#F1B82E"/>
                </div>
            </b-col>
        </b-row> 

        <b-row style="margin-top:30px"> 
            <b-col cols="12">
                <div> 
                    <Table :items_prop="items_table" />
                </div>
            </b-col>
        </b-row>
    </div> 
</template>

<script>
import Card from '../../components/Order/Card'
import Accessorial from '../../components/Accessorials/Accessorials'
import Table from '../../components/Table/Table'
import data from "../../data/info.json";

export default {
  data : () => ({
    zip_from: "",
    city_from: "",  
    zip_to: "",
    city_to:"",
    accesorials:[],
    items_table:[]
  }),

  components: {
    Card,
    Accessorial,
    Table
  },

  created: function () { 
    this.zip_from = data.hauls[0].zip_from;
    this.city_from = data.hauls[0].city_from;
    this.zip_to = data.hauls[0].zip_to;
    this.city_to = data.hauls[0].city_to;

    this.accesorials = data.hauls[0].accessorials;

    this.items_table = data.hauls[0].commodity.map(item => {
        var com = {};
        com['select'] = false;
        com['hu_count'] = item['hu_count'];
        com['dimensions'] = item['dimensions'];
        com['weight'] = item['weight'];

        return com;
    });
  }
}
</script>

<style scoped>

</style>