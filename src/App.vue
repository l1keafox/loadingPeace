<template>
  <div id="wrapper" data-configuration="1" data-roundness="3">
    <div class="shape"> </div>
    <div class="shape"> </div>
    <div class="shape"> </div>
    <div class="shape"> </div>
    <div class="shape"> </div>
    <div class="shape"> </div>
    <div class="shape"> </div>
  </div>
</template>

<script>

export default {
  name: 'App',
  components: {
  },
  mounted(){
    const wrapper = document.getElementById("wrapper");
    const rand = (min,max) =>  Math.floor(Math.random()*(max-min+1)+min );
    const combinations = [
      {configuration:1,roundness:1},
      {configuration:1,roundness:2},
      {configuration:1,roundness:4},
      {configuration:2,roundness:2},
      {configuration:2,roundness:3},
      {configuration:3,roundness:3},
    ];
    let prev = 0;
    const uniqueRand = (min, max,prev) =>{
      let next = prev;
      while(prev===next) next = rand(min,max);
      return next;
    }

    setInterval(()=>{
      const index = uniqueRand(0, combinations.length-1,prev),
          combination = combinations[index];
          wrapper.dataset.configuration = combination.configuration;
          wrapper.dataset.roundness = combination.roundness;

          prev- index;
    },3000 )

  }
}
</script>

<style>
body{
  height: 100vh;
  width:100vw;
  margin: 0px;
  overflow:hidden;
  background-color: rgb(20, 20, 20);
  display:grid;
  place-items: center;
}
#wrapper{
  aspect-ratio: 1.618;
  width: 90vmin;
  position: relative;
}

#wrapper > .shape{
  height: 30%;
  width: 30%;
  background-color: rgba(255, 255, 255, 0.5);
  position: absolute;
  transition: left,top,height,width,border-radius;
  transition-duration: 750ms;
  transition-timing-function: ease-in-out;
}

#wrapper > .shape:nth-child(1){
  background-color: #10002b;
}
#wrapper > .shape:nth-child(2){
  background-color: #240046;
}
#wrapper > .shape:nth-child(3){
  background-color: #3c096c;
}
#wrapper > .shape:nth-child(4){
  background-color: #5a189a;
}
#wrapper > .shape:nth-child(5){
  background-color: #7b2cbf;
}
#wrapper > .shape:nth-child(6){
  background-color: #9d4edd;
}
#wrapper > .shape:nth-child(7){
  background-color: #c77dff;
}

#wrapper[data-roundness="1"] > .shape{
  border-radius: 6rem;
}
#wrapper[data-roundness="2"] > .shape{
  border-radius: 0rem;
}
#wrapper[data-roundness="3"] > .shape{
  border-radius: 100rem;
}

#wrapper[data-roundness="4"] > .shape:nth-child(1){
  border-bottom-left-radius: 10rem;
}
#wrapper[data-roundness="4"] > .shape:nth-child(3){
  border-top-right-radius:12rem;
}
#wrapper[data-roundness="4"] > .shape:nth-child(4){
  border-top-right-radius:10rem;
  border-bottom-right-radius:10rem;
}
#wrapper[data-roundness="4"] > .shape:nth-child(7){
  border-top-left-radius:10rem;
}

#wrapper[data-configuration="1"] > .shape.shape:nth-child(1){
  left: 0%;
  top: 0%;
  height:50% ;
  width: 20%;
}
#wrapper[data-configuration="1"] > .shape.shape:nth-child(2){
  left: 20%;
  top: 0%;
  height: 50%;
  width: 30%;
}
#wrapper[data-configuration="1"] > .shape.shape:nth-child(3){
  left: 50%;
  top: 0%;
  height: 100%;
  width: 50%;
}
#wrapper[data-configuration="1"] > .shape.shape:nth-child(4){
  left: 0%;
  top: 50%;
  height: 50%;
  width: 30%;
}
#wrapper[data-configuration="1"] > .shape.shape:nth-child(5){
  left: 30%;
  top: 50%;
  height: 50%;
  width: 20%;
}
#wrapper[data-configuration="1"] > .shape.shape:nth-child(6){
  left: 70%;
  top: 50%;
  height: 50%;
  width: 30%;
}
#wrapper[data-configuration="1"] > .shape.shape:nth-child(7){
  left: 85%;
  top: 75%;
  height: 25%;
  width: 15%;
}

#wrapper[data-configuration="2"] > .shape.shape:nth-child(1){
  left: 25%;
  top: 20%;
  height:80% ;
  width: 15%;
}
#wrapper[data-configuration="2"] > .shape.shape:nth-child(2){
  left: 40%;
  top: 20%;
  height: 50%;
  width: 10%;
}
#wrapper[data-configuration="2"] > .shape.shape:nth-child(3){
  left: 50%;
  top: 0%;
  height: 100%;
  width: 25%;
}
#wrapper[data-configuration="2"] > .shape.shape:nth-child(4){
  left: 0%;
  top: 0%;
  height: 50%;
  width: 10%;
}
#wrapper[data-configuration="2"] > .shape.shape:nth-child(5){
  left: 10%;
  top: 5%;
  height: 70%;
  width: 15%;
}
#wrapper[data-configuration="2"] > .shape.shape:nth-child(6){
  left: 75%;
  top: 10%;
  height: 80%;
  width: 15%;
}
#wrapper[data-configuration="2"] > .shape.shape:nth-child(7){
  left: 90%;
  top: 40%;
  height: 60%;
  width: 10%;
}

</style>
