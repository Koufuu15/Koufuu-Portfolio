<template>
  <div class="works-section">

    <h2>Works</h2>

    <div class="slider">

      <div
        class="slides"
        :style="{ transform:`translateX(-${current * (100/3)}%)` }"
      >

        <div
          class="card"
          v-for="(work,i) in works"
          :key="i"
        >
          <h3>{{work.title}}</h3>
          <p>{{work.text}}</p>
        </div>

      </div>

    </div>

    <!-- dots -->
    <div class="dots">
      <span
        v-for="(w,i) in works.length-2"
        :key="i"
        :class="{active: i===current}"
        @click="current=i"
      ></span>
    </div>

  </div>
</template>

<script>
import {ref,onMounted} from "vue"

export default {

  setup(){

    const works = [
      {title:"Security Blog",text:"Write-ups about CTF"},
      {title:"CTF Tools",text:"Automation tools"},
      {title:"Web Apps",text:"Full stack apps"},
      {title:"Reverse Research",text:"Binary analysis"},
      {title:"Security Scripts",text:"Python tools"}
    ]

    const current = ref(0)

    onMounted(()=>{

      setInterval(()=>{

        current.value++

        if(current.value > works.length-3){
          current.value = 0
        }

      },4000)

    })

    return {works,current}

  }

}
</script>

<style scoped>
.works-section{
  max-width:1100px;
  margin:auto;
  padding:60px 20px;
}

h2{
  margin-bottom:40px;
}

/* slider */

.slider{
  overflow:hidden;
}

.slides{
  display:flex;
  transition:transform .7s ease;
}

/* card */

.card{

  min-width:33.33%;
  margin:0 10px;

  padding:28px;

  background:white;

  border-radius:12px;

  box-shadow:0 10px 25px rgba(0,0,0,0.08);

  transition:all .3s ease;

}

/* hover animation */

.card:hover{

  transform:translateY(-10px) scale(1.03);

  box-shadow:0 20px 40px rgba(0,0,0,0.15);

}

/* dots */

.dots{

  text-align:center;
  margin-top:25px;

}

.dots span{

  display:inline-block;

  width:10px;
  height:10px;

  margin:0 6px;

  border-radius:50%;

  background:#ccc;

  cursor:pointer;

  transition:.3s;

}

.dots span.active{

  background:#222;

  transform:scale(1.3);

}
</style>