<template>
  <div class="region">
    <h1>{{ $store.state.regionTitulo }}</h1>
    <h2>
      Total: {{ $store.state.regionTotal }} de infectados
    </h2>
    <button @click="$router.push('/')">Volver</button>
  </div>
</template>
