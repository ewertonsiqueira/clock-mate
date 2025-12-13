<template>
  <v-container class="d-flex justify-center align-center" style="min-height: 100vh;">
    <v-card class="mx-auto pa-6" max-width="400">
      <v-card-title class="mx-auto text-h5 mb-4">ClockMate</v-card-title>
      <v-card-text>
        <v-text-field
          v-model.number="total"
          class="mb-3"
          label="Total necessário"
          persistent-placeholder
          placeholder="Digite o total a serem feitos"
          type="number"
          variant="outlined"
        />
        <v-text-field
          v-model.number="feitas"
          class="mb-3"
          label="Horas já feitas"
          persistent-placeholder
          placeholder="Digite as horas já feitas"
          type="number"
          variant="outlined"
        />
        <v-text-field
          v-model.number="dias"
          class="mb-5"
          label="Dias restantes"
          persistent-placeholder
          placeholder="Digite os dias restantes"
          type="number"
          variant="outlined"
        />

        <div v-if="falta >= 0" class="mb-2 text-subtitle-1">Faltam {{ falta }} horas</div>
        <div v-if="porDia > 0" class="text-subtitle-1">
          Você precisa fazer aproximadamente {{ formatHorasMinutos(porDia) }} horas/dia
        </div>
      </v-card-text>
    </v-card>
  </v-container>
</template>

<script setup>
  import { computed, ref } from 'vue'

  const total = ref(200)
  const feitas = ref(0)
  const dias = ref(0)

  const falta = computed(() => total.value - feitas.value)
  const porDia = computed(() => falta.value / dias.value)

  function formatHorasMinutos (valor) {
    if (Number.isNaN(valor) || !Number.isFinite(valor)) return '0h 00min'
    const horas = Math.floor(valor)
    const minutos = Math.round((valor - horas) * 60)
    return `${horas}h ${minutos.toString().padStart(2, '0')}min`
  }
</script>

<style>

</style>
