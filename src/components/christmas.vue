/* 
Author : Faridho
Created: December 24, 2018 
*/
<template>
  <div class="row">
        <div class="col-lg-12">
            <div class="card">
                <div class="card-body">
                    {{ getGreetings() }}
                </div>
            </div>
      </div>
  </div>
</template>

<script>
export default {
  name: 'ChristmasNewYearComponent',
  data () {
    return {
      christmas: 'SELAMAT HARI NATAL',
      newYear: 'SELAMAT TAHUN BARU 2019'
    }
  },

  method: {
      getGreetings: function() {
          return this.christmas + ' & ' + this.newYear;
      }
  }
}
</script>
