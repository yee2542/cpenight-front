<template>
  <div id="register">
    <div id="register1" v-if="page == 1">
      <Register1 @pageReturn="pageReturn"/>
    </div>
    <div id="register2" v-if="page == 2">
      <Register2 @pageReturn="pageReturn"/>
    </div>
    <div id="register3" v-if="page == 3">
      <Register3 @pageReturn="pageReturn"/>
    </div>
    <div id="register4" v-if="page == 4">
      <Register4 @pageReturn="pageReturn"/>
    </div>
    <div id="register5" v-if="page == 5">
      <Register5 @pageReturn="pageReturn"/>
    </div>
  </div>
</template>

<script>
 import Register1 from "@/components/Register1.vue"
 import Register2 from "@/components/Register2.vue"
 import Register3 from "@/components/Register3.vue"
 import Register4 from "@/components/Register4.vue"
 import Register5 from "@/components/Register5.vue"
export default {
    name: "register",
    components: {
        Register1,
        Register2,
        Register3,
        Register4,
        Register5,
    },
    methods: {
      pageReturn(value){
        this.page = value
      }
    },
    data() {
        return {
            page : 1,           
        }
    },
}
</script>

<style>
  .vs__dropdown-menu{
    max-height: 250px;
  }

  .style-chooser .vs__search::placeholder,
  .style-chooser .vs__dropdown-toggle{
    background: #312F71; 
    border: none;
    font-family: "CloudLight";
    letter-spacing: 1.6px;
    color: #FFFFFF;
    opacity: 1;
    font-size: 18px;
  }

  .vs__searching{
    pointer-events: none;
    z-index: 6;
  }

  .style-chooser .vs__dropdown-menu {
    background: #FFFFFF; 
    border: none;
    font-family: "CloudLight";
    letter-spacing: 1.6px;
    color: #FFFFFF;
    font-size: 18px;
  }

  .vs__selected{
    background: #282667; 
    border: none;
    font-family: "CloudLight";
    letter-spacing: 1.6px;
    color: #FFFFFF;
    opacity: 0.7;
    font-size: 18px;
  }

  .style-chooser .vs__clear,
  .style-chooser .vs__open-indicator {
    fill: #FFFFFF;
  }

</style>