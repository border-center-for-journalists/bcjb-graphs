<script>
  export let value;
  export let title;
 
</script>
<main>
  <div class='container'>
    <div class='gauge' style="animation-delay: -{value}s"></div>
    <p class='value'>{value}%</p>
  </div>
  <h3>{title}</h3>
</main>
<style>
  main{
    width:150px;
  }
  h3{
    font-size:18px;
    text-align: center;
  }
.container{
  position: relative; 
  width:90px;
  height:90px;
  margin: 0 auto;
}
.value{
  position: absolute;
  top: 21px;
  left:0;
  right: 0;
  bottom: 0;
  font-size:18px;
  text-align: center;
}
.gauge {
  width: 90px;
  height: 90px;
  top: 0;
  left: 0;
  margin: auto;
  position: absolute;
  background: #676767 linear-gradient(to right, #676767 50%, #FFF200 50%);
  color: #FFF200;
  border-radius: 50%;
}
@-webkit-keyframes spin {
  to {
    transform: rotate(180deg);
  }
}
@keyframes spin {
  to {
    transform: rotate(180deg);
  }
}
@-webkit-keyframes background {
  50% {
    background-color: currentColor;
  }
}
@keyframes background {
  50% {
    background-color: currentColor;
  }
}
.gauge::after {
  content: '';
  position: absolute;
  width: 72%;
  height: 72%;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  margin: auto;
  background: #343434;
  border-radius: 50%;
}
.gauge::before {
  content: '';
  position: absolute;
  display: block;
  background-color: inherit;
  height: 100%;
  width: 50%;
  bottom: 0;
  right: 0;
  border-radius: 0 100% 100% 0 / 50%;
  transform: rotate(0);
  transform-origin: 0 50%;
  -webkit-animation: 50s spin infinite linear, 100s background infinite step-end;
          animation: 50s spin infinite linear, 100s background infinite step-end;
  -webkit-animation-play-state: paused;
          animation-play-state: paused;
  -webkit-animation-delay: inherit;
          animation-delay: inherit;
}



</style>