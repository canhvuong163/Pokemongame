<template>
    <CopyRightScr />
    <div>
        <div class="screen">
            <h1>POKEMON GAME</h1>
            <p>Chọn chế độ để bắt đầu!</p>
            <div class="modes">
                    <button @click="onStart(16)">
                        <span>4x4</span>
                        <span>Dễ</span>
                    </button>
                    <button @click="onStart(36)">
                        <span>6x6</span>
                        <span>Trung Bình</span>
                    </button>
                    <button @click="onStart(64)">
                        <span>8x8</span>
                        <span>Khó</span>
                    </button>
                    <button @click="onStart(100)">
                        <span>10x10</span>
                        <span>Siêu khó</span>
                    </button>
                    <button @click="onStart(144)">
                        <span>12x12</span>
                        <span>Địa Ngục</span>
                    </button>
                </div>
        </div>
    </div>
</template>
<script>
import CopyRightScr from './CopyRightScr.vue';
export default {
    name: "MainScreen",
    components: {
        CopyRightScr,
    },
    methods: {
        onStart(totalOfBlocks) {
            this.$emit("onStart", { totalOfBlocks });
        },
    },
};
</script>

<style lang="css" scoped>
    .screen {
  width: 100%;
  height: 100vh;
  position: absolute;
  top: 0;
  left: 0;
  z-index: 2;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  background-color: var(--dark);
  color: yellow;
}

.screen h1 {
  font-size: 4.5rem;
  text-transform: uppercase;
  
}

.screen p {
  font-size: 2rem;
}

.modes {
  display: flex;
  margin-top: 2rem;
}

.modes button {
  font: var(--font);
  width: 150px;
  height: 150px;
  background: transparent;
  box-shadow: none;
  border: 1px solid var(--light);
  color: var(--light);
  display: flex;
  flex-direction: column;
  border-radius: 1rem;
  margin: 0 1rem;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  transition: background 0.3s ease-in-out;
}

.modes button:hover {
  background-color: var(--light);
  color: var(--dark);
}

.modes button span:first-child {
  font-size: 2rem;
}

.modes button span:last-child {
  display: block;
  font-size: 1.25rem;
  margin-top: 0.5rem;
}
    
</style>