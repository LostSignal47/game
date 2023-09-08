<template>
  <div>
    <h1>เป่า ยิ้ง ฉุบ</h1>
    <button @click="playGame('random')">เป่า ยิ้ง ฉุบ</button>
    <button @click="resetGame">เริ่มใหม่</button> <!-- เพิ่มปุ่ม "เริ่มใหม่" -->
    <img :src="playerImgUrl" alt="Player choice" />
    <img :src="computerImgUrl" alt="Computer choice" />
    <p>{{ result }}</p>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const playerImgUrl = ref('https://img1.pnghut.com/t/20/23/1/1rWXQZLV7g/player-nose-cartoon-american-football-violet.jpg');
const computerImgUrl = ref('https://img1.pnghut.com/t/20/23/1/1rWXQZLV7g/player-nose-cartoon-american-football-violet.jpg');
const result = ref('');

const choices = {
  rock: 'https://png.pngtree.com/png-clipart/20210108/ourmid/pngtree-hammer-cartoon-style-hammer-clipart-png-image_2678399.jpg',
  paper: 'https://www.pngbie.com/assets/images/icon/xNPcdEQ0RvPngbie-06202151391624200699.png',
  scissors: 'https://png.pngtree.com/png-clipart/20190116/ourmid/pngtree-blue-scissors-beautiful-scissors-tailor-scissors-scissors-decoration-png-image_405186.jpg',
  love: 'https://img1.thaipng.com/20180407/quq/kisspng-heart-shape-clip-art-hearts-background-5ac84360db1146.4231384215230738888973.jpg' // เพิ่มตัวเลือกใหม่
};

const playGame = (playerChoice) => {
  if (playerChoice === 'random') {
    playerChoice = ['rock', 'paper', 'scissors', 'love'][Math.floor(Math.random() * 4)]; // เพิ่มตัวเลือกใหม่
  }

  const computerChoice = ['rock', 'paper', 'scissors', 'love'][Math.floor(Math.random() * 4)]; // เพิ่มตัวเลือกใหม่
  playerImgUrl.value = choices[playerChoice];
  computerImgUrl.value = choices[computerChoice];
  
  if (playerChoice === computerChoice) {
    result.value = 'Draw!';
  } else if (
    (playerChoice === 'rock' && computerChoice === 'scissors') ||
    (playerChoice === 'paper' && computerChoice === 'rock') ||
    (playerChoice === 'scissors' && computerChoice === 'paper') ||
    (playerChoice === 'love' && computerChoice !== 'love') // ตัวเลือกใหม่ชนะตัวเลือกอื่นทุกตัว
  ) {
    result.value = 'You win!';
  } else {
    result.value = 'You lose!';
  }
};

const resetGame = () => {
  playerImgUrl.value = 'https://img1.pnghut.com/t/20/23/1/1rWXQZLV7g/player-nose-cartoon-american-football-violet.jpg';
  computerImgUrl.value = 'https://img1.pnghut.com/t/20/23/1/1rWXQZLV7g/player-nose-cartoon-american-football-violet.jpg';
  result.value = '';
};
</script>
