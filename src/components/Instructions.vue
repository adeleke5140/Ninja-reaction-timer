<template>
  <div class="instructions">
    <p>
      Your mission is to strike at the target as fast as you can once it
      appears!
    </p>
    <p>Are you ready to take in On, <span class="green">Shinobi?</span> 🥷🏼</p>
  </div>
</template>

<script setup></script>

<style>
.instructions {
  font-family: "Assassin Ninja";
  position: absolute;
  top: 0;
  left: 0;
  text-align: left;
  padding: 20px;
  margin: 10px;
  font-size: 0.8rem;
  border-top-left-radius: 37px 140px;
  border-top-right-radius: 23px 130px;
  border-bottom-left-radius: 110px 19px;
  border-bottom-right-radius: 120px 24px;
  border: solid 1px #0faf87;
  transform: rotate(-1deg);
  box-shadow: 3px 15px 8px -10px rgba(0, 0, 0, 0.3);
  transition: all 0.13s ease-in;
}

.instructions:hover {
  transform: translateX(10px) rotate(1deg);
  box-shadow: 3px 15px 8px -10px rgba(0, 0, 0, 0.3);
}

.green {
  text-transform: uppercase;
  color: #0faf87;
}
</style>
