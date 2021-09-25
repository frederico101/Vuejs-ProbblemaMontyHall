<template>
  <div class="door-area">
      <div class="door-frame" :class="{ selectedCssClass: selectedBoolean }">
          <Gift v-if="open && hasGift" />
      </div>
      <div class="door" @click="selectedBoolean = !selectedBoolean">
          <div class="number" :class="{selectedCssClass: selectedBoolean}"> {{number}} </div>
          <div class="knob"></div> 
      </div>
  </div>
</template>

<script>
import Gift from './Gift'
export default {
     name: 'Door',
     components: { Gift },
     props:{
        number: {},
        hasGift: { type: Boolean }
     },
     data: function(){
        return { 
            open: false,
            selectedBoolean: false
        }
     }
}
</script>

<style>
:root {

    --door-border: 5px solid brown;
    --selected-border: 5px solid yellow;
}
.door-area{
    position: relative;
    width: 200px;
    height: 310px;
    border-bottom: 10px solid #AAA;
    margin-bottom: 20px;
    font-size: 3rem;

    display: flex;
    justify-content: center;

 }
 .door-frame {
  position: absolute;
  height: 300px;
  width: 180px;
  border-top: var(--door-border);
  border-left: var(--door-border);
  border-right: var(--door-border);

   display: flex;
   justify-content: center;
   align-items: flex-end;
 }
 .door{
     position: absolute;
     top: 5px;
     background-color: chocolate;
     height: 295px;
     width: 170px;

     display: flex;
     flex-direction: column;
     align-items: center;
     padding: 15px;
 }
 .door .knob{

     background-color: rgb(238, 230, 230);
     height: 20px;
     width: 20px;
     border-radius: 10px;
     align-self: flex-start;
     margin-top: 60px;
    
 }
 .door-frame.selectedCssClass {
   border-top: var(--selected-border);
  border-left: var(--selected-border);
  border-right: var(--selected-border);
 }
</style>