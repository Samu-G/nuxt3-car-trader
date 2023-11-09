<script setup>
import {useCars} from "~/composables/useCars.js";

const route = useRoute()
useHead({
  title: `${route.params.name} number ${route.params.ID}`
})

// recupero il file json
const { cars } = useCars();
// cerco nel file json l'auto tramite id
const car = computed(() => {
  // uso la funzione find di default per ricercare in file sotto forma di Array
  return cars.find((researchedCar) => {
    // definisco CONDIZIONE DI USCITA e return
    return researchedCar.id === parseInt(route.params.ID)
  })
})

// lancio un errore se viene richiesta una pagina con ID non corrispondente
if(!car.value) {
  throw createError({
    statusCode: '404',
    message: `Car with ID ${route.params.ID} doesn't exist`
  })
}

</script>

<template>
  <div>
    <NavBar/>
    <div v-if="car" class="mx-auto mt-4 max-w-7xl space-y-4 px-4 xs:px-8 sm:px-10 lg:px-16 pb-16 w-3/5">
      <CarDetailHero :car="car"/>
      <CarDetailAttributes :features="car.features"/>
      <CarDetailDescription :description="car.description"/>
      <CarDetailContact />
    </div>
  </div>
</template>