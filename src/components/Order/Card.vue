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


        <b-row>
            <b-col>
                <b-form-input v-model="zip" placeholder="Zip"></b-form-input>
            </b-col>
            <b-col>
                <b-form-input v-model="city" placeholder="City"></b-form-input>
            </b-col>
        </b-row>  

    </b-card> 
    
</template>

<script>
export default {
  data : () => ({}),

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