<template>

    <b-card header-tag="header" header-bg-variant="dark" class="text-center" style="max-width: 100%;" >
        <template #header>
            <h6 class="mb-0" style="color: white"><b>
                {{title}} 
                <svg version="1.1" xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 120 120">
                    <circle cx="60" cy="60" r="50" :fill="color" />
                </svg>
            </b></h6>
        </template>


        <b-row >
            <b-col cols="1.0"  v-for="item in accesorials" v-bind:key="item.name" style="margin-right: 40px;">
                <b-form-checkbox-group
                    id="checkbox-group-2"
                    v-model="selected"
                    name="flavour-2"
                >

                <b-form-checkbox :v-model="item.name" :value="item.name" :id="item.name">{{item.name}}</b-form-checkbox>

                </b-form-checkbox-group>
            </b-col>
        </b-row> 

    </b-card> 
    
</template>

<script>
export default {
  data : () => ({
      selected: [],
      accesorials: [{select: false, name:'Hazmat'}, {select: false, name:'Bonded'}, {select: false, name:'Tarps'}, {select: false, name:'Airport Delivery TSA'}, {select: false, name:'Oversize/Overweight Permits'}, {select: false, name:'Escorts'}, {select: false, name:'Team Drivers'}, {select: false, name:'Non Stackable'}]
  }),

  props: {
    title: String,
    color: String,
    zip: String,
    city: String,
    accessorials_props: Array
  },

  created: function () { 

      this.selected = this.accessorials_props;

  }
}
</script>

<style scoped>

</style>