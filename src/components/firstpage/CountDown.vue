<template>
  <div >
    <div v-if="timeLeft" class="countdown">
    <div>
        <div>
            {{ timeLeft.days }}
        </div> 
        <div>
            {{$t('countdownTimes.days')}}
        </div>
    </div>
    <div>
        <div>
            {{ timeLeft.hours }}
        </div> 
        <div>
            {{$t('countdownTimes.hours')}}
        </div>
    </div>
    <div>
        <div>
            {{ timeLeft.minutes }}
        </div>
        <div>
           {{$t('countdownTimes.minutes')}}
        </div> 
    </div>
    <div>
        <div>
            {{ timeLeft.seconds }}
        </div> 
        <div>
            {{$t('countdownTimes.seconds')}}
        </div>
    </div>
    </div>
    <div v-else>
      <p>It's the big day!</p>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue';

const targetDate = new Date('2024-08-18T00:00:00'); // Replace with your wedding date

const timeLeft = ref(null);

const updateTimeLeft = () => {
  const now = new Date();
  const difference = targetDate - now;

  if (difference <= 0) {
    timeLeft.value = null;
    return;
  }

  timeLeft.value = {
    days: Math.floor(difference / (1000 * 60 * 60 * 24)),
    hours: Math.floor((difference / (1000 * 60 * 60)) % 24),
    minutes: Math.floor((difference / 1000 / 60) % 60),
    seconds: Math.floor((difference / 1000) % 60)
  };
};

let interval;

onMounted(() => {
  updateTimeLeft();
  interval = setInterval(updateTimeLeft, 1000);
});

onUnmounted(() => {
  clearInterval(interval);
});
</script>

<style scoped>
div {
  text-align: center;
  display: flex;
  column-gap: 30px;
}
.countdown>div{
    display: flex;
    flex-direction: column;
    align-items: center;
}
.countdown>div>div:first-child{
    font-size: 60px;
    font-family: 'MontserratARM', Arial, sans-serif;
}
.countdown>div>div:nth-child(2){
    font-size: 20px;
}
.countdown>div:not(:last-child){
    border-right: 1px solid #f3ede6;
    padding-right: 20px;
}
h1 {
  font-size: 2em;
  margin-bottom: 0.5em;
}
p {
  font-size: 1.5em;
  margin: 0.2em;
}

@media screen and (min-width: 375px) and (max-width: 600px) {
    .countdown>div>div:first-child {
        font-size: 30px;
        font-family: 'MontserratARM', Arial, sans-serif;
    }
    .countdown>div>div:nth-child(2) {
    font-size: 17px;
}
}
</style>
