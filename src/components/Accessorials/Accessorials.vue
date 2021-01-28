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
            <b-col cols="1.0"  v-for="item in accesorials" v-bind:key="item" style="margin-right: 40px;">

                <b-form-checkbox :value="item" >{{item}}</b-form-checkbox>

            </b-col>
        </b-row> 

    </b-card> 
    
</template>

<script>
export default {
  data : () => ({
      accesorials: ['Hazmat', 'Bonded', 'Tarps', 'Airport Delivery TSA', 'Oversize/Overweight Permits', 'Escorts', 'Team Drivers', 'Non Stackable']
  }),

  props: {
    title: String,
    color: String,
    zip: String,
    city: String,
  }
}
</script>

<style scoped>

</style>