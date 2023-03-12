<template>
  <div>
    <button @click="mostrarSliders">Mostrar sliders</button>
    <div v-if="slidersMostrados">
      <div class="flex flex-col gap-4">
        <label for="slider1">Personalidad 1</label>
        <input
          type="range"
          min="0"
          max="100"
          v-model="sliders[0].porcentaje"
          class="bg-gray-200 h-2 rounded-full"
        >
        <label for="slider2">Personalidad 2</label>
        <input
          type="range"
          min="0"
          max="100"
          v-model="sliders[1].porcentaje"
          class="bg-gray-200 h-2 rounded-full"
        >
        <label for="slider3">Personalidad 3</label>
        <input
          type="range"
          min="0"
          max="100"
          v-model="sliders[2].porcentaje"
          class="bg-gray-200 h-2 rounded-full"
        >
        <label for="slider4">Personalidad 4</label>
        <input
          type="range"
          min="0"
          max="100"
          v-model="sliders[3].porcentaje"
          class="bg-gray-200 h-2 rounded-full"
        >
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      slidersMostrados: false,
      sliders: [
        { value: "Personalidad 1", porcentaje: "" },
        { value: "Personalidad 2", porcentaje: "" },
        { value: "Personalidad 3", porcentaje: "" },
        { value: "Personalidad 4", porcentaje: "" },
      ],
    };
  },
  methods: {
    mostrarSliders() {
      this.slidersMostrados = true;
    },
  },
};
</script>
