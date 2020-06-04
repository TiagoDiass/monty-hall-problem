<template>
  <div class="door-area">
    <div class="door-frame" :class="{ selected: selected && !open }">
      <Gift v-if="open && hasGift" />
    </div>
    <div class="door" :class="{ open }" @click="selected = !selected">
      <div class="number" :class="{ selected }">{{ number }}</div>
      <div class="knob" @click="open = true"></div>
    </div>
  </div>
</template>

<script>
import Gift from "./Gift";
export default {
  name: "Door",
  components: { Gift },
  props: {
    number: {},
    hasGift: { type: Boolean }
  },
  data: function() {
    return {
      open: false,
      selected: false
    };
  }
};
</script>

<style>
:root {
  --door-border: 5px solid brown;
  --selected-border: 5px solid var(--secondary-color);
  --secondary-color: #d8df20;
}

.door-area {
  position: relative;
  width: 200px;
  height: 310px;
  border-bottom: 10px solid #aaa;
  margin-bottom: 20px;
  font-size: 3rem;

  display: flex;
  justify-content: center;
}

.door-frame {
  position: absolute;
  width: 180px;
  height: 300px;

  border-left: var(--door-border);
  border-top: var(--door-border);
  border-right: var(--door-border);

  display: flex;
  justify-content: center;
  align-items: flex-end;
}

.door {
  position: absolute;
  top: 5px;
  height: 295px;
  width: 170px;
  background-color: chocolate;

  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 17px;
}

.door .knob {
  height: 20px;
  width: 20px;
  border-radius: 50%;
  background-color: brown;
  align-self: flex-start;
  margin-top: 60px;
  transition: opacity 0.1s;
}

.door .knob:hover {
  cursor: pointer;
  opacity: 75%;
}

.door-frame.selected {
  border-left: var(--selected-border);
  border-top: var(--selected-border);
  border-right: var(--selected-border);
}

.door .number.selected {
  color: var(--secondary-color);
}

.door.open {
  background: #0007;
}

.door.open .knob,
.door.open .number {
  display: none;
}
</style>