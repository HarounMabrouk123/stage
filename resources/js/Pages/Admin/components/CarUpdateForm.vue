this is my update form : <script setup>
import { onMounted } from 'vue'
import { initFlowbite } from 'flowbite'
import { router } from '@inertiajs/vue3';
import { useForm } from '@inertiajs/vue3';
import { usePage } from '@inertiajs/vue3';





const form = useForm({
      matricule: null,
      marque: null,
      distance: null,
    });

const car = usePage().props.car



    function submitForm(id){
        router.put(`/admin/dashbord/Cars/${id}`, form);

}    






// initialize components based on data attribute selectors
onMounted(() => {
  initFlowbite();
  // Update form values with car attributes
  if (car) {
    form.matricule = car.matricule || '';
    form.marque = car.marque || '';
    form.distance = car.distance || '';
  }
});
</script>
<template>
    <h1></h1>
                <div class="flex justify-between items-center pb-4 mb-4 rounded-t border-b sm:mb-5 dark:border-gray-600">
                <h3 class="text-lg font-semibold text-gray-900 dark:text-white">
                    Edit car
                </h3>
                <button type="button" class="text-gray-400 bg-transparent hover:bg-gray-200 hover:text-gray-900 rounded-lg text-sm p-1.5 ml-auto inline-flex items-center dark:hover:bg-gray-600 dark:hover:text-white" data-modal-toggle="defaultModal">
                    <svg aria-hidden="true" class="w-5 h-5" fill="currentColor" viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg"><path fill-rule="evenodd" d="M4.293 4.293a1 1 0 011.414 0L10 8.586l4.293-4.293a1 1 0 111.414 1.414L11.414 10l4.293 4.293a1 1 0 01-1.414 1.414L10 11.414l-4.293 4.293a1 1 0 01-1.414-1.414L8.586 10 4.293 5.707a1 1 0 010-1.414z" clip-rule="evenodd"></path></svg>
                    <span class="sr-only">Close modal</span>
                </button>
            </div>
            <form @submit.prevent="submitForm(car.id)">
                <div class="grid gap-4 mb-4 sm:grid-cols-2">
                    <div>
                        <label for="marque" class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Marque </label>
                        <input  v-model="form.marque" type="text" name="marque" id="marque" class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-primary-600 focus:border-primary-600 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-primary-500 dark:focus:border-primary-500" placeholder="Type car Model" >
                    </div>
                    <div>
                        <label for="distance" class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Kilométrage</label>
                        <input v-model="form.distance" type="text" name="distance" id="distance" class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-primary-600 focus:border-primary-600 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-primary-500 dark:focus:border-primary-500" placeholder="distance parcourue" >
                    </div>
                    <div>
                        <label for="matricule" class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Matricule</label>
                        <input v-model="form.matricule"  type="text" name="matricule" id="matricule" class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-primary-600 focus:border-primary-600 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-primary-500 dark:focus:border-primary-500" placeholder="distance parcourue" >
                    </div>

                </div>
                <button type="submit" class="bg-blue-500 text-black inline-flex items-center bg-primary-700 hover:bg-primary-800 focus:ring-4 focus:outline-none focus:ring-primary-300 font-medium rounded-lg text-sm px-5 py-2.5 text-center dark:bg-primary-600 dark:hover:bg-primary-700 dark:focus:ring-primary-800">
                    <svg class="mr-1 -ml-1 w-6 h-6" fill="currentColor" viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg"><path fill-rule="evenodd" d="M10 5a1 1 0 011 1v3h3a1 1 0 110 2h-3v3a1 1 0 11-2 0v-3H6a1 1 0 110-2h3V6a1 1 0 011-1z" clip-rule="evenodd"></path></svg>
                    Update car
                </button>
            </form>
</template>